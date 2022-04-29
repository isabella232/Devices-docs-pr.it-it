---
title: Configurare account di amministratore non globali in Surface Hub
description: Questo articolo descrive come configurare gli account amministratore non globali per gestire Surface Hub e Surface Hub 2S.
keywords: Surface Hub, Surface Hub v1, Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/15/2022
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: be6a6c75155b3c45ae9dda9dd2726033411100c4
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497695"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a>Configurare account di amministratore non globali in Surface Hub

L'aggiornamento Windows 10 Team 2020 aggiunge il supporto per la configurazione di account di amministrazione non globali che limitano le autorizzazioni per la gestione dell'app Impostazioni nei dispositivi Surface Hub aggiunti a un dominio Azure AD. In questo modo è possibile definire l'ambito delle autorizzazioni di amministratore solo per Surface Hub e impedire l'accesso amministratore potenzialmente indesiderato a un intero dominio Azure AD. Prima di iniziare, assicurarsi che il Surface Hub sia aggiunto a Azure AD e Intune registrato automaticamente. In caso contrario, sarà necessario reimpostare Surface Hub e completare il programma di installazione predefinito per la prima volta, scegliendo l'opzione per l'aggiunta a Azure AD.

Windows 10 Team 2020 Update 2 aggiunge il supporto per [il provider di servizi di configurazione LocalUsersAndGroups](/windows/client-management/mdm/policy-csp-localusersandgroups). In questo modo viene sostituito il [provider di servizi di configurazione RestrictedGroups](/windows/client-management/mdm/policy-csp-restrictedgroups), che rimane disponibile ma non è più consigliato, come illustrato di seguito.

## <a name="summary"></a>Riepilogo

Il processo di creazione di account amministratore non globali prevede i passaggi seguenti:

1. In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per gestire Surface Hub.
2. Ottenere Azure AD SID del gruppo tramite PowerShell.
3. Creare un file XML contenente Azure AD SID del gruppo.
4. Creare un gruppo di sicurezza contenente i dispositivi Surface Hub gestiti dal gruppo di sicurezza degli amministratori non globali. 
5. Creare un profilo di configurazione personalizzato destinato al gruppo di sicurezza che contiene i dispositivi Surface Hub.

## <a name="create-azure-ad-security-groups"></a>Creare gruppi di sicurezza Azure AD

Creare prima di tutto un gruppo di sicurezza contenente gli account amministratore. Creare quindi un altro gruppo di sicurezza per i dispositivi Surface Hub.  

### <a name="create-security-group-for-admin-accounts"></a>Creare un gruppo di sicurezza per gli account amministratore

1. Accedere a Intune tramite l'interfaccia di [amministrazione Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), selezionare **GruppiNuovo** **** >  gruppo > e in Tipo di gruppo selezionare **Sicurezza.**
2. Immettere un nome di gruppo, ad esempio **Surface Hub Amministratori locali**, e quindi selezionare **Crea.**

     ![Creare un gruppo di sicurezza per gli amministratori dell'hub.](images/sh-create-sec-group.png)

3. Aprire il gruppo, selezionare **Membri** e scegliere **Aggiungi membri** per immettere gli account amministratore da designare come amministratori non globali in Surface Hub. Per altre informazioni sulla creazione di gruppi in Intune, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](/mem/intune/fundamentals/groups-add).

### <a name="create-security-group-for-surface-hub-devices"></a>Creare un gruppo di sicurezza per i dispositivi Surface Hub

1. Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi hub. ad esempio **, Surface Hub dispositivi**.

     ![Creare un gruppo di sicurezza per i dispositivi hub.](images/sh-create-sec-group-devices.png)

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>Ottenere Azure AD SID del gruppo con PowerShell

1. Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e assicurarsi che il sistema sia configurato per l'esecuzione di script di PowerShell. Per altre informazioni, vedere [Informazioni sui criteri di esecuzione](/powershell/module/microsoft.powershell.core/about/about_execution_policies?).
2. [Installare Azure PowerShell modulo](/powershell/azure/install-az-ps).
3. Accedere al tenant Azure AD.

    ```powershell
    Connect-AzureAD
    ```

4. Dopo aver eseguito l'accesso al tenant, eseguire il cmdlet seguente. Verrà richiesto di digitare l'ID oggetto del gruppo di Azure AD.

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
      
    }
    ```

5. In Intune selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente.

     ![Copiare l'ID oggetto del gruppo di sicurezza.](images/sh-objectid.png)

6. Eseguire il cmdlet seguente per ottenere il SID del gruppo di sicurezza:

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```

7. Incollare l'ID oggetto nel cmdlet di PowerShell, premere **INVIO** e copiare il **SID del gruppo Azure AD** in un editor di testo.

## <a name="create-xml-file-containing-azure-ad-group-sid"></a>Creare un file XML contenente Azure AD SID del gruppo

1. Copiare quanto segue in un editor di testo:

    ```xml
    <GroupConfiguration>
    <accessgroup desc = "S-1-5-32-544">
        <group action = "U" />
        <add member = "AzureAD\bob@contoso.com"/>
        <add member = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX"/>
    </accessgroup>
    </GroupConfiguration>
    ```
2. Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID del gruppo di Azure AD** e quindi salvare il file come XML, ad esempio **aad-local-admin.xml**.

      > [!NOTE]
      > Anche se i gruppi devono essere specificati tramite il SID, se si desidera aggiungere direttamente gli utenti di Azure, specificare i nomi dell'entità utente (UPN) in questo formato: `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a>Creare un profilo di configurazione personalizzato

1. In Endpoint Manager selezionare **DispositiviProfili** >  >  **di configurazioneCrea** **profilo**.
2. In Piattaforma selezionare **Windows 10 e versioni successive.** In Profilo selezionare **ModelliPersonalizzazioneCrea** > **** > **.**
3. Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**
4. In **Impostazioni di configurazione** >  **IMPOSTAZIONI URI OMA** selezionare **Aggiungi**.
5. Nel riquadro Aggiungi riga aggiungere un nome e in     **URI OMA** aggiungere la stringa seguente:

    ```OMA-URI
     ./Device/Vendor/MSFT/Policy/Config/LocalUsersAndGroups/Configure
    ```

   > [!NOTE]
   > L'impostazione dei criteri **RestrictedGroups/ConfigureGroupMembership** consente anche di configurare membri (utenti o gruppi di AAD) in un gruppo locale Windows 10. Tuttavia, consente solo una sostituzione completa dei gruppi esistenti con i nuovi membri. Non è possibile aggiungere o rimuovere membri in modo selettivo.  Disponibile in Windows 10 Team 2020 Update 2, è consigliabile usare l'impostazione dei criteri **LocalUsersandGroups** anziché l'impostazione dei criteri RestrictedGroups. L'applicazione di entrambe le impostazioni dei criteri a Surface Hub non è supportata e può produrre risultati imprevedibili.

6. In Tipo di dati selezionare **Stringa XML** e selezionare per aprire il file XML creato nel passaggio precedente.

     ![caricare il file di configurazione xml dell'amministratore locale.](images/sh-local-admin-config.png)

7. Fai clic su **Salva**.
8. Fare clic su **Seleziona gruppi da includere** e scegliere il [gruppo di sicurezza creato in precedenza](#create-security-group-for-surface-hub-devices) (**Surface Hub dispositivi**). Fai clic su **Avanti**.
9. In Regole di applicabilità aggiungere una regola, se necessario. In caso contrario, selezionare **Avanti** e **quindi crea.**

Per altre informazioni sui profili di configurazione personalizzati che usano stringhe URI OMA, vedere [Usare impostazioni personalizzate per i dispositivi Windows 10 in Intune](/mem/intune/configuration/custom-settings-windows-10).

## <a name="non-global-admins-managing-surface-hub"></a>Amministratori non globali che gestiscono Surface Hub

I membri del gruppo **Surface Hub Local Admins** Security possono ora accedere all'app Impostazioni in Surface Hub e gestire le impostazioni.

> [!IMPORTANT]
> L'accesso predefinito degli amministratori globali all'app Impostazioni viene rimosso (a meno che non siano anche membri di questo nuovo gruppo di sicurezza).

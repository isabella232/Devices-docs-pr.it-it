---
title: Configurare account di amministratore non globali in Surface Hub
description: In questo articolo viene descritto come configurare gli account amministratore non globali per gestire Surface Hub e Surface Hub 2S.
keywords: Surface Hub, Surface Hub v1, Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/22/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 11170f6c202faef7aa3dddcb8aa8c6fa84bea80f
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643862"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a>Configurare account di amministratore non globali in Surface Hub

L'Windows 10 Team 2020 aggiunge il supporto per la configurazione di account amministratore non globali che limitano le autorizzazioni per la gestione dell'app Impostazioni nei dispositivi Surface Hub aggiunti a un dominio di Azure AD. In questo modo è possibile impostare l'ambito delle autorizzazioni di amministratore solo Surface Hub e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD. Prima di iniziare, assicurati che il Surface Hub sia aggiunto ad Azure AD e Intune registrato automaticamente. In caso contrario, sarà necessario reimpostare Surface Hub e completare il programma di installazione della Configurazione guidata, scegliendo l'opzione per partecipare ad Azure AD.

## <a name="summary"></a>Riepilogo 

Il processo di creazione di account amministratore non globali prevede i passaggi seguenti: 

1. In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per la gestione Surface Hub.
2. Ottenere il SID del gruppo di Azure AD tramite PowerShell.
3. Creare un file XML contenente il SID del gruppo di Azure AD.
4. Crea un gruppo di sicurezza contenente Surface Hub dispositivi che verranno gestiti dal gruppo di sicurezza non amministratori globali.
5. Crea un profilo di configurazione personalizzato per il gruppo di sicurezza che contiene i dispositivi Surface Hub personalizzati. 


## <a name="create-azure-ad-security-groups"></a>Creare gruppi di sicurezza di Azure AD

Creare innanzitutto un gruppo di sicurezza contenente gli account amministratore. Crea quindi un altro gruppo di sicurezza per Surface Hub dispositivi.  

### <a name="create-security-group-for-admin-accounts"></a>Creare un gruppo di sicurezza per gli account amministratore

1. Accedi a Intune tramite [l'Microsoft Endpoint Manager di amministrazione,](https://go.microsoft.com/fwlink/?linkid=2109431) **seleziona**Gruppi Nuovo gruppo > e in Tipo di gruppo seleziona  >  **** **Sicurezza.** 
2. Immettere un nome di gruppo, ad esempio Surface Hub **amministratori locali,** quindi selezionare **Crea.** 

     ![Creare un gruppo di sicurezza per gli amministratori hub](images/sh-create-sec-group.png)

3. Aprire il gruppo, selezionare **Membri**e quindi scegliere Aggiungi membri per immettere gli account amministratore che si desidera designare come amministratori non globali in Surface Hub. **** Per altre informazioni sulla creazione di gruppi in Intune, vedi [Aggiungere gruppi per organizzare utenti e dispositivi.](/mem/intune/fundamentals/groups-add)

### <a name="create-security-group-for-surface-hub-devices"></a>Creare un gruppo di sicurezza per Surface Hub dispositivi

1. Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi Hub. ad esempio, **Surface Hub dispositivi**. 

     ![Creare un gruppo di sicurezza per i dispositivi Hub](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>Ottenere il SID del gruppo di Azure AD tramite PowerShell

1. Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell. Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](/powershell/module/microsoft.powershell.core/about/about_execution_policies?) 
2. [Installare Azure PowerShell modulo](/powershell/azure/install-az-ps).
3. Accedere al tenant di Azure AD.

    ```powershell
    Connect-AzureAD
    ```

4. Dopo aver eseguito l'accesso al tenant, eseguire il seguente commandlet. Verrà richiesto di digitare l'ID oggetto del gruppo di Azure AD.

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. In Intune, selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente. 

     ![Copia ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. Eseguire il seguente commandlet per ottenere il SID del gruppo di sicurezza:

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. Incollare l'ID oggetto nel commandlet di PowerShell, premere **INVIO**e quindi copiare il **SID** del gruppo di Azure AD in un editor di testo. 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a>Creare un file XML contenente il SID del gruppo di Azure AD

1. Copiare quanto segue in un editor di testo: 

    ```xml
      <groupmembership>   
      <accessgroup desc = "S-1-5-32-544">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > Potrebbe essere necessario utilizzare il nome [localizzato per l'account Administrator.](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx) Non rimuovere il membro Administrator predefinito dal file XML.

2. Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID** del gruppo di Azure AD e quindi salvare il file come XML. ad esempio, **aad-local-admin.xml**. 

      > [!NOTE]
      > Anche se i gruppi devono essere specificati tramite il PROPRIO SID, se si desidera aggiungere direttamente gli utenti di Azure, è possibile aggiungerli specificando il nome dell'entità utente (UPN) in questo formato: `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a>Creare un profilo di configurazione personalizzato

1. In Endpoint Manager, selezionare **Profili di**configurazione  >  **dispositivi**Crea  >  **profilo.** 
2. In Piattaforma selezionare **Windows 10 e versioni successive.** In Profilo selezionare **Personalizzato**e quindi **Crea.**
3. Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**
4. In **Impostazioni di configurazione**uri  >  **OMA Impostazioni**selezionare **Aggiungi**.
5. Nel riquadro Aggiungi riga aggiungi un nome e in     **URI OMA**aggiungi la stringa seguente: 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. In Tipo di dati selezionare **Xml stringa** e cercare per aprire il file XML creato nel passaggio precedente. 

     ![caricare il file xml di configurazione dell'amministratore locale](images/sh-local-admin-config.png)

7. Fai clic su **Salva**.
8. Fai **clic su Seleziona gruppi da includere** e scegli il gruppo di sicurezza creato in [precedenza](#create-security-group-for-surface-hub-devices) (**Surface Hub dispositivi**). Fai clic su **Avanti**.
9. In Regole di applicabilità, aggiungere una regola, se lo si desidera. In caso contrario, **selezionare Avanti** e quindi **Crea**.

Per altre informazioni sui profili di configurazione personalizzati che usano stringhe URI OMA, vedi Usare impostazioni personalizzate per Windows 10 [dispositivi in Intune.](/mem/intune/configuration/custom-settings-windows-10)


## <a name="non-global-admins-managing-surface-hub"></a>Amministratori non globali che gestiscono Surface Hub

I membri del **Surface Hub Di sicurezza** degli amministratori locali possono ora accedere all'app Impostazioni in Surface Hub e gestire le impostazioni.

> [!IMPORTANT]
> L'accesso predefinito degli amministratori globali all'app Impostazioni viene rimosso (a meno che non siano anche membri di questo nuovo gruppo di sicurezza).

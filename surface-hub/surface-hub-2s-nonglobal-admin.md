---
title: Configurare gli account diversi da amministratore globale in Surface Hub 2S
description: Questo articolo descrive come configurare gli account di amministratore non globale per gestire Surface Hub 2S.
keywords: Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/07/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: e16e4f8bd4b2b253233fa9790987287cf17966c7
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385174"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub-2s"></a>Configurare gli account diversi da amministratore globale in Surface Hub 2S

Quando si aggiunge Surface Hub 2S a un dominio di Azure AD, è possibile configurare account di amministratore non globale che limitano le autorizzazioni alla gestione dell'app Impostazioni in Surface Hub 2S. In questo modo puoi impostare l'ambito delle autorizzazioni di amministratore solo per Surface Hub 2S e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD. Prima di iniziare, assicurati che Surface Hub 2S sia aggiunto ad Azure AD. In caso contrario, dovrai reimpostare Surface Hub 2S e completare il primo programma di installazione della Configurazione guidata, scegliendo l'opzione per partecipare ad Azure AD.

## <a name="summary"></a>Riepilogo 

Il processo di creazione di account di amministratore non globale prevede i passaggi seguenti: 

1. In Microsoft Intune crea un gruppo di sicurezza contenente gli amministratori designati per gestire Surface Hub 2S.
2. Ottenere il SID del gruppo di Azure AD tramite PowerShell.
3. Creare un file XML contenente il SID del gruppo di Azure AD.
4. Crea un gruppo di sicurezza contenente i dispositivi Surface Hub 2S che verranno gestiti dal gruppo di sicurezza degli amministratori non globali.
5. Crea un profilo di configurazione personalizzato per il gruppo di sicurezza che contiene i dispositivi Surface Hub 2S. 


## <a name="create-azure-ad-security-groups"></a>Creare gruppi di sicurezza di Azure AD

Creare innanzitutto un gruppo di sicurezza contenente gli account amministratore. Crea quindi un altro gruppo di sicurezza per i dispositivi Surface Hub.  

### <a name="create-security-group-for-admin-accounts"></a>Creare un gruppo di sicurezza per gli account amministratore

1. Accedi a Intune tramite l'interfaccia **** di amministrazione di [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)seleziona Gruppi nuovo gruppo > e in Tipo di gruppo  >  **** seleziona **Sicurezza.** 
2. Immetti un nome di gruppo, ad esempio Amministratori locali di **Surface Hub,** e quindi seleziona **Crea.** 

     ![Creare un gruppo di sicurezza per gli amministratori hub](images/sh-create-sec-group.png)

3. Apri il gruppo, **seleziona**Membri **** e quindi scegli Aggiungi membri per immettere gli account amministratore che vuoi designare come amministratori non globali in Surface Hub 2S. Per altre informazioni sulla creazione di gruppi in Intune, vedere [Aggiungere gruppi per organizzare utenti e dispositivi.](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)

### <a name="create-security-group-for-surface-hub-2s-devices"></a>Creare un gruppo di sicurezza per i dispositivi Surface Hub 2S

1. Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi Hub. ad esempio, **dispositivi Surface Hub.** 

     ![Creare un gruppo di sicurezza per i dispositivi Hub](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a>Ottenere il SID del gruppo di Azure AD tramite PowerShell

1. Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell. Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?) 
2. [Installare il modulo di Azure PowerShell.](https://docs.microsoft.com/powershell/azure/install-az-ps)
3. Accedere al tenant di Azure AD.

    ```powershell
    Connect-AzureAD
    ```

4. Dopo aver eseguito l'accesso al tenant, eseguire il seguente commandlet. Verrà richiesto di "Digitare l'ID oggetto del gruppo di Azure AD".

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. In Intune, selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente. 

     ![Copia l'ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

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
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. Sostituisci il SID segnaposto (a partire da S-1-12-1) con il **SID** del gruppo di Azure AD e quindi salva il file come XML; ad esempio, **aad-local-admin.xml**. 

## <a name="create-custom-configuration-profile"></a>Creare un profilo di configurazione personalizzato

1. In Endpoint Manager seleziona **Profili di**configurazione  >  **dei dispositivi**Crea  >  **profilo.** 
2. In Piattaforma selezionare **Windows 10 e versioni successive.** In Profilo selezionare **Personalizzato**e quindi selezionare **Crea.**
3. Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**
4. In **Impostazioni di configurazione**impostazioni URI  >  **OMA**selezionare **Aggiungi.**
5. Nel riquadro Aggiungi riga aggiungi un nome e in     **URI OMA**aggiungi la stringa seguente: 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. In Tipo di dati selezionare **Xml** stringa e individuare il file XML creato nel passaggio precedente. 

     ![caricare il file xml di configurazione dell'amministratore locale](images/sh-local-admin-config.png)

7. Fai clic su **Salva**.
8. Fai **clic su Seleziona gruppi da includere** e scegli il gruppo di sicurezza creato in [precedenza](#create-security-group-for-surface-hub-2s-devices) (**dispositivi Surface Hub).** Fai clic su **Avanti**.
9. In Regole di applicabilità, aggiungere una regola, se lo si desidera. In caso contrario, **selezionare Avanti** e quindi **Crea.**

Per altre informazioni sui profili di configurazione personalizzati con stringhe URI OMA, vedi Usare le impostazioni personalizzate per i [dispositivi Windows 10 in Intune.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)


## <a name="non-global-admins-managing-surface-hub-2s"></a>Amministratori non globali che gestiscono Surface Hub 2S

I membri del gruppo Di sicurezza degli amministratori locali di **Surface Hub** possono ora accedere all'app Impostazioni in Surface Hub 2S e gestire le impostazioni.

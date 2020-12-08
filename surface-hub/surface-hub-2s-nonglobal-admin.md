---
title: Configurare gli account di amministratore non globali in Surface Hub 2S
description: Questo articolo descrive come configurare gli account di amministratore non globali per la gestione di Surface Hub 2S.
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
ms.openlocfilehash: 647a7bf53e5ca8dc52ddec21ec8393cc574ee95a
ms.sourcegitcommit: 16cc2e8d9dfc5d6e061e0b5b6ddfcf35547643f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "11196810"
---
# Configurare gli account di amministratore non globali in Surface Hub 2S

Quando si entra in Surface Hub 2S in un dominio di Azure AD, è possibile configurare gli account di amministratore non globali che limitano le autorizzazioni per la gestione dell'app impostazioni in Surface Hub 2S. In questo modo puoi usare l'ambito delle autorizzazioni di amministratore per solo hub di Surface 2S e impedire l'accesso di amministratore potenzialmente indesiderato a un intero dominio Azure AD. Prima di iniziare, assicurati che l'hub di Surface 2S sia unito ad Azure AD. In caso contrario, dovrai reimpostare Surface Hub 2S e completare il programma di configurazione per la prima volta, out-of-the-box (OOBE), scegliendo l'opzione per partecipare ad Azure AD.

## Riepilogo 

Il processo di creazione di account di amministratore non globali prevede i passaggi seguenti: 

1. In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per gestire Surface Hub 2S.
2. Ottenere un SID di gruppo di Azure AD usando PowerShell.
3. Creare un file XML contenente un SID di gruppo di Azure AD.
4. Creare un gruppo di sicurezza contenente i dispositivi di Surface Hub 2S che verranno gestiti dal gruppo di sicurezza amministratori non globali.
5. Creare un profilo di configurazione personalizzato destinato al gruppo di sicurezza che contiene i dispositivi di Surface Hub 2S. 


## Creare gruppi di sicurezza di Azure AD

Creare prima di tutto un gruppo di sicurezza contenente gli account di amministratore. Crea quindi un altro gruppo di sicurezza per i dispositivi Surface Hub.  

### Creare un gruppo di sicurezza per gli account di amministratore

1. Accedere a Intune tramite l'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) **, selezionare Raggruppa**  >  **nuovo gruppo** > e quindi in tipo di gruppo selezionare **sicurezza.** 
2. Immettere il nome di un gruppo, ad esempio gli **amministratori locali di Surface Hub** , quindi selezionare **Crea.** 

     ![Creare un gruppo di sicurezza per gli amministratori di hub](images/sh-create-sec-group.png)

3. Aprire il gruppo, selezionare **membri**e quindi scegliere **Aggiungi membri** per immettere gli account di amministratore che si desidera designare come amministratori non globali in Surface Hub 2S. Per ulteriori informazioni sulla creazione di gruppi in Intune, vedere  [aggiungere gruppi per organizzare utenti e dispositivi](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).

### Creare un gruppo di sicurezza per i dispositivi Surface Hub 2S

1. Ripetere la procedura precedente per creare un gruppo di sicurezza distinto per i dispositivi hub; ad esempio, i **dispositivi Surface Hub**. 

     ![Creare un gruppo di sicurezza per i dispositivi hub](images/sh-create-sec-group-devices.png) 

## Ottenere un SID di gruppo di Azure AD usando PowerShell

1. Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell. Per altre informazioni, vedere [informazioni sui criteri di esecuzione](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?). 
2. [Installare il modulo di PowerShell di Azure](https://docs.microsoft.com/powershell/azure/install-az-ps).
3. Accedere al tenant di Azure AD.

    ```powershell
    Connect-AzureAD
    ```

4. Dopo avere effettuato l'accesso al tenant, eseguire il unifiedgroup seguente. Verrà chiesto di digitare l'ID oggetto del gruppo Azure AD.

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. In Intune selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente. 

     ![Copiare l'ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. Eseguire la seguente unifiedgroup per ottenere il SID del gruppo di sicurezza:

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. Incollare l'ID oggetto nell'unifiedgroup di PowerShell, premere **invio**e quindi copiare il **SID di gruppo di Azure ad** in un editor di testo. 

## Creare un file XML contenente un SID di gruppo di Azure AD

1. Copiare le operazioni seguenti in un editor di testo: 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID di gruppo di Azure ad** e quindi salvare il file come XML; ad esempio, **aad-local-admin.xml**. 

## Creare un profilo di configurazione personalizzato

1. In Endpoint Manager selezionare i profili di configurazione dei **dispositivi**per  >  **Configuration profiles**  >  **creare il profilo**. 
2. In Platform selezionare **Windows 10 e versioni successive.** In profilo selezionare **personalizzato**e quindi selezionare **Crea.**
3. Aggiungere un nome e una descrizione e quindi fare clic su **Avanti.**
4. In **Configuration settings**  >  **Impostazioni configurazione OMA-URI**selezionare **Aggiungi**.
5. Nel riquadro Aggiungi riga aggiungere un nome e in     **OMA-URI**aggiungere la stringa seguente: 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. In tipo di dati selezionare **stringa XML** e Sfoglia per aprire il file XML creato nel passaggio precedente. 

     ![caricare file di configurazione XML di amministrazione locale](images/sh-local-admin-config.png)

7. Fare clic su **Save**.
8. Fare clic su **Seleziona gruppi per includere** e scegliere il [gruppo di sicurezza creato in precedenza](#create-security-group-for-surface-hub-2s-devices) (**dispositivi Surface Hub**). Fai clic su **Avanti**.
9. In regole di applicabilità aggiungere una regola, se lo si desidera. In caso contrario, seleziona **Avanti** e quindi scegli **Crea**.

Per altre informazioni sui profili di configurazione personalizzati con le stringhe OMA-URI, vedere [usare le impostazioni personalizzate per i dispositivi Windows 10 in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).


## Amministratori non globali che gestiscono Surface Hub 2S

I membri del gruppo di sicurezza **amministratori locali di Surface Hub** possono ora accedere all'app impostazioni in Surface Hub 2S e gestire le impostazioni.

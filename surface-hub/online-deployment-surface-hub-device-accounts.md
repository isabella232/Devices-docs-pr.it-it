---
title: Distribuzione online con Office 365 (Surface Hub)
description: Questo argomento contiene le istruzioni per l&#39;aggiunta di un account del dispositivo per Microsoft Surface Hub nel caso di una distribuzione online pura.
ms.assetid: D325CA68-A03F-43DF-8520-EACF7C3EDEC1
ms.reviewer: ''
manager: laurawi
keywords: account del dispositivo per Surface Hub, distribuzione online
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/21/2018
ms.localizationpriority: medium
ms.openlocfilehash: b38b8eb0ef13c2e945d63821e6e246ac7a59b2d7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833615"
---
# Distribuzione online con Office 365 (Surface Hub)


Questo argomento contiene le istruzioni per l&#39;aggiunta di un account del dispositivo per Microsoft Surface Hub nel caso di una distribuzione online pura.

In presenza di una distribuzione online pura (Office 365), puoi [usare gli script di PowerShell forniti](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts) per creare gli account del dispositivo. 

1. Avvia una sessione di PowerShell remota su un PC e connettiti a Exchange.

   Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.

   ```PowerShell
   Set-ExecutionPolicy RemoteSigned
   $org='contoso.microsoft.com'
   $cred=Get-Credential admin@$org
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```

2. Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente. In questo modo l'account potrà essere autenticato in Surface Hub.

   Se devi modificare una cassetta postale delle risorse esistente:

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   Se devi creare una nuova cassetta postale delle risorse:

   ```PowerShell
   New-Mailbox -MicrosoftOnlineServicesID HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

   I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False. Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.

   Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs". Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false -AllowNonProvisionableDevices $True
   ```

   Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo.

   ```PowerShell
   Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.Id
   ```

4. È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .

   ```PowerShell
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. Connettiti ad Azure AD.
    
   È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2. Da un prompt dei comandi con privilegi elevati eseguire il comando seguente:
    
   ```PowerShell
   Install-Module -Name AzureAD
   ```
   Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account. Puoi eseguire questo cmdlet per la connessione.

   ```PowerShell
   Import-Module AzureAD
   Connect-AzureAD -Credential $cred
   ```

6. Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell. Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).

   ```PowerShell
   Set-AzureADUser -ObjectId "HUB01@contoso.com" -PasswordPolicies "DisablePasswordExpiration"
   ```

7. Surface Hub richiede una licenza per la funzionalità Skype for Business. Per abilitare Skype for Business, l'ambiente deve soddisfare i [prerequisiti di Skype for Business online](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online).
   
   Puoi quindi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.

   Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.

   ```PowerShell
   Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"
    
   Get-AzureADSubscribedSku | Select Sku*,*Units
   $License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
   $License.SkuId = SkuId You selected 
    
   $AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
   $AssignedLicenses.AddLicenses = $License
   $AssignedLicenses.RemoveLicenses = @()
    
   Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
   ```

8. Abilita l'account del dispositivo con Skype for Business.
   Se non è installato il modulo PowerShell di Skype for Business, [scarica il modulo di Windows PowerShell di Skype for Business online](https://www.microsoft.com/download/details.aspx?id=39366). 

   - Per iniziare, crea una sessione di PowerShell remota da un PC.

     ```PowerShell
     Import-Module SkypeOnlineConnector  
     $cssess=New-CsOnlineSession -Credential $cred  
     Import-PSSession $cssess -AllowClobber
     ```

   - Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet (ad esempio, <em>alice@contoso.com</em>):

       ```PowerShell
       Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool
       ```
       Oppure impostando una variabile
        
       ```PowerShell
    $strRegistrarPool = Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool | out-string
    $strRegistrarPool = $strRegistrarPool.Substring($strRegistrarPool.IndexOf(':') + 2)
       ```
        
   - Abilitare l'account di Surface Hub con il cmdlet seguente:
      
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool yourRegistrarPool -SipAddressType EmailAddress
       ```
        
       O utilizzando la variabile $strRegistarPool dall'alto
        
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool $strRegistrarPool -SipAddressType EmailAddress
       ```

Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.






---
title: Distribuzione locale a foresta singola (Surface Hub)
description: Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a foresta singola.
ms.assetid: 80E12195-A65B-42D1-8B84-ECC3FCBAAFC6
ms.reviewer: ''
manager: laurawi
keywords: distribuzione a foresta singola, distribuzione locale, account del dispositivo, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.localizationpriority: medium
ms.openlocfilehash: 37b157268769ddcdeaef67b7e19cc7260cd392b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833644"
---
# Distribuzione locale per Surface Hub in un ambiente a foresta singola


Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a foresta singola.

In presenza di una distribuzione locale a foresta singola con Microsoft Exchange 2013 o versioni successive e Skype for Business 2013 o versioni successive, puoi [usare gli script di PowerShell forniti](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) per creare gli account del dispositivo. Se usi una distribuzione a più foreste, vedi [Distribuzione locale per Surface Hub in un ambiente a più foreste](on-premises-deployment-surface-hub-multi-forest.md).

1. Avvia una sessione di PowerShell remota da un PC e connettiti a Exchange.

   Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.

   Tieni presente che `$strExchangeServer` è il nome di dominio completo (FQDN) del server Exchange, mentre `$strLyncFQDN` è il nome di dominio completo del tuo server Skype for Business.

   ```PowerShell
   Set-ExecutionPolicy Unrestricted
   $org='contoso.microsoft.com'
   $cred=Get-Credential $admin@$org
   $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $cred -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
   $sessLync = New-PSSession -Credential $cred -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
   Import-PSSession $sessExchange
   Import-PSSession $sessLync
   ```

2. Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente. In questo modo l'account potrà essere autenticato in Surface Hub.

   Se devi modificare una cassetta postale delle risorse esistente:

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   Se devi creare una nuova cassetta postale delle risorse:

   ```PowerShell
   New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
> [!IMPORTANT] 
> È necessario che l'autenticazione di base della directory virtuale di ActiveSync sia abilitata perché l'hub Surface non è in grado di eseguire l'autenticazione usando altri metodi di autenticazione.

3. Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

   I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False. Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.

   Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs". Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
   ```

   Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo. I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse. Devi convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitarla e impostare di nuovo la password.

   ```PowerShell
   $acctUpn = Get-Mailbox -Identity "<mailbox identity>"
   $credNewAccount.Password = ConvertTo-SecureString -String <room mailbox password> -AsPlainText -Force
   Set-Mailbox $acctUpn -Type Regular
   Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy
   Set-Mailbox $acctUpn -Type Room
   Set-Mailbox $acctUpn -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```

4. È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni degli utenti. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).

   ```PowerShell
   Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell. Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).

   ```PowerShell
   Set-AdUser $acctUpn -PasswordNeverExpires $true
   ```

6. Abilita l'account in Active Directory in modo che esegua l'autenticazione nel dispositivo Surface Hub.

   ```PowerShell
   Set-AdUser $acctUpn -Enabled $true
   ```

7. Abilita l'account del dispositivo con Skype for Business abilitando l'account AD di Surface Hub in un pool Skype for Business Server:

   ```PowerShell
   Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
    -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
    -Identity HUB01
   ```

   Dovrai usare l'indirizzo SIP (Session Initiation Protocol) e il controller di dominio per il dispositivo Surface Hub, oltre all'identificatore del pool Skype for Business Server e all'identità utente.

8. FACOLTATIVO: puoi anche consentire al dispositivo Surface Hub di effettuare e ricevere chiamate PSTN (Public Switched Telephone Network) abilitando la funzionalità VoIP aziendale per il tuo account. La funzionalità VoIP aziendale non è un requisito per Surface Hub, ma se vuoi abilitare la funzionalità di composizione PSTN per il client Surface Hub, ecco come attivarla:

   ```PowerShell
   Set-CsMeetingRoom  -Identity HUB01 -DomainController DC-ND-001.contoso.com -LineURI "tel:+14255550555;ext=50555"  -EnterpriseVoiceEnabled $true
   ```

   Anche in questo caso, è necessario sostituire gli esempi di Domain controller e numero di telefono forniti con le proprie informazioni. Il valore del parametro `$true` rimane invariato.
    

 ## Disabilitare la posta elettronica anonima e la messaggistica istantanea




Surface hub usa un account di dispositivo per inviare servizi di posta elettronica e di collaborazione (messaggistica istantanea, video, voce). Questo account di dispositivo viene usato come identità di origine (il partito "da") durante l'invio di posta elettronica, messaggistica istantanea e immissione delle chiamate. Dato che questo account non proviene da un singolo utente identificabile, viene considerato "anonimo" perché è stato originato dall'account del dispositivo Surface Hub.  

Si supponga di avere un criterio client per utente assegnato a ogni dispositivo della sala riunioni con un'identità di **SurfaceHubPolicy**. Per disabilitare la posta elettronica e la messaggistica anonima, è possibile aggiungere un clientPolicyEntry ai criteri client usando i comandi seguenti.

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $false
$clientPolicy = Get-CsClientPolicy -Identity SurfaceHubPolicy
$clientPolicy.PolicyEntry.Add($policyEntry)
Set-CsClientPolicy -Instance $clientPolicy
```

Per verificare che il criterio sia stato impostato:

```
Select-Object -InputObject $clientPolicy -Property PolicyEntry
```

L'output deve essere:

```
PolicyEntry
-----------
{Name=AllowResourceAccountSendMessage;Value=False}
```
    
    
Per modificare la voce dei criteri:

```
$policyEntry =  New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Replace = $policyEntry}
``` 
    
Per rimuovere la voce dei criteri:

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Remove = $policyEntry}
```

 






---
title: Distribuzione locale a più foreste (Surface Hub)
description: Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a più foreste.
keywords: distribuzione a più foreste, distribuzione locale, account del dispositivo, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 48fe874175a2c55b7e95ba0974cefe29f710c134
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833620"
---
# Distribuzione locale per Surface Hub in un ambiente a più foreste


Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a più foreste.

In presenza di una distribuzione locale a più foreste con Microsoft Exchange 2013 o versioni successive e Skype for Business 2013 o versioni successive, puoi [usare gli script di PowerShell forniti](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) per creare gli account del dispositivo. Se usi una distribuzione a foresta singola, vedi [Distribuzione locale per Surface Hub in un ambiente a foresta singola](on-premises-deployment-surface-hub-device-accounts.md).

1.  Avvia una sessione di PowerShell remota da un PC e connettiti a Exchange.

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

2.  Dopo aver stabilito una sessione, crea una nuova cassetta postale nella foresta delle risorse. In questo modo l’account potrà essere autenticato in Surface Hub.

    Se devi modificare una cassetta postale delle risorse esistente:

    ```PowerShell
    New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01"
    ```

3.  Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

    I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo associati a criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su **False**. Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.

    Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato “Surface Hubs”. Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

    ```PowerShell
    $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
    ```

    Dopo aver creato criteri compatibili, dovrai applicarli all’account del dispositivo. 

    ```PowerShell
    Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy -ActiveSyncEnabled $true
    Set-Mailbox $acctUpn -Type Room
    ```

4.  È possibile impostare varie proprietà di Exchange nell’account del dispositivo per migliorare l’esperienza per le riunioni degli utenti. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).

    ```PowerShell
    Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell. Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md). Questa proprietà deve essere impostata nella foresta degli utenti.

    ```PowerShell
    Set-AdUser $acctUpn -PasswordNeverExpires $true
    ```

6.  Abilita l’account in Active Directory in modo che esegua l’autenticazione nel dispositivo Surface Hub. Questa proprietà deve essere impostata nella foresta degli utenti.

    ```PowerShell
    Set-AdUser $acctUpn -Enabled $true
    ```

6. Ora devi modificare la cassetta postale della sala in una cassetta postale collegata:

    ```PowerShell
    $cred=Get-Credential AuthForest\ADAdmin
    Set-mailbox -Alias LinkedRoomTest1 -LinkedMasterAccount AuthForest\LinkedRoomTest1 -LinkedDomainController AuthForest-4939.AuthForest.extest.contoso.com -Name LinkedRoomTest1 -LinkedCredential $cred -Identity LinkedRoomTest1
    ```

7.  Abilita l’account del dispositivo con Skype for Business abilitando l’account AD di Surface Hub in un pool Skype for Business Server:

    ```PowerShell
    Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
     -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
     -Identity HUB01
    ```

    Dovrai usare l'indirizzo SIP (Session Initiation Protocol) e il controller di dominio per il dispositivo Surface Hub, oltre all'identificatore del pool Skype for Business Server e all'identità utente.


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
 






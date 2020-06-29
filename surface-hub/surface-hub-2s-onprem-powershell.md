---
title: Configurare gli account locali di Surface Hub 2S con PowerShell
description: Informazioni su come configurare gli account locali di Surface Hub 2S con PowerShell
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 6832f4e4b5bc307746ec5838c0f80d043a22021a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833999"
---
# Configurare gli account locali di Surface Hub 2S con PowerShell

## Connettersi a Exchange Server PowerShell

> [!IMPORTANT]
> È necessario il nome di dominio completo (FQDN) per il servizio di accesso client del server Exchange locale per alcuni di questi cmdlet.

```PowerShell
$ExchServer = Read-Host "Please Enter the FQDN of your Exchange Server"
$ExchSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://$ExchServer/PowerShell/ -Authentication Kerberos -Credential (Get-Credential)
Import-PSSession $ExchSession
```

## Creare l'account del dispositivo

```PowerShell
New-Mailbox -UserPrincipalName Hub01@contoso.com -Alias Hub01 -Name "Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

## Impostare l'elaborazione automatica del calendario

```PowerShell
Set-CalendarProcessing -Identity "HUB01@contoso.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

## Abilitare l'oggetto Skype for business

> [!NOTE]
> È importante conoscere il nome di dominio completo del pool di registrazione di Skype for business.

```PowerShell
Enable-CsMeetingRoom -Identity Contoso\HUB01 -SipAddressType emailaddress -RegistrarPool SfbIEFE01.contoso.local
```

## Criteri cassetta postale per dispositivi mobili

Potrebbe essere necessario creare un criterio cassetta postale di un dispositivo mobile (noto anche come criterio ActiveSync) per consentire all'hub Surface di connettersi all'ambiente online o locale.

## Creare un criterio per cassette postali per dispositivi mobili Surface Hub

```PowerShell
New-MobileDeviceMailboxPolicy -Name “Surface Hubs” -PasswordEnabled $false
```

## Impostazioni aggiuntive

Si consiglia di aggiungere un MailTip alle sale di Surface Hub in modo che gli utenti si ricordino di rendere la riunione una riunione Skype for business o teams:

```PowerShell
Set-Mailbox "Surface Hub 2S" -MailTip "This is a Surface Hub room. Please make sure this is a Microsoft Teams meeting."
```

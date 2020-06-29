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
# <span data-ttu-id="d405e-104">Configurare gli account locali di Surface Hub 2S con PowerShell</span><span class="sxs-lookup"><span data-stu-id="d405e-104">Configure Surface Hub 2S on-premises accounts with PowerShell</span></span>

## <span data-ttu-id="d405e-105">Connettersi a Exchange Server PowerShell</span><span class="sxs-lookup"><span data-stu-id="d405e-105">Connect to Exchange Server PowerShell</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d405e-106">È necessario il nome di dominio completo (FQDN) per il servizio di accesso client del server Exchange locale per alcuni di questi cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d405e-106">You'll need the Fully Qualified Domain Name (FQDN) for the Client Access service of the on-premises Exchange server for some of these cmdlets.</span></span>

```PowerShell
$ExchServer = Read-Host "Please Enter the FQDN of your Exchange Server"
$ExchSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri http://$ExchServer/PowerShell/ -Authentication Kerberos -Credential (Get-Credential)
Import-PSSession $ExchSession
```

## <span data-ttu-id="d405e-107">Creare l'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="d405e-107">Create the device account</span></span>

```PowerShell
New-Mailbox -UserPrincipalName Hub01@contoso.com -Alias Hub01 -Name "Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

## <span data-ttu-id="d405e-108">Impostare l'elaborazione automatica del calendario</span><span class="sxs-lookup"><span data-stu-id="d405e-108">Set automatic calendar processing</span></span>

```PowerShell
Set-CalendarProcessing -Identity "HUB01@contoso.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

## <span data-ttu-id="d405e-109">Abilitare l'oggetto Skype for business</span><span class="sxs-lookup"><span data-stu-id="d405e-109">Enable the Skype for Business object</span></span>

> [!NOTE]
> <span data-ttu-id="d405e-110">È importante conoscere il nome di dominio completo del pool di registrazione di Skype for business.</span><span class="sxs-lookup"><span data-stu-id="d405e-110">It is important that you know the FQDN of the Skype for Business Registrar Pool.</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity Contoso\HUB01 -SipAddressType emailaddress -RegistrarPool SfbIEFE01.contoso.local
```

## <span data-ttu-id="d405e-111">Criteri cassetta postale per dispositivi mobili</span><span class="sxs-lookup"><span data-stu-id="d405e-111">Mobile Device Mailbox Policy</span></span>

<span data-ttu-id="d405e-112">Potrebbe essere necessario creare un criterio cassetta postale di un dispositivo mobile (noto anche come criterio ActiveSync) per consentire all'hub Surface di connettersi all'ambiente online o locale.</span><span class="sxs-lookup"><span data-stu-id="d405e-112">You may need to create a Mobile Device Mailbox Policy (also known as ActiveSync Policy) to allow your Surface Hub to connect to your online or on-premises environment.</span></span>

## <span data-ttu-id="d405e-113">Creare un criterio per cassette postali per dispositivi mobili Surface Hub</span><span class="sxs-lookup"><span data-stu-id="d405e-113">Create a Surface Hub mobile device mailbox policy</span></span>

```PowerShell
New-MobileDeviceMailboxPolicy -Name “Surface Hubs” -PasswordEnabled $false
```

## <span data-ttu-id="d405e-114">Impostazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d405e-114">Additional settings</span></span>

<span data-ttu-id="d405e-115">Si consiglia di aggiungere un MailTip alle sale di Surface Hub in modo che gli utenti si ricordino di rendere la riunione una riunione Skype for business o teams:</span><span class="sxs-lookup"><span data-stu-id="d405e-115">It is recommended to add a MailTip to Surface Hub rooms so users remember to make the meeting a Skype for Business or Teams meeting:</span></span>

```PowerShell
Set-Mailbox "Surface Hub 2S" -MailTip "This is a Surface Hub room. Please make sure this is a Microsoft Teams meeting."
```

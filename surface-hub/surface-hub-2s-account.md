---
title: Creare un account dispositivo per Surface Hub 2S
description: Questa pagina descrive la procedura per la creazione dell'account di dispositivo Surface Hub 2S.
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
ms.openlocfilehash: 6d8c41872481d86316d8985871fe74823e005ed8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833801"
---
# <span data-ttu-id="97f2c-104">Creare un account dispositivo per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="97f2c-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="97f2c-105">La creazione di un account per dispositivi Surface Hub (nota anche come cassetta postale della sala) consente a Surface Hub 2S di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni usando Microsoft teams o Skype for business.</span><span class="sxs-lookup"><span data-stu-id="97f2c-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings using either Microsoft Teams or Skype for Business.</span></span> <span data-ttu-id="97f2c-106">Configurare l'account del dispositivo durante l'installazione della configurazione guidata.</span><span class="sxs-lookup"><span data-stu-id="97f2c-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="97f2c-107">Se necessario, è possibile modificarlo in un secondo momento (senza passare alla configurazione di OOBE).</span><span class="sxs-lookup"><span data-stu-id="97f2c-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="97f2c-108">Diversamente dalle cassette postali standard che rimangono disabilitate per impostazione predefinita, è necessario abilitare l'account di dispositivo Surface Hub 2S per accedere a Microsoft teams e Skype for business.</span><span class="sxs-lookup"><span data-stu-id="97f2c-108">Unlike standard Room mailboxes that remain disabled by default, you need to enable the Surface Hub 2S device account to sign on to Microsoft Teams and Skype for Business.</span></span> <span data-ttu-id="97f2c-109">Surface Hub 2S si basa su Exchange ActiveSync, che richiede un criterio cassetta postale di ActiveSync nell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="97f2c-109">Surface Hub 2S relies on Exchange ActiveSync, which requires an ActiveSync mailbox policy on the device account.</span></span> <span data-ttu-id="97f2c-110">Applicare il criterio cassetta postale di ActiveSync predefinito incluso in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="97f2c-110">Apply the default ActiveSync mailbox policy that comes with Exchange Online.</span></span>

<span data-ttu-id="97f2c-111">Creare l'account usando l'interfaccia di amministrazione di Microsoft 365 o usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97f2c-111">Create the account by using the Microsoft 365 admin center or by using PowerShell.</span></span> <span data-ttu-id="97f2c-112">È possibile usare PowerShell di Exchange Online per configurare caratteristiche specifiche, tra cui:</span><span class="sxs-lookup"><span data-stu-id="97f2c-112">You can use Exchange Online PowerShell to configure specific features including:</span></span>

- <span data-ttu-id="97f2c-113">Elaborazione del calendario per ogni account di dispositivo hub Surface.</span><span class="sxs-lookup"><span data-stu-id="97f2c-113">Calendar processing for every Surface Hub device account.</span></span>
- <span data-ttu-id="97f2c-114">Risposte automatiche personalizzate alle richieste di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="97f2c-114">Custom auto replies to scheduling requests.</span></span>
- <span data-ttu-id="97f2c-115">Se il criterio cassetta postale di ActiveSync predefinito è già stato modificato da un altro utente o da un altro processo, è probabile che sia necessario creare e assegnare un nuovo criterio cassetta postale di ActiveSync.</span><span class="sxs-lookup"><span data-stu-id="97f2c-115">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!NOTE]  
> <span data-ttu-id="97f2c-116">L'account di dispositivo Surface Hub non supporta i provider di identità federati di terze parti e deve essere un account Active Directory o Azure Active Directory standard.</span><span class="sxs-lookup"><span data-stu-id="97f2c-116">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <span data-ttu-id="97f2c-117">Creare un account con l'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="97f2c-117">Create account using Microsoft 365 admin center</span></span>

1. <span data-ttu-id="97f2c-118">Nell'interfaccia di amministrazione di Microsoft 365 accedere a **risorse** e scegliere **sale & attrezzature** e quindi selezionare **+ sala**.</span><span class="sxs-lookup"><span data-stu-id="97f2c-118">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Room**.</span></span>

2. <span data-ttu-id="97f2c-119">Specificare un nome e un indirizzo di posta elettronica per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="97f2c-119">Provide a name and email address for the device account.</span></span> <span data-ttu-id="97f2c-120">Lascia invariate le impostazioni rimanenti nello stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="97f2c-120">Leave remaining settings unchanged in the default state.</span></span>

   ![Specificare un nome e un indirizzo di posta elettronica](images/sh2-account2.png)

   ![Lascia invariate le impostazioni rimanenti nello stato predefinito](images/sh2-account3.png)

3. <span data-ttu-id="97f2c-123">Impostare la password per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="97f2c-123">Set the password for the device account.</span></span> <span data-ttu-id="97f2c-124">Per impostare la password, scegliere **utenti** e quindi selezionare **utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="97f2c-124">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="97f2c-125">Ora cerca l'utente appena creato per impostare la password.</span><span class="sxs-lookup"><span data-stu-id="97f2c-125">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="97f2c-126">Assicurati di **non** selezionare l'opzione imposta l' **utente come modificarne la password al primo accesso.**</span><span class="sxs-lookup"><span data-stu-id="97f2c-126">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![Impostare la password per l'account del dispositivo](images/sh2-account4.png)

4. <span data-ttu-id="97f2c-128">Assegnare la sala con una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="97f2c-128">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="97f2c-129">È consigliabile assegnare la licenza per la **sala riunioni** di Office 365, una nuova opzione che consente automaticamente l'account per Skype for business online e Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="97f2c-129">It’s recommended to assign the Office 365 **Meeting Room** license, a new option that automatically enables the account for Skype for Business Online and Microsoft Teams.</span></span>

   ![Assegnare la licenza di Office 365](images/sh2-account5.png)

### <span data-ttu-id="97f2c-131">Finalizzare la configurazione tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="97f2c-131">Finalize setup via PowerShell</span></span>

- <span data-ttu-id="97f2c-132">**Skype for business:** Solo per Skype for business (locale o online), puoi abilitare l'oggetto Skype for business eseguendo **Enable-CsMeetingRoom** per abilitare funzionalità come la richiesta della sala riunioni per l'audio e il blocco per le lobby.</span><span class="sxs-lookup"><span data-stu-id="97f2c-132">**Skype for Business:** For Skype for Business only (on-premises or online), you can enable the Skype for Business object by running **Enable-CsMeetingRoom** to enable features such as Meeting room prompt for audio and Lobby hold.</span></span>

- <span data-ttu-id="97f2c-133">**Calendario di Microsoft teams e Skype for business:** Impostare l' [**elaborazione automatica del calendario**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) per questo account.</span><span class="sxs-lookup"><span data-stu-id="97f2c-133">**Microsoft Teams and Skype for Business Calendar:** Set [**Calendar Auto processing**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) for this account.</span></span>

## <span data-ttu-id="97f2c-134">Creare un account tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="97f2c-134">Create account using PowerShell</span></span>

<span data-ttu-id="97f2c-135">Invece di usare il portale di interfaccia di amministrazione Microsoft, è possibile creare l'account usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97f2c-135">Instead of using the Microsoft Admin Center portal, you can create the account using PowerShell.</span></span>

### <span data-ttu-id="97f2c-136">Connettersi a PowerShell di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="97f2c-136">Connect to Exchange Online PowerShell</span></span>

```powershell
$365Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential (Get-Credential) -Authentication Basic –AllowRedirection
$ImportResults = Import-PSSession $365Session
```

### <span data-ttu-id="97f2c-137">Creare una nuova cassetta postale della sala</span><span class="sxs-lookup"><span data-stu-id="97f2c-137">Create a new Room mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID account@YourDomain.com -Alias SurfaceHub2S -Name SurfaceHub2S -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString  -String "<Enter Strong Password>" -AsPlainText -Force)
```

### <span data-ttu-id="97f2c-138">Impostare l'elaborazione automatica del calendario</span><span class="sxs-lookup"><span data-stu-id="97f2c-138">Set Calendar auto-processing</span></span>

```powershell
Set-CalendarProcessing -Identity "account@YourDomain.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

### <span data-ttu-id="97f2c-139">Assegnare una licenza</span><span class="sxs-lookup"><span data-stu-id="97f2c-139">Assign a license</span></span>

```powershell
Connect-MsolService
Set-Msoluser -UserPrincipalName account@YourDomain.com -UsageLocation IE
Set-MsolUserLicense -UserPrincipalName "account@YourDomain.com" -AddLicenses "contoso:MEETING_ROOM"
```

## <span data-ttu-id="97f2c-140">Connettersi a Skype for business online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="97f2c-140">Connect to Skype for Business Online using PowerShell</span></span>

### <span data-ttu-id="97f2c-141">Installare prerequisiti</span><span class="sxs-lookup"><span data-stu-id="97f2c-141">Install pre-requisites</span></span>

- [<span data-ttu-id="97f2c-142">Visual C++ 2017 ridistribuibile</span><span class="sxs-lookup"><span data-stu-id="97f2c-142">Visual C++ 2017 Redistributable</span></span>](https://aka.ms/vs/15/release/vc_redist.x64.exe)
- [<span data-ttu-id="97f2c-143">Modulo di PowerShell per Skype for business online</span><span class="sxs-lookup"><span data-stu-id="97f2c-143">Skype for Business Online PowerShell Module</span></span>](https://www.microsoft.com/download/confirmation.aspx?id=39366)

```powershell
Import-Module LyncOnlineConnector
$SfBSession = New-CsOnlineSession -Credential (Get-Credential)
Import-PSSession $SfBSession -AllowClobber

# Enable the Skype for Business meeting room
Enable-CsMeetingRoom -Identity account@YourDomain.com -RegistrarPool(Get-CsTenant).Registrarpool -SipAddressType EmailAddress
```

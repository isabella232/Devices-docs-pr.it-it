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
ms.date: 12/07/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e171d7c2db8a0d69594ca8d5f3a54f33ecebc9ae
ms.sourcegitcommit: dc08a2096a1fe955eb67e736e2a4453f75e926be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "11196729"
---
# <span data-ttu-id="5cf60-104">Creare un account dispositivo per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="5cf60-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="5cf60-105">La creazione di un account per dispositivi Surface Hub (nota anche come cassetta postale della sala) consente a Surface Hub 2S di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni usando Microsoft teams o Skype for business.</span><span class="sxs-lookup"><span data-stu-id="5cf60-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings using either Microsoft Teams or Skype for Business.</span></span> <span data-ttu-id="5cf60-106">Configurare l'account del dispositivo durante l'installazione della configurazione guidata.</span><span class="sxs-lookup"><span data-stu-id="5cf60-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="5cf60-107">Se necessario, è possibile modificarlo in un secondo momento (senza passare alla configurazione di OOBE).</span><span class="sxs-lookup"><span data-stu-id="5cf60-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="5cf60-108">Diversamente dalle cassette postali standard che rimangono disabilitate per impostazione predefinita, è necessario abilitare l'account di dispositivo Surface Hub 2S per accedere a Microsoft teams e Skype for business.</span><span class="sxs-lookup"><span data-stu-id="5cf60-108">Unlike standard Room mailboxes that remain disabled by default, you need to enable the Surface Hub 2S device account to sign on to Microsoft Teams and Skype for Business.</span></span> <span data-ttu-id="5cf60-109">Surface Hub 2S si basa su Exchange ActiveSync, che richiede un criterio cassetta postale di ActiveSync nell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5cf60-109">Surface Hub 2S relies on Exchange ActiveSync, which requires an ActiveSync mailbox policy on the device account.</span></span> <span data-ttu-id="5cf60-110">Applicare il criterio cassetta postale di ActiveSync predefinito incluso in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5cf60-110">Apply the default ActiveSync mailbox policy that comes with Exchange Online.</span></span>

<span data-ttu-id="5cf60-111">Creare l'account usando l'interfaccia di amministrazione di Microsoft 365 o usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cf60-111">Create the account by using the Microsoft 365 admin center or by using PowerShell.</span></span> <span data-ttu-id="5cf60-112">È possibile usare PowerShell di Exchange Online per configurare caratteristiche specifiche, tra cui:</span><span class="sxs-lookup"><span data-stu-id="5cf60-112">You can use Exchange Online PowerShell to configure specific features including:</span></span>

- <span data-ttu-id="5cf60-113">Elaborazione del calendario per ogni account di dispositivo hub Surface.</span><span class="sxs-lookup"><span data-stu-id="5cf60-113">Calendar processing for every Surface Hub device account.</span></span>
- <span data-ttu-id="5cf60-114">Risposte automatiche personalizzate alle richieste di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="5cf60-114">Custom auto replies to scheduling requests.</span></span>
- <span data-ttu-id="5cf60-115">Se il criterio cassetta postale di ActiveSync predefinito è già stato modificato da un altro utente o da un altro processo, è probabile che sia necessario creare e assegnare un nuovo criterio cassetta postale di ActiveSync.</span><span class="sxs-lookup"><span data-stu-id="5cf60-115">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!NOTE]  
> <span data-ttu-id="5cf60-116">L'account di dispositivo Surface Hub non supporta i provider di identità federati di terze parti e deve essere un account Active Directory o Azure Active Directory standard.</span><span class="sxs-lookup"><span data-stu-id="5cf60-116">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <span data-ttu-id="5cf60-117">Creare un account con l'interfaccia di amministrazione di Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5cf60-117">Create account using Microsoft 365 admin center</span></span>

1. <span data-ttu-id="5cf60-118">Nell'interfaccia di amministrazione di Microsoft 365 accedere a **risorse** e scegliere **sale & attrezzature** e quindi selezionare **+ sala**.</span><span class="sxs-lookup"><span data-stu-id="5cf60-118">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Room**.</span></span>

2. <span data-ttu-id="5cf60-119">Specificare un nome e un indirizzo di posta elettronica per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5cf60-119">Provide a name and email address for the device account.</span></span> <span data-ttu-id="5cf60-120">Lascia invariate le impostazioni rimanenti nello stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="5cf60-120">Leave remaining settings unchanged in the default state.</span></span>

   ![Specificare un nome e un indirizzo di posta elettronica](images/sh2-account2.png)

   ![Lascia invariate le impostazioni rimanenti nello stato predefinito](images/sh2-account3.png)

3. <span data-ttu-id="5cf60-123">Impostare la password per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5cf60-123">Set the password for the device account.</span></span> <span data-ttu-id="5cf60-124">Per impostare la password, scegliere **utenti** e quindi selezionare **utenti attivi**.</span><span class="sxs-lookup"><span data-stu-id="5cf60-124">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="5cf60-125">Ora cerca l'utente appena creato per impostare la password.</span><span class="sxs-lookup"><span data-stu-id="5cf60-125">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="5cf60-126">Assicurati di **non** selezionare l'opzione imposta l' **utente come modificarne la password al primo accesso.**</span><span class="sxs-lookup"><span data-stu-id="5cf60-126">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![Impostare la password per l'account del dispositivo](images/sh2-account4.png)

4. <span data-ttu-id="5cf60-128">Assegnare la sala con una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5cf60-128">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="5cf60-129">È consigliabile assegnare la licenza per la **sala riunioni** di Office 365, una nuova opzione che consente automaticamente l'account per Skype for business online e Microsoft teams.</span><span class="sxs-lookup"><span data-stu-id="5cf60-129">It’s recommended to assign the Office 365 **Meeting Room** license, a new option that automatically enables the account for Skype for Business Online and Microsoft Teams.</span></span>

   ![Assegnare la licenza di Office 365](images/sh2-account5.png)

### <span data-ttu-id="5cf60-131">Finalizzare la configurazione tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cf60-131">Finalize setup via PowerShell</span></span>

- <span data-ttu-id="5cf60-132">**Calendario di Microsoft teams e Skype for business:** Impostare l' [**elaborazione automatica del calendario**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) per questo account.</span><span class="sxs-lookup"><span data-stu-id="5cf60-132">**Microsoft Teams and Skype for Business Calendar:** Set [**Calendar Auto processing**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) for this account.</span></span>

## <span data-ttu-id="5cf60-133">Creare un account tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cf60-133">Create account using PowerShell</span></span>

<span data-ttu-id="5cf60-134">Invece di usare il portale di interfaccia di amministrazione Microsoft, è possibile creare l'account usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5cf60-134">Instead of using the Microsoft Admin Center portal, you can create the account using PowerShell.</span></span>

### <span data-ttu-id="5cf60-135">Connettersi a PowerShell di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5cf60-135">Connect to Exchange Online PowerShell</span></span>

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### <span data-ttu-id="5cf60-136">Creare una cassetta postale</span><span class="sxs-lookup"><span data-stu-id="5cf60-136">Create mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### <span data-ttu-id="5cf60-137">Impostare l'elaborazione automatica del calendario</span><span class="sxs-lookup"><span data-stu-id="5cf60-137">Set Calendar auto-processing</span></span>

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### <span data-ttu-id="5cf60-138">Abilitare ActiveSync se è necessaria l'uso dell'app di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="5cf60-138">Enable ActiveSync if use of email app is required</span></span>

 <span data-ttu-id="5cf60-139">I criteri di ActiveSync predefiniti funzioneranno se unchnaged.</span><span class="sxs-lookup"><span data-stu-id="5cf60-139">The default ActiveSync Policy will work if unchnaged.</span></span> <span data-ttu-id="5cf60-140">In caso contrario, crea un nuovo criterio e assegna.</span><span class="sxs-lookup"><span data-stu-id="5cf60-140">Otherwise create a new Policy and assign.</span></span>

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```
### <span data-ttu-id="5cf60-141">Connettiti ad Azure AD</span><span class="sxs-lookup"><span data-stu-id="5cf60-141">Connect to Azure AD</span></span>

```powershell
Connect-AzureAD
```

### <span data-ttu-id="5cf60-142">Assegnare una licenza</span><span class="sxs-lookup"><span data-stu-id="5cf60-142">Assign a license</span></span>

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### <span data-ttu-id="5cf60-143">Verificare la disponibilità di licenze disponibili</span><span class="sxs-lookup"><span data-stu-id="5cf60-143">Check for available licenses</span></span>

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```
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
# <span data-ttu-id="60f83-104">Distribuzione online con Office 365 (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="60f83-104">Online deployment with Office 365 (Surface Hub)</span></span>


<span data-ttu-id="60f83-105">Questo argomento contiene le istruzioni per l&#39;aggiunta di un account del dispositivo per Microsoft Surface Hub nel caso di una distribuzione online pura.</span><span class="sxs-lookup"><span data-stu-id="60f83-105">This topic has instructions for adding a device account for your Microsoft Surface Hub when you have a pure, online deployment.</span></span>

<span data-ttu-id="60f83-106">In presenza di una distribuzione online pura (Office 365), puoi [usare gli script di PowerShell forniti](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts) per creare gli account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60f83-106">If you have a pure, online (O365) deployment, then you can [use the provided PowerShell scripts](appendix-a-powershell-scripts-for-surface-hub.md#create-os356-ps-scripts) to create device accounts.</span></span> 

1. <span data-ttu-id="60f83-107">Avvia una sessione di PowerShell remota su un PC e connettiti a Exchange.</span><span class="sxs-lookup"><span data-stu-id="60f83-107">Start a remote PowerShell session on a PC and connect to Exchange.</span></span>

   <span data-ttu-id="60f83-108">Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.</span><span class="sxs-lookup"><span data-stu-id="60f83-108">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

   ```PowerShell
   Set-ExecutionPolicy RemoteSigned
   $org='contoso.microsoft.com'
   $cred=Get-Credential admin@$org
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```

2. <span data-ttu-id="60f83-109">Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente.</span><span class="sxs-lookup"><span data-stu-id="60f83-109">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="60f83-110">In questo modo l'account potrà essere autenticato in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="60f83-110">This will allow the account to authenticate into the Surface Hub.</span></span>

   <span data-ttu-id="60f83-111">Se devi modificare una cassetta postale delle risorse esistente:</span><span class="sxs-lookup"><span data-stu-id="60f83-111">If you're changing an existing resource mailbox:</span></span>

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   <span data-ttu-id="60f83-112">Se devi creare una nuova cassetta postale delle risorse:</span><span class="sxs-lookup"><span data-stu-id="60f83-112">If you’re creating a new resource mailbox:</span></span>

   ```PowerShell
   New-Mailbox -MicrosoftOnlineServicesID HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

3. <span data-ttu-id="60f83-113">Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.</span><span class="sxs-lookup"><span data-stu-id="60f83-113">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="60f83-114">I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False.</span><span class="sxs-lookup"><span data-stu-id="60f83-114">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="60f83-115">Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.</span><span class="sxs-lookup"><span data-stu-id="60f83-115">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

   <span data-ttu-id="60f83-116">Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs".</span><span class="sxs-lookup"><span data-stu-id="60f83-116">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="60f83-117">Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60f83-117">Once it’s created, you can apply the same policy to other device accounts.</span></span>

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false -AllowNonProvisionableDevices $True
   ```

   <span data-ttu-id="60f83-118">Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="60f83-118">Once you have a compatible policy, then you will need to apply the policy to the device account.</span></span>

   ```PowerShell
   Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.Id
   ```

4. <span data-ttu-id="60f83-119">È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="60f83-119">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="60f83-120">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .</span><span class="sxs-lookup"><span data-stu-id="60f83-120">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

   ```PowerShell
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. <span data-ttu-id="60f83-121">Connettiti ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="60f83-121">Connect to Azure AD.</span></span>
    
   <span data-ttu-id="60f83-122">È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2.</span><span class="sxs-lookup"><span data-stu-id="60f83-122">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="60f83-123">Da un prompt dei comandi con privilegi elevati eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="60f83-123">In an elevated powershell prompt run the following command :</span></span>
    
   ```PowerShell
   Install-Module -Name AzureAD
   ```
   <span data-ttu-id="60f83-124">Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account.</span><span class="sxs-lookup"><span data-stu-id="60f83-124">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="60f83-125">Puoi eseguire questo cmdlet per la connessione.</span><span class="sxs-lookup"><span data-stu-id="60f83-125">You can run this cmdlet to connect.</span></span>

   ```PowerShell
   Import-Module AzureAD
   Connect-AzureAD -Credential $cred
   ```

6. <span data-ttu-id="60f83-126">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="60f83-126">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="60f83-127">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="60f83-127">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

   ```PowerShell
   Set-AzureADUser -ObjectId "HUB01@contoso.com" -PasswordPolicies "DisablePasswordExpiration"
   ```

7. <span data-ttu-id="60f83-128">Surface Hub richiede una licenza per la funzionalità Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="60f83-128">Surface Hub requires a license for Skype for Business functionality.</span></span> <span data-ttu-id="60f83-129">Per abilitare Skype for Business, l'ambiente deve soddisfare i [prerequisiti di Skype for Business online](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online).</span><span class="sxs-lookup"><span data-stu-id="60f83-129">In order to enable Skype for Business, your environment will need to meet the [prerequisites for Skype for Business online](hybrid-deployment-surface-hub-device-accounts.md#skype-for-business-online).</span></span>
   
   <span data-ttu-id="60f83-130">Puoi quindi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.</span><span class="sxs-lookup"><span data-stu-id="60f83-130">Next, you can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

   <span data-ttu-id="60f83-131">Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.</span><span class="sxs-lookup"><span data-stu-id="60f83-131">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

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

8. <span data-ttu-id="60f83-132">Abilita l'account del dispositivo con Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="60f83-132">Enable the device account with Skype for Business.</span></span>
   <span data-ttu-id="60f83-133">Se non è installato il modulo PowerShell di Skype for Business, [scarica il modulo di Windows PowerShell di Skype for Business online](https://www.microsoft.com/download/details.aspx?id=39366).</span><span class="sxs-lookup"><span data-stu-id="60f83-133">If the Skype for Business PowerShell module is not installed, [download the Skype for Business Online Windows PowerShell Module](https://www.microsoft.com/download/details.aspx?id=39366).</span></span> 

   - <span data-ttu-id="60f83-134">Per iniziare, crea una sessione di PowerShell remota da un PC.</span><span class="sxs-lookup"><span data-stu-id="60f83-134">Start by creating a remote PowerShell session from a PC.</span></span>

     ```PowerShell
     Import-Module SkypeOnlineConnector  
     $cssess=New-CsOnlineSession -Credential $cred  
     Import-PSSession $cssess -AllowClobber
     ```

   - <span data-ttu-id="60f83-135">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet (ad esempio, <em>alice@contoso.com</em>):</span><span class="sxs-lookup"><span data-stu-id="60f83-135">Next, if you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet (for example, <em>alice@contoso.com</em>):</span></span>

       ```PowerShell
       Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool
       ```
       <span data-ttu-id="60f83-136">Oppure impostando una variabile</span><span class="sxs-lookup"><span data-stu-id="60f83-136">OR by setting a variable</span></span>
        
       ```PowerShell
    $strRegistrarPool = Get-CsOnlineUser -Identity 'alice@contoso.com' | fl registrarpool | out-string
    $strRegistrarPool = $strRegistrarPool.Substring($strRegistrarPool.IndexOf(':') + 2)
       ```
        
   - <span data-ttu-id="60f83-137">Abilitare l'account di Surface Hub con il cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="60f83-137">Enable the Surface Hub account with the following cmdlet:</span></span>
      
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool yourRegistrarPool -SipAddressType EmailAddress
       ```
        
       <span data-ttu-id="60f83-138">O utilizzando la variabile $strRegistarPool dall'alto</span><span class="sxs-lookup"><span data-stu-id="60f83-138">OR using the $strRegistarPool variable from above</span></span>
        
       ```PowerShell
       Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool $strRegistrarPool -SipAddressType EmailAddress
       ```

<span data-ttu-id="60f83-139">Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.</span><span class="sxs-lookup"><span data-stu-id="60f83-139">For validation, you should be able to use any Skype for Business client (PC, Android, etc) to sign in to this account.</span></span>






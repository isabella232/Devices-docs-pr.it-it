---
title: Distribuzione ibrida (Surface Hub)
description: La distribuzione ibrida richiede un'elaborazione speciale per poter configurare un account del dispositivo per Microsoft Surface Hub.
ms.assetid: 7BFBB7BE-F587-422E-9CE4-C9DDF829E4F1
ms.reviewer: ''
manager: laurawi
keywords: distribuzione ibrida, account del dispositivo per Surface Hub, Exchange ospitato in locale, Exchange ospitato online
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/30/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7444c3f31f7a144200a0b8b89cfa509ef7a7afc4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833669"
---
# <span data-ttu-id="5525d-104">Distribuzione ibrida (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="5525d-104">Hybrid deployment (Surface Hub)</span></span>

<span data-ttu-id="5525d-105">La distribuzione ibrida richiede un'elaborazione speciale per poter configurare un account del dispositivo per Microsoft Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-105">A hybrid deployment requires special processing to set up a device account for your Microsoft Surface Hub.</span></span> <span data-ttu-id="5525d-106">Se stai usando una distribuzione ibrida in cui l'organizzazione offre una combinazione di vari servizi, in parte ospitati in locale e in parte ospitati online, la configurazione dipenderà da dove sono ospitati i diversi servizi.</span><span class="sxs-lookup"><span data-stu-id="5525d-106">If you’re using a hybrid deployment, in which your organization has a mix of services, with some hosted on-premises and some hosted online, then your configuration will depend on where each service is hosted.</span></span> <span data-ttu-id="5525d-107">Questo argomento illustra le distribuzioni ibride per [Exchange ospitato in locale](#exchange-on-premises), [Exchange ospitato online](#exchange-online), Skype for Business in locale, Skype for Business online e Skype for Business con configurazione ibrida.</span><span class="sxs-lookup"><span data-stu-id="5525d-107">This topic covers hybrid deployments for [Exchange hosted on-premises](#exchange-on-premises), [Exchange hosted online](#exchange-online), Skype for Business on-premises, Skype for Business online, and Skype for Business hybrid.</span></span> <span data-ttu-id="5525d-108">Dal momento che esistono molte varianti in questo tipo di distribuzione, non è possibile fornire istruzioni dettagliate per tutte le tipologie.</span><span class="sxs-lookup"><span data-stu-id="5525d-108">Because there are so many different variations in this type of deployment, it's not possible to provide detailed instructions for all of them.</span></span> <span data-ttu-id="5525d-109">Il processo seguente è applicabile a gran parte delle configurazioni.</span><span class="sxs-lookup"><span data-stu-id="5525d-109">The following process will work for many configurations.</span></span> <span data-ttu-id="5525d-110">Se il processo non è adatto per la tua configurazione, ti consigliamo di usare PowerShell (vedi [Appendice: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)) per ottenere lo stesso risultato, come descritto in questo articolo, e per altre opzioni di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5525d-110">If the process isn't right for your setup, we recommend that you use PowerShell (see [Appendix: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)) to achieve the same end result as documented here, and for other deployment options.</span></span> <span data-ttu-id="5525d-111">Usa quindi lo script di PowerShell fornito per verificare la tua configurazione di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-111">You should then use the provided Powershell script to verify your Surface Hub setup.</span></span> <span data-ttu-id="5525d-112">(Vedi [Script di verifica degli account](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts).)</span><span class="sxs-lookup"><span data-stu-id="5525d-112">(See [Account Verification Script](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts).)</span></span>

> [!NOTE]
> <span data-ttu-id="5525d-113">In un ambiente ibrido di Exchange seguire i passaggi per [Exchange locale](#exchange-on-premises).</span><span class="sxs-lookup"><span data-stu-id="5525d-113">In an Exchange hybrid environment, follow the steps for [Exchange on-premises](#exchange-on-premises).</span></span> <span data-ttu-id="5525d-114">Per trasferire oggetti di Exchange in Office 365, usare il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps) .</span><span class="sxs-lookup"><span data-stu-id="5525d-114">To move Exchange objects to Office 365, use the [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps) cmdlet.</span></span>

## <span data-ttu-id="5525d-115">Exchange in locale</span><span class="sxs-lookup"><span data-stu-id="5525d-115">Exchange on-premises</span></span>

<span data-ttu-id="5525d-116">Usa questa procedura se usi Exchange in locale.</span><span class="sxs-lookup"><span data-stu-id="5525d-116">Use this procedure if you use Exchange on-premises.</span></span>

1. <span data-ttu-id="5525d-117">Per eseguire questa procedura, userai gli strumenti di amministrazione di AD per aggiungere un indirizzo e-mail per il tuo account di dominio locale.</span><span class="sxs-lookup"><span data-stu-id="5525d-117">For this procedure, you'll be using AD admin tools to add an email address for your on-premises domain account.</span></span> <span data-ttu-id="5525d-118">Questo account verrà sincronizzato con Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-118">This account will be synced to Office 365.</span></span>

- <span data-ttu-id="5525d-119">Nello strumento di AD **Utenti e computer di Active Directory** fai clic con il pulsante destro del mouse sulla cartella o sull'unità organizzativa in cui verranno creati i tuoi account di Surface Hub, fai clic su **Nuovo**e quindi su **Utente**.</span><span class="sxs-lookup"><span data-stu-id="5525d-119">In **Active Directory Users and Computers** AD tool, right-click on the folder or Organizational Unit that your Surface Hub accounts will be created in, click **New**, and **User**.</span></span>
- <span data-ttu-id="5525d-120">Digita il nome visualizzato dal cmdlet precedente nella casella **Nome completo** e l'alias nella casella **Nome accesso utente** .</span><span class="sxs-lookup"><span data-stu-id="5525d-120">Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box.</span></span> <span data-ttu-id="5525d-121">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5525d-121">Click **Next**.</span></span><p>

![Casella per un nuovo oggetto per creare un nuovo utente in Active Directory.](images/hybriddeployment-01a.png)

- <span data-ttu-id="5525d-123">Digita la password per questo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-123">Type the password for this account.</span></span> <span data-ttu-id="5525d-124">Dovrai digitarla di nuovo per la verifica.</span><span class="sxs-lookup"><span data-stu-id="5525d-124">You'll need to retype it for verification.</span></span> <span data-ttu-id="5525d-125">Assicurati che la casella di controllo **Nessuna scadenza password** sia l'unica opzione selezionata.</span><span class="sxs-lookup"><span data-stu-id="5525d-125">Make sure the **Password never expires** checkbox is the only option selected.</span></span>

> <span data-ttu-id="5525d-126">**Importante** La selezione dell'opzione **Nessuna scadenza password** è un requisito per Skype for Business in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-126">**Important** Selecting **Password never expires** is a requirement for Skype for Business on the Surface Hub.</span></span> <span data-ttu-id="5525d-127">Le regole del tuo dominio potrebbero vietare l'uso di password senza scadenza.</span><span class="sxs-lookup"><span data-stu-id="5525d-127">Your domain rules may prohibit passwords that don't expire.</span></span> <span data-ttu-id="5525d-128">In questo caso, dovrai creare un'eccezione per ogni account del dispositivo di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-128">If so, you'll need to create an exception for each Surface Hub device account.</span></span>

![Immagine che mostra la finestra di dialogo della password.](images/hybriddeployment-02a.png)

-   <span data-ttu-id="5525d-130">Fai clic su **Fine** per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-130">Click **Finish** to create the account.</span></span>

![Immagine con le opzioni per il nome di account, il nome di accesso e la password per il nuovo utente.](images/hybriddeployment-03a.png)

2. <span data-ttu-id="5525d-132">Abilita la cassetta postale remota.</span><span class="sxs-lookup"><span data-stu-id="5525d-132">Enable the remote mailbox.</span></span>

<span data-ttu-id="5525d-133">Apri Exchange Management Shell in locale con le autorizzazioni di amministratore ed esegui questo cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5525d-133">Open your on-premises Exchange Management Shell with administrator permissions, and run this cmdlet.</span></span>

```PowerShell
Enable-RemoteMailbox 'HUB01@contoso.com' -RemoteRoutingAddress 'HUB01@contoso.com' -Room
```

> [!NOTE]
> <span data-ttu-id="5525d-134">Se non disponi di un ambiente Exchange in locale per eseguire questo cmdlet, puoi apportare le stesse modifiche direttamente all'oggetto Active Directory per l'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-134">If you don't have an on-premises Exchange environment to run this cmdlet, you can make the same changes directly to the Active Directory object for the account.</span></span>
>
> <span data-ttu-id="5525d-135">msExchRemoteRecipientType = 33</span><span class="sxs-lookup"><span data-stu-id="5525d-135">msExchRemoteRecipientType = 33</span></span>
>
> <span data-ttu-id="5525d-136">msExchRecipientDisplayType = -2147481850</span><span class="sxs-lookup"><span data-stu-id="5525d-136">msExchRecipientDisplayType = -2147481850</span></span>
>
> <span data-ttu-id="5525d-137">msExchRecipientTypeDetails = 8589934592</span><span class="sxs-lookup"><span data-stu-id="5525d-137">msExchRecipientTypeDetails = 8589934592</span></span>

3. <span data-ttu-id="5525d-138">Dopo aver creato l'account, esegui una sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="5525d-138">After you've created the account, run a directory synchronization.</span></span> <span data-ttu-id="5525d-139">Al termine, accedere alla pagina utenti nell'interfaccia di amministrazione di Microsoft 365 e verificare che l'account creato nei passaggi precedenti sia stato unito a online.</span><span class="sxs-lookup"><span data-stu-id="5525d-139">When it's complete, go to the users page in your Microsoft 365 admin center and verify that the account created in the previous steps has merged to online.</span></span>

4. <span data-ttu-id="5525d-140">Connettiti a Microsoft Exchange Online e imposta alcune proprietà per l'account in Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-140">Connect to Microsoft Exchange Online and set some properties for the account in Office 365.</span></span>

<span data-ttu-id="5525d-141">Avvia una sessione remota di PowerShell in un PC e connettiti a Microsoft Exchange.</span><span class="sxs-lookup"><span data-stu-id="5525d-141">Start a remote PowerShell session on a PC and connect to Microsoft Exchange.</span></span> <span data-ttu-id="5525d-142">Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.</span><span class="sxs-lookup"><span data-stu-id="5525d-142">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

<span data-ttu-id="5525d-143">I passaggi successivi verranno eseguiti nel tuo tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-143">The next steps will be run on your Office 365 tenant.</span></span>

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri 'https://ps.outlook.com/powershell' -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

5. <span data-ttu-id="5525d-144">Crea un nuovo criterio di Exchange ActiveSync o usa un criterio esistente compatibile.</span><span class="sxs-lookup"><span data-stu-id="5525d-144">Create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

<span data-ttu-id="5525d-145">Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.</span><span class="sxs-lookup"><span data-stu-id="5525d-145">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy or use a compatible existing policy.</span></span>

<span data-ttu-id="5525d-146">I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False.</span><span class="sxs-lookup"><span data-stu-id="5525d-146">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="5525d-147">Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.</span><span class="sxs-lookup"><span data-stu-id="5525d-147">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

<span data-ttu-id="5525d-148">Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs".</span><span class="sxs-lookup"><span data-stu-id="5525d-148">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="5525d-149">Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5525d-149">Once it’s created, you can apply the same policy to other device accounts.</span></span>

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

<span data-ttu-id="5525d-150">Una volta che hai un criterio compatibile, dovrai applicare il criterio all'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5525d-150">Once you have a compatible policy, you will need to apply the policy to the device account.</span></span> 

```PowerShell
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
```

6. <span data-ttu-id="5525d-151">Imposta le proprietà di Exchange.</span><span class="sxs-lookup"><span data-stu-id="5525d-151">Set Exchange properties.</span></span>

<span data-ttu-id="5525d-152">Imposta le proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="5525d-152">Setting Exchange properties on the device account to improve the meeting experience.</span></span> <span data-ttu-id="5525d-153">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .</span><span class="sxs-lookup"><span data-stu-id="5525d-153">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse 'This is a Surface Hub room!'
```

7. <span data-ttu-id="5525d-154">Connettiti ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5525d-154">Connect to Azure AD.</span></span>

<span data-ttu-id="5525d-155">È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2.</span><span class="sxs-lookup"><span data-stu-id="5525d-155">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="5525d-156">In un prompt di PowerShell con privilegi elevati eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5525d-156">In an elevated PowerShell prompt, run the following command:</span></span>

```PowerShell
Install-Module -Name AzureAD
```

<span data-ttu-id="5525d-157">Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-157">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="5525d-158">Puoi eseguire questo cmdlet per la connessione.</span><span class="sxs-lookup"><span data-stu-id="5525d-158">You can run this cmdlet to connect.</span></span>

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. <span data-ttu-id="5525d-159">Assegna una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-159">Assign an Office 365 license.</span></span>

<span data-ttu-id="5525d-160">L'account del dispositivo deve avere una licenza valida per Office 365 (O365). In caso contrario, Exchange e Skype for Business non funzioneranno.</span><span class="sxs-lookup"><span data-stu-id="5525d-160">The device account needs to have a valid Office 365 (O365) license, or Exchange and Skype for Business will not work.</span></span> <span data-ttu-id="5525d-161">Se hai la licenza, devi assegnare una località di utilizzo al tuo account del dispositivo, che servirà per determinare gli SKU di licenza disponibili per il tuo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-161">If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account.</span></span>

<span data-ttu-id="5525d-162">Puoi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.</span><span class="sxs-lookup"><span data-stu-id="5525d-162">You can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

<span data-ttu-id="5525d-163">Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.</span><span class="sxs-lookup"><span data-stu-id="5525d-163">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

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

<span data-ttu-id="5525d-164">Abilita quindi l'account del dispositivo con [Skype for Business online](#skype-for-business-online), [Skype for Business in locale](#skype-for-business-on-premises) o [Skype for Business con configurazione ibrida](#skype-for-business-hybrid).</span><span class="sxs-lookup"><span data-stu-id="5525d-164">Next, you enable the device account with [Skype for Business Online](#skype-for-business-online), [Skype for Business on-premises](#skype-for-business-on-premises), or [Skype for Business hybrid](#skype-for-business-hybrid).</span></span>

### <span data-ttu-id="5525d-165">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5525d-165">Skype for Business Online</span></span>

<span data-ttu-id="5525d-166">Per abilitare Skype for Business online, gli utenti tenant devono avere cassette postali Exchange (è necessaria almeno una cassetta postale di Exchange nel tenant).</span><span class="sxs-lookup"><span data-stu-id="5525d-166">To enable Skype for Business online, your tenant users must have Exchange mailboxes (at least one Exchange mailbox in the tenant is required).</span></span> <span data-ttu-id="5525d-167">La tabella seguente illustra quali piani o servizi aggiuntivi sono necessari.</span><span class="sxs-lookup"><span data-stu-id="5525d-167">The following table explains which plans or additional services you need.</span></span>

| <span data-ttu-id="5525d-168">Scenario di sistema sala Skype</span><span class="sxs-lookup"><span data-stu-id="5525d-168">Skype room system scenario</span></span> | <span data-ttu-id="5525d-169">Se si dispone di Office 365 Premium, Microsoft 365 Apps for Enterprise o Skype for business standalone Plan 2, è necessario:</span><span class="sxs-lookup"><span data-stu-id="5525d-169">If you have Office 365 Premium, Microsoft 365 Apps for enterprise, or Skype for Business Standalone Plan 2, you need:</span></span> | <span data-ttu-id="5525d-170">Se disponi di un piano Enterprise, è necessario:</span><span class="sxs-lookup"><span data-stu-id="5525d-170">If you have an Enterprise-based plan, you need:</span></span> | <span data-ttu-id="5525d-171">Se si ha Skype for Business Server 2015 (locale o ibrido), è necessario:</span><span class="sxs-lookup"><span data-stu-id="5525d-171">If you have Skype for Business Server 2015 (on-premises or hybrid), you need:</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="5525d-172">Partecipare a una riunione pianificata</span><span class="sxs-lookup"><span data-stu-id="5525d-172">Join a scheduled meeting</span></span> | <span data-ttu-id="5525d-173">Skype for Business autonomo piano 1</span><span class="sxs-lookup"><span data-stu-id="5525d-173">Skype for Business Standalone Plan 1</span></span> | <span data-ttu-id="5525d-174">E1, 3, 4 o 5</span><span class="sxs-lookup"><span data-stu-id="5525d-174">E1, 3, 4, or 5</span></span> | <span data-ttu-id="5525d-175">Standard CAL per Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="5525d-175">Skype for Business Server Standard CAL</span></span> |
| <span data-ttu-id="5525d-176">Avviare una riunione ad-hoc</span><span class="sxs-lookup"><span data-stu-id="5525d-176">Initiate an ad-hoc meeting</span></span> | <span data-ttu-id="5525d-177">Skype for Business autonomo piano 2</span><span class="sxs-lookup"><span data-stu-id="5525d-177">Skype for Business Standalone Plan 2</span></span> | <span data-ttu-id="5525d-178">E 1, 3, 4 o 5</span><span class="sxs-lookup"><span data-stu-id="5525d-178">E 1, 3, 4, or 5</span></span> | <span data-ttu-id="5525d-179">Standard CAL o Enterprise CAL per Skype for Business</span><span class="sxs-lookup"><span data-stu-id="5525d-179">Skype for Business Server Standard CAL or Enterprise CAL</span></span> |
| <span data-ttu-id="5525d-180">Avviare una riunione ad-hoc e una chiamata remota da una riunione a numeri di telefono</span><span class="sxs-lookup"><span data-stu-id="5525d-180">Initiate an ad-hoc meeting and dial out from a meeting to phone numbers</span></span> | <span data-ttu-id="5525d-181">Skype for business standalone Plan 2 con servizi di audioconferenza</span><span class="sxs-lookup"><span data-stu-id="5525d-181">Skype for Business Standalone Plan 2 with Audio Conferencing</span></span></br></br><span data-ttu-id="5525d-182">**Nota**: la fatturazione per i consumi PSTN è facoltativa</span><span class="sxs-lookup"><span data-stu-id="5525d-182">**Note** PSTN consumption billing is optional</span></span> | <span data-ttu-id="5525d-183">E1 o E3 con servizi di audioconferenza o E5</span><span class="sxs-lookup"><span data-stu-id="5525d-183">E1 or E3 with Audio Conferencing, or E5</span></span>| <span data-ttu-id="5525d-184">Standard CAL o Enterprise CAL per Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="5525d-184">Skype for Business Server Standard CAL or Enterprise CAL</span></span> |
| <span data-ttu-id="5525d-185">Assegnare alla sala un numero di telefono ed effettuare o ricevere chiamate dalla sala o partecipare a una conferenza con chiamate in ingresso con un numero di telefono</span><span class="sxs-lookup"><span data-stu-id="5525d-185">Give the room a phone number and make or receive calls from the room or join a dial-in conference using a phone number</span></span> | <span data-ttu-id="5525d-186">Skype for business standalone Plan 2 con sistema telefonico e piano per chiamate vocali PSTN</span><span class="sxs-lookup"><span data-stu-id="5525d-186">Skype for Business Standalone Plan 2 with Phone System and a PSTN Voice Calling plan</span></span> | <span data-ttu-id="5525d-187">E1 o E3 con sistema telefonico e piano per chiamate vocali PSTN o E5</span><span class="sxs-lookup"><span data-stu-id="5525d-187">E1 or E3 with Phone System and a PSTN Voice Calling plan, or E5</span></span> | <span data-ttu-id="5525d-188">Standard CAL o Plus CAL per Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="5525d-188">Skype for Business Server Standard CAL or Plus CAL</span></span> |

<span data-ttu-id="5525d-189">La tabella seguente elenca i piani di Office 365 e le opzioni di Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="5525d-189">The following table lists the Office 365 plans and Skype for Business options.</span></span>

| <span data-ttu-id="5525d-190">Piano O365</span><span class="sxs-lookup"><span data-stu-id="5525d-190">O365 Plan</span></span> | <span data-ttu-id="5525d-191">Skype for Business</span><span class="sxs-lookup"><span data-stu-id="5525d-191">Skype for Business</span></span> | <span data-ttu-id="5525d-192">Sistema telefonico</span><span class="sxs-lookup"><span data-stu-id="5525d-192">Phone System</span></span> | <span data-ttu-id="5525d-193">Audioconferenza</span><span class="sxs-lookup"><span data-stu-id="5525d-193">Audio Conferencing</span></span> | <span data-ttu-id="5525d-194">Piani di chiamata</span><span class="sxs-lookup"><span data-stu-id="5525d-194">Calling Plans</span></span> |
| --- | --- | --- | --- | --- |
| <span data-ttu-id="5525d-195">O365 Business Essentials</span><span class="sxs-lookup"><span data-stu-id="5525d-195">O365 Business Essentials</span></span> | <span data-ttu-id="5525d-196">Inclusa</span><span class="sxs-lookup"><span data-stu-id="5525d-196">Included</span></span> |  |  |  |
| <span data-ttu-id="5525d-197">O365 Business Premium</span><span class="sxs-lookup"><span data-stu-id="5525d-197">O365 Business Premium</span></span> | <span data-ttu-id="5525d-198">Inclusa</span><span class="sxs-lookup"><span data-stu-id="5525d-198">Included</span></span> |  |  |  |
| <span data-ttu-id="5525d-199">E1</span><span class="sxs-lookup"><span data-stu-id="5525d-199">E1</span></span> | <span data-ttu-id="5525d-200">Incluso</span><span class="sxs-lookup"><span data-stu-id="5525d-200">Included</span></span> | <span data-ttu-id="5525d-201">Componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="5525d-201">Add-on</span></span> | <span data-ttu-id="5525d-202">Componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="5525d-202">Add-on</span></span> | <span data-ttu-id="5525d-203">Componente aggiuntivo (richiede il componente aggiuntivo per il sistema telefonico)</span><span class="sxs-lookup"><span data-stu-id="5525d-203">Add-on (requires Phone System add-on)</span></span> |
| <span data-ttu-id="5525d-204">E3</span><span class="sxs-lookup"><span data-stu-id="5525d-204">E3</span></span> | <span data-ttu-id="5525d-205">Inclusa</span><span class="sxs-lookup"><span data-stu-id="5525d-205">Included</span></span> | <span data-ttu-id="5525d-206">Componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="5525d-206">Add-on</span></span> | <span data-ttu-id="5525d-207">Componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="5525d-207">Add-on</span></span> | <span data-ttu-id="5525d-208">Componente aggiuntivo (richiede il componente aggiuntivo per il sistema telefonico)</span><span class="sxs-lookup"><span data-stu-id="5525d-208">Add-on (requires Phone System add-on)</span></span> |
| <span data-ttu-id="5525d-209">E5</span><span class="sxs-lookup"><span data-stu-id="5525d-209">E5</span></span> | <span data-ttu-id="5525d-210">Incluso</span><span class="sxs-lookup"><span data-stu-id="5525d-210">Included</span></span> | <span data-ttu-id="5525d-211">Incluso</span><span class="sxs-lookup"><span data-stu-id="5525d-211">Included</span></span> | <span data-ttu-id="5525d-212">Incluso</span><span class="sxs-lookup"><span data-stu-id="5525d-212">Included</span></span> | <span data-ttu-id="5525d-213">Componente aggiuntivo</span><span class="sxs-lookup"><span data-stu-id="5525d-213">Add-on</span></span>  |

1. <span data-ttu-id="5525d-214">Per iniziare, crea una sessione di PowerShell remota da un PC all'ambiente Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="5525d-214">Start by creating a remote PowerShell session from a PC to the Skype for Business online environment.</span></span>

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. <span data-ttu-id="5525d-215">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5525d-215">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool 'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

<span data-ttu-id="5525d-216">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5525d-216">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

```PowerShell
Get-CsOnlineUser -Identity ‘HUB01@contoso.com’| fl *registrarpool*
```

3. <span data-ttu-id="5525d-217">Assegna una licenza di Skype for Business al tuo account di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-217">Assign Skype for Business license to your Surface Hub account.</span></span>

 <span data-ttu-id="5525d-218">Dopo aver completato i passaggi precedenti per abilitare l'account di Surface Hub in Skype for Business Online, devi assegnare una licenza al dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-218">Once you've completed the preceding steps to enable your Surface Hub account in Skype for Business Online, you need to assign a license to the Surface Hub.</span></span> <span data-ttu-id="5525d-219">Usando il portale di amministrazione di Office 365, assegna al dispositivo una licenza Skype for business online (piano 2) o Skype for business online (piano 3).</span><span class="sxs-lookup"><span data-stu-id="5525d-219">Using the O365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.</span></span>

- <span data-ttu-id="5525d-220">Accedi come amministratore tenant, apri il portale di amministrazione di O365 e fai clic sull'app Admin.</span><span class="sxs-lookup"><span data-stu-id="5525d-220">Login as a tenant administrator, open the O365 Administrative Portal, and click on the Admin app.</span></span>

- <span data-ttu-id="5525d-221">Fai clic su **Utenti e gruppi** e quindi su **Aggiungere utenti, reimpostare password e altro**.</span><span class="sxs-lookup"><span data-stu-id="5525d-221">Click on **Users and Groups** and then **Add users, reset passwords, and more**.</span></span>

- <span data-ttu-id="5525d-222">Fai clic sull'account di Surface Hub e quindi fai clic sull'icona a forma di penna per modificare le informazioni dell'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-222">Click the Surface Hub account, and then click the pen icon to edit the account information.</span></span>

- <span data-ttu-id="5525d-223">Fai clic su **Licenze**.</span><span class="sxs-lookup"><span data-stu-id="5525d-223">Click **Licenses**.</span></span>

- <span data-ttu-id="5525d-224">In **assegna licenze**selezionare Skype for business (piano 1) o Skype for business (piano 2), a seconda delle licenze e dei requisiti per la segreteria telefonica aziendale.</span><span class="sxs-lookup"><span data-stu-id="5525d-224">In **Assign licenses**, select Skype for Business (Plan 1) or Skype for Business (Plan 2), depending on your licensing and Enterprise Voice requirements.</span></span> <span data-ttu-id="5525d-225">È necessario usare una licenza di piano 2 Se si vuole usare Enterprise Voice nell'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="5525d-225">You'll have to use a Plan 2 license if you want to use Enterprise Voice on your Surface Hub.</span></span>

- <span data-ttu-id="5525d-226">Fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5525d-226">Click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="5525d-227">Puoi anche usare il modulo di Microsoft Azure Active Directory per Windows PowerShell per eseguire i cmdlet necessari per assegnare una di queste licenze, ma questa opzione non è descritta qui.</span><span class="sxs-lookup"><span data-stu-id="5525d-227">You can also use the Windows Azure Active Directory Module for Windows Powershell to run the cmdlets needed to assign one of these licenses, but that's not covered here.</span></span>

<span data-ttu-id="5525d-228">Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-228">For validation, you should be able to use any Skype for Business client (PC, Android, etc.) to sign in to this account.</span></span>

### <span data-ttu-id="5525d-229">Skype for Business in locale</span><span class="sxs-lookup"><span data-stu-id="5525d-229">Skype for Business on-premises</span></span>

<span data-ttu-id="5525d-230">Per eseguire questo cmdlet, devi connetterti a uno dei front-end Skype.</span><span class="sxs-lookup"><span data-stu-id="5525d-230">To run this cmdlet, you will need to connect to one of the Skype front-ends.</span></span> <span data-ttu-id="5525d-231">Apri Skype PowerShell ed esegui:</span><span class="sxs-lookup"><span data-stu-id="5525d-231">Open the Skype PowerShell and run:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### <span data-ttu-id="5525d-232">Skype for Business con configurazione ibrida</span><span class="sxs-lookup"><span data-stu-id="5525d-232">Skype for Business hybrid</span></span>

<span data-ttu-id="5525d-233">Se l'organizzazione ha impostato la [connettività ibrida tra Skype for Business Server e Skype for Business online](https://technet.microsoft.com/library/jj205403.aspx), le indicazioni per la creazione degli account sono diverse rispetto a una distribuzione di Surface Hub standard.</span><span class="sxs-lookup"><span data-stu-id="5525d-233">If your organization has set up [hybrid connectivity between Skype for Business Server and Skype for Business Online](https://technet.microsoft.com/library/jj205403.aspx), the guidance for creating accounts differs from a standard Surface Hub deployment.</span></span>

<span data-ttu-id="5525d-234">Surface Hub richiede un account Skype di tipo `meetingroom`, mentre un utente normale userebbe un account Skype di tipo user.</span><span class="sxs-lookup"><span data-stu-id="5525d-234">The Surface Hub requires a Skype account of the type `meetingroom`, while a normal user would use a user type account in Skype.</span></span> <span data-ttu-id="5525d-235">Se il server di Skype è configurato in modo ibrido, ovvero possono essere presenti utenti nel server Skype locale nonché utenti ospitati in Office 365, possono verificarsi problemi durante la creazione di un account di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-235">If your Skype server is set up for hybrid where you might have users on the local Skype server as well as users hosted in Office 365, you might run into a few issues when trying to create a Surface Hub account.</span></span>

<span data-ttu-id="5525d-236">Nell'ambiente ibrido di Skype for Business Server 2015, tutti gli utenti desiderati in Skype for business online devono prima essere creati nella distribuzione locale, in modo che l'account utente venga creato in servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5525d-236">In Skype for Business Server 2015 hybrid environment, any user that you want in Skype for Business Online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services.</span></span> <span data-ttu-id="5525d-237">Puoi quindi trasferire l'utente in Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="5525d-237">You can then move the user to Skype for Business Online.</span></span> <span data-ttu-id="5525d-238">Il passaggio di un account utente da locale a online viene eseguito tramite il cmdlet [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) .</span><span class="sxs-lookup"><span data-stu-id="5525d-238">The move of a user account from on-premises to online is done via the [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) cmdlet.</span></span> <span data-ttu-id="5525d-239">Per rimuovere un oggetto CsMeetingRoom, usa il cmdlet [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) .</span><span class="sxs-lookup"><span data-stu-id="5525d-239">To move a Csmeetingroom object, use the [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="5525d-240">Per usare il cmdlet Move-CsMeetingRoom, è necessario aver installato [il 6.0.9319.281 di aggiornamento cumulativo di maggio 2017 per Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) o [il 5.0.8308.992 di aggiornamento cumulativo di luglio 2017 per Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span><span class="sxs-lookup"><span data-stu-id="5525d-240">To use the Move-CsMeetingRoom cmdlet, you must have installed [the May 2017 cumulative update 6.0.9319.281 for Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) or [the July 2017 cumulative update 5.0.8308.992 for Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span></span>


## <span data-ttu-id="5525d-241">Exchange online</span><span class="sxs-lookup"><span data-stu-id="5525d-241">Exchange online</span></span>

<span data-ttu-id="5525d-242">Usa questa procedura se usi Exchange online.</span><span class="sxs-lookup"><span data-stu-id="5525d-242">Use this procedure if you use Exchange online.</span></span>

1. <span data-ttu-id="5525d-243">Crea un account e-mail in Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-243">Create an email account in Office 365.</span></span>

<span data-ttu-id="5525d-244">Avvia una sessione di PowerShell remota su un PC e connettiti a Exchange.</span><span class="sxs-lookup"><span data-stu-id="5525d-244">Start a remote PowerShell session on a PC and connect to Exchange.</span></span> <span data-ttu-id="5525d-245">Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.</span><span class="sxs-lookup"><span data-stu-id="5525d-245">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/PowerShell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2. <span data-ttu-id="5525d-246">Configurare una cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="5525d-246">Set up a mailbox.</span></span>

<span data-ttu-id="5525d-247">Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente.</span><span class="sxs-lookup"><span data-stu-id="5525d-247">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="5525d-248">In questo modo l'account potrà essere autenticato in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-248">This will allow the account to authenticate into the Surface Hub.</span></span>

<span data-ttu-id="5525d-249">Se devi modificare una cassetta postale delle risorse esistente:</span><span class="sxs-lookup"><span data-stu-id="5525d-249">If you're changing an existing resource mailbox:</span></span>

```PowerShell
Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

<span data-ttu-id="5525d-250">Se devi creare una nuova cassetta postale delle risorse:</span><span class="sxs-lookup"><span data-stu-id="5525d-250">If you’re creating a new resource mailbox:</span></span>

```PowerShell
New-Mailbox -MicrosoftOnlineServicesID 'HUB01@contoso.com' -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3. <span data-ttu-id="5525d-251">Crea il criterio di Exchange ActiveSync.</span><span class="sxs-lookup"><span data-stu-id="5525d-251">Create Exchange ActiveSync policy.</span></span>

<span data-ttu-id="5525d-252">Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.</span><span class="sxs-lookup"><span data-stu-id="5525d-252">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

<span data-ttu-id="5525d-253">I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False.</span><span class="sxs-lookup"><span data-stu-id="5525d-253">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="5525d-254">Se non è impostato correttamente, i servizi Exchange nell'hub Surface (posta, calendario e riunioni di partecipazione) non verranno abilitati.</span><span class="sxs-lookup"><span data-stu-id="5525d-254">If this isn’t set properly, Exchange services on the Surface Hub (mail, calendar, and joining meetings) will not be enabled.</span></span>

<span data-ttu-id="5525d-255">Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs".</span><span class="sxs-lookup"><span data-stu-id="5525d-255">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="5525d-256">Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5525d-256">Once it’s created, you can apply the same policy to other device accounts.</span></span>

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

<span data-ttu-id="5525d-257">Una volta che hai un criterio compatibile, dovrai applicare il criterio all'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5525d-257">Once you have a compatible policy, you will need to apply the policy to the device account.</span></span> <span data-ttu-id="5525d-258">I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse.</span><span class="sxs-lookup"><span data-stu-id="5525d-258">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="5525d-259">Devi convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitarla e impostare di nuovo la password.</span><span class="sxs-lookup"><span data-stu-id="5525d-259">You need to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox—you may need to re-enable it and set the password again too.</span></span>

```PowerShell
Set-Mailbox 'HUB01@contoso.com' -Type Regular
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
Set-Mailbox 'HUB01@contoso.com' -Type Room
$credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
Set-Mailbox 'HUB01@contoso.com' -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
```

4. <span data-ttu-id="5525d-260">Imposta le proprietà di Exchange.</span><span class="sxs-lookup"><span data-stu-id="5525d-260">Set Exchange properties.</span></span>

<span data-ttu-id="5525d-261">È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="5525d-261">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="5525d-262">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .</span><span class="sxs-lookup"><span data-stu-id="5525d-262">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
```

5. <span data-ttu-id="5525d-263">Aggiungere un indirizzo di posta elettronica per l'account di dominio locale.</span><span class="sxs-lookup"><span data-stu-id="5525d-263">Add an email address for your on-premises domain account.</span></span>

<span data-ttu-id="5525d-264">Per eseguire questa procedura, userai gli strumenti di amministrazione di AD per aggiungere un indirizzo e-mail per il tuo account di dominio locale.</span><span class="sxs-lookup"><span data-stu-id="5525d-264">For this procedure, you'll be using AD admin tools to add an email address for your on-premises domain account.</span></span>

- <span data-ttu-id="5525d-265">Nello strumento di AD **Utenti e computer di Active Directory** fai clic con il pulsante destro del mouse sulla cartella o sull'unità organizzativa in cui verranno creati i tuoi account di Surface Hub, fai clic su **Nuovo**e quindi su **Utente**.</span><span class="sxs-lookup"><span data-stu-id="5525d-265">In **Active Directory Users and Computers** AD tool, right-click on the folder or Organizational Unit that your Surface Hub accounts will be created in, click **New**, and **User**.</span></span>
- <span data-ttu-id="5525d-266">Digita il nome visualizzato dal cmdlet precedente nella casella **Nome completo** e l'alias nella casella **Nome accesso utente** .</span><span class="sxs-lookup"><span data-stu-id="5525d-266">Type the display name from the previous cmdlet into the **Full name** box, and the alias into the **User logon name** box.</span></span> <span data-ttu-id="5525d-267">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5525d-267">Click **Next**.</span></span>

![Casella per un nuovo oggetto per creare un nuovo utente in Active Directory.](images/hybriddeployment-01a.png)

- <span data-ttu-id="5525d-269">Digita la password per questo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-269">Type the password for this account.</span></span> <span data-ttu-id="5525d-270">Dovrai digitarla di nuovo per la verifica.</span><span class="sxs-lookup"><span data-stu-id="5525d-270">You'll need to retype it for verification.</span></span> <span data-ttu-id="5525d-271">Assicurati che la casella di controllo **Nessuna scadenza password** sia l'unica opzione selezionata.</span><span class="sxs-lookup"><span data-stu-id="5525d-271">Make sure the **Password never expires** checkbox is the only option selected.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5525d-272">La selezione di **password non scade mai** è un requisito per Skype for business nell'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="5525d-272">Selecting **Password never expires** is a requirement for Skype for Business on the Surface Hub.</span></span> <span data-ttu-id="5525d-273">Le regole del tuo dominio potrebbero vietare l'uso di password senza scadenza.</span><span class="sxs-lookup"><span data-stu-id="5525d-273">Your domain rules may prohibit passwords that don't expire.</span></span> <span data-ttu-id="5525d-274">In questo caso, dovrai creare un'eccezione per ogni account del dispositivo di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-274">If so, you'll need to create an exception for each Surface Hub device account.</span></span>

![Immagine che mostra la finestra di dialogo della password.](images/hybriddeployment-02a.png)

- <span data-ttu-id="5525d-276">Fai clic su **Fine** per creare l'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-276">Click **Finish** to create the account.</span></span>

![Immagine con le opzioni per il nome di account, il nome di accesso e la password per il nuovo utente.](images/hybriddeployment-03a.png)

6. <span data-ttu-id="5525d-278">Esegui la sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="5525d-278">Run directory synchronization.</span></span>

<span data-ttu-id="5525d-279">Dopo aver creato l'account, esegui una sincronizzazione della directory.</span><span class="sxs-lookup"><span data-stu-id="5525d-279">After you've created the account, run a directory synchronization.</span></span> <span data-ttu-id="5525d-280">Al termine dell'operazione, accedi alla pagina degli utenti e verifica che i due account creati nei passaggi precedenti siano stati uniti.</span><span class="sxs-lookup"><span data-stu-id="5525d-280">When it's complete, go to the users page and verify that the two accounts created in the previous steps have merged.</span></span>

7. <span data-ttu-id="5525d-281">Connettiti ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="5525d-281">Connect to Azure AD.</span></span>

<span data-ttu-id="5525d-282">È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2.</span><span class="sxs-lookup"><span data-stu-id="5525d-282">You first need to install Azure AD module for PowerShell version 2.</span></span> <span data-ttu-id="5525d-283">In un prompt di PowerShell con privilegi elevati eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5525d-283">In an elevated PowerShell prompt, run the following command:</span></span>

```PowerShell
Install-Module -Name AzureAD
```

<span data-ttu-id="5525d-284">Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-284">You need to connect to Azure AD to apply some account settings.</span></span> <span data-ttu-id="5525d-285">Puoi eseguire questo cmdlet per la connessione:</span><span class="sxs-lookup"><span data-stu-id="5525d-285">You can run this cmdlet to connect:</span></span>

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. <span data-ttu-id="5525d-286">Assegna una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5525d-286">Assign an Office 365 license.</span></span>

<span data-ttu-id="5525d-287">L'account del dispositivo deve avere una licenza valida per Office 365 (O365). In caso contrario, Exchange e Skype for Business non funzioneranno.</span><span class="sxs-lookup"><span data-stu-id="5525d-287">The device account needs to have a valid Office 365 (O365) license, or Exchange and Skype for Business will not work.</span></span> <span data-ttu-id="5525d-288">Se hai la licenza, devi assegnare una località di utilizzo al tuo account del dispositivo, che servirà per determinare gli SKU di licenza disponibili per il tuo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-288">If you have the license, you need to assign a usage location to your device account—this determines what license SKUs are available for your account.</span></span>

<span data-ttu-id="5525d-289">Puoi quindi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.</span><span class="sxs-lookup"><span data-stu-id="5525d-289">Next, you can use `Get-AzureADSubscribedSku` to retrieve a list of available SKUs for your O365 tenant.</span></span>

<span data-ttu-id="5525d-290">Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.</span><span class="sxs-lookup"><span data-stu-id="5525d-290">Once you list out the SKUs, you'll need to assign the SkuId you want to the `$License.SkuId` variable.</span></span>

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

<span data-ttu-id="5525d-291">Abilita quindi l'account del dispositivo con [Skype for Business online](#skype-for-business-online), [Skype for Business in locale](#skype-for-business-on-premises) o [Skype for Business con configurazione ibrida](#skype-for-business-hybrid).</span><span class="sxs-lookup"><span data-stu-id="5525d-291">Next, you enable the device account with [Skype for Business Online](#skype-for-business-online), [Skype for Business on-premises](#skype-for-business-on-premises), or [Skype for Business hybrid](#skype-for-business-hybrid).</span></span>

### <span data-ttu-id="5525d-292">Skype for Business online</span><span class="sxs-lookup"><span data-stu-id="5525d-292">Skype for Business Online</span></span>

<span data-ttu-id="5525d-293">Per abilitare Skype for Business, l'ambiente deve soddisfare i [prerequisiti di Skype for Business online](#skype-for-business-online).</span><span class="sxs-lookup"><span data-stu-id="5525d-293">In order to enable Skype for Business, your environment will need to meet the [prerequisites for Skype for Business online](#skype-for-business-online).</span></span>

1. <span data-ttu-id="5525d-294">Per iniziare, crea una sessione di PowerShell remota da un PC all'ambiente Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="5525d-294">Start by creating a remote PowerShell session to the Skype for Business online environment from a PC.</span></span>

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. <span data-ttu-id="5525d-295">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5525d-295">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool  
'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

   <span data-ttu-id="5525d-296">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="5525d-296">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

```PowerShell
Get-CsOnlineUser -Identity 'HUB01@contoso.com'| fl *registrarpool*
```

10. <span data-ttu-id="5525d-297">Assegnare una licenza di Skype for Business al tuo account di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5525d-297">Assign Skype for Business license to your Surface Hub account</span></span>

<span data-ttu-id="5525d-298">Dopo aver completato i passaggi precedenti per abilitare l'account di Surface Hub in Skype for Business Online, devi assegnare una licenza al dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-298">Once you've completed the preceding steps to enable your Surface Hub account in Skype for Business Online, you need to assign a license to the Surface Hub.</span></span> <span data-ttu-id="5525d-299">Usando il portale di amministrazione di Office 365, assegna al dispositivo una licenza Skype for business online (piano 2) o Skype for business online (piano 3).</span><span class="sxs-lookup"><span data-stu-id="5525d-299">Using the O365 administrative portal, assign either a Skype for Business Online (Plan 2) or a Skype for Business Online (Plan 3) license to the device.</span></span>

- <span data-ttu-id="5525d-300">Accedi come amministratore tenant, apri il portale di amministrazione di O365 e fai clic sull'app Admin.</span><span class="sxs-lookup"><span data-stu-id="5525d-300">Sign in as a tenant administrator, open the O365 Administrative Portal, and click on the Admin app.</span></span>

- <span data-ttu-id="5525d-301">Fai clic su **Utenti e gruppi** e quindi su **Aggiungere utenti, reimpostare password e altro**.</span><span class="sxs-lookup"><span data-stu-id="5525d-301">Click on **Users and Groups** and then **Add users, reset passwords, and more**.</span></span>

- <span data-ttu-id="5525d-302">Fai clic sull'account di Surface Hub e quindi fai clic sull'icona a forma di penna per modificare le informazioni dell'account.</span><span class="sxs-lookup"><span data-stu-id="5525d-302">Click the Surface Hub account, and then click the pen icon to edit the account information.</span></span>

- <span data-ttu-id="5525d-303">Fai clic su **Licenze**.</span><span class="sxs-lookup"><span data-stu-id="5525d-303">Click **Licenses**.</span></span>

- <span data-ttu-id="5525d-304">In **Assegnazione licenze**seleziona Skype for Business (Piano 2) o Skype for Business (Piano 3), a seconda delle tue esigenze per licenze e VoIP aziendale.</span><span class="sxs-lookup"><span data-stu-id="5525d-304">In **Assign licenses**, select Skype for Business (Plan 2) or Skype for Business (Plan 3), depending on your licensing and Enterprise Voice requirements.</span></span> <span data-ttu-id="5525d-305">Dovrai usare una licenza per il Piano 3 se voi usare la funzionalità VoIP aziendale nel tuo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-305">You'll have to use a Plan 3 license if you want to use Enterprise Voice on your Surface Hub.</span></span>

- <span data-ttu-id="5525d-306">Fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="5525d-306">Click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="5525d-307">Puoi anche usare il Modulo di Microsoft Azure Active Directory per Windows PowerShell per eseguire i cmdlet necessari per assegnare una di queste licenze, ma questa opzione non è descritta qui.</span><span class="sxs-lookup"><span data-stu-id="5525d-307">You can also use the Windows Azure Active Directory Module for Windows PowerShell to run the cmdlets needed to assign one of these licenses, but that's not covered here.</span></span>

<span data-ttu-id="5525d-308">Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.</span><span class="sxs-lookup"><span data-stu-id="5525d-308">For validation, you should be able to use any Skype for Business client (PC, Android, etc) to sign in to this account.</span></span>

### <span data-ttu-id="5525d-309">Skype for Business in locale</span><span class="sxs-lookup"><span data-stu-id="5525d-309">Skype for Business on-premises</span></span>

<span data-ttu-id="5525d-310">Per eseguire questo cmdlet, devi connetterti a uno dei front-end Skype.</span><span class="sxs-lookup"><span data-stu-id="5525d-310">To run this cmdlet, you will need to connect to one of the Skype front-ends.</span></span> <span data-ttu-id="5525d-311">Apri Skype PowerShell ed esegui:</span><span class="sxs-lookup"><span data-stu-id="5525d-311">Open the Skype PowerShell and run:</span></span>

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### <span data-ttu-id="5525d-312">Skype for Business con configurazione ibrida</span><span class="sxs-lookup"><span data-stu-id="5525d-312">Skype for Business hybrid</span></span>

<span data-ttu-id="5525d-313">Se l'organizzazione ha impostato la [connettività ibrida tra Skype for Business Server e Skype for Business online](https://technet.microsoft.com/library/jj205403.aspx), le indicazioni per la creazione degli account sono diverse rispetto a una distribuzione di Surface Hub standard.</span><span class="sxs-lookup"><span data-stu-id="5525d-313">If your organization has set up [hybrid connectivity between Skype for Business Server and Skype for Business Online](https://technet.microsoft.com/library/jj205403.aspx), the guidance for creating accounts differs from a standard Surface Hub deployment.</span></span>

<span data-ttu-id="5525d-314">Surface Hub richiede un account Skype di tipo *meetingroom*, mentre un utente normale userebbe un account Skype di tipo *user*.</span><span class="sxs-lookup"><span data-stu-id="5525d-314">The Surface Hub requires a Skype account of the type *meetingroom*, while a normal user would use a *user* type account in Skype.</span></span> <span data-ttu-id="5525d-315">Se il server di Skype è configurato in modo ibrido, ovvero possono essere presenti utenti nel server Skype locale nonché utenti ospitati in Office 365, possono verificarsi problemi durante la creazione di un account di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5525d-315">If your Skype server is set up for hybrid where you might have users on the local Skype server as well as users hosted in Office 365, you might run into a few issues when trying to create a Surface Hub account.</span></span>

<span data-ttu-id="5525d-316">Nell'ambiente ibrido di Skype for Business Server 2015, tutti gli utenti desiderati in Skype for business online devono prima essere creati nella distribuzione locale, in modo che l'account utente venga creato in servizi di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5525d-316">In Skype for Business Server 2015 hybrid environment, any user that you want in Skype for Business Online must first be created in the on-premises deployment, so that the user account is created in Active Directory Domain Services.</span></span> <span data-ttu-id="5525d-317">Puoi quindi trasferire l'utente in Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="5525d-317">You can then move the user to Skype for Business Online.</span></span> <span data-ttu-id="5525d-318">Il passaggio di un account utente da locale a online viene eseguito tramite il cmdlet [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) .</span><span class="sxs-lookup"><span data-stu-id="5525d-318">The move of a user account from on-premises to online is done via the [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) cmdlet.</span></span> <span data-ttu-id="5525d-319">Per rimuovere un oggetto CsMeetingRoom, usa il cmdlet [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) .</span><span class="sxs-lookup"><span data-stu-id="5525d-319">To move a Csmeetingroom object, use the [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="5525d-320">Per usare il cmdlet Move-CsMeetingRoom, è necessario aver installato [il 6.0.9319.281 di aggiornamento cumulativo di maggio 2017 per Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) o [il 5.0.8308.992 di aggiornamento cumulativo di luglio 2017 per Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span><span class="sxs-lookup"><span data-stu-id="5525d-320">To use the Move-CsMeetingRoom cmdlet, you must have installed [the May 2017 cumulative update 6.0.9319.281 for Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) or [the July 2017 cumulative update 5.0.8308.992 for Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).</span></span>

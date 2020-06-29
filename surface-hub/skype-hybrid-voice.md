---
title: Distribuzione online o ibrida con l'ambiente Skype Hybrid Voice (Surface Hub)
description: In questo argomento viene illustrato come abilitare Skype for Business Cloud PBX con la connettività PSTN locale tramite un pool di Cloud Connector Edition o Skype for Business 2015.
keywords: distribuzione ibrida, Skype Hybrid Voice
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 08349a7d2decb4d4b053cb03fc95808b49d4f2f0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833842"
---
# <span data-ttu-id="96af2-104">Distribuzione online o ibrida con l'ambiente Skype Hybrid Voice (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="96af2-104">Online or hybrid deployment using Skype Hybrid Voice environment  (Surface Hub)</span></span>

<span data-ttu-id="96af2-105">In questo argomento viene illustrato come abilitare Skype for Business Cloud PBX con la connettività PSTN (Public Switched Telephone Network) locale tramite un pool di Cloud Connector Edition o Skype for Business 2015.</span><span class="sxs-lookup"><span data-stu-id="96af2-105">This topic explains how to enable Skype for Business Cloud PBX with on-premises Public Switched Telephone Network (PSTN) connectivity via Cloud Connector Edition or Skype for Business 2015 pool.</span></span> <span data-ttu-id="96af2-106">In questa opzione,</span><span class="sxs-lookup"><span data-stu-id="96af2-106">In this option.</span></span> <span data-ttu-id="96af2-107">i pool principali di Skype for Business e i server Exchange sono in cloud e connessi tramite PSTN utilizzando un pool locale che esegue Skype for Business 2015 o Cloud Connector Edition.</span><span class="sxs-lookup"><span data-stu-id="96af2-107">your Skype for Business home pools and Exchange servers are in the cloud, and are connected by PSTN via an on-premises pool running Skype for Business 2015 or Cloud Connector edition.</span></span> <span data-ttu-id="96af2-108">[Scopri di più sulle diverse opzioni Cloud PBX](https://technet.microsoft.com/library/mt612869.aspx).</span><span class="sxs-lookup"><span data-stu-id="96af2-108">[Learn more about different Cloud PBX options](https://technet.microsoft.com/library/mt612869.aspx).</span></span>  

<span data-ttu-id="96af2-109">Se hai distribuito Skype for Business Cloud PBX con una delle opzioni Hybrid Voice, segui questa procedura per abilitare l'account sala per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="96af2-109">If you deployed Skype for Business Cloud PBX with one of the hybrid voice options, follow the steps below to enable the room account for Surface Hub.</span></span> <span data-ttu-id="96af2-110">È importante creare prima un normale account utente, assegnare tutte le opzioni Hybrid Voice e i numeri di telefono e quindi convertire l'account in un account sala.</span><span class="sxs-lookup"><span data-stu-id="96af2-110">It is important to create a regular user account first, assign all hybrid voice options and phone numbers, and then convert the account to a room account.</span></span> <span data-ttu-id="96af2-111">Se non segui questo ordine, non potrai assegnare un numero di telefono ibrido.</span><span class="sxs-lookup"><span data-stu-id="96af2-111">If you do not follow this order, you will not be able to assign a hybrid phone number.</span></span>  

>[!WARNING]
><span data-ttu-id="96af2-112">Se crei un account prima della configurazione di Hybrid Voice (eseguendo il comando Enable-CSMeetingRoom), non sarai in grado di configurare i parametri Hybrid Voice necessari.</span><span class="sxs-lookup"><span data-stu-id="96af2-112">If you create an account before configuration of Hybrid voice (you run Enable-CSMeetingRoom command), you will not be able to configure required hybrid voice parameters.</span></span> <span data-ttu-id="96af2-113">Per configurare i parametri Hybrid Voice per un account configurato in precedenza o riconfigurare un numero di telefono, elimina la licenza E5 o E3 + componente aggiuntivo Cloud PBX, quindi segui questi passaggi, a partire dal passaggio 3.</span><span class="sxs-lookup"><span data-stu-id="96af2-113">In order to configure hybrid voice parameters for a previously configured account or to reconfigure a phone number, delete the E5 or E3  + Cloud PBX add-on license, and then follow the steps below, starting at step 3.</span></span>

1. <span data-ttu-id="96af2-114">Crea un nuovo account utente per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="96af2-114">Create a new user account for Surface Hub.</span></span> <span data-ttu-id="96af2-115">Questo esempio usa <strong> surfacehub2@adatum.com </strong> .</span><span class="sxs-lookup"><span data-stu-id="96af2-115">This example uses <strong>surfacehub2@adatum.com</strong>.</span></span> <span data-ttu-id="96af2-116">L'account può essere creato in Active Directory locale e sincronizzato con il cloud oppure creato direttamente nel cloud.</span><span class="sxs-lookup"><span data-stu-id="96af2-116">The account can be created in local Active Directory and synchronized to the cloud, or created directly in the cloud.</span></span> 

    ![nuovo oggetto - utente](images/new-user-hybrid-voice.png)

2. <span data-ttu-id="96af2-118">Seleziona **Nessuna scadenza password**.</span><span class="sxs-lookup"><span data-stu-id="96af2-118">Select **Password Never Expires**.</span></span> <span data-ttu-id="96af2-119">Questo è importante per un dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="96af2-119">This is important for a Surface Hub device.</span></span>

   ![Nessuna scadenza password](images/new-user-password-hybrid-voice.png)

3. <span data-ttu-id="96af2-121">In Office 365, aggiungi la licenza **E5** o **E3 e componente aggiuntivo Cloud PBX** all'account utente creato per la sala.</span><span class="sxs-lookup"><span data-stu-id="96af2-121">In Office 365, add **E5** license or **E3 and Cloud PBX** add-on to the user account created for the room.</span></span> <span data-ttu-id="96af2-122">Ciò è necessario per il funzionamento di Hybrid Voice.</span><span class="sxs-lookup"><span data-stu-id="96af2-122">This is required for Hybrid Voice to work.</span></span>

   ![Aggiungere licenze dei prodotti](images/product-license-hybrid-voice.png)

4. <span data-ttu-id="96af2-124">Attendi circa 15 minuti fino a quando non viene visualizzato l'account utente per la sala in Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="96af2-124">Wait approximately 15 minutes until the user account for the room appears in Skype for Business Online.</span></span>

5. <span data-ttu-id="96af2-125">Dopo aver creato l'account utente per la sala in Skype for Business online, abilitalo per Hybrid Voice in PowerShell remoto di Skype for Business eseguendo il cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="96af2-125">After the user account for room is created in Skype for Business Online, enable it for Hybrid Voice in Skype for Business Remote PowerShell by running the following cmdlet:</span></span>

   ```
   Set-csuser surfacehub2@adatum.com EnterpriseVoiceEnabled $true -HostedVoiceMail $true -onpremlineuri tel:+15005000102
   ```
    
6. <span data-ttu-id="96af2-126">Convalida il flusso di chiamate Hybrid Voice effettuando chiamate di test da Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="96af2-126">Validate Hybrid Voice call flow by placing test calls from the Surface Hub.</span></span>

7. <span data-ttu-id="96af2-127">Avvia una sessione remota di PowerShell su un PC e connettiti a Exchange eseguendo i cmdlet seguenti.</span><span class="sxs-lookup"><span data-stu-id="96af2-127">Start a remote PowerShell session on a PC and connect to Exchange by running the following cmdlets.</span></span>

   ```
   Set-ExecutionPolicy Unrestricted
   $cred=Get-Credential -Message "Please use your Office 365 admin credentials"
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/ps1-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```
    
8. <span data-ttu-id="96af2-128">Dopo aver stabilito una sessione, modifica l'account utente per la sala per abilitarlo come **RoomMailboxAccount** eseguendo i cmdlet seguenti.</span><span class="sxs-lookup"><span data-stu-id="96af2-128">After establishing a session, modify the user account for the room to enable it as a **RoomMailboxAccount** by running the following cmdlets.</span></span> <span data-ttu-id="96af2-129">In questo modo l'account potrà essere autenticato in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="96af2-129">This allows the account to authenticate with Surface Hub.</span></span>

   ```
   Set-Mailbox surfacehub2@adatum.com -Type Room
   Set-Mailbox surfacehub2@adatum.com -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
    
9. <span data-ttu-id="96af2-130">Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.</span><span class="sxs-lookup"><span data-stu-id="96af2-130">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="96af2-131">I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo associati a criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su **False**.</span><span class="sxs-lookup"><span data-stu-id="96af2-131">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to **False**.</span></span> <span data-ttu-id="96af2-132">Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.</span><span class="sxs-lookup"><span data-stu-id="96af2-132">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>
    
   <span data-ttu-id="96af2-133">Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs".</span><span class="sxs-lookup"><span data-stu-id="96af2-133">If you haven’t created a compatible policy yet, use the following cmdlet (this one creates a policy called "Surface Hubs").</span></span> <span data-ttu-id="96af2-134">Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="96af2-134">After it’s created, you can apply the same policy to other device accounts.</span></span>

   ```
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false
   ```
    
   <span data-ttu-id="96af2-135">Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="96af2-135">After you have a compatible policy, then you will need to apply the policy to the device account.</span></span> <span data-ttu-id="96af2-136">I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse.</span><span class="sxs-lookup"><span data-stu-id="96af2-136">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="96af2-137">Esegui i cmdlet seguenti per convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitare l'account e impostare di nuovo la password.</span><span class="sxs-lookup"><span data-stu-id="96af2-137">Run the following cmdlets to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox (you may need to re-enable the account and set the password again).</span></span>
    
   ```
   Set-Mailbox surfacehub2@adatum.com -Type Regular
   Set-CASMailbox surfacehub2@adatum.com -ActiveSyncMailboxPolicy $easPolicy.id
   Set-Mailbox surfacehub2@adatum.com -Type Room
   $credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
   Set-Mailbox surfacehub2@adatum.com -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```
    
10. <span data-ttu-id="96af2-138">È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="96af2-138">Various Exchange properties must be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="96af2-139">Puoi verificare quali proprietà possono essere impostate in [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="96af2-139">You can see which properties can be set in [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md).</span></span> <span data-ttu-id="96af2-140">I cmdlet seguenti forniscono un esempio di impostazione delle proprietà di Exchange.</span><span class="sxs-lookup"><span data-stu-id="96af2-140">The following cmdlets provide an example of setting Exchange properties.</span></span>

    ```
    Set-CalendarProcessing surfacehub2@adatum.com -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing surfacehub2@adatum.com -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

11. <span data-ttu-id="96af2-141">Abilita la cassetta postale come dispositivo per riunione in Skype for Business online.</span><span class="sxs-lookup"><span data-stu-id="96af2-141">Enable the mailbox as a meeting device in Skype for Business Online.</span></span> <span data-ttu-id="96af2-142">Eseguire il cmdlet seguente che Abilita l'account come dispositivo di riunione.</span><span class="sxs-lookup"><span data-stu-id="96af2-142">Run the following cmdlet which enables the account as a meeting device.</span></span> 

    ```
    Get-CsTenant | select registrarpool
    Enable-CsMeetingRoom surfacehub2@adatum.com -RegistrarPool  'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
    ```
    
    <span data-ttu-id="96af2-143">In seguito all'esecuzione di questo cmdlet, agli utenti verrà chiesto se si trovano in una sala riunioni, come illustrato nell'immagine seguente.</span><span class="sxs-lookup"><span data-stu-id="96af2-143">As a result of running this cmdlet, users will be asked if they are in a meeting room, as shown in the following image.</span></span> <span data-ttu-id="96af2-144">**Sì** disattiverà il microfono e l'altoparlante.</span><span class="sxs-lookup"><span data-stu-id="96af2-144">**Yes** will mute the microphone and speaker.</span></span>

    ![](images/adjust-room-audio.png)


    
<span data-ttu-id="96af2-145">In questo momento l'account sala è completamente configurato, incluso Hybrid Voice.</span><span class="sxs-lookup"><span data-stu-id="96af2-145">At this moment the room account is fully configured, including Hybrid Voice.</span></span> <span data-ttu-id="96af2-146">Se utilizzi Skype in locale, puoi configurare attributi aggiuntivi in locale, come descrizione, località e così via.</span><span class="sxs-lookup"><span data-stu-id="96af2-146">If you use Skype on-premises, you can configure additional attributes, like description, location, etc., on-premises.</span></span> <span data-ttu-id="96af2-147">Se crei una sala in Skype Online, questi parametri possono essere impostati online.</span><span class="sxs-lookup"><span data-stu-id="96af2-147">If you create a room in Skype Online, these parameters can be set online.</span></span> 

<span data-ttu-id="96af2-148">Nell'immagine seguente, puoi vedere come il dispositivo appare agli utenti.</span><span class="sxs-lookup"><span data-stu-id="96af2-148">In the following image, you can see how the device appears to users.</span></span>


![](images/select-room-hybrid-voice.png)

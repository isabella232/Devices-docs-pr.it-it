---
title: Ripristinare o recuperare un hub Surface
description: Descrive i processi di ripristino e recupero per il mozzo della superficie e fornisce istruzioni.
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Reimposta Hub superficie, recupera
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 1c8d8b6d89ec1a20550b7aa13c82c73a239c3965
ms.sourcegitcommit: d0a5c8fb2b37eb11858c7be4549e55c4b36d7471
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/08/2020
ms.locfileid: "11104818"
---
# <span data-ttu-id="a5f14-104">Ripristinare o recuperare un hub Surface</span><span class="sxs-lookup"><span data-stu-id="a5f14-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="a5f14-105">Questo articolo descrive come reimpostare o recuperare un hub di Surface Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5f14-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="a5f14-106">[La reimpostazione di Surface Hub](#reset-a-surface-hub) restituisce il proprio sistema operativo all'ultimo aggiornamento cumulativo di Windows e rimuove tutti i file utente locali e le informazioni di configurazione.</span><span class="sxs-lookup"><span data-stu-id="a5f14-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="a5f14-107">Le informazioni rimosse includono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5f14-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="a5f14-108">L'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="a5f14-108">The device account</span></span>
- <span data-ttu-id="a5f14-109">Informazioni sull'account per gli amministratori locali del dispositivo</span><span class="sxs-lookup"><span data-stu-id="a5f14-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="a5f14-110">Domain-Join o Azure AD-informazioni di join</span><span class="sxs-lookup"><span data-stu-id="a5f14-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="a5f14-111">Informazioni sulla registrazione di gestione di dispositivi mobili (MDM)</span><span class="sxs-lookup"><span data-stu-id="a5f14-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="a5f14-112">Informazioni sulla configurazione impostate usando MDM o l'app impostazioni</span><span class="sxs-lookup"><span data-stu-id="a5f14-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="a5f14-113">[Il recupero di un hub Surface dal cloud](#recover-a-surface-hub-from-the-cloud) rimuove anche queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="a5f14-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="a5f14-114">Inoltre, l'hub Surface Scarica una nuova immagine del sistema operativo e la installa.</span><span class="sxs-lookup"><span data-stu-id="a5f14-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="a5f14-115">Puoi specificare se il processo di ripristino mantiene altre informazioni memorizzate nell'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="a5f14-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span>

## <span data-ttu-id="a5f14-116">Reimpostare un hub di Surface</span><span class="sxs-lookup"><span data-stu-id="a5f14-116">Reset a Surface Hub</span></span>

<span data-ttu-id="a5f14-117">Potrebbe essere necessario reimpostare l'hub Surface per motivi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5f14-117">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="a5f14-118">Si sta purposing il dispositivo per una nuova area riunioni e si vuole riconfigurarlo.</span><span class="sxs-lookup"><span data-stu-id="a5f14-118">You are re-purposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="a5f14-119">Vuoi modificare la modalità di gestione locale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a5f14-119">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="a5f14-120">Il nome utente o la password dell'account del dispositivo o dell'account di amministratore è stata persa.</span><span class="sxs-lookup"><span data-stu-id="a5f14-120">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="a5f14-121">Dopo l'installazione di un aggiornamento, le prestazioni del dispositivo vengono decrementate.</span><span class="sxs-lookup"><span data-stu-id="a5f14-121">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="a5f14-122">Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="a5f14-122">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="a5f14-123">Il processo di ripristino del dispositivo può richiedere fino a sei ore.</span><span class="sxs-lookup"><span data-stu-id="a5f14-123">The device reset process may take up to six hours.</span></span> <span data-ttu-id="a5f14-124">Non disattivare o scollegare il mozzo della superficie fino al completamento del processo.</span><span class="sxs-lookup"><span data-stu-id="a5f14-124">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="a5f14-125">Se si interrompe il processo, il dispositivo diventa inutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="a5f14-125">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="a5f14-126">Il dispositivo richiede il servizio di garanzia per ridiventare funzionale.</span><span class="sxs-lookup"><span data-stu-id="a5f14-126">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="a5f14-127">Nel dispositivo Surface Hub apri **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-127">On your Surface Hub, open **Settings**.</span></span>

   ![Immagine che mostra l'app impostazioni per Surface Hub.](images/sh-settings.png)

1. <span data-ttu-id="a5f14-129">Selezionare **aggiorna & sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-129">Select **Update & Security**.</span></span>

   ![Immagine che mostra il gruppo di sicurezza Update & nell'app impostazioni per Surface Hub.](images/sh-settings-update-security.png)

1. <span data-ttu-id="a5f14-131">Selezionare **ripristino**e quindi, in **Reimposta dispositivo**, selezionare inizia **.**</span><span class="sxs-lookup"><span data-stu-id="a5f14-131">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   ![Immagine che mostra l'opzione Reimposta dispositivo nell'app impostazioni per hub Surface.](images/sh-settings-reset-device.png)

   <span data-ttu-id="a5f14-133">Al termine del processo di reimpostazione, l'hub Surface avvia di nuovo il [programma prima esecuzione](first-run-program-surface-hub.md) .</span><span class="sxs-lookup"><span data-stu-id="a5f14-133">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="a5f14-134">Se il processo di reimpostazione incontra un problema, rimanda il mozzo della superficie all'immagine del sistema operativo esistente in precedenza e quindi Visualizza la schermata iniziale.</span><span class="sxs-lookup"><span data-stu-id="a5f14-134">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <span data-ttu-id="a5f14-135">Ripristinare un dispositivo Surface Hub dal cloud</span><span class="sxs-lookup"><span data-stu-id="a5f14-135">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="a5f14-136">Se per qualche motivo l'hub Surface diventa inutilizzabile, è comunque possibile recuperarlo dal cloud senza assistenza da parte del supporto Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5f14-136">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="a5f14-137">L'hub Surface può scaricare un'immagine del sistema operativo fresco dal cloud e usare tale immagine per reinstallare il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="a5f14-137">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="a5f14-138">Potrebbe essere necessario usare questo tipo di processo di ripristino nelle circostanze seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5f14-138">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="a5f14-139">L'hub Surface o gli account correlati sono entrati in uno stato instabile</span><span class="sxs-lookup"><span data-stu-id="a5f14-139">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="a5f14-140">Il mozzo della superficie è bloccato</span><span class="sxs-lookup"><span data-stu-id="a5f14-140">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="a5f14-141">Il processo **di recupero dal cloud** richiede una connessione cablata che fornisce la connettività Internet aperta (nessun proxy o altre richieste di autenticazione).</span><span class="sxs-lookup"><span data-stu-id="a5f14-141">The **Recover from the cloud** process requires a wired connection that provides open internet connectivity (no proxy or other authentication prompts).</span></span>

### <span data-ttu-id="a5f14-142">Ripristinare un dispositivo Surface Hub in uno stato non valido</span><span class="sxs-lookup"><span data-stu-id="a5f14-142">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="a5f14-143">Se l'account del dispositivo entra in uno stato instabile o se l'account dell'amministratore incontra problemi, è possibile usare l'app impostazioni per avviare il processo di ripristino del cloud.</span><span class="sxs-lookup"><span data-stu-id="a5f14-143">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="a5f14-144">È consigliabile usare il processo di ripristino del cloud solo quando il processo di ripristino del [dispositivo](#reset-a-surface-hub) non risolve il problema.</span><span class="sxs-lookup"><span data-stu-id="a5f14-144">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="a5f14-145">Nell'hub Surface selezionare Aggiorna **Impostazioni** &gt; **&** &gt; **ripristino**della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="a5f14-145">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

1. <span data-ttu-id="a5f14-146">In **Recupera dal cloud**selezionare **Riavvia ora**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-146">Under **Recover from the cloud**, select **Restart now**.</span></span>

   ![ripristino dal cloud](images/recover-from-the-cloud.png)

### <span data-ttu-id="a5f14-148">Ripristinare un dispositivo Surface Hub bloccato</span><span class="sxs-lookup"><span data-stu-id="a5f14-148">Recover a locked Surface Hub</span></span>

<span data-ttu-id="a5f14-149">In rari casi, un dispositivo Surface Hub potrebbe riscontrare un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione.</span><span class="sxs-lookup"><span data-stu-id="a5f14-149">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="a5f14-150">In questo caso, il dispositivo viene riavviato automaticamente e ritenta l'operazione.</span><span class="sxs-lookup"><span data-stu-id="a5f14-150">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="a5f14-151">Ma se l'operazione non riesce più volte, il dispositivo si blocca automaticamente per proteggere i dati degli utenti.</span><span class="sxs-lookup"><span data-stu-id="a5f14-151">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="a5f14-152">Per sbloccarlo, è necessario [reimpostare il dispositivo](#reset-a-surface-hub) o, se non funziona, recuperarlo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="a5f14-152">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="a5f14-153">Individuare l'interruttore di alimentazione nella parte inferiore del mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="a5f14-153">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="a5f14-154">L'interruttore di alimentazione si trova accanto alla connessione del cavo di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="a5f14-154">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="a5f14-155">Per altre informazioni sull'interruttore di alimentazione, vedere la [Guida alla preparazione del sito hub Surface (PDF)](surface-hub-site-readiness-guide.md).</span><span class="sxs-lookup"><span data-stu-id="a5f14-155">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

1. <span data-ttu-id="a5f14-156">Mentre l'hub Surface Visualizza la schermata iniziale, usare l'interruttore Power per disattivare l'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="a5f14-156">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

1. <span data-ttu-id="a5f14-157">Usare l'interruttore di accensione per riattivare il mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="a5f14-157">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="a5f14-158">Il dispositivo viene avviato e viene visualizzata la schermata del logo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="a5f14-158">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="a5f14-159">Quando vedi puntini di filatura sotto il logo di Surface Hub, usa l'interruttore Power per disattivare di nuovo il mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="a5f14-159">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

1. <span data-ttu-id="a5f14-160">Ripetere il passaggio 3 3 volte oppure finché l'hub Surface non Visualizza il messaggio "preparazione della riparazione automatica".</span><span class="sxs-lookup"><span data-stu-id="a5f14-160">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="a5f14-161">Dopo aver visualizzato questo messaggio, l'hub Surface Visualizza la schermata di ripristino di Windows.</span><span class="sxs-lookup"><span data-stu-id="a5f14-161">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>

1. <span data-ttu-id="a5f14-162">Selezionare **Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-162">Select **Advanced Options**.</span></span>

1. <span data-ttu-id="a5f14-163">Selezionare **Recupera dal cloud**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-163">Select **Recover from the cloud**.</span></span> <span data-ttu-id="a5f14-164">(Facoltativamente, è possibile selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-164">(Optionally, you can select **Reset**.</span></span> <span data-ttu-id="a5f14-165">Tuttavia, il **recupero dal cloud** è l'approccio consigliato.</span><span class="sxs-lookup"><span data-stu-id="a5f14-165">However, **Recover from the cloud** is the recommended approach.)</span></span>

   ![Ripristino dal cloud](images/recover-from-cloud.png)
1. <span data-ttu-id="a5f14-167">Se viene chiesto di immettere la chiave BitLocker, eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a5f14-167">If you are prompted to enter the Bitlocker key, do one of the following:</span></span>

   - <span data-ttu-id="a5f14-168">Per mantenere le informazioni protette da BitLocker nell'hub di Surface, immettere la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="a5f14-168">To preserve the information that Bitlocker protects on the Surface Hub, enter the Bitlocker key.</span></span>
   - <span data-ttu-id="a5f14-169">Per annullare le informazioni protette, selezionare **Ignora l'unità**</span><span class="sxs-lookup"><span data-stu-id="a5f14-169">To discard the protected information, select **Skip this drive**</span></span>  

1. <span data-ttu-id="a5f14-170">Quando viene richiesto, selezionare **Reinstalla**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-170">When you are prompted, select **Reinstall**.</span></span>

    ![Reinstalla](images/reinstall.png)

1. <span data-ttu-id="a5f14-172">Per ripartizionare il disco, selezionare **Sì**.</span><span class="sxs-lookup"><span data-stu-id="a5f14-172">To repartition the disk, select **Yes**.</span></span>

   ![Ripartizione](images/repartition.png)

   <span data-ttu-id="a5f14-174">Prima di tutto, il processo di ripristino Scarica l'immagine del sistema operativo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="a5f14-174">First, the recovery process downloads the operating system image from the cloud.</span></span>  

   ![download 97& in corso](images/recover-progress.png)

   <span data-ttu-id="a5f14-176">Al termine del download, il processo di ripristino Ripristina il mozzo della superficie in base alle opzioni selezionate.</span><span class="sxs-lookup"><span data-stu-id="a5f14-176">When the download finishes, the recovery process restores the Surface Hub according to the options that you selected.</span></span>
   

## <span data-ttu-id="a5f14-177">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="a5f14-177">Contact Support</span></span>

<span data-ttu-id="a5f14-178">Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).</span><span class="sxs-lookup"><span data-stu-id="a5f14-178">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <span data-ttu-id="a5f14-179">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="a5f14-179">Related topics</span></span>

[<span data-ttu-id="a5f14-180">Gestire Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="a5f14-180">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="a5f14-181">Manuale dell'amministratore di Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="a5f14-181">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

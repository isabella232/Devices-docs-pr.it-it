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
ms.openlocfilehash: c5cf643d0f4a68344bb098916a909dd66e1dac9b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833729"
---
# <span data-ttu-id="c6233-104">Ripristinare o recuperare un hub Surface</span><span class="sxs-lookup"><span data-stu-id="c6233-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="c6233-105">Questo articolo descrive come reimpostare o recuperare un hub di Surface Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6233-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="c6233-106">[La reimpostazione di Surface Hub](#reset-a-surface-hub) restituisce il proprio sistema operativo all'ultimo aggiornamento cumulativo di Windows e rimuove tutti i file utente locali e le informazioni di configurazione.</span><span class="sxs-lookup"><span data-stu-id="c6233-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="c6233-107">Le informazioni rimosse includono le seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6233-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="c6233-108">L'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c6233-108">The device account</span></span>
- <span data-ttu-id="c6233-109">Informazioni sull'account per gli amministratori locali del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c6233-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="c6233-110">Domain-Join o Azure AD-informazioni di join</span><span class="sxs-lookup"><span data-stu-id="c6233-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="c6233-111">Informazioni sulla registrazione di gestione di dispositivi mobili (MDM)</span><span class="sxs-lookup"><span data-stu-id="c6233-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="c6233-112">Informazioni sulla configurazione impostate usando MDM o l'app impostazioni</span><span class="sxs-lookup"><span data-stu-id="c6233-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="c6233-113">[Il recupero di un hub Surface dal cloud](#recover-a-surface-hub-from-the-cloud) rimuove anche queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="c6233-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="c6233-114">Inoltre, l'hub Surface Scarica una nuova immagine del sistema operativo e la installa.</span><span class="sxs-lookup"><span data-stu-id="c6233-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="c6233-115">Puoi specificare se il processo di ripristino mantiene altre informazioni memorizzate nell'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="c6233-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span>

## <span data-ttu-id="c6233-116">Reimpostare un hub di Surface</span><span class="sxs-lookup"><span data-stu-id="c6233-116">Reset a Surface Hub</span></span>

<span data-ttu-id="c6233-117">Potrebbe essere necessario reimpostare l'hub Surface per motivi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6233-117">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="c6233-118">Si sta purposing il dispositivo per una nuova area riunioni e si vuole riconfigurarlo.</span><span class="sxs-lookup"><span data-stu-id="c6233-118">You are re-purposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="c6233-119">Vuoi modificare la modalità di gestione locale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c6233-119">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="c6233-120">Il nome utente o la password dell'account del dispositivo o dell'account di amministratore è stata persa.</span><span class="sxs-lookup"><span data-stu-id="c6233-120">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="c6233-121">Dopo l'installazione di un aggiornamento, le prestazioni del dispositivo vengono decrementate.</span><span class="sxs-lookup"><span data-stu-id="c6233-121">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="c6233-122">Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="c6233-122">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="c6233-123">Il processo di ripristino del dispositivo può richiedere fino a sei ore.</span><span class="sxs-lookup"><span data-stu-id="c6233-123">The device reset process may take up to six hours.</span></span> <span data-ttu-id="c6233-124">Non disattivare o scollegare il mozzo della superficie fino al completamento del processo.</span><span class="sxs-lookup"><span data-stu-id="c6233-124">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="c6233-125">Se si interrompe il processo, il dispositivo diventa inutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="c6233-125">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="c6233-126">Il dispositivo richiede il servizio di garanzia per ridiventare funzionale.</span><span class="sxs-lookup"><span data-stu-id="c6233-126">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="c6233-127">Nel dispositivo Surface Hub apri **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="c6233-127">On your Surface Hub, open **Settings**.</span></span>

   ![Immagine che mostra l'app impostazioni per Surface Hub.](images/sh-settings.png)

1. <span data-ttu-id="c6233-129">Selezionare **aggiorna & sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="c6233-129">Select **Update & Security**.</span></span>

   ![Immagine che mostra il gruppo di sicurezza Update & nell'app impostazioni per Surface Hub.](images/sh-settings-update-security.png)

1. <span data-ttu-id="c6233-131">Selezionare **ripristino**e quindi, in **Reimposta dispositivo**, selezionare inizia **.**</span><span class="sxs-lookup"><span data-stu-id="c6233-131">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   ![Immagine che mostra l'opzione Reimposta dispositivo nell'app impostazioni per hub Surface.](images/sh-settings-reset-device.png)

   <span data-ttu-id="c6233-133">Al termine del processo di reimpostazione, l'hub Surface avvia di nuovo il [programma prima esecuzione](first-run-program-surface-hub.md) .</span><span class="sxs-lookup"><span data-stu-id="c6233-133">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="c6233-134">Se il processo di reimpostazione incontra un problema, rimanda il mozzo della superficie all'immagine del sistema operativo esistente in precedenza e quindi Visualizza la schermata iniziale.</span><span class="sxs-lookup"><span data-stu-id="c6233-134">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <span data-ttu-id="c6233-135">Ripristinare un dispositivo Surface Hub dal cloud</span><span class="sxs-lookup"><span data-stu-id="c6233-135">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="c6233-136">Se per qualche motivo l'hub Surface diventa inutilizzabile, è comunque possibile recuperarlo dal cloud senza assistenza da parte del supporto Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c6233-136">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="c6233-137">L'hub Surface può scaricare un'immagine del sistema operativo fresco dal cloud e usare tale immagine per reinstallare il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="c6233-137">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="c6233-138">Potrebbe essere necessario usare questo tipo di processo di ripristino nelle circostanze seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6233-138">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="c6233-139">L'hub Surface o gli account correlati sono entrati in uno stato instabile</span><span class="sxs-lookup"><span data-stu-id="c6233-139">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="c6233-140">Il mozzo della superficie è bloccato</span><span class="sxs-lookup"><span data-stu-id="c6233-140">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="c6233-141">Il processo **di ripristino dal cloud** richiede una connessione Internet aperta (nessun proxy o altre autenticazioni).</span><span class="sxs-lookup"><span data-stu-id="c6233-141">The **Recover from the cloud** process requires an open internet connection (no proxy or other authentications).</span></span> <span data-ttu-id="c6233-142">È consigliabile una connessione Ethernet.</span><span class="sxs-lookup"><span data-stu-id="c6233-142">An ethernet connection is recommended.</span></span>

### <span data-ttu-id="c6233-143">Ripristinare un dispositivo Surface Hub in uno stato non valido</span><span class="sxs-lookup"><span data-stu-id="c6233-143">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="c6233-144">Se l'account del dispositivo entra in uno stato instabile o se l'account dell'amministratore incontra problemi, è possibile usare l'app impostazioni per avviare il processo di ripristino del cloud.</span><span class="sxs-lookup"><span data-stu-id="c6233-144">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="c6233-145">È consigliabile usare il processo di ripristino del cloud solo quando il processo di ripristino del [dispositivo](#reset-a-surface-hub) non risolve il problema.</span><span class="sxs-lookup"><span data-stu-id="c6233-145">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="c6233-146">Nell'hub Surface selezionare Aggiorna **Impostazioni** &gt; **&** &gt; **ripristino**della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="c6233-146">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

1. <span data-ttu-id="c6233-147">In **Recupera dal cloud**selezionare **Riavvia ora**.</span><span class="sxs-lookup"><span data-stu-id="c6233-147">Under **Recover from the cloud**, select **Restart now**.</span></span>

   ![ripristino dal cloud](images/recover-from-the-cloud.png)

### <span data-ttu-id="c6233-149">Ripristinare un dispositivo Surface Hub bloccato</span><span class="sxs-lookup"><span data-stu-id="c6233-149">Recover a locked Surface Hub</span></span>

<span data-ttu-id="c6233-150">In rari casi, un dispositivo Surface Hub potrebbe riscontrare un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione.</span><span class="sxs-lookup"><span data-stu-id="c6233-150">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="c6233-151">In questo caso, il dispositivo viene riavviato automaticamente e ritenta l'operazione.</span><span class="sxs-lookup"><span data-stu-id="c6233-151">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="c6233-152">Ma se l'operazione non riesce più volte, il dispositivo si blocca automaticamente per proteggere i dati degli utenti.</span><span class="sxs-lookup"><span data-stu-id="c6233-152">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="c6233-153">Per sbloccarlo, è necessario [reimpostare il dispositivo](#reset-a-surface-hub) o, se non funziona, recuperarlo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="c6233-153">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="c6233-154">Individuare l'interruttore di alimentazione nella parte inferiore del mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="c6233-154">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="c6233-155">L'interruttore di alimentazione si trova accanto alla connessione del cavo di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="c6233-155">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="c6233-156">Per altre informazioni sull'interruttore di alimentazione, vedere la [Guida alla preparazione del sito hub Surface (PDF)](surface-hub-site-readiness-guide.md).</span><span class="sxs-lookup"><span data-stu-id="c6233-156">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

1. <span data-ttu-id="c6233-157">Mentre l'hub Surface Visualizza la schermata iniziale, usare l'interruttore Power per disattivare l'hub Surface.</span><span class="sxs-lookup"><span data-stu-id="c6233-157">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

1. <span data-ttu-id="c6233-158">Usare l'interruttore di accensione per riattivare il mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="c6233-158">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="c6233-159">Il dispositivo viene avviato e viene visualizzata la schermata del logo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="c6233-159">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="c6233-160">Quando vedi puntini di filatura sotto il logo di Surface Hub, usa l'interruttore Power per disattivare di nuovo il mozzo della superficie.</span><span class="sxs-lookup"><span data-stu-id="c6233-160">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

1. <span data-ttu-id="c6233-161">Ripetere il passaggio 3 3 volte oppure finché l'hub Surface non Visualizza il messaggio "preparazione della riparazione automatica".</span><span class="sxs-lookup"><span data-stu-id="c6233-161">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="c6233-162">Dopo aver visualizzato questo messaggio, l'hub Surface Visualizza la schermata di ripristino di Windows.</span><span class="sxs-lookup"><span data-stu-id="c6233-162">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>

1. <span data-ttu-id="c6233-163">Selezionare **Opzioni avanzate**.</span><span class="sxs-lookup"><span data-stu-id="c6233-163">Select **Advanced Options**.</span></span>

1. <span data-ttu-id="c6233-164">Selezionare **Recupera dal cloud**.</span><span class="sxs-lookup"><span data-stu-id="c6233-164">Select **Recover from the cloud**.</span></span> <span data-ttu-id="c6233-165">(Facoltativamente, è possibile selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="c6233-165">(Optionally, you can select **Reset**.</span></span> <span data-ttu-id="c6233-166">Tuttavia, il **recupero dal cloud** è l'approccio consigliato.</span><span class="sxs-lookup"><span data-stu-id="c6233-166">However, **Recover from the cloud** is the recommended approach.)</span></span>

   ![Ripristino dal cloud](images/recover-from-cloud.png)
1. <span data-ttu-id="c6233-168">Se viene chiesto di immettere la chiave BitLocker, eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6233-168">If you are prompted to enter the Bitlocker key, do one of the following:</span></span>

   - <span data-ttu-id="c6233-169">Per mantenere le informazioni protette da BitLocker nell'hub di Surface, immettere la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="c6233-169">To preserve the information that Bitlocker protects on the Surface Hub, enter the Bitlocker key.</span></span>
   - <span data-ttu-id="c6233-170">Per annullare le informazioni protette, selezionare **Ignora l'unità**</span><span class="sxs-lookup"><span data-stu-id="c6233-170">To discard the protected information, select **Skip this drive**</span></span>  

1. <span data-ttu-id="c6233-171">Quando viene richiesto, selezionare **Reinstalla**.</span><span class="sxs-lookup"><span data-stu-id="c6233-171">When you are prompted, select **Reinstall**.</span></span>

    ![Reinstalla](images/reinstall.png)

1. <span data-ttu-id="c6233-173">Per ripartizionare il disco, selezionare **Sì**.</span><span class="sxs-lookup"><span data-stu-id="c6233-173">To repartition the disk, select **Yes**.</span></span>

   ![Ripartizione](images/repartition.png)

   <span data-ttu-id="c6233-175">Prima di tutto, il processo di ripristino Scarica l'immagine del sistema operativo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="c6233-175">First, the recovery process downloads the operating system image from the cloud.</span></span>  

   ![download 97& in corso](images/recover-progress.png)

   <span data-ttu-id="c6233-177">Al termine del download, il processo di ripristino Ripristina il mozzo della superficie in base alle opzioni selezionate.</span><span class="sxs-lookup"><span data-stu-id="c6233-177">When the download finishes, the recovery process restores the Surface Hub according to the options that you selected.</span></span>
   

## <span data-ttu-id="c6233-178">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="c6233-178">Contact Support</span></span>

<span data-ttu-id="c6233-179">Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).</span><span class="sxs-lookup"><span data-stu-id="c6233-179">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <span data-ttu-id="c6233-180">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="c6233-180">Related topics</span></span>

[<span data-ttu-id="c6233-181">Gestire Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="c6233-181">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="c6233-182">Manuale dell'amministratore di Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="c6233-182">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

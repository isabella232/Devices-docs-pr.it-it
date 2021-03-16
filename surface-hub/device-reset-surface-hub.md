---
title: Reimpostare o ripristinare un dispositivo Surface Hub
description: Descrive i processi di reimpostazione e ripristino per Surface Hub e fornisce istruzioni.
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: reimpostare Surface Hub, ripristinare
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/10/2021
ms.localizationpriority: medium
ms.openlocfilehash: 8d9a4f995abda4e005e8136ace62e10fb564c9b8
ms.sourcegitcommit: ea853f2dba67e63e6df33538670fd581e17facab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2021
ms.locfileid: "11408811"
---
# <a name="reset-or-recover-a-surface-hub"></a><span data-ttu-id="cd7f2-104">Reimpostare o ripristinare un dispositivo Surface Hub</span><span class="sxs-lookup"><span data-stu-id="cd7f2-104">Reset or recover a Surface Hub</span></span>

<span data-ttu-id="cd7f2-105">Questo articolo descrive come reimpostare o ripristinare un Microsoft Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-105">This article describes how to reset or recover a Microsoft Surface Hub.</span></span>  

<span data-ttu-id="cd7f2-106">[La reimpostazione di Surface Hub](#reset-a-surface-hub) riporta il sistema operativo all'ultimo aggiornamento cumulativo di Windows e rimuove tutti i file utente locali e le informazioni di configurazione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-106">[Resetting the Surface Hub](#reset-a-surface-hub) returns its operating system to the last cumulative Windows update, and removes all local user files and configuration information.</span></span> <span data-ttu-id="cd7f2-107">Le informazioni rimosse includono quanto segue:</span><span class="sxs-lookup"><span data-stu-id="cd7f2-107">The information that is removed includes the following:</span></span>

- <span data-ttu-id="cd7f2-108">L'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="cd7f2-108">The device account</span></span>
- <span data-ttu-id="cd7f2-109">Informazioni sull'account per gli amministratori locali del dispositivo</span><span class="sxs-lookup"><span data-stu-id="cd7f2-109">Account information for the device's local administrators</span></span>
- <span data-ttu-id="cd7f2-110">Informazioni sull'aggiunta a un dominio o azure AD</span><span class="sxs-lookup"><span data-stu-id="cd7f2-110">Domain-join or Azure AD-join information</span></span>
- <span data-ttu-id="cd7f2-111">Informazioni di registrazione di Gestione dispositivi mobili (MDM)</span><span class="sxs-lookup"><span data-stu-id="cd7f2-111">Mobile Device Management (MDM) enrollment information</span></span>
- <span data-ttu-id="cd7f2-112">Informazioni di configurazione impostate tramite MDM o l'app Impostazioni</span><span class="sxs-lookup"><span data-stu-id="cd7f2-112">Configuration information that was set by using MDM or the Settings app</span></span>

<span data-ttu-id="cd7f2-113">[Anche il ripristino di un dispositivo Surface Hub dal cloud](#recover-a-surface-hub-from-the-cloud) rimuove queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-113">[Recovering a Surface Hub from the cloud](#recover-a-surface-hub-from-the-cloud) also removes this information.</span></span> <span data-ttu-id="cd7f2-114">Inoltre, Surface Hub scarica una nuova immagine del sistema operativo e la installa.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-114">In addition, the Surface Hub downloads a new operating system image and installs it.</span></span> <span data-ttu-id="cd7f2-115">Puoi specificare se il processo di ripristino mantiene altre informazioni archiviate in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-115">You can specify whether the recovery process preserves other information that is stored on the Surface Hub.</span></span> <span data-ttu-id="cd7f2-116">La stessa immagine del sistema operativo viene usata dallo strumento di ripristino [di Surface Hub](surface-hub-recovery-tool.md) se devi ripristinare un dispositivo Surface Hub per il quale nessuna di queste opzioni può essere usata.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-116">The same operating system image is used by the [Surface Hub Recovery Tool](surface-hub-recovery-tool.md) if you need to recover a Surface Hub for which neither of these options can be used.</span></span>

## <a name="reset-a-surface-hub"></a><span data-ttu-id="cd7f2-117">Reimpostare un dispositivo Surface Hub</span><span class="sxs-lookup"><span data-stu-id="cd7f2-117">Reset a Surface Hub</span></span>

<span data-ttu-id="cd7f2-118">Potrebbe essere necessario reimpostare Surface Hub per motivi come i seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd7f2-118">You may have to reset your Surface Hub for reasons such as the following:</span></span>

- <span data-ttu-id="cd7f2-119">Si sta riconfigurando il dispositivo per un nuovo spazio riunioni e si desidera riconfigurarlo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-119">You are repurposing the device for a new meeting space and want to reconfigure it.</span></span>
- <span data-ttu-id="cd7f2-120">Vuoi modificare la modalità di gestione locale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-120">You want to change how you locally manage the device.</span></span>
- <span data-ttu-id="cd7f2-121">Il nome utente o la password dell'account del dispositivo o dell'account amministratore è stato perso.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-121">The user name or password for the device account or the Administrator account has been lost.</span></span>
- <span data-ttu-id="cd7f2-122">Dopo aver installato un aggiornamento, le prestazioni del dispositivo diminuiscono.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-122">After you install an update, the performance of the device decreases.</span></span>

<span data-ttu-id="cd7f2-123">Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-123">During the reset process, if you see a blank screen for long periods of time, please wait and do not take any action.</span></span>

> [!WARNING]
> <span data-ttu-id="cd7f2-124">Il processo di reimpostazione del dispositivo può richiedere fino a sei ore.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-124">The device reset process may take up to six hours.</span></span> <span data-ttu-id="cd7f2-125">Non spegnere o scollegare Surface Hub fino al termine del processo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-125">Do not turn off or unplug the Surface Hub until the process has finished.</span></span> <span data-ttu-id="cd7f2-126">Se interrompi il processo, il dispositivo diventa inoperabile.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-126">If you interrupt the process, the device becomes inoperable.</span></span> <span data-ttu-id="cd7f2-127">Il dispositivo richiede un servizio di garanzia per poter diventare nuovamente funzionante.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-127">The device requires warranty service in order to become functional again.</span></span>

1. <span data-ttu-id="cd7f2-128">Nel dispositivo Surface Hub apri **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-128">On your Surface Hub, open **Settings**.</span></span>

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra l'app Impostazioni per Surface Hub.](images/sh-settings.png)

2. <span data-ttu-id="cd7f2-130">Selezionare **Aggiorna & sicurezza**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-130">Select **Update & Security**.</span></span>

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra il gruppo & sicurezza nell'app Impostazioni per Surface Hub.](images/sh-settings-update-security.png)

3. <span data-ttu-id="cd7f2-132">Selezionare **Ripristino**e quindi, in **Reimposta dispositivo,** selezionare **Introduzione.**</span><span class="sxs-lookup"><span data-stu-id="cd7f2-132">Select **Recovery**, and then, under **Reset device**, select **Get started**.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="cd7f2-133">Assicurati di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, come verrà richiesto in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-133">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="cd7f2-134">Per altre informazioni, vedi [Salvare la chiave di BitLocker.](save-bitlocker-key-surface-hub.md)</span><span class="sxs-lookup"><span data-stu-id="cd7f2-134">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span> <span data-ttu-id="cd7f2-135">Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-135">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="cd7f2-136">Se si ignora il prompt, la reimpostazione avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-136">Skipping that prompt will cause reset to fail.</span></span>
   
   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra l'opzione Reimposta dispositivo nell'app Impostazioni per Surface Hub.](images/sh-settings-reset-device.png)

   <span data-ttu-id="cd7f2-138">Al termine del processo di reimpostazione, Surface Hub avvia [di nuovo il programma di prima](first-run-program-surface-hub.md) esecuzione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-138">After the reset process finishes, the Surface Hub starts the [first run program](first-run-program-surface-hub.md) again.</span></span> <span data-ttu-id="cd7f2-139">Se il processo di reimpostazione rileva un problema, il dispositivo Surface Hub viene riportato all'immagine del sistema operativo esistente in precedenza e quindi viene visualizzata la schermata iniziale.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-139">If the reset process encounters a problem, it rolls the Surface Hub back to the previously-existing operating system image and then displays the Welcome screen.</span></span>

<span id="cloud-recovery" />

## <a name="recover-a-surface-hub-from-the-cloud"></a><span data-ttu-id="cd7f2-140">Ripristinare un dispositivo Surface Hub dal cloud</span><span class="sxs-lookup"><span data-stu-id="cd7f2-140">Recover a Surface Hub from the cloud</span></span>

<span data-ttu-id="cd7f2-141">Se per qualche motivo Surface Hub diventa inutilizzabile, puoi comunque recuperarlo dal cloud senza assistenza del supporto Tecnico Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-141">If for some reason the Surface Hub becomes unusable, you can still recover it from the cloud without assistance from Microsoft Support.</span></span> <span data-ttu-id="cd7f2-142">Surface Hub può scaricare una nuova immagine del sistema operativo dal cloud e usarla per reinstallare il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-142">The Surface Hub can download a fresh operating system image from the cloud, and use that image to reinstall its operating system.</span></span>

<span data-ttu-id="cd7f2-143">Potrebbe essere necessario utilizzare questo tipo di processo di ripristino nelle circostanze seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd7f2-143">You may have to use this type of recovery process under the following circumstances:</span></span>

- [<span data-ttu-id="cd7f2-144">Surface Hub o i relativi account sono entrati in uno stato instabile</span><span class="sxs-lookup"><span data-stu-id="cd7f2-144">The Surface Hub or its related accounts have entered an unstable state</span></span>](#recover-a-surface-hub-in-a-bad-state)
- [<span data-ttu-id="cd7f2-145">Surface Hub è bloccato</span><span class="sxs-lookup"><span data-stu-id="cd7f2-145">The Surface Hub is locked</span></span>](#recover-a-locked-surface-hub)

>[!IMPORTANT]
><span data-ttu-id="cd7f2-146">Il **processo Di ripristino dal cloud** richiede una connessione cablata che fornisce connettività Internet aperta (nessun proxy o altre richieste di autenticazione).</span><span class="sxs-lookup"><span data-stu-id="cd7f2-146">The **Recover from the cloud** process requires a wired connection that provides open internet connectivity (no proxy or other authentication prompts).</span></span>

### <a name="recover-a-surface-hub-in-a-bad-state"></a><span data-ttu-id="cd7f2-147">Ripristinare un dispositivo Surface Hub in uno stato non valido</span><span class="sxs-lookup"><span data-stu-id="cd7f2-147">Recover a Surface Hub in a bad state</span></span>

<span data-ttu-id="cd7f2-148">Se l'account del dispositivo entra in uno stato instabile o se si verificano problemi con l'account amministratore, puoi usare l'app Impostazioni per avviare il processo di ripristino cloud.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-148">If the device account gets into an unstable state or if the administrator account encounters problems, you can use the Settings app to start the cloud recovery process.</span></span> <span data-ttu-id="cd7f2-149">Devi usare il processo di ripristino cloud solo quando il processo di [reimpostazione](#reset-a-surface-hub) del dispositivo non risolve il problema.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-149">You should only use the cloud recovery process when the [device reset](#reset-a-surface-hub) process doesn't fix the problem.</span></span>

1. <span data-ttu-id="cd7f2-150">Nel dispositivo Surface Hub seleziona **Impostazioni** &gt; **Aggiornamento & sicurezza** &gt; **Ripristino**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-150">On your Surface Hub, select **Settings** &gt; **Update & security** &gt; **Recovery**.</span></span>

2. <span data-ttu-id="cd7f2-151">In **Ripristina dal cloud**seleziona **Riavvia ora.**</span><span class="sxs-lookup"><span data-stu-id="cd7f2-151">Under **Recover from the cloud**, select **Restart now**.</span></span>

   > [!div class="mx-imgBorder"]
   > ![ripristino dal cloud](images/recover-from-the-cloud.png)

### <a name="recover-a-locked-surface-hub"></a><span data-ttu-id="cd7f2-153">Ripristinare un dispositivo Surface Hub bloccato</span><span class="sxs-lookup"><span data-stu-id="cd7f2-153">Recover a locked Surface Hub</span></span>

<span data-ttu-id="cd7f2-154">In rari casi, un dispositivo Surface Hub potrebbe riscontrare un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-154">On rare occasions, a Surface Hub may encounter an error while cleaning up user and app data at the end of a session.</span></span> <span data-ttu-id="cd7f2-155">In questo caso, il dispositivo si riavvia automaticamente e tenta di nuovo l'operazione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-155">When this happens, the device automatically restarts and tries the operation again.</span></span> <span data-ttu-id="cd7f2-156">Tuttavia, se l'operazione non riesce più volte, il dispositivo si blocca automaticamente per proteggere i dati dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-156">But if this operation fails repeatedly, the device automatically locks to protect user data.</span></span> <span data-ttu-id="cd7f2-157">Per sbloccarlo, devi [reimpostare il dispositivo](#reset-a-surface-hub) o, se non funziona, recuperarlo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-157">To unlock it, you must [reset the device](#reset-a-surface-hub) or, if that doesn't work, recover it from the cloud.</span></span>

1. <span data-ttu-id="cd7f2-158">Individua l'interruttore di alimentazione nella parte inferiore di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-158">Locate the power switch on the bottom of Surface Hub.</span></span> <span data-ttu-id="cd7f2-159">L'interruttore di alimentazione è accanto alla connessione del cavo di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-159">The power switch is next to the power cord connection.</span></span> <span data-ttu-id="cd7f2-160">Per ulteriori informazioni sull'interruttore di alimentazione, vedi la Guida alla preparazione del sito [Surface Hub (PDF)](surface-hub-site-readiness-guide.md).</span><span class="sxs-lookup"><span data-stu-id="cd7f2-160">For more information about the power switch, see the [Surface Hub Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).</span></span>

2. <span data-ttu-id="cd7f2-161">Mentre Surface Hub visualizza la schermata iniziale, usa l'interruttore di alimentazione per disattivare Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-161">While the Surface Hub displays the Welcome screen, use the power switch to turn off the Surface Hub.</span></span>

3. <span data-ttu-id="cd7f2-162">Usa l'interruttore di alimentazione per riattivare Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-162">Use the power switch to turn the Surface Hub back on.</span></span> <span data-ttu-id="cd7f2-163">Il dispositivo viene avviato e visualizza la schermata del logo di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-163">The device starts and displays the Surface Hub Logo screen.</span></span> <span data-ttu-id="cd7f2-164">Quando vedi punti rotanti sotto il logo di Surface Hub, usa l'interruttore di alimentazione per spegnere di nuovo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-164">When you see spinning dots under the Surface Hub Logo, use the power switch to turn the Surface Hub off again.</span></span>  

4. <span data-ttu-id="cd7f2-165">Ripeti il passaggio 3 tre volte o finché il dispositivo Surface Hub non visualizza il messaggio "Preparazione del ripristino automatico".</span><span class="sxs-lookup"><span data-stu-id="cd7f2-165">Repeat step 3 three times, or until the Surface Hub displays the "Preparing Automatic Repair" message.</span></span> <span data-ttu-id="cd7f2-166">Dopo la visualizzazione di questo messaggio, Surface Hub visualizza la schermata Windows RE.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-166">After it displays this message, the Surface Hub displays the Windows RE screen.</span></span>
 
5. <span data-ttu-id="cd7f2-167">Seleziona **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-167">Select **Reset**.</span></span> 

6. <span data-ttu-id="cd7f2-168">Se viene richiesto di immettere la chiave BitLocker, eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cd7f2-168">If you are prompted to enter the BitLocker key, do one of the following:</span></span>
   - <span data-ttu-id="cd7f2-169">Per conservare le informazioni protette da BitLocker in Surface Hub, immetti la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-169">To preserve the information that BitLocker protects on the Surface Hub, enter the BitLocker key.</span></span>
   - <span data-ttu-id="cd7f2-170">Per eliminare le informazioni protette, selezionare Ignora questa unità</span><span class="sxs-lookup"><span data-stu-id="cd7f2-170">To discard the protected information, select Skip this drive</span></span>

7. <span data-ttu-id="cd7f2-171">Seleziona **Download cloud.**</span><span class="sxs-lookup"><span data-stu-id="cd7f2-171">Select **Cloud download.**</span></span> 

   ![Download cloud](images/recover-cloud-download.png)

   >[!IMPORTANT]
   ><span data-ttu-id="cd7f2-173">Se viene visualizzato un messaggio di errore che indica **Impossibile scaricare**, selezionare **Annulla** e quindi **reimpostare di** nuovo.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-173">If you get an error message indicating **Unable to Download**, select **Cancel** and then **Reset** again.</span></span>

8. <span data-ttu-id="cd7f2-174">Selezionare **Pulire completamente l'unità.**</span><span class="sxs-lookup"><span data-stu-id="cd7f2-174">Select **Fully clean the drive.**</span></span>
 
   ![ripristino e pulizia completa dell'unità](images/recover-fully-clean-drive.png)

9. <span data-ttu-id="cd7f2-176">Ti verrà chiesto **Se sei pronto per reimpostare questo dispositivo?**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-176">You will be asked **Are you ready to reset this device?**.</span></span> <span data-ttu-id="cd7f2-177">Seleziona **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="cd7f2-177">Select **Reset**.</span></span> 
   
   ![ripristinare e confermare la reimpostazione](images/recover-confirm-reset.png)

10. <span data-ttu-id="cd7f2-179">Il download inizia e il processo di ripristino indica **reimpostazione di questo dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="cd7f2-179">The download begins and the recovery process indicates **Resetting this device**.</span></span>

    ![ripristino visualizzato in corso](images/recover-in-progress.png)

## <a name="contact-support"></a><span data-ttu-id="cd7f2-181">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="cd7f2-181">Contact Support</span></span>

<span data-ttu-id="cd7f2-182">Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).</span><span class="sxs-lookup"><span data-stu-id="cd7f2-182">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>


## <a name="related-topics"></a><span data-ttu-id="cd7f2-183">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="cd7f2-183">Related topics</span></span>

[<span data-ttu-id="cd7f2-184">Gestire Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="cd7f2-184">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="cd7f2-185">Manuale dell'amministratore di Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="cd7f2-185">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

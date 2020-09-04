---
title: Configurare Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo include suggerimenti per garantire un'esperienza ottimale quando si usa un tocco di grande schermo personalizzato e un computer penna.
keywords: Surface Hub, Windows 10, desktop, installa, configurazione
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.collection: M365-modern-desktop
ms.topic: article
ms.openlocfilehash: 47852284c35d213b81dd7b87ca875b400d8c713f
ms.sourcegitcommit: c74835239cf4e304af59465fb6fc785de4a0c5cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2020
ms.locfileid: "10994592"
---
# <span data-ttu-id="7cbb3-104">Configurare Windows 10 Pro o Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="7cbb3-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

**<span data-ttu-id="7cbb3-105">Si applica a: Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="7cbb3-105">Applies to: Surface Hub 2S</span></span>** 

<span data-ttu-id="7cbb3-106">Dopo aver completato il processo di installazione della migrazione a Windows 10 Pro o Enterprise, è possibile eseguire la procedura seguente per configurare le app e le impostazioni nel proprio Surface Hub 2.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-106">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="7cbb3-107">Questa procedura è consigliata per garantire un'esperienza ottimale quando si usa questo touch screen personalizzato di grandi dimensioni e un computer con penna.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-107">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="7cbb3-108">Durante l'esecuzione di questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-108">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <span data-ttu-id="7cbb3-109">Configurare le impostazioni di sistema</span><span class="sxs-lookup"><span data-stu-id="7cbb3-109">Configure system settings</span></span>

1. <span data-ttu-id="7cbb3-110">Accedere con un account che disponga dei privilegi di amministratore locale nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-110">Sign in with an account that has local administrator privileges on the device.</span></span>  
    - <span data-ttu-id="7cbb3-111">Nei dispositivi di Azure AD Uniti l'utente che esegue il join di Azure AD viene automaticamente aggiunto al gruppo di amministratori locali.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-111">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="7cbb3-112">Gli amministratori globali di Azure AD e i dispositivi Azure AD sono [anche amministratori locali](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-112">Azure AD global administrators and Azure AD devices administrators are [also local administrators](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin).</span></span> 
    - <span data-ttu-id="7cbb3-113">È possibile digitare **net localgroup Administrators** al prompt dei comandi per elencare gli account con diritti di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-113">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
2. <span data-ttu-id="7cbb3-114">Rinominare il dispositivo usando un nome descrittivo, ad esempio: **nomeutente-SHub-desktop**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-114">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>
3. <span data-ttu-id="7cbb3-115">Selezionare **Avvia**  >  **Settings**  >  **account**impostazioni  >  **sincronizzare le impostazioni** e disattivare **le impostazioni di sincronizzazione** .</span><span class="sxs-lookup"><span data-stu-id="7cbb3-115">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 
    - <span data-ttu-id="7cbb3-116">Le impostazioni usate in questo articolo sono destinate a consentire l'esperienza di tocco di grande schermo migliore e quindi potresti non voler sincronizzare altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-116">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
4. <span data-ttu-id="7cbb3-117">Riavviare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-117">Reboot the device.</span></span>

## <span data-ttu-id="7cbb3-118">Abilitare la tastiera virtuale e il touchpad</span><span class="sxs-lookup"><span data-stu-id="7cbb3-118">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="7cbb3-119">Toccare e tenere premuto o fare clic con il pulsante destro del mouse sulla barra delle applicazioni e quindi scegliere **Mostra pulsante tastiera virtuale** e **Mostra touchpad**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-119">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 
    - <span data-ttu-id="7cbb3-120">La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad Virtual aiuta con selezioni precise, suggerimenti per lo schermo in bilico o come alternativa per toccare e tenere premuto il pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-120">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    - <span data-ttu-id="7cbb3-121">Vedi l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-121">See the following example.</span></span>

     ![Impostazioni tocco](images/touch.png)

2. <span data-ttu-id="7cbb3-123">Configurare la tastiera virtuale su QWERTY e mobile.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-123">Configure the touch keyboard to QWERTY and floating.</span></span>
    1. <span data-ttu-id="7cbb3-124">Selezionare l'icona della tastiera sulla barra delle applicazioni per visualizzare la tastiera virtuale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-124">Select the keyboard icon on the taskbar to show the touch keyboard.</span></span>
    2. <span data-ttu-id="7cbb3-125">Nella tastiera virtuale selezionare l'icona della tastiera nell'angolo in alto a sinistra per aprire le impostazioni della tastiera.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-125">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    3. <span data-ttu-id="7cbb3-126">Selezionare il tipo di tastiera accanto a ultimo nella riga superiore per abilitare QWERTY e l'ultima opzione della seconda riga per abilitare il Floating, che è molto utile in questo grande schermo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-126">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="7cbb3-127">Vedere gli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-127">See the following examples.</span></span>

     ![Impostazioni della tastiera](images/kbd.png)

3. <span data-ttu-id="7cbb3-129">Configurare le impostazioni della tastiera morbida.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-129">Configure the soft keyboard settings.</span></span>
    1. <span data-ttu-id="7cbb3-130">Cercare e aprire **le impostazioni di digitazione**</span><span class="sxs-lookup"><span data-stu-id="7cbb3-130">Search for and open **Typing settings**</span></span> 
    2. <span data-ttu-id="7cbb3-131">Abilitare tutte le opzioni in controllo ortografia, digitazione e tastiera virtuale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-131">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="7cbb3-132">L'esempio seguente mostra il trackpad, utile per spostarsi e selezionare le opzioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-132">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="7cbb3-133">La tastiera su schermo viene usata per eseguire ricerche in Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-133">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![Uso del trackpad](images/store.png)

## <span data-ttu-id="7cbb3-135">Configurare la tastiera e il mouse Bluetooth (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="7cbb3-135">Configure bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="7cbb3-136">Connettere una tastiera e un mouse se si usa il dispositivo come dispositivo principale di Windows o si usa spesso per la digitazione o il lavoro di precisione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-136">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="7cbb3-137">Se il dispositivo Surface Hub è vicino a un PC, è possibile usare il [mouse senza bordi](https://aka.ms/mm) per passare facilmente tra il mozzo della superficie e il PC.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-137">If your Surface Hub device is near to a PC, you can use [Mouse without Borders](https://aka.ms/mm) to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="7cbb3-138">Per altre informazioni, vedere [download Microsoft dal garage: mouse senza bordi](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-138">For more information, see [Microsoft download from The Garage: Mouse without Borders](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).</span></span>

## <span data-ttu-id="7cbb3-139">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="7cbb3-139">OneDrive for Business</span></span>

<span data-ttu-id="7cbb3-140">Usare [OneDrive for business](https://docs.microsoft.com/onedrive/onedrive) per condividere facilmente strumenti, log e altri file tra tutti i dispositivi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-140">Use [OneDrive for Business](https://docs.microsoft.com/onedrive/onedrive) to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="7cbb3-141">OneDrive consente di condividere i file di lavoro tra i computer portatili, Surface Hub desktop e i dispositivi mobili gestiti da Intune.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-141">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="7cbb3-142">I file possono essere modificati in qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-142">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>
- <span data-ttu-id="7cbb3-143">Considerando le dimensioni di Surface Hub SSD (128GB), se si configura OneDrive nel dispositivo desktop Surface Hub, verificare che la configurazione predefinita contenga i file online e scarichi i file durante l'uso.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-143">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="7cbb3-144">Per configurare OneDrive per il download dei file solo quando necessario, impostare l'impostazione **file su richiesta** per **risparmiare spazio e scaricare i file durante l'uso**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-144">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="7cbb3-145">Per altre informazioni, vedere [query e impostare gli Stati su richiesta di file in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-145">For more information, see [Query and set Files On-Demand states in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).</span></span>

![Impostazioni di OneDrive](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="7cbb3-147">Puoi anche ripetere questi passaggi per configurare un OneDrive personale, ma assicurati di risparmiare spazio su disco e scaricare i file solo quando necessario.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-147">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <span data-ttu-id="7cbb3-148">SharePoint e teams</span><span class="sxs-lookup"><span data-stu-id="7cbb3-148">SharePoint and Teams</span></span>

<span data-ttu-id="7cbb3-149">I file di canale di SharePoint e teams possono anche essere sincronizzati localmente con i dispositivi desktop, ad esempio laptop e Surface Hub, usando il motore di sincronizzazione di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-149">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="7cbb3-150">Per sincronizzare i file aziendali interni con l'unità locale con l'app di sincronizzazione di OneDrive:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-150">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="7cbb3-151">Passare a un sito di SharePoint e passare alla directory principale del documento per i file che si vogliono visualizzare o modificare dal dispositivo locale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-151">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>
2. <span data-ttu-id="7cbb3-152">Selezionare il pulsante **Sincronizza** nella parte superiore della barra multifunzione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-152">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>
3. <span data-ttu-id="7cbb3-153">Selezionare **Apri** nel popup **questo sito sta provando ad aprire Microsoft OneDrive**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-153">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>
4. <span data-ttu-id="7cbb3-154">Verificare che i file di SharePoint vengano sincronizzati con l'unità locale selezionando l'icona OneDrive nell'angolo in basso a destra della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-154">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>
5. <span data-ttu-id="7cbb3-155">Verificare che la configurazione sia impostata in modo da conservare i file online e scaricare i file solo quando si usano:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-155">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>
    1. <span data-ttu-id="7cbb3-156">Aprire Esplora file.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-156">Open file explorer.</span></span>
    2. <span data-ttu-id="7cbb3-157">Passare a e fare clic con il pulsante destro del mouse su \*\*Microsoft \ \<SharePoint Document Folder Name\> \*\*.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-157">Navigate to and right select on the **Microsoft \ \<SharePoint Document Folder Name\>**.</span></span>
    3. <span data-ttu-id="7cbb3-158">Selezionare **libera spazio**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-158">Select **Free up space**.</span></span>
    4. <span data-ttu-id="7cbb3-159">La colonna stato visualizzerà lo stato di file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-159">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="7cbb3-160">Per altre informazioni, vedere [sincronizzare i file di SharePoint con il client di sincronizzazione di OneDrive](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-160">For more information, see [Sync SharePoint files with the OneDrive sync client](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).</span></span>
6. <span data-ttu-id="7cbb3-161">I file di canale di teams sono archiviati nei siti di SharePoint, con tutte le stesse funzionalità dei documenti di SharePoint, inclusa la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-161">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="7cbb3-162">Per sincronizzare i file del canale teams:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-162">To sync Teams Channel files:</span></span>
    1. <span data-ttu-id="7cbb3-163">Passare al canale teams di interesse e selezionare nella scheda **file** nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-163">Navigate to the Teams Channel of interest and select on the **Files** tab at the top.</span></span> <span data-ttu-id="7cbb3-164">Quindi seleziona **Sincronizza**. I file verranno avviati per la sincronizzazione e saranno visibili in Esplora file in \*\*Desktop \ Microsoft \<name of the Teams Channel\> \ \*\*.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-164">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Microsoft \ \<name of the Teams Channel\>**.</span></span>
    2. <span data-ttu-id="7cbb3-165">Usare la stessa procedura usata per sincronizzare i siti di SharePoint per mantenere i file nel cloud e scaricarli solo quando si usano, toccare e tenere premuto o fare clic con il pulsante destro del mouse in Esplora file nel nome del canale teams e quindi selezionare **libera spazio**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-165">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <span data-ttu-id="7cbb3-166">Associare la penna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="7cbb3-166">Pair the Surface Hub pen</span></span>

<span data-ttu-id="7cbb3-167">Per associare il dispositivo penna:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-167">To pair the pen device:</span></span>

1. <span data-ttu-id="7cbb3-168">Selezionare **Avvia**  >  **Settings**  >  **dispositivi**di impostazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-168">Select **Start** > **Settings** > **Devices**.</span></span>
2. <span data-ttu-id="7cbb3-169">Selezionare **Aggiungi Bluetooth o altro dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-169">Select **Add Bluetooth or other device**.</span></span>
3. <span data-ttu-id="7cbb3-170">Scegliere **Bluetooth**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-170">Choose **Bluetooth**.</span></span>
4. <span data-ttu-id="7cbb3-171">Rimuovere il pulsante della coda della penna e agitare per scollegare il connettore della batteria.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-171">Remove the pen tail button and shake to disconnect the battery connection.</span></span>
5. <span data-ttu-id="7cbb3-172">Riposizionare il cappuccio e premere e tenere premuto il cappuccio finché non lampeggia il LED di associazione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-172">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>
6. <span data-ttu-id="7cbb3-173">Nelle impostazioni di Surface Hub Bluetooth scegliere **Surface Hub 2 Pen**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-173">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>
7. <span data-ttu-id="7cbb3-174">Completare l'operazione di associazione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-174">Complete the pairing operation.</span></span> 
8. <span data-ttu-id="7cbb3-175">Se l'associazione non riesce, provare a associare di nuovo la penna.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-175">If the pairing is not successful, attempt to pair the pen again.</span></span> <span data-ttu-id="7cbb3-176">Se necessario, riavviare il dispositivo e riprovare.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-176">If necessary, reboot the device and then try again.</span></span>

## <span data-ttu-id="7cbb3-177">Configurazione della videocamera</span><span class="sxs-lookup"><span data-stu-id="7cbb3-177">Camera configuration</span></span>

<span data-ttu-id="7cbb3-178">È possibile montare la videocamera nella parte superiore o su entrambi i lati del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-178">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="7cbb3-179">Montare la videocamera in una posizione per ottimizzare l'angolazione della fotocamera se si usa l'hub con uno stand desktop anziché un carrello o si è in prossimità dell'hub.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-179">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="7cbb3-180">La fotocamera non ruota automaticamente, quindi è necessario disporre di una chiave esadecimale da 2mm per ruotare manualmente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-180">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="7cbb3-181">Per altre informazioni su come montare la videocamera e ruotarla manualmente, vedere orientamento dell'obiettivo della [fotocamera](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-181">For more information on how to side-mount the camera and rotate the camera manually, see [Surface Hub 2S camera lens orientation](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).</span></span>

## <span data-ttu-id="7cbb3-182">Configurazione di Windows Hello</span><span class="sxs-lookup"><span data-stu-id="7cbb3-182">Windows Hello configuration</span></span>

<span data-ttu-id="7cbb3-183">Surface Hub 2S con Windows 10 Enterprise consente la famiglia completa di applicazioni desktop Win32 e le opzioni biometriche di Windows Hello.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-183">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="7cbb3-184">L'accessorio lettore di impronte digitali Surface Hub 2 può essere collegato a qualsiasi porta USB-C del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-184">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

> <i><span data-ttu-id="7cbb3-185">Il lettore di impronte digitali Surface Hub 2 sarà presto disponibile per l'acquisto.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-185">The Surface Hub 2 Fingerprint Reader will be available for purchase soon.</span></span> <span data-ttu-id="7cbb3-186">Verificare di nuovo in questa pagina per altre informazioni, incluso l'acquisto.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-186">Please check back on this page for more information including how to purchase.</span></span></i>

<span data-ttu-id="7cbb3-187">Dopo aver inserito il lettore di impronte digitali **Start**, selezionare  >  **Settings**  >  **Accounts**  >  **Opzioni**di avvio per l'accesso agli account  >  di**Windows Hello Fingerprint** per registrare l'impronta digitale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-187">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="7cbb3-188">Usare un dispositivo certificato Windows Hello per il riconoscimento delle facce.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-188">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="7cbb3-189">La fotocamera di Surface Hub 2S non supporta il riconoscimento del volto di Windows Hello.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-189">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <span data-ttu-id="7cbb3-190">Abilitare un'icona di collegamento alla schermata di blocco sulla barra delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="7cbb3-190">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="7cbb3-191">Per aggiungere un'icona alla barra delle applicazioni che consente il blocco dello schermo con un tocco simile alla scelta rapida da tastiera Windows-L:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-191">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="7cbb3-192">Toccare e tenere premuto o fare clic con il pulsante destro del mouse sul desktop, scegliere **nuovo**  >  **collegamento**  >  **Sfoglia**  >  **Desktop**  >  **OK**  >  **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-192">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>

1.  <span data-ttu-id="7cbb3-193">Specificare un nome per il collegamento, ad esempio **Blocca PC**e quindi selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-193">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>

1.  <span data-ttu-id="7cbb3-194">Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento appena creato sul desktop e scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-194">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="7cbb3-195">Nella scheda **collegamento** immettere quanto segue nel campo di **destinazione** : **Rundll32.exe User32.dll, LockWorkStation**</span><span class="sxs-lookup"><span data-stu-id="7cbb3-195">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>

1.  <span data-ttu-id="7cbb3-196">Selezionare il pulsante **Cambia icona** e passare a **C:\Windows\System32\imageres.dll** e selezionare un'icona da usare.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-196">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 

    <span data-ttu-id="7cbb3-197">Vedi l'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-197">See the following example:</span></span>

    ![Scegliere un'icona](images/lock.png)
    
1.  <span data-ttu-id="7cbb3-199">Selezionare **OK** per salvare il collegamento.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-199">Select **OK** to save the shortcut.</span></span>

1.  <span data-ttu-id="7cbb3-200">Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento e selezionare **Aggiungi alla barra delle applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-200">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

## <span data-ttu-id="7cbb3-201">Applicazioni</span><span class="sxs-lookup"><span data-stu-id="7cbb3-201">Applications</span></span>

### <span data-ttu-id="7cbb3-202">Aggiornare le app installate</span><span class="sxs-lookup"><span data-stu-id="7cbb3-202">Update installed apps</span></span>

<span data-ttu-id="7cbb3-203">Per aggiornare tutte le app dello Store installate:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-203">To update all installed Store apps:</span></span>

1. <span data-ttu-id="7cbb3-204">Aprire l'app Microsoft Store e selezionare la **visualizzazione altri** puntini di sospensione nell'angolo in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-204">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>
2. <span data-ttu-id="7cbb3-205">Selezionare **download e aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-205">Select **Downloads and updates**.</span></span>
2. <span data-ttu-id="7cbb3-206">Selezionare **Ottieni aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-206">Select **Get updates**.</span></span>

### <span data-ttu-id="7cbb3-207">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="7cbb3-207">Microsoft Whiteboard</span></span>

<span data-ttu-id="7cbb3-208">Per installare la lavagna Microsoft:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-208">To install the Microsoft Whiteboard:</span></span>

 - <span data-ttu-id="7cbb3-209">Selezionare l'icona dell' **area di lavoro Windows Ink** nell'angolo inferiore destro della barra delle applicazioni e scaricare **lavagna**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-209">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span></span>
 
   ![Area di lavoro input penna](images/ink.png) 

<span data-ttu-id="7cbb3-211">In alternativa, è possibile installare lavagna da Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-211">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="7cbb3-212">Aprire l'app Microsoft Store e cercare **lavagna**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-212">Open Microsoft Store app and search for **Whiteboard**.</span></span>
2. <span data-ttu-id="7cbb3-213">Scegliere **No grazie** per accedere e usare i vari dispositivi.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-213">Choose **No thanks** to sign in and use across devices.</span></span>
3. <span data-ttu-id="7cbb3-214">Aggiungere la lavagna alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-214">Pin Whiteboard to the taskbar.</span></span>

### <span data-ttu-id="7cbb3-215">App Surface</span><span class="sxs-lookup"><span data-stu-id="7cbb3-215">Surface app</span></span>

1. <span data-ttu-id="7cbb3-216">In Microsoft Store cercare **Surface**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-216">In the Microsoft Store, search for **Surface**.</span></span>
2. <span data-ttu-id="7cbb3-217">Impostare il filtro **disponibile su** **tutti i dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-217">Set the **Available on** filter to **All devices**.</span></span>
3. <span data-ttu-id="7cbb3-218">Installare l'app **Surface** .</span><span class="sxs-lookup"><span data-stu-id="7cbb3-218">Install the **Surface** app.</span></span> <span data-ttu-id="7cbb3-219">Questa dovrebbe essere la prima app elencata.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-219">This should be the first app listed.</span></span> <span data-ttu-id="7cbb3-220">Potrebbe essere necessario associare il MSA allo Store per installare l'app.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-220">You might need to associate your MSA to the Store in order to install the app.</span></span>
4. <span data-ttu-id="7cbb3-221">Aggiungere l'app **Surface** alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-221">Pin the **Surface** app to taskbar.</span></span>

### <span data-ttu-id="7cbb3-222">Snip & sketch</span><span class="sxs-lookup"><span data-stu-id="7cbb3-222">Snip & Sketch</span></span>

1. <span data-ttu-id="7cbb3-223">Aprire l'app **Snip & sketch** e aggiungerla alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-223">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>
2. <span data-ttu-id="7cbb3-224">Selezionare i puntini di sospensione nell'angolo in alto a destra e quindi selezionare **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-224">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>
3. <span data-ttu-id="7cbb3-225">In **Impostazioni**, attiva **copia automatica negli Appunti**, **Salva snip**e **più finestre** (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-225">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <span data-ttu-id="7cbb3-226">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="7cbb3-226">Microsoft Office</span></span>

1. <span data-ttu-id="7cbb3-227">Aprire il [portale di Office](https://portal.office.com/account#installs) e installare le applicazioni desiderate.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-227">Open the [Office Portal](https://portal.office.com/account#installs) and install your desired applications.</span></span>
2. <span data-ttu-id="7cbb3-228">Bloccare le applicazioni di Office desiderate nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-228">Pin desired Office applications to the taskbar.</span></span>
3. <span data-ttu-id="7cbb3-229">Se Outlook è installato, assicurarsi di impostare Outlook OST per salvare solo la cache delle ultime due settimane.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-229">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="7cbb3-230">In questo modo si ridurrà notevolmente l'utilizzo del disco e il tempo di configurazione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-230">This will vastly reduce disk usage and setup time.</span></span>
    - <span data-ttu-id="7cbb3-231">Selezionare **File**  >  **Impostazioni account** file e selezionare il proprio account.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-231">Select **File** > **Account Settings** and select your account.</span></span>
    - <span data-ttu-id="7cbb3-232">Selezionare **Cambia** e impostare il dispositivo di scorrimento per **usare la modalità cache** per 14 giorni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-232">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <span data-ttu-id="7cbb3-233">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="7cbb3-233">Microsoft Teams</span></span>

1. <span data-ttu-id="7cbb3-234">Scaricare e installare [Microsoft teams](https://teams.microsoft.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-234">Download and install [Microsoft Teams](https://teams.microsoft.com/downloads).</span></span>
2. <span data-ttu-id="7cbb3-235">Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-235">Configure settings to Auto-start application (optional).</span></span>
3. <span data-ttu-id="7cbb3-236">Aggiungere Team alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-236">Pin Teams to the taskbar.</span></span>
4. <span data-ttu-id="7cbb3-237">Valutare la possibilità di ridurre le notifiche dei team sul dispositivo per evitare distrazioni (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-237">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

  ![Notifiche di Teams](images/teams.png)

### <span data-ttu-id="7cbb3-239">App Connect</span><span class="sxs-lookup"><span data-stu-id="7cbb3-239">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7cbb3-240">In Windows 10 versione 2004 e successive l'app Connect per la proiezione wireless che usa Miracast non è installata per impostazione predefinita, ma è disponibile come caratteristica facoltativa.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-240">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="7cbb3-241">Per installare l'app, seleziona nelle **Settings**  >  **app**impostazioni le  >  **funzionalità facoltative**  >  **aggiungono una caratteristica** e quindi installa l'app di **visualizzazione wireless** .</span><span class="sxs-lookup"><span data-stu-id="7cbb3-241">To install the app, select on **Settings** > **Apps** > **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

1. <span data-ttu-id="7cbb3-242">Cercare **Connetti**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-242">Search for **Connect**.</span></span>
2. <span data-ttu-id="7cbb3-243">Aprire l'app e quindi chiuderla (il**progetto in questo PC** potrebbe non funzionare a meno che l'app non sia stata eseguita almeno una volta).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-243">Open the app and then close it (**Project to this PC** might not work unless the app has been run at least once).</span></span>
3. <span data-ttu-id="7cbb3-244">Toccare e tenere premuto o fare clic con il pulsante destro del mouse sulla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-244">Tap and hold or right-click to pin to taskbar.</span></span>
4. <span data-ttu-id="7cbb3-245">Cercare **impostazioni di proiezione**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-245">Search for **Projection settings**.</span></span>
5. <span data-ttu-id="7cbb3-246">In **alcuni dispositivi Windows e Android possono essere proiettati in questo PC quando si dice che è OK**, scegliere **disponibile ovunque** se il dispositivo non si trova in una rete aziendale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-246">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose **Available everywhere** if the device is not on a corporate network.</span></span> <span data-ttu-id="7cbb3-247">In caso contrario, è possibile scegliere **disponibile ovunque su reti sicure**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-247">Otherwise, you can choose **Available everywhere on secure networks**.</span></span>
6. <span data-ttu-id="7cbb3-248">In **ask to Project to this PC**scegliere **First time only**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-248">Under **Ask to project to this PC**, choose **First time only**.</span></span>
7. <span data-ttu-id="7cbb3-249">In **Richiedi PIN per l'associazione**scegliere **mai**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-249">Under **Require PIN for pairing**, choose **Never**.</span></span>

<span data-ttu-id="7cbb3-250">Configurazione consigliata quando non è presente nella rete aziendale:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-250">Recommended configuration when not on the corporate network:</span></span>

  ![Impostazioni in Home](images/project1.png)

<span data-ttu-id="7cbb3-252">Configurazione consigliata nella rete aziendale:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-252">Recommended configuration on the corporate network:</span></span>

  ![Impostazioni sul lavoro](images/project2.png)

### <span data-ttu-id="7cbb3-254">Il tuo telefono</span><span class="sxs-lookup"><span data-stu-id="7cbb3-254">Your Phone</span></span>

<span data-ttu-id="7cbb3-255">L'app **telefono** è installata per impostazione predefinita in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-255">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="7cbb3-256">Se non è presente, è possibile installarlo anche da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-256">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="7cbb3-257">Per informazioni sulla configurazione dell'app, vedere [come configurare il telefono in Windows 10 e sincronizzare i dati tra il PC e il telefono](https://www.windowscentral.com/how-set-your-phone-windows-10).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-257">For information about setting up the app, see [How to set up Your Phone on Windows 10 and sync data between your PC and phone](https://www.windowscentral.com/how-set-your-phone-windows-10).</span></span> <span data-ttu-id="7cbb3-258">Vedi anche [come risolvere i problemi comuni con l'app telefono in Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-258">Also see [How to fix common problems with Your Phone app on Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).</span></span>

### <span data-ttu-id="7cbb3-259">Aree di fantasia Super</span><span class="sxs-lookup"><span data-stu-id="7cbb3-259">Super Fancy Zones</span></span>

<span data-ttu-id="7cbb3-260">**Super-Fancy Zones** aiuta gli utenti a disporre Windows per massimizzare la proprietà dello schermo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-260">**Super Fancy Zones** helps users arrange windows to maximize screen real estate.</span></span> <span data-ttu-id="7cbb3-261">È ora incluso in [PowerToys](https://github.com/microsoft/PowerToys/releases) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-261">It is now included in [PowerToys](https://github.com/microsoft/PowerToys/releases) on GitHub.</span></span>

### <span data-ttu-id="7cbb3-262">Browser cromo Edge</span><span class="sxs-lookup"><span data-stu-id="7cbb3-262">Edge Chromium browser</span></span>

<span data-ttu-id="7cbb3-263">Scaricare e installare il nuovo [browser cromo Edge](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-263">Download and install the new [Edge Chromium browser](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).</span></span>

## <span data-ttu-id="7cbb3-264">Impostazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="7cbb3-264">Additional settings</span></span>

### <span data-ttu-id="7cbb3-265">Coda di penna selezionare per avviare la lavagna</span><span class="sxs-lookup"><span data-stu-id="7cbb3-265">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="7cbb3-266">Cercare **penna** e selezionare **penna & impostazioni di Windows Ink**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-266">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>
2. <span data-ttu-id="7cbb3-267">Nella parte inferiore della pagina, in **scelte rapide da tastiera** , impostare **Seleziona una volta** su **Microsoft whiteboard**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-267">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <span data-ttu-id="7cbb3-268">Impostazioni di alimentazione e sospensione</span><span class="sxs-lookup"><span data-stu-id="7cbb3-268">Power and sleep settings</span></span>

1. <span data-ttu-id="7cbb3-269">Selezionare **Start**  >  **Settings**  >  **System**  >  **Power & Sleep**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-269">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>
2. <span data-ttu-id="7cbb3-270">Impostare il dispositivo di scorrimento Power Mode per **ottenere prestazioni ottimali**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-270">Set the power mode slider to **Best performance**.</span></span>
3. <span data-ttu-id="7cbb3-271">Configurare i valori di schermata e Sleep in preferenza.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-271">Configure screen and sleep values to your preference.</span></span>

### <span data-ttu-id="7cbb3-272">Salvaschermo</span><span class="sxs-lookup"><span data-stu-id="7cbb3-272">Screen saver</span></span>

1. <span data-ttu-id="7cbb3-273">Cercare la **schermata di blocco** e aprire **le impostazioni della schermata di blocco**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-273">Search for **Lock Screen** and open **Lock screen settings**.</span></span>
2. <span data-ttu-id="7cbb3-274">Configurare le impostazioni di **timeout dello schermo** e **le impostazioni dello screensaver** per le preferenze.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-274">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span>

### <span data-ttu-id="7cbb3-275">Sensore memoria</span><span class="sxs-lookup"><span data-stu-id="7cbb3-275">Storage Sense</span></span>

<span data-ttu-id="7cbb3-276">Surface Hub 2 ha un SSD 128GB per l'archiviazione locale, quindi è necessario considerare l'uso delle misure di salvataggio dello storage durante l'uso normale.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-276">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="7cbb3-277">Per configurare il senso di archiviazione:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-277">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="7cbb3-278">Cercare **le impostazioni di archiviazione**, disponibili in **impostazioni di sistema**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-278">Search for **storage settings**, which is found under **System settings**.</span></span>
2.  <span data-ttu-id="7cbb3-279">In **Impostazioni**selezionare **attiva il senso di archiviazione** per aprire la pagina impostazioni di **archiviazione** .</span><span class="sxs-lookup"><span data-stu-id="7cbb3-279">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>
3.  <span data-ttu-id="7cbb3-280">Attivare il senso di archiviazione **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-280">Turn Storage Sense to **On**.</span></span>
4.  <span data-ttu-id="7cbb3-281">Selezionare **Configura il senso di archiviazione o eseguirlo ora** e configurare le impostazioni per conservare i file online il più possibile (a causa dello spazio di unità limitato).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-281">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="7cbb3-282">Impostazioni consigliate:</span><span class="sxs-lookup"><span data-stu-id="7cbb3-282">Recommended settings:</span></span>
- <span data-ttu-id="7cbb3-283">Eseguire l'archiviazione Sense = ogni giorno.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-283">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="7cbb3-284">Eliminare i file temporanei che le app non usano = ogni 14 giorni (almeno).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-284">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="7cbb3-285">Eliminare i file nella cartella download se sono presenti da oltre 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-285">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="7cbb3-286">OneDrive: il contenuto diventa online solo se non viene aperto per più di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-286">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <span data-ttu-id="7cbb3-287">Modalità tablet</span><span class="sxs-lookup"><span data-stu-id="7cbb3-287">Tablet mode</span></span>

<span data-ttu-id="7cbb3-288">Attivare la modalità tablet, se necessario per esigenze di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-288">Turn on Tablet mode if desired for accessibility needs.</span></span>

### <span data-ttu-id="7cbb3-289">Power Management</span><span class="sxs-lookup"><span data-stu-id="7cbb3-289">Power management</span></span>

> [!NOTE]
> <span data-ttu-id="7cbb3-290">Prima di eseguire la procedura seguente, consultare il reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S da criteri globali di gestione dell'alimentazione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-290">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="7cbb3-291">Alcune impostazioni di Power Management possono disabilitare la funzione rilevamento presenza.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-291">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="7cbb3-292">Cercare **Centro software** e aprirlo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-292">Search for **Software Center** and open it.</span></span>
2. <span data-ttu-id="7cbb3-293">Selezionare le **Opzioni** nel riquadro di spostamento.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-293">Select **Options** in the navigation pane.</span></span>
3. <span data-ttu-id="7cbb3-294">Espandere la sezione **Power Management** e selezionare non **applicare le impostazioni di alimentazione dal reparto IT al computer in**uso.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-294">Expand the **Power management** section and select **Do not apply power settings from my IT department to this computer**.</span></span>

   ![Impostazioni software](images/soft-cntr.png)

### <span data-ttu-id="7cbb3-296">Impostazioni audio</span><span class="sxs-lookup"><span data-stu-id="7cbb3-296">Sound settings</span></span>

1. <span data-ttu-id="7cbb3-297">Cercare **le impostazioni audio** e aprire questa pagina.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-297">Search for **Sounds settings** and open this page.</span></span>
2. <span data-ttu-id="7cbb3-298">Selezionare **Pannello di controllo audio** a destra e selezionare la scheda **suoni** .</span><span class="sxs-lookup"><span data-stu-id="7cbb3-298">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>
3. <span data-ttu-id="7cbb3-299">In **eventi programma** imposta **dispositivo Connetti** e **Disconnetti dispositivo** su **nessuno**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-299">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <span data-ttu-id="7cbb3-300">Notifiche di tacitazione</span><span class="sxs-lookup"><span data-stu-id="7cbb3-300">Silence notifications</span></span>

1. <span data-ttu-id="7cbb3-301">Cercare l' **assistenza per lo stato attiva** e aprire questa pagina.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-301">Search for **Focus assist** and open this page.</span></span>
2. <span data-ttu-id="7cbb3-302">Selezionare **solo sveglie**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-302">Select **Alarms Only**.</span></span> <span data-ttu-id="7cbb3-303">Verrà evitato il riquadri a comparsa di notifica costante.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-303">This will avoid constant notification flyouts.</span></span>

### <span data-ttu-id="7cbb3-304">Pulizia disco</span><span class="sxs-lookup"><span data-stu-id="7cbb3-304">Disk Cleanup</span></span>

1. <span data-ttu-id="7cbb3-305">Cercare **pulizia disco** e aprire l'app.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-305">Search for **Disk Cleanup** and open this app.</span></span>
2. <span data-ttu-id="7cbb3-306">In **file da eliminare**selezionare i file che si desidera eliminare.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-306">Under **Files to delete**, select the files you wish to delete.</span></span> 
3. <span data-ttu-id="7cbb3-307">Selezionare anche **Pulisci file di sistema**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-307">Also select **Clean up system files**.</span></span>

## <span data-ttu-id="7cbb3-308">Completare e verificare</span><span class="sxs-lookup"><span data-stu-id="7cbb3-308">Complete and verify</span></span>

1. <span data-ttu-id="7cbb3-309">Cercare e installare tutti gli aggiornamenti di Windows.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-309">Scan for and install all Windows Updates.</span></span>
2. <span data-ttu-id="7cbb3-310">Aggiornare i criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="7cbb3-310">Update Group Policy</span></span>
    1. <span data-ttu-id="7cbb3-311">In un prompt dei comandi con privilegi elevati, immettere **gpupdate/force/boot/wait: 0**.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-311">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
3. <span data-ttu-id="7cbb3-312">Riavviare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-312">Reboot the device.</span></span>
4. <span data-ttu-id="7cbb3-313">Verificare le app della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-313">Verify taskbar apps.</span></span>
    - <span data-ttu-id="7cbb3-314">App Connect</span><span class="sxs-lookup"><span data-stu-id="7cbb3-314">Connect App</span></span>
    - <span data-ttu-id="7cbb3-315">Icona Blocca</span><span class="sxs-lookup"><span data-stu-id="7cbb3-315">Lock Icon</span></span>
    - <span data-ttu-id="7cbb3-316">Snip & sketch</span><span class="sxs-lookup"><span data-stu-id="7cbb3-316">Snip & Sketch</span></span>
    - <span data-ttu-id="7cbb3-317">Teams (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="7cbb3-317">Teams (if applicable)</span></span>
    - <span data-ttu-id="7cbb3-318">App di Office (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="7cbb3-318">Office Apps (if applicable)</span></span>
    - <span data-ttu-id="7cbb3-319">App Surface</span><span class="sxs-lookup"><span data-stu-id="7cbb3-319">Surface App</span></span>
    - <span data-ttu-id="7cbb3-320">Lavagna</span><span class="sxs-lookup"><span data-stu-id="7cbb3-320">Whiteboard</span></span>
5. <span data-ttu-id="7cbb3-321">Verificare il rilevamento della presenza.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-321">Verify presence detection.</span></span>
    - <span data-ttu-id="7cbb3-322">Il rilevamento della presenza sarà un'icona verde nella barra delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="7cbb3-322">Presence detection will be a green icon in the system tray</span></span>
6. <span data-ttu-id="7cbb3-323">Verificare che la proiezione in questo PC sia abilitata con l'app Connect (l'applicazione non deve essere in corso prima della connessione).</span><span class="sxs-lookup"><span data-stu-id="7cbb3-323">Verify projecting to this PC is enabled with the Connect App (the application does not need to be running before connecting).</span></span>
7. <span data-ttu-id="7cbb3-324">Verificare le impostazioni di alimentazione e sospensione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-324">Verify power and sleep settings.</span></span>
    - <span data-ttu-id="7cbb3-325">Salvaschermo: 15 minuti, impostato su (nessuno), mistificare o vuoto; casella di controllo per la richiesta di password selezionata</span><span class="sxs-lookup"><span data-stu-id="7cbb3-325">Screen Saver: 15 minutes, set to (none), Mystify or Blank; check box for requiring password is checked</span></span>
    - <span data-ttu-id="7cbb3-326">Schermo: 2 ore</span><span class="sxs-lookup"><span data-stu-id="7cbb3-326">Screen: 2 hours</span></span>
    - <span data-ttu-id="7cbb3-327">PC: 4 ore</span><span class="sxs-lookup"><span data-stu-id="7cbb3-327">PC: 4 hours</span></span>
8. <span data-ttu-id="7cbb3-328">Verificare che Windows Hello funzioni.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-328">Verify Windows Hello is working.</span></span>
9. <span data-ttu-id="7cbb3-329">Verificare le impostazioni di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-329">Verify power settings.</span></span>
10. <span data-ttu-id="7cbb3-330">Verificare la sincronizzazione le impostazioni sono disabilitate.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-330">Verify sync your settings is disabled.</span></span>
11. <span data-ttu-id="7cbb3-331">Verificare le app di avvio.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-331">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="7cbb3-332">Dopo l'installazione e la configurazione di Windows 10, l'hub di Surface 2S può essere gestito proprio come qualsiasi altro dispositivo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="7cbb3-332">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <span data-ttu-id="7cbb3-333">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="7cbb3-333">Related topics</span></span>

[<span data-ttu-id="7cbb3-334">Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="7cbb3-334">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>](surface-hub-2s-migrate-os.md)

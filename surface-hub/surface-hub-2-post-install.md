---
title: Configurare Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo include suggerimenti per garantire la migliore esperienza quando si usa un computer con tocco su schermo di grandi dimensioni e penna personalizzato.
keywords: Surface Hub, Windows 10, desktop, installare, configurazione
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.collection: M365-modern-desktop
ms.topic: article
ms.date: 12/08/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: 076d29462ffb949492291e120bcdad538f4287ec
ms.sourcegitcommit: e859374f90d640a5cd4be1c8dcc823bcd537ebdc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "11393596"
---
# <a name="configure-windows-10-pro-or-enterprise-on-surface-hub-2"></a><span data-ttu-id="e825c-104">Configurare Windows 10 Pro o Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e825c-104">Configure Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

<span data-ttu-id="e825c-105">Dopo aver completato il processo di installazione della migrazione a Windows 10 Pro o Enterprise, puoi eseguire la procedura seguente per configurare le app e le impostazioni nel dispositivo Surface Hub 2.</span><span class="sxs-lookup"><span data-stu-id="e825c-105">After you have completed the installation process of migrating to Windows 10 Pro or Enterprise, you can perform the following steps to configure apps and settings on your Surface Hub 2.</span></span> <span data-ttu-id="e825c-106">Questi passaggi sono consigliati per garantire la migliore esperienza quando si usa questo computer personalizzato con tocco su schermo grande e penna.</span><span class="sxs-lookup"><span data-stu-id="e825c-106">These steps are recommended to ensure the best experience when using this personalized large screen touch and pen computer.</span></span>

<span data-ttu-id="e825c-107">Durante l'esecuzione di questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.</span><span class="sxs-lookup"><span data-stu-id="e825c-107">When performing these steps, you might find it useful to use a wired or wireless keyboard and mouse.</span></span>

## <a name="configure-system-settings"></a><span data-ttu-id="e825c-108">Configurare le impostazioni di sistema</span><span class="sxs-lookup"><span data-stu-id="e825c-108">Configure system settings</span></span>

1. <span data-ttu-id="e825c-109">Accedi con un account con privilegi di amministratore locale nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-109">Sign in with an account that has local administrator privileges on the device.</span></span>  

    - <span data-ttu-id="e825c-110">Nei dispositivi aggiunti ad Azure AD, l'utente che esegue l'aggiunta ad Azure AD viene aggiunto automaticamente al gruppo di amministratori locali.</span><span class="sxs-lookup"><span data-stu-id="e825c-110">On Azure AD joined devices, the user that performs the Azure AD join is automatically added to the local administrator group.</span></span> <span data-ttu-id="e825c-111">Gli amministratori globali di Azure AD e gli amministratori dei dispositivi Azure AD <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> sono anche amministratori </a> locali.</span><span class="sxs-lookup"><span data-stu-id="e825c-111">Azure AD global administrators and Azure AD devices administrators are <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank">also local administrators</a>.</span></span> 
    
    - <span data-ttu-id="e825c-112">È possibile digitare **net localgroup administrators al** prompt dei comandi per elencare gli account con diritti di amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="e825c-112">You can type **net localgroup administrators** at a command prompt to list the accounts that have local administrator rights.</span></span>
    
2. <span data-ttu-id="e825c-113">Rinomina il dispositivo usando un nome descrittivo, ad esempio **nomeutente-SHub-Desktop.**</span><span class="sxs-lookup"><span data-stu-id="e825c-113">Rename the device using a friendly name, for example: **username-SHub-Desktop**.</span></span>

3. <span data-ttu-id="e825c-114">Seleziona **Start**  >  **Settings**  >  **Accounts**  >  **Sync your settings** and turn Sync **settings** off.</span><span class="sxs-lookup"><span data-stu-id="e825c-114">Select **Start** > **Settings** > **Accounts** > **Sync your settings** and turn **Sync settings** off.</span></span> 

    - <span data-ttu-id="e825c-115">Le impostazioni usate qui sono progettate per abilitare la migliore esperienza di tocco su schermo grande e pertanto potresti non voler sincronizzare altri dispositivi.</span><span class="sxs-lookup"><span data-stu-id="e825c-115">The settings used here are intended to enable the best large-screen touch experience, and therefore you may not want to sync other devices.</span></span>
    
4. <span data-ttu-id="e825c-116">Riavvia il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-116">Restart the device.</span></span>

## <a name="enable-the-touch-keyboard-and-touchpad"></a><span data-ttu-id="e825c-117">Abilitare la tastiera virtuale e il touchpad</span><span class="sxs-lookup"><span data-stu-id="e825c-117">Enable the touch keyboard and touchpad</span></span>

1. <span data-ttu-id="e825c-118">Seleziona **Start**  >  **Settings**  >  **Devices**  >  **Typing** e turn **Show the touch keyboard when not in tablet mode and there's no keyboard attached** on.</span><span class="sxs-lookup"><span data-stu-id="e825c-118">Select **Start** > **Settings** > **Devices** > **Typing** and turn **Show the touch keyboard when not in tablet mode and there's no keyboard attached** on.</span></span>

2. <span data-ttu-id="e825c-119">Tocca e tieni premuto o fai clic con il pulsante destro del mouse sulla barra delle applicazioni e quindi scegli Mostra pulsante **tastiera virtuale** e Mostra **pulsante touchpad.**</span><span class="sxs-lookup"><span data-stu-id="e825c-119">Tap and hold or right-click the taskbar and then select **Show touch keyboard button** and **Show touchpad button**.</span></span> 

    - <span data-ttu-id="e825c-120">La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad virtuale consente selezioni precise, descrizioni dello schermo al passaggio del mouse o come alternativa al tocco e alla sospensione per fare clic con il pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="e825c-120">The touch keyboard is helpful for direct user input, and the virtual touchpad helps with precise selections, hovering screen tips, or as an alternative to tap and hold for right-click.</span></span> 
    
    - <span data-ttu-id="e825c-121">Vedi l'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e825c-121">See the following example.</span></span>

      ![Impostazioni di tocco](images/touch.png)

3. <span data-ttu-id="e825c-123">Configura la tastiera virtuale su QWERTY e mobile.</span><span class="sxs-lookup"><span data-stu-id="e825c-123">Configure the touch keyboard to QWERTY and floating.</span></span>

    1. <span data-ttu-id="e825c-124">Seleziona **l'icona Tastiera** sulla barra delle applicazioni per visualizzare la tastiera virtuale.</span><span class="sxs-lookup"><span data-stu-id="e825c-124">Select the **Keyboard** icon on the taskbar to show the touch keyboard.</span></span>
    
    1. <span data-ttu-id="e825c-125">Sulla tastiera virtuale seleziona l'icona della tastiera nell'angolo superiore sinistro per aprire le impostazioni della tastiera.</span><span class="sxs-lookup"><span data-stu-id="e825c-125">On the touch keyboard, select the keyboard icon in the upper left corner to open keyboard settings.</span></span>
    
    1. <span data-ttu-id="e825c-126">Selezionare l'ultimo tipo di tastiera nella riga superiore per abilitare QWERTY e l'ultima opzione nella seconda riga per abilitare la virgola mobile, operazione molto utile su questo grande schermo.</span><span class="sxs-lookup"><span data-stu-id="e825c-126">Select the next to last keyboard type on the top row to enable QWERTY, and the last option on the second row to enable floating, which is very helpful on this large screen.</span></span> <span data-ttu-id="e825c-127">Vedere gli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="e825c-127">See the following examples.</span></span>

       ![Impostazioni della tastiera](images/kbd.png)
 
4. <span data-ttu-id="e825c-129">Configurare le impostazioni della tastiera soft.</span><span class="sxs-lookup"><span data-stu-id="e825c-129">Configure the soft keyboard settings.</span></span>

    1. <span data-ttu-id="e825c-130">Seleziona **l'icona Impostazioni** sulla tastiera virtuale o cerca e apri impostazioni **di digitazione.**</span><span class="sxs-lookup"><span data-stu-id="e825c-130">Select the **Settings** icon on the touch keyboard or search for and open **Typing settings**.</span></span>
    
       ![impostazioni della tastiera soft](images/sh2-softkeyboard.png)

    1. <span data-ttu-id="e825c-132">Abilita tutte le opzioni in Controllo ortografia, digitazione e tastiera virtuale.</span><span class="sxs-lookup"><span data-stu-id="e825c-132">Enable all the options under Spelling, Typing, and Touch keyboard.</span></span>


<span data-ttu-id="e825c-133">L'esempio seguente mostra il trackpad, utile per spostarsi e selezionare le opzioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-133">The following example shows the trackpad, which is useful to navigate and select options.</span></span> <span data-ttu-id="e825c-134">La tastiera su schermo viene usata per eseguire ricerche in Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="e825c-134">The onscreen keyboard is being used to search the Microsoft Store:</span></span>

![Uso del trackpad](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a><span data-ttu-id="e825c-136">Configurare Bluetooth tastiera e mouse (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="e825c-136">Configure Bluetooth keyboard and mouse (optional)</span></span>

<span data-ttu-id="e825c-137">Connetti una tastiera e un mouse se usi il dispositivo come dispositivo Windows principale o lo usi spesso per il lavoro di digitazione o precisione.</span><span class="sxs-lookup"><span data-stu-id="e825c-137">Connect a keyboard and mouse if you are using the device as your primary Windows device, or you use it often for typing or precision work.</span></span>

<span data-ttu-id="e825c-138">Se il dispositivo Surface Hub è vicino a un PC, puoi usare il mouse senza bordi per spostarsi facilmente tra <a href="https://aka.ms/mm" target="_blank"> Surface Hub e il </a> PC.</span><span class="sxs-lookup"><span data-stu-id="e825c-138">If your Surface Hub device is near to a PC, you can use <a href="https://aka.ms/mm" target="_blank"> Mouse without Borders</a> to move seamlessly between the Surface Hub and the PC.</span></span> <span data-ttu-id="e825c-139">Per altre informazioni, vedi <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> il download microsoft da The Garage: Mouse senza bordi.</span><span class="sxs-lookup"><span data-stu-id="e825c-139">For more information, see <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> Microsoft download from The Garage: Mouse without Borders.</span></span> </a>

## <a name="example-of-taskbar-layout"></a><span data-ttu-id="e825c-140">Esempio di layout della barra delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="e825c-140">Example of Taskbar layout</span></span>

<span data-ttu-id="e825c-141">Dopo aver completato i passaggi seguenti per configurare Surface Hub 2 per Windows 10 Professional o Enterprise, ti consigliamo di usare l'aggiunta delle applicazioni più usate alla barra delle applicazioni per un avvio rapido con un solo tocco di ogni applicazione.</span><span class="sxs-lookup"><span data-stu-id="e825c-141">After completing the below steps to setup/configure your Surface Hub 2 for Windows 10 Professional or Enterprise, we recommend you utilize pinning your most used applications to the Taskbar for a quick one-touch launch of each application.</span></span> <span data-ttu-id="e825c-142">Di seguito è riportato un esempio dell'aspetto della barra delle applicazioni:</span><span class="sxs-lookup"><span data-stu-id="e825c-142">Below is an example of what your taskbar could look like:</span></span>

 ![Layout della barra delle applicazioni](images/taskblyt.png)
### <a name="update-installed-apps"></a><span data-ttu-id="e825c-144">Aggiornare le app installate</span><span class="sxs-lookup"><span data-stu-id="e825c-144">Update installed apps</span></span>

<span data-ttu-id="e825c-145">Per aggiornare tutte le app dello Store installate:</span><span class="sxs-lookup"><span data-stu-id="e825c-145">To update all installed Store apps:</span></span>

1. <span data-ttu-id="e825c-146">Apri l'app di Microsoft Store e seleziona **i puntini** di sospensione Vedi altri puntini di sospensione nell'angolo in alto a destra.</span><span class="sxs-lookup"><span data-stu-id="e825c-146">Open Microsoft Store app and select the **See more** ellipsis in the top-right corner.</span></span>
2. <span data-ttu-id="e825c-147">Seleziona **Download e aggiornamenti.**</span><span class="sxs-lookup"><span data-stu-id="e825c-147">Select **Downloads and updates.**</span></span>
3. <span data-ttu-id="e825c-148">Selezionare **Ottieni aggiornamenti**</span><span class="sxs-lookup"><span data-stu-id="e825c-148">Select **Get updates**</span></span>

### <a name="scan-for-and-install-all-windows-updates"></a><span data-ttu-id="e825c-149">Cercare e installare tutti gli aggiornamenti di Windows</span><span class="sxs-lookup"><span data-stu-id="e825c-149">Scan for and install all Windows Updates</span></span>
<span data-ttu-id="e825c-150">Dopo la migrazione a Windows 10 Professional o Windows 10 Enterprise, potrebbero essere disponibili aggiornamenti di manutenzione e funzionalità da installare.</span><span class="sxs-lookup"><span data-stu-id="e825c-150">After migrating to Windows 10 Professional or Windows 10 Enterprise, there may be servicing and feature updates available for you to install.</span></span> 

- <span data-ttu-id="e825c-151">Vai a **Impostazioni**  >  **aggiornamento & sicurezza >** e quindi seleziona Verifica disponibilità **aggiornamenti.**</span><span class="sxs-lookup"><span data-stu-id="e825c-151">Go to **Settings** > **Update & Security** > and then select **Check for updates**.</span></span>
- <span data-ttu-id="e825c-152">Se sono presenti aggiornamenti, installarli, riavviarli e quindi ripetere il processo fino a quando non viene visualizzata la notifica seguente:</span><span class="sxs-lookup"><span data-stu-id="e825c-152">If there are any updates, install them, reboot, and then repeat the process until you see the following notification:</span></span>

> [!div class="mx-imgBorder"]
> ![Notifica "Sei aggiornato" di Windows Update](images/wustatus.png)


## <a name="onedrive-for-business"></a><span data-ttu-id="e825c-154">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="e825c-154">OneDrive for Business</span></span>

<span data-ttu-id="e825c-155">Usare <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business </a> per condividere facilmente strumenti, log e altri file tra tutti i dispositivi di lavoro.</span><span class="sxs-lookup"><span data-stu-id="e825c-155">Use <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business</a> to easily share tools, logs, and other files between all your work devices.</span></span>

- <span data-ttu-id="e825c-156">OneDrive consente di condividere i file di lavoro tra laptop, Surface Hub Desktop e dispositivi mobili gestiti da Intune.</span><span class="sxs-lookup"><span data-stu-id="e825c-156">OneDrive enables you to share your work files between your laptops, Surface Hub Desktop, and your Intune-managed mobile devices.</span></span> <span data-ttu-id="e825c-157">I file possono essere modificati su qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.</span><span class="sxs-lookup"><span data-stu-id="e825c-157">Files can be edited on any device, and all network connected devices will be updated with the changes.</span></span>

- <span data-ttu-id="e825c-158">Considerando le dimensioni del dispositivo Surface Hub SSD (128 GB), se si configura OneDrive nel dispositivo desktop Surface Hub, assicurarsi che la configurazione predefinita sia mantenere i file online e scaricare i file mentre vengono utilizzati.</span><span class="sxs-lookup"><span data-stu-id="e825c-158">Considering the size of the Surface Hub SSD (128GB), if you configure OneDrive on your Surface Hub Desktop device, make sure the default configuration is to keep the files online and download files as you use them.</span></span>

<span data-ttu-id="e825c-159">Per configurare OneDrive per il download \*\*\*\* dei file solo quando necessario, impostare File su richiesta su Risparmiare spazio e scaricare i file **mentre vengono utilizzati.**</span><span class="sxs-lookup"><span data-stu-id="e825c-159">To configure OneDrive to download files only when needed, set the **Files On-Demand** setting to **Save space and download files as you use them**.</span></span> <span data-ttu-id="e825c-160">Per altre informazioni, vedi <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Eseguire query e impostare gli stati file su richiesta in </a> Windows.</span><span class="sxs-lookup"><span data-stu-id="e825c-160">For more information, see <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Query and set Files On-Demand states in Windows</a>.</span></span>

![Impostazioni di OneDrive](images/onedrive.png)

> [!NOTE]
> <span data-ttu-id="e825c-162">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span><span class="sxs-lookup"><span data-stu-id="e825c-162">You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.</span></span>

## <a name="sharepoint-and-teams"></a><span data-ttu-id="e825c-163">SharePoint e Teams</span><span class="sxs-lookup"><span data-stu-id="e825c-163">SharePoint and Teams</span></span>

<span data-ttu-id="e825c-164">I file di SharePoint e del Canale di Teams possono anche essere sincronizzati localmente con i dispositivi desktop, ad esempio laptop e Surface Hub, usando il motore di sincronizzazione di OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e825c-164">SharePoint and Teams Channel files can also sync locally to your desktop devices, such as laptops and Surface Hubs, using the OneDrive sync engine.</span></span>

<span data-ttu-id="e825c-165">Per sincronizzare i file aziendali interni con l'unità locale con l'app di sincronizzazione di OneDrive:</span><span class="sxs-lookup"><span data-stu-id="e825c-165">To sync internal corporate files to your local drive with the OneDrive sync app:</span></span>

1. <span data-ttu-id="e825c-166">Passare a un sito di SharePoint e passare alla directory dei documenti di primo livello per i file che si desidera visualizzare o modificare dal dispositivo locale.</span><span class="sxs-lookup"><span data-stu-id="e825c-166">Go to a SharePoint site and navigate to the top-level document directory for files that you are interested in viewing or editing from your local device.</span></span>

2. <span data-ttu-id="e825c-167">Fare clic sul **pulsante Sincronizza** nella parte superiore della barra multifunzione di SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e825c-167">Select on the **Sync** button on the top of the SharePoint ribbon.</span></span>

3. <span data-ttu-id="e825c-168">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive.**</span><span class="sxs-lookup"><span data-stu-id="e825c-168">Select on **Open** on the popup **This site is trying to open Microsoft OneDrive**.</span></span>

4. <span data-ttu-id="e825c-169">Verificare che i file di SharePoint siano sincronizzati con l'unità locale selezionando l'icona di OneDrive nella parte inferiore destra della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-169">Verify that the SharePoint files are synchronizing to your local drive by selecting on the OneDrive icon at the bottom right of the taskbar.</span></span>

5. <span data-ttu-id="e825c-170">Verificare che la configurazione sia impostata per mantenere i file online e scaricarli solo quando vengono utilizzati:</span><span class="sxs-lookup"><span data-stu-id="e825c-170">Verify the configuration is set to keep the files online and download the files only as you use them:</span></span>

    1. <span data-ttu-id="e825c-171">Apri Esplora file.</span><span class="sxs-lookup"><span data-stu-id="e825c-171">Open file explorer.</span></span>
    
    2. <span data-ttu-id="e825c-172">Passare al nome di SharePoint e fare clic con il pulsante destro del mouse. ad esempio, \*\*Contoso \ \<SharePoint Document Folder Name\> \*\*.</span><span class="sxs-lookup"><span data-stu-id="e825c-172">Navigate to and right click your SharePoint name; for example, **Contoso \ \<SharePoint Document Folder Name\>**.</span></span>
    
    3. <span data-ttu-id="e825c-173">Selezionare **Libera spazio.**</span><span class="sxs-lookup"><span data-stu-id="e825c-173">Select **Free up space**.</span></span>
    
    4. <span data-ttu-id="e825c-174">Nella colonna Stato verrà visualizzato lo stato di file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="e825c-174">The Status column will display the status of files and folders.</span></span> <span data-ttu-id="e825c-175">Per ulteriori informazioni, vedere <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sincronizzare i file di SharePoint con il client di sincronizzazione di OneDrive. </a></span><span class="sxs-lookup"><span data-stu-id="e825c-175">For more information, see <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sync SharePoint files with the OneDrive sync client</a>.</span></span>
    
6. <span data-ttu-id="e825c-176">I file del canale di Teams vengono archiviati nei siti di SharePoint, con tutte le stesse funzionalità dei documenti di SharePoint, tra cui la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali.</span><span class="sxs-lookup"><span data-stu-id="e825c-176">Teams Channel files are stored in SharePoint sites, with all of the same SharePoint document functionality, including version history and synchronizing to your local desktop devices.</span></span> <span data-ttu-id="e825c-177">Per sincronizzare i file del canale di Teams:</span><span class="sxs-lookup"><span data-stu-id="e825c-177">To sync Teams Channel files:</span></span>

    1. <span data-ttu-id="e825c-178">Passare al Canale di Teams di interesse e selezionare la **scheda File** nella parte superiore.</span><span class="sxs-lookup"><span data-stu-id="e825c-178">Navigate to the Teams Channel of interest and select the **Files** tab at the top.</span></span> <span data-ttu-id="e825c-179">Selezionare quindi **Sincronizza.** The files will start synchronizing and will be visible in File Explorer at \*\*Desktop \ Contoso \ \<name of the Teams Channel\> \*\*.</span><span class="sxs-lookup"><span data-stu-id="e825c-179">Then select **Sync**. The files will start synchronizing and will be visible in File Explorer at **Desktop \ Contoso \ \<name of the Teams Channel\>**.</span></span>
    
    2. <span data-ttu-id="e825c-180">Utilizzare la stessa procedura utilizzata per sincronizzare i siti di SharePoint per mantenere i file nel cloud e scaricarli solo quando vengono usati, toccando e tenendo premuto o facendo clic con il pulsante destro del mouse in Esplora file nel nome del canale di Teams e selezionando Libera **spazio.**</span><span class="sxs-lookup"><span data-stu-id="e825c-180">Use the same procedure that you used for synchronizing SharePoint sites to keep the files in the cloud and only download them when you use them, by tap and hold or right-click in File Explorer on the Teams Channel name, and then selecting **Free up space**.</span></span>

## <a name="surface-hub-pen-settings"></a><span data-ttu-id="e825c-181">Impostazioni della penna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="e825c-181">Surface Hub pen settings</span></span>

**<span data-ttu-id="e825c-182">Associare la Bluetooth penna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="e825c-182">Pair the Bluetooth Surface Hub Pen</span></span>**

<span data-ttu-id="e825c-183">Associa la penna per mantenere aggiornato il firmware della penna, impostare i tasti di scelta rapida della penna e ottenere informazioni sulla carica della batteria nella pagina delle impostazioni del dispositivo Bluetooth o nell'app Surface:</span><span class="sxs-lookup"><span data-stu-id="e825c-183">Pair the pen to keep the pen firmware up to date, set the pen shortcuts, and get battery charge information on the Bluetooth device settings page, or in the Surface app:</span></span>

1. <span data-ttu-id="e825c-184">Seleziona **Start**  >  **Settings**  >  **Devices**.</span><span class="sxs-lookup"><span data-stu-id="e825c-184">Select **Start** > **Settings** > **Devices**.</span></span>

2. <span data-ttu-id="e825c-185">Seleziona **Aggiungi Bluetooth o altro dispositivo.**</span><span class="sxs-lookup"><span data-stu-id="e825c-185">Select **Add Bluetooth or other device**.</span></span>

3. <span data-ttu-id="e825c-186">Scegliere **Bluetooth**.</span><span class="sxs-lookup"><span data-stu-id="e825c-186">Choose **Bluetooth**.</span></span>

4. <span data-ttu-id="e825c-187">Rimuovi il pulsante di coda della penna e scossa per scollegare la connessione della batteria.</span><span class="sxs-lookup"><span data-stu-id="e825c-187">Remove the pen tail button and shake to disconnect the battery connection.</span></span>

5. <span data-ttu-id="e825c-188">Rimutare il tappo e tenere premuto il tappo fino a quando il LED di associazione lampeggia.</span><span class="sxs-lookup"><span data-stu-id="e825c-188">Put the cap back on and press and hold the cap until the pairing LED flashes.</span></span>

6. <span data-ttu-id="e825c-189">Nelle impostazioni del dispositivo Surface Hub Bluetooth scegliere **Penna per Surface Hub 2.**</span><span class="sxs-lookup"><span data-stu-id="e825c-189">On the Surface Hub Bluetooth settings, choose **Surface Hub 2 Pen**.</span></span>

7. <span data-ttu-id="e825c-190">Completare l'operazione di associazione.</span><span class="sxs-lookup"><span data-stu-id="e825c-190">Complete the pairing operation.</span></span> 

8. <span data-ttu-id="e825c-191">Se l'associazione non riesce, puoi tentare di associare di nuovo la penna.</span><span class="sxs-lookup"><span data-stu-id="e825c-191">If the pairing is not successful, you can attempt to pair the pen again.</span></span> <span data-ttu-id="e825c-192">Se non funziona, puoi verificare se la batteria è carica verificando che la penna funzioni nell'applicazione Whiteboard.</span><span class="sxs-lookup"><span data-stu-id="e825c-192">If that doesn't work, you can test to see if the battery is charged by verifying the pen works in the Whiteboard application.</span></span> <span data-ttu-id="e825c-193">In caso contrario, sostituisci la batteria e quindi prova ad associare di nuovo la penna.</span><span class="sxs-lookup"><span data-stu-id="e825c-193">If not, then replace the battery and then try to pair the pen again.</span></span> <span data-ttu-id="e825c-194">Se necessario, riavviare il dispositivo e riprovare.</span><span class="sxs-lookup"><span data-stu-id="e825c-194">If necessary, restart the device and then try again.</span></span>

<span data-ttu-id="e825c-195">**Impostare i tasti di scelta rapida della penna** La penna di Surface Hub ha un pulsante di scelta rapida a volte definito "clic di coda".</span><span class="sxs-lookup"><span data-stu-id="e825c-195">**Set pen shortcuts** The Surface Hub pen has a shortcut button sometimes referred to as a "tail click".</span></span> <span data-ttu-id="e825c-196">La configurazione dei tasti di scelta rapida richiede la prima associazione della penna, come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="e825c-196">Configuring shortcuts requires you to first pair the pen, as described earlier.</span></span>

1. <span data-ttu-id="e825c-197">Cerca Penna e seleziona Le impostazioni **di & windows ink.**</span><span class="sxs-lookup"><span data-stu-id="e825c-197">Search for Pen and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="e825c-198">Nella parte inferiore della pagina seleziona i tasti di scelta rapida della penna che apre la finestra di dialogo, illustrata di seguito:</span><span class="sxs-lookup"><span data-stu-id="e825c-198">Near the bottom of the page, select Pen shortcuts which opens the dialog box, shown here:</span></span>

   ![Tasti di scelta rapida della penna](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a><span data-ttu-id="e825c-200">Configurazione della fotocamera</span><span class="sxs-lookup"><span data-stu-id="e825c-200">Camera configuration</span></span>

<span data-ttu-id="e825c-201">Puoi montare la fotocamera nella parte superiore o su entrambi i lati del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-201">You can mount the camera on the top or on either side of the device.</span></span> <span data-ttu-id="e825c-202">Monta la fotocamera in una posizione per ottimizzare l'angolo della fotocamera se utilizzi l'hub con un supporto desktop invece di un carrello o se sei vicino all'Hub.</span><span class="sxs-lookup"><span data-stu-id="e825c-202">Mount the camera in a position to optimize the camera angle if you are using the Hub with a desktop stand instead of a cart, or are in close proximity to the Hub.</span></span> <span data-ttu-id="e825c-203">La fotocamera non ruota automaticamente, quindi devi avere un tasto esadecimale di 2 mm per ruotare manualmente la fotocamera.</span><span class="sxs-lookup"><span data-stu-id="e825c-203">The camera does not auto-rotate, so you need to have a 2mm hex key to manually rotate the camera.</span></span> 

<span data-ttu-id="e825c-204">Per altre informazioni su come montare la fotocamera e ruotarla manualmente, vedi l'orientamento dell'obiettivo della <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> fotocamera di Surface Hub 2S. </a></span><span class="sxs-lookup"><span data-stu-id="e825c-204">For more information on how to side-mount the camera and rotate the camera manually, see <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> Surface Hub 2S camera lens orientation</a>.</span></span>

## <a name="windows-hello-configuration"></a><span data-ttu-id="e825c-205">Configurazione di Windows Hello</span><span class="sxs-lookup"><span data-stu-id="e825c-205">Windows Hello configuration</span></span>

<span data-ttu-id="e825c-206">Surface Hub 2S che esegue Windows 10 Enterprise consente la famiglia completa di applicazioni desktop Win32 e le opzioni biometriche di Windows Hello.</span><span class="sxs-lookup"><span data-stu-id="e825c-206">Surface Hub 2S running Windows 10 Enterprise allows the full suite of Win32 desktop applications as well as biometric Windows Hello options.</span></span> <span data-ttu-id="e825c-207">L'accessorio lettore di impronta digitale di Surface Hub 2 può essere collegato a qualsiasi porta USB-C nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-207">The Surface Hub 2 Fingerprint Reader accessory can be plugged into any USB-C port on the device.</span></span> 

<span data-ttu-id="e825c-208">Per ordinare un lettore di impronta digitale di Surface Hub 2 o visualizzare le specifiche tecniche, vedi (surface-hub-2-essential-add-ons.md" target="_blank">Componenti aggiuntivi Essential per Windows 10 Pro ed Enterprise in Surface Hub </a> 2.</span><span class="sxs-lookup"><span data-stu-id="e825c-208">To order a Surface Hub 2 Fingerprint Reader or view technical specs, see (surface-hub-2-essential-add-ons.md" target="_blank">Essential add-ons for Windows 10 Pro and Enterprise on Surface Hub 2 </a>.</span></span> 

<span data-ttu-id="e825c-209">Dopo aver inserito il lettore di impronta digitale, seleziona **Start**  >  **Settings**  >  **Accounts**  >  **Sign-in options**Windows Hello  >  **Fingerprint** per registrare l'impronta digitale.</span><span class="sxs-lookup"><span data-stu-id="e825c-209">After inserting the fingerprint reader, select **Start** > **Settings** > **Accounts** > **Sign-in options** > **Windows Hello Fingerprint** to enroll your fingerprint.</span></span>

<span data-ttu-id="e825c-210">Usa un dispositivo certificato Windows Hello per il riconoscimento dei volto.</span><span class="sxs-lookup"><span data-stu-id="e825c-210">Use a Windows Hello certified device for face recognition.</span></span> <span data-ttu-id="e825c-211">La fotocamera Surface Hub 2S non supporta il riconoscimento dei facciali di Windows Hello.</span><span class="sxs-lookup"><span data-stu-id="e825c-211">The Surface Hub 2S camera does not support Windows Hello face recognition.</span></span>

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a><span data-ttu-id="e825c-212">Abilitazione di un'icona di scelta rapida della schermata di blocco sulla barra delle applicazioni</span><span class="sxs-lookup"><span data-stu-id="e825c-212">Enable a Lock Screen shortcut icon on the taskbar</span></span>

<span data-ttu-id="e825c-213">Per aggiungere un'icona alla barra delle applicazioni che abilita il blocco dello schermo con un solo tocco, in modo analogo ai tasti di scelta rapida di Windows-L:</span><span class="sxs-lookup"><span data-stu-id="e825c-213">To add an icon to the taskbar that enables one-touch screen lock similar to the Windows-L keyboard shortcut:</span></span> 

1.  <span data-ttu-id="e825c-214">Toccare e tenere premuto o fare clic con il pulsante destro del mouse sul desktop, selezionare **Nuovo**  >  **collegamento**  >  **Sfoglia**  >  **desktop**  >  **OK**  >  **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="e825c-214">Tap and hold or right-click on the desktop, select **New** > **Shortcut** > **Browse** > **Desktop** > **OK** > **Next**.</span></span>

1.  <span data-ttu-id="e825c-215">Specifica un nome per il collegamento, ad esempio **Blocca il PC,** e quindi seleziona **Fine.**</span><span class="sxs-lookup"><span data-stu-id="e825c-215">Provide a name for the shortcut such as **Lock my PC**, and then select **Finish**.</span></span>

1.  <span data-ttu-id="e825c-216">Fai clic con il pulsante destro del mouse o tocca e tieni premuto il collegamento appena creato sul desktop e seleziona **Proprietà.**</span><span class="sxs-lookup"><span data-stu-id="e825c-216">Right-click or tap and hold the newly created shortcut on the desktop, and select **Properties**.</span></span> <span data-ttu-id="e825c-217">Nella scheda **Collegamento** immettere quanto segue nel campo **Destinazione:** **Rundll32.exe User32.dll,LockWorkStation**</span><span class="sxs-lookup"><span data-stu-id="e825c-217">On the **Shortcut** tab, enter the following in the **Target** field: **Rundll32.exe User32.dll,LockWorkStation**</span></span>

1.  <span data-ttu-id="e825c-218">Seleziona il **pulsante Cambia** icona e passa a **C:\Windows\System32\imageres.dll** e seleziona un'icona da usare.</span><span class="sxs-lookup"><span data-stu-id="e825c-218">Select the **Change Icon** button and browse to **C:\Windows\System32\imageres.dll** and select an icon to use.</span></span> 

    <span data-ttu-id="e825c-219">Vedi l'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="e825c-219">See the following example:</span></span>

    ![Scegliere un'icona](images/lock.png)
    
1.  <span data-ttu-id="e825c-221">Selezionare **OK** per salvare il collegamento.</span><span class="sxs-lookup"><span data-stu-id="e825c-221">Select **OK** to save the shortcut.</span></span>

1.  <span data-ttu-id="e825c-222">Fai clic con il pulsante destro del mouse o tocca e tieni premuto il collegamento e seleziona **Aggiungi alla barra delle applicazioni.**</span><span class="sxs-lookup"><span data-stu-id="e825c-222">Right-click or tap and hold the shortcut and select **Pin to taskbar**.</span></span>

1. <span data-ttu-id="e825c-223">Dopo aver aggiunto il collegamento di blocco alla barra delle applicazioni, puoi eliminarlo dal desktop.</span><span class="sxs-lookup"><span data-stu-id="e825c-223">After you have pinned the lock shortcut to the taskbar, you can delete it from the desktop.</span></span>

## <a name="applications"></a><span data-ttu-id="e825c-224">Applicazioni</span><span class="sxs-lookup"><span data-stu-id="e825c-224">Applications</span></span>


### <a name="microsoft-whiteboard"></a><span data-ttu-id="e825c-225">Microsoft Whiteboard</span><span class="sxs-lookup"><span data-stu-id="e825c-225">Microsoft Whiteboard</span></span>

<span data-ttu-id="e825c-226">Per installare Microsoft Whiteboard:</span><span class="sxs-lookup"><span data-stu-id="e825c-226">To install the Microsoft Whiteboard:</span></span>

 - <span data-ttu-id="e825c-227">Seleziona **l'icona di Windows Ink Workspace** nell'angolo in basso a destra della barra delle applicazioni e scarica **Whiteboard.**</span><span class="sxs-lookup"><span data-stu-id="e825c-227">Select the **Windows Ink Workspace** icon on the lower right of the taskbar and download **Whiteboard**.</span></span>
 
   ![Area di lavoro input penna](images/ink.png) 

<span data-ttu-id="e825c-229">In alternativa, puoi installare Whiteboard da Microsoft Store:</span><span class="sxs-lookup"><span data-stu-id="e825c-229">Alternatively, you can install Whiteboard from the Microsoft Store:</span></span>

1. <span data-ttu-id="e825c-230">Apri l'app di Microsoft Store e cerca **Lavagna.**</span><span class="sxs-lookup"><span data-stu-id="e825c-230">Open Microsoft Store app and search for **Whiteboard**.</span></span>

2. <span data-ttu-id="e825c-231">Choose **No thanks** to sign in and use across devices.</span><span class="sxs-lookup"><span data-stu-id="e825c-231">Choose **No thanks** to sign in and use across devices.</span></span>

3. <span data-ttu-id="e825c-232">Aggiungi Whiteboard alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-232">Pin Whiteboard to the taskbar.</span></span>

### <a name="surface-app"></a><span data-ttu-id="e825c-233">App Surface</span><span class="sxs-lookup"><span data-stu-id="e825c-233">Surface app</span></span>

1. <span data-ttu-id="e825c-234">In Microsoft Store cerca **Surface.**</span><span class="sxs-lookup"><span data-stu-id="e825c-234">In the Microsoft Store, search for **Surface**.</span></span>

2. <span data-ttu-id="e825c-235">Impostare il **filtro Disponibile su** Tutti i **dispositivi.**</span><span class="sxs-lookup"><span data-stu-id="e825c-235">Set the **Available on** filter to **All devices**.</span></span>

3. <span data-ttu-id="e825c-236">Installa l'app **Surface.**</span><span class="sxs-lookup"><span data-stu-id="e825c-236">Install the **Surface** app.</span></span> <span data-ttu-id="e825c-237">Dovrebbe essere la prima app elencata.</span><span class="sxs-lookup"><span data-stu-id="e825c-237">This should be the first app listed.</span></span> <span data-ttu-id="e825c-238">Per installare l'app, potrebbe essere necessario associare l'account microsoft a Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e825c-238">You might need to associate your MSA to the Store in order to install the app.</span></span>

4. <span data-ttu-id="e825c-239">Aggiungi l'app **Surface** alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-239">Pin the **Surface** app to taskbar.</span></span>

### <a name="snip--sketch"></a><span data-ttu-id="e825c-240">Cattura e annota</span><span class="sxs-lookup"><span data-stu-id="e825c-240">Snip & Sketch</span></span>

1. <span data-ttu-id="e825c-241">Apri **l'app Snip & Sketch** e aggiungila alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-241">Open the **Snip & Sketch** app and pin it to the taskbar.</span></span>

2. <span data-ttu-id="e825c-242">Selezionare i puntini di sospensione nell'angolo superiore destro e quindi selezionare **Impostazioni.**</span><span class="sxs-lookup"><span data-stu-id="e825c-242">Select the ellipsis in the upper right corner and then select **Settings**.</span></span>

3. <span data-ttu-id="e825c-243">In **Impostazioni**attivare Copia **automatica negli Appunti,** Salva **e**Più **finestre** (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="e825c-243">In **Settings**, turn on **Auto copy to clipboard**, **Save snips**, and **Multiple windows** (optional).</span></span>

### <a name="microsoft-office"></a><span data-ttu-id="e825c-244">Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="e825c-244">Microsoft Office</span></span>

1. <span data-ttu-id="e825c-245">Aprire il <a href="https://portal.office.com/account#installs" target="_blank"> portale di Office e installare le applicazioni </a> desiderate.</span><span class="sxs-lookup"><span data-stu-id="e825c-245">Open the <a href="https://portal.office.com/account#installs" target="_blank"> Office Portal</a> and install your desired applications.</span></span>

2. <span data-ttu-id="e825c-246">Aggiungere le applicazioni di Office desiderate alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-246">Pin desired Office applications to the taskbar.</span></span>

3. <span data-ttu-id="e825c-247">Se Outlook è installato, assicurarsi di impostare il file OST di Outlook in modo da salvare solo la cache delle ultime due settimane.</span><span class="sxs-lookup"><span data-stu-id="e825c-247">If Outlook is installed, be sure to set the Outlook OST to only save last two weeks cache.</span></span> <span data-ttu-id="e825c-248">Ciò ridurrà notevolmente l'utilizzo del disco e i tempi di installazione.</span><span class="sxs-lookup"><span data-stu-id="e825c-248">This will vastly reduce disk usage and setup time.</span></span>

    - <span data-ttu-id="e825c-249">Seleziona **Impostazioni**  >  **account file** e seleziona il tuo account.</span><span class="sxs-lookup"><span data-stu-id="e825c-249">Select **File** > **Account Settings** and select your account.</span></span>
    
    - <span data-ttu-id="e825c-250">Selezionare **Modifica** e impostare il dispositivo di scorrimento per Usa **modalità cache** su 14 giorni.</span><span class="sxs-lookup"><span data-stu-id="e825c-250">Select **Change** and set the slider for **Use Cached Exchange Mode** to 14 days.</span></span>

### <a name="microsoft-teams"></a><span data-ttu-id="e825c-251">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e825c-251">Microsoft Teams</span></span>

1. <span data-ttu-id="e825c-252">Scaricare e installare <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft </a> Teams.</span><span class="sxs-lookup"><span data-stu-id="e825c-252">Download and install <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft Teams </a>.</span></span>

2. <span data-ttu-id="e825c-253">Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="e825c-253">Configure settings to Auto-start application (optional).</span></span>

3. <span data-ttu-id="e825c-254">Aggiungere Teams alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-254">Pin Teams to the taskbar.</span></span>

4. <span data-ttu-id="e825c-255">Valutare la possibilità di ridurre le notifiche di Teams nel dispositivo per evitare distrazioni (facoltativo).</span><span class="sxs-lookup"><span data-stu-id="e825c-255">Consider reducing Teams notifications on the device to avoid distractions (optional).</span></span>

   ![Notifiche di Teams](images/teams.png)

### <a name="connect-app"></a><span data-ttu-id="e825c-257">Connettere l'app</span><span class="sxs-lookup"><span data-stu-id="e825c-257">Connect app</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e825c-258">In Windows 10 versione 2004 e successive, l'app Connetti per la proiezione wireless con Miracast non è installata per impostazione predefinita, ma è disponibile come funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="e825c-258">In Windows 10, version 2004 and later, the Connect app for wireless projection using Miracast is not installed by default, but is available as an optional feature.</span></span> <span data-ttu-id="e825c-259">Se hai installato (o aggiornato) Windows versione 2004 o successiva, nella schermata Projecting to this PC potrebbe essere visualizzato quanto segue nelle impostazioni:</span><span class="sxs-lookup"><span data-stu-id="e825c-259">If you have installed (or updated to) Windows version 2004 or later, you may see the following on the Projecting to this PC screen in settings:</span></span>

![Project to this PC](images/sh2-project.png) 


1. <span data-ttu-id="e825c-261">Per installare l'app dalla pagina delle impostazioni "Progetto in questo PC", seleziona **Funzionalità**facoltative Aggiungi una funzionalità e quindi installa l'app  >  \*\*\*\* **Schermo** wireless.</span><span class="sxs-lookup"><span data-stu-id="e825c-261">To install the app from the “Projecting to this PC” settings page, select **Optional features** > **Add a feature** and then install the **Wireless Display** app.</span></span>

2. <span data-ttu-id="e825c-262">In **Alcuni dispositivi Windows e Android puoi proiettare su questo PC**quando dici che è ok, scegli:</span><span class="sxs-lookup"><span data-stu-id="e825c-262">Under **Some Windows and Android devices can project to this PC when you say it's OK**, choose:</span></span>

    - <span data-ttu-id="e825c-263">**Disponibile ovunque** se il dispositivo non si trova in una rete aziendale.</span><span class="sxs-lookup"><span data-stu-id="e825c-263">**Available everywhere** if the device is not on a corporate network.</span></span>
    - <span data-ttu-id="e825c-264">In caso contrario, **scegliere Disponibile ovunque nelle reti protette.**</span><span class="sxs-lookup"><span data-stu-id="e825c-264">Otherwise, choose **Available everywhere on secure networks**.</span></span>
    
3. <span data-ttu-id="e825c-265">In **Chiedi di proiettare in questo PC**scegliere Solo la prima **volta.**</span><span class="sxs-lookup"><span data-stu-id="e825c-265">Under **Ask to project to this PC**, choose **First time only**.</span></span>

4. <span data-ttu-id="e825c-266">In **Richiedi PIN per l'associazione**scegliere **Mai.**</span><span class="sxs-lookup"><span data-stu-id="e825c-266">Under **Require PIN for pairing**, choose **Never**.</span></span>

5. <span data-ttu-id="e825c-267">Per avviare l'app e aggiungere l'app alla barra delle applicazioni, cerca **Connetti.**</span><span class="sxs-lookup"><span data-stu-id="e825c-267">To then launch the app and pin it to the taskbar, search for **Connect**.</span></span>

6. <span data-ttu-id="e825c-268">Apri l'app.</span><span class="sxs-lookup"><span data-stu-id="e825c-268">Open the app.</span></span> <span data-ttu-id="e825c-269">Mentre l'app è aperta, fai clic con il pulsante destro del mouse sull'icona Connetti app sulla barra delle applicazioni e scegli **Aggiungi alla barra delle applicazioni.**</span><span class="sxs-lookup"><span data-stu-id="e825c-269">While the app is open, right-click on the Connect app icon on the taskbar, and select **pin to taskbar**.</span></span>

7. <span data-ttu-id="e825c-270">Chiudi quindi l'app Connetti.</span><span class="sxs-lookup"><span data-stu-id="e825c-270">Then close the Connect app.</span></span> <span data-ttu-id="e825c-271">**Project su questo PC potrebbe** non funzionare a meno che l'app non sia stata eseguita almeno una volta.</span><span class="sxs-lookup"><span data-stu-id="e825c-271">**Project to this PC** might not work unless the app has been run at least once.</span></span>

<span data-ttu-id="e825c-272">Configurazione consigliata quando non si utilizza la rete aziendale:</span><span class="sxs-lookup"><span data-stu-id="e825c-272">Recommended configuration when not on the corporate network:</span></span>

![Impostazioni a casa](images/project1.png)

<span data-ttu-id="e825c-274">Configurazione consigliata nella rete aziendale:</span><span class="sxs-lookup"><span data-stu-id="e825c-274">Recommended configuration on the corporate network:</span></span>

![Impostazioni sul lavoro](images/project2.png)

### <a name="your-phone"></a><span data-ttu-id="e825c-276">Il tuo telefono</span><span class="sxs-lookup"><span data-stu-id="e825c-276">Your Phone</span></span>

<span data-ttu-id="e825c-277">**L'app Telefono** è installata per impostazione predefinita in Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e825c-277">The **Your Phone** app is installed by default on Windows 10.</span></span> <span data-ttu-id="e825c-278">Se non è presente, puoi installarlo anche da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e825c-278">If it is not present, you can also install it from the Windows Store.</span></span>

<span data-ttu-id="e825c-279">Per informazioni sulla configurazione dell'app, vedi Come configurare il telefono in Windows 10 e sincronizzare i dati <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> tra PC e </a> telefono.</span><span class="sxs-lookup"><span data-stu-id="e825c-279">For information about setting up the app, see <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> How to set up Your Phone on Windows 10 and sync data between your PC and phone</a>.</span></span> <span data-ttu-id="e825c-280">Vedi anche <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> come risolvere i problemi comuni con l'app Telefono in Windows 10. </a></span><span class="sxs-lookup"><span data-stu-id="e825c-280">Also see <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> How to fix common problems with Your Phone app on Windows 10</a>.</span></span>

###  <a name="fancy-zones"></a><span data-ttu-id="e825c-281">Zone fantasiose</span><span class="sxs-lookup"><span data-stu-id="e825c-281">Fancy Zones</span></span>


<span data-ttu-id="e825c-282">**Fancy Zones** fa parte di una raccolta di strumenti denominata <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys </a> su GitHub.</span><span class="sxs-lookup"><span data-stu-id="e825c-282">**Fancy Zones** is part of a collection of tools called <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys</a> on GitHub..</span></span> <span data-ttu-id="e825c-283">È un ottimo modo per usare lo spazio sullo schermo in un dispositivo Surface Hub 2, offrendoti la possibilità di definire layout fissi sullo schermo ("aree") e quindi di selezionare l'app che verrà eseguita in ogni area.</span><span class="sxs-lookup"><span data-stu-id="e825c-283">It is a great way to utilize the screen real-estate on a Surface Hub 2 by giving you the ability to define fixed layouts on your display (“zones”), and then select which app will then run in each zone.</span></span> 


<span data-ttu-id="e825c-284">Il [wiki di PowerToys](https://github.com/microsoft/PowerToys/wiki) contiene istruzioni su come usare e personalizzare ogni strumento, tra cui [FancyZones.](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview)</span><span class="sxs-lookup"><span data-stu-id="e825c-284">The [PowerToys wiki](https://github.com/microsoft/PowerToys/wiki) has instructions for how to use and customize each tool, including [FancyZones](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview).</span></span> <span data-ttu-id="e825c-285">A livello elevato: dopo aver installato PowerToys, puoi selezionare o creare un layout personalizzato e quindi tenere premuto MAIUSC e trascinare o usare i tasti della tastiera per spostare un'app in esecuzione in aree specifiche.</span><span class="sxs-lookup"><span data-stu-id="e825c-285">At a high level – after installing PowerToys, you can select or create a custom layout, and then hold the shift key down and drag or use keyboard keys to move a running app into specific zones.</span></span> <span data-ttu-id="e825c-286">L'uso Bluetooth tastiera e mouse USB può essere utile oppure puoi usare la tastiera virtuale su schermo e il touchpad.</span><span class="sxs-lookup"><span data-stu-id="e825c-286">Using a Bluetooth or USB keyboard and mouse will help with this, or you can use the on-screen touch keyboard and touchpad.</span></span>

**<span data-ttu-id="e825c-287">Suggerimenti per Power Toys</span><span class="sxs-lookup"><span data-stu-id="e825c-287">Power toys tips</span></span>**
- <span data-ttu-id="e825c-288">Per ricevere notifiche tramite posta elettronica degli aggiornamenti delle versioni di PowerToys su GitHub, fai clic sul pulsante "registrazione" nella parte superiore della [pagina.](https://github.com/microsoft/PowerToys/releases)</span><span class="sxs-lookup"><span data-stu-id="e825c-288">To receive email notifications of PowerToys release updates on GitHub, click the “sign-up” button at the top of the [page](https://github.com/microsoft/PowerToys/releases).</span></span>
- <span data-ttu-id="e825c-289">Una volta installato PowerToys, è possibile ricevere notifiche di Windows e/o scaricare e \*\*\*\* installare gli aggiornamenti più recenti configurando le impostazioni di PowerToys Per scaricare automaticamente gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="e825c-289">Once PowerToys is installed, you can receive Windows notifications and/or download and install the latest updates by configuring the PowerToys settings **Download updates automatically** to on.</span></span>
- <span data-ttu-id="e825c-290">Per accedere alle impostazioni di PowerToys, \*\*\*\* seleziona le app in esecuzione nella barra delle applicazioni e quindi fai clic con il pulsante destro del mouse o tieni premuta l'icona PowerToys fino a quando non viene visualizzato il menu.</span><span class="sxs-lookup"><span data-stu-id="e825c-290">To get to the PowerToys settings, select the up carat **Running apps** on the taskbar, and then right click or press and hold the PowerToys icon until the menu appears.</span></span> <span data-ttu-id="e825c-291">Seleziona "Impostazioni".</span><span class="sxs-lookup"><span data-stu-id="e825c-291">Select “Settings”.</span></span>
- <span data-ttu-id="e825c-292">Nella parte inferiore della pagina delle impostazioni di PowerToys attiva **il download automatico** degli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="e825c-292">At the bottom of the PowerToys settings page, turn **Download updates automatically** to on.</span></span>
- <span data-ttu-id="e825c-293">Quando viene rilasciato un aggiornamento, viene visualizzata una notifica di Windows che consente di scegliere quando installare l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e825c-293">When an update has been released, a Windows notification will appear giving you the option of when to install the update.</span></span>


### <a name="edge-chromium-browser"></a><span data-ttu-id="e825c-294">Browser Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="e825c-294">Edge Chromium browser</span></span>

<span data-ttu-id="e825c-295">Scaricare e installare il nuovo <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> browser Edge Chromium. </a></span><span class="sxs-lookup"><span data-stu-id="e825c-295">Download and install the new <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank">Edge Chromium browser</a>.</span></span>


### <a name="surface-hub-hardware-diagnostic-tool"></a><span data-ttu-id="e825c-296">Strumento di diagnostica hardware di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="e825c-296">Surface Hub Hardware Diagnostic tool</span></span>

<span data-ttu-id="e825c-297">Strumento <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> di diagnostica hardware di Surface Hub disponibile gratuitamente da Microsoft </a> Store.</span><span class="sxs-lookup"><span data-stu-id="e825c-297">The <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> Surface Hub Hardware Diagnostic tool</a> available for free from the Microsoft Store.</span></span> <span data-ttu-id="e825c-298">Lo strumento è progettato per assicurarti che il dispositivo Surface Hub funzioni al meglio.</span><span class="sxs-lookup"><span data-stu-id="e825c-298">The tool is designed to help you make sure your Surface Hub is performing at its best.</span></span> <span data-ttu-id="e825c-299">Contiene test per determinare se il firmware è aggiornato e configurato correttamente.</span><span class="sxs-lookup"><span data-stu-id="e825c-299">It contains tests to determine if your firmware is up to date and configured correctly.</span></span> <span data-ttu-id="e825c-300">I test interattivi consentono di verificare che le funzionalità essenziali funzionino come previsto.</span><span class="sxs-lookup"><span data-stu-id="e825c-300">Interactive tests allow you to confirm essential functionality is working as expected.</span></span> <span data-ttu-id="e825c-301">Se si verificano problemi, i risultati possono essere salvati e condivisi con il team di supporto di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="e825c-301">If problems are encountered, results can be saved and shared with the Surface Hub Support Team.</span></span> <span data-ttu-id="e825c-302">Fai clic sul link per installarlo da Microsoft Store e quindi aggiungi l'applicazione alla barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-302">Click on the link to install it from the Microsoft Store, and then pin the application to your taskbar.</span></span>

## <a name="additional-settings"></a><span data-ttu-id="e825c-303">Impostazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="e825c-303">Additional settings</span></span>

### <a name="pen-tail-select-to-launch-whiteboard"></a><span data-ttu-id="e825c-304">Selezione della coda della penna per avviare Whiteboard</span><span class="sxs-lookup"><span data-stu-id="e825c-304">Pen tail select to launch Whiteboard</span></span>

1. <span data-ttu-id="e825c-305">Cerca Penna **e** seleziona Le impostazioni della penna **& di Windows Ink.**</span><span class="sxs-lookup"><span data-stu-id="e825c-305">Search for **Pen** and select **Pen & Windows Ink settings**.</span></span>

2. <span data-ttu-id="e825c-306">Nella parte inferiore della pagina, in Scelte rapide **da** penna impostare **Seleziona una sola volta** su Microsoft **Whiteboard.**</span><span class="sxs-lookup"><span data-stu-id="e825c-306">Near the bottom of the page, under **Pen shortcuts** set **Select once** to **Microsoft Whiteboard**.</span></span> 

### <a name="power-management"></a><span data-ttu-id="e825c-307">Risparmio energia</span><span class="sxs-lookup"><span data-stu-id="e825c-307">Power management</span></span>

<span data-ttu-id="e825c-308">Sono disponibili diverse impostazioni di risparmio energia per ottenere la migliore esperienza con Windows 10 Pro o Enterprise in Surface Hub 2.</span><span class="sxs-lookup"><span data-stu-id="e825c-308">There are several power settings available to get the best experience using Windows 10 Pro or Enterprise on Surface Hub 2.</span></span> <span data-ttu-id="e825c-309">Sono inclusi i timeout di schermo e pc e il modo in cui interagiscono con il rilevamento della presenza umana predefinito (Doppler), lo screen saver e la password di protezione e quindi, se appropriato, come superare le impostazioni di risparmio energia dei Criteri di gruppo destinate agli utenti di laptop/desktop.</span><span class="sxs-lookup"><span data-stu-id="e825c-309">This includes screen and pc timeouts and how they interact with the built-in human presence detection (Doppler), the screen saver and password protection, and then if appropriate how to by-pass group policy power settings intended for laptop / desktop users.</span></span>

<span data-ttu-id="e825c-310">Windows 10 Pro o Enterprise in Surface Hub 2 impedisce la sospensione dello schermo tramite tocco, mouse e tastiera, oltre al rilevamento dell'occupazione umana (Doppler) integrato.</span><span class="sxs-lookup"><span data-stu-id="e825c-310">Windows 10 Pro or Enterprise on Surface Hub 2 keeps the screen from going to sleep by touch, mouse, and keyboard actions, as well as the built-in human occupancy detection (Doppler).</span></span> <span data-ttu-id="e825c-311">Il rilevamento dell'occupazione umana è abilitato per impostazione predefinita, ma, se lo si desidera, può essere disabilitato in UEFI attivando l'opzione del dispositivo nello strumento Configuratore UEFI di Surface come parte della migrazione iniziale oppure creando e applicando un pacchetto di configurazione UEFI successivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-311">Human occupancy detection is enabled by default, but if desired it can be disabled in UEFI by toggling the device option in the Surface UEFI Configurator tool either as part of the initial migration, or by building and applying a later UEFI configuration package.</span></span> 

**<span data-ttu-id="e825c-312">Risparmio energia: impostazioni di sospensione dello schermo e del PC</span><span class="sxs-lookup"><span data-stu-id="e825c-312">Power Management: Screen and PC sleep settings</span></span>**

1. <span data-ttu-id="e825c-313">Selezionare **Start**  >  **Settings**  >  **System**  >  **Power & sleep**.</span><span class="sxs-lookup"><span data-stu-id="e825c-313">Select **Start** > **Settings** > **System** > **Power & sleep**.</span></span>

2. <span data-ttu-id="e825c-314">Impostare il dispositivo di scorrimento della modalità risparmio energia **su Prestazioni ottimali.**</span><span class="sxs-lookup"><span data-stu-id="e825c-314">Set the power mode slider to **Best performance**.</span></span>

3. <span data-ttu-id="e825c-315">Configura i valori dello schermo e della sospensione in base alle tue preferenze, tenendo conto anche del rilevamento della presenza Doppler che riattiva il dispositivo quando viene rilevato movimento.</span><span class="sxs-lookup"><span data-stu-id="e825c-315">Configure screen and sleep values to your preference while also accounting for Doppler presence detection that wakes up the device when movement is detected.</span></span> <span data-ttu-id="e825c-316">Di conseguenza, come procedura consigliata, è consigliabile impostare Lo schermo su Disattiva dopo **2** ore e il PC su Spegnimento **dopo 4 ore.**</span><span class="sxs-lookup"><span data-stu-id="e825c-316">Accordingly, as a best practice, it's recommended to set Screen to **Turn off after 2 hours** and the PC to **Turn off after 4 hours.**</span></span>

**<span data-ttu-id="e825c-317">Risparmio energia: screen saver</span><span class="sxs-lookup"><span data-stu-id="e825c-317">Power Management: Screen saver</span></span>**

1. <span data-ttu-id="e825c-318">Cercare la **schermata di blocco e** aprire le impostazioni della schermata di **blocco.**</span><span class="sxs-lookup"><span data-stu-id="e825c-318">Search for **Lock Screen** and open **Lock screen settings**.</span></span>

2. <span data-ttu-id="e825c-319">Configurare **le impostazioni di timeout dello** schermo e le impostazioni dello screen **saver** in base alle proprie preferenze.</span><span class="sxs-lookup"><span data-stu-id="e825c-319">Configure **Screen timeout settings** and **Screen saver settings** to your preference.</span></span> <span data-ttu-id="e825c-320">I valori predefiniti consigliati sono:</span><span class="sxs-lookup"><span data-stu-id="e825c-320">Recommended default values are:</span></span>

   - <span data-ttu-id="e825c-321">Screen saver to (None) or a screen saver of your choice.</span><span class="sxs-lookup"><span data-stu-id="e825c-321">Screen saver to (None) or a screen saver of your choice.</span></span>
   - <span data-ttu-id="e825c-322">Attendere fino a 15 minuti.</span><span class="sxs-lookup"><span data-stu-id="e825c-322">Wait time to 15 minutes.</span></span>
   - <span data-ttu-id="e825c-323">Al ripristino, visualizzare la schermata di accesso.</span><span class="sxs-lookup"><span data-stu-id="e825c-323">On resume, display logon screen.</span></span>


**<span data-ttu-id="e825c-324">Risparmio energia: Criteri di gruppo</span><span class="sxs-lookup"><span data-stu-id="e825c-324">Power Management: Group Policy</span></span>**

<span data-ttu-id="e825c-325">Prima di eseguire la procedura seguente, rivolgersi al reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S dai criteri globali di risparmio energia.</span><span class="sxs-lookup"><span data-stu-id="e825c-325">Before performing the following procedure, check with your IT department for approval to exclude a Surface Hub 2S device from global power management policy.</span></span> <span data-ttu-id="e825c-326">Alcune impostazioni di risparmio energia possono disabilitare la funzione di rilevamento della presenza.</span><span class="sxs-lookup"><span data-stu-id="e825c-326">Some power management settings can disable the presence detection function.</span></span>

1. <span data-ttu-id="e825c-327">Cercare **Software Center e** aprirlo.</span><span class="sxs-lookup"><span data-stu-id="e825c-327">Search for **Software Center** and open it.</span></span>

2. <span data-ttu-id="e825c-328">Selezionare **Opzioni.**</span><span class="sxs-lookup"><span data-stu-id="e825c-328">Select **Options**.</span></span>

3. <span data-ttu-id="e825c-329">Espandere Gestione **risparmio energia** e selezionare Non applicare le impostazioni di risparmio energia del reparto IT **al computer.**</span><span class="sxs-lookup"><span data-stu-id="e825c-329">Expand the **Power management**  and select **Do not apply power settings from my IT department to this computer**.</span></span>

   ![Impostazioni software](images/soft-cntr.png)

### <a name="storage-sense"></a><span data-ttu-id="e825c-331">Sensore memoria</span><span class="sxs-lookup"><span data-stu-id="e825c-331">Storage Sense</span></span>

<span data-ttu-id="e825c-332">Surface Hub 2 dispone di un SSD da 128 GB per l'archiviazione locale, quindi è necessario considerare l'uso di misure di salvataggio dello spazio di archiviazione durante il normale utilizzo.</span><span class="sxs-lookup"><span data-stu-id="e825c-332">The Surface Hub 2 has a 128GB SSD for local storage, so it is necessary to consider the use of storage saving measures during normal usage.</span></span>  <span data-ttu-id="e825c-333">Per configurare Il senso di archiviazione:</span><span class="sxs-lookup"><span data-stu-id="e825c-333">To configure Storage Sense:</span></span>

1.  <span data-ttu-id="e825c-334">Cercare le **impostazioni di archiviazione,** disponibili in **Impostazioni di sistema.**</span><span class="sxs-lookup"><span data-stu-id="e825c-334">Search for **storage settings**, which is found under **System settings**.</span></span>

2.  <span data-ttu-id="e825c-335">In **Impostazioni**selezionare **Attiva senso di archiviazione per** aprire la pagina **Impostazioni** di archiviazione.</span><span class="sxs-lookup"><span data-stu-id="e825c-335">Under **Settings**, select **Turn on storage sense** to open the **Storage** settings page.</span></span>

3.  <span data-ttu-id="e825c-336">Attivare Il senso di **archiviazione.**</span><span class="sxs-lookup"><span data-stu-id="e825c-336">Turn Storage Sense to **On**.</span></span>

4.  <span data-ttu-id="e825c-337">Selezionare **Configura Senso di archiviazione o eseguirlo ora** e configurare le impostazioni per mantenere i file online il più possibile (a causa di spazio su disco limitato).</span><span class="sxs-lookup"><span data-stu-id="e825c-337">Select **Configure Storage Sense or run it now** and configure settings to keep files online as much as possible (due to limited drive space).</span></span>

<span data-ttu-id="e825c-338">Impostazioni consigliate:</span><span class="sxs-lookup"><span data-stu-id="e825c-338">Recommended settings:</span></span>

- <span data-ttu-id="e825c-339">Eseguire Senso di archiviazione = Ogni giorno.</span><span class="sxs-lookup"><span data-stu-id="e825c-339">Run Storage Sense = Every Day.</span></span>
- <span data-ttu-id="e825c-340">Elimina i file temporanei che le mie app non usano = Ogni 14 giorni (almeno).</span><span class="sxs-lookup"><span data-stu-id="e825c-340">Delete temporary files that my apps aren't using = Every 14 days (at least).</span></span>
- <span data-ttu-id="e825c-341">Elimina i file nella cartella Download se sono presenti da più di 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="e825c-341">Delete files in my Downloads folder if they have been there for over = 30 days.</span></span>
- <span data-ttu-id="e825c-342">OneDrive: il contenuto diventerà online solo se non aperto per più di = 30 giorni.</span><span class="sxs-lookup"><span data-stu-id="e825c-342">OneDrive: Content will become online-only if not opened for more than = 30 days.</span></span>

### <a name="tablet-mode"></a><span data-ttu-id="e825c-343">Modalità tablet</span><span class="sxs-lookup"><span data-stu-id="e825c-343">Tablet mode</span></span>

<span data-ttu-id="e825c-344">Attivare la modalità tablet se lo si desidera per esigenze di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="e825c-344">Turn on Tablet mode if desired for accessibility needs.</span></span>


### <a name="sound-settings"></a><span data-ttu-id="e825c-345">Impostazioni audio</span><span class="sxs-lookup"><span data-stu-id="e825c-345">Sound settings</span></span>

1. <span data-ttu-id="e825c-346">Cerca le **impostazioni dei suoni** e apri questa pagina.</span><span class="sxs-lookup"><span data-stu-id="e825c-346">Search for **Sounds settings** and open this page.</span></span>

2. <span data-ttu-id="e825c-347">Seleziona **Pannello di controllo audio** a destra e seleziona la **scheda** Suoni.</span><span class="sxs-lookup"><span data-stu-id="e825c-347">Select **Sound Control Panel** on the right and select the **Sounds** tab.</span></span>

3. <span data-ttu-id="e825c-348">In **Eventi programma** imposta Device **Connect** e Device **Disconnect** su **None.**</span><span class="sxs-lookup"><span data-stu-id="e825c-348">Under **Program Events** set **Device Connect** and **Device Disconnect** to **None**.</span></span>

### <a name="silence-notifications"></a><span data-ttu-id="e825c-349">Notifiche di silenzio</span><span class="sxs-lookup"><span data-stu-id="e825c-349">Silence notifications</span></span>

1. <span data-ttu-id="e825c-350">Cerca **l'assistenza per lo stato** attivo e apri questa pagina.</span><span class="sxs-lookup"><span data-stu-id="e825c-350">Search for **Focus assist** and open this page.</span></span>

2. <span data-ttu-id="e825c-351">Selezionare **Solo sveglie.**</span><span class="sxs-lookup"><span data-stu-id="e825c-351">Select **Alarms Only**.</span></span> <span data-ttu-id="e825c-352">In questo modo si evitano riquadri a comparsa di notifica costanti.</span><span class="sxs-lookup"><span data-stu-id="e825c-352">This will avoid constant notification flyouts.</span></span>

### <a name="disk-cleanup"></a><span data-ttu-id="e825c-353">Pulizia disco</span><span class="sxs-lookup"><span data-stu-id="e825c-353">Disk Cleanup</span></span>

1. <span data-ttu-id="e825c-354">Cerca Pulizia **disco e** apri questa app.</span><span class="sxs-lookup"><span data-stu-id="e825c-354">Search for **Disk Cleanup** and open this app.</span></span>

2. <span data-ttu-id="e825c-355">In **File da eliminare**selezionare i file che si desidera eliminare.</span><span class="sxs-lookup"><span data-stu-id="e825c-355">Under **Files to delete**, select the files you wish to delete.</span></span> 

3. <span data-ttu-id="e825c-356">Selezionare anche **Pulire i file di sistema.**</span><span class="sxs-lookup"><span data-stu-id="e825c-356">Also select **Clean up system files**.</span></span>

## <a name="complete-and-verify"></a><span data-ttu-id="e825c-357">Completare e verificare</span><span class="sxs-lookup"><span data-stu-id="e825c-357">Complete and verify</span></span>

1. <span data-ttu-id="e825c-358">Cercare e installare tutti gli aggiornamenti di Windows.</span><span class="sxs-lookup"><span data-stu-id="e825c-358">Scan for and install all Windows Updates.</span></span>

2. <span data-ttu-id="e825c-359">Aggiornare Criteri di gruppo.</span><span class="sxs-lookup"><span data-stu-id="e825c-359">Update Group Policy.</span></span>

   1. <span data-ttu-id="e825c-360">In un prompt dei comandi con privilegi elevati, immettere **gpupdate /force /boot /wait:0**.</span><span class="sxs-lookup"><span data-stu-id="e825c-360">At an elevated command prompt, enter **gpupdate /force /boot /wait:0**.</span></span>
   
3. <span data-ttu-id="e825c-361">Riavvia il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e825c-361">Restart the device.</span></span>

4. <span data-ttu-id="e825c-362">Verificare le app della barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-362">Verify taskbar apps.</span></span>

   - <span data-ttu-id="e825c-363">Connect App</span><span class="sxs-lookup"><span data-stu-id="e825c-363">Connect App</span></span>
   - <span data-ttu-id="e825c-364">Icona Blocca</span><span class="sxs-lookup"><span data-stu-id="e825c-364">Lock Icon</span></span>
   - <span data-ttu-id="e825c-365">Cattura e annota</span><span class="sxs-lookup"><span data-stu-id="e825c-365">Snip & Sketch</span></span>
   - <span data-ttu-id="e825c-366">Teams (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="e825c-366">Teams (if applicable)</span></span>
   - <span data-ttu-id="e825c-367">App di Office (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="e825c-367">Office Apps (if applicable)</span></span>
   - <span data-ttu-id="e825c-368">Surface App</span><span class="sxs-lookup"><span data-stu-id="e825c-368">Surface App</span></span>
   - <span data-ttu-id="e825c-369">Lavagna</span><span class="sxs-lookup"><span data-stu-id="e825c-369">Whiteboard</span></span>
    
5. <span data-ttu-id="e825c-370">Verificare il rilevamento della presenza.</span><span class="sxs-lookup"><span data-stu-id="e825c-370">Verify presence detection.</span></span>

   - <span data-ttu-id="e825c-371">Il rilevamento della presenza sarà un'icona verde nella barra delle applicazioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-371">Presence detection will be a green icon in the system tray.</span></span>
    
6. <span data-ttu-id="e825c-372">Verifica che la proiettatura in questo PC sia abilitata con l'app Connetti.</span><span class="sxs-lookup"><span data-stu-id="e825c-372">Verify projecting to this PC is enabled with the Connect App.</span></span> <span data-ttu-id="e825c-373">Dopo aver configurato  **Project in questo PC,** esegui l'app Connetti almeno una volta.</span><span class="sxs-lookup"><span data-stu-id="e825c-373">After configuring  **Project to this PC** settings, run the Connect App at least once.</span></span> <span data-ttu-id="e825c-374">Successivamente, non è necessario che l'app Connect sia in esecuzione per proiettare in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="e825c-374">(Subsequently, the Connect App does not need to be running in order to project to Surface Hub.)</span></span>

7. <span data-ttu-id="e825c-375">Verificare le impostazioni di accensione e sospensione.</span><span class="sxs-lookup"><span data-stu-id="e825c-375">Verify power and sleep settings.</span></span>

    - <span data-ttu-id="e825c-376">Screen saver: 15 minuti, impostato su (nessuno), Mystify o Blank; Verificare che la casella di controllo per richiedere la password sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="e825c-376">Screen Saver: 15 minutes, set to (none), Mystify or Blank; ensure the check box for requiring password is selected.</span></span>
    - <span data-ttu-id="e825c-377">Schermata: **disattivare dopo 2 ore.**</span><span class="sxs-lookup"><span data-stu-id="e825c-377">Screen: **Turn off after 2 hours**.</span></span>
    - <span data-ttu-id="e825c-378">PC: **spegnimento dopo 4 ore.**</span><span class="sxs-lookup"><span data-stu-id="e825c-378">PC:  **Turn off after 4 hours**.</span></span>
    
8. <span data-ttu-id="e825c-379">Verificare che Windows Hello funzioni.</span><span class="sxs-lookup"><span data-stu-id="e825c-379">Verify Windows Hello is working.</span></span>

9. <span data-ttu-id="e825c-380">Verificare che la sincronizzazione delle impostazioni sia disabilitata.</span><span class="sxs-lookup"><span data-stu-id="e825c-380">Verify sync your settings is disabled.</span></span>

10. <span data-ttu-id="e825c-381">Verificare le app di avvio.</span><span class="sxs-lookup"><span data-stu-id="e825c-381">Verify startup apps.</span></span>

> [!TIP]
> <span data-ttu-id="e825c-382">Dopo l'installazione e la configurazione di Windows 10, Surface Hub 2S può essere gestito come qualsiasi altro dispositivo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e825c-382">After installing and configuring Windows 10, the Surface Hub 2S can be managed just like any other Windows 10 device.</span></span>

## <a name="related-topics"></a><span data-ttu-id="e825c-383">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="e825c-383">Related topics</span></span>

<a href="surface-hub-2s-migrate-os.md" target="_blank"> <span data-ttu-id="e825c-384">Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e825c-384">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span></a>

---
title: Aggiornamento del firmware Microsoft Surface Dock-informazioni tecniche per gli amministratori IT
description: Questo articolo spiega come usare Microsoft Surface Dock Update firmware per aggiornare il firmware di Surface Dock. Una volta installato nel dispositivo Surface, aggiornerà qualsiasi Dock di superficie collegato al dispositivo Surface.
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: aab4c67a6a262b11cd5982ebe145afbddfeaa1c9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832492"
---
# <span data-ttu-id="c92ed-104">Aggiornamento del firmware Microsoft Surface Dock: informazioni tecniche per gli amministratori IT</span><span class="sxs-lookup"><span data-stu-id="c92ed-104">Microsoft Surface Dock Firmware Update: Technical information for IT administrators</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c92ed-105">Questo articolo contiene le istruzioni tecniche per gli amministratori IT.</span><span class="sxs-lookup"><span data-stu-id="c92ed-105">This article contains technical instructions for IT administrators.</span></span> <span data-ttu-id="c92ed-106">Per gli utenti privati, vedere [come aggiornare il firmware di Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)   nel sito del supporto tecnico Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c92ed-106">If you are a home user, please see [How to update your Surface Dock Firmware](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) on the Microsoft Support site.</span></span> <span data-ttu-id="c92ed-107">Le istruzioni del sito di supporto sono le stesse della procedura di installazione generale di seguito, ma in questo articolo sono disponibili altre informazioni per il monitoraggio, la verifica e la distribuzione dell'aggiornamento in più dispositivi in rete.</span><span class="sxs-lookup"><span data-stu-id="c92ed-107">The instructions at the support site are the same as the general installation steps below, but this article has additional information for monitoring, verifying, and deploying the update to multiple devices on a network.</span></span>

<span data-ttu-id="c92ed-108">Questo articolo spiega come usare Microsoft Surface Dock Update firmware per aggiornare il firmware di Surface Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-108">This article explains how to use Microsoft Surface Dock Firmware Update to update Surface Dock firmware.</span></span> <span data-ttu-id="c92ed-109">Una volta installato nel dispositivo Surface, aggiornerà qualsiasi Dock di superficie collegato al dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="c92ed-109">When installed on your Surface device, it will update any Surface Dock attached to your Surface device.</span></span> 

<span data-ttu-id="c92ed-110">Questo strumento sostituisce lo strumento Microsoft Surface Dock Updater precedente, precedentemente disponibile per il download come parte di strumenti di Surface.</span><span class="sxs-lookup"><span data-stu-id="c92ed-110">This tool supersedes the earlier Microsoft Surface Dock Updater tool, previously available for download as part of Surface Tools for IT.</span></span> <span data-ttu-id="c92ed-111">Lo strumento precedente è stato denominato Surface_Dock_Updater_vx.xx.xxx.x.msi (dove x indica il numero di versione) e non è più disponibile per il download e non deve essere usato.</span><span class="sxs-lookup"><span data-stu-id="c92ed-111">The earlier tool was named Surface_Dock_Updater_vx.xx.xxx.x.msi (where x indicates the version number) and is no longer available for download and should not be used.</span></span>

## <span data-ttu-id="c92ed-112">Installare l'aggiornamento del firmware di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-112">Install the Surface Dock Firmware Update</span></span>

<span data-ttu-id="c92ed-113">Questa sezione descrive come installare manualmente l'aggiornamento del firmware.</span><span class="sxs-lookup"><span data-stu-id="c92ed-113">This section describes how to manually install the firmware update.</span></span>

> [!NOTE]
> <span data-ttu-id="c92ed-114">Microsoft rilascia periodicamente le nuove versioni dell'aggiornamento del firmware di Surface Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-114">Microsoft periodically releases new versions of Surface Dock Firmware Update.</span></span> <span data-ttu-id="c92ed-115">Il file MSI non viene aggiornato autonomamente.</span><span class="sxs-lookup"><span data-stu-id="c92ed-115">The MSI file is not self-updating.</span></span> <span data-ttu-id="c92ed-116">Se il file MSI è stato distribuito in dispositivi Surface e viene rilasciata una nuova versione del firmware, sarà necessario distribuire la nuova versione.</span><span class="sxs-lookup"><span data-stu-id="c92ed-116">If you have deployed the MSI to Surface devices and a new version of the firmware is released, you will need to deploy the new version.</span></span>

1. <span data-ttu-id="c92ed-117">Scaricare e installare l' [aggiornamento del firmware Microsoft Surface Dock](https://www.microsoft.com/download/details.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="c92ed-117">Download and install [Microsoft Surface Dock Firmware Update](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
    - <span data-ttu-id="c92ed-118">L'aggiornamento richiede un dispositivo Surface che esegua Windows 10, versione 1803 o successiva.</span><span class="sxs-lookup"><span data-stu-id="c92ed-118">The update requires a Surface device running Windows 10, version 1803 or later.</span></span>
    - <span data-ttu-id="c92ed-119">L'installazione del file MSI può richiedere di riavviare Surface.</span><span class="sxs-lookup"><span data-stu-id="c92ed-119">Installing the MSI file might prompt you to restart Surface.</span></span> <span data-ttu-id="c92ed-120">Tuttavia, non è necessario riavviare il computer per eseguire l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="c92ed-120">However, restarting is not required to perform the update.</span></span>

2. <span data-ttu-id="c92ed-121">Scollegare il dispositivo Surface dal Dock di Surface (usando l'adattatore di alimentazione), attendere ~ 5 secondi e quindi riconnettersi.</span><span class="sxs-lookup"><span data-stu-id="c92ed-121">Disconnect your Surface device from the Surface Dock (using the power adapter), wait ~5 seconds, and then reconnect.</span></span> <span data-ttu-id="c92ed-122">L'aggiornamento del firmware di Surface Dock aggiornerà il Dock in modo invisibile all'utente in background.</span><span class="sxs-lookup"><span data-stu-id="c92ed-122">The Surface Dock Firmware Update will update the dock silently in background.</span></span> <span data-ttu-id="c92ed-123">Il processo può richiedere alcuni minuti per il completamento e continuerà anche se interrotto.</span><span class="sxs-lookup"><span data-stu-id="c92ed-123">The process can take a few minutes to complete and will continue even if interrupted.</span></span> 

## <span data-ttu-id="c92ed-124">Monitorare l'aggiornamento del firmware di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-124">Monitor the Surface Dock Firmware Update</span></span>

<span data-ttu-id="c92ed-125">Questa sezione è facoltativa e offre una panoramica su come monitorare l'installazione dell'aggiornamento del firmware.</span><span class="sxs-lookup"><span data-stu-id="c92ed-125">This section is optional and provides an overview of how to monitor installation of the firmware update.</span></span> 

<span data-ttu-id="c92ed-126">Per monitorare l'aggiornamento:</span><span class="sxs-lookup"><span data-stu-id="c92ed-126">To monitor the update:</span></span>

1. <span data-ttu-id="c92ed-127">Aprire il Visualizzatore eventi, individuare i **registri di Windows > applicazione**e quindi in **azioni** nel riquadro destro fare clic su **filtro log corrente**, immettere **SurfaceDockFwUpdate** accanto a **origini eventi**e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="c92ed-127">Open Event Viewer, browse to **Windows Logs > Application**, and then under **Actions** in the right-hand pane click **Filter Current Log**, enter **SurfaceDockFwUpdate** next to **Event sources**, and then click **OK**.</span></span>

2. <span data-ttu-id="c92ed-128">Digitare il comando seguente a un prompt dei comandi con privilegi elevati:</span><span class="sxs-lookup"><span data-stu-id="c92ed-128">Type the following command at an elevated command prompt:</span></span>

    ```cmd
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. <span data-ttu-id="c92ed-129">Installare l'aggiornamento come descritto nella [sezione successiva](#install-the-surface-dock-firmware-update) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="c92ed-129">Install the update as described in the [next section](#install-the-surface-dock-firmware-update) of this article.</span></span>
4. <span data-ttu-id="c92ed-130">L'evento 2007 con il testo seguente indica un aggiornamento riuscito: **aggiornamento del firmware terminato. hr = 0 DriverTelementry eventCode = 2007**.</span><span class="sxs-lookup"><span data-stu-id="c92ed-130">Event 2007 with the following text indicates a successful update: **Firmware update finished. hr=0 DriverTelementry EventCode = 2007**.</span></span> 
    - <span data-ttu-id="c92ed-131">Se l'aggiornamento non riesce, l'ID evento 2007 verrà visualizzato come evento di **errore** anziché **informazioni**.</span><span class="sxs-lookup"><span data-stu-id="c92ed-131">If the update is not successful, then event ID 2007 will be displayed as an **Error** event rather than **Information**.</span></span> <span data-ttu-id="c92ed-132">Inoltre, la versione riportata nel registro di sistema di Windows non sarà aggiornata.</span><span class="sxs-lookup"><span data-stu-id="c92ed-132">Additionally, the version reported in the Windows Registry will not be current.</span></span>
5. <span data-ttu-id="c92ed-133">Al termine dell'aggiornamento, i valori DWORD aggiornati verranno visualizzati nel registro di sistema di Windows, in modo che corrispondano alla versione corrente dello strumento.</span><span class="sxs-lookup"><span data-stu-id="c92ed-133">When the update is complete, updated DWORD values will be displayed in the Windows Registry, corresponding to the current version of the tool.</span></span> <span data-ttu-id="c92ed-134">Per informazioni dettagliate, vedere la sezione [riferimenti alle versioni](#versions-reference) in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="c92ed-134">See the [Versions reference](#versions-reference) section in this article for details.</span></span> <span data-ttu-id="c92ed-135">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="c92ed-135">For example:</span></span>
    - <span data-ttu-id="c92ed-136">Component10CurrentFwVersion 0x04ac3970 (78395760)</span><span class="sxs-lookup"><span data-stu-id="c92ed-136">Component10CurrentFwVersion 0x04ac3970 (78395760)</span></span>
    - <span data-ttu-id="c92ed-137">Component20CurrentFwVersion 0x04915a70 (76634736)</span><span class="sxs-lookup"><span data-stu-id="c92ed-137">Component20CurrentFwVersion 0x04915a70 (76634736)</span></span>

>[!TIP]
><span data-ttu-id="c92ed-138">Se viene visualizzato "la descrizione per l'ID evento xxxx da SurfaceDockFwUpdate di origine non è possibile trovare" nel testo dell'evento, questa operazione è prevista e può essere ignorata.</span><span class="sxs-lookup"><span data-stu-id="c92ed-138">If you see "The description for Event ID xxxx from source SurfaceDockFwUpdate cannot be found" in event text, this is expected and can be ignored.</span></span>

<span data-ttu-id="c92ed-139">Vedere anche le sezioni seguenti in questo articolo:</span><span class="sxs-lookup"><span data-stu-id="c92ed-139">Also see the following sections in this article:</span></span> 
  - [<span data-ttu-id="c92ed-140">Come verificare il completamento dell'aggiornamento del firmware</span><span class="sxs-lookup"><span data-stu-id="c92ed-140">How to verify completion of firmware update</span></span>](#how-to-verify-completion-of-the-firmware-update)
  - [<span data-ttu-id="c92ed-141">Registrazione eventi</span><span class="sxs-lookup"><span data-stu-id="c92ed-141">Event logging</span></span>](#event-logging)
  - [<span data-ttu-id="c92ed-142">Suggerimenti per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="c92ed-142">Troubleshooting tips</span></span>](#troubleshooting-tips)
  - [<span data-ttu-id="c92ed-143">Riferimenti alle versioni</span><span class="sxs-lookup"><span data-stu-id="c92ed-143">Versions reference</span></span>](#versions-reference)

## <span data-ttu-id="c92ed-144">Distribuzione di rete</span><span class="sxs-lookup"><span data-stu-id="c92ed-144">Network deployment</span></span>

<span data-ttu-id="c92ed-145">Puoi usare i comandi di Windows Installer (Msiexec.exe) per distribuire l'aggiornamento del firmware di Surface dock a più dispositivi in tutta la rete.</span><span class="sxs-lookup"><span data-stu-id="c92ed-145">You can use Windows Installer commands (Msiexec.exe) to deploy Surface Dock Firmware Update to multiple devices across your network.</span></span> <span data-ttu-id="c92ed-146">Quando si usa Microsoft endpoint Configuration Manager o un altro strumento di distribuzione, immettere la sintassi seguente per verificare che l'installazione sia silenziosa:</span><span class="sxs-lookup"><span data-stu-id="c92ed-146">When using Microsoft Endpoint Configuration Manager or other deployment tool, enter the following syntax to ensure the installation is silent:</span></span>

- **<span data-ttu-id="c92ed-147">Msiexec.exe/i \<path to msi file\> /quiet/norestart</span><span class="sxs-lookup"><span data-stu-id="c92ed-147">Msiexec.exe /i \<path to msi file\> /quiet /norestart</span></span>** 

  <span data-ttu-id="c92ed-148">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="c92ed-148">For example:</span></span>
  ```
  msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
  ```

  > [!NOTE]
  > <span data-ttu-id="c92ed-149">Per impostazione predefinita, un file di log non viene creato.</span><span class="sxs-lookup"><span data-stu-id="c92ed-149">A log file is not created by default.</span></span> <span data-ttu-id="c92ed-150">Per creare un file di log, sarà necessario accodare "/l*v [path]". Ad esempio: Msiexec.exe/i \<path to msi file\> /l*v%windir%\logs\ SurfaceDockFWI. log "</span><span class="sxs-lookup"><span data-stu-id="c92ed-150">In order to create a log file, you will need to append "/l*v [path]". For example: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"</span></span>

  <span data-ttu-id="c92ed-151">Per altre informazioni, vedere la documentazione relativa alle [Opzioni della riga di comando](https://docs.microsoft.com/windows/win32/msi/command-line-options) .</span><span class="sxs-lookup"><span data-stu-id="c92ed-151">For more information, refer to [Command line options](https://docs.microsoft.com/windows/win32/msi/command-line-options) documentation.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c92ed-152">Se si vuole che il dock per Surface venga aggiornato usando qualsiasi altro metodo, vedere [aggiornare Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) per i dettagli.</span><span class="sxs-lookup"><span data-stu-id="c92ed-152">If you want to keep your Surface Dock updated using any other method, refer to [Update your Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) for details.</span></span>

## <span data-ttu-id="c92ed-153">Distribuzione di Intune</span><span class="sxs-lookup"><span data-stu-id="c92ed-153">Intune deployment</span></span>

<span data-ttu-id="c92ed-154">Puoi usare Intune per distribuire l'aggiornamento del firmware di Surface Dock ai tuoi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="c92ed-154">You can use Intune to distribute Surface Dock Firmware Update to your devices.</span></span> <span data-ttu-id="c92ed-155">Prima di tutto è necessario convertire il file MSI nel formato intunewin, come descritto nella documentazione seguente: [Intune standalone-gestione delle app Win32](https://docs.microsoft.com/intune/apps/apps-win32-app-management).</span><span class="sxs-lookup"><span data-stu-id="c92ed-155">First you will need to convert the MSI file to the .intunewin format, as described in the following documentation: [Intune Standalone - Win32 app management](https://docs.microsoft.com/intune/apps/apps-win32-app-management).</span></span>

<span data-ttu-id="c92ed-156">Usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="c92ed-156">Use the following command:</span></span>
  - **<span data-ttu-id="c92ed-157">msiexec/i \<path to msi file\> /quiet/q</span><span class="sxs-lookup"><span data-stu-id="c92ed-157">msiexec /i \<path to msi file\> /quiet /q</span></span>**

## <span data-ttu-id="c92ed-158">Come verificare il completamento dell'aggiornamento del firmware</span><span class="sxs-lookup"><span data-stu-id="c92ed-158">How to verify completion of the firmware update</span></span>

<span data-ttu-id="c92ed-159">Il firmware di Surface Dock è costituito da due componenti:</span><span class="sxs-lookup"><span data-stu-id="c92ed-159">Surface dock firmware consists of two components:</span></span>

- <span data-ttu-id="c92ed-160">**Component10:** Firmware dell'unità di controllo micro (MCU)</span><span class="sxs-lookup"><span data-stu-id="c92ed-160">**Component10:** Micro controller unit (MCU) firmware</span></span>
- <span data-ttu-id="c92ed-161">**Component20:** Visualizza il firmware della porta (DP).</span><span class="sxs-lookup"><span data-stu-id="c92ed-161">**Component20:** Display port (DP) firmware.</span></span>

<span data-ttu-id="c92ed-162">Il completamento dell'aggiornamento del firmware di Surface Dock restituisce i nuovi valori delle chiavi del registro di sistema per questi componenti del firmware.</span><span class="sxs-lookup"><span data-stu-id="c92ed-162">Successful completion of Surface Dock Firmware Update results in new registry key values for these firmware components.</span></span>

**<span data-ttu-id="c92ed-163">Per verificare gli aggiornamenti:</span><span class="sxs-lookup"><span data-stu-id="c92ed-163">To verify updates:</span></span>**

1. <span data-ttu-id="c92ed-164">Aprire regedit e passare al percorso del registro di sistema seguente:</span><span class="sxs-lookup"><span data-stu-id="c92ed-164">Open Regedit and navigate to the following registry path:</span></span>

    - **<span data-ttu-id="c92ed-165">HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span><span class="sxs-lookup"><span data-stu-id="c92ed-165">HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters</span></span>**

2. <span data-ttu-id="c92ed-166">Cercare le chiavi del registro di sistema: **Component10CurrentFwVersion e Component20CurrentFwVersion**, che fanno riferimento al firmware attualmente presente nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c92ed-166">Look for the registry keys: **Component10CurrentFwVersion and Component20CurrentFwVersion**, which refer to the firmware that is currently on the device.</span></span>

   ![Processo di installazione dell'aggiornamento del firmware Surface Dock](images/regeditDock.png)

3. <span data-ttu-id="c92ed-168">Verificare che i nuovi valori della chiave del registro di sistema corrispondano ai valori della chiave del registro di sistema aggiornati elencati nel riferimento alle versioni alla fine del documento.</span><span class="sxs-lookup"><span data-stu-id="c92ed-168">Verify the new registry key values match the updated registry key values listed in the Versions reference at the end of this document.</span></span> <span data-ttu-id="c92ed-169">Se i valori corrispondono, il firmware è stato aggiornato correttamente.</span><span class="sxs-lookup"><span data-stu-id="c92ed-169">If the values match, the firmware was updated successfully.</span></span>

4. <span data-ttu-id="c92ed-170">Se non è possibile verificare, esaminare la registrazione degli eventi e i suggerimenti per la risoluzione dei problemi nella sezione successiva.</span><span class="sxs-lookup"><span data-stu-id="c92ed-170">If unable to verify, review Event logging and Troubleshooting tips in the next section.</span></span>

## <span data-ttu-id="c92ed-171">Registrazione eventi</span><span class="sxs-lookup"><span data-stu-id="c92ed-171">Event logging</span></span>

**<span data-ttu-id="c92ed-172">Tabella 1.</span><span class="sxs-lookup"><span data-stu-id="c92ed-172">Table 1.</span></span> <span data-ttu-id="c92ed-173">File di log per l'aggiornamento del firmware di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-173">Log files for Surface Dock Firmware Update</span></span>**

| <span data-ttu-id="c92ed-174">Log</span><span class="sxs-lookup"><span data-stu-id="c92ed-174">Log</span></span>                              | <span data-ttu-id="c92ed-175">Posizione</span><span class="sxs-lookup"><span data-stu-id="c92ed-175">Location</span></span>                               | <span data-ttu-id="c92ed-176">Note</span><span class="sxs-lookup"><span data-stu-id="c92ed-176">Notes</span></span>                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="c92ed-177">Log degli aggiornamenti del firmware di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-177">Surface Dock Firmware Update log</span></span> | <span data-ttu-id="c92ed-178">Il percorso deve essere specificato (Vedi nota)</span><span class="sxs-lookup"><span data-stu-id="c92ed-178">Path needs to be specified (see note)</span></span> | <span data-ttu-id="c92ed-179">Le versioni precedenti di questo strumento hanno scritto eventi per le applicazioni e i servizi Logs\Microsoft Surface Dock Updater.</span><span class="sxs-lookup"><span data-stu-id="c92ed-179">Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>                                                                                                  |
| <span data-ttu-id="c92ed-180">Log di installazione di dispositivi Windows</span><span class="sxs-lookup"><span data-stu-id="c92ed-180">Windows Device Install log</span></span>       | <span data-ttu-id="c92ed-181">%windir%\inf\setupapi.dev.log</span><span class="sxs-lookup"><span data-stu-id="c92ed-181">%windir%\inf\setupapi.dev.log</span></span>           | <span data-ttu-id="c92ed-182">Per altre informazioni sull'uso del log di installazione del dispositivo, vedere la documentazione relativa alla [registrazione di Setupapi](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) .</span><span class="sxs-lookup"><span data-stu-id="c92ed-182">For more information about using Device Install Log, refer to [SetupAPI Logging](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) documentation.</span></span> |


**<span data-ttu-id="c92ed-183">Tabella 2.</span><span class="sxs-lookup"><span data-stu-id="c92ed-183">Table 2.</span></span> <span data-ttu-id="c92ed-184">ID log eventi per l'aggiornamento del firmware di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-184">Event log IDs for Surface Dock Firmware Update</span></span>**<br>
<span data-ttu-id="c92ed-185">Gli eventi vengono registrati nel log eventi applicazione.</span><span class="sxs-lookup"><span data-stu-id="c92ed-185">Events are logged in the Application Event Log.</span></span>  <span data-ttu-id="c92ed-186">Nota: le versioni precedenti di questo strumento hanno scritto eventi per le applicazioni e i servizi Logs\Microsoft Surface Dock Updater.</span><span class="sxs-lookup"><span data-stu-id="c92ed-186">Note:  Earlier versions of this tool wrote events to Applications and Services Logs\Microsoft Surface Dock Updater.</span></span>

| <span data-ttu-id="c92ed-187">ID evento</span><span class="sxs-lookup"><span data-stu-id="c92ed-187">Event ID</span></span> | <span data-ttu-id="c92ed-188">Tipo evento</span><span class="sxs-lookup"><span data-stu-id="c92ed-188">Event type</span></span>                                                           |
| -------- | -------------------------------------------------------------------- |
| <span data-ttu-id="c92ed-189">2001</span><span class="sxs-lookup"><span data-stu-id="c92ed-189">2001</span></span>     | <span data-ttu-id="c92ed-190">È stato avviato l'aggiornamento del firmware Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-190">Dock firmware update has started.</span></span>                                    |
| <span data-ttu-id="c92ed-191">2002</span><span class="sxs-lookup"><span data-stu-id="c92ed-191">2002</span></span>     | <span data-ttu-id="c92ed-192">Aggiornamento del firmware di ancoraggio ignorato perché il Dock è noto per essere aggiornato.</span><span class="sxs-lookup"><span data-stu-id="c92ed-192">Dock firmware update skipped because dock is known to be up to date.</span></span> |
| <span data-ttu-id="c92ed-193">2003</span><span class="sxs-lookup"><span data-stu-id="c92ed-193">2003</span></span>     | <span data-ttu-id="c92ed-194">L'aggiornamento del firmware Dock non è riuscito a ottenere la versione del firmware.</span><span class="sxs-lookup"><span data-stu-id="c92ed-194">Dock firmware update failed to get firmware version.</span></span>                 |
| <span data-ttu-id="c92ed-195">2004</span><span class="sxs-lookup"><span data-stu-id="c92ed-195">2004</span></span>     | <span data-ttu-id="c92ed-196">Query sulla versione del firmware.</span><span class="sxs-lookup"><span data-stu-id="c92ed-196">Querying the firmware version.</span></span>                                       |
| <span data-ttu-id="c92ed-197">2005</span><span class="sxs-lookup"><span data-stu-id="c92ed-197">2005</span></span>     | <span data-ttu-id="c92ed-198">Non è stato possibile avviare l'aggiornamento del firmware Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-198">Dock firmware failed to start update.</span></span>                                |
| <span data-ttu-id="c92ed-199">2006</span><span class="sxs-lookup"><span data-stu-id="c92ed-199">2006</span></span>     | <span data-ttu-id="c92ed-200">Impossibile inviare coppie di offerte/payload.</span><span class="sxs-lookup"><span data-stu-id="c92ed-200">Failed to send offer/payload pairs.</span></span>                                  |
| <span data-ttu-id="c92ed-201">2007</span><span class="sxs-lookup"><span data-stu-id="c92ed-201">2007</span></span>     | <span data-ttu-id="c92ed-202">Aggiornamento del firmware terminato.</span><span class="sxs-lookup"><span data-stu-id="c92ed-202">Firmware update finished.</span></span>                                            |
| <span data-ttu-id="c92ed-203">2008</span><span class="sxs-lookup"><span data-stu-id="c92ed-203">2008</span></span>     | <span data-ttu-id="c92ed-204">INIZIARE a collegare la telemetria.</span><span class="sxs-lookup"><span data-stu-id="c92ed-204">BEGIN dock telemetry.</span></span>                                                |
| <span data-ttu-id="c92ed-205">2011</span><span class="sxs-lookup"><span data-stu-id="c92ed-205">2011</span></span>     | <span data-ttu-id="c92ed-206">FINE della telemetria del Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-206">END dock telemetry.</span></span>                                                  |

## <span data-ttu-id="c92ed-207">Suggerimenti per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="c92ed-207">Troubleshooting tips</span></span>

- <span data-ttu-id="c92ed-208">Scollegare completamente l'alimentazione per Surface dock dall'alimentazione CA per reimpostare Surface Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-208">Completely disconnect power for Surface dock from the AC power to reset the Surface Dock.</span></span>
- <span data-ttu-id="c92ed-209">Scollegare tutte le periferiche eccetto il dock di superficie.</span><span class="sxs-lookup"><span data-stu-id="c92ed-209">Disconnect all peripherals except for the Surface Dock.</span></span>
- <span data-ttu-id="c92ed-210">Disinstallare qualsiasi aggiornamento del firmware di Surface dock corrente e quindi installare la versione più recente.</span><span class="sxs-lookup"><span data-stu-id="c92ed-210">Uninstall any current Surface Dock Firmware Update and then install the latest version.</span></span>
- <span data-ttu-id="c92ed-211">Assicurarsi che Surface dock sia disconnesso e quindi consentire un tempo sufficiente per completare l'aggiornamento come monitorato tramite un LED nella porta Ethernet del Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-211">Ensure that the Surface Dock is disconnected, and then allow enough time for the update to complete as monitored via an LED in the Ethernet port of the dock.</span></span> <span data-ttu-id="c92ed-212">Attendere che il LED smetta di lampeggiare prima di scollegare Surface dock dall'alimentazione.</span><span class="sxs-lookup"><span data-stu-id="c92ed-212">Wait until the LED stops blinking before you unplug Surface Dock from power.</span></span>
- <span data-ttu-id="c92ed-213">Connettere Surface dock a un dispositivo diverso per verificare se è in grado di aggiornare il Dock.</span><span class="sxs-lookup"><span data-stu-id="c92ed-213">Connect the Surface Dock to a different device to see if it is able to update the dock.</span></span>

## <span data-ttu-id="c92ed-214">Riferimenti alle versioni</span><span class="sxs-lookup"><span data-stu-id="c92ed-214">Versions reference</span></span>

>[!NOTE]
><span data-ttu-id="c92ed-215">Il file di installazione viene rilasciato con il formato di denominazione seguente: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (es: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) e viene installato per impostazione predefinita in C:\Program Files\SurfaceUpdate.</span><span class="sxs-lookup"><span data-stu-id="c92ed-215">The installation file is released with the following naming format: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ex: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) and installs by default to C:\Program Files\SurfaceUpdate.</span></span>

### <span data-ttu-id="c92ed-216">Versione 1.42.139</span><span class="sxs-lookup"><span data-stu-id="c92ed-216">Version 1.42.139</span></span> 
*<span data-ttu-id="c92ed-217">Data di rilascio: 18 2019 settembre</span><span class="sxs-lookup"><span data-stu-id="c92ed-217">Release Date: September 18 2019</span></span>*

<span data-ttu-id="c92ed-218">Questa versione, contenuta in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, aggiorna il firmware in background.</span><span class="sxs-lookup"><span data-stu-id="c92ed-218">This version, contained in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, updates firmware in the background.</span></span> 
**<span data-ttu-id="c92ed-219">Valori della chiave del registro di sistema aggiornati:</span><span class="sxs-lookup"><span data-stu-id="c92ed-219">Updated registry key values:</span></span>**<br>

- <span data-ttu-id="c92ed-220">Component10CurrentFwVersion è stato aggiornato a **4ac3970**.</span><span class="sxs-lookup"><span data-stu-id="c92ed-220">Component10CurrentFwVersion updated to **4ac3970**.</span></span>
- <span data-ttu-id="c92ed-221">Component20CurrentFwVersion è stato aggiornato a **4a1d570**.</span><span class="sxs-lookup"><span data-stu-id="c92ed-221">Component20CurrentFwVersion updated to **4a1d570**.</span></span>

<span data-ttu-id="c92ed-222">Aggiunge il supporto per Surface Pro 7 e Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="c92ed-222">It adds support for Surface Pro 7 and Surface Laptop 3.</span></span>

## <span data-ttu-id="c92ed-223">Versioni legacy</span><span class="sxs-lookup"><span data-stu-id="c92ed-223">Legacy versions</span></span>

### <span data-ttu-id="c92ed-224">Versione 2.23.139.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-224">Version 2.23.139.0</span></span>
*<span data-ttu-id="c92ed-225">Data di rilascio: 10 ottobre 2018</span><span class="sxs-lookup"><span data-stu-id="c92ed-225">Release Date: 10 October 2018</span></span>*

<span data-ttu-id="c92ed-226">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-226">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="c92ed-227">Aggiungere il supporto per Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="c92ed-227">Add support for Surface Pro 6</span></span>
- <span data-ttu-id="c92ed-228">Aggiungere il supporto per Surface laptop 2</span><span class="sxs-lookup"><span data-stu-id="c92ed-228">Add support for Surface Laptop 2</span></span>


### <span data-ttu-id="c92ed-229">Versione 2.22.139.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-229">Version 2.22.139.0</span></span>
*<span data-ttu-id="c92ed-230">Data di rilascio: 26 luglio 2018</span><span class="sxs-lookup"><span data-stu-id="c92ed-230">Release Date: 26 July 2018</span></span>*

<span data-ttu-id="c92ed-231">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-231">This version of Surface Dock Updater adds support for the following:</span></span>

- <span data-ttu-id="c92ed-232">Aumentare l'affidabilità degli aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="c92ed-232">Increase update reliability</span></span>
- <span data-ttu-id="c92ed-233">Aggiungere il supporto per Surface go</span><span class="sxs-lookup"><span data-stu-id="c92ed-233">Add support for Surface Go</span></span>

### <span data-ttu-id="c92ed-234">Versione 2.12.136.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-234">Version 2.12.136.0</span></span>
*<span data-ttu-id="c92ed-235">Data di rilascio: 29 gennaio 2018</span><span class="sxs-lookup"><span data-stu-id="c92ed-235">Release Date: 29 January 2018</span></span>*

<span data-ttu-id="c92ed-236">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-236">This version of Surface Dock Updater adds support for the following:</span></span>
* <span data-ttu-id="c92ed-237">Aggiornamento del firmware del chipset principale di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-237">Update for Surface Dock Main Chipset Firmware</span></span>
* <span data-ttu-id="c92ed-238">Aggiornamento del firmware DisplayPort di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-238">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="c92ed-239">Stabilità di visualizzazione migliorata per gli schermi esterni se usato con Surface Book o Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="c92ed-239">Improved display stability for external displays when used with Surface Book or Surface Book 2</span></span>

<span data-ttu-id="c92ed-240">Inoltre, l'installazione di questa versione di Surface Dock Updater nei dispositivi Surface Book include:</span><span class="sxs-lookup"><span data-stu-id="c92ed-240">Additionally, installation of this version of Surface Dock Updater on Surface Book devices includes the following:</span></span>
* <span data-ttu-id="c92ed-241">Aggiornamento del firmware per la base di Surface Book</span><span class="sxs-lookup"><span data-stu-id="c92ed-241">Update for Surface Book Base Firmware</span></span>
* <span data-ttu-id="c92ed-242">Aggiunta del supporto per gli aggiornamenti del firmware di Surface Dock con miglioramenti per i dispositivi Surface Book</span><span class="sxs-lookup"><span data-stu-id="c92ed-242">Added support for Surface Dock firmware updates with improvements targeted to Surface Book devices</span></span>


### <span data-ttu-id="c92ed-243">Versione 2.9.136.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-243">Version 2.9.136.0</span></span>
*<span data-ttu-id="c92ed-244">Data di rilascio: 3 novembre 2017</span><span class="sxs-lookup"><span data-stu-id="c92ed-244">Release date: November 3, 2017</span></span>*

<span data-ttu-id="c92ed-245">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-245">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="c92ed-246">Aggiornamento del firmware DisplayPort di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-246">Update for Surface Dock DisplayPort Firmware</span></span>
* <span data-ttu-id="c92ed-247">Risolve un problema con l'audio tramite schede di porta video passive</span><span class="sxs-lookup"><span data-stu-id="c92ed-247">Resolves an issue with audio over passive display port adapters</span></span>

### <span data-ttu-id="c92ed-248">Versione 2.1.15.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-248">Version 2.1.15.0</span></span>
*<span data-ttu-id="c92ed-249">Data di rilascio: 19 giugno 2017</span><span class="sxs-lookup"><span data-stu-id="c92ed-249">Release date: June 19, 2017</span></span>*

<span data-ttu-id="c92ed-250">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-250">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="c92ed-251">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="c92ed-251">Surface Laptop</span></span>
* <span data-ttu-id="c92ed-252">Surface Pro</span><span class="sxs-lookup"><span data-stu-id="c92ed-252">Surface Pro</span></span>

### <span data-ttu-id="c92ed-253">Versione 2.1.6.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-253">Version 2.1.6.0</span></span>
*<span data-ttu-id="c92ed-254">Data di rilascio: 7 aprile 2017</span><span class="sxs-lookup"><span data-stu-id="c92ed-254">Release date: April 7, 2017</span></span>*

<span data-ttu-id="c92ed-255">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-255">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="c92ed-256">Aggiornamento del firmware DisplayPort di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-256">Update for Surface Dock DisplayPort firmware</span></span>
* <span data-ttu-id="c92ed-257">Richiede Windows 10</span><span class="sxs-lookup"><span data-stu-id="c92ed-257">Requires Windows 10</span></span>

### <span data-ttu-id="c92ed-258">Versione 2.0.22.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-258">Version 2.0.22.0</span></span>
*<span data-ttu-id="c92ed-259">Data di rilascio: 21 ottobre 2016</span><span class="sxs-lookup"><span data-stu-id="c92ed-259">Release date: October 21, 2016</span></span>*

<span data-ttu-id="c92ed-260">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-260">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="c92ed-261">Aggiornamento del firmware USB di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-261">Update for Surface Dock USB firmware</span></span>
* <span data-ttu-id="c92ed-262">Miglioramento dell'affidabilità di Ethernet, audio e porte USB</span><span class="sxs-lookup"><span data-stu-id="c92ed-262">Improved reliability of Ethernet, audio, and USB ports</span></span>

### <span data-ttu-id="c92ed-263">Versione 1.0.8.0</span><span class="sxs-lookup"><span data-stu-id="c92ed-263">Version 1.0.8.0</span></span>
*<span data-ttu-id="c92ed-264">Data di rilascio: 26 aprile 2016</span><span class="sxs-lookup"><span data-stu-id="c92ed-264">Release date: April 26, 2016</span></span>*

<span data-ttu-id="c92ed-265">Questa versione di Surface Dock Updater aggiunge il supporto per:</span><span class="sxs-lookup"><span data-stu-id="c92ed-265">This version of Surface Dock Updater adds support for the following:</span></span>

* <span data-ttu-id="c92ed-266">Aggiornamento del firmware del chipset principale di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-266">Update for Surface Dock Main Chipset firmware</span></span>
* <span data-ttu-id="c92ed-267">Aggiornamento del firmware DisplayPort di Surface Dock</span><span class="sxs-lookup"><span data-stu-id="c92ed-267">Update for Surface Dock DisplayPort firmware</span></span>


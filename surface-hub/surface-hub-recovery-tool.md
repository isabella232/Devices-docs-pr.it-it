---
title: Uso dello strumento di ripristino di Surface Hub
description: Come usare lo strumento di ripristino di Surface Hub per ri-creare un'immagine dell'unità SSD.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: gestire Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/11/2020
ms.localizationpriority: medium
ms.openlocfilehash: 34a05eeabd284e0ad43317577b8e7ff9348ffe21
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327340"
---
# <span data-ttu-id="52f89-104">Uso dello strumento di ripristino di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="52f89-104">Using the Surface Hub Recovery Tool</span></span>

<span data-ttu-id="52f89-105">Lo strumento di ripristino di [Microsoft Surface Hub](https://www.microsoft.com/download/details.aspx?id=52210) consente di ri-creare un'immagine dell'unità SSD (Solid State Drive) di Surface Hub con un dispositivo desktop Windows 10, senza chiamare il supporto o sostituire l'unità SSD.</span><span class="sxs-lookup"><span data-stu-id="52f89-105">The [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) helps you re-image your Surface Hub Solid State Drive (SSD) using a Windows 10 desktop device, without calling support or replacing the SSD.</span></span> <span data-ttu-id="52f89-106">Con questo strumento puoi ricreare l'immagine di un'unità SSD con una password amministratore sconosciuta, errori di avvio, non è stato possibile completare un ripristino cloud o per un dispositivo con una versione precedente del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="52f89-106">With this tool, you can reimage an SSD that has an unknown Administrator password, boot errors, was unable to complete a cloud recovery, or for a device that has an older version of the operating system.</span></span> <span data-ttu-id="52f89-107">Lo strumento non correggerà le unità SSD danneggiate fisicamente.</span><span class="sxs-lookup"><span data-stu-id="52f89-107">The tool will not fix physically damaged SSDs.</span></span>

<span data-ttu-id="52f89-108">Per ri-creare un'immagine dell'unità SSD di Surface Hub con lo strumento di ripristino, dovrai rimuovere l'unità SSD da Surface Hub, connettere l'unità al cavo DA USB a SATA e quindi collegare il cavo al PC desktop in cui è installato lo strumento di ripristino.</span><span class="sxs-lookup"><span data-stu-id="52f89-108">To re-image the Surface Hub SSD using the Recovery Tool, you'll need to remove the SSD from the Surface Hub, connect the drive to the USB-to-SATA cable, and then connect the cable to the desktop PC on which the Recovery Tool is installed.</span></span> <span data-ttu-id="52f89-109">Per altre informazioni su come rimuovere l'unità esistente dal dispositivo Surface Hub, vedi La sostituzione [dell'unità SSD](surface-hub-ssd-replacement.md)di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="52f89-109">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52f89-110">Non lasciare che il dispositivo vada in sospensione o interrompa il download del file di immagine.</span><span class="sxs-lookup"><span data-stu-id="52f89-110">Do not let the device go to sleep or interrupt the download of the image file.</span></span>

<span data-ttu-id="52f89-111">Se lo strumento non riesce a riimimare l'unità, contatta il [supporto di Surface Hub.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)</span><span class="sxs-lookup"><span data-stu-id="52f89-111">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="52f89-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="52f89-112">Prerequisites</span></span>

### <span data-ttu-id="52f89-113">Mandatory</span><span class="sxs-lookup"><span data-stu-id="52f89-113">Mandatory</span></span>

- <span data-ttu-id="52f89-114">Pc host che esegue la versione a 64 bit di Windows 10 versione 1607 o successiva.</span><span class="sxs-lookup"><span data-stu-id="52f89-114">Host PC running 64-bit version of Windows 10, version 1607 or higher.</span></span>
- <span data-ttu-id="52f89-115">Accesso a Internet</span><span class="sxs-lookup"><span data-stu-id="52f89-115">Internet access</span></span>
- <span data-ttu-id="52f89-116">Aprire la porta USB 2.0 o successiva</span><span class="sxs-lookup"><span data-stu-id="52f89-116">Open USB 2.0 or greater port</span></span>
- <span data-ttu-id="52f89-117">Cavo DA USB a SATA</span><span class="sxs-lookup"><span data-stu-id="52f89-117">USB-to-SATA cable</span></span>
- <span data-ttu-id="52f89-118">10 GB di spazio libero su disco nel computer host</span><span class="sxs-lookup"><span data-stu-id="52f89-118">10 GB of free disk space on the host computer</span></span>
- <span data-ttu-id="52f89-119">SSD forniti con Surface Hub o un SSD fornito dal supporto in sostituzione.</span><span class="sxs-lookup"><span data-stu-id="52f89-119">SSDs shipped with Surface Hub or a SSD provided by Support as a replacement.</span></span> <span data-ttu-id="52f89-120">Le SSD non fornite da Microsoft non sono supportate.</span><span class="sxs-lookup"><span data-stu-id="52f89-120">SSDs not supplied by Microsoft are not supported.</span></span>

### <span data-ttu-id="52f89-121">Consigliato</span><span class="sxs-lookup"><span data-stu-id="52f89-121">Recommended</span></span>

- <span data-ttu-id="52f89-122">Connessione Internet ad alta velocità</span><span class="sxs-lookup"><span data-stu-id="52f89-122">High-speed Internet connection</span></span>
- <span data-ttu-id="52f89-123">Aprire la porta USB 3.0</span><span class="sxs-lookup"><span data-stu-id="52f89-123">Open USB 3.0 port</span></span>
- <span data-ttu-id="52f89-124">Cavo USB 3.0 o superiore da USB a SATA</span><span class="sxs-lookup"><span data-stu-id="52f89-124">USB 3.0 or higher USB-to-SATA cable</span></span>
- <span data-ttu-id="52f89-125">Lo strumento di creazione di immagini è stato testato con la seguente creazione e modello di cavi:</span><span class="sxs-lookup"><span data-stu-id="52f89-125">The imaging tool was tested with the following make and model of cables:</span></span>
    - <span data-ttu-id="52f89-126">Startech USB312SAT3CB</span><span class="sxs-lookup"><span data-stu-id="52f89-126">Startech USB312SAT3CB</span></span>
    - <span data-ttu-id="52f89-127">Rosawill RCUC16001</span><span class="sxs-lookup"><span data-stu-id="52f89-127">Rosewill RCUC16001</span></span>
    - <span data-ttu-id="52f89-128">Ugreen 20231</span><span class="sxs-lookup"><span data-stu-id="52f89-128">Ugreen 20231</span></span>

## <span data-ttu-id="52f89-129">Scaricare lo strumento di ripristino di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="52f89-129">Download Surface Hub Recovery Tool</span></span>

<span data-ttu-id="52f89-130">Lo strumento di ripristino di Surface Hub è disponibile per il download da [Strumenti di Surface Hub per l'IT](https://www.microsoft.com/download/details.aspx?id=52210)  con il nome file **SurfaceHub_Recovery_v2.7.139.0.msi**.</span><span class="sxs-lookup"><span data-stu-id="52f89-130">Surface Hub Recovery Tool is available for download from [Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)  under the file name **SurfaceHub_Recovery_v2.7.139.0.msi**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52f89-131">Questa versione, rilasciata l'11 febbraio 2021, sostituisce la build precedente, che non è più funzionante.</span><span class="sxs-lookup"><span data-stu-id="52f89-131">This version, released Feb 11, 2021, replaces the earlier build, which is no longer functional.</span></span> <span data-ttu-id="52f89-132">Se lo strumento è stato scaricato in precedenza, eliminare e usare la versione corrente.</span><span class="sxs-lookup"><span data-stu-id="52f89-132">If you downloaded this tool previously, please discard and use the current version.</span></span>

<span data-ttu-id="52f89-133">Per avviare il download, fare clic su **Download,** **scegliereSurfaceHub_Recovery_v2.7.139.0.msi'elenco** e fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="52f89-133">To start the download, click **Download**, choose **SurfaceHub_Recovery_v2.7.139.0.msi**  from the list, and click **Next**.</span></span> <span data-ttu-id="52f89-134">Dal popup scegliere una delle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="52f89-134">From the pop-up, choose one of the following:</span></span>

- <span data-ttu-id="52f89-135">Fare **clic su Esegui** per avviare immediatamente l'installazione.</span><span class="sxs-lookup"><span data-stu-id="52f89-135">Click **Run** to start the installation immediately.</span></span>
- <span data-ttu-id="52f89-136">Fare **clic su** Salva per copiare il download nel computer per un'installazione successiva.</span><span class="sxs-lookup"><span data-stu-id="52f89-136">Click **Save** to copy the download to your computer for later installation.</span></span>

<span data-ttu-id="52f89-137">Installare lo strumento di ripristino di Surface Hub nel PC host.</span><span class="sxs-lookup"><span data-stu-id="52f89-137">Install Surface Hub Recovery Tool on the host PC.</span></span>

## <span data-ttu-id="52f89-138">Eseguire lo strumento di ripristino di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="52f89-138">Run Surface Hub Recovery Tool</span></span>

1. <span data-ttu-id="52f89-139">Nel PC host seleziona il pulsante **Start,** scorri l'elenco alfabetico a sinistra e seleziona il collegamento dello strumento di ripristino.</span><span class="sxs-lookup"><span data-stu-id="52f89-139">On the host PC, select the **Start** button, scroll through the alphabetical list on the left, and select the recovery tool shortcut.</span></span>

    ![Collegamento dello strumento di ripristino di Microsoft Surface Hub](images/shrt-shortcut.png)

2. <span data-ttu-id="52f89-141">Fai clic su **Start**.</span><span class="sxs-lookup"><span data-stu-id="52f89-141">Click **Start**.</span></span>

    ![Pulsante Start dello strumento di ripristino](images/shrt-start.png)


3. <span data-ttu-id="52f89-143">Nella finestra **Linee guida** fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="52f89-143">In the **Guidance** window, click **Next**.</span></span>

    ![Non consentire al computer di passare alla guida di sospensione](images/shrt-guidance.png)

4. <span data-ttu-id="52f89-145">Nella finestra Seleziona immagine fare clic su **RS2** o sul successore **20H2,** selezionare **Continua e** quindi **selezionare Scarica immagine.**</span><span class="sxs-lookup"><span data-stu-id="52f89-145">In the Select image window, click either **RS2** or its successor **20H2**, select **Continue,** and then select **Download image.**</span></span>

     <span data-ttu-id="52f89-146">![Immagine di download dello strumento ](images/shrt-select-image.png) ![ di recupero dell'immagine selezionata](images/shrt-download-image.png)</span><span class="sxs-lookup"><span data-stu-id="52f89-146">![Recovery Tool Select image](images/shrt-select-image.png) ![Recovery Tool Download image](images/shrt-download-image.png)</span></span>

5. <span data-ttu-id="52f89-147">Il tempo necessario per scaricare l'immagine di ripristino dipende dalla velocità della connessione Internet.</span><span class="sxs-lookup"><span data-stu-id="52f89-147">Time to download the recovery image is dependent on internet connection speeds.</span></span> <span data-ttu-id="52f89-148">In una connessione aziendale media, il download del file di immagine da 8 GB può richiedere fino a un'ora.</span><span class="sxs-lookup"><span data-stu-id="52f89-148">On an average corporate connection, it can take up to an hour to download the 8GB image file.</span></span>

    ![Download dell'immagine](images/shrt-download.png)



5. <span data-ttu-id="52f89-150">Al termine del download, lo strumento indica di connettere un'unità SSD.</span><span class="sxs-lookup"><span data-stu-id="52f89-150">When the download is complete, the tool instructs you to connect an SSD drive.</span></span> <span data-ttu-id="52f89-151">Se lo strumento non è in grado di individuare l'unità collegata, è probabile che il cavo utilizzato non sia in grado di segnalare il nome dell'unità SSD a Windows.</span><span class="sxs-lookup"><span data-stu-id="52f89-151">If the tool is unable to locate the attached drive, there is a good chance that the cable being used is not reporting the name of the SSD to Windows.</span></span>  <span data-ttu-id="52f89-152">Lo strumento di creazione di immagini deve trovare il nome dell'unità come "LITEON L CH-128V2S USB Device" prima di poter continuare.</span><span class="sxs-lookup"><span data-stu-id="52f89-152">The imaging tool must find the name of the drive as "LITEON L CH-128V2S USB Device" before it can continue.</span></span>  <span data-ttu-id="52f89-153">Per altre informazioni su come rimuovere l'unità esistente dal dispositivo Surface Hub, vedi La sostituzione [dell'unità SSD](surface-hub-ssd-replacement.md)di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="52f89-153">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

    ![Connettere SSD](images/shrt-drive.png)

6. <span data-ttu-id="52f89-155">Quando l'unità viene riconosciuta, fai clic su **Start** per avviare il processo di creazione di una immagine.</span><span class="sxs-lookup"><span data-stu-id="52f89-155">When the drive is recognized, click **Start** to begin the re-imaging process.</span></span> <span data-ttu-id="52f89-156">Nell'avviso che indica che tutti i dati nell'unità verranno cancellati, fare clic su **OK.**</span><span class="sxs-lookup"><span data-stu-id="52f89-156">On the warning that all data on the drive will be erased, click **OK**.</span></span>



    <span data-ttu-id="52f89-157">Prima di applicare l'immagine di sistema all'unità, l'unità SSD viene ripartizionata e formattata.</span><span class="sxs-lookup"><span data-stu-id="52f89-157">Prior to applying the system image to the drive, the SSD is repartitioned and formatted.</span></span> <span data-ttu-id="52f89-158">La copia dei file binari di sistema richiede circa 30 minuti, ma può richiedere più tempo a seconda della velocità del bus USB, del cavo in uso o del software antivirus installato nel sistema.</span><span class="sxs-lookup"><span data-stu-id="52f89-158">Copying the system binaries will take approximately 30 minutes, but can take longer depending on the speed of your USB bus, the cable being used, or antivirus software installed on your system.</span></span>



## <span data-ttu-id="52f89-159">Risoluzione dei problemi e problemi comuni</span><span class="sxs-lookup"><span data-stu-id="52f89-159">Troubleshooting and common problems</span></span>

<span data-ttu-id="52f89-160">Problema</span><span class="sxs-lookup"><span data-stu-id="52f89-160">Issue</span></span> | <span data-ttu-id="52f89-161">Note</span><span class="sxs-lookup"><span data-stu-id="52f89-161">Notes</span></span>
--- | ---
<span data-ttu-id="52f89-162">Lo strumento non riesce a creare un'immagine del disco SSD</span><span class="sxs-lookup"><span data-stu-id="52f89-162">The tool fails to image the SSD</span></span> | <span data-ttu-id="52f89-163">Assicurati di usare un SSD fornito in fabbrica e uno dei cavi testati.</span><span class="sxs-lookup"><span data-stu-id="52f89-163">Make sure you are using a factory-supplied SSD and one of the tested cables.</span></span>
<span data-ttu-id="52f89-164">Il processo di reimaging viene visualizzato interrotto/bloccato</span><span class="sxs-lookup"><span data-stu-id="52f89-164">The reimaging process appears halted/frozen</span></span> | <span data-ttu-id="52f89-165">È possibile chiudere e riavviare lo strumento di ripristino di Surface Hub senza alcun effetto negativo sull'unità SSD.</span><span class="sxs-lookup"><span data-stu-id="52f89-165">It is safe to close and restart the Surface Hub Recovery Tool with no ill effect to the SSD.</span></span>
<span data-ttu-id="52f89-166">L'unità non viene riconosciuta dallo strumento</span><span class="sxs-lookup"><span data-stu-id="52f89-166">The drive isn’t recognized by the tool</span></span> | <span data-ttu-id="52f89-167">Verifica che l'unità SSD di Surface Hub sia enumerata come unità Lite-On, "Dispositivo USB LITEON L CH-128V2S".</span><span class="sxs-lookup"><span data-stu-id="52f89-167">Verify that the Surface Hub SSD is enumerated as a Lite-On drive, "LITEON L CH-128V2S USB Device".</span></span>  <span data-ttu-id="52f89-168">Se l'unità viene riconosciuta come un altro dispositivo denominato, il cavo corrente non è compatibile.</span><span class="sxs-lookup"><span data-stu-id="52f89-168">If the drive is recognized as another named device, your current cable isn’t compatible.</span></span> <span data-ttu-id="52f89-169">Provare un altro cavo o uno dei cavi testati elencati in precedenza.</span><span class="sxs-lookup"><span data-stu-id="52f89-169">Try another cable or one of the tested cable listed above.</span></span>
<span data-ttu-id="52f89-170">Errore: -2147024809</span><span class="sxs-lookup"><span data-stu-id="52f89-170">Error: -2147024809</span></span> | <span data-ttu-id="52f89-171">Apri Gestione disco e rimuovi le partizioni nell'unità Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="52f89-171">Open Disk Manager and remove the partitions on the Surface Hub drive.</span></span>  <span data-ttu-id="52f89-172">Disconnettere e riconnettere l'unità al computer host.</span><span class="sxs-lookup"><span data-stu-id="52f89-172">Disconnect and reconnect the drive to the host machine.</span></span> <span data-ttu-id="52f89-173">Riavvia di nuovo lo strumento per la creazione di immagini.</span><span class="sxs-lookup"><span data-stu-id="52f89-173">Restart the imaging tool again.</span></span>

<span data-ttu-id="52f89-174">Se lo strumento non riesce a riimimare l'unità, contatta il [supporto di Surface Hub.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)</span><span class="sxs-lookup"><span data-stu-id="52f89-174">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="52f89-175">Cronologia delle versioni</span><span class="sxs-lookup"><span data-stu-id="52f89-175">Version history</span></span>


### <span data-ttu-id="52f89-176">Versione v2.7.139.0</span><span class="sxs-lookup"><span data-stu-id="52f89-176">Version v2.7.139.0</span></span>

*<span data-ttu-id="52f89-177">Data di rilascio: 11 febbraio 2021</span><span class="sxs-lookup"><span data-stu-id="52f89-177">Release date: February 11, 2021</span></span>*<br>
<span data-ttu-id="52f89-178">Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="52f89-178">This version of Surface Hub Recovery Tool adds support for the following:</span></span>

- <span data-ttu-id="52f89-179">Aggiornamento della sicurezza</span><span class="sxs-lookup"><span data-stu-id="52f89-179">Security update</span></span>


### <span data-ttu-id="52f89-180">Versione v2.0.139.0</span><span class="sxs-lookup"><span data-stu-id="52f89-180">Version v2.0.139.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52f89-181">Questa versione non è più funzionante.</span><span class="sxs-lookup"><span data-stu-id="52f89-181">This version is no longer functional.</span></span> <span data-ttu-id="52f89-182">Scarica la versione corrente, elencata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="52f89-182">Please download the current version, listed above.</span></span> 

*<span data-ttu-id="52f89-183">Data di rilascio: 18 dicembre 2020</span><span class="sxs-lookup"><span data-stu-id="52f89-183">Release date: December 18, 2020</span></span>*<br>
<span data-ttu-id="52f89-184">Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="52f89-184">This version of Surface Hub Recovery Tool adds support for the following:</span></span>
- <span data-ttu-id="52f89-185">Aggiornamento per supportare Windows 10 Team 2020 Update (20H2)</span><span class="sxs-lookup"><span data-stu-id="52f89-185">Update to support Windows 10 Team 2020 Update (20H2)</span></span>
- <span data-ttu-id="52f89-186">Miglioramenti dell'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="52f89-186">User experience improvements</span></span>
- <span data-ttu-id="52f89-187">Modifiche architetturali</span><span class="sxs-lookup"><span data-stu-id="52f89-187">Architectural changes</span></span>
- <span data-ttu-id="52f89-188">Aggiunte di telemetria</span><span class="sxs-lookup"><span data-stu-id="52f89-188">Telemetry additions</span></span>


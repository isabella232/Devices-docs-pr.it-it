---
title: Uso dello strumento di ripristino di Surface Hub
description: Come usare lo strumento di ripristino di Surface hub per ricreare l'immagine dell'SSD.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: gestire Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 12/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: a9ebab6848efa706609a39b0eb99fa42df2156bf
ms.sourcegitcommit: ce7ad475b776a78ba215e77111ea5371afeb4f28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "11237335"
---
# <span data-ttu-id="faad4-104">Uso dello strumento di ripristino di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="faad4-104">Using the Surface Hub Recovery Tool</span></span>

<span data-ttu-id="faad4-105">Lo [strumento Microsoft Surface Hub Recovery](https://www.microsoft.com/download/details.aspx?id=52210) consente di ricreare l'unità SSD (Solid State Drive) di Surface hub usando un dispositivo desktop Windows 10, senza chiamare il supporto o sostituendo l'SSD.</span><span class="sxs-lookup"><span data-stu-id="faad4-105">The [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) helps you re-image your Surface Hub Solid State Drive (SSD) using a Windows 10 desktop device, without calling support or replacing the SSD.</span></span> <span data-ttu-id="faad4-106">Con questo strumento puoi rieseguire l'immagine di un SSD che ha una password di amministratore sconosciuta, errori di avvio, non è riuscito a completare un ripristino del cloud o per un dispositivo con una versione precedente del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="faad4-106">With this tool, you can reimage an SSD that has an unknown Administrator password, boot errors, was unable to complete a cloud recovery, or for a device that has an older version of the operating system.</span></span> <span data-ttu-id="faad4-107">Lo strumento non risolverà gli SSD danneggiati fisicamente.</span><span class="sxs-lookup"><span data-stu-id="faad4-107">The tool will not fix physically damaged SSDs.</span></span>

<span data-ttu-id="faad4-108">Per ricreare l'unità SSD Surface hub usando lo strumento di ripristino, è necessario rimuovere l'SSD dall'hub di Surface, connettere il drive al cavo USB-to-SATA e quindi connettere il cavo al PC desktop in cui è installato lo strumento di ripristino.</span><span class="sxs-lookup"><span data-stu-id="faad4-108">To re-image the Surface Hub SSD using the Recovery Tool, you'll need to remove the SSD from the Surface Hub, connect the drive to the USB-to-SATA cable, and then connect the cable to the desktop PC on which the Recovery Tool is installed.</span></span> <span data-ttu-id="faad4-109">Per altre informazioni su come rimuovere l'unità esistente dal proprio hub Surface, vedere [sostituzione di Surface Hub SSD](surface-hub-ssd-replacement.md).</span><span class="sxs-lookup"><span data-stu-id="faad4-109">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="faad4-110">Non consentire al dispositivo di andare a dormire o interrompere il download del file di immagine.</span><span class="sxs-lookup"><span data-stu-id="faad4-110">Do not let the device go to sleep or interrupt the download of the image file.</span></span>

<span data-ttu-id="faad4-111">Se lo strumento non riesce a rieseguire la riimmagine dell'unità, contattare il [supporto per Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span><span class="sxs-lookup"><span data-stu-id="faad4-111">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="faad4-112">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="faad4-112">Prerequisites</span></span>

### <span data-ttu-id="faad4-113">Mandatory</span><span class="sxs-lookup"><span data-stu-id="faad4-113">Mandatory</span></span>

- <span data-ttu-id="faad4-114">PC host con versione a 64 bit di Windows 10, versione 1607 o successiva.</span><span class="sxs-lookup"><span data-stu-id="faad4-114">Host PC running 64-bit version of Windows 10, version 1607 or higher.</span></span>
- <span data-ttu-id="faad4-115">Accesso a Internet</span><span class="sxs-lookup"><span data-stu-id="faad4-115">Internet access</span></span>
- <span data-ttu-id="faad4-116">Aprire la porta USB 2,0 o maggiore</span><span class="sxs-lookup"><span data-stu-id="faad4-116">Open USB 2.0 or greater port</span></span>
- <span data-ttu-id="faad4-117">Cavo da USB a SATA</span><span class="sxs-lookup"><span data-stu-id="faad4-117">USB-to-SATA cable</span></span>
- <span data-ttu-id="faad4-118">10 GB di spazio libero su disco nel computer host</span><span class="sxs-lookup"><span data-stu-id="faad4-118">10 GB of free disk space on the host computer</span></span>
- <span data-ttu-id="faad4-119">SSD spediti con Surface Hub o un SSD forniti dal supporto come sostituto.</span><span class="sxs-lookup"><span data-stu-id="faad4-119">SSDs shipped with Surface Hub or a SSD provided by Support as a replacement.</span></span> <span data-ttu-id="faad4-120">Gli SSD non forniti da Microsoft non sono supportati.</span><span class="sxs-lookup"><span data-stu-id="faad4-120">SSDs not supplied by Microsoft are not supported.</span></span>

### <span data-ttu-id="faad4-121">Consigliato</span><span class="sxs-lookup"><span data-stu-id="faad4-121">Recommended</span></span>

- <span data-ttu-id="faad4-122">Connessione Internet ad alta velocità</span><span class="sxs-lookup"><span data-stu-id="faad4-122">High-speed Internet connection</span></span>
- <span data-ttu-id="faad4-123">Aprire la porta USB 3,0</span><span class="sxs-lookup"><span data-stu-id="faad4-123">Open USB 3.0 port</span></span>
- <span data-ttu-id="faad4-124">USB 3,0 o superiore cavo USB-to-SATA</span><span class="sxs-lookup"><span data-stu-id="faad4-124">USB 3.0 or higher USB-to-SATA cable</span></span>
- <span data-ttu-id="faad4-125">Lo strumento di imaging è stato testato con la creazione e il modello di cavi seguenti:</span><span class="sxs-lookup"><span data-stu-id="faad4-125">The imaging tool was tested with the following make and model of cables:</span></span>
    - <span data-ttu-id="faad4-126">Startech USB312SAT3CB</span><span class="sxs-lookup"><span data-stu-id="faad4-126">Startech USB312SAT3CB</span></span>
    - <span data-ttu-id="faad4-127">Rosewill RCUC16001</span><span class="sxs-lookup"><span data-stu-id="faad4-127">Rosewill RCUC16001</span></span>
    - <span data-ttu-id="faad4-128">UGreen 20231</span><span class="sxs-lookup"><span data-stu-id="faad4-128">Ugreen 20231</span></span>

## <span data-ttu-id="faad4-129">Scaricare lo strumento Surface Hub Recovery</span><span class="sxs-lookup"><span data-stu-id="faad4-129">Download Surface Hub Recovery Tool</span></span>

<span data-ttu-id="faad4-130">Lo strumento di ripristino di Surface Hub è disponibile per il download dagli [strumenti di Surface hub per](https://www.microsoft.com/download/details.aspx?id=52210)  l'oggetto sotto il nome file **SurfaceHub_Recovery_v2.0.139.0.msi**.</span><span class="sxs-lookup"><span data-stu-id="faad4-130">Surface Hub Recovery Tool is available for download from [Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210)  under the file name **SurfaceHub_Recovery_v2.0.139.0.msi**.</span></span>

<span data-ttu-id="faad4-131">Per avviare il download, fare clic su **Scarica**, scegliere **SurfaceHub_Recovery_v2.0.139.0.msi** nell'elenco e fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="faad4-131">To start the download, click **Download**, choose **SurfaceHub_Recovery_v2.0.139.0.msi** from the list, and click **Next**.</span></span> <span data-ttu-id="faad4-132">Nella finestra popup scegliere una delle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="faad4-132">From the pop-up, choose one of the following:</span></span>

- <span data-ttu-id="faad4-133">Fare clic su **Esegui** per avviare immediatamente l'installazione.</span><span class="sxs-lookup"><span data-stu-id="faad4-133">Click **Run** to start the installation immediately.</span></span>
- <span data-ttu-id="faad4-134">Fare clic su **Salva** per copiare il download nel computer per l'installazione successiva.</span><span class="sxs-lookup"><span data-stu-id="faad4-134">Click **Save** to copy the download to your computer for later installation.</span></span>

<span data-ttu-id="faad4-135">Installare lo strumento Surface Hub Recovery nel PC host.</span><span class="sxs-lookup"><span data-stu-id="faad4-135">Install Surface Hub Recovery Tool on the host PC.</span></span>

## <span data-ttu-id="faad4-136">Strumento Esegui recupero Hub Surface</span><span class="sxs-lookup"><span data-stu-id="faad4-136">Run Surface Hub Recovery Tool</span></span>

1. <span data-ttu-id="faad4-137">Nel PC host selezionare il pulsante **Start** , scorrere l'elenco alfabetico a sinistra e selezionare il collegamento strumento ripristino.</span><span class="sxs-lookup"><span data-stu-id="faad4-137">On the host PC, select the **Start** button, scroll through the alphabetical list on the left, and select the recovery tool shortcut.</span></span>

    ![Collegamento allo strumento Ripristino superficie Hub Microsoft](images/shrt-shortcut.png)

2. <span data-ttu-id="faad4-139">Fai clic su **Start**.</span><span class="sxs-lookup"><span data-stu-id="faad4-139">Click **Start**.</span></span>

    ![Pulsante Start dello strumento di ripristino](images/shrt-start.png)


3. <span data-ttu-id="faad4-141">Nella finestra **linee guida** fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="faad4-141">In the **Guidance** window, click **Next**.</span></span>

    ![Non consentire al computer di accedere alle indicazioni per il sonno](images/shrt-guidance.png)

4. <span data-ttu-id="faad4-143">Nella finestra Seleziona immagine fare clic su **RS2** o sul relativo successore **20H2**, selezionare **continua** e quindi selezionare **Scarica immagine.**</span><span class="sxs-lookup"><span data-stu-id="faad4-143">In the Select image window, click either **RS2** or its successor **20H2**, select **Continue,** and then select **Download image.**</span></span>

     <span data-ttu-id="faad4-144">![Strumento di ripristino selezionare immagine ](images/shrt-select-image.png) ![ download strumento di recupero immagini](images/shrt-download-image.png)</span><span class="sxs-lookup"><span data-stu-id="faad4-144">![Recovery Tool Select image](images/shrt-select-image.png) ![Recovery Tool Download image](images/shrt-download-image.png)</span></span>

5. <span data-ttu-id="faad4-145">Il tempo necessario per scaricare l'immagine di ripristino dipende dalle velocità di connessione Internet.</span><span class="sxs-lookup"><span data-stu-id="faad4-145">Time to download the recovery image is dependent on internet connection speeds.</span></span> <span data-ttu-id="faad4-146">In una connessione aziendale media può essere necessaria fino a un'ora per scaricare il file di immagine da 8GB.</span><span class="sxs-lookup"><span data-stu-id="faad4-146">On an average corporate connection, it can take up to an hour to download the 8GB image file.</span></span>

    ![Download dell'immagine](images/shrt-download.png)



5. <span data-ttu-id="faad4-148">Al termine del download, lo strumento indica di connettere un'unità SSD.</span><span class="sxs-lookup"><span data-stu-id="faad4-148">When the download is complete, the tool instructs you to connect an SSD drive.</span></span> <span data-ttu-id="faad4-149">Se lo strumento non riesce a trovare l'unità collegata, è probabile che il cavo usato non riferisca il nome dell'SSD a Windows.</span><span class="sxs-lookup"><span data-stu-id="faad4-149">If the tool is unable to locate the attached drive, there is a good chance that the cable being used is not reporting the name of the SSD to Windows.</span></span>  <span data-ttu-id="faad4-150">Lo strumento di imaging deve trovare il nome dell'unità come "LITEON L CH-128V2S USB Device" prima che possa continuare.</span><span class="sxs-lookup"><span data-stu-id="faad4-150">The imaging tool must find the name of the drive as "LITEON L CH-128V2S USB Device" before it can continue.</span></span>  <span data-ttu-id="faad4-151">Per altre informazioni su come rimuovere l'unità esistente dal proprio hub Surface, vedere [sostituzione di Surface Hub SSD](surface-hub-ssd-replacement.md).</span><span class="sxs-lookup"><span data-stu-id="faad4-151">For more information on how to remove the existing drive from your Surface Hub, see [Surface Hub SSD replacement](surface-hub-ssd-replacement.md).</span></span>

    ![Connettere SSD](images/shrt-drive.png)

6. <span data-ttu-id="faad4-153">Quando l'unità viene riconosciuta, fare clic sul pulsante **Start** per avviare il processo di creazione di immagini.</span><span class="sxs-lookup"><span data-stu-id="faad4-153">When the drive is recognized, click **Start** to begin the re-imaging process.</span></span> <span data-ttu-id="faad4-154">Nell'avviso che tutti i dati dell'unità verranno cancellati, fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="faad4-154">On the warning that all data on the drive will be erased, click **OK**.</span></span>



    <span data-ttu-id="faad4-155">Prima di applicare l'immagine del sistema all'unità, l'SSD viene ripartizionato e formattato.</span><span class="sxs-lookup"><span data-stu-id="faad4-155">Prior to applying the system image to the drive, the SSD is repartitioned and formatted.</span></span> <span data-ttu-id="faad4-156">La copia dei file binari di sistema impiegano circa 30 minuti, ma può richiedere più tempo a seconda della velocità del bus USB, del cavo usato o del software antivirus installato nel sistema.</span><span class="sxs-lookup"><span data-stu-id="faad4-156">Copying the system binaries will take approximately 30 minutes, but can take longer depending on the speed of your USB bus, the cable being used, or antivirus software installed on your system.</span></span>



## <span data-ttu-id="faad4-157">Problemi comuni per la risoluzione dei problemi</span><span class="sxs-lookup"><span data-stu-id="faad4-157">Troubleshooting and common problems</span></span>

<span data-ttu-id="faad4-158">Problema</span><span class="sxs-lookup"><span data-stu-id="faad4-158">Issue</span></span> | <span data-ttu-id="faad4-159">Note</span><span class="sxs-lookup"><span data-stu-id="faad4-159">Notes</span></span>
--- | ---
<span data-ttu-id="faad4-160">Lo strumento non riesce a immagine dell'SSD</span><span class="sxs-lookup"><span data-stu-id="faad4-160">The tool fails to image the SSD</span></span> | <span data-ttu-id="faad4-161">Assicurarsi di usare un SSD fornito in fabbrica e uno dei cavi testati.</span><span class="sxs-lookup"><span data-stu-id="faad4-161">Make sure you are using a factory-supplied SSD and one of the tested cables.</span></span>
<span data-ttu-id="faad4-162">Il processo di riimaging viene interrotto/bloccato</span><span class="sxs-lookup"><span data-stu-id="faad4-162">The reimaging process appears halted/frozen</span></span> | <span data-ttu-id="faad4-163">È sicuro chiudere e riavviare lo strumento di ripristino di Surface Hub senza effetti negativi per l'SSD.</span><span class="sxs-lookup"><span data-stu-id="faad4-163">It is safe to close and restart the Surface Hub Recovery Tool with no ill effect to the SSD.</span></span>
<span data-ttu-id="faad4-164">L'unità non viene riconosciuta dallo strumento</span><span class="sxs-lookup"><span data-stu-id="faad4-164">The drive isn’t recognized by the tool</span></span> | <span data-ttu-id="faad4-165">Verificare che l'unità SSD Surface hub sia enumerata come Lite-On Drive, "LITEON L CH-128V2S USB Device".</span><span class="sxs-lookup"><span data-stu-id="faad4-165">Verify that the Surface Hub SSD is enumerated as a Lite-On drive, "LITEON L CH-128V2S USB Device".</span></span>  <span data-ttu-id="faad4-166">Se l'unità viene riconosciuta come un altro dispositivo denominato, il cavo corrente non è compatibile.</span><span class="sxs-lookup"><span data-stu-id="faad4-166">If the drive is recognized as another named device, your current cable isn’t compatible.</span></span> <span data-ttu-id="faad4-167">Provare un altro cavo o uno dei cavi testati sopra elencati.</span><span class="sxs-lookup"><span data-stu-id="faad4-167">Try another cable or one of the tested cable listed above.</span></span>
<span data-ttu-id="faad4-168">Errore:-2147024809</span><span class="sxs-lookup"><span data-stu-id="faad4-168">Error: -2147024809</span></span> | <span data-ttu-id="faad4-169">Aprire Disk Manager e rimuovere le partizioni nell'unità Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="faad4-169">Open Disk Manager and remove the partitions on the Surface Hub drive.</span></span>  <span data-ttu-id="faad4-170">Disconnettere e riconnettere l'unità al computer host.</span><span class="sxs-lookup"><span data-stu-id="faad4-170">Disconnect and reconnect the drive to the host machine.</span></span> <span data-ttu-id="faad4-171">Riavviare lo strumento di imaging.</span><span class="sxs-lookup"><span data-stu-id="faad4-171">Restart the imaging tool again.</span></span>

<span data-ttu-id="faad4-172">Se lo strumento non riesce a rieseguire la riimmagine dell'unità, contattare il [supporto per Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span><span class="sxs-lookup"><span data-stu-id="faad4-172">If the tool is unsuccessful in reimaging your drive, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>

## <span data-ttu-id="faad4-173">Cronologia versioni</span><span class="sxs-lookup"><span data-stu-id="faad4-173">Version history</span></span>

### <span data-ttu-id="faad4-174">Versione v 2.0.139.0</span><span class="sxs-lookup"><span data-stu-id="faad4-174">Version v2.0.139.0</span></span>

*<span data-ttu-id="faad4-175">Data di rilascio: 18 dicembre 2020</span><span class="sxs-lookup"><span data-stu-id="faad4-175">Release date: December 18, 2020</span></span>*<br>
<span data-ttu-id="faad4-176">Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="faad4-176">This version of Surface Hub Recovery Tool adds support for the following:</span></span>
- <span data-ttu-id="faad4-177">Aggiornamento per supportare l'aggiornamento di Windows 10 team 2020 (20H2)</span><span class="sxs-lookup"><span data-stu-id="faad4-177">Update to support Windows 10 Team 2020 Update (20H2)</span></span>
- <span data-ttu-id="faad4-178">Miglioramenti dell'esperienza utente</span><span class="sxs-lookup"><span data-stu-id="faad4-178">User experience improvements</span></span>
- <span data-ttu-id="faad4-179">Modifiche architetturali</span><span class="sxs-lookup"><span data-stu-id="faad4-179">Architectural changes</span></span>
- <span data-ttu-id="faad4-180">Aggiunte di telemetria</span><span class="sxs-lookup"><span data-stu-id="faad4-180">Telemetry additions</span></span>


---
title: Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT
description: Quando si usa MDT per distribuire Windows 10 in computer portatili di Surface, è necessario importare i driver della tastiera da usare nell'ambiente Windows PE.
keywords: superficie di Windows 10, automatizza, Personalizza, MDT
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
ms.reviewer: scottmca
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: 5d4e4b46c109d9fe24fe75151c9eb1e0a8b702c0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832553"
---
# <span data-ttu-id="277f8-104">Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT</span><span class="sxs-lookup"><span data-stu-id="277f8-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="277f8-105">Questo articolo risolve un approccio di distribuzione che usa Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="277f8-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="277f8-106">Puoi anche applicare queste informazioni ad altre metodologie di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="277f8-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="277f8-107">Nella maggior parte dei tipi di dispositivi Surface la tastiera dovrebbe funzionare durante l'installazione di Lite Touch (LTI).</span><span class="sxs-lookup"><span data-stu-id="277f8-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="277f8-108">Tuttavia, Surface laptop richiede alcuni driver aggiuntivi per abilitare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="277f8-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="277f8-109">Per i dispositivi portatili Surface (1st Gen) e Surface laptop 2, è necessario preparare la struttura delle cartelle e i profili di selezione che consentono di specificare i driver della tastiera da usare durante la fase di preinstallazione di Windows (Windows PE) di LTI.</span><span class="sxs-lookup"><span data-stu-id="277f8-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="277f8-110">Per altre informazioni sulla struttura delle cartelle, vedere [distribuire un'immagine di Windows 10 con MDT: passaggio 5: preparare il repository dei driver](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span><span class="sxs-lookup"><span data-stu-id="277f8-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>

> [!NOTE]
> <span data-ttu-id="277f8-111">Non è attualmente supportato per aggiungere i driver della tastiera di Surface laptop 2 e Surface laptop 3 nella stessa istanza di avvio di Windows PE a causa di un conflitto di driver. USA invece istanze separate.</span><span class="sxs-lookup"><span data-stu-id="277f8-111">It is currently not supported to add Surface Laptop 2 and Surface Laptop 3 keyboard drivers in the same Windows PE boot instance due to a driver conflict; use separate instances instead.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="277f8-112">Se si sta distribuendo un'immagine di Windows 10 a un computer portatile Surface con Windows 10 in modalità S preinstallato, vedere KB [4032347, problemi durante la distribuzione di dispositivi Windows in Surface con Windows 10 preinstallato in modalità s](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span><span class="sxs-lookup"><span data-stu-id="277f8-112">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="277f8-113">Per aggiungere i driver della tastiera al profilo di selezione, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-113">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="277f8-114">Scaricare il file MSI di Surface laptop più recente dalle posizioni appropriate:</span><span class="sxs-lookup"><span data-stu-id="277f8-114">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="277f8-115">Driver e firmware di Surface laptop (1a Gen)</span><span class="sxs-lookup"><span data-stu-id="277f8-115">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="277f8-116">Computer portatile di Surface 2 driver e firmware</span><span class="sxs-lookup"><span data-stu-id="277f8-116">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="277f8-117">Surface laptop 3 con driver e firmware per processori Intel</span><span class="sxs-lookup"><span data-stu-id="277f8-117">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="277f8-118">Estrarre il contenuto del file MSI della superficie portatile in una cartella che è possibile individuare facilmente, ad esempio c:\ surface_laptop_drivers).</span><span class="sxs-lookup"><span data-stu-id="277f8-118">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="277f8-119">Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="277f8-119">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="277f8-120">Aprire Deployment Workbench ed espandere il nodo **condivisioni distribuzione** e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64** .</span><span class="sxs-lookup"><span data-stu-id="277f8-120">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![Immagine che mostra la posizione della cartella WindowsPEX64 in Deployment Workbench](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="277f8-122">Fare clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegliere **Importa driver**.</span><span class="sxs-lookup"><span data-stu-id="277f8-122">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>
5. <span data-ttu-id="277f8-123">Seguire le istruzioni della procedura guidata Importa driver per importare le cartelle del driver nella cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="277f8-123">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

> [!NOTE]
>  <span data-ttu-id="277f8-124">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="277f8-124">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="277f8-125">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="277f8-125">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

<span data-ttu-id="277f8-126">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-126">To support Surface Laptop (1st Gen), import the following folders:</span></span>

 - <span data-ttu-id="277f8-127">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-127">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="277f8-128">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-128">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
 - <span data-ttu-id="277f8-129">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-129">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="277f8-130">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="277f8-130">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="277f8-131">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="277f8-131">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="277f8-132">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-132">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="277f8-133">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-133">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
- <span data-ttu-id="277f8-134">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-134">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
- <span data-ttu-id="277f8-135">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-135">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="277f8-136">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-136">To support Surface Laptop 2, import the following folders:</span></span>

 - <span data-ttu-id="277f8-137">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-137">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="277f8-138">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-138">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
 - <span data-ttu-id="277f8-139">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-139">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="277f8-140">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="277f8-140">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
 - <span data-ttu-id="277f8-141">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="277f8-141">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
 - <span data-ttu-id="277f8-142">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="277f8-142">SurfacePlatformInstaller\Drivers\System\UART</span></span>
 - <span data-ttu-id="277f8-143">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="277f8-143">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="277f8-144">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="277f8-144">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="277f8-145">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-145">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="277f8-146">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="277f8-146">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="277f8-147">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="277f8-147">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="277f8-148">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="277f8-148">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="277f8-149">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="277f8-149">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="277f8-150">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="277f8-150">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="277f8-151">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-151">SurfaceUpdate\Itouch</span></span>

 
<span data-ttu-id="277f8-152">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-152">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

- <span data-ttu-id="277f8-153">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-153">SurfaceUpdate\IclSerialIOGPIO</span></span>
- <span data-ttu-id="277f8-154">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="277f8-154">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="277f8-155">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="277f8-155">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="277f8-156">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="277f8-156">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="277f8-157">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="277f8-157">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="277f8-158">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="277f8-158">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="277f8-159">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="277f8-159">SurfaceUpdate\SurfaceHotPlug</span></span>
- <span data-ttu-id="277f8-160">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-160">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="277f8-161">L'importazione delle cartelle seguenti consentirà la funzionalità completa di tastiera, trackpad e tocco in PE per Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="277f8-161">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

- <span data-ttu-id="277f8-162">IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-162">IclSerialIOGPIO</span></span>
- <span data-ttu-id="277f8-163">IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="277f8-163">IclSerialIOI2C</span></span>
- <span data-ttu-id="277f8-164">IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="277f8-164">IclSerialIOSPI</span></span>
- <span data-ttu-id="277f8-165">IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="277f8-165">IclSerialIOUART</span></span>
- <span data-ttu-id="277f8-166">iTouch</span><span class="sxs-lookup"><span data-stu-id="277f8-166">itouch</span></span>
- <span data-ttu-id="277f8-167">IclChipset</span><span class="sxs-lookup"><span data-stu-id="277f8-167">IclChipset</span></span>
- <span data-ttu-id="277f8-168">IclChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="277f8-168">IclChipsetLPSS</span></span>
- <span data-ttu-id="277f8-169">IclChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="277f8-169">IclChipsetNorthpeak</span></span>
- <span data-ttu-id="277f8-170">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="277f8-170">ManagementEngine</span></span>
- <span data-ttu-id="277f8-171">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="277f8-171">SurfaceAcpiNotify</span></span>
- <span data-ttu-id="277f8-172">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="277f8-172">SurfaceBattery</span></span>
- <span data-ttu-id="277f8-173">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="277f8-173">SurfaceDockIntegration</span></span>
- <span data-ttu-id="277f8-174">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="277f8-174">SurfaceHidMini</span></span>
- <span data-ttu-id="277f8-175">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="277f8-175">SurfaceHotPlug</span></span>
- <span data-ttu-id="277f8-176">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="277f8-176">SurfaceIntegration</span></span>
- <span data-ttu-id="277f8-177">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="277f8-177">SurfaceSerialHub</span></span>
- <span data-ttu-id="277f8-178">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="277f8-178">SurfaceService</span></span>
- <span data-ttu-id="277f8-179">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="277f8-179">SurfaceStorageFwUpdate</span></span>


    > [!NOTE]
    >  <span data-ttu-id="277f8-180">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="277f8-180">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="277f8-181">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="277f8-181">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="277f8-182">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-182">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="277f8-183">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-183">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="277f8-184">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-184">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="277f8-185">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-185">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="277f8-186">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="277f8-186">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="277f8-187">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="277f8-187">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="277f8-188">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-188">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="277f8-189">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-189">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="277f8-190">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-190">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="277f8-191">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-191">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="277f8-192">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-192">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="277f8-193">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-193">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="277f8-194">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-194">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="277f8-195">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="277f8-195">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="277f8-196">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="277f8-196">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="277f8-197">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="277f8-197">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="277f8-198">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="277f8-198">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="277f8-199">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="277f8-199">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="277f8-200">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="277f8-200">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="277f8-201">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-201">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="277f8-202">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="277f8-202">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="277f8-203">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="277f8-203">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="277f8-204">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="277f8-204">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="277f8-205">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="277f8-205">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="277f8-206">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="277f8-206">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="277f8-207">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-207">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="277f8-208">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="277f8-208">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="277f8-209">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="277f8-209">SurfaceUpdate\IclSerialIOGPIO</span></span>
    - <span data-ttu-id="277f8-210">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="277f8-210">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="277f8-211">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="277f8-211">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="277f8-212">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="277f8-212">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="277f8-213">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="277f8-213">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="277f8-214">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="277f8-214">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="277f8-215">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="277f8-215">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="277f8-216">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="277f8-216">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="277f8-217">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="277f8-217">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="277f8-218">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="277f8-218">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="277f8-219">Verificare che la cartella WindowsPEX64 ora contenga i driver importati.</span><span class="sxs-lookup"><span data-stu-id="277f8-219">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="277f8-220">La cartella dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="277f8-220">The folder should resemble the following:</span></span>  

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="277f8-222">Configurare un profilo di selezione che usa la cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="277f8-222">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="277f8-223">Il profilo di selezione deve essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="277f8-223">The selection profile should resemble the following:</span></span>  

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="277f8-225">Configurare le proprietà di Windows PE della condivisione di distribuzione MDT per usare il nuovo profilo di selezione, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="277f8-225">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="277f8-226">Per la **piattaforma**, selezionare **x64**.</span><span class="sxs-lookup"><span data-stu-id="277f8-226">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="277f8-227">Per il **profilo di selezione**, selezionare il nuovo profilo.</span><span class="sxs-lookup"><span data-stu-id="277f8-227">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="277f8-228">Selezionare **Includi tutti i driver dal profilo di selezione**.</span><span class="sxs-lookup"><span data-stu-id="277f8-228">Select **Include all drivers from the selection profile**.</span></span>
   
   ![Immagine che mostra le proprietà di Windows PE della condivisione di distribuzione MDT](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="277f8-230">Verificare di aver configurato i driver per i portatili della superficie rimanente usando un profilo di selezione o una variabile **DriverGroup001** .</span><span class="sxs-lookup"><span data-stu-id="277f8-230">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="277f8-231">Per laptop Surface (1a generazione), il modello è **laptop Surface**.</span><span class="sxs-lookup"><span data-stu-id="277f8-231">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="277f8-232">I driver portatili di Surface rimanenti dovrebbero risiedere nella cartella di \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface come illustrato nella figura che segue questo elenco.</span><span class="sxs-lookup"><span data-stu-id="277f8-232">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="277f8-233">Per Surface laptop 2, il modello è **Surface laptop 2**.</span><span class="sxs-lookup"><span data-stu-id="277f8-233">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="277f8-234">I driver portatili Surface rimanenti dovrebbero risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 2.</span><span class="sxs-lookup"><span data-stu-id="277f8-234">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="277f8-235">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="277f8-235">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="277f8-236">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="277f8-236">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![Immagine che mostra i driver normali per laptop Surface (1a Gen) nella cartella Surface Laptop di Deployment Workbench](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="277f8-238">Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto in [distribuire un'immagine di Windows 10 con MDT: passaggio 6: creare la sequenza di attività di distribuzione](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span><span class="sxs-lookup"><span data-stu-id="277f8-238">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>

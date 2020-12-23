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
ms.openlocfilehash: d7ae6fc434f77cad86e73f111243968493de4ff2
ms.sourcegitcommit: e6224f81f8efb6ac862afec0e60e3ddb182e9e6f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "11247308"
---
# <span data-ttu-id="73e69-104">Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT</span><span class="sxs-lookup"><span data-stu-id="73e69-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="73e69-105">Questo articolo risolve un approccio di distribuzione che usa Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="73e69-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="73e69-106">Puoi anche applicare queste informazioni ad altre metodologie di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="73e69-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="73e69-107">Nella maggior parte dei tipi di dispositivi Surface la tastiera dovrebbe funzionare durante l'installazione di Lite Touch (LTI).</span><span class="sxs-lookup"><span data-stu-id="73e69-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="73e69-108">Tuttavia, Surface laptop richiede alcuni driver aggiuntivi per abilitare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="73e69-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="73e69-109">Per i dispositivi portatili Surface (1st Gen) e Surface laptop 2, è necessario preparare la struttura delle cartelle e i profili di selezione che consentono di specificare i driver della tastiera da usare durante la fase di preinstallazione di Windows (Windows PE) di LTI.</span><span class="sxs-lookup"><span data-stu-id="73e69-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="73e69-110">Per altre informazioni sulla struttura delle cartelle, vedere [distribuire un'immagine di Windows 10 con MDT: passaggio 5: preparare il repository dei driver](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span><span class="sxs-lookup"><span data-stu-id="73e69-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>


> [!IMPORTANT]
> <span data-ttu-id="73e69-111">Se si sta distribuendo un'immagine di Windows 10 a un computer portatile Surface con Windows 10 in modalità S preinstallato, vedere KB [4032347, problemi durante la distribuzione di dispositivi Windows in Surface con Windows 10 preinstallato in modalità s](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span><span class="sxs-lookup"><span data-stu-id="73e69-111">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="73e69-112">Per aggiungere i driver della tastiera al profilo di selezione, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-112">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="73e69-113">Scaricare il file MSI di Surface laptop più recente dalle posizioni appropriate:</span><span class="sxs-lookup"><span data-stu-id="73e69-113">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="73e69-114">Driver e firmware di Surface laptop (1a Gen)</span><span class="sxs-lookup"><span data-stu-id="73e69-114">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="73e69-115">Computer portatile di Surface 2 driver e firmware</span><span class="sxs-lookup"><span data-stu-id="73e69-115">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="73e69-116">Surface laptop 3 con driver e firmware per processori Intel</span><span class="sxs-lookup"><span data-stu-id="73e69-116">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="73e69-117">Estrarre il contenuto del file MSI della superficie portatile in una cartella che è possibile individuare facilmente, ad esempio c:\ surface_laptop_drivers).</span><span class="sxs-lookup"><span data-stu-id="73e69-117">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="73e69-118">Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="73e69-118">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="73e69-119">Aprire Deployment Workbench ed espandere il nodo **condivisioni distribuzione** e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64** .</span><span class="sxs-lookup"><span data-stu-id="73e69-119">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![Immagine che mostra la posizione della cartella WindowsPEX64 in Deployment Workbench](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="73e69-121">Fare clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegliere **Importa driver**.</span><span class="sxs-lookup"><span data-stu-id="73e69-121">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>
5. <span data-ttu-id="73e69-122">Seguire le istruzioni della procedura guidata Importa driver per importare le cartelle del driver nella cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="73e69-122">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

> [!NOTE]
>  <span data-ttu-id="73e69-123">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="73e69-123">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="73e69-124">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="73e69-124">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

<span data-ttu-id="73e69-125">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-125">To support Surface Laptop (1st Gen), import the following folders:</span></span>

 - <span data-ttu-id="73e69-126">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-126">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="73e69-127">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-127">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
 - <span data-ttu-id="73e69-128">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-128">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="73e69-129">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="73e69-129">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="73e69-130">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="73e69-130">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="73e69-131">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-131">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="73e69-132">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-132">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
- <span data-ttu-id="73e69-133">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-133">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
- <span data-ttu-id="73e69-134">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-134">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="73e69-135">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-135">To support Surface Laptop 2, import the following folders:</span></span>

 - <span data-ttu-id="73e69-136">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-136">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
 - <span data-ttu-id="73e69-137">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-137">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
 - <span data-ttu-id="73e69-138">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-138">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
 - <span data-ttu-id="73e69-139">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="73e69-139">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
 - <span data-ttu-id="73e69-140">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="73e69-140">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
 - <span data-ttu-id="73e69-141">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="73e69-141">SurfacePlatformInstaller\Drivers\System\UART</span></span>
 - <span data-ttu-id="73e69-142">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="73e69-142">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

<span data-ttu-id="73e69-143">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="73e69-143">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

- <span data-ttu-id="73e69-144">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-144">SurfaceUpdate\SerialIOGPIO</span></span>
- <span data-ttu-id="73e69-145">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="73e69-145">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="73e69-146">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="73e69-146">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="73e69-147">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="73e69-147">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="73e69-148">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="73e69-148">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="73e69-149">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="73e69-149">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="73e69-150">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-150">SurfaceUpdate\Itouch</span></span>

 
<span data-ttu-id="73e69-151">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-151">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

- <span data-ttu-id="73e69-152">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-152">SurfaceUpdate\IclSerialIOGPIO</span></span>
- <span data-ttu-id="73e69-153">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="73e69-153">SurfaceUpdate\IclSerialIOI2C</span></span>
- <span data-ttu-id="73e69-154">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="73e69-154">SurfaceUpdate\IclSerialIOSPI</span></span>
- <span data-ttu-id="73e69-155">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="73e69-155">SurfaceUpdate\IclSerialIOUART</span></span>
- <span data-ttu-id="73e69-156">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="73e69-156">SurfaceUpdate\SurfaceHidMini</span></span>
- <span data-ttu-id="73e69-157">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="73e69-157">SurfaceUpdate\SurfaceSerialHub</span></span>
- <span data-ttu-id="73e69-158">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="73e69-158">SurfaceUpdate\SurfaceHotPlug</span></span>
- <span data-ttu-id="73e69-159">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-159">SurfaceUpdate\Itouch</span></span>

<span data-ttu-id="73e69-160">L'importazione delle cartelle seguenti consentirà la funzionalità completa di tastiera, trackpad e tocco in PE per Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="73e69-160">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

- <span data-ttu-id="73e69-161">IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-161">IclSerialIOGPIO</span></span>
- <span data-ttu-id="73e69-162">IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="73e69-162">IclSerialIOI2C</span></span>
- <span data-ttu-id="73e69-163">IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="73e69-163">IclSerialIOSPI</span></span>
- <span data-ttu-id="73e69-164">IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="73e69-164">IclSerialIOUART</span></span>
- <span data-ttu-id="73e69-165">iTouch</span><span class="sxs-lookup"><span data-stu-id="73e69-165">itouch</span></span>
- <span data-ttu-id="73e69-166">IclChipset</span><span class="sxs-lookup"><span data-stu-id="73e69-166">IclChipset</span></span>
- <span data-ttu-id="73e69-167">IclChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="73e69-167">IclChipsetLPSS</span></span>
- <span data-ttu-id="73e69-168">IclChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="73e69-168">IclChipsetNorthpeak</span></span>
- <span data-ttu-id="73e69-169">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="73e69-169">ManagementEngine</span></span>
- <span data-ttu-id="73e69-170">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="73e69-170">SurfaceAcpiNotify</span></span>
- <span data-ttu-id="73e69-171">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="73e69-171">SurfaceBattery</span></span>
- <span data-ttu-id="73e69-172">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="73e69-172">SurfaceDockIntegration</span></span>
- <span data-ttu-id="73e69-173">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="73e69-173">SurfaceHidMini</span></span>
- <span data-ttu-id="73e69-174">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="73e69-174">SurfaceHotPlug</span></span>
- <span data-ttu-id="73e69-175">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="73e69-175">SurfaceIntegration</span></span>
- <span data-ttu-id="73e69-176">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="73e69-176">SurfaceSerialHub</span></span>
- <span data-ttu-id="73e69-177">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="73e69-177">SurfaceService</span></span>
- <span data-ttu-id="73e69-178">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="73e69-178">SurfaceStorageFwUpdate</span></span>


    > [!NOTE]
    >  <span data-ttu-id="73e69-179">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="73e69-179">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="73e69-180">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="73e69-180">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="73e69-181">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-181">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="73e69-182">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-182">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="73e69-183">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-183">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="73e69-184">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-184">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="73e69-185">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="73e69-185">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="73e69-186">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="73e69-186">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="73e69-187">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-187">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="73e69-188">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-188">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="73e69-189">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-189">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="73e69-190">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-190">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="73e69-191">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-191">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="73e69-192">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-192">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="73e69-193">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-193">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="73e69-194">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="73e69-194">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="73e69-195">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="73e69-195">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="73e69-196">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="73e69-196">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="73e69-197">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="73e69-197">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="73e69-198">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="73e69-198">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="73e69-199">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="73e69-199">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="73e69-200">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-200">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="73e69-201">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="73e69-201">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="73e69-202">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="73e69-202">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="73e69-203">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="73e69-203">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="73e69-204">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="73e69-204">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="73e69-205">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="73e69-205">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="73e69-206">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-206">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="73e69-207">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="73e69-207">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="73e69-208">SurfaceUpdate\IclSerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="73e69-208">SurfaceUpdate\IclSerialIOGPIO</span></span>
    - <span data-ttu-id="73e69-209">SurfaceUpdate\IclSerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="73e69-209">SurfaceUpdate\IclSerialIOI2C</span></span>
    - <span data-ttu-id="73e69-210">SurfaceUpdate\IclSerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="73e69-210">SurfaceUpdate\IclSerialIOSPI</span></span>
    - <span data-ttu-id="73e69-211">SurfaceUpdate\IclSerialIOUART</span><span class="sxs-lookup"><span data-stu-id="73e69-211">SurfaceUpdate\IclSerialIOUART</span></span>
    - <span data-ttu-id="73e69-212">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="73e69-212">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="73e69-213">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="73e69-213">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="73e69-214">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="73e69-214">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="73e69-215">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="73e69-215">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="73e69-216">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="73e69-216">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="73e69-217">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="73e69-217">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="73e69-218">Verificare che la cartella WindowsPEX64 ora contenga i driver importati.</span><span class="sxs-lookup"><span data-stu-id="73e69-218">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="73e69-219">La cartella dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="73e69-219">The folder should resemble the following:</span></span>  

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="73e69-221">Configurare un profilo di selezione che usa la cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="73e69-221">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="73e69-222">Il profilo di selezione deve essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="73e69-222">The selection profile should resemble the following:</span></span>  

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="73e69-224">Configurare le proprietà di Windows PE della condivisione di distribuzione MDT per usare il nuovo profilo di selezione, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="73e69-224">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="73e69-225">Per la **piattaforma**, selezionare **x64**.</span><span class="sxs-lookup"><span data-stu-id="73e69-225">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="73e69-226">Per il **profilo di selezione**, selezionare il nuovo profilo.</span><span class="sxs-lookup"><span data-stu-id="73e69-226">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="73e69-227">Selezionare **Includi tutti i driver dal profilo di selezione**.</span><span class="sxs-lookup"><span data-stu-id="73e69-227">Select **Include all drivers from the selection profile**.</span></span>
   
   ![Immagine che mostra le proprietà di Windows PE della condivisione di distribuzione MDT](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="73e69-229">Verificare di aver configurato i driver per i portatili della superficie rimanente usando un profilo di selezione o una variabile **DriverGroup001** .</span><span class="sxs-lookup"><span data-stu-id="73e69-229">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="73e69-230">Per laptop Surface (1a generazione), il modello è **laptop Surface**.</span><span class="sxs-lookup"><span data-stu-id="73e69-230">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="73e69-231">I driver portatili di Surface rimanenti dovrebbero risiedere nella cartella di \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface come illustrato nella figura che segue questo elenco.</span><span class="sxs-lookup"><span data-stu-id="73e69-231">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="73e69-232">Per Surface laptop 2, il modello è **Surface laptop 2**.</span><span class="sxs-lookup"><span data-stu-id="73e69-232">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="73e69-233">I driver portatili Surface rimanenti dovrebbero risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 2.</span><span class="sxs-lookup"><span data-stu-id="73e69-233">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="73e69-234">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="73e69-234">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="73e69-235">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="73e69-235">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![Immagine che mostra i driver normali per laptop Surface (1a Gen) nella cartella Surface Laptop di Deployment Workbench](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="73e69-237">Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto in [distribuire un'immagine di Windows 10 con MDT: passaggio 6: creare la sequenza di attività di distribuzione](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span><span class="sxs-lookup"><span data-stu-id="73e69-237">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>

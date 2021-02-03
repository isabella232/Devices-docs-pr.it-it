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
ms.date: 02/02/2021
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: fb51dd3785882e74c90d8b2717e4cc499d492d6f
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312062"
---
# <span data-ttu-id="e341d-104">Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT</span><span class="sxs-lookup"><span data-stu-id="e341d-104">How to enable the Surface Laptop keyboard during MDT deployment</span></span>

<span data-ttu-id="e341d-105">Questo articolo risolve un approccio di distribuzione che usa Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="e341d-105">This article addresses a deployment approach that uses Microsoft Deployment Toolkit (MDT).</span></span> <span data-ttu-id="e341d-106">Puoi anche applicare queste informazioni ad altre metodologie di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e341d-106">You can also apply this information to other deployment methodologies.</span></span> <span data-ttu-id="e341d-107">Nella maggior parte dei tipi di dispositivi Surface la tastiera dovrebbe funzionare durante l'installazione di Lite Touch (LTI).</span><span class="sxs-lookup"><span data-stu-id="e341d-107">On most types of Surface devices, the keyboard should work during Lite Touch Installation (LTI).</span></span> <span data-ttu-id="e341d-108">Tuttavia, Surface laptop richiede alcuni driver aggiuntivi per abilitare la tastiera.</span><span class="sxs-lookup"><span data-stu-id="e341d-108">However, Surface Laptop requires some additional drivers to enable the keyboard.</span></span> <span data-ttu-id="e341d-109">Per i dispositivi portatili Surface (1st Gen) e Surface laptop 2, è necessario preparare la struttura delle cartelle e i profili di selezione che consentono di specificare i driver della tastiera da usare durante la fase di preinstallazione di Windows (Windows PE) di LTI.</span><span class="sxs-lookup"><span data-stu-id="e341d-109">For Surface Laptop (1st Gen) and Surface Laptop 2 devices, you must prepare the folder structure and selection profiles that allow you to specify keyboard drivers for use during the Windows Preinstallation Environment (Windows PE) phase of LTI.</span></span> <span data-ttu-id="e341d-110">Per altre informazioni sulla struttura delle cartelle, vedere [distribuire un'immagine di Windows 10 con MDT: passaggio 5: preparare il repository dei driver](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span><span class="sxs-lookup"><span data-stu-id="e341d-110">For more information about this folder structure, see [Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).</span></span>

> [!TIP]    
> <span data-ttu-id="e341d-111">Quando si usano i driver della tastiera per Surface laptop 2 e Surface laptop 3 nella stessa istanza di avvio di Windows PE, potrebbe essere necessario reimpostare manualmente il firmware se la tastiera o il touchpad non funzionano in Windows PE:</span><span class="sxs-lookup"><span data-stu-id="e341d-111">When using keyboard drivers for Surface Laptop 2 and Surface Laptop 3 in the same Windows PE boot instance, you may need to manually reset the firmware if the keyboard or touchpad don’t work in Windows PE:</span></span>
>
> - <span data-ttu-id="e341d-112">Premere e tenere premuto il pulsante di alimentazione per 30 secondi.</span><span class="sxs-lookup"><span data-stu-id="e341d-112">Press and hold the Power button for 30 seconds.</span></span> <span data-ttu-id="e341d-113">Se si è connessi a un alimentatore (PSU), premere e tenere premuto il pulsante di alimentazione finché non si vede la luce alla fine del cavo PSU brevemente disattivare prima di riattivare l'elemento.</span><span class="sxs-lookup"><span data-stu-id="e341d-113">If you are connected to a power supply unit (PSU), press and hold the Power button until you see the light at the end of the PSU cord briefly turn off before turning back on.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e341d-114">Se si sta distribuendo un'immagine di Windows 10 a un computer portatile Surface con Windows 10 in modalità S preinstallato, vedere KB [4032347, problemi durante la distribuzione di dispositivi Windows in Surface con Windows 10 preinstallato in modalità s](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span><span class="sxs-lookup"><span data-stu-id="e341d-114">If you are deploying a Windows 10 image to a Surface Laptop that has Windows 10 in S mode preinstalled, see KB [4032347, Problems when deploying Windows to Surface devices with preinstalled Windows 10 in S mode](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).</span></span>

<span data-ttu-id="e341d-115">Per aggiungere i driver della tastiera al profilo di selezione, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-115">To add the keyboard drivers to the selection profile, follow these steps:</span></span>

1. <span data-ttu-id="e341d-116">Scaricare il file MSI di Surface laptop più recente dalle posizioni appropriate:</span><span class="sxs-lookup"><span data-stu-id="e341d-116">Download the latest Surface Laptop MSI file from the appropriate locations:</span></span>
    - [<span data-ttu-id="e341d-117">Driver e firmware di Surface laptop (1a Gen)</span><span class="sxs-lookup"><span data-stu-id="e341d-117">Surface Laptop (1st Gen) Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=55489)
    - [<span data-ttu-id="e341d-118">Computer portatile di Surface 2 driver e firmware</span><span class="sxs-lookup"><span data-stu-id="e341d-118">Surface Laptop 2 Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=57515)
    - [<span data-ttu-id="e341d-119">Surface laptop 3 con driver e firmware per processori Intel</span><span class="sxs-lookup"><span data-stu-id="e341d-119">Surface Laptop 3 with Intel Processor Drivers and Firmware</span></span>](https://www.microsoft.com/download/details.aspx?id=100429)

2. <span data-ttu-id="e341d-120">Estrarre il contenuto del file MSI della superficie portatile in una cartella che è possibile individuare facilmente, ad esempio c:\ surface_laptop_drivers).</span><span class="sxs-lookup"><span data-stu-id="e341d-120">Extract the contents of the Surface Laptop MSI file to a folder that you can easily locate (for example, c:\surface_laptop_drivers).</span></span> <span data-ttu-id="e341d-121">Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="e341d-121">To extract the contents, open an elevated Command Prompt window and run the command from the following example:</span></span>

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. <span data-ttu-id="e341d-122">Aprire Deployment Workbench ed espandere il nodo **condivisioni distribuzione** e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64** .</span><span class="sxs-lookup"><span data-stu-id="e341d-122">Open the Deployment Workbench and expand the **Deployment Shares** node and your deployment share, then navigate to the **WindowsPEX64** folder.</span></span>

   ![Immagine che mostra la posizione della cartella WindowsPEX64 in Deployment Workbench](./images/surface-laptop-keyboard-1.png)

4. <span data-ttu-id="e341d-124">Fare clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegliere **Importa driver**.</span><span class="sxs-lookup"><span data-stu-id="e341d-124">Right-click the **WindowsPEX64** folder and select **Import Drivers**.</span></span>

5. <span data-ttu-id="e341d-125">Seguire le istruzioni della procedura guidata Importa driver per importare le cartelle del driver nella cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="e341d-125">Follow the instructions in the Import Driver Wizard to import the driver folders into the WindowsPEX64 folder.</span></span>  

    > [!NOTE]
    >  <span data-ttu-id="e341d-126">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="e341d-126">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="e341d-127">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="e341d-127">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

    <span data-ttu-id="e341d-128">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-128">To support Surface Laptop (1st Gen), import the following folders:</span></span>

     - <span data-ttu-id="e341d-129">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-129">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="e341d-130">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-130">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
     - <span data-ttu-id="e341d-131">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-131">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="e341d-132">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="e341d-132">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="e341d-133">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="e341d-133">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="e341d-134">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-134">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-135">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-135">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="e341d-136">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-136">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="e341d-137">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-137">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="e341d-138">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-138">To support Surface Laptop 2, import the following folders:</span></span>

     - <span data-ttu-id="e341d-139">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-139">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
     - <span data-ttu-id="e341d-140">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-140">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
     - <span data-ttu-id="e341d-141">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-141">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
     - <span data-ttu-id="e341d-142">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="e341d-142">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
     - <span data-ttu-id="e341d-143">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="e341d-143">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
     - <span data-ttu-id="e341d-144">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="e341d-144">SurfacePlatformInstaller\Drivers\System\UART</span></span>
     - <span data-ttu-id="e341d-145">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="e341d-145">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="e341d-146">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="e341d-146">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="e341d-147">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-147">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-148">SurfaceUpdate\serialioi2c</span><span class="sxs-lookup"><span data-stu-id="e341d-148">SurfaceUpdate\serialioi2c</span></span>
    - <span data-ttu-id="e341d-149">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="e341d-149">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="e341d-150">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="e341d-150">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="e341d-151">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="e341d-151">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="e341d-152">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="e341d-152">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="e341d-153">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-153">SurfaceUpdate\Itouch</span></span>

     
    <span data-ttu-id="e341d-154">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-154">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="e341d-155">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-155">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-156">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="e341d-156">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="e341d-157">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="e341d-157">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="e341d-158">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="e341d-158">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="e341d-159">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="e341d-159">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="e341d-160">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="e341d-160">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="e341d-161">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="e341d-161">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="e341d-162">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-162">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="e341d-163">L'importazione delle cartelle seguenti consentirà la funzionalità completa di tastiera, trackpad e tocco in PE per Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e341d-163">Importing the following folders will enable full keyboard, trackpad, and touch functionality in PE for Surface Laptop 3.</span></span>

    - <span data-ttu-id="e341d-164">SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-164">SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-165">SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="e341d-165">SerialIOI2C</span></span>
    - <span data-ttu-id="e341d-166">SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="e341d-166">SerialIOSPI</span></span>
    - <span data-ttu-id="e341d-167">SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="e341d-167">SerialIOUART</span></span>
    - <span data-ttu-id="e341d-168">iTouch</span><span class="sxs-lookup"><span data-stu-id="e341d-168">itouch</span></span>
    - <span data-ttu-id="e341d-169">Chipset</span><span class="sxs-lookup"><span data-stu-id="e341d-169">Chipset</span></span>
    - <span data-ttu-id="e341d-170">ChipsetLPSS</span><span class="sxs-lookup"><span data-stu-id="e341d-170">ChipsetLPSS</span></span>
    - <span data-ttu-id="e341d-171">ChipsetNorthpeak</span><span class="sxs-lookup"><span data-stu-id="e341d-171">ChipsetNorthpeak</span></span>
    - <span data-ttu-id="e341d-172">ManagementEngine</span><span class="sxs-lookup"><span data-stu-id="e341d-172">ManagementEngine</span></span>
    - <span data-ttu-id="e341d-173">SurfaceAcpiNotify</span><span class="sxs-lookup"><span data-stu-id="e341d-173">SurfaceAcpiNotify</span></span>
    - <span data-ttu-id="e341d-174">SurfaceBattery</span><span class="sxs-lookup"><span data-stu-id="e341d-174">SurfaceBattery</span></span>
    - <span data-ttu-id="e341d-175">SurfaceDockIntegration</span><span class="sxs-lookup"><span data-stu-id="e341d-175">SurfaceDockIntegration</span></span>
    - <span data-ttu-id="e341d-176">SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="e341d-176">SurfaceHidMini</span></span>
    - <span data-ttu-id="e341d-177">SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="e341d-177">SurfaceHotPlug</span></span>
    - <span data-ttu-id="e341d-178">SurfaceIntegration</span><span class="sxs-lookup"><span data-stu-id="e341d-178">SurfaceIntegration</span></span>
    - <span data-ttu-id="e341d-179">SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="e341d-179">SurfaceSerialHub</span></span>
    - <span data-ttu-id="e341d-180">SurfaceService</span><span class="sxs-lookup"><span data-stu-id="e341d-180">SurfaceService</span></span>
    - <span data-ttu-id="e341d-181">SurfaceStorageFwUpdate</span><span class="sxs-lookup"><span data-stu-id="e341d-181">SurfaceStorageFwUpdate</span></span>

     > [!NOTE]
     >  <span data-ttu-id="e341d-182">Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.</span><span class="sxs-lookup"><span data-stu-id="e341d-182">Check the downloaded MSI package to determine the format and directory structure.</span></span>  <span data-ttu-id="e341d-183">La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI.</span><span class="sxs-lookup"><span data-stu-id="e341d-183">The directory structure will start with either SurfacePlatformInstaller (older MSI files) or SurfaceUpdate (Newer MSI files) depending on when the MSI was released.</span></span> 

     <span data-ttu-id="e341d-184">Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-184">To support Surface Laptop (1st Gen), import the following folders:</span></span>

    - <span data-ttu-id="e341d-185">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-185">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
    - <span data-ttu-id="e341d-186">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-186">SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="e341d-187">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-187">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="e341d-188">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="e341d-188">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="e341d-189">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="e341d-189">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="e341d-190">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-190">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-191">SurfaceUpdate\SurfaceHidMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-191">SurfaceUpdate\SurfaceHidMiniDriver</span></span>
    - <span data-ttu-id="e341d-192">SurfaceUpdate\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-192">SurfaceUpdate\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="e341d-193">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-193">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="e341d-194">Per supportare Surface laptop 2, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-194">To support Surface Laptop 2, import the following folders:</span></span>

    - <span data-ttu-id="e341d-195">SurfacePlatformInstaller\Drivers\System\GPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-195">SurfacePlatformInstaller\Drivers\System\GPIO</span></span>
    - <span data-ttu-id="e341d-196">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-196">SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver</span></span>
    - <span data-ttu-id="e341d-197">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span><span class="sxs-lookup"><span data-stu-id="e341d-197">SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver</span></span>
    - <span data-ttu-id="e341d-198">SurfacePlatformInstaller\Drivers\System\I2C</span><span class="sxs-lookup"><span data-stu-id="e341d-198">SurfacePlatformInstaller\Drivers\System\I2C</span></span>
    - <span data-ttu-id="e341d-199">SurfacePlatformInstaller\Drivers\System\SPI</span><span class="sxs-lookup"><span data-stu-id="e341d-199">SurfacePlatformInstaller\Drivers\System\SPI</span></span>
    - <span data-ttu-id="e341d-200">SurfacePlatformInstaller\Drivers\System\UART</span><span class="sxs-lookup"><span data-stu-id="e341d-200">SurfacePlatformInstaller\Drivers\System\UART</span></span>
    - <span data-ttu-id="e341d-201">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span><span class="sxs-lookup"><span data-stu-id="e341d-201">SurfacePlatformInstaller\Drivers\System\PreciseTouch</span></span>

    <span data-ttu-id="e341d-202">O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:</span><span class="sxs-lookup"><span data-stu-id="e341d-202">Or for newer MSI files beginning with "SurfaceUpdate", use:</span></span>

    - <span data-ttu-id="e341d-203">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-203">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-204">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="e341d-204">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="e341d-205">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="e341d-205">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="e341d-206">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="e341d-206">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="e341d-207">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="e341d-207">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="e341d-208">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="e341d-208">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="e341d-209">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-209">SurfaceUpdate\Itouch</span></span>

    <span data-ttu-id="e341d-210">Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:</span><span class="sxs-lookup"><span data-stu-id="e341d-210">To support Surface Laptop 3 with Intel Processor, import the following folders:</span></span>

    - <span data-ttu-id="e341d-211">SurfaceUpdate\SerialIOGPIO</span><span class="sxs-lookup"><span data-stu-id="e341d-211">SurfaceUpdate\SerialIOGPIO</span></span>
    - <span data-ttu-id="e341d-212">SurfaceUpdate\SerialIOI2C</span><span class="sxs-lookup"><span data-stu-id="e341d-212">SurfaceUpdate\SerialIOI2C</span></span>
    - <span data-ttu-id="e341d-213">SurfaceUpdate\SerialIOSPI</span><span class="sxs-lookup"><span data-stu-id="e341d-213">SurfaceUpdate\SerialIOSPI</span></span>
    - <span data-ttu-id="e341d-214">SurfaceUpdate\SerialIOUART</span><span class="sxs-lookup"><span data-stu-id="e341d-214">SurfaceUpdate\SerialIOUART</span></span>
    - <span data-ttu-id="e341d-215">SurfaceUpdate\SurfaceHidMini</span><span class="sxs-lookup"><span data-stu-id="e341d-215">SurfaceUpdate\SurfaceHidMini</span></span>
    - <span data-ttu-id="e341d-216">SurfaceUpdate\SurfaceSerialHub</span><span class="sxs-lookup"><span data-stu-id="e341d-216">SurfaceUpdate\SurfaceSerialHub</span></span>
    - <span data-ttu-id="e341d-217">SurfaceUpdate\SurfaceHotPlug</span><span class="sxs-lookup"><span data-stu-id="e341d-217">SurfaceUpdate\SurfaceHotPlug</span></span>
    - <span data-ttu-id="e341d-218">SurfaceUpdate\Itouch</span><span class="sxs-lookup"><span data-stu-id="e341d-218">SurfaceUpdate\Itouch</span></span>

    > [!NOTE]
    > <span data-ttu-id="e341d-219">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e341d-219">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="e341d-220">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e341d-220">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

6. <span data-ttu-id="e341d-221">Verificare che la cartella WindowsPEX64 ora contenga i driver importati.</span><span class="sxs-lookup"><span data-stu-id="e341d-221">Verify that the WindowsPEX64 folder now contains the imported drivers.</span></span> <span data-ttu-id="e341d-222">La cartella dovrebbe essere simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="e341d-222">The folder should resemble the following:</span></span>  

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench](./images/surface-laptop-keyboard-2.png)

7. <span data-ttu-id="e341d-224">Configurare un profilo di selezione che usa la cartella WindowsPEX64.</span><span class="sxs-lookup"><span data-stu-id="e341d-224">Configure a selection profile that uses the WindowsPEX64 folder.</span></span> <span data-ttu-id="e341d-225">Il profilo di selezione deve essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="e341d-225">The selection profile should resemble the following:</span></span>  

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione](./images/surface-laptop-keyboard-3.png)

8. <span data-ttu-id="e341d-227">Configurare le proprietà di Windows PE della condivisione di distribuzione MDT per usare il nuovo profilo di selezione, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="e341d-227">Configure the Windows PE properties of the MDT deployment share to use the new selection profile, as follows:</span></span>  

   - <span data-ttu-id="e341d-228">Per la **piattaforma**, selezionare **x64**.</span><span class="sxs-lookup"><span data-stu-id="e341d-228">For **Platform**, select **x64**.</span></span>
   - <span data-ttu-id="e341d-229">Per il **profilo di selezione**, selezionare il nuovo profilo.</span><span class="sxs-lookup"><span data-stu-id="e341d-229">For **Selection profile**, select the new profile.</span></span>
   - <span data-ttu-id="e341d-230">Selezionare **Includi tutti i driver dal profilo di selezione**.</span><span class="sxs-lookup"><span data-stu-id="e341d-230">Select **Include all drivers from the selection profile**.</span></span>
   
   ![Immagine che mostra le proprietà di Windows PE della condivisione di distribuzione MDT](./images/surface-laptop-keyboard-4.png)

9. <span data-ttu-id="e341d-232">Verificare di aver configurato i driver per i portatili della superficie rimanente usando un profilo di selezione o una variabile **DriverGroup001** .</span><span class="sxs-lookup"><span data-stu-id="e341d-232">Verify that you have configured the remaining Surface Laptop drivers by using either a selection profile or a **DriverGroup001** variable.</span></span>  
   - <span data-ttu-id="e341d-233">Per laptop Surface (1a generazione), il modello è **laptop Surface**.</span><span class="sxs-lookup"><span data-stu-id="e341d-233">For Surface Laptop (1st Gen), the model is **Surface Laptop**.</span></span> <span data-ttu-id="e341d-234">I driver portatili di Surface rimanenti dovrebbero risiedere nella cartella di \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface come illustrato nella figura che segue questo elenco.</span><span class="sxs-lookup"><span data-stu-id="e341d-234">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop folder as shown in the figure that follows this list.</span></span>
   - <span data-ttu-id="e341d-235">Per Surface laptop 2, il modello è **Surface laptop 2**.</span><span class="sxs-lookup"><span data-stu-id="e341d-235">For Surface Laptop 2, the model is **Surface Laptop 2**.</span></span> <span data-ttu-id="e341d-236">I driver portatili Surface rimanenti dovrebbero risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 2.</span><span class="sxs-lookup"><span data-stu-id="e341d-236">The remaining Surface Laptop drivers should reside in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2 folder.</span></span> 
   - <span data-ttu-id="e341d-237">Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e341d-237">For Surface Laptop 3 with Intel processor, the model is Surface Laptop 3.</span></span> <span data-ttu-id="e341d-238">I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e341d-238">The remaining Surface Laptop drivers are located in the \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3 folder.</span></span>

   ![Immagine che mostra i driver normali per laptop Surface (1a Gen) nella cartella Surface Laptop di Deployment Workbench](./images/surface-laptop-keyboard-5.png)

<span data-ttu-id="e341d-240">Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto in [distribuire un'immagine di Windows 10 con MDT: passaggio 6: creare la sequenza di attività di distribuzione](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span><span class="sxs-lookup"><span data-stu-id="e341d-240">After configuring the MDT Deployment Share to use the new selection profile and related settings, continue the deployment process as described in [Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).</span></span>

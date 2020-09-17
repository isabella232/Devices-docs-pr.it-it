---
title: Microsoft Surface Deployment Accelerator (Surface)
description: Microsoft Surface Deployment Accelerator è un meccanismo di distribuzione semplice e rapido che permette di ricreare l'immagine dei dispositivi Surface.
ms.assetid: E7991E90-4AAE-44B6-8822-58BFDE3EADE4
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: distribuire, installare, strumento
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 5/08/2020
ms.openlocfilehash: 3ede7311289dc4bc720735c0142ff3a46fbb69e7
ms.sourcegitcommit: 582c5a79881c58c4f1aa66cfcab46db966ca9f24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016557"
---
# <span data-ttu-id="89f31-104">Microsoft Surface Deployment Accelerator</span><span class="sxs-lookup"><span data-stu-id="89f31-104">Microsoft Surface Deployment Accelerator</span></span>

<span data-ttu-id="89f31-105">Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.</span><span class="sxs-lookup"><span data-stu-id="89f31-105">Microsoft Surface Deployment Accelerator (SDA) automates the creation and configuration of a Microsoft recommended deployment experience by using free Microsoft deployment tools.</span></span>

<span data-ttu-id="89f31-106">Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.</span><span class="sxs-lookup"><span data-stu-id="89f31-106">Redesigned in April 2020 to simplify and automate deployment of Surface images in a corporate environment, the SDA tool allows you to build a “factory-like” Windows image that you can customize to your organizational requirements.</span></span>

<span data-ttu-id="89f31-107">Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione.</span><span class="sxs-lookup"><span data-stu-id="89f31-107">The open source, script-driven SDA tool leverages the Windows Assessment and Deployment Kit (ADK) for Windows 10, facilitating the creation of Windows images (WIM) in test or production environments.</span></span> <span data-ttu-id="89f31-108">Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.</span><span class="sxs-lookup"><span data-stu-id="89f31-108">If the latest ADK is not already installed, it will be downloaded and installed when running the SDA tool.</span></span>

<span data-ttu-id="89f31-109">L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.</span><span class="sxs-lookup"><span data-stu-id="89f31-109">The resulting image closely matches the configuration of Bare Metal Recovery (BMR) images, without any pre-installed applications such as Microsoft Office or the Surface UWP application.</span></span>

## <span data-ttu-id="89f31-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="89f31-110">Requirements</span></span>

1. <span data-ttu-id="89f31-111">Un'unità thumb USB di dimensioni almeno 16 GB.</span><span class="sxs-lookup"><span data-stu-id="89f31-111">A USB thumb drive at least 16 GB in size.</span></span> <span data-ttu-id="89f31-112">L'unità USB verrà formattata.</span><span class="sxs-lookup"><span data-stu-id="89f31-112">The USB drive will be formatted.</span></span>
2. <span data-ttu-id="89f31-113">Un file con estensione ISO con Windows 10 Pro o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="89f31-113">An .iso file with Windows 10 Pro or Windows 10 Enterprise.</span></span> <span data-ttu-id="89f31-114">Lo strumento per la creazione di elementi multimediali può essere usato per scaricare Windows 10 e creare un file ISO.</span><span class="sxs-lookup"><span data-stu-id="89f31-114">The media creation tool can be used to download Windows 10 and create an .iso file.</span></span> <span data-ttu-id="89f31-115">Per altre informazioni, vedere [scaricare Windows 10](https://www.microsoft.com/software-download/windows10).</span><span class="sxs-lookup"><span data-stu-id="89f31-115">For more information, see [Download Windows 10](https://www.microsoft.com/software-download/windows10).</span></span>
3. <span data-ttu-id="89f31-116">Dispositivo che utilizza Windows 10, versione 2004 o successiva con accesso a Internet.</span><span class="sxs-lookup"><span data-stu-id="89f31-116">A device running Windows 10, version 2004 or later with Internet access.</span></span>

<span data-ttu-id="89f31-117">Vedere la sezione [prerequisiti](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) del documento README per un elenco dettagliato dei requisiti.</span><span class="sxs-lookup"><span data-stu-id="89f31-117">See the [Prerequisites](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) section of the README document for a detailed list of requirements.</span></span>

## <span data-ttu-id="89f31-118">Come eseguire l'SDA</span><span class="sxs-lookup"><span data-stu-id="89f31-118">How to run the SDA</span></span>

**<span data-ttu-id="89f31-119">Per eseguire SDA:</span><span class="sxs-lookup"><span data-stu-id="89f31-119">To run SDA:</span></span>**

1. <span data-ttu-id="89f31-120">Accedere a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="89f31-120">Go to [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) on GitHub.</span></span> 
2. <span data-ttu-id="89f31-121">Esaminare la documentazione del [file Leggimi](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) .</span><span class="sxs-lookup"><span data-stu-id="89f31-121">Review the [README](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) documentation.</span></span>
3. <span data-ttu-id="89f31-122">Nella pagina [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) fare clic sul pulsante **codice** e quindi selezionare **Scarica zip** per salvare i file localmente nel computer.</span><span class="sxs-lookup"><span data-stu-id="89f31-122">On the [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) page, click the **Code** button and then select **Download ZIP** to save the files locally on your computer.</span></span>
4. <span data-ttu-id="89f31-123">Fare clic con il pulsante destro del mouse sul file con estensione zip e quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="89f31-123">Right-click the .zip file and then click **Properties**.</span></span>
5. <span data-ttu-id="89f31-124">Nella scheda **generale** selezionare la casella di controllo **Sblocca** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="89f31-124">On the **General** tab, select the **Unblock** checkbox and then click **OK**.</span></span>
6. <span data-ttu-id="89f31-125">Estrarre il file con estensione zip in una posizione nel disco rigido (es: C:\SDA).</span><span class="sxs-lookup"><span data-stu-id="89f31-125">Extract the .zip file to a location on your hard drive (ex: C:\SDA).</span></span>
7. <span data-ttu-id="89f31-126">Aprire un prompt di Windows PowerShell con privilegi elevati e impostare ExecutionPolicy per la sessione corrente su senza restrizioni.</span><span class="sxs-lookup"><span data-stu-id="89f31-126">Open an elevated Windows PowerShell prompt and set ExecutionPolicy for the current session to Unrestricted.</span></span>

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. <span data-ttu-id="89f31-127">Eseguire lo script SDA specificando i parametri per l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="89f31-127">Run the SDA script specifying parameters for your environment.</span></span> <span data-ttu-id="89f31-128">Lo script può essere usato per creare immagini per l'installazione di Windows 10 su un'ampia gamma di dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="89f31-128">The script can be used to create images to install Windows 10 on a variety of Surface devices.</span></span> <span data-ttu-id="89f31-129">Per un elenco completo dei dispositivi supportati, vedere la [Descrizione del parametro di dispositivo](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) nell'articolo Leggimi di SDA.</span><span class="sxs-lookup"><span data-stu-id="89f31-129">For a full list of supported devices, see the [Device parameter description](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) in the SDA README article.</span></span> 

    <span data-ttu-id="89f31-130">Ad esempio, il comando seguente crea un'unità USB avviabile che può essere usata per [installare Windows 10 in Surface Hub 2](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os):</span><span class="sxs-lookup"><span data-stu-id="89f31-130">For example, the following command will create a bootable USB drive that can be used to [install Windows 10 on Surface Hub 2](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os):</span></span>

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```
    <span data-ttu-id="89f31-131">L'output degli script di esempio è inferiore.</span><span class="sxs-lookup"><span data-stu-id="89f31-131">Sample script output is below.</span></span>

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/sda1.png)

    <span data-ttu-id="89f31-133">Lo script richiederà circa 45 minuti per l'esecuzione, ma potrebbe richiedere più tempo a seconda delle risorse disponibili per la CPU e il disco.</span><span class="sxs-lookup"><span data-stu-id="89f31-133">The script will require about 45 minutes to run, but could take longer depending on available CPU and disk resources.</span></span> 

    <span data-ttu-id="89f31-134">Dopo aver creato un'immagine di Windows, lo script ti chiederà di inserire e confermare la lettera dell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="89f31-134">After creating a Windows image, the script will ask you to insert and confirm the drive letter of your USB drive.</span></span> <span data-ttu-id="89f31-135">L'unità USB verrà quindi formattata, configurata come avviabile e file copiati per consentire l'installazione dell'immagine personalizzata di Windows 10 per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="89f31-135">The USB drive will then be formatted, configured as bootable, and files copied to enable installation of the custom Windows 10 image for Surface devices.</span></span>

9. <span data-ttu-id="89f31-136">Inserire l'unità USB nel dispositivo in cui si vuole installare Windows 10 e riavviare per iniziare l'installazione di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89f31-136">Insert the USB drive into the device where you want to install Windows 10 and reboot to begin installing Windows 10.</span></span> <span data-ttu-id="89f31-137">L'avvio USB deve essere abilitato nel BIOS, che può richiedere di disabilitare temporaneamente l'avvio sicuro.</span><span class="sxs-lookup"><span data-stu-id="89f31-137">USB boot must be enabled in BIOS, which can require that you temporarily disable Secure Boot.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89f31-138">L'avvio dall'unità USB inizierà immediatamente l'installazione di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="89f31-138">Booting from the USB drive will immediately begin installing Windows 10.</span></span> <span data-ttu-id="89f31-139">Assicurarsi che il dispositivo sia pronto prima di inserire l'USB e riavviare.</span><span class="sxs-lookup"><span data-stu-id="89f31-139">Ensure that your device is ready before inserting the USB and restarting.</span></span> 

## <span data-ttu-id="89f31-140">Collegamenti correlati</span><span class="sxs-lookup"><span data-stu-id="89f31-140">Related links</span></span>

 - [<span data-ttu-id="89f31-141">Strumento di distribuzione delle immagini open source rilasciato su GitHub</span><span class="sxs-lookup"><span data-stu-id="89f31-141">Open source image deployment tool released on GitHub</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)
 - [<span data-ttu-id="89f31-142">Scaricare e installare Windows ADK</span><span class="sxs-lookup"><span data-stu-id="89f31-142">Download and install the Windows ADK</span></span>](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

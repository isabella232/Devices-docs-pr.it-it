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
ms.openlocfilehash: 0e136bd0a69db7a4c4e5cea7d2c065727dcc8fcc
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016440"
---
# <span data-ttu-id="25ea4-104">Microsoft Surface Deployment Accelerator</span><span class="sxs-lookup"><span data-stu-id="25ea4-104">Microsoft Surface Deployment Accelerator</span></span>

<span data-ttu-id="25ea4-105">Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.</span><span class="sxs-lookup"><span data-stu-id="25ea4-105">Microsoft Surface Deployment Accelerator (SDA) automates the creation and configuration of a Microsoft recommended deployment experience by using free Microsoft deployment tools.</span></span>

<span data-ttu-id="25ea4-106">Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.</span><span class="sxs-lookup"><span data-stu-id="25ea4-106">Redesigned in April 2020 to simplify and automate deployment of Surface images in a corporate environment, the SDA tool allows you to build a “factory-like” Windows image that you can customize to your organizational requirements.</span></span>

<span data-ttu-id="25ea4-107">Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione.</span><span class="sxs-lookup"><span data-stu-id="25ea4-107">The open source, script-driven SDA tool leverages the Windows Assessment and Deployment Kit (ADK) for Windows 10, facilitating the creation of Windows images (WIM) in test or production environments.</span></span> <span data-ttu-id="25ea4-108">Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.</span><span class="sxs-lookup"><span data-stu-id="25ea4-108">If the latest ADK is not already installed, it will be downloaded and installed when running the SDA tool.</span></span>

<span data-ttu-id="25ea4-109">L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.</span><span class="sxs-lookup"><span data-stu-id="25ea4-109">The resulting image closely matches the configuration of Bare Metal Recovery (BMR) images, without any pre-installed applications such as Microsoft Office or the Surface UWP application.</span></span>

## <span data-ttu-id="25ea4-110">Requisiti</span><span class="sxs-lookup"><span data-stu-id="25ea4-110">Requirements</span></span>

1. <span data-ttu-id="25ea4-111">Un'unità thumb USB di dimensioni almeno 16 GB.</span><span class="sxs-lookup"><span data-stu-id="25ea4-111">A USB thumb drive at least 16 GB in size.</span></span> <span data-ttu-id="25ea4-112">L'unità USB verrà formattata.</span><span class="sxs-lookup"><span data-stu-id="25ea4-112">The USB drive will be formatted.</span></span>
2. <span data-ttu-id="25ea4-113">Un file con estensione ISO con Windows 10 Pro o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="25ea4-113">An .iso file with Windows 10 Pro or Windows 10 Enterprise.</span></span> <span data-ttu-id="25ea4-114">Lo strumento per la creazione di elementi multimediali può essere usato per scaricare Windows 10 e creare un file ISO.</span><span class="sxs-lookup"><span data-stu-id="25ea4-114">The media creation tool can be used to download Windows 10 and create an .iso file.</span></span> <span data-ttu-id="25ea4-115">Per altre informazioni, vedere [scaricare Windows 10](https://www.microsoft.com/software-download/windows10).</span><span class="sxs-lookup"><span data-stu-id="25ea4-115">For more information, see [Download Windows 10](https://www.microsoft.com/software-download/windows10).</span></span>

## <span data-ttu-id="25ea4-116">Come eseguire SDA</span><span class="sxs-lookup"><span data-stu-id="25ea4-116">How to run SDA</span></span>

**<span data-ttu-id="25ea4-117">Per eseguire SDA:</span><span class="sxs-lookup"><span data-stu-id="25ea4-117">To run SDA:</span></span>**

1. <span data-ttu-id="25ea4-118">Accedere a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="25ea4-118">Go to [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) on GitHub.</span></span> 
2. <span data-ttu-id="25ea4-119">Esaminare la documentazione del [file Leggimi](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) .</span><span class="sxs-lookup"><span data-stu-id="25ea4-119">Review the [README](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) documentation.</span></span>
3. <span data-ttu-id="25ea4-120">Nella pagina [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) fare clic sul pulsante **codice** e quindi selezionare **Scarica zip** per salvare i file localmente nel computer.</span><span class="sxs-lookup"><span data-stu-id="25ea4-120">On the [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) page, click the **Code** button and then select **Download ZIP** to save the files locally on your computer.</span></span>
4. <span data-ttu-id="25ea4-121">Fare clic con il pulsante destro del mouse sul file con estensione zip e quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="25ea4-121">Right-click the .zip file and then click **Properties**.</span></span>
5. <span data-ttu-id="25ea4-122">Nella scheda **generale** selezionare la casella di controllo **Sblocca** e quindi fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="25ea4-122">On the **General** tab, select the **Unblock** checkbox and then click **OK**.</span></span>
6. <span data-ttu-id="25ea4-123">Estrarre il file con estensione zip in una posizione nel disco rigido (es: C:\SDA).</span><span class="sxs-lookup"><span data-stu-id="25ea4-123">Extract the .zip file to a location on your hard drive (ex: C:\SDA).</span></span>
7. <span data-ttu-id="25ea4-124">Aprire un prompt di Windows PowerShell con privilegi elevati e impostare ExecutionPolicy per la sessione corrente su senza restrizioni.</span><span class="sxs-lookup"><span data-stu-id="25ea4-124">Open an elevated Windows PowerShell prompt and set ExecutionPolicy for the current session to Unrestricted.</span></span>

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. <span data-ttu-id="25ea4-125">Eseguire lo script SDA specificando i parametri per l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="25ea4-125">Run the SDA script specifying parameters for your environment.</span></span> <span data-ttu-id="25ea4-126">Ad esempio, il comando seguente creerà un'unità USB avviabile che può essere usata per installare Windows 10 su un hub Surface 2:</span><span class="sxs-lookup"><span data-stu-id="25ea4-126">For example, the following command will create a bootable USB drive that can be used to install Windows 10 on a Surface Hub 2:</span></span>

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/sda1.png)

    <span data-ttu-id="25ea4-128">Lo script richiederà circa 45 minuti per l'esecuzione, ma potrebbe richiedere più tempo a seconda delle risorse disponibili per la CPU e il disco.</span><span class="sxs-lookup"><span data-stu-id="25ea4-128">The script will require about 45 minutes to run, but could take longer depending on available CPU and disk resources.</span></span> 

    <span data-ttu-id="25ea4-129">Dopo aver creato un'immagine Windows, lo script ti chiederà di confermare la lettera dell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="25ea4-129">After creating a Windows image, the script will ask you to confirm the drive letter of your USB drive.</span></span> <span data-ttu-id="25ea4-130">L'unità USB verrà quindi formattata, configurata come avviabile e file copiati per consentire l'installazione dell'immagine personalizzata di Windows 10 per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="25ea4-130">The USB drive will then be formatted, configured as bootable, and files copied to enable installation of the custom Windows 10 image for Surface devices.</span></span>

9. <span data-ttu-id="25ea4-131">Inserire l'unità USB nel dispositivo in cui si vuole installare Windows 10 e riavviare per iniziare l'installazione di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="25ea4-131">Insert the USB drive into the device where you want to install Windows 10 and reboot to begin installing Windows 10.</span></span> <span data-ttu-id="25ea4-132">L'avvio USB deve essere abilitato nel BIOS, che può richiedere di disabilitare temporaneamente l'avvio sicuro.</span><span class="sxs-lookup"><span data-stu-id="25ea4-132">USB boot must be enabled in BIOS, which can require that you temporarily disable Secure Boot.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25ea4-133">L'avvio dall'unità USB inizierà immediatamente l'installazione di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="25ea4-133">Booting from the USB drive will immediately begin installing Windows 10.</span></span> <span data-ttu-id="25ea4-134">Assicurarsi che il dispositivo sia pronto prima di inserire l'USB e riavviare.</span><span class="sxs-lookup"><span data-stu-id="25ea4-134">Ensure that your device is ready before inserting the USB and restarting.</span></span> 

## <span data-ttu-id="25ea4-135">Collegamenti correlati</span><span class="sxs-lookup"><span data-stu-id="25ea4-135">Related links</span></span>

 - [<span data-ttu-id="25ea4-136">Strumento di distribuzione delle immagini open source rilasciato su GitHub</span><span class="sxs-lookup"><span data-stu-id="25ea4-136">Open source image deployment tool released on GitHub</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [<span data-ttu-id="25ea4-137">Scaricare e installare Windows ADK</span><span class="sxs-lookup"><span data-stu-id="25ea4-137">Download and install the Windows ADK</span></span>](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

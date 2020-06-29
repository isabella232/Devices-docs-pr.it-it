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
ms.openlocfilehash: 32d8fded8c325766f7ab6bbc750ba7fe13e01d70
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832312"
---
# <span data-ttu-id="607fd-104">Microsoft Surface Deployment Accelerator</span><span class="sxs-lookup"><span data-stu-id="607fd-104">Microsoft Surface Deployment Accelerator</span></span>

<span data-ttu-id="607fd-105">Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.</span><span class="sxs-lookup"><span data-stu-id="607fd-105">Microsoft Surface Deployment Accelerator (SDA) automates the creation and configuration of a Microsoft recommended deployment experience by using free Microsoft deployment tools.</span></span>

<span data-ttu-id="607fd-106">Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.</span><span class="sxs-lookup"><span data-stu-id="607fd-106">Redesigned in April 2020 to simplify and automate deployment of Surface images in a corporate environment, the SDA tool allows you to build a “factory-like” Windows image that you can customize to your organizational requirements.</span></span>

<span data-ttu-id="607fd-107">Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione.</span><span class="sxs-lookup"><span data-stu-id="607fd-107">The open source, script-driven SDA tool leverages the Windows Assessment and Deployment Kit (ADK) for Windows 10, facilitating the creation of Windows images (WIM) in test or production environments.</span></span> <span data-ttu-id="607fd-108">Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.</span><span class="sxs-lookup"><span data-stu-id="607fd-108">If the latest ADK is not already installed, it will be downloaded and installed when running the SDA tool.</span></span>

<span data-ttu-id="607fd-109">L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.</span><span class="sxs-lookup"><span data-stu-id="607fd-109">The resulting image closely matches the configuration of Bare Metal Recovery (BMR) images, without any pre-installed applications such as Microsoft Office or the Surface UWP application.</span></span>

**<span data-ttu-id="607fd-110">Per eseguire SDA:</span><span class="sxs-lookup"><span data-stu-id="607fd-110">To run SDA:</span></span>**

1. <span data-ttu-id="607fd-111">Accedere a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) su GitHub.</span><span class="sxs-lookup"><span data-stu-id="607fd-111">Go to [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) on GitHub.</span></span> 
2. <span data-ttu-id="607fd-112">Selezionare **clona o Scarica** e rivedere il file Readme.</span><span class="sxs-lookup"><span data-stu-id="607fd-112">Select **Clone or Download** and review the Readme file.</span></span>
3. <span data-ttu-id="607fd-113">Modificare lo script con le variabili appropriate per l'ambiente, come documentato nel file Leggimi, e rivederlo prima di eseguirlo nell'ambiente di test.</span><span class="sxs-lookup"><span data-stu-id="607fd-113">Edit the script with the appropriate variables for your environment, as documented in the Readme, and review before running it in your test environment.</span></span> 

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/surface-deployment-accelerator.png)

## <span data-ttu-id="607fd-115">Collegamenti correlati</span><span class="sxs-lookup"><span data-stu-id="607fd-115">Related links</span></span>

 - [<span data-ttu-id="607fd-116">Strumento di distribuzione delle immagini open source rilasciato su GitHub</span><span class="sxs-lookup"><span data-stu-id="607fd-116">Open source image deployment tool released on GitHub</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [<span data-ttu-id="607fd-117">Scaricare e installare Windows ADK</span><span class="sxs-lookup"><span data-stu-id="607fd-117">Download and install the Windows ADK</span></span>](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

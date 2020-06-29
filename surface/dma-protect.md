---
title: Protezione DMA superficiale
description: Questo articolo descrive la protezione DMA nei dispositivi Surface compatibili
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 6/10/2020
ms.reviewer: carlol
manager: laurawi
audience: itpro
ms.openlocfilehash: 00994263cd61086ab86996920543a717a63d5078
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832847"
---
# <span data-ttu-id="2a68f-103">Protezione DMA su dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="2a68f-103">DMA Protection on Surface devices</span></span>

<span data-ttu-id="2a68f-104">La protezione DMA (Direct Memory Access) è progettata per limitare potenziali vulnerabilità di sicurezza associate all'uso di SSD rimovibili o dispositivi di archiviazione esterni.</span><span class="sxs-lookup"><span data-stu-id="2a68f-104">Direct Memory Access (DMA) protection is designed to mitigate potential security vulnerabilities associated with using removable SSDs or external storage devices.</span></span> <span data-ttu-id="2a68f-105">I dispositivi Surface più recenti sono dotati di protezione DMA abilitata per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="2a68f-105">Newer Surface devices come with DMA Protection enabled by default.</span></span> <span data-ttu-id="2a68f-106">Questi includono Surface Pro 7, Surface laptop 3 e Surface Pro X.  Per verificare la presenza della funzionalità di protezione DMA nel dispositivo, aprire informazioni di sistema (**Start**  >  **msinfo32.exe**), come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="2a68f-106">These include Surface Pro 7, Surface Laptop 3, and Surface Pro X.  To check the presence of DMA protection feature on your device, open System Information (**Start** > **msinfo32.exe**), as shown in the figure below.</span></span>

![Informazioni di sistema che mostrano la protezione DMA abilitata](images/systeminfodma.png)

<span data-ttu-id="2a68f-108">Se una superficie SSD rimovibile viene manomessa, il dispositivo spegnerà l'alimentazione.</span><span class="sxs-lookup"><span data-stu-id="2a68f-108">If a Surface removable SSD is tampered with, the device will shutoff power.</span></span> <span data-ttu-id="2a68f-109">Il riavvio risultante causa l'eliminazione della memoria da parte di UEFI, per cancellare i dati residui.</span><span class="sxs-lookup"><span data-stu-id="2a68f-109">The resulting reboot causes UEFI to wipe memory, to erase any residual data.</span></span>

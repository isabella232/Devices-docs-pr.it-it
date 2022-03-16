---
title: Protezione DMA del Surface
description: Questo articolo descrive la protezione DMA nei dispositivi Surface compatibili
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 12/01/2021
ms.reviewer: carlol
manager: laurawi
audience: itpro
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: a0f04b4dd089309ad44cab12cf738d8203d1526d
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449499"
---
# <a name="dma-protection-on-surface-devices"></a>Protezione DMA nei dispositivi Surface

La protezione DMA (Direct Memory Access) è progettata per ridurre le potenziali vulnerabilità di sicurezza associate all'utilizzo di SSD rimovibili o di dispositivi di archiviazione esterni. I dispositivi Surface più nuovi sono disponibili con la protezione DMA abilitata per impostazione predefinita. Questi includono Surface Pro 8, Surface Laptop Studio, Surface Go 3, Surface Laptop edizione Standard, Surface Pro 7+, Surface Pro 7, Surface Laptop 3 e Surface Pro  X.  Per verificare la presenza della funzionalità di protezione DMA nel dispositivo, apri System Information (**Start** > **msinfo32.exe**), come illustrato nella figura seguente.

![Informazioni di sistema che mostrano la protezione DMA abilitata.](images/systeminfodma.png)

Se un SSD rimovibile surface viene manomesso, il dispositivo arresterà l'alimentazione. Il riavvio risultante fa sì che UEFI cancelli la memoria, cancellando eventuali dati residui.

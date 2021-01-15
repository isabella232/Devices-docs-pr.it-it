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
ms.date: 1/14/2021
ms.reviewer: carlol
manager: laurawi
audience: itpro
appliesto:
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.openlocfilehash: af5187a2b110804a2dff82291f1d5f912ac61a7b
ms.sourcegitcommit: d4e2a29aa21a911ee55642cd66b4337b89eebdd8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "11270621"
---
# Protezione DMA su dispositivi Surface

La protezione DMA (Direct Memory Access) è progettata per limitare potenziali vulnerabilità di sicurezza associate all'uso di SSD rimovibili o dispositivi di archiviazione esterni. I dispositivi Surface più recenti sono dotati di protezione DMA abilitata per impostazione predefinita. Questi includono Surface Pro 7 +. Surface Pro 7, Surface laptop 3 e Surface Pro X.  Per verificare la presenza della funzionalità di protezione DMA nel dispositivo, aprire informazioni di sistema (**Start**  >  **msinfo32.exe**), come illustrato nella figura seguente.

![Informazioni di sistema che mostrano la protezione DMA abilitata](images/systeminfodma.png)

Se una superficie SSD rimovibile viene manomessa, il dispositivo spegnerà l'alimentazione. Il riavvio risultante causa l'eliminazione della memoria da parte di UEFI, per cancellare i dati residui.

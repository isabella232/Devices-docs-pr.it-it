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
# Protezione DMA su dispositivi Surface

La protezione DMA (Direct Memory Access) è progettata per limitare potenziali vulnerabilità di sicurezza associate all'uso di SSD rimovibili o dispositivi di archiviazione esterni. I dispositivi Surface più recenti sono dotati di protezione DMA abilitata per impostazione predefinita. Questi includono Surface Pro 7, Surface laptop 3 e Surface Pro X.  Per verificare la presenza della funzionalità di protezione DMA nel dispositivo, aprire informazioni di sistema (**Start**  >  **msinfo32.exe**), come illustrato nella figura seguente.

![Informazioni di sistema che mostrano la protezione DMA abilitata](images/systeminfodma.png)

Se una superficie SSD rimovibile viene manomessa, il dispositivo spegnerà l'alimentazione. Il riavvio risultante causa l'eliminazione della memoria da parte di UEFI, per cancellare i dati residui.

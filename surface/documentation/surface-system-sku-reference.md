---
title: Riferimento di superficie SKU di sistema
description: Questo argomento fornisce un riferimento ai nomi di SKU di sistema che puoi usare per determinare rapidamente lo stato del computer di un dispositivo specifico.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 29cd47beb855c9b643fca42d91c7b316c374fcca
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832846"
---
# Riferimento SKU di Surface System
Questo documento fornisce un riferimento ai nomi di SKU di sistema che è possibile usare per determinare rapidamente lo stato del computer di un dispositivo specifico usando PowerShell, WMI e gli strumenti correlati. 

SKU di sistema è una variabile (insieme al modello di sistema e ad altri) archiviata nelle tabelle SMBIOS (System Management BIOS) nel layer UEFI dei dispositivi Surface.  Usare il nome SKU di sistema ogni volta che è necessario distinguere tra dispositivi con lo stesso nome di modello di sistema, ad esempio Surface Pro e Surface Pro con LTE Advanced. 

| **Dispositivo**| **Modello di sistema** | **SKU di sistema**|
| --- | ---| --- |
| Superficie 3 WiFI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE su&T                                           | Surface 3        | Surface_3_US1                    |
| Superficie 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Superficie 3 LTE Nord America                                  | Surface 3        | Surface_3_NAG                    |
| Surface 3 LTE al di fuori del Nord America e T-Mobile in Giappone | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro con LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13inch                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15inch                                        | Surface Book 2   | Surface_Book_1793                |
| Superficie go consumer                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Superficie go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Superficie Go 2                                                 | Superficie Go 2     | Surface_Go_2_1927                |
| Superficie Pro 6 consumer                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Superficie Pro 6 Commercial                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Laptop Surface 2 consumer                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Superficie portatile 2 commerciale                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |

## Uso delle variabili di SKU di sistema 

### PowerShell

     gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 

### System Information
È anche possibile trovare il SKU di sistema e il modello di sistema per un dispositivo in informazioni di sistema. 
- Fare clic su **Avvia**  >   **msinfo32**.  

### WMI
È possibile usare le variabili di SKU di sistema in una condizione WMI per una sequenza di attività in Microsoft Deployment Toolkit (MDT) o Microsoft endpoint Configuration Manager. Ad esempio: 

    - Spazio dei nomi WMI-Root\WMI
    - Query WQL: selezionare * da MS_SystemInformation dove SystemSKU = "Surface_Pro_1796"

 
 
 



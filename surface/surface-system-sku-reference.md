---
title: Riferimento SKU di sistema (superficie)
description: Vedere un riferimento ai nomi dei modelli di sistema e SKU di sistema.
keywords: UEFI, configura, firmware, Secure, SEMM
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 08/04/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 3eb177e976bd99ec245996db8cb22eab639f63cc
ms.sourcegitcommit: c0676329f894135388b6d52f85ee8ac9507a836e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2020
ms.locfileid: "10905673"
---
# Riferimento SKU di sistema

Questo documento fornisce un riferimento ai nomi dei modelli di sistema e SKU di sistema che puoi usare per determinare rapidamente lo stato del computer di un dispositivo specifico usando PowerShell o WMI.

Modello di sistema e SKU di sistema sono variabili archiviate nelle tabelle SMBIOS (System Management BIOS) nel layer UEFI dei dispositivi Surface. Usare il nome SKU di sistema ogni volta che è necessario distinguere tra dispositivi con lo stesso nome di modello di sistema, ad esempio Surface Pro e Surface Pro con LTE Advanced.

| Dispositivo   | Modello di sistema | SKU di sistema       |
| ---------- | ----------- | -------------- |
| Superficie 3 WiFI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE su&T                                           | Surface 3        | Surface_3_US1                    |
| Superficie 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Superficie 3 LTE Nord America                                  | Surface 3        | Surface_3_NAG                    |
| Surface 3 LTE al di fuori del Nord America e Y! mobile in Giappone | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro con LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13 "                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15 "                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13 "                                        | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15 "                                        | Surface Book 3   | Surface_Book_3_1899
| Superficie go LTE Commercial | Vai al sistema | Surface_Go_1825_Commercial |
| Superficie go consumer                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Superficie go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Superficie Go 2                                                 | Superficie Go 2     | Surface_Go_2_1927                |
| Superficie Pro 6 consumer                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Superficie Pro 6 Commercial                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Laptop Surface 2 consumer                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Superficie portatile 2 commerciale                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Pro 7                 | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro X                 | Surface Pro X    | Surface_Pro_X_1876         |
| Superficie portatile 3 13 "Intel | Laptop Surface 3 | Surface_Laptop_3_1867:1868 |
| Superficie portatile 3 15 "Intel | Laptop Surface 3 | Surface_Laptop_3_1872      |
| Superficie portatile 3 15 "AMD   | Laptop Surface 3 | Surface_Laptop_3_1873      | 

## Esempi 

**Recupero dell'USK tramite PowerShell**  
Usare il comando di PowerShell seguente per estrarre le informazioni di SKU di sistema:

 ``` powershell  
gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 
```

**Recupero dell'USK tramite le informazioni di sistema**  
È anche possibile trovare il SKU di sistema e il modello di sistema per un dispositivo in **informazioni di sistema**. A tale scopo, effettua quanto segue:

1. Selezionare **Start**e quindi digitare **msinfo32** nella casella di ricerca.  
1. Selezionare **informazioni di sistema**.

**Uso dell'Usk in una condizione WMI per una sequenza di attività**  
È possibile usare le informazioni di SKU del sistema in Microsoft Deployment Toolkit (MDT) o Microsoft endpoint Configuration Manager come parte di una condizione WMI per una sequenza di attività.

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ``` 

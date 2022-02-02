---
title: Riferimento SKU del sistema Surface
description: Vedi un riferimento ai nomi SKU di sistema e modello di sistema per tutti i dispositivi Surface.
keywords: uefi, configurare, firmware, sicuro, semm, Autopilot
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 01/07/2022
ms.reviewer: carlol
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 4d9b845901734e23c5b83ee47f9d6608f7495b91
ms.sourcegitcommit: e7d95d583429169eb65aae9034eab2347b1f04a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2022
ms.locfileid: "12338509"
---
# <a name="surface-system-sku-reference"></a>Riferimento SKU del sistema Surface

In questo documento viene fornito un riferimento che può essere utilizzato per varie attività IT, ad esempio l'esecuzione di comandi o l'installazione di driver in base ai nomi del modello di dispositivo/SKU. Modello di sistema e SKU di sistema sono variabili archiviate nelle tabelle SMBIOS (System Management BIOS) nel livello UEFI dei dispositivi Surface. Usa il nome SKU di sistema ogni volta che devi distinguere i dispositivi con lo stesso nome del modello di sistema, ad esempio Surface Pro e Surface Pro con LTE Advanced. Gli SKU elencati nella tabella seguente fanno riferimento a dispositivi commerciali, a meno che non siano etichettati come Consumer. 

| Dispositivo   | Modello di sistema | SKU di sistema       |
| ---------- | ----------- | -------------- |
| Surface 3 Wi-FI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE AT&T                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE North America                                  | Surface 3        | Surface_3_NAG                    |
| Surface 3 LTE al di fuori del Nord America e Y!mobile in Giappone | Surface 3        | Surface_3_ROW                    |
| Surface Book 2 13"                                           | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15"                                           | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13"                                           | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15"                                           | Surface Book 3   | Surface_Book_3_1899
| Surface Go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go Consumer                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go LTE Commercial                                    | Surface Go       | Surface_Go_1825_Commercial |
| Surface Go 2 Commercial                                      | Surface Go 2     | Surface_Go_2_1926                |
| Surface Go 2 Consumer                                        | Surface Go 2     | Surface_Go_2_1901                |
| Surface Go 2 LTE                                             | Surface Go 2     | Surface_Go_2_1927                |
| Surface Go 3 Commercial                                      | Surface Go 3     | Surface_Go_3_1926                |
| Surface Go 3 Consumer                                        | Surface Go 3     | Surface_Go_3_1901                |
| Surface Go 3 LTE                                             | Surface Go 3     | Surface_Go_3_2022                |
| Surface Hub 2S 50"                                           | Surface Hub 2S   | Surface Hub 2S                   |
| Surface Hub 2S 85"                                           | Surface Hub 2S   | Surface Hub 2S 85                |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Surface Laptop 2 Commercial                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Laptop 2 Consumer                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface Laptop Intel da 3 13"                                   | Surface Laptop 3 | Surface_Laptop_3_1867:1868 |
| Surface Laptop AMD da 3 15"                                     | Surface Laptop 3 | Surface_Laptop_3_1873      |
| Surface Laptop Intel da 3 15"                                   | Surface Laptop 3 | Surface_Laptop_3_1872      |
| Surface Laptop AMD da 4 13"                                     | Surface Laptop 4 | Surface_Laptop_4_1958:1959    |
| Surface Laptop Intel da 4 13"                                   | Surface Laptop 4 | Surface_Laptop_4_1950:1951 |
| Surface Laptop AMD da 4 15"                                     | Surface Laptop 4 | Surface_Laptop_4_1952:1953     |
| Surface Laptop Intel da 4 15"                                   | Surface Laptop 4 | Surface_Laptop_4_1978:1979     |
| Surface Laptop Go                                            | Surface Laptop Go | Surface_Laptop_Go_1943      |
| Surface Laptop edizione Standard                                            | Surface Laptop edizione Standard | Surface Laptop edizione Standard            |
| Surface Laptop Studio                                        | Surface Laptop Studio | Surface_Laptop_Studio_1964 |
| Surface Pro (5° generazione)                                        | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro con LTE Advanced (5° generazione)                      | Surface Pro      | Surface_Pro_1807                 |
| Surface Pro 6 Commerciale                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Pro 6 Consumer                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 7                                                | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro 7+                                               | Surface Pro 7+   | Surface_Pro_7+_1960|
| Surface Pro 7+ LTE                                           | Surface Pro 7+   | Surface_Pro_7+_with_LTE_Advanced_1961|
| Surface Pro 8                                                | Surface Pro 8    | Surface_Pro_8_for_Business_1983|
| Surface Pro 8 LTE                                            | Surface Pro 8    | Surface_Pro_8_for_Business_with_LTE_Advanced_1982|
| Surface Pro X con processore SQ1                             | Surface Pro X    | Surface_Pro_X_1876         |
| Surface Pro X con processore SQ2                             | Surface Pro X    | Surface_Pro_X_H_1876        |
| Surface Pro X (Wi-Fi)                                        | Surface Pro X    | Surface_Pro_X_2010        |
| Surface Studio                                               | Surface Studio   | Surface_Studio   |
| Surface Studio 2                                             | Surface Studio 2 | Surface_Studio_2_1707_Commercial   |


## <a name="examples"></a>Esempi

**Recupero dello SKU tramite PowerShell**  
Utilizzare il comando di PowerShell seguente per estrarre le informazioni sullo SKU di sistema:

 ``` powershell  
(Get-CimInstance -Namespace root\wmi -ClassName MS_SystemInformation).SystemSKU
```

**Recupero dello SKU tramite System Information**  
Puoi anche trovare la SKU di sistema e il modello di sistema per un dispositivo in **System Information**. A tale scopo, procedi come segue:

1. Selezionare **Start** e quindi digitare **MSInfo32** nella casella di ricerca.  
1. Selezionare **System Information**.

**Utilizzo dello SKU in una condizione WMI della sequenza di attività**  
È possibile utilizzare le informazioni SKU di sistema in Microsoft Deployment Toolkit (MDT) o Microsoft Endpoint Configuration Manager come parte di una condizione WMI della sequenza di attività.

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ```

## <a name="learn-more"></a>Scopri di più

- [Informazioni di riferimento su WMI](/windows/win32/wmisdk/wmi-reference)
- [Supporto alla registrazione di Surface per Windows Autopilot](surface-autopilot-registration-support.md)

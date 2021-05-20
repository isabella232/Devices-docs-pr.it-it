---
title: Riferimento di superficie SKU di sistema
description: Vedi un riferimento ai nomi SKU di sistema e modello di sistema per tutti i dispositivi Surface.
keywords: uefi, configurare, firmware, sicuro, semm, Autopilot
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 04/19/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: bf3fb926c5e66f5f02f921f1c0d4fbe5f016f02d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577046"
---
# <a name="surface-system-sku-reference"></a>Riferimento di superficie SKU di sistema

Questo documento fornisce un riferimento che può essere usato per varie attività IT, ad esempio la registrazione di dispositivi Surface con Windows Autopilot o la verifica dello stato del computer di un dispositivo specifico con PowerShell o WMI.

Modello di sistema e SKU di sistema sono variabili archiviate nelle tabelle SMBIOS (System Management BIOS) nel livello UEFI dei dispositivi Surface. Usa il nome SKU di sistema ogni volta che devi distinguere i dispositivi con lo stesso nome del modello di sistema, ad esempio Surface Pro e Surface Pro con LTE Advanced.

| Dispositivo   | Modello di sistema | SKU di sistema       |
| ---------- | ----------- | -------------- |
| Surface 3 WiFI                                               | Surface 3        | Surface_3                        |
| Surface 3 LTE AT&T                                           | Surface 3        | Surface_3_US1                    |
| Surface 3 LTE Verizon                                        | Surface 3        | Surface_3_US2                    |
| Surface 3 LTE North America                                  | Surface 3        | Surface_3_NAG                    |
| Surface 3 LTE al di fuori del Nord America e Y!mobile in Giappone | Surface 3        | Surface_3_ROW                    |
| Surface Pro                                                  | Surface Pro      | Surface_Pro_1796                 |
| Surface Pro con LTE Advanced                                | Surface Pro      | Surface_Pro_1807                 |
| Surface Book 2 13"                                        | Surface Book 2   | Surface_Book_1832                |
| Surface Book 2 15"                                        | Surface Book 2   | Surface_Book_1793                |
| Surface Book 3 13"                                        | Surface Book 3   | Surface_Book_3_1900                |
| Surface Book 3 15"                                        | Surface Book 3   | Surface_Book_3_1899
| Surface Go LTE Commercial | Sistema Go | Surface_Go_1825_Commercial |
| Surface Go Consumer                                          | Surface Go       | Surface_Go_1824_Consumer         |
| Surface Go Commercial                                        | Surface Go       | Surface_Go_1824_Commercial       |
| Surface Go 2                                                 | Surface Go 2     | Surface_Go_2_1927                |
| Surface Pro 6 Consumer                                       | Surface Pro 6    | Surface_Pro_6_1796_Consumer      |
| Surface Pro 6 Commerciale                                     | Surface Pro 6    | Surface_Pro_6_1796_Commercial    |
| Surface Laptop                                               | Surface Laptop   | Surface_Laptop                   |
| Surface Laptop 2 Consumer                                    | Surface Laptop 2 | Surface_Laptop_2_1769_Consumer   |
| Surface Laptop 2 Commerciale                                  | Surface Laptop 2 | Surface_Laptop_2_1769_Commercial |
| Surface Pro 7+                                               | Surface Pro 7+ | Surface_Pro_7+_1960|
| Surface Pro 7+ LTE                                           | Surface Pro 7+ | Surface_Pro_7+_with_LTE_Advanced_1961|
| Surface Pro 7                 | Surface Pro 7    | Surface_Pro_7_1866         |
| Surface Pro X                 | Surface Pro X    | Surface_Pro_X_1876         |
| Surface Pro X con processore SQ2                | Surface Pro X    | Surface_Pro_X_H_1876        |
| Surface Laptop Intel da 3 13" | Surface Laptop 3 | Surface_Laptop_3_1867:1868 |
| Surface Laptop Intel da 3 15" | Surface Laptop 3 | Surface_Laptop_3_1872      |
| Surface Laptop AMD da 3 15"   | Surface Laptop 3 | Surface_Laptop_3_1873      | 
| Surface Laptop Go  | Surface Laptop Go | Surface_Laptop_Go_1943      | 
| Surface Laptop Intel da 4 13" | Surface Laptop 4 | Surface_Laptop_4_1950:1951 |
| Surface Laptop Intel da 4 15" | Surface Laptop 4 | Surface_Laptop_4_1978:1979     |
| Surface Laptop AMD da 4 15"   | Surface Laptop 4 | Surface_Laptop_4_1952:1953     | 
| Surface Laptop AMD da 4 13"   | Surface Laptop 4 | Surface_Laptop_4_1958:1959    | 
| Surface Hub 2S 50"  | Surface Hub 2S | Surface Hub 2S   | 
| Surface Hub 2S 85"  | Surface Hub 2S | Surface Hub 2S 85   | 

## <a name="examples"></a>Esempi 

**Recupero dello SKU tramite PowerShell**  
Utilizzare il comando di PowerShell seguente per estrarre le informazioni sullo SKU di sistema:

 ``` powershell  
gwmi -namespace root\wmi -class MS_SystemInformation | select SystemSKU 
```

**Recupero dello SKU tramite System Information**  
Puoi anche trovare la SKU di sistema e il modello di sistema per un dispositivo in **System Information**. A tale scopo, procedere come segue:

1. Selezionare **Start**e quindi digitare **MSInfo32** nella casella di ricerca.  
1. Selezionare **System Information**.

**Utilizzo dello SKU in una condizione WMI della sequenza di attività**  
È possibile utilizzare le informazioni SKU di sistema in Microsoft Deployment Toolkit (MDT) o Microsoft Endpoint Configuration Manager come parte di una condizione WMI della sequenza di attività.

 ``` powershell  
    - WMI Namespace – Root\WMI
    - WQL Query – SELECT * FROM MS_SystemInformation WHERE SystemSKU = "Surface_Pro_1796"
 ``` 

## <a name="learn-more"></a>Altre informazioni

- [Informazioni di riferimento su WMI](https://docs.microsoft.com/windows/win32/wmisdk/wmi-reference)
- [Supporto alla registrazione di Surface per Windows Autopilot](surface-autopilot-registration-support.md)

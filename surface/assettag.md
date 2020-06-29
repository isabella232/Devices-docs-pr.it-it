---
title: Strumento Tag Surface asset
description: Questo argomento spiega come usare lo strumento di Surface asset tag.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.openlocfilehash: ca6a71a6b864692953fcd96eb687c2752527c9f5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832577"
---
# Strumento Tag Surface asset

Surface asset tag è un'utilità CLI (Command Line Interface) che consente di visualizzare, assegnare e modificare un valore di tag asset assegnato per i dispositivi Surface. Funziona in Surface Pro 3 e in tutti i dispositivi Surface più recenti.

## Requisiti di sistema

- Surface Pro 3 o versioni successive

- Versione del firmware UEFI 3.9.150.0 o successiva

## Uso di Surface Asset Tag 

Per eseguire il tag Surface asset:

1.  Nel dispositivo Surface scaricare **Surface Asset Tag.zip** dall' [area download Microsoft](https://www.microsoft.com/download/details.aspx?id=46703), estrarre il file zip e salvare AssetTag.exe nella cartella desiderata (in questo esempio C:\\assets).

    > [!NOTE]
    > Per Surface Pro X, usare l'applicazione denominata **AssetTag_x86** nel file zip. 

2.  Aprire una console dei comandi come amministratore ed eseguire AssetTag.exe, immettendo il percorso completo dello strumento.

3.  Riavviare Surface.

### Comandi dello strumento Tag asset   
Negli esempi seguenti AssetTag.exe viene salvato in una directory in un computer locale (C:\assets). 

Per ottenere il tag asset proposto, eseguire AssetTag-g.

**Esempio**

   ```
 C:\assets\AssetTag.exe -g
  ```
 
 Per cancellare il tag asset proposto, eseguire AssetTag-s.
 
 **Esempio**
 
   ```
C:\assets\AssetTag.exe -s
  ```
Per impostare il tag asset proposto, eseguire AssetTag-s testassettag12.

**Esempio**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>Il valore del tag asset deve contenere tra i caratteri 1 e 36. I caratteri validi includono A-Z, a-z, 0-9, punto (.) e segno meno (-).


## Gestione dei tag asset

È possibile visualizzare il tag asset esistente nelle impostazioni UEFI in informazioni dispositivo (**Pannello di controllo > ripristino > avvio avanzato > Riavvia ora**.)

La figura seguente mostra i risultati dell'uso dello strumento Tag asset in Surface go.

![Risultati dello strumento di modifica delle risorse in superficie in Surface go.
](images/assettag-fig1.png)

> **Figura 1.** Risultati dello strumento di modifica della superficie in Surface go

In alternativa, è possibile usare WMI per eseguire query sul tag asset esistente in un dispositivo:

(Get-WmiObject-Query "Select * from Win32_SystemEnclosure")

**Esempio**

   ```
C:\Windows\System32> (Get-WmiObject -query “Select * from Win32_SystemEnclosure”)
  ```
  
### Uso di PowerShell

Puoi usare lo script seguente come strumento per ottenere il valore proposto e interpretare gli eventuali errori.

 ```
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim(“\`r\`n”)

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output (“Good Tag = ” + $asset\_tag)  
} else {  
Write-Output (  
“Failure: Code = ” + $asset\_tag\_return\_code +  
“Tag = ” + $asset\_tag +  
“Message = ” + $error\_message)

}
 ```

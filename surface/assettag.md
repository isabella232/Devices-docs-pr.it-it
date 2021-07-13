---
title: Surface Asset Tag Tool
description: Questo argomento spiega come usare surface Asset Tag Tool.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: carlol
ms.date: 06/29/2021
manager: laurawi
ms.openlocfilehash: b130f6b0bf52dc1c3a28231a2330cae51a5ef44a
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643832"
---
# <a name="surface-asset-tag-tool"></a>Surface Asset Tag Tool

Surface Asset Tag è un'utilità CLI (Command Line Interface) che consente di visualizzare, assegnare e modificare un valore di tag asset assegnato per i dispositivi Surface. Funziona su Surface Pro 3 e tutti i dispositivi Surface più nuovi.

## <a name="system-requirements"></a>Requisiti di sistema

- Surface Pro 3 o versione successiva

- Firmware UEFI versione 3.9.150.0 o successiva

## <a name="using-surface-asset-tag"></a>Uso di Surface Asset Tag

Per eseguire Surface Asset Tag:

1. Nel dispositivo Surface scarica **Surface Asset Tag.zip** dall'Area download [Microsoft,](https://www.microsoft.com/download/details.aspx?id=46703)estrai il file ZIP e salva AssetTag.exe nella cartella desiderata (in questo esempio, C:\\assets).

    > [!NOTE]
    > Per Surface Pro X, usa l'applicazione denominata **AssetTag_x86** nel file ZIP.

2. Aprire una console dei comandi come amministratore ed eseguire AssetTag.exe, immettendo il percorso completo dello strumento.

3. Riavvia Surface.

    > [!NOTE]
    > Dopo aver impostato il tag asset, è necessario un secondo riavvio prima che venga visualizzato in WMI.

### <a name="asset-tag-tool-commands"></a>Comandi dello strumento Tag asset

Negli esempi seguenti la AssetTag.exe viene salvata in una directory in un computer locale (C:\assets).

Per ottenere il tag dell'asset proposto, esegui **AssetTag -g**:

```console
C:\assets\AssetTag.exe -g
```

Per cancellare il tag asset proposto, esegui **AssetTag -s**:

```console
C:\assets\AssetTag.exe -s
```

Per impostare il tag asset proposto, eseguire **AssetTag -s testassettag12**:

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
>Il valore del tag asset deve contenere da 1 a 36 caratteri. I caratteri validi includono A-Z, a-z, 0-9, punto (.) e trattino (-).

## <a name="managing-asset-tags"></a>Gestione dei tag degli asset

Puoi visualizzare il tag asset esistente nelle impostazioni UEFI in Informazioni dispositivo ( Pannello di controllo > Ripristino > Avvio avanzato **> Riavvia ora**.)

La figura seguente mostra i risultati dell'esecuzione di Asset Tag Tool in Surface Go.

![Risultati dell'esecuzione dello strumento Surface Asset Tag in Surface Go.](images/assettag-fig1.png)

> **Figura 1.** Risultati dell'esecuzione dello strumento Surface Asset Tag in Surface Go

In alternativa, è possibile utilizzare WMI per eseguire query sul tag asset esistente in un dispositivo:

(Get-WmiObject -query "Select * from Win32_SystemEnclosure")

### <a name="example"></a>Esempio

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a>Uso di PowerShell

È possibile utilizzare lo script seguente per ottenere il valore proposto e interpretare eventuali errori.

```powershell
AssetTag -g \> $asset\_tag 2\> $error\_message  
$asset\_tag\_return\_code = $LASTEXITCODE  
$asset\_tag = $asset\_tag.Trim("\`r\`n")

if ($asset\_tag\_return\_code -eq 0) {  
Write-Output ("Good Tag = " + $asset\_tag)  
} else {  
Write-Output (  
"Failure: Code = " + $asset\_tag\_return\_code +  
"Tag = " + $asset\_tag +  
"Message = " + $error\_message)

}
```

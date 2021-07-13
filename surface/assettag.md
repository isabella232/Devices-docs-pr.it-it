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
# <a name="surface-asset-tag-tool"></a><span data-ttu-id="64788-103">Surface Asset Tag Tool</span><span class="sxs-lookup"><span data-stu-id="64788-103">Surface Asset Tag Tool</span></span>

<span data-ttu-id="64788-104">Surface Asset Tag è un'utilità CLI (Command Line Interface) che consente di visualizzare, assegnare e modificare un valore di tag asset assegnato per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="64788-104">Surface Asset Tag is a command line interface (CLI) utility that allows you to view, assign, and modify an assigned asset tag value for Surface devices.</span></span> <span data-ttu-id="64788-105">Funziona su Surface Pro 3 e tutti i dispositivi Surface più nuovi.</span><span class="sxs-lookup"><span data-stu-id="64788-105">It works on Surface Pro 3 and all newer Surface devices.</span></span>

## <a name="system-requirements"></a><span data-ttu-id="64788-106">Requisiti di sistema</span><span class="sxs-lookup"><span data-stu-id="64788-106">System requirements</span></span>

- <span data-ttu-id="64788-107">Surface Pro 3 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="64788-107">Surface Pro 3 or later</span></span>

- <span data-ttu-id="64788-108">Firmware UEFI versione 3.9.150.0 o successiva</span><span class="sxs-lookup"><span data-stu-id="64788-108">UEFI firmware version 3.9.150.0 or later</span></span>

## <a name="using-surface-asset-tag"></a><span data-ttu-id="64788-109">Uso di Surface Asset Tag</span><span class="sxs-lookup"><span data-stu-id="64788-109">Using Surface Asset Tag</span></span>

<span data-ttu-id="64788-110">Per eseguire Surface Asset Tag:</span><span class="sxs-lookup"><span data-stu-id="64788-110">To run Surface Asset Tag:</span></span>

1. <span data-ttu-id="64788-111">Nel dispositivo Surface scarica **Surface Asset Tag.zip** dall'Area download [Microsoft,](https://www.microsoft.com/download/details.aspx?id=46703)estrai il file ZIP e salva AssetTag.exe nella cartella desiderata (in questo esempio, C:\\assets).</span><span class="sxs-lookup"><span data-stu-id="64788-111">On the Surface device, download **Surface Asset Tag.zip** from the [Microsoft Download  Center](https://www.microsoft.com/download/details.aspx?id=46703),  extract the zip file, and save AssetTag.exe in desired folder (in  this example, C:\\assets).</span></span>

    > [!NOTE]
    > <span data-ttu-id="64788-112">Per Surface Pro X, usa l'applicazione denominata **AssetTag_x86** nel file ZIP.</span><span class="sxs-lookup"><span data-stu-id="64788-112">For Surface Pro X, use the application named **AssetTag_x86**  in the ZIP file.</span></span>

2. <span data-ttu-id="64788-113">Aprire una console dei comandi come amministratore ed eseguire AssetTag.exe, immettendo il percorso completo dello strumento.</span><span class="sxs-lookup"><span data-stu-id="64788-113">Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.</span></span>

3. <span data-ttu-id="64788-114">Riavvia Surface.</span><span class="sxs-lookup"><span data-stu-id="64788-114">Restart Surface.</span></span>

    > [!NOTE]
    > <span data-ttu-id="64788-115">Dopo aver impostato il tag asset, è necessario un secondo riavvio prima che venga visualizzato in WMI.</span><span class="sxs-lookup"><span data-stu-id="64788-115">After setting the asset tag, a second reboot is required before it appears in WMI.</span></span>

### <a name="asset-tag-tool-commands"></a><span data-ttu-id="64788-116">Comandi dello strumento Tag asset</span><span class="sxs-lookup"><span data-stu-id="64788-116">Asset Tag tool commands</span></span>

<span data-ttu-id="64788-117">Negli esempi seguenti la AssetTag.exe viene salvata in una directory in un computer locale (C:\assets).</span><span class="sxs-lookup"><span data-stu-id="64788-117">In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).</span></span>

<span data-ttu-id="64788-118">Per ottenere il tag dell'asset proposto, esegui **AssetTag -g**:</span><span class="sxs-lookup"><span data-stu-id="64788-118">To get the proposed asset tag, run **AssetTag -g**:</span></span>

```console
C:\assets\AssetTag.exe -g
```

<span data-ttu-id="64788-119">Per cancellare il tag asset proposto, esegui **AssetTag -s**:</span><span class="sxs-lookup"><span data-stu-id="64788-119">To clear the proposed asset tag, run **AssetTag -s**:</span></span>

```console
C:\assets\AssetTag.exe -s
```

<span data-ttu-id="64788-120">Per impostare il tag asset proposto, eseguire **AssetTag -s testassettag12**:</span><span class="sxs-lookup"><span data-stu-id="64788-120">To set the proposed asset tag, run **AssetTag -s testassettag12**:</span></span>

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
><span data-ttu-id="64788-121">Il valore del tag asset deve contenere da 1 a 36 caratteri.</span><span class="sxs-lookup"><span data-stu-id="64788-121">The asset tag value must contain between 1 and 36 characters.</span></span> <span data-ttu-id="64788-122">I caratteri validi includono A-Z, a-z, 0-9, punto (.) e trattino (-).</span><span class="sxs-lookup"><span data-stu-id="64788-122">Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).</span></span>

## <a name="managing-asset-tags"></a><span data-ttu-id="64788-123">Gestione dei tag degli asset</span><span class="sxs-lookup"><span data-stu-id="64788-123">Managing asset tags</span></span>

<span data-ttu-id="64788-124">Puoi visualizzare il tag asset esistente nelle impostazioni UEFI in Informazioni dispositivo ( Pannello di controllo > Ripristino > Avvio avanzato **> Riavvia ora**.)</span><span class="sxs-lookup"><span data-stu-id="64788-124">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span></span>

<span data-ttu-id="64788-125">La figura seguente mostra i risultati dell'esecuzione di Asset Tag Tool in Surface Go.</span><span class="sxs-lookup"><span data-stu-id="64788-125">The figure below shows the results of running the Asset Tag Tool on Surface Go.</span></span>

![Risultati dell'esecuzione dello strumento Surface Asset Tag in Surface Go.](images/assettag-fig1.png)

> **<span data-ttu-id="64788-127&quot;>Figura 1.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;64788-127&quot;>Figure 1.</span></span>** <span data-ttu-id=&quot;64788-128&quot;>Risultati dell'esecuzione dello strumento Surface Asset Tag in Surface Go</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;64788-128&quot;>Results of running Surface Asset Tag tool on Surface Go</span></span>

<span data-ttu-id=&quot;64788-129&quot;>In alternativa, è possibile utilizzare WMI per eseguire query sul tag asset esistente in un dispositivo:</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;64788-129&quot;>Alternately, you can use WMI to query the existing asset tag on a device:</span></span>

<span data-ttu-id=&quot;64788-130&quot;>(Get-WmiObject -query &quot;Select \* from Win32_SystemEnclosure")</span><span class="sxs-lookup"><span data-stu-id="64788-130">(Get-WmiObject -query "Select \* from Win32_SystemEnclosure")</span></span>

### <a name="example"></a><span data-ttu-id="64788-131">Esempio</span><span class="sxs-lookup"><span data-stu-id="64788-131">Example</span></span>

```console
C:\Windows\System32> (Get-WmiObject -query "Select * from Win32_SystemEnclosure")
```
  
### <a name="using-powershell"></a><span data-ttu-id="64788-132">Uso di PowerShell</span><span class="sxs-lookup"><span data-stu-id="64788-132">Using PowerShell</span></span>

<span data-ttu-id="64788-133">È possibile utilizzare lo script seguente per ottenere il valore proposto e interpretare eventuali errori.</span><span class="sxs-lookup"><span data-stu-id="64788-133">You can use the script below as a way of getting the proposed value and interpreting any errors.</span></span>

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

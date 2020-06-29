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
# <span data-ttu-id="c1773-103">Strumento Tag Surface asset</span><span class="sxs-lookup"><span data-stu-id="c1773-103">Surface Asset Tag Tool</span></span>

<span data-ttu-id="c1773-104">Surface asset tag è un'utilità CLI (Command Line Interface) che consente di visualizzare, assegnare e modificare un valore di tag asset assegnato per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="c1773-104">Surface Asset Tag is a command line interface (CLI) utility that allows you to view, assign, and modify an assigned asset tag value for Surface devices.</span></span> <span data-ttu-id="c1773-105">Funziona in Surface Pro 3 e in tutti i dispositivi Surface più recenti.</span><span class="sxs-lookup"><span data-stu-id="c1773-105">It works on Surface Pro 3 and all newer Surface devices.</span></span>

## <span data-ttu-id="c1773-106">Requisiti di sistema</span><span class="sxs-lookup"><span data-stu-id="c1773-106">System requirements</span></span>

- <span data-ttu-id="c1773-107">Surface Pro 3 o versioni successive</span><span class="sxs-lookup"><span data-stu-id="c1773-107">Surface Pro 3 or later</span></span>

- <span data-ttu-id="c1773-108">Versione del firmware UEFI 3.9.150.0 o successiva</span><span class="sxs-lookup"><span data-stu-id="c1773-108">UEFI firmware version 3.9.150.0 or later</span></span>

## <span data-ttu-id="c1773-109">Uso di Surface Asset Tag</span><span class="sxs-lookup"><span data-stu-id="c1773-109">Using Surface Asset Tag</span></span> 

<span data-ttu-id="c1773-110">Per eseguire il tag Surface asset:</span><span class="sxs-lookup"><span data-stu-id="c1773-110">To run Surface Asset Tag:</span></span>

1.  <span data-ttu-id="c1773-111">Nel dispositivo Surface scaricare **Surface Asset Tag.zip** dall' [area download Microsoft](https://www.microsoft.com/download/details.aspx?id=46703), estrarre il file zip e salvare AssetTag.exe nella cartella desiderata (in questo esempio C:\\assets).</span><span class="sxs-lookup"><span data-stu-id="c1773-111">On the Surface device, download **Surface Asset Tag.zip** from the [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=46703), extract the zip file, and save AssetTag.exe in desired folder (in this example, C:\\assets).</span></span>

    > [!NOTE]
    > <span data-ttu-id="c1773-112">Per Surface Pro X, usare l'applicazione denominata **AssetTag_x86** nel file zip.</span><span class="sxs-lookup"><span data-stu-id="c1773-112">For Surface Pro X, use the application named **AssetTag_x86**  in the ZIP file.</span></span> 

2.  <span data-ttu-id="c1773-113">Aprire una console dei comandi come amministratore ed eseguire AssetTag.exe, immettendo il percorso completo dello strumento.</span><span class="sxs-lookup"><span data-stu-id="c1773-113">Open a command console as an Administrator and run AssetTag.exe, entering the full path to the tool.</span></span>

3.  <span data-ttu-id="c1773-114">Riavviare Surface.</span><span class="sxs-lookup"><span data-stu-id="c1773-114">Restart Surface.</span></span>

### <span data-ttu-id="c1773-115">Comandi dello strumento Tag asset</span><span class="sxs-lookup"><span data-stu-id="c1773-115">Asset Tag tool commands</span></span>   
<span data-ttu-id="c1773-116">Negli esempi seguenti AssetTag.exe viene salvato in una directory in un computer locale (C:\assets).</span><span class="sxs-lookup"><span data-stu-id="c1773-116">In the following examples, AssetTag.exe is saved in a directory on a local machine (C:\assets).</span></span> 

<span data-ttu-id="c1773-117">Per ottenere il tag asset proposto, eseguire AssetTag-g.</span><span class="sxs-lookup"><span data-stu-id="c1773-117">To get the proposed asset tag, run AssetTag -g.</span></span>

**<span data-ttu-id="c1773-118">Esempio</span><span class="sxs-lookup"><span data-stu-id="c1773-118">Example</span></span>**

   ```
 C:\assets\AssetTag.exe -g
  ```
 
 <span data-ttu-id="c1773-119">Per cancellare il tag asset proposto, eseguire AssetTag-s.</span><span class="sxs-lookup"><span data-stu-id="c1773-119">To clear the proposed asset tag, run AssetTag -s.</span></span>
 
 **<span data-ttu-id="c1773-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="c1773-120">Example</span></span>**
 
   ```
C:\assets\AssetTag.exe -s
  ```
<span data-ttu-id="c1773-121">Per impostare il tag asset proposto, eseguire AssetTag-s testassettag12.</span><span class="sxs-lookup"><span data-stu-id="c1773-121">To set the proposed asset tag, run AssetTag -s testassettag12.</span></span>

**<span data-ttu-id="c1773-122">Esempio</span><span class="sxs-lookup"><span data-stu-id="c1773-122">Example</span></span>**

```
C:\assets\AssetTag.exe -s testassettag12
```

>[!NOTE]
><span data-ttu-id="c1773-123">Il valore del tag asset deve contenere tra i caratteri 1 e 36.</span><span class="sxs-lookup"><span data-stu-id="c1773-123">The asset tag value must contain between 1 and 36 characters.</span></span> <span data-ttu-id="c1773-124">I caratteri validi includono A-Z, a-z, 0-9, punto (.) e segno meno (-).</span><span class="sxs-lookup"><span data-stu-id="c1773-124">Valid characters include A-Z, a-z, 0-9, period (.) and hyphen (-).</span></span>


## <span data-ttu-id="c1773-125">Gestione dei tag asset</span><span class="sxs-lookup"><span data-stu-id="c1773-125">Managing asset tags</span></span>

<span data-ttu-id="c1773-126">È possibile visualizzare il tag asset esistente nelle impostazioni UEFI in informazioni dispositivo (**Pannello di controllo > ripristino > avvio avanzato > Riavvia ora**.)</span><span class="sxs-lookup"><span data-stu-id="c1773-126">You can view the existing asset tag in the UEFI settings under Device Information (**Control Panel > Recovery > Advanced Startup > Restart now**.)</span></span>

<span data-ttu-id="c1773-127">La figura seguente mostra i risultati dell'uso dello strumento Tag asset in Surface go.</span><span class="sxs-lookup"><span data-stu-id="c1773-127">The figure below shows the results of running the Asset Tag Tool on Surface Go.</span></span>

![<span data-ttu-id="c1773-128">Risultati dello strumento di modifica delle risorse in superficie in Surface go.</span><span class="sxs-lookup"><span data-stu-id="c1773-128">Results of running Surface Asset Tag tool on Surface Go.</span></span>
](images/assettag-fig1.png)

> **<span data-ttu-id="c1773-129">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="c1773-129">Figure 1.</span></span>** <span data-ttu-id="c1773-130">Risultati dello strumento di modifica della superficie in Surface go</span><span class="sxs-lookup"><span data-stu-id="c1773-130">Results of running Surface Asset Tag tool on Surface Go</span></span>

<span data-ttu-id="c1773-131">In alternativa, è possibile usare WMI per eseguire query sul tag asset esistente in un dispositivo:</span><span class="sxs-lookup"><span data-stu-id="c1773-131">Alternately, you can use WMI to query the existing asset tag on a device:</span></span>

<span data-ttu-id="c1773-132">(Get-WmiObject-Query "Select \* from Win32_SystemEnclosure")</span><span class="sxs-lookup"><span data-stu-id="c1773-132">(Get-WmiObject -query “Select \* from Win32_SystemEnclosure”)</span></span>

**<span data-ttu-id="c1773-133">Esempio</span><span class="sxs-lookup"><span data-stu-id="c1773-133">Example</span></span>**

   ```
C:\Windows\System32> (Get-WmiObject -query “Select * from Win32_SystemEnclosure”)
  ```
  
### <span data-ttu-id="c1773-134">Uso di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c1773-134">Using PowerShell</span></span>

<span data-ttu-id="c1773-135">Puoi usare lo script seguente come strumento per ottenere il valore proposto e interpretare gli eventuali errori.</span><span class="sxs-lookup"><span data-stu-id="c1773-135">You can use the script below as a way of getting the proposed value and interpreting any errors.</span></span>

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

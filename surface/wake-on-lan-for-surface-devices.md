---
title: Wake on LAN per Surface Devices (Surface)
description: Informazioni su come usare Wake on LAN per riattivare i dispositivi in remoto per eseguire attività di gestione o manutenzione oppure per abilitare automaticamente le soluzioni di gestione, anche se i dispositivi sono spenti.
keywords: aggiornamento, distribuzione, driver, WOL, Wake-on-LAN
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 760ba75ea7b36238d6de722d38e44a3854073112
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833152"
---
# <span data-ttu-id="e60ef-104">Riattivazione LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="e60ef-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="e60ef-105">I dispositivi Surface che eseguono Windows 10, versione 1607 (nota anche come aggiornamento per l'anniversario di Windows 10) o versioni successive e usano una scheda Ethernet Surface per connettersi a una rete cablata, sono in grado di riattivare la LAN (WOL) dalla modalità standby connessa.</span><span class="sxs-lookup"><span data-stu-id="e60ef-105">Surface devices that run Windows 10, version 1607 (also known as Windows 10 Anniversary Update) or later and use a Surface Ethernet adapter to connect to a wired network, are capable of Wake On LAN (WOL) from Connected Standby.</span></span> <span data-ttu-id="e60ef-106">Con WOL, è possibile riattivare i dispositivi in remoto per eseguire attività di gestione o manutenzione o abilitare automaticamente le soluzioni di gestione, ad esempio Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="e60ef-106">With WOL, you can remotely wake up devices to perform management or maintenance tasks or enable management solutions (such as Microsoft Endpoint Configuration Manager) automatically.</span></span> <span data-ttu-id="e60ef-107">Ad esempio, è possibile distribuire le applicazioni ai dispositivi Surface lasciati ancorati con una docking Surface dock o Surface Pro 3, usando Microsoft endpoint Configuration Manager durante una finestra nel bel mezzo della notte, quando l'ufficio è vuoto.</span><span class="sxs-lookup"><span data-stu-id="e60ef-107">For example, you can deploy applications to Surface devices left docked with a Surface Dock or Surface Pro 3 Docking Station by using Microsoft Endpoint Configuration Manager during a window in the middle of the night, when the office is empty.</span></span>

>[!NOTE]
><span data-ttu-id="e60ef-108">I dispositivi Surface devono essere connessi all'alimentazione CA e in standby connesso (Sleep) per supportare WOL.</span><span class="sxs-lookup"><span data-stu-id="e60ef-108">Surface devices must be connected to AC power and in Connected Standby (Sleep) to support WOL.</span></span> <span data-ttu-id="e60ef-109">Il WOL non è possibile dai dispositivi in ibernazione o spenti.</span><span class="sxs-lookup"><span data-stu-id="e60ef-109">WOL is not possible from devices that are in hibernation or powered off.</span></span>

## <span data-ttu-id="e60ef-110">Dispositivi supportati</span><span class="sxs-lookup"><span data-stu-id="e60ef-110">Supported devices</span></span>

<span data-ttu-id="e60ef-111">I dispositivi seguenti sono supportati per WOL:</span><span class="sxs-lookup"><span data-stu-id="e60ef-111">The following devices are supported for WOL:</span></span>

* <span data-ttu-id="e60ef-112">Scheda Ethernet di Surface</span><span class="sxs-lookup"><span data-stu-id="e60ef-112">Surface Ethernet adapter</span></span>
* <span data-ttu-id="e60ef-113">Surface USB-C per Ethernet e adattatore USB</span><span class="sxs-lookup"><span data-stu-id="e60ef-113">Surface USB-C to Ethernet and USB Adapter</span></span>
* <span data-ttu-id="e60ef-114">Dock Surface</span><span class="sxs-lookup"><span data-stu-id="e60ef-114">Surface Dock</span></span>
* <span data-ttu-id="e60ef-115">Docking station per Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="e60ef-115">Surface Docking Station for Surface Pro 3</span></span>
* <span data-ttu-id="e60ef-116">Surface 3</span><span class="sxs-lookup"><span data-stu-id="e60ef-116">Surface 3</span></span>
* <span data-ttu-id="e60ef-117">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="e60ef-117">Surface Pro 3</span></span>
* <span data-ttu-id="e60ef-118">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="e60ef-118">Surface Pro 4</span></span>
* <span data-ttu-id="e60ef-119">Surface Pro (5a generazione)</span><span class="sxs-lookup"><span data-stu-id="e60ef-119">Surface Pro (5th Gen)</span></span>
* <span data-ttu-id="e60ef-120">Surface Pro (5a generazione) con LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="e60ef-120">Surface Pro (5th Gen) with LTE Advanced</span></span>
* <span data-ttu-id="e60ef-121">Surface Book</span><span class="sxs-lookup"><span data-stu-id="e60ef-121">Surface Book</span></span>
* <span data-ttu-id="e60ef-122">Laptop Surface (1a generazione)</span><span class="sxs-lookup"><span data-stu-id="e60ef-122">Surface Laptop (1st Gen)</span></span>
* <span data-ttu-id="e60ef-123">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="e60ef-123">Surface Pro 6</span></span>
* <span data-ttu-id="e60ef-124">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="e60ef-124">Surface Book 2</span></span>
* <span data-ttu-id="e60ef-125">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="e60ef-125">Surface Laptop 2</span></span>
* <span data-ttu-id="e60ef-126">Surface Go</span><span class="sxs-lookup"><span data-stu-id="e60ef-126">Surface Go</span></span>
* <span data-ttu-id="e60ef-127">Surface Go con LTE Advanced</span><span class="sxs-lookup"><span data-stu-id="e60ef-127">Surface Go with LTE Advanced</span></span>
* <span data-ttu-id="e60ef-128">Surface Studio 2 (vedere le istruzioni di Surface Studio 2)</span><span class="sxs-lookup"><span data-stu-id="e60ef-128">Surface Studio 2 (see Surface Studio 2 instructions below)</span></span>
* <span data-ttu-id="e60ef-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="e60ef-129">Surface Pro 7</span></span>
* <span data-ttu-id="e60ef-130">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="e60ef-130">Surface Laptop 3</span></span>

## <span data-ttu-id="e60ef-131">Driver WOL</span><span class="sxs-lookup"><span data-stu-id="e60ef-131">WOL driver</span></span>

<span data-ttu-id="e60ef-132">Per abilitare il supporto WOL su dispositivi Surface, è necessario un driver specifico per la scheda Ethernet Surface.</span><span class="sxs-lookup"><span data-stu-id="e60ef-132">To enable WOL support on Surface devices, a specific driver for the Surface Ethernet adapter is required.</span></span> <span data-ttu-id="e60ef-133">Questo driver non è incluso nel driver standard e nel pacchetto firmware per i dispositivi Surface: è necessario scaricarlo e installarlo separatamente.</span><span class="sxs-lookup"><span data-stu-id="e60ef-133">This driver is not included in the standard driver and firmware pack for Surface devices – you must download and install it separately.</span></span> <span data-ttu-id="e60ef-134">È possibile scaricare il driver Surface WOL (SurfaceWOL.msi) dalla pagina [strumenti superficie per l'it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e60ef-134">You can download the Surface WOL driver (SurfaceWOL.msi) from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span>

<span data-ttu-id="e60ef-135">Puoi eseguire questo file di Microsoft Windows Installer (con estensione msi) su un dispositivo Surface per installare il driver Surface WOL oppure distribuirlo ai dispositivi Surface con una soluzione di distribuzione dell'applicazione, ad esempio Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="e60ef-135">You can run this Microsoft Windows Installer (.msi) file on a Surface device to install the Surface WOL driver, or you can distribute it to Surface devices with an application deployment solution, such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="e60ef-136">Per includere il driver Surface WOL durante la distribuzione, è possibile installare il file con estensione msi come applicazione durante il processo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e60ef-136">To include the Surface WOL driver during deployment, you can install the .msi file as an application during the deployment process.</span></span> <span data-ttu-id="e60ef-137">È anche possibile estrarre i file del driver di Surface WOL per includerli nel processo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="e60ef-137">You can also extract the Surface WOL driver files to include them in the deployment process.</span></span> <span data-ttu-id="e60ef-138">Ad esempio, è possibile includerli nella condivisione di distribuzione di Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="e60ef-138">For example, you can include them in your Microsoft Deployment Toolkit (MDT) deployment share.</span></span> <span data-ttu-id="e60ef-139">Per altre informazioni sulla distribuzione di Surface con MDT, vedere [distribuire Windows 10 ai dispositivi Surface con Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt).</span><span class="sxs-lookup"><span data-stu-id="e60ef-139">You can read more about Surface deployment with MDT in [Deploy Windows 10 to Surface devices with Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt).</span></span>

> [!NOTE]
> <span data-ttu-id="e60ef-140">Durante l'installazione di SurfaceWOL.msi, la chiave del registro di sistema seguente viene impostata su un valore pari a 1, che consente di identificare facilmente i sistemi in cui è stato installato il driver WOL.</span><span class="sxs-lookup"><span data-stu-id="e60ef-140">During the installation of SurfaceWOL.msi, the following registry key is set to a value of 1, which allows easy identification of systems where the WOL driver has been installed.</span></span> <span data-ttu-id="e60ef-141">Se si è scelto di estrarre e installare questi driver separatamente durante la distribuzione, questa chiave del registro di sistema non verrà configurata e deve essere configurata manualmente o con uno script.</span><span class="sxs-lookup"><span data-stu-id="e60ef-141">If you chose to extract and install these drivers separately during deployment, this registry key will not be configured and must be configured manually or with a script.</span></span>
> 
> **<span data-ttu-id="e60ef-142">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span><span class="sxs-lookup"><span data-stu-id="e60ef-142">HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests</span></span>** 

<span data-ttu-id="e60ef-143">Per estrarre il contenuto di SurfaceWOL.msi, usare l'opzione di installazione amministrativa MSIExec (**/a**), come illustrato nell'esempio seguente, per estrarre il contenuto nella cartella C:\WOL\:</span><span class="sxs-lookup"><span data-stu-id="e60ef-143">To extract the contents of SurfaceWOL.msi, use the MSIExec administrative installation option (**/a**), as shown in the following example, to extract the contents to the C:\WOL\ folder:</span></span>

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## <span data-ttu-id="e60ef-144">Istruzioni di Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="e60ef-144">Surface Studio 2 instructions</span></span>

<span data-ttu-id="e60ef-145">Per abilitare WOL in Surface Studio 2, è necessario usare la procedura seguente</span><span class="sxs-lookup"><span data-stu-id="e60ef-145">To enable WOL on Surface Studio 2, you must use the following procedure</span></span>

1. <span data-ttu-id="e60ef-146">Creare le chiavi del registro di sistema seguenti:</span><span class="sxs-lookup"><span data-stu-id="e60ef-146">Create the following registry keys:</span></span>

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. <span data-ttu-id="e60ef-147">Eseguire il comando seguente</span><span class="sxs-lookup"><span data-stu-id="e60ef-147">Run the following command</span></span>

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```

## <span data-ttu-id="e60ef-148">Uso di Surface WOL</span><span class="sxs-lookup"><span data-stu-id="e60ef-148">Using Surface WOL</span></span>

<span data-ttu-id="e60ef-149">Il driver Surface WOL è conforme allo standard WOL, in cui il dispositivo viene svegliato da una comunicazione di rete speciale nota come pacchetto magico.</span><span class="sxs-lookup"><span data-stu-id="e60ef-149">The Surface WOL driver conforms to the WOL standard, whereby the device is woken by a special network communication known as a magic packet.</span></span> <span data-ttu-id="e60ef-150">Il pacchetto magico è costituito da 6 byte di 255 (o FF in esadecimale) seguiti da 16 ripetizioni dell'indirizzo MAC del computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="e60ef-150">The magic packet consists of 6 bytes of 255 (or FF in hexadecimal) followed by 16 repetitions of the target computer’s MAC address.</span></span> <span data-ttu-id="e60ef-151">Per altre informazioni, vedere il pacchetto Magic e lo standard WOL su [Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet).</span><span class="sxs-lookup"><span data-stu-id="e60ef-151">You can read more about the magic packet and the WOL standard on [Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet).</span></span>

>[!NOTE]
><span data-ttu-id="e60ef-152">Per inviare un pacchetto magico e riattivare un dispositivo tramite WOL, è necessario conoscere l'indirizzo MAC del dispositivo di destinazione e della scheda Ethernet.</span><span class="sxs-lookup"><span data-stu-id="e60ef-152">To send a magic packet and wake up a device by using WOL, you must know the MAC address of the target device and Ethernet adapter.</span></span> <span data-ttu-id="e60ef-153">Poiché il pacchetto magico non usa il protocollo di rete IP, non è possibile usare l'indirizzo IP o il nome DNS del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e60ef-153">Because the magic packet does not use the IP network protocol, it is not possible to use the IP address or DNS name of the device.</span></span>

<span data-ttu-id="e60ef-154">Molte soluzioni di gestione, ad esempio Configuration Manager, includono il supporto predefinito per WOL.</span><span class="sxs-lookup"><span data-stu-id="e60ef-154">Many management solutions, such as Configuration Manager, provide built-in support for WOL.</span></span> <span data-ttu-id="e60ef-155">Sono disponibili anche molte soluzioni, tra cui le app Microsoft Store, i moduli di PowerShell, le applicazioni di terze parti e le soluzioni di gestione di terze parti che consentono di inviare un pacchetto magico per riattivare un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e60ef-155">There are also many solutions, including Microsoft Store apps, PowerShell modules, third-party applications, and third-party management solutions that allow you to send a magic packet to wake up a device.</span></span> <span data-ttu-id="e60ef-156">Ad esempio, puoi usare il [modulo di PowerShell Wake on LAN](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) da TechNet Script Center.</span><span class="sxs-lookup"><span data-stu-id="e60ef-156">For example, you can use the [Wake On LAN PowerShell module](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) from the TechNet Script Center.</span></span> 

>[!NOTE]
><span data-ttu-id="e60ef-157">Dopo che un dispositivo è stato riattivato con un pacchetto magico, il dispositivo tornerà in stato di sospensione se un'applicazione non impedisce attivamente il blocco del sistema o se la chiave del registro di AllowSystemRequiredPowerRequests non è configurata su 1, che consente alle applicazioni di impedire il blocco del sonno.</span><span class="sxs-lookup"><span data-stu-id="e60ef-157">After a device has been woken up with a magic packet, the device will return to sleep if an application is not actively preventing sleep on the system or if the AllowSystemRequiredPowerRequests registry key is not configured to 1, which allows applications to prevent sleep.</span></span> <span data-ttu-id="e60ef-158">Per altre informazioni su questa chiave del registro di sistema, vedere la sezione [driver WOL](#wol-driver) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="e60ef-158">See the [WOL driver](#wol-driver) section of this article for more information about this registry key.</span></span>

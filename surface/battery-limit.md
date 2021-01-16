---
title: Impostazione limite batteria (superficie)
description: Il limite di batteria è un'impostazione UEFI che cambia il modo in cui viene caricata la batteria del dispositivo Surface e può prolungarne la longevità.
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.reviewer: jesko
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
manager: laurawi
audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 8ce1dcfc621a547aca9ca1db322f3ed2ce082728
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271143"
---
# <span data-ttu-id="dc552-103">Impostazione del limite della batteria</span><span class="sxs-lookup"><span data-stu-id="dc552-103">Battery Limit setting</span></span>

<span data-ttu-id="dc552-104">L'opzione limite batteria è un'impostazione UEFI che cambia il modo in cui viene caricata la batteria del dispositivo Surface e può prolungarne la longevità.</span><span class="sxs-lookup"><span data-stu-id="dc552-104">Battery Limit option is a UEFI setting that changes how the Surface device battery is charged and may prolong its longevity.</span></span> <span data-ttu-id="dc552-105">Questa impostazione è consigliata nei casi in cui il dispositivo è continuamente connesso a Power, ad esempio quando i dispositivi sono integrati in soluzioni Kiosk.</span><span class="sxs-lookup"><span data-stu-id="dc552-105">This setting is recommended in  cases  in which the device is continuously connected to power, for example when devices are integrated into kiosk solutions.</span></span>  

## <span data-ttu-id="dc552-106">Funzionamento del limite di batteria</span><span class="sxs-lookup"><span data-stu-id="dc552-106">How Battery Limit works</span></span>

<span data-ttu-id="dc552-107">L'impostazione del dispositivo sul limite della batteria cambia il protocollo per la ricarica della batteria del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="dc552-107">Setting the device on Battery Limit changes the protocol for charging the device battery.</span></span> <span data-ttu-id="dc552-108">Quando il limite della batteria è abilitato, la carica della batteria sarà limitata al 50% della sua capacità massima.</span><span class="sxs-lookup"><span data-stu-id="dc552-108">When Battery Limit is enabled, the battery charge will be limited to 50% of its maximum capacity.</span></span> <span data-ttu-id="dc552-109">Il livello di carica segnalato in Windows rifletterà questo limite.</span><span class="sxs-lookup"><span data-stu-id="dc552-109">The charge level reported in Windows will reflect this limit.</span></span> <span data-ttu-id="dc552-110">Di conseguenza, mostrerà che la batteria viene caricata fino al 50% e non viene applicata oltre questo limite.</span><span class="sxs-lookup"><span data-stu-id="dc552-110">Therefore, it will show that the battery is charged up to 50% and will not charge beyond  this limit.</span></span> <span data-ttu-id="dc552-111">Se si Abilita il limite della batteria mentre il dispositivo supera la carica di 50%, l'icona della batteria mostrerà che il dispositivo è collegato ma si Scarica finché il dispositivo non raggiunge il 50% della capacità massima di carica.</span><span class="sxs-lookup"><span data-stu-id="dc552-111">If you enable Battery Limit while the device is above 50% charge, the Battery icon will show that the device is plugged in but discharging until the device reaches 50% of its maximum charge capacity.</span></span>  

## <span data-ttu-id="dc552-112">Dispositivi supportati</span><span class="sxs-lookup"><span data-stu-id="dc552-112">Supported devices</span></span>

<span data-ttu-id="dc552-113">L'impostazione del limite di batteria UEFI è integrata negli ultimi dispositivi Surface, tra cui Surface Pro 7 +, Surface Pro 7 e Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="dc552-113">The Battery Limit UEFI setting is built into the latest Surface devices including Surface Pro 7+, Surface Pro 7, and Surface Laptop 3.</span></span> <span data-ttu-id="dc552-114">I dispositivi precedenti richiedono un [aggiornamento del firmware UEFI di Surface](manage-surface-driver-and-firmware-updates.md), disponibile tramite Windows Update o tramite il driver MSI e i pacchetti del firmware nel sito di [supporto Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface).</span><span class="sxs-lookup"><span data-stu-id="dc552-114">Earlier devices require a [Surface UEFI firmware update](manage-surface-driver-and-firmware-updates.md), available through Windows Update or via the MSI driver and firmware packages on the [Surface Support site](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface).</span></span> <span data-ttu-id="dc552-115">Selezionare [Abilita "limite batteria" per i dispositivi Surface che devono essere collegati per periodi di tempo prolungati](https://support.microsoft.com/help/4464941) per la specifica versione UEFI di Surface necessaria per ogni dispositivo supportato.</span><span class="sxs-lookup"><span data-stu-id="dc552-115">Check [Enable "Battery Limit" for Surface devices that have to be plugged in for extended periods of time](https://support.microsoft.com/help/4464941) for the specific Surface UEFI version required for each supported device.</span></span> 

## <span data-ttu-id="dc552-116">Abilitazione del limite di batteria in UEFI di Surface (Surface Pro 4 e versioni successive)</span><span class="sxs-lookup"><span data-stu-id="dc552-116">Enabling Battery Limit in Surface UEFI (Surface Pro 4 and later)</span></span>

<span data-ttu-id="dc552-117">L'impostazione del limite di batteria di Surface UEFI può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo).</span><span class="sxs-lookup"><span data-stu-id="dc552-117">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="dc552-118">Scegliere **configurazione di avvio**e quindi, in **Opzioni avanzate**, attivare la **modalità limite batteria** **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="dc552-118">Choose **boot configuration**, and then, under **Advanced Options**, toggle **Enable Battery Limit Mode** to **On**.</span></span>  

![Opzioni avanzate del limite di batteria](images/enable-bl.png) 

## <span data-ttu-id="dc552-120">Abilitazione del limite di batteria in Surface go e Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="dc552-120">Enabling battery limit on Surface Go and Surface Go 2</span></span>
<span data-ttu-id="dc552-121">L'impostazione limite di superficie della batteria può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo).</span><span class="sxs-lookup"><span data-stu-id="dc552-121">The Surface Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="dc552-122">Scegliere **configurazione di avvio**e quindi, in **modalità Kiosk**, posizionare il dispositivo di scorrimento a destra per impostare il limite di batteria su **abilitato**.</span><span class="sxs-lookup"><span data-stu-id="dc552-122">Choose **boot configuration**, and then, under **Kiosk Mode**, move the slider to the right to set Battery Limit to **Enabled**.</span></span>  

![Limite della batteria in modalità Kiosk in Surface go](images/go-batterylimit.png) 

## <span data-ttu-id="dc552-124">Abilitazione del limite di batteria in UEFI di Surface (Surface Pro 3)</span><span class="sxs-lookup"><span data-stu-id="dc552-124">Enabling Battery Limit in Surface UEFI (Surface Pro 3)</span></span>

<span data-ttu-id="dc552-125">L'impostazione del limite di batteria di Surface UEFI può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo).</span><span class="sxs-lookup"><span data-stu-id="dc552-125">The Surface UEFI Battery Limit setting can be configured by booting into Surface UEFI (**Power + Vol Up** when turning on the device).</span></span> <span data-ttu-id="dc552-126">Scegliere la **modalità Kiosk**, selezionare **limite batteria**e quindi scegliere **abilitato**.</span><span class="sxs-lookup"><span data-stu-id="dc552-126">Choose **Kiosk Mode**, select **Battery Limit**, and then choose **Enabled**.</span></span>

![Screenshot delle opzioni avanzate](images/enable-bl-sp3.png) 

![Opzioni avanzate](images/enable-bl-sp3-2.png) 

## <span data-ttu-id="dc552-129">Abilitazione del limite della batteria con gli script di PowerShell per il firmware di Surface Enterprise Management (SEMM) o Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="dc552-129">Enabling Battery Limit using Surface Enterprise Management Mode (SEMM) or Surface Pro 3 firmware PowerShell scripts</span></span>

<span data-ttu-id="dc552-130">Il limite di batteria di Surface UEFI è disponibile anche per la configurazione con i metodi seguenti:</span><span class="sxs-lookup"><span data-stu-id="dc552-130">The Surface UEFI battery limit is also available for configuration via the following methods:</span></span>

- <span data-ttu-id="dc552-131">Surface Pro 4 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="dc552-131">Surface Pro 4 and later</span></span> 
    - [<span data-ttu-id="dc552-132">Microsoft Surface UEFI Configurator</span><span class="sxs-lookup"><span data-stu-id="dc552-132">Microsoft Surface UEFI Configurator</span></span>](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - <span data-ttu-id="dc552-133">Script di PowerShell di Surface UEFI Manager (SEMM_Powershell.zip) negli [strumenti Surface per i download](https://www.microsoft.com/download/details.aspx?id=46703)</span><span class="sxs-lookup"><span data-stu-id="dc552-133">Surface UEFI Manager Powershell scripts (SEMM_Powershell.zip) in the [Surface Tools for IT downloads](https://www.microsoft.com/download/details.aspx?id=46703)</span></span>
- <span data-ttu-id="dc552-134">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="dc552-134">Surface Pro 3</span></span> 
    - [<span data-ttu-id="dc552-135">SP3_Firmware_Powershell_Scripts.zip</span><span class="sxs-lookup"><span data-stu-id="dc552-135">SP3_Firmware_Powershell_Scripts.zip</span></span>](https://www.microsoft.com/download/details.aspx?id=46703)

### <span data-ttu-id="dc552-136">Uso di Microsoft Surface UEFI Configurator</span><span class="sxs-lookup"><span data-stu-id="dc552-136">Using Microsoft Surface UEFI Configurator</span></span>

<span data-ttu-id="dc552-137">Per configurare la modalità limite batteria, impostare l'impostazione **sostituzioni Kiosk** nella pagina configurazione **Impostazioni avanzate** in SEMM (Surface Pro 4 e versioni successive).</span><span class="sxs-lookup"><span data-stu-id="dc552-137">To configure Battery Limit mode, set the **Kiosk Overrides** setting on the **Advanced Settings** configuration page in SEMM (Surface Pro 4 and later).</span></span>

![Screenshot delle impostazioni avanzate](images/semm-bl.png)

### <span data-ttu-id="dc552-139">Usare gli script di PowerShell di Surface UEFI Manager</span><span class="sxs-lookup"><span data-stu-id="dc552-139">Using Surface UEFI Manager PowerShell scripts</span></span>

<span data-ttu-id="dc552-140">La caratteristica limite batteria viene controllata con l'impostazione seguente:</span><span class="sxs-lookup"><span data-stu-id="dc552-140">The battery limit feature is controlled via the following setting:</span></span>  

`407 = Battery Profile`

<span data-ttu-id="dc552-141">**Descrizione**: schema di gestione attiva per il modello di utilizzo della batteria</span><span class="sxs-lookup"><span data-stu-id="dc552-141">**Description**:  Active management scheme for battery usage pattern</span></span>

<span data-ttu-id="dc552-142">**Impostazione predefinita**:</span><span class="sxs-lookup"><span data-stu-id="dc552-142">**Default**:</span></span>  `0` 

<span data-ttu-id="dc552-143">Impostare questo valore su `1` per abilitare il limite di batteria.</span><span class="sxs-lookup"><span data-stu-id="dc552-143">Set this to `1` to enable Battery Limit.</span></span>

### <span data-ttu-id="dc552-144">Uso di strumenti firmware di Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="dc552-144">Using Surface Pro 3 firmware tools</span></span>

<span data-ttu-id="dc552-145">La caratteristica limite batteria viene controllata con l'impostazione seguente:</span><span class="sxs-lookup"><span data-stu-id="dc552-145">The battery limit feature is controlled via the following setting:</span></span>  

<span data-ttu-id="dc552-146">**Nome**: BatteryLimitEnable</span><span class="sxs-lookup"><span data-stu-id="dc552-146">**Name**: BatteryLimitEnable</span></span>

<span data-ttu-id="dc552-147">**Descrizione**: BatteryLimit</span><span class="sxs-lookup"><span data-stu-id="dc552-147">**Description**:  BatteryLimit</span></span>

<span data-ttu-id="dc552-148">**Valore corrente**:</span><span class="sxs-lookup"><span data-stu-id="dc552-148">**Current Value**:</span></span>  `0` 

<span data-ttu-id="dc552-149">**Valore predefinito**:</span><span class="sxs-lookup"><span data-stu-id="dc552-149">**Default Value**:</span></span> `0`

<span data-ttu-id="dc552-150">**Valore proposto**:</span><span class="sxs-lookup"><span data-stu-id="dc552-150">**Proposed Value**:</span></span> `0` 

<span data-ttu-id="dc552-151">Impostare questo valore su `1` per abilitare il limite di batteria.</span><span class="sxs-lookup"><span data-stu-id="dc552-151">Set this to `1` to enable Battery Limit.</span></span>

>[!NOTE]
><span data-ttu-id="dc552-152">Per configurare questa impostazione, è necessario usare [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="dc552-152">To configure this setting, you must use [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703).</span></span> 


---
title: Riattivazione LAN per i dispositivi Surface
description: Scopri come puoi usare riattivazione LAN per riattivare in remoto i dispositivi per eseguire automaticamente le attività di gestione.
keywords: aggiornare, distribuire, driver, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.date: 6/04/2021
ms.openlocfilehash: 83989461ca557d27740252149418056688774d3f
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613801"
---
# <a name="wake-on-lan-for-surface-devices"></a><span data-ttu-id="9f6fe-104">Riattivazione LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="9f6fe-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="9f6fe-105">Per mantenere i dispositivi completamente aggiornati, gli amministratori IT devono essere in grado di gestire i dispositivi quando non sono in uso, in genere durante le finestre di manutenzione notturne.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="9f6fe-106">Wake on LAN (WOL) consente agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione con Microsoft Endpoint Manager o soluzioni di terze parti.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-106">Wake on LAN (WOL) enables admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or third-party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="9f6fe-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="9f6fe-107">Requirements</span></span>

<span data-ttu-id="9f6fe-108">I dispositivi devono essere connessi all'alimentazione CA e disporre di una connessione cablata con una delle seguenti schede Ethernet compatibili:</span><span class="sxs-lookup"><span data-stu-id="9f6fe-108">Devices must be connected to AC power and have a wired connection with one of the following compatible Ethernet adapters:</span></span>

- <span data-ttu-id="9f6fe-109">Scheda Ethernet Surface USB 3.0 Gigabit</span><span class="sxs-lookup"><span data-stu-id="9f6fe-109">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>
- <span data-ttu-id="9f6fe-110">Scheda Surface Ethernet</span><span class="sxs-lookup"><span data-stu-id="9f6fe-110">Surface Ethernet Adapter</span></span>
- <span data-ttu-id="9f6fe-111">Surface USB-C to Ethernet and USB Adapter</span><span class="sxs-lookup"><span data-stu-id="9f6fe-111">Surface USB-C to Ethernet and USB Adapter</span></span>
- <span data-ttu-id="9f6fe-112">Hub adattatore da viaggio USB-C Microsoft</span><span class="sxs-lookup"><span data-stu-id="9f6fe-112">Microsoft USB-C Travel Adapter Hub</span></span>
- <span data-ttu-id="9f6fe-113">Dock Surface</span><span class="sxs-lookup"><span data-stu-id="9f6fe-113">Surface Dock</span></span>
- <span data-ttu-id="9f6fe-114">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="9f6fe-114">Surface Dock 2</span></span>

> [!NOTE]
> <span data-ttu-id="9f6fe-115">Surface Dock 2 offre il miglior supporto per Wake on LAN senza la necessità di ulteriori configurazioni IT.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-115">Surface Dock 2 provides the best support for Wake on LAN without the need for any additional IT configuration.</span></span> <span data-ttu-id="9f6fe-116">Per altre informazioni, vedi [Wake on LAN per Surface Dock 2](wake-on-lan-surface-dock2.md)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-116">To learn more, see [Wake on LAN for Surface Dock 2](wake-on-lan-surface-dock2.md)</span></span>

## <a name="how-it-works"></a><span data-ttu-id="9f6fe-117">Come funziona</span><span class="sxs-lookup"><span data-stu-id="9f6fe-117">How it works</span></span>

<span data-ttu-id="9f6fe-118">Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-118">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="9f6fe-119">Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-119">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="9f6fe-120">Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e app Microsoft Store di terze parti, forniscono il supporto incorporato per WOL.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-120">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span> <span data-ttu-id="9f6fe-121">Per ulteriori informazioni sui dispositivi di attivazione con Endpoint Configuration Manager, vedere [Configure Wake on LAN - Configuration Manager.](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-121">To learn more about waking devices with Endpoint Configuration Manager, see [Configure Wake on LAN - Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan).</span></span>

<span data-ttu-id="9f6fe-122">Il supporto per Wake on LAN varia a seconda dello stato di sospensione: Standby connesso o Ibernazione (stato di alimentazione S4).</span><span class="sxs-lookup"><span data-stu-id="9f6fe-122">Support for Wake on LAN varies depending on sleep state:  Connected Standby or Hibernation (S4 power state).</span></span>

## <a name="connected-standby"></a><span data-ttu-id="9f6fe-123">Standby connesso</span><span class="sxs-lookup"><span data-stu-id="9f6fe-123">Connected Standby</span></span>

<span data-ttu-id="9f6fe-124">Per impostazione predefinita, Windows 10 supporta Wake on LAN per i dispositivi Surface in Standby connesso.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-124">By default, Windows 10 supports Wake on LAN for Surface devices in Connected Standby.</span></span>

### <a name="supported-surface-devices---connected-standby"></a><span data-ttu-id="9f6fe-125">Dispositivi Surface supportati - Standby connesso</span><span class="sxs-lookup"><span data-stu-id="9f6fe-125">Supported Surface devices - Connected Standby</span></span>

- <span data-ttu-id="9f6fe-126">Surface Laptop 4 (solo processori Intel)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-126">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="9f6fe-127">Surface Laptop 3 (solo processori Intel)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-127">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="9f6fe-128">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="9f6fe-128">Surface Pro 7+</span></span>
- <span data-ttu-id="9f6fe-129">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="9f6fe-129">Surface Pro 7</span></span>
- <span data-ttu-id="9f6fe-130">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="9f6fe-130">Surface Pro X</span></span>
- <span data-ttu-id="9f6fe-131">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="9f6fe-131">Surface Go 2</span></span>
- <span data-ttu-id="9f6fe-132">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="9f6fe-132">Surface Laptop Go</span></span>
- <span data-ttu-id="9f6fe-133">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="9f6fe-133">Surface Book 3</span></span>

## <a name="hibernation"></a><span data-ttu-id="9f6fe-134">Ibernazione</span><span class="sxs-lookup"><span data-stu-id="9f6fe-134">Hibernation</span></span>

<span data-ttu-id="9f6fe-135">Per riattivare i dispositivi dall'ibernazione è necessario abilitare un'impostazione dei criteri UEFI tramite la modalità di gestione di [Surface Enterprise](surface-enterprise-management-mode.md) (SEMM) (non necessaria per i dispositivi connessi a Surface Dock 2).</span><span class="sxs-lookup"><span data-stu-id="9f6fe-135">To wake devices out of Hibernation requires enabling a UEFI policy setting via [Surface Enterprise Management Mode](surface-enterprise-management-mode.md) (SEMM) (not required for devices connected to Surface Dock 2).</span></span>

### <a name="supported-surface-devices---hibernation"></a><span data-ttu-id="9f6fe-136">Dispositivi Surface supportati - Ibernazione</span><span class="sxs-lookup"><span data-stu-id="9f6fe-136">Supported Surface devices - Hibernation</span></span>

- <span data-ttu-id="9f6fe-137">Surface Laptop 4 (solo processori Intel)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-137">Surface Laptop 4 (Intel processors only)</span></span>
- <span data-ttu-id="9f6fe-138">Surface Laptop 3 (solo processori Intel)</span><span class="sxs-lookup"><span data-stu-id="9f6fe-138">Surface Laptop 3 (Intel processors only)</span></span>
- <span data-ttu-id="9f6fe-139">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="9f6fe-139">Surface Pro 7+</span></span>
- <span data-ttu-id="9f6fe-140">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="9f6fe-140">Surface Pro 7</span></span>
- <span data-ttu-id="9f6fe-141">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="9f6fe-141">Surface Laptop Go</span></span>
- <span data-ttu-id="9f6fe-142">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="9f6fe-142">Surface Book 3</span></span>

### <a name="to-enable-wake-on-lan-uefi-setting"></a><span data-ttu-id="9f6fe-143">Per abilitare l'impostazione UEFI Wake on LAN</span><span class="sxs-lookup"><span data-stu-id="9f6fe-143">To enable Wake on LAN UEFI setting</span></span>

<span data-ttu-id="9f6fe-144">Per abilitare l'impostazione UEFI Wake on LAN, devi registrare i dispositivi di destinazione in SEMM, creare un pacchetto di configurazione e applicare il pacchetto ai dispositivi.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-144">To enable the Wake on LAN UEFI setting you need to enroll target devices into SEMM, create a configuration package, and apply the package to the devices.</span></span> <span data-ttu-id="9f6fe-145">Per ulteriori informazioni, fai riferimento a:</span><span class="sxs-lookup"><span data-stu-id="9f6fe-145">For more information, refer to:</span></span>

- [<span data-ttu-id="9f6fe-146">Surface Enterprise Management Mode</span><span class="sxs-lookup"><span data-stu-id="9f6fe-146">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="9f6fe-147">Registrare e configurare i dispositivi Surface con SEMM</span><span class="sxs-lookup"><span data-stu-id="9f6fe-147">Enroll and configure Surface devices with SEMM</span></span>](enroll-and-configure-surface-devices-with-semm.md)

1. <span data-ttu-id="9f6fe-148">Scaricare e installare [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="9f6fe-148">Download and install [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>
2. <span data-ttu-id="9f6fe-149">Selezionare **Start**  >  **Configuration Package**  >  **Create**+ Certificate  > **Protection**.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-149">Select **Start** > **Configuration Package** > **Create** >**+ Certificate Protection**.</span></span>
3. <span data-ttu-id="9f6fe-150">Passare a **Impostazioni avanzate e** impostare Wake on **LAN** su **On.**</span><span class="sxs-lookup"><span data-stu-id="9f6fe-150">Go to **Advanced settings** and switch **Wake on LAN** to **On**.</span></span>
4. <span data-ttu-id="9f6fe-151">Applica il pacchetto ai dispositivi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="9f6fe-151">Apply the package to target devices.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Abilita l'impostazione dei criteri UEFI wake on LAN](images/wol-uefi.png)

## <a name="learn-more"></a><span data-ttu-id="9f6fe-153">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="9f6fe-153">Learn more</span></span>

- [<span data-ttu-id="9f6fe-154">Wake on LAN per Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="9f6fe-154">Wake on LAN for Surface Dock 2</span></span>](wake-on-lan-surface-dock2.md)
- [<span data-ttu-id="9f6fe-155">Da MICROSOFT Surface USB-C a Ethernet e adattatore USB</span><span class="sxs-lookup"><span data-stu-id="9f6fe-155">Microsoft Surface USB-C to Ethernet and USB Adapter</span></span>](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)
- [<span data-ttu-id="9f6fe-156">Scheda Ethernet Surface USB 3.0 Gigabit</span><span class="sxs-lookup"><span data-stu-id="9f6fe-156">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)

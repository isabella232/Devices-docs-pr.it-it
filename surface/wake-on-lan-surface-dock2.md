---
title: Riattivazione LAN con Surface Dock 2
description: Surface Dock 2 offre il supporto migliore per Wake on LAN (WOL) che consente agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente le attività di gestione.
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
ms.date: 7/02/2021
ms.openlocfilehash: 4a74efb8af776e9805ad3148ea656f0a65d5d09c
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643852"
---
# <a name="wake-on-lan-with-surface-dock-2"></a><span data-ttu-id="fd6fb-104">Riattivazione LAN con Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="fd6fb-104">Wake On LAN with Surface Dock 2</span></span>

<span data-ttu-id="fd6fb-105">Per mantenere i dispositivi completamente aggiornati, gli amministratori IT devono essere in grado di gestire i dispositivi quando non sono in uso, in genere durante le finestre di manutenzione notturne.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-105">To keep devices fully up to date, IT admins need to be able to manage devices when they’re not in use, typically during nightly maintenance windows.</span></span> <span data-ttu-id="fd6fb-106">Surface Dock 2 offre il supporto migliore per Wake on LAN (WOL) consentendo agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione con Microsoft Endpoint Manager o altre soluzioni di terze parti.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-106">Surface Dock 2 provides the best support for Wake on LAN (WOL) enabling admins to remotely wake up devices and automatically perform management tasks with Microsoft Endpoint Manager or other third party solutions.</span></span>

## <a name="requirements"></a><span data-ttu-id="fd6fb-107">Requisiti</span><span class="sxs-lookup"><span data-stu-id="fd6fb-107">Requirements</span></span>

<span data-ttu-id="fd6fb-108">I dispositivi devono avere una connessione cablata con Surface Dock 2 e rimanere connessi all'alimentazione CA.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-108">Devices must have a wired connection with Surface Dock 2 and stay connected to AC Power.</span></span>

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a><span data-ttu-id="fd6fb-110">Dispositivi Surface supportati</span><span class="sxs-lookup"><span data-stu-id="fd6fb-110">Supported Surface devices</span></span>

- <span data-ttu-id="fd6fb-111">Surface Laptop 4 (processori Intel)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-111">Surface Laptop 4 (Intel processors)</span></span>
- <span data-ttu-id="fd6fb-112">Surface Laptop 4 (processori AMD)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-112">Surface Laptop 4 (AMD processors)</span></span>
- <span data-ttu-id="fd6fb-113">Surface Laptop 3 (processori Intel)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-113">Surface Laptop 3 (Intel processors)</span></span>
- <span data-ttu-id="fd6fb-114">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="fd6fb-114">Surface Pro 7+</span></span>
- <span data-ttu-id="fd6fb-115">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="fd6fb-115">Surface Pro 7</span></span>
- <span data-ttu-id="fd6fb-116">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="fd6fb-116">Surface Pro X</span></span>
- <span data-ttu-id="fd6fb-117">Surface Go 2</span><span class="sxs-lookup"><span data-stu-id="fd6fb-117">Surface Go 2</span></span>
- <span data-ttu-id="fd6fb-118">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="fd6fb-118">Surface Laptop Go</span></span>
- <span data-ttu-id="fd6fb-119">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="fd6fb-119">Surface Book 3</span></span>

<span data-ttu-id="fd6fb-120">Surface Dock 2 fornisce il supporto WOL per i dispositivi nei seguenti stati di alimentazione:</span><span class="sxs-lookup"><span data-stu-id="fd6fb-120">Surface Dock 2 provides WOL support for devices in the following power states:</span></span>

- <span data-ttu-id="fd6fb-121">Standby connesso</span><span class="sxs-lookup"><span data-stu-id="fd6fb-121">Connected standby</span></span>
- <span data-ttu-id="fd6fb-122">Ibernazione (stato di alimentazione S4)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-122">Hibernation (S4 power state)</span></span>
- <span data-ttu-id="fd6fb-123">Spegnimento (stato di alimentazione "soft off" S5)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-123">Shutdown (S5 “soft off” power state)</span></span>

<span data-ttu-id="fd6fb-124">Per ulteriori informazioni sugli stati di alimentazione, vedere [Stati di alimentazione del sistema](/windows/win32/power/system-power-states).</span><span class="sxs-lookup"><span data-stu-id="fd6fb-124">To learn more about power states, see [System Power States](/windows/win32/power/system-power-states).</span></span>

## <a name="how-it-works"></a><span data-ttu-id="fd6fb-125">Come funziona</span><span class="sxs-lookup"><span data-stu-id="fd6fb-125">How it works</span></span>

<span data-ttu-id="fd6fb-126">Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-126">When not in use, Surface devices enter an idle, low powered state known as Modern Standby or Connected Standby.</span></span> <span data-ttu-id="fd6fb-127">Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-127">IT admins can remotely trigger devices using a wake request (magic packet) that contains the Media Access Control (MAC) address of the target Surface device.</span></span> <span data-ttu-id="fd6fb-128">Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e app Microsoft Store di terze parti, forniscono il supporto incorporato per WOL.</span><span class="sxs-lookup"><span data-stu-id="fd6fb-128">Many management solutions, such as Microsoft Endpoint Configuration Manager and third-party Microsoft Store apps provide built-in support for WOL.</span></span>

<span data-ttu-id="fd6fb-129">Per abilitare WOL nei dispositivi senza Surface Dock 2, vedi [Wake on LAN for Surface devices.](wake-on-lan-for-surface-devices.md)</span><span class="sxs-lookup"><span data-stu-id="fd6fb-129">To enable WOL on devices without Surface Dock 2, see [Wake on LAN for Surface devices](wake-on-lan-for-surface-devices.md).</span></span>

## <a name="learn-more"></a><span data-ttu-id="fd6fb-130">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="fd6fb-130">Learn more</span></span>

- [<span data-ttu-id="fd6fb-131">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="fd6fb-131">Surface Dock 2</span></span>](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [<span data-ttu-id="fd6fb-132">Riattivazione LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="fd6fb-132">Wake On LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)
- [<span data-ttu-id="fd6fb-133">Stati di alimentazione del sistema</span><span class="sxs-lookup"><span data-stu-id="fd6fb-133">System Power States</span></span>](/windows/win32/power/system-power-states)
- [<span data-ttu-id="fd6fb-134">Configurare Wake on LAN - Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="fd6fb-134">Configure Wake on LAN - Configuration Manager</span></span>](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)

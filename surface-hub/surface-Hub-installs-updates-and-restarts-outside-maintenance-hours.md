---
title: Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni
description: informazioni sulla risoluzione dei problemi relativi all'hub di Surface per gli aggiornamenti automatici
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: Hub Surface, finestra di manutenzione, aggiornamento
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 117c18cfce6dfb84b4fe2156ea98198f96da2abf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833819"
---
# <span data-ttu-id="1fc78-104">Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni</span><span class="sxs-lookup"><span data-stu-id="1fc78-104">Surface Hub may install updates and restart outside maintenance hours</span></span>

<span data-ttu-id="1fc78-105">In circostanze specifiche, Surface Hub installa gli aggiornamenti durante le ore lavorative anziché durante la normale finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="1fc78-105">Under specific circumstances, Surface Hub installs updates during business hours instead of during the regular maintenance window.</span></span> <span data-ttu-id="1fc78-106">Il dispositivo viene quindi riavviato, se necessario.</span><span class="sxs-lookup"><span data-stu-id="1fc78-106">The device then restarts if it is necessary.</span></span> <span data-ttu-id="1fc78-107">Non è possibile usare il dispositivo fino al completamento del processo.</span><span class="sxs-lookup"><span data-stu-id="1fc78-107">You cannot use the device until the process is completed.</span></span>

> [!NOTE]  
> <span data-ttu-id="1fc78-108">Non si tratta di un comportamento previsto per la mancata finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="1fc78-108">This isn't expected behavior for missing a maintenance window.</span></span> <span data-ttu-id="1fc78-109">Si verifica solo se il dispositivo non è aggiornato per un periodo di tempo prolungato.</span><span class="sxs-lookup"><span data-stu-id="1fc78-109">It occurs only if the device is out-of-date for a long time.</span></span>

## <span data-ttu-id="1fc78-110">Causa</span><span class="sxs-lookup"><span data-stu-id="1fc78-110">Cause</span></span>
<span data-ttu-id="1fc78-111">Per assicurarti che l'hub superficie rimanga disponibile per l'uso durante le ore lavorative, l'hub è configurato per eseguire funzioni amministrative durante una finestra di manutenzione definita in impostazioni (Vedi "Riferimenti").</span><span class="sxs-lookup"><span data-stu-id="1fc78-111">To ensure that Surface Hub remains available for use during business hours, the Hub is configured to perform administrative functions during a maintenance window that is defined in Settings (see "References," below).</span></span> <span data-ttu-id="1fc78-112">Durante questo periodo di manutenzione, l'hub installa automaticamente gli aggiornamenti disponibili tramite Windows Update o Windows Server Update Service (WSUS).</span><span class="sxs-lookup"><span data-stu-id="1fc78-112">During this maintenance period, the Hub automatically installs any available updates through Windows Update or Windows Server Update Service (WSUS).</span></span> <span data-ttu-id="1fc78-113">Una volta completati gli aggiornamenti, l'hub può essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="1fc78-113">Once updates are complete, the Hub may restart.</span></span>

<span data-ttu-id="1fc78-114">Gli aggiornamenti possono essere installati durante la finestra di manutenzione solo se l'hub superficie è attivato ma non in uso o riservato.</span><span class="sxs-lookup"><span data-stu-id="1fc78-114">Updates can be installed during the maintenance window only if the Surface Hub is turned on but not in use or reserved.</span></span> <span data-ttu-id="1fc78-115">Ad esempio, se l'hub Surface è programmato per una riunione che dura 24 ore, gli eventuali aggiornamenti programmati per l'installazione verranno rinviati finché l'hub non sarà disponibile durante la finestra di manutenzione successiva.</span><span class="sxs-lookup"><span data-stu-id="1fc78-115">For example, if the Surface Hub is scheduled for a meeting that lasts 24 hours, any updates that are scheduled to be installed will be deferred until the Hub is available during the next maintenance window.</span></span> <span data-ttu-id="1fc78-116">Se l'hub continua ad essere occupato e mancano più finestre di manutenzione, l'hub inizierà a installare e scaricare gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="1fc78-116">If the Hub continues to be busy and misses multiple maintenance windows, the Hub will eventually begin to install and download updates.</span></span> <span data-ttu-id="1fc78-117">Questo problema può verificarsi durante o all'esterno della finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="1fc78-117">This can occur during or outside the maintenance window.</span></span> <span data-ttu-id="1fc78-118">Una volta che il download e l'installazione sono iniziati, il dispositivo può essere riavviato.</span><span class="sxs-lookup"><span data-stu-id="1fc78-118">Once the download and installation has begun, the device may restart.</span></span>

## <span data-ttu-id="1fc78-119">Per evitare questo problema</span><span class="sxs-lookup"><span data-stu-id="1fc78-119">To avoid this issue</span></span>

<span data-ttu-id="1fc78-120">È importante impostare il tempo di manutenzione per l'hub di Surface per eseguire funzioni amministrative.</span><span class="sxs-lookup"><span data-stu-id="1fc78-120">It's important that you set aside maintenance time for Surface Hub to perform administrative functions.</span></span> <span data-ttu-id="1fc78-121">La riservatezza del mozzo della superficie per intervalli di 24 ore o l'uso del dispositivo durante la finestra di manutenzione ritarda l'installazione degli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="1fc78-121">Reserving the Surface Hub for 24 hour intervals or using the device during the maintenance window delays installing updates.</span></span> <span data-ttu-id="1fc78-122">Ti consigliamo di non usare o prenotare l'hub durante il periodo di manutenzione pianificata.</span><span class="sxs-lookup"><span data-stu-id="1fc78-122">We recommend that you not use or reserve the Hub during scheduled maintenance period.</span></span> <span data-ttu-id="1fc78-123">Una finestra di due ore deve essere riservata per l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fc78-123">A two-hour window should be reserved for updating.</span></span>

<span data-ttu-id="1fc78-124">Un'opzione che puoi usare per controllare la disponibilità degli aggiornamenti è Windows Server Update Service (WSUS).</span><span class="sxs-lookup"><span data-stu-id="1fc78-124">One option that you can use to control the availability of updates is Windows Server Update Service (WSUS).</span></span> <span data-ttu-id="1fc78-125">WSUS fornisce il controllo sugli aggiornamenti installati e quando.</span><span class="sxs-lookup"><span data-stu-id="1fc78-125">WSUS provides control over what updates are installed and when.</span></span>

## <span data-ttu-id="1fc78-126">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="1fc78-126">References</span></span> 
 
[<span data-ttu-id="1fc78-127">Aggiornare Surface Hub</span><span class="sxs-lookup"><span data-stu-id="1fc78-127">Update the Surface Hub</span></span>](first-run-program-surface-hub.md#update-the-surface-hub) 

[<span data-ttu-id="1fc78-128">Finestra di manutenzione</span><span class="sxs-lookup"><span data-stu-id="1fc78-128">Maintenance window</span></span>](manage-windows-updates-for-surface-hub.md#maintenance-window) 

[<span data-ttu-id="1fc78-129">Distribuisci gli aggiornamenti di Windows10 con WindowsServer Update Services (WSUS)</span><span class="sxs-lookup"><span data-stu-id="1fc78-129">Deploy Windows 10 updates using Windows Server Update Services (WSUS)</span></span>](/windows/deployment/update/waas-manage-updates-wsus) 



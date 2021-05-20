---
title: Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni
description: informazioni sulla risoluzione dei problemi Surface Hub sugli aggiornamenti automatici
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub, finestra di manutenzione, aggiornamento
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.date: 04/15/2021
ms.openlocfilehash: 7df7857258c1baeedf4ff239eda17c66c93a531c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577026"
---
# <a name="surface-hub-may-install-updates-and-restart-outside-maintenance-hours"></a><span data-ttu-id="dd66b-104">Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni</span><span class="sxs-lookup"><span data-stu-id="dd66b-104">Surface Hub may install updates and restart outside maintenance hours</span></span>

<span data-ttu-id="dd66b-105">In circostanze specifiche, Surface Hub gli aggiornamenti vengono installati durante l'orario di ufficio anziché durante la normale finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="dd66b-105">Under specific circumstances, Surface Hub installs updates during business hours instead of during the regular maintenance window.</span></span> <span data-ttu-id="dd66b-106">Il dispositivo viene quindi riavviato, se necessario.</span><span class="sxs-lookup"><span data-stu-id="dd66b-106">The device then restarts if it is necessary.</span></span> <span data-ttu-id="dd66b-107">Non puoi usare il dispositivo finché il processo non viene completato.</span><span class="sxs-lookup"><span data-stu-id="dd66b-107">You cannot use the device until the process is completed.</span></span>

> [!NOTE]  
> <span data-ttu-id="dd66b-108">Questo comportamento non è previsto per la mancanza di una finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="dd66b-108">This isn't expected behavior for missing a maintenance window.</span></span> <span data-ttu-id="dd66b-109">Si verifica solo se il dispositivo non è aggiornato per un lungo periodo di tempo.</span><span class="sxs-lookup"><span data-stu-id="dd66b-109">It occurs only if the device is out-of-date for a long time.</span></span>

## <a name="cause"></a><span data-ttu-id="dd66b-110">Causa</span><span class="sxs-lookup"><span data-stu-id="dd66b-110">Cause</span></span>

<span data-ttu-id="dd66b-111">Per garantire che Surface Hub sia disponibile per l'uso durante l'orario di ufficio, l'hub è configurato per eseguire funzioni amministrative durante una finestra di manutenzione definita in Impostazioni (vedere "Riferimenti", di seguito).</span><span class="sxs-lookup"><span data-stu-id="dd66b-111">To ensure that Surface Hub remains available for use during business hours, the Hub is configured to perform administrative functions during a maintenance window that is defined in Settings (see "References," below).</span></span> <span data-ttu-id="dd66b-112">Durante questo periodo di manutenzione, Hub installa automaticamente gli aggiornamenti disponibili tramite Windows Update o Windows Update for Business (WUfB).</span><span class="sxs-lookup"><span data-stu-id="dd66b-112">During this maintenance period, the Hub automatically installs any available updates through Windows Update or Windows Update for Business (WUfB).</span></span> <span data-ttu-id="dd66b-113">Una volta completati gli aggiornamenti, l'hub potrebbe riavviarsi.</span><span class="sxs-lookup"><span data-stu-id="dd66b-113">Once updates are complete, the Hub may restart.</span></span>

<span data-ttu-id="dd66b-114">Gli aggiornamenti possono essere installati durante la finestra di manutenzione solo se il Surface Hub è attivato ma non è in uso o riservato.</span><span class="sxs-lookup"><span data-stu-id="dd66b-114">Updates can be installed during the maintenance window only if the Surface Hub is turned on but not in use or reserved.</span></span> <span data-ttu-id="dd66b-115">Ad esempio, se il Surface Hub è pianificato per una riunione che dura 24 ore, tutti gli aggiornamenti pianificati per l'installazione verranno rinviati fino a quando l'hub non sarà disponibile durante la successiva finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="dd66b-115">For example, if the Surface Hub is scheduled for a meeting that lasts 24 hours, any updates that are scheduled to be installed will be deferred until the Hub is available during the next maintenance window.</span></span> <span data-ttu-id="dd66b-116">Se l'hub continua a essere occupato e mancano più finestre di manutenzione, l'hub inizierà a installare e scaricare gli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="dd66b-116">If the Hub continues to be busy and misses multiple maintenance windows, the Hub will eventually begin to install and download updates.</span></span> <span data-ttu-id="dd66b-117">Ciò può verificarsi durante o all'esterno della finestra di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="dd66b-117">This can occur during or outside the maintenance window.</span></span> <span data-ttu-id="dd66b-118">Dopo l'inizio del download e dell'installazione, il dispositivo potrebbe riavviarsi.</span><span class="sxs-lookup"><span data-stu-id="dd66b-118">Once the download and installation has begun, the device may restart.</span></span>

## <a name="to-avoid-this-issue"></a><span data-ttu-id="dd66b-119">Per evitare questo problema</span><span class="sxs-lookup"><span data-stu-id="dd66b-119">To avoid this issue</span></span>

<span data-ttu-id="dd66b-120">È importante riservare tempo di manutenzione per Surface Hub funzioni amministrative.</span><span class="sxs-lookup"><span data-stu-id="dd66b-120">It's important that you set aside maintenance time for Surface Hub to perform administrative functions.</span></span> <span data-ttu-id="dd66b-121">La prenotazione del Surface Hub per intervalli di 24 ore o l'utilizzo del dispositivo durante la finestra di manutenzione ritarda l'installazione degli aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="dd66b-121">Reserving the Surface Hub for 24 hour intervals or using the device during the maintenance window delays installing updates.</span></span> <span data-ttu-id="dd66b-122">È consigliabile non usare o prenotare l'hub durante il periodo di manutenzione pianificato.</span><span class="sxs-lookup"><span data-stu-id="dd66b-122">We recommend that you not use or reserve the Hub during scheduled maintenance period.</span></span> <span data-ttu-id="dd66b-123">Una finestra di due ore deve essere riservata per l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="dd66b-123">A two-hour window should be reserved for updating.</span></span>

<span data-ttu-id="dd66b-124">Un'opzione che puoi usare per controllare la disponibilità degli aggiornamenti è Windows Update for Business.</span><span class="sxs-lookup"><span data-stu-id="dd66b-124">One option that you can use to control the availability of updates is Windows Update for Business.</span></span>

## <a name="learn-more"></a><span data-ttu-id="dd66b-125">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="dd66b-125">Learn more</span></span>
 
- [<span data-ttu-id="dd66b-126">Aggiornare Surface Hub</span><span class="sxs-lookup"><span data-stu-id="dd66b-126">Update the Surface Hub</span></span>](first-run-program-surface-hub.md#update-the-surface-hub) 
- [<span data-ttu-id="dd66b-127">Finestra di manutenzione</span><span class="sxs-lookup"><span data-stu-id="dd66b-127">Maintenance window</span></span>](manage-windows-updates-for-surface-hub.md#maintenance-window) 

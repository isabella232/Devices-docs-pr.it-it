---
title: Come usare il recupero cloud per BitLocker in un Surface Hub
description: Come usare il recupero cloud per BitLocker in un Surface Hub
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: Impostazioni di accessibilità, app Impostazioni, Accessibilità
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7912f9d1bab2ba625995c56d6d7da4e6b2d3df37
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832672"
---
# <span data-ttu-id="cc36d-104">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="cc36d-104">Summary</span></span>

<span data-ttu-id="cc36d-105">Questo articolo descrive come usare la funzione di ripristino cloud se viene richiesto in modo imprevisto da BitLocker su un dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="cc36d-105">This article describes how to use the cloud recovery function if you are unexpectedly prompted by BitLocker on a Surface Hub device.</span></span>

> [!NOTE]
> <span data-ttu-id="cc36d-106">Seguire questa procedura solo se non è disponibile una chiave di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="cc36d-106">You should follow these steps only if a BitLocker recovery key isn't available.</span></span>

> [!WARNING]
> * <span data-ttu-id="cc36d-107">Questo processo di ripristino Elimina il contenuto dell'unità interna.</span><span class="sxs-lookup"><span data-stu-id="cc36d-107">This recovery process deletes the contents of the internal drive.</span></span> <span data-ttu-id="cc36d-108">Se il processo non riesce, l'unità interna diventerà completamente inutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="cc36d-108">If the process fails, the internal drive will become completely unusable.</span></span> <span data-ttu-id="cc36d-109">In questo caso, sarà necessario registrare una richiesta di servizio con Microsoft per una risoluzione.</span><span class="sxs-lookup"><span data-stu-id="cc36d-109">If this occurs, you will have to log a service request with Microsoft for a resolution.</span></span>
> * <span data-ttu-id="cc36d-110">Al termine del processo di ripristino, il dispositivo verrà reimpostato sulle impostazioni di fabbrica e restituito allo stato di esperienza della casella.</span><span class="sxs-lookup"><span data-stu-id="cc36d-110">After the recovery process is complete, the device will be reset to the factory settings and returned to its Out of Box Experience state.</span></span>
> * <span data-ttu-id="cc36d-111">Dopo il ripristino, il mozzo della superficie deve essere completamente riconfigurato.</span><span class="sxs-lookup"><span data-stu-id="cc36d-111">After the recovery, the Surface Hub must be completely reconfigured.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc36d-112">Questo processo richiede una connessione Internet aperta che non usa un proxy o un altro metodo di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="cc36d-112">This process requires an open Internet connection that does not use a proxy or other authentication method.</span></span>

## <span data-ttu-id="cc36d-113">Processo di ripristino del cloud</span><span class="sxs-lookup"><span data-stu-id="cc36d-113">Cloud recovery process</span></span>

<span data-ttu-id="cc36d-114">Per eseguire un ripristino cloud, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="cc36d-114">To perform a cloud recovery, follow these steps:</span></span>

1. <span data-ttu-id="cc36d-115">Selezionare **premi ESC per altre opzioni di ripristino**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-115">Select **Press Esc for more recovery options**.</span></span>

   ![Schermata di escape](images/01-escape.png)

1. <span data-ttu-id="cc36d-117">Selezionare **Ignora l'unità**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-117">Select **Skip this drive**.</span></span>

   ![Screenshot di skip this drive](images/02-skip-this-drive.png)

1. <span data-ttu-id="cc36d-119">Selezionare **Recupera dal cloud**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-119">Select **Recover from the cloud**.</span></span>

   ![Screenshot del ripristino dal cloud](images/03-recover-from-cloud.png)

1. <span data-ttu-id="cc36d-121">Selezionare **Sì**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-121">Select **Yes**.</span></span>

   ![Schermata di sì](images/04-yes.png)

1. <span data-ttu-id="cc36d-123">Selezionare **Reinstalla**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-123">Select **Reinstall**.</span></span>

   ![Screenshot della reinstallazione](images/05a-reinstall.png)

   ![Screenshot del download](images/05b-downloading.png)

1. <span data-ttu-id="cc36d-126">Dopo il completamento del processo di ripristino della nuvola, avviare la riconfigurazione usando l' **esperienza fuori scatola**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-126">After the cloud recovery process is complete, start the reconfiguration by using the **Out of Box Experience**.</span></span>

   ![Screenshot della casella fuori sede](images/06-out-of-box.png)

## <span data-ttu-id="cc36d-128">Messaggio di errore "si è verificato un problema"</span><span class="sxs-lookup"><span data-stu-id="cc36d-128">"Something went Wrong" error message</span></span>

<span data-ttu-id="cc36d-129">Questo errore è in genere causato da problemi di rete che si verificano durante il download del ripristino.</span><span class="sxs-lookup"><span data-stu-id="cc36d-129">This error is usually caused by network issues that occur during the recovery download.</span></span> <span data-ttu-id="cc36d-130">Quando si verifica questo problema, non disattivare l'hub perché non sarà possibile riavviarlo.</span><span class="sxs-lookup"><span data-stu-id="cc36d-130">When this issue occurs, don't turn off the Hub because you won't be able to restart it.</span></span> <span data-ttu-id="cc36d-131">Se viene visualizzato questo messaggio di errore, tornare al passaggio "Recupera dal cloud" e quindi riavviare il processo di ripristino.</span><span class="sxs-lookup"><span data-stu-id="cc36d-131">If you receive this error message, return to the "Recover from the cloud" step, and then restart the recovery process.</span></span>

1. <span data-ttu-id="cc36d-132">Selezionare **Annulla**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-132">Select **Cancel**.</span></span>

   ![Screenshot di Cancel](images/07-cancel.png)

1. <span data-ttu-id="cc36d-134">Selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-134">Select **Troubleshoot**.</span></span>

   ![Screenshot della risoluzione dei problemi](images/08-troubleshoot.png)

1. <span data-ttu-id="cc36d-136">Selezionare **Recupera dal cloud**.</span><span class="sxs-lookup"><span data-stu-id="cc36d-136">Select **Recover from the cloud**.</span></span>

   ![Screenshot del ripristino dal cloud](images/09-recover-from-cloud2.png)

1. <span data-ttu-id="cc36d-138">Se la **rete cablata non viene trovata** si verifica un errore, selezionare **Annulla**e quindi l'hub Surface riscoprirà la rete cablata.</span><span class="sxs-lookup"><span data-stu-id="cc36d-138">If the **Wired network isn't found** error occurs, select **Cancel**, and then let the Surface Hub rediscover the wired network.</span></span>

   ![Screenshot della rete cablata non trovata](images/10-cancel.png)
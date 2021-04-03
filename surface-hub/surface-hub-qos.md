---
title: Implementare la qualità del servizio in Surface Hub
ms.reviewer: ''
manager: laurawi
description: Scopri come configurare QoS in Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 32d7493dc4a76b8e7642b927ec5db41a1e697b2a
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470484"
---
# <a name="implement-quality-of-service-qos-on-surface-hub"></a><span data-ttu-id="49b63-103">Implementare la qualità del servizio (QoS) in Surface Hub</span><span class="sxs-lookup"><span data-stu-id="49b63-103">Implement Quality of Service (QoS) on Surface Hub</span></span>

<span data-ttu-id="49b63-104">Quality of Service (QoS) è una combinazione di tecnologie di rete che consente agli amministratori di ottimizzare l'esperienza delle comunicazioni audio/video e di condivisione delle applicazioni in tempo reale.</span><span class="sxs-lookup"><span data-stu-id="49b63-104">Quality of Service (QoS) is a combination of network technologies that allows the administrators to optimize the experience of real time audio/video and application sharing communications.</span></span>
 
<span data-ttu-id="49b63-105">La configurazione [di QoS per Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) su Surface Hub può essere eseguita usando il provider di gestione dei dispositivi mobili [(MDM)](manage-settings-with-mdm-for-surface-hub.md) o tramite un [pacchetto di provisioning.](provisioning-packages-for-surface-hub.md)</span><span class="sxs-lookup"><span data-stu-id="49b63-105">Configuring [QoS for Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) on the Surface Hub can be done using your [mobile device management (MDM) provider](manage-settings-with-mdm-for-surface-hub.md) or through a [provisioning package](provisioning-packages-for-surface-hub.md).</span></span> 
 
 
<span data-ttu-id="49b63-106">Questa procedura spiega come configurare QoS per Surface Hub con Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="49b63-106">This procedure explains how to configure QoS for Surface Hub using Microsoft Intune.</span></span> 

1. <span data-ttu-id="49b63-107">In Intune crea [un criterio personalizzato.](https://docs.microsoft.com/intune/custom-settings-configure)</span><span class="sxs-lookup"><span data-stu-id="49b63-107">In Intune, [create a custom policy](https://docs.microsoft.com/intune/custom-settings-configure).</span></span>

    > [!div class="mx-imgBorder"]
    > ![Screenshot della finestra di dialogo per la creazione di criteri personalizzati in Intune](images/qos-create.png)

2. <span data-ttu-id="49b63-109">In **Impostazioni URI OMA personalizzate**seleziona **Aggiungi.**</span><span class="sxs-lookup"><span data-stu-id="49b63-109">In **Custom OMA-URI Settings**, select **Add**.</span></span> <span data-ttu-id="49b63-110">Per ogni impostazione aggiunta, verranno immessi un nome, una descrizione (facoltativa), un tipo di dati, un URI OMA e un valore.</span><span class="sxs-lookup"><span data-stu-id="49b63-110">For each setting that you add, you will enter a name, description (optional), data type, OMA-URI, and value.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Screenshot di una finestra di dialogo di impostazione URI OMA vuota](images/qos-setting.png)

3. <span data-ttu-id="49b63-112">Aggiungi le impostazioni URI OMA personalizzate seguenti:</span><span class="sxs-lookup"><span data-stu-id="49b63-112">Add the following custom OMA-URI settings:</span></span><br/><br/>

    <span data-ttu-id="49b63-113">Nome</span><span class="sxs-lookup"><span data-stu-id="49b63-113">Name</span></span> | <span data-ttu-id="49b63-114">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="49b63-114">Data type</span></span> | <span data-ttu-id="49b63-115">URI OMA</span><span class="sxs-lookup"><span data-stu-id="49b63-115">OMA-URI</span></span><br><span data-ttu-id="49b63-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span><span class="sxs-lookup"><span data-stu-id="49b63-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span></span> |  <span data-ttu-id="49b63-117">Value</span><span class="sxs-lookup"><span data-stu-id="49b63-117">Value</span></span>
    --- | --- | --- | ---
    <span data-ttu-id="49b63-118">Porta origine audio</span><span class="sxs-lookup"><span data-stu-id="49b63-118">Audio Source Port</span></span> | <span data-ttu-id="49b63-119">Stringa</span><span class="sxs-lookup"><span data-stu-id="49b63-119">String</span></span> |  <span data-ttu-id="49b63-120">/HubAudio/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="49b63-120">/HubAudio/SourcePortMatchCondition</span></span>  |   <span data-ttu-id="49b63-121">Ottenere i valori dall'amministratore di Skype</span><span class="sxs-lookup"><span data-stu-id="49b63-121">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="49b63-122">DSCP audio</span><span class="sxs-lookup"><span data-stu-id="49b63-122">Audio DSCP</span></span> | <span data-ttu-id="49b63-123">Numero intero</span><span class="sxs-lookup"><span data-stu-id="49b63-123">Integer</span></span> |  <span data-ttu-id="49b63-124">/HubAudio/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="49b63-124">/HubAudio/DSCPAction</span></span>  |   <span data-ttu-id="49b63-125">46</span><span class="sxs-lookup"><span data-stu-id="49b63-125">46</span></span>
    <span data-ttu-id="49b63-126">Porta origine video</span><span class="sxs-lookup"><span data-stu-id="49b63-126">Video Source Port</span></span> | <span data-ttu-id="49b63-127">Stringa</span><span class="sxs-lookup"><span data-stu-id="49b63-127">String</span></span> |  <span data-ttu-id="49b63-128">/HubVideo/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="49b63-128">/HubVideo/SourcePortMatchCondition</span></span>   |  <span data-ttu-id="49b63-129">Ottenere i valori dall'amministratore di Skype</span><span class="sxs-lookup"><span data-stu-id="49b63-129">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="49b63-130">DSCP video</span><span class="sxs-lookup"><span data-stu-id="49b63-130">Video DSCP</span></span> | <span data-ttu-id="49b63-131">Numero intero</span><span class="sxs-lookup"><span data-stu-id="49b63-131">Integer</span></span> |  <span data-ttu-id="49b63-132">/HubVideo/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="49b63-132">/HubVideo/DSCPAction</span></span>   |   <span data-ttu-id="49b63-133">34</span><span class="sxs-lookup"><span data-stu-id="49b63-133">34</span></span>
    <span data-ttu-id="49b63-134">Nome processo audio</span><span class="sxs-lookup"><span data-stu-id="49b63-134">Audio Process Name</span></span> | <span data-ttu-id="49b63-135">Stringa</span><span class="sxs-lookup"><span data-stu-id="49b63-135">String</span></span> |  <span data-ttu-id="49b63-136">/HubAudio/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="49b63-136">/HubAudio/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="49b63-137">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="49b63-137">Microsoft.PPISkype.Windows.exe</span></span>
    <span data-ttu-id="49b63-138">Nome processo video</span><span class="sxs-lookup"><span data-stu-id="49b63-138">Video Process Name</span></span> | <span data-ttu-id="49b63-139">Stringa</span><span class="sxs-lookup"><span data-stu-id="49b63-139">String</span></span> |  <span data-ttu-id="49b63-140">/HubVideo/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="49b63-140">/HubVideo/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="49b63-141">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="49b63-141">Microsoft.PPISkype.Windows.exe</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="49b63-142">Ogni **percorso URI OMA** inizia con `./Device/Vendor/MSFT/NetworkQoSPolicy` .</span><span class="sxs-lookup"><span data-stu-id="49b63-142">Each **OMA-URI** path begins with `./Device/Vendor/MSFT/NetworkQoSPolicy`.</span></span> <span data-ttu-id="49b63-143">Il percorso completo per l'impostazione della porta di origine audio, ad esempio, sarà `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` .</span><span class="sxs-lookup"><span data-stu-id="49b63-143">The full path for the audio source port setting, for example, will be `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition`.</span></span>

4. <span data-ttu-id="49b63-144">Quando il criterio è stato creato, distribuiscilo in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="49b63-144">When the policy has been created, deploy it to Surface Hub.</span></span>


>[!WARNING]
><span data-ttu-id="49b63-145">Attualmente, non è possibile configurare **l'impostazione IPProtocolMatchCondition** nel [CSP NetworkQoSPolicy.](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp)</span><span class="sxs-lookup"><span data-stu-id="49b63-145">Currently, you cannot configure the setting **IPProtocolMatchCondition** in the [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).</span></span> <span data-ttu-id="49b63-146">Se questa impostazione è configurata, il criterio non verrà applicato.</span><span class="sxs-lookup"><span data-stu-id="49b63-146">If this setting is configured, the policy will fail to apply.</span></span>
 

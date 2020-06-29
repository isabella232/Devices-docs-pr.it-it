---
title: Implementare la qualità del servizio in Surface Hub
ms.reviewer: ''
manager: laurawi
description: Informazioni su come configurare QoS su Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 99172e77be260559c770f5fc8a1438734bed660f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832912"
---
# <span data-ttu-id="a86ca-103">Implementare la qualità del servizio (QoS) in Surface Hub</span><span class="sxs-lookup"><span data-stu-id="a86ca-103">Implement Quality of Service (QoS) on Surface Hub</span></span>

<span data-ttu-id="a86ca-104">La qualità del servizio (QoS) è una combinazione di tecnologie di rete che consente agli amministratori di ottimizzare l'esperienza delle comunicazioni in tempo reale audio/video e condivisione applicazioni.</span><span class="sxs-lookup"><span data-stu-id="a86ca-104">Quality of Service (QoS) is a combination of network technologies that allows the administrators to optimize the experience of real time audio/video and application sharing communications.</span></span>
 
<span data-ttu-id="a86ca-105">La configurazione [di QoS per Skype for business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) nell'hub Surface può essere eseguita usando il [provider di gestione di dispositivi mobili (MDM)](manage-settings-with-mdm-for-surface-hub.md) o tramite un pacchetto di [provisioning](provisioning-packages-for-surface-hub.md).</span><span class="sxs-lookup"><span data-stu-id="a86ca-105">Configuring [QoS for Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) on the Surface Hub can be done using your [mobile device management (MDM) provider](manage-settings-with-mdm-for-surface-hub.md) or through a [provisioning package](provisioning-packages-for-surface-hub.md).</span></span> 
 
 
<span data-ttu-id="a86ca-106">Questa procedura spiega come configurare QoS per Surface Hub con Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="a86ca-106">This procedure explains how to configure QoS for Surface Hub using Microsoft Intune.</span></span> 

1. <span data-ttu-id="a86ca-107">In Intune [creare criteri personalizzati](https://docs.microsoft.com/intune/custom-settings-configure).</span><span class="sxs-lookup"><span data-stu-id="a86ca-107">In Intune, [create a custom policy](https://docs.microsoft.com/intune/custom-settings-configure).</span></span>

    ![Screenshot della finestra di dialogo Creazione di criteri personalizzati in Intune](images/qos-create.png)

2. <span data-ttu-id="a86ca-109">In **impostazioni di URI OMA personalizzate**selezionare **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="a86ca-109">In **Custom OMA-URI Settings**, select **Add**.</span></span> <span data-ttu-id="a86ca-110">Per ogni impostazione aggiunta, si immetterà un nome, una descrizione (facoltativo), un tipo di dati, un URI OMA e un valore.</span><span class="sxs-lookup"><span data-stu-id="a86ca-110">For each setting that you add, you will enter a name, description (optional), data type, OMA-URI, and value.</span></span>

    ![Schermata di una finestra di dialogo di impostazione di URI OMA vuota](images/qos-setting.png)

3. <span data-ttu-id="a86ca-112">Aggiungere le impostazioni di URI OMA personalizzate seguenti:</span><span class="sxs-lookup"><span data-stu-id="a86ca-112">Add the following custom OMA-URI settings:</span></span>

    <span data-ttu-id="a86ca-113">Nome</span><span class="sxs-lookup"><span data-stu-id="a86ca-113">Name</span></span> | <span data-ttu-id="a86ca-114">Tipo di dati</span><span class="sxs-lookup"><span data-stu-id="a86ca-114">Data type</span></span> | <span data-ttu-id="a86ca-115">URI OMA</span><span class="sxs-lookup"><span data-stu-id="a86ca-115">OMA-URI</span></span><br><span data-ttu-id="a86ca-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span><span class="sxs-lookup"><span data-stu-id="a86ca-116">./Device/Vendor/MSFT/NetworkQoSPolicy</span></span> |  <span data-ttu-id="a86ca-117">Value</span><span class="sxs-lookup"><span data-stu-id="a86ca-117">Value</span></span>
    --- | --- | --- | ---
    <span data-ttu-id="a86ca-118">Porta di origine audio</span><span class="sxs-lookup"><span data-stu-id="a86ca-118">Audio Source Port</span></span> | <span data-ttu-id="a86ca-119">String</span><span class="sxs-lookup"><span data-stu-id="a86ca-119">String</span></span> |  <span data-ttu-id="a86ca-120">/HubAudio/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="a86ca-120">/HubAudio/SourcePortMatchCondition</span></span>  |   <span data-ttu-id="a86ca-121">Ottenere i valori dall'amministratore Skype</span><span class="sxs-lookup"><span data-stu-id="a86ca-121">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="a86ca-122">DSCP audio</span><span class="sxs-lookup"><span data-stu-id="a86ca-122">Audio DSCP</span></span> | <span data-ttu-id="a86ca-123">Integer</span><span class="sxs-lookup"><span data-stu-id="a86ca-123">Integer</span></span> |  <span data-ttu-id="a86ca-124">/HubAudio/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="a86ca-124">/HubAudio/DSCPAction</span></span>  |   <span data-ttu-id="a86ca-125">46</span><span class="sxs-lookup"><span data-stu-id="a86ca-125">46</span></span>
    <span data-ttu-id="a86ca-126">Porta di origine video</span><span class="sxs-lookup"><span data-stu-id="a86ca-126">Video Source Port</span></span> | <span data-ttu-id="a86ca-127">String</span><span class="sxs-lookup"><span data-stu-id="a86ca-127">String</span></span> |  <span data-ttu-id="a86ca-128">/HubVideo/SourcePortMatchCondition</span><span class="sxs-lookup"><span data-stu-id="a86ca-128">/HubVideo/SourcePortMatchCondition</span></span>   |  <span data-ttu-id="a86ca-129">Ottenere i valori dall'amministratore Skype</span><span class="sxs-lookup"><span data-stu-id="a86ca-129">Get the values from your Skype administrator</span></span>
    <span data-ttu-id="a86ca-130">DSCP video</span><span class="sxs-lookup"><span data-stu-id="a86ca-130">Video DSCP</span></span> | <span data-ttu-id="a86ca-131">Integer</span><span class="sxs-lookup"><span data-stu-id="a86ca-131">Integer</span></span> |  <span data-ttu-id="a86ca-132">/HubVideo/DSCPAction</span><span class="sxs-lookup"><span data-stu-id="a86ca-132">/HubVideo/DSCPAction</span></span>   |   <span data-ttu-id="a86ca-133">34</span><span class="sxs-lookup"><span data-stu-id="a86ca-133">34</span></span>
    <span data-ttu-id="a86ca-134">Nome processo audio</span><span class="sxs-lookup"><span data-stu-id="a86ca-134">Audio Process Name</span></span> | <span data-ttu-id="a86ca-135">String</span><span class="sxs-lookup"><span data-stu-id="a86ca-135">String</span></span> |  <span data-ttu-id="a86ca-136">/HubAudio/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="a86ca-136">/HubAudio/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="a86ca-137">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="a86ca-137">Microsoft.PPISkype.Windows.exe</span></span>
    <span data-ttu-id="a86ca-138">Nome processo video</span><span class="sxs-lookup"><span data-stu-id="a86ca-138">Video Process Name</span></span> | <span data-ttu-id="a86ca-139">String</span><span class="sxs-lookup"><span data-stu-id="a86ca-139">String</span></span> |  <span data-ttu-id="a86ca-140">/HubVideo/AppPathNameMatchCondition</span><span class="sxs-lookup"><span data-stu-id="a86ca-140">/HubVideo/AppPathNameMatchCondition</span></span>  |   <span data-ttu-id="a86ca-141">Microsoft.PPISkype.Windows.exe</span><span class="sxs-lookup"><span data-stu-id="a86ca-141">Microsoft.PPISkype.Windows.exe</span></span>

    >[!IMPORTANT]
    ><span data-ttu-id="a86ca-142">Ogni percorso con **URI OMA** inizia con `./Device/Vendor/MSFT/NetworkQoSPolicy` .</span><span class="sxs-lookup"><span data-stu-id="a86ca-142">Each **OMA-URI** path begins with `./Device/Vendor/MSFT/NetworkQoSPolicy`.</span></span> <span data-ttu-id="a86ca-143">Il percorso completo per l'impostazione della porta di origine audio, ad esempio, sarà `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` .</span><span class="sxs-lookup"><span data-stu-id="a86ca-143">The full path for the audio source port setting, for example, will be `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition`.</span></span>




4. <span data-ttu-id="a86ca-144">Quando il criterio è stato creato, [distribuirlo nell'hub Surface.](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)</span><span class="sxs-lookup"><span data-stu-id="a86ca-144">When the policy has been created, [deploy it to the Surface Hub.](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)</span></span>


>[!WARNING]
><span data-ttu-id="a86ca-145">Attualmente non è possibile configurare l'impostazione **IPProtocolMatchCondition** nel [CSP NetworkQoSPolicy](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).</span><span class="sxs-lookup"><span data-stu-id="a86ca-145">Currently, you cannot configure the setting **IPProtocolMatchCondition** in the [NetworkQoSPolicy CSP](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp).</span></span> <span data-ttu-id="a86ca-146">Se questa impostazione è configurata, il criterio non verrà applicato.</span><span class="sxs-lookup"><span data-stu-id="a86ca-146">If this setting is configured, the policy will fail to apply.</span></span>
 

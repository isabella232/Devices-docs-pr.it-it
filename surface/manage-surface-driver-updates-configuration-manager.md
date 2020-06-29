---
title: Gestire gli aggiornamenti di Surface driver in Configuration Manager
description: Questo articolo descrive le opzioni disponibili per gestire e distribuire gli aggiornamenti del firmware e del driver per i dispositivi Surface.
ms.assetid: b64879c4-37eb-4fcf-a000-e05cbb3d26ea
ms.reviewer: ''
author: v-miegge
manager: laurawi
keywords: Surface, Surface Pro 3, firmware, aggiornamento, dispositivo, gestire, distribuire, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.author: daclark
ms.topic: article
audience: itpro
ms.openlocfilehash: 1a9c8c64bd524de58696c73a28795b69cc70a7b2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833417"
---
# <span data-ttu-id="43bd0-104">Gestire gli aggiornamenti di Surface driver in Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="43bd0-104">Manage Surface driver updates in Configuration Manager</span></span>

## <span data-ttu-id="43bd0-105">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="43bd0-105">Summary</span></span>

<span data-ttu-id="43bd0-106">A partire da [Microsoft System Center Configuration Manager versione 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates), è possibile sincronizzare e distribuire il firmware Microsoft Surface e gli aggiornamenti dei driver direttamente tramite il client Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="43bd0-106">Starting in [Microsoft System Center Configuration Manager version 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates), you can synchronize and deploy Microsoft Surface firmware and driver updates directly through the Configuration Manager client.</span></span> <span data-ttu-id="43bd0-107">Il processo è simile alla distribuzione di aggiornamenti regolari.</span><span class="sxs-lookup"><span data-stu-id="43bd0-107">The process resembles deploying regular updates.</span></span> <span data-ttu-id="43bd0-108">Tuttavia, sono necessarie altre configurazioni per ottenere gli aggiornamenti di Surface driver nel catalogo.</span><span class="sxs-lookup"><span data-stu-id="43bd0-108">However, some additional configurations are required to get the Surface driver updates into your catalog.</span></span>

## <span data-ttu-id="43bd0-109">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="43bd0-109">Prerequisites</span></span>

<span data-ttu-id="43bd0-110">Per gestire gli aggiornamenti dei driver di Surface, è necessario soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-110">To manage Surface driver updates, the following prerequisites must be met:</span></span>

- <span data-ttu-id="43bd0-111">È necessario usare Configuration Manager versione 1710 o una versione successiva.</span><span class="sxs-lookup"><span data-stu-id="43bd0-111">You must use Configuration Manager version 1710 or a later version.</span></span>
- <span data-ttu-id="43bd0-112">Tutti i punti di aggiornamento software (SUP) devono eseguire Windows Server 2016 o una versione successiva.</span><span class="sxs-lookup"><span data-stu-id="43bd0-112">All Software Update Points (SUPs) must run Windows Server 2016 or a later version.</span></span> <span data-ttu-id="43bd0-113">In caso contrario, Configuration Manager ignora questa impostazione e i driver di superficie non verranno sincronizzati.</span><span class="sxs-lookup"><span data-stu-id="43bd0-113">Otherwise, Configuration Manager ignores this setting and Surface drivers won't be synchronized.</span></span>

> [!NOTE]
> <span data-ttu-id="43bd0-114">Se l'ambiente non soddisfa i prerequisiti, vedere i [metodi alternativi](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) per distribuire gli aggiornamenti del driver di superficie e del firmware nella sezione [domande frequenti](#frequently-asked-questions-faq) .</span><span class="sxs-lookup"><span data-stu-id="43bd0-114">If your environment doesn’t meet the prerequisites, refer to the [alternative methods](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) to deploy Surface driver and firmware updates in the [FAQ](#frequently-asked-questions-faq) section.</span></span>

## <span data-ttu-id="43bd0-115">File di log utili</span><span class="sxs-lookup"><span data-stu-id="43bd0-115">Useful log files</span></span>

<span data-ttu-id="43bd0-116">I registri seguenti sono particolarmente utili per gestire gli aggiornamenti di Surface driver.</span><span class="sxs-lookup"><span data-stu-id="43bd0-116">The following logs are especially useful when you manage Surface driver updates.</span></span>

|<span data-ttu-id="43bd0-117">Nome log</span><span class="sxs-lookup"><span data-stu-id="43bd0-117">Log name</span></span>|<span data-ttu-id="43bd0-118">Descrizione</span><span class="sxs-lookup"><span data-stu-id="43bd0-118">Description</span></span>|
|---|---|
|<span data-ttu-id="43bd0-119">WCM. log</span><span class="sxs-lookup"><span data-stu-id="43bd0-119">WCM.log</span></span>|<span data-ttu-id="43bd0-120">Registra i dettagli sulla configurazione del punto di aggiornamento software e sulle connessioni al server WSUS per categorie di aggiornamento sottoscritte, classificazioni e lingue.</span><span class="sxs-lookup"><span data-stu-id="43bd0-120">Records details about the software update point configuration and connections to the WSUS server for subscribed update categories, classifications, and languages.</span></span>|
|<span data-ttu-id="43bd0-121">WsyncMgr. log</span><span class="sxs-lookup"><span data-stu-id="43bd0-121">WsyncMgr.log</span></span>|<span data-ttu-id="43bd0-122">Registra i dettagli sul processo di sincronizzazione degli aggiornamenti software.</span><span class="sxs-lookup"><span data-stu-id="43bd0-122">Records details about the software updates sync process.</span></span>|

<span data-ttu-id="43bd0-123">Questi registri si trovano nel server del sito che gestisce il SUP o nel SUP stesso se è installato direttamente in un server del sito.</span><span class="sxs-lookup"><span data-stu-id="43bd0-123">These logs are located on the site server that manages the SUP, or on the SUP itself if it's installed directly on a site server.</span></span>
<span data-ttu-id="43bd0-124">Per un elenco completo dei log di Configuration Manager, vedere [file di log in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).</span><span class="sxs-lookup"><span data-stu-id="43bd0-124">For a complete list of Configuration Manager logs, see [Log files in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).</span></span>

## <span data-ttu-id="43bd0-125">Abilitazione della gestione aggiornamenti di Surface driver</span><span class="sxs-lookup"><span data-stu-id="43bd0-125">Enabling Surface driver updates management</span></span>

<span data-ttu-id="43bd0-126">Per abilitare la gestione degli aggiornamenti di Surface driver in Configuration Manager, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-126">To enable Surface driver updates management in Configuration Manager, follow these steps:</span></span>

1. <span data-ttu-id="43bd0-127">Nella console di Configuration Manager accedere ai siti di configurazione del sito di **Amministrazione**  >  **Panoramica**  >  **Site Configuration**  >  **Sites**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-127">In the Configuration Manager console, go to **Administration** > **Overview** > **Site Configuration** > **Sites**.</span></span>
1. <span data-ttu-id="43bd0-128">Selezionare il sito che contiene il server SUP di primo livello per l'ambiente.</span><span class="sxs-lookup"><span data-stu-id="43bd0-128">Select the site that contains the top-level SUP server for your environment.</span></span>
1. <span data-ttu-id="43bd0-129">Sulla barra multifunzione selezionare **Configura componenti sito**e quindi selezionare il **punto di aggiornamento software**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-129">On the ribbon, select **Configure Site Components**, and then select **Software Update Point**.</span></span> <span data-ttu-id="43bd0-130">In alternativa, fare clic con il pulsante destro del mouse sul sito e quindi scegliere **Configura**  >  **punto di aggiornamento software**componenti sito.</span><span class="sxs-lookup"><span data-stu-id="43bd0-130">Or, right-click the site, and then select **Configure Site Components** > **Software Update Point**.</span></span>
1. <span data-ttu-id="43bd0-131">Nella scheda **classificazioni** selezionare la casella di controllo **Includi Microsoft Surface Drivers and Firmware Updates** .</span><span class="sxs-lookup"><span data-stu-id="43bd0-131">On the **Classifications** tab, select the **Include Microsoft Surface drivers and firmware updates** check box.</span></span>

   ![Proprietà del componente punto di aggiornamento software](images/manage-surface-driver-updates-1.png)

1. <span data-ttu-id="43bd0-133">Quando viene visualizzato il messaggio di avviso seguente, selezionare **OK**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-133">When you're prompted by the following warning message, select **OK**.</span></span>

   ![Configuration Manager](images/manage-surface-driver-updates-2.png)

1. <span data-ttu-id="43bd0-135">Nella scheda prodotti selezionare i prodotti che si desidera aggiornare e quindi scegliere **OK**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-135">On the Products tab, select the products that you want to update, and then select **OK**.</span></span>

   <span data-ttu-id="43bd0-136">La maggior parte dei driver appartiene ai gruppi di prodotti seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-136">Most drivers belong to the following product groups:</span></span>

   - <span data-ttu-id="43bd0-137">Driver per Windows 10 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="43bd0-137">Windows 10 and later version drivers</span></span>
   - <span data-ttu-id="43bd0-138">Windows 10 e aggiornamento successivo & i driver di manutenzione</span><span class="sxs-lookup"><span data-stu-id="43bd0-138">Windows 10 and later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-139">Aggiornamento dell'anniversario di Windows 10 e driver di manutenzione successivi</span><span class="sxs-lookup"><span data-stu-id="43bd0-139">Windows 10 Anniversary Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-140">Aggiornamento dell'anniversario di Windows 10 e aggiornamento successivo & driver di manutenzione</span><span class="sxs-lookup"><span data-stu-id="43bd0-140">Windows 10 Anniversary Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-141">Aggiornamento di Windows 10 Creators e driver di manutenzione successivi</span><span class="sxs-lookup"><span data-stu-id="43bd0-141">Windows 10 Creators Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-142">Aggiornamento di Windows 10 Creator e aggiornamento successivo & driver di manutenzione</span><span class="sxs-lookup"><span data-stu-id="43bd0-142">Windows 10 Creators Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-143">Aggiornamento di Windows 10 Fall Creators e driver di manutenzione successivi</span><span class="sxs-lookup"><span data-stu-id="43bd0-143">Windows 10 Fall Creators Update and Later Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-144">Aggiornamento di Windows 10 Fall Creators e aggiornamento successivo & driver di manutenzione</span><span class="sxs-lookup"><span data-stu-id="43bd0-144">Windows 10 Fall Creators Update and Later Upgrade & Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-145">Driver di manutenzione di Windows 10 S e versioni successive</span><span class="sxs-lookup"><span data-stu-id="43bd0-145">Windows 10 S and Later Servicing Drivers</span></span>
   - <span data-ttu-id="43bd0-146">Windows 10 S versione 1709 e versioni successive di manutenzione per i test</span><span class="sxs-lookup"><span data-stu-id="43bd0-146">Windows 10 S Version 1709 and Later Servicing Drivers for testing</span></span>
   - <span data-ttu-id="43bd0-147">Windows 10 S versione 1709 e successive aggiornamento & i driver di manutenzione per i test</span><span class="sxs-lookup"><span data-stu-id="43bd0-147">Windows 10 S Version 1709 and Later Upgrade & Servicing Drivers for testing</span></span>

   > [!NOTE]
   > <span data-ttu-id="43bd0-148">La maggior parte dei driver di superficie appartiene a più gruppi di prodotti Windows 10.</span><span class="sxs-lookup"><span data-stu-id="43bd0-148">Most Surface drivers belong to multiple Windows 10 product groups.</span></span> <span data-ttu-id="43bd0-149">Potrebbe non essere necessario selezionare tutti i prodotti elencati qui.</span><span class="sxs-lookup"><span data-stu-id="43bd0-149">You may not have to select all the products that are listed here.</span></span> <span data-ttu-id="43bd0-150">Per ridurre il numero di prodotti che popolano il catalogo di aggiornamento, è consigliabile selezionare solo i prodotti richiesti dall'ambiente per la sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="43bd0-150">To help reduce the number of products that populate your Update Catalog, we recommend that you select only the products that are required by your environment for synchronization.</span></span>

## <span data-ttu-id="43bd0-151">Verifica della configurazione</span><span class="sxs-lookup"><span data-stu-id="43bd0-151">Verifying the configuration</span></span>

<span data-ttu-id="43bd0-152">Per verificare che il SUP sia configurato correttamente, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-152">To verify that the SUP is configured correctly, follow these steps:</span></span>

1. <span data-ttu-id="43bd0-153">Aprire WsyncMgr. log e quindi cercare la voce seguente:</span><span class="sxs-lookup"><span data-stu-id="43bd0-153">Open WsyncMgr.log, and then look for the following entry:</span></span>

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   <span data-ttu-id="43bd0-154">Se una delle voci seguenti è stata registrata in WsyncMgr. log, ripetere il controllo del passaggio 4 nella sezione precedente:</span><span class="sxs-lookup"><span data-stu-id="43bd0-154">If either of the following entries is logged in WsyncMgr.log, recheck step 4 in the previous section:</span></span>

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. <span data-ttu-id="43bd0-155">Aprire WCM. log e cercare una voce simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="43bd0-155">Open WCM.log, and then look for an entry that resembles the following:</span></span>

   ![Impostazioni di WCM. log](images/manage-surface-driver-updates-3.png)

   <span data-ttu-id="43bd0-157">Questa voce è un elemento XML che elenca tutti i gruppi di prodotti e la classificazione attualmente sincronizzati dal server SUP.</span><span class="sxs-lookup"><span data-stu-id="43bd0-157">This entry is an XML element that lists every product group and classification that's currently synchronized by your SUP server.</span></span> <span data-ttu-id="43bd0-158">Ad esempio, potrebbe essere visualizzata una voce simile alla seguente:</span><span class="sxs-lookup"><span data-stu-id="43bd0-158">For example, you might see an entry that resembles the following:</span></span>

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   <span data-ttu-id="43bd0-159">Se non si trovano i prodotti selezionati nel passaggio 6 nella sezione precedente, verificare che le impostazioni SUP siano salvate.</span><span class="sxs-lookup"><span data-stu-id="43bd0-159">If you can't find the products that you selected in step 6 in the previous section, double-check whether the SUP settings are saved.</span></span>

   <span data-ttu-id="43bd0-160">È anche possibile attendere il completamento della sincronizzazione successiva, quindi verificare se il driver della superficie e gli aggiornamenti del firmware sono elencati in aggiornamenti software nella console di Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="43bd0-160">You can also wait until the next synchronization finishes, and then check whether the Surface driver and firmware updates are listed in Software Updates in the Configuration Manager console.</span></span> <span data-ttu-id="43bd0-161">Ad esempio, la console può visualizzare le informazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-161">For example, the console might display the following information:</span></span>

   ![Tutti i risultati della ricerca degli aggiornamenti software](images/manage-surface-driver-updates-4.png)

## <span data-ttu-id="43bd0-163">Sincronizzazione manuale</span><span class="sxs-lookup"><span data-stu-id="43bd0-163">Manual synchronization</span></span>

<span data-ttu-id="43bd0-164">Se non si vuole attendere la sincronizzazione successiva, eseguire la procedura seguente per avviare una sincronizzazione:</span><span class="sxs-lookup"><span data-stu-id="43bd0-164">If you don't want to wait until the next synchronization, follow these steps to start a synchronization:</span></span>

1. <span data-ttu-id="43bd0-165">Nella console di Configuration Manager, vai a Panoramica della **raccolta software**  >  **Overview**  >  **Aggiorna**  >  **tutti gli aggiornamenti software**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-165">In the Configuration Manager console, go to **Software Library** > **Overview** > **Software Updates** > **All Software Updates**.</span></span>
1. <span data-ttu-id="43bd0-166">Sulla barra multifunzione selezionare **Sincronizza aggiornamenti software**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-166">On the ribbon, select **Synchronize Software Updates**.</span></span> <span data-ttu-id="43bd0-167">In alternativa, fare clic con il pulsante destro del mouse su **tutti gli aggiornamenti software**e quindi scegliere **Sincronizza aggiornamento software**.</span><span class="sxs-lookup"><span data-stu-id="43bd0-167">Or, right-click **All Software Update**, and then select **Synchronize Software Update**.</span></span>
1. <span data-ttu-id="43bd0-168">Monitorare lo stato di avanzamento della sincronizzazione cercando le voci seguenti in WsyncMgr. log:</span><span class="sxs-lookup"><span data-stu-id="43bd0-168">Monitor the synchronization progress by looking for the following entries in WsyncMgr.log:</span></span>

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   sync: SMS synchronizing categories 
   sync: SMS synchronizing categories, processed 0 out of 311 items (0%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing updates

   Synchronizing update 7eaa0148-c42b-45fd-a1ab-012c82972de6 - Microsoft driver update for Surface Type Cover Integration
   Synchronizing update 2dcb07f8-37ec-41ef-8cd5-030bf24dc1d8 - Surface driver update for Surface Pen Pairing
   Synchronizing update 63067414-ae52-422b-b3d1-0382a4d6519a - Surface driver update for Surface UEFI
   Synchronizing update 8e4e3a41-a784-4dd7-9a42-041f43ddb775 - Surface driver update for Surface Integration
   Synchronizing update 7f8baee8-419f-47e2-918a-045a15a188e7 - Microsoft driver update for Surface DTX
   Synchronizing update aed66e05-719b-48cd-a0e7-059e50f67fdc - Microsoft driver update for Surface Base Firmware Update
   Synchronizing update 8ffe1526-6e66-43cc-86e3-05ad92a24e3a - Surface driver update for Surface UEFI
   Synchronizing update 74102899-0a49-48cf-97e6-05bde18a27ff - Microsoft driver update for Surface UEFI
   ```

## <span data-ttu-id="43bd0-169">Distribuzione di aggiornamenti di Surface firmware e driver</span><span class="sxs-lookup"><span data-stu-id="43bd0-169">Deploying Surface firmware and driver updates</span></span>

<span data-ttu-id="43bd0-170">È possibile distribuire gli aggiornamenti del firmware e del driver della superficie nello stesso modo in cui si distribuiscono altri aggiornamenti.</span><span class="sxs-lookup"><span data-stu-id="43bd0-170">You can deploy Surface firmware and driver updates in the same manner as you deploy other updates.</span></span>

<span data-ttu-id="43bd0-171">Per altre informazioni sulla distribuzione, vedere [System Center 2012 Configuration Manager-part7: aggiornamenti software (distribuzione)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).</span><span class="sxs-lookup"><span data-stu-id="43bd0-171">For more information about deployment, see [System Center 2012 Configuration Manager–Part7: Software Updates (Deploy)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).</span></span>

## <span data-ttu-id="43bd0-172">Domande frequenti</span><span class="sxs-lookup"><span data-stu-id="43bd0-172">Frequently asked questions (FAQ)</span></span>

**<span data-ttu-id="43bd0-173">Dopo aver seguito i passaggi descritti in questo articolo, i driver di Surface non sono ancora sincronizzati.</span><span class="sxs-lookup"><span data-stu-id="43bd0-173">After I follow the steps in this article, my Surface drivers are still not synchronized.</span></span> <span data-ttu-id="43bd0-174">Perché?</span><span class="sxs-lookup"><span data-stu-id="43bd0-174">Why?</span></span>**

<span data-ttu-id="43bd0-175">Se si effettua la sincronizzazione da un server Windows Server Update Services (WSUS) upstream, invece di Microsoft Update, verificare che il server WSUS upstream sia configurato per supportare e sincronizzare gli aggiornamenti dei driver di superficie.</span><span class="sxs-lookup"><span data-stu-id="43bd0-175">If you synchronize from an upstream Windows Server Update Services (WSUS) server, instead of Microsoft Update, make sure that the upstream WSUS server is configured to support and synchronize Surface driver updates.</span></span> <span data-ttu-id="43bd0-176">Tutti i server downstream sono limitati agli aggiornamenti presenti nel database del server WSUS upstream.</span><span class="sxs-lookup"><span data-stu-id="43bd0-176">All downstream servers are limited to updates that are present in the upstream WSUS server database.</span></span>

<span data-ttu-id="43bd0-177">Sono disponibili più di 68.000 aggiornamenti classificati come driver in WSUS.</span><span class="sxs-lookup"><span data-stu-id="43bd0-177">There are more than 68,000 updates that are classified as drivers in WSUS.</span></span> <span data-ttu-id="43bd0-178">Per evitare che i driver correlati a una superficie vengano sincronizzati con Configuration Manager, Microsoft filtra la sincronizzazione del driver rispetto a un elenco di Consenti.</span><span class="sxs-lookup"><span data-stu-id="43bd0-178">To prevent non-Surface related drivers from synchronizing to Configuration Manager, Microsoft filters driver synchronization against an allow list.</span></span> <span data-ttu-id="43bd0-179">Dopo che il nuovo elenco Consenti viene pubblicato e incorporato in Gestione configurazione, i nuovi driver vengono aggiunti alla console dopo la sincronizzazione successiva.</span><span class="sxs-lookup"><span data-stu-id="43bd0-179">After the new allow list is published and incorporated into Configuration Manager, the new drivers are added to the console following the next synchronization.</span></span> <span data-ttu-id="43bd0-180">Microsoft mira a ottenere i driver Surface aggiunti all'elenco Consenti ogni mese in linea con la patch martedì per renderli disponibili per la sincronizzazione con Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="43bd0-180">Microsoft aims to get the Surface drivers added to the allow list each month in line with Patch Tuesday to make them available for synchronization to Configuration Manager.</span></span>

<span data-ttu-id="43bd0-181">Se l'ambiente di gestione configurazione è offline, viene importato un nuovo elenco di Consenti ogni volta che si importano [gli aggiornamenti di manutenzione](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) in Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="43bd0-181">If your Configuration Manager environment is offline, a new allow list is imported every time you import [servicing updates](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) to Configuration Manager.</span></span> <span data-ttu-id="43bd0-182">Sarà inoltre necessario importare un [nuovo catalogo WSUS](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) che contiene i driver prima che gli aggiornamenti vengano visualizzati nella console di Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="43bd0-182">You will also have to import a [new WSUS catalog](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) that contains the drivers before the updates are displayed in the Configuration Manager console.</span></span> <span data-ttu-id="43bd0-183">Poiché un ambiente WSUS autonomo contiene più driver di un SUP di Configuration Manager, è consigliabile stabilire un ambiente di gestione configurazione con funzionalità online e configurarlo per sincronizzare i driver di Surface.</span><span class="sxs-lookup"><span data-stu-id="43bd0-183">Because a stand-alone WSUS environment contains more drivers than a Configuration Manager SUP, we recommend that you establish a Configuration Manager environment that has online capabilities, and that you configure it to synchronize Surface drivers.</span></span> <span data-ttu-id="43bd0-184">In questo articolo viene fornita un'esportazione più piccola di WSUS che assomiglia molto all'ambiente offline.</span><span class="sxs-lookup"><span data-stu-id="43bd0-184">This provides a smaller WSUS export that closely resembles the offline environment.</span></span>

<span data-ttu-id="43bd0-185">Se l'ambiente di Configuration Manager è online ed è in grado di rilevare nuovi aggiornamenti, si riceveranno automaticamente gli aggiornamenti all'elenco.</span><span class="sxs-lookup"><span data-stu-id="43bd0-185">If your Configuration Manager environment is online and able to detect new updates, you will receive updates to the list automatically.</span></span> <span data-ttu-id="43bd0-186">Se i driver previsti non sono visualizzati, vedere il WCM. log e WsyncMgr. log per eventuali errori di sincronizzazione.</span><span class="sxs-lookup"><span data-stu-id="43bd0-186">If you don’t see the expected drivers, please review the WCM.log and WsyncMgr.log for any synchronization failures.</span></span>

**<span data-ttu-id="43bd0-187">L'ambiente di gestione configurazione è offline, è possibile importare manualmente i driver di Surface in WSUS?</span><span class="sxs-lookup"><span data-stu-id="43bd0-187">My Configuration Manager environment is offline, can I manually import Surface drivers into WSUS?</span></span>**

<span data-ttu-id="43bd0-188">No.</span><span class="sxs-lookup"><span data-stu-id="43bd0-188">No.</span></span> <span data-ttu-id="43bd0-189">Anche se l'aggiornamento viene importato in WSUS, l'aggiornamento non verrà importato nella console di Configuration Manager per la distribuzione se non è elencato nell'elenco Consenti.</span><span class="sxs-lookup"><span data-stu-id="43bd0-189">Even if the update is imported into WSUS, the update won't be imported into the Configuration Manager console for deployment if it isn't listed in the allow list.</span></span> <span data-ttu-id="43bd0-190">È necessario usare lo [strumento di connessione del servizio](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) per importare gli aggiornamenti di manutenzione in Gestione configurazione per aggiornare l'elenco Consenti.</span><span class="sxs-lookup"><span data-stu-id="43bd0-190">You must use the [Service Connection Tool](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) to import servicing updates to Configuration Manager to update the allow list.</span></span>

**<span data-ttu-id="43bd0-191">Quali metodi alternativi è necessario distribuire per il driver di superficie e gli aggiornamenti del firmware?</span><span class="sxs-lookup"><span data-stu-id="43bd0-191">What alternative methods do I have to deploy Surface driver and firmware updates?</span></span>**

<span data-ttu-id="43bd0-192">Per informazioni su come distribuire gli aggiornamenti del driver di superficie e del firmware tramite canali alternativi, vedere [gestire gli aggiornamenti del driver di superficie e del firmware](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates).</span><span class="sxs-lookup"><span data-stu-id="43bd0-192">For information about how to deploy Surface driver and firmware updates through alternative channels, see [Manage Surface driver and firmware updates](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates).</span></span> <span data-ttu-id="43bd0-193">Se si vuole scaricare il file con estensione msi o exe e quindi distribuire i canali tradizionali di distribuzione del software, vedere [mantenere aggiornato il firmware della superficie con Configuration Manager](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager).</span><span class="sxs-lookup"><span data-stu-id="43bd0-193">If you want to download the .msi or .exe file, and then deploy through traditional software deployment channels, see [Keeping Surface Firmware Updated with Configuration Manager](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager).</span></span>

## <span data-ttu-id="43bd0-194">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="43bd0-194">Additional Information</span></span>

<span data-ttu-id="43bd0-195">Per altre informazioni sul driver di superficie e gli aggiornamenti del firmware, vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="43bd0-195">For more information about Surface driver and firmware updates, see the following articles:</span></span>

- [<span data-ttu-id="43bd0-196">Scaricare le versioni più recenti di firmware e driver per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="43bd0-196">Download the latest firmware and drivers for Surface devices</span></span>](https://docs.microsoft.com/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices)
- [<span data-ttu-id="43bd0-197">Gestire gli aggiornamenti di driver e firmware di Surface</span><span class="sxs-lookup"><span data-stu-id="43bd0-197">Manage Surface driver and firmware updates</span></span>](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates)
- [<span data-ttu-id="43bd0-198">Considerazioni per Surface e System Center Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="43bd0-198">Considerations for Surface and System Center Configuration Manager</span></span>](https://docs.microsoft.com/surface/considerations-for-surface-and-system-center-configuration-manager)

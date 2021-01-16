---
title: Come abilitare la riattivazione dell'alimentazione per Surface
ms.author: v-todmc
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121602
ms.reviewer: hachidan
description: Descrive come abilitare e disabilitare la riattivazione in Power per i dispositivi Surface.
keywords: aggiornamento, distribuzione, driver, WOL, Wake-on-LAN
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.date: 01/15/2021
ms.openlocfilehash: 6ad359861f6af29c567bf0fbf26878ec15c7c642
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271560"
---
# <span data-ttu-id="8ae29-104">Riattivazione alimentazione per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="8ae29-104">Wake on Power for Surface devices</span></span>

<span data-ttu-id="8ae29-105">I dispositivi Surface possono essere spenti quando si è lontani dalla propria scrivania o impostati come modalità di sospensione per risparmiare la durata della batteria.</span><span class="sxs-lookup"><span data-stu-id="8ae29-105">Surface devices can be powered off while you're away from your desk, or set to hibernate mode to save battery life.</span></span> <span data-ttu-id="8ae29-106">Per migliorare la gestibilità di questi dispositivi, Wake on Power consente ai dispositivi Surface compatibili di iniziare automaticamente quando si riconnetteno a Power.</span><span class="sxs-lookup"><span data-stu-id="8ae29-106">To improve the manageability of these devices, Wake on Power enables compatible Surface devices to automatically start when they're reconnected to power.</span></span> <span data-ttu-id="8ae29-107">Per configurare la riattivazione in Power, è possibile usare la modalità di gestione di Surface Enterprise (SEMM) tramite Surface UEFI Configurator o UEFI Manager.</span><span class="sxs-lookup"><span data-stu-id="8ae29-107">To configure Wake on Power, you can use Surface Enterprise Management Mode (SEMM) either through Surface UEFI Configurator or the UEFI Manager.</span></span>

<span data-ttu-id="8ae29-108">La funzionalità riattiva in Power è disponibile nei dispositivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ae29-108">The Wake on Power feature is available on the following devices:</span></span>

- <span data-ttu-id="8ae29-109">Surface Pro 7 +</span><span class="sxs-lookup"><span data-stu-id="8ae29-109">Surface Pro 7+</span></span>
- <span data-ttu-id="8ae29-110">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="8ae29-110">Surface Book 3</span></span>
- <span data-ttu-id="8ae29-111">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="8ae29-111">Surface Pro 7</span></span>
- <span data-ttu-id="8ae29-112">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="8ae29-112">Surface Laptop 3</span></span>
- <span data-ttu-id="8ae29-113">Portatile Surface go</span><span class="sxs-lookup"><span data-stu-id="8ae29-113">Surface Laptop Go</span></span>
- <span data-ttu-id="8ae29-114">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="8ae29-114">Surface Pro X</span></span> 


## <span data-ttu-id="8ae29-115">Panoramica e prerequisiti</span><span class="sxs-lookup"><span data-stu-id="8ae29-115">Overview and prerequisites</span></span>

<span data-ttu-id="8ae29-116">Surface UEFI Configurator consente di salvare singole impostazioni UEFI in un pacchetto di Windows Installer. msi per la distribuzione in dispositivi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="8ae29-116">Surface UEFI Configurator lets you save individual UEFI settings in a Windows Installer .msi package for distribution to target devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="8ae29-117">Questo articolo presuppone che tu sappia usare SEMM.</span><span class="sxs-lookup"><span data-stu-id="8ae29-117">This article assumes that you know how to use SEMM.</span></span> <span data-ttu-id="8ae29-118">Per altre informazioni, vedere la documentazione sulla [modalità di gestione di Surface Enterprise (SEMM)](surface-enterprise-management-mode.md) .</span><span class="sxs-lookup"><span data-stu-id="8ae29-118">For more information, see [Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md) documentation.</span></span>

## <span data-ttu-id="8ae29-119">Per abilitare la riattivazione in Power</span><span class="sxs-lookup"><span data-stu-id="8ae29-119">To enable Wake on Power</span></span>

1.  <span data-ttu-id="8ae29-120">Scaricare l'ultima versione di [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="8ae29-120">Download the latest version of [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span></span>
2.  <span data-ttu-id="8ae29-121">Accedere al dispositivo Surface come amministratore, aprire il **Configuratore di Surface UEFI**, selezionare **dispositivi Surface**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-121">Sign in to your Surface device as an administrator, open **Surface UEFI Configurator**, select **Surface Devices**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Selezionare dispositivi Surface e selezionare Avanti.":::
3.  <span data-ttu-id="8ae29-123">Selezionare **Start**, quindi selezionare **Crea** in **pacchetto di configurazione**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-123">Select **Start**, and then select **Create** under **Configuration Package**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Selezionare Crea pacchetto di configurazione.":::
4.  <span data-ttu-id="8ae29-125">Selezionare **protezione certificato**e aggiungere il file con estensione pfx certificato.</span><span class="sxs-lookup"><span data-stu-id="8ae29-125">Select **Certificate Protection**, and add your certificate .pfx file.</span></span> 
5. <span data-ttu-id="8ae29-126">Immettere la password, scegliere **Avanti**, aggiungere la **protezione tramite password**, in base alle esigenze e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-126">Enter your password, select **Next**, add **Password Protection**, as appropriate, and then select **Next**.</span></span>
6.  <span data-ttu-id="8ae29-127">Nella pagina **scegliere il tipo di superficie da cui si vuole assegnare la destinazione** selezionare i dispositivi di destinazione in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="8ae29-127">On the **Choose which Surface type you want to target** page, select your target devices as appropriate.</span></span> <span data-ttu-id="8ae29-128">Ad esempio, selezionare **Surface Pro 7**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-128">For example, select **Surface Pro 7**.</span></span>
7.  <span data-ttu-id="8ae29-129">Nella pagina **funzionalità avanzate** selezionare **riattiva in Power**, impostare la caratteristica **su**attivato e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-129">On the **Advanced Features** page, select **Wake on Power**, set the feature to **On**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Selezionare Riattiva in Power e imposta su attivato."::: 
8.  <span data-ttu-id="8ae29-131">Nella pagina **completata** selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="8ae29-131">On the **Successful** page, select **End**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8ae29-132">Se è la prima volta che si forniscono impostazioni al dispositivo, verrà richiesto di specificare anche gli ultimi due caratteri dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="8ae29-132">If this is the first time that you are providing settings to your device, you will be prompted to also provide the last two characters of the certificate thumbprint.</span></span> 
9.  <span data-ttu-id="8ae29-133">Salvare il pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="8ae29-133">Save the .msi package.</span></span> 

## <span data-ttu-id="8ae29-134">Applicare il pacchetto MSI</span><span class="sxs-lookup"><span data-stu-id="8ae29-134">Apply the MSI package</span></span> 

<span data-ttu-id="8ae29-135">Puoi applicare il pacchetto MSI ai dispositivi della rete usando strumenti di distribuzione del software come Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="8ae29-135">You can apply the MSI package to devices across your network by using software distribution tools such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="8ae29-136">Questa procedura include i passaggi per installare il pacchetto nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="8ae29-136">This procedure includes steps to install the package on your local computer.</span></span> 

1.  <span data-ttu-id="8ae29-137">In un prompt dei comandi con privilegi elevati, immettere il percorso completo del file MSI per eseguire il pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="8ae29-137">At an elevated command prompt, enter the full path of the .msi file to run the .msi package.</span></span> 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  <span data-ttu-id="8ae29-138">Nella finestra di dialogo **avviso** selezionare **OK** o disabilitare BitLocker, in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="8ae29-138">In the **Warning** dialog box, select **OK** or disable BitLocker, as appropriate.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Selezionare OK o disabilitare BitLocker in base alle esigenze.":::
3.  <span data-ttu-id="8ae29-140">Nella pagina di benvenuto selezionare **Avanti** per eseguire il pacchetto e applicare l'impostazione UEFI appena configurata.</span><span class="sxs-lookup"><span data-stu-id="8ae29-140">On the Welcome page, select **Next** to run the package and apply the newly configured UEFI setting.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Una pagina iniziale, selezionare Avanti.":::
4.  <span data-ttu-id="8ae29-142">Riavviare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8ae29-142">Restart your device.</span></span> 

<span data-ttu-id="8ae29-143">La riattivazione dell'alimentazione è ora configurata.</span><span class="sxs-lookup"><span data-stu-id="8ae29-143">Wake on Power is now configured.</span></span> <span data-ttu-id="8ae29-144">Per verificare le impostazioni, disattivare il dispositivo, scollegare l'alimentazione e quindi riconnettere l'alimentazione.</span><span class="sxs-lookup"><span data-stu-id="8ae29-144">To test the settings, turn off your device, disconnect the power, and then reconnect the power.</span></span> <span data-ttu-id="8ae29-145">Il dispositivo dovrebbe iniziare automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8ae29-145">The device should start automatically.</span></span> 

## <span data-ttu-id="8ae29-146">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="8ae29-146">References</span></span>

<span data-ttu-id="8ae29-147">Per altre informazioni, vedere gli articoli seguenti.</span><span class="sxs-lookup"><span data-stu-id="8ae29-147">For more information, see the following articles.</span></span> 

- [<span data-ttu-id="8ae29-148">Surface Enterprise Management Mode</span><span class="sxs-lookup"><span data-stu-id="8ae29-148">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="8ae29-149">Riattivare la LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="8ae29-149">Wake on LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)

<span data-ttu-id="8ae29-150">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="8ae29-150">Still need help?</span></span> <span data-ttu-id="8ae29-151">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="8ae29-151">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
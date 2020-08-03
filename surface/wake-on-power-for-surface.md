---
title: Come abilitare la riattivazione dell'alimentazione per Surface
ms.author: v-todmc
author: mccoybot
ms.date: 7/30/2020
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121602
ms.reviewer: johnk@cadencepreferred.com
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
ms.openlocfilehash: 271831651280299a40c4e7a7480fa86e29bd1cf5
ms.sourcegitcommit: f875a45961ff5f3c04006afc8690b5e5965e4d80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "10903019"
---
# <span data-ttu-id="d0fdc-104">Riattivazione in Power per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="d0fdc-104">Wake on Power for Surface devices</span></span>

<span data-ttu-id="d0fdc-105">I dispositivi Surface possono essere spenti mentre si è lontani dalla scrivania o impostati in modalità di sospensione per salvare la batteria.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-105">Surface devices can be powered off while away from the desk or set to hibernate mode to save battery.</span></span> <span data-ttu-id="d0fdc-106">Per migliorare la gestibilità di questi dispositivi, Wake on Power consente ai dispositivi Surface compatibili di iniziare automaticamente la riconnessione a Power.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-106">To improve the manageability of these devices, Wake on Power enables compatible Surface devices to automatically start when reconnected to power.</span></span> <span data-ttu-id="d0fdc-107">La configurazione di Wake on Power richiede l'uso della modalità di gestione di Surface Enterprise (SEMM) tramite Surface UEFI Configurator o UEFI Manager.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-107">Configuring Wake on Power requires using Surface Enterprise Management Mode (SEMM) either through Surface UEFI Configurator or the UEFI Manager.</span></span>

<span data-ttu-id="d0fdc-108">Wake on Power è una funzionalità disponibile nei dispositivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0fdc-108">Wake on Power is a feature available on the following devices:</span></span>

- <span data-ttu-id="d0fdc-109">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="d0fdc-109">Surface Book 3</span></span>
- <span data-ttu-id="d0fdc-110">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="d0fdc-110">Surface Pro 7</span></span>
- <span data-ttu-id="d0fdc-111">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="d0fdc-111">Surface Laptop 3</span></span>
- <span data-ttu-id="d0fdc-112">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="d0fdc-112">Surface Pro X</span></span> 

## <span data-ttu-id="d0fdc-113">Panoramica e prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d0fdc-113">Overview and prerequisites</span></span>

<span data-ttu-id="d0fdc-114">Puoi usare Surface UEFI Configurator per configurare singole impostazioni UEFI salvate in un pacchetto di Windows Installer. msi per la distribuzione in dispositivi di destinazione.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-114">You can use the Surface UEFI Configurator to configure individual UEFI settings that are saved in a Windows Installer .msi package for distribution to target devices.</span></span> 

> [!NOTE]
> <span data-ttu-id="d0fdc-115">Questo articolo presuppone che si abbia familiarità con l'uso di SEMM.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-115">This article assumes that you are familiar with using SEMM.</span></span> <span data-ttu-id="d0fdc-116">Per altre informazioni, vedere la documentazione sulla [modalità di gestione di Surface Enterprise (SEMM)](surface-enterprise-management-mode.md) .</span><span class="sxs-lookup"><span data-stu-id="d0fdc-116">For more information, see [Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md) documentation.</span></span>

## <span data-ttu-id="d0fdc-117">Per abilitare la riattivazione in Power</span><span class="sxs-lookup"><span data-stu-id="d0fdc-117">To enable Wake on Power</span></span>

1.  <span data-ttu-id="d0fdc-118">Scaricare l'ultima versione di [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="d0fdc-118">Download the latest version of [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).</span></span>
2.  <span data-ttu-id="d0fdc-119">Accedere al dispositivo Surface come amministratore, aprire il **Configuratore di Surface UEFI**, selezionare **dispositivi Surface**e quindi fare clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-119">Sign into your Surface device as an Administrator, open **Surface UEFI Configurator**, select **Surface Devices**, and then select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Selezionare dispositivi Surface e selezionare Avanti.":::
3.  <span data-ttu-id="d0fdc-121">Selezionare **Avvia** e quindi in **pacchetto di configurazione** Selezionare **Crea**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-121">Select **Start** and then under **Configuration Package** select **Create**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Selezionare Crea pacchetto di configurazione.":::
4.  <span data-ttu-id="d0fdc-123">Selezionare **protezione certificato** e aggiungere il file con estensione pfx certificato.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-123">Select **Certificate Protection** and add your certificate .pfx file.</span></span> <span data-ttu-id="d0fdc-124">Dopo aver immesso la password, selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-124">After entering your password, select **Next**.</span></span> <span data-ttu-id="d0fdc-125">Aggiungere la **protezione con password**, in base alle esigenze e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-125">Add **Password Protection**, as appropriate, and then select **Next**.</span></span>
5.  <span data-ttu-id="d0fdc-126">Nella pagina **scegliere il tipo di superficie da cui si vuole assegnare la destinazione** selezionare i dispositivi di destinazione in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-126">On the **Choose which Surface type you want to target** page, select your target devices as appropriate.</span></span> <span data-ttu-id="d0fdc-127">Ad esempio, **Surface Pro 7**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-127">For example, **Surface Pro 7**.</span></span>
6.  <span data-ttu-id="d0fdc-128">Nella pagina **funzionalità avanzate** selezionare **riattiva in Power** e imposta **su**attivato.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-128">On the **Advanced Features** page, select **Wake on Power** and set to **On**.</span></span> <span data-ttu-id="d0fdc-129">Seleziona **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-129">Select **Next**.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Selezionare Riattiva in Power e imposta su attivato."::: 
7.  <span data-ttu-id="d0fdc-131">Nella pagina **completata** selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-131">On the **Successful** page, select **End**.</span></span> <span data-ttu-id="d0fdc-132">Se è la prima volta che fornisci le impostazioni al dispositivo, verrà richiesto di specificare gli ultimi due caratteri dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-132">If this is your first time providing settings to your device, you will be prompted to provide the last two characters of the certificate thumbprint.</span></span> 
8.  <span data-ttu-id="d0fdc-133">Salvare il pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-133">Save the .msi package.</span></span> 

## <span data-ttu-id="d0fdc-134">Applicare il pacchetto MSI</span><span class="sxs-lookup"><span data-stu-id="d0fdc-134">Apply the MSI package</span></span> 

<span data-ttu-id="d0fdc-135">Puoi applicare il pacchetto MSI ai dispositivi della rete usando strumenti di distribuzione del software come Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-135">You can apply the MSI package to devices across your network using software distribution tools such as Microsoft Endpoint Configuration Manager.</span></span> <span data-ttu-id="d0fdc-136">Questa procedura include i passaggi per installare il pacchetto nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-136">This procedure includes steps for installing the package on your local machine.</span></span> 

1.  <span data-ttu-id="d0fdc-137">Aprire un prompt dei comandi con privilegi elevati e immettere il percorso completo del file MSI per eseguire il pacchetto MSI.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-137">Open an elevated command prompt and enter the full path of the .msi file to run the .msi package.</span></span> 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  <span data-ttu-id="d0fdc-138">Nella finestra di dialogo **avviso** selezionare **OK** o disabilitare BitLocker in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-138">On the **Warning** dialog box, select **OK** or disable Bitlocker as appropriate.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Selezionare OK o disabilitare BitLocker in base alle esigenze.":::
3.  <span data-ttu-id="d0fdc-140">Nella pagina di benvenuto selezionare **Avanti** per eseguire il pacchetto e applicare l'impostazione UEFI appena configurata.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-140">On the Welcome page, select **Next** to run the package and apply the newly configured UEFI setting.</span></span>

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Una pagina iniziale, selezionare Avanti.":::
4.  <span data-ttu-id="d0fdc-142">Riavviare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-142">Restart your device.</span></span> 

<span data-ttu-id="d0fdc-143">La riattivazione dell'alimentazione è ora configurata.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-143">Wake on Power is now configured.</span></span> <span data-ttu-id="d0fdc-144">Per testare l'impostazione, disattivare il dispositivo, scollegare l'alimentazione e quindi riconnettere l'alimentazione.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-144">To test the setting, turn off your device, disconnect the power, and then reconnect the power.</span></span> <span data-ttu-id="d0fdc-145">Il dispositivo verrà avviato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-145">The device will start automatically.</span></span> 

## <span data-ttu-id="d0fdc-146">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="d0fdc-146">More information</span></span>

<span data-ttu-id="d0fdc-147">Per altre informazioni, vedere gli articoli seguenti.</span><span class="sxs-lookup"><span data-stu-id="d0fdc-147">For more information, see the following articles.</span></span> 

- [<span data-ttu-id="d0fdc-148">Surface Enterprise Management Mode</span><span class="sxs-lookup"><span data-stu-id="d0fdc-148">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)
- [<span data-ttu-id="d0fdc-149">Riattivare la LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="d0fdc-149">Wake on LAN for Surface devices</span></span>](wake-on-lan-for-surface-devices.md)

<span data-ttu-id="d0fdc-150">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="d0fdc-150">Still need help?</span></span> <span data-ttu-id="d0fdc-151">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="d0fdc-151">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
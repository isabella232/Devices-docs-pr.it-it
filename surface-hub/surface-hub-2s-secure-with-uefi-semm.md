---
title: Proteggere e gestire Surface Hub 2S con SEMM
description: Leggi altre informazioni su come proteggere Surface Hub 2S con SEMM.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 03ce1dfa48ade8aade545c63818ca5ae8947e6b7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832972"
---
# <span data-ttu-id="9778d-104">Proteggere e gestire Surface Hub 2S con SEMM e UEFI</span><span class="sxs-lookup"><span data-stu-id="9778d-104">Secure and manage Surface Hub 2S with SEMM and UEFI</span></span>

<span data-ttu-id="9778d-105">Nuovo in Surface Hub 2S, è possibile usare SEMM per gestire l'impostazione UEFI del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9778d-105">New in Surface Hub 2S, you can use SEMM to manage the UEFI setting of the device.</span></span>
<span data-ttu-id="9778d-106">Usare Microsoft Surface UEFI Configurator per controllare i componenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="9778d-106">Use the Microsoft Surface UEFI Configurator to control the following components:</span></span>

- <span data-ttu-id="9778d-107">LAN cablata</span><span class="sxs-lookup"><span data-stu-id="9778d-107">Wired LAN</span></span>
- <span data-ttu-id="9778d-108">Fotocamere</span><span class="sxs-lookup"><span data-stu-id="9778d-108">Cameras</span></span>
- <span data-ttu-id="9778d-109">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="9778d-109">Bluetooth</span></span>
- <span data-ttu-id="9778d-110">Wi-Fi</span><span class="sxs-lookup"><span data-stu-id="9778d-110">Wi-Fi</span></span>
- <span data-ttu-id="9778d-111">Sensore di presenza</span><span class="sxs-lookup"><span data-stu-id="9778d-111">Occupancy sensor</span></span>

<span data-ttu-id="9778d-112">Usare Microsoft Surface UEFI Configurator per attivare o disattivare le impostazioni UEFI seguenti:</span><span class="sxs-lookup"><span data-stu-id="9778d-112">Use the Microsoft Surface UEFI Configurator to turn on or off the following UEFI settings:</span></span>

- <span data-ttu-id="9778d-113">Avvio</span><span class="sxs-lookup"><span data-stu-id="9778d-113">Boot</span></span>

    - <span data-ttu-id="9778d-114">Avvio di IPv6 per PXE</span><span class="sxs-lookup"><span data-stu-id="9778d-114">IPv6 for PXE Boot</span></span>
    - <span data-ttu-id="9778d-115">Avvio alternativo</span><span class="sxs-lookup"><span data-stu-id="9778d-115">Alternate Boot</span></span>
    - <span data-ttu-id="9778d-116">Blocco ordine di avvio</span><span class="sxs-lookup"><span data-stu-id="9778d-116">Boot Order Lock</span></span>
    - <span data-ttu-id="9778d-117">Avvio da USB</span><span class="sxs-lookup"><span data-stu-id="9778d-117">USB Boot</span></span>
- <span data-ttu-id="9778d-118">Prima pagina UEFI</span><span class="sxs-lookup"><span data-stu-id="9778d-118">UEFI Front Page</span></span>

    - <span data-ttu-id="9778d-119">Dispositivi</span><span class="sxs-lookup"><span data-stu-id="9778d-119">Devices</span></span>
    - <span data-ttu-id="9778d-120">Avvio</span><span class="sxs-lookup"><span data-stu-id="9778d-120">Boot</span></span>
    - <span data-ttu-id="9778d-121">Data/ora</span><span class="sxs-lookup"><span data-stu-id="9778d-121">Date/Time</span></span>

## <span data-ttu-id="9778d-122">Creare un'immagine di configurazione UEFI</span><span class="sxs-lookup"><span data-stu-id="9778d-122">Create UEFI configuration image</span></span>

<span data-ttu-id="9778d-123">Diversamente da altri dispositivi Surface, non è possibile usare un file MSI o un'immagine PE Win per applicare queste impostazioni su Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="9778d-123">Unlike other Surface devices, you cannot use an MSI file or a Win PE image to apply these settings on Surface Hub 2S.</span></span> <span data-ttu-id="9778d-124">Devi invece creare un'immagine USB per caricarla nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="9778d-124">Instead, you need to create a USB image to load into the device.</span></span> <span data-ttu-id="9778d-125">Per creare un'immagine di configurazione UEFI di Surface Hub 2S, scaricare e installare la versione più recente di Microsoft Surface UEFI Configurator dalla pagina [strumenti Surface per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9778d-125">To create a Surface Hub 2S UEFI configuration image, download and install the latest version of the Microsoft Surface UEFI Configurator from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page in the Microsoft Download Center.</span></span> <span data-ttu-id="9778d-126">Per altre informazioni sull'uso di UEFI e SEMM, vedere [modalità di gestione di Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span><span class="sxs-lookup"><span data-stu-id="9778d-126">For more information about using UEFI and SEMM, see [Microsoft Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>

## <span data-ttu-id="9778d-127">Per configurare UEFI su Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="9778d-127">To configure UEFI on Surface Hub 2S</span></span>

1. <span data-ttu-id="9778d-128">Avviare il configuratore UEFI e nella prima schermata scegliere **pacchetto di configurazione**.</span><span class="sxs-lookup"><span data-stu-id="9778d-128">Start the UEFI Configurator and on the first screen, choose **Configuration Package**.</span></span><br><br>
![\* Avviare il configuratore UEFI e scegliere il pacchetto di configurazione \*](images/sh2-uefi1.png) <br> <br>
2. <span data-ttu-id="9778d-130">Per aggiungere il certificato al pacchetto, è necessario disporre di un certificato valido con la chiave privata in un formato di file PFX per firmare e proteggere il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9778d-130">To add the certificate to your package, you must have a valid certificate with the private key in a .pfx file format to sign and protect the package.</span></span> <span data-ttu-id="9778d-131">Selezionare **+ protezione certificato.**</span><span class="sxs-lookup"><span data-stu-id="9778d-131">Select **+ Certificate Protection.**</span></span> <br>
![\* Selezionare + protezione certificato \*](images/sh2-uefi2.png) <br><br>
3. <span data-ttu-id="9778d-133">Immettere la password della chiave privata del certificato.</span><span class="sxs-lookup"><span data-stu-id="9778d-133">Enter the certificate’s private key’s password.</span></span><br>
![\* Immettere la password della chiave privata del certificato \*](images/sh2-uefi3.png) <br><br>
4. <span data-ttu-id="9778d-135">Dopo aver importato la chiave privata, continuare a creare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9778d-135">After importing the private key, continue creating the package.</span></span><br>
![\* Continuare a creare il pacchetto \*](images/sh2-uefi4.png) <br><br>
5. <span data-ttu-id="9778d-137">Scegli **Hub** e **Surface Hub 2S** come destinazione per il pacchetto di configurazione UEFI.</span><span class="sxs-lookup"><span data-stu-id="9778d-137">Choose **Hub** and **Surface Hub 2S** as the target for the UEFI configuration package.</span></span><br>
![\* Scegliere hub e Surface Hub 2S come destinazione per il pacchetto di configurazione UEFI \*](images/sh2-uefi5.png) <br><br>
6. <span data-ttu-id="9778d-139">Scegliere i componenti e le impostazioni che si desidera attivare o disattivare in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="9778d-139">Choose the components and settings you want to activate or deactivate on Surface Hub 2S.</span></span><br>
![\* Scegliere i componenti e le impostazioni che si desidera attivare o disattivare \*](images/sh2-uefi6.png) <br><br>
7. <span data-ttu-id="9778d-141">Usare l'opzione USB per esportare il file.</span><span class="sxs-lookup"><span data-stu-id="9778d-141">Use the USB option to export the file.</span></span><br>
![\* Usare l'opzione USB per esportare il file \*](images/sh2-uefi8.png) <br><br>
8. <span data-ttu-id="9778d-143">Inserire e scegliere l'unità USB che si vuole usare per questo pacchetto.</span><span class="sxs-lookup"><span data-stu-id="9778d-143">Insert and choose the USB drive you’d like to use for this package.</span></span> <span data-ttu-id="9778d-144">L'unità USB verrà formattata e si perdono tutte le informazioni personali.</span><span class="sxs-lookup"><span data-stu-id="9778d-144">The USB drive will be formatted and you lose any information you have on it.</span></span><br>
![\* Inserire e scegliere l'unità USB per il pacchetto \*](images/sh2-uefi9.png) <br><br>
9. <span data-ttu-id="9778d-146">Dopo aver completato la creazione del pacchetto, il configuratore visualizzerà gli ultimi due caratteri dell'identificazione personale del certificato.</span><span class="sxs-lookup"><span data-stu-id="9778d-146">Upon successful creation of the package, the Configurator will display the last two characters of your certificate’s thumbprint.</span></span> <span data-ttu-id="9778d-147">Questi caratteri sono necessari quando si importano nella configurazione in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="9778d-147">You need these characters when you import to the configuration to Surface Hub 2S.</span></span><br>
![\* Configurazione corretta del pacchetto \*](images/sh2-uefi10.png) <br>

## <span data-ttu-id="9778d-149">Per eseguire l'avvio in UEFI</span><span class="sxs-lookup"><span data-stu-id="9778d-149">To boot into UEFI</span></span>

<span data-ttu-id="9778d-150">Disattivare l'hub di Surface 2S.</span><span class="sxs-lookup"><span data-stu-id="9778d-150">Turn off Surface Hub 2S.</span></span> <span data-ttu-id="9778d-151">Premere e tenere premuto il pulsante **volume su** e premere il pulsante di **accensione** .</span><span class="sxs-lookup"><span data-stu-id="9778d-151">Press and hold the **Volume Up** button and press the **Power** Button.</span></span> <span data-ttu-id="9778d-152">Tenere premuto il pulsante volume su finché non viene visualizzato il menu UEFI.</span><span class="sxs-lookup"><span data-stu-id="9778d-152">Keep holding the Volume Up button until the UEFI menu appears.</span></span>

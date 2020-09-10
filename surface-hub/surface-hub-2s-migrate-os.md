---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: In questo articolo vengono illustrati i processi di migrazione dal team di Windows 10 in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e47ee735c0ba1cc0782c892b64d50f7e9d09f355
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004488"
---
# <span data-ttu-id="e6263-104">Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e6263-104">Migrate to Windows 10 Pro or Enterprise on Surface Hub 2</span></span>

## <span data-ttu-id="e6263-105">Introduzione</span><span class="sxs-lookup"><span data-stu-id="e6263-105">Introduction</span></span>

<span data-ttu-id="e6263-106">Surface Hub 2S viene preinstallato con Windows 10 team, un'edizione personalizzata di Windows 10 progettata per facilitare la collaborazione in ambienti sala riunioni.</span><span class="sxs-lookup"><span data-stu-id="e6263-106">Surface Hub 2S comes pre-installed with Windows 10 Team, a customized edition of Windows 10 designed to facilitate easy collaboration in meeting room environments.</span></span> <span data-ttu-id="e6263-107">Ora hai la possibilità di usare Windows 10 Pro o Enterprise per utilizzare Surface Hub 2S molto simile a qualsiasi altro PC.</span><span class="sxs-lookup"><span data-stu-id="e6263-107">Now you have the option of running Windows 10 Pro or Enterprise to use Surface Hub 2S much like any other PC.</span></span> 

> [!IMPORTANT]
><span data-ttu-id="e6263-108">A differenza di un tipico aggiornamento o migrazione, questo processo richiede di seguire una procedura prescrittiva, come descritto in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="e6263-108">Unlike a typical upgrade or migration, this process requires you to follow a prescriptive procedure, as described on this page.</span></span> <span data-ttu-id="e6263-109">Esaminare i [componenti della soluzione](#solution-components) e il [flusso di lavoro di migrazione](#migration-workflow-summary) prima di procedere.</span><span class="sxs-lookup"><span data-stu-id="e6263-109">Review the [Solution components](#solution-components) and [Migration workflow](#migration-workflow-summary) before proceeding.</span></span>

<span data-ttu-id="e6263-110">Si avvia la migrazione da team Windows 10 usando un PC separato e uno strumento scaricabile-- **Surface UEFI Configurator** --per creare un pacchetto contenente una nuova impostazione UEFI applicata a Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-110">You start the migration from Windows 10 Team using a separate PC and downloadable tool -- **Surface UEFI Configurator** --  to create a package containing a new UEFI setting that you apply to Surface Hub 2S.</span></span>  <span data-ttu-id="e6263-111">Surface UEFI Configurator funge da interfaccia in modalità di gestione di Surface Enterprise (SEMM), progettato per facilitare la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale.</span><span class="sxs-lookup"><span data-stu-id="e6263-111">Surface UEFI Configurator functions as an interface into Surface Enterprise Management Mode (SEMM), designed to facilitate centralized management of firmware settings on Surface devices in a corporate environment.</span></span> <span data-ttu-id="e6263-112">Per altre informazioni su SEMM, vedere la [documentazione relativa alla modalità di gestione Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span><span class="sxs-lookup"><span data-stu-id="e6263-112">To learn more about SEMM, see [Microsoft Surface Enterprise Management Mode documentation](https://docs.microsoft.com/surface/surface-enterprise-management-mode).</span></span>
 

## <span data-ttu-id="e6263-113">Componenti della soluzione</span><span class="sxs-lookup"><span data-stu-id="e6263-113">Solution Components</span></span>

- <span data-ttu-id="e6263-114">Dispositivo Surface Hub 2S con sistema operativo Windows 10 team</span><span class="sxs-lookup"><span data-stu-id="e6263-114">Surface Hub 2S device running Windows 10 Team operating system</span></span>
- <span data-ttu-id="e6263-115">Dispositivo separato con Windows 10</span><span class="sxs-lookup"><span data-stu-id="e6263-115">Separate device running Windows 10</span></span>
- <span data-ttu-id="e6263-116">Strumento di configurazione UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e6263-116">Surface UEFI Configurator tool</span></span>
- <span data-ttu-id="e6263-117">Immagine di Windows 10 Pro o Enterprise OS, versione 1903 o successiva</span><span class="sxs-lookup"><span data-stu-id="e6263-117">Windows 10 Pro or Enterprise OS image, version 1903 or greater</span></span>
- <span data-ttu-id="e6263-118">Due unità USB con 16GB di spazio di archiviazione, formato FAT32</span><span class="sxs-lookup"><span data-stu-id="e6263-118">Two USB drives with 16GB of storage, FAT32 format</span></span>
- <span data-ttu-id="e6263-119">Driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2, Windows Installer. File MSI</span><span class="sxs-lookup"><span data-stu-id="e6263-119">Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2, Windows Installer .MSI file</span></span>
- <span data-ttu-id="e6263-120">Connessione Internet</span><span class="sxs-lookup"><span data-stu-id="e6263-120">Internet connection</span></span>
- <span data-ttu-id="e6263-121">Soluzione di imaging (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="e6263-121">Imaging solution (optional)</span></span>

 
## <span data-ttu-id="e6263-122">Riepilogo del flusso di lavoro di migrazione</span><span class="sxs-lookup"><span data-stu-id="e6263-122">Migration workflow summary</span></span>

| <span data-ttu-id="e6263-123">Passaggio</span><span class="sxs-lookup"><span data-stu-id="e6263-123">Step</span></span>  | <span data-ttu-id="e6263-124">Azione</span><span class="sxs-lookup"><span data-stu-id="e6263-124">Action</span></span>                                                                                                 | <span data-ttu-id="e6263-125">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="e6263-125">Summary</span></span>                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <span data-ttu-id="e6263-126">1</span><span class="sxs-lookup"><span data-stu-id="e6263-126">1</span></span> | [<span data-ttu-id="e6263-127">Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi</span><span class="sxs-lookup"><span data-stu-id="e6263-127">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | <span data-ttu-id="e6263-128">Verificare che la versione UEFI sia 694.2938.768.0 o successiva.</span><span class="sxs-lookup"><span data-stu-id="e6263-128">Ensure the UEFI version is 694.2938.768.0 or later.</span></span>                                                                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="e6263-129">2</span><span class="sxs-lookup"><span data-stu-id="e6263-129">2</span></span> | [<span data-ttu-id="e6263-130">Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware</span><span class="sxs-lookup"><span data-stu-id="e6263-130">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | <span data-ttu-id="e6263-131">Scaricare [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) da strumenti Surface per l'installazione e installarlo in un PC separato.</span><span class="sxs-lookup"><span data-stu-id="e6263-131">Download [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) from Surface Tools for IT and install it on a separate PC.</span></span> <span data-ttu-id="e6263-132">Scaricare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) e salvarlo per l'uso nel passaggio 5.</span><span class="sxs-lookup"><span data-stu-id="e6263-132">Download [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) and save it for use in Step 5.</span></span> |
| <span data-ttu-id="e6263-133">3</span><span class="sxs-lookup"><span data-stu-id="e6263-133">3</span></span> | [<span data-ttu-id="e6263-134">Preparare il certificato di SEMM</span><span class="sxs-lookup"><span data-stu-id="e6263-134">Prepare SEMM certificate</span></span>](#prepare-semm-certificate)                                                                          | <span data-ttu-id="e6263-135">Preparare il certificato richiesto per l'uso di Surface UEFI Configurator o usare il certificato corrente.</span><span class="sxs-lookup"><span data-stu-id="e6263-135">Prepare required certificate for running Surface UEFI Configurator or use your current certificate.</span></span>                                                                                                                                                                                                                                                                                                      |
| <span data-ttu-id="e6263-136">4</span><span class="sxs-lookup"><span data-stu-id="e6263-136">4</span></span> | [<span data-ttu-id="e6263-137">Creare un pacchetto SEMM</span><span class="sxs-lookup"><span data-stu-id="e6263-137">Create SEMM package</span></span>](#create-semm-package)                                                                               | <span data-ttu-id="e6263-138">Avviare il configuratore di Surface UEFI per creare un pacchetto SEMM su un'unità USB che conterrà i file di configurazione necessari per l'applicazione in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-138">Launch Surface UEFI Configurator to create a SEMM package on a USB drive which will contain the required configuration files to apply on Surface Hub 2S.</span></span> <span data-ttu-id="e6263-139">Copiare questi file di pacchetto di SEMM in una cartella nel PC.</span><span class="sxs-lookup"><span data-stu-id="e6263-139">Copy these SEMM package  files to a folder on your PC.</span></span>                                                                                                                                                                                          |
| <span data-ttu-id="e6263-140">5</span><span class="sxs-lookup"><span data-stu-id="e6263-140">5</span></span> | [<span data-ttu-id="e6263-141">Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e6263-141">Prepare USB flash drive containing Windows 10 image, SEMM package, and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2</span></span>](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | <span data-ttu-id="e6263-142">Creare una singola unità USB (denominata **BOOTME** in questo esempio) contenente un'immagine di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e6263-142">Create a single USB drive (named **BOOTME** in this example) containing a Windows 10 image.</span></span> <span data-ttu-id="e6263-143">Aggiungere i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2 (passaggio 2) e i file di pacchetto di SEMM (passaggio 4) all'unità **BOOTME** .</span><span class="sxs-lookup"><span data-stu-id="e6263-143">Add your Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 (Step 2) and SEMM package files (Step 4) to the **BOOTME** drive.</span></span>                                                                                                                                                                                                  |
| <span data-ttu-id="e6263-144">6</span><span class="sxs-lookup"><span data-stu-id="e6263-144">6</span></span> | [<span data-ttu-id="e6263-145">Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e6263-145">Update UEFI on Surface Hub 2S to enable OS migration</span></span>](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | <span data-ttu-id="e6263-146">Usare l'unità **BOOTME** per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.</span><span class="sxs-lookup"><span data-stu-id="e6263-146">Use the **BOOTME** drive to boot Surface Hub 2S to the UEFI menu and install SEMM package.</span></span>|
| <span data-ttu-id="e6263-147">7</span><span class="sxs-lookup"><span data-stu-id="e6263-147">7</span></span> | [<span data-ttu-id="e6263-148">Installare Windows 10 Pro o Enterprise versione 1903 o successiva</span><span class="sxs-lookup"><span data-stu-id="e6263-148">Install Windows 10 Pro or Enterprise version 1903 or later</span></span>](#install-windows-10-pro-or-enterprise)                                        | <span data-ttu-id="e6263-149">Usare l'unità **BOOTME** per installare **Windows 10 Pro o Enterprise** versione 1903 o successiva.</span><span class="sxs-lookup"><span data-stu-id="e6263-149">Use the **BOOTME** drive to Install **Windows 10 Pro or Enterprise** version 1903 or later.</span></span>                                                                                                                                                                                                                                                                                 |
| <span data-ttu-id="e6263-150">8</span><span class="sxs-lookup"><span data-stu-id="e6263-150">8</span></span> | [<span data-ttu-id="e6263-151">Installare driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e6263-151">Install Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2</span></span>](#install-surface-hub-2-drivers-and-firmware)                                        | <span data-ttu-id="e6263-152">Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974)</span><span class="sxs-lookup"><span data-stu-id="e6263-152">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file](https://www.microsoft.com/download/details.aspx?id=101974)</span></span>                                                                                                                                                                                                                                                                                  |
| <span data-ttu-id="e6263-153">9</span><span class="sxs-lookup"><span data-stu-id="e6263-153">9</span></span> | [<span data-ttu-id="e6263-154">Configurare completamente Surface Hub 2S come dispositivo di produttività personale</span><span class="sxs-lookup"><span data-stu-id="e6263-154">Fully configure Surface Hub 2S as a personal productivity device</span></span>](#next-steps)                                        |  <span data-ttu-id="e6263-155">Abilita il set di impostazioni e applicazioni consigliate per ottimizzare l'uso di Surface Hub 2S come dispositivo di produttività personale.</span><span class="sxs-lookup"><span data-stu-id="e6263-155">Enable the set of recommended settings and applications to optimize use of Surface Hub 2S as a personal productivity device.</span></span>                                                                                                                                                                                                                                                                    |

### <span data-ttu-id="e6263-156">Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi</span><span class="sxs-lookup"><span data-stu-id="e6263-156">Verify UEFI version on Surface Hub 2S meets minimum requirements</span></span>

<span data-ttu-id="e6263-157">La versione UEFI minima necessaria prima di eseguire la migrazione di Surface Hub da Windows 10 team a Windows 10 desktop è **694.2938.768.0**.</span><span class="sxs-lookup"><span data-stu-id="e6263-157">The minimum UEFI version required prior to migrating the Surface Hub from Windows 10 Team to Windows 10 Desktop is **694.2938.768.0**.</span></span>
 
**<span data-ttu-id="e6263-158">Per verificare la versione UEFI corrente nel sistema:</span><span class="sxs-lookup"><span data-stu-id="e6263-158">To verify the current UEFI version on your system:</span></span>**

1. <span data-ttu-id="e6263-159">Nella schermata iniziale di Surface Hub 2S selezionare **Avvia** e aprire la **SurfaceApp** (**tutte le app**  >  **Surface**).</span><span class="sxs-lookup"><span data-stu-id="e6263-159">On Surface Hub 2S home screen, select **Start** and open the **SurfaceApp** (**All Apps** > **Surface**).</span></span>

2. <span data-ttu-id="e6263-160">Selezionare la **superficie** per visualizzare le informazioni relative al mozzo della superficie, inclusa la versione corrente dell'UEFI nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e6263-160">Select **Your Surface** to display information about the Surface Hub, including the current version of the UEFI on the device.</span></span> <span data-ttu-id="e6263-161">Se la versione UEFI è **694.2938.768.0** o successiva, come illustrato di seguito, l'UEFI può creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="e6263-161">If the UEFI version is **694.2938.768.0** or later as shown below, the UEFI is eligible for you to create the SEMM package to enable OS migration.</span></span>

    ![App Apri superficie & selezionare la superficie](images/shm-fig1.png)
 
3. <span data-ttu-id="e6263-163">Se la versione UEFI è precedente alla versione **694.2938.768.0**, sarà necessario ottenere una versione corrente con Windows Update.</span><span class="sxs-lookup"><span data-stu-id="e6263-163">If the UEFI version is earlier than version **694.2938.768.0**, you will need to obtain a current version using Windows Update.</span></span>

**<span data-ttu-id="e6263-164">Per aggiornare UEFI da Windows Update:</span><span class="sxs-lookup"><span data-stu-id="e6263-164">To update UEFI from Windows Update:</span></span>**
1. <span data-ttu-id="e6263-165">In Surface Hub 2S, accedere come **amministratore**, accedere a **tutte**le  >  **impostazioni delle**app >  **aggiornamento e sicurezza**di  >  **Windows Update** e installare tutti gli aggiornamenti, quindi riavviare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e6263-165">On your Surface Hub 2S, sign in as an **Admin**, go to **All apps** > **Settings**> **Update and Security** > **Windows Update** and install all updates, then restart the device.</span></span> <span data-ttu-id="e6263-166">Verificare la versione UEFI usando l'app Surface.</span><span class="sxs-lookup"><span data-stu-id="e6263-166">Verify the UEFI version using the Surface App.</span></span> <span data-ttu-id="e6263-167">Nota: se non si conosce il nome utente o la password di amministratore, sarà necessario reimpostare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e6263-167">Note: If you do not know your username or admin password, you will need to reset the device.</span></span> <span data-ttu-id="e6263-168">Per altre informazioni, vedere [reimpostazione e ripristino per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span><span class="sxs-lookup"><span data-stu-id="e6263-168">To learn more, see [Reset and recovery for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).</span></span>

2. <span data-ttu-id="e6263-169">Ripetere questi passaggi fino a quando la versione UEFI non è **694.2938.768.0** o successiva.</span><span class="sxs-lookup"><span data-stu-id="e6263-169">Repeat these steps until the UEFI version is **694.2938.768.0** or later.</span></span>

3. <span data-ttu-id="e6263-170">Se non si vede ancora l'UEFI aggiornato dopo più tentativi, controllare la **cronologia degli aggiornamenti** e cercare eventuali istanze di installazioni del firmware non riuscite.</span><span class="sxs-lookup"><span data-stu-id="e6263-170">If you still do not see the updated UEFI after multiple attempts, check **Update History** and look for any instances of failed firmware installations.</span></span> <span data-ttu-id="e6263-171">Potrebbe essere necessario reimpostare il dispositivo (aggiornamento**delle impostazioni**  >  **&**  >  **dispositivo di ripristino**della sicurezza).</span><span class="sxs-lookup"><span data-stu-id="e6263-171">You may need to reset your device (**Settings** > **Update & security** > **Reset device**).</span></span>

### <span data-ttu-id="e6263-172">Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware</span><span class="sxs-lookup"><span data-stu-id="e6263-172">Download Surface UEFI Configurator and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="e6263-173">In un PC separato:</span><span class="sxs-lookup"><span data-stu-id="e6263-173">On a separate PC:</span></span>

- <span data-ttu-id="e6263-174">Scaricare e installare Microsoft [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) da strumenti di Surface.</span><span class="sxs-lookup"><span data-stu-id="e6263-174">Download and install Microsoft [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) from Surface Tools for IT.</span></span> <span data-ttu-id="e6263-175">Surface UEFI Configurator non può essere eseguito in Surface Hub 2S, mentre è installato Windows 10 team.</span><span class="sxs-lookup"><span data-stu-id="e6263-175">Surface UEFI Configurator cannot be run on Surface Hub 2S, while Windows 10 Team is installed.</span></span>

- <span data-ttu-id="e6263-176">Download [di Surface Hub 2 driver e firmware Windows Installer. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) da applicare durante l'installazione del nuovo sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="e6263-176">Download [Surface Hub 2 Drivers and Firmware Windows Installer .MSI file](https://www.microsoft.com/download/details.aspx?id=101974) to be applied when installing the new operating system.</span></span>

### <span data-ttu-id="e6263-177">Preparare il certificato di SEMM</span><span class="sxs-lookup"><span data-stu-id="e6263-177">Prepare SEMM certificate</span></span>

<span data-ttu-id="e6263-178">Se è la prima volta che si usa Surface UEFI Configurator, è necessario preparare un certificato.</span><span class="sxs-lookup"><span data-stu-id="e6263-178">If this is your first time using Surface UEFI Configurator, you’ll need to prepare a certificate.</span></span> <span data-ttu-id="e6263-179">Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, sia possibile usare solo i pacchetti creati con il certificato approvato per modificare le impostazioni UEFI.</span><span class="sxs-lookup"><span data-stu-id="e6263-179">This certificate ensures that after a device is enrolled in SEMM, only packages created with the approved certificate can be used to modify UEFI settings.</span></span> <span data-ttu-id="e6263-180">La modalità di acquisizione di un certificato può variare in base alle dimensioni o alla complessità dell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="e6263-180">How you acquire a certificate may vary depending on the size or complexity of your organization:</span></span>

- <span data-ttu-id="e6263-181">Le organizzazioni aziendali di grandi dimensioni in genere mantengono una propria infrastruttura di certificati per generare certificati per procedure di sicurezza standard.</span><span class="sxs-lookup"><span data-stu-id="e6263-181">Large enterprise organizations typically maintain their own certificate infrastructure to generate certificates per standard security practices.</span></span>

- <span data-ttu-id="e6263-182">Le medie imprese e altre persone possono scegliere di ottenere un certificato da provider di terze parti.</span><span class="sxs-lookup"><span data-stu-id="e6263-182">Medium-sized businesses and others may choose to obtain a certificate from third party providers.</span></span> <span data-ttu-id="e6263-183">Questa è l'opzione consigliata per le organizzazioni senza sufficienti competenze IT o un team di sicurezza IT dedicato.</span><span class="sxs-lookup"><span data-stu-id="e6263-183">This is the recommended option for organizations without sufficient IT expertise or dedicated IT security team.</span></span>

- <span data-ttu-id="e6263-184">In alternativa, è possibile generare un certificato autofirmato con uno script di PowerShell per la documentazione seguente: [requisiti di certificato in modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span><span class="sxs-lookup"><span data-stu-id="e6263-184">Alternatively, you can generate a self-signed certificate with a PowerShell script per the following documentation: [Surface Enterprise Management Mode certificate requirements](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span> <span data-ttu-id="e6263-185">In alternativa, usare PowerShell per creare un certificato personalizzato per la documentazione seguente: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps).</span><span class="sxs-lookup"><span data-stu-id="e6263-185">Or use PowerShell to create your own certificate per the following documentation: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps).</span></span>

<span data-ttu-id="e6263-186">Il pacchetto SEMM deve essere protetto con un certificato per verificare la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate.</span><span class="sxs-lookup"><span data-stu-id="e6263-186">The SEMM package must be secured with a certificate to verify the signature of configuration files before UEFI settings can be applied.</span></span> <span data-ttu-id="e6263-187">Per altre informazioni, vedere la documentazione relativa alla [modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode) .</span><span class="sxs-lookup"><span data-stu-id="e6263-187">To learn more, see [Surface Enterprise Management Mode](https://docs.microsoft.com/surface/surface-enterprise-management-mode) documentation.</span></span>
 
 
### <span data-ttu-id="e6263-188">Creare un pacchetto SEMM</span><span class="sxs-lookup"><span data-stu-id="e6263-188">Create SEMM package</span></span>

1. <span data-ttu-id="e6263-189">Aprire il **Configuratore di Surface UEFI** e selezionare **Avvia**.</span><span class="sxs-lookup"><span data-stu-id="e6263-189">Open **Surface UEFI Configurator** and select **Start**.</span></span>

   ![Open Surface UEFI Configurator](images/shm-fig2.png)
   
2. <span data-ttu-id="e6263-191">Selezionare **dispositivi Surface** e quindi **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-191">Select **Surface Devices** and then select **Next**.</span></span>

   ![Selezionare i dispositivi Surface](images/shm-fig3.png)
  
3. <span data-ttu-id="e6263-193">Selezionare **pacchetto di configurazione**.</span><span class="sxs-lookup"><span data-stu-id="e6263-193">Select **Configuration Package**.</span></span>

   ![Selezionare il pacchetto di configurazione](images/shm-fig4.png)
  
4. <span data-ttu-id="e6263-195">Selezionare **protezione certificato**.</span><span class="sxs-lookup"><span data-stu-id="e6263-195">Select **Certificate Protection**.</span></span>

   ![Selezionare protezione certificato](images/shm-fig5.png)

5. <span data-ttu-id="e6263-197">Verrà richiesto di aggiungere il file con estensione pfx certificato.</span><span class="sxs-lookup"><span data-stu-id="e6263-197">You will be prompted to add your certificate .pfx file.</span></span>

   ![Verrà richiesto di aggiungere il certificato](images/shm-fig6.png)
   
6. <span data-ttu-id="e6263-199">Immettere la **password del certificato** e scegliere **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6263-199">Enter your **Certificate password** and select **OK**.</span></span>

   ![Immettere la password del certificato e scegliere OK](images/shm-fig7.png)

7. <span data-ttu-id="e6263-201">Selezionare **password di protezione** per aggiungere una password per Surface UEFI.</span><span class="sxs-lookup"><span data-stu-id="e6263-201">Select **Password Protection** to add a password to Surface UEFI.</span></span> <span data-ttu-id="e6263-202">Questa password sarà necessaria ogni volta che si avvia l'avvio in UEFI.</span><span class="sxs-lookup"><span data-stu-id="e6263-202">This password will be required whenever you boot to UEFI.</span></span> <span data-ttu-id="e6263-203">Si **consiglia vivamente** di impostare una password UEFI che si userà su Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-203">It is **strongly recommended** to set a UEFI password you will use on Surface Hub 2S.</span></span>

   ![Fare clic su password di protezione](images/shm-fig8.png)
   
8. <span data-ttu-id="e6263-205">Impostare una **password UEFI** e scegliere **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6263-205">Set a **UEFI password** and select **OK**.</span></span>

   ![Immettere la password UEFI](images/shm-fig9.png)

   > [!IMPORTANT]
   > <span data-ttu-id="e6263-207">Prendere nota della password.</span><span class="sxs-lookup"><span data-stu-id="e6263-207">Make a note of your password.</span></span> <span data-ttu-id="e6263-208">Se si dimentica o si perde la password, non esiste un processo di ripristino.</span><span class="sxs-lookup"><span data-stu-id="e6263-208">If you forget or lose your password, there is no recovery process.</span></span> 

9. <span data-ttu-id="e6263-209">Selezionare **Surface Hub 2S** , quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-209">Select **Surface Hub 2S** and then select **Next**.</span></span>

   ![Selezionare Surface Hub 2S](images/shm-fig10.png)
   
10. <span data-ttu-id="e6263-211">Seleziona **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-211">Select **Next**.</span></span>

    ![Selezionare Avanti](images/shm-fig10a.png)

11. <span data-ttu-id="e6263-213">Per consentire l'installazione di Windows 10 Pro o Enterprise, selezionare **EnableOsMigration.**</span><span class="sxs-lookup"><span data-stu-id="e6263-213">To allow installation of Windows 10 Pro or Enterprise, select **EnableOsMigration.**</span></span>

    ![Selezionare Abilita migrazione del sistema operativo](images/shm-fig11.png)
    
12. <span data-ttu-id="e6263-215">Impostare **EnableOSMigration** **su** attivato e selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-215">Set **EnableOSMigration** to **On** and select **Next**.</span></span>

    ![Impostare attiva migrazione del sistema operativo su attivato](images/shm-fig12.png)

> [!NOTE]
> <span data-ttu-id="e6263-217">Dopo aver applicato un pacchetto SEMM, tutte le impostazioni UEFI verranno visualizzate in grigio (bloccato) nel menu UEFI del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e6263-217">After you apply a SEMM package, all UEFI settings will display as grayed out (locked) in the UEFI menu on the device.</span></span> <span data-ttu-id="e6263-218">Sono inclusi i valori predefiniti per altre impostazioni, ad esempio IPv6 per l'avvio PXE.</span><span class="sxs-lookup"><span data-stu-id="e6263-218">This includes default values for other settings such as IPv6 for PXE Boot.</span></span> <span data-ttu-id="e6263-219">Per modificare le impostazioni UEFI, dovrai applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM.</span><span class="sxs-lookup"><span data-stu-id="e6263-219">To modify UEFI settings, you will need to apply another SEMM package or unenroll the device from SEMM.</span></span>

#### <span data-ttu-id="e6263-220">Salvare il pacchetto SEMM in un'unità USB</span><span class="sxs-lookup"><span data-stu-id="e6263-220">Save SEMM package to USB drive</span></span>

1. <span data-ttu-id="e6263-221">Connettere un'unità USB al PC.</span><span class="sxs-lookup"><span data-stu-id="e6263-221">Connect a USB Drive to your PC.</span></span> <span data-ttu-id="e6263-222">Scegliere **Hub 2S** e quindi **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-222">Choose **Hub 2S** and then select **Next**.</span></span>

   ![Selezionare USB](images/shm-fig13.png)
   
2. <span data-ttu-id="e6263-224">Selezionare **Compila**.</span><span class="sxs-lookup"><span data-stu-id="e6263-224">Select **Build**.</span></span>

   ![Selezionare Compila](images/shm-fig14.png)

3. <span data-ttu-id="e6263-226">Acquisire uno screenshot della pagina e quindi selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="e6263-226">Capture a screenshot of this page and then select **End**.</span></span> <span data-ttu-id="e6263-227">Il pacchetto SEMM è ora pronto e contiene il pacchetto SEMM **DfciUpdate. DFI** e un file di testo con l'identificazione personale di SEMM (gli ultimi due caratteri dell'identificazione personale del certificato).</span><span class="sxs-lookup"><span data-stu-id="e6263-227">Your SEMM package is now ready and contains the SEMM package **DfciUpdate.dfi** and a text file with the SEMM thumbprint (the last two characters of the certificate’s thumbprint).</span></span>

   ![Seleziona fine](images/shm-fig15.png)
   
4. <span data-ttu-id="e6263-229">Salvare gli ultimi 2 caratteri dell'identificazione personale del certificato, necessari per attivare SEMM quando si applica il pacchetto su Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-229">Save the certificate thumbprint’s last 2 characters, which is required to activate SEMM when you apply the package on Surface Hub 2S.</span></span>

### <span data-ttu-id="e6263-230">Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e6263-230">Prepare USB flash drive containing Windows 10 image, SEMM package, and Surface Hub 2 Drivers and Firmware</span></span>

<span data-ttu-id="e6263-231">È possibile installare un'immagine di Windows 10 Pro o Enterprise (versione 1903 o successiva) usando una delle opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e6263-231">You can install a Windows 10 Pro or Enterprise image (version 1903 or later) using one of the following options:</span></span>

- <span data-ttu-id="e6263-232">Soluzione di imaging corrente.</span><span class="sxs-lookup"><span data-stu-id="e6263-232">Your current imaging solution.</span></span>

- <span data-ttu-id="e6263-233">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) ti consente di creare un'immagine di Windows 10 avviabile che può includere tutti gli attuali aggiornamenti di Windows 10, Office, altre app di tua scelta, nonché i driver e il firmware necessari.</span><span class="sxs-lookup"><span data-stu-id="e6263-233">[Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) lets you create a bootable Windows 10 image which can include all of the current Windows 10 updates, Office, other apps of your choice, as well as the required drivers and firmware.</span></span> 

- <span data-ttu-id="e6263-234">Unità flash USB con Windows 10 Pro o Enterprise Image, seguita dall'installazione di  [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span><span class="sxs-lookup"><span data-stu-id="e6263-234">USB flash drive with Windows 10 Pro or Enterprise image, followed by installing  [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 

<span data-ttu-id="e6263-235">Questa procedura descrive la creazione di un'unità flash USB dal supporto di installazione e quindi l'aggiunta dei file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI.</span><span class="sxs-lookup"><span data-stu-id="e6263-235">This procedure describes creating a USB flash drive from installation media and then adding the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI file.</span></span> <span data-ttu-id="e6263-236">Se si usano altri metodi di distribuzione, passare alla sezione seguente: [aggiornare UEFI in Surface Hub 2s per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration).</span><span class="sxs-lookup"><span data-stu-id="e6263-236">If you’re using other deployment methods, proceed to the following section: [Update UEFI on Surface Hub 2S to enable OS migration](#update-uefi-on-surface-hub-2s-to-enable-os-migration).</span></span>

> [!NOTE]
> <span data-ttu-id="e6263-237">Una volta installato, sarà necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e6263-237">Once installed, you will need a valid license for Windows 10 Pro or Windows 10 Enterprise.</span></span>

1. <span data-ttu-id="e6263-238">Per creare un'installazione di Windows 10 Pro, seguire le istruzioni nella pagina [Scarica Windows 10](https://www.microsoft.com/software-download/windows10) per l'uso dello strumento di **creazione di elementi multimediali** .</span><span class="sxs-lookup"><span data-stu-id="e6263-238">To create a Windows 10 Pro installation, follow the instructions on the [Download Windows 10](https://www.microsoft.com/software-download/windows10) page for using the **Media Creation** tool.</span></span> <span data-ttu-id="e6263-239">Per scaricare Windows 10 Enterprise, accedere al [centro servizi per contratti multilicenza Microsoft.](https://www.microsoft.com/licensing/servicecenter/default.aspx)</span><span class="sxs-lookup"><span data-stu-id="e6263-239">To download Windows 10 Enterprise, go to the [Microsoft Volume Licensing Service Center.](https://www.microsoft.com/licensing/servicecenter/default.aspx).</span></span>

2. <span data-ttu-id="e6263-240">Inserire una nuova unità di **archiviazione USB** .</span><span class="sxs-lookup"><span data-stu-id="e6263-240">Insert a new **USB storage** drive.</span></span> <span data-ttu-id="e6263-241">Avviare lo strumento **creazione multimediale** , selezionare **Crea supporto di installazione** e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-241">Launch the **Media Creation** tool, select **Create installation media** and then select **Next**.</span></span>

   ![Creare elementi multimediali di installazione](images/shm-fig16.png)
   
3. <span data-ttu-id="e6263-243">Selezionare lingua, Windows 10 e 64 bit (x64), quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-243">Select language, Windows 10, and 64-bit (x64) and then select **Next**.</span></span>

   ![Selezionare lingua, Windows 10 e 64 bit & selezionare Avanti](images/shm-fig17.png)
   
4. <span data-ttu-id="e6263-245">Selezionare **USB Flash Drive** e quindi **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e6263-245">Select **USB flash drive** and select **Next**.</span></span>

   ![Selezionare unità flash USB e selezionare Avanti](images/shm-fig18.png)
   
5. <span data-ttu-id="e6263-247">Al termine del download, selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="e6263-247">When the download completes, select **Finish**.</span></span>

   ![Selezionare fine](images/shm-fig19.png)
   
6. <span data-ttu-id="e6263-249">Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. MSI per l'unità flash USB (**BOOTME**) che contiene l'immagine di Windows 10:</span><span class="sxs-lookup"><span data-stu-id="e6263-249">Copy the SEMM package files and Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI to the USB flash drive (**BOOTME**) containing your Windows 10 image:</span></span>

    - <span data-ttu-id="e6263-250">DfciUpdate. DFI</span><span class="sxs-lookup"><span data-stu-id="e6263-250">DfciUpdate.dfi</span></span>
    - <span data-ttu-id="e6263-251">File di testo con l'identificazione personale di SEMM.</span><span class="sxs-lookup"><span data-stu-id="e6263-251">Text file with the SEMM thumbprint.</span></span> <span data-ttu-id="e6263-252">In questo esempio: SurfaceUEFI_2020Aug25_1058.txt)</span><span class="sxs-lookup"><span data-stu-id="e6263-252">(In this example: SurfaceUEFI_2020Aug25_1058.txt)</span></span>
    - <span data-ttu-id="e6263-253">Driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)</span><span class="sxs-lookup"><span data-stu-id="e6263-253">Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)</span></span>

### <span data-ttu-id="e6263-254">Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e6263-254">Update UEFI on Surface Hub 2S to enable OS migration</span></span>

<span data-ttu-id="e6263-255">Usare l'unità **BOOTME** per installare i file di pacchetto di SEMM e aggiornare l'UEFI, abilitando Surface hub per eseguire Windows 10 Pro o Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e6263-255">Use your **BOOTME** drive to install the SEMM package files and update the UEFI, enabling Surface Hub to run Windows 10 Pro or Enterprise.</span></span> <span data-ttu-id="e6263-256">Quindi fai il boot dall'unità **BOOTME** per installare Windows 10.</span><span class="sxs-lookup"><span data-stu-id="e6263-256">Then boot from the **BOOTME** drive to install Windows 10.</span></span>

1. <span data-ttu-id="e6263-257">Inserire l'unità **BOOTME** contenente i file di pacchetto di SEMM, i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. MSI e Windows 10 installano i file nella porta USB-A di Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-257">Insert your **BOOTME** drive containing SEMM package files, Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2 .MSI, and Windows 10 install files into the USB-A port on Surface Hub 2S.</span></span>  

2. <span data-ttu-id="e6263-258">Per eseguire il boot in UEFI:</span><span class="sxs-lookup"><span data-stu-id="e6263-258">To boot into UEFI:</span></span>

   1. <span data-ttu-id="e6263-259">Spegnere prima di tutto (Shutdown) il mozzo della superficie 2S.</span><span class="sxs-lookup"><span data-stu-id="e6263-259">First power off (shutdown) your Surface Hub 2S.</span></span>
   1. <span data-ttu-id="e6263-260">Tenere premuto **volume +** e quindi premere e rilasciare il pulsante di **accensione** .</span><span class="sxs-lookup"><span data-stu-id="e6263-260">Press and hold **Volume +** and then press and release the **Power** button.</span></span>
   1. <span data-ttu-id="e6263-261">Tenere premuto **volume +** finché non viene visualizzato il menu UEFI.</span><span class="sxs-lookup"><span data-stu-id="e6263-261">Keep holding **Volume +** until the UEFI menu appears.</span></span>
   
      ![Tenere premuto volume + finché non viene visualizzato il menu UEFI](images/shm-fig20.png)
      
3. <span data-ttu-id="e6263-263">Quando il dispositivo viene riavviato, immettere la password UEFI creata in precedenza, se applicabile (fortemente consigliata).</span><span class="sxs-lookup"><span data-stu-id="e6263-263">When the device restarts, enter the UEFI password you created earlier, if applicable (strongly recommended).</span></span>

   ![Quando il dispositivo viene riavviato, immettere il proprio UEFI paassword](images/shm-fig22.png)
   
4. <span data-ttu-id="e6263-265">Nel menu UEFI selezionare **gestione**  >  **installazione da USB**.</span><span class="sxs-lookup"><span data-stu-id="e6263-265">In the UEFI menu, select **Management** > **Install from USB**.</span></span>

   ![Selezionare Gestione & installazione da USB](images/shm-fig21.png)
   
5. <span data-ttu-id="e6263-267">Selezionare **Riavvia ora**, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="e6263-267">Select **Restart now**, as shown below.</span></span> <span data-ttu-id="e6263-268">Il dispositivo si arresta.</span><span class="sxs-lookup"><span data-stu-id="e6263-268">The device will shut down.</span></span>

   ![Selezionare Riavvia ora](images/shm-fig25.png)
   
6. <span data-ttu-id="e6263-270">Premere e rilasciare il pulsante di alimentazione, verrà visualizzata una schermata rossa che richiede di attivare la modalità di gestione di Surface Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e6263-270">Press and release the power button, a red screen will display prompting you to activate Surface Enterprise Management Mode.</span></span> 

7. <span data-ttu-id="e6263-271">Immettere l' **identificazione personale del certificato**a due caratteri, la **password delle impostazioni UEFI** e quindi scegliere **OK**.</span><span class="sxs-lookup"><span data-stu-id="e6263-271">Enter your two-character **certificate thumbprint**, your **UEFI settings password** and then select **OK**.</span></span>

   ![Immettere l'identificazione personale del certificato di 2 caratteri](images/shm-fig23.png)
 
   > [!NOTE]
   > <span data-ttu-id="e6263-273">Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione UEFI **EnableOSMigration** .</span><span class="sxs-lookup"><span data-stu-id="e6263-273">Once you activate SEMM on your device, the new UEFI setting **EnableOSMigration** is applied.</span></span> <span data-ttu-id="e6263-274">Non sarà più possibile accedere al team di Windows 10 e procedere con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="e6263-274">You will no longer be able to access Windows 10 Team and must proceed to the next step and install Windows 10 Pro or Windows 10 Enterprise.</span></span> 

8. <span data-ttu-id="e6263-275">Il dispositivo verrà riavviato, visualizzerà il quadrato bianco di 4 al centro dello schermo e quindi di nuovo disattivato.</span><span class="sxs-lookup"><span data-stu-id="e6263-275">The device will reboot, display the white 4-square in the middle of the screen, and then again turn off.</span></span>

### <span data-ttu-id="e6263-276">Installare Windows 10 Pro o Enterprise</span><span class="sxs-lookup"><span data-stu-id="e6263-276">Install Windows 10 Pro or Enterprise</span></span>

1. <span data-ttu-id="e6263-277">Se l'unità di avvio di Windows 10 Pro o Enterprise non è già presente nella porta Surface Hub 2 USB-A, inserirla ora e quindi premere e rilasciare il pulsante di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="e6263-277">If your bootable Windows 10 Pro or Enterprise drive is not already in the Surface Hub 2 USB-A port, insert it now and then press and release the power button.</span></span>

2. <span data-ttu-id="e6263-278">Il dispositivo verrà avviato, si vedrà il quadratino bianco a 4 al centro dello schermo, quindi verrà visualizzato un cerchio di filatura sotto il logo quadrato bianco.</span><span class="sxs-lookup"><span data-stu-id="e6263-278">The device will start, you will see the white 4-square in the middle of the screen, and then you will see a spinning circle below the white four-square logo.</span></span>

3. <span data-ttu-id="e6263-279">Se il dispositivo non si avvia automaticamente sull'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e ricollegarlo), premere e rilasciare il pulsante di alimentazione, quindi tenere premuto il pulsante volume giù finché non viene visualizzato il cerchio di filatura sotto il logo quadrato bianco.</span><span class="sxs-lookup"><span data-stu-id="e6263-279">If the device does not automatically boot to the USB drive, power off the device (unplug the power cord and plug it back in),  press and release the power button and then press and hold the volume down button until you see the spinning circle below the white four-square logo.</span></span>
 
   ![Avviare Windows 10 da USB](images/shm-fig26.png)
   
4. <span data-ttu-id="e6263-281">Quando viene avviata l'installazione della configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).</span><span class="sxs-lookup"><span data-stu-id="e6263-281">When the out of box experience (OOBE) setup launches, follow the instructions to install Windows 10 Pro or Enterprise (version 1903 or later).</span></span>

### <span data-ttu-id="e6263-282">Installare i driver e il firmware di Surface Hub 2</span><span class="sxs-lookup"><span data-stu-id="e6263-282">Install Surface Hub 2 drivers and firmware</span></span>

 - <span data-ttu-id="e6263-283">Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span><span class="sxs-lookup"><span data-stu-id="e6263-283">To ensure your device has all the latest updates and drivers, install [Drivers and Firmware for Windows 10 Pro and Enterprise on Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</span></span>
 
### <span data-ttu-id="e6263-284">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="e6263-284">Next steps</span></span>

<span data-ttu-id="e6263-285">Per configurare completamente Surface Hub 2S come dispositivo di produttività personale, vedere [configurare Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2-post-install.md).</span><span class="sxs-lookup"><span data-stu-id="e6263-285">To fully configure Surface Hub 2S as a personal productivity device, see [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).</span></span>

> [!NOTE]
><span data-ttu-id="e6263-286">Se seguire i passaggi descritti in questo documento non riesce a eseguire la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2, contattare il supporto per [Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span><span class="sxs-lookup"><span data-stu-id="e6263-286">If following the steps outlined in this document is unsuccessful in migrating your device to Windows 10 Pro or Enterprise for Surface Hub 2, please contact [Surface Hub Support](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).</span></span>


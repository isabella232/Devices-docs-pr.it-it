---
title: Usare Microsoft endpoint Configuration Manager per gestire i dispositivi con SEMM (Surface)
description: Informazioni su come gestire Microsoft Surface Enterprise Management Mode (SEMM) con endpoint Configuration Manager.
keywords: registrazione, aggiornamento, script, impostazioni
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/13/2020
ms.openlocfilehash: bfd10df3bb7a7dd031c1719d4191ffc46418c4e3
ms.sourcegitcommit: 30c1eb469610dfd2ad9169c154ca07e565240fdb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "11117852"
---
# <span data-ttu-id="5a776-104">Usare Microsoft Endpoint Configuration Manager per configurare dispositivi con SEMM</span><span class="sxs-lookup"><span data-stu-id="5a776-104">Use Microsoft Endpoint Configuration Manager to manage devices with SEMM</span></span>

<span data-ttu-id="5a776-105">La funzionalità SEMM (Microsoft Surface Enterprise Management Mode) dei dispositivi UEFI di Surface consente agli amministratori di gestire e proteggere la configurazione delle impostazioni di Surface UEFI.</span><span class="sxs-lookup"><span data-stu-id="5a776-105">The Microsoft Surface Enterprise Management Mode (SEMM) feature of Surface UEFI devices lets administrators manage and help secure the configuration of Surface UEFI settings.</span></span> <span data-ttu-id="5a776-106">Per la maggior parte delle organizzazioni, questo processo viene eseguito creando pacchetti di Windows Installer (con estensione msi) con lo strumento Microsoft Surface UEFI Configurator.</span><span class="sxs-lookup"><span data-stu-id="5a776-106">For most organizations, this process is accomplished by creating Windows Installer (.msi) packages with the Microsoft Surface UEFI Configurator tool.</span></span> <span data-ttu-id="5a776-107">Questi pacchetti vengono quindi eseguiti o distribuiti nei dispositivi Surface client per la registrazione dei dispositivi in SEMM e per aggiornare la configurazione delle impostazioni di Surface UEFI.</span><span class="sxs-lookup"><span data-stu-id="5a776-107">These packages are then run or deployed to the client Surface devices to enroll the devices in SEMM and to update the Surface UEFI settings configuration.</span></span>

<span data-ttu-id="5a776-108">Per le organizzazioni con Microsoft endpoint Configuration Manager è disponibile un'alternativa all'uso del processo Microsoft Surface UEFI Configurator. msi per la distribuzione e l'amministrazione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-108">For organizations with Microsoft Endpoint Configuration Manager there is an alternative to using the Microsoft Surface UEFI Configurator .msi process to deploy and administer SEMM.</span></span> <span data-ttu-id="5a776-109">Microsoft Surface UEFI Manager è un programma di installazione leggero che rende disponibili gli assembly necessari per la gestione di SEMM in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a776-109">Microsoft Surface UEFI Manager is a lightweight installer that makes required assemblies for SEMM management available on a device.</span></span> <span data-ttu-id="5a776-110">Installando questi assembly con Microsoft Surface UEFI Manager in un client gestito, SEMM può essere gestito da Configuration Manager con gli script di PowerShell, distribuiti come applicazioni.</span><span class="sxs-lookup"><span data-stu-id="5a776-110">By installing these assemblies with Microsoft Surface UEFI Manager on a managed client, SEMM can be administered by Configuration Manager with PowerShell scripts, deployed as applications.</span></span> <span data-ttu-id="5a776-111">Con questo processo, la gestione di SEMM viene eseguita in Configuration Manager, che elimina l'esigenza dello strumento Microsoft Surface UEFI Configurator esterno.</span><span class="sxs-lookup"><span data-stu-id="5a776-111">With this process, SEMM management is performed within Configuration Manager, which eliminates the need for the external Microsoft Surface UEFI Configurator tool.</span></span>

> [!Note]
> <span data-ttu-id="5a776-112">Anche se il processo descritto in questo articolo può funzionare con le versioni precedenti di endpoint Configuration Manager o con altre soluzioni di gestione di terze parti, la gestione di SEMM con Microsoft Surface UEFI Manager e PowerShell è supportata solo con il ramo corrente di endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-112">Although the process described in this article may work with earlier versions of Endpoint Configuration Manager or with other third-party management solutions, management of SEMM with Microsoft Surface UEFI Manager and PowerShell is supported only with the Current Branch of Endpoint Configuration Manager.</span></span>

#### <span data-ttu-id="5a776-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="5a776-113">Prerequisites</span></span>

<span data-ttu-id="5a776-114">Prima di iniziare il processo descritto in questo articolo, acquisire familiarità con le tecnologie e gli strumenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a776-114">Before you begin the process outlined in this article, familiarize yourself with the following technologies and tools:</span></span>

* [<span data-ttu-id="5a776-115">UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="5a776-115">Surface UEFI</span></span>](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)
* [<span data-ttu-id="5a776-116">SEMM (Surface Enterprise Management Mode)</span><span class="sxs-lookup"><span data-stu-id="5a776-116">Surface Enterprise Management Mode (SEMM)</span></span>](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)
* [<span data-ttu-id="5a776-117">Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a776-117">PowerShell scripting</span></span>](https://technet.microsoft.com/scriptcenter/dd742419)
* [<span data-ttu-id="5a776-118">Distribuzione delle applicazioni di System Center Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="5a776-118">System Center Configuration Manager application deployment</span></span>](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)
* <span data-ttu-id="5a776-119">Gestione dei certificati</span><span class="sxs-lookup"><span data-stu-id="5a776-119">Certificate management</span></span>

> [!Note]
> <span data-ttu-id="5a776-120">Sarà inoltre necessario l'accesso al certificato che si vuole usare per proteggere SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-120">You will also need access to the certificate that you intend to use to secure SEMM.</span></span> <span data-ttu-id="5a776-121">Per informazioni dettagliate sui requisiti per il certificato, vedere [requisiti per i certificati della modalità di gestione di Surface Enterprise](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span><span class="sxs-lookup"><span data-stu-id="5a776-121">For details about the requirements for this certificate, see [Surface Enterprise Management Mode certificate requirements](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).</span></span>
> 
> <span data-ttu-id="5a776-122">È molto importante che il certificato venga mantenuto in una posizione sicura e correttamente eseguito il backup.</span><span class="sxs-lookup"><span data-stu-id="5a776-122">It is very important that this certificate be kept in a safe location and properly backed up.</span></span> <span data-ttu-id="5a776-123">Se il certificato viene perso o inutilizzabile, non è possibile reimpostare la superficie UEFI, modificare le impostazioni di Surface UEFI gestite o rimuovere SEMM da un dispositivo Surface registrato.</span><span class="sxs-lookup"><span data-stu-id="5a776-123">If this certificate becomes lost or unusable, it is not possible to reset Surface UEFI, change managed Surface UEFI settings, or remove SEMM from an enrolled Surface device.</span></span>

#### <span data-ttu-id="5a776-124">Scarica Microsoft Surface UEFI Manager</span><span class="sxs-lookup"><span data-stu-id="5a776-124">Download Microsoft Surface UEFI Manager</span></span>

<span data-ttu-id="5a776-125">La gestione di SEMM con Configuration Manager richiede l'installazione di Microsoft Surface UEFI Manager in ogni dispositivo Surface client.</span><span class="sxs-lookup"><span data-stu-id="5a776-125">Management of SEMM with Configuration Manager requires the installation of Microsoft Surface UEFI Manager on each client Surface device.</span></span> <span data-ttu-id="5a776-126">È possibile scaricare Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) dalla pagina [strumenti superficie per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a776-126">You can download Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) from the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page on the Microsoft Download Center.</span></span>

#### <span data-ttu-id="5a776-127">Scaricare gli script di SEMM per Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="5a776-127">Download SEMM scripts for Configuration Manager</span></span>

<span data-ttu-id="5a776-128">Dopo aver installato Microsoft Surface UEFI Manager nel dispositivo Surface client, SEMM viene distribuito e gestito con gli script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a776-128">After Microsoft Surface UEFI Manager is installed on the client Surface device, SEMM is deployed and managed with PowerShell scripts.</span></span> <span data-ttu-id="5a776-129">È possibile scaricare esempi degli [script di gestione di SEMM](https://www.microsoft.com/download/details.aspx?id=46703) dall'area download.</span><span class="sxs-lookup"><span data-stu-id="5a776-129">You can download samples of the [SEMM management scripts](https://www.microsoft.com/download/details.aspx?id=46703) from the Download Center.</span></span>

## <span data-ttu-id="5a776-130">Distribuire Microsoft Surface UEFI Manager</span><span class="sxs-lookup"><span data-stu-id="5a776-130">Deploy Microsoft Surface UEFI Manager</span></span>

<span data-ttu-id="5a776-131">La distribuzione di Microsoft Surface UEFI Manager è una distribuzione tipica dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-131">Deployment of Microsoft Surface UEFI Manager is a typical application deployment.</span></span> <span data-ttu-id="5a776-132">Il file del programma di installazione di Microsoft Surface UEFI Manager è un file di Windows Installer standard che è possibile installare con l' [opzione standard quiet](https://msdn.microsoft.com/library/windows/desktop/aa367988).</span><span class="sxs-lookup"><span data-stu-id="5a776-132">The Microsoft Surface UEFI Manager installer file is a standard Windows Installer file that you can install with the [standard quiet option](https://msdn.microsoft.com/library/windows/desktop/aa367988).</span></span>

<span data-ttu-id="5a776-133">Il comando per installare Microsoft Surface UEFI Manager è il seguente.</span><span class="sxs-lookup"><span data-stu-id="5a776-133">The command to install Microsoft Surface UEFI Manager is as follows.</span></span>

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

<span data-ttu-id="5a776-134">Il comando per disinstallare Microsoft Surface UEFI Manager è il seguente.</span><span class="sxs-lookup"><span data-stu-id="5a776-134">The command to uninstall Microsoft Surface UEFI Manager is as follows.</span></span>

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

<span data-ttu-id="5a776-135">Per creare una nuova applicazione e distribuirla a una raccolta che contiene i dispositivi Surface, eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="5a776-135">To create a new application and deploy it to a collection that contains your Surface devices, perform the following steps:</span></span>

1. <span data-ttu-id="5a776-136">Aprire Configuration Manager Console dalla schermata **Start** o dal menu **Start** .</span><span class="sxs-lookup"><span data-stu-id="5a776-136">Open Configuration Manager Console from the **Start** screen or **Start** menu.</span></span>
2. <span data-ttu-id="5a776-137">Selezionare **raccolta software** nell'angolo in basso a sinistra della finestra.</span><span class="sxs-lookup"><span data-stu-id="5a776-137">Select **Software Library** in the bottom left corner of the window.</span></span>
3. <span data-ttu-id="5a776-138">Espandere il nodo **Gestione applicazioni** della raccolta software e quindi selezionare **applicazioni**.</span><span class="sxs-lookup"><span data-stu-id="5a776-138">Expand the **Application Management** node of the Software Library, and then select **Applications**.</span></span>
4. <span data-ttu-id="5a776-139">Selezionare il pulsante **Crea applicazione** nella scheda **Home** nella parte superiore della finestra.</span><span class="sxs-lookup"><span data-stu-id="5a776-139">Select the **Create Application** button under the **Home** tab at the top of the window.</span></span> <span data-ttu-id="5a776-140">Verrà avviata la creazione guidata applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-140">This starts the Create Application Wizard.</span></span>
5. <span data-ttu-id="5a776-141">La procedura guidata Crea applicazione presenta una serie di passaggi:</span><span class="sxs-lookup"><span data-stu-id="5a776-141">The Create Application Wizard presents a series of steps:</span></span>

   * <span data-ttu-id="5a776-142">**Generale** : l'opzione **rileva automaticamente le informazioni sull'applicazione da file di installazione** è selezionata per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="5a776-142">**General** – The **Automatically detect information about this application from installation files** option is selected by default.</span></span> <span data-ttu-id="5a776-143">Nel campo **tipo** è selezionato anche **Windows Installer (file con estensione msi)** per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="5a776-143">In the **Type** field, **Windows Installer (.msi file)** is also selected by default.</span></span> <span data-ttu-id="5a776-144">Selezionare **Sfoglia** per passare a e selezionare **SurfaceUEFIManagerSetup.msi**e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5a776-144">Select **Browse** to navigate to and select **SurfaceUEFIManagerSetup.msi**, and then select **Next**.</span></span>
   
      > [!Note]
      > <span data-ttu-id="5a776-145">La posizione di SurfaceUEFIManagerSetup.msi deve essere in una condivisione di rete e si trova in una cartella che non contiene altri file.</span><span class="sxs-lookup"><span data-stu-id="5a776-145">The location of SurfaceUEFIManagerSetup.msi must be on a network share and located in a folder that contains no other files.</span></span> <span data-ttu-id="5a776-146">Non è possibile usare un percorso di file locale.</span><span class="sxs-lookup"><span data-stu-id="5a776-146">A local file location cannot be used.</span></span>

   * <span data-ttu-id="5a776-147">**Importare informazioni** : la creazione guidata applicazione analizzerà il file con estensione msi e leggerà il **nome dell'applicazione** e il **codice del prodotto**.</span><span class="sxs-lookup"><span data-stu-id="5a776-147">**Import Information** – The Create Application Wizard will parse the .msi file and read the **Application Name** and **Product Code**.</span></span> <span data-ttu-id="5a776-148">SurfaceUEFIManagerSetup.msi deve essere elencato come unico file sotto i file di **contenuto**della riga, come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="5a776-148">SurfaceUEFIManagerSetup.msi should be listed as the only file under the line **Content Files**, as shown in Figure 1.</span></span> <span data-ttu-id="5a776-149">Selezionare **Avanti** per procedere.</span><span class="sxs-lookup"><span data-stu-id="5a776-149">Select **Next** to proceed.</span></span>

      ![Le informazioni dalla configurazione di Surface UEFI Manager vengono analizzate automaticamente](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *<span data-ttu-id="5a776-151">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="5a776-151">Figure 1.</span></span> <span data-ttu-id="5a776-152">Le informazioni della configurazione di Microsoft Surface UEFI Manager vengono analizzate automaticamente</span><span class="sxs-lookup"><span data-stu-id="5a776-152">Information from Microsoft Surface UEFI Manager setup is automatically parsed</span></span>*

   * <span data-ttu-id="5a776-153">**Informazioni generali** : è possibile modificare il nome dell'applicazione e le informazioni sull'editore e la versione oppure aggiungere commenti in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-153">**General Information** – You can modify the name of the application and information about the publisher and version, or add comments on this page.</span></span> <span data-ttu-id="5a776-154">Il comando di installazione per Microsoft Surface UEFI Manager viene visualizzato nel campo del programma di installazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-154">The installation command for Microsoft Surface UEFI Manager is displayed in the Installation Program field.</span></span> <span data-ttu-id="5a776-155">Il comportamento predefinito per l'installazione di install for System consentirà a Microsoft Surface UEFI Manager di installare gli assembly necessari per SEMM anche se un utente non ha effettuato l'accesso al dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="5a776-155">The default installation behavior of Install for system will allow Microsoft Surface UEFI Manager to install the required assemblies for SEMM even if a user is not logged on to the Surface device.</span></span> <span data-ttu-id="5a776-156">Selezionare **Avanti** per procedere.</span><span class="sxs-lookup"><span data-stu-id="5a776-156">Select **Next** to proceed.</span></span>
   * <span data-ttu-id="5a776-157">**Riepilogo** : le informazioni analizzate nel passaggio informazioni sull' **importazione** e le selezioni del passaggio **informazioni generali** vengono visualizzate in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-157">**Summary** – The information that was parsed in the **Import Information** step and your selections from the **General Information** step is displayed on this page.</span></span> <span data-ttu-id="5a776-158">Selezionare **Avanti** per confermare le selezioni e creare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-158">Select **Next** to confirm your selections and create the application.</span></span>
   * <span data-ttu-id="5a776-159">**Progress** : Visualizza una barra di stato e uno stato quando l'applicazione viene importata e aggiunta alla raccolta software.</span><span class="sxs-lookup"><span data-stu-id="5a776-159">**Progress** – Displays a progress bar and status as the application is imported and added to the Software Library.</span></span>
   * <span data-ttu-id="5a776-160">**Completamento** : la conferma della corretta creazione dell'applicazione viene visualizzata al termine del processo di creazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-160">**Completion** – Confirmation of the successful application creation is displayed when the application creation process is complete.</span></span> <span data-ttu-id="5a776-161">Selezionare **Chiudi** per completare la creazione guidata applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-161">Select **Close** to finish the Create Application Wizard.</span></span>

<span data-ttu-id="5a776-162">Dopo aver creato l'applicazione in Configuration Manager, è possibile distribuirla ai punti di distribuzione e distribuirla alle raccolte, inclusi i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="5a776-162">After the application is created in Configuration Manager, you can distribute it to your distribution points and deploy it to the collections including your Surface devices.</span></span> <span data-ttu-id="5a776-163">Questa applicazione non installerà o consentirà SEMM nel dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="5a776-163">This application will not install or enable SEMM on the Surface device.</span></span> <span data-ttu-id="5a776-164">Fornisce solo gli assembly necessari per l'abilitazione di SEMM con lo script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a776-164">It only provides the assemblies required for SEMM to be enabled using the PowerShell script.</span></span>

<span data-ttu-id="5a776-165">Se non si vogliono installare gli assembly di Microsoft Surface UEFI Manager nei dispositivi che non verranno gestiti con SEMM, è possibile configurare Microsoft Surface UEFI Manager come dipendenza dagli script di gestione configurazione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-165">If you do not want to install the Microsoft Surface UEFI Manager assemblies on devices that will not be managed with SEMM, you can configure Microsoft Surface UEFI Manager as a dependency of the SEMM Configuration Manager scripts.</span></span> <span data-ttu-id="5a776-166">Questo scenario è descritto nella sezione [deploy SEMM Configuration Manager scripts](#deploy-semm-configuration-manager-scripts) più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-166">This scenario is covered in the [Deploy SEMM Configuration Manager Scripts](#deploy-semm-configuration-manager-scripts) section later in this article.</span></span>

## <span data-ttu-id="5a776-167">Creare o modificare gli script di gestione configurazione di SEMM</span><span class="sxs-lookup"><span data-stu-id="5a776-167">Create or modify the SEMM Configuration Manager scripts</span></span>

<span data-ttu-id="5a776-168">Dopo aver installato gli assembly obbligatori nei dispositivi, il processo di registrazione dei dispositivi in SEMM e configurazione della superficie UEFI viene eseguito con gli script di PowerShell e distribuiti come applicazione script con Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-168">After the required assemblies have been installed on the devices, the process of enrolling the devices in SEMM and configuring Surface UEFI is done with PowerShell scripts and deployed as a script application with Configuration Manager.</span></span> <span data-ttu-id="5a776-169">Questi script possono essere modificati per adattarsi alle esigenze dell'organizzazione e dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="5a776-169">These scripts can be modified to fit the needs of your organization and environment.</span></span> <span data-ttu-id="5a776-170">Ad esempio, puoi creare più configurazioni per i dispositivi Surface gestiti in diversi reparti o ruoli.</span><span class="sxs-lookup"><span data-stu-id="5a776-170">For example, you can create multiple configurations for managed Surface devices in different departments or roles.</span></span> <span data-ttu-id="5a776-171">È possibile scaricare esempi di script per SEMM e Configuration Manager dal collegamento nella sezione [prerequisiti](#prerequisites) all'inizio di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-171">You can download samples of the scripts for SEMM and Configuration Manager from the link in the [Prerequisites](#prerequisites) section at the beginning of this article.</span></span>

<span data-ttu-id="5a776-172">Per eseguire una distribuzione di SEMM con Configuration Manager sono necessari due script principali:</span><span class="sxs-lookup"><span data-stu-id="5a776-172">There are two primary scripts you will need in order to perform a SEMM deployment with Configuration Manager:</span></span>

* <span data-ttu-id="5a776-173">**ConfigureSEMM.ps1** : usare questo script per creare pacchetti di configurazione per i dispositivi Surface con le impostazioni di UEFI di Surface desiderate per applicare le impostazioni specificate a un dispositivo Surface, per registrare il dispositivo in SEMM e per impostare una chiave del registro di sistema usata per identificare la registrazione del dispositivo in SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-173">**ConfigureSEMM.ps1** – Use this script to create configuration packages for your Surface devices with your desired Surface UEFI settings to apply the specified settings to a Surface device, to enroll the device in SEMM, and to set a registry key used to identify the enrollment of the device in SEMM.</span></span>
* <span data-ttu-id="5a776-174">**ResetSEMM.ps1** : usa questo script per reimpostare SEMM su un dispositivo Surface, che annulla la registrazione da SEMM e rimuove il controllo sulle impostazioni di Surface UEFI.</span><span class="sxs-lookup"><span data-stu-id="5a776-174">**ResetSEMM.ps1** – Use this script to reset SEMM on a Surface device, which unenrolls it from SEMM and removes the control over Surface UEFI settings.</span></span>

<span data-ttu-id="5a776-175">Gli script di esempio includono esempi di come impostare le impostazioni di Surface UEFI e come controllare le autorizzazioni per tali impostazioni.</span><span class="sxs-lookup"><span data-stu-id="5a776-175">The sample scripts include examples of how to set Surface UEFI settings and how to control permissions to those settings.</span></span> <span data-ttu-id="5a776-176">Queste impostazioni possono essere modificate per proteggere la superficie UEFI e impostare le impostazioni di Surface UEFI in base alle esigenze dell'ambiente.</span><span class="sxs-lookup"><span data-stu-id="5a776-176">These settings can be modified to secure Surface UEFI and set Surface UEFI settings according to the needs of your environment.</span></span> <span data-ttu-id="5a776-177">Le sezioni seguenti di questo articolo illustrano lo script ConfigureSEMM.ps1 ed esplorano le modifiche che è necessario apportare allo script in base alle proprie esigenze.</span><span class="sxs-lookup"><span data-stu-id="5a776-177">The following sections of this article explain the ConfigureSEMM.ps1 script and explore the modifications you need to make to the script to fit your requirements.</span></span>

> [!NOTE]
> <span data-ttu-id="5a776-178">Gli script di gestione configurazione di SEMM e il file di certificato SEMM esportato (PFX) devono essere posizionati nella stessa cartella senza altri file prima di aggiungerli a Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-178">The SEMM Configuration Manager scripts and the exported SEMM certificate file (.pfx) should be placed in the same folder with no other files before they are added to Configuration Manager.</span></span>

### <span data-ttu-id="5a776-179">Specificare i nomi di certificato e pacchetto</span><span class="sxs-lookup"><span data-stu-id="5a776-179">Specify certificate and package names</span></span>

<span data-ttu-id="5a776-180">La prima area dello script che è necessario modificare è la parte che specifica e carica il certificato SEMM e indica anche la versione SurfaceUEFIManager e i nomi per il pacchetto di configurazione di SEMM e il pacchetto di reimpostazione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-180">The first region of the script that you need to modify is the portion that specifies and loads the SEMM certificate, and also indicates SurfaceUEFIManager version, and the names for the SEMM configuration package and SEMM reset package.</span></span> <span data-ttu-id="5a776-181">Il nome del certificato e la versione di SurfaceUEFIManager sono specificati nelle righe da 56 a 73 nello script ConfigureSEMM.ps1.</span><span class="sxs-lookup"><span data-stu-id="5a776-181">The certificate name and SurfaceUEFIManager version are specified on lines 56 through 73 in the ConfigureSEMM.ps1 script.</span></span>

  ```powershell
  56    $WorkingDirPath = split-path -parent $MyInvocation.MyCommand.Definition
  57    $packageRoot = "$WorkingDirPath\Config"
  58    $certName = "FabrikamSEMMSample.pfx"
  59  $DllVersion = "2.26.136.0"
  60
  61  $certNameOnly = [System.IO.Path]::GetFileNameWithoutExtension($certName)
  62  $ProvisioningPackage = $certNameOnly + "ProvisioningPackage.pkg"
  63  $ResetPackage = $certNameOnly + "ResetPackage.pkg"
  64
  65    if (-not (Test-Path $packageRoot))  { New-Item -ItemType Directory -Force -Path $packageRoot }
  66    Copy-Item "$WorkingDirPath\$certName" $packageRoot
  67    
  68    $privateOwnerKey = Join-Path -Path $packageRoot -ChildPath $certName
  69    $ownerPackageName = Join-Path -Path $packageRoot -ChildPath $ProvisioningPackage
  70    $resetPackageName = Join-Path -Path $packageRoot -ChildPath $ResetPackage
  71    
  72    # If your PFX file requires a password then it can be set here, otherwise use a blank string.
  73    $password = "1234" 
  ```

<span data-ttu-id="5a776-182">Sostituire il valore **FabrikamSEMMSample. pfx** per la variabile **$CertName** con il nome del file di certificato SEMM nella riga 58.</span><span class="sxs-lookup"><span data-stu-id="5a776-182">Replace the **FabrikamSEMMSample.pfx** value for the **$certName** variable with the name of your SEMM Certificate file on line 58.</span></span> <span data-ttu-id="5a776-183">Lo script creerà una directory di lavoro (denominata config) nella cartella in cui si trovano gli script e quindi copierà il file del certificato nella directory di lavoro.</span><span class="sxs-lookup"><span data-stu-id="5a776-183">The script will create a working directory (named Config) in the folder where your scripts are located, and then copies the certificate file to this working directory.</span></span>

<span data-ttu-id="5a776-184">Verrà creato anche il pacchetto proprietario e il pacchetto Reimposta nella directory di configurazione e si terrà la configurazione per le impostazioni e le autorizzazioni di Surface UEFI generate dallo script.</span><span class="sxs-lookup"><span data-stu-id="5a776-184">Owner package and reset package will also be created in the Config directory and hold the configuration for Surface UEFI settings and permissions generated by the script.</span></span>

<span data-ttu-id="5a776-185">Nella riga 73 sostituire il valore della variabile **$password** , da **1234** alla password del file di certificato.</span><span class="sxs-lookup"><span data-stu-id="5a776-185">On line 73, replace the value of the **$password** variable, from **1234** to the password for your certificate file.</span></span> <span data-ttu-id="5a776-186">Se non è necessaria una password, eliminare il testo di **1234** .</span><span class="sxs-lookup"><span data-stu-id="5a776-186">If a password is not required, delete the **1234** text.</span></span>

> [!Note]
> <span data-ttu-id="5a776-187">Gli ultimi due caratteri dell'identificazione personale del certificato sono necessari per la registrazione di un dispositivo in SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-187">The last two characters of the certificate thumbprint are required to enroll a device in SEMM.</span></span> <span data-ttu-id="5a776-188">Questo script visualizzerà queste cifre per l'utente, che consente all'utente o al tecnico di registrare queste cifre prima che il sistema venga riavviato per la registrazione del dispositivo in SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-188">This script will display these digits to the user, which allows the user or technician to record these digits before the system reboots to enroll the device in SEMM.</span></span> <span data-ttu-id="5a776-189">Lo script usa il codice seguente, disponibile nelle righe 150-155, per eseguire questa operazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-189">The script uses the following code, found on lines 150-155, to accomplish this.</span></span>

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

Gli amministratori con accesso al file di certificato (con estensione pfx) possono leggere l'identificazione personale in qualsiasi momento aprendo il file pfx in CertMgr. <span data-ttu-id="5a776-191">Per visualizzare l'identificazione personale con CertMgr, seguire questa procedura:</span><span class="sxs-lookup"><span data-stu-id="5a776-191">To view the thumbprint with CertMgr, follow this process:</span></span>

1. <span data-ttu-id="5a776-192">Fare clic con il pulsante destro del mouse sul file PFX e quindi scegliere **Apri**.</span><span class="sxs-lookup"><span data-stu-id="5a776-192">Right-click the .pfx file, and then select **Open**.</span></span>
2. <span data-ttu-id="5a776-193">Espandere la cartella nel riquadro di spostamento.</span><span class="sxs-lookup"><span data-stu-id="5a776-193">Expand the folder in the navigation pane.</span></span>
3. <span data-ttu-id="5a776-194">Selezionare **certificati**.</span><span class="sxs-lookup"><span data-stu-id="5a776-194">Select **Certificates**.</span></span>
4. <span data-ttu-id="5a776-195">Fare clic con il pulsante destro del mouse sul certificato nel riquadro principale e quindi scegliere **Apri**.</span><span class="sxs-lookup"><span data-stu-id="5a776-195">Right-click your certificate in the main pane, and then select **Open**.</span></span>
5. <span data-ttu-id="5a776-196">Selezionare la scheda **Dettagli** .</span><span class="sxs-lookup"><span data-stu-id="5a776-196">Select the **Details** tab.</span></span>
6. <span data-ttu-id="5a776-197">È necessario selezionare solo **tutte le** **proprietà o solo** nel menu a discesa **Mostra** .</span><span class="sxs-lookup"><span data-stu-id="5a776-197">**All** or **Properties Only** must be selected in the **Show** drop-down menu.</span></span>
7. <span data-ttu-id="5a776-198">Selezionare l' **identificazione personale**del campo.</span><span class="sxs-lookup"><span data-stu-id="5a776-198">Select the field **Thumbprint**.</span></span>

> [!NOTE]
> <span data-ttu-id="5a776-199">Il nome del certificato e la password di SEMM devono essere immessi anche in questa sezione dello script ResetSEMM.ps1 per abilitare Configuration Manager per rimuovere SEMM dal dispositivo con l'azione di disinstallazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-199">The SEMM certificate name and password must also be entered in this section of the ResetSEMM.ps1 script to enable Configuration Manager to remove SEMM from the device with the uninstall action.</span></span>

### <span data-ttu-id="5a776-200">Configurare le autorizzazioni</span><span class="sxs-lookup"><span data-stu-id="5a776-200">Configure permissions</span></span>

<span data-ttu-id="5a776-201">La prima area dello script in cui verrà specificata la configurazione per la superficie UEFI è l'area di configurazione **delle autorizzazioni** .</span><span class="sxs-lookup"><span data-stu-id="5a776-201">The first region of the script where you will specify the configuration for Surface UEFI is the **Configure Permissions** region.</span></span> <span data-ttu-id="5a776-202">Questa area inizia alla riga 210 nello script di esempio con il commento **# Configura le autorizzazioni** e continua alla riga 247.</span><span class="sxs-lookup"><span data-stu-id="5a776-202">This region begins at line 210 in the sample script with the comment **# Configure Permissions** and continues to line 247.</span></span> <span data-ttu-id="5a776-203">Il frammento di codice seguente imposta prima di tutto le autorizzazioni per tutte le impostazioni di Surface UEFI in modo che possano essere modificate solo da SEMM, quindi aggiunge autorizzazioni esplicite per consentire all'utente locale di modificare la password di Surface UEFI, il TPM e le telecamere anteriori e posteriori.</span><span class="sxs-lookup"><span data-stu-id="5a776-203">The following code fragment first sets permissions to all Surface UEFI settings so that they may be modified by SEMM only, then adds explicit permissions to allow the local user to modify the Surface UEFI password, TPM, and front and rear cameras.</span></span>

```powershell
210 # Configure Permissions
211 foreach ($uefiV2 IN $surfaceDevices.Values) {
212 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
213 Write-Host "Configuring permissions"
214 Write-Host $Device.Model
215 Write-Host "======================="
216
217 # Here we define which "identities" will be allowed to modify which settings
218 #   PermissionSignerOwner = The primary SEMM enterprise owner identity
219 #   PermissionLocal = The user when booting to the UEFI pre-boot GUI
220 #   PermissionSignerUser, PermissionSignerUser1, PermissionSignerUser2 =
221 #     Additional user identities created so that the signer owner
222 #     can delegate permission control for some settings.
223 $ownerOnly = [Microsoft.Surface.IUefiSetting]::PermissionSignerOwner
224 $ownerAndLocalUser = ([Microsoft.Surface.IUefiSetting]::PermissionSignerOwner -bor [Microsoft.Surface.IUefiSetting]::PermissionLocal)
225 
226 # Make all permissions owner only by default
227 foreach ($setting IN $uefiV2.Settings.Values) {
228 $setting.ConfiguredPermissionFlags = $ownerOnly
229 }
230 
231 # Allow the local user to change their own password
232 $uefiV2.SettingsById[501].ConfiguredPermissionFlags = $ownerAndLocalUser
233
234 Write-Host ""
235  
236 # Create a unique package name based on family and LSV.
237 # We will choose a name that can be parsed by later scripts.
238 $packageName = $uefiV2.SurfaceUefiFamily + "^Permissions^" + $lsv + ".pkg"
239 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
240 
241 # Build and sign the Permission package then save it to a file.
242 $permissionPackageStream =  $uefiV2.BuildAndSignPermissionPackage($privateOwnerKey, $password, "", $null, $lsv)
243 $permissionPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
244 $permissionPackageStream.CopyTo($permissionPackage)
245 $permissionPackage.Close()
246 }
247 }
```

<span data-ttu-id="5a776-204">Ogni variabile **$uefiV 2** identifica un'impostazione UEFI di superficie impostando nome o ID e quindi configura le autorizzazioni su uno dei valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a776-204">Each **$uefiV2** variable identifies a Surface UEFI setting by setting name or ID, and then configures the permissions to one of the following values:</span></span>

* <span data-ttu-id="5a776-205">**$ownerOnly** : l'autorizzazione per la modifica di questa impostazione viene concessa solo a SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-205">**$ownerOnly** – Permission to modify this setting is granted only to SEMM.</span></span>
* <span data-ttu-id="5a776-206">**$ownerAndLocalUser** : l'autorizzazione per la modifica di questa impostazione viene concessa a un utente locale che avvia l'installazione di Surface UEFI, nonché a SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-206">**$ownerAndLocalUser** – Permission to modify this setting is granted to a local user booting to Surface UEFI, as well as to SEMM.</span></span>

<span data-ttu-id="5a776-207">Puoi trovare informazioni sui nomi delle impostazioni disponibili e sugli ID per la superficie UEFI nella sezione [nomi delle impostazioni e ID](#settings-names-and-ids) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-207">You can find information about the available settings names and IDs for Surface UEFI in the [Settings Names and IDs](#settings-names-and-ids) section of this article.</span></span>

### <span data-ttu-id="5a776-208">Configurare le impostazioni</span><span class="sxs-lookup"><span data-stu-id="5a776-208">Configure settings</span></span>

<span data-ttu-id="5a776-209">La seconda area dello script in cui verrà specificata la configurazione per la superficie UEFI è l'area **Configura impostazioni** dello script ConfigureSEMM.ps1, che configura se ogni impostazione è abilitata o disabilitata.</span><span class="sxs-lookup"><span data-stu-id="5a776-209">The second region of the script where you will specify the configuration for Surface UEFI is the **Configure Settings** region of the ConfigureSEMM.ps1 script, which configures whether each setting is enabled or disabled.</span></span> <span data-ttu-id="5a776-210">Lo script di esempio include istruzioni per impostare tutte le impostazioni sui valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="5a776-210">The sample script includes instructions to set all settings to their default values.</span></span> <span data-ttu-id="5a776-211">Lo script fornisce quindi istruzioni esplicite per disabilitare l'avvio di IPv6 per PXE e per non modificare la password di amministratore di Surface UEFI.</span><span class="sxs-lookup"><span data-stu-id="5a776-211">The script then provides explicit instructions to disable IPv6 for PXE Boot and to leave the Surface UEFI Administrator password unchanged.</span></span> <span data-ttu-id="5a776-212">Questa regione può iniziare con il commento **# Configure Settings** alla riga 291 tramite la riga 335 nello script di esempio.</span><span class="sxs-lookup"><span data-stu-id="5a776-212">You can find this region beginning with the **# Configure Settings** comment at line 291 through line 335 in the sample script.</span></span> <span data-ttu-id="5a776-213">L'area geografica viene visualizzata come segue.</span><span class="sxs-lookup"><span data-stu-id="5a776-213">The region appears as follows.</span></span>

```powershell
291 # Configure Settings
292 foreach ($uefiV2 IN $surfaceDevices.Values) {
293 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
294 Write-Host "Configuring settings"
295 Write-Host $Device.Model
296 Write-Host "===================="
297
298 # In this demo, we will start by setting every setting to the default factory setting.
299 # You may want to start by doing this in your scripts
300 # so that every setting gets set to a known state.
301 foreach ($setting IN $uefiV2.Settings.Values) {
302 $setting.ConfiguredValue = $setting.DefaultValue
303 }
304 
305 $EnabledValue = "Enabled"
306 $DisabledValue = "Disabled"
307
308 # If you want to set something to a different value from the default,
309 # here are examples of how to accomplish this.
310 # This disables IPv6 PXE boot by name:
311 $uefiV2.Settings["IPv6 for PXE Boot"].ConfiguredValue = $DisabledValue
312
313 # This disables IPv6 PXE Boot by ID:
314 $uefiV2.SettingsById[400].ConfiguredValue = $DisabledValue
315
316 Write-Host ""
317
318 # If you want to leave the setting unmodified, set it to $null
319 # PowerShell has issues setting things to $null so ClearConfiguredValue()
320 # is supplied to do this explicitly.
321 # Here is an example of leaving the UEFI administrator password as-is,
322 # even after we initially set it to factory default above.
323 $uefiV2.SettingsById[501].ClearConfiguredValue()
324 
325 # Create a unique package name based on family and LSV.
326 # We will choose a name that can be parsed by later scripts.
327 $packageName = $uefiV2.SurfaceUefiFamily + "^Settings^" + $lsv + ".pkg"
328 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
329 
330 # Build and sign the Settings package then save it to a file.
331 $settingsPackageStream =  $uefiV2.BuildAndSignSecuredSettingsPackage($privateOwnerKey, $password, "", $null, $lsv)
332 $settingsPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
333 $settingsPackageStream.CopyTo($settingsPackage)
334 $settingsPackage.Close()
335 }
```

<span data-ttu-id="5a776-214">Come le autorizzazioni impostate nella sezione **Configura autorizzazioni** dello script, la configurazione di ogni impostazione UEFI di Surface viene eseguita definendo la variabile **$uefiV 2** .</span><span class="sxs-lookup"><span data-stu-id="5a776-214">Like the permissions set in the **Configure Permissions** section of the script, the configuration of each Surface UEFI setting is performed by defining the **$uefiV2** variable.</span></span> <span data-ttu-id="5a776-215">Per ogni riga che definisce la variabile **$uefiV 2** , viene identificata un'impostazione UEFI di Surface impostando Name o ID e il valore configurato è impostato su **Enabled** o **disabled**.</span><span class="sxs-lookup"><span data-stu-id="5a776-215">For each line defining the **$uefiV2** variable, a Surface UEFI setting is identified by setting name or ID and the configured value is set to **Enabled** or **Disabled**.</span></span>

<span data-ttu-id="5a776-216">Se non si vuole modificare la configurazione di un'impostazione UEFI di Surface, ad esempio per verificare che la password di amministratore di Surface UEFI non sia cancellata dall'azione di reimpostare tutte le impostazioni di Surface UEFI sul valore predefinito, è possibile usare **ClearConfiguredValue ()** per far sì che questa impostazione non venga modificata.</span><span class="sxs-lookup"><span data-stu-id="5a776-216">If you do not want to alter the configuration of a Surface UEFI setting, for example to ensure that the Surface UEFI administrator password is not cleared by the action of resetting all Surface UEFI settings to their default, you can use **ClearConfiguredValue()** to enforce that this setting will not be altered.</span></span> <span data-ttu-id="5a776-217">Nello script di esempio, questo viene usato in linea 323 per impedire la cancellazione della password di amministratore di Surface UEFI, identificata nello script di esempio dall'ID di impostazione, **501**.</span><span class="sxs-lookup"><span data-stu-id="5a776-217">In the sample script, this is used on line 323 to prevent the clearing of the Surface UEFI Administrator password, identified in the sample script by its setting ID, **501**.</span></span>

<span data-ttu-id="5a776-218">Puoi trovare informazioni sui nomi delle impostazioni disponibili e sugli ID per l'UEFI di Surface nella sezione [nomi delle impostazioni e ID](#settings-names-and-ids) più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-218">You can find information about the available settings names and IDs for Surface UEFI in the [Settings Names and IDs](#settings-names-and-ids) section later in this article.</span></span>

### <span data-ttu-id="5a776-219">Chiave del registro di sistema impostazioni</span><span class="sxs-lookup"><span data-stu-id="5a776-219">Settings registry key</span></span>

<span data-ttu-id="5a776-220">Per identificare i sistemi registrati per Configuration Manager, lo script ConfigureSEMM.ps1 scrive le chiavi del registro di sistema che possono essere usate per identificare i sistemi registrati come installati con lo script di configurazione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-220">To identify enrolled systems for Configuration Manager, the ConfigureSEMM.ps1 script writes registry keys that can be used to identify enrolled systems as having been installed with the SEMM configuration script.</span></span> <span data-ttu-id="5a776-221">Queste chiavi si trovano nella posizione seguente.</span><span class="sxs-lookup"><span data-stu-id="5a776-221">These keys can be found at the following location.</span></span>

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

<span data-ttu-id="5a776-222">Il frammento di codice seguente, disponibile nelle righe 380-477, viene usato per scrivere queste chiavi del registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="5a776-222">The following code fragment, found on lines 380-477, is used to write these registry keys.</span></span>

```powershell
380 # For Endpoint Configuration Manager or other management solutions that wish to know what version is applied, tattoo the LSV and current DateTime (in UTC) to the registry:
381 $UTCDate = (Get-Date).ToUniversalTime().ToString()
382 $certIssuer = $certPrint.Issuer
383 $certSubject = $certPrint.Subject
384 
385 $SurfaceRegKey = "HKLM:\SOFTWARE\Microsoft\Surface\SEMM"
386 New-RegKey $SurfaceRegKey
387 $LSVRegValue = Get-ItemProperty $SurfaceRegKey LSV -ErrorAction SilentlyContinue
388 $DateTimeRegValue = Get-ItemProperty $SurfaceRegKey LastConfiguredUTC -ErrorAction SilentlyContinue
389 $OwnershipSessionIdRegValue = Get-ItemProperty $SurfaceRegKey OwnershipSessionId -ErrorAction SilentlyContinue
390 $PermissionSessionIdRegValue = Get-ItemProperty $SurfaceRegKey PermissionSessionId -ErrorAction SilentlyContinue
391 $SettingsSessionIdRegValue = Get-ItemProperty $SurfaceRegKey SettingsSessionId -ErrorAction SilentlyContinue
392 $IsResetRegValue = Get-ItemProperty $SurfaceRegKey IsReset -ErrorAction SilentlyContinue
393 $certUsedRegValue = Get-ItemProperty $SurfaceRegKey CertName -ErrorAction SilentlyContinue
394 $certIssuerRegValue = Get-ItemProperty $SurfaceRegKey CertIssuer -ErrorAction SilentlyContinue
395 $certSubjectRegValue = Get-ItemProperty $SurfaceRegKey CertSubject -ErrorAction SilentlyContinue
396 
397 
398 If ($LSVRegValue -eq $null)
399 {
400     New-ItemProperty -Path $SurfaceRegKey -Name LSV -PropertyType DWORD -Value $lsv | Out-Null
401 }
402 Else
403 {
404     Set-ItemProperty -Path $SurfaceRegKey -Name LSV -Value $lsv
405 }
406 
407 If ($DateTimeRegValue -eq $null)
408 {
409     New-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -PropertyType String -Value $UTCDate | Out-Null
410 }
411 Else
412 {
413     Set-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -Value $UTCDate
414 }
415 
416 If ($OwnershipSessionIdRegValue -eq $null)
417 {
418     New-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -PropertyType String -Value $ownerSessionIdValue | Out-Null
419 }
420 Else
421 {
422     Set-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -Value $ownerSessionIdValue
423 }
424 
425 If ($PermissionSessionIdRegValue -eq $null)
426 {
427     New-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -PropertyType String -Value $permissionSessionIdValue | Out-Null
428 }
429 Else
430 {
431     Set-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -Value $permissionSessionIdValue
432 }
433 
434 If ($SettingsSessionIdRegValue -eq $null)
435 {
436     New-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -PropertyType String -Value $settingsSessionIdValue | Out-Null
437 }
438 Else
439 {
440     Set-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -Value $settingsSessionIdValue
441 }
442 
443 If ($IsResetRegValue -eq $null)
444 {
445     New-ItemProperty -Path $SurfaceRegKey -Name IsReset -PropertyType DWORD -Value 0 | Out-Null
446 }
447 Else
448 {
449     Set-ItemProperty -Path $SurfaceRegKey -Name IsReset -Value 0
450 }
451 
452 If ($certUsedRegValue -eq $null)
453 {
454     New-ItemProperty -Path $SurfaceRegKey -Name CertName -PropertyType String -Value $certName | Out-Null
455 }
456 Else
457 {
458     Set-ItemProperty -Path $SurfaceRegKey -Name CertName -Value $certName
459 }
460 
461 If ($certIssuerRegValue -eq $null)
462 {
463     New-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -PropertyType String -Value $certIssuer | Out-Null
464 }
465 Else
466 {
467     Set-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -Value $certIssuer
468 }
469 
470 If ($certSubjectRegValue -eq $null)
471 {
472     New-ItemProperty -Path $SurfaceRegKey -Name CertSubject -PropertyType String -Value $certSubject | Out-Null
473 }
474 Else
475 {
476     Set-ItemProperty -Path $SurfaceRegKey -Name CertSubject -Value $certSubject
477 }
```

### <span data-ttu-id="5a776-223">Nomi delle impostazioni e ID</span><span class="sxs-lookup"><span data-stu-id="5a776-223">Settings names and IDs</span></span>

<span data-ttu-id="5a776-224">Per configurare le impostazioni di Surface UEFI o le autorizzazioni per le impostazioni di Surface UEFI, è necessario fare riferimento a ogni impostazione tramite il nome dell'impostazione o l'ID impostazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-224">To configure Surface UEFI settings or permissions for Surface UEFI settings, you must refer to each setting by either its setting name or setting ID.</span></span> <span data-ttu-id="5a776-225">Con ogni nuovo aggiornamento per la superficie UEFI, potrebbero essere aggiunte nuove impostazioni.</span><span class="sxs-lookup"><span data-stu-id="5a776-225">With each new update for Surface UEFI, new settings may be added.</span></span> <span data-ttu-id="5a776-226">Il modo migliore per ottenere un elenco completo delle impostazioni disponibili in un dispositivo Surface, insieme al nome delle impostazioni e agli ID delle impostazioni, consiste nell'usare lo script ShowSettingsOptions.ps1 di SEMM_Powershell.zip in [strumenti di Surface per i download](https://www.microsoft.com/download/details.aspx?id=46703)</span><span class="sxs-lookup"><span data-stu-id="5a776-226">The best way to get a complete list of the settings available on a Surface device, along with the settings name and settings IDs, is to use the ShowSettingsOptions.ps1 script from SEMM_Powershell.zip in [Surface Tools for IT Downloads](https://www.microsoft.com/download/details.aspx?id=46703)</span></span> 

<span data-ttu-id="5a776-227">Il computer in cui è in esecuzione ShowSettingsOptions.ps1 deve avere Microsoft Surface UEFI Manager installato, ma lo script non richiede un dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="5a776-227">The computer where ShowSettingsOptions.ps1 is run must have Microsoft Surface UEFI Manager installed, but the script does not require a Surface device.</span></span>

<span data-ttu-id="5a776-228">Il modo migliore per visualizzare i nomi e gli ID delle impostazioni più recenti per i dispositivi consiste nell'usare lo script ConfigureSEMM.ps1 o ConfigureSEMM- <device name> . ps1 dall'SEMM_Powershell.zip in [strumenti di Surface per il download](https://www.microsoft.com/download/details.aspx?id=46703).</span><span class="sxs-lookup"><span data-stu-id="5a776-228">The best way to view the most current Setting names and IDs for devices is to use the ConfigureSEMM.ps1 script or the ConfigureSEMM - <device name>.ps1 from the SEMM_Powershell.zip in [Surface Tools for IT Downloads](https://www.microsoft.com/download/details.aspx?id=46703).</span></span>

<span data-ttu-id="5a776-229">L'impostazione di nomi e ID per tutti i dispositivi può essere visualizzata nello script ConfigureSEMM.ps1.</span><span class="sxs-lookup"><span data-stu-id="5a776-229">Setting names and IDs for all devices can be seen in the ConfigureSEMM.ps1 script.</span></span>

<span data-ttu-id="5a776-230">L'impostazione di nomi e ID per dispositivi specifici può essere visualizzata negli script ConfigureSEMM- <device name> . ps1.</span><span class="sxs-lookup"><span data-stu-id="5a776-230">Setting names and IDs for specific devices can be seen in the ConfigureSEMM - <device name>.ps1 scripts.</span></span> 

## <span data-ttu-id="5a776-231">Distribuire script di gestione configurazione di SEMM</span><span class="sxs-lookup"><span data-stu-id="5a776-231">Deploy SEMM Configuration Manager scripts</span></span>

<span data-ttu-id="5a776-232">Dopo aver preparato gli script per la configurazione e l'abilitazione di SEMM nel dispositivo client, il passaggio successivo consiste nell'aggiungere questi script come applicazione in Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-232">After your scripts are prepared to configure and enable SEMM on the client device, the next step is to add these scripts as an application in Configuration Manager.</span></span> <span data-ttu-id="5a776-233">Prima di aprire Configuration Manager, assicurarsi che i file seguenti si trovino in una cartella condivisa che non includa altri file:</span><span class="sxs-lookup"><span data-stu-id="5a776-233">Before you open Configuration Manager, ensure that the following files are in a shared folder that does not include other files:</span></span>

* <span data-ttu-id="5a776-234">ConfigureSEMM.ps1</span><span class="sxs-lookup"><span data-stu-id="5a776-234">ConfigureSEMM.ps1</span></span>
* <span data-ttu-id="5a776-235">ResetSEMM.ps1</span><span class="sxs-lookup"><span data-stu-id="5a776-235">ResetSEMM.ps1</span></span>
* <span data-ttu-id="5a776-236">Il certificato di SEMM (ad esempio SEMMCertificate. pfx)</span><span class="sxs-lookup"><span data-stu-id="5a776-236">Your SEMM certificate (for example SEMMCertificate.pfx)</span></span>

<span data-ttu-id="5a776-237">Gli script di gestione configurazione di SEMM verranno aggiunti a Configuration Manager come applicazione script.</span><span class="sxs-lookup"><span data-stu-id="5a776-237">The SEMM Configuration Manager scripts will be added to Configuration Manager as a script application.</span></span> <span data-ttu-id="5a776-238">Il comando per installare SEMM con ConfigureSEMM.ps1 è il seguente.</span><span class="sxs-lookup"><span data-stu-id="5a776-238">The command to install SEMM with ConfigureSEMM.ps1 is as follows.</span></span>

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

<span data-ttu-id="5a776-239">Il comando per disinstallare SEMM con ResetSEMM.ps1 è il seguente.</span><span class="sxs-lookup"><span data-stu-id="5a776-239">The command to uninstall SEMM with ResetSEMM.ps1 is as follows.</span></span>

`Powershell.exe -file ".\ResetSEMM.ps1"`

<span data-ttu-id="5a776-240">Per aggiungere gli script di gestione configurazione di SEMM a Configuration Manager come applicazione, usare il processo seguente:</span><span class="sxs-lookup"><span data-stu-id="5a776-240">To add the SEMM Configuration Manager scripts to Configuration Manager as an application, use the following process:</span></span>

1. <span data-ttu-id="5a776-241">Avviare la creazione guidata applicazione usando il passaggio 1 al passaggio 5 dalla sezione [Distribuisci Microsoft Surface UEFI Manager](#deploy-microsoft-surface-uefi-manager) in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-241">Start the Create Application Wizard using Step 1 through Step 5 from the [Deploy Microsoft Surface UEFI Manager](#deploy-microsoft-surface-uefi-manager) section earlier in this article.</span></span>

2. <span data-ttu-id="5a776-242">Procedere con la procedura guidata Crea applicazione come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5a776-242">Proceed through The Create Application Wizard as follows:</span></span>

   - <span data-ttu-id="5a776-243">**Generale** : selezionare **specifica manualmente le informazioni sull'applicazione**e quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5a776-243">**General** – Select **Manually specify the application information**, and then select **Next**.</span></span>

   - <span data-ttu-id="5a776-244">**Informazioni generali** : immettere un nome per l'applicazione (ad esempio SEMM) e tutte le altre informazioni desiderate, come Publisher, versione o commenti in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-244">**General Information** – Enter a name for the application (for example SEMM) and any other information you want such as publisher, version, or comments on this page.</span></span> <span data-ttu-id="5a776-245">Selezionare **Avanti** per procedere.</span><span class="sxs-lookup"><span data-stu-id="5a776-245">Select **Next** to proceed.</span></span>

   - <span data-ttu-id="5a776-246">**Catalogo applicazioni** : i campi in questa pagina possono essere lasciati con i relativi valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="5a776-246">**Application Catalog** – The fields on this page can be left with their default values.</span></span> <span data-ttu-id="5a776-247">Seleziona **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="5a776-247">Select **Next**.</span></span>

   - <span data-ttu-id="5a776-248">**Tipi di distribuzione** : selezionare **Aggiungi** per avviare la procedura guidata Crea tipo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5a776-248">**Deployment Types** – Select **Add** to start the Create Deployment Type Wizard.</span></span>

   - <span data-ttu-id="5a776-249">Procedere con i passaggi della procedura guidata Crea tipo di distribuzione, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="5a776-249">Proceed through the steps of the Create Deployment Type Wizard, as follows:</span></span>

     * <span data-ttu-id="5a776-250">**Generale** : selezionare **script Installer** dal menu a discesa **tipo** .</span><span class="sxs-lookup"><span data-stu-id="5a776-250">**General** – Select **Script Installer** from the **Type** drop-down menu.</span></span> <span data-ttu-id="5a776-251">L'opzione **specifica manualmente le informazioni sul tipo di distribuzione** verrà selezionata automaticamente.</span><span class="sxs-lookup"><span data-stu-id="5a776-251">The **Manually specify the deployment type information** option will automatically be selected.</span></span> <span data-ttu-id="5a776-252">Selezionare **Avanti** per procedere.</span><span class="sxs-lookup"><span data-stu-id="5a776-252">Select **Next** to proceed.</span></span>
     * <span data-ttu-id="5a776-253">**Informazioni generali** : immettere un nome per il tipo di distribuzione, ad esempio gli script di configurazione di SEMM, quindi scegliere **Avanti** per continuare.</span><span class="sxs-lookup"><span data-stu-id="5a776-253">**General Information** – Enter a name for the deployment type (for example SEMM Configuration Scripts), and then select **Next** to continue.</span></span>
     * <span data-ttu-id="5a776-254">**Contenuto** : selezionare **Sfoglia** accanto al campo **percorso contenuto** e quindi selezionare la cartella in cui si trovano gli script di gestione configurazione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-254">**Content** – Select **Browse** next to the **Content Location** field, and then select the folder where your SEMM Configuration Manager scripts are located.</span></span> <span data-ttu-id="5a776-255">Nel campo **programma di installazione** Digitare il [comando di installazione](#deploy-semm-configuration-manager-scripts) trovato in precedenza in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-255">In the **Installation Program** field, type the [installation command](#deploy-semm-configuration-manager-scripts) found earlier in this article.</span></span> <span data-ttu-id="5a776-256">Nel campo **Disinstalla programma** immettere il comando di [disinstallazione](#deploy-semm-configuration-manager-scripts) disponibile in precedenza in questo articolo (illustrato nella figura 2).</span><span class="sxs-lookup"><span data-stu-id="5a776-256">In the **Uninstall Program** field, enter the [uninstallation command](#deploy-semm-configuration-manager-scripts) found earlier in this article (shown in Figure 2).</span></span> <span data-ttu-id="5a776-257">Selezionare **Avanti** per tornare alla pagina successiva.</span><span class="sxs-lookup"><span data-stu-id="5a776-257">Select **Next** to move to the next page.</span></span>
    
     ![Impostare gli script di gestione configurazione di SEMM come comandi di installazione e disinstallazione](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *<span data-ttu-id="5a776-259">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="5a776-259">Figure 2.</span></span> <span data-ttu-id="5a776-260">Impostare gli script di gestione configurazione di SEMM come comandi di installazione e disinstallazione</span><span class="sxs-lookup"><span data-stu-id="5a776-260">Set the SEMM Configuration Manager scripts as the install and uninstall commands</span></span>*

     * <span data-ttu-id="5a776-261">**Metodo di rilevamento** : selezionare **Aggiungi clausola** per aggiungere la regola di rilevamento della chiave del registro di sistema di SEMM Configuration Manager script.</span><span class="sxs-lookup"><span data-stu-id="5a776-261">**Detection Method** – Select **Add Clause** to add the SEMM Configuration Manager script registry key detection rule.</span></span> <span data-ttu-id="5a776-262">Viene visualizzata la finestra della **regola di rilevamento** , come illustrato nella figura 3.</span><span class="sxs-lookup"><span data-stu-id="5a776-262">The **Detection Rule** window is displayed, as shown in Figure 3.</span></span> <span data-ttu-id="5a776-263">Usa le impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a776-263">Use the following settings:</span></span>

       - <span data-ttu-id="5a776-264">Selezionare **Registro di sistema** dal menu a discesa **tipo di impostazione** .</span><span class="sxs-lookup"><span data-stu-id="5a776-264">Select **Registry** from the **Setting Type** drop-down menu.</span></span>
       - <span data-ttu-id="5a776-265">Selezionare **HKEY_LOCAL_MACHINE** dal menu a discesa **hive** .</span><span class="sxs-lookup"><span data-stu-id="5a776-265">Select **HKEY_LOCAL_MACHINE** from the **Hive** drop-down menu.</span></span>
       - <span data-ttu-id="5a776-266">Immettere **SOFTWARE\Microsoft\Surface\SEMM** nel campo **chiave** .</span><span class="sxs-lookup"><span data-stu-id="5a776-266">Enter **SOFTWARE\Microsoft\Surface\SEMM** in the **Key** field.</span></span>
       - <span data-ttu-id="5a776-267">Immettere **CertName** nel campo **valore** .</span><span class="sxs-lookup"><span data-stu-id="5a776-267">Enter **CertName** in the **Value** field.</span></span>
       - <span data-ttu-id="5a776-268">Selezionare **stringa** dal menu a discesa **tipo di dati** .</span><span class="sxs-lookup"><span data-stu-id="5a776-268">Select **String** from the **Data Type** drop-down menu.</span></span>
       - <span data-ttu-id="5a776-269">Selezionare l' **impostazione di questo registro di sistema deve soddisfare la regola seguente per indicare la presenza del pulsante applicazione** .</span><span class="sxs-lookup"><span data-stu-id="5a776-269">Select the **This registry setting must satisfy the following rule to indicate the presence of this application** button.</span></span>
       - <span data-ttu-id="5a776-270">Immettere il nome del certificato immesso nella riga 58 dello script nel campo **valore** .</span><span class="sxs-lookup"><span data-stu-id="5a776-270">Enter the name of the certificate you entered in line 58 of the script in the **Value** field.</span></span>
       - <span data-ttu-id="5a776-271">Selezionare **OK** per chiudere la finestra della **regola di rilevamento** .</span><span class="sxs-lookup"><span data-stu-id="5a776-271">Select **OK** to close the **Detection Rule** window.</span></span>

     ![Usare una chiave del registro di sistema per identificare i dispositivi registrati in SEMM](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *<span data-ttu-id="5a776-273">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="5a776-273">Figure 3.</span></span> <span data-ttu-id="5a776-274">Usare una chiave del registro di sistema per identificare i dispositivi registrati in SEMM</span><span class="sxs-lookup"><span data-stu-id="5a776-274">Use a registry key to identify devices enrolled in SEMM</span></span>*

     * <span data-ttu-id="5a776-275">Selezionare **Avanti** per passare alla pagina successiva.</span><span class="sxs-lookup"><span data-stu-id="5a776-275">Select **Next** to proceed to the next page.</span></span>
     
     * <span data-ttu-id="5a776-276">**Esperienza utente** : selezionare **Installa per sistema** dal menu a discesa **comportamento di installazione** .</span><span class="sxs-lookup"><span data-stu-id="5a776-276">**User Experience** – Select **Install for system** from the **Installation Behavior** drop-down menu.</span></span> <span data-ttu-id="5a776-277">Se si vuole che gli utenti registrino e immettino l'identificazione personale del certificato, abbandonare il requisito di accesso **solo quando l'utente ha effettuato**l'accesso.</span><span class="sxs-lookup"><span data-stu-id="5a776-277">If you want your users to record and enter the certificate thumbprint themselves, leave the logon requirement set to **Only when a user is logged on**.</span></span> <span data-ttu-id="5a776-278">Se si vuole che gli amministratori immettino l'identificazione personale per gli utenti e che gli utenti non debbano vedere l'identificazione personale, selezionare **se un utente ha effettuato** l'accesso dal menu a discesa **requisiti di accesso** .</span><span class="sxs-lookup"><span data-stu-id="5a776-278">If you want your administrators to enter the thumbprint for users and the users do not need to see the thumbprint, select **Whether or not a user is logged on** from the **Logon Requirement** drop-down menu.</span></span>

     * <span data-ttu-id="5a776-279">**Requisiti** : lo script ConfigureSEMM.ps1 verifica automaticamente che il dispositivo sia un dispositivo Surface prima di provare a abilitare SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-279">**Requirements** – The ConfigureSEMM.ps1 script automatically verifies that the device is a Surface device before attempting to enable SEMM.</span></span> <span data-ttu-id="5a776-280">Tuttavia, se intendi distribuire questa applicazione di script a una raccolta con dispositivi diversi da quelli da gestire con SEMM, puoi aggiungere requisiti per verificare che l'applicazione venga eseguita solo su dispositivi o dispositivi di Surface che intendi usare con SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-280">However, if you intend to deploy this script application to a collection with devices other than those to be managed with SEMM, you could add requirements here to ensure this application would run only on Surface devices or devices you intend to manage with SEMM.</span></span> <span data-ttu-id="5a776-281">Selezionare **Avanti** per continuare.</span><span class="sxs-lookup"><span data-stu-id="5a776-281">Select **Next** to continue.</span></span>
     
     * <span data-ttu-id="5a776-282">**Dipendenze** : selezionare **Aggiungi** per aprire la finestra **Aggiungi dipendenza** .</span><span class="sxs-lookup"><span data-stu-id="5a776-282">**Dependencies** – Select **Add** to open the **Add Dependency** window.</span></span>

       * <span data-ttu-id="5a776-283">Selezionare **Aggiungi** per aprire la finestra **specifica applicazione richiesta** .</span><span class="sxs-lookup"><span data-stu-id="5a776-283">Select **Add** to open the **Specify Required Application** window.</span></span>

          - <span data-ttu-id="5a776-284">Immettere un nome per le dipendenze SEMM nel campo **nome gruppo di dipendenze** (ad esempio, *assembly SEMM*).</span><span class="sxs-lookup"><span data-stu-id="5a776-284">Enter a name for the SEMM dependencies in the **Dependency Group Name** field (for example, *SEMM Assemblies*).</span></span>

          - <span data-ttu-id="5a776-285">Selezionare **Microsoft Surface UEFI Manager** dall'elenco delle **applicazioni disponibili** e dal tipo di distribuzione MSI, quindi scegliere **OK** per chiudere la finestra **specifica applicazione necessaria** .</span><span class="sxs-lookup"><span data-stu-id="5a776-285">Select **Microsoft Surface UEFI Manager** from the list of **Available Applications** and the MSI deployment type, and then select **OK** to close the **Specify Required Application** window.</span></span>
          
         *   <span data-ttu-id="5a776-286">Selezionare la casella di controllo **installazione automatica** se si vuole che Microsoft Surface UEFI Manager sia installato automaticamente nei dispositivi quando si tenta di abilitare SEMM con gli script di Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-286">Keep the **Auto Install** check box selected if you want Microsoft Surface UEFI Manager installed automatically on devices when you attempt to enable SEMM with the Configuration Manager scripts.</span></span> <span data-ttu-id="5a776-287">Selezionare **OK** per chiudere la finestra **Aggiungi dipendenza** .</span><span class="sxs-lookup"><span data-stu-id="5a776-287">Select **OK** to close the **Add Dependency** window.</span></span>

     * <span data-ttu-id="5a776-288">Selezionare **Avanti** per procedere.</span><span class="sxs-lookup"><span data-stu-id="5a776-288">Select **Next** to proceed.</span></span>
     
     * <span data-ttu-id="5a776-289">**Riepilogo** : le informazioni immesse in tutta la procedura guidata Crea tipo di distribuzione vengono visualizzate in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-289">**Summary** – The information you have entered throughout the Create Deployment Type wizard is displayed on this page.</span></span> <span data-ttu-id="5a776-290">Selezionare **Avanti** per confermare le selezioni.</span><span class="sxs-lookup"><span data-stu-id="5a776-290">Select **Next** to confirm your selections.</span></span>
     
     * <span data-ttu-id="5a776-291">**Progress** : viene visualizzata una barra di stato e uno stato come tipo di distribuzione per l'applicazione di script SEMM in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-291">**Progress** – A progress bar and status as the deployment type is added for the SEMM script application is displayed on this page.</span></span>
     
     * <span data-ttu-id="5a776-292">**Completamento** : la conferma della creazione del tipo di distribuzione viene visualizzata al termine del processo.</span><span class="sxs-lookup"><span data-stu-id="5a776-292">**Completion** – Confirmation of the deployment type creation is displayed when the process is complete.</span></span> <span data-ttu-id="5a776-293">Selezionare **Chiudi** per completare la procedura guidata Crea tipo di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="5a776-293">Select **Close** to finish the Create Deployment Type Wizard.</span></span>

   - <span data-ttu-id="5a776-294">**Riepilogo** : vengono visualizzate le informazioni immesse in tutta la creazione guidata applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-294">**Summary** – The information that you entered throughout the Create Application Wizard is displayed.</span></span> <span data-ttu-id="5a776-295">Selezionare **Avanti** per creare l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-295">Select **Next** to create the application.</span></span>

   - <span data-ttu-id="5a776-296">**Progress** : viene visualizzata una barra di stato e uno stato quando l'applicazione viene aggiunta alla raccolta software in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="5a776-296">**Progress** – A progress bar and status as the application is added to the Software Library is displayed on this page.</span></span>

   - <span data-ttu-id="5a776-297">**Completamento** : la conferma della corretta creazione dell'applicazione viene visualizzata al termine del processo di creazione dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-297">**Completion** – Confirmation of the successful application creation is displayed when the application creation process is complete.</span></span> <span data-ttu-id="5a776-298">Selezionare **Chiudi** per completare la creazione guidata applicazione.</span><span class="sxs-lookup"><span data-stu-id="5a776-298">Select **Close** to finish the Create Application Wizard.</span></span>

<span data-ttu-id="5a776-299">Dopo che l'applicazione script è disponibile nella raccolta software di Configuration Manager, è possibile distribuire e distribuire SEMM usando gli script preparati per i dispositivi o le raccolte.</span><span class="sxs-lookup"><span data-stu-id="5a776-299">After the script application is available in the Software Library of Configuration Manager, you can distribute and deploy SEMM using the scripts you prepared to devices or collections.</span></span> <span data-ttu-id="5a776-300">Se gli assembly di Microsoft Surface UEFI Manager sono stati configurati come una dipendenza che verrà installata automaticamente, è possibile distribuire SEMM in un singolo passaggio.</span><span class="sxs-lookup"><span data-stu-id="5a776-300">If you have configured the Microsoft Surface UEFI Manager assemblies as a dependency that will be automatically installed, you can deploy SEMM in a single step.</span></span> <span data-ttu-id="5a776-301">Se gli assembly non sono stati configurati come dipendenza, è necessario che siano installati nei dispositivi che si vuole gestire prima di abilitare SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-301">If you have not configured the assemblies as a dependency, they must be installed on the devices you intend to manage before you enable SEMM.</span></span>

<span data-ttu-id="5a776-302">Quando si distribuisce SEMM con questa applicazione script e con una configurazione visibile per l'utente finale, verrà avviato lo script di PowerShell e l'identificazione personale del certificato verrà visualizzata dalla finestra di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a776-302">When you deploy SEMM using this script application and with a configuration that is visible to the end user, the PowerShell script will start and the thumbprint for the certificate will be displayed by the PowerShell window.</span></span> <span data-ttu-id="5a776-303">Gli utenti possono registrare questa identificazione personale e immetterla quando viene richiesto dall'UEFI di Surface dopo il riavvio del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a776-303">You can have your users record this thumbprint and enter it when prompted by Surface UEFI after the device reboots.</span></span>

<span data-ttu-id="5a776-304">In alternativa, puoi configurare l'installazione dell'applicazione per il riavvio automatico e per l'installazione invisibile all'utente.</span><span class="sxs-lookup"><span data-stu-id="5a776-304">Alternatively, you can configure the application installation to reboot automatically and to install invisibly to the user.</span></span> <span data-ttu-id="5a776-305">In questo scenario, a un tecnico verrà richiesto di immettere l'identificazione personale in ogni dispositivo durante il riavvio.</span><span class="sxs-lookup"><span data-stu-id="5a776-305">In this scenario, a technician will be required to enter the thumbprint on each device as it reboots.</span></span> <span data-ttu-id="5a776-306">Qualsiasi tecnico con accesso al file di certificato può leggere l'identificazione personale visualizzando il certificato con CertMgr.</span><span class="sxs-lookup"><span data-stu-id="5a776-306">Any technician with access to the certificate file can read the thumbprint by viewing the certificate with CertMgr.</span></span> <span data-ttu-id="5a776-307">Le istruzioni per la visualizzazione dell'identificazione personale con CertMgr si trovano nella sezione [creare o modificare gli script di gestione configurazione di SEMM](#create-or-modify-the-semm-configuration-manager-scripts) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="5a776-307">Instructions for viewing the thumbprint with CertMgr are in the [Create or modify the SEMM Configuration Manager scripts](#create-or-modify-the-semm-configuration-manager-scripts) section of this article.</span></span>

<span data-ttu-id="5a776-308">La rimozione di SEMM da un dispositivo distribuito con Configuration Manager tramite questi script è facile come disinstallare l'applicazione con Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5a776-308">Removal of SEMM from a device deployed with Configuration Manager using these scripts is as easy as uninstalling the application with Configuration Manager.</span></span> <span data-ttu-id="5a776-309">Questa azione avvia lo script ResetSEMM.ps1 e disiscrive correttamente il dispositivo con lo stesso file di certificato usato durante la distribuzione di SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-309">This action starts the ResetSEMM.ps1 script and properly unenrolls the device with the same certificate file that was used during the deployment of SEMM.</span></span>

> [!NOTE]
> <span data-ttu-id="5a776-310">Microsoft Surface consiglia di creare pacchetti di reimpostazione solo quando è necessario annullare la registrazione di un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a776-310">Microsoft Surface recommends that you create reset packages only when you need to unenroll a device.</span></span> <span data-ttu-id="5a776-311">Questi pacchetti di reimpostazione sono in genere validi per un solo dispositivo, identificato dal numero seriale.</span><span class="sxs-lookup"><span data-stu-id="5a776-311">These reset packages are typically valid for only one device, identified by its serial number.</span></span> <span data-ttu-id="5a776-312">Puoi tuttavia creare un pacchetto di reimpostazione universale che funzioni per qualsiasi dispositivo registrato in SEMM con questo certificato.</span><span class="sxs-lookup"><span data-stu-id="5a776-312">You can, however, create a universal reset package that would work for any device enrolled in SEMM with this certificate.</span></span>
> 
> <span data-ttu-id="5a776-313">Ti consigliamo vivamente di proteggere il pacchetto di reimpostazione universale con la massima cautela del certificato usato per la registrazione dei dispositivi in SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-313">We strongly recommend that you protect your universal reset package as carefully as the certificate you used to enroll devices in SEMM.</span></span> <span data-ttu-id="5a776-314">Tieni presente che, proprio come il certificato stesso, questo pacchetto di reimpostazione universale può essere usato per annullare la registrazione dei dispositivi Surface della tua organizzazione da SEMM.</span><span class="sxs-lookup"><span data-stu-id="5a776-314">Please remember that, just like the certificate itself, this universal reset package can be used to unenroll any of your organization’s Surface devices from SEMM.</span></span>
> 
> <span data-ttu-id="5a776-315">Quando si installa un pacchetto di reimpostazione, il valore supportato più basso (LSV) viene reimpostato su un valore pari a 1.</span><span class="sxs-lookup"><span data-stu-id="5a776-315">When you install a reset package, the Lowest Supported Value (LSV) is reset to a value of 1.</span></span> <span data-ttu-id="5a776-316">Puoi rieseguire la registrazione di un dispositivo usando un pacchetto di configurazione esistente.</span><span class="sxs-lookup"><span data-stu-id="5a776-316">You can reenroll a device by using an existing configuration package.</span></span> <span data-ttu-id="5a776-317">Il dispositivo chiederà l'identificazione personale del certificato prima che venga eseguita la proprietà.</span><span class="sxs-lookup"><span data-stu-id="5a776-317">The device will prompt for the certificate thumbprint before ownership is taken.</span></span>
> 
> <span data-ttu-id="5a776-318">Per questo motivo, la riregistrazione di un dispositivo in SEMM richiederà la creazione e l'installazione di un nuovo pacchetto nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5a776-318">For this reason, the reenrollment of a device in SEMM would require a new package to be created and installed on that device.</span></span> <span data-ttu-id="5a776-319">Poiché questa azione è una nuova registrazione e non una modifica della configurazione in un dispositivo già registrato in SEMM, il dispositivo chiederà l'identificazione personale del certificato prima che venga eseguita la proprietà.</span><span class="sxs-lookup"><span data-stu-id="5a776-319">Because this action is a new enrollment and not a change in configuration on a device already enrolled in SEMM, the device will prompt for the certificate thumbprint before ownership is taken.</span></span>

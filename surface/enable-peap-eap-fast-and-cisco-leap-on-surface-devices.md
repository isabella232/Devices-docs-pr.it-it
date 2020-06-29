---
title: Abilitare PEAP, EAP-FAST e Cisco LEAP in dispositivi Surface (Surface)
description: Scopri come abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nel tuo dispositivo Surface.
ms.assetid: A281EFA3-1552-467D-8A21-EB151E58856D
ms.reviewer: ''
manager: laurawi
keywords: rete, wireless, dispositivo, distribuire, autenticazione, protocollo
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 1a9bef0a6e0bfdd4bede1b508b4013fd14e1a0bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833495"
---
# <span data-ttu-id="528cf-104">Abilitare PEAP, EAP-FAST e Cisco LEAP in dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="528cf-104">Enable PEAP, EAP-FAST, and Cisco LEAP on Surface devices</span></span>


<span data-ttu-id="528cf-105">Scopri come abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nel tuo dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="528cf-105">Find out how to enable support for PEAP, EAP-FAST, or Cisco LEAP protocols on your Surface device.</span></span>

<span data-ttu-id="528cf-106">Se usi PEAP, EAP-FAST o Cisco LEAP nella tua rete aziendale, probabilmente sai già che questi tre protocolli di autenticazione wireless non sono supportati dai dispositivi Surface in modo predefinito.</span><span class="sxs-lookup"><span data-stu-id="528cf-106">If you use PEAP, EAP-FAST, or Cisco LEAP in your enterprise network, you probably already know that these three wireless authentication protocols are not supported by Surface devices out of the box.</span></span> <span data-ttu-id="528cf-107">Alcuni utenti potrebbero rendersi conto del mancato supporto quando tentano di connettersi alla rete wireless, mentre altri potrebbero scoprirlo quando non riescono ad accedere alle risorse all'interno della rete, ad esempio a condivisioni di file e siti interni.</span><span class="sxs-lookup"><span data-stu-id="528cf-107">Some users may discover this when they attempt to connect to your wireless network; others may discover it when they are unable to gain access to resources inside the network, like file shares and internal sites.</span></span> <span data-ttu-id="528cf-108">Per altre informazioni, vedi [Extensible Authentication Protocol](https://technet.microsoft.com/network/bb643147).</span><span class="sxs-lookup"><span data-stu-id="528cf-108">For more information, see [Extensible Authentication Protocol](https://technet.microsoft.com/network/bb643147).</span></span>

<span data-ttu-id="528cf-109">Puoi aggiungere il supporto per ogni protocollo eseguendo un piccolo pacchetto MSI da una chiavetta USB o una condivisione di file.</span><span class="sxs-lookup"><span data-stu-id="528cf-109">You can add support for each protocol by executing a small MSI package from a USB stick or from a file share.</span></span> <span data-ttu-id="528cf-110">Per le organizzazioni che desiderano abilitare il supporto EAP nei dispositivi di Surface, il formato del pacchetto MSI supporta la distribuzione con molti strumenti di gestione e distribuzione, come Microsoft Deployment Toolkit (MDT) e Microsoft endpoint Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="528cf-110">For organizations that want to enable EAP support on their Surface devices, the MSI package format supports deployment with many management and deployment tools, like the Microsoft Deployment Toolkit (MDT) and Microsoft Endpoint Configuration Manager.</span></span>

## <a href="" id="download-peap--eap-fast--or-cisco-leap-installation-files--"></a><span data-ttu-id="528cf-111">Scaricare i file di installazione per PEAP, EAP-FAST o Cisco LEAP</span><span class="sxs-lookup"><span data-stu-id="528cf-111">Download PEAP, EAP-FAST, or Cisco LEAP installation files</span></span>


<span data-ttu-id="528cf-112">Puoi scaricare i file di installazione MSI per PEAP, EAP-FAST o Cisco LEAP in un singolo file di archivio ZIP dall'Area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="528cf-112">You can download the MSI installation files for PEAP, EAP-FAST, or Cisco LEAP in a single zip archive file from the Microsoft Download Center.</span></span> <span data-ttu-id="528cf-113">Per scaricare questo file, passa alla pagina degli [strumenti di Surface per l'IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft, fai clic su **Download** e quindi seleziona il file **Cisco EAP-Supplicant Installer.zip**.</span><span class="sxs-lookup"><span data-stu-id="528cf-113">To download this file, go to the [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) page on the Microsoft Download Center, click **Download**, and then select the **Cisco EAP-Supplicant Installer.zip** file.</span></span>

## <span data-ttu-id="528cf-114">Distribuire PEAP, EAP-FAST o Cisco LEAP con MDT</span><span class="sxs-lookup"><span data-stu-id="528cf-114">Deploy PEAP, EAP-FAST, or Cisco LEAP with MDT</span></span>


<span data-ttu-id="528cf-115">Se stai già eseguendo una distribuzione di Windows nei dispositivi Surface nella tua organizzazione, l'aggiunta dei file di installazione per ogni protocollo alla condivisione di distribuzione e la configurazione dell'installazione automatica durante la distribuzione sono operazioni rapide e semplici.</span><span class="sxs-lookup"><span data-stu-id="528cf-115">If you are already performing a Windows deployment to Surface devices in your organization, it is quick and easy to add the installation files for each protocol to your deployment share and configure automatic installation during deployment.</span></span> <span data-ttu-id="528cf-116">Puoi addirittura configurare una sequenza di attività per l'aggiornamento dei dispositivi Surface distribuiti in precedenza per offrire supporto per questi protocolli usando lo stesso processo.</span><span class="sxs-lookup"><span data-stu-id="528cf-116">You can even configure a task sequence that updates previously deployed Surface devices to provide support for these protocols using the same process.</span></span>

<span data-ttu-id="528cf-117">Per abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nei nuovi dispositivi Surface distribuiti, segui questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="528cf-117">To enable support for PEAP, EAP-FAST, or Cisco LEAP on newly deployed Surface devices, follow these steps:</span></span>

1.  <span data-ttu-id="528cf-118">Scarica ed estrai i file di installazione per ogni protocollo in cartelle separate in un percorso facilmente accessibile.</span><span class="sxs-lookup"><span data-stu-id="528cf-118">Download and extract the installation files for each protocol to separate folders in an easily accessible location.</span></span>

2.  <span data-ttu-id="528cf-119">Apri MDT Deployment Workbench ed espandi la condivisione di distribuzione alla cartella **Applications**.</span><span class="sxs-lookup"><span data-stu-id="528cf-119">Open the MDT Deployment Workbench and expand your deployment share to the **Applications** folder.</span></span>

3.  <span data-ttu-id="528cf-120">Seleziona **New Application** nel riquadro **Action**.</span><span class="sxs-lookup"><span data-stu-id="528cf-120">Select **New Application** from the **Action** pane.</span></span>

4.  <span data-ttu-id="528cf-121">Scegli **Application with source files** per copiare i file MSI nella condivisione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="528cf-121">Choose **Application with source files** to copy the MSI files into the Deployment Share.</span></span>

5.  <span data-ttu-id="528cf-122">Seleziona la cartella che hai creato nel passaggio 1 per il protocollo desiderato.</span><span class="sxs-lookup"><span data-stu-id="528cf-122">Select the folder you created in step 1 for the desired protocol.</span></span>

6.  <span data-ttu-id="528cf-123">Assegna un nome alla cartella nella condivisione di distribuzione in cui verranno archiviati i file di installazione.</span><span class="sxs-lookup"><span data-stu-id="528cf-123">Name the folder in the deployment share where the installation files will be stored.</span></span>

7.  <span data-ttu-id="528cf-124">Specifica la riga di comando per distribuire l'applicazione:</span><span class="sxs-lookup"><span data-stu-id="528cf-124">Specify the command line to deploy the application:</span></span>

    -   <span data-ttu-id="528cf-125">Per PEAP usa **EAP-PEAP.msi /qn /norestart**.</span><span class="sxs-lookup"><span data-stu-id="528cf-125">For PEAP use **EAP-PEAP.msi /qn /norestart**.</span></span>

    -   <span data-ttu-id="528cf-126">Per LEAP usa **EAP-LEAP.msi /qn /norestart**.</span><span class="sxs-lookup"><span data-stu-id="528cf-126">For LEAP use **EAP-LEAP.msi /qn /norestart**.</span></span>

    -   <span data-ttu-id="528cf-127">Per EAP-FAST usa **EAP-FAST.msi /qn /norestart**.</span><span class="sxs-lookup"><span data-stu-id="528cf-127">For EAP-FAST use **EAP-FAST.msi /qn /norestart**.</span></span>

8.  <span data-ttu-id="528cf-128">Usa le opzioni predefinite per completare la procedura guidata New Application Wizard.</span><span class="sxs-lookup"><span data-stu-id="528cf-128">Use the default options to complete the New Application Wizard.</span></span>

9.  <span data-ttu-id="528cf-129">Ripeti i passaggi da 3 a 8 per ogni protocollo desiderato.</span><span class="sxs-lookup"><span data-stu-id="528cf-129">Repeat steps 3 through 8 for each desired protocol.</span></span>

<span data-ttu-id="528cf-130">Dopo aver eseguito questi passaggi per importare i tre pacchetti MSI in MDT, i pacchetti saranno disponibili per la selezione nella pagina Applications della procedura guidata Windows Deployment Wizard.</span><span class="sxs-lookup"><span data-stu-id="528cf-130">After you’ve performed these steps to import the three MSI packages as applications into MDT, they will be available for selection in the Applications page of the Windows Deployment Wizard.</span></span> <span data-ttu-id="528cf-131">Benché in alcuni scenari di distribuzione semplici potrebbe essere sufficiente permettere ai tecnici di selezionare ogni pacchetto al momento della distribuzione, non si tratta di una scelta consigliata.</span><span class="sxs-lookup"><span data-stu-id="528cf-131">Although in some simple deployment scenarios it might be sufficient to have technicians select each package at the time of deployment, it is not recommended.</span></span> <span data-ttu-id="528cf-132">Questa procedura implica la possibilità che un tecnico tenti di applicare i pacchetti a computer diversi dai dispositivi Surface o che un dispositivo Surface venga distribuito senza supporto EAP a causa di un errore umano.</span><span class="sxs-lookup"><span data-stu-id="528cf-132">This practice introduces the possibility that a technician could attempt to apply these packages to computers other than Surface devices, or that a Surface device could be deployed without EAP support due to human error.</span></span>

<span data-ttu-id="528cf-133">Per nascondere queste applicazioni dalla pagina Install Applications, seleziona la casella di controllo **Hide this application in the Deployment Wizard** nelle proprietà di ogni applicazione.</span><span class="sxs-lookup"><span data-stu-id="528cf-133">To hide these applications from the Install Applications page, select the **Hide this application in the Deployment Wizard** checkbox in the properties of each application.</span></span> <span data-ttu-id="528cf-134">Una volta nascoste, le applicazioni non verranno visualizzate come facoltative durante la distribuzione.</span><span class="sxs-lookup"><span data-stu-id="528cf-134">After the applications are hidden, they will not be displayed as optional applications during deployment.</span></span> <span data-ttu-id="528cf-135">Per distribuirle nella sequenza di attività di distribuzione di Surface, le applicazioni devono essere definite in modo esplicito per l'installazione tramite un passaggio separato nella sequenza di attività.</span><span class="sxs-lookup"><span data-stu-id="528cf-135">To deploy them in your Surface deployment task sequence, they must be explicitly defined for installation through a separate step in the task sequence.</span></span>

<span data-ttu-id="528cf-136">Per specificare i protocolli in modo esplicito, segui questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="528cf-136">To specify the protocol(s) explicitly, follow these steps:</span></span>

1.  <span data-ttu-id="528cf-137">Apri le proprietà della sequenza di attività di distribuzione di Surface da MDT Deployment Workbench.</span><span class="sxs-lookup"><span data-stu-id="528cf-137">Open your Surface deployment task sequence properties from the MDT Deployment Workbench.</span></span>

2.  <span data-ttu-id="528cf-138">Nella scheda **Task Sequence** seleziona il passaggio **Install Applications** in **State Restore**.</span><span class="sxs-lookup"><span data-stu-id="528cf-138">On the **Task Sequence** tab, select the **Install Applications** step under **State Restore**.</span></span> <span data-ttu-id="528cf-139">Questo è in genere disponibile tra i passaggi di pre-applicazione e post-applicazione di Windows Update.</span><span class="sxs-lookup"><span data-stu-id="528cf-139">This is typically found between the pre-application and post-application Windows Update steps.</span></span>

3.  <span data-ttu-id="528cf-140">Usa il pulsante **Add** per creare un nuovo passaggio **Install Application** nella categoria **General**.</span><span class="sxs-lookup"><span data-stu-id="528cf-140">Use the **Add** button to create a new **Install Application** step from the **General** category.</span></span>

4.  <span data-ttu-id="528cf-141">Seleziona **Install a single application** nella scheda **Properties** del passaggio.</span><span class="sxs-lookup"><span data-stu-id="528cf-141">Select **Install a single application** in the step **Properties** tab.</span></span>

5.  <span data-ttu-id="528cf-142">Seleziona il protocollo EAP desiderato nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="528cf-142">Select the desired EAP protocol from the list.</span></span>

6.  <span data-ttu-id="528cf-143">Ripeti i passaggi da 2 a 5 per ogni protocollo desiderato.</span><span class="sxs-lookup"><span data-stu-id="528cf-143">Repeat steps 2 through 5 for each desired protocol.</span></span>

## <span data-ttu-id="528cf-144">Distribuire PEAP, EAP-FAST o Cisco LEAP con Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="528cf-144">Deploy PEAP, EAP-FAST, or Cisco LEAP with Configuration Manager</span></span>


<span data-ttu-id="528cf-145">Per le organizzazioni che gestiscono i dispositivi Surface con Configuration Manager, la distribuzione del supporto PEAP, EAP-FAST o Cisco LEAP per tali dispositivi è ancora più semplice.</span><span class="sxs-lookup"><span data-stu-id="528cf-145">For organizations that manage Surface devices with Configuration Manager, it is even easier to deploy PEAP, EAP-FAST, or Cisco LEAP support to Surface devices.</span></span> <span data-ttu-id="528cf-146">È sufficiente importare ogni file MSI come applicazione dall'area Raccolta software e quindi configurare una distribuzione nella raccolta di dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="528cf-146">Simply import each MSI file as an application from the Software Library and configure a deployment to your Surface device collection.</span></span>

<span data-ttu-id="528cf-147">Per altre informazioni su come distribuire applicazioni con Configuration Manager, vedi [Come creare applicazioni in Configuration Manager](https://technet.microsoft.com/library/gg682159.aspx) e [Come distribuire le applicazioni in Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx).</span><span class="sxs-lookup"><span data-stu-id="528cf-147">For more information on how to deploy applications with Configuration Manager see [How to Create Applications in Configuration Manager](https://technet.microsoft.com/library/gg682159.aspx) and [How to Deploy Applications in Configuration Manager](https://technet.microsoft.com/library/gg682082.aspx).</span></span>

 

 






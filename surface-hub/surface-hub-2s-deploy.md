---
title: Creare pacchetti di provisioning per Surface Hub 2S
description: Questa pagina descrive come distribuire l'hub di Surface 2S usando i pacchetti di provisioning e altri strumenti.
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
ms.openlocfilehash: 8f91b751a10977d80210d10ac1b48a93d9ba0f6f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836942"
---
# <span data-ttu-id="03f98-104">Creare pacchetti di provisioning per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="03f98-104">Create provisioning packages for Surface Hub 2S</span></span>

<span data-ttu-id="03f98-105">Puoi usare Windows Configuration designer (WCD) per creare pacchetti di provisioning per automatizzare il processo di distribuzione di Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="03f98-105">You can use Windows Configuration Designer (WCD) to create provisioning packages to automate the deployment process of Surface Hub 2S.</span></span> <span data-ttu-id="03f98-106">Usare i pacchetti di provisioning per aggiungere certificati, configurare proxy, impostare gli amministratori dei dispositivi e gli account di dispositivo.</span><span class="sxs-lookup"><span data-stu-id="03f98-106">Use provisioning packages to add certificates, configure proxies, set up device administrators and device accounts.</span></span> <span data-ttu-id="03f98-107">Puoi anche usare i pacchetti di provisioning insieme a un file di configurazione per distribuire più hub di Surface con una singola unità thumb USB.</span><span class="sxs-lookup"><span data-stu-id="03f98-107">You can also use provisioning packages along with a configuration file to deploy multiple Surface Hubs with a single USB thumb drive.</span></span>

### <span data-ttu-id="03f98-108">Installare Progettazione configurazione di Windows</span><span class="sxs-lookup"><span data-stu-id="03f98-108">Install Windows Configuration Designer</span></span>

<span data-ttu-id="03f98-109">Installare Windows Configuration designer da Windows Assessment and Deployment Kit (ADK) per Windows 10.</span><span class="sxs-lookup"><span data-stu-id="03f98-109">Install Windows Configuration Designer from the Windows Assessment and Deployment Kit (ADK) for Windows 10.</span></span> <span data-ttu-id="03f98-110">Scaricare e installare [ADK per Windows 10, versione 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542).</span><span class="sxs-lookup"><span data-stu-id="03f98-110">Download and install the [ADK for Windows 10, version 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542).</span></span> <span data-ttu-id="03f98-111">Per altre informazioni, vedere [scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span><span class="sxs-lookup"><span data-stu-id="03f98-111">For more information, see [Download and install the Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span></span>

### <span data-ttu-id="03f98-112">Aggiungere certificati</span><span class="sxs-lookup"><span data-stu-id="03f98-112">Add certificates</span></span>

<span data-ttu-id="03f98-113">È possibile importare certificati di autorità di certificazione in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="03f98-113">You can import Certificate Authority certificates to Surface Hub 2S.</span></span>
<span data-ttu-id="03f98-114">Per aggiungere certificati a Surface Hub 2S, è necessaria una copia di ogni certificato come X. 509 in formato CER.</span><span class="sxs-lookup"><span data-stu-id="03f98-114">To add certificates to Surface Hub 2S, you need a copy of each certificate as X.509 in .cer format.</span></span> <span data-ttu-id="03f98-115">Non è possibile importare. CRT, pfx o altri formati contenitore.</span><span class="sxs-lookup"><span data-stu-id="03f98-115">You cannot import .crt, .pfx or other container formats.</span></span> <span data-ttu-id="03f98-116">I certificati devono essere importati in progettazione configurazione Windows e disposti per gerarchia:</span><span class="sxs-lookup"><span data-stu-id="03f98-116">Certificates must be imported into Windows Configuration Designer and arranged by hierarchy:</span></span>

 ![Aggiungere certificati](images/sh2-wcd.png)

### <span data-ttu-id="03f98-118">Configurare il proxy durante la configurazione guidata</span><span class="sxs-lookup"><span data-stu-id="03f98-118">Configure proxy during OOBE</span></span>

<span data-ttu-id="03f98-119">In Windows Configuration designer passare alla scheda Configura impostazioni proxy e immettere le impostazioni appropriate, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="03f98-119">In Windows Configuration Designer, go to the Configure proxy settings tab and enter the appropriate settings as shown below.</span></span>

 ![Configurare le impostazioni del proxy](images/sh2-proxy.png) 

> [!NOTE]
> <span data-ttu-id="03f98-121">Quando si configurano le impostazioni proxy, disattivare **rileva automaticamente le impostazioni** se si intende usare uno script di configurazione o un server proxy.</span><span class="sxs-lookup"><span data-stu-id="03f98-121">When configuring proxy settings, turn off **Automatically detect settings** if you intend to use a setup script or a proxy server.</span></span> <span data-ttu-id="03f98-122">È possibile usare uno script di configurazione *o* un server proxy, non entrambi.</span><span class="sxs-lookup"><span data-stu-id="03f98-122">You can use a setup script *or* a proxy server, not both.</span></span>

### <span data-ttu-id="03f98-123">Superficie di affiliazione Hub 2S con Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="03f98-123">Affiliate Surface Hub 2S with Azure Active Directory</span></span>

<span data-ttu-id="03f98-124">Puoi affiliare Surface Hub 2S con Azure Active Directory usando un pacchetto di provisioning: come amministratore globale di Azure Active Directory, puoi partecipare a un numero elevato di nuovi dispositivi Windows ad Azure Active Directory e Intune usando un token in blocco.</span><span class="sxs-lookup"><span data-stu-id="03f98-124">You can affiliate Surface Hub 2S with Azure Active Directory using a provisioning package: As an Azure Active Directory Global Administrator, you can join large numbers of new Windows devices to Azure Active Directory and Intune using a bulk token.</span></span>

<span data-ttu-id="03f98-125">Per creare un token in blocco, assegnargli un nome descrittivo, configurare la data di scadenza (massimo 30 giorni) e usare le credenziali di amministratore per acquisire il token, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="03f98-125">To create a bulk token, give it a friendly name, configure the expiration date (maximum of 30 days) and use your Admin credentials to acquire the token as shown below:</span></span>

 ![Configurare gli amministratori di dispositivo](images/sh2-token.png) <br><br>
 ![Configurare gli amministratori di dispositivo](images/sh2-token2.png) <br><br>
 ![Configurare gli amministratori di dispositivo](images/sh2-token3.png) <br><br>

### <span data-ttu-id="03f98-129">Provisioning di più dispositivi (file CSV)</span><span class="sxs-lookup"><span data-stu-id="03f98-129">Provisioning multiple devices (.csv file)</span></span>

<span data-ttu-id="03f98-130">Oltre al pacchetto di provisioning, puoi usare un file di configurazione di Surface hub per renderlo ancora più facile da configurare i tuoi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="03f98-130">In addition to the provisioning package, you can use a Surface Hub configuration file to make it even easier to set up your devices.</span></span> <span data-ttu-id="03f98-131">Un file di configurazione di Surface Hub contiene un elenco di account di dispositivo e nomi descrittivi per la proiezione wireless.</span><span class="sxs-lookup"><span data-stu-id="03f98-131">A Surface Hub configuration file contains a list of device accounts and friendly names for wireless projection.</span></span> <span data-ttu-id="03f98-132">Durante la prima esecuzione, viene scelta l'opzione per scegliere un account di dispositivo e un nome descrittivo da un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="03f98-132">During first run, you get an option to choose a device account and friendly name from a configuration file.</span></span>

### <span data-ttu-id="03f98-133">Per creare un file di configurazione di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="03f98-133">To create a Surface Hub configuration file</span></span>

1. <span data-ttu-id="03f98-134">Se si usa Microsoft Excel o un altro editor CSV, creare un file CSV denominato: **SurfaceHubConfiguration.csv**</span><span class="sxs-lookup"><span data-stu-id="03f98-134">Using Microsoft Excel or another CSV editor, create a CSV file named: **SurfaceHubConfiguration.csv**</span></span>
2. <span data-ttu-id="03f98-135">Immettere un elenco di account di dispositivo e nomi descrittivi in questo formato:</span><span class="sxs-lookup"><span data-stu-id="03f98-135">Enter a list of device accounts and friendly names in this format:</span></span>

```
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```

3. <span data-ttu-id="03f98-136">Salvare il file nella radice dell'unità thumb USB in cui è stato copiato il file PPKG.</span><span class="sxs-lookup"><span data-stu-id="03f98-136">Save the file to the root of the USB thumb drive where you copied the PPKG file.</span></span>

    ![Esempio di file di configurazione](images/sh2-config-file.png)

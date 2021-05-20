---
title: Creare pacchetti di provisioning per Surface Hub 2S
description: Questa pagina descrive come distribuire Surface Hub 2S usando pacchetti di provisioning e altri strumenti.
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
ms.openlocfilehash: 214a71a759358ae08eb0da7942ea190946deb327
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576866"
---
# <a name="create-provisioning-packages-for-surface-hub-2s"></a><span data-ttu-id="97d00-104">Creare pacchetti di provisioning per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="97d00-104">Create provisioning packages for Surface Hub 2S</span></span>

<span data-ttu-id="97d00-105">Puoi usare progettazione Windows (WCD) per creare pacchetti di provisioning per automatizzare la distribuzione di Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="97d00-105">You can use Windows Configuration Designer (WCD) to create provisioning packages to automate deployment of Surface Hub 2S.</span></span> <span data-ttu-id="97d00-106">Usa i pacchetti di provisioning per aggiungere certificati, configurare proxy, configurare gli amministratori dei dispositivi e gli account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="97d00-106">Use provisioning packages to add certificates, configure proxies, set up device administrators and device accounts.</span></span> <span data-ttu-id="97d00-107">Puoi anche usare i pacchetti di provisioning insieme a un file di configurazione per distribuire più Dispositivi Surface Hub con una singola unità usb.</span><span class="sxs-lookup"><span data-stu-id="97d00-107">You can also use provisioning packages along with a configuration file to deploy multiple Surface Hubs with a single USB thumb drive.</span></span>

### <a name="install-windows-configuration-designer"></a><span data-ttu-id="97d00-108">Installare Progettazione configurazione di Windows</span><span class="sxs-lookup"><span data-stu-id="97d00-108">Install Windows Configuration Designer</span></span>

<span data-ttu-id="97d00-109">Installare Windows Configuration Designer da Windows Assessment and Deployment Kit (ADK) per Windows 10.</span><span class="sxs-lookup"><span data-stu-id="97d00-109">Install Windows Configuration Designer from the Windows Assessment and Deployment Kit (ADK) for Windows 10.</span></span> <span data-ttu-id="97d00-110">Scaricare e installare [ADK per Windows 10 versione 1703.](https://go.microsoft.com/fwlink/p/?LinkId=845542)</span><span class="sxs-lookup"><span data-stu-id="97d00-110">Download and install the [ADK for Windows 10, version 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542).</span></span> <span data-ttu-id="97d00-111">Per altre informazioni, vedere [Scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span><span class="sxs-lookup"><span data-stu-id="97d00-111">For more information, see [Download and install the Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).</span></span>

### <a name="add-certificates"></a><span data-ttu-id="97d00-112">Aggiungere certificati</span><span class="sxs-lookup"><span data-stu-id="97d00-112">Add certificates</span></span>

<span data-ttu-id="97d00-113">È possibile importare certificati dell'autorità di certificazione Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="97d00-113">You can import Certificate Authority certificates to Surface Hub 2S.</span></span>
<span data-ttu-id="97d00-114">Per aggiungere certificati a Surface Hub 2S, è necessaria una copia di ogni certificato come X.509 in formato cer.</span><span class="sxs-lookup"><span data-stu-id="97d00-114">To add certificates to Surface Hub 2S, you need a copy of each certificate as X.509 in .cer format.</span></span> <span data-ttu-id="97d00-115">Non è possibile importare .crt, .pfx o altri formati di contenitore.</span><span class="sxs-lookup"><span data-stu-id="97d00-115">You cannot import .crt, .pfx or other container formats.</span></span> <span data-ttu-id="97d00-116">I certificati devono essere importati in Progettazione Windows e disposti in base alla gerarchia:</span><span class="sxs-lookup"><span data-stu-id="97d00-116">Certificates must be imported into Windows Configuration Designer and arranged by hierarchy:</span></span>

> [!div class="mx-imgBorder"]
> ![Aggiungere certificati](images/sh2-wcd.png)

### <a name="configure-proxy-during-oobe"></a><span data-ttu-id="97d00-118">Configurare il proxy durante la Configurazione guidata</span><span class="sxs-lookup"><span data-stu-id="97d00-118">Configure proxy during OOBE</span></span>

<span data-ttu-id="97d00-119">In Windows Progettazione configurazione passare alla scheda Configura impostazioni proxy e immettere le impostazioni appropriate come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="97d00-119">In Windows Configuration Designer, go to the Configure proxy settings tab and enter the appropriate settings as shown below.</span></span>

> [!div class="mx-imgBorder"]
> ![Configurare le impostazioni del proxy](images/sh2-proxy.png) 

> [!NOTE]
> <span data-ttu-id="97d00-121">Quando si configurano le impostazioni proxy, disattivare Rileva automaticamente **le** impostazioni se si intende utilizzare uno script di installazione o un server proxy.</span><span class="sxs-lookup"><span data-stu-id="97d00-121">When configuring proxy settings, turn off **Automatically detect settings** if you intend to use a setup script or a proxy server.</span></span> <span data-ttu-id="97d00-122">È possibile utilizzare uno script di *installazione o* un server proxy, non entrambi.</span><span class="sxs-lookup"><span data-stu-id="97d00-122">You can use a setup script *or* a proxy server, not both.</span></span>

### <a name="affiliate-surface-hub-2s-with-azure-active-directory"></a><span data-ttu-id="97d00-123">Affiliate Surface Hub 2S with Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="97d00-123">Affiliate Surface Hub 2S with Azure Active Directory</span></span>

<span data-ttu-id="97d00-124">Puoi consociare Surface Hub 2S con Azure Active Directory usando un pacchetto di provisioning: come amministratore globale di Azure Active Directory, puoi aggiungere un numero elevato di nuovi dispositivi Windows a Azure Active Directory e Intune usando un token in blocco.</span><span class="sxs-lookup"><span data-stu-id="97d00-124">You can affiliate Surface Hub 2S with Azure Active Directory using a provisioning package: As an Azure Active Directory Global Administrator, you can join large numbers of new Windows devices to Azure Active Directory and Intune using a bulk token.</span></span>

<span data-ttu-id="97d00-125">Per creare un token in blocco, assegnargli un nome descrittivo, configurare la data di scadenza (massimo 30 giorni) e usare le credenziali di amministratore per acquisire il token come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="97d00-125">To create a bulk token, give it a friendly name, configure the expiration date (maximum of 30 days) and use your Admin credentials to acquire the token as shown below:</span></span>

> [!div class="mx-imgBorder"]
> ![Esempio 1 per configurare gli amministratori dei dispositivi](images/sh2-token.png)

> [!div class="mx-imgBorder"]
> ![Esempio 2 per configurare gli amministratori dei dispositivi](images/sh2-token2.png)

> [!div class="mx-imgBorder"]
> ![Esempio 3 per configurare gli amministratori dei dispositivi](images/sh2-token3.png)


### <a name="provisioning-multiple-devices-csv-file"></a><span data-ttu-id="97d00-129">Provisioning di più dispositivi (.csv file)</span><span class="sxs-lookup"><span data-stu-id="97d00-129">Provisioning multiple devices (.csv file)</span></span>

<span data-ttu-id="97d00-130">Oltre al pacchetto di provisioning, puoi usare un file di Surface Hub di configurazione per semplificare ancora di più la configurazione dei dispositivi.</span><span class="sxs-lookup"><span data-stu-id="97d00-130">In addition to the provisioning package, you can use a Surface Hub configuration file to make it even easier to set up your devices.</span></span> <span data-ttu-id="97d00-131">Un Surface Hub di configurazione contiene un elenco di account del dispositivo e nomi descrittivi per la proiezione wireless.</span><span class="sxs-lookup"><span data-stu-id="97d00-131">A Surface Hub configuration file contains a list of device accounts and friendly names for wireless projection.</span></span> <span data-ttu-id="97d00-132">Durante la prima esecuzione, puoi scegliere un account del dispositivo e un nome descrittivo da un file di configurazione.</span><span class="sxs-lookup"><span data-stu-id="97d00-132">During first run, you get an option to choose a device account and friendly name from a configuration file.</span></span>

### <a name="to-create-a-surface-hub-configuration-file"></a><span data-ttu-id="97d00-133">Per creare un file Surface Hub file di configurazione</span><span class="sxs-lookup"><span data-stu-id="97d00-133">To create a Surface Hub configuration file</span></span>

1. <span data-ttu-id="97d00-134">Usando Microsoft Excel o un altro editor CSV, crea un file CSV denominato: **SurfaceHubConfiguration.csv**</span><span class="sxs-lookup"><span data-stu-id="97d00-134">Using Microsoft Excel or another CSV editor, create a CSV file named: **SurfaceHubConfiguration.csv**</span></span>

2. <span data-ttu-id="97d00-135">Immetti un elenco di account del dispositivo e nomi descrittivi nel formato seguente:</span><span class="sxs-lookup"><span data-stu-id="97d00-135">Enter a list of device accounts and friendly names in this format:</span></span>

    `<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>`

3. <span data-ttu-id="97d00-136">Salvare il file nella radice dell'unità usb in cui è stato copiato il file PPKG.</span><span class="sxs-lookup"><span data-stu-id="97d00-136">Save the file to the root of the USB thumb drive where you copied the PPKG file.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Esempio di file di configurazione](images/sh2-config-file.png)

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
# <a name="create-provisioning-packages-for-surface-hub-2s"></a>Creare pacchetti di provisioning per Surface Hub 2S

Puoi usare progettazione Windows (WCD) per creare pacchetti di provisioning per automatizzare la distribuzione di Surface Hub 2S. Usa i pacchetti di provisioning per aggiungere certificati, configurare proxy, configurare gli amministratori dei dispositivi e gli account del dispositivo. Puoi anche usare i pacchetti di provisioning insieme a un file di configurazione per distribuire più Dispositivi Surface Hub con una singola unità usb.

### <a name="install-windows-configuration-designer"></a>Installare Progettazione configurazione di Windows

Installare Windows Configuration Designer da Windows Assessment and Deployment Kit (ADK) per Windows 10. Scaricare e installare [ADK per Windows 10 versione 1703.](https://go.microsoft.com/fwlink/p/?LinkId=845542) Per altre informazioni, vedere [Scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).

### <a name="add-certificates"></a>Aggiungere certificati

È possibile importare certificati dell'autorità di certificazione Surface Hub 2S.
Per aggiungere certificati a Surface Hub 2S, è necessaria una copia di ogni certificato come X.509 in formato cer. Non è possibile importare .crt, .pfx o altri formati di contenitore. I certificati devono essere importati in Progettazione Windows e disposti in base alla gerarchia:

> [!div class="mx-imgBorder"]
> ![Aggiungere certificati](images/sh2-wcd.png)

### <a name="configure-proxy-during-oobe"></a>Configurare il proxy durante la Configurazione guidata

In Windows Progettazione configurazione passare alla scheda Configura impostazioni proxy e immettere le impostazioni appropriate come illustrato di seguito.

> [!div class="mx-imgBorder"]
> ![Configurare le impostazioni del proxy](images/sh2-proxy.png) 

> [!NOTE]
> Quando si configurano le impostazioni proxy, disattivare Rileva automaticamente **le** impostazioni se si intende utilizzare uno script di installazione o un server proxy. È possibile utilizzare uno script di *installazione o* un server proxy, non entrambi.

### <a name="affiliate-surface-hub-2s-with-azure-active-directory"></a>Affiliate Surface Hub 2S with Azure Active Directory

Puoi consociare Surface Hub 2S con Azure Active Directory usando un pacchetto di provisioning: come amministratore globale di Azure Active Directory, puoi aggiungere un numero elevato di nuovi dispositivi Windows a Azure Active Directory e Intune usando un token in blocco.

Per creare un token in blocco, assegnargli un nome descrittivo, configurare la data di scadenza (massimo 30 giorni) e usare le credenziali di amministratore per acquisire il token come illustrato di seguito:

> [!div class="mx-imgBorder"]
> ![Esempio 1 per configurare gli amministratori dei dispositivi](images/sh2-token.png)

> [!div class="mx-imgBorder"]
> ![Esempio 2 per configurare gli amministratori dei dispositivi](images/sh2-token2.png)

> [!div class="mx-imgBorder"]
> ![Esempio 3 per configurare gli amministratori dei dispositivi](images/sh2-token3.png)


### <a name="provisioning-multiple-devices-csv-file"></a>Provisioning di più dispositivi (.csv file)

Oltre al pacchetto di provisioning, puoi usare un file di Surface Hub di configurazione per semplificare ancora di più la configurazione dei dispositivi. Un Surface Hub di configurazione contiene un elenco di account del dispositivo e nomi descrittivi per la proiezione wireless. Durante la prima esecuzione, puoi scegliere un account del dispositivo e un nome descrittivo da un file di configurazione.

### <a name="to-create-a-surface-hub-configuration-file"></a>Per creare un file Surface Hub file di configurazione

1. Usando Microsoft Excel o un altro editor CSV, crea un file CSV denominato: **SurfaceHubConfiguration.csv**

2. Immetti un elenco di account del dispositivo e nomi descrittivi nel formato seguente:

    `<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>`

3. Salvare il file nella radice dell'unità usb in cui è stato copiato il file PPKG.

    > [!div class="mx-imgBorder"]
    > ![Esempio di file di configurazione](images/sh2-config-file.png)

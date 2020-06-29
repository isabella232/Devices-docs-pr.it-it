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
# Creare pacchetti di provisioning per Surface Hub 2S

Puoi usare Windows Configuration designer (WCD) per creare pacchetti di provisioning per automatizzare il processo di distribuzione di Surface Hub 2S. Usare i pacchetti di provisioning per aggiungere certificati, configurare proxy, impostare gli amministratori dei dispositivi e gli account di dispositivo. Puoi anche usare i pacchetti di provisioning insieme a un file di configurazione per distribuire più hub di Surface con una singola unità thumb USB.

### Installare Progettazione configurazione di Windows

Installare Windows Configuration designer da Windows Assessment and Deployment Kit (ADK) per Windows 10. Scaricare e installare [ADK per Windows 10, versione 1703](https://go.microsoft.com/fwlink/p/?LinkId=845542). Per altre informazioni, vedere [scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install).

### Aggiungere certificati

È possibile importare certificati di autorità di certificazione in Surface Hub 2S.
Per aggiungere certificati a Surface Hub 2S, è necessaria una copia di ogni certificato come X. 509 in formato CER. Non è possibile importare. CRT, pfx o altri formati contenitore. I certificati devono essere importati in progettazione configurazione Windows e disposti per gerarchia:

 ![Aggiungere certificati](images/sh2-wcd.png)

### Configurare il proxy durante la configurazione guidata

In Windows Configuration designer passare alla scheda Configura impostazioni proxy e immettere le impostazioni appropriate, come illustrato di seguito.

 ![Configurare le impostazioni del proxy](images/sh2-proxy.png) 

> [!NOTE]
> Quando si configurano le impostazioni proxy, disattivare **rileva automaticamente le impostazioni** se si intende usare uno script di configurazione o un server proxy. È possibile usare uno script di configurazione *o* un server proxy, non entrambi.

### Superficie di affiliazione Hub 2S con Azure Active Directory

Puoi affiliare Surface Hub 2S con Azure Active Directory usando un pacchetto di provisioning: come amministratore globale di Azure Active Directory, puoi partecipare a un numero elevato di nuovi dispositivi Windows ad Azure Active Directory e Intune usando un token in blocco.

Per creare un token in blocco, assegnargli un nome descrittivo, configurare la data di scadenza (massimo 30 giorni) e usare le credenziali di amministratore per acquisire il token, come illustrato di seguito:

 ![Configurare gli amministratori di dispositivo](images/sh2-token.png) <br><br>
 ![Configurare gli amministratori di dispositivo](images/sh2-token2.png) <br><br>
 ![Configurare gli amministratori di dispositivo](images/sh2-token3.png) <br><br>

### Provisioning di più dispositivi (file CSV)

Oltre al pacchetto di provisioning, puoi usare un file di configurazione di Surface hub per renderlo ancora più facile da configurare i tuoi dispositivi. Un file di configurazione di Surface Hub contiene un elenco di account di dispositivo e nomi descrittivi per la proiezione wireless. Durante la prima esecuzione, viene scelta l'opzione per scegliere un account di dispositivo e un nome descrittivo da un file di configurazione.

### Per creare un file di configurazione di Surface Hub

1. Se si usa Microsoft Excel o un altro editor CSV, creare un file CSV denominato: **SurfaceHubConfiguration.csv**
2. Immettere un elenco di account di dispositivo e nomi descrittivi in questo formato:

```
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```

3. Salvare il file nella radice dell'unità thumb USB in cui è stato copiato il file PPKG.

    ![Esempio di file di configurazione](images/sh2-config-file.png)

---
title: Considerazioni per Surface e Microsoft Endpoint Configuration Manager
description: La gestione e la distribuzione dei dispositivi Surface con Configuration Manager sono fondamentalmente uguali a qualsiasi altro PC. in questo articolo vengono descritti gli scenari che possono richiedere ulteriori considerazioni.
keywords: gestire, distribuzione, aggiornamenti, driver, firmware
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.date: 08/12/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 88d25786601bdb88c027b689431d1c08c80cb9ec
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448339"
---
# <a name="considerations-for-surface-and-microsoft-endpoint-configuration-manager"></a>Considerazioni per Surface e Microsoft Endpoint Configuration Manager

Fondamentalmente, la gestione e la distribuzione di dispositivi Surface con Microsoft Endpoint Configuration Manager è la stessa della gestione e della distribuzione di qualsiasi altro PC. Come qualsiasi altro PC, una distribuzione di dispositivi Surface include l'importazione di driver, l'importazione di un'immagine Windows, la preparazione di una sequenza di attività di distribuzione e quindi la distribuzione della sequenza di attività in una raccolta. Dopo la distribuzione, i dispositivi Surface sono come qualsiasi altro client Windows; per pubblicare app, impostazioni e criteri, usi lo stesso processo che userei per qualsiasi altro dispositivo.

Per ulteriori informazioni, vedere Microsoft Endpoint Configuration Manager [documentazione](/mem/configmgr/).

Anche se la distribuzione e la gestione dei dispositivi Surface sono fondamentalmente simili ad altri PC, alcuni scenari potrebbero richiedere attività IT aggiuntive, come descritto in questo articolo. 

> [!TIP]
> Usa [current branch of Microsoft Endpoint Configuration Manager](/mem/configmgr/core/servers/manage/updates) per gestire i dispositivi Surface.

## <a name="update-surface-device-drivers-and-firmware"></a>Aggiornare i driver e il firmware dei dispositivi Surface

Per distribuire gli aggiornamenti dei driver di dispositivo e del firmware con Configuration Manager o Windows Server Update Services (WSUS), vedi [Gestire gli aggiornamenti del firmware e dei driver di Surface](manage-surface-driver-and-firmware-updates.md).

## <a name="surface-ethernet-adapters-and-configuration-manager-deployment"></a>Schede Surface Ethernet e distribuzione di Configuration Manager

Il meccanismo predefinito utilizzato da Configuration Manager per identificare i dispositivi durante la distribuzione è l'indirizzo MAC (Media Access Control). Poiché l'indirizzo MAC è associato al controller Ethernet, una scheda Ethernet condivisa tra più dispositivi causerà l'identificazione di ognuno dei dispositivi come un solo dispositivo, con conseguente distribuzione non riuscita. 

Per assicurarti che i dispositivi Surface che usano la stessa scheda Ethernet siano identificati come dispositivi univoci durante la distribuzione, puoi indicare a Configuration Manager di identificare i dispositivi con un altro metodo. È possibile specificare che Configuration Manager utilizzi altri metodi di identificazione, come descritto in [Manage duplicate hardware identifiers](/mem/configmgr/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers):

- Aggiungi un'esclusione per gli indirizzi MAC delle schede Surface Ethernet, che forza Configuration Manager a ignorare l'indirizzo MAC in preferenza dell'UUID di sistema.

- Usa uno script per identificare un dispositivo Surface appena distribuito dall'indirizzo MAC della scheda wireless.

### <a name="surface-ethernet-driver"></a>Surface Ethernet Driver

Dal 2016, il driver per la scheda Surface Ethernet è stato incluso per impostazione predefinita in Windows e non richiede alcuna configurazione IT aggiuntiva. A partire dalla sua inclusione in Windows 10, il driver non è più disponibile per il download dall'Area download Microsoft. Se è necessario distribuire versioni precedenti di Windows 10 Pro, è possibile scaricare il driver più recente dal [Catalogo di Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=surface%20ethernet%20drivers).

## <a name="deploy-surface-app-with-configuration-manager"></a>Distribuire l'app Surface con Configuration Manager

Con il rilascio di Microsoft Store per le aziende, l'app Surface non è più disponibile come download di driver e firmware. Le organizzazioni che distribuiscono l'app Surface nei dispositivi Surface gestiti o durante la distribuzione tramite Configuration Manager devono prima acquisire l'app Surface Microsoft Store per le aziende. Per altre informazioni, vedi [Distribuire l'app Surface con Microsoft Store per le aziende](deploy-surface-app-with-windows-store-for-business.md).

## <a name="use-prestaged-media-with-surface-clients"></a>Usare supporti prestaged con client Surface

Se l'organizzazione usa supporti prestaged per caricare le risorse di distribuzione nei computer prima della distribuzione con Configuration Manager, la natura dei dispositivi Surface come dispositivi UEFI potrebbe richiedere ulteriori passaggi. In particolare, un ambiente UEFI nativo richiede la creazione di più partizioni nel disco di avvio del sistema. Se stai seguendo insieme alla documentazione per i supporti [prestaged](/mem/configmgr/osd/deploy-use/create-prestaged-media), le istruzioni forniscono solo dischi di avvio a partizione singola e pertanto avranno esito negativo se applicati ai dispositivi Surface.

Le istruzioni per l'applicazione di supporti prestaged ai dispositivi UEFI, ad esempio i dispositivi Surface, sono disponibili nel post di blog How [to apply Task Sequence Prestaged Media on multi-partitioned disks for BIOS or UEFI PC nel](https://techcommunity.microsoft.com/t5/configuration-manager-archive/how-to-apply-task-sequence-prestaged-media-on-multi-partitioned/ba-p/392239) post di blog del sistema.

## <a name="licensing-conflicts-with-oem-activation-30"></a>Conflitti di licenze con Attivazione OEM 3.0

I dispositivi Surface vengono preinstallati con una copia con licenza di Windows. Il codice di licenza per questa copia preinstallata di Windows è incorporato nel firmware del dispositivo con [OEM Activation 3.0](/windows-hardware/manufacture/desktop/oem-activation-3) (OA 3.0). Quando esegui un Windows di installazione in un dispositivo con una chiave OA 3.0, il programma di installazione di Windows legge automaticamente il codice di licenza e lo usa per installare e attivare Windows. Nella maggior parte dei casi, ciò semplifica la reinstallazione Windows, perché l'utente non deve trovare o immettere un codice di licenza.

Quando si ricrea l'immagine di un dispositivo Windows Enterprise, questo codice di licenza incorporato non causa un conflitto. Questo perché il supporto di installazione per Windows Enterprise è configurato per installare solo un'edizione Enterprise di Windows e pertanto non è compatibile con il codice di licenza incorporato nel firmware di sistema. Se non viene specificato un codice Product Key (ad esempio quando si intende eseguire l'attivazione con i servizi di gestione delle chiavi [Servizio di gestione delle chiavi] o l'attivazione basata su Active Directory), viene utilizzato un codice Product Key per contratti multilicenza (GVLK) generico fino a quando Windows non viene attivato da una di queste tecnologie.

Tuttavia, possono verificarsi problemi quando le organizzazioni intendono utilizzare versioni di Windows compatibili con la chiave incorporata del firmware. Ad esempio, un'organizzazione che desidera installare Windows 10 Pro in un dispositivo originariamente fornito con Windows 10 Home potrebbe riscontrare difficoltà quando il programma di installazione di Windows legge automaticamente il codice Home edition durante l'installazione e viene installato come Windows 10 Home anziché come Windows 10 Home Windows 10 Pro. Per evitare questo conflitto, utilizzare il file Ei.cfg o Pid.txt per indicare esplicitamente al programma di installazione di Windows di richiedere un codice Product Key o immettere un codice Product Key specifico nella sequenza di attività di distribuzione. Per ulteriori informazioni, vedere Windows [Setup Edition Configuration and Product ID Files](/windows-hardware/manufacture/desktop/windows-setup-edition-configuration-and-product-id-files--eicfg-and-pidtxt). Se non si dispone di un codice Product Key specifico, è possibile utilizzare i codici Product Key predefiniti per Windows. Per ulteriori informazioni, vedere [Deploy Windows 10](/windows/deployment/deploy).

## <a name="apply-an-asset-tag-during-deployment"></a>Applicare un tag asset durante la distribuzione

Con lo [strumento tag Surface Asset](assettag.md) puoi identificare i dispositivi da UEFI anche se il sistema operativo ha esito negativo. Per altre informazioni sulla gestione degli asset con Configuration Manager, vedi [Introduzione all'asset intelligence in Configuration Manager](/mem/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence).

## <a name="configure-push-button-reset"></a>Configurare la reimpostazione del pulsante push

Quando distribuisci Windows in un dispositivo Surface, la funzionalità di reimpostazione dei pulsanti di Windows è configurata per impostazione predefinita per ripristinare lo stato del sistema in cui l'ambiente non è ancora configurato. Quando viene utilizzata la funzione di reimpostazione, il sistema elimina tutte le applicazioni e le impostazioni installate. Anche se in alcune situazioni può essere utile ripristinare lo stato del sistema senza applicazioni e impostazioni, in un ambiente professionale questo rende effettivamente inutilizzabile il sistema per l'utente finale.

La reimpostazione del pulsante push può tuttavia essere configurata per ripristinare la configurazione di sistema a uno stato in cui è pronta per l'uso da parte dell'utente finale. Segui il processo descritto in [Deploy push-button reset features](/windows-hardware/manufacture/desktop/deploy-push-button-reset-features) to customize the push-button reset experience for your devices.

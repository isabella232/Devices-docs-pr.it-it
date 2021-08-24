---
title: Gestire e installare gli aggiornamenti di driver e firmware per Surface
description: Questo articolo illustra le opzioni disponibili per gestire e distribuire gli aggiornamenti del firmware e dei driver per i dispositivi Surface.
ms.assetid: CD1219BA-8EDE-4BC8-BEEF-99B50C211D73
ms.reviewer: ''
manager: laurawi
keywords: Surface, Surface Pro 3, firmware, aggiornamento, dispositivo, gestire, distribuire, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 10/12/2020
ms.openlocfilehash: afc7b2e82519fb42ca07b107bff73ddea894cfdf
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911641"
---
# <a name="manage-and-deploy-surface-driver-and-firmware-updates"></a>Gestire e installare gli aggiornamenti di driver e firmware per Surface

La modalità di gestione degli aggiornamenti di driver e firmware di Surface varia a seconda dei requisiti dell'ambiente e dell'organizzazione. Nei dispositivi Surface, il firmware viene esposto al sistema operativo come driver ed è visibile in Gestione dispositivi. In questo modo il firmware e i driver del dispositivo possono essere aggiornati automaticamente Windows Update o Windows Update for Business. Anche se questo approccio semplificato può essere fattibile per le startup e le piccole o medie imprese, le organizzazioni più grandi in genere necessitano di amministratori IT per distribuire gli aggiornamenti internamente. Ciò può comportare la pianificazione completa, i test di compatibilità delle applicazioni e la sperimentazione e la convalida degli aggiornamenti prima dell'approvazione e della distribuzione finali nella rete.

> [!NOTE]
> Questo articolo è destinato agli agenti di supporto tecnico e ai professionisti IT e si applica solo ai dispositivi Surface. Per informazioni su come installare gli aggiornamenti di Surface o il firmware in un dispositivo principale, vedi [Aggiornare il firmware di Surface e Windows 10](https://support.microsoft.com/help/4023505).

Mentre le soluzioni di distribuzione software di livello aziendale continuano a evolversi, la logica aziendale per la gestione centralizzata degli aggiornamenti rimane la stessa: mantenere la sicurezza dei dispositivi Surface e mantenerli aggiornati con i miglioramenti più recenti del sistema operativo e delle funzionalità. Ciò è essenziale per mantenere un ambiente di produzione stabile e garantire che agli utenti non venga impedito di essere produttivi. In questo articolo viene fornita una panoramica degli strumenti e dei processi consigliati per le organizzazioni più grandi per raggiungere questi obiettivi.

## <a name="central-update-management-in-commercial-environments"></a>Gestione centrale degli aggiornamenti in ambienti commerciali

Microsoft ha strumenti semplificati per la gestione dei dispositivi, inclusi gli aggiornamenti di driver e [firmware, in](https://devicemanagement.microsoft.com/) una singola esperienza unificata denominata interfaccia di amministrazione di Microsoft Endpoint Manager a cui è possibile accedere [da devicemanagement.microsoft.com](https://devicemanagement.microsoft.com/#home).

### <a name="manage-updates-with-configuration-manager-and-intune"></a>Gestire gli aggiornamenti con Configuration Manager e Intune

Microsoft Endpoint Configuration Manager consente di sincronizzare e distribuire gli aggiornamenti del firmware e dei driver di Surface con il client di Configuration Manager. L'Microsoft Intune consente di visualizzare tutti i dispositivi gestiti, co-gestiti e gestiti dal partner in un'unica posizione. Questa è la soluzione consigliata per le organizzazioni di grandi dimensioni per gestire gli aggiornamenti di Surface.

Per la procedura dettagliata, vedere le risorse seguenti:

- [Gestire gli aggiornamenti dei driver di Surface in Configuration Manager](https://docs.microsoft.com/surface/manage-surface-driver-updates-configuration-manager)
- [Distribuire applicazioni con Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/)

### <a name="manage-updates-with-microsoft-deployment-toolkit"></a>Gestire gli aggiornamenti con Microsoft Deployment Toolkit

Microsoft Deployment Toolkit (MDT) è incluso in Endpoint Configuration Manager. Contiene strumenti di distribuzione facoltativi che è possibile utilizzare, a seconda dell'ambiente. Questi includono Windows Assessment and Deployment Kit (Windows ADK), Windows System Image Manager (Windows SIM), Deployment Image Servicing and Management (DISM) e User State Migration Tool (USMT). Puoi scaricare la versione più recente di MDT dalla pagina [di download di Microsoft Deployment Toolkit .](https://www.microsoft.com/download/details.aspx?id=54259)

Per la procedura dettagliata, vedere le risorse seguenti:

- [Documentazione di Microsoft Deployment Toolkit](https://docs.microsoft.com/configmgr/mdt/)
- [Distribuire Windows10 con Microsoft Deployment Toolkit](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Distribuire Windows 10 nei dispositivi Surface con Microsoft Deployment Toolkit](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)

Gli aggiornamenti del driver e del firmware di Surface vengono Windows file Windows Installer (*.msi). Per distribuire questi pacchetti Windows Installer, puoi usare Endpoint Configuration Manager o MDT. Per informazioni su come selezionare il file .msi corretto per un dispositivo e un sistema operativo, fare riferimento alle indicazioni nelle sezioni seguenti sul download di .msi file.

Per istruzioni su come distribuire gli aggiornamenti tramite Endpoint Configuration Manager, vedi [Distribuire applicazioni con Configuration Manager.](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications) Per istruzioni su come distribuire gli aggiornamenti tramite MDT, vedi [Distribuire un'immagine Windows 10 tramite MDT.](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt)

**Firmware e driver di WindowsPE e Surface**

Endpoint Configuration Manager e MDT usano entrambi il Windows Preinstallation Environment (WindowsPE) durante il processo di distribuzione. WindowsPE supporta solo un set limitato di driver di base, ad esempio quelli per schede di rete e controller di archiviazione. I driver Windows componenti che non fanno parte di WindowsPE potrebbero generare errori. Come procedura consigliata, è possibile evitare tali errori configurando il processo di distribuzione in modo che utilizzi solo i driver necessari durante la fase di WindowsPE.

### <a name="endpoint-configuration-manager"></a>Endpoint Configuration Manager

A partire da Endpoint Configuration Manager, puoi sincronizzare e distribuire gli aggiornamenti del firmware e dei driver di Microsoft Surface usando il client di Configuration Manager. Per ulteriori informazioni, vedi Kb 4098906 come [gestire gli aggiornamenti dei driver di Surface in Configuration Manager.](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)

## <a name="supported-devices"></a>Dispositivi supportati

I file .msi scaricabili sono disponibili per i dispositivi Surface Pro 2 e versioni successive (ad eccezione di Surface Pro X che viene eseguito Windows 10 su ARM).

## <a name="managing-firmware-with-dfci"></a>Gestione del firmware con DFCI

Grazie ai profili DFCI (Device Firmware Configuration Interface) incorporati [in](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)Intune (ora disponibile in anteprima pubblica), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning a tocco zero, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza (incluse le opzioni di avvio e le periferiche incorporate) e mette a punto le basi per scenari di sicurezza avanzati in futuro. Per ulteriori informazioni, vedere gli articoli seguenti:

- [Gestione di Intune delle impostazioni UEFI di Surface](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: Annuncio della](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)gestione remota delle impostazioni UEFI di Surface da Intune.

## <a name="best-practices-for-update-deployment-processes"></a>Procedure consigliate per i processi di distribuzione degli aggiornamenti

Per mantenere un ambiente stabile, è consigliabile mantenere la parità con la versione più recente di Windows 10.  Per suggerimenti sulle procedure consigliate, vedere [Build deployment rings for Windows 10 updates](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates).

## <a name="downloadable-surface-update-packages"></a>Pacchetti di aggiornamento di Surface scaricabili

Versioni specifiche di Windows 10 hanno file .msi separati, ognuno dei quali contiene tutti gli aggiornamenti cumulativi di driver e firmware necessari per i dispositivi Surface. I pacchetti di aggiornamento possono includere alcuni o tutti i componenti seguenti:

- Wi-Fi e LTE
- Video
- Unità a stato solido
- Modulo aggregatore di sistema (SAM)
- Batteria
- Controller tastiera
- Controller incorporato (EC)
- Motore di gestione (ME)
- Interfaccia UEFI (Unified Extensible Firmware Interface)

### <a name="downloading-msi-files"></a>Download di .msi file

1. Passare a [Scaricare driver e firmware per Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware) nell'Area download Microsoft.
2. Seleziona il .msi del file che corrisponde al modello Surface e alla versione di Windows. Il .msi file include il numero minimo di build Windows necessario per installare i driver e il firmware. Ad esempio, fare riferimento alla figura seguente. Per aggiornare un Surface Book 2 con build 18362 di Windows 10, scegliere **SurfaceBook2_Win10_18362_19.101.13994.msi.** Per un Surface Book 2 con build 16299 di Windows 10, scegliere **SurfaceBook2_Win10_16299_1803509_3.msi**.

    ![Figura 1. Download degli aggiornamenti di Surface.](images/fig1-downloads-msi.png)

    *Figura 1. Download degli aggiornamenti di Surface*

### <a name="surface-msi-naming-convention"></a>Convenzione di denominazione .msi Surface

Da agosto 2019, i .msi utilizzano la convenzione di denominazione seguente:

- *Product*_*Windows release Windows*_ build*number*Numero di_*versione*_ Revisione del numero di*versione (in genere zero)*.

**Esempio**

- SurfacePro6_Win10_18362_19.073.44195_0.msi

Questo nome di file fornisce le informazioni seguenti:

- **Prodotto:** SurfacePro6
- **Windows rilascio:** Win10
- **Build:** 18362
- **Versione:** 19.073.44195 - Indica la data e l'ora di creazione del file, come indicato di seguito:
  - **Anno:** 19 (2019)
  - **Mese e settimana:** 073 (terza settimana di luglio)
  - **Minuto del mese:** 44195
- **Revisione della versione:** 0 (prima versione di questa versione)

### <a name="legacy-surface-msi-naming-convention"></a>Convenzione di denominazione .msi Surface legacy

I .msi legacy (file creati prima di agosto 2019) hanno seguito la stessa formula di denominazione complessiva, ma hanno utilizzato un metodo diverso per derivare il numero di versione.

**Esempio**

- SurfacePro6_Win10_16299_1900307_0.msi

Questo nome di file fornisce le informazioni seguenti:

- **Prodotto:** SurfacePro6
- **Windows rilascio:** Win10
- **Build:** 16299
- **Version:** 1900307 : mostra la data di creazione del file e la relativa posizione nella sequenza di rilascio, come indicato di seguito:
  - **Anno:** 19 (2019)
  - **Numero di rilascio:** 003 (terza versione dell'anno)
  - **Numero di versione del prodotto:** 07 (Surface Pro 6 è ufficialmente la settima versione di Surface Pro)
- **Revisione della versione:** 0 (prima versione di questa versione)

## <a name="learn-more"></a>Scopri di più

- [Scaricare driver e firmware per Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)
- [Come gestire gli aggiornamenti dei driver di Surface in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [Distribuire applicazioni con Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/)
- [Documentazione di Microsoft Deployment Toolkit](https://docs.microsoft.com/configmgr/mdt/)
- [Distribuire Windows10 con Microsoft Deployment Toolkit](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Distribuire Windows 10 nei dispositivi Surface con Microsoft Deployment Toolkit](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)  
- [Gestione di Intune delle impostazioni UEFI di Surface](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: Annuncio della](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)gestione remota delle impostazioni UEFI di Surface da Intune.
- [Creare circuiti di distribuzione per gli aggiornamenti di Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)

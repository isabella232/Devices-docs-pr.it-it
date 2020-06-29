---
title: Gestire e distribuire gli aggiornamenti di driver e firmware Surface
description: Questo articolo descrive le opzioni disponibili per gestire e distribuire gli aggiornamenti del firmware e del driver per i dispositivi Surface.
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
ms.openlocfilehash: 91cde5fdf4a7745d491bd2eb928baca75955b90d
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832829"
---
# Gestire e distribuire gli aggiornamenti di driver e firmware Surface

Il modo in cui Gestisci gli aggiornamenti di Surface driver e firmware varia a seconda dell'ambiente e dei requisiti dell'organizzazione. Nei dispositivi Surface il firmware viene esposto al sistema operativo come driver ed è visibile in gestione dispositivi, consentendo il firmware e i driver del dispositivo per l'aggiornamento automatico tramite Windows Update o Windows Update for business. Anche se questo approccio semplificato può essere possibile per le start-up e le piccole e medie imprese, le organizzazioni più grandi in genere necessitano di amministratori IT per distribuire gli aggiornamenti internamente. Ciò può comportare la pianificazione completa, il test di compatibilità delle applicazioni, il pilotaggio e la convalida degli aggiornamenti, prima dell'approvazione finale e della distribuzione in rete.

> [!NOTE]
> Questo articolo è destinato agli agenti del supporto tecnico e ai professionisti IT e si applica solo ai dispositivi Surface. Per informazioni su come installare gli aggiornamenti della superficie o il firmware in un dispositivo Home, vedere [aggiornare il firmware della superficie e Windows 10](https://support.microsoft.com/help/4023505).

Mentre le soluzioni di distribuzione del software di livello aziendale continuano ad evolversi, la logica aziendale per la gestione centralizzata degli aggiornamenti rimane la stessa: gestire la sicurezza dei dispositivi Surface e tenerli aggiornati con i miglioramenti più recenti del sistema operativo e delle funzionalità. Ciò è essenziale per sostenere un ambiente di produzione stabile e garantire che gli utenti non vengano bloccati dall'essere produttivi. Questo articolo offre una panoramica degli strumenti e dei processi consigliati per le organizzazioni di grandi dimensioni per realizzare questi obiettivi.

## Gestione degli aggiornamenti centralizzati in ambienti commerciali

Microsoft offre strumenti semplificati per la gestione dei dispositivi, inclusi i driver e gli aggiornamenti del firmware, in un'unica esperienza unificata denominata interfaccia di [amministrazione di Microsoft Endpoint Manager](https://devicemanagement.microsoft.com/) accessibile da devicemanagement.Microsoft.com.

### Gestire gli aggiornamenti con Configuration Manager e Intune

Microsoft endpoint Configuration Manager consente di sincronizzare e distribuire gli aggiornamenti di Surface firmware e driver con il client Configuration Manager. L'integrazione con Microsoft Intune consente di visualizzare tutti i dispositivi gestiti, co-gestiti e gestiti da partner in un'unica posizione. Questa è la soluzione consigliata per le organizzazioni di grandi dimensioni per gestire gli aggiornamenti della superficie.

Per la procedura dettagliata, vedere le risorse seguenti:

- [Come gestire gli aggiornamenti di Surface driver in Configuration Manager](https://docs.microsoft.com/surface/manage-surface-driver-updates-configuration-manager)
- [Distribuire applicazioni con Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di endpoint Configuration Manager](https://docs.microsoft.com/configmgr/)

### Gestire gli aggiornamenti con Microsoft Deployment Toolkit

Incluso in endpoint Configuration Manager, Microsoft Deployment Toolkit (MDT) contiene gli strumenti di distribuzione facoltativi che possono essere usati a seconda dell'ambiente. Questi includono il kit di valutazione e distribuzione di Windows (Windows ADK), Windows System Image Manager (Windows SIM), gestione e manutenzione immagini distribuzione (DISM) e strumento di migrazione stato utente. È possibile scaricare la versione più recente di MDT dalla [pagina di download di Microsoft Deployment Toolkit](https://www.microsoft.com/download/details.aspx?id=54259).

Per la procedura dettagliata, vedere le risorse seguenti:

- [Documentazione di Microsoft Deployment Toolkit](https://docs.microsoft.com/configmgr/mdt/)
- [Distribuire Windows10 con Microsoft Deployment Toolkit](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Distribuire Windows 10 ai dispositivi Surface con Microsoft Deployment Toolkit](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)

I driver di superficie e gli aggiornamenti del firmware vengono assemblati come file di Windows Installer (*. msi). Per distribuire questi pacchetti di Windows Installer, è possibile usare endpoint Configuration Manager o MDT. Per informazioni su come selezionare il file MSI corretto per un dispositivo e un sistema operativo, vedere le indicazioni seguenti sul download di file con estensione msi.

Per istruzioni su come distribuire gli aggiornamenti usando Gestione configurazione di endpoint, fare riferimento a [Distribuisci applicazioni con Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications). Per istruzioni su come distribuire gli aggiornamenti tramite MDT, vedere [distribuire un'immagine di Windows 10 con MDT](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).

**Firmware e driver della superficie e di WindowsPE**

Endpoint Configuration Manager e MDT usano entrambi l'ambiente di preinstallazione di Windows (WindowsPE) durante il processo di distribuzione. WindowsPE supporta solo un set limitato di driver di base, ad esempio quelli per le schede di rete e i controller di archiviazione. I driver per i componenti Windows che non fanno parte di WindowsPE potrebbero generare errori. Come procedura consigliata, puoi impedire tali errori configurando il processo di distribuzione in modo da usare solo i driver necessari durante la fase WindowsPE.

### Endpoint Configuration Manager

A partire da endpoint Configuration Manager, è possibile sincronizzare e distribuire il firmware e gli aggiornamenti del driver Microsoft Surface usando il client Configuration Manager. Per altre informazioni, vedere KB 4098906, [come gestire gli aggiornamenti dei driver di superficie in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager).

## Dispositivi supportati

I file con estensione msi scaricabili sono disponibili per i dispositivi Surface da Surface Pro 2 e versioni successive. Le informazioni sui file MSI per i dispositivi di superficie più recenti, ad esempio Surface Pro 7, Surface Pro X e Surface laptop 3, saranno disponibili in questa pagina al momento del rilascio.

## Gestione del firmware con DFCI

Con i profili DFCI (device firmware Configuration Interface) incorporati in Intune (ora disponibile in [anteprima pubblica](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI Management estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning a zero tocco, Elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, incluse le opzioni di avvio e le periferiche predefinite, e stabilisce le basi per scenari di sicurezza avanzati in futuro. Per altre informazioni, vedi:

- [Gestione di Intune delle impostazioni UEFI di Surface](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: annuncia la gestione remota delle impostazioni di Surface UEFI da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).

## Procedure consigliate per l'aggiornamento dei processi di distribuzione

Per mantenere un ambiente stabile, è vivamente consigliabile mantenere la parità con la versione più recente di Windows 10.  Per le procedure consigliate, vedere [creare anelli di distribuzione per gli aggiornamenti di Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates).

## Pacchetti di aggiornamento per Surface scaricabili

Le versioni specifiche di Windows 10 hanno file MSI distinti, ognuno contenente tutti i driver cumulativi necessari e gli aggiornamenti del firmware per i dispositivi Surface. I pacchetti di aggiornamento possono includere alcuni o tutti i componenti seguenti:

- Wi-Fi e LTE
- Video
- Unità a stato solido
- Modulo aggregatore di sistema (SAM)
- Batteria
- Controller di tastiera
- Controller incorporato (EC)
- Motore di gestione (ME)
- Interfaccia UEFI (Unified Extensible Firmware Interface)

### Download di file con estensione msi

1. Individuare per [scaricare i driver e il firmware per Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware) nell'area download Microsoft.
2. Selezionare il nome del file MSI che corrisponde al modello di superficie e alla versione di Windows. Il nome del file MSI include il numero di build di Windows minimo supportato necessario per installare i driver e il firmware. Ad esempio, come illustrato nella figura seguente, per aggiornare un libro Surface 2 con Build 18362 di Windows 10, scegliere **SurfaceBook2_Win10_18362_19.101.13994.msi.** Per un libro Surface 2 con Build 16299 di Windows 10, scegliere **SurfaceBook2_Win10_16299_1803509_3.msi**.

    ![Figura 1. Download degli aggiornamenti della superficie](images/fig1-downloads-msi.png)

    *Figura 1. Download degli aggiornamenti della superficie*

### Convenzione di denominazione Surface. msi

Dal 2019 agosto i file MSI hanno usato la convenzione di denominazione seguente:

- *Prodotto*_*Windows Release*_ numero di versione di*Windows Build*_*Version number*_ Number*revisione del numero di versione (in genere zero)*.

**Esempio**

- SurfacePro6_Win10_18362_19.073.44195_0.msi

Questo nome file fornisce le informazioni seguenti:

- **Prodotto:** SurfacePro6
- **Windows Release:** Win10
- **Build:** 18362
- **Versione:** 19.073.44195-Mostra la data e l'ora in cui il file è stato creato, come indicato di seguito:
  - **Anno:** 19 (2019)
  - **Mese e settimana:** 073 (terza settimana di luglio)
  - **Minuto del mese:** 44195
- **Revisione della versione:** 0 (prima versione di questa versione)

### Convenzione di denominazione della superficie legacy. msi

I file MSI legacy (file creati prima di agosto 2019) hanno seguito la stessa formula di denominazione complessiva, ma hanno usato un metodo diverso per derivare il numero di versione.

**Esempio**

- SurfacePro6_Win10_16299_1900307_0.msi

Questo nome file fornisce le informazioni seguenti:

- **Prodotto:** SurfacePro6
- **Windows Release:** Win10
- **Build:** 16299
- **Versione:** 1900307-indica la data di creazione del file e la relativa posizione nella sequenza di rilascio, come indicato di seguito:
  - **Anno:** 19 (2019)
  - **Numero di rilascio:** 003 (terza versione dell'anno)
  - **Numero di versione del prodotto:** 07 (Surface Pro 6 è ufficialmente la settima versione di Surface Pro)
- **Revisione della versione:** 0 (prima versione di questa versione)

## Scopri di più

- [Scaricare driver e firmware per Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware)
- [Come gestire gli aggiornamenti di Surface driver in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [Distribuire applicazioni con Configuration Manager](https://docs.microsoft.com/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di endpoint Configuration Manager](https://docs.microsoft.com/configmgr/)
- [Documentazione di Microsoft Deployment Toolkit](https://docs.microsoft.com/configmgr/mdt/)
- [Distribuire Windows10 con Microsoft Deployment Toolkit](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Distribuire Windows 10 ai dispositivi Surface con Microsoft Deployment Toolkit](https://docs.microsoft.com/surface/deploy-windows-10-to-surface-devices-with-mdt)  
- [Gestione di Intune delle impostazioni UEFI di Surface](https://docs.microsoft.com/surface/surface-manage-dfci-guide)
- [Ignite 2019: annuncia la gestione remota delle impostazioni di Surface UEFI da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).
- [Creare circuiti di distribuzione per gli aggiornamenti di Windows10](https://docs.microsoft.com/windows/deployment/update/waas-deployment-rings-windows-10-updates)

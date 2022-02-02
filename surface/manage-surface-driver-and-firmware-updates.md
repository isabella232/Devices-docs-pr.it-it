---
title: Gestire e installare gli aggiornamenti di driver e firmware per Surface
description: Questo articolo fornisce collegamenti a pacchetti scaricabili contenenti aggiornamenti di driver e firmware per i dispositivi Surface e spiega le soluzioni di gestione e distribuzione disponibili.
ms.assetid: CD1219BA-8EDE-4BC8-BEEF-99B50C211D73
ms.reviewer: ''
manager: laurawi
keywords: Surface, Surface Pro 8, Surface Go, Surface Laptop, Surface Studio, Surface Pro 3, firmware, aggiornamento, dispositivo, gestire, distribuire, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 12/14/2021
ms.openlocfilehash: 6cfe5f44c156c8042172741739fffbfed3ceba07
ms.sourcegitcommit: e7d95d583429169eb65aae9034eab2347b1f04a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2022
ms.locfileid: "12338579"
---
# <a name="manage-and-deploy-surface-driver-and-firmware-updates"></a>Gestire e installare gli aggiornamenti di driver e firmware per Surface

La modalità di gestione degli aggiornamenti di driver e firmware di Surface può variare a seconda dei requisiti dell'ambiente e dell'organizzazione. Nelle organizzazioni di grandi dimensioni, gli amministratori IT in genere effettuano le distribuzioni internamente e allocano tempo per testare gli aggiornamenti prima di  rollarli nei dispositivi degli utenti.

> [!NOTE]
> Questo articolo è destinato ai professionisti IT e agli agenti di supporto tecnico e si applica solo ai dispositivi Surface. Per informazioni su come installare gli aggiornamenti di Surface o il firmware in un dispositivo principale, vedi [Scaricare driver e firmware per Surface](https://support.microsoft.com/help/4023505).

Mentre le soluzioni di distribuzione software di livello aziendale continuano a evolversi, la logica aziendale per la gestione centralizzata degli aggiornamenti rimane la stessa: mantenere la sicurezza dei dispositivi Surface e mantenerli aggiornati con i miglioramenti più recenti del sistema operativo e delle funzionalità. Ciò è essenziale per mantenere un ambiente di produzione stabile e garantire che agli utenti non venga impedito di essere produttivi.

## <a name="whats-in-surface-driver-and-firmware-updates"></a>Cosa c'è negli aggiornamenti del firmware e del driver di Surface

Windows file .msi installer contengono tutti gli aggiornamenti cumulativi di driver e firmware necessari per i dispositivi Surface. I pacchetti di aggiornamento possono includere alcuni o tutti i componenti seguenti:

- Wi-Fi e LTE
- Video
- Unità a stato solido
- Modulo aggregatore di sistema (SAM)
- Batteria
- Controller tastiera
- Controller incorporato (EC)
- Motore di gestione (ME)
- Interfaccia UEFI (Unified Extensible Firmware Interface)

## <a name="download-msi-files"></a>Scaricare .msi file

Questa sezione fornisce collegamenti diretti ai pacchetti scaricabili contenenti aggiornamenti di driver e firmware per i dispositivi Surface. 

1. Selezionare Windows 10 o Windows 11 in base alle esigenze. 
2. Per i dispositivi con .msi file, seleziona il nome del file .msi corrispondente al modello Surface e alla versione di Windows distribuiti nell'organizzazione.  


| Dispositivo Surface                                                                                                                                        | Downloadable .msi                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ----------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Surface Pro**                                                                                                                                       | - [Surface Pro 8](https://www.microsoft.com/en-us/download/details.aspx?id=103503)<br>- [Surface Pro 7+ e Surface Pro 7+ (LTE)](https://www.microsoft.com/en-us/download/details.aspx?id=102633)<br>- [Surface Pro 7](https://www.microsoft.com/download/details.aspx?id=100419)<br>- [Surface Pro 6](https://www.microsoft.com/download/details.aspx?id=57514)<br>- [Surface Pro 5 (LTE)](https://www.microsoft.com/download/details.aspx?id=56278)<br>- [Surface Pro 5 (Wi-Fi)](https://www.microsoft.com/download/details.aspx?id=55484)<br>- [Surface Pro 4](https://www.microsoft.com/download/details.aspx?id=49498)<br>- [Surface Pro 3](https://www.microsoft.com/download/details.aspx?id=38826)<br>- [Surface Pro 2](https://www.microsoft.com/download/details.aspx?id=49042)<br>- [Surface Pro](https://www.microsoft.com/download/details.aspx?id=49038) |
| **Surface Laptop**                                                                                                                                    | - [Surface Laptop Go](https://www.microsoft.com/download/details.aspx?id=102261)<br>- [Surface Laptop 4 con processore Intel](https://www.microsoft.com/download/details.aspx?id=102924)<br>- [Surface Laptop 4 con processore AMD](https://www.microsoft.com/download/details.aspx?id=102923)<br>- [Surface Laptop 3 con processore Intel](https://www.microsoft.com/download/details.aspx?id=100429)<br>- [Surface Laptop 3 con processore AMD](https://www.microsoft.com/download/details.aspx?id=100428)<br>- [Surface Laptop 2](https://www.microsoft.com/download/details.aspx?id=57515)<br>- [Surface Laptop](https://www.microsoft.com/en-us/download/details.aspx?id=55489)                                                                                                                                                                                    |
| **Surface Laptop Studio**                                                                                                                             | - [Surface Laptop Studio](https://www.microsoft.com/en-us/download/details.aspx?id=103505)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| **Surface Book**                                                                                                                                      | - [Surface Book 3](https://www.microsoft.com/download/details.aspx?id=101315)<br>- [Surface Book 2](https://www.microsoft.com/download/details.aspx?id=56261)<br>- [Surface Book](https://www.microsoft.com/download/details.aspx?id=49497)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| **Surface Go**                                                                                                                                        | - [Surface Go 3](https://www.microsoft.com/en-us/download/details.aspx?id=103504)<br>- [Surface Go 2](https://www.microsoft.com/download/details.aspx?id=101304)<br>- [Surface Go (Wi-Fi)](https://www.microsoft.com/download/details.aspx?id=57439)<br>- [Surface Go (LTE)](https://www.microsoft.com/download/details.aspx?id=57601)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **Surface Studio**                                                                                                                                    | - [Surface Studio 2](https://www.microsoft.com/download/details.aspx?id=57593)<br>- [Surface Studio](https://www.microsoft.com/download/details.aspx?id=54311)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Surface 3**                                                                                                                                         | - [Surface 3 (Wi-Fi)](https://www.microsoft.com/download/details.aspx?id=49040)<br>- [Surface 3 (LTE) - ATT](https://www.microsoft.com/download/details.aspx?id=49039)<br>- [Surface 3 (LTE) - Verizon](https://www.microsoft.com/download/details.aspx?id=49920)<br>- [Surface 3 (LTE) - Nord America Carrier Unlocked](https://www.microsoft.com/download/details.aspx?id=49037)<br>- [Surface 3 (LTE) - Al di fuori del Nord America e Y!mobile in Giappone](https://www.microsoft.com/download/details.aspx?id=49041)                                                                                                                                                                                                                                                                                                                                                   |
| **Surface Hub in** [**esecuzione Windows 10 Pro o Windows 10 Enterprise**](/surface-hub/surface-hub-2s-migrate-os)   | - [Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| **Surface Hub esecuzione Windows 10 Teams 2020 Update**                                                                                                  | - Vedere [Manage Windows updates on Surface Hub](/surface-hub/manage-windows-updates-for-surface-hub)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| **Surface Dock 2**                                                                                                                                    | - [Surface Dock 2](https://www.microsoft.com/download/details.aspx?id=101317)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

 

> [!TIP]
> Per i dispositivi precedenti che includono file separati per diverse versioni Windows, seleziona il nome del file .msi corrispondente al modello Surface e alla versione di Windows. Il .msi file include il numero minimo di build Windows necessario per installare i driver e il firmware. Ad esempio, per aggiornare un Surface Book 2 con build 18362 di Windows 10, scegliere **SurfaceBook2_Win10_18362_19.101.13994.msi.** Per un Surface Book 2 con build 16299 di Windows 10, scegliere **SurfaceBook2_Win10_16299_1803509_3.msi**.

## <a name="central-update-management-in-commercial-environments"></a>Gestione centrale degli aggiornamenti in ambienti commerciali

Strumenti per la gestione dei dispositivi, inclusi gli aggiornamenti di driver e firmware, inclusi in [Microsoft Endpoint Manager](https://devicemanagement.microsoft.com/). 

### <a name="manage-updates-with-configuration-manager-and-intune"></a>Gestire gli aggiornamenti con Configuration Manager e Intune

Microsoft Endpoint Configuration Manager consente di sincronizzare e distribuire gli aggiornamenti del firmware e dei driver di Surface con il client di Configuration Manager. L'Microsoft Intune consente di visualizzare tutti i dispositivi gestiti, co-gestiti e gestiti dal partner in un'unica posizione. Questa è la soluzione consigliata per le organizzazioni di grandi dimensioni per gestire gli aggiornamenti di Surface.

Per la procedura dettagliata, vedere le risorse seguenti:

- [Gestire gli aggiornamenti dei driver di Surface in Configuration Manager](manage-surface-driver-updates-configuration-manager.md)
- [Distribuire applicazioni con Configuration Manager](/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di Endpoint Configuration Manager](/configmgr/)

### <a name="manage-updates-with-microsoft-deployment-toolkit"></a>Gestire gli aggiornamenti con Microsoft Deployment Toolkit

Microsoft Deployment Toolkit (MDT) è incluso in Endpoint Configuration Manager. A seconda dell'ambiente, contiene strumenti di distribuzione facoltativi che è possibile utilizzare.  Questi includono Windows Assessment and Deployment Kit (Windows ADK), Windows System Image Manager (Windows SIM), Deployment Image Servicing and Management (DISM) e User State Migration Tool (USMT). Puoi scaricare la versione più recente di MDT dalla pagina [di download di Microsoft Deployment Toolkit download](https://www.microsoft.com/download/details.aspx?id=54259).

Per la procedura dettagliata, vedere le risorse seguenti:

- [Documentazione di Microsoft Deployment Toolkit](/configmgr/mdt/)
- [Prepararsi per la distribuzione con MDT](/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)

Per istruzioni su come distribuire gli aggiornamenti tramite Endpoint Configuration Manager, vedi [Distribuire applicazioni con Configuration Manager](/configmgr/apps/deploy-use/deploy-applications). Per istruzioni su come distribuire gli aggiornamenti tramite MDT, vedi [Distribuire un'immagine Windows 10 con MDT](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt).

**Firmware e driver di WindowsPE e Surface**

Endpoint Configuration Manager e MDT usano entrambi Windows Preinstallation Environment (WindowsPE) durante il processo di distribuzione.Endpoint Configuration Manager and MDT both use the Windows Preinstallation Environment (WindowsPE) during the deployment process. WindowsPE supporta solo un set limitato di driver di base, ad esempio schede di rete e controller di archiviazione. I driver Windows componenti che non fanno parte di WindowsPE potrebbero generare errori. Come procedura consigliata, è possibile evitare tali errori configurando il processo di distribuzione in modo che utilizzi solo i driver necessari durante la fase WindowsPE.

### <a name="endpoint-configuration-manager"></a>Endpoint Configuration Manager

A partire da Endpoint Configuration Manager, puoi sincronizzare e distribuire gli aggiornamenti del firmware e dei driver di Microsoft Surface usando il client di Configuration Manager. Per altre informazioni, vedi Kb 4098906, [Gestire gli aggiornamenti dei driver di Surface in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager).

## <a name="supported-devices"></a>Dispositivi supportati

I file .msi scaricabili sono disponibili per i dispositivi Surface Pro 2 e versioni successive (ad eccezione di Surface Pro X che viene eseguito Windows 10 su ARM).

## <a name="managing-firmware-with-dfci"></a>Gestione del firmware con DFCI

Grazie ai profili DFCI (Device Firmware Configuration Interface) incorporati [in Intune](/intune/configuration/device-firmware-configuration-interface-windows), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning a tocco zero, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza (incluse le opzioni di avvio e le periferiche incorporate) e mette a punto le basi per scenari di sicurezza avanzati in futuro. Per ulteriori informazioni, vedere le pagine seguenti:

- [Gestire DFCI nei dispositivi Surface](surface-manage-dfci-guide.md)
- [Ignite 2019: Annuncio della gestione remota delle impostazioni UEFI di Surface da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).

## <a name="best-practices-for-update-deployment-processes"></a>Procedure consigliate per i processi di distribuzione degli aggiornamenti

Per mantenere un ambiente stabile, è consigliabile mantenere la parità con la versione più recente di Windows 10.  Per suggerimenti sulle procedure consigliate, vedere [Prepare servicing strategy for Windows client updates](/windows/deployment/update/waas-deployment-rings-windows-10-updates).

### <a name="surface-msi-naming-convention"></a>Convenzione di denominazione .msi Surface

Da agosto 2019, .msi file utilizzano la convenzione di denominazione seguente:

- *Product* _*Windows release*_ *Windows build numberVersion*_**_ *numberRevision del numero di versione (in genere zero)*.

**Esempio**

- SurfacePro6_Win10_18362_19.073.44195_0.msi

Questo nome di file fornisce le informazioni seguenti:

- **Prodotto:** SurfacePro6
- **Windows:** Win10
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
- **Windows:** Win10
- **Build:** 16299
- **Version:** 1900307 : mostra la data di creazione del file e la relativa posizione nella sequenza di rilascio, come indicato di seguito:
  - **Anno:** 19 (2019)
  - **Numero di rilascio:** 003 (terza versione dell'anno)
  - **Numero di versione del prodotto:** 07 (Surface Pro 6 è ufficialmente la settima versione di Surface Pro)
- **Revisione della versione:** 0 (prima versione di questa versione)

## <a name="learn-more"></a>Scopri di più

- [Preparare la strategia di manutenzione per gli aggiornamenti del client Windows](/windows/deployment/update/waas-deployment-rings-windows-10-updates)
- [Gestire gli aggiornamenti dei driver di Surface in Configuration Manager](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager)
- [Distribuire applicazioni con Configuration Manager](/configmgr/apps/deploy-use/deploy-applications)
- [Documentazione di Endpoint Configuration Manager](/configmgr/)
- [Documentazione di Microsoft Deployment Toolkit](/configmgr/mdt/)
- [Prepararsi per la distribuzione con MDT](/windows/deployment/deploy-windows-mdt/deploy-windows-10-with-the-microsoft-deployment-toolkit)
- [Gestire DFCI nei dispositivi Surface](surface-manage-dfci-guide.md)
- [Ignite 2019: Annuncio della gestione remota delle impostazioni UEFI di Surface da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).


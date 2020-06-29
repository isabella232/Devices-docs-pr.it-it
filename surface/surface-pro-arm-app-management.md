---
title: Distribuzione, gestione e manutenzione di Surface Pro X
description: In questo articolo viene fornita una panoramica delle considerazioni fondamentali per la distribuzione, la gestione e la manutenzione di Surface Pro X.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: high
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 4/15/2020
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: d1e7aa41f8219f0ae6ccd81a36fa0fc142dd1c3c
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833201"
---
# Distribuzione, gestione e manutenzione di Surface Pro X

## Introduzione

Ideato per gestire i requisiti commerciali ad alte prestazioni, Surface Pro X è un precursore, incorpora il processore più potente mai rilasciato su un dispositivo ARM, il chipset Microsoft SQ1 ARM.

Alimentato da una CPU a 3 GHz e da una GPU teraflop 2.1, Surface Pro X offre un'esperienza di Windows completa. La durata della batteria di 13 ore e l'LTE 4G integrato lo rendono ideale per gli operatori di telefonia mobile di prima linea e professionisti in campo finanziario, legale e medico o per qualsiasi altro ruolo che richiede una durata della batteria estesa e funzionalità di connettività continua.

Surface Pro X è progettato quasi esclusivamente per un ambiente moderno basato su cloud, incentrato su Microsoft 365, Intune e Windows Autopilot. In questo articolo vengono illustrate le considerazioni più importanti per la distribuzione, la gestione e la manutenzione di Surface Pro X.

## Distribuzione di Surface Pro X

Per un'esperienza ottimale, distribuisci Surface Pro X tramite Windows Autopilot con l'assistenza di un Microsoft Cloud Solution Provider o tramite self-provisioning con profili di distribuzione di Windows Autopilot e relative funzionalità. Per ulteriori informazioni, fai riferimento a:

- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md)
- [Panoramica di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)

La distribuzione di Autopilot presenta diversi vantaggi: consente di usare il sistema operativo di cui è stato eseguito il provisioning in fabbrica, semplificato per la distribuzione automatica per includere la preinstallazione di Office Pro Plus.

Le organizzazioni che usano già soluzioni moderne per la gestione, la sicurezza e la produttività sono ben posizionate per sfruttare le funzionalità esclusive relative alle prestazioni di Surface Pro X. Anche i clienti che usano le app line-of-business moderne, le app del Microsoft store (UWP) o le soluzioni desktop remoto possono trarne vantaggio.

## Considerazioni sulla distribuzione basate su immagini

MDT (Microsoft Deployment Toolkit) e Microsoft Endpoint Configuration Manager (in precedenza System Center Configuration Manager) attualmente non supportano Surface Pro X per la distribuzione del sistema operativo. I clienti che si affidano alla distribuzione basata su immagini devono considerare Surface Pro 7 mentre continuano a valutare il momento giusto per la transizione al cloud.

## Gestione dei dispositivi Surface Pro X

### Intune

Un componente di Microsoft Enterprise Mobility + Security, Intune si integra con Azure Active Directory per il controllo delle identità e degli accessi e fornisce la gestione granulare dei dispositivi Surface Pro X registrati. I criteri di gestione di dispositivi mobili (MDM) di Intune presentano numerosi vantaggi rispetto agli strumenti locali meno recenti, ad esempio i criteri di gruppo di Windows. Sono inclusi i tempi di accesso al dispositivo più veloci e un catalogo semplificato di criteri che consentono la gestione completa dei dispositivi dal cloud. Ad esempio, è possibile gestire LTE utilizzando i profili eSIM per configurare i piani dati e distribuire i codici di attivazione a più dispositivi.<br> 

Per ulteriori informazioni sull'utilizzo di Intune, fare riferimento alla [documentazione di Intune](https://docs.microsoft.com/intune/).

### Gestione condivisa

Una volta eseguita la distribuzione in Autopilot, puoi aggiungere dispositivi Surface Pro X a Azure AD o Active Directory (Aggiunta ad Azure AD ibrido) in cui potrai gestire i dispositivi con Intune o cogestirli con Endpoint Configuration Manager, che installerà il client ConfigMgr x86 a 32 bit.

### Soluzioni MDM di terze parti

Potresti utilizzare strumenti MDM di terze parti per gestire i dispositivi Surface Pro X. Per i dettagli, contattare il provider MDM.

### Software antivirus

Windows Defender ti aiuta a proteggere Windows 10 su pc basati su ARM per la durata supportata del dispositivo Windows 10. 

Non è possibile installare alcuni software antivirus di terze parti su un qualsiasi PC Windows 10 su un processore basato su ARM. La collaborazione con provider di software antivirus di terze parti continua per la disponibilità di app antivirus nei PC basati su ARM. Contatta il provider del software antivirus per capire quando saranno disponibili le app.

## Manutenzione di Surface Pro X

Surface Pro X supporta Windows 10 versione 1903 e successive. Come dispositivo basato su ARM, dispone di requisiti specifici per la manutenzione dei driver e del firmware più recenti. 

Surface Pro X è stato progettato per usare Windows Update per semplificare il processo di aggiornamento dei driver e del firmware sia per gli utenti domestici che per gli utenti business. Utilizzare le impostazioni predefinite per ricevere gli aggiornamenti automatici.  Per verificare:

1. Vai a **Start** > **Impostazioni > Aggiornamento e sicurezza > Windows Update** > **Opzioni avanzate.**
2. In **Scegli come installare gli aggiornamenti,** seleziona **Automatico (scelta consigliata)**.

### Consigli per i clienti commerciali

- Usa Windows Update o Windows Update per le aziende per mantenere i driver e il firmware più recenti. Per altre informazioni, vedi [Distribuire gli aggiornamenti mediante Windows Update per le aziende](https://docs.microsoft.com/windows/deployment/update/waas-manage-updates-wufb).
- Se le procedure richiedono l'uso di un file .msi di Windows Installer, contatta il [supporto di Surface per le aziende](https://support.microsoft.com/help/4037645). 
- Per altre informazioni sulla distribuzione e la gestione degli aggiornamenti nei dispositivi Surface, vedere [Gestire e distribuire gli aggiornamenti di driver e firmware Surface](manage-surface-driver-and-firmware-updates.md).
- Nota che Windows Server Update Services (WSUS) non supporta la possibilità di distribuire driver e firmware a Surface Pro X.

## Esecuzione di app su Surface Pro X

La maggior parte delle app viene eseguita su PC Windows 10 basati su ARM con esclusioni limitate.

### App supportate

- La maggior parte delle app Win32 x86 viene eseguita su Surface Pro X.
- Le app ARM64 e Microsoft Store UWP native offrono un'esperienza utente eccellente che utilizza la velocità nativa completa del processore basato su ARM, ottimizzando la durata della batteria.
- App che usano driver progettati per un PC Windows 10 in esecuzione su un processore basato su ARM.

### Non supportato

- Le app x64 non verranno eseguite su un PC Windows 10 in esecuzione su un processore basato su ARM.

Per altre informazioni sull'esecuzione delle app su Surface Pro X, fai riferimento a:

- [Domande frequenti sul supporto per PC Windows 10 basati su ARM](https://support.microsoft.com/help/4521606)
- [Documentazione di Windows 10 su ARM](https://docs.microsoft.com/windows/arm)

## Desktop virtuali (VDI)

Desktop virtuale Windows consente l'accesso a desktop, applicazioni e dati di Windows su qualsiasi dispositivo o piattaforma di elaborazione, da qualsiasi posizione. Per ulteriori informazioni, fai riferimento al [sito di Desktop virtuale Windows](https://aka.ms/wvd). 

## Esplorazione con Surface Pro X

I browser più diffusi vengono eseguiti su Surface Pro X:

- Edge, Firefox, Chrome e Internet Explorer inclusi vengono tutti eseguiti su Surface Pro X.
- Edge e Firefox inclusi vengono eseguiti in modalità nativa e quindi hanno prestazioni avanzate su un PC Windows 10 in esecuzione su un processore basato su ARM.

## Installazione e utilizzo di Microsoft Office

- Usa Office 365 per un'esperienza ottimale su un PC Windows 10 su un processore basato su ARM.
- L'opzione "A portata di clic" di Office 365 installa Outlook, Word, Excel e PowerPoint, ottimizzati per essere eseguiti su un PC Windows 10 su un processore basato su ARM.
- Microsoft Teams viene eseguito in modo ottimale su Surface Pro X.
- Per le "versioni perpetue" di Office, ad esempio Office 2019, installare la versione a 32 bit.

## VPN

Per confermare se una VPN di terze parti specifica supporta un PC Windows 10 su un processore basato su ARM, contatta il provider VPN.

## Confronto delle funzionalità principali

Nelle seguenti tabelle viene visualizzata la disponibilità delle funzionalità principali selezionate su Surface Pro X con Windows 10 su ARM in confronto a Surface Pro 7 basato su Intel.

| Distribuzione                              | Surface Pro 7 | Surface Pro X | Note                                                                                                                           |
| --------------------------------------- | ------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Windows Autopilot                       | Sì           | Sì           |                                                                                                                                 |
| Supporto per l'avvio di rete (PXE)          | Sì           | No           |                                                                                                                                 |
| Progettazione configurazione di Windows          | Sì           | No            | Non consigliato per Surface Pro X.                                                                                              |
| WinPE                                   | Sì           | Sì           | Non consigliato per Surface Pro X. Microsoft non fornisce il file. ISO necessario e i driver per il supporto di WinPE su Surface Pro X. |
| Endpoint Configuration Manager: distribuzione del sistema operativo(OSD) | Sì           | No            | Non è supportato su Surface Pro X.                                                                                              |
| MDT                                     | Sì           | No            | Non è supportato su Surface Pro X.                                                                                              |


| Gestione                                    | Surface Pro 7       | Surface Pro X | Note                                                                                 |
| --------------------------------------------- | ------------------- | ------------- | ------------------------------------------------------------------------------------- |
| Intune                                        | Sì                 | Sì           | Gestisci LTE con i profili eSIM.                                                        |
| Windows Autopilot                             | Sì                 | Sì           |                                                                                       |
| Azure AD (gestione condivisa)                      | Sì                 | Sì           | Possibilità di aggiungere Surface Pro X ad Azure AD o Active Directory (Aggiunta ad Azure AD ibrido). |
| Endpoint Configuration Manager                                          | Sì               | Sì           |                                                                                       |
| Accendi al ripristino CA                      | Sì                 | Sì           |                                                                                   |
| Toolkit di diagnostica per Surface (SDT) per le aziende | Sì                 | Sì           |                                                                                   |
| Aggiornamento del firmware di Surface Dock                  | Sì                 | No           |                                                                                   |
| Utilità Tag asset                             | Sì                 | Sì           |                                                                                   |
| SEMM (Surface Enterprise Management Mode)     | Sì | Parziale       | Nessuna opzione per disabilitare l'hardware in Surface Pro X a livello di firmware.                 |
| Strumento di configurazione UEFI di Surface                     | Sì |   No            | Nessuna opzione per disabilitare l'hardware. in Surface Pro X a livello di firmware.                |
| Strumento di gestione UEFI di Surface                          | Sì | Parziale       | Nessuna opzione per disabilitare l'hardware in Surface Pro X a livello di firmware.                 |


| Sicurezza                          | Surface Pro 7 | Surface Pro X | Note                                                                                                                                                                                                                                                                                                                                                |
| --------------------------------- | ------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| BitLocker                         | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                      |
| Windows Defender                  | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                      |
| Supporto per gli antivirus di terze parti | Sì           | Vedi nota      |Non è possibile installare alcuni software antivirus di terze parti su un qualsiasi PC Windows 10 su un processore basato su ARM. La collaborazione con provider di software antivirus di terze parti continua per la disponibilità di app antivirus nei PC basati su ARM. Contatta il provider del software antivirus per capire quando saranno disponibili le app. |
| Accesso condizionale                | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                      |
| Avvio protetto                       | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                      |
| Windows Information Protection    | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                      |
| Surface Data Eraser (SDE)         | Sì           | Sì           |                                                                                                                                                                                                                                                                                                                                                     
## Domande frequenti

### Posso distribuire Surface Pro X con MDT o Endpoint Configuration Manager?

The Microsoft Deployment Toolkit (MDT) e Microsoft Endpoint Configuration Manager attualmente non supportano Surface Pro X per la distribuzione del sistema operativo. I clienti che si affidano alla distribuzione basata su immagini devono considerare Surface Pro 7 mentre continuano a valutare il momento giusto per la transizione al cloud.

### Come posso distribuire Surface Pro X?

Distribuisci Surface Pro X tramite Windows Autopilot.

### Sarà disponibile un ripristino bare metal?

Sì.

### Per gestire Surface Pro X è necessario Intune?

Intune è consigliato ma non obbligatorio. Una volta eseguita la distribuzione in Autopilot, puoi aggiungere dispositivi Surface Pro X a Azure AD o Active Directory (Aggiunta ad Azure AD ibrido) in cui potrai gestire i dispositivi con Intune o cogestirli con Endpoint Configuration Manager, che installerà il client ConfigMgr x86 a 32 bit.

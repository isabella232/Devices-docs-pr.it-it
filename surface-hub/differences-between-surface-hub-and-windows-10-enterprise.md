---
title: Nozioni fondamentali del sistema operativo (Surface Hub)
description: Questo argomento illustra gli aspetti univoci del sistema operativo Windows 10 team e la sua differenza rispetto a Windows 10 Enterprise.
keywords: cronologia delle modifiche
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 92a634e897d3e0c9163fe092aaf7992f625de991
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833146"
---
# Nozioni fondamentali del sistema operativo (Surface Hub)

Il sistema operativo di Surface Hub, Windows 10 Team, è basato su Windows 10 Enterprise e fornisce un supporto avanzato per la gestione aziendale, la sicurezza e altre funzionalità. Esistono tuttavia alcune importanti differenze tra le due versioni. Mentre l'edizione Enterprise è progettata per i PC, Windows 10 Team è completamente progettato per gli schermi di grandi dimensioni e le sale riunioni. Durante la valutazione dei requisiti di sicurezza e di gestione per Surface Hub, è consigliabile considerarlo come un nuovo sistema operativo. Questo articolo illustra le principali differenze tra Windows 10 Team in Surface Hub e Windows 10 Enterprise, descrivendo il significato di queste differenze per le organizzazioni.

## Interfaccia utente

### Shell (interfaccia utente del sistema operativo)

La shell di Surface Hub è completamente progettata per l'ottimizzazione per il tocco e gli schermi di grandi dimensioni. Non viene usata la stessa shell di Windows 10 Enterprise.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Le impostazioni relative ai controlli nella shell di Windows 10 Enterprise non vengono applicate per Surface Hub.

### Schermata di blocco e screen saver

Surface Hub non dispone di una schermata di blocco o di uno screen saver, ma include una funzionalità simile denominata schermata iniziale. La schermata iniziale mostra le riunioni pianificate dal calendario dell'account del dispositivo e contiene comandi per accedere facilmente alle principali app di Surface Hub: Skype for Business, Lavagna e Connessione.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Le impostazioni per la schermata di blocco, il timeout dello schermo e lo screen saver non vengono applicate per Surface Hub.

### Accesso dell'utente

Surface Hub è progettato per essere usato in spazi comuni, ad esempio sale riunioni. A differenza dei PC Windows, tutti gli utenti possono utilizzare un dispositivo Surface Hub senza effettuare l'accesso. Per abilitare questa funzionalità in comune, Surface Hub non supporta l'accesso Windows allo stesso modo di Windows 10 Enterprise (ad esempio, l'accesso di un utente al sistema operativo e l'utilizzo delle stesse credenziali in tutto il sistema operativo). Al contrario, c'è sempre un utente con privilegi limitati, autenticato automaticamente, locale che è connesso a Surface Hub. Non supporta la registrazione di utenti aggiuntivi, inclusi gli utenti amministratori (ad esempio, quando un amministratore accede, non viene connesso al sistema operativo).

Gli utenti possono accedere a un dispositivo Surface Hub, ma non verranno registrati nel sistema operativo. Quando, ad esempio, un utente accede a App o a Riunioni e file, l'utente viene registrato solo nelle app o nei servizi, non nel sistema operativo. Di conseguenza, l'utente connesso è in grado di recuperare i file cloud e le riunioni personali archiviati nel cloud e queste credenziali vengono eliminate quando viene attivata **Fine sessione**.


*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> In generale, Surface Hub usa funzionalità di blocco anziché il controllo dell'accesso utente per applicare la sicurezza. I criteri relativi a requisiti delle password, accesso interattivo, account utente e controllo dell'accesso non vengono applicati per Surface Hub.

### Salvataggio ed esplorazione dei file

Gli utenti possono accedere a un set limitato di directory in Surface Hub:
- Musica
- Video
- Documenti
- Immagini
- Download

I file salvati in queste directory vengono eliminati quando l'utente preme **Termina sessione**. Per salvare il contenuto creato durante una riunione, gli utenti devono salvare i file in un'unità USB o in OneDrive.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I criteri relativi ad autorizzazioni di accesso e proprietà di file e cartelle non vengono applicati per Surface Hub. Gli utenti non possono esplorare directory di sistema e cartelle di rete o salvare file in tali posizioni.

## Applicazioni

### Applicazioni predefinite

Con alcune eccezioni, le app UWP (Universal Windows Platform) predefinite in Surface Hub sono disponibili anche nei PC Windows 10.

App UWP preinstallate in Surface Hub:
- Sveglie e orologio
- Calcolatrice
- Connessione
- Excel Mobile
- Hub di Feedback
- Esplora file*
- Informazioni di base
- Mappe
- Microsoft Edge
- Microsoft Power BI
- OneDrive
- Foto
- PowerPoint Mobile
- Impostazioni*
- Skype for Business*
- Store
- Lavagna*
- Word Mobile

*Le app con un asterisco (&ast;) sono specifiche di Surface Hub*

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Usa le linee guida per Windows 10 Enterprise per determinare le funzionalità e i requisiti di rete per le app predefinite di Surface Hub.

### Installazione di app, driver e servizi

Per preservare la funzione di appliance del dispositivo, Surface Hub supporta solo l'installazione di app UWP (Universal Windows Platform) e non supporta l'installazione di app, servizi e driver Win32 classici. Inoltre, solo gli amministratori hanno accesso per l'installazione delle app UWP.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I dipendenti possono usare solo le app che sono state installate dagli amministratori, riducendo i rischi di uso involontario. Surface Hub non supporta l'installazione degli agenti Win32 richiesti dalla maggior parte degli strumenti di gestione e monitoraggio dei PC tradizionali.

## Sicurezza e blocco

Per consentire l'uso di Surface Hub negli spazi comuni, come le sale riunioni, il sistema operativo personalizzato del dispositivo implementa molte delle funzionalità di sicurezza e di blocco disponibili in Windows 10.

Surface Hub implementa queste funzionalità di sicurezza di Windows 10:
- [Avvio protetto UEFI](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview)
- [Integrità del codice modalità utente con Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Criteri di restrizione delle applicazioni con AppLocker](https://technet.microsoft.com/itpro/windows/keep-secure/applocker-overview)
- [Crittografia unità BitLocker](https://technet.microsoft.com/itpro/windows/keep-secure/bitlocker-overview)
- [Trusted Platform Module (TPM)](https://technet.microsoft.com/itpro/windows/keep-secure/trusted-platform-module-overview)
- [Windows Defender](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-in-windows-10)
- [Controllo dell'account utente](https://technet.microsoft.com/itpro/windows/keep-secure/user-account-control-overview) per l'accesso all'app Impostazioni

Queste funzionalità di Surface Hub offrono maggiore sicurezza:
- Firmware UEFI personalizzato
- Shell e menu Start personalizzati per limitare il dispositivo alle funzioni per le riunioni
- Esplora file personalizzato consente solo l'accesso ai file e alle cartelle nella cartella Documenti
- L'app Impostazioni personalizzata consente solo agli amministratori di modificare le impostazioni del dispositivo
- Il download di driver Plug and Play avanzati è disabilitato

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Prendi in considerazione queste funzionalità durante la valutazione della sicurezza per Surface Hub.

## Gestione

### Impostazioni del dispositivo

Le impostazioni del dispositivo possono essere configurate tramite l'app Impostazioni. L'app Impostazioni è personalizzata per Surface Hub, ma contiene anche numerose impostazioni familiari di Windows 10 Desktop. Quando si apre l'app Impostazioni, viene visualizzata una richiesta di Controllo dell'account utente per verificare le credenziali dell'amministratore, ma in questo modo non viene eseguito l'accesso come amministratore.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I dipendenti possono usare Surface Hub per le riunioni, ma non possono modificare le impostazioni del dispositivo. Oltre a garantire il blocco delle funzionalità, questo assicura che il dispositivo venga usato solo per le riunioni.

### Funzionalità di amministrazione

Le funzionalità amministrative di Windows 10 Enterprise, ad esempio Microsoft Management Console, Esegui, il prompt dei comandi, PowerShell, l'editor del Registro di sistema, il Visualizzatore eventi e Gestione attività, non sono supportate in Surface Hub. L'app Impostazioni contiene tutte le funzionalità amministrative disponibili in locale in Surface Hub.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I dispositivi Surface Hub non vengono gestiti come PC tradizionali. Usa MDM per configurare le impostazioni e OMS per controllare il dispositivo Surface Hub.

### Gestione e monitoraggio remoti

Surface Hub supporta la gestione remota tramite soluzioni di gestione di dispositivi mobili (MDM) come [Microsoft Intune](https://docs.microsoft.com/intune/) e il monitoraggio tramite [Azure monitor](https://azure.microsoft.com/services/monitor/). 

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Surface Hub non supporta l'installazione degli agenti Win32 richiesti dalla maggior parte degli strumenti di gestione e monitoraggio dei PC tradizionali, come System Center Operations Manager.

### Criteri di gruppo

Surface Hub non supporta i criteri di gruppo di Windows, incluso il controllo. Usa invece MDM per applicare i criteri per il dispositivo Surface Hub. Per altre informazioni su MDM, vedi [Gestire le impostazioni con un provider MDM](manage-settings-with-mdm-for-surface-hub.md).

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Usa MDM per gestire Surface Hub invece dei criteri di gruppo.

### Assistenza remota

Surface Hub non supporta l'assistenza remota.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I criteri relativi all'assistenza remota non vengono applicati per Surface Hub.

## Rete

### Aggiunta a un dominio e ad Azure Active Directory (Azure AD) 

Surface Hub usa l'aggiunta a un dominio e l'aggiunta ad Azure AD principalmente per fornire un gruppo di amministratori basato su directory. Gli utenti non possono accedere con un account di dominio. Per altre informazioni, vedi [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md).

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I criteri di gruppo non vengono applicati quando un dispositivo Surface Hub viene aggiunto al dominio. I criteri relativi all'appartenenza al dominio non vengono applicati per Surface Hub.

### Accesso a risorse di dominio

Gli utenti possono eseguire l'accesso a Microsoft Edge per accedere a siti Intranet e risorse online (ad esempio, Office 365). Se Surface Hub è configurato con un account del dispositivo, il sistema lo usa per accedere a Exchange e Skype for Business. Surface Hub non supporta tuttavia l'accesso a risorse di dominio come condivisioni di file e stampanti.

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> I criteri relativi all'accesso a risorse di dominio non vengono applicati per Surface Hub.

<!--
### Endpoints



*Organization policies that this may affect:* <br> 
-->

### Dati di diagnostica

Il sistema operativo di Surface Hub usa il componente Esperienze utente connesse e telemetria di Windows 10 e per raccogliere e trasmettere i dati di diagnostica. Per altre informazioni, vedi [Configurare i dati di diagnostica di Windows nell'organizzazione](https://technet.microsoft.com/itpro/windows/manage/configure-windows-diagnostic-data-in-your-organization).

*Criteri dell'organizzazione su cui può influire questo aspetto:* <br> Configura i livelli di dati di diagnostica per Surface Hub nello stesso modo in cui sono configurati per Windows 10 Enterprise.

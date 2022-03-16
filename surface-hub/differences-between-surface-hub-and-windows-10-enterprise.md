---
title: Nozioni fondamentali del sistema operativo (Surface Hub)
description: In questo argomento vengono illustrati aspetti univoci del Windows 10 Team sistema operativo e le differenze rispetto a Windows 10 Enterprise.
keywords: cronologia delle modifiche
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/15/2022
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 6963a51b492bfbdc09da5ec667d091d62eed4569
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449239"
---
# <a name="operating-system-essentials-surface-hub"></a>Nozioni fondamentali del sistema operativo (Surface Hub)

Il sistema operativo di Surface Hub, Windows 10 Team, è basato su Windows 10 Enterprise e fornisce un supporto avanzato per la gestione aziendale, la sicurezza e altre funzionalità. Esistono tuttavia alcune importanti differenze tra le due versioni. Mentre l'edizione Enterprise è progettata per i PC, Windows 10 Team è completamente progettato per gli schermi di grandi dimensioni e le sale riunioni. Durante la valutazione dei requisiti di sicurezza e di gestione per Surface Hub, è consigliabile considerarlo come un nuovo sistema operativo. Questo articolo illustra le principali differenze tra Windows 10 Team in Surface Hub e Windows 10 Enterprise, descrivendo il significato di queste differenze per le organizzazioni.

A partire da settembre 2020, i clienti hanno la possibilità di eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2S. Per altre informazioni, vedi le risorse seguenti:

- [Annuncio della disponibilità di Windows 10 Pro e Enterprise in Surface Hub 2](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/announcing-the-availability-of-windows-10-pro-and-enterprise-on/ba-p/1624107).

- [Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2s-migrate-os.md)

## <a name="user-interface"></a>Interfaccia utente

### <a name="shell-os-user-interface"></a>Shell (interfaccia utente del sistema operativo)

La shell di Surface Hub è completamente progettata per l'ottimizzazione per il tocco e gli schermi di grandi dimensioni. Non viene usata la stessa shell di Windows 10 Enterprise.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Le impostazioni relative ai controlli nella shell di Windows 10 Enterprise non vengono applicate per Surface Hub.

### <a name="lock-screen-and-screensaver"></a>Schermata di blocco e screen saver

Surface Hub non dispone di una schermata di blocco o di uno screen saver, ma include una funzionalità simile denominata schermata iniziale. La schermata iniziale mostra le riunioni pianificate dal calendario dell'account del dispositivo e contiene comandi per accedere facilmente alle principali app di Surface Hub: Skype for Business, Lavagna e Connessione.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Le impostazioni per la schermata di blocco, il timeout dello schermo e lo screen saver non vengono applicate per Surface Hub.

### <a name="user-sign-in"></a>Accesso dell'utente

Surface Hub è progettato per essere usato in spazi comuni, ad esempio sale riunioni. A differenza dei PC Windows, tutti gli utenti possono utilizzare un dispositivo Surface Hub senza effettuare l'accesso. Per abilitare questa funzionalità in comune, Surface Hub non supporta l'accesso Windows allo stesso modo di Windows 10 Enterprise (ad esempio, l'accesso di un utente al sistema operativo e l'utilizzo delle stesse credenziali in tutto il sistema operativo). Al contrario, c'è sempre un utente con privilegi limitati, autenticato automaticamente, locale che è connesso a Surface Hub. Non supporta la registrazione di utenti aggiuntivi, inclusi gli utenti amministratori (ad esempio, quando un amministratore accede, non viene connesso al sistema operativo).

Gli utenti possono accedere a un dispositivo Surface Hub, ma non verranno registrati nel sistema operativo. Quando, ad esempio, un utente accede a App o a Riunioni e file, l'utente viene registrato solo nelle app o nei servizi, non nel sistema operativo. Di conseguenza, l'utente connesso è in grado di recuperare i file cloud e le riunioni personali archiviati nel cloud e queste credenziali vengono eliminate quando viene attivata **Fine sessione**.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- In generale, Surface Hub usa funzionalità di blocco anziché il controllo dell'accesso utente per applicare la sicurezza. I criteri relativi a requisiti delle password, accesso interattivo, account utente e controllo dell'accesso non vengono applicati per Surface Hub.

### <a name="saving-and-browsing-files"></a>Salvataggio ed esplorazione dei file

Gli utenti possono accedere a un set limitato di directory in Surface Hub:
- Musica
- Video
- Documenti
- Immagini
- Download

I file salvati in queste directory vengono eliminati quando l'utente preme **Termina sessione**. Per salvare il contenuto creato durante una riunione, gli utenti devono salvare i file in un'unità USB o in OneDrive.

*Criteri dell'organizzazione che possono influire:* - I criteri relativi alle autorizzazioni di accesso e alla proprietà di file e cartelle non si applicano Surface Hub. Gli utenti non possono esplorare directory di sistema e cartelle di rete o salvare file in tali posizioni.

## <a name="applications"></a>Applicazioni

### <a name="default-applications"></a>Applicazioni predefinite

Con alcune eccezioni, le app UWP (Universal Windows Platform) predefinite in Surface Hub sono disponibili anche nei PC Windows 10.

App UWP preinstallate in Surface Hub:

- Sveglie e orologio
- Calcolatrice
- Connessione
- Excel Mobile
- Hub di Feedback
- Esplora file
- Informazioni di base
- Mappe
- Microsoft Edge
- Microsoft Power BI
- Microsoft Teams
- Microsoft Whiteboard
- OneDrive
- Foto
- PowerPoint Mobile
- Impostazioni
- Store
- Suggerimenti
- Word Mobile

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Usa le linee guida per Windows 10 Enterprise per determinare le funzionalità e i requisiti di rete per le app predefinite di Surface Hub.

### <a name="installing-apps-drivers-and-services"></a>Installazione di app, driver e servizi

Per preservare la funzione di appliance del dispositivo, Surface Hub supporta solo l'installazione di app UWP (Universal Windows Platform) e non supporta l'installazione di app, servizi e driver Win32 classici. Inoltre, solo gli amministratori hanno accesso per l'installazione delle app UWP.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- I dipendenti possono usare solo le app che sono state installate dagli amministratori, riducendo i rischi di uso involontario. Surface Hub non supporta l'installazione degli agenti Win32 richiesti dalla maggior parte degli strumenti di gestione e monitoraggio dei PC tradizionali.

## <a name="security-and-lockdown"></a>Sicurezza e blocco

Per consentire l'uso di Surface Hub negli spazi comuni, come le sale riunioni, il sistema operativo personalizzato del dispositivo implementa molte delle funzionalità di sicurezza e di blocco disponibili in Windows 10. Per altre informazioni, vedi panoramica [Surface Hub sicurezza](surface-hub-security.md)

Surface Hub implementa queste funzionalità di sicurezza di Windows 10:

- [Avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot)
- [Controllo di applicazioni di Windows Defender e protezione dell'integrità del codice basata sulla virtualizzazione](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)
- [Criteri di restrizione delle applicazioni con AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview)
- [Crittografia unità BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview)
- [Trusted Platform Module (TPM)](/security/information-protection/tpm/trusted-platform-module-overview)
- [Antivirus Microsoft Defender in Windows](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows)
- [Controllo dell'account utente](/windows/security/identity-protection/user-account-control/user-account-control-overview) per l'accesso all'app Impostazioni

Queste funzionalità di Surface Hub offrono maggiore sicurezza:

- Firmware UEFI personalizzato
- Shell e menu Start personalizzati per limitare il dispositivo alle funzioni per le riunioni
- Esplora file personalizzato consente solo l'accesso ai file e alle cartelle nella cartella Documenti
- L'app Impostazioni personalizzata consente solo agli amministratori di modificare le impostazioni del dispositivo
- Il download di driver Plug and Play avanzati è disabilitato

*Criteri dell'organizzazione su cui può influire questo aspetto:*

- Prendi in considerazione queste funzionalità durante la valutazione della sicurezza per Surface Hub.

## <a name="management"></a>Gestione

### <a name="device-settings"></a>Impostazioni del dispositivo

Le impostazioni del dispositivo possono essere configurate tramite l'app Impostazioni. L'app Impostazioni è personalizzata per Surface Hub, ma contiene anche numerose impostazioni familiari di Windows 10 Desktop. Quando si apre l'app Impostazioni, viene visualizzata una richiesta di Controllo dell'account utente per verificare le credenziali dell'amministratore, ma in questo modo non viene eseguito l'accesso come amministratore.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- I dipendenti possono usare Surface Hub per le riunioni, ma non possono modificare le impostazioni del dispositivo. Oltre a garantire il blocco delle funzionalità, questo assicura che il dispositivo venga usato solo per le riunioni.

### <a name="administrative-features"></a>Funzionalità di amministrazione

Le funzionalità amministrative di Windows 10 Enterprise, ad esempio Microsoft Management Console, Esegui, Prompt dei comandi, PowerShell, Editor del Registro di sistema e Gestione attività non sono supportate in Surface Hub. L'app Impostazioni contiene tutte le funzionalità amministrative disponibili in locale in Surface Hub.

#### <a name="event-viewer"></a>Visualizzatore eventi

Windows 10 Team 2020 Update 2 aggiunge il supporto per il Visualizzatore eventi di Windows, che è identico al Visualizzatore eventi installato in [](/host-integration-server/core/windows-event-viewer1) Windows 10 Pro o Windows 10 Enterprise. 

**Per aprire visualizzatore eventi:**

1. Accedi **all'Impostazioni** app con credenziali di amministratore.
2. Selezionare **Aggiorna &** **SecurityLogs** >  e in Visualizzatore eventi selezionare **Apri**. 

Per ulteriori informazioni, vedere [visualizzatore Windows eventi](/host-integration-server/core/windows-event-viewer1).

### <a name="remote-management-and-monitoring"></a>Gestione e monitoraggio remoti

Surface Hub supporta la gestione remota tramite soluzioni di gestione dei dispositivi mobili (MDM), ad esempio [Microsoft Intune e il](/mem/intune/) monitoraggio tramite [Azure Monitor](/azure/azure-monitor/). 

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Surface Hub non supporta l'installazione degli agenti Win32 richiesti dalla maggior parte degli strumenti di gestione e monitoraggio dei PC tradizionali, come System Center Operations Manager.

### <a name="group-policy"></a>Criteri di gruppo

Surface Hub non supporta i criteri Windows di gruppo, incluso il controllo. Usa invece MDM per applicare i criteri per il dispositivo Surface Hub. Per altre informazioni su MDM, vedi [Gestire le impostazioni con un provider MDM](manage-settings-with-mdm-for-surface-hub.md).

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Usa MDM per gestire Surface Hub invece dei criteri di gruppo.

### <a name="remote-assistance"></a>Assistenza remota

Surface Hub non supporta l'assistenza remota.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- I criteri relativi all'assistenza remota non vengono applicati per Surface Hub.

## <a name="network"></a>Rete

### <a name="domain-join-and-azure-active-directory-azure-ad-join"></a>Aggiunta a un dominio e ad Azure Active Directory (Azure AD) 

Surface Hub usa l'aggiunta a un dominio e l'aggiunta ad Azure AD principalmente per fornire un gruppo di amministratori basato su directory. L'aggiunta ibrida non è supportata. Gli utenti non possono accedere con un account di dominio. Per altre informazioni, vedi [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md).

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Le impostazioni di Criteri di gruppo non vengono applicate quando un Surface Hub viene aggiunto al dominio. Le impostazioni dei criteri relative all'appartenenza al dominio non si applicano Surface Hub.

### <a name="accessing-domain-resources"></a>Accesso a risorse di dominio

Gli utenti possono eseguire l'accesso a Microsoft Edge per accedere a siti Intranet e risorse online (ad esempio, Office 365). Se Surface Hub è configurato con un account del dispositivo, il sistema lo usa per accedere a Exchange e Skype for Business. Surface Hub non supporta tuttavia l'accesso a risorse di dominio come condivisioni di file e stampanti.

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- I criteri relativi all'accesso a risorse di dominio non vengono applicati per Surface Hub.

### <a name="diagnostic-data"></a>Dati di diagnostica

Il sistema operativo di Surface Hub usa il componente Esperienze utente connesse e telemetria di Windows 10 e per raccogliere e trasmettere i dati di diagnostica. Per altre informazioni, vedi [Configurare i dati di diagnostica di Windows nell'organizzazione](/windows/privacy/configure-windows-diagnostic-data-in-your-organization).

*Criteri dell'organizzazione su cui può influire questo aspetto:* 

- Configura i livelli di dati di diagnostica per Surface Hub nello stesso modo in cui sono configurati per Windows 10 Enterprise.

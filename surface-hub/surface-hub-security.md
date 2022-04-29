---
title: Panoramica della sicurezza di Surface Hub
description: Questa pagina spiega la progettazione di misure di difesa avanzate di Surface Hub e descrive i miglioramenti riguardanti la sicurezza in Surface Hub 2S, le protezioni di sicurezza wireless e le funzionalità correlate.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: coveminer
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 01/26/2021
ms.localizationpriority: High
ms.openlocfilehash: 6d921fd1a418863eaf03434f2c27344470f12ca2
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497739"
---
# <a name="surface-hub-security-overview"></a>Panoramica della sicurezza di Surface Hub

Surface Hub fornisce un'esperienza di tipo appliance bloccata con firmware della piattaforma personalizzato che esegue il sistema operativo Windows 10 Team. Il dispositivo risultante utilizza il tradizionale chiosco multimediale di sicurezza "monouso", segue il metodo "eseguire solo ciò di cui si ha bisogno" e offre un approccio moderno. Sviluppato per supportare una ricca esperienza utente collaborativa, Surface Hub è protetto dalle minacce alla sicurezza in continua evoluzione.

Basato su Windows 10, Surface Hub offre una sicurezza moderna di classe enterprise che consente agli amministratori IT di applicare la protezione dei dati con BitLocker, Trusted Platform Module 2.0 (TPM), oltre alla sicurezza basata sul cloud con Windows Defender (noto anche come Microsoft Defender).

## <a name="defense-in-depth-security"></a>Misure di sicurezza avanzate

I protocolli di protezione si avviano non appena viene attivato Surface Hub. A partire dal livello del firmware, Surface Hub caricherà il sistema operativo e i suoi componenti solo in risposta a più controlli di sicurezza. Surface Hub utilizza misure di sicurezza avanzate che prevedono più livelli di sottocomponenti di protezione indipendenti per proteggere l'intero sistema in caso di guasto parziale. Questa strategia già utilizzata nel settore ha dimostrato di essere altamente efficace nell'attenuare potenziali exploit unilaterali e punti deboli nei sottocomponenti.

La moderna interfaccia UEFI (Unified Extensible Firmware Interface) è configurata staticamente e in modo sicuro da Microsoft per avviare solo un sistema operativo Windows 10 Team autenticato dalla memoria interna.  Per ogni riga di codice eseguita su Surface Hub viene verificata la firma prima dell'esecuzione. Solo le applicazioni firmate da Microsoft, come parte del sistema operativo o installate tramite Microsoft Store, possono essere eseguite su Surface Hub. Il codice o le app che non soddisfano questi requisiti sono bloccati.

I sistemi di sicurezza di Surface Hub includono quanto segue:

- **Difese in fase di avvio:** carica solo componenti del sistema operativo Surface Hub affidabili.
- **Difese del sistema operativo:** protegge dall'esecuzione di software o codice non autorizzato o dannoso.
- **Difese dell'interfaccia utente:** fornisce un'interfaccia utente sicura per gli utenti finali, impedendo l'accesso ad attività potenzialmente rischiose come l'esecuzione di eseguibili dalla riga di comando.

### <a name="boot-time-defenses"></a>Difese in fase di avvio

Il SoC ha un processore di sicurezza separato da ogni altra memoria centrale. Quando Surface Hub viene avviato per la prima volta, solo il processore di sicurezza si avvia prima di caricare qualsiasi altra cosa.

![Fasi di avvio di bootstrap dell'Hub che mostrano le protezioni del processore di sicurezza.](images/hub-sec-1.png)

#### <a name="secure-boot"></a>Avvio protetto

L'avvio protetto viene utilizzato per verificare che i componenti del processo di avvio, inclusi i driver e il sistema operativo, siano convalidati rispetto a un database di firme valide e note. Su Surface Hub, una firma specifica della piattaforma deve essere convalidata prima di poter caricare il sistema operativo Windows Team autorizzato. Questo aiuta a prevenire gli attacchi da un sistema clonato o modificato che esegue codice dannoso nascosto in quella che sembra essere un'esperienza utente normale.  Per altre informazioni, vedere [Panoramica di avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot).

### <a name="operating-system-defenses"></a>Difese del sistema operativo

Una volta verificato che il sistema operativo proviene da Microsoft e Surface Hub completa correttamente il processo di avvio, il dispositivo esamina il codice eseguibile. L'approccio alla protezione del sistema operativo prevede l'identificazione della firma del codice di tutti gli eseguibili, consentendo di caricare nel runtime solo quelli che superano le restrizioni. Questo metodo di firma del codice consente al sistema operativo di verificare l'autore e confermare che il codice non è stato modificato prima di essere eseguito sul dispositivo.

Surface Hub utilizza una funzionalità di firma del codice nota come UMCI (User Mode Code Integrity, Integrità del codice modalità utente) in Controllo di applicazioni di Windows (precedentemente noto come Device Guard). Le impostazioni dei criteri sono configurate per consentire solo le app che soddisfano uno dei seguenti requisiti:

- Le app della piattaforma UWP (Universal Windows Platform) (Microsoft Store) che sono [certificate ufficialmente](/windows/uwp/publish/the-app-certification-process).
- App firmate con l'esclusiva autorità di certificazione (CA) radice di produzione Microsoft, che può essere firmata solo da dipendenti Microsoft con accesso autorizzato a tali certificati.
- App firmate con l'esclusiva autorità di certificazione radice di produzione Surface Hub.

Il file di configurazione viene firmato utilizzando l'autorità di certificazione radice principale di produzione Microsoft progettata per impedire che le restrizioni vengano rimosse o modificate da terzi. Tutti gli altri eseguibili a questo punto vengono semplicemente bloccati a livello di runtime del sistema operativo e impediscono l'accesso alla potenza di elaborazione. Questa riduzione della superficie di attacco fornisce le seguenti protezioni:

- Nessuna modalità documento legacy
- Nessun modulo script legacy
- Nessun Vector Markup Language
- Nessun oggetto browser helper
- Nessun controllo ActiveX

Oltre a bloccare il codice non firmato o firmato in modo errato tramite l’interfaccia UMCI, Surface Hub utilizza il Controllo di applicazioni di Windows per bloccare i componenti di Windows, come il prompt dei comandi, PowerShell e Gestione attività. Queste misure di sicurezza rispecchiano la caratteristica di progettazione fondamentale di Surface Hub come dispositivo di elaborazione sicuro. Per ulteriori informazioni, vedere le pagine seguenti:

- [Panoramica di Controllo di applicazioni](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Controllo di applicazioni di Windows Defender e protezione dell'integrità del codice basata sulla virtualizzazione](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

### <a name="user-interface-defenses"></a>Difese dell'interfaccia utente

Mentre le difese al momento dell'avvio e le misure di sicurezza di blocco del sistema operativo offrono sicurezza di base, l'interfaccia utente fornisce un livello aggiuntivo progettato per ridurre ulteriormente il rischio. Per impedire al codice dannoso di raggiungere il dispositivo tramite i driver, Surface Hub non scarica i driver avanzati per i dispositivi plug and play (PnP). I dispositivi che sfruttano i driver di base, come chiavette USB o periferiche Surface Hub certificate (altoparlanti, microfoni, fotocamere) funzionano come previsto, ma non sarà lo stesso per i sistemi avanzati, ad esempio le stampanti.

Le difese dell'interfaccia utente, inoltre, semplificano l'interfaccia stessa, impedendo ulteriormente l'esecuzione di software o codice dannoso. I seguenti elementi dell'interfaccia utente di Surface Hub si aggiungono al livello di sicurezza principale fornito dalla firma del codice:

- **Esplora file:** Surface Hub include una funzione Esplora file personalizzata che consente di accedere rapidamente alle cartelle Musica, Video, Documenti, Immagini e Download, senza esporre gli utenti a file di sistema o di programma. Altre posizioni sul disco rigido locale non sono disponibili tramite Esplora file. Inoltre, molti tipi di file in esecuzione come .exe e .msi non possono essere eseguiti, fornendo un altro livello di sicurezza contro eseguibili potenzialmente dannosi.

- **Start e Tutte le app:** i componenti Start e Tutte le app di Surface Hub non espongono l'accesso al prompt dei comandi, a PowerShell o ad altri componenti di Windows bloccati tramite Controllo di applicazioni. Inoltre, la funzionalità di esecuzione di Windows generalmente accessibile su PC dalla casella di ricerca è disattivata per Surface Hub.

## <a name="security-enhancements-in-surface-hub-2s"></a>Miglioramenti riguardanti la sicurezza in Surface Hub 2S

Sebbene Surface Hub e Surface Hub 2S eseguano entrambi lo stesso software del sistema operativo, alcune funzionalità esclusive di Surface Hub 2S offrono funzionalità di gestione e sicurezza aggiuntive che consentono agli amministratori IT di eseguire le seguenti attività:

- Gestire le impostazioni UEFI con SEMM
- Ripristinare l'Hub con USB di avvio
- Proteggere l'account del dispositivo con rotazione della password

### <a name="manage-uefi-settings-with-semm"></a>Gestire le impostazioni UEFI con SEMM

L'interfaccia UEFI si trova tra le parti della piattaforma hardware sottostante e il sistema operativo. Su Surface Hub, un'implementazione UEFI personalizzata consente un controllo granulare su queste impostazioni e impedisce a qualsiasi entità non Microsoft la modifica delle impostazioni UEFI del dispositivo o l'avvio su un'unità rimovibile per modificare o cambiare il sistema operativo.

Ad un livello elevato, durante il processo di provisioning di fabbrica, l'interfaccia UEFI di Surface Hub è preconfigurata per abilitare l'avvio protetto ed è impostata per essere avviata solo dall'unità SSD (Solid State Drive) interna, con accesso ai menu UEFI bloccato e collegamenti rimossi. Ciò esegue il sealing all'accesso UEFI e garantisce che il dispositivo possa essere avviato solo nel sistema operativo Windows Team installato su Surface Hub.

Se gestiti tramite SEMM (Microsoft Surface Enterprise Management Mode), gli amministratori IT possono distribuire le impostazioni UEFI sui dispositivi Hub all'interno di un'organizzazione. Ciò include la possibilità di abilitare o disabilitare i componenti hardware integrati, proteggere le impostazioni UEFI da modifiche da parte di utenti non autorizzati e regolare le impostazioni di avvio.

![Impostazioni UEFI di Surface Hub.](images/hub-sec-2.png)

Gli amministratori possono implementare i dispositivi SEMM e Surface Hub 2S registrati utilizzando lo [Strumento di configurazione UEFI di Microsoft Surface](https://www.microsoft.com/download/details.aspx?id=46703) scaricabile. Per altre informazioni, vedere [Proteggere e gestire Surface Hub 2S con SEMM e UEFI](/surface-hub/surface-hub-2s-secure-with-uefi-semm).
Grazie a un certificato utilizzato per proteggere la configurazione da manomissione o rimozione non autorizzate, SEMM consente la gestione dei seguenti componenti:

- LAN cablata
- Fotocamera
- Bluetooth
- Wi-Fi
- Sensore di presenza
- Avvio di IPv6 per PXE
- Avvio alternativo
- Blocco ordine di avvio
- Avvio da USB
- Interfaccia di pagina riepilogativa UEFI
    - Dispositivi
    - Avvio
    - Data/ora

    
### <a name="recover-hub-with-bootable-usb"></a>Ripristinare l'Hub con USB di avvio

Surface Hub 2S consente agli amministratori di riportare il dispositivo alle impostazioni di fabbrica usando un'immagine di ripristino in appena 20 minuti. In genere, questa operazione è necessaria solo se Surface Hub non è più funzionante. Il ripristino è utile anche se è stata smarrita la chiave di Bitlocker o non si dispone più delle credenziali di amministratore nell'app Impostazioni.

### <a name="harden-device-account-with-password-rotation"></a>Proteggere l'account del dispositivo con rotazione della password

Surface Hub utilizza un account del dispositivo, noto anche come "account sala", per l'autenticazione con Exchange, Microsoft Teams e altri servizi. Quando si abilita la rotazione della password, Hub 2S genera automaticamente una nuova password ogni 7 giorni, composta da 15-32 caratteri con una combinazione di lettere maiuscole e minuscole, numeri e caratteri speciali. Poiché nessuno conosce la password, la rotazione della password dell'account del dispositivo attenua efficacemente il rischio associato a errore umano e potenziali attacchi alla sicurezza di ingegneria sociale.

## <a name="enterprise-grade-security"></a>Sicurezza di livello aziendale

Oltre alle configurazioni e alle funzionalità specifiche di Surface Hub descritte in questo documento, Surface Hub usa anche le funzionalità di sicurezza standard di Windows. tra cui:

- **BitLocker**: l'unità SSD di Surface Hub è dotata di BitLocker per proteggere i dati sul dispositivo e la sua configurazione segue gli standard del settore. Per altre informazioni, vedere [Panoramica di BitLocker](/windows-hardware/design/device-experiences/oem-secure-boot).
- **Windows Defender:** il motore antimalware di Windows Defender funziona continuamente su Surface Hub e si occupa di correggere automaticamente le minacce rilevate su Surface Hub. Il motore di Windows Defender riceve automaticamente gli aggiornamenti ed è gestito in modalità remota dagli amministratori IT. Windows Defender è un perfetto esempio di come funzionano le misure di difesa avanzate di Microsoft: se il malware riesce a trovare un modo per aggirare la soluzione di sicurezza basata sulla firma del codice, verrà comunque individuato qui. Per altre informazioni, vedere [Controllo di applicazioni di Windows Defender e protezione dell'integrità del codice basata sulla virtualizzazione](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control).
- **Driver plug and play:** Per impedire al codice dannoso di raggiungere il dispositivo tramite i driver, Surface Hub non scarica i driver avanzati per i dispositivi PnP (plug and play). Ciò consente ai dispositivi che utilizzano i driver di base come le chiavette USB di funzionare come previsto, bloccando invece i sistemi più avanzati come le stampanti.
- **Trusted Platform Module 2.0** Surface Hub dispone di un modulo dTMP (discrete Trusted Platform Module) basato sugli standard di settore per la generazione e l'archiviazione di chiavi e hash crittografici. Il dTPM protegge le chiavi utilizzate per la verifica delle fasi di avvio, la chiave master si BitLocker, la chiave di accesso senza password e altro. Il dTPM è conforme alla certificazione [FIPS 140-2 livello 2](/windows/security/threat-protection/fips-140-validation), lo standard di sicurezza informatica del governo degli Stati Uniti, ed è conforme alla certificazione [Common Criteria](/windows/security/threat-protection/windows-platform-common-criteria) utilizzata in tutto il mondo.

## <a name="wireless-security-for-surface-hub"></a>Sicurezza wireless per Surface Hub

Surface Hub utilizza la tecnologia Wi-Fi Direct/Miracast e gli standard 802.11, Wi-Fi Protected Access (WPA2) e Wireless Protected Setup (WPS) associati. Dato che il dispositivo supporta solo WPS (anziché la chiave precondivisa WPA2 (PSK) o WPA2 Enterprise), i problemi associati normalmente alla crittografia 802.11 sono stati semplificati a livello di progettazione.

Miracast è incluso nello standard Wi-Fi Display, che a sua volta è supportato dal protocollo Wi-Fi Direct. Questi standard sono supportati nei dispositivi mobili più recenti per la condivisione dello schermo e la collaborazione.

Il protocollo Wi-Fi Direct o Wi-Fi "peer-to-peer" (P2P) è uno standard rilasciato da Wi-Fi Alliance per le reti "ad hoc". Grazie ad esso, i dispositivi supportati possono comunicare direttamente e creare gruppi di reti senza utilizzare un punto di accesso Wi-Fi tradizionale o una connessione Internet.

La protezione per Wi-Fi Direct è fornita da WPA2 utilizzando lo standard WPS. I dispositivi possono essere autenticati utilizzando un pin numerico, un pulsante fisico o virtuale o un messaggio fuori banda mediante tecnologia NFC (Near Field Communication). Surface Hub supporta sia il comando tramite pulsante per impostazione predefinita sia i metodi con PIN. Per altre informazioni, vedere [Risoluzione dei problemi relativi alla sicurezza di Wi-Fi Direct con Surface Hub](/surface-hub/surface-hub-wifi-direct).

## <a name="learn-more"></a>Scopri di più

- [Panoramica di avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot)

- [Panoramica di Bitlocker](/windows/security/information-protection/bitlocker/bitlocker-overview)

- [Panoramica di Controllo di applicazioni](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control)

- [Proteggere e gestire Surface Hub 2S con SEMM e UEFI](/surface-hub/surface-hub-2s-secure-with-uefi-semm)

- [Risoluzione dei problemi relativi alla sicurezza di Wi-Fi Direct con Surface Hub](/surface-hub/surface-hub-wifi-direct)

- [Controllo di applicazioni di Windows Defender e protezione dell'integrità del codice basata sulla virtualizzazione](/windows/security/threat-protection/device-guard/introduction-to-device-guard-virtualization-based-security-and-windows-defender-application-control)

- [Strumenti di Surface per IT](https://www.microsoft.com/download/details.aspx?id=46703)

- [FIPS 140-2 livello2](/windows/security/threat-protection/fips-140-validation)

- [Certificazione Common Criteria](/windows/security/threat-protection/windows-platform-common-criteria)

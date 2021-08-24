---
title: Panoramica della protezione di Surface
description: Questo articolo fornisce una panoramica della sicurezza dei dispositivi Surface
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 06/04/2021
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: 193053745628b434c07a63f23a042e95fead32eb
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911807"
---
# <a name="surface-security-overview"></a>Panoramica della protezione di Surface

I recenti progressi nella ricerca sulla sicurezza dimostrano che, man appena più protezioni sono integrate nel sistema operativo e nei servizi connessi, gli utenti malintenzionati cercano altre vie di sfruttamento con il firmware che emerge come obiettivo principale.

Oggi, la gestione del firmware del dispositivo è un'esperienza incoerente e spesso coinvolge provider di terze parti che complicano il monitoraggio e la manutenzione del firmware. In definitiva, questo può limitare la capacità dei produttori di hardware di rilevare ed inviare aggiornamenti in tempo reale in risposta alle minacce.

Microsoft Surface usa un approccio unificato alla protezione del firmware e alla sicurezza dei dispositivi dal 2015 attraverso la completa proprietà end-to-end della progettazione hardware, lo sviluppo del firmware interno e un approccio olistico agli aggiornamenti e alla gestione dei dispositivi.

Per Surface, UEFI (Unified Extensible Firmware Interface) 1 viene mantenuto in-house, aggiornato regolarmente tramite Windows Update e distribuito senza problemi per la gestione tramite <sup> [](#references) Windows Autopilot, riducendo al minimo i rischi e massimizzando il controllo a livello di firmware prima dell'avvio del </sup> dispositivo. Microsoft fornisce la massima trasparenza della base di codice nel nostro UEFI tramite l'open source [Project Mu](https://microsoft.github.io/mu/) su GitHub, gestito da Microsoft Endpoint Manager.

## <a name="microsoft-designed-and-built-components"></a>Componenti progettati e creati da Microsoft

Ogni livello di Surface da chip a cloud viene sviluppato e gestito da Microsoft, offrendoti il massimo controllo, protezione proattiva e tranquillità ovunque e comunque il lavoro venga svolto. I dispositivi Surface vengono forniti con i protocolli di sicurezza più potenti che Microsoft offre e consente una gestione semplificata che riduce la complessità IT che consente agli utenti di rimanere concentrati sul proprio lavoro.

Surface guida la sicurezza attraverso un approccio di difesa approfondito utilizzando una suddivisione in livelli di sotto-componenti difensivi indipendenti. Da chip a cloud o UEFI che garantisce una radice di attendibilità all'intelligenza artificiale di Microsoft Defender for Endpoint che funziona per prevenire, rilevare, analizzare e rispondere alle minacce avanzate, Surface impone la posizione che l'integrato da Microsoft è meglio di bullone.

| Funzionalità                         | Descrizione                                                                                                                                                                                                                                                                                                                         | Scopri di più                                                                                                                                                                   |
| ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft Built UEFI            | Software che configura il dispositivo e avvia Windows 10<br>Controlla l'avvio iniziale del dispositivo e Windows 10, quindi fornisce servizi di runtime del firmware al sistema operativo. garantisce un controllo significativamente maggiore sull'hardware di un dispositivo tramite la gestione semm in ambiente prem e la gestione basata su cloud DFCI tramite Microsoft Endpoint Manager | [Gestire le impostazioni UEFI di Surface](manage-surface-uefi-settings.md)                                                                        |
| TPM fisico 2.0                | Trusted Platform Module - Microcontroller dedicato progettato per proteggere l'hardware tramite chiavi di crittografia integrate.<br>Crittografa e archivia le chiavi (BitLocker, Windows Hello, Credenziali AD,)<br>PCR - Registri di configurazione della piattaforma che protegge le misurazioni e le metriche rilevanti per rilevare le modifiche alla configurazione precedente  | [Panoramica della tecnologia Trusted Platform Module](/windows/security/information-protection/tpm/trusted-platform-module-overview)                 |
| Windows Hello for Business      | Sostituisce le password con l'autenticazione a due fattori avanzata su PC e dispositivi mobili. Questa autenticazione biometrica è costituita da un nuovo tipo di credenziale utente collegata a un dispositivo e che usa una biometria o un PIN.                                                                                                                   | [Funzionamento di Windows Hello for Business - Microsoft 365 Security](/windows/security/identity-protection/hello-for-business/hello-how-it-works) |
| Crittografia integrata           | La crittografia integrata è abilitata da BitLocker per proteggere e crittografare i dati e Windows Hello per abilitare l'accesso senza password, in combinazione con TPM fisico e UEFI.                                                                                                                                                                 | [BitLocker (Windows 10) - Microsoft 365 Security](/windows/security/information-protection/bitlocker/bitlocker-overview)                     |
| Microsoft Defender per endpoint | Fornisce una piattaforma di sicurezza degli endpoint aziendali progettata per aiutare le reti aziendali a prevenire, rilevare, analizzare e rispondere alle minacce avanzate.                                                                                                                                                                               | [Microsoft Defender per endpoint](/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)                 |

## <a name="factory-level-security-protocols-and-inspection"></a>Protocolli di sicurezza e ispezione a livello di fabbrica

Dal firmware al sistema operativo e da ogni componente hardware prima dell'assemblaggio finale, i dispositivi Surface sono al sicuro dagli attacchi della catena di approvvigionamento nelle nostre strutture di sviluppo e produzione fisicamente protette.

Per definizione, una catena di approvvigionamento sicura offre prodotti finiti che soddisfano gli obiettivi di qualità, prestazioni e operativi. In poche parole, una catena di approvvigionamento sicura garantisce che tutti i componenti siano autentici e liberi da manipolazioni o attacchi di manopolazione non autorizzati o dannosi. Produciamo dispositivi in factory altamente protette in cui tutto, dal firmware UEFI al sistema operativo, proviene direttamente da Microsoft. Non sono coinvolti fornitori di BIOS di terze parti. Questa è una parte importante del modo in cui proteggiamo gli attacchi della catena di approvvigionamento per i prodotti Surface. Abbiamo ridotto la superficie di attacco nel nostro UEFI rimuovendo qualsiasi codice inutilizzato, incluse le funzioni SMM della modalità di gestione del sistema che sono dispositivi non necessari.

La protezione delle strutture da attacchi esterni basati su Internet, intrusioni e altre minacce richiede un investimento continuo in aree chiave, tra cui:

- Ispezione e test rigorosi di tutti i componenti nelle posizioni finali dell'assemblaggio.
- Mantenimento di livelli elevati di sicurezza fisica in fabbrica.
- L'uso solo di Microsoft ha & firmware, driver e sistema operativo gestiti.
- Proteggere la logistica e la distribuzione attendibile dei dispositivi Surface direttamente ai rivenditori Microsoft.

Quando si esce dalla factory, Surface per le aziende dispositivi vengono protetti tramite Windows Update per tutto il ciclo di vita.

## <a name="advanced-windows-security-features"></a>Funzionalità Windows sicurezza avanzata

L'escalation degli attacchi di privilegi è il migliore amico di un attore malintenzionato e spesso mira a informazioni riservate archiviate in memoria. Questi tipi di attacchi possono trasformare una piccola compromissione della modalità utente in una compromissione completa del sistema operativo e del dispositivo. Per contrastare questi tipi di attacchi, Microsoft ha sviluppato la sicurezza basata su virtualizzazione (VBS) e l'integrità del codice protetto tramite Hypervisor (HVCI, anche comunemente noto come integrità della memoria). VBS e HVCI usano la potenza delle funzionalità hardware come la virtualizzazione per garantire una migliore protezione da malware comuni e sofisticati eseguendo operazioni di sicurezza riservate in un ambiente isolato.

Surface viene fornito con Windows funzionalità di sicurezza hardware avanzate abilitate per offrire ai clienti una sicurezza ancora più avanzata integrata e attivata per impostazione predefinita.

## <a name="virtualization-based-security"></a>Sicurezza basata su virtualizzazione

La sicurezza basata su virtualizzazione, o VBS, usa le funzionalità di virtualizzazione hardware per creare e isolare un'area di memoria sicura dal normale sistema operativo. Windows può usare questa "modalità sicura virtuale" per ospitare una serie di soluzioni di sicurezza, offrendo loro una protezione notevolmente maggiore dalle vulnerabilità nel sistema operativo e impedendo l'uso di exploit dannosi che tentano di sconfiggire le protezioni.

### <a name="hypervisor-enforced-code-integrity-hvci"></a>Hypervisor-Enforced del codice (HVCI)

HVCI usa VBS per rafforzare in modo significativo l'applicazione dei criteri di integrità del codice. L'integrità del codice in modalità kernel controlla tutti i driver e i file binari in modalità kernel prima che vengano avviati e impedisce il caricamento di driver o file di sistema non firmati nella memoria di sistema. Come illustrato nel diagramma seguente, HVCI viene eseguito in un ambiente di esecuzione isolato e verifica l'integrità del codice kernel in base ai criteri di firma del kernel.

Sia VBS che HVCI sono abilitati nei seguenti dispositivi Surface:

- Surface Laptop 4
- Surface Pro 7+
- Surface Book 3,
- Surface Laptop Vai,
- Surface Pro X

## <a name="secure-boot-and-boot-guard"></a>Protezione di avvio e boot guard

Root of Trust dei dispositivi Surface controlla le firme e le misurazioni per garantire che ogni fase sia sicura e autentica prima di consentire alla fase successiva di avvio di procedere. Abilitato da UEFI e TPM 2.0, l'avvio protetto garantisce che solo il codice firmato, misurato e implementato correttamente possa essere eseguito in un dispositivo Surface.

Come illustrato nella figura 2, l'integrità del firmware viene controllata in ogni fase, dalla pressione del pulsante di alimentazione all'esecuzione del sistema operativo.

 > [!div class="mx-imgBorder"]
 > ![Figura 1. Avvio sicuro per i dispositivi Surface. ](images/secboot.png)
  *Figura 1. Avvio protetto per i dispositivi Surface*

| Passaggio  | Fase di avvio protetto                                                                                                                                                                                                                                      |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Viene creata un'istanza della sicurezza ogni volta che si preme il pulsante di alimentazione da una radice di attendibilità fornita dal TPM. Quando un dispositivo viene acceso per la prima volta, il sistema esegue una serie di controlli di sicurezza per assicurarsi che il firmware del dispositivo non sia stato manomesso o danneggiato. |
| **2** | Quando è acceso, il SoC usa una chiave del fornitore di chipset per convalidare e avviare il caricamento del microcodice utilizzando il modulo ACM (Authenticated Code Module) (nei dispositivi basati su Intel).                                                                              |
| **3** | L'ACM misura il codice UEFI prima del caricamento e lo confronta con la misura nota nel Registro di configurazione della piattaforma del TPM [PCR] per garantire che il codice UEFI non sia stato alterato.                                                                |
| **4** | Prima di consentire l'esecuzione di UEFI, Boot Guard controlla che l'UEFI sia firmato con una chiave OEM di Surface. Il modulo UEFI inizialmente controllato è la sicurezza SEC e le sezioni PEI Pre-EFI mostrate nel diagramma.                                                |
| **5** | La sezione PEI controlla la presenza di una firma Surface nell'ambiente di esecuzione del driver, il modulo DXE, durante il caricamento. Il modulo DXE include la fase di selezione del dispositivo di avvio.                                                                          |
| **6** | Dopo aver selezionato il dispositivo di avvio, UEFI legge il dispositivo di avvio e controlla la firma del caricatore di avvio del sistema operativo prima di consentirlo di eseguire.                                                                                                             |
| **7** | Il sistema operativo controlla quindi le firme nel componente principale quando apre il sistema operativo.

### <a name="malware-protection"></a>Protezione antimalware

Per proteggere il dispositivo da attacchi di software dannoso, Surface consente l'avvio sicuro per garantire che sia avviata una versione autentica di Windows 10 e che il firmware sia originale come quando ha lasciato la fabbrica.

SoC nei dispositivi Surface ha un processore di sicurezza separato da ogni altro core. Quando si avvia il dispositivo Surface per la prima volta, viene avviato solo il processore di sicurezza prima di poter caricare qualsiasi altra operazione. L'avvio protetto viene utilizzato per verificare che i componenti del processo di avvio, inclusi i driver e il sistema operativo, siano convalidati rispetto a un database di firme valide e note. Questo aiuta a prevenire gli attacchi da un sistema clonato o modificato che esegue codice dannoso nascosto in quella che sembra essere un'esperienza utente normale. Per altre informazioni, vedere [Panoramica di avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot).

Dopo aver verificato che il sistema operativo proviene da Microsoft e che il dispositivo Surface completa correttamente il processo di avvio, il dispositivo esamina il codice eseguibile. L'approccio alla protezione del sistema operativo prevede l'identificazione della firma del codice di tutti gli eseguibili, consentendo di caricare nel runtime solo quelli che superano le restrizioni. Questo metodo di firma del codice consente al sistema operativo di verificare l'autore e confermare che il codice non è stato modificato prima di essere eseguito sul dispositivo.

## <a name="drtm-protection-in-amd-devices"></a>Protezione DRTM nei dispositivi AMD

I dispositivi Surface contenenti processori AMD implementano l'avvio protetto in modo equivalente. Surface Laptop 4 con il processore AMD Ryzen Microsoft Surface Edition protegge il firmware dall'accensione iniziale usando la tecnologia DRTM (Dynamic Root of Trust Measurements). DRTM controlla tutte le CPU, forzando l'esecuzione lungo un percorso misurato e ristabilire l'attendibilità in varie fasi per verificare l'integrità del firmware/software di sistema. La transizione in questo stato attendibile in anticipo offre una maggiore protezione da potenziali attacchi nelle fasi di avvio.

DRTM protegge le misurazioni assicurando che siano crittografate tramite TSME (Total System Memory Encryption). Una volta impostato TSME, se non può essere cancellato se non tramite una reimpostazione del sistema. Una nuova chiave di crittografia per ogni reimpostazione garantisce la crittografia a uso singolo per la sicurezza.

Le chiamate di runtime alla modalità di gestione del sistema vengono eseguite al livello più alto, il che può essere rischioso se il codice SMM presenta problemi. Surface Laptop 4 con AMD Ryzen protegge il sistema intercettando gli interrupt di gestione del sistema (SMI) e invia l'esecuzione del codice SMM a un livello inferiore (utente) per proteggere il sistema dall'accesso non valido al codice e ai dati. La protezione SMM utilizza protezioni hardware per limitare il codice, i dati e le risorse di sistema a cui è possibile accedere, impedendo ulteriormente la protezione da incidenti accidentali o dannosi.

Surface Laptop 4 con AMD Ryzen supporta linee guida sulla resilienza del firmware della piattaforma [NIST 800-193,](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-193.pdf)oltre al solido supporto per gli aggiornamenti del firmware. Il meccanismo di aggiornamento resiliente per il firmware di avvio utilizza un meccanismo di ripristino A-B che fornisce il ripristino automatico a una copia di backup del firmware nel caso in cui la sequenza di avvio rilevi una copia danneggiata del firmware durante l'avvio.

Per ulteriori informazioni su DRTM e SMM, vedere Come Windows Defender System Guard aiuta a proteggere Windows 10 [- Windows sicurezza | Documenti Microsoft](/windows/security/threat-protection/windows-defender-system-guard/how-hardware-based-root-of-trust-helps-protect-windows)

## <a name="remote-device-management-control"></a>Controllo di gestione remota dei dispositivi

Gli amministratori IT possono gestire in remoto i dispositivi Surface senza dover toccare fisicamente ogni dispositivo. Microsoft Endpoint Manager con Intune e Windows Autopilot consente la gestione remota completa dei dispositivi Surface dal cloud di Azure, offrendo dispositivi completamente configurati agli utenti all'avvio. Le funzionalità di cancellazione e ritiro consentono all'IT di riutilizzare facilmente un dispositivo per un nuovo utente remoto e cancellare un dispositivo rubato. Ciò consente funzionalità di risposta rapida e sicura in caso di perdita o furto di un dispositivo Surface, consentendoti di rimuovere in remoto tutti i dati aziendali e riconfigurare Surface come dispositivo completamente nuovo.

| Funzionalità                                        | Descrizione                                                                                                                                                                                                                                                                                                                                                                                                        | Scopri di più                                                                                                                                                                                                                                                              |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| DCFI (Device Firmware Configuration Interface) | Offre la gestione remota del firmware su scala cloud con provisioning di dispositivi senza tocco. UeFI di Microsoft consente un'implementazione DCFI più efficace, consentendo alle organizzazioni di disabilitare gli elementi hardware e bloccare in remoto UEFI con Intune. ¹                                                                                                                                                                          | [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)<br> <br>[Gestire le impostazioni UEFI di Surface](manage-surface-uefi-settings.md)                                          |
| SEMM (modalità di Enterprise Surface)      | Consente l'interazione aziendale centralizzata delle impostazioni del firmware UEFI in ambienti locali, ibridi e cloud.¹                                                                                                                                                                                                                                                                                           | [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)                                                                                                                                                       |
| Windows Update per le aziende                    | Consente agli amministratori IT di mantenere sempre aggiornati i dispositivi Windows 10 dell'organizzazione con le difese di sicurezza, le funzionalità di Windows e il firmware di Surface più recenti connettendo direttamente questi sistemi al servizio di aggiornamento Windows. Puoi usare Criteri di gruppo o soluzioni MDM come Microsoft Intune per configurare le impostazioni di Windows Update for Business che controllano come e quando vengono aggiornati i dispositivi Surface. | [Windows Update per le aziende](/windows/deployment/update/waas-manage-updates-wufb)<br> <br>[Gestire e installare gli aggiornamenti di driver e firmware per Surface](manage-surface-driver-and-firmware-updates.md) |

## <a name="references"></a>Riferimenti

1. Surface Go e Surface Go 2 usano un UEFI di terze parti e non supportano DFCI. DFCI è attualmente disponibile per Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X. 

## <a name="learn-more"></a>Scopri di più

- [I nuovi PC Surface abilitano la sicurezza basata su virtualizzazione (VBS) per impostazione predefinita per consentire ai clienti di fare di più in modo sicuro](https://www.microsoft.com/security/blog/2021/01/11/new-surface-pcs-enable-virtualization-based-security-vbs-by-default-to-empower-customers-to-do-more-securely/)
- [Lo studio evidenzia il ruolo critico della protezione del firmware di Surface](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/study-highlights-critical-role-of-surface-firmware-protection/ba-p/2245244)
- [Miglioramento della sicurezza e della conformità con Microsoft Surface e Microsoft 365](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/enhancing-security-and-compliance-with-microsoft-surface-and/ba-p/2283062)
- [Gestire le impostazioni UEFI di Surface](manage-surface-uefi-settings.md)
- [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)
- [Project Mu](https://microsoft.github.io/mu/)

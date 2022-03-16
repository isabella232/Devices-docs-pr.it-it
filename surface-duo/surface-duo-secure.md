---
title: Panoramica della sicurezza di Surface Duo
description: Questo articolo illustra come Surface Duo garantisce una sicurezza di livello aziendale su un dispositivo mobile tramite il sistema operativo Android e UEFI progettato da Microsoft.
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 8/12/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 677839038d8990aa7cb88800dabd51ace565e472
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449159"
---
# <a name="surface-duo-security-overview"></a>Panoramica della sicurezza di Surface Duo

Surface Duo ha una protezione integrata a tutti i livelli con hardware, firmware e software completamente integrati per proteggere dispositivi, identità e dati. Come dispositivo Android 10, Surface Duo usa le funzionalità di sicurezza android a livello del sistema operativo e del livello di servizi Google. Il sistema operativo Android sfrutta i controlli di sicurezza del sistema operativo tradizionali per proteggere i dati utente e le risorse di sistema, protegge l'integrità del dispositivo dal malware e fornisce l'isolamento delle applicazioni. Inoltre, Google fornisce vari servizi a più livelli sul sistema operativo che, se combinati con la sicurezza del sistema operativo Android, aiutano a proteggere continuamente l'utente Android.

- **UEFI personalizzato.** Unico per Surface Duo, tra i dispositivi Android, è l'interfaccia UEFI (Unified Extensible Firmware Interface) personalizzata di Microsoft, che consente il controllo completo dei componenti del firmware. Microsoft fornisce una sicurezza di livello Enterprise a Surface Duo scrivendo o rivedendo ogni riga di codice firmware interno, consentendo a Microsoft di rispondere direttamente e in modo agile a potenziali minacce del firmware e ridurre i rischi di sicurezza della catena di approvvigionamento.
- **Avvio verificato.** A partire dal livello hardware al momento dell'accesso, l'avvio verificato cerca di garantire che il codice eseguito proviene solo da un'origine attendibile. Stabilisce una catena completa di trust, dalla radice di trust protetta dall'hardware al bootloader, alla partizione di avvio e ad altre partizioni verificate. Quando Surface Duo si avvia, ogni fase verifica l'integrità e l'autenticità della fase successiva prima di consegnare l'esecuzione.
- **Separazione delle app.** La sandbox delle applicazioni isola e protegge le app Android, impedendo alle app dannose di accedere a informazioni private. La crittografia e la gestione delle chiavi obbligatorie e sempre disponibili consentono di proteggere i dati in transito e in pausa, anche se i dispositivi cadono nelle mani sbagliate. La crittografia è protetta con le chiavi keystore, che archiviano le chiavi di crittografia in un contenitore, rendendo più difficile l'estrazione da un dispositivo.
- **Google Play Protect.** A livello software, Surface Duo usa il rilevamento delle minacce di Google Play Protect, che analizza tutte le applicazioni, incluse le app pubbliche di Google Play, le app di sistema aggiornate da Microsoft e gli operatori e le app sideloaded.
- **Microsoft Defender ATP.** Il software di protezione antivirus e malware di livello enterprise per Windows 10 è ora disponibile per i dispositivi Android gestiti da Intune. Per altre informazioni, vedi [Microsoft defender ATP per Android](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-android).

## <a name="mobile-device-management-security"></a>Sicurezza della gestione dei dispositivi mobili

Surface Duo è protetto in un ambiente aziendale utilizzando una soluzione EMM (Mobility Management) di Enterprise che fornisce un insieme coerente di strumenti di protezione, tecnologie e procedure consigliate che è possibile personalizzare per soddisfare i requisiti di conformità e organizzazione. Un'ampia gamma di API di gestione offre ai reparti IT gli strumenti per evitare perdite di dati e applicare la conformità in diversi scenari. Il supporto multi-profilo e le opzioni di gestione dei dispositivi consentono la separazione dei dati personali e di lavoro, contribuendo a proteggere i dati aziendali.

La sicurezza MDM si basa su un set in espansione di tecnologie di configurazione per consentire agli utenti di essere produttivi in viaggio proteggendo allo stesso tempo la proprietà intellettuale aziendale critica. Sono inclusi i criteri di protezione delle app, i criteri di restrizione dei dispositivi e le tecnologie correlate progettate per consentire di raggiungere obiettivi specifici a seconda dell'ambiente, sia che l'azienda sia costituita dalla consegna di ordini di acquisto di ristoranti, dalla gestione dei servizi IT per gli uffici o dalla gestione di informazioni sensibili sulla sicurezza nazionale.

Ad esempio, potresti voler rafforzare l'autenticazione del dispositivo richiedendo agli utenti di immettere un pin alfanumerico a 6 cifre insieme all'autenticazione a 2 fattori. Potresti voler limitare i dispositivi a cui gli utenti possono iscriversi per mantenere la conformità ai limiti di licenza o evitare di concedere l'accesso ai telefoni "jailbroken" o ad altri tipi di dispositivi non supportati. Intune e altri emm consentono alle organizzazioni di gestire i dispositivi in base alle proprie esigenze.

## <a name="app-protection-policies"></a>Criteri di protezione delle app

I criteri di protezione delle app sono regole che assicurano che i dati di un'organizzazione rimangano sicuri o contenuti in un'app gestita. Un criterio può essere una regola che viene applicata quando l'utente tenta di accedere o spostare dati "aziendali" o un set di azioni non consentite o monitorate quando l'utente si trova all'interno dell'app. Un'app gestita è un'app a cui sono applicati criteri di protezione delle app e che può essere gestita da Intune.

I criteri di protezione delle app consentono di gestire e proteggere i dati dell'organizzazione all'interno di un'applicazione. Molte app di produttività, ad esempio Microsoft Office, possono essere gestite da Intune MAM. Vedi l'elenco ufficiale delle [Microsoft Intune protette disponibili](/mem/intune/apps/apps-supported-intune-apps) per l'uso pubblico.

## <a name="security-considerations-for-managing-surface-duo"></a>Considerazioni sulla sicurezza per la gestione di Surface Duo

Il numero crescente di impostazioni dei criteri disponibili nelle soluzioni di gestione dei dispositivi mobili consente alle organizzazioni di modificare i livelli di protezione in base alle proprie esigenze specifiche. Per aiutare le organizzazioni a definire la priorità delle impostazioni di sicurezza per Surface Duo (o qualsiasi altro dispositivo Android), Intune ha introdotto il framework di configurazione della sicurezza di [Android Enterprise organizzato in](/mem/intune/enrollment/android-configuration-framework) diversi scenari di configurazione distinti, fornendo indicazioni per il profilo di lavoro e gli scenari completamente gestiti.

| Livello Sicurezza                                                                                                       | Mirato a                                                                                                                                                                      | Riepilogo                                                                                                                                                                                     | Impostazioni info                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sicurezza di base del profilo di lavoro - Livello 1                                                                                | Dispositivi personali con accesso ai dati dell'istituto di istruzione o dell'istituto di istruzione.                                                                                                                             | Introduce i requisiti delle password, separa i dati personali e di lavoro e convalida l'attestazione del dispositivo Android.                                                                               | [Impostazioni di livello 1 del profilo di lavoro](/mem/intune/enrollment/android-work-profile-security-settings) |
| Sicurezza elevata del profilo di lavoro - Livello 3<br>A causa delle convenzioni del framework, questo è il livello successivo al di sopra del livello 1.<br>  | Dispositivi utilizzati da utenti o gruppi a rischio univoco. Ad esempio, gli utenti che gestendo dati estremamente sensibili in cui la divulgazione non autorizzata causa una notevole perdita di materiale. | Introduce la difesa dalle minacce mobili o Microsoft Defender ATP, imposta la versione minima di Android su 8.0, emana criteri password più forti e limita ulteriormente il lavoro e la separazione personale. | [Impostazioni di livello 3 del profilo di lavoro](/mem/intune/enrollment/android-work-profile-security-settings#work-profile-high-security)                                                                                         |
| Sicurezza di base completamente gestita - Livello 1                                                                                | Configurazione di sicurezza minima per un dispositivo aziendale, applicabile alla maggior parte degli utenti mobili che accedono ai dati aziendali o dell'istituto di istruzione.                                                          | Introduce i requisiti per le password, imposta la versione minima di Android su 8.0 e introduce alcune restrizioni per i dispositivi.                                                                          | [Impostazioni di livello 1 completamente gestite](/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-basic-security)                                                                                     |
| Sicurezza avanzata completamente gestita Livello 2                                                                              | Dispositivi in cui gli utenti accedono a informazioni riservate o riservate.                                                                                                                | Emana criteri password più potenti e disabilita le funzionalità utente/account.                                                                                                                   | [Settng di livello 2 completamente gestiti](/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-enhanced-security)                                                                                   |
| Livello di sicurezza elevato completamente gestito 3                                                                                  | Dispositivi utilizzati da utenti o gruppi a rischio univoco. Ad esempio, gli utenti che gestendo dati estremamente sensibili in cui la divulgazione non autorizzata causa una notevole perdita di materiale. | Aumenta la versione minima di Android a 10.0, introduce la difesa dalle minacce mobili o Microsoft Defender ATP e applica ulteriori restrizioni per i dispositivi.                                     | [Impostazioni di livello 3 completamente gestite](/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-high-security)                                                                                      |

 Come per qualsiasi framework, potrebbe essere necessario modificare le impostazioni all'interno di un livello corrispondente in base alle esigenze dell'organizzazione, in quanto la sicurezza deve valutare l'ambiente delle minacce, la propensione al rischio e l'impatto sull'usabilità.

## <a name="learn-more"></a>Scopri di più

- [Framework di configurazione della sicurezza di Android Enterprise](/mem/intune/enrollment/android-configuration-framework)
- [Panoramica dei criteri di protezione delle app](/mem/intune/apps/app-protection-policy)
- [Impostazioni dei criteri di protezione delle app android in Microsoft Intune](/mem/intune/apps/app-protection-policy-settings-android)
- [Impostare restrizioni di registrazione](/mem/intune/enrollment/enrollment-restrictions-set)
- [White paper sulla sicurezza di Android Enterprise](https://static.googleusercontent.com/media/www.android.com/en//static/2016/pdfs/enterprise/Android_Enterprise_Security_White_Paper_2019.pdf)

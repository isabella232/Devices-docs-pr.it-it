---
title: Panoramica della sicurezza di Surface Duo
description: Questo articolo illustra come Surface Duo offre sicurezza di livello aziendale su un dispositivo mobile tramite il sistema operativo Android e l'UEFI di Microsoft Engineered.
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
ms.openlocfilehash: 91eb893dbdc6dae93cf402a602b64a83309388e8
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326192"
---
# Panoramica della sicurezza di Surface Duo

Surface Duo include la protezione integrata in tutti i livelli con hardware, firmware e software integrati in modo approfondito per proteggere i dispositivi, le identità e i dati. Come dispositivo Android 10, Surface Duo usa le caratteristiche di sicurezza di Android a livello di sistema operativo e al livello dei servizi di Google. Il sistema operativo Android sfrutta i tradizionali controlli di sicurezza del sistema operativo per proteggere i dati degli utenti e le risorse di sistema, protegge l'integrità dei dispositivi da malware e fornisce l'isolamento delle applicazioni. Google offre inoltre una serie di servizi sovrapposti al sistema operativo che, se combinati con la sicurezza del sistema operativo Android, aiutano a proteggere continuamente l'utente Android.

- **UEFI ingegnerizzato personalizzato.** Unique to surface Duo, tra i dispositivi Android, è l'interfaccia UEFI (Unified Extensible Firmware Interface) di Microsoft, che consente il controllo completo sui componenti del firmware. Microsoft offre sicurezza di livello aziendale per Surface duo scrivendo o rivedendo ogni riga di codice del firmware in House, consentendo a Microsoft di rispondere direttamente e con agilità, alle potenziali minacce del firmware e a mitigare i rischi per la sicurezza della catena di approvvigionamento.
- **Avvio verificato.** A partire dal livello hardware all'accesso, l'avvio verificato si sforza di garantire che il codice eseguito venga fornito solo da un'origine attendibile. Stabilisce una catena di attendibilità completa, dalla radice di attendibilità protetta dall'hardware al bootloader, alla partizione di avvio e ad altre partizioni verificate. Quando Surface Duo viene avviato, ogni fase verifica l'integrità e l'autenticità della fase successiva prima di consegnare l'esecuzione.
- **Separazione delle app.** L'applicazione sandboxing isola e protegge le app Android, impedendo alle app malevole di accedere a informazioni private. La crittografia e la gestione delle chiavi obbligatorie, sempre in uso aiutano a proteggere i dati in transito e a riposo, anche se i dispositivi cadono nelle mani sbagliate. La crittografia è protetta con i tasti Keys, che memorizzano le chiavi crittografiche in un contenitore, rendendo più difficile l'estrazione da un dispositivo.
- **Protezione di Google Play.** Al livello software Surface Duo usa Google Play Protect Threat detection, che analizza tutte le applicazioni, incluse le app pubbliche di Google Play, le app di sistema aggiornate da Microsoft e i vettori e le app sideload.
- **Microsoft Defender ATP.** Il software antivirus e di protezione antimalware per la finestra 10 di livello aziendale è ora disponibile per i dispositivi Android gestiti da Intune. Per altre informazioni, vedere [Microsoft Defender ATP per Android](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-android). 


## Sicurezza per la gestione di dispositivi mobili

Surface Duo è protetto in un ambiente aziendale tramite una soluzione EMM (Enterprise Mobility Management) che offre un set coerente di strumenti di protezione, tecnologie e procedure consigliate per soddisfare i requisiti di organizzazione e conformità. Una vasta gamma di API di gestione offre agli uffici IT gli strumenti per evitare perdite di dati e applicare la conformità in diversi scenari. Le opzioni di supporto multiprofilo e di gestione dei dispositivi consentono la separazione dei dati personali e del lavoro, contribuendo a proteggere i dati aziendali.

La sicurezza di MDM si basa su un set di tecnologie di configurazione in espansione per consentire agli utenti di essere produttivi ovunque, proteggendo anche le proprietà intellettuali aziendali critiche. Questo include i criteri di protezione delle app, i criteri di restrizione dei dispositivi e le tecnologie correlate progettate per consentire di raggiungere obiettivi specifici a seconda dell'ambiente, indipendentemente dal fatto che l'azienda contenga gli ordini di asporto del ristorante, gestendo i servizi IT per gli uffici odontoiatrici o gestendo le informazioni riservate sulla sicurezza nazionale. 

Ad esempio, potresti voler rafforzare l'autenticazione dei dispositivi richiedendo agli utenti di immettere un PIN alfanumerico a 6 cifre insieme all'autenticazione a due fattori.  Potresti voler limitare i dispositivi che gli utenti possono eseguire la registrazione per assicurarti di rimanere conforme ai limiti di licenza o evitare di concedere l'accesso ai telefoni "jailbroken" o ad altri tipi di dispositivo non supportati.
Intune e altri EMMs consentono alle organizzazioni di gestire i dispositivi in base alle proprie esigenze.

## Criteri di protezione delle app

I criteri di protezione delle app sono regole che assicurano che i dati di un'organizzazione rimangano sicuri o contenuti in un'app gestita. Un criterio può essere una regola imposta quando l'utente tenta di accedere o di trasferire dati "aziendali" oppure un set di azioni che sono vietate o monitorate quando l'utente si trova all'interno dell'app. Un'app gestita è un'app a cui sono applicati i criteri di protezione delle app e può essere gestita da Intune.

I criteri di protezione delle app consentono di gestire e proteggere i dati dell'organizzazione all'interno di un'applicazione. Molte app per la produttività, come le app di Microsoft Office, possono essere gestite da Intune MAM. Vedere l'elenco ufficiale delle [app protette di Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/apps-supported-intune-apps) disponibili per l'uso pubblico.

## Considerazioni sulla sicurezza per la gestione di Surface Duo

Il numero crescente di impostazioni dei criteri disponibili nelle soluzioni per la gestione di dispositivi mobili consente alle organizzazioni di regolare i livelli di protezione in base alle specifiche esigenze. Per aiutare le organizzazioni a dare priorità alle impostazioni di sicurezza per Surface Duo (o qualsiasi altro dispositivo Android), Intune ha introdotto il [Framework di configurazione della sicurezza di Android Enterprise](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework) organizzato in diversi scenari di configurazione, fornendo indicazioni per il profilo del lavoro e gli scenari completamente gestiti.
 

| Livello Sicurezza                                                                                                       | Mirato a                                                                                                                                                                      | Riepilogo                                                                                                                                                                                     | Informazioni sulle impostazioni                                                                                                                                                                                                                                     |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Sicurezza di base del profilo di lavoro-livello 1                                                                                | Dispositivi personali con accesso a dati lavorativi o scolastici.                                                                                                                             | Introduce i requisiti per le password, separa i dati personali e il lavoro e convalida l'attestazione del dispositivo Android.                                                                               | [Impostazioni di livello 1 del profilo di lavoro](https://microsoft.sharepoint.com/teams/EpsilonAdminGuide/Shared%20Documents/General/•%09https:/docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-basic-security) |
| Profilo di lavoro High Security-livello 3<br>(A causa delle convenzioni del Framework, questo è il livello successivo sopra il livello 1).<br> ** | Dispositivi usati da utenti o gruppi che sono ad alto rischio in modo univoco. Ad esempio, gli utenti che gestiscono dati altamente riservati in cui la divulgazione non autorizzata causa notevoli perdite di materiale. | Introduce la difesa delle minacce per dispositivi mobili o l'ATP Microsoft Defender, imposta la versione minima di Android in 8,0, Crea criteri di password più forti e limita ulteriormente il lavoro e la separazione personale. | [Impostazioni di livello del profilo di lavoro 3](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-security-settings#work-profile-high-security)                                                                                         |
| Sicurezza di base completamente gestita-livello 1                                                                                | Configurazione minima di sicurezza per un dispositivo aziendale, applicabile alla maggior parte degli utenti di dispositivi mobili che accedono a dati aziendali o scolastici.                                                          | Introduce i requisiti per le password, imposta la versione minima di Android in 8,0 e apporta determinate restrizioni per i dispositivi.                                                                          | [Impostazioni di livello 1 completamente gestite](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-basic-security)                                                                                     |
| Livello di sicurezza avanzato completamente gestito 2                                                                              | Dispositivi in cui gli utenti accedono a informazioni riservate o confidenziali.                                                                                                                | Consente di usare criteri di password più forti e Disabilita le funzionalità utente/account.                                                                                                                   | [Settngs di livello 2 completamente gestito](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-enhanced-security)                                                                                   |
| Livello di sicurezza alto completamente gestito 3                                                                                  | Dispositivi usati da utenti o gruppi che sono ad alto rischio in modo univoco. Ad esempio, gli utenti che gestiscono dati altamente riservati in cui la divulgazione non autorizzata causa notevoli perdite di materiale. | Aumenta la versione minima di Android in 10,0, introduce la difesa delle minacce per dispositivi mobili o l'ATP Microsoft Defender e applica restrizioni aggiuntive per i dispositivi.                                     | [Impostazioni di livello 3 completamente gestite](https://docs.microsoft.com/mem/intune/enrollment/android-fully-managed-security-settings#fully-managed-high-security)                                                                                      |
 
Come per qualsiasi Framework, è necessario che le impostazioni di un livello corrispondente vengano modificate in base alle esigenze dell'organizzazione perché la sicurezza deve valutare l'ambiente delle minacce, l'appetito e l'impatto sull'usabilità.
 
 
**Altre informazioni**


- [Framework di configurazione della sicurezza di Android Enterprise](https://docs.microsoft.com/mem/intune/enrollment/android-configuration-framework)
- [Panoramica dei criteri di protezione delle app](https://docs.microsoft.com/mem/intune/apps/app-protection-policy)
- [Impostazioni dei criteri di protezione delle app Android in Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/app-protection-policy-settings-android)
- [Impostare le restrizioni di registrazione](https://docs.microsoft.com/mem/intune/enrollment/enrollment-restrictions-set)
- [Carta bianca di sicurezza di Android Enterprise](https://static.googleusercontent.com/media/www.android.com/en//static/2016/pdfs/enterprise/Android_Enterprise_Security_White_Paper_2019.pdf)
 
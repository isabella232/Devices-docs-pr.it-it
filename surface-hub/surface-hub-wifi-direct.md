---
title: Risoluzione dei problemi relativi alla sicurezza di Wi-Fi Direct con Surface Hub
description: Indicazioni sui rischi di sicurezza diretti Wi-Fi.
keywords: cronologia delle modifiche
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/27/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d877d9b6a4e330a74a9d79cf1150487d89c0da23
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832768"
---
# Risoluzione dei problemi di protezione di Wi-Fi Direct con Surface Hub

Microsoft Surface Hub è un dispositivo per la produttività completo, che consente ai team di svolgere al meglio attività quali brainstorming, collaborazione e condivisione di idee. Surface Hub si basa su Miracast per la proiezione wireless tramite Wi-Fi Direct.

In questo articolo vengono illustrate le vulnerabilità della sicurezza diretta Wi-Fi, la modalità di accesso ai rischi da parte di Surface Hub e il modo in cui gli amministratori possono configurare Surface hub per il massimo livello di sicurezza. Queste informazioni aiuteranno i clienti che hanno requisiti di sicurezza elevati a proteggere le reti e i dati connessi all'hub di Surface in transito.

I destinatari previsti per questo articolo sono IT e gli amministratori di rete che vogliono distribuire Surface Hub nell'ambiente aziendale con impostazioni di sicurezza ottimali.

##  <a name="overview"></a>Panoramica

La sicurezza per Surface Hub dipende ampiamente da Wi-Fi Direct/Miracast e dagli standard associati di 802,11, Wi-Fi Protected Access (WPA2) e Wireless Protected Setup (WPS). Dato che il dispositivo supporta solo WPS (in contrapposizione alla chiave pre-condivisa WPA2 [PSK] o WPA2 Enterprise), i problemi spesso associati alla crittografia di 802,11 sono semplificati.

Surface hub funziona alla pari con il campo dei ricevitori Miracast. Quindi, è vulnerabile a un insieme simile di exploit come tutti i dispositivi di rete wireless basati su WPS. Ma l'implementazione di Surface Hub di WPS include ulteriori precauzioni. Inoltre, la sua architettura interna aiuta a impedire a un utente malintenzionato che ha compromesso il livello Wi-Fi Direct/Miracast layer di spostarsi oltre l'interfaccia di rete su altre superfici di attacco e reti aziendali connesse.

##  <a name="wi-fi-direct-background"></a>Panoramica di Wi-Fi Direct

Miracast fa parte dello standard di visualizzazione Wi-Fi, che è supportato dal protocollo Wi-Fi Direct. Questi standard sono supportati nei dispositivi mobili più recenti per la condivisione dello schermo e la collaborazione.

Wi-Fi Direct o Wi-Fi "peer to peer" (P2P) è uno standard dell'Alleanza Wi-Fi per le reti "ad-hoc". I dispositivi supportati possono comunicare direttamente e creare gruppi di reti senza un punto di accesso Wi-Fi convenzionale o una connessione Internet.

La sicurezza per Wi-Fi Direct è fornita da WPA2 in base allo standard WPS. Il meccanismo di autenticazione per i dispositivi può essere un PIN numerico (WPS-PIN), un pulsante di push fisico o virtuale (WPS-PBC) o un messaggio fuori banda, come Near Field Communication (WPS-OOO). Surface Hub supporta sia il metodo PIN che il metodo Push Button, che è l'impostazione predefinita.

In Wi-Fi Direct i gruppi vengono creati come uno dei tipi seguenti:
- *Persistente*, in cui può essere eseguita la riconnessione automatica tramite il materiale della chiave archiviata
- *Temporaneo*, in cui i dispositivi non possono eseguire di nuovo l'autenticazione senza l'azione dell'utente

I gruppi Wi-Fi Direct determinano un *proprietario del gruppo* (go) tramite un protocollo di negoziazione, che simula la funzionalità "stazione" o "punto di accesso" per il gruppo Wi-Fi diretto stabilito. La connessione Wi-Fi Direct GO fornisce l'autenticazione (tramite un "registrar interno") e facilita le connessioni di rete upstream. Per Surface Hub, questa negoziazione non si verifica. La rete funziona solo in modalità "autonoma" e Surface Hub è sempre il proprietario del gruppo. Infine, Surface hub stesso non si unisce ad altre reti Wi-Fi Direct come client.

##  <a name="how-surface-hub-addresses-wi-fi-direct-vulnerabilities"></a>Come l'hub di Surface risolve le vulnerabilità dirette Wi-Fi

**Vulnerabilità e attacchi nel processo di invito, trasmissione e rilevamento diretto Wi-Fi:** Gli attacchi Wi-Fi Direct/Miracast possono raggiungere punti deboli nella creazione di gruppi, individuazione peer, trasmissione di dispositivi o processi di invito.

|Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| Il processo di individuazione può rimanere attivo per un periodo di tempo prolungato, in modo che gli inviti e le connessioni vengano stabiliti senza l'approvazione del proprietario del dispositivo. | Surface hub funziona solo come proprietario del gruppo, che non esegue l'individuazione del client o i processi di negoziazione. È possibile disabilitare completamente la proiezione wireless per disattivare la trasmissione. |
| Invito ed individuazione tramite PBC consente a un utente malintenzionato non autenticato di eseguire tentativi di connessione ripetuti o di accettare automaticamente le connessioni non autenticate. | Richiedendo la sicurezza dei PIN WPS, gli amministratori possono ridurre il potenziale per tali connessioni non autorizzate o "bombe a invito", in cui gli inviti vengono ripetutamente inviati fino a quando un utente non accetta erroneamente uno. |

**Connessione Wi-Fi Protected Setup (WPS) Push Button Connect (PBC) vs pin:** Le debolezze pubbliche sono state dimostrate nella progettazione e implementazione di metodi WPS-PIN. WPS-PBC presenta altre vulnerabilità che potrebbero consentire attacchi attivi a un protocollo progettato per l'uso di una tantum.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| PBC WPS è vulnerabile agli attacchi attivi. La specifica WPS afferma che "il metodo PBC contiene zero bit di entropia e protegge solo dagli attacchi passivi di intercettazione. Il metodo PBC offre protezione contro gli attacchi di intercettazione e utilizza strategie per evitare che un dispositivo partecipi a una rete che non sia stata selezionata dal proprietario del dispositivo. L'assenza di autenticazione, tuttavia, indica che PBC non protegge da attacchi attivi. " I pirati informatici possono usare la funzionalità di jamming wireless selettiva o altre tecniche di negazione del servizio per attivare una connessione o un accesso diretto Wi-Fi non intenzionale. Inoltre, un aggressore attivo che ha semplicemente la vicinanza fisica può ripetutamente abbattere qualsiasi gruppo Direct Wi-Fi e tentare l'attacco fino a quando non riesce. | Abilitare la sicurezza del PIN WPS nella configurazione di Surface Hub. La specifica Wi-Fi WPS stabilisce: "il metodo PBC deve essere usato solo se non è disponibile un registrar abilitato per i PIN e l'utente WLAN è disposto ad accettare i rischi associati alla PBC." |
| Le implementazioni WPS-PIN possono essere soggette ad attacchi a forza bruta che mirano a una vulnerabilità nello standard WPS. La progettazione della verifica dei PIN divisi ha portato a più vulnerabilità di implementazione negli ultimi anni in una gamma di produttori di hardware Wi-Fi. In 2011 i ricercatori Stefan Viehböck e Craig Heffner hanno rilasciato informazioni su questa vulnerabilità e strumenti come "Reaver" come prova del concetto. |   L'implementazione Microsoft di WPS in Surface Hub cambia il PIN ogni 30 secondi. Per craccare il PIN, un utente malintenzionato deve completare l'intero exploit in meno di 30 secondi. Considerato lo stato attuale degli strumenti e della ricerca in questo settore, è improbabile che venga eseguito un attacco di PIN-cracking a forza bruta tramite WPS. |
| Il PIN WPS può essere incrinato da un attacco offline a causa della chiave iniziale debole (E-S1, E S2) entropia. In 2014, Dominique Bongard descrisse un attacco "polvere pixie", in cui la scarsa casualità iniziale per il generatore di numeri casuali pseudo (PRNG) nel dispositivo wireless consentiva un attacco di forza bruta offline. | L'implementazione Microsoft di WPS in Surface Hub non è soggetta a questo attacco di forza bruta PIN offline. Il PIN WPS è generato casualmente per ogni connessione. |

**Esposizione non voluta dei servizi di rete:** I demoni di rete progettati per i servizi Ethernet o WLAN possono essere esposti per errore a causa di una configurazione errata, ad esempio il binding a interfacce "All"/0.0.0.0. Altre possibili cause includono un firewall di dispositivo mal configurato o regole del firewall mancanti.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| Una configurazione errata associa un servizio di rete vulnerabile o non autenticato a “tutte” le interfacce, tra cui l’interfaccia Wi-Fi Direct. In questo modo puoi esporre i servizi che non devono essere accessibili ai client Direct Wi-Fi, che potrebbero essere autenticati debolmente o automaticamente. | In Surface Hub le regole del firewall predefinite consentono solo le porte di rete TCP e UDP necessarie e, per impostazione predefinita, negano tutte le connessioni in ingresso. Configurare l'autenticazione avanzata abilitando la modalità WPS-PIN.|

**Bridging Wi-Fi Direct e altre reti cablate o wireless:** Il bridging di rete tra reti WLAN o Ethernet è una violazione della specifica Wi-Fi Direct. Un Bridge o una configurazione errata può effettivamente abbassare o rimuovere i controlli di accesso wireless per la rete aziendale interna.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| I dispositivi Wi-Fi Direct potrebbero consentire l’accesso non autenticato o con un’autenticazione debole alle connessioni di rete con bridging. Ciò potrebbe consentire alle reti Wi-Fi Direct di indirizzare il traffico verso la rete LAN Ethernet o altre infrastrutture o le reti WLAN aziendali in violazione dei protocolli di sicurezza IT esistenti. | Surface Hub non può essere configurato per ponticellare le interfacce wireless o consentire il routing tra reti diverse. Le regole predefinite del firewall aggiungono difese avanzate a tali connessioni di instradamento o bridging. |

**Uso della modalità "Legacy" Wi-Fi Direct:** L'esposizione a reti o dispositivi non previsti può verificarsi quando si opera in modalità "Legacy". Se il PIN WPS non è abilitato, si possono verificare connessioni indesiderate o lo spoofing dei dispositivi.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| Grazie al supporto dei client di infrastruttura Wi-Fi Direct e 802.11, il sistema funziona con una modalità di supporto “legacy”. Questo potrebbe esporre la fase di configurazione della connessione a tempo indefinito, consentendo ai gruppi di essere Uniti o i dispositivi invitati a connettersi bene dopo la terminazione della fase di configurazione prevista. |    Surface Hub non supporta i client legacy Direct Wi-Fi. A Surface Hub possono solo essere effettuate connessioni Wi-Fi Direct anche quando è abilitata la modalità PIN WPS. |

**Wi-Fi Direct go Negotiation durante la configurazione della connessione:** Il proprietario del gruppo in Wi-Fi Direct è analogo al "punto di accesso" in una rete wireless 802,11 convenzionale. La negoziazione può essere manipolata da un utente malintenzionato.

|Vulnerabilità Direct Wi-Fi |   Attenuazione di Surface Hub |
| --- | --- |
| Se i gruppi sono stabiliti in modo dinamico o se il dispositivo Direct Wi-Fi può essere creato per partecipare a nuovi gruppi, la negoziazione del proprietario del gruppo può essere vinta da un dispositivo malintenzionato che specifica sempre il valore massimo del proprietario del gruppo "Intent" di 15. Ma la connessione non riesce se il dispositivo è configurato per essere sempre un proprietario del gruppo.  | Surface Hub sfrutta la funzione Wi-Fi Direct "modalità autonoma", che ignora la fase di negoziazione della procedura di configurazione della connessione. E Surface Hub è sempre il proprietario del gruppo. |

**Disautenticazione Wi-Fi indesiderata o malintenzionata:** La deautenticazione Wi-Fi è un attacco obsoleto in cui un utente malintenzionato locale può accelerare le perdite di informazioni nel processo di configurazione della connessione, attivare nuovi handshake a quattro vie, creare un obiettivo Wi-Fi Direct WPS-PBC per gli attacchi attivi o crea attacchi Denial of Service.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| I pacchetti di deautenticazione possono essere inviati da un aggressore non autenticato per fare in modo che la stazione venga autenticata di nuovo per annusare l'handshake risultante. Dall’handshake derivante, possono essere tentati attacchi crittografici o di forza bruta. La mitigazione per questi attacchi include i criteri di lunghezza e complessità per le chiavi già condivise, la configurazione del punto di accesso (se applicabile) per individuare i livelli illeciti di pacchetti di deautenticazione e l'uso di WPS per generare automaticamente chiavi forti. In modalità PBC l'utente interagisce con un pulsante fisico o virtuale per consentire l'associazione di dispositivi arbitrari. Questo processo deve avvenire solo durante la configurazione, in una breve finestra. Dopo che il pulsante viene "inserito" automaticamente, il dispositivo accetterà qualsiasi stazione associata tramite un valore PIN canonico (tutti gli zeri). La deautenticazione può forzare la ripetizione del processo di configurazione. |   Surface Hub USA WPS in modalità PIN o PBC. Nessuna configurazione PSK è consentita. Questo metodo consente di applicare la generazione di chiavi complesse. È consigliabile abilitare la sicurezza del PIN WPS per Surface Hub. |
| Oltre agli attacchi Denial of Service, i pacchetti di deautenticazione possono essere usati per attivare una riconnessione che riapre la finestra di opportunità per attacchi attivi contro WPS-PBC. |   Abilitare la sicurezza del PIN WPS nella configurazione di Surface Hub. |

**Divulgazione di informazioni wireless di base:** Le reti wireless, 802,11 o in altro modo, sono intrinsecamente a rischio di divulgazione delle informazioni. Anche se queste informazioni sono principalmente i metadati di connessione o di dispositivo, questo problema rimane un rischio noto per qualsiasi amministratore di rete di 802,11. Wi-Fi Direct con l’autenticazione del dispositivo tramite PIN WPS rivela effettivamente le stesse informazioni di una rete 802.11 PSK o Enterprise.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| Durante la trasmissione, la configurazione della connessione o anche il normale funzionamento delle connessioni già crittografate, le informazioni di base sui dispositivi e le dimensioni dei pacchetti vengono trasmesse in modalità wireless. A livello di base, un utente malintenzionato locale che si trova all'interno di un intervallo wireless può esaminare gli elementi di informazioni rilevanti di 802,11 per determinare i nomi dei dispositivi wireless, gli indirizzi MAC degli strumenti di comunicazione e, eventualmente, altri dettagli, ad esempio la versione dello stack wireless, le dimensioni dei pacchetti o le opzioni di Access Point o owner di gruppo configurati.  | La rete Wi-Fi Direct che Surface Hub USA non può essere ulteriormente protetta dalle perdite di metadati, come per le reti wireless 802,11 Enterprise o PSK. La sicurezza fisica e la rimozione di potenziali minacce dalla vicinanza wireless possono aiutare a ridurre le potenziali perdite di informazioni. |

**Wireless Evil Twin o attacchi di spoofing:**  Lo spoofing del nome wireless è un exploit semplice e noto che un utente malintenzionato locale può usare per attirare gli utenti ignari o sbagliati per la connessione.

| Vulnerabilità Direct Wi-Fi | Attenuazione di Surface Hub |
| --- | --- |
| Falsificando o clonando il nome wireless o "SSID" della rete di destinazione, un aggressore può ingannare l'utente nella connessione a una rete fittizia. Supportando i Miracast di accesso automatico non autenticati, un utente malintenzionato potrebbe acquisire i materiali di visualizzazione previsti o avviare attacchi di rete sul dispositivo di connessione. | Anche se non esistono protezioni specifiche per l'Unione di un hub di Surface contraffatto, questa vulnerabilità viene parzialmente attenuata in due modi. Prima di tutto, qualsiasi attacco deve essere condotto entro la portata della rete wireless. In secondo luogo, questo attacco è possibile solo durante la prima connessione. Le connessioni successive usano un gruppo diretto Wi-Fi persistente e Windows ricorderà e consentirà di assegnare priorità alla connessione precedente durante l'uso di Hub futuro. Nota: lo spoofing dell'indirizzo MAC, del canale Wi-Fi e di SSID simultaneamente non è stato considerato per questo report e può causare un comportamento incoerente Wi-Fi. In generale, questa debolezza è un problema fondamentale per qualsiasi rete wireless di 802,11 priva di protocolli di WPA2 aziendale, ad esempio EAP-TLS o EAP-PWD, che Wi-Fi Direct non supporta. |

##  <a name="surface-hub-hardening-guidelines"></a>Linee guida per la protezione avanzata di Surface Hub

Surface Hub è progettato per agevolare la collaborazione e consentire agli utenti di iniziare o partecipare alle riunioni in modo rapido ed efficiente. Le impostazioni predefinite Wi-Fi Direct per Surface Hub sono ottimizzate per questo scenario.

Per una maggiore sicurezza dell'interfaccia wireless, gli utenti di Surface Hub dovrebbero abilitare l'impostazione di sicurezza WPS-PIN. Questa impostazione disattiva la modalità WPS-PBC e offre l'autenticazione del client. Offre il livello di protezione più forte impedendo la connessione non autorizzata all'hub Surface.

Se si hanno ancora dubbi sull'autenticazione e l'autorizzazione per Surface Hub, è consigliabile connettere il dispositivo a una rete separata. È possibile usare la rete Wi-Fi (ad esempio una rete Wi-Fi "Guest") o un network Ethernet distinto, preferibilmente una rete fisica completamente diversa. Ma una VLAN può anche dare sicurezza aggiuntiva. Naturalmente, questo approccio può impedire la connessione a risorse o servizi di rete interna e può richiedere ulteriore configurazione di rete per riottenere l'accesso.

Argomenti consigliati:
- [Installare aggiornamenti di sistema regolari](manage-windows-updates-for-surface-hub.md) 
- Aggiornare le impostazioni di Miracast per disabilitare la modalità di presentazione automatica

##  <a name="learn-more"></a>Altre informazioni

- [Specifiche di Wi-Fi Direct](http://www.wi-fi.org/discover-wi-fi/wi-fi-direct)
- [Specifiche WPS (Wireless Protected Setup)](http://www.wi-fi.org/discover-wi-fi/wi-fi-protected-setup)




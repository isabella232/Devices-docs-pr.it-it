---
title: Programma di prima esecuzione - Surface Hub
description: Il termine \ 0034;prima esecuzione \ 0034; si riferisce alla serie di passaggi che dovrai eseguire alla prima accensione del dispositivo Surface Hub e ha lo stesso significato di \ 0034;configurazione guidata \ 0034; (OOBE, Out-Of-Box Experience). Questa sezione descrive dettagliatamente questo processo.
ms.assetid: 07C9E84C-1245-4511-B3B3-75939AD57C49
ms.reviewer: ''
manager: laurawi
keywords: prima esecuzione, Surface Hub, configurazione guidata, out-of-box experience, OOBE
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/27/2020
ms.localizationpriority: medium
ms.openlocfilehash: e070c28d13cd8466bff47022f4508fdb8aa06331
ms.sourcegitcommit: 19d2a78242777590bd09af3ac6552c07b032e0a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "11142915"
---
# Programma di prima esecuzione - Surface Hub


Il termine "prima esecuzione" si riferisce alla serie di passaggi che dovrai eseguire alla prima accensione del dispositivo Microsoft Surface Hub e ha lo stesso significato di "configurazione guidata" (OOBE, Out-Of-Box Experience). Questa sezione descrive dettagliatamente questo processo.

A questo punto, dovresti avere già eseguito tutti i passaggi precedenti:

-   [Preparare l'ambiente per Surface Hub](prepare-your-environment-for-surface-hub.md)
-   [Installare fisicamente il dispositivo Surface Hub](physically-install-your-surface-hub-device.md) e
-   [Foglio di lavoro per la configurazione](setup-worksheet-surface-hub.md)

Supponendo che questa sia la situazione, la prima esecuzione dovrebbe essere semplice e veloce.
La procedura normale prevede sei passaggi:

1.  [Pagina Ciao](#first-page)
2.  [Pagina Impostazioni automatiche](#set-up-for-you)
3.  [Pagina Account dispositivo](#device-account)
4.  [Pagina Assegna un nome a questo dispositivo](#name-this-device)
5.  [Pagina Configura gli amministratori per il dispositivo](#setup-admins)
6.  [Aggiornare Surface Hub](#update-surface-hub)

Ognuna di queste sezioni contiene anche informazioni sui percorsi da seguire nel caso sia presente qualche differenza. Ad esempio, la maggior parte dei dispositivi Surface Hub userà una connessione di rete cablata, ma alcuni di essi verranno invece impostati per l'uso di una connessione wireless. I dettagli sono descritti nelle posizioni appropriate.

>[!NOTE]
>È consigliabile installare e predisporre la tastiera separata fornita con il dispositivo Surface Hub prima di iniziare. Vedi la guida all'installazione di Surface Hub per altri dettagli.

 

## <a href="" id="first-page"></a>Pagina Ciao


Questa è la prima schermata che vedrai alla prima accensione del dispositivo Surface Hub. In questa schermata dovrai immettere le informazioni di localizzazione per il tuo dispositivo.

>[!NOTE]
>È anche la posizione da cui è possibile avviare il processo facoltativo di distribuzione di un pacchetto di provisioning. Vedere [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md) se è ciò che si desidera.

 Selezionare una lingua e verranno visualizzate le opzioni di configurazione iniziali.

![Immagine dell'elenco di controllo delle opzioni di Progettazione immagine e configurazione.](images/setuplocale.png)

### Dettagli

Se i valori predefiniti visualizzati sono corretti, sarà possibile fare clic su **Avanti** per procedere. In caso contrario, dovrai immettere i dati nelle caselle appropriate.

-   **Paese/area geografica:** seleziona il paese o l'area geografica in cui verrà usato il dispositivo Surface Hub.
-   **Lingua per le app:** le app e le funzionalità verranno visualizzate con questa lingua e questo formato di lingua.
-   **Layout di tastiera:** seleziona il layout di tastiera per le tastiere su schermo e fisica che verranno usate con il tuo dispositivo.
-   **Fuso orario:** seleziona il fuso orario in cui verrà usato il dispositivo Surface Hub.

### Conseguenze

>[!NOTE]
> Dopo aver completato le impostazioni in questa pagina non potrai tornare a questa schermata, se non reimpostando il dispositivo (vedi [Reimpostazione del dispositivo](device-reset-surface-hub.md)). Assicurati che le impostazioni siano configurate in modo corretto prima di procedere.

 

Quando le impostazioni vengono accettate, il dispositivo inizierà la ricerca di una connessione di rete cablata. Se la connessione viene attivata correttamente, verrà visualizzata la [Pagina Impostazioni automatiche](#set-up-for-you). In caso di problemi con la connessione cablata, nel dispositivo verrà visualizzata la [pagina Configurazione della rete](#network-setup).

Se non è disponibile alcuna connessione cablata, il dispositivo tenterà di configurare una connessione wireless e visualizzerà la [pagina Configurazione della rete](#network-setup).

## <a href="" id="network-setup"></a>pagina Configurazione della rete


Vedrai questa pagina se il dispositivo non rileva una connessione cablata utilizzabile per connettersi a una rete o a Internet. Da questa pagina puoi connetterti a una rete wireless o saltare l'impostazione della connessione di rete.

![Immagine della pagina di configurazione della rete.](images/setupnetworksetup-1.png)

### Dettagli

Questa schermata viene visualizzata solo se il dispositivo non riesce a rilevare una rete cablata. Se viene visualizzata questa schermata, hai tre scelte:

-   Puoi selezionare una delle reti wireless indicate. Se la rete è protetta verrai indirizzato a una pagina di accesso. Vedi [Configurazione della rete wireless](#wireless) per altri dettagli.
-   Fai clic su **Ignora questo passaggio** se non vuoi eseguire la connessione a una rete. Verrà visualizzata la [pagina Impostazioni automatiche](#set-up-for-you).
    >[!NOTE]
    >Se salti questo passaggio, il dispositivo non potrà usare una connessione di rete e tutte le funzionalità di Surface Hub che richiedono una connessione di rete non saranno disponibili, ad esempio gli aggiornamenti di sistema e la sincronizzazione di e-mail e calendario. È possibile connettersi a una rete wireless in seguito usando le impostazioni (vedere [gestione della rete wireless](wireless-network-management-for-surface-hub.md)).

     

-   È possibile collegare un cavo di rete mentre è visualizzata questa schermata. Il dispositivo lo rileverà e aggiungerà il pulsante **Avanti** nella schermata. Fai clic su **Avanti** per continuare con l'attivazione della connessione cablata.

### Conseguenze

Se il dispositivo dispone di una connessione cablata all'avvio e può stabilire una connessione di rete o Internet, questa pagina non verrà visualizzata. Se vuoi usare una connessione wireless per il dispositivo, assicurati che durante la prima esecuzione non sia collegato un cavo Ethernet in modo da visualizzare questa schermata. Indipendentemente da ciò che scegli in questa fase, puoi usare [Impostazioni](wireless-network-management-for-surface-hub.md) per configurare connessioni diverse in un secondo momento.

Se vuoi connetterti a una rete wireless protetta da questa pagina, fai clic sulla rete di tua scelta e quindi fornisci le informazioni necessarie (password o credenziali dell'account) per la connessione. Vedi [Configurazione della rete wireless](#wireless).

## <a href="" id="wireless"></a>Configurazione della rete wireless


Questa pagina viene visualizzata quando selezioni una rete wireless protetta.

![Immagine della pagina di configurazione di una rete wireless.](images/setupnetworksetup-3.png)

### Dettagli

-   **Nome utente:** immetti il nome utente per la rete wireless selezionata.
-   **Password:** questa è la password della rete.

### Conseguenze

Il dispositivo tenterà di connettersi alla rete specificata. Se la connessione riesce, verrai indirizzato alla [pagina Impostazioni automatiche](#set-up-for-you).

## <a href="" id="proxy"></a>Configurazione del proxy di rete


Questa pagina verrà visualizzata quando il dispositivo rileva una connessione cablata con connettività limitata. Hai tre opzioni:

-   Puoi selezionare una rete wireless da usare al posto della connessione cablata limitata.
-   Puoi evitare la connessione a una rete selezionando **Ignora questo passaggio**. Verrà visualizzata la [pagina Impostazioni automatiche](#set-up-for-you).
    **Nota** Se salti questo passaggio, il dispositivo non potrà usare una connessione di rete e tutte le funzionalità di Surface Hub che richiedono una connessione di rete non saranno disponibili, ad esempio la sincronizzazione di e-mail e calendario. È possibile connettersi a una rete wireless in seguito usando le impostazioni (vedere [gestione della rete wireless](wireless-network-management-for-surface-hub.md)).

     

-   Puoi selezionare **Immetti impostazioni proxy** . In questo modo potrai specificare come usare il proxy di rete. Verrà visualizzata la schermata successiva.

    ![Immagine della pagina del proxy di rete.](images/setupnetworksetup-2.png)

    Questa è la schermata che vedrai se hai fatto clic su **Immetti impostazioni proxy** nella schermata precedente.

    ![Immagine dei dettagli relativi alla configurazione del server proxy](images/setupnetworksetup-4.png)

### Dettagli

Per stabilire una connessione di rete, dovrai immettere un nome di script oppure il server proxy e info sulla porta.

-   **Script proxy:** specifica l'indirizzo di uno script proxy.
-   **Server e porta proxy:** puoi specificare l'indirizzo del server proxy e la porta.

### Conseguenze

Quando fai clic su **Avanti**, il dispositivo tenterà di connettersi al server proxy. Se la connessione riesce, verrai indirizzato alla [pagina Impostazioni automatiche](#set-up-for-you).

Puoi evitare la connessione a una rete selezionando **Ignora questo passaggio**. Verrà visualizzata la [pagina Impostazioni automatiche](#set-up-for-you).

>[!NOTE]
>Se salti questo passaggio, il dispositivo non potrà usare una connessione di rete e tutte le funzionalità di Surface Hub che richiedono una connessione di rete non saranno disponibili, ad esempio la sincronizzazione di e-mail e calendario. È possibile connettersi a una rete wireless in seguito usando le impostazioni (vedere [gestione della rete wireless](wireless-network-management-for-surface-hub.md)).

 

## <a href="" id="set-up-for-you"></a>Pagina Impostazioni automatiche


Questa schermata è puramente informativa e mostra le impostazioni consigliate abilitate per impostazione predefinita.

![Immagine della pagina Impostazioni automatiche.](images/setupsetupforyou.png)

### Dettagli

Devi leggere questa schermata e prendere nota dei servizi abilitati per impostazione predefinita. Sono tutti modificabili tramite l'app Impostazioni, se necessario, ma devi tenere conto dei possibili effetti di queste operazioni. Vedi [Introduzione a Surface Hub](intro-to-surface-hub.md) per altri dettagli.

Dopo aver verificato le impostazioni, fai clic su **Avanti** per procedere.

### Conseguenze

Le impostazioni visualizzate nella pagina sono già state applicate e non possono essere modificate fino al termine della prima esecuzione.

## <a href="" id="device-account"></a>Pagina Account dispositivo


In questa pagina il dispositivo Surface Hub ti chiederà le credenziali per l'account del dispositivo che hai configurato in precedenza (vedi [Creare e testare un account del dispositivo](create-and-test-a-device-account-surface-hub.md)). Il dispositivo Surface Hub tenterà di individuare varie proprietà dell'account e, se non ci riesce, potrebbe richiedere informazioni aggiuntive in un'altra pagina.

>[!NOTE]
>Questa sezione non illustra gli errori specifici che possono verificarsi durante la prima esecuzione. Per altre informazioni sugli errori, vedi [Risoluzione dei problemi relativi a Surface Hub](troubleshoot-surface-hub.md) .


![Immagine della pagina Immetti le info dell'account del dispositivo.](images/setupdeviceacct.png)

### Dettagli

Usa un **nome dell'entità utente (UPN)** o **dominio\\nome utente** come identificatore dell'account nel primo campo di immissione. Usa il formato corrispondente all'ambiente e quindi immetti la password.


|                      Ambiente                      | Formato richiesto per l'account del dispositivo |
|-------------------------------------------------------|------------------------------------|
|         L'account del dispositivo è ospitato solo online.         |        nomeutente@dominio.com         |
|        L'account del dispositivo è ospitato solo in locale.         |          DOMINIO\nomeutente           |
| L'account del dispositivo è ospitato online e in locale (ibrido). |          DOMINIO\nomeutente           |

Fai clic su **Ignora la configurazione di un account del dispositivo** per non configurare un account del dispositivo. Tuttavia, se non configuri un account del dispositivo, il dispositivo non verrà integrato completamente nell'infrastruttura. Ad esempio, gli utenti non potranno:

-   Visualizzare un calendario delle riunioni nella schermata iniziale
-   Avviare una riunione dalla schermata iniziale
-   Inviare lavagne tramite e-mail da OneNote
-   Usare Skype for Business per le riunioni.

Se non esegui la procedura di configurazione in questa fase, puoi aggiungere un account del dispositivo in seguito tramite l'app Impostazioni.

Se fai clic su **Ignora la configurazione di un account del dispositivo**, il dispositivo visualizzerà una finestra di dialogo che mostra cosa succede se per il dispositivo non è disponibile un account del dispositivo. Se scegli **Sì, ignora**, verrai indirizzato alla [pagina Assegna un nome a questo dispositivo](#name-this-device).

![Immagine che mostra il messaggio viene visualizzato per confermare che si vuole ignorare la creazione di un account di dispositivo.](images/setupskipdeviceacct.png)

### Conseguenze

Il dispositivo userà il nome UPN o DOMINIO\\Nome utente e la password dell'account del dispositivo per eseguire le operazioni seguenti:

-   Controllare se l'account esiste in Active Directory (AD) o Azure Active Directory (Azure AD).

    -   Se è stato immesso un UPN: il dispositivo cercherà l'account in Azure AD.
    -   Se è stato immesso DOMINIO\\Nome utente: il dispositivo cercherà l'account in AD.
-   Cercare il server Microsoft Exchange per la cassetta postale dell'account.
-   Cercare l'indirizzo SIP (Session Initiation Protocol) per l'account.
-   Recuperare il nome visualizzato e gli attributi alias per l'account.

## <a href="" id="exchange-server"></a>Pagina Exchange Server


Questa pagina verrà visualizzata solo se c'è un problema. In genere, significa che l'account del dispositivo specificato è stato trovato in Active Directory (AD) o Azure Active Directory (Azure AD), ma non è stato individuato il server Exchange per l'account.

![Immagine della pagina del server Exchange.](images/setupexchangeserver-01.png)

### Dettagli

Immetti il nome del server Exchange che ospita la cassetta postale dell'account del dispositivo.

Fai clic su **Ignora la configurazione dei servizi di Exchange** per ignorare questo passaggio. In caso contrario, le persone non saranno in grado di:

-   Visualizzare un calendario delle riunioni nella schermata iniziale.
-   Avviare una riunione dalla schermata iniziale.
-   Inviare lavagne tramite e-mail da OneNote.

Per altri dettagli sulle dipendenze per la configurazione, vedi [Introduzione a Surface Hub](intro-to-surface-hub.md) .

Puoi abilitare i servizi di Exchange per un account del dispositivo in seguito tramite l'app Impostazioni.

Se fai clic su **Ignora la configurazione dei servizi di Exchange**, il dispositivo visualizzerà una finestra di dialogo che mostra le conseguenze. Se scegli **Sì, ignora**, i servizi di Exchange non verranno configurati.

![Immagine del messaggio di conferma visualizzato quando si ignora la configurazione dei servizi di Exchange.](images/setupexchangeserver-02.png)

### Conseguenze

Il dispositivo Surface Hub tenterà di convalidare l'account del dispositivo nel server Exchange immesso. Se il server Exchange è raggiungibile e può essere convalidato, la prima esecuzione continuerà.

Se scegli di non eseguire la configurazione dei servizi di Exchange, il dispositivo Surface Hub interromperà la ricerca del server Exchange e non verrà abilitato alcun servizio di Exchange (posta e calendario).

## <a href="" id="exchange-policies"></a>Pagina dei criteri di Exchange


Questa pagina verrà visualizzata quando:

-   L'account del dispositivo usa criteri Exchange Active Sync (EAS) in cui il criterio PasswordEnabled è impostato su 1.
-   Non è disponibile una connessione a Exchange.
-   Exchange restituisce un codice di stato che indica un errore. (Ad esempio: È stato eseguito il provisioning dell'account per troppi dispositivi.)
-   I protocolli supportati da Exchange non sono supportati da Surface Hub.
-   Exchange restituisce XML errato.

![Immagine della pagina dei criteri di Exchange.](images/setupexchangepolicies.png)

### Dettagli

Questa pagina è puramente informativa, pertanto non è necessario alcun input. Hai comunque due opzioni per continuare: ignorare e procedere oppure ritentare la convalida che ha causato l'errore. Prima di decidere quale opzione è la migliore, leggi la sezione **Conseguenze** seguente. Potresti riuscire a risolvere il problema altrove prima di fare clic su una delle opzioni.

-   **Fai clic qui per continuare a usare i criteri non supportati**: fai clic su questa opzione per continuare la prima esecuzione. Il dispositivo Surface Hub non sarà in grado di usare i servizi di Exchange o di eseguire la sincronizzazione.
-   **Riprova**: ricontrolla i criteri nel server Exchange.

### Conseguenze

Il dispositivo Surface Hub controlla se per i criteri EAS dell'account del dispositivo il criterio PasswordEnabled è impostato su 0 (False). In caso negativo, la posta e il calendario non possono essere sincronizzati e il dispositivo Surface Hub non può usare i servizi di Exchange. Puoi usare gli strumenti di gestione di Exchange da un PC per verificare che il criterio PasswordEnabled sia impostato su 0 per l'account del dispositivo. In caso contrario, puoi riconfigurare l'account e fare clic su **Riprova** qui.

Se il criterio è già stato configurato correttamente, verifica che il dispositivo sia connesso correttamente alla rete o a Internet e possa raggiungere il server Exchange, perché questa pagina verrà visualizzata anche se il dispositivo Surface Hub non riesce a raggiungere il server Exchange.

Un altro motivo per cui Exchange può non essere raggiungibile è correlato all'autenticazione basata su certificati. Potresti ritrovarti bloccato in questa pagina a causa di problemi di certificato. Tieni presente  che se il dispositivo visualizza i codici di errore 0x80072F0D o 0X800C0019, è necessario un certificato. Dato che il provisioning viene eseguito nella prima pagina del processo di prima esecuzione, devi disabilitare i servizi di Exchange facendo clic su **Fai clic qui per continuare a usare i criteri non supportati**e quindi installare i certificati corretti tramite l'app Impostazioni.

Se scegli di non eseguire questo controllo, il dispositivo Surface Hub interromperà la ricerca del server Exchange e la convalida dei criteri EAS e non verrà abilitato alcun servizio di Exchange. Per altri dettagli sulle dipendenze per la configurazione, vedi [Introduzione a Surface Hub](intro-to-surface-hub.md) .

## <a href="" id="name-this-device"></a>Pagina Assegna un nome a questo dispositivo


Questa pagina richiede di specificare due nomi che verranno usati per identificare il dispositivo Surface Hub.

![Immagine della pagina Assegna un nome a questo dispositivo.](images/setupnamedevice.png)

### Dettagli

Se i valori predefiniti visualizzati sono corretti, puoi fare clic su **Avanti** per procedere. In caso contrario, immetti i dati in una o entrambe le caselle di testo.

-   **Nome descrittivo:** si tratta del nome che gli utenti vedranno quando vogliono connettere in modalità wireless a Surface Hub.
-   **Nome dispositivo:** può essere impostato su qualsiasi nome univoco, come descritto nella schermata.

A condizione che entrambi i nomi rispettino i requisiti di lunghezza e non usino caratteri non consentiti, quando fai clic su **Avanti** verrà visualizzata la pagina successiva [Configura gli amministratori per il dispositivo](#setup-admins).

### Conseguenze

Il dispositivo Surface Hub richiede due nomi per il dispositivo, con queste impostazioni predefinite:

-   **Nome descrittivo:** corrisponde per impostazione predefinita al nome visualizzato dell'account del dispositivo
-   **Nome dispositivo:** corrisponde per impostazione predefinita all'alias dell'account del dispositivo

Anche se entrambi i nomi possono essere modificati in seguito, tieni presente che:

-   Il nome descrittivo deve essere riconoscibile e diverso in modo che gli utenti possano distinguere un dispositivo Surface Hub da un altro durante il tentativo di connessione wireless.
-   Se decidi di aggiungere il dispositivo a un dominio, il nome del dispositivo non deve essere uguale a quello di altri dispositivi nel dominio Active Directory dell'account. Il dispositivo non può essere aggiunto al dominio se usa lo stesso nome di un altro dispositivo aggiunto al dominio.

>[!NOTE]
>Se desideri abilitare [Miracast su infrastruttura](miracast-over-infrastructure.md), il nome del dispositivo deve essere rilevabile tramite DNS. Puoi ottenere questo consentendo al dispositivo Surface Hub di registrarsi automaticamente tramite DNS dinamico o creando manualmente un record A o AAAA per il nome del dispositivo di Surface Hub.

## <a href="" id="setup-admins"></a>Pagina Configura gli amministratori per il dispositivo


In questa pagina, potrai scegliere tra diverse opzioni per stabilire come vuoi configurare gli account amministratore per la gestione locale del dispositivo.

Dato che Surface Hub può essere usato da qualsiasi numero di dipendenti autenticati, le impostazioni vengono bloccate in modo che non possano essere modificate da una sessione all'altra. Solo gli amministratori possono configurare le impostazioni nel dispositivo e in questa pagina potrai scegliere il tipo di amministratori che avranno questo privilegio.

>[!NOTE]
>Lo scopo di questa pagina è principalmente quello di stabilire chi può configurare il dispositivo dall’interfaccia utente del dispositivo, vale a dire chi può effettivamente visitare un dispositivo, accedervi, aprire l’app Impostazioni e apportare modifiche alle impostazioni.

 

![Immagine della pagina Configura gli amministratori per il dispositivo.](images/setupsetupadmins.png)

### Dettagli

Scegli una delle tre opzioni disponibili:

-   **Usa Microsoft Azure Active Directory**
-   **Usa Servizi di dominio Active Directory**
-   **Usa un amministratore locale**

### Conseguenze

Questo è ciò che accade quando scegli un'opzione.

-   **Usa Microsoft Azure Active Directory**

    Scegliendo questa opzione puoi aggiungere il dispositivo ad Azure AD. Quando fai clic su **Avanti**, il dispositivo verrà riavviato per applicare alcune impostazioni e quindi verrà visualizzata la pagina [Usa Microsoft Azure Active Directory](#use-microsoft-azure) e verrà richiesto di immettere le credenziali che possono consentire l'aggiunta ad Azure AD. I membri del ruolo di amministratori globali di Azure dall'organizzazione unita saranno in grado di usare l'app Impostazioni. Le persone specifiche autorizzate dipendono dalla sottoscrizione di Azure AD e da come sono state configurate le impostazioni per l'organizzazione di Azure AD.
    
    > [!IMPORTANT]
    > Gli amministratori aggiunti al ruolo di Azure Device Administrators dopo l'accesso al dispositivo ad Azure AD non saranno in grado di usare l'app Impostazioni.
    >
    > Se si accede a Surface Hub da Azure AD durante la prima configurazione, l'accesso single sign-on (SSO) per le app di Office non funzionerà correttamente. Gli utenti avranno accesso individualmente ad ogni app di Office.

-   **Usare i Servizi del dominio di Active Directory**

    Fare clic su questa opzione per aggiungere il dispositivo ad AD. Quando fai clic su **Avanti**verrà visualizzata la pagina [Usa Servizi di dominio Active Directory](#use-active-directory) e richiesto di immettere le credenziali che consentono l'aggiunta al dominio specificato. Dopo l'aggiunta, puoi selezionare un gruppo di sicurezza dal dominio aggiunto e le persone incluse in tale gruppo di sicurezza potranno usare l'app Impostazioni.

-   **Usa un amministratore locale**

    L'amministratore non sarà supportato da alcun servizio directory, quindi ti consigliamo di scegliere questa opzione solo se il dispositivo non ha accesso ad Azure AD o AD. Dopo avere creato nome utente e password dell'amministratore nella pagina [Usa un amministratore locale](#use-a-local-admin), dovrai immettere nuovamente le stesse credenziali ogni volta che apri l'app Impostazioni.

    Tieni presente che un amministratore locale deve avere accesso fisico a Surface Hub per eseguire l’accesso.

>[!NOTE]
>Dopo aver completato questo processo, non potrai più modificare l’opzione per l’amministratore del dispositivo, se non reimpostandolo.

 

### <a href="" id="use-microsoft-azure"></a>Usa Microsoft Azure Active Directory

Se hai deciso di aggiungere il dispositivo Surface Hub ad Azure Active Directory (Azure AD), vedrai questa pagina **Conseguenze** . Leggi il contenuto e fai clic su **Avanti** per passare alla **pagina Preparativi per l'accesso**.

L'aggiunta ad Azure AD presenta due vantaggi principali:

1.  Alcuni dipendenti dall'organizzazione saranno in grado di accedere al dispositivo come amministratori e potranno avviare l'app Impostazioni e configurare il dispositivo. Le persone con autorizzazioni amministrative verranno definite nella tua sottoscrizione di Azure AD.

2.  Se Azure AD è connesso a una soluzione di gestione di dispositivi mobili (MDM), il dispositivo verrà registrato nella soluzione MDM in modo da poter applicare i criteri e la configurazione.

    ![Immagine del messaggio che viene visualizzato quando aggiungi Surface Hub ad Azure Active Directory.](images/setupjoiningazuread-1.png)

### Dettagli

È necessario immettere le informazioni seguenti:

-   **UPN dell'utente:** il nome dell'entità utente (UPN) di un account che può essere aggiunto ad Azure AD.
-   **Password:** la password dell'account usato per l'aggiunta ad Azure AD.

![Immagine delle informazioni di accesso all'account.](images/setupjoiningazuread-2.png)

Se arrivi a questo punto e non hai credenziali valide per un account Azure AD, il dispositivo ti permetterà di continuare creando un account di amministratore locale. Fai clic su **Configurare Windows con un account locale**.

![Immagine della pagina Configura un account amministratore.](images/setupjoiningazuread-3.png)

### Conseguenze

Dopo aver immesso credenziali valide per un account Azure AD, il dispositivo tenterà l'aggiunta all'organizzazione di Azure AD associata. In caso positivo, il dispositivo eseguirà il provisioning dei dipendenti nell'organizzazione come amministratori locali nel dispositivo. Se il tuo tenant Azure AD è stato configurato per la gestione di dispositivi mobili, il dispositivo verrà anche registrato nella soluzione MDM.

### <a href="" id="use-active-directory"></a>Usa Servizi di dominio Active Directory

Questa pagina richiederà le credenziali per accedere a un dominio, in modo che il dispositivo Surface Hub possa eseguire il provisioning di un gruppo di sicurezza come amministratori del dispositivo.

Dopo aver aggiunto il dispositivo a un dominio, devi specificare un gruppo di sicurezza da tale dominio. Verrà eseguito il provisioning di questo gruppo di sicurezza come amministratori in Surface Hub e tutti gli utenti del gruppo di sicurezza potranno immettere le credenziali di dominio per accedere a Impostazioni.

![Immagine della pagina Configura gli amministratori usando l'aggiunta al dominio.](images/setupdomainjoin.png)

### Dettagli

È necessario immettere le informazioni seguenti:

-   **Dominio:** questo è il nome di dominio completo (FQDN) del dominio a cui vuoi aggiungere il dispositivo. È possibile usare un gruppo di sicurezza di questo dominio per gestire il dispositivo.
-   **Nome utente:** il nome utente di un account con autorizzazioni sufficienti per l'aggiunta al dominio specificato. 
-   **Password:** la password per l'account.

Dopo aver verificato le credenziali, verrà richiesto di digitare il nome di un gruppo di sicurezza. Questo input è necessario.

![Immagine della pagina Immetti un gruppo di sicurezza.](images/setupsecuritygroup-1.png)

### Conseguenze

Usando il dominio specificato, le credenziali dell'account dalla [pagina Usa Servizi di dominio Active Directory](#use-active-directory) e il nome del dispositivo dalla pagina [Assegna un nome a questo dispositivo](#name-this-device) , il dispositivo Surface Hub tenterà l'aggiunta al dominio. Se l'aggiunta riesce, la prima esecuzione continuerà e richiederà un gruppo di sicurezza. In caso contrario, la prima esecuzione verrà interrotta e ti verrà richiesto di modificare le informazioni fornite.

Se l'aggiunta riesce, verrà visualizzata la pagina **Immetti un gruppo di sicurezza** . Quando fai clic sul pulsante **Seleziona** in questa pagina, il dispositivo cercherà il gruppo di sicurezza specificato nel tuo dominio. Se viene trovato, il gruppo verrà verificato. Fai clic su **Fine** per completare il processo di prima esecuzione.

>[!NOTE]
>Se aggiungi Surface Hub a un dominio, potrai separarlo solo reimpostando il dispositivo.

 

### Usa un amministratore locale

Se decidi di non usare Azure Active Directory (Azure AD) o Active Directory (AD) per gestire il dispositivo Surface Hub, dovrai creare un account amministratore locale.

![Immagine della pagina Configura un account amministratore per la configurazione di un amministratore locale.](images/setuplocaladmin.png)

### Dettagli

È necessario immettere le informazioni seguenti:

-   **Nome utente:** si tratta del nome utente dell'account amministratore locale che verrà creato per questo dispositivo Surface Hub.
-   **Password:** questa è la password dell'account del dispositivo.
-   **Immetti nuovamente la password:** verifica della password immessa nella casella precedente.

### Conseguenze

Questa pagina tenerà di creare un nuovo account amministratore con le credenziali immesse qui. Se l'operazione riesce, la prima esecuzione verrà terminata. In caso contrario, ti verrà richiesto di immettere credenziali diverse.

## <a href="" id="update-surface-hub"></a>Aggiornare Surface Hub


>[!IMPORTANT]
>Prima di eseguire gli aggiornamenti, assicurati di leggere [Salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md) per essere certo di avere un backup della chiave.

 

Per ottenere le funzionalità e le correzioni più recenti, è consigliabile aggiornare il dispositivo Surface Hub subito dopo aver completato tutti i passaggi della procedura di prima esecuzione.

1.  Verificare che il dispositivo abbia accesso ai server Windows Update. 
2.  Apri impostazioni, fai clic su **Aggiornamento e sicurezza**, **Windows Update** e quindi fai clic su **Verifica disponibilità aggiornamenti**.
3.  Se sono disponibili aggiornamenti, verranno scaricati. Dopo aver completato il download, fai clic sul pulsante **Aggiorna** per installare gli aggiornamenti.
4.  Segui le istruzioni sullo schermo dopo l'installazione degli aggiornamenti. Potrebbe essere necessario riavviare il dispositivo.

 

 






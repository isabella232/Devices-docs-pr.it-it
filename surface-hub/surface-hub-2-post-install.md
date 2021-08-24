---
title: Configurare Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo include suggerimenti per garantire la migliore esperienza quando si usa un computer con tocco e penna di grandi dimensioni personalizzato.
keywords: Surface Hub, Windows 10 desktop, installare, configurazione
ms.prod: surface-hub
ms.mktglfcycl: deploy
ms.localizationpriority: low
ms.sitesec: library
ms.pagetype: deploy
audience: admin
manager: laurawi
ms.audience: itpro
author: greg-lindsay
ms.author: greglin
ms.collection: M365-modern-desktop
ms.topic: article
ms.date: 12/08/2020
appliesto:
- Surface Hub 2S
ms.openlocfilehash: 5bb207823abb462179faf72810354885050dc25f
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911231"
---
# <a name="configure-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Configurare Windows 10 Pro o Enterprise in Surface Hub 2

Dopo aver completato il processo di installazione della migrazione a Windows 10 Pro o Enterprise, è possibile eseguire la procedura seguente per configurare app e impostazioni nel Surface Hub 2. Questi passaggi sono consigliati per garantire l'esperienza ottimale quando si usa questo computer personalizzato con tocco su schermo grande e penna.

Quando si eseguono questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.

## <a name="configure-system-settings"></a>Configurare le impostazioni di sistema

1. Accedi con un account con privilegi di amministratore locale nel dispositivo.  

    - Nei dispositivi aggiunti ad Azure AD, l'utente che esegue l'aggiunta ad Azure AD viene aggiunto automaticamente al gruppo di amministratori locali. Gli amministratori globali di Azure AD e gli amministratori dei dispositivi Azure AD <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> sono anche amministratori </a> locali. 
    
    - È possibile digitare **net localgroup administrators al** prompt dei comandi per elencare gli account con diritti di amministratore locale.
    
2. Rinominare il dispositivo con un nome descrittivo, ad esempio: **nomeutente-SHub-Desktop**.

3. Seleziona **Start**  >  **Impostazioni**  >  **Accounts**Sincronizza le impostazioni  >  **e** disattiva Le impostazioni di **sincronizzazione.** 

    - Le impostazioni utilizzate qui sono destinate a abilitare la migliore esperienza di tocco su schermo grande e pertanto potresti non voler sincronizzare altri dispositivi.
    
4. Riavvia il dispositivo.

## <a name="enable-the-touch-keyboard-and-touchpad"></a>Abilitare la tastiera virtuale e il touchpad

1. Seleziona **Start**  >  **Impostazioni**  >  **dispositivi**  >  **digitando** **** e attiva Mostra la tastiera virtuale quando non è in modalità tablet e non è collegata alcuna tastiera.

2. Tocca e tieni premuto o fai clic con il pulsante destro del mouse sulla barra delle applicazioni e quindi scegli Mostra pulsante **tastiera virtuale** e Mostra **pulsante touchpad.** 

    - La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad virtuale aiuta con selezioni precise, suggerimenti per lo schermo al passaggio del mouse o come alternativa al tocco e al blocco per fare clic con il pulsante destro del mouse. 
    
    - Vedi l'esempio seguente.

      ![Impostazioni tocco.](images/touch.png)

3. Configura la tastiera virtuale su QWERTY e mobile.

    1. Seleziona **l'icona** Tastiera sulla barra delle applicazioni per visualizzare la tastiera virtuale.
    
    1. Sulla tastiera virtuale seleziona l'icona della tastiera nell'angolo in alto a sinistra per aprire le impostazioni della tastiera.
    
    1. Seleziona il tipo di tastiera accanto all'ultimo nella riga superiore per abilitare QWERTY e l'ultima opzione nella seconda riga per abilitare la virgola mobile, che è molto utile su questo grande schermo. Vedere gli esempi seguenti.

       ![Impostazioni della tastiera.](images/kbd.png)
 
4. Configurare le impostazioni della tastiera virtuale.

    1. Seleziona **l'Impostazioni** sulla tastiera virtuale o cerca e apri Impostazioni **digitazione.**
    
       ![impostazioni della tastiera soft.](images/sh2-softkeyboard.png)

    1. Abilita tutte le opzioni in Ortografia, Digitazione e Tastiera virtuale.


L'esempio seguente mostra il track pad, utile per spostarsi e selezionare le opzioni. La tastiera su schermo viene usata per cercare il Microsoft Store:

![Uso del track pad.](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a>Configurare Bluetooth tastiera e mouse (facoltativo)

Connessione tastiera e mouse se usi il dispositivo come dispositivo Windows principale o lo usi spesso per il lavoro di digitazione o di precisione.

Se il Surface Hub è vicino a un PC, puoi usare Mouse senza bordi per spostarsi senza problemi tra il Surface Hub <a href="https://aka.ms/mm" target="_blank"> </a> e il PC. Per altre informazioni, vedi <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> Download Microsoft da The Garage: Mouse without Borders. </a>

## <a name="example-of-taskbar-layout"></a>Esempio di layout della barra delle applicazioni

Dopo aver completato i passaggi seguenti per configurare il Surface Hub 2 per Windows 10 Professional o Enterprise, ti consigliamo di usare l'aggiunta delle applicazioni più usate alla barra delle applicazioni per un avvio rapido con un tocco di ogni applicazione. Di seguito è riportato un esempio dell'aspetto della barra delle applicazioni:

 ![Layout della barra delle applicazioni.](images/taskblyt.png)
### <a name="update-installed-apps"></a>Aggiornare le app installate

Per aggiornare tutte le app dello Store installate:

1. Apri Microsoft Store app e seleziona **i** puntini di sospensione Vedi altri puntini di sospensione nell'angolo in alto a destra.
2. Seleziona **Download e aggiornamenti.**
3. Seleziona **Scarica aggiornamenti**

### <a name="scan-for-and-install-all-windows-updates"></a>Cercare e installare tutti gli Windows aggiornamenti
Dopo la migrazione a Windows 10 Professional o Windows 10 Enterprise, potrebbero essere disponibili aggiornamenti di manutenzione e funzionalità da installare. 

- Vai a **Impostazioni**  >  **Aggiornamento & sicurezza** > e quindi seleziona Controlla **aggiornamenti**.
- Se sono presenti aggiornamenti, installarli, riavviarli e quindi ripetere il processo fino a quando non viene visualizzata la notifica seguente:

> [!div class="mx-imgBorder"]
> ![Windows Aggiornare la notifica "Sei aggiornato".](images/wustatus.png)


## <a name="onedrive-for-business"></a>OneDrive for Business

Usa <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business per condividere facilmente </a> strumenti, log e altri file tra tutti i dispositivi di lavoro.

- OneDrive consente di condividere i file di lavoro tra i portatili, Surface Hub Desktop e i dispositivi mobili gestiti da Intune. I file possono essere modificati su qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.

- Considerando le dimensioni dell'SSD di Surface Hub (128 GB), se si configura OneDrive nel dispositivo desktop Surface Hub, assicurarsi che la configurazione predefinita sia mantenere i file online e scaricare i file durante l'uso.

Per configurare OneDrive per il download dei **** file solo quando necessario, impostare l'impostazione File su richiesta su Salva spazio e scarica i file mentre **li usi.** Per ulteriori informazioni, vedere <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Query and set Files On-Demand states in Windows </a> .

![OneDrive impostazioni predefinite.](images/onedrive.png)

> [!NOTE]
> Puoi anche ripetere questi passaggi per configurare un OneDrive personale, ma assicurati di risparmiare spazio su disco e scaricare solo i file in base alle tue necessità.

## <a name="sharepoint-and-teams"></a>SharePoint e Teams

SharePoint e Teams Channel possono essere sincronizzati localmente con i dispositivi desktop, ad esempio laptop e Surface Hub, usando il motore sincronizzazione OneDrive.

Per sincronizzare i file aziendali interni all'unità locale con l sincronizzazione OneDrive app:

1. Passare a un SharePoint e passare alla directory dei documenti di primo livello per i file che si desidera visualizzare o modificare dal dispositivo locale.

2. Fare clic sul **pulsante Sincronizza** nella parte superiore della SharePoint barra multifunzione.

3. Selezionare **Apri** nel popup **Questo sito sta tentando di aprire Microsoft OneDrive**.

4. Verifica che i SharePoint siano sincronizzati con l'unità locale selezionando l'icona OneDrive nella parte inferiore destra della barra delle applicazioni.

5. Verificare che la configurazione sia impostata per mantenere i file online e scaricarli solo quando vengono utilizzati:

    1. Apri Esplora file.
    
    2. Passare a e fare clic con il pulsante destro del mouse sul nome SharePoint; ad esempio, **Contoso \ \<SharePoint Document Folder Name\> **.
    
    3. Selezionare **Liberare spazio.**
    
    4. Nella colonna Stato verrà visualizzato lo stato di file e cartelle. Per ulteriori informazioni, vedere <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sync SharePoint files with the sincronizzazione OneDrive client </a> .
    
6. Teams I file di canale vengono archiviati SharePoint siti, con tutte le stesse funzionalità SharePoint documenti, tra cui la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali. Per sincronizzare Teams Channel:

    1. Passa al canale Teams di interesse e seleziona la **scheda File** nella parte superiore. Selezionare quindi **Sincronizza**. I file inizieranno la sincronizzazione e saranno visibili in Esplora file in **Desktop \ Contoso \ \<name of the Teams Channel\> **.
    
    2. Utilizzare la stessa procedura utilizzata per sincronizzare i siti di SharePoint per mantenere i file nel cloud e scaricarli solo quando vengono utilizzati, toccando e tenendo premuto o facendo clic con il pulsante destro del mouse in Esplora file sul nome del canale di Teams e quindi selezionando Libera **spazio**.

## <a name="surface-hub-pen-settings"></a>Surface Hub della penna

**Associare la Bluetooth Surface Hub penna**

Associa la penna per mantenere aggiornato il firmware della penna, imposta i tasti di scelta rapida della penna e ottieni informazioni sulla carica della batteria nella pagina delle impostazioni del dispositivo Bluetooth o nell'app Surface:

1. Selezionare **Start**  >  **Impostazioni**  >  **Devices**.

2. Seleziona **Aggiungi Bluetooth o altro dispositivo.**

3. Scegliere **Bluetooth**.

4. Rimuovi il pulsante della coda della penna e scuoti per scollegare la connessione della batteria.

5. Riempiamo il tappo e tieni premuto il tappo fino a quando il LED di associazione lampeggia.

6. Nelle impostazioni Surface Hub Bluetooth, scegliere **Surface Hub 2 Penna.**

7. Completare l'operazione di associazione. 

8. Se l'associazione non riesce, puoi tentare di associare di nuovo la penna. Se non funziona, puoi verificare se la batteria è carica verificando che la penna funzioni nell'applicazione Lavagna. In caso contrario, sostituire la batteria e quindi provare di nuovo ad associare la penna. Se necessario, riavviare il dispositivo e riprovare.

**Impostare i tasti di scelta rapida della penna** La Surface Hub penna ha un pulsante di scelta rapida a volte definito "clic in coda". La configurazione dei tasti di scelta rapida richiede la prima associazione della penna, come descritto in precedenza.

1. Cerca Penna e seleziona **Impostazioni & Windows Ink penna.**

2. Nella parte inferiore della pagina seleziona Tasti di scelta rapida penna che apre la finestra di dialogo, mostrata qui:

   ![Tasti di scelta rapida della penna.](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a>Configurazione della fotocamera

Puoi montare la fotocamera nella parte superiore o su entrambi i lati del dispositivo. Montare la fotocamera in una posizione per ottimizzare l'angolo della fotocamera se si utilizza l'hub con un supporto desktop invece di un carrello o se ci si trova in prossimità dell'hub. La fotocamera non ruota automaticamente, quindi devi avere un tasto esadecimale di 2 mm per ruotare manualmente la fotocamera. 

Per altre informazioni su come montare la fotocamera e ruotarla manualmente, vedi l'Surface Hub dell'obiettivo della <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> fotocamera 2S. </a>

## <a name="windows-hello-configuration"></a>Windows Hello configurazione

Surface Hub 2S che esegue Windows 10 Enterprise consente la famiglia completa di applicazioni desktop Win32 e opzioni di Windows Hello biometriche. L'Surface Hub lettore di impronte digitali 2 può essere collegato a qualsiasi porta USB-C del dispositivo. 

Per ordinare un lettore di impronte digitali Surface Hub 2 o visualizzare le specifiche tecniche, vedere (surface-hub-2-essential-add-ons.md" target="_blank">Componenti aggiuntivi essenziali per Windows 10 Pro e Enterprise in Surface Hub 2 </a> . 

Dopo aver inserito il lettore di impronte digitali, seleziona **Avvia**Impostazioni account Opzioni di accesso  >  ****  >  ****  >  ****  >  **Windows Hello'impronta** digitale per registrare l'impronta digitale.

Usa un dispositivo Windows Hello certificato per il riconoscimento del volto. La Surface Hub 2S non supporta il riconoscimento Windows Hello del volto.

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a>Abilitare un'icona di scelta rapida della schermata di blocco sulla barra delle applicazioni

Per aggiungere un'icona alla barra delle applicazioni che abilita il blocco dello schermo con un tocco simile al tasto di scelta rapida Windows-L: 

1.  Toccare e tenere premuto o fare clic con il pulsante destro del mouse sul desktop, selezionare **Nuovo**  >  **collegamento**  >  **Sfoglia**  >  **desktop**  >  **OK**  >  **Avanti.**

1.  Fornisci un nome per il collegamento, ad esempio **Blocca il PC,** quindi seleziona **Fine.**

1.  Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento appena creato sul desktop e selezionare **Proprietà.** Nella scheda **Collegamento** immettere quanto segue nel **campo** Destinazione: **Rundll32.exe User32.dll,LockWorkStation**

1.  Seleziona il **pulsante Cambia icona** e cercaC:\Windows\System32\imageres.dlle seleziona un'icona da usare. **** 

    Vedi l'esempio seguente:

    ![Scegliere un'icona.](images/lock.png)
    
1.  Selezionare **OK** per salvare il collegamento.

1.  Fai clic con il pulsante destro del mouse o tocca e tieni premuto il collegamento e seleziona **Aggiungi alla barra delle applicazioni.**

1. Dopo aver aggiunto il collegamento di blocco alla barra delle applicazioni, puoi eliminarlo dal desktop.

## <a name="applications"></a>Applicazioni


### <a name="microsoft-whiteboard"></a>Microsoft Whiteboard

Per installare il Microsoft Whiteboard:

 - Seleziona **l Area Windows Ink a** icona nella parte inferiore destra della barra delle applicazioni e scarica **Lavagna.**
 
   ![Area di lavoro input penna.](images/ink.png) 

In alternativa, è possibile installare Whiteboard dal Microsoft Store:

1. Apri Microsoft Store'app e cerca **Lavagna.**

2. Scegliere **No grazie** per accedere e usare tra dispositivi.

3. Aggiungi Lavagna alla barra delle applicazioni.

### <a name="surface-app"></a>App Surface

1. Nell'Microsoft Store cerca **Surface.**

2. Imposta il **filtro Disponibile su** Tutti i **dispositivi.**

3. Installa l'app **Surface.** Questa dovrebbe essere la prima app elencata. Per installare l'app, potrebbe essere necessario associare l'amministratore di sistema a Store.

4. Aggiungi **l'app Surface** alla barra delle applicazioni.

### <a name="snip--sketch"></a>Cattura e annota

1. Apri **l'app Snip & Sketch** e aggiungila alla barra delle applicazioni.

2. Selezionare i puntini di sospensione nell'angolo superiore destro e quindi selezionare **Impostazioni**.

3. In **Impostazioni**, attivare Copia automatica **negli Appunti,** Salva i renip e Più **finestre** (facoltativo). ****

### <a name="microsoft-office"></a>Microsoft Office

1. Aprire il <a href="https://portal.office.com/account#installs" target="_blank"> Office portal e installare le applicazioni </a> desiderate.

2. Aggiungi le applicazioni Office desiderate alla barra delle applicazioni.

3. Se Outlook è installato, assicurarsi di impostare il Outlook OST per salvare solo la cache delle ultime due settimane. Ciò ridurrà notevolmente l'utilizzo del disco e i tempi di installazione.

    - Seleziona **File**  >  **Account Impostazioni** e seleziona il tuo account.
    
    - Seleziona **Cambia** e imposta il dispositivo di scorrimento per Usa **modalità Exchange cache** su 14 giorni.

### <a name="microsoft-teams"></a>Microsoft Teams

1. Scaricare e installare <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft Teams </a> .

2. Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).

3. Aggiungi Teams alla barra delle applicazioni.

4. Prendi in considerazione Teams notifiche sul dispositivo per evitare distrazioni (facoltativo).

   ![Teams notifiche.](images/teams.png)

### <a name="connect-app"></a>Connessione app

> [!IMPORTANT]
> In Windows 10 versione 2004 e successive, l'app Connessione per la proiezione wireless con Miracast non è installata per impostazione predefinita, ma è disponibile come funzionalità facoltativa. Se è stato installato (o aggiornato a) Windows versione 2004 o successiva, nella schermata Projecting to this PC nelle impostazioni potrebbe essere visualizzato quanto segue:

![Project a questo PC.](images/sh2-project.png) 


1. Per installare l'app dalla pagina delle impostazioni "Proietta in questo PC", seleziona Funzionalità facoltative ****  >  **Aggiungi una funzionalità** e quindi installa l'app **Schermo** wireless.

2. In Alcuni Windows e i dispositivi Android possono proiettare su questo PC quando dici che **è OK,** scegli:

    - **Disponibile ovunque** se il dispositivo non si trova in una rete aziendale.
    - In caso contrario, **scegliere Disponibile ovunque nelle reti protette.**
    
3. In **Chiedi di proiettare su questo PC**scegli Solo prima **volta.**

4. In **Richiedi PIN per l'associazione**scegliere **Mai.**

5. Per avviare l'app e aggiungere l'app alla barra delle applicazioni, cerca **Connessione**.

6. Apri l'app. Mentre l'app è aperta, fai clic con il pulsante destro del mouse sull'icona Connessione'app sulla barra delle applicazioni e seleziona **Aggiungi alla barra delle applicazioni.**

7. Chiudi quindi l'app Connessione app. **Project questo PC potrebbe** non funzionare a meno che l'app non sia stata eseguita almeno una volta.

Configurazione consigliata quando non nella rete aziendale:

![Impostazioni a casa.](images/project1.png)

Configurazione consigliata nella rete aziendale:

![Impostazioni sul lavoro.](images/project2.png)

### <a name="your-phone&quot;></a>Il tuo telefono

**L Il tuo telefono app** è installata per impostazione predefinita in Windows 10. Se non è presente, puoi anche installarlo da Windows Store.

Per informazioni sulla configurazione dell'app, vedi Come configurare Il tuo telefono in Windows 10 e sincronizzare i dati <a href=&quot;https://www.windowscentral.com/how-set-your-phone-windows-10&quot; target=&quot;_blank&quot;> tra PC e </a> telefono. Vedi anche <a href=&quot;https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10&quot; target=&quot;_blank&quot;> Come risolvere i problemi comuni con Il tuo telefono'app in Windows 10 </a> .

###  <a name=&quot;fancy-zones&quot;></a>Aree sofisticate


**Fancy Zones** fa parte di una raccolta di strumenti denominati <a href=&quot;https://github.com/microsoft/PowerToys/releases&quot; target=&quot;_blank&quot;> PowerToys in </a> GitHub.. È un ottimo modo per usare lo spazio sullo schermo su un Surface Hub 2, offrendoti la possibilità di definire layout fissi sullo schermo (&quot;zone")e quindi selezionare l'app che verrà eseguita in ogni area. 


Il [wiki PowerToys contiene](https://github.com/microsoft/PowerToys/wiki) istruzioni su come usare e personalizzare ogni strumento, tra cui [FancyZones.](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview) A livello elevato: dopo aver installato PowerToys, puoi selezionare o creare un layout personalizzato e quindi tenere premuto il tasto MAIUSC e trascinare o usare i tasti della tastiera per spostare un'app in esecuzione in aree specifiche. L'Bluetooth tastiera usb o USB ti aiuterà a risolvere questo problema oppure puoi usare la tastiera virtuale su schermo e il touchpad.

**Suggerimenti per power toys**
- Per ricevere notifiche tramite posta elettronica PowerToys aggiornamenti delle versioni GitHub, fare clic sul pulsante "iscrizione" nella parte superiore della [pagina.](https://github.com/microsoft/PowerToys/releases)
- Una volta PowerToys, è possibile ricevere notifiche Windows e/o scaricare e installare gli aggiornamenti più recenti **** configurando le impostazioni di PowerToys Scarica automaticamente gli aggiornamenti.
- Per accedere alle impostazioni PowerToys, seleziona l'icona su **Carat** Applicazioni in esecuzione sulla barra delle applicazioni e quindi fai clic con il pulsante destro del mouse o tieni premuta l'icona PowerToys finché non viene visualizzato il menu. Selezionare "Impostazioni".
- Nella parte inferiore della pagina delle PowerToys, attiva Scarica **automaticamente** gli aggiornamenti.
- Dopo il rilascio di un aggiornamento, Windows verrà visualizzata una notifica che consente di scegliere quando installare l'aggiornamento.


### <a name="edge-chromium-browser"></a>Edge Chromium browser

Scaricare e installare il nuovo <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> edge Chromium browser </a> .


### <a name="surface-hub-hardware-diagnostic-tool"></a>Surface Hub Strumento di diagnostica hardware

Lo <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> Surface Hub di diagnostica hardware disponibile gratuitamente </a> dall'Microsoft Store. Lo strumento è progettato per garantire che il Surface Hub funzioni al meglio. Contiene test per determinare se il firmware è aggiornato e configurato correttamente. I test interattivi consentono di verificare che le funzionalità essenziali funzionino come previsto. Se si verificano problemi, i risultati possono essere salvati e condivisi con il team di supporto di Surface Hub. Fai clic sul collegamento per installarlo dal Microsoft Store e quindi aggiungi l'applicazione alla barra delle applicazioni.

## <a name="additional-settings"></a>Impostazioni aggiuntive

### <a name="pen-tail-select-to-launch-whiteboard"></a>Selezione della coda della penna per l'avvio della Lavagna

1. Cerca Penna **e** seleziona **Impostazioni & Windows Ink penna**.

2. Nella parte inferiore della pagina, in Scelte **rapide da** penna impostare **Seleziona una sola volta** **Microsoft Whiteboard**. 

### <a name="power-management"></a>Gestione del risparmio energia

Sono disponibili diverse impostazioni di risparmio energia per ottenere la migliore esperienza con Windows 10 Pro o Enterprise su Surface Hub 2. Sono inclusi i timeout di schermo e pc e il modo in cui interagiscono con il rilevamento della presenza umana incorporato (Doppler), lo screen saver e la password di protezione e quindi, se appropriato, come passare le impostazioni di risparmio energia dei Criteri di gruppo destinate agli utenti portatili/desktop.

Windows 10 Pro o Enterprise su Surface Hub 2 impedisce lo stato di sospensione dello schermo tramite azioni tramite tocco, mouse e tastiera, nonché il rilevamento dell'occupazione umana incorporato (Doppler). Il rilevamento dell'occupazione umana è abilitato per impostazione predefinita, ma, se lo si desidera, può essere disabilitato in UEFI attivando l'opzione del dispositivo nello strumento Configuratore UEFI di Surface nell'ambito della migrazione iniziale oppure creando e applicando un pacchetto di configurazione UEFI successivo. 

**Gestione risparmio energia: impostazioni di sospensione dello schermo e del PC**

1. Selezionare **Start**  >  **Impostazioni**  >  **System**  >  **Power & sleep**.

2. Impostare il dispositivo di scorrimento della modalità risparmio energia **su Prestazioni migliori.**

3. Configura i valori dello schermo e della sospensione in base alle tue preferenze, tenendo conto anche del rilevamento della presenza Doppler che riattiva il dispositivo quando viene rilevato il movimento. Di conseguenza, come procedura consigliata, è consigliabile impostare Schermo su Disattiva dopo **2** ore e il PC su Disattiva **dopo 4 ore.**

**Risparmio energia: screen saver**

1. Cerca Schermata **di blocco e** apri Impostazioni schermata di **blocco.**

2. Configura **le impostazioni di timeout dello** schermo e le impostazioni dello screen **saver** in base alle tue preferenze. I valori predefiniti consigliati sono:

   - Screen saver to (None) or a screen saver of your choice.
   - Attendere fino a 15 minuti.
   - Alla ripresa, visualizzare la schermata di accesso.


**Gestione risparmio energia: Criteri di gruppo**

Prima di eseguire la procedura seguente, rivolgersi al reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S dai criteri di gestione del risparmio energia globali. Alcune impostazioni di gestione del risparmio energia possono disabilitare la funzione di rilevamento della presenza.

1. Cercare **Software Center e** aprirlo.

2. Selezionare **Opzioni**.

3. Espandere Gestione **risparmio energia** e selezionare Non applicare le impostazioni di risparmio energia dal reparto IT **al computer.**

   ![Impostazioni software.](images/soft-cntr.png)

### <a name="storage-sense"></a>Sensore memoria

Il Surface Hub 2 ha un SSD da 128 GB per l'archiviazione locale, quindi è necessario considerare l'uso di misure di salvataggio dello spazio di archiviazione durante il normale utilizzo.  Per configurare Archiviazione Sense:

1.  Cercare le **impostazioni di archiviazione**, che si trova in Impostazioni di **sistema**.

2.  In **Impostazioni**selezionare **Attiva senso di archiviazione** per aprire la pagina **Archiviazione** impostazioni.

3.  Attivare Archiviazione sense su **On.**

4.  Seleziona **Configura Archiviazione Sense o eseguilo** subito e configura le impostazioni per mantenere i file online il più possibile (a causa di spazio su disco limitato).

Impostazioni consigliate:

- Eseguire Archiviazione Sense = Ogni giorno.
- Eliminare i file temporanei che le app non usano = Ogni 14 giorni (almeno).
- Elimina i file nella cartella Download se sono presenti da più di 30 giorni.
- OneDrive: il contenuto diventerà solo online se non aperto per più di = 30 giorni.

### <a name="tablet-mode"></a>Modalità tablet

Attivare la modalità Tablet se lo si desidera per esigenze di accessibilità.


### <a name="sound-settings"></a>Impostazioni audio

1. Cerca impostazioni **suoni e** apri questa pagina.

2. Seleziona **Pannello di controllo audio** a destra e seleziona la **scheda** Suoni.

3. In **Eventi programma** imposta Device **Connessione** e Device **Disconnect** su **None.**

### <a name="silence-notifications"></a>Notifiche silenziose

1. Cerca **l'assistente stato attivo** e apri questa pagina.

2. Selezionare **Solo sveglie**. In questo modo si evitano riquadri a comparsa di notifica costanti.

### <a name="disk-cleanup"></a>Pulizia disco

1. Cerca Pulizia **disco e** apri questa app.

2. In **File da eliminare**selezionare i file che si desidera eliminare. 

3. Selezionare anche **Pulisci file di sistema**.

## <a name="complete-and-verify"></a>Completare e verificare

1. Cercare e installare tutti gli Windows aggiornamenti.

2. Aggiornare Criteri di gruppo.

   1. Al prompt dei comandi con privilegi elevati immettere **gpupdate /force /boot /wait:0**.
   
3. Riavvia il dispositivo.

4. Verificare le app della barra delle applicazioni.

   - Connessione App
   - Icona Blocca
   - Cattura e annota
   - Teams (se applicabile)
   - Office App (se applicabile)
   - Surface App
   - Lavagna
    
5. Verificare il rilevamento della presenza.

   - Il rilevamento della presenza sarà un'icona verde nella barra delle applicazioni.
    
6. Verifica che la proiettazione su questo PC sia abilitata con l Connessione app. Dopo aver configurato **Project impostazioni del PC,** esegui l'app Connessione app almeno una volta. In seguito, l Connessione App non deve essere in esecuzione per poter eseguire la Surface Hub.

7. Verificare le impostazioni di alimentazione e sospensione.

    - Screen saver: 15 minuti, impostato su (nessuno), Mystify o Blank; verificare che la casella di controllo per richiedere la password sia selezionata.
    - Schermo: **disattivare dopo 2 ore**.
    - PC:  **spegni dopo 4 ore**.
    
8. Verificare Windows Hello che funzioni.

9. Verificare che la sincronizzazione delle impostazioni sia disabilitata.

10. Verificare le app di avvio.

> [!TIP]
> Dopo aver installato e configurato Windows 10, il Surface Hub 2S può essere gestito come qualsiasi altro Windows 10 dispositivo.

## <a name="related-topics"></a>Argomenti correlati

<a href="surface-hub-2s-migrate-os.md" target="_blank"> Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2</a>

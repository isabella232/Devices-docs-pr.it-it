---
title: Configurare Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo include suggerimenti per garantire la migliore esperienza quando si usa un computer con tocco su schermo di grandi dimensioni e penna personalizzato.
keywords: Surface Hub, Windows 10, desktop, installare, configurazione
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
ms.openlocfilehash: 076d29462ffb949492291e120bcdad538f4287ec
ms.sourcegitcommit: e859374f90d640a5cd4be1c8dcc823bcd537ebdc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "11393596"
---
# <a name="configure-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Configurare Windows 10 Pro o Enterprise in Surface Hub 2

Dopo aver completato il processo di installazione della migrazione a Windows 10 Pro o Enterprise, puoi eseguire la procedura seguente per configurare le app e le impostazioni nel dispositivo Surface Hub 2. Questi passaggi sono consigliati per garantire la migliore esperienza quando si usa questo computer personalizzato con tocco su schermo grande e penna.

Durante l'esecuzione di questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.

## <a name="configure-system-settings"></a>Configurare le impostazioni di sistema

1. Accedi con un account con privilegi di amministratore locale nel dispositivo.  

    - Nei dispositivi aggiunti ad Azure AD, l'utente che esegue l'aggiunta ad Azure AD viene aggiunto automaticamente al gruppo di amministratori locali. Gli amministratori globali di Azure AD e gli amministratori dei dispositivi Azure AD <a href="https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin" target="_blank"> sono anche amministratori </a> locali. 
    
    - È possibile digitare **net localgroup administrators al** prompt dei comandi per elencare gli account con diritti di amministratore locale.
    
2. Rinomina il dispositivo usando un nome descrittivo, ad esempio **nomeutente-SHub-Desktop.**

3. Seleziona **Start**  >  **Settings**  >  **Accounts**  >  **Sync your settings** and turn Sync **settings** off. 

    - Le impostazioni usate qui sono progettate per abilitare la migliore esperienza di tocco su schermo grande e pertanto potresti non voler sincronizzare altri dispositivi.
    
4. Riavvia il dispositivo.

## <a name="enable-the-touch-keyboard-and-touchpad"></a>Abilitare la tastiera virtuale e il touchpad

1. Seleziona **Start**  >  **Settings**  >  **Devices**  >  **Typing** e turn **Show the touch keyboard when not in tablet mode and there's no keyboard attached** on.

2. Tocca e tieni premuto o fai clic con il pulsante destro del mouse sulla barra delle applicazioni e quindi scegli Mostra pulsante **tastiera virtuale** e Mostra **pulsante touchpad.** 

    - La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad virtuale consente selezioni precise, descrizioni dello schermo al passaggio del mouse o come alternativa al tocco e alla sospensione per fare clic con il pulsante destro del mouse. 
    
    - Vedi l'esempio seguente.

      ![Impostazioni di tocco](images/touch.png)

3. Configura la tastiera virtuale su QWERTY e mobile.

    1. Seleziona **l'icona Tastiera** sulla barra delle applicazioni per visualizzare la tastiera virtuale.
    
    1. Sulla tastiera virtuale seleziona l'icona della tastiera nell'angolo superiore sinistro per aprire le impostazioni della tastiera.
    
    1. Selezionare l'ultimo tipo di tastiera nella riga superiore per abilitare QWERTY e l'ultima opzione nella seconda riga per abilitare la virgola mobile, operazione molto utile su questo grande schermo. Vedere gli esempi seguenti.

       ![Impostazioni della tastiera](images/kbd.png)
 
4. Configurare le impostazioni della tastiera soft.

    1. Seleziona **l'icona Impostazioni** sulla tastiera virtuale o cerca e apri impostazioni **di digitazione.**
    
       ![impostazioni della tastiera soft](images/sh2-softkeyboard.png)

    1. Abilita tutte le opzioni in Controllo ortografia, digitazione e tastiera virtuale.


L'esempio seguente mostra il trackpad, utile per spostarsi e selezionare le opzioni. La tastiera su schermo viene usata per eseguire ricerche in Microsoft Store:

![Uso del trackpad](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a>Configurare Bluetooth tastiera e mouse (facoltativo)

Connetti una tastiera e un mouse se usi il dispositivo come dispositivo Windows principale o lo usi spesso per il lavoro di digitazione o precisione.

Se il dispositivo Surface Hub è vicino a un PC, puoi usare il mouse senza bordi per spostarsi facilmente tra <a href="https://aka.ms/mm" target="_blank"> Surface Hub e il </a> PC. Per altre informazioni, vedi <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> il download microsoft da The Garage: Mouse senza bordi. </a>

## <a name="example-of-taskbar-layout"></a>Esempio di layout della barra delle applicazioni

Dopo aver completato i passaggi seguenti per configurare Surface Hub 2 per Windows 10 Professional o Enterprise, ti consigliamo di usare l'aggiunta delle applicazioni più usate alla barra delle applicazioni per un avvio rapido con un solo tocco di ogni applicazione. Di seguito è riportato un esempio dell'aspetto della barra delle applicazioni:

 ![Layout della barra delle applicazioni](images/taskblyt.png)
### <a name="update-installed-apps"></a>Aggiornare le app installate

Per aggiornare tutte le app dello Store installate:

1. Apri l'app di Microsoft Store e seleziona **i puntini** di sospensione Vedi altri puntini di sospensione nell'angolo in alto a destra.
2. Seleziona **Download e aggiornamenti.**
3. Selezionare **Ottieni aggiornamenti**

### <a name="scan-for-and-install-all-windows-updates"></a>Cercare e installare tutti gli aggiornamenti di Windows
Dopo la migrazione a Windows 10 Professional o Windows 10 Enterprise, potrebbero essere disponibili aggiornamenti di manutenzione e funzionalità da installare. 

- Vai a **Impostazioni**  >  **aggiornamento & sicurezza >** e quindi seleziona Verifica disponibilità **aggiornamenti.**
- Se sono presenti aggiornamenti, installarli, riavviarli e quindi ripetere il processo fino a quando non viene visualizzata la notifica seguente:

> [!div class="mx-imgBorder"]
> ![Notifica "Sei aggiornato" di Windows Update](images/wustatus.png)


## <a name="onedrive-for-business"></a>OneDrive for Business

Usare <a href="https://docs.microsoft.com/onedrive/onedrive" target="_blank"> OneDrive for Business </a> per condividere facilmente strumenti, log e altri file tra tutti i dispositivi di lavoro.

- OneDrive consente di condividere i file di lavoro tra laptop, Surface Hub Desktop e dispositivi mobili gestiti da Intune. I file possono essere modificati su qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.

- Considerando le dimensioni del dispositivo Surface Hub SSD (128 GB), se si configura OneDrive nel dispositivo desktop Surface Hub, assicurarsi che la configurazione predefinita sia mantenere i file online e scaricare i file mentre vengono utilizzati.

Per configurare OneDrive per il download **** dei file solo quando necessario, impostare File su richiesta su Risparmiare spazio e scaricare i file **mentre vengono utilizzati.** Per altre informazioni, vedi <a href="https://docs.microsoft.com/onedrive/files-on-demand-windows" target="_blank"> Eseguire query e impostare gli stati file su richiesta in </a> Windows.

![Impostazioni di OneDrive](images/onedrive.png)

> [!NOTE]
> You can also repeat these steps to configure a personal OneDrive but be sure to conserve drive space and only download files as you need them.

## <a name="sharepoint-and-teams"></a>SharePoint e Teams

I file di SharePoint e del Canale di Teams possono anche essere sincronizzati localmente con i dispositivi desktop, ad esempio laptop e Surface Hub, usando il motore di sincronizzazione di OneDrive.

Per sincronizzare i file aziendali interni con l'unità locale con l'app di sincronizzazione di OneDrive:

1. Passare a un sito di SharePoint e passare alla directory dei documenti di primo livello per i file che si desidera visualizzare o modificare dal dispositivo locale.

2. Fare clic sul **pulsante Sincronizza** nella parte superiore della barra multifunzione di SharePoint.

3. Select on **Open** on the popup **This site is trying to open Microsoft OneDrive.**

4. Verificare che i file di SharePoint siano sincronizzati con l'unità locale selezionando l'icona di OneDrive nella parte inferiore destra della barra delle applicazioni.

5. Verificare che la configurazione sia impostata per mantenere i file online e scaricarli solo quando vengono utilizzati:

    1. Apri Esplora file.
    
    2. Passare al nome di SharePoint e fare clic con il pulsante destro del mouse. ad esempio, **Contoso \ \<SharePoint Document Folder Name\> **.
    
    3. Selezionare **Libera spazio.**
    
    4. Nella colonna Stato verrà visualizzato lo stato di file e cartelle. Per ulteriori informazioni, vedere <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sincronizzare i file di SharePoint con il client di sincronizzazione di OneDrive. </a>
    
6. I file del canale di Teams vengono archiviati nei siti di SharePoint, con tutte le stesse funzionalità dei documenti di SharePoint, tra cui la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali. Per sincronizzare i file del canale di Teams:

    1. Passare al Canale di Teams di interesse e selezionare la **scheda File** nella parte superiore. Selezionare quindi **Sincronizza.** The files will start synchronizing and will be visible in File Explorer at **Desktop \ Contoso \ \<name of the Teams Channel\> **.
    
    2. Utilizzare la stessa procedura utilizzata per sincronizzare i siti di SharePoint per mantenere i file nel cloud e scaricarli solo quando vengono usati, toccando e tenendo premuto o facendo clic con il pulsante destro del mouse in Esplora file nel nome del canale di Teams e selezionando Libera **spazio.**

## <a name="surface-hub-pen-settings"></a>Impostazioni della penna di Surface Hub

**Associare la Bluetooth penna di Surface Hub**

Associa la penna per mantenere aggiornato il firmware della penna, impostare i tasti di scelta rapida della penna e ottenere informazioni sulla carica della batteria nella pagina delle impostazioni del dispositivo Bluetooth o nell'app Surface:

1. Seleziona **Start**  >  **Settings**  >  **Devices**.

2. Seleziona **Aggiungi Bluetooth o altro dispositivo.**

3. Scegliere **Bluetooth**.

4. Rimuovi il pulsante di coda della penna e scossa per scollegare la connessione della batteria.

5. Rimutare il tappo e tenere premuto il tappo fino a quando il LED di associazione lampeggia.

6. Nelle impostazioni del dispositivo Surface Hub Bluetooth scegliere **Penna per Surface Hub 2.**

7. Completare l'operazione di associazione. 

8. Se l'associazione non riesce, puoi tentare di associare di nuovo la penna. Se non funziona, puoi verificare se la batteria è carica verificando che la penna funzioni nell'applicazione Whiteboard. In caso contrario, sostituisci la batteria e quindi prova ad associare di nuovo la penna. Se necessario, riavviare il dispositivo e riprovare.

**Impostare i tasti di scelta rapida della penna** La penna di Surface Hub ha un pulsante di scelta rapida a volte definito "clic di coda". La configurazione dei tasti di scelta rapida richiede la prima associazione della penna, come descritto in precedenza.

1. Cerca Penna e seleziona Le impostazioni **di & windows ink.**

2. Nella parte inferiore della pagina seleziona i tasti di scelta rapida della penna che apre la finestra di dialogo, illustrata di seguito:

   ![Tasti di scelta rapida della penna](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a>Configurazione della fotocamera

Puoi montare la fotocamera nella parte superiore o su entrambi i lati del dispositivo. Monta la fotocamera in una posizione per ottimizzare l'angolo della fotocamera se utilizzi l'hub con un supporto desktop invece di un carrello o se sei vicino all'Hub. La fotocamera non ruota automaticamente, quindi devi avere un tasto esadecimale di 2 mm per ruotare manualmente la fotocamera. 

Per altre informazioni su come montare la fotocamera e ruotarla manualmente, vedi l'orientamento dell'obiettivo della <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> fotocamera di Surface Hub 2S. </a>

## <a name="windows-hello-configuration"></a>Configurazione di Windows Hello

Surface Hub 2S che esegue Windows 10 Enterprise consente la famiglia completa di applicazioni desktop Win32 e le opzioni biometriche di Windows Hello. L'accessorio lettore di impronta digitale di Surface Hub 2 può essere collegato a qualsiasi porta USB-C nel dispositivo. 

Per ordinare un lettore di impronta digitale di Surface Hub 2 o visualizzare le specifiche tecniche, vedi (surface-hub-2-essential-add-ons.md" target="_blank">Componenti aggiuntivi Essential per Windows 10 Pro ed Enterprise in Surface Hub </a> 2. 

Dopo aver inserito il lettore di impronta digitale, seleziona **Start**  >  **Settings**  >  **Accounts**  >  **Sign-in options**Windows Hello  >  **Fingerprint** per registrare l'impronta digitale.

Usa un dispositivo certificato Windows Hello per il riconoscimento dei volto. La fotocamera Surface Hub 2S non supporta il riconoscimento dei facciali di Windows Hello.

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a>Abilitazione di un'icona di scelta rapida della schermata di blocco sulla barra delle applicazioni

Per aggiungere un'icona alla barra delle applicazioni che abilita il blocco dello schermo con un solo tocco, in modo analogo ai tasti di scelta rapida di Windows-L: 

1.  Toccare e tenere premuto o fare clic con il pulsante destro del mouse sul desktop, selezionare **Nuovo**  >  **collegamento**  >  **Sfoglia**  >  **desktop**  >  **OK**  >  **Avanti.**

1.  Specifica un nome per il collegamento, ad esempio **Blocca il PC,** e quindi seleziona **Fine.**

1.  Fai clic con il pulsante destro del mouse o tocca e tieni premuto il collegamento appena creato sul desktop e seleziona **Proprietà.** Nella scheda **Collegamento** immettere quanto segue nel campo **Destinazione:** **Rundll32.exe User32.dll,LockWorkStation**

1.  Seleziona il **pulsante Cambia** icona e passa a **C:\Windows\System32\imageres.dll** e seleziona un'icona da usare. 

    Vedi l'esempio seguente:

    ![Scegliere un'icona](images/lock.png)
    
1.  Selezionare **OK** per salvare il collegamento.

1.  Fai clic con il pulsante destro del mouse o tocca e tieni premuto il collegamento e seleziona **Aggiungi alla barra delle applicazioni.**

1. Dopo aver aggiunto il collegamento di blocco alla barra delle applicazioni, puoi eliminarlo dal desktop.

## <a name="applications"></a>Applicazioni


### <a name="microsoft-whiteboard"></a>Microsoft Whiteboard

Per installare Microsoft Whiteboard:

 - Seleziona **l'icona di Windows Ink Workspace** nell'angolo in basso a destra della barra delle applicazioni e scarica **Whiteboard.**
 
   ![Area di lavoro input penna](images/ink.png) 

In alternativa, puoi installare Whiteboard da Microsoft Store:

1. Apri l'app di Microsoft Store e cerca **Lavagna.**

2. Choose **No thanks** to sign in and use across devices.

3. Aggiungi Whiteboard alla barra delle applicazioni.

### <a name="surface-app"></a>App Surface

1. In Microsoft Store cerca **Surface.**

2. Impostare il **filtro Disponibile su** Tutti i **dispositivi.**

3. Installa l'app **Surface.** Dovrebbe essere la prima app elencata. Per installare l'app, potrebbe essere necessario associare l'account microsoft a Windows Store.

4. Aggiungi l'app **Surface** alla barra delle applicazioni.

### <a name="snip--sketch"></a>Cattura e annota

1. Apri **l'app Snip & Sketch** e aggiungila alla barra delle applicazioni.

2. Selezionare i puntini di sospensione nell'angolo superiore destro e quindi selezionare **Impostazioni.**

3. In **Impostazioni**attivare Copia **automatica negli Appunti,** Salva **e**Più **finestre** (facoltativo).

### <a name="microsoft-office"></a>Microsoft Office

1. Aprire il <a href="https://portal.office.com/account#installs" target="_blank"> portale di Office e installare le applicazioni </a> desiderate.

2. Aggiungere le applicazioni di Office desiderate alla barra delle applicazioni.

3. Se Outlook è installato, assicurarsi di impostare il file OST di Outlook in modo da salvare solo la cache delle ultime due settimane. Ciò ridurrà notevolmente l'utilizzo del disco e i tempi di installazione.

    - Seleziona **Impostazioni**  >  **account file** e seleziona il tuo account.
    
    - Selezionare **Modifica** e impostare il dispositivo di scorrimento per Usa **modalità cache** su 14 giorni.

### <a name="microsoft-teams"></a>Microsoft Teams

1. Scaricare e installare <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft </a> Teams.

2. Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).

3. Aggiungere Teams alla barra delle applicazioni.

4. Valutare la possibilità di ridurre le notifiche di Teams nel dispositivo per evitare distrazioni (facoltativo).

   ![Notifiche di Teams](images/teams.png)

### <a name="connect-app"></a>Connettere l'app

> [!IMPORTANT]
> In Windows 10 versione 2004 e successive, l'app Connetti per la proiezione wireless con Miracast non è installata per impostazione predefinita, ma è disponibile come funzionalità facoltativa. Se hai installato (o aggiornato) Windows versione 2004 o successiva, nella schermata Projecting to this PC potrebbe essere visualizzato quanto segue nelle impostazioni:

![Project to this PC](images/sh2-project.png) 


1. Per installare l'app dalla pagina delle impostazioni "Progetto in questo PC", seleziona **Funzionalità**facoltative Aggiungi una funzionalità e quindi installa l'app  >  **** **Schermo** wireless.

2. In **Alcuni dispositivi Windows e Android puoi proiettare su questo PC**quando dici che è ok, scegli:

    - **Disponibile ovunque** se il dispositivo non si trova in una rete aziendale.
    - In caso contrario, **scegliere Disponibile ovunque nelle reti protette.**
    
3. In **Chiedi di proiettare in questo PC**scegliere Solo la prima **volta.**

4. In **Richiedi PIN per l'associazione**scegliere **Mai.**

5. Per avviare l'app e aggiungere l'app alla barra delle applicazioni, cerca **Connetti.**

6. Apri l'app. Mentre l'app è aperta, fai clic con il pulsante destro del mouse sull'icona Connetti app sulla barra delle applicazioni e scegli **Aggiungi alla barra delle applicazioni.**

7. Chiudi quindi l'app Connetti. **Project su questo PC potrebbe** non funzionare a meno che l'app non sia stata eseguita almeno una volta.

Configurazione consigliata quando non si utilizza la rete aziendale:

![Impostazioni a casa](images/project1.png)

Configurazione consigliata nella rete aziendale:

![Impostazioni sul lavoro](images/project2.png)

### <a name="your-phone"></a>Il tuo telefono

**L'app Telefono** è installata per impostazione predefinita in Windows 10. Se non è presente, puoi installarlo anche da Windows Store.

Per informazioni sulla configurazione dell'app, vedi Come configurare il telefono in Windows 10 e sincronizzare i dati <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> tra PC e </a> telefono. Vedi anche <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> come risolvere i problemi comuni con l'app Telefono in Windows 10. </a>

###  <a name="fancy-zones"></a>Zone fantasiose


**Fancy Zones** fa parte di una raccolta di strumenti denominata <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys </a> su GitHub. È un ottimo modo per usare lo spazio sullo schermo in un dispositivo Surface Hub 2, offrendoti la possibilità di definire layout fissi sullo schermo ("aree") e quindi di selezionare l'app che verrà eseguita in ogni area. 


Il [wiki di PowerToys](https://github.com/microsoft/PowerToys/wiki) contiene istruzioni su come usare e personalizzare ogni strumento, tra cui [FancyZones.](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview) A livello elevato: dopo aver installato PowerToys, puoi selezionare o creare un layout personalizzato e quindi tenere premuto MAIUSC e trascinare o usare i tasti della tastiera per spostare un'app in esecuzione in aree specifiche. L'uso Bluetooth tastiera e mouse USB può essere utile oppure puoi usare la tastiera virtuale su schermo e il touchpad.

**Suggerimenti per Power Toys**
- Per ricevere notifiche tramite posta elettronica degli aggiornamenti delle versioni di PowerToys su GitHub, fai clic sul pulsante "registrazione" nella parte superiore della [pagina.](https://github.com/microsoft/PowerToys/releases)
- Una volta installato PowerToys, è possibile ricevere notifiche di Windows e/o scaricare e **** installare gli aggiornamenti più recenti configurando le impostazioni di PowerToys Per scaricare automaticamente gli aggiornamenti.
- Per accedere alle impostazioni di PowerToys, **** seleziona le app in esecuzione nella barra delle applicazioni e quindi fai clic con il pulsante destro del mouse o tieni premuta l'icona PowerToys fino a quando non viene visualizzato il menu. Seleziona "Impostazioni".
- Nella parte inferiore della pagina delle impostazioni di PowerToys attiva **il download automatico** degli aggiornamenti.
- Quando viene rilasciato un aggiornamento, viene visualizzata una notifica di Windows che consente di scegliere quando installare l'aggiornamento.


### <a name="edge-chromium-browser"></a>Browser Edge Chromium

Scaricare e installare il nuovo <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank"> browser Edge Chromium. </a>


### <a name="surface-hub-hardware-diagnostic-tool"></a>Strumento di diagnostica hardware di Surface Hub

Strumento <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> di diagnostica hardware di Surface Hub disponibile gratuitamente da Microsoft </a> Store. Lo strumento è progettato per assicurarti che il dispositivo Surface Hub funzioni al meglio. Contiene test per determinare se il firmware è aggiornato e configurato correttamente. I test interattivi consentono di verificare che le funzionalità essenziali funzionino come previsto. Se si verificano problemi, i risultati possono essere salvati e condivisi con il team di supporto di Surface Hub. Fai clic sul link per installarlo da Microsoft Store e quindi aggiungi l'applicazione alla barra delle applicazioni.

## <a name="additional-settings"></a>Impostazioni aggiuntive

### <a name="pen-tail-select-to-launch-whiteboard"></a>Selezione della coda della penna per avviare Whiteboard

1. Cerca Penna **e** seleziona Le impostazioni della penna **& di Windows Ink.**

2. Nella parte inferiore della pagina, in Scelte rapide **da** penna impostare **Seleziona una sola volta** su Microsoft **Whiteboard.** 

### <a name="power-management"></a>Risparmio energia

Sono disponibili diverse impostazioni di risparmio energia per ottenere la migliore esperienza con Windows 10 Pro o Enterprise in Surface Hub 2. Sono inclusi i timeout di schermo e pc e il modo in cui interagiscono con il rilevamento della presenza umana predefinito (Doppler), lo screen saver e la password di protezione e quindi, se appropriato, come superare le impostazioni di risparmio energia dei Criteri di gruppo destinate agli utenti di laptop/desktop.

Windows 10 Pro o Enterprise in Surface Hub 2 impedisce la sospensione dello schermo tramite tocco, mouse e tastiera, oltre al rilevamento dell'occupazione umana (Doppler) integrato. Il rilevamento dell'occupazione umana è abilitato per impostazione predefinita, ma, se lo si desidera, può essere disabilitato in UEFI attivando l'opzione del dispositivo nello strumento Configuratore UEFI di Surface come parte della migrazione iniziale oppure creando e applicando un pacchetto di configurazione UEFI successivo. 

**Risparmio energia: impostazioni di sospensione dello schermo e del PC**

1. Selezionare **Start**  >  **Settings**  >  **System**  >  **Power & sleep**.

2. Impostare il dispositivo di scorrimento della modalità risparmio energia **su Prestazioni ottimali.**

3. Configura i valori dello schermo e della sospensione in base alle tue preferenze, tenendo conto anche del rilevamento della presenza Doppler che riattiva il dispositivo quando viene rilevato movimento. Di conseguenza, come procedura consigliata, è consigliabile impostare Lo schermo su Disattiva dopo **2** ore e il PC su Spegnimento **dopo 4 ore.**

**Risparmio energia: screen saver**

1. Cercare la **schermata di blocco e** aprire le impostazioni della schermata di **blocco.**

2. Configurare **le impostazioni di timeout dello** schermo e le impostazioni dello screen **saver** in base alle proprie preferenze. I valori predefiniti consigliati sono:

   - Screen saver to (None) or a screen saver of your choice.
   - Attendere fino a 15 minuti.
   - Al ripristino, visualizzare la schermata di accesso.


**Risparmio energia: Criteri di gruppo**

Prima di eseguire la procedura seguente, rivolgersi al reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S dai criteri globali di risparmio energia. Alcune impostazioni di risparmio energia possono disabilitare la funzione di rilevamento della presenza.

1. Cercare **Software Center e** aprirlo.

2. Selezionare **Opzioni.**

3. Espandere Gestione **risparmio energia** e selezionare Non applicare le impostazioni di risparmio energia del reparto IT **al computer.**

   ![Impostazioni software](images/soft-cntr.png)

### <a name="storage-sense"></a>Sensore memoria

Surface Hub 2 dispone di un SSD da 128 GB per l'archiviazione locale, quindi è necessario considerare l'uso di misure di salvataggio dello spazio di archiviazione durante il normale utilizzo.  Per configurare Il senso di archiviazione:

1.  Cercare le **impostazioni di archiviazione,** disponibili in **Impostazioni di sistema.**

2.  In **Impostazioni**selezionare **Attiva senso di archiviazione per** aprire la pagina **Impostazioni** di archiviazione.

3.  Attivare Il senso di **archiviazione.**

4.  Selezionare **Configura Senso di archiviazione o eseguirlo ora** e configurare le impostazioni per mantenere i file online il più possibile (a causa di spazio su disco limitato).

Impostazioni consigliate:

- Eseguire Senso di archiviazione = Ogni giorno.
- Elimina i file temporanei che le mie app non usano = Ogni 14 giorni (almeno).
- Elimina i file nella cartella Download se sono presenti da più di 30 giorni.
- OneDrive: il contenuto diventerà online solo se non aperto per più di = 30 giorni.

### <a name="tablet-mode"></a>Modalità tablet

Attivare la modalità tablet se lo si desidera per esigenze di accessibilità.


### <a name="sound-settings"></a>Impostazioni audio

1. Cerca le **impostazioni dei suoni** e apri questa pagina.

2. Seleziona **Pannello di controllo audio** a destra e seleziona la **scheda** Suoni.

3. In **Eventi programma** imposta Device **Connect** e Device **Disconnect** su **None.**

### <a name="silence-notifications"></a>Notifiche di silenzio

1. Cerca **l'assistenza per lo stato** attivo e apri questa pagina.

2. Selezionare **Solo sveglie.** In questo modo si evitano riquadri a comparsa di notifica costanti.

### <a name="disk-cleanup"></a>Pulizia disco

1. Cerca Pulizia **disco e** apri questa app.

2. In **File da eliminare**selezionare i file che si desidera eliminare. 

3. Selezionare anche **Pulire i file di sistema.**

## <a name="complete-and-verify"></a>Completare e verificare

1. Cercare e installare tutti gli aggiornamenti di Windows.

2. Aggiornare Criteri di gruppo.

   1. In un prompt dei comandi con privilegi elevati, immettere **gpupdate /force /boot /wait:0**.
   
3. Riavvia il dispositivo.

4. Verificare le app della barra delle applicazioni.

   - Connect App
   - Icona Blocca
   - Cattura e annota
   - Teams (se applicabile)
   - App di Office (se applicabile)
   - Surface App
   - Lavagna
    
5. Verificare il rilevamento della presenza.

   - Il rilevamento della presenza sarà un'icona verde nella barra delle applicazioni.
    
6. Verifica che la proiettatura in questo PC sia abilitata con l'app Connetti. Dopo aver configurato  **Project in questo PC,** esegui l'app Connetti almeno una volta. Successivamente, non è necessario che l'app Connect sia in esecuzione per proiettare in Surface Hub.

7. Verificare le impostazioni di accensione e sospensione.

    - Screen saver: 15 minuti, impostato su (nessuno), Mystify o Blank; Verificare che la casella di controllo per richiedere la password sia selezionata.
    - Schermata: **disattivare dopo 2 ore.**
    - PC: **spegnimento dopo 4 ore.**
    
8. Verificare che Windows Hello funzioni.

9. Verificare che la sincronizzazione delle impostazioni sia disabilitata.

10. Verificare le app di avvio.

> [!TIP]
> Dopo l'installazione e la configurazione di Windows 10, Surface Hub 2S può essere gestito come qualsiasi altro dispositivo Windows 10.

## <a name="related-topics"></a>Argomenti correlati

<a href="surface-hub-2s-migrate-os.md" target="_blank"> Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2</a>

---
title: Configurare Pro o Enterprise Windows 10/11 in Surface Hub 2
description: Questo articolo include consigli per garantire l'esperienza migliore quando si usa un computer con tocco e penna su schermo grande personalizzato.
keywords: Surface Hub, Windows 10, desktop, installazione, configurazione
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
- Windows 10
- Windows 11
ms.openlocfilehash: 2b645ef580eda85a91bf282c8772c42c09cbb67d
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497769"
---
# <a name="configure-windows-1011-pro-or-enterprise-on-surface-hub-2"></a>Configurare Pro o Enterprise Windows 10/11 in Surface Hub 2

Dopo la migrazione a Windows 10/11 Pro o Enterprise, è possibile configurare app e impostazioni per garantire l'esperienza migliore usando questo computer personalizzato con tocco e penna su schermo grande.

Quando si eseguono questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.

## <a name="configure-system-settings"></a>Configurare le impostazioni di sistema

1. Accedere con un account con privilegi di amministratore locale nel dispositivo.  

    - L'utente che esegue l'aggiunta Azure AD in Azure AD dispositivi aggiunti viene aggiunto automaticamente al gruppo di amministratori locali.  Azure AD amministratori globali e gli amministratori dei dispositivi Azure AD sono <a href="/azure/active-directory/devices/assign-local-admin" target="_blank">anche amministratori</a> locali. 

    - È possibile digitare **net localgroup administrators** al prompt dei comandi per elencare gli account con diritti di amministratore locale.
    
2. Rinominare il dispositivo usando un nome descrittivo, ad esempio **username-SHub-Desktop**.

3. Selezionare **Start** >  **Impostazioni** >  **AccountSincronizza****** >  le impostazioni e disattiva **Impostazioni di sincronizzazione**. 

    - Le impostazioni usate qui hanno lo scopo di abilitare la migliore esperienza di tocco su schermo grande e quindi potresti non voler sincronizzare altri dispositivi.
    
4. Riavvia il dispositivo.

## <a name="enable-the-touch-keyboard-and-touchpad"></a>Abilitare la tastiera virtuale e il touchpad

1. Selezionare **Start** >  **Impostazioni** >  **DispositiviTipo** >  e attivare **Mostra la tastiera virtuale quando non è in modalità tablet e non è presente alcuna tastiera collegata**.****

2. Tocca e tieni premuto o fai clic con il pulsante destro del mouse sulla barra delle applicazioni e seleziona il **pulsante Mostra tastiera virtuale** e **mostra il pulsante Mostra touchpad**. 

    - La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad virtuale consente selezioni precise, suggerimenti sullo schermo al passaggio del mouse o come alternativa per toccare e tenere premuto per fare clic con il pulsante destro del mouse. 
    
    - Vedi l'esempio seguente.

      ![Impostazioni tocco.](images/touch.png)

3. Configurare la tastiera virtuale su QWERTY e mobile.

    1. Selezionare l'icona **Tastiera** sulla barra delle applicazioni per visualizzare la tastiera virtuale.
    
    1. Nella tastiera virtuale selezionare l'icona della tastiera nell'angolo superiore sinistro per aprire le impostazioni della tastiera.
    
    1. Selezionare il tipo di tastiera successivo all'ultimo nella riga superiore per abilitare QWERTY e l'ultima opzione nella seconda riga per abilitare la virgola mobile, utile su questo schermo di grandi dimensioni. Vedere gli esempi seguenti.

       ![Impostazioni della tastiera.](images/kbd.png)
 
4. Configurare le impostazioni della tastiera temporanea.

    1. Selezionare l'icona **Impostazioni** sulla tastiera virtuale oppure cercare e aprire **Impostazioni di digitazione**.
    
       ![impostazioni della tastiera soft.](images/sh2-softkeyboard.png)

    1. Abilitare tutte le opzioni in Controllo ortografia, Digitazione e Tastiera virtuale.


L'esempio seguente mostra il trackpad, utile per spostarsi e selezionare le opzioni. La tastiera su schermo viene usata per eseguire ricerche nella Microsoft Store:

![Uso del trackpad.](images/store.png)

## <a name="configure-bluetooth-keyboard-and-mouse-optional"></a>Configurare Bluetooth tastiera e mouse (facoltativo)

Connessione una tastiera e un mouse se si usa il dispositivo come dispositivo Windows principale o lo si usa spesso per la digitazione o il lavoro di precisione.

Se il dispositivo Surface Hub è vicino a un PC, è possibile usare <a href="https://aka.ms/mm" target="_blank"> Mouse senza bordi</a> per spostarsi facilmente tra il Surface Hub e il PC. Per altre informazioni, vedere <a href="https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/" target="_blank"> Download Microsoft da The Garage: Mouse without Borders. </a>

## <a name="example-of-taskbar-layout"></a>Esempio di layout della barra delle applicazioni

Dopo aver completato i passaggi seguenti per configurare o configurare il Surface Hub 2 per Windows 10/11 Pro o Enterprise, è consigliabile usare l'aggiunta delle applicazioni più usate alla barra delle applicazioni per un avvio rapido con un tocco di ogni applicazione. Di seguito è riportato un esempio dell'aspetto della barra delle applicazioni:

 ![Layout della barra delle applicazioni.](images/taskblyt.png)
### <a name="update-installed-apps"></a>Aggiornare le app installate

Per aggiornare tutte le app dello Store installate:

1. Aprire l'app Microsoft Store e selezionare i puntini di sospensione **Vedi altri** puntini di sospensione nell'angolo in alto a destra.
2. Selezionare **Download e aggiornamenti.**
3. Selezionare **Recupera aggiornamenti**

### <a name="scan-for-and-install-all-windows-updates"></a>Cercare e installare tutti gli aggiornamenti Windows

Dopo la migrazione, potrebbero essere disponibili aggiornamenti delle funzionalità e della manutenzione da installare. 

- Passare a **Impostazioni** >  **Aggiorna & security** > e selezionare **Controlla aggiornamenti**.
- Se sono presenti aggiornamenti, installarli, riavviarli e quindi ripetere il processo fino a quando non viene visualizzata la notifica seguente:

> [!div class="mx-imgBorder"]
> ![Windows Update notifica "Sei aggiornato".](images/wustatus.png)


## <a name="onedrive-for-business"></a>OneDrive for Business

Usare <a href="/onedrive/onedrive" target="_blank"> OneDrive for Business</a> per condividere facilmente strumenti, log e altri file tra tutti i dispositivi di lavoro.

- OneDrive consente di condividere i file di lavoro tra i portatili, Surface Hub Desktop e i dispositivi mobili gestiti da Intune. I file possono essere modificati in qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.

- Considerando le dimensioni del Surface Hub SSD (128 GB), se si configura OneDrive nel dispositivo desktop Surface Hub, assicurarsi che la configurazione predefinita sia mantenere i file online e scaricare i file mentre vengono usati.

Per configurare OneDrive per scaricare i file solo quando necessario, impostare l'impostazione **File su richiesta su** **Salva spazio e scaricare i file durante l'uso**. Per altre informazioni, vedere <a href="/onedrive/files-on-demand-windows" target="_blank"> Eseguire query e impostare gli stati di File su richiesta in Windows</a>.

![OneDrive impostazioni.](images/onedrive.png)

> [!NOTE]
> È anche possibile ripetere questi passaggi per configurare un OneDrive personale, ma assicurarsi di risparmiare spazio su disco e scaricare solo i file in base alle esigenze.

## <a name="sharepoint-and-teams"></a>SharePoint e Teams

SharePoint e Teams i file del canale possono anche essere sincronizzati in locale con i dispositivi desktop, ad esempio portatili e Surface Hub, usando il motore di sincronizzazione OneDrive.

Per sincronizzare i file aziendali interni con l'unità locale con l'app sincronizzazione OneDrive:

1. Passare a un sito SharePoint e passare alla directory del documento di primo livello per i file che si desidera visualizzare o modificare dal dispositivo locale.

2. Selezionare il pulsante **Sincronizza** nella parte superiore della barra multifunzione SharePoint.

3. Selezionare **Apri** nella finestra popup **Questo sito sta provando ad aprire Microsoft OneDrive**.

4. Verificare che i file SharePoint vengano sincronizzati con l'unità locale selezionando l'icona OneDrive nella parte inferiore destra della barra delle applicazioni.

5. Verificare che la configurazione sia impostata per mantenere i file online e scaricare i file solo quando vengono usati:

    1. Aprire Esplora file.
    
    2. Passare a e fare clic con il pulsante destro del mouse sul nome SharePoint, ad esempio **Contoso \ \<SharePoint Document Folder Name\>**.
    
    3. Selezionare **Libera spazio**.
    
    4. Nella colonna Stato verrà visualizzato lo stato di file e cartelle. Per altre informazioni, vedere <a href="https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd" target="_blank"> Sincronizzare i file SharePoint con il client</a> sincronizzazione OneDrive.
    
6. Teams file del canale vengono archiviati in siti SharePoint, con la stessa funzionalità SharePoint documento, inclusa la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali. Per sincronizzare Teams file di canale:

    1. Passare al canale Teams di interesse e selezionare la scheda **File** nella parte superiore. Selezionare quindi **Sincronizza**. I file inizieranno la sincronizzazione e saranno visibili in Esplora file in **Desktop \ Contoso \ \<name of the Teams Channel\>**.
    
    2. Usare la stessa procedura usata per sincronizzare i siti SharePoint per mantenere i file nel cloud e scaricarli solo quando vengono usati, toccando e tenendo premuto o facendo clic con il pulsante destro del mouse in Esplora file sul nome del canale Teams e quindi selezionando **Libera spazio**.

## <a name="surface-hub-pen-settings"></a>Surface Hub impostazioni della penna

**Associare la penna Bluetooth Surface Hub**

Associare la penna per mantenere aggiornato il firmware della penna, impostare i collegamenti della penna e ottenere informazioni sulla carica della batteria nella pagina delle impostazioni del dispositivo Bluetooth o nell'app Surface:

1. Selezionare **Start** >  **Impostazioni** >  **Dispositivi**.

2. Selezionare **Aggiungi Bluetooth o un altro dispositivo**.

3. Scegliere **Bluetooth**.

4. Rimuovere il pulsante della coda della penna e agitare per disconnettere la connessione della batteria.

5. Rimetti il cappuccio e premi e tieni premuto il cappuccio fino a quando il LED di associazione non lampeggia.

6. Nelle impostazioni Surface Hub Bluetooth scegliere **Surface Hub 2 penna**.

7. Completare l'operazione di associazione. 

8. Se l'associazione non riesce, provare di nuovo ad associare la penna. Se questo non funziona, è possibile verificare se la batteria è carica verificando che la penna funzioni nell'applicazione Lavagna. In caso contrario, sostituire la batteria e provare ad associare di nuovo la penna.  Se necessario, riavviare il dispositivo e riprovare.

**Impostare i tasti di scelta rapida per la penna** La penna Surface Hub ha un pulsante di scelta rapida a volte chiamato "clic finale". Per configurare i collegamenti è necessario associare prima la penna, come descritto in precedenza.

1. Cercare Penna e selezionare **Pen & Windows Ink settings (Pen & Windows Ink impostazioni**).

2. Nella parte inferiore della pagina selezionare Scelte rapide da penna che aprono la finestra di dialogo, come illustrato di seguito:

   ![Tasti di scelta rapida per la penna.](images/sh2-pen-shortcuts.png)

## <a name="camera-configuration"></a>Configurazione della fotocamera

È possibile montare la fotocamera nella parte superiore o su entrambi i lati del dispositivo. Monta la fotocamera in una posizione per ottimizzare l'angolo della fotocamera se usi l'hub con un supporto desktop anziché un carrello o sei vicino all'hub. La fotocamera non ruota automaticamente, quindi è necessario avere un tasto esadecimale di 2mm per ruotare manualmente la fotocamera. 

Per altre informazioni su come montare la fotocamera lateralmente e ruotarla manualmente, vedere <a href="https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation" target="_blank"> Surface Hub orientamento dell'obiettivo</a> della fotocamera 2S.

## <a name="windows-hello-configuration"></a>configurazione Windows Hello

Surface Hub 2S che esegue Windows 10/11 Pro o Enterprise consente la suite completa di applicazioni desktop Win32 e le opzioni di Windows Hello biometrica. L'accessorio lettore di impronte digitali Surface Hub 2 può essere collegato a qualsiasi porta USB-C del dispositivo. 

Per ordinare un lettore di impronte digitali Surface Hub 2 o visualizzare le specifiche tecniche, vedere (surface-hub-2-essential-add-ons.md" target="_blank">Componenti aggiuntivi essenziali per Windows 10 Pro e Enterprise in Surface Hub 2 </a>. 

Dopo aver inserito il lettore di impronte digitali, selezionare **Start** >  **Impostazioni** >  **AccountsOpzioni** >  >  **di accesso** **Windows Hello Impronta digitale** per registrare l'impronta digitale.

Usare un dispositivo certificato Windows Hello per il riconoscimento facciale. La fotocamera 2S Surface Hub non supporta Windows Hello riconoscimento facciale.

## <a name="enable-a-lock-screen-shortcut-icon-on-the-taskbar"></a>Abilitare un'icona di scelta rapida della schermata di blocco sulla barra delle applicazioni

Per aggiungere un'icona alla barra delle applicazioni che abilita il blocco dello schermo con un tocco simile al tasto di scelta rapida Windows-L: 

1.  Toccare e tenere premuto o fare clic con il pulsante destro **** del mouse sul desktop, selezionare NewShortcutBrowseDesktopOKNext**** > .**************** >  >  >  > 

1.  Specificare un nome per il collegamento, ad esempio **Blocca il PC**, e quindi selezionare **Fine**.

1.  Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento appena creato sul desktop e selezionare **Proprietà**. Nella scheda **Collegamento** immettere quanto segue nel campo **Destinazione** : **Rundll32.exe User32.dll,LockWorkStation**

1.  Selezionare il pulsante **Cambia icona** e passare a **C:\Windows\System32\imageres.dll** e selezionare un'icona da usare. 

    Vedere l'esempio seguente:

    ![Scegliere un'icona.](images/lock.png)
    
1.  Selezionare **OK** per salvare il collegamento.

1.  Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento e selezionare **Aggiungi alla barra delle applicazioni**.

1. Dopo aver aggiunto il collegamento di blocco alla barra delle applicazioni, è possibile eliminarlo dal desktop.

## <a name="applications"></a>Applicazioni


### <a name="microsoft-whiteboard"></a>Microsoft Whiteboard

Per installare il Microsoft Whiteboard:

 - Selezionare l'icona **Area Windows Ink** in basso a destra della barra delle applicazioni e scaricare **Lavagna**.
 
   ![Area di lavoro Input penna.](images/ink.png) 

In alternativa, è possibile installare Lavagna dal Microsoft Store:

1. Aprire Microsoft Store'app e cercare **Lavagna**.

2. Scegliere **No grazie** all'accesso e all'uso tra dispositivi.

3. Aggiungere lavagna alla barra delle applicazioni.

### <a name="surface-app"></a>App Surface

1. Nel Microsoft Store cercare **Surface**.

2. Impostare il filtro **Disponibile su** **Tutti i dispositivi**.

3. Installare l'app **Surface** . Questa dovrebbe essere la prima app elencata. Potrebbe essere necessario associare l'account del servizio gestito allo Store per installare l'app.

4. Aggiungere l'app **Surface** alla barra delle applicazioni.

### <a name="snip--sketch"></a>Cattura e annota

1. Aprire l'app **Snip & Sketch** e aggiungerla alla barra delle applicazioni.

2. Selezionare i puntini di sospensione nell'angolo superiore destro e quindi selezionare **Impostazioni**.

3. In **Impostazioni** attivare **Copia automatica negli Appunti**, **Salva frammenti di** codice e **Più finestre** (facoltativo).

### <a name="microsoft-office"></a>Microsoft Office

1. Aprire il <a href="https://portal.office.com/account#installs" target="_blank"> portale</a> di Office e installare le applicazioni desiderate.

2. Aggiungere le applicazioni desiderate Office alla barra delle applicazioni.

3. Se Outlook è installato, assicurarsi di impostare l'ost Outlook per salvare solo la cache delle ultime due settimane. Ciò ridurrà notevolmente l'utilizzo del disco e il tempo di installazione.

    - Selezionare **FileAccount** >  **Impostazioni** e selezionare l'account.
    
    - Selezionare **Modifica** e impostare il dispositivo di scorrimento per **Usa modalità Exchange memorizzata nella cache** su 14 giorni.

### <a name="microsoft-teams"></a>Microsoft Teams

1. Scaricare e installare <a href="https://teams.microsoft.com/downloads" target="_blank"> Microsoft Teams </a>.

2. Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).

3. Aggiungere Teams alla barra delle applicazioni.

4. Valutare la possibilità di ridurre Teams notifiche nel dispositivo per evitare distrazioni (facoltativo).

   ![Teams notifiche.](images/teams.png)

### <a name="connect-app"></a>Connessione'app

> [!IMPORTANT]
> In Windows 10 versione 2004 e successive, l'app Connessione per la proiezione wireless con Miracast non è installata per impostazione predefinita, ma è disponibile come funzionalità facoltativa. Se è stata installata (o aggiornata a) Windows versione 2004 o successiva, è possibile che nella schermata Projecting to this PC (Proiezione in questo PC) siano disponibili le impostazioni seguenti:

![Project a questo PC.](images/sh2-project.png) 


1. Per installare l'app dalla pagina delle impostazioni "Proiezione in questo PC", selezionare **Funzionalità** >  **facoltativeAggiungi una funzionalità** e quindi installare l'app **Display wireless**.

2. In **Alcuni dispositivi Windows e Android possono essere proiettati su questo PC quando si dice che è OK**, scegliere:

    - **Disponibile ovunque** se il dispositivo non si trova in una rete aziendale.
    - In caso contrario, scegliere **Disponibile ovunque nelle reti sicure**.
    
3. In **Chiedi di proiettare in questo PC** scegliere **Solo prima volta**.

4. In **Richiedi PIN per l'associazione** scegliere **Mai**.

5. Per avviare quindi l'app e aggiungerla alla barra delle applicazioni, cercare **Connessione**.

6. Aprire l'app. Mentre l'app è aperta, fare clic con il pulsante destro del mouse sull'icona dell'app Connessione sulla barra delle applicazioni e selezionare **Aggiungi alla barra delle applicazioni**.

7. Chiudere quindi l'app Connessione. **Project a questo PC** potrebbero non funzionare a meno che l'app non sia stata eseguita almeno una volta.

Configurazione consigliata quando non si usa la rete aziendale:

![Impostazioni a casa.](images/project1.png)

Configurazione consigliata nella rete aziendale:

![Impostazioni al lavoro.](images/project2.png)

### <a name="your-phone"></a>Il tuo telefono

L'app **Your Telefono** viene installata per impostazione predefinita in Windows 10. Se non è presente, è anche possibile installarlo da Windows Store.

Per informazioni sulla configurazione dell'app, vedere <a href="https://www.windowscentral.com/how-set-your-phone-windows-10" target="_blank"> Come configurare il Telefono in Windows 10 e sincronizzare i dati tra PC e telefono</a>. Vedere <a href="https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10" target="_blank"> anche Come risolvere i problemi comuni con l'app Telefono in Windows 10</a>.

###  <a name="fancy-zones"></a>Zone di fantasia


**Fancy Zones** fa parte di una raccolta di strumenti denominata <a href="https://github.com/microsoft/PowerToys/releases" target="_blank"> PowerToys</a> in GitHub. È un ottimo modo per utilizzare lo schermo immobiliare su un Surface Hub 2, offrendo la possibilità di definire layout fissi sul tuo display ("zone") e quindi selezionare quale app verrà eseguita in ogni zona. 


Il [wiki PowerToys](https://github.com/microsoft/PowerToys/wiki) contiene istruzioni su come usare e personalizzare ogni strumento, inclusi [FancyZones](https://github.com/microsoft/PowerToys/wiki/FancyZones-Overview). A livello generale: dopo aver installato PowerToys, è possibile selezionare o creare un layout personalizzato e quindi tenere premuto il tasto MAIUSC e trascinare o usare i tasti di tastiera per spostare un'app in esecuzione in zone specifiche. L'uso di una tastiera e di un mouse USB o Bluetooth ti aiuterà in questo modo oppure puoi usare la tastiera virtuale e il touchpad sullo schermo.

**Suggerimenti per i giocattoli di potenza**
- Per ricevere notifiche tramite posta elettronica degli aggiornamenti della versione PowerToys in GitHub, fare clic sul pulsante "Iscrizione" nella parte superiore della [pagina](https://github.com/microsoft/PowerToys/releases).
- Dopo aver installato PowerToys, è possibile ricevere notifiche Windows e/o scaricare e installare gli aggiornamenti più recenti configurando le impostazioni di PowerToys **Scarica aggiornamenti automaticamente** su on.
- Per accedere alle impostazioni PowerToys, selezionare il carat **Up Running apps** sulla barra delle applicazioni, quindi fare clic con il pulsante destro del mouse o premere e tenere premuta l'icona PowerToys fino a quando non viene visualizzato il menu. Selezionare "Impostazioni".
- Nella parte inferiore della pagina delle impostazioni di PowerToys attivare **Scarica aggiornamenti automaticamente**.
- Quando un aggiornamento è stato rilasciato, verrà visualizzata una notifica di Windows che consente di scegliere quando installare l'aggiornamento.


### <a name="edge-chromium-browser"></a>Browser Chromium Edge

Scaricare e installare il nuovo <a href="https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL" target="_blank">browser</a> Chromium Edge.


### <a name="surface-hub-hardware-diagnostic-tool"></a>strumento di diagnostica hardware Surface Hub

Lo <a href="https://www.microsoft.com/p/surface-hub-hardware-diagnostic/9nblggh51f2g" target="_blank"> strumento</a> di diagnostica hardware Surface Hub disponibile gratuitamente dal Microsoft Store. Lo strumento è progettato per aiutarti a assicurarti che il tuo Surface Hub funzioni al meglio. Contiene test per determinare se il firmware è aggiornato e configurato correttamente. I test interattivi consentono di verificare che le funzionalità essenziali funzionino come previsto. Se si verificano problemi, i risultati possono essere salvati e condivisi con il team di supporto di Surface Hub. Fare clic sul collegamento per installarlo dal Microsoft Store e quindi aggiungere l'applicazione alla barra delle applicazioni.

## <a name="additional-settings"></a>Impostazioni aggiuntive

### <a name="pen-tail-select-to-launch-whiteboard"></a>Selezione della coda della penna per avviare Lavagna

1. Cercare **Penna** e selezionare **Pen & Windows Ink settings (Pen & Windows Ink impostazioni**).

2. Nella parte inferiore della pagina, in **Scelte rapide da penna** impostare **Seleziona una volta** su **Microsoft Whiteboard**. 

### <a name="power-management"></a>Risparmio energia

Sono disponibili diverse impostazioni di alimentazione per ottenere l'esperienza migliore usando Pro Windows 10/11 o Enterprise in Surface Hub 2. Sono inclusi i timeout dello schermo e del pc e il modo in cui interagiscono con il rilevamento della presenza umana predefinito (Doppler), lo screen saver e la protezione password e quindi, se appropriato, come by-pass impostazioni di alimentazione dei criteri di gruppo destinate agli utenti portatili/desktop.

Windows 10/11 Pro o Enterprise su Surface Hub 2 impedisce la sospensione dello schermo tramite tocco, mouse e tastiera, nonché il rilevamento dell'occupazione umana predefinito (Doppler). Il rilevamento dell'occupazione umana è abilitato per impostazione predefinita, ma se lo si desidera può essere disabilitato in UEFI attivando l'opzione del dispositivo nello strumento Surface UEFI Configurator come parte della migrazione iniziale o compilando e applicando un pacchetto di configurazione UEFI successivo. 

**Risparmio energia: impostazioni di sospensione dello schermo e del PC**

1. Selezionare **Start** >  **Impostazioni** >  **SystemPower** >  **& sospensione**.

2. Impostare il dispositivo di scorrimento della modalità di alimentazione su **Prestazioni ottimali**.

3. Configurare i valori dello schermo e della sospensione in base alle preferenze, tenendo anche conto del rilevamento della presenza Doppler che riattiva il dispositivo quando viene rilevato lo spostamento. Di conseguenza, come procedura consigliata, è consigliabile impostare Schermo su **Disattiva dopo 2 ore** e il PC per **disattivare dopo 4 ore.**

**Risparmio energia: screen saver**

1. Cercare **Schermata di blocco** e aprire **Impostazioni della schermata di blocco**.

2. Configurare **le impostazioni di timeout dello schermo** e **le impostazioni dello screen saver** in base alle proprie preferenze. I valori predefiniti consigliati sono:

   - Screen saver per (Nessuno) o uno screen saver di propria scelta.
   - Tempo di attesa fino a 15 minuti.
   - Alla ripresa, visualizzare la schermata di accesso.


**Risparmio energia: Criteri di gruppo**

Prima di eseguire la procedura seguente, rivolgersi al reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S dai criteri di risparmio energia globali. Alcune impostazioni di risparmio energia possono disabilitare la funzione di rilevamento della presenza.

1. Cercare **Software Center** e aprirlo.

2. Selezionare **Opzioni**.

3. Espandere **Risparmio energia**  e selezionare **Non applicare le impostazioni di risparmio energia dal reparto IT al computer**.

   ![Impostazioni software.](images/soft-cntr.png)

### <a name="storage-sense"></a>Sensore memoria

Il Surface Hub 2 ha un SSD da 128 GB per l'archiviazione locale, quindi è necessario prendere in considerazione l'uso di misure di risparmio di archiviazione durante il normale utilizzo.  Per configurare Archiviazione Sense:

1.  Cercare **le impostazioni di archiviazione** disponibili in **Impostazioni di sistema**.

2.  In **Impostazioni** selezionare **Attiva senso di archiviazione** per aprire la pagina delle impostazioni **di Archiviazione**.

3.  Attivare Archiviazione **Senso.**

4.  Selezionare **Configura Archiviazione Sense o eseguirlo ora** e configurare le impostazioni per mantenere i file online il più possibile (a causa dello spazio su disco limitato).

Impostazioni consigliate:

- Eseguire Archiviazione Sense = Ogni giorno.
- Eliminare i file temporanei che le app non usano = almeno ogni 14 giorni.
- Eliminare i file nella cartella Download se sono presenti da più di = 30 giorni.
- OneDrive: il contenuto diventerà online solo se non verrà aperto per più di = 30 giorni.

### <a name="tablet-mode"></a>Modalità tablet

Attivare la modalità Tablet se lo si desidera per esigenze di accessibilità.


### <a name="sound-settings"></a>Impostazioni audio

1. Cercare **Impostazioni suoni** e aprire questa pagina.

2. Selezionare **Audio Pannello di controllo** a destra e selezionare la scheda **Suoni**.

3. In **Eventi programma** impostare **Device Connessione** e **Device Disconnect (Disconnetti dispositivo)** su **None (Nessuno**).

### <a name="silence-notifications"></a>Notifiche di silenzio

1. Cercare **Focus Assist** e aprire questa pagina.

2. Selezionare **Solo allarmi**. In questo modo si eviteranno riquadri a comparsa di notifica costanti.

### <a name="disk-cleanup"></a>Pulizia disco

1. Cercare **Pulizia disco** e aprire l'app.

2. In **File da eliminare** selezionare i file da eliminare. 

3. Selezionare anche **Pulisci file di sistema**.

## <a name="complete-and-verify"></a>Completare e verificare

1. Cercare e installare tutti gli aggiornamenti Windows.

2. Aggiornare Criteri di gruppo.

   1. Al prompt dei comandi con privilegi elevati immettere **gpupdate /force /boot /wait:0**.
   
3. Riavvia il dispositivo.

4. Verificare le app della barra delle applicazioni.

   - app Connessione
   - Icona lucchetto
   - Cattura e annota
   - Teams (se applicabile)
   - Office Apps (se applicabile)
   - Surface App
   - Lavagna
    
5. Verificare il rilevamento della presenza.

   - Il rilevamento della presenza sarà un'icona verde nella barra degli strumenti di sistema.
    
6. Verificare che la proiezione nel PC sia abilitata con l'app Connessione. Dopo aver configurato **Project a queste impostazioni del PC**, eseguire l'app Connessione almeno una volta. Successivamente, non è necessario che l'app Connessione sia in esecuzione per eseguire il progetto per Surface Hub.

7. Verificare le impostazioni di alimentazione e sospensione.

    - Screen Saver: 15 minuti, impostato su (nessuno), Mystify o Blank; verificare che la casella di controllo per richiedere la password sia selezionata.
    - Schermata: **disattiva dopo 2 ore**.
    - PC:  **spegni dopo 4 ore**.
    
8. Verificare che Windows Hello funzioni.

9. Verificare che la sincronizzazione delle impostazioni sia disabilitata.

10. Verificare le app di avvio.

> [!TIP]
> Dopo aver installato e configurato Windows 10, il Surface Hub 2S può essere gestito come qualsiasi altro dispositivo Windows 10 o Windows 11.

## <a name="related-topics"></a>Argomenti correlati

<a href="surface-hub-2s-migrate-os.md" target="_blank"> Eseguire la migrazione a Pro o Enterprise Windows 10/11 il Surface Hub 2</a>

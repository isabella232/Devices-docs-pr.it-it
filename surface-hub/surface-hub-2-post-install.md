---
title: Configurare Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo include suggerimenti per garantire un'esperienza ottimale quando si usa un tocco di grande schermo personalizzato e un computer penna.
keywords: Surface Hub, Windows 10, desktop, installa, configurazione
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
ms.openlocfilehash: f6ea6324799981e57c36a11b33cf2e22ea80039e
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004478"
---
# Configurare Windows 10 Pro o Enterprise in Surface Hub 2

**Si applica a: Surface Hub 2S** 

Dopo aver completato il processo di installazione della migrazione a Windows 10 Pro o Enterprise, è possibile eseguire la procedura seguente per configurare le app e le impostazioni nel proprio Surface Hub 2. Questa procedura è consigliata per garantire un'esperienza ottimale quando si usa questo touch screen personalizzato di grandi dimensioni e un computer con penna.

Durante l'esecuzione di questi passaggi, potrebbe essere utile usare una tastiera e un mouse cablati o wireless.

## Configurare le impostazioni di sistema

1. Accedere con un account che disponga dei privilegi di amministratore locale nel dispositivo.  
    - Nei dispositivi di Azure AD Uniti l'utente che esegue il join di Azure AD viene automaticamente aggiunto al gruppo di amministratori locali. Gli amministratori globali di Azure AD e i dispositivi Azure AD sono [anche amministratori locali](https://docs.microsoft.com/azure/active-directory/devices/assign-local-admin). 
    - È possibile digitare **net localgroup Administrators** al prompt dei comandi per elencare gli account con diritti di amministratore locale.
2. Rinominare il dispositivo usando un nome descrittivo, ad esempio: **nomeutente-SHub-desktop**.
3. Selezionare **Avvia**  >  **Settings**  >  **account**impostazioni  >  **sincronizzare le impostazioni** e disattivare **le impostazioni di sincronizzazione** . 
    - Le impostazioni usate in questo articolo sono destinate a consentire l'esperienza di tocco di grande schermo migliore e quindi potresti non voler sincronizzare altri dispositivi.
4. Riavviare il dispositivo.

## Abilitare la tastiera virtuale e il touchpad

1. Toccare e tenere premuto o fare clic con il pulsante destro del mouse sulla barra delle applicazioni e quindi scegliere **Mostra pulsante tastiera virtuale** e **Mostra touchpad**. 
    - La tastiera virtuale è utile per l'input diretto dell'utente e il touchpad Virtual aiuta con selezioni precise, suggerimenti per lo schermo in bilico o come alternativa per toccare e tenere premuto il pulsante destro del mouse. 
    - Vedi l'esempio seguente.

     ![Impostazioni tocco](images/touch.png)

2. Configurare la tastiera virtuale su QWERTY e mobile.
    1. Selezionare l'icona della tastiera sulla barra delle applicazioni per visualizzare la tastiera virtuale.
    2. Nella tastiera virtuale selezionare l'icona della tastiera nell'angolo in alto a sinistra per aprire le impostazioni della tastiera.
    3. Selezionare il tipo di tastiera accanto a ultimo nella riga superiore per abilitare QWERTY e l'ultima opzione della seconda riga per abilitare il Floating, che è molto utile in questo grande schermo. Vedere gli esempi seguenti.

     ![Impostazioni della tastiera](images/kbd.png)

3. Configurare le impostazioni della tastiera morbida.
    1. Cercare e aprire **le impostazioni di digitazione** 
    2. Abilitare tutte le opzioni in controllo ortografia, digitazione e tastiera virtuale.


L'esempio seguente mostra il trackpad, utile per spostarsi e selezionare le opzioni. La tastiera su schermo viene usata per eseguire ricerche in Microsoft Store:

![Uso del trackpad](images/store.png)

## Configurare la tastiera e il mouse Bluetooth (facoltativo)

Connettere una tastiera e un mouse se si usa il dispositivo come dispositivo principale di Windows o si usa spesso per la digitazione o il lavoro di precisione.

Se il dispositivo Surface Hub è vicino a un PC, è possibile usare il [mouse senza bordi](https://aka.ms/mm) per passare facilmente tra il mozzo della superficie e il PC. Per altre informazioni, vedere [download Microsoft dal garage: mouse senza bordi](https://blogs.microsoft.com/ai/microsoft-download-from-the-garage-mouse-without-borders/).

## OneDrive for Business

Usare [OneDrive for business](https://docs.microsoft.com/onedrive/onedrive) per condividere facilmente strumenti, log e altri file tra tutti i dispositivi di lavoro.

- OneDrive consente di condividere i file di lavoro tra i computer portatili, Surface Hub desktop e i dispositivi mobili gestiti da Intune. I file possono essere modificati in qualsiasi dispositivo e tutti i dispositivi connessi alla rete verranno aggiornati con le modifiche.
- Considerando le dimensioni di Surface Hub SSD (128GB), se si configura OneDrive nel dispositivo desktop Surface Hub, verificare che la configurazione predefinita contenga i file online e scarichi i file durante l'uso.

Per configurare OneDrive per il download dei file solo quando necessario, impostare l'impostazione **file su richiesta** per **risparmiare spazio e scaricare i file durante l'uso**. Per altre informazioni, vedere [query e impostare gli Stati su richiesta di file in Windows](https://docs.microsoft.com/onedrive/files-on-demand-windows).

![Impostazioni di OneDrive](images/onedrive.png)

> [!NOTE]
> Puoi anche ripetere questi passaggi per configurare un OneDrive personale, ma assicurati di risparmiare spazio su disco e scaricare i file solo quando necessario.

## SharePoint e teams

I file di canale di SharePoint e teams possono anche essere sincronizzati localmente con i dispositivi desktop, ad esempio laptop e Surface Hub, usando il motore di sincronizzazione di OneDrive.

Per sincronizzare i file aziendali interni con l'unità locale con l'app di sincronizzazione di OneDrive:

1. Passare a un sito di SharePoint e passare alla directory principale del documento per i file che si vogliono visualizzare o modificare dal dispositivo locale.
2. Selezionare il pulsante **Sincronizza** nella parte superiore della barra multifunzione di SharePoint.
3. Selezionare **Apri** nel popup **questo sito sta provando ad aprire Microsoft OneDrive**.
4. Verificare che i file di SharePoint vengano sincronizzati con l'unità locale selezionando l'icona OneDrive nell'angolo in basso a destra della barra delle applicazioni.
5. Verificare che la configurazione sia impostata in modo da conservare i file online e scaricare i file solo quando si usano:
    1. Aprire Esplora file.
    2. Passare a e fare clic con il pulsante destro del mouse su **Microsoft \ \<SharePoint Document Folder Name\> **.
    3. Selezionare **libera spazio**.
    4. La colonna stato visualizzerà lo stato di file e cartelle. Per altre informazioni, vedere [sincronizzare i file di SharePoint con il client di sincronizzazione di OneDrive](https://support.microsoft.com/office/sync-sharepoint-files-with-the-onedrive-sync-client-groove-exe-59b1de2b-519e-4d3a-8f45-51647cf291cd).
6. I file di canale di teams sono archiviati nei siti di SharePoint, con tutte le stesse funzionalità dei documenti di SharePoint, inclusa la cronologia delle versioni e la sincronizzazione con i dispositivi desktop locali. Per sincronizzare i file del canale teams:
    1. Passare al canale teams di interesse e selezionare nella scheda **file** nella parte superiore. Quindi seleziona **Sincronizza**. I file verranno avviati per la sincronizzazione e saranno visibili in Esplora file in **Desktop \ Microsoft \<name of the Teams Channel\> \ **.
    2. Usare la stessa procedura usata per sincronizzare i siti di SharePoint per mantenere i file nel cloud e scaricarli solo quando si usano, toccare e tenere premuto o fare clic con il pulsante destro del mouse in Esplora file nel nome del canale teams e quindi selezionare **libera spazio**.

## Associare la penna di Surface Hub

Per associare il dispositivo penna:

1. Selezionare **Avvia**  >  **Settings**  >  **dispositivi**di impostazioni.
2. Selezionare **Aggiungi Bluetooth o altro dispositivo**.
3. Scegliere **Bluetooth**.
4. Rimuovere il pulsante della coda della penna e agitare per scollegare il connettore della batteria.
5. Riposizionare il cappuccio e premere e tenere premuto il cappuccio finché non lampeggia il LED di associazione.
6. Nelle impostazioni di Surface Hub Bluetooth scegliere **Surface Hub 2 Pen**.
7. Completare l'operazione di associazione. 
8. Se l'associazione non riesce, provare a associare di nuovo la penna. Se necessario, riavviare il dispositivo e riprovare.

## Configurazione della videocamera

È possibile montare la videocamera nella parte superiore o su entrambi i lati del dispositivo. Montare la videocamera in una posizione per ottimizzare l'angolazione della fotocamera se si usa l'hub con uno stand desktop anziché un carrello o si è in prossimità dell'hub. La fotocamera non ruota automaticamente, quindi è necessario disporre di una chiave esadecimale da 2mm per ruotare manualmente la fotocamera. 

Per altre informazioni su come montare la videocamera e ruotarla manualmente, vedere orientamento dell'obiettivo della [fotocamera](https://support.microsoft.com/help/4509729/surface-hub-2s-camera-lens-orientation).

## Configurazione di Windows Hello

Surface Hub 2S con Windows 10 Enterprise consente la famiglia completa di applicazioni desktop Win32 e le opzioni biometriche di Windows Hello. L'accessorio lettore di impronte digitali Surface Hub 2 può essere collegato a qualsiasi porta USB-C del dispositivo. 

> <i>Il lettore di impronte digitali Surface Hub 2 sarà presto disponibile per l'acquisto. Verificare di nuovo in questa pagina per altre informazioni, incluso l'acquisto.</i>

Dopo aver inserito il lettore di impronte digitali **Start**, selezionare  >  **Settings**  >  **Accounts**  >  **Opzioni**di avvio per l'accesso agli account  >  di**Windows Hello Fingerprint** per registrare l'impronta digitale.

Usare un dispositivo certificato Windows Hello per il riconoscimento delle facce. La fotocamera di Surface Hub 2S non supporta il riconoscimento del volto di Windows Hello.

## Abilitare un'icona di collegamento alla schermata di blocco sulla barra delle applicazioni

Per aggiungere un'icona alla barra delle applicazioni che consente il blocco dello schermo con un tocco simile alla scelta rapida da tastiera Windows-L: 

1.  Toccare e tenere premuto o fare clic con il pulsante destro del mouse sul desktop, scegliere **nuovo**  >  **collegamento**  >  **Sfoglia**  >  **Desktop**  >  **OK**  >  **Avanti**.

1.  Specificare un nome per il collegamento, ad esempio **Blocca PC**e quindi selezionare **fine**.

1.  Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento appena creato sul desktop e scegliere **Proprietà**. Nella scheda **collegamento** immettere quanto segue nel campo di **destinazione** : **Rundll32.exe User32.dll, LockWorkStation**

1.  Selezionare il pulsante **Cambia icona** e passare a **C:\Windows\System32\imageres.dll** e selezionare un'icona da usare. 

    Vedi l'esempio seguente:

    ![Scegliere un'icona](images/lock.png)
    
1.  Selezionare **OK** per salvare il collegamento.

1.  Fare clic con il pulsante destro del mouse o toccare e tenere premuto il collegamento e selezionare **Aggiungi alla barra delle applicazioni**.

## Applicazioni

### Aggiornare le app installate

Per aggiornare tutte le app dello Store installate:

1. Aprire l'app Microsoft Store e selezionare la **visualizzazione altri** puntini di sospensione nell'angolo in alto a destra.
2. Selezionare **Download e aggiornamenti**.
2. Selezionare **Ottieni aggiornamenti**.

### Microsoft Whiteboard

Per installare la lavagna Microsoft:

 - Selezionare l'icona dell' **area di lavoro Windows Ink** nell'angolo inferiore destro della barra delle applicazioni e scaricare **lavagna**.
 
   ![Area di lavoro input penna](images/ink.png) 

In alternativa, è possibile installare lavagna da Microsoft Store:

1. Aprire l'app Microsoft Store e cercare **lavagna**.
2. Scegliere **No grazie** per accedere e usare i vari dispositivi.
3. Aggiungere la lavagna alla barra delle applicazioni.

### App Surface

1. In Microsoft Store cercare **Surface**.
2. Impostare il filtro **disponibile su** **tutti i dispositivi**.
3. Installare l'app **Surface** . Questa dovrebbe essere la prima app elencata. Potrebbe essere necessario associare il MSA allo Store per installare l'app.
4. Aggiungere l'app **Surface** alla barra delle applicazioni.

### Snip & sketch

1. Aprire l'app **Snip & sketch** e aggiungerla alla barra delle applicazioni.
2. Selezionare i puntini di sospensione nell'angolo in alto a destra e quindi selezionare **Impostazioni**.
3. In **Impostazioni**, attiva **copia automatica negli Appunti**, **Salva snip**e **più finestre** (facoltativo).

### Microsoft Office

1. Aprire il [portale di Office](https://portal.office.com/account#installs) e installare le applicazioni desiderate.
2. Bloccare le applicazioni di Office desiderate nella barra delle applicazioni.
3. Se Outlook è installato, assicurarsi di impostare Outlook OST per salvare solo la cache delle ultime due settimane. In questo modo si ridurrà notevolmente l'utilizzo del disco e il tempo di configurazione.
    - Selezionare **File**  >  **Impostazioni account** file e selezionare il proprio account.
    - Selezionare **Cambia** e impostare il dispositivo di scorrimento per **usare la modalità cache** per 14 giorni.

### Microsoft Teams

1. Scaricare e installare [Microsoft teams](https://teams.microsoft.com/downloads).
2. Configurare le impostazioni per l'avvio automatico dell'applicazione (facoltativo).
3. Aggiungere Team alla barra delle applicazioni.
4. Valutare la possibilità di ridurre le notifiche dei team sul dispositivo per evitare distrazioni (facoltativo).

  ![Notifiche di Teams](images/teams.png)

### App Connect

> [!IMPORTANT]
> In Windows 10 versione 2004 e successive l'app Connect per la proiezione wireless che usa Miracast non è installata per impostazione predefinita, ma è disponibile come caratteristica facoltativa. Per installare l'app, seleziona nelle **Settings**  >  **app**impostazioni le  >  **funzionalità facoltative**  >  **aggiungono una caratteristica** e quindi installa l'app di **visualizzazione wireless** .

1. Cercare **Connetti**.
2. Aprire l'app e quindi chiuderla (il**progetto in questo PC** potrebbe non funzionare a meno che l'app non sia stata eseguita almeno una volta).
3. Toccare e tenere premuto o fare clic con il pulsante destro del mouse sulla barra delle applicazioni.
4. Cercare **impostazioni di proiezione**.
5. In **alcuni dispositivi Windows e Android possono essere proiettati in questo PC quando si dice che è OK**, scegliere **disponibile ovunque** se il dispositivo non si trova in una rete aziendale. In caso contrario, è possibile scegliere **disponibile ovunque su reti sicure**.
6. In **ask to Project to this PC**scegliere **First time only**.
7. In **Richiedi PIN per l'associazione**scegliere **mai**.

Configurazione consigliata quando non è presente nella rete aziendale:

  ![Impostazioni in Home](images/project1.png)

Configurazione consigliata nella rete aziendale:

  ![Impostazioni sul lavoro](images/project2.png)

### Il tuo telefono

L'app **telefono** è installata per impostazione predefinita in Windows 10. Se non è presente, è possibile installarlo anche da Windows Store.

Per informazioni sulla configurazione dell'app, vedere [come configurare il telefono in Windows 10 e sincronizzare i dati tra il PC e il telefono](https://www.windowscentral.com/how-set-your-phone-windows-10). Vedi anche [come risolvere i problemi comuni con l'app telefono in Windows 10](https://www.windowscentral.com/how-fix-common-problems-your-phone-app-windows-10).

### Aree di fantasia Super

**Super-Fancy Zones** aiuta gli utenti a disporre Windows per massimizzare la proprietà dello schermo. È ora incluso in [PowerToys](https://github.com/microsoft/PowerToys/releases) su GitHub.

### Browser cromo Edge

Scaricare e installare il nuovo [browser cromo Edge](https://www.microsoft.com/en-us/edge?form=MY01BL&OCID=MY01BL).

## Impostazioni aggiuntive

### Coda di penna selezionare per avviare la lavagna

1. Cercare **penna** e selezionare **penna & impostazioni di Windows Ink**.
2. Nella parte inferiore della pagina, in **scelte rapide da tastiera** , impostare **Seleziona una volta** su **Microsoft whiteboard**. 

### Impostazioni di alimentazione e sospensione

1. Selezionare **Start**  >  **Settings**  >  **System**  >  **Power & Sleep**.
2. Impostare il dispositivo di scorrimento Power Mode per **ottenere prestazioni ottimali**.
3. Configurare i valori di schermata e Sleep in preferenza.

### Salvaschermo

1. Cercare la **schermata di blocco** e aprire **le impostazioni della schermata di blocco**.
2. Configurare le impostazioni di **timeout dello schermo** e **le impostazioni dello screensaver** per le preferenze.

### Sensore memoria

Surface Hub 2 ha un SSD 128GB per l'archiviazione locale, quindi è necessario considerare l'uso delle misure di salvataggio dello storage durante l'uso normale.  Per configurare il senso di archiviazione:

1.  Cercare **le impostazioni di archiviazione**, disponibili in **impostazioni di sistema**.
2.  In **Impostazioni**selezionare **attiva il senso di archiviazione** per aprire la pagina impostazioni di **archiviazione** .
3.  Attivare il senso di archiviazione **su**attivato.
4.  Selezionare **Configura il senso di archiviazione o eseguirlo ora** e configurare le impostazioni per conservare i file online il più possibile (a causa dello spazio di unità limitato).

Impostazioni consigliate:
- Eseguire l'archiviazione Sense = ogni giorno.
- Eliminare i file temporanei che le app non usano = ogni 14 giorni (almeno).
- Eliminare i file nella cartella download se sono presenti da oltre 30 giorni.
- OneDrive: il contenuto diventa online solo se non viene aperto per più di 30 giorni.

### Modalità tablet

Attivare la modalità tablet, se necessario per esigenze di accessibilità.

### Power Management

> [!NOTE]
> Prima di eseguire la procedura seguente, consultare il reparto IT per l'approvazione per escludere un dispositivo Surface Hub 2S da criteri globali di gestione dell'alimentazione. Alcune impostazioni di Power Management possono disabilitare la funzione rilevamento presenza.

1. Cercare **Centro software** e aprirlo.
2. Selezionare le **Opzioni** nel riquadro di spostamento.
3. Espandere la sezione **Power Management** e selezionare non **applicare le impostazioni di alimentazione dal reparto IT al computer in**uso.

   ![Impostazioni software](images/soft-cntr.png)

### Impostazioni audio

1. Cercare **le impostazioni audio** e aprire questa pagina.
2. Selezionare **Pannello di controllo audio** a destra e selezionare la scheda **suoni** .
3. In **eventi programma** imposta **dispositivo Connetti** e **Disconnetti dispositivo** su **nessuno**.

### Notifiche di tacitazione

1. Cercare l' **assistenza per lo stato attiva** e aprire questa pagina.
2. Selezionare **solo sveglie**. Verrà evitato il riquadri a comparsa di notifica costante.

### Pulizia disco

1. Cercare **pulizia disco** e aprire l'app.
2. In **file da eliminare**selezionare i file che si desidera eliminare. 
3. Selezionare anche **Pulisci file di sistema**.

## Completare e verificare

1. Cercare e installare tutti gli aggiornamenti di Windows.
2. Aggiornare i criteri di gruppo
    1. In un prompt dei comandi con privilegi elevati, immettere **gpupdate/force/boot/wait: 0**.
3. Riavviare il dispositivo.
4. Verificare le app della barra delle applicazioni.
    - App Connect
    - Icona Blocca
    - Snip & sketch
    - Teams (se applicabile)
    - App di Office (se applicabile)
    - App Surface
    - Lavagna
5. Verificare il rilevamento della presenza.
    - Il rilevamento della presenza sarà un'icona verde nella barra delle applicazioni
6. Verificare che la proiezione in questo PC sia abilitata con l'app Connect (l'applicazione non deve essere in corso prima della connessione).
7. Verificare le impostazioni di alimentazione e sospensione.
    - Salvaschermo: 15 minuti, impostato su (nessuno), mistificare o vuoto; casella di controllo per la richiesta di password selezionata
    - Schermo: 2 ore
    - PC: 4 ore
8. Verificare che Windows Hello funzioni.
9. Verificare le impostazioni di alimentazione.
10. Verificare la sincronizzazione le impostazioni sono disabilitate.
11. Verificare le app di avvio.

> [!TIP]
> Dopo l'installazione e la configurazione di Windows 10, l'hub di Surface 2S può essere gestito proprio come qualsiasi altro dispositivo Windows 10.

## Argomenti correlati

[Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2s-migrate-os.md)

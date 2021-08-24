---
title: Microsoft Surface Data Eraser (Surface)
description: Scopri in che modo lo strumento Microsoft Surface Data Eraser può aiutarti a cancellare in tutta sicurezza i dati dai dispositivi Surface.
ms.assetid: 8DD3F9FE-5458-4467-BE26-E9200341CF10
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: strumento, USB, dati, cancellare
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
audience: itpro
ms.date: 05/17/2021
ms.openlocfilehash: 292c20c9999d9f226f28daed87069c78b43fd4bf
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911191"
---
# <a name="microsoft-surface-data-eraser"></a>Microsoft Surface Data Eraser

Scopri in che modo lo strumento Microsoft Surface Data Eraser può aiutarti a cancellare in tutta sicurezza i dati dai dispositivi Surface.

[Microsoft Surface Data Eraser](https://www.microsoft.com/download/details.aspx?id=46703) è uno strumento che si avvia da una chiavetta USB e ti permette di eseguire una cancellazione sicura di tutti i dati da un dispositivo Surface compatibile. Una chiavetta USB di Microsoft Surface Data Eraser deve avere la funzionalità di avvio da USB. La chiavetta USB è facile da creare con la procedura guidata fornita, Microsoft Surface Data Eraser Wrapper, e facile da usare con una semplice interfaccia grafica, senza alcuna riga di comando. Per altre informazioni sulle funzionalità e sulle procedure di cancellazione dei dati usate da Microsoft durante il processo di assistenza per Surface, vedi [Proteggere i dati quando si invia Surface in assistenza](https://www.microsoft.com/surface/support/security-sign-in-and-accounts/data-wiping-policy).

>[!IMPORTANT]
>Microsoft Surface Data Eraser usa il comando di formato NVM Express (NVMe) per cancellare i dati delle autorizzazioni nella [pubblicazione speciale NIST 800-88 revisione 1](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf).

I dispositivi Surface compatibili includono:

- Surface Book (tutte le edizioni)
- Surface Go (tutte le edizioni)
- Surface Pro X (tutte le edizioni)
- Surface Laptop (tutte le edizioni)
- Surface Laptop Go
- Surface Studio (tutte le edizioni)
- Surface Pro 2 e versioni successive
- Surface 3
- Windows 10 Pro e Enterprise su Surface Hub 2

Ecco alcuni scenari in cui Microsoft Surface Data Eraser può essere utile:

- Preparare un dispositivo Surface da inviare per la riparazione.
- Rimuovere un dispositivo Surface da rimuovere. dall'uso aziendale o dell'organizzazione.
- Reimpieni un dispositivo Surface per l'uso in un nuovo reparto o per l'uso da parte di un nuovo utente.
- Procedura standard quando si esegue la ri-creazione di immagini per i dispositivi usati con dati sensibili.

>[!NOTE]
>I dispositivi di terze parti, i dispositivi Surface che eseguono Windows RT (inclusi Surface e Surface 2) e Surface Pro non sono compatibili con Microsoft Surface Data Eraser.

>[!NOTE]
>Poiché per l'esecuzione di Microsoft Surface Data Eraser è necessario poter eseguire l'avvio dall'unità USB, se il dispositivo non è configurato per l'avvio da USB o se non è in grado di avviarsi o eseguire attività POST correttamente, lo strumento Microsoft Surface Data Eraser non funzionerà.

>[!NOTE]
>Surface Data Eraser in Surface Studio e Surface Studio 2 può richiedere fino a 6 minuti per l'avvio in WinPE prima che possa verificarsi la cancellazione del disco.

## <a name="how-to-create-a-microsoft-surface-data-eraser-usb-stick"></a>Come creare una chiavetta USB di Microsoft Surface Data Eraser

Per creare una chiavetta USB di Microsoft Surface Data Eraser, installa prima di tutto lo strumento di installazione di Microsoft Surface Data Eraser dall'Area download Microsoft usando il link fornito all'inizio di questo articolo. Non è necessario un dispositivo Surface per *creare* la chiavetta USB. Dopo aver scaricato il file di installazione nel computer, segui questa procedura per installare lo strumento di creazione di Microsoft Surface Data Eraser:

1. Eseguire il DataEraserSetup.msi di installazione scaricato [dall'Area download Microsoft.](https://www.microsoft.com/download/details.aspx?id=46703)

2. Seleziona la casella di controllo per accettare le condizioni del contratto di licenza e quindi fai clic su **Install**.

3. Fai clic su **Finish** per chiudere la finestra di installazione di Microsoft Surface Data Eraser.

Dopo l'installazione dello strumento di creazione, segui questa procedura per creare una chiavetta USB di Microsoft Surface Data Eraser. Prima di iniziare questa procedura, verifica che al computer sia connessa una chiavetta USB 3.0 con almeno 4 GB di spazio.

1. Avvia Microsoft Surface Data Eraser dal menu Start o dalla schermata Start.

2. Fai clic su **Build** per avviare il processo di creazione dell'unità USB di Microsoft Surface Data Eraser.

3. Fai clic su **Start** per confermare che è connessa una chiavetta USB con almeno 4 GB di spazio, come illustrato nella figura 1.

   ![Avvia lo strumento Microsoft Surface Data Eraser.](images/dataeraser-start-tool.png "Start the Microsoft Surface Data Eraser tool")

   *Figura 1. Avvio dello strumento Microsoft Surface Data Eraser*
4. Scegli **x64** per la maggior parte dei dispositivi Surface o **ARM64** per Surface Pro X dalla pagina **Selezione** architettura, come illustrato nella figura 2. Seleziona **Continua**.

    ![Selezione dell'architettura.](images/dataeraser-arch.png "Architecture Selection")<br>
       *Figura 2. Selezionare l'architettura dei dispositivi*

5. Seleziona l'unità USB di tua scelta dalla pagina Selezione unità usb **thumb,** come illustrato nella figura 3, quindi fai clic su **Start** per avviare il processo di creazione usb. L'unità selezionata verrà formattata e tutti i dati presenti nell'unità andranno persi.

   >[!TIP]
   >Se il pulsante Start è disabilitato, controlla che l'unità rimovibile abbia una capacità totale di almeno 4 GB.
  
   ![Selezione dell'unità pollice USB.](images/dataeraser-usb-selection.png "USB thumb drive selection")

   *Figura 3. Selezione della chiavetta USB*

6. Al termine del processo di creazione, l'unità USB è stata formattata e tutti i file binari sono stati copiati nell'unità USB. Fai clic su **Success**.

7. Quando viene visualizzata la schermata **Congratulations**, puoi espellere e rimuovere la chiavetta USB. Questa chiavetta USB è ora pronta per essere inserita in un dispositivo Surface e usata per l'avvio e la cancellazione di tutti i dati nel dispositivo. Fare **clic su** Completa per completare il processo di creazione usb, come illustrato nella figura 4.

   ![Processo di creazione USB di Surface Data Eraser.](images/dataeraser-complete-process.png "Surface Data Eraser USB creation process")

   *Figura 4. Completamento del processo di creazione dell'unità USB di Microsoft Surface Data Eraser*

8. Fai clic su **X** per chiudere Microsoft Surface Data Eraser.

## <a name="how-to-use-a-microsoft-surface-data-eraser-usb-stick"></a>Come usare una chiavetta USB di Microsoft Surface Data Eraser

Dopo aver creato una chiavetta USB di Microsoft Surface Data Eraser, puoi avviare un dispositivo Surface supportato dalla chiavetta USB seguendo questa procedura:

1. Inserisci la chiavetta USB di avvio di Microsoft Surface Data Eraser nel dispositivo Surface supportato.

2. Avvia il dispositivo Surface dalla chiavetta USB di Microsoft Surface Data Eraser. Per avviare il dispositivo dalla chiavetta USB attieniti alla procedura seguente:

   a. Spegni il dispositivo Surface.
   b. Tieni premuto il pulsante di **riduzione del volume**.
   c. Premi e rilascia il pulsante di **alimentazione**.
   d. Rilascia il pulsante di **riduzione del volume**.

   >[!TIP]
   >Se il dispositivo non si avvia dalla chiavetta USB con questa procedura, è necessario attivare l'opzione **Enable Alternate Boot Sequence** nell'interfaccia UEFI di Surface. Per altre informazioni sulla configurazione di avvio UEFI di Surface, vedi [Gestire le impostazioni UEFI di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings).

3. Quando il dispositivo Surface viene avviato, viene visualizzato un file di testo **SoftwareLicenseTerms,** come illustrato nella figura 5.

   ![Avvio della chiavetta USB di Microsoft Surface Data Eraser.](images/data-eraser-3.png "Booting the Microsoft Surface Data Eraser USB stick")

   *Figura 5. Avvio dalla chiavetta USB di Microsoft Surface Data Eraser*

4. Leggi le condizioni di licenza software e quindi chiudi il file nel Blocco note.

5. Accetta o rifiuta le condizioni di licenza software selezionando **Accept** o **Decline**. Se intendi continuare, devi accettare le condizioni di licenza.

6. Lo script di Microsoft Surface Data Eraser rileva i dispositivi di archiviazione che sono presenti nel dispositivo Surface e visualizza i dettagli del dispositivo di archiviazione originale. Per continuare, premi **Y** (questa azione esegue Microsoft Surface Data Eraser e rimuove tutti i dati dal dispositivo di archiviazione) o premi **N** (questa azione arresta il dispositivo senza rimuovere i dati).

   >[!CAUTION]
   >Lo strumento Microsoft Surface Data Eraser eliminerà tutti i dati, inclusi i file del sistema operativo Windows necessari per l'avvio del dispositivo, in modo sicuro e irreversibile. Per avviare un dispositivo Surface che è stato cancellato con Microsoft Surface Data Eraser, è necessario innanzitutto reinstallare il sistema operativo Windows. Per rimuovere i dati da un dispositivo Surface senza rimuovere il sistema operativo Windows, è possibile utilizzare la funzione **Reimposta il PC**. Tuttavia, ciò non impedisce il ripristino dei dati con l'uso di funzionalità di ripristino dati e forensi. Per altre informazioni, vedi [Opzioni di ripristino in Windows 10](https://support.microsoft.com/help/12415/windows-10-recovery-options).

   ![Viene visualizzata la partizione da cancellare.](images/sda-fig5-erase.png "Partition to be erased is displayed")
  
   *Figura 6. La partizione da cui cancellare i dati viene visualizzata in Microsoft Surface Data Eraser*

7. Se hai premuto **Y** nel passaggio 6, a causa della natura distruttiva del processo di cancellazione dei dati, viene visualizzata un'altra finestra di dialogo in cui puoi confermare la scelta.

8. Fai clic sul pulsante **Yes** pulsante per continuare a cancellare i dati nel dispositivo Surface.

   >[!TIP]
   >Quando esegui Surface Data Eraser nell'unità USB di Surface Data Eraser, viene generato un file di log nella cartella **SurfaceDataEraserLogs**.

## <a name="changes-and-updates"></a>Modifiche e aggiornamenti

Microsoft Surface Data Eraser viene aggiornato periodicamente da Microsoft. Per ulteriori informazioni sulle modifiche apportate in ogni nuova versione, vedi quanto segue:

### <a name="3391390"></a>3.39.139.0

*Data di rilascio: 13 aprile 2021*

Questa versione di Surface Data Eraser include:

- Supporto per Surface Laptop 4

### <a name="2341390"></a>2.34.139.0

*Data di rilascio: 15 gennaio 2021*

Questa versione di Surface Data Eraser:

- Include correzioni di bug

### <a name="333139"></a>3.33.139

*Data di rilascio: 9 settembre 2020*

Questa versione di Surface Data Eraser include correzioni di bug e aggiunge il supporto per: 

- Ri-progettazione dell'architettura per ridurre la necessità di aggiornamento con le nuove versioni del prodotto
- Notifica disponibile per i nuovi aggiornamenti degli strumenti
- Aggiunte di telemetria
- Windows 10 Pro e Enterprise su Surface Hub 2

### <a name="330139"></a>3.30.139

*Data di rilascio: 11 maggio 2020*

Questa versione di Surface Data Eraser aggiunge il supporto per:

- Surface Book 3
- Surface Go 2
- Nuovo SSD in Surface Go

### <a name="328137"></a>3.28.137

*Data di rilascio: 11 novembre 2019*

Questa versione di Surface Data Eraser:

- Include correzioni di bug

### <a name="version-321137"></a>Versione 3.21.137

*Data di rilascio: 21 ottobre 2019*

Questa versione di Surface Data Eraser viene compilata per x86 e aggiunge il supporto per i dispositivi seguenti:

- Surface Pro 7, Surface Pro X e Surface Laptop 3

### <a name="version-32780"></a>Versione 3.2.78.0

*Data di rilascio: 4 dicembre 2018*

Questa versione di Surface Data Eraser:

- Include correzioni di bug

### <a name="version-32750"></a>Versione 3.2.75.0

*Data di rilascio: 12 novembre 2018*

Questa versione di Surface Data Eraser:

- Aggiunge supporto a Surface Studio 2
- Consente di risolvere i problemi relativi alla scheda SD

### <a name="version-32690"></a>Versione 3.2.69.0

*Data di rilascio: 12 ottobre 2018*

Questa versione di Surface Data Eraser aggiunge il supporto per gli elementi seguenti:

- Surface Pro 6
- Surface Laptop 2

### <a name="version-32680"></a>Versione 3.2.68.0

Questa versione di Microsoft Surface Data Eraser aggiunge il supporto per:

- Surface Go

### <a name="version-32580"></a>Versione 3.2.58.0

Questa versione di Microsoft Surface Data Eraser aggiunge il supporto per:

- Dispositivi di archiviazione aggiuntivi (unità) per Surface Pro e Surface Laptop dispositivi

### <a name="version-32460"></a>Versione 3.2.46.0

Questa versione di Microsoft Surface Data Eraser aggiunge il supporto per:

- Surface Pro con LTE Advanced

### <a name="version-32450"></a>Versione 3.2.45.0

Questa versione di Microsoft Surface Data Eraser aggiunge il supporto per:

- Surface Book 2
- Surface Pro da 1 TB

   >[!NOTE]
   >Surface Data Eraser v3.2.45.0 e versioni successive può essere utilizzato per ripristinare i dispositivi Surface Pro o Surface Laptop con l'opzione di memoria da 1 TB in uno scenario in cui il dispositivo mostra due volumi distinti da 512 GB o rileva errori durante il tentativo di distribuire o installare Windows 10. Vedi [Surface Pro modello 1796 e Surface Laptop da 1 TB mostrano due unità](https://support.microsoft.com/help/4046105/surface-pro-model-1796-and-surface-laptop-1tb-display-two-drives) per ulteriori informazioni.

### <a name="version-32360"></a>Versione 3.2.36.0

Questa versione di Microsoft Surface Data Eraser aggiunge il supporto per:

- Surface Pro
- Surface Laptop

>[!NOTE]
>Lo strumento di creazione dell'unità USB di Microsoft Surface Data Eraser non è in grado di funzionare su Windows 10 S. Per cancellare un Surface Laptop in cui è in esecuzione Windows 10 S, devi innanzitutto creare l'unità USB di Microsoft Surface Data Eraser in un altro computer con Windows 10 Pro o Windows 10 Enterprise.

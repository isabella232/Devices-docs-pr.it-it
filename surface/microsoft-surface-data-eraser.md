---
title: Microsoft Surface Data Eraser (Surface)
description: Lo strumento Microsoft Surface Data Eraser consente di cancellare in modo sicuro i dati dai dispositivi Surface.
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
ms.date: 10/06/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: e40c967003fc6dd40725e5015c01497eb3fa141a
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449649"
---
# <a name="microsoft-surface-data-eraser"></a>Microsoft Surface Data Eraser

Scopri in che modo lo strumento Microsoft Surface Data Eraser può aiutarti a cancellare in tutta sicurezza i dati dai dispositivi Surface.

[Microsoft Surface Data Eraser](https://www.microsoft.com/download/details.aspx?id=46703) è uno strumento che si avvia da una chiavetta USB e ti permette di eseguire una cancellazione sicura di tutti i dati da un dispositivo Surface compatibile. Una chiavetta USB di Microsoft Surface Data Eraser deve avere la funzionalità di avvio da USB. Per altre informazioni sulle funzionalità e sulle procedure di cancellazione dei dati usate da Microsoft durante il processo di assistenza per Surface, vedi [Proteggere i dati quando si invia Surface in assistenza](https://www.microsoft.com/surface/support/security-sign-in-and-accounts/data-wiping-policy).

>[!IMPORTANT]
>Microsoft Surface Data Eraser usa il comando di formato NVM Express (NVMe) per cancellare i dati delle autorizzazioni nella [pubblicazione speciale NIST 800-88 revisione 1](http://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-88r1.pdf).

I dispositivi Surface compatibili includono:

- Surface Laptop Studio
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
- Rimuovere le autorizzazioni di un dispositivo Surface dall'uso aziendale o dell'organizzazione.
- Reimpieni un dispositivo Surface per un nuovo utente.
- Reimage devices containing sensitive data.

## <a name="how-to-create-a-microsoft-surface-data-eraser-usb-stick"></a>Come creare una chiavetta USB di Microsoft Surface Data Eraser

Dopo l'installazione dello strumento di creazione, segui questa procedura per creare una chiavetta USB di Microsoft Surface Data Eraser. Prima di iniziare questa procedura, verifica che al computer sia connessa una chiavetta USB 3.0 con almeno 4 GB di spazio.

1. Eseguire il DataEraserSetup.msi di installazione scaricato [dall'Area download Microsoft](https://www.microsoft.com/download/details.aspx?id=46703).

2. Seleziona **Compila** per avviare il processo di creazione usb di Microsoft Surface Data Eraser, come illustrato nella figura 1.

   :::image type="content" source="images/microsoft-surface-data-eraser/fig1-build.png" alt-text="Figura 1. Avviare lo strumento Microsoft Surface Data Eraser":::<br>
  *Figura 1. Avviare lo strumento Microsoft Surface Data Eraser*

3. Selezionare **Continua** per confermare di avere un'unità USB di almeno 4 GB connessa, come illustrato nella figura 2.
   
   :::image type="content" source="images/microsoft-surface-data-eraser/fig2-continue.png" alt-text="Figura 2. Verificare che l'unità USB di almeno 4 GB sia connessa":::<br>
   *Figura 2. Verificare che l'unità USB di almeno 4 GB sia connessa*

4. Scegli **x64 (solo per i dispositivi 2021+ )** per i dispositivi 2021 o più recenti, scegli **x64** per i dispositivi 2020 e versioni precedenti o **ARM64** per Surface Pro X dalla pagina **Selezione** architettura, come illustrato nella figura-3. Seleziona **Continua**.

   :::image type="content" source="images/microsoft-surface-data-eraser/fig3-select.png" alt-text="Figura 3. Selezionare l'architettura dei dispositivi":::

5. Seleziona l'unità USB di tua scelta nella pagina Selezione unità usb thumb **,** come illustrato nella figura 4, quindi seleziona **Avvia** per avviare il processo di creazione dell'UNITÀ USB. L'unità selezionata verrà formattata e tutti i dati presenti nell'unità andranno persi.

   :::image type="content" source="images/microsoft-surface-data-eraser/fig4-start.png" alt-text="Figura 4. Selezione dell'unità pollice USB>":::<br>
   *Figura 4. Selezione della chiavetta USB*

  >[!TIP]
   >Se il pulsante Start è disabilitato, controlla che l'unità rimovibile abbia una capacità totale di almeno 4 GB.

6. Al termine del processo di creazione, l'unità USB è stata formattata e tutti i file binari sono stati copiati nell'unità USB. Selezionare **Success**.

7. Quando viene visualizzata la schermata **Congratulations**, puoi espellere e rimuovere la chiavetta USB. Questa chiavetta USB è ora pronta per essere inserita in un dispositivo Surface e usata per l'avvio e la cancellazione di tutti i dati nel dispositivo. Selezionare **Completa** per completare il processo di creazione USB, come illustrato nella figura 5.

   :::image type="content" source="images/microsoft-surface-data-eraser/fig5-complete.png" alt-text="Completare lo strumento Microsoft Surface Data Eraser":::<br>
   *Figura 5. Completamento del processo di creazione dell'unità USB di Microsoft Surface Data Eraser*

8. Seleziona **X** per chiudere Microsoft Surface Data Eraser.

## <a name="how-to-use-a-microsoft-surface-data-eraser-usb-stick"></a>Come usare una chiavetta USB di Microsoft Surface Data Eraser

Dopo aver creato una chiavetta USB di Microsoft Surface Data Eraser, puoi avviare un dispositivo Surface supportato dalla chiavetta USB seguendo questa procedura:

>[!NOTE]
>Surface Data Eraser in Surface Studio e Surface Studio 2 può richiedere fino a 6 minuti per l'avvio in WinPE prima che possa verificarsi la cancellazione del disco.

1. Inserisci la chiavetta USB di avvio di Microsoft Surface Data Eraser nel dispositivo Surface supportato.

2. Avvia il dispositivo Surface dalla chiavetta USB di Microsoft Surface Data Eraser. Per avviare il dispositivo dalla chiavetta USB attieniti alla procedura seguente:

   a. Spegni il dispositivo Surface.
   b. Tieni premuto il pulsante di **riduzione del volume**.
   c. Premi e rilascia il pulsante di **alimentazione**.
   d. Rilascia il pulsante di **riduzione del volume**.

   >[!TIP]
   >Se il dispositivo non si avvia dalla chiavetta USB con questa procedura, è necessario attivare l'opzione **Enable Alternate Boot Sequence** nell'interfaccia UEFI di Surface. Per altre informazioni sulla configurazione di avvio UEFI di Surface, vedi [Gestire le impostazioni UEFI di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings).

3. Quando il dispositivo Surface viene avviato, viene visualizzato un file di testo **SoftwareLicenseTerms** , come illustrato nella figura 5.

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

8. Seleziona **Sì** per continuare a cancellare i dati nel dispositivo Surface.

   >[!TIP]
   >Quando esegui Surface Data Eraser nell'unità USB di Surface Data Eraser, viene generato un file di log nella cartella **SurfaceDataEraserLogs**.

## <a name="changes-and-updates"></a>Modifiche e aggiornamenti

Microsoft Surface Data Eraser viene aggiornato periodicamente da Microsoft. Per ulteriori informazioni sulle modifiche apportate in ogni nuova versione, vedi quanto segue:

### <a name="3421390"></a>3.42.139.0

*Data di rilascio: 5 ottobre 2021*

Questa versione di Surface Data Eraser include:

- Opzione separata per la versione 2021 e supporto per i dispositivi più nuovi, tra cui Surface Laptop Studio, Surface Pro 8 e Surface Go 3.

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
- Risolve i problemi relativi alla scheda SD

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
>Lo strumento di creazione dell'unità USB di Microsoft Surface Data Eraser non è in grado di essere eseguito Windows 10 S. Per cancellare un Surface Laptop che esegue Windows 10 S, devi prima creare l'unità USB di Microsoft Surface Data Eraser in un altro computer con Windows 10/11 Pro o Windows 10/11 Enterprise.

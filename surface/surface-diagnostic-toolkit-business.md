---
title: Toolkit di diagnostica per Surface per le aziende
description: Questo argomento spiega come distribuire e usare Surface Diagnostic Toolkit for Business, che consente agli amministratori IT di analizzare, risolvere e risolvere rapidamente i problemi hardware, software e firmware con i dispositivi Surface.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/25/2021
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 71a909a00187cf8727ada4e1adabd998b26eb3c0
ms.sourcegitcommit: 94e11386d7034c6bc5fe753f7bebf61a9c815509
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2021
ms.locfileid: "12153981"
---
# <a name="surface-diagnostic-toolkit-for-business"></a>Toolkit di diagnostica per Surface per le aziende

Se Surface non funziona correttamente, Microsoft Surface Diagnostic Toolkit (SDT) for Business può aiutare l'utente o l'amministratore a trovare e risolvere i problemi.  SDT per le aziende ti consente di analizzare, risolvere e risolvere rapidamente i problemi hardware, software e firmware con i dispositivi Surface nella rete.

> [!NOTE]
> Surface Diagnostic Toolkit for Business è progettato per dispositivi commerciali. Se il dispositivo è un dispositivo personale e non è gestito dall'istituto di istruzione o dall'istituto di istruzione, esegui il Toolkit [surface.](https://support.microsoft.com/help/4037239/surface-fix-common-surface-problems-using-surface-diagnostic-toolkit)

In particolare, SDT for Business consente di:

- [Personalizzare il pacchetto.](#preparing-the-sdt-package-for-distribution)
- [Esegui l'app usando i comandi.](surface-diagnostic-toolkit-command-line.md)
- [Eseguire più test hardware per risolvere i problemi.](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [Generare registri per l'analisi dei problemi.](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [Ottieni report dettagliati che confrontano il dispositivo con la configurazione ottimale.](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)

## <a name="primary-scenarios-and-download-resources"></a>Scenari principali e risorse di download

Per eseguire Surface Diagnostic Toolkit for Business, scarica i componenti elencati nella tabella seguente.

Modalità | Scenari principali | Download | Scopri di più
--- | --- | --- | ---
Modalità desktop | Assiste gli utenti nell'esecuzione di SDT nei propri dispositivi Surface per risolvere i problemi.<br>Crea un pacchetto personalizzato da distribuire in uno o più dispositivi Surface, consentendo agli utenti di selezionare log specifici da raccogliere e analizzare. | Pacchetto MSI distribuibile SDT:<br>Programma di installazione di Microsoft Surface Diagnostic Toolkit for Business<br>[Strumenti di Surface per IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Usare le funzionalità di diagnostica Toolkit Surface in modalità desktop](surface-diagnostic-toolkit-desktop-mode.md)
Riga di comando | Risolvere direttamente i problemi dei dispositivi Surface in remoto senza l'interazione dell'utente, usando strumenti standard come Configuration Manager. Include i comandi seguenti:<br>`-DataCollector` raccoglie tutti i file di registro<br>`-bpa` esegue la diagnostica dell'integrità utilizzando Best Practice Analyzer.<br>`-windowsupdate` controlla Windows update per gli aggiornamenti del firmware o dei driver mancanti.<br>`-warranty` controlla le informazioni sulla garanzia. <br><br>| App console SDT:<br>Microsoft Surface Diagnostics App Console<br>[Strumenti di Surface per IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Eseguire la console dell'app da riga di comando con Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-command-line.md)

## <a name="supported-devices"></a>Dispositivi supportati

SDT for Business è supportato nei dispositivi Surface 3 e versioni successive (ad eccezione dei dispositivi configurati in modalità S):

- Surface Book - tutte le generazioni
- Surface Laptop Studio
- Surface Go - tutte le generazioni
- Surface Laptop - tutte le generazioni
- Surface Laptop Go
- Surface Pro 3 e versioni successive
- Surface Pro X - tutte le generazioni
- Surface Studio - tutte le generazioni
- Surface 3 LTE
- Surface 3

## <a name="installing-surface-diagnostic-toolkit-for-business"></a>Installazione di Surface Diagnostic Toolkit for Business

Per creare un pacchetto SDT che puoi distribuire agli utenti dell'organizzazione:

1. Accedi al dispositivo Surface con l'account amministratore.

2. Scarica SDT Windows Installer Package (.msi) dalla pagina [di download di Surface Tools per IT.](https://www.microsoft.com/download/details.aspx?id=46703)

    - Per i dispositivi Intel/AMD, scarica: **Surface_Diagnostic_Toolkit_for_Business_v2.168.139.0.msi**.
    - Per ARM dispositivi, scaricare: **Surface_Diagnostic_Toolkit_for_Business_v2.168.139.0_x86.msi**.

3. Copia il file .msi in una posizione preferita nel dispositivo Surface, ad esempio Desktop. Viene visualizzata la configurazione guidata di SDT, come illustrato nella figura 1. Fai clic su **Avanti**.

    >[!NOTE]
    >Se l'installazione guidata non viene visualizzata, verificare di aver eseguito l'accesso all'account Administrator nel computer.

    ![Benvenuto nella configurazione guidata di Diagnostica Surface Toolkit configurazione guidata.](images/sdt-1.png)<br/>
    *Figura 1. Configurazione guidata Toolkit diagnostica Surface*

4. Quando viene visualizzata la configurazione guidata di SDT, fare clic su **Avanti**, accettare il Contratto di Licenza con l'utente finale (EULA).

5. Nella schermata Opzioni di installazione modificare il percorso di installazione predefinito, se lo si desidera.

6. In Tipo di installazione selezionare **Avanzate.**

    >[!NOTE]
    >L'opzione standard consente agli utenti di eseguire lo strumento di diagnostica direttamente sul dispositivo Surface, purché siano connessi al dispositivo con un account amministratore.

    ![Opzioni di installazione: Avanzate.](images/sdt-install.png)

7. Fare **clic su** Avanti e quindi su **Installa**.

## <a name="installing-using-the-command-line"></a>Installazione tramite riga di comando

Se lo si desidera, è possibile installare SDT al prompt dei comandi e impostare un flag personalizzato per installare lo strumento in modalità amministratore. SDT contiene i seguenti flag di opzione di installazione:

- `SENDTELEMETRY` invia i dati di telemetria a Microsoft. Il flag accetta per `0` disabled o `1` per enabled. Il valore predefinito è `1` l'invio della telemetria.
- `ADMINMODE` configura lo strumento per l'installazione in modalità amministratore. Il flag accetta per `0` la modalità client o per la modalità amministratore `1` IT. Il valore predefinito è `0`.

### <a name="to-install-sdt-from-the-command-line"></a>Per installare SDT dalla riga di comando

1. Aprire un prompt dei comandi e immettere:

    ```console
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```

    **Esempio:**

    ```console
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## <a name="locating-sdt-on-your-surface-device"></a>Individuazione di SDT nel dispositivo Surface

Sia SDT che la console dell'app SDT sono installati in `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` .

Oltre al file .exe, SDT installa un file JSON e un file admin.dll (modules\admin.dll), come illustrato nella figura 2.

:::image type="content" alt-text="elenco dei file SDT installati in Esplora file." source="images/sdt-2.png":::<br/>
*Figura 2. File installati da SDT*

## <a name="preparing-the-sdt-package-for-distribution"></a>Preparazione del pacchetto SDT per la distribuzione

La creazione di un pacchetto personalizzato consente di impostare lo strumento come destinazione per problemi noti specifici.

1. Fai **clic su Start > Esegui,** immetti **Surface** e quindi fai clic su Surface Diagnostic Toolkit **for Business.**

2. All'apertura dello strumento, fare **clic su Crea pacchetto personalizzato**, come illustrato nella figura 3.

    ![Opzione Crea pacchetto personalizzato.](images/sdt-3.png)<br/>
    *Figura 3. Creare un pacchetto personalizzato*

### <a name="language-and-telemetry-settings"></a>Impostazioni di lingua e telemetria

  Quando crei un pacchetto, puoi selezionare le impostazioni della lingua o rifiutare esplicitamente di inviare informazioni di telemetria a Microsoft. Per impostazione predefinita, SDT invia la telemetria a Microsoft che viene usata per migliorare l'applicazione in conformità con [l'Informativa sulla privacy di Microsoft.](https://privacy.microsoft.com/privacystatement) Se si desidera rifiutare, deselezionare la casella di controllo quando si crea un pacchetto personalizzato, come illustrato di seguito. O deselezionare la **casella di controllo Invia** telemetria a Microsoft nella pagina **Opzioni** di installazione durante l'installazione di SDT.

>[!NOTE]
>Questa impostazione non influisce sulla telemetria minima archiviata automaticamente nei server Microsoft durante l'esecuzione di test e riparazioni che richiedono una connessione Internet, ad esempio Windows Update e Ripristino software, o per fornire feedback usando i pulsanti Smile o Cipiglio nella barra degli strumenti dell'app.

![Selezionare le impostazioni di lingua e telemetria.](images/sdt-4.png)<br/>
*Figura 4. Selezionare le impostazioni di lingua e telemetria*

### <a name="windows-update-page"></a>Windows Pagina Aggiorna

Selezionare l'opzione appropriata per l'organizzazione. La maggior parte delle organizzazioni con più utenti in genere sceglie di ricevere gli aggiornamenti tramite Windows Server Update Services (WSUS), come illustrato nella figura 5. Se si usano pacchetti di Windows o WSUS, immettere il percorso appropriato.

![Selezionare Windows'opzione Aggiorna.](images/sdt-5.png)<br/>
*Figura 5. Windows Opzione di aggiornamento*

### <a name="software-repair-page"></a>Pagina di ripristino software

In questo modo è possibile selezionare o rimuovere l'opzione per eseguire gli aggiornamenti di ripristino software.

![Selezionare l'opzione di ripristino del software.](images/sdt-6.png)<br/>
*Figura 6. Opzione di ripristino software*

### <a name="collecting-logs-and-saving-package-page"></a>Pagina Raccolta dei log e salvataggio del pacchetto

È possibile scegliere di eseguire un'ampia gamma di registri tra applicazioni, driver, hardware e sistema operativo. Fare clic sull'area appropriata e scegliere dal menu dei log disponibili. È quindi possibile salvare il pacchetto in un punto di distribuzione software o in un percorso equivalente a cui gli utenti possono accedere.

![Selezionare le opzioni del registro.](images/sdt-7.png)<br/>
*Figura 7. Opzione di log e salvataggio del pacchetto*

## <a name="next-steps"></a>Passaggi successivi

- [Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop](surface-diagnostic-toolkit-desktop-mode.md)
- [Eseguire la console dell'app da riga di comando con Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-command-line.md)

## <a name="changes-and-updates"></a>Modifiche e aggiornamenti

### <a name="version-21681390"></a>Versione 2.168.139.0

Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Surface Pro 8
- Surface Laptop Studio
- Surface Go 3

### <a name="version-21311390"></a>Versione 2.131.139.0

Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Surface Pro 7+
- Esperienza di supporto senza problemi in Surface Pro X
- Miglioramenti della sicurezza
- Miglioramenti inclusivi dell'esperienza utente

### <a name="version-21241390"></a>Versione 2.124.139.0

Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Supporto integrato senza problemi
- Salvare tutti i risultati dei test
- Verificare se l'immagine è stata creata in modo personalizzato
- Includere avvisi da Gestione dispositivi
- Versione firmware dock
- Contrassegnare le unità come potenziali errori nel test di archiviazione
- Rimuovere il collegamento dello Store

### <a name="version-2121139"></a>Versione 2.121.139

*Data di rilascio: 31 luglio 2020*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Esperienza di supporto senza problemi
- Correzioni di bug

### <a name="version-2941390"></a>Versione 2.94.139.0

*Data di rilascio: 11 maggio 2020*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Possibilità di ignorare Windows Update per eseguire il controllo hardware.
- Possibilità di ricevere notifiche sull'aggiornamento della versione più recente
- Surface Go 2
- Surface Book 3
- Mostra indicatore di stato

### <a name="version-2431390"></a>Versione 2.43.139.0

*Data di rilascio: 21 ottobre 2019*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Surface Pro 7
- Surface Laptop 3

### <a name="version-2421390"></a>Versione 2.42.139.0

*Data di rilascio: 24 settembre 2019*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Possibilità di scaricare i report hardware.
- Possibilità di contattare il supporto Tecnico Microsoft direttamente dallo strumento.

### <a name="version-2411390"></a>Versione 2.41.139.0

*Data di rilascio: 24 giugno 2019*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Informazioni sulla versione del driver incluse nei registri e nei report.
- Possibilità di fornire feedback sull'app.

### <a name="version-2361390"></a>Versione 2.36.139.0

*Data di rilascio: 26 aprile 2019*<br>
Questa versione di Surface Diagnostic Toolkit for Business aggiunge il supporto per gli elementi seguenti:

- Opzione di installazione avanzata per sbloccare le funzionalità di amministrazione tramite l'interfaccia utente del programma di installazione, senza richiedere la configurazione della riga di comando.
- Miglioramenti all'accessibilità.
- Impostazioni di controllo della luminosità della superficie incluse nei registri.
- Collegamento al supporto per la compatibilità del monitor esterno nel generatore di report.

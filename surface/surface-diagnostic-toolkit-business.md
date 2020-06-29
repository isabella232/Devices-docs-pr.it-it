---
title: Implementare Toolkit di diagnostica per Surface per le aziende
description: Questo argomento spiega come usare Surface Diagnostic Toolkit for business.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 05/11/2020
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 9233ca1f7e32e2017424e9fb6ceb0556de9d37bd
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832241"
---
# Implementare Toolkit di diagnostica per Surface per le aziende

Microsoft Surface Diagnostic Toolkit for business (SDT) consente agli amministratori IT di analizzare rapidamente, risolvere i problemi relativi a hardware, software e firmware con i dispositivi Surface. È possibile eseguire una serie di test diagnostici e riparazioni software oltre ad ottenere informazioni dettagliate sulla salute dei dispositivi e indicazioni per la risoluzione dei problemi. 

In particolare, SDT for business consente di:

- [Personalizzare il pacchetto.](#create-custom-sdt)
- [Esegui l'app usando i comandi.](surface-diagnostic-toolkit-command-line.md)
- [Eseguire più test hardware per la risoluzione dei problemi.](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [Genera log per l'analisi dei problemi.](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [Ottenere report dettagliati per confrontare la configurazione ottimale del dispositivo.](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## Scenari principali e risorse di download 

Per eseguire SDT for business, scaricare i componenti elencati nella tabella seguente.


Modalità |  Scenari principali | Download | Scopri di più
--- | --- | --- | ---
Modalità desktop |  Aiutare gli utenti a eseguire SDT sui dispositivi Surface per risolvere i problemi.<br>Creare un pacchetto personalizzato da distribuire in uno o più dispositivi Surface, consentendo agli utenti di selezionare registri specifici per la raccolta e l'analisi. | Pacchetto MSI distribuibili di SDT:<br>Programma di installazione di Microsoft Surface Diagnostic Toolkit for business<br>[Strumenti di Surface per IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Usare il Toolkit di diagnostica Surface in modalità desktop](surface-diagnostic-toolkit-desktop-mode.md)
Riga di comando |  Risolvere direttamente i dispositivi Surface in remoto senza interazione con l'utente, usando strumenti standard come Configuration Manager. Include i comandi seguenti:<br>`-DataCollector` raccoglie tutti i file di log<br>`-bpa` esegue la diagnostica sanitaria con Best Practice Analyzer.<br>`-windowsupdate` Controlla Windows Update per gli aggiornamenti mancanti del firmware o del driver.<br>`-warranty` Controlla le informazioni sulla garanzia. <br><br>| App console SDT:<br>Console app Microsoft Surface Diagnostics<br>[Strumenti di Surface per IT](https://www.microsoft.com/download/details.aspx?id=46703) | [Eseguire il Toolkit di diagnostica superficie usando i comandi](surface-diagnostic-toolkit-command-line.md)

## Dispositivi supportati 

SDT for business è supportato nei dispositivi Surface 3 e versioni successive, tra cui:

- Surface Book 3
- Superficie Go 2
- Surface Pro X
- Surface Pro 7
- Laptop Surface 3
- Surface Pro 6
- Surface Laptop 2
- Surface Go
- Surface go con LTE
- Surface Book 2
- Surface Pro con LTE Advanced (Modello 1807)
- Surface Pro (Modello 1796)
- Surface Laptop
- Surface Studio
- Surface Studio 2
- Surface Book
- Surface Pro 4
- Surface 3 LTE
- Surface 3
- Surface Pro 3

## Installazione di Surface Diagnostic Toolkit for business

Per creare un pacchetto SDT che può essere distribuito agli utenti dell'organizzazione:

1. Accedere al dispositivo Surface usando l'account Administrator.
2. Scarica il pacchetto SDT Windows Installer (. msi) dalla [pagina strumenti Surface per il download](https://www.microsoft.com/download/details.aspx?id=46703) e copialo in una posizione preferita nel dispositivo Surface, ad esempio desktop.
3. Verrà visualizzata la configurazione guidata SDT, come illustrato nella figura 1. Fai clic su **Avanti**. 

    >[!NOTE]
    >Se la configurazione guidata non viene visualizzata, assicurarsi di avere eseguito l'accesso all'account di amministratore nel computer. 

    ![Introduzione alla configurazione guidata di Surface Diagnostic Toolkit](images/sdt-1.png)

    *Figura 1. Configurazione guidata di Surface Diagnostic Toolkit*

4. Quando viene visualizzata la configurazione guidata SDT, fare clic su **Avanti**, accettare il contratto di licenza con l'utente finale (EULA)

5. Nella schermata Opzioni di installazione modificare la posizione di installazione predefinita, se necessario. 
6. In tipo di installazione selezionare **Avanzate**. 

    >[!NOTE]
    >L'opzione standard consente agli utenti di eseguire lo strumento di diagnostica direttamente sul dispositivo Surface, purché abbiano eseguito l'accesso al dispositivo usando un account di amministratore. 
    
     ![Opzioni di installazione: avanzate](images/sdt-install.png)

7. Fare clic su **Avanti** e quindi su **Installa**. 

## Installazione tramite la riga di comando
Se lo si desidera, è possibile installare SDT al prompt dei comandi e impostare un contrassegno personalizzato per l'installazione dello strumento in modalità amministratore. SDT contiene i seguenti flag di opzione di installazione:

- `SENDTELEMETRY` Invia i dati di telemetria a Microsoft. Il contrassegno accetta `0` per disabilitato o `1` abilitato. Il valore predefinito è l' `1` invio di telemetria.
- `ADMINMODE` Configura lo strumento da installare in modalità amministratore. Il contrassegno accetta `0` per la modalità client o `1` per l'amministratore it. Il valore predefinito è `0`.

### Per installare SDT dalla riga di comando:

1. Aprire un prompt dei comandi e immettere:

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **Esempio:**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## Individuazione di SDT nel dispositivo Surface

Sono installate sia l'SDT che la console dell'app SDT `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` .

Oltre al file exe, SDT installa un file JSON e un file di admin.dll (modules\admin.dll), come illustrato nella figura 2.

![elenco dei file installati in SDT in Esplora file](images/sdt-2.png)

*Figura 2. File installati da SDT*

<span id="create-custom-sdt" />

## Preparazione del pacchetto SDT per la distribuzione

La creazione di un pacchetto personalizzato consente di indirizzare lo strumento a problemi noti specifici.

1. Fare clic su **avvia > Esegui**, immettere **Surface** e quindi fare clic su **Surface Diagnostic Toolkit for business**. 
2. Quando lo strumento si apre, fare clic su **Crea pacchetto personalizzato**, come illustrato nella figura 3.

    ![Opzione Crea pacchetto personalizzato](images/sdt-3.png)

    *Figura 3. Creare un pacchetto personalizzato*

### Impostazioni della lingua e della telemetria

  Quando si crea un pacchetto, è possibile selezionare le impostazioni della lingua o rifiutare di inviare informazioni di telemetria a Microsoft. Per impostazione predefinita, l'SDT Invia la telemetria a Microsoft usata per migliorare l'applicazione conformemente all' [informativa sulla privacy Microsoft](https://privacy.microsoft.com/privacystatement). Se si vuole rifiutare, deselezionare la casella di controllo quando si crea un pacchetto personalizzato, come illustrato di seguito. O deselezionare la casella **di controllo Invia telemetria a Microsoft** nella pagina **Opzioni di installazione** durante la configurazione SDT. 

>[!NOTE]
>Questa impostazione non ha alcun effetto sulla telemetria minima memorizzata automaticamente nei server Microsoft quando si esegue test e riparazioni che richiedono una connessione Internet, ad esempio Windows Update e software Repair, o un feedback usando i pulsanti Smile o cipiglio nella barra degli strumenti dell'app. 


![Selezionare la lingua e le impostazioni di telemetria](images/sdt-4.png)

*Figura 4. Selezionare la lingua e le impostazioni di telemetria*


### Pagina Windows Update

Selezionare l'opzione appropriata per l'organizzazione. La maggior parte delle organizzazioni con più utenti in genere verrà selezionata per ricevere gli aggiornamenti tramite Windows Server Update Services (WSUS), come illustrato nella figura 5. Se si usano i pacchetti di Windows Update locali o WSUS, immettere il percorso in base alle esigenze. 

![Selezionare l'opzione Windows Update](images/sdt-5.png)

*Figura 5. Opzione Windows Update*

### Pagina di ripristino del software

In questo modo è possibile selezionare o rimuovere l'opzione per eseguire gli aggiornamenti per il ripristino del software. 

![Selezionare l'opzione di ripristino software](images/sdt-6.png)

*Figura 6. Opzione di ripristino software*

### Raccolta di registri e salvataggio della pagina del pacchetto

È possibile selezionare l'esecuzione di un'ampia gamma di log tra applicazioni, driver, hardware e sistema operativo. Fare clic sull'area appropriata e selezionare dal menu dei registri disponibili. È quindi possibile salvare il pacchetto in un punto di distribuzione del software o in una posizione equivalente a cui gli utenti possono accedere. 

![Selezionare opzioni log](images/sdt-7.png)

*Figura 7. Opzione log e Salva pacchetto*

## Passaggi successivi

- [Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop](surface-diagnostic-toolkit-desktop-mode.md)
- [Usare i comandi con Surface Diagnostic Toolkit for business](surface-diagnostic-toolkit-command-line.md)

## Modifiche e aggiornamenti

### Versione 2.94.139.0
*Data di rilascio: 11 maggio 2020*<br>
Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:

- Possibilità di ignorare Windows Update per eseguire il controllo hardware.
- Possibilità di ricevere notifiche per informazioni sull'aggiornamento della versione più recente
- Superficie Go 2
- Surface Book 3
- Mostra indicatore di stato


### Versione 2.43.139.0
*Data di rilascio: 21 ottobre 2019*<br>
Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:

- Surface Pro 7
- Laptop Surface 3

### Versione 2.42.139.0
*Data di rilascio: 24 settembre 2019*<br>
Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti: 
- Possibilità di scaricare i report hardware.
- Possibilità di contattare il supporto Microsoft direttamente dallo strumento. <br>

### Versione 2.41.139.0
*Data di rilascio: 24 giugno 2019*<br>
Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti: 
- Informazioni sulla versione del driver incluse nei registri e nel report.
- Possibilità di inviare commenti e suggerimenti sull'app.<br>


### Versione 2.36.139.0
*Data di rilascio: 26 aprile 2019*<br>
Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti: 
- Opzione di configurazione avanzata per sbloccare le funzionalità di amministrazione tramite l'interfaccia utente del programma di installazione, senza richiedere la configurazione della riga di comando.
- Miglioramenti dell'accessibilità.
- Impostazioni di controllo della luminosità superficiale incluse nei registri.
- Collegamento supporto compatibilità monitor esterno in Generatore report.

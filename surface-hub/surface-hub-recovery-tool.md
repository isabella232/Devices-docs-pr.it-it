---
title: Uso dello strumento di ripristino di Surface Hub
description: Come usare lo strumento di ripristino di Surface hub per ricreare l'immagine dell'SSD.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: gestire Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 12/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: a9ebab6848efa706609a39b0eb99fa42df2156bf
ms.sourcegitcommit: ce7ad475b776a78ba215e77111ea5371afeb4f28
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2020
ms.locfileid: "11237335"
---
# Uso dello strumento di ripristino di Surface Hub

Lo [strumento Microsoft Surface Hub Recovery](https://www.microsoft.com/download/details.aspx?id=52210) consente di ricreare l'unità SSD (Solid State Drive) di Surface hub usando un dispositivo desktop Windows 10, senza chiamare il supporto o sostituendo l'SSD. Con questo strumento puoi rieseguire l'immagine di un SSD che ha una password di amministratore sconosciuta, errori di avvio, non è riuscito a completare un ripristino del cloud o per un dispositivo con una versione precedente del sistema operativo. Lo strumento non risolverà gli SSD danneggiati fisicamente.

Per ricreare l'unità SSD Surface hub usando lo strumento di ripristino, è necessario rimuovere l'SSD dall'hub di Surface, connettere il drive al cavo USB-to-SATA e quindi connettere il cavo al PC desktop in cui è installato lo strumento di ripristino. Per altre informazioni su come rimuovere l'unità esistente dal proprio hub Surface, vedere [sostituzione di Surface Hub SSD](surface-hub-ssd-replacement.md).

> [!IMPORTANT]
> Non consentire al dispositivo di andare a dormire o interrompere il download del file di immagine.

Se lo strumento non riesce a rieseguire la riimmagine dell'unità, contattare il [supporto per Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

## Prerequisiti

### Mandatory

- PC host con versione a 64 bit di Windows 10, versione 1607 o successiva.
- Accesso a Internet
- Aprire la porta USB 2,0 o maggiore
- Cavo da USB a SATA
- 10 GB di spazio libero su disco nel computer host
- SSD spediti con Surface Hub o un SSD forniti dal supporto come sostituto. Gli SSD non forniti da Microsoft non sono supportati.

### Consigliato

- Connessione Internet ad alta velocità
- Aprire la porta USB 3,0
- USB 3,0 o superiore cavo USB-to-SATA
- Lo strumento di imaging è stato testato con la creazione e il modello di cavi seguenti:
    - Startech USB312SAT3CB
    - Rosewill RCUC16001
    - UGreen 20231

## Scaricare lo strumento Surface Hub Recovery

Lo strumento di ripristino di Surface Hub è disponibile per il download dagli [strumenti di Surface hub per](https://www.microsoft.com/download/details.aspx?id=52210)  l'oggetto sotto il nome file **SurfaceHub_Recovery_v2.0.139.0.msi**.

Per avviare il download, fare clic su **Scarica**, scegliere **SurfaceHub_Recovery_v2.0.139.0.msi** nell'elenco e fare clic su **Avanti**. Nella finestra popup scegliere una delle opzioni seguenti:

- Fare clic su **Esegui** per avviare immediatamente l'installazione.
- Fare clic su **Salva** per copiare il download nel computer per l'installazione successiva.

Installare lo strumento Surface Hub Recovery nel PC host.

## Strumento Esegui recupero Hub Surface

1. Nel PC host selezionare il pulsante **Start** , scorrere l'elenco alfabetico a sinistra e selezionare il collegamento strumento ripristino.

    ![Collegamento allo strumento Ripristino superficie Hub Microsoft](images/shrt-shortcut.png)

2. Fai clic su **Start**.

    ![Pulsante Start dello strumento di ripristino](images/shrt-start.png)


3. Nella finestra **linee guida** fare clic su **Avanti**.

    ![Non consentire al computer di accedere alle indicazioni per il sonno](images/shrt-guidance.png)

4. Nella finestra Seleziona immagine fare clic su **RS2** o sul relativo successore **20H2**, selezionare **continua** e quindi selezionare **Scarica immagine.**

     ![Strumento di ripristino selezionare immagine ](images/shrt-select-image.png) ![ download strumento di recupero immagini](images/shrt-download-image.png)

5. Il tempo necessario per scaricare l'immagine di ripristino dipende dalle velocità di connessione Internet. In una connessione aziendale media può essere necessaria fino a un'ora per scaricare il file di immagine da 8GB.

    ![Download dell'immagine](images/shrt-download.png)



5. Al termine del download, lo strumento indica di connettere un'unità SSD. Se lo strumento non riesce a trovare l'unità collegata, è probabile che il cavo usato non riferisca il nome dell'SSD a Windows.  Lo strumento di imaging deve trovare il nome dell'unità come "LITEON L CH-128V2S USB Device" prima che possa continuare.  Per altre informazioni su come rimuovere l'unità esistente dal proprio hub Surface, vedere [sostituzione di Surface Hub SSD](surface-hub-ssd-replacement.md).

    ![Connettere SSD](images/shrt-drive.png)

6. Quando l'unità viene riconosciuta, fare clic sul pulsante **Start** per avviare il processo di creazione di immagini. Nell'avviso che tutti i dati dell'unità verranno cancellati, fare clic su **OK**.



    Prima di applicare l'immagine del sistema all'unità, l'SSD viene ripartizionato e formattato. La copia dei file binari di sistema impiegano circa 30 minuti, ma può richiedere più tempo a seconda della velocità del bus USB, del cavo usato o del software antivirus installato nel sistema.



## Problemi comuni per la risoluzione dei problemi

Problema | Note
--- | ---
Lo strumento non riesce a immagine dell'SSD | Assicurarsi di usare un SSD fornito in fabbrica e uno dei cavi testati.
Il processo di riimaging viene interrotto/bloccato | È sicuro chiudere e riavviare lo strumento di ripristino di Surface Hub senza effetti negativi per l'SSD.
L'unità non viene riconosciuta dallo strumento | Verificare che l'unità SSD Surface hub sia enumerata come Lite-On Drive, "LITEON L CH-128V2S USB Device".  Se l'unità viene riconosciuta come un altro dispositivo denominato, il cavo corrente non è compatibile. Provare un altro cavo o uno dei cavi testati sopra elencati.
Errore:-2147024809 | Aprire Disk Manager e rimuovere le partizioni nell'unità Surface Hub.  Disconnettere e riconnettere l'unità al computer host. Riavviare lo strumento di imaging.

Se lo strumento non riesce a rieseguire la riimmagine dell'unità, contattare il [supporto per Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

## Cronologia versioni

### Versione v 2.0.139.0

*Data di rilascio: 18 dicembre 2020*<br>
Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:
- Aggiornamento per supportare l'aggiornamento di Windows 10 team 2020 (20H2)
- Miglioramenti dell'esperienza utente
- Modifiche architetturali
- Aggiunte di telemetria


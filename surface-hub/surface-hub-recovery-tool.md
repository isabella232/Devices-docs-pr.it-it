---
title: Uso dello strumento di ripristino di Surface Hub
description: Come usare lo strumento di ripristino di Surface Hub per ri-creare un'immagine dell'unità SSD.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: gestire Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/11/2020
ms.localizationpriority: medium
ms.openlocfilehash: 0cc444eab51e9c3cc0bf2f9c2f0c36ac491906b1
ms.sourcegitcommit: 7b09b4bc757c5385c4f5560713cb03448afde9ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/16/2021
ms.locfileid: "11339367"
---
# Uso dello strumento di ripristino di Surface Hub

Lo strumento di ripristino di [Microsoft Surface Hub](https://www.microsoft.com/download/details.aspx?id=52210) consente di ri-creare un'immagine dell'unità SSD (Solid State Drive) di Surface Hub con un dispositivo desktop Windows 10, senza chiamare il supporto o sostituire l'unità SSD. Con questo strumento puoi ricreare l'immagine di un'unità SSD con una password amministratore sconosciuta, errori di avvio, non è stato possibile completare un ripristino cloud o per un dispositivo con una versione precedente del sistema operativo. Lo strumento non correggerà le unità SSD danneggiate fisicamente.

Per ri-creare un'immagine dell'unità SSD di Surface Hub con lo strumento di ripristino, dovrai rimuovere l'unità SSD da Surface Hub, connettere l'unità al cavo DA USB a SATA e quindi collegare il cavo al PC desktop in cui è installato lo strumento di ripristino. Per altre informazioni su come rimuovere l'unità esistente dal dispositivo Surface Hub, vedi La sostituzione [dell'unità SSD](surface-hub-ssd-replacement.md)di Surface Hub.

> [!IMPORTANT]
> Non lasciare che il dispositivo vada in sospensione o interrompa il download del file di immagine.

Se lo strumento non riesce a riimimare l'unità, contatta il [supporto di Surface Hub.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

## Prerequisiti

### Mandatory

- Pc host che esegue la versione a 64 bit di Windows 10 versione 1607 o successiva.
- Accesso a Internet
- Aprire la porta USB 2.0 o successiva
- Cavo DA USB a SATA
- 10 GB di spazio libero su disco nel computer host
- SSD forniti con Surface Hub o un SSD fornito dal supporto in sostituzione. Le SSD non fornite da Microsoft non sono supportate.

### Consigliato

- Connessione Internet ad alta velocità
- Aprire la porta USB 3.0
- Cavo USB 3.0 o superiore da USB a SATA
- Lo strumento di creazione di immagini è stato testato con la seguente creazione e modello di cavi:
    - Startech USB312SAT3CB
    - Rosawill RCUC16001
    - Ugreen 20231

## Scaricare lo strumento di ripristino di Surface Hub

Lo strumento di ripristino di Surface Hub è disponibile per il download da [Strumenti di Surface Hub per l'IT](https://www.microsoft.com/download/details.aspx?id=52210)  con il nome file **SurfaceHub_Recovery_v2.7.139.0.msi**.

> [!IMPORTANT]
> Questa versione, rilasciata l'11 febbraio 2021, sostituisce la build precedente, che non è più funzionante. Se lo strumento è stato scaricato in precedenza, disinstallarlo e installare la versione corrente.

Per avviare il download, fare clic su **Download,** **scegliereSurfaceHub_Recovery_v2.7.139.0.msi'elenco** e fare clic su **Avanti.** Dal popup, scegliere una delle opzioni seguenti:

- Fare **clic su Esegui** per avviare immediatamente l'installazione.
- Fare **clic su** Salva per copiare il download nel computer per un'installazione successiva.

Installare lo strumento di ripristino di Surface Hub nel PC host.

## Eseguire lo strumento di ripristino di Surface Hub

1. Nel PC host seleziona il pulsante **Start,** scorri l'elenco alfabetico a sinistra e seleziona il collegamento dello strumento di ripristino.

    ![Collegamento dello strumento di ripristino di Microsoft Surface Hub](images/shrt-shortcut.png)

2. Fai clic su **Start**.

    ![Pulsante Start dello strumento di ripristino](images/shrt-start.png)


3. Nella finestra **Linee guida** fare clic su **Avanti.**

    ![Non consentire al computer di passare alla guida di sospensione](images/shrt-guidance.png)

4. Nella finestra Seleziona immagine fare clic su **RS2** o sul successore **20H2,** selezionare **Continua e** quindi **Selezionare Scarica immagine.**

     ![Immagine di download dello strumento ](images/shrt-select-image.png) ![ di recupero dell'immagine selezionata](images/shrt-download-image.png)

5. Il tempo necessario per scaricare l'immagine di ripristino dipende dalla velocità della connessione Internet. In una connessione aziendale media, il download del file di immagine da 8 GB può richiedere fino a un'ora.

    ![Download dell'immagine](images/shrt-download.png)



5. Al termine del download, lo strumento indica di connettere un'unità SSD. Se lo strumento non riesce a individuare l'unità collegata, è probabile che il cavo in uso non segnala il nome dell'unità SSD a Windows.  Lo strumento di creazione di immagini deve trovare il nome dell'unità come "LITEON L CH-128V2S USB Device" prima di poter continuare.  Per altre informazioni su come rimuovere l'unità esistente dal dispositivo Surface Hub, vedi La sostituzione [dell'unità SSD](surface-hub-ssd-replacement.md)di Surface Hub.

    ![Connettere SSD](images/shrt-drive.png)

6. Quando l'unità viene riconosciuta, fai clic su **Start** per avviare il processo di creazione di una immagine. Nell'avviso che indica che tutti i dati nell'unità verranno cancellati, fare clic su **OK.**



    Prima di applicare l'immagine di sistema all'unità, l'unità SSD viene ripartizionata e formattata. La copia dei file binari di sistema richiede circa 30 minuti, ma può richiedere più tempo a seconda della velocità del bus USB, del cavo in uso o del software antivirus installato nel sistema.



## Risoluzione dei problemi e problemi comuni

Problema | Note
--- | ---
Lo strumento non riesce a creare un'immagine del disco SSD | Assicurati di usare un SSD fornito in fabbrica e uno dei cavi testati.
Il processo di reimaging viene visualizzato interrotto/bloccato | È possibile chiudere e riavviare lo strumento di ripristino di Surface Hub senza alcun effetto negativo sull'unità SSD.
L'unità non viene riconosciuta dallo strumento | Verifica che l'unità SSD di Surface Hub sia enumerata come unità Lite-On, "Dispositivo USB LITEON L CH-128V2S".  Se l'unità viene riconosciuta come un altro dispositivo denominato, il cavo corrente non è compatibile. Provare un altro cavo o uno dei cavi testati elencati in precedenza.
Errore: -2147024809 | Apri Gestione disco e rimuovi le partizioni nell'unità Surface Hub.  Disconnettere e riconnettere l'unità al computer host. Riavvia di nuovo lo strumento per la creazione di immagini.

Se lo strumento non riesce a riimimare l'unità, contatta il [supporto di Surface Hub.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

## Cronologia delle versioni


### Versione v2.7.139.0

*Data di rilascio: 11 febbraio 2021*<br>
Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:

- Aggiornamento della sicurezza


### Versione v2.0.139.0

> [!IMPORTANT]
> Questa versione non è più funzionante. Scarica la versione corrente, elencata in precedenza. 

*Data di rilascio: 18 dicembre 2020*<br>
Questa versione dello strumento di ripristino di Surface Hub aggiunge il supporto per gli elementi seguenti:
- Aggiornamento per supportare Windows 10 Team 2020 Update (20H2)
- Miglioramenti dell'esperienza utente
- Modifiche architetturali
- Aggiunte di telemetria


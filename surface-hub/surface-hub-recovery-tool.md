---
title: Uso dello strumento di ripristino di Surface Hub
description: Come usare lo strumento Surface Hub ripristino per riappare l'immagine del disco SSD.
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
ms.openlocfilehash: f472d42bba9270b117cfa8cb9b54eaeb020aefc4
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11910981"
---
# <a name="using-the-surface-hub-recovery-tool"></a>Uso dello strumento di ripristino di Surface Hub

Lo [Microsoft Surface Hub Recovery Tool](https://www.microsoft.com/download/details.aspx?id=52210) consente di ri-immagine dell'unità SSD (Solid State Drive) di Surface Hub usando un dispositivo desktop Windows 10, senza chiamare il supporto o sostituire l'unità SSD. Con questo strumento, puoi ricreare l'immagine di un SSD con una password di amministratore sconosciuta, errori di avvio, non è stato in grado di completare un ripristino cloud o per un dispositivo con una versione precedente del sistema operativo. Lo strumento non correggerà gli SSD danneggiati fisicamente.

Per eseguire nuovamente l'immagine dell'unità SSD di Surface Hub utilizzando lo strumento di ripristino, è necessario rimuovere l'SSD dal Surface Hub, connettere l'unità al cavo da USB a SATA e quindi collegare il cavo al PC desktop in cui è installato lo strumento di ripristino. Per ulteriori informazioni su come rimuovere l'unità esistente dal Surface Hub, vedere Surface Hub [sostituzione SSD.](surface-hub-ssd-replacement.md)

> [!IMPORTANT]
> Non lasciare che il dispositivo vada in sospensione o interrompa il download del file di immagine.

Se lo strumento non riesce a riim mediare l'unità, contattare [Surface Hub Supporto tecnico.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

## <a name="prerequisites"></a>Prerequisiti

### <a name="mandatory"></a>Mandatory

- Pc host che esegue la versione a 64 bit di Windows 10 versione 1607 o successiva.
- Accesso a Internet
- Aprire la porta USB 2.0 o successiva
- Cavo DA USB a SATA
- 10 GB di spazio libero su disco nel computer host
- SSD forniti con Surface Hub o un SSD fornito dal supporto in sostituzione. Gli SSD non forniti da Microsoft non sono supportati.

### <a name="recommended"></a>Consigliato

- Connessione Internet ad alta velocità
- Aprire la porta USB 3.0
- Cavo USB 3.0 o superiore da USB a SATA
- Lo strumento di creazione di immagini è stato testato con la seguente creazione e modello di cavi:
    - Startech USB312SAT3CB
    - Rosewill RCUC16001
    - Ugreen 20231

## <a name="download-surface-hub-recovery-tool"></a>Download Surface Hub Recovery Tool

Surface Hub Lo strumento di ripristino è disponibile per il download [da Surface Hub Tools for IT](https://www.microsoft.com/download/details.aspx?id=52210) sotto il nome file **SurfaceHub_Recovery_v2.7.139.0.msi**.

> [!IMPORTANT]
> Questa versione, rilasciata l'11 febbraio 2021, sostituisce la build precedente, che non è più funzionante. Se lo strumento è stato scaricato in precedenza, disinstallarlo e installare la versione corrente.

Per avviare il download, fare clic su **Scarica,** **scegliereSurfaceHub_Recovery_v2.7.139.0.msi** dall'elenco e fare clic su **Avanti.** Dal popup scegliere una delle opzioni seguenti:

- Fare **clic su** Esegui per avviare immediatamente l'installazione.
- Fare **clic su** Salva per copiare il download nel computer per l'installazione successiva.

Installare Surface Hub di ripristino sul PC host.

## <a name="run-surface-hub-recovery-tool"></a>Eseguire Surface Hub Recovery Tool

1. Nel PC host seleziona il pulsante **Start,** scorri l'elenco alfabetico a sinistra e seleziona il collegamento dello strumento di ripristino.

    ![Microsoft Surface Hub Collegamento dello strumento di ripristino.](images/shrt-shortcut.png)

2. Fai clic su **Start**.

    ![Pulsante Start dello strumento di ripristino.](images/shrt-start.png)


3. Nella finestra **Linee guida** fare clic su **Avanti.**

    ![Non lasciare che il computer vada in sospensione.](images/shrt-guidance.png)

4. Nella finestra Seleziona immagine fare clic su **RS2** o sul suo successore **20H2,** selezionare **Continua e** quindi **selezionare Scarica immagine.**

     ![Immagine di selezione dello strumento di ripristino.](images/shrt-select-image.png)
    ![Immagine di download dello strumento di ripristino.](images/shrt-download-image.png)

5. Il tempo necessario per scaricare l'immagine di ripristino dipende dalla velocità della connessione Internet. In una connessione aziendale media, il download del file di immagine da 8 GB può richiedere fino a un'ora.

    ![Download dell'immagine.](images/shrt-download.png)



5. Al termine del download, lo strumento indica di connettere un'unità SSD. Se lo strumento non è in grado di individuare l'unità collegata, è probabile che il cavo utilizzato non segnala il nome dell'unità SSD a Windows.  Per poter continuare, lo strumento di creazione di immagini deve trovare il nome dell'unità come "Dispositivo USB LITEON L CH-128V2S".  Per ulteriori informazioni su come rimuovere l'unità esistente dal Surface Hub, vedere Surface Hub [sostituzione SSD.](surface-hub-ssd-replacement.md)

    ![Connessione SSD.](images/shrt-drive.png)

6. Quando l'unità viene riconosciuta, fare clic **su Avvia** per avviare il processo di creazione di immagini. Nell'avviso che tutti i dati nell'unità verranno cancellati, fare clic su **OK.**



    Prima di applicare l'immagine di sistema all'unità, l'SSD viene ripartizionato e formattato. La copia dei file binari di sistema richiede circa 30 minuti, ma può richiedere più tempo a seconda della velocità del bus USB, del cavo utilizzato o del software antivirus installato nel sistema.



## <a name="troubleshooting-and-common-problems"></a>Risoluzione dei problemi e problemi comuni

Problema | Note
--- | ---
Lo strumento non riesce a visualizzare l'immagine del file SSD | Assicurati di usare un SSD fornito in fabbrica e uno dei cavi testati.
Il processo di reimaging risulta interrotto/bloccato | È sicuro chiudere e riavviare lo Surface Hub di ripristino senza alcun effetto negativo per l'SSD.
L'unità non viene riconosciuta dallo strumento | Verificare che il Surface Hub SSD sia enumerato come unità Lite-On, "Dispositivo USB LITEON L CH-128V2S".  Se l'unità viene riconosciuta come un altro dispositivo denominato, il cavo corrente non è compatibile. Provare un altro cavo o uno dei cavi testati elencati in precedenza.
Errore: -2147024809 | Aprire Gestione disco e rimuovere le partizioni nell'Surface Hub disco.  Disconnettere e riconnettere l'unità al computer host. Riavviare di nuovo lo strumento di creazione di immagini.

Se lo strumento non riesce a riim mediare l'unità, contattare [Surface Hub Supporto tecnico.](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support)

## <a name="version-history"></a>Cronologia versioni


### <a name="version-v271390"></a>Versione v2.7.139.0

*Data di rilascio: 11 febbraio 2021*<br>
Questa versione di Surface Hub Recovery Tool aggiunge il supporto per gli elementi seguenti:

- Aggiornamento della sicurezza


### <a name="version-v201390"></a>Versione v2.0.139.0

> [!IMPORTANT]
> Questa versione non è più funzionante. Scarica la versione corrente, elencata sopra. 

*Data di rilascio: 18 dicembre 2020*<br>
Questa versione di Surface Hub Recovery Tool aggiunge il supporto per gli elementi seguenti:
- Aggiornamento per il Windows 10 Team 2020 (20H2)
- Miglioramenti dell'esperienza utente
- Modifiche architetturali
- Aggiunte di telemetria


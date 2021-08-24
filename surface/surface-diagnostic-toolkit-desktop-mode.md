---
title: Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop
description: Come usare SDT per aiutare gli utenti dell'organizzazione a eseguire lo strumento per identificare e diagnosticare i problemi con il dispositivo Surface, nonché inviare richieste di supporto direttamente dallo strumento.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 7/31/2020
ms.openlocfilehash: 7ebdff37cb96589c765e9c9315b098a760976c80
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911241"
---
# <a name="use-surface-diagnostic-toolkit-for-business-in-desktop-mode"></a>Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop

Questo argomento spiega come usare Surface Diagnostic Toolkit (SDT) per aiutare gli utenti dell'organizzazione a eseguire lo strumento per identificare e diagnosticare i problemi con il dispositivo Surface, nonché inviare richieste di supporto direttamente dallo strumento. 

L'esecuzione corretta di SDT può determinare rapidamente se un problema segnalato è causato da un errore hardware o da un errore dell'utente. Per un elenco dei dispositivi Surface supportati in SDT, fai riferimento a [Deploy Surface Diagnostic Toolkit for Business.](surface-diagnostic-toolkit-business.md)


1. Indica all'utente di installare [il pacchetto SDT](surface-diagnostic-toolkit-business.md#preparing-the-sdt-package-for-distribution)) da un punto di distribuzione software o da una condivisione di rete. Dopo l'installazione, sei pronto per guidare l'utente attraverso una serie di test. 

2. Iniziare dalla home page, che consente agli utenti di immettere una descrizione del problema e fare clic su **Continua**, come illustrato nella figura 1.

    ![Avvia SDT in modalità desktop. ](images/sdt-desk-1.png)
 *Figura 1. SDT in modalità desktop*

3. Quando SDT indica che il dispositivo ha gli aggiornamenti più recenti, fai clic su **Continua** per passare al catalogo dei test disponibili, come illustrato nella figura 2.

    ![Selezionare una delle opzioni SDT. ](images/sdt1.png)
 *Figura 2. Seleziona da opzioni SDT*

4. È possibile scegliere di eseguire tutti i test di diagnostica. In caso contrario, se si sospetta già un problema specifico, **** ad esempio uno schermo difettoso o un problema di alimentazione, fare clic su Seleziona per scegliere tra i test disponibili e fare clic su Esegui selezionato **,** come illustrato nella figura 3. Per informazioni dettagliate su ogni test, vedere la tabella seguente. 

    ![Selezionare i test hardware. ](images/sdt2.png)
 *Figura 3. Selezionare i test hardware*

    Test hardware | Descrizione
    --- | ---
    Alimentazione e batteria |  Verifica che l'alimentazione funzioni in modo ottimale
    Display and Sound   | Controlla la luminosità, i pixel bloccati o non funzionanti, il funzionamento dell'altoparlante e del microfono
    Porte e accessori   | Controlla accessori, collegamento schermo e funzionamento USB
    Connectivity |  Controlla Bluetooth, wireless e la connettività LTE
    Sicurezza    | Controlla i problemi correlati alla sicurezza
    Touch screen   | Controlla i problemi correlati al tocco
    Tastiera e tocco |    Controlla la connessione della tastiera integrata e la copertura del tipo
    Sensori | Controlla il funzionamento di sensori diversi nel dispositivo
    Hardware |  Controlla i problemi relativi a diversi componenti hardware, ad esempio scheda grafica e fotocamera

5. Al termine di tutti i test, lo strumento chiede di confermare se il problema è stato risolto. 

 ![Il problema è stato risolto? ](images/sdt3.png)
 *Figura 3a. Il problema è stato risolto?*

6. Se il problema non viene risolto o non si sa, è possibile inviare un ticket di supporto selezionando **Contattaci** per **ottenere assistenza.**
 
 ![Inviare un ticket di supporto. ](images/sdt4.png)
 *Figura 3b. Inviare un ticket di supporto*

<span id="multiple" />

## <a name="running-multiple-hardware-tests-to-troubleshoot-issues"></a>Esecuzione di più test hardware per risolvere i problemi

SDT è progettato come uno strumento interattivo che esegue una serie di test. Per ogni test, SDT fornisce istruzioni che riepilogano la natura del test e cosa gli utenti devono aspettarsi o cercare perché il test sia completato correttamente. Ad esempio, per diagnosticare se la luminosità dello schermo funziona correttamente, SDT inizia da zero e **** aumenta la luminosità al 100%, chiedendo agli utenti di confermare , rispondendo sì o **no,** che la luminosità funzioni come previsto, come illustrato nella figura 4. 

Per ogni test, se la funzionalità non funziona come previsto e l'utente fa clic su **No,** SDT genera un report sulle possibili cause e sui modi per risolverlo. 

![Esecuzione della diagnostica hardware. ](images/sdt-desk-4.png)
 *Figura 4. Esecuzione della diagnostica hardware*

1. Se la luminosità viene regolata correttamente da 0 a 100% come previsto, indica all'utente di fare clic su **Sì** e quindi su **Continua.** 
2. Se la luminosità non riesce a regolare da 0 a 100% come previsto, indica all'utente di fare clic su **No** e quindi su **Continua.** 
3. Guidare gli utenti attraverso i test rimanenti in base alle esigenze. Al termine, SDT fornisce automaticamente un riepilogo di alto livello del report, incluse le possibili cause di eventuali problemi hardware insieme alle indicazioni per la risoluzione.


### <a name="repairing-applications"></a>Ripristino delle applicazioni

SDT consente di diagnosticare e ripristinare le applicazioni che potrebbero causare problemi, come illustrato nella figura 5.

![Esecuzione di riparazioni. ](images/sdt-desk-5.png)
 *Figura 5. Esecuzione di riparazioni*
<span id="logs" />

### <a name="generating-logs-for-analyzing-issues"></a>Generazione di log per l'analisi dei problemi 

SDT offre un ampio supporto per la diagnosi abilitata per i log tra applicazioni, driver, hardware e problemi del sistema operativo, come illustrato nella figura 6.

![Generazione di log. ](images/sdt-desk-6.png)
 *Figura 6. Generazione di log*

<span id="detailed-report" />

### <a name="generating-detailed-report-comparing-device-vs-optimal-configuration"></a>Generazione di report dettagliati sul confronto tra dispositivo e configurazione ottimale

In base ai log, SDT genera un report per i problemi basati su software e firmware che è possibile salvare in una posizione preferita.

## <a name="related-topics"></a>Argomenti correlati

- [Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi](surface-diagnostic-toolkit-command-line.md)


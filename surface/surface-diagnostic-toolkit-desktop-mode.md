---
title: Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop
description: Come usare SDT per aiutare gli utenti dell'organizzazione a eseguire lo strumento per identificare e diagnosticare i problemi con il dispositivo Surface e inviare richieste di supporto direttamente dallo strumento.
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
ms.openlocfilehash: 8b113d16f2053fe0904518b2643f1bafeaebdf64
ms.sourcegitcommit: 5448f775d3fe177806fce6cbaf0b2b091ed8b7d1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "11145941"
---
# Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop

Questo argomento spiega come usare Surface Diagnostic Toolkit (SDT) per aiutare gli utenti dell'organizzazione a eseguire lo strumento per identificare e diagnosticare i problemi relativi al dispositivo Surface, nonché inviare richieste di supporto direttamente dallo strumento. 

L'uso di SDT può determinare rapidamente se un problema segnalato è causato da un errore hardware o utente non riuscito. Per un elenco dei dispositivi Surface supportati in SDT, vedere [distribuire Toolkit di diagnostica superficie per le aziende](surface-diagnostic-toolkit-business.md).


1. Indirizzare l'utente all'installazione [del pacchetto SDT](surface-diagnostic-toolkit-business.md#preparing-the-sdt-package-for-distribution)da un punto di distribuzione del software o da una condivisione di rete. Dopo l'installazione, sei pronto per guidare l'utente tramite una serie di test. 

2. Iniziare nella Home page, che consente agli utenti di immettere una descrizione del problema e fare clic su **continua**, come illustrato nella figura 1.

    ![Avviare SDT in modalità desktop ](images/sdt-desk-1.png)
 *Figura 1. SDT in modalità desktop*

3. Quando SDT indica che il dispositivo contiene gli aggiornamenti più recenti, fare clic su **continua** per passare al catalogo dei test disponibili, come illustrato nella figura 2.

    ![Selezionare le opzioni di SDT ](images/sdt1.png)
 *nella figura 2. Selezionare le opzioni di SDT*

4. Puoi scegliere di eseguire tutti i test diagnostici. In alternativa, se si sospetta già di avere un problema specifico, ad esempio un errore di visualizzazione o un problema di alimentazione, fare clic su **Seleziona** per scegliere tra i test disponibili e fare clic su **Esegui selezionato**, come illustrato nella figura 3. Per informazioni dettagliate su ogni test, vedere la tabella seguente. 

    ![Selezionare test hardware ](images/sdt2.png)
 *nella figura 3. Selezionare test hardware*

    Test hardware | Descrizione
    --- | ---
    Alimentatore e batteria |  Controlla che l'alimentatore funzioni in modo ottimale
    Visualizzazione e audio   | Controlla la luminosità, i pixel bloccati o morti, il funzionamento dell'altoparlante e del microfono
    Porte e accessori   | Controlla gli accessori, l'Allegatura dello schermo e il funzionamento USB
    Connectivity |  Controlla la connettività Bluetooth, wireless e LTE
    Sicurezza    | Verifica i problemi relativi alla sicurezza
    Touch screen   | Verifica i problemi relativi al tocco
    Tastiera e tocco |    Controlla la connessione della tastiera integrata e il tipo di copertina
    Sensori | Verifica il funzionamento di sensori diversi nel dispositivo
    Hardware |  Verifica i problemi relativi a componenti hardware diversi, ad esempio la scheda grafica e la fotocamera

5. Al termine di tutti i test, lo strumento chiede di verificare se il problema è stato risolto. 

 ![Il problema è stato risolto? ](images/sdt3.png)
 *Figura 3A. il problema è stato risolto?*

6. Se il problema non è stato risolto o non si sa, è possibile inviare un ticket di supporto selezionando **Contattaci** per **ottenere assistenza ora.**
 
 ![Inviare un ticket di supporto ](images/sdt4.png)
 *Figura 3b. inviare un ticket di supporto*

<span id="multiple" />

## Eseguire più test hardware per la risoluzione dei problemi

SDT è progettato come strumento interattivo che esegue una serie di test. Per ogni test, SDT fornisce istruzioni che riepilogano la natura del test e gli elementi che gli utenti devono aspettarsi o cercare per avere successo nel test. Ad esempio, per diagnosticare se la luminosità dello schermo funziona correttamente, l'SDT inizia da zero e aumenta la luminosità in 100%, chiedendo agli utenti di confermare, rispondendo **Sì** o **No** , che la luminosità funziona come previsto, come illustrato nella figura 4. 

Per ogni test, se la funzionalità non funziona come previsto e l'utente fa clic su **No**, SDT genera un report delle possibili cause e dei modi per risolverlo. 

![Eseguire la diagnostica hardware ](images/sdt-desk-4.png)
 *nella figura 4. Diagnostica hardware in uso*

1. Se la luminosità viene modificata correttamente da 0-100 per cento come previsto, è possibile fare clic su **Sì** e quindi su **continua**. 
2. Se la luminosità non riesce a regolare da 0-100 per cento come previsto, indirizzare l'utente a fare clic su **No** e quindi su **continua**. 
3. Guida gli utenti con i test rimanenti, in base alle esigenze. Al termine, SDT fornisce automaticamente un riepilogo di alto livello del report, incluse le possibili cause di eventuali problemi hardware, oltre alle indicazioni per la risoluzione.


### Ripristino delle applicazioni

SDT consente di diagnosticare e ripristinare le applicazioni che potrebbero causare problemi, come illustrato nella figura 5.

![Eseguire le riparazioni ](images/sdt-desk-5.png)
 *Figura 5. Eseguire le riparazioni*
<span id="logs" />

### Generazione di log per l'analisi dei problemi 

SDT offre il supporto completo per la diagnosi del log in tutte le applicazioni, i driver, l'hardware e i problemi del sistema operativo, come illustrato nella figura 6.

![Generazione di log ](images/sdt-desk-6.png)
 *nella figura 6. Generazione di registri*

<span id="detailed-report" />

### Generazione di report dettagliati rispetto alla configurazione ottimale dei dispositivi

In base ai log, SDT genera un report per i problemi basati su software e firmware che è possibile salvare in una posizione preferita.

## Argomenti correlati

- [Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi](surface-diagnostic-toolkit-command-line.md)


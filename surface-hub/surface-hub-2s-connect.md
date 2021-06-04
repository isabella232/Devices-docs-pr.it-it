---
title: Connessione dei dispositivi a Surface Hub 2S
description: Questa pagina spiega come connettere dispositivi esterni a Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/24/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 1c4f9b4a74b50edb5587185f28a18163a02d62f9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833326"
---
# Connessione dei dispositivi a Surface Hub 2S
Surface Hub 2S consente di connettere dispositivi esterni, rispecchiare la visualizzazione su Surface Hub 2S in un altro dispositivo e connettere più periferiche di terze parti, tra cui videocamere videoconferenze, telefoni per conferenze e dispositivi per sistemi room.

È possibile visualizzare il contenuto dei dispositivi in Surface Hub 2S. Se il dispositivo di origine è basato su Windows, il dispositivo può anche specificare TouchBack e InkBack, che consente di ottenere video e audio dal dispositivo connesso e li presenta in Surface Hub 2S. Se Surface Hub 2S incontra un segnale HDCP (High-bandwidth Digital Content Protection), ad esempio un lettore Blu-ray DVD, la sorgente viene visualizzata come immagine nera.

> [!NOTE]
> Surface Hub 2S usa l'input video selezionato fino a quando non viene effettuata una nuova connessione, la connessione esistente viene interrotta oppure l'app Connect viene chiusa.

##  <a name="recommended-wired-configurations"></a>Configurazioni cablate consigliate 

In generale, è consigliabile usare connessioni via cavo native quando possibile, ad esempio da USB-C a USB-C o da HDMI a HDMI. Altre combinazioni come MiniDP a HDMI o MiniDP a USB-C funzioneranno anche. Potrebbe essere necessaria una configurazione aggiuntiva per ottimizzare l'esperienza di uscita video, come descritto in questa pagina.

| **Connessione** | **Funzionalità** | **Descrizione**|
| --- | --- | ---|
| HDMI + USB-C | HDMI-in per audio e video<br><br>USB-C per TouchBack e InkBack | USB-C supporta TouchBack e InkBack con la connessione HDMI A/V.<br><br>Usare USB-C per USB-a per connettersi a computer legacy.<br><br>**Nota:** Per ottenere risultati ottimali, connettere HDMI prima di connettere un cavo USB-C. Se il computer usato per HDMI non è compatibile con TouchBack e InkBack, non è necessario un cavo USB-C. |
| USB-C <br> (tramite il modulo Compute) | Video in <br>Audio-in | Cavo singolo necessario per un/V<br><br>TouchBack e InkBack è supportato<br><br>HDCP abilitato |
| HDMI (in porta) | Video, audio in Surface Hub 2S | Cavo singolo necessario per un/V<br><br>TouchBack e InkBack non sono supportati<br><br>HDCP abilitato |
| Output di MiniDP 1,2 | Video-out, ad esempio il mirroring di un proiettore più grande. | Cavo singolo necessario per un/V |

Quando si connette un computer guest a Surface Hub 2S tramite la porta USB-C, vengono individuati e configurati diversi dispositivi USB. Questi dispositivi periferici vengono creati per TouchBack e InkBack. Come illustrato nella tabella seguente, i dispositivi periferici possono essere visualizzati in gestione dispositivi, in cui verranno visualizzati i nomi duplicati per alcuni dispositivi, come illustrato nella tabella seguente.

 
|**Periferica**| **Elenco in gestione dispositivi** |
| ---------------------------- |------------- | ------------------------------|
| Dispositivi HID (Human Interface Device) | Dispositivo controllo consumi compatibile HID<br>Penna compatibile HID<br>Penna compatibile HID (elemento duplicato)<br>Penna compatibile HID (elemento duplicato)<br>Touch screen compatibile HID<br>Dispositivo di input USB<br>Dispositivo di input USB (elemento duplicato) |
| Tastiere | Tastiera standard PS/2 |
| Mouse e altri dispositivi di puntamento | Mouse compatibile HID |
| Controller USB | Hub USB generico<br>Dispositivo USB composito |

##  <a name="connecting-video-in-to-surface-hub-2s"></a>Connessione di video-in a Surface Hub 2S

È possibile inserire il video in Surface Hub 2S usando USB-C o HDMI, come indicato nella tabella seguente.  

###  <a name="surface-hub-2s-video-in-settings"></a>Impostazioni di Surface Hub 2S video-in

| **Tipo di segnale** | **Risoluzione** | **Frequenza dei fotogrammi** | **HDMI** | **USB-C** |
| --------------- | -------------- | -------------- | -------- | --------- |
| PC              | 640 x 480      | 60             | X        | X         |
| PC              | 720 x 480      | 60             | X        | X         |
| PC              | 1024 x 768     | 60             | X        | X         |
| PC              | 1920 x 1080    | 60             | X        | X         |
| PC              | 3840x2560      | 30             | X        | X         |
| HDTV            | 720p           | 60             | X        | X         |
| HDTV            | 1080p          | 60             | X        | X         |
| 4K UHD          | 3840x2560      | 30             | X        | X         |

> [!NOTE]
> La risoluzione 4K UHD (3840 × 2560) è supportata solo quando si esegue la connessione alle porte nel modulo COMPUTE. Non è supportata nelle porte USB "Guest" situate sul lato sinistro, superiore e destro del dispositivo.

> [!NOTE]
> Il video da un PC esterno connesso può sembrare più piccolo quando viene visualizzato in Surface Hub 2S.

##  <a name="mirroring-surface-hub-2s-display-on-another-device"></a>Hub superficie speculare 2S visualizzato in un altro dispositivo

È possibile eseguire il video di output in un altro schermo usando MiniDP, come indicato nella tabella seguente.

###  <a name="surface-hub-2s-video-out-settings"></a>Impostazioni di Surface Hub 2S video-out

| **Tipo di segnale** | **Risoluzione** | **Frequenza dei fotogrammi** | **MiniDP** |
| --------------- | -------------- | -------------- | ---------- |
| PC              | 640 x 480      | 60             | X          |
| PC              | 720 x 480      | 60             | X          |
| PC              | 1024 x 768     | 60             | X          |
| PC              | 1920 x 1080    | 60             | X          |
| PC              | 3840 x 2560    | 60             | X          |
| HDTV            | 720p           | 60             | X          |
| HDTV            | 1080p          | 60             | X          |
| 4K UHD          | 3840 x 2560    | 60             | X          |


 
Surface Hub 2S include una porta di uscita video MiniDP per proiettare il contenuto visivo da Surface Hub 2S a un altro schermo. Se si prevede di usare Surface Hub 2S per proiettarlo in un'altra visualizzazione, tenere presente quanto segue:

- **Tastiera necessaria.** Prima di iniziare, è necessario connettere una tastiera esterna con cavo o Bluetooth per Surface Hub 2S. Tieni presente che, diversamente dall'originale Hub Surface, una tastiera per Surface Hub 2S viene venduta separatamente e non è inclusa nel pacchetto di spedizione.<br><br>
- **Impostare la modalità duplicata.** Surface Hub 2S supporta l'uscita video solo in modalità duplicata. Tuttavia, sarà comunque necessario configurare manualmente la modalità di visualizzazione quando ci si connette per la prima volta:
    1. Immettere il **tasto Windows**  +  **P**, che apre il riquadro del progetto sul lato destro di Surface Hub 2S e quindi selezionare modalità **Duplica** .
    2. Al termine della sessione di Surface Hub 2S, selezionare **Termina sessione**. In questo modo si garantisce che l'impostazione duplicata venga salvata per la sessione successiva.<br><br>
- **Pianificare per proporzioni diverse.** Come altri dispositivi Surface, Surface Hub 2S usa una proporzioni di visualizzazione di 3:2 (la relazione tra la larghezza e l'altezza dello schermo). È supportata la proiezione del mozzo della superficie 2S su schermi con proporzioni diverse. Si noti tuttavia che, dato che il valore di Surface Hub 2S duplica lo schermo, l'output di MiniDP viene visualizzato solo in un rapporto di 3:2, che può causare la letterbox o il sipario a seconda delle proporzioni dello schermo di ricezione. 

> [!NOTE]
> Se il secondo monitor usa un rapporto di proporzioni 16:9 (il rapporto predominante per la maggior parte dei monitor TV), le barre nere potrebbero essere visualizzate sul lato sinistro e destro dello schermo con mirroring. In questo caso, potresti voler informare gli utenti che non è necessario modificare la seconda visualizzazione.

##  <a name="selecting-cables"></a>Selezione di cavi

Tenere presente i suggerimenti seguenti:

- **USB.** Cavi USB 3,1 gen 2.
- **MiniDP.** Cavi DisplayPort certificati per un massimo di 3 metri di lunghezza.
- **HDMI.** Se è necessario un cavo lungo, è consigliabile usare HDMI per l'ampia disponibilità di cavi a lunga distanza e convenienti, con la possibilità di installare i ripetitori, se necessario.

> [!NOTE]
> La maggior parte delle origini DisplayPort passa automaticamente alla segnalazione HDMI se viene rilevato HDMI.

##  <a name="wirelessly-connect-to-surface-hub-2s"></a>Connettersi in modalità wireless a Surface Hub 2S

Windows 10 supporta nativamente Miracast, che consente di connettersi senza fili a Surface Hub 2S.<br><br>

###  <a name="to-connect-using-miracast"></a>Per connettersi tramite Miracast:

1. Nel dispositivo Windows 10 immettere il **tasto logo Windows**  +  **K**. 
2. Nella finestra Connetti cercare il nome del mozzo della superficie 2S nell'elenco dei dispositivi vicini. Puoi trovare il nome dell'hub di Surface 2S nell'angolo in basso a sinistra dello schermo.
3. Immettere un PIN se l'amministratore di sistema ha abilitato l'impostazione PIN per le connessioni Miracast. Questo richiede l'immissione di un numero PIN quando ci si connette a Surface Hub 2S per la prima volta.

> [!NOTE]
>Se il nome del dispositivo Surface Hub 2S non viene visualizzato come previsto, è possibile che la sessione precedente sia stata chiusa prematuramente. In questo caso, accedere direttamente a Surface Hub 2S per terminare la sessione precedente e quindi connettersi dal dispositivo esterno.

##  <a name="connecting-peripherals-to-surface-hub-2s"></a>Connettere le periferiche a Surface Hub 2S

###  <a name="bluetooth-accessories"></a>Accessori Bluetooth

È possibile connettere gli accessori seguenti a Surface Hub-2S tramite Bluetooth:

- Mouse
- Tastiere
- Auricolari
- Altoparlanti
- Penne Surface Hub 2

> [!NOTE]
> Dopo aver connesso un auricolare o un altoparlante Bluetooth, potrebbe essere necessario modificare le impostazioni predefinite del microfono e dell'altoparlante. Per altre informazioni, vedere [**gestione locale per le impostazioni di Surface Hub**](https://docs.microsoft.com/surface-hub/local-management-surface-hub-settings).

---
title: Connessione dei dispositivi a Surface Hub 2S
description: Questa pagina illustra come connettere i dispositivi esterni a Surface Hub 2S.
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
ms.openlocfilehash: e3d1aa79ad056e790d5dc6a46f299cbaa9b5f9b0
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497476"
---
# <a name="connect-devices-to-surface-hub-2s"></a>Connessione dei dispositivi a Surface Hub 2S

Surface Hub 2S consente di connettere dispositivi esterni, eseguire il mirroring dello schermo su Surface Hub 2S a un altro dispositivo e connettere più periferiche di terze parti, tra cui videocamere per conferenze, telefoni per conferenze e dispositivi di sistema della sala.

È possibile visualizzare il contenuto dai dispositivi a Surface Hub 2S. Se il dispositivo di origine è basato su Windows, tale dispositivo può anche fornire TouchBack e InkBack, che acquisisce video e audio dal dispositivo connesso e li presenta su Surface Hub 2S. Se Surface Hub 2S rileva un segnale HDCP (Digital Content Protection) High-Bandwidth, ad esempio un lettore DVD Blu-ray, l'origine viene visualizzata come immagine nera.

> [!NOTE]
> Surface Hub 2S usa l'input video selezionato fino a quando non viene stabilita una nuova connessione, la connessione esistente viene interrotta o l'app Connessione viene chiusa.

## <a name="recommended-wired-configurations"></a>Configurazioni cablate consigliate 

In generale, è consigliabile usare connessioni via cavo native quando possibile, ad esempio da USB-C a USB-C o da HDMI a HDMI. Funzioneranno anche altre combinazioni come Da MiniDP a HDMI o Da MiniDP a USB-C. Potrebbe essere necessaria una configurazione aggiuntiva per ottimizzare l'esperienza di uscita video, come descritto in questa pagina.

| **Connessione** | **Funzionalità** | **Descrizione**|
| --- | --- | ---|
| HDMI + USB-C | HDMI-in per audio e video<br><br>USB-C per TouchBack e InkBack | USB-C supporta TouchBack e InkBack con la connessione HDMI A/V.<br><br>Usare da USB-C a USB-A per connettersi ai computer legacy.<br><br>**NOTA:** Per ottenere risultati ottimali, connettere HDMI prima di collegare un cavo USB-C. Se il computer in uso per HDMI non è compatibile con TouchBack e InkBack, non sarà necessario un cavo USB-C. |
| USB-C <br> (tramite modulo di calcolo) | Video-in <br>Audio-in | Cavo singolo necessario per A/V<br><br>TouchBack e InkBack sono supportati<br><br>HDCP abilitato |
| HDMI (in porta) | Video, Audio in Surface Hub 2S | Cavo singolo necessario per A/V<br><br>TouchBack e InkBack non supportati<br><br>HDCP abilitato |
| Output MiniDP 1.2 | Video-out come il mirroring in un proiettore più grande. | Cavo singolo necessario per A/V |

Quando si connette un computer guest a Surface Hub 2S tramite la porta USB-C, vengono individuati e configurati diversi dispositivi USB. Questi dispositivi periferici vengono creati per TouchBack e InkBack. Come illustrato nella tabella seguente, i dispositivi periferici possono essere visualizzati in Gestione dispositivi, che mostrerà nomi duplicati per alcuni dispositivi, come illustrato nella tabella seguente.

 
|**Periferica**| **Elenco in Gestione dispositivi** |
| ---------------------------- |------------- | ------------------------------|
| Dispositivi HID (Human Interface Device) | Dispositivo controllo consumi compatibile HID<br>Penna compatibile HID<br>Penna compatibile HID (elemento duplicato)<br>Penna compatibile HID (elemento duplicato)<br>Touch screen compatibile HID<br>Dispositivo di input USB<br>Dispositivo di input USB (elemento duplicato) |
| Tastiere | Tastiera standard PS/2 |
| Mouse e altri dispositivi di puntamento | Mouse compatibile HID |
| Controller USB | Hub USB generico<br>Dispositivo USB composito |

## <a name="connecting-video-in-to-surface-hub-2s"></a>Connessione del video-in a Surface Hub 2S

È possibile inserire video in Surface Hub 2S usando USB-C o HDMI, come indicato nella tabella seguente.  

### <a name="surface-hub-2s-video-in-settings"></a>Surface Hub impostazioni di video-in 2S

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
> La risoluzione UHD 4K (3840×2560) è supportata solo quando ci si connette alle porte nel modulo di calcolo. Non è supportato sulle porte USB "guest" che si trovano sui lati sinistro, superiore e destro del dispositivo.

> [!NOTE]
> Il video da un PC esterno connesso può apparire più piccolo se visualizzato in Surface Hub 2S.

## <a name="mirroring-surface-hub-2s-display-on-another-device"></a>Mirroring Surface Hub visualizzazione 2S in un altro dispositivo

È possibile inviare video a un altro display usando MiniDP, come indicato nella tabella seguente.

### <a name="surface-hub-2s-video-out-settings"></a>Surface Hub impostazioni di videoout 2S

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


 
Surface Hub 2S include una porta di uscita video MiniDP per la proiezione di contenuto visivo da Surface Hub 2S a un altro schermo. Se si prevede di usare Surface Hub 2S per proiettare in un'altra visualizzazione, prendere nota delle raccomandazioni seguenti:

- **Tastiera necessaria.** Prima di iniziare, è necessario connettere una tastiera esterna cablata o abilitata per Bluetooth a Surface Hub 2S. Si noti che, a differenza del Surface Hub originale, una tastiera per Surface Hub 2S viene venduta separatamente e non è inclusa nel pacchetto di spedizione.<br><br>
- **Impostare la modalità duplicata.** Surface Hub 2S supporta il video out solo in modalità duplicata. Tuttavia, sarà comunque necessario configurare manualmente la modalità di visualizzazione quando ci si connette per la prima volta:
    1. Immettere il **Windows tasto logoP** + , che apre il riquadro Project sul lato destro di Surface Hub 2S, quindi selezionare **Modalità duplica**.****
    2. Al termine della sessione Surface Hub 2S, selezionare **Fine sessione**. In questo modo si garantisce che l'impostazione duplicata venga salvata per la sessione successiva.<br><br>
- **Pianificare proporzioni diverse.** Come altri dispositivi Surface, Surface Hub 2S usa proporzioni di visualizzazione 3:2 (la relazione tra la larghezza e l'altezza dello schermo). È supportata la proiezione Surface Hub 2S su schermi con proporzioni diverse. Si noti tuttavia che, poiché Surface Hub 2S duplica la visualizzazione, anche l'output MiniDP verrà visualizzato solo in proporzioni 3:2, il che può comportare la creazione di lettere o tende a seconda delle proporzioni del display ricevente. 

> [!NOTE]
> se il secondo monitor usa proporzioni 16:9 (il rapporto predominante per la maggior parte dei monitor TV), è possibile che vengano visualizzate barre nere sui lati sinistro e destro dello schermo con mirroring. In questo caso, è possibile informare gli utenti che non è necessario modificare il secondo display.

## <a name="selecting-cables"></a>Selezione dei cavi

Si noti quanto segue:

- **USB.** Cavi USB 3.1 Gen 2.
- **MiniDP.** Cavi DisplayPort certificati per una lunghezza massima di 3 metri.
- **HDMI.** Se è necessario un cavo lungo, è consigliato HDMI a causa dell'ampia disponibilità di cavi a lungo raggio convenienti con la possibilità di installare ripetitori, se necessario.

> [!NOTE]
> La maggior parte delle origini DisplayPort passa automaticamente alla segnalazione HDMI se viene rilevato HDMI.

## <a name="wirelessly-connect-to-surface-hub-2s"></a>Connessione wireless a Surface Hub 2S

Windows 10/11 supporta in modo nativo Miracast, che consente la connessione wireless a Surface Hub 2S.<br><br>

### <a name="to-connect-using-miracast"></a>Per connettersi usando Miracast:

1. Nel dispositivo Windows 10/11 immettere **Windows tasto logoK** + .**** 
2. Nella finestra Connessione cercare il nome del Surface Hub 2S nell'elenco dei dispositivi vicini. È possibile trovare il nome del Surface Hub 2S nell'angolo inferiore sinistro dello schermo.
3. Immettere un PIN se l'amministratore di sistema ha abilitato l'impostazione PIN per le connessioni Miracast. È quindi necessario immettere un numero PIN quando ci si connette per la prima volta a Surface Hub 2S.

> [!NOTE]
>Se non viene visualizzato il nome del dispositivo Surface Hub 2S come previsto, è possibile che la sessione precedente sia stata chiusa prematuramente. In tal caso, accedere direttamente a Surface Hub 2S per terminare la sessione precedente e quindi connettersi dal dispositivo esterno.

## <a name="connecting-peripherals-to-surface-hub-2s"></a>Connessione di periferiche a Surface Hub 2S

### <a name="bluetooth-accessories"></a>Accessori Bluetooth

È possibile connettere gli accessori seguenti a Surface Hub-2S usando Bluetooth:

- Mouse
- Tastiere
- Auricolari
- Altoparlanti
- Surface Hub 2 penne

> [!NOTE]
> Dopo aver connesso un auricolare o un altoparlante Bluetooth, potrebbe essere necessario modificare le impostazioni predefinite del microfono e dell'altoparlante. Per altre informazioni, vedi [Gestione locale per le impostazioni di Surface Hub](local-management-surface-hub-settings.md).

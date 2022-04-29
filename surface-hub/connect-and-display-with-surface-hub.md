---
title: Connettere altri dispositivi e vederne i contenuti con Surface Hub
description: Puoi connettere un altro dispositivo a Surface Hub per visualizzarne i contenuti.
ms.assetid: 8BB80FA3-D364-4A90-B72B-65F0F0FC1F0D
ms.reviewer: ''
manager: laurawi
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: b176b4cce07d28bcd9b6d07c7fe1f91992910620
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497349"
---
# <a name="connect-other-devices-and-display-with-surface-hub"></a>Connettere altri dispositivi e vederne i contenuti con Surface Hub

Puoi connettere altri dispositivi a Microsoft Surface Hub per visualizzarne i contenuti. In questo argomento viene descritta la modalità Guest, la modalità PC sostitutivo e la funzionalità Uscita video disponibile tramite connessioni cablate e sono elencati anche gli accessori che è possibile connettere a Surface Hub utilizzando il [Bluetooth](#bluetooth-accessories).

>[!NOTE]
>Surface Hub userà l'input video selezionato fino a quando non viene stabilita una nuova connessione, la connessione esistente viene interrotta o l'app Connessione viene chiusa.

## <a name="which-method-should-i-choose"></a>Quale metodo devo scegliere?

Sono disponibili diverse opzioni per la connessione di dispositivi esterni e schermi a Surface Hub. Il metodo usato dipende dallo scenario e dalle specifiche esigenze.

| Per: | Usa questo metodo: |
| --- | --- |
| Eseguire il mirroring dello schermo del dispositivo Surface Hub su un altro dispositivo. | [Uscita video](#video-out) |
| Presentare lo schermo di un altro dispositivo sullo schermo di Surface Hub e interagire con il contenuto del dispositivo e l'esperienza predefinita Surface Hub. | [Modalità Guest](#guest-mode) |
| Accendere il Surface Hub da un PC Windows 10 o Windows 11 esterno, disattivando il computer incorporato del Surface Hub. Fotocamere, microfoni, altoparlanti e altre periferiche vengono inviate al PC esterno, in aggiunta a penna e tocco. | [Modalità PC sostitutivo](#replacement-pc-mode) |

## <a name="guest-mode"></a>Modalità Guest

La modalità Guest usa una connessione cablata per consentire agli utenti di visualizzare i contenuti dei propri dispositivi su Surface Hub. Se il dispositivo di origine è basato su Windows, saranno disponibili anche le funzioni touchback e inkback. Il PC interno a Surface Hub riceve i dati audio e video dal dispositivo connesso e li presenta su Surface Hub. Se Surface Hub rileva un segnale High-Bandwidth Digital Content Protection (HDCP), l'origine verrà visualizzata come immagine nera. Per visualizzare il contenuto senza violare i requisiti HDCP, usa il tastierino numerico sul lato destro di Surface Hub per scegliere direttamente l'origine esterna.

>[!NOTE]
>Quando è connessa un'origine HDCP, usa il tastierino laterale per cambiare l'input di origine.

### <a name="ports"></a>Porte

Per la modalità Guest è possibile usare una delle porte seguenti di Surface Hub.

| Interfaccia         | Tipo        | Descrizione        | Funzionalità                                                                                                                                                                      |
| ----------------- | ----------- | ------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Display Port 1.1a | Input video | Input guest n. 1     | - Supporto della visualizzazione dell'input guest simultaneo con l'input guest #2 e l'input guest n. 3 (una risoluzione completa, due anteprime).<br>- Conforme a HDCP in modalità bypass<br>- Touchback abilitato |
| HDMI 1.4          | Input video | Input guest n. 2     | - Supportare la visualizzazione dell'input guest simultaneo con l'input guest #1 e l'input guest n. 3 (una risoluzione completa, due anteprime).<br>- Conforme a HDCP in modalità bypass<br>- Touchback abilitato |
| VGA               | Input video | Input guest n. 3     | - Supporto della visualizzazione dell'input guest simultaneo con l'input guest #1 e l'input guest n. 2 (una risoluzione completa, due anteprime).<br>- Conforme a HDCP in modalità bypass<br>- Touchback abilitato |
| Jack da 3,5 mm       | Input audio | Input audio analogico | - Inserire in Surface Hub PC, in genere con l'input video VGA.                                                                                                                   |
| USB 2.0, tipo B   | Uscita USB     | Touchback          | - Fornisce l'accesso ai dispositivi di input HID mouse, tocco, tastiera e stilo al PC guest.                                                                               |

### <a name="port-locations"></a>Posizione delle porte

Queste sono le porte di connessione usate per la modalità Guest sui dispositivi Surface Hub da 55" e 84".

![Immagine delle porte Guest su Surface Hub da 55".](images/sh-55-guest-ports.png)

Porte per connessioni cablate sul dispositivo Surface Hub da 55"

![Immagine delle porte Guest su Surface Hub da 84".](images/sh-84-guest-ports.png)

Porte per connessioni cablate sul dispositivo Surface Hub da 84"

### <a name="port-enumeration"></a>Enumerazione delle porte

Quando un dispositivo Surface Hub viene connesso a un computer guest tramite la porta USB per connessioni cablate, viene identificato e configurato un certo numero di dispositivi USB. Questi dispositivi periferici vengono creati per le funzioni touchback e inkback e risultano visibili in Gestione dispositivi. Per alcuni di questi dispositivi vengono visualizzati nomi duplicati in Gestione dispositivi.

#### <a name="human-interface-devices"></a>Dispositivi HID (Human Interface Device)

- Dispositivo controllo consumi compatibile HID

- Penna compatibile HID

- Penna compatibile HID (elemento duplicato)

- Penna compatibile HID (elemento duplicato)

- Touch screen compatibile HID

- Dispositivo di input USB

- Dispositivo di input USB (elemento duplicato)

#### <a name="keyboards"></a>Tastiere

- Tastiera standard PS/2

#### <a name="mice-and-other-pointing-devices"></a>Mouse e altri dispositivi di puntamento

- Mouse compatibile HID

#### <a name="universal-serial-bus-controllers"></a>Controller USB (Universal Serial Bus)

- Hub USB generico

- Dispositivo USB composito

### <a name="guest-mode-connectivity"></a>Connettività in modalità Guest

La scelta del cavo video dipende dai contenuti trasmessi dall'input di origine. Il dispositivo Surface Hub supporta tre tipi di input video: DisplayPort, HDMI e VGA. Fai riferimento al grafico seguente per informazioni sulle risoluzioni disponibili.

| Tipo di segnale | Risoluzione | Frequenza dei fotogrammi | HDMI - RGB | DisplayPort | VGA |
| ----------- | ---------- | ---------- | ---------- | ----------- | --- |
| PC          | 640 x 480  | 59,94/60   | X          | X           | X   |
| PC          | 720 x 480  | 59,94/60   | X          | X           |     |
| PC          | 1024 x 768 | 60         | X          | X           | X   |
| HDTV        | 720p       | 59,94/60   | X          | X           | X   |
| HDTV        | 1080p      | 59,94/60   | X          | X           | X   |

L'audio di origine viene fornito dai cavi DisplayPort e HDMI. Se devi usare una connessione VGA, Surface Hub è dotato di una porta di input audio con un connettore da 3,5 mm. Surface Hub usa anche un cavo USB che fornisce touchback e inkback dal Surface Hub a dispositivi Windows 10 o Windows 11 compatibili. Il cavo USB può essere usato con qualsiasi input video già connesso con un cavo.

Gli utenti che scelgono la modalità Guest per connettere un PC possono usare una delle opzioni seguenti:

**DisplayPort**: cavo DisplayPort e cavo USB 2.0

**HDMI**: cavo HDMI e cavo USB 2.0

**VGA**: cavo VGA, cavo audio 3,5 mm e cavo USB 2.0

Se il computer connesso in modalità Guest non è compatibile con le funzionalità Touchback e Inkback, il cavo USB non è necessario.

## <a name="replacement-pc-mode"></a>Modalità PC sostitutivo

In modalità PC sostitutivo, il computer integrato in Surface Hub viene disattivato e un PC esterno viene connesso a Surface Hub. Le connessioni alle porte del PC sostitutivo consentono di accedere alle principali periferiche di Surface Hub, tra cui lo schermo, la penna e le funzionalità di tocco. Questo non significa che Surface Hub non tragga vantaggio dall'esperienza Windows Team, ma che sarà disponibile una maggiore flessibilità, offerta dalla possibilità di usare e gestire il proprio computer Windows.

### <a name="software-requirements"></a>Requisiti software

È possibile eseguire Surface Hub in modalità PC sostitutivo con versioni a 64 bit di Windows 10 o Windows 11 Home, Windows 10 o Windows 11 Pro e Windows 10 o Windows 11 Enterprise. Puoi scaricare il [pacchetto di driver per PC sostitutivi di Surface Hub](https://www.microsoft.com/download/details.aspx?id=52210) dall'area download Microsoft. Ti consigliamo di installare i driver in tutti i computer che intendi usare come PC sostitutivi.

### <a name="hardware-requirements"></a>Requisiti hardware

Surface Hub è compatibile con un'ampia gamma di componenti hardware. È sufficiente scegliere una combinazione di processore e memoria che consenta al PC sostitutivo di supportare i programmi che dovrai usare. L'hardware del PC sostitutivo deve supportare versioni a 64 bit di Windows 10 o Windows 11.

### <a name="graphics-adapter"></a>Scheda grafica

In modalità PC sostitutivo, Surface Hub supporta qualsiasi scheda grafica in grado di produrre un segnale DisplayPort. Per un'esperienza migliore si consiglia tuttavia una scheda grafica ottimizzata per la risoluzione e la frequenza di aggiornamento di Surface Hub. Per un uso ottimale di Surface Hub in modalità PC sostitutivo, è consigliato un segnale video a 120 Hz.

**Surface Hub da 55"**: per un'esperienza ottimale scegli una scheda grafica in grado di fornire una risoluzione di 1080p a 120 Hz.

**Surface Hub da 84"**: per un'esperienza ottimale, scegli una scheda grafica in grado di produrre quattro flussi DisplayPort 1.2 e garantire una risoluzione di 2160p a 120 Hz (3840 x 2160 con aggiornamento verticale di 120 Hz). È stato verificato il funzionamento del dispositivo con NVIDIA Quadro K2200, NVIDIA Quadro K4200, NVIDIA Quadro M6000, AMD FirePro W5100, AMD FirePro W7100 e AMD FirePro W9100. Queste non sono le uniche schede grafiche, altre sono disponibili da altri fornitori.

Per i driver più recenti contatta direttamente i fornitori delle rispettive schede grafiche.

| Fornitore scheda grafica | Pagina di download dei driver                                                           |
| --------------- | ------------------------------------------------------------------------------ |
| NVIDIA          | [http://nvidia.com/Download/index.aspx](http://nvidia.com/Download/index.aspx) |
| AMD             | [http://support.amd.com/en-us/download](http://support.amd.com/download) |
| Intel           | [https://downloadcenter.intel.com/](https://downloadcenter.intel.com/)         |

### <a name="replacement-pc-ports"></a>Porte PC sostitutive

Porte per PC sostitutivo su Surface Hub da 55"

![Immagine delle porte per PC sostitutivo su Surface Hub da 55"](images/sh-55-rpc-ports.png)

| Descrizione          | Tipo        | Interfaccia      | Dettagli                                                                                                                            |
| -------------------- | ----------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Video PC             | Input video | DP 1.2         | - Visualizzazione a schermo intero di 1080p a 120 Hz, più audio<br>- Conforme a HDCP                                                           |
| Periferiche interne | Uscita USB  | USB 2.0 tipo B | - Tocco<br>- Penna<br>- Relatori<br>- Microfono<br>- Fotocamere<br>- Sensore NFC<br>- Sensore di luce ambientale<br>- Sensore a infrarossi passivo |
| Hub USB              | Uscita USB  | USB 2.0 tipo B | - Sotto le porte USB                                                                                                             |

Porte per PC sostitutivo su Surface Hub da 84"

![Immagine delle porte per PC sostitutivo su Surface Hub da 84"](images/sh-84-rpc-ports.png)

| Descrizione          | Tipo        | Interfaccia      | Dettagli                                                                                                                            |
| -------------------- | ----------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
| Video PC             | Input video | DP 1.2 (2x)    | - Visualizzazione a schermo intero di 2160p a 120 Hz, più audio<br>- Conforme a HDCP                                                           |
| Periferiche interne | Uscita USB  | USB 2.0 tipo B | - Tocco<br>- Penna<br>- Relatori<br>- Microfono<br>- Fotocamere<br>- Sensore NFC<br>- Sensore di luce ambientale<br>- Sensore a infrarossi passivo |
| Hub USB              | Uscita USB  | USB 2.0 tipo B | - Sotto le porte USB                                                                                                             |

### <a name="replacement-pc-setup-instructions"></a>Istruzioni per l'installazione del PC sostitutivo

#### <a name="to-use-replacement-pc-mode"></a>Per usare la modalità PC sostitutivo

1. Scarica e installa sul PC sostitutivo il [pacchetto di driver per PC sostitutivi di Surface Hub](https://www.microsoft.com/download/details.aspx?id=52210).

    >[!NOTE]
    >Ti consigliamo di impostare la modalità di sospensione o ibernazione nel PC remoto in modo che lo schermo di Surface Hub si spenga automaticamente quando non viene usato.

2. Spegni Surface Hub mediante l'interruttore di alimentazione accanto al cavo di alimentazione.

3. Collega i cavi dalle porte per PC sostitutivo di Surface Hub al PC sostitutivo. Queste porte sono generalmente coperte da un coperchio rimovibile in plastica.

    55" Surface Hub: connettere un cavo DisplayPort e due cavi USB.

    84" Surface Hub: connettere due cavi DisplayPort e due cavi USB.

4. Imposta l'interruttore di modalità su **PC sostitutivo**. L'interruttore è accanto alle porte per PC sostitutivo.

5. Accendi Surface Hub mediante l'interruttore di alimentazione accanto al cavo di alimentazione.

6. Premi il pulsante di alimentazione sul lato destro di Surface Hub.

Puoi anche ripristinare Surface Hub alla modalità di utilizzo del PC interno.

#### <a name="to-switch-back-to-internal-pc"></a>Per tornare alla modalità di utilizzo del PC interno

1. Spegni Surface Hub mediante l'interruttore di alimentazione accanto al cavo di alimentazione.

2. Imposta l'interruttore di modalità su PC interno. L'interruttore è accanto alle porte per PC sostitutivo.

3. Accendi Surface Hub mediante l'interruttore di alimentazione accanto al cavo di alimentazione.

## <a name="video-out"></a>Uscita video

Surface Hub include una porta di uscita video per il mirroring del contenuto visivo da Surface Hub a un altro schermo.

### <a name="video-out-ports"></a>Porte di uscita video

Porta di uscita video su Surface Hub da 55"

![Illustrazione della porta di output video su 55" Surface Hub.](images/video-out-55.png)

Porta di uscita video su Surface Hub da 84"

![Illustrazione della porta di output video 84" Surface Hub.](images/video-out-84.png)

| Descrizione         | Tipo         | Interfaccia    | Funzionalità                                                                                                                                                                                                               |
| ------------------- | ------------ | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mirroring dell'uscita video | Uscita video | Uscita video | - Supporta la connessione a un monitor DisplayPort standard (supporta solo un collegamento x4 con risoluzione 1080p60 a 24bpp)<br>- Supporta l'uso con monitor HDMI (che supportano 1080p60) usando un adattatore DisplayPort-to-HDMI |

## <a name="cables"></a>Cavi

Entrambi i dispositivi Surface Hub da 55 e 84 pollici sono stati testati per funzionare con cavi certificati DisplayPort e HDMI.  Benché i fornitori vendano cavi più lunghi che potrebbero funzionare con Surface Hub, solo i cavi che sono stati certificati dai laboratori di test sono garantiti per funzionare con l'Hub. Ad esempio, i cavi DisplayPort sono certificati solo fino a 3 metri, ma molti fornitori vendono cavi di lunghezza tre volte superiore. Se è necessario un cavo lungo, è consigliabile usare un cavo HDMI.  HDMI ha molte soluzioni convenienti per i cavi prolungati, incluso l'uso dei ripetitori. Se viene rilevato un sink HDMI, quasi tutte le origini DisplayPort passeranno automaticamente alla segnalazione HDMI.

## <a name="bluetooth-accessories"></a>Accessori Bluetooth

È possibile connettere i seguenti accessori a Surface Hub utilizzando il Bluetooth:

- Mouse
- Tastiere
- Auricolari
- Altoparlanti

>[!NOTE]
>Dopo aver connesso un auricolare o un altoparlante Bluetooth, potrebbe essere necessario modificare le [impostazioni predefinite del microfono e dell'altoparlante](local-management-surface-hub-settings.md).

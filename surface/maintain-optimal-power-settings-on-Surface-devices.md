---
title: Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface
description: Questo argomento fornisce consigli pratici per la gestione delle impostazioni di potenza ottimali e spiega come l'area ottimizza l'esperienza di risparmio energia. Questo articolo si applica a tutti i dispositivi Surface attualmente supportati, tra cui Surface Pro 7, Surface Pro X e Surface laptop 3.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2019
ms.openlocfilehash: 73a74dc05a5a6929fa6360e04aac5d342b9c06a8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832511"
---
# Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface

I dispositivi Surface sono progettati per sfruttare i più recenti progressi nel consumo di energia dei dispositivi mobili per offrire un'esperienza semplificata ottimizzata tra i carichi di lavoro. A seconda di quello che si sta facendo, la superficie si sintonizza dinamicamente su come i singoli componenti hardware vengono riattivati momentaneamente per gestire le attività in background, ad esempio un messaggio di posta elettronica o un traffico di rete, prima di tornare a uno stato di inattività ridotta (S0ix).

## Riepilogo dei suggerimenti per gli amministratori IT

Per garantire che i dispositivi Surface in tutta l'organizzazione traggano vantaggio dalle caratteristiche di Power Optimization:

-  Installare i driver e il firmware più recenti da Windows Update o dal driver della superficie e dal firmware MSI. In questo modo, per impostazione predefinita, viene creato il Power Plan bilanciato (aka Power profile) e vengono configurate le impostazioni di potenza  Per altre informazioni, vedere [gestire e distribuire il driver della superficie e gli aggiornamenti del firmware](manage-surface-driver-and-firmware-updates.md).
- Evitare di creare profili di alimentazione personalizzati o di modificare le impostazioni di Power avanzate non visibili nell'interfaccia utente predefinita (**System**  >  **Power & Sleep**).
- Se è necessario gestire il profilo di alimentazione dei dispositivi in rete, ad esempio in organizzazioni altamente gestite, usare lo strumento di comando powercfg per esportare il piano di alimentazione dall'immagine di fabbrica del dispositivo Surface e quindi importarlo nel pacchetto di provisioning per i dispositivi Surface. 

    >[!NOTE]
    >È possibile esportare solo un piano di alimentazione in uno stesso tipo di dispositivo Surface.  Ad esempio, non è possibile esportare un Power Plan dal portatile Surface e importarlo in Surface Pro.  Per altre informazioni, vedere [configurare le impostazioni di risparmio energia](https://docs.microsoft.com/windows-hardware/customize/power-settings/configure-power-settings).

- Escludere i dispositivi Surface da eventuali impostazioni dei criteri di risparmio energia esistenti. 

## Background

Il modo in cui Surface implementa la gestione dell'alimentazione differisce significativamente rispetto allo standard precedente del sistema operativo che riduce gradualmente e disattiva l'alimentazione tramite una serie di Stati di sospensione; ad esempio, in bicicletta tra S1, S2, S3 e così via.

La superficie è invece un'immagine con un profilo di alimentazione personalizzato che sostituisce la funzionalità di sospensione e consumo di energia legacy con caratteristiche di standby moderne e una fine tuning dinamico. Questo profilo di alimentazione personalizzato viene implementato tramite il driver hub seriale Surface e il modulo aggregator di sistema (SAM). Il chip SAM funziona come proprietario dei criteri di alimentazione del dispositivo Surface, usando gli algoritmi per calcolare i requisiti di potenza ottimali. Funziona in combinazione con Windows Power Manager per allocare o limitare solo l'esatta quantità di energia necessaria per il funzionamento dei componenti hardware. Questo articolo si applica a tutti i dispositivi Surface attualmente supportati, tra cui Surface Pro 7, Surface Pro X e Surface laptop 3.

## Utilizzo del profilo di alimentazione personalizzato in Surface

Se si accede alle opzioni di Power in un dispositivo Surface, si noterà che è disponibile un unico piano di alimentazione. Questo è il profilo di alimentazione personalizzato. Se si passa alle impostazioni di Power avanzate, viene visualizzato un sottoinsieme molto più piccolo di opzioni di alimentazione rispetto a un PC generico che utilizza Windows 10. A differenza dei dispositivi generici, Surface include firmware e componenti personalizzati per gestire queste opzioni di risparmio energia.


## Standby moderno

Il profilo di alimentazione personalizzato algoritmicamente Embedded consente la connettività di standby moderna per Surface mantenendo uno stato di basso consumo per la funzionalità Instant on/Instant off tipica degli smartphone. S0ix, noto anche come lo stato della piattaforma di runtime inattivo più profondo (gocciola), è la modalità di alimentazione predefinita per i dispositivi Surface. La modalità standby moderna è composta da due modi:

- **Standby connesso.** La modalità predefinita per il recapito continuo di messaggi di posta elettronica, messaggistica e dati sincronizzati sul cloud, standby connesso mantiene la connessione Wi-Fi e mantiene la connettività di rete.

- **Standby disconnesso.** Una modalità facoltativa per la durata della batteria estesa, standby disconnessa offre la stessa esperienza immediata e consente di risparmiare energia disattivando Wi-Fi, Bluetooth e connettività di rete correlata.

Per altre informazioni sulla modalità standby moderna, vedere [Microsoft hardware Dev Center](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources).

## Razionalizzazione della superficie dell'esperienza di gestione del risparmio energia 

Surface integra le caratteristiche seguenti progettate per aiutare gli utenti a ottimizzare l'esperienza di gestione dell'alimentazione:

- [Power Plan singolare](#singular-power-plan)

- [Interfaccia utente di Power Settings semplificata](#simplified-power-settings-user-interface)

- [Dispositivo di scorrimento Power performance di Windows](#windows-performance-power-slider)

### Power Plan singolare

Surface è progettato per un'esperienza di gestione dell'alimentazione semplificata che elimina la necessità di creare piani di alimentazione personalizzati o configurare manualmente le impostazioni di Power. Microsoft ottimizza l'esperienza utente distribuendo un singolo Power Plan (bilanciato) che sostituisce i piani di alimentazione multipli dalle build standard di Windows.

### Interfaccia utente di Power Settings semplificata

Surface offre un'interfaccia utente semplificata in conformità con le raccomandazioni per l'impostazione dell'alimentazione ottimale. In generale, è consigliabile regolare solo le impostazioni visibili nell'interfaccia utente predefinita ed evitare di configurare impostazioni avanzate di Power Settings o criteri di gruppo. L'uso della schermata predefinita e dei timeout di sospensione per evitare i massimi livelli di luminosità è il modo più efficace per consentire agli utenti di mantenere la durata della batteria estesa.

![Figura 1. Impostazioni di Power & Sleep semplificate](images/powerintrofig1.png)

Figura 1. Impostazioni di alimentazione e sospensione semplificate

### Dispositivo di scorrimento Power performance di Windows

I dispositivi Surface che utilizzano Windows 10 Build 1709 e versioni successive includono un dispositivo di scorrimento di Power che consente di assegnare priorità alla durata della batteria, se necessario o a favore delle prestazioni. È possibile accedere a Power Slider dalla barra delle applicazioni facendo clic sull'icona della batteria. Scorrere a sinistra per ottenere una durata maggiore della batteria (modalità risparmio batteria) o scorrere verso destra per ottenere prestazioni più rapide.

![Figura 2. Power Slider](images/powerintrofig2a.png)

Figura 2. Power Slider

Power Slider consente quattro Stati come descritto nella tabella seguente:

| Modalità dispositivo di scorrimento| Descrizione |
|---|---|
| Risparmia batteria| Consente di risparmiare energia e prolungare la durata della batteria quando il sistema è disconnesso da una fonte di energia. Quando il risparmio batteria è attivo, alcune funzionalità di Windows sono disabilitate, limitate o si comportano in modo diverso. La luminosità dello schermo è anche ridotta. Il risparmio batteria è disponibile solo quando si usa la potenza della batteria (DC). Per altre informazioni, vedere [risparmio batteria](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver).|
| Consigliato | Garantisce una durata della batteria maggiore rispetto alle impostazioni predefinite nelle versioni precedenti di Windows. |
| Prestazioni migliori | Favorisce leggermente le prestazioni rispetto alla durata della batteria, funzionando come la modalità predefinita del dispositivo di scorrimento. |
| Prestazioni ottimali | Favorisce le prestazioni rispetto alla potenza per i carichi di lavoro che richiedono massime prestazioni e capacità di risposta, indipendentemente dal consumo di energia a batteria.|

Le modalità di Power Slider controllano direttamente componenti hardware specifici illustrati nella tabella seguente.

| Componente | Funzionalità del dispositivo di scorrimento |
|---|---|
| Intel Speed Shift (CPU Energy registers) e hint per le preferenze di prestazioni energetiche. | Seleziona la migliore frequenza e tensione operativa per ottenere prestazioni e potenza ottimali. La preferenza per le prestazioni energetiche (PERFEPP) è un suggerimento per l'efficienza di alimentazione globale della CPU. |
| Velocità ventola (RPM)| Se applicabile, consente di modificare le condizioni, ad esempio mantenere silenzioso il ventilatore in modalità dispositivo di scorrimento risparmio batteria.|
| Pacchetto di Power limits per il processore (PL1/PL2).| Richiede alla CPU di gestire le proprie scelte di frequenza per supportare un limite medio corrente per i carichi di lavoro di stato costante (PL1) e Turbo (PL2).|
| Limiti di frequenza Turbo del processore (limitazioni di IA Turbo). | Regola le prestazioni dei processori e della grafica per consentire ai core del processore di eseguire più rapidamente o più lentamente rispetto alla frequenza nominale.                                                |

>[!NOTE]
>Il dispositivo di scorrimento di Power è completamente indipendente dalle impostazioni di alimentazione del sistema operativo, sia configurato da pannello di controllo/opzioni di alimentazione, criteri di gruppo o metodi correlati.

Per altre informazioni, vedere:

-   [Personalizzare il dispositivo di scorrimento Power performance di Windows](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

-   [Risparmio batteria.](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)

## Procedure consigliate per la durata della batteria estesa


| Procedura consigliata | Vai a | Passaggi successivi |
|---|---|---|                                                                                                                                    
| Verificare che il dispositivo Surface sia aggiornato| Windows Update | Nella casella di ricerca sulla barra delle applicazioni digitare **Windows Update** e selezionare **Controlla aggiornamenti**. |
| Scegliere l'impostazione di potenza ottimale per le operazioni da eseguire | Power Slider | Nella barra delle applicazioni selezionare l'icona della batteria, quindi scegliere **prestazioni ottimali**, **durata ottimale della batteria**o da qualche parte in mezzo.|
| Risparmiare batteria quando è bassa | Risparmia batteria | Nella barra delle applicazioni selezionare l'icona batteria e fare clic su **Impostazioni batteria**. Selezionare **attiva automaticamente il risparmio batteria se la batteria scende** al di sotto e quindi il dispositivo di scorrimento si sposta più a destra per una durata più lunga. |
| Configurare la luminosità ottimale dello schermo | Risparmia batteria | Nella barra delle applicazioni selezionare l'icona batteria e fare clic su **Impostazioni batteria**, selezionare **luminosità inferiore dello schermo durante il risparmio batteria**. |
| Risparmiare energia ogni volta che non si è connessi | Risparmia batteria| Selezionare **attiva lo stato di risparmio batteria fino a carica successiva**.|
| Esaminare i problemi relativi alle impostazioni di alimentazione. | Strumento di risoluzione dei problemi di Power | Nella barra delle applicazioni cercare risoluzione dei problemi selezionare **risoluzione dei problemi**e quindi selezionare **alimentazione** e seguire le istruzioni.|
| Controllare l'utilizzo dell'app | Le tue app | Chiudere le app.|
| Controllare il cavo di alimentazione per eventuali danni.| Il cavo di alimentazione | Sostituire il cavo di alimentazione se usurato o danneggiato.|

## Scopri di più 

- [Standby moderno](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)

<!-- -->

- [Personalizzare il dispositivo di scorrimento Power performance di Windows](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

- [Risparmio batteria](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)
- [Gestire e distribuire gli aggiornamenti di driver e firmware Surface](manage-surface-driver-and-firmware-updates.md)

---
title: Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface
description: In questo argomento vengono forniti consigli sulle procedure consigliate per mantenere le impostazioni di risparmio energia ottimali e viene illustrato come Surface semplifica l'esperienza di gestione del risparmio energia. Questo articolo si applica a tutti i dispositivi Surface attualmente supportati, tra cui Surface Pro 7+, Surface Pro 7, Surface Pro X e Surface Laptop 3.
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
ms.date: 1/15/2021
ms.openlocfilehash: 23b94c865c43ad92b7ae6f047e980084760e4aed
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911751"
---
# <a name="best-practice-power-settings-for-surface-devices"></a>Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface

I dispositivi Surface sono progettati per sfruttare i più recenti progressi nel consumo di energia dei dispositivi mobili per offrire un'esperienza semplificata ottimizzata tra i carichi di lavoro. A seconda di ciò che stai facendo, Surface regola dinamicamente il flusso dell'alimentazione ai singoli componenti hardware, svegliando momentaneamente i componenti di sistema per gestire le attività in background, ad esempio un messaggio di posta elettronica in arrivo o il traffico di rete, prima di tornare a uno stato di inattività a basso consumo (S0ix).

## <a name="summary-of-recommendations-for-it-administrators"></a>Riepilogo dei suggerimenti per gli amministratori IT

Per garantire che i dispositivi Surface nell'organizzazione trarranno vantaggio dalle funzionalità di ottimizzazione dell'alimentazione di Surface:

-  Installa i driver e il firmware più recenti da Windows Update o dal file MSI surface driver e firmware. In questo modo viene creata la combinazione per il risparmio di energia bilanciata (anche noto come profilo di alimentazione) per impostazione predefinita e vengono configurate impostazioni di risparmio energia ottimali.  Per altre informazioni, fai riferimento a [Gestire e distribuire gli aggiornamenti del firmware e dei driver di Surface.](manage-surface-driver-and-firmware-updates.md)
- Evitare di creare profili di alimentazione personalizzati o di regolare le impostazioni avanzate di risparmio energia non visibili nell'interfaccia utente predefinita (**Alimentazione**  >  **di sistema & sospensione**).
- Se devi gestire il profilo di alimentazione dei dispositivi nella rete (ad esempio nelle organizzazioni altamente gestite), usa lo strumento di comando powercfg per esportare la combinazione per il risparmio di energia dall'immagine di fabbrica del dispositivo Surface e quindi importarla nel pacchetto di provisioning per i dispositivi Surface. 

    >[!NOTE]
    >Puoi esportare una combinazione per il risparmio di energia solo nello stesso tipo di dispositivo Surface.  Ad esempio, non è possibile esportare una combinazione per il risparmio di Surface Laptop e importarla in Surface Pro.  Per ulteriori informazioni, vedere [Configurare le impostazioni di risparmio energia.](https://docs.microsoft.com/windows-hardware/customize/power-settings/configure-power-settings)

- Escludere i dispositivi Surface da eventuali impostazioni dei criteri di risparmio energia esistenti. 

## <a name="background"></a>Background

Il modo in cui Surface implementa la gestione dell'alimentazione differisce in modo significativo dallo standard precedente del sistema operativo che riduce gradualmente e spegne l'alimentazione tramite una serie di stati di sospensione; ad esempio, ciclo attraverso S1, S2, S3 e così via.

Surface viene invece immagineta con un profilo di alimentazione personalizzato che sostituisce le funzionalità di sospensione e consumo di energia legacy con funzionalità di standby moderne e ottimizzazione dinamica. Questo profilo di alimentazione personalizzato viene implementato tramite il driver Surface Serial Hub e il modulo di aggregazione di sistema (SAM). Il chip SAM funziona come proprietario dei criteri di alimentazione dei dispositivi Surface, usando algoritmi per calcolare i requisiti di alimentazione ottimali. Funziona in combinazione con Windows power manager per allocare o limitazione solo la quantità esatta di energia necessaria per il funzionamento dei componenti hardware. Questo articolo si applica a tutti i dispositivi Surface attualmente supportati, tra cui Surface Pro 7+, Surface Laptop Go, Surface Pro 7, Surface Pro X e Surface Laptop 3.

## <a name="utilizing-the-custom-power-profile-in-surface"></a>Utilizzo del profilo di alimentazione personalizzato in Surface

Se si passa alle opzioni di alimentazione in un dispositivo Surface, si scoprirà che è disponibile una singola combinazione per il risparmio di energia. Questo è il profilo di alimentazione personalizzato. Se si passa alle impostazioni avanzate per il risparmio di energia, verrà visualizzato un sottoinsieme molto più piccolo di opzioni di risparmio energia rispetto a un PC generico che esegue Windows 10. A differenza dei dispositivi generici, Surface dispone di firmware e componenti personalizzati per gestire queste opzioni di alimentazione.


## <a name="modern-standby"></a>Standby moderno

Il profilo di alimentazione personalizzato incorporato algoritmicamente consente la connettività di standby moderna per Surface mantenendo uno stato di alimentazione basso per le funzionalità di accensione/interruzione istantanea tipiche degli smartphone. S0ix, noto anche come stato DRIPS (Deepest Runtime Idle Platform State), è la modalità di alimentazione predefinita per i dispositivi Surface. Lo standby moderno ha due modalità:

- **Standby connesso.** La modalità predefinita per il recapito di messaggi di posta elettronica, messaggistica e dati sincronizzati sul cloud, lo standby connesso mantiene attiva la Wi-Fi e mantiene la connettività di rete.

- **Standby disconnesso.** Una modalità facoltativa per una durata prolungata della batteria, lo standby disconnesso offre la stessa esperienza di attivazione istantanea e consente di risparmiare energia disattivando Wi-Fi, Bluetooth e connettività di rete correlata.

Per ulteriori informazioni sullo standby moderno, fare riferimento a [Microsoft Hardware Dev Center](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources).

## <a name="how-surface-streamlines-the-power-management-experience"></a>Come Surface semplifica l'esperienza di gestione del risparmio energia 

Surface integra le funzionalità seguenti progettate per aiutare gli utenti a ottimizzare l'esperienza di gestione del risparmio energia:

- [Combinazione per il risparmio di energia singolare](#singular-power-plan)

- [Interfaccia utente per le impostazioni di risparmio energia semplificate](#simplified-power-settings-user-interface)

- [Windows dispositivo di scorrimento per l'alimentazione delle prestazioni](#windows-performance-power-slider)

### <a name="singular-power-plan"></a>Combinazione per il risparmio di energia singolare

Surface è progettato per un'esperienza di gestione del risparmio energia semplificata che elimina la necessità di creare combinazioni per il risparmio di energia personalizzate o configurare manualmente le impostazioni di risparmio energia. Microsoft semplifica l'esperienza utente offrendo una singola combinazione per il risparmio di energia (bilanciata) che sostituisce le più combinazioni per il risparmio di energia dalle build Windows standard.

### <a name="simplified-power-settings-user-interface"></a>Interfaccia utente per le impostazioni di risparmio energia semplificate

Surface offre un'interfaccia utente semplificata in base alle procedure consigliate per l'impostazione dell'alimentazione. In generale, è consigliabile modificare solo le impostazioni visibili nell'interfaccia utente predefinita ed evitare di configurare impostazioni avanzate per il risparmio di energia o impostazioni di Criteri di gruppo. L'uso dei timeout predefiniti dello schermo e della sospensione evitando i livelli di luminosità massimi sono i modi più efficaci per mantenere la durata prolungata della batteria.

![Figura 1. Impostazioni di sospensione & risparmio energia semplificate.](images/powerintrofig1.png)

Figura 1. Impostazioni di alimentazione e sospensione semplificate

### <a name="windows-performance-power-slider"></a>Windows dispositivo di scorrimento per l'alimentazione delle prestazioni

I dispositivi Surface che Windows 10 build 1709 e versioni successive includono un dispositivo di scorrimento di alimentazione che consente di definire la priorità della durata della batteria quando necessario o di favorire le prestazioni se lo si desidera. Puoi accedere al dispositivo di scorrimento di alimentazione dalla barra delle applicazioni facendo clic sull'icona della batteria. Scorrere verso sinistra per una durata della batteria più lunga (modalità risparmio batteria) o scorrere verso destra per velocizzare le prestazioni.

![Figura 2. Dispositivo di scorrimento alimentazione.](images/powerintrofig2a.png)

Figura 2. Dispositivo di scorrimento alimentazione

Il dispositivo di scorrimento di alimentazione abilita quattro stati, come descritto nella tabella seguente:

| Modalità dispositivo di scorrimento| Descrizione |
|---|---|
| Risparmia batteria| Consente di risparmiare energia e prolungare la durata della batteria quando il sistema è scollegato da una fonte di alimentazione. Quando il risparmio batteria è attivata, alcune funzionalità Windows sono disabilitate, limitate o comportano in modo diverso. Anche la luminosità dello schermo è ridotta. Il risparmio batteria è disponibile solo quando si utilizza l'alimentazione a batteria (DC). Per ulteriori informazioni, vedere [Risparmio batteria.](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)|
| Consigliato | Garantisce una durata della batteria maggiore rispetto alle impostazioni predefinite nelle versioni precedenti di Windows. |
| Prestazioni migliori | Favorisce leggermente le prestazioni rispetto alla durata della batteria, funzionando come modalità dispositivo di scorrimento predefinita. |
| Prestazioni ottimali | Favorisce le prestazioni rispetto all'alimentazione per i carichi di lavoro che richiedono prestazioni e velocità di risposta massime, indipendentemente dal consumo di energia della batteria.|

Le modalità dispositivo di scorrimento di alimentazione controllano direttamente componenti hardware specifici illustrati nella tabella seguente.

| Componente | Funzionalità dispositivo di scorrimento |
|---|---|
| Intel Speed Shift (registri di energia della CPU) e suggerimento di preferenza per le prestazioni energetiche. | Seleziona la migliore frequenza operativa e la migliore tensione per prestazioni e potenza ottimali. La preferenza prestazioni energetiche (PERFEPP) è un suggerimento di efficienza energetica globale per la CPU. |
| Velocità ventola (RPM)| Se applicabile, regola le condizioni che cambiano, ad esempio per mantenere in silenzio la ventola in modalità dispositivo di scorrimento risparmio batteria.|
| Limiti di alimentazione del pacchetto del processore (PL1/PL2).| Richiede alla CPU di gestire le scelte di frequenza per supportare un limite di alimentazione medio in esecuzione sia per i carichi di lavoro a stato FISSO (PL1) che per i carichi di lavoro turbo (PL2).|
| Limiti di frequenza turbo del processore (limitazioni IA turbo). | Regola le prestazioni del processore e della grafica consentendo ai core del processore di essere eseguiti più velocemente o più lentamente rispetto alla frequenza operativa valutata.                                                |

>[!NOTE]
>Il dispositivo di scorrimento dell'alimentazione è completamente indipendente dalle impostazioni di risparmio energia del sistema operativo configurate dal Pannello di controllo/ Opzioni risparmio energia, da Criteri di gruppo o da metodi correlati.

Per ulteriori informazioni, vedere:

-   [Personalizzare il dispositivo Windows di alimentazione delle prestazioni](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

-   [Risparmio batteria.](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)

## <a name="best-practices-for-extended-battery-life"></a>Procedure consigliate per una durata prolungata della batteria


| Procedura consigliata | Vai a | Passaggi successivi |
|---|---|---|                                                                                                                                    
| Assicurati che il dispositivo Surface sia aggiornato| Windows Update | Nella casella di ricerca della barra delle applicazioni digita **Windows Aggiorna** e seleziona **Controlla aggiornamenti**. |
| Scegliere l'impostazione di risparmio energia migliore per le prestazioni | Dispositivo di scorrimento alimentazione | Nella barra delle applicazioni seleziona l'icona della batteria, quindi scegli **Prestazioni migliori,** **Durata migliore della batteria**o altrove.|
| Conservare la batteria quando è bassa | Risparmia batteria | Nella barra delle applicazioni seleziona l'icona della batteria e fai clic su **Impostazioni batteria.** Seleziona **Attiva automaticamente il risparmio batteria** se la batteria scende al di sotto e quindi sposta il dispositivo di scorrimento più a destra per una durata della batteria più lunga. |
| Configurare la luminosità ottimale dello schermo | Risparmia batteria | Nella barra delle applicazioni seleziona l'icona della batteria e fai clic su **Impostazioni batteria,** seleziona Luminosità dello schermo inferiore **mentre si salva batteria.** |
| Risparmiare energia ogni volta che non si è collegati | Risparmia batteria| Seleziona **Attiva stato risparmio batteria fino al successivo addebito.**|
| Analizzare i problemi relativi alle impostazioni di risparmio energia. | Risoluzione dei problemi di alimentazione | Nella ricerca della barra delle applicazioni per la risoluzione dei problemi seleziona **Risoluzione dei**problemi e quindi seleziona **Alimentazione** e segui le istruzioni.|
| Controllare l'utilizzo dell'app | Le tue app | Chiudi le app.|
| Verificare la presenza di eventuali danni al cavo di alimentazione.| Cavo di alimentazione | Sostituire il cavo di alimentazione se usurato o danneggiato.|

## <a name="learn-more"></a>Scopri di più 

- [Standby moderno](https://docs.microsoft.com/windows-hardware/design/device-experiences/modern-standby-wake-sources)

<!-- -->

- [Personalizzare il dispositivo Windows di alimentazione delle prestazioni](https://docs.microsoft.com/windows-hardware/customize/desktop/customize-power-slider)

- [Risparmio batteria](https://docs.microsoft.com/windows-hardware/design/component-guidelines/battery-saver)
- [Gestire e installare gli aggiornamenti di driver e firmware per Surface](manage-surface-driver-and-firmware-updates.md)

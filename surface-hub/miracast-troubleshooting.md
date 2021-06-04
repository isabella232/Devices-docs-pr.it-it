---
title: Risolvere i problemi relativi a Miracast su Surface Hub
description: Scopri come risolvere i problemi con Miracast su Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 96c7c42fe0176f275a8657165d88bf447e57772b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836952"
---
# Risolvere i problemi relativi a Miracast su Surface Hub

Surface Hub supporta la proiezione wireless tramite il protocollo Miracast. La maggior parte dei monitor e degli adattatori wireless disponibili attualmente usa l'implementazione originale di Miracast. Surface Hub usa una versione leggermente diversa di Miracast nota come **Miracast Autonomous Group Owner (AGO)**. Un passaggio comune della risoluzione dei problemi quando si verifica un errore di proiezione in modalità wireless su Surface Hub è quello di testare la proiezione wireless su un altro monitor o adattatore. Nella maggior parte dei casi, tuttavia, questi dispositivi non utilizzano Miracast AGO e non gestiscono la proiezione wireless nello stesso modo del dispositivo Surface Hub.

Nel Miracast tradizionale il dispositivo di proiezione connetterà il punto di accesso configurato dal monitor abilitato per Miracast, quindi il monitor invierà il traffico di nuovo al dispositivo di proiezione tramite il canale di rete del dispositivo di proiezione. Miracast AGO è un processo di connessione in due passaggi:

- Il primo passaggio è la connessione iniziale che utilizza 2,4 GHz. 
- Dopo tale handshake iniziale il dispositivo di proiezione invia il traffico al monitor utilizzando le impostazioni di canale wireless sul monitor. Se Surface Hub è connesso a una rete Wi-Fi, il punto di accesso, verrà utilizzato lo stesso canale della rete connessa; in caso contrario, verrà utilizzato il canale Miracast da Impostazioni.

A livello generale esistono due tipi di problemi con l'attività da Miracast a Surface Hub: [connessione](#connect-issues) e [prestazioni](#performance-issues). In entrambi i casi, è consigliabile ottenere un'immagine generale delle attività di rete wireless nella posizione dell'hub Surface. L'esecuzione di uno strumento di scansione della rete ti mostrerà le reti disponibili e l'utilizzo dei canali nell'ambiente.

## Problemi di connessione

Assicurati che sia Wi-Fi che Miracast sono abilitati in Impostazioni nel dispositivo Surface Hub. 

Se hai eseguito un'analisi di rete, dovresti vedere che Miracast di Surface Hub è elencato come punto di accesso. Se la rete Miracast di Surface Hub viene visualizzata nella scansione, ma non è possibile visualizzarla come dispositivo disponibile, è possibile provare a regolare il canale Miracast usato da Surface Hub. 

Quando Surface Hub è connesso a una rete Wi-Fi utilizzerà le stesse impostazioni di canale utilizzate dal punto di accesso Wi-Fi per il punto di accesso Miracast. Per la risoluzione dei problemi, scollega Surface Hub da tutte le reti Wi-Fi, ma mantieni il Wi-Fi abilitato, così puoi controllare il canale usato per Miracast. Puoi selezionare manualmente il canale Miracast in Impostazioni. Dovrai riavviare Surface Hub dopo ogni modifica. In generale, devi usare canali che per l'analisi di rete non presentino un utilizzo intenso.

È anche possibile che il problema di connessione possa essere il risultato di un problema nel dispositivo di connessione. Se nel dispositivo di proiezione è in esecuzione Windows, dovrebbe trattarsi di Windows 8.1 o di una versione successiva per il supporto completo di Miracast. Di nuovo, per la risoluzione dei problemi, disconnetti il dispositivo di proiezione da tutte le reti Wi-Fi. In questo modo verrà eliminato qualsiasi passaggio di canale tra il canale del punto di accesso e il canale Miracast impostato sul dispositivo Surface Hub. Inoltre, alcune impostazioni dei Criteri di gruppo e del firewall potrebbero essere collegate a una rete Wi-Fi.

### Controllare i driver

È anche consigliabile verificare che i driver e gli aggiornamenti più recenti siano installati nel dispositivo di proiezione. In Gestione dispositivi apri la scheda Wi-Fi e la scheda video e controlla che sia disponibile una versione aggiornata del driver. L'[Hotfix 3120232](https://support.microsoft.com/help/3120232/poor-wireless-performance-on-5-ghz-connections-on-surface-pro-3-and-surface-3) è vivamente consigliato per Surface Pro 3 e Surface Pro 4 se si trovano in un driver Wi-Fi meno recente. 

### Verificare che Miracast sia supportato

Successivamente, assicurati che Miracast sia supportato nel dispositivo. 

1. Premi il tasto Windows + R e digita `dxdiag`. 
2. Fare clic su "Salva tutte le informazioni". 
3. Apri il file dxdiag.txt salvato e trova **Miracast**. Dovrebbe essere visualizzato **Disponibile, con HDCP**. 
    
### Verificare il firewall
    
Windows Firewall può bloccare il traffico Miracast. Il test più semplice consiste nel disabilitare il firewall e testare la proiezione. Se Miracast funziona con il firewall disabilitato, aggiungi un'eccezione per

    C:\Windows\System32\WUDFHost.exe
    Allow In/Out connections for TCP and UDP, Ports: All.

### Verificare le impostazioni di Criteri di gruppo

Nei dispositivi aggiunti a un dominio i Criteri di gruppo possono anche bloccare Miracast. 

1. Utilizza il tasto Windows + R e digita `rsop.msc` per eseguire lo snap-in **Set di criteri risultante**. Questo mostrerà i criteri correnti applicati al PC. 
2. Rivedi **Configurazione computer** > **Impostazioni di Windows** > **Impostazioni sicurezza** > **Criteri di rete wireless (IEEE 802.11)**. Deve essere presente un'impostazione per i criteri wireless. 
3. Fai doppio clic sull'impostazione dei criteri wireless e verrà visualizzata una finestra di dialogo. 
4. Apri la scheda **Autorizzazioni reti** e seleziona **Consenti al gruppo Everyone di creare tutti i profili utente**.

### Controllare i registri eventi

L'ultima posizione da verificare si trova nei registri eventi. Gli eventi Miracast verranno registrati in **Wlanautoconfig**. Ciò vale sia su Surface Hub che sul dispositivo di proiezione. Se si esportano i registri di Surface Hub, è possibile visualizzare i Wlanautoconfig di Surface Hub nella cartella **WindowsEventLog** . Gli errori nel registro eventi possono fornire informazioni aggiuntive riguardo al punto in cui la connessione non funziona.

## Problemi relativi alle prestazioni

Dopo che la proiezione wireless è connessa, è possibile vedere i problemi relativi alle prestazioni che causano la latenza. Questo è a livello generale il risultato della saturazione globale del canale o la situazione che provoca il passaggio di canale. 

Per la saturazione di canale, vedi l'analisi della rete e tenta di utilizzare i canali con minore quantità di traffico.

Il passaggio di canale si verifica quando la scheda di rete Wi-Fi deve inviare traffico a più canali. Alcuni canali supportano la selezione dinamica della frequenza (Dynamic Frequency Selection o "DFS"). La DFS viene utilizzata sui canali da 49 a 148. Alcuni driver Wi-Fi mostreranno una riduzione delle prestazioni quando saranno connessi a un canale DFS. Se le prestazioni Miracast sono scarse durante la connessione a un canale DFS, prova la proiezione su un canale non DFS. Sia Surface Hub che il dispositivo di proiezione devono usare canali non DFS.

Se Surface Hub e il dispositivo di proiezione sono entrambi connessi alla rete Wi-Fi, ma utilizzano punti di accesso diversi con canali diversi, Surface Hub e il dispositivo di proiezione saranno obbligati a un passaggio di canale mentre Miracast è connesso. Il risultato sarà una proiezione wireless scarsa e un peggioramento delle prestazioni di rete tramite Wi-Fi. Il passaggio di canale influirà sulle prestazioni di tutto il traffico wireless, non solo della proiezione wireless. 

Il passaggio di canale si verifica anche se il dispositivo di proiezione è connesso a una rete Wi-Fi che usa un canale diverso da quello che Surface Hub usa per Miracast. Quindi, la procedura consigliata consiste nel impostare il canale di Miracast di Surface Hub sullo stesso canale del punto di accesso usato più comunemente. 

Se sono presenti più reti Wi-Fi o punti di accesso nell'ambiente, qualche passaggio di canale è inevitabile. Questo viene risolto meglio verificando che tutti i driver Wi-Fi siano aggiornati.

##  <a name="contact-support"></a>Supporto tecnico

Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).

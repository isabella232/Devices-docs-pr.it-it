---
title: Ottimizzare la connettività Wi-Fi per i dispositivi Surface
description: Questo argomento descrive le impostazioni di Wi-Fi consigliate per garantire che i dispositivi Surface rimangano connessi in ambienti di rete congestionati e scenari mobili.
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.audience: itpro
ms.localizationpriority: medium
ms.author: greglin
ms.topic: article
ms.reviewer: tokatz
manager: laurawi
ms.date: 10/26/2020
ms.openlocfilehash: d211ceea20b89824d45e433cf9670abe137130a0
ms.sourcegitcommit: 07ac65bf70c8c6efcda28eecc3013983fc386e0d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "11136146"
---
# Ottimizzare la connettività Wi-Fi per i dispositivi Surface


Per rimanere in contatto con la durata della batteria giornaliera, i dispositivi Surface implementano le impostazioni di connettività wireless che equilibrano le prestazioni e la conservazione dell'energia. Al di fuori degli scenari di mobilità più esigenti, gli utenti possono mantenere una connettività wireless sufficiente senza modificare le impostazioni di rete predefinite o le opzioni correlate. Questa pagina evidenzia le principali considerazioni sulla connettività wireless in scenari mobili con i più recenti dispositivi Surface, tra cui Surface Pro 7, Surface Pro X, Surface laptop 3, Surface Book 3, Surface Go 2 e Surface laptop go.  

## Prerequisiti

In questo documento si presuppone che sia stata distribuita correttamente una rete wireless che supporta 802.11 n (Wi-Fi 4) o versione successiva in base alle procedure consigliate per le procedure consigliate dei principali fornitori di apparecchiature.

## Configurazione di Access Point per funzionalità di roaming ottimali

Se si gestisce una rete wireless in genere accessibile da diversi tipi di dispositivi client, è consigliabile abilitare protocolli specifici su Access Point (APs) nella WLAN, come descritto in [roaming veloce con 802.11 k, 802.11 v e 802.11 r](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r). I dispositivi Surface possono sfruttare i seguenti protocolli wireless:

- **802.11 r.** "**Transizione BSS veloce"** accelera la connessione ai nuovi punti di accesso wireless riducendo il numero di fotogrammi necessari prima che il dispositivo possa accedere ad un altro AP mentre ci si sposta con il dispositivo. Nella nuova generazione di dispositivi Surface rilasciati a partire da 2019 gli utenti finali possono accedere alle impostazioni di aggressività del roaming nel dispositivo. Anche se non è consigliabile modificare le impostazioni predefinite, gli utenti devono essere consapevoli di questa funzionalità e capire in che modo le impostazioni specifiche possono influire sulla possibilità di rimanere connesse.
- **802.11 k.** **"Report Neighbor"** fornisce i dispositivi con informazioni sulle condizioni correnti nei punti di accesso adiacenti. Può aiutare il dispositivo Surface a scegliere l'AP migliore usando criteri diversi dalla potenza del segnale, ad esempio l'utilizzo di AP.

I dispositivi Surface specifici possono anche usare i frame di gestione della transizione BSS "802.11 v", che funziona in modo molto simile a 802.11 k per fornire informazioni sulle vicinanze del candidato APs. Questi includono Surface go, Surface Pro 7, Surface Pro X e Surface laptop 3. 

## Gestione delle impostazioni utente

Puoi ottenere funzionalità di roaming ottimali grazie a una rete ben progettata che supporta 802.11 r e 802.11 k in tutti i punti di accesso. Verificare che la rete sia configurata in modo corretto per consentire agli utenti la migliore esperienza wireless è l'approccio consigliato rispetto al tentativo di gestire le impostazioni utente nei singoli dispositivi. 

### Impostazioni consigliate degli utenti e procedure consigliate

In alcune situazioni, la modifica delle impostazioni avanzate della scheda di rete incorporati in dispositivi di Surface può facilitare una connessione più affidabile. Tieni presente tuttavia che l'impossibilità di connettersi a risorse wireless è più spesso dovuta a un problema di Access Point, un difetto di progettazione della rete o un problema di sito ambientale.

> [!NOTE]
> La modalità di mantenimento della superficie Pro o Surface Go può anche influire sulla potenza del segnale. Se si verifica una perdita di larghezza di banda, verificare che non si stia tenendo la parte superiore dello schermo, in cui si trova il ricevitore radio Wi-Fi. Anche se tenendo la parte superiore dello schermo non blocca i segnali wireless, può attivare il driver di dispositivo per avviare le modifiche che riducono la connettività.

### Mantieni l'impostazione automatica predefinita per la funzionalità dual Bandwidth

Nella maggior parte dei dispositivi Surface è possibile configurare le impostazioni della scheda di rete client per connettersi solo ai punti di accesso wireless oltre 5 gigahertz (GHz), connettere solo oltre 2,4 GHz o consentire al sistema operativo di scegliere l'opzione migliore (impostazione automatica predefinita).

**Per accedere alle impostazioni della scheda di rete, vedere:**

- **Inizio**  >  pagina **Pannello**  >  di controllo Centro rete e **condivisione**  >  **scheda Wi-Fi**  >  **Proprietà**  >  **Configurare**  >  **Avanzate**.

![* WiFi-impostazioni banda *](images/wifi-band.png) <br>

Tieni presente che 2,4 GHz presenta alcuni vantaggi superiori a 5 GHz: si estende ulteriormente e più facilmente penetra attraverso muri o altri oggetti solidi. A meno che non si disponga di un caso di utilizzo chiaro che garantisce la connessione a 5 GHz, è consigliabile abbandonare l'impostazione della banda nello stato predefinito per evitare possibili conseguenze negative. Ad esempio:


- Molti hotspot presenti in alberghi, caffetterie e aeroporti usano ancora solo 2,4 GHz, bloccando effettivamente l'accesso ai dispositivi se la banda è impostata solo su 5 GHz.
- Dato che le connessioni dello schermo wireless di Miracast richiedono il completamento della stretta di mano iniziale oltre i canali di 2,4 GHz, i dispositivi non saranno in grado di connettersi solo a 5 GHz.

> [!NOTE]
> Per impostazione predefinita, i dispositivi Surface preferiscono connettersi a 5 GHz, se disponibile. Tuttavia, per preservare l'alimentazione in uno stato di batteria scarica, Surface cercherà prima di tutto una connessione a 2,4 GHz.

È anche possibile attivare o disattivare l'impostazione della banda in base alle esigenze dell'ambiente. Ad esempio, gli utenti che vivono in edifici di appartamenti ad alta densità con più hotspot Wi-Fi, in mezzo alla presenza di dispositivi consumer tutti i broadcasting via 2,4 GHz, potrebbero avvantaggiarsi impostando il loro dispositivo Surface per connettersi solo a 5 GHz e quindi ripristinare l'auto quando necessario.

### Impostazioni di aggressività del roaming su dispositivi Surface con adapter Intel 

Gli utenti potrebbero voler selezionare una soglia di intensità del segnale che chiede al dispositivo di cercare un nuovo punto di accesso quando il segnale scende (aggressività del roaming). Per impostazione predefinita, i dispositivi Surface con gli adattatori Intel tentano di spostarsi in un nuovo punto di accesso se l'intensità del segnale scende al di sotto di **media** (72% di intensità del segnale). Si noti inoltre che le organizzazioni possono implementare protocolli wireless creati appositamente in più punti di accesso alla rete per facilitare il roaming degli ambienti di rete congestionati, come spiegato in precedenza in questa pagina. 

Mentre aumenta l'aggressività del roaming sopra il **medio** può produrre una connettività migliorata in ambienti di Office o residenziali altamente congestionati, può causare una connettività degradata quando si esce da questi ambienti. 

È consigliabile abbandonare l'impostazione di aggressività del roaming nello stato predefinito, a meno che non si verifichino problemi di connettività in scenari specifici per dispositivi mobili, ad esempio per eseguire ispezioni dei siti ambientali, mantenendo anche la connettività vocale e video durante una riunione di conferenza. Se non si nota alcun miglioramento, tornare allo stato medio predefinito. Tieni presente che se aumenti l'aggressività del roaming, acceleri anche il consumo di energia della batteria. 

**Per abilitare l'aggressività del roaming su Surface:**

1. Passa a **Avvia**  >  **Gestione dispositivi**.
2. In **schede di rete** selezionare **Intel Wi-Fi 6** e quindi fare clic con il pulsante destro del mouse su **proprietà**.
3. Selezionare la scheda **Avanzate** .
4. Selezionare l' **aggressività del roaming** e scegliere il valore desiderato nel menu a discesa.

![* Impostazioni di aggressività del roaming-Intel *](images/wifi-roaming-int.png) <br>

### Impostazioni di aggressività del roaming in Surface go e Surface Pro X

I lavoratori di prima linea che usano Surface go possono selezionare una soglia di intensità del segnale che chiede al dispositivo di cercare un nuovo punto di accesso quando l'intensità del segnale scende (aggressività del roaming). Per impostazione predefinita, i dispositivi di superficie tentano di spostarsi in un nuovo punto di accesso se l'intensità del segnale scende al di sotto di **media** (50%). Tieni presente che ogni volta che aumenti l'aggressività del roaming, acceleri il consumo di energia della batteria.

Abbandonare l'impostazione di aggressività del roaming nello stato predefinito, a meno che non si verifichino problemi di connettività in scenari specifici per dispositivi mobili, ad esempio l'esecuzione di ispezioni del sito ambientali, ma anche la connettività vocale e video durante una riunione di conferenza. Se non si nota alcun miglioramento, tornare allo stato **medio** predefinito.

**Per abilitare l'aggressività del roaming in Surface Go:**

1. Accedere alla pagina **Start > pannello di controllo**  >  **e**alla  >  **rete Internet e al centro condivisione.**
2. In **connessioni** selezionare **Wi-Fi** e quindi selezionare **Proprietà.**
3. Selezionare **client per Microsoft Networks** e quindi selezionare **Configura**
4. Selezionare **Advanced**l'  >  **aggressività del roaming** avanzato e scegliere il valore preferito nel menu a discesa.

![* Impostazioni di aggressività del roaming-QualComm *](images/wifi-roaming.png) <br>


## Conclusione

I dispositivi Surface sono progettati con le impostazioni predefinite per una connettività wireless ottimale bilanciata a fianco della necessità di preservare la durata della batteria. Il modo più efficace per abilitare la connettività affidabile per i dispositivi Surface è attraverso una rete ben progettata che supporta 802.11 r e 802.11 k. Gli utenti possono modificare le impostazioni della scheda di rete o l'aggressività del roaming, ma devono essere eseguite solo in risposta a specifici fattori ambientali e ripristinare lo stato predefinito, se non si verificano miglioramenti evidenti.

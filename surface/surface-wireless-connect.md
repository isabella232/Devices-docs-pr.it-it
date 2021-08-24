---
title: Ottimizzare la connettività Wi-Fi per i dispositivi Surface
description: Questo argomento descrive le impostazioni Wi-Fi per garantire che i dispositivi Surface rimangano connessi in ambienti di rete congestionati e in scenari mobili.
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
ms.date: 01/15/2021
ms.openlocfilehash: 3670a809f837619851b627e320203d7061d1e913
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911461"
---
# <a name="optimize-wi-fi-connectivity-for-surface-devices"></a>Ottimizzare la connettività Wi-Fi per i dispositivi Surface


Per rimanere connessi con la durata della batteria per tutto il giorno, i dispositivi Surface implementano impostazioni di connettività wireless che bilanciano le prestazioni e la conservazione dell'alimentazione. Al di fuori degli scenari di mobilità più impegnativi, gli utenti possono mantenere una connettività wireless sufficiente senza modificare la scheda di rete predefinita o le impostazioni correlate. Questa pagina evidenzia le considerazioni chiave sulla connettività wireless negli scenari per dispositivi mobili che usano i dispositivi Surface più recenti, tra cui Surface Pro 7+, Surface Laptop Go, Surface Go 2, Surface Pro X, Surface Laptop 3, Surface Book 3 e Surface Pro 7.

## <a name="prerequisites"></a>Prerequisiti

In questo documento si presuppone che sia stata distribuita correttamente una rete wireless che supporta 802.11n (Wi-Fi 4) o versione successiva in conformità alle procedure consigliate dai principali fornitori di attrezzature.

## <a name="configuring-access-points-for-optimal-roaming-capabilities"></a>Configurazione dei punti di accesso per funzionalità di roaming ottimali

Se si gestisce una rete wireless a cui in genere accedono molti tipi diversi di dispositivi client, è consigliabile abilitare protocolli specifici sui punti di accesso (AP) nella rete WLAN, come descritto in Roaming veloce con [802.11k, 802.11v e 802.11r.](https://docs.microsoft.com/windows-hardware/drivers/network/fast-roaming-with-802-11k--802-11v--and-802-11r) I dispositivi Surface possono sfruttare i protocolli wireless seguenti:

- **802.11r.** "Transizione**BSS rapida"** accelera la connessione ai nuovi punti di accesso wireless riducendo il numero di fotogrammi necessari prima che il dispositivo possa accedere a un altro AP mentre ci si sposta con il dispositivo. Nella nuova generazione di dispositivi Surface rilasciati a partire dal 2019, gli utenti finali possono accedere alle impostazioni di aggressività roaming nel dispositivo. Anche se non è consigliabile modificare le impostazioni predefinite, gli utenti devono essere consapevoli di questa funzionalità e comprendere in che modo impostazioni specifiche possono influire sulla loro capacità di rimanere connessi.
- **802.11k.** **I "rapporti vicini"** forniscono ai dispositivi informazioni sulle condizioni correnti nei punti di accesso vicini. Può aiutare il dispositivo Surface a scegliere l'AP migliore usando criteri diversi dall'intensità del segnale, ad esempio l'utilizzo dell'AP.

Dispositivi Surface specifici possono anche usare 802.11v "BSS Transition Management Frames", che funziona in modo molto simile a 802.11k per fornire informazioni sui criteri di accesso candidati vicini. Questi includono Surface Pro 7+, Surface Go, Surface Go 2, Surface Pro 7, Surface Pro X e Surface Laptop 3. 

## <a name="managing-user-settings"></a>Gestione delle impostazioni utente

È possibile ottenere funzionalità di roaming ottimali tramite una rete ben progettata che supporta 802.11r e 802.11k in tutti i punti di accesso. Verificare che la rete sia configurata correttamente per offrire agli utenti la migliore esperienza wireless è l'approccio consigliato rispetto al tentativo di gestire le impostazioni utente su singoli dispositivi. 

### <a name="recommended-user-settings-and-best-practices"></a>Procedure consigliate e impostazioni utente consigliate

In alcune situazioni, la modifica delle impostazioni avanzate delle schede di rete integrate nei dispositivi Surface può facilitare una connessione più affidabile. Tenere presente tuttavia che l'impossibilità di connettersi alle risorse wireless è più spesso dovuta a un problema del punto di accesso, a un difetto di progettazione della rete o a un problema di sito ambientale.

> [!NOTE]
> Anche il modo in cui tieni Surface Pro o Surface Go può influire sulla potenza del segnale. Se si verifica una perdita di larghezza di banda, verificare di non tenere la parte superiore dello schermo, in cui si trova il ricevitore Wi-Fi radio. Anche se tenere la parte superiore dello schermo non blocca i segnali wireless, può attivare il driver di dispositivo per avviare modifiche che riducono la connettività.

### <a name="keep-default-auto-setting-for-dual-bandwidth-capability"></a>Mantenere l'impostazione automatica predefinita per la doppia larghezza di banda

Nella maggior parte dei dispositivi Surface puoi configurare le impostazioni della scheda di rete client in modo che si connettano solo a punti di accesso wireless oltre 5 gigahertz (GHz), connettiti solo a 2,4 GHz o consenti al sistema operativo di scegliere l'opzione migliore (impostazione automatica predefinita).

**Per accedere alle impostazioni della scheda di rete, andare a:**

- **Start**  >  **Pannello di controllo**  >  **Centro connessioni di rete e condivisione**  >  **scheda Wi-Fi**  >  **Proprietà**  >  **Configurare**  >  **Advanced**.

![* impostazioni della banda wifi*.](images/wifi-band.png) <br>

Tieni presente che 2,4 GHz offre alcuni vantaggi rispetto ai 5 GHz: si estende ulteriormente e penetra più facilmente attraverso pareti o altri oggetti solidi. A meno che non si abbia un caso d'uso chiaro che garantisca la connessione a 5 GHz, è consigliabile lasciare l'impostazione Banda nello stato predefinito per evitare possibili conseguenze negative. Ad esempio:


- Molti hotspot presenti in hotel, bar e aeroporti usano ancora solo 2,4 GHz, bloccando in modo efficace l'accesso ai dispositivi se Banda è impostata su Solo 5 GHz.
- Poiché Miracast le connessioni dello schermo wireless richiedono il completamento dell'handshake iniziale su canali da 2,4 GHz, i dispositivi non saranno in grado di connettersi solo a 5 GHz.

> [!NOTE]
> Per impostazione predefinita, i dispositivi Surface preferiscono connettersi a 5 GHz, se disponibili. Tuttavia, per mantenere l'alimentazione in uno stato di batteria bassa, Surface cerca innanzitutto una connessione a 2,4 GHz.

Puoi anche attivare o disattivare l'impostazione della banda in base alle esigenze per il tuo ambiente. Ad esempio, gli utenti che vivono in edifici ad alta densità con più hotspot Wi-Fi ( in presenza di dispositivi consumer tutti trasmessi tramite 2,4 GHz) probabilmente trarranno vantaggio impostando il dispositivo Surface in modo che si connetta solo a 5 GHz e quindi ritornino su Auto quando necessario.

### <a name="roaming-aggressiveness-settings-on-surface-devices-with-intel-adapters"></a>Impostazioni di aggressività roaming nei dispositivi Surface con schede Intel 

Gli utenti possono scegliere una soglia di potenza del segnale che richiede al dispositivo di cercare un nuovo punto di accesso quando il segnale scende (aggressività roaming). Per impostazione predefinita, i dispositivi Surface con schede Intel tentano di eseguire il roaming verso un nuovo punto di accesso se la potenza del segnale scende al di sotto di **Media** (potenza del segnale del 72%). Si noti inoltre che le organizzazioni possono implementare protocolli wireless appositamente creati in più punti di accesso di rete per facilitare il roaming degli ambienti di rete congestionati, come illustrato in precedenza in questa pagina. 

Anche se aumentare **** l'aggressività del roaming al di sopra di Medio può produrre una connettività migliorata in ambienti di uffici o residenziali altamente congestionati, può causare una connettività degradata quando si esegue un'istruzione all'esterno di questi ambienti. 

È consigliabile lasciare l'impostazione di aggressività roaming nello stato predefinito, a meno che non si verifichino problemi di connettività in scenari mobili specifici, ad esempio l'esecuzione di ispezioni di siti ambientali, mantenendo al contempo la connettività vocale e video durante una riunione di conferenza. Se non si nota alcun miglioramento, ripristinare lo stato medio predefinito. Tieni presente che se aumenti l'aggressività del roaming, acceleri anche il consumo di energia della batteria. 

**Per abilitare l'aggressività del roaming in Surface:**

1. Vai a **Avvia**  >  **Gestione dispositivi**.
2. In **Schede di rete selezionare** Intel Wi-Fi **6** e quindi fare clic con il pulsante destro del mouse su **Proprietà.**
3. Selezionare la **scheda** Avanzate.
4. Seleziona **Aggressività roaming** e scegli il valore preferito dal menu a discesa.

![* Impostazioni di aggressività roaming-Intel *.](images/wifi-roaming-int.png) <br>

### <a name="roaming-aggressiveness-settings-on-surface-go-and-surface-pro-x"></a>Impostazioni di aggressività roaming in Surface Go e Surface Pro X

I lavoratori in prima linea che usano Surface Go potrebbero voler selezionare una soglia di potenza del segnale che richiede al dispositivo di cercare un nuovo punto di accesso quando la forza del segnale scende (aggressività roaming). Per impostazione predefinita, i dispositivi Surface tentano di eseguire il roaming verso un nuovo punto di accesso se la potenza del segnale scende al di sotto di **Medio** (potenza del segnale del 50%). Tieni presente che ogni volta che aumenti l'aggressività del roaming, acceleri il consumo di energia della batteria.

Lasciare l'impostazione di aggressività roaming nello stato predefinito, a meno che non si verifichino problemi di connettività in scenari mobili specifici, ad esempio l'esecuzione di ispezioni di siti ambientali, pur mantenendo la connettività vocale e video durante una riunione di conferenza. Se non si nota alcun miglioramento ripristinare lo stato **medio** predefinito.

**Per abilitare l'aggressività del roaming in Surface Go:**

1. Vai a **Start > Pannello di controllo**Rete e Centro connessioni  >  **di**rete e condivisione  >  **Internet.**
2. In **Connessioni** seleziona **Wi-Fi** e quindi seleziona **Proprietà.**
3. Selezionare **Client per reti Microsoft,** quindi selezionare **Configura**
4. Seleziona **Advanced**  >  **Roaming Aggressiveness** e scegli il valore preferito dal menu a discesa.

![* Impostazioni di aggressività roaming-QualComm *.](images/wifi-roaming.png) <br>


## <a name="conclusion"></a>Conclusione

I dispositivi Surface sono progettati con le impostazioni predefinite per una connettività wireless ottimale bilanciata insieme alla necessità di mantenere la durata della batteria. Il modo più efficace per abilitare una connettività affidabile per i dispositivi Surface è tramite una rete ben progettata che supporta 802.11r e 802.11k. Gli utenti possono modificare le impostazioni della scheda di rete o l'aggressività del roaming, ma devono farlo solo in risposta a fattori ambientali specifici e ripristinare lo stato predefinito se non vi sono miglioramenti notevoli.

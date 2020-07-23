---
title: Installare Windows 10 team 2020 Update Preview Build
description: L'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 team 2020 Update, è ora disponibile.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/22/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 9177b184d7a1d6dca63e94740b6208987d97229f
ms.sourcegitcommit: df1e178b724966e4cf8ff219c5e937e6c31cd9b4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "10894112"
---
# Installare Windows 10 team 2020 Update Preview Build 

L'aggiornamento più recente del sistema operativo Surface Hub, **Windows 10 Team 2020 Update**, è ora disponibile senza costi aggiuntivi per i dispositivi di Surface hub da 50 pollici e Surface Hub da 2S 55 per il [programma Windows Insider](https://insider.windows.com). Il modello di Surface Hub 84-inch sarà supportato nella versione finale di Windows 10 team 2020 Update.

Windows 10 team 2020 Update offre miglioramenti importanti alla distribuzione e alla gestibilità dei dispositivi insieme alle caratteristiche più recenti di Windows 10. Per altre informazioni sulle novità, vedere il post di Blog seguente: [nuovo aggiornamento del sistema operativo Surface Hub rilasciato per l'anteprima pubblica.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823) Per i problemi noti, vedere la sezione "problemi noti" di seguito.
 
## Prerequisiti

- Eseguire la registrazione con il [programma Windows Insider](https://insider.windows.com/).
- Scaricare la build Preview di aggiornamento di Windows 10 team 2020 da Windows Insider Fast Channel.
- Dopo aver installato la build di anteprima, scaricare gli aggiornamenti del firmware necessari. Nota: gli aggiornamenti del firmware non possono essere disinstallati anche se si decide di uscire da Windows Insider Program.

## Preparare il mozzo della superficie

Prima di iniziare, verifica che il tuo hub Surface disponga degli aggiornamenti più recenti di Windows Update e assicurati di salvare la chiave BitLocker associata al dispositivo.

**Per verificare manualmente la disponibilità di aggiornamenti:**

1. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
2. Passare a **Aggiorna & Security**  >  **Windows Update** e quindi selezionare **Controlla aggiornamenti**.

Per altre informazioni, vedere [gestire gli aggiornamenti di Windows in Surface Hub](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub).

**Per salvare manualmente la chiave BitLocker:**

1. Inserire un'unità USB in Surface Hub.
2. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
3. Passare a **aggiornamento &**  >  **ripristino**della sicurezza.
4. In **BitLocker**selezionare **Salva**. La chiave BitLocker viene salvata in un file di testo nell'unità USB.

Per altre informazioni, vedere [salvare la chiave BitLocker](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub).
 
## Installare la build Preview di aggiornamento di Windows 10 team 2020

1. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
2. Passare al programma **Update & Security**  >  **Windows Insider** e quindi selezionare per **iniziare**.
3. Seguire le istruzioni per la registrazione come Windows Insider usando l'account di lavoro (consigliato) o l'account Microsoft personale. Per informazioni dettagliate sui vantaggi della registrazione con l'account aziendale, vedere [registrazione per Windows Insider Program for business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).
4. In Seleziona le **Impostazioni Insider**selezionare **Fast**.
5. Consentire all'hub Surface di installare automaticamente la build di anteprima e gli aggiornamenti del firmware necessari nei prossimi 3 o 4 giorni. Il dispositivo scaricherà e installerà automaticamente gli aggiornamenti durante le [finestre di manutenzione](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)giornaliera. Ad esempio:

- Durante la prima finestra di manutenzione, Surface Hub avvia il download della build di anteprima da Windows Update.
- Durante una seconda finestra di manutenzione, il dispositivo viene riavviato per completare l'aggiornamento.
- Durante una terza finestra di manutenzione, il dispositivo Scarica e installa gli aggiornamenti del firmware necessari.

> [!IMPORTANT]
> Microsoft consiglia di prenotare la superficie hub per 3-4 giorni per consentire al dispositivo di completare l'installazione della build di anteprima e gli aggiornamenti del firmware necessari. Se si usa il dispositivo durante questo processo, è possibile che si verifichino problemi di grafica, audio e interfaccia utente.

### Se si sceglie di installare manualmente la build di anteprima e gli aggiornamenti del firmware necessari:

1. Dopo aver effettuato la registrazione con il programma Windows Insider, vedere l'aggiornamento **delle impostazioni**  >  **& Security**  >  **Windows Update** e selezionare **Controlla aggiornamenti** per installare la build di anteprima.
2. Dopo l'installazione della build di anteprima (potrebbero essere necessarie fino a 14 ore), selezionare **Riavvia ora** per completare la procedura.
3. Dopo il riavvio del dispositivo, vedere aggiornare **le impostazioni**  >  **& Security**  >  **Windows Update**e selezionare **Controlla aggiornamenti per installare gli aggiornamenti del firmware necessari**.
4. Dopo l'installazione del firmware, selezionare **Riavvia ora**.

> [!WARNING]
> Se si installa la build di anteprima senza installare gli aggiornamenti del firmware necessari, è possibile che vengano visualizzati problemi relativi a grafica, audio e interfaccia utente.

> [!NOTE]
> Se si sceglie di abbandonare il programma Windows Insider e ripristinare Surface Hub in una versione precedente del sistema operativo, è necessario prima di tutto [reimpostare il dispositivo](https://docs.microsoft.com/surface-hub/device-reset-surface-hub). In seguito, dovrai passare attraverso il [programma prima esecuzione](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) per riconfigurare il dispositivo.
 
## Problemi noti: Build Preview di aggiornamento di Windows 10 team 2020

### Problemi relativi a grafica, audio e interfaccia utente 

È possibile che si verifichino diversi problemi di interfaccia utente e grafica se si installa la build di anteprima, ma non si installano immediatamente gli aggiornamenti del firmware necessari in seguito. Microsoft prevede di risolvere questi problemi nella build di rilascio di Windows 10 team 2020 Update.

### Surface Hub 84-inch: problemi di interfaccia grafica e utente

È possibile che si verifichino diversi problemi di interfaccia utente e grafica se si installa la build di anteprima in un dispositivo hub Surface di prima generazione da 84 pollici. Il 84-inch di Surface hub sarà supportato nella versione finale di Windows 10 team 2020 Update.

### L'accesso è influenzato quando si applicano i criteri di Access condizionali

- L'accesso non riesce quando si tenta di accedere a app come Microsoft whiteboard. Gli utenti devono prima eseguire l'accesso da [riunioni e file](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub) dal menu Start.

- L'accesso non riesce se l'account utente è registrato in un tenant di Azure AD diverso da quello usato da Surface Hub ad Azure AD join.

Microsoft prevede di risolvere questi problemi nella build di rilascio di Windows 10 team 2020 Update.

### Windows Update richiede di installare nuovi driver quando nessuno è disponibile

Quando si passa all'aggiornamento **delle impostazioni**  >  **& Security**  >  **Windows Update** dopo l'installazione di Windows 10 team 2020 Update e gli aggiornamenti del firmware necessari, è possibile che venga visualizzato il seguente messaggio di errore: 

- "Un driver corrente nel PC potrebbe essere migliore del driver che si sta provando a installare. Continueremo a provare a installare ". 

Questo errore può essere ignorato in modo sicuro. Microsoft sta esaminando attivamente questo problema.

### Non è possibile installare i criteri di Surface hub usando i pacchetti di provisioning

Il provisioning dei pacchetti che usano i criteri del provider di servizi di Surface Hub Configuration (CSP) non riesce a installare. Per il momento, USA Microsoft Intune o un altro provider di gestione di dispositivi mobili (MDM) per applicare i criteri di Surface Hub. Microsoft prevede di risolvere il problema nella build di rilascio di Windows 10 team 2020 Update.

### Prompt per rimuovere l'unità USB prematuramente durante la prima esecuzione

Quando si usa un pacchetto di provisioning per configurare l'hub Surface durante la prima esecuzione, viene chiesto di rimuovere l'unità USB prima che il dispositivo sia in grado di leggere il file di configurazione di Surface Hub. Ignorare il messaggio se si usa un file di configurazione per configurare l'account del dispositivo. Microsoft sta esaminando attivamente questo problema.
 
### Non è possibile configurare le impostazioni proxy durante la prima esecuzione

Se si usa un proxy per connettersi a Internet, è possibile che si disponga di una connettività Internet limitata durante il programma per la prima esecuzione. Microsoft prevede di risolvere il problema nella build di rilascio di Windows 10 team 2020 Update.
 
### Viene visualizzato un messaggio di errore quando si scaricano app da Microsoft Store

Per scaricare un'app da Microsoft Store, verrà visualizzata una richiesta di accesso. Un problema noto fa sì che venga visualizzato un messaggio di errore durante l'accesso, ma ciò non influenza la possibilità di scaricare app. Microsoft sta esaminando attivamente questo problema.

### Surface Hub 2S intermittentemente perde la connessione Wi-Fi

Provare a scollegare il dispositivo e a collegarlo di nuovo o a usare un cavo Ethernet per connettersi a Internet. Microsoft sta esaminando attivamente questo problema.

### Surface Hub 2S in modo intermittente non riesce a riprendere dal sonno

Surface Hub 2S potrebbe non riuscire a riprendere completamente dal sonno e sembra che smetta di rispondere in una schermata che mostra il logo Microsoft. Provare a scollegare il dispositivo e a collegarlo di nuovo. 

Per evitare questo problema:

1. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
2. Passare alla sessione di **Surface Hub**  >  **& Power**. 
3. In **quando il dispositivo passa a dormire, usare questa impostazione di alimentazione**, selezionare **standby connesso.**
4. In **quando non è presente nessuno, inserire il dispositivo in modalità di sospensione**, selezionare **mai.**

Microsoft prevede di risolvere il problema in un aggiornamento del firmware prima della versione finale dell'aggiornamento di Windows 10 team 2020.

### Problemi di proiezione quando l'app Connect non è in visualizzazione

- Quando usi un cavo per proiettare su Surface Hub, Touchback smette di funzionare se ti sposti dall'app Connect.
- Quando si proietta nell'hub Surface usando Miracast, la connessione wireless non viene rilasciata subito dopo l'esplorazione dall'app Connect.

Microsoft sta esaminando attivamente questi problemi.

### Skype for business non usa proxy per il traffico multimediale

Per alcuni dispositivi che usano un proxy, Skype for business può eseguire l'accesso, ma non userà il server proxy per il traffico multimediale. Microsoft sta esaminando attivamente questo problema.

Ti invitiamo a condividere le tue intuizioni e i tuoi suggerimenti con il supporto Microsoft.

## Scopri di più

- [Nuovo aggiornamento del sistema operativo Surface Hub rilasciato per l'anteprima pubblica.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [Attività iniziali con il programma Windows Insider per le aziende](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)
---
title: Installare la versione in anteprima dell'aggiornamento di Windows 10 Team 2020
description: L'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 team 2020 Update, è ora disponibile.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 08/07/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 79e6c35deba5c4635945c3b376a1069e3df324d9
ms.sourcegitcommit: 83530906c7e34c92bbee90b723321acd61e77669
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2020
ms.locfileid: "10918916"
---
# Installare la versione in anteprima dell'aggiornamento di Windows 10 Team 2020 

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
2. Passare a **Privacy > diagnostica & feedback** e **completo** per i dati di diagnostica. 
3. Passare al programma **Update & Security**  >  **Windows Insider** e quindi selezionare per **iniziare**.
4. Seguire le istruzioni per la registrazione come Windows Insider usando l'account di lavoro (consigliato) o l'account Microsoft personale. Per informazioni dettagliate sui vantaggi della registrazione con l'account aziendale, vedere [registrazione per Windows Insider Program for business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).
5. In Seleziona le **Impostazioni Insider**selezionare **Fast**.
6. Consentire all'hub Surface di installare automaticamente la build di anteprima e gli aggiornamenti del firmware necessari nei prossimi 3 o 4 giorni. Il dispositivo scaricherà e installerà automaticamente gli aggiornamenti durante le [finestre di manutenzione](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)giornaliera. Ad esempio:

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
 

## Scopri di più

- [Problemi noti: aggiornamento di Windows 10 team 2020](surface-hub-2020-team-update-known-issues.md)
- [Nuovo aggiornamento del sistema operativo Surface Hub rilasciato per l'anteprima pubblica.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [Attività iniziali con il programma Windows Insider per le aziende](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)
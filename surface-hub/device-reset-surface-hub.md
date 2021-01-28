---
title: Ripristinare o recuperare un hub Surface
description: Descrive i processi di ripristino e recupero per il mozzo della superficie e fornisce istruzioni.
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: Reimposta Hub superficie, recupera
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/31/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73c7cf5a387bf7506bb69f62100171df4d94ad2d
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304819"
---
# Ripristinare o recuperare un hub Surface

Questo articolo descrive come reimpostare o recuperare un hub di Surface Microsoft.  

[La reimpostazione di Surface Hub](#reset-a-surface-hub) restituisce il proprio sistema operativo all'ultimo aggiornamento cumulativo di Windows e rimuove tutti i file utente locali e le informazioni di configurazione. Le informazioni rimosse includono le seguenti:

- L'account del dispositivo
- Informazioni sull'account per gli amministratori locali del dispositivo
- Domain-Join o Azure AD-informazioni di join
- Informazioni sulla registrazione di gestione di dispositivi mobili (MDM)
- Informazioni sulla configurazione impostate usando MDM o l'app impostazioni

[Il recupero di un hub Surface dal cloud](#recover-a-surface-hub-from-the-cloud) rimuove anche queste informazioni. Inoltre, l'hub Surface Scarica una nuova immagine del sistema operativo e la installa. Puoi specificare se il processo di ripristino mantiene altre informazioni memorizzate nell'hub Surface. La stessa immagine del sistema operativo viene usata dallo [strumento di ripristino di Surface Hub](surface-hub-recovery-tool.md) se è necessario recuperare un hub Surface per cui non è possibile usare nessuna di queste opzioni.

## Reimpostare un hub di Surface

Potrebbe essere necessario reimpostare l'hub Surface per motivi come i seguenti:

- Si sta purposing il dispositivo per una nuova area riunioni e si vuole riconfigurarlo.
- Vuoi modificare la modalità di gestione locale del dispositivo.
- Il nome utente o la password dell'account del dispositivo o dell'account di amministratore è stata persa.
- Dopo l'installazione di un aggiornamento, le prestazioni del dispositivo vengono decrementate.

Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.

> [!WARNING]
> Il processo di ripristino del dispositivo può richiedere fino a sei ore. Non disattivare o scollegare il mozzo della superficie fino al completamento del processo. Se si interrompe il processo, il dispositivo diventa inutilizzabile. Il dispositivo richiede il servizio di garanzia per ridiventare funzionale.

1. Nel dispositivo Surface Hub apri **Impostazioni**.

   ![Immagine che mostra l'app impostazioni per Surface Hub.](images/sh-settings.png)

2. Selezionare **aggiorna & sicurezza**.

   ![Immagine che mostra il gruppo di sicurezza Update & nell'app impostazioni per Surface Hub.](images/sh-settings-update-security.png)

3. Selezionare **ripristino**e quindi, in **Reimposta dispositivo**, selezionare inizia **.**

   > [!IMPORTANT]
   > Verificare di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, dato che verrà richiesto in un secondo momento. Per altre informazioni, vedere [salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md). Quando l'hub viene riavviato nella partizione di ripristino, verrà chiesto di immettere la chiave BitLocker. Se si ignora il messaggio, il comando Reimposta non riesce.
   
   ![Immagine che mostra l'opzione Reimposta dispositivo nell'app impostazioni per hub Surface.](images/sh-settings-reset-device.png)

   Al termine del processo di reimpostazione, l'hub Surface avvia di nuovo il [programma prima esecuzione](first-run-program-surface-hub.md) . Se il processo di reimpostazione incontra un problema, rimanda il mozzo della superficie all'immagine del sistema operativo esistente in precedenza e quindi Visualizza la schermata iniziale.

<span id="cloud-recovery" />

## Ripristinare un dispositivo Surface Hub dal cloud

Se per qualche motivo l'hub Surface diventa inutilizzabile, è comunque possibile recuperarlo dal cloud senza assistenza da parte del supporto Microsoft. L'hub Surface può scaricare un'immagine del sistema operativo fresco dal cloud e usare tale immagine per reinstallare il sistema operativo.

Potrebbe essere necessario usare questo tipo di processo di ripristino nelle circostanze seguenti:

- [L'hub Surface o gli account correlati sono entrati in uno stato instabile](#recover-a-surface-hub-in-a-bad-state)
- [Il mozzo della superficie è bloccato](#recover-a-locked-surface-hub)

>[!IMPORTANT]
>Il processo **di recupero dal cloud** richiede una connessione cablata che fornisce la connettività Internet aperta (nessun proxy o altre richieste di autenticazione).

### Ripristinare un dispositivo Surface Hub in uno stato non valido

Se l'account del dispositivo entra in uno stato instabile o se l'account dell'amministratore incontra problemi, è possibile usare l'app impostazioni per avviare il processo di ripristino del cloud. È consigliabile usare il processo di ripristino del cloud solo quando il processo di ripristino del [dispositivo](#reset-a-surface-hub) non risolve il problema.

1. Nell'hub Surface selezionare Aggiorna **Impostazioni** &gt; **&** &gt; **ripristino**della sicurezza.

2. In **Recupera dal cloud**selezionare **Riavvia ora**.

   ![ripristino dal cloud](images/recover-from-the-cloud.png)

### Ripristinare un dispositivo Surface Hub bloccato

In rari casi, un dispositivo Surface Hub potrebbe riscontrare un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione. In questo caso, il dispositivo viene riavviato automaticamente e ritenta l'operazione. Ma se l'operazione non riesce più volte, il dispositivo si blocca automaticamente per proteggere i dati degli utenti. Per sbloccarlo, è necessario [reimpostare il dispositivo](#reset-a-surface-hub) o, se non funziona, recuperarlo dal cloud.

1. Individuare l'interruttore di alimentazione nella parte inferiore del mozzo della superficie. L'interruttore di alimentazione si trova accanto alla connessione del cavo di alimentazione. Per altre informazioni sull'interruttore di alimentazione, vedere la [Guida alla preparazione del sito hub Surface (PDF)](surface-hub-site-readiness-guide.md).

2. Mentre l'hub Surface Visualizza la schermata iniziale, usare l'interruttore Power per disattivare l'hub Surface.

3. Usare l'interruttore di accensione per riattivare il mozzo della superficie. Il dispositivo viene avviato e viene visualizzata la schermata del logo Surface Hub. Quando vedi puntini di filatura sotto il logo di Surface Hub, usa l'interruttore Power per disattivare di nuovo il mozzo della superficie.  

4. Ripetere il passaggio 3 3 volte oppure finché l'hub Surface non Visualizza il messaggio "preparazione della riparazione automatica". Dopo aver visualizzato questo messaggio, l'hub Surface Visualizza la schermata di ripristino di Windows.

5. Selezionare **Opzioni avanzate**.

6. Selezionare **Recupera dal cloud**. (Facoltativamente, è possibile selezionare **Reimposta**. Tuttavia, il **recupero dal cloud** è l'approccio consigliato.

   ![Ripristino dal cloud](images/recover-from-cloud.png)
7. Se viene chiesto di immettere la chiave BitLocker, eseguire una delle operazioni seguenti:

   - Per mantenere le informazioni protette da BitLocker nell'hub di Surface, immettere la chiave BitLocker.
   - Per annullare le informazioni protette, selezionare **Ignora l'unità**  

8. Quando viene richiesto, selezionare **Reinstalla**.

    ![Reinstalla](images/reinstall.png)

9. Per ripartizionare il disco, selezionare **Sì**.

   ![Ripartizione](images/repartition.png)

   Prima di tutto, il processo di ripristino Scarica l'immagine del sistema operativo dal cloud.  

   ![download 97& in corso](images/recover-progress.png)

   Al termine del download, il processo di ripristino Ripristina il mozzo della superficie in base alle opzioni selezionate.
   

## Supporto tecnico

Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).


## Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

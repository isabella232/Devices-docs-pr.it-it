---
title: Reimpostare o ripristinare un Surface Hub
description: Descrive i processi di reimpostazione e ripristino per il Surface Hub e fornisce istruzioni.
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: reset Surface Hub, recover
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/10/2021
ms.localizationpriority: medium
ms.openlocfilehash: ee8ac1129aab34afeb3be783133681fe80434831
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911021"
---
# <a name="reset-or-recover-a-surface-hub"></a>Reimpostare o ripristinare un Surface Hub

In questo articolo viene descritto come reimpostare o ripristinare un Microsoft Surface Hub.  

[Reimpostando il Surface Hub](#reset-a-surface-hub) il sistema operativo viene riportato all'ultimo aggiornamento cumulativo Windows e vengono rimossi tutti i file utente locali e le informazioni di configurazione. Le informazioni rimosse includono quanto segue:

- L'account del dispositivo
- Informazioni sull'account per gli amministratori locali del dispositivo
- Informazioni sull'aggiunta a un dominio o azure AD
- Informazioni di registrazione di Gestione dispositivi mobili (MDM)
- Informazioni di configurazione impostate tramite MDM o l Impostazioni app

[Anche il ripristino di Surface Hub dal cloud](#recover-a-surface-hub-from-the-cloud) rimuove queste informazioni. Inoltre, il Surface Hub scarica una nuova immagine del sistema operativo e la installa. È possibile specificare se il processo di ripristino mantiene altre informazioni archiviate nel Surface Hub. La stessa immagine del sistema operativo viene utilizzata dallo strumento di ripristino [di Surface Hub](surface-hub-recovery-tool.md) se è necessario ripristinare un Surface Hub per il quale non è possibile utilizzare nessuna di queste opzioni.

## <a name="reset-a-surface-hub"></a>Reimpostare un Surface Hub

Potrebbe essere necessario reimpostare il Surface Hub per motivi come i seguenti:

- Si sta riconfigurando il dispositivo per un nuovo spazio riunioni e si desidera riconfigurarlo.
- Vuoi modificare la modalità di gestione locale del dispositivo.
- Il nome utente o la password dell'account del dispositivo o dell'account amministratore è stato perso.
- Dopo aver installato un aggiornamento, le prestazioni del dispositivo diminuiscono.

Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.

> [!WARNING]
> Il processo di reimpostazione del dispositivo può richiedere fino a sei ore. Non disattivare o scollegare il Surface Hub fino al termine del processo. Se interrompi il processo, il dispositivo diventa inoperabile. Il dispositivo richiede un servizio di garanzia per poter diventare nuovamente funzionante.

1. Nel dispositivo Surface Hub apri **Impostazioni**.

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra Impostazioni'app per Surface Hub.](images/sh-settings.png)

2. Selezionare **Aggiorna & sicurezza**.

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra il gruppo Update & Security Impostazioni app per Surface Hub.](images/sh-settings-update-security.png)

3. Selezionare **Ripristino**e quindi, in **Reimposta dispositivo,** selezionare **Introduzione.**

   > [!IMPORTANT]
   > Assicurati di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, come verrà richiesto in un secondo momento. Per altre informazioni, vedi [Salvare la chiave di BitLocker.](save-bitlocker-key-surface-hub.md) Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker. Se si ignora il prompt, la reimpostazione avrà esito negativo.
   
   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra l'opzione Reimposta dispositivo nell Impostazioni app per Surface Hub.](images/sh-settings-reset-device.png)

   Al termine del processo di reimpostazione, il Surface Hub avvia di [nuovo il programma di prima](first-run-program-surface-hub.md) esecuzione. Se il processo di reimpostazione rileva un problema, il Surface Hub viene riportato all'immagine del sistema operativo esistente in precedenza e quindi viene visualizzata la schermata iniziale.

<span id="cloud-recovery" />

## <a name="recover-a-surface-hub-from-the-cloud"></a>Ripristinare un dispositivo Surface Hub dal cloud

Se per qualche motivo il Surface Hub diventa inutilizzabile, è comunque possibile ripristinarlo dal cloud senza l'assistenza del supporto Tecnico Microsoft. Il Surface Hub può scaricare una nuova immagine del sistema operativo dal cloud e usarla per reinstallare il sistema operativo.

Potrebbe essere necessario utilizzare questo tipo di processo di ripristino nelle circostanze seguenti:

- [Il Surface Hub o i relativi account sono stati inseriti in uno stato instabile](#recover-a-surface-hub-in-a-bad-state)
- [Il Surface Hub è bloccato](#recover-a-locked-surface-hub)

>[!IMPORTANT]
>Il **processo Di ripristino dal cloud** richiede una connessione cablata che fornisce connettività Internet aperta (nessun proxy o altre richieste di autenticazione).

### <a name="recover-a-surface-hub-in-a-bad-state"></a>Ripristinare un dispositivo Surface Hub in uno stato non valido

Se l'account del dispositivo entra in uno stato instabile o se l'account amministratore riscontra problemi, puoi usare l'app Impostazioni per avviare il processo di ripristino cloud. Devi usare il processo di ripristino cloud solo quando il processo di [reimpostazione](#reset-a-surface-hub) del dispositivo non risolve il problema.

1. Nella pagina Surface Hub, selezionare **Impostazioni** &gt; **aggiornamento & sicurezza** &gt; **ripristino**.

2. In **Ripristina dal cloud**seleziona **Riavvia ora.**

   > [!div class="mx-imgBorder"]
   > ![ripristino dal cloud.](images/recover-from-the-cloud.png)

### <a name="recover-a-locked-surface-hub"></a>Ripristinare un dispositivo Surface Hub bloccato

In rari casi, un dispositivo Surface Hub potrebbe riscontrare un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione. In questo caso, il dispositivo si riavvia automaticamente e tenta di nuovo l'operazione. Tuttavia, se l'operazione non riesce più volte, il dispositivo si blocca automaticamente per proteggere i dati dell'utente. Per sbloccarlo, devi [reimpostare il dispositivo](#reset-a-surface-hub) o, se non funziona, recuperarlo dal cloud.

1. Individuare l'interruttore di alimentazione nella parte inferiore Surface Hub. L'interruttore di alimentazione è accanto alla connessione del cavo di alimentazione. Per ulteriori informazioni sull'interruttore di alimentazione, vedere Surface Hub [Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).

2. Mentre nella Surface Hub viene visualizzata la schermata iniziale, utilizzare l'interruttore di alimentazione per disattivare l'Surface Hub.

3. Utilizzare l'interruttore di alimentazione per riattivare Surface Hub accensione. Il dispositivo viene avviato e visualizza la Surface Hub logo. Quando vedi punti rotanti sotto il logo Surface Hub, usa l'interruttore di alimentazione per disattivare Surface Hub di nuovo.  

4. Ripetere il passaggio 3 tre volte o finché non viene visualizzato Surface Hub messaggio "Preparazione del ripristino automatico". Dopo aver visualizzato questo messaggio, il Surface Hub viene visualizzata la Ambiente ripristino Windows schermo.
 
5. Selezionare **Ripristina**. 

6. Se viene richiesto di immettere la chiave BitLocker, eseguire una delle operazioni seguenti:
   - Per conservare le informazioni protette da BitLocker nel Surface Hub, immettere la chiave BitLocker.
   - Per eliminare le informazioni protette, selezionare Ignora questa unità

7. Seleziona **Download cloud.** 

   ![Download cloud.](images/recover-cloud-download.png)

   >[!IMPORTANT]
   >Se viene visualizzato un messaggio di errore che indica **Impossibile scaricare**, selezionare **Annulla** e quindi **reimpostare di** nuovo.

8. Selezionare **Pulire completamente l'unità.**
 
   ![ripristinare e pulire completamente l'unità.](images/recover-fully-clean-drive.png)

9. Ti verrà chiesto **Se sei pronto per reimpostare questo dispositivo?**. Selezionare **Ripristina**. 
   
   ![ripristinare e confermare la reimpostazione.](images/recover-confirm-reset.png)

10. Il download inizia e il processo di ripristino indica **reimpostazione di questo dispositivo.**

    ![ripristino visualizzato in corso.](images/recover-in-progress.png)

## <a name="contact-support"></a>Supporto tecnico

Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).


## <a name="related-topics"></a>Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

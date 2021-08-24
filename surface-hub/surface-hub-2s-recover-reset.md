---
title: Reimpostazione e ripristino per Surface Hub 2S
description: Informazioni su come ripristinare e reimpostare Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/05/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 28e067852422dd8c4a4b82c337e94eaa94290fd9
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911361"
---
# <a name="reset-and-recovery-for-surface-hub-2s"></a>Reimpostazione e ripristino per Surface Hub 2S

Se si verificano problemi con Surface Hub 2S, è possibile reimpostare le impostazioni di fabbrica o ripristinare il dispositivo utilizzando un'unità USB.

Per iniziare, accedi a Surface Hub 2S con credenziali di amministratore, apri l'app **Impostazioni,** seleziona Aggiorna & **sicurezza**e quindi seleziona **Ripristino**.

## <a name="reset-the-device"></a>Reimpostare il dispositivo

   > [!IMPORTANT]
   > Assicurati di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, come verrà richiesto in un secondo momento. Per altre informazioni, vedi [Salvare la chiave di BitLocker.](save-bitlocker-key-surface-hub.md)

1. Per reimpostare il dispositivo, selezionare **Informazioni di base**.

2. Quando viene **visualizzata la finestra Pronto per reimpostare il** dispositivo, selezionare **Reimposta**. 
  
   > [!IMPORTANT]
   > Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker. Se si ignora il prompt, la reimpostazione avrà esito negativo. Una volta immessa la chiave BitLocker, Hub reinstalla il sistema operativo dalla partizione di ripristino. Il completamento dell'operazione potrebbe richiedere fino a un'ora.
  
3. Per riconfigurare il dispositivo, eseguire il programma di installazione della prima volta.

4. Se gestisci il dispositivo usando Microsoft Intune o un'altra soluzione di gestione dei dispositivi mobili, ritira ed elimina il record precedente e quindi registra di nuovo il nuovo dispositivo. Per altre informazioni, vedi [Rimuovere i dispositivi tramite cancellazione,](https://docs.microsoft.com/intune/devices-wipe)ritiro o annullamento manuale della registrazione del dispositivo.

   > [!div class="mx-imgBorder"]
   > ![*Reimpostazione e ripristino per Surface Hub 2S*.](images/sh2-reset.png)
   <br/>*Figura 1. Reimpostazione e ripristino per Surface Hub 2S* 

## <a name="recover-surface-hub-2s-by-using-a-usb-recovery-drive"></a>Ripristinare Surface Hub 2S utilizzando un'unità di ripristino USB

Novità di Surface Hub 2S, ora puoi reinstallare il dispositivo usando un'immagine di ripristino.

### <a name="recovery-from-a-usb-drive"></a>Ripristino da un'unità USB

Usando Surface Hub 2S, puoi reinstallare il dispositivo usando un'immagine di ripristino. In questo modo, puoi reinstallare il dispositivo nelle impostazioni di fabbrica se hai perso la chiave BitLocker o se non hai più le credenziali di amministratore per l'app Impostazioni.

>[!NOTE]
>Usa un'unità USB 3.0 con 8 GB o 16 GB di spazio di archiviazione, formattato come FAT32.

1. Da un PC separato, scarica l'.zip di ripristino dei file dal sito Web [di Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) e quindi torna a queste istruzioni. 

1. Nella casella di ricerca sulla barra delle applicazioni immetti unità di **ripristino**e quindi seleziona Crea un'unità **di ripristino** o Unità di **ripristino** dai risultati. Potrebbe essere necessario immettere una password di amministratore o confermare la scelta.

1. Nella casella **Controllo account utente** selezionare **Sì.**

1. Assicurarsi di deselezionare la casella di controllo Backup dei file di **sistema nell'unità di** ripristino e quindi selezionare **Avanti**.

1. Seleziona l'unità USB e quindi seleziona **Avanti > Crea**.  Alcune utilità devono essere copiate nell'unità di ripristino, pertanto l'operazione potrebbe richiedere alcuni minuti.

1. Quando l'unità di ripristino è pronta, selezionare **Fine.**

1. Fare doppio clic sull'immagine di .zip file scaricato in precedenza per aprirla.

1. Seleziona tutti i file dalla cartella dell'immagine di ripristino, copiali nella radice dell'unità USB e quindi seleziona Scegli per sostituire i **file nella destinazione.**

1. Dopo aver completato la copia dei file, seleziona l'icona Rimuovi **hardware** ed espulso in modo sicuro nella barra delle applicazioni e rimuovi l'unità USB.

1. Connessione'unità USB a qualsiasi porta USB-C o USB-A Surface Hub 2S.

1. Disattiva Hub e quindi eseguire la procedura seguente per l'avvio dall'unità USB:

   1. Premendo il pulsante Volume giù, premere il pulsante Alimentazione.
   1. Continuare a premere entrambi i pulsanti finché non viene visualizzato Windows logo.
   1. Rilascia il pulsante Di alimentazione, ma continua a tenere premuto il pulsante Volume fino all'avvio dell'interfaccia utente di installazione.

      ![*Usare i pulsanti volume giù e alimentazione per avviare il ripristino*.](images/sh2-keypad.png)
      <br>*Figura 2. Pulsanti volume e alimentazione*

1. Nella schermata di selezione della lingua, selezionare la lingua di visualizzazione per il Surface Hub 2S.

1. Selezionare **Recupera da un'unità** e **Pulire completamente l'unità**e quindi selezionare **Recupera**. Se ti viene richiesto di specificare una chiave BitLocker, seleziona **Ignora questa unità.** Surface Hub 2S viene riavviato più volte e richiede circa 30 minuti per completare il processo di ripristino.

Quando viene visualizzata la prima schermata di configurazione, rimuovi l'unità USB.

## <a name="contact-support"></a>Supporto tecnico

Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).

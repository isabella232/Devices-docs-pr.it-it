---
title: Ripristino e ripristino per Surface Hub 2S
description: Scopri come ripristinare e reimpostare Surface Hub 2S.
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
ms.openlocfilehash: 64ceee291d3d3e067f581707d9431fa92398c785
ms.sourcegitcommit: ecb4909c091e69b7bdb1faacfc8c34b480dc884b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2021
ms.locfileid: "11342976"
---
# Ripristino e ripristino per Surface Hub 2S

Se si verificano problemi con Surface Hub 2S, puoi ripristinare le impostazioni predefinite del dispositivo usando un'unità USB.

Per iniziare, accedi a Surface Hub 2S con **** le credenziali di amministratore, apri l'app Impostazioni, seleziona Aggiornamento **& sicurezza**e quindi **seleziona Ripristino.**

## Reimpostare il dispositivo

   > [!IMPORTANT]
   > Assicurati di avere a disposizione la chiave BitLocker prima di reimpostare il dispositivo, come ti verrà richiesto in seguito. Per altre informazioni, vedi [Salvare la chiave BitLocker.](save-bitlocker-key-surface-hub.md)

1. Per reimpostare il dispositivo, selezionare **Introduzione.**

2. Quando viene **visualizzata la finestra Pronto per la** reimpostazione del dispositivo, selezionare **Reimposta.** 
  
   > [!IMPORTANT]
   > Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker. Se si ignora tale richiesta, il ripristino avrà esito negativo. Una volta immessa la chiave BitLocker, l'hub reinstalla il sistema operativo dalla partizione di ripristino. Il completamento dell'operazione potrebbe richiedere fino a un'ora.
  
3. Per riconfigurare il dispositivo, eseguire il programma di installazione della prima volta.

4. Se si gestisce il dispositivo con Microsoft Intune o un'altra soluzione di gestione dei dispositivi mobili, ritirare ed eliminare il record precedente e quindi registrare di nuovo il nuovo dispositivo. Per altre informazioni, vedi [Rimuovere i dispositivi tramite cancellazione,](https://docs.microsoft.com/intune/devices-wipe)ritiro o annullamento manuale della registrazione del dispositivo.

   > [!div class="mx-imgBorder"]
   > ![*Ripristino e ripristino per Surface Hub 2S*](images/sh2-reset.png)
   <br/>*Figura 1. Ripristino e ripristino per Surface Hub 2S* 

## Ripristinare Surface Hub 2S usando un'unità di ripristino USB

Novità di Surface Hub 2S, ora puoi reinstallare il dispositivo usando un'immagine di ripristino.

### Ripristino da un'unità USB

Con Surface Hub 2S puoi reinstallare il dispositivo usando un'immagine di ripristino. In questo modo, puoi reinstallare il dispositivo nelle impostazioni di fabbrica se hai perso la chiave BitLocker o se non hai più le credenziali di amministratore per l'app Impostazioni.

>[!NOTE]
>Usa un'unità USB 3.0 con 8 GB o 16 GB di spazio di archiviazione, formattato come FAT32.

1. Da un PC separato, scarica l'immagine di ripristino del file ZIP dal sito [Web di Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) e quindi torna a queste istruzioni. 

1. Nella casella di ricerca sulla barra delle applicazioni immetti l'unità di ripristino **e**quindi seleziona Crea un'unità di **ripristino** o **Un'unità** di ripristino dai risultati. Potrebbe essere necessario immettere una password di amministratore o confermare la scelta.

1. Nella casella **Controllo account utente** selezionare **Sì.**

1. Assicurarsi di deselezionare la casella di controllo Backup dei file di **sistema nell'unità** di ripristino e quindi selezionare **Avanti.**

1. Seleziona l'unità USB e quindi seleziona **Avanti > crea.**  Alcune utilità devono essere copiate nell'unità di ripristino, pertanto l'operazione potrebbe richiedere alcuni minuti.

1. Quando l'unità di ripristino è pronta, selezionare **Fine.**

1. Fare doppio clic sul file ZIP dell'immagine di ripristino precedentemente scaricato per aprirlo.

1. Seleziona tutti i file dalla cartella dell'immagine di ripristino, copiali nella radice dell'unità USB e quindi seleziona Scegli di sostituire i **file nella destinazione.**

1. Dopo aver completato la copia dei file, seleziona l'icona Rimuovi hardware ed **eject media** in modo sicuro sulla barra delle applicazioni e rimuovi l'unità USB.

1. Connetti l'unità USB a qualsiasi porta USB-C o USB-A in Surface Hub 2S.

1. Disattiva l'hub e quindi prendi questi passaggi per eseguire l'avvio dall'unità USB:

   1. Mentre premi il pulsante Volume down, premi il pulsante Di alimentazione.
   1. Continua a premere entrambi i pulsanti finché non viene visualizzato il logo Windows.
   1. Rilascia il pulsante di alimentazione, ma continua a tenere premuto il pulsante Volume down fino all'inizio dell'interfaccia utente di installazione.

      ![*Usare i pulsanti di accensione e di interruzione del volume per avviare il ripristino*](images/sh2-keypad.png)
      <br>*Figura 2. Pulsanti volume e alimentazione*

1. Nella schermata di selezione della lingua seleziona la lingua di visualizzazione per il dispositivo Surface Hub 2S.

1. Selezionare **Recupera da un'unità** e **Pulire completamente l'unità,** quindi selezionare **Recupera.** Se ti viene richiesto di specificare una chiave BitLocker, seleziona **Ignora questa unità.** Surface Hub 2S viene riavviato più volte e richiede circa 30 minuti per completare il processo di ripristino.

Quando viene visualizzata la prima schermata di configurazione, rimuovi l'unità USB.

## Supporto tecnico

Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto.](https://support.microsoft.com/supportforbusiness/productselection)

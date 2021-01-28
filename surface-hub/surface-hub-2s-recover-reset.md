---
title: Reset e ripristino per Surface Hub 2S
description: Informazioni su come recuperare e ripristinare Surface Hub 2S.
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
ms.openlocfilehash: 88f5d912f7505aecaa5bd7ba659acab2d6c4fa1a
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304809"
---
# Reset e ripristino per Surface Hub 2S

Se si verificano problemi con Surface Hub 2S, è possibile reimpostare il dispositivo in base alle impostazioni di fabbrica o ripristinarlo usando un'unità USB.

Per iniziare, accedi a Surface Hub 2S con le credenziali di amministratore, Apri l'app **Impostazioni** , seleziona **Aggiorna & sicurezza**e quindi seleziona **ripristino**.

## Reimpostare il dispositivo

   > [!IMPORTANT]
   > Verificare di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, dato che verrà richiesto in un secondo momento. Per altre informazioni, vedere [salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md).

1. Per reimpostare il dispositivo, selezionare **inizia**.

2. Quando viene visualizzata la finestra **pronto per reimpostare il dispositivo** , selezionare **Reimposta**. 
  
   > [!IMPORTANT]
   > Quando l'hub viene riavviato nella partizione di ripristino, verrà chiesto di immettere la chiave BitLocker. Se si ignora il messaggio, il comando Reimposta non riesce. Dopo aver immesso la chiave BitLocker, l'hub reinstalla il sistema operativo dalla partizione di ripristino. Il completamento può richiedere fino a un'ora.
  
3. Per riconfigurare il dispositivo, eseguire il programma di installazione per la prima volta.

4. Se si gestisce il dispositivo con Microsoft Intune o un'altra soluzione di gestione di dispositivi mobili, ritirare ed eliminare il record precedente e quindi ripetere la registrazione del nuovo dispositivo. Per altre informazioni, vedere [rimuovere i dispositivi tramite wipe, ritirarsi o annullare la registrazione manuale del dispositivo](https://docs.microsoft.com/intune/devices-wipe).

   > [!div class="mx-imgBorder"]
   > ![* Reset e ripristino per Surface Hub 2S *](images/sh2-reset.png)
   <br/>*Figura 1. Reset e ripristino per Surface Hub 2S* 

## Recuperare Surface Hub 2S usando un'unità di ripristino USB

Nuovo in Surface Hub 2S è ora possibile reinstallare il dispositivo usando un'immagine di ripristino.

### Ripristino da un'unità USB

Con Surface Hub 2S puoi reinstallare il dispositivo usando un'immagine di ripristino. In questo modo, puoi reinstallare il dispositivo nelle impostazioni di fabbrica se hai perso la chiave BitLocker o se non hai più le credenziali di amministratore per l'app Impostazioni.

>[!NOTE]
>Usare un'unità USB 3,0 con 8 GB o 16 GB di spazio di archiviazione, formattati come FAT32.

1. Da un PC separato scaricare l'immagine di ripristino del file zip dal [sito Web Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) e quindi tornare a queste istruzioni. 

1. Decomprimere il file scaricato nella radice dell'unità USB.  

1. Connettere l'unità USB a qualsiasi porta USB-C o USB-A su Surface Hub 2S.

1. Disattivare il dispositivo:

   1. Mentre si preme il pulsante volume giù, premere il pulsante di alimentazione.
   1. Continua a premere entrambi i pulsanti finché non viene visualizzato il logo Windows.
   1. Rilasciare il pulsante di alimentazione, ma continuare a tenere premuto il pulsante volume giù fino a quando non inizia l'interfaccia utente di installazione.

      ![* Usare i pulsanti volume giù e Power per avviare il ripristino *](images/sh2-keypad.png)
      <br>*Figura 2. Pulsanti di alimentazione e di volume*

1. Nella schermata Selezione lingua selezionare la lingua di visualizzazione per il mozzo della superficie 2S.

1. Selezionare **Recupera da un'unità** e **pulire completamente l'unità**e quindi selezionare **Recupera**. Se viene richiesta una chiave BitLocker, selezionare **Ignora l'unità**. Surface Hub 2S viene riavviato più volte e impiega circa 30 minuti per completare il processo di ripristino.

Quando viene visualizzata la schermata di configurazione per la prima volta, rimuovere l'unità USB.

## Supporto tecnico

Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).

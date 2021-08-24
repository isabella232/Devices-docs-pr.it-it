---
title: Aggiornare il firmware della penna in Surface Hub 2S
description: Questa pagina descrive come aggiornare il firmware per la penna Surface Hub 2.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 04/15/2021
ms.localizationpriority: Medium
ms.openlocfilehash: fb0948623ec9c12aa818e4829285ea77229bf71d
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911581"
---
# <a name="update-pen-firmware-on-surface-hub-2s"></a>Aggiornare il firmware della penna in Surface Hub 2S

Puoi aggiornare il firmware Surface Hub 2 penna da Windows Update for Business o scaricando l'aggiornamento del firmware in un PC separato. Il firmware aggiornato è disponibile Windows update a partire dal 26 febbraio 2020. 

## <a name="update-pen-firmware-using-windows-update-for-business"></a>Aggiornare il firmware della penna Windows Update for Business

In questa sezione viene descritto come aggiornare il firmware della penna tramite i cicli di manutenzione automatizzati per Windows Update, configurato per impostazione predefinita per l'esecuzione notturna alle 3 del giorno. Dovrai pianificare il completamento di due cicli di manutenzione prima di applicare l'aggiornamento alla penna Surface Hub 2. In alternativa, come qualsiasi altro aggiornamento, puoi usare Windows Update for Business (WUfB) per applicare il firmware della penna. Per ulteriori informazioni, vedere [Managing Windows updates on Surface Hub](manage-windows-updates-for-surface-hub.md).

1. Assicurati che la Surface Hub 2 penna sia associata Surface Hub 2S: **** tieni premuto il pulsante superiore finché la luce LED dell'indicatore bianco non inizia a lampeggiare.

    > [!div class="mx-imgBorder"]
    > ![Surface Hub 2 penna.](images/sh2-pen-1.png)

2. In Surface Hub, accedere come amministratore, **aprire**Impostazioni e quindi cercare nuovi Bluetooth dispositivi.

3. Selezionare la penna per completare il processo di associazione.

4. Premi il **pulsante** superiore della penna per applicare l'aggiornamento. Il completamento potrebbe richiedere fino a due ore.

## <a name="update-pen-firmware-by-downloading-to-separate-pc"></a>Aggiornare il firmware della penna scaricandolo in un PC separato

Puoi aggiornare il firmware su Surface Hub 2 penna da un PC separato che esegue Windows 10. Questo metodo consente inoltre di verificare che il firmware della penna sia stato aggiornato correttamente alla versione più recente.

1. Associa la Surface Hub 2 penna al PC Bluetooth: tieni premuto il **** pulsante superiore finché la luce LED dell'indicatore bianco non inizia a lampeggiare.

    > [!div class="mx-imgBorder"]
    > ![Surface Hub 2 penna.](images/sh2-pen-1.png)

2. Nel PC cerca nuovi dispositivi Bluetooth computer.

3. Selezionare la penna per completare il processo di associazione.

4. Disconnettere tutte le Surface Hub penne 2s prima di avviare un nuovo aggiornamento.

5. Scarica lo [Surface Hub 2 Pen Firmware Update Tool](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip) nel PC.

6. Eseguire **PenCfu.exe.** Lo stato dell'installazione viene visualizzato nello strumento. L'aggiornamento potrebbe richiedere alcuni minuti. 


## <a name="check-firmware-version-of-surface-hub-2-pen"></a>Controllare la versione del firmware di Surface Hub 2 penna

1. Esegui **get_version.bat** e premi il **pulsante** superiore sulla penna.

2. Lo strumento segnala la versione firmware della penna. 

   Esempio:
    - Il vecchio firmware è 468.2727.368
    - Il nuovo firmware è 468.3347.368

## <a name="command-line-options"></a>Opzioni della riga di comando

È possibile eseguire Surface Hub 2 Pen Firmware Update Tool (PenCfu.exe) dalla riga di comando.

1. Associa la penna al PC e fai clic **sul pulsante** superiore della penna.

2. Fai doppio ** clicPenCfu.exe** per avviare l'aggiornamento del firmware. Tieni presente che il file di configurazione e i file di immagine del firmware devono essere archiviati nella stessa cartella dello strumento.

3. Per ulteriori opzioni, ** eseguirePenCfu.exe -h** per visualizzare i parametri disponibili, come indicato nella tabella seguente.  

   Esempio: `PenCfu.exe -h`

4. Immetti **CTRL+C per** arrestare lo strumento in modo sicuro.


| Comando | Descrizione |
| -------------- |---------------------------- |
| -h guida        | Visualizza la Guida dell'interfaccia della riga di comando dello strumento ed esci. |
| -v versione     | Visualizzare la versione dello strumento ed uscire. |
| -l log-filter  | Impostare un livello di filtro per il file di registro. I messaggi di registro hanno 4 livelli possibili: DEBUG (minimo), INFO, AVVISO ed ERRORE (massimo). L'impostazione di un livello di filtro del registro consente di filtrare i messaggi di registro solo per i messaggi con lo stesso livello o superiore. Ad esempio, se il livello di filtro è impostato su AVVISO, verranno registrati solo i messaggi DI AVVISO ed ERRORE. Per impostazione predefinita, questa opzione è impostata su OFF, che disabilita la registrazione. |
| -g get-version | Se specificato, lo strumento otterrà solo la versione FW della penna connessa corrispondente al file di configurazione archiviato nella stessa cartella dello strumento.  |


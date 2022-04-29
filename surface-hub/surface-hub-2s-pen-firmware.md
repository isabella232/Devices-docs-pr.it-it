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
ms.openlocfilehash: b1955f1806c963ce553d5d2eef99e72e90c5adfe
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497719"
---
# <a name="update-pen-firmware-on-surface-hub-2s"></a>Aggiornare il firmware della penna in Surface Hub 2S

È possibile aggiornare il firmware su Surface Hub penna 2 da Windows Update per le aziende o scaricando l'aggiornamento del firmware in un PC separato. Il firmware aggiornato è disponibile da Windows Update a partire dal 26 febbraio 2020. 

## <a name="update-pen-firmware-using-windows-update-for-business"></a>Aggiornare il firmware della penna usando Windows Update per le aziende

Questa sezione descrive come aggiornare il firmware della penna tramite i cicli di manutenzione automatizzati per Windows Update, configurati per impostazione predefinita in modo che si verifichino di notte alle 3 del mattino. È necessario pianificare il completamento di due cicli di manutenzione prima di applicare l'aggiornamento alla penna Surface Hub 2. In alternativa, come qualsiasi altro aggiornamento, è possibile usare Windows Update for Business (WUfB) per applicare il firmware della penna. Per altre informazioni, vedere [Gestione degli aggiornamenti Windows in Surface Hub](manage-windows-updates-for-surface-hub.md).

1. Assicurarsi che la penna Surface Hub 2 sia abbinata a Surface Hub 2S: premere e tenere premuto il pulsante **superiore** fino a quando la luce LED dell'indicatore bianco non inizia a lampeggiare.

    > [!div class="mx-imgBorder"]
    > ![Surface Hub 2 penna.](images/sh2-pen-1.png)

2. In Surface Hub accedere come amministratore, aprire **Impostazioni** e quindi cercare nuovi dispositivi Bluetooth.

3. Selezionare la penna per completare il processo di associazione.

4. Premere il pulsante **superiore** sulla penna per applicare l'aggiornamento. Il completamento può richiedere fino a due ore.

## <a name="update-pen-firmware-by-downloading-to-separate-pc"></a>Aggiornare il firmware della penna scaricando in un PC separato

È possibile aggiornare il firmware su Surface Hub penna 2 da un PC separato che esegue Windows 10 o Windows 11. Questo metodo consente anche di verificare che il firmware della penna sia stato aggiornato correttamente alla versione più recente.

1. Associare la penna Surface Hub 2 al PC con supporto per Bluetooth: premere e tenere premuto il pulsante **superiore** fino a quando la luce led indicatore bianco inizia a lampeggiare.

    > [!div class="mx-imgBorder"]
    > ![Surface Hub 2 penna.](images/sh2-pen-1.png)

2. Nel PC cercare nuovi dispositivi Bluetooth.

3. Selezionare la penna per completare il processo di associazione.

4. Disconnettere tutte le altre penne Surface Hub 2s prima di avviare un nuovo aggiornamento.

5. Scaricare il [Surface Hub 2 Pen Firmware Update Tool](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip) sul PC.

6. Eseguire **PenCfu.exe.** Lo stato di avanzamento dell'installazione viene visualizzato nello strumento. Il completamento dell'aggiornamento potrebbe richiedere alcuni minuti. 


## <a name="check-firmware-version-of-surface-hub-2-pen"></a>Controllare la versione del firmware di Surface Hub 2 penna

1. Eseguire **get_version.bat** e premere il pulsante **superiore** sulla penna.

2. Lo strumento segnalerà la versione del firmware della penna. 

   Esempio:
    - Il firmware precedente è 468.2727.368
    - Il nuovo firmware è 468.3347.368

## <a name="command-line-options"></a>Opzioni della riga di comando

È possibile eseguire Surface Hub 2 Pen Firmware Update Tool (PenCfu.exe) dalla riga di comando.

1. Associare la penna al PC e fare clic sul pulsante **superiore** sulla penna.

2. Fare doppio clic **PenCfu.exe** per avviare l'aggiornamento del firmware. Si noti che il file di configurazione e i file di immagine del firmware devono essere archiviati nella stessa cartella dello strumento.

3. Per altre opzioni, eseguire **PenCfu.exe -h** per visualizzare i parametri disponibili, come indicato nella tabella seguente.  

   Esempio: `PenCfu.exe -h`

4. Immettere **CTRL+C** per arrestare lo strumento in modo sicuro.


| Comando | Descrizione |
| -------------- |---------------------------- |
| -h guida        | Visualizzare la Guida e uscire dall'interfaccia della riga di comando dello strumento. |
| -v versione     | Visualizzare la versione e l'uscita dello strumento. |
| -l log-filter  | Impostare un livello di filtro per il file di log. I messaggi di log hanno 4 livelli possibili: DEBUG (più basso), INFO, AVVISO ed ERRORE (massimo). L'impostazione di un livello di filtro del log consente di filtrare i messaggi di log solo per i messaggi con lo stesso livello o superiore. Ad esempio, se il livello di filtro è impostato su AVVISO, verranno registrati solo i messaggi WARNING e ERROR. Per impostazione predefinita, questa opzione è impostata su OFF, che disabilita la registrazione. |
| -g get-version | Se specificato, lo strumento otterrà solo la versione FW della penna connessa corrispondente al file di configurazione archiviato nella stessa cartella dello strumento.  |


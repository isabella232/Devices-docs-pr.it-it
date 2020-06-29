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
ms.date: 02/26/2020
ms.localizationpriority: Medium
ms.openlocfilehash: c0ad8f275d2476e42c9a5bd3f1130fbca85a5599
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833056"
---
# Aggiornare il firmware della penna in Surface Hub 2S

È possibile aggiornare il firmware nella penna Surface Hub 2 da Windows Update for business o scaricando l'aggiornamento del firmware in un PC separato. Il firmware aggiornato è disponibile in Windows Update a partire dal 26 febbraio 2020. 

## Aggiornare il firmware della penna tramite Windows Update for business

Questa sezione descrive come aggiornare il firmware della penna tramite i cicli di manutenzione automatici per Windows Update, configurati per impostazione predefinita in modo che si verifichino ogni sera alle 3 del mattino. Prima di applicare l'aggiornamento alla penna Surface Hub 2, sarà necessario pianificare il completamento di due cicli di manutenzione. In alternativa, come per qualsiasi altro aggiornamento, è possibile usare Windows Server Update Services (WSUS) per applicare il firmware della penna. Per altre informazioni, vedere [gestione degli aggiornamenti di Windows in Surface Hub](manage-windows-updates-for-surface-hub.md).

1. Verificare che la penna Surface Hub 2 sia associata a Surface Hub 2S: tenere premuto il pulsante **superiore** fino a quando il LED indicatore bianco non inizia a lampeggiare. <br>
![Penna Surface Hub 2](images/sh2-pen-1.png) <br>
2. In Surface Hub, accedi come amministratore, Apri **Impostazioni**e quindi analizza per nuovi dispositivi Bluetooth.
3. Selezionare la penna per completare il processo di associazione.
4. Premere il pulsante **superiore** della penna per applicare l'aggiornamento. Il completamento può richiedere fino a due ore.

## Aggiornare il firmware della penna scaricando un PC separato

È possibile aggiornare il firmware nella penna Surface Hub 2 da un PC separato con Windows 10. Questo metodo consente inoltre di verificare che il firmware della penna sia stato aggiornato correttamente alla versione più recente.

1. Associare la penna Surface Hub 2 al PC con funzionalità Bluetooth: tenere premuto il pulsante **superiore** finché il LED indicatore bianco non inizia a lampeggiare. <br>
![Penna Surface Hub 2](images/sh2-pen-1.png) <br>
2. Nel PC eseguire la ricerca di nuovi dispositivi Bluetooth.
3. Selezionare la penna per completare il processo di associazione.
4. Prima di iniziare un nuovo aggiornamento, scollegare tutte le altre penne di Surface Hub 2S.
3. Scaricare lo [strumento di aggiornamento del firmware della penna Surface Hub 2](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Pen_Firmware_Tool.zip) nel PC.
4. Eseguire **PenCfu.exe.** Lo stato di installazione viene visualizzato nello strumento. Per completare l'aggiornamento, potrebbero essere necessarie diversi minuti. 


## Controllare la versione del firmware della penna Surface Hub 2

1. Eseguire **get_version.bat** e premere il pulsante **superiore** della penna.
2. Lo strumento segnalerà la versione del firmware della penna. Esempio:
    - Il vecchio firmware è 468.2727.368
    - Il nuovo firmware è 468.2863.369

## Opzioni della riga di comando

È possibile eseguire Surface Hub 2 Pen Firmware Update Tool (PenCfu.exe) dalla riga di comando.

1. Associare la penna al PC e fare clic sul pulsante **superiore** della penna.
2. Fare doppio clic su **PenCfu.exe** per avviare l'aggiornamento del firmware. Tieni presente che il file di configurazione e i file di immagine del firmware devono essere archiviati nella stessa cartella dello strumento.
3. Per altre opzioni, eseguire **PenCfu.exe-h** per visualizzare i parametri disponibili, come indicato nella tabella seguente.  
    - Esempio: PenCfu.exe-h
4. Immettere **CTRL + C** per arrestare in modo sicuro lo strumento.

 

| **Comando**    | **Descrizione**                                                                                                                                                                                                                                                                                                                                                                                |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -Guida di h        | Strumento Visualizza interfaccia della riga di comando e quindi Esci.                                                                                                                                                                                                                                                                                                                                             |
| -v versione     | Visualizzare la versione dello strumento e uscire.                                                                                                                                                                                                                                                                                                                                                                 |
| -filtro log-l  | Impostare un livello di filtro per il file di log. I messaggi di log hanno 4 livelli possibili: DEBUG (minimo), INFO, avviso ed errore (massimo). L'impostazione di filtri a livello di filtro log consente di registrare i messaggi solo con lo stesso livello o superiore. Ad esempio, se il livello di filtro è impostato su avviso, verranno registrati solo i messaggi di avviso e di errore. Per impostazione predefinita, questa opzione è impostata su disattivato, che disabilita la registrazione. |
| -g get-version | Se specificato, lo strumento otterrà solo la versione FW della penna connessa che corrisponde al file di configurazione archiviato nella stessa cartella dello strumento.                                                                                                                                                                                                                                    
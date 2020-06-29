---
title: Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni
description: informazioni sulla risoluzione dei problemi relativi all'hub di Surface per gli aggiornamenti automatici
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: Hub Surface, finestra di manutenzione, aggiornamento
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 117c18cfce6dfb84b4fe2156ea98198f96da2abf
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833819"
---
# Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni

In circostanze specifiche, Surface Hub installa gli aggiornamenti durante le ore lavorative anziché durante la normale finestra di manutenzione. Il dispositivo viene quindi riavviato, se necessario. Non è possibile usare il dispositivo fino al completamento del processo.

> [!NOTE]  
> Non si tratta di un comportamento previsto per la mancata finestra di manutenzione. Si verifica solo se il dispositivo non è aggiornato per un periodo di tempo prolungato.

## Causa
Per assicurarti che l'hub superficie rimanga disponibile per l'uso durante le ore lavorative, l'hub è configurato per eseguire funzioni amministrative durante una finestra di manutenzione definita in impostazioni (Vedi "Riferimenti"). Durante questo periodo di manutenzione, l'hub installa automaticamente gli aggiornamenti disponibili tramite Windows Update o Windows Server Update Service (WSUS). Una volta completati gli aggiornamenti, l'hub può essere riavviato.

Gli aggiornamenti possono essere installati durante la finestra di manutenzione solo se l'hub superficie è attivato ma non in uso o riservato. Ad esempio, se l'hub Surface è programmato per una riunione che dura 24 ore, gli eventuali aggiornamenti programmati per l'installazione verranno rinviati finché l'hub non sarà disponibile durante la finestra di manutenzione successiva. Se l'hub continua ad essere occupato e mancano più finestre di manutenzione, l'hub inizierà a installare e scaricare gli aggiornamenti. Questo problema può verificarsi durante o all'esterno della finestra di manutenzione. Una volta che il download e l'installazione sono iniziati, il dispositivo può essere riavviato.

## Per evitare questo problema

È importante impostare il tempo di manutenzione per l'hub di Surface per eseguire funzioni amministrative. La riservatezza del mozzo della superficie per intervalli di 24 ore o l'uso del dispositivo durante la finestra di manutenzione ritarda l'installazione degli aggiornamenti. Ti consigliamo di non usare o prenotare l'hub durante il periodo di manutenzione pianificata. Una finestra di due ore deve essere riservata per l'aggiornamento.

Un'opzione che puoi usare per controllare la disponibilità degli aggiornamenti è Windows Server Update Service (WSUS). WSUS fornisce il controllo sugli aggiornamenti installati e quando.

## Riferimenti 
 
[Aggiornare Surface Hub](first-run-program-surface-hub.md#update-the-surface-hub) 

[Finestra di manutenzione](manage-windows-updates-for-surface-hub.md#maintenance-window) 

[Distribuisci gli aggiornamenti di Windows10 con WindowsServer Update Services (WSUS)](/windows/deployment/update/waas-manage-updates-wsus) 



---
title: Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni
description: informazioni sulla risoluzione dei problemi Surface Hub sugli aggiornamenti automatici
ms.assetid: 6C09A9F8-F9CF-4491-BBFB-67A1A1DED0AA
keywords: surface hub, finestra di manutenzione, aggiornamento
ms.prod: surface-hub
ms.sitesec: library
author: Teresa-MOTIV
ms.author: v-tea
ms.topic: article
ms.localizationpriority: medium
ms.date: 04/15/2021
ms.openlocfilehash: 7df7857258c1baeedf4ff239eda17c66c93a531c
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11577026"
---
# <a name="surface-hub-may-install-updates-and-restart-outside-maintenance-hours"></a>Surface Hub può installare gli aggiornamenti e riavviare gli orari di manutenzione esterni

In circostanze specifiche, Surface Hub gli aggiornamenti vengono installati durante l'orario di ufficio anziché durante la normale finestra di manutenzione. Il dispositivo viene quindi riavviato, se necessario. Non puoi usare il dispositivo finché il processo non viene completato.

> [!NOTE]  
> Questo comportamento non è previsto per la mancanza di una finestra di manutenzione. Si verifica solo se il dispositivo non è aggiornato per un lungo periodo di tempo.

## <a name="cause"></a>Causa

Per garantire che Surface Hub sia disponibile per l'uso durante l'orario di ufficio, l'hub è configurato per eseguire funzioni amministrative durante una finestra di manutenzione definita in Impostazioni (vedere "Riferimenti", di seguito). Durante questo periodo di manutenzione, Hub installa automaticamente gli aggiornamenti disponibili tramite Windows Update o Windows Update for Business (WUfB). Una volta completati gli aggiornamenti, l'hub potrebbe riavviarsi.

Gli aggiornamenti possono essere installati durante la finestra di manutenzione solo se il Surface Hub è attivato ma non è in uso o riservato. Ad esempio, se il Surface Hub è pianificato per una riunione che dura 24 ore, tutti gli aggiornamenti pianificati per l'installazione verranno rinviati fino a quando l'hub non sarà disponibile durante la successiva finestra di manutenzione. Se l'hub continua a essere occupato e mancano più finestre di manutenzione, l'hub inizierà a installare e scaricare gli aggiornamenti. Ciò può verificarsi durante o all'esterno della finestra di manutenzione. Dopo l'inizio del download e dell'installazione, il dispositivo potrebbe riavviarsi.

## <a name="to-avoid-this-issue"></a>Per evitare questo problema

È importante riservare tempo di manutenzione per Surface Hub funzioni amministrative. La prenotazione del Surface Hub per intervalli di 24 ore o l'utilizzo del dispositivo durante la finestra di manutenzione ritarda l'installazione degli aggiornamenti. È consigliabile non usare o prenotare l'hub durante il periodo di manutenzione pianificato. Una finestra di due ore deve essere riservata per l'aggiornamento.

Un'opzione che puoi usare per controllare la disponibilità degli aggiornamenti è Windows Update for Business.

## <a name="learn-more"></a>Altre informazioni
 
- [Aggiornare Surface Hub](first-run-program-surface-hub.md#update-the-surface-hub) 
- [Finestra di manutenzione](manage-windows-updates-for-surface-hub.md#maintenance-window) 

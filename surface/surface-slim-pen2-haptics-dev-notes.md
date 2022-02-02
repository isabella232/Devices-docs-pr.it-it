---
title: Note per sviluppatori di Surface Slim Pen 2 aptiche
description: Questa pagina fornisce note sull'implementazione per gli sviluppatori di app che desiderano estendere Windows 11 funzionalità di input penna di Surface Slim Pen 2 per le aziende.
ms.prod: w11
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 12/07/2021
ms.reviewer: gusing
manager: laurawi
audience: itpro
ms.openlocfilehash: 8a3dbbdde85cfdceaf5674750a68fc21d3fcd877
ms.sourcegitcommit: e7d95d583429169eb65aae9034eab2347b1f04a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2022
ms.locfileid: "12338705"
---
# <a name="surface-slim-pen-2-haptics-dev-notes"></a>Note per sviluppatori di Surface Slim Pen 2 aptiche

Questa pagina fornisce note sull'implementazione per gli sviluppatori di app che desiderano estendere Windows 11 funzionalità di input penna di [Surface Slim Pen 2 per le aziende](https://www.microsoft.com/d/surface-slim-pen-2-for-business/8mjc4rmvltj0?). Le funzionalità aptiche personalizzabili includono:

- **Feedback input penna** che simula l'aspetto di penne, matite e altri strumenti di scrittura o disegno.
- **Feedback sull'interazione** che risponde direttamente alle azioni dell'utente, ad esempio il passaggio del mouse su un pulsante, la selezione di un pulsante o il completamento di un'attività con la penna.

Se stai personalizzando un'app per Surface Slim Pen 2, fai riferimento alle linee guida di Windows Ink descritte in Interazioni con la penna e [feedback aptico](/windows/apps/design/input/pen-haptics) e quindi consulta le note seguenti.

## <a name="implementation-notes"></a>Note sull'implementazione

Surface Slim Pen 2 è conforme alle linee guida Windows 11 Ink con le eccezioni seguenti:

- **Forme d'onda di interazione.** Come documentato nella sezione Invia e interrompi [feedback](/windows/apps/design/input/pen-haptics#send-and-stop-interaction-feedback) interazione", l'invio di una forma d'onda di interazione quando viene riprodotta una forma d'onda input penna interromperà temporaneamente la forma d'onda di input penna. Tuttavia, con l'implementazione corrente di Slim Pen 2, la forma d'onda di input penna potrebbe non riprendere quando la forma d'onda di interazione si interrompe. Pertanto, se necessario, la forma d'onda dell'input penna deve essere ri abilitata dopo il feedback dell'interazione. Non è necessario attendere il completamento del feedback dell'interazione.
- **Funzionalità non supportate.** Come documentato nella sezione [Personalizzazioni del feedback](/windows/apps/design/input/pen-haptics#haptic-feedback-customizations) aptico", le seguenti funzionalità facoltative non sono supportate in Surface Slim Pen 2: Play Count e Replay Pause Interval. Anche se questi utilizzi vengono visualizzati nel descrittore, non sono attualmente supportati. Di conseguenza, le funzioni seguenti restituiscono un valore non corretto: IsPlayCountSupported, IsPlayDurationSupported, IsReplayPauseIntervalSupported.

## <a name="learn-more"></a>Scopri di più

- [Interazioni e Windows Ink penna nelle Windows app](/windows/apps/design/input/pen-and-stylus-interactions)
- [Surface Slim Pen 2 for Business](https://www.microsoft.com/d/surface-slim-pen-2-for-business/8mjc4rmvltj0?)
- [Funzionalità e compatibilità della penna di Surface](https://support.microsoft.com/surface/identify-your-surface-pen-and-features-c82a0208-2e35-b347-dae0-d7f4922edc77)


---
title: Applicazione criteri ActiveSync ad account dispositivo - Surface Hub
description: L'account del dispositivo Microsoft Surface Hub usa ActiveSync per sincronizzare l'e-mail e il calendario. In questo modo gli utenti possono partecipare e avviare riunioni pianificate da Surface Hub, nonché inviare tramite e-mail tutte le lavagne create durante la riunione.
ms.assetid: FAABBA74-3088-4275-B58E-EC1070F4D110
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, criteri ActiveSync
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: b5f828ee6757c150b1287e8210c81592e970b74a
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2021
ms.locfileid: "11311962"
---
# Applicazione di criteri ActiveSync agli account del dispositivo - Surface Hub


L'account del dispositivo Microsoft Surface Hub usa ActiveSync per sincronizzare l'e-mail e il calendario. In questo modo gli utenti possono partecipare e avviare riunioni pianificate da Surface Hub, nonché inviare tramite e-mail tutte le lavagne create durante la riunione.

Per il corretto funzionamento di queste funzionalità, i criteri di ActiveSync per l'organizzazione devono essere configurati come segue:

-   Non possono esistere criteri globali che bloccano la sincronizzazione della cassetta postale delle risorse usata dall'account del dispositivo Surface Hub. Se esiste un criterio di blocco, è necessario aggiungere l'hub Surface come dispositivo consentito.
-   Devi impostare un criterio cassetta postale per dispositivi mobili con l'impostazione **PasswordEnabled** impostata su False. Le altre impostazioni del criterio cassetta postale per dispositivi mobili non sono compatibili con il dispositivo Surface Hub.

## Consentire il DeviceID

L'organizzazione potrebbe disporre di un criterio globale che impedisce la sincronizzazione degli account del dispositivo configurati nei dispositivi Surface Hub. Per configurare questa proprietà, vedi [Consentire ID di dispositivo per ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).

## Impostazione di PasswordEnabled

L'account del dispositivo deve disporre di un criterio di ActiveSync con l'attributo **PasswordEnabled** impostato su False o 0. Per configurare questa proprietà, vedi [Creare un criterio di Microsoft Exchange ActiveSync compatibile con Surface Hub](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).

 

 






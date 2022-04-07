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
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: fa393eca697897ee620732b543ebb6889aa035d1
ms.sourcegitcommit: b922aaf7287bdfb99f848aad455b2b4001b8f5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2022
ms.locfileid: "12472575"
---
# <a name="applying-activesync-policies-to-device-accounts-surface-hub"></a>Applicazione di criteri ActiveSync agli account del dispositivo - Surface Hub

Surface Hub in Windows 10 Team 1703 e versioni precedenti usavano ActiveSync per sincronizzare la posta & calendario.

I requisiti Surface Hub per i criteri ActiveSync nell'organizzazione sono i seguenti:

-   Non possono essere presenti criteri globali che bloccano la sincronizzazione della cassetta postale delle risorse usata dall'account del dispositivo del Surface Hub. Se è presente un criterio di blocco di questo tipo, è necessario aggiungere il Surface Hub come dispositivo consentito.
-   Devi impostare un criterio cassetta postale per dispositivi mobili con l'impostazione **PasswordEnabled** impostata su False. Le altre impostazioni del criterio cassetta postale per dispositivi mobili non sono compatibili con il dispositivo Surface Hub.

## <a name="allowing-the-deviceid"></a>Abilitazione dell'ID dispositivo

L'organizzazione potrebbe disporre di un criterio globale che impedisce la sincronizzazione degli account del dispositivo configurati nei dispositivi Surface Hub. Per configurare questa proprietà, vedi [Consentire ID di dispositivo per ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).

## <a name="setting-passwordenabled"></a>Impostazione di PasswordEnabled

L'account del dispositivo deve disporre di un criterio di ActiveSync con l'attributo **PasswordEnabled** impostato su False o 0. Per configurare questa proprietà, vedi [Creare un criterio di Microsoft Exchange ActiveSync compatibile con Surface Hub](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).

 

 






---
title: Gestire Microsoft Surface Hub
description: Come gestire il dispositivo Surface Hub al termine del programma di prima esecuzione.
ms.assetid: FDB6182C-1211-4A92-A930-6C106BCD5DC1
ms.reviewer: ''
manager: laurawi
keywords: gestire Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/17/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7fa715c679803da460cc1d57bd6e84fa33d30413
ms.sourcegitcommit: d9c413f1c50908a81e5489aca2c6023eab573148
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2021
ms.locfileid: "12093043"
---
# <a name="manage-microsoft-surface-hub"></a>Gestire Microsoft Surface Hub

Dopo la configurazione iniziale Microsoft Surface Hub, le impostazioni e la configurazione del dispositivo possono essere modificate o modificate in due modi:

- **Gestione locale**: tutti i dispositivi Surface Hub possono essere configurati localmente usando l'app **Impostazioni** nel dispositivo. Per impedire agli utenti non autorizzati di modificare le impostazioni, l'app Impostazioni richiede credenziali di amministratore per aprire l'app. Per altre informazioni, vedi [Gestione locale per le impostazioni di Surface Hub](local-management-surface-hub-settings.md).
- **Gestione remota:** Surface Hub consente agli amministratori IT di gestire impostazioni e criteri utilizzando un provider di gestione dei dispositivi mobili (MDM), ad esempio Microsoft Intune, Microsoft Endpoint Configuration Manager e altri provider di terze parti. Inoltre, gli amministratori possono monitorare i surface hub usando Azure Monitor.  Per altre informazioni, vedi [Gestire le impostazioni con](manage-settings-with-mdm-for-surface-hub.md)un provider MDM e Monitorare Surface Hub con Azure Monitor per tenere traccia [dell'integrità.](/azure/azure-monitor/insights/surface-hubs) 

> [!NOTE]
> Questi metodi di gestione non si escludono a vicenda. I dispositivi possono essere gestiti in locale o in remoto, in base alle tue esigenze. Tuttavia, i criteri e le impostazioni MDM sovrascriveranno le modifiche locali quando il Surface Hub viene sincronizzato con il server di gestione. 

## <a name="in-this-section"></a>Contenuto della sezione

Informazioni sulla gestione e l'aggiornamento di Surface Hub.

| Argomento | Descrizione |
| ----- | ----------- |
| [Gestione remota di Surface Hub](remote-surface-hub-management.md) |Argomenti correlati alla gestione remota del dispositivo Surface Hub. Includono l'installazione delle app, la gestione delle impostazioni con MDM e il monitoraggio tramite Operations Management Suite. |
| [Gestire le impostazioni di Surface Hub](manage-surface-hub-settings.md) |Argomenti correlati alla gestione delle impostazioni di Surface Hub: accessibilità, account del dispositivo, reimpostazione del dispositivo, nome di dominio completo, impostazioni di Windows Update e rete wireless. |
| [Installare app in Surface Hub](install-apps-on-surface-hub.md) | Gli amministratori possono installare app da Microsoft Store o da Microsoft Store per le aziende.|
[Configurare il menu Start di Surface Hub](surface-hub-start-menu.md) | Usa MDM per personalizzare il menu Start per Surface Hub.
| [Configurare e usare Microsoft Whiteboard](whiteboard-collaboration.md)  | L'aggiornamento più recente di Microsoft Whiteboard include la funzionalità che consente a due dispositivi Surface Hub di collaborare in tempo reale sulla stessa lavagna.   |
| [Terminare una riunione con Termina sessione](finishing-your-surface-hub-meeting.md) | Al termine di una riunione, gli utenti possono toccare **Termina sessione** per cancellare tutti i dati sensibili e preparare il dispositivo per la riunione successiva.|
| [Accedere a Surface Hub con Microsoft Authenticator](surface-hub-authenticator-app.md) | Puoi accedere a un dispositivo Surface Hub senza password con l'app Microsoft Authenticator, disponibile su Android e iOS.   |
| [Salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md) | Ogni dispositivo Surface Hub viene automaticamente configurato con il software di crittografia delle unità BitLocker. Microsoft consiglia vivamente di assicurarti di eseguire il backup delle chiavi di ripristino di BitLocker.|
| [Connettere altri dispositivi e vederne i contenuti con Surface Hub](connect-and-display-with-surface-hub.md) | Puoi connettere un altro dispositivo a Surface Hub per visualizzarne i contenuti.|
| [Miracast su rete wireless o LAN esistente](miracast-over-infrastructure.md) | Puoi utilizzare Miracast sulla rete wireless o LAN per connetterti a Surface Hub. |
 [Abilita autenticazione cablata 802.1x](enable-8021x-wired-authentication.md) | I criteri MDM per l'autenticazione cablata 802.1x sono stati abilitati nei dispositivi Surface Hub. 
| [Uso di un sistema di controllo della sala](use-room-control-system-with-surface-hub.md) | Puoi usare i sistemi di controllo della sala con il tuo dispositivo Microsoft Surface Hub.|
[Uso dello strumento di ripristino di Surface Hub](surface-hub-recovery-tool.md) | Usa lo Surface Hub di ripristino per riappare l'immagine Surface Hub SSD.
[Sostituzione di Surface Hub SSD](surface-hub-ssd-replacement.md) | Scopri come rimuovere e sostituire l'unità a stato solido nell'Surface Hub.

## <a name="related-topics"></a>Argomenti correlati

- [Visualizzare la modalità di presentazione di Power BI in Surface Hub e Windows 10](https://powerbi.microsoft.com/documentation/powerbi-mobile-win10-app-presentation-mode/)

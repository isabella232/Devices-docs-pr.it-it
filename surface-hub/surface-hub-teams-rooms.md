---
title: Microsoft Teams Rooms su Surface Hub
description: In questo articolo viene fornita una panoramica delle Microsoft Teams Rooms su Surface Hub.
keywords: Teams Rooms, Surface Hub, Intune, QoS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/20/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 2d8bd08c150c1665365ae21bc87fd3485b8c69a8
ms.sourcegitcommit: b5e7ea8118b848846cf1fb332ed7bf96c4583d20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2021
ms.locfileid: "11909976"
---
# <a name="microsoft-teams-rooms-on-surface-hub"></a>Microsoft Teams Rooms su Surface Hub

Teams Rooms per Surface Hub sostituirà automaticamente [l'app](hub-teams-app.md) Surface Hub Teams corrente come parte di un'implementazione globale di 4 settimane a partire dal 23 settembre. Per una demo della nuova esperienza Teams, attualmente disponibile come anteprima tramite il programma Windows Insider, vedi Introduzione Teams Rooms su [Surface Hub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/introducing-teams-rooms-on-surface-hub/ba-p/2118373).

## <a name="whats-new"></a>Novità

- Le riunioni unite dalla Surface Hub iniziale o dalla nuova pagina Agenda si uniscono a "Edge to Edge" per mettere le persone in primo piano.
- Caratteristiche familiari delle riunioni, tra cui bolle di chat, reazioni, condivisione desktop e applicazioni, dare e prendere il controllo e l'audio, supporto PowerPoint live completo, modalità insieme e raccolta di grandi dimensioni.
- Teams Rooms in Surface Hub esecuzione affiancata ad altre applicazioni o ridotta a icona.
- Gli amministratori possono configurare funzionalità come Riunione coordinata e Partecipazione di prossimità per Surface Hub. [I file XML](/microsoftteams/rooms/surface-hub-manage-config#teams-configuration-file-syntax) sono supportati e verranno migrati nel nuovo modello di impostazioni.
- Nuove opzioni QoS e requisiti di rete. Per ulteriori informazioni, vedere [Configure networking and Quality of Service for Microsoft Teams Room on Surface Hub](surface-hub-teams-rooms-networking.md).
- Modifiche alla Teams, sostituendo Skype for Business come app predefinita per la collaborazione e le riunioni. Per ulteriori informazioni, vedere [Deploy Microsoft Teams for Surface Hub](/MicrosoftTeams/teams-surface-hub).

## <a name="in-meeting-experience"></a>Nell'esperienza di riunione

Teams Rooms'esperienza Surface Hub riunioni è allineata all'esperienza familiare che gli utenti conoscono dai propri dispositivi personali con le regolazioni apportate per ottimizzare un dispositivo con schermo di grandi dimensioni. L'Teams su Surface Hub consente agli utenti di accedere a funzionalità chiave, tra cui partecipazione a una riunione con un solo tocco, Riunione e Tastiera del telefono per chiamate PSTN o peer-to-peer.

:::image type="content" source="images/teamsroomsagendascreen.png" alt-text="Teams Rooms su Surface Hub Agenda.":::

:::image type="content" source="images/teamsroomsmeeting.png" alt-text="Teams Rooms in Surface Hub riunione.":::

## <a name="manage-teams-rooms-on-surface-hub"></a>Gestire Teams Rooms in Surface Hub

 È possibile personalizzare l Teams'esperienza utente direttamente dal menu Impostazioni dopo aver immesso le credenziali amministrative, tra cui:

- Configurare [riunioni coordinate](/microsoftteams/rooms/coordinated-meetings) e partecipazione di prossimità.
- Regola le impostazioni per microfoni, fotocamere e altoparlanti predefiniti.
- Controllare la versione client e cercare gli aggiornamenti più recenti.

:::image type="content" source="images/teamsroomssetttings.png" alt-text="Teams Rooms Impostazioni.":::

Il nuovo Teams Rooms per Surface Hub client, applierà automaticamente le impostazioni esistenti configurate tramite file XML, pacchetti di provisioning o un provider MDM. Questi metodi, illustrati in [Manage Microsoft Teams configuration on Surface Hub](/microsoftteams/rooms/surface-hub-manage-config), verranno sostituiti da nuove soluzioni basate sul cloud, come descritto di seguito in Gestione semplificata di Teams in arrivo [Surface Hub](#simplified-management-of-teams-coming-to-surface-hub).

### <a name="prepare-networking-for-teams-rooms"></a>Preparare la rete per Teams Rooms

Per ottimizzare Teams Rooms fare riferimento ai requisiti e ai suggerimenti descritti in [Configure networking and Quality of Service for Microsoft Teams Room on Surface Hub](surface-hub-teams-rooms-networking.md).

### <a name="simplified-management-of-teams-coming-to-surface-hub"></a>Gestione semplificata dei Teams in Surface Hub

Quando Teams Rooms per Surface Hub pubblicamente rilasciato entro la fine dell'anno, gli amministratori possono sfruttare le soluzioni seguenti:

- **Teams Interfaccia di amministrazione.** Teams L'interfaccia di amministrazione offre una piattaforma di auto-gestione completa per monitorare e gestire l'esperienza Teams Rooms in Teams dispositivi. Teams L'interfaccia di amministrazione sarà disponibile Microsoft Teams Rooms utenti senza costi aggiuntivi.
- **Microsoft Teams Rooms servizio gestito.** Il [servizio gestito Microsoft Teams Rooms](/microsoftteams/rooms/microsoft-teams-rooms-premium) è un servizio di gestione e monitoraggio IT basato su cloud che mantiene aggiornati e monitorati proattivamente i dispositivi Microsoft Teams Rooms e le relative periferiche, supportando un ambiente ottimizzato per un'esperienza utente ottimale.

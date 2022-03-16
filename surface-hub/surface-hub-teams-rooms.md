---
title: Microsoft Teams Rooms in Surface Hub
description: In questo articolo viene fornita una panoramica delle Microsoft Teams Rooms su Surface Hub.
keywords: Teams Rooms, Surface Hub, Intune, QoS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/20/2021
ms.reviewer: dpandre
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d607a34b532420123941a77d510d19db65531c85
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448729"
---
# <a name="microsoft-teams-rooms-on-surface-hub"></a>Microsoft Teams Rooms in Surface Hub

Teams Rooms per Surface Hub sostituito automaticamente [l'app Surface Hub Teams precedente](hub-teams-app.md) al momento dell'installazione di [KB5004196, KB5004198 e KB5004199](surface-hub-update-history.md).

## <a name="whats-new"></a>Novità

- Le riunioni unite dalla Surface Hub iniziale o dalla nuova pagina Agenda si uniscono a "Edge to Edge" per mettere le persone in primo piano.
- Caratteristiche familiari delle riunioni, tra cui bolle di chat, reazioni, condivisione desktop e applicazioni, dare e prendere il controllo e l'audio, supporto PowerPoint live completo, modalità insieme e raccolta di grandi dimensioni.
- Teams Rooms in Surface Hub esecuzione affiancata ad altre applicazioni o ridotta a icona.
- Gli amministratori possono configurare funzionalità come Riunione coordinata e Partecipazione di prossimità per Surface Hub. [I file XML](/microsoftteams/rooms/surface-hub-manage-config#teams-configuration-file-syntax) sono supportati e verranno migrati nel nuovo modello di impostazioni.
- Nuove opzioni QoS e requisiti di rete. Per ulteriori informazioni, vedere [Configure networking and Quality of Service for Microsoft Teams Room on Surface Hub](surface-hub-teams-rooms-networking.md).
- Se non è già l'impostazione predefinita, Teams può essere impostata come app predefinita per riunioni e chiamate in **Impostazioni** >  **Surface Hub** >  **Calling & audio**. Per altre informazioni sulle modalità riunione e sulla loro configurazione tramite i criteri MDM, [vedi Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md#changing-default-app-for-meetings--calls).

## <a name="in-meeting-experience"></a>Nell'esperienza di riunione

Teams Rooms'esperienza Surface Hub riunioni è allineata all'esperienza familiare che gli utenti conoscono dai propri dispositivi personali con le regolazioni apportate per ottimizzare un dispositivo con schermo di grandi dimensioni. L'apertura Teams su Surface Hub consente agli utenti di accedere a funzionalità chiave, tra cui partecipazione a riunioni con un solo tocco, Riunione e Tastiera del telefono per chiamate PSTN o peer-to-peer.

:::image type="content" source="images/teamsroomsagendascreen.png" alt-text="Teams Rooms su Surface Hub Agenda.":::

:::image type="content" source="images/teamsroomsmeeting.png" alt-text="Teams Rooms in Surface Hub riunione.":::

## <a name="manage-teams-rooms-on-surface-hub"></a>Gestire Teams Rooms in Surface Hub

 È possibile personalizzare l Teams'esperienza utente direttamente dal menu Impostazioni dopo aver immesso le credenziali amministrative, tra cui:

- Configurare [riunioni coordinate](/microsoftteams/rooms/coordinated-meetings) e partecipazione di prossimità.
- Regola le impostazioni per microfoni, fotocamere e altoparlanti predefiniti.
- Controllare la versione client e cercare gli aggiornamenti più recenti.

:::image type="content" source="images/teamsroomssetttings.png" alt-text="Teams Rooms Impostazioni.":::

Il nuovo Teams Rooms per Surface Hub client, applierà automaticamente le impostazioni esistenti configurate tramite file XML, pacchetti di provisioning o un provider MDM. Questi metodi, descritti in [Manage Microsoft Teams configuration on Surface Hub](/microsoftteams/rooms/surface-hub-manage-config), saranno sostituiti da nuove soluzioni basate sul cloud, come descritto di seguito in [Gestione](#simplified-management-of-teams-coming-to-surface-hub) semplificata di Teams in arrivo Surface Hub.

### <a name="prepare-networking-for-teams-rooms"></a>Preparare la rete per Teams Rooms

Per ottimizzare Teams Rooms fare riferimento ai requisiti e ai suggerimenti descritti in [Configure networking and Quality of Service for Microsoft Teams Room on Surface Hub](surface-hub-teams-rooms-networking.md).

### <a name="simplified-management-of-teams-coming-to-surface-hub"></a>Gestione semplificata dei Teams in Surface Hub

Quando Teams Rooms per Surface Hub pubblicamente rilasciato entro la fine dell'anno, gli amministratori possono sfruttare le soluzioni seguenti:

- **Teams'interfaccia di amministrazione.** Teams Admin Center offre una piattaforma di auto-gestione completa per monitorare e gestire l'esperienza Teams Rooms nei Teams dispositivi. Teams'interfaccia di amministrazione sarà disponibile per Microsoft Teams Rooms utenti senza costi aggiuntivi.
- **Microsoft Teams Rooms servizio gestito.** Il [servizio gestito Microsoft Teams Rooms](/microsoftteams/rooms/microsoft-teams-rooms-premium) è un servizio di gestione e monitoraggio IT basato su cloud che mantiene aggiornati e monitorati proattivamente i dispositivi Microsoft Teams Rooms e le relative periferiche, supportando un ambiente ottimizzato per un'esperienza utente ottimale.


## <a name="support-for-teams-rooms-in-government-community-cloud-high-gcc-h"></a>Supporto per Teams Rooms in Government Community Cloud High (GCC-H)

È necessario un aggiornamento manuale una sola volta del client Teams Rooms alla versione 1.4.00.25354 per potersi connettere a un tenant GCC-H e mantenersi aggiornato automaticamente:

 - Verificare che nell'hub sia installato l'aggiornamento cumulativo KB5005611 o Windows versione successiva
 - Utilizzare [Teams_Uninstall_win32.ppkg](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Teams_Uninstall_Win32.ppkg) per rimuovere le Teams Rooms correnti Surface Hub versione
 - Riavviare il dispositivo
 - Installare [Teams_win32.ppkg](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/Teams_Win32.ppkg) per installare la versione 1.4.00.25354
 - Riavviare di nuovo il dispositivo

Passaggi dettagliati:

1. Salva entrambi i pacchetti di provisioning nella radice dell'unità USB.
2.  Inserisci l'unità USB nel Surface Hub.
3.  Nel Surface Hub, apri il menu Start, seleziona Tutte le app e quindi seleziona Impostazioni.
4.  Fornisci le credenziali di amministratore hub quando richiesto.
5.  Vai a **Surface Hub** >  **Gestione dei dispositiviAggiungi** >  **o rimuovi un pacchetto di provisioning** e quindi seleziona **Aggiungi un pacchetto**.
6.  In **Seleziona un pacchetto** seleziona il pacchetto di provisioning Teams_Uninstall_win32.ppkg e quindi riavvia il Surface Hub.
7.  Nel Surface Hub, apri il menu Start, seleziona Tutte le app e quindi seleziona Impostazioni.
8.  Fornisci le credenziali di amministratore hub quando richiesto.
9.  Vai a **Surface Hub** >  **Gestione dei dispositiviAggiungi** >  **o rimuovi un pacchetto di provisioning** e quindi seleziona **Aggiungi un pacchetto**.
10. In **Seleziona un pacchetto** seleziona il pacchetto di provisioning Teams_win32.ppkg e quindi riavvia il Surface Hub.

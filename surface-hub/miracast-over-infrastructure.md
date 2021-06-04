---
title: Miracast su rete wireless o LAN esistente
description: Windows 10 ti consente di inviare un flusso di Miracast tramite una rete locale.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/24/2020
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d63b3de0f76cb70fe86fff246d82cbe166278461
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10836973"
---
# Miracast su infrastruttura

In Windows 10, versione 1703 Microsoft ha esteso la possibilità di inviare un flusso di Miracast tramite una rete locale, anziché tramite un link diretto wireless. Questa funzionalità si basa sul [protocollo di attivazione della connessione Miracast su infrastruttura (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx).

Miracast su infrastruttura offre numerosi vantaggi:

- Windows rileva automaticamente quando l'invio del flusso video su questo percorso è applicabile.
- Windows sceglierà questo percorso solo se la connessione è tramite Ethernet o una rete Wi-Fi protetta.
- Gli utenti non devono cambiare il modo in cui si connettono a un ricevitore Miracast. Usano la stessa esperienza utente che utilizzano per le connessioni Miracast standard.
- Non è necessaria alcuna modifica ai driver wireless correnti o all'hardware del PC.
- Funziona bene con hardware wireless precedente che non è ottimizzato per Miracast tramite Wi-Fi Direct.
- Si avvale di una connessione esistente che riduce il tempo per la connessione e fornisce un flusso molto stabile.


##  <a name="how-it-works"></a>Come funziona

Gli utenti tenteranno di connettersi a un ricevitore Miracast tramite la loro scheda Wi-Fi, come in precedenza. Quando l'elenco di ricevitori Miracast è popolato, Windows 10 indicherà che il destinatario è in grado di supportare una connessione tramite l'infrastruttura. Quando l'utente seleziona un ricevitore Miracast, Windows 10 tenterà di risolvere il nome host del dispositivo tramite DNS standard, nonché tramite DNS multicast (mDNS). Se il nome non è risolvibile tramite uno dei metodi DNS, Windows 10 tornerà a stabilire la sessione Miracast con la connessione Wi-Fi Direct standard.

> [!NOTE]
> Per altre informazioni sulla sequenza di negoziazione della connessione, Vedi [Miracast over Protocol establishment Connection Infrastructure (MS-MICE)](https://msdn.microsoft.com/library/mt796768.aspx)




##  <a name="enabling-miracast-over-infrastructure-"></a>Abilitazione di Miracast su infrastruttura 

Se hai un dispositivo Surface Hub o un altro dispositivo Windows 10 che è stato aggiornato a Windows 10, versione 1703, automaticamente disponi di questa nuova funzionalità. Per sfruttare i vantaggi nell'ambiente in uso, devi assicurarti che quanto segue è appropriato all'interno della tua distribuzione:

- Nel dispositivo Surface Hub o nel dispositivo (PC o telefono Windows) deve essere in esecuzione Windows 10, versione 1703.
- Aprire la porta TCP: **7250**.
- Un dispositivo Surface Hub o un PC Windows può fungere da *ricevitore* Miracast su infrastruttura. Un dispositivo PC o un telefono Windows può fungere da *origine* Miracast su infrastruttura.
    - Come ricevitore Miracast, il dispositivo Surface Hub o il dispositivo deve essere connesso alla rete aziendale tramite Ethernet o una connessione Wi-Fi protetta (ad esempio utilizzando la protezione WPA2-PSK o WPA2-Enterprise). Se l'hub o il dispositivo Surface è connesso a una connessione Wi-Fi aperta, Miracast l'infrastruttura verrà disabilitata.
    - Come origine Miracast, il PC o il telefono Windows deve essere connesso alla stessa rete aziendale tramite Ethernet o una connessione Wi-Fi protetta.
- L'hostname DNS (nome dispositivo) dell'hub o del dispositivo Surface deve essere risolvibile tramite i server DNS. Puoi ottenere questo consentendo al dispositivo Surface Hub di registrarsi automaticamente tramite DNS dinamico o creando manualmente un record A o AAAA per il nome host di Surface Hub. 
- I PC Windows 10 devono essere connessi alla stessa rete aziendale tramite Ethernet o una connessione Wi-Fi protetta. 
-   Nei PC con Windows 10, la funzionalità **di projecting to this PC** deve essere abilitata nelle impostazioni di sistema e il dispositivo deve avere un'interfaccia Wi-Fi abilitata per rispondere alle richieste di individuazione che si verificano solo tramite la scheda Wi-Fi.


È importante notare che Miracast su infrastruttura non è una sostituzione per Miracast standard. Al contrario, la funzionalità è complementare e offre un vantaggio per gli utenti che fanno parte della rete aziendale. Gli utenti che sono ospiti di una posizione particolare e non hanno accesso alla rete aziendale continueranno a connettersi usando il metodo di connessione Wi-Fi Direct.

L'impostazione **InBoxApps/WirelessProjection/PinRequired** nel [provider di servizi di configurazione SurfaceHub (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) non è necessario per Miracast su infrastruttura. Questo avviene perché Miracast su infrastruttura funziona solo quando entrambi i dispositivi sono connessi alla stessa rete aziendale. In questo modo viene rimossa la restrizione di sicurezza che in precedenza mancava da Miracast. Ti consigliamo di continuare con questa impostazione, se la utilizzavi già in precedenza, poiché Miracast eseguirà il fallback a un Miracast regolare se la connessione all'infrastruttura non funzionerà. 

##  <a name="faq"></a>Domande frequenti
**Perché è ancora necessario Wi-Fi per usare Miracast sull'infrastruttura?**<br>
Le richieste di individuazione per identificare i destinatari di Miracast possono avvenire solo tramite la scheda Wi-Fi. Una volta identificati i destinatari, Windows 10 può quindi tentare la connessione alla rete.

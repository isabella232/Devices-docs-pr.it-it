---
title: Gestione delle password (Surface Hub)
description: Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo.
ms.assetid: 0FBFB546-05F0-430E-905E-87111046E4B8
ms.reviewer: ''
manager: laurawi
keywords: password, gestione delle password, rotazione delle password, account del dispositivo
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 215736527121306c712932f57a5a3a853fb3bb20
ms.sourcegitcommit: 366eedceb9f859f5e87ba032b161f248360cb895
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/23/2021
ms.locfileid: "11445582"
---
# <a name="password-management-surface-hub"></a>Gestione delle password (Surface Hub)

Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo. Per motivi di sicurezza, potrebbe essere utile modificare la password o impostarne la "rotazione" con regolarità. Tuttavia, se la password dell'account del dispositivo cambia, la password precedentemente archiviata nel dispositivo Surface Hub non sarà più valida e tutte le funzionalità che dipendono dall'account del dispositivo verranno disabilitate. Sarà necessario aggiornare la password dell'account del dispositivo in Surface Hub dall'app Impostazioni per riabilitare queste funzionalità.

Per semplificare la gestione delle password per gli account del dispositivo Surface Hub, sono disponibili due opzioni:

1.  Disattivare la scadenza delle password per l'account del dispositivo.
2.  Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo.


## <a name="turn-off-password-rotation-for-the-device-account"></a>Disattivare la rotazione delle password per l'account del dispositivo

Imposta la proprietà **PasswordNeverExpires** dell'account del dispositivo su True. Devi verificare se l'impostazione soddisfa i requisiti di sicurezza della tua organizzazione.


## <a name="allow-the-surface-hub-to-automatically-rotate-the-device-accounts-password"></a>Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo

Surface Hub può modificare automaticamente la password di un account del dispositivo senza richiedere l'aggiornamento manuale. Puoi abilitare questa funzionalità in **Impostazioni Account**  >  **Surface**  >  **Hub.** Se accerti Rotazione password, Surface Hub tenterà di cambiare la password ogni 7 giorni durante le ore di manutenzione. Le password non cambiano durante una riunione. Se sono trascorsi 7 giorni dall'ultima rotazione della password, ma Surface Hub era spento, tenterà di cambiare la password immediatamente quando è attivata o ogni 10 minuti fino a quando non avrà esito positivo.

Le password generate automaticamente contengono da 15 a 32 caratteri, tra cui una combinazione di lettere maiuscole e minuscole, numeri e caratteri speciali. Tieni presente che quando la password dell'account del dispositivo viene modificata, non ti verrà visualizzata la nuova password. Se devi accedere all'account o fornire di nuovo la password (ad esempio, se vuoi modificare le impostazioni dell'account del dispositivo nel Dispositivo Surface Hub), dovrai usare Active Directory o il portale di amministrazione di Microsoft 365 per reimpostare la password.

> [!IMPORTANT]
> Il formato usato per aggiungere l'account del dispositivo a Surface Hub ha un impatto sull'opzione di [affiliazione](prepare-your-environment-for-surface-hub.md) del dispositivo da usare per il corretto funzionamento della rotazione delle password. Se si aggiunge l'account nel formato **dominio\nomeutente,** consociare l'hub ad Active Directory locale durante la configurazione iniziale. Se si aggiunge l'account in `username@domain.com` formato, consociare l'hub ad Azure Active Directory durante la configurazione iniziale. In caso contrario, la rotazione delle password non funzionerà.

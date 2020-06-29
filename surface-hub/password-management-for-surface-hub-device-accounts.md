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
ms.openlocfilehash: bef626fce875d5074f3ed47ed957e821beec7c77
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834028"
---
# Gestione delle password (Surface Hub)

Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo. Per motivi di sicurezza, potrebbe essere utile modificare la password o impostarne la "rotazione" con regolarità. Tuttavia, se la password dell'account del dispositivo cambia, la password precedentemente archiviata nel dispositivo Surface Hub non sarà più valida e tutte le funzionalità che dipendono dall'account del dispositivo verranno disabilitate. Sarà necessario aggiornare la password dell'account del dispositivo in Surface Hub dall'app Impostazioni per riabilitare queste funzionalità.

Per semplificare la gestione delle password per gli account del dispositivo Surface Hub, sono disponibili due opzioni:

1.  Disattivare la scadenza delle password per l'account del dispositivo.
2.  Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo.


## Disattivare la rotazione delle password per l'account del dispositivo

Imposta la proprietà **PasswordNeverExpires** dell'account del dispositivo su True. Devi verificare se l'impostazione soddisfa i requisiti di sicurezza della tua organizzazione.


## Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo

Il dispositivo Surface Hub può gestire una password dell'account del dispositivo cambiandola frequentemente senza richiedere l'aggiornamento manuale delle informazioni dell'account del dispositivo. Puoi abilitare questa funzionalità in **Impostazioni**. Una volta abilitata, la password dell'account del dispositivo cambierà ogni settimana durante l'orario di manutenzione.

Importante: quando la password dell'account del dispositivo viene modificata, la nuova password non verrà più visualizzata. Se hai bisogno di accedere all'account o per specificare nuovamente la password (ad esempio, se vuoi modificare le impostazioni dell'account del dispositivo in Surface Hub), devi reimpostare la password con Active Directory o tramite il portale di amministrazione di Office 365.

> [!IMPORTANT]
> Se l'organizzazione usa una topologia ibrida (con alcuni servizi ospitati in locale e alcuni ospitati online tramite Office 365), dovrai configurare l'account del dispositivo nel formato **dominio\nomeutente**. In caso contrario, la rotazione delle password non funzionerà.

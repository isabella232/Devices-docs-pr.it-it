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
ms.openlocfilehash: ab2726577201157ed9a7ff4d265e826c063cf477
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676610"
---
# <a name="password-management-surface-hub"></a>Gestione delle password (Surface Hub)

Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo. Per motivi di sicurezza, potrebbe essere utile modificare la password o impostarne la "rotazione" con regolarità. Tuttavia, se la password dell'account del dispositivo cambia, la password precedentemente archiviata nel dispositivo Surface Hub non sarà più valida e tutte le funzionalità che dipendono dall'account del dispositivo verranno disabilitate. Sarà necessario aggiornare la password dell'account del dispositivo in Surface Hub dall'app Impostazioni per riabilitare queste funzionalità.

Per semplificare la gestione delle password per gli account del dispositivo Surface Hub, sono disponibili due opzioni:

1.  Disattivare la scadenza delle password per l'account del dispositivo.
2.  Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo.


## <a name="turn-off-password-rotation-for-the-device-account"></a>Disattivare la rotazione delle password per l'account del dispositivo

Imposta la proprietà **PasswordNeverExpires** dell'account del dispositivo su True. Devi verificare se l'impostazione soddisfa i requisiti di sicurezza della tua organizzazione.


## <a name="allow-the-surface-hub-to-automatically-rotate-the-device-accounts-password"></a>Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo

Il Surface Hub può modificare automaticamente la password di un account del dispositivo senza richiedere l'aggiornamento manuale. È possibile abilitare questa funzionalità in **Impostazioni**  >  **Surface Hub**  >  **account**. Se si attiva Rotazione password, il Surface Hub tenterà di modificare la password ogni 7 giorni durante le ore di manutenzione. Le password non cambiano durante una riunione. Se sono trascorsi 7 giorni dall'ultima rotazione della password, ma il Surface Hub era disattivato, tenterà di cambiare la password immediatamente quando viene attivata o ogni 10 minuti fino a quando non avrà esito positivo.

Le password generate automaticamente contengono da 15 a 32 caratteri, tra cui una combinazione di lettere maiuscole e minuscole, numeri e caratteri speciali. Tieni presente che quando la password dell'account del dispositivo viene modificata, non ti verrà visualizzata la nuova password. Se devi accedere all'account o fornire di nuovo la password (ad esempio, se vuoi modificare le impostazioni dell'account del dispositivo nel Surface Hub), dovrai usare Active Directory o il portale di amministrazione di Microsoft 365 per reimpostare la password.

> [!IMPORTANT]
> [L'opzione di affiliazione](prepare-your-environment-for-surface-hub.md) del dispositivo selezionata durante la configurazione iniziale del Surface Hub influisce sul formato dell'account del dispositivo che può essere usato con la rotazione delle password. Gli hub affiliati a un Active Directory locale possono ruotare solo le password degli account del dispositivo immessi nel **formato dominio\nomeutente.** Gli hub affiliati a un Azure Active Directory possono ruotare solo le password degli account del dispositivo immessi nel formato, ma solo se l'account è solo cloud o se il dominio AAD è configurato per l'autenticazione cloud e il writeback delle `username@domain.com` [password.](/azure/active-directory/authentication/concept-sspr-writeback) [](/azure/active-directory/hybrid/choose-ad-authn#cloud-authentication)

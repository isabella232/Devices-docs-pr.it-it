---
title: Problemi noti e altre informazioni su Microsoft Surface Hub
description: Delinea i problemi noti di Microsoft Surface Hub.
ms.assetid: aee90a0c-fb05-466e-a2b1-92de89d0f2b7
keywords: Surface, Hub, issues
ms.prod: surface-hub
ms.sitesec: library
author: todmccoy
ms.author: v-todmc
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: ec6746098203b5e91e2aaf3b044d21b81c31c897
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833092"
---
# Problemi noti e altre informazioni su Microsoft Surface Hub

Stiamo ascoltando. La qualità è una priorità assoluta e desideriamo tenerti informati sui problemi che impattano i clienti. Di seguito sono riportati alcuni problemi noti di Microsoft Surface Hub:

- **Skype for business non usa proxy per il traffico multimediale con RS2**
<br/>Per alcuni utenti di Surface Hub che si trovano dietro un proxy, Skype for business non userà il server proxy per elementi multimediali. Tuttavia, l'hub Surface sarà in grado di accedere all'account. Quando si usa proxy, viene visualizzato il proprio feedback e si conosce il problema del traffico multimediale. Stiamo esaminando attivamente il problema e rilasceremo le correzioni non appena verrà identificata e testata una soluzione. 

- **Per i dispositivi segnalati da AAD, quando un utente tenta di accedere a "i miei incontri & file", Surface Hub riporta che non esiste una connessione Internet**
<br/>Siamo a conoscenza di un set di problemi che interessano l'accesso e il Document Access in Surface Hub. Stiamo esaminando attivamente questi problemi. Come soluzione alternativa fino a quando non viene rilasciata una risoluzione, i clienti possono reimpostare i loro dispositivi e configurare l'hub per l'uso di un account di amministratore locale. Dopo la riconfigurazione per usare l'account di amministratore locale, "le mie riunioni e i miei file" funzioneranno come previsto.
- **Accesso singolo quando è stato aggiunto Azure AD**
<br/>Surface Hub è stato progettato per gli spazi comuni, che hanno un impatto sul modo in cui vengono archiviate le credenziali utente. A causa di questo, esistono attualmente limitazioni nel funzionamento di Single Sign-in quando i dispositivi sono collegati AD Azure AD. Microsoft è a conoscenza di questa limitazione e sta esaminando attivamente le opzioni per una risoluzione.
- **Miracast sopra la proiezione dell'infrastruttura su Surface Hub non riesce se l'hub Surface ha un carattere punto (.) nel nome descrittivo**
<br/>Gli utenti di Surface Hub potrebbero riscontrare problemi di proiezione nel dispositivo se il nome descrittivo include un punto o un puntino nel nome (.), ad esempio "conf. Room42". Per risolvere il problema, cambiare il nome descrittivo dell'Hub nell' **Settings**  >  **Hub Surface**delle impostazioni  >  **About**e quindi riavviare il dispositivo. Microsoft sta lavorando a una soluzione per questo problema.
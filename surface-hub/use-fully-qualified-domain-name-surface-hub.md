---
title: Usare il nome di dominio completo con Surface Hub
description: Risolvi i problemi comuni, inclusi quelli di configurazione, e gli errori di Exchange ActiveSync.
keywords:
- Risolvere i problemi comuni
- problemi di configurazione
- Errori di Exchange ActiveSync
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.prod: surface-hub
ms.sitesec: library
ms.openlocfilehash: c9617ec9c77d0f0c0333a156448ca24c18aec1db
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911761"
---
# <a name="configure-domain-name-for-skype-for-business"></a>Configurare il nome di dominio per Skype for Business

Esistono alcuni scenari in cui è necessario specificare il nome di dominio di Skype for Business Server:
- **Più suffissi DNS** - Quando l'infrastruttura di Skype for Business ha spazi dei nomi disgiunti e quindi uno o più server hanno un suffisso DNS che non corrisponde al suffisso dell'indirizzo di accesso per Skype for Business.  
- **I suffissi di Skype for Business ed Exchange sono diversi** - Quando il suffisso dell'indirizzo di accesso per Skype for Business è diverso dal suffisso dell'indirizzo di Exchange usato per l'account di dispositivo.
- **Utilizzo dei certificati** : le organizzazioni di grandi dimensioni con server Skype for Business locali utilizzano in genere certificati con la propria autorità di certificazione radice. In genere il dominio dell'autorità di certificazione è diverso da quello di Skype for Business Server e per questo il certificato non viene considerato attendibile e l'accesso non riesce.  Skype deve conoscere il nome di dominio del certificato per configurare una relazione di trust. In genere le aziende usano Criteri di gruppo per la versione desktop di Skype, ma l'uso di Criteri di gruppo non è supportato in Surface Hub.

**Per configurare il nome di dominio per Skype for Business Server**</br>
1. Nel dispositivo Surface Hub apri **Impostazioni**.
2. Fai clic su **Surface Hub**, quindi su **Audio e chiamate**. 
3. In **Configurazione di Skype for Business** fai clic su **Configura nome di dominio**. 
4. Digita il nome di dominio per Skype for Business Server e quindi fai clic su **OK**. 
   > [!TIP]
   > Puoi digitare più nomi di dominio, separandoli con una virgola. <br> Ad esempio: lync.com, outlook.com, lync.glbdns.microsoft.com

    ![Aggiungere Skype for Business FQDN a Impostazioni.](images/system-settings-add-fqdn.png)

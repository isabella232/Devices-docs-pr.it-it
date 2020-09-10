---
title: Autenticazione moderna di Surface Hub
description: Questa pagina descrive l'uso dell'autenticazione moderna su Surface Hub in contrasto con l'autenticazione di base legacy.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 14be433923ca564123952c2d1d7b1c158e725af3
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004468"
---
# Autenticazione moderna di Surface Hub

Il supporto per l'autenticazione moderna degli account basati sul cloud è completamente integrato nel prossimo aggiornamento di Windows 10 team 2020, con le build di anteprima disponibili nel [programma Windows Insider](https://insider.windows.com/). Dopo aver [installato la build di anteprima](surface-hub-install-2020preview.md), è possibile eseguire la migrazione dall'autenticazione di base legacy e usare i miglioramenti di sicurezza più recenti di Microsoft Azure ed Exchange Online. Con l'aggiornamento di 2020, Surface Hub supporta i protocolli di Exchange Web Services (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) che Abilita Exchange Online per la sincronizzazione dell'account del dispositivo.

Per i nuovi account basati sul cloud, Surface Hub USA automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriore configurazione oltre a creare semplicemente account di dispositivo usando il formato [alias@contoso.com](mailto:alias@contoso.com). Non usare il formato legacy-Contoso\alias, che non è supportato per l'autenticazione moderna. Per altre informazioni, Vedi [creare l'account del dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).

> [!NOTE]
> Surface Hub non supporta l'autenticazione moderna per gli account locali. Gli account devono essere creati nel cloud.


---
title: Autenticazione moderna su Surface Hub
description: Questa pagina descrive l'uso dell'autenticazione moderna su Surface Hub in contrasto con l'autenticazione di base legacy.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/21/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 387d799e15ae25bb1043e9ee3417aa3c31676825
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893153"
---
# Autenticazione moderna su Surface Hub

Il supporto per l'autenticazione moderna degli account basati sul cloud è completamente integrato nell'aggiornamento di Windows 10 team 2020, che consente di eseguire la migrazione dall'autenticazione di base legacy e di usare i miglioramenti più recenti di sicurezza di Microsoft Azure ed Exchange Online. Con l'aggiornamento di 2020, Surface Hub supporta i protocolli di Exchange Web Services (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) che Abilita Exchange Online per la sincronizzazione dell'account del dispositivo.

Per i nuovi account basati sul cloud, Surface Hub USA automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriore configurazione oltre a creare semplicemente account di dispositivo usando il formato [alias@contoso.com](mailto:alias@contoso.com). Non usare il formato legacy-Contoso\alias, che non è supportato per l'autenticazione moderna. Per altre informazioni, Vedi [creare l'account del dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).

> [!NOTE]
> Surface Hub non supporta l'autenticazione moderna per gli account locali. Gli account devono essere creati nel cloud.


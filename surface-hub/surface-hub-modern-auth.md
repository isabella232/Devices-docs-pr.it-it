---
title: Autenticazione moderna di Surface Hub
description: Questa pagina descrive l'uso dell'autenticazione moderna in Surface Hub in contrasto con l'autenticazione di base legacy.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/10/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: 1674b7abd74a666e2ab1040f66d9ea548ab3c201
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385164"
---
# <a name="modern-authentication-on-surface-hub"></a>Autenticazione moderna di Surface Hub

Windows 10 Team 2020 Update aggiunge il supporto per l'autenticazione moderna dell'account del dispositivo Hub in alcuni scenari. Dopo aver installato l'aggiornamento 2020, è possibile eseguire la migrazione dall'autenticazione di base legacy per utilizzare gli ultimi miglioramenti della sicurezza se l'account del dispositivo viene autenticato tramite Azure Active Directory e la cassetta postale dell'account è ospitata in Exchange Online. Con l'aggiornamento 2020, Surface Hub supporta i protocolli di Servizi Web Exchange (EWS) e l'autenticazione basata su Active Directory Authentication Library (ADAL) durante la sincronizzazione dell'account del dispositivo con Exchange Online.

Per i nuovi account basati sul cloud, Surface Hub usa automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriori configurazioni oltre alla semplice creazione di account [del dispositivo usando](mailto:alias@contoso.com)il formato alias@contoso.com . Non utilizzare il formato legacy: Contoso\alias, che non è supportato per l'autenticazione moderna. Per altre informazioni, vedi Creare un account del dispositivo [Surface Hub 2S.](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)

> [!NOTE]
> Surface Hub non supporta l'autenticazione moderna per gli account locali. Gli account devono essere creati nel cloud.


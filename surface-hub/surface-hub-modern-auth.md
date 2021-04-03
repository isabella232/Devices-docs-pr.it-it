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
ms.openlocfilehash: 3873d0ac7ffff3fa790f44b474d937772e5a0900
ms.sourcegitcommit: 4ec96ff1cd563d055fa0689a63f136acf2794a2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "11474763"
---
# <a name="modern-authentication-on-surface-hub"></a>Autenticazione moderna di Surface Hub

Windows 10 Team 2020 Update aggiunge il supporto per l'autenticazione moderna dell'account del dispositivo Hub in alcuni scenari. Dopo aver installato l'aggiornamento 2020, è possibile eseguire la migrazione dall'autenticazione di base legacy per utilizzare i miglioramenti di sicurezza più recenti se l'account del dispositivo esegue l'autenticazione tramite Azure Active Directory e la cassetta postale dell'account è ospitata in Exchange Online. Con l'aggiornamento 2020, Surface Hub supporta i protocolli di Servizi Web Exchange (EWS) e l'autenticazione basata su Active Directory Authentication Library (ADAL) durante la sincronizzazione dell'account del dispositivo con Exchange Online.

Per i nuovi account basati su cloud, Surface Hub usa automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere una configurazione aggiuntiva oltre ad aggiungere semplicemente l'account del dispositivo a Surface Hub usando il formato [alias@contoso.com](mailto:alias@contoso.com). Non utilizzare il formato legacy : Contoso\alias, che non è supportato per l'autenticazione moderna. Per altre informazioni, vedi [Creare e testare un account del dispositivo.](create-and-test-a-device-account-surface-hub.md)

> [!NOTE]
> L'autenticazione moderna non è supportata per gli account Surface Hub locali. Gli account devono usare solo Azure AD per l'autenticazione.

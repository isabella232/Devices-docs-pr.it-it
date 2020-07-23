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
# <span data-ttu-id="5340b-104">Autenticazione moderna su Surface Hub</span><span class="sxs-lookup"><span data-stu-id="5340b-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="5340b-105">Il supporto per l'autenticazione moderna degli account basati sul cloud è completamente integrato nell'aggiornamento di Windows 10 team 2020, che consente di eseguire la migrazione dall'autenticazione di base legacy e di usare i miglioramenti più recenti di sicurezza di Microsoft Azure ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="5340b-105">Support for modern authentication of cloud-based accounts is fully integrated in Windows 10 Team 2020 Update, allowing you to migrate from legacy basic authentication and utilize the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="5340b-106">Con l'aggiornamento di 2020, Surface Hub supporta i protocolli di Exchange Web Services (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) che Abilita Exchange Online per la sincronizzazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5340b-106">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="5340b-107">Per i nuovi account basati sul cloud, Surface Hub USA automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriore configurazione oltre a creare semplicemente account di dispositivo usando il formato [alias@contoso.com](mailto:alias@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="5340b-107">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="5340b-108">Non usare il formato legacy-Contoso\alias, che non è supportato per l'autenticazione moderna.</span><span class="sxs-lookup"><span data-stu-id="5340b-108">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="5340b-109">Per altre informazioni, Vedi [creare l'account del dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span><span class="sxs-lookup"><span data-stu-id="5340b-109">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="5340b-110">Surface Hub non supporta l'autenticazione moderna per gli account locali.</span><span class="sxs-lookup"><span data-stu-id="5340b-110">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="5340b-111">Gli account devono essere creati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="5340b-111">The accounts must be created in the cloud.</span></span>


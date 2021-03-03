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
# <a name="modern-authentication-on-surface-hub"></a><span data-ttu-id="c87d7-104">Autenticazione moderna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="c87d7-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="c87d7-105">Windows 10 Team 2020 Update aggiunge il supporto per l'autenticazione moderna dell'account del dispositivo Hub in alcuni scenari.</span><span class="sxs-lookup"><span data-stu-id="c87d7-105">The Windows 10 Team 2020 Update adds support for modern authentication of the Hub device account in some scenarios.</span></span> <span data-ttu-id="c87d7-106">Dopo aver installato l'aggiornamento 2020, è possibile eseguire la migrazione dall'autenticazione di base legacy per utilizzare gli ultimi miglioramenti della sicurezza se l'account del dispositivo viene autenticato tramite Azure Active Directory e la cassetta postale dell'account è ospitata in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c87d7-106">Once you install the 2020 update, you can migrate from legacy basic authentication to make use of the latest security improvements if the device account authenticates via Azure Active Directory and the account's mailbox is hosted in Exchange Online.</span></span> <span data-ttu-id="c87d7-107">Con l'aggiornamento 2020, Surface Hub supporta i protocolli di Servizi Web Exchange (EWS) e l'autenticazione basata su Active Directory Authentication Library (ADAL) durante la sincronizzazione dell'account del dispositivo con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="c87d7-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication when syncing the device account with Exchange Online.</span></span>

<span data-ttu-id="c87d7-108">Per i nuovi account basati sul cloud, Surface Hub usa automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriori configurazioni oltre alla semplice creazione di account [del dispositivo usando](mailto:alias@contoso.com)il formato alias@contoso.com .</span><span class="sxs-lookup"><span data-stu-id="c87d7-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="c87d7-109">Non utilizzare il formato legacy: Contoso\alias, che non è supportato per l'autenticazione moderna.</span><span class="sxs-lookup"><span data-stu-id="c87d7-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="c87d7-110">Per altre informazioni, vedi Creare un account del dispositivo [Surface Hub 2S.](https://docs.microsoft.com/surface-hub/surface-hub-2s-account)</span><span class="sxs-lookup"><span data-stu-id="c87d7-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="c87d7-111">Surface Hub non supporta l'autenticazione moderna per gli account locali.</span><span class="sxs-lookup"><span data-stu-id="c87d7-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="c87d7-112">Gli account devono essere creati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="c87d7-112">The accounts must be created in the cloud.</span></span>


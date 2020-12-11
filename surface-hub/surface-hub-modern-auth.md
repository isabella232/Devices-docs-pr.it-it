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
ms.date: 12/10/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: dd0b0ad257abbc52c443b075e62db00dcf5713ea
ms.sourcegitcommit: 4b1cfcac090910a3ea634929942063eb51fc54f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/11/2020
ms.locfileid: "11206280"
---
# <span data-ttu-id="17203-104">Autenticazione moderna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="17203-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="17203-105">Il supporto per l'autenticazione moderna degli account basati sul cloud è completamente integrato nell' [aggiornamento di Windows 10 Team 2020](surface-hub-2020-update.md).</span><span class="sxs-lookup"><span data-stu-id="17203-105">Support for modern authentication of cloud-based accounts is fully integrated in [Windows 10 Team 2020 Update](surface-hub-2020-update.md).</span></span> <span data-ttu-id="17203-106">Dopo aver installato l'aggiornamento di 2020, è possibile eseguire la migrazione dall'autenticazione di base legacy e usare i miglioramenti di sicurezza più recenti di Microsoft Azure ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="17203-106">Once you install the 2020 update, you can migrate from legacy basic authentication and use the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="17203-107">Con l'aggiornamento di 2020, Surface Hub supporta i protocolli di Exchange Web Services (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) che Abilita Exchange Online per la sincronizzazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="17203-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="17203-108">Per i nuovi account basati sul cloud, Surface Hub USA automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriore configurazione oltre a creare semplicemente account di dispositivo usando il formato [alias@contoso.com](mailto:alias@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="17203-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="17203-109">Non usare il formato legacy-Contoso\alias, che non è supportato per l'autenticazione moderna.</span><span class="sxs-lookup"><span data-stu-id="17203-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="17203-110">Per altre informazioni, Vedi [creare l'account del dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span><span class="sxs-lookup"><span data-stu-id="17203-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="17203-111">Surface Hub non supporta l'autenticazione moderna per gli account locali.</span><span class="sxs-lookup"><span data-stu-id="17203-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="17203-112">Gli account devono essere creati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="17203-112">The accounts must be created in the cloud.</span></span>


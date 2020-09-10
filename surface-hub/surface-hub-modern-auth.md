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
# <span data-ttu-id="69739-104">Autenticazione moderna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="69739-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="69739-105">Il supporto per l'autenticazione moderna degli account basati sul cloud è completamente integrato nel prossimo aggiornamento di Windows 10 team 2020, con le build di anteprima disponibili nel [programma Windows Insider](https://insider.windows.com/).</span><span class="sxs-lookup"><span data-stu-id="69739-105">Support for modern authentication of cloud-based accounts is fully integrated in the upcoming Windows 10 Team 2020 Update, with preview builds available from the [Windows Insider Program](https://insider.windows.com/).</span></span> <span data-ttu-id="69739-106">Dopo aver [installato la build di anteprima](surface-hub-install-2020preview.md), è possibile eseguire la migrazione dall'autenticazione di base legacy e usare i miglioramenti di sicurezza più recenti di Microsoft Azure ed Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="69739-106">Once you [install the preview build](surface-hub-install-2020preview.md), you can migrate from legacy basic authentication and utilize the latest security improvements from Microsoft Azure and Exchange Online.</span></span> <span data-ttu-id="69739-107">Con l'aggiornamento di 2020, Surface Hub supporta i protocolli di Exchange Web Services (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) che Abilita Exchange Online per la sincronizzazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="69739-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication enabling Exchange Online for Device Account syncing.</span></span>

<span data-ttu-id="69739-108">Per i nuovi account basati sul cloud, Surface Hub USA automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere ulteriore configurazione oltre a creare semplicemente account di dispositivo usando il formato [alias@contoso.com](mailto:alias@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="69739-108">For new cloud-based accounts, Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply creating device accounts using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="69739-109">Non usare il formato legacy-Contoso\alias, che non è supportato per l'autenticazione moderna.</span><span class="sxs-lookup"><span data-stu-id="69739-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="69739-110">Per altre informazioni, Vedi [creare l'account del dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span><span class="sxs-lookup"><span data-stu-id="69739-110">For more information, see [Create Surface Hub 2S device account](https://docs.microsoft.com/surface-hub/surface-hub-2s-account).</span></span>

> [!NOTE]
> <span data-ttu-id="69739-111">Surface Hub non supporta l'autenticazione moderna per gli account locali.</span><span class="sxs-lookup"><span data-stu-id="69739-111">Surface Hub does not support modern authentication for on-premises accounts.</span></span> <span data-ttu-id="69739-112">Gli account devono essere creati nel cloud.</span><span class="sxs-lookup"><span data-stu-id="69739-112">The accounts must be created in the cloud.</span></span>


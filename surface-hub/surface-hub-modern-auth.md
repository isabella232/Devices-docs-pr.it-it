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
# <a name="modern-authentication-on-surface-hub"></a><span data-ttu-id="241b7-104">Autenticazione moderna di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="241b7-104">Modern authentication on Surface Hub</span></span>

<span data-ttu-id="241b7-105">Windows 10 Team 2020 Update aggiunge il supporto per l'autenticazione moderna dell'account del dispositivo Hub in alcuni scenari.</span><span class="sxs-lookup"><span data-stu-id="241b7-105">The Windows 10 Team 2020 Update adds support for modern authentication of the Hub device account in some scenarios.</span></span> <span data-ttu-id="241b7-106">Dopo aver installato l'aggiornamento 2020, è possibile eseguire la migrazione dall'autenticazione di base legacy per utilizzare i miglioramenti di sicurezza più recenti se l'account del dispositivo esegue l'autenticazione tramite Azure Active Directory e la cassetta postale dell'account è ospitata in Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="241b7-106">Once you install the 2020 update, you can migrate from legacy basic authentication to make use of the latest security improvements if the device account authenticates via Azure Active Directory and the account's mailbox is hosted in Exchange Online.</span></span> <span data-ttu-id="241b7-107">Con l'aggiornamento 2020, Surface Hub supporta i protocolli di Servizi Web Exchange (EWS) e l'autenticazione basata su Active Directory Authentication Library (ADAL) durante la sincronizzazione dell'account del dispositivo con Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="241b7-107">With the 2020 Update, Surface Hub supports Exchange Web Services (EWS) protocols and Active Directory Authentication Library (ADAL) based authentication when syncing the device account with Exchange Online.</span></span>

<span data-ttu-id="241b7-108">Per i nuovi account basati su cloud, Surface Hub usa automaticamente l'autenticazione moderna per connettersi a Exchange Online senza richiedere una configurazione aggiuntiva oltre ad aggiungere semplicemente l'account del dispositivo a Surface Hub usando il formato [alias@contoso.com](mailto:alias@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="241b7-108">For new cloud-based accounts, the Surface Hub automatically uses Modern Authentication to connect to Exchange Online without requiring additional configuration beyond simply adding the device account to the Surface Hub using the format [alias@contoso.com](mailto:alias@contoso.com).</span></span> <span data-ttu-id="241b7-109">Non utilizzare il formato legacy : Contoso\alias, che non è supportato per l'autenticazione moderna.</span><span class="sxs-lookup"><span data-stu-id="241b7-109">Do not use the legacy format – Contoso\alias, which is not supported for modern authentication.</span></span> <span data-ttu-id="241b7-110">Per altre informazioni, vedi [Creare e testare un account del dispositivo.](create-and-test-a-device-account-surface-hub.md)</span><span class="sxs-lookup"><span data-stu-id="241b7-110">For more information, see [create and test a device account](create-and-test-a-device-account-surface-hub.md).</span></span>

> [!NOTE]
> <span data-ttu-id="241b7-111">L'autenticazione moderna non è supportata per gli account Surface Hub locali.</span><span class="sxs-lookup"><span data-stu-id="241b7-111">Modern authentication is not supported for on-premises Surface Hub accounts.</span></span> <span data-ttu-id="241b7-112">Gli account devono usare solo Azure AD per l'autenticazione.</span><span class="sxs-lookup"><span data-stu-id="241b7-112">The accounts must use only Azure AD for authentication.</span></span>

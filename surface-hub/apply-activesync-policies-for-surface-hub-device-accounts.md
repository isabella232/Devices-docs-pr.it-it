---
title: Applicazione criteri ActiveSync ad account dispositivo - Surface Hub
description: L'account del dispositivo Microsoft Surface Hub usa ActiveSync per sincronizzare l'e-mail e il calendario. In questo modo gli utenti possono partecipare e avviare riunioni pianificate da Surface Hub, nonché inviare tramite e-mail tutte le lavagne create durante la riunione.
ms.assetid: FAABBA74-3088-4275-B58E-EC1070F4D110
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, criteri ActiveSync
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 7ead08e49d3eee2d616ac9fcf06b85dd82e136dc
ms.sourcegitcommit: 4ec96ff1cd563d055fa0689a63f136acf2794a2e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "11474733"
---
# <a name="applying-activesync-policies-to-device-accounts-surface-hub"></a><span data-ttu-id="1c603-105">Applicazione di criteri ActiveSync agli account del dispositivo - Surface Hub</span><span class="sxs-lookup"><span data-stu-id="1c603-105">Applying ActiveSync policies to device accounts (Surface Hub)</span></span>


<span data-ttu-id="1c603-106">I dispositivi Surface Hub che usano account del dispositivo Active Directory (provisioning nell'Hub in formato **dominio\nome** utente) e i servizi exchange locali usano ActiveSync per sincronizzare posta e calendario.</span><span class="sxs-lookup"><span data-stu-id="1c603-106">Surface Hubs using Active Directory device accounts (provisioned on the Hub in **domain\username** format) and on-premises Exchange services make use of ActiveSync to sync mail and calendar.</span></span> <span data-ttu-id="1c603-107">In questo modo gli utenti possono partecipare e avviare riunioni pianificate da Surface Hub, nonché inviare tramite e-mail tutte le lavagne create durante la riunione.</span><span class="sxs-lookup"><span data-stu-id="1c603-107">This allows people to join and start scheduled meetings from the Surface Hub, and allows them to email any whiteboards they have made during their meeting.</span></span>

<span data-ttu-id="1c603-108">Per il corretto funzionamento di queste funzionalità, i criteri di ActiveSync per l'organizzazione devono essere configurati come segue:</span><span class="sxs-lookup"><span data-stu-id="1c603-108">For these features to work, the ActiveSync policies for your organization must be configured as follows:</span></span>

-   <span data-ttu-id="1c603-109">Non possono esistere criteri globali che bloccano la sincronizzazione della cassetta postale delle risorse usata dall'account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c603-109">There can't be any global policies that block synchronization of the resource mailbox that's being used by the Surface Hub’s device account.</span></span> <span data-ttu-id="1c603-110">Se esiste un criterio di blocco di questo tipo, devi aggiungere Surface Hub come dispositivo consentito.</span><span class="sxs-lookup"><span data-stu-id="1c603-110">If there is such a blocking policy, you need to add the Surface Hub as an allowed device.</span></span>
-   <span data-ttu-id="1c603-111">Devi impostare un criterio cassetta postale per dispositivi mobili con l'impostazione **PasswordEnabled** impostata su False.</span><span class="sxs-lookup"><span data-stu-id="1c603-111">You must set a mobile device mailbox policy where the **PasswordEnabled** setting is set to False.</span></span> <span data-ttu-id="1c603-112">Le altre impostazioni del criterio cassetta postale per dispositivi mobili non sono compatibili con il dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c603-112">Other mobile device mailbox policy settings are not compatible with the Surface Hub.</span></span>

## <a name="allowing-the-deviceid"></a><span data-ttu-id="1c603-113">Autorizzazione di DeviceID</span><span class="sxs-lookup"><span data-stu-id="1c603-113">Allowing the DeviceID</span></span>

<span data-ttu-id="1c603-114">L'organizzazione potrebbe disporre di un criterio globale che impedisce la sincronizzazione degli account del dispositivo configurati nei dispositivi Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c603-114">Your organization may have a global policy that prevents syncing of device accounts provisioned on Surface Hubs.</span></span> <span data-ttu-id="1c603-115">Per configurare questa proprietà, vedi [Consentire ID di dispositivo per ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).</span><span class="sxs-lookup"><span data-stu-id="1c603-115">To configure this property, see [Allowing device IDs for ActiveSync](appendix-a-powershell-scripts-for-surface-hub.md#allowing-device-ids-for-activesync).</span></span>

## <a name="setting-passwordenabled"></a><span data-ttu-id="1c603-116">Impostazione di PasswordEnabled</span><span class="sxs-lookup"><span data-stu-id="1c603-116">Setting PasswordEnabled</span></span>

<span data-ttu-id="1c603-117">L'account del dispositivo deve disporre di un criterio di ActiveSync con l'attributo **PasswordEnabled** impostato su False o 0.</span><span class="sxs-lookup"><span data-stu-id="1c603-117">The device account must have an ActiveSync policy where the **PasswordEnabled** attribute is set to False or 0.</span></span> <span data-ttu-id="1c603-118">Per configurare questa proprietà, vedi [Creare un criterio di Microsoft Exchange ActiveSync compatibile con Surface Hub](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).</span><span class="sxs-lookup"><span data-stu-id="1c603-118">To configure this property, see [Creating a Surface Hub-compatible Microsoft Exchange ActiveSync policy](appendix-a-powershell-scripts-for-surface-hub.md#create-compatible-as-policy).</span></span>

 

 






---
title: Novità di Windows 10, versione 1703 per Surface Hub
description: Windows 10, versione 1703 (Creators Update) offre nuove funzionalità per Microsoft Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 01/18/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: bdc6e384839606fe6138c75e190d68a84679f5b4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832690"
---
# <span data-ttu-id="1c217-103">Quali sono le novità di Windows 10, versione 1703 per Microsoft Surface Hub?</span><span class="sxs-lookup"><span data-stu-id="1c217-103">What's new in Windows 10, version 1703 for Microsoft Surface Hub?</span></span>

<span data-ttu-id="1c217-104">Guarda Jordan Marchese, tecnico di Surface Hub, presentare gli aggiornamenti a Microsoft Surface Hub con Windows 10, versione 1703 (Creators Update).</span><span class="sxs-lookup"><span data-stu-id="1c217-104">Watch Surface Hub engineer Jordan Marchese present updates to Microsoft Surface Hub with Windows 10, version 1703 (Creators Update).</span></span> 

<a href="https://www.youtube.com/watch?v=R8tX10VIgq0" target="_blank"> <img src="images/whats-new-video-thumbnail.png" alt="Link to Surface Hub video on Youtube" /></a>

<span data-ttu-id="1c217-105">Windows 10, versione 1703 (detta anche Creators Update), presenta le seguenti modifiche per Microsoft Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c217-105">Windows 10, version 1703 (also called the Creators Update), introduces the following changes for Microsoft Surface Hub.</span></span>

## <span data-ttu-id="1c217-106">Nuove impostazioni</span><span class="sxs-lookup"><span data-stu-id="1c217-106">New settings</span></span>

<span data-ttu-id="1c217-107">Sono state aggiunte nuove impostazioni alla gestione dei dispositivi mobili (MDM, Mobile Device Management) e ai provider dei servizi di configurazione (CSP) per espandere le funzionalità di gestione di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c217-107">Settings have been added to mobile device management (MDM) and configuration service providers (CSPs) to expand the Surface Hub management capabilities.</span></span> <span data-ttu-id="1c217-108">[Le nuove impostazioni includono](manage-settings-with-mdm-for-surface-hub.md):</span><span class="sxs-lookup"><span data-stu-id="1c217-108">[New settings include](manage-settings-with-mdm-for-surface-hub.md):</span></span>

- <span data-ttu-id="1c217-109">InBoxApps/SkypeForBusiness/DomainName</span><span class="sxs-lookup"><span data-stu-id="1c217-109">InBoxApps/SkypeForBusiness/DomainName</span></span>
- <span data-ttu-id="1c217-110">InBoxApps/Connect/AutoLaunch</span><span class="sxs-lookup"><span data-stu-id="1c217-110">InBoxApps/Connect/AutoLaunch</span></span>
- <span data-ttu-id="1c217-111">Proprietà/DefaultVolume</span><span class="sxs-lookup"><span data-stu-id="1c217-111">Properties/DefaultVolume</span></span>
- <span data-ttu-id="1c217-112">Proprietà/ScreenTimeout</span><span class="sxs-lookup"><span data-stu-id="1c217-112">Properties/ScreenTimeout</span></span>
- <span data-ttu-id="1c217-113">Proprietà/SessionTimeout</span><span class="sxs-lookup"><span data-stu-id="1c217-113">Properties/SessionTimeout</span></span>
- <span data-ttu-id="1c217-114">Proprietà/SleepTimeout</span><span class="sxs-lookup"><span data-stu-id="1c217-114">Properties/SleepTimeout</span></span>
- <span data-ttu-id="1c217-115">Proprietà/AllowSessionResume</span><span class="sxs-lookup"><span data-stu-id="1c217-115">Properties/AllowSessionResume</span></span>
- <span data-ttu-id="1c217-116">Proprietà/AllowAutoProxyAuth</span><span class="sxs-lookup"><span data-stu-id="1c217-116">Properties/AllowAutoProxyAuth</span></span>
- <span data-ttu-id="1c217-117">Proprietà/DisableSigninSuggestions</span><span class="sxs-lookup"><span data-stu-id="1c217-117">Properties/DisableSigninSuggestions</span></span>
- <span data-ttu-id="1c217-118">Proprietà/DoNotShowMyMeetingsAndFiles</span><span class="sxs-lookup"><span data-stu-id="1c217-118">Properties/DoNotShowMyMeetingsAndFiles</span></span>
- <span data-ttu-id="1c217-119">Sistema/AllowStorageCard</span><span class="sxs-lookup"><span data-stu-id="1c217-119">System/AllowStorageCard</span></span>

<span data-ttu-id="1c217-120">Oltre a impostazioni basate sui nuovi [CSP NetworkQoSPolicy](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) e [CSP NetworkProxy](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp).</span><span class="sxs-lookup"><span data-stu-id="1c217-120">Plus settings based on the new [NetworkQoSPolicy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) and [NetworkProxy CSP](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp).</span></span>
</br>

## <span data-ttu-id="1c217-121">Provisioning guidato</span><span class="sxs-lookup"><span data-stu-id="1c217-121">Provisioning wizard</span></span>

<span data-ttu-id="1c217-122">Una semplice procedura guidata consente di creare velocemente pacchetti di provisioning che possono essere applicati a più dispositivi Surface Hub e di includere l'aggiunta in blocco ad Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1c217-122">An easy-to-use wizard helps you quickly create provisioning packages that you can apply to multiple Surface Hub devices, and includes bulk join to Azure Active Directory.</span></span> [<span data-ttu-id="1c217-123">Scopri come creare un pacchetto di provisioning per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="1c217-123">Learn how to create a provisioning package for Surface Hub.</span></span>](provisioning-packages-for-certificates-surface-hub.md)

![passaggi della procedura guidata per il provisioning dei dispositivi Surface Hub](images/wcd-wizard.png)
    
## <span data-ttu-id="1c217-125">Miracast sulla tua rete wireless o LAN esistente</span><span class="sxs-lookup"><span data-stu-id="1c217-125">Miracast on your existing wireless network or LAN</span></span> 

<span data-ttu-id="1c217-126">Microsoft ha esteso la possibilità di [inviare un flusso di Miracast tramite una rete locale](miracast-over-infrastructure.md), anziché tramite un link wireless diretto.</span><span class="sxs-lookup"><span data-stu-id="1c217-126">Microsoft has extended the ability to [send a Miracast stream over a local network](miracast-over-infrastructure.md) rather than over a direct wireless link.</span></span> 
    
## <span data-ttu-id="1c217-127">Ripristino cloud</span><span class="sxs-lookup"><span data-stu-id="1c217-127">Cloud recovery</span></span>

<span data-ttu-id="1c217-128">Quando reimposti un dispositivo Surface Hub, hai ora la possibilità di scaricare e installare una build di fabbrica del sistema operativo dal cloud.</span><span class="sxs-lookup"><span data-stu-id="1c217-128">When you reset a Surface Hub device, you now have the ability to download and install a factory build of the operating system from the cloud.</span></span> [<span data-ttu-id="1c217-129">Altre informazioni sul ripristino cloud.</span><span class="sxs-lookup"><span data-stu-id="1c217-129">Learn more about cloud recovery.</span></span>](device-reset-surface-hub.md#cloud-recovery)

>[!NOTE]
><span data-ttu-id="1c217-130">Il ripristino cloud non funziona se si usano server proxy.</span><span class="sxs-lookup"><span data-stu-id="1c217-130">Cloud recovery doesn't work if you use proxy servers.</span></span>
    
![Reinstalla](images/reinstall.png)
    
## <span data-ttu-id="1c217-132">Termina sessione</span><span class="sxs-lookup"><span data-stu-id="1c217-132">End session</span></span>

<span data-ttu-id="1c217-133">**Fatto** è ora **Termina sessione**.</span><span class="sxs-lookup"><span data-stu-id="1c217-133">**I'm done** is now **End session**.</span></span> [<span data-ttu-id="1c217-134">Scopri come usare Termina sessione.</span><span class="sxs-lookup"><span data-stu-id="1c217-134">Learn how to use End session.</span></span>](i-am-done-finishing-your-surface-hub-meeting.md) 

![termina sessione](images/end-session.png)



 

 

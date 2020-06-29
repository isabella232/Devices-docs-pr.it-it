---
title: Usare il nome di dominio completo con Surface Hub
description: Risolvi i problemi comuni, inclusi quelli di configurazione, e gli errori di Exchange ActiveSync.
keywords:
- Risolvere i problemi comuni
- problemi di configurazione
- Errori di Exchange ActiveSync
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.prod: surface-hub
ms.sitesec: library
ms.openlocfilehash: 79507f5b4bb22b23d1e6c4db6b4aab6ea891d876
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832655"
---
# <span data-ttu-id="ffe4a-106">Configurare il nome di dominio per Skype for Business</span><span class="sxs-lookup"><span data-stu-id="ffe4a-106">Configure domain name for Skype for Business</span></span>

<span data-ttu-id="ffe4a-107">Esistono alcuni scenari in cui è necessario specificare il nome di dominio di Skype for Business Server:</span><span class="sxs-lookup"><span data-stu-id="ffe4a-107">There are a few scenarios where you need to specify the domain name of your Skype for Business server:</span></span>
- <span data-ttu-id="ffe4a-108">**Più suffissi DNS** - Quando l'infrastruttura di Skype for Business ha spazi dei nomi disgiunti e quindi uno o più server hanno un suffisso DNS che non corrisponde al suffisso dell'indirizzo di accesso per Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-108">**Multiple DNS suffixes** - When your Skype for Business infrastructure has disjointed namespaces such that one or more servers have a DNS suffix that doesn't match the suffix of the sign-in address (SIP) for Skype for Business.</span></span>  
- <span data-ttu-id="ffe4a-109">**I suffissi di Skype for Business ed Exchange sono diversi** - Quando il suffisso dell'indirizzo di accesso per Skype for Business è diverso dal suffisso dell'indirizzo di Exchange usato per l'account di dispositivo.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-109">**Skype for Business and Exchange suffixes are different** - When the suffix of the sign-in address for Skype for Business differs from the suffix of the Exchange address used for the device account.</span></span>
- <span data-ttu-id="ffe4a-110">Uso dei **certificati** : le organizzazioni di grandi dimensioni con i server Skype for business locali usano comunemente i certificati con la propria autorità di certificazione radice.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-110">**Working with certificates** - Large organizations with on-premises Skype for Business servers commonly use certificates with their own root certificate authority (CA).</span></span> <span data-ttu-id="ffe4a-111">In genere il dominio dell'autorità di certificazione è diverso da quello di Skype for Business Server e per questo il certificato non viene considerato attendibile e l'accesso non riesce.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-111">It is common for the CA domain to be different than the domain of the Skype for Business server which causes the certificate to not be trusted, and sign-in fails.</span></span>  <span data-ttu-id="ffe4a-112">Skype deve conoscere il nome di dominio del certificato per configurare una relazione di trust.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-112">Skype needs to know the domain name of the certificate in order to set up a trust relationship.</span></span> <span data-ttu-id="ffe4a-113">In genere le aziende usano Criteri di gruppo per la versione desktop di Skype, ma l'uso di Criteri di gruppo non è supportato in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-113">Enterprises typically use Group Policy to push this out to Skype desktop, but Group Policy is not supported on Surface Hub.</span></span>

**<span data-ttu-id="ffe4a-114">Per configurare il nome di dominio per Skype for Business Server</span><span class="sxs-lookup"><span data-stu-id="ffe4a-114">To configure the domain name for your Skype for Business server</span></span>**</br>
1. <span data-ttu-id="ffe4a-115">Nel dispositivo Surface Hub apri **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-115">On Surface Hub, open **Settings**.</span></span>
2. <span data-ttu-id="ffe4a-116">Fai clic su **Surface Hub**, quindi su **Audio e chiamate**.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-116">Click **Surface Hub**, and then click **Calling & Audio**.</span></span> 
3. <span data-ttu-id="ffe4a-117">In **Configurazione di Skype for Business** fai clic su **Configura nome di dominio**.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-117">Under **Skype for Business configuration**, click **Configure domain name**.</span></span> 
4. <span data-ttu-id="ffe4a-118">Digita il nome di dominio per Skype for Business Server e quindi fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-118">Type the domain name for your Skype for Business server, and then click **Ok**.</span></span> 
   > [!TIP]
   > <span data-ttu-id="ffe4a-119">Puoi digitare più nomi di dominio, separandoli con una virgola.</span><span class="sxs-lookup"><span data-stu-id="ffe4a-119">You can type multiple domain names, separated by commas.</span></span> <br> <span data-ttu-id="ffe4a-120">Ad esempio: lync.com, outlook.com, lync.glbdns.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="ffe4a-120">For example: lync.com, outlook.com, lync.glbdns.microsoft.com</span></span>

    ![Aggiungere il nome di dominio completo di Skype for business alle impostazioni](images/system-settings-add-fqdn.png)

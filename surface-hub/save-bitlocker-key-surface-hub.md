---
title: Salvare la chiave di BitLocker (Surface Hub)
description: Ogni dispositivo Microsoft Surface Hub viene automaticamente configurato con il software di crittografia delle unità BitLocker. Microsoft consiglia vivamente di assicurarti di eseguire il backup delle chiavi di ripristino di BitLocker.
ms.assetid: E11E4AB6-B13E-4ACA-BCE1-4EDC9987E4F2
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, BitLocker, chiavi di ripristino di BitLocker
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73efa418fa80ef90a643d4fb4c457280ab982b38
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833866"
---
# <span data-ttu-id="3cd47-105">Salvare la chiave di BitLocker (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="3cd47-105">Save your BitLocker key (Surface Hub)</span></span>


<span data-ttu-id="3cd47-106">Ogni dispositivo Microsoft Surface Hub viene automaticamente configurato con il software di crittografia delle unità BitLocker.</span><span class="sxs-lookup"><span data-stu-id="3cd47-106">Every Microsoft Surface Hub is automatically set up with BitLocker drive encryption software.</span></span> <span data-ttu-id="3cd47-107">Microsoft consiglia vivamente di assicurarti di eseguire il backup delle chiavi di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="3cd47-107">Microsoft strongly recommends that you make sure you back up your BitLocker recovery keys.</span></span>

<span data-ttu-id="3cd47-108">Esistono diversi modi per gestire la chiave BitLocker in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="3cd47-108">There are several ways to manage your BitLocker key on the Surface Hub.</span></span>

1.  <span data-ttu-id="3cd47-109">Se hai aggiunto il dispositivo Surface Hub a un dominio, il dispositivo eseguirà il backup della chiave nel dominio e la archivierà nell'oggetto computer.</span><span class="sxs-lookup"><span data-stu-id="3cd47-109">If you’ve joined the Surface Hub to a domain, the device will back up the key on the domain and store it under the computer object.</span></span>

    <span data-ttu-id="3cd47-110">Se non riesci a trovare la chiave BitLocker dopo aver aggiunto il dispositivo a un dominio, è probabile che lo schema di Active Directory non supporti il backup della chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="3cd47-110">If you can’t find the BitLocker key after joining the device to a domain, it’s likely that your Active Directory schema doesn’t support BitLocker key backup.</span></span> <span data-ttu-id="3cd47-111">Se non vuoi modificare lo schema, puoi salvare la chiave BitLocker accedendo a Impostazioni e seguendo la procedura per usare un account amministratore locale, descritta nel dettaglio più avanti nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="3cd47-111">If you don’t want to change the schema, you can save the BitLocker key by going to Settings and following the procedure for using a local admin account, which is detailed later in this list.</span></span>

2.  <span data-ttu-id="3cd47-112">Se hai aggiunto il dispositivo Surface Hub ad Azure Active Directory (Azure AD), la chiave BitLocker verrà archiviata con l'account usato per aggiungere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3cd47-112">If you’ve joined the Surface Hub to Azure Active Directory (Azure AD), the BitLocker key will be stored under the account that was used to join the device.</span></span>

3.  <span data-ttu-id="3cd47-113">Se si usa un account di amministrazione locale per gestire il dispositivo, è possibile salvare la chiave BitLocker accedendo all'app **Impostazioni** e passando a **Aggiorna &** &gt; **ripristino**della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="3cd47-113">If you’re using a local admin account to manage the device, you can save the BitLocker key by going to the **Settings** app and navigating to **Update & security** &gt; **Recovery**.</span></span> <span data-ttu-id="3cd47-114">Inserisci un'unità USB e seleziona l'opzione per salvare la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="3cd47-114">Insert a USB drive and select the option to save the BitLocker key.</span></span> <span data-ttu-id="3cd47-115">La chiave verrà salvata in un file di testo nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="3cd47-115">The key will be saved to a text file on the USB drive.</span></span>


## <span data-ttu-id="3cd47-116">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="3cd47-116">Related topics</span></span>

[<span data-ttu-id="3cd47-117">Gestire Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="3cd47-117">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="3cd47-118">Manuale dell'amministratore di Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="3cd47-118">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

 

 






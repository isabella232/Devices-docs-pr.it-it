---
title: Gestione delle password (Surface Hub)
description: Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo.
ms.assetid: 0FBFB546-05F0-430E-905E-87111046E4B8
ms.reviewer: ''
manager: laurawi
keywords: password, gestione delle password, rotazione delle password, account del dispositivo
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: bef626fce875d5074f3ed47ed957e821beec7c77
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834028"
---
# <span data-ttu-id="5981d-104">Gestione delle password (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="5981d-104">Password management (Surface Hub)</span></span>

<span data-ttu-id="5981d-105">Ogni account del dispositivo Microsoft Surface Hub richiede una password per l'autenticazione e l'abilitazione delle funzionalità nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5981d-105">Every Microsoft Surface Hub device account requires a password to authenticate and enable features on the device.</span></span> <span data-ttu-id="5981d-106">Per motivi di sicurezza, potrebbe essere utile modificare la password o impostarne la "rotazione" con regolarità.</span><span class="sxs-lookup"><span data-stu-id="5981d-106">For security reasons, you may want to change (or "rotate") this password regularly.</span></span> <span data-ttu-id="5981d-107">Tuttavia, se la password dell'account del dispositivo cambia, la password precedentemente archiviata nel dispositivo Surface Hub non sarà più valida e tutte le funzionalità che dipendono dall'account del dispositivo verranno disabilitate.</span><span class="sxs-lookup"><span data-stu-id="5981d-107">However, if the device account’s password changes, the password that was previously stored on the Surface Hub will be invalid, and all features that depend on the device account will be disabled.</span></span> <span data-ttu-id="5981d-108">Sarà necessario aggiornare la password dell'account del dispositivo in Surface Hub dall'app Impostazioni per riabilitare queste funzionalità.</span><span class="sxs-lookup"><span data-stu-id="5981d-108">You will need to update the device account’s password on the Surface Hub from the Settings app to re-enable these features.</span></span>

<span data-ttu-id="5981d-109">Per semplificare la gestione delle password per gli account del dispositivo Surface Hub, sono disponibili due opzioni:</span><span class="sxs-lookup"><span data-stu-id="5981d-109">To simplify password management for your Surface Hub device accounts, there are two options:</span></span>

1.  <span data-ttu-id="5981d-110">Disattivare la scadenza delle password per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5981d-110">Turn off password expiration for the device account.</span></span>
2.  <span data-ttu-id="5981d-111">Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5981d-111">Allow the Surface Hub to automatically rotate the device account’s password.</span></span>


## <span data-ttu-id="5981d-112">Disattivare la rotazione delle password per l'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5981d-112">Turn off password rotation for the device account</span></span>

<span data-ttu-id="5981d-113">Imposta la proprietà **PasswordNeverExpires** dell'account del dispositivo su True.</span><span class="sxs-lookup"><span data-stu-id="5981d-113">Set the device account’s **PasswordNeverExpires** property to True.</span></span> <span data-ttu-id="5981d-114">Devi verificare se l'impostazione soddisfa i requisiti di sicurezza della tua organizzazione.</span><span class="sxs-lookup"><span data-stu-id="5981d-114">You should verify whether this meets your organization’s security requirements.</span></span>


## <span data-ttu-id="5981d-115">Consentire al dispositivo Surface Hub di ruotare automaticamente la password dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="5981d-115">Allow the Surface Hub to automatically rotate the device account’s password</span></span>

<span data-ttu-id="5981d-116">Il dispositivo Surface Hub può gestire una password dell'account del dispositivo cambiandola frequentemente senza richiedere l'aggiornamento manuale delle informazioni dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5981d-116">The Surface Hub can manage a device account’s password by changing it frequently without requiring you to manually update the device account’s information.</span></span> <span data-ttu-id="5981d-117">Puoi abilitare questa funzionalità in **Impostazioni**.</span><span class="sxs-lookup"><span data-stu-id="5981d-117">You can enable this feature in **Settings**.</span></span> <span data-ttu-id="5981d-118">Una volta abilitata, la password dell'account del dispositivo cambierà ogni settimana durante l'orario di manutenzione.</span><span class="sxs-lookup"><span data-stu-id="5981d-118">Once enabled, the device account's password will change weekly during maintenance hours.</span></span>

<span data-ttu-id="5981d-119">Importante: quando la password dell'account del dispositivo viene modificata, la nuova password non verrà più visualizzata.</span><span class="sxs-lookup"><span data-stu-id="5981d-119">Note that when the device account’s password is changed, you will not be shown the new password.</span></span> <span data-ttu-id="5981d-120">Se hai bisogno di accedere all'account o per specificare nuovamente la password (ad esempio, se vuoi modificare le impostazioni dell'account del dispositivo in Surface Hub), devi reimpostare la password con Active Directory o tramite il portale di amministrazione di Office 365.</span><span class="sxs-lookup"><span data-stu-id="5981d-120">If you need to sign in to the account, or to provide the password again (for example, if you want to change the device account settings on the Surface Hub), then you'll need use Active Directory or the Office 365 admin portal to reset the password.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5981d-121">Se l'organizzazione usa una topologia ibrida (con alcuni servizi ospitati in locale e alcuni ospitati online tramite Office 365), dovrai configurare l'account del dispositivo nel formato **dominio\nomeutente**.</span><span class="sxs-lookup"><span data-stu-id="5981d-121">If your organization uses a hybrid topology (some services are hosted on-premises and some are hosted online through Office 365), you must setup the device account in **domain\username** format.</span></span> <span data-ttu-id="5981d-122">In caso contrario, la rotazione delle password non funzionerà.</span><span class="sxs-lookup"><span data-stu-id="5981d-122">Otherwise, password rotation will not work.</span></span>

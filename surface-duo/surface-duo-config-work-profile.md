---
title: Configurare il profilo di lavoro Android Enterprise per Surface Duo
description: Questo articolo illustra come configurare il profilo di lavoro in Surface Duo.
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/25/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 393844a4e4f0f06f16d11d1313ec9aacfa109d57
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326193"
---
# <span data-ttu-id="fc5b6-103">Configurare il profilo di lavoro Android Enterprise per Surface Duo</span><span class="sxs-lookup"><span data-stu-id="fc5b6-103">Configure Android Enterprise Work Profile for Surface Duo</span></span>

<span data-ttu-id="fc5b6-104">Mirate alle distribuzioni di BYOD, i profili di lavoro offrono uno spazio separato in duo per le app e i dati di lavoro, offrendo alle organizzazioni il controllo completo dei loro dati, delle app e i criteri di sicurezza senza impedire ai dipendenti di usare il loro dispositivo per le app e i dati personali.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-104">Targeted at  BYOD deployments, work profiles provide a separate space on Duo for work apps and data, giving organizations full control of their data, apps, and security policies without preventing employees from using their device for personal apps and data.</span></span>

### <span data-ttu-id="fc5b6-105">Configurare il profilo di lavoro aziendale Android</span><span class="sxs-lookup"><span data-stu-id="fc5b6-105">Set up Android Enterprise Work Profile</span></span>

<span data-ttu-id="fc5b6-106">Usare i profili di lavoro per gestire i dati aziendali e le app nei dispositivi Android di proprietà dell'utente.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-106">Use work profiles to manage corporate data and apps on user-owned Android devices.</span></span> <span data-ttu-id="fc5b6-107">Per impostazione predefinita, la registrazione dei dispositivi di profili di lavoro personali è abilitata e non richiede ulteriori configurazioni di amministratore.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-107">By default, enrollment of personally owned work profile devices is enabled and requires no further admin configuration.</span></span>  

**<span data-ttu-id="fc5b6-108">Per abilitare il profilo di lavoro aziendale:</span><span class="sxs-lookup"><span data-stu-id="fc5b6-108">To enable Enterprise Work Profile:</span></span>**

- <span data-ttu-id="fc5b6-109">In Endpoint Manager selezionare **Devices**  >  **Android per**  >  **la registrazione** e quindi selezionare **dispositivi personali con il profilo lavoro**.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-109">In Endpoint Manager, select **Devices** > **Android** > **Android enrollment** and then select **Personal devices with work profile**.</span></span>
<br><br>
 ![Abilitare il profilo di lavoro aziendale](images/enroll-start.png)

 
**<span data-ttu-id="fc5b6-111">Accedere a Surface Duo con il profilo di lavoro Android Enterprise</span><span class="sxs-lookup"><span data-stu-id="fc5b6-111">Sign into Surface Duo with Android Enterprise Work Profile</span></span>**

1. <span data-ttu-id="fc5b6-112">Installare l'app portale aziendale da Google Play Store ed eseguire l'accesso con l'account Microsoft Work o dell'Istituto di istruzione.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-112">Install the Company Portal app from Google Play Store and sign in with your Microsoft work or school account.</span></span><br><br>
![Accedere a Surface Duo](images/duo-wp-1.png)
 
2. <span data-ttu-id="fc5b6-114">Nella pagina Configurazione di Access selezionare **inizia**.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-114">On the Access Setup page, select **Begin**.</span></span><br><br>
![Iniziare](images/duo-wp-2.png)

3. <span data-ttu-id="fc5b6-116">Esaminare le informazioni nella pagina privacy e selezionare **continue**.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-116">Review the information on the privacy page and select **Continue**.</span></span><br><br>
 ![Continua](images/duo-wp-3.png)
<br><br>
 ![Selezionare continua](images/duo-wp-4.png)
 
4. <span data-ttu-id="fc5b6-119">Al termine della configurazione del profilo di lavoro, selezionare **continua** per attivare e registrare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-119">When the work profile setup completes, select **Continue** to activate and register the device.</span></span><br><br>
 ![Selezionare continua per attivare e registrare il dispositivo](images/duo-wp-5.png)

5. <span data-ttu-id="fc5b6-121">Seleziona **Continua**.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-121">Select **Continue**.</span></span><br><br>
 ![Selezionare continua di nuovo](images/duo-wp-6.png)

6. <span data-ttu-id="fc5b6-123">Dopo aver attivato il profilo di lavoro, selezionare **continua** per aggiornare le impostazioni del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-123">When you have activated the work profile, select **Continue** to update device settings.</span></span> <span data-ttu-id="fc5b6-124">In questo esempio, il profilo di lavoro applica un'impostazione MDM per richiedere una password alfanumerica a 6 cifre più forte.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-124">In this example, the work profile applies an MDM setting to require a stronger 6-digit alphanumeric password.</span></span> <br><br>

     ![Esempio di password alfanumerica](images/duo-wp-7.png)<br><br>
7. <span data-ttu-id="fc5b6-126">Selezionare **Risolvi** per immettere l'autenticazione necessaria e quindi selezionare **continua** per completare la configurazione del profilo di lavoro.</span><span class="sxs-lookup"><span data-stu-id="fc5b6-126">Select **Resolve** to enter the required authentication and then select **Continue** to complete Work Profile setup.</span></span> <br><br>
     ![Selezionare continua per completare la configurazione](images/duo-wp-8.png)<br><br>
     ![configurazione completa](images/duo-wp-9.png)<br><br>

## <span data-ttu-id="fc5b6-129">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="fc5b6-129">Learn more</span></span>

- [<span data-ttu-id="fc5b6-130">Configurare la registrazione dei dispositivi di profilo aziendale di Android</span><span class="sxs-lookup"><span data-stu-id="fc5b6-130">Set up enrollment of Android Enterprise work profile devices</span></span>](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)


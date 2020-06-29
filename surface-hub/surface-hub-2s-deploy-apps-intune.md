---
title: Distribuire app in Surface Hub 2S con Intune
description: Informazioni su come distribuire le app in Surface Hub 2S usando Intune.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 51e54a5b2881519f2fc361675253c9e50bad0864
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833284"
---
# <span data-ttu-id="45d30-104">Distribuire app in Surface Hub 2S con Intune</span><span class="sxs-lookup"><span data-stu-id="45d30-104">Deploy apps to Surface Hub 2S using Intune</span></span>

<span data-ttu-id="45d30-105">È possibile installare altre app per soddisfare le esigenze del team o dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="45d30-105">You can install additional apps to fit your team or organization's needs.</span></span>

## <span data-ttu-id="45d30-106">Linee guida per gli sviluppatori</span><span class="sxs-lookup"><span data-stu-id="45d30-106">Developer guidelines</span></span>

- <span data-ttu-id="45d30-107">Surface Hub esegue solo le [app della piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp).</span><span class="sxs-lookup"><span data-stu-id="45d30-107">Surface Hub only runs [Universal Windows Platform (UWP) apps](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp).</span></span> <span data-ttu-id="45d30-108">Le app create utilizzando [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) non verranno eseguite su Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="45d30-108">Apps created using the [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) will not run on Surface Hub.</span></span>
- <span data-ttu-id="45d30-109">Le app devono essere destinate alla [famiglia di dispositivi universali](https://msdn.microsoft.com/library/windows/apps/dn894631) o alla famiglia di dispositivi Windows Team.</span><span class="sxs-lookup"><span data-stu-id="45d30-109">Apps must be targeted for the [Universal device family](https://msdn.microsoft.com/library/windows/apps/dn894631) or Windows Team device family.</span></span>
- <span data-ttu-id="45d30-110">Surface Hub supporta solo le [app con licenza offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) di [Microsoft Store for business](https://businessstore.microsoft.com/store).</span><span class="sxs-lookup"><span data-stu-id="45d30-110">Surface Hub only supports [offline-licensed apps](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) from [Microsoft Store for Business](https://businessstore.microsoft.com/store).</span></span>
- <span data-ttu-id="45d30-111">Per impostazione predefinita, le app devono riportare la firma dello Store per essere installate.</span><span class="sxs-lookup"><span data-stu-id="45d30-111">By default, apps must be Store-signed to be installed.</span></span> <span data-ttu-id="45d30-112">Durante lo sviluppo e il test, puoi anche scegliere di eseguire app UWP firmate dallo sviluppatore inserendo il dispositivo in modalità sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="45d30-112">During testing and development, you can also choose to run developer-signed UWP apps by placing the device in developer mode.</span></span>
- <span data-ttu-id="45d30-113">Durante lo sviluppo e l'invio di app a Microsoft Store, imposta la disponibilità della famiglia di dispositivi e le opzioni di licenza organizzativa per verificare che le app siano disponibili per l'esecuzione su Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="45d30-113">When developing and submitting apps to the Microsoft Store, set Device family availability and Organizational licensing options to ensure that apps are available to run on Surface Hub.</span></span>
- <span data-ttu-id="45d30-114">Sono necessarie credenziali di amministratore per installare le app in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="45d30-114">You need admin credentials to install apps on Surface Hub.</span></span> <span data-ttu-id="45d30-115">Progettato per l'uso nelle sale riunioni e in altri spazi condivisi, Surface Hub impedisce agli utenti abituali di accedere a Microsoft Store per scaricare e installare le app.</span><span class="sxs-lookup"><span data-stu-id="45d30-115">Designed for use in meeting rooms and other shared spaces, Surface Hub prevents regular users from accessing the Microsoft Store to download and install apps.</span></span>

## <span data-ttu-id="45d30-116">Linee guida per la distribuzione</span><span class="sxs-lookup"><span data-stu-id="45d30-116">Deployment guidelines</span></span>

<span data-ttu-id="45d30-117">Puoi distribuire app UWP (Universal Windows Platform) a Surface Hub 2S usando Intune, facilitando la distribuzione delle app ai dispositivi.</span><span class="sxs-lookup"><span data-stu-id="45d30-117">You can deploy Universal Windows Platform (UWP) apps to Surface Hub 2S using Intune, easing app deployment to devices.</span></span>

1. <span data-ttu-id="45d30-118">Per distribuire le app, Abilita MDM per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="45d30-118">To deploy apps, enable MDM for your organization.</span></span> <span data-ttu-id="45d30-119">Nel portale di Intune selezionare **Intune** come autorità MDM (scelta consigliata).</span><span class="sxs-lookup"><span data-stu-id="45d30-119">In the Intune portal, select **Intune** as your MDM Authority (recommended).</span></span> <br>

    ![Scegliere autorità MDM](images/sh2-set-intune5.png)

2. <span data-ttu-id="45d30-121">Abilitare Microsoft Store for business in Intune.</span><span class="sxs-lookup"><span data-stu-id="45d30-121">Enable the Microsoft Store for Business in Intune.</span></span> <span data-ttu-id="45d30-122">Aprire Intune, selezionare **app client**  >  **Microsoft Store for business.**</span><span class="sxs-lookup"><span data-stu-id="45d30-122">Open Intune, select **Client apps** > **Microsoft Store for Business.**</span></span> <br>

    ![Abilitare Store for business](images/sh2-deploy-apps-sync.png)

3. <span data-ttu-id="45d30-124">In Intune aprire **Microsoft Store for business** e selezionare **Impostazioni**  >  **Distribuisci**  >  **strumenti di gestione**.</span><span class="sxs-lookup"><span data-stu-id="45d30-124">In Intune open **Microsoft Store for Business** and select **Settings** > **Distribute** > **Management tools**.</span></span> <span data-ttu-id="45d30-125">Scegliere **Microsoft Intune** come strumento di gestione.</span><span class="sxs-lookup"><span data-stu-id="45d30-125">Choose **Microsoft Intune** as your management tool.</span></span> <br>

    ![Aggiungere Intune come strumento di gestione](images/sh2-set-intune8.png)

4. <span data-ttu-id="45d30-127">In Microsoft Store for business selezionare **Impostazioni**  >  **Shop**  >  **shopping experience**Shop e quindi selezionare **Mostra app offline**.</span><span class="sxs-lookup"><span data-stu-id="45d30-127">In Microsoft Store for Business, select **Settings** > **Shop** > **Shopping Experience**, and then select **Show offline apps**.</span></span> <span data-ttu-id="45d30-128">Le app offline si riferiscono alle app che possono essere sincronizzate con Intune e distribuite centralmente in un dispositivo.</span><span class="sxs-lookup"><span data-stu-id="45d30-128">Offline apps refer to apps that can be synced to Intune and centrally deployed to a device.</span></span>
5. <span data-ttu-id="45d30-129">Dopo aver abilitato lo shopping offline, puoi acquistare licenze offline per le app che puoi sincronizzare con Intune e distribuire come licenze per dispositivi.</span><span class="sxs-lookup"><span data-stu-id="45d30-129">After enabling Offline shopping, you can acquire offline licenses for apps that you can sync to Intune and deploy as Device licensing.</span></span>
6. <span data-ttu-id="45d30-130">Nelle **Intune**  >  **app client**di Intune  >  **Microsoft Store for business**selezionare **Sincronizza**.</span><span class="sxs-lookup"><span data-stu-id="45d30-130">In **Intune** > **Client apps** > **Microsoft Store for Business**, select **Sync**.</span></span>
7. <span data-ttu-id="45d30-131">Nella pagina app client cerca l'app nell'elenco delle app.</span><span class="sxs-lookup"><span data-stu-id="45d30-131">In the Client apps page, search for the app in the apps list.</span></span> <span data-ttu-id="45d30-132">Assegna le app al gruppo o ai gruppi di dispositivi desiderati.</span><span class="sxs-lookup"><span data-stu-id="45d30-132">Assign the apps to the desired device group or groups.</span></span> <span data-ttu-id="45d30-133">Selezionare **assegnazioni**  >  **gruppo Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="45d30-133">Select **Assignments** > **Add group**.</span></span> <br>

![\* Assegnazione di app a gruppi \*](images/sh2-assign-group.png) <br>

8. <span data-ttu-id="45d30-135">In tipo di assegnazione scegliere **obbligatorio**.</span><span class="sxs-lookup"><span data-stu-id="45d30-135">Under assignment type, choose **Required**.</span></span> <br>

![\* Assegnazione di app a gruppi \*](images/sh2-add-group.png) <br>

9. <span data-ttu-id="45d30-137">Per i gruppi selezionati, scegliere **licenze per dispositivi** e quindi fare clic su **OK** e salvare l'assegnazione.</span><span class="sxs-lookup"><span data-stu-id="45d30-137">For the selected groups, choose **Device licensing** and then select **OK** and save the assignment.</span></span> <br>
 
![\* Assegnazione di app a gruppi \*](images/sh2-apps-assign.png)

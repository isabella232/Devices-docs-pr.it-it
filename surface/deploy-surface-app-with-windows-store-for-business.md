---
title: Distribuire l'app Surface con Microsoft Store per le aziende o Microsoft Store per la formazione (Surface)
description: Scopri come aggiungere e scaricare l'app Surface con Microsoft Store per le aziende o Microsoft Store per la formazione, oltre a installare l'app Surface con PowerShell e MDT.
keywords: surface app, app, distribuzione, personalizzare
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, store
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.date: 4/16/2021
ms.openlocfilehash: c7a882859339ff3d7feeb685c62672bc57c301ec
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576526"
---
# <a name="deploy-surface-app-with-microsoft-store-for-business-and-education"></a><span data-ttu-id="ec2e6-104">Distribuire l'app Surface con Microsoft Store per le aziende e Education</span><span class="sxs-lookup"><span data-stu-id="ec2e6-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="ec2e6-105">Si applica a</span><span class="sxs-lookup"><span data-stu-id="ec2e6-105">Applies to</span></span>**

- <span data-ttu-id="ec2e6-106">Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="ec2e6-106">Surface Laptop 4</span></span>
- <span data-ttu-id="ec2e6-107">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="ec2e6-107">Surface Pro 7+</span></span>
- <span data-ttu-id="ec2e6-108">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="ec2e6-108">Surface Laptop Go</span></span>
- <span data-ttu-id="ec2e6-109">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="ec2e6-109">Surface Pro 7</span></span>
- <span data-ttu-id="ec2e6-110">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="ec2e6-110">Surface Laptop 3</span></span>
- <span data-ttu-id="ec2e6-111">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="ec2e6-111">Surface Pro 6</span></span>
- <span data-ttu-id="ec2e6-112">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="ec2e6-112">Surface Laptop 2</span></span>
- <span data-ttu-id="ec2e6-113">Surface Go</span><span class="sxs-lookup"><span data-stu-id="ec2e6-113">Surface Go</span></span>
- <span data-ttu-id="ec2e6-114">Surface Go con LTE</span><span class="sxs-lookup"><span data-stu-id="ec2e6-114">Surface Go with LTE</span></span>
- <span data-ttu-id="ec2e6-115">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="ec2e6-115">Surface Book 2</span></span>
- <span data-ttu-id="ec2e6-116">Surface Pro con LTE Advanced (Modello 1807)</span><span class="sxs-lookup"><span data-stu-id="ec2e6-116">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="ec2e6-117">Surface Pro (Modello 1796)</span><span class="sxs-lookup"><span data-stu-id="ec2e6-117">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="ec2e6-118">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="ec2e6-118">Surface Laptop</span></span>
- <span data-ttu-id="ec2e6-119">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="ec2e6-119">Surface Studio</span></span>
- <span data-ttu-id="ec2e6-120">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="ec2e6-120">Surface Studio 2</span></span>
- <span data-ttu-id="ec2e6-121">Surface Book</span><span class="sxs-lookup"><span data-stu-id="ec2e6-121">Surface Book</span></span>
- <span data-ttu-id="ec2e6-122">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="ec2e6-122">Surface Pro 4</span></span>
- <span data-ttu-id="ec2e6-123">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="ec2e6-123">Surface 3 LTE</span></span>
- <span data-ttu-id="ec2e6-124">Surface 3</span><span class="sxs-lookup"><span data-stu-id="ec2e6-124">Surface 3</span></span>
- <span data-ttu-id="ec2e6-125">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="ec2e6-125">Surface Pro 3</span></span>


<span data-ttu-id="ec2e6-126">L'app Surface è un'app Microsoft Store semplice che fornisce il controllo di molte impostazioni e opzioni specifiche di Surface, tra cui:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-126">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="ec2e6-127">Abilitazione o disabilitazione del pulsante Windows nel dispositivo Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-127">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="ec2e6-128">Regolazione della sensibilità di una penna per Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-128">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="ec2e6-129">Personalizzazione delle azioni dei pulsanti della penna per Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-129">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="ec2e6-130">Abilitazione o disabilitazione dei miglioramenti audio di Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-130">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="ec2e6-131">Accesso rapido alla documentazione e alle informazioni di supporto per il dispositivo</span><span class="sxs-lookup"><span data-stu-id="ec2e6-131">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="ec2e6-132">I clienti che Windows Update riceveranno normalmente l'app Surface come parte degli aggiornamenti automatici.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-132">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="ec2e6-133">Tuttavia, se l'organizzazione prepara le immagini per la distribuzione nei dispositivi Surface, potresti voler includere l'app Surface (in precedenza denominata Surface Hub) nel processo di creazione di immagini e distribuzione invece di richiedere agli utenti di ogni singolo dispositivo di scaricare e installare l'app dal Microsoft Store o dal Microsoft Store per le aziende.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-133">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="ec2e6-134">Questo articolo non si applica a Surface Pro X. Per ulteriori informazioni, vedere [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span><span class="sxs-lookup"><span data-stu-id="ec2e6-134">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <a name="surface-app-overview"></a><span data-ttu-id="ec2e6-135">Panoramica dell'app Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-135">Surface app overview</span></span>

<span data-ttu-id="ec2e6-136">L'app Surface è disponibile come download gratuito [da Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span><span class="sxs-lookup"><span data-stu-id="ec2e6-136">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="ec2e6-137">Gli utenti possono scaricarla e installarla dal Microsoft Store, ma se l'organizzazione usa invece Microsoft Store per le aziende, dovrai aggiungerla all'inventario dello Store ed eventualmente includere l'app come parte del processo di distribuzione di Windows.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-137">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="ec2e6-138">Questi processi vengono illustrati in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-138">These processes are discussed throughout this article.</span></span> <span data-ttu-id="ec2e6-139">Per ulteriori informazioni su Microsoft Store per le aziende, [vedere Microsoft Store per le aziende](https://docs.microsoft.com/microsoft-store/) nel TechCenter Windows.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-139">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <a name="add-surface-app-to-a-microsoft-store-for-business-account"></a><span data-ttu-id="ec2e6-140">Aggiungere un'app Surface a un Microsoft Store per le aziende account</span><span class="sxs-lookup"><span data-stu-id="ec2e6-140">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="ec2e6-141">Prima che gli utenti possano installare o distribuire un'app dall'account Microsoft Store per le aziende di una società, le app desiderate devono prima essere rese disponibili e concesse in licenza agli utenti di un'azienda.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-141">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="ec2e6-142">Se non l'hai già fatto, crea un [Microsoft Store per le aziende account](https://www.microsoft.com/business-store).</span><span class="sxs-lookup"><span data-stu-id="ec2e6-142">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="ec2e6-143">Accedere al portale.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-143">Log on to the portal.</span></span> 

3. <span data-ttu-id="ec2e6-144">Abilita licenze offline: fai clic su Gestisci impostazioni di **>Store**e quindi seleziona la casella di controllo Mostra app con licenza offline agli utenti che acquistino nello **Store,** come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-144">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="ec2e6-145">Per altre informazioni sui modelli Microsoft Store per le aziende licenze delle app, vedi [App in Microsoft Store per le aziende e Education.](https://docs.microsoft.com/microsoft-store/)</span><span class="sxs-lookup"><span data-stu-id="ec2e6-145">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span>

   > [!div class="mx-imgBorder"]
   > ![Casella di controllo Mostra le app per le licenze offline](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="ec2e6-147">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-147">Figure 1.</span></span> <span data-ttu-id="ec2e6-148">Abilitare le app per l'uso offline</span><span class="sxs-lookup"><span data-stu-id="ec2e6-148">Enable apps for offline use</span></span>*

4. <span data-ttu-id="ec2e6-149">Aggiungi l'app Surface al tuo account Microsoft Store per le aziende seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-149">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>

    * <span data-ttu-id="ec2e6-150">Fai clic sul menu **Negozio.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-150">Click the **Shop** menu.</span></span>
    
    * <span data-ttu-id="ec2e6-151">Nella casella di ricerca digita **App Surface**e quindi fai clic sull'icona di ricerca.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-151">In the search box, type **Surface app**, and then click the search icon.</span></span>
    
    * <span data-ttu-id="ec2e6-152">Dopo aver presentato l'app Surface nei risultati della ricerca, fai clic sull'icona dell'app.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-152">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    
    * <span data-ttu-id="ec2e6-153">Viene visualizzata una scelta (selezionare **Online** o **Offline),** come illustrato nella figura 2.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-153">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![Seleziona la modalità di licenza offline e aggiungi l'app all'inventario](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *<span data-ttu-id="ec2e6-155">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-155">Figure 2.</span></span> <span data-ttu-id="ec2e6-156">Seleziona la modalità di licenza offline e aggiungi l'app all'inventario</span><span class="sxs-lookup"><span data-stu-id="ec2e6-156">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="ec2e6-157">Fare **clic su Offline** per selezionare la modalità di licenza offline.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-157">Click **Offline** to select the Offline licensing mode.</span></span>
    
    * <span data-ttu-id="ec2e6-158">Fai **clic su Ottieni l'app** per aggiungere l'app al tuo Microsoft Store per le aziende inventario.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-158">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="ec2e6-159">Come illustrato nella figura 3, verrà visualizzata una finestra di dialogo in cui viene richiesto di confermare che le app offline possono essere distribuite tramite uno strumento di gestione o scaricate dalla pagina dell'inventario aziendale nel proprio archivio privato.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-159">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
      > [!div class="mx-imgBorder"]
      > ![<span data-ttu-id="ec2e6-160">Finestra di conferma delle app con licenza offline ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *Figura 3. Riconoscimento delle app con licenza offline*</span><span class="sxs-lookup"><span data-stu-id="ec2e6-160">Offline-licensed app acknowledgement window](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
*Figure 3. Offline-licensed app acknowledgement*</span></span>
      
    * <span data-ttu-id="ec2e6-161">Fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-161">Click **OK**.</span></span>

## <a name="download-surface-app-from-a-microsoft-store-for-business-account"></a><span data-ttu-id="ec2e6-162">Scaricare l'app Surface da un account Microsoft Store per le aziende utente</span><span class="sxs-lookup"><span data-stu-id="ec2e6-162">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="ec2e6-163">Dopo aver aggiunto un'app all'account Microsoft Store per le aziende in modalità offline, puoi scaricare e aggiungere l'app come AppxBundle a una condivisione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-163">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>

1. <span data-ttu-id="ec2e6-164">Accedere all'account Microsoft Store per le aziende all'indirizzo https://businessstore.microsoft.com .</span><span class="sxs-lookup"><span data-stu-id="ec2e6-164">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>

2. <span data-ttu-id="ec2e6-165">Fare **clic su Gestisci >app & software**.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-165">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="ec2e6-166">Viene visualizzato un elenco di tutte le app della tua azienda, inclusa l'app Surface che hai aggiunto nella sezione [Aggiungere l'app Surface a](#add-surface-app-to-a-microsoft-store-for-business-account) un account Microsoft Store per le aziende di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-166">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>

3. <span data-ttu-id="ec2e6-167">In **Azioni**fai clic sui puntini di sospensione (**...**) e quindi fai clic su Scarica per l'uso **offline** per l'app Surface.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-167">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>

4. <span data-ttu-id="ec2e6-168">Selezionare le opzioni **piattaforma** **e** architettura desiderate tra le selezioni disponibili per l'app selezionata, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-168">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Esempio del pacchetto AppxBundle](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *<span data-ttu-id="ec2e6-170">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-170">Figure 4.</span></span> <span data-ttu-id="ec2e6-171">Scaricare il pacchetto AppxBundle per un'app</span><span class="sxs-lookup"><span data-stu-id="ec2e6-171">Download the AppxBundle package for an app</span></span>*
    
5. <span data-ttu-id="ec2e6-172">Fare clic **su Scarica**.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-172">Click **Download**.</span></span> <span data-ttu-id="ec2e6-173">Il pacchetto AppxBundle verrà scaricato.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-173">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="ec2e6-174">Assicurati di prendere nota del percorso del file scaricato perché sarà necessario più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-174">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>

6. <span data-ttu-id="ec2e6-175">Fare clic **sull'opzione Licenza codificata** o **Licenza non codificata.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-175">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="ec2e6-176">Usa l'opzione Licenza codificata con strumenti di gestione come Microsoft Endpoint Configuration Manager o quando usi progettazione Windows per creare un pacchetto di provisioning.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-176">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="ec2e6-177">Seleziona l'opzione Licenza non codificata quando usi Gestione e manutenzione immagini distribuzione o soluzioni di distribuzione basate sulla creazione di immagini, incluso Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="ec2e6-177">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>

7. <span data-ttu-id="ec2e6-178">Fai **clic su** Genera per generare e scaricare la licenza per l'app.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-178">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="ec2e6-179">Assicurati di prendere nota del percorso del file di licenza perché sarà necessario più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-179">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="ec2e6-180">Quando scaririchi un'app per l'uso offline, ad esempio l'app Surface, potresti notare una sezione nella parte inferiore della pagina con l'etichetta **Framework obbligatori.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-180">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="ec2e6-181">I computer di destinazione devono avere i framework installati per l'esecuzione dell'app, quindi potrebbe essere necessario ripetere il processo di download per ognuno dei framework necessari per l'architettura (x86 o x64) e includerli anche come parte della distribuzione di Windows illustrata più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-181">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="ec2e6-182">La figura 5 mostra i framework necessari per l'app Surface.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-182">Figure 5 shows the required frameworks for the Surface app.</span></span>

> [!div class="mx-imgBorder"]
> ![Framework necessari per l'app Surface](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*<span data-ttu-id="ec2e6-184">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-184">Figure 5.</span></span> <span data-ttu-id="ec2e6-185">Framework necessari per l'app Surface</span><span class="sxs-lookup"><span data-stu-id="ec2e6-185">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="ec2e6-186">I numeri di versione dell'app Surface e i framework necessari cambieranno quando le app vengono aggiornate.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-186">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="ec2e6-187">Controlla la versione più recente dell'app Surface e ogni framework in Microsoft Store per le aziende.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-187">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="ec2e6-188">Usa sempre l'app Surface e le versioni consigliate del framework come indicato da Microsoft Store per le aziende.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-188">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="ec2e6-189">L'uso di framework obsoleti o di versioni non corrette può causare errori o arresti anomali dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-189">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="ec2e6-190">Per scaricare i framework necessari per l'app Surface, segui questi passaggi:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-190">To download the required frameworks for the Surface app, follow these steps:</span></span>

1. <span data-ttu-id="ec2e6-191">Fare clic **sul** pulsante Download in **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-191">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="ec2e6-192">Verrà scaricato il Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe. File Appx nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-192">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

2. <span data-ttu-id="ec2e6-193">Fare **clic** sul pulsante Download **in Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-193">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="ec2e6-194">In questo modo il file Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx viene scaricato nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-194">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="ec2e6-195">Solo la versione a 64 bit (x64) di ogni framework è necessaria per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-195">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="ec2e6-196">I dispositivi Surface sono dispositivi UEFI nativi a 64 bit e non sono compatibili con le versioni a 32 bit (x86) di Windows che richiedono framework a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-196">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <a name="install-surface-app-on-your-computer-with-powershell"></a><span data-ttu-id="ec2e6-197">Installare l'app Surface nel computer con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec2e6-197">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="ec2e6-198">La procedura seguente esegue il provisioning dell'app Surface nel computer e la rende disponibile per tutti gli account utente creati nel computer in seguito.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-198">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>

1. <span data-ttu-id="ec2e6-199">Usando la procedura descritta nella sezione Come scaricare [l'app Surface](#download-surface-app-from-a-microsoft-store-for-business-account) da un account Microsoft Store per le aziende di questo articolo, scarica il file di licenza e AppxBundle dell'app Surface.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-199">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="ec2e6-200">Avvia una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-200">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="ec2e6-201">Se non esegui PowerShell come amministratore, la sessione non dirà le autorizzazioni necessarie per installare l'app.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-201">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="ec2e6-202">Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-202">In the elevated PowerShell session, copy and paste the following command:</span></span>

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="ec2e6-203">Dove `<DownloadPath>` è la cartella in cui hai scaricato appxBundle e il file di licenza dall'account Microsoft Store per le aziende account.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-203">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="ec2e6-204">Ad esempio, se i file sono stati scaricati in c:\Temp, il comando eseguito è:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-204">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. <span data-ttu-id="ec2e6-205">L'app Surface sarà ora disponibile nel computer Windows corrente.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-205">The Surface app will now be available on your current Windows computer.</span></span> 

   <span data-ttu-id="ec2e6-206">Prima che l'app Surface funzioni nel computer in cui è stato eseguito il provisioning, devi anche eseguire il provisioning dei framework descritti in precedenza in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-206">Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article.</span></span> <span data-ttu-id="ec2e6-207">Per eseguire il provisioning di questi framework, usa la procedura seguente nella sessione di PowerShell con privilegi elevati usata per eseguire il provisioning dell'app Surface.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-207">To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.</span></span>

5. <span data-ttu-id="ec2e6-208">Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-208">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. <span data-ttu-id="ec2e6-209">Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-209">In the elevated PowerShell session, copy and paste the following command:</span></span>

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <a name="install-surface-app-with-mdt"></a><span data-ttu-id="ec2e6-210">Installare l'app Surface con MDT</span><span class="sxs-lookup"><span data-stu-id="ec2e6-210">Install Surface app with MDT</span></span>
<span data-ttu-id="ec2e6-211">La procedura seguente usa MDT per automatizzare l'installazione dell'app Surface al momento della distribuzione.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-211">The following procedure uses MDT to automate installation of the Surface app at the time of deployment.</span></span> <span data-ttu-id="ec2e6-212">Il provisioning dell'applicazione viene effettuato automaticamente da MDT durante la distribuzione e quindi puoi usare questo processo con le immagini esistenti.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-212">The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images.</span></span> <span data-ttu-id="ec2e6-213">Questo è il processo consigliato per distribuire l'app Surface come parte di una distribuzione di Windows nei dispositivi Surface perché non riduce la compatibilità tra piattaforme dell'Windows immagine.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-213">This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.</span></span>

1. <span data-ttu-id="ec2e6-214">Usando la procedura descritta [in precedenza in questo articolo,](#download-surface-app-from-a-microsoft-store-for-business-account)scarica l'app Surface AppxBundle e il file di licenza.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-214">Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file.</span></span> 

2. <span data-ttu-id="ec2e6-215">Usando la Creazione guidata nuova applicazione in MDT Deployment Workbench, importare i file scaricati come nuova **applicazione con file di origine.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-215">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="ec2e6-216">Nella pagina **Dettagli comando** della Creazione guidata nuova applicazione specificare la **directory** di lavoro predefinita e per **Il** comando specificare il nome file di AppxBundle, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-216">On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:</span></span>

   * <span data-ttu-id="ec2e6-217">Comando:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-217">Command:</span></span>
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * <span data-ttu-id="ec2e6-218">Directory di lavoro: %DEPLOYROOT%\Applications\SurfaceApp</span><span class="sxs-lookup"><span data-stu-id="ec2e6-218">Working Directory: %DEPLOYROOT%\Applications\SurfaceApp</span></span>

<span data-ttu-id="ec2e6-219">Per il funzionamento dell'app Surface nel computer di destinazione, saranno necessari anche i framework descritti in precedenza in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-219">For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article.</span></span> <span data-ttu-id="ec2e6-220">Usa la procedura seguente per importare i framework necessari per l'app Surface in MDT e configurarli come dipendenze.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-220">Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.</span></span>

1. <span data-ttu-id="ec2e6-221">Usando la procedura descritta in precedenza in questo articolo, scaricare i file del framework.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-221">Using the procedure described earlier in this article, download the framework files.</span></span> <span data-ttu-id="ec2e6-222">Archiviare ogni framework in una cartella separata.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-222">Store each framework in a separate folder.</span></span>

2. <span data-ttu-id="ec2e6-223">Usando la Creazione guidata nuova applicazione in MDT Deployment Workbench, importare i file scaricati come nuova **applicazione con file di origine.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-223">Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.</span></span>

3. <span data-ttu-id="ec2e6-224">Nella pagina **Dettagli comando** digitare il nome file di ogni applicazione scaricata nel campo **Comando** e nella directory di lavoro predefinita.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-224">On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.</span></span>

<span data-ttu-id="ec2e6-225">Per configurare i framework come dipendenze dell'app Surface, usa questo processo:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-225">To configure the frameworks as dependencies of the Surface app, use this process:</span></span>

1. <span data-ttu-id="ec2e6-226">Apri le proprietà dell'app Surface in MDT Deployment Workbench.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-226">Open the properties of the Surface app in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="ec2e6-227">Fare clic **sulla scheda** Dipendenze e quindi su **Aggiungi.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-227">Click the **Dependencies** tab, and then click **Add**.</span></span>

3. <span data-ttu-id="ec2e6-228">Selezionare la casella di controllo per ogni framework utilizzando il nome specificato nella Creazione guidata nuova applicazione.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-228">Select the check box for each framework using the name you provided in the New Application Wizard.</span></span>

<span data-ttu-id="ec2e6-229">Dopo l'importazione, l'app Surface sarà disponibile per la selezione nel passaggio **Applicazioni** della Windows distribuzione guidata.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-229">After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard.</span></span> <span data-ttu-id="ec2e6-230">Puoi anche installare l'applicazione automaticamente specificandola nella sequenza di attività di distribuzione seguendo questo processo:</span><span class="sxs-lookup"><span data-stu-id="ec2e6-230">You can also install the application automatically by specifying the application in the deployment task sequence by following this process:</span></span>

1. <span data-ttu-id="ec2e6-231">Apri la sequenza di attività di distribuzione in MDT Deployment Workbench.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-231">Open your deployment task sequence in the MDT Deployment Workbench.</span></span>

2. <span data-ttu-id="ec2e6-232">Aggiungi una nuova attività **Install Application** nella sezione **State Restore** della distribuzione.</span><span class="sxs-lookup"><span data-stu-id="ec2e6-232">Add a new **Install Application** task in the **State Restore** section of deployment.</span></span>

3. <span data-ttu-id="ec2e6-233">Seleziona **Installa una singola applicazione** e specifica **l'app Surface** come applicazione da **installare.**</span><span class="sxs-lookup"><span data-stu-id="ec2e6-233">Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.</span></span>

<span data-ttu-id="ec2e6-234">Per ulteriori informazioni sull'inclusione di app nelle distribuzioni Windows, vedere [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).</span><span class="sxs-lookup"><span data-stu-id="ec2e6-234">For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).</span></span>

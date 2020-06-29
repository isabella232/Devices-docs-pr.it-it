---
title: Distribuire l'app Surface con Microsoft Store per le aziende o Microsoft Store per l'istruzione (Surface)
description: Scopri come aggiungere e scaricare app Surface con Microsoft Store per le aziende o Microsoft Store per l'istruzione, oltre a installare l'app Surface con PowerShell e MDT.
keywords: app Surface, app, distribuzione, Personalizza
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
ms.openlocfilehash: e25e146de49110dca1fea797f9630d9fa2d953e3
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832859"
---
# <span data-ttu-id="2f76a-104">Distribuire l'app Surface con Microsoft Store per le aziende e l'istruzione</span><span class="sxs-lookup"><span data-stu-id="2f76a-104">Deploy Surface app with Microsoft Store for Business and Education</span></span>

**<span data-ttu-id="2f76a-105">Ambito di applicazione</span><span class="sxs-lookup"><span data-stu-id="2f76a-105">Applies to</span></span>**

- <span data-ttu-id="2f76a-106">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="2f76a-106">Surface Pro 7</span></span>
- <span data-ttu-id="2f76a-107">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="2f76a-107">Surface Laptop 3</span></span>
- <span data-ttu-id="2f76a-108">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="2f76a-108">Surface Pro 6</span></span>
- <span data-ttu-id="2f76a-109">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="2f76a-109">Surface Laptop 2</span></span>
- <span data-ttu-id="2f76a-110">Surface Go</span><span class="sxs-lookup"><span data-stu-id="2f76a-110">Surface Go</span></span>
- <span data-ttu-id="2f76a-111">Surface go con LTE</span><span class="sxs-lookup"><span data-stu-id="2f76a-111">Surface Go with LTE</span></span>
- <span data-ttu-id="2f76a-112">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="2f76a-112">Surface Book 2</span></span>
- <span data-ttu-id="2f76a-113">Surface Pro con LTE Advanced (Modello 1807)</span><span class="sxs-lookup"><span data-stu-id="2f76a-113">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="2f76a-114">Surface Pro (Modello 1796)</span><span class="sxs-lookup"><span data-stu-id="2f76a-114">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="2f76a-115">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="2f76a-115">Surface Laptop</span></span>
- <span data-ttu-id="2f76a-116">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="2f76a-116">Surface Studio</span></span>
- <span data-ttu-id="2f76a-117">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="2f76a-117">Surface Studio 2</span></span>
- <span data-ttu-id="2f76a-118">Surface Book</span><span class="sxs-lookup"><span data-stu-id="2f76a-118">Surface Book</span></span>
- <span data-ttu-id="2f76a-119">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="2f76a-119">Surface Pro 4</span></span>
- <span data-ttu-id="2f76a-120">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="2f76a-120">Surface 3 LTE</span></span>
- <span data-ttu-id="2f76a-121">Surface 3</span><span class="sxs-lookup"><span data-stu-id="2f76a-121">Surface 3</span></span>
- <span data-ttu-id="2f76a-122">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="2f76a-122">Surface Pro 3</span></span>


<span data-ttu-id="2f76a-123">L'app Surface è un'app Microsoft Store leggera che offre il controllo di molte opzioni e impostazioni specifiche della superficie, tra cui:</span><span class="sxs-lookup"><span data-stu-id="2f76a-123">The Surface app is a lightweight Microsoft Store app that provides control of many Surface-specific settings and options, including:</span></span> 

* <span data-ttu-id="2f76a-124">Abilitazione o disabilitazione del pulsante Windows nel dispositivo Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-124">Enable or disable the Windows button on the Surface device</span></span> 

* <span data-ttu-id="2f76a-125">Regolazione della sensibilità di una penna per Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-125">Adjust the sensitivity of a Surface Pen</span></span> 

* <span data-ttu-id="2f76a-126">Personalizzazione delle azioni dei pulsanti della penna per Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-126">Customize Surface Pen button actions</span></span> 

* <span data-ttu-id="2f76a-127">Abilitazione o disabilitazione dei miglioramenti audio di Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-127">Enable or disable Surface audio enhancements</span></span> 

* <span data-ttu-id="2f76a-128">Accesso rapido per supportare la documentazione e le informazioni per il dispositivo</span><span class="sxs-lookup"><span data-stu-id="2f76a-128">Quick access to support documentation and information for your device</span></span>

<span data-ttu-id="2f76a-129">I clienti che usano Windows Update riceveranno in genere l'app Surface come parte degli aggiornamenti automatici.</span><span class="sxs-lookup"><span data-stu-id="2f76a-129">Customers using Windows Update will ordinarily receive Surface app as part of automatic updates.</span></span> <span data-ttu-id="2f76a-130">Tuttavia, se l'organizzazione sta preparando immagini per la distribuzione ai dispositivi Surface, potresti voler includere l'app Surface (in precedenza chiamato Surface Hub) nel processo di imaging e distribuzione invece di richiedere agli utenti di ogni singolo dispositivo di scaricare e installare l'app da Microsoft Store o da Microsoft Store for business.</span><span class="sxs-lookup"><span data-stu-id="2f76a-130">But if your organization is preparing images for deployment to your Surface devices, you may want to include the Surface app (formerly called the Surface Hub) in your imaging and deployment process instead of requiring users of each individual device to download and install the app from the Microsoft Store or your Microsoft Store for Business.</span></span> 

> [!NOTE]
> <span data-ttu-id="2f76a-131">Questo articolo non si applica a Surface Pro X. Per altre informazioni, vedere [distribuzione, gestione e manutenzione di Surface Pro X](surface-pro-arm-app-management.md)</span><span class="sxs-lookup"><span data-stu-id="2f76a-131">This article does not apply to Surface Pro X. For more information, refer to [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)</span></span>

## <span data-ttu-id="2f76a-132">Panoramica dell'app Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-132">Surface app overview</span></span>

<span data-ttu-id="2f76a-133">L'app Surface è disponibile come download gratuito da [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span><span class="sxs-lookup"><span data-stu-id="2f76a-133">The Surface app is available as a free download from the [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P).</span></span> <span data-ttu-id="2f76a-134">Gli utenti possono scaricarlo e installarlo da Microsoft Store, ma se l'organizzazione usa Microsoft Store per le aziende, sarà necessario aggiungerla all'inventario dell'archivio e possibilmente includere l'app nell'ambito del processo di distribuzione di Windows.</span><span class="sxs-lookup"><span data-stu-id="2f76a-134">Users can download and install it from the Microsoft Store, but if your organization uses Microsoft Store for Business instead, you will need to add it to your store’s inventory and possibly include the app as part of your Windows deployment process.</span></span> <span data-ttu-id="2f76a-135">Questi processi vengono discussi in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="2f76a-135">These processes are discussed throughout this article.</span></span> <span data-ttu-id="2f76a-136">Per altre informazioni su Microsoft Store for business, vedere [Microsoft Store for business](https://docs.microsoft.com/microsoft-store/) in Windows TechCenter.</span><span class="sxs-lookup"><span data-stu-id="2f76a-136">For more information about Microsoft Store for Business, see [Microsoft Store for Business](https://docs.microsoft.com/microsoft-store/) in the Windows TechCenter.</span></span> 

## <span data-ttu-id="2f76a-137">Aggiungere un'app Surface a un account di Microsoft Store per le aziende</span><span class="sxs-lookup"><span data-stu-id="2f76a-137">Add Surface app to a Microsoft Store for Business account</span></span> 

<span data-ttu-id="2f76a-138">Prima che gli utenti possano installare o distribuire un'app dall'account Microsoft Store for business di una società, l'app desiderata deve prima essere resa disponibile e concessa in licenza agli utenti di un'azienda.</span><span class="sxs-lookup"><span data-stu-id="2f76a-138">Before users can install or deploy an app from a company’s Microsoft Store for Business account, the desired app(s) must first be made available and licensed to the users of a business.</span></span> 

1. <span data-ttu-id="2f76a-139">Se non è già stato fatto, creare un [account di Microsoft Store per le aziende](https://www.microsoft.com/business-store).</span><span class="sxs-lookup"><span data-stu-id="2f76a-139">If you have not already done so, create a [Microsoft Store for Business account](https://www.microsoft.com/business-store).</span></span> 

2. <span data-ttu-id="2f76a-140">Accedere al portale.</span><span class="sxs-lookup"><span data-stu-id="2f76a-140">Log on to the portal.</span></span> 

3. <span data-ttu-id="2f76a-141">Abilitare le licenze offline: fare clic su **Gestisci->impostazioni dello Store**e quindi selezionare la casella **di controllo Mostra app con licenza offline per gli acquisti di persone nello Store** , come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="2f76a-141">Enable offline licensing: click **Manage->Store settings**, and then select the **Show offline licensed apps to people shopping in the store** checkbox, as shown in Figure 1.</span></span> <span data-ttu-id="2f76a-142">Per altre informazioni sui modelli di licenze per le app Microsoft Store per le aziende, vedere [app in Microsoft Store per le aziende e l'istruzione](https://docs.microsoft.com/microsoft-store/).</span><span class="sxs-lookup"><span data-stu-id="2f76a-142">For more information about Microsoft Store for Business app licensing models, see [Apps in Microsoft Store for Business and Education](https://docs.microsoft.com/microsoft-store/).</span></span><br/> <br/>
   ![Casella di controllo Mostra app licenze offline](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *<span data-ttu-id="2f76a-144">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="2f76a-144">Figure 1.</span></span> <span data-ttu-id="2f76a-145">Abilitare le app per l'uso offline</span><span class="sxs-lookup"><span data-stu-id="2f76a-145">Enable apps for offline use</span></span>*

4. <span data-ttu-id="2f76a-146">Aggiungere l'app Surface al proprio account di Microsoft Store per le aziende seguendo questa procedura:</span><span class="sxs-lookup"><span data-stu-id="2f76a-146">Add Surface app to your Microsoft Store for Business account by following this procedure:</span></span>
    * <span data-ttu-id="2f76a-147">Fare clic sul menu **Shop** .</span><span class="sxs-lookup"><span data-stu-id="2f76a-147">Click the **Shop** menu.</span></span>
    * <span data-ttu-id="2f76a-148">Nella casella di ricerca digitare **app Surface**e quindi fare clic sull'icona di ricerca.</span><span class="sxs-lookup"><span data-stu-id="2f76a-148">In the search box, type **Surface app**, and then click the search icon.</span></span>
    * <span data-ttu-id="2f76a-149">Dopo aver presentato l'app Surface nei risultati della ricerca, fare clic sull'icona dell'app.</span><span class="sxs-lookup"><span data-stu-id="2f76a-149">After the Surface app is presented in the search results, click the app’s icon.</span></span>
    * <span data-ttu-id="2f76a-150">Viene visualizzata una scelta (selezionare **online** o **offline**), come illustrato nella figura 2.</span><span class="sxs-lookup"><span data-stu-id="2f76a-150">You are presented with a choice (select **Online** or **Offline**), as shown in Figure 2.</span></span><br/><br/>
    
    ![Selezionare la modalità di gestione licenze offline e aggiungere l'app all'inventario](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")
    
    *<span data-ttu-id="2f76a-152">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="2f76a-152">Figure 2.</span></span> <span data-ttu-id="2f76a-153">Selezionare la modalità di gestione licenze offline e aggiungere l'app all'inventario</span><span class="sxs-lookup"><span data-stu-id="2f76a-153">Select the Offline licensing mode and add the app to your inventory</span></span>*
    
    * <span data-ttu-id="2f76a-154">Fare clic su **offline** per selezionare la modalità di gestione licenze offline.</span><span class="sxs-lookup"><span data-stu-id="2f76a-154">Click **Offline** to select the Offline licensing mode.</span></span>
    * <span data-ttu-id="2f76a-155">Fai clic su **Ottieni l'app** per aggiungere l'app all'inventario di Microsoft Store per le aziende.</span><span class="sxs-lookup"><span data-stu-id="2f76a-155">Click **Get the app** to add the app to your Microsoft Store for Business inventory.</span></span> <span data-ttu-id="2f76a-156">Come illustrato nella figura 3, viene visualizzata una finestra di dialogo in cui viene chiesto di confermare che le app offline possono essere distribuite tramite uno strumento di gestione o scaricate dalla pagina dell'inventario della società nel proprio archivio privato.</span><span class="sxs-lookup"><span data-stu-id="2f76a-156">As shown in Figure 3, you’ll see a dialog box that prompts you to acknowledge that offline apps can be deployed using a management tool or downloaded from the company’s inventory page in their private store.</span></span>
    
    ![Finestra di riconoscimento app con licenza offline](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
    
    *<span data-ttu-id="2f76a-158">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="2f76a-158">Figure 3.</span></span> <span data-ttu-id="2f76a-159">Riconoscimento delle app con licenza offline</span><span class="sxs-lookup"><span data-stu-id="2f76a-159">Offline-licensed app acknowledgement</span></span>*
    * <span data-ttu-id="2f76a-160">Fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-160">Click **OK**.</span></span>

## <span data-ttu-id="2f76a-161">Scaricare l'app Surface da un account di Microsoft Store per le aziende</span><span class="sxs-lookup"><span data-stu-id="2f76a-161">Download Surface app from a Microsoft Store for Business account</span></span>
<span data-ttu-id="2f76a-162">Dopo aver aggiunto un'app all'account Microsoft Store for business in modalità offline, è possibile scaricare e aggiungere l'app come AppxBundle a una condivisione di distribuzione.</span><span class="sxs-lookup"><span data-stu-id="2f76a-162">After you add an app to the Microsoft Store for Business account in Offline mode, you can download and add the app as an AppxBundle to a deployment share.</span></span>
1. <span data-ttu-id="2f76a-163">Accedere all'account Microsoft Store for business all'indirizzo https://businessstore.microsoft.com .</span><span class="sxs-lookup"><span data-stu-id="2f76a-163">Log on to the Microsoft Store for Business account at https://businessstore.microsoft.com.</span></span>
2. <span data-ttu-id="2f76a-164">Fare clic su **Gestisci->app & software**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-164">Click **Manage->Apps & software**.</span></span> <span data-ttu-id="2f76a-165">Viene visualizzato un elenco di tutte le app della tua azienda, inclusa l'app Surface aggiunta nell' [app Aggiungi superficie a una sezione dell'account di Microsoft Store for business](#add-surface-app-to-a-microsoft-store-for-business-account) di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="2f76a-165">A list of all of your company’s apps is displayed, including the Surface app you added in the [Add Surface app to a Microsoft Store for Business account](#add-surface-app-to-a-microsoft-store-for-business-account) section of this article.</span></span>
3. <span data-ttu-id="2f76a-166">In **azioni**fare clic sui puntini di sospensione (**...**) e quindi su **Scarica per l'uso offline** per l'app Surface.</span><span class="sxs-lookup"><span data-stu-id="2f76a-166">Under **Actions**, click the ellipsis (**…**), and then click **Download for offline use** for the Surface app.</span></span>
4. <span data-ttu-id="2f76a-167">Selezionare le opzioni della **piattaforma** e dell' **architettura** desiderate dalle selezioni disponibili per l'app selezionata, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="2f76a-167">Select the desired **Platform** and **Architecture** options from the available selections for the selected app, as shown in Figure 4.</span></span>

    ![Esempio di pacchetto AppxBundle](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")

    *<span data-ttu-id="2f76a-169">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="2f76a-169">Figure 4.</span></span> <span data-ttu-id="2f76a-170">Scaricare il pacchetto AppxBundle per un'app</span><span class="sxs-lookup"><span data-stu-id="2f76a-170">Download the AppxBundle package for an app</span></span>*
5. <span data-ttu-id="2f76a-171">Fare clic su **Scarica**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-171">Click **Download**.</span></span> <span data-ttu-id="2f76a-172">Verrà scaricato il pacchetto AppxBundle.</span><span class="sxs-lookup"><span data-stu-id="2f76a-172">The AppxBundle package will be downloaded.</span></span> <span data-ttu-id="2f76a-173">Verificare di aver notato il percorso del file scaricato, perché sarà necessario più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="2f76a-173">Make sure you note the path of the downloaded file because you’ll need that later in this article.</span></span>
6. <span data-ttu-id="2f76a-174">Fare clic sull'opzione **licenza codificata** o **licenza non codificata** .</span><span class="sxs-lookup"><span data-stu-id="2f76a-174">Click either the **Encoded license** or **Unencoded license** option.</span></span> <span data-ttu-id="2f76a-175">Usa l'opzione di licenza codificata con strumenti di gestione come Microsoft endpoint Configuration Manager o quando usi Windows Configuration designer per creare un pacchetto di provisioning.</span><span class="sxs-lookup"><span data-stu-id="2f76a-175">Use the Encoded license option with management tools like Microsoft Endpoint Configuration Manager or when you use Windows Configuration Designer to create a provisioning package.</span></span> <span data-ttu-id="2f76a-176">Selezionare l'opzione di licenza non codificata quando si usano le soluzioni di gestione e manutenzione immagini distribuzione o distributive basate sull'imaging, incluso Microsoft Deployment Toolkit (MDT).</span><span class="sxs-lookup"><span data-stu-id="2f76a-176">Select the Unencoded license option when you use Deployment Image Servicing and Management (DISM) or deployment solutions based on imaging, including the Microsoft Deployment Toolkit (MDT).</span></span>
7. <span data-ttu-id="2f76a-177">Fare clic su **genera** per generare e scaricare la licenza per l'app.</span><span class="sxs-lookup"><span data-stu-id="2f76a-177">Click **Generate** to generate and download the license for the app.</span></span> <span data-ttu-id="2f76a-178">Verificare di aver notato il percorso del file di licenza, perché sarà necessario più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="2f76a-178">Make sure you note the path of the license file because you’ll need that later in this article.</span></span>

>[!NOTE]
><span data-ttu-id="2f76a-179">Quando scarichi un'app per l'uso offline, come l'app Surface, potresti notare una sezione nella parte inferiore della pagina denominata **Framework obbligatori**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-179">When you download an app for offline use, such as the Surface app, you may notice a section at the bottom of the page labeled **Required frameworks**.</span></span> <span data-ttu-id="2f76a-180">I computer di destinazione devono avere i Framework installati per l'esecuzione dell'app, quindi potrebbe essere necessario ripetere il processo di download per ogni Framework necessario per l'architettura (x86 o x64) e includerli anche come parte della distribuzione di Windows descritta più avanti in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="2f76a-180">Your target computers must have the frameworks installed for the app to run, so you may need to repeat the download process for each of the required frameworks for your architecture (either x86 or x64) and also include them as part of your Windows deployment discussed later in this article.</span></span>

<span data-ttu-id="2f76a-181">La figura 5 Mostra i Framework necessari per l'app Surface.</span><span class="sxs-lookup"><span data-stu-id="2f76a-181">Figure 5 shows the required frameworks for the Surface app.</span></span>

![Framework necessari per l'app Surface](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")

*<span data-ttu-id="2f76a-183">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="2f76a-183">Figure 5.</span></span> <span data-ttu-id="2f76a-184">Framework necessari per l'app Surface</span><span class="sxs-lookup"><span data-stu-id="2f76a-184">Required frameworks for the Surface app</span></span>*

>[!NOTE]
><span data-ttu-id="2f76a-185">I numeri di versione dell'app Surface e dei Framework obbligatori cambieranno Man mano che le app verranno aggiornate.</span><span class="sxs-lookup"><span data-stu-id="2f76a-185">The version numbers of the Surface app and required frameworks will change as the apps are updated.</span></span> <span data-ttu-id="2f76a-186">Controlla l'ultima versione di Surface app e ogni Framework in Microsoft Store for business.</span><span class="sxs-lookup"><span data-stu-id="2f76a-186">Check for the latest version of Surface app and each framework in Microsoft Store for Business.</span></span> <span data-ttu-id="2f76a-187">Usa sempre l'app Surface e le versioni di Framework consigliate fornite da Microsoft Store for business.</span><span class="sxs-lookup"><span data-stu-id="2f76a-187">Always use the Surface app and recommended framework versions as provided by Microsoft Store for Business.</span></span> <span data-ttu-id="2f76a-188">L'uso di Framework obsoleti o di versioni non corrette può causare errori o arresti anomali dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="2f76a-188">Using outdated frameworks or the incorrect versions may result in errors or application crashes.</span></span>

<span data-ttu-id="2f76a-189">Per scaricare i Framework necessari per l'app Surface, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="2f76a-189">To download the required frameworks for the Surface app, follow these steps:</span></span>
1. <span data-ttu-id="2f76a-190">Fare clic sul pulsante **Scarica** in **Microsoft. VCLibs. 140.00 _ 14.0.23816.0_x64__8wekyb3d8bbwe**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-190">Click the **Download** button under **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="2f76a-191">Questo Scarica il Microsoft. VCLibs. 140.00 _ 14.0.23816.0_x64__8wekyb3d8bbwe. Appx file nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="2f76a-191">This downloads the Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>
2. <span data-ttu-id="2f76a-192">Fare clic sul pulsante **Scarica** in **Microsoft. NET. native. Runtime. 1.1 _ 1.1.23406.0_x64__8wekyb3d8bbwe**.</span><span class="sxs-lookup"><span data-stu-id="2f76a-192">Click the **Download** button under **Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**.</span></span> <span data-ttu-id="2f76a-193">Questo Scarica il file Microsoft. NET. native. Runtime. 1.1 _ 1.1.23406.0_x64__8wekyb3d8bbwe. appx nella cartella specificata.</span><span class="sxs-lookup"><span data-stu-id="2f76a-193">This downloads the Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx file to your specified folder.</span></span>

>[!NOTE]
><span data-ttu-id="2f76a-194">Solo la versione a 64 bit (x64) di ogni Framework è necessaria per i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="2f76a-194">Only the 64-bit (x64) version of each framework is required for Surface devices.</span></span> <span data-ttu-id="2f76a-195">I dispositivi Surface sono dispositivi UEFI a 64 bit nativi e non sono compatibili con le versioni di Windows a 32 bit (x86) che richiedono Framework a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="2f76a-195">Surface devices are native 64-bit UEFI devices and are not compatible with 32-bit (x86) versions of Windows that would require 32-bit frameworks.</span></span> 

## <span data-ttu-id="2f76a-196">Installare l'app Surface nel computer con PowerShell</span><span class="sxs-lookup"><span data-stu-id="2f76a-196">Install Surface app on your computer with PowerShell</span></span>
<span data-ttu-id="2f76a-197">La procedura seguente riferisce l'app Surface nel computer e la rende disponibile per tutti gli account utente creati nel computer in seguito.</span><span class="sxs-lookup"><span data-stu-id="2f76a-197">The following procedure provisions the Surface app onto your computer and makes it available for any user accounts created on the computer afterwards.</span></span>
1. <span data-ttu-id="2f76a-198">Usando la procedura descritta nell' [app come scaricare la superficie da una sezione di un account di Microsoft Store per le aziende](#download-surface-app-from-a-microsoft-store-for-business-account) di questo articolo, Scarica l'app Surface AppxBundle e il file di licenza.</span><span class="sxs-lookup"><span data-stu-id="2f76a-198">Using the procedure described in the [How to download Surface app from a Microsoft Store for Business account](#download-surface-app-from-a-microsoft-store-for-business-account) section of this article, download the Surface app AppxBundle and license file.</span></span> 
2. <span data-ttu-id="2f76a-199">Avvia una sessione di PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="2f76a-199">Begin an elevated PowerShell session.</span></span>

    >[!NOTE]
    ><span data-ttu-id="2f76a-200">Se PowerShell non viene eseguito come amministratore, la sessione non avrà le autorizzazioni necessarie per installare l'app.</span><span class="sxs-lookup"><span data-stu-id="2f76a-200">If you don’t run PowerShell as an Administrator, the session won’t have the required permissions to install the app.</span></span>
    
3. <span data-ttu-id="2f76a-201">Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="2f76a-201">In the elevated PowerShell session, copy and paste the following command:</span></span>
    ```
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    <span data-ttu-id="2f76a-202">Dove si `<DownloadPath>` trova la cartella in cui è stato scaricato il file di licenza e AppxBundle dall'account di Microsoft Store per le aziende.</span><span class="sxs-lookup"><span data-stu-id="2f76a-202">Where `<DownloadPath>` is the folder where you downloaded the AppxBundle and license file from the Microsoft Store for Business account.</span></span>

    <span data-ttu-id="2f76a-203">Se ad esempio sono stati scaricati i file in c:\Temp, il comando eseguito è:</span><span class="sxs-lookup"><span data-stu-id="2f76a-203">For example, if you downloaded the files to c:\Temp, the command you run is:</span></span>
    ````
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. The Surface app will now be available on your current Windows computer. 

Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article. To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.

5. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
6. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## Install Surface app with MDT
The following procedure uses MDT to automate installation of the Surface app at the time of deployment. The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images. This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.
1. Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file. 
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:

   * Command:
     ```
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
   * Working Directory: %DEPLOYROOT%\Applications\SurfaceApp

For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article. Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.
1. Using the procedure described earlier in this article, download the framework files. Store each framework in a separate folder.
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.

To configure the frameworks as dependencies of the Surface app, use this process:
1. Open the properties of the Surface app in the MDT Deployment Workbench.
2. Click the **Dependencies** tab, and then click **Add**.
3. Select the check box for each framework using the name you provided in the New Application Wizard.

After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard. You can also install the application automatically by specifying the application in the deployment task sequence by following this process:
1. Open your deployment task sequence in the MDT Deployment Workbench.
2. Add a new **Install Application** task in the **State Restore** section of deployment.
3. Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.

For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).

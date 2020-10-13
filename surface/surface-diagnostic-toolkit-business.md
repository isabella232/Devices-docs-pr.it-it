---
title: Implementare Toolkit di diagnostica per Surface per le aziende
description: Questo argomento spiega come usare Surface Diagnostic Toolkit for business.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/12/2020
ms.reviewer: hachidan
manager: laurawi
audience: itpro
ms.openlocfilehash: 1f2661811516507abd432dba602cf8ce81e6dbb3
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114664"
---
# <span data-ttu-id="4d651-103">Implementare Toolkit di diagnostica per Surface per le aziende</span><span class="sxs-lookup"><span data-stu-id="4d651-103">Deploy Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="4d651-104">Microsoft Surface Diagnostic Toolkit for business (SDT) consente agli amministratori IT di analizzare rapidamente, risolvere i problemi relativi a hardware, software e firmware con i dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="4d651-104">The Microsoft Surface Diagnostic Toolkit for Business (SDT) enables IT administrators to quickly investigate, troubleshoot, and resolve hardware, software, and firmware issues with Surface devices.</span></span> <span data-ttu-id="4d651-105">È possibile eseguire una serie di test diagnostici e riparazioni software oltre ad ottenere informazioni dettagliate sulla salute dei dispositivi e indicazioni per la risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="4d651-105">You can run a range of diagnostic tests and software repairs in addition to obtaining device health insights and guidance for resolving issues.</span></span> 

<span data-ttu-id="4d651-106">In particolare, SDT for business consente di:</span><span class="sxs-lookup"><span data-stu-id="4d651-106">Specifically, SDT for Business enables you to:</span></span>

- [<span data-ttu-id="4d651-107">Personalizzare il pacchetto.</span><span class="sxs-lookup"><span data-stu-id="4d651-107">Customize the package.</span></span>](#create-custom-sdt)
- [<span data-ttu-id="4d651-108">Esegui l'app usando i comandi.</span><span class="sxs-lookup"><span data-stu-id="4d651-108">Run the app using commands.</span></span>](surface-diagnostic-toolkit-command-line.md)
- [<span data-ttu-id="4d651-109">Eseguire più test hardware per la risoluzione dei problemi.</span><span class="sxs-lookup"><span data-stu-id="4d651-109">Run multiple hardware tests to troubleshoot issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#multiple)
- [<span data-ttu-id="4d651-110">Genera log per l'analisi dei problemi.</span><span class="sxs-lookup"><span data-stu-id="4d651-110">Generate logs for analyzing issues.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#logs)
- [<span data-ttu-id="4d651-111">Ottenere report dettagliati per confrontare la configurazione ottimale del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4d651-111">Obtain detailed report comparing device vs optimal configuration.</span></span>](surface-diagnostic-toolkit-desktop-mode.md#detailed-report)


## <span data-ttu-id="4d651-112">Scenari principali e risorse di download</span><span class="sxs-lookup"><span data-stu-id="4d651-112">Primary scenarios and download resources</span></span> 

<span data-ttu-id="4d651-113">Per eseguire SDT for business, scaricare i componenti elencati nella tabella seguente.</span><span class="sxs-lookup"><span data-stu-id="4d651-113">To run SDT for Business, download the components listed in the following table.</span></span>


<span data-ttu-id="4d651-114">Modalità</span><span class="sxs-lookup"><span data-stu-id="4d651-114">Mode</span></span> |  <span data-ttu-id="4d651-115">Scenari principali</span><span class="sxs-lookup"><span data-stu-id="4d651-115">Primary scenarios</span></span> | <span data-ttu-id="4d651-116">Download</span><span class="sxs-lookup"><span data-stu-id="4d651-116">Download</span></span> | <span data-ttu-id="4d651-117">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="4d651-117">Learn more</span></span>
--- | --- | --- | ---
<span data-ttu-id="4d651-118">Modalità desktop</span><span class="sxs-lookup"><span data-stu-id="4d651-118">Desktop mode</span></span> |  <span data-ttu-id="4d651-119">Aiutare gli utenti a eseguire SDT sui dispositivi Surface per risolvere i problemi.</span><span class="sxs-lookup"><span data-stu-id="4d651-119">Assist users in running SDT on their Surface devices to troubleshoot issues.</span></span><br><span data-ttu-id="4d651-120">Creare un pacchetto personalizzato da distribuire in uno o più dispositivi Surface, consentendo agli utenti di selezionare registri specifici per la raccolta e l'analisi.</span><span class="sxs-lookup"><span data-stu-id="4d651-120">Create a custom package to deploy on one or more Surface devices allowing users to select specific logs to collect and analyze.</span></span> | <span data-ttu-id="4d651-121">Pacchetto MSI distribuibili di SDT:</span><span class="sxs-lookup"><span data-stu-id="4d651-121">SDT distributable MSI package:</span></span><br><span data-ttu-id="4d651-122">Programma di installazione di Microsoft Surface Diagnostic Toolkit for business</span><span class="sxs-lookup"><span data-stu-id="4d651-122">Microsoft Surface Diagnostic Toolkit for Business Installer</span></span><br>[<span data-ttu-id="4d651-123">Strumenti di Surface per IT</span><span class="sxs-lookup"><span data-stu-id="4d651-123">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="4d651-124">Usare il Toolkit di diagnostica Surface in modalità desktop</span><span class="sxs-lookup"><span data-stu-id="4d651-124">Use Surface Diagnostic Toolkit in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
<span data-ttu-id="4d651-125">Riga di comando</span><span class="sxs-lookup"><span data-stu-id="4d651-125">Command line</span></span> |  <span data-ttu-id="4d651-126">Risolvere direttamente i dispositivi Surface in remoto senza interazione con l'utente, usando strumenti standard come Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="4d651-126">Directly troubleshoot Surface devices remotely without user interaction, using standard tools such as Configuration Manager.</span></span> <span data-ttu-id="4d651-127">Include i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-127">It includes the following commands:</span></span><br>`-DataCollector` <span data-ttu-id="4d651-128">raccoglie tutti i file di log</span><span class="sxs-lookup"><span data-stu-id="4d651-128">collects all log files</span></span><br>`-bpa` <span data-ttu-id="4d651-129">esegue la diagnostica sanitaria con Best Practice Analyzer.</span><span class="sxs-lookup"><span data-stu-id="4d651-129">runs health diagnostics using Best Practice Analyzer.</span></span><br>`-windowsupdate` <span data-ttu-id="4d651-130">Controlla Windows Update per gli aggiornamenti mancanti del firmware o del driver.</span><span class="sxs-lookup"><span data-stu-id="4d651-130">checks Windows Update for missing firmware or driver updates.</span></span><br>`-warranty` <span data-ttu-id="4d651-131">Controlla le informazioni sulla garanzia.</span><span class="sxs-lookup"><span data-stu-id="4d651-131">checks warranty information.</span></span> <br><br>| <span data-ttu-id="4d651-132">App console SDT:</span><span class="sxs-lookup"><span data-stu-id="4d651-132">SDT console app:</span></span><br><span data-ttu-id="4d651-133">Console app Microsoft Surface Diagnostics</span><span class="sxs-lookup"><span data-stu-id="4d651-133">Microsoft Surface Diagnostics App Console</span></span><br>[<span data-ttu-id="4d651-134">Strumenti di Surface per IT</span><span class="sxs-lookup"><span data-stu-id="4d651-134">Surface Tools for IT</span></span>](https://www.microsoft.com/download/details.aspx?id=46703) | [<span data-ttu-id="4d651-135">Eseguire il Toolkit di diagnostica superficie usando i comandi</span><span class="sxs-lookup"><span data-stu-id="4d651-135">Run Surface Diagnostic Toolkit using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <span data-ttu-id="4d651-136">Dispositivi supportati</span><span class="sxs-lookup"><span data-stu-id="4d651-136">Supported devices</span></span> 

<span data-ttu-id="4d651-137">SDT for business è supportato nei dispositivi Surface 3 e versioni successive, tra cui:</span><span class="sxs-lookup"><span data-stu-id="4d651-137">SDT for Business is supported on Surface 3 and later devices, including:</span></span>

- <span data-ttu-id="4d651-138">Portatile Surface go</span><span class="sxs-lookup"><span data-stu-id="4d651-138">Surface Laptop Go</span></span>
- <span data-ttu-id="4d651-139">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="4d651-139">Surface Book 3</span></span>
- <span data-ttu-id="4d651-140">Superficie Go 2</span><span class="sxs-lookup"><span data-stu-id="4d651-140">Surface Go 2</span></span>
- <span data-ttu-id="4d651-141">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="4d651-141">Surface Pro X</span></span>
- <span data-ttu-id="4d651-142">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="4d651-142">Surface Pro 7</span></span>
- <span data-ttu-id="4d651-143">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="4d651-143">Surface Laptop 3</span></span>
- <span data-ttu-id="4d651-144">Surface Pro 6</span><span class="sxs-lookup"><span data-stu-id="4d651-144">Surface Pro 6</span></span>
- <span data-ttu-id="4d651-145">Surface Laptop 2</span><span class="sxs-lookup"><span data-stu-id="4d651-145">Surface Laptop 2</span></span>
- <span data-ttu-id="4d651-146">Surface Go</span><span class="sxs-lookup"><span data-stu-id="4d651-146">Surface Go</span></span>
- <span data-ttu-id="4d651-147">Surface go con LTE</span><span class="sxs-lookup"><span data-stu-id="4d651-147">Surface Go with LTE</span></span>
- <span data-ttu-id="4d651-148">Surface Book 2</span><span class="sxs-lookup"><span data-stu-id="4d651-148">Surface Book 2</span></span>
- <span data-ttu-id="4d651-149">Surface Pro con LTE Advanced (Modello 1807)</span><span class="sxs-lookup"><span data-stu-id="4d651-149">Surface Pro with LTE Advanced (Model 1807)</span></span>
- <span data-ttu-id="4d651-150">Surface Pro (Modello 1796)</span><span class="sxs-lookup"><span data-stu-id="4d651-150">Surface Pro (Model 1796)</span></span>
- <span data-ttu-id="4d651-151">Surface Laptop</span><span class="sxs-lookup"><span data-stu-id="4d651-151">Surface Laptop</span></span>
- <span data-ttu-id="4d651-152">Surface Studio</span><span class="sxs-lookup"><span data-stu-id="4d651-152">Surface Studio</span></span>
- <span data-ttu-id="4d651-153">Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="4d651-153">Surface Studio 2</span></span>
- <span data-ttu-id="4d651-154">Surface Book</span><span class="sxs-lookup"><span data-stu-id="4d651-154">Surface Book</span></span>
- <span data-ttu-id="4d651-155">Surface Pro 4</span><span class="sxs-lookup"><span data-stu-id="4d651-155">Surface Pro 4</span></span>
- <span data-ttu-id="4d651-156">Surface 3 LTE</span><span class="sxs-lookup"><span data-stu-id="4d651-156">Surface 3 LTE</span></span>
- <span data-ttu-id="4d651-157">Surface 3</span><span class="sxs-lookup"><span data-stu-id="4d651-157">Surface 3</span></span>
- <span data-ttu-id="4d651-158">Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="4d651-158">Surface Pro 3</span></span>

## <span data-ttu-id="4d651-159">Installazione di Surface Diagnostic Toolkit for business</span><span class="sxs-lookup"><span data-stu-id="4d651-159">Installing Surface Diagnostic Toolkit for Business</span></span>

<span data-ttu-id="4d651-160">Per creare un pacchetto SDT che può essere distribuito agli utenti dell'organizzazione:</span><span class="sxs-lookup"><span data-stu-id="4d651-160">To create an SDT package that you can distribute to users in your organization:</span></span>

1. <span data-ttu-id="4d651-161">Accedere al dispositivo Surface usando l'account Administrator.</span><span class="sxs-lookup"><span data-stu-id="4d651-161">Sign in to your Surface device using the Administrator account.</span></span>
2. <span data-ttu-id="4d651-162">Scarica il pacchetto SDT Windows Installer (. msi) dalla [pagina strumenti Surface per il download](https://www.microsoft.com/download/details.aspx?id=46703) e copialo in una posizione preferita nel dispositivo Surface, ad esempio desktop.</span><span class="sxs-lookup"><span data-stu-id="4d651-162">Download SDT Windows Installer Package (.msi) from the [Surface Tools for IT download page](https://www.microsoft.com/download/details.aspx?id=46703) and copy it to a preferred location on your Surface device, such as Desktop.</span></span>
3. <span data-ttu-id="4d651-163">Verrà visualizzata la configurazione guidata SDT, come illustrato nella figura 1.</span><span class="sxs-lookup"><span data-stu-id="4d651-163">The SDT setup wizard appears, as shown in figure 1.</span></span> <span data-ttu-id="4d651-164">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="4d651-164">Click **Next**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="4d651-165">Se la configurazione guidata non viene visualizzata, assicurarsi di avere eseguito l'accesso all'account di amministratore nel computer.</span><span class="sxs-lookup"><span data-stu-id="4d651-165">If the setup wizard does not appear, ensure that you are signed into the Administrator account on your computer.</span></span> 

    ![Introduzione alla configurazione guidata di Surface Diagnostic Toolkit](images/sdt-1.png)

    *<span data-ttu-id="4d651-167">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="4d651-167">Figure 1.</span></span> <span data-ttu-id="4d651-168">Configurazione guidata di Surface Diagnostic Toolkit</span><span class="sxs-lookup"><span data-stu-id="4d651-168">Surface Diagnostic Toolkit setup wizard</span></span>*

4. <span data-ttu-id="4d651-169">Quando viene visualizzata la configurazione guidata SDT, fare clic su **Avanti**, accettare il contratto di licenza con l'utente finale (EULA)</span><span class="sxs-lookup"><span data-stu-id="4d651-169">When the SDT setup wizard appears, click **Next**, accept the End User License Agreement (EULA)</span></span>

5. <span data-ttu-id="4d651-170">Nella schermata Opzioni di installazione modificare la posizione di installazione predefinita, se necessario.</span><span class="sxs-lookup"><span data-stu-id="4d651-170">On the Install Options screen, change the default install location if desired.</span></span> 
6. <span data-ttu-id="4d651-171">In tipo di installazione selezionare **Avanzate**.</span><span class="sxs-lookup"><span data-stu-id="4d651-171">Under Setup Type, select **Advanced**.</span></span> 

    >[!NOTE]
    ><span data-ttu-id="4d651-172">L'opzione standard consente agli utenti di eseguire lo strumento di diagnostica direttamente sul dispositivo Surface, purché abbiano eseguito l'accesso al dispositivo usando un account di amministratore.</span><span class="sxs-lookup"><span data-stu-id="4d651-172">The standard option allows users to run the diagnostic tool directly on their Surface device provided they are signed into their device using an Administrator account.</span></span> 
    
     ![Opzioni di installazione: avanzate](images/sdt-install.png)

7. <span data-ttu-id="4d651-174">Fare clic su **Avanti** e quindi su **Installa**.</span><span class="sxs-lookup"><span data-stu-id="4d651-174">Click **Next** and then click **Install**.</span></span> 

## <span data-ttu-id="4d651-175">Installazione tramite la riga di comando</span><span class="sxs-lookup"><span data-stu-id="4d651-175">Installing using the command line</span></span>
<span data-ttu-id="4d651-176">Se lo si desidera, è possibile installare SDT al prompt dei comandi e impostare un contrassegno personalizzato per l'installazione dello strumento in modalità amministratore.</span><span class="sxs-lookup"><span data-stu-id="4d651-176">If desired, you can install SDT at a command prompt and set a custom flag to install the tool in admin mode.</span></span> <span data-ttu-id="4d651-177">SDT contiene i seguenti flag di opzione di installazione:</span><span class="sxs-lookup"><span data-stu-id="4d651-177">SDT contains the following install option flags:</span></span>

- `SENDTELEMETRY` <span data-ttu-id="4d651-178">Invia i dati di telemetria a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d651-178">sends telemetry data to Microsoft.</span></span> <span data-ttu-id="4d651-179">Il contrassegno accetta `0` per disabilitato o `1` abilitato.</span><span class="sxs-lookup"><span data-stu-id="4d651-179">The flag accepts `0` for disabled or `1` for enabled.</span></span> <span data-ttu-id="4d651-180">Il valore predefinito è l' `1` invio di telemetria.</span><span class="sxs-lookup"><span data-stu-id="4d651-180">The default value is `1` to send telemetry.</span></span>
- `ADMINMODE` <span data-ttu-id="4d651-181">Configura lo strumento da installare in modalità amministratore.</span><span class="sxs-lookup"><span data-stu-id="4d651-181">configures the tool to be installed in admin mode.</span></span> <span data-ttu-id="4d651-182">Il contrassegno accetta `0` per la modalità client o `1` per l'amministratore it.</span><span class="sxs-lookup"><span data-stu-id="4d651-182">The flag accepts `0` for client mode or `1` for IT Administrator mode.</span></span> <span data-ttu-id="4d651-183">Il valore predefinito è `0`.</span><span class="sxs-lookup"><span data-stu-id="4d651-183">The default value is `0`.</span></span>

### <span data-ttu-id="4d651-184">Per installare SDT dalla riga di comando:</span><span class="sxs-lookup"><span data-stu-id="4d651-184">To install SDT from the command line:</span></span>

1. <span data-ttu-id="4d651-185">Aprire un prompt dei comandi e immettere:</span><span class="sxs-lookup"><span data-stu-id="4d651-185">Open a command prompt and enter:</span></span>

    ```
    msiexec.exe /i <the path of installer> ADMINMODE=1. 
    ```
    **<span data-ttu-id="4d651-186">Esempio:</span><span class="sxs-lookup"><span data-stu-id="4d651-186">Example:</span></span>**

    ```
    C:\Users\Administrator> msiexec.exe/I"C:\Users\Administrator\Desktop\Microsoft_Surface_Diagnostic_Toolkit_for_Business_Installer.msi" ADMINMODE=1
    ```

## <span data-ttu-id="4d651-187">Individuazione di SDT nel dispositivo Surface</span><span class="sxs-lookup"><span data-stu-id="4d651-187">Locating SDT on your Surface device</span></span>

<span data-ttu-id="4d651-188">Sono installate sia l'SDT che la console dell'app SDT `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business` .</span><span class="sxs-lookup"><span data-stu-id="4d651-188">Both SDT and the SDT app console are installed at `C:\Program Files\Microsoft\Surface\Microsoft Surface Diagnostic Toolkit for Business`.</span></span>

<span data-ttu-id="4d651-189">Oltre al file exe, SDT installa un file JSON e un file di admin.dll (modules\admin.dll), come illustrato nella figura 2.</span><span class="sxs-lookup"><span data-stu-id="4d651-189">In addition to the .exe file, SDT installs a JSON file and an admin.dll file (modules\admin.dll), as shown in figure 2.</span></span>

![elenco dei file installati in SDT in Esplora file](images/sdt-2.png)

*<span data-ttu-id="4d651-191">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="4d651-191">Figure 2.</span></span> <span data-ttu-id="4d651-192">File installati da SDT</span><span class="sxs-lookup"><span data-stu-id="4d651-192">Files installed by SDT</span></span>*

<span id="create-custom-sdt" />

## <span data-ttu-id="4d651-193">Preparazione del pacchetto SDT per la distribuzione</span><span class="sxs-lookup"><span data-stu-id="4d651-193">Preparing the SDT package for distribution</span></span>

<span data-ttu-id="4d651-194">La creazione di un pacchetto personalizzato consente di indirizzare lo strumento a problemi noti specifici.</span><span class="sxs-lookup"><span data-stu-id="4d651-194">Creating a custom package allows you to target the tool to specific known issues.</span></span>

1. <span data-ttu-id="4d651-195">Fare clic su **avvia > Esegui**, immettere **Surface** e quindi fare clic su **Surface Diagnostic Toolkit for business**.</span><span class="sxs-lookup"><span data-stu-id="4d651-195">Click **Start > Run**, enter **Surface** and then click **Surface Diagnostic Toolkit for Business**.</span></span> 
2. <span data-ttu-id="4d651-196">Quando lo strumento si apre, fare clic su **Crea pacchetto personalizzato**, come illustrato nella figura 3.</span><span class="sxs-lookup"><span data-stu-id="4d651-196">When the tool opens, click **Create Custom Package**, as shown in figure 3.</span></span>

    ![Opzione Crea pacchetto personalizzato](images/sdt-3.png)

    *<span data-ttu-id="4d651-198">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="4d651-198">Figure 3.</span></span> <span data-ttu-id="4d651-199">Creare un pacchetto personalizzato</span><span class="sxs-lookup"><span data-stu-id="4d651-199">Create custom package</span></span>*

### <span data-ttu-id="4d651-200">Impostazioni della lingua e della telemetria</span><span class="sxs-lookup"><span data-stu-id="4d651-200">Language and telemetry settings</span></span>

  <span data-ttu-id="4d651-201">Quando si crea un pacchetto, è possibile selezionare le impostazioni della lingua o rifiutare di inviare informazioni di telemetria a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4d651-201">When creating a package, you can select language settings or opt out of sending telemetry information to Microsoft.</span></span> <span data-ttu-id="4d651-202">Per impostazione predefinita, l'SDT Invia la telemetria a Microsoft usata per migliorare l'applicazione conformemente all' [informativa sulla privacy Microsoft](https://privacy.microsoft.com/privacystatement).</span><span class="sxs-lookup"><span data-stu-id="4d651-202">By default, SDT sends telemetry to Microsoft that is used to improve the application in accordance with the [Microsoft Privacy Statement](https://privacy.microsoft.com/privacystatement).</span></span> <span data-ttu-id="4d651-203">Se si vuole rifiutare, deselezionare la casella di controllo quando si crea un pacchetto personalizzato, come illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="4d651-203">If you wish to decline, clear the check box when creating a custom package, as shown below.</span></span> <span data-ttu-id="4d651-204">O deselezionare la casella **di controllo Invia telemetria a Microsoft** nella pagina **Opzioni di installazione** durante la configurazione SDT.</span><span class="sxs-lookup"><span data-stu-id="4d651-204">Or clear the **Send telemetry to Microsoft** check box on the **Install Options** page during SDT Setup.</span></span> 

>[!NOTE]
><span data-ttu-id="4d651-205">Questa impostazione non ha alcun effetto sulla telemetria minima memorizzata automaticamente nei server Microsoft quando si esegue test e riparazioni che richiedono una connessione Internet, ad esempio Windows Update e software Repair, o un feedback usando i pulsanti Smile o cipiglio nella barra degli strumenti dell'app.</span><span class="sxs-lookup"><span data-stu-id="4d651-205">This setting does not affect the minimal telemetry automatically stored on Microsoft servers when running tests and repairs that require an Internet connection, such as Windows Update and Software repair, or providing feedback using the Smile or Frown buttons in the app toolbar.</span></span> 


![Selezionare la lingua e le impostazioni di telemetria](images/sdt-4.png)

*<span data-ttu-id="4d651-207">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="4d651-207">Figure 4.</span></span> <span data-ttu-id="4d651-208">Selezionare la lingua e le impostazioni di telemetria</span><span class="sxs-lookup"><span data-stu-id="4d651-208">Select language and telemetry settings</span></span>*


### <span data-ttu-id="4d651-209">Pagina Windows Update</span><span class="sxs-lookup"><span data-stu-id="4d651-209">Windows Update page</span></span>

<span data-ttu-id="4d651-210">Selezionare l'opzione appropriata per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="4d651-210">Select the option appropriate for your organization.</span></span> <span data-ttu-id="4d651-211">La maggior parte delle organizzazioni con più utenti in genere verrà selezionata per ricevere gli aggiornamenti tramite Windows Server Update Services (WSUS), come illustrato nella figura 5.</span><span class="sxs-lookup"><span data-stu-id="4d651-211">Most organizations with multiple users will typically select to receive updates via Windows Server Update Services (WSUS), as shown in figure 5.</span></span> <span data-ttu-id="4d651-212">Se si usano i pacchetti di Windows Update locali o WSUS, immettere il percorso in base alle esigenze.</span><span class="sxs-lookup"><span data-stu-id="4d651-212">If using local Windows Update packages or WSUS, enter the path as appropriate.</span></span> 

![Selezionare l'opzione Windows Update](images/sdt-5.png)

*<span data-ttu-id="4d651-214">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="4d651-214">Figure 5.</span></span> <span data-ttu-id="4d651-215">Opzione Windows Update</span><span class="sxs-lookup"><span data-stu-id="4d651-215">Windows Update option</span></span>*

### <span data-ttu-id="4d651-216">Pagina di ripristino del software</span><span class="sxs-lookup"><span data-stu-id="4d651-216">Software repair page</span></span>

<span data-ttu-id="4d651-217">In questo modo è possibile selezionare o rimuovere l'opzione per eseguire gli aggiornamenti per il ripristino del software.</span><span class="sxs-lookup"><span data-stu-id="4d651-217">This allows you to select or remove the option to run software repair updates.</span></span> 

![Selezionare l'opzione di ripristino software](images/sdt-6.png)

*<span data-ttu-id="4d651-219">Figura 6.</span><span class="sxs-lookup"><span data-stu-id="4d651-219">Figure 6.</span></span> <span data-ttu-id="4d651-220">Opzione di ripristino software</span><span class="sxs-lookup"><span data-stu-id="4d651-220">Software repair option</span></span>*

### <span data-ttu-id="4d651-221">Raccolta di registri e salvataggio della pagina del pacchetto</span><span class="sxs-lookup"><span data-stu-id="4d651-221">Collecting logs and saving package page</span></span>

<span data-ttu-id="4d651-222">È possibile selezionare l'esecuzione di un'ampia gamma di log tra applicazioni, driver, hardware e sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="4d651-222">You can select to run a wide range of logs across applications, drivers, hardware, and the operating system.</span></span> <span data-ttu-id="4d651-223">Fare clic sull'area appropriata e selezionare dal menu dei registri disponibili.</span><span class="sxs-lookup"><span data-stu-id="4d651-223">Click the appropriate area and select from the menu of available logs.</span></span> <span data-ttu-id="4d651-224">È quindi possibile salvare il pacchetto in un punto di distribuzione del software o in una posizione equivalente a cui gli utenti possono accedere.</span><span class="sxs-lookup"><span data-stu-id="4d651-224">You can then save the package to a software distribution point or equivalent location that users can access.</span></span> 

![Selezionare opzioni log](images/sdt-7.png)

*<span data-ttu-id="4d651-226">Figura 7.</span><span class="sxs-lookup"><span data-stu-id="4d651-226">Figure 7.</span></span> <span data-ttu-id="4d651-227">Opzione log e Salva pacchetto</span><span class="sxs-lookup"><span data-stu-id="4d651-227">Log option and save package</span></span>*

## <span data-ttu-id="4d651-228">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="4d651-228">Next steps</span></span>

- [<span data-ttu-id="4d651-229">Usare Toolkit di diagnostica per Surface per le aziende in modalità desktop</span><span class="sxs-lookup"><span data-stu-id="4d651-229">Use Surface Diagnostic Toolkit for Business in desktop mode</span></span>](surface-diagnostic-toolkit-desktop-mode.md)
- [<span data-ttu-id="4d651-230">Usare i comandi con Surface Diagnostic Toolkit for business</span><span class="sxs-lookup"><span data-stu-id="4d651-230">Use Surface Diagnostic Toolkit for Business using commands</span></span>](surface-diagnostic-toolkit-command-line.md)

## <span data-ttu-id="4d651-231">Modifiche e aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="4d651-231">Changes and updates</span></span>

### <span data-ttu-id="4d651-232">Versione 2.124.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-232">Version 2.124.139.0</span></span>

<span data-ttu-id="4d651-233">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-233">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="4d651-234">Supporto integrato senza soluzione di continuità</span><span class="sxs-lookup"><span data-stu-id="4d651-234">Seamless integrated support</span></span>
- <span data-ttu-id="4d651-235">Salvare tutti i risultati del test</span><span class="sxs-lookup"><span data-stu-id="4d651-235">Save all test results</span></span>
- <span data-ttu-id="4d651-236">Verificare se l'immagine è creata in formato personalizzato</span><span class="sxs-lookup"><span data-stu-id="4d651-236">Check if the image is custom created</span></span>
- <span data-ttu-id="4d651-237">Includere avvisi da Gestione dispositivi</span><span class="sxs-lookup"><span data-stu-id="4d651-237">Include warnings from device manager</span></span>
- <span data-ttu-id="4d651-238">Versione del firmware Dock</span><span class="sxs-lookup"><span data-stu-id="4d651-238">Dock firmware version</span></span>
- <span data-ttu-id="4d651-239">Contrassegnare le unità come potenziali errori nel test di archiviazione</span><span class="sxs-lookup"><span data-stu-id="4d651-239">Flag drives as potential failures in storage test</span></span>
- <span data-ttu-id="4d651-240">Rimuovi collegamento allo Store</span><span class="sxs-lookup"><span data-stu-id="4d651-240">Remove store link</span></span> 

### <span data-ttu-id="4d651-241">Versione 2.121.139</span><span class="sxs-lookup"><span data-stu-id="4d651-241">Version 2.121.139</span></span>
*<span data-ttu-id="4d651-242">Data di rilascio: 31 2020 luglio</span><span class="sxs-lookup"><span data-stu-id="4d651-242">Release date: July 31 2020</span></span>*<br>
<span data-ttu-id="4d651-243">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-243">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="4d651-244">Esperienza di supporto continuo</span><span class="sxs-lookup"><span data-stu-id="4d651-244">Seamless support experience</span></span>
- <span data-ttu-id="4d651-245">Correzioni di bug</span><span class="sxs-lookup"><span data-stu-id="4d651-245">Bug fixes</span></span>

### <span data-ttu-id="4d651-246">Versione 2.94.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-246">Version 2.94.139.0</span></span>
*<span data-ttu-id="4d651-247">Data di rilascio: 11 maggio 2020</span><span class="sxs-lookup"><span data-stu-id="4d651-247">Release date: May 11, 2020</span></span>*<br>
<span data-ttu-id="4d651-248">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-248">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="4d651-249">Possibilità di ignorare Windows Update per eseguire il controllo hardware.</span><span class="sxs-lookup"><span data-stu-id="4d651-249">Ability to skip Windows Update to perform hardware check.</span></span>
- <span data-ttu-id="4d651-250">Possibilità di ricevere notifiche per informazioni sull'aggiornamento della versione più recente</span><span class="sxs-lookup"><span data-stu-id="4d651-250">Ability to receive notifications for about the latest version update</span></span>
- <span data-ttu-id="4d651-251">Superficie Go 2</span><span class="sxs-lookup"><span data-stu-id="4d651-251">Surface Go 2</span></span>
- <span data-ttu-id="4d651-252">Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="4d651-252">Surface Book 3</span></span>
- <span data-ttu-id="4d651-253">Mostra indicatore di stato</span><span class="sxs-lookup"><span data-stu-id="4d651-253">Show progress indicator</span></span>


### <span data-ttu-id="4d651-254">Versione 2.43.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-254">Version 2.43.139.0</span></span>
*<span data-ttu-id="4d651-255">Data di rilascio: 21 ottobre 2019</span><span class="sxs-lookup"><span data-stu-id="4d651-255">Release date: October 21, 2019</span></span>*<br>
<span data-ttu-id="4d651-256">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-256">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span>

- <span data-ttu-id="4d651-257">Surface Pro 7</span><span class="sxs-lookup"><span data-stu-id="4d651-257">Surface Pro 7</span></span>
- <span data-ttu-id="4d651-258">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="4d651-258">Surface Laptop 3</span></span>

### <span data-ttu-id="4d651-259">Versione 2.42.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-259">Version 2.42.139.0</span></span>
*<span data-ttu-id="4d651-260">Data di rilascio: 24 settembre 2019</span><span class="sxs-lookup"><span data-stu-id="4d651-260">Release date: September 24, 2019</span></span>*<br>
<span data-ttu-id="4d651-261">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-261">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="4d651-262">Possibilità di scaricare i report hardware.</span><span class="sxs-lookup"><span data-stu-id="4d651-262">Ability to download hardware reports.</span></span>
- <span data-ttu-id="4d651-263">Possibilità di contattare il supporto Microsoft direttamente dallo strumento.</span><span class="sxs-lookup"><span data-stu-id="4d651-263">Ability to contact Microsoft Support directly from the tool.</span></span> <br>

### <span data-ttu-id="4d651-264">Versione 2.41.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-264">Version 2.41.139.0</span></span>
*<span data-ttu-id="4d651-265">Data di rilascio: 24 giugno 2019</span><span class="sxs-lookup"><span data-stu-id="4d651-265">Release date: June 24, 2019</span></span>*<br>
<span data-ttu-id="4d651-266">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-266">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="4d651-267">Informazioni sulla versione del driver incluse nei registri e nel report.</span><span class="sxs-lookup"><span data-stu-id="4d651-267">Driver version information included in logs and report.</span></span>
- <span data-ttu-id="4d651-268">Possibilità di inviare commenti e suggerimenti sull'app.</span><span class="sxs-lookup"><span data-stu-id="4d651-268">Ability to provide feedback about the app.</span></span><br>


### <span data-ttu-id="4d651-269">Versione 2.36.139.0</span><span class="sxs-lookup"><span data-stu-id="4d651-269">Version 2.36.139.0</span></span>
*<span data-ttu-id="4d651-270">Data di rilascio: 26 aprile 2019</span><span class="sxs-lookup"><span data-stu-id="4d651-270">Release date: April 26, 2019</span></span>*<br>
<span data-ttu-id="4d651-271">Questa versione di Surface Diagnostic Toolkit for business aggiunge il supporto per gli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4d651-271">This version of Surface Diagnostic Toolkit for Business adds support for the following:</span></span> 
- <span data-ttu-id="4d651-272">Opzione di configurazione avanzata per sbloccare le funzionalità di amministrazione tramite l'interfaccia utente del programma di installazione, senza richiedere la configurazione della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="4d651-272">Advanced Setup option to unlock admin capabilities through the installer UI, without requiring command line configuration.</span></span>
- <span data-ttu-id="4d651-273">Miglioramenti dell'accessibilità.</span><span class="sxs-lookup"><span data-stu-id="4d651-273">Accessibility improvements.</span></span>
- <span data-ttu-id="4d651-274">Impostazioni di controllo della luminosità superficiale incluse nei registri.</span><span class="sxs-lookup"><span data-stu-id="4d651-274">Surface brightness control settings included in logs.</span></span>
- <span data-ttu-id="4d651-275">Collegamento supporto compatibilità monitor esterno in Generatore report.</span><span class="sxs-lookup"><span data-stu-id="4d651-275">External monitor compatibility support link in report generator.</span></span>

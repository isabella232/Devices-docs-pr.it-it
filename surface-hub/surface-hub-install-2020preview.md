---
title: 'Installare la versione di anteprima dell’aggiornamento di Windows 10 Team 2020 '
description: L'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 team 2020 Update, è ora disponibile.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/27/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 6d370db0232ae1f93d1ba6b8ff15b5ff2cfa9f10
ms.sourcegitcommit: 19d2a78242777590bd09af3ac6552c07b032e0a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2020
ms.locfileid: "11142905"
---
# <span data-ttu-id="0177a-104">Installare la versione di anteprima dell’aggiornamento di Windows 10 Team 2020 </span><span class="sxs-lookup"><span data-stu-id="0177a-104">Install Windows 10 Team 2020 Update Preview Build</span></span> 

<span data-ttu-id="0177a-105">La build di anteprima del sistema operativo Surface Hub, **Windows 10 Team 2020 Update Preview**, è disponibile senza costi aggiuntivi da [Windows Insider Program](https://insider.windows.com).</span><span class="sxs-lookup"><span data-stu-id="0177a-105">The preview build of the Surface Hub operating system, **Windows 10 Team 2020 Update Preview**, is available at no additional cost from the [Windows Insider Program](https://insider.windows.com).</span></span> 

> [!NOTE] 
> <span data-ttu-id="0177a-106">Il rilascio finale pubblico di Windows 10 team 2020 Update è ora disponibile.</span><span class="sxs-lookup"><span data-stu-id="0177a-106">The final public release of Windows 10 Team 2020  Update is now available.</span></span> <span data-ttu-id="0177a-107">Per altre informazioni, vedere [aggiornamento di Windows 10 Team 2020](surface-hub-2020-update.md).</span><span class="sxs-lookup"><span data-stu-id="0177a-107">To learn more, see [Windows 10 Team 2020 Update](surface-hub-2020-update.md).</span></span>

<span data-ttu-id="0177a-108">Windows 10 team 2020 Update offre miglioramenti importanti alla distribuzione e alla gestibilità dei dispositivi insieme alle caratteristiche più recenti di Windows 10.</span><span class="sxs-lookup"><span data-stu-id="0177a-108">Windows 10 Team 2020 Update brings major improvements to device deployment and manageability along with the latest Windows 10 features.</span></span> <span data-ttu-id="0177a-109">Per altre informazioni sulle novità, vedere il post di Blog seguente: [nuovo aggiornamento del sistema operativo Surface Hub rilasciato per l'anteprima pubblica.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)</span><span class="sxs-lookup"><span data-stu-id="0177a-109">To learn more about what's new, see the following blog post: [New Surface Hub OS update released for public preview.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)</span></span> <span data-ttu-id="0177a-110">Per i problemi noti, vedere [problemi noti: Windows 10 Team 2020 Update](surface-hub-2020-team-update-known-issues.md)</span><span class="sxs-lookup"><span data-stu-id="0177a-110">For known issues, refer to [Known issues: Windows 10 Team 2020 Update](surface-hub-2020-team-update-known-issues.md)</span></span>
 
## <span data-ttu-id="0177a-111">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="0177a-111">Prerequisites</span></span>

- <span data-ttu-id="0177a-112">Eseguire la registrazione con il [programma Windows Insider](https://insider.windows.com/).</span><span class="sxs-lookup"><span data-stu-id="0177a-112">Register with the [Windows Insider Program](https://insider.windows.com/).</span></span>
- <span data-ttu-id="0177a-113">Scaricare la build Preview di aggiornamento di Windows 10 team 2020 da Windows Insider Fast Channel.</span><span class="sxs-lookup"><span data-stu-id="0177a-113">Download the Windows 10 Team 2020 Update Preview Build from the Windows Insider Program Fast Channel.</span></span>
- <span data-ttu-id="0177a-114">Dopo aver installato la build di anteprima, scaricare gli aggiornamenti del firmware necessari.</span><span class="sxs-lookup"><span data-stu-id="0177a-114">After you install the Preview build, download the required firmware updates.</span></span> <span data-ttu-id="0177a-115">Nota: gli aggiornamenti del firmware non possono essere disinstallati anche se si decide di uscire da Windows Insider Program.</span><span class="sxs-lookup"><span data-stu-id="0177a-115">Note: Firmware updates cannot be uninstalled even if you decide to leave the Windows Insider Program.</span></span>

## <span data-ttu-id="0177a-116">Preparare il mozzo della superficie</span><span class="sxs-lookup"><span data-stu-id="0177a-116">Prepare your Surface Hub</span></span>

<span data-ttu-id="0177a-117">Prima di iniziare, verifica che il tuo hub Surface disponga degli aggiornamenti più recenti di Windows Update e assicurati di salvare la chiave BitLocker associata al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0177a-117">Before you begin, check that your Surface Hub has the latest updates from Windows Update and make sure you save the BitLocker key associated with your device.</span></span>

**<span data-ttu-id="0177a-118">Per verificare manualmente la disponibilità di aggiornamenti:</span><span class="sxs-lookup"><span data-stu-id="0177a-118">To manually check for updates:</span></span>**

1. <span data-ttu-id="0177a-119">In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="0177a-119">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="0177a-120">Passare a **Aggiorna & Security**  >  **Windows Update** e quindi selezionare **Controlla aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="0177a-120">Navigate to **Update & Security** > **Windows Update** and then select **Check for updates**.</span></span>

<span data-ttu-id="0177a-121">Per altre informazioni, vedere [gestire gli aggiornamenti di Windows in Surface Hub](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub).</span><span class="sxs-lookup"><span data-stu-id="0177a-121">For more information, see [Manage Windows updates on Surface Hub](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub).</span></span>

**<span data-ttu-id="0177a-122">Per salvare manualmente la chiave BitLocker:</span><span class="sxs-lookup"><span data-stu-id="0177a-122">To manually save your BitLocker key:</span></span>**

1. <span data-ttu-id="0177a-123">Inserire un'unità USB in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="0177a-123">Insert a USB drive into Surface Hub.</span></span>
2. <span data-ttu-id="0177a-124">In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="0177a-124">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
3. <span data-ttu-id="0177a-125">Passare a **aggiornamento &**  >  **ripristino**della sicurezza.</span><span class="sxs-lookup"><span data-stu-id="0177a-125">Navigate to **Update & Security** > **Recovery**.</span></span>
4. <span data-ttu-id="0177a-126">In **BitLocker**selezionare **Salva**.</span><span class="sxs-lookup"><span data-stu-id="0177a-126">Under **BitLocker**, select **Save**.</span></span> <span data-ttu-id="0177a-127">La chiave BitLocker viene salvata in un file di testo nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="0177a-127">The BitLocker key is saved to a text file on the USB drive.</span></span>

<span data-ttu-id="0177a-128">Per altre informazioni, vedere [salvare la chiave BitLocker](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub).</span><span class="sxs-lookup"><span data-stu-id="0177a-128">For more information, see [Save your BitLocker key](https://docs.microsoft.com/surface-hub/save-bitlocker-key-surface-hub).</span></span>
 
## <span data-ttu-id="0177a-129">Installare la build Preview di aggiornamento di Windows 10 team 2020</span><span class="sxs-lookup"><span data-stu-id="0177a-129">Install the Windows 10 Team 2020 Update Preview Build</span></span>

1. <span data-ttu-id="0177a-130">In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="0177a-130">On Surface Hub, open **Settings** and enter your admin credentials when prompted.</span></span>
2. <span data-ttu-id="0177a-131">Passare a **Privacy > diagnostics & feedback** e impostare i dati di diagnostica su **full**.</span><span class="sxs-lookup"><span data-stu-id="0177a-131">Navigate to **Privacy > Diagnostics & feedback** and set Diagnostic data to **Full**.</span></span> <span data-ttu-id="0177a-132">Alcune aree o organizzazioni potrebbero dover applicare questa impostazione tramite i criteri MDM o il file PPKG:</span><span class="sxs-lookup"><span data-stu-id="0177a-132">Some regions or organizations may need to apply this setting via MDM policy or PPKG file:</span></span>
   - <span data-ttu-id="0177a-133">**Per MDM:** Impostare i criteri seguenti:. **/Vendor/MSFT/Policy/System/AllowTelemetry** con il valore intero di 3:</span><span class="sxs-lookup"><span data-stu-id="0177a-133">**For MDM:** Set the following policy: .**/Vendor/MSFT/Policy/System/AllowTelemetry** with the integer value of 3:</span></span>
    
        ![Impostare AllowTelemetry su 3](images/hub-2020-allow-telemetry.png)

    - <span data-ttu-id="0177a-135">**Per PPKG:** Scaricare il [file PPKG](https://aka.ms/HubTltmtry).</span><span class="sxs-lookup"><span data-stu-id="0177a-135">**For PPKG:** Download the [PPKG file](https://aka.ms/HubTltmtry).</span></span>

3. <span data-ttu-id="0177a-136">Passare al programma **Update & Security**  >  **Windows Insider** e quindi selezionare **inizia** a eseguire la registrazione.</span><span class="sxs-lookup"><span data-stu-id="0177a-136">Navigate to **Update & Security** > **Windows Insider Program** and then select **Get started** to enroll.</span></span>
4. <span data-ttu-id="0177a-137">Seguire le istruzioni per la registrazione come Windows Insider usando l'account di lavoro (consigliato) o l'account Microsoft personale.</span><span class="sxs-lookup"><span data-stu-id="0177a-137">Follow the prompts to register as a Windows Insider using either your work account (recommended) or your personal Microsoft account.</span></span> <span data-ttu-id="0177a-138">Per informazioni dettagliate sui vantaggi della registrazione con l'account aziendale, vedere [registrazione per Windows Insider Program for business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).</span><span class="sxs-lookup"><span data-stu-id="0177a-138">For details on the benefits of registering with your work account, see [Register for the Windows Insider Program for Business](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-register).</span></span>
5. <span data-ttu-id="0177a-139">In Seleziona le **Impostazioni Insider**selezionare **Fast**.</span><span class="sxs-lookup"><span data-stu-id="0177a-139">Under **Pick your Insider settings**, select **Fast**.</span></span>
6. <span data-ttu-id="0177a-140">Consentire all'hub Surface di installare automaticamente la build di anteprima e gli aggiornamenti del firmware necessari nei prossimi 3 o 4 giorni.</span><span class="sxs-lookup"><span data-stu-id="0177a-140">Allow the Surface Hub to automatically install the Preview Build and the required firmware updates over the next 3 to 4 days.</span></span> <span data-ttu-id="0177a-141">Il dispositivo scaricherà e installerà automaticamente gli aggiornamenti durante le [finestre di manutenzione](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window)giornaliera.</span><span class="sxs-lookup"><span data-stu-id="0177a-141">The device will automatically download and install the updates during daily [maintenance windows](https://docs.microsoft.com/surface-hub/manage-windows-updates-for-surface-hub#maintenance-window).</span></span> <span data-ttu-id="0177a-142">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="0177a-142">For example:</span></span>

- <span data-ttu-id="0177a-143">Durante la prima finestra di manutenzione, Surface Hub avvia il download della build di anteprima da Windows Update.</span><span class="sxs-lookup"><span data-stu-id="0177a-143">During the first maintenance window, Surface Hub starts downloading the Preview Build from Windows Update.</span></span>
- <span data-ttu-id="0177a-144">Durante una seconda finestra di manutenzione, il dispositivo viene riavviato per completare l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="0177a-144">During a second maintenance window, the device restarts to complete the update.</span></span>
- <span data-ttu-id="0177a-145">Durante una terza finestra di manutenzione, il dispositivo Scarica e installa gli aggiornamenti del firmware necessari.</span><span class="sxs-lookup"><span data-stu-id="0177a-145">During a third maintenance window, the device downloads and installs the required firmware updates.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0177a-146">Microsoft consiglia di prenotare la superficie hub per 3-4 giorni per consentire al dispositivo di completare l'installazione della build di anteprima e gli aggiornamenti del firmware necessari.</span><span class="sxs-lookup"><span data-stu-id="0177a-146">Microsoft recommends reserving the Surface Hub for 3-4 days to allow the device to finish installing the Preview Build and the required firmware updates.</span></span> <span data-ttu-id="0177a-147">Se si usa il dispositivo durante questo processo, è possibile che si verifichino problemi di grafica, audio e interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0177a-147">You may experience graphics, audio, and user interface issues if you use the device during this process.</span></span>

### <span data-ttu-id="0177a-148">Se si sceglie di installare manualmente la build di anteprima e gli aggiornamenti del firmware necessari:</span><span class="sxs-lookup"><span data-stu-id="0177a-148">If you choose to manually install the Preview Build and required firmware updates:</span></span>

1. <span data-ttu-id="0177a-149">Dopo aver effettuato la registrazione con il programma Windows Insider, vedere l'aggiornamento **delle impostazioni**  >  **& Security**  >  **Windows Update** e selezionare **Controlla aggiornamenti** per installare la build di anteprima.</span><span class="sxs-lookup"><span data-stu-id="0177a-149">After you've registered with the Windows Insider Program, go to **Settings** > **Update & Security** > **Windows Update** and select **Check for updates** to install the Preview Build.</span></span>
2. <span data-ttu-id="0177a-150">Dopo l'installazione della build di anteprima (potrebbero essere necessarie fino a 14 ore), selezionare **Riavvia ora** per completare la procedura.</span><span class="sxs-lookup"><span data-stu-id="0177a-150">Once the Preview Build installs (it may take up to 14 hours), select **Restart now** to complete the installation.</span></span>
3. <span data-ttu-id="0177a-151">Dopo il riavvio del dispositivo, vedere aggiornare **le impostazioni**  >  **& Security**  >  **Windows Update**e selezionare **Controlla aggiornamenti per installare gli aggiornamenti del firmware necessari**.</span><span class="sxs-lookup"><span data-stu-id="0177a-151">After the device restarts, go to **Settings** > **Update & Security** > **Windows Update**, and select **Check for updates to install required firmware updates**.</span></span>
4. <span data-ttu-id="0177a-152">Dopo l'installazione del firmware, selezionare **Riavvia ora**.</span><span class="sxs-lookup"><span data-stu-id="0177a-152">Once the firmware installs, select **Restart now**.</span></span>

> [!WARNING]
> <span data-ttu-id="0177a-153">Se si installa la build di anteprima senza installare gli aggiornamenti del firmware necessari, è possibile che vengano visualizzati problemi relativi a grafica, audio e interfaccia utente.</span><span class="sxs-lookup"><span data-stu-id="0177a-153">You may see graphics, audio, and user interface issues if you install the Preview Build without installing the required firmware updates.</span></span>

> [!NOTE]
> <span data-ttu-id="0177a-154">Se si sceglie di abbandonare il programma Windows Insider e ripristinare Surface Hub in una versione precedente del sistema operativo, è necessario prima di tutto [reimpostare il dispositivo](https://docs.microsoft.com/surface-hub/device-reset-surface-hub).</span><span class="sxs-lookup"><span data-stu-id="0177a-154">If you choose to leave the Windows Insider Program and revert your Surface Hub to an older version of the operating system, you must first [reset your device](https://docs.microsoft.com/surface-hub/device-reset-surface-hub).</span></span> <span data-ttu-id="0177a-155">In seguito, dovrai passare attraverso il [programma prima esecuzione](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) per riconfigurare il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0177a-155">Afterwards, you will need to go through the [first run program](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub) to re-configure your device.</span></span>
 

## <span data-ttu-id="0177a-156">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="0177a-156">Learn more</span></span>

- [<span data-ttu-id="0177a-157">Problemi noti: aggiornamento di Windows 10 team 2020</span><span class="sxs-lookup"><span data-stu-id="0177a-157">Known issues: Windows 10 Team 2020 Update</span></span>](surface-hub-2020-team-update-known-issues.md)
- [<span data-ttu-id="0177a-158">Nuovo aggiornamento del sistema operativo Surface Hub rilasciato per l'anteprima pubblica.</span><span class="sxs-lookup"><span data-stu-id="0177a-158">New Surface Hub OS update released for public preview.</span></span>](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/new-surface-hub-os-update-released-for-public-preview/ba-p/1534823)
- [<span data-ttu-id="0177a-159">Attività iniziali con il programma Windows Insider per le aziende</span><span class="sxs-lookup"><span data-stu-id="0177a-159">Getting started with the Windows Insider Program for Business</span></span>](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-manage)
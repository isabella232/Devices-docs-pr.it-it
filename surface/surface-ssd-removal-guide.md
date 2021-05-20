---
title: Rimozione SSD nei dispositivi Surface compatibili
description: In questo articolo, destinato a tecnici IT qualificati, vengono descritte le procedure consigliate per la rimozione e la sostituzione di SSD in Surface Laptop 4, Surface Laptop 3, Surface Pro 7+, Surface Pro X e Surface Laptop Go.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: brrecord
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
- Surface Laptop 4
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 7ba66981c021f1f0a08ebf33aab0a73481111a4d
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576906"
---
# <a name="best-practices-for-ssd-removal-from-compatible-surface-devices"></a><span data-ttu-id="4817c-103">Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili</span><span class="sxs-lookup"><span data-stu-id="4817c-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4817c-104">Questo articolo è destinato all'utilizzo da parte di tecnici IT qualificati solo in un'organizzazione aziendale.</span><span class="sxs-lookup"><span data-stu-id="4817c-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="4817c-105">Vengono descritte le procedure consigliate per l'utilizzo da parte di tecnici IT qualificati nella rimozione e sostituzione di SSD nei seguenti dispositivi Surface compatibili:</span><span class="sxs-lookup"><span data-stu-id="4817c-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="4817c-106">Surface Pro 7+</span><span class="sxs-lookup"><span data-stu-id="4817c-106">Surface Pro 7+</span></span>
- <span data-ttu-id="4817c-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="4817c-107">Surface Pro X</span></span>
- <span data-ttu-id="4817c-108">Surface Laptop Go</span><span class="sxs-lookup"><span data-stu-id="4817c-108">Surface Laptop Go</span></span>
- <span data-ttu-id="4817c-109">Surface Laptop 3</span><span class="sxs-lookup"><span data-stu-id="4817c-109">Surface Laptop 3</span></span>
- <span data-ttu-id="4817c-110">Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="4817c-110">Surface Laptop 4</span></span>

> [!WARNING]
> <span data-ttu-id="4817c-111">L'apertura di dispositivi e la sostituzione dei componenti del dispositivo possono presentare rischi di urto elettrico, danni al dispositivo, incendio e lesioni personali e altri rischi.</span><span class="sxs-lookup"><span data-stu-id="4817c-111">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="4817c-112">Prestare sempre attenzione quando si intraprendono tali attività.</span><span class="sxs-lookup"><span data-stu-id="4817c-112">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="4817c-113">Seguire le precauzioni e le procedure di sicurezza identificate nella Guida alla rimozione [di rSSD per Enterprise](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="4817c-113">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="4817c-114">Si consiglia di ottenere assistenza professionale se non è possibile seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di rSSD per Enterprise".</span><span class="sxs-lookup"><span data-stu-id="4817c-114">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4817c-115">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="4817c-115">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4817c-116">In questo articolo si presuppone che l'utente comprendi le procedure e i criteri e i criteri di sicurezza generali descritti nella "Guida alla rimozione di rSSD per Enterprise".</span><span class="sxs-lookup"><span data-stu-id="4817c-116">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <a name="prepare-for-ssd-removal"></a><span data-ttu-id="4817c-117">Preparare la rimozione di SSD</span><span class="sxs-lookup"><span data-stu-id="4817c-117">Prepare for SSD removal</span></span> 

### <a name="install-the-latest-updates"></a><span data-ttu-id="4817c-118">Installare gli aggiornamenti più recenti</span><span class="sxs-lookup"><span data-stu-id="4817c-118">Install the latest updates</span></span> 

<span data-ttu-id="4817c-119">Prima di iniziare, verificare che nella versione di Windows siano installati gli aggiornamenti più recenti:</span><span class="sxs-lookup"><span data-stu-id="4817c-119">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="4817c-120">Vai a **Start**  >  **Impostazioni**  >  **Update & Security**e seleziona Controlla disponibilità **aggiornamenti.**</span><span class="sxs-lookup"><span data-stu-id="4817c-120">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="4817c-121">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="4817c-121">Install all available updates.</span></span>
3. <span data-ttu-id="4817c-122">Verificare le password necessarie per accedere al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-122">Verify any passwords that are necessary to access the device.</span></span>  
 
## <a name="manage-bitlocker"></a><span data-ttu-id="4817c-123">Gestione BitLocker</span><span class="sxs-lookup"><span data-stu-id="4817c-123">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="4817c-124">Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la BitLocker per i dischi rigidi.</span><span class="sxs-lookup"><span data-stu-id="4817c-124">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="4817c-125">Per ulteriori informazioni, vedere [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span><span class="sxs-lookup"><span data-stu-id="4817c-125">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <a name="if-bitlocker-encryption-is-disabled-during-ssd-removal-and-replacement"></a><span data-ttu-id="4817c-126">Se BitLocker crittografia è disabilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="4817c-126">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="4817c-127">Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, segui questi passaggi per disattivare BitLocker:</span><span class="sxs-lookup"><span data-stu-id="4817c-127">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="4817c-128">In **Impostazioni**digitare **BitLocker** e quindi selezionare **Gestisci BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="4817c-128">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="4817c-129">Selezionare **Disattiva BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="4817c-129">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="4817c-130">Accensione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-130">Power down the device.</span></span> 

### <a name="if-bitlocker-encryption-is-enabled-during-ssd-removal-and-replacement"></a><span data-ttu-id="4817c-131">Se BitLocker crittografia è abilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="4817c-131">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="4817c-132">Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, segui questi passaggi per generare una chiave di ripristino BitLocker e salvarla nell'archiviazione USB:</span><span class="sxs-lookup"><span data-stu-id="4817c-132">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="4817c-133">In **Impostazioni**digitare **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="4817c-133">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="4817c-134">Selezionare **Manage BitLocker**Generate BitLocker Recovery  > **Key**.</span><span class="sxs-lookup"><span data-stu-id="4817c-134">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="4817c-135">Inserire un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="4817c-135">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="4817c-136">Salvare la chiave di ripristino nell'archiviazione USB.</span><span class="sxs-lookup"><span data-stu-id="4817c-136">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="4817c-137">Rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="4817c-137">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="4817c-138">Accensione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-138">Power down the device.</span></span> 

## <a name="remove-and-replace-ssd"></a><span data-ttu-id="4817c-139">Rimuovere e sostituire SSD</span><span class="sxs-lookup"><span data-stu-id="4817c-139">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="4817c-140">Rimuovi l'SSD usando le istruzioni appropriate per il dispositivo incluso nella Guida alla rimozione [di rSSD per Enterprise](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="4817c-140">Remove the SSD by using the appropriate instructions for your device included in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="4817c-141">Inserisci l'SSD originale in un nuovo dispositivo e connetti il nuovo dispositivo a una connessione Internet cablata.</span><span class="sxs-lookup"><span data-stu-id="4817c-141">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="4817c-142">Accensione del nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-142">Power on the new device.</span></span> <span data-ttu-id="4817c-143">Il dispositivo potrebbe passare attraverso un aggiornamento del firmware durante l'avvio.</span><span class="sxs-lookup"><span data-stu-id="4817c-143">The device may go through a firmware update during startup.</span></span>  
 
## <a name="after-ssd-removal-and-replacement"></a><span data-ttu-id="4817c-144">Dopo la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="4817c-144">After SSD removal and replacement</span></span>

### <a name="manage-unencrypted-ssds"></a><span data-ttu-id="4817c-145">Gestire gli SSD non crittografati</span><span class="sxs-lookup"><span data-stu-id="4817c-145">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="4817c-146">Se il file SSD non è crittografato durante il trasferimento, eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="4817c-146">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="4817c-147">Vai a **Opzioni di accesso**  >  **Password** (rappresentata dall'icona del tasto a sinistra).</span><span class="sxs-lookup"><span data-stu-id="4817c-147">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="4817c-148">Immetti la password e accedi in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="4817c-148">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="4817c-149">Dopo aver effettuato l'accesso completo, passare a **Start**  >  **Account**  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="4817c-149">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="4817c-150">Accedi di nuovo usando la password e configura Windows Hello e un PIN quando ti viene richiesto.</span><span class="sxs-lookup"><span data-stu-id="4817c-150">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="4817c-151">Se il dispositivo è stato disabilitato BitLocker per facilitare la rimozione e la sostituzione di SSD e si desidera abilitare BitLocker dopo la sostituzione, passare **a BitLocker**Gestisci BitLocker  >  \*\*\*\*  >  **Riprendi BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="4817c-151">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="4817c-152">Esegui microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-152">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="4817c-153">Per verificare Windows'attivazione, passare a **Impostazioni**  >  **attivazione**.</span><span class="sxs-lookup"><span data-stu-id="4817c-153">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="4817c-154">Se vengono visualizzati messaggi di errore, selezionare **Risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="4817c-154">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="4817c-155">Controlla l Office account aprendo **l'app Office,** passa a **Account file**e quindi controlla la presenza di eventuali messaggi  >  \*\*\*\* di errore.</span><span class="sxs-lookup"><span data-stu-id="4817c-155">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <a name="managing-encrypted-ssds"></a><span data-ttu-id="4817c-156">Gestione degli SSD crittografati</span><span class="sxs-lookup"><span data-stu-id="4817c-156">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="4817c-157">Sarà necessario disporre di un secondo dispositivo per leggere BitLocker chiave di ripristino salvata nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="4817c-157">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="4817c-158">Se l'SSD viene crittografato durante il trasferimento, eseguire la procedura seguente:</span><span class="sxs-lookup"><span data-stu-id="4817c-158">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="4817c-159">Inserisci l'unità USB che contiene la BitLocker di ripristino nel secondo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-159">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="4817c-160">Aprire il .txt file contenente la chiave di ripristino di Bitlocker.</span><span class="sxs-lookup"><span data-stu-id="4817c-160">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="4817c-161">Immetti manualmente la BitLocker di ripristino sul nuovo dispositivo che contiene l'SSD originale.</span><span class="sxs-lookup"><span data-stu-id="4817c-161">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="4817c-162">Dopo aver immesso correttamente la chiave BitLocker \*\*\*\* di ripristino, passare a Opzioni di accesso Password (rappresentata dall'icona del tasto  >  \*\*\*\* a sinistra).</span><span class="sxs-lookup"><span data-stu-id="4817c-162">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="4817c-163">Immetti la password e accedi, in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="4817c-163">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="4817c-164">Dopo aver effettuato l'accesso completo, passare a **Start**  >  **Account**  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="4817c-164">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="4817c-165">Accedi di nuovo usando la password, quindi configura Windows Hello e aggiungi un PIN.</span><span class="sxs-lookup"><span data-stu-id="4817c-165">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="4817c-166">Se il dispositivo è stato disabilitato BitLocker per facilitare la rimozione e la sostituzione di SSD e se si desidera abilitare BitLocker dopo la sostituzione, passare **a Impostazioni**  >  **BitLocker**  >  **Manage BitLocker**Resume  >  **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="4817c-166">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="4817c-167">Esegui **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4817c-167">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="4817c-168">Per controllare Windows'attivazione, **selezionare Impostazioni**  >  **attiva.**</span><span class="sxs-lookup"><span data-stu-id="4817c-168">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="4817c-169">Se vengono visualizzati messaggi di errore, selezionare **Risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="4817c-169">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="4817c-170">Per controllare lo stato dell'account Office, apri **l'app Office**e quindi vai a **Account file**per  >  \*\*\*\* verificare la presenza di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="4817c-170">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <a name="learn-more"></a><span data-ttu-id="4817c-171">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="4817c-171">Learn more</span></span>

- [<span data-ttu-id="4817c-172">Guida alla rimozione di rSSD per Enterprise</span><span class="sxs-lookup"><span data-stu-id="4817c-172">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="4817c-173">Guida al ripristino di BitLocker</span><span class="sxs-lookup"><span data-stu-id="4817c-173">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="4817c-174">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="4817c-174">Still need help?</span></span> <span data-ttu-id="4817c-175">Passare a [Microsoft Community](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="4817c-175">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
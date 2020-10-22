---
title: Rimozione di SSD in dispositivi Surface compatibili
description: Questo articolo, destinato ai tecnici IT qualificati, descrive le procedure consigliate per la rimozione e la sostituzione degli SSD in Surface laptop 3, Surface Pro X e Surface laptop go.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 10/21/2020
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 56c740b39d86ea3fab386e88efa6932e050bb957
ms.sourcegitcommit: 959d2d856b1e5b5c72cd636f576b5feb1b633048
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2020
ms.locfileid: "11133171"
---
# <span data-ttu-id="1e6ed-103">Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili</span><span class="sxs-lookup"><span data-stu-id="1e6ed-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e6ed-104">Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="1e6ed-105">Descrive le procedure consigliate per l'uso da parte di tecnici IT qualificati per la rimozione e la sostituzione di SSD nei seguenti dispositivi Surface compatibili:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="1e6ed-106">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="1e6ed-106">Surface Laptop 3</span></span> 
- <span data-ttu-id="1e6ed-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="1e6ed-107">Surface Pro X</span></span> 
- <span data-ttu-id="1e6ed-108">Portatile Surface go</span><span class="sxs-lookup"><span data-stu-id="1e6ed-108">Surface Laptop Go</span></span>

> [!WARNING]
> <span data-ttu-id="1e6ed-109">Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-109">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="1e6ed-110">Prestare sempre attenzione quando si intraprendono tali attività.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-110">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="1e6ed-111">Seguire le precauzioni e le procedure di sicurezza identificate nella [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-111">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="1e6ed-112">È consigliabile ottenere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="1e6ed-112">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="1e6ed-113">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="1e6ed-113">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1e6ed-114">In questo articolo si presuppone che siano presenti le condizioni generali per la sicurezza e i criteri e le procedure di sicurezza descritti nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="1e6ed-114">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="1e6ed-115">Preparare la rimozione di SSD</span><span class="sxs-lookup"><span data-stu-id="1e6ed-115">Prepare for SSD removal</span></span> 

### <span data-ttu-id="1e6ed-116">Installare gli aggiornamenti più recenti</span><span class="sxs-lookup"><span data-stu-id="1e6ed-116">Install the latest updates</span></span> 

<span data-ttu-id="1e6ed-117">Prima di iniziare, verificare che la versione di Windows in cui siano installati gli aggiornamenti più recenti:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-117">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="1e6ed-118">Andare a **Start**  >  **Settings**  >  **Update & Security**e selezionare **Controlla aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-118">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="1e6ed-119">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-119">Install all available updates.</span></span>
3. <span data-ttu-id="1e6ed-120">Verificare le password necessarie per accedere al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-120">Verify any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="1e6ed-121">Gestione BitLocker</span><span class="sxs-lookup"><span data-stu-id="1e6ed-121">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="1e6ed-122">Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-122">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="1e6ed-123">Per altre informazioni, vedere  [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-123">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="1e6ed-124">Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="1e6ed-124">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="1e6ed-125">Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-125">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="1e6ed-126">In **Impostazioni**digitare **BitLocker** , quindi selezionare **Gestisci BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-126">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="1e6ed-127">Selezionare **Disattiva BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-127">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="1e6ed-128">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-128">Power down the device.</span></span> 

### <span data-ttu-id="1e6ed-129">Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="1e6ed-129">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="1e6ed-130">Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-130">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="1e6ed-131">In **Impostazioni**digitare **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-131">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="1e6ed-132">Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-132">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="1e6ed-133">Inserire un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-133">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="1e6ed-134">Salvare la chiave di ripristino in archiviazione USB.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-134">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="1e6ed-135">Rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-135">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="1e6ed-136">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-136">Power down the device.</span></span> 

## <span data-ttu-id="1e6ed-137">Rimuovere e sostituire SSD</span><span class="sxs-lookup"><span data-stu-id="1e6ed-137">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="1e6ed-138">Rimuovere l'SSD usando le istruzioni in [Guida alla rimozione di Pierluigi per Enterprise](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-138">Remove the SSD by using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="1e6ed-139">Inserire l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-139">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="1e6ed-140">Accendere il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-140">Power on the new device.</span></span> <span data-ttu-id="1e6ed-141">Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-141">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="1e6ed-142">Dopo la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="1e6ed-142">After SSD removal and replacement</span></span>

### <span data-ttu-id="1e6ed-143">Gestire gli SSD non crittografati</span><span class="sxs-lookup"><span data-stu-id="1e6ed-143">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="1e6ed-144">Se durante il trasferimento l'SSD non è crittografato, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-144">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="1e6ed-145">Accedere alla **Sign-In Options**  >  **password** delle opzioni di accesso (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-145">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="1e6ed-146">Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-146">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="1e6ed-147">Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-147">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="1e6ed-148">Eseguire di nuovo l'accesso usando la password e configurare Windows Hello e un PIN quando viene richiesto.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-148">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="1e6ed-149">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-149">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="1e6ed-150">Eseguire [Microsoft Surface Diagnostic Toolkit for business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-150">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="1e6ed-151">Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  **Activation**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-151">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="1e6ed-152">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-152">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="1e6ed-153">Selezionare l'account di Office aprendo l' **app di Office**, passare all' **File**  >  **account** file e quindi verificare la ricerca di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-153">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="1e6ed-154">Gestione degli SSD crittografati</span><span class="sxs-lookup"><span data-stu-id="1e6ed-154">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="1e6ed-155">Sarà necessario disporre di un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-155">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="1e6ed-156">Se l'SSD viene crittografato durante il trasferimento, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="1e6ed-156">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="1e6ed-157">Inserire l'unità USB che contiene la chiave di ripristino di BitLocker nel secondo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-157">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="1e6ed-158">Aprire il file txt che contiene la chiave di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-158">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="1e6ed-159">Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-159">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="1e6ed-160">Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-160">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="1e6ed-161">Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-161">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="1e6ed-162">Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-162">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="1e6ed-163">Eseguire di nuovo l'accesso usando la password e quindi configurare Windows Hello e aggiungere un PIN.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-163">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="1e6ed-164">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e se si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-164">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="1e6ed-165">Eseguire **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-165">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="1e6ed-166">Per controllare l'attivazione di Windows **Settings**, selezionare  >  **attivazione**impostazioni.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-166">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="1e6ed-167">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-167">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="1e6ed-168">Per controllare lo stato dell'account di Office, aprire l' **app di Office**, quindi scegliere **File**  >  **account** file per verificare la disponibilità di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="1e6ed-168">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="1e6ed-169">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="1e6ed-169">Learn more</span></span>

- [<span data-ttu-id="1e6ed-170">Guida alla rimozione di Pierluigi per le aziende</span><span class="sxs-lookup"><span data-stu-id="1e6ed-170">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="1e6ed-171">Guida al ripristino di BitLocker</span><span class="sxs-lookup"><span data-stu-id="1e6ed-171">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="1e6ed-172">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="1e6ed-172">Still need help?</span></span> <span data-ttu-id="1e6ed-173">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="1e6ed-173">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
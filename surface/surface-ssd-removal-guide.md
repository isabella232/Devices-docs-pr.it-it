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
ms.date: 01/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 51ef676e7379f0898d6b601bb08c96002c9e6ace
ms.sourcegitcommit: d4e2a29aa21a911ee55642cd66b4337b89eebdd8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "11270631"
---
# <span data-ttu-id="2e0a6-103">Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili</span><span class="sxs-lookup"><span data-stu-id="2e0a6-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e0a6-104">Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="2e0a6-105">Descrive le procedure consigliate per l'uso da parte di tecnici IT qualificati per la rimozione e la sostituzione di SSD nei seguenti dispositivi Surface compatibili:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-105">It describes the recommended best practices for use by qualified IT technicians in the removal and replacement of SSDs in the following compatible Surface devices:</span></span> 

- <span data-ttu-id="2e0a6-106">Surface Pro 7 +</span><span class="sxs-lookup"><span data-stu-id="2e0a6-106">Surface Pro 7+</span></span>
- <span data-ttu-id="2e0a6-107">Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="2e0a6-107">Surface Pro X</span></span>
- <span data-ttu-id="2e0a6-108">Portatile Surface go</span><span class="sxs-lookup"><span data-stu-id="2e0a6-108">Surface Laptop Go</span></span>
- <span data-ttu-id="2e0a6-109">Laptop Surface 3</span><span class="sxs-lookup"><span data-stu-id="2e0a6-109">Surface Laptop 3</span></span>

> [!WARNING]
> <span data-ttu-id="2e0a6-110">Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-110">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="2e0a6-111">Prestare sempre attenzione quando si intraprendono tali attività.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-111">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="2e0a6-112">Seguire le precauzioni e le procedure di sicurezza identificate nella [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-112">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="2e0a6-113">È consigliabile ottenere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="2e0a6-113">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="2e0a6-114">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="2e0a6-114">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e0a6-115">In questo articolo si presuppone che siano presenti le condizioni generali per la sicurezza e i criteri e le procedure di sicurezza descritti nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="2e0a6-115">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="2e0a6-116">Preparare la rimozione di SSD</span><span class="sxs-lookup"><span data-stu-id="2e0a6-116">Prepare for SSD removal</span></span> 

### <span data-ttu-id="2e0a6-117">Installare gli aggiornamenti più recenti</span><span class="sxs-lookup"><span data-stu-id="2e0a6-117">Install the latest updates</span></span> 

<span data-ttu-id="2e0a6-118">Prima di iniziare, verificare che la versione di Windows in cui siano installati gli aggiornamenti più recenti:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-118">Before you begin, make sure that your version of Windows has the latest updates installed:</span></span>

1.  <span data-ttu-id="2e0a6-119">Andare a **Start**  >  **Settings**  >  **Update & Security**e selezionare **Controlla aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-119">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span>
2. <span data-ttu-id="2e0a6-120">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-120">Install all available updates.</span></span>
3. <span data-ttu-id="2e0a6-121">Verificare le password necessarie per accedere al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-121">Verify any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="2e0a6-122">Gestione BitLocker</span><span class="sxs-lookup"><span data-stu-id="2e0a6-122">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="2e0a6-123">Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-123">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="2e0a6-124">Per altre informazioni, vedere  [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-124">For more information, see  [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="2e0a6-125">Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="2e0a6-125">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="2e0a6-126">Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-126">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="2e0a6-127">In **Impostazioni**digitare **BitLocker** , quindi selezionare **Gestisci BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-127">In **Settings**, type **BitLocker** and then select **Manage BitLocker**.</span></span> 
2.  <span data-ttu-id="2e0a6-128">Selezionare **Disattiva BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-128">Select **Turn Off BitLocker**.</span></span> 
3.  <span data-ttu-id="2e0a6-129">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-129">Power down the device.</span></span> 

### <span data-ttu-id="2e0a6-130">Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="2e0a6-130">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="2e0a6-131">Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-131">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="2e0a6-132">In **Impostazioni**digitare **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-132">In **Settings**, type **BitLocker**.</span></span>
2. <span data-ttu-id="2e0a6-133">Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-133">Select **Manage BitLocker** >**Generate BitLocker Recovery Key**.</span></span>
2.  <span data-ttu-id="2e0a6-134">Inserire un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-134">Insert a USB drive.</span></span> 
4.  <span data-ttu-id="2e0a6-135">Salvare la chiave di ripristino in archiviazione USB.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-135">Save the recovery key to USB storage.</span></span>  
5.  <span data-ttu-id="2e0a6-136">Rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-136">Remove the USB drive.</span></span>  
6.  <span data-ttu-id="2e0a6-137">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-137">Power down the device.</span></span> 

## <span data-ttu-id="2e0a6-138">Rimuovere e sostituire SSD</span><span class="sxs-lookup"><span data-stu-id="2e0a6-138">Remove and replace SSD</span></span> 

1.  <span data-ttu-id="2e0a6-139">Rimuovere l'SSD usando le istruzioni appropriate per il dispositivo incluso nella [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-139">Remove the SSD by using the appropriate instructions for your device included in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2.  <span data-ttu-id="2e0a6-140">Inserire l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-140">Put the original SSD into a new device and connect the new device to a wired internet connection.</span></span>
3.  <span data-ttu-id="2e0a6-141">Accendere il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-141">Power on the new device.</span></span> <span data-ttu-id="2e0a6-142">Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-142">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="2e0a6-143">Dopo la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="2e0a6-143">After SSD removal and replacement</span></span>

### <span data-ttu-id="2e0a6-144">Gestire gli SSD non crittografati</span><span class="sxs-lookup"><span data-stu-id="2e0a6-144">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="2e0a6-145">Se durante il trasferimento l'SSD non è crittografato, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-145">If the SSD is unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="2e0a6-146">Accedere alla \*\*\*\*  >  **password** delle opzioni di accesso (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-146">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="2e0a6-147">Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-147">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="2e0a6-148">Dopo aver effettuato l'accesso completo, accedere all' \*\*\*\*  >  **account**Start  >  \*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-148">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="2e0a6-149">Eseguire di nuovo l'accesso usando la password e configurare Windows Hello e un PIN quando viene richiesto.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-149">Sign back in by using the password and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="2e0a6-150">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-150">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
6.  <span data-ttu-id="2e0a6-151">Eseguire [Microsoft Surface Diagnostic Toolkit for business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-151">Run the [Microsoft Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="2e0a6-152">Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  \*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-152">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="2e0a6-153">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-153">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="2e0a6-154">Selezionare l'account di Office aprendo l' **app di Office**, passare all' \*\*\*\*  >  **account** file e quindi verificare la ricerca di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-154">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="2e0a6-155">Gestione degli SSD crittografati</span><span class="sxs-lookup"><span data-stu-id="2e0a6-155">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="2e0a6-156">Sarà necessario disporre di un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-156">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="2e0a6-157">Se l'SSD viene crittografato durante il trasferimento, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="2e0a6-157">If the SSD is encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="2e0a6-158">Inserire l'unità USB che contiene la chiave di ripristino di BitLocker nel secondo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-158">Insert the USB drive that contains the BitLocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="2e0a6-159">Aprire il file txt che contiene la chiave di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-159">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="2e0a6-160">Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-160">Manually enter the BitLocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="2e0a6-161">Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  \*\*\*\* (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-161">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="2e0a6-162">Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-162">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="2e0a6-163">Dopo aver effettuato l'accesso completo, accedere all' \*\*\*\*  >  **account**Start  >  \*\*\*\*.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-163">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="2e0a6-164">Eseguire di nuovo l'accesso usando la password e quindi configurare Windows Hello e aggiungere un PIN.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-164">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="2e0a6-165">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e se si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-165">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **BitLocker** > **Manage BitLocker** > **Resume BitLocker**.</span></span>  
9.  <span data-ttu-id="2e0a6-166">Eseguire **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-166">Run **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** to verify full device functionality.</span></span>  
10. <span data-ttu-id="2e0a6-167">Per controllare l'attivazione di Windows \*\*\*\*, selezionare  >  **attivazione**impostazioni.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-167">To check Windows activation, select **Settings** > **Activation**.</span></span>  <span data-ttu-id="2e0a6-168">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-168">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="2e0a6-169">Per controllare lo stato dell'account di Office, aprire l' **app di Office**, quindi scegliere \*\*\*\*  >  **account** file per verificare la disponibilità di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="2e0a6-169">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="2e0a6-170">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="2e0a6-170">Learn more</span></span>

- [<span data-ttu-id="2e0a6-171">Guida alla rimozione di Pierluigi per le aziende</span><span class="sxs-lookup"><span data-stu-id="2e0a6-171">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="2e0a6-172">Guida al ripristino di BitLocker</span><span class="sxs-lookup"><span data-stu-id="2e0a6-172">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="2e0a6-173">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="2e0a6-173">Still need help?</span></span> <span data-ttu-id="2e0a6-174">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="2e0a6-174">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
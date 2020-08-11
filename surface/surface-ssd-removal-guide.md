---
title: Rimozione di SSD in dispositivi Surface compatibili
description: Come trasferire un SSD da un dispositivo Surface a un altro.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 8/7/2020
ms.reviewer: johnk
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 66860af06f4fad8f19ca26702350f19cc85ffef1
ms.sourcegitcommit: bad416f04c6877f2200f134a69146bb633155f22
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/10/2020
ms.locfileid: "10919225"
---
# <span data-ttu-id="51687-103">Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili</span><span class="sxs-lookup"><span data-stu-id="51687-103">Best practices for SSD removal from compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51687-104">Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale.</span><span class="sxs-lookup"><span data-stu-id="51687-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="51687-105">Descrive le procedure consigliate per l'uso da parte dei tecnici IT qualificati quando rimuove e sostituisce gli SSD in dispositivi di Surface con SSD rimovibili.</span><span class="sxs-lookup"><span data-stu-id="51687-105">It describes the recommended best practices for use by qualified IT technicians when they remove and replace SSDs in Surface devices that have removable SSDs.</span></span> 

> [!WARNING]
> <span data-ttu-id="51687-106">Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.</span><span class="sxs-lookup"><span data-stu-id="51687-106">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="51687-107">Prestare sempre attenzione quando si intraprendono tali attività.</span><span class="sxs-lookup"><span data-stu-id="51687-107">Always use caution when you undertake such activities.</span></span> <span data-ttu-id="51687-108">Seguire le precauzioni e le procedure di sicurezza identificate nella [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="51687-108">Follow the safety precautions and procedures that are identified in the [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> <span data-ttu-id="51687-109">È consigliabile ottenere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="51687-109">We recommend that you get professional assistance if you cannot follow the safety precautions and procedures that are specified in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="51687-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="51687-110">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51687-111">In questo articolo si presuppone che siano presenti le condizioni generali per la sicurezza e i criteri e le procedure di sicurezza descritti nella "Guida alla rimozione di Pierluigi per le aziende".</span><span class="sxs-lookup"><span data-stu-id="51687-111">This article assumes that you understand the General Safety Precautions and Safety policies and procedures that are described in the "rSSD Removal Guide for Enterprise."</span></span>

## <span data-ttu-id="51687-112">Preparare la rimozione di SSD</span><span class="sxs-lookup"><span data-stu-id="51687-112">Prepare for SSD removal</span></span> 

### <span data-ttu-id="51687-113">Installare gli aggiornamenti più recenti</span><span class="sxs-lookup"><span data-stu-id="51687-113">Install the latest updates</span></span> 

<span data-ttu-id="51687-114">Prima di iniziare, verificare che la versione di Windows abbia gli aggiornamenti più recenti intalled:</span><span class="sxs-lookup"><span data-stu-id="51687-114">Before you begin, make sure that your version of Windows has the latest updates intalled:</span></span>

1.  <span data-ttu-id="51687-115">Andare a **Start**  >  **Settings**  >  **Update & Security**e selezionare **Controlla aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="51687-115">Go to **Start** > **Settings** > **Update & Security**, and select **Check for updates**.</span></span> <span data-ttu-id="51687-116">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="51687-116">Install all available updates.</span></span> 
2. <span data-ttu-id="51687-117">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="51687-117">Install all available updates.</span></span>
3. <span data-ttu-id="51687-118">Verificare di avere le password necessarie per accedere al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-118">Verify that you have any passwords that are necessary to access the device.</span></span>  
 
## <span data-ttu-id="51687-119">Gestione BitLocker</span><span class="sxs-lookup"><span data-stu-id="51687-119">Manage BitLocker</span></span> 

> [!NOTE]
> <span data-ttu-id="51687-120">Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi.</span><span class="sxs-lookup"><span data-stu-id="51687-120">This section includes recommendations for organizations that have enabled BitLocker encryption for hard disks.</span></span> <span data-ttu-id="51687-121">Per altre informazioni, vedere la [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span><span class="sxs-lookup"><span data-stu-id="51687-121">For more information, see the [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="51687-122">Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="51687-122">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="51687-123">Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:</span><span class="sxs-lookup"><span data-stu-id="51687-123">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="51687-124">In **Impostazioni**digitare **BitLocker**, quindi selezionare **Gestisci BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="51687-124">In **Settings**, type **Bitlocker**, and then select **Manage Bitlocker**.</span></span> 
2.  <span data-ttu-id="51687-125">Selezionare **Disattiva BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="51687-125">Select **Turn Off Bitlocker**.</span></span> 
3.  <span data-ttu-id="51687-126">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-126">Power down the device.</span></span> 

### <span data-ttu-id="51687-127">Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="51687-127">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="51687-128">Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:</span><span class="sxs-lookup"><span data-stu-id="51687-128">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="51687-129">In **Impostazioni**digitare **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="51687-129">In **Settings**, type **Bitlocker**.</span></span>
2. <span data-ttu-id="51687-130">Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="51687-130">Select **Manage Bitlocker** >**Generate Bitlocker Recovery Key**.</span></span>
2.  <span data-ttu-id="51687-131">Inserire un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="51687-131">Insert a USB drive.</span></span> 
3.  <span data-ttu-id="51687-132">Salvare la chiave di ripristino in archiviazione USB.</span><span class="sxs-lookup"><span data-stu-id="51687-132">Save the recovery key to USB storage.</span></span>  
4.  <span data-ttu-id="51687-133">Rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="51687-133">Remove the USB drive.</span></span>  
5.  <span data-ttu-id="51687-134">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-134">Power down the device.</span></span> 

## <span data-ttu-id="51687-135">Rimuovere e sostituire l'SSD</span><span class="sxs-lookup"><span data-stu-id="51687-135">Remove and replace the SSD</span></span> 

1.  <span data-ttu-id="51687-136">Rimuovere l'SSD usando le istruzioni in [Guida alla rimozione di Pierluigi per Enterprise](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="51687-136">Remove the SSD by using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2. <span data-ttu-id="51687-137">Inserire l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.</span><span class="sxs-lookup"><span data-stu-id="51687-137">Put the original SSD into a new device, and connect the new device to a wired internet connection.</span></span>
2.  <span data-ttu-id="51687-138">Accendere il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-138">Power on the new device.</span></span> <span data-ttu-id="51687-139">Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.</span><span class="sxs-lookup"><span data-stu-id="51687-139">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="51687-140">Dopo la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="51687-140">After SSD removal and replacement</span></span>

### <span data-ttu-id="51687-141">Gestire gli SSD non crittografati</span><span class="sxs-lookup"><span data-stu-id="51687-141">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="51687-142">Se l'SSD rimane non crittografato durante il trasferimento, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="51687-142">If the SSD remains unencrypted during the transfer, follow these steps:</span></span> 

1.  <span data-ttu-id="51687-143">Accedere alla **Sign-In Options**  >  **password** delle opzioni di accesso (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="51687-143">Go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
2.  <span data-ttu-id="51687-144">Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="51687-144">Enter the password, and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="51687-145">Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="51687-145">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="51687-146">Eseguire di nuovo l'accesso usando la password e configurare Windows Hello e un PIN quando viene richiesto.</span><span class="sxs-lookup"><span data-stu-id="51687-146">Sign back in by using the password, and set up Windows Hello and a PIN when you are prompted.</span></span> 
    - <span data-ttu-id="51687-147">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.</span><span class="sxs-lookup"><span data-stu-id="51687-147">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
6.  <span data-ttu-id="51687-148">Eseguire Microsoft Surface Diagnostic Toolkit for business (SDT) per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-148">Run the Microsoft Surface Diagnostic Toolkit for Business (SDT) to verify full device functionality.</span></span>  
7.  <span data-ttu-id="51687-149">Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  **Activation**.</span><span class="sxs-lookup"><span data-stu-id="51687-149">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="51687-150">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="51687-150">If you see any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="51687-151">Selezionare l'account di Office aprendo l' **app di Office**, passare all' **File**  >  **account** file e quindi verificare la ricerca di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="51687-151">Check the Office account by opening the **Office App**, navigate to **File** > **Account** and then check for any error messages.</span></span>  

### <span data-ttu-id="51687-152">Gestione degli SSD crittografati</span><span class="sxs-lookup"><span data-stu-id="51687-152">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="51687-153">Sarà necessario disporre di un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="51687-153">You will have to have a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="51687-154">Se l'SSD è rimasto crittografato durante il trasferimento, eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="51687-154">If the SSD remained encrypted during the transfer, follow these steps:</span></span>

1.  <span data-ttu-id="51687-155">Inserire l'unità USB che contiene la chiave di ripristino di BitLocker nel secondo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-155">Insert the USB drive that contains the Bitlocker recovery key into the second device.</span></span> 
2.  <span data-ttu-id="51687-156">Aprire il file txt che contiene la chiave di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="51687-156">Open the .txt file that contains the Bitlocker recovery key.</span></span> 
3.  <span data-ttu-id="51687-157">Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.</span><span class="sxs-lookup"><span data-stu-id="51687-157">Manually enter the Bitlocker recovery key on the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="51687-158">Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="51687-158">After you have successfully entered the BitLocker recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="51687-159">Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="51687-159">Enter the password and sign in, pending completion of two-factor authentication (if applicable).</span></span>
6.  <span data-ttu-id="51687-160">Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="51687-160">After you are fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="51687-161">Eseguire di nuovo l'accesso usando la password e quindi configurare Windows Hello e aggiungere un PIN.</span><span class="sxs-lookup"><span data-stu-id="51687-161">Sign back in by using the password, and then set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="51687-162">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e se si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="51687-162">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and if you want to enable BitLocker after the replacement, go to **Settings** > **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
9.  <span data-ttu-id="51687-163">Eseguire **SDT** per verificare la funzionalità completa del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="51687-163">Run **SDT** to verify full device functionality.</span></span>  
10. <span data-ttu-id="51687-164">Controlla l'attivazione di Windows passando all' **attivazione delle impostazioni**  >  **Activation**.</span><span class="sxs-lookup"><span data-stu-id="51687-164">Check Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="51687-165">Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="51687-165">If you see any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="51687-166">Per controllare lo stato dell'account di Office, aprire l' **app di Office**, quindi scegliere **File**  >  **account** file per verificare la disponibilità di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="51687-166">To check the status of the Office account, open the **Office App**, then go to **File** > **Account** to check for any error messages.</span></span>

## <span data-ttu-id="51687-167">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="51687-167">More information</span></span> 

<span data-ttu-id="51687-168">Per informazioni, vedi gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="51687-168">For more information, see the following articles:</span></span>

- [<span data-ttu-id="51687-169">Guida alla rimozione di Pierluigi per le aziende</span><span class="sxs-lookup"><span data-stu-id="51687-169">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="51687-170">Guida al ripristino di BitLocker</span><span class="sxs-lookup"><span data-stu-id="51687-170">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="51687-171">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="51687-171">Still need help?</span></span> <span data-ttu-id="51687-172">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="51687-172">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
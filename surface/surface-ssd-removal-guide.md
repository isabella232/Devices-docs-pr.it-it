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
ms.openlocfilehash: 9cde08c8106703b50218bf7f5ed60e3d7fea0b67
ms.sourcegitcommit: 83530906c7e34c92bbee90b723321acd61e77669
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2020
ms.locfileid: "10918961"
---
# <span data-ttu-id="63ee2-103">Procedure consigliate per la rimozione di SSD in dispositivi Surface compatibili</span><span class="sxs-lookup"><span data-stu-id="63ee2-103">Best practices for SSD removal in compatible Surface devices</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63ee2-104">Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale.</span><span class="sxs-lookup"><span data-stu-id="63ee2-104">This article is intended for use by qualified IT technicians in an enterprise organization only.</span></span> <span data-ttu-id="63ee2-105">Descrive le procedure consigliate per l'uso da parte di tecnici IT qualificati per la rimozione e la sostituzione di SSD in dispositivi Surface con SSD rimovibili.</span><span class="sxs-lookup"><span data-stu-id="63ee2-105">It describes the recommended best practices for use by qualified IT technicians when removing and replacing SSDs in Surface devices with removable SSDs.</span></span> 

> [!WARNING]
> <span data-ttu-id="63ee2-106">Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.</span><span class="sxs-lookup"><span data-stu-id="63ee2-106">Opening devices and replacing device components can present electric shock, device damage, fire, and personal injury risks, and other hazards.</span></span>  <span data-ttu-id="63ee2-107">Usare sempre cautela quando si intraprende tali attività.</span><span class="sxs-lookup"><span data-stu-id="63ee2-107">Always use caution when undertaking such activities.</span></span> <span data-ttu-id="63ee2-108">Seguire le precauzioni e le procedure di sicurezza identificate nella Guida alla rimozione di Pierluigi per le aziende.</span><span class="sxs-lookup"><span data-stu-id="63ee2-108">Follow the safety precautions and procedures identified in the rSSD Removal Guide for Enterprise.</span></span> <span data-ttu-id="63ee2-109">Microsoft consiglia di richiedere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella Guida alla rimozione di Pierluigi per le aziende.</span><span class="sxs-lookup"><span data-stu-id="63ee2-109">Microsoft recommends that you seek professional assistance if you are unable to follow the safety precautions and procedures specified in the rSSD Removal Guide for Enterprise.</span></span> 

## <span data-ttu-id="63ee2-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="63ee2-110">Prerequisites</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63ee2-111">In questo articolo si presuppone la comprensione delle precauzioni generali e delle procedure di sicurezza descritte in [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="63ee2-111">This article assumes you understand the General Safety Precautions and Safety policies and procedures described in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span>

## <span data-ttu-id="63ee2-112">Preparare la rimozione di SSD</span><span class="sxs-lookup"><span data-stu-id="63ee2-112">Prepare for SSD removal</span></span> 

### <span data-ttu-id="63ee2-113">Installare gli aggiornamenti più recenti</span><span class="sxs-lookup"><span data-stu-id="63ee2-113">Install the latest updates</span></span> 

<span data-ttu-id="63ee2-114">Prima di iniziare, verificare che la versione di Windows contenga gli aggiornamenti più recenti.</span><span class="sxs-lookup"><span data-stu-id="63ee2-114">Before you begin, make sure your version of Windows has the latest updates.</span></span>

1.  <span data-ttu-id="63ee2-115">Andare a **Start**  >  **Settings**  >  **Update & Security** e selezionare **Controlla aggiornamenti**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-115">Go to **Start** > **Settings** > **Update & Security** and select **Check for updates**.</span></span> <span data-ttu-id="63ee2-116">Installare tutti gli aggiornamenti disponibili.</span><span class="sxs-lookup"><span data-stu-id="63ee2-116">Install all available updates.</span></span>  

2.  <span data-ttu-id="63ee2-117">Verificare di avere le password necessarie per accedere al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-117">Confirm that you have any passwords needed to access the device.</span></span>  
 
## <span data-ttu-id="63ee2-118">Gestire BitLocker</span><span class="sxs-lookup"><span data-stu-id="63ee2-118">Manage Bitlocker</span></span> 

> [!NOTE]
> <span data-ttu-id="63ee2-119">Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi.</span><span class="sxs-lookup"><span data-stu-id="63ee2-119">This section includes recommendations for organizations that have enabled BitLocker encryption for hard drives.</span></span> <span data-ttu-id="63ee2-120">Per altre informazioni, vedere la [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span><span class="sxs-lookup"><span data-stu-id="63ee2-120">For more information, see the [BitLocker Recovery Guide](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).</span></span> 

### <span data-ttu-id="63ee2-121">Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="63ee2-121">If BitLocker encryption is disabled during SSD removal and replacement</span></span>

<span data-ttu-id="63ee2-122">Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:</span><span class="sxs-lookup"><span data-stu-id="63ee2-122">If the device can be unencrypted before SSD removal and replacement, follow these steps to turn off BitLocker:</span></span>

1.  <span data-ttu-id="63ee2-123">In **Impostazioni**digitare **BitLocker** e selezionare **Gestisci BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-123">In **Settings**, type **Bitlocker** and select **Manage Bitlocker**.</span></span> 
2.  <span data-ttu-id="63ee2-124">Selezionare **Disattiva BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-124">Select **Turn Off Bitlocker**.</span></span> 
3.  <span data-ttu-id="63ee2-125">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-125">Power down the device.</span></span> 

### <span data-ttu-id="63ee2-126">Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="63ee2-126">If BitLocker encryption is enabled during SSD removal and replacement</span></span>

<span data-ttu-id="63ee2-127">Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:</span><span class="sxs-lookup"><span data-stu-id="63ee2-127">If the device is encrypted before SSD removal and replacement, follow these steps to generate a BitLocker recovery key and save it to USB storage:</span></span>

1.  <span data-ttu-id="63ee2-128">Accedere a **Impostazioni** e digitare **BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-128">Go to **Settings** and type **Bitlocker**.</span></span>
2. <span data-ttu-id="63ee2-129">Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-129">Select **Manage Bitlocker** >**Generate Bitlocker Recovery Key**.</span></span>
2.  <span data-ttu-id="63ee2-130">Inserire un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="63ee2-130">Insert a USB drive.</span></span> 
3.  <span data-ttu-id="63ee2-131">Salvare la chiave di ripristino in archiviazione USB.</span><span class="sxs-lookup"><span data-stu-id="63ee2-131">Save the recovery key to USB storage.</span></span>  
4.  <span data-ttu-id="63ee2-132">Rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="63ee2-132">Remove the USB drive.</span></span>  
5.  <span data-ttu-id="63ee2-133">Spegnere il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-133">Power down the device.</span></span> 

## <span data-ttu-id="63ee2-134">Rimuovere e sostituire l'SSD</span><span class="sxs-lookup"><span data-stu-id="63ee2-134">Remove and replace the SSD</span></span> 

1.  <span data-ttu-id="63ee2-135">Rimuovere l'SSD usando le istruzioni nella [Guida alla rimozione di Pierluigi per Enterprise](https://www.microsoft.com/download/100440).</span><span class="sxs-lookup"><span data-stu-id="63ee2-135">Remove the SSD using the instructions in [rSSD Removal Guide for Enterprise](https://www.microsoft.com/download/100440).</span></span> 
2. <span data-ttu-id="63ee2-136">Posizionare l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.</span><span class="sxs-lookup"><span data-stu-id="63ee2-136">Place the original SSD in a new device and connect the new device to a wired internet connection.</span></span>
2.  <span data-ttu-id="63ee2-137">Accendere il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-137">Power on the new device.</span></span> <span data-ttu-id="63ee2-138">Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.</span><span class="sxs-lookup"><span data-stu-id="63ee2-138">The device may go through a firmware update during startup.</span></span>  
 
## <span data-ttu-id="63ee2-139">Dopo la rimozione e la sostituzione di SSD</span><span class="sxs-lookup"><span data-stu-id="63ee2-139">After SSD removal and replacement</span></span>

### <span data-ttu-id="63ee2-140">Gestire gli SSD non crittografati</span><span class="sxs-lookup"><span data-stu-id="63ee2-140">Manage unencrypted SSDs</span></span> 

<span data-ttu-id="63ee2-141">Se l'SSD rimane non crittografato durante il trasferimento, completare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="63ee2-141">If the SSD remains unencrypted during the transfer, complete the following:</span></span> 

1.  <span data-ttu-id="63ee2-142">Accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata come icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="63ee2-142">Go to **Sign-In Options** > **Password** (represented as the key icon on the left side).</span></span>  
2.  <span data-ttu-id="63ee2-143">Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).</span><span class="sxs-lookup"><span data-stu-id="63ee2-143">Enter the password and sign in pending completion of two-factor authentication (if applicable).</span></span>
3.  <span data-ttu-id="63ee2-144">Una volta completata l'accesso, accedere **Start**all'  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-144">Once fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
4.  <span data-ttu-id="63ee2-145">Eseguire di nuovo l'accesso con la password e configurare Windows Hello e un PIN quando richiesto.</span><span class="sxs-lookup"><span data-stu-id="63ee2-145">Sign back in with the password and set up Windows Hello and a PIN when prompted.</span></span> 
    - <span data-ttu-id="63ee2-146">Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.</span><span class="sxs-lookup"><span data-stu-id="63ee2-146">If the device was BitLocker-disabled to facilitate SSD removal and replacement and you want to enable BitLocker after the replacement, go to **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
6.  <span data-ttu-id="63ee2-147">Eseguire **SDT** per confermare la funzionalità del dispositivo completo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-147">Run **SDT** to confirm full device functionality.</span></span>  
7.  <span data-ttu-id="63ee2-148">Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  **Activation**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-148">Check for Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="63ee2-149">Se sono presenti messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-149">If there are any error messages, select **Troubleshoot**.</span></span> 
8.  <span data-ttu-id="63ee2-150">Selezionare l'account di Office aprendo l' **app di Office**, quindi passare **File**all'  >  **account** file e verificare la ricerca di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="63ee2-150">Check the Office account by opening the **Office App**, then navigate to **File** > **Account** and check for any error messages.</span></span>  

### <span data-ttu-id="63ee2-151">Gestione degli SSD crittografati</span><span class="sxs-lookup"><span data-stu-id="63ee2-151">Managing encrypted SSDs</span></span> 

> [!NOTE]
> <span data-ttu-id="63ee2-152">Sarà necessario un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="63ee2-152">You will need a second device to read the BitLocker Recovery key that was saved on the USB drive.</span></span> 

<span data-ttu-id="63ee2-153">Se l'SSD è rimasto crittografato durante il trasferimento, completare le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="63ee2-153">If the SSD remained encrypted during the transfer, complete the following:</span></span>

1.  <span data-ttu-id="63ee2-154">Inserire l'unità USB contenente la chiave di ripristino di BitLocker nel secondo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-154">Insert the USB drive containing the Bitlocker Recovery key into the second device.</span></span> 
2.  <span data-ttu-id="63ee2-155">Aprire il file txt contenente la chiave di ripristino di BitLocker.</span><span class="sxs-lookup"><span data-stu-id="63ee2-155">Open the .txt file containing the Bitlocker Recovery key.</span></span> 
3.  <span data-ttu-id="63ee2-156">Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.</span><span class="sxs-lookup"><span data-stu-id="63ee2-156">Manually enter the Bitlocker Recovery key into the new device that contains the original SSD.</span></span>  
4.  <span data-ttu-id="63ee2-157">Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata dall'icona chiave sul lato sinistro).</span><span class="sxs-lookup"><span data-stu-id="63ee2-157">After you have successfully entered the BitLocker Recovery key, go to **Sign-In Options** > **Password** (represented by the key icon on the left side).</span></span>  
5.  <span data-ttu-id="63ee2-158">Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile)</span><span class="sxs-lookup"><span data-stu-id="63ee2-158">Enter the password and sign in, pending completion of two-factor authentication (if applicable)</span></span> 
6.  <span data-ttu-id="63ee2-159">Una volta completata l'accesso, accedere **Start**all'  >  **account**Start  >  **Sign out**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-159">Once fully signed in, go to **Start** > **Account** > **Sign out**.</span></span>  
7.  <span data-ttu-id="63ee2-160">Accedere di nuovo con la password e configurare Windows Hello e aggiungere un PIN.</span><span class="sxs-lookup"><span data-stu-id="63ee2-160">Sign back in with the password and set up Windows Hello and add a PIN.</span></span> 
8.  <span data-ttu-id="63ee2-161">Se il dispositivo è stato disabilitato da BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-161">If the device was BitLocker-disabled to facilitate SSD removal and replacement, and you want to enable BitLocker after the replacement, go to to **Settings** > **Bitlocker** > **Manage Bitlocker** > **Resume Bitlocker**.</span></span>  
9.  <span data-ttu-id="63ee2-162">Eseguire **SDT** per confermare la funzionalità del dispositivo completo.</span><span class="sxs-lookup"><span data-stu-id="63ee2-162">Run **SDT** to confirm full device functionality.</span></span>  
10. <span data-ttu-id="63ee2-163">Controlla l'attivazione di Windows passando all' **attivazione delle impostazioni**  >  **Activation**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-163">Check Windows activation by navigating to **Settings** > **Activation**.</span></span>  <span data-ttu-id="63ee2-164">Se sono presenti messaggi di errore, selezionare **risoluzione dei problemi**.</span><span class="sxs-lookup"><span data-stu-id="63ee2-164">If there are any error messages, select **Troubleshoot**.</span></span>
11. <span data-ttu-id="63ee2-165">Per controllare l'account di Office, aprire l' **app di Office**, quindi selezionare l'account **file**  >  **Account** e verificare la ricerca di eventuali messaggi di errore.</span><span class="sxs-lookup"><span data-stu-id="63ee2-165">To check the Office Account, open the **Office App**, then go to **File** > **Account** and check for any error messages.</span></span>

## <span data-ttu-id="63ee2-166">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="63ee2-166">More information</span></span> 

<span data-ttu-id="63ee2-167">Per informazioni, vedi gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="63ee2-167">For more information, see the following articles:</span></span>

- [<span data-ttu-id="63ee2-168">Guida alla rimozione di Pierluigi per le aziende</span><span class="sxs-lookup"><span data-stu-id="63ee2-168">rSSD Removal Guide for Enterprise</span></span>](https://www.microsoft.com/download/100440)
- [<span data-ttu-id="63ee2-169">Guida al ripristino di BitLocker</span><span class="sxs-lookup"><span data-stu-id="63ee2-169">BitLocker Recovery Guide</span></span>](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

<span data-ttu-id="63ee2-170">Hai ancora bisogno di assistenza?</span><span class="sxs-lookup"><span data-stu-id="63ee2-170">Still need help?</span></span> <span data-ttu-id="63ee2-171">Accedere alla [community Microsoft](https://answers.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="63ee2-171">Go to [Microsoft Community](https://answers.microsoft.com/).</span></span>
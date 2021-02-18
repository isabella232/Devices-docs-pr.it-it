---
title: Ripristino e ripristino per Surface Hub 2S
description: Scopri come ripristinare e reimpostare Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/05/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 64ceee291d3d3e067f581707d9431fa92398c785
ms.sourcegitcommit: ecb4909c091e69b7bdb1faacfc8c34b480dc884b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/17/2021
ms.locfileid: "11342976"
---
# <span data-ttu-id="f9747-104">Ripristino e ripristino per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="f9747-104">Reset and recovery for Surface Hub 2S</span></span>

<span data-ttu-id="f9747-105">Se si verificano problemi con Surface Hub 2S, puoi ripristinare le impostazioni predefinite del dispositivo usando un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="f9747-105">If you encounter problems with Surface Hub 2S, you can reset the device to factory settings or restore by using a USB drive.</span></span>

<span data-ttu-id="f9747-106">Per iniziare, accedi a Surface Hub 2S con \*\*\*\* le credenziali di amministratore, apri l'app Impostazioni, seleziona Aggiornamento **& sicurezza**e quindi **seleziona Ripristino.**</span><span class="sxs-lookup"><span data-stu-id="f9747-106">To begin, sign in to Surface Hub 2S with admin credentials, open the **Settings** app, select **Update & security**, and then select **Recovery**.</span></span>

## <span data-ttu-id="f9747-107">Reimpostare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="f9747-107">Reset the device</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="f9747-108">Assicurati di avere a disposizione la chiave BitLocker prima di reimpostare il dispositivo, come ti verrà richiesto in seguito.</span><span class="sxs-lookup"><span data-stu-id="f9747-108">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="f9747-109">Per altre informazioni, vedi [Salvare la chiave BitLocker.](save-bitlocker-key-surface-hub.md)</span><span class="sxs-lookup"><span data-stu-id="f9747-109">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

1. <span data-ttu-id="f9747-110">Per reimpostare il dispositivo, selezionare **Introduzione.**</span><span class="sxs-lookup"><span data-stu-id="f9747-110">To reset the device, select **Get Started**.</span></span>

2. <span data-ttu-id="f9747-111">Quando viene **visualizzata la finestra Pronto per la** reimpostazione del dispositivo, selezionare **Reimposta.**</span><span class="sxs-lookup"><span data-stu-id="f9747-111">When the **Ready to reset this device** window appears, select **Reset**.</span></span> 
  
   > [!IMPORTANT]
   > <span data-ttu-id="f9747-112">Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="f9747-112">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="f9747-113">Se si ignora tale richiesta, il ripristino avrà esito negativo.</span><span class="sxs-lookup"><span data-stu-id="f9747-113">Skipping that prompt will cause reset to fail.</span></span> <span data-ttu-id="f9747-114">Una volta immessa la chiave BitLocker, l'hub reinstalla il sistema operativo dalla partizione di ripristino.</span><span class="sxs-lookup"><span data-stu-id="f9747-114">Once you enter the BitLocker key the Hub reinstalls the operating system from the recovery partition.</span></span> <span data-ttu-id="f9747-115">Il completamento dell'operazione potrebbe richiedere fino a un'ora.</span><span class="sxs-lookup"><span data-stu-id="f9747-115">This may take up to one hour to complete.</span></span>
  
3. <span data-ttu-id="f9747-116">Per riconfigurare il dispositivo, eseguire il programma di installazione della prima volta.</span><span class="sxs-lookup"><span data-stu-id="f9747-116">To reconfigure the device, run the first-time Setup program.</span></span>

4. <span data-ttu-id="f9747-117">Se si gestisce il dispositivo con Microsoft Intune o un'altra soluzione di gestione dei dispositivi mobili, ritirare ed eliminare il record precedente e quindi registrare di nuovo il nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f9747-117">If you manage the device using Microsoft Intune or another mobile device management solution, retire and delete the previous record, and then re-enroll the new device.</span></span> <span data-ttu-id="f9747-118">Per altre informazioni, vedi [Rimuovere i dispositivi tramite cancellazione,](https://docs.microsoft.com/intune/devices-wipe)ritiro o annullamento manuale della registrazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="f9747-118">For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/devices-wipe).</span></span>

   > [!div class="mx-imgBorder"]
   > ![*Ripristino e ripristino per Surface Hub 2S*](images/sh2-reset.png)
   <br/>*<span data-ttu-id="f9747-120">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="f9747-120">Figure 1.</span></span> <span data-ttu-id="f9747-121">Ripristino e ripristino per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="f9747-121">Reset and recovery for Surface Hub 2S</span></span>* 

## <span data-ttu-id="f9747-122">Ripristinare Surface Hub 2S usando un'unità di ripristino USB</span><span class="sxs-lookup"><span data-stu-id="f9747-122">Recover Surface Hub 2S by using a USB recovery drive</span></span>

<span data-ttu-id="f9747-123">Novità di Surface Hub 2S, ora puoi reinstallare il dispositivo usando un'immagine di ripristino.</span><span class="sxs-lookup"><span data-stu-id="f9747-123">New in Surface Hub 2S, you can now reinstall the device by using a recovery image.</span></span>

### <span data-ttu-id="f9747-124">Ripristino da un'unità USB</span><span class="sxs-lookup"><span data-stu-id="f9747-124">Recovery from a USB drive</span></span>

<span data-ttu-id="f9747-125">Con Surface Hub 2S puoi reinstallare il dispositivo usando un'immagine di ripristino.</span><span class="sxs-lookup"><span data-stu-id="f9747-125">Using Surface Hub 2S, you can reinstall the device by using a recovery image.</span></span> <span data-ttu-id="f9747-126">In questo modo, puoi reinstallare il dispositivo nelle impostazioni di fabbrica se hai perso la chiave BitLocker o se non hai più le credenziali di amministratore per l'app Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="f9747-126">By doing this, you can reinstall the device to the factory settings if you lost the BitLocker key, or if you no longer have admin credentials to the Settings app.</span></span>

>[!NOTE]
><span data-ttu-id="f9747-127">Usa un'unità USB 3.0 con 8 GB o 16 GB di spazio di archiviazione, formattato come FAT32.</span><span class="sxs-lookup"><span data-stu-id="f9747-127">Use a USB 3.0 drive with 8 GB or 16 GB of storage, formatted as FAT32.</span></span>

1. <span data-ttu-id="f9747-128">Da un PC separato, scarica l'immagine di ripristino del file ZIP dal sito [Web di Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) e quindi torna a queste istruzioni.</span><span class="sxs-lookup"><span data-stu-id="f9747-128">From a separate PC, download the .zip file recovery image from the [Surface Recovery website](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) and then return to these instructions.</span></span> 

1. <span data-ttu-id="f9747-129">Nella casella di ricerca sulla barra delle applicazioni immetti l'unità di ripristino **e**quindi seleziona Crea un'unità di **ripristino** o **Un'unità** di ripristino dai risultati.</span><span class="sxs-lookup"><span data-stu-id="f9747-129">In the search box on the taskbar, enter **recovery drive**, and then select **Create a recovery drive** or **Recovery Drive** from the results.</span></span> <span data-ttu-id="f9747-130">Potrebbe essere necessario immettere una password di amministratore o confermare la scelta.</span><span class="sxs-lookup"><span data-stu-id="f9747-130">You may need to enter an admin password or confirm your choice.</span></span>

1. <span data-ttu-id="f9747-131">Nella casella **Controllo account utente** selezionare **Sì.**</span><span class="sxs-lookup"><span data-stu-id="f9747-131">In the **User Account Control** box, select **Yes**.</span></span>

1. <span data-ttu-id="f9747-132">Assicurarsi di deselezionare la casella di controllo Backup dei file di **sistema nell'unità** di ripristino e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="f9747-132">Make sure to clear the **Back up system files to the recovery drive** check box and then select **Next**.</span></span>

1. <span data-ttu-id="f9747-133">Seleziona l'unità USB e quindi seleziona **Avanti > crea.**</span><span class="sxs-lookup"><span data-stu-id="f9747-133">Select your USB drive, and then select **Next > Create**.</span></span>  <span data-ttu-id="f9747-134">Alcune utilità devono essere copiate nell'unità di ripristino, pertanto l'operazione potrebbe richiedere alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="f9747-134">Some utilities need to be copied to the recovery drive, so this might take a few minutes.</span></span>

1. <span data-ttu-id="f9747-135">Quando l'unità di ripristino è pronta, selezionare **Fine.**</span><span class="sxs-lookup"><span data-stu-id="f9747-135">When the recovery drive is ready, select **Finish**.</span></span>

1. <span data-ttu-id="f9747-136">Fare doppio clic sul file ZIP dell'immagine di ripristino precedentemente scaricato per aprirlo.</span><span class="sxs-lookup"><span data-stu-id="f9747-136">Double-click the recovery image .zip file that you previously downloaded to open it.</span></span>

1. <span data-ttu-id="f9747-137">Seleziona tutti i file dalla cartella dell'immagine di ripristino, copiali nella radice dell'unità USB e quindi seleziona Scegli di sostituire i **file nella destinazione.**</span><span class="sxs-lookup"><span data-stu-id="f9747-137">Select all the files from the recovery image folder, copy them to the root of your USB drive, and then select **Choose to replace the files in the destination**.</span></span>

1. <span data-ttu-id="f9747-138">Dopo aver completato la copia dei file, seleziona l'icona Rimuovi hardware ed **eject media** in modo sicuro sulla barra delle applicazioni e rimuovi l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="f9747-138">Once the files have finished copying, select the **Safely Remove Hardware and Eject Media** icon on the taskbar, and remove your USB drive.</span></span>

1. <span data-ttu-id="f9747-139">Connetti l'unità USB a qualsiasi porta USB-C o USB-A in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="f9747-139">Connect the USB drive to any USB-C or USB-A port on the Surface Hub 2S.</span></span>

1. <span data-ttu-id="f9747-140">Disattiva l'hub e quindi prendi questi passaggi per eseguire l'avvio dall'unità USB:</span><span class="sxs-lookup"><span data-stu-id="f9747-140">Turn off the Hub and then take these steps to boot from the USB drive:</span></span>

   1. <span data-ttu-id="f9747-141">Mentre premi il pulsante Volume down, premi il pulsante Di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="f9747-141">While pressing the Volume down button, press the Power button.</span></span>
   1. <span data-ttu-id="f9747-142">Continua a premere entrambi i pulsanti finché non viene visualizzato il logo Windows.</span><span class="sxs-lookup"><span data-stu-id="f9747-142">Keep pressing both buttons until you see the Windows logo.</span></span>
   1. <span data-ttu-id="f9747-143">Rilascia il pulsante di alimentazione, ma continua a tenere premuto il pulsante Volume down fino all'inizio dell'interfaccia utente di installazione.</span><span class="sxs-lookup"><span data-stu-id="f9747-143">Release the Power button but continue to hold the Volume down button until the Install UI begins.</span></span>

      ![*Usare i pulsanti di accensione e di interruzione del volume per avviare il ripristino*](images/sh2-keypad.png)
      <br>*<span data-ttu-id="f9747-145">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="f9747-145">Figure 2.</span></span> <span data-ttu-id="f9747-146">Pulsanti volume e alimentazione</span><span class="sxs-lookup"><span data-stu-id="f9747-146">Volume and Power buttons</span></span>*

1. <span data-ttu-id="f9747-147">Nella schermata di selezione della lingua seleziona la lingua di visualizzazione per il dispositivo Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="f9747-147">On the language selection screen, select the display language for your Surface Hub 2S.</span></span>

1. <span data-ttu-id="f9747-148">Selezionare **Recupera da un'unità** e **Pulire completamente l'unità,** quindi selezionare **Recupera.**</span><span class="sxs-lookup"><span data-stu-id="f9747-148">Select **Recover from a drive** and **Fully clean the drive**, and then select **Recover**.</span></span> <span data-ttu-id="f9747-149">Se ti viene richiesto di specificare una chiave BitLocker, seleziona **Ignora questa unità.**</span><span class="sxs-lookup"><span data-stu-id="f9747-149">If you're prompted for a BitLocker key, select **Skip this drive**.</span></span> <span data-ttu-id="f9747-150">Surface Hub 2S viene riavviato più volte e richiede circa 30 minuti per completare il processo di ripristino.</span><span class="sxs-lookup"><span data-stu-id="f9747-150">Surface Hub 2S reboots several times and takes approximately 30 minutes to complete the recovery process.</span></span>

<span data-ttu-id="f9747-151">Quando viene visualizzata la prima schermata di configurazione, rimuovi l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="f9747-151">When the first-time setup screen appears, remove the USB drive.</span></span>

## <span data-ttu-id="f9747-152">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="f9747-152">Contact Support</span></span>

<span data-ttu-id="f9747-153">Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto.](https://support.microsoft.com/supportforbusiness/productselection)</span><span class="sxs-lookup"><span data-stu-id="f9747-153">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>

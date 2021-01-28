---
title: Reset e ripristino per Surface Hub 2S
description: Informazioni su come recuperare e ripristinare Surface Hub 2S.
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
ms.openlocfilehash: 88f5d912f7505aecaa5bd7ba659acab2d6c4fa1a
ms.sourcegitcommit: 25b8d880c6438f94b008f47b4fecc3aa4c473e85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/28/2021
ms.locfileid: "11304809"
---
# <span data-ttu-id="0330e-104">Reset e ripristino per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="0330e-104">Reset and recovery for Surface Hub 2S</span></span>

<span data-ttu-id="0330e-105">Se si verificano problemi con Surface Hub 2S, è possibile reimpostare il dispositivo in base alle impostazioni di fabbrica o ripristinarlo usando un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="0330e-105">If you encounter problems with Surface Hub 2S, you can reset the device to factory settings or restore by using a USB drive.</span></span>

<span data-ttu-id="0330e-106">Per iniziare, accedi a Surface Hub 2S con le credenziali di amministratore, Apri l'app **Impostazioni** , seleziona **Aggiorna & sicurezza**e quindi seleziona **ripristino**.</span><span class="sxs-lookup"><span data-stu-id="0330e-106">To begin, sign in to Surface Hub 2S with admin credentials, open the **Settings** app, select **Update & security**, and then select **Recovery**.</span></span>

## <span data-ttu-id="0330e-107">Reimpostare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="0330e-107">Reset the device</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="0330e-108">Verificare di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, dato che verrà richiesto in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="0330e-108">Ensure that you have your BitLocker key available before resetting the device, as you will be prompted for it later.</span></span> <span data-ttu-id="0330e-109">Per altre informazioni, vedere [salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md).</span><span class="sxs-lookup"><span data-stu-id="0330e-109">To learn more, see [Save your BitLocker key](save-bitlocker-key-surface-hub.md).</span></span>

1. <span data-ttu-id="0330e-110">Per reimpostare il dispositivo, selezionare **inizia**.</span><span class="sxs-lookup"><span data-stu-id="0330e-110">To reset the device, select **Get Started**.</span></span>

2. <span data-ttu-id="0330e-111">Quando viene visualizzata la finestra **pronto per reimpostare il dispositivo** , selezionare **Reimposta**.</span><span class="sxs-lookup"><span data-stu-id="0330e-111">When the **Ready to reset this device** window appears, select **Reset**.</span></span> 
  
   > [!IMPORTANT]
   > <span data-ttu-id="0330e-112">Quando l'hub viene riavviato nella partizione di ripristino, verrà chiesto di immettere la chiave BitLocker.</span><span class="sxs-lookup"><span data-stu-id="0330e-112">When the Hub reboots to the recovery partition, it will prompt you to enter the BitLocker key.</span></span> <span data-ttu-id="0330e-113">Se si ignora il messaggio, il comando Reimposta non riesce.</span><span class="sxs-lookup"><span data-stu-id="0330e-113">Skipping that prompt will cause reset to fail.</span></span> <span data-ttu-id="0330e-114">Dopo aver immesso la chiave BitLocker, l'hub reinstalla il sistema operativo dalla partizione di ripristino.</span><span class="sxs-lookup"><span data-stu-id="0330e-114">Once you enter the BitLocker key the Hub reinstalls the operating system from the recovery partition.</span></span> <span data-ttu-id="0330e-115">Il completamento può richiedere fino a un'ora.</span><span class="sxs-lookup"><span data-stu-id="0330e-115">This may take up to one hour to complete.</span></span>
  
3. <span data-ttu-id="0330e-116">Per riconfigurare il dispositivo, eseguire il programma di installazione per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="0330e-116">To reconfigure the device, run the first-time Setup program.</span></span>

4. <span data-ttu-id="0330e-117">Se si gestisce il dispositivo con Microsoft Intune o un'altra soluzione di gestione di dispositivi mobili, ritirare ed eliminare il record precedente e quindi ripetere la registrazione del nuovo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0330e-117">If you manage the device using Microsoft Intune or another mobile device management solution, retire and delete the previous record, and then re-enroll the new device.</span></span> <span data-ttu-id="0330e-118">Per altre informazioni, vedere [rimuovere i dispositivi tramite wipe, ritirarsi o annullare la registrazione manuale del dispositivo](https://docs.microsoft.com/intune/devices-wipe).</span><span class="sxs-lookup"><span data-stu-id="0330e-118">For more information, see [Remove devices by using wipe, retire, or manually unenrolling the device](https://docs.microsoft.com/intune/devices-wipe).</span></span>

   > [!div class="mx-imgBorder"]
   > ![\* Reset e ripristino per Surface Hub 2S \*](images/sh2-reset.png)
   <br/>*<span data-ttu-id="0330e-120">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="0330e-120">Figure 1.</span></span> <span data-ttu-id="0330e-121">Reset e ripristino per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="0330e-121">Reset and recovery for Surface Hub 2S</span></span>* 

## <span data-ttu-id="0330e-122">Recuperare Surface Hub 2S usando un'unità di ripristino USB</span><span class="sxs-lookup"><span data-stu-id="0330e-122">Recover Surface Hub 2S by using a USB recovery drive</span></span>

<span data-ttu-id="0330e-123">Nuovo in Surface Hub 2S è ora possibile reinstallare il dispositivo usando un'immagine di ripristino.</span><span class="sxs-lookup"><span data-stu-id="0330e-123">New in Surface Hub 2S, you can now reinstall the device by using a recovery image.</span></span>

### <span data-ttu-id="0330e-124">Ripristino da un'unità USB</span><span class="sxs-lookup"><span data-stu-id="0330e-124">Recovery from a USB drive</span></span>

<span data-ttu-id="0330e-125">Con Surface Hub 2S puoi reinstallare il dispositivo usando un'immagine di ripristino.</span><span class="sxs-lookup"><span data-stu-id="0330e-125">Using Surface Hub 2S, you can reinstall the device by using a recovery image.</span></span> <span data-ttu-id="0330e-126">In questo modo, puoi reinstallare il dispositivo nelle impostazioni di fabbrica se hai perso la chiave BitLocker o se non hai più le credenziali di amministratore per l'app Impostazioni.</span><span class="sxs-lookup"><span data-stu-id="0330e-126">By doing this, you can reinstall the device to the factory settings if you lost the BitLocker key, or if you no longer have admin credentials to the Settings app.</span></span>

>[!NOTE]
><span data-ttu-id="0330e-127">Usare un'unità USB 3,0 con 8 GB o 16 GB di spazio di archiviazione, formattati come FAT32.</span><span class="sxs-lookup"><span data-stu-id="0330e-127">Use a USB 3.0 drive with 8 GB or 16 GB of storage, formatted as FAT32.</span></span>

1. <span data-ttu-id="0330e-128">Da un PC separato scaricare l'immagine di ripristino del file zip dal [sito Web Surface Recovery](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) e quindi tornare a queste istruzioni.</span><span class="sxs-lookup"><span data-stu-id="0330e-128">From a separate PC, download the .zip file recovery image from the [Surface Recovery website](https://support.microsoft.com/surfacerecoveryimage?devicetype=surfacehub2s) and then return to these instructions.</span></span> 

1. <span data-ttu-id="0330e-129">Decomprimere il file scaricato nella radice dell'unità USB.</span><span class="sxs-lookup"><span data-stu-id="0330e-129">Unzip the downloaded file onto the root of the USB drive.</span></span>  

1. <span data-ttu-id="0330e-130">Connettere l'unità USB a qualsiasi porta USB-C o USB-A su Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="0330e-130">Connect the USB drive to any USB-C or USB-A port on Surface Hub 2S.</span></span>

1. <span data-ttu-id="0330e-131">Disattivare il dispositivo:</span><span class="sxs-lookup"><span data-stu-id="0330e-131">Turn off the device:</span></span>

   1. <span data-ttu-id="0330e-132">Mentre si preme il pulsante volume giù, premere il pulsante di alimentazione.</span><span class="sxs-lookup"><span data-stu-id="0330e-132">While pressing the Volume down button, press the Power button.</span></span>
   1. <span data-ttu-id="0330e-133">Continua a premere entrambi i pulsanti finché non viene visualizzato il logo Windows.</span><span class="sxs-lookup"><span data-stu-id="0330e-133">Keep pressing both buttons until you see the Windows logo.</span></span>
   1. <span data-ttu-id="0330e-134">Rilasciare il pulsante di alimentazione, ma continuare a tenere premuto il pulsante volume giù fino a quando non inizia l'interfaccia utente di installazione.</span><span class="sxs-lookup"><span data-stu-id="0330e-134">Release the Power button but continue to hold the Volume down button until the Install UI begins.</span></span>

      ![\* Usare i pulsanti volume giù e Power per avviare il ripristino \*](images/sh2-keypad.png)
      <br>*<span data-ttu-id="0330e-136">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="0330e-136">Figure 2.</span></span> <span data-ttu-id="0330e-137">Pulsanti di alimentazione e di volume</span><span class="sxs-lookup"><span data-stu-id="0330e-137">Volume and Power buttons</span></span>*

1. <span data-ttu-id="0330e-138">Nella schermata Selezione lingua selezionare la lingua di visualizzazione per il mozzo della superficie 2S.</span><span class="sxs-lookup"><span data-stu-id="0330e-138">On the language selection screen, select the display language for your Surface Hub 2S.</span></span>

1. <span data-ttu-id="0330e-139">Selezionare **Recupera da un'unità** e **pulire completamente l'unità**e quindi selezionare **Recupera**.</span><span class="sxs-lookup"><span data-stu-id="0330e-139">Select **Recover from a drive** and **Fully clean the drive**, and then select **Recover**.</span></span> <span data-ttu-id="0330e-140">Se viene richiesta una chiave BitLocker, selezionare **Ignora l'unità**.</span><span class="sxs-lookup"><span data-stu-id="0330e-140">If you're prompted for a BitLocker key, select **Skip this drive**.</span></span> <span data-ttu-id="0330e-141">Surface Hub 2S viene riavviato più volte e impiega circa 30 minuti per completare il processo di ripristino.</span><span class="sxs-lookup"><span data-stu-id="0330e-141">Surface Hub 2S reboots several times and takes approximately 30 minutes to complete the recovery process.</span></span>

<span data-ttu-id="0330e-142">Quando viene visualizzata la schermata di configurazione per la prima volta, rimuovere l'unità USB.</span><span class="sxs-lookup"><span data-stu-id="0330e-142">When the first-time setup screen appears, remove the USB drive.</span></span>

## <span data-ttu-id="0330e-143">Supporto tecnico</span><span class="sxs-lookup"><span data-stu-id="0330e-143">Contact Support</span></span>

<span data-ttu-id="0330e-144">Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).</span><span class="sxs-lookup"><span data-stu-id="0330e-144">If you have questions or need help, you can [create a support request](https://support.microsoft.com/supportforbusiness/productselection).</span></span>

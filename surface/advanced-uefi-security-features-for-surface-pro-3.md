---
title: Funzionalità di sicurezza UEFI avanzate per Surface Pro 3 (Surface)
description: L'articolo descrive come installare e configurare l'aggiornamento UEFI v3.11.760.0 per abilitare opzioni di sicurezza aggiuntive nei dispositivi Surface Pro 3.
ms.assetid: 90F790C0-E5FC-4482-AD71-60589E3C9C93
ms.reviewer: ''
manager: laurawi
keywords: sicurezza, funzionalità, configurare, hardware, dispositivo, personalizzato, script, aggiornamento
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 6a5c53c3e161bd4c49069a0665896762ce587618
ms.sourcegitcommit: e9190a6fe68b8a7cd9b024aea4be9f885f0de388
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "11163186"
---
# <span data-ttu-id="bec93-104">Funzionalità di sicurezza UEFI avanzate per Surface Pro 3</span><span class="sxs-lookup"><span data-stu-id="bec93-104">Advanced UEFI security features for Surface Pro 3</span></span>


<span data-ttu-id="bec93-105">L'articolo descrive come installare e configurare l'aggiornamento UEFI v3.11.760.0 per abilitare opzioni di sicurezza aggiuntive nei dispositivi Surface Pro 3.</span><span class="sxs-lookup"><span data-stu-id="bec93-105">This article describes how to install and configure the v3.11.760.0 UEFI update to enable additional security options for Surface Pro 3 devices.</span></span>

<span data-ttu-id="bec93-106">Per esercitare un controllo più granulare sulla sicurezza dei dispositivi Surface, l'aggiornamento UEFI v3.11.760.0 offre opzioni di sicurezza aggiuntive che ti permettono di disabilitare dispositivi hardware specifici o di impedire l'avvio da questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="bec93-106">To address more granular control over the security of Surface devices, the v3.11.760.0 UEFI update provides additional security options that allow you to disable specific hardware devices or to prevent starting from those devices.</span></span> <span data-ttu-id="bec93-107">Dopo aver installato l'aggiornamento UEFI nel dispositivo, puoi configurarlo manualmente o automaticamente eseguendo uno script.</span><span class="sxs-lookup"><span data-stu-id="bec93-107">After the UEFI update is installed on a device, you can configure it manually or automatically by running a script.</span></span>

## <span data-ttu-id="bec93-108">Installare manualmente l'aggiornamento UEFI</span><span class="sxs-lookup"><span data-stu-id="bec93-108">Manually install the UEFI update</span></span>


<span data-ttu-id="bec93-109">Prima di poter configurare le funzionalità di sicurezza avanzate del dispositivo Surface, devi installare l'aggiornamento UEFI v3.11.760.0.</span><span class="sxs-lookup"><span data-stu-id="bec93-109">Before you can configure the advanced security features of your Surface device, you must first install the v3.11.760.0 UEFI update.</span></span> <span data-ttu-id="bec93-110">Questo aggiornamento viene installato automaticamente se ricevi gli aggiornamenti da Windows Update.</span><span class="sxs-lookup"><span data-stu-id="bec93-110">This update is installed automatically if you receive your updates from Windows Update.</span></span> <span data-ttu-id="bec93-111">Per altre informazioni su come configurare Windows per l'aggiornamento automatico con Windows Update, vedi [Come configurare e usare gli aggiornamenti automatici in Windows](https://support.microsoft.com/kb/306525).</span><span class="sxs-lookup"><span data-stu-id="bec93-111">For more information about how to configure Windows to update automatically by using Windows Update, see [How to configure and use Automatic Updates in Windows](https://support.microsoft.com/kb/306525).</span></span>

<span data-ttu-id="bec93-112">Per aggiornare UEFI in Surface Pro 3, puoi scaricare e installare gli aggiornamenti UEFI di Surface inclusi nel pacchetto di driver e firmware per Surface Pro 3.</span><span class="sxs-lookup"><span data-stu-id="bec93-112">To update the UEFI on Surface Pro 3, you can download and install the Surface UEFI updates as part of the Surface Pro 3 Firmware and Driver Pack.</span></span> <span data-ttu-id="bec93-113">Questi pacchetti di driver e firmware sono disponibili nella [pagina Surface Pro 3](https://www.microsoft.com/download/details.aspx?id=38826) dell'Area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bec93-113">These firmware and driver packs are available from the [Surface Pro 3 page](https://www.microsoft.com/download/details.aspx?id=38826) on the Microsoft Download Center.</span></span> <span data-ttu-id="bec93-114">Puoi trovare altre informazioni sui pacchetti di driver e firmware in [Scaricare le versioni più recenti di driver e firmware per dispositivi Surface](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices).</span><span class="sxs-lookup"><span data-stu-id="bec93-114">You can find out more about the firmware and driver packs at [Download the latest firmware and drivers for Surface devices](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices).</span></span> <span data-ttu-id="bec93-115">I pacchetti di driver e firmware sono disponibili sia in formato Windows Installer autonomo (MSI) sia in formato archivio (ZIP).</span><span class="sxs-lookup"><span data-stu-id="bec93-115">The firmware and driver packs are available as both self-contained Windows Installer (.msi) and archive (.zip) formats.</span></span> <span data-ttu-id="bec93-116">Puoi trovare altre informazioni su questi due formati e su come usarli per aggiornare i driver in [Gestire gli aggiornamenti di driver e firmware di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates).</span><span class="sxs-lookup"><span data-stu-id="bec93-116">You can find out more about these two formats and how you can use them to update your drivers at [Manage Surface driver and firmware updates](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates).</span></span>

## <span data-ttu-id="bec93-117">Configurare manualmente impostazioni di sicurezza aggiuntive</span><span class="sxs-lookup"><span data-stu-id="bec93-117">Manually configure additional security settings</span></span>


>[!NOTE]
><span data-ttu-id="bec93-118">Per avviare l'installazione del firmware in un dispositivo Surface, inizia con il dispositivo spento, tieni premuto il pulsante di **aumento del volume**, premi e rilascia il pulsante di **accensione**, quindi rilascia il pulsante di **aumento del volume** dopo che il dispositivo inizia l'avvio.</span><span class="sxs-lookup"><span data-stu-id="bec93-118">To enter firmware setup on a Surface device, begin with the device powered off, press and hold the **Volume Up** button, then press and release the **Power** button, then release the **Volume Up** button after the device has begun to boot.</span></span>

<span data-ttu-id="bec93-119">Dopo aver installato l'aggiornamento UEFI v3.11.760.0 in un dispositivo Surface, è disponibile un nuovo menu di UEFI chiamato **Advanced Device Security**.</span><span class="sxs-lookup"><span data-stu-id="bec93-119">After the v3.11.760.0 UEFI update is installed on a Surface device, an additional UEFI menu named **Advanced Device Security** becomes available.</span></span> <span data-ttu-id="bec93-120">Se fai clic su questo menu, vengono visualizzate le opzioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="bec93-120">If you click this menu, the following options are displayed:</span></span>

| <span data-ttu-id="bec93-121">Opzione</span><span class="sxs-lookup"><span data-stu-id="bec93-121">Option</span></span>         | <span data-ttu-id="bec93-122">Descrizione</span><span class="sxs-lookup"><span data-stu-id="bec93-122">Description</span></span>                                                                                                                                                                          | <span data-ttu-id="bec93-123">Impostazioni disponibili (valori predefiniti indicati in grassetto)</span><span class="sxs-lookup"><span data-stu-id="bec93-123">Available settings (default listed in bold)</span></span> |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| <span data-ttu-id="bec93-124">Network Boot</span><span class="sxs-lookup"><span data-stu-id="bec93-124">Network Boot</span></span>   | <span data-ttu-id="bec93-125">Abilita o disabilita la capacità del dispositivo Surface di eseguire l'avvio dalla rete (chiamata anche avvio PXE).</span><span class="sxs-lookup"><span data-stu-id="bec93-125">Enables or disables the ability of your Surface device to boot from the network (also known as PXE boot).</span></span>                                                                            | <span data-ttu-id="bec93-126">**Enabled**, Not Bootable</span><span class="sxs-lookup"><span data-stu-id="bec93-126">**Enabled**, Not Bootable</span></span>                   |
| <span data-ttu-id="bec93-127">Side USB</span><span class="sxs-lookup"><span data-stu-id="bec93-127">Side USB</span></span>       | <span data-ttu-id="bec93-128">Abilita o disabilita la porta USB sul lato del dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-128">Enables or disables the USB port on the side of the Surface device.</span></span> <span data-ttu-id="bec93-129">La porta USB può inoltre essere abilitata, ma senza permettere l'avvio.</span><span class="sxs-lookup"><span data-stu-id="bec93-129">Additionally, the USB port can be enabled, but not allow booting.</span></span>                                                | <span data-ttu-id="bec93-130">**Enabled**, Not Bootable, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-130">**Enabled**, Not Bootable, Disabled</span></span>         |
| <span data-ttu-id="bec93-131">Docking Port</span><span class="sxs-lookup"><span data-stu-id="bec93-131">Docking Port</span></span>   | <span data-ttu-id="bec93-132">Abilita o disabilita le porte sull'alloggiamento di espansione di Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-132">Enables or disables the ports on the Surface docking station.</span></span> <span data-ttu-id="bec93-133">Inoltre, è possibile abilitare la porta dell'alloggiamento di espansione bloccando però l'avvio da qualsiasi porta USB o Ethernet sull'alloggiamento di espansione.</span><span class="sxs-lookup"><span data-stu-id="bec93-133">Additionally, the docking port can be enabled, but block booting from any USB or Ethernet port in the docking station.</span></span> | <span data-ttu-id="bec93-134">**Enabled**, Not Bootable, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-134">**Enabled**, Not Bootable, Disabled</span></span>         |
| <span data-ttu-id="bec93-135">Front Camera</span><span class="sxs-lookup"><span data-stu-id="bec93-135">Front Camera</span></span>   | <span data-ttu-id="bec93-136">Abilita o disabilita la fotocamera sul lato anteriore del dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-136">Enables or disables the camera on the front of the Surface device.</span></span>                                                                                                                   | <span data-ttu-id="bec93-137">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-137">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="bec93-138">Rear Camera</span><span class="sxs-lookup"><span data-stu-id="bec93-138">Rear Camera</span></span>    | <span data-ttu-id="bec93-139">Abilita o disabilita la fotocamera sul retro del dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-139">Enables or disables the camera on the rear of the Surface device.</span></span>                                                                                                                    | <span data-ttu-id="bec93-140">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-140">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="bec93-141">On Board Audio</span><span class="sxs-lookup"><span data-stu-id="bec93-141">On Board Audio</span></span> | <span data-ttu-id="bec93-142">Abilita o disabilita l'audio nel dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-142">Enables or disables audio on the Surface device.</span></span>                                                                                                                                     | <span data-ttu-id="bec93-143">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-143">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="bec93-144">microSD</span><span class="sxs-lookup"><span data-stu-id="bec93-144">microSD</span></span>        | <span data-ttu-id="bec93-145">Abilita o disabilita lo slot microSD nel dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-145">Enables or disables the microSD slot on the Surface device.</span></span>                                                                                                                          | <span data-ttu-id="bec93-146">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-146">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="bec93-147">WiFi</span><span class="sxs-lookup"><span data-stu-id="bec93-147">WiFi</span></span>           | <span data-ttu-id="bec93-148">Abilita o disabilita il ricetrasmettitore Wi-Fi integrato nel dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-148">Enables or disables the built-in Wi-Fi transceiver in the Surface device.</span></span> <span data-ttu-id="bec93-149">Viene disabilitata anche la funzionalità Bluetooth.</span><span class="sxs-lookup"><span data-stu-id="bec93-149">This also disables Bluetooth.</span></span>                                                                              | <span data-ttu-id="bec93-150">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-150">**Enabled**, Disabled</span></span>                       |
| <span data-ttu-id="bec93-151">Bluetooth</span><span class="sxs-lookup"><span data-stu-id="bec93-151">Bluetooth</span></span>      | <span data-ttu-id="bec93-152">Abilita o disabilita il ricetrasmettitore Bluetooth integrato nel dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="bec93-152">Enables or disables the built-in Bluetooth transceiver in the Surface device.</span></span>                                                                                                        | <span data-ttu-id="bec93-153">**Enabled**, Disabled</span><span class="sxs-lookup"><span data-stu-id="bec93-153">**Enabled**, Disabled</span></span>                       |

 

## <span data-ttu-id="bec93-154">Automatizzare le impostazioni di sicurezza aggiuntive</span><span class="sxs-lookup"><span data-stu-id="bec93-154">Automate additional security settings</span></span>


<span data-ttu-id="bec93-155">In qualità di professionista IT con privilegi amministrativi, puoi automatizzare la configurazione delle impostazioni UEFI sfruttando gli [strumenti firmware per Surface Pro 3 (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) disponibili nell'Area download Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bec93-155">As an IT professional with administrative privileges, you can automate the configuration of UEFI settings by leveraging [Surface Pro 3 Firmware Tools (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) available from the Microsoft Download Center.</span></span> <span data-ttu-id="bec93-156">Questi strumenti installano un assembly .NET che può essere chiamato da qualsiasi applicazione o script personalizzato.</span><span class="sxs-lookup"><span data-stu-id="bec93-156">These tools install a .NET assembly that can be called from any custom application or script.</span></span>

**<span data-ttu-id="bec93-157">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="bec93-157">Prerequisites</span></span>**

-   <span data-ttu-id="bec93-158">Gli script di esempio di seguito sfruttano l'estensione citata sopra e di conseguenza presuppongono che lo strumento sia stato installato nel dispositivo gestito.</span><span class="sxs-lookup"><span data-stu-id="bec93-158">The sample scripts below leverage the previously mentioned extension and therefore assume that the tool has been installed on the device being managed.</span></span>
-   <span data-ttu-id="bec93-159">Gli script devono essere eseguiti con privilegi amministrativi.</span><span class="sxs-lookup"><span data-stu-id="bec93-159">The scripts must be run with administrative privilege.</span></span>
-   <span data-ttu-id="bec93-160">Il comando [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) di Windows PowerShell deve essere chiamato prima di eseguire gli script di esempio se questi sono senza firma digitale.</span><span class="sxs-lookup"><span data-stu-id="bec93-160">The Windows PowerShell command [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) must be called prior to running sample scripts if they are not digitally signed.</span></span>

**<span data-ttu-id="bec93-161">Script di esempio</span><span class="sxs-lookup"><span data-stu-id="bec93-161">Sample scripts</span></span>**

> [!NOTE]
> <span data-ttu-id="bec93-162">La password UEFI usata negli script di esempio di seguito è presentata come testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="bec93-162">The UEFI password used in the sample scripts below is presented in clear text.</span></span> <span data-ttu-id="bec93-163">Consigliamo di salvare gli script in un percorso protetto e di eseguirli in un ambiente controllato.</span><span class="sxs-lookup"><span data-stu-id="bec93-163">We strongly recommend saving the scripts in a protected location and running them in a controlled environment.</span></span>


<span data-ttu-id="bec93-164">Mostrare tutte le opzioni di configurazione:</span><span class="sxs-lookup"><span data-stu-id="bec93-164">Show all configurable options:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
foreach ($uefiOption in $uefiOptions) 
{ 
    Write-Host "Name:" $uefiOption.Name 
    Write-Host " Description =" $uefiOption.Description 
    Write-Host " Current Value =" $uefiOption.CurrentValue 
    Write-Host " Default Value =" $uefiOption.DefaultValue 
    Write-Host " Proposed Value =" $uefiOption.ProposedValue 
     
    # This gives usage and validation information 
    Write-Host " Allowed Values =" $uefiOption.FriendlyRegEx 
    Write-Host " Regular Expression =" $uefiOption.RegEx 
     
    Write-Host 
}
```

<span data-ttu-id="bec93-165">Impostare o modificare la password UEFI:</span><span class="sxs-lookup"><span data-stu-id="bec93-165">Set or change UEFI password:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
$Password = [Microsoft.Surface.FirmwareOption]::Find("Password") 
 
# Set New value to 12345 
$Password.ProposedValue = "12345"
```

<span data-ttu-id="bec93-166">Controllare lo stato delle modifiche proposte:</span><span class="sxs-lookup"><span data-stu-id="bec93-166">Check status of proposed changes:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Check update status 
$updateStatus = [Microsoft.Surface.FirmwareOption]::UpdateStatus 
$updateIteration = [Microsoft.Surface.FirmwareOption]::UpdateIteration 
Write-Host "Last Update Status =" $updateStatus 
Write-Host "Last Update Iteration =" $updateIteration 
 
# Get the individual results for the last proposed update 
# If the device has never had an update attempt this will be an empty list 
$details = [Microsoft.Surface.FirmwareOption]::UpdateStatusDetails 
Write-Host $details.Count "Settings were proposed" 
if ($details.Count -gt 0) 
{ 
    Write-Host "Result Details" 
    foreach ($detail in $details.GetEnumerator()) 
    { 
        Write-Host " " $detail.Key "=" $detail.Value 
    } 
}
```

<span data-ttu-id="bec93-167">Ripristinare i valori predefiniti di UEFI:</span><span class="sxs-lookup"><span data-stu-id="bec93-167">Revert UEFI to default values:</span></span>

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
# Reset all options to the factory default 
foreach ($uefiOption in $uefiOptions) 
{ 
    $uefiOption.ProposedValue = $uefiOption.DefaultValue 
}
```

<span data-ttu-id="bec93-168">Interpretazione dei codici di stato</span><span class="sxs-lookup"><span data-stu-id="bec93-168">Status code interpretation</span></span>

-   <span data-ttu-id="bec93-169">00: l'aggiornamento proposto è riuscito</span><span class="sxs-lookup"><span data-stu-id="bec93-169">00 - The proposed update was a success</span></span>
-   <span data-ttu-id="bec93-170">02: uno dei valori proposti non è valido</span><span class="sxs-lookup"><span data-stu-id="bec93-170">02 - One of the proposed values had an invalid value</span></span>
-   <span data-ttu-id="bec93-171">03: uno dei valori proposti impostati non è stato riconosciuto</span><span class="sxs-lookup"><span data-stu-id="bec93-171">03 - There was a proposed value set that was not recognized</span></span>
-   <span data-ttu-id="bec93-172">0F: la password di sblocco non corrisponde a quella attualmente impostata</span><span class="sxs-lookup"><span data-stu-id="bec93-172">0F - The unlock password did not match currently set password</span></span>

 

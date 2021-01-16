---
title: Gestire le impostazioni UEFI di Surface
description: Usa le impostazioni UEFI di Surface per abilitare o disabilitare dispositivi o componenti, configurare impostazioni di sicurezza e modificare le impostazioni di avvio dei dispositivi Surface.
keywords: firmware, sicurezza, funzionalità, configurare, hardware
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: devices, surface
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.date: 01/15/2021
ms.openlocfilehash: d8d47db3bd6f69783670b285a797337373e02d72
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271430"
---
# <span data-ttu-id="e0efb-104">Gestire le impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-104">Manage Surface UEFI settings</span></span>

<span data-ttu-id="e0efb-105">Tutte le generazioni correnti e future dei dispositivi Surface usano un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft in modo specifico per questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="e0efb-105">All current and future generations of Surface devices use a unique Unified Extensible Firmware Interface (UEFI) engineered by Microsoft specifically for these devices.</span></span> <span data-ttu-id="e0efb-106">Le impostazioni di Surface UEFI offrono la possibilità di abilitare o disabilitare dispositivi e componenti incorporati, proteggere le impostazioni UEFI e modificare le impostazioni di avvio del dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="e0efb-106">Surface UEFI settings provide the ability to enable or disable built-in devices and components, protect UEFI settings from being changed, and adjust the Surface device boot settings.</span></span> 

## <span data-ttu-id="e0efb-107">Prodotti supportati</span><span class="sxs-lookup"><span data-stu-id="e0efb-107">Supported products</span></span>

<span data-ttu-id="e0efb-108">La gestione UEFI è supportata nelle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="e0efb-108">UEFI management is supported on the following:</span></span> 

- <span data-ttu-id="e0efb-109">Surface Pro 4, Surface Pro (5a gen), Surface Pro 6, Surface Pro 7, Surface Pro 7 +, Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="e0efb-109">Surface Pro 4, Surface Pro (5th Gen), Surface Pro 6, Surface Pro 7, Surface Pro 7+, Surface Pro X</span></span>
- <span data-ttu-id="e0efb-110">Superficie portatile (1a Gen), Surface laptop 2, Surface laptop 3, Surface laptop go</span><span class="sxs-lookup"><span data-stu-id="e0efb-110">Surface Laptop (1st Gen), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go</span></span>
- <span data-ttu-id="e0efb-111">Surface Studio (1a generazione), Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="e0efb-111">Surface Studio (1st Gen), Surface Studio 2</span></span>
- <span data-ttu-id="e0efb-112">Surface Book, Surface Book 2, Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="e0efb-112">Surface Book, Surface Book 2, Surface Book 3</span></span>
- <span data-ttu-id="e0efb-113">Superficie andare, superficie andare 2</span><span class="sxs-lookup"><span data-stu-id="e0efb-113">Surface Go, Surface Go 2</span></span>

## <span data-ttu-id="e0efb-114">Supporto per la gestione basata sul cloud</span><span class="sxs-lookup"><span data-stu-id="e0efb-114">Support for cloud-based management</span></span>

<span data-ttu-id="e0efb-115">Con i profili di DFCI (device firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in anteprima pubblica), Surface UEFI Management estende il moderno stack di gestione fino al livello hardware UEFI.</span><span class="sxs-lookup"><span data-stu-id="e0efb-115">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="e0efb-116">DFCI supporta il provisioning a zero tocco, Elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, incluse le opzioni di avvio e le periferiche predefinite, e stabilisce le basi per scenari di sicurezza avanzati in futuro.</span><span class="sxs-lookup"><span data-stu-id="e0efb-116">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="e0efb-117">DFCI è attualmente disponibile per Surface Pro 7 +, Surface Laptop Go, Surface Book 3, Surface laptop 3, Surface Pro 7 e Surface Pro X.  Per altre informazioni, vedere [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md).</span><span class="sxs-lookup"><span data-stu-id="e0efb-117">DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7, and Surface Pro X.  For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="e0efb-118">Menu open Surface UEFI</span><span class="sxs-lookup"><span data-stu-id="e0efb-118">Open Surface UEFI menu</span></span>

<span data-ttu-id="e0efb-119">Per regolare le impostazioni UEFI durante l'avvio del sistema:</span><span class="sxs-lookup"><span data-stu-id="e0efb-119">To adjust UEFI settings during system startup:</span></span>

1. <span data-ttu-id="e0efb-120">Chiudere la superficie e attendere circa 10 secondi per verificare che sia disattivata.</span><span class="sxs-lookup"><span data-stu-id="e0efb-120">Shut down your Surface and wait about 10 seconds to make sure it's off.</span></span>
2. <span data-ttu-id="e0efb-121">Premere e tenere premuto il pulsante **volume-up** e-allo stesso tempo-premere e rilasciare il **pulsante di accensione.**</span><span class="sxs-lookup"><span data-stu-id="e0efb-121">Press and hold the **Volume-up** button  and - at the same time - press and release the **Power button.**</span></span>
3. <span data-ttu-id="e0efb-122">Quando sullo schermo compare il logo Microsoft o Surface, continuare a tenere premuto il pulsante **volume-up** finché non viene visualizzata la schermata UEFI.</span><span class="sxs-lookup"><span data-stu-id="e0efb-122">As the Microsoft or Surface logo appears on your screen, continue to hold the **Volume-up** button until the UEFI screen appears.</span></span>

## <span data-ttu-id="e0efb-123">Pagina informazioni PC UEFI</span><span class="sxs-lookup"><span data-stu-id="e0efb-123">UEFI PC information page</span></span>

<span data-ttu-id="e0efb-124">La pagina informazioni PC include informazioni dettagliate sul dispositivo Surface:</span><span class="sxs-lookup"><span data-stu-id="e0efb-124">The PC information page includes detailed information about your Surface device:</span></span> 

- <span data-ttu-id="e0efb-125">**Modello** : il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7.</span><span class="sxs-lookup"><span data-stu-id="e0efb-125">**Model** – Your Surface device’s model will be displayed here, such as Surface Book 2 or Surface Pro 7.</span></span> <span data-ttu-id="e0efb-126">L'esatta configurazione del dispositivo non viene visualizzata, ad esempio processore, dimensioni dei dischi o dimensioni della memoria.</span><span class="sxs-lookup"><span data-stu-id="e0efb-126">The exact configuration of your device is not shown, (such as processor, disk size, or memory size).</span></span> 
- <span data-ttu-id="e0efb-127">**UUID**: codice Universally Unique Identification specifico del dispositivo e usato per identificare il dispositivo durante la distribuzione o la gestione.</span><span class="sxs-lookup"><span data-stu-id="e0efb-127">**UUID** – This Universally Unique Identification number is specific to your device and is used to identify the device during deployment or management.</span></span> 

- <span data-ttu-id="e0efb-128">**Serial Number**: numero usato per identificare questo dispositivo Surface specifico per gli scenari di tag asset e supporto.</span><span class="sxs-lookup"><span data-stu-id="e0efb-128">**Serial Number** – This number is used to identify this specific Surface device for asset tagging and support scenarios.</span></span>
- <span data-ttu-id="e0efb-129">**Asset Tag**: tag asset assegnato al dispositivo Surface tramite [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span><span class="sxs-lookup"><span data-stu-id="e0efb-129">**Asset Tag** – The asset tag is assigned to the Surface device with the [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span></span> 

<span data-ttu-id="e0efb-130">Qui troverai anche informazioni dettagliate sul firmware del tuo dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="e0efb-130">You will also find detailed information about the firmware of your Surface device.</span></span> <span data-ttu-id="e0efb-131">I dispositivi Surface hanno svariati componenti interni, ognuno dei quali esegue versioni diverse del firmware.</span><span class="sxs-lookup"><span data-stu-id="e0efb-131">Surface devices have several internal components that each run different versions of firmware.</span></span> <span data-ttu-id="e0efb-132">La versione del firmware di ognuno dei dispositivi seguenti viene visualizzata nella pagina **PC information** (mostrata nella figura 1):</span><span class="sxs-lookup"><span data-stu-id="e0efb-132">The firmware version of each of the following devices is displayed on the **PC information** page (as shown in Figure 1):</span></span> 

- <span data-ttu-id="e0efb-133">UEFI di sistema</span><span class="sxs-lookup"><span data-stu-id="e0efb-133">System UEFI</span></span> 

- <span data-ttu-id="e0efb-134">Controller SAM</span><span class="sxs-lookup"><span data-stu-id="e0efb-134">SAM Controller</span></span> 

- <span data-ttu-id="e0efb-135">Intel Management Engine</span><span class="sxs-lookup"><span data-stu-id="e0efb-135">Intel Management Engine</span></span> 

- <span data-ttu-id="e0efb-136">Controller integrato di sistema</span><span class="sxs-lookup"><span data-stu-id="e0efb-136">System Embedded Controller</span></span> 

- <span data-ttu-id="e0efb-137">Firmware per il tocco</span><span class="sxs-lookup"><span data-stu-id="e0efb-137">Touch Firmware</span></span> 

![Informazioni di sistema e informazioni sulla versione del firmware](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*<span data-ttu-id="e0efb-139">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="e0efb-139">Figure 1.</span></span> <span data-ttu-id="e0efb-140">Informazioni di sistema e informazioni sulla versione del firmware</span><span class="sxs-lookup"><span data-stu-id="e0efb-140">System information and firmware version information</span></span>*

<span data-ttu-id="e0efb-141">Puoi trovare informazioni aggiornate sulla versione più recente del firmware per il dispositivo Surface nella pagina [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) per il tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="e0efb-141">You can find up-to-date information about the latest firmware version for your Surface device in the [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) for your device.</span></span> 

## <span data-ttu-id="e0efb-142">Pagina sicurezza UEFI</span><span class="sxs-lookup"><span data-stu-id="e0efb-142">UEFI Security page</span></span> 

![Configurazione delle impostazioni di sicurezza UEFI di Surface](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*<span data-ttu-id="e0efb-144">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="e0efb-144">Figure 2.</span></span> <span data-ttu-id="e0efb-145">Configurazione delle impostazioni di sicurezza UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-145">Configure Surface UEFI security settings</span></span>*

<span data-ttu-id="e0efb-146">La pagina sicurezza consente di impostare una password per la protezione delle impostazioni UEFI.</span><span class="sxs-lookup"><span data-stu-id="e0efb-146">The Security page allows you to set a password to protect UEFI settings.</span></span> <span data-ttu-id="e0efb-147">Questa password deve essere immessa quando avvii il dispositivo Surface in UEFI.</span><span class="sxs-lookup"><span data-stu-id="e0efb-147">This password must be entered when you boot the Surface device to UEFI.</span></span> <span data-ttu-id="e0efb-148">La password può contenere i caratteri seguenti (come illustrato nella figura 3):</span><span class="sxs-lookup"><span data-stu-id="e0efb-148">The password can contain the following characters (as shown in Figure 3):</span></span> 

- <span data-ttu-id="e0efb-149">Lettere maiuscole: A-Z</span><span class="sxs-lookup"><span data-stu-id="e0efb-149">Uppercase letters: A-Z</span></span> 

- <span data-ttu-id="e0efb-150">Lettere minuscole: a-z</span><span class="sxs-lookup"><span data-stu-id="e0efb-150">Lowercase letters: a-z</span></span> 

- <span data-ttu-id="e0efb-151">Numeri: 1-0</span><span class="sxs-lookup"><span data-stu-id="e0efb-151">Numbers: 1-0</span></span> 

- <span data-ttu-id="e0efb-152">Caratteri speciali:! @ # $% ^& \* ()? <>{} []-_ = + |.,;:'' "</span><span class="sxs-lookup"><span data-stu-id="e0efb-152">Special characters: !@#$%^&\*()?<>{}[]-_=+|.,;:’\`”</span></span> 

<span data-ttu-id="e0efb-153">La password deve contenere almeno 6 caratteri e fa distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="e0efb-153">The password must be at least 6 characters and is case sensitive.</span></span> 

![Aggiunta di una password per proteggere le impostazioni UEFI di Surface](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*<span data-ttu-id="e0efb-155">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="e0efb-155">Figure 3.</span></span> <span data-ttu-id="e0efb-156">Aggiunta di una password per proteggere le impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-156">Add a password to protect Surface UEFI settings</span></span>*

<span data-ttu-id="e0efb-157">Nella pagina Security puoi anche modificare la configurazione di Avvio protetto nel tuo dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="e0efb-157">On the Security page you can also change the configuration of Secure Boot on your Surface device.</span></span> <span data-ttu-id="e0efb-158">La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit.</span><span class="sxs-lookup"><span data-stu-id="e0efb-158">Secure Boot technology prevents unauthorized boot code from booting on your Surface device, which protects against bootkit and rootkit-type malware infections.</span></span> <span data-ttu-id="e0efb-159">Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti.</span><span class="sxs-lookup"><span data-stu-id="e0efb-159">You can disable Secure Boot to allow your Surface device to boot third-party operating systems or bootable media.</span></span> <span data-ttu-id="e0efb-160">È anche possibile configurare l'avvio sicuro per l'utilizzo con certificati di terze parti, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="e0efb-160">You can also configure Secure Boot to work with third-party certificates, as shown in Figure 4.</span></span> <span data-ttu-id="e0efb-161">Per altre informazioni, vedi [Avvio protetto](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) nella Libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="e0efb-161">Read more about [Secure Boot](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) in the TechNet Library.</span></span>

![Configurazione di Avvio protetto](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*<span data-ttu-id="e0efb-163">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="e0efb-163">Figure 4.</span></span> <span data-ttu-id="e0efb-164">Configurazione di Avvio protetto</span><span class="sxs-lookup"><span data-stu-id="e0efb-164">Configure Secure Boot</span></span>*

<span data-ttu-id="e0efb-165">A seconda del dispositivo, potrebbe essere anche possibile verificare se il TPM è abilitato o disabilitato.</span><span class="sxs-lookup"><span data-stu-id="e0efb-165">Depending on your device, you may also be able to see if your TPM is enabled or disabled.</span></span> <span data-ttu-id="e0efb-166">Se l'impostazione **Abilita TPM**  non è visibile, aprire TPM. msc in Windows per verificare lo stato, come illustrato nella figura 5.</span><span class="sxs-lookup"><span data-stu-id="e0efb-166">If you do not see the **Enable TPM**  setting, open tpm.msc in Windows to check the status, as shown in Figure 5.</span></span> <span data-ttu-id="e0efb-167">Il dispositivo TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker.</span><span class="sxs-lookup"><span data-stu-id="e0efb-167">The TPM is used to authenticate encryption for your device’s data with BitLocker.</span></span> <span data-ttu-id="e0efb-168">Per altre informazioni, vedere [Cenni preliminari su BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span><span class="sxs-lookup"><span data-stu-id="e0efb-168">To learn more, see [BitLocker overview](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span></span> 

![Console TPM](images/manage-surface-uefi-fig5-a.png "TPM console")

*<span data-ttu-id="e0efb-170">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="e0efb-170">Figure 5.</span></span> <span data-ttu-id="e0efb-171">Console TPM</span><span class="sxs-lookup"><span data-stu-id="e0efb-171">TPM console</span></span>*


## <span data-ttu-id="e0efb-172">Menu UEFI: dispositivi</span><span class="sxs-lookup"><span data-stu-id="e0efb-172">UEFI menu: Devices</span></span> 

<span data-ttu-id="e0efb-173">La pagina dispositivi consente di abilitare o disabilitare dispositivi e componenti specifici, tra cui:</span><span class="sxs-lookup"><span data-stu-id="e0efb-173">The Devices page allows you to  enable or disable specific devices and components including:</span></span>

- <span data-ttu-id="e0efb-174">Alloggiamento di espansione e porte USB</span><span class="sxs-lookup"><span data-stu-id="e0efb-174">Docking and USB Ports</span></span> 

- <span data-ttu-id="e0efb-175">Slot per scheda microSD o SD</span><span class="sxs-lookup"><span data-stu-id="e0efb-175">MicroSD or SD Card Slot</span></span> 

- <span data-ttu-id="e0efb-176">Fotocamera posteriore</span><span class="sxs-lookup"><span data-stu-id="e0efb-176">Rear Camera</span></span> 

- <span data-ttu-id="e0efb-177">Fotocamera anteriore</span><span class="sxs-lookup"><span data-stu-id="e0efb-177">Front Camera</span></span> 

- <span data-ttu-id="e0efb-178">Fotocamera a infrarossi</span><span class="sxs-lookup"><span data-stu-id="e0efb-178">Infrared (IR) Camera</span></span> 

- <span data-ttu-id="e0efb-179">Wi-Fi e Bluetooth</span><span class="sxs-lookup"><span data-stu-id="e0efb-179">Wi-Fi and Bluetooth</span></span> 

- <span data-ttu-id="e0efb-180">Audio integrato (altoparlanti e microfono)</span><span class="sxs-lookup"><span data-stu-id="e0efb-180">Onboard Audio (Speakers and Microphone)</span></span> 

<span data-ttu-id="e0efb-181">Ogni dispositivo è elencato con un **pulsante di scorrimento che consente di spostare** la posizione **attivato (abilitato) o disattivato** (disabilitato), come illustrato nella figura 6.</span><span class="sxs-lookup"><span data-stu-id="e0efb-181">Each device is listed with a slider button that you can move to **On** (enabled) or **Off** (disabled) position, as shown in Figure 6.</span></span> 

![Abilitazione e disabilitazione di dispositivi specifici](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*<span data-ttu-id="e0efb-183">Figura 6.</span><span class="sxs-lookup"><span data-stu-id="e0efb-183">Figure 6.</span></span> <span data-ttu-id="e0efb-184">Abilitazione e disabilitazione di dispositivi specifici</span><span class="sxs-lookup"><span data-stu-id="e0efb-184">Enable and disable specific devices</span></span>*

## <span data-ttu-id="e0efb-185">Menu UEFI: configurazione di avvio</span><span class="sxs-lookup"><span data-stu-id="e0efb-185">UEFI menu: Boot configuration</span></span> 

<span data-ttu-id="e0efb-186">La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio e di abilitare o disabilitare l'avvio dei dispositivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="e0efb-186">The Boot Configuration page allows you to change the order of your boot devices as well as enable or disable boot of the following devices:</span></span> 

- <span data-ttu-id="e0efb-187">Windows Boot Manager</span><span class="sxs-lookup"><span data-stu-id="e0efb-187">Windows Boot Manager</span></span> 

- <span data-ttu-id="e0efb-188">Archiviazione USB</span><span class="sxs-lookup"><span data-stu-id="e0efb-188">USB Storage</span></span> 

- <span data-ttu-id="e0efb-189">Rete PXE</span><span class="sxs-lookup"><span data-stu-id="e0efb-189">PXE Network</span></span> 

- <span data-ttu-id="e0efb-190">Archiviazione interna</span><span class="sxs-lookup"><span data-stu-id="e0efb-190">Internal Storage</span></span> 

<span data-ttu-id="e0efb-191">Puoi eseguire l'avvio da un dispositivo specifico immediatamente oppure puoi scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen.</span><span class="sxs-lookup"><span data-stu-id="e0efb-191">You can boot from a specific device immediately, or you can swipe left on that device’s entry in the list using the touchscreen.</span></span> <span data-ttu-id="e0efb-192">Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="e0efb-192">You can also boot immediately to a USB device or USB Ethernet adapter when the Surface device is powered off by pressing the **Volume Down** button and the **Power** button simultaneously.</span></span> 

<span data-ttu-id="e0efb-193">Per rendere effettivo l'ordine di avvio specificato, è necessario impostare l'opzione **Attiva sequenza di avvio alternativo** **su**attivato, come illustrato nella figura 7.</span><span class="sxs-lookup"><span data-stu-id="e0efb-193">For the specified boot order to take effect, you must set the **Enable Alternate Boot Sequence** option to **On**, as shown in Figure 7.</span></span> 

![Configurazione dell'ordine di avvio per il dispositivo Surface](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*<span data-ttu-id="e0efb-195">Figura 7.</span><span class="sxs-lookup"><span data-stu-id="e0efb-195">Figure 7.</span></span> <span data-ttu-id="e0efb-196">Configurazione dell'ordine di avvio per il dispositivo Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-196">Configure the boot order for your Surface device</span></span>* 

<span data-ttu-id="e0efb-197">Poi anche attivare o disattivare il supporto IPv6 per PXE con l'opzione **Enable IPv6 for PXE Network Boot**, ad esempio quando esegui una distribuzione di Windows con PXE in cui il server PXE è configurato solo per IPv4.</span><span class="sxs-lookup"><span data-stu-id="e0efb-197">You can also turn on and off IPv6 support for PXE with the **Enable IPv6 for PXE Network Boot** option, for example when performing a Windows deployment using PXE where the PXE server is configured for IPv4 only.</span></span>  

## <span data-ttu-id="e0efb-198">Menu UEFI: gestione</span><span class="sxs-lookup"><span data-stu-id="e0efb-198">UEFI menu: Management</span></span>
<span data-ttu-id="e0efb-199">La pagina di gestione consente di gestire l'uso della gestione delle funzioni di zero touch UEFI e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 7, Surface Pro X e Surface laptop 3.</span><span class="sxs-lookup"><span data-stu-id="e0efb-199">The Management page allows you to manage use of Zero Touch UEFI Management and other features on eligible devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

![<span data-ttu-id="e0efb-200">Gestire l'accesso alla gestione di zero touch UEFI e ad altre caratteristiche ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *Figura 8. Gestire l'accesso alla gestione di zero touch UEFI e ad altre caratteristiche*</span><span class="sxs-lookup"><span data-stu-id="e0efb-200">Manage access to Zero Touch UEFI Management and other features](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
*Figure 8. Manage access to Zero Touch UEFI Management and other features*</span></span> 


<span data-ttu-id="e0efb-201">Zero Touch UEFI Management consente di gestire in remoto le impostazioni UEFI usando un profilo di dispositivo all'interno di Intune denominato device firmware Configuration Interface (DFCI).</span><span class="sxs-lookup"><span data-stu-id="e0efb-201">Zero Touch UEFI Management lets you remotely manage UEFI settings  by using a device profile within Intune called Device Firmware Configuration Interface (DFCI).</span></span> <span data-ttu-id="e0efb-202">Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **pronto**.</span><span class="sxs-lookup"><span data-stu-id="e0efb-202">If you do not configure this setting, the ability to manage eligible devices with DFCI is set to **Ready**.</span></span> <span data-ttu-id="e0efb-203">Per evitare DFCI, selezionare **opt-out**.</span><span class="sxs-lookup"><span data-stu-id="e0efb-203">To prevent DFCI, select **Opt-Out**.</span></span> 

> [!NOTE]
> <span data-ttu-id="e0efb-204">La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono attualmente disponibili per Surface Pro 7 +, Surface Laptop Go, Surface Book 3, Surface laptop 3, Surface Pro 7 e Surface Pro X. Per altre informazioni, Vedi [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md).</span><span class="sxs-lookup"><span data-stu-id="e0efb-204">The UEFI Management settings page and use of DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7, and Surface Pro X. To learn more, see [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <span data-ttu-id="e0efb-205">Menu UEFI: Esci</span><span class="sxs-lookup"><span data-stu-id="e0efb-205">UEFI menu: Exit</span></span> 

<span data-ttu-id="e0efb-206">Usare il pulsante **Riavvia ora** nella pagina **Esci** per uscire dalle impostazioni di UEFI, come illustrato nella figura 9.</span><span class="sxs-lookup"><span data-stu-id="e0efb-206">Use the **Restart Now** button on the **Exit** page to exit UEFI settings, as shown in Figure 9.</span></span> 

![Chiusura delle impostazioni UEFI di Surface e riavvio del dispositivo](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*<span data-ttu-id="e0efb-208">Figura 9.</span><span class="sxs-lookup"><span data-stu-id="e0efb-208">Figure 9.</span></span> <span data-ttu-id="e0efb-209">Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="e0efb-209">Click Restart Now to exit Surface UEFI and restart the device</span></span>*

## <span data-ttu-id="e0efb-210">Schermate di avvio UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-210">Surface UEFI boot screens</span></span>

<span data-ttu-id="e0efb-211">Quando aggiorni il firmware del dispositivo Surface, tramite Windows Update o un'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma al successivo ciclo di riavvio.</span><span class="sxs-lookup"><span data-stu-id="e0efb-211">When you update Surface device firmware, by using either Windows Update or manual installation, the updates are not applied immediately to the device, but instead during the next reboot cycle.</span></span> <span data-ttu-id="e0efb-212">Puoi trovare ulteriori informazioni sul processo di aggiornamento del firmware di Surface in [Gestire gli aggiornamenti di driver e firmware Surface](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates).</span><span class="sxs-lookup"><span data-stu-id="e0efb-212">You can find out more about the Surface firmware update process in [Manage Surface driver and firmware updates](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates).</span></span> <span data-ttu-id="e0efb-213">Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su uno schermo con barre di stato di colori diversi per indicare il firmware di ogni componente.</span><span class="sxs-lookup"><span data-stu-id="e0efb-213">The progress of the firmware update is displayed on a screen with progress bars of differing colors to indicate the firmware for each component.</span></span> <span data-ttu-id="e0efb-214">La barra di stato di ogni componente viene visualizzata nelle figure da 9 a 18.</span><span class="sxs-lookup"><span data-stu-id="e0efb-214">Each component’s progress bar is shown in Figures 9 through 18.</span></span>

![Aggiornamento del firmware UEFI di Surface con barra di stato blu](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*<span data-ttu-id="e0efb-216">Figura 10.</span><span class="sxs-lookup"><span data-stu-id="e0efb-216">Figure 10.</span></span> <span data-ttu-id="e0efb-217">L'aggiornamento del firmware UEFI di Surface visualizza una barra di stato blu</span><span class="sxs-lookup"><span data-stu-id="e0efb-217">The Surface UEFI firmware update displays a blue progress bar</span></span>*

![Firmware del controller integrato di sistema con la barra di stato verde](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*<span data-ttu-id="e0efb-219">Figura 11.</span><span class="sxs-lookup"><span data-stu-id="e0efb-219">Figure 11.</span></span> <span data-ttu-id="e0efb-220">L'aggiornamento del firmware del controller integrato di sistema visualizza una barra di stato verde</span><span class="sxs-lookup"><span data-stu-id="e0efb-220">The System Embedded Controller firmware update displays a green progress bar</span></span>*

![Aggiornamento del firmware del controller SAM con barra di stato arancione](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*<span data-ttu-id="e0efb-222">Figura 12.</span><span class="sxs-lookup"><span data-stu-id="e0efb-222">Figure 12.</span></span> <span data-ttu-id="e0efb-223">L'aggiornamento del firmware del controller SAM visualizza una barra di stato arancione</span><span class="sxs-lookup"><span data-stu-id="e0efb-223">The SAM Controller firmware update displays an orange progress bar</span></span>*

![Firmware Intel Management Engine con barra di stato rosso](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*<span data-ttu-id="e0efb-225">Figura 13.</span><span class="sxs-lookup"><span data-stu-id="e0efb-225">Figure 13.</span></span> <span data-ttu-id="e0efb-226">L'aggiornamento del firmware Intel Management Engine visualizza una barra di stato rossa</span><span class="sxs-lookup"><span data-stu-id="e0efb-226">The Intel Management Engine firmware update displays a red progress bar</span></span>*

![Firmware di Surface touch con barra di stato grigia](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*<span data-ttu-id="e0efb-228">Figura 14.</span><span class="sxs-lookup"><span data-stu-id="e0efb-228">Figure 14.</span></span> <span data-ttu-id="e0efb-229">L'aggiornamento del firmware di Surface touch visualizza una barra di stato grigia</span><span class="sxs-lookup"><span data-stu-id="e0efb-229">The Surface touch firmware update displays a gray progress bar</span></span>*

![Firmware di Surface KIP con barra di avanzamento verde chiaro](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*<span data-ttu-id="e0efb-231">Figura 15.</span><span class="sxs-lookup"><span data-stu-id="e0efb-231">Figure 15.</span></span> <span data-ttu-id="e0efb-232">L'aggiornamento del firmware di Surface KIP Visualizza una barra di stato verde chiaro</span><span class="sxs-lookup"><span data-stu-id="e0efb-232">The Surface KIP firmware update displays a light green progress bar</span></span>*

![Superficie del firmware ISH con barra di avanzamento rosa](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*<span data-ttu-id="e0efb-234">Figura 16 la superficie dell'aggiornamento del firmware ISH Mostra una barra di avanzamento rosa chiaro</span><span class="sxs-lookup"><span data-stu-id="e0efb-234">Figure 16 The Surface ISH firmware update displays a light pink progress bar</span></span>*

![Firmware Surface trackpad con barra di avanzamento grigio](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*<span data-ttu-id="e0efb-236">Figura 17.</span><span class="sxs-lookup"><span data-stu-id="e0efb-236">Figure 17.</span></span> <span data-ttu-id="e0efb-237">L'aggiornamento del firmware Surface trackpad Visualizza una barra di stato rosa</span><span class="sxs-lookup"><span data-stu-id="e0efb-237">The Surface Trackpad firmware update displays a pink progress bar</span></span>*

![Firmware Surface TCON con indicatore di stato grigio chiaro](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*<span data-ttu-id="e0efb-239">Figura 18.</span><span class="sxs-lookup"><span data-stu-id="e0efb-239">Figure 18.</span></span> <span data-ttu-id="e0efb-240">L'aggiornamento del firmware Surface TCON Visualizza una barra di stato grigio chiaro</span><span class="sxs-lookup"><span data-stu-id="e0efb-240">The Surface TCON firmware update displays a light gray progress bar</span></span>*


![Firmware di Surface TPM con indicatore di stato viola chiaro](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*<span data-ttu-id="e0efb-242">Figura 19.</span><span class="sxs-lookup"><span data-stu-id="e0efb-242">Figure 19.</span></span> <span data-ttu-id="e0efb-243">L'aggiornamento del firmware Surface TPM Visualizza una barra di stato viola</span><span class="sxs-lookup"><span data-stu-id="e0efb-243">The Surface TPM firmware update displays a purple progress bar</span></span>*


>[!NOTE]
><span data-ttu-id="e0efb-244">Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio sicuro è disabilitato, come illustrato nella figura 19.</span><span class="sxs-lookup"><span data-stu-id="e0efb-244">An additional warning message that indicates Secure Boot is disabled is displayed, as shown in Figure 19.</span></span>

![Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*<span data-ttu-id="e0efb-246">Figura 20.</span><span class="sxs-lookup"><span data-stu-id="e0efb-246">Figure 20.</span></span> <span data-ttu-id="e0efb-247">Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-247">Surface boot screen that indicates Secure Boot has been disabled in Surface UEFI settings</span></span>*

## <span data-ttu-id="e0efb-248">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="e0efb-248">Related topics</span></span>

- [<span data-ttu-id="e0efb-249">Gestione di Intune delle impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="e0efb-249">Intune management of Surface UEFI settings</span></span>](surface-manage-dfci-guide.md)

-  [<span data-ttu-id="e0efb-250">Surface Enterprise Management Mode</span><span class="sxs-lookup"><span data-stu-id="e0efb-250">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)

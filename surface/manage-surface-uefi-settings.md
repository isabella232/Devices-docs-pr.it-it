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
ms.date: 04/13/2021
ms.openlocfilehash: ea995eda277ecf235eedd92f3af6edb0b60ae68a
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576506"
---
# <a name="manage-surface-uefi-settings"></a><span data-ttu-id="b97e6-104">Gestire le impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-104">Manage Surface UEFI settings</span></span>

 <span data-ttu-id="b97e6-105">I dispositivi Surface PC sono progettati per utilizzare un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft in modo specifico per questi dispositivi.</span><span class="sxs-lookup"><span data-stu-id="b97e6-105">Surface PC devices are designed to utilize a unique Unified Extensible Firmware Interface (UEFI) engineered by Microsoft specifically for these devices.</span></span> <span data-ttu-id="b97e6-106">Le impostazioni UEFI di Surface consentono di abilitare o disabilitare i dispositivi e i componenti incorporati, proteggere le impostazioni UEFI dalle modifiche e modificare le impostazioni di avvio dei dispositivi Surface.</span><span class="sxs-lookup"><span data-stu-id="b97e6-106">Surface UEFI settings provide the ability to enable or disable built-in devices and components, protect UEFI settings from being changed, and adjust the Surface device boot settings.</span></span> 

## <a name="supported-products"></a><span data-ttu-id="b97e6-107">Prodotti supportati</span><span class="sxs-lookup"><span data-stu-id="b97e6-107">Supported products</span></span>

<span data-ttu-id="b97e6-108">La gestione UEFI è supportata nei seguenti modi:</span><span class="sxs-lookup"><span data-stu-id="b97e6-108">UEFI management is supported on the following:</span></span> 

- <span data-ttu-id="b97e6-109">Surface Pro 4, Surface Pro (5° generazione), Surface Pro 6, Surface Pro 7, Surface Pro 7+, Surface Pro X</span><span class="sxs-lookup"><span data-stu-id="b97e6-109">Surface Pro 4, Surface Pro (5th Gen), Surface Pro 6, Surface Pro 7, Surface Pro 7+, Surface Pro X</span></span>
- <span data-ttu-id="b97e6-110">Surface Laptop (prima generazione), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4</span><span class="sxs-lookup"><span data-stu-id="b97e6-110">Surface Laptop (1st Gen), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4</span></span>
- <span data-ttu-id="b97e6-111">Surface Studio (prima generazione), Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="b97e6-111">Surface Studio (1st Gen), Surface Studio 2</span></span>
- <span data-ttu-id="b97e6-112">Surface Book, Surface Book 2, Surface Book 3</span><span class="sxs-lookup"><span data-stu-id="b97e6-112">Surface Book, Surface Book 2, Surface Book 3</span></span>
- <span data-ttu-id="b97e6-113">Surface Go, Surface Go 2[ <sup> 1 </sup> ](#references)</span><span class="sxs-lookup"><span data-stu-id="b97e6-113">Surface Go, Surface Go 2[<sup>1</sup>](#references)</span></span>

## <a name="support-for-cloud-based-management"></a><span data-ttu-id="b97e6-114">Supporto per la gestione basata su cloud</span><span class="sxs-lookup"><span data-stu-id="b97e6-114">Support for cloud-based management</span></span>

<span data-ttu-id="b97e6-115">Con i profili DFCI (Device Firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in anteprima pubblica), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI.</span><span class="sxs-lookup"><span data-stu-id="b97e6-115">With Device Firmware Configuration Interface (DFCI) profiles built into Microsoft Intune (now available in public preview), Surface UEFI management extends the modern management stack down to the UEFI hardware level.</span></span> <span data-ttu-id="b97e6-116">DFCI supporta il provisioning a tocco zero, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, tra cui le opzioni di avvio e le periferiche incorporate, e costituisce le basi per scenari di sicurezza avanzati in futuro.</span><span class="sxs-lookup"><span data-stu-id="b97e6-116">DFCI supports zero-touch provisioning, eliminates BIOS passwords, provides control of security settings including boot options and built-in peripherals, and lays the groundwork for advanced security scenarios in the future.</span></span> <span data-ttu-id="b97e6-117">DFCI è attualmente disponibile per Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7 e Surface Pro X.  Per altre informazioni, fai riferimento alla [gestione di Intune delle impostazioni UEFI di Surface.](surface-manage-dfci-guide.md)</span><span class="sxs-lookup"><span data-stu-id="b97e6-117">DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7, and Surface Pro X.  For more information, refer to [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <a name="open-surface-uefi-menu"></a><span data-ttu-id="b97e6-118">Apri il menu UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-118">Open Surface UEFI menu</span></span>

<span data-ttu-id="b97e6-119">Per modificare le impostazioni UEFI durante l'avvio del sistema:</span><span class="sxs-lookup"><span data-stu-id="b97e6-119">To adjust UEFI settings during system startup:</span></span>

1. <span data-ttu-id="b97e6-120">Arresta Surface e attendi circa 10 secondi per assicurarti che sia spento.</span><span class="sxs-lookup"><span data-stu-id="b97e6-120">Shut down your Surface and wait about 10 seconds to make sure it's off.</span></span>
2. <span data-ttu-id="b97e6-121">Tenere premuto il **pulsante Volume-up** e, contemporaneamente, premere e rilasciare il **pulsante Di alimentazione.**</span><span class="sxs-lookup"><span data-stu-id="b97e6-121">Press and hold the **Volume-up** button  and - at the same time - press and release the **Power button.**</span></span>
3. <span data-ttu-id="b97e6-122">Man mano che sullo schermo viene visualizzato il logo Microsoft o Surface, continua a tenere premuto il pulsante **Volume-up** finché non viene visualizzata la schermata UEFI.</span><span class="sxs-lookup"><span data-stu-id="b97e6-122">As the Microsoft or Surface logo appears on your screen, continue to hold the **Volume-up** button until the UEFI screen appears.</span></span>

## <a name="uefi-pc-information-page"></a><span data-ttu-id="b97e6-123">Pagina informazioni PC UEFI</span><span class="sxs-lookup"><span data-stu-id="b97e6-123">UEFI PC information page</span></span>

<span data-ttu-id="b97e6-124">La pagina delle informazioni sul PC include informazioni dettagliate sul dispositivo Surface:</span><span class="sxs-lookup"><span data-stu-id="b97e6-124">The PC information page includes detailed information about your Surface device:</span></span> 

- <span data-ttu-id="b97e6-125">**Modello:** il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7.</span><span class="sxs-lookup"><span data-stu-id="b97e6-125">**Model** – Your Surface device’s model will be displayed here, such as Surface Book 2 or Surface Pro 7.</span></span> <span data-ttu-id="b97e6-126">L'esatta configurazione del dispositivo non viene visualizzata, ad esempio processore, dimensioni dei dischi o dimensioni della memoria.</span><span class="sxs-lookup"><span data-stu-id="b97e6-126">The exact configuration of your device is not shown, (such as processor, disk size, or memory size).</span></span> 
- <span data-ttu-id="b97e6-127">**UUID**: codice Universally Unique Identification specifico del dispositivo e usato per identificare il dispositivo durante la distribuzione o la gestione.</span><span class="sxs-lookup"><span data-stu-id="b97e6-127">**UUID** – This Universally Unique Identification number is specific to your device and is used to identify the device during deployment or management.</span></span> 

- <span data-ttu-id="b97e6-128">**Serial Number**: numero usato per identificare questo dispositivo Surface specifico per gli scenari di tag asset e supporto.</span><span class="sxs-lookup"><span data-stu-id="b97e6-128">**Serial Number** – This number is used to identify this specific Surface device for asset tagging and support scenarios.</span></span>
- <span data-ttu-id="b97e6-129">**Asset Tag**: tag asset assegnato al dispositivo Surface tramite [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span><span class="sxs-lookup"><span data-stu-id="b97e6-129">**Asset Tag** – The asset tag is assigned to the Surface device with the [Asset Tag Tool](https://docs.microsoft.com/surface/assettag).</span></span> 

<span data-ttu-id="b97e6-130">Qui troverai anche informazioni dettagliate sul firmware del tuo dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="b97e6-130">You will also find detailed information about the firmware of your Surface device.</span></span> <span data-ttu-id="b97e6-131">I dispositivi Surface hanno svariati componenti interni, ognuno dei quali esegue versioni diverse del firmware.</span><span class="sxs-lookup"><span data-stu-id="b97e6-131">Surface devices have several internal components that each run different versions of firmware.</span></span> <span data-ttu-id="b97e6-132">La versione del firmware di ognuno dei dispositivi seguenti viene visualizzata nella pagina **PC information** (mostrata nella figura 1):</span><span class="sxs-lookup"><span data-stu-id="b97e6-132">The firmware version of each of the following devices is displayed on the **PC information** page (as shown in Figure 1):</span></span> 

- <span data-ttu-id="b97e6-133">UEFI di sistema</span><span class="sxs-lookup"><span data-stu-id="b97e6-133">System UEFI</span></span> 

- <span data-ttu-id="b97e6-134">Controller SAM</span><span class="sxs-lookup"><span data-stu-id="b97e6-134">SAM Controller</span></span> 

- <span data-ttu-id="b97e6-135">Intel Management Engine</span><span class="sxs-lookup"><span data-stu-id="b97e6-135">Intel Management Engine</span></span> 

- <span data-ttu-id="b97e6-136">Controller integrato di sistema</span><span class="sxs-lookup"><span data-stu-id="b97e6-136">System Embedded Controller</span></span> 

- <span data-ttu-id="b97e6-137">Firmware per il tocco</span><span class="sxs-lookup"><span data-stu-id="b97e6-137">Touch Firmware</span></span> 

![Informazioni di sistema e informazioni sulla versione del firmware](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*<span data-ttu-id="b97e6-139">Figura 1.</span><span class="sxs-lookup"><span data-stu-id="b97e6-139">Figure 1.</span></span> <span data-ttu-id="b97e6-140">Informazioni di sistema e informazioni sulla versione del firmware</span><span class="sxs-lookup"><span data-stu-id="b97e6-140">System information and firmware version information</span></span>*

<span data-ttu-id="b97e6-141">Puoi trovare informazioni aggiornate sulla versione più recente del firmware per il dispositivo Surface nella pagina [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) per il tuo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b97e6-141">You can find up-to-date information about the latest firmware version for your Surface device in the [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) for your device.</span></span> 

## <a name="uefi-security-page"></a><span data-ttu-id="b97e6-142">Pagina Sicurezza UEFI</span><span class="sxs-lookup"><span data-stu-id="b97e6-142">UEFI Security page</span></span> 

![Configurazione delle impostazioni di sicurezza UEFI di Surface](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*<span data-ttu-id="b97e6-144">Figura 2.</span><span class="sxs-lookup"><span data-stu-id="b97e6-144">Figure 2.</span></span> <span data-ttu-id="b97e6-145">Configurazione delle impostazioni di sicurezza UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-145">Configure Surface UEFI security settings</span></span>*

<span data-ttu-id="b97e6-146">La pagina Sicurezza consente di impostare una password per proteggere le impostazioni UEFI.</span><span class="sxs-lookup"><span data-stu-id="b97e6-146">The Security page allows you to set a password to protect UEFI settings.</span></span> <span data-ttu-id="b97e6-147">Questa password deve essere immessa quando avvii il dispositivo Surface in UEFI.</span><span class="sxs-lookup"><span data-stu-id="b97e6-147">This password must be entered when you boot the Surface device to UEFI.</span></span> <span data-ttu-id="b97e6-148">La password può contenere i caratteri seguenti (come illustrato nella figura 3):</span><span class="sxs-lookup"><span data-stu-id="b97e6-148">The password can contain the following characters (as shown in Figure 3):</span></span> 

- <span data-ttu-id="b97e6-149">Lettere maiuscole: A-Z</span><span class="sxs-lookup"><span data-stu-id="b97e6-149">Uppercase letters: A-Z</span></span> 

- <span data-ttu-id="b97e6-150">Lettere minuscole: a-z</span><span class="sxs-lookup"><span data-stu-id="b97e6-150">Lowercase letters: a-z</span></span> 

- <span data-ttu-id="b97e6-151">Numeri: 1-0</span><span class="sxs-lookup"><span data-stu-id="b97e6-151">Numbers: 1-0</span></span> 

- <span data-ttu-id="b97e6-152">Caratteri speciali: !@#$%^&\*()?<>{} []-_=+|.,;:'""</span><span class="sxs-lookup"><span data-stu-id="b97e6-152">Special characters: !@#$%^&\*()?<>{}[]-_=+|.,;:’\`”</span></span> 

<span data-ttu-id="b97e6-153">La password deve contenere almeno 6 caratteri e fa distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="b97e6-153">The password must be at least 6 characters and is case sensitive.</span></span> 

![Aggiunta di una password per proteggere le impostazioni UEFI di Surface](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*<span data-ttu-id="b97e6-155">Figura 3.</span><span class="sxs-lookup"><span data-stu-id="b97e6-155">Figure 3.</span></span> <span data-ttu-id="b97e6-156">Aggiunta di una password per proteggere le impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-156">Add a password to protect Surface UEFI settings</span></span>*

<span data-ttu-id="b97e6-157">Nella pagina Security puoi anche modificare la configurazione di Avvio protetto nel tuo dispositivo Surface.</span><span class="sxs-lookup"><span data-stu-id="b97e6-157">On the Security page you can also change the configuration of Secure Boot on your Surface device.</span></span> <span data-ttu-id="b97e6-158">La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit.</span><span class="sxs-lookup"><span data-stu-id="b97e6-158">Secure Boot technology prevents unauthorized boot code from booting on your Surface device, which protects against bootkit and rootkit-type malware infections.</span></span> <span data-ttu-id="b97e6-159">Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti.</span><span class="sxs-lookup"><span data-stu-id="b97e6-159">You can disable Secure Boot to allow your Surface device to boot third-party operating systems or bootable media.</span></span> <span data-ttu-id="b97e6-160">È inoltre possibile configurare l'avvio protetto per l'utilizzo con certificati di terze parti, come illustrato nella figura 4.</span><span class="sxs-lookup"><span data-stu-id="b97e6-160">You can also configure Secure Boot to work with third-party certificates, as shown in Figure 4.</span></span> <span data-ttu-id="b97e6-161">Per altre informazioni, vedi [Avvio protetto](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) nella Libreria TechNet.</span><span class="sxs-lookup"><span data-stu-id="b97e6-161">Read more about [Secure Boot](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) in the TechNet Library.</span></span>

![Configurazione di Avvio protetto](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*<span data-ttu-id="b97e6-163">Figura 4.</span><span class="sxs-lookup"><span data-stu-id="b97e6-163">Figure 4.</span></span> <span data-ttu-id="b97e6-164">Configurazione di Avvio protetto</span><span class="sxs-lookup"><span data-stu-id="b97e6-164">Configure Secure Boot</span></span>*

<span data-ttu-id="b97e6-165">A seconda del dispositivo, potresti anche essere in grado di vedere se il TPM è abilitato o disabilitato.</span><span class="sxs-lookup"><span data-stu-id="b97e6-165">Depending on your device, you may also be able to see if your TPM is enabled or disabled.</span></span> <span data-ttu-id="b97e6-166">Se non viene visualizzata l'impostazione **Abilita TPM,** aprire tpm.msc in Windows per verificare lo stato, come illustrato nella figura 5.</span><span class="sxs-lookup"><span data-stu-id="b97e6-166">If you do not see the **Enable TPM**  setting, open tpm.msc in Windows to check the status, as shown in Figure 5.</span></span> <span data-ttu-id="b97e6-167">Il dispositivo TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker.</span><span class="sxs-lookup"><span data-stu-id="b97e6-167">The TPM is used to authenticate encryption for your device’s data with BitLocker.</span></span> <span data-ttu-id="b97e6-168">Per ulteriori informazioni, vedere [BitLocker panoramica.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)</span><span class="sxs-lookup"><span data-stu-id="b97e6-168">To learn more, see [BitLocker overview](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview).</span></span> 

![Console TPM](images/manage-surface-uefi-fig5-a.png "TPM console")

*<span data-ttu-id="b97e6-170">Figura 5.</span><span class="sxs-lookup"><span data-stu-id="b97e6-170">Figure 5.</span></span> <span data-ttu-id="b97e6-171">Console TPM</span><span class="sxs-lookup"><span data-stu-id="b97e6-171">TPM console</span></span>*


## <a name="uefi-menu-devices"></a><span data-ttu-id="b97e6-172">Menu UEFI: dispositivi</span><span class="sxs-lookup"><span data-stu-id="b97e6-172">UEFI menu: Devices</span></span> 

<span data-ttu-id="b97e6-173">La pagina Dispositivi consente di abilitare o disabilitare dispositivi e componenti specifici, tra cui:</span><span class="sxs-lookup"><span data-stu-id="b97e6-173">The Devices page allows you to  enable or disable specific devices and components including:</span></span>

- <span data-ttu-id="b97e6-174">Alloggiamento di espansione e porte USB</span><span class="sxs-lookup"><span data-stu-id="b97e6-174">Docking and USB Ports</span></span> 

- <span data-ttu-id="b97e6-175">Slot per scheda microSD o SD</span><span class="sxs-lookup"><span data-stu-id="b97e6-175">MicroSD or SD Card Slot</span></span> 

- <span data-ttu-id="b97e6-176">Fotocamera posteriore</span><span class="sxs-lookup"><span data-stu-id="b97e6-176">Rear Camera</span></span> 

- <span data-ttu-id="b97e6-177">Fotocamera anteriore</span><span class="sxs-lookup"><span data-stu-id="b97e6-177">Front Camera</span></span> 

- <span data-ttu-id="b97e6-178">Fotocamera a infrarossi</span><span class="sxs-lookup"><span data-stu-id="b97e6-178">Infrared (IR) Camera</span></span> 

- <span data-ttu-id="b97e6-179">Wi-Fi e Bluetooth</span><span class="sxs-lookup"><span data-stu-id="b97e6-179">Wi-Fi and Bluetooth</span></span> 

- <span data-ttu-id="b97e6-180">Audio integrato (altoparlanti e microfono)</span><span class="sxs-lookup"><span data-stu-id="b97e6-180">Onboard Audio (Speakers and Microphone)</span></span> 

<span data-ttu-id="b97e6-181">Ogni dispositivo è elencato con un pulsante del dispositivo di scorrimento che puoi spostare nella posizione **Attivato** (abilitato) o **Disattivato** (disabilitato), come illustrato nella figura 6.</span><span class="sxs-lookup"><span data-stu-id="b97e6-181">Each device is listed with a slider button that you can move to **On** (enabled) or **Off** (disabled) position, as shown in Figure 6.</span></span> 

![Abilitazione e disabilitazione di dispositivi specifici](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*<span data-ttu-id="b97e6-183">Figura 6.</span><span class="sxs-lookup"><span data-stu-id="b97e6-183">Figure 6.</span></span> <span data-ttu-id="b97e6-184">Abilitazione e disabilitazione di dispositivi specifici</span><span class="sxs-lookup"><span data-stu-id="b97e6-184">Enable and disable specific devices</span></span>*

## <a name="uefi-menu-boot-configuration"></a><span data-ttu-id="b97e6-185">Menu UEFI: Configurazione di avvio</span><span class="sxs-lookup"><span data-stu-id="b97e6-185">UEFI menu: Boot configuration</span></span> 

<span data-ttu-id="b97e6-186">La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio, nonché di abilitare o disabilitare l'avvio dei dispositivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="b97e6-186">The Boot Configuration page allows you to change the order of your boot devices as well as enable or disable boot of the following devices:</span></span> 

- <span data-ttu-id="b97e6-187">Windows Boot Manager</span><span class="sxs-lookup"><span data-stu-id="b97e6-187">Windows Boot Manager</span></span> 

- <span data-ttu-id="b97e6-188">Archiviazione USB</span><span class="sxs-lookup"><span data-stu-id="b97e6-188">USB Storage</span></span> 

- <span data-ttu-id="b97e6-189">Rete PXE</span><span class="sxs-lookup"><span data-stu-id="b97e6-189">PXE Network</span></span> 

- <span data-ttu-id="b97e6-190">Archiviazione interna</span><span class="sxs-lookup"><span data-stu-id="b97e6-190">Internal Storage</span></span> 

<span data-ttu-id="b97e6-191">Puoi eseguire l'avvio da un dispositivo specifico immediatamente oppure puoi scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen.</span><span class="sxs-lookup"><span data-stu-id="b97e6-191">You can boot from a specific device immediately, or you can swipe left on that device’s entry in the list using the touchscreen.</span></span> <span data-ttu-id="b97e6-192">Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="b97e6-192">You can also boot immediately to a USB device or USB Ethernet adapter when the Surface device is powered off by pressing the **Volume Down** button and the **Power** button simultaneously.</span></span> 

<span data-ttu-id="b97e6-193">Per fare in modo che l'ordine di avvio specificato sia attivo, è necessario impostare l'opzione **Abilita sequenza di** avvio alternativa su **On,** come illustrato nella figura 7.</span><span class="sxs-lookup"><span data-stu-id="b97e6-193">For the specified boot order to take effect, you must set the **Enable Alternate Boot Sequence** option to **On**, as shown in Figure 7.</span></span> 

![Configurazione dell'ordine di avvio per il dispositivo Surface](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*<span data-ttu-id="b97e6-195">Figura 7.</span><span class="sxs-lookup"><span data-stu-id="b97e6-195">Figure 7.</span></span> <span data-ttu-id="b97e6-196">Configurazione dell'ordine di avvio per il dispositivo Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-196">Configure the boot order for your Surface device</span></span>* 

<span data-ttu-id="b97e6-197">Poi anche attivare o disattivare il supporto IPv6 per PXE con l'opzione **Enable IPv6 for PXE Network Boot**, ad esempio quando esegui una distribuzione di Windows con PXE in cui il server PXE è configurato solo per IPv4.</span><span class="sxs-lookup"><span data-stu-id="b97e6-197">You can also turn on and off IPv6 support for PXE with the **Enable IPv6 for PXE Network Boot** option, for example when performing a Windows deployment using PXE where the PXE server is configured for IPv4 only.</span></span>  

## <a name="uefi-menu-management"></a><span data-ttu-id="b97e6-198">Menu UEFI: Gestione</span><span class="sxs-lookup"><span data-stu-id="b97e6-198">UEFI menu: Management</span></span>
<span data-ttu-id="b97e6-199">La pagina Gestione consente di gestire l'uso di Zero Touch UEFI Management e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 7, Surface Pro X e Surface Laptop 3.</span><span class="sxs-lookup"><span data-stu-id="b97e6-199">The Management page allows you to manage use of Zero Touch UEFI Management and other features on eligible devices including Surface Pro 7, Surface Pro X, and Surface Laptop 3.</span></span>  

![<span data-ttu-id="b97e6-200">Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *figura 8. Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità*</span><span class="sxs-lookup"><span data-stu-id="b97e6-200">Manage access to Zero Touch UEFI Management and other features](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
*Figure 8. Manage access to Zero Touch UEFI Management and other features*</span></span> 


<span data-ttu-id="b97e6-201">Zero Touch UEFI Management consente di gestire in remoto le impostazioni UEFI usando un profilo del dispositivo in Intune denominato Device Firmware Configuration Interface (DFCI).</span><span class="sxs-lookup"><span data-stu-id="b97e6-201">Zero Touch UEFI Management lets you remotely manage UEFI settings  by using a device profile within Intune called Device Firmware Configuration Interface (DFCI).</span></span> <span data-ttu-id="b97e6-202">Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **Pronto.**</span><span class="sxs-lookup"><span data-stu-id="b97e6-202">If you do not configure this setting, the ability to manage eligible devices with DFCI is set to **Ready**.</span></span> <span data-ttu-id="b97e6-203">Per impedire la DFCI, selezionare **Rifiuta.**</span><span class="sxs-lookup"><span data-stu-id="b97e6-203">To prevent DFCI, select **Opt-Out**.</span></span> 

> [!NOTE]
> <span data-ttu-id="b97e6-204">La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono attualmente disponibili per Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Pro 7 e Surface Pro X. Per altre informazioni, vedi [Gestione di Intune delle impostazioni UEFI di Surface.](surface-manage-dfci-guide.md)</span><span class="sxs-lookup"><span data-stu-id="b97e6-204">The UEFI Management settings page and use of DFCI is currently available for Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Pro 7, and Surface Pro X. To learn more, see [Intune management of Surface UEFI settings](surface-manage-dfci-guide.md).</span></span>

## <a name="uefi-menu-exit"></a><span data-ttu-id="b97e6-205">Menu UEFI: Esci</span><span class="sxs-lookup"><span data-stu-id="b97e6-205">UEFI menu: Exit</span></span> 

<span data-ttu-id="b97e6-206">Utilizzare il **pulsante Riavvia** ora nella **pagina Esci** per uscire da impostazioni UEFI, come illustrato nella figura 9.</span><span class="sxs-lookup"><span data-stu-id="b97e6-206">Use the **Restart Now** button on the **Exit** page to exit UEFI settings, as shown in Figure 9.</span></span> 

![Chiusura delle impostazioni UEFI di Surface e riavvio del dispositivo](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*<span data-ttu-id="b97e6-208">Figura 9.</span><span class="sxs-lookup"><span data-stu-id="b97e6-208">Figure 9.</span></span> <span data-ttu-id="b97e6-209">Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo</span><span class="sxs-lookup"><span data-stu-id="b97e6-209">Click Restart Now to exit Surface UEFI and restart the device</span></span>*

## <a name="surface-uefi-boot-screens"></a><span data-ttu-id="b97e6-210">Schermate di avvio UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-210">Surface UEFI boot screens</span></span>

<span data-ttu-id="b97e6-211">Quando aggiorni il firmware del dispositivo Surface, tramite Windows Update o un'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma al successivo ciclo di riavvio.</span><span class="sxs-lookup"><span data-stu-id="b97e6-211">When you update Surface device firmware, by using either Windows Update or manual installation, the updates are not applied immediately to the device, but instead during the next reboot cycle.</span></span> <span data-ttu-id="b97e6-212">Per altre informazioni sul processo di aggiornamento del firmware di Surface, vedere Gestire e distribuire gli aggiornamenti di driver e [firmware di Surface.](manage-surface-driver-and-firmware-updates.md)</span><span class="sxs-lookup"><span data-stu-id="b97e6-212">You can find out more about the Surface firmware update process in [Manage and deploy Surface driver and firmware updates](manage-surface-driver-and-firmware-updates.md).</span></span> <span data-ttu-id="b97e6-213">Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su uno schermo con barre di stato di colori diversi per indicare il firmware di ogni componente.</span><span class="sxs-lookup"><span data-stu-id="b97e6-213">The progress of the firmware update is displayed on a screen with progress bars of differing colors to indicate the firmware for each component.</span></span> <span data-ttu-id="b97e6-214">L'indicatore di stato di ogni componente viene visualizzato nelle figure da 9 a 18.</span><span class="sxs-lookup"><span data-stu-id="b97e6-214">Each component’s progress bar is shown in Figures 9 through 18.</span></span>

![Aggiornamento del firmware UEFI di Surface con barra di stato blu](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*<span data-ttu-id="b97e6-216">Figura 10.</span><span class="sxs-lookup"><span data-stu-id="b97e6-216">Figure 10.</span></span> <span data-ttu-id="b97e6-217">L'aggiornamento del firmware UEFI di Surface visualizza una barra di stato blu</span><span class="sxs-lookup"><span data-stu-id="b97e6-217">The Surface UEFI firmware update displays a blue progress bar</span></span>*

![Firmware del controller integrato di sistema con la barra di stato verde](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*<span data-ttu-id="b97e6-219">Figura 11.</span><span class="sxs-lookup"><span data-stu-id="b97e6-219">Figure 11.</span></span> <span data-ttu-id="b97e6-220">L'aggiornamento del firmware del controller integrato di sistema visualizza una barra di stato verde</span><span class="sxs-lookup"><span data-stu-id="b97e6-220">The System Embedded Controller firmware update displays a green progress bar</span></span>*

![Aggiornamento del firmware del controller SAM con barra di stato arancione](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*<span data-ttu-id="b97e6-222">Figura 12.</span><span class="sxs-lookup"><span data-stu-id="b97e6-222">Figure 12.</span></span> <span data-ttu-id="b97e6-223">L'aggiornamento del firmware del controller SAM visualizza una barra di stato arancione</span><span class="sxs-lookup"><span data-stu-id="b97e6-223">The SAM Controller firmware update displays an orange progress bar</span></span>*

![Firmware Intel Management Engine con barra di stato rosso](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*<span data-ttu-id="b97e6-225">Figura 13.</span><span class="sxs-lookup"><span data-stu-id="b97e6-225">Figure 13.</span></span> <span data-ttu-id="b97e6-226">L'aggiornamento del firmware Intel Management Engine visualizza una barra di stato rossa</span><span class="sxs-lookup"><span data-stu-id="b97e6-226">The Intel Management Engine firmware update displays a red progress bar</span></span>*

![Firmware di Surface touch con barra di stato grigia](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*<span data-ttu-id="b97e6-228">Figura 14.</span><span class="sxs-lookup"><span data-stu-id="b97e6-228">Figure 14.</span></span> <span data-ttu-id="b97e6-229">L'aggiornamento del firmware di Surface touch visualizza una barra di stato grigia</span><span class="sxs-lookup"><span data-stu-id="b97e6-229">The Surface touch firmware update displays a gray progress bar</span></span>*

![Firmware Surface KIP con indicatore di stato verde chiaro](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*<span data-ttu-id="b97e6-231">Figura 15.</span><span class="sxs-lookup"><span data-stu-id="b97e6-231">Figure 15.</span></span> <span data-ttu-id="b97e6-232">L'aggiornamento del firmware di Surface KIP visualizza un indicatore di stato verde chiaro</span><span class="sxs-lookup"><span data-stu-id="b97e6-232">The Surface KIP firmware update displays a light green progress bar</span></span>*

![Firmware ISH surface con barra di avanzamento rosa](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*<span data-ttu-id="b97e6-234">Figura 16 L'aggiornamento del firmware ISH di Surface visualizza un indicatore di stato rosa chiaro</span><span class="sxs-lookup"><span data-stu-id="b97e6-234">Figure 16 The Surface ISH firmware update displays a light pink progress bar</span></span>*

![Firmware Surface Trackpad con indicatore di stato grigio](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*<span data-ttu-id="b97e6-236">Figura 17.</span><span class="sxs-lookup"><span data-stu-id="b97e6-236">Figure 17.</span></span> <span data-ttu-id="b97e6-237">L'aggiornamento del firmware di Surface Trackpad visualizza un indicatore di stato rosa</span><span class="sxs-lookup"><span data-stu-id="b97e6-237">The Surface Trackpad firmware update displays a pink progress bar</span></span>*

![Firmware Surface TCON con indicatore di stato grigio chiaro](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*<span data-ttu-id="b97e6-239">Figura 18.</span><span class="sxs-lookup"><span data-stu-id="b97e6-239">Figure 18.</span></span> <span data-ttu-id="b97e6-240">L'aggiornamento del firmware TCON di Surface visualizza un indicatore di stato grigio chiaro</span><span class="sxs-lookup"><span data-stu-id="b97e6-240">The Surface TCON firmware update displays a light gray progress bar</span></span>*


![Firmware TPM surface con indicatore di stato viola chiaro](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*<span data-ttu-id="b97e6-242">Figura 19.</span><span class="sxs-lookup"><span data-stu-id="b97e6-242">Figure 19.</span></span> <span data-ttu-id="b97e6-243">L'aggiornamento del firmware TPM di Surface visualizza un indicatore di stato viola</span><span class="sxs-lookup"><span data-stu-id="b97e6-243">The Surface TPM firmware update displays a purple progress bar</span></span>*


>[!NOTE]
><span data-ttu-id="b97e6-244">Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio protetto è disabilitato, come illustrato nella figura 19.</span><span class="sxs-lookup"><span data-stu-id="b97e6-244">An additional warning message that indicates Secure Boot is disabled is displayed, as shown in Figure 19.</span></span>

![Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*<span data-ttu-id="b97e6-246">Figura 20.</span><span class="sxs-lookup"><span data-stu-id="b97e6-246">Figure 20.</span></span> <span data-ttu-id="b97e6-247">Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-247">Surface boot screen that indicates Secure Boot has been disabled in Surface UEFI settings</span></span>*

## <a name="references"></a><span data-ttu-id="b97e6-248">Riferimenti</span><span class="sxs-lookup"><span data-stu-id="b97e6-248">References</span></span>

1. <span data-ttu-id="b97e6-249">Surface Go e Surface Go 2 usano un UEFI di terze parti e non supportano DFCI.</span><span class="sxs-lookup"><span data-stu-id="b97e6-249">Surface Go and Surface Go 2 use a third-party UEFI and do not support DFCI.</span></span> 

## <a name="related-topics"></a><span data-ttu-id="b97e6-250">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="b97e6-250">Related topics</span></span>

- [<span data-ttu-id="b97e6-251">Gestione di Intune delle impostazioni UEFI di Surface</span><span class="sxs-lookup"><span data-stu-id="b97e6-251">Intune management of Surface UEFI settings</span></span>](surface-manage-dfci-guide.md)

-  [<span data-ttu-id="b97e6-252">Surface Enterprise Management Mode</span><span class="sxs-lookup"><span data-stu-id="b97e6-252">Surface Enterprise Management Mode</span></span>](surface-enterprise-management-mode.md)

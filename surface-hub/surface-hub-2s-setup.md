---
title: Configurazione per la prima volta per Surface Hub 2S
description: Informazioni su come completare la configurazione per la prima volta per Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 47a393944c1b524931a6ac56962cc2cd60786007
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833609"
---
# <span data-ttu-id="b196e-104">Configurazione per la prima volta per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="b196e-104">First time Setup for Surface Hub 2S</span></span>

<span data-ttu-id="b196e-105">Quando si avvia Surface Hub 2S per la prima volta, il dispositivo entra automaticamente nella modalità di configurazione iniziale per guidarti attraverso la configurazione dell'account e le impostazioni correlate.</span><span class="sxs-lookup"><span data-stu-id="b196e-105">When you first start Surface Hub 2S, the device automatically enters first time Setup mode to guide you through account configuration and related settings.</span></span>

## <span data-ttu-id="b196e-106">Configurazione dell'account di Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="b196e-106">Configuring Surface Hub 2S account</span></span>

1. **<span data-ttu-id="b196e-107">Configurare le impostazioni locali.</span><span class="sxs-lookup"><span data-stu-id="b196e-107">Configure your locale.</span></span>** <span data-ttu-id="b196e-108">Immettere le informazioni relative a area, lingua, layout di tastiera e fuso orario.</span><span class="sxs-lookup"><span data-stu-id="b196e-108">Enter region, language, keyboard layout and time zone information.</span></span> <span data-ttu-id="b196e-109">Seleziona **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b196e-109">Select **Next**.</span></span>

   ![\* Configurare le impostazioni locali \*](images/sh2-run1.png) <br>
1. **<span data-ttu-id="b196e-111">Connettersi a una rete wireless.</span><span class="sxs-lookup"><span data-stu-id="b196e-111">Connect  to a wireless network.</span></span>** <span data-ttu-id="b196e-112">Scegliere la rete wireless preferita e quindi fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="b196e-112">Choose your preferred wireless network and select **Next.**</span></span>

- <span data-ttu-id="b196e-113">Questa opzione non viene visualizzata se connessa tramite un cavo Ethernet.</span><span class="sxs-lookup"><span data-stu-id="b196e-113">This option is not shown if connected using an Ethernet cable.</span></span>
- <span data-ttu-id="b196e-114">Non è possibile connettersi a una rete wireless in hotspot (portali captive) che reindirizza le richieste di accesso al sito Web del provider.</span><span class="sxs-lookup"><span data-stu-id="b196e-114">You cannot connect to a wireless network in hotspots (captive portals) that redirect sign-in requests to a provider’s website.</span></span>

3. **<span data-ttu-id="b196e-115">Immettere le informazioni sull'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b196e-115">Enter device account info.</span></span>** <span data-ttu-id="b196e-116">USA **dominio\utente** per ambienti locali e ibridi e per gli **utenti \ @example. com** per gli ambienti online.</span><span class="sxs-lookup"><span data-stu-id="b196e-116">Use **domain\user** for on-premises and hybrid environments and **user\@example.com** for online environments.</span></span> <span data-ttu-id="b196e-117">Selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="b196e-117">Select **Next.**</span></span>

   ![\* Immettere le informazioni sull'account del dispositivo \*](images/sh2-run2.png) <br>
1. **<span data-ttu-id="b196e-119">Immettere altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="b196e-119">Enter additional info.</span></span>** <span data-ttu-id="b196e-120">Se richiesto, specificare l'indirizzo del server di Exchange e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="b196e-120">If requested, provide your Exchange server address and then select **Next.**</span></span>

    ![\* Immettere altre info; ad esempio, Exchange Server Name \*](images/sh2-run3.png) <br>

1. **<span data-ttu-id="b196e-122">Assegnare un nome al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b196e-122">Name this device.</span></span>** <span data-ttu-id="b196e-123">Immettere un nome per il dispositivo oppure usare quello suggerito in base al nome visualizzato dell'account e al nome del principio utente [UPN].</span><span class="sxs-lookup"><span data-stu-id="b196e-123">Enter a name for your device or use the suggested one based on your account’s display name and user principle name [UPN].</span></span> <span data-ttu-id="b196e-124">**Selezionare Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b196e-124">**Select Next**.</span></span>

- <span data-ttu-id="b196e-125">Il **nome descrittivo** è visibile nell'angolo in basso a sinistra di Surface Hub 2S e viene visualizzato durante la proiezione al dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b196e-125">The **Friendly name** is visible on the bottom left corner of Surface Hub 2S and is shown when projecting to the device.</span></span>

- <span data-ttu-id="b196e-126">Il **nome del dispositivo** identifica il dispositivo quando è affiliato a Active Directory o Azure Active Directory e quando si iscrive il dispositivo con Intune.</span><span class="sxs-lookup"><span data-stu-id="b196e-126">The **Device name** identifies the device when affiliated with Active Directory or Azure Active Directory, and when enrolling the device with Intune.</span></span>

  ![\* Assegnare un nome al dispositivo \*](images/sh2-run4.png) <br>
 
## <span data-ttu-id="b196e-128">Configurazione degli account di amministratore del dispositivo</span><span class="sxs-lookup"><span data-stu-id="b196e-128">Configuring device admin accounts</span></span>

<span data-ttu-id="b196e-129">È possibile configurare gli amministratori del dispositivo solo durante la configurazione per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="b196e-129">You can only set up device admins during first time Setup.</span></span> <span data-ttu-id="b196e-130">Per altre informazioni, vedere [affiliazione al dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation).</span><span class="sxs-lookup"><span data-stu-id="b196e-130">For more information, refer to [Surface Hub 2S device affiliation](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation).</span></span>

 <span data-ttu-id="b196e-131">Nella finestra di **dialogo amministratori per il dispositivo** selezionare una delle opzioni seguenti: Servizi di dominio Active Directory, Azure Active Directory o amministratore locale.</span><span class="sxs-lookup"><span data-stu-id="b196e-131">In the **Setup admins for this device** window, select one of the following options: Active Directory Domain Services, Azure Active Directory, or Local admin.</span></span>

   ![\* Amministratori configurazione per questo dispositivo \*](images/sh2-run5.png) <br>

### <span data-ttu-id="b196e-133">Active Directory Domain Services</span><span class="sxs-lookup"><span data-stu-id="b196e-133">Active Directory Domain Services</span></span>

1. <span data-ttu-id="b196e-134">Immettere le credenziali di un utente che dispone delle autorizzazioni necessarie per accedere al dispositivo ad Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b196e-134">Enter the credentials of a user who has permissions to join the device to Active Directory.</span></span>

    ![\* Amministratori configurazione con Domain Join \*](images/sh2-run6.png) <br>

2. <span data-ttu-id="b196e-136">Selezionare il gruppo di sicurezza di Active Directory contenente i membri autorizzati ad accedere all'app impostazioni in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="b196e-136">Select the Active Directory Security Group containing members allowed to log on to the Settings app on Surface Hub 2S.</span></span>

    ![\* Immettere un gruppo di sicurezza \*](images/sh2-run7.png) <br>
1. <span data-ttu-id="b196e-138">Selezionare **fine**.</span><span class="sxs-lookup"><span data-stu-id="b196e-138">Select **Finish**.</span></span> <span data-ttu-id="b196e-139">Il dispositivo verrà riavviato.</span><span class="sxs-lookup"><span data-stu-id="b196e-139">The device will restart.</span></span>

### <span data-ttu-id="b196e-140">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="b196e-140">Azure Active Directory</span></span>

<span data-ttu-id="b196e-141">Quando si sceglie di affiliare il dispositivo con Azure Active Directory, il dispositivo verrà immediatamente riavviato e visualizzato nella pagina seguente.</span><span class="sxs-lookup"><span data-stu-id="b196e-141">When choosing to affiliate your device with Azure Active Directory, the device will immediately restart and display the following page.</span></span> <span data-ttu-id="b196e-142">Seleziona **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="b196e-142">Select **Next**.</span></span>

![\* Se l'organizzazione usa Office 365 o altri servizi commerciali da Microsoft, questo dispositivo verrà registrato con l'organizzazione \*](images/sh2-run8.png) <br>

1. <span data-ttu-id="b196e-144">Immettere l'indirizzo di posta elettronica o l'UPN di un account **con Intune piano 1** o superiore e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="b196e-144">Enter the email address or UPN of an account **with Intune Plan 1** or greater and then select **Next.**</span></span>

    ![\* Immettere l'account di lavoro o dell'Istituto di istruzione \*](images/sh2-run9.png) <br>

2. <span data-ttu-id="b196e-146">Se viene reindirizzato, eseguire l'autenticazione usando la pagina di accesso dell'organizzazione e specificare altre informazioni di accesso, se richiesto.</span><span class="sxs-lookup"><span data-stu-id="b196e-146">If redirected, authenticate using your organization’s sign-in page and provide additional logon information if requested.</span></span> <span data-ttu-id="b196e-147">Il dispositivo verrà riavviato.</span><span class="sxs-lookup"><span data-stu-id="b196e-147">The device will restart.</span></span>

## <span data-ttu-id="b196e-148">Account di amministratore locale</span><span class="sxs-lookup"><span data-stu-id="b196e-148">Local Administrator account</span></span>

- <span data-ttu-id="b196e-149">Immettere un nome utente e una password per l'amministratore locale. Il dispositivo verrà riavviato.</span><span class="sxs-lookup"><span data-stu-id="b196e-149">Enter a username and password for your local admin. The device will restart.</span></span>

     ![\* Configurare un account di amministratore \*](images/sh2-run10.png) <br>
 
## <span data-ttu-id="b196e-151">Uso di pacchetti di provisioning</span><span class="sxs-lookup"><span data-stu-id="b196e-151">Using provisioning packages</span></span>

<span data-ttu-id="b196e-152">Se si inserisce un'unità thumb USB con un pacchetto di provisioning in una delle porte USB quando si avvia Surface Hub 2S, il dispositivo Visualizza la pagina seguente.</span><span class="sxs-lookup"><span data-stu-id="b196e-152">If you insert a USB thumb drive with a provisioning package into one of the USB ports when you start Surface Hub 2S, the device displays the following page.</span></span>

1. <span data-ttu-id="b196e-153">Immettere le impostazioni richieste e selezionare **Configura**.</span><span class="sxs-lookup"><span data-stu-id="b196e-153">Enter the requested settings and select **Set up**.</span></span>

    ![\* Immettere le impostazioni internazionali per il pacchetto di provisioning \*](images/sh2-run11.png) <br>

    ![\* Eseguire il provisioning del dispositivo da un supporto rimovibile \*](images/sh2-run12.png) <br>
2. <span data-ttu-id="b196e-156">Scegliere il pacchetto di provisioning che si vuole usare.</span><span class="sxs-lookup"><span data-stu-id="b196e-156">Choose the provisioning package you’d like to use.</span></span>

   ![\* Scegliere il pacchetto di provisioning da usare \*](images/sh2-run13.png) <br>

3. <span data-ttu-id="b196e-158">Se è stato creato un file CSV con più dispositivi, sarà possibile scegliere una configurazione del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="b196e-158">If you created a multiple devices CSV file, you will be able to choose a device configuration.</span></span> <span data-ttu-id="b196e-159">Per altre informazioni, vedere [creare pacchetti di provisioning per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file).</span><span class="sxs-lookup"><span data-stu-id="b196e-159">For more information, refer to [Create provisioning packages for Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file).</span></span>


    ![\* Selezionare un account di dispositivo e un nome descrittivo dal file di configurazione \*](images/sh2-run14.png) <br>

4. <span data-ttu-id="b196e-161">Seguire le istruzioni per completare la configurazione per la prima volta.</span><span class="sxs-lookup"><span data-stu-id="b196e-161">Follow the instructions to complete first time Setup.</span></span>

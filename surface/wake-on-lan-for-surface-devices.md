---
title: Riattivazione LAN per i dispositivi Surface
description: Scopri come puoi usare riattivazione LAN per riattivare in remoto i dispositivi per eseguire automaticamente le attività di gestione.
keywords: aggiornare, distribuire, driver, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
ms.date: 3/19/2021
ms.openlocfilehash: 9c3302616de97cf60b7d750948fed653456a7cba
ms.sourcegitcommit: 6c362c5d5f67449f1adf4618847093eaf6ad087b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2021
ms.locfileid: "11442890"
---
# <a name="wake-on-lan-for-surface-devices"></a><span data-ttu-id="1d58d-104">Riattivazione LAN per i dispositivi Surface</span><span class="sxs-lookup"><span data-stu-id="1d58d-104">Wake On LAN for Surface devices</span></span>

<span data-ttu-id="1d58d-105">I dispositivi Surface che usano una scheda Surface Ethernet per connettersi a una rete cablata possono sfruttare riattivazione LAN (WOL) da Connected Standby.</span><span class="sxs-lookup"><span data-stu-id="1d58d-105">Surface devices that use a Surface Ethernet adapter to connect to a wired network can take advantage of Wake On LAN (WOL) from Connected Standby.</span></span> <span data-ttu-id="1d58d-106">Con WOL, puoi riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione usando soluzioni di gestione come Microsoft Endpoint Manager/Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="1d58d-106">With WOL, you can remotely wake up devices and automatically perform management tasks using management solutions such as Microsoft Endpoint Manager/Microsoft Intune.</span></span>

## <a name="wol-supported-devices"></a><span data-ttu-id="1d58d-107">Dispositivi supportati da WOL</span><span class="sxs-lookup"><span data-stu-id="1d58d-107">WOL-supported devices</span></span>

- <span data-ttu-id="1d58d-108">Scheda Surface Ethernet</span><span class="sxs-lookup"><span data-stu-id="1d58d-108">Surface Ethernet adapter</span></span>
- <span data-ttu-id="1d58d-109">Surface USB-C to Ethernet and USB Adapter</span><span class="sxs-lookup"><span data-stu-id="1d58d-109">Surface USB-C to Ethernet and USB Adapter</span></span>
- <span data-ttu-id="1d58d-110">Surface Dock 2</span><span class="sxs-lookup"><span data-stu-id="1d58d-110">Surface Dock 2</span></span>
- <span data-ttu-id="1d58d-111">Surface Pro 6 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="1d58d-111">Surface Pro 6 and later</span></span>
- <span data-ttu-id="1d58d-112">Surface Book (tutte le generazioni)</span><span class="sxs-lookup"><span data-stu-id="1d58d-112">Surface Book (all generations)</span></span>
- <span data-ttu-id="1d58d-113">Surface Laptop (tutte le generazioni)</span><span class="sxs-lookup"><span data-stu-id="1d58d-113">Surface Laptop (all generations)</span></span>
- <span data-ttu-id="1d58d-114">Surface Go (tutte le generazioni)</span><span class="sxs-lookup"><span data-stu-id="1d58d-114">Surface Go (all generations)</span></span>
- <span data-ttu-id="1d58d-115">Surface Studio 2 (vedi Appendice)</span><span class="sxs-lookup"><span data-stu-id="1d58d-115">Surface Studio 2 (see Appendix)</span></span>


## <a name="using-surface-wol"></a><span data-ttu-id="1d58d-116">Uso di Surface WOL</span><span class="sxs-lookup"><span data-stu-id="1d58d-116">Using Surface WOL</span></span>

<span data-ttu-id="1d58d-117">Gli amministratori IT possono attivare i dispositivi usando una richiesta wake on LAN (pacchetto magico) contenente l'indirizzo MAC del computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="1d58d-117">IT admins can trigger devices using a wake on LAN request (magic packet) that contains the target computer’s MAC address.</span></span> <span data-ttu-id="1d58d-118">Per inviare un pacchetto magico e riattivare un dispositivo utilizzando WOL, devi conoscere l'indirizzo MAC del dispositivo di destinazione e della scheda Ethernet.</span><span class="sxs-lookup"><span data-stu-id="1d58d-118">To send a magic packet and wake up a device by using WOL, you must know the MAC address of the target device and Ethernet adapter.</span></span> <span data-ttu-id="1d58d-119">Poiché il pacchetto magico non utilizza il protocollo di rete IP, non è possibile utilizzare l'indirizzo IP o il nome DNS del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="1d58d-119">Because the magic packet does not use the IP network protocol, it is not possible to use the IP address or DNS name of the device.</span></span>

<span data-ttu-id="1d58d-120">Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e le app di Microsoft Store di terze parti, offrono supporto incorporato per WOL.</span><span class="sxs-lookup"><span data-stu-id="1d58d-120">Many management solutions, such as Microsoft Endpoint Configuration Manager and third party Microsoft Store apps provide built-in support for WOL.</span></span> <span data-ttu-id="1d58d-121">Tieni presente che i dispositivi devono essere in modalità Standby connesso (sospensione) e connessi all'alimentazione CA.</span><span class="sxs-lookup"><span data-stu-id="1d58d-121">Note that devices need to be in Connected Standby (Sleep) mode and connected to AC power.</span></span> <span data-ttu-id="1d58d-122">Per ulteriori informazioni sui dispositivi di attivazione con Endpoint Configuration Manager, vedere [Configure Wake on LAN - Configuration Manager.](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan)</span><span class="sxs-lookup"><span data-stu-id="1d58d-122">To learn more about waking devices with Endpoint Configuration Manager, see [Configure Wake on LAN - Configuration Manager](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan).</span></span>


### <a name="to-check-wol-is-enabled-on-your-device"></a><span data-ttu-id="1d58d-123">Per verificare che WOL sia abilitato nel dispositivo</span><span class="sxs-lookup"><span data-stu-id="1d58d-123">To check WOL is enabled on your device</span></span>

1. <span data-ttu-id="1d58d-124">Nel dispositivo connesso Ethernet selezionare la scheda di rete e quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="1d58d-124">On your Ethernet connected device, select your network adapter, and then select **Properties**.</span></span>

   > [!div class="mx-imgBorder"]
   > ![Scheda Surface Ethernet](images/surface-ethernet.png)

2. <span data-ttu-id="1d58d-126">Selezionare **Configura**  >  **avanzate**.</span><span class="sxs-lookup"><span data-stu-id="1d58d-126">Select **Configure** > **Advanced**.</span></span>
3. <span data-ttu-id="1d58d-127">Scorri fino **a Modern Standby WoL Magic Packet** e assicurati che **l'opzione Enabled** sia selezionata.</span><span class="sxs-lookup"><span data-stu-id="1d58d-127">Scroll to **Modern Standby WoL Magic Packet** and ensure **Enabled** is selected.</span></span>

     ![Verificare che IL SERVIZIO SIA abilitato nel dispositivo](images/ethernet-wol-setting.png)

## <a name="appendix-surface-studio-2"></a><span data-ttu-id="1d58d-129">Appendice: Surface Studio 2</span><span class="sxs-lookup"><span data-stu-id="1d58d-129">Appendix: Surface Studio 2</span></span>

<span data-ttu-id="1d58d-130">Per abilitare WOL in Surface Studio 2, usa la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="1d58d-130">To enable WOL on Surface Studio 2, use the following procedure.</span></span>

1. <span data-ttu-id="1d58d-131">Creare le seguenti chiavi del Registro di sistema:</span><span class="sxs-lookup"><span data-stu-id="1d58d-131">Create the following registry keys:</span></span>

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. <span data-ttu-id="1d58d-132">Eseguire il comando seguente</span><span class="sxs-lookup"><span data-stu-id="1d58d-132">Run the following command</span></span>

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```


## <a name="learn-more"></a><span data-ttu-id="1d58d-133">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="1d58d-133">Learn more</span></span>

- [<span data-ttu-id="1d58d-134">Da MICROSOFT Surface USB-C a Ethernet e adattatore USB</span><span class="sxs-lookup"><span data-stu-id="1d58d-134">Microsoft Surface USB-C to Ethernet and USB Adapter</span></span>](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)

- [<span data-ttu-id="1d58d-135">Scheda Ethernet Surface USB 3.0 Gigabit</span><span class="sxs-lookup"><span data-stu-id="1d58d-135">Surface USB 3.0 Gigabit Ethernet Adapter</span></span>](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)

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
# <a name="wake-on-lan-for-surface-devices"></a>Riattivazione LAN per i dispositivi Surface

I dispositivi Surface che usano una scheda Surface Ethernet per connettersi a una rete cablata possono sfruttare riattivazione LAN (WOL) da Connected Standby. Con WOL, puoi riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione usando soluzioni di gestione come Microsoft Endpoint Manager/Microsoft Intune.

## <a name="wol-supported-devices"></a>Dispositivi supportati da WOL

- Scheda Surface Ethernet
- Surface USB-C to Ethernet and USB Adapter
- Surface Dock 2
- Surface Pro 6 e versioni successive
- Surface Book (tutte le generazioni)
- Surface Laptop (tutte le generazioni)
- Surface Go (tutte le generazioni)
- Surface Studio 2 (vedi Appendice)


## <a name="using-surface-wol"></a>Uso di Surface WOL

Gli amministratori IT possono attivare i dispositivi usando una richiesta wake on LAN (pacchetto magico) contenente l'indirizzo MAC del computer di destinazione. Per inviare un pacchetto magico e riattivare un dispositivo utilizzando WOL, devi conoscere l'indirizzo MAC del dispositivo di destinazione e della scheda Ethernet. Poiché il pacchetto magico non utilizza il protocollo di rete IP, non è possibile utilizzare l'indirizzo IP o il nome DNS del dispositivo.

Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e le app di Microsoft Store di terze parti, offrono supporto incorporato per WOL. Tieni presente che i dispositivi devono essere in modalità Standby connesso (sospensione) e connessi all'alimentazione CA. Per ulteriori informazioni sui dispositivi di attivazione con Endpoint Configuration Manager, vedere [Configure Wake on LAN - Configuration Manager.](https://docs.microsoft.com/mem/configmgr/core/clients/deploy/configure-wake-on-lan)


### <a name="to-check-wol-is-enabled-on-your-device"></a>Per verificare che WOL sia abilitato nel dispositivo

1. Nel dispositivo connesso Ethernet selezionare la scheda di rete e quindi scegliere **Proprietà**.

   > [!div class="mx-imgBorder"]
   > ![Scheda Surface Ethernet](images/surface-ethernet.png)

2. Selezionare **Configura**  >  **avanzate**.
3. Scorri fino **a Modern Standby WoL Magic Packet** e assicurati che **l'opzione Enabled** sia selezionata.

     ![Verificare che IL SERVIZIO SIA abilitato nel dispositivo](images/ethernet-wol-setting.png)

## <a name="appendix-surface-studio-2"></a>Appendice: Surface Studio 2

Per abilitare WOL in Surface Studio 2, usa la procedura seguente.

1. Creare le seguenti chiavi del Registro di sistema:

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0 and AllowSystemRequiredPowerRequests to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   "AllowSystemRequiredPowerRequests"=dword:00000001
   ```

2. Eseguire il comando seguente

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```


## <a name="learn-more"></a>Altre informazioni

- [Da MICROSOFT Surface USB-C a Ethernet e adattatore USB](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)

- [Scheda Ethernet Surface USB 3.0 Gigabit](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)

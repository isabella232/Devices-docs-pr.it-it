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
ms.date: 6/04/2021
ms.openlocfilehash: 83989461ca557d27740252149418056688774d3f
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613801"
---
# <a name="wake-on-lan-for-surface-devices"></a>Riattivazione LAN per i dispositivi Surface

Per mantenere i dispositivi completamente aggiornati, gli amministratori IT devono essere in grado di gestire i dispositivi quando non sono in uso, in genere durante le finestre di manutenzione notturne. Wake on LAN (WOL) consente agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione con Microsoft Endpoint Manager o soluzioni di terze parti.

## <a name="requirements"></a>Requisiti

I dispositivi devono essere connessi all'alimentazione CA e disporre di una connessione cablata con una delle seguenti schede Ethernet compatibili:

- Scheda Ethernet Surface USB 3.0 Gigabit
- Scheda Surface Ethernet
- Surface USB-C to Ethernet and USB Adapter
- Hub adattatore da viaggio USB-C Microsoft
- Dock Surface
- Surface Dock 2

> [!NOTE]
> Surface Dock 2 offre il miglior supporto per Wake on LAN senza la necessità di ulteriori configurazioni IT. Per altre informazioni, vedi [Wake on LAN per Surface Dock 2](wake-on-lan-surface-dock2.md)

## <a name="how-it-works"></a>Come funziona

Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso. Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione. Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e app Microsoft Store di terze parti, forniscono il supporto incorporato per WOL. Per ulteriori informazioni sui dispositivi di attivazione con Endpoint Configuration Manager, vedere [Configure Wake on LAN - Configuration Manager.](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)

Il supporto per Wake on LAN varia a seconda dello stato di sospensione: Standby connesso o Ibernazione (stato di alimentazione S4).

## <a name="connected-standby"></a>Standby connesso

Per impostazione predefinita, Windows 10 supporta Wake on LAN per i dispositivi Surface in Standby connesso.

### <a name="supported-surface-devices---connected-standby"></a>Dispositivi Surface supportati - Standby connesso

- Surface Laptop 4 (solo processori Intel)
- Surface Laptop 3 (solo processori Intel)
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Go 2
- Surface Laptop Go
- Surface Book 3

## <a name="hibernation"></a>Ibernazione

Per riattivare i dispositivi dall'ibernazione è necessario abilitare un'impostazione dei criteri UEFI tramite la modalità di gestione di [Surface Enterprise](surface-enterprise-management-mode.md) (SEMM) (non necessaria per i dispositivi connessi a Surface Dock 2).

### <a name="supported-surface-devices---hibernation"></a>Dispositivi Surface supportati - Ibernazione

- Surface Laptop 4 (solo processori Intel)
- Surface Laptop 3 (solo processori Intel)
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop Go
- Surface Book 3

### <a name="to-enable-wake-on-lan-uefi-setting"></a>Per abilitare l'impostazione UEFI Wake on LAN

Per abilitare l'impostazione UEFI Wake on LAN, devi registrare i dispositivi di destinazione in SEMM, creare un pacchetto di configurazione e applicare il pacchetto ai dispositivi. Per ulteriori informazioni, fai riferimento a:

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)
- [Registrare e configurare i dispositivi Surface con SEMM](enroll-and-configure-surface-devices-with-semm.md)

1. Scaricare e installare [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).
2. Selezionare **Start**  >  **Configuration Package**  >  **Create**+ Certificate  > **Protection**.
3. Passare a **Impostazioni avanzate e** impostare Wake on **LAN** su **On.**
4. Applica il pacchetto ai dispositivi di destinazione.

    > [!div class="mx-imgBorder"]
    > ![Abilita l'impostazione dei criteri UEFI wake on LAN](images/wol-uefi.png)

## <a name="learn-more"></a>Altre informazioni

- [Wake on LAN per Surface Dock 2](wake-on-lan-surface-dock2.md)
- [Da MICROSOFT Surface USB-C a Ethernet e adattatore USB](https://www.microsoft.com/p/surface-usb-c-to-ethernet-and-usb-adapter/8wt81cglrblp?)
- [Scheda Ethernet Surface USB 3.0 Gigabit](https://www.microsoft.com/p/surface-usb-30-gigabit-ethernet-adapter/8xn9fqvzbvq0?)

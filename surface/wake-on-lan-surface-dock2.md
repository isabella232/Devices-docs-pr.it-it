---
title: riattivazione LAN con Surface Dock 2
description: Surface Dock 2 offre il supporto migliore per Wake on LAN (WOL) che consente agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente le attività di gestione.
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
ms.date: 6/03/2021
ms.openlocfilehash: 74b36b60cb58ecb9042b73b8cdba7271d0af8c80
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614095"
---
# <a name="wake-on-lan-with-surface-dock-2"></a>riattivazione LAN con Surface Dock 2

Per mantenere i dispositivi completamente aggiornati, gli amministratori IT devono essere in grado di gestire i dispositivi quando non sono in uso, in genere durante le finestre di manutenzione notturne. Surface Dock 2 offre il supporto migliore per Wake on LAN (WOL) consentendo agli amministratori di riattivare in remoto i dispositivi ed eseguire automaticamente attività di gestione con Microsoft Endpoint Manager o altre soluzioni di terze parti.

## <a name="requirements"></a>Requisiti

I dispositivi devono avere una connessione cablata con Surface Dock 2 e rimanere connessi all'alimentazione CA.

> [!div class="mx-imgBorder"]
> ![Surface Dock 2](images/surface-dock2-angled.png)

## <a name="supported-surface-devices"></a>Dispositivi Surface supportati

- Surface Laptop 4 (processori Intel)
- Surface Laptop 4 (processori AMD)
- Surface Laptop 3 (processori Intel)
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Go 2
- Surface Laptop Go
- Surface Book 3

Surface Dock 2 fornisce il supporto WOL per i dispositivi nei seguenti stati di alimentazione:

- Standby connesso
- Ibernazione (stato di alimentazione S4)
- Ibernazione (stato di alimentazione "soft off" S5)

Per ulteriori informazioni sugli stati di alimentazione, vedere [Stati di alimentazione del sistema](/windows/win32/power/system-power-states).

## <a name="how-it-works"></a>Come funziona

Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso. Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione. Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e app Microsoft Store di terze parti, forniscono il supporto incorporato per WOL.

Per abilitare WOL nei dispositivi senza Surface Dock 2, vedi [Wake on LAN for Surface devices.](wake-on-lan-for-surface-devices.md)

## <a name="learn-more"></a>Altre informazioni

- [Surface Dock 2](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [Riattivazione LAN per i dispositivi Surface](wake-on-lan-for-surface-devices.md)
- [Stati di alimentazione del sistema](/windows/win32/power/system-power-states)
- [Configurare Wake on LAN - Configuration Manager](/mem/configmgr/core/clients/deploy/configure-wake-on-lan)

---
title: Riattivazione LAN con Surface Dock 2
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
ms.date: 7/30/2021
ms.openlocfilehash: 84a87342891dac2e4c0b0490458941c82fa0d018
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911611"
---
# <a name="wake-on-lan-with-surface-dock-2"></a>Riattivazione LAN con Surface Dock 2

Per mantenere i dispositivi completamente aggiornati, gli amministratori IT devono essere in grado di gestire i dispositivi quando non sono in uso, in genere durante le finestre di manutenzione notturne. Surface Dock 2 offre il supporto migliore per Wake on LAN (WOL) consentendo agli amministratori di riattivare in remoto i dispositivi Surface ed eseguire automaticamente le attività di gestione con Microsoft Endpoint Manager o altre soluzioni di terze parti.

## <a name="requirements"></a>Requisiti

I dispositivi devono avere una connessione cablata con Surface Dock 2 e rimanere connessi all'alimentazione CA.

> [!div class="mx-imgBorder"]
> ![Surface Dock 2.](images/surface-dock2-angled.png)

> [!NOTE]
> I dispositivi waking connessi a Surface Dock 2 non richiedono l'uso della modalità di gestione di Surface Enterprise (SEMM) o l'abilitazione di impostazioni dei criteri UEFI.
 
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
- Spegnimento (stato di alimentazione "soft off" S5)

Per ulteriori informazioni sugli stati di alimentazione, vedere [Stati di alimentazione del sistema](/windows/win32/power/system-power-states).

## <a name="how-it-works"></a>Come funziona

Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso. Oppure i dispositivi potrebbero essere in stato di ibernazione (S4) o arresto (S5) in base alle impostazioni di alimentazione configurate nel dispositivo. Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione. Molte soluzioni di gestione, ad esempio Microsoft Endpoint Configuration Manager e app Microsoft Store di terze parti, offrono supporto incorporato per WOL.

Per abilitare WOL nei dispositivi senza Surface Dock 2, vedi:

- [Wake on LAN per dispositivi Surface](wake-on-lan-for-surface-devices.md)

## <a name="learn-more"></a>Scopri di più

- [Surface Dock 2](https://www.microsoft.com/p/surface-dock-2-for-business/8q4hgc6kbmdq?)
- [Riattivazione LAN per i dispositivi Surface](wake-on-lan-for-surface-devices.md)
- [Stati di alimentazione del sistema](/windows/win32/power/system-power-states)


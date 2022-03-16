---
title: Riattivazione LAN per i dispositivi Surface
description: I dispositivi Surface che eseguono Windows 10 versione 1607 o successiva e usano una scheda Surface Ethernet per connettersi a una rete cablata sono in grado di riattivazione LAN (WOL) da Modern Standby.
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
ms.date: 11/30/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: f0d2215fae1ce8aa5cdc6d55fb36158d6a95af4d
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448284"
---
# <a name="wake-on-lan-for-surface-devices"></a>Riattivazione LAN per i dispositivi Surface 

I dispositivi Surface che eseguono Windows 10 versione 1607 o successiva sono in grado di riattivazione LAN (WOL) da Modern Standby (noto anche come Standby connesso). Con WOL, gli amministratori IT possono riattivare in remoto i dispositivi ed eseguire automaticamente le attività di gestione con Microsoft Endpoint Manager o soluzioni di terze parti.

>[!NOTE]
>Per supportare WOL, i dispositivi Surface devono essere collegati all'alimentazione CA e usare una scheda Surface Ethernet connessa a una rete cablata.

## <a name="supported-devices"></a>Dispositivi supportati

Schede Ethernet con supporto per WOL:

- Microsoft USB-C Travel Hub
- Scheda Surface Ethernet
- Surface USB-C to Ethernet and USB 3.0 Adapter
- Scheda Ethernet Surface USB 3.0 Gigabit 
- Surface DockDocking Station per Surface Pro 3 
- Surface Dock 2
- Docking Station per Surface 3
- Docking Station per Surface Pro 3 

Dispositivi Surface con supporto per WOL:

- Surface 3
- Surface Pro 3
- Surface Pro 4
- Surface Pro (5° generazione)
- Surface Pro (5° generazione) con LTE Advanced
- Surface Pro 6
- Surface Pro 7
- Surface Pro 7+
- Surface Pro 8
- Surface Book (tutte le generazioni)
- Surface Go (tutte le generazioni)
- Surface Laptop (tutte le generazioni)
- Surface Laptop Go
- Surface Laptop edizione Standard
- Surface Laptop Studio
- Surface Studio 2 (vedere Surface Studio 2 istruzioni seguenti)


## <a name="using-wol"></a>Utilizzo di WOL 

Quando non sono in uso, i dispositivi Surface entrano in uno stato inattivo e a basso consumo noto come Standby moderno o Standby connesso. Gli amministratori IT possono attivare in remoto i dispositivi usando una richiesta di riattivazione (pacchetto magico) che contiene l'indirizzo MAC (Media Access Control) del dispositivo Surface di destinazione. La scheda di interfaccia di rete di destinazione confronta l'indirizzo MAC con il proprio prima di svegliare il dispositivo. Se l'indirizzo MAC nella richiesta di riattivazione del pacchetto magico non corrisponde all'indirizzo MAC nella scheda NIC di destinazione, la nic non riattiva il dispositivo. Per ulteriori informazioni, consultare la [documentazione relativa alle origini di riattivazione](/windows-hardware/design/device-experiences/modern-standby-wake-sources)

## <a name="modern-standby"></a>Standby moderno

Lo standby moderno viene avviato quando l'utente fa entrare il sistema in stato di sospensione o il dispositivo passa alla modalità di sospensione in base alle impostazioni Windows di alimentazione impostate dall'utente. Ad esempio, l'utente preme il pulsante di alimentazione, chiude il coperchio o seleziona Sospensione dal pulsante di alimentazione nella Windows menu Start. WOL funziona per impostazione predefinita per i dispositivi Surface in modalità Standby moderno Windows 10 versione 1607 o successiva. Non è necessaria alcuna configurazione IT aggiuntiva, ad eccezione di Surface Studio 2.

## <a name="surface-studio-2-instructions"></a>Surface Studio 2 istruzioni

Per abilitare WOL in Surface Studio 2, è necessario eseguire la procedura seguente

1. Aprire l'editor del Registro di** sistema **(**StartSearch** > **** > regedit.exe) e creare le seguenti chiavi del Registro di sistema:

   ```console
   ; Set CONNECTIVITYINSTANDBY to 1:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings\F15576E8-98B7-4186-B944-EAFA664402D9]
   "Attributes"=dword:00000001
   ; Set EnforceDisconnectedStandby to 0:
   [HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power]
   "EnforceDisconnectedStandby"=dword:00000000
   ```

2. Eseguire il comando seguente

    ```powercfg /SETACVALUEINDEX SCHEME_BALANCED SUB_NONE CONNECTIVITYINSTANDBY 1```

> [!NOTE]
> Se si aggiorna la versione di Windows 10 sul Surface Studio 2 (ad esempio, si esegue l'aggiornamento da Windows 10 20H2 a 21H1), sarà necessario seguire di nuovo queste istruzioni per abilitare WOL.


### <a name="to-wake-from-hibernation-s4-or-shutdown-s5"></a>Per riattivare l'ibernazione (S4) o l'arresto (S5) 

- Per i dispositivi connessi a Surface Dock 2, vedi [Wake on LAN per Surface Dock 2](wake-on-lan-surface-dock2.md)

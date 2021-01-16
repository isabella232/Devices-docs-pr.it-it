---
title: Wake on LAN per Surface Devices (Surface)
description: Informazioni su come usare Wake on LAN per riattivare i dispositivi in remoto per eseguire attività di gestione o manutenzione oppure per abilitare automaticamente le soluzioni di gestione, anche se i dispositivi sono spenti.
keywords: aggiornamento, distribuzione, driver, WOL, Wake-on-LAN
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 709286cc0d62bd0b4c1e28e7626529fc4a215ae2
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271123"
---
# Riattivazione LAN per i dispositivi Surface

I dispositivi Surface che eseguono Windows 10, versione 1607 (nota anche come aggiornamento per l'anniversario di Windows 10) o versioni successive e usano una scheda Ethernet Surface per connettersi a una rete cablata, sono in grado di riattivare la LAN (WOL) dalla modalità standby connessa. Con WOL, è possibile riattivare i dispositivi in remoto per eseguire attività di gestione o manutenzione o abilitare automaticamente le soluzioni di gestione, ad esempio Microsoft endpoint Configuration Manager. Ad esempio, è possibile distribuire le applicazioni ai dispositivi Surface lasciati ancorati con una docking Surface dock o Surface Pro 3, usando Microsoft endpoint Configuration Manager durante una finestra nel bel mezzo della notte, quando l'ufficio è vuoto.

>[!NOTE]
>I dispositivi Surface devono essere connessi all'alimentazione CA e in standby connesso (Sleep) per supportare WOL. Il WOL non è possibile dai dispositivi in ibernazione o spenti.

## Dispositivi supportati

I dispositivi seguenti sono supportati per WOL:

* Scheda Ethernet di Surface
* Surface USB-C per Ethernet e adattatore USB
* Dock Surface
* Docking station per Surface Pro 3
* Surface 3
* Surface Pro 3
* Surface Pro 4
* Surface Pro (5a generazione)
* Surface Pro (5a generazione) con LTE Advanced
* Surface Book
* Laptop Surface (1a generazione)
* Surface Pro 6
* Surface Book 2
* Surface Laptop 2
* Surface Go
* Surface Go con LTE Advanced
* Surface Studio 2 (vedere le istruzioni di Surface Studio 2)
* Surface Pro 7
* Laptop Surface 3
* Portatile Surface go
* Surface Pro 7 +

## Driver WOL

Per abilitare il supporto WOL su dispositivi Surface, è necessario un driver specifico per la scheda Ethernet Surface. Questo driver non è incluso nel driver standard e nel pacchetto firmware per i dispositivi Surface: è necessario scaricarlo e installarlo separatamente. È possibile scaricare il driver Surface WOL (SurfaceWOL.msi) dalla pagina [strumenti superficie per l'it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.

Puoi eseguire questo file di Microsoft Windows Installer (con estensione msi) su un dispositivo Surface per installare il driver Surface WOL oppure distribuirlo ai dispositivi Surface con una soluzione di distribuzione dell'applicazione, ad esempio Microsoft endpoint Configuration Manager. Per includere il driver Surface WOL durante la distribuzione, è possibile installare il file con estensione msi come applicazione durante il processo di distribuzione. È anche possibile estrarre i file del driver di Surface WOL per includerli nel processo di distribuzione. Ad esempio, è possibile includerli nella condivisione di distribuzione di Microsoft Deployment Toolkit (MDT). Per altre informazioni sulla distribuzione di Surface con MDT, vedere [distribuire Windows 10 ai dispositivi Surface con Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/deploy-windows-10-to-surface-devices-with-mdt).

> [!NOTE]
> Durante l'installazione di SurfaceWOL.msi, la chiave del registro di sistema seguente viene impostata su un valore pari a 1, che consente di identificare facilmente i sistemi in cui è stato installato il driver WOL. Se si è scelto di estrarre e installare questi driver separatamente durante la distribuzione, questa chiave del registro di sistema non verrà configurata e deve essere configurata manualmente o con uno script.
> 
> **HKLM\SYSTEM\CurrentControlSet\Control\Power AllowSystemRequiredPowerRequests** 

Per estrarre il contenuto di SurfaceWOL.msi, usare l'opzione di installazione amministrativa MSIExec (**/a**), come illustrato nell'esempio seguente, per estrarre il contenuto nella cartella C:\WOL\:

   `msiexec /a surfacewol.msi targetdir=C:\WOL /qn`

## Istruzioni di Surface Studio 2

Per abilitare WOL in Surface Studio 2, è necessario usare la procedura seguente

1. Creare le chiavi del registro di sistema seguenti:

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

## Uso di Surface WOL

Il driver Surface WOL è conforme allo standard WOL, in cui il dispositivo viene svegliato da una comunicazione di rete speciale nota come pacchetto magico. Il pacchetto magico è costituito da 6 byte di 255 (o FF in esadecimale) seguiti da 16 ripetizioni dell'indirizzo MAC del computer di destinazione. Per altre informazioni, vedere il pacchetto Magic e lo standard WOL su [Wikipedia](https://wikipedia.org/wiki/Wake-on-LAN#Magic_packet).

>[!NOTE]
>Per inviare un pacchetto magico e riattivare un dispositivo tramite WOL, è necessario conoscere l'indirizzo MAC del dispositivo di destinazione e della scheda Ethernet. Poiché il pacchetto magico non usa il protocollo di rete IP, non è possibile usare l'indirizzo IP o il nome DNS del dispositivo.

Molte soluzioni di gestione, ad esempio Configuration Manager, includono il supporto predefinito per WOL. Sono disponibili anche molte soluzioni, tra cui le app Microsoft Store, i moduli di PowerShell, le applicazioni di terze parti e le soluzioni di gestione di terze parti che consentono di inviare un pacchetto magico per riattivare un dispositivo. Ad esempio, puoi usare il [modulo di PowerShell Wake on LAN](https://gallery.technet.microsoft.com/scriptcenter/Wake-On-Lan-815424c4) da TechNet Script Center. 

>[!NOTE]
>Dopo che un dispositivo è stato riattivato con un pacchetto magico, il dispositivo tornerà in stato di sospensione se un'applicazione non impedisce attivamente il blocco del sistema o se la chiave del registro di AllowSystemRequiredPowerRequests non è configurata su 1, che consente alle applicazioni di impedire il blocco del sonno. Per altre informazioni su questa chiave del registro di sistema, vedere la sezione [driver WOL](#wol-driver) di questo articolo.

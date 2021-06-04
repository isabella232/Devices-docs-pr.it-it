---
title: Impostazione limite batteria (superficie)
description: Il limite di batteria è un'impostazione UEFI che cambia il modo in cui viene caricata la batteria del dispositivo Surface e può prolungarne la longevità.
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.reviewer: jesko
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
manager: laurawi
audience: itpro
ms.date: 1/15/2021
ms.openlocfilehash: 8ce1dcfc621a547aca9ca1db322f3ed2ce082728
ms.sourcegitcommit: 1b86286bd13b13749ddbf454ae78d9a24fec44ee
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/15/2021
ms.locfileid: "11271143"
---
# Impostazione del limite della batteria

L'opzione limite batteria è un'impostazione UEFI che cambia il modo in cui viene caricata la batteria del dispositivo Surface e può prolungarne la longevità. Questa impostazione è consigliata nei casi in cui il dispositivo è continuamente connesso a Power, ad esempio quando i dispositivi sono integrati in soluzioni Kiosk.  

##  <a name="how-battery-limit-works"></a>Funzionamento del limite di batteria

L'impostazione del dispositivo sul limite della batteria cambia il protocollo per la ricarica della batteria del dispositivo. Quando il limite della batteria è abilitato, la carica della batteria sarà limitata al 50% della sua capacità massima. Il livello di carica segnalato in Windows rifletterà questo limite. Di conseguenza, mostrerà che la batteria viene caricata fino al 50% e non viene applicata oltre questo limite. Se si Abilita il limite della batteria mentre il dispositivo supera la carica di 50%, l'icona della batteria mostrerà che il dispositivo è collegato ma si Scarica finché il dispositivo non raggiunge il 50% della capacità massima di carica.  

##  <a name="supported-devices"></a>Dispositivi supportati

L'impostazione del limite di batteria UEFI è integrata negli ultimi dispositivi Surface, tra cui Surface Pro 7 +, Surface Pro 7 e Surface laptop 3. I dispositivi precedenti richiedono un [aggiornamento del firmware UEFI di Surface](manage-surface-driver-and-firmware-updates.md), disponibile tramite Windows Update o tramite il driver MSI e i pacchetti del firmware nel sito di [supporto Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface). Selezionare [Abilita "limite batteria" per i dispositivi Surface che devono essere collegati per periodi di tempo prolungati](https://support.microsoft.com/help/4464941) per la specifica versione UEFI di Surface necessaria per ogni dispositivo supportato. 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-4-and-later)"></a>Abilitazione del limite di batteria in UEFI di Surface (Surface Pro 4 e versioni successive)

L'impostazione del limite di batteria di Surface UEFI può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo). Scegliere **configurazione di avvio**e quindi, in **Opzioni avanzate**, attivare la **modalità limite batteria** **su**attivato.  

![Opzioni avanzate del limite di batteria](images/enable-bl.png) 

##  <a name="enabling-battery-limit-on-surface-go-and-surface-go-2"></a>Abilitazione del limite di batteria in Surface go e Surface Go 2
L'impostazione limite di superficie della batteria può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo). Scegliere **configurazione di avvio**e quindi, in **modalità Kiosk**, posizionare il dispositivo di scorrimento a destra per impostare il limite di batteria su **abilitato**.  

![Limite della batteria in modalità Kiosk in Surface go](images/go-batterylimit.png) 

##  <a name="enabling-battery-limit-in-surface-uefi-(surface-pro-3)"></a>Abilitazione del limite di batteria in UEFI di Surface (Surface Pro 3)

L'impostazione del limite di batteria di Surface UEFI può essere configurata eseguendo l'avvio in Surface UEFI (**Power + Vol Up** quando si attiva il dispositivo). Scegliere la **modalità Kiosk**, selezionare **limite batteria**e quindi scegliere **abilitato**.

![Screenshot delle opzioni avanzate](images/enable-bl-sp3.png) 

![Opzioni avanzate](images/enable-bl-sp3-2.png) 

##  <a name="enabling-battery-limit-using-surface-enterprise-management-mode-(semm)-or-surface-pro-3-firmware-powershell-scripts"></a>Abilitazione del limite della batteria con gli script di PowerShell per il firmware di Surface Enterprise Management (SEMM) o Surface Pro 3

Il limite di batteria di Surface UEFI è disponibile anche per la configurazione con i metodi seguenti:

- Surface Pro 4 e versioni successive 
    - [Microsoft Surface UEFI Configurator](https://docs.microsoft.com/surface/surface-enterprise-management-mode)  
    - Script di PowerShell di Surface UEFI Manager (SEMM_Powershell.zip) negli [strumenti Surface per i download](https://www.microsoft.com/download/details.aspx?id=46703)
- Surface Pro 3 
    - [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703)

###  <a name="using-microsoft-surface-uefi-configurator"></a>Uso di Microsoft Surface UEFI Configurator

Per configurare la modalità limite batteria, impostare l'impostazione **sostituzioni Kiosk** nella pagina configurazione **Impostazioni avanzate** in SEMM (Surface Pro 4 e versioni successive).

![Screenshot delle impostazioni avanzate](images/semm-bl.png)

###  <a name="using-surface-uefi-manager-powershell-scripts"></a>Usare gli script di PowerShell di Surface UEFI Manager

La caratteristica limite batteria viene controllata con l'impostazione seguente:  

`407 = Battery Profile`

**Descrizione**: schema di gestione attiva per il modello di utilizzo della batteria

**Impostazione predefinita**:  `0` 

Impostare questo valore su `1` per abilitare il limite di batteria.

###  <a name="using-surface-pro-3-firmware-tools"></a>Uso di strumenti firmware di Surface Pro 3

La caratteristica limite batteria viene controllata con l'impostazione seguente:  

**Nome**: BatteryLimitEnable

**Descrizione**: BatteryLimit

**Valore corrente**:  `0` 

**Valore predefinito**: `0`

**Valore proposto**: `0` 

Impostare questo valore su `1` per abilitare il limite di batteria.

>[!NOTE]
>Per configurare questa impostazione, è necessario usare [SP3_Firmware_Powershell_Scripts.zip](https://www.microsoft.com/download/details.aspx?id=46703). 


---
title: Impostazione Limite batteria (Surface)
description: Limite batteria è un'impostazione UEFI che modifica la modalità di carica della batteria del dispositivo Surface e può prolungarne la longevità.
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
ms.openlocfilehash: 9cf623a9a4b9d1a8d292cfa0cff25d2e57318db7
ms.sourcegitcommit: e7d95d583429169eb65aae9034eab2347b1f04a0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/02/2022
ms.locfileid: "12338329"
---
# <a name="battery-limit-setting"></a>Impostazione del limite della batteria

L'opzione Limite batteria è un'impostazione UEFI che modifica la modalità di carica della batteria del dispositivo Surface e può prolungarne la longevità. Questa impostazione è consigliata nei casi in cui il dispositivo è connesso continuamente all'alimentazione, ad esempio quando i dispositivi sono integrati nelle soluzioni chiosco multimediale.  

## <a name="how-battery-limit-works"></a>Funzionamento del limite di batteria

L'impostazione del dispositivo su Limite batteria modifica il protocollo per caricare la batteria del dispositivo. Quando il limite della batteria è abilitato, la carica della batteria sarà limitata al 50% della capacità massima. Il livello di addebito riportato in Windows rifletterà questo limite. Pertanto, mostrerà che la batteria è carica fino al 50% e non si carica oltre questo limite. Se abiliti Il limite di batteria mentre il dispositivo è superiore al 50% di carica, l'icona Della batteria mostrerà che il dispositivo è collegato ma si scarica fino a quando il dispositivo non raggiunge il 50% della capacità massima di carica.  

## <a name="supported-devices"></a>Dispositivi supportati

L'impostazione UEFI limite batteria è incorporata nei dispositivi Surface per impostazione predefinita, tra cui: 

- Surface Pro 7 e versioni successive
- Surface Laptop 3 e versioni successive
- Surface Book 3
- Surface Laptop Studio
- Surface Laptop Go
- Surface Studio 2
- Surface Laptop edizione Standard

 I dispositivi precedenti richiedono un aggiornamento [del firmware UEFI di Surface](manage-surface-driver-and-firmware-updates.md), disponibile tramite Windows Update o tramite i pacchetti di driver e firmware MSI nel sito [del supporto di Surface](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface). Seleziona [Abilita "Limite batteria"](https://support.microsoft.com/help/4464941) per i dispositivi Surface che devono essere collegati per lunghi periodi di tempo per la versione UEFI di Surface specifica necessaria per ogni dispositivo supportato.

## <a name="enabling-battery-limit-in-surface-uefi-surface-pro-4-and-later"></a>Abilitazione del limite di batteria in Surface UEFI (Surface Pro 4 e versioni successive)

L'impostazione Limite batteria UEFI di Surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegli **configurazione di avvio** e quindi, in **Opzioni avanzate**, attiva Attiva modalità **limite** **batteria.**  

![Limite batteria Opzioni avanzate.](images/enable-bl.png)

## <a name="enabling-battery-limit-on-surface-go-all-generations"></a>Abilitazione del limite della batteria in Surface Go (tutte le generazioni)

L'impostazione Limite batteria surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegli **configurazione di avvio** e quindi, in Modalità **tutto** schermo, sposta il dispositivo di scorrimento a destra per impostare Limite batteria su **Abilitato**.  

![Limite batteria in modalità tutto schermo in Surface Go.](images/go-batterylimit.png)

## <a name="enabling-battery-limit-in-surface-uefi-surface-pro-3"></a>Abilitazione del limite di batteria in Surface UEFI (Surface Pro 3)

L'impostazione Limite batteria UEFI di Surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegli **Modalità tutto schermo**, seleziona **Limite batteria** e quindi scegli **Abilitato**.

![Screenshot delle opzioni avanzate.](images/enable-bl-sp3.png)

![Opzioni avanzate.](images/enable-bl-sp3-2.png)

## <a name="enabling-battery-limit-using-surface-enterprise-management-mode-semm-or-surface-pro-3-firmware-powershell-scripts"></a>Abilitazione del limite di batteria tramite surface Enterprise Management Mode (SEMM) o Surface Pro 3 script di PowerShell del firmware

Il limite della batteria UEFI di Surface è disponibile anche per la configurazione tramite i metodi seguenti:

- Surface Pro 4 e versioni successive
  - [Configuratore UEFI di Microsoft Surface](surface-enterprise-management-mode.md)  
    - Script di PowerShell per Surface UEFI Manager (SEMM_Powershell.zip) in [Surface Tools for IT downloads](https://www.microsoft.com/download/details.aspx?id=46703)

### <a name="using-microsoft-surface-uefi-configurator"></a>Utilizzo del configuratore UEFI di Microsoft Surface

Per configurare la modalità Limite batteria, imposta **** l'impostazione Sostituzioni chiosco multimediale nella pagina **Configurazione** avanzata Impostazioni in SEMM (Surface Pro 4 e versioni successive).

![Screenshot delle impostazioni avanzate.](images/semm-bl.png)

### <a name="using-surface-uefi-manager-powershell-scripts"></a>Uso degli script di PowerShell di Surface UEFI Manager

La funzionalità di limite della batteria è controllata tramite l'impostazione seguente:  

`407 = Battery Profile`

**Descrizione**: schema di gestione attivo per il modello di utilizzo della batteria

**Impostazione predefinita**:  `0`

Impostare questa opzione su `1` per abilitare il limite di batteria.

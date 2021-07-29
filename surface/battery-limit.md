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
ms.openlocfilehash: 07e4131321387a410e5abd5b7039128942b1b339
ms.sourcegitcommit: ad08299d14810db746514f01d977a81fc5a3961e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "11708797"
---
# <a name="battery-limit-setting"></a>Impostazione del limite della batteria

L'opzione Limite batteria è un'impostazione UEFI che modifica la modalità di carica della batteria del dispositivo Surface e può prolungarne la longevità. Questa impostazione è consigliata nei casi in cui il dispositivo è connesso continuamente all'alimentazione, ad esempio quando i dispositivi sono integrati nelle soluzioni chiosco multimediale.  

## <a name="how-battery-limit-works"></a>Funzionamento del limite di batteria

L'impostazione del dispositivo su Limite batteria modifica il protocollo per caricare la batteria del dispositivo. Quando il limite della batteria è abilitato, la carica della batteria sarà limitata al 50% della capacità massima. Il livello di addebito riportato Windows rifletterà questo limite. Di conseguenza, mostrerà che la batteria è carica fino al 50% e non si carica oltre questo limite. Se abiliti Il limite di batteria mentre il dispositivo è superiore al 50% di carica, l'icona Della batteria mostrerà che il dispositivo è collegato ma si scarica fino a quando il dispositivo non raggiunge il 50% della capacità massima di carica.  

## <a name="supported-devices"></a>Dispositivi supportati

L'impostazione UEFI limite batteria è integrata nei dispositivi Surface più recenti, tra cui Surface Pro 7+, Surface Pro 7 e Surface Laptop 3. I dispositivi precedenti richiedono un aggiornamento [del firmware UEFI](manage-surface-driver-and-firmware-updates.md)di Surface, disponibile tramite Windows Update o tramite i pacchetti di driver e firmware MSI nel sito [del supporto di Surface.](https://support.microsoft.com/help/4023482/surface-download-drivers-and-firmware-for-surface) Seleziona [Abilita "Limite batteria"](https://support.microsoft.com/help/4464941) per i dispositivi Surface che devono essere collegati per lunghi periodi di tempo per la versione UEFI di Surface specifica necessaria per ogni dispositivo supportato.

## <a name="enabling-battery-limit-in-surface-uefi-surface-pro-4-and-later"></a>Abilitazione del limite di batteria in Surface UEFI (Surface Pro 4 e versioni successive)

L'impostazione Limite batteria UEFI di Surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegliere **configurazione di avvio**e quindi, in Opzioni **avanzate,** attivare Attiva modalità **limite** **batteria.**  

![Limite batteria Opzioni avanzate](images/enable-bl.png)

## <a name="enabling-battery-limit-on-surface-go-and-surface-go-2"></a>Abilitazione del limite della batteria in Surface Go e Surface Go 2

L'impostazione Limite batteria surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegli **configurazione di avvio**e quindi, in Modalità **tutto**schermo, sposta il dispositivo di scorrimento verso destra per impostare Limite batteria su **Abilitato.**  

![Limite batteria modalità tutto schermo in Surface Go](images/go-batterylimit.png)

## <a name="enabling-battery-limit-in-surface-uefi-surface-pro-3"></a>Abilitazione del limite di batteria in Surface UEFI (Surface Pro 3)

L'impostazione Limite batteria UEFI di Surface può essere configurata avviando surface UEFI (**Power + Vol Up** quando si accende il dispositivo). Scegli **Modalità tutto schermo,** seleziona **Limite batteria**e quindi scegli **Abilitato.**

![Screenshot delle opzioni avanzate](images/enable-bl-sp3.png)

![Opzioni avanzate](images/enable-bl-sp3-2.png)

## <a name="enabling-battery-limit-using-surface-enterprise-management-mode-semm-or-surface-pro-3-firmware-powershell-scripts"></a>Abilitazione del limite di batteria tramite surface Enterprise Management Mode (SEMM) o Surface Pro 3 script di PowerShell del firmware

Il limite della batteria UEFI di Surface è disponibile anche per la configurazione tramite i metodi seguenti:

- Surface Pro 4 e versioni successive
  - [Configuratore UEFI di Microsoft Surface](surface-enterprise-management-mode.md)  
    - Script di PowerShell per Surface UEFI Manager (SEMM_Powershell.zip) nei [download di Surface Tools per IT](https://www.microsoft.com/download/details.aspx?id=46703)

### <a name="using-microsoft-surface-uefi-configurator"></a>Utilizzo del configuratore UEFI di Microsoft Surface

Per configurare la modalità **** limite batteria, imposta l'impostazione Sostituzioni chiosco multimediale nella pagina **Configurazione** avanzata Impostazioni in SEMM (Surface Pro 4 e versioni successive).

![Screenshot delle impostazioni avanzate](images/semm-bl.png)

### <a name="using-surface-uefi-manager-powershell-scripts"></a>Uso degli script di PowerShell di Surface UEFI Manager

La funzionalità di limite della batteria è controllata tramite l'impostazione seguente:  

`407 = Battery Profile`

**Descrizione:** schema di gestione attivo per il modello di utilizzo della batteria

**Impostazione predefinita**:  `0`

Impostare questa opzione su `1` per abilitare il limite di batteria.

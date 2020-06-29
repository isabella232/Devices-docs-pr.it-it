---
title: Controllo della luminosità Surface
description: Questo argomento descrive come usare l'app controllo luminosità superficiale per gestire la luminosità dello schermo in scenari di punti vendita e chioschi.
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 197ed9fe1abc880779ad6bb0f85d2970086395f6
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833374"
---
# Controllo della luminosità Surface

Quando si distribuiscono i dispositivi Surface nel punto vendita o in altri scenari di Kiosk "always-on", è possibile ottimizzare la gestione dell'alimentazione usando la nuova app controllo luminosità superficiale.

Disponibile per il download con [gli strumenti di Surface](https://www.microsoft.com/download/details.aspx?id=46703).
Il controllo della luminosità superficiale è progettato per ridurre il carico termico e abbassare l'impronta ambientale complessiva per i dispositivi Surface distribuiti.
Se si prevede di recuperare solo questo strumento dalla pagina di download, selezionare il file **Surface_Brightness_Control_v1.16.137.0.msi** nell'elenco disponibile.
Lo strumento oscura automaticamente la schermata quando non è in uso e include le opzioni di configurazione seguenti:

- Periodo di inattività prima di visualizzare la visualizzazione in grigio.

- Livello di luminosità in grigio.

- Livello di luminosità massimo quando è in uso.

**Per eseguire il controllo della luminosità superficiale:**

- Installare surfacebrightnesscontrol.msi nel dispositivo di destinazione e il controllo della luminosità della superficie inizierà a funzionare immediatamente.

## Configurazione del controllo di luminosità superficiale

Puoi modificare i valori predefiniti tramite il registro di sistema di Windows. Per altre informazioni sull'uso del registro di sistema di Windows, vedere la [documentazione del registro di sistema](https://docs.microsoft.com/windows/desktop/sysinfo/registry).

1.  Eseguire regedit da un prompt dei comandi per aprire l'editor del registro di sistema di Windows.
    
      - Computer\HKEY\ _LOCAL \ _MACHINE controllo di luminosità \SOFTWARE\WOW6432Node\Microsoft\Surface\Surface \ 
    
    Se si sta eseguendo una versione precedente del controllo di luminosità superficiale, eseguire invece il comando seguente:
    
      - Computer\HKEY\ _LOCAL \ _MACHINE controllo di luminosità \SOFTWARE\Microsoft\Surface\Surface \


| Impostazione del registro di sistema | Dati| Descrizione  
|-----------|------------|---------------
| Controllo luminosità abilitato  |  Impostazione predefinita: 01  <br> Opzione: 01, 00 <br> Digitare: REG_BINARY |  Questa impostazione consente di attivare o disattivare il controllo di luminosità superficiale. Per disabilitare il controllo di luminosità superficiale, imposta il valore su 00. Se non si configura questa impostazione, il controllo luminosità superficie è attivato. |
| Controllo luminosità in Power Enabled| Impostazione predefinita: 01 <br> Opzioni: 01, 00 <br> Digitare: REG_BINARY | Questa impostazione consente di disattivare il controllo di luminosità superficiale quando il dispositivo è collegato direttamente a Power. Per disabilitare il controllo di luminosità superficiale quando l'alimentazione è collegata, imposta il valore su 00. Se non si configura questa impostazione, il controllo luminosità superficie è attivato. |
| Luminosità in grigio   | Impostazione predefinita: 20  <br>Opzione: intervallo di 0-100% della luminosità dello schermo <br> Tipo di dati: numero intero positivo <br> Digitare: REG_DWORD | Questa impostazione consente di gestire l'intervallo di luminosità durante i periodi di inattività. Se non si configura questa impostazione, il livello di luminosità scenderà al 20% della luminosità completa dopo 30 secondi di inattività. |
Luminosità completa   | Impostazione predefinita: 100  <br>Opzione: intervallo di 0-100% della luminosità dello schermo <br> Tipo di dati: numero intero positivo <br> Digitare: REG_DWORD  | Questa impostazione consente di gestire l'intervallo di luminosità massimo per il dispositivo. Se non si configura questa impostazione, l'intervallo di luminosità massimo è 100%.|  
| Timeout inattività| Impostazione predefinita: 30 secondi <br>Opzione: qualsiasi valore numerico  <br>Tipo di dati: intero  <br> Digitare: REG_DWORD | Questa impostazione consente di gestire il periodo di inattività prima di impostare l'oscuramento del dispositivo. Se non si configura questa impostazione, il timeout di inattività è di 30 secondi.|
| Telemetria abilitata | Impostazione predefinita: 01 <br>Opzione: 01, 00 <br> Digitare: REG_BINARY  | Questa impostazione consente di gestire la condivisione delle informazioni sull'utilizzo dell'app per migliorare il software e consentire un'esperienza utente migliore. Per disabilitare la telemetria, imposta il valore su 00. Se non si configura questa impostazione, le informazioni di telemetria vengono condivise con Microsoft in conformità con l' [informativa sulla privacy Microsoft](https://privacy.microsoft.com/privacystatement). |

## Modifiche e aggiornamenti

### Versione 1.16.137<br>
*Data di rilascio: 22 ottobre 2019*<br>
Questa versione del controllo della luminosità superficiale aggiunge il supporto per i seguenti:-ricompilato per x86, aggiungendo il supporto per Surface Pro 7, Surface Pro X e Surface laptop 3. 

### Versione 1.12.239.0
*Data di rilascio: 26 aprile 2019*<br>
Questa versione del controllo di luminosità superficiale aggiunge il supporto per i seguenti:
- Correzioni di ritardo tocco.


## Argomenti correlati

- [Impostazione del limite di batteria](battery-limit.md)

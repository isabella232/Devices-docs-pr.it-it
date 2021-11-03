---
title: Controllo della luminosità Surface
description: Questo argomento descrive come usare l'app Controllo luminosità di Surface per gestire la luminosità dello schermo negli scenari di vendita e chiosco multimediale.
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
ms.openlocfilehash: 518db8ad0070e5e7355ef57b96057c6f4ae45137
ms.sourcegitcommit: 94e11386d7034c6bc5fe753f7bebf61a9c815509
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2021
ms.locfileid: "12154071"
---
# <a name="surface-brightness-control"></a>Controllo della luminosità Surface

Quando distribuisci dispositivi Surface in punti vendita o in altri scenari di chiosco multimediale "always-on", puoi ottimizzare la gestione del risparmio energia usando la nuova app Surface Brightness Control. Surface Brightness Control è progettato per ridurre il carico termico e ridurre l'impronta di co2 complessiva per i dispositivi Surface distribuiti. Lo strumento ridimensiona automaticamente lo schermo quando non è in uso e include le opzioni di configurazione seguenti:

- Periodo di inattività prima di attenuare lo schermo.
- Livello di luminosità quando è in grigio.
- Livello massimo di luminosità in uso.

Scaricalo da [Surface Tools for IT.](https://www.microsoft.com/download/details.aspx?id=46703) Selezionare il file **Surface_Brightness_Control_v1.16.137.0.msi** nell'elenco disponibile.

## <a name="supported-devices"></a>Dispositivi supportati

- Surface Pro 3 e versioni successive
- Surface Pro X (tutte le generazioni)
- Surface 3
- Surface Book (tutte le generazioni)
- Surface Laptop Studio
- Surface Studio (tutte le generazioni)
- Surface Laptop (tutte le generazioni)
- Surface Laptop Go
- Surface Go (tutte le generazioni)


## <a name="run-surface-brightness-control"></a>Esegui controllo luminosità superficie

- Installa **Surface_Brightness_Control_v1.16.137.0.msi** nel dispositivo di destinazione e Surface Brightness Control inizierà a funzionare immediatamente.

## <a name="configure-surface-brightness-control"></a>Configurare il controllo luminosità della superficie

 è possibile modificare i valori predefiniti tramite il Windows Registro di sistema. Per ulteriori informazioni sull'utilizzo del Windows, vedere la documentazione [del Registro di sistema](/windows/desktop/sysinfo/registry).

1. Eseguire regedit da un prompt dei comandi per aprire l Windows Editor del Registro di sistema.
2. Passa a Computer\HKEY\_LOCAL\_MACHINE\SOFTWARE\WOW6432Node\Microsoft\Surface\Surface Brightness Control.
3. Modificare i valori della chiave del Registro di sistema, come descritto nella tabella seguente.

> [!TIP]
> Se stai eseguendo una versione precedente del controllo Surface Brightness, passa a: Computer\HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Surface\Surface Brightness Control\

| Impostazione del Registro di sistema | Dati| Descrizione  
|-----------|------------|---------------
| Controllo luminosità abilitato  |  Valore predefinito: 01  <br> Opzione: 01, 00 <br> Tipo: REG_BINARY |  Questa impostazione consente di attivare o disattivare Surface Brightness Control. Per disabilitare Surface Brightness Control, imposta il valore su 00. Se non si configura questa impostazione, Surface Brightness Control è attivata. |
| Controllo luminosità all'alimentazione abilitata| Valore predefinito: 01 <br> Opzioni: 01, 00 <br> Tipo: REG_BINARY | Questa impostazione consente di disattivare Il controllo della luminosità di Surface quando il dispositivo è connesso direttamente all'alimentazione. Per disabilitare Surface Brightness Control quando l'alimentazione è collegata, imposta il valore su 00. Se non si configura questa impostazione, Surface Brightness Control è attivata. |
| Luminosità in grigio   | Impostazione predefinita: 20  <br>Opzione: intervallo compreso tra 0 e 100% della luminosità dello schermo <br> Tipo di dati: numero intero positivo <br> Tipo: REG_DWORD | Questa impostazione consente di gestire l'intervallo di luminosità durante i periodi di inattività. Se non si configura questa impostazione, il livello di luminosità scenderà al 20% della luminosità completa dopo 30 secondi di inattività. |
Luminosità completa   | Impostazione predefinita: 100  <br>Opzione: intervallo compreso tra 0 e 100% della luminosità dello schermo <br> Tipo di dati: numero intero positivo <br> Tipo: REG_DWORD  | Questa impostazione consente di gestire l'intervallo di luminosità massimo per il dispositivo. Se non si configura questa impostazione, l'intervallo di luminosità massimo è 100%.|  
| Timeout inattività| Impostazione predefinita: 30 secondi <br>Opzione: qualsiasi valore numerico  <br>Tipo di dati: Integer  <br> Tipo: REG_DWORD | Questa impostazione consente di gestire il periodo di inattività prima di attenuare il dispositivo. Se non si configura questa impostazione, il timeout di inattività è 30 secondi.|
| Telemetria abilitata | Valore predefinito: 01 <br>Opzione: 01, 00 <br> Tipo: REG_BINARY  | Questa impostazione consente di gestire la condivisione delle informazioni sull'utilizzo delle app per migliorare il software e offrire un'esperienza utente migliore. Per disabilitare la telemetria, impostare il valore su 00. Se non si configura questa impostazione, le informazioni di telemetria vengono condivise con Microsoft in conformità [all'Informativa sulla privacy di Microsoft.](https://privacy.microsoft.com/privacystatement) |

## <a name="changes-and-updates"></a>Modifiche e aggiornamenti

### <a name="version-116137br"></a>Versione 1.16.137<br>

*Data di rilascio: 22 ottobre 2019*<br>
Questa versione di Surface Brightness Control aggiunge il supporto per gli elementi seguenti: -Recompiled per x86, aggiungendo il supporto per Surface Pro 7, Surface Pro X e Surface Laptop 3.

### <a name="version-1122390"></a>Versione 1.12.239.0

*Data di rilascio: 26 aprile 2019*<br>
Questa versione di Surface Brightness Control aggiunge il supporto per gli elementi seguenti:

- Correzioni di ritardo tocco.

## <a name="related-topics"></a>Argomenti correlati

- [Impostazione limite batteria](battery-limit.md)

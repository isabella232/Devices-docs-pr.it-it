---
title: Ottimizzare le videoconferenze sui dispositivi Surface
description: Questa pagina fornisce le procedure consigliate per l'uso di Microsoft Teams e altre soluzioni di videoconferenza nei dispositivi Surface
ms.prod: w11
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 12/10/2021
ms.reviewer: gusing
manager: laurawi
audience: itpro
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 28ad64b41dedb7d66092cf98388920a732fee737
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449679"
---
# <a name="optimize-video-conferencing-on-surface-devices"></a>Ottimizzare le videoconferenze sui dispositivi Surface

I dispositivi Surface sfruttano i più recenti progressi nel consumo di energia dei dispositivi mobili per offrire un'esperienza semplificata ottimizzata tra i carichi di lavoro. Per la maggior parte dei carichi di lavoro, questo offre un'esperienza ottimale. Per alcuni carichi di lavoro che Microsoft Teams o altre applicazioni di videoconferenza, è consigliabile seguire questi consigli per garantire l'esperienza migliore.

## <a name="surface-drivers-and-firmware"></a>Driver e firmware di Surface

Microsoft rilascia regolarmente gli aggiornamenti per i dispositivi Surface e ha rilasciato diversi aggiornamenti di Surface per i carichi di lavoro di videoconferenza, tra cui:

- Miglioramenti delle prestazioni del sistema
- Miglioramenti del consumo energetico nei driver della fotocamera
- Aggiornamenti dei driver di grafica
- Ottimizzazioni delle impostazioni di risparmio energia

### <a name="get-updates-to-all-devices"></a>Ottenere aggiornamenti per tutti i dispositivi

Assicurati che l'organizzazione abbia un processo per i dispositivi per ricevere questi aggiornamenti. Se stai usando Windows Update o [Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb), ricevi già gli aggiornamenti più recenti di Surface quando vengono rilasciati. Controlla la disponibilità di aggiornamenti Windows Update e verifica che siano stati installati gli aggiornamenti più recenti di Surface. Per ulteriori informazioni, vedere:

- [Cronologia degli aggiornamenti di Surface](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history)
- [Installare surface e Windows aggiornamenti](https://www.microsoft.com/surface/support/performance-and-maintenance/install-software-updates-for-surface?)

Se stai usando altre opzioni per installare i driver di Surface e gli aggiornamenti del firmware, dovrai installare manualmente gli aggiornamenti di Surface più recenti usando i file MSI pubblicati o installare gli aggiornamenti con Configuration Manager. Per ulteriori informazioni, vedere:

- [Scaricare driver e firmware per Surface](https://support.microsoft.com/help/4023482)
- [Gestire e installare gli aggiornamenti di driver e firmware per Surface](manage-surface-driver-and-firmware-updates.md)
- [Come gestire gli aggiornamenti dei driver di Surface in Configuration Manager](https://support.microsoft.com/help/4098906)

### <a name="graphics-driver-updates-for-microsoft-teams"></a>Aggiornamenti dei driver di grafica per Microsoft Teams

I modelli di dispositivi Surface più recenti con processori Intel di 10° e 11° generazione hanno ricevuto aggiornamenti dei driver di grafica che consentono di risolvere i carichi di lavoro delle videoconferenze. Per abilitare questi miglioramenti, assicurarsi di installare quanto segue:

- Microsoft Teams **versione 1.4.00.22472** o successiva.
- Driver di grafica Intel **27.20.100.9621** o versione successiva.

### <a name="power-settings-optimizations"></a>Ottimizzazioni delle impostazioni di risparmio energia

I dispositivi Surface possono regolare le impostazioni di risparmio energia correlate alle prestazioni modificando la posizione del dispositivo di scorrimento di alimentazione Windows prestazioni in Windows 10, nota anche come modalità risparmio energia in Windows 11.

Alcuni dispositivi Surface hanno ricevuto aggiornamenti che includono ottimizzazioni delle impostazioni di alimentazione per i carichi di lavoro di videoconferenza in base alla posizione del dispositivo di scorrimento o alla modalità di alimentazione. Tuttavia, poiché Windows 10 e Windows 11 usano la posizione consigliata del dispositivo di scorrimento **** di alimentazione e la posizione in modalità di alimentazione per i carichi di lavoro delle videoconferenze, dovrai regolare il dispositivo di scorrimento di alimentazione per abilitare queste ottimizzazioni:

1. Connessione'alimentazione CA (le ottimizzazioni non vengono eseguite quando si utilizza l'alimentazione a batteria).  
2. Regola il dispositivo di scorrimento o la posizione della modalità risparmio energia per usare **Prestazioni migliori** **o Prestazioni migliori.**

## <a name="learn-more"></a>Scopri di più

- [Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface](maintain-optimal-power-settings-on-surface-devices.md)
- [Massimizzare la durata della batteria di Surface](https://support.microsoft.com/surface/maximize-your-surface-battery-life-45479867-a7fa-33dd-fc4d-6762e9b3b11a)

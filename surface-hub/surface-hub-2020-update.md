---
title: Installare l'aggiornamento 2020 di Windows 10 Team
description: Ottenere l'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 Team aggiornamento 2020.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/17/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 7474787351a9371fb09fa10348ac9f6591b81f6b
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497829"
---
# <a name="install-windows-10-team-2020-update"></a>Installare l'aggiornamento 2020 di Windows 10 Team 

Il nuovo sistema operativo Surface Hub, **Windows 10 Team aggiornamento 2020**, basato su Windows 10 versione 20H2, è ora disponibile per Surface Hub 2S e il Surface Hub originale (v1). 

- Vedere anche: [Problemi noti: aggiornamento Windows 10 Team 2020](surface-hub-2020-team-update-known-issues.md)

## <a name="distribution"></a>Distribuzione

È possibile ottenere Windows aggiornamento 2020 usando uno dei metodi seguenti:

- **Windows Update per le aziende**.
- **Immagine bare metal recovery (BMR).** Opzione consigliata per i clienti che si uniscono ai propri dispositivi per Azure Active Directory o non consentono ai propri dispositivi di ricevere aggiornamenti da Internet. Per iniziare, vedi [Scaricare un'immagine di ripristino per Surface](https://support.microsoft.com/surfacerecoveryimage).
- **Windows Update.** La disponibilità varia in base all'area/paese, come indicato nella tabella seguente:

| Fase | Paese/Area geografica                         | A partire          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ, Australia, Canada, Belgio, Messico | Ottobre 2020  |
| 2     | Regno Unito, Giappone, Svizzera, Italia          | Novembre 2020 |
| 3     | Germania, Paesi Bassi                   | Fine febbraio 2021 |
| 4     | Globale                                 | Inizio marzo 2021 |

## <a name="servicing-surface-hubs-with-windows-10-team-edition-version-1703"></a>Manutenzione di Surface Hub con Windows 10 Team Edition versione 1703 

Il supporto completo per la manutenzione per [Windows 10 Team Edition versione 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f) è previsto per continuare fino al 16 marzo 2021.

### <a name="2s-devices"></a>Dispositivi 2S 

I clienti in tutte le aree possono aggiornare i dispositivi Surface Hub 2S all'aggiornamento 2020 tramite Windows Update, Windows Update per le aziende o usando l'immagine di ripristino bare metal, come illustrato in [Reimpostazione e ripristino per Surface Hub 2S](surface-hub-2s-recover-reset.md).

### <a name="v1-devices"></a>Dispositivi V1 

I clienti di tutte le aree possono aggiornare i dispositivi Surface Hub v1 all'aggiornamento 2020 tramite Windows Update, Windows Update per le aziende o [usando lo strumento di ripristino Surface Hub](surface-hub-recovery-tool.md). È necessario installare KB5000749 per ricevere l'aggiornamento in modalità over-the-air. Per altre informazioni, vedere [Surface IT Pro Blog](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-hub-v1-status/ba-p/2118371).
 
## <a name="whats-new"></a>Novità

Windows 10 Team aggiornamento 2020 offre importanti miglioramenti alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità di Windows più recenti. Per altre informazioni, vedere [Novità dell'aggiornamento di Windows 10 Team 2020](surface-hub-2020-update-whats-new.md).
 
## <a name="before-you-begin"></a>Prima di iniziare

Prima di installare Windows 10 Team aggiornamento 2020, assicurarsi di salvare la chiave BitLocker associata al dispositivo. 

**Per salvare manualmente la chiave di BitLocker**

1. Inserire un'unità USB in Surface Hub.
2. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
3. Passare a Update & **SecurityRecovery.Navigate to Update & SecurityRecovery.Navigate** to **Update & SecurityRecovery** > .
4. In **BitLocker** selezionare **Salva**. La chiave BitLocker viene salvata in un file di testo nell'unità USB.

Per altre informazioni, vedere [Salvare la chiave di BitLocker](save-bitlocker-key-surface-hub.md).

## <a name="learn-more"></a>Scopri di più

- [Novità dell'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update-whats-new.md)
- [Aggiornamento all'implementazione di Windows 10 Team](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-february-status/ba-p/2118369)

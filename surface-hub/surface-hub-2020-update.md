---
title: Installare l'aggiornamento 2020 di Windows 10 Team
description: Ottieni l'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 Team 2020 Update.
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
ms.openlocfilehash: 4d68f751bd15ef6529bcd16a6305d8c682970747
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470414"
---
# <a name="install-windows-10-team-2020-update"></a>Installare l'aggiornamento 2020 di Windows 10 Team 

Il nuovo sistema operativo Surface Hub, **Windows 10 Team 2020 Update,** basato su Windows 10 versione 20H2, è ora disponibile per Surface Hub 2S e Surface Hub originale (v1). 

- Vedi anche: [Problemi noti: Windows 10 Team 2020 Update](surface-hub-2020-team-update-known-issues.md)

## <a name="distribution"></a>Distribuzione

È possibile ottenere Windows 2020 Update utilizzando uno dei metodi seguenti:

- **Windows Update for Business**.
- **Immagine di ripristino bare metal (BMR).** Opzione consigliata per i clienti che aderiscono ai propri dispositivi ad Azure Active Directory o non consentono ai dispositivi di ricevere aggiornamenti da Internet. Per iniziare, vedi [Scaricare un'immagine di ripristino per Surface.](https://support.microsoft.com/surfacerecoveryimage)
- **Windows Update.** La disponibilità varia in base all'area geografica/paese, come illustrato nella tabella seguente:

| Fase | Paese/Area geografica                         | Avvio          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ, Australia, Canada, Belgio, Messico | Ottobre 2020  |
| 2     | Regno Unito, Giappone, Svizzera, Italia          | Novembre 2020 |
| 3     | Germania, Paesi Bassi                   | Fine febbraio 2021 |
| 4     | Globale                                 | Inizio marzo 2021 |

## <a name="servicing-surface-hubs-with-windows-10-team-edition-version-1703"></a>Manutenzione di Surface Hub con Windows 10 Team Edition versione 1703 

Il supporto completo per la manutenzione per [Windows 10 Team Edition versione 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f) è pianificato per continuare fino al 16 marzo 2021.

### <a name="2s-devices"></a>Dispositivi 2S 

I clienti di tutte le aree geografiche possono aggiornare i dispositivi Surface Hub 2S all'aggiornamento 2020 tramite Windows Update, Windows Update per le aziende o usando l'immagine di ripristino bare metal (BMR), come spiegato in [Reset and recovery for Surface Hub 2S.](surface-hub-2s-recover-reset.md)

### <a name="v1-devices"></a>Dispositivi V1 

I clienti di tutte le aree geografiche possono aggiornare i dispositivi Surface Hub v1 all'aggiornamento 2020 tramite Windows Update, Windows Update for Business o lo strumento di ripristino [di Surface Hub.](surface-hub-recovery-tool.md) KB5000749 deve essere installato per ricevere l'aggiornamento in modalità over-the-air. Per altre informazioni, vedi [Blog su Surface IT Pro.](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-hub-v1-status/ba-p/2118371)
 
## <a name="whats-new"></a>Novità

Windows 10 Team 2020 Update apporta miglioramenti principali alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità più recenti di Windows 10. Per altre informazioni, vedi [Novità di Windows 10 Team 2020 Update.](surface-hub-2020-update-whats-new.md)
 
## <a name="before-you-begin"></a>Prima di iniziare

Prima di installare Windows 10 Team 2020 Update, assicurati di salvare la chiave BitLocker associata al dispositivo. 

**Per salvare manualmente la chiave di BitLocker**

1. Inserisci un'unità USB in Surface Hub.
2. In Surface Hub apri **Impostazioni** e immetti le credenziali di amministratore quando richiesto.
3. Passare a **Update & Security**  >  **Recovery**.
4. In **BitLocker**seleziona **Salva.** La chiave BitLocker viene salvata in un file di testo nell'unità USB.

Per altre informazioni, vedi [Salvare la chiave di BitLocker.](save-bitlocker-key-surface-hub.md)

## <a name="learn-more"></a>Altre informazioni

- [Novità dell'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update-whats-new.md)
- [Aggiornamento all'implementazione di Windows 10 Team](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-february-status/ba-p/2118369)

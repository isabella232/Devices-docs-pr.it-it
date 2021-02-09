---
title: Installare l'aggiornamento 2020 di Windows 10 Team
description: Ottenere l'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 team 2020 Update.
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
ms.openlocfilehash: 291a2eda0c1fa6e5e2fd2240861c8570d00054df
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319180"
---
# Installare l'aggiornamento 2020 di Windows 10 Team 

Il nuovo sistema operativo Surface Hub, **Windows 10 Team 2020 Update**, basato su Windows 10 versione 20H2, è ora disponibile per Surface Hub 2S e per Surface Hub originale (V1). 

- Vedere anche: [problemi noti: aggiornamento di Windows 10 Team 2020](surface-hub-2020-team-update-known-issues.md)

## Distribuzione

Per ottenere l'aggiornamento di Windows 2020, è possibile usare uno dei metodi seguenti:

- **Windows Update for business**.
- **Immagine di recupero bare metal (BMR)**. Opzione consigliata per i clienti che accedono ai loro dispositivi in Azure Active Directory o non consentono ai loro dispositivi di ricevere aggiornamenti da Internet. Per iniziare, vedere [scaricare un'immagine di ripristino per la superficie](https://support.microsoft.com/surfacerecoveryimage).
- **Windows Update.** La disponibilità varia in base all'area geografica/paese, come indicato nella tabella seguente:

| Fase | Paese/Area geografica                         | Iniziale          |
| ----- | -------------------------------------- | ----------------- |
| 1     | NZ, Australia, Canada, Belgio, Messico | 2020 ottobre  |
| 2     | UK, Giappone, Svizzera, Italia          | 2020 novembre |
| 3     | Stati Uniti, Germania                            | Fine febbraio 2021 |
| 4     | Globale                                 | Fine febbraio 2021 |

## Manutenzione degli hub di Surface con Windows 10 Team Edition versione 1703 

Il supporto completo per la manutenzione per [Windows 10 Team Edition versione 1703](https://support.microsoft.com/topic/november-12-2019-kb4525245-os-build-15063-2172-dfc81b85-11a6-54ef-4370-11408193419f) è programmato per continuare fino al 16 marzo 2021.

### dispositivi 2S 

I clienti di tutte le aree geografiche possono continuare ad aggiornare i loro dispositivi di Surface Hub 2S all'aggiornamento di 2020 usando Windows Update for business o usando un'immagine BMR (Bare Metal Recovery), come spiegato in [reimpostazione e ripristino per Surface Hub 2S](surface-hub-2s-recover-reset.md).

### Dispositivi V1 

I clienti di tutte le aree geografiche possono ora aggiornare i loro dispositivi Surface Hub V1 all'aggiornamento di 2020 [usando lo strumento di ripristino di Surface Hub](surface-hub-recovery-tool.md). Saranno presto disponibili altri metodi per aggiornare questi dispositivi all'aggiornamento di Windows 10 team 2020. Per altre informazioni, Vedi [Blog Surface it Pro](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655).
 
## Novità

Windows 10 team 2020 Update offre miglioramenti importanti alla distribuzione e alla gestibilità dei dispositivi insieme alle caratteristiche più recenti di Windows 10. Per altre informazioni, vedere [novità di Windows 10 Team 2020 Update](surface-hub-2020-update-whats-new.md).
 
## Prima di iniziare

Prima di installare Windows 10 team 2020 Update, verificare di aver salvato la chiave BitLocker associata al dispositivo. 

**Per salvare manualmente la chiave BitLocker**

1. Inserire un'unità USB in Surface Hub.
2. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
3. Passare a **aggiornamento &**  >  **ripristino**della sicurezza.
4. In **BitLocker**selezionare **Salva**. La chiave BitLocker viene salvata in un file di testo nell'unità USB.

Per altre informazioni, vedere [salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md).

## Altre informazioni

- [Novità dell'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update-whats-new.md)
- [Aggiornamento all'implementazione di Windows 10 Team](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)

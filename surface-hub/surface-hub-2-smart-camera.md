---
title: Installare e gestire Surface Hub 2 Smart Camera
description: Spiega come installare e gestire le impostazioni per la smart camera Surface Hub 2.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/16/2022
ms.localizationpriority: Medium
ms.openlocfilehash: 1b510d98cf65b5b1594d300a3bcf6c928e1f27e2
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497519"
---
# <a name="install-and-manage-surface-hub-2-smart-camera"></a>Installare e gestire Surface Hub 2 smart camera

Surface Hub 2 Smart Camera1<sup></sup> è progettato per i team ibridi e ottimizzato per i partecipanti remoti. Con una forte attenzione al primo piano e allo sfondo, i partecipanti remoti possono vedere le persone interagire con il contenuto sulla Surface Hub, visualizzando anche tutti gli altri nella stanza. Surface Hub 2 Smart Camera ha un ampio campo visivo superiore a 136 gradi, inquadratura automatica, ottica in vetro di alta qualità e un sensore a bassa luce.
![La visualizzazione della fotocamera ultra-wide include la lavagna delle persone su bordi estremi dell'hub da 85"](images/surface-hub-2-smart-camera-fov.png)

*La visualizzazione della fotocamera ultra-wide include la lavagna delle persone su bordi estremi dell'hub da 85"*

## <a name="system-requirements"></a>Requisiti di sistema

Per surface hub che eseguono il sistema operativo del team, Surface Hub 2 Smart Camera richiede gli aggiornamenti seguenti per [l'aggiornamento di Windows 10 Team 2020](surface-hub-2020-update-whats-new.md) (20H2) in Surface Hub 2:

- Windows 10 Team 2020 Update 2 (KB5010415 o un aggiornamento Windows successivo)
- Aggiornamento hardware di sistema — 21/1/2022 (o un successivo aggiornamento hardware del sistema)

Per altre informazioni, vedere [Surface Hub cronologia degli aggiornamenti](surface-hub-update-history.md).

> [!NOTE]
> Non sono necessari aggiornamenti aggiuntivi per surface hub migrati per eseguire Windows 10/11 Pro o Enterprise.

## <a name="install-smart-camera"></a>Installare la fotocamera intelligente

1. Collegare la fotocamera alla porta USB-C al centro della parte superiore di Surface Hub 2. L'indicatore LED si accende brevemente quando la fotocamera è connessa e in modo continuo quando la fotocamera è in uso.

     ![Collegare la fotocamera alla porta USB-C al centro della parte superiore di Surface Hub 2.](images/hub2smartcamera1.png)

2. Per rimuovere la fotocamera, tirare su e avanti. Un tether magnetico impedisce che la fotocamera venga spenta o tirata all'indietro.

    ![Per rimuovere la fotocamera, tirare su e avanti.](images/hub2smartcamera2.png)

> [!TIP]
> Il coperchio della fotocamera si aggancia magneticamente alla parte anteriore per la privacy e alla parte posteriore per l'archiviazione quando non è in uso.

## <a name="manage-automatic-framing-settings"></a>Gestire le impostazioni di frame automatico

L'inquadratura automatica zooma dinamicamente e ti mantiene centrato nel video quando ti sposti. La modalità di gestione delle impostazioni dipende dal sistema operativo installato in Surface Hub:

- [aggiornamento Windows 10 Team 2020 (20H2)](#windows-10-team-2020-update-20h2)
- [Windows 11 Desktop in Surface Hub](#windows-11-desktop-on-surface-hub)
- [Windows 10 Desktop in Surface Hub](#windows-10-desktop-on-surface-hub)

### <a name="windows-10-team-2020-update-20h2"></a>aggiornamento Windows 10 Team 2020 (20H2)

Quando si installa il Surface Hub Smart Camera, l'inquadratura automatica è abilitata per impostazione predefinita. Gli amministratori possono gestire l'inquadratura automatica da Impostazioni tramite un interruttore On/Off che imposta lo stato di frame automatico all'inizio di ogni sessione di Surface Hub.

**Per regolare l'inquadratura automatica:**

1. Nel Surface Hub 2S accedere come **amministratore**.

> [!NOTE]
> Se non si conosce il nome utente o la password di amministratore, è necessario reimpostare il dispositivo. Per altre informazioni, vedere [Reimpostazione e ripristino per Surface Hub 2S](/surface-hub/surface-hub-2s-recover-reset).

2. Aprire **Impostazioni** e passare a **Surface Hub > Chiamata & Audio.**
3. In **Inquadratura automatica** regolare l'interruttore, in base alle esigenze. 
4. Selezionare **Fine sessione**; le impostazioni modificate vengono applicate all'avvio di una nuova sessione. 

Se l'interruttore è impostato su **Attivato**, il frame automatico sarà sempre attivato per impostazione predefinita quando gli utenti iniziano una sessione in Surface Hub. Se l'interruttore è impostato su **Disattivato**, l'inquadratura automatica sarà sempre disattivata per impostazione predefinita all'avvio di una sessione in Surface Hub.

#### <a name="manage-camera-settings-via-an-mdm-provider"></a>Gestire le impostazioni della fotocamera tramite un provider MDM

Gli amministratori possono gestire l'inquadratura automatica tramite il [provider di servizi di configurazione Surface Hub](/windows/client-management/mdm/surfacehub-csp) (CSP) da Intune o da un provider di gestione di dispositivi mobili (MDM) di terze parti.

|Impostazione dei criteri CSP| Descrizione|
|------------------|------------|
|DefaultAutomaticFraming|Se si attiva questa impostazione di criterio, l'inquadratura automatica è abilitata. Se si disattiva questa impostazione di criterio, il frame automatico viene disabilitato. Se non si configura questa impostazione di criterio, l'inquadratura automatica è abilitata. |

Per altre informazioni, vedere quanto segue:

- [Gestire le impostazioni con un provider MDM](/surface-hub/manage-settings-with-mdm-for-surface-hub#create-custom-configuration-profile)
- [SurfaceHub CSP - Gestione client Windows](/windows/client-management/mdm/surfacehub-csp)

### <a name="windows-11-desktop-on-surface-hub"></a>Windows 11 Desktop in Surface Hub

Se è stata [eseguita la migrazione del Surface Hub](surface-hub-2s-migrate-os.md) per eseguire Windows 11 Pro o Windows 11 Enterprise, è necessario attivare l'inquadratura automatica per la smart camera Surface Hub. Per impostazione predefinita, l'inquadratura automatica è disattivata.

Per attivare l'inquadratura automatica, passare ai **dispositivi Impostazioni > Bluetooth & > Gestire le fotocamere> Surface Hub 2 Smart Camera.**

### <a name="windows-10-desktop-on-surface-hub"></a>Windows 10 Desktop in Surface Hub

Il frame automatico è sempre abilitato e non può essere disabilitato o configurato in altro modo.

## <a name="order-surface-hub-2-smart-camera"></a>Ordinare Surface Hub 2 smart camera

Acquistare Surface Hub 2 Smart Camera dal [rivenditore Microsoft Surface autorizzato](https://www.microsoft.com/surface/business/where-to-buy-microsoft-surface?).

### <a name="references"></a>Riferimenti

1. Surface Hub 2 Smart Camera, venduto separatamente a partire dal 16 marzo 2022, regola dinamicamente il feed video per i partecipanti remoti. Surface Hub 2 Smart Camera sarà inclusa nella scatola con Surface Hub 2S 85" a partire da maggio 2022.

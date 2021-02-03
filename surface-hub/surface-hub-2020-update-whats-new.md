---
title: Novità dell'aggiornamento 2020 di Windows 10 Team
description: Scopri le novità dell'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 team 2020 Update.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: Medium
ms.openlocfilehash: f87b8f084b8731bfb329b6c52403d565bca03e3e
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312052"
---
# Novità dell'aggiornamento 2020 di Windows 10 Team

Windows 10 team 2020 Update offre miglioramenti importanti alla distribuzione e alla gestibilità dei dispositivi insieme alle caratteristiche più recenti di Windows 10.

##  Distribuzione e gestibilità

- **Autenticazione moderna per gli account di dispositivo cloud**. Surface Hub supporta i servizi Web Exchange (EWS) e l'autenticazione basata su ADAL (Active Directory Authentication Library) per connettersi a Exchange, consentendo ai clienti di deprecare l'uso dell'autenticazione di base. Per altre informazioni, vedere [autenticazione moderna in Surface Hub](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth).
- **Più di 20 criteri di gestione di dispositivi mobili nuovi e aggiornati (MDM)**.      Questi criteri conferiscono agli amministratori IT un maggiore controllo sulle impostazioni di più dispositivi, tra cui: gli aggiornamenti delle app da Microsoft Store, le impostazioni di proiezione wireless, ad esempio Miracast, le impostazioni di rete, ad esempio la qualità del servizio e l'autenticazione cablata 802.1 x, e le nuove impostazioni relative alla privacy/PILR. Per altre informazioni, vedere: 
- [Gestire Surface Hub 2S con Microsoft Intune](surface-hub-2s-manage-intune.md).
- [Criteri CSP supportati da Microsoft Surface Hub](https://docs.microsoft.com//windows/client-management/mdm/policy-csps-supported-by-surface-hub)

##  Dispositivi Uniti in Azure Active Directory

- **Single Sign-on (SSO) per i dispositivi Uniti ad Azure ad**. Quando gli utenti accede con le proprie credenziali di Microsoft 365 a "riunioni e file personali", le credenziali utente scorrono senza problemi dall'app all'app, incluse le esperienze di Microsoft 365 nel browser.
- **Accesso condizionale (CA) per i dispositivi Uniti ad Azure ad**.       Gli amministratori IT possono distribuire criteri di sicurezza a livello di dispositivo nel relativo hub Surface di Azure ad, per controllare l'accesso alle risorse dell'organizzazione in conformità con i requisiti di sicurezza e conformità aziendali.
- **Supporto per gli amministratori non globali per i dispositivi Uniti ad Azure ad**. I clienti possono scegliere un set di amministratori più granulare nella gerarchia di amministratori per gestire Surface Hub. Per altre informazioni, vedere [configurare gli account di amministratore non globali in Surface Hub 2S](surface-hub-2s-nonglobal-admin.md).


## Browser e penna

- **Supporto per il nuovo Microsoft Edge**. Microsoft Edge è stato ricostruito per ottimizzare le prestazioni, la sicurezza e la privacy di compatibilità. Per altre informazioni, vedere [installare e configurare il nuovo Microsoft Edge in Surface Hub](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge).
- - **Input penna a due punte su Surface Hub 2S**.   Gli utenti possono lavagna e collaborare affiancati su Surface Hub 2S usando due penne Surface Hub 2. Gli aggiornamenti del firmware necessari per abilitare l'input penna Dual-Pen verranno rilasciati con un aggiornamento successivo.

## Microsoft Teams  

- **Microsoft teams è installato per impostazione predefinita**.        Microsoft teams è incluso come le riunioni predefinite, l'app per la chiamata e la collaborazione nei nuovi dispositivi di Surface Hub che possono essere modificati o configurati tramite MDM o direttamente su Surface hub usando l'app Impostazioni. Per altre informazioni, vedere [distribuire Microsoft teams](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub).
- **Supporto per la vicinanza a Microsoft teams**.  Il join di prossimità consente agli utenti di eseguire chiamate Microsoft teams pianificate su un hub di Surface vicino usando il loro portatile/telefono o la transizione senza soluzione di una riunione in corso a un hub di Surface vicino. Windows 10 team 2020 Update aggiunge il supporto per la gestione di dispositivi mobili (MDM) per configurare l'aggiunta di prossimità. Per altre informazioni, vedere: 

  - [Blog di Microsoft teams](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833). 
  - [Gestire le impostazioni di Microsoft Teams in Surface Hub](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

- **Supporto per riunioni coordinate con Microsoft teams**. Nelle sale riunioni che includono un hub Surface e un dispositivo sala Microsoft teams oppure gli spazi con due dispositivi Surface Hub, le riunioni coordinate consentono agli utenti di sfruttare facilmente entrambi i dispositivi durante una riunione di Microsoft teams. Con un singolo tocco, gli utenti possono partecipare a una riunione da uno dei due dispositivi e massimizzare l'immobiliare dello schermo mostrando i feed video su un dispositivo e una lavagna digitale o un contenuto dall'altro. Windows 10 team 2020 Update aggiunge il supporto per la gestione di dispositivi mobili (MDM) per configurare riunioni coordinate e la funzionalità verrà successivamente rilasciata come aggiornamento di Microsoft teams tramite Microsoft Store.To altre informazioni, vedere [configurare riunioni coordinate con le sale di Microsoft teams e Surface Hub](https://docs.microsoft.com/microsoftteams/rooms/coordinated-meetings).

## Sicurezza

- **Accesso senza password tramite le chiavi di sicurezza di FIDO2**     Usando le chiavi di sicurezza di FIDO2, i clienti possono accedere rapidamente e facilmente a Surface Hub senza dover digitare nomi utente e password. In combinazione con Single Sign-On (SSO), questa caratteristica offre un'autenticazione veloce e perfetta per file, app e siti Web durante una riunione. Per altre informazioni, vedere [configurare l'accesso senza password su Surface Hub](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate).
- **Miglioramenti all'accesso senza password tramite Microsoft Authenticator**.  Per le organizzazioni che usano Azure AD, gli utenti possono usare l'app Microsoft Authenticator per accedere senza dover digitare nomi utente e password. Inoltre, gli utenti possono accedere usando gli alias di posta elettronica preferiti in Azure AD oltre al nome dell'entità utente (UPN). Per altre informazioni, vedere [accedere a Surface Hub con Microsoft Authenticator](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app).


## Altre informazioni

- [Aggiornamento all'implementazione di Windows 10 Team](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)
- [Installare l'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update.md)  
 
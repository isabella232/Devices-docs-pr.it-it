---
title: Novità dell'aggiornamento 2020 di Windows 10 Team
description: Scopri le novità dell'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 Team 2020 Update.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 14e08cf099ac441f7b2b3b76366406868ac6c056
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470424"
---
# <a name="whats-new-in-windows-10-team-2020-update"></a>Novità dell'aggiornamento 2020 di Windows 10 Team

Windows 10 Team 2020 Update apporta miglioramenti principali alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità più recenti di Windows 10.

##  <a name="deployment-and-manageability"></a>Distribuzione e gestibilità

- **Autenticazione moderna per gli account dei dispositivi cloud**. Surface Hub supporta l'autenticazione basata su Servizi Web Exchange (EWS) e Active Directory Authentication Library (ADAL) per connettersi a Exchange, consentendo ai clienti di deprecato l'uso dell'autenticazione di base. Per altre informazioni, vedi [Autenticazione moderna in Surface Hub.](https://docs.microsoft.com/surface-hub/surface-hub-modern-auth)
- **Più di 20 impostazioni dei criteri**di gestione dei dispositivi mobili (MDM) nuove e aggiornate.  Queste impostazioni dei criteri offrono agli amministratori IT un controllo migliorato su più impostazioni del dispositivo, tra cui: aggiornamenti delle app da Microsoft Store, impostazioni di proiezione wireless come Miracast sull'infrastruttura, impostazioni di rete come qualità del servizio e autenticazione cablata 802.1x e nuove impostazioni correlate a privacy/GDPR. I nuovi provider di servizi di configurazione includono: 

  - [CSP account](https://docs.microsoft.com/windows/client-management/mdm/accounts-csp) 
  - [Firewall-CSP](https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) 
  - [CSP RemoteWipe](https://docs.microsoft.com/windows/client-management/mdm/remotewipe-csp) 
  - [Wifi-CSP](https://docs.microsoft.com/windows/client-management/mdm/wifi-csp) 
  - [Wirednetwork-CSP](https://docs.microsoft.com/windows/client-management/mdm/wirednetwork-csp) 

Per ulteriori informazioni, vedere: 
- [CSP supportati in Microsoft Surface Hub](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md)


##  <a name="azure-active-directory-joined-devices"></a>Dispositivi aggiunti ad Azure Active Directory

- **Single #A0 (SSO) per dispositivi aggiunti ad Azure AD**. Quando gli utenti acorrono con le credenziali di Microsoft 365 a "Riunioni e file personali", le credenziali utente fluire senza problemi da un'app all'altra, incluse le esperienze di Microsoft 365 nel browser.
- **Accesso condizionale (CA) per dispositivi aggiunti ad Azure AD**.       Gli amministratori IT possono distribuire criteri di sicurezza a livello di dispositivo al dispositivo Surface Hub aggiunto ad Azure AD per controllare l'accesso alle risorse dell'organizzazione in conformità ai requisiti di conformità e sicurezza aziendali.
- **Supporto per gli amministratori non globali per i dispositivi aggiunti ad Azure AD**. I clienti possono scegliere un set più granulare di amministratori all'interno della gerarchia di amministrazione per gestire Surface Hub. Per altre informazioni, vedi [Configurare account di amministratore non globali in Surface Hub.](surface-hub-2s-nonglobal-admin.md)


## <a name="browser-and-pen"></a>Browser e penna

- **Supporto per il nuovo Microsoft Edge**. Microsoft Edge è stato ricostruito per garantire prestazioni ottimali di compatibilità, sicurezza e privacy. Per altre informazioni, vedi [Installare e configurare il nuovo Microsoft Edge in Surface Hub.](https://docs.microsoft.com/surface-hub/surface-hub-install-chromium-edge)
- **Input penna doppia in Surface Hub 2S.**   Gli utenti possono lavagna e collaborare side-by-side in Surface Hub 2S usando due penne surface hub 2. Gli aggiornamenti del firmware necessari per abilitare l'input penna doppia verranno rilasciati con un aggiornamento successivo.

## <a name="microsoft-teams"></a>Microsoft Teams  

- **Microsoft Teams installato per impostazione predefinita.**        Microsoft Teams è incluso come app riunioni, chiamate e collaborazione predefinita nei nuovi dispositivi Surface Hub che possono essere modificati o configurati tramite MDM o direttamente su Surface Hub usando l'app Impostazioni. Per ulteriori informazioni, vedere [Deploy Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/teams-surface-hub).
- **Supporto per l'aggiunta di prossimità con Microsoft Teams**.  L'aggiunta di prossimità consente agli utenti di effettuare chiamate pianificate di Microsoft Teams su un dispositivo Surface Hub nelle vicinanze usando il portatile/telefono o di eseguire la transizione senza problemi di una riunione in corso a un Dispositivo Surface Hub nelle vicinanze. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dispositivi mobili (MDM) per configurare l'aggiunta di prossimità. Per ulteriori informazioni, vedere: 

  - [Blog di Microsoft Teams](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833). 
  - [Gestire le impostazioni di Microsoft Teams in Surface Hub](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

- **Supporto per riunioni coordinate con Microsoft Teams**. Nelle sale riunioni che presentano un dispositivo Surface Hub e una sala di Microsoft Teams o spazi con due dispositivi Surface Hub, le riunioni coordinate consentono agli utenti di sfruttare facilmente entrambi i dispositivi durante una riunione di Microsoft Teams. Con un singolo tocco, gli utenti possono partecipare a una riunione da entrambi i dispositivi e ottimizzare lo spazio sullo schermo mostrando feed video su un dispositivo e una lavagna digitale o contenuto sull'altro. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dei dispositivi mobili (MDM) per configurare le riunioni coordinate e la funzionalità verrà successivamente rilasciata come aggiornamento di Microsoft Teams tramite Microsoft Store.To Per ulteriori informazioni, vedere [Set up Coordinated Meetings with Microsoft Teams Rooms and Surface Hub.](https://docs.microsoft.com/microsoftteams/rooms/coordinated-meetings)

## <a name="security"></a>Sicurezza

- **Accesso senza password con chiavi di sicurezza FIDO2**     Usando le chiavi di sicurezza FIDO2, i clienti possono accedere rapidamente e facilmente a Surface Hub senza dover digitare nomi utente e password. In combinazione con Single Sign-On (SSO), questa funzionalità offre un'autenticazione rapida e semplice per file, app e siti Web durante una riunione. Per altre informazioni, vedi [Configurare l'accesso senza password in Surface Hub.](https://docs.microsoft.com/surface-hub/surface-hub-2s-phone-authenticate)
- **Miglioramenti all'accesso senza password con Microsoft Authenticator**.  Per le organizzazioni che usano Azure AD, gli utenti possono usare l'app Microsoft Authenticator per accedere senza dover digitare nomi utente e password. Inoltre, gli utenti possono accedere usando gli alias di posta elettronica preferiti in Azure AD oltre al nome dell'entità utente (UPN). Per altre informazioni, vedi [Accedere a Surface Hub con Microsoft Authenticator.](https://docs.microsoft.com/surface-hub/surface-hub-authenticator-app)


## <a name="learn-more"></a>Altre informazioni

- [Aggiornamento all'implementazione di Windows 10 Team](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/update-to-the-windows-10-team-rollout/ba-p/1669655)
- [Installare l'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update.md)  
 
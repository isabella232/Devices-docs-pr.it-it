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
ms.date: 10/19/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 3b9dbf0e4b7412967c3f2c68ddc10a6fccac8907
ms.sourcegitcommit: 4012a9499f658799197fedc7ea1a0c35d6127ed5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2021
ms.locfileid: "12101223"
---
# <a name="whats-new-in-windows-10-team-2020-update"></a>Novità dell'aggiornamento 2020 di Windows 10 Team

Windows 10 Team 2020 Update apporta miglioramenti principali alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità Windows 10 più recenti.

## <a name="deployment-and-manageability"></a>Distribuzione e gestibilità

- **Autenticazione moderna per gli account dei dispositivi cloud**. Surface Hub supporta l'autenticazione basata su Exchange Web Services (EWS) e Active Directory Authentication Library (ADAL) per connettersi a Exchange, consentendo ai clienti di deprecato l'utilizzo dell'autenticazione di base. Per ulteriori informazioni, vedere [Autenticazione moderna in Surface Hub](surface-hub-modern-auth.md).
- **Più di 20 impostazioni dei criteri**di gestione dei dispositivi mobili (MDM) nuove e aggiornate.  Queste impostazioni dei criteri offrono agli amministratori IT un controllo migliorato su più impostazioni del dispositivo, tra cui: aggiornamenti delle app dal Microsoft Store, impostazioni di proiezione wireless come Miracast sull'infrastruttura, impostazioni di rete come qualità del servizio e autenticazione cablata 802.1x e nuove impostazioni correlate a privacy/GDPR. I nuovi provider di servizi di configurazione includono: 

  - [CSP account](/windows/client-management/mdm/accounts-csp) 
  - [Firewall-CSP](/windows/client-management/mdm/firewall-csp) 
  - [CSP RemoteWipe](/windows/client-management/mdm/remotewipe-csp) 
  - [Wifi-CSP](/windows/client-management/mdm/wifi-csp) 
  - [Wirednetwork-CSP](/windows/client-management/mdm/wirednetwork-csp) 

Per ulteriori informazioni, vedere: 
- [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md)

## <a name="azure-active-directory-joined-devices"></a>Azure Active Directory Dispositivi aggiunti

- **Single #A0 (SSO) per i Azure AD aggiunti.** Quando gli utenti acorrono con le credenziali Microsoft 365 "Riunioni e file personali", le credenziali utente fluire senza problemi da un'app all'altra, incluse le esperienze Microsoft 365 nel browser.
- **Accesso condizionale (CA) per Azure AD aggiunti a dispositivi**. Gli amministratori IT possono controllare l'accesso degli utenti alle risorse dell'organizzazione da Azure AD aggiunti a Surface Hub assegnando criteri di dispositivo in base ai requisiti di sicurezza e conformità aziendali.
- **Supporto per gli amministratori non globali per i Azure AD aggiunti.** I clienti possono scegliere un set più granulare di amministratori all'interno della gerarchia di amministrazione per gestire i Surface Hub. Per ulteriori informazioni, vedere [Configure non Global admin accounts on Surface Hub](surface-hub-2s-nonglobal-admin.md).

## <a name="browser-and-pen"></a>Browser e penna

- **Nuovo Microsoft Edge installato per impostazione predefinita**. Microsoft Edge è stato ricostruito per garantire prestazioni ottimali di compatibilità, sicurezza e privacy. Per ulteriori informazioni, vedere [Manage Microsoft Edge on Surface Hub](surface-hub-install-chromium-edge.md).
- **Input penna doppia su Surface Hub 2S**.   Gli utenti possono lavagna e collaborare affiancati su Surface Hub 2S usando due Surface Hub 2 penne. Gli aggiornamenti del firmware necessari per abilitare l'input penna doppia verranno rilasciati con un aggiornamento successivo.

## <a name="microsoft-teams"></a>Microsoft Teams  

- **Microsoft Teams installato per impostazione predefinita**.        Microsoft Teams è inclusa come app riunioni, chiamate e collaborazione predefinita nei nuovi dispositivi Surface Hub che possono essere modificati o configurati tramite MDM o direttamente su Surface Hub usando l'app Impostazioni. Per ulteriori informazioni, vedere [[Deploy Microsoft Teams](/MicrosoftTeams/teams-surface-hub).
- **Supporto per l'aggiunta di prossimità con Microsoft Teams**.  L'aggiunta di prossimità consente agli utenti di effettuare chiamate Microsoft Teams pianificate su un Surface Hub nelle vicinanze usando il portatile o il telefono oppure di eseguire senza problemi la transizione di una riunione in corso a una riunione Surface Hub. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dispositivi mobili (MDM) per configurare l'aggiunta di prossimità. Per ulteriori informazioni, vedere: 

  - [Microsoft Teams Blog](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833). 
  - [Gestire le impostazioni di Microsoft Teams in Surface Hub](/MicrosoftTeams/rooms/surface-hub-manage-config)

- **Supporto per riunioni coordinate con Microsoft Teams**. Nelle sale riunioni che presentano un Surface Hub e un dispositivo sala Microsoft Teams o spazi con due dispositivi Surface Hub, le riunioni coordinate consentono agli utenti di sfruttare facilmente entrambi i dispositivi durante una riunione Microsoft Teams. Con un singolo tocco, gli utenti possono partecipare a una riunione da entrambi i dispositivi e ottimizzare lo spazio sullo schermo mostrando feed video su un dispositivo e una lavagna digitale o contenuto sull'altro. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dispositivi mobili (MDM) per configurare le riunioni coordinate e la funzionalità verrà successivamente rilasciata come aggiornamento Microsoft Teams tramite Microsoft Store. Per ulteriori informazioni, vedere [Set up Coordinated Meetings with Microsoft Teams Rooms and Surface Hub](/MicrosoftTeams/rooms/coordinated-meetings).

## <a name="security"></a>Sicurezza

- **Accesso senza password con chiavi di sicurezza FIDO2**     Usando le chiavi di sicurezza FIDO2, i clienti possono accedere rapidamente e facilmente Surface Hub senza dover digitare nomi utente e password. In combinazione con Single Sign-On (SSO), questa funzionalità offre un'autenticazione rapida e semplice per file, app e siti Web durante una riunione. Per ulteriori informazioni, vedere [Configure passwordless sign-in on Surface Hub](surface-hub-2s-phone-authenticate.md).
- **Miglioramenti all'accesso senza**password tramite Microsoft Authenticator .  Per le organizzazioni che usano Azure AD, gli utenti possono usare l'app Microsoft Authenticator per accedere senza dover digitare nomi utente e password. Inoltre, gli utenti possono accedere usando gli alias di posta elettronica preferiti in Azure AD oltre al nome dell'entità utente (UPN). Per ulteriori informazioni, vedere [Sign in to Surface Hub with Microsoft Authenticator](surface-hub-authenticator-app.md).

## <a name="learn-more"></a>Scopri di più

- [Windows 10 Team 2020 Update 1 rilasciato a tutti i Surface Hub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/windows-10-team-2020-update-1-released-to-all-surface-hubs/ba-p/2653503)
- [Installare l'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update.md)  
 
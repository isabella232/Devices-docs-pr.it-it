---
title: Novità degli aggiornamenti Windows 10 Team 2020
description: Scopri le novità dell'aggiornamento più recente del sistema operativo Surface Hub, Windows 10 Team 2020 Update.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/15/2022
ms.localizationpriority: Medium
ms.openlocfilehash: c44ec68a39158910c841375aeda0a6d6bf11635f
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448269"
---
# <a name="whats-new-in-windows-10-team-2020-updates"></a>Novità degli aggiornamenti Windows 10 Team 2020

Surface Hub gli aggiornamenti periodici che offrono nuove funzionalità e funzionalità. L'aggiornamento 2020 da 20H2 a Windows 10 Team e successivamente l'aggiornamento 1 & update 2 offrono miglioramenti significativi alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità Windows 10 più recenti.

## <a name="windows-10-team-2020-update-2"></a>Windows 10 Team 2020 Update 2 

### <a name="gcc-high-support"></a>GCC Supporto elevato

Dopo l'installazione di questo aggiornamento ([KB5010415](https://support.microsoft.com/help/5010415) o una versione successiva di Windows CU), i dispositivi Surface Hub sono supportati in ambienti GCC high. In questo momento, [sono necessari ulteriori ](surface-hub-teams-rooms.md#support-for-teams-rooms-in-government-community-cloud-high-gcc-h) passaggi per il client Teams Rooms per connettersi correttamente GCC tenant elevati.

### <a name="ease-of-access-updates"></a>Aggiornamenti della facilità di accesso

Gli utenti possono modificare le impostazioni di accessibilità durante una sessione Surface Hub e chiudere le app come in altre versioni di Windows 10. 

- **Accessibilità**. Gli utenti possono modificare le impostazioni seguenti senza effettuare l'accesso: Schermo, Cursore testo, Lente di ingrandimento, Contrasto elevato, Assistente vocale, Sottotitoli codificati e Tastiera. 
- **Interfaccia utente familiare per le app**. Gli utenti possono chiudere le app Surface Hub selezionando il pulsante Chiudi nell'angolo in alto a destra dell'app. In questo modo viene rimossa la necessità di chiudere le app trascinandole nella parte inferiore Surface Hub schermo. Nota: questa funzionalità sarà disponibile nel browser Edge come parte del prossimo aggiornamento edge, pianificato per marzo 2022. 

Per ulteriori informazioni, vedere [Adjust Ease of Access settings on Surface Hub](accessibility-surface-hub.md).

### <a name="administrator-updates"></a>Aggiornamenti dell'amministratore

- **Visualizzatore eventi**. Gli amministratori possono accedere al Visualizzatore Windows eventi direttamente dall'app Impostazioni app. 
- **Nuove impostazioni dei criteri di gestione dei dispositivi mobili (MDM**). I nuovi provider di servizi di configurazione includono:

  - [TimeLanguageSettings-CSP](/windows/client-management/mdm/policy-csp-timelanguagesettings)
  - [LocalUsersAndGroups-CSP](/windows/client-management/mdm/policy-csp-localusersandgroups) 

Per ulteriori informazioni, vedere [Configure non Global admin accounts on Surface Hub](surface-hub-2s-nonglobal-admin.md).


## <a name="windows-10-team-2020-update-1"></a>Windows 10 Team 2020 Update 1

### <a name="support-for-new-teams-rooms-application"></a>Supporto per la nuova Teams Rooms applicazione

Dopo l'installazione di questo aggiornamento ([KB5005101](https://support.microsoft.com/help/5005101) o un aggiornamento cumulativo Windows successivo), Surface Hub supporta un aggiornamento automatico al nuovo [client Teams Rooms](surface-hub-teams-rooms.md) tramite Windows Update.

### <a name="support-for-new-whiteboard-application"></a>Supporto per la nuova applicazione Lavagna

Dopo l'installazione di questo aggiornamento, Surface Hubs supporta un aggiornamento automatico (se disponibile) alla nuova [app Lavagna](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/unified-whiteboard-experience-coming-to-surface-hub/ba-p/3145226) tramite Microsoft Store aggiornamenti.

### <a name="new-microsoft-edge-browser-installed-by-default"></a>Nuovo Microsoft Edge browser installato per impostazione predefinita

Dopo l'installazione di questo aggiornamento, i dispositivi Surface Hub sostituiranno automaticamente il browser Versione legacy di Microsoft Edge con il nuovo browser Edge Chromium basato su Chromium.  Per ulteriori informazioni, vedere [Manage Microsoft Edge on Surface Hub](surface-hub-install-chromium-edge.md). Edge Legacy non è più disponibile in Windows 10 Team dopo l'installazione di questo aggiornamento o una successiva Windows CU.


## <a name="windows-10-team-2020-update-20h2"></a>Windows 10 Team 2020 Update (20H2)

### <a name="deployment-and-manageability"></a>Distribuzione e gestibilità

- **Autenticazione moderna per gli account dei dispositivi cloud**. Surface Hub supporta l'autenticazione basata su Exchange Web Services (EWS) e Active Directory Authentication Library (ADAL) per connettersi a Exchange, consentendo ai clienti di deprecato l'utilizzo dell'autenticazione di base. Per ulteriori informazioni, vedere [Autenticazione moderna Surface Hub](surface-hub-modern-auth.md).
- **Più di 20 impostazioni dei criteri MDM nuove e aggiornate**.  Queste impostazioni dei criteri offrono agli amministratori IT un controllo migliorato su più impostazioni del dispositivo, inclusi gli aggiornamenti delle app dal Microsoft Store, le impostazioni di proiezione wireless come Miracast sull'infrastruttura, le impostazioni di rete come qualità del servizio e autenticazione cablata 802.1x e nuove impostazioni correlate a privacy/GDPR. I nuovi CSP includono:

  - [CSP account](/windows/client-management/mdm/accounts-csp)
  - [Firewall-CSP](/windows/client-management/mdm/firewall-csp)
  - [CSP RemoteWipe](/windows/client-management/mdm/remotewipe-csp)
  - [Wifi-CSP](/windows/client-management/mdm/wifi-csp)
  - [Wirednetwork-CSP](/windows/client-management/mdm/wirednetwork-csp)

Per ulteriori informazioni, vedere:

- [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md)

### <a name="azure-active-directory-joined-devices"></a>Azure Active Directory aggiunti

- **Single #A0 (SSO) per i Azure AD aggiunti**. Quando gli utenti acorrono con le credenziali Microsoft 365 le riunioni personali **** e i file le loro credenziali fluire senza problemi da un'app all'altra, incluse le esperienze Microsoft 365 nel browser.
- **Accesso condizionale (CA) per i Azure AD aggiunti**. Gli amministratori IT possono controllare l'accesso degli utenti alle risorse dell'organizzazione Azure AD aggiunti a Surface Hub assegnando criteri di dispositivo in base ai requisiti di sicurezza e conformità aziendali.
- **Supporto per gli amministratori non globali per Azure AD aggiunti**. I clienti possono scegliere un set più granulare di amministratori all'interno della gerarchia di amministrazione per gestire i Surface Hub. Per ulteriori informazioni, vedere [Configure non Global admin accounts on Surface Hub](surface-hub-2s-nonglobal-admin.md).

### <a name="inking-improvements"></a>Miglioramenti dell'input penna

- **Supporto per l'input penna doppia Surface Hub 2S**.  Usa la lavagna e collabora affiancata in Surface Hub 2S con due Surface Hub 2 penne. Qualsiasi aggiornamento hardware di sistema installato dopo l'aggiornamento a Windows 10 Team 2020 aggiungerà il supporto del firmware per questo scenario.

### <a name="microsoft-teams"></a>Microsoft Teams  

- **Microsoft Teams installato per impostazione predefinita**. Microsoft Teams è incluso come app predefinita per riunioni, chiamate e collaborazione su nuovi dispositivi Surface Hub, che possono essere modificati o configurati tramite MDM o direttamente su Surface Hub usando l'app Impostazioni. Per ulteriori informazioni, vedere [Deploy Microsoft Teams](/MicrosoftTeams/teams-surface-hub).
- **Supporto per l'aggiunta di prossimità con Microsoft Teams**.  L'aggiunta di prossimità consente agli utenti di effettuare Microsoft Teams chiamate pianificate su un Surface Hub vicino usando il portatile o il telefono.  Consente inoltre agli utenti di eseguire la transizione di una riunione in corso a una riunione Surface Hub. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dispositivi mobili (MDM) per configurare l'aggiunta di prossimità. Per ulteriori informazioni, vedere:

  - [Microsoft Teams Blog](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833).
  - [Gestire le impostazioni di Microsoft Teams in Surface Hub](/MicrosoftTeams/rooms/surface-hub-manage-config)

- **Supporto per riunioni coordinate con Microsoft Teams**. Nelle sale riunioni che presentano un Surface Hub e un dispositivo sala Microsoft Teams o spazi con due dispositivi Surface Hub, le riunioni coordinate consentono agli utenti di sfruttare rapidamente entrambi i dispositivi durante una riunione Microsoft Teams. Gli utenti possono partecipare a una riunione da entrambi i dispositivi con un solo tocco e ottimizzare lo spazio sullo schermo mostrando feed video su un dispositivo e una lavagna digitale o contenuto sull'altro. Windows 10 Team 2020 Update aggiunge il supporto di Gestione dispositivi mobili (MDM) per configurare le riunioni coordinate e la funzionalità verrà successivamente rilasciata come aggiornamento Microsoft Teams tramite Microsoft Store. Per ulteriori informazioni, vedere [Set up Coordinated Meetings with Microsoft Teams Rooms and Surface Hub](/MicrosoftTeams/rooms/coordinated-meetings).

### <a name="security"></a>Sicurezza

- **Accesso senza password con chiavi di sicurezza FIDO2** Con le chiavi di sicurezza FIDO2, gli utenti possono accedere rapidamente a Surface Hub senza digitare nomi utente e password. In combinazione con Single Sign-On (SSO), questa funzionalità offre un'autenticazione rapida e semplice per file, app e siti Web durante una riunione. Per ulteriori informazioni, vedere [Configure passwordless sign-in on Surface Hub](surface-hub-2s-phone-authenticate.md).
- **Miglioramenti all'accesso senza password con Microsoft Authenticator**.  Per le organizzazioni che usano Azure AD, gli utenti possono accedere con l Microsoft Authenticator app. Inoltre, gli utenti possono accedere con gli alias di posta elettronica preferiti in Azure AD e con il nome dell'entità utente (UPN). Per ulteriori informazioni, vedere [Sign in to Surface Hub with Microsoft Authenticator](surface-hub-authenticator-app.md).

## <a name="learn-more"></a>Scopri di più

- [Windows 10 Team 2020 Update 1 rilasciato a tutti i surface hub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/windows-10-team-2020-update-1-released-to-all-surface-hubs/ba-p/2653503)
- [Windows 10 Team 2020 Aggiornamento disponibile il 27 ottobre](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-available-october-27/ba-p/1810739)
- [Installare l'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update.md)

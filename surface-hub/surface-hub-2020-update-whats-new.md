---
title: Novità degli aggiornamenti di Windows 10 Team 2020
description: Vedere le novità dell'aggiornamento più recente del sistema operativo Surface Hub Windows 10 Team aggiornamento 2020.
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
ms.openlocfilehash: 995766eb216051de270a387c15c96ee42dd008a3
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497959"
---
# <a name="whats-new-in-windows-10-team-2020-updates"></a>Novità degli aggiornamenti di Windows 10 Team 2020

Surface Hub vantaggi degli aggiornamenti periodici che offrono nuove funzionalità e funzionalità. L'aggiornamento 2020 (20H2) per Windows 10 Team e successivamente l'aggiornamento 1 & Update 2, offre miglioramenti significativi alla distribuzione e alla gestibilità dei dispositivi insieme alle funzionalità di Windows più recenti.

## <a name="windows-10-team-2020-update-2"></a>Windows 10 Team 2020 Update 2 

### <a name="gcc-high-support"></a>supporto elevato GCC

Dopo l'installazione di questo aggiornamento ([KB5010415](https://support.microsoft.com/help/5010415) o una cu Windows successiva), surface hub sono supportati in ambienti GCC high. In questo momento, sono necessari [passaggi aggiuntivi ](surface-hub-teams-rooms.md#support-for-teams-rooms-in-government-community-cloud-high-gcc-h) per consentire al client Teams Rooms di connettersi correttamente ai tenant GCC high.

### <a name="support-for-surface-hub-2-smart-camera"></a>Supporto per Surface Hub 2 Smart Camera

La smart camera Surface Hub 2 basata su intelligenza artificiale è ottimizzata per i team ibridi che consentono ai partecipanti remoti di vedere le persone interagire con i contenuti nella Surface Hub, visualizzando anche tutti gli altri utenti nella stanza.  Per altre informazioni, vedere [Installare e gestire Surface Hub 2 Smart Camera](surface-hub-2-smart-camera.md). 

### <a name="support-for-progressive-web-apps-pwas"></a>Supporto per i App Web progressivi (PWA)

Gli amministratori possono installare i PWA in remoto in Surface Hub usando un provider di gestione di dispositivi mobili (MDM) che applica un pacchetto di provisioning. Per altre informazioni, vedere [Installare App Web progressive in Surface Hub](install-pwa-surface-hub.md). 

### <a name="ease-of-access-updates"></a>Aggiornamenti di Facilità di accesso

Gli utenti possono modificare le impostazioni di Accessibilità durante una sessione di Surface Hub e chiudere le app proprio come in altre versioni di Windows 10 o Windows 11. 

- **Facilità di accesso**. Gli utenti possono modificare le impostazioni seguenti senza accedere: Display, Text cursor, Magnifier, High Contrast, Narrator, Closed captions e Keyboard. 
- **Interfaccia utente familiare per le app**. Gli utenti possono chiudere le app in Surface Hub selezionando il pulsante Chiudi nell'angolo in alto a destra dell'app. In questo modo viene rimossa la necessità di chiudere le app trascinandole nella parte inferiore della visualizzazione Surface Hub. Nota: questa funzionalità sarà disponibile nel browser Edge come parte del prossimo aggiornamento edge, pianificato per marzo 2022. 

Per altre informazioni, vedere [Modificare le impostazioni di accessibilità in Surface Hub](accessibility-surface-hub.md).

### <a name="administrator-updates"></a>Aggiornamenti dell'amministratore

- **Visualizzatore eventi**. Gli amministratori possono accedere al Windows Visualizzatore eventi direttamente dall'app Impostazioni. 
- **Nuove impostazioni dei criteri di gestione dei dispositivi mobili (MDM**). I nuovi provider di servizi di configurazione (CSP) includono:

  - [TimeLanguageSettings-CSP](/windows/client-management/mdm/policy-csp-timelanguagesettings)
  - [LocalUsersAndGroups-CSP](/windows/client-management/mdm/policy-csp-localusersandgroups) 

Per altre informazioni, vedere [Configurare gli account di amministrazione non globali in Surface Hub](surface-hub-2s-nonglobal-admin.md).


## <a name="windows-10-team-2020-update-1"></a>Windows 10 Team 2020 Update 1

### <a name="support-for-new-teams-rooms-application"></a>Supporto per la nuova applicazione Teams Rooms

Dopo l'installazione di questo aggiornamento ([KB5005101](https://support.microsoft.com/help/5005101) o una cu Windows successiva), Surface Hubs supporta un aggiornamento automatico al nuovo [client Teams Rooms](surface-hub-teams-rooms.md) tramite Windows Update.

### <a name="support-for-new-whiteboard-application"></a>Supporto per la nuova applicazione Whiteboard

Dopo l'installazione di questo aggiornamento, Surface Hubs supporta un aggiornamento automatico (se disponibile) alla nuova [app Whiteboard](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/unified-whiteboard-experience-coming-to-surface-hub/ba-p/3145226) tramite gli aggiornamenti Microsoft Store.

### <a name="new-microsoft-edge-browser-installed-by-default"></a>Nuovo browser Microsoft Edge installato per impostazione predefinita

Dopo l'installazione di questo aggiornamento, Surface Hubs sostituirà automaticamente il browser Versione legacy di Microsoft Edge con il nuovo browser Edge basato su Chromium.  Per altre informazioni, vedere [Gestire Microsoft Edge in Surface Hub](surface-hub-install-chromium-edge.md). Edge Legacy non è più disponibile in Windows 10 Team dopo l'installazione di questo aggiornamento o di una versione successiva Windows CU.


## <a name="windows-10-team-2020-update-20h2"></a>Windows 10 Team 2020 Update (20H2)

### <a name="deployment-and-manageability"></a>Distribuzione e gestibilità

- **Autenticazione moderna per gli account del dispositivo cloud**. Surface Hub supporta l'autenticazione basata su servizi Web Exchange (EWS) e Active Directory Authentication Library (ADAL) per connettersi a Exchange, consentendo ai clienti di deprecato l'uso dell'autenticazione di base. Per altre informazioni, vedere [Autenticazione moderna in Surface Hub](surface-hub-modern-auth.md).
- **Più di 20 impostazioni dei criteri MDM nuove e aggiornate**.  Queste impostazioni dei criteri offrono agli amministratori IT un controllo migliorato su più impostazioni del dispositivo, inclusi gli aggiornamenti delle app dal Microsoft Store, le impostazioni di proiezione wireless, ad esempio Miracast sull'infrastruttura, le impostazioni di rete come Quality-Of-Service e l'autenticazione cablata 802.1x e le nuove impostazioni correlate alla privacy/GDPR. I nuovi CSP includono:

  - [CSP account](/windows/client-management/mdm/accounts-csp)
  - [Firewall-CSP](/windows/client-management/mdm/firewall-csp)
  - [CSP RemoteWipe](/windows/client-management/mdm/remotewipe-csp)
  - [Wifi-CSP](/windows/client-management/mdm/wifi-csp)
  - [Wirednetwork-CSP](/windows/client-management/mdm/wirednetwork-csp)

Per altre informazioni, vedere:

- [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md)

### <a name="azure-active-directory-joined-devices"></a>Azure Active Directory dispositivi aggiunti

- **Single Sign-On (SSO) per Azure AD dispositivi aggiunti**. Quando gli utenti accedono con le proprie credenziali di Microsoft 365 a **Riunioni e file** personali, le credenziali passano facilmente dall'app all'app, incluse le esperienze Microsoft 365 nel browser.
- **Accesso condizionale (CA) per Azure AD dispositivi aggiunti**. Gli amministratori IT possono controllare l'accesso degli utenti alle risorse dell'organizzazione da Azure AD surface hub aggiunti assegnando i criteri dei dispositivi in base ai requisiti di sicurezza e conformità aziendali.
- **Supporto per amministratori non globali per Azure AD dispositivi aggiunti**. I clienti possono scegliere un set più granulare di amministratori all'interno della gerarchia di amministrazione per gestire Surface Hub. Per altre informazioni, vedere [Configurare gli account di amministrazione non globali in Surface Hub](surface-hub-2s-nonglobal-admin.md).

### <a name="inking-improvements"></a>Miglioramenti dell'input penna

- **Supporto per l'input penna a doppia penna su Surface Hub 2S**.  Usare la lavagna e collaborare side-by-side su Surface Hub 2S con due Surface Hub 2 penne. Qualsiasi aggiornamento hardware di sistema installato dopo l'aggiornamento a Windows 10 Team 2020 aggiungerà il supporto del firmware per questo scenario.

### <a name="microsoft-teams"></a>Microsoft Teams  

- **Microsoft Teams installato per impostazione predefinita**. Microsoft Teams è l'app predefinita per riunioni, chiamate e collaborazione su nuovi dispositivi Surface Hub, che può essere modificata o configurata tramite MDM o direttamente in Surface Hub usando l'app Impostazioni. Per altre informazioni, vedere [Distribuire Microsoft Teams](/MicrosoftTeams/teams-surface-hub).
- **Supporto per l'aggiunta di prossimità con Microsoft Teams**.  L'aggiunta di prossimità consente agli utenti di effettuare chiamate Microsoft Teams pianificate su un Surface Hub nelle vicinanze usando il portatile o il telefono.  Consente inoltre agli utenti di eseguire la transizione di una riunione in corso a un Surface Hub nelle vicinanze. Windows 10 Team aggiornamento 2020 aggiunge il supporto di Mobile Gestione dispositivi (MDM) per configurare l'aggiunta di prossimità. Per altre informazioni, vedere:

  - [Microsoft Teams Blog](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/microsoft-teams-devices-for-shared-spaces-july-and-august-update/ba-p/1604833).
  - [Gestire le impostazioni di Microsoft Teams in Surface Hub](/MicrosoftTeams/rooms/surface-hub-manage-config)

- **Supporto per riunioni coordinate con Microsoft Teams**. Nelle sale riunioni con un Surface Hub e un dispositivo Microsoft Teams Room o spazi con due dispositivi Surface Hub, le riunioni coordinate consentono agli utenti di sfruttare rapidamente entrambi i dispositivi durante una riunione Microsoft Teams. Gli utenti possono partecipare a una riunione da entrambi i dispositivi con un solo tocco e ottimizzare la proprietà dello schermo visualizzando i feed video su un dispositivo e una lavagna digitale o contenuti sull'altro. Windows 10 Team aggiornamento 2020 aggiunge il supporto di Mobile Gestione dispositivi (MDM) per configurare le riunioni coordinate e la funzionalità verrà rilasciata successivamente come aggiornamento Microsoft Teams tramite Microsoft Store. Per altre informazioni, vedere [Configurare riunioni coordinate con Microsoft Teams Rooms e Surface Hub](/MicrosoftTeams/rooms/coordinated-meetings).

### <a name="security"></a>Sicurezza

- **Accesso senza password tramite chiavi di sicurezza FIDO2** Con le chiavi di sicurezza FIDO2, gli utenti possono accedere rapidamente a Surface Hub senza digitare nomi utente e password. In combinazione con Single Sign-On (SSO), questa funzionalità offre un'autenticazione rapida e semplice a file, app e siti Web durante una riunione. Per altre informazioni, vedere [Configurare l'accesso senza password Surface Hub](surface-hub-2s-phone-authenticate.md).
- **Miglioramenti all'accesso senza password tramite Microsoft Authenticator**.  Per le organizzazioni che usano Azure AD, gli utenti possono accedere con l'app Microsoft Authenticator. Inoltre, gli utenti possono accedere con gli alias di posta elettronica preferiti in Azure AD o il nome dell'entità utente (UPN). Per altre informazioni, vedere [Accedere a Surface Hub con Microsoft Authenticator](surface-hub-authenticator-app.md).

## <a name="learn-more"></a>Scopri di più

- [Windows 10 Team 2020 Update 1 rilasciato a tutti i surface hub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/windows-10-team-2020-update-1-released-to-all-surface-hubs/ba-p/2653503)
- [aggiornamento Windows 10 Team 2020 disponibile il 27 ottobre](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/surface-hub-windows-10-team-2020-update-available-october-27/ba-p/1810739)
- [Installare l'aggiornamento 2020 di Windows 10 Team](surface-hub-2020-update.md)

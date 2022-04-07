---
title: Creare e testare un account del dispositivo (Surface Hub)
description: Questo argomento spiega come creare e testare l'account del dispositivo che Microsoft Surface Hub usa per comunicare con Microsoft Exchange e Skype.
ms.assetid: C8605B5F-2178-4C3A-B4E0-CE32C70ECF67
ms.reviewer: rikot
manager: laurawi
keywords: creare e testare l'account del dispositivo, account del dispositivo, Surface Hub e Microsoft Exchange, Surface Hub e Skype
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/01/2021
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: c925cb952c7fd04a86d824dfba99a373c07b313e
ms.sourcegitcommit: b922aaf7287bdfb99f848aad455b2b4001b8f5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2022
ms.locfileid: "12472625"
---
# <a name="create-and-test-a-device-account-surface-hub"></a>Creare e testare un account del dispositivo (Surface Hub)

La creazione di un account del dispositivo Surface Hub (noto anche come account della risorsa/cassetta postale della sala) consente al Surface Hub di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni.

Dopo aver effettuato il provisioning dell'account del dispositivo in un Surface Hub, gli utenti possono aggiungere questo account a un invito alla riunione nello stesso modo in cui invitano una sala conferenze. 

È possibile configurare l'account del dispositivo durante [l'installazione di Configurazione](first-run-program-surface-hub.md) guidata. Se necessario, è anche possibile modificarlo più avanti in **Impostazioni** >  **Surface Hub** >  **Accounts**.

## <a name="configuration-overview"></a>Panoramica della configurazione

Questa tabella descrive i passaggi principali e le decisioni di configurazione per la creazione di un account del dispositivo.
 
| Passaggio | Descrizione                     |  Scopo                             |
|------|---------------------------------|--------------------------------------|
| 1    | Creare una cassetta postale della sala abilitata per l'accesso (Exchange Online o Exchange Server 2016 e versioni successive) | Questo tipo di cassetta postale consente al dispositivo di gestire un calendario riunioni, ricevere convocazioni di riunione e inviare messaggi di posta elettronica. Deve essere abilitato per l'accesso per poter essere usato con un Surface Hub. |
| 2    | Configurare le proprietà della cassetta postale | La cassetta postale deve essere configurata con le proprietà corrette per assicurare la migliore esperienza per le riunioni nel dispositivo Surface Hub. Per altre informazioni sulle proprietà della cassetta postale, vedi l'argomento relativo alle [proprietà della cassetta postale](exchange-properties-for-surface-hub-device-accounts.md). |
| 3    | Assicurarsi che Exchange Web Services (EWS) sia abilitato e che l'autenticazione a più fattori (MFA) sia disabilitata | Il Surface Hub usa EWS per sincronizzare il calendario. Se non si consente EWS nell'ambiente per impostazione predefinita, la cassetta postale dell'hub deve essere abilitata in modo esplicito. Poiché il Surface Hub accede a Exchange in background senza l'interazione dell'utente, non può rispondere a richieste interattive, ad esempio MFA. L'account del dispositivo creato deve essere escluso da tali requisiti di autenticazione. In caso contrario, Surface Hub non sarà in grado di sincronizzare le informazioni della posta e del calendario. |
| 4    | Abilitare l'account per Teams o Skype for Business (Skype for Business Server 2015 e versioni successive) | Skype for Business o Teams devono essere abilitate per l'uso di funzionalità di conferenza, ad esempio videochiamate e condivisione dello schermo. Per altre informazioni sulle licenze che consentono Teams, vedere [Teams Sala riunioni licenze](/MicrosoftTeams/rooms/rooms-licensing) e [Teams descrizione del servizio](/office365/servicedescriptions/teams-service-description). Le applicazioni Teams e SfB nel Surface Hub non sono compatibili con [Azure AD criteri di accesso condizionale](/azure/active-directory/conditional-access/concept-conditional-access-policies) che richiedono informazioni sul dispositivo (ad esempio la conformità). L'account del dispositivo creato deve essere escluso da tali criteri ca. In caso contrario, Surface Hub non è in grado di usare alcuna funzionalità di conferenza. |
| 5    | (Facoltativo) Disabilitare la scadenza delle password | Per semplificare la gestione, puoi disattivare la scadenza delle password per l'account del dispositivo e consentire al dispositivo Surface Hub di ruotare automaticamente la password per l'account del dispositivo. Per altre informazioni sulla gestione delle password, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).  |

> [!NOTE]  
> L'account del dispositivo Surface Hub non supporta provider di identità federati di terze parti e deve eseguire l'autenticazione tramite Active Directory o Azure Active Directory.

## <a name="detailed-configuration-steps"></a>Passaggi di configurazione dettagliati 

I passaggi di configurazione dell'account del dispositivo possono variare in base all'ambiente. Selezionare lo scenario di distribuzione nella tabella seguente per trovare i passaggi appropriati e prendere nota della colonna "Formato da usare" per la configurazione di Surface Hub dopo il provisioning degli account.

| Distribuzione dell'organizzazione             |  Descrizione                  |        Formato da usare durante l'installazione di Surface Hub
|---------------------------------|--------------------------------------|
| [Distribuzione online (Microsoft 365)](/MicrosoftTeams/rooms/with-office-365?tabs=m365-admin-center) |L'ambiente dell'organizzazione viene distribuito interamente in Microsoft 365. | nomeutente@dominio.com |
| [Distribuzione ibrida (Exchange locale)](/MicrosoftTeams/rooms/with-office-365?tabs=exchange-server) | L'organizzazione offre una combinazione di servizi, con Exchange Server ospitati in locale e Microsoft Teams online. | username@domain.com se [l'autenticazione moderna ibrida](/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication) è abilitata in Exchange, DOMINIO\nomeutente in caso contrario |
| [Distribuzione ibrida (Exchange Online)](/skypeforbusiness/deploy/deploy-clients/hybrid-deployments) | L'organizzazione offre una combinazione di servizi, con Skype for Business Server ospitati in locale e Exchange Online. | username@domain.com se [l'autenticazione moderna ibrida](/microsoft-365/enterprise/configure-skype-for-business-for-hybrid-modern-authentication) è abilitata in SfB, DOMINIO\nomeutente in caso contrario |
| [Distribuzione locale (singola foresta)](/skypeforbusiness/deploy/deploy-clients/single-forest-on-premises-deployments) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a foresta singola.  | DOMINIO\nomeutente |
| [Distribuzione locale (più foreste)](/skypeforbusiness/deploy/deploy-clients/multiple-forest-on-premises-deployments) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a più foreste. | ACCOUNTFOREST\username |

Per le distribuzioni online, è disponibile anche una [distribuzione guidata per gli amministratori Microsoft 365](https://admin.microsoft.com/Adminportal/Home#/modernonboarding/surfacehubsetupguide) direttamente nell'interfaccia di amministrazione di M365. Questa procedura guidata consente di creare nuovi account del dispositivo o convalidare gli account di risorse esistenti disponibili per trasformarli in account di dispositivo Surface Hub compatibili.

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
ms.openlocfilehash: 685359f1371a1bef8bd216223a98b934c997a1d8
ms.sourcegitcommit: 879e80200aea26f6705c887fa392db5db35b99ed
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/03/2021
ms.locfileid: "11475090"
---
# <a name="create-and-test-a-device-account-surface-hub"></a>Creare e testare un account del dispositivo (Surface Hub)

La creazione di un account del dispositivo Surface Hub (noto anche come account risorsa/cassetta postale sala) consente a Surface Hub di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni.

Dopo aver effettuato il provisioning dell'account del dispositivo in un dispositivo Surface Hub, gli utenti possono aggiungere questo account a un invito alla riunione nello stesso modo in cui invitano una sala riunioni. 

Puoi configurare l'account del dispositivo [durante l'installazione](first-run-program-surface-hub.md)della Configurazione guidata . Se necessario, puoi anche modificarlo in un secondo momento in **Impostazioni**  >  **Account Surface**  >  **Hub.**

## <a name="configuration-overview"></a>Panoramica della configurazione

Questa tabella descrive i passaggi principali e le decisioni di configurazione per la creazione di un account del dispositivo.
 
| Passaggio | Descrizione                     |  Scopo                             |
|------|---------------------------------|--------------------------------------|
| 1    | Creare una cassetta postale sala abilitata per l'accesso (Exchange Online o Exchange Server 2016 e versioni successive) | Questo tipo di cassetta postale consente al dispositivo di gestire un calendario delle riunioni, ricevere convocazioni di riunione e inviare posta. Deve essere abilitato per l'accesso per poter essere usato con un dispositivo Surface Hub. |
| 2    | Configurare le proprietà della cassetta postale | La cassetta postale deve essere configurata con le proprietà corrette per assicurare la migliore esperienza per le riunioni nel dispositivo Surface Hub. Per altre informazioni sulle proprietà della cassetta postale, vedi l'argomento relativo alle [proprietà della cassetta postale](exchange-properties-for-surface-hub-device-accounts.md). |
| 3    | Verificare che Servizi Web Exchange (EWS) sia abilitato e che l'autenticazione a più fattori (MFA) sia disabilitata | Surface Hub usa EWS per sincronizzare il calendario. Se non si consente EWS nell'ambiente per impostazione predefinita, la cassetta postale hub deve essere abilitata in modo esplicito. Quando Surface Hub accede a Exchange in background senza l'interazione dell'utente, non può rispondere a richieste interattive, ad esempio MFA. L'account del dispositivo creato deve essere escluso da tali requisiti di autenticazione. In caso contrario, Surface Hub non sarà in grado di sincronizzare le informazioni della posta e del calendario. |
| 4    | Abilitare l'account per Teams o Skype for Business (Skype for Business Server 2015 e versioni successive) | Skype for Business o Teams deve essere abilitato per usare funzionalità di conferenza come videochiamate, messaggistica istantanea e condivisione dello schermo. Per ulteriori informazioni sulle licenze che abilitano Teams, vedere Licenze per sale riunioni [di Teams](https://docs.microsoft.com/MicrosoftTeams/rooms/rooms-licensing) e Descrizione del [servizio Teams.](https://docs.microsoft.com/office365/servicedescriptions/teams-service-description) |
| 5    | (Facoltativo) Disabilitare la scadenza delle password | Per semplificare la gestione, puoi disattivare la scadenza delle password per l'account del dispositivo e consentire al dispositivo Surface Hub di ruotare automaticamente la password per l'account del dispositivo. Per altre informazioni sulla gestione delle password, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).  |
| 6    | (Facoltativo) Configurare i criteri di Exchange per consentire ActiveSync | Con alcune distribuzioni locali Exchange Server & Active Directory, ActiveSync verrà usato per sincronizzare la posta dell'account del dispositivo e le informazioni del calendario. Per altre informazioni sui criteri da configurare, vedi [Criteri di ActiveSync per gli account Surface Hub.](apply-activesync-policies-for-surface-hub-device-accounts.md) |

> [!NOTE]  
> L'account del dispositivo Surface Hub non supporta provider di identità federati di terze parti e deve eseguire l'autenticazione tramite Active Directory o Azure Active Directory.

## <a name="detailed-configuration-steps"></a>Passaggi di configurazione dettagliati 

Ti consigliamo di configurare gli account del dispositivo Surface Hub usando i dispositivi Windows PowerShell. Microsoft fornisce [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), uno script che consente di creare nuovi account delle risorse o di convalidare gli account delle risorse esistenti di cui si dispone per poterli trasformare in account del dispositivo Surface Hub compatibili. Se si preferisce, è possibile scegliere un'opzione dalla tabella seguente e seguire i passaggi dettagliati di PowerShell in base alla distribuzione dell'organizzazione.

| Distribuzione dell'organizzazione             |  Descrizione                  |        Formato da usare durante la configurazione di Surface Hub
|---------------------------------|--------------------------------------|
| [Distribuzione online (Microsoft 365 o Office 365)](https://docs.microsoft.com/microsoftteams/rooms/with-office-365) |L'ambiente dell'organizzazione viene distribuito interamente in Microsoft 365 o Office 365. | nomeutente@dominio.com |
| [Distribuzione ibrida (Exchange locale)](https://docs.microsoft.com/microsoftteams/rooms/with-exchange-on-premises) | L'organizzazione dispone di una combinazione di servizi, con Exchange Server ospitati in locale e Microsoft Teams online. | username@domain.com se [l'autenticazione moderna ibrida](https://docs.microsoft.com/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication) è abilitata in Exchange, DOMINIO\nomeutente in caso contrario |
| [Distribuzione ibrida (Exchange Online)](https://docs.microsoft.com/microsoftteams/rooms/with-exchange-online) | L'organizzazione dispone di una combinazione di servizi, con Skype for Business Server ospitato in locale ed Exchange Online. | username@domain.com se [l'autenticazione moderna ibrida](https://docs.microsoft.com/microsoft-365/enterprise/configure-skype-for-business-for-hybrid-modern-authentication) è abilitata in SfB, DOMINIO\nomeutente in caso contrario |
| [Distribuzione locale (singola foresta)](https://docs.microsoft.com/microsoftteams/rooms/with-skype-for-business-server-2015) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a foresta singola.  | DOMINIO\nomeutente |
| [Distribuzione locale (più foreste)](https://docs.microsoft.com/skypeforbusiness/deploy/deploy-clients/multiple-forest-on-premises-deployments) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a più foreste. | ACCOUNTFOREST\username |


## <a name="account-verification-and-testing"></a>Verifica dell'account e test

Sono disponibili due metodi che puoi usare per convalidare e testare un account del dispositivo Surface Hub: [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105) e l'app [Diagnostica hardware Surface Hub.](https://www.microsoft.com/store/apps/9nblggh51f2g) Lo script di provisioning dell'account può convalidare un account del dispositivo creato in precedenza usando PowerShell dal PC. L'app di diagnostica hardware di Surface Hub viene installata in Surface Hub e fornisce un feedback dettagliato sugli errori di accesso e comunicazione. Entrambi gli strumenti sono efficaci per testare gli account del dispositivo appena creati e devono essere usati per garantire una disponibilità ottimale degli account.

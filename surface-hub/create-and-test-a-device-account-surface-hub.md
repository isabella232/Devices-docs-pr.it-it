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
ms.openlocfilehash: 9d2214453c8cb4c8d03f526dd4ac83264d2a16ad
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676380"
---
# <a name="create-and-test-a-device-account-surface-hub"></a>Creare e testare un account del dispositivo (Surface Hub)

La creazione di un account Surface Hub dispositivo (noto anche come account della risorsa/cassetta postale sala) consente al Surface Hub di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni.

Dopo il provisioning dell'account del dispositivo in un Surface Hub, gli utenti possono aggiungere questo account a un invito alla riunione nello stesso modo in cui invitano una sala riunioni. 

Puoi configurare l'account del dispositivo [durante l'installazione](first-run-program-surface-hub.md)della Configurazione guidata . Se necessario, è anche possibile modificarlo in un secondo **momento**in Impostazioni  >  **Surface Hub**  >  **Account**.

## <a name="configuration-overview"></a>Panoramica della configurazione

Questa tabella descrive i passaggi principali e le decisioni di configurazione per la creazione di un account del dispositivo.
 
| Passaggio | Descrizione                     |  Scopo                             |
|------|---------------------------------|--------------------------------------|
| 1    | Creare una cassetta postale sala abilitata all'accesso (Exchange Online o Exchange Server 2016 e versioni successive) | Questo tipo di cassetta postale consente al dispositivo di gestire un calendario delle riunioni, ricevere convocazioni di riunione e inviare posta. Deve essere abilitato all'accesso per poter essere utilizzato con un Surface Hub. |
| 2    | Configurare le proprietà della cassetta postale | La cassetta postale deve essere configurata con le proprietà corrette per assicurare la migliore esperienza per le riunioni nel dispositivo Surface Hub. Per altre informazioni sulle proprietà della cassetta postale, vedi l'argomento relativo alle [proprietà della cassetta postale](exchange-properties-for-surface-hub-device-accounts.md). |
| 3    | Verificare che Exchange Web Services (EWS) sia abilitato e che l'autenticazione a più fattori (MFA) sia disabilitata | Il Surface Hub utilizza EWS per sincronizzare il calendario. Se non si consente EWS nell'ambiente per impostazione predefinita, la cassetta postale hub deve essere abilitata in modo esplicito. Quando il Surface Hub accede Exchange in background senza l'interazione dell'utente, non può rispondere a prompt interattivi, ad esempio MFA. L'account del dispositivo creato deve essere escluso da tali requisiti di autenticazione. In caso contrario, Surface Hub non sarà in grado di sincronizzare le informazioni della posta e del calendario. |
| 4    | Abilitare l'account Teams o Skype for Business (Skype for Business Server 2015 e versioni successive) | Skype for Business o Teams devono essere abilitate per usare funzionalità di conferenza come videochiamate e condivisione dello schermo. Per ulteriori informazioni sulle licenze che abilitano la Teams, vedere Teams Sala riunioni [licenze](/MicrosoftTeams/rooms/rooms-licensing) e descrizione [Teams servizio.](/office365/servicedescriptions/teams-service-description) Le applicazioni Teams e SfB nel Surface Hub non sono compatibili con i criteri di accesso condizionale di [Azure AD](/azure/active-directory/conditional-access/concept-conditional-access-policies) che richiedono informazioni sul dispositivo (ad esempio conformità). L'account del dispositivo creato deve essere escluso da tali criteri CA. In caso contrario, Surface Hub non sarà possibile utilizzare alcuna funzionalità di conferenza. |
| 5    | (Facoltativo) Disabilitare la scadenza delle password | Per semplificare la gestione, puoi disattivare la scadenza delle password per l'account del dispositivo e consentire al dispositivo Surface Hub di ruotare automaticamente la password per l'account del dispositivo. Per altre informazioni sulla gestione delle password, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).  |
| 6    | (Facoltativo) Configurare Exchange criteri per consentire ActiveSync | Con alcune distribuzioni locali Exchange Server & Active Directory, ActiveSync verrà usato per sincronizzare la posta dell'account del dispositivo e le informazioni del calendario. Per ulteriori informazioni sui criteri da configurare, vedere [Criteri di ActiveSync per Surface Hub account](apply-activesync-policies-for-surface-hub-device-accounts.md). |

> [!NOTE]  
> L Surface Hub dell'account del dispositivo non supporta provider di identità federati di terze parti e deve eseguire l'autenticazione tramite Active Directory o Azure Active Directory.

## <a name="detailed-configuration-steps"></a>Passaggi di configurazione dettagliati 

Ti consigliamo di configurare gli account Surface Hub dispositivo usando gli account Windows PowerShell. Microsoft fornisce [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105), uno script che consente di creare nuovi account delle risorse o di convalidare gli account delle risorse esistenti di cui si dispone per poterli convertire in account Surface Hub compatibili. Se si preferisce, è possibile scegliere un'opzione dalla tabella seguente e seguire i passaggi dettagliati di PowerShell in base alla distribuzione dell'organizzazione.

| Distribuzione dell'organizzazione             |  Descrizione                  |        Formato da utilizzare durante l'Surface Hub di installazione
|---------------------------------|--------------------------------------|
| [Distribuzione online (Microsoft 365 o Office 365)](/MicrosoftTeams/rooms/with-office-365) |L'ambiente dell'organizzazione viene distribuito interamente Microsoft 365 o Office 365. | nomeutente@dominio.com |
| [Distribuzione ibrida (Exchange locale)](/MicrosoftTeams/rooms/with-exchange-on-premises) | L'organizzazione dispone di una combinazione di servizi, con Exchange Server ospitati in locale e Microsoft Teams online. | username@domain.com se [l'autenticazione moderna ibrida](/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication) è abilitata in Exchange, DOMINIO\nomeutente in caso contrario |
| [Distribuzione ibrida (Exchange Online)](/MicrosoftTeams/rooms/with-exchange-online) | L'organizzazione dispone di una combinazione di servizi, con Skype for Business Server ospitati in locale e Exchange Online. | username@domain.com se [l'autenticazione moderna ibrida](/microsoft-365/enterprise/configure-skype-for-business-for-hybrid-modern-authentication) è abilitata in SfB, DOMINIO\nomeutente in caso contrario |
| [Distribuzione locale (singola foresta)](/MicrosoftTeams/rooms/with-skype-for-business-server-2015) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a foresta singola.  | DOMINIO\nomeutente |
| [Distribuzione locale (più foreste)](/skypeforbusiness/deploy/deploy-clients/multiple-forest-on-premises-deployments) | L'organizzazione dispone di server che controlla, in cui Active Directory, Exchange e Skype for Business Server sono ospitati in un ambiente a più foreste. | ACCOUNTFOREST\username |


## <a name="account-verification-and-testing"></a>Verifica dell'account e test

Sono disponibili due metodi che puoi usare per convalidare e testare un account Surface Hub dispositivo: [SkypeRoomProvisioningScript.ps1](https://go.microsoft.com/fwlink/?linkid=870105) e l Surface Hub app [diagnostica hardware.](https://www.microsoft.com/store/apps/9nblggh51f2g) Lo script di provisioning dell'account può convalidare un account del dispositivo creato in precedenza usando PowerShell dal PC. L'app di diagnostica hardware di Surface Hub viene installata in Surface Hub e fornisce un feedback dettagliato sugli errori di accesso e comunicazione. Entrambi gli strumenti sono efficaci per testare gli account del dispositivo appena creati e devono essere usati per garantire una disponibilità ottimale degli account.

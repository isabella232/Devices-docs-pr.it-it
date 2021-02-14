---
title: Gestire Surface Hub 2S con Intune
description: Informazioni su come aggiornare e gestire Surface Hub 2S utilizzando Intune.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/10/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 3b3b5ed47e3a34369c6890aac051436db1f42347
ms.sourcegitcommit: f8f32455b1230742c58ee74004cbaaad037069b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/14/2021
ms.locfileid: "11328210"
---
# Gestire Surface Hub 2S con Intune

## Registrare Surface Hub 2S con Intune

Surface Hub 2S consente agli amministratori IT di gestire le impostazioni e i criteri con un provider di gestione dei dispositivi mobili (MDM, Mobile Device Management). Surface Hub 2S dispone di un componente di gestione predefinito per comunicare con il server di gestione, quindi non occorre installare ulteriori client nel dispositivo.

### Registrazione manuale

1. Apri **l'app** Impostazioni in Surface Hub 2S e accedi come amministratore locale. Selezionare **Surface Hub** > **Gestione dispositivi** e quindi selezionare **+** da aggiungere.
2. Ti verrà richiesto di eseguire l'accesso con l'account da usare per Intune. In seguito all'autenticazione, il dispositivo viene registrato automaticamente con Intune.

   ![Registrare Surface Hub 2S con Intune](images/sh2-set-intune1.png)<br>
   
> [!NOTE]
> L'account usato per l'autenticazione sarà l'account di registrazione di Intune e deve essere concesso in licenza per Intune.

### Registrazione automatica — Affiliata ad Azure Active Directory

Durante il processo di configurazione iniziale, quando si affilia un Surface Hub a un tenant di Azure AD con la registrazione automatica di Intune abilitata, il dispositivo verrà registrato automaticamente con Intune. Per ulteriori informazioni, vedere [Metodi di registrazione di Intune per dispositivi Windows](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods). L'affiliazione di Azure AD e la registrazione automatica di Intune sono necessarie affinché Surface Hub risulti come "dispositivo conforme" in Intune. 

## Gestione delle impostazioni di Windows 10 Team con Intune

1. Accedi a **Microsoft Endpoint Manager,** seleziona **Profili di**configurazione dei  >  **dispositivi**  >  **Crea profilo.** 
2. In **Piattaforma**seleziona **Restrizioni dispositivo per Windows 10**e  >  **versioni successive (Windows 10 Team)** e quindi seleziona **Crea.** 
3. Ora puoi sfogliare e selezionare le impostazioni di restrizione del dispositivo preimpostate per Surface Hub e Surface Hub 2S.

 ![Impostare le restrizioni del dispositivo per Surface Hub 2S.](images/sh2-set-intune3.png) <br>

Queste impostazioni si estendono alle categorie seguenti: app ed esperienza, informazioni operative di Azure, manutenzione, sessione e proiezione wireless.  

## Provider di servizi di configurazione supportati

Oltre ai criteri disponibili direttamente tramite la console di Intune, esistono numerosi provider di servizi di configurazione (CSP) mappati a chiavi o file del Registro di sistema. 

Microsoft fornisce in genere nuovi CSP con ogni nuova versione del sistema operativo Windows 10. [Windows 10 Team 2020 Update](surface-hub-2020-update.md) include più di 20 criteri di gestione dei dispositivi nuovi e aggiornati per Surface Hub e Surface Hub 2S. Questi criteri MDM offrono agli amministratori IT un maggiore controllo degli aggiornamenti delle app da Microsoft Store, impostazioni di proiezione wireless come Miracast sull'infrastruttura, impostazioni di rete come qualità del servizio e autenticazione cablata 802.1x e nuove impostazioni correlate a privacy/GDPR.

Per ulteriori informazioni, vedere le risorse seguenti: 

- [Riferimento del provider di servizi di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) 
- [CSP SurfaceHub](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
- [Criteri CSP supportati da Microsoft Surface Hub](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)
- [Novità di Surface Hub Team 2020 Update](surface-hub-2020-update-whats-new.md)

## Impostazioni Quality of Service (QoS)

Per garantire una qualità audio e video ottimale su Surface Hub 2S, aggiungere le seguenti impostazioni QoS al dispositivo. 

### Impostazioni QoS di Microsoft Teams 

| Nome | Descrizione | URI OMA | Tipo | Value |
|:------ |:------------- |:--------- |:------ |:------- |
|**Porte audio**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DestinationPortMatchCondition | String  | 3478-3479 |
|**DSCP audio**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction | Integer | 46 |
|**Porta video**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DestinationPortMatchCondition | String  | 3480 |
|**DSCP video**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction | Integer | 34 |
|**Porta di condivisione**| Intervallo porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DestinationPortMatchCondition | Stringa  | 3481 |
|**Condivisione DSCP**| Contrassegno delle porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DSCPAction | Numero intero | 18 |
|**Porte audio P2P**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DestinationPortMatchCondition | String  | 50000-50019 |
|**DSCP audio P2P**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DSCPAction | Integer | 46 |
|**Porte video P2P**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DestinationPortMatchCondition | String  | 50020-50039 |
|**DSCP video P2P**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DSCPAction | Integer | 34 |
|**Porte di condivisione P2P**| Intervallo porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DestinationPortMatchCondition | String  | 50040-50059 |
|**DSCP di condivisione P2P**| Contrassegno delle porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DSCPAction | Integer | 18 |


### Impostazioni QoS di Skype for Business

| Nome                 | Descrizione           | URI OMA                                                                    | Tipo    | Value                          |
| -------------------- | --------------------- | -------------------------------------------------------------------------- | ------- | ------------------------------ |
| Porte audio          | Intervallo porte audio      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/SourcePortMatchCondition    | String  | 50000-50019                    |
| DSCP audio           | Contrassegno porte audio   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/DSCPAction                  | Integer | 46                             |
| Origine supporti audio   | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| Porte video          | Intervallo porte video      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/SourcePortMatchCondition    | String  | 50020-50039                    |
| DSCP video           | Contrassegno porte video   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/DSCPAction                  | Integer | 34                             |
| Origine supporti video   | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| Condivisione delle porte        | Intervallo porte di condivisione    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/SourcePortMatchCondition  | Stringa  | 50040-50059                    |
| Condivisione DSCP         | Contrassegno delle porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/DSCPAction                | Numero intero | 18                             |
| Condivisione dell'origine multimediale | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |

> [!NOTE]
> Entrambe le tabelle mostrano intervalli di porte predefiniti. Gli amministratori possono modificare gli intervalli di porte nel pannello di controllo di Skype for Business e Teams.

## Impostazioni di Microsoft Teams

È possibile configurare varie impostazioni di Microsoft Teams con Intune.

### Modalità

Surface Hub 2S viene installato con Microsoft Teams in modalità 0, che supporta sia Microsoft Teams che Skype for Business. Le modalità funzionano come descritto di seguito:

- Modalità 0: Skype for Business con funzionalità di Microsoft Teams per le riunioni pianificate.
- Modalità 1: Microsoft Teams con funzionalità di Skype for Business per le riunioni pianificate.
- Modalità 2: solo Microsoft Teams.

Per modificare la modalità, aggiungi le impostazioni seguenti a un [profilo di configurazione del dispositivo personalizzato.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure)

| Nome | Descrizione | URI OMA | Tipo | Value |
|:--- |:--- |:--- |:--- |:--- |
|**ID app Teams**|Nome dell'app|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Modalità app Teams**|Modalità Teams|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0 o 1 o 2|

### Riunioni coordinate e partecipazione di prossimità

Le funzionalità riunione coordinata e partecipazione di prossimità di Teams possono essere [configurate tramite un file XML](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure) distribuito tramite un profilo Intune.

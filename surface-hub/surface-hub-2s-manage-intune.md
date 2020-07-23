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
ms.date: 07/23/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 05279a54b51113ca96c4c939e8d64e51c4eca543
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893111"
---
# Gestire Surface Hub 2S con Intune

## Registrare Surface Hub 2S con Intune

Surface Hub 2S consente agli amministratori IT di gestire le impostazioni e i criteri con un provider di gestione dei dispositivi mobili (MDM, Mobile Device Management). Surface Hub 2S dispone di un componente di gestione predefinito per comunicare con il server di gestione, quindi non occorre installare ulteriori client nel dispositivo.

### Registrazione manuale

1. Eseguire l'accesso come amministratore locale in Surface Hub 2S e aprire l'app **Impostazioni**. Selezionare **Surface Hub** > **Gestione dispositivi** e quindi selezionare **+** da aggiungere.
2. In seguito all'autenticazione, il dispositivo viene registrato automaticamente con Intune.

   ![Registrare Surface Hub 2S con Intune](images/sh2-set-intune1.png)<br>

### Registrazione automatica — Affiliata ad Azure Active Directory

Durante il processo di configurazione iniziale, quando si affilia un Surface Hub a un tenant di Azure AD con la registrazione automatica di Intune abilitata, il dispositivo verrà registrato automaticamente con Intune. Per ulteriori informazioni, vedere [Metodi di registrazione di Intune per dispositivi Windows](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods). L'affiliazione di Azure AD e la registrazione automatica di Intune sono necessarie affinché Surface Hub risulti come "dispositivo conforme" in Intune. 

## Gestione delle impostazioni di Windows 10 Team Edition con Intune

1. Accedere a **Microsoft Endpoint Manager**, selezionare i profili di configurazione dei **dispositivi**per  >  **Configuration profiles**  >  **creare il profilo**. 
2. In **piattaforma**selezionare **Windows 10 e le**  >  **restrizioni di dispositivo successive (team Windows 10)** e quindi selezionare **Crea**. 
3. Ora è possibile esplorare e selezionare le impostazioni di restrizione del dispositivo predefinite per hub Surface e Surface Hub 2S.

 ![Impostare le restrizioni del dispositivo per Surface Hub 2S.](images/sh2-set-intune3.png) <br>

Queste impostazioni si estendono alle seguenti categorie: app ed esperienze, approfondimenti operativi di Azure, manutenzione, sessione e proiezione wireless.  

## Provider di servizi di configurazione supportati (CSP)

Oltre ai criteri disponibili direttamente tramite la console Intune, sono presenti numerosi provider di servizi di configurazione (CSP) che mappano le chiavi del registro di sistema o i file. 

Microsoft fornisce in genere nuovi CSP con ogni nuova versione del sistema operativo Windows 10. L' [aggiornamento di Windows 10 Team 2020](surface-hub-install-2020preview.md), disponibile in anteprima tramite il programma Windows Insider, include più di 20 criteri di gestione dei dispositivi nuovi e aggiornati per i mozzi Surface Hub e Surface Hub 2S. Questi criteri MDM conferiscono agli amministratori IT un maggiore controllo sugli aggiornamenti delle app da Microsoft Store, impostazioni di proiezione wireless come Miracast su infrastruttura, impostazioni di rete, ad esempio qualità del servizio e autenticazione cablata 802.1 x, e nuove impostazioni relative alla privacy/PILR.

Per altre informazioni, vedi le risorse seguenti: 

- [Riferimento del provider di servizi di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference) 
- [CSP SurfaceHub](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
- [Criteri CSP supportati da Microsoft Surface Hub](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)

## Impostazioni Quality of Service (QoS)

Per garantire una qualità audio e video ottimale su Surface Hub 2S, aggiungere le seguenti impostazioni QoS al dispositivo. 

### Impostazioni QoS di Microsoft Teams 

|**Nome**|**Descrizione**|**URI OMA**|**Tipo**|**Value**|
|:------ |:------------- |:--------- |:------ |:------- |
|**Porte audio**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DestinationPortMatchCondition | Stringa  | 3478-3479 |
|**DSCP audio**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction | Numero intero | 46 |
|**Porta video**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DestinationPortMatchCondition | Stringa  | 3480 |
|**DSCP video**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction | Integer | 34 |
|**Porte audio P2P**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DestinationPortMatchCondition | Stringa  | 50000-50019 |
|**DSCP audio P2P**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DSCPAction | Numero intero | 46 |
|**Porte video P2P**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DestinationPortMatchCondition | Stringa  | 50020-50039 |
|**DSCP video P2P**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DSCPAction | Integer | 34 |


### Impostazioni QoS di Skype for Business

| Nome               | Descrizione         | URI OMA                                                                  | Tipo    | Value                          |
| ------------------ | ------------------- | ------------------------------------------------------------------------ | ------- | ------------------------------ |
| Porte audio        | Intervallo porte audio    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/SourcePortMatchCondition  | Stringa  | 50000-50019                    |
| DSCP audio         | Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/DSCPAction                | Numero intero | 46                             |
| Origine supporti audio | Nome app Skype      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |
| Porte video        | Intervallo porte video    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/SourcePortMatchCondition  | Stringa  | 50020-50039                    |
| DSCP video         | Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/DSCPAction                | Integer | 34                             |
| Origine supporti video | Nome app Skype      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |

> [!NOTE]
> Entrambe le tabelle mostrano intervalli di porte predefiniti. Gli amministratori possono modificare gli intervalli di porte nel pannello di controllo di Skype for Business e Teams.

## Impostazioni di modalità di Microsoft Teams

È possibile impostare la modalità dell'app Microsoft Teams con Intune. Surface Hub 2S viene installato con Microsoft Teams in modalità 0, che supporta sia Microsoft Teams che Skype for Business. È possibile modificare le modalità come illustrato di seguito.

### Modalità:

- Modalità 0: Skype for Business con funzionalità di Microsoft Teams per le riunioni pianificate.
- Modalità 1: Microsoft Teams con funzionalità di Skype for Business per le riunioni pianificate.
- Modalità 2: solo Microsoft Teams.

Per impostare le modalità, aggiungere le impostazioni seguenti a un profilo di configurazione dispositivo personalizzato.

|**Nome**|**Descrizione**|**URI OMA**|**Tipo**|**Value**|
|:--- |:--- |:--- |:--- |:--- |
|**ID app Teams**|Nome dell'app|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Modalità app Teams**|Modalità Teams|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0 o 1 o 2|

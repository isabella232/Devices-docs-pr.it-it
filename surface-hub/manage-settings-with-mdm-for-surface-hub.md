---
title: Gestire le impostazioni con un provider MDM (Surface Hub)
description: Con Surface Hub gli amministratori possono gestire criteri e applicazioni aziendali in questi dispositivi con una soluzione di gestione di dispositivi mobili.
ms.assetid: 18EB8464-6E22-479D-B0C3-21C4ADD168FE
ms.reviewer: ''
manager: laurawi
keywords: gestione dei dispositivi mobili, MDM (Mobile Device Management), gestire i criteri
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 1afa4d63dde793e61e30d1c4dd54f552b5581a81
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470459"
---
# <a name="manage-surface-hub-with-an-mdm-provider"></a>Gestire Surface Hub con un provider MDM

Surface Hub consente agli amministratori IT di gestire le impostazioni e i criteri usando un provider di gestione dei dispositivi mobili (MDM), ad esempio Microsoft Intune. Surface Hub ha un componente di gestione incorporato per comunicare con il server di gestione. Non è necessario installare altri client nel dispositivo.

## <a name="enrolling-surface-hub-into-mdm-management"></a>Registrazione di Surface Hub nella gestione MDM 

Puoi registrare Surface in Microsoft Intune o in un altro provider MDM tramite registrazione manuale o automatica.

### <a name="manual-enrollment"></a>Registrazione manuale

1. Apri **l'app** Impostazioni e accedi come amministratore locale. Seleziona **Gestione dispositivi Surface Hub**e quindi seleziona  >  **** **+Gestione dispositivi.**
2. Ti verrà richiesto di accedere con l'account da usare per il provider MDM. Dopo l'autenticazione, il dispositivo si registra automaticamente con il provider MDM.

> [!TIP]
> Se si usa Intune e l'indirizzo del server non viene rilevato, immettere **manage.microsoft.com**.
   
> [!NOTE]
>  La registrazione MDM usa i dettagli dell'account forniti per l'autenticazione. L'account deve disporre delle autorizzazioni per registrare un dispositivo Windows, nonché una licenza di Intune (o le promissioni di registrazione equivalenti configurate nel provider MDM di terze parti).

### <a name="auto-enrollment--azure-ad-affiliated"></a>Registrazione automatica : consociata ad Azure AD

Durante il processo di configurazione iniziale, quando si affilia Surface Hub a un tenant di Azure Active Directory (AD) con la registrazione automatica di Intune abilitata, il dispositivo verrà registrato automaticamente con Intune. Per altre informazioni, fai riferimento ai [metodi di registrazione di Intune per i dispositivi Windows.](https://docs.microsoft.com/intune/enrollment/windows-enrollment-methods) L'affiliazione di Azure AD e la registrazione automatica di Intune sono necessarie affinché Surface Hub risulti come "dispositivo conforme" in Intune. 

## <a name="manage-surface-hub-windows-10-team-settings-with-intune"></a>Gestire le impostazioni del team di Windows 10 di Surface Hub con Intune

Il blocco predefinito di base della gestione delle impostazioni dei criteri in Intune e altri provider MDM è il protocollo Open Mobile Alliance-Device Management (OMA-DM) basato su XML. Windows 10 implementa xml OMA-DM tramite uno dei molti provider di servizi di configurazione disponibili con nomi come CSP AccountManagement, CSP DeviceStatus, Wirednetwork-CSP e così via. Per un elenco completo, fai riferimento ai [CSP supportati in Microsoft Surface Hub.](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)


Microsoft Intune e altri provider MDM usano CSP per fornire un'interfaccia utente che consente di configurare le impostazioni dei criteri all'interno dei profili di configurazione. Intune usa il CSP di Surface Hub per il suo profilo incorporato, ovvero restrizioni per i dispositivi  **(Windows 10 Team),** che ti consente di configurare le impostazioni di base, ad esempio impedire a Surface Hub di "svegliarsi" ogni volta che qualcuno si sposta nelle vicinanze entro il suo intervallo di prossimità. Per gestire le impostazioni e le funzionalità dell'hub al di fuori del profilo predefinito di Intune, dovrai usare un profilo personalizzato, come [illustrato di seguito.](#create-custom-configuration-profile) 

Per riepilogare, le opzioni per configurare e gestire le impostazioni dei criteri in Intune includono: 
 
- **Creare un profilo di restrizione del dispositivo.** Usa il profilo incorporato di Intune e configura le impostazioni direttamente nell'interfaccia utente di Intune. Vedi [Creare il profilo di restrizione del dispositivo.](#create-device-restriction-profile)
- **Creare un profilo di configurazione del dispositivo.**  Seleziona un modello incentrato su una funzionalità o una tecnologia specifica, ad esempio Microsoft Defender o certificati di sicurezza. Vedi [Creare il profilo di configurazione del dispositivo.](#create-device-configuration-profile)
- **Creare un profilo di configurazione personalizzato.**  Estendi l'ambito di gestione usando un URI OMA (Uniform Resource Identifier) OMA da uno dei [CSP supportati in Microsoft Surface Hub.](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport) Vedi [Creare un profilo di configurazione personalizzato.](#create-custom-configuration-profile)


## <a name="create-device-restriction-profile"></a>Creare il profilo di restrizione del dispositivo

1. Accedi [**all'interfaccia di amministrazione di Microsoft Endpoint Manager,**](https://endpoint.microsoft.com/)seleziona **Profili**di  >  **configurazione dispositivi**  >  **+** **Crea profilo.**
2. In **Piattaforma**seleziona **Windows 10 e versioni successive** >
3. In Tipo di profilo ****, seleziona **Modelli** e quindi seleziona **Restrizioni dispositivo (Windows 10 Team)** ****
4. Selezionare **Crea**, aggiungere un nome e quindi selezionare **Avanti.**
6. Ora puoi esplorare e scegliere tra le impostazioni di restrizione predefinite dei dispositivi per Surface Hub nelle categorie seguenti: app ed esperienza, informazioni operative di Azure, manutenzione, sessione e proiezione wireless. L'esempio mostrato nella figura seguente specifica una finestra di manutenzione di 4 ore e un timeout di 15 minuti per la ripresa dello schermo, della sospensione e della sessione.

     ![Configurare le impostazioni di Surface Hub con il profilo di restrizione del dispositivo Intune](images/sh-device-restrictions.png)

Per altre informazioni sulla creazione e la gestione dei profili, vedi Limitare le funzionalità [dei dispositivi usando i criteri in Microsoft Intune.](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-configure#create-the-profile)
 
Per altre informazioni su come gestire le funzionalità e le impostazioni di Surface Hub, vedi Restrizioni per i dispositivi [Surface Hub Windows 10 Team in Microsoft Intune](https://docs.microsoft.com/mem/intune/configuration/device-restrictions-windows-10-teams)
 

## <a name="create-device-configuration-profile"></a>Creare il profilo di configurazione del dispositivo

1. Accedi [**all'interfaccia di amministrazione di Microsoft Endpoint Manager,**](https://endpoint.microsoft.com/)seleziona **Profili**di configurazione  >  **dei dispositivi**  >  **+ Crea profilo.**
2. In **Piattaforma**seleziona **Windows 10 e versioni successive** >
3. In **Tipo di profilo**seleziona **Modelli** e scegli uno dei modelli seguenti supportati in Surface Hub:

    - Restrizioni dei dispositivi (Windows 10 Team), come descritto nella [sezione precedente.](#create-device-restriction-profile)
    - Microsoft Defender for Endpoint (Windows 10 Desktop)
    - Certificato PKCS
    - Certificato importato PKCS
    - Certificato SCEP
    - Certificato attendibile

## <a name="create-custom-configuration-profile"></a>Creare un profilo di configurazione personalizzato

Puoi estendere l'ambito [](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure) di gestione creando un profilo personalizzato usando un URI OMA da uno dei provider di servizi di configurazione [supportati in Microsoft Surface Hub.](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport) Ogni impostazione in un provider di servizi di configurazione ha un URI OMA corrispondente che puoi impostare usando profili di configurazione personalizzati in Intune. Per informazioni dettagliate sui CSP supportati da Surface Hub, puoi fare riferimento alle risorse seguenti: 

- [Riferimento del provider di servizi di configurazione](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Criteri CSP supportati da Microsoft Surface Hub](https://docs.microsoft.com/windows/client-management/mdm/policy-csps-supported-by-surface-hub)
- [CSP SurfaceHub](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp)
> [!NOTE]
> La gestione dell'account del dispositivo con le impostazioni del [CSP SurfaceHub](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp) non è attualmente possibile con Intune e richiede l'uso di un provider MDM di terze parti.

Per implementare le impostazioni dei criteri basati su CSP, iniziare generando un URI OMA e quindi aggiungerlo a un profilo di configurazione personalizzato in Intune.

### <a name="generate-oma-uri-for-target-setting"></a>Generare l'URI OMA per l'impostazione di destinazione
 
Per generare l'URI OMA per qualsiasi impostazione:

1. Nella documentazione [del provider di servizi di](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)configurazione identificare il nodo radice del provider di servizi di configurazione. In genere, è **simile a <name of CSP> ./Vendor/MSFT/**. 
    - **Esempio:** Il nodo radice del [CSP SurfaceHub](https://docs.microsoft.com/windows/client-management/mdm/surfacehub-csp) **è ./Vendor/MSFT/SurfaceHub.**
2. Identifica il percorso del nodo per l'impostazione che vuoi usare. 
    - **Esempio:** Il percorso del nodo per l'impostazione per abilitare la proiezione wireless è **InBoxApps/WirelessProjection/Enabled.**
3. Aggiungi il percorso del nodo al nodo radice per generare l'URI OMA. 
    - **Esempio:** L'URI OMA per l'impostazione per abilitare la proiezione wireless è **./Vendor/MSFT/SurfaceHub/InBoxApps/WirelessProjection/Enabled.**
4. Anche il tipo di dati è indicato nella documentazione del CSP. I tipi di dati più comuni sono:
    - char (stringa)
    - int (intero)
    - bool (booleano)

### <a name="add-oma-uri-to-custom-configuration-profile"></a>Aggiungere l'URI OMA al profilo di configurazione personalizzato

1. In Endpoint Manager seleziona **Profili di**  >  **configurazione dispositivi**Crea  >  **profilo.**
2. In Piattaforma seleziona **Windows 10 e versioni successive.** In Profilo selezionare **Personalizzato**e quindi **Crea.**
3. Aggiungere un nome e una descrizione facoltativa e quindi selezionare **Avanti.**
4. In **Impostazioni di configurazione**Impostazioni URI  >  **OMA**seleziona **Aggiungi.**

  
## <a name="manage-specific-surface-hub-features"></a>Gestire funzionalità di Surface Hub specifiche

In questa sezione vengono evidenziate le informazioni sulle funzionalità che è possibile gestire tramite Intune o un altro provider MDM. Ciò include:

- [Qualità del servizio (QoS)](#quality-of-service-settings)
- [Microsoft Teams e Skype for Business](#microsoft-teams-and-skype-for-business-settings)

### <a name="quality-of-service-settings"></a>Impostazioni qualità del servizio

Per garantire una qualità audio e video ottimale in Surface Hub, aggiungi le impostazioni QoS seguenti al dispositivo. 

| Nome | Descrizione | URI OMA | Tipo | Value |
|:------ |:------------- |:--------- |:------ |:------- |
|**Porte audio**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DestinationPortMatchCondition | String  | 3478-3479 |
|**DSCP audio**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction | Integer | 46 |
|**Porta video**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DestinationPortMatchCondition | String  | 3480 |
|**DSCP video**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction | Integer | 34 |
|**Porta di condivisione**| Intervallo porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DestinationPortMatchCondition | Stringa  | 3481 |
|**Condivisione di DSCP**| Contrassegno porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DSCPAction | Numero intero | 18 |
|**Porte audio P2P**| Intervallo porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DestinationPortMatchCondition | String  | 50000-50019 |
|**DSCP audio P2P**| Contrassegno porte audio | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PAudio/DSCPAction | Integer | 46 |
|**Porte video P2P**| Intervallo porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DestinationPortMatchCondition | String  | 50020-50039 |
|**DSCP video P2P**| Contrassegno porte video | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PVideo/DSCPAction | Integer | 34 |
|**Porte di condivisione P2P**| Intervallo porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DestinationPortMatchCondition | Stringa  | 50040-50059 |
|**Condivisione P2P DSCP**| Contrassegno porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsP2PSharing/DSCPAction | Numero intero | 18 |


#### <a name="skype-for-business-qos-settings"></a>Impostazioni QoS di Skype for Business

| Nome                 | Descrizione           | URI OMA                                                                    | Tipo    | Value                          |
| -------------------- | --------------------- | -------------------------------------------------------------------------- | ------- | ------------------------------ |
| Porte audio          | Intervallo porte audio      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/SourcePortMatchCondition    | String  | 50000-50019                    |
| DSCP audio           | Contrassegno porte audio   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/DSCPAction                  | Integer | 46                             |
| Origine supporti audio   | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBAudio/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| Porte video          | Intervallo porte video      | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/SourcePortMatchCondition    | String  | 50020-50039                    |
| DSCP video           | Contrassegno porte video   | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/DSCPAction                  | Integer | 34                             |
| Origine supporti video   | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBVideo/AppPathNameMatchCondition   | String  | Microsoft.PPISkype.Windows.exe |
| Condivisione delle porte        | Intervallo porte di condivisione    | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/SourcePortMatchCondition  | Stringa  | 50040-50059                    |
| Condivisione di DSCP         | Contrassegno porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/DSCPAction                | Numero intero | 18                             |
| Condivisione dell'origine multimediale | Nome app Skype        | ./Device/Vendor/MSFT/NetworkQoSPolicy/SfBSharing/AppPathNameMatchCondition | String  | Microsoft.PPISkype.Windows.exe |

> [!NOTE]
> Entrambe le tabelle mostrano intervalli di porte predefiniti. Gli amministratori possono modificare gli intervalli di porte nel pannello di controllo di Skype for Business e Teams.

### <a name="microsoft-teams-and-skype-for-business-settings"></a>Impostazioni di Microsoft Teams e Skype for Business

È possibile creare un profilo di configurazione personalizzato per gestire riunioni coordinate di Teams, partecipazione di prossimità e altre funzionalità. Per altre informazioni, vedi [Gestire la configurazione di Microsoft Teams in Surface Hub.](https://docs.microsoft.com/microsoftteams/rooms/surface-hub-manage-config)

#### <a name="changing-default-business-communications-platform"></a>Modifica della piattaforma di comunicazione aziendale predefinita

La piattaforma di comunicazione aziendale predefinita in Surface Hub varia a seconda di come installi Windows 10 Team 2020 Update (noto anche come Windows 10 20H2). Se re-immagine surface Hub a Windows 10 20H2, Microsoft Teams verrà impostato come predefinito, con la funzionalità Skype for Business disponibile (modalità 1). Se a upgrade your Hub from an earlier OS version, Skype for Business will remain as the default, with Teams functionality available (Mode 0) unless you had already configured Teams as your default. 

Per modificare l'installazione predefinita, utilizzare un [profilo personalizzato](https://docs.microsoft.com/mem/intune/configuration/custom-settings-configure) impostando la modalità app di Teams nel modo seguente:  

- Modalità 0: Skype for Business con funzionalità di Microsoft Teams per le riunioni pianificate.
- Modalità 1: Microsoft Teams con funzionalità di Skype for Business per le riunioni pianificate.
- Modalità 2: solo Microsoft Teams.

| Nome | Descrizione | URI OMA | Tipo | Value |
|:--- |:--- |:--- |:--- |:--- |
|**ID app Teams**|Nome dell'app|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Modalità app Teams**|Modalità Teams|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0 o 1 o 2|











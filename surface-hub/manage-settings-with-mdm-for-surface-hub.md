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
ms.openlocfilehash: e126799fe023d97468e58c01b003ce4b605f2db7
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497789"
---
# <a name="manage-surface-hub-with-an-mdm-provider"></a>Gestire Surface Hub con un provider MDM

Surface Hub consente agli amministratori IT di gestire impostazioni e criteri usando un provider di gestione dei dispositivi mobili (MDM), ad esempio Microsoft Intune. Surface Hub dispone di un componente di gestione predefinito per comunicare con il server di gestione. Non è necessario installare altri client nel dispositivo.

## <a name="enrolling-surface-hub-into-mdm-management"></a>Registrazione di Surface Hub nella gestione MDM 

È possibile registrare Surface in Microsoft Intune o in un altro provider MDM tramite registrazione manuale o automatica.

### <a name="manual-enrollment"></a>Registrazione manuale

1. Aprire l'app **Impostazioni** e accedere come amministratore locale. Selezionare **Surface Hub** >  **Gestione dei dispositivi** e quindi selezionare **+Gestione dispositivi**.
2. Verrà richiesto di accedere con l'account da usare per il provider MDM. Dopo l'autenticazione, il dispositivo si registra automaticamente con il provider MDM.

> [!TIP]
> Se si usa Intune e l'indirizzo del server non viene rilevato, immettere **manage.microsoft.com**.
   
> [!NOTE]
> La registrazione MDM usa i dettagli dell'account forniti per l'autenticazione. L'account deve avere le autorizzazioni per registrare un dispositivo Windows e una licenza Intune (o le autorizzazioni di registrazione equivalenti configurate nel provider MDM di terze parti).

### <a name="auto-enrollment--azure-ad-affiliated"></a>Registrazione automatica — Azure AD affiliata

Durante il processo di installazione iniziale, quando si associa Surface Hub con un tenant di Azure Active Directory (AD) con Intune registrazione automatica abilitata, il dispositivo verrà registrato automaticamente con Intune. Per altre informazioni, vedere [Intune metodi di registrazione per i dispositivi Windows](/intune/enrollment/windows-enrollment-methods). L'affiliazione di Azure AD e la registrazione automatica di Intune sono necessarie affinché Surface Hub risulti come "dispositivo conforme" in Intune. 

## <a name="manage-surface-hub-windows-10-team-settings-with-intune"></a>Gestire le impostazioni di Surface Hub Windows 10 Team con Intune

Il blocco predefinito fondamentale della gestione delle impostazioni dei criteri in Intune e altri provider MDM è il protocollo Open Mobile Alliance-Device Management (OMA-DM) basato su XML. Windows implementa OMA-DM XML tramite uno dei numerosi provider di servizi di configurazione (CSP) disponibili con nomi come AccountManagement CSP, DeviceStatus CSP, WiFi-CSP e così via. Per un elenco completo, vedere [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport).

Microsoft Intune e altri provider MDM usano CSP per distribuire un'interfaccia utente che consente di configurare le impostazioni dei criteri all'interno dei profili di configurazione. Intune usa l'Surface Hub CSP per il profilo predefinito **, ovvero Limitazioni del dispositivo (Windows 10 Team),** che consente di configurare impostazioni di base, ad esempio impedire Surface Hub di "riattivarsi" ogni volta che qualcuno si sposta nelle vicinanze all'interno dell'intervallo di prossimità. Per gestire le impostazioni e le funzionalità dell'hub al di fuori del profilo predefinito di Intune, è necessario usare un profilo personalizzato, come [illustrato di seguito](#create-custom-configuration-profile). 

Per riepilogare, le opzioni per configurare e gestire le impostazioni dei criteri all'interno di Intune includono quanto segue: 
 
- **Creare un profilo di restrizione del dispositivo.** Usa il profilo predefinito di Intune e configura le impostazioni direttamente nell'interfaccia utente Intune. Vedere [Creare il profilo di restrizione del dispositivo](#create-device-restriction-profile).
- **Creare un profilo di configurazione del dispositivo.**  Selezionare un modello incentrato su una funzionalità o una tecnologia specifica, ad esempio Microsoft Defender o i certificati di sicurezza. Vedere [Creare il profilo di configurazione del dispositivo](#create-device-configuration-profile).
- **Creare un profilo di configurazione personalizzato.**  Estendere l'ambito di gestione usando un URI OMA (Uniform Resource Identifier) OMA da uno dei [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport). Vedere [Creare un profilo di configurazione personalizzato](#create-custom-configuration-profile).

> [!NOTE]
> I profili devono essere assegnati ai gruppi di dispositivi contenenti i dispositivi Surface Hub registrati.

## <a name="create-device-restriction-profile"></a>Creare il profilo di restrizione del dispositivo

1. Accedere a [**Microsoft Endpoint Manager'interfaccia di amministrazione**](https://endpoint.microsoft.com/), selezionare **DispositiviProfili** > **** > **+** di configurazione **Crea profilo**.
2. In **Piattaforma** selezionare **Windows 10 e versioni successive** >
3. In ******Tipo di** profilo selezionare **Modelli** e quindi Selezionare **Restrizioni del dispositivo (Windows 10 Team)**
4. Selezionare **Crea**, aggiungere un nome e quindi selezionare **Avanti.**
6. È ora possibile esplorare e scegliere tra impostazioni di restrizione del dispositivo predefinite per Surface Hub nelle categorie seguenti: App ed esperienza, Informazioni operative di Azure, Manutenzione, Sessione e Proiezione wireless. L'esempio illustrato nella figura seguente specifica una finestra di manutenzione di 4 ore e un timeout di 15 minuti per la ripresa dello schermo, della sospensione e della sessione.

     ![Configurare le impostazioni di Surface Hub con Intune profilo di restrizione del dispositivo.](images/sh-device-restrictions.png)

Per altre informazioni sulla creazione e la gestione dei profili, vedere [Limitare le funzionalità dei dispositivi usando i criteri in Microsoft Intune](/mem/intune/configuration/device-restrictions-configure#create-the-profile).
 
Per altre informazioni su come gestire le funzionalità e le impostazioni di Surface Hub, vedere [impostazioni di Windows 10 Team per consentire o limitare le funzionalità nei Surface Hub usando Intune](/mem/intune/configuration/device-restrictions-windows-10-teams)
 

## <a name="create-device-configuration-profile"></a>Creare il profilo di configurazione del dispositivo

1. Accedere a [**Microsoft Endpoint Manager'interfaccia di amministrazione**](https://endpoint.microsoft.com/), selezionare **DispositiviProfili** > **** >  di configurazione **+ Crea profilo**.
2. In **Piattaforma** selezionare **Windows 10 e versioni successive** >
3. In **Tipo di profilo** selezionare **Modelli** e scegliere tra i modelli seguenti supportati in Surface Hub:

    - Restrizioni del dispositivo (Windows 10 Team), come descritto nella [sezione precedente](#create-device-restriction-profile).
    - Microsoft Defender per endpoint (desktop Windows 10)
    - Certificato PKCS
    - Certificato PKCS importato
    - Certificato SCEP
    - Certificato attendibile

## <a name="create-custom-configuration-profile"></a>Creare un profilo di configurazione personalizzato

È possibile estendere l'ambito della gestione [creando un profilo personalizzato](/mem/intune/configuration/custom-settings-configure) usando un URI OMA da uno dei [CSP supportati in Microsoft Surface Hub](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport). Ogni impostazione in un provider di servizi di configurazione ha un URI OMA corrispondente che è possibile impostare usando profili di configurazione personalizzati in Intune. Per informazioni dettagliate sui CSP supportati da Surface Hub, è possibile fare riferimento alle risorse seguenti: 

- [Riferimento del provider di servizi di configurazione](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport)
- [Criteri CSP supportati da Microsoft Surface Hub](/windows/client-management/mdm/policy-csps-supported-by-surface-hub)
- [CSP SurfaceHub](/windows/client-management/mdm/surfacehub-csp)
> [!NOTE]
> La gestione dell'account del dispositivo tramite le impostazioni di [SurfaceHub CSP](/windows/client-management/mdm/surfacehub-csp) non è attualmente possibile con Intune e richiede l'uso di un provider MDM di terze parti.

Per implementare le impostazioni dei criteri basate su CSP, iniziare generando un URI OMA e quindi aggiungendolo a un profilo di configurazione personalizzato in Intune.

### <a name="generate-oma-uri-for-target-setting"></a>Generare l'URI OMA per l'impostazione di destinazione
 
Per generare l'URI OMA per qualsiasi impostazione:

1. Nella [documentazione CSP](/windows/client-management/mdm/configuration-service-provider-reference#surfacehubcspsupport) identificare il nodo radice del CSP. In genere, questo aspetto è simile **a ./Vendor/MSFT/NameOfCSP**. 
    - **Esempio:** Il nodo radice del [provider di servizi di configurazione SurfaceHub](/windows/client-management/mdm/surfacehub-csp) è **./Vendor/MSFT/SurfaceHub**.
2. Identifica il percorso del nodo per l'impostazione che vuoi usare. 
    - **Esempio:** Il percorso del nodo per l'impostazione per abilitare la proiezione wireless è **InBoxApps/WirelessProjection/Enabled**.
3. Aggiungi il percorso del nodo al nodo radice per generare l'URI OMA. 
    - **Esempio:** L'URI OMA per l'impostazione per abilitare la proiezione wireless è **./Vendor/MSFT/SurfaceHub/InBoxApps/WirelessProjection/Enabled.**
4. Anche il tipo di dati è indicato nella documentazione del CSP. I tipi di dati più comuni sono:
    - char (stringa)
    - int (intero)
    - bool (booleano)

### <a name="add-oma-uri-to-custom-configuration-profile"></a>Aggiungere l'URI OMA al profilo di configurazione personalizzato

1. In Endpoint Manager selezionare **DispositiviProfili** >  >  **di configurazioneCrea** **profilo**.
2. In Piattaforma selezionare **Windows 10 e versioni successive.** In Profilo selezionare **Personalizzato** e quindi selezionare **Crea.**
3. Aggiungere un nome e una descrizione facoltativa e quindi selezionare **Avanti.**
4. In **Impostazioni di configurazione** >  **IMPOSTAZIONI URI OMA** selezionare **Aggiungi**.

  
## <a name="microsoft-teams-and-skype-for-business-settings"></a>impostazioni Microsoft Teams e Skype for Business

Questa sezione evidenzia le impostazioni Teams e Skype for Business che è possibile gestire tramite Intune o un altro provider MDM. Ciò include:

- [Qualità del servizio (QoS)](#quality-of-service-settings)
- [Gestire funzionalità specifiche di Teams](#manage-teams-specific-features)

### <a name="quality-of-service-settings"></a>Impostazioni della qualità del servizio

Per garantire una qualità audio e video ottimale in Surface Hub, aggiungere le impostazioni QoS seguenti al dispositivo. 

| Nome                 | Descrizione           | URI OMA                                                                 | Tipo    | Value                          |
| -------------------- | --------------------- | ----------------------------------------------------------------------- | ------- | ------------------------------ |
| Porte audio          | Intervallo porte audio      | ./Device/Vendor/MSFT/NetworkQoSPolicy/Audio/SourcePortMatchCondition    | String  | 50000-50019                    |
| DSCP audio           | Contrassegno porte audio   | ./Device/Vendor/MSFT/NetworkQoSPolicy/Audio/DSCPAction                  | Integer | 46                             |
| Porte video          | Intervallo porte video      | ./Device/Vendor/MSFT/NetworkQoSPolicy/Video/SourcePortMatchCondition    | String  | 50020-50039                    |
| DSCP video           | Contrassegno porte video   | ./Device/Vendor/MSFT/NetworkQoSPolicy/Video/DSCPAction                  | Integer | 34                             |
| Porte di condivisione        | Intervallo di porte di condivisione    | ./Device/Vendor/MSFT/NetworkQoSPolicy/Sharing/SourcePortMatchCondition  | Stringa  | 50040-50059                    |
| Condivisione di DSCP         | Contrassegno delle porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/Sharing/DSCPAction                | Numero intero | 18                             |

> [!NOTE]
> La tabella mostra gli intervalli di porte predefiniti. Gli amministratori possono modificare gli intervalli di porte nel pannello di controllo di Skype for Business e Teams.

### <a name="manage-teams-specific-features"></a>Gestire funzionalità specifiche di Teams

È possibile creare un profilo di configurazione personalizzato per gestire Teams riunioni coordinate, join di prossimità e altre funzionalità. Per altre informazioni, vedere [Gestire la configurazione Microsoft Teams in Surface Hub](/microsoftteams/rooms/surface-hub-manage-config).

### <a name="changing-default-app-for-meetings--calls"></a>Modifica dell'app predefinita per le riunioni & le chiamate

L'app predefinita per le riunioni & chiamate nel Surface Hub varia a seconda di come si installa Windows 10 Team aggiornamento 2020 (noto anche come Windows 10 20H2 Team Edition). Se si ricrea l'immagine di un Surface Hub per Windows 10 20H2, Microsoft Teams verrà impostato come predefinito, con Skype for Business non disponibile (modalità 1). Se si aggiorna l'hub da una versione precedente del sistema operativo, Skype for Business rimarrà come impostazione predefinita, con Teams funzionalità disponibile (modalità 0) a meno che non sia già stato configurato Teams come impostazione predefinita. 

Per modificare l'installazione predefinita, usare un [profilo personalizzato](/mem/intune/configuration/custom-settings-configure) per impostare la modalità riunione Teams come indicato di seguito:  

- Modalità 0: Skype for Business con funzionalità di Microsoft Teams per le riunioni pianificate.
- Modalità 1: solo Microsoft Teams.

| Nome | Descrizione | URI OMA | Tipo | Value |
|:--- |:--- |:--- |:--- |:--- |
|**ID app Teams**|Nome dell'app|./Vendor/MSFT/SurfaceHub/Properties/VtcAppPackageId|String| Microsoft.MicrosoftTeamsforSurfaceHub_8wekyb3d8bbwe!Teams|
|**Modalità app Teams**|Modalità Teams|./Vendor/MSFT/SurfaceHub/Properties/SurfaceHubMeetingMode|Integer| 0 o 1|



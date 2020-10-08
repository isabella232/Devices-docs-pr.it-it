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
ms.date: 03/07/2018
ms.localizationpriority: medium
ms.openlocfilehash: 2bee8b58b7978923c6e60e43f9e10a85dc4bec06
ms.sourcegitcommit: 17170c03206d190851b5f8e794fcc83ebbed7b5f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2020
ms.locfileid: "11103902"
---
# Gestire le impostazioni con un provider MDM (Surface Hub)

Surface Hub e altri dispositivi Windows10 consentono agli amministratori IT di gestire le impostazioni e i criteri con un provider di gestione dei dispositivi mobili (MDM, Mobile Device Management). Un componente di gestione predefinito comunica con il server di gestione, quindi non occorre installare ulteriori client nel dispositivo. For more information, see [Windows 10 mobile device management](https://msdn.microsoft.com/library/windows/hardware/dn914769.aspx).

Surface Hub has been validated with Microsoft's first-party MDM providers:
- Microsoft Intune standalone
- On-premises MDM with Microsoft Endpoint Configuration Manager

You can also manage Surface Hubs using any third-party MDM provider that can communicate with Windows 10 using the MDM protocol.

## <a href="" id="enroll-into-mdm"></a>Enroll a Surface Hub into MDM
You can enroll your Surface Hubs using bulk, manual, or automatic enrollment.

### Bulk enrollment
**Per configurare la registrazione in blocco**
- Surface Hub supporta il [CSP Provisioning](https://msdn.microsoft.com/library/windows/hardware/mt203665.aspx) per la registrazione in blocco in MDM. Per altre informazioni, vedi [Registrazione in blocco in Windows10](https://msdn.microsoft.com/library/windows/hardware/mt613115.aspx).<br>
--OR--
- If you have an on-premises Microsoft Endpoint Configuration Manager infrastructure, see [How to bulk enroll devices with On-premises Mobile Device Management in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/mdm/deploy-use/bulk-enroll-devices-on-premises-mdm).

### Manual enrollment
**Per configurare la registrazione manuale**
1. Nel dispositivo Surface Hub apri **Impostazioni**.
2. Quando viene richiesto, digita le credenziali di amministratore del dispositivo.
3. Seleziona **Questo dispositivo** e passa a **Gestione dei dispositivi**.
4. In **Gestione dei dispositivi**, seleziona **+ Gestione dei dispositivi**.
5. Follow the instructions in the dialog to connect to your MDM provider.

### Automatic enrollment via Azure Active Directory join

Surface Hub now supports the ability to automatically enroll in Intune by joining the device to Azure Active Directory. 

First step is to set up Automatic MDM enrollment. See [Enable Windows 10 automatic enrollment](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment).

Then, when devices are setup during First-run, pick the option to join to Azure Active Directory, see [Set up admins for this device page](https://docs.microsoft.com/surface-hub/first-run-program-surface-hub#set-up-admins-for-this-device-page)

## Manage Surface Hub settings with MDM

Puoi usare MDM per gestire alcune [impostazioni del CSP SurfaceHub](#supported-surface-hub-csp-settings) e alcune [impostazioni di Windows10](#supported-windows-10-settings). Depending on the MDM provider that you use, you may set these settings using a built-in user interface, or by deploying custom SyncML. Microsoft Intune and Microsoft Endpoint Configuration Manager provide built-in experiences to help create policy templates for Surface Hub. Refer to documentation from your MDM provider to learn how to create and deploy SyncML.

### Impostazioni supportate del CSP SurfaceHub

You can configure the Surface Hub settings in the following table using MDM. The table identifies if the setting is supported with Microsoft Intune, Microsoft Endpoint Configuration Manager, or SyncML.

For more information, see [SurfaceHub configuration service provider](https://msdn.microsoft.com/library/windows/hardware/mt608323). 


|                                     Impostazione                                      |                                                    Nodo nel CSP SurfaceHub                                                    |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|----------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|                                Orario di manutenzione                                 |                        MaintenanceHoursSimple/Hours/StartTime <br> MaintenanceHoursSimple/Hours/Duration                         |                       Sì                        |                       Sì                       |             Sì             |
|              Attivazione automatica dello schermo quando vengono usati sensori di movimento               |                                                 InBoxApps/Welcome/AutoWakeScreen                                                 |                       Sì                        |                       Sì                       |             Sì             |
|                      Richiesta di un PIN per la proiezione wireless                       |                                             InBoxApps/WirelessProjection/PINRequired                                             |                       Sì                        |                       Sì                       |             Sì             |
|                            Abilitazione della proiezione wireless                            |                                               InBoxApps/WirelessProjection/Enabled                                               |                       Sì                        | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                 Canale Miracast da usare per la proiezione wireless                  |                                               InBoxApps/WirelessProjection/Channel                                               |                       Sì                        | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|              Connessione all'area di lavoro di Operations Management Suite               |                                         MOMAgent/WorkspaceID <br> MOMAgent/WorkspaceKey                                          |                       Sì                        | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                         Immagine di sfondo della schermata iniziale                          |                                             InBoxApps/Welcome/CurrentBackgroundPath                                              |                       Sì                        | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Visualizzazione delle informazioni sulla riunione nella schermata iniziale                |                                               InBoxApps/Welcome/MeetingInfoOption                                                |                       Sì                        | Yes.<br> [Use a custom setting.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager |             Yes             |
|                      Nome descrittivo per la proiezione wireless                       |                                                     Properties/FriendlyName                                                      | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Yes             |
|                   Device account                                                 | DeviceAccount/*`<name_of_policy>`* <br> Vedi [CSP SurfaceHub](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx). |                        No                        |                       No                        |             Sì             |
|                               Specificare il dominio di Skype                               |                                              InBoxApps/SkypeForBusiness/DomainName                                               |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Avvio automatico dell'app Connetti quando viene avviata la proiezione               |                                                   InBoxApps/Connect/AutoLaunch                                                   |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                                Volume predefinito set                                |                                                     Proprietà/DefaultVolume                                                     |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                                Timeout dello schermo set                                |                                                     Proprietà/ScreenTimeout                                                     |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                               Impostare il timeout della sessione                                |                                                    Proprietà/SessionTimeout                                                     |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                                Timeout di sospensione del set                                 |                                                     Proprietà/SleepTimeout                                                      |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                   Consenti alla sessione di essere ripristinata dopo l'inattività dello schermo                   |                                                  Proprietà/AllowSessionResume                                                   |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|             Consentire l'account del dispositivo da usare per l'autenticazione proxy             |                                                  Proprietà/AllowAutoProxyAuth                                                   |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
| Disabilitare la finestra di dialogo accesso con le riunioni pianificate invitati auto-compilazione |                                               Proprietà/DisableSignInSuggestions                                                |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|              Disabilitare la funzionalità "Le mie riunioni e i miei file" nel menu Start               |                                              Proprietà/DoNotShowMyMeetingsAndFiles                                              |                    Sì </br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                     Imposta LanProfile per autenticazione cablata 802.1x                     |                                                         Dot3/LanProfile                                                          | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                    Imposta EapUserData per autenticazione cablata 802.1x                     |                                                         Dot3/EapUserData                                                         | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

### Impostazioni di Windows 10 supportate

Oltre alle impostazioni specifiche per Surface Hub, esistono numerose impostazioni comuni a tutti i dispositivi Windows10. Queste impostazioni sono definite nelle [Informazioni di riferimento sui provider di servizi di configurazione (CSP)](https://docs.microsoft.com/windows/client-management/mdm/configuration-service-provider-reference). 

Le tabelle seguenti includono info sulle impostazioni di Windows10 convalidate con Surface Hub. There is a table with settings for these areas: security, browser, Windows Updates, Windows Defender, remote reboot, certificates, and logs. Each table identifies if the setting is supported with Microsoft Intune, Microsoft Endpoint Configuration Manager, or SyncML.

#### Security settings

|      Impostazione       |                                            Dettagli                                             |                                                                          Riferimento sui provider di servizi di configurazione (CSP)                                                                           |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|--------------------|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|  Consenti Bluetooth   |                      Mantieni abilitata questa impostazione per supportare le periferiche Bluetooth.                       |                   [Connectivity/AllowBluetooth](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Connectivity_AllowBluetooth)                   |                    Sì. <br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
| Criteri Bluetooth | Usa questa impostazione per specificare il nome del dispositivo Bluetooth e bloccare annunci, individuazione e associazione automatica. |                     Bluetooth/*`<name of policy>`* <br> Vedi [CSP Policy](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)                      |                    Sì. <br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|    Consenti fotocamera    |                           Mantieni abilitata questa impostazione per Skype for Business.                            |                            [Fotocamera/Consenti fotocamera](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Camera_AllowCamera)                            |                    Sì. <br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|   Consenti posizione   |                        Mantieni abilitata questa impostazione per supportare app come Mappe.                         |                          [System/AllowLocation](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#System_AllowLocation)                          |                   Sì. <br> .                    | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|  Consenti telemetria   |                    Mantieni abilitata questa impostazione per consentire a Microsoft di migliorare Surface Hub.                    |                         [System/AllowTelemetry](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#System_AllowTelemetry)                         |                    Sì. <br>                     | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|  Consenti unità USB  |                     Tenere questa opzione abilitata per il supporto di unità USB sul dispositivo Surface Hub                     | [Sistema/AllowStorageCard](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/policy-configuration-service-provider#system-allowstoragecard) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows. 

#### Impostazioni relative al browser

|                          Impostazione                          |                                                                        Dettagli                                                                        |                                                                             Riferimento sui provider di servizi di configurazione (CSP)                                                                              |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|-----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|                         Pagine iniziali                         |                                               Usa questa impostazione per configurare le pagine iniziali predefinite in Microsoft Edge.                                               |                                [Browser/Homepages](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_Homepages)                                | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                       Consenti cookie                       |                    Surface Hub elimina automaticamente i cookie alla fine di una sessione. Usa questa impostazione per bloccare i cookie all'interno di una sessione.                     |                             [Browser/AllowCookies](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowCookies)                             | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                   Consenti strumenti di sviluppo                   |                                                   Usa questa impostazione per impedire agli utenti di usare gli strumenti di sviluppo F12                                                   |                      [Browser/AllowDeveloperTools](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowDeveloperTools)                      | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                    Consenti Do Not Track                     |                                                          Usa questa impostazione per consentire le intestazioni Do Not Track.                                                          |                          [Browser/AllowDoNotTrack](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowDoNotTrack)                          | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                       Consenti popup                       |                                                         Usa questa impostazione per bloccare le finestre popup del browser.                                                          |                              [Browser/AllowPopups](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowPopups)                              | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|                 Consenti suggerimenti per la ricerca                  |                                                  Usa questa impostazione per bloccare i suggerimenti per la ricerca nella barra degli indirizzi.                                                  |       [Browser/AllowSearchSuggestionsinAddressBar](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowSearchSuggestionsinAddressBar)       | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Yes             |
|                     Allow Windows Defender SmartScreen                     |                                                       Keep this enabled to turn on Windows Defender SmartScreen.                                                       |                         [Browser/AllowSmartScreen](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_AllowSmartScreen)                         | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Yes             |
| Prevent ignoring Windows Defender SmartScreen warnings for websites |     For extra security, use to stop users from ignoring Windows Defender SmartScreen warnings and block them from accessing potentially malicious websites.     |         [Browser/PreventSmartScreenPromptOverride](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_PreventSmartScreenPromptOverride)         | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Yes             |
|  Prevent ignoring Windows Defender SmartScreen warnings for files   | For extra security, use to stop users from ignoring Windows Defender SmartScreen warnings and block them from downloading unverified files from Microsoft Edge. | [Browser/PreventSmartScreenPromptOverrideForFiles](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Browser_PreventSmartScreenPromptOverrideForFiles) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Impostazioni di Windows Update

|                      Impostazione                      |                                                                                                           Dettagli                                                                                                            |                                                                    Riferimento sui provider di servizi di configurazione (CSP)                                                                    |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Use Current Branch or Current Branch for Business |                                                       Usa questa impostazione per configurare Windows Update for Business - vedi [Aggiornamenti di Windows](manage-windows-updates-for-surface-hub.md).                                                       |            [Update/BranchReadinessLevel](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_BranchReadinessLevel)             | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Rinvia aggiornamenti delle funzionalità               |                                                                                                          Vedere sopra.                                                                                                          | [Update/DeferFeatureUpdatesPeriodInDays](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_DeferFeatureUpdatesPeriodInDays) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Rinvia aggiornamenti qualitativi               |                                                                                                          Vedere sopra.                                                                                                          | [Update/DeferQualityUpdatesPeriodInDays](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_DeferQualityUpdatesPeriodInDays)  | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Sospendi gli aggiornamenti delle funzionalità               |                                                                                                          Vedere sopra.                                                                                                          |             [Update/PauseFeatureUpdates](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_PauseFeatureUpdates)              | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Sospendi gli aggiornamenti qualitativi               |                                                                                                          Vedere sopra.                                                                                                          |             [Update/PauseQualityUpdates](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_PauseQualityUpdates)              | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|           Configura il dispositivo per l'uso di WSUS            |                                            Usa questa impostazione per connettere il tuo dispositivo Surface Hub a WSUS invece che a Windows Update - vedi [Aggiornamenti di Windows](manage-windows-updates-for-surface-hub.md).                                             |                [Update/UpdateServiceUrl](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_UpdateServiceUrl)                 | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|               Ottimizzazione recapito               | Usa la condivisione del contenuto peer-to-peer per ridurre i problemi di larghezza di banda durante gli aggiornamenti. Vedi [Configurare Ottimizzazione recapito per Windows 10](https://technet.microsoft.com/itpro/windows/manage/waas-delivery-optimization) per altri dettagli. |         DeliveryOptimization/*`<name of policy>`* <br> Vedi [CSP Policy](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx)          | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Impostazioni relative a Windows Defender

|      Impostazione      |                                              Dettagli                                               |                                                     Riferimento sui provider di servizi di configurazione (CSP)                                                      |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|-------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Criteri di Defender |            Usa queste impostazioni per configurare varie impostazioni relative a Defender, inclusa l'ora pianificata per l'analisi.            | Defender/*`<name of policy>`* <br> Vedere [Criteri CSP](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
|  Defender status  | Use to initiate a Defender scan, force a Security intelligence update, query any threats detected. |                   [Defender CSP](https://msdn.microsoft.com/library/windows/hardware/mt187856.aspx)                    |                       Yes                        |                       Sì                       |             Sì             |

\*Le impostazioni supportate da SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Avvio remoto

|                       Impostazione                        |                                                          Dettagli                                                          |                                                             Riferimento sui provider di servizi di configurazione (CSP)                                                             |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
|            Riavvia il dispositivo immediatamente             | Usa questa impostazione in combinazione con OMS per ridurre al minimo i costi di supporto - vedi [Monitorare il dispositivo Microsoft Surface Hub](monitor-surface-hub.md). |        ./Vendor/MSFT/Reboot/RebootNow <br> Vedi [CSP Reboot](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx)        |                       Sì                        |                       No                        |             Sì             |
|    Riavvia il dispositivo nella data e nell'ora pianificate    |                                                        Vedi sopra.                                                         |     ./Vendor/MSFT/Reboot/Schedule/Single <br> Vedere [Riavvio CSP](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx)     | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |
| Riavvia il dispositivo ogni giorno nella data e nell'ora pianificate |                                                        Vedi sopra.                                                         | ./Vendor/MSFT/Reboot/Schedule/DailyRecurrent <br> Vedi [CSP Reboot](https://msdn.microsoft.com/library/windows/hardware/mt720802.aspx) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Installa i certificati

|             Impostazione             |                           Dettagli                            |                                           Riferimento sui provider di servizi di configurazione (CSP)                                            |                                                         Supportata con<br>Intune?                                                          |                                                                  Supportata con<br>Configuration Manager?                                                                  | Supportata con<br>SyncML\*? |
|---------------------------------|--------------------------------------------------------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| Installa certificati di CA attendibili | Usa questa impostazione per distribuire certificati radice trusted e certificati di CA intermedia. | [RootCATrustedCertificates CSP](https://msdn.microsoft.com/library/windows/hardware/dn904970.aspx) | Sì. <br> Vedi l'argomento relativo a come [configurare i profili certificato di Intune](https://docs.microsoft.com/intune/deploy-use/configure-intune-certificate-profiles). | Yes. <br> See [How to create certificate profiles in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/protect/deploy-use/create-certificate-profiles). |             Yes             |

<!--
| Install client certificates  | Use to deploy Personal Information Exchange (.pfx, .p12) certificates. | [ClientCertificateInstall CSP](https://msdn.microsoft.com/library/windows/hardware/dn920023.aspx) | Yes. <br> See [How to Create and Deploy PFX Certificate Profiles in Intune Standalone](https://blogs.technet.microsoft.com/karanrustagi/2016/03/16/want-to-push-a-certificate-to-device-but-cant-use-ndes-continue-reading/). | Yes. <br> See [How to create PFX certificate profiles in Microsoft Endpoint Configuration Manager](https://docs.microsoft.com/configmgr/protect/deploy-use/create-pfx-certificate-profiles). | Yes |
-->
\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Raccogli log

|     Impostazione      |                      Dettagli                       |                                     Riferimento sui provider di servizi di configurazione (CSP)                                      | Supportata con<br>Intune? | Supportata con<br>Configuration Manager? | Supportata con<br>SyncML\*? |
|------------------|----------------------------------------------------|----------------------------------------------------------------------------------------|---------------------------|------------------------------------------|-----------------------------|
| Collect ETW logs | Usa questa impostazione per la raccolta remota dei log ETW da Surface Hub. | [CSP DiagnosticLog](https://msdn.microsoft.com/library/windows/hardware/mt219118.aspx) |            No             |                    No                    |             Sì             |

<!--
| Collect security auditing logs | Use to remotely collect security auditing logs from Surface Hub. | SecurityAuditing node in [Reporting CSP](https://msdn.microsoft.com/library/windows/hardware/mt608321.aspx) | No | No | Yes |-->
\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Impostare i criteri QoS (Quality of Service) di rete

|        Impostazione         |                                                            Dettagli                                                             |                                                    Riferimento sui provider di servizi di configurazione (CSP)                                                     |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Set Network QoS Policy | Consente di impostare un criterio QoS per eseguire una serie di azioni sul traffico di rete. Ciò è utile per assegnare la priorità ai pacchetti di rete di Skype. | [CSP NetworkQoSPolicy](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkqospolicy-csp) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Configurare il proxy di rete

|      Impostazione      |                               Dettagli                               |                                                Riferimento sui provider di servizi di configurazione (CSP)                                                 |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|-------------------|---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Set Network proxy | Il CSP NetworkProxy viene utilizzato per configurare un server proxy per le connessioni Ethernet e Wi-Fi. | [CSP NetworkProxy](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/networkproxy-csp) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

#### Configura il menu Start

|       Impostazione        |                                                                       Dettagli                                                                        |                                                        Riferimento sui provider di servizi di configurazione (CSP)                                                         |            Supportata con<br>Intune?             |    Supportata con<br>Configuration Manager?     | Supportata con<br>SyncML\*? |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|-------------------------------------------------|-----------------------------|
| Configure Start menu | Utilizza per configurare le app visualizzate nel menu Start. Per altre informazioni, vedi [Configurare il menu Start di Surface Hub](surface-hub-start-menu.md) . | [CSP criteri: Start/StartLayout](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-start#start-startlayout) | Sì <br> [Usa un criterio personalizzato.](#example-manage-surface-hub-settings-with-microsoft-intune) | Sì.<br> [Usa un'impostazione personalizzata.](#example-manage-surface-hub-settings-with-microsoft-endpoint-configuration-manager) |             Sì             |

\*Le impostazioni supportate con SyncML possono anche essere configurate in un pacchetto di provisioning di Progettazione configurazione di Windows.

### Generate OMA URIs for settings 
You need to use a setting's OMA URI to create a custom policy in Intune, or a custom setting in Microsoft Endpoint Configuration Manager.

**To generate the OMA URI for any setting in the CSP documentation**
1. Nella documentazione del CSP individua il nodo radice del CSP. In genere ha questo aspetto `./Vendor/MSFT/<name of CSP>` <br>
*Ad esempio, il nodo radice del [CSP SurfaceHub](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx) è `./Vendor/MSFT/SurfaceHub`.*
2. Identifica il percorso del nodo per l'impostazione che vuoi usare. <br>
*Ad esempio, il percorso del nodo per l'impostazione per abilitare la proiezione wireless è `InBoxApps/WirelessProjection/Enabled`.*
3. Aggiungi il percorso del nodo al nodo radice per generare l'URI OMA. <br>
*L'URI OMA per l'impostazione per abilitare la proiezione wireless è ad esempio `./Vendor/MSFT/SurfaceHub/InBoxApps/WirelessProjection/Enabled`.*

Anche il tipo di dati è indicato nella documentazione del CSP. I tipi di dati più comuni sono:
- char (stringa)
- int (intero)
- bool (booleano)


## Esempio: Gestire le impostazioni di Surface Hub con Microsoft Intune

Puoi usare Microsoft Intune per gestire le impostazioni di Surface Hub. Per le impostazioni personalizzate, segui le istruzioni in [Come configurare le impostazioni dei dispositivi personalizzati in Microsoft Intune](https://docs.microsoft.com/intune/custom-settings-configure). For **Platform**, select **Windows 10 and later**, and in **Profile type**, select **Device restrictions (Windows 10 Team)**.



## Example: Manage Surface Hub settings with Microsoft Endpoint Configuration Manager
Configuration Manager supports managing modern devices that do not require the Configuration Manager client to manage them, including Surface Hub. If you already use Configuration Manager to manage other devices in your organization, you can continue to use the Configuration Manager console as your single location for managing Surface Hubs.

> [!NOTE]
> These instructions are based on the current branch of Configuration Manager.

**To create a configuration item for Surface Hub settings**

1. Nell'area **Asset e conformità** della console di Configuration Manager fai clic su **Panoramica** > **Impostazioni di conformità** > **Elementi di configurazione**.
2. Nella scheda **Home** fai clic su **Crea elemento di configurazione** nel gruppo **Crea**.
3. Nella pagina **Generale** della Creazione guidata dell'elemento di configurazione specifica un nome e una descrizione facoltativa per l'elemento di configurazione.
4. In **Impostazioni per i dispositivi gestiti senza il client Configuration Manager** seleziona **Windows 8.1 e Windows 10**, quindi fai clic su **Avanti**.

    ![Esempio di interfaccia utente](images/configmgr-create.png)
5. Nella pagina **Piattaforme supportate** espandi **Windows 10** e seleziona **Tutti i dispositivi Windows 10 Team e versioni successive**. Deseleziona le altre piattaforme Windows e quindi fai clic su **Avanti**.

    ![Selezione della piattaforma](images/configmgr-platform.png)
7. Nella pagina **Impostazioni dispositivo**, in **Gruppi di impostazioni dispositivo**, seleziona **Windows10 Team**.


8. Nella pagina **Windows10 Team** configura le impostazioni necessarie.

    ![Windows 10 Team](images/configmgr-team.png)
9. Dovrai creare impostazioni personalizzate per gestire le impostazioni non disponibili nella pagina Windows10 Team. Nella pagina **Impostazioni dispositivo** seleziona la casella di controllo**Configura impostazioni aggiuntive non presenti nei gruppi di impostazioni predefinite**.

    ![Impostazioni aggiuntive](images/configmgr-additional.png)
10. Nella pagina **Impostazioni aggiuntive** fai clic su **Aggiungi**.
11. Nella finestra di dialogo **Sfoglia impostazioni** fai clic su **Crea impostazione**.
12. Nella finestra di dialogo **Crea impostazione**, nella scheda **Generale**, specifica un nome e una descrizione facoltativa per l'impostazione personalizzata.
13. In **Tipo di impostazione** seleziona **URI OMA**.
14. Compila il modulo per creare una nuova impostazione e quindi fai clic su **OK**.

    ![Impostazione URI OMA](images/configmgr-oma-uri.png)
15. Nella finestra di dialogo **Sfoglia impostazioni**, in **Impostazioni disponibili** seleziona la nuova impostazione creata e quindi fai clic su **Seleziona**.
16. Nella finestra di dialogo **Crea regola** compila il modulo per specificare una regola per l'impostazione e quindi fai clic su **OK**.
17. Ripeti i passaggi da 9 a 15 per ogni impostazione personalizzata che vuoi aggiungere all'elemento di configurazione.
18. Al termine, nella finestra di dialogo **Sfoglia impostazioni** fai clic su **Chiudi**.
19. Completa la procedura guidata. <br> You can view the new configuration item in the **Configuration Items** node of the **Assets and Compliance** workspace.

For more information, see [Create configuration items for Windows 8.1 and Windows 10 devices managed without the Microsoft Endpoint Configuration Manager client](https://docs.microsoft.com/configmgr/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).

## Related topics

[Gestire Microsoft Surface Hub](manage-surface-hub.md)












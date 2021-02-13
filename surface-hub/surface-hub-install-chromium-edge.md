---
title: Installare e configurare il nuovo Microsoft Edge in Surface Hub
description: Installare e configurare il nuovo Microsoft Edge in Surface Hub.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/10/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 2bc11fb18137ce21cba27368e0c12bbb9e73a4c2
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327310"
---
# Installare e configurare il nuovo Microsoft Edge in Surface Hub

Windows 10 Team 2020 Update supporta il nuovo Microsoft Edge basato su Chromium (versione 85 e successive) come browser consigliato per Surface Hub 2S e Surface Hub (v1). Questo articolo spiega come installare il browser usando uno dei tre metodi seguenti: un pacchetto di provisioning, Microsoft Intune o un provider mdm (Mobile Device Management) di terze parti.

> [!IMPORTANT]
> Per impostazione predefinita, i dispositivi Surface Hub sono preinstallati con Microsoft Edge Legacy (versione 44). Dopo aver installato [l'aggiornamento 2020,](surface-hub-2020-update.md)è consigliabile passare al nuovo browser Microsoft Edge; Il supporto [per Microsoft Edge Legacy](https://support.microsoft.com/microsoft-edge/what-is-microsoft-edge-legacy-3e779e55-4c55-08e6-ecc8-2333768c0fb0) terminerà il 9 marzo 2021.

## Installare Microsoft Edge con un pacchetto di provisioning

1. Da un PC scarica il pacchetto di [provisioning di Microsoft Edge](https://aka.ms/HubEdge) (MicrosoftEdgeInstaller.ppkg) nella cartella radice di un'unità USB.
2. Inserisci l'unità USB in Surface Hub.
3. Da Surface Hub apri **Impostazioni** e immetti le credenziali di amministratore quando richiesto.
4. Vai su **Surface Hub** > **Gestione dei dispositivi**. In **Pacchetti di provisioning** seleziona **Aggiungi o rimuovi un pacchetto di provisioning**.
5. Seleziona **Aggiungi un pacchetto**.
6. Scegli il pacchetto di provisioning di Microsoft Edge e seleziona **Aggiungi.**
7. Verrà visualizzato un riepilogo delle modifiche applicate al pacchetto di provisioning. Seleziona **Sì, aggiungilo**.
8. Attendere il completamento dell'installazione di Microsoft Edge. Dopo l'installazione, passa al menu Start di Surface Hub per accedere al nuovo Microsoft Edge.              

> [!NOTE]
> Se è disponibile una versione più recente di Microsoft Edge, verrà aggiornata automaticamente.
 
## Installare Microsoft Edge con Intune
 
> [!NOTE]
> Il dispositivo Surface Hub deve essere registrato e gestito con Intune. Per altre informazioni, vedi [Gestire Surface Hub 2S con Microsoft Intune.](https://docs.microsoft.com/surface-hub/surface-hub-2s-manage-intune)
 

1. [Scaricare il programma di installazione di Microsoft Edge.](https://www.microsoft.com/edge/business/download)
    - Usare la versione corrente del [canale Stable](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows a 64 bit**
2. [Aggiungere il programma di installazione di Microsoft Edge come app line-of-business a Microsoft Intune.](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows)
    - Se scegli di usare Microsoft Edge Update per gestire gli aggiornamenti automatici di Microsoft Edge, assicurati di configurare l'impostazione Ignora versione **app** nel riquadro **informazioni app.** Quando si imposta questa impostazione su **Sì,** Microsoft Intune non applica la versione dell'app installata nel dispositivo Surface Hub.

## Installare Microsoft Edge con un provider MDM di terze parti

1. [Scaricare il programma di installazione di Microsoft Edge da Microsoft](https://www.microsoft.com/edge/business/download).
    - Usare la versione corrente del [canale Stable](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows a 64 bit**
2. Installare il programma di installazione di Microsoft Edge in un percorso ospitato, ad esempio una condivisione file locale (\\server\share\MicrosoftEdgeEnterpriseX64.msi). Il dispositivo Surface Hub deve disporre dell'autorizzazione per accedere alla posizione ospitata.
3. Usa il provider di servizi di configurazione [(CSP) EnterpriseDesktopAppManagement tramite](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp) il provider MDM per installare Microsoft Edge.

## Configurare Microsoft Edge

### Criteri predefiniti di Microsoft Edge per Surface Hub

Microsoft Edge è preconfigurato con le impostazioni dei criteri seguenti per offrire un'esperienza ottimizzata per Surface Hub.
 
> [!TIP]
> È consigliabile mantenere il valore predefinito per queste impostazioni dei criteri.
 

| Impostazione dei criteri                                                                                                   | Esperienza consigliata                                                                                                                                                                                                                                               | Valore predefinito |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Non importare automaticamente i tipi di dati e le impostazioni dalla versione legacy di Microsoft Edge. In questo modo si evita di modificare i profili degli utenti connessi con le impostazioni condivise da Surface Hub.                                                                                                 | 4                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | Consenti ai processi di Microsoft Edge di continuare a essere eseguiti in background anche dopo la chiusura dell'ultima finestra del browser, consentendo un accesso più rapido alle app Web durante una sessione.                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Non consentire agli utenti di creare nuovi profili in Microsoft Edge. Ciò semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Consente a un solo utente di accedere a Microsoft Edge. Ciò semplifica l'esplorazione e l'esperienza di accesso                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | Consente agli utenti di utilizzare single Sign-On (SSO) in Microsoft Edge. Quando un utente è connesso a Surface Hub, le credenziali possono fluire nei siti Web supportati senza richiedere la nuova autenticazione.  | 1                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | Impedisce agli utenti non amministratori di installare nuove estensioni in Microsoft Edge. Per configurare un elenco di estensioni da installare per impostazione predefinita, utilizzare [ExtensionInstallForcelist.](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist) | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | Nasconde l'esperienza di prima esecuzione e la schermata iniziale che normalmente viene visualizzata quando gli utenti eseguono Microsoft Edge per la prima volta. Poiché Surface Hub è un dispositivo condiviso, questo semplifica l'esperienza utente.                                                                      | 1                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | Disabilita la modalità InPrivate. Poiché Termina sessione cancella già i dati di esplorazione, questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | Mostra l'esperienza dei feed di Office 365 nelle nuove schede. Quando un utente è connesso a Surface Hub, questo consente di accedere rapidamente ai file e al contenuto in Office 365.                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | Quando un utente ha eseguito l'accesso a Surface Hub, verrà creato un profilo non rimovibile con l'account dell'organizzazione. Ciò semplifica l'esperienza single Sign-On (SSO).                                                                                                 | 1                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | Disabilita la stampa in Microsoft Edge. Surface Hub non supporta la stampa.                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Consente a Microsoft Edge di autenticare in modo proattivo gli utenti connessi con i servizi Microsoft. Ciò semplifica l'esperienza single Sign-On (SSO).                                                                                                                         | 1                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | Salva automaticamente i file nella cartella Download, anziché chiedere agli utenti dove salvarlo. Questo semplifica l'esperienza di esplorazione.                                                                                                                             | 0                 |

> [!IMPORTANT]
> Le app Web progressive distribuibili non sono attualmente supportate nel sistema operativo Windows 10 Team.  Nota anche che l'impostazione dei criteri di Microsoft Edge [WebAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist) non è supportata in Surface Hub. 

### Configurare le impostazioni dei criteri di Microsoft Edge

Usare [i criteri del browser Microsoft Edge](https://docs.microsoft.com/deployedge/microsoft-edge-policies) per configurare le impostazioni del browser in Microsoft Edge. Questi criteri possono essere applicati utilizzando:

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune),
- Il provider di gestione dei dispositivi mobili [(MDM, Mobile Device Management) preferito che supporta l'inserimento ADMX](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)oppure
- [Provisioning dei pacchetti con l'inserimento ADMX in Progettazione configurazione di Windows.](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion)

 
### Configurare gli aggiornamenti di Microsoft Edge

Per impostazione predefinita, Microsoft Edge viene aggiornato automaticamente. Usare [i criteri di aggiornamento di Microsoft Edge](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies) per configurare le impostazioni per Microsoft Edge Update.
Tieni presente che Surface Hub non supporta i criteri di aggiornamento di Microsoft Edge seguenti:

- **Allowsxs:** in Surface Hub, il canale Stable di Microsoft Edge sostituisce sempre la versione legacy di Microsoft Edge.
- **CreateDesktopShortcut:** Surface Hub non usa i tasti di scelta rapida del desktop.

> [!TIP]
>  Microsoft Edge richiede la connettività a Internet per supportare le funzionalità. Assicurarsi che gli [URL di dominio necessari](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) siano aggiunti all'elenco Consenti per garantire le comunicazioni tramite firewall e altri meccanismi di sicurezza.

## Collegamenti correlati

- [Documentazione di Microsoft Edge](https://docs.microsoft.com/microsoft-edge/)


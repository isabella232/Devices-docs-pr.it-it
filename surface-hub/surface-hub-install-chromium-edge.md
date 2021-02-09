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
ms.date: 02/08/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 74ae47e80447f89753110c52a49daf649478dd50
ms.sourcegitcommit: 7029e80d9ca1a3de5c336cf662e566ed4b6b3e7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/09/2021
ms.locfileid: "11319170"
---
# Installare e configurare il nuovo Microsoft Edge in Surface Hub

Windows 10 team 2020 Update supporta il nuovo Microsoft Edge basato su Chromium (versione 85 e successive) come browser consigliato per Surface Hub 2S e Surface Hub (V1). Questo articolo spiega come installare il browser usando uno dei tre metodi seguenti: un pacchetto di provisioning, Microsoft Intune o un provider di gestione di dispositivi mobili (MDM) di terze parti.

> [!IMPORTANT]
> Per impostazione predefinita, i dispositivi Surface Hub sono preinstallati con Microsoft Edge Legacy (versione 44). Dopo l'installazione dell' [aggiornamento di 2020](surface-hub-2020-update.md), è consigliabile passare al nuovo browser Microsoft Edge; il supporto per [legacy Microsoft Edge](https://support.microsoft.com/microsoft-edge/what-is-microsoft-edge-legacy-3e779e55-4c55-08e6-ecc8-2333768c0fb0) terminerà il 9 marzo 2021.

## Installare Microsoft Edge usando un pacchetto di provisioning

1. Da un PC scaricare il [pacchetto Microsoft Edge provisioning](https://aka.ms/HubEdge) (MicrosoftEdgeInstaller. ppkg) nella cartella radice di un'unità USB.
2. Inserire l'unità USB in Surface Hub.
3. In Surface Hub aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
4. Vai su **Surface Hub** > **Gestione dei dispositivi**. In **Pacchetti di provisioning** seleziona **Aggiungi o rimuovi un pacchetto di provisioning**.
5. Seleziona **Aggiungi un pacchetto**.
6. Scegliere il pacchetto Microsoft Edge provisioning e selezionare **Aggiungi**.
7. Verrà visualizzato un riepilogo delle modifiche apportate al pacchetto di provisioning. Seleziona **Sì, aggiungilo**.
8. Attendere il completamento dell'installazione di Microsoft Edge. Una volta installato, passare al menu Start di Surface hub per accedere al nuovo Microsoft Edge.              

> [!NOTE]
> Se è disponibile una versione più recente di Microsoft Edge, verrà aggiornata automaticamente.
 
## Installare Microsoft Edge tramite Intune
 
> [!NOTE]
> Il dispositivo Surface hub deve essere registrato e gestito tramite Intune. Per altre informazioni, vedere [gestire Surface Hub 2S con Microsoft Intune](https://docs.microsoft.com/surface-hub/surface-hub-2s-manage-intune).
 

1. [Scaricare il programma di installazione Microsoft Edge](https://www.microsoft.com/edge/business/download).
    - Usare la versione corrente da [Stable Channel](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows 64 bit**
2. [Aggiungere il programma di installazione Microsoft Edge come app line-of-business a Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows).
    - Se si sceglie di usare Microsoft Edge Update per gestire gli aggiornamenti automatici di Microsoft Edge, assicurarsi di configurare la **versione dell'app ignore** impostando il riquadro **informazioni app** . Quando si cambia questa impostazione su **Sì**, Microsoft Intune non applica la versione dell'app installata nel dispositivo Surface Hub.

## Installare Microsoft Edge usando il provider MDM di terze parti

1. [Scaricare il programma di installazione Microsoft Edge da Microsoft](https://www.microsoft.com/edge/business/download).
    - Usare la versione corrente da [Stable Channel](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows 64 bit**
2. Organizzare il programma di installazione Microsoft Edge in una posizione ospitata, ad esempio una condivisione file locale (\\server\share\MicrosoftEdgeEnterpriseX64.msi). Il dispositivo Surface hub deve avere l'autorizzazione per accedere alla posizione ospitata.
3. Usa il [provider di servizi di configurazione di EnterpriseDesktopAppManagement (CSP)](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp) tramite il provider MDM per installare Microsoft Edge.

## Configurare Microsoft Edge

### Criteri Microsoft Edge predefiniti per Surface Hub

Microsoft Edge è preconfigurato con il criterio seguente setttings per ottenere un'esperienza ottimizzata per Surface Hub.
 
> [!TIP]
> È consigliabile mantenere il valore predefinito per queste impostazioni dei criteri.
 

| Impostazione dei criteri                                                                                                   | Esperienza consigliata                                                                                                                                                                                                                                               | Valore predefinito |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Non importare automaticamente i tipi di dati e le impostazioni dall'legacy Microsoft Edge. In questo articolo viene evitato di modificare i profili degli utenti con accesso condiviso dall'hub Surface.                                                                                                 | 4                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | Consenti ai processi Microsoft Edge di restare in funzione in background anche dopo la chiusura dell'ultima finestra del browser, consentendo un accesso più rapido alle app Web durante una sessione.                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Non consentire agli utenti di creare nuovi profili in Microsoft Edge. Questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Consente a un solo utente di accedere a Microsoft Edge. Questo semplifica l'esplorazione e l'esperienza di accesso                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | Consente agli utenti di utilizzare Single Sign-On (SSO) in Microsoft Edge. Quando un utente ha eseguito l'accesso a Surface Hub, le proprie credenziali possono fluire in siti Web supportati senza richiedere la nuova autenticazione.  | 1                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | Impedisce agli utenti non amministratori di installare nuove estensioni in Microsoft Edge. Per configurare un elenco di estensioni da installare per impostazione predefinita, usare [ExtensionInstallForcelist](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist). | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | Nasconde la prima esperienza di esecuzione e la schermata iniziale che viene normalmente visualizzata quando gli utenti eseguono Microsoft Edge per la prima volta. Dato che Surface Hub è un dispositivo condiviso, questo semplifica l'esperienza utente.                                                                      | 1                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | Disabilita la modalità InPrivate. Poiché la sessione finale Cancella già la visualizzazione dei dati, questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | Mostra l'esperienza di feed di Office 365 nelle nuove pagine della scheda. Quando un utente ha eseguito l'accesso a Surface Hub, questo consente di accedere rapidamente ai file e ai contenuti di Office 365.                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | Quando un utente ha eseguito l'accesso a Surface Hub, verrà creato un profilo non rimovibile usando il proprio account aziendale. Questo semplifica l'esperienza single Sign-On (SSO).                                                                                                 | 1                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | Disabilita la stampa in Microsoft Edge. Surface Hub non supporta la stampa.                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Consente a Microsoft Edge di autenticare in modo proattivo gli utenti connessi con l'accesso con i servizi Microsoft. Questo semplifica l'esperienza single Sign-On (SSO).                                                                                                                         | 1                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | Salva automaticamente i file nella cartella download, invece di chiedere agli utenti dove salvare il file. Questo semplifica l'esperienza di esplorazione.                                                                                                                             | 0                 |

> [!IMPORTANT]
> Le app Web progressive distribuibili (PWAs) non sono attualmente supportate nel sistema operativo Windows 10 team.  Si noti inoltre che l'impostazione dei criteri Microsoft Edge [WebAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist) non è supportata in Surface Hub. 

### Configurare le impostazioni dei criteri Microsoft Edge

Usare i [criteri del browser Microsoft Edge](https://docs.microsoft.com/deployedge/microsoft-edge-policies) per configurare le impostazioni del browser in Microsoft Edge. Questi criteri possono essere applicati usando:

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune),
- [Il provider di gestione di dispositivi mobili (MDM) preferito che supporta l'ingestione di ADMX](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)oppure
- [Provisioning di pacchetti con l'ingestione di ADMX in Windows Configuration designer](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion).

 
### Configurare gli aggiornamenti di Microsoft Edge

Per impostazione predefinita, Microsoft Edge viene aggiornato automaticamente. Usare i [criteri di aggiornamento Microsoft Edge](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies) per configurare le impostazioni per Microsoft Edge Update.
Tieni presente che Surface Hub non supporta i seguenti criteri di aggiornamento di Microsoft Edge:

- **Allowsxs** -su Surface Hub, Microsoft Edge Stable Channel sostituisce sempre Microsoft Edge legacy.
- **CreateDesktopShortcut** -Surface Hub non usa le scelte rapide da desktop.

> [!NOTE]
>  Microsoft Edge richiede la connettività a Internet per supportare le funzionalità. Assicurarsi che gli [URL di dominio necessari](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) vengano aggiunti all'elenco Consenti per garantire le comunicazioni tramite firewall e altri meccanismi di sicurezza.
 
### Visualizzare Microsoft Edge nel menu Start di Surface Hub

Se si usa il layout del menu Start predefinito, è possibile installare il menu Start con Microsoft Edge provisioning Package per aggiungere Microsoft Edge come app bloccata.
Se si vuole applicare un layout di menu Start personalizzato, usare il codice XML seguente per aggiungere un riquadro aggiunto per Microsoft Edge.

```xml

<start:DesktopApplicationTile

DesktopApplicationLinkPath="C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe"

Size="2x2"

Row="0"

Column="0"/>
```

Per altre informazioni, vedere [configurare il menu Start di Surface Hub](https://docs.microsoft.com/surface-hub/surface-hub-start-menu).
 
> [!NOTE]
> Il nuovo Microsoft Edge non supporta i siti Web aggiunti.

## Collegamenti correlati

- [Documentazione Microsoft Edge](https://docs.microsoft.com/microsoft-edge/).


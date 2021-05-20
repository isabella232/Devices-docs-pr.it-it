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
ms.openlocfilehash: 93f76cadafe2570197fbe70db88540b6be90c3f1
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576726"
---
# <a name="install-and-configure-the-new-microsoft-edge-on-surface-hub"></a>Installare e configurare il nuovo Microsoft Edge in Surface Hub

Windows 10 Team 2020 Update supporta il nuovo Microsoft Edge basato su Chromium (versione 85 e successive) come browser consigliato per Surface Hub 2S e Surface Hub (v1). Questo articolo spiega come installare il browser usando uno dei tre metodi seguenti: un pacchetto di provisioning, un Microsoft Intune o un provider mdm (Mobile Device Management) di terze parti.

> [!IMPORTANT]
> Per impostazione predefinita, Surface Hub dispositivi sono preinstallati con Versione legacy di Microsoft Edge (versione 44). Dopo aver installato [l'aggiornamento 2020,](surface-hub-2020-update.md)è consigliabile passare al nuovo browser di Microsoft Edge; il supporto [per Versione legacy di Microsoft Edge](https://support.microsoft.com/microsoft-edge/what-is-microsoft-edge-legacy-3e779e55-4c55-08e6-ecc8-2333768c0fb0) terminerà il 9 marzo 2021.

> [!NOTE]
> Il gesto scorrimento rapido verso il basso dalla parte superiore dello schermo per uscire dalla modalità schermo intero richiede due dita con il nuovo Microsoft Edge. L'azione esci a schermo intero è disponibile anche nel menu di scelta rapida visualizzato dopo un lungo tocco.


## <a name="install-microsoft-edge-using-a-provisioning-package"></a>Installare Microsoft Edge con un pacchetto di provisioning

1. Da un PC scarica il pacchetto [Microsoft Edge provisioning](https://aka.ms/HubEdge) (MicrosoftEdgeInstaller.ppkg) nella cartella radice di un'unità USB.
2. Inserisci l'unità USB in Surface Hub.
3. Da Surface Hub, aprire **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
4. Vai su **Surface Hub** > **Gestione dei dispositivi**. In **Pacchetti di provisioning** seleziona **Aggiungi o rimuovi un pacchetto di provisioning**.
5. Seleziona **Aggiungi un pacchetto**.
6. Scegli il Microsoft Edge di provisioning e seleziona **Aggiungi**.
7. Verrà visualizzato un riepilogo delle modifiche applicate al pacchetto di provisioning. Seleziona **Sì, aggiungilo**.
8. Attendere il completamento dell Microsoft Edge installazione. Dopo l'installazione, passare al menu Surface Hub Start per accedere al nuovo Microsoft Edge.              

> [!NOTE]
> Se è disponibile una versione più recente di Microsoft Edge, verrà aggiornata automaticamente.
 
## <a name="install-microsoft-edge-using-intune"></a>Installare Microsoft Edge con Intune
 
> [!NOTE]
> Per usare questo metodo di installazione, il dispositivo Surface Hub deve essere registrato e gestito tramite Intune. Per altre informazioni, vedi [Gestire Surface Hub 2S con MDM.](manage-settings-with-mdm-for-surface-hub.md)
 

1. [Scarica il programma Microsoft Edge installer](https://www.microsoft.com/edge/business/download).
    - Usare la versione corrente del [canale Stable](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows a 64 bit**
2. [Aggiungi il Microsoft Edge di installazione come app line-of-business per Microsoft Intune](https://docs.microsoft.com/mem/intune/apps/lob-apps-windows).
    - Se scegli di usare Microsoft Edge Update per gestire gli aggiornamenti automatici Microsoft Edge, assicurati di configurare l'impostazione Ignora versione **app** nel riquadro **Informazioni app.** Quando si imposta questa impostazione su **Sì,** Microsoft Intune non verrà applicata la versione dell'app installata nel Surface Hub dispositivo.

## <a name="install-microsoft-edge-using-third-party-mdm-provider"></a>Installare Microsoft Edge provider MDM di terze parti

1. [Scaricare il Microsoft Edge di installazione da Microsoft](https://www.microsoft.com/edge/business/download).
    - Usare la versione corrente del [canale Stable](https://docs.microsoft.com/deployedge/microsoft-edge-channels) **(versione 85)**
    - Scegliere **Windows a 64 bit**
2. Eseguire il programma Microsoft Edge programma di installazione in una posizione ospitata, ad esempio una condivisione file locale (\\server\share\MicrosoftEdgeEnterpriseX64.msi). Il Surface Hub deve disporre dell'autorizzazione per accedere alla posizione ospitata.
3. Usa [EnterpriseDesktopAppManagement Configuration Service Provider (CSP)](https://docs.microsoft.com/windows/client-management/mdm/enterprisedesktopappmanagement-csp) tramite il provider MDM per installare Microsoft Edge.

## <a name="configure-microsoft-edge"></a>Configurare Microsoft Edge

### <a name="default-microsoft-edge-policies-for-surface-hub"></a>Criteri Microsoft Edge predefiniti per Surface Hub

Microsoft Edge è preconfigurato con le seguenti impostazioni di criteri per offrire un'esperienza ottimizzata per Surface Hub.
 
> [!TIP]
> È consigliabile mantenere il valore predefinito per queste impostazioni dei criteri.
 

| Impostazione dei criteri                                                                                                   | Esperienza consigliata                                                                                                                                                                                                                                               | Valore predefinito |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](https://docs.microsoft.com/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Non importare automaticamente i tipi di dati e le impostazioni Versione legacy di Microsoft Edge. In questo modo si evita di modificare i profili degli utenti connessi con le impostazioni condivise Surface Hub.                                                                                                 | 4                 |
| [BackgroundModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | Consenti Microsoft Edge processi continuino a essere in esecuzione in background anche dopo la chiusura dell'ultima finestra del browser, consentendo un accesso più rapido alle app Web durante una sessione.                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Non consentire agli utenti di creare nuovi profili in Microsoft Edge. Questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Consente a un solo utente di accedere a Microsoft Edge. In questo modo si semplifica l'esplorazione e l'esperienza di accesso                                                                                                                                                                | 0                 |
| [BrowserSignin](https://docs.microsoft.com/deployedge/microsoft-edge-policies#browsersignin)                           | Consente agli utenti di utilizzare single Sign-On (SSO) in Microsoft Edge. Quando un utente esegue l'Surface Hub, le credenziali possono fluire verso i siti Web supportati senza richiedere loro di eseguire nuovamente l'autenticazione.  | 1                 |
| [ExtensionInstallBlockList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | Impedisce agli utenti non amministratori di installare nuove estensioni in Microsoft Edge. Per configurare un elenco di estensioni da installare per impostazione predefinita, usa [ExtensionInstallForcelist.](https://docs.microsoft.com/deployedge/microsoft-edge-policies#extensioninstallforcelist) | *                 |
| [HideFirstRunExperience](https://docs.microsoft.com/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | Nasconde la prima esperienza di esecuzione e la schermata iniziale normalmente visualizzata quando gli utenti eseguono Microsoft Edge per la prima volta. Poiché Surface Hub è un dispositivo condiviso, questo semplifica l'esperienza utente.                                                                      | 1                 |
| [InPrivateModeAvailability](https://docs.microsoft.com/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | Disabilita la modalità InPrivate. Poiché End Session cancella già i dati di esplorazione, questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](https://docs.microsoft.com/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | Mostra l'Office 365 feed nelle nuove schede. Quando un utente accede a Surface Hub, ciò consente di accedere rapidamente ai file e al contenuto in Office 365.                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | Quando un utente esegue l'Surface Hub, verrà creato un profilo non rimovibile utilizzando l'account dell'organizzazione. In questo modo viene semplificata l'esperienza single Sign-On (SSO).                                                                                                 | 1                 |
| [PrintingEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#printingenabled)                       | Disabilita la stampa in Microsoft Edge. Surface Hub non supporta la stampa.                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](https://docs.microsoft.com/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Consente Microsoft Edge autenticare in modo proattivo gli utenti connessi con servizi Microsoft. In questo modo viene semplificata l'esperienza single Sign-On (SSO).                                                                                                                         | 1                 |
| [PromptForDownloadLocation](https://docs.microsoft.com/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | Salva automaticamente i file nella cartella Download, anziché chiedere agli utenti dove salvare il file. Questo semplifica l'esperienza di esplorazione.                                                                                                                             | 0                 |

> [!IMPORTANT]
> Le app Web progressive distribuibili non sono attualmente supportate nel Windows 10 Team sistema operativo.  Si noti inoltre che l'impostazione Microsoft Edge [webAppInstallForceList](https://docs.microsoft.com/deployedge/microsoft-edge-policies#webappinstallforcelist) non è supportata in Surface Hub. 

### <a name="configure-microsoft-edge-policy-settings"></a>Configurare le Microsoft Edge dei criteri

Utilizzare [Microsoft Edge dei browser per](https://docs.microsoft.com/deployedge/microsoft-edge-policies) configurare le impostazioni del browser in Microsoft Edge. Questi criteri possono essere applicati utilizzando:

- [Microsoft Intune](https://docs.microsoft.com/deployedge/configure-edge-with-intune),
- [Il provider mdm (Mobile Device Management) preferito che supporta l'inserimento ADMX](https://docs.microsoft.com/deployedge/configure-edge-with-mdm)o
- [Provisioning dei pacchetti con l'inserimento ADMX in progettazione Windows configurazione](https://docs.microsoft.com/windows/configuration/wcd/wcd-admxingestion).

 
### <a name="configure-microsoft-edge-updates"></a>Configurare Microsoft Edge aggiornamenti

Per impostazione predefinita, Microsoft Edge viene aggiornato automaticamente. Utilizzare [Microsoft Edge criteri di aggiornamento per](https://docs.microsoft.com/deployedge/microsoft-edge-update-policies) configurare le impostazioni per Microsoft Edge Update.
Tenere presente Surface Hub non supporta i criteri di aggiornamento Microsoft Edge seguenti:

- **Allowsxs:** in Surface Hub, Microsoft Edge Stable sostituisce sempre Versione legacy di Microsoft Edge.
- **CreateDesktopShortcut:** Surface Hub non utilizza i collegamenti del desktop.

> [!TIP]
>  Microsoft Edge richiede la connettività a Internet per supportare le funzionalità. Assicurati che gli [URL di dominio necessari](https://docs.microsoft.com/deployedge/microsoft-edge-security-endpoints) siano aggiunti all'elenco Consenti per garantire le comunicazioni tramite firewall e altri meccanismi di sicurezza.

## <a name="related-links"></a>Collegamenti correlati

- [Documentazione di Microsoft Edge](https://docs.microsoft.com/microsoft-edge/)


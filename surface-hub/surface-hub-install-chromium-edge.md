---
title: Gestire Microsoft Edge in Surface Hub
description: In questo articolo vengono descritte le impostazioni Microsoft Edge criteri predefiniti e gli strumenti per configurare le impostazioni del browser.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 08/17/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 80e861fd575324db21be458f7b82cd5fdb538b50
ms.sourcegitcommit: 68b6e86919d6e29155bf9386d05279866e1157e5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2021
ms.locfileid: "12100714"
---
# <a name="manage-microsoft-edge-on-surface-hub"></a>Gestire Microsoft Edge in Surface Hub

Utilizzare [Microsoft Edge dei browser](/deployedge/microsoft-edge-policies) per configurare le impostazioni del browser in Microsoft Edge tramite uno dei metodi seguenti:

- [Microsoft Intune](/deployedge/configure-edge-with-intune)
- [Il provider mdm (Mobile Device Management) preferito che supporta l'inserimento ADMX](/deployedge/configure-edge-with-mdm)
- [Provisioning dei pacchetti con l'inserimento ADMX in progettazione Windows configurazione](/windows/configuration/wcd/wcd-admxingestion)

> [!TIP]
> Il gesto scorrimento rapido verso il basso dalla parte superiore dello schermo per uscire dalla modalità schermo intero richiede due dita con il nuovo Microsoft Edge. L'azione esci a schermo intero è disponibile anche nel menu di scelta rapida visualizzato dopo un lungo tocco.

## <a name="default-microsoft-edge-policies-for-surface-hub"></a>Criteri Microsoft Edge predefiniti per Surface Hub

Microsoft Edge è preconfigurato con le seguenti impostazioni di criteri per offrire un'esperienza ottimizzata per Surface Hub.


> [!TIP]
> È consigliabile mantenere il valore predefinito per queste impostazioni dei criteri.

| Impostazione dei criteri                                                                                                   | Esperienza consigliata                                                                                                                                                                                                                                               | Valore predefinito |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Non importare automaticamente i tipi di dati e le impostazioni Versione legacy di Microsoft Edge. In questo modo si evita di modificare i profili degli utenti connessi con le impostazioni condivise Surface Hub.                                                                                                 | 4                 |
| [BackgroundModeEnabled](/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | Consenti Microsoft Edge processi continuino a essere in esecuzione in background anche dopo la chiusura dell'ultima finestra del browser, consentendo un accesso più rapido alle app Web durante una sessione.                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Non consentire agli utenti di creare nuovi profili in Microsoft Edge. Questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Consente a un solo utente di accedere a Microsoft Edge. In questo modo si semplifica l'esplorazione e l'esperienza di accesso                                                                                                                                                                | 0                 |
| [BrowserSignin](/deployedge/microsoft-edge-policies#browsersignin)                           | Consente agli utenti di utilizzare single Sign-On (SSO) in Microsoft Edge. Quando un utente esegue l'Surface Hub, le credenziali possono fluire verso i siti Web supportati senza richiedere di eseguire nuovamente l'autenticazione.  | 1                 |
| [ExtensionInstallBlockList](/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | Impedisce agli utenti non amministratori di installare nuove estensioni in Microsoft Edge. Per configurare un elenco di estensioni da installare per impostazione predefinita, usa [ExtensionInstallForcelist.](/deployedge/microsoft-edge-policies#extensioninstallforcelist) | *                 |
| [HideFirstRunExperience](/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | Nasconde la prima esperienza di esecuzione e la schermata iniziale normalmente visualizzata quando gli utenti eseguono Microsoft Edge per la prima volta. Poiché Surface Hub è un dispositivo condiviso, questo semplifica l'esperienza utente.                                                                      | 1                 |
| [InPrivateModeAvailability](/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | Disabilita la modalità InPrivate. Poiché Termina sessione cancella già i dati di esplorazione, questo semplifica l'esplorazione e l'esperienza di accesso.                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | Mostra l'Office 365 feed nelle nuove schede. Quando un utente ha eseguito l'Surface Hub, ciò consente di accedere rapidamente ai file e al contenuto in Office 365.                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | Quando un utente esegue l'Surface Hub, verrà creato un profilo non rimovibile utilizzando l'account dell'organizzazione. In questo modo viene semplificata l'esperienza single Sign-On (SSO).                                                                                                 | 1                 |
| [PrintingEnabled](/deployedge/microsoft-edge-policies#printingenabled)                       | Disabilita la stampa in Microsoft Edge. Surface Hub non supporta la stampa.                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Consente Microsoft Edge autenticare in modo proattivo gli utenti connessi con servizi Microsoft. In questo modo viene semplificata l'esperienza single Sign-On (SSO).                                                                                                                         | 1                 |
| [PromptForDownloadLocation](/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | Salva automaticamente i file nella cartella Download, anziché chiedere agli utenti dove salvare il file. Questo semplifica l'esperienza di esplorazione.                                                                                                                             | 0                 |

> [!IMPORTANT]
> Le app Web progressive distribuibili non sono attualmente supportate nel Windows 10 Team sistema operativo.  Si noti inoltre che l'impostazione Microsoft Edge [webAppInstallForceList](/deployedge/microsoft-edge-policies#webappinstallforcelist) non è supportata in Surface Hub.

### <a name="configure-microsoft-edge-updates"></a>Configurare Microsoft Edge aggiornamenti

Per impostazione predefinita, Microsoft Edge viene aggiornato automaticamente. Utilizzare [Microsoft Edge criteri di aggiornamento](/deployedge/microsoft-edge-update-policies) per configurare le impostazioni per Microsoft Edge Update. Si noti Surface Hub non supporta l'impostazione del criterio **CreateDesktopShortcut** Surface Hub non utilizza i collegamenti del desktop.

> [!TIP]
> Microsoft Edge richiede la connettività a Internet per supportare le funzionalità. Aggiungere gli [URL di dominio necessari all'elenco](/deployedge/microsoft-edge-security-endpoints) Consenti per garantire le comunicazioni tramite firewall e altri meccanismi di sicurezza.

## <a name="related-links"></a>Collegamenti correlati

- [Documentazione di Microsoft Edge](/microsoft-edge/)
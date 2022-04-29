---
title: Gestire le impostazioni di Microsoft Edge in Surface Hub
description: Questo articolo descrive le impostazioni predefinite dei criteri di Microsoft Edge e gli strumenti per configurare le impostazioni del browser.
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
ms.openlocfilehash: b652b990ce798d807ff2a27e87d212d01f3c23a2
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497729"
---
# <a name="manage-microsoft-edge-on-surface-hub"></a>Gestire le impostazioni di Microsoft Edge in Surface Hub

Usare [Microsoft Edge criteri del browser](/deployedge/microsoft-edge-policies) per configurare le impostazioni del browser in Microsoft Edge tramite uno dei metodi seguenti:

- [Microsoft Intune](/deployedge/configure-edge-with-intune)
- [Provider MDM (Mobile Gestione dispositivi) preferito che supporta l'inserimento ADMX](/deployedge/configure-edge-with-mdm)
- [Provisioning di pacchetti con inserimento ADMX in Progettazione configurazione Windows](/windows/configuration/wcd/wcd-admxingestion)

> [!TIP]
> Lo scorrimento rapido verso il basso dalla parte superiore dello schermo per uscire dalla modalità schermo intero richiede due dita con il nuovo Microsoft Edge. L'azione esci a schermo intero è disponibile anche nel menu di scelta rapida visualizzato dopo un tocco a pressione prolungata.

## <a name="default-microsoft-edge-policies-for-surface-hub"></a>Criteri di Microsoft Edge predefiniti per Surface Hub

Microsoft Edge è preconfigurato con i set di criteri seguenti per offrire un'esperienza ottimizzata per Surface Hub.


> [!TIP]
> È consigliabile mantenere il valore predefinito per queste impostazioni dei criteri.

| Impostazione dei criteri                                                                                                   | Esperienza consigliata                                                                                                                                                                                                                                               | Valore predefinito |
| ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------- |
| [AutoImportAtFirstRun](/deployedge/microsoft-edge-policies#autoimportatfirstrun)             | Non importare automaticamente tipi di dati e impostazioni da Versione legacy di Microsoft Edge. In questo modo si evita di modificare i profili degli utenti connessi con le impostazioni condivise dal Surface Hub.                                                                                                 | 4                 |
| [BackgroundModeEnabled](/deployedge/microsoft-edge-policies#backgroundmodeenabled)           | Consenti ai processi Microsoft Edge di continuare a essere eseguiti in background anche dopo la chiusura dell'ultima finestra del browser, consentendo un accesso più rapido alle app Web durante una sessione.                                                                                                      | 1                 |
| [BrowserAddProfileEnabled](/deployedge/microsoft-edge-policies#browseraddprofileenabled)     | Non consentire agli utenti di creare nuovi profili in Microsoft Edge. Ciò semplifica l'esperienza di esplorazione e accesso.                                                                                                                                                      | 0                 |
| [BrowserGuestModeEnabled](/deployedge/microsoft-edge-policies#browserguestmodeenabled)       | Consente a un solo utente di accedere a Microsoft Edge. Ciò semplifica l'esperienza di esplorazione e accesso                                                                                                                                                                | 0                 |
| [BrowserSignin](/deployedge/microsoft-edge-policies#browsersignin)                           | Consente agli utenti di usufruire di Single Sign-On (SSO) in Microsoft Edge. Quando un utente accede a Surface Hub, le credenziali possono passare ai siti Web supportati senza dover ripetere l'autenticazione.  | 1                 |
| [ExtensionInstallBlockList](/deployedge/microsoft-edge-policies#extensioninstallblocklist)   | Impedisce agli utenti non amministratori di installare nuove estensioni in Microsoft Edge. Per configurare un elenco di estensioni da installare per impostazione predefinita, usare [ExtensionInstallForcelist](/deployedge/microsoft-edge-policies#extensioninstallforcelist). | *                 |
| [HideFirstRunExperience](/deployedge/microsoft-edge-policies#hidefirstrunexperience)         | Nasconde la prima esperienza di esecuzione e la schermata iniziale che viene normalmente visualizzata quando gli utenti eseguono Microsoft Edge per la prima volta. Poiché Surface Hub è un dispositivo condiviso, questo semplifica l'esperienza utente.                                                                      | 1                 |
| [InPrivateModeAvailability](/deployedge/microsoft-edge-policies#inprivatemodeavailability)   | Disabilita la modalità InPrivate. Poiché End Session cancella già i dati di esplorazione, ciò semplifica l'esperienza di esplorazione e accesso.                                                                                                                                          | 1                 |
| [NewTabPageSetFeedType](/deployedge/microsoft-edge-policies#newtabpagesetfeedtype)           | Mostra l'esperienza Office 365 feed nelle nuove schede. Quando un utente accede a Surface Hub, questo consente l'accesso rapido ai file e al contenuto in Office 365.                                                                                                        | 1                 |
| [NonRemovableProfileEnabled](/deployedge/microsoft-edge-policies#nonremovableprofileenabled) | Quando un utente ha eseguito l'accesso a Surface Hub, verrà creato un profilo non rimovibile usando il proprio account aziendale. Ciò semplifica l'esperienza Single Sign-On (SSO).                                                                                                 | 1                 |
| [PrintingEnabled](/deployedge/microsoft-edge-policies#printingenabled)                       | Disabilita la stampa in Microsoft Edge. Surface Hub non supporta la stampa.                                                                                                                                                                                              | 0                 |
| [ProActiveAuthEnabled](/deployedge/microsoft-edge-policies#proactiveauthenabled)             | Consente Microsoft Edge di autenticare in modo proattivo gli utenti connessi con servizi Microsoft. Ciò semplifica l'esperienza Single Sign-On (SSO).                                                                                                                         | 1                 |
| [PromptForDownloadLocation](/deployedge/microsoft-edge-policies#promptfordownloadlocation)   | Salva automaticamente i file nella cartella Download, anziché chiedere agli utenti dove salvare il file. Ciò semplifica l'esperienza di esplorazione.                                                                                                                             | 0                 |

> [!TIP]
> Le app Web progressive distribuibili sono ora supportate nel sistema operativo Windows 10 Team. Per altre informazioni, vedere [Installare App Web progressive in Surface Hub](install-pwa-surface-hub.md). 

### <a name="configure-microsoft-edge-updates"></a>Configurare gli aggiornamenti Microsoft Edge

Per impostazione predefinita, Microsoft Edge viene aggiornato automaticamente. Usare [Microsoft Edge criteri di aggiornamento](/deployedge/microsoft-edge-update-policies) per configurare le impostazioni per Microsoft Edge Update. Si noti che Surface Hub non supporta l'impostazione dei criteri **CreateDesktopShortcut** perché Surface Hub non usa i collegamenti desktop.

> [!TIP]
> Microsoft Edge richiede la connettività a Internet per supportare le funzionalità. Aggiungere gli [URL di dominio necessari](/deployedge/microsoft-edge-security-endpoints) all'elenco Consenti per garantire le comunicazioni tramite firewall e altri meccanismi di sicurezza.

## <a name="related-links"></a>Collegamenti correlati

- [Documentazione di Microsoft Edge](/microsoft-edge/)
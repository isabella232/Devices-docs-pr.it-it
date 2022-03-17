---
title: Distribuzione, gestione e manutenzione di Surface Pro X
description: In questo articolo viene fornita una panoramica delle considerazioni fondamentali per la distribuzione, la gestione e la manutenzione di Surface Pro X.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: high
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 12/01/2021
ms.reviewer: jessko
manager: laurawi
ms.audience: itpro
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 35cfd848ee8f66981c421a8d0f55f8c3bb379a02
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449599"
---
# <a name="deploying-managing--servicing-surface-pro-x"></a>Distribuzione, gestione e manutenzione di Surface Pro X

Creato per gestire i requisiti commerciali ad alte prestazioni, Surface Pro X incorpora i processori più potenti di questa classe, i chipset Microsoft SQ1 e Microsoft SQ1 ARM.

Alimentato da una CPU a 3 GHz e da una GPU teraflop 2.1, Surface Pro X offre un'esperienza di Windows completa. Il Gigabit-LTE integrato con durata della batteria di 15 ore e tocco, penna, tablet e portatile versatili lo rendono l'ideale per gli operatori mobili in prima linea e professionisti in campo finanziario, legale e medico o per qualsiasi altro ruolo che richiede una durata della batteria estesa e funzionalità di connettività continua.

Surface Pro X è progettato quasi esclusivamente per un ambiente moderno basato su cloud e funziona al meglio con Microsoft 365, Intune e Windows Autopilot. In questo articolo vengono illustrate le considerazioni più importanti per la distribuzione, la gestione e la manutenzione di Surface Pro X.

## <a name="deploying-surface-pro-x"></a>Distribuzione di Surface Pro X

Per un'esperienza ottimale, distribuisci Surface Pro X tramite Windows Autopilot con l'assistenza di un Microsoft Cloud Solution Provider o tramite self-provisioning con profili di distribuzione di Windows Autopilot e relative funzionalità. Per ulteriori informazioni, fai riferimento a:

- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md)
- [Panoramica di Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot)

La distribuzione di Autopilot offre diversi vantaggi: consente di usare il sistema operativo di cui è stato eseguito il provisioning predefinito, semplificato per la distribuzione senza tocco, per includere la preinstallazione di [Microsoft 365 Apps for enterprise](https://www.microsoft.com/microsoft-365/enterprise/microsoft-365-apps-for-enterprise).

Le organizzazioni che usano già soluzioni moderne per la gestione, la sicurezza e la produttività sono ben posizionate per sfruttare le funzionalità esclusive relative alle prestazioni di Surface Pro X. Anche i clienti che usano le [app line-of-business](/microsoft-store/working-with-line-of-business-apps), le [app del Microsoft store (UWP)](/windows/uwp/get-started/universal-application-platform-guide) o le soluzioni desktop remoto modernizzate possono trarne vantaggio.

## <a name="image-based-deployment-considerations"></a>Considerazioni sulla distribuzione basate su immagini

MDT (Microsoft Deployment Toolkit) e Microsoft Endpoint Configuration Manager (in precedenza System Center Configuration Manager) non supportano Surface Pro X per la distribuzione del sistema operativo. I clienti che si affidano alla distribuzione basata su immagini devono prendere in considerazione Surface Pro 8 mentre continuano a valutare il momento giusto per la transizione a soluzioni di distribuzione moderne. 

## <a name="managing-surface-pro-x-devices"></a>Gestione dei dispositivi Surface Pro X

### <a name="intune"></a>Intune

[Microsoft Intune](/intune) si integra con Azure Active Directory per il controllo delle identità e degli accessi e fornisce la gestione granulare dei dispositivi Surface Pro X registrati. Le impostazioni dei criteri di gestione di dispositivi mobili (MDM) di Intune presentano numerosi vantaggi rispetto agli strumenti locali meno recenti, ad esempio i criteri di gruppo di Windows. Sono inclusi tempi di accesso al dispositivo più veloci e un catalogo semplificato di impostazioni dei criteri che consentono di gestire completamente i dispositivi dal cloud. Ad esempio, è possibile [gestire LTE utilizzando i profili eSIM](/windows/client-management/mdm/esim-enterprise-management) per configurare i piani dati e distribuire i codici di attivazione a più dispositivi.

### <a name="co-management"></a>Gestione condivisa

Una volta eseguita la distribuzione in Autopilot, è possibile aggiungere dispositivi Surface Pro X a Azure AD o Active Directory ([Aggiunta ad Azure AD ibrido](/azure/active-directory/devices/concept-azure-ad-join-hybrid)) in cui potrai [gestire i dispositivi con Intune](/mem/intune/remote-actions/device-management) o [cogestirli con Endpoint Configuration Manager](/mem/configmgr/comanage/overview), che installerà il client ConfigMgr x86 a 32 bit.

### <a name="third-party-mdm-solutions"></a>Soluzioni MDM di terze parti

Potresti utilizzare strumenti MDM di terze parti per gestire i dispositivi Surface Pro X. Per i dettagli, contattare il provider MDM.

### <a name="antivirus-software"></a>Software antivirus

Microsoft Defender consente di proteggere Windows 10 e Windows 11 su PC basati su ARM per la durata supportata del dispositivo. 

Non è possibile installare alcuni software antivirus di terze parti su dispositivi che eseguono un processore basato su ARM. La collaborazione con provider di software antivirus di terze parti continua per la disponibilità di app antivirus nei PC basati su ARM. Contatta il provider del software antivirus per capire quando saranno disponibili le app.

## <a name="servicing-surface-pro-x"></a>Manutenzione di Surface Pro X

Surface Pro X viene fornito con Windows 10 versione 2004 ed è compatibile con Windows 10, versione 1903 e versioni successive. Come dispositivo basato su ARM, dispone di requisiti specifici per la manutenzione dei driver e del firmware più recenti. 

Surface Pro X è stato progettato per l'uso di Windows Update per semplificare l'aggiornamento dei driver e del firmware sia per gli utenti domestici che per gli utenti business. Utilizzare le impostazioni predefinite per ricevere gli aggiornamenti automatici.  Per verificare:

1. Vai a **Start** > **Impostazioni > Aggiornamento e sicurezza > Windows Update** > **Opzioni avanzate.**
2. In **Scegli come installare gli aggiornamenti,** seleziona **Automatico (scelta consigliata)**.

### <a name="recommendations-for-commercial-customers"></a>Consigli per i clienti commerciali

- Usa Windows Update o Windows Update per le aziende per mantenere i driver e il firmware più recenti. Per altre informazioni, vedi [Distribuire gli aggiornamenti mediante Windows Update per le aziende](/windows/deployment/update/waas-manage-updates-wufb).
- Per altre informazioni sulla distribuzione e la gestione degli aggiornamenti nei dispositivi Surface, vedere [Gestire e distribuire gli aggiornamenti di driver e firmware Surface](manage-surface-driver-and-firmware-updates.md).
- Si noti che Windows Server Update Services (WSUS) non supporta la distribuzione di driver e firmware a Surface Pro X.

## <a name="running-apps-on-surface-pro-x"></a>Esecuzione di app su Surface Pro X

La maggior parte delle app viene eseguita su PC Windows 10 basati su ARM con esclusioni limitate.

### <a name="supported-apps"></a>App supportate

- La maggior parte delle app Win32 x86 viene eseguita su Surface Pro X.
- Le app ARM64 e Microsoft Store UWP native offrono un'esperienza utente eccellente che utilizza la velocità nativa completa del processore basato su ARM, ottimizzando la durata della batteria.
- App che usano driver progettati per PC Windows 10 o Windows 11 che eseguono un processore basato su ARM.
- L'emulazione x64 per Windows ora è disponibile a livello generale su Windows 11.

### <a name="fasttrack-app-assure"></a>App FastTrack Assure 

Il programma app Assure è disponibile per i clienti commerciali per le applicazioni LOB, ISV e Microsoft di terze parti destinate a Windows 10 su ARM. Se i clienti commerciali riscontrano un problema di compatibilità con le app di Windows 10 su ARM, Microsoft fornirà risorse agli sviluppatori per la risoluzione dei problemi e l'assistenza con le correzioni alle app, senza costi aggiuntivi. Per saperne di più, visita [aka.ms/AppAssure](/fasttrack/products-and-capabilities#app-assure).

Per altre informazioni sull'esecuzione delle app su Surface Pro X, fai riferimento a:

- [Domande frequenti sul supporto per PC Windows 10 basati su ARM](https://support.microsoft.com/help/4521606)
- [Documentazione di Windows 10 su ARM](/windows/arm)

## <a name="virtual-desktops-vdi"></a>Desktop virtuali (VDI)

Desktop virtuale di Azure consente l'accesso a desktop, applicazioni e dati di Windows su qualsiasi dispositivo o piattaforma di elaborazione, da qualsiasi posizione. Per altre informazioni, fai riferimento al [sito di Desktop virtuale di Azure](https://aka.ms/wvd). 

## <a name="browsing-with-surface-pro-x"></a>Esplorazione con Surface Pro X

I browser più diffusi vengono eseguiti su Surface Pro X:

- Edge, Firefox, Chrome e Internet Explorer inclusi vengono tutti eseguiti su Surface Pro X.
- Firefox e Microsoft Edge basati su Chromium vengono eseguiti in modalità nativa con prestazioni avanzate su PC Windows 10 o Windows 11 basati su ARM.

## <a name="installing-and-using-microsoft-office"></a>Installazione e utilizzo di Microsoft Office

- Usare Office 365 per un'esperienza ottimale su un PC Windows 10 o Windows 11 con processore basato su ARM.
- L'opzione "A portata di clic" di Office 365 installa Outlook, Word, Excel e PowerPoint, ottimizzati per essere eseguiti su un PC Windows 10 o Windows 11 con processore basato su ARM.
- Microsoft Teams viene eseguito in modo ottimale su Surface Pro X.
- Per le "versioni perpetue" di Office, ad esempio Office 2019, installare la versione a 32 bit.

## <a name="vpn"></a>VPN

Per confermare se una VPN di terze parti specifica supporta un PC Windows 10 su un processore basato su ARM, contatta il provider VPN.

## <a name="feature-summary"></a>Riepilogo delle funzionalità

Nelle seguenti tabelle viene visualizzata la disponibilità delle funzionalità principali selezionate su Surface Pro X con Windows 10 o Windows 11 su ARM.


### <a name="deployment"></a>Distribuzione

| Funzionalità                                                           | (S/N) | Note                                                                                                                             |
| ----------------------------------------------------------------- | --- | --------------------------------------------------------------------------------------------------------------------------------- |
| Windows Autopilot                                                 | Sì |                                                                                                                                   |
| Supporto per l'avvio di rete (PXE)                                    | No  |                                                                                                                                   |
| Progettazione configurazione di Windows                                    | No  | Non consigliato per Surface Pro X.                                                                                                |
| WinPE                                                             | Sì | Non consigliato per Surface Pro X. Microsoft non fornisce il file. ISO necessario e i driver per il supporto di WinPE su Surface Pro X. |
| Endpoint Configuration Manager: distribuzione del sistema operativo(OSD) | No  | Non è supportato su Surface Pro X.                                                                                                   |
| MDT                                                               | No  | Non è supportato su Surface Pro X.                                                                                                   |

 
 
### <a name="management"></a>Management
 

| Funzionalità                                       | (S/N)     | Note                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| Intune                                        | Sì     | Gestisci LTE con i profili eSIM.                                                        |
| Windows Autopilot                             | Sì     |                                                                                       |
| Azure AD (gestione condivisa)                      | Sì     | Possibilità di aggiungere Surface Pro X ad Azure AD o Active Directory (Aggiunta ad Azure AD ibrido). |
| Endpoint Configuration Manager                | Sì     |                                                                                       |
| Accendi al ripristino CA                      | Sì     |                                                                                       |
| Toolkit di diagnostica per Surface (SDT) per le aziende | Sì     |                                                                                       |
| Strumento Asset tag di Surface                        | Sì     |                                                                                       |
| SEMM (Surface Enterprise Management Mode)     | Parziale | Nessuna opzione per disabilitare l'hardware in Surface Pro X a livello di firmware.                 |
| Strumento di configurazione UEFI di Surface                     | No      | Nessuna opzione per disabilitare l'hardware in Surface Pro X a livello di firmware.                |
| Strumento di gestione UEFI di Surface                          | Parziale | Nessuna opzione per disabilitare l'hardware in Surface Pro X a livello di firmware.                 |

 

### <a name="security"></a>Sicurezza
 
 Funzionalità                                        | (S/N)     | Note                                                                                 |
| --------------------------------------------- | ------- | ------------------------------------------------------------------------------------- |
| BitLocker                                     | Sì     |                                                                                       |
| Microsoft Defender                            | Sì     |                                                                                       |
| Supporto per gli antivirus di terze parti             | Vedi nota| Non è possibile installare alcuni software antivirus di terze parti su un processore basato su ARM. Contatta il provider del software antivirus per capire quando saranno disponibili le app. |
| Avvio protetto                                   | Sì     |                                                                                       |
| Windows Information Protection                | Sì     |                                                                                       |
| Surface Data Eraser (SDE)                     | Sì     |                                                                                       |


## <a name="faq"></a>Domande frequenti

### <a name="can-i-deploy-surface-pro-x-with-mdt-or-endpoint-configuration-manager"></a>Posso distribuire Surface Pro X con MDT o Endpoint Configuration Manager?

Microsoft Deployment Toolkit (MDT) e Microsoft Endpoint Configuration Manager attualmente non supportano Surface Pro X per la distribuzione del sistema operativo. I clienti che si affidano alla distribuzione basata su immagini devono prendere in considerazione Surface Pro 8 mentre continuano a valutare il momento giusto per la transizione al cloud.

### <a name="how-can-i-deploy-surface-pro-x"></a>Come posso distribuire Surface Pro X?

Distribuisci Surface Pro X tramite Windows Autopilot.

### <a name="is-a-bmr-available"></a>È BMR disponibile?

Sì, fare riferimento a [Scaricare un'immagine di ripristino per ](https://support.microsoft.com/surfacerecoveryimage)Surface.

### <a name="is-intune-required-to-manage-surface-pro-x"></a>Per gestire Surface Pro X è necessario Intune?

Intune è consigliato ma non obbligatorio. Una volta eseguita la distribuzione in Autopilot, puoi aggiungere dispositivi Surface Pro X a Azure AD o Active Directory (Aggiunta ad Azure AD ibrido) in cui potrai gestire i dispositivi con Intune o cogestirli con Endpoint Configuration Manager, che installerà il client ConfigMgr x86 a 32 bit.

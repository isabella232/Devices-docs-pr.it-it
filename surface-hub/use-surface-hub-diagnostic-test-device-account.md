---
title: Uso dello strumento di diagnostica hardware Surface Hub per testare un account di dispositivo
description: Uso dello strumento di diagnostica hardware Surface Hub per testare un account di dispositivo
ms.assetid: a87b7d41-d0a7-4acc-bfa6-b9070f99bc9c
keywords: Impostazioni di accessibilità, app Impostazioni, Accessibilità
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 6661f2347d2f411ed11fe6057ede8ca2bab07c33
ms.sourcegitcommit: f0c976664116c45605edf3d56c4f58119a246b93
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/11/2021
ms.locfileid: "11406669"
---
# <a name="using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-account"></a>Uso dello strumento di diagnostica hardware Surface Hub per testare un account di dispositivo

## <a name="introduction"></a>Introduzione

> [!NOTE]
> La sezione "Impostazioni account" dello strumento di diagnostica hardware Surface Hub non raccoglie alcuna informazione. I messaggi di posta elettronica e la password immessi come input vengono utilizzati solo direttamente nell'ambiente e non vengono raccolti o trasferiti a nessuno. Le informazioni di accesso vengono mantenute solo finché l'applicazione non viene chiusa o non si termina la sessione corrente in Surface Hub.

> [!IMPORTANT]
> * Per eseguire questa applicazione non sono necessari privilegi di amministratore.
> * I risultati della diagnostica devono essere discussi con l'amministratore locale prima di aprire una chiamata di servizio con Microsoft.

### <a name="surface-hub-hardware-diagnostic"></a>Diagnostica hardware Surface Hub

Per impostazione predefinita, [l'applicazione diagnostica hardware Surface Hub](https://www.microsoft.com/store/apps/9nblggh51f2g) non è installata nelle versioni precedenti del sistema Surface Hub. L'applicazione è disponibile gratuitamente da Microsoft Store. Per installare l'applicazione sono necessari privilegi di amministratore.

   ![Screenshot of Hardware Diagnostic](images/01-diagnostic.png)

## <a name="about-the-surface-hub-hardware-diagnostic-tool"></a>Informazioni sullo strumento di diagnostica hardware di Surface Hub

Lo strumento di diagnostica hardware Surface Hub è uno strumento facile da esplorare che consente all'utente di testare molti dei componenti hardware all'interno del dispositivo Surface Hub. Questo strumento può anche testare e verificare un account del dispositivo Surface Hub. Questo articolo descrive come usare il test Impostazioni account all'interno dello strumento di diagnostica hardware Surface Hub.

> [!NOTE]
> L'account del dispositivo per Surface Hub deve essere creato prima di eseguire qualsiasi test. La Guida all'amministratore di Surface Hub fornisce istruzioni e script di PowerShell per creare account di dispositivi locali, online (Office365) o ibridi. Per altre informazioni, vai all'argomento Creare e [testare un account del dispositivo (Surface Hub)](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) nella guida.

### <a name="device-account-testing-process"></a>Processo di test dell'account del dispositivo

1. Passa a **Tutte le app**e quindi individua l'applicazione di diagnostica hardware Surface Hub.

    ![Screenshot di Tutte le app](images/02-all-apps.png)

1. All'avvio dell'applicazione, la **pagina** di benvenuto fornisce una finestra di testo per documentare il motivo per cui si sta testando l'hub. Questa nota può essere salvata su USB insieme ai risultati di diagnostica al termine del test. Dopo aver immesso una nota, selezionare il **pulsante** Continua.

    >[!NOTE]
    >Quando si salvano i risultati di diagnostica, non modificare il percorso predefinito o selezionare una sottodirectory. I file possono essere copiati in un secondo momento tramite l'app Esplora file.

    ![Screenshot of Welcome](images/03-welcome.png)

1. La schermata successiva offre la possibilità di testare tutti o alcuni componenti di Surface Hub. Per iniziare a testare l'account del dispositivo, seleziona **l'icona Risultati test.**

    ![Screenshot of Test Options](images/04-test-results-1.png)

    ![Screenshot of Test Results](images/05-test-results-2.png)

1. Selezionare **Impostazioni account**.  

    ![Screenshot of Account Settings](images/06-account-settings.png)

    La schermata Impostazioni account viene usata per testare l'account del dispositivo.

    ![Screenshot of Account Settings Details](images/07-account-settings-details.png)

1. Immetti l'indirizzo di posta elettronica dell'account del dispositivo. La password è facoltativa, ma è consigliata. Seleziona il **pulsante Test account** quando sei pronto per continuare.

    ![Screenshot of Test Account](images/08-test-account.png)

1. Al termine del test, esaminare i risultati per le quattro aree di test. Ogni sezione può essere espansa o compressa selezionando il segno più o meno accanto a ogni argomento.

    **Rete**

    ![Screenshot of Network](images/09-network.png)

    **Environment**

    ![Screenshot of Environment](images/10-environment.png)

    **Certificati**

    ![Screenshot of Certificates](images/11-certificates.png)

    **Modello di attendibilità**

    ![Screenshot of Trust Model](images/12-trust-model.png)

## <a name="appendix"></a>Appendice

### <a name="field-messages-and-resolution"></a>Messaggi di campo e risoluzione

#### <a name="network"></a>Rete

Campo |Operazione riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Connettività Internet |Il dispositivo dispone di connettività Internet |Il dispositivo non dispone di connettività Internet |Verifica la connettività Internet, inclusa la connessione proxy |
Versione HTTP |1.1 |1.0 |Se HTTP 1.0 è stato trovato, causerà un problema con WU e Store |
Connettività Internet diretta |Il dispositivo dispone di un proxy configurato Per il dispositivo non è configurato alcun proxy |N/D |Informativo. Il dispositivo è dietro un proxy? |
Indirizzo proxy | | |Se configurato, restituisce l'indirizzo proxy. |
Autenticazione proxy |Il proxy non richiede l'autenticazione |Il proxy richiede l'autenticazione proxy |Il risultato può essere un falso positivo se un utente ha già una sessione aperta in Edge ed è stato autenticato tramite il proxy. |
Tipi di autenticazione proxy | | |Se viene utilizzata l'autenticazione proxy, restituire i metodi di autenticazione annunciati dal proxy.  |

#### <a name="environment"></a>Environment

Campo |Operazione riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Dominio SIP | | |Informativo.  |
Ambiente Skype |Skype for Business Online, Skype for Business OnPrem, Skype for Business Hybrid |Informativo. |Tipo di ambiente rilevato. Nota: l'ambiente ibrido può essere rilevato solo se viene immessa la password.
LyncDiscover FQDN | | |Informativo. Visualizza il risultato DNS LyncDiscover |
LyncDiscover URI | | |Informativo. Visualizza l'URL utilizzato per eseguire un LyncDiscover nell'ambiente.|
LyncDiscover |Connessione completata |Connessione non riuscita |Risposta dal servizio Web LyncDiscover. |
Nome host pool SIP | | |Informativo. Visualizzare il nome del pool SIP individuato da LyncDiscover |

#### <a name="certificates-in-premises-hybrid-only"></a>Certificati (solo ibrido locale)

LyncDiscover Certificate

Campo |Operazione riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
LyncDiscover Cert CN | | |Informativo. Visualizza il certificato LD Nome comune |
LyncDiscover Cert CA | | |Informativo. Visualizza l'autorità di certificazione LD |
LyncDiscover Cert Root CA | | |Informativo. Visualizza la CA radice del certificato LD, se disponibile. |
Stato attendibilità LD |Certificato attendibile. |Il certificato non è attendibile, aggiungere l'autorità di certificazione radice. |Verificare il certificato nell'archivio certificati locale. Restituisce positivo se il computer considera attendibile il certificato.|[Scaricare e distribuire i certificati di Skype for Business tramite PowerShell](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) / [Elementi supportati per i pacchetti di provisioning di Surface Hub](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)

Certificazione pool SIP

Campo |Operazione riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
SIP Pool Cert CN | | |(CONTENTS) |
CA certificato pool SIP | | |(CONTENTS) |
Stato attendibilità pool SIP |Certificato attendibile. |Il certificato non è attendibile, aggiungere l'autorità di certificazione radice. |Verificare il certificato rispetto all'archivio certificati locale e restituire un valore positivo se i dispositivi considera attendibile il certificato. |
CA radice certificato pool SIP | | |Informazioni. Visualizzare l'autorità di certificazione radice del pool SIP, se disponibile. |

#### <a name="trust-model-on-premises-hybrid-only"></a>Modello di attendibilità (solo ibrido locale)

Campo |Operazione riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Stato modello di attendibilità |Nessun problema del modello di attendibilità rilevato. |Dominio SIP e dominio del server sono diversi, aggiungere i domini seguenti. |Controllare l'FQDN LD/ nome del server LD/ nome del server del pool per problema del modello di attendibilità. 
Domain Name(s) | | |Restituire l'elenco dei domini da aggiungere per la connessione di SFB. |

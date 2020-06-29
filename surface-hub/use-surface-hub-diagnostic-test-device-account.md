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
ms.openlocfilehash: 127be0a5f320418d8a1086aec3de62e3ef54e42a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832679"
---
# Uso dello strumento di diagnostica hardware Surface Hub per testare un account di dispositivo

## Introduzione

> [!NOTE]
> La sezione "Impostazioni account" dello strumento di diagnostica hardware Surface Hub non raccoglie alcuna informazione. Il messaggio di posta elettronica e la password immessi come input vengono usati solo direttamente nell'ambiente e non vengono raccolti o trasferiti a nessuno. Le informazioni di accesso vengono mantenute solo finché l'applicazione non viene chiusa o si termina la sessione corrente nell'hub Surface.

> [!IMPORTANT]
> * I privilegi di amministratore non sono necessari per eseguire questa applicazione.
> * I risultati della diagnostica devono essere discussi con l'amministratore locale prima di aprire una chiamata di servizio con Microsoft.

### Diagnostica hardware di Surface Hub

Per impostazione predefinita, l'applicazione di [diagnostica hardware Surface Hub](https://www.microsoft.com/store/apps/9nblggh51f2g) non è installata nelle versioni precedenti del sistema Hub Surface. L'applicazione è disponibile gratuitamente da Microsoft Store. Per installare l'applicazione sono necessari i privilegi di amministratore.

   ![Screenshot della diagnostica hardware](images/01-diagnostic.png)

## Informazioni sullo strumento di diagnostica hardware Surface Hub

Lo strumento di diagnostica hardware Surface Hub è uno strumento facile da esplorare che consente all'utente di testare molti componenti hardware all'interno del dispositivo Surface Hub. Questo strumento può anche testare e verificare un account di dispositivo hub Surface. Questo articolo descrive come usare il test delle impostazioni dell'account all'interno dello strumento di diagnostica hardware Surface Hub.

> [!NOTE]
> L'account del dispositivo per l'hub Surface deve essere creato prima di eseguire qualsiasi test. La guida per gli amministratori di Surface Hub fornisce istruzioni e script di PowerShell che consentono di creare account di dispositivo online (Office365) o ibridi. Per altre informazioni, vedere l'argomento [creare e testare un account di dispositivo (Surface Hub)](https://docs.microsoft.com/surface-hub/create-and-test-a-device-account-surface-hub) nella guida.

### Processo di test dell'account del dispositivo

1. Passare a **tutte le app**e quindi individuare l'applicazione di diagnostica hardware Surface Hub.

    ![Screenshot di tutte le app](images/02-all-apps.png)

1. Quando l'applicazione viene avviata, la pagina di **benvenuto** fornisce una finestra di testo per documentare il motivo per cui viene testato l'hub. Questa nota può essere salvata in USB insieme ai risultati diagnostici alla conclusione del test. Dopo aver completato l'immissione di una nota, selezionare il pulsante **continua** .

    ![Schermata di benvenuto](images/03-welcome.png)

1. Nella schermata successiva è disponibile l'opzione per testare tutti o alcuni componenti di Surface Hub. Per iniziare a testare l'account del dispositivo, selezionare l'icona dei **risultati del test** .

    ![Schermata dei risultati del test](images/04-test-results-1.png)

    ![Schermata dei risultati del test](images/05-test-results-2.png)

1. Selezionare **Impostazioni account**.  

    ![Screenshot delle impostazioni dell'account](images/06-account-settings.png)

    La schermata Impostazioni account viene usata per testare l'account del dispositivo.

    ![Screenshot dei dettagli delle impostazioni dell'account](images/07-account-settings-details.png)

1. Immettere l'indirizzo di posta elettronica dell'account del dispositivo. La password è facoltativa, ma è consigliata. Selezionare il pulsante **test account** quando si è pronti per continuare.

    ![Screenshot dell'account di test](images/08-test-account.png)

1. Al termine del test, esaminare i risultati per le quattro aree di test. Ogni sezione può essere espansa o compressa selezionando il segno più o meno accanto a ogni argomento.

    **Rete**

    ![Screenshot della rete](images/09-network.png)

    **Ambiente**

    ![Schermata dell'ambiente](images/10-environment.png)

    **Certificati**

    ![Screenshot dei certificati](images/11-certificates.png)

    **Modello di attendibilità**

    ![Screenshot del modello di attendibilità](images/12-trust-model.png)

## Appendice

### Messaggi di campo e risoluzione

#### Rete

Campo |Operazioni riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Connettività Internet |Il dispositivo ha connettività Internet |Il dispositivo non ha connettività Internet |Verifica la connettività Internet, inclusa la connessione proxy |
Versione HTTP |1,1 |1.0 |Se è stato trovato il 1,0 HTTP, il problema verrà causato da WU e Store |
Connettività Internet diretta |Il dispositivo ha configurato un dispositivo proxy non ha configurato un proxy |N/D |Informativo. Il dispositivo è dietro un proxy? |
Indirizzo proxy | | |Se configurato, restituisce l'indirizzo del proxy. |
Autenticazione proxy |Proxy non richiede l'autenticazione |Proxy richiede l'autenticazione proxy |Il risultato può essere un falso positivo se un utente ha già una sessione aperta in Edge ed è autenticato tramite il proxy. |
Tipi di auth proxy | | |Se si usa l'autenticazione proxy, restituire i metodi di autenticazione annunciati dal proxy.  |

#### Ambiente

Campo |Operazioni riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Dominio SIP | | |Informativo.  |
Ambiente Skype |Skype for business online, Skype for business OnPrem, Skype for business Hybrid |Informativo. |Quale tipo di ambiente è stato rilevato. Nota: Hybrid può essere rilevato solo se è stata immessa la password.
LyncDiscover FQDN | | |Informativo. Visualizza il risultato DNS di LyncDiscover |
URI LyncDiscover | | |Informativo. Visualizza l'URL usato per eseguire una LyncDiscover nell'ambiente.|
LyncDiscover |Connessione completata |Connessione non riuscita |Risposta da LyncDiscover Web Service. |
Hostname del pool SIP | | |Informativo. Visualizzare il nome del pool SIP scoperto da LyncDiscover |

#### Certificati (solo ibridi in locale)

Certificato LyncDiscover

Campo |Operazioni riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
LyncDiscover CERT CN | | |Informativo. Visualizza il nome comune LD CERT |
LyncDiscover CERT CA | | |Informativo. Visualizza la CA LD CERT |
CA radice di LyncDiscover CERT | | |Informativo. Visualizza la CA radice LD CERT, se disponibile. |
Stato attendibile LD |Il certificato è attendibile. |Il certificato non è attendibile, aggiungere la CA radice. |Verificare il certificato in base all'archivio CERT locale. Restituisce positivo se il computer considera attendibile il certificato.|[Scaricare e distribuire certificati Skype for business con PowerShell](https://blogs.msdn.microsoft.com/surfacehub/2016/06/07/download-and-deploy-skype-for-business-certificates-using-powershell/) / [Elementi supportati per i pacchetti di provisioning di Surface Hub](https://docs.microsoft.com/surface-hub/provisioning-packages-for-surface-hub#supported-items-for-surface-hub-provisioning-packages)

Certificazione SIP per pool

Campo |Operazioni riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
CERT CN pool SIP | | |CONTENUTO |
CA Cert pool SIP | | |CONTENUTO |
Stato di attendibilità del pool SIP |Il certificato è attendibile. |Il certificato non è attendibile, aggiungere la CA radice. |Verificare il certificato con l'archivio CERT locale e restituire un risultato positivo se il certificato viene considerato attendibile dai dispositivi. |
CA radice CERT pool SIP | | |Informazioni. Visualizzare la CA radice del pool di certificati SIP, se disponibile. |

#### Modello di attendibilità (solo ibrida locale)

Campo |Operazioni riuscita |Errore |Comment |Riferimento
|------|------|------|------|------|
Stato modello di attendibilità |Nessun problema di modello di attendibilità rilevato. |Il dominio SIP e il dominio del server sono diversi per aggiungere i domini seguenti. |Controllare il nome del nome del server o del pool di nomi FQDN LD per il problema del modello di attendibilità. 
Nome di dominio (s) | | |Restituisce l'elenco dei domini che devono essere aggiunti per SFB per la connessione. |

---
title: 'Problemi noti: Surface Hub'
description: Questa pagina fornisce un elenco di problemi noti per Surface Hub
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/09/2021
ms.localizationpriority: Medium
ms.openlocfilehash: a9435db1de48b33d062d5e79d0d622f1d17815f0
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497486"
---
# <a name="known-issues-surface-hub"></a>Problemi noti: Surface Hub

Questo articolo elenca i problemi noti relativi a Surface Hub che eseguono il sistema operativo corrente, Windows 10 Team aggiornamento 2020.

Per assicurarsi che Surface Hub riceva gli aggiornamenti più recenti, accedere con un account amministratore e selezionare **Tutte le app** >  **Impostazioni** >  **Aggiorna e sicurezza** >  **Windows Update** e quindi installare tutti gli aggiornamenti.

| Problema               | Descrizione           | Rimedio                 |
|---------------------|-----------------------|------------------------|
| Quando si usa l'applicazione lavagna nei dispositivi Surface Hub, il contenuto non può essere condiviso tramite posta elettronica. | La funzionalità "Condivisione facile" è stata rimossa dalla nuova versione dell'app Lavagna. | Il modo consigliato per salvare il contenuto della lavagna consiste nell'accedere all'app. Se l'accesso non è possibile, un file di immagine può essere salvato nell'archiviazione locale e quindi condiviso tramite un servizio preferito dall'utente tramite il browser Edge. La funzionalità "Condivisione facile" verrà restituita in una versione futura della lavagna. [Altre informazioni sugli scenari di condivisione della lavagna.](https://support.microsoft.com/office/enable-microsoft-whiteboard-for-your-organization-1caaa2e2-5c18-4bdf-b878-2d98f1da4b24) |
| Alcuni surface hub vengono riavviati quando un utente seleziona "Fine sessione".  | Quando Surface Hub utenti del dispositivo selezionano la funzionalità "Fine sessione" per cancellare i dati utente, il dispositivo Surface Hub potrebbe rilevare erroneamente un errore di pulizia, forzando il riavvio di Windows per garantire che la pulizia venga eseguita correttamente.  | Microsoft è a conoscenza di questo problema e sta esaminando attivamente questo problema.  Microsoft fornirà informazioni aggiuntive su una risoluzione il più rapidamente possibile.|
| Quando si usano Surface Hub in ambienti GCC High, l'aggiunta alla riunione con un clic dal calendario della schermata iniziale non funziona. | Se si fa clic su "Partecipa" dal calendario Surface Hub per una riunione Teams in un ambiente GCC Alto, la riunione non viene avviata automaticamente. | Per partecipare alla riunione, avviare Teams e quindi parteciparvi dall'agenda visualizzata del client Teams. <br></br>Microsoft sta anche esaminando attivamente questo problema e fornirà informazioni aggiuntive su una risoluzione il più rapidamente possibile. |
| Le impostazioni QoS (Quality of Service) non funzionano come previsto | Dopo aver configurato le impostazioni QoS tramite i criteri MDM o il pacchetto di provisioning, i contrassegni DSCP non vengono applicati al traffico multimediale Teams o Skype for Business (SfB). | Microsoft è a conoscenza di questo problema e sta esaminando attivamente questo problema.  Microsoft fornirà informazioni aggiuntive su una risoluzione il più rapidamente possibile. |
| La sincronizzazione del calendario degli account dei dispositivi ibridi con le cassette postali locali non riesce. | Surface Hub dispositivi usano per impostazione predefinita l'autenticazione moderna per gli account presenti in Azure AD, anche se hanno cassette postali in ambienti locali in cui non è abilitata [l'autenticazione moderna ibrida](/microsoft-365/enterprise/configure-exchange-server-for-hybrid-modern-authentication). In questo scenario, Exchange interrompe la sincronizzazione delle riunioni con il dispositivo. Di conseguenza, il dispositivo non riceve né visualizza nuove riunioni. | Dopo [l'installazione di KB4598291](https://support.microsoft.com/help/4598291) (o di una successiva Windows CU), il provider di servizi di configurazione [di SurfaceHub](/windows/client-management/mdm/surfacehub-csp) ha un nuovo parametro ExchangeModernAuthEnabled disponibile per attivare o disattivare l'uso dell'autenticazione moderna. Può essere impostato su false tramite i criteri MDM o il [pacchetto di provisioning](https://download.microsoft.com/download/8/3/F/83FD5089-D14E-42E3-AF7C-6FC36F80D347/ExchangeModernAuthDisabled.ppkg) per impedire all'hub di usare l'autenticazione moderna. |
| Un piccolo subset di dispositivi Surface Hub v1 non è in grado di eseguire automaticamente l'aggiornamento all'aggiornamento Windows 10 Team 2020. | Questo piccolo subset di dispositivi Surface Hub v1 si trova in uno stato che impedisce la compatibilità con l'aggiornamento diretto tramite Windows Update. | Ricreare manualmente l'immagine del dispositivo nell'aggiornamento Windows 10 Team 2020 [usando lo strumento di ripristino Surface Hub](surface-hub-recovery-tool.md). |
| Surface Hub visualizza il messaggio "Nessun dispositivo di avvio" dopo il tentativo di installare l'aggiornamento Windows 10 Team 2020. | Durante il processo di Windows Update per Windows 10 Team 2020, alcuni dispositivi hub v1 passeranno a uno stato non avviabile. | Ricreare manualmente l'immagine del dispositivo nell'aggiornamento Windows 10 Team 2020 [usando lo strumento di ripristino Surface Hub](surface-hub-recovery-tool.md). |
| I dispositivi Hub 2S non sono in grado di ricevere gli aggiornamenti dei driver tramite WSUS. | Surface Hub 2S supporta Windows Update e Windows Update per le aziende per distribuire i driver; la distribuzione tramite Windows Server Update Services (WSUS) non è supportata. | Se si usa WSUS, eseguire la migrazione a Windows Update per le aziende.<br> <br>**Altre informazioni**: [Che cos'è l'aggiornamento Windows per le aziende?](/windows/deployment/update/waas-manage-updates-wufb) |
| Il Centro notifiche ha un collegamento Impostazioni non selezionabile. | Questo collegamento non deve essere visualizzato in Windows 10 Team e può causare confusione. | La funzionalità è la stessa di prima dell'aggiornamento 2020; La sezione App del menu Start deve essere usata per avviare l'app Impostazioni.  |
| Alcune impostazioni di facilità di accesso vengono mantenute al termine di una sessione| Quando gli utenti attivano l'interruttore Contrasto elevato dal menu Azioni rapide o dall'app Impostazioni, questo interruttore viene mantenuto al termine della sessione utente. Analogamente, se gli utenti modificano la visualizzazione delle notifiche per indicare 7 secondi rispetto ai 5 secondi definiti dall'amministratore, rimangono 7 secondi, anche se le altre impostazioni vengono reimpostate sui valori definiti dall'amministratore. | Gli utenti possono disattivare l'interruttore Contrasto elevato dal menu azioni rapide (cursore) accessibile sulla barra delle applicazioni subito dopo l'avvio di una sessione nell'hub. La durata di visualizzazione delle notifiche può essere impostata su un valore diverso tramite l'app Impostazioni dall'utente successivo. Questa impostazione è accessibile a tutti gli utenti. Microsoft sta attivamente cercando di trovare una soluzione a questo problema.| 

---
title: Rimozione di SSD in dispositivi Surface compatibili
description: Questo articolo, destinato ai tecnici IT qualificati, descrive le procedure consigliate per la rimozione e la sostituzione degli SSD in Surface laptop 3, Surface Pro X e Surface laptop go.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 10/21/2020
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 56c740b39d86ea3fab386e88efa6932e050bb957
ms.sourcegitcommit: 959d2d856b1e5b5c72cd636f576b5feb1b633048
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/21/2020
ms.locfileid: "11133171"
---
# Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili

> [!IMPORTANT]
> Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale. Descrive le procedure consigliate per l'uso da parte di tecnici IT qualificati per la rimozione e la sostituzione di SSD nei seguenti dispositivi Surface compatibili: 

- Laptop Surface 3 
- Surface Pro X 
- Portatile Surface go

> [!WARNING]
> Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.  Prestare sempre attenzione quando si intraprendono tali attività. Seguire le precauzioni e le procedure di sicurezza identificate nella [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440). È consigliabile ottenere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di Pierluigi per le aziende".

## Prerequisiti

> [!IMPORTANT]
> In questo articolo si presuppone che siano presenti le condizioni generali per la sicurezza e i criteri e le procedure di sicurezza descritti nella "Guida alla rimozione di Pierluigi per le aziende".

## Preparare la rimozione di SSD 

### Installare gli aggiornamenti più recenti 

Prima di iniziare, verificare che la versione di Windows in cui siano installati gli aggiornamenti più recenti:

1.  Andare a **Start**  >  **Settings**  >  **Update & Security**e selezionare **Controlla aggiornamenti**.
2. Installare tutti gli aggiornamenti disponibili.
3. Verificare le password necessarie per accedere al dispositivo.  
 
## Gestione BitLocker 

> [!NOTE]
> Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi. Per altre informazioni, vedere  [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan). 

### Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:

1.  In **Impostazioni**digitare **BitLocker** , quindi selezionare **Gestisci BitLocker**. 
2.  Selezionare **Disattiva BitLocker**. 
3.  Spegnere il dispositivo. 

### Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:

1.  In **Impostazioni**digitare **BitLocker**.
2. Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.
2.  Inserire un'unità USB. 
4.  Salvare la chiave di ripristino in archiviazione USB.  
5.  Rimuovere l'unità USB.  
6.  Spegnere il dispositivo. 

## Rimuovere e sostituire SSD 

1.  Rimuovere l'SSD usando le istruzioni in [Guida alla rimozione di Pierluigi per Enterprise](https://www.microsoft.com/download/100440). 
2.  Inserire l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.
3.  Accendere il nuovo dispositivo. Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.  
 
## Dopo la rimozione e la sostituzione di SSD

### Gestire gli SSD non crittografati 

Se durante il trasferimento l'SSD non è crittografato, eseguire le operazioni seguenti: 

1.  Accedere alla **Sign-In Options**  >  **password** delle opzioni di accesso (rappresentata dall'icona chiave sul lato sinistro).  
2.  Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).
3.  Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.  
4.  Eseguire di nuovo l'accesso usando la password e configurare Windows Hello e un PIN quando viene richiesto. 
    - Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.  
6.  Eseguire [Microsoft Surface Diagnostic Toolkit for business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) per verificare la funzionalità completa del dispositivo.  
7.  Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  **Activation**.  Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**. 
8.  Selezionare l'account di Office aprendo l' **app di Office**, passare all' **File**  >  **account** file e quindi verificare la ricerca di eventuali messaggi di errore.  

### Gestione degli SSD crittografati 

> [!NOTE]
> Sarà necessario disporre di un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB. 

Se l'SSD viene crittografato durante il trasferimento, eseguire le operazioni seguenti:

1.  Inserire l'unità USB che contiene la chiave di ripristino di BitLocker nel secondo dispositivo. 
2.  Aprire il file txt che contiene la chiave di ripristino di BitLocker. 
3.  Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.  
4.  Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata dall'icona chiave sul lato sinistro).  
5.  Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile).
6.  Dopo aver effettuato l'accesso completo, accedere all' **Start**  >  **account**Start  >  **Sign out**.  
7.  Eseguire di nuovo l'accesso usando la password e quindi configurare Windows Hello e aggiungere un PIN. 
8.  Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e se si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.  
9.  Eseguire **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** per verificare la funzionalità completa del dispositivo.  
10. Per controllare l'attivazione di Windows **Settings**, selezionare  >  **attivazione**impostazioni.  Se vengono visualizzati messaggi di errore, selezionare **risoluzione dei problemi**.
11. Per controllare lo stato dell'account di Office, aprire l' **app di Office**, quindi scegliere **File**  >  **account** file per verificare la disponibilità di eventuali messaggi di errore.

## Scopri di più

- [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440)
- [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

Hai ancora bisogno di assistenza? Accedere alla [community Microsoft](https://answers.microsoft.com/).
---
title: Rimozione di SSD in dispositivi Surface compatibili
description: Come trasferire un SSD da un dispositivo Surface a un altro.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: v-todmc
ms.topic: article
ms.date: 8/7/2020
ms.reviewer: johnk
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: 9cde08c8106703b50218bf7f5ed60e3d7fea0b67
ms.sourcegitcommit: 83530906c7e34c92bbee90b723321acd61e77669
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2020
ms.locfileid: "10918961"
---
# Procedure consigliate per la rimozione di SSD in dispositivi Surface compatibili

> [!IMPORTANT]
> Questo articolo è destinato all'uso da tecnici IT qualificati in un'organizzazione aziendale. Descrive le procedure consigliate per l'uso da parte di tecnici IT qualificati per la rimozione e la sostituzione di SSD in dispositivi Surface con SSD rimovibili. 

> [!WARNING]
> Aprire dispositivi e sostituire i componenti del dispositivo può presentare scosse elettriche, danni ai dispositivi, incendi e rischi per infortuni personali e altri pericoli.  Usare sempre cautela quando si intraprende tali attività. Seguire le precauzioni e le procedure di sicurezza identificate nella Guida alla rimozione di Pierluigi per le aziende. Microsoft consiglia di richiedere assistenza professionale se non si riesce a seguire le precauzioni e le procedure di sicurezza specificate nella Guida alla rimozione di Pierluigi per le aziende. 

## Prerequisiti

> [!IMPORTANT]
> In questo articolo si presuppone la comprensione delle precauzioni generali e delle procedure di sicurezza descritte in [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440).

## Preparare la rimozione di SSD 

### Installare gli aggiornamenti più recenti 

Prima di iniziare, verificare che la versione di Windows contenga gli aggiornamenti più recenti.

1.  Andare a **Start**  >  **Settings**  >  **Update & Security** e selezionare **Controlla aggiornamenti**. Installare tutti gli aggiornamenti disponibili.  

2.  Verificare di avere le password necessarie per accedere al dispositivo.  
 
## Gestire BitLocker 

> [!NOTE]
> Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi. Per altre informazioni, vedere la [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan). 

### Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per disattivare BitLocker:

1.  In **Impostazioni**digitare **BitLocker** e selezionare **Gestisci BitLocker**. 
2.  Selezionare **Disattiva BitLocker**. 
3.  Spegnere il dispositivo. 

### Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, eseguire la procedura seguente per generare una chiave di ripristino di BitLocker e salvarla nello spazio di archiviazione USB:

1.  Accedere a **Impostazioni** e digitare **BitLocker**.
2. Selezionare **Gestisci BitLocker**  > **Genera chiave di ripristino di BitLocker**.
2.  Inserire un'unità USB. 
3.  Salvare la chiave di ripristino in archiviazione USB.  
4.  Rimuovere l'unità USB.  
5.  Spegnere il dispositivo. 

## Rimuovere e sostituire l'SSD 

1.  Rimuovere l'SSD usando le istruzioni nella [Guida alla rimozione di Pierluigi per Enterprise](https://www.microsoft.com/download/100440). 
2. Posizionare l'SSD originale in un nuovo dispositivo e connettere il nuovo dispositivo a una connessione internet cablata.
2.  Accendere il nuovo dispositivo. Il dispositivo può passare a un aggiornamento del firmware durante l'avvio.  
 
## Dopo la rimozione e la sostituzione di SSD

### Gestire gli SSD non crittografati 

Se l'SSD rimane non crittografato durante il trasferimento, completare le operazioni seguenti: 

1.  Accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata come icona chiave sul lato sinistro).  
2.  Immettere la password e accedere in attesa del completamento dell'autenticazione a due fattori (se applicabile).
3.  Una volta completata l'accesso, accedere **Start**all'  >  **account**Start  >  **Sign out**.  
4.  Eseguire di nuovo l'accesso con la password e configurare Windows Hello e un PIN quando richiesto. 
    - Se il dispositivo è stato abilitato per BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, **accedere a BitLocker**  >  **Manage**BitLocker  >  **Resume**BitLocker.  
6.  Eseguire **SDT** per confermare la funzionalità del dispositivo completo.  
7.  Controlla l'attivazione di Windows passando all'attivazione **delle impostazioni**  >  **Activation**.  Se sono presenti messaggi di errore, selezionare **risoluzione dei problemi**. 
8.  Selezionare l'account di Office aprendo l' **app di Office**, quindi passare **File**all'  >  **account** file e verificare la ricerca di eventuali messaggi di errore.  

### Gestione degli SSD crittografati 

> [!NOTE]
> Sarà necessario un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB. 

Se l'SSD è rimasto crittografato durante il trasferimento, completare le operazioni seguenti:

1.  Inserire l'unità USB contenente la chiave di ripristino di BitLocker nel secondo dispositivo. 
2.  Aprire il file txt contenente la chiave di ripristino di BitLocker. 
3.  Immettere manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.  
4.  Dopo aver immesso correttamente la chiave di ripristino di BitLocker, accedere alla password delle **Opzioni di accesso**  >  **Password** (rappresentata dall'icona chiave sul lato sinistro).  
5.  Immettere la password e accedere, in attesa del completamento dell'autenticazione a due fattori (se applicabile) 
6.  Una volta completata l'accesso, accedere **Start**all'  >  **account**Start  >  **Sign out**.  
7.  Accedere di nuovo con la password e configurare Windows Hello e aggiungere un PIN. 
8.  Se il dispositivo è stato disabilitato da BitLocker per facilitare la rimozione e la sostituzione di SSD e si vuole abilitare BitLocker dopo la sostituzione, accedere a **Impostazioni**  >  **BitLocker**  >  **Manage**BitLocker  >  **Resume BitLocker**.  
9.  Eseguire **SDT** per confermare la funzionalità del dispositivo completo.  
10. Controlla l'attivazione di Windows passando all' **attivazione delle impostazioni**  >  **Activation**.  Se sono presenti messaggi di errore, selezionare **risoluzione dei problemi**.
11. Per controllare l'account di Office, aprire l' **app di Office**, quindi selezionare l'account **file**  >  **Account** e verificare la ricerca di eventuali messaggi di errore.

## Altre informazioni 

Per informazioni, vedi gli articoli seguenti:

- [Guida alla rimozione di Pierluigi per le aziende](https://www.microsoft.com/download/100440)
- [Guida al ripristino di BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

Hai ancora bisogno di assistenza? Accedere alla [community Microsoft](https://answers.microsoft.com/).
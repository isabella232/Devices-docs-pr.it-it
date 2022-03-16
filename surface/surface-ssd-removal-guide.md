---
title: Rimozione SSD nei dispositivi Surface compatibili
description: In questo articolo, destinato a tecnici IT qualificati, vengono descritte le procedure consigliate per la rimozione e la sostituzione di SSD in Surface Laptop 4, Surface Laptop 3, Surface Pro 7+, Surface Pro X e Surface Laptop Go.
ms.prod: w10
ms.localizationpriority: medium
ms.mktglfcycl: manage
ms.sitesec: library
author: mccoybot
ms.author: brrecord
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: ''
manager: laurawi
ms.audience: itpro
audience: ITPro
appliesto:
- Surface Laptop Studio
- Surface Pro 8
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
- Surface Laptop 4
- Windows 10
- Windows 11
ms.custom:
- CI 121887
- CSSTroubleshoot
ms.openlocfilehash: fbc1e2bee35874328637b23e66d148a4924030db
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449269"
---
# <a name="best-practices-for-ssd-removal-from-compatible-surface-devices"></a>Procedure consigliate per la rimozione di SSD da dispositivi Surface compatibili

> [!IMPORTANT]
> Questo articolo è destinato all'utilizzo da parte di tecnici IT qualificati solo in un'organizzazione aziendale. Vengono descritte le procedure consigliate per l'utilizzo da parte di tecnici IT qualificati nella rimozione e sostituzione di SSD nei seguenti dispositivi Surface compatibili:

- Surface Laptop Studio
- Surface Pro 8
- Surface Pro 7+
- Surface Pro X
- Surface Laptop Go
- Surface Laptop 3
- Surface Laptop 4

> [!WARNING]
> L'apertura di dispositivi e la sostituzione dei componenti del dispositivo possono presentare rischi di urto elettrico, danni al dispositivo, incendio e lesioni personali e altri rischi.  Prestare sempre attenzione quando si intraprendono tali attività. Seguire le precauzioni e le procedure di sicurezza identificate nella Guida alla rimozione [di rSSD per](https://www.microsoft.com/download/100440) Enterprise. Si consiglia di ottenere assistenza professionale se non è possibile seguire le precauzioni e le procedure di sicurezza specificate nella "Guida alla rimozione di rSSD per Enterprise".

## <a name="prerequisites"></a>Prerequisiti

> [!IMPORTANT]
> In questo articolo si presuppone che l'utente comprendi le procedure e i criteri e i criteri di sicurezza generali descritti nella "Guida alla rimozione di rSSD per Enterprise".

## <a name="prepare-for-ssd-removal"></a>Preparare la rimozione di SSD

### <a name="install-the-latest-updates"></a>Installare gli aggiornamenti più recenti

Prima di iniziare, verificare che nella versione di Windows siano installati gli aggiornamenti più recenti:

1. Vai a **Start** >  **Impostazioni** >  **Update & Sicurezza** e seleziona **Controlla aggiornamenti**.
2. Installare tutti gli aggiornamenti disponibili.
3. Verificare le password necessarie per accedere al dispositivo.  

## <a name="manage-bitlocker"></a>Gestione BitLocker

> [!NOTE]
> Questa sezione include suggerimenti per le organizzazioni che hanno abilitato la crittografia BitLocker per i dischi rigidi. Per ulteriori informazioni, vedere  [Guida al ripristino di BitLocker](/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan).

### <a name="if-bitlocker-encryption-is-disabled-during-ssd-removal-and-replacement"></a>Se la crittografia BitLocker è disabilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo può essere decrittografato prima della rimozione e della sostituzione di SSD, segui questi passaggi per disattivare BitLocker:

1. In **Impostazioni** digita **BitLocker** e quindi seleziona **Gestisci BitLocker**.
2. Seleziona **Disattiva BitLocker**.
3. Accensione del dispositivo.

### <a name="if-bitlocker-encryption-is-enabled-during-ssd-removal-and-replacement"></a>Se la crittografia BitLocker è abilitata durante la rimozione e la sostituzione di SSD

Se il dispositivo viene crittografato prima della rimozione e della sostituzione di SSD, segui questi passaggi per generare una chiave di ripristino di BitLocker e salvarla nell'archiviazione USB:

1. In **Impostazioni** digitare **BitLocker**.
2. Selezionare **Manage BitLockerGenerate** > **BitLocker Recovery Key**.
2. Inserire un'unità USB.
4. Salvare la chiave di ripristino nell'archiviazione USB.  
5. Rimuovere l'unità USB.  
6. Accensione del dispositivo.

## <a name="remove-and-replace-ssd"></a>Rimuovere e sostituire SSD

1. Rimuovi l'SSD usando le istruzioni appropriate per il dispositivo incluso nella Guida alla rimozione [di rSSD per Enterprise](https://www.microsoft.com/download/100440).
2. Inserisci l'SSD originale in un nuovo dispositivo e connetti il nuovo dispositivo a una connessione Internet cablata.
3. Accensione del nuovo dispositivo. Il dispositivo potrebbe passare attraverso un aggiornamento del firmware durante l'avvio.  

## <a name="after-ssd-removal-and-replacement"></a>Dopo la rimozione e la sostituzione di SSD

### <a name="manage-unencrypted-ssds"></a>Gestire gli SSD non crittografati

Se il file SSD non è crittografato durante il trasferimento, eseguire la procedura seguente:

1. Vai a **Opzioni di accessoPassword** >  (rappresentata dall'icona del tasto a sinistra).****  
2. Immetti la password e accedi in attesa del completamento dell'autenticazione a due fattori (se applicabile).
3. Dopo aver effettuato l'accesso, passare a **StartAccountSign** > **** >  **out**.  
4. Accedere di nuovo utilizzando la password e configurare Windows Hello e un PIN quando richiesto.
    - Se il dispositivo è stato disabilitato da BitLocker per facilitare la rimozione e la sostituzione di SSD e vuoi abilitare BitLocker dopo la sostituzione, vai a **BitLockerManage** >  **BitLockerResume** >  **BitLocker**.  
6. Esegui microsoft [Surface Diagnostic Toolkit for Business](surface-diagnostic-toolkit-for-business-intro.md) (SDT) per verificare la funzionalità completa del dispositivo.  
7. Controlla l Windows attivazione accedendo a **Impostazioni** >  **Activation**.  Se vengono visualizzati messaggi di errore, selezionare **Risoluzione dei problemi**.
8. Controlla il Office account aprendo **l'app Office**, passa a **FileAccount** >  e quindi controlla la presenza di eventuali messaggi di errore.****  

### <a name="managing-encrypted-ssds"></a>Gestione degli SSD crittografati

> [!NOTE]
> Sarà necessario disporre di un secondo dispositivo per leggere la chiave di ripristino di BitLocker salvata nell'unità USB.

Se l'SSD viene crittografato durante il trasferimento, eseguire la procedura seguente:

1. Inserisci l'unità USB che contiene la chiave di ripristino di BitLocker nel secondo dispositivo.
2. Aprire il .txt contenente la chiave di ripristino di Bitlocker.
3. Immetti manualmente la chiave di ripristino di BitLocker nel nuovo dispositivo che contiene l'SSD originale.  
4. Dopo aver immesso correttamente la chiave di ripristino di BitLocker, passare a **Opzioni** >  di **accessoPassword** (rappresentata dall'icona della chiave a sinistra).  
5. Immetti la password e accedi, in attesa del completamento dell'autenticazione a due fattori (se applicabile).
6. Dopo aver effettuato l'accesso, passare a **StartAccountSign** > **** >  **out**.  
7. Accedi di nuovo usando la password, quindi configura Windows Hello e aggiungi un PIN.
8. Se il dispositivo è stato disabilitato da BitLocker per facilitare la rimozione e la sostituzione di SSD e se vuoi abilitare BitLocker dopo la sostituzione, vai **a** >  Impostazioni **BitLockerManage** >  **BitLockerResume** >  **BitLocker**.  
9. Esegui **[SDT](surface-diagnostic-toolkit-for-business-intro.md)** per verificare la funzionalità completa del dispositivo.  
10. Per controllare Windows attivazione, **selezionare Impostazioni** >  **Attivazione**.  Se vengono visualizzati messaggi di errore, selezionare **Risoluzione dei problemi**.
11. Per controllare lo stato dell'account Office, apri **l'app Office**, quindi vai a **FileAccount** >  per verificare la presenza di eventuali messaggi di errore.****

## <a name="learn-more"></a>Scopri di più

- [Guida alla rimozione di rSSD per Enterprise](https://www.microsoft.com/download/100440)
- [Guida al ripristino di BitLocker](/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)

Hai ancora bisogno di assistenza? Passare a [Microsoft Community](https://answers.microsoft.com/).

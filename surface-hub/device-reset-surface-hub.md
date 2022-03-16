---
title: Reimpostazione e ripristino per Surface Hub
description: Descrive i processi di reimpostazione e ripristino per il Surface Hub e fornisce istruzioni.
ms.assetid: 44E82EEE-1905-464B-A758-C2A1463909FF
ms.reviewer: ''
manager: laurawi
keywords: reset Surface Hub, recover
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/10/2021
ms.localizationpriority: medium
ms.openlocfilehash: f0292d4c2ec599ba620ab87930fbecf3bab9e078
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449279"
---
# <a name="reset-and-recovery-for-surface-hub"></a>Reimpostazione e ripristino per Surface Hub

In questo articolo viene descritto come reimpostare un Microsoft Surface Hub.  

[Reimpostando il Surface Hub](#reset-a-surface-hub) il sistema operativo viene riportato all'ultimo aggiornamento cumulativo Windows e vengono rimossi tutti i file utente locali e le informazioni di configurazione. Le informazioni rimosse includono quanto segue:

- L'account del dispositivo
- Informazioni sull'account per gli amministratori locali del dispositivo
- Informazioni sull'aggiunta Azure AD dominio o l'aggiunta a un dominio
- Informazioni di registrazione di Gestione dispositivi mobili (MDM)
- Informazioni di configurazione impostate tramite MDM o l Impostazioni app

È possibile specificare se il processo di ripristino mantiene altre informazioni archiviate nel Surface Hub. Se non è possibile utilizzare l'opzione di reimpostazione, lo strumento Surface Hub [ripristino è](surface-hub-recovery-tool.md) disponibile per creare nuovamente l'immagine Surface Hub SSD.

## <a name="reset-a-surface-hub"></a>Reimpostare un Surface Hub

Potrebbe essere necessario reimpostare il Surface Hub per motivi come i seguenti:

- Si sta riconfigurando il dispositivo per un nuovo spazio riunioni e si desidera riconfigurarlo.
- Vuoi modificare la modalità di gestione locale del dispositivo.

Durante il processo di reimpostazione, se viene visualizzata una schermata vuota per lunghi periodi di tempo, attendere e non eseguire alcuna azione.

> [!WARNING]
> Il processo di reimpostazione del dispositivo può richiedere fino a sei ore. Non disattivare o scollegare il Surface Hub fino al termine del processo. Se interrompi il processo, il dispositivo diventa inoperabile. Il dispositivo richiede un servizio di garanzia per poter diventare nuovamente funzionante.

1. Nel dispositivo Surface Hub apri **Impostazioni**.

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra Impostazioni'app per Surface Hub.](images/sh-settings.png)

2. Selezionare **Aggiorna & sicurezza**.

   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra il gruppo Update & Security Impostazioni app per Surface Hub.](images/sh-settings-update-security.png)

3. Seleziona **Ripristino** e quindi, in **Reimposta dispositivo**, seleziona **Introduzione**.

   > [!IMPORTANT]
   > Assicurati di avere la chiave BitLocker disponibile prima di reimpostare il dispositivo, come verrà richiesto in un secondo momento. Per altre informazioni, vedi [Salvare la chiave di BitLocker](save-bitlocker-key-surface-hub.md). Quando l'hub si riavvia nella partizione di ripristino, ti verrà richiesto di immettere la chiave BitLocker. Se si ignora il prompt, la reimpostazione avrà esito negativo.
   
   > [!div class="mx-imgBorder"]
   > ![Immagine che mostra l'opzione Reimposta dispositivo nell Impostazioni app per Surface Hub.](images/sh-settings-reset-device.png)

   Al termine del processo di reimpostazione, Surface Hub il [programma di prima esecuzione.](first-run-program-surface-hub.md) Se il processo di reimpostazione rileva un problema, il Surface Hub viene riportato all'immagine del sistema operativo esistente in precedenza e quindi viene visualizzata la schermata iniziale.

## <a name="recover-a-locked-surface-hub"></a>Ripristinare un dispositivo Surface Hub bloccato

Se per qualche motivo il Surface Hub diventa inutilizzabile e non riesci ad avviare una reimpostazione dall'app Impostazioni, puoi comunque reimpostare il Surface Hub se hai la chiave di ripristino di BitLocker.

1. Individuare l'interruttore di alimentazione nella parte inferiore Surface Hub. L'interruttore di alimentazione è accanto alla connessione del cavo di alimentazione. Per ulteriori informazioni sull'interruttore di alimentazione, vedere Surface Hub [Site Readiness Guide (PDF)](surface-hub-site-readiness-guide.md).

2. Mentre nella Surface Hub viene visualizzata la schermata iniziale, utilizzare l'interruttore di alimentazione per disattivare l'Surface Hub.

3. Utilizzare l'interruttore di alimentazione per riattivare Surface Hub accensione. Il dispositivo viene avviato e viene visualizzata la Surface Hub logo. Quando vedi punti rotanti sotto il logo Surface Hub, usa l'interruttore di alimentazione per spegnere Surface Hub di nuovo.  

4. Ripetere il passaggio 3 due volte o finché non viene visualizzato Surface Hub messaggio "Preparazione del ripristino automatico". Dopo aver visualizzato questo messaggio, il Surface Hub viene visualizzata la Ambiente ripristino Windows schermo.
 
5. Selezionare **Ripristina**.

6. Selezionare **Reinstallazione locale.**

7. Selezionare **Pulire completamente l'unità.**
 
   ![ripristinare e pulire completamente l'unità.](images/recover-fully-clean-drive.png)

8. Ti verrà chiesto **Se sei pronto per reimpostare questo dispositivo?**. Selezionare **Ripristina**. 
   
   ![ripristinare e confermare la reimpostazione.](images/recover-confirm-reset.png)


## <a name="contact-support"></a>Supporto tecnico

Se hai domande o hai bisogno di assistenza, puoi [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).


## <a name="related-topics"></a>Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

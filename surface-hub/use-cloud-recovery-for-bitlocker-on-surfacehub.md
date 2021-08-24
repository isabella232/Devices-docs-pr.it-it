---
title: Come usare il ripristino cloud per BitLocker su un Surface Hub
description: Come usare il ripristino cloud per BitLocker su un Surface Hub
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: Impostazioni di accessibilità, app Impostazioni, Accessibilità
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: e220be7d4613fcb6a14180e482dc4f2c66a5ddc8
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911031"
---
# <a name="summary"></a>Riepilogo

Questo articolo descrive come usare la funzione di ripristino cloud se viene richiesto in modo imprevisto da BitLocker in un Surface Hub dispositivo.

> [!NOTE]
> È consigliabile eseguire questa procedura solo se non è disponibile una chiave di ripristino di BitLocker.

> [!WARNING]
> * Questo processo di ripristino elimina il contenuto dell'unità interna. Se il processo non riesce, l'unità interna diventerà completamente inutilizzabile. In questo caso, sarà necessario registrare una richiesta di servizio con Microsoft per una risoluzione.
> * Al termine del processo di ripristino, il dispositivo verrà reimpostato alle impostazioni di fabbrica e verrà ripristinato lo stato Out of Box Experience.
> * Dopo il ripristino, il Surface Hub deve essere completamente riconfigurato.

> [!IMPORTANT]
> Questo processo richiede una connessione Internet aperta che non utilizza un proxy o un altro metodo di autenticazione.

## <a name="cloud-recovery-process"></a>Processo di ripristino cloud

Per eseguire un ripristino cloud, attenersi alla seguente procedura:

1. Selezionare **Premi ESC per altre opzioni di ripristino.**

   ![Screenshot di Escape.](images/01-escape.png)

1. Selezionare **Ignora questa unità.**

   ![Screenshot of Skip this drive.](images/02-skip-this-drive.png)

1. Selezionare **Recupera dal cloud**.

   ![Screenshot of Recover from the cloud.](images/03-recover-from-cloud.png)

1. Selezionare **Sì**.

   ![Screenshot of Yes.](images/04-yes.png)

1. Selezionare **Reinstalla**.

   ![Screenshot of Reinstall.](images/05a-reinstall.png)

   ![Screenshot of Downloading.](images/05b-downloading.png)

1. Al termine del processo di ripristino cloud, avviare la riconfigurazione utilizzando **l'esperienza predefinita.**

   ![Screenshot of Out of the Box.](images/06-out-of-box.png)

## <a name="something-went-wrong-error-message"></a>Messaggio di errore "Si è verificato un problema"

Questo errore è in genere causato da problemi di rete che si verificano durante il download di ripristino. Quando si verifica questo problema, non disattivare l'hub perché non sarà possibile riavviarlo. Se viene visualizzato questo messaggio di errore, tornare al passaggio "Ripristino dal cloud" e quindi riavviare il processo di ripristino.

1. Selezionare **Annulla**.

   ![Screenshot di Cancel.](images/07-cancel.png)

1. Selezionare **Risoluzione dei problemi**.

   ![Screenshot of Troubleshoot.](images/08-troubleshoot.png)

1. Selezionare **Recupera dal cloud**.

   ![Screenshot of Recover from the cloud.](images/09-recover-from-cloud2.png)

1. Se **l'errore di rete** cablata non viene trovato, selezionare **Annulla**e quindi lasciare che il Surface Hub riscoprire la rete cablata.

   ![Screenshot of Wired network isn't found.](images/10-cancel.png)
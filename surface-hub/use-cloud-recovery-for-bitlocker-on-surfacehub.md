---
title: Come usare il recupero cloud per BitLocker in un Surface Hub
description: Come usare il recupero cloud per BitLocker in un Surface Hub
ms.assetid: c0bde23a-49de-40f3-a675-701e3576d44d
keywords: Impostazioni di accessibilità, app Impostazioni, Accessibilità
ms.prod: surface-hub
ms.sitesec: library
author: v-miegge
ms.author: v-miegge
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 7912f9d1bab2ba625995c56d6d7da4e6b2d3df37
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832672"
---
# Riepilogo

Questo articolo descrive come usare la funzione di ripristino cloud se viene richiesto in modo imprevisto da BitLocker su un dispositivo Surface Hub.

> [!NOTE]
> Seguire questa procedura solo se non è disponibile una chiave di ripristino di BitLocker.

> [!WARNING]
> * Questo processo di ripristino Elimina il contenuto dell'unità interna. Se il processo non riesce, l'unità interna diventerà completamente inutilizzabile. In questo caso, sarà necessario registrare una richiesta di servizio con Microsoft per una risoluzione.
> * Al termine del processo di ripristino, il dispositivo verrà reimpostato sulle impostazioni di fabbrica e restituito allo stato di esperienza della casella.
> * Dopo il ripristino, il mozzo della superficie deve essere completamente riconfigurato.

> [!IMPORTANT]
> Questo processo richiede una connessione Internet aperta che non usa un proxy o un altro metodo di autenticazione.

## Processo di ripristino del cloud

Per eseguire un ripristino cloud, eseguire le operazioni seguenti:

1. Selezionare **premi ESC per altre opzioni di ripristino**.

   ![Schermata di escape](images/01-escape.png)

1. Selezionare **Ignora l'unità**.

   ![Screenshot di skip this drive](images/02-skip-this-drive.png)

1. Selezionare **Recupera dal cloud**.

   ![Screenshot del ripristino dal cloud](images/03-recover-from-cloud.png)

1. Selezionare **Sì**.

   ![Schermata di sì](images/04-yes.png)

1. Selezionare **Reinstalla**.

   ![Screenshot della reinstallazione](images/05a-reinstall.png)

   ![Screenshot del download](images/05b-downloading.png)

1. Dopo il completamento del processo di ripristino della nuvola, avviare la riconfigurazione usando l' **esperienza fuori scatola**.

   ![Screenshot della casella fuori sede](images/06-out-of-box.png)

## Messaggio di errore "si è verificato un problema"

Questo errore è in genere causato da problemi di rete che si verificano durante il download del ripristino. Quando si verifica questo problema, non disattivare l'hub perché non sarà possibile riavviarlo. Se viene visualizzato questo messaggio di errore, tornare al passaggio "Recupera dal cloud" e quindi riavviare il processo di ripristino.

1. Selezionare **Annulla**.

   ![Screenshot di Cancel](images/07-cancel.png)

1. Selezionare **risoluzione dei problemi**.

   ![Screenshot della risoluzione dei problemi](images/08-troubleshoot.png)

1. Selezionare **Recupera dal cloud**.

   ![Screenshot del ripristino dal cloud](images/09-recover-from-cloud2.png)

1. Se la **rete cablata non viene trovata** si verifica un errore, selezionare **Annulla**e quindi l'hub Surface riscoprirà la rete cablata.

   ![Screenshot della rete cablata non trovata](images/10-cancel.png)
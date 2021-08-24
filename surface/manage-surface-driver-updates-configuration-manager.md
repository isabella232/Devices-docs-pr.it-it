---
title: Gestire gli aggiornamenti dei driver di Surface in Configuration Manager
description: Questo articolo descrive le opzioni disponibili per gestire e distribuire gli aggiornamenti del firmware e dei driver per i dispositivi Surface.
ms.assetid: b64879c4-37eb-4fcf-a000-e05cbb3d26ea
ms.reviewer: ''
author: v-miegge
manager: laurawi
keywords: Surface, Surface Pro 3, firmware, aggiornamento, dispositivo, gestire, distribuire, driver, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.author: daclark
ms.topic: article
audience: itpro
ms.openlocfilehash: da90a0481052d06c2108c8fd096d088bfacdcb87
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911001"
---
# <a name="manage-surface-driver-updates-in-configuration-manager"></a>Gestire gli aggiornamenti dei driver di Surface in Configuration Manager

## <a name="summary"></a>Riepilogo

A partire [da Microsoft System Center Configuration Manager versione 1710,](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates)puoi sincronizzare e distribuire gli aggiornamenti del firmware e dei driver di Microsoft Surface direttamente tramite il client di Configuration Manager. Il processo è simile alla distribuzione di aggiornamenti regolari. Tuttavia, alcune configurazioni aggiuntive sono necessarie per ottenere gli aggiornamenti dei driver di Surface nel catalogo.

## <a name="prerequisites"></a>Prerequisiti

Per gestire gli aggiornamenti dei driver di Surface, è necessario che siano soddisfatti i prerequisiti seguenti:

- È necessario usare Configuration Manager versione 1710 o successiva.
- Tutti i punti di aggiornamento software devono essere eseguiti Windows Server 2016 versione successiva. In caso contrario, Configuration Manager ignora questa impostazione e i driver di Surface non verranno sincronizzati.

> [!NOTE]
> Se l'ambiente non soddisfa i prerequisiti, fai riferimento ai [metodi alternativi](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) per distribuire gli aggiornamenti di driver e firmware di Surface nella [sezione Domande](#frequently-asked-questions-faq) frequenti.

## <a name="useful-log-files"></a>File di registro utili

I log seguenti sono particolarmente utili quando gestisci gli aggiornamenti dei driver di Surface.

|Nome registro|Descrizione|
|---|---|
|WCM.log|Registra i dettagli sulla configurazione del punto di aggiornamento software e sulle connessioni al server WSUS per le categorie, le classificazioni e le lingue degli aggiornamenti sottoscritti.|
|WsyncMgr.log|Registra i dettagli sul processo di sincronizzazione degli aggiornamenti software.|

Questi log si trovano nel server del sito che gestisce il SUP o nel SUP stesso se è installato direttamente in un server del sito.
Per un elenco completo dei log di Configuration Manager, vedere [File di registro in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).

## <a name="enabling-surface-driver-updates-management"></a>Abilitazione della gestione degli aggiornamenti dei driver di Surface

Per abilitare la gestione degli aggiornamenti dei driver di Surface in Configuration Manager, segui questi passaggi:

1. Nella console di Configuration Manager passare a **Amministrazione**  >  **Panoramica**  >  **Siti di configurazione del**  >  **sito**.
1. Selezionare il sito contenente il server SUP di primo livello per l'ambiente.
1. Sulla barra multifunzione selezionare **Configura componenti del sito**e quindi Selezionare Punto di aggiornamento **software.** In caso contrario, fare clic con il pulsante destro del mouse sul sito e quindi **scegliere Configura componenti**del sito Punto di aggiornamento  >  **software.**
1. Nella scheda **Classificazioni seleziona** la casella di controllo Includi driver **e firmware di Microsoft Surface.**

   ![Proprietà del componente punto di aggiornamento software.](images/manage-surface-driver-updates-1.png)

1. Quando viene visualizzato il messaggio di avviso seguente, selezionare **OK**.

   ![Configuration Manager.](images/manage-surface-driver-updates-2.png)

1. Nella scheda Prodotti selezionare i prodotti che si desidera aggiornare e quindi fare clic su **OK.**

   La maggior parte dei driver appartiene ai gruppi di prodotti seguenti:

   - Windows 10 e versioni successive
   - Windows 10 aggiornamento e versioni successive & di manutenzione
   - Windows 10 Aggiornamento dell'anniversario e driver di manutenzione successivi
   - Windows 10 Aggiornamento dell'anniversario e aggiornamento successivo & di manutenzione
   - Windows 10 Creators Update e successivi driver di manutenzione
   - Windows 10 Creators Update e versioni successive & di manutenzione
   - Windows 10 Fall Creators Update e successivi driver di manutenzione
   - Windows 10 Fall Creators Update e versioni successive di & di manutenzione
   - Windows 10 Driver di manutenzione S e successivi
   - Windows 10 Driver di manutenzione S versione 1709 e successive per il testing
   - Windows 10 S Versione 1709 e versioni successive dei driver & manutenzione per i test

   > [!NOTE]
   > La maggior parte dei driver di Surface appartiene a Windows 10 gruppi di prodotti. Potrebbe non essere necessario selezionare tutti i prodotti elencati qui. Per ridurre il numero di prodotti che popolano il Catalogo aggiornamenti, è consigliabile selezionare solo i prodotti richiesti dall'ambiente per la sincronizzazione.

## <a name="verifying-the-configuration"></a>Verifica della configurazione

Per verificare che sup sia configurato correttamente, attenersi alla seguente procedura:

1. Aprire WsyncMgr.log e quindi cercare la voce seguente:

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   Se una delle voci seguenti viene registrata in WsyncMgr.log, ricontrollare il passaggio 4 della sezione precedente:

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. Aprire WCM.log e quindi cercare una voce simile alla seguente:

   ![Impostazioni WCM.log.](images/manage-surface-driver-updates-3.png)

   Questa voce è un elemento XML che elenca tutti i gruppi di prodotti e la classificazione attualmente sincronizzati dal server SUP. Ad esempio, potrebbe essere visualizzata una voce simile alla seguente:

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   Se non è possibile trovare i prodotti selezionati nel passaggio 6 della sezione precedente, verificare se le impostazioni SUP sono state salvate.

   Puoi anche attendere il termine della sincronizzazione successiva e quindi verificare se gli aggiornamenti del driver e del firmware di Surface sono elencati in Aggiornamenti software nella console di Configuration Manager. Ad esempio, la console potrebbe visualizzare le informazioni seguenti.

   ![Tutti i risultati della ricerca aggiornamenti software.](images/manage-surface-driver-updates-4.png)

## <a name="manual-synchronization"></a>Sincronizzazione manuale

Se non si desidera attendere la sincronizzazione successiva, eseguire la procedura seguente per avviare una sincronizzazione:

1. Nella console di Configuration Manager passare a **Software Library**  >  **Overview**  >  **Software Updates**All Software  >  **Updates**.
1. Sulla barra multifunzione selezionare **Sincronizza aggiornamenti software.** In caso contrario, fare **clic con il pulsante destro del**mouse su Tutti gli aggiornamenti software e quindi scegliere Sincronizza aggiornamento **software.**
1. Monitorare l'avanzamento della sincronizzazione cercando le voci seguenti in WsyncMgr.log:

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   sync: SMS synchronizing categories 
   sync: SMS synchronizing categories, processed 0 out of 311 items (0%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing categories, processed 311 out of 311 items (100%)
   sync: SMS synchronizing updates

   Synchronizing update 7eaa0148-c42b-45fd-a1ab-012c82972de6 - Microsoft driver update for Surface Type Cover Integration
   Synchronizing update 2dcb07f8-37ec-41ef-8cd5-030bf24dc1d8 - Surface driver update for Surface Pen Pairing
   Synchronizing update 63067414-ae52-422b-b3d1-0382a4d6519a - Surface driver update for Surface UEFI
   Synchronizing update 8e4e3a41-a784-4dd7-9a42-041f43ddb775 - Surface driver update for Surface Integration
   Synchronizing update 7f8baee8-419f-47e2-918a-045a15a188e7 - Microsoft driver update for Surface DTX
   Synchronizing update aed66e05-719b-48cd-a0e7-059e50f67fdc - Microsoft driver update for Surface Base Firmware Update
   Synchronizing update 8ffe1526-6e66-43cc-86e3-05ad92a24e3a - Surface driver update for Surface UEFI
   Synchronizing update 74102899-0a49-48cf-97e6-05bde18a27ff - Microsoft driver update for Surface UEFI
   ```

## <a name="deploying-surface-firmware-and-driver-updates"></a>Distribuzione degli aggiornamenti del firmware e dei driver di Surface

Puoi distribuire gli aggiornamenti del firmware e dei driver di Surface nello stesso modo in cui distribuisci altri aggiornamenti.

Per ulteriori informazioni sulla distribuzione, [vedere System Center 2012 Configuration Manager–Part7: Software Updates (Deploy)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).

## <a name="frequently-asked-questions-faq"></a>Domande frequenti

**Dopo aver seguito i passaggi descritti in questo articolo, i driver di Surface non sono ancora sincronizzati. Perché?**

Se si esegue la sincronizzazione da un server wsus (upstream Windows Server Update Services), invece di Microsoft Update, verificare che il server WSUS upstream sia configurato per supportare e sincronizzare gli aggiornamenti dei driver di Surface. Tutti i server downstream sono limitati agli aggiornamenti presenti nel database del server WSUS upstream.

Esistono più di 68.000 aggiornamenti classificati come driver in WSUS. Per impedire la sincronizzazione dei driver non correlati a Surface con Configuration Manager, Microsoft filtra la sincronizzazione dei driver in base a un elenco consenti. Dopo che il nuovo elenco consenti viene pubblicato e incorporato in Configuration Manager, i nuovi driver vengono aggiunti alla console dopo la sincronizzazione successiva. Microsoft mira a far aggiungere i driver di Surface all'elenco consenti ogni mese in allineamento con i rilasci degli aggiornamenti mensili per renderli disponibili per la sincronizzazione con Configuration Manager.

Se l'ambiente di Configuration Manager è offline, viene importato un nuovo elenco consenti ogni volta che si importano gli aggiornamenti di [manutenzione](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) in Configuration Manager. Sarà inoltre necessario importare un [nuovo catalogo WSUS](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) contenente i driver prima che gli aggiornamenti siano visualizzati nella console di Configuration Manager. Poiché un ambiente WSUS autonomo contiene più driver di un SUP di Configuration Manager, ti consigliamo di stabilire un ambiente di Configuration Manager con funzionalità online e di configurarlo per sincronizzare i driver di Surface. In questo modo viene fornita un'esportazione WSUS di dimensioni inferiori, simile all'ambiente offline.

Se l'ambiente di Configuration Manager è online e in grado di rilevare nuovi aggiornamenti, riceverai automaticamente gli aggiornamenti dell'elenco. Se non vengono visualizzati i driver previsti, esaminare i file WCM.log e WsyncMgr.log per eventuali errori di sincronizzazione.

**L'ambiente di Configuration Manager è offline. È possibile importare manualmente i driver di Surface in WSUS?**

No. Anche se l'aggiornamento viene importato in WSUS, l'aggiornamento non verrà importato nella console di Configuration Manager per la distribuzione se non è elencato nell'elenco consenti. È necessario utilizzare lo [strumento di connessione del servizio](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) per importare gli aggiornamenti di manutenzione in Configuration Manager per aggiornare l'elenco consenti.

**Quali metodi alternativi sono necessari per distribuire gli aggiornamenti del firmware e dei driver di Surface?**

Per informazioni su come distribuire gli aggiornamenti del firmware e dei driver di Surface tramite canali alternativi, vedi Gestire gli aggiornamenti del firmware e [dei driver di Surface.](manage-surface-driver-and-firmware-updates.md) Se vuoi scaricare il file .msi o .exe e quindi distribuirlo tramite i canali di distribuzione software tradizionali, vedi [Mantenere il firmware di Surface aggiornato con Configuration Manager.](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager)

## <a name="additional-information"></a>Ulteriori informazioni

Per altre informazioni sugli aggiornamenti del firmware e dei driver di Surface, vedi gli articoli seguenti:

- [Gestire gli aggiornamenti dei driver e del firmware di Surface](manage-surface-driver-and-firmware-updates.md)
- [Considerazioni per Surface e System Center Configuration Manager](considerations-for-surface-and-system-center-configuration-manager.md)

---
title: Gestire gli aggiornamenti dei driver di Surface in Configuration Manager
description: Questo articolo descrive le opzioni disponibili per gestire e distribuire gli aggiornamenti del firmware e del driver per i dispositivi Surface.
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
ms.openlocfilehash: be32309b26ff6a873c36927cc39595022c4dbb90
ms.sourcegitcommit: ed4478dd3c6116a25b1e01a3a0f5ff6c1f940013
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "10897074"
---
# Gestire gli aggiornamenti dei driver di Surface in Configuration Manager

##  <a name="summary"></a>Riepilogo

A partire da [Microsoft System Center Configuration Manager versione 1710](https://docs.microsoft.com/sccm/core/plan-design/changes/whats-new-in-version-1710#software-updates), è possibile sincronizzare e distribuire il firmware Microsoft Surface e gli aggiornamenti dei driver direttamente tramite il client Configuration Manager. Il processo è simile alla distribuzione di aggiornamenti regolari. Tuttavia, sono necessarie altre configurazioni per ottenere gli aggiornamenti di Surface driver nel catalogo.

##  <a name="prerequisites"></a>Prerequisiti

Per gestire gli aggiornamenti dei driver di Surface, è necessario soddisfare i prerequisiti seguenti:

- È necessario usare Configuration Manager versione 1710 o una versione successiva.
- Tutti i punti di aggiornamento software (SUP) devono eseguire Windows Server 2016 o una versione successiva. In caso contrario, Configuration Manager ignora questa impostazione e i driver di superficie non verranno sincronizzati.

> [!NOTE]
> Se l'ambiente non soddisfa i prerequisiti, vedere i [metodi alternativi](https://support.microsoft.com/help/4098906/manage-surface-driver-updates-in-configuration-manager#1) per distribuire gli aggiornamenti del driver di superficie e del firmware nella sezione [domande frequenti](#frequently-asked-questions-faq) .

## File di log utili

I registri seguenti sono particolarmente utili per gestire gli aggiornamenti di Surface driver.

|Nome log|Descrizione|
|---|---|
|WCM. log|Registra i dettagli sulla configurazione del punto di aggiornamento software e sulle connessioni al server WSUS per categorie di aggiornamento sottoscritte, classificazioni e lingue.|
|WsyncMgr. log|Registra i dettagli sul processo di sincronizzazione degli aggiornamenti software.|

Questi registri si trovano nel server del sito che gestisce il SUP o nel SUP stesso se è installato direttamente in un server del sito.
Per un elenco completo dei log di Configuration Manager, vedere [file di log in System Center Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files).

## Abilitazione della gestione aggiornamenti di Surface driver

Per abilitare la gestione degli aggiornamenti di Surface driver in Configuration Manager, eseguire le operazioni seguenti:

1. Nella console di Configuration Manager accedere ai siti di configurazione del sito di **Amministrazione**  >  **Panoramica**  >  **Site Configuration**  >  **Sites**.
1. Selezionare il sito che contiene il server SUP di primo livello per l'ambiente.
1. Sulla barra multifunzione selezionare **Configura componenti sito**e quindi selezionare il **punto di aggiornamento software**. In alternativa, fare clic con il pulsante destro del mouse sul sito e quindi scegliere **Configura**  >  **punto di aggiornamento software**componenti sito.
1. Nella scheda **classificazioni** selezionare la casella di controllo **Includi Microsoft Surface Drivers and Firmware Updates** .

   ![Proprietà del componente punto di aggiornamento software](images/manage-surface-driver-updates-1.png)

1. Quando viene visualizzato il messaggio di avviso seguente, selezionare **OK**.

   ![Configuration Manager](images/manage-surface-driver-updates-2.png)

1. Nella scheda prodotti selezionare i prodotti che si desidera aggiornare e quindi scegliere **OK**.

   La maggior parte dei driver appartiene ai gruppi di prodotti seguenti:

   - Driver per Windows 10 e versioni successive
   - Windows 10 e aggiornamento successivo & i driver di manutenzione
   - Aggiornamento dell'anniversario di Windows 10 e driver di manutenzione successivi
   - Aggiornamento dell'anniversario di Windows 10 e aggiornamento successivo & driver di manutenzione
   - Aggiornamento di Windows 10 Creators e driver di manutenzione successivi
   - Aggiornamento di Windows 10 Creator e aggiornamento successivo & driver di manutenzione
   - Aggiornamento di Windows 10 Fall Creators e driver di manutenzione successivi
   - Aggiornamento di Windows 10 Fall Creators e aggiornamento successivo & driver di manutenzione
   - Driver di manutenzione di Windows 10 S e versioni successive
   - Windows 10 S versione 1709 e versioni successive di manutenzione per i test
   - Windows 10 S versione 1709 e successive aggiornamento & i driver di manutenzione per i test

   > [!NOTE]
   > La maggior parte dei driver di superficie appartiene a più gruppi di prodotti Windows 10. Potrebbe non essere necessario selezionare tutti i prodotti elencati qui. Per ridurre il numero di prodotti che popolano il catalogo di aggiornamento, è consigliabile selezionare solo i prodotti richiesti dall'ambiente per la sincronizzazione.

## Verifica della configurazione

Per verificare che il SUP sia configurato correttamente, eseguire le operazioni seguenti:

1. Aprire WsyncMgr. log e quindi cercare la voce seguente:

   ```console
   Surface Drivers can be supported in this hierarchy since all SUPs are on Windows Server 2016, WCM SCF property Sync Catalog Drivers is set.

   Sync Catalog Drivers SCF value is set to : 1
   ```

   Se una delle voci seguenti è stata registrata in WsyncMgr. log, ripetere il controllo del passaggio 4 nella sezione precedente:

   ```console
   Sync Surface Drivers option is not set

   Sync Catalog Drivers SCF value is set to : 0
   ```

1. Aprire WCM. log e cercare una voce simile alla seguente:

   ![Impostazioni di WCM. log](images/manage-surface-driver-updates-3.png)

   Questa voce è un elemento XML che elenca tutti i gruppi di prodotti e la classificazione attualmente sincronizzati dal server SUP. Ad esempio, potrebbe essere visualizzata una voce simile alla seguente:

   ```xml
   <Categories>
       <Category Id="Product:05eebf61-148b-43cf-80da-1c99ab0b8699"><![CDATA[Windows 10 and later drivers]]></Category>
       <Category Id="Product:06da2f0c-7937-4e28-b46c-a37317eade73"><![CDATA[Windows 10 Creators Update and Later Upgrade & Servicing Drivers]]></Category>
       <Category Id="Product:c1006636-eab4-4b0b-b1b0-d50282c0377e"><![CDATA[Windows 10 S and Later Servicing Drivers]]></Category>
   </Categories>
   ```

   Se non si trovano i prodotti selezionati nel passaggio 6 nella sezione precedente, verificare che le impostazioni SUP siano salvate.

   È anche possibile attendere il completamento della sincronizzazione successiva, quindi verificare se il driver della superficie e gli aggiornamenti del firmware sono elencati in aggiornamenti software nella console di Configuration Manager. Ad esempio, la console può visualizzare le informazioni seguenti.

   ![Tutti i risultati della ricerca degli aggiornamenti software](images/manage-surface-driver-updates-4.png)

## Sincronizzazione manuale

Se non si vuole attendere la sincronizzazione successiva, eseguire la procedura seguente per avviare una sincronizzazione:

1. Nella console di Configuration Manager, vai a Panoramica della **raccolta software**  >  **Overview**  >  **Aggiorna**  >  **tutti gli aggiornamenti software**.
1. Sulla barra multifunzione selezionare **Sincronizza aggiornamenti software**. In alternativa, fare clic con il pulsante destro del mouse su **tutti gli aggiornamenti software**e quindi scegliere **Sincronizza aggiornamento software**.
1. Monitorare lo stato di avanzamento della sincronizzazione cercando le voci seguenti in WsyncMgr. log:

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

## Distribuzione di aggiornamenti di Surface firmware e driver

È possibile distribuire gli aggiornamenti del firmware e del driver della superficie nello stesso modo in cui si distribuiscono altri aggiornamenti.

Per altre informazioni sulla distribuzione, vedere [System Center 2012 Configuration Manager-part7: aggiornamenti software (distribuzione)](https://blogs.technet.microsoft.com/elie/2012/05/25/system-center-2012-configuration-managerpart7-software-updates-deploy/).

##  <a name="faq"></a>Domande frequenti

**Dopo aver seguito i passaggi descritti in questo articolo, i driver di Surface non sono ancora sincronizzati. Perché?**

Se si effettua la sincronizzazione da un server Windows Server Update Services (WSUS) upstream, invece di Microsoft Update, verificare che il server WSUS upstream sia configurato per supportare e sincronizzare gli aggiornamenti dei driver di superficie. Tutti i server downstream sono limitati agli aggiornamenti presenti nel database del server WSUS upstream.

Sono disponibili più di 68.000 aggiornamenti classificati come driver in WSUS. Per evitare che i driver correlati a una superficie vengano sincronizzati con Configuration Manager, Microsoft filtra la sincronizzazione del driver rispetto a un elenco di Consenti. Dopo che il nuovo elenco Consenti viene pubblicato e incorporato in Gestione configurazione, i nuovi driver vengono aggiunti alla console dopo la sincronizzazione successiva. Microsoft mira a ottenere i driver Surface aggiunti all'elenco Consenti ogni mese in allineamento con le versioni di aggiornamento mensili per renderle disponibili per la sincronizzazione con Configuration Manager.

Se l'ambiente di gestione configurazione è offline, viene importato un nuovo elenco di Consenti ogni volta che si importano [gli aggiornamenti della manutenzione](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) in Configuration Manager. Sarà inoltre necessario importare un [nuovo catalogo WSUS](https://docs.microsoft.com/mem/configmgr/sum/get-started/synchronize-software-updates-disconnected) che contiene i driver prima che gli aggiornamenti vengano visualizzati nella console di Configuration Manager. Poiché un ambiente WSUS autonomo contiene più driver di un SUP di Configuration Manager, è consigliabile stabilire un ambiente di gestione configurazione con funzionalità online e configurarlo per sincronizzare i driver di Surface. In questo articolo viene fornita un'esportazione più piccola di WSUS che assomiglia molto all'ambiente offline.

Se l'ambiente di Configuration Manager è online ed è in grado di rilevare nuovi aggiornamenti, si riceveranno automaticamente gli aggiornamenti all'elenco. Se i driver previsti non sono visualizzati, vedere i file WCM. log e WsyncMgr. log per eventuali errori di sincronizzazione.

**L'ambiente di gestione configurazione non è in linea. È possibile importare manualmente i driver di Surface in WSUS?**

No. Anche se l'aggiornamento viene importato in WSUS, l'aggiornamento non verrà importato nella console di Configuration Manager per la distribuzione se non è elencato nell'elenco Consenti. È necessario usare lo [strumento di connessione del servizio](https://docs.microsoft.com/mem/configmgr/core/servers/manage/use-the-service-connection-tool) per importare gli aggiornamenti di manutenzione in Gestione configurazione per aggiornare l'elenco Consenti.

**Quali metodi alternativi è necessario distribuire per il driver di superficie e gli aggiornamenti del firmware?**

Per informazioni su come distribuire gli aggiornamenti del driver di superficie e del firmware tramite canali alternativi, vedere [gestire gli aggiornamenti del driver di superficie e del firmware](manage-surface-driver-and-firmware-updates.md). Se si vuole scaricare il file con estensione msi o exe e quindi distribuire i canali tradizionali di distribuzione del software, vedere [mantenere aggiornato il firmware della superficie con Configuration Manager](https://docs.microsoft.com/archive/blogs/thejoncallahan/keeping-surface-firmware-updated-with-configuration-manager).

##  <a name="learn-more"></a>Altre informazioni

Per altre informazioni sul driver di superficie e gli aggiornamenti del firmware, vedere gli articoli seguenti:

- [Gestire gli aggiornamenti dei driver e del firmware di Surface](manage-surface-driver-and-firmware-updates.md)
- [Considerazioni per Surface e System Center Configuration Manager](considerations-for-surface-and-system-center-configuration-manager.md)

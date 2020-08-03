---
title: Come abilitare la riattivazione dell'alimentazione per Surface
ms.author: v-todmc
author: mccoybot
ms.date: 7/30/2020
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
ms.custom:
- CI 121602
ms.reviewer: johnk@cadencepreferred.com
description: Descrive come abilitare e disabilitare la riattivazione in Power per i dispositivi Surface.
keywords: aggiornamento, distribuzione, driver, WOL, Wake-on-LAN
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.openlocfilehash: 271831651280299a40c4e7a7480fa86e29bd1cf5
ms.sourcegitcommit: f875a45961ff5f3c04006afc8690b5e5965e4d80
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "10903019"
---
# Riattivazione in Power per i dispositivi Surface

I dispositivi Surface possono essere spenti mentre si è lontani dalla scrivania o impostati in modalità di sospensione per salvare la batteria. Per migliorare la gestibilità di questi dispositivi, Wake on Power consente ai dispositivi Surface compatibili di iniziare automaticamente la riconnessione a Power. La configurazione di Wake on Power richiede l'uso della modalità di gestione di Surface Enterprise (SEMM) tramite Surface UEFI Configurator o UEFI Manager.

Wake on Power è una funzionalità disponibile nei dispositivi seguenti:

- Surface Book 3
- Surface Pro 7
- Laptop Surface 3
- Surface Pro X 

## Panoramica e prerequisiti

Puoi usare Surface UEFI Configurator per configurare singole impostazioni UEFI salvate in un pacchetto di Windows Installer. msi per la distribuzione in dispositivi di destinazione. 

> [!NOTE]
> Questo articolo presuppone che si abbia familiarità con l'uso di SEMM. Per altre informazioni, vedere la documentazione sulla [modalità di gestione di Surface Enterprise (SEMM)](surface-enterprise-management-mode.md) .

## Per abilitare la riattivazione in Power

1.  Scaricare l'ultima versione di [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).
2.  Accedere al dispositivo Surface come amministratore, aprire il **Configuratore di Surface UEFI**, selezionare **dispositivi Surface**e quindi fare clic su **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Selezionare dispositivi Surface e selezionare Avanti.":::
3.  Selezionare **Avvia** e quindi in **pacchetto di configurazione** Selezionare **Crea**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Selezionare Crea pacchetto di configurazione.":::
4.  Selezionare **protezione certificato** e aggiungere il file con estensione pfx certificato. Dopo aver immesso la password, selezionare **Avanti**. Aggiungere la **protezione con password**, in base alle esigenze e quindi selezionare **Avanti**.
5.  Nella pagina **scegliere il tipo di superficie da cui si vuole assegnare la destinazione** selezionare i dispositivi di destinazione in base alle esigenze. Ad esempio, **Surface Pro 7**.
6.  Nella pagina **funzionalità avanzate** selezionare **riattiva in Power** e imposta **su**attivato. Seleziona **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Selezionare Riattiva in Power e imposta su attivato."::: 
7.  Nella pagina **completata** selezionare **fine**. Se è la prima volta che fornisci le impostazioni al dispositivo, verrà richiesto di specificare gli ultimi due caratteri dell'identificazione personale del certificato. 
8.  Salvare il pacchetto MSI. 

## Applicare il pacchetto MSI 

Puoi applicare il pacchetto MSI ai dispositivi della rete usando strumenti di distribuzione del software come Microsoft endpoint Configuration Manager. Questa procedura include i passaggi per installare il pacchetto nel computer locale. 

1.  Aprire un prompt dei comandi con privilegi elevati e immettere il percorso completo del file MSI per eseguire il pacchetto MSI. 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  Nella finestra di dialogo **avviso** selezionare **OK** o disabilitare BitLocker in base alle esigenze.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Selezionare OK o disabilitare BitLocker in base alle esigenze.":::
3.  Nella pagina di benvenuto selezionare **Avanti** per eseguire il pacchetto e applicare l'impostazione UEFI appena configurata.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Una pagina iniziale, selezionare Avanti.":::
4.  Riavviare il dispositivo. 

La riattivazione dell'alimentazione è ora configurata. Per testare l'impostazione, disattivare il dispositivo, scollegare l'alimentazione e quindi riconnettere l'alimentazione. Il dispositivo verrà avviato automaticamente. 

## Altre informazioni

Per altre informazioni, vedere gli articoli seguenti. 

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)
- [Riattivare la LAN per i dispositivi Surface](wake-on-lan-for-surface-devices.md)

Hai ancora bisogno di assistenza? Accedere alla [community Microsoft](https://answers.microsoft.com/).
---
title: Come abilitare la riattivazione dell'alimentazione per Surface
ms.author: v-todmc
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
appliesto:
- Surface Book 3
- Surface Pro 7+
- Surface Pro 7
- Surface Laptop 3
- Surface Pro X
- Surface Laptop Go
ms.custom:
- CI 121602
ms.reviewer: hachidan
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
ms.date: 01/15/2021
ms.openlocfilehash: 6ad359861f6af29c567bf0fbf26878ec15c7c642
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271560"
---
# Riattivazione alimentazione per i dispositivi Surface

I dispositivi Surface possono essere spenti quando si è lontani dalla propria scrivania o impostati come modalità di sospensione per risparmiare la durata della batteria. Per migliorare la gestibilità di questi dispositivi, Wake on Power consente ai dispositivi Surface compatibili di iniziare automaticamente quando si riconnetteno a Power. Per configurare la riattivazione in Power, è possibile usare la modalità di gestione di Surface Enterprise (SEMM) tramite Surface UEFI Configurator o UEFI Manager.

La funzionalità riattiva in Power è disponibile nei dispositivi seguenti:

- Surface Pro 7 +
- Surface Book 3
- Surface Pro 7
- Laptop Surface 3
- Portatile Surface go
- Surface Pro X 


## Panoramica e prerequisiti

Surface UEFI Configurator consente di salvare singole impostazioni UEFI in un pacchetto di Windows Installer. msi per la distribuzione in dispositivi di destinazione. 

> [!NOTE]
> Questo articolo presuppone che tu sappia usare SEMM. Per altre informazioni, vedere la documentazione sulla [modalità di gestione di Surface Enterprise (SEMM)](surface-enterprise-management-mode.md) .

## Per abilitare la riattivazione in Power

1.  Scaricare l'ultima versione di [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).
2.  Accedere al dispositivo Surface come amministratore, aprire il **Configuratore di Surface UEFI**, selezionare **dispositivi Surface**e quindi fare clic su **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Selezionare dispositivi Surface e selezionare Avanti.":::
3.  Selezionare **Start**, quindi selezionare **Crea** in **pacchetto di configurazione**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Selezionare Crea pacchetto di configurazione.":::
4.  Selezionare **protezione certificato**e aggiungere il file con estensione pfx certificato. 
5. Immettere la password, scegliere **Avanti**, aggiungere la **protezione tramite password**, in base alle esigenze e quindi selezionare **Avanti**.
6.  Nella pagina **scegliere il tipo di superficie da cui si vuole assegnare la destinazione** selezionare i dispositivi di destinazione in base alle esigenze. Ad esempio, selezionare **Surface Pro 7**.
7.  Nella pagina **funzionalità avanzate** selezionare **riattiva in Power**, impostare la caratteristica **su**attivato e quindi selezionare **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Selezionare Riattiva in Power e imposta su attivato."::: 
8.  Nella pagina **completata** selezionare **fine**.

    > [!NOTE]
    > Se è la prima volta che si forniscono impostazioni al dispositivo, verrà richiesto di specificare anche gli ultimi due caratteri dell'identificazione personale del certificato. 
9.  Salvare il pacchetto MSI. 

## Applicare il pacchetto MSI 

Puoi applicare il pacchetto MSI ai dispositivi della rete usando strumenti di distribuzione del software come Microsoft endpoint Configuration Manager. Questa procedura include i passaggi per installare il pacchetto nel computer locale. 

1.  In un prompt dei comandi con privilegi elevati, immettere il percorso completo del file MSI per eseguire il pacchetto MSI. 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  Nella finestra di dialogo **avviso** selezionare **OK** o disabilitare BitLocker, in base alle esigenze.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Selezionare OK o disabilitare BitLocker in base alle esigenze.":::
3.  Nella pagina di benvenuto selezionare **Avanti** per eseguire il pacchetto e applicare l'impostazione UEFI appena configurata.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Una pagina iniziale, selezionare Avanti.":::
4.  Riavviare il dispositivo. 

La riattivazione dell'alimentazione è ora configurata. Per verificare le impostazioni, disattivare il dispositivo, scollegare l'alimentazione e quindi riconnettere l'alimentazione. Il dispositivo dovrebbe iniziare automaticamente. 

## Riferimenti

Per altre informazioni, vedere gli articoli seguenti. 

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)
- [Riattivare la LAN per i dispositivi Surface](wake-on-lan-for-surface-devices.md)

Hai ancora bisogno di assistenza? Accedere alla [community Microsoft](https://answers.microsoft.com/).
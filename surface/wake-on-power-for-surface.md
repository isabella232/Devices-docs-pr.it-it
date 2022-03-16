---
title: Riattivazione alimentazione per i dispositivi Surface
ms.author: greglin
author: mccoybot
audience: ITPro
search.appverid:
- SPO160
- MET150
ms.custom:
- CI 121602
ms.reviewer: hachidan
description: Descrive come abilitare e disabilitare Wake on Power per i dispositivi Surface.
keywords: aggiornare, distribuire, driver, wol, wake-on-lan
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
ms.localizationpriority: medium
ms.topic: article
manager: laurawi
ms.audience: itpro
ms.date: 12/08/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 44508875254d2e3d004afef710b43ada2911de08
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448659"
---
# <a name="wake-on-power-for-surface-devices"></a>Riattivazione alimentazione per i dispositivi Surface

I dispositivi Surface possono essere spenti mentre sei lontano dalla scrivania o impostato sulla modalità ibernazione per risparmiare tempo a batteria. Per migliorare la gestibilità di questi dispositivi, Wake on Power consente ai dispositivi Surface compatibili di avviarsi automaticamente quando vengono riconnessi all'alimentazione. Per configurare Wake on Power, puoi usare surface Enterprise Management Mode (SEMM) tramite Surface UEFI Configurator o UEFI Manager.

La funzionalità Riattivazione è disponibile nei dispositivi seguenti:

- Surface Pro 8 (solo SKU commerciali)
- Surface Pro 7+ (solo SKU commerciali)
- Surface Pro X (tutti gli SKU)
- Surface Pro 7 (tutti gli SKU)
- Surface Go 3 (solo SKU commerciali)
- Surface Laptop Studio (solo SKU commerciali)
- Surface Book 3 (tutti gli SKU)
- Surface Laptop 4 (solo SKU commerciali)
- Surface Laptop 3 (tutti gli SKU)
- Surface Laptop Go (tutti gli SKU)


>[!TIP]
> Le SKU commerciali (Surface per le aziende) vengono eseguite Windows 10 Pro/Enterprise o Windows 11 Pro/Enterprise; le SKU consumer vengono eseguite Windows 10/Windows 11 Home. Per altre informazioni, vedi [Visualizzare le informazioni di sistema](https://support.microsoft.com/windows/view-your-system-info-a965a8f2-0773-1d65-472a-1e747c9ebe00). 

## <a name="overview-and-prerequisites"></a>Panoramica e prerequisiti

Surface UEFI Configurator consente di salvare singole impostazioni UEFI in un pacchetto Windows Installer .msi per la distribuzione nei dispositivi di destinazione. 

> [!NOTE]
> Questo articolo presuppone che tu sappia come usare SEMM. Per altre informazioni, vedi la [documentazione relativa alla modalità di gestione di Surface Enterprise (SEMM](surface-enterprise-management-mode.md)).

## <a name="to-enable-wake-on-power"></a>Per abilitare l'attivazione dell'alimentazione

1.  Scarica la versione più recente di [Surface UEFI Configurator](https://www.microsoft.com/download/confirmation.aspx?id=46703).
2.  Accedi al dispositivo Surface come amministratore, apri **Configuratore UEFI di Surface**, seleziona **Dispositivi Surface** e quindi seleziona **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-1.png" alt-text="Seleziona Dispositivi Surface e seleziona Avanti.":::
3.  Seleziona **Start**, quindi seleziona **Crea in** **Pacchetto di configurazione**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-2.png" alt-text="Seleziona Crea pacchetto di configurazione.":::
4.  Selezionare **Protezione certificato** e aggiungere il file PFX del certificato. 
5. Immettere la password, selezionare **Avanti**, aggiungere **Password di** protezione, se appropriato, quindi selezionare **Avanti**.
6.  Nella pagina **Scegli il tipo di Surface** di destinazione seleziona i dispositivi di destinazione in base alle esigenze. Ad esempio, selezionare **Surface Pro 7**.
7.  Nella pagina **Funzionalità avanzate** selezionare **Riattiva l'alimentazione**, impostare la funzionalità su **Attivata** e quindi selezionare **Avanti**.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-3.png" alt-text="Seleziona Wake on Power e imposta su On."::: 
8.  Nella pagina **Operazione completata** selezionare **Fine**.

    > [!NOTE]
    > Se è la prima volta che fornisci impostazioni al dispositivo, ti verrà richiesto di fornire anche gli ultimi due caratteri dell'identificazione personale del certificato. 
9.  Salvare il .msi pacchetto. 

## <a name="apply-the-msi-package"></a>Applicare il pacchetto MSI 

Puoi applicare il pacchetto MSI ai dispositivi della rete usando strumenti di distribuzione software come Microsoft Endpoint Configuration Manager. Questa procedura include i passaggi per installare il pacchetto nel computer locale. 

1.  Al prompt dei comandi con privilegi elevati immettere il percorso completo del file .msi per eseguire il pacchetto .msi file. 

    ```
    C:\SEMM\wake-on-power.msi 
    ```

2.  Nella finestra **di dialogo** Avviso selezionare **OK** o disabilitare BitLocker, in base alle esigenze.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-4.png" alt-text="Selezionare OK o disabilitare BitLocker in base alle esigenze.":::
3.  Nella pagina iniziale seleziona **Avanti** per eseguire il pacchetto e applicare l'impostazione UEFI appena configurata.

    :::image type="content" source="images/wake-on-power-for-surface/wake-on-power-for-surface-5.png" alt-text="Nella pagina iniziale selezionare Avanti.":::
4.  Riavviare il dispositivo. 

La riattivazione dell'alimentazione è ora configurata. Per testare le impostazioni, spegnere il dispositivo, scollegare l'alimentazione e quindi riconnettere l'alimentazione. Il dispositivo deve essere avviato automaticamente. 

## <a name="references"></a>Riferimenti

Per ulteriori informazioni, vedere gli articoli seguenti. 

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)
- [Wake on LAN per dispositivi Surface](wake-on-lan-for-surface-devices.md)

Hai ancora bisogno di assistenza? Passare a [Microsoft Community](https://answers.microsoft.com/).
---
title: Microsoft Surface Deployment Accelerator (Surface)
description: Microsoft Surface Deployment Accelerator è un meccanismo di distribuzione semplice e rapido che permette di ricreare l'immagine dei dispositivi Surface.
ms.assetid: E7991E90-4AAE-44B6-8822-58BFDE3EADE4
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
keywords: distribuire, installare, strumento
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.date: 5/08/2020
ms.openlocfilehash: 0e136bd0a69db7a4c4e5cea7d2c065727dcc8fcc
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016440"
---
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.

Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.

Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione. Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.

L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.

## Requisiti

1. Un'unità thumb USB di dimensioni almeno 16 GB. L'unità USB verrà formattata.
2. Un file con estensione ISO con Windows 10 Pro o Windows 10 Enterprise. Lo strumento per la creazione di elementi multimediali può essere usato per scaricare Windows 10 e creare un file ISO. Per altre informazioni, vedere [scaricare Windows 10](https://www.microsoft.com/software-download/windows10).

## Come eseguire SDA

**Per eseguire SDA:**

1. Accedere a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) su GitHub. 
2. Esaminare la documentazione del [file Leggimi](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md) .
3. Nella pagina [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) fare clic sul pulsante **codice** e quindi selezionare **Scarica zip** per salvare i file localmente nel computer.
4. Fare clic con il pulsante destro del mouse sul file con estensione zip e quindi scegliere **Proprietà**.
5. Nella scheda **generale** selezionare la casella di controllo **Sblocca** e quindi fare clic su **OK**.
6. Estrarre il file con estensione zip in una posizione nel disco rigido (es: C:\SDA).
7. Aprire un prompt di Windows PowerShell con privilegi elevati e impostare ExecutionPolicy per la sessione corrente su senza restrizioni.

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. Eseguire lo script SDA specificando i parametri per l'ambiente. Ad esempio, il comando seguente creerà un'unità USB avviabile che può essere usata per installare Windows 10 su un hub Surface 2:

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/sda1.png)

    Lo script richiederà circa 45 minuti per l'esecuzione, ma potrebbe richiedere più tempo a seconda delle risorse disponibili per la CPU e il disco. 

    Dopo aver creato un'immagine Windows, lo script ti chiederà di confermare la lettera dell'unità USB. L'unità USB verrà quindi formattata, configurata come avviabile e file copiati per consentire l'installazione dell'immagine personalizzata di Windows 10 per i dispositivi Surface.

9. Inserire l'unità USB nel dispositivo in cui si vuole installare Windows 10 e riavviare per iniziare l'installazione di Windows 10. L'avvio USB deve essere abilitato nel BIOS, che può richiedere di disabilitare temporaneamente l'avvio sicuro.

> [!IMPORTANT]
> L'avvio dall'unità USB inizierà immediatamente l'installazione di Windows 10. Assicurarsi che il dispositivo sia pronto prima di inserire l'USB e riavviare. 

## Collegamenti correlati

 - [Strumento di distribuzione delle immagini open source rilasciato su GitHub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [Scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

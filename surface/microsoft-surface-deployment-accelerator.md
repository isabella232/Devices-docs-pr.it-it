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
ms.openlocfilehash: 3ede7311289dc4bc720735c0142ff3a46fbb69e7
ms.sourcegitcommit: 582c5a79881c58c4f1aa66cfcab46db966ca9f24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016557"
---
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.

Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.

Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione. Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.

L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.

## Requisiti

1. Un'unità thumb USB di dimensioni almeno 16 GB. L'unità USB verrà formattata.
2. Un file con estensione ISO con Windows 10 Pro o Windows 10 Enterprise. Lo strumento per la creazione di elementi multimediali può essere usato per scaricare Windows 10 e creare un file ISO. Per altre informazioni, vedere [scaricare Windows 10](https://www.microsoft.com/software-download/windows10).
3. Dispositivo che utilizza Windows 10, versione 2004 o successiva con accesso a Internet.

Vedere la sezione [prerequisiti](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) del documento README per un elenco dettagliato dei requisiti.

## Come eseguire l'SDA

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
8. Eseguire lo script SDA specificando i parametri per l'ambiente. Lo script può essere usato per creare immagini per l'installazione di Windows 10 su un'ampia gamma di dispositivi Surface. Per un elenco completo dei dispositivi supportati, vedere la [Descrizione del parametro di dispositivo](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) nell'articolo Leggimi di SDA. 

    Ad esempio, il comando seguente crea un'unità USB avviabile che può essere usata per [installare Windows 10 in Surface Hub 2](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os):

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```
    L'output degli script di esempio è inferiore.

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/sda1.png)

    Lo script richiederà circa 45 minuti per l'esecuzione, ma potrebbe richiedere più tempo a seconda delle risorse disponibili per la CPU e il disco. 

    Dopo aver creato un'immagine di Windows, lo script ti chiederà di inserire e confermare la lettera dell'unità USB. L'unità USB verrà quindi formattata, configurata come avviabile e file copiati per consentire l'installazione dell'immagine personalizzata di Windows 10 per i dispositivi Surface.

9. Inserire l'unità USB nel dispositivo in cui si vuole installare Windows 10 e riavviare per iniziare l'installazione di Windows 10. L'avvio USB deve essere abilitato nel BIOS, che può richiedere di disabilitare temporaneamente l'avvio sicuro.

> [!IMPORTANT]
> L'avvio dall'unità USB inizierà immediatamente l'installazione di Windows 10. Assicurarsi che il dispositivo sia pronto prima di inserire l'USB e riavviare. 

## Collegamenti correlati

 - [Strumento di distribuzione delle immagini open source rilasciato su GitHub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)
 - [Scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

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
ms.openlocfilehash: 48f89e8929bdb9d075bea988558fea234da5bbd2
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911421"
---
# <a name="microsoft-surface-deployment-accelerator"></a>Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata da Microsoft usando strumenti di distribuzione Microsoft gratuiti.

Riprogettato ad aprile 2020 per semplificare e automatizzare la distribuzione di immagini Surface in un ambiente aziendale, lo strumento SDA consente di creare un'immagine Windows "di tipo factory" che è possibile personalizzare in base ai requisiti dell'organizzazione.

Lo strumento SDA basato su script open source sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di testing o di produzione. Se l'adk più recente non è già installato, verrà scaricato e installato durante l'esecuzione dello strumento SDA.

L'immagine risultante corrisponde strettamente alla configurazione delle immagini bare metal recovery (BMR), senza applicazioni preinstallati come Microsoft Office o l'applicazione UWP surface.

## <a name="requirements"></a>Requisiti

1. Unità usb con dimensioni di almeno 16 GB. L'unità USB verrà formattata.
2. Un file iso con Windows 10 Pro o Windows 10 Enterprise. Lo strumento di creazione dei supporti può essere usato per scaricare Windows 10 e creare un file iso. Per ulteriori informazioni, vedere [Download Windows 10](https://www.microsoft.com/software-download/windows10).
3. Dispositivo che esegue Windows 10 versione 2004 o successiva con accesso a Internet.

Per un [elenco dettagliato dei](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#prerequisites) requisiti, vedere la sezione Prerequisiti del documento README.

## <a name="how-to-run-the-sda"></a>Come eseguire L'SDA

**Per eseguire SDA:**

1. Vai a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) in GitHub. 
2. Consultare la [documentazione README.](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md)
3. Nella pagina [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) fai clic sul pulsante **Codice** e quindi seleziona **Scarica ZIP** per salvare i file in locale nel computer.
4. Fare clic con il pulsante destro del .zip file e quindi scegliere **Proprietà**.
5. Nella scheda **Generale** selezionare la casella di controllo **Sblocca** e quindi fare clic su **OK.**
6. Estrarre il .zip file in un percorso sul disco rigido (ad esempio: C:\SDA).
7. Apri un prompt dei Windows PowerShell con privilegi elevati e imposta ExecutionPolicy per la sessione corrente su Unrestricted.

    ```powershell
    Set-ExecutionPolicy -Scope Process -ExecutionPolicy Unrestricted -Force
    ```
8. Eseguire lo script SDA specificando i parametri per l'ambiente. Lo script può essere usato per creare immagini da installare Windows 10 su un'ampia gamma di dispositivi Surface. Per un elenco completo dei dispositivi supportati, vedi la descrizione del parametro [Device](https://github.com/microsoft/SurfaceDeploymentAccelerator/blob/master/README.md#full-parameter-documentation) nell'articolo SDA README. 

    Ad esempio, il comando seguente creerà un'unità USB di avvio che può essere usata per installare Windows 10 [in Surface Hub 2](https://docs.microsoft.com/surface-hub/surface-hub-2s-migrate-os):

    ```powershell
    .\CreateSurfaceWindowsImage.ps1 -ISO C:\SDA\enterprise_client.iso -OSSKU Enterprise -DestinationFolder C:\Output -Device SurfaceHub2 -CreateUSB $True
    ```
    Di seguito è riportato l'output di script di esempio.

   ![Esecuzione dello strumento Surface Deployment Accelerator.](images/sda1.png)

    L'esecuzione dello script richiederà circa 45 minuti, ma potrebbe richiedere più tempo a seconda delle risorse di CPU e disco disponibili. 

    Dopo aver creato Windows immagine, lo script chiederà di inserire e confermare la lettera di unità dell'unità USB. L'unità USB verrà quindi formattata, configurata come avviabile e i file copiati per abilitare l'installazione dell'immagine Windows 10 personalizzata per i dispositivi Surface.

9. Inserisci l'unità USB nel dispositivo in cui vuoi installare Windows 10 e riavvia per iniziare l'installazione Windows 10. L'avvio USB deve essere abilitato nel BIOS, che può richiedere la disabilitazione temporanea dell'avvio protetto.

> [!IMPORTANT]
> L'avvio dall'unità USB inizierà immediatamente l'installazione Windows 10. Assicurati che il dispositivo sia pronto prima di inserire l'USB e riavviarlo. 

## <a name="related-links"></a>Collegamenti correlati

 - [Strumento di distribuzione di immagini open source rilasciato in GitHub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)
 - [Scaricare e installare il Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

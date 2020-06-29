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
ms.openlocfilehash: 32d8fded8c325766f7ab6bbc750ba7fe13e01d70
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832312"
---
# Microsoft Surface Deployment Accelerator

Microsoft Surface Deployment Accelerator (SDA) automatizza la creazione e la configurazione di un'esperienza di distribuzione consigliata Microsoft usando gli strumenti di distribuzione Microsoft gratuiti.

Riprogettato in aprile 2020 per semplificare e automatizzare la distribuzione di immagini di superficie in un ambiente aziendale, lo strumento SDA consente di creare un'immagine di Windows "simile a una fabbrica" che è possibile personalizzare in base alle proprie esigenze organizzative.

Lo strumento SDA open source basato su script sfrutta Windows Assessment and Deployment Kit (ADK) per Windows 10, facilitando la creazione di immagini Windows (WIM) in ambienti di test o di produzione. Se l'ultima versione di ADK non è già installata, verrà scaricata e installata durante l'uso dello strumento SDA.

L'immagine risultante corrisponde strettamente alla configurazione delle immagini BMR (Bare Metal Recovery), senza applicazioni preinstallate come Microsoft Office o l'applicazione Surface UWP.

**Per eseguire SDA:**

1. Accedere a [SurfaceDeploymentAccelerator](https://github.com/microsoft/SurfaceDeploymentAccelerator) su GitHub. 
2. Selezionare **clona o Scarica** e rivedere il file Readme.
3. Modificare lo script con le variabili appropriate per l'ambiente, come documentato nel file Leggimi, e rivederlo prima di eseguirlo nell'ambiente di test. 

   ![Strumento di accelerazione della distribuzione della superficie in uso](images/surface-deployment-accelerator.png)

## Collegamenti correlati

 - [Strumento di distribuzione delle immagini open source rilasciato su GitHub](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/open-source-image-deployment-tool-released-on-github/ba-p/1314115)

 - [Scaricare e installare Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install)

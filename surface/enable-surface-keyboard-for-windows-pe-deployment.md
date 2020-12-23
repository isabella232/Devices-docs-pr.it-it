---
title: Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT
description: Quando si usa MDT per distribuire Windows 10 in computer portatili di Surface, è necessario importare i driver della tastiera da usare nell'ambiente Windows PE.
keywords: superficie di Windows 10, automatizza, Personalizza, MDT
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: Teresa-Motiv
ms.author: v-tea
ms.topic: article
ms.reviewer: scottmca
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
ms.openlocfilehash: d7ae6fc434f77cad86e73f111243968493de4ff2
ms.sourcegitcommit: e6224f81f8efb6ac862afec0e60e3ddb182e9e6f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "11247308"
---
# Come abilitare la tastiera del computer portatile Surface durante la distribuzione di MDT

Questo articolo risolve un approccio di distribuzione che usa Microsoft Deployment Toolkit (MDT). Puoi anche applicare queste informazioni ad altre metodologie di distribuzione. Nella maggior parte dei tipi di dispositivi Surface la tastiera dovrebbe funzionare durante l'installazione di Lite Touch (LTI). Tuttavia, Surface laptop richiede alcuni driver aggiuntivi per abilitare la tastiera. Per i dispositivi portatili Surface (1st Gen) e Surface laptop 2, è necessario preparare la struttura delle cartelle e i profili di selezione che consentono di specificare i driver della tastiera da usare durante la fase di preinstallazione di Windows (Windows PE) di LTI. Per altre informazioni sulla struttura delle cartelle, vedere [distribuire un'immagine di Windows 10 con MDT: passaggio 5: preparare il repository dei driver](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).


> [!IMPORTANT]
> Se si sta distribuendo un'immagine di Windows 10 a un computer portatile Surface con Windows 10 in modalità S preinstallato, vedere KB [4032347, problemi durante la distribuzione di dispositivi Windows in Surface con Windows 10 preinstallato in modalità s](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).

Per aggiungere i driver della tastiera al profilo di selezione, eseguire le operazioni seguenti:

1. Scaricare il file MSI di Surface laptop più recente dalle posizioni appropriate:
    - [Driver e firmware di Surface laptop (1a Gen)](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Computer portatile di Surface 2 driver e firmware](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Surface laptop 3 con driver e firmware per processori Intel](https://www.microsoft.com/download/details.aspx?id=100429)

2. Estrarre il contenuto del file MSI della superficie portatile in una cartella che è possibile individuare facilmente, ad esempio c:\ surface_laptop_drivers). Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Aprire Deployment Workbench ed espandere il nodo **condivisioni distribuzione** e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64** .

   ![Immagine che mostra la posizione della cartella WindowsPEX64 in Deployment Workbench](./images/surface-laptop-keyboard-1.png)

4. Fare clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegliere **Importa driver**.
5. Seguire le istruzioni della procedura guidata Importa driver per importare le cartelle del driver nella cartella WindowsPEX64.  

> [!NOTE]
>  Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.  La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI. 

Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\SurfaceHidMiniDriver
- SurfaceUpdate\SurfaceSerialHubDriver
- SurfaceUpdate\Itouch

Per supportare Surface laptop 2, importare le cartelle seguenti:

 - SurfacePlatformInstaller\Drivers\System\GPIO
 - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
 - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
 - SurfacePlatformInstaller\Drivers\System\I2C
 - SurfacePlatformInstaller\Drivers\System\SPI
 - SurfacePlatformInstaller\Drivers\System\UART
 - SurfacePlatformInstaller\Drivers\System\PreciseTouch

O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:

- SurfaceUpdate\SerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\Itouch

 
Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:

- SurfaceUpdate\IclSerialIOGPIO
- SurfaceUpdate\IclSerialIOI2C
- SurfaceUpdate\IclSerialIOSPI
- SurfaceUpdate\IclSerialIOUART
- SurfaceUpdate\SurfaceHidMini
- SurfaceUpdate\SurfaceSerialHub
- SurfaceUpdate\SurfaceHotPlug
- SurfaceUpdate\Itouch

L'importazione delle cartelle seguenti consentirà la funzionalità completa di tastiera, trackpad e tocco in PE per Surface laptop 3.

- IclSerialIOGPIO
- IclSerialIOI2C
- IclSerialIOSPI
- IclSerialIOUART
- iTouch
- IclChipset
- IclChipsetLPSS
- IclChipsetNorthpeak
- ManagementEngine
- SurfaceAcpiNotify
- SurfaceBattery
- SurfaceDockIntegration
- SurfaceHidMini
- SurfaceHotPlug
- SurfaceIntegration
- SurfaceSerialHub
- SurfaceService
- SurfaceStorageFwUpdate


    > [!NOTE]
    >  Controllare il pacchetto MSI scaricato per determinare il formato e la struttura della directory.  La struttura della directory inizierà con SurfacePlatformInstaller (file MSI meno recenti) o SurfaceUpdate (file MSI più nuovi) a seconda di quando è stato rilasciato l'MSI. 

    Per supportare laptop Surface (1a generazione), importare le cartelle seguenti:

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\SurfaceHidMiniDriver
    - SurfaceUpdate\SurfaceSerialHubDriver
    - SurfaceUpdate\Itouch

    Per supportare Surface laptop 2, importare le cartelle seguenti:

     - SurfacePlatformInstaller\Drivers\System\GPIO
     - SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver
     - SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver
     - SurfacePlatformInstaller\Drivers\System\I2C
     - SurfacePlatformInstaller\Drivers\System\SPI
     - SurfacePlatformInstaller\Drivers\System\UART
     - SurfacePlatformInstaller\Drivers\System\PreciseTouch

    O per i file MSI più recenti che iniziano con "SurfaceUpdate", USA:

    - SurfaceUpdate\SerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\Itouch

    Per supportare Surface laptop 3 con processore Intel, importare le cartelle seguenti:

    - SurfaceUpdate\IclSerialIOGPIO
    - SurfaceUpdate\IclSerialIOI2C
    - SurfaceUpdate\IclSerialIOSPI
    - SurfaceUpdate\IclSerialIOUART
    - SurfaceUpdate\SurfaceHidMini
    - SurfaceUpdate\SurfaceSerialHub
    - SurfaceUpdate\SurfaceHotPlug
    - SurfaceUpdate\Itouch

    > [!NOTE]
    > Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3. I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.

6. Verificare che la cartella WindowsPEX64 ora contenga i driver importati. La cartella dovrebbe essere simile alla seguente:  

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench](./images/surface-laptop-keyboard-2.png)

7. Configurare un profilo di selezione che usa la cartella WindowsPEX64. Il profilo di selezione deve essere simile al seguente:  

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione](./images/surface-laptop-keyboard-3.png)

8. Configurare le proprietà di Windows PE della condivisione di distribuzione MDT per usare il nuovo profilo di selezione, come indicato di seguito:  

   - Per la **piattaforma**, selezionare **x64**.
   - Per il **profilo di selezione**, selezionare il nuovo profilo.
   - Selezionare **Includi tutti i driver dal profilo di selezione**.
   
   ![Immagine che mostra le proprietà di Windows PE della condivisione di distribuzione MDT](./images/surface-laptop-keyboard-4.png)

9. Verificare di aver configurato i driver per i portatili della superficie rimanente usando un profilo di selezione o una variabile **DriverGroup001** .  
   - Per laptop Surface (1a generazione), il modello è **laptop Surface**. I driver portatili di Surface rimanenti dovrebbero risiedere nella cartella di \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface come illustrato nella figura che segue questo elenco.
   - Per Surface laptop 2, il modello è **Surface laptop 2**. I driver portatili Surface rimanenti dovrebbero risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 2. 
   - Per Surface laptop 3 con processore Intel, il modello è Surface laptop 3. I driver per portatili Surface rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface laptop 3.

   ![Immagine che mostra i driver normali per laptop Surface (1a Gen) nella cartella Surface Laptop di Deployment Workbench](./images/surface-laptop-keyboard-5.png)

Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto in [distribuire un'immagine di Windows 10 con MDT: passaggio 6: creare la sequenza di attività di distribuzione](https://docs.microsoft.com/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).

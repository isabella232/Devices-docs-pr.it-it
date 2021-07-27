---
title: Come abilitare la tastiera Surface Laptop durante la distribuzione di MDT
description: Quando usi MDT per distribuire Windows 10 ai portatili Surface, devi importare i driver di tastiera da usare nell'ambiente Windows PE.
keywords: windows 10 surface, automatizza, personalizza, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: coveminer
ms.author: v-tea
ms.topic: article
ms.reviewer: carlol
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
ms.date: 06/21/2021
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
- Surface Laptop 4
ms.openlocfilehash: 1ee3376a24d3e83cc66c8a220a1f7afa195840d0
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676720"
---
# <a name="how-to-enable-the-surface-laptop-keyboard-during-mdt-deployment"></a>Come abilitare la tastiera Surface Laptop durante la distribuzione di MDT

Questo articolo tratta un approccio di distribuzione che usa Microsoft Deployment Toolkit (MDT). È inoltre possibile applicare queste informazioni ad altre metodologie di distribuzione. Nella maggior parte dei tipi di dispositivi Surface, la tastiera dovrebbe funzionare durante l'installazione Lite Touch (LTI). Tuttavia, Surface Laptop alcuni driver aggiuntivi per abilitare la tastiera. Per i dispositivi Surface Laptop (1° generazione) e Surface Laptop 2, è necessario preparare la struttura delle cartelle e i profili di selezione che consentono di specificare i driver della tastiera da utilizzare durante la fase Windows Preinstallation Environment (Windows PE) di LTI. Per ulteriori informazioni su questa struttura di cartelle, [vedere Deploy a Windows 10 image using MDT: Step 5: Prepare the drivers repository.](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository)

> [!TIP]
> Quando si usano driver di tastiera per Surface Laptop 2 e Surface Laptop 3 nella stessa istanza di avvio pe di Windows, potrebbe essere necessario reimpostare manualmente il firmware se la tastiera o il touchpad non funzionano in Windows PE:
>
> - Tieni premuto il pulsante Di alimentazione per 30 secondi. Se si è connessi a un'unità di alimentazione (PSU), tenere premuto il pulsante Di alimentazione fino a quando la luce alla fine del cavo PSU si spegne brevemente prima di riattivarla.

> [!IMPORTANT]
> Se stai distribuendo un'immagine Windows 10 a un Surface Laptop con Windows 10 preinstallato in modalità S, vedi KB 4032347, Problemi durante la distribuzione di Windows nei dispositivi Surface con [Windows 10 preinstallato in modalità S.](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues)

## <a name="add-keyboard-drivers-to-the-selection-profile"></a>Aggiungere driver di tastiera al profilo di selezione

1. Scaricare il file Surface Laptop .msi file più recente dai percorsi appropriati:
    - [Surface Laptop driver e firmware (prima generazione)](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface Laptop 2 driver e firmware](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Surface Laptop 3 con driver e firmware del processore Intel](https://www.microsoft.com/download/details.aspx?id=100429)
    - [Surface Laptop 4 con driver e firmware del processore Intel](https://www.microsoft.com/download/102924)
    - [Surface Laptop 4 con driver e firmware del processore AMD](https://www.microsoft.com/download/102923)
2. Estrarre il contenuto del file Surface Laptop .msi in una cartella facilmente individuabile, ad esempio c:\surface_laptop_drivers. Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Aprire Deployment Workbench ed espandere il **nodo Deployment Shares** e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64.**
4. Fai clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegli **Importa driver.**
5. Seguire le istruzioni dell'Importazione guidata driver per importare le cartelle dei driver nella cartella WindowsPEX64.

 > [!NOTE]
 > Controlla il pacchetto .msi download per determinare il formato e la struttura della directory.  La struttura della directory inizierà con SurfacePlatformInstaller (file di .msi meno recenti) o SurfaceUpdate (file .msi più recenti) a seconda del momento in cui è stato rilasciato il file .msi.

## <a name="import-drivers-for-surface-devices"></a>Importare driver per dispositivi Surface

Importare le cartelle seguenti in base alle esigenze del Surface Laptop dispositivo.  

| Dispositivo                                | Importare cartelle                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Altre informazioni                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Surface Laptop 4 con processore Intel | TglSerial<br>IntelPreciseTouch<br>SurfaceEthernetAdapter<br>SurfaceBattery<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceSerialHub<br>SurfaceTconDriver<br>surfacetimealarmacpifilter<br>surfacevirtualfunctionenum<br>TglChipset<br>ManagementEngine                                                                                                                                                                                                                                                                                                                          |n/d                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 4 con processore AMD   | U0361415<br>AMDfendr<br>AMDGpio2<br>AMDI2c<br>AMDLpcFilterDriverAMDMicroPEP<br>AMDPsp<br>AMDSmf<br>AMDSpi<br>AMDUart<br>SurfaceEthernetAdapter<br>SMBUS<br>SurfaceBattery<br>SurfaceButton<br>SurfaceDigitizerHidSpiExtnPackage<br>SurfaceHIDFriendlyNames<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceOemPanel<br>SurfacePowerMeter<br>SurfacePowerTrackerCore<br>SurfaceSerialHub<br>SurfaceSMFClient<br>SurfaceSmfDisplayClient<br>SurfaceSystemManagementFramework<br>SurfaceTconDriver<br>SurfaceThermalPolicy<br>Surfacetimealarmacpifilter<br>SurfaceUcmUcsiHidClient |n/d                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Surface Laptop 3 con processore Intel | SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SerialIOI2C<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\SurfaceHotPlug<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                                                                                                   | L'importazione delle cartelle seguenti consentirà la funzionalità completa di tastiera, trackpad e tocco in PE:<br><br>SerialIOGPIO<br>SerialIOI2C<br>SerialIOSPI<br>SerialIOUART<br>itouch<br>Chipset<br>ChipsetLPSS<br>ChipsetNorthpeak<br>ManagementEngine<br>SurfaceAcpiNotify<br>SurfaceBattery<br>SurfaceDockIntegration<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceIntegration<br>SurfaceSerialHub<br>SurfaceService<br>SurfaceStorageFwUpdat |
| Surface Laptop 2                      | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\I2C<br>SurfacePlatformInstaller\Drivers\System\SPI<br>SurfacePlatformInstaller\Drivers\System\UART<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                           | Per i file .msi più nuovi che iniziano con "SurfaceUpdate", usa:<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\serialioi2c<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\Itouch                                                                                                                                                                    |
| Surface Laptop (prima generazione)              | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                                                                                                                                                                         | Per i file .msi più nuovi che iniziano con "SurfaceUpdate", usa:<br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SurfaceHidMiniDriver<br>SurfaceUpdate\SurfaceSerialHubDriver<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                |

  > [!TIP]
  > Controlla il pacchetto .msi download per determinare il formato e la struttura della directory.  La struttura della directory inizierà con SurfacePlatformInstaller (file di .msi meno recenti) o SurfaceUpdate (file di .msi più recenti) a seconda di quando è stato rilasciato il .msi.

## <a name="verify-imported-drivers--configure-windows-pe-properties"></a>Verificare che i driver importati & configurare Windows pe

1. Verificare che la cartella WindowsPEX64 contenga ora i driver importati, come illustrato nella figura seguente:

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench](./images/surface-laptop-keyboard-2.png)
1. Configurare un profilo di selezione che utilizza la cartella WindowsPEX64, come illustrato nella figura seguente:

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione](./images/surface-laptop-keyboard-3.png)
1. Configurare le Windows pe della condivisione di distribuzione MDT per l'utilizzo del nuovo profilo di selezione, come indicato di seguito:
    - Per **Piattaforma,** selezionare **x64.**
    - In **Profilo di selezione**selezionare il nuovo profilo.
    - Selezionare **Includi tutti i driver dal profilo di selezione.**

    ![Immagine che mostra le Windows PE della condivisione di distribuzione MDT](./images/surface-laptop-keyboard-4.png)
4. Verificare di aver configurato i driver di Surface Laptop driver rimanenti utilizzando un profilo di selezione o una **variabile DriverGroup001.**
    - Per Surface Laptop (prima generazione), il modello è **Surface Laptop**. I driver di Surface Laptop rimanenti devono trovarsi nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop, come illustrato nella figura seguente.
    - Per Surface Laptop 2, il modello è **Surface Laptop 2**. I driver Surface Laptop devono trovarsi nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2.
    - Per Surface Laptop 3 con processore Intel, il modello è Surface Laptop 3. I driver Surface Laptop aggiuntivi si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3.

    ![Immagine che mostra i normali Surface Laptop (prima generazione) nella cartella Surface Laptop di Deployment Workbench](./images/surface-laptop-keyboard-5.png)

Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto [in Deploy a Windows 10 image using MDT: Step 6: Create the deployment task sequence](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).

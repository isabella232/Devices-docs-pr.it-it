---
title: Come abilitare la tastiera Surface Laptop durante la distribuzione MDT
description: Quando si usa MDT per distribuire Windows 10 nei portatili Surface, è necessario importare i driver della tastiera da usare nell'ambiente PE Windows.
keywords: windows 10 surface, automatizzare, personalizzare, mdt
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: carlol
ms.localizationpriority: medium
ms.audience: itpro
manager: jarrettr
ms.date: 01/05/2022
appliesto:
- Surface Laptop (1st Gen)
- Surface Laptop 2
- Surface Laptop 3
- Surface Laptop 4
- Surface Laptop Studio
- Surface Pro 8
- Windows 10
- Windows 11
ms.openlocfilehash: d207d0843e23f68713597c12a529ab5574fa695e
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497919"
---
# <a name="how-to-enable-the-surface-laptop-keyboard-during-mdt-deployment"></a>Come abilitare la tastiera Surface Laptop durante la distribuzione MDT

Questo articolo illustra un approccio alla distribuzione che usa Microsoft Deployment Toolkit (MDT). È anche possibile applicare queste informazioni ad altre metodologie di distribuzione. Nella maggior parte dei tipi di dispositivi Surface, la tastiera dovrebbe funzionare durante l'installazione Lite Touch (LTI). Tuttavia, Surface Laptop richiede alcuni driver aggiuntivi per abilitare la tastiera. Per Surface Laptop (prima generazione) e Surface Laptop 2 dispositivi, è necessario preparare la struttura di cartelle e i profili di selezione che consentono di specificare i driver della tastiera da usare durante la fase Windows Ambiente di preinstallazione (Windows PE) dell'LTI. Per altre informazioni su questa struttura di cartelle, vedere [Distribuire un'immagine Windows 10 usando MDT: Passaggio 5: Preparare il repository dei driver](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt?redirectedfrom=MSDN#step-5-prepare-the-drivers-repository).

> [!TIP]
> Quando si usano i driver della tastiera per Surface Laptop 2 e Surface Laptop 3 nella stessa istanza di avvio pe Windows, potrebbe essere necessario reimpostare manualmente il firmware se la tastiera o il touchpad non funzionano in Windows PE:
>
> - Tenere premuto il pulsante di alimentazione per 30 secondi. Se si è connessi a un'unità di alimentazione (PSU), premere e tenere premuto il pulsante di alimentazione fino a quando la luce alla fine del cavo PSU si spegne brevemente prima di riattivarsi.

> [!IMPORTANT]
> Se si distribuisce un'immagine Windows 10 in un Surface Laptop con Windows 10 in modalità S preinstallata, vedere [KB 4032347, Problemi durante la distribuzione di Windows nei dispositivi Surface con Windows 10 preinstallati in modalità S](https://support.microsoft.com/help/4032347/surface-preinstall-windows10-s-mode-issues).

## <a name="add-keyboard-drivers-to-the-selection-profile"></a>Aggiungere driver di tastiera al profilo di selezione

1. Scaricare il file Surface Laptop .msi più recente dai percorsi appropriati:
    - [driver e firmware di Surface Laptop (prima generazione)](https://www.microsoft.com/download/details.aspx?id=55489)
    - [Surface Laptop 2 driver e firmware](https://www.microsoft.com/download/details.aspx?id=57515)
    - [Surface Laptop 3 con i driver e il firmware del processore Intel](https://www.microsoft.com/download/details.aspx?id=100429)
    - [Surface Laptop 4 con driver e firmware del processore Intel](https://www.microsoft.com/download/102924)
    - [Surface Laptop 4 con driver e firmware del processore AMD](https://www.microsoft.com/download/102923)
    - [driver e firmware di Surface Laptop Studio](https://www.microsoft.com/download/details.aspx?id=103505)
    - [Surface Pro 8 driver e firmware](https://www.microsoft.com/download/details.aspx?id=103503)

2. Estrarre il contenuto del file Surface Laptop .msi in una cartella facilmente individuabile, ad esempio c:\surface_laptop_drivers. Per estrarre il contenuto, aprire una finestra del prompt dei comandi con privilegi elevati ed eseguire il comando dall'esempio seguente:

   ```cmd
   Msiexec.exe /a SurfaceLaptop_Win10_15063_1703008_1.msi targetdir=c:\surface_laptop_drivers /qn
   ```

3. Aprire Deployment Workbench ed espandere il nodo **Condivisioni di** distribuzione e la condivisione di distribuzione, quindi passare alla cartella **WindowsPEX64** .
4. Fare clic con il pulsante destro del mouse sulla cartella **WindowsPEX64** e scegliere **Importa driver**.
5. Seguire le istruzioni dell'Importazione guidata driver per importare le cartelle driver nella cartella WindowsPEX64.

 > [!NOTE]
 > Controllare il pacchetto .msi scaricato per determinare il formato e la struttura di directory.  La struttura di directory inizierà con SurfacePlatformInstaller (file .msi precedenti) o SurfaceUpdate (file .msi più recenti) a seconda del momento in cui è stato rilasciato il file .msi.

## <a name="import-drivers-for-surface-devices"></a>Importare i driver per i dispositivi Surface

Importare le cartelle seguenti in base alle esigenze per il dispositivo Surface Laptop.

| Dispositivo                                    | Importare cartelle                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Altre informazioni                                                                                                                                                                                                                                                                                                                                                                                                                            |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Surface Laptop Studio**                 | Heci<br>ialpss2_gpio2_tgl<br>ialpss2_uart2_tgl<br>intelthcbase<br>surfacehidminidriver<br>surfacehotplug<br>surfaceintegrationdriver<br>surfacepenwirelesschargerhotkey<br>surfacesarmanager<br>surfaceserialhubdriver<br>surfacestoragefwupdateenum<br>surfacestoragefwupdatekbg40zns256gpackage<br>surfacewakeontouchcontrol                                                                                                                                                                                                                                                 | n/d                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Surface Pro 8**                         | intelthcbase<br>ManagementEngine<br>surfaceacpiplatformextension<br>SurfaceBattery<br>SurfaceCoverClick<br>SurfaceEthernetAdapter<br>SurfaceHidMini<br>SurfaceHotPlug<br>surfaceintegrationdriver<br>SurfaceSar<br>SurfaceSerialHub<br>surfacetimealarmacpifilter<br>surfacetypecoverv7fprude<br>SurfaceUcmUcsiHidClient<br>surfacevirtualfunctionenum<br>tbtslimhostcontroller<br>TglChipset<br>TglSerial                                                                                                                                                                     | n/d                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Surface Laptop 4 con processore Intel** | TglSerial<br>IntelPreciseTouch<br>SurfaceEthernetAdapter<br>SurfaceBattery<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceSerialHub<br>SurfaceTconDriver<br>surfacetimealarmacpifilter<br>surfacevirtualfunctionenum<br>TglChipset<br>ManagementEngine                                                                                                                                                                                                                                                                                                                          | n/d                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Surface Laptop 4 con processore AMD**   | U0361415<br>AMDfendr<br>AMDGpio2<br>AMDI2c<br>AMDLpcFilterDriverAMDMicroPEP<br>AMDPsp<br>AMDSmf<br>AMDSpi<br>AMDUart<br>SurfaceEthernetAdapter<br>SMBUS<br>SurfaceBattery<br>SurfaceButton<br>SurfaceDigitizerHidSpiExtnPackage<br>SurfaceHIDFriendlyNames<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceOemPanel<br>SurfacePowerMeter<br>SurfacePowerTrackerCore<br>SurfaceSerialHub<br>SurfaceSMFClient<br>SurfaceSmfDisplayClient<br>SurfaceSystemManagementFramework<br>SurfaceTconDriver<br>SurfaceThermalPolicy<br>Surfacetimealarmacpifilter<br>SurfaceUcmUcsiHidClient | n/d                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Surface Laptop 3 con processore Intel** | SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SerialIOI2C<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\SurfaceHotPlug<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                                                                                                                   | L'importazione delle cartelle seguenti abiliterà la tastiera completa, il trackpad e la funzionalità di tocco in PE:<br><br>SerialIOGPIO<br>SerialIOI2C<br>SerialIOSPI<br>SerialIOUART<br>Itouch<br>Chipset<br>ChipsetLPSS<br>ChipsetNorthpeak<br>ManagementEngine<br>SurfaceAcpiNotify<br>SurfaceBattery<br>SurfaceDockIntegration<br>SurfaceHidMini<br>SurfaceHotPlug<br>SurfaceIntegration<br>SurfaceSerialHub<br>SurfaceService<br>SurfaceStorageFwUpdat |
| **Surface Laptop 2**                      | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHIDMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\I2C<br>SurfacePlatformInstaller\Drivers\System\SPI<br>SurfacePlatformInstaller\Drivers\System\UART<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                           | Per i file .msi più recenti che iniziano con "SurfaceUpdate", usa:<br><br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\serialioi2c<br>SurfaceUpdate\SerialIOSPI<br>SurfaceUpdate\SerialIOUART<br>SurfaceUpdate\SurfaceHidMini<br>SurfaceUpdate\SurfaceSerialHub<br>SurfaceUpdate\Itouch                                                                                                                                                               |
| **Surface Laptop (prima generazione)**              | SurfacePlatformInstaller\Drivers\System\GPIO<br>SurfacePlatformInstaller\Drivers\System\SurfaceHidMiniDriver<br>SurfacePlatformInstaller\Drivers\System\SurfaceSerialHubDriver<br>SurfacePlatformInstaller\Drivers\System\PreciseTouch                                                                                                                                                                                                                                                                                                                                         | Per i file .msi più recenti che iniziano con **"SurfaceUpdate",** usa:<br><br>SurfaceUpdate\SerialIOGPIO<br>SurfaceUpdate\SurfaceHidMiniDriver<br>SurfaceUpdate\SurfaceSerialHubDriver<br>SurfaceUpdate\Itouch                                                                                                                                                                                                                                       |

  > [!TIP]
  > Controllare il pacchetto .msi scaricato per determinare il formato e la struttura di directory.  La struttura di directory inizierà con SurfacePlatformInstaller (file di .msi precedenti) o SurfaceUpdate (file .msi più recenti) a seconda del momento in cui è stato rilasciato il .msi.

## <a name="verify-imported-drivers--configure-windows-pe-properties"></a>Verificare i driver importati & configurare Windows proprietà PE

1. Verificare che la cartella WindowsPEX64 contenga ora i driver importati, come illustrato nella figura seguente:

   ![Immagine che mostra i driver appena importati nella cartella WindowsPEX64 di Deployment Workbench.](./images/surface-laptop-keyboard-2.png)
1. Configurare un profilo di selezione che usa la cartella WindowsPEX64, come illustrato nella figura seguente:

   ![Immagine che mostra la cartella WindowsPEX64 selezionata come parte di un profilo di selezione.](./images/surface-laptop-keyboard-3.png)
1. Configurare le proprietà PE Windows della condivisione di distribuzione MDT per l'uso del nuovo profilo di selezione, come indicato di seguito:
    - In **Piattaforma** selezionare **x64**.
    - In **Profilo di selezione** selezionare il nuovo profilo.
    - Selezionare **Includi tutti i driver nel profilo di selezione**.

    ![Immagine che mostra le proprietà PE Windows della condivisione di distribuzione MDT.](./images/surface-laptop-keyboard-4.png)
4. Verificare di aver configurato i driver di Surface Laptop rimanenti usando un profilo di selezione o una variabile **DriverGroup001**.
    - Per Surface Laptop (prima generazione), il modello viene **Surface Laptop**. I driver Surface Laptop rimanenti devono risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop, come illustrato nella figura seguente.
    - Per Surface Laptop 2, il modello è **Surface Laptop 2**. I driver Surface Laptop rimanenti devono risiedere nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 2.
    - Per Surface Laptop 3 con processore Intel, il modello è Surface Laptop 3. I driver Surface Laptop rimanenti si trovano nella cartella \MDT Deployment Share\Out-of-Box Drivers\Windows10\X64\Surface Laptop 3.

    ![Immagine che mostra i normali driver Surface Laptop (prima generazione) nella cartella Surface Laptop di Deployment Workbench.](./images/surface-laptop-keyboard-5.png)

Dopo aver configurato la condivisione di distribuzione MDT per usare il nuovo profilo di selezione e le impostazioni correlate, continuare il processo di distribuzione come descritto in [Distribuire un'immagine Windows 10 usando MDT: Passaggio 6: Creare la sequenza di attività di distribuzione](/windows/deployment/deploy-windows-mdt/deploy-a-windows-10-image-using-mdt#step-6-create-the-deployment-task-sequence).

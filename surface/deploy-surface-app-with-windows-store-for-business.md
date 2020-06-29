---
title: Distribuire l'app Surface con Microsoft Store per le aziende o Microsoft Store per l'istruzione (Surface)
description: Scopri come aggiungere e scaricare app Surface con Microsoft Store per le aziende o Microsoft Store per l'istruzione, oltre a installare l'app Surface con PowerShell e MDT.
keywords: app Surface, app, distribuzione, Personalizza
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, store
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: e25e146de49110dca1fea797f9630d9fa2d953e3
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832859"
---
# Distribuire l'app Surface con Microsoft Store per le aziende e l'istruzione

**Ambito di applicazione**

- Surface Pro 7
- Laptop Surface 3
- Surface Pro 6
- Surface Laptop 2
- Surface Go
- Surface go con LTE
- Surface Book 2
- Surface Pro con LTE Advanced (Modello 1807)
- Surface Pro (Modello 1796)
- Surface Laptop
- Surface Studio
- Surface Studio 2
- Surface Book
- Surface Pro 4
- Surface 3 LTE
- Surface 3
- Surface Pro 3


L'app Surface è un'app Microsoft Store leggera che offre il controllo di molte opzioni e impostazioni specifiche della superficie, tra cui: 

* Abilitazione o disabilitazione del pulsante Windows nel dispositivo Surface 

* Regolazione della sensibilità di una penna per Surface 

* Personalizzazione delle azioni dei pulsanti della penna per Surface 

* Abilitazione o disabilitazione dei miglioramenti audio di Surface 

* Accesso rapido per supportare la documentazione e le informazioni per il dispositivo

I clienti che usano Windows Update riceveranno in genere l'app Surface come parte degli aggiornamenti automatici. Tuttavia, se l'organizzazione sta preparando immagini per la distribuzione ai dispositivi Surface, potresti voler includere l'app Surface (in precedenza chiamato Surface Hub) nel processo di imaging e distribuzione invece di richiedere agli utenti di ogni singolo dispositivo di scaricare e installare l'app da Microsoft Store o da Microsoft Store for business. 

> [!NOTE]
> Questo articolo non si applica a Surface Pro X. Per altre informazioni, vedere [distribuzione, gestione e manutenzione di Surface Pro X](surface-pro-arm-app-management.md)

## Panoramica dell'app Surface

L'app Surface è disponibile come download gratuito da [Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P). Gli utenti possono scaricarlo e installarlo da Microsoft Store, ma se l'organizzazione usa Microsoft Store per le aziende, sarà necessario aggiungerla all'inventario dell'archivio e possibilmente includere l'app nell'ambito del processo di distribuzione di Windows. Questi processi vengono discussi in questo articolo. Per altre informazioni su Microsoft Store for business, vedere [Microsoft Store for business](https://docs.microsoft.com/microsoft-store/) in Windows TechCenter. 

## Aggiungere un'app Surface a un account di Microsoft Store per le aziende 

Prima che gli utenti possano installare o distribuire un'app dall'account Microsoft Store for business di una società, l'app desiderata deve prima essere resa disponibile e concessa in licenza agli utenti di un'azienda. 

1. Se non è già stato fatto, creare un [account di Microsoft Store per le aziende](https://www.microsoft.com/business-store). 

2. Accedere al portale. 

3. Abilitare le licenze offline: fare clic su **Gestisci->impostazioni dello Store**e quindi selezionare la casella **di controllo Mostra app con licenza offline per gli acquisti di persone nello Store** , come illustrato nella figura 1. Per altre informazioni sui modelli di licenze per le app Microsoft Store per le aziende, vedere [app in Microsoft Store per le aziende e l'istruzione](https://docs.microsoft.com/microsoft-store/).<br/> <br/>
   ![Casella di controllo Mostra app licenze offline](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *Figura 1. Abilitare le app per l'uso offline*

4. Aggiungere l'app Surface al proprio account di Microsoft Store per le aziende seguendo questa procedura:
    * Fare clic sul menu **Shop** .
    * Nella casella di ricerca digitare **app Surface**e quindi fare clic sull'icona di ricerca.
    * Dopo aver presentato l'app Surface nei risultati della ricerca, fare clic sull'icona dell'app.
    * Viene visualizzata una scelta (selezionare **online** o **offline**), come illustrato nella figura 2.<br/><br/>
    
    ![Selezionare la modalità di gestione licenze offline e aggiungere l'app all'inventario](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")
    
    *Figura 2. Selezionare la modalità di gestione licenze offline e aggiungere l'app all'inventario*
    
    * Fare clic su **offline** per selezionare la modalità di gestione licenze offline.
    * Fai clic su **Ottieni l'app** per aggiungere l'app all'inventario di Microsoft Store per le aziende. Come illustrato nella figura 3, viene visualizzata una finestra di dialogo in cui viene chiesto di confermare che le app offline possono essere distribuite tramite uno strumento di gestione o scaricate dalla pagina dell'inventario della società nel proprio archivio privato.
    
    ![Finestra di riconoscimento app con licenza offline](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
    
    *Figura 3. Riconoscimento delle app con licenza offline*
    * Fai clic su **OK**.

## Scaricare l'app Surface da un account di Microsoft Store per le aziende
Dopo aver aggiunto un'app all'account Microsoft Store for business in modalità offline, è possibile scaricare e aggiungere l'app come AppxBundle a una condivisione di distribuzione.
1. Accedere all'account Microsoft Store for business all'indirizzo https://businessstore.microsoft.com .
2. Fare clic su **Gestisci->app & software**. Viene visualizzato un elenco di tutte le app della tua azienda, inclusa l'app Surface aggiunta nell' [app Aggiungi superficie a una sezione dell'account di Microsoft Store for business](#add-surface-app-to-a-microsoft-store-for-business-account) di questo articolo.
3. In **azioni**fare clic sui puntini di sospensione (**...**) e quindi su **Scarica per l'uso offline** per l'app Surface.
4. Selezionare le opzioni della **piattaforma** e dell' **architettura** desiderate dalle selezioni disponibili per l'app selezionata, come illustrato nella figura 4.

    ![Esempio di pacchetto AppxBundle](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")

    *Figura 4. Scaricare il pacchetto AppxBundle per un'app*
5. Fare clic su **Scarica**. Verrà scaricato il pacchetto AppxBundle. Verificare di aver notato il percorso del file scaricato, perché sarà necessario più avanti in questo articolo.
6. Fare clic sull'opzione **licenza codificata** o **licenza non codificata** . Usa l'opzione di licenza codificata con strumenti di gestione come Microsoft endpoint Configuration Manager o quando usi Windows Configuration designer per creare un pacchetto di provisioning. Selezionare l'opzione di licenza non codificata quando si usano le soluzioni di gestione e manutenzione immagini distribuzione o distributive basate sull'imaging, incluso Microsoft Deployment Toolkit (MDT).
7. Fare clic su **genera** per generare e scaricare la licenza per l'app. Verificare di aver notato il percorso del file di licenza, perché sarà necessario più avanti in questo articolo.

>[!NOTE]
>Quando scarichi un'app per l'uso offline, come l'app Surface, potresti notare una sezione nella parte inferiore della pagina denominata **Framework obbligatori**. I computer di destinazione devono avere i Framework installati per l'esecuzione dell'app, quindi potrebbe essere necessario ripetere il processo di download per ogni Framework necessario per l'architettura (x86 o x64) e includerli anche come parte della distribuzione di Windows descritta più avanti in questo articolo.

La figura 5 Mostra i Framework necessari per l'app Surface.

![Framework necessari per l'app Surface](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")

*Figura 5. Framework necessari per l'app Surface*

>[!NOTE]
>I numeri di versione dell'app Surface e dei Framework obbligatori cambieranno Man mano che le app verranno aggiornate. Controlla l'ultima versione di Surface app e ogni Framework in Microsoft Store for business. Usa sempre l'app Surface e le versioni di Framework consigliate fornite da Microsoft Store for business. L'uso di Framework obsoleti o di versioni non corrette può causare errori o arresti anomali dell'applicazione.

Per scaricare i Framework necessari per l'app Surface, eseguire le operazioni seguenti:
1. Fare clic sul pulsante **Scarica** in **Microsoft. VCLibs. 140.00 _ 14.0.23816.0_x64__8wekyb3d8bbwe**. Questo Scarica il Microsoft. VCLibs. 140.00 _ 14.0.23816.0_x64__8wekyb3d8bbwe. Appx file nella cartella specificata.
2. Fare clic sul pulsante **Scarica** in **Microsoft. NET. native. Runtime. 1.1 _ 1.1.23406.0_x64__8wekyb3d8bbwe**. Questo Scarica il file Microsoft. NET. native. Runtime. 1.1 _ 1.1.23406.0_x64__8wekyb3d8bbwe. appx nella cartella specificata.

>[!NOTE]
>Solo la versione a 64 bit (x64) di ogni Framework è necessaria per i dispositivi Surface. I dispositivi Surface sono dispositivi UEFI a 64 bit nativi e non sono compatibili con le versioni di Windows a 32 bit (x86) che richiedono Framework a 32 bit. 

## Installare l'app Surface nel computer con PowerShell
La procedura seguente riferisce l'app Surface nel computer e la rende disponibile per tutti gli account utente creati nel computer in seguito.
1. Usando la procedura descritta nell' [app come scaricare la superficie da una sezione di un account di Microsoft Store per le aziende](#download-surface-app-from-a-microsoft-store-for-business-account) di questo articolo, Scarica l'app Surface AppxBundle e il file di licenza. 
2. Avvia una sessione di PowerShell con privilegi elevati.

    >[!NOTE]
    >Se PowerShell non viene eseguito come amministratore, la sessione non avrà le autorizzazioni necessarie per installare l'app.
    
3. Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:
    ```
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    Dove si `<DownloadPath>` trova la cartella in cui è stato scaricato il file di licenza e AppxBundle dall'account di Microsoft Store per le aziende.

    Se ad esempio sono stati scaricati i file in c:\Temp, il comando eseguito è:
    ````
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. The Surface app will now be available on your current Windows computer. 

Before the Surface app is functional on the computer where it has been provisioned, you must also provision the frameworks described earlier in this article. To provision these frameworks, use the following procedure in the elevated PowerShell session you used to provision the Surface app.

5. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
6. In the elevated PowerShell session, copy and paste the following command:
   ```
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## Install Surface app with MDT
The following procedure uses MDT to automate installation of the Surface app at the time of deployment. The application is provisioned automatically by MDT during deployment and thus you can use this process with existing images. This is the recommended process to deploy the Surface app as part of a Windows deployment to Surface devices because it does not reduce the cross platform compatibility of the Windows image.
1. Using the procedure described [earlier in this article](#download-surface-app-from-a-microsoft-store-for-business-account), download the Surface app AppxBundle and license file. 
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page of the New Application Wizard, specify the default **Working Directory** and for the **Command** specify the file name of the AppxBundle, as follows:

   * Command:
     ```
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
   * Working Directory: %DEPLOYROOT%\Applications\SurfaceApp

For the Surface app to function on the target computer, it will also require the frameworks described earlier in this article. Use the following procedure to import the frameworks required for the Surface app into MDT and to configure them as dependencies.
1. Using the procedure described earlier in this article, download the framework files. Store each framework in a separate folder.
2. Using the New Application Wizard in the MDT Deployment Workbench, import the downloaded files as a new **Application with source files**.
3. On the **Command Details** page, type the file name of each application you downloaded in the **Command** field and the default Working Directory.

To configure the frameworks as dependencies of the Surface app, use this process:
1. Open the properties of the Surface app in the MDT Deployment Workbench.
2. Click the **Dependencies** tab, and then click **Add**.
3. Select the check box for each framework using the name you provided in the New Application Wizard.

After import, the Surface app will be available for selection in the **Applications** step of the Windows Deployment Wizard. You can also install the application automatically by specifying the application in the deployment task sequence by following this process:
1. Open your deployment task sequence in the MDT Deployment Workbench.
2. Add a new **Install Application** task in the **State Restore** section of deployment.
3. Select **Install a single application** and specify the **Surface App** as the **Application to be installed**.

For more information about including apps into your Windows deployments, see [Deploy Windows 10 with the Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit).

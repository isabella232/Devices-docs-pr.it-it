---
title: Distribuire l'app Surface con Microsoft Store per le aziende o Microsoft Store per la formazione (Surface)
description: Scopri come aggiungere e scaricare l'app Surface con Microsoft Store per le aziende o Microsoft Store per la formazione, oltre a installare l'app Surface con PowerShell e MDT.
keywords: surface app, app, distribuzione, personalizzare
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
ms.date: 4/16/2021
ms.openlocfilehash: 339a6a3ab76f36004f2399b333d48487c9d6e31d
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676682"
---
# <a name="deploy-surface-app-with-microsoft-store-for-business-and-education"></a>Distribuire l'app Surface con Microsoft Store per le aziende e Education

**Si applica a**

- Surface Laptop 4
- Surface Pro 7+
- Surface Laptop Go
- Surface Pro 7
- Surface Laptop 3
- Surface Pro 6
- Surface Laptop 2
- Surface Go
- Surface Go con LTE
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


L'app Surface è un'app Microsoft Store leggera che fornisce il controllo di molte impostazioni e opzioni specifiche di Surface con accesso rapido alle informazioni sul dispositivo, tra cui il numero di serie, il nome del modello Surface, la versione UEFI e i driver correlati.  

I clienti che Windows Update riceveranno normalmente l'app Surface come parte degli aggiornamenti automatici. Tuttavia, se l'organizzazione prepara le immagini per la distribuzione nei dispositivi Surface, potresti voler includere l'app Surface (in precedenza denominata Surface Hub) nel processo di creazione di immagini e distribuzione invece di richiedere agli utenti di ogni singolo dispositivo di scaricare e installare l'app dal Microsoft Store o dal Microsoft Store per le aziende. 

> [!NOTE]
> Questo articolo non si applica a Surface Pro X. Per ulteriori informazioni, vedere [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md)

## <a name="surface-app-overview"></a>Panoramica dell'app Surface

L'app Surface è disponibile come download gratuito [da Microsoft Store](https://www.microsoft.com/store/apps/Surface/9WZDNCRFJB8P). Gli utenti possono scaricarla e installarla dal Microsoft Store, ma se l'organizzazione usa invece Microsoft Store per le aziende, dovrai aggiungerla all'inventario dello Store ed eventualmente includere l'app come parte del processo di distribuzione di Windows. Questi processi vengono illustrati in questo articolo. Per ulteriori informazioni sulle Microsoft Store per le aziende, [vedere Microsoft Store per le aziende](/microsoft-store/). 

## <a name="add-surface-app-to-a-microsoft-store-for-business-account"></a>Aggiungere un'app Surface a un Microsoft Store per le aziende account 

Prima che gli utenti possano installare o distribuire un'app dall'account Microsoft Store per le aziende di una società, le app desiderate devono prima essere rese disponibili e concesse in licenza agli utenti di un'azienda. 

1. Se non l'hai già fatto, crea un [Microsoft Store per le aziende account](https://www.microsoft.com/business-store). 

2. Accedere al portale. 

3. Abilita licenze offline: fai clic su Gestisci **** Impostazioni e quindi seleziona la casella di controllo Mostra app con licenza offline agli utenti che acquistino nello Store, come illustrato nella figura  >  **** 1. **** Per altre informazioni sui modelli Microsoft Store per le aziende licenze delle app, vedi [App in Microsoft Store per le aziende e Education.](/microsoft-store/)

   > [!div class="mx-imgBorder"]
   > ![Casella di controllo Mostra le app per le licenze offline](images/deploysurfapp-figure1-enablingapps.png "Show offline licenses apps checkbox")<br/>
   *Figura 1. Abilitare le app per l'uso offline*

4. Aggiungi l'app Surface al tuo account Microsoft Store per le aziende:

    * Cercare **l'app Surface** in Store 
    
    * Dopo aver presentato l'app Surface nei risultati della ricerca, fai clic sull'icona dell'app.
    
    * Viene visualizzata una scelta (selezionare **Online** o **Offline),** come illustrato nella figura 2.
    
      > [!div class="mx-imgBorder"]
      > ![Seleziona la modalità di licenza offline e aggiungi l'app all'inventario](images/deploysurfapp-fig2-selectingofflinelicense.png "Select the Offline licensing mode and add the app to your inventory")   
      *Figura 2. Seleziona la modalità di licenza offline e aggiungi l'app all'inventario*
    
    * Fare **clic su Offline** per selezionare la modalità di licenza offline.
    
    * Fai **clic su Ottieni l'app** per aggiungere l'app al tuo Microsoft Store per le aziende inventario. Come illustrato nella figura 3, verrà visualizzata una finestra di dialogo in cui viene richiesto di confermare che le app offline possono essere distribuite tramite uno strumento di gestione o scaricate dalla pagina dell'inventario aziendale nel proprio archivio privato.
    
      > [!div class="mx-imgBorder"]
      > ![Finestra di conferma delle app con licenza offline ](images/deploysurfapp-fig3-acknowledge.png "Offline-licensed app acknowledgement window")
       *Figura 3. Riconoscimento delle app con licenza offline*
      
    * Fai clic su **OK**.

## <a name="download-surface-app-from-a-microsoft-store-for-business-account"></a>Scaricare l'app Surface da un account Microsoft Store per le aziende utente
Dopo aver aggiunto un'app all'account Microsoft Store per le aziende in modalità offline, puoi scaricare e aggiungere l'app come AppxBundle a una condivisione di distribuzione.

1. Accedere all'account Microsoft Store per le aziende all'indirizzo https://businessstore.microsoft.com .

2. Fare **clic su Gestisci >app & software**. Viene visualizzato un elenco di tutte le app della tua azienda, inclusa l'app Surface che hai aggiunto nella sezione [Aggiungere l'app Surface a](#add-surface-app-to-a-microsoft-store-for-business-account) un account Microsoft Store per le aziende di questo articolo.

3. In **Azioni**fai clic sui puntini di sospensione (**...**) e quindi fai clic su Scarica per l'uso **offline** per l'app Surface.

4. Selezionare le opzioni **piattaforma** **e** architettura desiderate tra le selezioni disponibili per l'app selezionata, come illustrato nella figura 4.

    > [!div class="mx-imgBorder"]
    > ![Esempio del pacchetto AppxBundle](images/deploysurfapp-fig4-downloadappxbundle.png "Example of the AppxBundle package")<br/>
    *Figura 4. Scaricare il pacchetto AppxBundle per un'app*
    
5. Fare clic **su Scarica**. Il pacchetto AppxBundle verrà scaricato. Assicurati di prendere nota del percorso del file scaricato perché sarà necessario più avanti in questo articolo.

6. Fare clic **sull'opzione Licenza codificata** o **Licenza non codificata.** Usa l'opzione Licenza codificata con strumenti di gestione come Microsoft Endpoint Configuration Manager o quando usi progettazione Windows per creare un pacchetto di provisioning. Seleziona l'opzione Licenza non codificata quando usi Gestione e manutenzione immagini distribuzione o soluzioni di distribuzione basate sulla creazione di immagini, incluso Microsoft Deployment Toolkit (MDT).

7. Fai **clic su** Genera per generare e scaricare la licenza per l'app. Assicurati di prendere nota del percorso del file di licenza perché sarà necessario più avanti in questo articolo.

>[!NOTE]
>Quando scaririchi un'app per l'uso offline, ad esempio l'app Surface, potresti notare una sezione nella parte inferiore della pagina con l'etichetta **Framework obbligatori.** I computer di destinazione devono avere i framework installati per l'esecuzione dell'app, quindi potrebbe essere necessario ripetere il processo di download per ognuno dei framework necessari per l'architettura (x86 o x64) e includerli anche come parte della distribuzione di Windows illustrata più avanti in questo articolo.

La figura 5 mostra i framework necessari per l'app Surface.

> [!div class="mx-imgBorder"]
> ![Framework necessari per l'app Surface](images/deploysurfapp-fig5-requiredframework.png "Required frameworks for the Surface app")<br/>
*Figura 5. Framework necessari per l'app Surface*

>[!NOTE]
>I numeri di versione dell'app Surface e i framework necessari cambieranno quando le app vengono aggiornate. Controlla la versione più recente dell'app Surface e ogni framework in Microsoft Store per le aziende. Usa sempre l'app Surface e le versioni consigliate del framework come indicato da Microsoft Store per le aziende. L'uso di framework obsoleti o di versioni non corrette può causare errori o arresti anomali dell'applicazione.

Per scaricare i framework necessari per l'app Surface, segui questi passaggi:

1. Fare clic **sul** pulsante Download in **Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe**. Verrà scaricato il Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe. File Appx nella cartella specificata.

2. Fare **clic** sul pulsante Download **in Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe**. In questo modo il file Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx viene scaricato nella cartella specificata.

>[!NOTE]
>Solo la versione a 64 bit (x64) di ogni framework è necessaria per i dispositivi Surface. I dispositivi Surface sono dispositivi UEFI nativi a 64 bit e non sono compatibili con le versioni a 32 bit (x86) di Windows che richiedono framework a 32 bit. 

## <a name="install-surface-app-on-your-computer-with-powershell"></a>Installare l'app Surface nel computer con PowerShell
La procedura seguente esegue il provisioning dell'app Surface nel computer e la rende disponibile per tutti gli account utente creati nel computer in seguito.

1. Usando la procedura descritta nella sezione Come scaricare [l'app Surface](#download-surface-app-from-a-microsoft-store-for-business-account) da un account Microsoft Store per le aziende di questo articolo, scarica il file di licenza e AppxBundle dell'app Surface. 

2. Avvia una sessione di PowerShell con privilegi elevati.

    >[!NOTE]
    >Se non esegui PowerShell come amministratore, la sessione non dirà le autorizzazioni necessarie per installare l'app.
    
3. Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:

    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath <DownloadPath>\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath <DownloadPath>\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

    Dove `<DownloadPath>` è la cartella in cui hai scaricato appxBundle e il file di licenza dall'account Microsoft Store per le aziende account.

    Ad esempio, se i file sono stati scaricati in c:\Temp, il comando eseguito è:
    
    ```powershell
    Add-AppxProvisionedPackage –Online –PackagePath c:\Temp\ Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle –LicensePath c:\Temp\ Microsoft.SurfaceHub_8wekyb3d8bbwe_a53ef8ab-9dbd-dec1-46c5-7b664d4dd003.xml
    ```

4. L'app Surface sarà ora disponibile nel computer Windows corrente. 

   Prima che l'app Surface funzioni nel computer in cui è stato eseguito il provisioning, devi anche eseguire il provisioning dei framework descritti in precedenza in questo articolo. Per eseguire il provisioning di questi framework, usa la procedura seguente nella sessione di PowerShell con privilegi elevati usata per eseguire il provisioning dell'app Surface.

5. Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.VCLibs.140.00_14.0.23816.0_x64__8wekyb3d8bbwe.Appx
   ```
   
6. Nella sessione di PowerShell con privilegi elevati copia e incolla il comando seguente:

   ```powershell
   Add-AppxProvisionedPackage –Online –SkipLicense –PackagePath <DownloadPath>\Microsoft.NET.Native.Runtime.1.1_1.1.23406.0_x64__8wekyb3d8bbwe.Appx
   ```

## <a name="install-surface-app-with-mdt"></a>Installare l'app Surface con MDT
La procedura seguente usa MDT per automatizzare l'installazione dell'app Surface al momento della distribuzione. Il provisioning dell'applicazione viene effettuato automaticamente da MDT durante la distribuzione e quindi puoi usare questo processo con le immagini esistenti. Questo è il processo consigliato per distribuire l'app Surface come parte di una distribuzione di Windows nei dispositivi Surface perché non riduce la compatibilità tra piattaforme dell'Windows immagine.

1. Usando la procedura descritta [in precedenza in questo articolo,](#download-surface-app-from-a-microsoft-store-for-business-account)scarica l'app Surface AppxBundle e il file di licenza. 

2. Usando la Creazione guidata nuova applicazione in MDT Deployment Workbench, importare i file scaricati come nuova **applicazione con file di origine.**

3. Nella pagina **Dettagli comando** della Creazione guidata nuova applicazione specificare la **directory** di lavoro predefinita e per **Il** comando specificare il nome file di AppxBundle, come indicato di seguito:

   * Comando:
   
     ```console
     Microsoft.SurfaceHub_10.0.342.0_neutral_~_8wekyb3d8bbwe.AppxBundle
     ```
     
   * Directory di lavoro: %DEPLOYROOT%\Applications\SurfaceApp

Per il funzionamento dell'app Surface nel computer di destinazione, saranno necessari anche i framework descritti in precedenza in questo articolo. Usa la procedura seguente per importare i framework necessari per l'app Surface in MDT e configurarli come dipendenze.

1. Usando la procedura descritta in precedenza in questo articolo, scaricare i file del framework. Archiviare ogni framework in una cartella separata.

2. Usando la Creazione guidata nuova applicazione in MDT Deployment Workbench, importare i file scaricati come nuova **applicazione con file di origine.**

3. Nella pagina **Dettagli comando** digitare il nome file di ogni applicazione scaricata nel campo **Comando** e nella directory di lavoro predefinita.

Per configurare i framework come dipendenze dell'app Surface, usa questo processo:

1. Apri le proprietà dell'app Surface in MDT Deployment Workbench.

2. Fare clic **sulla scheda** Dipendenze e quindi su **Aggiungi.**

3. Selezionare la casella di controllo per ogni framework utilizzando il nome specificato nella Creazione guidata nuova applicazione.

Dopo l'importazione, l'app Surface sarà disponibile per la selezione nel passaggio **Applicazioni** della Windows distribuzione guidata. Puoi anche installare l'applicazione automaticamente specificandola nella sequenza di attività di distribuzione seguendo questo processo:

1. Apri la sequenza di attività di distribuzione in MDT Deployment Workbench.

2. Aggiungi una nuova attività **Install Application** nella sezione **State Restore** della distribuzione.

3. Seleziona **Installa una singola applicazione** e specifica **l'app Surface** come applicazione da **installare.**

Per altre informazioni sull'inclusione di app nelle Windows, vedi [Preparare la distribuzione con MDT.](/windows/deployment/deploy-windows-mdt/prepare-for-windows-deployment-with-mdt)

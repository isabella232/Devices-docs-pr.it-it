---
title: Creare pacchetti di provisioning (Surface Hub)
description: In Windows 10, le impostazioni che usano il Registro di sistema o un provider di servizi di configurazione (CSP) possono essere configurate tramite pacchetti di provisioning.
ms.assetid: 8AA25BD4-8A8F-4B95-9268-504A49BA5345
ms.reviewer: ''
manager: laurawi
keywords: aggiungere certificato, pacchetto di provisioning
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2019
ms.localizationpriority: medium
ms.openlocfilehash: 5e0714d284cc5c8207633719ec8fb52cec9f95cb
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576986"
---
# <a name="create-provisioning-packages-surface-hub"></a>Creare pacchetti di provisioning (Surface Hub)

Questo argomento spiega come creare un pacchetto di provisioning con Progettazione configurazione di Windows e come applicarlo ai dispositivi Surface Hub. Per Surface Hub, i pacchetti di provisioning possono essere usati per aggiungere certificati, installare app della piattaforma UWP (Universal Windows Platform) e personalizzare criteri e impostazioni.

È possibile applicare un pacchetto di provisioning tramite una chiavetta USB durante l'installazione di prima esecuzione o con l'app **Impostazioni**. 


## <a name="advantages"></a>Vantaggi
-   Configurare rapidamente i dispositivi senza usare un provider di gestione di dispositivi mobili (MDM, Mobile Device Management).

-   Connettività di rete non necessaria.

-   Semplicità di applicazione.

[Scopri i vantaggi e gli usi dei pacchetti di provisioning.](https://technet.microsoft.com/itpro/windows/configure/provisioning-packages)


## <a name="requirements"></a>Requisiti 

Per creare e applicare un pacchetto di provisioning a un dispositivo Surface Hub, sono necessari i requisiti seguenti:

-   Progettazione configurazione di Windows, che può essere installato tramite Microsoft Store o Windows 10 Assessment and Deployment Kit (ADK). [Scopri come installare Progettazione configurazione di Windows.](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd)
-   Una chiavetta USB.
-   Se applichi il pacchetto usando l'app **Impostazioni**, ti serviranno le credenziali di amministratore del dispositivo.

Devi creare il pacchetto di provisioning in un PC con Windows 10, salvare il pacchetto in un'unità USB e quindi distribuirlo nel tuo dispositivo Surface Hub.


## <a name="supported-items-for-surface-hub-provisioning-packages"></a>Elementi supportati per i pacchetti di provisioning di Surface Hub

Utilizzando la procedura guidata **Effettuare il provisioning dei dispositivi Surface Hub** è possibile:

- Registrarsi su Active Directory, Azure Active Directory o MDM 
- Creare un account amministratore dispositivo 
- Aggiungere applicazioni e certificati
- Configurare le impostazioni del proxy
- Aggiungere un file di configurazione di Surface Hub

>[!WARNING]
>È necessario eseguire Progettazione configurazione di Windows in Windows 10 per configurare la registrazione di Azure Active Directory utilizzando la procedura guidata.

Utilizzando l'editor di provisioning avanzato è possibile aggiungere questi elementi ai pacchetti di provisioning per Surface Hub:

- **Criteri**: Surface Hub supporta un sottoinsieme di criteri del [provider di servizi di configurazione Policy](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#surfacehubpolicies). 
- **Impostazioni**: puoi configurare qualsiasi impostazione del [provider di servizi di configurazione SurfaceHub](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx).

>[!TIP]
> Utilizzare la procedura guidata per creare un pacchetto con le impostazioni comuni, quindi passare all'editor avanzato per aggiungere altre impostazioni.
>
>![editor avanzato aperto](images/icd-simple-edit.png)

## <a name="use-the-surface-hub-provisioning-wizard"></a>Utilizzare la procedura guidata per il provisioning di Surface Hub

Dopo aver [installato Progettazione configurazione di Windows](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd) puoi usarlo per creare un pacchetto di provisioning.

### <a name="create-the-provisioning-package"></a>Creare il pacchetto di provisioning 

1. Aprire Progettazione configurazione di Windows:
   - Dal campo di ricerca della schermata Start o del menu Start digita "Progettazione configurazione di Windows" e fai clic sul collegamento corrispondente 
    
     oppure
    
   - Se hai installato Progettazione configurazione di Windows da ADK, passa a `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (in un computer x64) o a `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (in un computer x86), quindi fai doppio clic su **ICD.exe**.

2. Fai clic su **Effettuare il provisioning dei dispositivi Surface Hub**.

3. Assegna un nome al progetto e fai clic su **Avanti**.

### <a name="configure-settings"></a>Configurare le impostazioni

<table>
<tr><td style="width:45%" valign="top"><img src="images/one.png" alt="step one"/> <img src="images/add-certificates.png" alt="add certificates"/></br></br>Per effettuare il provisioning del dispositivo con un certificato, fai clic su <strong>Aggiungi certificato</strong>. Immetti un nome per il certificato, quindi individua e seleziona il certificato da utilizzare.</td><td><img src="images/add-certificates-details.png" alt="add a certificate"/></td></tr> 
<tr><td style="width:45%" valign="top"><img src="images/two.png" alt="step two"/>  <img src="images/proxy.png" alt="configure proxy settings"/></br></br>Scegli <strong>Sì</strong> o <strong>No</strong> per le impostazioni del proxy. Per configurazione predefinita Surface Hub rileva automaticamente le impostazioni del proxy, per cui è possibile selezionare <strong>No</strong> se è questa l'impostazione che si desidera. Tuttavia, se in precedenza, l'infrastruttura richiedeva l'utilizzo di un server proxy e, dopo la modifica, non è più necessario, è possibile utilizzare un pacchetto di provisioning per ripristinare le impostazioni predefinite dei dispositivi Surface Hub selezionando <strong>Sì</strong> e <strong>Rileva automaticamente impostazioni</strong>. </br></br>Scegliendo <strong>Sì</strong>, è possibile rilevare automaticamente le impostazioni del proxy o configurare manualmente le impostazioni immettendo un URL in uno script di installazione o un indirizzo statico del server proxy. È inoltre possibile identificare se si desidera utilizzare il server proxy per indirizzi locali e immettere le eccezioni (indirizzi a cui Surface Hub deve connettersi direttamente senza utilizzare il server proxy).  </td><td><img src="images/proxy-details.png" alt="proxy configuration details"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/three.png" alt="step three"/>  <img src="images/set-up-device-admins.png" alt="device admins"/></br></br>È possibile registrare il dispositivo in Active Directory e specificare un gruppo di sicurezza per usare l'app Impostazioni, eseguire la registrazione ad Azure Active Directory per consentire agli amministratori globali di usare l'app Impostazioni o creare un account amministratore locale nel dispositivo.</br></br>Per registrare il dispositivo in Active Directory, immettere le credenziali per un account utente con privilegi minimi per aggiungere il dispositivo al dominio e specificare il gruppo di sicurezza per disporre di credenziali di amministratore in Surface Hub. Se un pacchetto di provisioning che registra un dispositivo in Active Directory viene applicato a un dispositivo Surface Hub ripristinato, lo stesso account di dominio può essere utilizzato solo se l'account elencato è un amministratore di dominio o è lo stesso account che ha inizialmente configurato il dispositivo Surface Hub. In caso contrario, è necessario utilizzare un account di dominio diverso nel pacchetto di provisioning.</br></br>Prima di utilizzare una procedura guidata di Progettazione configurazione di Windows per configurare la registrazione in blocco in Azure AD, <a href="https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup" data-raw-source="[set up Azure AD join in your organization](https://docs.microsoft.com/azure/active-directory/active-directory-azureadjoin-setup)">configura l'aggiunta di Azure AD nella tua organizzazione</a>. L'impostazione <strong>Numero massimo di dispositivi per utente</strong> nel tenant di Azure AD determina quante volte può essere utilizzato il token di massa recuperato nella procedura guidata. Per registrare il dispositivo in Azure AD, seleziona l'opzione corrispondente e immetti un nome descrittivo per il token di massa che otterrai utilizzando la procedura guidata. Imposta una data di scadenza per il token (il valore massimo è di 30 giorni dalla data di recupero del token). Fai clic su <strong>Recupera token di massa</strong>. Nella finestra Consenti&#39;l'accesso immetti un account che dispone delle autorizzazioni per aggiungere un dispositivo <strong> ad Azure AD e quindi la </strong> password. Fai clic su <strong>Accetta</strong> per concedere le autorizzazioni necessarie a Progettazione configurazione di Windows.</br></br>Per creare un account amministratore locale, seleziona l'opzione corrispondente e immetti un nome utente e una password. </br></br><strong>Importante:</strong> se crei un account locale nel pacchetto di provisioning, devi la password utilizzando l'app <strong>Impostazioni</strong> ogni 42 giorni. Se la password non viene modificata entro tale periodo, l'account potrebbe essere bloccato ed è impossibile accedervi.  </td><td><img src="images/set-up-device-admins-details.png" alt="join Active Directory, Azure AD, or create a local admin account"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/four.png" alt="step four"/> <img src="images/enroll-mdm.png" alt="enroll in device management"/></br></br>Usa questa sezione per registrarti nei provider MDM oltre a Intune. Per la registrazione di Intune, usare l'aggiunta ad Azure AD nella sezione precedente con <a href="https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment" data-raw-source="[automatic Intune enrollment](https://docs.microsoft.com/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment)"> la registrazione automatica di </a> Intune.</br></br>Seleziona <strong>Sì</strong> o <strong>No</strong> per la registrazione in MDM. </br></br>Selezionando <strong>Sì</strong>, è necessario fornire un account di servizio e una password o un certificato di identificazione personale autorizzato a registrare il dispositivo, nonché specificare il tipo di autenticazione. Se richiesto dal provider MDM, immettere l'URL per i servizi di individuazione, registrazione e criteri. <a href="manage-settings-with-mdm-for-surface-hub.md" data-raw-source="[Learn more about managing Surface Hub with MDM.](manage-settings-with-mdm-for-surface-hub.md)">Altre informazioni sulla gestione di Surface Hub con MDM.</a></td><td><img src="images/enroll-mdm-details.png" alt="enroll in mobile device management"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/five.png" alt="step five"/> <img src="images/add-applications.png" alt="add applications"/></br></br>È possibile installare più app della piattaforma UWP (Universal Windows Platform) in un pacchetto di provisioning. Per informazioni sulle impostazioni, vedi <a href="https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps" data-raw-source="[Provision PCs with apps](https://technet.microsoft.com/itpro/windows/configure/provision-pcs-with-apps)">Effettuare il provisioning di PC con app</a>. </br></br><strong>Importante: anche se l'interfaccia della procedura guidata ti consente di selezionare un'app Win32 classica, includi solo le app UWP in un pacchetto di provisioning che verrà applicato </strong> a Surface Hub. Se si include un'app Win32 classica, il provisioning non andrà a buon fine. </td><td><img src="images/add-applications-details.png" alt="add an application"/></td></tr>
<tr><td style="width:45%" valign="top"><img src="images/six.png" alt="step six"/>  <img src="images/add-config-file.png" alt="Add configuration file"/></br></br>Non è&#39;configurare alcuna impostazione in questo passaggio. Fornisce istruzioni per includere un file di configurazione che contiene un elenco degli account del dispositivo. Il file di configurazione non deve contenere le intestazioni di colonna. Quando si applica il pacchetto di provisioning a Surface Hub, se un file di configurazione di Surface Hub è incluso nell'unità USB, è possibile selezionare l'account e il nome descrittivo per il dispositivo dal file. Vedere il <a href="#sample-configuration-file" data-raw-source="[Sample configuration file](#sample-configuration-file)">file di configurazione di esempio</a> per un esempio.</br></br><strong>Importante: il file di configurazione può essere applicato solo durante l'esperienza di installazione predefinita e può essere usato solo con i pacchetti di provisioning creati con progettazione della configurazione di Windows rilasciati con </strong> Windows 10 versione 1703.  </td><td><img src="images/add-config-file-details.png" alt="Add a Surface Hub configuration file"/></td></tr>
<tr><td style="width:45%" valign="top">  <img src="images/finish.png" alt="finish creating your package"/></br></br>Puoi impostare una password per proteggere il pacchetto di provisioning. Quando si applica il pacchetto di provisioning a un dispositivo devi immettere la password.</td><td><img src="images/finish-details.png" alt="Protect your package"/></td></tr>
</table>

Al termine, fai clic su **Crea**. L'operazione richiede solo pochi secondi. Al termine della compilazione del pacchetto, il percorso in cui è archiviato il pacchetto è visualizzato come collegamento ipertestuale nella parte inferiore della pagina.

## <a name="sample-configuration-file"></a>File di configurazione di esempio

Un file di configurazione di Surface Hub contiene un elenco degli account del dispositivo che il dispositivo può usare per connettersi a Exchange e Skype for Business. Quando si applica un pacchetto di provisioning a Surface Hub, è possibile includere un file di configurazione nella directory radice dell'unità flash USB, quindi selezionare l'account desiderato da applicare al dispositivo. Il file di configurazione può essere applicato solo durante la configurazione guidata dell'installazione (OOBE) e può essere usato solo con pacchetti di provisioning creati con la Progettazione configurazione di Windows rilasciata con Windows 10, versione 1703.

Utilizzare Microsoft Excel o altri editor CSV per creare un file CSV denominato `SurfaceHubConfiguration.csv`. Nel file, immettere un elenco di account del dispositivo e i nomi descrittivi in questo formato:

```console
<DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
```
>[!IMPORTANT]
>Poiché il file di configurazione archivia le password degli account del dispositivo in testo normale, è consigliabile aggiornare le password dopo aver applicato il pacchetto di provisioning per i dispositivi. È possibile utilizzare il [nodo DeviceAccount](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp#deviceaccount) nel [provider di servizi di configurazione di Surface Hub (CSP)](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/surfacehub-csp) per aggiornare le password tramite MDM.


Di seguito viene riportato un esempio di `SurfaceHubConfiguration.csv`. 

```console
Rainier@contoso.com,password,Rainier Surface Hub
Adams@contoso.com,password,Adams Surface Hub
Baker@contoso.com,password,Baker Surface Hub
Glacier@constoso.com,password,Glacier Surface Hub
Stuart@contoso.com,password,Stuart Surface Hub
Fernow@contoso.com,password,Fernow Surface Hub
Goode@contoso.com,password,Goode Surface Hub
Shuksan@contoso.com,password,Shuksan Surface Hub
Buckner@contoso.com,password,Buckner Surface Hub
Logan@contoso.com,password,Logan Surface Hub
Maude@consoto.com,password,Maude Surface hub
Spickard@contoso.com,password,Spickard Surface Hub
Redoubt@contoso.com,password,Redoubt Surface Hub
Dome@contoso.com,password,Dome Surface Hub
Eldorado@contoso.com,password,Eldorado Surface Hub
Dragontail@contoso.com,password,Dragontail Surface Hub
Forbidden@contoso.com,password,Forbidden Surface Hub
Oval@contoso.com,password,Oval Surface Hub
StHelens@contoso.com,password,St Helens Surface Hub
Rushmore@contoso.com,password,Rushmore Surface Hub
```

## <a name="use-advanced-provisioning"></a>Utilizzare il provisioning avanzato

Dopo aver [installato Progettazione configurazione di Windows](https://technet.microsoft.com/itpro/windows/configure/provisioning-install-icd) puoi usarlo per creare un pacchetto di provisioning.

### <a name="create-the-provisioning-package-advanced"></a>Creare il pacchetto di provisioning (avanzato)

1. Aprire Progettazione configurazione di Windows:
   - Dal campo di ricerca della schermata Start o del menu Start digita "Progettazione configurazione di Windows" e fai clic sul collegamento corrispondente 
    
     oppure
    
   - se hai installato Progettazione configurazione di Windows da ADK, passa a `C:\Program Files (x86)\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86` (in un computer x64) o a `C:\Program Files\Windows Kits\10\Assessment and Deployment Kit\Imaging and Configuration Designer\x86\ICD.exe` (in un computer x86), quindi fai doppio clic su **ICD.exe**.

2. Fai clic su **Provisioning avanzato**.
   
3. Assegna un nome al progetto e fai clic su **Avanti**.

4. Selezionare **Comune a Windows 10 Team**, fare clic su **Avanti**e quindi su **Fine.**

    ![Progettazione immagine e configurazione - Nuovo progetto](images/icd-new-project.png)

5. Nel progetto, in **Personalizzazioni disponibili,** selezionare **Impostazioni team comuni.**

    ![Progettazione immagine e configurazione - Impostazioni comuni](images/icd-common-settings.png)


### <a name="add-a-certificate-to-your-package"></a>Aggiungere un certificato al pacchetto
Puoi usare i pacchetti di provisioning per installare certificati che consentiranno al dispositivo di eseguire l'autenticazione in Microsoft Exchange.

> [!NOTE]
> I pacchetti di provisioning sono in grado di installare i certificati solo nell'archivio del dispositivo (computer locale) e non nell'archivio dell'utente. Se l'organizzazione richiede che i certificati siano installati **** nell'archivio utenti, puoi usare il pulsante Importa certificato nella sezione Aggiornamento dei certificati di sicurezza di **&**  >  **** dell'app hub **Impostazioni.** In alternativa, i criteri di gestione dei dispositivi mobili [(MDM)](manage-settings-with-mdm-for-surface-hub.md) possono essere usati per distribuire i certificati nell'archivio dei dispositivi o nell'archivio utenti.

1. Nel riquadro **Personalizzazioni disponibili**, passa a **Impostazioni di runtime** > **Certificati** > **ClientCertificates**.
   > [!NOTE]
   > La sezione **ClientCertificates** è per i file pfx con una chiave privata. I file CER per le CA radice devono essere inseriti nella sezione **RootCertificates** e per le CA intermedie nella sezione **CACertificates.**

2. Immettere un'etichetta per **CertificateName** e quindi fare clic su **Aggiungi.** 

2. Immetti **CertificatePassword**. 

3. Per **CertificatePath**, cerca e seleziona il certificato. 

4. Imposta **ExportCertificate** su **False**.

5. Per **KeyLocation**, seleziona **Software only**.


### <a name="add-a-universal-windows-platform-uwp-app-to-your-package"></a>Aggiungere un'app UWP (Universal Windows Platform) al pacchetto
Prima di aggiungere un'app UWP a un pacchetto di provisioning, hai bisogno del pacchetto dell'app (un file con estensione APPX o APPXBUNDLE) e di eventuali file di dipendenza. Se hai acquistato l'app da Microsoft Store per le aziende, ti servirà anche la licenza dell'app *non codificata*. Vedi [Distribuire app offline](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app) per informazioni su come scaricare questi elementi da Microsoft Store per le aziende.

1. Nel riquadro **Personalizzazioni disponibili** passa a **Impostazioni di runtime** > **UniversalAppInstall** > **DeviceContextApp**.

2. Immetti un valore per **PackageFamilyName** per l'app e quindi fai clic su **Aggiungi**. Per coerenza, usa il nome della famiglia di pacchetti dell'app. Se hai acquistato l'app da Microsoft Store per le aziende, puoi trovare il nome della famiglia di pacchetti nella licenza dell'app. Apri il file di licenza con un editor di testo e usa il valore tra i \<PFM\> \</PFM\> tag ... .

3. Per **ApplicationFile**, fai clic su **Sfoglia** per trovare e selezionare l'app di destinazione (un file \*.appx o \*.appxbundle).

4. Per **DependencyAppxFiles**, fai clic su **Sfoglia** per trovare e aggiungere eventuali dipendenze per l'app. Per Surface Hub, avrai bisogno solo delle versioni x64 di queste dipendenze.

Se hai acquistato l'app da Microsoft Store per le aziende, dovrai anche aggiungere la licenza dell'app al tuo pacchetto di provisioning.

1. Crea una copia della licenza dell'app e rinominala in modo da usare un'estensione **.ms-windows-store-license**. Ad esempio, "esempio.xml" diventa "esempio.ms-windows-store-license".

2. In Progettazione immagine e configurazione, nel riquadro **Personalizzazioni disponibili** passa a **Impostazioni di runtime** > **UniversalAppInstall** > **DeviceContextAppLicense**.

3. Immetti **LicenseProductId** e quindi fai clic su **Aggiungi**. Per coerenza, usa l'ID licenza dell'app disponibile nella licenza dell'app. Apri il file di licenza con un editor di testo. Quindi, nel \<License\> tag, usa il valore nell'attributo **LicenseID.**

4. Seleziona il nuovo nodo **LicenseProductId**. Per **LicenseInstall**, fai clic su **Sfoglia** per individuare e selezionare il file di licenza che hai rinominato nel passaggio 1.


### <a name="add-a-policy-to-your-package"></a>Aggiungere un criterio al pacchetto
Surface Hub supporta un sottoinsieme di criteri del [provider di servizi di configurazione Policy](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx). Alcuni di questi criteri possono essere configurati con Progettazione immagine e configurazione.

1. Nel riquadro **Personalizzazioni disponibili** passa a **Impostazioni di runtime** > **Criteri**.

2. Seleziona una delle aree dei criteri disponibili.

3. Seleziona e imposta il criterio che vuoi aggiungere al pacchetto di provisioning.


### <a name="add-surface-hub-settings-to-your-package"></a>Aggiungere impostazioni di Surface Hub al pacchetto 

Puoi aggiungere al pacchetto di provisioning impostazioni dal [provider di servizi di configurazione SurfaceHub](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx). 

1. Nel riquadro **Personalizzazioni disponibili** vai a **Impostazioni di runtime**  >  **SurfaceHub.**

2. Seleziona una delle aree delle impostazioni disponibili.

3. Seleziona e imposta l'impostazione che vuoi aggiungere al pacchetto di provisioning. 


## <a name="build-your-package"></a>Compilare il pacchetto

1. Dopo aver configurato il pacchetto di provisioning, fai clic su **Salva** nel menu **File**.

2. Leggi l'avviso indicante che i file di progetto possono contenere informazioni riservate e fai clic su **OK**.

    > [!IMPORTANT]
    > Quando crei un pacchetto di provisioning potresti includere informazioni riservate nei file di progetto e nel file del pacchetto di provisioning (con estensione PPKG). Anche se hai la possibilità di crittografare il file con estensione PPKG, i file di progetto non vengono crittografati. Devi archiviare i file del progetto in un luogo sicuro ed eliminare i file del progetto quando non sono più necessari.

3. Fai clic su **Pacchetto di provisioning** nel menu **Esporta**.

4. Modifica **Proprietario** in **Amministratore IT** per assegnare a questo pacchetto di provisioning una precedenza maggiore rispetto agli altri pacchetti di provisioning applicati al dispositivo da altre origini.

5. Imposta un valore per **Versione pacchetto** e quindi seleziona **Avanti**.

    > [!TIP]
    > Puoi apportare modifiche a pacchetti esistenti e modificare il numero di versione per aggiornare pacchetti applicati in precedenza.

6. Facoltativo: puoi scegliere di crittografare il pacchetto e abilitare la firma del pacchetto.

    -   **Abilita crittografia pacchetto** - Se selezioni questa opzione, sullo schermo verrà visualizzata una password generata automaticamente.

    -   **Abilita firma pacchetto**: se selezioni questa opzione, devi selezionare un certificato valido da usare per la firma del pacchetto. Per specificare il certificato, fai clic su **Sfoglia...** e scegli il certificato che vuoi usare per firmare il pacchetto.

        > [!IMPORTANT]
        > Ti consigliamo di includere nel pacchetto di provisioning un certificato di provisioning attendibile. Quando il pacchetto viene applicato a un dispositivo, il certificato viene aggiunto all'archivio di sistema e qualsiasi pacchetto firmato con tale certificato potrà in seguito essere applicato automaticamente. 

7. Fai clic su **Avanti** per specificare il percorso di output in cui vuoi posizionare il pacchetto di provisioning creato. Per impostazione predefinita, Progettazione immagini e configurazione di Windows usa la cartella di progetto come percorso di output.<p>
Facoltativamente, puoi fare clic su **Sfoglia** per modificare il percorso di output predefinito.

8. Fai clic su **Avanti**.

9. Fai clic su **Build** per iniziare a compilare il pacchetto. Le informazioni del progetto vengono visualizzate nella pagina di compilazione e la barra di stato indica lo stato della compilazione.<p>
Se devi annullare la compilazione, fai clic su **Cancel**. Ciò consente di annullare il processo di compilazione corrente, di chiudere la procedura guidata e di tornare alla **pagina per le personalizzazioni**.

10. Se la compilazione non riesce, viene visualizzato un messaggio di errore che include un link alla cartella del progetto. Puoi esaminare i log per stabilire la causa dell'errore. Dopo aver risolto il problema, prova a generare il pacchetto di nuovo.<p>
Se la compilazione riesce, verranno visualizzati il nome del pacchetto di provisioning, la directory di output e la directory del progetto.

    -   Se vuoi, puoi generare di nuovo il pacchetto di provisioning e selezionare un percorso diverso per il pacchetto di output. A tale scopo, fai clic su **Back** per modificare il nome e il percorso del pacchetto di output, quindi fai clic su **Next** per avviare un'altra compilazione.
    
    -   Al termine, fai clic su **Fine** per chiudere la procedura guidata e tornare alla pagina **Personalizzazioni**.

11. Seleziona il link **Percorso di output** per passare al percorso del pacchetto. Copia il file con estensione PPKG in un'unità flash USB vuota.


## <a name="apply-a-provisioning-package-to-surface-hub"></a>Applicare un pacchetto di provisioning in un dispositivo Surface Hub

Sono disponibili due opzioni per la distribuzione di pacchetti di provisioning in un dispositivo Surface Hub. Durante la prima esecuzione [guidata,](#apply-a-provisioning-package-during-first-run)è possibile applicare un pacchetto di provisioning che installa i certificati oppure al termine del programma di prima esecuzione, è possibile applicare un pacchetto di provisioning che configura impostazioni, app e certificati [tramite Impostazioni](#apply-a-package-using-settings). 


### <a name="apply-a-provisioning-package-during-first-run"></a>Applicare un pacchetto di provisioning durante la prima esecuzione

> [!IMPORTANT]
> Durante il programma di prima esecuzione, puoi usare solo pacchetti di provisioning per installare i certificati. Usa l'app **Impostazioni** per installare app e applicare altre impostazioni.

1. Alla prima accensione del dispositivo Surface Hub, il programma di prima esecuzione visualizzerà la [**pagina Ciao**](first-run-program-surface-hub.md#first-page). Assicurati che le impostazioni siano configurate in modo corretto prima di procedere.

2. Inserisci l'unità flash USB contenente il file con estensione ppkg in Surface Hub. Se il pacchetto è nella directory radice dell'unità, il programma di prima esecuzione lo riconoscerà e ti verrà chiesto se vuoi configurare il dispositivo. Seleziona **Configura**.

    ![Configurare il dispositivo?](images/provisioningpackageoobe-01.png)

3. Nella schermata successiva viene richiesto di selezionare un'origine di provisioning. Seleziona **Supporto rimovibile** e tocca **Avanti**.

    ![Esegui il provisioning in questo dispositivo](images/provisioningpackageoobe-02.png)
    
4. Seleziona il pacchetto di provisioning (\*.ppkg) che vuoi applicare e quindi tocca **Avanti**. Tieni presente che puoi installare un solo pacchetto durante la prima esecuzione.

    ![Scegliere un pacchetto](images/provisioningpackageoobe-03.png)

5. Il programma di prima esecuzione ti mostrerà un riepilogo delle modifiche che il pacchetto di provisioning applicherà. Seleziona **Sì, aggiungilo**.  

    ![Consideri attendibile il pacchetto?](images/provisioningpackageoobe-04.png)
    
6. Se un file di configurazione è incluso nella directory radice dell'unità flash USB, vedrai la dicitura **Selezionare una configurazione**. Nel file di configurazione verrà visualizzato l'account del primo dispositivo con un riepilogo delle informazioni sull'account che verranno applicate a Surface Hub.

    ![selezionare una configurazione](images/ppkg-config.png)    

7. In **Selezionare una configurazione**, seleziona il nome del dispositivo da applicare, quindi fai clic su **Avanti**.

    ![selezionare un nome descrittivo per il dispositivo](images/ppkg-csv.png)
    
Le impostazioni dal pacchetto di provisioning verranno applicate al dispositivo e la configurazione guidata sarà completa. Dopo il riavvio del dispositivo, è possibile rimuovere l'unità flash USB.

### <a name="apply-a-package-using-settings"></a>Applicare un pacchetto usando le Impostazioni

1. Inserisci l'unità flash USB contenente il file con estensione ppkg in Surface Hub.

2. Nel dispositivo Surface Hub avvia **Impostazioni** e immetti le credenziali di amministratore quando richiesto.

3. Vai su **Surface Hub** > **Gestione dei dispositivi**. In **Pacchetti di provisioning** seleziona **Aggiungi o rimuovi un pacchetto di provisioning**.

4. Seleziona **Aggiungi un pacchetto**.

5. Scegli il pacchetto di provisioning e seleziona **Aggiungi**. Potrebbe essere necessario reinserire le credenziali di amministratore, se richiesto.

6. Verrà visualizzato un riepilogo delle modifiche che il pacchetto di provisioning applicherà. Seleziona **Sì, aggiungilo**.



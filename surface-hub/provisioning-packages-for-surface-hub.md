---
title: Creare pacchetti di provisioning
description: In Windows 10, le impostazioni che usano il Registro di sistema o un provider di servizi di configurazione (CSP) possono essere configurate tramite pacchetti di provisioning.
ms.assetid: 8AA25BD4-8A8F-4B95-9268-504A49BA5345
ms.reviewer: dpandre
manager: laurawi
keywords: aggiungere certificato, pacchetto di provisioning
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/28/2021
ms.localizationpriority: medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 087826a7a0cba7a47accc0d3d66714289f2ae9d2
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613975"
---
# <a name="create-provisioning-packages-for-surface-hub"></a>Creare pacchetti di provisioning per Surface Hub

I pacchetti di provisioning consentono di automatizzare la distribuzione delle funzionalità chiave, consentendo di offrire un'esperienza coerente in tutti i Surface Hub dell'organizzazione.  Usando Windows Configuration Designer (WCD) in un PC separato, puoi completare le attività seguenti:

- Registrare in Active Directory o Azure Active Directory
- Creare un account amministratore del dispositivo
- Aggiungere applicazioni e certificati
- Configurare le impostazioni del proxy
- Aggiungere un file di configurazione di Surface Hub
- Configurare le impostazioni del provider di servizi [di configurazione (CSP)](/windows/client-management/mdm/surfacehub-csp)

## <a name="overview"></a>Panoramica

1. In un PC separato che esegue Windows 10, [installa Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22) dalla Microsoft Store.
1. Seleziona [**Provisioning Surface Hub dispositivi per**](#use-surface-hub-provisioning-wizard) configurare le impostazioni comuni tramite una procedura guidata. Oppure seleziona [Provisioning avanzato](#use-advanced-provisioning) per visualizzare e configurare tutte le impostazioni possibili.
1. Crea il pacchetto di provisioning e salvalo in un'unità USB.
1. Distribuisci il pacchetto nel Surface Hub durante la prima esecuzione dell'installazione o tramite l'app Impostazioni app. Per altre informazioni, vedi [Creare un pacchetto di provisioning per Windows 10](/windows/configuration/provisioning-packages/provisioning-create-package).

## <a name="use-surface-hub-provisioning-wizard"></a>Usare Surface Hub provisioning guidato

1. Apri Windows Progettazione configurazione e seleziona **Provisioning Surface Hub dispositivi**.<br>
    ![Utilizzare la procedura guidata per il provisioning di Surface Hub](images/sh-prov-start.png)
    
2. Assegnare un nome al progetto e selezionare **Avanti**.

### <a name="add-certificates"></a>Aggiungere certificati

> [!div class="mx-imgBorder"]
> ![aggiungere un certificato](images/sh-prov-cert.png)

Per eseguire il provisioning del dispositivo con un certificato, seleziona **Aggiungi un certificato.** Immettere un nome per il certificato e quindi selezionare il certificato da utilizzare.  Per le opzioni di provisioning avanzate, fai riferimento alla sezione seguente [Aggiungi un certificato al pacchetto.](#add-a-certificate-to-your-package)

### <a name="configure-proxy-settings"></a>Configurare le impostazioni del proxy

> [!div class="mx-imgBorder"]
> ![configurare le impostazioni del proxy](images/sh-prov-proxy.png)

1. Scegli **Sì** o **No** per le impostazioni del proxy. Per impostazione predefinita, Surface Hub rileva automaticamente le impostazioni proxy. Tuttavia, se in precedenza, l'infrastruttura richiedeva l'utilizzo di un server proxy e, dopo la modifica, non è più necessario, è possibile utilizzare un pacchetto di provisioning per ripristinare le impostazioni predefinite dei dispositivi Surface Hub selezionando **Sì** e **Rileva automaticamente impostazioni**.
2. Se si attiva o **disattiva Sì,** è possibile scegliere di rilevare automaticamente le impostazioni proxy o configurare manualmente le impostazioni immettendo una delle opzioni seguenti:

    - URL di uno script di installazione.
    - Informazioni sulla porta e sull'indirizzo di un server proxy statico.

3. Se si intende utilizzare uno script di installazione o un server proxy, disattivare **Rileva automaticamente impostazioni**. È possibile utilizzare uno script di *installazione o* un server proxy, non entrambi.
4. Immettere le eccezioni (indirizzi a cui Surface Hub connettersi direttamente senza utilizzare il server proxy). **Esempio:** *.office365.com
5. Identificare se utilizzare il server proxy per gli indirizzi locali.

### <a name="set-up-device-admins"></a>Configurare gli amministratori dei dispositivi

 > [!div class="mx-imgBorder"]
 > ![Partecipare ad Active Directory, Azure AD o creare un account amministratore locale](images/sh2-wcd.png)

È possibile registrare il dispositivo in Active Directory e specificare un gruppo di sicurezza per usare l'app Impostazioni, eseguire la registrazione ad Azure Active Directory per consentire agli amministratori globali di usare l'app Impostazioni o creare un account amministratore locale nel dispositivo.

1. Per registrare il dispositivo in Active Directory, immettere le credenziali per un account utente con privilegi minimi per aggiungere il dispositivo al dominio e specificare il gruppo di sicurezza per disporre di credenziali di amministratore in Surface Hub. Se si applica il pacchetto a un Surface Hub che è stato reimpostato, è possibile utilizzare lo stesso account di dominio purché sia lo stesso account che ha configurato inizialmente il Surface Hub. In caso contrario, è necessario utilizzare un account di dominio diverso nel pacchetto di provisioning.
2. Prima di usare Progettazione Windows configurazione per configurare la registrazione di Azure AD in blocco, [pianificare l'implementazione dell'aggiunta ad Azure AD.](/azure/active-directory/devices/azureadjoin-plan) L'impostazione **Numero massimo di dispositivi per utente** nel tenant di Azure AD determina quante volte può essere utilizzato il token di massa recuperato nella procedura guidata.
3. Per registrare il dispositivo in Azure AD, seleziona l'opzione corrispondente e immetti un nome descrittivo per il token di massa che otterrai utilizzando la procedura guidata. Imposta una data di scadenza per il token (il valore massimo è di 30 giorni dalla data di recupero del token). Seleziona **Ottieni token in blocco**. Nella finestra **Let's get you signed in** immetti un account che dispone delle autorizzazioni per aggiungere un dispositivo ad Azure AD, quindi la password. Selezionare **Accetta** per assegnare Windows progettazione della configurazione alle autorizzazioni necessarie.
4. Per creare un account amministratore locale, seleziona l'opzione corrispondente e immetti un nome utente e una password.

> [!IMPORTANT]
> Se crei un account locale nel pacchetto di provisioning, è necessario modificare la password utilizzando l'app **Impostazioni** ogni 42 giorni. Se la password non viene modificata entro tale periodo, l'account potrebbe essere bloccato ed è impossibile accedervi.

### <a name="enroll-in-third-party-mdm-provider"></a>Iscriversi a un provider MDM di terze parti

> [!div class="mx-imgBorder"]
> ![Iscriversi alla gestione di dispositivi mobili di terze parti](images/sh-prov-mdm.png)

Se usi un provider mdm (Mobile Device Management) di terze parti, puoi usare questa sezione per registrare Surface Hub. Per eseguire la registrazione in Intune, configurare innanzitutto l'aggiunta ad Azure AD, come descritto nella sezione precedente, e seguire le istruzioni nella documentazione di Intune [seguente: Configurare la](/mem/intune/enrollment/quickstart-setup-auto-enrollment)registrazione automatica per Windows 10 dispositivi .

1. **Attiva/disattiva Sì** **o No** per la registrazione in MDM di terze parti.
2. Se si attiva o **disattiva Sì,** fornire un account di servizio e una password o un'identificazione personale del certificato autorizzato a registrare il dispositivo e specificare il tipo di autenticazione.
3. Se richiesto dal provider MDM, immetti gli URL per il servizio di individuazione, il servizio di registrazione e il servizio criteri.

 Per altre informazioni, vedi [Gestire Surface Hub con un provider MDM.](manage-settings-with-mdm-for-surface-hub.md)

### <a name="add-applications"></a>Aggiungere applicazioni

> [!div class="mx-imgBorder"]
> ![aggiungere un'applicazione](images/sh-prov-apps.png)

È possibile installare più app della piattaforma UWP (Universal Windows Platform) in un pacchetto di provisioning. Per altre informazioni, vedi [Effettuare il provisioning dei PC con le app.](/windows/configuration/provisioning-packages/provision-pcs-with-apps)

> [!NOTE]
> Anche Windows Configuration Designer ti consente di aggiungere un'app Win32 classica a un pacchetto di provisioning, Surface Hub accetta solo app UWP. Se si include un'app Win32 classica, il provisioning non andrà a buon fine.

### <a name="add-a-configuration-file"></a>Aggiungere un file di configurazione

Oltre a questo pacchetto di provisioning, puoi usare un file di Surface Hub di configurazione per semplificare ancora di più la configurazione dei dispositivi. Un file Surface Hub di configurazione contiene un elenco di account del dispositivo per la connessione a Exchange, Microsoft Teams o Skype for Business, nonché "nomi descrittivi" per la proiezione wireless.

**Per creare un file Surface Hub file di configurazione:**

1. Aprire Microsoft Excel (o un altro editor di .csv), creare un file .csv denominato SurfaceHubConfiguration.csv
2. Immetti un elenco di account del dispositivo e nomi descrittivi nel formato seguente:

    ```
    <DeviceAccountName>,<DeviceAccountPassword>,<FriendlyName>
    ```

    > [!NOTE]
    > Il file di configurazione non deve contenere le intestazioni di colonna. Se incluso in un pacchetto di provisioning applicato a Surface Hub, puoi selezionare l'account e il nome descrittivo per il dispositivo dal file. Per creare il file .csv, utilizzare un formato di indirizzo UPN (rainier@contoso.com) o un formato di nome di accesso di livello inferiore (contoso\rainier).

- rainier@contoso.com,password,Rainier Surface Hub

3. Salva il file nella cartella del progetto e copialo nella chiave USB con il pacchetto di provisioning.

> [!NOTE]
> Il file di configurazione può essere applicato solo durante la prima esecuzione dell'installazione.

### <a name="password-protect-provisioning-package"></a>Proteggere con password il pacchetto di provisioning

Se scegli di usare una password, dovrai immetterla ogni volta che applicherai il pacchetto di provisioning a un dispositivo.

### <a name="complete-provisioning-wizard"></a>Completare la procedura guidata di provisioning

Se devi solo configurare le impostazioni comuni, seleziona **Fine**creazione e passa alla  >  **** sezione Creare [il pacchetto.](#build-your-package) Oppure continua a configurare le impostazioni passando a Provisioning avanzato.

## <a name="use-advanced-provisioning"></a>Usare il provisioning avanzato

> [!TIP]
> Utilizzare la procedura guidata per creare un pacchetto con le impostazioni comuni, quindi passare all'editor avanzato per aggiungere altre impostazioni.<br><br> ![Passare all'editor avanzato](images/icd-simple-edit.png)

1. Se si continua dalla sezione precedente, selezionare **Passa all'editor** avanzato altrimenti aprire progettazione Windows **configurazione** e selezionare **Provisioning avanzato**.<br>
  ![Utilizzare il provisioning avanzato](images/sh-prov-adv.png)

2. Assegnare un nome al progetto e selezionare **Avanti**.
3. Selezionare **Common to Windows 10 Team**, selezionare **Next**e **quindi**finish .<br>
     ![Nuovo progetto WCD](images/icd-new-project.png)

4. Nel progetto, in **Personalizzazioni disponibili,** selezionare **Impostazioni team comuni.**<br>
     ![Impostazioni comuni WCD](images/icd-common-settings.png)

### <a name="add-a-certificate-to-your-package"></a>Aggiungere un certificato al pacchetto

Puoi usare i pacchetti di provisioning per installare certificati che consentiranno al dispositivo di eseguire l'autenticazione in Microsoft Exchange.

> [!NOTE]
> I pacchetti di provisioning sono in grado di installare i certificati solo nell'archivio del dispositivo (computer locale) e non nell'archivio dell'utente. Se l'organizzazione richiede che i certificati siano installati nell'archivio utenti, usa l'app Hub **Impostazioni:** Aggiornare & **Certificato**di importazione  >  **certificati**  >  **di sicurezza**.
In alternativa, puoi usare i  [**criteri MDM**](manage-settings-with-mdm-for-surface-hub.md) per distribuire i certificati nell'archivio dispositivi o nell'archivio utente.

> [!TIP]
> La sezione **ClientCertificates** è per i file pfx con una chiave privata. I file CER per le CA radice devono essere inseriti nella sezione **RootCertificates** e per le CA intermedie nella sezione **CACertificates.**

1. In **Windows Progettazione configurazione**  >  **Personalizzazioni disponibili** , passare a **Impostazioni di runtime**  >  **Certificati**  >  **ClientCertificates**.
2. Immetti un'etichetta per **CertificateName** e quindi seleziona **Aggiungi**.
3. Immetti **CertificatePassword**.
4. Per **CertificatePath**, cerca e seleziona il certificato.
5. Imposta **ExportCertificate** su **False**.
6. Per **KeyLocation**, seleziona **Software only**.

### <a name="add-a-uwp-app-to-your-package"></a>Aggiungere un'app UWP al pacchetto

Per aggiungere un'app UWP a un pacchetto di provisioning, è necessario il pacchetto dell'app (file con estensione appx o appxbundle) e tutti i file di dipendenza. Se hai acquistato l'app da Microsoft Store per le aziende, ti servirà anche la licenza dell'app *non codificata*. Vedi [Distribuire app offline](/microsoft-store/distribute-offline-apps) per informazioni su come scaricare questi elementi da Microsoft Store per le aziende.

**Per aggiungere un'app UWP:**

1. Nel riquadro **Personalizzazioni disponibili** passa a **Impostazioni di runtime** > **UniversalAppInstall** > **DeviceContextApp**.
2. Immetti un **PackageFamilyName** per l'app e quindi seleziona **Aggiungi.** Per coerenza, usa il nome della famiglia di pacchetti dell'app. Se hai acquistato l'app da Microsoft Store per le aziende, puoi trovare il nome della famiglia di pacchetti nella licenza dell'app. Apri il file di licenza con un editor di testo e usa il valore tra i tag PFM.
3. Per **ApplicationFile**seleziona **Sfoglia per** trovare e selezionare l'app di destinazione ( .appx o .appxbundle).
4. Per **DependencyAppxFiles**seleziona **Sfoglia** per trovare e aggiungere eventuali dipendenze per l'app. Per Surface Hub, avrai bisogno solo delle versioni x64 di queste dipendenze.

Se hai acquistato l'app dal Microsoft Store per le aziende, dovrai aggiungere la licenza dell'app al pacchetto di provisioning.

**Per aggiungere la licenza dell'app:**

1. Crea una copia della licenza dell'app e rinominala in modo da usare un'estensione **.ms-windows-store-license**. Ad esempio, rinomina "example.xml" in "example.ms-windows-store-license".
2. In Progettazione Windows configurazione passare a **Personalizzazioni**disponibili  >  **Impostazioni di runtime**  >  **UniversalAppInstall**  >  **DeviceContextAppLicense**.
3. Immetti **licenseProductId** e quindi seleziona **Aggiungi**. Per coerenza, usa l'ID licenza dell'app disponibile nella licenza dell'app. Apri il file di licenza con un editor di testo. Quindi, nel tag **License,** usa il valore **nell'attributo LicenseID.**
4. Seleziona il nuovo nodo **LicenseProductId**. Per **LicenseInstall**seleziona **Sfoglia per** trovare e selezionare il file di licenza rinominato (example.ms-windows-store-license).

### <a name="add-a-policy-to-your-package"></a>Aggiungere un criterio al pacchetto

Surface Hub supporta un sottoinsieme di criteri del [provider di servizi di configurazione Policy](/windows/client-management/mdm/policy-configuration-service-provider). Alcuni di questi criteri possono essere configurati con Progettazione Windows configurazione.

 **Per aggiungere [criteri CSP:](/windows/client-management/mdm/policies-in-policy-csp-supported-by-surface-hub)**

1. Vai a **Personalizzazioni disponibili**  >  **Impostazioni di runtime**  >  **Criteri**.
2. Selezionare il componente che si desidera gestire e configurare l'impostazione dei criteri in base alle esigenze. Ad esempio, per impedire ai dipendenti di usare l'esplorazione del sito Web InPrivate Surface Hub, selezionare **AllowInPrivate** e quindi **selezionare Disabilita**.  

    > [!div class="mx-imgBorder"]
    > ![Configurare l'impostazione dei criteri](images/sh-prov-policies.png)

### <a name="add-surface-hub-settings-to-your-package"></a>Aggiungere impostazioni di Surface Hub al pacchetto

Puoi aggiungere al pacchetto di provisioning impostazioni dal [provider di servizi di configurazione SurfaceHub](/windows/client-management/mdm/surfacehub-csp).

1. Passare a **Personalizzazioni disponibili**  >  **Common Team Edition Impostazioni**.
1. Selezionare il componente che si desidera gestire e configurare l'impostazione dei criteri in base alle esigenze.
1. Al termine della configurazione del pacchetto di provisioning, selezionare **Salva**  >  **file.**
1. Leggere l'avviso che i file di progetto potrebbero contenere informazioni riservate e selezionare **OK**

### <a name="build-your-package"></a>Compilare il pacchetto

Quando crei un pacchetto di provisioning potresti includere informazioni riservate nei file di progetto e nel file del pacchetto di provisioning (con estensione PPKG). Anche se hai la possibilità di crittografare il file con estensione PPKG, i file di progetto non vengono crittografati.  Archiviare i file di progetto in un percorso sicuro o eliminarli se non sono più necessari.

1. Apri **il Windows di**provisioning di Configuration Designer  >  ****  >  **Export.**
2. Cambia **proprietario** in **Amministratore IT**.  
3. Imposta un valore per **Versione pacchetto** e quindi seleziona **Avanti**.

> [!TIP]
> L'impostazione del proprietario su Amministratore IT garantisce che le impostazioni del pacchetto mantengano le "proprietà di precedenza" appropriate e rimangano effettive su Surface Hub se altri pacchetti di provisioning vengono successivamente applicati da altre origini.

> [!TIP]
> Puoi modificare i pacchetti esistenti e modificare il numero di versione per aggiornare i pacchetti applicati in precedenza.

4. Facoltativo: puoi scegliere di crittografare il pacchetto e abilitare la firma del pacchetto:

    1. Seleziona **Crittografa pacchetto** e quindi immetti una password.
    1. Selezionare **Sign package**  >  **Browse** e scegliere il certificato in base alle esigenze.

    > [!IMPORTANT]
    > È consigliabile includere un certificato di provisioning attendibile nel pacchetto di provisioning. Quando il pacchetto viene applicato a un dispositivo, il certificato viene aggiunto all'archivio di sistema, consentendo l'applicazione automatica dei pacchetti successivi.

5. Selezionare **Avanti** per specificare il percorso di output. Per impostazione predefinita, Progettazione configurazione di Windows usa la cartella di progetto come percorso di output. Oppure selezionare **Sfoglia** per modificare il percorso di output predefinito. Seleziona **Avanti**.
6. Seleziona **Compila** per iniziare a compilare il pacchetto. Le informazioni sul progetto vengono visualizzate nella pagina di compilazione.
7. Se la compilazione ha esito negativo, viene visualizzato un messaggio di errore con un collegamento alla cartella del progetto. Esaminare i log per diagnosticare l'errore e provare a compilare di nuovo il pacchetto.
8. Se la compilazione ha esito positivo, vengono visualizzati il nome del pacchetto di provisioning, la directory di output e la directory del progetto. Selezionare **Fine** per chiudere la procedura guidata e tornare alla pagina Personalizzazioni.
9. Seleziona  **il percorso**  di output per passare al percorso del pacchetto. Copia il file con estensione PPKG in un'unità flash USB vuota.

## <a name="apply-a-provisioning-package-to-surface-hub"></a>Applicare un pacchetto di provisioning in un dispositivo Surface Hub

Sono disponibili due opzioni per la distribuzione di pacchetti di provisioning in un dispositivo Surface Hub. Durante la prima esecuzione [guidata,](#apply-a-provisioning-package-during-first-run)è possibile applicare un pacchetto di provisioning che installa i certificati oppure al termine del programma di prima esecuzione, è possibile applicare un pacchetto di provisioning che configura impostazioni, app e certificati [tramite Impostazioni](#apply-a-provisioning-package-using-settings-app).

### <a name="apply-a-provisioning-package-during-first-run"></a>Applicare un pacchetto di provisioning durante la prima esecuzione

> [!IMPORTANT]
> Durante il programma di prima esecuzione, puoi usare solo pacchetti di provisioning per installare i certificati. Usa l'app **Impostazioni** per installare app e applicare altre impostazioni.

1. Quando si attiva il Surface Hub per la prima volta, nel programma di prima esecuzione viene visualizzata la pagina Hi [**there**](first-run-program-surface-hub.md). Assicurati che le impostazioni siano configurate in modo corretto prima di procedere.
2. Inserisci l'unità flash USB contenente il file con estensione ppkg in Surface Hub. Se il pacchetto è nella directory radice dell'unità, il programma di prima esecuzione lo riconoscerà e ti verrà chiesto se vuoi configurare il dispositivo. Seleziona **Configura**.
3. Nella schermata successiva viene richiesto di selezionare un'origine di provisioning. Seleziona **Supporto rimovibile** e tocca **Avanti**.
4. Seleziona il pacchetto di provisioning (*.ppkg) che vuoi applicare e tocca **Avanti.** Tieni presente che puoi installare un solo pacchetto durante la prima esecuzione.
5. Il programma di prima esecuzione ti mostrerà un riepilogo delle modifiche che il pacchetto di provisioning applicherà. Seleziona **Sì, aggiungilo**.
6. Se un file di configurazione è incluso nella directory radice dell'unità flash USB, vedrai la dicitura **Selezionare una configurazione**. Nel file di configurazione verrà visualizzato l'account del primo dispositivo con un riepilogo delle informazioni sull'account che verranno applicate a Surface Hub.
7. In **Selezionare una configurazione**selezionare il nome del dispositivo da applicare e quindi selezionare **Avanti.**

Le impostazioni dal pacchetto di provisioning verranno applicate al dispositivo e la configurazione guidata sarà completa. Dopo il riavvio del dispositivo, è possibile rimuovere l'unità flash USB.

### <a name="apply-a-provisioning-package-using-settings-app"></a>Applicare un pacchetto di provisioning con Impostazioni app

1. Inserisci l'unità flash USB contenente il file con estensione ppkg in Surface Hub.
2. Da Surface Hub, avviare **Impostazioni** e immettere le credenziali di amministratore quando richiesto.
3. Vai su **Surface Hub** > **Gestione dei dispositivi**. In **Pacchetti di provisioning**seleziona Aggiungi o rimuovi un pacchetto di **provisioning**Aggiungi  >  **un pacchetto.**
4. Scegli il pacchetto di provisioning e seleziona **Aggiungi**.  Se richiesto, immettere di nuovo le credenziali di amministratore.
5. Verrà visualizzato un riepilogo delle modifiche da applicare. Seleziona **Sì, aggiungilo**.

## <a name="learn-more"></a>Altre informazioni

- [Scaricare Windows Progettazione configurazione](https://www.microsoft.com/store/apps/9nblggh4tx22)
- [Creare un pacchetto di provisioning per Windows 10](/windows/configuration/provisioning-packages/provisioning-create-package)
- [Gestire Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md)

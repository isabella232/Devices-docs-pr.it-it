---
title: Registrare e configurare i dispositivi Surface con SEMM (Surface)
description: Scopri come creare un pacchetto di configurazione UEFI di Surface per controllare le impostazioni di Surface UEFI e registrare un dispositivo Surface in SEMM.
keywords: surface enterprise management
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: hachinda
manager: laurawi
ms.date: 1/15/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 7626c6b5d98f65cbaa4f3ffae7649bd5dc05b56f
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449489"
---
# <a name="enroll-and-configure-surface-devices-with-semm"></a>Registrare e configurare i dispositivi Surface con SEMM

Con la modalità di gestione di Microsoft Surface Enterprise (SEMM), puoi configurare in modo sicuro le impostazioni di Surface UEFI in un dispositivo Surface e gestire tali impostazioni nei dispositivi Surface nell'organizzazione. Quando un dispositivo Surface viene gestito da SEMM, tale dispositivo viene considerato *registrato (a* volte definito attivato). Questo articolo illustra come creare un pacchetto di configurazione UEFI di Surface che non solo controlla le impostazioni di Surface UEFI, ma registra anche un dispositivo Surface in SEMM.

Per una panoramica più generale di SEMM, vedi [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

In alternativa a SEMM, i dispositivi Surface più nuovi supportano la gestione remota di un sottoinsieme di impostazioni del firmware tramite Microsoft Intune. Per altre informazioni, fai riferimento alla [gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

> [!NOTE]
> SEMM è supportato su Surface Pro X solo tramite il gestore UEFI. Per ulteriori informazioni, vedere [Deploying, managing, and servicing Surface Pro X](surface-pro-arm-app-management.md).

#### <a name="download-and-install-microsoft-surface-uefi-configurator"></a>Scaricare e installare Microsoft Surface UEFI Configurator

Lo strumento usato per creare pacchetti SEMM è Microsoft Surface UEFI Configurator. Puoi scaricare il configuratore UEFI di Microsoft Surface dalla pagina [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft.
Esegui il file del programma di installazione Windows configuratore UEFI (.msi) di Microsoft Surface per avviare l'installazione dello strumento. Al termine del programma di installazione, trova Configuratore UEFI di Microsoft Surface nella sezione Tutte le app del menu Start.

>[!NOTE]
>Configuratore UEFI di Microsoft Surface è supportato solo in Windows 10 e Windows 11.

## <a name="create-a-surface-uefi-configuration-package"></a>Creare un pacchetto di configurazione UEFI di Surface

Il pacchetto di configurazione UEFI di Surface svolge sia il ruolo di applicare una nuova configurazione delle impostazioni UEFI di Surface a un dispositivo Surface gestito con SEMM sia il ruolo di registrazione dei dispositivi Surface in SEMM. La creazione di un pacchetto di configurazione richiede che tu abbia un certificato di firma da usare con SEMM per proteggere la configurazione delle impostazioni UEFI in ogni dispositivo Surface. Per altre informazioni sui requisiti per il certificato SEMM, vedi [Modalità di gestione di Microsoft Surface Enterprise.](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)

Per creare un pacchetto di configurazione UEFI di Surface, segui questi passaggi:

1. Apri Configuratore UEFI di Microsoft Surface dalla menu Start.

2. Fai clic su **Start**.

3. Fare **clic su Pacchetto** di configurazione, come illustrato nella figura 1.

   ![Creare un pacchetto per la registrazione SEMM.](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *Figura 1. Selezionare Pacchetto di configurazione per creare un pacchetto per la registrazione e la configurazione SEMM*

4. Fare **clic su Protezione** certificato per aggiungere il file del certificato esportato con la chiave privata (pfx), come illustrato nella figura 2. Passare al percorso del file del certificato, selezionarlo e quindi fare clic su **OK**.

   ![Aggiungi il certificato SEM e la password UEFI di Surface al pacchetto di configurazione.](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *Figura 2. Aggiungere il certificato SEMM e la password UEFI di Surface a un pacchetto di configurazione UEFI di Surface*

5. Quando viene richiesto di confermare la password del certificato, immettere e confermare la password per il file del certificato e quindi fare clic su **OK**.

6. Fai **clic su Password di** protezione per aggiungere una password a Surface UEFI. Questa password sarà necessaria ogni volta che si avvia UEFI. Se questa password non viene immessa, verranno visualizzate solo le informazioni sul **PC****, informazioni** **su, Enterprise** e **** le pagine Esci. Si tratta di un elemento opzionale.

7. Quando richiesto, immetti e conferma la password scelta per Surface UEFI e quindi fai clic su **OK**. Se vuoi cancellare una password UEFI di Surface esistente, lascia vuoto il campo della password.

8. Se non vuoi che il pacchetto UEFI di Surface si applififi a un determinato dispositivo, nella pagina Scegli il tipo **di Surface** di destinazione fai clic sul dispositivo di scorrimento sotto il dispositivo corrispondente in modo che sia in posizione **Disattivato** , come illustrato nella figura 3.
   > [!TIP] 
   > Devi selezionare un dispositivo in quanto nessuno è selezionato per impostazione predefinita.

   ![Scegli i dispositivi per la compatibilità dei pacchetti.](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *Figura 3. Scegliere i dispositivi per la compatibilità dei pacchetti*

9. Fai clic su **Avanti**.

10. Se vuoi disattivare un componente nei dispositivi Surface gestiti, nella pagina Scegli **** i componenti da attivare o disattivare fai clic sul dispositivo di scorrimento accanto a qualsiasi dispositivo o gruppo di dispositivi che vuoi disattivare in modo che il dispositivo di scorrimento si trova nella posizione **Disattivato**. (Mostrato nella figura 4). La configurazione predefinita per ogni dispositivo è **Attivata**. Fare clic **sul pulsante** Reimposta se si desidera ripristinare la posizione predefinita di tutti i dispositivi di scorrimento.

    ![Disabilitare o abilitare i componenti surface.](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *Figura 4. Disabilitare o abilitare singoli componenti surface*

11. Fai clic su **Avanti**.

12. Per abilitare o disabilitare le opzioni avanzate in Surface UEFI o la visualizzazione delle pagine UEFI di Surface****, nella pagina Scegli le impostazioni avanzate per i dispositivi fai clic sul dispositivo di scorrimento accanto all'impostazione **** desiderata per configurare l'opzione su Attivato o **Disattivato** (illustrato nella figura 5). Nella sezione **Pagina iniziale UEFI** puoi usare i dispositivi di scorrimento per **Sicurezza, Dispositivi** e Avvio per **** controllare quali pagine sono disponibili per gli utenti che si avviano in Surface UEFI. **** Per altre informazioni sulle impostazioni UEFI di Surface, vedi [Gestire le impostazioni UEFI di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings). Fai **clic su** Compila dopo aver selezionato le opzioni per generare e salvare il pacchetto.

    ![Controlla le impostazioni UEFI avanzate di Surface e le pagine UEFI di Surface.](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *Figura 5. Controllare le impostazioni UEFI avanzate di Surface e le pagine UEFI di Surface con SEMM*

13. Nella finestra **di dialogo Salva** con nome specificare un nome per il pacchetto di configurazione UEFI di Surface, passare al percorso in cui si desidera salvare il file e quindi fare clic su **Salva**.

14. Quando il pacchetto viene creato e salvato **, viene visualizzata** la pagina Operazione completata.

    >[!NOTE]
    >Registrare i caratteri di identificazione personale del certificato visualizzati in questa pagina, come illustrato nella figura 6. Questi caratteri ti servono per confermare la registrazione dei nuovi dispositivi Surface in SEMM. Fai **clic su Fine** per completare la creazione del pacchetto e chiudi Il configuratore UEFI di Microsoft Surface.
    
    ![Visualizzazione dei caratteri di identificazione personale del certificato.](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")
    
    *Figura 6. Gli ultimi due caratteri dell'identificazione personale del certificato vengono visualizzati nella pagina Esito positivo*

Dopo aver creato il pacchetto di configurazione UEFI di Surface, puoi registrare o configurare i dispositivi Surface.

>[!NOTE]
>Quando viene creato un pacchetto di configurazione UEFI di Surface, viene creato un file di registro sul desktop con i dettagli delle impostazioni e delle opzioni del pacchetto di configurazione.

## <a name="enroll-a-surface-device-in-semm"></a>Registrare un dispositivo Surface in SEMM
Quando viene eseguito il pacchetto di configurazione UEFI di Surface, il certificato SEMM e i file di configurazione UEFI di Surface vengono a fasi nell'archiviazione del firmware del dispositivo Surface. Quando il dispositivo Surface viene riavviato, Surface UEFI elabora questi file e inizia il processo di applicazione della configurazione UEFI di Surface o della registrazione del dispositivo Surface in SEMM, come illustrato nella figura 7.

![Processo SEMM per la configurazione di Surface UEFI o la registrazione.](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*Figura 7. Processo SEMM per la configurazione di Surface UEFI o la registrazione di un dispositivo Surface*

Prima di iniziare il processo di registrazione di un dispositivo Surface in SEMM, assicurati di avere a disposizione gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri saranno necessari per confermare la registrazione del dispositivo (vedere la figura 6).

Per registrare un dispositivo Surface in SEMM con un pacchetto di configurazione UEFI di Surface, segui questi passaggi:

1. Esegui il pacchetto di configurazione UEFI di Surface .msi file nel dispositivo Surface che vuoi registrare in SEMM. In questo modo verrà eseguito il provisioning del file di configurazione UEFI di Surface nel firmware del dispositivo.
2. Selezionare la **casella di controllo** Accetto i termini del Contratto di Licenza per accettare il Contratto di Licenza con l'utente finale e quindi fare **clic su Installa** per avviare il processo di installazione.
3. Fai **clic su** Fine per completare l'installazione del pacchetto di configurazione UEFI di Surface e riavvia il dispositivo Surface quando ti viene richiesto di farlo.
4. Surface UEFI carica il file di configurazione e determina che SEMM non è abilitato nel dispositivo. Surface UEFI inizierà quindi il processo di registrazione SEMM, come indicato di seguito:
   * Surface UEFI verificherà che il file di configurazione SEMM contenga un certificato SEMM.
   * Surface UEFI richiederà di immettere gli ultimi due caratteri dell'identificazione personale del certificato per confermare la registrazione del dispositivo Surface in SEMM, come illustrato nella figura 8.

      ![La registrazione SEMM richiede gli ultimi due caratteri di identificazione personale del certificato.](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *Figura 8. La registrazione in SEMM richiede gli ultimi due caratteri dell'identificazione personale del certificato*

   * Surface UEFI archivia il certificato SEMM nel firmware e applica le impostazioni di configurazione specificate nel file di configurazione UEFI di Surface.
   
5. Il dispositivo Surface è ora registrato in SEMM e verrà avviato Windows.

Puoi verificare che un dispositivo Surface sia stato registrato correttamente in SEMM cercando Pacchetto di configurazione **di Microsoft Surface** **in Programmi** e funzionalità (come illustrato nella figura 9) o negli eventi archiviati nel registro del configuratore **UEFI di Microsoft Surface** , disponibile in Registri **applicazioni** e servizi nel Visualizzatore eventi (come illustrato nella figura 10).

:::image type="content" alt-text="Verificare la registrazione del dispositivo Surface in SEMM in Programmi e funzionalità." source="images/surface-semm-enroll-fig9.png":::

*Figura 9. Verificare la registrazione di un dispositivo Surface in SEMM in Programmi e funzionalità*

:::image type="content" alt-text="Verificare la registrazione del dispositivo Surface in SEMM nel Visualizzatore eventi." source="images/surface-semm-enroll-fig10.png":::

*Figura 10. Verificare la registrazione di un dispositivo Surface in SEMM nel Visualizzatore eventi*

Puoi anche verificare che il dispositivo sia registrato in SEMM in Surface UEFI: mentre il dispositivo è registrato, Surface UEFI conterrà la pagina di gestione di **Enterprise** (come illustrato nella figura 11).

:::image type="content" alt-text="Pagina di gestione Enterprise UEFI di Surface." source="images/surface-semm-enroll-fig11.png":::

*Figura 11. Pagina di gestione Enterprise uefi di Surface*


## <a name="configure-surface-uefi-settings-with-semm"></a>Configurare le impostazioni UEFI di Surface con SEMM

Dopo la registrazione di un dispositivo in SEMM, puoi eseguire i pacchetti di configurazione UEFI di Surface firmati con lo stesso certificato SEMM per applicare nuove impostazioni UEFI di Surface. Queste impostazioni vengono applicate automaticamente al successivo avvio del dispositivo, senza alcuna interazione da parte dell'utente. Puoi usare soluzioni di distribuzione delle applicazioni come Microsoft Endpoint Configuration Manager per distribuire i pacchetti di configurazione UEFI di Surface nei dispositivi Surface per modificare o gestire le impostazioni in Surface UEFI.

Per ulteriori informazioni su come distribuire i file di Windows Installer (.msi) con Configuration Manager, vedere [Deploy and manage applications with Microsoft Endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959).

Se hai protetto Surface UEFI con una password, gli utenti senza la password che tentano di eseguire l'avvio in Surface UEFI avranno solo le pagine relative **a** **PC****, informazioni** su, **** gestione Enterprise e uscita visualizzate.

Se non hai protetto Surface UEFI con una password o un utente immette correttamente la password, le impostazioni configurate con SEMM saranno disattivate (non disponibili) e il testo Alcune impostazioni sono gestite dall'organizzazione verranno visualizzate nella parte superiore della pagina, come illustrato nella figura 12.

:::image type="content" alt-text="Impostazioni gestito da SEMM disabilitato in Surface UEFI." source="images/surface-semm-enroll-fig12.png":::

*Figura 12. Impostazioni gestito da SEMM verrà disabilitato in Surface UEFI*

---
title: Registrare e configurare dispositivi Surface con SEMM (Surface)
description: Informazioni su come creare un pacchetto di configurazione UEFI di Surface per controllare le impostazioni di Surface UEFI e registrare un dispositivo Surface in SEMM.
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
ms.openlocfilehash: 6df11e1c6e0b28616cb4d365e159f134195c0ecb
ms.sourcegitcommit: b922aaf7287bdfb99f848aad455b2b4001b8f5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2022
ms.locfileid: "12472404"
---
# <a name="enroll-and-configure-surface-devices-with-semm"></a>Registrare e configurare i dispositivi Surface con SEMM

Con Microsoft Surface Enterprise Management Mode (SEMM), puoi configurare in modo sicuro le impostazioni di Surface UEFI in un dispositivo Surface e gestirle nei dispositivi Surface dell'organizzazione. Quando un dispositivo Surface viene gestito da SEMM, tale dispositivo viene considerato *registrato* (a volte definito attivato). Questo articolo illustra come creare un pacchetto di configurazione UEFI di Surface che controlla le impostazioni di Surface UEFI e registra un dispositivo Surface in SEMM.

Per una panoramica più generale di SEMM, vedere Microsoft Surface Enterprise Management Mode.For a more high-level overview of SEMM, see [Microsoft Surface Enterprise Management Mode.For](surface-enterprise-management-mode.md) a more high-level overview of SEMM, see Microsoft Surface Enterprise Management Mode.

In alternativa a SEMM, i dispositivi Surface più recenti supportano la gestione remota di un subset di impostazioni del firmware tramite Microsoft Intune. Per altre informazioni, vedere [Intune gestione delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

> [!NOTE]
> SEMM è supportato in Surface Pro X solo tramite UEFI Manager. Per altre informazioni, vedere [Distribuzione, gestione e manutenzione Surface Pro X](surface-pro-arm-app-management.md).

#### <a name="download-and-install-microsoft-surface-uefi-configurator"></a>Scaricare e installare Microsoft Surface UEFI Configurator

Lo strumento usato per creare pacchetti SEMM è Microsoft Surface UEFI Configurator. È possibile scaricare Microsoft Surface UEFI Configurator dalla pagina [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft.
Eseguire il file microsoft Surface UEFI Configurator Windows Installer (.msi) per avviare l'installazione dello strumento. Al termine del programma di installazione, trovare Microsoft Surface UEFI Configurator nella sezione Tutte le app del menu Start.

>[!NOTE]
>Microsoft Surface UEFI Configurator è supportato solo in Windows 10 e Windows 11.

## <a name="create-a-surface-uefi-configuration-package"></a>Creare un pacchetto di configurazione UEFI di Surface

Il pacchetto di configurazione UEFI di Surface svolge sia il ruolo di applicazione di una nuova configurazione delle impostazioni UEFI di Surface a un dispositivo Surface gestito con SEMM che il ruolo di registrazione dei dispositivi Surface in SEMM. La creazione di un pacchetto di configurazione richiede l'uso di un certificato di firma con SEMM per proteggere la configurazione delle impostazioni UEFI in ogni dispositivo Surface. Per altre informazioni sui requisiti per il certificato SEMM, vedere [Microsoft Surface Enterprise Management Mode.For](surface-enterprise-management-mode.md) more information about the requirements for the SEMM certificate, see Microsoft Surface Enterprise Management Mode.

Per creare un pacchetto di configurazione UEFI di Surface, seguire questa procedura:

1. Aprire Microsoft Surface UEFI Configurator dal menu Start.

2. Fai clic su **Start**.

3. Fare clic su **Pacchetto di configurazione**, come illustrato nella figura 1.

   ![Creare un pacchetto per la registrazione SEMM.](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *Figura 1. Selezionare Pacchetto di configurazione per creare un pacchetto per la registrazione e la configurazione SEMM*

4. Fare clic su **Protezione certificati** per aggiungere il file di certificato esportato con chiave privata (con estensione pfx), come illustrato nella figura 2. Passare al percorso del file del certificato, selezionare il file e quindi fare clic su **OK**.

   ![Aggiungere il certificato SEM e la password UEFI di Surface al pacchetto di configurazione.](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to the configuration package")

   *Figura 2. Aggiungere il certificato SEMM e la password UEFI di Surface al pacchetto di configurazione UEFI di Surface*

5. Quando viene richiesto di confermare la password del certificato, immettere e confermare la password per il file del certificato e quindi fare clic su **OK**.

6. Fare clic su **Protezione password** per aggiungere una password a Surface UEFI. Questa password sarà necessaria ogni volta che si esegue l'avvio in UEFI. Se questa password non viene immessa, verranno visualizzate solo le **informazioni sul PC**, **Informazioni su**, **gestione Enterprise** e **Pagine di uscita**. Si tratta di un elemento opzionale.

7. Quando richiesto, immettere e confermare la password scelta per Surface UEFI e quindi fare clic su **OK**. Lasciare vuoto il campo password se si vuole cancellare una password UEFI di Surface esistente.

8. Se non vuoi che il pacchetto SURFACE UEFI si applichi a un dispositivo specifico, nella pagina **Scegli il tipo di surface di destinazione** fai clic sul dispositivo di scorrimento sotto il dispositivo corrispondente in modo che si trova nella posizione **Disattivata** , come illustrato nella figura 3.
   > [!TIP] 
   > È necessario selezionare un dispositivo perché nessuno è selezionato per impostazione predefinita. Scorrere verso destra per visualizzare tutti i dispositivi disponibili.

   ![Scegliere i dispositivi per la compatibilità dei pacchetti e scorrere verso destra per visualizzare tutti i dispositivi disponibili](images/surface-semm-enroll-fig3.png "Choose devices for package compatibility")

   ![Scegliere i dispositivi per la compatibilità dei pacchetti.](images/surface-semm-enroll-fig3a.png "Choose devices for package compatibility")


   *Figura 3. Scegliere i dispositivi per la compatibilità dei pacchetti*

9. Fai clic su **Avanti**.

10. Se vuoi disattivare un componente nei dispositivi Surface gestiti, nella pagina **Scegli quali componenti vuoi attivare o disattivare** fai clic sul dispositivo di scorrimento accanto a qualsiasi dispositivo o gruppo di dispositivi che vuoi disattivare in modo che il dispositivo di scorrimento sia in posizione **Disattivata** . (Illustrato nella figura 4). La configurazione predefinita per ogni dispositivo è **attivata**. Fare clic sul pulsante **Reimposta** per riportare tutti i dispositivi di scorrimento nella posizione predefinita.

    ![Disabilitare o abilitare i componenti Surface.](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *Figura 4. Disabilitare o abilitare singoli componenti Surface*

11. Fai clic su **Avanti**.

12. Per abilitare o disabilitare le opzioni avanzate in Surface UEFI o la visualizzazione delle pagine UEFI di Surface, nella pagina **Scegliere le impostazioni avanzate per i dispositivi** fare clic sul dispositivo di scorrimento accanto all'impostazione desiderata per configurare l'opzione su **Attivato** o **Disattivato** (illustrato nella figura 5). Nella sezione **Front page UEFI** puoi usare i dispositivi di scorrimento per **Sicurezza**, **Dispositivi** e **Avvio** per controllare quali pagine sono disponibili per gli utenti che avviano Surface UEFI. Per altre informazioni sulle impostazioni UEFI di Surface, vedere [Gestire le impostazioni UEFI di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings). Al termine della selezione delle opzioni per generare e salvare il pacchetto, fare clic su **Compila**. 

    ![Controlla le impostazioni UEFI avanzate di Surface e le pagine UEFI di Surface.](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *Figura 5. Controllare le impostazioni UEFI avanzate di Surface e le pagine UEFI di Surface con SEMM*

13. Nella finestra di dialogo **Salva con** nome specificare il nome del pacchetto di configurazione UEFI di Surface, passare al percorso in cui si vuole salvare il file e fare clic su **Salva**.

14. Quando il pacchetto viene creato e salvato, viene visualizzata la pagina **Operazione riuscita** .

    >[!NOTE]
    >Registrare i caratteri di identificazione personale del certificato visualizzati in questa pagina, come illustrato nella figura 6. Questi caratteri saranno necessari per confermare la registrazione dei nuovi dispositivi Surface in SEMM. Fare clic su **Fine** per completare la creazione del pacchetto e chiudere Microsoft Surface UEFI Configurator.
    
    ![Visualizzazione dei caratteri di identificazione personale del certificato.](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")
    
    *Figura 6. Gli ultimi due caratteri dell'identificazione personale del certificato vengono visualizzati nella pagina Esito positivo*

Dopo aver creato il pacchetto di configurazione UEFI di Surface, è possibile registrare o configurare i dispositivi Surface.

>[!NOTE]
>Quando viene creato un pacchetto di configurazione UEFI di Surface, sul desktop viene visualizzato un file di log con i dettagli delle impostazioni e delle opzioni del pacchetto di configurazione.

## <a name="enroll-a-surface-device-in-semm"></a>Registrare un dispositivo Surface in SEMM
Quando viene eseguito il pacchetto di configurazione UEFI di Surface, il certificato SEMM e i file di configurazione UEFI di Surface vengono eseguiti in fasi nell'archiviazione del firmware del dispositivo Surface. Al riavvio del dispositivo Surface, Surface UEFI elabora questi file e inizia il processo di applicazione della configurazione UEFI di Surface o della registrazione del dispositivo Surface in SEMM, come illustrato nella figura 7.

![Processo SEMM per la configurazione di Surface UEFI o la registrazione.](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*Figura 7. Processo SEMM per la configurazione di Surface UEFI o la registrazione di un dispositivo Surface*

Prima di registrare un dispositivo Surface in SEMM, assicurarsi di disporre degli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri saranno necessari per confermare la registrazione del dispositivo (vedere la figura 6).

Per registrare un dispositivo Surface in SEMM con un pacchetto di configurazione UEFI di Surface, seguire questa procedura:

1. Eseguire il pacchetto di configurazione UEFI di Surface .msi file nel dispositivo Surface da registrare in SEMM. Verrà eseguito il provisioning del file di configurazione UEFI di Surface nel firmware del dispositivo.
2. Selezionare la casella di controllo **Accetto le condizioni nel Contratto di licenza** per accettare il Contratto di licenza con l'utente finale e fare clic su **Installa** per avviare il processo di installazione.
3. Fare clic su **Fine** per completare l'installazione del pacchetto di configurazione UEFI di Surface e riavviare il dispositivo Surface quando richiesto.
4. Surface UEFI caricherà il file di configurazione e determinerà che SEMM non è abilitato nel dispositivo. Surface UEFI inizierà quindi il processo di registrazione SEMM, come indicato di seguito:
   * Surface UEFI verificherà che il file di configurazione SEMM contenga un certificato SEMM.
   * Surface UEFI richiederà di immettere gli ultimi due caratteri dell'identificazione personale del certificato per confermare la registrazione del dispositivo Surface in SEMM, come illustrato nella figura 8.

      ![La registrazione SEMM richiede gli ultimi due caratteri dell'identificazione personale del certificato.](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *Figura 8. La registrazione SEMM richiede gli ultimi due caratteri dell'identificazione personale del certificato*

   * Surface UEFI archivierà il certificato SEMM nel firmware e applicherà le impostazioni di configurazione specificate nel file di configurazione UEFI di Surface.
   
5. Il dispositivo Surface è ora registrato in SEMM e verrà avviato in Windows.

È possibile verificare che un dispositivo Surface sia stato registrato correttamente in SEMM cercando **Microsoft Surface Configuration Package** in **Programmi e funzionalità** (come illustrato nella figura 9) o negli eventi archiviati nel log di **Microsoft Surface UEFI Configurator**, disponibile in **Registri applicazioni e servizi** in Visualizzatore eventi (come illustrato nella figura 10).

:::image type="content" alt-text="Verificare la registrazione del dispositivo Surface in SEMM in Programmi e funzionalità." source="images/surface-semm-enroll-fig9.png":::

*Figura 9. Verificare la registrazione di un dispositivo Surface in SEMM in Programmi e funzionalità*

:::image type="content" alt-text="Verificare la registrazione del dispositivo Surface in SEMM in Visualizzatore eventi." source="images/surface-semm-enroll-fig10.png":::

*Figura 10. Verificare la registrazione di un dispositivo Surface in SEMM in Visualizzatore eventi*

Puoi anche verificare che il dispositivo sia registrato in SEMM in Surface UEFI: mentre il dispositivo è registrato, Surface UEFI conterrà la pagina di **gestione Enterprise** (come illustrato nella figura 11).

:::image type="content" alt-text="Pagina di gestione di Surface UEFI Enterprise." source="images/surface-semm-enroll-fig11.png":::

*Figura 11. Pagina di gestione di Surface UEFI Enterprise*


## <a name="configure-surface-uefi-settings-with-semm"></a>Configurare le impostazioni UEFI di Surface con SEMM

Dopo la registrazione di un dispositivo in SEMM, è possibile eseguire i pacchetti di configurazione UEFI di Surface firmati con lo stesso certificato SEMM per applicare le nuove impostazioni UEFI di Surface. Queste impostazioni vengono applicate automaticamente al successivo avvio del dispositivo, senza alcuna interazione da parte dell'utente. È possibile usare soluzioni di distribuzione di applicazioni come Microsoft Endpoint Configuration Manager per distribuire i pacchetti di configurazione UEFI di Surface nei dispositivi Surface per modificare o gestire le impostazioni in Surface UEFI.

Per altre informazioni su come distribuire Windows file del programma di installazione (.msi) con Configuration Manager, vedere [Distribuire e gestire applicazioni con Microsoft Endpoint Configuration Manager](/mem/configmgr/apps/deploy-use/deploy-applications).

Si supponga di aver protetto Surface UEFI con una password. In tal caso, gli utenti senza password che tentano di avviare Surface UEFI avranno solo le **informazioni sul PC**, **Informazioni su**, **gestione Enterprise** e **Le pagine di uscita** visualizzate.

Se Surface UEFI non è stato protetto con una password o un utente immette correttamente la password, le impostazioni configurate con SEMM verranno disattivate (non disponibili) indicando  **che alcune impostazioni sono gestite dall'organizzazione**, come illustrato nella figura 12.

:::image type="content" alt-text="Impostazioni gestiti da SEMM sono disabilitati in Surface UEFI." source="images/surface-semm-enroll-fig12.png":::

*Figura 12. Impostazioni gestito da SEMM verrà disabilitato in Surface UEFI*

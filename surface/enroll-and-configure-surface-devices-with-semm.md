---
title: Registrare e configurare i dispositivi Surface con SEMM (Surface)
description: Informazioni su come creare un pacchetto di configurazione UEFI di Surface per controllare le impostazioni di Surface UEFI e registrare un dispositivo Surface in SEMM.
keywords: gestione di Surface Enterprise
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 183eceee47eba8b8d1e794e9e7d3efffa7a9b2e0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833482"
---
# Registrare e configurare i dispositivi Surface con SEMM

Con la modalità di gestione di Surface Enterprise (SEMM) Microsoft, è possibile configurare in modo sicuro le impostazioni di Surface UEFI su un dispositivo Surface e gestire tali impostazioni nei dispositivi Surface dell'organizzazione. Quando un dispositivo Surface viene gestito da SEMM, tale dispositivo viene considerato *registrato* (a volte indicato come attivato). Questo articolo illustra come creare un pacchetto di configurazione UEFI di Surface che non solo controlla le impostazioni di Surface UEFI, ma anche la registrazione di un dispositivo Surface in SEMM.

Per una panoramica più di alto livello di SEMM, vedi la [modalità di gestione Microsoft Surface Enterprise](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

Un metodo semplificato per la gestione del firmware dal cloud su Surface Pro 7, Surface Pro X e Surface laptop 3 è ora disponibile in anteprima pubblica. Per altre informazioni, vedere [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md).

> [!NOTE]
> SEMM è supportato solo in Surface Pro X tramite il gestore UEFI. Per altre informazioni, vedere [distribuzione, gestione e manutenzione di Surface Pro X](surface-pro-arm-app-management.md).

#### Scaricare e installare Microsoft Surface UEFI Configurator
Lo strumento usato per creare pacchetti di SEMM è Microsoft Surface UEFI Configurator. È possibile scaricare Microsoft Surface UEFI Configurator dalla pagina [strumenti superficie per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.
Eseguire il file di Windows Installer (MSI) Microsoft Surface UEFI Configurator per avviare l'installazione dello strumento. Al termine del programma di installazione, trova Microsoft Surface UEFI Configurator nella sezione tutte le app del menu Start.

>[!NOTE]
>Microsoft Surface UEFI Configurator è supportato solo in Windows 10.

## Creare un pacchetto di configurazione UEFI di Surface

Il pacchetto di configurazione UEFI di Surface esegue sia il ruolo dell'applicazione di una nuova configurazione delle impostazioni di Surface UEFI a un dispositivo Surface gestito con SEMM che il ruolo di registrazione dei dispositivi Surface in SEMM. La creazione di un pacchetto di configurazione richiede l'uso di un certificato di firma da usare con SEMM per proteggere la configurazione delle impostazioni UEFI in ogni dispositivo Surface. Per altre informazioni sui requisiti per il certificato SEMM, vedere [modalità Microsoft Surface Enterprise Management](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

Per creare un pacchetto di configurazione UEFI di Surface, eseguire le operazioni seguenti:

1. Aprire Microsoft Surface UEFI Configurator dal menu Start.
2. Fai clic su **Start**.
3. Fare clic su **pacchetto di configurazione**, come illustrato nella figura 1.

   ![Creare un pacchetto per l'iscrizione a SEMM](images/surface-ent-mgmt-fig1-uefi-configurator.png "Create a package for SEMM enrollment")

   *Figura 1. Selezionare pacchetto di configurazione per creare un pacchetto per la registrazione e la configurazione di SEMM*

4. Fare clic su **protezione certificato** per aggiungere il file di certificato esportato con la chiave privata (PFX), come illustrato nella figura 2. Passare al percorso del file del certificato, selezionare il file e quindi fare clic su **OK**.

   ![Aggiungere il certificato SEM e la password di Surface UEFI alla configurazione del pacchetto](images/surface-ent-mgmt-fig2-securepackage.png "Add the SEM certificate and Surface UEFI password to configuration package")

   *Figura 2. Aggiungere il certificato SEMM e la password UEFI di Surface a un pacchetto di configurazione UEFI di Surface*

5. Quando viene richiesto di confermare la password del certificato, immettere e confermare la password per il file di certificato e quindi fare clic su **OK**.
6. Fare clic su **password di protezione** per aggiungere una password per Surface UEFI. Questa password sarà necessaria ogni volta che si avvia l'avvio in UEFI. Se questa password non viene immessa, verranno visualizzate solo le pagine **informazioni** **su**PC, **gestione aziendale**e **uscita** . Si tratta di un elemento opzionale.
7. Quando viene richiesto, immettere e confermare la password scelta per l'UEFI di Surface e quindi fare clic su **OK**. Se si vuole cancellare una password di Surface UEFI esistente, lasciar vuoto il campo password.
8. Se non si vuole che il pacchetto UEFI di Surface si applichi a un determinato dispositivo, nella pagina **scegliere il tipo di superficie da cui si vuole** fare clic sulla barra di scorrimento sotto l'immagine di Surface Book o Surface Pro 4 in modo che sia in posizione **disattivata** . (Come illustrato nella figura 3).
   > [!NOTE] 
   > Per impostazione predefinita, è necessario selezionare un dispositivo come nessuno selezionato.

   ![Scegliere i dispositivi per la compatibilità dei pacchetti](images/surface-semm-enroll-fig3.jpg "Choose devices for package compatibility")

   *Figura 3. Scegliere i dispositivi per la compatibilità dei pacchetti*

9. Fai clic su **Avanti**.
10. Se si vuole disattivare un componente nei dispositivi di Surface gestiti, **scegliere i componenti da attivare o** disattivare la pagina, fare clic sul dispositivo di scorrimento accanto a qualsiasi periferica o gruppo di dispositivi da disattivare in modo che lo slider si trovi in posizione **disattivata** . (Illustrato nella figura 4). La configurazione predefinita per ogni dispositivo è **attivata**. Fare clic sul pulsante **Reimposta per ripristinare** la posizione predefinita di tutti i dispositivi di scorrimento.

    ![Disabilitare o abilitare i componenti di Surface](images/surface-ent-mgmt-fig3-enabledisable.png "Disable or enable Surface components")

    *Figura 4. Disabilitare o abilitare singoli componenti di Surface*

11. Fai clic su **Avanti**.
12. Per abilitare o disabilitare le opzioni avanzate in UEFI di Surface o nella visualizzazione di pagine UEFI di Surface, nella pagina **scegliere Impostazioni avanzate per i dispositivi** fare clic sul dispositivo di scorrimento accanto all'impostazione desiderata per configurare l'opzione **su** attivato o **disattivato** (illustrato nella figura 5). Nella sezione **prima pagina UEFI** puoi usare i cursori per la **sicurezza**, i **dispositivi**e l' **avvio** per controllare quali pagine sono disponibili per gli utenti che si avviano in UEFI di Surface. Per altre informazioni sulle impostazioni di Surface UEFI, vedere [gestire le impostazioni di Surface UEFI](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings). Fare clic su **Compila** dopo avere completato la selezione delle opzioni per generare e salvare il pacchetto.

    ![Controllare le impostazioni UEFI della superficie avanzata e le pagine UEFI di Surface](images/surface-ent-mgmt-fig4-advancedsettings.png "Control advanced Surface UEFI settings and Surface UEFI pages")

    *Figura 5. Controllare le impostazioni UEFI della superficie avanzata e le pagine UEFI di Surface con SEMM*

13. Nella finestra di dialogo **Salva con** nome specificare un cognome per il pacchetto di configurazione UEFI di Surface, passare al percorso in cui si vuole salvare il file e quindi fare clic su **Salva**.
14. Quando il pacchetto viene creato e salvato, viene visualizzata la pagina di **successo** .

>[!NOTE]
>Registrare i caratteri di identificazione personale del certificato visualizzati in questa pagina, come illustrato nella figura 6. Questi caratteri sono necessari per confermare la registrazione di nuovi dispositivi Surface in SEMM. Fare clic su **fine** per completare la creazione del pacchetto e chiudere Microsoft Surface UEFI Configurator.

![Visualizzazione dei caratteri di identificazione personale del certificato](images/surface-ent-mgmt-fig5-success.png "Display of certificate thumbprint characters")

*Figura 6. Gli ultimi due caratteri dell'identificazione personale del certificato vengono visualizzati nella pagina completata*

Dopo aver creato il pacchetto di configurazione UEFI di Surface, è possibile iscriversi o configurare i dispositivi Surface.

>[!NOTE]
>Quando viene creato un pacchetto di configurazione UEFI di Surface, sul desktop viene creato un file di log con i dettagli delle impostazioni e delle opzioni del pacchetto di configurazione.

## Registrare un dispositivo Surface in SEMM
Quando viene eseguito il pacchetto di configurazione UEFI di Surface, il certificato SEMM e i file di configurazione di Surface UEFI vengono assegnati allo spazio di archiviazione del firmware del dispositivo Surface. Quando il dispositivo Surface viene riavviato, Surface UEFI elabora questi file e inizia il processo di applicazione della configurazione UEFI di Surface o di registrazione del dispositivo Surface in SEMM, come illustrato nella figura 7.

![Processo di SEMM per la configurazione dell'UEFI o della registrazione della superficie](images/surface-semm-enroll-fig7.png "SEMM process for configuration of Surface UEFI or enrollment")

*Figura 7. Processo SEMM per la configurazione dell'UEFI di superficie o dell'iscrizione di un dispositivo Surface*

Prima di iniziare il processo di registrazione di un dispositivo Surface in SEMM, assicurarsi di avere a disposizione gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri saranno necessari per confermare la registrazione del dispositivo (vedere la figura 6).

Per registrare un dispositivo Surface in SEMM con un pacchetto di configurazione UEFI di Surface, eseguire le operazioni seguenti:

1. Eseguire il file di configurazione di Surface UEFI Package. msi nel dispositivo Surface che si vuole registrare in SEMM. In questo modo verrà provisioning il file di configurazione UEFI di Surface nel firmware del dispositivo.
2. Selezionare la casella di controllo Accetto **i termini del contratto di licenza** per accettare il contratto di licenza con l'utente finale (EULA) e quindi fare clic su **Installa** per avviare il processo di installazione.
3. Fare clic su **fine** per completare l'installazione del pacchetto di configurazione UEFI di Surface e riavviare il dispositivo Surface quando viene richiesto di eseguire questa operazione.
4. La superficie UEFI caricherà il file di configurazione e determinerà che SEMM non è abilitato nel dispositivo. La superficie UEFI inizierà quindi il processo di registrazione di SEMM, come indicato di seguito:
   * La superficie UEFI verificherà che il file di configurazione di SEMM contenga un certificato SEMM.
   * La superficie UEFI chiederà di immettere gli ultimi due caratteri dell'identificazione personale del certificato per confermare la registrazione del dispositivo Surface in SEMM, come illustrato nella figura 8.

      ![L'iscrizione a SEMM richiede ultimi due caratteri di identificazione personale del certificato](images/surface-semm-enroll-fig8.png "SEMM enrollment requires last two characters of certificate thumbprint")

      *Figura 8. L'iscrizione in SEMM richiede gli ultimi due caratteri dell'identificazione personale del certificato*

   * La superficie UEFI memorizzerà il certificato SEMM nel firmware e applica le impostazioni di configurazione specificate nel file di configurazione di Surface UEFI.
   
5. Il dispositivo Surface è ora registrato in SEMM e verrà avviato in Windows.

Puoi verificare che un dispositivo Surface sia stato registrato correttamente in SEMM cercando il pacchetto di configurazione della **superficie Microsoft** in **programmi e funzionalità** (come illustrato nella figura 9) o negli eventi archiviati nel registro **Microsoft Surface UEFI Configurator** , disponibile in **registri applicazioni e servizi** nel Visualizzatore eventi (come illustrato nella figura 10).

![Verificare la registrazione del dispositivo Surface in SEMM in programmi e funzionalità](images/surface-semm-enroll-fig9.png "Verify enrollment of Surface device in SEMM in Programs and Features")

*Figura 9. Verificare la registrazione di un dispositivo Surface in SEMM in programmi e funzionalità*

![Verificare la registrazione del dispositivo Surface in SEMM nel Visualizzatore eventi](images/surface-semm-enroll-fig10.png "Verify enrollment of Surface device in SEMM in Event Viewer")

*Figura 10. Verificare la registrazione di un dispositivo Surface in SEMM nel Visualizzatore eventi*

Puoi anche verificare che il dispositivo sia registrato in SEMM in Surface UEFI-mentre il dispositivo è registrato, Surface UEFI conterrà la pagina **gestione aziendale** (come illustrato nella figura 11).

![Pagina di gestione aziendale UEFI di Surface](images/surface-semm-enroll-fig11.png "Surface UEFI Enterprise management page")

*Figura 11. Pagina di gestione aziendale UEFI di Surface*


## Configurare le impostazioni di Surface UEFI con SEMM

Dopo l'iscrizione di un dispositivo in SEMM, è possibile eseguire i pacchetti di configurazione UEFI di Surface firmati con lo stesso certificato SEMM per applicare le nuove impostazioni di Surface UEFI. Queste impostazioni vengono applicate automaticamente al successivo avvio del dispositivo, senza alcuna interazione da parte dell'utente. Puoi usare le soluzioni di distribuzione delle applicazioni come Microsoft endpoint Configuration Manager per distribuire pacchetti di configurazione UEFI di Surface in dispositivi Surface per modificare o gestire le impostazioni in UEFI di Surface.

Per altre informazioni su come distribuire file di Windows Installer (con estensione msi) con Configuration Manager, vedere [distribuire e gestire applicazioni con Microsoft endpoint Configuration Manager](https://technet.microsoft.com/library/mt627959).

Se è stata garantita una password per la superficie UEFI, gli utenti che non hanno la password che tenti di eseguire l'avvio di Surface UEFI avranno solo le **informazioni sul PC**, **su**, **gestione aziendale**e le pagine di **uscita** visualizzate.

Se non si dispone di un UEFI di Surface protetto con una password o un utente immette correttamente la password, le impostazioni configurate con SEMM verranno visualizzate in grigio (non disponibile) e il testo che alcune impostazioni vengono gestite dall'organizzazione verrà visualizzato nella parte superiore della pagina, come illustrato nella figura 12.

![Impostazioni gestite da SEMM disabilitato in Surface UEFI](images/surface-semm-enroll-fig12.png "Settings managed by SEMM disabled in Surface UEFI")

*Figura 12. Le impostazioni gestite da SEMM verranno disabilitate in UEFI di Surface*

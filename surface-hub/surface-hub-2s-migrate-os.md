---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: Come eseguire la migrazione da Windows 10 Team in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: Surface Hub Desktop, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 472dc41bd73ace90cccdeb4e52884401c2f9d6d7
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11613855"
---
# <a name="migrate-to-windows-10-pro-or-enterprise-on-surface-hub-2"></a>Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2

- [Cronologia delle versioni degli articoli](#version-history)

Surface Hub 2S viene fornito con Windows 10 Team installato. Questa edizione personalizzata di Windows 10 facilita la collaborazione in ambienti di sale riunioni. Ora puoi invece eseguire Windows 10 Pro o Enterprise per usare il Surface Hub 2S in modo molto simile a qualsiasi altro PC.

> [!IMPORTANT]
> Questo processo di migrazione richiede di seguire la procedura specifica descritta in questo articolo. Prima di continuare, leggere [Componenti della soluzione e](#solution-components) Flusso di lavoro di migrazione e [installazione.](#migration-and-installation-workflow-summary)

> [!NOTE]
> Quando installi Windows 10 Pro o Enterprise in Surface Hub 2S, devi disporre di una nuova licenza distinta dalla licenza Windows 10 Team esistente fornita con il dispositivo.

Avvia la migrazione da Windows 10 Team usando un PC separato e lo strumento *di configurazione UEFI di Surface* scaricabile. Lo strumento crea un pacchetto contenente una nuova impostazione UEFI che si applica al Surface Hub 2S.  

Surface UEFI Configurator funziona come interfaccia in Surface Enterprise Management Mode (SEMM). Consente la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni, vedi Modalità di [gestione di Microsoft Surface Enterprise.](/surface/surface-enterprise-management-mode)
 
## <a name="solution-components"></a>Componenti della soluzione

- Surface Hub dispositivo 2S che esegue Windows 10 Team
- Dispositivo separato che esegue Windows 10
- Strumento surface UEFI Configurator per creare il pacchetto SEMM
- Windows 10 Pro o Enterprise OS, versione 1903 o successiva
- Due unità USB con 16 GB di spazio di archiviazione, formato FAT32
- I driver e il firmware per Windows 10 Pro e Enterprise in un file Surface Hub 2 di Microsoft Windows Installer (MSI)
- Connessione Internet
- Soluzione di creazione di immagini (facoltativa)
 
## <a name="migration-and-installation-workflow-summary"></a>Riepilogo del flusso di lavoro di migrazione e installazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare la versione UEFI nel Surface Hub 2S.](#verify-the-uefi-version-on-surface-hub-2s)                                  | La versione UEFI deve essere *la versione 694.2938.768.0* o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Scarica Surface UEFI Configurator e il Surface Hub 2 driver e firmware.](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Nella pagina **[Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703)** seleziona </a> **Download.** Seleziona e scarica il **file MSI del configuratore UEFI**di Surface e installalo in un PC separato. Scarica anche i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo in [Surface Hub 2 file MSI.](https://www.microsoft.com/download/details.aspx?id=101974)</a> Salvare il pacchetto per l'utilizzo nel passaggio 5. |
| 3 | [Preparare il certificato SEMM.](#prepare-the-semm-certificate)                                                                          | Preparare il certificato necessario per eseguire Surface UEFI Configurator o usare il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM.](#create-a-semm-package)                                                                               | Avvia Surface UEFI Configurator per creare un pacchetto SEMM in un'unità USB. Questo pacchetto conterrà i file di configurazione da applicare Surface Hub 2S. Copia questi file del pacchetto SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Caricare un'unità flash USB con Windows 10 immagine, il pacchetto SEMM e driver e firmware.](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Crea un'unità USB che contiene un'Windows 10 immagine. In questo esempio l'unità è denominata *BOOTME.* Aggiungere i driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise su Surface Hub 2 (dal passaggio 2) e i file del pacchetto SEMM (dal passaggio 4) all'unità *BOOTME.*                                                                                                                                                                                                  |
| 6 | [Aggiornare UEFI nel Surface Hub 2S per abilitare la migrazione del sistema operativo.](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usa *l'unità BOOTME* per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise.](#install-windows-10-pro-or-enterprise)                                        | Utilizzare *l'unità BOOTME* per installare Windows 10 Pro o Enterprise versione 1903 o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise.](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarti che il dispositivo abbia tutti gli aggiornamenti e i driver più recenti, installa i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> in Surface Hub 2 file MSI.</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Configurare Surface Hub 2S come dispositivo di produttività personale.](#configure-recommended-settings)                                        |  Abilita le impostazioni e le applicazioni consigliate per ottimizzare Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### <a name="verify-the-uefi-version-on-surface-hub-2s"></a>Verificare la versione UEFI in Surface Hub 2S

Prima di eseguire la Surface Hub da Windows 10 Team a Windows 10 Desktop, è necessario UEFI *versione 694.2938.768.0* o successiva.
 
**Per verificare la versione UEFI nel sistema:**

1. Nella home page Surface Hub 2S seleziona **Start**e quindi apri l'app Surface (**Tutte le app**  >  **Surface).**

2. Seleziona **Surface per** visualizzare le informazioni Surface Hub, inclusa la versione UEFI corrente nel dispositivo. 
   - Se la versione UEFI è *694.2938.768.0* o successiva, come illustrato nell'immagine seguente, è possibile creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

       ![Screenshot shows the "Your Surface" page in the Surface app.](images/shm-fig1.png)
 
   - Se la versione UEFI è precedente alla *versione 694.2938.768.0,* utilizzare uno dei metodi seguenti per ottenere una versione più recente
   
#### <a name="update-uefi-via-windows-update"></a>Aggiornare UEFI tramite Windows update

1. Nel Surface Hub 2S, accedere come **amministratore**.

    >[!Note]
    > Se non conosci il nome utente o la password di amministratore, dovrai reimpostare il dispositivo. Per ulteriori informazioni, vedere [Reset and recovery for Surface Hub 2S.](/surface-hub/surface-hub-2s-recover-reset)

1. Vai a **Tutte le app**  >  **Impostazioni**  >  **Update e Security Windows**  >  **Update**e installa tutti gli aggiornamenti.
1. Riavvia il dispositivo.
1. Verifica la versione UEFI usando l'app Surface. Se la versione UEFI non è *la versione 694.2938.768.0* o successiva, ripetere questi passaggi oppure eseguire la procedura seguente per ottenere la versione UEFI più recente.

#### <a name="update-the-uefi-via-bare-metal-recovery-bmr-image"></a>Aggiornare l'immagine UEFI tramite ripristino bare metal (BMR)

1.  Vai al sito [di ripristino di Surface](https://support.microsoft.com/surfacerecoveryimage) e seleziona Surface Hub **2S**.
3.  Immetti il numero di serie dell'hub. Si trova sul retro dell'hub accanto alla connessione di alimentazione.
4.  Segui le istruzioni per scaricare l'immagine in un'unità USB formattata installando l'Windows 10 Team 2020 Update.
5.  Dopo l'aggiornamento, il dispositivo immette la configurazione guidata. Non è necessario completare l'installazione. La versione UEFI è già aggiornata. In alternativa, spegnere il dispositivo tenendo premuto il pulsante di alimentazione fino a quando lo schermo non si spegne.

### <a name="download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware"></a>Scaricare Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato, segui questi passaggi:

1. Nella pagina <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Surface Tools for IT seleziona </a> **Download.**  
1. Seleziona e scarica il file MSI del configuratore UEFI di Surface e installalo in un PC separato. Lo strumento Configuratore UEFI di Surface non può essere eseguito su un Surface Hub 2S mentre è Windows 10 Team'edizione.

1. Scaricare i [driver Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974)e il firmware Windows file MSI del programma di installazione. Questo file verrà utilizzato quando si installa il nuovo sistema operativo.

### <a name="prepare-the-semm-certificate"></a>Preparare il certificato SEMM

Se non hai usato surface UEFI Configurator prima, devi preparare un certificato. Questo certificato garantisce che dopo la registrazione di un dispositivo in SEMM, puoi modificare le impostazioni UEFI solo usando pacchetti creati con il certificato approvato.

La modalità di ottenere un certificato dipende dalle dimensioni o dalla complessità dell'organizzazione:

- Enterprise le organizzazioni mantengono in genere la propria infrastruttura per generare certificati in base alle procedure di sicurezza standard.

- Le aziende di medie dimensioni e altri spesso scelgono di ottenere certificati dai provider di partner. Questa opzione è consigliata per le organizzazioni che non dispongono di competenze IT o che non dispongono di un team dedicato alla sicurezza IT.

- In alternativa, è possibile generare un certificato autofirmato utilizzando uno script di PowerShell. Per altre informazioni, vedi i requisiti [dei certificati per la modalità di gestione di Surface Enterprise](/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements). Oppure puoi usare PowerShell per creare un certificato personalizzato. Per ulteriori informazioni, vedere la [documentazione relativa ai certificati autofirmati.](/dotnet/core/additional-tools/self-signed-certificates-guide#create-a-self-signed-certificate)

Il pacchetto SEMM creato da Surface UEFI Configurator deve essere protetto con un certificato. Il certificato verifica la firma dei file di configurazione prima di poter applicare le impostazioni UEFI. Per ulteriori informazioni, vedere la [documentazione SEMM.](/surface/surface-enterprise-management-mode)
 
### <a name="create-a-semm-package"></a>Creare un pacchetto SEMM

1. In un PC separato, installa lo strumento Configuratore UEFI di Surface che hai scaricato in precedenza.

1. Apri Surface UEFI Configurator e quindi seleziona **Start.**

   ![Schermata iniziale di Surface UEFI Configurator.](images/shm-fig2.png)
   
1. Seleziona **Dispositivi Surface**e quindi seleziona **Avanti.**

   ![Screenshot shows the Surface Devices option selected.](images/shm-fig3.png)
  
1. Selezionare **Pacchetto di configurazione**.

   ![Screenshot shows "Select Configuration Package" selected.](images/shm-fig4.png)
  
1. Selezionare **Protezione certificato**.

   ![Screenshot shows were to choose "Select Certificate Protection".](images/shm-fig5.png)

   Verrà richiesto di aggiungere il file PFX del certificato.

   ![Screenshot shows where to add your certificate file.](images/shm-fig6.png)
   
1. Immetti la password del certificato e quindi seleziona **OK.**

   ![Screenshot shows fields to enter and confirm your certificate password.](images/shm-fig7.png)

1. Seleziona **Password di protezione** per aggiungere una password a Surface UEFI. Questa password è necessaria ogni volta che si avvia UEFI. *È consigliabile impostare una password UEFI che verrà utilizzata in Surface Hub 2S.*

   ![Screenshot shows where to select Password Protection.](images/shm-fig8.png)
   
1. Impostare una password UEFI e quindi selezionare **OK.**

   > [!IMPORTANT]
   > Salvare la password in un percorso sicuro accessibile agli amministratori IT che gestiscono Surface Hub. *Se la password viene persa, non può essere recuperata.*

   ![Screenshot shows where you set the UEFI password.](images/shm-fig9.png)

1. Selezionare **Surface Hub 2S**e quindi selezionare **Avanti.**

    ![Screenshot shows where to select Surface Hub 2S.](images/shm-fig10.png)
   
1. Selezionare **di nuovo** Avanti.

    ![Screenshot shows to select Next under "Choose which components".](images/shm-fig10a.png)

1. Per consentire l'Windows 10 Pro o Enterprise, attivare **EnableOsMigration**e quindi selezionare **Avanti.**

    ![Screenshot shows where to select Enable O S Migration.](images/shm-fig11.png)
    
    ![Screenshot shows where to set Enable OS Migration to on.](images/shm-fig12.png)

### <a name="manage-semm-enrollment"></a>Gestire la registrazione SEMM

La registrazione di un dispositivo in SEMM influisce su come puoi gestirlo. Ad esempio, dopo aver applicato un pacchetto SEMM, tutte le impostazioni UEFI non sono disponibili (bloccate) nel menu UEFI del dispositivo. Anche i valori predefiniti per altre impostazioni, ad esempio **IPv6 per l'avvio PXE,** non sono disponibili.

Per modificare le impostazioni UEFI al termine della migrazione, applica un altro pacchetto SEMM o annulla la registrazione del dispositivo da SEMM. Se applichino un altro pacchetto SEMM per modificare le impostazioni UEFI, devi usare il certificato originale durante la compilazione del nuovo pacchetto SEMM. Usa lo strumento configuratore UEFI e lascia **disattivato EnableOSMigration** *(non* *attivato* come nei passaggi di migrazione originali).

#### <a name="if-you-work-with-partners"></a>Se si collabora con i partner

Se l'azienda esternalizza la migrazione di Surface Hub 2 a Windows 10 Pro o Enterprise, è possibile che il partner trasferisca all'utente il certificato SEMM, il pacchetto SEMM e la password UEFI. In caso contrario, dopo aver eseguito la migrazione dell'hub, puoi annullare immediatamente la registrazione da SEMM. Questo passaggio consente l'amministrazione locale di UEFI e il trasferimento del dispositivo a un'altra parte. È comunque consigliabile usare una password UEFI, che può essere configurata dopo la migrazione. Per altre informazioni, vedi [Gestire le impostazioni UEFI di Surface.](/surface/manage-surface-uefi-settings) 

#### <a name="to-roll-back-to-windows-10-team"></a>Per eseguire il rollback a Windows 10 Team

Se si sceglie di ripristinare l'Windows 10 Team dopo la migrazione, come descritto più avanti [in questo](#to-roll-back-to-windows-10-team)articolo, è consigliabile annullare la registrazione dell'hub da SEMM. Per altre informazioni, vedi [Annullare la registrazione dei dispositivi Surface da SEMM.](/surface/unenroll-surface-devices-from-semm)

#### <a name="save-the-semm-package-to-a-usb-drive"></a>Salvare il pacchetto SEMM in un'unità USB

1. Connessione un'unità USB al PC.
1. Scegli **Hub 2S**e quindi seleziona **Avanti.**

   ![Screenshot shows where to select Hub 2S](images/shm-fig13.png)

   > [!WARNING]
   > Tutti i dati esistenti nell'unità USB verranno cancellati quando viene creato il pacchetto SEMM. Prima di creare il pacchetto SEMM, rimuovi tutti i file necessari dall'unità USB.
   
1. Selezionare **Compila**.

   ![Screenshot shows where to select Build.](images/shm-fig14.png)

1. Acquisire uno screenshot di questa pagina e quindi selezionare **Fine.** Il pacchetto SEMM è pronto. Contiene il pacchetto SEMM *DfciUpdate.dfi* e un file di testo che include l'identificazione personale *SEMM,* ovvero gli ultimi due caratteri dell'identificazione personale del certificato.

   ![Screenshot shows where to select End.](images/shm-fig15.png)
   
4. Salvare gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri ti servono per attivare SEMM quando applichino il pacchetto Surface Hub 2S.

### <a name="load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware"></a>Caricare un'unità flash USB con un'immagine Windows 10, un pacchetto SEMM e Surface Hub 2 driver e firmware

È possibile installare un'Windows 10 Pro o Enterprise immagine *(versione 1903* o successiva) utilizzando una delle opzioni seguenti:

- La soluzione di creazione di immagini corrente.

- [Surface Deployment Accelerator](/surface/microsoft-surface-deployment-accelerator). Usa questo strumento per creare un'immagine Windows 10 di avvio. L'immagine può includere tutti gli aggiornamenti Windows 10, Microsoft Office, altre app e i driver e il firmware necessari.

- Unità flash USB che contiene un'Windows 10 Pro o Enterprise immagine. Questa opzione non sarà disponibile Wi-Fi dopo l'installazione della Configurazione guidata. Al termine dell'installazione, installa i driver [Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974) e il firmware necessari per Windows 10 Pro e Enterprise nel dispositivo.
 
La procedura seguente mostra come creare un'unità flash USB dal supporto di installazione e quindi aggiungere i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise in un file MSI Surface Hub 2. Se si utilizza un altro metodo di distribuzione, passare alla sezione Aggiornamento UEFI in [Surface Hub 2S](#update-uefi-on-surface-hub-2s-to-enable-os-migration) per abilitare la migrazione del sistema operativo di questo articolo.

> [!NOTE]
> Al termine dell'installazione, è necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise separata dalla licenza Windows 10 Team esistente.

1. Per creare un'Windows 10 Pro, seguire le istruzioni per scaricare lo strumento di creazione dei supporti in [Download Windows 10](https://www.microsoft.com/software-download/windows10). Per scaricare Windows 10 Enterprise, passare al [Centro servizi per contratti multilicenza Microsoft.](https://www.microsoft.com/licensing/servicecenter/default.aspx)

1. Inserire una nuova unità di archiviazione USB.
1. Apri lo strumento di creazione dei supporti, seleziona **Crea supporto di installazione**e quindi seleziona **Avanti.**

   ![Screenshot shows the option to create installation media.](images/shm-fig16.png)
   
3. Selezionare una lingua e quindi **selezionare** Windows 10 a **64 bit (x64).** Quindi selezionare **Avanti**.

   ![Screenshot shows where you select the language, O S edition, and architecture type.](images/shm-fig17.png)
   
4. Seleziona **Unità flash USB**e quindi seleziona **Avanti.**

   ![Screenshot shows where to select U S B flash drive.](images/shm-fig18.png)
   
5. Al termine del download, selezionare **Fine.**

   ![Lo schermo segnala che l'unità U S B è pronta e include un pulsante Fine.](images/shm-fig19.png)
   
6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise in Surface Hub 2 (file MSI) nella radice dell'unità flash USB (*BOOTME*) che contiene l'immagine Windows 10. L'unità USB BOOTME conterrà:

    - Immagine Windows 10 di avvio.
    
    - I file del pacchetto SEMM, copiati nella radice dell'unità USB:
    
      - *DfciUpdate.dfi*.
      - File di testo che include l'identificazione personale SEMM. In questo esempio il file è *SurfaceUEFI_2020Aug25_1058.txt*.) L'indicatore di data e ora generato automaticamente corrisponde alla data in cui hai creato il file usando Surface UEFI Configurator.

   - Driver e firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi). Copia questo file nella radice dell'unità USB.

### <a name="update-uefi-on-surface-hub-2s-to-enable-os-migration"></a>Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

1. Inserire l'unità BOOTME nella porta USB-A nel Surface Hub 2S. Per un elenco dei contenuti necessari, vedere la sezione precedente.

1. Per eseguire l'avvio in UEFI:

   1. Disattiva (arresta) il Surface Hub 2S.
   1. Tieni premuto **Volume +** e quindi premi e rilascia il pulsante di alimentazione. Tieni premuto **Volume +** fino a quando non viene visualizzato il menu UEFI.
   
      ![Disegno mostra il volume e i pulsanti di alimentazione.](images/shm-fig20.png)
      
3. Al riavvio del dispositivo, immetti la password UEFI creata in precedenza, se applicabile (scelta consigliata).

   ![Schermata password di sistema.](images/shm-fig22.png)
   
4. Scegliere Gestione dal menu **** UEFI. Quindi seleziona  **Installa da USB**.

   ![Screenshot shows where to select Management and then "Install from U S B".](images/shm-fig21.png)
   
5. Seleziona **Riavvia ora**, come illustrato nell'immagine seguente. Il dispositivo viene ora riavviato. Verrà visualizzato un logo Microsoft bianco al centro della finestra e quindi arrestato.

   ![Screenshot shows a message prompting you to restart.](images/shm-fig25.png)
   
6. Premere e rilasciare il pulsante di alimentazione. Nella finestra di dialogo rossa visualizzata scegli di attivare la modalità di gestione Enterprise Surface.

7. Immetti l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI. Quindi selezionare **OK**.

   ![Screenshot shows the confirm-activation dialog box where you enter your two-character certificate thumbprint and your UEFI settings password.](images/shm-fig23.png)
 
   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione **UEFI EnableOSMigration.** Non è più possibile accedere Windows 10 Team. È invece necessario continuare con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise.

   Il dispositivo viene riavviato. Visualizza il logo bianco al centro dello schermo e quindi si arresta di nuovo.

### <a name="install-windows-10-pro-or-enterprise"></a>Installare Windows 10 Pro o Enterprise

1. Se l'unità Windows 10 Pro o Enterprise di avvio non è già presente nella porta USB-A Surface Hub 2, inserirla ora. Quindi premere e rilasciare il pulsante di alimentazione.

    All'avvio del dispositivo, vedrai il logo bianco al centro dello schermo. Quindi viene visualizzato un cerchio rotante sotto il logo bianco.

3. Se il dispositivo Surface non si avvia automaticamente nell'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e quindi collegarlo di nuovo). Dopo aver collegato di nuovo il cavo di alimentazione, il dispositivo dovrebbe avviarsi dopo alcuni secondi. Vedrai quindi il logo bianco al centro dello schermo.

    Se il dispositivo non si accende, premi e rilascia il pulsante di alimentazione. Subito dopo aver visualizzato il logo al centro dello schermo, tieni premuto il pulsante Volume verso il basso finché non vedi il cerchio rotante sotto il logo bianco.
 
   ![Immagine dei pulsanti di alimentazione e volume.](images/shm-fig26.png)
   
4. Quando viene avviata la configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).

### <a name="install-surface-hub-2-drivers-and-firmware"></a>Installare Surface Hub 2 driver e firmware

Per assicurarsi che il Surface Hub 2 sia aggiornato, installare driver e firmware per Windows 10 Pro [e Enterprise](https://www.microsoft.com/download/details.aspx?id=101974). Quindi riavvia il dispositivo. Mantieni Surface attivato per un'ora e quindi riavvialo di nuovo. Non verrà richiesto il secondo riavvio. Questa pausa e riavvio aggiuntivo garantisce che il firmware sia stato completamente aggiornato.
 
## <a name="configure-recommended-settings"></a>Configurare le impostazioni consigliate

Per configurare Surface Hub 2S come dispositivo di produttività personale, vedere [Configure Windows 10 Pro or Enterprise on Surface Hub 2](surface-hub-2-post-install.md).

> [!NOTE]
>Se non riesci a eseguire correttamente la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2 seguendo la procedura descritta in questo articolo, contatta il [supporto Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

## <a name="to-roll-back-to-windows-10-team"></a>Per eseguire il rollback a Windows 10 Team

Se vuoi ripristinare il dispositivo in Windows 10 Team, vedi Reimpostazione e ripristino [per Surface Hub 2S.](surface-hub-2s-recover-reset.md)

> [!NOTE]
> Prima di eseguire il rollback a Windows 10 Team, è consigliabile annullare la registrazione della Surface Hub da SEMM. Per altre informazioni, vedi [Annullare la registrazione dei dispositivi Surface da SEMM.](/surface/unenroll-surface-devices-from-semm)

## <a name="version-history"></a>Cronologia versioni

Nella tabella seguente sono riepilogate le modifiche apportate a questo articolo.

| Versione | Data               | Descrizione                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1.4  | 14 dicembre 2020 | Fornisce [](#install-surface-hub-2-drivers-and-firmware) ulteriori informazioni sull'installazione del file MSI per "Driver e firmware per il sistema operativo Windows 10 Pro e Enterprise in Surface Hub 2", consigliando che potrebbe essere necessario un secondo riavvio a seconda dello stato del sistema.                                                          |
| v. 1.3  | 3 dicembre 2020 | Aggiornamento con indicazioni sulla [gestione della registrazione SEMM](#manage-semm-enrollment).                                                       |
| v. 1.2  | 29 settembre 2020 | Aggiornamenti vari che affrontano il feedback sull'usabilità.                                                        |
| v. 1.1  | 15 settembre 2020 | È stata inserita una nota aggiuntiva nell'introduzione che chiarisce i requisiti di licenza per l'installazione di un nuovo sistema operativo. |
| v. 1.0  | 1 settembre 2020  | Nuovo articolo.                                                                                           |

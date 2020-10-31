---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: In questo articolo vengono illustrati i processi di migrazione dal team di Windows 10 in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: Surface Hub desktop, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 12742cc887ba495f8f7cbded8bd84dc4fd63b6f6
ms.sourcegitcommit: 5448f775d3fe177806fce6cbaf0b2b091ed8b7d1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2020
ms.locfileid: "11145971"
---
# Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2

## Introduzione

Surface Hub 2S viene preinstallato con Windows 10 team, un'edizione personalizzata di Windows 10 progettata per facilitare la collaborazione in ambienti sala riunioni. Ora hai la possibilità di usare Windows 10 Pro o Enterprise per utilizzare Surface Hub 2S molto simile a qualsiasi altro PC. 

> [!IMPORTANT]
>A differenza di un tipico aggiornamento o migrazione, questo processo richiede di seguire una procedura prescrittiva, come descritto in questa pagina. Esaminare i [componenti della soluzione](#solution-components) e il [flusso di lavoro di migrazione e installazione](#migration-and-installation-workflow-summary) prima di procedere.


> [!NOTE]
> Quando si installa Windows 10 Pro o Enterprise, è necessario disporre di una nuova licenza separata dalla licenza del team di Windows 10 esistente. 


Si avvia la migrazione da team Windows 10 usando un PC separato e uno strumento scaricabile-- **Surface UEFI Configurator** --per creare un pacchetto contenente una nuova impostazione UEFI applicata a Surface Hub 2S.  Surface UEFI Configurator funge da interfaccia in modalità di gestione di Surface Enterprise (SEMM), progettato per facilitare la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni su SEMM, vedere la [documentazione relativa alla modalità di gestione Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).
 

## Componenti della soluzione

- Dispositivo Surface Hub 2S con sistema operativo Windows 10 team.
- Dispositivo separato con Windows 10.
- Strumento di Configuratore di Surface UEFI per creare il pacchetto SEMM.
- Immagine di Windows 10 Pro o Enterprise OS, versione 1903 o successiva.
- Due unità USB con 16GB di spazio di archiviazione, formato FAT32.
- Driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2, Windows Installer. File MSI.
- Connessione Internet.
- Soluzione di imaging (facoltativo).

 
## Riepilogo del flusso di lavoro di migrazione e installazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | Verificare che la versione UEFI sia **694.2938.768.0** o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Selezionare il pulsante Download nella pagina [strumenti superficie per](https://www.microsoft.com/download/details.aspx?id=46703) la pagina, selezionare e scaricare il **Configuratore di Surface UEFI. File MSI** e installarlo in un PC separato. Scaricare [driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) e salvarlo per l'uso nel passaggio 5. |
| 3 | [Preparare il certificato di SEMM](#prepare-semm-certificate)                                                                          | Preparare il certificato richiesto per l'uso di Surface UEFI Configurator o usare il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM](#create-semm-package)                                                                               | Avviare il configuratore di Surface UEFI per creare un pacchetto SEMM in un'unità USB, che conterrà i file di configurazione necessari per l'applicazione su Surface Hub 2S. Copiare questi file di pacchetto di SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise in Surface Hub 2](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Creare una singola unità USB (denominata **BOOTME** in questo esempio) contenente un'immagine di Windows 10. Aggiungere driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (passaggio 2) e i file di pacchetto di SEMM (passaggio 4) all'unità **BOOTME** .                                                                                                                                                                                                  |
| 6 | [Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usare l'unità **BOOTME** per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise versione 1903 o successiva](#install-windows-10-pro-or-enterprise)                                        | Usare l'unità **BOOTME** per installare **Windows 10 Pro o Enterprise** versione 1903 o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974).                                                                                                                                                                                                                                                                                  |
| 9 | [Configurare completamente Surface Hub 2S come dispositivo di produttività personale](#next-steps)                                        |  Abilitare le impostazioni e le applicazioni consigliate per ottimizzare l'uso di Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi

La versione UEFI minima necessaria prima di eseguire la migrazione di Surface Hub da Windows 10 team a Windows 10 desktop è **694.2938.768.0**.
 
**Per verificare la versione UEFI corrente nel sistema:**

1. Nella schermata iniziale di Surface Hub 2S selezionare **Avvia** e aprire la **SurfaceApp** (**tutte le app**  >  **Surface**).

2. Selezionare la **superficie** per visualizzare le informazioni sul mozzo della superficie, inclusa la versione UEFI corrente nel dispositivo. Se la versione UEFI è **694.2938.768.0** o successiva, come illustrato di seguito, l'UEFI può creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

    ![App Apri superficie & selezionare la superficie](images/shm-fig1.png)
 
3. Se la versione UEFI è precedente alla versione **694.2938.768.0**, sarà necessario ottenere una versione corrente con Windows Update.

**Per aggiornare UEFI da Windows Update:**

1. In Surface Hub 2S, accedere come **amministratore**, accedere a **tutte**le  >  **impostazioni delle**app  >  **aggiornamento e sicurezza**di  >  **Windows Update** e installare tutti gli aggiornamenti, quindi riavviare il dispositivo. Verificare la versione UEFI usando l'app Surface. **Nota:** Se non si conosce il nome utente o la password di amministratore, sarà necessario reimpostare il dispositivo. Per altre informazioni, vedere [reimpostazione e ripristino per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).

2. Ripetere questi passaggi fino a quando la versione UEFI non è **694.2938.768.0** o successiva.

3. Se non si vede ancora l'UEFI aggiornato dopo più tentativi, controllare la **cronologia degli aggiornamenti** e cercare eventuali istanze di installazioni del firmware non riuscite. Potrebbe essere necessario reimpostare il dispositivo (aggiornamento**delle impostazioni**  >  **&**  >  **dispositivo di ripristino**della sicurezza).

### Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato:

- Selezionare il pulsante Download nella [pagina strumenti superficie per la pagina](https://www.microsoft.com/download/details.aspx?id=46703), selezionare e scaricare il configuratore di Surface UEFI. File MSI e installarlo in un PC separato. Lo strumento per il configuratore di Surface UEFI non può essere eseguito su un hub di Surface 2S mentre è installato Windows 10 Team Edition.

- Download [di Surface Hub 2 driver e firmware Windows Installer. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) da applicare durante l'installazione del nuovo sistema operativo.

### Preparare il certificato di SEMM

Se è la prima volta che si usa Surface UEFI Configurator, è necessario preparare un certificato. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, sia possibile usare solo i pacchetti creati con il certificato approvato per modificare le impostazioni UEFI. La modalità di acquisizione di un certificato può variare in base alle dimensioni o alla complessità dell'organizzazione:

- Le organizzazioni aziendali di grandi dimensioni in genere mantengono una propria infrastruttura di certificati per generare certificati per procedure di sicurezza standard.

- Le medie imprese e altre persone possono scegliere di ottenere un certificato da provider di terze parti. Questa è l'opzione consigliata per le organizzazioni senza sufficienti competenze IT o un team di sicurezza IT dedicato.

- In alternativa, è possibile generare un certificato autofirmato con uno script di PowerShell per la documentazione seguente: [requisiti di certificato in modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements). In alternativa, usare PowerShell per creare un certificato personalizzato per la documentazione seguente: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).

Il pacchetto SEMM creato usando lo strumento Surface UEFI Configurator deve essere protetto con un certificato per verificare la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate. Per altre informazioni, vedere la documentazione relativa alla [modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode) .
 
 
### Creare un pacchetto SEMM

1. Installare lo strumento **Surface UEFI Configurator** , come scaricato in precedenza, in un PC separato. 

2. Aprire il **Configuratore di Surface UEFI** e selezionare **Avvia**.

   ![Open Surface UEFI Configurator](images/shm-fig2.png)
   
3. Selezionare **dispositivi Surface** e quindi **Avanti**.

   ![Selezionare i dispositivi Surface](images/shm-fig3.png)
  
4. Selezionare **pacchetto di configurazione**.

   ![Selezionare il pacchetto di configurazione](images/shm-fig4.png)
  
5. Selezionare **protezione certificato**.

   ![Selezionare protezione certificato](images/shm-fig5.png)

6. Verrà richiesto di aggiungere il file con estensione pfx certificato.

   ![Verrà richiesto di aggiungere il certificato](images/shm-fig6.png)
   
7. Immettere la **password del certificato** e scegliere **OK**.

   ![Immettere la password del certificato e scegliere OK](images/shm-fig7.png)

8. Selezionare **password di protezione** per aggiungere una password per Surface UEFI. Questa password sarà necessaria ogni volta che si avvia l'avvio in UEFI. Si **consiglia vivamente** di impostare una password UEFI che si userà su Surface Hub 2S.

   ![Fare clic su password di protezione](images/shm-fig8.png)
   
9. Impostare una **password UEFI** e scegliere **OK**.

   > [!IMPORTANT]
   > Salvare la password in un percorso sicuro accessibile agli amministratori IT dell'organizzazione responsabili della gestione degli hub di Surface. Se la password viene persa, non esiste un processo di ripristino. 

   ![Immettere la password UEFI](images/shm-fig9.png)

10. Selezionare **Surface Hub 2S** , quindi selezionare **Avanti**.

    ![Selezionare Surface Hub 2S](images/shm-fig10.png)
   
11. Seleziona **Avanti**.

    ![Selezionare Avanti](images/shm-fig10a.png)

12. Per consentire l'installazione di Windows 10 Pro o Enterprise, selezionare **EnableOsMigration.**

    ![Selezionare Abilita migrazione del sistema operativo](images/shm-fig11.png)
    
13. Impostare **EnableOSMigration** **su** attivato e selezionare **Avanti**.

    ![Impostare attiva migrazione del sistema operativo su attivato](images/shm-fig12.png)

> [!NOTE]
> Dopo aver applicato un pacchetto SEMM, tutte le impostazioni UEFI verranno visualizzate in grigio (bloccato) nel menu UEFI del dispositivo. Sono inclusi i valori predefiniti per altre impostazioni, ad esempio IPv6 per l'avvio PXE. Per modificare le impostazioni UEFI dopo il completamento della migrazione, è necessario applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM. Se si applica un altro pacchetto di SEMM per modificare le impostazioni UEFI, è necessario usare il certificato originale durante la creazione del nuovo pacchetto SEMM usando lo strumento UEFI Configurator e lasciando "EnableOSMigration" disattivato (e non "attivato", come illustrato nella procedura di migrazione originale).

#### Salvare il pacchetto SEMM in un'unità USB

1. Connettere un'unità USB al PC. Scegliere **Hub 2S** e quindi **Avanti**.

   ![Selezionare USB](images/shm-fig13.png)

> [!WARNING]
> Tutti i dati esistenti nell'unità USB vengono cancellati durante la creazione del pacchetto SEMM. Prima di creare il pacchetto SEMM, rimuovere eventuali file dall'unità USB che si vuole salvare.
   
2. Selezionare **Compila**.

   ![Selezionare Compila](images/shm-fig14.png)

3. Acquisire uno screenshot della pagina e quindi selezionare **fine**. Il pacchetto SEMM è ora pronto e contiene il pacchetto SEMM **DfciUpdate. DFI** e un file di testo con l'identificazione personale di SEMM (gli ultimi due caratteri dell'identificazione personale del certificato).

   ![Seleziona fine](images/shm-fig15.png)
   
4. Salvare gli ultimi 2 caratteri dell'identificazione personale del certificato, necessari per attivare SEMM quando si applica il pacchetto su Surface Hub 2S.

### Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware Surface Hub 2

È possibile installare un'immagine di Windows 10 Pro o Enterprise (versione 1903 o successiva) usando una delle opzioni seguenti:

- Soluzione di imaging corrente.

- [Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) ti consente di creare un'immagine di Windows 10 avviabile che può includere tutti gli aggiornamenti di Windows 10, Office, altre app di tua scelta, nonché i driver e il firmware necessari. 

- Unità flash USB con Windows 10 Pro o Enterprise Image, seguita dall'installazione di  [driver e firmware per Windows 10 Pro e Enterprise OS in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).
 
Questa procedura descrive la creazione di un'unità flash USB dal supporto di installazione e quindi l'aggiunta dei file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2. File MSI. Se si usano altri metodi di distribuzione, passare alla sezione [aggiornare UEFI in Surface Hub 2s per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration).

> [!NOTE]
> Una volta installato, è necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise separata dalla licenza del team di Windows 10 esistente.

1. Per creare un'installazione di Windows 10 Pro, seguire le istruzioni nella pagina [Scarica Windows 10](https://www.microsoft.com/software-download/windows10) per l'uso dello strumento di **creazione di elementi multimediali** . Per scaricare Windows 10 Enterprise, accedere al [centro servizi per contratti multilicenza Microsoft](https://www.microsoft.com/licensing/servicecenter/default.aspx).

2. Inserire una nuova unità di **archiviazione USB** . Avviare lo strumento **creazione multimediale** , selezionare **Crea supporto di installazione** e quindi selezionare **Avanti**.

   ![Creare elementi multimediali di installazione](images/shm-fig16.png)
   
3. Selezionare lingua, Windows 10 e 64 bit (x64), quindi selezionare **Avanti**.

   ![Selezionare lingua, Windows 10 e 64 bit & selezionare Avanti](images/shm-fig17.png)
   
4. Selezionare **USB Flash Drive** e quindi **Avanti**.

   ![Selezionare unità flash USB e selezionare Avanti](images/shm-fig18.png)
   
5. Al termine del download, selezionare **fine**.

   ![Selezionare fine](images/shm-fig19.png)
   
6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS in Surface Hub 2 (. File MSI) nella radice dell'unità flash USB (**BOOTME**) contenente l'immagine di Windows 10. L'unità USB BOOTME contiene:

    - Immagine avviabile di Windows 10.
    
    - File di pacchetto di SEMM (copiati nella radice dell'unità USB)
    
      - DfciUpdate DFI.
      - File di testo con l'identificazione personale di SEMM. In questo esempio: SurfaceUEFI_2020Aug25_1058.txt. Il timestamp della data generato automaticamente corrisponde alla data in cui è stato creato il file usando Surface UEFI Configurator.

   - I driver e il firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi) sono stati copiati anche nella radice dell'unità USB.

### Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

1. Inserire l'unità **BOOTME** nella porta USB-a di Surface Hub 2S. Vedere la sezione precedente per l'elenco dei file necessari.

2. Per eseguire il boot in UEFI:

   1. Spegnere (spegnere) il mozzo della superficie 2S.
   1. Tenere premuto **volume +** e quindi premere e rilasciare il pulsante di **accensione** .
   1. Tenere premuto **volume +** finché non viene visualizzato il menu UEFI.
   
      ![Tenere premuto volume + finché non viene visualizzato il menu UEFI](images/shm-fig20.png)
      
3. Quando il dispositivo viene riavviato, immettere la password UEFI creata in precedenza, se applicabile (fortemente consigliata).

   ![Quando il dispositivo viene riavviato, immettere il proprio UEFI paassword](images/shm-fig22.png)
   
4. Nel menu UEFI selezionare **gestione**  >  **installazione da USB**.

   ![Selezionare Gestione & installazione da USB](images/shm-fig21.png)
   
5. Selezionare **Riavvia ora**, come illustrato di seguito. Il dispositivo riavvia e visualizza il logo quadrato bianco di 4 nel centro dello schermo e quindi si arresta.

   ![Selezionare Riavvia ora](images/shm-fig25.png)
   
6. Premere e rilasciare il pulsante di alimentazione, verrà visualizzata una schermata rossa che richiede di attivare la modalità di gestione di Surface Enterprise. 

7. Immettere l' **identificazione personale del certificato**a due caratteri, la **password delle impostazioni UEFI** e quindi scegliere **OK**.

   ![Immettere l'identificazione personale del certificato di 2 caratteri](images/shm-fig23.png)
 
   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione UEFI **EnableOSMigration** . Non sarà più possibile accedere al team di Windows 10 e procedere con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise. 

8. Il dispositivo verrà riavviato, visualizzerà il logo quadrato bianco di 4 al centro dello schermo, quindi si chiuderà di nuovo.

### Installare Windows 10 Pro o Enterprise

1. Se l'unità di avvio di Windows 10 Pro o Enterprise non è già presente nella porta Surface Hub 2 USB-A, inserirla ora e quindi premere e rilasciare il pulsante di alimentazione.

2. Il dispositivo verrà avviato, si vedrà il quadratino bianco a 4 al centro dello schermo, quindi verrà visualizzato un cerchio di filatura sotto il logo quadrato bianco.

3. Se il dispositivo non si avvia automaticamente sull'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e collegarlo nuovamente). Dopo aver ricollegato il cavo di alimentazione, il dispositivo deve eseguire l'avvio dopo pochi secondi al logo bianco di 4 quadrati al centro dello schermo oppure premere e rilasciare il pulsante di alimentazione per riattivare il dispositivo. Subito dopo aver visualizzato il logo a quattro piazze al centro dello schermo, tenere premuto il pulsante volume giù fino a visualizzare il cerchio di filatura sotto il logo quadrato bianco.
 
   ![Avviare Windows 10 da USB](images/shm-fig26.png)
   
4. Quando viene avviata l'installazione della configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).

### Installare i driver e il firmware di Surface Hub 2

 - Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).
 
### Passaggi successivi

Per configurare completamente Surface Hub 2S come dispositivo di produttività personale, vedere [configurare Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2-post-install.md).

> [!NOTE]
>Se seguire i passaggi descritti in questo documento non riesce a eseguire la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2, contattare il supporto per [Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

### Ripristinare il team di Windows 10

Per ripristinare il dispositivo al team di Windows 10, vedere [reimpostazione e ripristino per Surface Hub 2S](surface-hub-2s-recover-reset.md).

## Cronologia versioni

| Versione | Data               | Descrizione                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1,2  | 29 settembre 2020 | Aggiornamenti vari per feedback sull'usabilità.                                                        |
| v. 1,1  | 15 settembre 2020 | Aggiunta di una nota aggiuntiva nell'introduzione che chiarisce i requisiti di licenza per l'installazione di un nuovo sistema operativo. |
| v. 1.0  | 1 settembre 2020  | Nuovo articolo.                                                                                           |

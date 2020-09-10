---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: In questo articolo vengono illustrati i processi di migrazione dal team di Windows 10 in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 09/08/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e47ee735c0ba1cc0782c892b64d50f7e9d09f355
ms.sourcegitcommit: d24759da42dfe0b913fd9ebf716407a673c2b818
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2020
ms.locfileid: "11004488"
---
# Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2

## Introduzione

Surface Hub 2S viene preinstallato con Windows 10 team, un'edizione personalizzata di Windows 10 progettata per facilitare la collaborazione in ambienti sala riunioni. Ora hai la possibilità di usare Windows 10 Pro o Enterprise per utilizzare Surface Hub 2S molto simile a qualsiasi altro PC. 

> [!IMPORTANT]
>A differenza di un tipico aggiornamento o migrazione, questo processo richiede di seguire una procedura prescrittiva, come descritto in questa pagina. Esaminare i [componenti della soluzione](#solution-components) e il [flusso di lavoro di migrazione](#migration-workflow-summary) prima di procedere.

Si avvia la migrazione da team Windows 10 usando un PC separato e uno strumento scaricabile-- **Surface UEFI Configurator** --per creare un pacchetto contenente una nuova impostazione UEFI applicata a Surface Hub 2S.  Surface UEFI Configurator funge da interfaccia in modalità di gestione di Surface Enterprise (SEMM), progettato per facilitare la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni su SEMM, vedere la [documentazione relativa alla modalità di gestione Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).
 

## Componenti della soluzione

- Dispositivo Surface Hub 2S con sistema operativo Windows 10 team
- Dispositivo separato con Windows 10
- Strumento di configurazione UEFI di Surface
- Immagine di Windows 10 Pro o Enterprise OS, versione 1903 o successiva
- Due unità USB con 16GB di spazio di archiviazione, formato FAT32
- Driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2, Windows Installer. File MSI
- Connessione Internet
- Soluzione di imaging (facoltativo)

 
## Riepilogo del flusso di lavoro di migrazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | Verificare che la versione UEFI sia 694.2938.768.0 o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Scaricare [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) da strumenti Surface per l'installazione e installarlo in un PC separato. Scaricare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) e salvarlo per l'uso nel passaggio 5. |
| 3 | [Preparare il certificato di SEMM](#prepare-semm-certificate)                                                                          | Preparare il certificato richiesto per l'uso di Surface UEFI Configurator o usare il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM](#create-semm-package)                                                                               | Avviare il configuratore di Surface UEFI per creare un pacchetto SEMM su un'unità USB che conterrà i file di configurazione necessari per l'applicazione in Surface Hub 2S. Copiare questi file di pacchetto di SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2](#prepare-usb-flash-drive-containing-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Creare una singola unità USB (denominata **BOOTME** in questo esempio) contenente un'immagine di Windows 10. Aggiungere i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2 (passaggio 2) e i file di pacchetto di SEMM (passaggio 4) all'unità **BOOTME** .                                                                                                                                                                                                  |
| 6 | [Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usare l'unità **BOOTME** per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise versione 1903 o successiva](#install-windows-10-pro-or-enterprise)                                        | Usare l'unità **BOOTME** per installare **Windows 10 Pro o Enterprise** versione 1903 o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI](https://www.microsoft.com/download/details.aspx?id=101974)                                                                                                                                                                                                                                                                                  |
| 9 | [Configurare completamente Surface Hub 2S come dispositivo di produttività personale](#next-steps)                                        |  Abilita il set di impostazioni e applicazioni consigliate per ottimizzare l'uso di Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi

La versione UEFI minima necessaria prima di eseguire la migrazione di Surface Hub da Windows 10 team a Windows 10 desktop è **694.2938.768.0**.
 
**Per verificare la versione UEFI corrente nel sistema:**

1. Nella schermata iniziale di Surface Hub 2S selezionare **Avvia** e aprire la **SurfaceApp** (**tutte le app**  >  **Surface**).

2. Selezionare la **superficie** per visualizzare le informazioni relative al mozzo della superficie, inclusa la versione corrente dell'UEFI nel dispositivo. Se la versione UEFI è **694.2938.768.0** o successiva, come illustrato di seguito, l'UEFI può creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

    ![App Apri superficie & selezionare la superficie](images/shm-fig1.png)
 
3. Se la versione UEFI è precedente alla versione **694.2938.768.0**, sarà necessario ottenere una versione corrente con Windows Update.

**Per aggiornare UEFI da Windows Update:**
1. In Surface Hub 2S, accedere come **amministratore**, accedere a **tutte**le  >  **impostazioni delle**app >  **aggiornamento e sicurezza**di  >  **Windows Update** e installare tutti gli aggiornamenti, quindi riavviare il dispositivo. Verificare la versione UEFI usando l'app Surface. Nota: se non si conosce il nome utente o la password di amministratore, sarà necessario reimpostare il dispositivo. Per altre informazioni, vedere [reimpostazione e ripristino per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).

2. Ripetere questi passaggi fino a quando la versione UEFI non è **694.2938.768.0** o successiva.

3. Se non si vede ancora l'UEFI aggiornato dopo più tentativi, controllare la **cronologia degli aggiornamenti** e cercare eventuali istanze di installazioni del firmware non riuscite. Potrebbe essere necessario reimpostare il dispositivo (aggiornamento**delle impostazioni**  >  **&**  >  **dispositivo di ripristino**della sicurezza).

### Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato:

- Scaricare e installare Microsoft [Surface UEFI Configurator](https://www.microsoft.com/download/details.aspx?id=46703) da strumenti di Surface. Surface UEFI Configurator non può essere eseguito in Surface Hub 2S, mentre è installato Windows 10 team.

- Download [di Surface Hub 2 driver e firmware Windows Installer. File MSI](https://www.microsoft.com/download/details.aspx?id=101974) da applicare durante l'installazione del nuovo sistema operativo.

### Preparare il certificato di SEMM

Se è la prima volta che si usa Surface UEFI Configurator, è necessario preparare un certificato. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, sia possibile usare solo i pacchetti creati con il certificato approvato per modificare le impostazioni UEFI. La modalità di acquisizione di un certificato può variare in base alle dimensioni o alla complessità dell'organizzazione:

- Le organizzazioni aziendali di grandi dimensioni in genere mantengono una propria infrastruttura di certificati per generare certificati per procedure di sicurezza standard.

- Le medie imprese e altre persone possono scegliere di ottenere un certificato da provider di terze parti. Questa è l'opzione consigliata per le organizzazioni senza sufficienti competenze IT o un team di sicurezza IT dedicato.

- In alternativa, è possibile generare un certificato autofirmato con uno script di PowerShell per la documentazione seguente: [requisiti di certificato in modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements). In alternativa, usare PowerShell per creare un certificato personalizzato per la documentazione seguente: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate?view=win10-ps).

Il pacchetto SEMM deve essere protetto con un certificato per verificare la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate. Per altre informazioni, vedere la documentazione relativa alla [modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode) .
 
 
### Creare un pacchetto SEMM

1. Aprire il **Configuratore di Surface UEFI** e selezionare **Avvia**.

   ![Open Surface UEFI Configurator](images/shm-fig2.png)
   
2. Selezionare **dispositivi Surface** e quindi **Avanti**.

   ![Selezionare i dispositivi Surface](images/shm-fig3.png)
  
3. Selezionare **pacchetto di configurazione**.

   ![Selezionare il pacchetto di configurazione](images/shm-fig4.png)
  
4. Selezionare **protezione certificato**.

   ![Selezionare protezione certificato](images/shm-fig5.png)

5. Verrà richiesto di aggiungere il file con estensione pfx certificato.

   ![Verrà richiesto di aggiungere il certificato](images/shm-fig6.png)
   
6. Immettere la **password del certificato** e scegliere **OK**.

   ![Immettere la password del certificato e scegliere OK](images/shm-fig7.png)

7. Selezionare **password di protezione** per aggiungere una password per Surface UEFI. Questa password sarà necessaria ogni volta che si avvia l'avvio in UEFI. Si **consiglia vivamente** di impostare una password UEFI che si userà su Surface Hub 2S.

   ![Fare clic su password di protezione](images/shm-fig8.png)
   
8. Impostare una **password UEFI** e scegliere **OK**.

   ![Immettere la password UEFI](images/shm-fig9.png)

   > [!IMPORTANT]
   > Prendere nota della password. Se si dimentica o si perde la password, non esiste un processo di ripristino. 

9. Selezionare **Surface Hub 2S** , quindi selezionare **Avanti**.

   ![Selezionare Surface Hub 2S](images/shm-fig10.png)
   
10. Seleziona **Avanti**.

    ![Selezionare Avanti](images/shm-fig10a.png)

11. Per consentire l'installazione di Windows 10 Pro o Enterprise, selezionare **EnableOsMigration.**

    ![Selezionare Abilita migrazione del sistema operativo](images/shm-fig11.png)
    
12. Impostare **EnableOSMigration** **su** attivato e selezionare **Avanti**.

    ![Impostare attiva migrazione del sistema operativo su attivato](images/shm-fig12.png)

> [!NOTE]
> Dopo aver applicato un pacchetto SEMM, tutte le impostazioni UEFI verranno visualizzate in grigio (bloccato) nel menu UEFI del dispositivo. Sono inclusi i valori predefiniti per altre impostazioni, ad esempio IPv6 per l'avvio PXE. Per modificare le impostazioni UEFI, dovrai applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM.

#### Salvare il pacchetto SEMM in un'unità USB

1. Connettere un'unità USB al PC. Scegliere **Hub 2S** e quindi **Avanti**.

   ![Selezionare USB](images/shm-fig13.png)
   
2. Selezionare **Compila**.

   ![Selezionare Compila](images/shm-fig14.png)

3. Acquisire uno screenshot della pagina e quindi selezionare **fine**. Il pacchetto SEMM è ora pronto e contiene il pacchetto SEMM **DfciUpdate. DFI** e un file di testo con l'identificazione personale di SEMM (gli ultimi due caratteri dell'identificazione personale del certificato).

   ![Seleziona fine](images/shm-fig15.png)
   
4. Salvare gli ultimi 2 caratteri dell'identificazione personale del certificato, necessari per attivare SEMM quando si applica il pacchetto su Surface Hub 2S.

### Preparare l'unità flash USB contenente l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware Surface Hub 2

È possibile installare un'immagine di Windows 10 Pro o Enterprise (versione 1903 o successiva) usando una delle opzioni seguenti:

- Soluzione di imaging corrente.

- [Surface Deployment Accelerator](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator) ti consente di creare un'immagine di Windows 10 avviabile che può includere tutti gli attuali aggiornamenti di Windows 10, Office, altre app di tua scelta, nonché i driver e il firmware necessari. 

- Unità flash USB con Windows 10 Pro o Enterprise Image, seguita dall'installazione di  [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).
 

Questa procedura descrive la creazione di un'unità flash USB dal supporto di installazione e quindi l'aggiunta dei file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. File MSI. Se si usano altri metodi di distribuzione, passare alla sezione seguente: [aggiornare UEFI in Surface Hub 2s per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration).

> [!NOTE]
> Una volta installato, sarà necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise.

1. Per creare un'installazione di Windows 10 Pro, seguire le istruzioni nella pagina [Scarica Windows 10](https://www.microsoft.com/software-download/windows10) per l'uso dello strumento di **creazione di elementi multimediali** . Per scaricare Windows 10 Enterprise, accedere al [centro servizi per contratti multilicenza Microsoft.](https://www.microsoft.com/licensing/servicecenter/default.aspx)

2. Inserire una nuova unità di **archiviazione USB** . Avviare lo strumento **creazione multimediale** , selezionare **Crea supporto di installazione** e quindi selezionare **Avanti**.

   ![Creare elementi multimediali di installazione](images/shm-fig16.png)
   
3. Selezionare lingua, Windows 10 e 64 bit (x64), quindi selezionare **Avanti**.

   ![Selezionare lingua, Windows 10 e 64 bit & selezionare Avanti](images/shm-fig17.png)
   
4. Selezionare **USB Flash Drive** e quindi **Avanti**.

   ![Selezionare unità flash USB e selezionare Avanti](images/shm-fig18.png)
   
5. Al termine del download, selezionare **fine**.

   ![Selezionare fine](images/shm-fig19.png)
   
6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. MSI per l'unità flash USB (**BOOTME**) che contiene l'immagine di Windows 10:

    - DfciUpdate. DFI
    - File di testo con l'identificazione personale di SEMM. In questo esempio: SurfaceUEFI_2020Aug25_1058.txt)
    - Driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi)

### Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

Usare l'unità **BOOTME** per installare i file di pacchetto di SEMM e aggiornare l'UEFI, abilitando Surface hub per eseguire Windows 10 Pro o Enterprise. Quindi fai il boot dall'unità **BOOTME** per installare Windows 10.

1. Inserire l'unità **BOOTME** contenente i file di pacchetto di SEMM, i driver e il firmware per Windows 10 Pro e Enterprise in Surface Hub 2. MSI e Windows 10 installano i file nella porta USB-A di Surface Hub 2S.  

2. Per eseguire il boot in UEFI:

   1. Spegnere prima di tutto (Shutdown) il mozzo della superficie 2S.
   1. Tenere premuto **volume +** e quindi premere e rilasciare il pulsante di **accensione** .
   1. Tenere premuto **volume +** finché non viene visualizzato il menu UEFI.
   
      ![Tenere premuto volume + finché non viene visualizzato il menu UEFI](images/shm-fig20.png)
      
3. Quando il dispositivo viene riavviato, immettere la password UEFI creata in precedenza, se applicabile (fortemente consigliata).

   ![Quando il dispositivo viene riavviato, immettere il proprio UEFI paassword](images/shm-fig22.png)
   
4. Nel menu UEFI selezionare **gestione**  >  **installazione da USB**.

   ![Selezionare Gestione & installazione da USB](images/shm-fig21.png)
   
5. Selezionare **Riavvia ora**, come illustrato di seguito. Il dispositivo si arresta.

   ![Selezionare Riavvia ora](images/shm-fig25.png)
   
6. Premere e rilasciare il pulsante di alimentazione, verrà visualizzata una schermata rossa che richiede di attivare la modalità di gestione di Surface Enterprise. 

7. Immettere l' **identificazione personale del certificato**a due caratteri, la **password delle impostazioni UEFI** e quindi scegliere **OK**.

   ![Immettere l'identificazione personale del certificato di 2 caratteri](images/shm-fig23.png)
 
   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione UEFI **EnableOSMigration** . Non sarà più possibile accedere al team di Windows 10 e procedere con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise. 

8. Il dispositivo verrà riavviato, visualizzerà il quadrato bianco di 4 al centro dello schermo e quindi di nuovo disattivato.

### Installare Windows 10 Pro o Enterprise

1. Se l'unità di avvio di Windows 10 Pro o Enterprise non è già presente nella porta Surface Hub 2 USB-A, inserirla ora e quindi premere e rilasciare il pulsante di alimentazione.

2. Il dispositivo verrà avviato, si vedrà il quadratino bianco a 4 al centro dello schermo, quindi verrà visualizzato un cerchio di filatura sotto il logo quadrato bianco.

3. Se il dispositivo non si avvia automaticamente sull'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e ricollegarlo), premere e rilasciare il pulsante di alimentazione, quindi tenere premuto il pulsante volume giù finché non viene visualizzato il cerchio di filatura sotto il logo quadrato bianco.
 
   ![Avviare Windows 10 da USB](images/shm-fig26.png)
   
4. Quando viene avviata l'installazione della configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).

### Installare i driver e il firmware di Surface Hub 2

 - Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare [driver e firmware per Windows 10 Pro e Enterprise in Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).
 
### Passaggi successivi

Per configurare completamente Surface Hub 2S come dispositivo di produttività personale, vedere [configurare Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2-post-install.md).

> [!NOTE]
>Se seguire i passaggi descritti in questo documento non riesce a eseguire la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2, contattare il supporto per [Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).


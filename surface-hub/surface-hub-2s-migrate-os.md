---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: Come eseguire la migrazione da team Windows 10 in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: Surface Hub desktop, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/14/2020
ms.localizationpriority: Medium
ms.openlocfilehash: d7ecee2ca66640b054efc106191d12c1844b90a1
ms.sourcegitcommit: 1bc22f7343af9b1b1b8b375d540adee2af68e693
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2021
ms.locfileid: "11297639"
---
# Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2

- [Articolo cronologia versioni](#version-history)

Surface Hub 2S include il team di Windows 10 installato. Questa edizione personalizzata di Windows 10 facilita la collaborazione in ambienti sala riunioni. Ora puoi invece eseguire Windows 10 Pro o Enterprise per usare la tua Surface Hub 2S molto simile a qualsiasi altro PC.

> [!IMPORTANT]
> Questo processo di migrazione richiede di seguire la procedura specifica descritta in questo articolo. Prima di continuare, leggere i [componenti della soluzione](#solution-components) e il [flusso di lavoro di migrazione e installazione](#migration-and-installation-workflow-summary).

> [!NOTE]
> Quando si installa Windows 10 Pro o Enterprise, è necessaria una nuova licenza separata dall'attuale licenza per Windows 10 team.

Avviare la migrazione dal team di Windows 10 usando un PC separato e lo strumento di *configurazione di Surface UEFI* scaricabile. Lo strumento crea un pacchetto che contiene una nuova impostazione UEFI applicata all'hub di Surface 2S.  

Surface UEFI Configurator funziona come interfaccia nella modalità di gestione di Surface Enterprise (SEMM). Consente la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni, vedere [modalità di gestione Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).
 
## Componenti della soluzione

- Dispositivo Surface Hub 2S con il team di Windows 10
- Dispositivo separato con Windows 10
- Strumento di configurazione UEFI di Surface per creare il pacchetto SEMM
- Immagine di Windows 10 Pro o Enterprise OS, versione 1903 o successiva
- Due unità USB con 16 GB di spazio di archiviazione, formato FAT32
- Driver e firmware per Windows 10 Pro e Enterprise in un file di Surface Hub 2 Microsoft Windows Installer (MSI)
- Connessione Internet
- Soluzione di imaging (facoltativo)
 
## Riepilogo del flusso di lavoro di migrazione e installazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare la versione UEFI nella scheda Surface Hub 2S](#verify-the-uefi-version-on-surface-hub-2s).                                  | La versione UEFI deve essere versione *694.2938.768.0* o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Scaricare Surface UEFI Configurator e i driver e il firmware Surface Hub 2.](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Nella pagina **[strumenti superficie per it](https://www.microsoft.com/download/details.aspx?id=46703)** </a> selezionare **Scarica**. Selezionare e scaricare il **file MSI di Surface UEFI Configurator**e installarlo in un PC separato. Scaricare anche i [driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise OS sul file MSI di Surface Hub 2](https://www.microsoft.com/download/details.aspx?id=101974).</a> Salvare il pacchetto da usare nel passaggio 5. |
| 3 | [Preparare il certificato SEMM.](#prepare-the-semm-certificate)                                                                          | Preparare il certificato necessario per eseguire Surface UEFI Configurator oppure usare il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM.](#create-a-semm-package)                                                                               | Avviare la superficie UEFI Configurator per creare un pacchetto SEMM in un'unità USB. Questo pacchetto conterrà i file di configurazione da applicare su Surface Hub 2S. Copiare questi file di pacchetto di SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Caricare un'unità flash USB con l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware.](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Creare un'unità USB che contiene un'immagine di Windows 10. In questo esempio l'unità è denominata *BOOTME*. Aggiungere i driver e il firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (dal passaggio 2) e i file di pacchetto di SEMM (dal passaggio 4) all'unità *BOOTME* .                                                                                                                                                                                                  |
| 6 | [Aggiornare l'UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo.](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usare l'unità *BOOTME* per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise.](#install-windows-10-pro-or-enterprise)                                        | Usare l'unità *BOOTME* per installare Windows 10 Pro o Enterprise versione 1903 o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise.](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare i <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise OS sul file MSI di Surface Hub 2.</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Configura Surface Hub 2S come dispositivo di produttività personale.](#configure-recommended-settings)                                        |  Abilitare le impostazioni e le applicazioni consigliate per ottimizzare Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### Verificare la versione UEFI in Surface Hub 2S

Prima di eseguire la migrazione di Surface Hub dal team Windows 10 al desktop di Windows 10, è necessaria la versione *694.2938.768.0* o successiva di UEFI.
 
**Per verificare la versione UEFI nel sistema:**

1. Nella Home page di Surface Hub 2S selezionare **Start**, quindi aprire l'app Surface (**tutte le app**  >  **Surface**).

2. Selezionare **la superficie** per visualizzare le informazioni su Surface Hub, inclusa la versione UEFI corrente nel dispositivo. 
   - Se la versione UEFI è *694.2938.768.0* o successiva, come illustrato nella figura seguente, è possibile creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

       ![La schermata mostra la pagina "la tua superficie" nell'app Surface.](images/shm-fig1.png)
 
   - Se la versione UEFI è precedente alla versione *694.2938.768.0*, usare uno dei metodi seguenti per ottenere una versione più recente
   
#### Aggiornare UEFI tramite Windows Update

1. Nell'hub di Surface 2S accedere come **amministratore**.

    >[!Note]
    > Se non si conosce il nome utente o la password di amministratore, è necessario reimpostare il dispositivo. Per altre informazioni, vedere [reimpostazione e ripristino per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset).

1. Accedere a **tutte**le  >  **impostazioni delle**app  >  **aggiornamento e sicurezza**di  >  **Windows Update**e installare tutti gli aggiornamenti.
1. Riavvia il dispositivo.
1. Verificare la versione UEFI usando l'app Surface. Se la versione UEFI non è *694.2938.768.0* o versione successiva, ripetere questi passaggi o usare la procedura seguente per ottenere la versione più recente di UEFI.

#### Aggiornare l'UEFI tramite l'immagine di recupero bare metal (BMR)

1.  Accedere al [sito di ripristino della superficie](https://support.microsoft.com/surfacerecoveryimage) e selezionare **Surface Hub 2S**.
3.  Immettere il numero di serie dell'hub. Si trova nella parte posteriore dell'hub accanto alla connessione di alimentazione.
4.  Seguire le indicazioni per scaricare l'immagine su un'unità USB formattata installando l'aggiornamento di Windows 10 team 2020.
5.  Dopo l'aggiornamento, il dispositivo entra nella configurazione della procedura guidata. Non è necessario completare la configurazione. La versione UEFI è già aggiornata. Spegnere invece il dispositivo tenendo premuto il pulsante di alimentazione finché lo schermo non si spegne.

### Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato seguire questa procedura:

1. Nella <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> pagina strumenti superficie per it </a> selezionare **Scarica**.  
1. Selezionare e scaricare il file MSI di Surface UEFI Configurator e installarlo in un PC separato. Lo strumento per il configuratore di Surface UEFI non può essere eseguito su un hub di Surface 2S mentre è installato Windows 10 Team Edition.

1. Scaricare i [driver di Surface Hub 2 e il file MSI del firmware di Windows Installer](https://www.microsoft.com/download/details.aspx?id=101974). Questo file viene usato quando si installa il nuovo sistema operativo.

### Preparare il certificato SEMM

Se non è stato usato un configuratore di Surface UEFI prima, è necessario preparare un certificato. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, è possibile modificare le impostazioni UEFI solo usando i pacchetti creati con il certificato approvato.

La modalità di ottenimento di un certificato dipende dalle dimensioni o dalla complessità dell'organizzazione:

- Le organizzazioni aziendali in genere mantengono la propria infrastruttura per generare certificati in base alle procedure di sicurezza standard.

- Le medie imprese e altre spesso scelgono di ottenere i certificati dai provider partner. Questa opzione è consigliata per le organizzazioni che non hanno più esperienza acquisita o che non dispongono di un team di sicurezza IT dedicato.

- In alternativa, puoi generare un certificato autofirmato usando uno script di PowerShell. Per altre informazioni, vedere Requisiti per i [certificati della modalità di gestione di Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements). In alternativa, puoi usare PowerShell per creare un certificato personalizzato. Per altre informazioni, vedere la documentazione di [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate) .

Il pacchetto SEMM creato da Surface UEFI Configurator deve essere protetto con un certificato. Il certificato verifica la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate. Per altre informazioni, vedi la documentazione di [SEMM](https://docs.microsoft.com/surface/surface-enterprise-management-mode) .
 
### Creare un pacchetto SEMM

1. In un PC separato installare lo strumento per il configuratore di Surface UEFI scaricato in precedenza.

1. Aprire il configuratore UEFI di Surface e quindi selezionare **Avvia**.

   ![Schermata iniziale di Surface UEFI Configurator.](images/shm-fig2.png)
   
1. Selezionare **dispositivi Surface**e quindi **Avanti**.

   ![La schermata mostra l'opzione dispositivi Surface selezionata.](images/shm-fig3.png)
  
1. Selezionare **pacchetto di configurazione**.

   ![La schermata mostra "Seleziona pacchetto di configurazione" selezionata.](images/shm-fig4.png)
  
1. Selezionare **protezione certificato**.

   ![La schermata mostra dove scegliere "seleziona protezione certificato".](images/shm-fig5.png)

   Verrà richiesto di aggiungere il file con estensione pfx certificato.

   ![La schermata mostra dove aggiungere il file di certificato.](images/shm-fig6.png)
   
1. Immettere la password del certificato e quindi fare clic su **OK**.

   ![La schermata mostra i campi per immettere e confermare la password del certificato.](images/shm-fig7.png)

1. Selezionare **password di protezione** per aggiungere una password all'UEFI di Surface. È necessaria questa password ogni volta che si avvia il sistema UEFI. *Ti consigliamo vivamente di impostare una password UEFI che userai su Surface Hub 2S.*

   ![La schermata mostra dove selezionare la protezione con password.](images/shm-fig8.png)
   
1. Impostare una password UEFI e quindi fare clic su **OK**.

   > [!IMPORTANT]
   > Salvare la password in un percorso sicuro accessibile agli amministratori IT che gestiscono Surface Hub. *Se la password viene persa, non può essere recuperata.*

   ![La schermata mostra la posizione in cui è stata impostata la password UEFI.](images/shm-fig9.png)

1. Selezionare **Surface Hub 2S**, quindi fare clic su **Avanti**.

    ![La schermata mostra dove selezionare Surface Hub 2S.](images/shm-fig10.png)
   
1. Selezionare di nuovo **Next** .

    ![La schermata mostra per selezionare avanti in "Scegli i componenti".](images/shm-fig10a.png)

1. Per consentire l'installazione di Windows 10 Pro o Enterprise, attivare **EnableOsMigration**e quindi selezionare **Avanti**.

    ![La schermata mostra dove selezionare Abilita migrazione O S.](images/shm-fig11.png)
    
    ![La schermata mostra la posizione in cui impostare Enable OS Migration su on.](images/shm-fig12.png)

### Gestire l'iscrizione a SEMM

La registrazione di un dispositivo in SEMM influisce sul modo in cui è possibile gestirla. Dopo aver applicato un pacchetto SEMM, ad esempio, tutte le impostazioni UEFI non sono disponibili (bloccate) nel menu UEFI del dispositivo. Anche i valori predefiniti per altre impostazioni, come **IPv6 per l'avvio PXE** , non sono disponibili.

Per modificare le impostazioni di UEFI al termine della migrazione, applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM. Se si applica un altro pacchetto SEMM per modificare le impostazioni UEFI, è necessario usare il certificato originale quando si compila il nuovo pacchetto SEMM. Usare lo strumento UEFI Configurator e uscire da **EnableOSMigration** *(* non *nella procedura* di migrazione originale).

#### Se si collabora con i partner

Se la società esternalizza la migrazione a Surface Hub 2 in Windows 10 Pro o Enterprise, è possibile che il partner trasferisca il certificato SEMM, il pacchetto SEMM e la password UEFI. In alternativa, dopo la migrazione dell'hub, è possibile annullare la registrazione immediata da SEMM. Questo passaggio consente l'amministrazione locale di UEFI e il trasferimento del dispositivo a un'altra parte. Ma ti consigliamo vivamente di usare una password UEFI, che può essere configurata dopo la migrazione. Per altre informazioni, vedere [gestire le impostazioni UEFI di Surface](https://docs.microsoft.com/surface/manage-surface-uefi-settings). 

#### Per eseguire il rollback al team di Windows 10

Se si sceglie di ripristinare il dispositivo al team di Windows 10 dopo la migrazione, [come descritto più avanti in questo articolo](#to-roll-back-to-windows-10-team), è consigliabile prima di tutto annullare la registrazione di hub da SEMM. Per altre informazioni, vedere annullare la [registrazione dei dispositivi Surface da SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).

#### Salvare il pacchetto SEMM in un'unità USB

1. Connettere un'unità USB al PC.
1. Scegliere **Hub 2S**, quindi selezionare **Avanti**.

   ![Screenshot che mostra dove selezionare Hub 2S](images/shm-fig13.png)

   > [!WARNING]
   > Tutti i dati esistenti nell'unità USB verranno cancellati quando viene compilato il pacchetto SEMM. Prima di compilare il pacchetto SEMM, Rimuovi tutti i file necessari dall'unità USB.
   
1. Selezionare **Compila**.

   ![La schermata mostra dove selezionare Build.](images/shm-fig14.png)

1. Acquisire uno screenshot della pagina e quindi selezionare **fine**. Il pacchetto SEMM è ora pronto. Contiene il pacchetto SEMM *DfciUpdate. DFI* e un file di testo che include l' *identificazione digitale*SEMM, ovvero gli ultimi due caratteri dell'identificazione personale del certificato.

   ![La schermata mostra la posizione in cui selezionare fine.](images/shm-fig15.png)
   
4. Salvare gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri possono essere necessari per attivare SEMM quando si applica il pacchetto su Surface Hub 2S.

### Caricare un'unità flash USB con un'immagine di Windows 10, un pacchetto SEMM e un driver e un firmware Surface Hub 2

È possibile installare un'immagine di Windows 10 Pro o Enterprise (versione *1903* o successiva) usando una delle opzioni seguenti:

- Soluzione di imaging corrente.

- [Acceleratore di distribuzione di Surface](https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator). Usare questo strumento per creare un'immagine di Windows 10 avviabile. L'immagine può includere tutti gli aggiornamenti di Windows 10 correnti, Microsoft Office, altre app e i driver e il firmware necessari.

- Un'unità flash USB che contiene un'immagine di Windows 10 Pro o Enterprise. Installare quindi [driver e firmware per Windows 10 Pro e Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) in Surface Hub 2.
 
I passaggi seguenti illustrano come creare un'unità flash USB dal supporto di installazione e quindi aggiungere i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS sul file MSI di Surface Hub 2. Se si usa un altro metodo di distribuzione, fare clic [su Aggiorna UEFI su Surface Hub 2s per abilitare la sezione migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration) di questo articolo.

> [!NOTE]
> Dopo aver completato l'installazione, è necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise separata dalla licenza per il team di Windows 10 esistente.

1. Per creare un'installazione di Windows 10 Pro, seguire le istruzioni per scaricare lo strumento di creazione multimediale in [Scarica Windows 10](https://www.microsoft.com/software-download/windows10). Per scaricare Windows 10 Enterprise, accedere al [centro servizi per contratti multilicenza Microsoft](https://www.microsoft.com/licensing/servicecenter/default.aspx).

1. Inserire una nuova unità di archiviazione USB.
1. Aprire lo strumento creazione multimediale, selezionare **Crea supporto di installazione**e quindi selezionare **Avanti**.

   ![La schermata mostra l'opzione per creare il supporto di installazione.](images/shm-fig16.png)
   
3. Selezionare una lingua, quindi selezionare **Windows 10** e **64 bit (x64)**. Quindi selezionare **Avanti**.

   ![La schermata mostra la posizione in cui si seleziona la lingua, l'edizione O il tipo di architettura.](images/shm-fig17.png)
   
4. Selezionare **unità flash USB**, quindi scegliere **Avanti**.

   ![La schermata mostra la posizione in cui selezionare U S B Flash Drive.](images/shm-fig18.png)
   
5. Al termine del download, selezionare **fine**.

   ![La schermata segnala che l'unità U S B è pronta e include un pulsante fine.](images/shm-fig19.png)
   
6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS in Surface Hub 2 (il file MSI) nella radice dell'unità flash USB (*BOOTME*) che contiene l'immagine di Windows 10. L'unità USB BOOTME conterrà:

    - Immagine avviabile di Windows 10.
    
    - I file di pacchetto di SEMM, copiati nella radice dell'unità USB:
    
      - *DfciUpdate DFI*.
      - Un file di testo che include l'identificazione personale di SEMM. In questo esempio il file è *SurfaceUEFI_2020Aug25_1058.txt*. L'indicatore di data e ora generato automaticamente corrisponde alla data in cui è stato creato il file usando Surface UEFI Configurator.

   - Driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi). Copiare il file nella radice dell'unità USB.

### Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

1. Inserire l'unità BOOTME nella porta USB-A di Surface Hub 2S. Per un elenco dei contenuti necessari, vedere la sezione precedente.

1. Per eseguire il boot in UEFI:

   1. Disattivare (arrestare) il mozzo della superficie 2S.
   1. Tenere premuto **volume +** e quindi premere e rilasciare il pulsante di accensione. Tenere premuto **volume +** finché non viene visualizzato il menu UEFI.
   
      ![Il disegno mostra i pulsanti volume e Power.](images/shm-fig20.png)
      
3. Quando il dispositivo viene riavviato, immettere la password UEFI creata in precedenza, se applicabile (scelta consigliata).

   ![Schermata password di sistema.](images/shm-fig22.png)
   
4. Nel menu UEFI selezionare **gestione**. Quindi seleziona  **Installa da USB**.

   ![La schermata mostra dove selezionare gestione e quindi "Installa da U S B".](images/shm-fig21.png)
   
5. Selezionare **Riavvia ora**, come illustrato nell'immagine seguente. Il dispositivo viene ora riavviato. Visualizzerà un logo Microsoft bianco al centro della finestra e quindi si chiuderà.

   ![Screenshot mostra un messaggio che chiede di riavviare.](images/shm-fig25.png)
   
6. Premere e rilasciare il pulsante di accensione. Nella finestra di dialogo rosso visualizzata scegliere per attivare la modalità di gestione di Surface Enterprise.

7. Immettere l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI. Quindi scegliere **OK**.

   ![La schermata mostra la finestra di dialogo conferma attivazione in cui si immette l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI.](images/shm-fig23.png)
 
   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione di **ENABLEOSMIGRATION** UEFI. Non è più possibile accedere al team di Windows 10. Devi invece continuare con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise.

   Il dispositivo viene riavviato. Visualizza il logo bianco al centro dello schermo e quindi si arresta di nuovo.

### Installare Windows 10 Pro o Enterprise

1. Se l'unità di avvio di Windows 10 Pro o Enterprise non è già presente nella porta Surface Hub 2 USB-A, inserirla ora. Quindi premi e rilascia il pulsante di accensione.

    Quando il dispositivo viene avviato, il logo bianco viene visualizzato al centro dello schermo. Sotto il logo bianco viene visualizzato un cerchio di filatura.

3. Se il dispositivo Surface non si avvia automaticamente sull'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e quindi ricollegarlo). Dopo aver ricollegato il cavo di alimentazione, il dispositivo dovrebbe avviarsi dopo pochi secondi. Verrà visualizzato il logo bianco al centro dello schermo.

    Se il dispositivo non si attiva, premere e rilasciare il pulsante di alimentazione. Subito dopo aver visualizzato il logo al centro dello schermo, tenere premuto il pulsante volume finché non viene visualizzato il cerchio di filatura sotto il logo bianco.
 
   ![Immagine dei pulsanti volume e Power.](images/shm-fig26.png)
   
4. Quando viene avviata l'installazione della configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).

### Installare i driver e il firmware di Surface Hub 2

Per assicurarsi che Surface Hub 2 sia aggiornato, installare [driver e firmware per Windows 10 Pro e Enterprise](https://www.microsoft.com/download/details.aspx?id=101974). Quindi riavvia il dispositivo. Mantieni la superficie attiva per un'ora, quindi riavvia di nuovo. Non verrà richiesto il secondo riavvio. Questa pausa e il riavvio aggiuntivo garantiscono che il firmware sia stato completamente aggiornato.
 
## Configurare le impostazioni consigliate

Per configurare Surface Hub 2S come dispositivo di produttività personale, vedere [configurare Windows 10 Pro o Enterprise in Surface Hub 2](surface-hub-2-post-install.md).

> [!NOTE]
>Se non è possibile eseguire correttamente la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2, seguire i passaggi descritti in questo articolo, contattare il [supporto di Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

## Per eseguire il rollback al team di Windows 10

Per ripristinare il dispositivo in un team di Windows 10, vedere [reimpostazione e ripristino per Surface Hub 2S](surface-hub-2s-recover-reset.md).

> [!NOTE]
> Prima di ripristinare il team di Windows 10, è consigliabile annullare la registrazione di Surface Hub da SEMM. Per altre informazioni, vedere annullare la [registrazione dei dispositivi Surface da SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).

## Cronologia versioni

Nella tabella seguente vengono riepilogate le modifiche apportate a questo articolo.

| Versione | Data               | Descrizione                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1,4  | 14 dicembre 2020 | Fornisce [altre informazioni](#install-surface-hub-2-drivers-and-firmware) su come installare il file MSI per "driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2", in modo che sia necessario un secondo riavvio a seconda dello stato del sistema.                                                          |
| v. 1,3  | 3 dicembre 2020 | Aggiornato con le indicazioni sulla [gestione della registrazione di SEMM](#manage-semm-enrollment).                                                       |
| v. 1,2  | 29 settembre 2020 | Aggiornamenti vari che indirizzano il feedback sull'usabilità.                                                        |
| v. 1,1  | 15 settembre 2020 | È stata inserita una nota aggiuntiva nell'introduzione che chiarisce i requisiti di licenza per l'installazione di un nuovo sistema operativo. |
| v. 1.0  | 1 settembre 2020  | Nuovo articolo.                                                                                           |

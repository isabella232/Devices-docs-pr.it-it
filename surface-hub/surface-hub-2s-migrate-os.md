---
title: Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2
description: Questo articolo descrive come eseguire la migrazione da un team Windows 10 in Surface Hub 2 a Windows 10 Pro o Windows 10 Enterprise.
keywords: Surface Hub desktop, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/03/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 01c5c8a5c6b9f7ed657829fe792fc9eecd1facb5
ms.sourcegitcommit: 5d02cca9ca8c0a252798c2fc0a89dbda81911c44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "11195401"
---
# Eseguire la migrazione a Windows 10 Pro o Enterprise in Surface Hub 2

Surface Hub 2S viene preinstallato con il team di Windows 10. Questa edizione personalizzata di Windows 10 è progettata per facilitare la collaborazione in ambienti sala riunioni. Ora hai la possibilità di usare Windows 10 Pro o Enterprise per utilizzare Surface Hub 2S molto simile a qualsiasi altro PC. 

> [!IMPORTANT]
>A differenza di un tipico aggiornamento o migrazione, questo processo richiede di seguire una procedura prescrittiva, come descritto in questo articolo. Esaminare i [componenti della soluzione](#solution-components) e il [flusso di lavoro di migrazione e installazione](#migration-and-installation-workflow-summary) prima di continuare.


> [!NOTE]
> Quando si installa Windows 10 Pro o Enterprise, è necessaria una nuova licenza separata dall'attuale licenza per Windows 10 team. 


Avviare la migrazione dal team di Windows 10 usando un PC separato e lo strumento scaricabile *Surface UEFI Configurator*. Usare lo strumento per creare un pacchetto che contiene una nuova impostazione UEFI applicata a Surface Hub 2S.  

Surface UEFI Configurator funziona come interfaccia nella modalità di gestione di Surface Enterprise (SEMM). È progettato per facilitare la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni, vedere la <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> documentazione di Microsoft SEMM</a>
 

## Componenti della soluzione

- Dispositivo Surface Hub 2S in cui è installato il sistema operativo Windows 10 team
- Dispositivo separato con Windows 10
- Strumento di configurazione UEFI di Surface per creare il pacchetto SEMM
- Immagine di Windows 10 Pro o Enterprise OS, versione 1903 o successiva
- Due unità USB con 16 GB di spazio di archiviazione, formato FAT32
- Driver e firmware per Windows 10 Pro e il sistema operativo Enterprise OS su Surface Hub 2 Microsoft Windows Installer (MSI)
- Connessione Internet
- Soluzione di imaging (facoltativo)

 
## Riepilogo del flusso di lavoro di migrazione e installazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi.](#verify-uefi-version-on-surface-hub-2s-meets-minimum-requirements)                                  | Verificare che la versione UEFI sia 694.2938.768.0 o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware.](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Nella pagina <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> **strumenti superficie per it** </a> selezionare **Scarica**. Quindi seleziona e Scarica **Surface UEFI Configurator. File MSI** e installarlo in un PC separato. Scaricare i <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise OS sul file MSI di Surface Hub 2.</a> Salvarla per l'uso nel passaggio 5. |
| 3 | [Preparare il certificato SEMM.](#prepare-the-semm-certificate)                                                                          | Preparare il certificato necessario per eseguire Surface UEFI Configurator. Oppure usa il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM.](#create-a-semm-package)                                                                               | Avviare la superficie UEFI Configurator per creare un pacchetto SEMM su un'unità USB, che conterrà i file di configurazione da applicare in Surface Hub 2S. Copiare questi file di pacchetto di SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Preparare l'unità flash USB che contiene l'immagine di Windows 10, il pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2.](#prepare-a-usb-flash-drive-that-contains-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Creare un'unica unità USB che contiene un'immagine di Windows 10. In questo esempio l'unità è denominata *BOOTME*. Aggiungere driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (passaggio 2) e i file di pacchetto di SEMM (passaggio 4) all'unità *BOOTME* .                                                                                                                                                                                                  |
| 6 | [Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo.](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usare l'unità *BOOTME* per avviare Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise versione 1903 o successiva.](#install-windows-10-pro-or-enterprise)                                        | Usare l'unità *BOOTME* per installare Windows 10 Pro o Enterprise versione 1903 o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise OS in Surface Hub 2.](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare i <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver e il firmware per Windows 10 Pro e il sistema operativo Enterprise OS sul file MSI di Surface Hub 2.</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Configurare completamente Surface Hub 2S come dispositivo di produttività personale.](#configure-recommended-settings)                                        |  Abilitare le impostazioni e le applicazioni consigliate per ottimizzare Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### Verificare che la versione UEFI in Surface Hub 2S soddisfi i requisiti minimi

Prima di eseguire la migrazione di Surface Hub dal team Windows 10 al desktop di Windows 10, è necessaria una versione UEFI almeno *694.2938.768.0*.
 
**Per verificare la versione UEFI nel sistema:**

1. Nella Home page di Surface Hub 2S selezionare **Start**, quindi aprire l'app Surface (**tutte le app**  >  **Surface**).

2. Selezionare **la superficie** per visualizzare le informazioni su Surface Hub, inclusa la versione UEFI corrente nel dispositivo. 
   - Se la versione UEFI è *694.2938.768.0* o successiva, come illustrato nella figura seguente, è possibile creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

       ![Screenshot che mostra la pagina della superficie nell'app Surface.](images/shm-fig1.png)
 
   - Se la versione UEFI è antecedente alla versione 694.2938.768.0, è necessario ottenere una versione corrente installando l'immagine di Windows 10 team 2020 Update bare metal Recovery (BMR) o usando l'aggiornamento.
   
**Per aggiornare UEFI tramite Windows Update:**

1. Nell'hub di Surface 2S accedere come **amministratore**. 
    >[!Note]
    > Se non si conosce il nome utente o la password di amministratore, è necessario reimpostare il dispositivo. Per altre informazioni, vedere <a href="https://docs.microsoft.com/surface-hub/surface-hub-2s-recover-reset" target="_blank"> reimpostazione e ripristino per Surface Hub 2S.</a>

1. Accedere a **tutte**le  >  **impostazioni delle**app  >  **aggiornamento e sicurezza**di  >  **Windows Update**e quindi installare tutti gli aggiornamenti. 
1. Riavvia il dispositivo. 
1. Verificare la versione UEFI usando l'app Surface. 
1. A questo punto, se la versione UEFI non è ancora in versione 694.2938.768.0 o successiva, è possibile ripetere i passaggi descritti in precedenza oppure è possibile ottenere l'UEFI più recente installando l'immagine di Windows 10 team 2020 Update bare metal Recovery (BMR).

**Per aggiornare UEFI tramite l'immagine di recupero bare metal (BMR):**

1.  Accedere al [sito di ripristino della superficie](https://support.microsoft.com/surfacerecoveryimage) e selezionare **Surface Hub 2S**
3.  Immettere il numero di serie dell'hub (situato sul lato posteriore dell'hub accanto alla connessione di alimentazione).
4.  Seguire le indicazioni per scaricare l'immagine su un'unità USB formattata con l'installazione dell'aggiornamento di Windows 10 team 2020.
5.  Dopo aver completato l'aggiornamento e il dispositivo immette la configurazione per la prima volta OOBE, non è necessario completare la procedura guidata, verrà aggiornata la versione UEFI. Spegnere invece il dispositivo tenendo premuto il pulsante di alimentazione finché lo schermo non si spegne. 

### Download di Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato:

1. Nella <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> pagina strumenti superficie per it </a> selezionare **Scarica**.  
1. Selezionare e scaricare il file MSI di Surface UEFI Configurator e installarlo in un PC separato. Lo strumento di configurazione UEFI di Surface non può essere eseguito su un hub di Surface 2S mentre è installato Windows 10 Team Edition.

1. Scaricare i <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver di Surface Hub 2 e il file MSI del firmware di Windows Installer </a> . Questo file viene usato quando si installa il nuovo sistema operativo.

### Preparare il certificato SEMM

Se non è stato usato un configuratore di Surface UEFI prima, è necessario preparare un certificato. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, è possibile modificare le impostazioni UEFI solo usando i pacchetti creati con il certificato approvato. 

La modalità di ottenimento di un certificato dipende dalle dimensioni o dalla complessità dell'organizzazione:

- Le organizzazioni aziendali in genere mantengono la propria infrastruttura per generare certificati in base alle procedure di sicurezza standard.

- Le medie imprese e altre possono scegliere di ottenere certificati da provider di partner. Questa opzione è consigliata per le organizzazioni che non dispongono di competenze IT sufficienti o di un team di sicurezza IT dedicato.

- In alternativa, puoi generare un certificato autofirmato usando uno script di PowerShell. Per altre informazioni, vedere Requisiti per i <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements" target="_blank"> certificati della modalità di gestione di Surface Enterprise </a> . In alternativa, puoi usare PowerShell per creare un certificato personalizzato. Per altre informazioni, vedere la <a href="https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate" target="_blank"> documentazione di New-SelfSignedCertificate </a> .

Il pacchetto SEMM creato da Surface UEFI Configurator deve essere protetto con un certificato. Il certificato verifica la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate. Per altre informazioni, vedi la <a href="https://docs.microsoft.com/surface/surface-enterprise-management-mode" target="_blank"> documentazione di SEMM </a> .
 
 
### Creare un pacchetto SEMM

1. In un PC separato installare lo strumento per il configuratore di Surface UEFI scaricato in precedenza. 

2. Aprire il configuratore UEFI di Surface e quindi selezionare **Avvia**.

   ![Aprire il configuratore UEFI Surface.](images/shm-fig2.png)
   
3. Selezionare **dispositivi Surface**e quindi **Avanti**.

   ![Selezionare dispositivi Surface.](images/shm-fig3.png)
  
4. Selezionare **pacchetto di configurazione**.

   ![Selezionare pacchetto di configurazione.](images/shm-fig4.png)
  
5. Selezionare **protezione certificato**.

   ![Selezionare protezione certificato.](images/shm-fig5.png)

   Viene richiesto di aggiungere il file con estensione pfx certificato.

   ![Aggiungere il certificato.](images/shm-fig6.png)
   
7. Immettere la password del certificato e quindi fare clic su **OK**.

   ![Immettere la password del certificato e scegliere OK.](images/shm-fig7.png)

8. Selezionare **password di protezione** per aggiungere una password per Surface UEFI. È necessaria questa password ogni volta che si avvia l'avvio in UEFI. Ti *consigliamo vivamente* di impostare una password UEFI che userai su Surface Hub 2S.

   ![Selezionare password di protezione.](images/shm-fig8.png)
   
9. Impostare una password UEFI e quindi fare clic su **OK**.

   > [!IMPORTANT]
   > Salvare la password in un percorso sicuro accessibile agli amministratori IT che gestiscono Surface Hub. Se la password viene persa, non può essere recuperata. 

   ![Immettere la password UEFI.](images/shm-fig9.png)

10. Selezionare **Surface Hub 2S**, quindi fare clic su **Avanti**.

    ![Selezionare Surface Hub 2S.](images/shm-fig10.png)
   
11. Seleziona **Avanti**.

    ![Seleziona Avanti.](images/shm-fig10a.png)

12. Per consentire l'installazione di Windows 10 Pro o Enterprise, attivare **EnableOsMigration**e quindi selezionare **Avanti**.

    ![Selezionare Abilita migrazione O S.](images/shm-fig11.png)
    
    ![Impostare Enable OS Migration su attivato.](images/shm-fig12.png)

### Gestione della registrazione di SEMM

La registrazione di dispositivi in SEMM influisce su come gestire il dispositivo in futuro. Ad esempio, dopo aver applicato un pacchetto SEMM, nel menu UEFI del dispositivo tutte le impostazioni UEFI non sono disponibili (bloccata). Anche i valori predefiniti per altre impostazioni, come **IPv6 per l'avvio PXE** , non sono disponibili. 

Per modificare le impostazioni di UEFI al termine della migrazione, applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM. Se si applica un altro pacchetto SEMM per modificare le impostazioni UEFI, è necessario usare il certificato originale quando si compila il nuovo pacchetto SEMM. Usare lo strumento UEFI Configurator e uscire da **EnableOSMigration** (non attivato, come illustrato nella procedura di migrazione originale).

#### Uso dei partner

Se la società sta esternalizzando la migrazione a Windows 10 Pro o Enterprise su Surface Hub 2, è possibile che il partner trasferisca il certificato SEMM, il pacchetto SEMM e la password UEFI.  In alternativa, dopo la migrazione dell'hub, puoi immediatamente annullare la registrazione da SEMM, che consentirà l'amministrazione locale di UEFI e il trasferimento del dispositivo a un'altra persona. Tuttavia, è ancora vivamente consigliabile usare una password UEFI, che può essere configurata dopo la migrazione. Per altre informazioni, vedere [gestire le impostazioni UEFI di Surface](https://docs.microsoft.com/surface/manage-surface-uefi-settings). 

#### Ripristinare il team di Windows 10

Se dopo la migrazione si sceglie di ripristinare il dispositivo al team di Windows 10, [come descritto di seguito](#roll-back-to-windows-10-team), è consigliabile annullare la registrazione di hub da SEMM. Per altre informazioni, vedere annullare la [registrazione dei dispositivi Surface da SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).


#### Salvare il pacchetto SEMM in un'unità USB

1. Connettere un'unità USB al PC. 
1. Scegliere **Hub 2S**, quindi selezionare **Avanti**.

   ![Selezionare USB](images/shm-fig13.png)

   > [!WARNING]
   > Tutti i dati esistenti nell'unità USB vengono cancellati quando viene compilato il pacchetto SEMM. Prima di creare il pacchetto SEMM, rimuovere eventuali file dall'unità USB che si vuole salvare.
   
2. Selezionare **Compila**.

   ![Selezionare Compila.](images/shm-fig14.png)

3. Acquisire uno screenshot della pagina e quindi selezionare **fine**. Il pacchetto SEMM è ora pronto. Contiene il pacchetto SEMM *DfciUpdate. DFI* e un file di testo che include l'identificazione digitale SEMM (gli ultimi due caratteri dell'identificazione personale del certificato).

   ![Selezionare fine.](images/shm-fig15.png)
   
4. Salvare gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri possono essere necessari per attivare SEMM quando si applica il pacchetto su Surface Hub 2S.

### Preparare un'unità flash USB che contiene un'immagine di Windows 10, un pacchetto SEMM e i driver e il firmware Surface Hub 2

È possibile installare un'immagine di Windows 10 Pro o Enterprise (versione 1903 o successiva) usando una delle opzioni seguenti:

- Soluzione di imaging corrente.

- <a href="https://docs.microsoft.com/surface/microsoft-surface-deployment-accelerator" target="_blank"> Acceleratore di distribuzione di Surface </a> . Usare questo strumento per creare un'immagine di Windows 10 avviabile. L'immagine può includere tutti gli attuali aggiornamenti di Windows 10, Office, altre app scelte e i driver e il firmware necessari. 

- Unità flash USB che contiene un'immagine di Windows 10 Pro o Enterprise. Installare quindi <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 </a> .
 
La procedura seguente descrive come creare un'unità flash USB dal supporto di installazione e quindi aggiungere i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS sul file MSI di Surface Hub 2. Se si usano altri metodi di distribuzione, vedere l' [aggiornamento UEFI in Surface Hub 2s per abilitare la sezione migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration) in questo articolo.

> [!NOTE]
> Dopo aver completato l'installazione, è necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise separata dalla licenza per il team di Windows 10 esistente.

1. Per creare un'installazione di Windows 10 Pro, nella <a href="https://www.microsoft.com/software-download/windows10" target="_blank"> pagina Scarica Windows 10 </a> seguire le istruzioni per scaricare lo strumento per la creazione di elementi multimediali. Per scaricare Windows 10 Enterprise, accedere al <a href="https://www.microsoft.com/licensing/servicecenter/default.aspx" target="_blank"> centro servizi per contratti multilicenza Microsoft </a> .

2. Inserire una nuova unità di archiviazione USB. 
1. Aprire lo strumento creazione multimediale, selezionare **Crea supporto di installazione**e quindi selezionare **Avanti**.

   ![Creare elementi multimediali di installazione.](images/shm-fig16.png)
   
3. Selezionare una lingua e quindi scegliere **Windows 10** e **64 bit (x64)**. Quindi selezionare **Avanti**.

   ![Selezionare lingua e scegliere Windows 10 e 64 bit. Quindi selezionare Avanti.](images/shm-fig17.png)
   
4. Selezionare **unità flash USB**, quindi scegliere **Avanti**.

   ![Selezionare U S B Flash Drive e selezionare Avanti.](images/shm-fig18.png)
   
5. Al termine del download, selezionare **fine**.

   ![Selezionare fine.](images/shm-fig19.png)
   
6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise OS in Surface Hub 2 (il file MSI) nella radice dell'unità flash USB (*BOOTME*) che contiene l'immagine di Windows 10. L'unità USB BOOTME contiene:

    - Immagine avviabile di Windows 10.
    
    - File di pacchetto di SEMM (copiati nella radice dell'unità USB).
    
      - *DfciUpdate DFI*.
      - File di testo che include l'identificazione personale di SEMM. In questo esempio il file è *SurfaceUEFI_2020Aug25_1058.txt*. L'indicatore di data e ora generato automaticamente corrisponde alla data in cui è stato creato il file usando Surface UEFI Configurator.

   - Driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi). Copiare il file nella radice dell'unità USB.

### Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

1. Inserire l'unità BOOTME nella porta USB-A di Surface Hub 2S. Per un elenco dei file necessari, vedere la sezione precedente.

2. Per eseguire il boot in UEFI:

   1. Disattivare (arrestare) il mozzo della superficie 2S.
   1. Tenere premuto **volume +** e quindi premere e rilasciare il pulsante di accensione.
   1. Tenere premuto **volume +** finché non viene visualizzato il menu UEFI.
   
      ![Premere e tenere premuto il pulsante volume-up finché non viene visualizzato il menu UEFI.](images/shm-fig20.png)
      
3. Quando il dispositivo viene riavviato, immettere la password UEFI creata in precedenza, se applicabile (fortemente consigliata).

   ![Immettere la password UEFI.](images/shm-fig22.png)
   
4. Nel menu UEFI selezionare **gestione**  >  **installazione da USB**.

   ![Selezionare Gestione e installazione da U S B.](images/shm-fig21.png)
   
5. Selezionare **Riavvia ora**, come illustrato nell'immagine seguente. Il dispositivo viene riavviato. Visualizza un logo Microsoft bianco al centro della finestra e quindi si arresta.

   ![Selezionare Riavvia ora.](images/shm-fig25.png)
   
6. Premere e rilasciare il pulsante di accensione. Nella finestra rossa visualizzata attivare la modalità di gestione di Surface Enterprise. 

7. Immettere l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI. Quindi scegliere **OK**.

   ![Immettere l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI.](images/shm-fig23.png)
 
   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione di **ENABLEOSMIGRATION** UEFI. Non sarà più possibile accedere al team di Windows 10. Devi invece continuare con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise. 

   Il dispositivo viene riavviato. Visualizza il logo bianco al centro dello schermo e quindi si arresta di nuovo.

### Installare Windows 10 Pro o Enterprise

1. Se l'unità di avvio di Windows 10 Pro o Enterprise non è già presente nella porta Surface Hub 2 USB-A, inserirla ora. Quindi premi e rilascia il pulsante di accensione. 

    Quando il dispositivo viene avviato, viene visualizzato il logo bianco al centro dello schermo. Viene visualizzato un cerchio di filatura sotto il logo bianco.

3. Se il dispositivo non si avvia automaticamente sull'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e quindi ricollegarlo). Dopo aver ricollegato il cavo di alimentazione, il dispositivo dovrebbe avviarsi dopo pochi secondi. Verrà visualizzato il logo bianco al centro dello schermo. 

    Se il dispositivo non si attiva, premere e rilasciare il pulsante di alimentazione. Subito dopo aver visualizzato il logo al centro dello schermo, tenere premuto il pulsante volume finché non viene visualizzato il cerchio di filatura sotto il logo bianco.
 
   ![Eseguire l'avvio in Windows 10 dall'unità U S B.](images/shm-fig26.png)
   
4. Quando viene avviata l'installazione della configurazione guidata, seguire le istruzioni per installare Windows 10 Pro o Enterprise (versione 1903 o successiva).

### Installare i driver e il firmware di Surface Hub 2

Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank"> driver e firmware per Windows 10 Pro e Enterprise OS su Surface Hub 2 </a> .
 
## Configurare le impostazioni consigliate

Per configurare completamente Surface Hub 2S come dispositivo di produttività personale, vedere <a href="surface-hub-2-post-install.md" target="_blank"> configurare Windows 10 Pro o Enterprise in Surface Hub 2 </a> .

> [!NOTE]
>Se la procedura descritta in questo articolo non esegue correttamente la migrazione del dispositivo a Windows 10 Pro o Enterprise per Surface Hub 2, contattare il <a href="https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support" target="_blank"> supporto Hub Surface </a> .

## Eseguire il rollback al team di Windows 10

Per ripristinare il dispositivo in un team di Windows 10, vedere <a href="surface-hub-2s-recover-reset.md" target="_blank"> reimpostazione e ripristino per Surface Hub 2S </a> .

> [!NOTE]
> Prima di ripristinare il team di Windows 10, è consigliabile annullare la registrazione di hub da SEMM. Per altre informazioni, vedere annullare la [registrazione dei dispositivi Surface da SEMM](https://docs.microsoft.com/surface/unenroll-surface-devices-from-semm).

## Cronologia versioni

Nella tabella seguente vengono riepilogate le modifiche apportate a questo articolo.

| Versione | Data               | Descrizione                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| v. 1,3  | 3 dicembre 2020 | Aggiornamento con le indicazioni sulla gestione della registrazione di SEMM                                                        |
| v. 1,2  | 29 settembre 2020 | Aggiornamenti vari che indirizzano il feedback sull'usabilità.                                                        |
| v. 1,1  | 15 settembre 2020 | È stata inserita una nota aggiuntiva nell'introduzione che chiarisce i requisiti di licenza per l'installazione di un nuovo sistema operativo. |
| v. 1.0  | 1 settembre 2020  | Nuovo articolo.                                                                                           |

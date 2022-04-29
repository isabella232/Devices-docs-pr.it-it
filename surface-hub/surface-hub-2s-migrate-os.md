---
title: Eseguire la migrazione a Pro o Enterprise Windows 10/11 il Surface Hub 2
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
appliesto:
- Surface Hub 2S
- Windows 10
- Windows 11
ms.openlocfilehash: 7b221b6f8b4a7753a10dd974da47ce58af41d006
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497759"
---
# <a name="migrate-to-windows-1011-pro-or-enterprise-on-surface-hub-2"></a>Eseguire la migrazione a Pro o Enterprise Windows 10/11 il Surface Hub 2

- [Cronologia delle versioni dell'articolo](#version-history)

Surface Hub 2S viene fornito con Windows 10 Team installato. Questa edizione personalizzata di Windows 10 facilita la collaborazione negli ambienti della sala riunioni. È invece possibile eseguire Windows 10/11 Pro o Enterprise per usare il Surface Hub 2S in modo analogo a qualsiasi altro PC.

> [!IMPORTANT]
> Questo processo di migrazione richiede di seguire la procedura specifica descritta in questo articolo. Prima di continuare, leggere [Componenti della soluzione](#solution-components) e [Flusso di lavoro migrazione e installazione](#migration-and-installation-workflow-summary).

> [!NOTE]
> Quando si installa Windows 10/11 Pro o Enterprise nel Surface Hub 2S, è necessaria una nuova licenza distinta dalla licenza Windows 10 Team esistente fornita con il dispositivo.

Avviare la migrazione da Windows 10 Team usando un PC separato e lo strumento *Surface UEFI Configurator* scaricabile. Lo strumento crea un pacchetto che contiene una nuova impostazione UEFI applicata all'Surface Hub 2S.  

Surface UEFI Configurator funziona come interfaccia in Surface Enterprise Management Mode (SEMM). Consente la gestione centralizzata delle impostazioni del firmware nei dispositivi Surface in un ambiente aziendale. Per altre informazioni, vedere [Microsoft Surface Enterprise Management Mode.For more information, see Microsoft Surface Enterprise Management Mode](/surface/surface-enterprise-management-mode).

## <a name="solution-components"></a>Componenti della soluzione

- Surface Hub dispositivo 2S in esecuzione Windows 10 Team
- Dispositivo separato in esecuzione Windows 10
- Strumento Surface UEFI Configurator per creare il pacchetto SEMM
- Windows 10/11 Pro o Enterprise'immagine del sistema operativo, versione 20H2 o successiva
- Due unità USB con 16 GB di spazio di archiviazione, formato FAT32
- Driver e firmware per Windows 10 Pro e Enterprise in un file del programma di installazione di Microsoft Windows (MSI) Surface Hub 2
- Connessione Internet
- Soluzione di imaging (facoltativa)

## <a name="migration-and-installation-workflow-summary"></a>Riepilogo del flusso di lavoro di migrazione e installazione

| Passaggio  | Azione                                                                                                 | Riepilogo                                                                                                                                                                                                                                                                                                                                                                                                  |
| - | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | [Verificare la versione UEFI nel Surface Hub 2S](#verify-the-uefi-version-on-surface-hub-2s).                                  | La versione UEFI deve essere *la versione 694.2938.768.0* o successiva.                                                                                                                                                                                                                                                                                                                                                      |
| 2 | [Scaricare Surface UEFI Configurator e Surface Hub 2 driver e firmware.](#download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware)                             | Nella pagina</a> **[Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703)** selezionare **Scarica**. Selezionare e scaricare quindi il **file MSI di Surface UEFI Configurator** e installarlo in un PC separato. Scaricare anche [i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 file MSI](https://www.microsoft.com/download/details.aspx?id=101974).</a> Salvare questo pacchetto per usarlo nel passaggio 5. |
| 3 | [Preparare il certificato SEMM.](#prepare-the-semm-certificate)                                                                          | Preparare il certificato necessario per eseguire Surface UEFI Configurator o usare il certificato corrente.                                                                                                                                                                                                                                                                                                      |
| 4 | [Creare un pacchetto SEMM.](#create-a-semm-package)                                                                               | Avviare Surface UEFI Configurator per creare un pacchetto SEMM in un'unità USB. Questo pacchetto conterrà i file di configurazione che è necessario applicare in Surface Hub 2S. Copiare questi file di pacchetto SEMM in una cartella nel PC.                                                                                                                                                                                          |
| 5 | [Caricare un'unità flash USB con Windows 10 immagine, il pacchetto SEMM e driver e firmware.](#load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware) | Creare un'unità USB che contiene un'immagine Windows 10. In questo esempio l'unità è denominata *BOOTME*. Aggiungere i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 (dal passaggio 2) e i file del pacchetto SEMM (dal passaggio 4) all'unità *BOOTME*.                                                                                                                                                                                                  |
| 6 | [Aggiornare UEFI nel Surface Hub 2S per abilitare la migrazione del sistema operativo.](#update-uefi-on-surface-hub-2s-to-enable-os-migration)                                              | Usare l'unità *BOOTME* per avviare il Surface Hub 2S nel menu UEFI e installare il pacchetto SEMM.|
| 7 | [Installare Windows 10 Pro o Enterprise.](#install-windows-1011-pro-or-enterprise)                                        | Usare l'unità *BOOTME* per installare Windows 10 Pro o Enterprise versione *20H2* o successiva.                                                                                                                                                                                                                                                                                 |
| 8 | [Installare driver e firmware per Windows 10 Pro e Enterprise.](#install-surface-hub-2-drivers-and-firmware)                                        | Per assicurarsi che il dispositivo disponga di tutti gli aggiornamenti e i driver più recenti, installare i driver e il <a href="https://www.microsoft.com/download/details.aspx?id=101974" target="_blank">firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 file MSI.</a>                                                                                                                                                                                                                                                                                  |
| 9 | [Configurare Surface Hub 2S come dispositivo di produttività personale.](#configure-recommended-settings)                                        |  Abilitare le impostazioni e le applicazioni consigliate per ottimizzare Surface Hub 2S come dispositivo di produttività personale.                                                                                                                                                                                                                                                                    |

### <a name="verify-the-uefi-version-on-surface-hub-2s"></a>Verificare la versione UEFI in Surface Hub 2S

Prima di eseguire la migrazione di Surface Hub da Windows 10 Team a Windows 10 Desktop, è necessaria la versione *UEFI 694.2938.768.0* o successiva.

**Per verificare la versione UEFI nel sistema:**

1. Nella home page Surface Hub 2S selezionare **Start** e quindi aprire l'app Surface (**Tutte le** **appSuperficie** > ).

2. Selezionare **Your Surface** per visualizzare informazioni su Surface Hub, inclusa la versione UEFI corrente nel dispositivo.
   - Se la versione UEFI è *694.2938.768.0* o successiva, come illustrato nell'immagine seguente, è possibile creare il pacchetto SEMM per abilitare la migrazione del sistema operativo.

    ![Screenshot che mostra la pagina "Your Surface" nell'app Surface.](images/shm-fig1.png)

   - Se la versione UEFI è precedente alla versione *694.2938.768.0*, usare uno dei metodi seguenti per ottenere una versione più recente

#### <a name="update-uefi-via-windows-update"></a>Aggiornare UEFI tramite Windows Update

1. Nel Surface Hub 2S accedere come **amministratore**.

    >[!Note]
    > Se non si conosce il nome utente o la password di amministratore, è necessario reimpostare il dispositivo. Per altre informazioni, vedere [Reimpostazione e ripristino per Surface Hub 2S](/surface-hub/surface-hub-2s-recover-reset).

1. Passare a **Tutte le app** >  **Impostazioni** >  **Aggiorna e sicurezza** >  **Windows Update** e installare tutti gli aggiornamenti.
1. Riavvia il dispositivo.
1. Verificare la versione UEFI usando l'app Surface. Se la versione UEFI non è la versione *694.2938.768.0* o successiva, ripetere questi passaggi o usare la procedura seguente per ottenere la versione UEFI più recente.

#### <a name="update-the-uefi-via-bare-metal-recovery-bmr-image"></a>Aggiornare l'immagine UEFI tramite ripristino bare metal (BMR)

1. Passare al [sito di Surface Recovery](https://support.microsoft.com/surfacerecoveryimage) e selezionare **Surface Hub 2S**.
3. Immettere il numero di serie dell'hub. Si trova sul retro dell'hub accanto alla connessione di alimentazione.
4. Seguire le istruzioni per scaricare l'immagine in un'unità USB formattata installando l'aggiornamento Windows 10 Team 2020.
5. Dopo l'aggiornamento, il dispositivo entra in configurazione predefinita.After the update, the device enters out-of-box-experience (OOBE) setup. Non è necessario completare la configurazione. La versione UEFI è già aggiornata. Spegnere invece il dispositivo tenendo premuto il pulsante di accensione fino a quando lo schermo non si spegne.

### <a name="download-surface-uefi-configurator-and-surface-hub-2-drivers-and-firmware"></a>Scaricare Surface UEFI Configurator e Surface Hub 2 driver e firmware

In un PC separato seguire questa procedura:

1. <a href="https://www.microsoft.com/download/details.aspx?id=46703" target="_blank"> Nella pagina</a> Surface Tools for IT selezionare **Scarica**.  
1. Selezionare e scaricare il file MSI di Surface UEFI Configurator e installarlo in un PC separato. Lo strumento Surface UEFI Configurator non può essere eseguito in un Surface Hub 2S mentre è installata Windows 10 Team edizione.

1. Scaricare il [file MSI del programma di installazione Windows Surface Hub 2 driver e firmware](https://www.microsoft.com/download/details.aspx?id=101974). Questo file verrà usato quando si installa il nuovo sistema operativo.

### <a name="prepare-the-semm-certificate"></a>Preparare il certificato SEMM

Se non hai mai usato Surface UEFI Configurator in precedenza, devi preparare un certificato. Questo certificato garantisce che dopo la registrazione di un dispositivo in SEMM sia possibile modificare le impostazioni UEFI solo usando i pacchetti creati con il certificato approvato.

Il modo in cui si ottiene un certificato dipende dalle dimensioni o dalla complessità dell'organizzazione:

- Enterprise organizzazioni in genere gestiscono la propria infrastruttura per generare certificati in base alle procedure di sicurezza standard.

- Le aziende di medie dimensioni e altre spesso scelgono di ottenere certificati dai provider partner. Questa opzione è consigliata per le organizzazioni che non hanno tanta esperienza IT o non dispongono di un team di sicurezza IT dedicato.

- In alternativa, è possibile generare un certificato autofirmate usando uno script di PowerShell. Per altre informazioni, vedere [i requisiti del certificato della modalità di gestione di Surface Enterprise](/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements). In alternativa, è possibile usare PowerShell per creare un certificato personalizzato. Per altre informazioni, vedere la documentazione [del certificato autofirma](/dotnet/core/additional-tools/self-signed-certificates-guide#create-a-self-signed-certificate) .

Il pacchetto SEMM creato da Surface UEFI Configurator deve essere protetto con un certificato. Il certificato verifica la firma dei file di configurazione prima che sia possibile applicare le impostazioni UEFI. Per altre informazioni, vedere la documentazione [di SEMM](/surface/surface-enterprise-management-mode) .

### <a name="create-a-semm-package"></a>Creare un pacchetto SEMM

1. In un PC separato installare lo strumento Surface UEFI Configurator scaricato in precedenza.

1. Aprire Surface UEFI Configurator e quindi selezionare **Avvia**.

   ![Schermata iniziale di Surface UEFI Configurator.](images/shm-fig2.png)

1. Selezionare **Surface Devices (Dispositivi Surface)** e quindi **Next (Avanti**).

   ![Screenshot che mostra l'opzione Surface Devices selezionata.](images/shm-fig3.png)
  
1. Selezionare **Pacchetto di configurazione**.

   ![Screenshot che mostra l'opzione "Seleziona pacchetto di configurazione" selezionata.](images/shm-fig4.png)
  
1. Selezionare **Protezione certificato**.

   ![Screenshot che mostra la scelta di "Select Certificate Protection".](images/shm-fig5.png)

   Verrà richiesto di aggiungere il file con estensione pfx del certificato.

   ![Screenshot che mostra dove aggiungere il file del certificato.](images/shm-fig6.png)

1. Immettere la password del certificato e quindi selezionare **OK**.

   ![Screenshot che mostra i campi per immettere e confermare la password del certificato.](images/shm-fig7.png)

1. Selezionare **Protezione password** per aggiungere una password a Surface UEFI. Questa password sarà necessaria ogni volta che si esegue l'avvio in UEFI. *È consigliabile impostare una password UEFI da usare in Surface Hub 2S.*

   ![Screenshot che mostra dove selezionare Protezione password.](images/shm-fig8.png)

1. Impostare una password UEFI e quindi selezionare **OK**.

   > [!IMPORTANT]
   > Salvare la password in un percorso sicuro accessibile agli amministratori IT che gestiscono Surface Hub. *Se questa password viene persa, non può essere recuperata.*

   ![Screenshot che mostra dove si imposta la password UEFI.](images/shm-fig9.png)

1. Selezionare **Surface Hub 2S** e quindi selezionare **Avanti**.

    ![Screenshot che mostra dove selezionare Surface Hub 2S.](images/shm-fig10.png)

1. Selezionare di nuovo **Avanti** .

    ![Screenshot che mostra di selezionare Avanti in "Scegliere i componenti".](images/shm-fig10a.png)

1. Per consentire l'installazione di Windows 10/11 Pro o Enterprise, attivare **EnableOsMigration** e quindi selezionare **Avanti**.

    ![Screenshot che mostra dove selezionare Abilita migrazione O S.](images/shm-fig11.png)

    ![Screenshot che mostra dove impostare Abilita migrazione del sistema operativo su .](images/shm-fig12.png)

### <a name="manage-semm-enrollment"></a>Gestire la registrazione SEMM

La registrazione di un dispositivo in SEMM influisce su come è possibile gestirlo. Ad esempio, dopo aver applicato un pacchetto SEMM, tutte le impostazioni UEFI non sono disponibili (bloccate) nel menu UEFI del dispositivo. Anche i valori predefiniti per altre impostazioni, ad esempio **IPv6 per L'avvio PXE** , non sono disponibili.

Per modificare le impostazioni UEFI dopo aver completato la migrazione, applicare un altro pacchetto SEMM o annullare la registrazione del dispositivo da SEMM. Se si applica un altro pacchetto SEMM per modificare le impostazioni UEFI, è necessario usare il certificato originale quando si compila il nuovo pacchetto SEMM. Usare lo strumento CONFIGURATOre UEFI e lasciare *disattivato* **EnableOSMigration** (non *attivato* come nei passaggi di migrazione originali).

#### <a name="if-you-work-with-partners"></a>Se si lavora con i partner

Se l'azienda esternalizza la migrazione Surface Hub 2 a Windows 10/11 Pro o Enterprise, è possibile che il partner trasferisca all'utente il certificato SEMM, il pacchetto SEMM e la password UEFI. In alternativa, dopo aver eseguito la migrazione dell'hub, è possibile annullare immediatamente la registrazione da SEMM. Questo passaggio consente l'amministrazione locale di UEFI e il trasferimento del dispositivo a un'altra parte. Tuttavia, è comunque consigliabile usare una password UEFI, che può essere configurata dopo la migrazione. Per altre informazioni, vedere [Gestire le impostazioni UEFI di Surface](/surface/manage-surface-uefi-settings).

#### <a name="to-roll-back-to-windows-10-team"></a>Per eseguire il rollback a Windows 10 Team

Se si sceglie di ripristinare il dispositivo in Windows 10 Team dopo la migrazione[, come descritto più avanti in questo articolo](#to-roll-back-to-windows-10-team), è consigliabile annullare la registrazione dell'hub da SEMM. Per altre informazioni, vedere [Annullare la registrazione dei dispositivi Surface da SEMM](/surface/unenroll-surface-devices-from-semm).

>[!WARNING]
>Per annullare la registrazione di un dispositivo da SEMM e ripristinare il controllo utente delle impostazioni UEFI di Surface, è necessario disporre del certificato SEMM usato per registrare il dispositivo in SEMM. Se questo certificato viene perso o danneggiato, non è possibile annullare la registrazione da SEMM. Eseguire il backup e proteggere il certificato SEMM di conseguenza.

#### <a name="save-the-semm-package-to-a-usb-drive"></a>Salvare il pacchetto SEMM in un'unità USB

1. Connessione un'unità USB al PC.
1. Scegliere **Hub 2S** e quindi selezionare **Avanti**.

   ![Screenshot che mostra dove selezionare Hub 2S.](images/shm-fig13.png)

   > [!WARNING]
   > Tutti i dati esistenti nell'unità USB verranno cancellati quando viene creato il pacchetto SEMM. Prima di compilare il pacchetto SEMM, rimuovere tutti i file necessari dall'unità USB.

1. Selezionare **Compila**.

   ![Screenshot che mostra dove selezionare Compila.](images/shm-fig14.png)

1. Acquisire uno screenshot di questa pagina e quindi selezionare **Fine**. Il pacchetto SEMM è ora pronto. Contiene il pacchetto SEMM *DfciUpdate.dfi* e un file di testo che include *l'identificazione personale* SEMM, ovvero gli ultimi due caratteri dell'identificazione personale del certificato.

   ![Screenshot che mostra dove selezionare Fine.](images/shm-fig15.png)

4. Salvare gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri saranno necessari per attivare SEMM quando si applica il pacchetto in Surface Hub 2S.

### <a name="load-a-usb-flash-drive-with-a-windows-10-image-semm-package-and-surface-hub-2-drivers-and-firmware"></a>Caricare un'unità flash USB con un'immagine Windows 10, un pacchetto SEMM e Surface Hub 2 driver e firmware

È possibile installare un'immagine Windows 10/11 Pro o Enterprise (versione *20H2* o successiva) usando una delle opzioni seguenti:

- Soluzione di imaging corrente.

- [Acceleratore di distribuzione surface](/surface/microsoft-surface-deployment-accelerator). Usare questo strumento per creare un'immagine di Windows 10 avviabile. L'immagine può includere tutti gli aggiornamenti Windows 10 correnti, Microsoft Office, altre app e i driver e il firmware necessari.

- Un'unità flash USB che contiene un'immagine Pro o Enterprise Windows 10/11. Questa opzione non avrà Wi-Fi disponibile fino a dopo la configurazione predefinita. Al termine dell'installazione, installare i [Surface Hub 2 driver e firmware necessari per Windows 10 Pro e Enterprise](https://www.microsoft.com/download/details.aspx?id=101974) nel dispositivo.

La procedura seguente illustra come creare un'unità flash USB dal supporto di installazione e quindi aggiungere i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 file MSI. Se si usa un altro metodo di distribuzione, passare alla sezione [Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo](#update-uefi-on-surface-hub-2s-to-enable-os-migration) di questo articolo.

> [!NOTE]
> Al termine dell'installazione, sarà necessaria una licenza valida per Windows 10 Pro o Windows 10 Enterprise separata dalla licenza di Windows 10 Team esistente.

1. Per creare un'installazione Windows 10 Pro, seguire le istruzioni per scaricare lo strumento di creazione dei supporti in [Scarica Windows 10](https://www.microsoft.com/software-download/windows10). Per scaricare Windows 10 Enterprise, passare al [Centro servizi per contratti multilicenza Microsoft](https://www.microsoft.com/licensing/servicecenter/default.aspx).

1. Inserire una nuova unità di archiviazione USB.
1. Aprire lo strumento di creazione dei supporti, selezionare **Crea supporto di installazione** e quindi selezionare **Avanti**.

   ![Screenshot che mostra l'opzione per creare supporti di installazione.](images/shm-fig16.png)

3. Selezionare una lingua e quindi selezionare **Windows 10** e **a 64 bit (x64).** Selezionare quindi **Avanti**.

   ![Screenshot che mostra dove si selezionano la lingua, l'edizione O S e il tipo di architettura.](images/shm-fig17.png)

4. Selezionare **Unità flash USB** e **quindi avanti.**

   ![Screenshot che mostra dove selezionare l'unità flash U S B.](images/shm-fig18.png)

5. Al termine del download, selezionare **Fine**.

   ![La schermata segnala che l'unità U S B è pronta e include un pulsante Fine.](images/shm-fig19.png)

6. Copiare i file del pacchetto SEMM e i driver e il firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 (file MSI) nella radice dell'unità flash USB (*BOOTME*) che contiene l'immagine Windows 10. L'unità USB BOOTME conterrà:

    - L'immagine Windows 10 avviabile.

    - File del pacchetto SEMM copiati nella radice dell'unità USB:

      - *DfciUpdate.dfi*.
      - File di testo che include l'identificazione personale SEMM. In questo esempio il file è *SurfaceUEFI_2020Aug25_1058.txt*. Il timestamp data-ora generato automaticamente corrisponde alla data in cui è stato creato il file usando Surface UEFI Configurator.

   - Driver e firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2 (SurfaceHub2S_Win10_18362_20.082.25682.0.msi). Copiare questo file nella radice dell'unità USB.

### <a name="update-uefi-on-surface-hub-2s-to-enable-os-migration"></a>Aggiornare UEFI in Surface Hub 2S per abilitare la migrazione del sistema operativo

1. Inserire l'unità BOOTME nella porta USB-A nella Surface Hub 2S. Per un elenco dei contenuti necessari, vedere la sezione precedente.

1. Per eseguire l'avvio in UEFI:

   1. Disattivare (arrestare) il Surface Hub 2S.
   1. Tenere premuto **Volume +**, quindi premere e rilasciare il pulsante di accensione. Tenere premuto **Volume +** fino a quando non viene visualizzato il menu UEFI.

      ![Il disegno mostra il volume e i pulsanti di alimentazione.](images/shm-fig20.png)

3. Al riavvio del dispositivo, immettere la password UEFI creata in precedenza, se applicabile (scelta consigliata).

   ![Schermata della password di sistema.](images/shm-fig22.png)

4. Dal menu UEFI selezionare **Gestione**. Selezionare quindi  **Installa da USB**.

   ![Screenshot che mostra dove selezionare Gestione e quindi "Installa da U S B".](images/shm-fig21.png)

5. Selezionare **Riavvia ora**, come illustrato nell'immagine seguente. Il dispositivo viene ora riavviato. Verrà visualizzato un logo Microsoft bianco al centro della finestra e quindi arrestato.

   ![Screenshot che mostra un messaggio che richiede il riavvio.](images/shm-fig25.png)

6. Premere e rilasciare il pulsante di accensione. Nella finestra di dialogo rossa visualizzata scegliere di attivare la modalità di gestione di Surface Enterprise.

7. Immettere l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI. Selezionare quindi **OK**.

   ![Screenshot che mostra la finestra di dialogo conferma attivazione in cui immettere l'identificazione personale del certificato a due caratteri e la password delle impostazioni UEFI.](images/shm-fig23.png)

   > [!NOTE]
   > Dopo aver attivato SEMM nel dispositivo, viene applicata la nuova impostazione UEFI **EnableOSMigration** . Non è più possibile accedere a Windows 10 Team. È invece necessario continuare con il passaggio successivo e installare Windows 10 Pro o Windows 10 Enterprise.

   Il dispositivo viene riavviato. Visualizza il logo bianco al centro dello schermo e quindi si spegne di nuovo.

### <a name="install-windows-1011-pro-or-enterprise"></a>Installare Pro o Enterprise Windows 10/11

1. Se l'unità di avvio Windows 10/11 Pro o Enterprise non è già presente nella porta USB-A Surface Hub 2, inserirla ora. Quindi premere e rilasciare il pulsante di accensione.

    All'avvio del dispositivo, verrà visualizzato il logo bianco al centro dello schermo. Sotto il logo bianco viene quindi visualizzato un cerchio rotante.

3. Se il dispositivo Surface non viene avviato automaticamente nell'unità USB, spegnere il dispositivo (scollegare il cavo di alimentazione e quindi ricollegarlo). Dopo aver collegato di nuovo il cavo di alimentazione, il dispositivo deve essere avviato dopo alcuni secondi. Quindi vedrai il logo bianco al centro dello schermo.

    Se il dispositivo non si accende, premere e rilasciare il pulsante di accensione. Subito dopo aver visualizzato il logo al centro dello schermo, tenere premuto il pulsante Volume verso il basso fino a quando non viene visualizzato il cerchio rotante sotto il logo bianco.

   ![Immagine del volume e dei pulsanti di alimentazione.](images/shm-fig26.png)

4. Quando viene avviata l'installazione predefinita dell'esperienza guidata, seguire le istruzioni per installare Windows 10/11 Pro o Enterprise (versione *20H2* o successiva).

### <a name="install-surface-hub-2-drivers-and-firmware"></a>Installare Surface Hub 2 driver e firmware

Per assicurarsi che il Surface Hub 2 sia aggiornato, installare [driver e firmware per Windows 10 Pro e Enterprise](https://www.microsoft.com/download/details.aspx?id=101974). Riavviare quindi il dispositivo. Mantenere la superficie attiva per un'ora e quindi riavviarla di nuovo. Non verrà richiesto il secondo riavvio. Questa sospensione e il riavvio aggiuntivo garantiscono che il firmware sia stato completamente aggiornato.

## <a name="configure-recommended-settings"></a>Configurare le impostazioni consigliate

Per configurare Surface Hub 2S come dispositivo di produttività personale, vedere [Configurare Pro Windows 10/11 o Enterprise in Surface Hub 2](surface-hub-2-post-install.md).

> [!NOTE]
>Se non è possibile eseguire correttamente la migrazione del dispositivo a Windows 10/11 Pro o Enterprise per Surface Hub 2 seguendo la procedura descritta in questo articolo, contattare [il supporto tecnico Surface Hub](https://support.microsoft.com/help/4037644/surface-contact-surface-warranty-and-software-support).

## <a name="to-roll-back-to-windows-10-team"></a>Per eseguire il rollback a Windows 10 Team

Per ripristinare il dispositivo in Windows 10 Team, vedere [Reimpostazione e ripristino per Surface Hub 2S](surface-hub-2s-recover-reset.md).

> [!NOTE]
> Prima di eseguire il rollback a Windows 10 Team, è consigliabile annullare la registrazione del Surface Hub da SEMM. Per altre informazioni, vedere [Annullare la registrazione dei dispositivi Surface da SEMM](/surface/unenroll-surface-devices-from-semm).

## <a name="version-history"></a>Cronologia delle versioni

La tabella seguente riepiloga le modifiche apportate a questo articolo.

| Versione | Data               | Descrizione                                                                                           |
| ------- | ------------------ | ----------------------------------------------------------------------------------------------------- |
| Presso. 1.5  | 1° dicembre 2021  | Aggiornato per mostrare il supporto per Windows 11
| Presso. 1.4  | 14 dicembre 2020 | Fornisce [altre informazioni](#install-surface-hub-2-drivers-and-firmware) sull'installazione del file MSI per "Driver e firmware per Windows 10 Pro e Enterprise sistema operativo in Surface Hub 2", informando che potrebbe essere necessario un secondo riavvio a seconda dello stato del sistema.                                                          |
| Presso. 1.3  | 3 dicembre 2020 | Aggiornato con indicazioni sulla [gestione della registrazione SEMM](#manage-semm-enrollment).                                                       |
| Presso. 1.2  | 29 settembre 2020 | Aggiornamenti vari che rispondono al feedback sull'usabilità.                                                        |
| Presso. 1.1  | 15 settembre 2020 | Nell'introduzione è stata inserita una nota aggiuntiva che chiarisce i requisiti di licenza per l'installazione di un nuovo sistema operativo. |
| Presso. 1.0  | 1° settembre 2020  | Nuovo articolo.                                                                                           |

---
title: Annullare la registrazione dei dispositivi Surface da SEMM (Surface)
description: Scopri come annullare la registrazione di un dispositivo da SEMM usando un pacchetto di reimpostazione UEFI di Surface o l'opzione Richiesta di ripristino.
keywords: surface enterprise management
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 4942dd5ab187b7350e5093d8d189ad52536ef5bd
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448559"
---
# <a name="unenroll-surface-devices-from-semm"></a>Annullare la registrazione dei dispositivi Surface da SEMM

Quando un dispositivo Surface viene registrato in surface Enterprise Management Mode (SEMM), un certificato viene archiviato nel firmware del dispositivo. La presenza di tale certificato e la registrazione in SEMM impediscono modifiche non autorizzate alle impostazioni o alle opzioni UEFI di Surface mentre il dispositivo è registrato in SEMM. Per ripristinare il controllo delle impostazioni UEFI di Surface per l'utente, è necessario annullare la registrazione del dispositivo Surface da SEMM, un processo talvolta descritto come reimpostazione o ripristino. Esistono due metodi che puoi usare per annullare la registrazione di un dispositivo da SEMM, ovvero un pacchetto di reimpostazione UEFI di Surface e una richiesta di ripristino.

>[!WARNING]
>Per annullare la registrazione di un dispositivo da SEMM e ripristinare il controllo utente delle impostazioni UEFI di Surface, devi disporre del certificato SEMM usato per registrare il dispositivo in SEMM. Se questo certificato viene perso o danneggiato, non è possibile annullare la registrazione da SEMM. Eseguire il backup e proteggere il certificato SEMM di conseguenza.

Per altre informazioni su SEMM, vedi [Microsoft Surface Enterprise Management Mode](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

## <a name="unenroll-a-surface-device-from-semm-with-a-surface-uefi-reset-package"></a>Annullare la registrazione di un dispositivo Surface da SEMM con un pacchetto di reimpostazione UEFI di Surface

Il pacchetto di reimpostazione UEFI di Surface è il metodo principale che usi per annullare la registrazione di un dispositivo Surface da SEMM. Come un pacchetto di configurazione UEFI di Surface, il pacchetto di reimpostazione è un file Windows Installer (.msi) che configura SEMM nel dispositivo. A differenza del pacchetto di configurazione, il pacchetto di reimpostazione reimposta la configurazione UEFI di Surface in un dispositivo Surface alle impostazioni predefinite, rimuove il certificato SEMM e annulla la registrazione del dispositivo da SEMM.

I pacchetti di reimpostazione vengono creati in modo specifico per un singolo dispositivo Surface. Per iniziare il processo di creazione di un pacchetto di reimpostazione, è necessario il numero di serie del dispositivo che si desidera annullare la registrazione, nonché il certificato SEMM usato per registrare il dispositivo. Puoi trovare il numero di serie del dispositivo Surface nella pagina delle informazioni **del PC** di Surface UEFI, come illustrato nella figura 1. Questa pagina viene visualizzata anche se Surface UEFI è protetto da password e la password non è corretta.

![Viene visualizzato il numero di serie del dispositivo Surface.](images/surface-semm-unenroll-fig1.png "Serial number of Surface device is displayed")

*Figura 1. Il numero di serie del dispositivo Surface viene visualizzato nella pagina delle informazioni sul PC UeFI di Surface*

>[!NOTE]
>Per avviare Surface UEFI, premi **Volume Up** e **Power** contemporaneamente mentre il dispositivo è spento. Tieni **premuto Volume fino** a quando non viene visualizzato il logo surface e il dispositivo inizia l'avvio.

Per creare un pacchetto di reimpostazione UEFI di Surface, segui questi passaggi:

1. Apri Configuratore UEFI di Microsoft Surface dalla menu Start.
2. Fai clic su **Start**.
3. Fare **clic su Reimposta** pacchetto, come illustrato nella figura 2.

   ![Seleziona Reimposta pacchetto per creare un pacchetto per annullare la registrazione del dispositivo Surface da SEMM.](images/surface-semm-unenroll-fig2.png "Select Reset Package to create a package to unenroll Surface device from SEMM")

   *Figura 2. Fai clic su Reimposta pacchetto per creare un pacchetto per annullare la registrazione di un dispositivo Surface da SEMM*

4. Fare **clic su Protezione** certificato per aggiungere il file di certificato SEMM con chiave privata (pfx), come illustrato nella figura 3. Passare al percorso del file del certificato, selezionarlo e quindi fare clic su **OK**.

   ![Aggiungi il certificato SEMM al pacchetto di reimpostazione UEFI di Surface.](images/surface-semm-unenroll-fig3.png "Add the SEMM certificate to Surface UEFI reset package")

   *Figura 3. Aggiungere il certificato SEMM a un pacchetto di reimpostazione UEFI di Surface*

5. Fai clic su **Avanti**.
6. Digita il numero di serie del dispositivo che vuoi annullare la registrazione da SEMM (come illustrato nella figura 4) e quindi fai clic su **Compila** per generare il pacchetto di reimpostazione UEFI di Surface.

   ![Crea un pacchetto di reimpostazione UEFI di Surface con numero di serie del dispositivo Surface.](images/surface-semm-unenroll-fig4.png "Create a Surface UEFI reset package with serial number of Surface device")

   *Figura 4. Usa il numero di serie del dispositivo Surface per creare un pacchetto di reimpostazione UEFI di Surface*

7. Nella finestra **di dialogo Salva** con nome specificare un nome per il pacchetto di reimpostazione UEFI di Surface, passare al percorso in cui si desidera salvare il file e quindi fare clic su **Salva**.
8. Al termine della generazione del pacchetto **, viene visualizzata** la pagina Operazione completata. Fai **clic su Fine** per completare la creazione del pacchetto e chiudi Il configuratore UEFI di Microsoft Surface.

Esegui il file Windows Installer (.msi) del pacchetto di reimpostazione UEFI di Surface nel dispositivo Surface per annullare la registrazione del dispositivo da SEMM. Il pacchetto di reimpostazione richiederà un riavvio per eseguire l'operazione di annullamento della registrazione. Dopo l'annullamento della registrazione del dispositivo, puoi verificare la corretta rimozione verificando che l'elemento Pacchetto di configurazione **di Microsoft Surface** **in Programmi** e funzionalità (illustrato nella figura 5) non sia più presente.

![Schermata che mostra che il dispositivo è registrato in SEMM.](images/surface-semm-unenroll-fig5.png "Screen that shows device is enrolled in SEMM")

*Figura 5. La presenza dell'elemento Pacchetto di configurazione di Microsoft Surface in Programmi e funzionalità indica che il dispositivo è registrato in SEMM*

## <a name="unenroll-a-surface-device-from-semm-with-a-recovery-request"></a>Annullare la registrazione di un dispositivo Surface da SEMM con una richiesta di ripristino

In alcuni scenari, un pacchetto di reimpostazione UEFI di Surface potrebbe non essere un'opzione praticabile per annullare la registrazione di un dispositivo Surface da SEMM (ad esempio, in cui Windows è diventato inutilizzabile). In questi scenari puoi annullare la registrazione del dispositivo usando una richiesta di ripristino generata da Surface UEFI. Il processo di richiesta di ripristino può essere avviato anche nei dispositivi in cui non hai la password UEFI di Surface.

Il processo di richiesta di ripristino viene avviato da Surface UEFI nel dispositivo Surface, approvato con Il configuratore UEFI di Microsoft Surface in un altro computer e quindi completato in Surface UEFI. Come il pacchetto di reimpostazione, l'approvazione di una richiesta di ripristino con configuratore UEFI di Microsoft Surface richiede l'accesso al certificato SEMM usato per registrare il dispositivo Surface.

Per avviare una richiesta di ripristino, attenersi alla seguente procedura:

1. Avvia il dispositivo Surface di cui annullare la registrazione da SEMM a Surface UEFI.
2. Se richiesto, digita la password UEFI di Surface.
3. Fare clic **sulla Enterprise di** gestione dei dati, come illustrato nella figura 6.

   ![Enterprise Gestione utenti.](images/surface-semm-unenroll-fig6.png "Enterprise Management page")

   *Figura 6. La Enterprise di gestione dei dispositivi viene visualizzata in Surface UEFI nei dispositivi registrati in SEMM*

4. Fare clic o premere **Informazioni di base**.
5. Fare clic o premere **Avanti** per avviare il processo di richiesta di ripristino.
   >[!NOTE]
   >Una richiesta di ripristino scade due ore dopo la sua creazione. Se una richiesta di ripristino non viene completata in questo momento, sarà necessario riavviare il processo di richiesta di ripristino.
6. Selezionare **SeMM Certificate** dall'elenco dei certificati visualizzato nella pagina **Choose a SEMM reset key** (shown in Figure 7), quindi fare clic o premere **Next**.

   ![Selezionare il certificato SEMM per la richiesta di ripristino.](images/surface-semm-unenroll-fig7.png "Select SEMM certificate for your Recovery Request")

   *Figura 7. Scegliere il certificato SEMM per la richiesta di ripristino (richiesta di reimpostazione)*

7. Nella pagina Immetti codice di verifica reimpostazione **SEMM** è possibile fare clic sui pulsanti Codice **** **QR** o Testo per visualizzare la richiesta di ripristino (richiesta di reimpostazione) come illustrato nella figura 8 o il pulsante **USB** per salvare la richiesta di ripristino (richiesta di reimpostazione) come file in un'unità USB, come illustrato nella figura 9.

   ![Richiesta di ripristino visualizzata come codice QR.](images/surface-semm-unenroll-fig8.png "Recovery Request displayed as a QR Code")

   *Figura 8. Una richiesta di ripristino (richiesta di reimpostazione) visualizzata come codice QR*

   ![Salvare una richiesta di ripristino in un'unità USB.](images/surface-semm-unenroll-fig9.png "Save a recovery request to a USB drive")

   *Figura 9. Salvare una richiesta di ripristino (richiesta di reimpostazione) in un'unità USB*

   * Per usare una richiesta di ripristino del codice QR (richiesta di reimpostazione), usa un'app lettore QR su un dispositivo mobile per leggere il codice. L'app lettore QR tradurrà il codice QR in una stringa alfanumerica. Puoi quindi inviare tramite posta elettronica o messaggio tale stringa all'amministratore che produrrà il codice di verifica di reimpostazione con Microsoft Surface UEFI Configurator.
   * Per usare una richiesta di ripristino (richiesta di reimpostazione) salvata in un'unità USB come file, usa l'unità USB per trasferire il file nel computer in cui verrà usato il configuratore UEFI di Microsoft Surface per produrre il codice di verifica di reimpostazione. Il file può anche essere copiato dall'unità USB su un altro dispositivo per essere inviato tramite posta elettronica o trasferito in rete.
   * Per usare la richiesta di ripristino (richiesta di reimpostazione) come testo, digita semplicemente il testo direttamente nel Configuratore UEFI di Microsoft Surface.

8. Apri Configuratore UEFI di Microsoft Surface dal menu Start in un altro computer.
    >[!NOTE]
    >Il configuratore UEFI di Microsoft Surface deve essere eseguito in un ambiente in grado di autenticare la catena di certificati per il certificato SEMM.
9. Fai clic su **Start**.
10. Fare **clic su Richiesta** di ripristino, come illustrato nella figura 10.

    ![Avviare il processo per approvare una richiesta di ripristino.](images/surface-semm-unenroll-fig10.png "Start process to approve a Recovery Request")

    *Figura 10. Fare clic su Richiesta di ripristino per avviare il processo per approvare una richiesta di ripristino*

11. Fare **clic su Protezione** certificato per autenticare la richiesta di ripristino con il certificato SEMM.
12. Individuare e selezionare il file del certificato SEMM e quindi fare clic su **OK**.
13. Quando viene richiesto di immettere la password del certificato come illustrato nella figura 11, digitare e confermare la password per il file del certificato e quindi fare clic su **OK**.

    ![Digitare la password per il certificato SEMM.](images/surface-semm-unenroll-fig11.png "Type password for SEMM certificate")

    *Figura 11. Digitare la password per il certificato SEMM*

14. Fai clic su **Avanti**.
15. Immetti la richiesta di ripristino (richiesta di reimpostazione), quindi fai clic su **Genera** per creare un codice di verifica di reimpostazione (come illustrato nella figura 12).

    ![Immettere la richiesta di ripristino.](images/surface-semm-unenroll-fig12.png "Enter the recovery request")

    *Figura 12. Immettere la richiesta di ripristino (richiesta di reimpostazione)*

    * Se hai visualizzato la richiesta di ripristino (richiesta di reimpostazione) come testo nel dispositivo Surface da reimpostare, usa la tastiera per digitare la richiesta di ripristino (richiesta di reimpostazione) nel campo fornito.
    * Se hai visualizzato la richiesta di ripristino (richiesta di reimpostazione) come codice QR e quindi hai usato un'applicazione di messaggistica o di posta elettronica per inviare il codice al computer con il configuratore UEFI di Microsoft Surface, copia e incolla il codice nel campo fornito.
    * Se la richiesta di ripristino (richiesta di reimpostazione) è stata salvata come file in un'unità **** USB, fare clic sul pulsante Importa, individuare e selezionare il file Richiesta di ripristino (richiesta di reimpostazione) e quindi fare clic su **OK**.

16. Il codice di verifica della reimpostazione viene visualizzato nel configuratore UEFI di Microsoft Surface, come illustrato nella figura 13.

    ![Visualizzazione del codice di verifica della reimpostazione.](images/surface-semm-unenroll-fig13.png "Display of the reset verification code")

    *Figura 13. Il codice di verifica della reimpostazione visualizzato nel configuratore UEFI di Microsoft Surface*

    * Fai clic **sul pulsante** Condividi per inviare il codice di verifica della reimpostazione tramite posta elettronica.

17. Immetti il codice di verifica della reimpostazione nel campo fornito nel dispositivo Surface (mostrato nella figura 8), quindi fai clic o premi **** Verifica per reimpostare il dispositivo e annullare la registrazione del dispositivo da SEMM.
18. Fare clic o premere **Riavvia** ora nella pagina **reimpostazione SEMM** completata per completare l'annullamento della registrazione da SEMM, come illustrato nella figura 14.

    ![Visualizzazione di esempio dell'annullamento della registrazione da SEMM.](images/surface-semm-unenroll-fig14.png "Example display of successful unenrollment from SEMM")

    *Figura 14. Annullamento della registrazione da SEMM completato*

19. Fai **clic su** Termina in Configuratore UEFI di Microsoft Surface per completare il processo di richiesta di ripristino (richiesta di reimpostazione) e chiudere Configuratore UEFI di Microsoft Surface.



---
title: Annullare la registrazione dei dispositivi Surface da SEMM (Surface)
description: Informazioni su come annullare la registrazione di un dispositivo da SEMM usando un pacchetto di ripristino UEFI di Surface o l'opzione di richiesta di ripristino.
keywords: gestione di Surface Enterprise
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
ms.openlocfilehash: aa24ff1ac8a93ebc8078490c5e0c8fa34c940a25
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832474"
---
# Annullare la registrazione dei dispositivi Surface da SEMM

Quando un dispositivo Surface viene registrato in modalità di gestione di Surface Enterprise (SEMM), un certificato viene archiviato nel firmware di tale dispositivo. La presenza di tale certificato e la registrazione in SEMM impediscono eventuali modifiche non autorizzate alle impostazioni o alle opzioni di Surface UEFI mentre il dispositivo è registrato in SEMM. Per ripristinare il controllo delle impostazioni di Surface UEFI per l'utente, è necessario annullare la registrazione del dispositivo Surface da SEMM, un processo a volte descritto come Reset o Recovery. Esistono due metodi che è possibile usare per annullare la registrazione di un dispositivo da SEMM, ovvero un pacchetto di ripristino di Surface UEFI e una richiesta di ripristino.

>[!WARNING]
>Per annullare la registrazione di un dispositivo da SEMM e ripristinare il controllo utente delle impostazioni di Surface UEFI, è necessario disporre del certificato SEMM usato per registrare il dispositivo in SEMM. Se il certificato viene perso o danneggiato, non è possibile annullare la registrazione da SEMM. Eseguire il backup e proteggere il certificato di SEMM di conseguenza.

Per altre informazioni su SEMM, vedere [modalità di gestione Microsoft Surface Enterprise](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode).

## Annullare la registrazione di un dispositivo Surface da SEMM con un pacchetto di ripristino di Surface UEFI

Il pacchetto di ripristino di Surface UEFI è il metodo principale usato per annullare la registrazione di un dispositivo Surface da SEMM. Come un pacchetto di configurazione UEFI di Surface, il pacchetto reset è un file di Windows Installer (con estensione msi) che configura SEMM nel dispositivo. A differenza del pacchetto di configurazione, il pacchetto Reimposta reimposta la configurazione di Surface UEFI su un dispositivo Surface sulle impostazioni predefinite, rimuove il certificato SEMM e Annulla la registrazione del dispositivo da SEMM.

I pacchetti reset vengono creati in modo specifico per un singolo dispositivo Surface. Per iniziare il processo di creazione di un pacchetto di reimpostazione, è necessario il numero seriale del dispositivo che si vuole annullare la registrazione, oltre al certificato SEMM usato per la registrazione del dispositivo. È possibile trovare il numero seriale del dispositivo Surface nella pagina **informazioni PC** di Surface UEFI, come illustrato nella figura 1. Questa pagina viene visualizzata anche se Surface UEFI è protetto da password e viene immessa la password non corretta.

![Viene visualizzato il numero seriale del dispositivo Surface](images/surface-semm-unenroll-fig1.png "Serial number of Surface device is displayed")

*Figura 1. Il numero seriale del dispositivo Surface viene visualizzato nella pagina informazioni PC di Surface UEFI*

>[!NOTE]
>Per eseguire l'avvio da Surface UEFI, premere **volume su** e **Power** contemporaneamente mentre il dispositivo è disattivato. Tenere premuto **volume** fino a visualizzare il logo Surface e il dispositivo inizia ad avviarsi.

Per creare un pacchetto di ripristino di Surface UEFI, eseguire le operazioni seguenti:

1. Aprire Microsoft Surface UEFI Configurator dal menu Start.
2. Fai clic su **Start**.
3. Fare clic su **Reimposta pacchetto**, come illustrato nella figura 2.

   ![Selezionare Reimposta pacchetto per creare un pacchetto per annullare la registrazione del dispositivo Surface da SEMM](images/surface-semm-unenroll-fig2.png "Select Reset Package to create a package to unenroll Surface device from SEMM")

   *Figura 2. Fare clic su Reimposta pacchetto per creare un pacchetto per annullare la registrazione di un dispositivo Surface da SEMM*

4. Fare clic su **protezione certificato** per aggiungere il file di certificato SEMM con la chiave privata (PFX), come illustrato nella figura 3. Passare al percorso del file del certificato, selezionare il file e quindi fare clic su **OK**.

   ![Aggiungere il certificato SEMM al pacchetto di ripristino UEFI di Surface](images/surface-semm-unenroll-fig3.png "Add the SEMM certificate to Surface UEFI reset package")

   *Figura 3. Aggiungere il certificato SEMM a un pacchetto di ripristino di Surface UEFI*

5. Fai clic su **Avanti**.
6. Digitare il numero seriale del dispositivo che si vuole annullare la registrazione da SEMM (come illustrato nella figura 4) e quindi fare clic su **Compila** per generare il pacchetto di ripristino di Surface UEFI.

   ![Creare un pacchetto di reimpostazione UEFI di Surface con numero seriale di dispositivo Surface](images/surface-semm-unenroll-fig4.png "Create a Surface UEFI reset package with serial number of Surface device")

   *Figura 4. Usare il numero seriale del dispositivo Surface per creare un pacchetto di ripristino di Surface UEFI*

7. Nella finestra di dialogo **Salva con** nome specificare un cognome per il pacchetto di ripristino di Surface UEFI, passare al percorso in cui si vuole salvare il file e quindi fare clic su **Salva**.
8. Quando la generazione del pacchetto è stata completata, viene visualizzata la pagina **completata** . Fare clic su **fine** per completare la creazione del pacchetto e chiudere Microsoft Surface UEFI Configurator.

Eseguire il file di Surface UEFI Reset package Windows Installer (con estensione msi) nel dispositivo Surface per annullare la registrazione del dispositivo da SEMM. Il pacchetto Reimposta richiederà un riavvio per eseguire l'operazione di disregistrazione. Dopo che il dispositivo è stato annullato la registrazione, è possibile verificare la rimozione corretta garantendo che l'elemento del **pacchetto di configurazione della superficie Microsoft** in **programmi e funzionalità** (illustrato nella figura 5) non sia più presente.

![Schermata che mostra il dispositivo registrato in SEMM](images/surface-semm-unenroll-fig5.png "Screen that shows device is enrolled in SEMM")

*Figura 5. La presenza dell'elemento del pacchetto di configurazione della superficie Microsoft in programmi e funzionalità indica che il dispositivo è registrato in SEMM*

## Annullare la registrazione di un dispositivo Surface da SEMM con una richiesta di ripristino

In alcuni scenari, un pacchetto di ripristino di Surface UEFI potrebbe non essere un'opzione valida per annullare la registrazione di un dispositivo Surface da SEMM (ad esempio, dove Windows è diventato inutilizzabile). In questi scenari puoi annullare la registrazione del dispositivo usando una richiesta di ripristino generata dall'interno di Surface UEFI. Il processo di richiesta di ripristino può essere avviato anche nei dispositivi in cui non è presente la password di Surface UEFI.

Il processo di richiesta di ripristino viene avviato dall'UEFI di Surface sul dispositivo Surface, approvato con Microsoft Surface UEFI Configurator in un altro computer e quindi completato in Surface UEFI. Come il pacchetto di reimpostazione, l'approvazione di una richiesta di ripristino con Microsoft Surface UEFI Configurator richiede l'accesso al certificato SEMM usato per la registrazione del dispositivo Surface.

Per avviare una richiesta di ripristino, eseguire le operazioni seguenti:

1. Avviare il dispositivo Surface da cui annullare la registrazione da SEMM alla superficie UEFI.
2. Se richiesto, digitare la password di Surface UEFI.
3. Fare clic sulla pagina **gestione aziendale** , come illustrato nella figura 6.

   ![Pagina Gestione aziendale](images/surface-semm-unenroll-fig6.png "Enterprise Management page")

   *Figura 6. La pagina Gestione aziendale viene visualizzata in UEFI di Surface nei dispositivi registrati in SEMM*

4. Fare clic o premere per **iniziare**.
5. Fare clic o premere **Avanti** per avviare il processo di richiesta di ripristino.
   >[!NOTE]
   >Una richiesta di ripristino scade due ore dopo la creazione. Se non è stata completata una richiesta di recupero in questo momento, sarà necessario riavviare il processo di richiesta di ripristino.
6. Selezionare **SEMM certificato** nell'elenco dei certificati visualizzati nella pagina **scegliere una chiave di reimpostazione di SEMM** (illustrato nella figura 7), quindi fare clic o premere **Avanti**.

   ![Selezionare certificato SEMM per la richiesta di ripristino](images/surface-semm-unenroll-fig7.png "Select SEMM certificate for your Recovery Request")

   *Figura 7. Scegliere il certificato SEMM per la richiesta di ripristino (richiesta di reimpostazione)*

7. Nella pagina **immettere il codice di verifica di SEMM Reset** è possibile fare clic sul **codice QR** o sui pulsanti di **testo** per visualizzare la richiesta di ripristino (richiesta di reimpostazione) come illustrato nella figura 8 o il pulsante **USB** per salvare la richiesta di ripristino (reimpostazione richiesta) come file in un'unità USB, come illustrato nella figura 9.

   ![Richiesta di ripristino visualizzata come codice QR](images/surface-semm-unenroll-fig8.png "Recovery Request displayed as a QR Code")

   *Figura 8. Richiesta di ripristino (richiesta di reimpostazione) visualizzata come codice QR*

   ![Salvare una richiesta di ripristino in un'unità USB](images/surface-semm-unenroll-fig9.png "Save a recovery request to a USB drive")

   *Figura 9. Salvare una richiesta di ripristino (richiesta di reimpostazione) su un'unità USB*

   * Per usare una richiesta di ripristino del codice QR (richiesta di reimpostazione), usare un'app di lettura QR su un dispositivo mobile per leggere il codice. L'app di lettura QR tradurrà il codice QR in una stringa alfanumerica. È quindi possibile inviare un messaggio di posta elettronica o una stringa all'amministratore che produrrà il codice di verifica reimpostazione con Microsoft Surface UEFI Configurator.
   * Per usare una richiesta di ripristino (richiesta di reimpostazione) salvata in un'unità USB come file, usare l'unità USB per trasferire il file nel computer in cui verrà usato Microsoft Surface UEFI Configurator per produrre il codice di verifica reset. Il file può anche essere copiato dall'unità USB in un altro dispositivo per essere inviato tramite posta elettronica o trasferito tramite la rete.
   * Per usare la richiesta di ripristino (reimpostazione richiesta) come testo, è sufficiente digitare il testo direttamente in Microsoft Surface UEFI Configurator.

8. Aprire Microsoft Surface UEFI Configurator dal menu Start in un altro computer.
    >[!NOTE]
    >Microsoft Surface UEFI Configurator deve essere eseguito in un ambiente in grado di autenticare la catena di certificati per il certificato SEMM.
9. Fai clic su **Start**.
10. Fare clic su **richiesta di ripristino**, come illustrato nella figura 10.

    ![Avviare il processo per approvare una richiesta di ripristino](images/surface-semm-unenroll-fig10.png "Start process to approve a Recovery Request")

    *Figura 10. Fare clic su richiesta di ripristino per avviare il processo per approvare una richiesta di ripristino*

11. Fare clic su **protezione certificati** per autenticare la richiesta di recupero con il certificato SEMM.
12. Individuare e selezionare il file di certificato di SEMM e quindi fare clic su **OK**.
13. Quando viene richiesto di immettere la password del certificato, come illustrato nella figura 11, digitare e confermare la password per il file di certificato e quindi fare clic su **OK**.

    ![Digitare la password per il certificato SEMM](images/surface-semm-unenroll-fig11.png "Type password for SEMM certificate")

    *Figura 11. Digitare la password per il certificato SEMM*

14. Fai clic su **Avanti**.
15. Immettere la richiesta di ripristino (richiesta di reimpostazione) e quindi fare clic su **genera** per creare un codice di verifica reimpostazione (come illustrato nella figura 12).

    ![Immettere la richiesta di ripristino](images/surface-semm-unenroll-fig12.png "Enter the recovery request")

    *Figura 12. Immettere la richiesta di ripristino (richiesta di reimpostazione)*

    * Se è stata visualizzata la richiesta di ripristino (richiesta di reimpostazione) come testo sul dispositivo Surface da reimpostare, usare la tastiera per digitare la richiesta di ripristino (richiesta di reimpostazione) nel campo specificato.
    * Se la richiesta di ripristino viene visualizzata come codice QR e quindi si usa un'applicazione di messaggistica o di posta elettronica per inviare il codice al computer con Microsoft Surface UEFI Configurator, copiare e incollare il codice nel campo specificato.
    * Se la richiesta di ripristino viene salvata come file in un'unità USB, fare clic sul pulsante **Importa** , individuare e selezionare il file della richiesta di ripristino (reimpostare la richiesta) e quindi fare clic su **OK**.

16. Il codice di verifica Reset viene visualizzato in Microsoft Surface UEFI Configurator, come illustrato nella figura 13.

    ![Visualizzazione del codice di verifica Reset](images/surface-semm-unenroll-fig13.png "Display of the reset verification code")

    *Figura 13. Codice di verifica reimpostazione visualizzato in Microsoft Surface UEFI Configurator*

    * Fare clic sul pulsante **Condividi** per inviare il codice di verifica reimpostazione tramite posta elettronica.

17. Immettere il codice di verifica reimpostazione nel campo specificato nel dispositivo Surface (illustrato nella figura 8), quindi fare clic o premere **Verifica** per reimpostare il dispositivo e annullare la registrazione del dispositivo da SEMM.
18. Fare clic o premere **Riavvia ora** nella pagina **SEMM Reset Successful** per completare la registrazione da SEMM, come illustrato nella figura 14.

    ![Esempio di visualizzazione della registrazione riuscita da SEMM](images/surface-semm-unenroll-fig14.png "Example display of successful unenrollment from SEMM")

    *Figura 14. Esito positivo della registrazione da SEMM*

19. Fare clic su **fine** in Microsoft Surface UEFI Configurator per completare il processo di richiesta di ripristino (reimpostazione della richiesta) e chiudere Microsoft Surface UEFI Configurator.



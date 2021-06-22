---
title: Garanzia e servizio surface self-service
description: Microsoft 365 I clienti aziendali potrebbero essere idonei a usare il nodo beta Di garanzia self-service e servizio surface nell'interfaccia di amministrazione di Microsoft per creare e gestire gli ordini di assistenza.
ms.prod: w10
ms.mktglfcycl: support
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 06/07/2021
ms.reviewer: louannh
manager: laurawi
audience: itpro
ms.openlocfilehash: a6021a58c85ac6ee4c039959dcde9bab632ea1bb
ms.sourcegitcommit: 267e12897efd9d11f8c7303eaf780632741cfe77
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/22/2021
ms.locfileid: "11614099"
---
# <a name="surface-self-serve-warranty-and-service"></a>Garanzia e servizio self-service surface

Microsoft 365 I clienti aziendali potrebbero essere idonei a usare il nodo Surface Self Serve Warranty and Service nel Amministrazione Microsoft 365 Center per creare e gestire gli ordini di assistenza. Questa nuova funzionalità, disponibile come programma beta, consente agli amministratori globali di designare le autorizzazioni per gli utenti dell'azienda responsabili del supporto delle richieste di garanzia e dei servizi, tra cui:

- Upload numeri di serie per i dispositivi che richiedono il servizio.
- Aggiungere più indirizzi di spedizione.
- Creare un singolo ordine di assistenza per uno o più dispositivi e copertine tipo.
- Vedi lo stato dell'ordine di assistenza in tempo reale.
- Spedire e ricevere le spedizioni di Exchange advance in blocco se i dispositivi sono coperti da una garanzia estesa o advanced Exchange è stato incluso come parte dell'acquisto del dispositivo.

## <a name="join-beta-program"></a>Partecipare al programma beta

Per altre informazioni sull'esperienza e su come partecipare al programma beta, contatta il responsabile dell'account microsoft per il successo dei clienti o il customer success manager.

## <a name="role-based-permissions"></a>Autorizzazioni basate sui ruoli

La garanzia e il servizio Surface Self-Serve consente a un amministratore globale Microsoft 365 di concedere autorizzazioni diverse per la creazione e la gestione degli ordini di assistenza assegnando ruoli agli utenti.

Quando un tenant Microsoft 365 viene aggiunto al programma beta, ai ruoli di amministratore seguenti vengono concesse autorizzazioni aggiuntive:

| Ruolo                  | Autorizzazioni                                                                                                                         |
| --------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Amministratore globale          | Visualizza richieste di ripristino<br>Creare/gestire richieste di ripristino<br>Add/Edit/Delete Ship to Address(es)<br>Creare/gestire gli utenti e i relativi ruoli |
| Service Support Admin | Visualizza richieste di ripristino<br>Creare/gestire richieste di ripristino                                                                               |
| Amministratore fatturazione         | Visualizza richieste di ripristino<br>Creare/gestire richieste di ripristino<br>Add/Edit/Delete Ship to address(es)                                        |

Per ulteriori informazioni sugli utenti e sulle autorizzazioni, vedere [Panoramica dell'interfaccia di amministrazione di Microsoft.](/microsoft-365/admin/admin-overview/about-the-admin-center)

## <a name="create-and-manage-a-service-order"></a>Creare e gestire un ordine di assistenza

1. Accedere al Centro Amministrazione Microsoft 365 e [https://admin.microsoft.com](https://go.microsoft.com/fwlink/p/?linkid=2024339) accedere con le autorizzazioni di amministratore appropriate. Per altre informazioni, vedere [Who autorizzazioni di amministratore nella mia azienda?](/microsoft-365/business-video/admin-center-overview#who-has-admin-permissions-in-my-business)
2. Vai a **Support**  >  **Surface Device Repairs** e seleziona **Crea richiesta di ripristino.** Se non viene visualizzata questa opzione di ripristino, non si dispone dell'autorizzazione per accedere a questa pagina.

    > [!div class="mx-imgBorder"]
    > ![Avviare la richiesta di ripristino self-service](images/self-serve-fig1.png)

3. Puoi creare una richiesta di ripristino per uno o più dispositivi. Seleziona **Invia 1 dispositivo** alla **** volta o Invia più dispositivi per usare un file .csv per caricare più numeri di serie e seleziona **Avanti.**

    > [!NOTE]
    > **Per più dispositivi:**
    >
    > - Nella pagina Dell'interfaccia di amministrazione scaricare il modello CSV di esempio, aggiungere le informazioni necessarie e salvarle nell'unità locale.
    > - Selezionare **Upload file CSV**per le voci in blocco, selezionare il file .csv salvato nell'unità locale e selezionare **Apri.**
    > - I numeri di serie del dispositivo verranno caricati. Selezionare **Avanti** per continuare la creazione del ripristino.

4. In **Sostituzione spedizione a**selezionare un indirizzo di spedizione. Oppure selezionare **Aggiungi nuovo indirizzo.**

    > [!NOTE]
    >
    > - Le autorizzazioni consentono ad alcuni amministratori di aggiungere una nuova spedizione agli indirizzi. Se si dispone delle autorizzazioni, > aggiungere nuovi indirizzi. Immetti le informazioni necessarie e quindi seleziona  **Salva**.
    > - Il modulo convalida automaticamente le informazioni sull'indirizzo e potrebbe essere corretto apportare modifiche se l'indirizzo non viene riconosciuto dal sistema postale locale. L'indirizzo di posta elettronica viene utilizzato per inviare notifiche e comunicazioni per la richiesta di ripristino.

    > [!div class="mx-imgBorder"]
    > ![
      Aggiungi un nuovo indirizzo
    ](images/self-serve-fig2a.png)

5. Aggiungi dispositivo immettendo il numero di serie del dispositivo nel blocco di testo. Per altre informazioni, vedi Numeri [di serie del dispositivo.](https://support.microsoft.com/help/4036293/surface-find-the-serial-number-on-surface) Se il numero di serie è valido, verranno visualizzate un'immagine e informazioni sul prodotto, tra cui la data della garanzia e il numero di modello. Seleziona **Aggiungi dispositivo** se le informazioni sono corrette.

    > [!div class="mx-imgBorder"]
    > ![Aggiungi dispositivi](images/self-serve-fig2.png)

6. Ripeti i passaggi da 1 a 2 per aggiungere più dispositivi (fino a 20 totali) alla richiesta.
7. Dal menu a discesa seleziona il tipo di problema che meglio descrive il problema e seleziona **Avanti.**

    > [!div class="mx-imgBorder"]
    > ![Seleziona categoria di problema](images/self-serve-fig3.png)

8. Rivedere l'ordine. Se le informazioni non sono corrette, scegliere **Indietro** per correggere gli errori.
9. Accettare i termini delle condizioni.
10. Se il riepilogo delle richieste è corretto, selezionare **Invia la richiesta.**

    > [!div class="mx-imgBorder"]
    > ![Inviare una richiesta di ripristino self-service](images/self-serve-fig4.png)

Quando viene visualizzata la home page, è possibile visualizzare la richiesta di servizio nell'elenco riepilogativo e ricevere un messaggio di posta elettronica di conferma.

## <a name="frequently-asked-questions"></a>Domande frequenti

### <a name="why-am-i-getting-error-code-400-generic-client-service-error-401-unauthorized-service-error-or-error-403-forbidden-service-error"></a>Perché viene visualizzato il codice di errore 400 "Errore del servizio client generico", 401 "Errore di servizio non autorizzato" o l'errore 403 "Errore del servizio non consentito"?

Potrebbe verificarsi un problema con l'account Microsoft 365 o l'utente non dispone delle autorizzazioni per accedere al contenuto. Contatta il tuo amministratore Microsoft 365 per assistenza.

### <a name="when-i-enter-my-shipping-address-and-i-get-an-error-message-that-no-shipping-offers-are-available"></a>Quando si immette l'indirizzo di spedizione e viene visualizzato un messaggio di errore che indica che non sono disponibili offerte di spedizione?

La versione beta Self-Serve Surface Self-Serve e service ha una disponibilità limitata in questo momento. Le offerte saranno disponibili solo se l'indirizzo si trova in uno dei seguenti paesi:

Austria, Bahrain, Belgio, Bulgaria, Croazia, Cipro, Repubblica Ceca, Danimarca, Estonia, Finlandia, Francia, Germania, Grecia, Ungheria, Irlanda, Italia, Kuwait, Lettonia, Lituania, Lussemburgo, Malta, Paesi Bassi, Oman, Polonia, Portogallo, Romania, Slovacchia, Slovenia, Sudafrica, Spagna, Svezia e Regno Unito (escluso l'Irlanda del Nord).

### <a name="where-can-i-see-orders-that-i-have-placed-through-the-microsoft-365-portal"></a>Dove è possibile visualizzare gli ordini effettuati tramite il Microsoft 365 portale?

Vai a [interfaccia di amministrazione di Microsoft 365 - Richieste di servizio](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/support/devicerepairs) e accedi con le credenziali Microsoft 365 servizio.

Gli ordini creati tramite il Servizio Supporto Tecnico Clienti Microsoft non saranno visibili nel Self-Serve garanzia e gestione dei servizi.

### <a name="why-am-i-unable-to-add-edit-or-delete-a-shipping-address"></a>Perché non è possibile aggiungere, modificare o eliminare un indirizzo di spedizione?

La possibilità di aggiungere, modificare o eliminare un indirizzo di spedizione può essere eseguita solo dall'amministratore globale o di fatturazione di Microsoft 365. Contattare l'amministratore per assistenza.  

### <a name="how-can-i-contact-microsoft-support-for-the-surface-self-serve-warranty-and-service-beta"></a>Come posso contattare il supporto Microsoft per la versione beta della garanzia Self-Serve Surface e del servizio?

Puoi contattare il supporto direttamente tramite il modulo di supporto di Surface nell'interfaccia di amministrazione di Microsoft.

1. Accedi all'interfaccia di amministrazione di Microsoft usando le credenziali Microsoft 365 utente.
2. Seleziona **Support**  >  **Surface Device Repairs > Serve assistenza?** e descrivi il problema.
3. Se i risultati non sono utili, selezionare **Contatta il supporto**e immettere una descrizione del problema. Confermare il numero di contatto e l'indirizzo di posta elettronica, selezionare il metodo di contatto preferito e quindi selezionare **Contattami.**

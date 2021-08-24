---
title: Prima installazione per Surface Hub
description: Il termine \ 0034;prima esecuzione \ 0034; si riferisce alla serie di passaggi che dovrai eseguire alla prima accensione del dispositivo Surface Hub e ha lo stesso significato di \ 0034;configurazione guidata \ 0034; (OOBE, Out-Of-Box Experience). Questa sezione descrive dettagliatamente questo processo.
ms.assetid: 07C9E84C-1245-4511-B3B3-75939AD57C49
ms.reviewer: ''
manager: laurawi
keywords: prima esecuzione, Surface Hub, configurazione guidata, out-of-box experience, OOBE
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/17/2021
ms.localizationpriority: medium
ms.openlocfilehash: 95b3e9dceab3304da627807cf28a9e37a5af10d4
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911451"
---
# <a name="first-time-setup-for-surface-hub"></a>Prima installazione per Surface Hub

Al primo avvio Surface Hub, il dispositivo entra automaticamente in modalità di installazione per la prima volta per guidarti nella configurazione dell'account e nelle impostazioni correlate.

> [!TIP]
> Puoi automatizzare l'intero processo di configurazione con un [pacchetto di provisioning](#use-provisioning-packages) per garantire un'esperienza coerente in più Surface Hub.

## <a name="get-started"></a>Introduzione

1. Per impostazione predefinita, Cortana è abilitato per guidare l'utente attraverso il processo. Per disattivare la Cortana assistenza, selezionare l'icona del microfono.

    :::image type="content" source="images/hub-setup-cortana.png" alt-text="Cortana è abilitato per guidare l'utente attraverso il processo.":::

2. **Seleziona la tua regione.** Confermare l'area rilevata automaticamente e selezionare **Sì.**

    :::image type="content" source="images/hub-setup-region.png" alt-text="Seleziona la tua regione.":::

3. **Confermare il layout di tastiera.** Selezionare **Sì**.

    :::image type="content" source="images/hub-setup-keyboard.png" alt-text="Confermare il layout di tastiera.":::

4. Per aggiungere una seconda tastiera, selezionare **Aggiungi layout.** In caso contrario, **selezionare Ignora**.

    :::image type="content" source="images/hub-setup-2keyboard.png" alt-text="Aggiungere una seconda tastiera.":::

5. **Connessione a una rete.** Se è già stato collegato un cavo Ethernet, Surface Hub si connette automaticamente alla rete. In alternativa, è possibile connettersi a una rete wireless. **Nota:** Non è possibile connettersi a una rete wireless negli hotspot (portali captive) che reindirizzano le richieste di accesso al sito Web di un provider. Seleziona **Avanti**.

    :::image type="content" source="images/hub-setup-network.png" alt-text="Connessione a una rete.":::

6. **Accettare Windows 10 di licenza.** Selezionare **Accetta**.

    :::image type="content" source="images/hub-setup-license.png" alt-text="Accettare Windows 10 di licenza.":::

7. **Immetti informazioni sull'account** del dispositivo usando un indirizzo UPN (user@contoso.com) o un indirizzo di dominio di livello inferiore (CONTOSO\utente). Utilizzare il formato corrispondente all'ambiente e immettere la password.

    :::image type="content" source="images/hub-setup-device-account.png" alt-text="Immetti informazioni sull'account del dispositivo.":::

| Ambiente                                              | Formato richiesto per l'account del dispositivo |
| -------------------------------------------------------- | ---------------------------------- |
| L'account del dispositivo è ospitato solo online                     | username@contoso.com               |
| L'account del dispositivo è ospitato solo in locale                | CONTOSO\user                       |
| L'account del dispositivo è ospitato online e locale (ibrido) | CONTOSO\user                       |

>[!NOTE]
>Anche se puoi ignorare la configurazione di un account del dispositivo, il dispositivo non sarà completamente integrato nell'infrastruttura. Se non esegui la procedura di configurazione in questa fase, puoi aggiungere un account del dispositivo in seguito tramite l'app Impostazioni.

8. **Immettere la password** e selezionare **Avanti.**

9. Surface Hub rileva automaticamente Exchange server e indirizzo SIP dal dominio immesso nel passaggio precedente. Se necessario, fornire l'indirizzo Exchange server e selezionare **Avanti.**

    :::image type="content" source="images/hub-setup-exchange.png" alt-text="Exchange server e indirizzo SIP.":::

10. **Assegnare un nome al dispositivo.** Immetti un nome per il dispositivo o usa quello suggerito. **Selezionare Avanti**.

    :::image type="content" source="images/hub-setup-name.png" alt-text="Assegnare un nome al dispositivo.":::

- Il **nome descrittivo** è visibile nell'angolo in basso a sinistra di Surface Hub 2S e viene visualizzato durante la proiettata sul dispositivo.
- Il **nome del dispositivo** identifica il dispositivo quando è affiliato ad Active Directory o Azure Active Directory e durante la registrazione del dispositivo con Intune.

>[!NOTE]
>Se desideri abilitare [Miracast su infrastruttura](miracast-over-infrastructure.md), il nome del dispositivo deve essere rilevabile tramite DNS. Puoi ottenere questo consentendo al dispositivo Surface Hub di registrarsi automaticamente tramite DNS dinamico o creando manualmente un record A o AAAA per il nome del dispositivo di Surface Hub.

### <a name="configure-device-admin-accounts"></a>Configurare gli account di amministratore del dispositivo

Puoi configurare gli amministratori dei dispositivi solo durante la prima installazione. Per ulteriori informazioni, fai riferimento a:

- [Surface Hub'affiliazione di dispositivi 2S](/surface-hub/prepare-your-environment-for-surface-hub#device-affiliation)
- [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md)

1. **Scegliere il tipo di account amministratore.** Selezionare una delle opzioni seguenti: Servizi di dominio Active Directory, Azure Active Directory o Amministratore locale.

    :::image type="content" source="images/hub-setup-join.png" alt-text="Scegliere il tipo di account amministratore.":::

### <a name="active-directory-domain-services"></a>Active Directory Domain Services

1. Se si intende utilizzare Surface Hub in un ambiente locale, è possibile consociare Hub a Servizi di **dominio Active Directory.**  Immettere le credenziali di un utente che dispone delle autorizzazioni per aggiungere il dispositivo ad Active Directory.
2. Selezionare il gruppo di sicurezza di Active Directory contenente i membri autorizzati ad accedere all'app Impostazioni in Surface Hub 2S.
3. Selezionare **Fine.** Il dispositivo viene ora riavviato.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

1. Se intendi gestire i Surface Hub dal cloud usando Microsoft Intune o un provider MDM, **seleziona Microsoft Azure Active Directory**.
2. Seleziona Avanti e accedi con un account aziendale o dell'istituto di istruzione. Se reindirizzato, eseguire l'autenticazione utilizzando la pagina di accesso dell'organizzazione e fornire credenziali aggiuntive, se richiesto. In caso contrario, immettere la password e selezionare **Avanti.**

    :::image type="content" source="images/hub-setup-signin.png" alt-text="Accedi con l'account aziendale o dell'istituto di istruzione.":::

>[!NOTE]
>Per configurare chi può usare l'app Impostazioni per l'amministrazione di Surface Hub, assicurati che la registrazione automatica di Intune sia abilitata nel tenant prima di aggiungere il dispositivo ad Azure AD. I criteri di Intune possono quindi essere usati [per configurare gli](surface-hub-2s-nonglobal-admin.md) amministratori non globali nei dispositivi Surface Hub.

### <a name="local-administrator-account"></a>Account amministratore locale

- Immettere un nome utente e una password memorabile per l'amministratore locale. [](surface-hub-2s-recover-reset.md) Se si dimentica la password dell'amministratore locale, sarà necessario recuperare il dispositivo e ripetere il processo di configurazione.  

    :::image type="content" source="images/hub-setup-local-admin.png" alt-text="Immettere una password memorabile per l'account amministratore locale.":::

### <a name="choose-privacy-settings-for-your-device"></a>Scegliere le impostazioni di privacy per il dispositivo

- Selezionare una delle impostazioni di privacy disponibili e selezionare **Accetta.**

    :::image type="content" source="images/hub-setup-privacy.png" alt-text="Scegliere le impostazioni di privacy.":::

### <a name="use-provisioning-packages"></a>Usare pacchetti di provisioning

Puoi personalizzare le opzioni di configurazione per la prima volta, consentendoti di garantire un'esperienza coerente in più Dispositivi Surface Hub.

1. Per iniziare, consulta la documentazione in Creare pacchetti [di provisioning](provisioning-packages-for-surface-hub.md) e salvare il pacchetto di provisioning in un'unità usb thumb.
2. Inserisci l'unità usb thumb in una delle porte USB prima di iniziare il processo di installazione.
3. Quando richiesto, scegli il pacchetto di provisioning che vuoi usare.
4. Se hai creato un file CSV per più dispositivi, potrai scegliere una configurazione del dispositivo.
5. Seguire le istruzioni per completare la prima installazione.

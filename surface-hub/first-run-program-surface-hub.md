---
title: Configurazione della prima volta per Surface Hub
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
ms.openlocfilehash: 551867ccbb041fe292d9ec60f38bb89acfbc764e
ms.sourcegitcommit: b922aaf7287bdfb99f848aad455b2b4001b8f5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2022
ms.locfileid: "12472446"
---
# <a name="first-time-setup-for-surface-hub"></a>Configurazione della prima volta per Surface Hub

Quando si avvia per la prima volta Surface Hub, il dispositivo entra automaticamente in modalità di installazione per la prima volta per guidare l'utente nella configurazione dell'account e nelle impostazioni correlate.

> [!TIP]
> È possibile automatizzare l'intero processo di installazione con un [pacchetto di provisioning](#use-provisioning-packages) per garantire un'esperienza coerente tra più Surface Hub.

## <a name="get-started"></a>Informazioni di base

1. Per impostazione predefinita, Cortana è abilitato per guidare l'utente durante il processo. Per disattivare Cortana assistenza, selezionare l'icona del microfono.

    :::image type="content" source="images/hub-setup-cortana.png" alt-text="Cortana è abilitato per guidare l'utente durante il processo.":::

2. **Seleziona la tua regione.** Confermare l'area rilevata automaticamente e selezionare **Sì**.

    :::image type="content" source="images/hub-setup-region.png" alt-text="Seleziona la tua regione.":::

3. **Confermare il layout della tastiera.** Selezionare **Sì**.

    :::image type="content" source="images/hub-setup-keyboard.png" alt-text="Confermare il layout della tastiera.":::

4. Per aggiungere una seconda tastiera, selezionare **Aggiungi layout**. In caso contrario, selezionare **Ignora**.

    :::image type="content" source="images/hub-setup-2keyboard.png" alt-text="Aggiungere una seconda tastiera.":::

5. **Connessione a una rete.** Se è già stato collegato un cavo Ethernet, Surface Hub si connette automaticamente alla rete. In alternativa, è possibile connettersi a una rete wireless. **Nota:** Non è possibile connettersi a una rete wireless negli hotspot (portali vincolati) che reindirizzano le richieste di accesso al sito Web di un provider. Seleziona **Avanti**.

    :::image type="content" source="images/hub-setup-network.png" alt-text="Connessione a una rete.":::

6. **Accettare Windows 10 contratto di licenza.** Selezionare **Accetta**.

    :::image type="content" source="images/hub-setup-license.png" alt-text="Accettare Windows 10 contratto di licenza.":::

7. **Immettere le informazioni sull'account del dispositivo** usando un indirizzo UPN (user@contoso.com) o un indirizzo di dominio di livello inferiore (CONTOSO\utente). Usare il formato corrispondente all'ambiente e immettere la password.

    :::image type="content" source="images/hub-setup-device-account.png" alt-text="Immettere le informazioni sull'account del dispositivo.":::

| Ambiente                                              | Formato richiesto per l'account del dispositivo |
| -------------------------------------------------------- | ---------------------------------- |
| L'account del dispositivo è ospitato solo online                     | username@contoso.com               |
| L'account del dispositivo è ospitato solo in locale                | CONTOSO\utente                       |
| L'account del dispositivo è ospitato online e locale (ibrido) | CONTOSO\utente                       |

>[!NOTE]
>Anche se è possibile ignorare la configurazione di un account del dispositivo, il dispositivo non sarà completamente integrato nell'infrastruttura. Se non esegui la procedura di configurazione in questa fase, puoi aggiungere un account del dispositivo in seguito tramite l'app Impostazioni.

8. **Immettere la password** e selezionare **Avanti.**

9. Surface Hub rileva automaticamente Exchange informazioni sul server e sull'indirizzo SIP dal dominio immesso nel passaggio precedente. In alternativa, se necessario, specificare l'indirizzo del server Exchange e selezionare **Avanti**.

    :::image type="content" source="images/hub-setup-exchange.png" alt-text="Exchange server e l'indirizzo SIP.":::

10. **Assegnare al dispositivo il nome .** Immettere un nome per il dispositivo o usare quello suggerito. **Selezionare Avanti**.

    :::image type="content" source="images/hub-setup-name.png" alt-text="Assegnare al dispositivo il nome .":::

- Il **nome descrittivo** è visibile nell'angolo inferiore sinistro di Surface Hub 2S e viene visualizzato durante la proiezione al dispositivo.
- Il **nome del** dispositivo identifica il dispositivo quando è associato ad Active Directory o Azure Active Directory e quando registra il dispositivo con Intune.

>[!IMPORTANT]
>Se si prevede di distribuire il Surface Hub con Active Directory, il nome del dispositivo deve soddisfare [i requisiti standard per i nomi di computer in Active Directory, in](/troubleshoot/windows-server/identity/naming-conventions-for-computer-domain-site-ou#computer-names) caso contrario l'installazione avrà esito negativo.

>[!NOTE]
>Se desideri abilitare [Miracast su infrastruttura](miracast-over-infrastructure.md), il nome del dispositivo deve essere rilevabile tramite DNS. Puoi ottenere questo consentendo al dispositivo Surface Hub di registrarsi automaticamente tramite DNS dinamico o creando manualmente un record A o AAAA per il nome del dispositivo di Surface Hub.

### <a name="configure-device-admin-accounts"></a>Configurare gli account amministratore del dispositivo

È possibile configurare gli amministratori del dispositivo solo durante la prima installazione. Per ulteriori informazioni, fai riferimento a:

- [Surface Hub l'affiliazione del dispositivo 2S](/surface-hub/prepare-your-environment-for-surface-hub#device-affiliation)
- [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md)

1. **Scegliere il tipo di account amministratore.** Selezionare una delle opzioni seguenti: Active Directory Domain Services, Azure Active Directory o Amministratore locale.

    :::image type="content" source="images/hub-setup-join.png" alt-text="Scegliere il tipo di account amministratore.":::

### <a name="active-directory-domain-services"></a>Active Directory Domain Services

1. Se si intende usare Surface Hub in un ambiente locale, è possibile associare Hub con **Active Directory Domain Services**.  Immettere le credenziali di un utente che dispone delle autorizzazioni per aggiungere il dispositivo ad Active Directory.
2. Selezionare il gruppo di sicurezza di Active Directory contenente i membri autorizzati ad accedere all'app Impostazioni in Surface Hub 2S.
3. Selezionare **Fine**. Il dispositivo viene ora riavviato.

### <a name="microsoft-azure-active-directory"></a>Microsoft Azure Active Directory

1. Se si intende gestire Surface Hub dal cloud usando Microsoft Intune o un provider MDM, selezionare **Microsoft Azure Active Directory**.
2. Selezionare Avanti e accedere con un account aziendale o dell'istituto di istruzione. Se reindirizzato, eseguire l'autenticazione usando la pagina di accesso dell'organizzazione e fornire credenziali aggiuntive, se richiesto. In caso contrario, immettere la password e selezionare **Avanti.**

    :::image type="content" source="images/hub-setup-signin.png" alt-text="Accedere con l'account aziendale o dell'istituto di istruzione.":::

>[!NOTE]
>Per configurare chi può usare l'app Impostazioni per amministrare Surface Hub, assicurarsi che la registrazione automatica Intune sia abilitata nel tenant prima di aggiungere il dispositivo a Azure AD. Intune criteri possono quindi essere usati per [configurare amministratori non globali](surface-hub-2s-nonglobal-admin.md) in Surface Hubs.

### <a name="local-administrator-account"></a>Account amministratore locale

- Immettere un nome utente e una password memorabile per l'amministratore locale. Se si dimentica la password dell'amministratore locale, sarà necessario [ripristinare il dispositivo](surface-hub-2s-recover-reset.md) e ripetere il processo di installazione.  

    :::image type="content" source="images/hub-setup-local-admin.png" alt-text="Immettere una password memorabile per l'account amministratore locale.":::

### <a name="choose-privacy-settings-for-your-device"></a>Scegliere le impostazioni di privacy per il dispositivo

- Selezionare tra le impostazioni di privacy disponibili e selezionare **Accetta.**

    :::image type="content" source="images/hub-setup-privacy.png" alt-text="Scegliere le impostazioni di privacy.":::

### <a name="use-provisioning-packages"></a>Usare i pacchetti di provisioning

Puoi personalizzare le opzioni di configurazione per la prima volta, consentendoti di garantire un'esperienza coerente tra più Surface Hub.

1. Per iniziare, esaminare la documentazione in [Creare pacchetti di provisioning](provisioning-packages-for-surface-hub.md) e salvare il pacchetto di provisioning in un'unità usb.
2. Inserire l'unità usb usb in una delle porte USB quando viene visualizzata la pagina Del contratto di licenza (passaggio 6 nella procedura di configurazione precedente).
3. Quando richiesto, scegliere il pacchetto di provisioning da usare.
4. Se è stato creato un file CSV per più dispositivi, sarà possibile scegliere una configurazione del dispositivo.
5. Seguire le istruzioni per completare la prima installazione.

---
title: Prima installazione per Surface Hub 2S
description: Scopri come completare la prima installazione per Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 9cbce8bf0cc9c729af4cd052167fef016197274f
ms.sourcegitcommit: 8b35cdee6c638359403697711ee53d07cca6ee51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2021
ms.locfileid: "11442194"
---
# <a name="first-time-setup-for-surface-hub-2s"></a>Prima installazione per Surface Hub 2S

Al primo avvio di Surface Hub 2S, il dispositivo entra automaticamente in modalità di installazione per la prima volta per guidarti nella configurazione dell'account e nelle impostazioni correlate.

## <a name="configuring-surface-hub-2s-account"></a>Configurazione dell'account Surface Hub 2S

1. **Configurare le impostazioni locali.** Immetti informazioni su area geografica, lingua, layout di tastiera e fuso orario. Seleziona **Avanti**.

   ![* Configurare le impostazioni locali *](images/sh2-run1.png)

1. **Connettersi a una rete wireless.** Scegliere la rete wireless preferita e selezionare **Avanti.**

   - Questa opzione non viene visualizzata se è collegata tramite un cavo Ethernet.

   - Non è possibile connettersi a una rete wireless negli hotspot (portali captive) che reindirizzano le richieste di accesso al sito Web di un provider.

3. **Immetti le informazioni sull'account del dispositivo.** Usa **dominio\utente** per ambienti locali e ibridi e **user\@example.com** per gli ambienti online. Selezionare **Avanti.**

   ![* Immettere informazioni sull'account del dispositivo *](images/sh2-run2.png)

1. **Immetti informazioni aggiuntive.** Se richiesto, fornire l'indirizzo del server Exchange e quindi selezionare **Avanti.**

   ![* Immetti altre info; ad esempio, Nome server Exchange*](images/sh2-run3.png)

1. **Assegnare un nome al dispositivo.** Immetti un nome per il dispositivo o usa quello suggerito in base al nome visualizzato dell'account e al nome del principio utente [UPN]. **Selezionare Avanti**.

   - Il **nome descrittivo** è visibile nell'angolo in basso a sinistra di Surface Hub 2S e viene visualizzato quando si proietta sul dispositivo.

   - Il **nome del dispositivo** identifica il dispositivo quando è affiliato ad Active Directory o Azure Active Directory e durante la registrazione del dispositivo con Intune.

   ![* Assegnare un nome al dispositivo*](images/sh2-run4.png)
 

## <a name="configuring-device-admin-accounts"></a>Configurazione degli account di amministratore del dispositivo

Puoi configurare gli amministratori dei dispositivi solo durante la prima installazione. Per altre informazioni, fai riferimento a Affiliazione di dispositivi [Surface Hub 2S.](https://docs.microsoft.com/surface-hub/prepare-your-environment-for-surface-hub#device-affiliation)

Nella finestra **Setup admins for this device** selezionare una delle opzioni seguenti: Servizi di dominio Active Directory, Azure Active Directory o Amministratore locale.

![* Amministratori dell'installazione per questo dispositivo *](images/sh2-run5.png)

### <a name="active-directory-domain-services"></a>Active Directory Domain Services

1. Immettere le credenziali di un utente che dispone delle autorizzazioni per aggiungere il dispositivo ad Active Directory.

    ![* Configurare gli amministratori con l'aggiunta al dominio *](images/sh2-run6.png)

2. Seleziona il gruppo di sicurezza di Active Directory contenente i membri autorizzati ad accedere all'app Impostazioni in Surface Hub 2S.

   ![* Immettere un gruppo di sicurezza *](images/sh2-run7.png)

1. Selezionare **Fine.** Il dispositivo viene ora riavviato.

### <a name="azure-active-directory"></a>Azure Active Directory

Quando si sceglie di consociare il dispositivo con Azure Active Directory, il dispositivo verrà riavviato immediatamente e verrà visualizzata la pagina seguente.

![* Se l'organizzazione usa Office 365 o altri servizi aziendali di Microsoft, questo dispositivo verrà registrato con l'organizzazione*](images/sh2-run8.png)

1. Seleziona **Avanti**.

1. Immetti l'indirizzo di posta elettronica o l'UPN di un account **con Intune Piano 1** o versione successiva e quindi seleziona **Avanti.**

   ![* Immettere l'account aziendale o dell'istituto di istruzione*](images/sh2-run9.png)

1. Se reindirizzato, eseguire l'autenticazione utilizzando la pagina di accesso dell'organizzazione e fornire ulteriori informazioni di accesso, se richiesto. Il dispositivo viene ora riavviato.

## <a name="local-administrator-account"></a>Account amministratore locale

- Immettere un nome utente e una password per l'amministratore locale. Il dispositivo verrà riavviato.

  ![* Configurare un account amministratore*](images/sh2-run10.png)
 
## <a name="using-provisioning-packages"></a>Uso dei pacchetti di provisioning

Se inserisci un'unità usb con un pacchetto di provisioning in una delle porte USB all'avvio di Surface Hub 2S, il dispositivo visualizza la pagina seguente.

1. Immetti le impostazioni richieste e seleziona **Configura**.

   ![* Immettere le impostazioni internazionali per il pacchetto di provisioning*](images/sh2-run11.png)

   ![* Effettuare il provisioning di questo dispositivo da supporti rimovibili*](images/sh2-run12.png)

2. Scegli il pacchetto di provisioning che vuoi usare.

   ![* Scegliere il pacchetto di provisioning da usare*](images/sh2-run13.png)

3. Se hai creato un file CSV per più dispositivi, potrai scegliere una configurazione del dispositivo. Per altre informazioni, fai riferimento a Creare pacchetti [di provisioning per Surface Hub 2S.](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file)

   ![* Selezionare un account del dispositivo e un nome descrittivo dal file di configurazione*](images/sh2-run14.png)

4. Seguire le istruzioni per completare la prima installazione.

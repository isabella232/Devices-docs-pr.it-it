---
title: Configurazione per la prima volta per Surface Hub 2S
description: Informazioni su come completare la configurazione per la prima volta per Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/03/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 47a393944c1b524931a6ac56962cc2cd60786007
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833609"
---
# Configurazione per la prima volta per Surface Hub 2S

Quando si avvia Surface Hub 2S per la prima volta, il dispositivo entra automaticamente nella modalità di configurazione iniziale per guidarti attraverso la configurazione dell'account e le impostazioni correlate.

## Configurazione dell'account di Surface Hub 2S

1. **Configurare le impostazioni locali.** Immettere le informazioni relative a area, lingua, layout di tastiera e fuso orario. Seleziona **Avanti**.

   ![* Configurare le impostazioni locali *](images/sh2-run1.png) <br>
1. **Connettersi a una rete wireless.** Scegliere la rete wireless preferita e quindi fare clic su **Avanti.**

- Questa opzione non viene visualizzata se connessa tramite un cavo Ethernet.
- Non è possibile connettersi a una rete wireless in hotspot (portali captive) che reindirizza le richieste di accesso al sito Web del provider.

3. **Immettere le informazioni sull'account del dispositivo.** USA **dominio\utente** per ambienti locali e ibridi e per gli **utenti \ @example. com** per gli ambienti online. Selezionare **Avanti.**

   ![* Immettere le informazioni sull'account del dispositivo *](images/sh2-run2.png) <br>
1. **Immettere altre informazioni.** Se richiesto, specificare l'indirizzo del server di Exchange e quindi selezionare **Avanti.**

    ![* Immettere altre info; ad esempio, Exchange Server Name *](images/sh2-run3.png) <br>

1. **Assegnare un nome al dispositivo.** Immettere un nome per il dispositivo oppure usare quello suggerito in base al nome visualizzato dell'account e al nome del principio utente [UPN]. **Selezionare Avanti**.

- Il **nome descrittivo** è visibile nell'angolo in basso a sinistra di Surface Hub 2S e viene visualizzato durante la proiezione al dispositivo.

- Il **nome del dispositivo** identifica il dispositivo quando è affiliato a Active Directory o Azure Active Directory e quando si iscrive il dispositivo con Intune.

  ![* Assegnare un nome al dispositivo *](images/sh2-run4.png) <br>
 
## Configurazione degli account di amministratore del dispositivo

È possibile configurare gli amministratori del dispositivo solo durante la configurazione per la prima volta. Per altre informazioni, vedere [affiliazione al dispositivo Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-prepare-environment#device-affiliation).

 Nella finestra di **dialogo amministratori per il dispositivo** selezionare una delle opzioni seguenti: Servizi di dominio Active Directory, Azure Active Directory o amministratore locale.

   ![* Amministratori configurazione per questo dispositivo *](images/sh2-run5.png) <br>

### Active Directory Domain Services

1. Immettere le credenziali di un utente che dispone delle autorizzazioni necessarie per accedere al dispositivo ad Active Directory.

    ![* Amministratori configurazione con Domain Join *](images/sh2-run6.png) <br>

2. Selezionare il gruppo di sicurezza di Active Directory contenente i membri autorizzati ad accedere all'app impostazioni in Surface Hub 2S.

    ![* Immettere un gruppo di sicurezza *](images/sh2-run7.png) <br>
1. Selezionare **fine**. Il dispositivo verrà riavviato.

### Azure Active Directory

Quando si sceglie di affiliare il dispositivo con Azure Active Directory, il dispositivo verrà immediatamente riavviato e visualizzato nella pagina seguente. Seleziona **Avanti**.

![* Se l'organizzazione usa Office 365 o altri servizi commerciali da Microsoft, questo dispositivo verrà registrato con l'organizzazione *](images/sh2-run8.png) <br>

1. Immettere l'indirizzo di posta elettronica o l'UPN di un account **con Intune piano 1** o superiore e quindi selezionare **Avanti.**

    ![* Immettere l'account di lavoro o dell'Istituto di istruzione *](images/sh2-run9.png) <br>

2. Se viene reindirizzato, eseguire l'autenticazione usando la pagina di accesso dell'organizzazione e specificare altre informazioni di accesso, se richiesto. Il dispositivo verrà riavviato.

## Account di amministratore locale

- Immettere un nome utente e una password per l'amministratore locale. Il dispositivo verrà riavviato.

     ![* Configurare un account di amministratore *](images/sh2-run10.png) <br>
 
## Uso di pacchetti di provisioning

Se si inserisce un'unità thumb USB con un pacchetto di provisioning in una delle porte USB quando si avvia Surface Hub 2S, il dispositivo Visualizza la pagina seguente.

1. Immettere le impostazioni richieste e selezionare **Configura**.

    ![* Immettere le impostazioni internazionali per il pacchetto di provisioning *](images/sh2-run11.png) <br>

    ![* Eseguire il provisioning del dispositivo da un supporto rimovibile *](images/sh2-run12.png) <br>
2. Scegliere il pacchetto di provisioning che si vuole usare.

   ![* Scegliere il pacchetto di provisioning da usare *](images/sh2-run13.png) <br>

3. Se è stato creato un file CSV con più dispositivi, sarà possibile scegliere una configurazione del dispositivo. Per altre informazioni, vedere [creare pacchetti di provisioning per Surface Hub 2S](https://docs.microsoft.com/surface-hub/surface-hub-2s-deploy#provisioning-multiple-devices-csv-file).


    ![* Selezionare un account di dispositivo e un nome descrittivo dal file di configurazione *](images/sh2-run14.png) <br>

4. Seguire le istruzioni per completare la configurazione per la prima volta.

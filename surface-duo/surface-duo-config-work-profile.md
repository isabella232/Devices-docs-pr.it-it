---
title: Configurare il profilo di lavoro Android Enterprise per Surface Duo
description: Questo articolo spiega come configurare il profilo di lavoro in Surface Duo.
ms.technology: windows
ms.prod: surface
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/25/2020
ms.reviewer: karand
manager: laurawi
ms.audience: itpro
audience: ITPro
ms.localizationpriority: medium
appliesto:
- Surface Duo
ms.openlocfilehash: 380c5fc625983119a516f5d0e2294af70e0dbd29
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911201"
---
# <a name="configure-android-enterprise-work-profile-for-surface-duo"></a>Configurare il profilo di lavoro Android Enterprise per Surface Duo

Destinati alle distribuzioni BYOD, i profili di lavoro offrono uno spazio separato in Duo per le app e i dati di lavoro, offrendo alle organizzazioni il controllo completo dei propri dati, app e criteri di sicurezza senza impedire ai dipendenti di usare il proprio dispositivo per le app e i dati personali.

### <a name="set-up-android-enterprise-work-profile"></a>Configurare il profilo di Enterprise Android

Usa i profili di lavoro per gestire i dati aziendali e le app nei dispositivi Android di proprietà dell'utente. Per impostazione predefinita, la registrazione dei dispositivi del profilo di lavoro di proprietà personale è abilitata e non richiede ulteriori configurazioni dell'amministratore.  

**Per abilitare Enterprise profilo di lavoro:**

- In Endpoint Manager, seleziona **Dispositivi**  >  **registrazione Android**  >  **Android** e quindi seleziona Dispositivi **personali con profilo di lavoro.**
<br><br>
 ![Abilita Enterprise profilo di lavoro.](images/enroll-start.png)

 
**Accedi a Surface Duo con Il profilo di lavoro Enterprise Android**

1. Installa l Portale aziendale app da Google Play Store e accedi con il tuo account aziendale o dell'istituto di istruzione Microsoft.<br><br>
![Accedi a Surface Duo.](images/duo-wp-1.png)
 
2. Nella pagina Installazione di Access selezionare **Avvia**.<br><br>
![Iniziare.](images/duo-wp-2.png)

3. Esaminare le informazioni nella pagina privacy e selezionare **Continua.**<br><br>
 ![Continua.](images/duo-wp-3.png)
<br><br>
 ![Selezionare continua.](images/duo-wp-4.png)
 
4. Al termine della configurazione del profilo di lavoro, seleziona **Continua** per attivare e registrare il dispositivo.<br><br>
 ![Seleziona continua per attivare e registrare il dispositivo.](images/duo-wp-5.png)

5. Seleziona **Continua**.<br><br>
 ![Selezionare continua di nuovo.](images/duo-wp-6.png)

6. Dopo aver attivato il profilo di lavoro, seleziona **Continua** per aggiornare le impostazioni del dispositivo. In questo esempio, il profilo di lavoro applica un'impostazione MDM per richiedere una password alfanumerica a 6 cifre più complessa. <br><br>

     ![Password alfanumerica di esempio.](images/duo-wp-7.png)<br><br>
7. Selezionare **Risolvi** per immettere l'autenticazione necessaria e quindi **selezionare Continua** per completare la configurazione del profilo di lavoro. <br><br>
     ![Selezionare continua per completare l'installazione.](images/duo-wp-8.png)<br><br>
     ![completare l'installazione.](images/duo-wp-9.png)<br><br>

## <a name="learn-more"></a>Scopri di più

- [Configurare la registrazione dei dispositivi del profilo Enterprise Android](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)


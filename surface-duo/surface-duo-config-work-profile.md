---
title: Configurare il profilo di lavoro Android Enterprise per Surface Duo
description: Questo articolo illustra come configurare il profilo di lavoro in Surface Duo.
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
ms.openlocfilehash: 393844a4e4f0f06f16d11d1313ec9aacfa109d57
ms.sourcegitcommit: 37e0994e2b8ae62b0352b016b698edcc7ca500fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/10/2021
ms.locfileid: "11326193"
---
# Configurare il profilo di lavoro Android Enterprise per Surface Duo

Mirate alle distribuzioni di BYOD, i profili di lavoro offrono uno spazio separato in duo per le app e i dati di lavoro, offrendo alle organizzazioni il controllo completo dei loro dati, delle app e i criteri di sicurezza senza impedire ai dipendenti di usare il loro dispositivo per le app e i dati personali.

###  <a name="set-up-android-enterprise-work-profile"></a>Configurare il profilo di lavoro aziendale Android

Usare i profili di lavoro per gestire i dati aziendali e le app nei dispositivi Android di proprietà dell'utente. Per impostazione predefinita, la registrazione dei dispositivi di profili di lavoro personali è abilitata e non richiede ulteriori configurazioni di amministratore.  

**Per abilitare il profilo di lavoro aziendale:**

- In Endpoint Manager selezionare **Devices**  >  **Android per**  >  **la registrazione** e quindi selezionare **dispositivi personali con il profilo lavoro**.
<br><br>
 ![Abilitare il profilo di lavoro aziendale](images/enroll-start.png)

 
**Accedere a Surface Duo con il profilo di lavoro Android Enterprise**

1. Installare l'app portale aziendale da Google Play Store ed eseguire l'accesso con l'account Microsoft Work o dell'Istituto di istruzione.<br><br>
![Accedere a Surface Duo](images/duo-wp-1.png)
 
2. Nella pagina Configurazione di Access selezionare **inizia**.<br><br>
![Iniziare](images/duo-wp-2.png)

3. Esaminare le informazioni nella pagina privacy e selezionare **continue**.<br><br>
 ![Continua](images/duo-wp-3.png)
<br><br>
 ![Selezionare continua](images/duo-wp-4.png)
 
4. Al termine della configurazione del profilo di lavoro, selezionare **continua** per attivare e registrare il dispositivo.<br><br>
 ![Selezionare continua per attivare e registrare il dispositivo](images/duo-wp-5.png)

5. Seleziona **Continua**.<br><br>
 ![Selezionare continua di nuovo](images/duo-wp-6.png)

6. Dopo aver attivato il profilo di lavoro, selezionare **continua** per aggiornare le impostazioni del dispositivo. In questo esempio, il profilo di lavoro applica un'impostazione MDM per richiedere una password alfanumerica a 6 cifre più forte. <br><br>

     ![Esempio di password alfanumerica](images/duo-wp-7.png)<br><br>
7. Selezionare **Risolvi** per immettere l'autenticazione necessaria e quindi selezionare **continua** per completare la configurazione del profilo di lavoro. <br><br>
     ![Selezionare continua per completare la configurazione](images/duo-wp-8.png)<br><br>
     ![configurazione completa](images/duo-wp-9.png)<br><br>

##  <a name="learn-more"></a>Altre informazioni

- [Configurare la registrazione dei dispositivi di profilo aziendale di Android](https://docs.microsoft.com/mem/intune/enrollment/android-work-profile-enroll)


---
title: Accedere a Surface Hub con Microsoft Authenticator
description: Utilizza Microsoft Authenticator nel tuo dispositivo mobile per l'accesso a Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/28/2017
ms.reviewer: ''
manager: laurawi
localizationpriority: medium
ms.openlocfilehash: e07591a25958677fb6efd5411d75f8b8e1549fed
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11912021"
---
# <a name="sign-in-to-surface-hub-with-microsoft-authenticator"></a>Accedere a Surface Hub con Microsoft Authenticator

Gli utenti dell'organizzazione possono accedere a un dispositivo Surface Hub senza password utilizzando l'app Microsoft Authenticator disponibile su Android e iOS.

## <a name="organization-prerequisites"></a>Prerequisiti dell'organizzazione

Per consentire agli utenti dell'organizzazione di accedere a Surface Hub con i loro telefoni e altri dispositivi anziché con una password, devi assicurarti che l'organizzazione soddisfi questi prerequisiti: 

- L'organizzazione deve essere un'organizzazione ibrida o solo cloud, supportato da Azure Active Directory (Azure AD). Per altre informazioni, vedi [Informazioni su Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).

- Assicurati di disporre almeno di una sottoscrizione di Office 365 E3. 

- [Configura Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings). Assicurati che **Notifica tramite app mobile** sia selezionato. 

    ![opzioni di autenticazione a più fattori.](images/mfa-options.png)

- Abilitare l'hosting del contenuto nei servizi di Azure AD, ad esempio Office, SharePoint e così via. 

- In Surface Hub deve essere in esecuzione Windows 10, versione 1703 o successiva.

- Surface Hub è configurato con un account locale o di dominio.

## <a name="individual-prerequisites"></a>Singoli prerequisiti

- Un telefono Android in cui è in esecuzione la versione 6.0 o successiva oppure un iPhone o iPad in cui è in esecuzione iOS9 o versione successiva 

- La versione più recente dell'app Microsoft Authenticator dell'archivio di app appropriate

    >[!NOTE]
    >In iOS, la versione dell'app deve essere 5.4.0 o successiva.
    >
    >L'app Microsoft Authenticator su telefoni in cui è in esecuzione un sistema operativo Windows non può essere utilizzata per accedere a Surface Hub.

- Il passcode o il blocco per lo schermo nel tuo dispositivo è abilitato

## <a name="how-to-set-up-the-microsoft-authenticator-app"></a>Come usare l'app Microsoft Authenticator

>[!NOTE]
>Se il portale aziendale è installato nel dispositivo Android, disinstallalo prima di configurare Microsoft Authenticator. Dopo aver configurato l'app, puoi reinstallare il portale aziendale.
>
>Se hai già impostato Microsoft Authenticator nel tuo telefono e registrato il dispositivo, vai alle istruzioni di accesso.

1. Aggiungi l'account aziendale o dell'istituto didattico a Microsoft Authenticator per Multi-Factor Authentication. Ti servirà un codice QR fornito dal reparto IT. Per altre informazioni, vedi [Introduzione all'app Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).
2. Vai a **Impostazioni** e registra il dispositivo.
3. Torna alla pagina degli account e scegli **Abilita l'accesso telefonico** dal menu a discesa dell'account.

## <a name="how-to-sign-in-to-surface-hub-during-a-meeting"></a>Come eseguire l'accesso a Surface Hub durante una riunione

1. Dopo aver impostato una riunione, vai a Surface Hub e seleziona **Accedi per visualizzare i file e le riunioni**.

    >[!NOTE]
    >Se non sei sicuro di come pianificare una riunione su un dispositivo Surface Hub, vedi [Pianificare un Surface hub](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting).

    ![Screenshot of Sign in option on Surface Hub.](images/sign-in.png)

2. Vedrai un elenco degli utenti invitati alla riunione. Seleziona te stesso (o la persona che vuole accedere, assicurati che questa persona abbia eseguito la procedura per configurare il proprio dispositivo prima della riunione), quindi **Continua**.

    ![Screenshot dell'elenco dei partecipanti a una riunione.](images/attendees.png)

    Vedrai un codice su Surface Hub.

    ![Screenshot del codice per Approvare l'accesso.](images/approve-signin.png)

3. Per approvare l'accesso, apri l'app Authenticator, immetti il codice a quattro cifre che viene visualizzato in Surface Hub e seleziona **Approva**. Ti verrà quindi chiesto di immettere il PIN o di usare l'impronta digitale per completare l'accesso. 

    ![Screenshot of the Approve sign-in screen in Microsoft Authenticator.](images/approve-signin2.png)

Ora puoi accedere a tutti i file tramite l'app OneDrive.

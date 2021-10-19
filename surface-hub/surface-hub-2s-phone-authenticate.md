---
title: Configurare l'accesso senza password a Surface Hub
description: Scopri come semplificare l'accesso a Surface Hub.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 07/21/2020
ms.localizationpriority: Medium
ms.openlocfilehash: 5449a3a168821c61b7c8969bfe445db91f357a2b
ms.sourcegitcommit: 4012a9499f658799197fedc7ea1a0c35d6127ed5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2021
ms.locfileid: "12101176"
---
# <a name="configure-passwordless-sign-in-on-surface-hub"></a>Configurare l'accesso senza password in Surface Hub

 
L'accesso senza password semplifica l'accesso alle app, alle riunioni e ai file. Surface Hub supporta l'accesso usando l'app Microsoft Authenticator e le chiavi di sicurezza FIDO2 fornite dall'organizzazione.

**Importante:** Questo contenuto è destinato agli utenti. Per utilizzare l'accesso senza password, l'amministratore IT deve abilitare l'autenticazione senza password per l'organizzazione. Per altre informazioni, vedi:

- [Abilitare l'accesso telefonico senza password](/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Abilitare l'accesso con chiave di sicurezza senza password](/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


## <a name="configure-sign-in-using-microsoft-authenticator-app"></a>Configurare l'accesso con Microsoft Authenticator app

**Nota:** A partire da Windows 10 Team 2020 Update, gli utenti possono usare gli alias di posta elettronica preferiti in Azure AD, nonché il nome dell'entità utente (UPN), per accedere usando Microsoft Authenticator. Ad esempio, un utente può usare il proprio alias preferito (John.Doe@contoso.com) o l'UPN (jdoe@contoso.com) per accedere.
 
L Microsoft Authenticator app consente di accedere a Surface Hub usando il dispositivo mobile. Per configurare l'accesso tramite Microsoft Authenticator:


1. Nel dispositivo mobile scarica l'app Microsoft Authenticator app.
    - Google Android: nel dispositivo Android, vai a Google Play per [scaricare e installare](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator)l Microsoft Authenticator app .
    - Apple iOS: nel dispositivo Apple iOS, vai all'App Store per scaricare e installare [l'app Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).
2. Nel PC configura [l'app Microsoft Authenticator](/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) app dalla pagina Info di sicurezza per il tuo account aziendale o dell'istituto di istruzione.
3. Dall'Microsoft Authenticator app sul dispositivo [mobile,](/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) attiva e usa l'accesso telefonico per il tuo account aziendale o dell'istituto di istruzione.

 
## <a name="configure-sign-in-using-fido2-security-keys"></a>Configurare l'accesso con le chiavi di sicurezza FIDO2

> [!NOTE]
>  L'accesso senza password Surface Hub le chiavi di sicurezza FIDO2 richiede l'aggiornamento Windows 10 Team 2020.

> [!IMPORTANT]
> Surface Hub supporta solo le chiavi di sicurezza USB.
 
Puoi anche accedere a Surface Hub usando una chiave di sicurezza FIDO2 fornita dall'organizzazione. 

### <a name="to-configure-sign-in-using-a-security-key"></a>Per configurare l'accesso utilizzando una chiave di sicurezza:


1. Nel PC passare alla pagina e [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) accedere all'account aziendale o dell'istituto di istruzione.
2. Seleziona **Info di** sicurezza nel riquadro di **** spostamento sinistro o dal collegamento nel blocco Info di sicurezza e quindi seleziona **Aggiungi** metodo nella pagina **Info di** sicurezza.
3. Nella pagina **Aggiungi metodo** selezionare Chiave **di sicurezza** nell'elenco a discesa e quindi selezionare **Aggiungi**.
4. Nella pagina **Chiave di sicurezza** scegliere Dispositivo **USB**.
5. Avere la chiave di sicurezza pronta e selezionare **Avanti**.
6. Nella finestra di dialogo visualizzata seguire le istruzioni per inserire la chiave di sicurezza, creare o immettere un PIN ed eseguire il movimento richiesto (biometrico o tocco).
7. Nella pagina **Chiave di sicurezza** assegna un nome alla chiave di sicurezza e quindi seleziona **Avanti.**
8. Selezionare **Fatto** per completare il processo.

## <a name="sign-in-to-surface-hub"></a>Accedi a Surface Hub

Dopo aver configurato l'accesso senza password, puoi usarlo per semplificare l'accesso alle app, alle riunioni e ai file nel Surface Hub:

- Partecipare rapidamente alle riunioni e aprire i file Microsoft 365 recenti. Per ulteriori informazioni, vedere [**Accedi per visualizzare le riunioni e i file.**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub)
- Accedi rapidamente alle app Microsoft come Lavagna, PowerPoint, Word, Excel, OneDrive e Power BI.
- Accedi rapidamente al nuovo Microsoft Edge per accedere ai preferiti e alle preferenze di esplorazione. Per ulteriori informazioni, vedere [Install and configure the new Microsoft Edge](surface-hub-install-chromium-edge.md).
- Dopo aver effettuato l'Surface Hub, puoi usare altre app senza dover eseguire di nuovo l'accesso fino a quando non seleziona **Termina sessione.** Se **si seleziona Termina** sessione, le credenziali, i file e i dati personali vengono eliminati dal dispositivo. Per ulteriori informazioni, vedere [End session](finishing-your-surface-hub-meeting.md).


## <a name="learn-more"></a>Scopri di più

- [Opzioni di autenticazione senza password per Azure Active Directory](/azure/active-directory/authentication/concept-authentication-passwordless)
- [Accesso senza password con l Microsoft Authenticator app](/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Accesso senza password con chiavi di sicurezza FIDO2](/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)


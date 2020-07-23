---
title: Configurare l'accesso senza password in Surface Hub
description: Informazioni su come semplificare l'accesso a Surface Hub.
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
ms.openlocfilehash: 0eaa48200be9ff3c8087530b6dfddeb9aa4620d8
ms.sourcegitcommit: 8738f44f2f4c86e3a45e9fbcbe6469388fc15924
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/22/2020
ms.locfileid: "10893048"
---
# Configurare l'accesso senza password su Surface Hub

 
Il login senza password semplifica l'accesso alle tue app, riunioni e file. Surface Hub supporta l'accesso con l'app Microsoft Authenticator e le chiavi di sicurezza di FIDO2 fornite dall'organizzazione.

**Importante:** Questo contenuto è destinato agli utenti. Per usare l'accesso senza password, l'amministratore IT deve abilitare l'autenticazione con password per l'organizzazione. Per altre informazioni, vedi:

- [Abilitare l'accesso tramite telefono senza password](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Abilitare l'accesso tramite chiave di sicurezza senza password](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


## Configurare l'accesso con l'app Microsoft Authenticator

**Nota:** A partire da Windows 10 team 2020 Update, gli utenti possono usare gli alias di posta elettronica preferiti in Azure AD, nonché il nome dell'entità utente (UPN), per accedere con Microsoft Authenticator. Ad esempio, un utente può usare l'alias preferito (John.Doe@contoso.com) o il relativo UPN (jdoe@contoso.com) per accedere.
 
L'app Microsoft Authenticator consente di accedere a Surface hub usando il dispositivo mobile. Per configurare l'accesso tramite Microsoft Authenticator:


1. Nel dispositivo mobile scaricare l'app Microsoft Authenticator.
    - Google Android: nel dispositivo Android, passa a Google Play per [scaricare e installare l'app Microsoft Authenticator](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).
    - Apple iOS: nel dispositivo iOS di Apple, accedere all'App Store per [scaricare e installare l'app Microsoft Authenticator](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).
2. Nel PC [configurare l'app Microsoft Authenticator dalla pagina Info sicurezza](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) per l'account di lavoro o dell'Istituto di istruzione.
3. Dall'app Microsoft Authenticator nel dispositivo mobile, [attivare e usare l'accesso telefonico](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) per l'account di lavoro o dell'Istituto di istruzione.

 
## Configurare l'accesso tramite le chiavi di sicurezza di FIDO2

> [!NOTE]
>  L'accesso senza password all'hub Surface con le chiavi di sicurezza di FIDO2 richiede l'aggiornamento di Windows 10 team 2020.

> [!IMPORTANT]
> Surface Hub supporta solo le chiavi di sicurezza USB.
 
Puoi anche accedere a Surface hub usando una chiave di sicurezza FIDO2 fornita dall'organizzazione. 

### Per configurare l'accesso tramite una chiave di sicurezza:


1. Nel PC accedere alla [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) pagina e accedere al proprio account di lavoro o dell'Istituto di istruzione.
2. Selezionare **info di sicurezza** dal riquadro di spostamento sinistro o dal collegamento nel blocco **info sicurezza** e quindi selezionare **Aggiungi metodo** nella pagina **info sicurezza** .
3. Nella pagina **Aggiungi metodo** selezionare **chiave di sicurezza** nell'elenco a discesa e quindi selezionare **Aggiungi**.
4. Nella pagina **chiave di sicurezza** scegliere **dispositivo USB**.
5. Avere la chiave di sicurezza pronta e selezionare **Avanti**.
6. Nella finestra di dialogo visualizzata seguire le istruzioni per inserire la chiave di sicurezza, creare o immettere un PIN ed eseguire il gesto richiesto (biometrico o tocco).
7. Nella pagina **chiave di sicurezza** assegnare un nome alla chiave di sicurezza, quindi selezionare **Avanti**.
8. Selezionare **fine** per completare il processo.

## Accesso a Surface Hub

Dopo aver configurato l'accesso senza password, è possibile usarlo per semplificare l'accessibilità delle app, delle riunioni e dei file nell'hub Surface:

- Partecipare rapidamente alle riunioni e aprire i file recenti di Microsoft 365. Per altre informazioni, vedere [**accedere per visualizzare le riunioni e i file**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub).
- Accedere rapidamente alle app Microsoft come lavagna, PowerPoint, Word, Excel, OneDrive e Power BI.
- Accedi rapidamente al nuovo Microsoft Edge per accedere ai tuoi preferiti e alle preferenze di esplorazione. Per altre informazioni, vedere [installare e configurare il nuovo Microsoft Edge](surface-hub-install-chromium-edge.md).
- Dopo aver effettuato l'accesso a Surface Hub, è possibile usare altre app senza dover eseguire di nuovo l'accesso finché non si seleziona **Termina sessione**. La selezione di **fine sessione** Elimina le credenziali, i file e i dati personali dal dispositivo. Per altre informazioni, Vedi [Termina sessione](finishing-your-surface-hub-meeting.md).


## Scopri di più

- [Opzioni di autenticazione con password per Azure Active Directory](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)
- [Accesso senza password con l'app Microsoft Authenticator](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [Accesso senza password tramite le chiavi di sicurezza di FIDO2](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)


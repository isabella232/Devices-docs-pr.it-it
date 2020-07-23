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
# <span data-ttu-id="7e00c-104">Configurare l'accesso senza password su Surface Hub</span><span class="sxs-lookup"><span data-stu-id="7e00c-104">Configure passwordless sign-in on Surface Hub</span></span>

 
<span data-ttu-id="7e00c-105">Il login senza password semplifica l'accesso alle tue app, riunioni e file.</span><span class="sxs-lookup"><span data-stu-id="7e00c-105">Passwordless sign-in simplifies access to your apps, meetings, and files.</span></span> <span data-ttu-id="7e00c-106">Surface Hub supporta l'accesso con l'app Microsoft Authenticator e le chiavi di sicurezza di FIDO2 fornite dall'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-106">Surface Hub supports signing in using the Microsoft Authenticator app and FIDO2 security keys provided by your organization.</span></span>

<span data-ttu-id="7e00c-107">**Importante:** Questo contenuto è destinato agli utenti.</span><span class="sxs-lookup"><span data-stu-id="7e00c-107">**Important:** This content is intended for users.</span></span> <span data-ttu-id="7e00c-108">Per usare l'accesso senza password, l'amministratore IT deve abilitare l'autenticazione con password per l'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-108">To use passwordless sign-in, your IT admin must enable passwordless authentication for your organization.</span></span> <span data-ttu-id="7e00c-109">Per altre informazioni, vedi:</span><span class="sxs-lookup"><span data-stu-id="7e00c-109">For more information, see:</span></span>

- [<span data-ttu-id="7e00c-110">Abilitare l'accesso tramite telefono senza password</span><span class="sxs-lookup"><span data-stu-id="7e00c-110">Enable passwordless phone sign-in</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [<span data-ttu-id="7e00c-111">Abilitare l'accesso tramite chiave di sicurezza senza password</span><span class="sxs-lookup"><span data-stu-id="7e00c-111">Enable passwordless security key sign-in</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key)


## <span data-ttu-id="7e00c-112">Configurare l'accesso con l'app Microsoft Authenticator</span><span class="sxs-lookup"><span data-stu-id="7e00c-112">Configure sign-in using Microsoft Authenticator app</span></span>

<span data-ttu-id="7e00c-113">**Nota:** A partire da Windows 10 team 2020 Update, gli utenti possono usare gli alias di posta elettronica preferiti in Azure AD, nonché il nome dell'entità utente (UPN), per accedere con Microsoft Authenticator.</span><span class="sxs-lookup"><span data-stu-id="7e00c-113">**Note:** Starting with Windows 10 Team 2020 Update, users can use their preferred email aliases in Azure AD, as well as their User Principal Name (UPN), to sign in using Microsoft Authenticator.</span></span> <span data-ttu-id="7e00c-114">Ad esempio, un utente può usare l'alias preferito (John.Doe@contoso.com) o il relativo UPN (jdoe@contoso.com) per accedere.</span><span class="sxs-lookup"><span data-stu-id="7e00c-114">For example, a user can use either their preferred alias (John.Doe@contoso.com) or their UPN (jdoe@contoso.com) to sign in.</span></span>
 
<span data-ttu-id="7e00c-115">L'app Microsoft Authenticator consente di accedere a Surface hub usando il dispositivo mobile.</span><span class="sxs-lookup"><span data-stu-id="7e00c-115">The Microsoft Authenticator app helps you sign-in to Surface Hub using your mobile device.</span></span> <span data-ttu-id="7e00c-116">Per configurare l'accesso tramite Microsoft Authenticator:</span><span class="sxs-lookup"><span data-stu-id="7e00c-116">To configure sign-in using Microsoft Authenticator:</span></span>


1. <span data-ttu-id="7e00c-117">Nel dispositivo mobile scaricare l'app Microsoft Authenticator.</span><span class="sxs-lookup"><span data-stu-id="7e00c-117">On your mobile device, download the Microsoft Authenticator app.</span></span>
    - <span data-ttu-id="7e00c-118">Google Android: nel dispositivo Android, passa a Google Play per [scaricare e installare l'app Microsoft Authenticator](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).</span><span class="sxs-lookup"><span data-stu-id="7e00c-118">Google Android: On your Android device, go to Google Play to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).</span></span>
    - <span data-ttu-id="7e00c-119">Apple iOS: nel dispositivo iOS di Apple, accedere all'App Store per [scaricare e installare l'app Microsoft Authenticator](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).</span><span class="sxs-lookup"><span data-stu-id="7e00c-119">Apple iOS: On your Apple iOS device, go to the App Store to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https%3A%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).</span></span>
2. <span data-ttu-id="7e00c-120">Nel PC [configurare l'app Microsoft Authenticator dalla pagina Info sicurezza](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) per l'account di lavoro o dell'Istituto di istruzione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-120">On your PC, [setup the Microsoft Authenticator app from the Security info page](https://docs.microsoft.com/azure/active-directory/user-help/security-info-setup-auth-app#set-up-the-microsoft-authenticator-app-from-the-security-info-page) for your work or school account.</span></span>
3. <span data-ttu-id="7e00c-121">Dall'app Microsoft Authenticator nel dispositivo mobile, [attivare e usare l'accesso telefonico](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) per l'account di lavoro o dell'Istituto di istruzione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-121">From the Microsoft Authenticator app on your mobile device, [turn on and use phone sign-in](https://docs.microsoft.com/azure/active-directory/user-help/user-help-auth-app-sign-in#turn-on-and-use-phone-sign-in-for-your-work-or-school-account) for your work or school account.</span></span>

 
## <span data-ttu-id="7e00c-122">Configurare l'accesso tramite le chiavi di sicurezza di FIDO2</span><span class="sxs-lookup"><span data-stu-id="7e00c-122">Configure sign-in using FIDO2 security keys</span></span>

> [!NOTE]
>  <span data-ttu-id="7e00c-123">L'accesso senza password all'hub Surface con le chiavi di sicurezza di FIDO2 richiede l'aggiornamento di Windows 10 team 2020.</span><span class="sxs-lookup"><span data-stu-id="7e00c-123">Passwordless sign-in on Surface Hub using FIDO2 security keys requires the Windows 10 Team 2020 Update.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e00c-124">Surface Hub supporta solo le chiavi di sicurezza USB.</span><span class="sxs-lookup"><span data-stu-id="7e00c-124">Surface Hub only supports USB security keys.</span></span>
 
<span data-ttu-id="7e00c-125">Puoi anche accedere a Surface hub usando una chiave di sicurezza FIDO2 fornita dall'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-125">You can also sign into Surface Hub using a FIDO2 security key provided by your organization.</span></span> 

### <span data-ttu-id="7e00c-126">Per configurare l'accesso tramite una chiave di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="7e00c-126">To configure sign-in using a security key:</span></span>


1. <span data-ttu-id="7e00c-127">Nel PC accedere alla [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) pagina e accedere al proprio account di lavoro o dell'Istituto di istruzione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-127">On your PC, go to your [https://myprofile.microsoft.com/](https://myprofile.microsoft.com/) page and sign in to your work or school account.</span></span>
2. <span data-ttu-id="7e00c-128">Selezionare **info di sicurezza** dal riquadro di spostamento sinistro o dal collegamento nel blocco **info sicurezza** e quindi selezionare **Aggiungi metodo** nella pagina **info sicurezza** .</span><span class="sxs-lookup"><span data-stu-id="7e00c-128">Select **Security info** from the left navigation pane or from the link in the **Security info** block, and then select **Add method** from the **Security info** page.</span></span>
3. <span data-ttu-id="7e00c-129">Nella pagina **Aggiungi metodo** selezionare **chiave di sicurezza** nell'elenco a discesa e quindi selezionare **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="7e00c-129">On the **Add a method** page, select **Security key** from the drop-down list, and then select **Add**.</span></span>
4. <span data-ttu-id="7e00c-130">Nella pagina **chiave di sicurezza** scegliere **dispositivo USB**.</span><span class="sxs-lookup"><span data-stu-id="7e00c-130">On the **Security key** page, choose **USB device**.</span></span>
5. <span data-ttu-id="7e00c-131">Avere la chiave di sicurezza pronta e selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="7e00c-131">Have your security key ready and select **Next**.</span></span>
6. <span data-ttu-id="7e00c-132">Nella finestra di dialogo visualizzata seguire le istruzioni per inserire la chiave di sicurezza, creare o immettere un PIN ed eseguire il gesto richiesto (biometrico o tocco).</span><span class="sxs-lookup"><span data-stu-id="7e00c-132">In the dialog box that appears, follow the instructions to insert the security key, create or enter a PIN, and perform the required gesture (either biometric or touch).</span></span>
7. <span data-ttu-id="7e00c-133">Nella pagina **chiave di sicurezza** assegnare un nome alla chiave di sicurezza, quindi selezionare **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="7e00c-133">On the **Security key** page, give your security key a name, then select **Next**.</span></span>
8. <span data-ttu-id="7e00c-134">Selezionare **fine** per completare il processo.</span><span class="sxs-lookup"><span data-stu-id="7e00c-134">Select **Done** to complete the process.</span></span>

## <span data-ttu-id="7e00c-135">Accesso a Surface Hub</span><span class="sxs-lookup"><span data-stu-id="7e00c-135">Sign-in to Surface Hub</span></span>

<span data-ttu-id="7e00c-136">Dopo aver configurato l'accesso senza password, è possibile usarlo per semplificare l'accessibilità delle app, delle riunioni e dei file nell'hub Surface:</span><span class="sxs-lookup"><span data-stu-id="7e00c-136">Once you've configured passwordless sign-in, you can use it to make it easier to access your apps, meetings, and files on the Surface Hub:</span></span>

- <span data-ttu-id="7e00c-137">Partecipare rapidamente alle riunioni e aprire i file recenti di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="7e00c-137">Quickly join your meetings and open recent Microsoft 365 files.</span></span> <span data-ttu-id="7e00c-138">Per altre informazioni, vedere [**accedere per visualizzare le riunioni e i file**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub).</span><span class="sxs-lookup"><span data-stu-id="7e00c-138">For more information, see [**Sign in to see your meetings and files**](https://support.microsoft.com/help/4506480/sign-in-to-see-your-meetings-and-files-on-surface-hub).</span></span>
- <span data-ttu-id="7e00c-139">Accedere rapidamente alle app Microsoft come lavagna, PowerPoint, Word, Excel, OneDrive e Power BI.</span><span class="sxs-lookup"><span data-stu-id="7e00c-139">Quickly sign in to Microsoft apps like Whiteboard, PowerPoint, Word, Excel, OneDrive, and Power BI.</span></span>
- <span data-ttu-id="7e00c-140">Accedi rapidamente al nuovo Microsoft Edge per accedere ai tuoi preferiti e alle preferenze di esplorazione.</span><span class="sxs-lookup"><span data-stu-id="7e00c-140">Quickly sign in to the new Microsoft Edge to access your favorites and browsing preferences.</span></span> <span data-ttu-id="7e00c-141">Per altre informazioni, vedere [installare e configurare il nuovo Microsoft Edge](surface-hub-install-chromium-edge.md).</span><span class="sxs-lookup"><span data-stu-id="7e00c-141">For more information, see [Install and configure the new Microsoft Edge](surface-hub-install-chromium-edge.md).</span></span>
- <span data-ttu-id="7e00c-142">Dopo aver effettuato l'accesso a Surface Hub, è possibile usare altre app senza dover eseguire di nuovo l'accesso finché non si seleziona **Termina sessione**.</span><span class="sxs-lookup"><span data-stu-id="7e00c-142">Once you've signed into Surface Hub, you can use other apps without having to sign in again until you select **End session**.</span></span> <span data-ttu-id="7e00c-143">La selezione di **fine sessione** Elimina le credenziali, i file e i dati personali dal dispositivo.</span><span class="sxs-lookup"><span data-stu-id="7e00c-143">Selecting **End session** deletes your credentials, files, and personal data from the device.</span></span> <span data-ttu-id="7e00c-144">Per altre informazioni, Vedi [Termina sessione](finishing-your-surface-hub-meeting.md).</span><span class="sxs-lookup"><span data-stu-id="7e00c-144">For more information, see [End session](finishing-your-surface-hub-meeting.md).</span></span>


## <span data-ttu-id="7e00c-145">Scopri di più</span><span class="sxs-lookup"><span data-stu-id="7e00c-145">Learn more</span></span>

- [<span data-ttu-id="7e00c-146">Opzioni di autenticazione con password per Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="7e00c-146">Passwordless authentication options for Azure Active Directory</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/concept-authentication-passwordless)
- [<span data-ttu-id="7e00c-147">Accesso senza password con l'app Microsoft Authenticator</span><span class="sxs-lookup"><span data-stu-id="7e00c-147">Passwordless sign-in with the Microsoft Authenticator app</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-phone)
- [<span data-ttu-id="7e00c-148">Accesso senza password tramite le chiavi di sicurezza di FIDO2</span><span class="sxs-lookup"><span data-stu-id="7e00c-148">Passwordless sign-in using FIDO2 security keys</span></span>](https://docs.microsoft.com/azure/active-directory/authentication/howto-authentication-passwordless-security-key#user-registration-and-management-of-fido2-security-keys)


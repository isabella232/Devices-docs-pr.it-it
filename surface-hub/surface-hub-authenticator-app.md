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
ms.openlocfilehash: 11768488d2ef7509af6a592b9e4ac945a7e35650
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832960"
---
# <span data-ttu-id="3117c-103">Accedere a Surface Hub con Microsoft Authenticator</span><span class="sxs-lookup"><span data-stu-id="3117c-103">Sign in to Surface Hub with Microsoft Authenticator</span></span>

<span data-ttu-id="3117c-104">Gli utenti dell'organizzazione possono accedere a un dispositivo Surface Hub senza password utilizzando l'app Microsoft Authenticator disponibile su Android e iOS.</span><span class="sxs-lookup"><span data-stu-id="3117c-104">People in your organization can sign in to a Surface Hub  without a password using the Microsoft Authenticator app, available on Android and iOS.</span></span>

## <span data-ttu-id="3117c-105">Prerequisiti dell'organizzazione</span><span class="sxs-lookup"><span data-stu-id="3117c-105">Organization prerequisites</span></span>

<span data-ttu-id="3117c-106">Per consentire agli utenti dell'organizzazione di accedere a Surface Hub con i loro telefoni e altri dispositivi anziché con una password, devi assicurarti che l'organizzazione soddisfi questi prerequisiti:</span><span class="sxs-lookup"><span data-stu-id="3117c-106">To let people in your organization sign in to Surface Hub with their phones and other devices instead of a password, you’ll need to make sure that your organization meets these prerequisites:</span></span> 

- <span data-ttu-id="3117c-107">L'organizzazione deve essere un'organizzazione ibrida o solo cloud, supportato da Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="3117c-107">Your organization must be a hybrid or cloud-only organization, backed by Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="3117c-108">Per altre informazioni, vedi [Informazioni su Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis).</span><span class="sxs-lookup"><span data-stu-id="3117c-108">For more information, see [What is Azure Active Directory?](https://docs.microsoft.com/azure/active-directory/active-directory-whatis)</span></span>

- <span data-ttu-id="3117c-109">Assicurati di disporre almeno di una sottoscrizione di Office 365 E3.</span><span class="sxs-lookup"><span data-stu-id="3117c-109">Make sure you have at minimum an Office 365 E3 subscription.</span></span> 

- <span data-ttu-id="3117c-110">[Configura Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings).</span><span class="sxs-lookup"><span data-stu-id="3117c-110">[Configure Multi-Factor Authentication](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfa-mfasettings).</span></span> <span data-ttu-id="3117c-111">Assicurati che **Notifica tramite app mobile** sia selezionato.</span><span class="sxs-lookup"><span data-stu-id="3117c-111">Make sure **Notification through mobile app** is selected.</span></span> 

    ![opzioni di Multi-Factor Authentication](images/mfa-options.png)

- <span data-ttu-id="3117c-113">Abilitare l'hosting di contenuti in servizi di Azure AD, ad esempio Office, SharePoint e così via.</span><span class="sxs-lookup"><span data-stu-id="3117c-113">Enable content hosting on Azure AD services such as Office, SharePoint, etc.</span></span> 

- <span data-ttu-id="3117c-114">In Surface Hub deve essere in esecuzione Windows 10, versione 1703 o successiva.</span><span class="sxs-lookup"><span data-stu-id="3117c-114">Surface Hub must be running Windows 10, version 1703 or later.</span></span>

- <span data-ttu-id="3117c-115">Surface Hub è configurato con un account locale o di dominio.</span><span class="sxs-lookup"><span data-stu-id="3117c-115">Surface Hub is set up with either a local or domain-joined account.</span></span>

<span data-ttu-id="3117c-116">Attualmente puoi utilizzare Microsoft Authenticator per accedere ai dispositivi Surface Hub che sono stati aggiunti ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="3117c-116">Currently, you cannot use Microsoft Authenticator to sign in to Surface Hubs that are joined to Azure AD.</span></span>

## <span data-ttu-id="3117c-117">Singoli prerequisiti</span><span class="sxs-lookup"><span data-stu-id="3117c-117">Individual prerequisites</span></span>

- <span data-ttu-id="3117c-118">Un telefono Android in cui è in esecuzione la versione 6.0 o successiva oppure un iPhone o iPad in cui è in esecuzione iOS9 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="3117c-118">An Android phone running 6.0 or later, or an iPhone or iPad running iOS9 or later</span></span> 

- <span data-ttu-id="3117c-119">La versione più recente dell'app Microsoft Authenticator dell'archivio di app appropriate</span><span class="sxs-lookup"><span data-stu-id="3117c-119">The most recent version of the Microsoft Authenticator app from the appropriate app store</span></span>

    >[!NOTE]
    ><span data-ttu-id="3117c-120">In iOS, la versione dell'app deve essere 5.4.0 o successiva.</span><span class="sxs-lookup"><span data-stu-id="3117c-120">On iOS, the app version must be 5.4.0 or higher.</span></span>
    >
    ><span data-ttu-id="3117c-121">L'app Microsoft Authenticator su telefoni in cui è in esecuzione un sistema operativo Windows non può essere utilizzata per accedere a Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="3117c-121">The Microsoft Authenticator app on phones running a Windows operating system can't be used to sign in to Surface Hub.</span></span>

- <span data-ttu-id="3117c-122">Il passcode o il blocco per lo schermo nel tuo dispositivo è abilitato</span><span class="sxs-lookup"><span data-stu-id="3117c-122">Passcode or screen lock on your device is enabled</span></span>

- <span data-ttu-id="3117c-123">Un indirizzo di posta elettronica SMTP standard (esempio: joe@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="3117c-123">A standard SMTP email address (example: joe@contoso.com).</span></span> <span data-ttu-id="3117c-124">Gli indirizzi di posta elettronica SMTP non standard o di reindirizzamento a microsito (esempio: nome.cognome@contoso.com) non funzionano.</span><span class="sxs-lookup"><span data-stu-id="3117c-124">Non-standard or vanity SMTP email addresses (example: firstname.lastname@contoso.com) currently don’t work.</span></span>

## <span data-ttu-id="3117c-125">Come usare l'app Microsoft Authenticator</span><span class="sxs-lookup"><span data-stu-id="3117c-125">How to set up the Microsoft Authenticator app</span></span>

>[!NOTE]
><span data-ttu-id="3117c-126">Se il portale aziendale è installato nel dispositivo Android, disinstallalo prima di configurare Microsoft Authenticator.</span><span class="sxs-lookup"><span data-stu-id="3117c-126">If Company Portal is installed on your Android device, uninstall it before you set up Microsoft Authenticator.</span></span> <span data-ttu-id="3117c-127">Dopo aver configurato l'app, puoi reinstallare il portale aziendale.</span><span class="sxs-lookup"><span data-stu-id="3117c-127">After you set up the app, you can reinstall Company Portal.</span></span>
>
><span data-ttu-id="3117c-128">Se hai già impostato Microsoft Authenticator nel tuo telefono e registrato il dispositivo, vai alle istruzioni di accesso.</span><span class="sxs-lookup"><span data-stu-id="3117c-128">If you have already set up Microsoft Authenticator on your phone and registered your device, go to the sign-in instructions.</span></span>

1. <span data-ttu-id="3117c-129">Aggiungi l'account aziendale o dell'istituto didattico a Microsoft Authenticator per Multi-Factor Authentication.</span><span class="sxs-lookup"><span data-stu-id="3117c-129">Add your work or school account to Microsoft Authenticator for Multi-Factor Authentication.</span></span> <span data-ttu-id="3117c-130">Ti servirà un codice QR fornito dal reparto IT.</span><span class="sxs-lookup"><span data-stu-id="3117c-130">You will need a QR code provided by your IT department.</span></span> <span data-ttu-id="3117c-131">Per altre informazioni, vedi [Introduzione all'app Microsoft Authenticator](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).</span><span class="sxs-lookup"><span data-stu-id="3117c-131">For help, see [Get started with the Microsoft Authenticator app](https://docs.microsoft.com/azure/multi-factor-authentication/end-user/microsoft-authenticator-app-how-to).</span></span>
2. <span data-ttu-id="3117c-132">Vai a **Impostazioni** e registra il dispositivo.</span><span class="sxs-lookup"><span data-stu-id="3117c-132">Go to **Settings** and register your device.</span></span>
3. <span data-ttu-id="3117c-133">Torna alla pagina degli account e scegli **Abilita l'accesso telefonico** dal menu a discesa dell'account.</span><span class="sxs-lookup"><span data-stu-id="3117c-133">Return to the accounts page and choose **Enable phone sign-in** from the account dropdown menu.</span></span>

## <span data-ttu-id="3117c-134">Come eseguire l'accesso a Surface Hub durante una riunione</span><span class="sxs-lookup"><span data-stu-id="3117c-134">How to sign in to Surface Hub during a meeting</span></span>

1. <span data-ttu-id="3117c-135">Dopo aver impostato una riunione, vai a Surface Hub e seleziona **Accedi per visualizzare i file e le riunioni**.</span><span class="sxs-lookup"><span data-stu-id="3117c-135">After you’ve set up a meeting, go to the Surface Hub and select **Sign in to see your meetings and files**.</span></span>

    >[!NOTE]
    ><span data-ttu-id="3117c-136">Se non sei sicuro di come pianificare una riunione su un dispositivo Surface Hub, vedi [Pianificare un Surface hub](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting).</span><span class="sxs-lookup"><span data-stu-id="3117c-136">If you’re not sure how to schedule a meeting on a Surface Hub, see [Schedule a meeting on Surface Hub](https://support.microsoft.com/help/17325/surfacehub-schedulemeeting).</span></span>

    ![screenshot dell'opzione Accesso in Surface Hub](images/sign-in.png)

2. <span data-ttu-id="3117c-138">Vedrai un elenco degli utenti invitati alla riunione.</span><span class="sxs-lookup"><span data-stu-id="3117c-138">You’ll see a list of the people invited to the meeting.</span></span> <span data-ttu-id="3117c-139">Seleziona te stesso (o la persona che vuole accedere, assicurati che questa persona abbia eseguito la procedura per configurare il proprio dispositivo prima della riunione), quindi **Continua**.</span><span class="sxs-lookup"><span data-stu-id="3117c-139">Select yourself (or the person who wants to sign in – make sure this person has gone through the steps to set up their device before your meeting), and then select **Continue**.</span></span>

    ![screenshot dell'elenco dei partecipanti a una riunione](images/attendees.png)

    <span data-ttu-id="3117c-141">Vedrai un codice su Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="3117c-141">You'll see a code on the Surface Hub.</span></span>

    ![screenshot del codice per l'approvazione dell'accesso](images/approve-signin.png)

3. <span data-ttu-id="3117c-143">Per approvare l'accesso, apri l'app Authenticator, immetti il codice a quattro cifre che viene visualizzato in Surface Hub e seleziona **Approva**.</span><span class="sxs-lookup"><span data-stu-id="3117c-143">To approve the sign-in, open the Authenticator app, enter the four-digit code that’s displayed on the Surface Hub, and select **Approve**.</span></span> <span data-ttu-id="3117c-144">Ti verrà quindi chiesto di immettere il PIN o di usare l'impronta digitale per completare l'accesso.</span><span class="sxs-lookup"><span data-stu-id="3117c-144">You will then be asked to enter the PIN or use your fingerprint to complete the sign in.</span></span> 

    ![screenshot della schermata dell'approvazione dell'accesso in Microsoft Authenticator](images/approve-signin2.png)

<span data-ttu-id="3117c-146">Ora puoi accedere a tutti i file tramite l'app OneDrive.</span><span class="sxs-lookup"><span data-stu-id="3117c-146">You can now access all files through the OneDrive app.</span></span>
---
title: Creare account del dispositivo con l&#39;interfaccia utente (Surface Hub)
description: Se vuoi usare un&#39;interfaccia GUI, puoi creare un account per Surface Hub con l&#39;interfaccia utente di Office 365 o l&#39;interfaccia di amministrazione di Exchange.
ms.assetid: D11BCDC4-DABA-4B9A-9ECB-58E02CC8218C
ms.reviewer: ''
manager: laurawi
keywords: creare un account di dispositivo, un'interfaccia utente di Office 365, un centro di amministrazione di Exchange, un centro di amministrazione di Microsoft 365, Skype for business, un criterio cassetta postale
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/04/2018
ms.localizationpriority: medium
ms.openlocfilehash: e1f82f084103d4eef942e812c5e4f0e8bf425def
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834076"
---
# <span data-ttu-id="04110-104">Creare account del dispositivo con l&#39;interfaccia utente (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="04110-104">Create a device account using UI (Surface Hub)</span></span>


<span data-ttu-id="04110-105">Se preferisci usare un'interfaccia utente grafica, puoi creare un account del dispositivo per Microsoft Surface Hub con l'[interfaccia utente di Office 365](#create-device-acct-o365) o l'[interfaccia di amministrazione di Exchange](#create-device-acct-eac).</span><span class="sxs-lookup"><span data-stu-id="04110-105">If you prefer to use a graphical user interface, you can create a device account for your Microsoft Surface Hub with either the [Office 365 UI](#create-device-acct-o365) or the [Exchange Admin Center](#create-device-acct-eac).</span></span>

## <a href="" id="create-device-acct-o365"></a><span data-ttu-id="04110-106">Creare un account del dispositivo con Office 365</span><span class="sxs-lookup"><span data-stu-id="04110-106">Create a device account using Office 365</span></span>


1.  <span data-ttu-id="04110-107">[Creare l'account nell'interfaccia di amministrazione di Microsoft 365](#create-device-acct-o365-admin-ctr).</span><span class="sxs-lookup"><span data-stu-id="04110-107">[Create the account in the Microsoft 365 Admin Center](#create-device-acct-o365-admin-ctr).</span></span>
2.  <span data-ttu-id="04110-108">[Creare un criterio cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Microsoft Exchange](#create-device-acct-o365-mbx-policy).</span><span class="sxs-lookup"><span data-stu-id="04110-108">[Create a mobile device mailbox (ActiveSync) policy from the Microsoft Exchange Admin Center](#create-device-acct-o365-mbx-policy).</span></span>
3.  <span data-ttu-id="04110-109">[Usare PowerShell per completare la creazione dell'account del dispositivo](#create-device-acct-o365-complete-acct)</span><span class="sxs-lookup"><span data-stu-id="04110-109">[Use PowerShell to complete device account creation](#create-device-acct-o365-complete-acct).</span></span>
4.  <span data-ttu-id="04110-110">[Usare PowerShell per configurare le proprietà di Exchange dell'account](#create-device-acct-o365-configure-exch-prop).</span><span class="sxs-lookup"><span data-stu-id="04110-110">[Use PowerShell to configure Exchange properties of the account](#create-device-acct-o365-configure-exch-prop).</span></span>
5.  <span data-ttu-id="04110-111">[Abilitare l'account con Skype for Business](#create-device-acct-o365-skype-for-business).</span><span class="sxs-lookup"><span data-stu-id="04110-111">[Enable the account with Skype for Business](#create-device-acct-o365-skype-for-business).</span></span>

### <a href="" id="create-device-acct-o365-admin-ctr"></a><span data-ttu-id="04110-112">Creare l'account nell'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="04110-112">Create the account in the admin center</span></span>

1.  <span data-ttu-id="04110-113">Accedere a Office 365 visitandohttps://portal.office.com</span><span class="sxs-lookup"><span data-stu-id="04110-113">Sign in to Office 365 by visiting https://portal.office.com</span></span>
2.  <span data-ttu-id="04110-114">Specifica le credenziali di amministratore per il tuo tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="04110-114">Provide the admin credentials for your Office 365 tenant.</span></span> <span data-ttu-id="04110-115">In questo modo è possibile usare l'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="04110-115">This will take you to your Microsoft 365 Admin Center.</span></span>

    ![Interfaccia di amministrazione di Microsoft 365.](images/setupdeviceaccto365-02.png)

3. <span data-ttu-id="04110-117">Nell'interfaccia di amministrazione passare a **risorse** nel riquadro sinistro e quindi fare clic su **sale & attrezzature**.</span><span class="sxs-lookup"><span data-stu-id="04110-117">In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.</span></span>

    ![Opzione camere & attrezzature nell'interfaccia di amministrazione](images/room-equipment.png)

4. <span data-ttu-id="04110-119">Fai clic su **Aggiungi** per creare un nuovo account Sala.</span><span class="sxs-lookup"><span data-stu-id="04110-119">Click **Add** to create a new Room account.</span></span> <span data-ttu-id="04110-120">Immetti un indirizzo di posta elettronica e un nome visualizzato per l'account, quindi fai clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="04110-120">Enter a display name and email address for the account, and then click **Add**.</span></span>

    ![Creare una finestra per un nuovo account sala](images/room-add.png)

5. <span data-ttu-id="04110-122">Seleziona l'account Sala appena creato nell'elenco Utenti attivi.</span><span class="sxs-lookup"><span data-stu-id="04110-122">Select the Room account you just created in the Active Users list.</span></span> <span data-ttu-id="04110-123">Nel pannello di destra sono elencate le proprietà dell'account e diverse azioni facoltative.</span><span class="sxs-lookup"><span data-stu-id="04110-123">In the right panel, you can see the account properties and several optional actions.</span></span> <span data-ttu-id="04110-124">Fai clic su **Reimposta password** per modificare la password e deseleziona **Chiedere all'utente di cambiare la password al primo accesso** in quanto non è possibile cambiare la password dal flusso di accesso di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="04110-124">Click **Reset password** to change the password, and unselect **Make this user change their password when they first sign in**, because it is not possible to change the password from the Surface Hub sign-in flow.</span></span>

6. <span data-ttu-id="04110-125">Nella sezione **Licenza assegnata** fai clic su **Modifica** e quindi fai clic sulla freccia in giù accanto alla licenza appropriata per visualizzare i dettagli.</span><span class="sxs-lookup"><span data-stu-id="04110-125">In the **Assigned license** section, click **Edit**, and then click the dropdown arrow next to the appropriate license to expand the details.</span></span> <span data-ttu-id="04110-126">Seleziona una posizione utente e, nell'elenco delle licenze, attiva **Skype for Business Online (Piano 2)** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="04110-126">Select a user location, and in the list of licenses, toggle on **Skype for Business Online (Plan 2)**, and then click **Save**.</span></span> <span data-ttu-id="04110-127">La licenza può variare a seconda dell'organizzazione, ad esempio potresti avere Piano 2 o Piano 3.</span><span class="sxs-lookup"><span data-stu-id="04110-127">The license may vary depending on your organization (for example, you might have Plan 2 or Plan 3).</span></span>

### <a href="" id="create-device-acct-o365-mbx-policy"></a><span data-ttu-id="04110-128">Creare criteri cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-128">Create a mobile device mailbox (ActiveSync) policy from the Exchange Admin Center</span></span>

1.  <span data-ttu-id="04110-129">Nel riquadro sinistro dell'interfaccia di amministrazione fare clic su **amministratore**e quindi su **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="04110-129">In the admin center’s left panel, click **ADMIN**, and then click **Exchange**.</span></span>

    ![interfaccia di amministrazione che Mostra gli utenti attivi di Exchange.](images/setupdeviceaccto365-08.png)

2.  <span data-ttu-id="04110-131">Verrà aperta un'altra scheda nel browser per permetterti di accedere all'interfaccia di amministrazione di Exchange, in cui puoi creare e configurare l'impostazione della cassetta postale per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="04110-131">This will open another tab on your browser to take you to the Exchange Admin Center, where you can create and set the Mailbox Setting for Surface Hub.</span></span>

    ![Interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-09.png)

3.  <span data-ttu-id="04110-133">Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e quindi fai clic su **Criteri della cassetta postale dei dispositivi mobili**.</span><span class="sxs-lookup"><span data-stu-id="04110-133">To create a Mobile Device Mailbox Policy, click **Mobile** from the left panel and then click **Mobile device mailbox policies**.</span></span> <span data-ttu-id="04110-134">Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account.</span><span class="sxs-lookup"><span data-stu-id="04110-134">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="04110-135">In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="04110-135">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Interfaccia di amministrazione di Exchange - creazione di criteri cassetta postale per dispositivi mobili.](images/setupdeviceaccto365-10.png)

4.  <span data-ttu-id="04110-137">Per creare un nuovo criterio cassetta postale per dispositivi mobili di Surface Hub, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio.</span><span class="sxs-lookup"><span data-stu-id="04110-137">To create a New Surface Hub mobile device mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="04110-138">Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*.</span><span class="sxs-lookup"><span data-stu-id="04110-138">For the name, provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="04110-139">Verifica che il criterio non richieda una password per i dispositivi assegnati, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="04110-139">Make sure the policy does not require a password for the devices assigned to, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![Immagine che mostra il nuovo criterio per dispositivi mobili](images/setupdeviceaccto365-11.png)

5.  <span data-ttu-id="04110-141">Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'**interfaccia di amministrazione di Exchange** per visualizzare il nuovo criterio nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="04110-141">After you have created the new mobile device mailbox policy, go back to the **Exchange Admin Center** and you will see the new policy listed.</span></span>

    ![Immagine con il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a><span data-ttu-id="04110-143">Usare Windows PowerShell per completare la creazione dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="04110-143">Use PowerShell to complete device account creation</span></span>

<span data-ttu-id="04110-144">A partire da questo momento, dovrai completare il processo di creazione dell'account usando PowerShell per definire alcune configurazioni.</span><span class="sxs-lookup"><span data-stu-id="04110-144">From here on, you'll need to finish the account creation process using PowerShell to set up some configuration.</span></span>

<span data-ttu-id="04110-145">Per eseguire i cmdlet usati da questi script di PowerShell, devi installare i seguenti componenti per la console PowerShell di amministrazione:</span><span class="sxs-lookup"><span data-stu-id="04110-145">In order to run cmdlets used by these PowerShell scripts, the following must be installed for the admin PowerShell console:</span></span>

-   [<span data-ttu-id="04110-146">Assistente per l'accesso ai Microsoft Online Services per professionisti IT-RTW</span><span class="sxs-lookup"><span data-stu-id="04110-146">Microsoft Online Services Sign-In Assistant for IT Professionals RTW</span></span>](https://www.microsoft.com/download/details.aspx?id=41950)
-   [<span data-ttu-id="04110-147">Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="04110-147">Windows Azure Active Directory Module for Windows PowerShell</span></span>](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [<span data-ttu-id="04110-148">Modulo di Windows PowerShell per Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="04110-148">Skype for Business Online, Windows PowerShell Module</span></span>](https://www.microsoft.com/download/details.aspx?id=39366)

<span data-ttu-id="04110-149">Installare il modulo seguente in PowerShell</span><span class="sxs-lookup"><span data-stu-id="04110-149">Install the following module in Powershell</span></span>
``` syntax
    install-module AzureAD
    Install-module MsOnline
```

### <span data-ttu-id="04110-150">Connessione ai servizi online</span><span class="sxs-lookup"><span data-stu-id="04110-150">Connecting to online services</span></span>

1.  <span data-ttu-id="04110-151">Esegui Windows PowerShell come amministratore.</span><span class="sxs-lookup"><span data-stu-id="04110-151">Run Windows PowerShell as Administrator.</span></span>

    ![Immagine che mostra come avviare Windows PowerShell ed eseguirlo come amministratore.](images/setupdeviceaccto365-17.png)

2.  <span data-ttu-id="04110-153">Crea un oggetto credenziali, crea una nuova sessione che si connette a Skype for Business Online e specifica l'account amministratore tenant globale, quindi fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="04110-153">Create a Credentials object, then create a new session that connects to Skype for Business Online, and provide the global tenant administrator account, then click **OK**.</span></span>

    ![Immagine per la richiesta di credenziali di Windows PowerShell.](images/setupdeviceaccto365-18.png)

3.  <span data-ttu-id="04110-155">Per connetterti a Microsoft Online Services, esegui:</span><span class="sxs-lookup"><span data-stu-id="04110-155">To connect to Microsoft Online Services, run:</span></span>

    ``` syntax
    Connect-MsolService -Credential $Cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-19.png)

4.  <span data-ttu-id="04110-157">A questo punto, per connetterti ai servizi Skype for Business Online, esegui:</span><span class="sxs-lookup"><span data-stu-id="04110-157">Now to connect to Skype for Business Online Services, run:</span></span>

    ``` syntax
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-20.png)

5.  <span data-ttu-id="04110-159">Infine, per connetterti ai servizi Exchange Online, esegui:</span><span class="sxs-lookup"><span data-stu-id="04110-159">Finally, to connect to Exchange Online Services, run:</span></span>

    ``` syntax
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-21.png)

6.  <span data-ttu-id="04110-161">Adesso devi importare la sessione di Skype for Business Online e la sessione di Exchange Online che hai appena creato, da cui verranno importati i comandi di Exchange e Skype per consentirti di usarli in locale.</span><span class="sxs-lookup"><span data-stu-id="04110-161">Now you have to import the Skype for Business Online Session and the Exchange Online session you have just created, which will import the Exchange and Skype Commands so you can use them locally.</span></span>

    ``` syntax
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    <span data-ttu-id="04110-162">Tieni presente che il completamento di questa operazione può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="04110-162">Note that this could take a while to complete.</span></span>

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-22.png)

7.  <span data-ttu-id="04110-164">Dopo la connessione ai servizi online devi eseguire altri cmdlet per configurare l'account come account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="04110-164">Once you’re connected to the online services you need to run a few more cmdlets to configure this account as a Surface Hub device account.</span></span>

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a><span data-ttu-id="04110-165">Usare PowerShell per configurare le proprietà di Exchange dell'account</span><span class="sxs-lookup"><span data-stu-id="04110-165">Use PowerShell to configure Exchange properties of the account</span></span>

<span data-ttu-id="04110-166">Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="04110-166">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="04110-167">Userai l'indirizzo e-mail dell'account del dispositivo per:</span><span class="sxs-lookup"><span data-stu-id="04110-167">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="04110-168">Modificare il tipo di cassetta postale da normale a cassetta postale della sala.</span><span class="sxs-lookup"><span data-stu-id="04110-168">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="04110-169">Impostare la password e abilitare l'account della cassetta postale della sala</span><span class="sxs-lookup"><span data-stu-id="04110-169">Set the password and enable the room mailbox account</span></span>
-   <span data-ttu-id="04110-170">Modificare varie proprietà di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-170">Change various Exchange properties</span></span>
-   <span data-ttu-id="04110-171">Impostare la password dell'account utente in modo che non scada mai.</span><span class="sxs-lookup"><span data-stu-id="04110-171">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="04110-172">Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:</span><span class="sxs-lookup"><span data-stu-id="04110-172">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="04110-173">Per archiviare il valore, recuperalo dalla cassetta postale:</span><span class="sxs-lookup"><span data-stu-id="04110-173">To store the value get it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="04110-174">Stampa il valore:</span><span class="sxs-lookup"><span data-stu-id="04110-174">Print the value:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="04110-175">Vedrai l'indirizzo e-mail corretto.</span><span class="sxs-lookup"><span data-stu-id="04110-175">You will see the correct email address.</span></span>

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-23.png)

2. <span data-ttu-id="04110-177">Eseguire il cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="04110-177">Run the following cmdlet:</span></span>

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  <span data-ttu-id="04110-178">È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="04110-178">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="04110-179">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="04110-179">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-26.png)

5.  <span data-ttu-id="04110-181">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04110-181">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="04110-182">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="04110-182">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ``` syntax
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a><span data-ttu-id="04110-183">Abilitare l'account con Skype for Business</span><span class="sxs-lookup"><span data-stu-id="04110-183">Enable the account with Skype for Business</span></span>

<span data-ttu-id="04110-184">Abilita l'account del dispositivo con Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="04110-184">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="04110-185">Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="04110-185">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="04110-186">Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="04110-186">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="04110-187">Il piano deve supportare funzionalità per conferenze.</span><span class="sxs-lookup"><span data-stu-id="04110-187">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="04110-188">Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.</span><span class="sxs-lookup"><span data-stu-id="04110-188">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="04110-189">Gli utenti tenant devono avere cassette postali di Exchange.</span><span class="sxs-lookup"><span data-stu-id="04110-189">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="04110-190">L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="04110-190">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="04110-191">Per iniziare, crea una sessione di PowerShell remota da un PC.</span><span class="sxs-lookup"><span data-stu-id="04110-191">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  <span data-ttu-id="04110-192">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="04110-192">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

    ```PowerShell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

    <span data-ttu-id="04110-193">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="04110-193">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a><span data-ttu-id="04110-194">Creare un account del dispositivo tramite l'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-194">Create a device account using the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="04110-195">Questo metodo funziona solo se si esegue la sincronizzazione da un Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="04110-195">This method will only work if you are syncing from an on-premises Active Directory.</span></span>

<span data-ttu-id="04110-196">Puoi usare l'interfaccia di amministrazione di Exchange per creare un account del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="04110-196">You can use the Exchange Admin Center to create a device account:</span></span>

1.  <span data-ttu-id="04110-197">[Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange](#create-device-acct-exch-admin-ctr).</span><span class="sxs-lookup"><span data-stu-id="04110-197">[Create an account and mailbox with the Exchange Admin Center](#create-device-acct-exch-admin-ctr).</span></span>
2.  <span data-ttu-id="04110-198">[Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange](#create-device-acct-exch-mbx-policy).</span><span class="sxs-lookup"><span data-stu-id="04110-198">[Create a mobile device mailbox policy from the Exchange Admin Center](#create-device-acct-exch-mbx-policy).</span></span>
3.  <span data-ttu-id="04110-199">[Usare PowerShell per configurare l'account](#create-device-acct-exch-powershell-conf).</span><span class="sxs-lookup"><span data-stu-id="04110-199">[Use PowerShell to configure the account](#create-device-acct-exch-powershell-conf).</span></span>
4.  <span data-ttu-id="04110-200">[Abilitare l'account con Skype for Business](#create-device-acct-exch-skype-for-business).</span><span class="sxs-lookup"><span data-stu-id="04110-200">[Enable the account with Skype for Business](#create-device-acct-exch-skype-for-business).</span></span>

### <a href="" id="create-device-acct-exch-admin-ctr"></a><span data-ttu-id="04110-201">Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-201">Create an account and mailbox with the Exchange Admin Center</span></span>

1.  <span data-ttu-id="04110-202">Accedi all'interfaccia di amministrazione di Exchange usando le credenziali di amministratore di Exchange.</span><span class="sxs-lookup"><span data-stu-id="04110-202">Sign in to your Exchange Admin Center using Exchange admin credentials.</span></span>
2.  <span data-ttu-id="04110-203">Dall'interfaccia di amministrazione di Exchange passa a **Destinatari** nel pannello sinistro.</span><span class="sxs-lookup"><span data-stu-id="04110-203">Once you are at the Exchange Admin Center (EAC), navigate to **Recipients** in the left panel.</span></span>

    ![Immagine che mostra le cassette postali nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-01.png)

3.  <span data-ttu-id="04110-205">Nei controlli sopra l'elenco delle cassette postali scegli **+** per creare una nuova cassetta e specifica i nomi in **Nome visualizzato**, **Nome** e **Nome accesso utente** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="04110-205">On the controls above the list of mailboxess, choose **+** to create a new one, and provide a **Display name**, **Name**, and **User logon name**, and then click **Save**.</span></span>

    ![Immagine che mostra la creazione di una nuova cassetta postale.](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a><span data-ttu-id="04110-207">Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-207">Create a mobile device mailbox policy from the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="04110-208">Se si vuole creare e assegnare un criterio all'account creato e si usa Exchange 2010, cercare le informazioni corrispondenti relative alla creazione e all'assegnazione dei criteri quando si usa EMC (Exchange Management Console).</span><span class="sxs-lookup"><span data-stu-id="04110-208">If you want to create and assign a policy to the account you created, and are using Exchange 2010, look up the corresponding information regarding policy creation and policy assignment when using the EMC (Exchange management console).</span></span>

 

1.  <span data-ttu-id="04110-209">Accedi all'interfaccia di amministrazione di Exchange.</span><span class="sxs-lookup"><span data-stu-id="04110-209">Go to the Exchange Admin Center.</span></span>

    ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-03.png)

2.  <span data-ttu-id="04110-211">Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e fai clic su **Criteri della cassetta postale dei dispositivi mobili**.</span><span class="sxs-lookup"><span data-stu-id="04110-211">To create a mobile device mailbox policy, click **Mobile** from the left panel, then **Mobile device mailbox policies**.</span></span> <span data-ttu-id="04110-212">Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account.</span><span class="sxs-lookup"><span data-stu-id="04110-212">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="04110-213">In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="04110-213">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Immagine che mostra l'uso dell'interfaccia di amministrazione di Exchange per creare un criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-05.png)

3.  <span data-ttu-id="04110-215">Per creare un nuovo criterio cassetta postale per l'account del dispositivo mobile, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio.</span><span class="sxs-lookup"><span data-stu-id="04110-215">To create a new mobile device account mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="04110-216">Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*.</span><span class="sxs-lookup"><span data-stu-id="04110-216">For the name provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="04110-217">Poiché il criterio non deve essere protetto da password, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="04110-217">The policy must not be password-protected, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-06.png)

4.  <span data-ttu-id="04110-219">Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'interfaccia di amministrazione di Exchange per visualizzare il nuovo criterio nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="04110-219">After you have created the new mobile device mailbox policy, go back to the Exchange Admin Center and you will see the new policy listed.</span></span>

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-07.png)

5.  <span data-ttu-id="04110-221">Per applicare il criterio di ActiveSync senza usare PowerShell, puoi procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="04110-221">To apply the ActiveSync policy without using PowerShell, you can do the following:</span></span>

    -   <span data-ttu-id="04110-222">Nell'interfaccia di amministrazione di Exchange fai clic su **Destinatari** &gt; **Cassette postali** e seleziona una cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="04110-222">In the EAC, click **Recipients** &gt; **Mailboxes** and select a mailbox.</span></span>

        ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-08.png)

    -   <span data-ttu-id="04110-224">Nel riquadro **Dettagli** scorri fino a **Funzionalità telefoniche e vocali** e fai clic su **Visualizza dettagli** per visualizzare la schermata **Dettagli dispositivo mobile**.</span><span class="sxs-lookup"><span data-stu-id="04110-224">In the **Details** pane, scroll to **Phone and Voice Features** and click **View details** to display the **Mobile Device Details** screen.</span></span>

        ![Immagine che mostra i dettagli delle cassette postali.](images/setupdeviceacctexch-09.png)

    -   <span data-ttu-id="04110-226">Vengono visualizzati i criteri cassetta postale per dispositivi mobili attualmente assegnati.</span><span class="sxs-lookup"><span data-stu-id="04110-226">The mobile device mailbox policy that’s currently assigned is displayed.</span></span> <span data-ttu-id="04110-227">Per modificare i criteri cassetta postale per dispositivi mobili, fai clic su **Sfoglia**.</span><span class="sxs-lookup"><span data-stu-id="04110-227">To change the mobile device mailbox policy, click **Browse**.</span></span>

        ![Immagine che mostra il criterio cassetta postale per dispositivi mobili attualmente assegnato.](images/setupdeviceacctexch-10.png)

    -   <span data-ttu-id="04110-229">Scegli i criteri cassetta postale per dispositivi mobili appropriati nell'elenco, fai clic su **OK** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="04110-229">Choose the appropriate mobile device mailbox policy from the list, click **OK** and then click **Save**.</span></span>

        ![Immagine che mostra l'elenco dei criteri cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a><span data-ttu-id="04110-231">Usare PowerShell per configurare l'account</span><span class="sxs-lookup"><span data-stu-id="04110-231">Use PowerShell to configure the account</span></span>

<span data-ttu-id="04110-232">Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="04110-232">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="04110-233">Userai l'indirizzo e-mail dell'account del dispositivo per:</span><span class="sxs-lookup"><span data-stu-id="04110-233">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="04110-234">Modificare il tipo di cassetta postale da normale a cassetta postale della sala.</span><span class="sxs-lookup"><span data-stu-id="04110-234">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="04110-235">Modificare varie proprietà di Exchange</span><span class="sxs-lookup"><span data-stu-id="04110-235">Change various Exchange properties</span></span>
-   <span data-ttu-id="04110-236">Impostare la password dell'account utente in modo che non scada mai.</span><span class="sxs-lookup"><span data-stu-id="04110-236">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="04110-237">Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:</span><span class="sxs-lookup"><span data-stu-id="04110-237">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ``` syntax
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="04110-238">Per archiviare il valore, recuperalo dalla cassetta postale:</span><span class="sxs-lookup"><span data-stu-id="04110-238">To store the value got it from the mailbox:</span></span>

    ``` syntax
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="04110-239">Stampa il valore eseguendo:</span><span class="sxs-lookup"><span data-stu-id="04110-239">Print the value by running:</span></span>

    ``` syntax
    $strEmail
    ```

    <span data-ttu-id="04110-240">Vedrai l'indirizzo e-mail corretto.</span><span class="sxs-lookup"><span data-stu-id="04110-240">You will see the correct email address.</span></span>

2.  <span data-ttu-id="04110-241">È necessario convertire l'account in una cassetta postale della sala, quindi eseguire:</span><span class="sxs-lookup"><span data-stu-id="04110-241">You need to convert the account into a room mailbox, so run:</span></span>

    ``` syntax
    Set-Mailbox $strEmail -Type Room
    ```

3.  <span data-ttu-id="04110-242">Affinché l'account del dispositivo possa essere autenticato in un dispositivo Surface Hub, devi abilitare l'account della cassetta postale della sala e impostare una password, in modo che l'account possa essere usato dal dispositivo per ottenere informazioni sulle riunioni tramite ActiveSync e per accedere a Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="04110-242">In order for the device account to be authenticated on a Surface Hub, you need to enable the room mailbox account and set a password, so the account can be used by the device to get meeting information using ActiveSync and log in to Skype for Business.</span></span>

    ``` syntax
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  <span data-ttu-id="04110-243">È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="04110-243">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="04110-244">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="04110-244">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ``` syntax
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  <span data-ttu-id="04110-245">A questo punto devi impostare alcune proprietà in AD.</span><span class="sxs-lookup"><span data-stu-id="04110-245">Now we have to set some properties in AD.</span></span> <span data-ttu-id="04110-246">A tale scopo, ti serve l'alias dell'account (la parte dell'UPN che precede "@").</span><span class="sxs-lookup"><span data-stu-id="04110-246">To do that, you need the alias of the account (this is the part of the UPN that becomes before the “@”).</span></span>

    ``` syntax
    $strAlias = “<your device account’s alias>”
    ```

6.  <span data-ttu-id="04110-247">Per poter eseguire l'autenticazione con un dispositivo Surface Hub, l'utente deve essere abilitato in AD.</span><span class="sxs-lookup"><span data-stu-id="04110-247">The user needs to be enabled in AD before it can authenticate with a Surface Hub.</span></span> <span data-ttu-id="04110-248">Esegui:</span><span class="sxs-lookup"><span data-stu-id="04110-248">Run:</span></span>

    ``` syntax
    Set-ADUser $strAlias -Enabled $True
    ```

7.  <span data-ttu-id="04110-249">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="04110-249">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="04110-250">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="04110-250">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ``` syntax
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a><span data-ttu-id="04110-251">Abilitare l'account con Skype for Business</span><span class="sxs-lookup"><span data-stu-id="04110-251">Enable the account with Skype for Business</span></span>

<span data-ttu-id="04110-252">Abilita l'account del dispositivo con Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="04110-252">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="04110-253">Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="04110-253">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="04110-254">Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="04110-254">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="04110-255">Il piano deve supportare funzionalità per conferenze.</span><span class="sxs-lookup"><span data-stu-id="04110-255">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="04110-256">Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.</span><span class="sxs-lookup"><span data-stu-id="04110-256">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="04110-257">Gli utenti tenant devono avere cassette postali di Exchange.</span><span class="sxs-lookup"><span data-stu-id="04110-257">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="04110-258">L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="04110-258">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="04110-259">Per iniziare, crea una sessione di PowerShell remota da un PC.</span><span class="sxs-lookup"><span data-stu-id="04110-259">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. <span data-ttu-id="04110-260">Recuperare il pool di registrazione dell'account Hub Surface</span><span class="sxs-lookup"><span data-stu-id="04110-260">Retrieve your Surface Hub account Registrar Pool</span></span>

<span data-ttu-id="04110-261">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="04110-261">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```PowerShell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```
    
3. <span data-ttu-id="04110-262">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="04110-262">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```

    






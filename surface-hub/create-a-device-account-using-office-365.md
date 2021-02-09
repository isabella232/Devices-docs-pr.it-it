---
title: Creare un account di dispositivo usando l'interfaccia utente (Surface Hub V1)
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
ms.openlocfilehash: dd19e2fd2417acd29e71c7555e94ee849fbc1bec
ms.sourcegitcommit: 32b6c25698479fa289f642c5b5761ff3be15b686
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "11318010"
---
# <span data-ttu-id="106ac-104">Creare un account di dispositivo usando l'interfaccia utente (Surface Hub V1)</span><span class="sxs-lookup"><span data-stu-id="106ac-104">Create a device account using UI (Surface Hub v1)</span></span>

 > [!NOTE]
 ><span data-ttu-id="106ac-105">Questa pagina include informazioni sull'hub della superficie originale (V1).</span><span class="sxs-lookup"><span data-stu-id="106ac-105">This page includes information about the original Surface Hub (v1).</span></span> <span data-ttu-id="106ac-106">Per Surface Hub 2S, Vedi [creare l'account del dispositivo Surface Hub 2S](surface-hub-2s-account.md).</span><span class="sxs-lookup"><span data-stu-id="106ac-106">For Surface Hub 2S, see [Create Surface Hub 2S device account](surface-hub-2s-account.md).</span></span>

<span data-ttu-id="106ac-107">Se preferisci usare un'interfaccia utente grafica, puoi creare un account del dispositivo per Microsoft Surface Hub con l'[interfaccia utente di Office 365](#create-device-acct-o365) o l'[interfaccia di amministrazione di Exchange](#create-device-acct-eac).</span><span class="sxs-lookup"><span data-stu-id="106ac-107">If you prefer to use a graphical user interface, you can create a device account for your Microsoft Surface Hub with either the [Office 365 UI](#create-device-acct-o365) or the [Exchange Admin Center](#create-device-acct-eac).</span></span>

## <a href="" id="create-device-acct-o365"></a><span data-ttu-id="106ac-108">Creare un account del dispositivo con Office 365</span><span class="sxs-lookup"><span data-stu-id="106ac-108">Create a device account using Office 365</span></span>


1.  <span data-ttu-id="106ac-109">[Creare l'account nell'interfaccia di amministrazione di Microsoft 365](#create-device-acct-o365-admin-ctr).</span><span class="sxs-lookup"><span data-stu-id="106ac-109">[Create the account in the Microsoft 365 Admin Center](#create-device-acct-o365-admin-ctr).</span></span>
2.  <span data-ttu-id="106ac-110">[Creare un criterio cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Microsoft Exchange](#create-device-acct-o365-mbx-policy).</span><span class="sxs-lookup"><span data-stu-id="106ac-110">[Create a mobile device mailbox (ActiveSync) policy from the Microsoft Exchange Admin Center](#create-device-acct-o365-mbx-policy).</span></span>
3.  <span data-ttu-id="106ac-111">[Usare PowerShell per completare la creazione dell'account del dispositivo](#create-device-acct-o365-complete-acct)</span><span class="sxs-lookup"><span data-stu-id="106ac-111">[Use PowerShell to complete device account creation](#create-device-acct-o365-complete-acct).</span></span>
4.  <span data-ttu-id="106ac-112">[Usare PowerShell per configurare le proprietà di Exchange dell'account](#create-device-acct-o365-configure-exch-prop).</span><span class="sxs-lookup"><span data-stu-id="106ac-112">[Use PowerShell to configure Exchange properties of the account](#create-device-acct-o365-configure-exch-prop).</span></span>
5.  <span data-ttu-id="106ac-113">[Abilitare l'account con Skype for Business](#create-device-acct-o365-skype-for-business).</span><span class="sxs-lookup"><span data-stu-id="106ac-113">[Enable the account with Skype for Business](#create-device-acct-o365-skype-for-business).</span></span>

### <a href="" id="create-device-acct-o365-admin-ctr"></a><span data-ttu-id="106ac-114">Creare l'account nell'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="106ac-114">Create the account in the admin center</span></span>

1.  <span data-ttu-id="106ac-115">Accedere a Office 365 visitando [https://portal.office.com](https://portal.office.com) .</span><span class="sxs-lookup"><span data-stu-id="106ac-115">Sign in to Office 365 by visiting [https://portal.office.com](https://portal.office.com).</span></span>

2.  <span data-ttu-id="106ac-116">Specifica le credenziali di amministratore per il tuo tenant di Office 365.</span><span class="sxs-lookup"><span data-stu-id="106ac-116">Provide the admin credentials for your Office 365 tenant.</span></span> <span data-ttu-id="106ac-117">In questo modo è possibile usare l'interfaccia di amministrazione di Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="106ac-117">This will take you to your Microsoft 365 Admin Center.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Microsoft 365.](images/setupdeviceaccto365-02.png)

3. <span data-ttu-id="106ac-119">Nell'interfaccia di amministrazione passare a **risorse** nel riquadro sinistro e quindi fare clic su **sale & attrezzature**.</span><span class="sxs-lookup"><span data-stu-id="106ac-119">In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Opzione camere & attrezzature nell'interfaccia di amministrazione](images/room-equipment.png)

4. <span data-ttu-id="106ac-121">Fai clic su **Aggiungi** per creare un nuovo account Sala.</span><span class="sxs-lookup"><span data-stu-id="106ac-121">Click **Add** to create a new Room account.</span></span> <span data-ttu-id="106ac-122">Immetti un indirizzo di posta elettronica e un nome visualizzato per l'account, quindi fai clic su **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="106ac-122">Enter a display name and email address for the account, and then click **Add**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Creare una finestra per un nuovo account sala](images/room-add.png)

5. <span data-ttu-id="106ac-124">Seleziona l'account Sala appena creato nell'elenco Utenti attivi.</span><span class="sxs-lookup"><span data-stu-id="106ac-124">Select the Room account you just created in the Active Users list.</span></span> <span data-ttu-id="106ac-125">Nel pannello di destra sono elencate le proprietà dell'account e diverse azioni facoltative.</span><span class="sxs-lookup"><span data-stu-id="106ac-125">In the right panel, you can see the account properties and several optional actions.</span></span> <span data-ttu-id="106ac-126">Fai clic su **Reimposta password** per modificare la password e deseleziona **Chiedere all'utente di cambiare la password al primo accesso** in quanto non è possibile cambiare la password dal flusso di accesso di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="106ac-126">Click **Reset password** to change the password, and unselect **Make this user change their password when they first sign in**, because it is not possible to change the password from the Surface Hub sign-in flow.</span></span>

6. <span data-ttu-id="106ac-127">Nella sezione **Licenza assegnata** fai clic su **Modifica** e quindi fai clic sulla freccia in giù accanto alla licenza appropriata per visualizzare i dettagli.</span><span class="sxs-lookup"><span data-stu-id="106ac-127">In the **Assigned license** section, click **Edit**, and then click the dropdown arrow next to the appropriate license to expand the details.</span></span> <span data-ttu-id="106ac-128">Seleziona una posizione utente e, nell'elenco delle licenze, attiva **Skype for Business Online (Piano 2)** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="106ac-128">Select a user location, and in the list of licenses, toggle on **Skype for Business Online (Plan 2)**, and then click **Save**.</span></span> <span data-ttu-id="106ac-129">La licenza può variare a seconda dell'organizzazione, ad esempio potresti avere Piano 2 o Piano 3.</span><span class="sxs-lookup"><span data-stu-id="106ac-129">The license may vary depending on your organization (for example, you might have Plan 2 or Plan 3).</span></span>

### <a href="" id="create-device-acct-o365-mbx-policy"></a><span data-ttu-id="106ac-130">Creare criteri cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-130">Create a mobile device mailbox (ActiveSync) policy from the Exchange Admin Center</span></span>

1.  <span data-ttu-id="106ac-131">Nel riquadro sinistro dell'interfaccia di amministrazione fare clic su **amministratore**e quindi su **Exchange**.</span><span class="sxs-lookup"><span data-stu-id="106ac-131">In the admin center’s left panel, click **ADMIN**, and then click **Exchange**.</span></span>

    > [!div class="mx-imgBorder"]
    > ![interfaccia di amministrazione che Mostra gli utenti attivi di Exchange.](images/setupdeviceaccto365-08.png)

2.  <span data-ttu-id="106ac-133">Verrà aperta un'altra scheda nel browser per permetterti di accedere all'interfaccia di amministrazione di Exchange, in cui puoi creare e configurare l'impostazione della cassetta postale per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="106ac-133">This will open another tab on your browser to take you to the Exchange Admin Center, where you can create and set the Mailbox Setting for Surface Hub.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-09.png)

3.  <span data-ttu-id="106ac-135">Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e quindi fai clic su **Criteri della cassetta postale dei dispositivi mobili**.</span><span class="sxs-lookup"><span data-stu-id="106ac-135">To create a Mobile Device Mailbox Policy, click **Mobile** from the left panel and then click **Mobile device mailbox policies**.</span></span> <span data-ttu-id="106ac-136">Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account.</span><span class="sxs-lookup"><span data-stu-id="106ac-136">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="106ac-137">In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="106ac-137">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Exchange - creazione di criteri cassetta postale per dispositivi mobili.](images/setupdeviceaccto365-10.png)

4.  <span data-ttu-id="106ac-139">Per creare un nuovo criterio cassetta postale per dispositivi mobili di Surface Hub, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio.</span><span class="sxs-lookup"><span data-stu-id="106ac-139">To create a New Surface Hub mobile device mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="106ac-140">Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*.</span><span class="sxs-lookup"><span data-stu-id="106ac-140">For the name, provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="106ac-141">Verifica che il criterio non richieda una password per i dispositivi assegnati, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="106ac-141">Make sure the policy does not require a password for the devices assigned to, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![Immagine che mostra il nuovo criterio per dispositivi mobili](images/setupdeviceaccto365-11.png)

5.  <span data-ttu-id="106ac-143">Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'**interfaccia di amministrazione di Exchange** per visualizzare il nuovo criterio nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="106ac-143">After you have created the new mobile device mailbox policy, go back to the **Exchange Admin Center** and you will see the new policy listed.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Immagine con il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a><span data-ttu-id="106ac-145">Usare Windows PowerShell per completare la creazione dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="106ac-145">Use PowerShell to complete device account creation</span></span>

<span data-ttu-id="106ac-146">A partire da questo momento, dovrai completare il processo di creazione dell'account usando PowerShell per definire alcune configurazioni.</span><span class="sxs-lookup"><span data-stu-id="106ac-146">From here on, you'll need to finish the account creation process using PowerShell to set up some configuration.</span></span>

<span data-ttu-id="106ac-147">Per eseguire i cmdlet usati da questi script di PowerShell, devi installare i seguenti componenti per la console PowerShell di amministrazione:</span><span class="sxs-lookup"><span data-stu-id="106ac-147">In order to run cmdlets used by these PowerShell scripts, the following must be installed for the admin PowerShell console:</span></span>

-   [<span data-ttu-id="106ac-148">Microsoft Online Services Sign-In Assistant per professionisti IT-RTW</span><span class="sxs-lookup"><span data-stu-id="106ac-148">Microsoft Online Services Sign-In Assistant for IT Professionals RTW</span></span>](https://www.microsoft.com/download/details.aspx?id=41950)
-   [<span data-ttu-id="106ac-149">Modulo di Microsoft Azure Active Directory per Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="106ac-149">Windows Azure Active Directory Module for Windows PowerShell</span></span>](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [<span data-ttu-id="106ac-150">Modulo di Windows PowerShell per Skype for Business Online</span><span class="sxs-lookup"><span data-stu-id="106ac-150">Skype for Business Online, Windows PowerShell Module</span></span>](https://www.microsoft.com/download/details.aspx?id=39366)

<span data-ttu-id="106ac-151">Installare il modulo seguente in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="106ac-151">Install the following module in PowerShell.</span></span>

```powershell
install-module AzureAD
Install-module MsOnline
```

### <span data-ttu-id="106ac-152">Connessione ai servizi online</span><span class="sxs-lookup"><span data-stu-id="106ac-152">Connecting to online services</span></span>

1.  <span data-ttu-id="106ac-153">Esegui Windows PowerShell come amministratore.</span><span class="sxs-lookup"><span data-stu-id="106ac-153">Run Windows PowerShell as Administrator.</span></span>

    > [!div class="mx-imgBorder"]
    > ![Immagine che mostra come avviare Windows PowerShell ed eseguirlo come amministratore.](images/setupdeviceaccto365-17.png)

2.  <span data-ttu-id="106ac-155">Crea un oggetto credenziali, crea una nuova sessione che si connette a Skype for Business Online e specifica l'account amministratore tenant globale, quindi fai clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="106ac-155">Create a Credentials object, then create a new session that connects to Skype for Business Online, and provide the global tenant administrator account, then click **OK**.</span></span>

    ![Immagine per la richiesta di credenziali di Windows PowerShell.](images/setupdeviceaccto365-18.png)

3.  <span data-ttu-id="106ac-157">Per connetterti a Microsoft Online Services, esegui:</span><span class="sxs-lookup"><span data-stu-id="106ac-157">To connect to Microsoft Online Services, run:</span></span>

    ```powershell
    Connect-MsolService -Credential $Cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-19.png)

4.  <span data-ttu-id="106ac-159">A questo punto, per connetterti ai servizi Skype for Business Online, esegui:</span><span class="sxs-lookup"><span data-stu-id="106ac-159">Now to connect to Skype for Business Online Services, run:</span></span>

    ```powershell
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-20.png)

5.  <span data-ttu-id="106ac-161">Infine, per connetterti ai servizi Exchange Online, esegui:</span><span class="sxs-lookup"><span data-stu-id="106ac-161">Finally, to connect to Exchange Online Services, run:</span></span>

    ```powershell
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-21.png)

6.  <span data-ttu-id="106ac-163">Adesso devi importare la sessione di Skype for Business Online e la sessione di Exchange Online che hai appena creato, da cui verranno importati i comandi di Exchange e Skype per consentirti di usarli in locale.</span><span class="sxs-lookup"><span data-stu-id="106ac-163">Now you have to import the Skype for Business Online Session and the Exchange Online session you have just created, which will import the Exchange and Skype Commands so you can use them locally.</span></span>

    ```powershell
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    <span data-ttu-id="106ac-164">Tieni presente che il completamento di questa operazione può richiedere molto tempo.</span><span class="sxs-lookup"><span data-stu-id="106ac-164">Note that this could take a while to complete.</span></span>

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-22.png)

7.  <span data-ttu-id="106ac-166">Dopo la connessione ai servizi online devi eseguire altri cmdlet per configurare l'account come account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="106ac-166">Once you’re connected to the online services you need to run a few more cmdlets to configure this account as a Surface Hub device account.</span></span>

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a><span data-ttu-id="106ac-167">Usare PowerShell per configurare le proprietà di Exchange dell'account</span><span class="sxs-lookup"><span data-stu-id="106ac-167">Use PowerShell to configure Exchange properties of the account</span></span>

<span data-ttu-id="106ac-168">Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="106ac-168">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="106ac-169">Userai l'indirizzo e-mail dell'account del dispositivo per:</span><span class="sxs-lookup"><span data-stu-id="106ac-169">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="106ac-170">Modificare il tipo di cassetta postale da normale a cassetta postale della sala.</span><span class="sxs-lookup"><span data-stu-id="106ac-170">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="106ac-171">Impostare la password e abilitare l'account della cassetta postale della sala</span><span class="sxs-lookup"><span data-stu-id="106ac-171">Set the password and enable the room mailbox account</span></span>
-   <span data-ttu-id="106ac-172">Modificare varie proprietà di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-172">Change various Exchange properties</span></span>
-   <span data-ttu-id="106ac-173">Impostare la password dell'account utente in modo che non scada mai.</span><span class="sxs-lookup"><span data-stu-id="106ac-173">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="106ac-174">Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:</span><span class="sxs-lookup"><span data-stu-id="106ac-174">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="106ac-175">Per archiviare il valore, recuperalo dalla cassetta postale:</span><span class="sxs-lookup"><span data-stu-id="106ac-175">To store the value get it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="106ac-176">Stampa il valore:</span><span class="sxs-lookup"><span data-stu-id="106ac-176">Print the value:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="106ac-177">Vedrai l'indirizzo e-mail corretto.</span><span class="sxs-lookup"><span data-stu-id="106ac-177">You will see the correct email address.</span></span>

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-23.png)

2. <span data-ttu-id="106ac-179">Eseguire il cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="106ac-179">Run the following cmdlet:</span></span>

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  <span data-ttu-id="106ac-180">È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="106ac-180">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="106ac-181">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="106ac-181">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-26.png)

5.  <span data-ttu-id="106ac-183">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="106ac-183">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="106ac-184">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="106ac-184">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ```powershell
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a><span data-ttu-id="106ac-185">Abilitare l'account con Skype for Business</span><span class="sxs-lookup"><span data-stu-id="106ac-185">Enable the account with Skype for Business</span></span>

<span data-ttu-id="106ac-186">Abilita l'account del dispositivo con Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="106ac-186">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="106ac-187">Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="106ac-187">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

-   <span data-ttu-id="106ac-188">Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="106ac-188">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="106ac-189">Il piano deve supportare funzionalità per conferenze.</span><span class="sxs-lookup"><span data-stu-id="106ac-189">The plan needs to support conferencing capability.</span></span>
-   <span data-ttu-id="106ac-190">Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.</span><span class="sxs-lookup"><span data-stu-id="106ac-190">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
-   <span data-ttu-id="106ac-191">Gli utenti tenant devono avere cassette postali di Exchange.</span><span class="sxs-lookup"><span data-stu-id="106ac-191">Your tenant users must have Exchange mailboxes.</span></span>
-   <span data-ttu-id="106ac-192">L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="106ac-192">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1.  <span data-ttu-id="106ac-193">Per iniziare, crea una sessione di PowerShell remota da un PC.</span><span class="sxs-lookup"><span data-stu-id="106ac-193">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  <span data-ttu-id="106ac-194">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="106ac-194">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

    ```powershell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

     <span data-ttu-id="106ac-195">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="106ac-195">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

    ```powershell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a><span data-ttu-id="106ac-196">Creare un account del dispositivo tramite l'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-196">Create a device account using the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="106ac-197">Questo metodo funziona solo se si esegue la sincronizzazione da un Active Directory locale.</span><span class="sxs-lookup"><span data-stu-id="106ac-197">This method will only work if you are syncing from an on-premises Active Directory.</span></span>

<span data-ttu-id="106ac-198">Puoi usare l'interfaccia di amministrazione di Exchange per creare un account del dispositivo:</span><span class="sxs-lookup"><span data-stu-id="106ac-198">You can use the Exchange Admin Center to create a device account:</span></span>

1.  <span data-ttu-id="106ac-199">[Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange](#create-device-acct-exch-admin-ctr).</span><span class="sxs-lookup"><span data-stu-id="106ac-199">[Create an account and mailbox with the Exchange Admin Center](#create-device-acct-exch-admin-ctr).</span></span>
2.  <span data-ttu-id="106ac-200">[Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange](#create-device-acct-exch-mbx-policy).</span><span class="sxs-lookup"><span data-stu-id="106ac-200">[Create a mobile device mailbox policy from the Exchange Admin Center](#create-device-acct-exch-mbx-policy).</span></span>
3.  <span data-ttu-id="106ac-201">[Usare PowerShell per configurare l'account](#create-device-acct-exch-powershell-conf).</span><span class="sxs-lookup"><span data-stu-id="106ac-201">[Use PowerShell to configure the account](#create-device-acct-exch-powershell-conf).</span></span>
4.  <span data-ttu-id="106ac-202">[Abilitare l'account con Skype for Business](#create-device-acct-exch-skype-for-business).</span><span class="sxs-lookup"><span data-stu-id="106ac-202">[Enable the account with Skype for Business](#create-device-acct-exch-skype-for-business).</span></span>

### <a href="" id="create-device-acct-exch-admin-ctr"></a><span data-ttu-id="106ac-203">Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-203">Create an account and mailbox with the Exchange Admin Center</span></span>

1.  <span data-ttu-id="106ac-204">Accedi all'interfaccia di amministrazione di Exchange usando le credenziali di amministratore di Exchange.</span><span class="sxs-lookup"><span data-stu-id="106ac-204">Sign in to your Exchange Admin Center using Exchange admin credentials.</span></span>
2.  <span data-ttu-id="106ac-205">Dall'interfaccia di amministrazione di Exchange passa a **Destinatari** nel pannello sinistro.</span><span class="sxs-lookup"><span data-stu-id="106ac-205">Once you are at the Exchange Admin Center (EAC), navigate to **Recipients** in the left panel.</span></span>

    ![Immagine che mostra le cassette postali nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-01.png)

3.  <span data-ttu-id="106ac-207">Nei controlli sopra l'elenco delle cassette postali scegli **+** per creare una nuova cassetta e specifica i nomi in **Nome visualizzato**, **Nome** e **Nome accesso utente** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="106ac-207">On the controls above the list of mailboxess, choose **+** to create a new one, and provide a **Display name**, **Name**, and **User logon name**, and then click **Save**.</span></span>

    ![Immagine che mostra la creazione di una nuova cassetta postale.](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a><span data-ttu-id="106ac-209">Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-209">Create a mobile device mailbox policy from the Exchange Admin Center</span></span>

>[!NOTE]
><span data-ttu-id="106ac-210">Se si vuole creare e assegnare un criterio all'account creato e si usa Exchange 2010, cercare le informazioni corrispondenti relative alla creazione e all'assegnazione dei criteri quando si usa EMC (Exchange Management Console).</span><span class="sxs-lookup"><span data-stu-id="106ac-210">If you want to create and assign a policy to the account you created, and are using Exchange 2010, look up the corresponding information regarding policy creation and policy assignment when using the EMC (Exchange management console).</span></span>

 

1.  <span data-ttu-id="106ac-211">Accedi all'interfaccia di amministrazione di Exchange.</span><span class="sxs-lookup"><span data-stu-id="106ac-211">Go to the Exchange Admin Center.</span></span>

    ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-03.png)

2.  <span data-ttu-id="106ac-213">Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e fai clic su **Criteri della cassetta postale dei dispositivi mobili**.</span><span class="sxs-lookup"><span data-stu-id="106ac-213">To create a mobile device mailbox policy, click **Mobile** from the left panel, then **Mobile device mailbox policies**.</span></span> <span data-ttu-id="106ac-214">Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account.</span><span class="sxs-lookup"><span data-stu-id="106ac-214">Surface Hubs require an account with a mobile device mailbox policy that does not require a password, so if you already have an existing policy that matches this requirement, you can apply that policy to the account.</span></span> <span data-ttu-id="106ac-215">In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="106ac-215">Otherwise use the following steps to create a new one to be used only for Surface Hub device accounts.</span></span>

    ![Immagine che mostra l'uso dell'interfaccia di amministrazione di Exchange per creare un criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-05.png)

3.  <span data-ttu-id="106ac-217">Per creare un nuovo criterio cassetta postale per l'account del dispositivo mobile, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio.</span><span class="sxs-lookup"><span data-stu-id="106ac-217">To create a new mobile device account mailbox policy, click the **+** button from the controls above the list of policies to add a new policy.</span></span> <span data-ttu-id="106ac-218">Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*.</span><span class="sxs-lookup"><span data-stu-id="106ac-218">For the name provide a name that will help you distinguish this policy from other device accounts (for example, *SurfaceHubDeviceMobilePolicy*).</span></span> <span data-ttu-id="106ac-219">Poiché il criterio non deve essere protetto da password, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="106ac-219">The policy must not be password-protected, so make sure **Require a Password** remains unchecked, then click **Save**.</span></span>

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-06.png)

4.  <span data-ttu-id="106ac-221">Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'interfaccia di amministrazione di Exchange per visualizzare il nuovo criterio nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="106ac-221">After you have created the new mobile device mailbox policy, go back to the Exchange Admin Center and you will see the new policy listed.</span></span>

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-07.png)

5.  <span data-ttu-id="106ac-223">Per applicare il criterio di ActiveSync senza usare PowerShell, puoi procedere come segue:</span><span class="sxs-lookup"><span data-stu-id="106ac-223">To apply the ActiveSync policy without using PowerShell, you can do the following:</span></span>

    -   <span data-ttu-id="106ac-224">Nell'interfaccia di amministrazione di Exchange fai clic su **Destinatari** &gt; **Cassette postali** e seleziona una cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="106ac-224">In the EAC, click **Recipients** &gt; **Mailboxes** and select a mailbox.</span></span>

        ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-08.png)

    -   <span data-ttu-id="106ac-226">Nel riquadro **Dettagli** scorri fino a **Funzionalità telefoniche e vocali** e fai clic su **Visualizza dettagli** per visualizzare la schermata **Dettagli dispositivo mobile**.</span><span class="sxs-lookup"><span data-stu-id="106ac-226">In the **Details** pane, scroll to **Phone and Voice Features** and click **View details** to display the **Mobile Device Details** screen.</span></span>

        ![Immagine che mostra i dettagli delle cassette postali.](images/setupdeviceacctexch-09.png)

    -   <span data-ttu-id="106ac-228">Vengono visualizzati i criteri cassetta postale per dispositivi mobili attualmente assegnati.</span><span class="sxs-lookup"><span data-stu-id="106ac-228">The mobile device mailbox policy that’s currently assigned is displayed.</span></span> <span data-ttu-id="106ac-229">Per modificare i criteri cassetta postale per dispositivi mobili, fai clic su **Sfoglia**.</span><span class="sxs-lookup"><span data-stu-id="106ac-229">To change the mobile device mailbox policy, click **Browse**.</span></span>

        ![Immagine che mostra il criterio cassetta postale per dispositivi mobili attualmente assegnato.](images/setupdeviceacctexch-10.png)

    -   <span data-ttu-id="106ac-231">Scegli i criteri cassetta postale per dispositivi mobili appropriati nell'elenco, fai clic su **OK** e quindi fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="106ac-231">Choose the appropriate mobile device mailbox policy from the list, click **OK** and then click **Save**.</span></span>

        ![Immagine che mostra l'elenco dei criteri cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a><span data-ttu-id="106ac-233">Usare PowerShell per configurare l'account</span><span class="sxs-lookup"><span data-stu-id="106ac-233">Use PowerShell to configure the account</span></span>

<span data-ttu-id="106ac-234">Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="106ac-234">Now that you're connected to the online services, you can finish setting up the device account.</span></span> <span data-ttu-id="106ac-235">Userai l'indirizzo e-mail dell'account del dispositivo per:</span><span class="sxs-lookup"><span data-stu-id="106ac-235">You'll use the device account email address to:</span></span>

-   <span data-ttu-id="106ac-236">Modificare il tipo di cassetta postale da normale a cassetta postale della sala.</span><span class="sxs-lookup"><span data-stu-id="106ac-236">Change the mailbox type from regular to room.</span></span>
-   <span data-ttu-id="106ac-237">Modificare varie proprietà di Exchange</span><span class="sxs-lookup"><span data-stu-id="106ac-237">Change various Exchange properties</span></span>
-   <span data-ttu-id="106ac-238">Impostare la password dell'account utente in modo che non scada mai.</span><span class="sxs-lookup"><span data-stu-id="106ac-238">Set the user account password to never expire.</span></span>

1.  <span data-ttu-id="106ac-239">Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:</span><span class="sxs-lookup"><span data-stu-id="106ac-239">You’ll need to enter the account’s mail address and create a variable with that value:</span></span>

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    <span data-ttu-id="106ac-240">Per archiviare il valore, recuperalo dalla cassetta postale:</span><span class="sxs-lookup"><span data-stu-id="106ac-240">To store the value got it from the mailbox:</span></span>

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    <span data-ttu-id="106ac-241">Stampa il valore eseguendo:</span><span class="sxs-lookup"><span data-stu-id="106ac-241">Print the value by running:</span></span>

    ```powershell
    $strEmail
    ```

    <span data-ttu-id="106ac-242">Vedrai l'indirizzo e-mail corretto.</span><span class="sxs-lookup"><span data-stu-id="106ac-242">You will see the correct email address.</span></span>

2.  <span data-ttu-id="106ac-243">È necessario convertire l'account in una cassetta postale della sala, quindi eseguire:</span><span class="sxs-lookup"><span data-stu-id="106ac-243">You need to convert the account into a room mailbox, so run:</span></span>

    ```powershell
    Set-Mailbox $strEmail -Type Room
    ```

3.  <span data-ttu-id="106ac-244">Affinché l'account del dispositivo possa essere autenticato in un dispositivo Surface Hub, devi abilitare l'account della cassetta postale della sala e impostare una password, in modo che l'account possa essere usato dal dispositivo per ottenere informazioni sulle riunioni tramite ActiveSync e per accedere a Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="106ac-244">In order for the device account to be authenticated on a Surface Hub, you need to enable the room mailbox account and set a password, so the account can be used by the device to get meeting information using ActiveSync and log in to Skype for Business.</span></span>

    ```powershell
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  <span data-ttu-id="106ac-245">È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni.</span><span class="sxs-lookup"><span data-stu-id="106ac-245">Various Exchange properties can be set on the device account to improve the meeting experience.</span></span> <span data-ttu-id="106ac-246">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="106ac-246">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  <span data-ttu-id="106ac-247">A questo punto devi impostare alcune proprietà in AD.</span><span class="sxs-lookup"><span data-stu-id="106ac-247">Now we have to set some properties in AD.</span></span> <span data-ttu-id="106ac-248">A tale scopo, ti serve l'alias dell'account (la parte dell'UPN che precede "@").</span><span class="sxs-lookup"><span data-stu-id="106ac-248">To do that, you need the alias of the account (this is the part of the UPN that becomes before the “@”).</span></span>

    ```powershell
    $strAlias = “<your device account’s alias>”
    ```

6.  <span data-ttu-id="106ac-249">Per poter eseguire l'autenticazione con un dispositivo Surface Hub, l'utente deve essere abilitato in AD.</span><span class="sxs-lookup"><span data-stu-id="106ac-249">The user needs to be enabled in AD before it can authenticate with a Surface Hub.</span></span> <span data-ttu-id="106ac-250">Esegui:</span><span class="sxs-lookup"><span data-stu-id="106ac-250">Run:</span></span>

    ```powershell
    Set-ADUser $strAlias -Enabled $True
    ```

7.  <span data-ttu-id="106ac-251">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="106ac-251">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="106ac-252">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="106ac-252">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

    ```powershell
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a><span data-ttu-id="106ac-253">Abilitare l'account con Skype for Business</span><span class="sxs-lookup"><span data-stu-id="106ac-253">Enable the account with Skype for Business</span></span>

<span data-ttu-id="106ac-254">Abilita l'account del dispositivo con Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="106ac-254">Enable the device account with Skype for Business.</span></span>

<span data-ttu-id="106ac-255">Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:</span><span class="sxs-lookup"><span data-stu-id="106ac-255">In order to enable Skype for Business, your environment will need to meet the following prerequisites:</span></span>

- <span data-ttu-id="106ac-256">Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online.</span><span class="sxs-lookup"><span data-stu-id="106ac-256">You'll need to have Skype for Business Online Standalone Plan 2 or higher in your O365 plan.</span></span> <span data-ttu-id="106ac-257">Il piano deve supportare funzionalità per conferenze.</span><span class="sxs-lookup"><span data-stu-id="106ac-257">The plan needs to support conferencing capability.</span></span>
- <span data-ttu-id="106ac-258">Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.</span><span class="sxs-lookup"><span data-stu-id="106ac-258">If you need Enterprise Voice (PSTN telephony) using telephony service providers for the Surface Hub, you need Skype for Business Online Standalone Plan 3.</span></span>
- <span data-ttu-id="106ac-259">Gli utenti tenant devono avere cassette postali di Exchange.</span><span class="sxs-lookup"><span data-stu-id="106ac-259">Your tenant users must have Exchange mailboxes.</span></span>
- <span data-ttu-id="106ac-260">L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="106ac-260">Your Surface Hub account does require a Skype for Business Online Standalone Plan 2 or Skype for Business Online Standalone Plan 3 license, but it does not require an Exchange Online license.</span></span>

1. <span data-ttu-id="106ac-261">Per iniziare, crea una sessione di PowerShell remota da un PC.</span><span class="sxs-lookup"><span data-stu-id="106ac-261">Start by creating a remote PowerShell session from a PC.</span></span>

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. <span data-ttu-id="106ac-262">Recuperare il pool di registrazione dell'account Hub Surface.</span><span class="sxs-lookup"><span data-stu-id="106ac-262">Retrieve your Surface Hub account Registrar Pool.</span></span>

   <span data-ttu-id="106ac-263">Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="106ac-263">If you aren't sure what value to use for the `RegistrarPool` parameter in your environment, you can get the value from an existing Skype for Business user using this cmdlet:</span></span>

   ```PowerShell
   Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
   ```

3. <span data-ttu-id="106ac-264">Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:</span><span class="sxs-lookup"><span data-stu-id="106ac-264">To enable your Surface Hub account for Skype for Business Server, run this cmdlet:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```
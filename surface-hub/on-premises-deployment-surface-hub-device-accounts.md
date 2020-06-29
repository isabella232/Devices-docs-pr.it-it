---
title: Distribuzione locale a foresta singola (Surface Hub)
description: Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a foresta singola.
ms.assetid: 80E12195-A65B-42D1-8B84-ECC3FCBAAFC6
ms.reviewer: ''
manager: laurawi
keywords: distribuzione a foresta singola, distribuzione locale, account del dispositivo, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.date: 08/28/2018
ms.localizationpriority: medium
ms.openlocfilehash: 37b157268769ddcdeaef67b7e19cc7260cd392b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833644"
---
# <span data-ttu-id="5ca88-104">Distribuzione locale per Surface Hub in un ambiente a foresta singola</span><span class="sxs-lookup"><span data-stu-id="5ca88-104">On-premises deployment for Surface Hub in a single-forest environment</span></span>


<span data-ttu-id="5ca88-105">Questo argomento descrive come aggiungere un account del dispositivo per Microsoft Surface Hub in presenza di una distribuzione locale a foresta singola.</span><span class="sxs-lookup"><span data-stu-id="5ca88-105">This topic explains how you add a device account for your Microsoft Surface Hub when you have a single-forest, on-premises deployment.</span></span>

<span data-ttu-id="5ca88-106">In presenza di una distribuzione locale a foresta singola con Microsoft Exchange 2013 o versioni successive e Skype for Business 2013 o versioni successive, puoi [usare gli script di PowerShell forniti](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) per creare gli account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ca88-106">If you have a single-forest on-premises deployment with Microsoft Exchange 2013 or later and Skype for Business 2013 or later, then you can [use the provided PowerShell scripts](appendix-a-powershell-scripts-for-surface-hub.md#create-on-premises-ps-scripts) to create device accounts.</span></span> <span data-ttu-id="5ca88-107">Se usi una distribuzione a più foreste, vedi [Distribuzione locale per Surface Hub in un ambiente a più foreste](on-premises-deployment-surface-hub-multi-forest.md).</span><span class="sxs-lookup"><span data-stu-id="5ca88-107">If you’re using a multi-forest deployment, see [On-premises deployment for Surface Hub in a multi-forest environment](on-premises-deployment-surface-hub-multi-forest.md).</span></span>

1. <span data-ttu-id="5ca88-108">Avvia una sessione di PowerShell remota da un PC e connettiti a Exchange.</span><span class="sxs-lookup"><span data-stu-id="5ca88-108">Start a remote PowerShell session from a PC and connect to Exchange.</span></span>

   <span data-ttu-id="5ca88-109">Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.</span><span class="sxs-lookup"><span data-stu-id="5ca88-109">Be sure you have the right permissions set to run the associated cmdlets.</span></span>

   <span data-ttu-id="5ca88-110">Tieni presente che `$strExchangeServer` è il nome di dominio completo (FQDN) del server Exchange, mentre `$strLyncFQDN` è il nome di dominio completo del tuo server Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="5ca88-110">Note here that `$strExchangeServer` is the fully qualified domain name (FQDN) of your Exchange server, and `$strLyncFQDN` is the FQDN of your Skype for Business server.</span></span>

   ```PowerShell
   Set-ExecutionPolicy Unrestricted
   $org='contoso.microsoft.com'
   $cred=Get-Credential $admin@$org
   $sessExchange = New-PSSession -ConfigurationName microsoft.exchange -Credential $cred -AllowRedirection -Authentication Kerberos -ConnectionUri "http://$strExchangeServer/powershell" -WarningAction SilentlyContinue
   $sessLync = New-PSSession -Credential $cred -ConnectionURI "https://$strLyncFQDN/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
   Import-PSSession $sessExchange
   Import-PSSession $sessLync
   ```

2. <span data-ttu-id="5ca88-111">Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente.</span><span class="sxs-lookup"><span data-stu-id="5ca88-111">After establishing a session, you’ll either create a new mailbox and enable it as a RoomMailboxAccount, or change the settings for an existing room mailbox.</span></span> <span data-ttu-id="5ca88-112">In questo modo l'account potrà essere autenticato in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5ca88-112">This will allow the account to authenticate into the Surface Hub.</span></span>

   <span data-ttu-id="5ca88-113">Se devi modificare una cassetta postale delle risorse esistente:</span><span class="sxs-lookup"><span data-stu-id="5ca88-113">If you're changing an existing resource mailbox:</span></span>

   ```PowerShell
   Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```

   <span data-ttu-id="5ca88-114">Se devi creare una nuova cassetta postale delle risorse:</span><span class="sxs-lookup"><span data-stu-id="5ca88-114">If you’re creating a new resource mailbox:</span></span>

   ```PowerShell
   New-Mailbox -UserPrincipalName HUB01@contoso.com -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
> [!IMPORTANT] 
> <span data-ttu-id="5ca88-115">È necessario che l'autenticazione di base della directory virtuale di ActiveSync sia abilitata perché l'hub Surface non è in grado di eseguire l'autenticazione usando altri metodi di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="5ca88-115">ActiveSync Virtual Directory Basic Authentication is required to be enabled as the Surface Hub is unable to authenticate using other authentication methods.</span></span>

3. <span data-ttu-id="5ca88-116">Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.</span><span class="sxs-lookup"><span data-stu-id="5ca88-116">After setting up the mailbox, you will need to either create a new Exchange ActiveSync policy, or use a compatible existing policy.</span></span>

   <span data-ttu-id="5ca88-117">I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False.</span><span class="sxs-lookup"><span data-stu-id="5ca88-117">Surface Hubs are only compatible with device accounts that have an ActiveSync policy where the **PasswordEnabled** property is set to False.</span></span> <span data-ttu-id="5ca88-118">Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.</span><span class="sxs-lookup"><span data-stu-id="5ca88-118">If this isn’t set properly, then Exchange services on the Surface Hub (mail, calendar, and joining meetings), will not be enabled.</span></span>

   <span data-ttu-id="5ca88-119">Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs".</span><span class="sxs-lookup"><span data-stu-id="5ca88-119">If you haven’t created a compatible policy yet, use the following cmdlet—this one creates a policy called "Surface Hubs".</span></span> <span data-ttu-id="5ca88-120">Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ca88-120">Once it’s created, you can apply the same policy to other device accounts.</span></span>

   ```PowerShell
   $easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
   ```

   <span data-ttu-id="5ca88-121">Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="5ca88-121">Once you have a compatible policy, then you will need to apply the policy to the device account.</span></span> <span data-ttu-id="5ca88-122">I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse.</span><span class="sxs-lookup"><span data-stu-id="5ca88-122">However, policies can only be applied to user accounts and not resource mailboxes.</span></span> <span data-ttu-id="5ca88-123">Devi convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitarla e impostare di nuovo la password.</span><span class="sxs-lookup"><span data-stu-id="5ca88-123">You need to convert the mailbox into a user type, apply the policy, and then convert it back into a mailbox—you may need to re-enable it and set the password again too.</span></span>

   ```PowerShell
   $acctUpn = Get-Mailbox -Identity "<mailbox identity>"
   $credNewAccount.Password = ConvertTo-SecureString -String <room mailbox password> -AsPlainText -Force
   Set-Mailbox $acctUpn -Type Regular
   Set-CASMailbox $acctUpn -ActiveSyncMailboxPolicy $easPolicy
   Set-Mailbox $acctUpn -Type Room
   Set-Mailbox $acctUpn -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```

4. <span data-ttu-id="5ca88-124">È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni degli utenti.</span><span class="sxs-lookup"><span data-stu-id="5ca88-124">Various Exchange properties can be set on the device account to improve the meeting experience for people.</span></span> <span data-ttu-id="5ca88-125">Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="5ca88-125">You can see which properties need to be set in the [Exchange properties](exchange-properties-for-surface-hub-device-accounts.md) section.</span></span>

   ```PowerShell
   Set-CalendarProcessing -Identity $acctUpn -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
   Set-CalendarProcessing -Identity $acctUpn -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
   ```

5. <span data-ttu-id="5ca88-126">Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ca88-126">If you decide to have the password not expire, you can set that with PowerShell cmdlets too.</span></span> <span data-ttu-id="5ca88-127">Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).</span><span class="sxs-lookup"><span data-stu-id="5ca88-127">See [Password management](password-management-for-surface-hub-device-accounts.md) for more information.</span></span>

   ```PowerShell
   Set-AdUser $acctUpn -PasswordNeverExpires $true
   ```

6. <span data-ttu-id="5ca88-128">Abilita l'account in Active Directory in modo che esegua l'autenticazione nel dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5ca88-128">Enable the account in Active Directory so it will authenticate to the Surface Hub.</span></span>

   ```PowerShell
   Set-AdUser $acctUpn -Enabled $true
   ```

7. <span data-ttu-id="5ca88-129">Abilita l'account del dispositivo con Skype for Business abilitando l'account AD di Surface Hub in un pool Skype for Business Server:</span><span class="sxs-lookup"><span data-stu-id="5ca88-129">Enable the device account with Skype for Business by enabling your Surface Hub AD account on a Skype for Business Server pool:</span></span>

   ```PowerShell
   Enable-CsMeetingRoom -SipAddress "sip:HUB01@contoso.com"
    -DomainController DC-ND-001.contoso.com -RegistrarPool LYNCPool15.contoso.com
    -Identity HUB01
   ```

   <span data-ttu-id="5ca88-130">Dovrai usare l'indirizzo SIP (Session Initiation Protocol) e il controller di dominio per il dispositivo Surface Hub, oltre all'identificatore del pool Skype for Business Server e all'identità utente.</span><span class="sxs-lookup"><span data-stu-id="5ca88-130">You'll need to use the Session Initiation Protocol (SIP) address and domain controller for the Surface Hub, along with your own Skype for Business Server pool identifier and user identity.</span></span>

8. <span data-ttu-id="5ca88-131">FACOLTATIVO: puoi anche consentire al dispositivo Surface Hub di effettuare e ricevere chiamate PSTN (Public Switched Telephone Network) abilitando la funzionalità VoIP aziendale per il tuo account.</span><span class="sxs-lookup"><span data-stu-id="5ca88-131">OPTIONAL: You can also allow your Surface Hub to make and receive public switched telephone network (PSTN) phone calls by enabling Enterprise Voice for your account.</span></span> <span data-ttu-id="5ca88-132">La funzionalità VoIP aziendale non è un requisito per Surface Hub, ma se vuoi abilitare la funzionalità di composizione PSTN per il client Surface Hub, ecco come attivarla:</span><span class="sxs-lookup"><span data-stu-id="5ca88-132">Enterprise Voice isn't a requirement for Surface Hub, but if you want PSTN dialing functionality for the Surface Hub client, here's how to enable it:</span></span>

   ```PowerShell
   Set-CsMeetingRoom  -Identity HUB01 -DomainController DC-ND-001.contoso.com -LineURI "tel:+14255550555;ext=50555"  -EnterpriseVoiceEnabled $true
   ```

   <span data-ttu-id="5ca88-133">Anche in questo caso, è necessario sostituire gli esempi di Domain controller e numero di telefono forniti con le proprie informazioni.</span><span class="sxs-lookup"><span data-stu-id="5ca88-133">Again, you need to replace the provided domain controller and phone number examples with your own information.</span></span> <span data-ttu-id="5ca88-134">Il valore del parametro `$true` rimane invariato.</span><span class="sxs-lookup"><span data-stu-id="5ca88-134">The parameter value `$true` stays the same.</span></span>
    

 ## <span data-ttu-id="5ca88-135">Disabilitare la posta elettronica anonima e la messaggistica istantanea</span><span class="sxs-lookup"><span data-stu-id="5ca88-135">Disable anonymous email and IM</span></span>




<span data-ttu-id="5ca88-136">Surface hub usa un account di dispositivo per inviare servizi di posta elettronica e di collaborazione (messaggistica istantanea, video, voce).</span><span class="sxs-lookup"><span data-stu-id="5ca88-136">Surface Hub uses a device account to provide email and collaboration services (IM, video, voice).</span></span> <span data-ttu-id="5ca88-137">Questo account di dispositivo viene usato come identità di origine (il partito "da") durante l'invio di posta elettronica, messaggistica istantanea e immissione delle chiamate.</span><span class="sxs-lookup"><span data-stu-id="5ca88-137">This device account is used as the originating identity (the “from” party) when sending email, IM, and placing calls.</span></span> <span data-ttu-id="5ca88-138">Dato che questo account non proviene da un singolo utente identificabile, viene considerato "anonimo" perché è stato originato dall'account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5ca88-138">As this account is not coming from an individual, identifiable user, it is deemed “anonymous” because it originated from the Surface Hub's device account.</span></span>  

<span data-ttu-id="5ca88-139">Si supponga di avere un criterio client per utente assegnato a ogni dispositivo della sala riunioni con un'identità di **SurfaceHubPolicy**.</span><span class="sxs-lookup"><span data-stu-id="5ca88-139">Assume you have a per-user client policy assigned to each meeting room device with an identity of **SurfaceHubPolicy**.</span></span> <span data-ttu-id="5ca88-140">Per disabilitare la posta elettronica e la messaggistica anonima, è possibile aggiungere un clientPolicyEntry ai criteri client usando i comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="5ca88-140">To disable anonymous email and messaging, you add a clientPolicyEntry to this client policy by using the following commands.</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $false
$clientPolicy = Get-CsClientPolicy -Identity SurfaceHubPolicy
$clientPolicy.PolicyEntry.Add($policyEntry)
Set-CsClientPolicy -Instance $clientPolicy
```

<span data-ttu-id="5ca88-141">Per verificare che il criterio sia stato impostato:</span><span class="sxs-lookup"><span data-stu-id="5ca88-141">To verify that the policy has been set:</span></span>

```
Select-Object -InputObject $clientPolicy -Property PolicyEntry
```

<span data-ttu-id="5ca88-142">L'output deve essere:</span><span class="sxs-lookup"><span data-stu-id="5ca88-142">The output should be:</span></span>

```
PolicyEntry
-----------
{Name=AllowResourceAccountSendMessage;Value=False}
```
    
    
<span data-ttu-id="5ca88-143">Per modificare la voce dei criteri:</span><span class="sxs-lookup"><span data-stu-id="5ca88-143">To change the policy entry:</span></span>

```
$policyEntry =  New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Replace = $policyEntry}
``` 
    
<span data-ttu-id="5ca88-144">Per rimuovere la voce dei criteri:</span><span class="sxs-lookup"><span data-stu-id="5ca88-144">To remove the policy entry:</span></span>

```
$policyEntry = New-CsClientPolicyEntry -Name AllowResourceAccountSendMessage -value $true
$clientPolicy | Set-CsClientPolicy -PolicyEntry @{Remove = $policyEntry}
```

 






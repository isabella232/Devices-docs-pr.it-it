---
title: Foglio di lavoro per la configurazione (Surface Hub)
description: Quando al termine della pre-installazione vuoi avviare la prima configurazione di Surface Hub, accertati di avere tutte le info elencate in questa sezione.
ms.assetid: AC6F925B-BADE-48F5-8D53-8B6FFF6EE3EB
ms.reviewer: ''
manager: laurawi
keywords: foglio di lavoro per la configurazione, pre-configurazione, prima configurazione
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: e0c31082669336d3762fd02f46a939aa8b0ff1bc
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833854"
---
# <span data-ttu-id="38bfa-104">Foglio di lavoro per la configurazione (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="38bfa-104">Setup worksheet (Surface Hub)</span></span>


<span data-ttu-id="38bfa-105">Quando al termine della pre-installazione vuoi avviare la prima configurazione del tuo dispositivo Microsoft Surface Hub, accertati di avere tutte le informazioni elencate in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="38bfa-105">When you've finished pre-setup and are ready to start first-time setup for your Microsoft Surface Hub, make sure you have all the information listed in this section.</span></span>

<span data-ttu-id="38bfa-106">Devi compilare un elenco per ogni dispositivo Surface Hub da configurare, anche se alcune informazioni possono essere usate in tutti i dispositivi Surface Hub, come le informazioni sul proxy o le credenziali di dominio.</span><span class="sxs-lookup"><span data-stu-id="38bfa-106">You should fill out one list for each Surface Hub you need to configure, although some information can be used on all Surface Hubs, like the proxy information or domain credentials.</span></span> <span data-ttu-id="38bfa-107">Alcune di queste informazioni potrebbero non essere necessarie, a seconda di come hai scelto di configurare il dispositivo o a seconda di come è configurato l'ambiente per l'infrastruttura dell'organizzazione.</span><span class="sxs-lookup"><span data-stu-id="38bfa-107">Some of this information may not be needed, depending on how you've decided to configure your device, or depending on how the environment is configured for your organization's infrastructure.</span></span>

<table>
<tr>
<th><span data-ttu-id="38bfa-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="38bfa-108">Property</span></span></th>
<th><span data-ttu-id="38bfa-109">In quali casi si usa</span><span class="sxs-lookup"><span data-stu-id="38bfa-109">What this is used for</span></span></th>
<th><span data-ttu-id="38bfa-110">Esempio</span><span class="sxs-lookup"><span data-stu-id="38bfa-110">Example</span></span></th>
<th><span data-ttu-id="38bfa-111">Valore effettivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-111">Actual value</span></span></th>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-112">Informazioni sul proxy</span><span class="sxs-lookup"><span data-stu-id="38bfa-112">Proxy information</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-113">Se la rete usa un proxy per l'accesso alla rete e/o a Internet, devi specificare uno script o informazioni sulla porta o sul server.</span><span class="sxs-lookup"><span data-stu-id="38bfa-113">If your network uses a proxy for network and/or Internet access, you must provide a script or server/port information.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-114">Script proxy:</span><span class="sxs-lookup"><span data-stu-id="38bfa-114">Proxy script:</span></span> <code>http://contoso/proxy.pa</code> </br>
- <span data-ttu-id="38bfa-115">oppure -</span><span class="sxs-lookup"><span data-stu-id="38bfa-115">OR -</span></span> </br>
<span data-ttu-id="38bfa-116">Informazioni sul server e sulla porta: 10.10.10.100, porta 80</span><span class="sxs-lookup"><span data-stu-id="38bfa-116">Server and port info: 10.10.10.100, port 80</span></span>
</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-117">Credenziali di rete wireless (nome utente e password)</span><span class="sxs-lookup"><span data-stu-id="38bfa-117">Wireless network credentials (username and password)</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-118">Se decidi di connettere il tuo dispositivo al Wi-Fi e la rete wireless richiede le credenziali utente.</span><span class="sxs-lookup"><span data-stu-id="38bfa-118">If you decide to connect your device to Wi-Fi, and your wireless network requires user credentials.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-119">admin1@contoso.com, #MiaPassw0rd</span><span class="sxs-lookup"><span data-stu-id="38bfa-119">admin1@contoso.com, #MyPassw0rd</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-120">UPN dell'account del dispositivo o Dominio\nomeutente e password dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-120">Device account UPN or Domain\username and device account password</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-121">Si tratta del nome dell'entità utente (UPN) o del dominio\nomeutente e della password dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-121">This is the User Principal Name (UPN) or the domain\username, and the password of the device account.</span></span> <span data-ttu-id="38bfa-122">La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.</span><span class="sxs-lookup"><span data-stu-id="38bfa-122">Mail, calendar, and Skype for Business depend on a compatible device account.</span></span></p>
</td>
<td>
<p> <span data-ttu-id="38bfa-123">UPN: ConfRoom15@contoso.com, #Passw0rd1</span><span class="sxs-lookup"><span data-stu-id="38bfa-123">UPN: ConfRoom15@contoso.com, #Passw0rd1</span></span> </br>
- <span data-ttu-id="38bfa-124">oppure -</span><span class="sxs-lookup"><span data-stu-id="38bfa-124">OR -</span></span> <br> 
<span data-ttu-id="38bfa-125">Nome utente e dominio: CONTOSO\ConfRoom15, #Passw0rd1</span><span class="sxs-lookup"><span data-stu-id="38bfa-125">Domain and username: CONTOSO\ConfRoom15, #Passw0rd1</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-126">Server Microsoft Exchange dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-126">Device account Microsoft Exchange server</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-127">Si tratta del server Exchange dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-127">This is the device account's Exchange server.</span></span>
<span data-ttu-id="38bfa-128">La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.</span><span class="sxs-lookup"><span data-stu-id="38bfa-128">Mail, calendar, and Skype for Business depend on a compatible device account.</span></span>
<span data-ttu-id="38bfa-129">Per il corretto funzionamento della posta e del calendario, l'account del dispositivo deve avere un server Exchange valido.</span><span class="sxs-lookup"><span data-stu-id="38bfa-129">For mail and calendar to work, the device account must have a valid Exchange server.</span></span> <span data-ttu-id="38bfa-130">Il dispositivo tenterà di trovarlo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="38bfa-130">The device will try to find this automatically.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-131">outlook.office365.com</span><span class="sxs-lookup"><span data-stu-id="38bfa-131">outlook.office365.com</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-132">Indirizzo SIP (Session Initiation Protocol) dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-132">Device account Session Initiation Protocol (SIP) address</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-133">Si tratta dell'indirizzo SIP Skype for Business dell'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-133">This is the device account's Skype for Business SIP address.</span></span>
<span data-ttu-id="38bfa-134">La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.</span><span class="sxs-lookup"><span data-stu-id="38bfa-134">Mail, calendar, and Skype for Business depend on a compatible device account.</span></span>
<span data-ttu-id="38bfa-135">Per il corretto funzionamento di Skype for Business, l'account del dispositivo deve avere un indirizzo SIP valido.</span><span class="sxs-lookup"><span data-stu-id="38bfa-135">For Skype for Business to work, the device account must have a valid SIP address.</span></span> <span data-ttu-id="38bfa-136">Il dispositivo tenterà di trovarlo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="38bfa-136">The device will try to find this automatically.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-137">SIP: ConfRoom15@contoso.com</span><span class="sxs-lookup"><span data-stu-id="38bfa-137">sip: ConfRoom15@contoso.com</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-138">Nome descrittivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-138">Friendly name</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-139">Il nome descrittivo del dispositivo è il nome di broadcast che gli utenti vedranno quando provano a connettersi in modalità wireless a Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="38bfa-139">The friendly name of the device is the broadcast name that people will see when they try to wirelessly connect to the Surface Hub.</span></span> <span data-ttu-id="38bfa-140">Questo nome verrà visualizzato in evidenza sullo schermo di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="38bfa-140">This name will be displayed prominently on the Surface Hub's screen.</span></span>
<span data-ttu-id="38bfa-141">Ti consigliamo di scegliere un nome descrittivo riconoscibile e univoco, in modo che gli utenti possano distinguere un dispositivo Surface Hub da un altro durante il tentativo di connessione.</span><span class="sxs-lookup"><span data-stu-id="38bfa-141">We suggest that the friendly name you choose is recognizable and unique so that people can distinguish one Surface Hub from another when trying to connect.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-142">Sala riunioni 15</span><span class="sxs-lookup"><span data-stu-id="38bfa-142">Conference Room 15</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-143">Nome dispositivo</span><span class="sxs-lookup"><span data-stu-id="38bfa-143">Device name</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-144">Il nome del dispositivo è il nome che verrà usato per l'aggiunta al dominio ed è l'identità che visualizzerai nel provider MDM se il dispositivo è registrato in MDM.</span><span class="sxs-lookup"><span data-stu-id="38bfa-144">The device name is the name that will be used for domain join, and is the identity you will see in your MDM provider if the device is enrolled into MDM.</span></span>
<span data-ttu-id="38bfa-145">Il nome del dispositivo scelto non deve essere uguale a quello di altri dispositivi nel dominio Active Directory dell'utente (se decidi di aggiungere il dispositivo al dominio).</span><span class="sxs-lookup"><span data-stu-id="38bfa-145">The device name you choose must not be the same name as any other device on the user’s Active Directory domain (if you decide to domain join the device).</span></span> <span data-ttu-id="38bfa-146">Il dispositivo non può essere aggiunto al dominio se il nome non è univoco.</span><span class="sxs-lookup"><span data-stu-id="38bfa-146">The device cannot join the domain if its name is not unique.</span></span>
</p>
</td>
<td>
<p><span data-ttu-id="38bfa-147">sala15</span><span class="sxs-lookup"><span data-stu-id="38bfa-147">confroom15</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b><span data-ttu-id="38bfa-148">PER L'AGGIUNTA AD AZURE AD</span><span class="sxs-lookup"><span data-stu-id="38bfa-148">IF YOU'RE JOINING AZURE AD</span></span></b></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-149">Credenziali utente tenant di Azure AD (nome utente e password)</span><span class="sxs-lookup"><span data-stu-id="38bfa-149">Azure AD tenant user credentials (username and password)</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-150">Se decidi di assegnare a persone della tua organizzazione Azure Active Directory (Azure AD) il ruolo di amministratori del dispositivo, devi eseguire l'aggiunta ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="38bfa-150">If you decide to have people in your Azure Active Directory (Azure AD) organization become admins on the device, then you'll need to join Azure AD.</span></span>
<span data-ttu-id="38bfa-151">Per l'aggiunta ad Azure AD, devi avere credenziali utente valide.</span><span class="sxs-lookup"><span data-stu-id="38bfa-151">To join Azure AD, you will need valid user credentials.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-152">admin1@contoso.com, #MiaPassw0rd</span><span class="sxs-lookup"><span data-stu-id="38bfa-152">admin1@contoso.com, #MyPassw0rd</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b><span data-ttu-id="38bfa-153">PER L'AGGIUNTA A UN DOMINIO</span><span class="sxs-lookup"><span data-stu-id="38bfa-153">IF YOU'RE JOINING A DOMAIN</span></span></b></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-154">Dominio per l'aggiunta</span><span class="sxs-lookup"><span data-stu-id="38bfa-154">Domain to join</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-155">Si tratta del dominio a cui dovrai eseguire l'aggiunta per consentire al gruppo di sicurezza scelto di diventare amministratori del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-155">This is the domain you will need to join so that a security group of your choice can be admins for the device.</span></span>
<span data-ttu-id="38bfa-156">Potrebbe servirti il nome di dominio completo (FQDN).</span><span class="sxs-lookup"><span data-stu-id="38bfa-156">You may need the fully qualified domain name (FQDN).</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-157">contoso (nome breve) O contoso.corp.com (FQDN)</span><span class="sxs-lookup"><span data-stu-id="38bfa-157">contoso (short name) OR contoso.corp.com (FQDN)</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-158">Credenziali dell'account di dominio (nome utente e password)</span><span class="sxs-lookup"><span data-stu-id="38bfa-158">Domain account credentials (username and password)</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-159">L'aggiunta a un dominio non può avvenire a meno che non specifichi credenziali dell'account sufficienti per l'aggiunta al dominio.</span><span class="sxs-lookup"><span data-stu-id="38bfa-159">A domain can't be joined unless you provide sufficient account credentials to join the domain.</span></span> <span data-ttu-id="38bfa-160">Dopo aver specificato un dominio per l'aggiunta e le credenziali per l'aggiunta al dominio, il gruppo di sicurezza scelto può modificare le impostazioni nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-160">Once you provide a domain to join and credentials to join the domain, then a security group of your choice can change settings on the device.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-161">admin1, #MiaPassw0rd</span><span class="sxs-lookup"><span data-stu-id="38bfa-161">admin1, #MyPassw0rd</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-162">Alias gruppo di sicurezza amministratori</span><span class="sxs-lookup"><span data-stu-id="38bfa-162">Admin security group alias</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-163">Si tratta di un gruppo di sicurezza in Active Directory (AD). I membri di questo gruppo di sicurezza possono modificare le impostazioni nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-163">This is a security group in your Active Directory (AD); any members of this security group can change settings on the device.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-164">AmministratoriSurfaceHub</span><span class="sxs-lookup"><span data-stu-id="38bfa-164">SurfaceHubAdmins</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b><span data-ttu-id="38bfa-165">SE USI UN AMMINISTRATORE LOCALE</span><span class="sxs-lookup"><span data-stu-id="38bfa-165">IF YOU'RE USING A LOCAL ADMIN</span></span></b></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-166">Credenziali dell'account dell'amministratore locale (nome utente e password)</span><span class="sxs-lookup"><span data-stu-id="38bfa-166">Local admin account credentials (username and password)</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-167">Se decidi di non eseguire l'aggiunta a un dominio AD o ad Azure AD, puoi creare un account amministratore locale nel dispositivo.</span><span class="sxs-lookup"><span data-stu-id="38bfa-167">If you decide not to join an AD domain or Azure AD, you can create a local admin account on the device.</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-168">admin1, #MiaPassw0rd</span><span class="sxs-lookup"><span data-stu-id="38bfa-168">admin1, #MyPassw0rd</span></span></p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b><span data-ttu-id="38bfa-169">SE VUOI INSTALLARE CERTIFICATI O APP</span><span class="sxs-lookup"><span data-stu-id="38bfa-169">IF YOU NEED TO INSTALL CERTIFICATES OR APPS</span></span></b></p>
</td>
</tr>
<tr>
<td>
<p><span data-ttu-id="38bfa-170">Unità USB</span><span class="sxs-lookup"><span data-stu-id="38bfa-170">USB drive</span></span></p>
</td>
<td>
<p><span data-ttu-id="38bfa-171">Se prima della prima esecuzione sai di voler installare certificati o app universali, segui i passaggi descritti in <a href="provisioning-packages-for-certificates-surface-hub.md">Creare pacchetti di provisioning</a>.</span><span class="sxs-lookup"><span data-stu-id="38bfa-171">If you know before first run that you want to install certificates or universal apps, follow the steps in <a href="provisioning-packages-for-certificates-surface-hub.md">Create provisioning packages</a>.</span></span> <span data-ttu-id="38bfa-172">I pacchetti di provisioning verranno creati in un'unità USB.</span><span class="sxs-lookup"><span data-stu-id="38bfa-172">Your provisioning packages will be created on a USB drive.</span></span></p>
</td>
<td>
<p></p>
</td>
<td>
<p></p>
</td>
</tr>
</table> 






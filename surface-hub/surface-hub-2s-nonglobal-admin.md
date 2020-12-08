---
title: Configurare gli account di amministratore non globali in Surface Hub 2S
description: Questo articolo descrive come configurare gli account di amministratore non globali per la gestione di Surface Hub 2S.
keywords: Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 12/07/2020
ms.localizationpriority: Medium
appliesto:
- Surface Hub 2S 2020 Update
ms.openlocfilehash: 647a7bf53e5ca8dc52ddec21ec8393cc574ee95a
ms.sourcegitcommit: 16cc2e8d9dfc5d6e061e0b5b6ddfcf35547643f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "11196810"
---
# <span data-ttu-id="435ae-104">Configurare gli account di amministratore non globali in Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="435ae-104">Configure non Global admin accounts on Surface Hub 2S</span></span>

<span data-ttu-id="435ae-105">Quando si entra in Surface Hub 2S in un dominio di Azure AD, è possibile configurare gli account di amministratore non globali che limitano le autorizzazioni per la gestione dell'app impostazioni in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="435ae-105">When you join Surface Hub 2S to an Azure AD domain, you can configure non Global admin accounts that limit permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="435ae-106">In questo modo puoi usare l'ambito delle autorizzazioni di amministratore per solo hub di Surface 2S e impedire l'accesso di amministratore potenzialmente indesiderato a un intero dominio Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-106">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access an entire Azure AD domain.</span></span> <span data-ttu-id="435ae-107">Prima di iniziare, assicurati che l'hub di Surface 2S sia unito ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-107">Before you begin, make sure your Surface Hub 2S is joined to Azure AD.</span></span> <span data-ttu-id="435ae-108">In caso contrario, dovrai reimpostare Surface Hub 2S e completare il programma di configurazione per la prima volta, out-of-the-box (OOBE), scegliendo l'opzione per partecipare ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-108">If not, you will need to reset Surface Hub 2S and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <span data-ttu-id="435ae-109">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="435ae-109">Summary</span></span> 

<span data-ttu-id="435ae-110">Il processo di creazione di account di amministratore non globali prevede i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="435ae-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="435ae-111">In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per gestire Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="435ae-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub 2S.</span></span>
2. <span data-ttu-id="435ae-112">Ottenere un SID di gruppo di Azure AD usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="435ae-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="435ae-113">Creare un file XML contenente un SID di gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="435ae-114">Creare un gruppo di sicurezza contenente i dispositivi di Surface Hub 2S che verranno gestiti dal gruppo di sicurezza amministratori non globali.</span><span class="sxs-lookup"><span data-stu-id="435ae-114">Create a Security Group containing the Surface Hub 2S devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="435ae-115">Creare un profilo di configurazione personalizzato destinato al gruppo di sicurezza che contiene i dispositivi di Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="435ae-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub 2S devices.</span></span> 


## <span data-ttu-id="435ae-116">Creare gruppi di sicurezza di Azure AD</span><span class="sxs-lookup"><span data-stu-id="435ae-116">Create Azure AD security groups</span></span>

<span data-ttu-id="435ae-117">Creare prima di tutto un gruppo di sicurezza contenente gli account di amministratore.</span><span class="sxs-lookup"><span data-stu-id="435ae-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="435ae-118">Crea quindi un altro gruppo di sicurezza per i dispositivi Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="435ae-118">Then create another security group for Surface Hub devices.</span></span>  

### <span data-ttu-id="435ae-119">Creare un gruppo di sicurezza per gli account di amministratore</span><span class="sxs-lookup"><span data-stu-id="435ae-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="435ae-120">Accedere a Intune tramite l'interfaccia di [amministrazione di Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431) **, selezionare Raggruppa**  >  **nuovo gruppo** > e quindi in tipo di gruppo selezionare **sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="435ae-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="435ae-121">Immettere il nome di un gruppo, ad esempio gli **amministratori locali di Surface Hub** , quindi selezionare **Crea.**</span><span class="sxs-lookup"><span data-stu-id="435ae-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![Creare un gruppo di sicurezza per gli amministratori di hub](images/sh-create-sec-group.png)

3. <span data-ttu-id="435ae-123">Aprire il gruppo, selezionare **membri**e quindi scegliere **Aggiungi membri** per immettere gli account di amministratore che si desidera designare come amministratori non globali in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="435ae-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub 2S.</span></span> <span data-ttu-id="435ae-124">Per ulteriori informazioni sulla creazione di gruppi in Intune, vedere  [aggiungere gruppi per organizzare utenti e dispositivi](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span><span class="sxs-lookup"><span data-stu-id="435ae-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span></span>

### <span data-ttu-id="435ae-125">Creare un gruppo di sicurezza per i dispositivi Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="435ae-125">Create security group for Surface Hub 2S devices</span></span>

1. <span data-ttu-id="435ae-126">Ripetere la procedura precedente per creare un gruppo di sicurezza distinto per i dispositivi hub; ad esempio, i **dispositivi Surface Hub**.</span><span class="sxs-lookup"><span data-stu-id="435ae-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![Creare un gruppo di sicurezza per i dispositivi hub](images/sh-create-sec-group-devices.png) 

## <span data-ttu-id="435ae-128">Ottenere un SID di gruppo di Azure AD usando PowerShell</span><span class="sxs-lookup"><span data-stu-id="435ae-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="435ae-129">Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="435ae-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="435ae-130">Per altre informazioni, vedere [informazioni sui criteri di esecuzione](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span><span class="sxs-lookup"><span data-stu-id="435ae-130">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="435ae-131">[Installare il modulo di PowerShell di Azure](https://docs.microsoft.com/powershell/azure/install-az-ps).</span><span class="sxs-lookup"><span data-stu-id="435ae-131">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="435ae-132">Accedere al tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="435ae-133">Dopo avere effettuato l'accesso al tenant, eseguire il unifiedgroup seguente.</span><span class="sxs-lookup"><span data-stu-id="435ae-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="435ae-134">Verrà chiesto di digitare l'ID oggetto del gruppo Azure AD.</span><span class="sxs-lookup"><span data-stu-id="435ae-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="435ae-135">In Intune selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="435ae-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![Copiare l'ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. <span data-ttu-id="435ae-137">Eseguire la seguente unifiedgroup per ottenere il SID del gruppo di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="435ae-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="435ae-138">Incollare l'ID oggetto nell'unifiedgroup di PowerShell, premere **invio**e quindi copiare il **SID di gruppo di Azure ad** in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="435ae-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <span data-ttu-id="435ae-139">Creare un file XML contenente un SID di gruppo di Azure AD</span><span class="sxs-lookup"><span data-stu-id="435ae-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="435ae-140">Copiare le operazioni seguenti in un editor di testo:</span><span class="sxs-lookup"><span data-stu-id="435ae-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. <span data-ttu-id="435ae-141">Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID di gruppo di Azure ad** e quindi salvare il file come XML; ad esempio, **aad-local-admin.xml**.</span><span class="sxs-lookup"><span data-stu-id="435ae-141">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

## <span data-ttu-id="435ae-142">Creare un profilo di configurazione personalizzato</span><span class="sxs-lookup"><span data-stu-id="435ae-142">Create Custom configuration profile</span></span>

1. <span data-ttu-id="435ae-143">In Endpoint Manager selezionare i profili di configurazione dei **dispositivi**per  >  **Configuration profiles**  >  **creare il profilo**.</span><span class="sxs-lookup"><span data-stu-id="435ae-143">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="435ae-144">In Platform selezionare **Windows 10 e versioni successive.**</span><span class="sxs-lookup"><span data-stu-id="435ae-144">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="435ae-145">In profilo selezionare **personalizzato**e quindi selezionare **Crea.**</span><span class="sxs-lookup"><span data-stu-id="435ae-145">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="435ae-146">Aggiungere un nome e una descrizione e quindi fare clic su **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="435ae-146">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="435ae-147">In **Configuration settings**  >  **Impostazioni configurazione OMA-URI**selezionare **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="435ae-147">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="435ae-148">Nel riquadro Aggiungi riga aggiungere un nome e in     **OMA-URI**aggiungere la stringa seguente:</span><span class="sxs-lookup"><span data-stu-id="435ae-148">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="435ae-149">In tipo di dati selezionare **stringa XML** e Sfoglia per aprire il file XML creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="435ae-149">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![caricare file di configurazione XML di amministrazione locale](images/sh-local-admin-config.png)

7. <span data-ttu-id="435ae-151">Fare clic su **Save**.</span><span class="sxs-lookup"><span data-stu-id="435ae-151">Click **Save**.</span></span>
8. <span data-ttu-id="435ae-152">Fare clic su **Seleziona gruppi per includere** e scegliere il [gruppo di sicurezza creato in precedenza](#create-security-group-for-surface-hub-2s-devices) (**dispositivi Surface Hub**).</span><span class="sxs-lookup"><span data-stu-id="435ae-152">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="435ae-153">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="435ae-153">Click **Next.**</span></span>
9. <span data-ttu-id="435ae-154">In regole di applicabilità aggiungere una regola, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="435ae-154">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="435ae-155">In caso contrario, seleziona **Avanti** e quindi scegli **Crea**.</span><span class="sxs-lookup"><span data-stu-id="435ae-155">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="435ae-156">Per altre informazioni sui profili di configurazione personalizzati con le stringhe OMA-URI, vedere [usare le impostazioni personalizzate per i dispositivi Windows 10 in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span><span class="sxs-lookup"><span data-stu-id="435ae-156">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <span data-ttu-id="435ae-157">Amministratori non globali che gestiscono Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="435ae-157">Non Global admins managing Surface Hub 2S</span></span>

<span data-ttu-id="435ae-158">I membri del gruppo di sicurezza **amministratori locali di Surface Hub** possono ora accedere all'app impostazioni in Surface Hub 2S e gestire le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="435ae-158">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub 2S and manage settings.</span></span>

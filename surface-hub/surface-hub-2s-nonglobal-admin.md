---
title: Configurare account di amministratore non globali in Surface Hub
description: In questo articolo viene descritto come configurare gli account amministratore non globali per gestire Surface Hub e Surface Hub 2S.
keywords: Surface Hub, Surface Hub v1, Surface Hub 2S
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 03/22/2021
ms.localizationpriority: Medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 03359a7d8ea028a8094c064c1fcb82cc9a53fe6a
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576766"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a><span data-ttu-id="6a582-104">Configurare account di amministratore non globali in Surface Hub</span><span class="sxs-lookup"><span data-stu-id="6a582-104">Configure non Global admin accounts on Surface Hub</span></span>

<span data-ttu-id="6a582-105">L'Windows 10 Team 2020 aggiunge il supporto per la configurazione di account amministratore non globali che limitano le autorizzazioni per la gestione dell'app Impostazioni nei dispositivi Surface Hub aggiunti a un dominio di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-105">The Windows 10 Team 2020 Update adds support for configuring non Global admin accounts that limit permissions to management of the Settings app on Surface Hub devices joined to an Azure AD domain.</span></span> <span data-ttu-id="6a582-106">In questo modo è possibile impostare l'ambito delle autorizzazioni di amministratore solo Surface Hub e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-106">This enables you to scope admin permissions for Surface Hub only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> <span data-ttu-id="6a582-107">Prima di iniziare, assicurati che il Surface Hub sia aggiunto ad Azure AD e Intune registrato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="6a582-107">Before you begin, make sure your Surface Hub is joined to Azure AD and Intune auto-enrolled.</span></span> <span data-ttu-id="6a582-108">In caso contrario, sarà necessario reimpostare Surface Hub e completare il programma di installazione della Configurazione guidata, scegliendo l'opzione per partecipare ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-108">If not, you will need to reset Surface Hub and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <a name="summary"></a><span data-ttu-id="6a582-109">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="6a582-109">Summary</span></span> 

<span data-ttu-id="6a582-110">Il processo di creazione di account amministratore non globali prevede i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="6a582-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="6a582-111">In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per la gestione Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="6a582-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub.</span></span>
2. <span data-ttu-id="6a582-112">Ottenere il SID del gruppo di Azure AD tramite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a582-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="6a582-113">Creare un file XML contenente il SID del gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="6a582-114">Crea un gruppo di sicurezza contenente Surface Hub dispositivi che verranno gestiti dal gruppo di sicurezza non amministratori globali.</span><span class="sxs-lookup"><span data-stu-id="6a582-114">Create a Security Group containing the Surface Hub devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="6a582-115">Crea un profilo di configurazione personalizzato per il gruppo di sicurezza che contiene i dispositivi Surface Hub personalizzati.</span><span class="sxs-lookup"><span data-stu-id="6a582-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub devices.</span></span> 


## <a name="create-azure-ad-security-groups"></a><span data-ttu-id="6a582-116">Creare gruppi di sicurezza di Azure AD</span><span class="sxs-lookup"><span data-stu-id="6a582-116">Create Azure AD security groups</span></span>

<span data-ttu-id="6a582-117">Creare innanzitutto un gruppo di sicurezza contenente gli account amministratore.</span><span class="sxs-lookup"><span data-stu-id="6a582-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="6a582-118">Crea quindi un altro gruppo di sicurezza per Surface Hub dispositivi.</span><span class="sxs-lookup"><span data-stu-id="6a582-118">Then create another security group for Surface Hub devices.</span></span>  

### <a name="create-security-group-for-admin-accounts"></a><span data-ttu-id="6a582-119">Creare un gruppo di sicurezza per gli account amministratore</span><span class="sxs-lookup"><span data-stu-id="6a582-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="6a582-120">Accedi a Intune tramite [l'Microsoft Endpoint Manager di amministrazione,](https://go.microsoft.com/fwlink/?linkid=2109431) **seleziona**Gruppi Nuovo gruppo > e in Tipo di gruppo seleziona  >  \*\*\*\* **Sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="6a582-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="6a582-121">Immettere un nome di gruppo, ad esempio Surface Hub **amministratori locali,** quindi selezionare **Crea.**</span><span class="sxs-lookup"><span data-stu-id="6a582-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![Creare un gruppo di sicurezza per gli amministratori hub](images/sh-create-sec-group.png)

3. <span data-ttu-id="6a582-123">Aprire il gruppo, selezionare **Membri**e quindi scegliere Aggiungi membri per immettere gli account amministratore che si desidera designare come amministratori non globali in Surface Hub. \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="6a582-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub.</span></span> <span data-ttu-id="6a582-124">Per altre informazioni sulla creazione di gruppi in Intune, vedi [Aggiungere gruppi per organizzare utenti e dispositivi.](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)</span><span class="sxs-lookup"><span data-stu-id="6a582-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span></span>

### <a name="create-security-group-for-surface-hub-devices"></a><span data-ttu-id="6a582-125">Creare un gruppo di sicurezza per Surface Hub dispositivi</span><span class="sxs-lookup"><span data-stu-id="6a582-125">Create security group for Surface Hub devices</span></span>

1. <span data-ttu-id="6a582-126">Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi Hub. ad esempio, **Surface Hub dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="6a582-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![Creare un gruppo di sicurezza per i dispositivi Hub](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a><span data-ttu-id="6a582-128">Ottenere il SID del gruppo di Azure AD tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="6a582-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="6a582-129">Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6a582-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="6a582-130">Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)</span><span class="sxs-lookup"><span data-stu-id="6a582-130">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="6a582-131">[Installare Azure PowerShell modulo](https://docs.microsoft.com/powershell/azure/install-az-ps).</span><span class="sxs-lookup"><span data-stu-id="6a582-131">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="6a582-132">Accedere al tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="6a582-133">Dopo aver eseguito l'accesso al tenant, eseguire il seguente commandlet.</span><span class="sxs-lookup"><span data-stu-id="6a582-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="6a582-134">Verrà richiesto di digitare l'ID oggetto del gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6a582-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="6a582-135">In Intune, selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="6a582-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![Copia ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. <span data-ttu-id="6a582-137">Eseguire il seguente commandlet per ottenere il SID del gruppo di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="6a582-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="6a582-138">Incollare l'ID oggetto nel commandlet di PowerShell, premere **INVIO**e quindi copiare il **SID** del gruppo di Azure AD in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="6a582-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a><span data-ttu-id="6a582-139">Creare un file XML contenente il SID del gruppo di Azure AD</span><span class="sxs-lookup"><span data-stu-id="6a582-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="6a582-140">Copiare quanto segue in un editor di testo:</span><span class="sxs-lookup"><span data-stu-id="6a582-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > <span data-ttu-id="6a582-141">Non rimuovere il membro Administrator predefinito dal file XML.</span><span class="sxs-lookup"><span data-stu-id="6a582-141">Do not remove the default Administrator member from the XML file.</span></span>

2. <span data-ttu-id="6a582-142">Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID** del gruppo di Azure AD e quindi salvare il file come XML. ad esempio, **aad-local-admin.xml**.</span><span class="sxs-lookup"><span data-stu-id="6a582-142">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

## <a name="create-custom-configuration-profile"></a><span data-ttu-id="6a582-143">Creare un profilo di configurazione personalizzato</span><span class="sxs-lookup"><span data-stu-id="6a582-143">Create Custom configuration profile</span></span>

1. <span data-ttu-id="6a582-144">In Endpoint Manager, selezionare **Profili di**configurazione  >  **dispositivi**Crea  >  **profilo.**</span><span class="sxs-lookup"><span data-stu-id="6a582-144">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="6a582-145">In Piattaforma selezionare **Windows 10 e versioni successive.**</span><span class="sxs-lookup"><span data-stu-id="6a582-145">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="6a582-146">In Profilo selezionare **Personalizzato**e quindi **Crea.**</span><span class="sxs-lookup"><span data-stu-id="6a582-146">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="6a582-147">Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="6a582-147">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="6a582-148">In **Impostazioni di configurazione**uri  >  **OMA Impostazioni**selezionare **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="6a582-148">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="6a582-149">Nel riquadro Aggiungi riga aggiungi un nome e in     **URI OMA**aggiungi la stringa seguente:</span><span class="sxs-lookup"><span data-stu-id="6a582-149">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="6a582-150">In Tipo di dati selezionare **Xml stringa** e cercare per aprire il file XML creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="6a582-150">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![caricare il file xml di configurazione dell'amministratore locale](images/sh-local-admin-config.png)

7. <span data-ttu-id="6a582-152">Fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="6a582-152">Click **Save**.</span></span>
8. <span data-ttu-id="6a582-153">Fai **clic su Seleziona gruppi da includere** e scegli il gruppo di sicurezza creato in [precedenza](#create-security-group-for-surface-hub-devices) (**Surface Hub dispositivi**).</span><span class="sxs-lookup"><span data-stu-id="6a582-153">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="6a582-154">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="6a582-154">Click **Next.**</span></span>
9. <span data-ttu-id="6a582-155">In Regole di applicabilità, aggiungere una regola, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="6a582-155">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="6a582-156">In caso contrario, **selezionare Avanti** e quindi **Crea**.</span><span class="sxs-lookup"><span data-stu-id="6a582-156">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="6a582-157">Per altre informazioni sui profili di configurazione personalizzati che usano stringhe URI OMA, vedi Usare impostazioni personalizzate per Windows 10 [dispositivi in Intune.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)</span><span class="sxs-lookup"><span data-stu-id="6a582-157">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <a name="non-global-admins-managing-surface-hub"></a><span data-ttu-id="6a582-158">Amministratori non globali che gestiscono Surface Hub</span><span class="sxs-lookup"><span data-stu-id="6a582-158">Non Global admins managing Surface Hub</span></span>

<span data-ttu-id="6a582-159">I membri del **Surface Hub Di sicurezza** degli amministratori locali possono ora accedere all'app Impostazioni in Surface Hub e gestire le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="6a582-159">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub and manage settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a582-160">L'accesso predefinito degli amministratori globali all'app Impostazioni viene rimosso (a meno che non siano anche membri di questo nuovo gruppo di sicurezza).</span><span class="sxs-lookup"><span data-stu-id="6a582-160">The default access of global admins to the Settings app is removed (unless they are also members of this new security group).</span></span>

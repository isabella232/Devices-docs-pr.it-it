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
ms.openlocfilehash: 11170f6c202faef7aa3dddcb8aa8c6fa84bea80f
ms.sourcegitcommit: d020d899e9c7e1eb0b85193ecb0a17a85bb39fe6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2021
ms.locfileid: "11643862"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub"></a><span data-ttu-id="e237f-104">Configurare account di amministratore non globali in Surface Hub</span><span class="sxs-lookup"><span data-stu-id="e237f-104">Configure non Global admin accounts on Surface Hub</span></span>

<span data-ttu-id="e237f-105">L'Windows 10 Team 2020 aggiunge il supporto per la configurazione di account amministratore non globali che limitano le autorizzazioni per la gestione dell'app Impostazioni nei dispositivi Surface Hub aggiunti a un dominio di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-105">The Windows 10 Team 2020 Update adds support for configuring non Global admin accounts that limit permissions to management of the Settings app on Surface Hub devices joined to an Azure AD domain.</span></span> <span data-ttu-id="e237f-106">In questo modo è possibile impostare l'ambito delle autorizzazioni di amministratore solo Surface Hub e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-106">This enables you to scope admin permissions for Surface Hub only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> <span data-ttu-id="e237f-107">Prima di iniziare, assicurati che il Surface Hub sia aggiunto ad Azure AD e Intune registrato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e237f-107">Before you begin, make sure your Surface Hub is joined to Azure AD and Intune auto-enrolled.</span></span> <span data-ttu-id="e237f-108">In caso contrario, sarà necessario reimpostare Surface Hub e completare il programma di installazione della Configurazione guidata, scegliendo l'opzione per partecipare ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-108">If not, you will need to reset Surface Hub and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <a name="summary"></a><span data-ttu-id="e237f-109">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="e237f-109">Summary</span></span> 

<span data-ttu-id="e237f-110">Il processo di creazione di account amministratore non globali prevede i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="e237f-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="e237f-111">In Microsoft Intune creare un gruppo di sicurezza contenente gli amministratori designati per la gestione Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="e237f-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub.</span></span>
2. <span data-ttu-id="e237f-112">Ottenere il SID del gruppo di Azure AD tramite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e237f-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="e237f-113">Creare un file XML contenente il SID del gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="e237f-114">Crea un gruppo di sicurezza contenente Surface Hub dispositivi che verranno gestiti dal gruppo di sicurezza non amministratori globali.</span><span class="sxs-lookup"><span data-stu-id="e237f-114">Create a Security Group containing the Surface Hub devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="e237f-115">Crea un profilo di configurazione personalizzato per il gruppo di sicurezza che contiene i dispositivi Surface Hub personalizzati.</span><span class="sxs-lookup"><span data-stu-id="e237f-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub devices.</span></span> 


## <a name="create-azure-ad-security-groups"></a><span data-ttu-id="e237f-116">Creare gruppi di sicurezza di Azure AD</span><span class="sxs-lookup"><span data-stu-id="e237f-116">Create Azure AD security groups</span></span>

<span data-ttu-id="e237f-117">Creare innanzitutto un gruppo di sicurezza contenente gli account amministratore.</span><span class="sxs-lookup"><span data-stu-id="e237f-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="e237f-118">Crea quindi un altro gruppo di sicurezza per Surface Hub dispositivi.</span><span class="sxs-lookup"><span data-stu-id="e237f-118">Then create another security group for Surface Hub devices.</span></span>  

### <a name="create-security-group-for-admin-accounts"></a><span data-ttu-id="e237f-119">Creare un gruppo di sicurezza per gli account amministratore</span><span class="sxs-lookup"><span data-stu-id="e237f-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="e237f-120">Accedi a Intune tramite [l'Microsoft Endpoint Manager di amministrazione,](https://go.microsoft.com/fwlink/?linkid=2109431) **seleziona**Gruppi Nuovo gruppo > e in Tipo di gruppo seleziona  >  \*\*\*\* **Sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="e237f-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="e237f-121">Immettere un nome di gruppo, ad esempio Surface Hub **amministratori locali,** quindi selezionare **Crea.**</span><span class="sxs-lookup"><span data-stu-id="e237f-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![Creare un gruppo di sicurezza per gli amministratori hub](images/sh-create-sec-group.png)

3. <span data-ttu-id="e237f-123">Aprire il gruppo, selezionare **Membri**e quindi scegliere Aggiungi membri per immettere gli account amministratore che si desidera designare come amministratori non globali in Surface Hub. \*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e237f-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub.</span></span> <span data-ttu-id="e237f-124">Per altre informazioni sulla creazione di gruppi in Intune, vedi [Aggiungere gruppi per organizzare utenti e dispositivi.](/mem/intune/fundamentals/groups-add)</span><span class="sxs-lookup"><span data-stu-id="e237f-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](/mem/intune/fundamentals/groups-add).</span></span>

### <a name="create-security-group-for-surface-hub-devices"></a><span data-ttu-id="e237f-125">Creare un gruppo di sicurezza per Surface Hub dispositivi</span><span class="sxs-lookup"><span data-stu-id="e237f-125">Create security group for Surface Hub devices</span></span>

1. <span data-ttu-id="e237f-126">Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi Hub. ad esempio, **Surface Hub dispositivi**.</span><span class="sxs-lookup"><span data-stu-id="e237f-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![Creare un gruppo di sicurezza per i dispositivi Hub](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a><span data-ttu-id="e237f-128">Ottenere il SID del gruppo di Azure AD tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="e237f-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="e237f-129">Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e237f-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="e237f-130">Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](/powershell/module/microsoft.powershell.core/about/about_execution_policies?)</span><span class="sxs-lookup"><span data-stu-id="e237f-130">To learn more, refer to [About Execution Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="e237f-131">[Installare Azure PowerShell modulo](/powershell/azure/install-az-ps).</span><span class="sxs-lookup"><span data-stu-id="e237f-131">[Install Azure PowerShell module](/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="e237f-132">Accedere al tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="e237f-133">Dopo aver eseguito l'accesso al tenant, eseguire il seguente commandlet.</span><span class="sxs-lookup"><span data-stu-id="e237f-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="e237f-134">Verrà richiesto di digitare l'ID oggetto del gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="e237f-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="e237f-135">In Intune, selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="e237f-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![Copia ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. <span data-ttu-id="e237f-137">Eseguire il seguente commandlet per ottenere il SID del gruppo di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="e237f-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="e237f-138">Incollare l'ID oggetto nel commandlet di PowerShell, premere **INVIO**e quindi copiare il **SID** del gruppo di Azure AD in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="e237f-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a><span data-ttu-id="e237f-139">Creare un file XML contenente il SID del gruppo di Azure AD</span><span class="sxs-lookup"><span data-stu-id="e237f-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="e237f-140">Copiare quanto segue in un editor di testo:</span><span class="sxs-lookup"><span data-stu-id="e237f-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "S-1-5-32-544">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```
      > [!IMPORTANT]
      > <span data-ttu-id="e237f-141">Potrebbe essere necessario utilizzare il nome [localizzato per l'account Administrator.](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx)</span><span class="sxs-lookup"><span data-stu-id="e237f-141">You may need to use the [localized name for the Administrator account](https://social.technet.microsoft.com/wiki/contents/articles/13813.localized-names-for-administrator-account-in-windows.aspx).</span></span> <span data-ttu-id="e237f-142">Non rimuovere il membro Administrator predefinito dal file XML.</span><span class="sxs-lookup"><span data-stu-id="e237f-142">Do not remove the default Administrator member from the XML file.</span></span>

2. <span data-ttu-id="e237f-143">Sostituire il SID segnaposto (a partire da S-1-12-1) con il **SID** del gruppo di Azure AD e quindi salvare il file come XML. ad esempio, **aad-local-admin.xml**.</span><span class="sxs-lookup"><span data-stu-id="e237f-143">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

      > [!NOTE]
      > <span data-ttu-id="e237f-144">Anche se i gruppi devono essere specificati tramite il PROPRIO SID, se si desidera aggiungere direttamente gli utenti di Azure, è possibile aggiungerli specificando il nome dell'entità utente (UPN) in questo formato:</span><span class="sxs-lookup"><span data-stu-id="e237f-144">While groups should be specified via their SID, if you would like to add Azure users directly, they can be added by specifying their User Principal Name (UPN) in this format:</span></span> `<member name = "AzureAD\user@contoso.com" />`

## <a name="create-custom-configuration-profile"></a><span data-ttu-id="e237f-145">Creare un profilo di configurazione personalizzato</span><span class="sxs-lookup"><span data-stu-id="e237f-145">Create Custom configuration profile</span></span>

1. <span data-ttu-id="e237f-146">In Endpoint Manager, selezionare **Profili di**configurazione  >  **dispositivi**Crea  >  **profilo.**</span><span class="sxs-lookup"><span data-stu-id="e237f-146">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="e237f-147">In Piattaforma selezionare **Windows 10 e versioni successive.**</span><span class="sxs-lookup"><span data-stu-id="e237f-147">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="e237f-148">In Profilo selezionare **Personalizzato**e quindi **Crea.**</span><span class="sxs-lookup"><span data-stu-id="e237f-148">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="e237f-149">Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="e237f-149">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="e237f-150">In **Impostazioni di configurazione**uri  >  **OMA Impostazioni**selezionare **Aggiungi**.</span><span class="sxs-lookup"><span data-stu-id="e237f-150">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="e237f-151">Nel riquadro Aggiungi riga aggiungi un nome e in     **URI OMA**aggiungi la stringa seguente:</span><span class="sxs-lookup"><span data-stu-id="e237f-151">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="e237f-152">In Tipo di dati selezionare **Xml stringa** e cercare per aprire il file XML creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="e237f-152">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![caricare il file xml di configurazione dell'amministratore locale](images/sh-local-admin-config.png)

7. <span data-ttu-id="e237f-154">Fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="e237f-154">Click **Save**.</span></span>
8. <span data-ttu-id="e237f-155">Fai **clic su Seleziona gruppi da includere** e scegli il gruppo di sicurezza creato in [precedenza](#create-security-group-for-surface-hub-devices) (**Surface Hub dispositivi**).</span><span class="sxs-lookup"><span data-stu-id="e237f-155">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="e237f-156">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="e237f-156">Click **Next.**</span></span>
9. <span data-ttu-id="e237f-157">In Regole di applicabilità, aggiungere una regola, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="e237f-157">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="e237f-158">In caso contrario, **selezionare Avanti** e quindi **Crea**.</span><span class="sxs-lookup"><span data-stu-id="e237f-158">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="e237f-159">Per altre informazioni sui profili di configurazione personalizzati che usano stringhe URI OMA, vedi Usare impostazioni personalizzate per Windows 10 [dispositivi in Intune.](/mem/intune/configuration/custom-settings-windows-10)</span><span class="sxs-lookup"><span data-stu-id="e237f-159">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <a name="non-global-admins-managing-surface-hub"></a><span data-ttu-id="e237f-160">Amministratori non globali che gestiscono Surface Hub</span><span class="sxs-lookup"><span data-stu-id="e237f-160">Non Global admins managing Surface Hub</span></span>

<span data-ttu-id="e237f-161">I membri del **Surface Hub Di sicurezza** degli amministratori locali possono ora accedere all'app Impostazioni in Surface Hub e gestire le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="e237f-161">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub and manage settings.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e237f-162">L'accesso predefinito degli amministratori globali all'app Impostazioni viene rimosso (a meno che non siano anche membri di questo nuovo gruppo di sicurezza).</span><span class="sxs-lookup"><span data-stu-id="e237f-162">The default access of global admins to the Settings app is removed (unless they are also members of this new security group).</span></span>

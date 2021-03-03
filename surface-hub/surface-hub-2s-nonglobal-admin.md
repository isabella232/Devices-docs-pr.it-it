---
title: Configurare gli account diversi da amministratore globale in Surface Hub 2S
description: Questo articolo descrive come configurare gli account di amministratore non globale per gestire Surface Hub 2S.
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
ms.openlocfilehash: e16e4f8bd4b2b253233fa9790987287cf17966c7
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385174"
---
# <a name="configure-non-global-admin-accounts-on-surface-hub-2s"></a><span data-ttu-id="675de-104">Configurare gli account diversi da amministratore globale in Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="675de-104">Configure non Global admin accounts on Surface Hub 2S</span></span>

<span data-ttu-id="675de-105">Quando si aggiunge Surface Hub 2S a un dominio di Azure AD, è possibile configurare account di amministratore non globale che limitano le autorizzazioni alla gestione dell'app Impostazioni in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="675de-105">When you join Surface Hub 2S to an Azure AD domain, you can configure non Global admin accounts that limit permissions to management of the Settings app on Surface Hub 2S.</span></span> <span data-ttu-id="675de-106">In questo modo puoi impostare l'ambito delle autorizzazioni di amministratore solo per Surface Hub 2S e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="675de-106">This enables you to scope admin permissions for Surface Hub 2S only and prevent potentially unwanted admin access across an entire Azure AD domain.</span></span> <span data-ttu-id="675de-107">Prima di iniziare, assicurati che Surface Hub 2S sia aggiunto ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="675de-107">Before you begin, make sure your Surface Hub 2S is joined to Azure AD.</span></span> <span data-ttu-id="675de-108">In caso contrario, dovrai reimpostare Surface Hub 2S e completare il primo programma di installazione della Configurazione guidata, scegliendo l'opzione per partecipare ad Azure AD.</span><span class="sxs-lookup"><span data-stu-id="675de-108">If not, you will need to reset Surface Hub 2S and complete the first-time, out-of-the-box (OOBE) setup program, choosing the option to join Azure AD.</span></span>

## <a name="summary"></a><span data-ttu-id="675de-109">Riepilogo</span><span class="sxs-lookup"><span data-stu-id="675de-109">Summary</span></span> 

<span data-ttu-id="675de-110">Il processo di creazione di account di amministratore non globale prevede i passaggi seguenti:</span><span class="sxs-lookup"><span data-stu-id="675de-110">The process of creating non Global admin accounts involves the following steps:</span></span> 

1. <span data-ttu-id="675de-111">In Microsoft Intune crea un gruppo di sicurezza contenente gli amministratori designati per gestire Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="675de-111">In Microsoft Intune, create a Security group containing the admins designated to manage Surface Hub 2S.</span></span>
2. <span data-ttu-id="675de-112">Ottenere il SID del gruppo di Azure AD tramite PowerShell.</span><span class="sxs-lookup"><span data-stu-id="675de-112">Obtain Azure AD Group SID using PowerShell.</span></span>
3. <span data-ttu-id="675de-113">Creare un file XML contenente il SID del gruppo di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="675de-113">Create XML file containing Azure AD Group SID.</span></span>
4. <span data-ttu-id="675de-114">Crea un gruppo di sicurezza contenente i dispositivi Surface Hub 2S che verranno gestiti dal gruppo di sicurezza degli amministratori non globali.</span><span class="sxs-lookup"><span data-stu-id="675de-114">Create a Security Group containing the Surface Hub 2S devices that will be managed by the non-Global admins Security group.</span></span>
5. <span data-ttu-id="675de-115">Crea un profilo di configurazione personalizzato per il gruppo di sicurezza che contiene i dispositivi Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="675de-115">Create a custom Configuration profile targeting the security group that contains your Surface Hub 2S devices.</span></span> 


## <a name="create-azure-ad-security-groups"></a><span data-ttu-id="675de-116">Creare gruppi di sicurezza di Azure AD</span><span class="sxs-lookup"><span data-stu-id="675de-116">Create Azure AD security groups</span></span>

<span data-ttu-id="675de-117">Creare innanzitutto un gruppo di sicurezza contenente gli account amministratore.</span><span class="sxs-lookup"><span data-stu-id="675de-117">First create a security group containing the admin accounts.</span></span> <span data-ttu-id="675de-118">Crea quindi un altro gruppo di sicurezza per i dispositivi Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="675de-118">Then create another security group for Surface Hub devices.</span></span>  

### <a name="create-security-group-for-admin-accounts"></a><span data-ttu-id="675de-119">Creare un gruppo di sicurezza per gli account amministratore</span><span class="sxs-lookup"><span data-stu-id="675de-119">Create security group for Admin accounts</span></span>

1. <span data-ttu-id="675de-120">Accedi a Intune tramite l'interfaccia \*\*\*\* di amministrazione di [Microsoft Endpoint Manager,](https://go.microsoft.com/fwlink/?linkid=2109431)seleziona Gruppi nuovo gruppo > e in Tipo di gruppo  >  \*\*\*\* seleziona **Sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="675de-120">Sign into Intune via the [Microsoft Endpoint Manager admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New Group** > and under Group type, select **Security.**</span></span> 
2. <span data-ttu-id="675de-121">Immetti un nome di gruppo, ad esempio Amministratori locali di **Surface Hub,** e quindi seleziona **Crea.**</span><span class="sxs-lookup"><span data-stu-id="675de-121">Enter a Group name -- for example, **Surface Hub Local Admins** -- and then select **Create.**</span></span> 

     ![Creare un gruppo di sicurezza per gli amministratori hub](images/sh-create-sec-group.png)

3. <span data-ttu-id="675de-123">Apri il gruppo, **seleziona**Membri \*\*\*\* e quindi scegli Aggiungi membri per immettere gli account amministratore che vuoi designare come amministratori non globali in Surface Hub 2S.</span><span class="sxs-lookup"><span data-stu-id="675de-123">Open the group, select **Members**, and then choose **Add members** to enter the Administrator accounts that you wish to designate as non Global admins on Surface Hub 2S.</span></span> <span data-ttu-id="675de-124">Per altre informazioni sulla creazione di gruppi in Intune, vedere [Aggiungere gruppi per organizzare utenti e dispositivi.](https://docs.microsoft.com/mem/intune/fundamentals/groups-add)</span><span class="sxs-lookup"><span data-stu-id="675de-124">To learn more about creating groups in Intune, see  [Add groups to organize users and devices](https://docs.microsoft.com/mem/intune/fundamentals/groups-add).</span></span>

### <a name="create-security-group-for-surface-hub-2s-devices"></a><span data-ttu-id="675de-125">Creare un gruppo di sicurezza per i dispositivi Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="675de-125">Create security group for Surface Hub 2S devices</span></span>

1. <span data-ttu-id="675de-126">Ripetere la procedura precedente per creare un gruppo di sicurezza separato per i dispositivi Hub. ad esempio, **dispositivi Surface Hub.**</span><span class="sxs-lookup"><span data-stu-id="675de-126">Repeat the previous procedure to create a separate security group for Hub devices; for example, **Surface Hub devices**.</span></span> 

     ![Creare un gruppo di sicurezza per i dispositivi Hub](images/sh-create-sec-group-devices.png) 

## <a name="obtain-azure-ad-group-sid-using-powershell"></a><span data-ttu-id="675de-128">Ottenere il SID del gruppo di Azure AD tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="675de-128">Obtain Azure AD Group SID using PowerShell</span></span>

1. <span data-ttu-id="675de-129">Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="675de-129">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="675de-130">Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)</span><span class="sxs-lookup"><span data-stu-id="675de-130">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="675de-131">[Installare il modulo di Azure PowerShell.](https://docs.microsoft.com/powershell/azure/install-az-ps)</span><span class="sxs-lookup"><span data-stu-id="675de-131">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>
3. <span data-ttu-id="675de-132">Accedere al tenant di Azure AD.</span><span class="sxs-lookup"><span data-stu-id="675de-132">Sign into your Azure AD tenant.</span></span>

    ```powershell
    Connect-AzureAD
    ```

4. <span data-ttu-id="675de-133">Dopo aver eseguito l'accesso al tenant, eseguire il seguente commandlet.</span><span class="sxs-lookup"><span data-stu-id="675de-133">When you're signed into your tenant, run the following commandlet.</span></span> <span data-ttu-id="675de-134">Verrà richiesto di "Digitare l'ID oggetto del gruppo di Azure AD".</span><span class="sxs-lookup"><span data-stu-id="675de-134">It will prompt you to "Please type the Object ID of your Azure AD Group."</span></span>

    ```powershell
    function Convert-ObjectIdToSid
    {    param([String] $ObjectId)   
         $d=[UInt32[]]::new(4);[Buffer]::BlockCopy([Guid]::Parse($ObjectId).ToByteArray(),0,$d,0,16);"S-1-12-1-$d".Replace(' ','-')
         
    }
    ```

5. <span data-ttu-id="675de-135">In Intune, selezionare il gruppo creato in precedenza e copiare l'ID oggetto, come illustrato nella figura seguente.</span><span class="sxs-lookup"><span data-stu-id="675de-135">In Intune, select the group you created earlier and copy the Object id, as shown in the following figure.</span></span> 

     ![Copia l'ID oggetto del gruppo di sicurezza](images/sh-objectid.png)

6. <span data-ttu-id="675de-137">Eseguire il seguente commandlet per ottenere il SID del gruppo di sicurezza:</span><span class="sxs-lookup"><span data-stu-id="675de-137">Run the following commandlet to get the security group's SID:</span></span>

    ```powershell
    $AADGroup = Read-Host "Please type the Object ID of your Azure AD Group"
    $Result = Convert-ObjectIdToSid $AADGroup
    Write-Host "Your Azure Ad Group SID is" -ForegroundColor Yellow $Result
    ```
    
7. <span data-ttu-id="675de-138">Incollare l'ID oggetto nel commandlet di PowerShell, premere **INVIO**e quindi copiare il **SID** del gruppo di Azure AD in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="675de-138">Paste the Object id into the PowerShell commandlet, press **Enter**, and then copy the **Azure AD Group SID** into a text editor.</span></span> 

## <a name="create-xml-file-containing-azure-ad-group-sid"></a><span data-ttu-id="675de-139">Creare un file XML contenente il SID del gruppo di Azure AD</span><span class="sxs-lookup"><span data-stu-id="675de-139">Create XML file containing Azure AD Group SID</span></span>

1. <span data-ttu-id="675de-140">Copiare quanto segue in un editor di testo:</span><span class="sxs-lookup"><span data-stu-id="675de-140">Copy the following into a text editor:</span></span> 

    ```xml
      <groupmembership>   
      <accessgroup desc = "Administrators">        
      <member name = "Administrator" />        
      <member name = "S-1-12-1-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX-XXXXXXXXXX" />  
      </accessgroup>
      </groupmembership>
      ```

2. <span data-ttu-id="675de-141">Sostituisci il SID segnaposto (a partire da S-1-12-1) con il **SID** del gruppo di Azure AD e quindi salva il file come XML; ad esempio, **aad-local-admin.xml**.</span><span class="sxs-lookup"><span data-stu-id="675de-141">Replace the placeholder SID (beginning with S-1-12-1) with your **Azure AD Group SID** and then save the file as XML; for example, **aad-local-admin.xml**.</span></span> 

## <a name="create-custom-configuration-profile"></a><span data-ttu-id="675de-142">Creare un profilo di configurazione personalizzato</span><span class="sxs-lookup"><span data-stu-id="675de-142">Create Custom configuration profile</span></span>

1. <span data-ttu-id="675de-143">In Endpoint Manager seleziona **Profili di**configurazione  >  **dei dispositivi**Crea  >  **profilo.**</span><span class="sxs-lookup"><span data-stu-id="675de-143">In Endpoint Manager, select **Devices** > **Configuration profiles** > **Create profile**.</span></span> 
2. <span data-ttu-id="675de-144">In Piattaforma selezionare **Windows 10 e versioni successive.**</span><span class="sxs-lookup"><span data-stu-id="675de-144">Under Platform select **Windows 10 and later.**</span></span> <span data-ttu-id="675de-145">In Profilo selezionare **Personalizzato**e quindi selezionare **Crea.**</span><span class="sxs-lookup"><span data-stu-id="675de-145">Under Profile, select **Custom**, and then select **Create.**</span></span>
3. <span data-ttu-id="675de-146">Aggiungere un nome e una descrizione e quindi selezionare **Avanti.**</span><span class="sxs-lookup"><span data-stu-id="675de-146">Add a name and description and then select **Next.**</span></span>
4. <span data-ttu-id="675de-147">In **Impostazioni di configurazione**impostazioni URI  >  **OMA**selezionare **Aggiungi.**</span><span class="sxs-lookup"><span data-stu-id="675de-147">Under **Configuration settings** > **OMA-URI Settings**, select **Add**.</span></span>
5. <span data-ttu-id="675de-148">Nel riquadro Aggiungi riga aggiungi un nome e in     **URI OMA**aggiungi la stringa seguente:</span><span class="sxs-lookup"><span data-stu-id="675de-148">In the Add Row pane, add a name and under     **OMA-URI**, add the following  string:</span></span> 

    ```OMA-URI
    ./Device/Vendor/MSFT/Policy/Config/RestrictedGroups/ConfigureGroupMembership
    ```
6. <span data-ttu-id="675de-149">In Tipo di dati selezionare **Xml** stringa e individuare il file XML creato nel passaggio precedente.</span><span class="sxs-lookup"><span data-stu-id="675de-149">Under Data type, select **String XML** and browse to open the XML file you created in the previous step.</span></span> 

     ![caricare il file xml di configurazione dell'amministratore locale](images/sh-local-admin-config.png)

7. <span data-ttu-id="675de-151">Fai clic su **Salva**.</span><span class="sxs-lookup"><span data-stu-id="675de-151">Click **Save**.</span></span>
8. <span data-ttu-id="675de-152">Fai **clic su Seleziona gruppi da includere** e scegli il gruppo di sicurezza creato in [precedenza](#create-security-group-for-surface-hub-2s-devices) (**dispositivi Surface Hub).**</span><span class="sxs-lookup"><span data-stu-id="675de-152">Click **Select groups to include** and choose the [security group you created earlier](#create-security-group-for-surface-hub-2s-devices) (**Surface Hub devices**).</span></span> <span data-ttu-id="675de-153">Fai clic su **Avanti**.</span><span class="sxs-lookup"><span data-stu-id="675de-153">Click **Next.**</span></span>
9. <span data-ttu-id="675de-154">In Regole di applicabilità, aggiungere una regola, se lo si desidera.</span><span class="sxs-lookup"><span data-stu-id="675de-154">Under Applicability rules, add a Rule if desired.</span></span> <span data-ttu-id="675de-155">In caso contrario, **selezionare Avanti** e quindi **Crea.**</span><span class="sxs-lookup"><span data-stu-id="675de-155">Otherwise, select **Next** and then select **Create**.</span></span>

<span data-ttu-id="675de-156">Per altre informazioni sui profili di configurazione personalizzati con stringhe URI OMA, vedi Usare le impostazioni personalizzate per i [dispositivi Windows 10 in Intune.](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10)</span><span class="sxs-lookup"><span data-stu-id="675de-156">To learn more about custom configuration profiles using OMA-URI strings, see [Use custom settings for Windows 10 devices in Intune](https://docs.microsoft.com/mem/intune/configuration/custom-settings-windows-10).</span></span>


## <a name="non-global-admins-managing-surface-hub-2s"></a><span data-ttu-id="675de-157">Amministratori non globali che gestiscono Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="675de-157">Non Global admins managing Surface Hub 2S</span></span>

<span data-ttu-id="675de-158">I membri del gruppo Di sicurezza degli amministratori locali di **Surface Hub** possono ora accedere all'app Impostazioni in Surface Hub 2S e gestire le impostazioni.</span><span class="sxs-lookup"><span data-stu-id="675de-158">Members of the **Surface Hub Local Admins** Security group can now sign in to the Settings app on Surface Hub 2S and manage settings.</span></span>

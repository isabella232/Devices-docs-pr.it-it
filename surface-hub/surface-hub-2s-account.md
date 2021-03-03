---
title: Creare un account dispositivo per Surface Hub 2S
description: Questa pagina descrive la procedura per la creazione dell'account del dispositivo Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/18/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 3afd4115ff4bd22a84f9a5fb86ceb6805c347f8a
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385224"
---
# <a name="create-surface-hub-2s-device-account"></a><span data-ttu-id="90d7b-104">Creare un account dispositivo per Surface Hub 2S</span><span class="sxs-lookup"><span data-stu-id="90d7b-104">Create Surface Hub 2S device account</span></span>

<span data-ttu-id="90d7b-105">La creazione di un account del dispositivo Surface Hub (noto anche come cassetta postale sala) consente a Surface Hub 2S di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni.</span><span class="sxs-lookup"><span data-stu-id="90d7b-105">Creating a Surface Hub device account (also known as a Room mailbox) allows Surface Hub 2S to receive, approve, or decline meeting requests and join meetings.</span></span> <span data-ttu-id="90d7b-106">Configura l'account del dispositivo durante la configurazione guidata.</span><span class="sxs-lookup"><span data-stu-id="90d7b-106">Configure the device account during Out-of-Box Experience (OOBE) setup.</span></span> <span data-ttu-id="90d7b-107">Se necessario, è possibile modificarlo in un secondo momento (senza eseguire l'installazione della Configurazione guidata).</span><span class="sxs-lookup"><span data-stu-id="90d7b-107">If needed, you can change it later (without going through OOBE setup).</span></span>

<span data-ttu-id="90d7b-108">È possibile creare l'account dall'interfaccia di amministrazione di Microsoft 365 in combinazione con Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="90d7b-108">You can create the account from  Microsoft 365 Admin center in combination with Windows PowerShell:</span></span> 

- <span data-ttu-id="90d7b-109">**Creare un account tramite l'interfaccia di amministrazione.**</span><span class="sxs-lookup"><span data-stu-id="90d7b-109">**Create account via Admin center**.</span></span> <span data-ttu-id="90d7b-110">Per soddisfare i requisiti minimi, è possibile configurare tutto il necessario per l'account direttamente dall'interfaccia di amministrazione di [Microsoft 365.](https://admin.microsoft.com/AdminPortal)</span><span class="sxs-lookup"><span data-stu-id="90d7b-110">To meet minimum requirements, you can configure everything you need for the account directly from the [Microsoft 365 admin center](https://admin.microsoft.com/AdminPortal).</span></span> <span data-ttu-id="90d7b-111">Alcune funzionalità come la condivisione di lavagne direttamente dall'app lavagna richiedono l'uso di PowerShell per configurare ActiveSync; Vedere [Abilitare ActiveSync se è necessario usare l'app di posta elettronica](#enable-activesync-if-use-of-email-app-is-required) in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="90d7b-111">Some features like sharing whiteboards directly from the whiteboard app require using PowerShell to configure ActiveSync; see [Enable ActiveSync if use of email app is required](#enable-activesync-if-use-of-email-app-is-required) on this page.</span></span>

- <span data-ttu-id="90d7b-112">**Creare un account tramite PowerShell.**</span><span class="sxs-lookup"><span data-stu-id="90d7b-112">**Create account via PowerShell**.</span></span> <span data-ttu-id="90d7b-113">È possibile utilizzare gli script di PowerShell per facilitare la creazione di più account del dispositivo e configurare rapidamente funzionalità specifiche, tra cui:</span><span class="sxs-lookup"><span data-stu-id="90d7b-113">You can use PowerShell scripts to facilitate creation of multiple device accounts and quickly configure specific features including:</span></span>
    - <span data-ttu-id="90d7b-114">Elaborazione del calendario per ogni account del dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="90d7b-114">Calendar processing for every Surface Hub device account.</span></span>
    - <span data-ttu-id="90d7b-115">Risposte automatiche personalizzate alle richieste di pianificazione.</span><span class="sxs-lookup"><span data-stu-id="90d7b-115">Custom auto replies to scheduling requests.</span></span>
    - <span data-ttu-id="90d7b-116">Se il criterio cassetta postale di ActiveSync predefinito è già stato modificato da un altro utente o da un altro processo, è probabile che sia necessario creare e assegnare un nuovo criterio cassetta postale di ActiveSync.</span><span class="sxs-lookup"><span data-stu-id="90d7b-116">If the default ActiveSync mailbox policy has already been modified by someone else or by another process, you will likely have to create and assign a new ActiveSync mailbox policy.</span></span>

> [!TIP]
> <span data-ttu-id="90d7b-117">Puoi controllare la configurazione dell'account eseguendo lo [script di verifica dell'account](#account-verification-script) seguente.</span><span class="sxs-lookup"><span data-stu-id="90d7b-117">You can check account setup by running the [Account verification script](#account-verification-script) below.</span></span>

> [!NOTE]  
> <span data-ttu-id="90d7b-118">L'account del dispositivo Surface Hub non supporta i provider di identità federati (FIP) di terze parti e deve essere un account Active Directory o Azure Active Directory standard.</span><span class="sxs-lookup"><span data-stu-id="90d7b-118">The Surface Hub device account doesn’t support third-party Federated Identity Providers (FIPs) and must be a standard Active Directory or Azure Active Directory account.</span></span>

## <a name="create-account-via-admin-center"></a><span data-ttu-id="90d7b-119">Creare un account tramite l'interfaccia di amministrazione</span><span class="sxs-lookup"><span data-stu-id="90d7b-119">Create account via admin center</span></span>

1. <span data-ttu-id="90d7b-120">Nell'interfaccia di amministrazione di Microsoft \*\*\*\* 365 passare a Risorse e scegliere **Sale & Attrezzature** e quindi selezionare + **Aggiungi risorsa.**</span><span class="sxs-lookup"><span data-stu-id="90d7b-120">In the Microsoft 365 admin center, go to **Resources** and choose **Rooms & Equipment** and then select **+ Add resource**.</span></span>

2. <span data-ttu-id="90d7b-121">Specifica un nome e un indirizzo e-mail per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="90d7b-121">Provide a name and email address for the device account.</span></span> <span data-ttu-id="90d7b-122">Lasciare invariate le impostazioni rimanenti nello stato predefinito.</span><span class="sxs-lookup"><span data-stu-id="90d7b-122">Leave remaining settings unchanged in the default state.</span></span>

   ![Fornire un nome e un indirizzo di posta elettronica](images/sh2-account2.png)

   ![Lasciare invariate le impostazioni rimanenti nello stato predefinito](images/sh2-account3.png)

3. <span data-ttu-id="90d7b-125">Imposta la password per l'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="90d7b-125">Set the password for the device account.</span></span> <span data-ttu-id="90d7b-126">Per impostare la password, scegliere **Utenti** e quindi **Selezionare Utenti attivi.**</span><span class="sxs-lookup"><span data-stu-id="90d7b-126">To set the password, choose **Users** and then select **Active Users**.</span></span> <span data-ttu-id="90d7b-127">Cercare ora l'utente appena creato per impostare la password.</span><span class="sxs-lookup"><span data-stu-id="90d7b-127">Now search for the newly created user to set the password.</span></span> <span data-ttu-id="90d7b-128">Assicurarsi di non **selezionare l'opzione** Rendi l'utente che modifica la password al **primo accesso.**</span><span class="sxs-lookup"><span data-stu-id="90d7b-128">Ensure that you **do not** select the option **Make this user change their password when they first sign in.**</span></span>

   ![Impostare la password per l'account del dispositivo](images/sh2-account4.png)

4. <span data-ttu-id="90d7b-130">Assegnare la sala con una licenza di Office 365.</span><span class="sxs-lookup"><span data-stu-id="90d7b-130">Assign the room with an Office 365 license.</span></span> <span data-ttu-id="90d7b-131">È consigliabile assegnare la licenza \*\*\*\* sala riunioni di Office 365, che abilita automaticamente l'account per Microsoft Teams e Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="90d7b-131">It’s recommended to assign the Office 365 **Meeting Room** license, which automatically enables the account for Microsoft Teams and Skype for Business.</span></span>

   ![Assegnare la licenza di Office 365](images/sh2-account5.png)


> [!NOTE]  
> <span data-ttu-id="90d7b-133">Se si usa Skype for Business, sarà necessario finalizzare la configurazione tramite PowerShell -- Calendario di Skype for Business: impostare l'elaborazione automatica [del calendario](#set-calendar-auto-processing-skype-for-business-only) per questo account.</span><span class="sxs-lookup"><span data-stu-id="90d7b-133">If using Skype for Business, you will need to finalize setup via PowerShell -- Skype for Business Calendar: Set [Calendar Autoprocessing](#set-calendar-auto-processing-skype-for-business-only) for this account.</span></span> 

## <a name="create-account-via-powershell"></a><span data-ttu-id="90d7b-134">Creare un account tramite PowerShell</span><span class="sxs-lookup"><span data-stu-id="90d7b-134">Create account via PowerShell</span></span>

 <span data-ttu-id="90d7b-135">L'uso di PowerShell per automatizzare rapidamente le attività in Surface Hub non richiede necessariamente l'esperienza di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90d7b-135">Using PowerShell to rapidly automate tasks on Surface Hub does not necessarily require PowerShell expertise.</span></span> <span data-ttu-id="90d7b-136">Verificare di aver completato i prerequisiti di installazione prima di utilizzare gli script appropriati in questa pagina.</span><span class="sxs-lookup"><span data-stu-id="90d7b-136">Ensure you have completed the setup prerequisites before using the appropriate scripts on this page.</span></span>

### <a name="prerequisites-for-using-powershell-to-manage-surface-hub"></a><span data-ttu-id="90d7b-137">Prerequisiti per l'uso di PowerShell per gestire Surface Hub</span><span class="sxs-lookup"><span data-stu-id="90d7b-137">Prerequisites for using PowerShell to manage Surface Hub</span></span> 

1. <span data-ttu-id="90d7b-138">Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="90d7b-138">Launch PowerShell with elevated account privileges (**Run as Administrator**) and ensure your system is configured to run PowerShell scripts.</span></span> <span data-ttu-id="90d7b-139">Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione.](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?)</span><span class="sxs-lookup"><span data-stu-id="90d7b-139">To learn more, refer to [About Execution Policies](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?).</span></span> 
2. <span data-ttu-id="90d7b-140">[Installare il modulo di Azure PowerShell.](https://docs.microsoft.com/powershell/azure/install-az-ps)</span><span class="sxs-lookup"><span data-stu-id="90d7b-140">[Install Azure PowerShell module](https://docs.microsoft.com/powershell/azure/install-az-ps).</span></span>


### <a name="connect-to-exchange-online-powershell"></a><span data-ttu-id="90d7b-141">Connettersi a PowerShell di Exchange Online</span><span class="sxs-lookup"><span data-stu-id="90d7b-141">Connect to Exchange Online PowerShell</span></span>

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### <a name="create-mailbox"></a><span data-ttu-id="90d7b-142">Creare una cassetta postale</span><span class="sxs-lookup"><span data-stu-id="90d7b-142">Create mailbox</span></span>

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### <a name="set-calendar-auto-processing-skype-for-business-only"></a><span data-ttu-id="90d7b-143">Impostare l'elaborazione automatica del calendario (solo Skype for Business)</span><span class="sxs-lookup"><span data-stu-id="90d7b-143">Set Calendar auto-processing (Skype for Business only)</span></span>

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### <a name="enable-activesync-if-use-of-email-app-is-required"></a><span data-ttu-id="90d7b-144">Abilitare ActiveSync se è necessario l'uso dell'app di posta elettronica</span><span class="sxs-lookup"><span data-stu-id="90d7b-144">Enable ActiveSync if use of email app is required</span></span>

 <span data-ttu-id="90d7b-145">Il criterio ActiveSync predefinito funzionerà se non viene modificato.</span><span class="sxs-lookup"><span data-stu-id="90d7b-145">The default ActiveSync Policy will work if unchanged.</span></span> <span data-ttu-id="90d7b-146">In caso contrario, crea un nuovo criterio e assegnalo.</span><span class="sxs-lookup"><span data-stu-id="90d7b-146">Otherwise create a new Policy and assign.</span></span>

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```

### <a name="connect-to-azure-ad"></a><span data-ttu-id="90d7b-147">Connettiti ad Azure AD</span><span class="sxs-lookup"><span data-stu-id="90d7b-147">Connect to Azure AD</span></span>

```powershell
Connect-AzureAD
```

### <a name="assign-a-license"></a><span data-ttu-id="90d7b-148">Assegnare una licenza</span><span class="sxs-lookup"><span data-stu-id="90d7b-148">Assign a license</span></span>

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### <a name="check-for-available-licenses"></a><span data-ttu-id="90d7b-149">Verificare la disponibilità di licenze</span><span class="sxs-lookup"><span data-stu-id="90d7b-149">Check for available licenses</span></span>

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```

## <a name="account-verification-script"></a><span data-ttu-id="90d7b-150">Script di verifica degli account</span><span class="sxs-lookup"><span data-stu-id="90d7b-150">Account verification script</span></span>

<span data-ttu-id="90d7b-151">Dopo aver creato l'account del dispositivo, puoi eseguire lo script di verifica seguente.</span><span class="sxs-lookup"><span data-stu-id="90d7b-151">After creating the device account, you can run the following verification script.</span></span> <span data-ttu-id="90d7b-152">Questo script convalida un account del dispositivo creato in precedenza e genera un rapporto riepilogativo.</span><span class="sxs-lookup"><span data-stu-id="90d7b-152">This script validates a previously-created device account and produces a summary report.</span></span> <span data-ttu-id="90d7b-153">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="90d7b-153">For example:</span></span>

``` syntax
15 tests executed
0 failures
2 warnings
15 passed
```

<span data-ttu-id="90d7b-154">Non verranno visualizzati i dettagli delle impostazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="90d7b-154">Details of specific settings will not be shown.</span></span>

```PowerShell
# SHAccountValidate.ps1

$Error.Clear()
$ErrorActionPreference = "Stop"


# Cleans up set state such as remote powershell sessions
function Cleanup()
{
    if ($sessEx)
    {
        Remove-PSSession $sessEx
    }
    if ($sessSfb)
    {
        Remove-PSSession $sessSfb
    }
}

function PrintError($strMsg)
{
    Write-Host $strMsg -foregroundcolor "red"
}

function PrintSuccess($strMsg)
{
    Write-Host $strMsg -foregroundcolor "green"
}

function PrintAction($strMsg)
{
    Write-Host $strMsg -ForegroundColor Cyan
}


# Cleans up and prints an error message
function CleanupAndFail($strMsg)
{
    if ($strMsg)
    {
        PrintError($strMsg);
    }
    Cleanup
    exit 1
}

# Exits if there is an error set and prints the given message
function ExitIfError($strMsg)
{
    if ($Error)
    {
        CleanupAndFail($strMsg);
    }
}

$strUpn = Read-Host "What is the email address of the account you wish to validate?"
if (!$strUpn.Contains('@'))
{
    CleanupAndFail "$strUpn is not a valid email address"
}
$strExServer = Read-Host "What is your exchange server? (leave blank for online tenants)"
if ($strExServer.Equals(""))
{
    $fExIsOnline = $true
}
else
{
    $fExIsOnline = $false
}
$credEx = Get-Credential -Message "Please provide exchange user credentials"

$strRegistrarPool = Read-Host ("What is the Skype for Business registrar pool for $strUpn" + "? (leave blank for online tenants)")
$fSfbIsOnline = $strRegistrarPool.Equals("")

$fHasOnPrem = $true
if ($fSfbIsOnline -and $fExIsOnline)
{
    do
    {
        $strHasOnPrem = (Read-Host "Do you have an on-premises Active Directory (Y/N) (No if your domain services are hosted entirely online)").ToUpper()
    } while ($strHasOnPrem -ne "Y" -and $strHasOnPrem -ne "N")
    $fHasOnPrem = $strHasOnPrem.Equals("Y")
}

$fHasOnline = $false
if ($fSfbIsOnline -or $fExIsOnline)
{
    $fHasOnline = $true
}

if ($fSfbIsOnline)
{
    try {
        Import-Module SkypeOnlineConnector
    }
    catch
    {
        CleanupAndFail "To verify Skype for Business in online tenants you need the Lync Online Connector module from https://www.microsoft.com/download/details.aspx?id=39366"
    }
}
else
{
    $credSfb = (Get-Credential -Message "Please enter Skype for Business admin credentials")
}

if ($fHasOnline)
{
    $credSfb = $credEx
    try {
        Import-Module MSOnline
    }
    catch
    {
        CleanupAndFail "To verify accounts in online tenants you need the Azure Active Directory module for PowerShell from https://go.microsoft.com/fwlink/p/?linkid=236297"
    }
}

PrintAction "Connecting to Exchange Powershell Session..."
[System.Management.Automation.Runspaces.AuthenticationMechanism] $authType = [System.Management.Automation.Runspaces.AuthenticationMechanism]::Kerberos
if ($fExIsOnline)
{
    $authType = [System.Management.Automation.Runspaces.AuthenticationMechanism]::Basic
}
try
{
    $sessEx = $null
    if ($fExIsOnline)
    {
        $sessEx = New-PSSession -ConfigurationName microsoft.exchange -Credential $credEx -AllowRedirection -Authentication $authType -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -WarningAction SilentlyContinue
    }
    else
    {
        $sessEx = New-PSSession -ConfigurationName microsoft.exchange -Credential $credEx -AllowRedirection -Authentication $authType -ConnectionUri https://$strExServer/powershell -WarningAction SilentlyContinue
    }
}
catch
{
}

if (!$sessEx)
{
    CleanupAndFail "Connecting to Exchange Powershell failed, please validate your server is accessible and credentials are correct"
}

PrintSuccess "Connected to Exchange Powershell Session"

PrintAction "Connecting to Skype for Business Powershell Session..."

if ($fSfbIsOnline)
{
    $sessSfb = New-CsOnlineSession -Credential $credSfb
}
else
{
    $sessSfb = New-PSSession -Credential $credSfb -ConnectionURI "https://$strRegistrarPool/OcsPowershell" -AllowRedirection -WarningAction SilentlyContinue
}

if (!$sessSfb)
{
    CleanupAndFail "Connecting to Skype for Business Powershell failed, please validate your server is accessible and credentials are correct"
}

PrintSuccess "Connected to Skype for Business Powershell"

if ($fHasOnline)
{
    $credMsol = $null
    if ($fExIsOnline)
    {
        $credMsol = $credEx
    }
    elseif ($fSfbIsOnline)
    {
        $credMsol = $credSfb
    }
    else
    {
        CleanupAndFail "Internal error - could not determine MS Online credentials"
    }
    try
    {
        PrintAction "Connecting to Azure Active Directory Services..."
        Connect-MsolService -Credential $credMsol
        PrintSuccess "Connected to Azure Active Directory Services"
    }
    catch
    {
        # This really shouldn't happen unless there is a network error
        CleanupAndFail "Failed to connect to MSOnline"
    }
}


PrintAction "Importing remote sessions into the local session..."
try
{
    $importEx = Import-PSSession $sessEx -AllowClobber -WarningAction SilentlyContinue -DisableNameChecking
    $importSfb = Import-PSSession $sessSfb -AllowClobber -WarningAction SilentlyContinue -DisableNameChecking
}
catch
{
}
if (!$importEx -or !$importSfb)
{
    CleanupAndFail "Import failed"
}
PrintSuccess "Import successful"


$mailbox = $null
try
{
    $mailbox = Get-Mailbox -Identity $strUpn
}
catch
{
}

if (!$mailbox)
{
    CleanupAndFail "Account exists check failed. Unable to find the mailbox for $strUpn - please make sure the Exchange account exists on $strExServer"
}

$exchange = $null
if (!$fExIsOnline)
{
    $exchange = Get-ExchangeServer
    if (!$exchange -or !$exchange.IsE14OrLater)
    {
        CleanupAndFail "A compatible exchange server version was not found. Please use at least exchange 2010."
    }
}


$strAlias = $mailbox.UserPrincipalName
$strDisplayName = $mailbox.DisplayName

$strLinkedAccount = $strLinkedDomain = $strLinkedUser = $strLinkedServer = $null
$credLinkedDomain = $Null
if (!$fExIsOnline -and ![System.String]::IsNullOrEmpty($mailbox.LinkedMasterAccount) -and !$mailbox.LinkedMasterAccount.EndsWith("\SELF"))
{
    $strLinkedAccount = $mailbox.LinkedMasterAccount
    $strLinkedDomain = $strLinkedAccount.substring(0,$strLinkedAccount.IndexOf('\'))
    $strLinkedUser = $strLinkedAccount.substring($strLinkedAccount.IndexOf('\') + 1)
    $strLinkedServer = Read-Host "What is the domain controller for the $strLinkedDomain"
    $credLinkedDomain = (Get-Credential -Message "Please provide credentials for $strLinkedDomain")
}







Write-Host
Write-Host
Write-Host
PrintAction "Performing verification checks on $strDisplayName..."
$Global:iTotalFailures = 0
$global:iTotalWarnings = 0
$Global:iTotalPasses = 0

function Validate()
{
    Param(
        [string]$Test,
        [bool]  $Condition,
        [string]$FailureMsg,
        [switch]$WarningOnly
    )

    Write-Host -NoNewline -ForegroundColor White $Test.PadRight(100,'.')
    if ($Condition)
    {
        Write-Host -ForegroundColor Green "Passed"
        $global:iTotalPasses++
    }
    else
    {
        if ($WarningOnly)
        {
            Write-Host -ForegroundColor Yellow ("Warning: "+$FailureMsg)
            $global:iTotalWarnings++
        }
        else
        {
            Write-Host -ForegroundColor Red ("Failed: "+$FailureMsg)
            $global:iTotalFailures++
        }
    }
}
```

## <a name="learn-more"></a><span data-ttu-id="90d7b-155">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="90d7b-155">Learn more</span></span>

- [<span data-ttu-id="90d7b-156">Creare gli account locali di Surface Hub 2S con PowerShell</span><span class="sxs-lookup"><span data-stu-id="90d7b-156">Create Surface Hub 2S on-premises accounts with PowerShell</span></span>](surface-hub-2s-onprem-powershell.md)
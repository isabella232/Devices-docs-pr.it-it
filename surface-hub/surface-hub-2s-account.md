---
title: Creare un account dispositivo per Surface Hub 2S
description: Questa pagina descrive la procedura per la creazione dell'account di dispositivo Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: Medium
ms.openlocfilehash: 76ac960be2ab30a30b4e29618f350a13a284f52a
ms.sourcegitcommit: 5cfac94c220c8a8d4620c6a7fa75ae2fae089c7f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2021
ms.locfileid: "11312022"
---
# Creare un account dispositivo per Surface Hub 2S

La creazione di un account per dispositivi Surface Hub (nota anche come cassetta postale della sala) consente a Surface Hub 2S di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni. Configurare l'account del dispositivo durante l'installazione della configurazione guidata. Se necessario, è possibile modificarlo in un secondo momento (senza passare alla configurazione di OOBE).

È possibile creare l'account dall'interfaccia di amministrazione di Microsoft 365 in combinazione con Windows PowerShell: 

- **Creare un account tramite**l'interfaccia di amministrazione. Per soddisfare i requisiti minimi, è possibile configurare tutto il necessario per l'account direttamente dall'interfaccia di [amministrazione di Microsoft 365](https://admin.microsoft.com/AdminPortal). Alcune caratteristiche, come la condivisione delle lavagne direttamente dall'app lavagna, richiedono l'uso di PowerShell per configurare ActiveSync. vedere [abilitare ActiveSync se l'uso dell'app di posta elettronica è obbligatorio](#enable-activesync-if-use-of-email-app-is-required) in questa pagina.

- **Creare un account tramite PowerShell**. Puoi usare gli script di PowerShell per semplificare la creazione di più account di dispositivo e configurare rapidamente caratteristiche specifiche, tra cui:
    - Elaborazione del calendario per ogni account di dispositivo hub Surface.
    - Risposte automatiche personalizzate alle richieste di pianificazione.
    - Se il criterio cassetta postale di ActiveSync predefinito è già stato modificato da un altro utente o da un altro processo, è probabile che sia necessario creare e assegnare un nuovo criterio cassetta postale di ActiveSync.

> [!TIP]
> È possibile controllare la configurazione dell'account eseguendo lo [script di verifica dell'account](#account-verification-script) seguente.

> [!NOTE]  
> L'account di dispositivo Surface Hub non supporta i provider di identità federati di terze parti e deve essere un account Active Directory o Azure Active Directory standard.

## Creare un account tramite l'interfaccia di amministrazione

1. Nell'interfaccia di amministrazione di Microsoft 365 accedere a **risorse** e scegliere **sale & attrezzature** e quindi selezionare **+ Aggiungi risorsa**.

2. Specificare un nome e un indirizzo di posta elettronica per l'account del dispositivo. Lascia invariate le impostazioni rimanenti nello stato predefinito.

   ![Specificare un nome e un indirizzo di posta elettronica](images/sh2-account2.png)

   ![Lascia invariate le impostazioni rimanenti nello stato predefinito](images/sh2-account3.png)

3. Impostare la password per l'account del dispositivo. Per impostare la password, scegliere **utenti** e quindi selezionare **utenti attivi**. Ora cerca l'utente appena creato per impostare la password. Assicurati di **non** selezionare l'opzione imposta l' **utente come modificarne la password al primo accesso.**

   ![Impostare la password per l'account del dispositivo](images/sh2-account4.png)

4. Assegnare la sala con una licenza di Office 365. È consigliabile assegnare la licenza per la **sala riunioni** di Office 365, che abilita automaticamente l'account per Microsoft teams e Skype for business.

   ![Assegnare la licenza di Office 365](images/sh2-account5.png)


> [!NOTE]  
> Se si usa Skype for business, è necessario finalizzare la configurazione tramite PowerShell--calendario di Skype for business: impostare l'elaborazione automatica del [Calendario](#set-calendar-auto-processing-skype-for-business-only) per questo account. 

## Creare un account tramite PowerShell

 L'uso di PowerShell per automatizzare rapidamente le attività su Surface Hub non richiede necessariamente competenze di PowerShell. Verificare di aver completato i prerequisiti di configurazione prima di usare gli script appropriati in questa pagina.

### Prerequisiti per l'uso di PowerShell per la gestione di Surface Hub 

1. Avviare PowerShell con privilegi di account elevati (**Esegui come amministratore**) e verificare che il sistema sia configurato per l'esecuzione di script di PowerShell. Per altre informazioni, vedere [informazioni sui criteri di esecuzione](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies?). 
2. [Installare il modulo di PowerShell di Azure](https://docs.microsoft.com/powershell/azure/install-az-ps).


### Connettersi a PowerShell di Exchange Online

```powershell
Install-Module -Name ExchangeOnlineManagement
Import-Module ExchangeOnlineManagement
Connect-ExchangeOnline -UserPrincipalName admin@contoso.com -ShowProgress $true
```

### Creare una cassetta postale

```powershell
New-Mailbox -MicrosoftOnlineServicesID 'SurfaceHub01@contoso.com' -Alias SurfaceHub01 -Name "Surface Hub 01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String 'Pass@word1' -AsPlainText -Force)
```

### Impostare l'elaborazione automatica del calendario (solo Skype for business)

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### Abilitare ActiveSync se è necessaria l'uso dell'app di posta elettronica

 I criteri di ActiveSync predefiniti funzioneranno se invariati. In caso contrario, createStupid un nuovo criterio e assegna.

```powershell
New-MobileDeviceMailboxPolicy -Name:"SurfaceHub" -PasswordEnabled:$false
#Assign Policy to Hub:
Set-CASMailbox -Identity SurfaceHub01@contoso.com -ActiveSyncMailboxPolicy "SurfaceHub"
```

### Connettiti ad Azure AD

```powershell
Connect-AzureAD
```

### Assegnare una licenza

```powershell
Set-AzureADUser -ObjectId 'SurfaceHub01@contoso.com' -UsageLocation US
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense 
$License.SkuId = "c7df2760-2c81-4ef7-b578-5b5392b571df" 
$Licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses 
$Licenses.AddLicenses = $License 
Set-AzureADUserLicense -ObjectId 'SurfaceHub01@contoso.com' -AssignedLicenses $Licenses
```

### Verificare la disponibilità di licenze disponibili

```powershell
Get-AzureADUser -Filter "userPrincipalName eq 'SurfaceHub01@contoso.com'" |fl *
#Meeting Room Standard SKU:
6070a4c8-34c6-4937-8dfb-39bbc6397a60
```

## Script di verifica degli account

Dopo aver creato l'account del dispositivo, è possibile eseguire lo script di verifica seguente. Questo script convalida un account di dispositivo creato in precedenza e produce un report di riepilogo. Ad esempio:

``` syntax
15 tests executed
0 failures
2 warnings
15 passed
```

Non verranno visualizzati i dettagli delle impostazioni specifiche.

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

## Altre informazioni

- [Creare gli account locali di Surface Hub 2S con PowerShell](surface-hub-2s-onprem-powershell.md)
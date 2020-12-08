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
ms.date: 12/07/2020
ms.localizationpriority: Medium
ms.openlocfilehash: e171d7c2db8a0d69594ca8d5f3a54f33ecebc9ae
ms.sourcegitcommit: dc08a2096a1fe955eb67e736e2a4453f75e926be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2020
ms.locfileid: "11196729"
---
# Creare un account dispositivo per Surface Hub 2S

La creazione di un account per dispositivi Surface Hub (nota anche come cassetta postale della sala) consente a Surface Hub 2S di ricevere, approvare o rifiutare le convocazioni di riunione e partecipare alle riunioni usando Microsoft teams o Skype for business. Configurare l'account del dispositivo durante l'installazione della configurazione guidata. Se necessario, è possibile modificarlo in un secondo momento (senza passare alla configurazione di OOBE).

Diversamente dalle cassette postali standard che rimangono disabilitate per impostazione predefinita, è necessario abilitare l'account di dispositivo Surface Hub 2S per accedere a Microsoft teams e Skype for business. Surface Hub 2S si basa su Exchange ActiveSync, che richiede un criterio cassetta postale di ActiveSync nell'account del dispositivo. Applicare il criterio cassetta postale di ActiveSync predefinito incluso in Exchange Online.

Creare l'account usando l'interfaccia di amministrazione di Microsoft 365 o usando PowerShell. È possibile usare PowerShell di Exchange Online per configurare caratteristiche specifiche, tra cui:

- Elaborazione del calendario per ogni account di dispositivo hub Surface.
- Risposte automatiche personalizzate alle richieste di pianificazione.
- Se il criterio cassetta postale di ActiveSync predefinito è già stato modificato da un altro utente o da un altro processo, è probabile che sia necessario creare e assegnare un nuovo criterio cassetta postale di ActiveSync.

> [!NOTE]  
> L'account di dispositivo Surface Hub non supporta i provider di identità federati di terze parti e deve essere un account Active Directory o Azure Active Directory standard.

## Creare un account con l'interfaccia di amministrazione di Microsoft 365

1. Nell'interfaccia di amministrazione di Microsoft 365 accedere a **risorse** e scegliere **sale & attrezzature** e quindi selezionare **+ sala**.

2. Specificare un nome e un indirizzo di posta elettronica per l'account del dispositivo. Lascia invariate le impostazioni rimanenti nello stato predefinito.

   ![Specificare un nome e un indirizzo di posta elettronica](images/sh2-account2.png)

   ![Lascia invariate le impostazioni rimanenti nello stato predefinito](images/sh2-account3.png)

3. Impostare la password per l'account del dispositivo. Per impostare la password, scegliere **utenti** e quindi selezionare **utenti attivi**. Ora cerca l'utente appena creato per impostare la password. Assicurati di **non** selezionare l'opzione imposta l' **utente come modificarne la password al primo accesso.**

   ![Impostare la password per l'account del dispositivo](images/sh2-account4.png)

4. Assegnare la sala con una licenza di Office 365. È consigliabile assegnare la licenza per la **sala riunioni** di Office 365, una nuova opzione che consente automaticamente l'account per Skype for business online e Microsoft teams.

   ![Assegnare la licenza di Office 365](images/sh2-account5.png)

### Finalizzare la configurazione tramite PowerShell

- **Calendario di Microsoft teams e Skype for business:** Impostare l' [**elaborazione automatica del calendario**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) per questo account.

## Creare un account tramite PowerShell

Invece di usare il portale di interfaccia di amministrazione Microsoft, è possibile creare l'account usando PowerShell.

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

### Impostare l'elaborazione automatica del calendario

```powershell
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false -AllowConflicts $false -DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'SurfaceHub01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Microsoft Surface Hub. Please make sure this meeting is a Microsoft Teams meeting!"
```

### Abilitare ActiveSync se è necessaria l'uso dell'app di posta elettronica

 I criteri di ActiveSync predefiniti funzioneranno se unchnaged. In caso contrario, crea un nuovo criterio e assegna.

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
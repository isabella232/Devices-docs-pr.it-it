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
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 6d8c41872481d86316d8985871fe74823e005ed8
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833801"
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

- **Skype for business:** Solo per Skype for business (locale o online), puoi abilitare l'oggetto Skype for business eseguendo **Enable-CsMeetingRoom** per abilitare funzionalità come la richiesta della sala riunioni per l'audio e il blocco per le lobby.

- **Calendario di Microsoft teams e Skype for business:** Impostare l' [**elaborazione automatica del calendario**](https://docs.microsoft.com/surface-hub/surface-hub-2s-account?source=docs#set-calendar-auto-processing) per questo account.

## Creare un account tramite PowerShell

Invece di usare il portale di interfaccia di amministrazione Microsoft, è possibile creare l'account usando PowerShell.

### Connettersi a PowerShell di Exchange Online

```powershell
$365Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell -Credential (Get-Credential) -Authentication Basic –AllowRedirection
$ImportResults = Import-PSSession $365Session
```

### Creare una nuova cassetta postale della sala

```powershell
New-Mailbox -MicrosoftOnlineServicesID account@YourDomain.com -Alias SurfaceHub2S -Name SurfaceHub2S -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString  -String "<Enter Strong Password>" -AsPlainText -Force)
```

### Impostare l'elaborazione automatica del calendario

```powershell
Set-CalendarProcessing -Identity "account@YourDomain.com" -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false -AddAdditionalResponse $true -AdditionalResponse "This room is equipped with a Surface Hub"
```

### Assegnare una licenza

```powershell
Connect-MsolService
Set-Msoluser -UserPrincipalName account@YourDomain.com -UsageLocation IE
Set-MsolUserLicense -UserPrincipalName "account@YourDomain.com" -AddLicenses "contoso:MEETING_ROOM"
```

## Connettersi a Skype for business online con PowerShell

### Installare prerequisiti

- [Visual C++ 2017 ridistribuibile](https://aka.ms/vs/15/release/vc_redist.x64.exe)
- [Modulo di PowerShell per Skype for business online](https://www.microsoft.com/download/confirmation.aspx?id=39366)

```powershell
Import-Module LyncOnlineConnector
$SfBSession = New-CsOnlineSession -Credential (Get-Credential)
Import-PSSession $SfBSession -AllowClobber

# Enable the Skype for Business meeting room
Enable-CsMeetingRoom -Identity account@YourDomain.com -RegistrarPool(Get-CsTenant).Registrarpool -SipAddressType EmailAddress
```

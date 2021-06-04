---
title: Funzionalità di sicurezza UEFI avanzate per Surface Pro 3 (Surface)
description: L'articolo descrive come installare e configurare l'aggiornamento UEFI v3.11.760.0 per abilitare opzioni di sicurezza aggiuntive nei dispositivi Surface Pro 3.
ms.assetid: 90F790C0-E5FC-4482-AD71-60589E3C9C93
ms.reviewer: ''
manager: laurawi
keywords: sicurezza, funzionalità, configurare, hardware, dispositivo, personalizzato, script, aggiornamento
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.openlocfilehash: 6a5c53c3e161bd4c49069a0665896762ce587618
ms.sourcegitcommit: e9190a6fe68b8a7cd9b024aea4be9f885f0de388
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "11163186"
---
# Funzionalità di sicurezza UEFI avanzate per Surface Pro 3


L'articolo descrive come installare e configurare l'aggiornamento UEFI v3.11.760.0 per abilitare opzioni di sicurezza aggiuntive nei dispositivi Surface Pro 3.

Per esercitare un controllo più granulare sulla sicurezza dei dispositivi Surface, l'aggiornamento UEFI v3.11.760.0 offre opzioni di sicurezza aggiuntive che ti permettono di disabilitare dispositivi hardware specifici o di impedire l'avvio da questi dispositivi. Dopo aver installato l'aggiornamento UEFI nel dispositivo, puoi configurarlo manualmente o automaticamente eseguendo uno script.

##  <a name="manually-install-the-uefi-update"></a>Installare manualmente l'aggiornamento UEFI


Prima di poter configurare le funzionalità di sicurezza avanzate del dispositivo Surface, devi installare l'aggiornamento UEFI v3.11.760.0. Questo aggiornamento viene installato automaticamente se ricevi gli aggiornamenti da Windows Update. Per altre informazioni su come configurare Windows per l'aggiornamento automatico con Windows Update, vedi [Come configurare e usare gli aggiornamenti automatici in Windows](https://support.microsoft.com/kb/306525).

Per aggiornare UEFI in Surface Pro 3, puoi scaricare e installare gli aggiornamenti UEFI di Surface inclusi nel pacchetto di driver e firmware per Surface Pro 3. Questi pacchetti di driver e firmware sono disponibili nella [pagina Surface Pro 3](https://www.microsoft.com/download/details.aspx?id=38826) dell'Area download Microsoft. Puoi trovare altre informazioni sui pacchetti di driver e firmware in [Scaricare le versioni più recenti di driver e firmware per dispositivi Surface](https://technet.microsoft.com/itpro/surface/deploy-the-latest-firmware-and-drivers-for-surface-devices). I pacchetti di driver e firmware sono disponibili sia in formato Windows Installer autonomo (MSI) sia in formato archivio (ZIP). Puoi trovare altre informazioni su questi due formati e su come usarli per aggiornare i driver in [Gestire gli aggiornamenti di driver e firmware di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-pro-3-firmware-updates).

##  <a name="manually-configure-additional-security-settings"></a>Configurare manualmente impostazioni di sicurezza aggiuntive


>[!NOTE]
>Per avviare l'installazione del firmware in un dispositivo Surface, inizia con il dispositivo spento, tieni premuto il pulsante di **aumento del volume**, premi e rilascia il pulsante di **accensione**, quindi rilascia il pulsante di **aumento del volume** dopo che il dispositivo inizia l'avvio.

Dopo aver installato l'aggiornamento UEFI v3.11.760.0 in un dispositivo Surface, è disponibile un nuovo menu di UEFI chiamato **Advanced Device Security**. Se fai clic su questo menu, vengono visualizzate le opzioni seguenti:

| Opzione         | Descrizione                                                                                                                                                                          | Impostazioni disponibili (valori predefiniti indicati in grassetto) |
|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| Network Boot   | Abilita o disabilita la capacità del dispositivo Surface di eseguire l'avvio dalla rete (chiamata anche avvio PXE).                                                                            | **Enabled**, Not Bootable                   |
| Side USB       | Abilita o disabilita la porta USB sul lato del dispositivo Surface. La porta USB può inoltre essere abilitata, ma senza permettere l'avvio.                                                | **Enabled**, Not Bootable, Disabled         |
| Docking Port   | Abilita o disabilita le porte sull'alloggiamento di espansione di Surface. Inoltre, è possibile abilitare la porta dell'alloggiamento di espansione bloccando però l'avvio da qualsiasi porta USB o Ethernet sull'alloggiamento di espansione. | **Enabled**, Not Bootable, Disabled         |
| Front Camera   | Abilita o disabilita la fotocamera sul lato anteriore del dispositivo Surface.                                                                                                                   | **Enabled**, Disabled                       |
| Rear Camera    | Abilita o disabilita la fotocamera sul retro del dispositivo Surface.                                                                                                                    | **Enabled**, Disabled                       |
| On Board Audio | Abilita o disabilita l'audio nel dispositivo Surface.                                                                                                                                     | **Enabled**, Disabled                       |
| microSD        | Abilita o disabilita lo slot microSD nel dispositivo Surface.                                                                                                                          | **Enabled**, Disabled                       |
| WiFi           | Abilita o disabilita il ricetrasmettitore Wi-Fi integrato nel dispositivo Surface. Viene disabilitata anche la funzionalità Bluetooth.                                                                              | **Enabled**, Disabled                       |
| Bluetooth      | Abilita o disabilita il ricetrasmettitore Bluetooth integrato nel dispositivo Surface.                                                                                                        | **Enabled**, Disabled                       |

 

##  <a name="automate-additional-security-settings"></a>Automatizzare le impostazioni di sicurezza aggiuntive


In qualità di professionista IT con privilegi amministrativi, puoi automatizzare la configurazione delle impostazioni UEFI sfruttando gli [strumenti firmware per Surface Pro 3 (476 KB)](https://go.microsoft.com/fwlink/p/?LinkID=618038) disponibili nell'Area download Microsoft. Questi strumenti installano un assembly .NET che può essere chiamato da qualsiasi applicazione o script personalizzato.

**Prerequisiti**

-   Gli script di esempio di seguito sfruttano l'estensione citata sopra e di conseguenza presuppongono che lo strumento sia stato installato nel dispositivo gestito.
-   Gli script devono essere eseguiti con privilegi amministrativi.
-   Il comando [**Set-ExecutionPolicy Unrestricted**](https://technet.microsoft.com/library/ee176961.aspx) di Windows PowerShell deve essere chiamato prima di eseguire gli script di esempio se questi sono senza firma digitale.

**Script di esempio**

> [!NOTE]
> La password UEFI usata negli script di esempio di seguito è presentata come testo non crittografato. Consigliamo di salvare gli script in un percorso protetto e di eseguirli in un ambiente controllato.


Mostrare tutte le opzioni di configurazione:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
foreach ($uefiOption in $uefiOptions) 
{ 
    Write-Host "Name:" $uefiOption.Name 
    Write-Host " Description =" $uefiOption.Description 
    Write-Host " Current Value =" $uefiOption.CurrentValue 
    Write-Host " Default Value =" $uefiOption.DefaultValue 
    Write-Host " Proposed Value =" $uefiOption.ProposedValue 
     
    # This gives usage and validation information 
    Write-Host " Allowed Values =" $uefiOption.FriendlyRegEx 
    Write-Host " Regular Expression =" $uefiOption.RegEx 
     
    Write-Host 
}
```

Impostare o modificare la password UEFI:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
$Password = [Microsoft.Surface.FirmwareOption]::Find("Password") 
 
# Set New value to 12345 
$Password.ProposedValue = "12345"
```

Controllare lo stato delle modifiche proposte:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Check update status 
$updateStatus = [Microsoft.Surface.FirmwareOption]::UpdateStatus 
$updateIteration = [Microsoft.Surface.FirmwareOption]::UpdateIteration 
Write-Host "Last Update Status =" $updateStatus 
Write-Host "Last Update Iteration =" $updateIteration 
 
# Get the individual results for the last proposed update 
# If the device has never had an update attempt this will be an empty list 
$details = [Microsoft.Surface.FirmwareOption]::UpdateStatusDetails 
Write-Host $details.Count "Settings were proposed" 
if ($details.Count -gt 0) 
{ 
    Write-Host "Result Details" 
    foreach ($detail in $details.GetEnumerator()) 
    { 
        Write-Host " " $detail.Key "=" $detail.Value 
    } 
}
```

Ripristinare i valori predefiniti di UEFI:

```powershell
# Load the extension 
[System.Reflection.Assembly]::Load("SurfaceUefiManager, Version=1.0.5483.22783, Culture=neutral, PublicKeyToken=20606f4b5276c705")  
 
# Must supply UEFI administrator Password if set 
# If it is not currently set this is ignored 
[Microsoft.Surface.FirmwareOption]::Unlock("1234") 
 
# Get the collection of all configurable settings 
$uefiOptions = [Microsoft.Surface.FirmwareOption]::All() 
 
# Reset all options to the factory default 
foreach ($uefiOption in $uefiOptions) 
{ 
    $uefiOption.ProposedValue = $uefiOption.DefaultValue 
}
```

Interpretazione dei codici di stato

-   00: l'aggiornamento proposto è riuscito
-   02: uno dei valori proposti non è valido
-   03: uno dei valori proposti impostati non è stato riconosciuto
-   0F: la password di sblocco non corrisponde a quella attualmente impostata

 

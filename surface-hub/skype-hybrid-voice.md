---
title: Distribuzione online o ibrida con l'ambiente Skype Hybrid Voice (Surface Hub)
description: In questo argomento viene illustrato come abilitare Skype for Business Cloud PBX con la connettività PSTN locale tramite un pool di Cloud Connector Edition o Skype for Business 2015.
keywords: distribuzione ibrida, Skype Hybrid Voice
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 08349a7d2decb4d4b053cb03fc95808b49d4f2f0
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833842"
---
# Distribuzione online o ibrida con l'ambiente Skype Hybrid Voice (Surface Hub)

In questo argomento viene illustrato come abilitare Skype for Business Cloud PBX con la connettività PSTN (Public Switched Telephone Network) locale tramite un pool di Cloud Connector Edition o Skype for Business 2015. In questa opzione, i pool principali di Skype for Business e i server Exchange sono in cloud e connessi tramite PSTN utilizzando un pool locale che esegue Skype for Business 2015 o Cloud Connector Edition. [Scopri di più sulle diverse opzioni Cloud PBX](https://technet.microsoft.com/library/mt612869.aspx).  

Se hai distribuito Skype for Business Cloud PBX con una delle opzioni Hybrid Voice, segui questa procedura per abilitare l'account sala per Surface Hub. È importante creare prima un normale account utente, assegnare tutte le opzioni Hybrid Voice e i numeri di telefono e quindi convertire l'account in un account sala. Se non segui questo ordine, non potrai assegnare un numero di telefono ibrido.  

>[!WARNING]
>Se crei un account prima della configurazione di Hybrid Voice (eseguendo il comando Enable-CSMeetingRoom), non sarai in grado di configurare i parametri Hybrid Voice necessari. Per configurare i parametri Hybrid Voice per un account configurato in precedenza o riconfigurare un numero di telefono, elimina la licenza E5 o E3 + componente aggiuntivo Cloud PBX, quindi segui questi passaggi, a partire dal passaggio 3.

1. Crea un nuovo account utente per Surface Hub. Questo esempio usa <strong> surfacehub2@adatum.com </strong> . L'account può essere creato in Active Directory locale e sincronizzato con il cloud oppure creato direttamente nel cloud. 

    ![nuovo oggetto - utente](images/new-user-hybrid-voice.png)

2. Seleziona **Nessuna scadenza password**. Questo è importante per un dispositivo Surface Hub.

   ![Nessuna scadenza password](images/new-user-password-hybrid-voice.png)

3. In Office 365, aggiungi la licenza **E5** o **E3 e componente aggiuntivo Cloud PBX** all'account utente creato per la sala. Ciò è necessario per il funzionamento di Hybrid Voice.

   ![Aggiungere licenze dei prodotti](images/product-license-hybrid-voice.png)

4. Attendi circa 15 minuti fino a quando non viene visualizzato l'account utente per la sala in Skype for Business online.

5. Dopo aver creato l'account utente per la sala in Skype for Business online, abilitalo per Hybrid Voice in PowerShell remoto di Skype for Business eseguendo il cmdlet seguente:

   ```
   Set-csuser surfacehub2@adatum.com EnterpriseVoiceEnabled $true -HostedVoiceMail $true -onpremlineuri tel:+15005000102
   ```
    
6. Convalida il flusso di chiamate Hybrid Voice effettuando chiamate di test da Surface Hub.

7. Avvia una sessione remota di PowerShell su un PC e connettiti a Exchange eseguendo i cmdlet seguenti.

   ```
   Set-ExecutionPolicy Unrestricted
   $cred=Get-Credential -Message "Please use your Office 365 admin credentials"
   $sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/ps1-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
   Import-PSSession $sess
   ```
    
8. Dopo aver stabilito una sessione, modifica l'account utente per la sala per abilitarlo come **RoomMailboxAccount** eseguendo i cmdlet seguenti. In questo modo l'account potrà essere autenticato in Surface Hub.

   ```
   Set-Mailbox surfacehub2@adatum.com -Type Room
   Set-Mailbox surfacehub2@adatum.com -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
   ```
    
9. Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

   I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo associati a criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su **False**. Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.
    
   Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs". Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

   ```
   $easPolicy = New-MobileDeviceMailboxPolicy -Name "SurfaceHubs" -PasswordEnabled $false
   ```
    
   Dopo aver creato criteri compatibili, dovrai applicarli all'account del dispositivo. I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse. Esegui i cmdlet seguenti per convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitare l'account e impostare di nuovo la password.
    
   ```
   Set-Mailbox surfacehub2@adatum.com -Type Regular
   Set-CASMailbox surfacehub2@adatum.com -ActiveSyncMailboxPolicy $easPolicy.id
   Set-Mailbox surfacehub2@adatum.com -Type Room
   $credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
   Set-Mailbox surfacehub2@adatum.com -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
   ```
    
10. È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi verificare quali proprietà possono essere impostate in [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md). I cmdlet seguenti forniscono un esempio di impostazione delle proprietà di Exchange.

    ```
    Set-CalendarProcessing surfacehub2@adatum.com -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing surfacehub2@adatum.com -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

11. Abilita la cassetta postale come dispositivo per riunione in Skype for Business online. Eseguire il cmdlet seguente che Abilita l'account come dispositivo di riunione. 

    ```
    Get-CsTenant | select registrarpool
    Enable-CsMeetingRoom surfacehub2@adatum.com -RegistrarPool  'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
    ```
    
    In seguito all'esecuzione di questo cmdlet, agli utenti verrà chiesto se si trovano in una sala riunioni, come illustrato nell'immagine seguente. **Sì** disattiverà il microfono e l'altoparlante.

    ![](images/adjust-room-audio.png)


    
In questo momento l'account sala è completamente configurato, incluso Hybrid Voice. Se utilizzi Skype in locale, puoi configurare attributi aggiuntivi in locale, come descrizione, località e così via. Se crei una sala in Skype Online, questi parametri possono essere impostati online. 

Nell'immagine seguente, puoi vedere come il dispositivo appare agli utenti.


![](images/select-room-hybrid-voice.png)

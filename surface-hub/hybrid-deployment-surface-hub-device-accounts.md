---
title: Distribuzione ibrida (Surface Hub)
description: La distribuzione ibrida richiede un'elaborazione speciale per poter configurare un account del dispositivo per Microsoft Surface Hub.
ms.assetid: 7BFBB7BE-F587-422E-9CE4-C9DDF829E4F1
ms.reviewer: ''
manager: laurawi
keywords: distribuzione ibrida, account del dispositivo per Surface Hub, Exchange ospitato in locale, Exchange ospitato online
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/30/2018
ms.localizationpriority: medium
ms.openlocfilehash: 7444c3f31f7a144200a0b8b89cfa509ef7a7afc4
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833669"
---
# Distribuzione ibrida (Surface Hub)

La distribuzione ibrida richiede un'elaborazione speciale per poter configurare un account del dispositivo per Microsoft Surface Hub. Se stai usando una distribuzione ibrida in cui l'organizzazione offre una combinazione di vari servizi, in parte ospitati in locale e in parte ospitati online, la configurazione dipenderà da dove sono ospitati i diversi servizi. Questo argomento illustra le distribuzioni ibride per [Exchange ospitato in locale](#exchange-on-premises), [Exchange ospitato online](#exchange-online), Skype for Business in locale, Skype for Business online e Skype for Business con configurazione ibrida. Dal momento che esistono molte varianti in questo tipo di distribuzione, non è possibile fornire istruzioni dettagliate per tutte le tipologie. Il processo seguente è applicabile a gran parte delle configurazioni. Se il processo non è adatto per la tua configurazione, ti consigliamo di usare PowerShell (vedi [Appendice: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md)) per ottenere lo stesso risultato, come descritto in questo articolo, e per altre opzioni di distribuzione. Usa quindi lo script di PowerShell fornito per verificare la tua configurazione di Surface Hub. (Vedi [Script di verifica degli account](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts).)

> [!NOTE]
> In un ambiente ibrido di Exchange seguire i passaggi per [Exchange locale](#exchange-on-premises). Per trasferire oggetti di Exchange in Office 365, usare il cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest?view=exchange-ps) .

## Exchange in locale

Usa questa procedura se usi Exchange in locale.

1. Per eseguire questa procedura, userai gli strumenti di amministrazione di AD per aggiungere un indirizzo e-mail per il tuo account di dominio locale. Questo account verrà sincronizzato con Office 365.

- Nello strumento di AD **Utenti e computer di Active Directory** fai clic con il pulsante destro del mouse sulla cartella o sull'unità organizzativa in cui verranno creati i tuoi account di Surface Hub, fai clic su **Nuovo**e quindi su **Utente**.
- Digita il nome visualizzato dal cmdlet precedente nella casella **Nome completo** e l'alias nella casella **Nome accesso utente** . Fai clic su **Avanti**.<p>

![Casella per un nuovo oggetto per creare un nuovo utente in Active Directory.](images/hybriddeployment-01a.png)

- Digita la password per questo account. Dovrai digitarla di nuovo per la verifica. Assicurati che la casella di controllo **Nessuna scadenza password** sia l'unica opzione selezionata.

> **Importante** La selezione dell'opzione **Nessuna scadenza password** è un requisito per Skype for Business in Surface Hub. Le regole del tuo dominio potrebbero vietare l'uso di password senza scadenza. In questo caso, dovrai creare un'eccezione per ogni account del dispositivo di Surface Hub.

![Immagine che mostra la finestra di dialogo della password.](images/hybriddeployment-02a.png)

-   Fai clic su **Fine** per creare l'account.

![Immagine con le opzioni per il nome di account, il nome di accesso e la password per il nuovo utente.](images/hybriddeployment-03a.png)

2. Abilita la cassetta postale remota.

Apri Exchange Management Shell in locale con le autorizzazioni di amministratore ed esegui questo cmdlet.

```PowerShell
Enable-RemoteMailbox 'HUB01@contoso.com' -RemoteRoutingAddress 'HUB01@contoso.com' -Room
```

> [!NOTE]
> Se non disponi di un ambiente Exchange in locale per eseguire questo cmdlet, puoi apportare le stesse modifiche direttamente all'oggetto Active Directory per l'account.
>
> msExchRemoteRecipientType = 33
>
> msExchRecipientDisplayType = -2147481850
>
> msExchRecipientTypeDetails = 8589934592

3. Dopo aver creato l'account, esegui una sincronizzazione della directory. Al termine, accedere alla pagina utenti nell'interfaccia di amministrazione di Microsoft 365 e verificare che l'account creato nei passaggi precedenti sia stato unito a online.

4. Connettiti a Microsoft Exchange Online e imposta alcune proprietà per l'account in Office 365.

Avvia una sessione remota di PowerShell in un PC e connettiti a Microsoft Exchange. Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.

I passaggi successivi verranno eseguiti nel tuo tenant di Office 365.

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri 'https://ps.outlook.com/powershell' -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

5. Crea un nuovo criterio di Exchange ActiveSync o usa un criterio esistente compatibile.

Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False. Se questa proprietà non è impostata correttamente, i servizi di Exchange in Surface Hub (posta, calendario e partecipazione alle riunioni), non saranno abilitati.

Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs". Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

Una volta che hai un criterio compatibile, dovrai applicare il criterio all'account del dispositivo. 

```PowerShell
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
```

6. Imposta le proprietà di Exchange.

Imposta le proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse 'This is a Surface Hub room!'
```

7. Connettiti ad Azure AD.

È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2. In un prompt di PowerShell con privilegi elevati eseguire il comando seguente:

```PowerShell
Install-Module -Name AzureAD
```

Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account. Puoi eseguire questo cmdlet per la connessione.

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. Assegna una licenza di Office 365.

L'account del dispositivo deve avere una licenza valida per Office 365 (O365). In caso contrario, Exchange e Skype for Business non funzioneranno. Se hai la licenza, devi assegnare una località di utilizzo al tuo account del dispositivo, che servirà per determinare gli SKU di licenza disponibili per il tuo account.

Puoi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.

Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

Abilita quindi l'account del dispositivo con [Skype for Business online](#skype-for-business-online), [Skype for Business in locale](#skype-for-business-on-premises) o [Skype for Business con configurazione ibrida](#skype-for-business-hybrid).

### Skype for Business online

Per abilitare Skype for Business online, gli utenti tenant devono avere cassette postali Exchange (è necessaria almeno una cassetta postale di Exchange nel tenant). La tabella seguente illustra quali piani o servizi aggiuntivi sono necessari.

| Scenario di sistema sala Skype | Se si dispone di Office 365 Premium, Microsoft 365 Apps for Enterprise o Skype for business standalone Plan 2, è necessario: | Se disponi di un piano Enterprise, è necessario: | Se si ha Skype for Business Server 2015 (locale o ibrido), è necessario: |
| --- | --- | --- | --- |
| Partecipare a una riunione pianificata | Skype for Business autonomo piano 1 | E1, 3, 4 o 5 | Standard CAL per Skype for Business Server |
| Avviare una riunione ad-hoc | Skype for Business autonomo piano 2 | E 1, 3, 4 o 5 | Standard CAL o Enterprise CAL per Skype for Business |
| Avviare una riunione ad-hoc e una chiamata remota da una riunione a numeri di telefono | Skype for business standalone Plan 2 con servizi di audioconferenza</br></br>**Nota**: la fatturazione per i consumi PSTN è facoltativa | E1 o E3 con servizi di audioconferenza o E5| Standard CAL o Enterprise CAL per Skype for Business Server |
| Assegnare alla sala un numero di telefono ed effettuare o ricevere chiamate dalla sala o partecipare a una conferenza con chiamate in ingresso con un numero di telefono | Skype for business standalone Plan 2 con sistema telefonico e piano per chiamate vocali PSTN | E1 o E3 con sistema telefonico e piano per chiamate vocali PSTN o E5 | Standard CAL o Plus CAL per Skype for Business Server |

La tabella seguente elenca i piani di Office 365 e le opzioni di Skype for Business.

| Piano O365 | Skype for Business | Sistema telefonico | Audioconferenza | Piani di chiamata |
| --- | --- | --- | --- | --- |
| O365 Business Essentials | Inclusa |  |  |  |
| O365 Business Premium | Inclusa |  |  |  |
| E1 | Incluso | Componente aggiuntivo | Componente aggiuntivo | Componente aggiuntivo (richiede il componente aggiuntivo per il sistema telefonico) |
| E3 | Inclusa | Componente aggiuntivo | Componente aggiuntivo | Componente aggiuntivo (richiede il componente aggiuntivo per il sistema telefonico) |
| E5 | Incluso | Incluso | Incluso | Componente aggiuntivo  |

1. Per iniziare, crea una sessione di PowerShell remota da un PC all'ambiente Skype for Business online.

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool 'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:

```PowerShell
Get-CsOnlineUser -Identity ‘HUB01@contoso.com’| fl *registrarpool*
```

3. Assegna una licenza di Skype for Business al tuo account di Surface Hub.

 Dopo aver completato i passaggi precedenti per abilitare l'account di Surface Hub in Skype for Business Online, devi assegnare una licenza al dispositivo Surface Hub. Usando il portale di amministrazione di Office 365, assegna al dispositivo una licenza Skype for business online (piano 2) o Skype for business online (piano 3).

- Accedi come amministratore tenant, apri il portale di amministrazione di O365 e fai clic sull'app Admin.

- Fai clic su **Utenti e gruppi** e quindi su **Aggiungere utenti, reimpostare password e altro**.

- Fai clic sull'account di Surface Hub e quindi fai clic sull'icona a forma di penna per modificare le informazioni dell'account.

- Fai clic su **Licenze**.

- In **assegna licenze**selezionare Skype for business (piano 1) o Skype for business (piano 2), a seconda delle licenze e dei requisiti per la segreteria telefonica aziendale. È necessario usare una licenza di piano 2 Se si vuole usare Enterprise Voice nell'hub Surface.

- Fai clic su **Salva**.

> [!NOTE]
> Puoi anche usare il modulo di Microsoft Azure Active Directory per Windows PowerShell per eseguire i cmdlet necessari per assegnare una di queste licenze, ma questa opzione non è descritta qui.

Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.

### Skype for Business in locale

Per eseguire questo cmdlet, devi connetterti a uno dei front-end Skype. Apri Skype PowerShell ed esegui:

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### Skype for Business con configurazione ibrida

Se l'organizzazione ha impostato la [connettività ibrida tra Skype for Business Server e Skype for Business online](https://technet.microsoft.com/library/jj205403.aspx), le indicazioni per la creazione degli account sono diverse rispetto a una distribuzione di Surface Hub standard.

Surface Hub richiede un account Skype di tipo `meetingroom`, mentre un utente normale userebbe un account Skype di tipo user. Se il server di Skype è configurato in modo ibrido, ovvero possono essere presenti utenti nel server Skype locale nonché utenti ospitati in Office 365, possono verificarsi problemi durante la creazione di un account di Surface Hub.

Nell'ambiente ibrido di Skype for Business Server 2015, tutti gli utenti desiderati in Skype for business online devono prima essere creati nella distribuzione locale, in modo che l'account utente venga creato in servizi di dominio Active Directory. Puoi quindi trasferire l'utente in Skype for business online. Il passaggio di un account utente da locale a online viene eseguito tramite il cmdlet [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) . Per rimuovere un oggetto CsMeetingRoom, usa il cmdlet [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) .

> [!NOTE]
> Per usare il cmdlet Move-CsMeetingRoom, è necessario aver installato [il 6.0.9319.281 di aggiornamento cumulativo di maggio 2017 per Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) o [il 5.0.8308.992 di aggiornamento cumulativo di luglio 2017 per Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).


## Exchange online

Usa questa procedura se usi Exchange online.

1. Crea un account e-mail in Office 365.

Avvia una sessione di PowerShell remota su un PC e connettiti a Exchange. Assicurati di avere impostato le autorizzazioni corrette per l'esecuzione dei cmdlet associati.

```PowerShell
Set-ExecutionPolicy RemoteSigned
$cred=Get-Credential -Message "Please use your Office 365 admin credentials"
$sess= New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/PowerShell-liveid/ -Credential $cred -Authentication Basic -AllowRedirection
Import-PSSession $sess
```

2. Configurare una cassetta postale.

Dopo aver stabilito una sessione, dovrai creare una nuova cassetta postale e abilitarla come un RoomMailboxAccount oppure modificare le impostazioni per una cassetta postale della sala esistente. In questo modo l'account potrà essere autenticato in Surface Hub.

Se devi modificare una cassetta postale delle risorse esistente:

```PowerShell
Set-Mailbox -Identity 'HUB01' -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

Se devi creare una nuova cassetta postale delle risorse:

```PowerShell
New-Mailbox -MicrosoftOnlineServicesID 'HUB01@contoso.com' -Alias HUB01 -Name "Hub-01" -Room -EnableRoomMailboxAccount $true -RoomMailboxPassword (ConvertTo-SecureString -String <password> -AsPlainText -Force)
```

3. Crea il criterio di Exchange ActiveSync.

Dopo aver configurato la cassetta postale, dovrai creare nuovi criteri di Exchange ActiveSync o usare criteri esistenti compatibili.

I dispositivi Surface Hub sono compatibili solo con gli account del dispositivo con criteri ActiveSync in cui la proprietà **PasswordEnabled** è impostata su False. Se non è impostato correttamente, i servizi Exchange nell'hub Surface (posta, calendario e riunioni di partecipazione) non verranno abilitati.

Se non hai ancora creato criteri compatibili, usa il cmdlet seguente, che crea un criterio denominato "Surface Hubs". Dopo la creazione, puoi applicare gli stessi criteri ad altri account del dispositivo.

```PowerShell
$easPolicy = New-MobileDeviceMailboxPolicy -Name “SurfaceHubs” -PasswordEnabled $false
```

Una volta che hai un criterio compatibile, dovrai applicare il criterio all'account del dispositivo. I criteri possono tuttavia essere applicati solo agli account utente e non alle cassette postali delle risorse. Devi convertire la cassetta postale in un tipo di utente, applicare i criteri e quindi riconvertirla in una cassetta postale. Potrebbe essere anche necessario riabilitarla e impostare di nuovo la password.

```PowerShell
Set-Mailbox 'HUB01@contoso.com' -Type Regular
Set-CASMailbox 'HUB01@contoso.com' -ActiveSyncMailboxPolicy $easPolicy.id
Set-Mailbox 'HUB01@contoso.com' -Type Room
$credNewAccount = Get-Credential -Message "Please provide the Surface Hub username and password"
Set-Mailbox 'HUB01@contoso.com' -RoomMailboxPassword $credNewAccount.Password -EnableRoomMailboxAccount $true
```

4. Imposta le proprietà di Exchange.

È necessario impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md) .

```PowerShell
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
Set-CalendarProcessing -Identity 'HUB01@contoso.com' -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
```

5. Aggiungere un indirizzo di posta elettronica per l'account di dominio locale.

Per eseguire questa procedura, userai gli strumenti di amministrazione di AD per aggiungere un indirizzo e-mail per il tuo account di dominio locale.

- Nello strumento di AD **Utenti e computer di Active Directory** fai clic con il pulsante destro del mouse sulla cartella o sull'unità organizzativa in cui verranno creati i tuoi account di Surface Hub, fai clic su **Nuovo**e quindi su **Utente**.
- Digita il nome visualizzato dal cmdlet precedente nella casella **Nome completo** e l'alias nella casella **Nome accesso utente** . Fai clic su **Avanti**.

![Casella per un nuovo oggetto per creare un nuovo utente in Active Directory.](images/hybriddeployment-01a.png)

- Digita la password per questo account. Dovrai digitarla di nuovo per la verifica. Assicurati che la casella di controllo **Nessuna scadenza password** sia l'unica opzione selezionata.

> [!IMPORTANT]
> La selezione di **password non scade mai** è un requisito per Skype for business nell'hub Surface. Le regole del tuo dominio potrebbero vietare l'uso di password senza scadenza. In questo caso, dovrai creare un'eccezione per ogni account del dispositivo di Surface Hub.

![Immagine che mostra la finestra di dialogo della password.](images/hybriddeployment-02a.png)

- Fai clic su **Fine** per creare l'account.

![Immagine con le opzioni per il nome di account, il nome di accesso e la password per il nuovo utente.](images/hybriddeployment-03a.png)

6. Esegui la sincronizzazione della directory.

Dopo aver creato l'account, esegui una sincronizzazione della directory. Al termine dell'operazione, accedi alla pagina degli utenti e verifica che i due account creati nei passaggi precedenti siano stati uniti.

7. Connettiti ad Azure AD.

È innanzitutto necessario installare il modulo Azure AD per PowerShell versione 2. In un prompt di PowerShell con privilegi elevati eseguire il comando seguente:

```PowerShell
Install-Module -Name AzureAD
```

Devi connetterti ad Azure AD per applicare alcune impostazioni dell'account. Puoi eseguire questo cmdlet per la connessione:

```PowerShell
Import-Module AzureAD
Connect-AzureAD -Credential $cred
```

8. Assegna una licenza di Office 365.

L'account del dispositivo deve avere una licenza valida per Office 365 (O365). In caso contrario, Exchange e Skype for Business non funzioneranno. Se hai la licenza, devi assegnare una località di utilizzo al tuo account del dispositivo, che servirà per determinare gli SKU di licenza disponibili per il tuo account.

Puoi quindi usare `Get-AzureADSubscribedSku` per recuperare un elenco di SKU disponibili per il tuo tenant O365.

Dopo aver ottenuto l'elenco di SKU, devi assegnare lo SkuId desiderato alla variabile `$License.SkuId`.

```PowerShell
Set-AzureADUser -ObjectId "HUB01@contoso.com" -UsageLocation "US"

Get-AzureADSubscribedSku | Select Sku*,*Units
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = SkuId You selected 

$AssignedLicenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$AssignedLicenses.AddLicenses = $License
$AssignedLicenses.RemoveLicenses = @()

Set-AzureADUserLicense -ObjectId "HUB01@contoso.com"  -AssignedLicenses $AssignedLicenses
```

Abilita quindi l'account del dispositivo con [Skype for Business online](#skype-for-business-online), [Skype for Business in locale](#skype-for-business-on-premises) o [Skype for Business con configurazione ibrida](#skype-for-business-hybrid).

### Skype for Business online

Per abilitare Skype for Business, l'ambiente deve soddisfare i [prerequisiti di Skype for Business online](#skype-for-business-online).

1. Per iniziare, crea una sessione di PowerShell remota da un PC all'ambiente Skype for Business online.

```PowerShell
Import-Module SkypeOnlineConnector  
$cssess=New-CsOnlineSession -Credential $cred  
Import-PSSession $cssess -AllowClobber
```

2. Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool  
'sippoolbl20a04.infra.lync.com' -SipAddressType UserPrincipalName
```

   Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:

```PowerShell
Get-CsOnlineUser -Identity 'HUB01@contoso.com'| fl *registrarpool*
```

10. Assegnare una licenza di Skype for Business al tuo account di Surface Hub

Dopo aver completato i passaggi precedenti per abilitare l'account di Surface Hub in Skype for Business Online, devi assegnare una licenza al dispositivo Surface Hub. Usando il portale di amministrazione di Office 365, assegna al dispositivo una licenza Skype for business online (piano 2) o Skype for business online (piano 3).

- Accedi come amministratore tenant, apri il portale di amministrazione di O365 e fai clic sull'app Admin.

- Fai clic su **Utenti e gruppi** e quindi su **Aggiungere utenti, reimpostare password e altro**.

- Fai clic sull'account di Surface Hub e quindi fai clic sull'icona a forma di penna per modificare le informazioni dell'account.

- Fai clic su **Licenze**.

- In **Assegnazione licenze**seleziona Skype for Business (Piano 2) o Skype for Business (Piano 3), a seconda delle tue esigenze per licenze e VoIP aziendale. Dovrai usare una licenza per il Piano 3 se voi usare la funzionalità VoIP aziendale nel tuo Surface Hub.

- Fai clic su **Salva**.

> [!NOTE]
> Puoi anche usare il Modulo di Microsoft Azure Active Directory per Windows PowerShell per eseguire i cmdlet necessari per assegnare una di queste licenze, ma questa opzione non è descritta qui.

Per la convalida, dovresti essere in grado di usare qualsiasi client Skype for Business (PC, Android e così via) per accedere a questo account.

### Skype for Business in locale

Per eseguire questo cmdlet, devi connetterti a uno dei front-end Skype. Apri Skype PowerShell ed esegui:

```PowerShell
Enable-CsMeetingRoom -Identity 'HUB01@contoso.com' -RegistrarPool registrarpoolfqdn -SipAddressType UserPrincipalName 
```

### Skype for Business con configurazione ibrida

Se l'organizzazione ha impostato la [connettività ibrida tra Skype for Business Server e Skype for Business online](https://technet.microsoft.com/library/jj205403.aspx), le indicazioni per la creazione degli account sono diverse rispetto a una distribuzione di Surface Hub standard.

Surface Hub richiede un account Skype di tipo *meetingroom*, mentre un utente normale userebbe un account Skype di tipo *user*. Se il server di Skype è configurato in modo ibrido, ovvero possono essere presenti utenti nel server Skype locale nonché utenti ospitati in Office 365, possono verificarsi problemi durante la creazione di un account di Surface Hub.

Nell'ambiente ibrido di Skype for Business Server 2015, tutti gli utenti desiderati in Skype for business online devono prima essere creati nella distribuzione locale, in modo che l'account utente venga creato in servizi di dominio Active Directory. Puoi quindi trasferire l'utente in Skype for business online. Il passaggio di un account utente da locale a online viene eseguito tramite il cmdlet [Move-CsUser](https://technet.microsoft.com/library/gg398528.aspx) . Per rimuovere un oggetto CsMeetingRoom, usa il cmdlet [Move-CsMeetingRoom](https://technet.microsoft.com/library/jj204889.aspx?f=255&mspperror=-2147217396) .

> [!NOTE]
> Per usare il cmdlet Move-CsMeetingRoom, è necessario aver installato [il 6.0.9319.281 di aggiornamento cumulativo di maggio 2017 per Skype for Business Server 2015](https://support.microsoft.com/help/4020991/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p) o [il 5.0.8308.992 di aggiornamento cumulativo di luglio 2017 per Lync Server 2013](https://support.microsoft.com/help/4034279/enables-the-move-csmeetingroom-cmdlet-to-move-a-meeting-room-from-on-p).

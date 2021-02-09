---
title: Creare un account di dispositivo usando l'interfaccia utente (Surface Hub V1)
description: Se vuoi usare un&#39;interfaccia GUI, puoi creare un account per Surface Hub con l&#39;interfaccia utente di Office 365 o l&#39;interfaccia di amministrazione di Exchange.
ms.assetid: D11BCDC4-DABA-4B9A-9ECB-58E02CC8218C
ms.reviewer: ''
manager: laurawi
keywords: creare un account di dispositivo, un'interfaccia utente di Office 365, un centro di amministrazione di Exchange, un centro di amministrazione di Microsoft 365, Skype for business, un criterio cassetta postale
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 05/04/2018
ms.localizationpriority: medium
ms.openlocfilehash: dd19e2fd2417acd29e71c7555e94ee849fbc1bec
ms.sourcegitcommit: 32b6c25698479fa289f642c5b5761ff3be15b686
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "11318010"
---
# Creare un account di dispositivo usando l'interfaccia utente (Surface Hub V1)

 > [!NOTE]
 >Questa pagina include informazioni sull'hub della superficie originale (V1). Per Surface Hub 2S, Vedi [creare l'account del dispositivo Surface Hub 2S](surface-hub-2s-account.md).

Se preferisci usare un'interfaccia utente grafica, puoi creare un account del dispositivo per Microsoft Surface Hub con l'[interfaccia utente di Office 365](#create-device-acct-o365) o l'[interfaccia di amministrazione di Exchange](#create-device-acct-eac).

## <a href="" id="create-device-acct-o365"></a>Creare un account del dispositivo con Office 365


1.  [Creare l'account nell'interfaccia di amministrazione di Microsoft 365](#create-device-acct-o365-admin-ctr).
2.  [Creare un criterio cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Microsoft Exchange](#create-device-acct-o365-mbx-policy).
3.  [Usare PowerShell per completare la creazione dell'account del dispositivo](#create-device-acct-o365-complete-acct)
4.  [Usare PowerShell per configurare le proprietà di Exchange dell'account](#create-device-acct-o365-configure-exch-prop).
5.  [Abilitare l'account con Skype for Business](#create-device-acct-o365-skype-for-business).

### <a href="" id="create-device-acct-o365-admin-ctr"></a>Creare l'account nell'interfaccia di amministrazione

1.  Accedere a Office 365 visitando [https://portal.office.com](https://portal.office.com) .

2.  Specifica le credenziali di amministratore per il tuo tenant di Office 365. In questo modo è possibile usare l'interfaccia di amministrazione di Microsoft 365.

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Microsoft 365.](images/setupdeviceaccto365-02.png)

3. Nell'interfaccia di amministrazione passare a **risorse** nel riquadro sinistro e quindi fare clic su **sale & attrezzature**.

    > [!div class="mx-imgBorder"]
    > ![Opzione camere & attrezzature nell'interfaccia di amministrazione](images/room-equipment.png)

4. Fai clic su **Aggiungi** per creare un nuovo account Sala. Immetti un indirizzo di posta elettronica e un nome visualizzato per l'account, quindi fai clic su **Aggiungi**.

    > [!div class="mx-imgBorder"]
    > ![Creare una finestra per un nuovo account sala](images/room-add.png)

5. Seleziona l'account Sala appena creato nell'elenco Utenti attivi. Nel pannello di destra sono elencate le proprietà dell'account e diverse azioni facoltative. Fai clic su **Reimposta password** per modificare la password e deseleziona **Chiedere all'utente di cambiare la password al primo accesso** in quanto non è possibile cambiare la password dal flusso di accesso di Surface Hub.

6. Nella sezione **Licenza assegnata** fai clic su **Modifica** e quindi fai clic sulla freccia in giù accanto alla licenza appropriata per visualizzare i dettagli. Seleziona una posizione utente e, nell'elenco delle licenze, attiva **Skype for Business Online (Piano 2)** e quindi fai clic su **Salva**. La licenza può variare a seconda dell'organizzazione, ad esempio potresti avere Piano 2 o Piano 3.

### <a href="" id="create-device-acct-o365-mbx-policy"></a>Creare criteri cassetta postale per dispositivi mobili (ActiveSync) dall'interfaccia di amministrazione di Exchange

1.  Nel riquadro sinistro dell'interfaccia di amministrazione fare clic su **amministratore**e quindi su **Exchange**.

    > [!div class="mx-imgBorder"]
    > ![interfaccia di amministrazione che Mostra gli utenti attivi di Exchange.](images/setupdeviceaccto365-08.png)

2.  Verrà aperta un'altra scheda nel browser per permetterti di accedere all'interfaccia di amministrazione di Exchange, in cui puoi creare e configurare l'impostazione della cassetta postale per Surface Hub.

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-09.png)

3.  Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e quindi fai clic su **Criteri della cassetta postale dei dispositivi mobili**. Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account. In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.

    > [!div class="mx-imgBorder"]
    > ![Interfaccia di amministrazione di Exchange - creazione di criteri cassetta postale per dispositivi mobili.](images/setupdeviceaccto365-10.png)

4.  Per creare un nuovo criterio cassetta postale per dispositivi mobili di Surface Hub, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio. Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*. Verifica che il criterio non richieda una password per i dispositivi assegnati, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.

    ![Immagine che mostra il nuovo criterio per dispositivi mobili](images/setupdeviceaccto365-11.png)

5.  Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'**interfaccia di amministrazione di Exchange** per visualizzare il nuovo criterio nell'elenco.

    > [!div class="mx-imgBorder"]
    > ![Immagine con il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceaccto365-12.png)



### <a href="" id="create-device-acct-o365-complete-acct"></a>Usare Windows PowerShell per completare la creazione dell'account del dispositivo

A partire da questo momento, dovrai completare il processo di creazione dell'account usando PowerShell per definire alcune configurazioni.

Per eseguire i cmdlet usati da questi script di PowerShell, devi installare i seguenti componenti per la console PowerShell di amministrazione:

-   [Microsoft Online Services Sign-In Assistant per professionisti IT-RTW](https://www.microsoft.com/download/details.aspx?id=41950)
-   [Modulo di Microsoft Azure Active Directory per Windows PowerShell](https://www.microsoft.com/web/handlers/webpi.ashx/getinstaller/WindowsAzurePowershellGet.3f.3f.3fnew.appids)
-   [Modulo di Windows PowerShell per Skype for Business Online](https://www.microsoft.com/download/details.aspx?id=39366)

Installare il modulo seguente in PowerShell.

```powershell
install-module AzureAD
Install-module MsOnline
```

### Connessione ai servizi online

1.  Esegui Windows PowerShell come amministratore.

    > [!div class="mx-imgBorder"]
    > ![Immagine che mostra come avviare Windows PowerShell ed eseguirlo come amministratore.](images/setupdeviceaccto365-17.png)

2.  Crea un oggetto credenziali, crea una nuova sessione che si connette a Skype for Business Online e specifica l'account amministratore tenant globale, quindi fai clic su **OK**.

    ![Immagine per la richiesta di credenziali di Windows PowerShell.](images/setupdeviceaccto365-18.png)

3.  Per connetterti a Microsoft Online Services, esegui:

    ```powershell
    Connect-MsolService -Credential $Cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-19.png)

4.  A questo punto, per connetterti ai servizi Skype for Business Online, esegui:

    ```powershell
    $sfbsession = New-CsOnlineSession -Credential $cred
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-20.png)

5.  Infine, per connetterti ai servizi Exchange Online, esegui:

    ```powershell
    $exchangeSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri "https://outlook.office365.com/powershell-liveid/" -Credential $cred -Authentication "Basic" –AllowRedirection
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-21.png)

6.  Adesso devi importare la sessione di Skype for Business Online e la sessione di Exchange Online che hai appena creato, da cui verranno importati i comandi di Exchange e Skype per consentirti di usarli in locale.

    ```powershell
    Import-PSSession $exchangesession -AllowClobber -WarningAction SilentlyContinue
    Import-PSSession $sfbsession -AllowClobber -WarningAction SilentlyContinue
    ```

    Tieni presente che il completamento di questa operazione può richiedere molto tempo.

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-22.png)

7.  Dopo la connessione ai servizi online devi eseguire altri cmdlet per configurare l'account come account del dispositivo Surface Hub.

### <a href="" id="create-device-acct-o365-configure-exch-prop"></a>Usare PowerShell per configurare le proprietà di Exchange dell'account

Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo. Userai l'indirizzo e-mail dell'account del dispositivo per:

-   Modificare il tipo di cassetta postale da normale a cassetta postale della sala.
-   Impostare la password e abilitare l'account della cassetta postale della sala
-   Modificare varie proprietà di Exchange
-   Impostare la password dell'account utente in modo che non scada mai.

1.  Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    Per archiviare il valore, recuperalo dalla cassetta postale:

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    Stampa il valore:

    ```powershell
    $strEmail
    ```

    Vedrai l'indirizzo e-mail corretto.

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-23.png)

2. Eseguire il cmdlet seguente:

    ```powershell
    Set-CASMailbox $strEmail  -ActiveSyncMailboxPolicy "SurfaceHubDeviceMobilePolicy"
    ```

4.  È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

    ![Immagine che mostra il cmdlet di PowerShell.](images/setupdeviceaccto365-26.png)

5.  Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell. Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).

    ```powershell
    Set-MsolUser -UserPrincipalName $strEmail -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-o365-skype-for-business"></a>Abilitare l'account con Skype for Business

Abilita l'account del dispositivo con Skype for Business.

Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:

-   Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online. Il piano deve supportare funzionalità per conferenze.
-   Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.
-   Gli utenti tenant devono avere cassette postali di Exchange.
-   L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.

1.  Per iniziare, crea una sessione di PowerShell remota da un PC.

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2.  Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:

    ```powershell
    Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
    ```

     Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:

    ```powershell
    Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
    ```

## <a href="" id="create-device-acct-eac"></a>Creare un account del dispositivo tramite l'interfaccia di amministrazione di Exchange

>[!NOTE]
>Questo metodo funziona solo se si esegue la sincronizzazione da un Active Directory locale.

Puoi usare l'interfaccia di amministrazione di Exchange per creare un account del dispositivo:

1.  [Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange](#create-device-acct-exch-admin-ctr).
2.  [Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange](#create-device-acct-exch-mbx-policy).
3.  [Usare PowerShell per configurare l'account](#create-device-acct-exch-powershell-conf).
4.  [Abilitare l'account con Skype for Business](#create-device-acct-exch-skype-for-business).

### <a href="" id="create-device-acct-exch-admin-ctr"></a>Creare un account e una cassetta postale con l'interfaccia di amministrazione di Exchange

1.  Accedi all'interfaccia di amministrazione di Exchange usando le credenziali di amministratore di Exchange.
2.  Dall'interfaccia di amministrazione di Exchange passa a **Destinatari** nel pannello sinistro.

    ![Immagine che mostra le cassette postali nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-01.png)

3.  Nei controlli sopra l'elenco delle cassette postali scegli **+** per creare una nuova cassetta e specifica i nomi in **Nome visualizzato**, **Nome** e **Nome accesso utente** e quindi fai clic su **Salva**.

    ![Immagine che mostra la creazione di una nuova cassetta postale.](images/setupdeviceacctexch-02.png)

### <a href="" id="create-device-acct-exch-mbx-policy"></a>Creare un criterio cassetta postale per dispositivi mobili dall'interfaccia di amministrazione di Exchange

>[!NOTE]
>Se si vuole creare e assegnare un criterio all'account creato e si usa Exchange 2010, cercare le informazioni corrispondenti relative alla creazione e all'assegnazione dei criteri quando si usa EMC (Exchange Management Console).

 

1.  Accedi all'interfaccia di amministrazione di Exchange.

    ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-03.png)

2.  Per creare un criterio cassetta postale per dispositivi mobili, fai clic su **Dispositivi mobili** nel pannello di sinistra e fai clic su **Criteri della cassetta postale dei dispositivi mobili**. Per i dispositivi Surface Hub è necessario un account con criteri cassetta postale per dispositivi mobili che non richiedono una password, quindi se hai già criteri esistenti che soddisfano questo requisito, puoi applicarli all'account. In caso contrario, usa la procedura seguente per creare nuovi criteri da usare esclusivamente per gli account del dispositivo Surface Hub.

    ![Immagine che mostra l'uso dell'interfaccia di amministrazione di Exchange per creare un criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-05.png)

3.  Per creare un nuovo criterio cassetta postale per l'account del dispositivo mobile, fai clic sul pulsante **+** dai controlli sopra l'elenco dei criteri per aggiungere un nuovo criterio. Specifica un nome che ti permetterà di distinguere questo criterio dagli altri account del dispositivo, ad esempio *SurfaceHubDeviceMobilePolicy*. Poiché il criterio non deve essere protetto da password, assicurati che l'opzione **Richiedi una password** resti deselezionata e quindi fai clic su **Salva**.

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-06.png)

4.  Dopo aver creato il nuovo criterio cassetta postale per dispositivi mobili, torna all'interfaccia di amministrazione di Exchange per visualizzare il nuovo criterio nell'elenco.

    ![Immagine che mostra il nuovo criterio cassetta postale per dispositivi mobili nell'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-07.png)

5.  Per applicare il criterio di ActiveSync senza usare PowerShell, puoi procedere come segue:

    -   Nell'interfaccia di amministrazione di Exchange fai clic su **Destinatari** &gt; **Cassette postali** e seleziona una cassetta postale.

        ![Immagine che mostra l'interfaccia di amministrazione di Exchange.](images/setupdeviceacctexch-08.png)

    -   Nel riquadro **Dettagli** scorri fino a **Funzionalità telefoniche e vocali** e fai clic su **Visualizza dettagli** per visualizzare la schermata **Dettagli dispositivo mobile**.

        ![Immagine che mostra i dettagli delle cassette postali.](images/setupdeviceacctexch-09.png)

    -   Vengono visualizzati i criteri cassetta postale per dispositivi mobili attualmente assegnati. Per modificare i criteri cassetta postale per dispositivi mobili, fai clic su **Sfoglia**.

        ![Immagine che mostra il criterio cassetta postale per dispositivi mobili attualmente assegnato.](images/setupdeviceacctexch-10.png)

    -   Scegli i criteri cassetta postale per dispositivi mobili appropriati nell'elenco, fai clic su **OK** e quindi fai clic su **Salva**.

        ![Immagine che mostra l'elenco dei criteri cassetta postale per dispositivi mobili.](images/setupdeviceacctexch-11.png)

### <a href="" id="create-device-acct-exch-powershell-conf"></a>Usare PowerShell per configurare l'account

Ora che sei connesso ai servizi online, puoi completare la configurazione dell'account del dispositivo. Userai l'indirizzo e-mail dell'account del dispositivo per:

-   Modificare il tipo di cassetta postale da normale a cassetta postale della sala.
-   Modificare varie proprietà di Exchange
-   Impostare la password dell'account utente in modo che non scada mai.

1.  Dovrai immettere l'indirizzo e-mail dell'account e creare una variabile con tale valore:

    ```powershell
    $mailbox = (Get-Mailbox <your device account’s alias>)
    ```

    Per archiviare il valore, recuperalo dalla cassetta postale:

    ```powershell
    $strEmail = $mailbox.WindowsEmailAddress
    ```

    Stampa il valore eseguendo:

    ```powershell
    $strEmail
    ```

    Vedrai l'indirizzo e-mail corretto.

2.  È necessario convertire l'account in una cassetta postale della sala, quindi eseguire:

    ```powershell
    Set-Mailbox $strEmail -Type Room
    ```

3.  Affinché l'account del dispositivo possa essere autenticato in un dispositivo Surface Hub, devi abilitare l'account della cassetta postale della sala e impostare una password, in modo che l'account possa essere usato dal dispositivo per ottenere informazioni sulle riunioni tramite ActiveSync e per accedere a Skype for Business.

    ```powershell
    Set-Mailbox $strEmail -RoomMailboxPassword (ConvertTo-SecureString  -String "<your password>" -AsPlainText -Force) -EnableRoomMailboxAccount $true
    ```

4.  È possibile impostare varie proprietà di Exchange nell'account del dispositivo per migliorare l'esperienza per le riunioni. Puoi vedere le proprietà che devono essere impostate nella sezione [Proprietà di Exchange](exchange-properties-for-surface-hub-device-accounts.md).

    ```powershell
    Set-CalendarProcessing -Identity $strEmail -AutomateProcessing AutoAccept -AddOrganizerToSubject $false –AllowConflicts   $false –DeleteComments $false -DeleteSubject $false -RemovePrivateProperty $false
    Set-CalendarProcessing -Identity $strEmail -AddAdditionalResponse $true -AdditionalResponse "This is a Surface Hub room!"
    ```

5.  A questo punto devi impostare alcune proprietà in AD. A tale scopo, ti serve l'alias dell'account (la parte dell'UPN che precede "@").

    ```powershell
    $strAlias = “<your device account’s alias>”
    ```

6.  Per poter eseguire l'autenticazione con un dispositivo Surface Hub, l'utente deve essere abilitato in AD. Esegui:

    ```powershell
    Set-ADUser $strAlias -Enabled $True
    ```

7.  Se decidi di impostare una password senza scadenza, puoi farlo anche con i cmdlet di PowerShell. Per altre informazioni, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).

    ```powershell
    Set-ADUser $strAlias -PasswordNeverExpires $True
    ```

### <a href="" id="create-device-acct-exch-skype-for-business"></a>Abilitare l'account con Skype for Business

Abilita l'account del dispositivo con Skype for Business.

Per abilitare Skype for Business, l'ambiente deve soddisfare i prerequisiti seguenti:

- Per il piano Office 365 è necessario avere il piano standalone 2 o superiore di Skype for business online. Il piano deve supportare funzionalità per conferenze.
- Se hai bisogno di VoIP aziendale (telefonia PSTN) usando i provider di servizi di telefonia per Surface Hub, hai bisogno di Skype for business online piano Standalone 3.
- Gli utenti tenant devono avere cassette postali di Exchange.
- L'account di Surface Hub richiede una licenza standalone piano 2 o Skype for business online di Skype for business online, ma non richiede una licenza di Exchange Online.

1. Per iniziare, crea una sessione di PowerShell remota da un PC.

    ```PowerShell
    Import-Module SkypeOnlineConnector
    $cssess=New-CsOnlineSession -Credential $cred
    Import-PSSession $cssess -AllowClobber
    ```

2. Recuperare il pool di registrazione dell'account Hub Surface.

   Se non sei certo del valore da usare per il parametro `RegistrarPool` nel tuo ambiente, puoi ottenere il valore da un utente Skype for Business esistente con questo cmdlet:

   ```PowerShell
   Get-CsOnlineUser -Identity ‘alice@contoso.microsoft.com’| fl *registrarpool*
   ```

3. Per abilitare l'account di Surface Hub per Skype for Business Server, esegui questo cmdlet:

   ```PowerShell
   Enable-CsMeetingRoom -Identity $strEmail -RegistrarPool "sippoolbl20a04.infra.lync.com" -SipAddressType EmailAddress
   ```
---
title: Risolvere i problemi relativi a Microsoft Surface Hub
description: Risolvi i problemi comuni, inclusi quelli di configurazione, e gli errori di Exchange ActiveSync.
ms.assetid: CF58F74D-8077-48C3-981E-FCFDCA34B34A
ms.reviewer: ''
manager: laurawi
keywords: Risolvere problemi comuni, i problemi di configurazione e gli errori di Exchange ActiveSync
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/16/2018
ms.localizationpriority: medium
ms.openlocfilehash: fe87c56474a05152f991a5b63f6abf0cf05e8b03
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832685"
---
# Risolvere i problemi relativi a Microsoft Surface Hub


Risolvi i problemi comuni, inclusi quelli di configurazione, e gli errori di Exchange ActiveSync.

Lo strumento di [diagnostica hardware di Surface Hub](https://www.microsoft.com/store/p/surface-hub-hardware-diagnostic/9nblggh51f2g?rtc=1&activetab=pivot%3aoverviewtab) include test interattivi che consentono di verificare che la funzionalità essenziale di Hub si comporti come previsto. Oltre ad eseguire test hardware, lo strumento di diagnostica può eseguire test anche sull'account della risorsa per verificare che sia correttamente configurato per il relativo ambiente. Se si verificano problemi, i risultati possono essere salvati e condivisi con il team di supporto di Surface Hub. Per informazioni sull'utilizzo, vedere [Uso dello strumento di diagnostica hardware di Surface Hub per testare un account dispositivo](https://support.microsoft.com/help/4077574/using-the-surface-hub-hardware-diagnostic-tool-to-test-a-device-accoun).

I problemi comuni sono elencati nella tabella seguente, insieme alle cause e alle soluzioni possibili. La sezione [Risoluzione dei problemi di configurazione](#setup-troubleshooting) contiene un elenco dei problemi relativi al dispositivo, insieme a diversi tipi di problemi che possono verificarsi durante l'esperienza di prima esecuzione. La sezione [Errori di Exchange ActiveSync](#exchange-activesync-errors) elenca gli errori comuni che possono verificarsi nel dispositivo durante il tentativo di sincronizzazione con un server Microsoft Exchange ActiveSync.




## Risoluzione dei problemi di configurazione 


In questa sezione sono elencate le cause e le soluzioni possibili per risolvere i problemi che potresti riscontrare durante la configurazione del dispositivo Microsoft Surface Hub.

### Problemi relativi al dispositivo

Soluzioni possibili per i problemi relativi al dispositivo Surface Hub dopo il completamento del programma di prima esecuzione.

<table>
<tr>
<th>Problema</th>
<th>Cause</th>
<th>Soluzioni possibili</th>
</tr>
<tr>
<td rowspan="2">
<p>Mancata ricezione dei messaggi con accettazione o rifiuto automatici.</p>
</td>
<td>
<p>L'account del dispositivo non è configurato per accettare o rifiutare automaticamente i messaggi.</p>
</td>
<td>
<p>Usa il cmdlet <code>Set-CalendarProcessing $upn -AutomateProcessing AutoAccept</code> di PowerShell.</p>
</td>
</tr>
<tr>
<td>
<p>L'account del dispositivo non è configurato per elaborare le convocazioni riunione esterne.</p>
</td>
<td>
<p>Usa il cmdlet <code>Set-CalendarProcessing $upn -ProcessExternalMeetingMessages $true</code> di PowerShell.</p>
</td>
</tr>
<tr>
<td>
<p>Il calendario non viene visualizzato nella schermata iniziale oppure viene visualizzato il messaggio "Gli appuntamenti potrebbero non essere aggiornati (nessun account configurato)".</p>
</td>
<td>
<p>In Surface Hub non è configurato alcun account del dispositivo.</p>
</td>
<td>
<p>Esegui il provisioning di un account del dispositivo tramite Impostazioni.</p>
</td>
</tr>
<tr>
<td>
<p>Il calendario non viene visualizzato nella schermata iniziale oppure viene visualizzato il messaggio "Gli appuntamenti potrebbero non essere aggiornati (provisioning eccessivo)".</p>
</td>
<td>
<p>L'account del dispositivo è configurato in troppi dispositivi.</p>
</td>
<td>
<p>Rimuovi l'account del dispositivo da altri dispositivi in cui è configurato. Questa operazione può essere eseguita tramite il portale di amministrazione di Exchange.</p>
</td>
</tr>
<tr>
<td>
<p>Il calendario non viene visualizzato nella schermata iniziale oppure viene visualizzato il messaggio "Gli appuntamenti potrebbero non essere aggiornati (credenziali non valide)".</p>
</td>
<td>
<p>La password dell'account del dispositivo è scaduta e non è più valida.</p>
</td>
<td>
<p>Aggiorna la password dell'account in Impostazioni. Vedi anche <a href="password-management-for-surface-hub-device-accounts.md">Gestione delle password</a>.</p>
</td>
</tr>
<tr>
<td>
<p>Il calendario non viene visualizzato nella schermata iniziale oppure viene visualizzato il messaggio "Gli appuntamenti potrebbero non essere aggiornati (criteri dell'account)".</p>
</td>
<td>
<p>L'account del dispositivo usa un criterio di ActiveSync non valido.</p>
</td>
<td>
<p>Assicurati che l'account del dispositivo abbia un criterio di ActiveSync in cui <code>PasswordEnabled == False</code>.</p>
</td>
</tr>
<tr>
<td>
<p>Il calendario non viene visualizzato nella schermata iniziale oppure viene visualizzato il messaggio "Gli appuntamenti potrebbero non essere aggiornati".</p>
</td>
<td>
<p>Exchange non è abilitato.</p>
</td>
<td>Abilita l'account del dispositivo per i servizi di Exchange tramite Impostazioni. Devi assicurarti di avere il set di criteri ActiveSync corretto e di aver installato eventuali certificati necessari per il funzionamento dei servizi di Exchange.</td>
</tr>
<tr>
<td>
<p>Non è possibile accedere a Skype for Business.</p>
</td>
<td>
<p>L'account del dispositivo non dispone di una proprietà dell'indirizzo SIP (Session Protocol).</p>
</td>
<td>
<p>L'account non dispone di una proprietà dell'indirizzo SIP e il relativo nome dell'entità utente (UPN) non corrisponde all'indirizzo SIP effettivo. Nell'account deve essere impostato l'indirizzo SIP oppure l'indirizzo SIP deve essere aggiunto tramite l'app Impostazioni.</p>
</td>
</tr>
<tr>
<td>
<p>Non è possibile accedere a Skype for Business.</p>
</td>
<td>
<p>L'account del dispositivo richiede un certificato per l'autenticazione in Skype for Business.</p>
</td>
<td>
<p>Installa il certificato appropriato con pacchetti di provisioning.</p>
</td>
</tr>
</table>
 

### Prima esecuzione

Soluzioni possibili per i problemi relativi al programma di prima esecuzione di Surface Hub.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problema</th>
<th align="left">Cause</th>
<th align="left">Soluzioni possibili</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Non è possibile trovare l'account quando vengono richiesti dominio e nome utente.</p></td>
<td align="left"><p>Il dominio deve corrispondere al nome di dominio completo (FQDN).</p></td>
<td align="left"><p>Il nome di dominio completo deve essere specificato nel campo del dominio.</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-device-acct-page"></a>Pagina dell'account del dispositivo, problemi relativi alle impostazioni per nuovi account

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problema</th>
<th align="left">Cause</th>
<th align="left">Soluzioni possibili</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Non è possibile trovare l'account specificato in Azure AD.</p></td>
<td align="left"><p>Il nome dell'entità utente (UPN) dell'account specificato ha un tenant non raggiungibile in Azure AD.</p></td>
<td align="left"><p>Assicurati di avere una connessione Internet funzionante e che il dispositivo sia in grado di accedere ai Microsoft Online Services. Assicurati che le credenziali dell'account vengono immesse correttamente.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Non è possibile raggiungere la directory specificata.</p></td>
<td align="left"><p>Il dominio dell'account specificato indica un dominio non raggiungibile.</p></td>
<td align="left"><p>Assicurati di avere una connessione di rete funzionante e che il dispositivo sia in grado di accedere al controller di dominio. Assicurati che le credenziali dell'account vengono immesse correttamente. Puoi anche provare a usare il nome di dominio completo.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Non è possibile individuare automaticamente il server Exchange.</p></td>
<td align="left"><p>Il server Exchange non è configurato per l'individuazione automatica.</p></td>
<td align="left"><p>Abilita l'individuazione automatica del server Exchange per l'account del dispositivo oppure immetti manualmente l'indirizzo del server Exchange.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Non è possibile individuare l'indirizzo SIP dopo avere immesso le credenziali dell'account.</p></td>
<td align="left"><p>Non è presente alcuna voce relativa all'indirizzo SIP in Active Directory o Azure AD.</p></td>
<td align="left"><p>Assicurati che l'account sia abilitato per Skype for Business e che abbia un indirizzo SIP. In caso contrario, puoi immettere l'indirizzo SIP manualmente nella casella di testo.</p></td>
</tr>
</tbody>
</table>

 

### Pagina dell'account del dispositivo, problemi relativi alle impostazioni per account esistenti

<table>
<tr>
<th>Problema</th>
<th>Cause</th>
<th>Codici di errore</th>
<th>Soluzioni possibili</th>
</tr>
<tr>
<td>
<p>Non è stato possibile eseguire l'autenticazione dell'account con le credenziali specificate.</p>
</td>
<td>
<p>L'account non è abilitato come utente in Active Directory (AD), richiede una password per l'autenticazione o la password non è corretta.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Assicurati che le credenziali siano immesse correttamente. Abilita l'account come utente in AD e aggiungi una password o imposta RoomMailboxPassword</p>. </td>
</tr>
<tr>
<td>
<p>Viene visualizzato l'errore 0x800C0019 quando si specifica un server Exchange.</p>
</td>
<td>
<p>L'account del dispositivo richiede un certificato per l'autenticazione.</p>
</td>
<td>
<p>0x800C0019</p>
</td>
<td>
<p>Installa il certificato appropriato con pacchetti di provisioning.</p>
</td>
</tr>
<tr>
<td>
<p>Le credenziali dell'account del dispositivo non sono valide per il server Exchange specificato.</p>
</td>
<td>
<p>Il server Exchange specificato non ospita la cassetta postale dell'account del dispositivo.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Assicurati di specificare il server di posta Exchange corretto per l'account del dispositivo.</p>
</td>
</tr>
<tr>
<td>
<p>Timeout HTTP durante il tentativo di accesso al server Exchange.</p>
</td>
<td></td>
<td>
<p>0x80072EE2</p>
</td>
<td></td>
</tr>
<tr>
<td>
<p>Non è possibile trovare il server Exchange specificato.</p>
</td>
<td>
<p>Il server Exchange specificato non è stato trovato.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Assicurati di avere una connessione di rete o a Internet funzionante e che il server Exchange specificato sia corretto.</p>
</td>
</tr>
<tr>
<td>
<p>http non supportato.</p>
</td>
<td>
<p>È stato specificato un server Exchange con <i>http://</i> invece che con <i>https://</i>.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Usa un server Exchange che usa https.</p>
</td>
</tr>
<tr>
<td rowspan="3">
<div><p>Gli utenti accedono alla pagina intitolata "Si è verificato un problema con questo account" relativa ad ActiveSync.</p>
</div>
<div> </div>
</td>
<td>
<p>Il criterio di ActiveSync PasswordEnabled è impostato su True (o 1).</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Crea un nuovo criterio di ActiveSync con PasswordEnabled impostato su False (o 0) e quindi applica tale criterio all'account.</p>
</td>
</tr>
<tr>
<td>
<p>Il dispositivo Surface Hub non ha a disposizione una connessione a Exchange.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Assicurati di avere a disposizione una connessione di rete o a Internet funzionante.</p>
</td>
</tr>
<tr>
<td>
<p>Exchange restituisce un codice di stato che indica un errore.</p>
</td>
<td>
<p>Nessuno</p>
</td>
<td>
<p>Assicurati di avere a disposizione una connessione di rete o a Internet funzionante.</p>
</td>
</tr>
</table>
 

### <a href="" id="first-run-domain-join-page"></a>Prima esecuzione, problemi relativi alla pagina di aggiunta al dominio

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problema</th>
<th align="left">Cause</th>
<th align="left">Soluzioni possibili</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Quando si tenta l'aggiunta a un dominio, un errore indica che l'account non è stato in grado di eseguire l'autenticazione usando le credenziali specificate.</p></td>
<td align="left"><p>Le credenziali specificate non sono in grado di eseguire l'aggiunta al dominio specificato.</p></td>
<td align="left"><p>Immetti le credenziali corrette per un account esistente nel dominio specificato.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Quando si specifica un gruppo di un dominio, un errore indica che il gruppo non è stato trovato nel dominio.</p></td>
<td align="left"><p>Il gruppo potrebbe essere stato rimosso o non esiste più.</p></td>
<td align="left"><p>Verifica che il gruppo esista all'interno del dominio.</p></td>
</tr>
</tbody>
</table>

 

### Prima esecuzione, pagina del server Exchange

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problema</th>
<th align="left">Cause</th>
<th align="left">Soluzioni possibili</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Gli utenti accedono a questa pagina e devono immettere l'indirizzo del server Exchange.</p></td>
<td align="left"><p>Il server Exchange non è configurato per l'individuazione automatica.</p></td>
<td align="left"><p>Abilita l'individuazione automatica del server Exchange per l'account del dispositivo oppure immetti manualmente l'indirizzo del server Exchange.</p></td>
</tr>
</tbody>
</table>

 

### <a href="" id="first-run-on-device"></a>Prima esecuzione, problemi relativi al dispositivo

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Problema</th>
<th align="left">Cause</th>
<th align="left">Codici di errore</th>
<th align="left">Soluzioni possibili</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Non è possibile sincronizzare la posta o il calendario.</p></td>
<td align="left"><p>L'account non ha autorizzato il dispositivo Surface Hub come dispositivo consentito.</p></td>
<td align="left"><p>0x86000C1C</p></td>
<td align="left"><p>Aggiungi l'ID dispositivo Surface Hub all'elenco consentiti impostando <strong> la </strong> Proprietà ActiveSyncAllowedDeviceIds per la cassetta postale.</p></td>
</tr>
</tbody>
</table>

 



 

## Errori di Exchange ActiveSync


In questa sezione sono elencati i codici di stato, il mapping, i messaggi utente e le azioni che un amministratore può eseguire per risolvere gli errori di Exchange ActiveSync.

<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Codice esadecimale</th>
<th align="left">Mapping</th>
<th align="left">Messaggio descrittivo</th>
<th align="left">Azione che deve eseguire l'amministratore</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x85010002</p></td>
<td align="left"><p>E_HTTP_DENIED</p></td>
<td align="left"><p>La password deve essere aggiornata.</p></td>
<td align="left"><p>Aggiorna la password.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072EFD</p></td>
<td align="left"><p>WININET_E_CANNOT_CONNECT</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento. Aspetta un po' di tempo e riprova o controlla le impostazioni dell'account.</p></td>
<td align="left"><p>Verifica che il nome del server sia corretto e raggiungibile. Verifica che il dispositivo sia connesso alla rete.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C29</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_NOTPROVISIONED (i criteri non corrispondono)</p></td>
<td align="left"><p>L'account è configurato con criteri non compatibili con Surface Hub.</p></td>
<td align="left"><p>Disabilita il criterio <strong>PasswordEnabled</strong> per questo account.</p>
<p>Abbiamo un bug in caso di errori di criteri di superficie se l'account non riceve le notifiche del server nell'intervallo di aggiornamento dei criteri.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C4C</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAXIMUMDEVICESREACHED</p></td>
<td align="left"><p>L'account ha troppe relazioni tra dispositivi.</p></td>
<td align="left"><p>Elimina una o più relazioni nel server.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C0A</p></td>
<td align="left"><p>E_NEXUS_STATUS_SERVERERROR_RETRYLATER</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento.</p></td>
<td align="left"><p>Aspetta fino a quando il server ritorna online. Se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050003</p></td>
<td align="left"><p>E_CREDENTIALS_EXPIRED (le credenziali sono scadute e devono essere aggiornate)</p></td>
<td align="left"><p>La password deve essere aggiornata.</p></td>
<td align="left"><p>Aggiorna la password.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x8505000D</p></td>
<td align="left"><p>E_AIRSYNC_RESET_RETRY</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento. Attendere qualche istante o controllare le impostazioni dell'account.</p></td>
<td align="left"><p>Si tratta in genere di un errore temporaneo ma, se il problema persiste, controlla il numero di dispositivi associati all'account ed eliminane alcuni se il numero è elevato.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C16</p></td>
<td align="left"><p>E_NEXUS_STATUS_USER_HASNOMAILBOX</p></td>
<td align="left"><p>È stata eseguita la migrazione della cassetta postale a un server diverso.</p></td>
<td align="left"><p>Non dovresti mai visualizzare questo errore. Se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010004</p></td>
<td align="left"><p>E_HTTP_FORBIDDEN</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento. Attendere un po' di tempo e riprovare o controllare le impostazioni dell'account.</p></td>
<td align="left"><p>Verifica il nome del server per assicurarti che sia corretto. Se l'account usa l'autenticazione basata sul certificato, assicurati che il certificato sia ancora valido e aggiornalo in caso contrario.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85030028</p></td>
<td align="left"><p>E_ACTIVESYNC_PASSWORD_OR_GETCERT</p></td>
<td align="left"><p>La password o il certificato client dell'account sono mancanti o non validi.</p></td>
<td align="left"><p>Aggiorna la password e/o distribuisci il certificato client.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x86000C2A</p></td>
<td align="left"><p>E_NEXUS_STATUS_DEVICE_POLICYREFRESH</p></td>
<td align="left"><p>L'account è configurato con criteri non compatibili con Surface Hub.</p></td>
<td align="left"><p>Disabilita i criteri PasswordEnabled per questo account.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85050002</p></td>
<td align="left"><p>E_CREDENTIALS_UNAVAILABLE</p></td>
<td align="left"><p>La password deve essere aggiornata.</p></td>
<td align="left"><p>Aggiorna la password.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE2</p></td>
<td align="left"><p>WININET_E_TIMEOUT</p></td>
<td align="left"><p>La rete non supporta il timeout minimo necessario per ricevere la notifica del server o il server è offline.</p></td>
<td align="left"><p>Verifica che il server sia in esecuzione. Verifica le impostazioni NAT.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85002004</p></td>
<td align="left"><p>E_FAIL_ABORT</p></td>
<td align="left"><p>Questo errore viene usato per interrompere la sincronizzazione bloccata e non verrà esposto agli utenti. Verrà visualizzato nei dati di diagnostica se forzi una sincronizzazione interattiva, elimini l'account o aggiorni le relative impostazioni.</p></td>
<td align="left"><p>Niente.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010017</p></td>
<td align="left"><p>E_HTTP_SERVICE_UNAVAIL</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento. Attendere qualche istante o controllare le impostazioni dell'account.</p></td>
<td align="left"><p>Verifica il nome del server per assicurarti che sia corretto. Aspetta fino a quando il server ritorna online. Se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C0D</p></td>
<td align="left"><p>E_NEXUS_STATUS_MAILBOX_SERVEROFFLINE</p></td>
<td align="left"><p>Non è possibile connettersi al server in questo momento. Attendere qualche istante o controllare le impostazioni dell'account.</p></td>
<td align="left"><p>Verifica il nome del server per assicurarti che sia corretto. Aspetta fino a quando il server ritorna online. Se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85030027</p></td>
<td align="left"><p>E_ACTIVESYNC_GETCERT</p></td>
<td align="left"><p>Il server Exchange richiede un certificato.</p></td>
<td align="left"><p>Importa il certificato EAS appropriato nel dispositivo Surface Hub.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x86000C2B</p></td>
<td align="left"><p>E_NEXUS_STATUS_INVALID_POLICYKEY</p></td>
<td align="left"><p>L'account è configurato con criteri non compatibili con Surface Hub.</p></td>
<td align="left"><p>Disabilita i criteri PasswordEnabled per questo account.</p>
<p>Abbiamo un bug in caso di errori di criteri di superficie se l'account non riceve le notifiche del server nell'intervallo di aggiornamento dei criteri.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x85010005</p></td>
<td align="left"><p>E_HTTP_NOT_FOUND</p></td>
<td align="left"><p>Nome del server non valido.</p></td>
<td align="left"><p>Verifica il nome del server per assicurarti che sia corretto. Se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x85010014</p></td>
<td align="left"><p>E_HTTP_SERVER_ERROR</p></td>
<td align="left"><p>Non è possibile connettersi al server.</p></td>
<td align="left"><p>Verifica il nome del server per assicurarti che sia corretto. Attiva una sincronizzazione e, se il problema persiste, esegui di nuovo il provisioning dell'account.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80072EE7</p></td>
<td align="left"><p>WININET_E_NAME_NOT_RESOLVED</p></td>
<td align="left"><p>Non è possibile risolvere l'indirizzo o il nome del server.</p></td>
<td align="left"><p>Assicurati che il nome del server sia stato immesso correttamente.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x8007052F</p></td>
<td align="left"><p>ERROR_ACCOUNT_RESTRICTION</p></td>
<td align="left"><p>Durante l'individuazione automatica del server Exchange, viene applicato un criterio che impedisce all'utente connesso di accedere al server.</p></td>
<td align="left"><p>Si tratta di un problema di temporizzazione. Verifica nuovamente le credenziali dell'account. Prova a rieseguire il provisioning con le credenziali corrette.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x800C0019</p></td>
<td align="left"><p>INET_E_INVALID_CERTIFICATE</p></td>
<td align="left"><p>Il certificato di sicurezza necessario per accedere a questa risorsa non è valido.</p></td>
<td align="left"><p>Installa il certificato ActiveSync corretto necessario per l'account del dispositivo specificato.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x80072F0D</p></td>
<td align="left"><p>WININET_E_INVALID_CA</p></td>
<td align="left"><p>L'autorità di certificazione non è valida o non è corretta. Non è possibile individuare automaticamente il server Exchange perché manca un certificato.</p></td>
<td align="left"><p>Installa il certificato ActiveSync corretto necessario per l'account del dispositivo specificato.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x80004005</p></td>
<td align="left"><p>E_FAIL</p></td>
<td align="left"><p>Non è possibile trovare il dominio specificato. Il server Exchange non è stato individuato automaticamente e non è stato specificato nelle impostazioni.</p></td>
<td align="left"><p>Assicurati che il dominio immesso sia il nome di dominio completo e che sia stato immesso un server Exchange nella relativa casella di testo.</p></td>
</tr>
</tbody>
</table>

##  <a name="contact-support"></a>Supporto tecnico

Se si hanno domande o si ha bisogno di assistenza, è possibile [creare una richiesta di supporto](https://support.microsoft.com/supportforbusiness/productselection).


 
## Contenuti correlati

- [Risoluzione dei problemi di connessione Miracast a Surface Hub](https://docs.microsoft.com/surface-hub/miracast-troubleshooting)
 






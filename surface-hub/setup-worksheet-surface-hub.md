---
title: Foglio di lavoro per la configurazione (Surface Hub)
description: Quando al termine della pre-installazione vuoi avviare la prima configurazione di Surface Hub, accertati di avere tutte le info elencate in questa sezione.
ms.assetid: AC6F925B-BADE-48F5-8D53-8B6FFF6EE3EB
ms.reviewer: ''
manager: laurawi
keywords: foglio di lavoro per la configurazione, pre-configurazione, prima configurazione
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: e0c31082669336d3762fd02f46a939aa8b0ff1bc
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833854"
---
# Foglio di lavoro per la configurazione (Surface Hub)


Quando al termine della pre-installazione vuoi avviare la prima configurazione del tuo dispositivo Microsoft Surface Hub, accertati di avere tutte le informazioni elencate in questa sezione.

Devi compilare un elenco per ogni dispositivo Surface Hub da configurare, anche se alcune informazioni possono essere usate in tutti i dispositivi Surface Hub, come le informazioni sul proxy o le credenziali di dominio. Alcune di queste informazioni potrebbero non essere necessarie, a seconda di come hai scelto di configurare il dispositivo o a seconda di come è configurato l'ambiente per l'infrastruttura dell'organizzazione.

<table>
<tr>
<th>Proprietà</th>
<th>In quali casi si usa</th>
<th>Esempio</th>
<th>Valore effettivo</th>
</tr>
<tr>
<td>
<p>Informazioni sul proxy</p>
</td>
<td>
<p>Se la rete usa un proxy per l'accesso alla rete e/o a Internet, devi specificare uno script o informazioni sulla porta o sul server.</p>
</td>
<td>
<p>Script proxy: <code>http://contoso/proxy.pa</code> </br>
- oppure - </br>
Informazioni sul server e sulla porta: 10.10.10.100, porta 80
</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Credenziali di rete wireless (nome utente e password)</p>
</td>
<td>
<p>Se decidi di connettere il tuo dispositivo al Wi-Fi e la rete wireless richiede le credenziali utente.</p>
</td>
<td>
<p>admin1@contoso.com, #MiaPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>UPN dell'account del dispositivo o Dominio\nomeutente e password dell'account del dispositivo</p>
</td>
<td>
<p>Si tratta del nome dell'entità utente (UPN) o del dominio\nomeutente e della password dell'account del dispositivo. La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.</p>
</td>
<td>
<p> UPN: ConfRoom15@contoso.com, #Passw0rd1 </br>
- oppure - <br> 
Nome utente e dominio: CONTOSO\ConfRoom15, #Passw0rd1</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Server Microsoft Exchange dell'account del dispositivo</p>
</td>
<td>
<p>Si tratta del server Exchange dell'account del dispositivo.
La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.
Per il corretto funzionamento della posta e del calendario, l'account del dispositivo deve avere un server Exchange valido. Il dispositivo tenterà di trovarlo automaticamente.</p>
</td>
<td>
<p>outlook.office365.com</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Indirizzo SIP (Session Initiation Protocol) dell'account del dispositivo</p>
</td>
<td>
<p>Si tratta dell'indirizzo SIP Skype for Business dell'account del dispositivo.
La posta, il calendario e Skype for Business dipendono da un account del dispositivo compatibile.
Per il corretto funzionamento di Skype for Business, l'account del dispositivo deve avere un indirizzo SIP valido. Il dispositivo tenterà di trovarlo automaticamente.</p>
</td>
<td>
<p>SIP: ConfRoom15@contoso.com</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Nome descrittivo</p>
</td>
<td>
<p>Il nome descrittivo del dispositivo è il nome di broadcast che gli utenti vedranno quando provano a connettersi in modalità wireless a Surface Hub. Questo nome verrà visualizzato in evidenza sullo schermo di Surface Hub.
Ti consigliamo di scegliere un nome descrittivo riconoscibile e univoco, in modo che gli utenti possano distinguere un dispositivo Surface Hub da un altro durante il tentativo di connessione.</p>
</td>
<td>
<p>Sala riunioni 15</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Nome dispositivo</p>
</td>
<td>
<p>Il nome del dispositivo è il nome che verrà usato per l'aggiunta al dominio ed è l'identità che visualizzerai nel provider MDM se il dispositivo è registrato in MDM.
Il nome del dispositivo scelto non deve essere uguale a quello di altri dispositivi nel dominio Active Directory dell'utente (se decidi di aggiungere il dispositivo al dominio). Il dispositivo non può essere aggiunto al dominio se il nome non è univoco.
</p>
</td>
<td>
<p>sala15</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>PER L'AGGIUNTA AD AZURE AD</b></p>
</td>
</tr>
<tr>
<td>
<p>Credenziali utente tenant di Azure AD (nome utente e password)</p>
</td>
<td>
<p>Se decidi di assegnare a persone della tua organizzazione Azure Active Directory (Azure AD) il ruolo di amministratori del dispositivo, devi eseguire l'aggiunta ad Azure AD.
Per l'aggiunta ad Azure AD, devi avere credenziali utente valide.</p>
</td>
<td>
<p>admin1@contoso.com, #MiaPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>PER L'AGGIUNTA A UN DOMINIO</b></p>
</td>
</tr>
<tr>
<td>
<p>Dominio per l'aggiunta</p>
</td>
<td>
<p>Si tratta del dominio a cui dovrai eseguire l'aggiunta per consentire al gruppo di sicurezza scelto di diventare amministratori del dispositivo.
Potrebbe servirti il nome di dominio completo (FQDN).</p>
</td>
<td>
<p>contoso (nome breve) O contoso.corp.com (FQDN)</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Credenziali dell'account di dominio (nome utente e password)</p>
</td>
<td>
<p>L'aggiunta a un dominio non può avvenire a meno che non specifichi credenziali dell'account sufficienti per l'aggiunta al dominio. Dopo aver specificato un dominio per l'aggiunta e le credenziali per l'aggiunta al dominio, il gruppo di sicurezza scelto può modificare le impostazioni nel dispositivo.</p>
</td>
<td>
<p>admin1, #MiaPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td>
<p>Alias gruppo di sicurezza amministratori</p>
</td>
<td>
<p>Si tratta di un gruppo di sicurezza in Active Directory (AD). I membri di questo gruppo di sicurezza possono modificare le impostazioni nel dispositivo.</p>
</td>
<td>
<p>AmministratoriSurfaceHub</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>SE USI UN AMMINISTRATORE LOCALE</b></p>
</td>
</tr>
<tr>
<td>
<p>Credenziali dell'account dell'amministratore locale (nome utente e password)</p>
</td>
<td>
<p>Se decidi di non eseguire l'aggiunta a un dominio AD o ad Azure AD, puoi creare un account amministratore locale nel dispositivo.</p>
</td>
<td>
<p>admin1, #MiaPassw0rd</p>
</td>
<td>
<p></p>
</td>
</tr>
<tr>
<td colspan="4">
<p><b>SE VUOI INSTALLARE CERTIFICATI O APP</b></p>
</td>
</tr>
<tr>
<td>
<p>Unità USB</p>
</td>
<td>
<p>Se prima della prima esecuzione sai di voler installare certificati o app universali, segui i passaggi descritti in <a href="provisioning-packages-for-certificates-surface-hub.md">Creare pacchetti di provisioning</a>. I pacchetti di provisioning verranno creati in un'unità USB.</p>
</td>
<td>
<p></p>
</td>
<td>
<p></p>
</td>
</tr>
</table> 






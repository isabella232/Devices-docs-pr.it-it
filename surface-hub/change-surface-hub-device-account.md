---
title: Modificare l'account del dispositivo Microsoft Surface Hub
description: In Impostazioni puoi aggiungere un account del dispositivo se non è ancora configurato o modificare le proprietà di un account già configurato.
ms.assetid: AFC43043-3319-44BC-9310-29B1F375E672
ms.reviewer: ''
manager: laurawi
keywords: modificare l'account del dispositivo, modificare le proprietà, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: b90ef3e208f1e76e4b02fb9f49e3e24030947bc7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10834082"
---
# Modificare l'account del dispositivo Microsoft Surface Hub


Puoi modificare l'account del dispositivo in Impostazioni per aggiungere un account se non è stato configurato nessun account o per modificare le proprietà di un account che è già stato configurato.

## Dettagli


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Valore</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Nome entità utente</p></td>
<td align="left"><p>Nome dell'entità utente (UPN) dell'account del dispositivo.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Password</p></td>
<td align="left"><p>Password corrispondente dell'account del dispositivo.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Dominio</p></td>
<td align="left"><p>Dominio a cui appartiene l'account del dispositivo. Non è necessario specificare le informazioni in questo campo per gli account di Office 365.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Nome utente</p></td>
<td align="left"><p>Nome utente dell'account del dispositivo. Non è necessario specificare le informazioni in questo campo per gli account di Office 365.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Indirizzo SIP (Session Initiation Protocol)</p></td>
<td align="left"><p>Indirizzo SIP dell'account del dispositivo.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Server Microsoft Exchange</p></td>
<td align="left"><p>Server Exchange dell'account del dispositivo. Il nome utente e la password dell'account del dispositivo devono essere in grado di eseguire l'autenticazione nel server Exchange specificato.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Abilita servizi di Exchange</p></td>
<td align="left"><p>Quando il valore è selezionato, tutti i servizi di Exchange verranno abilitati (ad esempio, il calendario nella schermata iniziale, l'invio delle lavagne tramite e-mail). Quando il valore non è selezionato, tutti i servizi di Exchange saranno disabilitati e il server Exchange non dovrà essere specificato.</p></td>
</tr>
</tbody>
</table>

 

## Conseguenze


L'UPN e la password vengono usati per convalidare l'account in AD o Azure AD. Se la convalida ha esito negativo, potresti dover specificare dominio e nome utente.

Usando le credenziali fornite, Microsoft proverà a individuare l'indirizzo SIP. Se non viene trovato alcun indirizzo SIP, Skype for Business userà l'UPN come indirizzo SIP. Se non si tratta dell'indirizzo SIP corretto per l'account, dovrai specificare l'indirizzo SIP.

Se il dispositivo non riesce a trovare un server associato alle credenziali di accesso, dovrai specificare l'indirizzo del server Exchange. Microsoft Surface Hub userà il server Exchange per comunicare con ActiveSync, un componente che abilita diverse funzionalità chiave nel dispositivo.

## Argomenti correlati


[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

 

 






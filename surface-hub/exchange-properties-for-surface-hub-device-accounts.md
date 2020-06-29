---
title: Proprietà di Microsoft Exchange (Surface Hub)
description: Certe proprietà di Exchange dell&#39;account del dispositivo devono essere impostate su valori specifici per un&#39;esperienza ottimale per le riunioni in Surface Hub.
ms.assetid: 3E84393B-C425-45BF-95A6-D6502BA1BF29
ms.reviewer: ''
manager: laurawi
keywords: Proprietà di Microsoft Exchange, account del dispositivo, Surface Hub, cmdlet di Windows PowerShell
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: medium
ms.openlocfilehash: 8879762857146011f3e1a198b72a895bc6bf9473
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833698"
---
# Proprietà di Microsoft Exchange (Surface Hub)


Alcune proprietà di Microsoft Exchange dell&#39;account del dispositivo devono essere impostate su valori specifici per ottenere un&#39;esperienza ottimale per le riunioni in Microsoft Surface Hub. La tabella seguente elenca diverse proprietà di Exchange basate sui parametri dei cmdlet di PowerShell, il rispettivo scopo e i valori su cui devono essere impostate.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Proprietà</th>
<th align="left">Descrizione</th>
<th align="left">Valore</th>
<th align="left">Impatto</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>AutomateProcessing</p></td>
<td align="left"><p>Il parametro AutomateProcessing abilita o disabilita l'elaborazione del calendario nella cassetta postale.</p></td>
<td align="left"><p>AutoAccept</p></td>
<td align="left"><p>Il dispositivo Surface Hub sarà in grado di accettare o rifiutare automaticamente le convocazioni riunione in base alla disponibilità.</p></td>
</tr>
<tr class="even">
<td align="left"><p>AddOrganizerToSubject</p></td>
<td align="left"><p>Il parametro AddOrganizerToSubject specifica se il nome dell'organizzatore della riunione viene usato come oggetto della convocazione riunione.</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>La schermata iniziale non mostrerà due volte l'organizzatore della riunione (anziché visualizzarlo sia come organizzatore sia nell'oggetto della riunione).</p></td>
</tr>
<tr class="odd">
<td align="left"><p>AllowConflicts</p></td>
<td align="left"><p>Il parametro AllowConflicts indica se consentire o meno le convocazioni riunione in conflitto.</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>Il dispositivo Surface Hub rifiuterà le convocazioni riunione in conflitto con l'orario di un'altra riunione.</p></td>
</tr>
<tr class="even">
<td align="left"><p>DeleteComments</p></td>
<td align="left"><p>Il parametro DeleteComments indica se rimuovere o mantenere il testo nel corpo del messaggio delle convocazioni riunione in arrivo.</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>Il corpo del messaggio delle riunioni può essere conservato e recuperato da un dispositivo Surface Hub, se necessario durante una riunione.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>DeleteSubject</p></td>
<td align="left"><p>Il parametro DeleteSubject indica se rimuovere o mantenere l'oggetto delle convocazioni riunione in arrivo.</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>Gli oggetti delle convocazioni riunione possono essere visualizzati nel dispositivo Surface Hub.</p></td>
</tr>
<tr class="even">
<td align="left"><p>RemovePrivateProperty</p></td>
<td align="left"><p>Il parametro RemovePrivateProperty indica se eliminare o meno il flag privato per le convocazioni riunione in arrivo.</p></td>
<td align="left"><p>$False</p></td>
<td align="left"><p>Gli oggetti delle riunioni private verranno indicati come Privato nella schermata iniziale.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>AddAdditionalResponse</p></td>
<td align="left"><p>Il parametro AddAdditionalResponse indica se verranno inviate informazioni aggiuntive dalla cassetta postale delle risorse in risposta alle convocazioni riunione.</p></td>
<td align="left"><p>$True</p></td>
<td align="left"><p>Quando viene inviata una risposta a una convocazione riunione, nella risposta verrà inserito testo personalizzato.</p></td>
</tr>
<tr class="even">
<td align="left"><p>AdditionalResponse</p></td>
<td align="left"><p>Il parametro AdditionalResponse specifica le informazioni aggiuntive da includere nelle risposte alle convocazioni riunione.</p>
<div class="alert">
<strong>Nota </strong> questo testo non verrà inviato a meno che AddAdditionalResponse non sia impostato su $true.
</div>
<div>
 
</div></td>
<td align="left"><p>A tua scelta: la risposta aggiuntiva può essere usata per informare gli utenti su come usare un dispositivo Surface Hub o indirizzarli verso le risorse.</p></td>
<td align="left"><p>L'aggiunta di un messaggio di risposta aggiuntivo può offrire agli utenti un'introduzione su come usare un dispositivo Surface Hub durante la riunione.</p></td>
</tr>
</tbody>
</table>

 

 

 






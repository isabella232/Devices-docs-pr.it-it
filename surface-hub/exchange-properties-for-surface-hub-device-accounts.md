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
# <span data-ttu-id="5025c-104">Proprietà di Microsoft Exchange (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="5025c-104">Microsoft Exchange properties (Surface Hub)</span></span>


<span data-ttu-id="5025c-105">Alcune proprietà di Microsoft Exchange dell&#39;account del dispositivo devono essere impostate su valori specifici per ottenere un&#39;esperienza ottimale per le riunioni in Microsoft Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5025c-105">Some Microsoft Exchange properties of the device account must be set to particular values to have the best meeting experience on Microsoft Surface Hub.</span></span> <span data-ttu-id="5025c-106">La tabella seguente elenca diverse proprietà di Exchange basate sui parametri dei cmdlet di PowerShell, il rispettivo scopo e i valori su cui devono essere impostate.</span><span class="sxs-lookup"><span data-stu-id="5025c-106">The following table lists various Exchange properties based on PowerShell cmdlet parameters, their purpose, and the values they should be set to.</span></span>

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5025c-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="5025c-107">Property</span></span></th>
<th align="left"><span data-ttu-id="5025c-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="5025c-108">Description</span></span></th>
<th align="left"><span data-ttu-id="5025c-109">Valore</span><span class="sxs-lookup"><span data-stu-id="5025c-109">Value</span></span></th>
<th align="left"><span data-ttu-id="5025c-110">Impatto</span><span class="sxs-lookup"><span data-stu-id="5025c-110">Impact</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><span data-ttu-id="5025c-111">AutomateProcessing</span><span class="sxs-lookup"><span data-stu-id="5025c-111">AutomateProcessing</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-112">Il parametro AutomateProcessing abilita o disabilita l'elaborazione del calendario nella cassetta postale.</span><span class="sxs-lookup"><span data-stu-id="5025c-112">The AutomateProcessing parameter enables or disables calendar processing on the mailbox.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-113">AutoAccept</span><span class="sxs-lookup"><span data-stu-id="5025c-113">AutoAccept</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-114">Il dispositivo Surface Hub sarà in grado di accettare o rifiutare automaticamente le convocazioni riunione in base alla disponibilità.</span><span class="sxs-lookup"><span data-stu-id="5025c-114">The Surface Hub will be able to automatically accept or decline meeting requests based on its availability.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="5025c-115">AddOrganizerToSubject</span><span class="sxs-lookup"><span data-stu-id="5025c-115">AddOrganizerToSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-116">Il parametro AddOrganizerToSubject specifica se il nome dell'organizzatore della riunione viene usato come oggetto della convocazione riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-116">The AddOrganizerToSubject parameter specifies whether the meeting organizer's name is used as the subject of the meeting request.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-117">$False</span><span class="sxs-lookup"><span data-stu-id="5025c-117">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-118">La schermata iniziale non mostrerà due volte l'organizzatore della riunione (anziché visualizzarlo sia come organizzatore sia nell'oggetto della riunione).</span><span class="sxs-lookup"><span data-stu-id="5025c-118">The welcome screen will not show the meeting organizer twice (instead of showing it as both the organizer and in the meeting subject).</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="5025c-119">AllowConflicts</span><span class="sxs-lookup"><span data-stu-id="5025c-119">AllowConflicts</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-120">Il parametro AllowConflicts indica se consentire o meno le convocazioni riunione in conflitto.</span><span class="sxs-lookup"><span data-stu-id="5025c-120">The AllowConflicts parameter specifies whether to allow conflicting meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-121">$False</span><span class="sxs-lookup"><span data-stu-id="5025c-121">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-122">Il dispositivo Surface Hub rifiuterà le convocazioni riunione in conflitto con l'orario di un'altra riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-122">The Surface Hub will decline meeting requests that conflict with another meeting’s time.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="5025c-123">DeleteComments</span><span class="sxs-lookup"><span data-stu-id="5025c-123">DeleteComments</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-124">Il parametro DeleteComments indica se rimuovere o mantenere il testo nel corpo del messaggio delle convocazioni riunione in arrivo.</span><span class="sxs-lookup"><span data-stu-id="5025c-124">The DeleteComments parameter specifies whether to remove or keep any text in the message body of incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-125">$False</span><span class="sxs-lookup"><span data-stu-id="5025c-125">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-126">Il corpo del messaggio delle riunioni può essere conservato e recuperato da un dispositivo Surface Hub, se necessario durante una riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-126">The message body of meetings can be retained and retrieved from a Surface Hub if you need it during a meeting.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="5025c-127">DeleteSubject</span><span class="sxs-lookup"><span data-stu-id="5025c-127">DeleteSubject</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-128">Il parametro DeleteSubject indica se rimuovere o mantenere l'oggetto delle convocazioni riunione in arrivo.</span><span class="sxs-lookup"><span data-stu-id="5025c-128">The DeleteSubject parameter specifies whether to remove or keep the subject of incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-129">$False</span><span class="sxs-lookup"><span data-stu-id="5025c-129">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-130">Gli oggetti delle convocazioni riunione possono essere visualizzati nel dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="5025c-130">Meeting request subjects can be shown on the Surface Hub.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="5025c-131">RemovePrivateProperty</span><span class="sxs-lookup"><span data-stu-id="5025c-131">RemovePrivateProperty</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-132">Il parametro RemovePrivateProperty indica se eliminare o meno il flag privato per le convocazioni riunione in arrivo.</span><span class="sxs-lookup"><span data-stu-id="5025c-132">The RemovePrivateProperty parameter specifies whether to clear the private flag for incoming meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-133">$False</span><span class="sxs-lookup"><span data-stu-id="5025c-133">$False</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-134">Gli oggetti delle riunioni private verranno indicati come Privato nella schermata iniziale.</span><span class="sxs-lookup"><span data-stu-id="5025c-134">Private meeting subjects will show as Private on the welcome screen.</span></span></p></td>
</tr>
<tr class="odd">
<td align="left"><p><span data-ttu-id="5025c-135">AddAdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="5025c-135">AddAdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-136">Il parametro AddAdditionalResponse indica se verranno inviate informazioni aggiuntive dalla cassetta postale delle risorse in risposta alle convocazioni riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-136">The AddAdditionalResponse parameter specifies whether additional information will be sent from the resource mailbox when responding to meeting requests.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-137">$True</span><span class="sxs-lookup"><span data-stu-id="5025c-137">$True</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-138">Quando viene inviata una risposta a una convocazione riunione, nella risposta verrà inserito testo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="5025c-138">When a response is sent to a meeting request, custom text will be provided in the response.</span></span></p></td>
</tr>
<tr class="even">
<td align="left"><p><span data-ttu-id="5025c-139">AdditionalResponse</span><span class="sxs-lookup"><span data-stu-id="5025c-139">AdditionalResponse</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-140">Il parametro AdditionalResponse specifica le informazioni aggiuntive da includere nelle risposte alle convocazioni riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-140">The AdditionalResponse parameter specifies the additional information to be included in responses to meeting requests.</span></span></p>
<div class="alert">
<strong><span data-ttu-id="5025c-141">Nota </strong> questo testo non verrà inviato a meno che AddAdditionalResponse non sia impostato su $true.</span><span class="sxs-lookup"><span data-stu-id="5025c-141">Note</strong>This text will not be sent unless AddAdditionalResponse is set to $True.</span></span>
</div>
<div>
 
</div></td>
<td align="left"><p><span data-ttu-id="5025c-142">A tua scelta: la risposta aggiuntiva può essere usata per informare gli utenti su come usare un dispositivo Surface Hub o indirizzarli verso le risorse.</span><span class="sxs-lookup"><span data-stu-id="5025c-142">Your choice—the additional response can be used to inform people how to use a Surface Hub or point them towards resources.</span></span></p></td>
<td align="left"><p><span data-ttu-id="5025c-143">L'aggiunta di un messaggio di risposta aggiuntivo può offrire agli utenti un'introduzione su come usare un dispositivo Surface Hub durante la riunione.</span><span class="sxs-lookup"><span data-stu-id="5025c-143">Adding an additional response message can provide people an introduction to how they can use a Surface Hub in their meeting.</span></span></p></td>
</tr>
</tbody>
</table>

 

 

 






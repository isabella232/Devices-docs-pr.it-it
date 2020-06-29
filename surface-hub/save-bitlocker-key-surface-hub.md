---
title: Salvare la chiave di BitLocker (Surface Hub)
description: Ogni dispositivo Microsoft Surface Hub viene automaticamente configurato con il software di crittografia delle unità BitLocker. Microsoft consiglia vivamente di assicurarti di eseguire il backup delle chiavi di ripristino di BitLocker.
ms.assetid: E11E4AB6-B13E-4ACA-BCE1-4EDC9987E4F2
ms.reviewer: ''
manager: laurawi
keywords: Surface Hub, BitLocker, chiavi di ripristino di BitLocker
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/08/2019
ms.localizationpriority: medium
ms.openlocfilehash: 73efa418fa80ef90a643d4fb4c457280ab982b38
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833866"
---
# Salvare la chiave di BitLocker (Surface Hub)


Ogni dispositivo Microsoft Surface Hub viene automaticamente configurato con il software di crittografia delle unità BitLocker. Microsoft consiglia vivamente di assicurarti di eseguire il backup delle chiavi di ripristino di BitLocker.

Esistono diversi modi per gestire la chiave BitLocker in Surface Hub.

1.  Se hai aggiunto il dispositivo Surface Hub a un dominio, il dispositivo eseguirà il backup della chiave nel dominio e la archivierà nell'oggetto computer.

    Se non riesci a trovare la chiave BitLocker dopo aver aggiunto il dispositivo a un dominio, è probabile che lo schema di Active Directory non supporti il backup della chiave BitLocker. Se non vuoi modificare lo schema, puoi salvare la chiave BitLocker accedendo a Impostazioni e seguendo la procedura per usare un account amministratore locale, descritta nel dettaglio più avanti nell'elenco.

2.  Se hai aggiunto il dispositivo Surface Hub ad Azure Active Directory (Azure AD), la chiave BitLocker verrà archiviata con l'account usato per aggiungere il dispositivo.

3.  Se si usa un account di amministrazione locale per gestire il dispositivo, è possibile salvare la chiave BitLocker accedendo all'app **Impostazioni** e passando a **Aggiorna &** &gt; **ripristino**della sicurezza. Inserisci un'unità USB e seleziona l'opzione per salvare la chiave BitLocker. La chiave verrà salvata in un file di testo nell'unità USB.


## Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

 

 






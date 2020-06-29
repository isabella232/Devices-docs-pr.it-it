---
title: Gestire la rotazione della password dell'account del dispositivo
description: Informazioni su come configurare gli account locali di Surface Hub 2S con PowerShell
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: ea445588fe2242e3200284a39fdb4a3a8473f94a
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833998"
---
# Gestire la rotazione della password dell'account del dispositivo

Puoi configurare Surface Hub 2S per cambiare automaticamente la password di un account del dispositivo senza richiedere di aggiornare manualmente le informazioni sull'account del dispositivo.

Se si attiva la rotazione della password, Surface Hub 2S cambia la password ogni 7 giorni. Le password generate automaticamente contengono caratteri di 15-32, tra cui una combinazione di lettere maiuscole e minuscole, numeri e caratteri speciali.

Le password non cambiano durante una riunione. Se Surface Hub 2S è disattivato, tenta di cambiare la password immediatamente quando viene attivato o ogni 10 minuti fino al completamento.

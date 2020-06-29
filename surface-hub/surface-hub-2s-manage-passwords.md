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
# <span data-ttu-id="c1eb6-104">Gestire la rotazione della password dell'account del dispositivo</span><span class="sxs-lookup"><span data-stu-id="c1eb6-104">Manage device account password rotation</span></span>

<span data-ttu-id="c1eb6-105">Puoi configurare Surface Hub 2S per cambiare automaticamente la password di un account del dispositivo senza richiedere di aggiornare manualmente le informazioni sull'account del dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c1eb6-105">You can configure Surface Hub 2S to automatically change a device account password without requiring you to manually update the device account information.</span></span>

<span data-ttu-id="c1eb6-106">Se si attiva la rotazione della password, Surface Hub 2S cambia la password ogni 7 giorni.</span><span class="sxs-lookup"><span data-stu-id="c1eb6-106">If you turn on Password Rotation, Surface Hub 2S changes the password every 7 days.</span></span> <span data-ttu-id="c1eb6-107">Le password generate automaticamente contengono caratteri di 15-32, tra cui una combinazione di lettere maiuscole e minuscole, numeri e caratteri speciali.</span><span class="sxs-lookup"><span data-stu-id="c1eb6-107">The automatically generated passwords contain 15-32 characters including  a combination of uppercase and lowercase letters, numbers, and special characters.</span></span>

<span data-ttu-id="c1eb6-108">Le password non cambiano durante una riunione.</span><span class="sxs-lookup"><span data-stu-id="c1eb6-108">Passwords do not change during a meeting.</span></span> <span data-ttu-id="c1eb6-109">Se Surface Hub 2S è disattivato, tenta di cambiare la password immediatamente quando viene attivato o ogni 10 minuti fino al completamento.</span><span class="sxs-lookup"><span data-stu-id="c1eb6-109">If Surface Hub 2S is turned off, it attempts to change the password immediately when turned on or every 10 minutes until successful.</span></span>

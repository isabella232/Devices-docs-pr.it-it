---
title: Compatibilità dei dispositivi Surface con Windows 10 Long-Term Servicing Channel (Surface)
description: Scopri la compatibilità e le limitazioni dei dispositivi Surface che eseguono Windows 10 Enterprise edizione LTSB.
keywords: ltsb, aggiornamento, opzioni di manutenzione della superficie
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 07/21/2021
ms.reviewer: scottmca
manager: laurawi
ms.openlocfilehash: d8c1e0996b02ac385b587661f3894ce30e406d9a
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448919"
---
# <a name="surface-device-compatibility-with-windows-10-long-term-servicing-channel-ltsc"></a>Compatibilità dei dispositivi Surface con Windows 10 Long-Term Servicing Channel (LTSC)

I dispositivi Surface sono progettati per offrire esperienze ottimali in scenari di produttività e di uso generale. Gli aggiornamenti regolari consentono ai dispositivi Surface di offrire innovazioni ed evolversi con le nuove funzionalità Windows 10 aggiornamenti delle funzionalità. Gli aggiornamenti delle funzionalità sono disponibili solo nelle Windows 10 Pro o Windows 10 Enterprise che ricevono aggiornamenti continui tramite Semi-Annual Channel (SAC).

A differenza dell'opzione di manutenzione SAC, precedentemente nota come opzioni di manutenzione CB (Current Branch) o CBB (Current Branch for Business), non è possibile selezionare l'opzione Long-Term Servicing Channel (LTSC) nelle impostazioni di Windows 10. Per utilizzare l'opzione di manutenzione LTSC, è necessario installare un'edizione separata di Windows 10 Enterprise, nota come Windows 10 Enterprise LTSC, in precedenza noto come Windows 10 Enterprise LTSB (Long-Term Servicing Branch).

>[!TIP]
>Per le informazioni più recenti su LTSC, fare riferimento alle seguenti domande frequenti: La versione successiva [Windows 10 Long Term Servicing Channel (LTSC](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/the-next-windows-10-long-term-servicing-channel-ltsc-release/ba-p/2147232)).

 Oltre a fornire un modello di manutenzione esteso, l'edizione LTSC di Windows 10 Enterprise offre anche un ambiente con diversi componenti Windows componenti rimossi. Le esperienze surface di base che influiscono su LTSC includono:

* Windows aggiornamenti delle funzionalità, inclusi miglioramenti quali:

  * Miglioramenti all'input penna diretto e al rifiuto del palmo fornito in Windows 10 versione 1607 (noto anche come aggiornamento dell'anniversario)
  * Supporto migliorato per le applicazioni DPI elevate fornite in Windows 10 versione 1703 (noto anche come Creators Update)

* Impostazioni di riservatezza della pressione fornite dall'app Surface

* Il Area Windows Ink

* Key touch-optimized in-box applications including Microsoft Edge, OneNote, Calendar, and Camera

L'uso dell'ambiente ltSC di Windows 10 Enterprise nei dispositivi Surface comporta esperienze utente finali non ottimali e dovresti evitare di usarlo in ambienti in cui gli utenti desiderano e si aspettano un'esperienza utente premium e aggiornata.

L'opzione di manutenzione LTSC è progettata per tipi di dispositivi e scenari in cui l'attributo chiave è destinato a funzionalità o funzionalità che non cambiano mai. Alcuni esempi sono i sistemi di produzione di energia o di apparecchiature mediche o i sistemi incorporati nei chioschi multimediale, ad esempio bancomat o sistemi di biglietteria per l'aeroporto.

>[!NOTE]
>Per informazioni generali sui Windows di manutenzione, incluso LTSC, vedere [Overview of Windows as a Service](/windows/deployment/update/waas-overview).

Come linea guida generale, i dispositivi che soddisfano i criteri seguenti sono considerati dispositivi generici e devono essere associati a Windows 10 Pro o Windows 10 Enterprise usando l'opzione di manutenzione del canale Semi-Annual:

* Dispositivi che eseguono software di produttività come Microsoft Office

* Dispositivi che usano Microsoft Store applicazioni

* Dispositivi usati per l'esplorazione generale di Internet (ad esempio, ricerca o accesso ai social media)

Prima di scegliere di usare Windows 10 Enterprise edizione LTSC nei dispositivi Surface, prendi in considerazione le limitazioni seguenti:

* Gli aggiornamenti di driver e firmware non vengono testati in modo esplicito rispetto alle versioni di Windows 10 Enterprise LTSC.

* In caso di problemi, il supporto Tecnico Microsoft fornirà assistenza per la risoluzione dei problemi. Tuttavia, a causa della natura di manutenzione di Windows LTSC, la risoluzione dei problemi potrebbe richiedere l'aggiornamento dei dispositivi a una versione più recente di Windows 10 Enterprise LTSC o Windows 10 Pro o Enterprise con l'opzione di manutenzione SAC.

* Le sostituzioni di dispositivi Surface (ad esempio, i dispositivi sostituiti in garanzia) possono contenere lievi variazioni nei componenti hardware che richiedono driver di dispositivo e firmware aggiornati. La compatibilità con questi aggiornamenti potrebbe richiedere l'installazione di una versione più recente di Windows 10 Enterprise LTSC o Windows 10 Pro o Enterprise con l'opzione di manutenzione SAC.

>[!NOTE]
>Le organizzazioni che standardizzano una versione specifica di Windows 10 Enterprise LTSC potrebbero non essere in grado di adottare nuove generazioni di hardware Surface come Surface Pro 8, Surface Pro X o Surface Laptop 4 senza eseguire l'aggiornamento a una versione successiva di Windows 10 Enterprise LTSC o Windows 10 Pro o Enterprise. Per ulteriori informazioni, fare riferimento alle domande frequenti sul ciclo di [vita - Windows](/lifecycle/faq/windows#what-are-the-requirements-for-servicing-and-updating-the-windows-10-long-term-servicing-channel--ltsc--).

I dispositivi Surface che Windows 10 Enterprise'edizione LTSC non riceveranno nuove funzionalità. In molti casi, i clienti richiedono queste funzionalità per migliorare l'usabilità e le funzionalità dell'hardware Surface. Ad esempio, ulteriori miglioramenti per le applicazioni con valori DPI elevati in Windows 10 versione 1703. I clienti che usano dispositivi Surface nella configurazione LTSC non vedranno i miglioramenti fino a quando non vengono aggiornati a una nuova versione di Windows 10 Enterprise LTSC o a una versione di Windows 10 con supporto per l'opzione di manutenzione SAC.

I dispositivi possono essere modificati da Windows 10 Enterprise LTSC a una versione più recente di Windows 10 Enterprise, con il supporto per l'opzione di manutenzione SAC, senza perdere i dati degli utenti eseguendo un'installazione di aggiornamento. Puoi anche eseguire un'installazione di aggiornamento su più dispositivi sfruttando i modelli di sequenza di attività di aggiornamento disponibili in Microsoft Deployment Toolkit (MDT) e Microsoft Endpoint Configuration Manager. Per altre informazioni, vedi [Aggiornare i dispositivi Surface Windows 10 con Microsoft Deployment Toolkit](upgrade-surface-devices-to-windows-10-with-mdt.md).

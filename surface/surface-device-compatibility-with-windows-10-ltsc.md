---
title: Compatibilità dei dispositivi di Surface con il canale di manutenzione a lungo termine di Windows 10 (Surface)
description: Informazioni sulla compatibilità e sulle limitazioni dei dispositivi Surface con Windows 10 Enterprise LTSB Edition.
keywords: opzioni di ltsb, aggiornamento e manutenzione superficiale
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: scottmca
manager: laurawi
ms.openlocfilehash: db3dfd57c3b79fcec507ffd146483915490801b9
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832235"
---
# Compatibilità dei dispositivi di Surface con il canale di manutenzione a lungo termine di Windows 10 (LTSC)

I dispositivi Surface sono progettati per ottenere esperienze ottimali in scenari di produttività e per scopi generali. Gli aggiornamenti regolari consentono ai dispositivi Surface di apportare nuove innovazioni e di evolversi con le nuove funzionalità fornite dagli aggiornamenti delle funzionalità di Windows 10. Gli aggiornamenti delle caratteristiche sono disponibili solo nelle edizioni di Windows 10 Pro o Windows 10 Enterprise che ricevono aggiornamenti continui tramite il canale semestrale (SAC).

A differenza dell'opzione manutenzione SAC, nota in precedenza come le opzioni di manutenzione di Branch (CB) o Current Branch for business (CBB), non è possibile selezionare l'opzione LTSC (Long-Term Servicing Channel) nelle impostazioni di Windows 10. Per usare l'opzione di manutenzione LTSC, è necessario installare una versione separata di Windows 10 Enterprise, nota come Windows 10 Enterprise LTSC, in precedenza noto come Windows 10 Enterprise LTSB (filiale di manutenzione a lungo termine. Oltre a fornire un modello di manutenzione estesa, Windows 10 Enterprise LTSC Edition offre anche un ambiente con diversi componenti di Windows rimossi. Le esperienze di superficie principali interessate da LTSC includono:

* Aggiornamenti delle funzionalità di Windows, inclusi miglioramenti, ad esempio:

  *  Miglioramenti per l'input penna e il rifiuto della palma forniti in Windows 10, versione 1607 (detta anche aggiornamento dell'anniversario)
  *  Supporto migliorato per le applicazioni High DPI fornite in Windows 10, versione 1703 (nota anche come aggiornamento per i creatori)

* Impostazioni di sensibilità alla pressione fornite dall'app Surface

* Area di lavoro di Windows Ink

* Principali applicazioni in-box ottimizzate per il tocco, tra cui Microsoft Edge, OneNote, calendario e fotocamera

L'uso dell'ambiente Windows 10 Enterprise LTSC per i dispositivi Surface consente di ottenere esperienze utente finali subottimali ed evitare di usarlo in ambienti in cui gli utenti vogliono e si aspettano un'esperienza utente Premium e aggiornata.

L'opzione di manutenzione LTSC è progettata per i tipi di dispositivo e gli scenari in cui l'attributo Key è per le caratteristiche o le funzionalità che non cambiano mai. Gli esempi includono sistemi che producono energia o apparecchiature medicali o sistemi incorporati nei chioschi, come i bancomat o i sistemi di ticketing aeroportuali.

>[!NOTE]
>Per informazioni generali sui rami di manutenzione di Windows, incluso LTSC, vedere [Panoramica di Windows come servizio](https://technet.microsoft.com/itpro/windows/update/waas-overview#long-term-servicing-branch).

Come guida generale, i dispositivi che soddisfano i criteri seguenti sono considerati dispositivi di uso generale e devono essere associati a Windows 10 Pro o Windows 10 Enterprise usando l'opzione di manutenzione del canale semestrale:

* Dispositivi che eseguono software di produttività, ad esempio Microsoft Office

* Dispositivi che usano le applicazioni di Microsoft Store

* Dispositivi usati per la navigazione Internet generale, ad esempio ricerca o accesso a social media

Prima di scegliere di usare Windows 10 Enterprise LTSC Edition su dispositivi Surface, prendere in considerazione le limitazioni seguenti:

* I driver e gli aggiornamenti del firmware non vengono testati in modo esplicito rispetto alle versioni di Windows 10 Enterprise LTSC.

* Se si verificano problemi, il supporto tecnico Microsoft fornirà assistenza per la risoluzione dei problemi. Tuttavia, a causa della natura di manutenzione di Windows LTSC, la risoluzione dei problemi può richiedere che i dispositivi vengano aggiornati a una versione più recente di Windows 10 Enterprise LTSC o a Windows 10 Pro o Enterprise con l'opzione di manutenzione SAC.

* Le sostituzioni di dispositivi di superficie, ad esempio i dispositivi sostituiti in garanzia, potrebbero contenere piccole variazioni nei componenti hardware che richiedono il firmware e i driver di dispositivo aggiornati. La compatibilità con questi aggiornamenti può richiedere l'installazione di una versione più recente di Windows 10 Enterprise LTSC o Windows 10 Pro o Enterprise con l'opzione di manutenzione SAC.

>[!NOTE]
>Le organizzazioni che si uniformano in una specifica versione di Windows 10 Enterprise LTSC potrebbero non essere in grado di adottare nuove generazioni di hardware di superficie, ad esempio Surface Pro 7, Surface Pro X o Surface laptop 3, senza anche eseguire l'aggiornamento a una versione successiva di Windows 10 Enterprise LTSC o Windows 10 Pro o Enterprise. Per altre informazioni, vedere **come sarà supportato Windows 10 LTSBs?** argomento relativo al **supporto delle domande frequenti sui processori e i chipset nella sezione Windows** dei criteri del ciclo di vita [-prodotti Windows](https://support.microsoft.com/help/18581/lifecycle-policy-faq-windows-products#b4).

I dispositivi Surface che usano Windows 10 Enterprise LTSC Edition non riceveranno nuove funzionalità. In molti casi queste funzionalità sono richieste dai clienti per migliorare l'usabilità e le funzionalità dell'hardware di Surface. Ad esempio, nuovi miglioramenti per le applicazioni ad alta risoluzione DPI in Windows 10, versione 1703. I clienti che usano i dispositivi Surface nella configurazione di LTSC non vedranno i miglioramenti finché non vengono aggiornati in una nuova versione di LTSC Enterprise di Windows 10 o non vengono aggiornati in Windows 10 con il supporto per l'opzione di manutenzione SAC.

I dispositivi possono essere modificati da Windows 10 Enterprise LTSC a una versione più recente di Windows 10 Enterprise, con il supporto per l'opzione di manutenzione SAC, senza la perdita di dati utente eseguendo un'installazione di aggiornamento. È anche possibile eseguire un'installazione di aggiornamento su più dispositivi sfruttando i modelli di sequenza delle attività di aggiornamento disponibili in Microsoft Deployment Toolkit (MDT) e Microsoft endpoint Configuration Manager. Per altre informazioni, vedere [aggiornare i dispositivi Surface a Windows 10 con Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/surface/upgrade-surface-devices-to-windows-10-with-mdt).

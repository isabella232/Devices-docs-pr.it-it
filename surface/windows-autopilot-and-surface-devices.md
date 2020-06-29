---
title: Windows Autopilot e dispositivi Surface
ms.reviewer: ''
manager: laurawi
description: Informazioni sulle opzioni di distribuzione di Windows Autopilot per i dispositivi Surface.
keywords: Autopilot, Windows 10, Surface, Deployment
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: ea5920649a4a29841b102de73c88187440968910
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832481"
---
# Windows Autopilot e dispositivi Surface

Windows Autopilot è una tecnologia di distribuzione basata sul cloud in Windows 10. Puoi usare Windows Autopilot per distribuire e configurare in remoto i dispositivi in un processo a tocco zero direttamente dalla casella.

Windows Autopilot-i dispositivi registrati vengono identificati tramite Internet all'avvio iniziale tramite una firma di dispositivo univoca denominata *hash hardware*. Vengono automaticamente registrati e configurati con le moderne soluzioni di gestione, ad esempio Azure Active Directory (Azure AD) e gestione di dispositivi mobili.

È possibile registrare i dispositivi Surface al momento dell'acquisto da un partner Surface abilitato per Windows Autopilot. Questi partner possono spedire nuovi dispositivi direttamente agli utenti. I dispositivi verranno automaticamente registrati e configurati quando vengono attivati per la prima volta. Questo processo Elimina la riimaging durante la distribuzione, che consente di implementare nuovi metodi agili di gestione e distribuzione dei dispositivi.

## Gestione moderna

Autopilot è l'opzione di distribuzione consigliata per i dispositivi Surface, tra cui Surface Pro 7, Surface laptop 3 e Surface Pro X, progettato specificamente per la distribuzione tramite Autopilot.

 È consigliabile registrare i dispositivi Surface con l'aiuto di un provider di soluzioni cloud Microsoft. Questo passaggio consente di gestire le impostazioni del firmware UEFI in Surface direttamente da Intune. Elimina la necessità di toccare fisicamente i dispositivi per la gestione dei certificati. Per informazioni dettagliate, vedere [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md) .

## Considerazioni sulla versione di Windows

La distribuzione estensiva di dispositivi Surface tramite il pilota automatico Windows, inclusa la registrazione per partner di Surface al momento dell'acquisto, richiede Windows 10 versione 1709 (Update per i creatori di cadute) o versioni successive.

Queste versioni di Windows supportano un valore hash di 4.000 byte (4K) che identifica in modo univoco i dispositivi per il pilota automatico di Windows, che è necessario per le distribuzioni in scala. Tutti i nuovi dispositivi Surface, tra cui Surface Pro 7, Surface Pro X e Surface laptop 3, vengono forniti con Windows 10 versione 1903 o successiva.

## Esperienza di Exchange su dispositivi Surface che necessitano di riparazioni o sostituzioni

Microsoft controlla automaticamente ogni superficie per la registrazione automatica e deregistrerà il dispositivo dal tenant del cliente.  Microsoft assicura che il dispositivo sostitutivo sia registrato in Windows Autopilot una volta che un sostituto viene spedito al cliente. Questo servizio è disponibile in tutti gli ordini di servizio di Exchange per dispositivi direttamente con Microsoft.

> [!NOTE]
> Quando i clienti usano un partner per restituire dispositivi, il partner è responsabile della gestione del processo di Exchange, tra cui la registrazione e l'iscrizione dei dispositivi in Windows Autopilot.

## Partner di Surface abilitato per il pilota automatico di Windows

Selezionare Surface partner può registrare i dispositivi Surface in Windows Autopilot per l'utente al momento dell'acquisto. Possono anche spedire i dispositivi registrati direttamente agli utenti. I dispositivi possono essere configurati interamente tramite un processo di zero-tocco usando il pilota automatico di Windows, Azure AD e gestione di dispositivi mobili.

I partner di Surface abilitati per Windows Autopilot includono:

| Partner degli Stati Uniti | Partner globali | Distributori degli Stati Uniti |
|--------------|---------------|-------------------|
| * [CDW](https://www.cdw.com/) | * [ANCHE](https://www.also.com/ec/cms5/de_1010/1010_anbieter/microsoft/windows-autopilot/index.jsp) | * [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)  |
| * [Connessione](https://www.connection.com/brand/microsoft/microsoft-surface)   | * [ATEA](https://www.atea.com/) | * [TechData](https://www.techdata.com/)  |
| * [Rappresentazione](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)  | * [Bechtle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot) | * [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)   |
| * [SHI](https://www.shi.com/Surface) | * [Cancom](https://www.cancom.de/) |    |
| * [LDI Connect](https://www.myldi.com/managed-it/)  | * [Computacenter](https://www.computacenter.com/uk) |    |
| * [F1](https://www.functiononeit.com/#empower)  |   |  |
| * [Attendibilità protetta](https://go.microsoft.com/fwlink/p/?LinkID=2129005) | | | 

## Scopri di più

Per altre informazioni su Windows Autopilot, vedere:
- [Panoramica di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot)
- [Requisiti di Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot-requirements)
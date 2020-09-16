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
ms.date: 9/14/2020
ms.openlocfilehash: d2a948d236ffa286192937cc5ca71099b6eeeafb
ms.sourcegitcommit: c2df79cab0e59e9d7ea6640e5899531b57cd383f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/16/2020
ms.locfileid: "11016425"
---
# Windows Autopilot e dispositivi Surface

Windows Autopilot è una tecnologia di distribuzione basata sul cloud in Windows 10. Puoi usare Windows Autopilot per distribuire e configurare in remoto i dispositivi in un processo a tocco zero direttamente dalla casella.

Tradizionalmente i professionisti IT spendono molto tempo per la creazione e la personalizzazione di immagini che verranno poi distribuite in dispositivi già dotati di un sistema operativo perfettamente valido. Windows Autopilot introduce un nuovo approccio per la distribuzione a zero tocco usando una raccolta di tecnologie per configurare i dispositivi Windows. Questo consente a un reparto IT di configurare/personalizzare le immagini con poca o nessuna infrastruttura da gestire e un processo facile e semplice. Dal punto di vista dell'utente, bastano pochi semplici passaggi per ottenere la superficie in uno stato produttivo. Infatti, l'unica interazione richiesta dall'utente finale consiste nel connettersi a una rete e verificare le proprie credenziali. Tutto ciò che è stato completato automaticamente.

Windows Autopilot consente di:

- Aggiungere automaticamente dispositivi ad Azure Active Directory (Azure AD).
- Registrare automaticamente i dispositivi in Servizi MDM, ad esempio Microsoft Intune (richiede un abbonamento a Azure AD Premium).
- Limitare la creazione di account amministratore. Il pilota automatico è l'unico modo per avere la prima persona che accede a Windows ENTER come utente standard.
- Creare e assegnare automaticamente dispositivi ai gruppi di configurazione in base ai profili di dispositivo.
- Personalizzare il contenuto e il branding del file OOBE per soddisfare i requisiti dell'organizzazione.
- Abilitare la configurazione completa del dispositivo con Intune.
- Reimpostare o riavviare i dispositivi in remoto.

## Come funziona

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

## Registrazione del supporto Microsoft

I clienti e i provider di soluzioni cloud Microsoft (CSP) hanno la possibilità di registrare i dispositivi Surface inviando richieste al supporto Microsoft. Per altre informazioni, vedere [supporto per la registrazione della superficie per Windows Autopilot](surface-autopilot-registration-support.md).

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
- [Supporto per la registrazione superficiale per Windows Autopilot](surface-autopilot-registration-support.md)
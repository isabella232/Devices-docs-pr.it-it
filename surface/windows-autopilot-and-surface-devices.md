---
title: Windows Autopilot e dispositivi Surface
ms.reviewer: ''
manager: laurawi
description: Informazioni sulle opzioni Windows distribuzione di Autopilot per i dispositivi Surface.
keywords: autopilot, windows 10, surface, distribuzione
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
ms.openlocfilehash: 6cf2996ab9348bcc778a4b334d82e52b2eebdcde
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676600"
---
# <a name="windows-autopilot-and-surface-devices"></a>Windows Autopilot e dispositivi Surface

Windows Autopilot è una tecnologia di distribuzione basata su cloud in Windows 10. Puoi usare Windows Autopilot per distribuire e configurare i dispositivi in remoto in un processo a tocco zero.

Tradizionalmente, i professionisti IT dedicano molto tempo alla creazione e alla personalizzazione di immagini che verranno successivamente distribuite nei dispositivi già disponibili con un sistema operativo perfettamente buono già installato su di essi. Windows Autopilot introduce un nuovo approccio alla distribuzione zero touch usando una raccolta di tecnologie per configurare e configurare Windows dispositivi. In questo modo un reparto IT può configurare/personalizzare le immagini con poca o nessuna infrastruttura da gestire e un processo semplice e semplice. Dal punto di vista dell'utente, bastano pochi semplici passaggi per ottenere Surface in uno stato produttivo. Infatti, l'unica interazione richiesta dall'utente finale è la connessione a una rete e la verifica delle credenziali. Tutto ciò che si verifica dopo è completamente automatizzato.

Windows Autopilot consente di:

- Aggiungere automaticamente i dispositivi Azure Active Directory (Azure AD).
- Registrare automaticamente i dispositivi nei servizi MDM, ad esempio Microsoft Intune (richiede una Azure AD Premium abbonamento).
- Limitare la creazione di account amministratore. Autopilot è l'unico modo per fare in modo che la prima persona che accede Windows immettere come utente standard.
- Creare e assegnare automaticamente i dispositivi ai gruppi di configurazione in base ai profili dei dispositivi.
- Personalizzare il contenuto e la personalizzazione della Configurazione fuori rete per soddisfare i requisiti dell'organizzazione.
- Abilitare la configurazione completa del dispositivo con Intune.
- Reimpostare o riavviare i dispositivi in remoto.

## <a name="how-it-works"></a>Come funziona

Windows I dispositivi registrati automaticamente vengono identificati tramite Internet al primo avvio tramite una firma univoca del dispositivo denominata *hash hardware.* Vengono registrati e configurati automaticamente usando soluzioni di gestione moderne come Azure Active Directory (Azure AD) e la gestione dei dispositivi mobili.

Puoi registrare i dispositivi Surface al momento dell'acquisto da un partner Surface abilitato per Windows Autopilot. Questi partner possono spedire nuovi dispositivi direttamente agli utenti. I dispositivi verranno registrati e configurati automaticamente quando vengono attivati per la prima volta. Questo processo elimina la reimaging durante la distribuzione, che ti consente di implementare nuovi metodi agili di gestione e distribuzione dei dispositivi.

## <a name="modern-management"></a>Gestione moderna

Autopilot è l'opzione di distribuzione consigliata per i dispositivi Surface, tra cui Surface Pro 7+, Surface Laptop 3, Surface Pro 7 e Surface Pro X, progettata specificamente per la distribuzione tramite Autopilot.

 È meglio registrare i dispositivi Surface con l'aiuto di un Microsoft Cloud Solution Provider. Questo passaggio consente di gestire le impostazioni del firmware UEFI su Surface direttamente da Intune. Elimina la necessità di toccare fisicamente i dispositivi per la gestione dei certificati. Per [informazioni dettagliate, vedi Gestione di Intune delle impostazioni UEFI di Surface.](surface-manage-dfci-guide.md)

## <a name="windows-version-considerations"></a>Windows sulla versione

L'ampia distribuzione di dispositivi Surface tramite Windows Autopilot, inclusa la registrazione da parte dei partner surface al momento dell'acquisto, richiede Windows 10 versione 1709 (Fall Creators Update) o versione successiva.

Queste versioni Windows supportano un valore hash di 4.000 byte (4k) che identifica in modo univoco i dispositivi per Windows Autopilot, che è necessario per le distribuzioni su larga scala. Tutti i nuovi dispositivi Surface, inclusi Surface Pro 7+, Surface Pro X e Surface Laptop 3 vengono forniti con Windows 10 versione 1903 o successiva.

## <a name="exchange-experience-on-surface-devices-in-need-of-repair-or-replacement"></a>Exchange nei dispositivi Surface che necessitano di riparazione o sostituzione

Microsoft controlla automaticamente ogni surface per la registrazione autopilot e annulla la registrazione del dispositivo dal tenant del cliente.  Microsoft garantisce che il dispositivo sostitutivo sia registrato Windows Autopilot una volta che una sostituzione viene spedita al cliente. Questo servizio è disponibile in tutti gli ordini di assistenza per lo scambio di dispositivi direttamente con Microsoft.

> [!NOTE]
> Quando i clienti usano un partner per restituire i dispositivi, il partner è responsabile della gestione del processo di scambio, inclusa la annullamento della registrazione e la registrazione dei dispositivi Windows Autopilot.

## <a name="microsoft-support-registration"></a>Registrazione del Supporto Tecnico Microsoft

I clienti e i provider di soluzioni cloud Microsoft hanno la possibilità di registrare i dispositivi Surface inviando richieste al supporto tecnico Microsoft. Per altre informazioni, vedi [Surface Registration Support for Windows Autopilot.](surface-autopilot-registration-support.md)

## <a name="surface-partners-enabled-for-windows-autopilot"></a>Partner surface abilitati per Windows Autopilot

I partner di Surface selezionati possono registrare i dispositivi Surface Windows Autopilot automaticamente al momento dell'acquisto. Possono anche spedire i dispositivi registrati direttamente agli utenti. I dispositivi possono essere configurati interamente tramite un processo zero-touch usando Windows Autopilot, Azure AD e la gestione dei dispositivi mobili.

I partner Surface abilitati per Windows Autopilot includono:

| Partner statunitensi | Partner globali | Distributori statunitensi |
|--------------|---------------|-------------------|
|  [CDW](https://www.cdw.com/) |  [ANCHE](https://www.also.com/ec/cms5/da_2800/2800-msportal/products-and-solutions/surface/surface-is-more/surface-and-wa/index.jsp) |  [Synnex](https://www.synnexcorp.com/us/microsoft/surface-autopilot/)  |
|  [Connessione](https://www.connection.com/brand/microsoft/microsoft-surface)   |  [ATEA](https://www.atea.com/) |  [Techdata](https://www.techdata.com/)  |
|  [Informazioni dettagliate](https://www.insight.com/en_US/buy/partner/microsoft/surface/windows-autopilot.html)  |  [Bechtle](https://www.bechtle.com/marken/microsoft/microsoft-windows-autopilot) |  [Ingram](https://go.microsoft.com/fwlink/p/?LinkID=2128954)   |
|  [SHI](https://www.shi.com/Surface) |  [Cancom](https://www.cancom.de/) |    |
|  [LDI Connessione](https://www.myldi.com/managed-it/)  |  [Computacenter](https://www.computacenter.com/uk) |    |
|  [F1](https://www.functiononeit.com/#empower)  |   |  |
|  [Trust protetto](https://go.microsoft.com/fwlink/p/?LinkID=2129005) | | |

## <a name="learn-more"></a>Altre informazioni

Per ulteriori informazioni su Windows Autopilot, vedere:

- [Panoramica di Windows Autopilot](/windows/deployment/windows-autopilot/windows-10-autopilot)
- [Requisiti di Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot-requirements)
- [Supporto alla registrazione di Surface per Windows Autopilot](surface-autopilot-registration-support.md)

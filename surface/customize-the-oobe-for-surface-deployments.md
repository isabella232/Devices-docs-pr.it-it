---
title: Personalizzare Configurazione guidata per le distribuzioni (Surface)
description: Questo articolo descrive in modo dettagliato la personalizzazione della Configurazione guidata di Surface per gli utenti finali nella tua organizzazione.
ms.assetid: F6910315-9FA9-4297-8FA8-2C284A4B1D87
ms.reviewer: ''
manager: laurawi
keywords: distribuire, personalizzare, automatizzare, rete, penna, accoppiare, avviare
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 97cc262d803875a76427d04c8f9b70547152f895
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833267"
---
# Personalizzare la Configurazione guidata per le distribuzioni di Surface

Questo articolo descrive la personalizzazione dell'esperienza di out-of-box in superficie per gli utenti finali dell'organizzazione.

In una distribuzione Windows è prassi comune personalizzare l'esperienza utente per il primo avvio dei computer distribuiti, ovvero la Configurazione guidata.

>[!NOTE]
>La Configurazione guidata viene usata spesso anche per descrivere la fase, o passaggio di configurazione, dell'installazione di Windows durante la quale viene visualizzata l'esperienza utente. Per altre informazioni sulla fase di installazione della Configurazione guidata, vedi [Funzionamento dei passaggi di configurazione](https://msdn.microsoft.com/library/windows/hardware/dn898581.aspx).

In alcuni scenari potresti voler fornire automazione completa per garantire che alla fine di una distribuzione i computer siano pronti per l'uso senza alcuna interazione da parte dell'utente. In altri scenari potresti voler permettere agli utenti di eseguire le azioni necessarie o selezionare quella desiderata tra diverse opzioni importanti riguardo agli elementi principali dell'esperienza. Per gli amministratori che eseguono la distribuzione in dispositivi Surface, ognuno di questi scenari costituisce una sfida unica da affrontare.

> [!NOTE]
> Questo articolo non si applica a Surface Pro X. Per altre informazioni, vedere [distribuzione, gestione e manutenzione di Surface Pro X](surface-pro-arm-app-management.md)

Questo articolo contiene un riepilogo degli scenari in cui una distribuzione potrebbe richiedere passaggi aggiuntivi. Sono inoltre disponibili le informazioni necessarie per garantire la realizzazione dell'esperienza desiderata su qualsiasi nuovo dispositivo Surface distribuito. Questo articolo è destinato agli amministratori che hanno familiarità con il processo di distribuzione, nonché con concetti come i file di risposte e le [immagini di riferimento](https://technet.microsoft.com/itpro/windows/deploy/create-a-windows-10-reference-image).

>[!NOTE]
>Anche se la fase di configurazione del programma di installazione viene ancora eseguita durante una distribuzione con una soluzione di distribuzione automatica, ad esempio [Microsoft Deployment Toolkit (MDT)](https://go.microsoft.com/fwlink/p/?LinkId=618117) o Microsoft endpoint Configuration Manager (OSD), viene automatizzato dalle impostazioni fornite nella procedura guidata di distribuzione e nella sequenza di attività. Per altre informazioni, vedi:<br/>
>- [Distribuire Windows 10 con Microsoft Deployment Toolkit](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-the-microsoft-deployment-toolkit)
>- [Distribuire Windows 10 con System Center 2012 R2 Configuration Manager](https://technet.microsoft.com/itpro/windows/deploy/deploy-windows-10-with-system-center-2012-r2-configuration-manager)

 

##  <a name="scenario-1:-wireless-networking-in-oobe-with-mdt-2013"></a>Scenario 1: rete wireless nella Configurazione guidata con MDT 2013


Quando una scheda di rete wireless è presente durante la Configurazione guidata, viene visualizzata la pagina **Connessione a rete wireless**, che chiede a un utente di connettersi a una rete wireless. Questa pagina non viene automaticamente nascosta dalle tecnologie di distribuzione, incluso MDT 2013, e di conseguenza verrà visualizzata anche quando una distribuzione è configurata per l'automazione completa.

Per evitare che una distribuzione automatica venga arrestata da questa pagina, la pagina deve essere nascosta configurando un'altra impostazione nel file di risposte, ovvero **HideWirelessSetupInOOBE**. Puoi trovare informazioni aggiuntive sull'impostazione **HideWirelessSetupInOOBE** in [Guida di riferimento all'installazione automatica di Windows](https://technet.microsoft.com/library/ff716213.aspx).

##  <a name="scenario-2:-surface-pen-pairing-in-oobe"></a>Scenario 2: associazione della Penna per Surface nella Configurazione guidata


Quando estrai un dispositivo Surface Pro 3, Surface Pro 4, Surface Book o Surface Studio dalla confezione per la prima volta e lo avvii, il completamento dell'installazione dell'immagine produttore computer include un prompt che ti chiede di associare al dispositivo la Penna per Surface inclusa. Questo prompt viene fornito solo dall'immagine produttore computer inclusa con il dispositivo e non è compreso in altre immagini usate per la distribuzione, come i supporti di installazione di Windows Enterprise scaricati dal Centro servizi per contratti multilicenza. Poiché l'associazione della Penna per Surface Bluetooth al di fuori di questa esperienza richiede l'uso del Pannello di controllo o della funzionalità Impostazioni PC e l'associazione manuale di un dispositivo Bluetooth, potresti voler fare in modo che gli utenti o un tecnico usino questo prompt per eseguire l'operazione di associazione.

Per fornire l'esperienza di associazione della Penna per Surface del produttore computer nella Configurazione guidata, devi copiare quattro file dall'immagine produttore computer di Surface all'immagine di riferimento. Puoi copiare questi file nell'ambiente di riferimento prima di acquisire l'immagine di riferimento oppure puoi aggiungerli in un secondo momento usando Gestione e manutenzione immagini distribuzione per montare l'immagine. I quattro file necessari sono:

-   %windir%\\system32\\oobe\\info\\default\\1033\\oobe.xml
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenPairing\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenError\_en-US.png
-   %windir%\\system32\\oobe\\info\\default\\1033\\PenSuccess\_en-US.png

>[!NOTE]
>Devi copiare i file da un'immagine produttore computer per il dispositivo Surface dello stesso modello in cui intendi eseguire la distribuzione. Ad esempio, dovresti usare i file di Surface Pro 7 per eseguire la distribuzione in Surface Pro 7 e i file di Surface Book 2 per distribuire Surface Book 2, ma non usare i file di Surface Pro 7 per distribuire Surface Book o Surface Pro 6.

 

Il processo dettagliato per l'aggiunta di questi file necessari a un'immagine viene descritto nella pagina dei [suggerimenti per la distribuzione della Penna per Surface Pro 3 e OneNote](https://blogs.technet.microsoft.com/askcore/2014/07/15/deploying-surface-pro-3-pen-and-onenote-tips/). Questo post di blog contiene anche alcuni suggerimenti per garantire l'installazione degli aggiornamenti per l'esperienza di creazione rapida delle note con la Penna per Surface, che permette agli utenti di inviare note a OneNote con un solo clic.

 

 






---
title: Schede Ethernet e distribuzione di Surface (Surface)
description: Questo articolo contiene le linee guida e le risposte utili per aiutarti a eseguire una distribuzione di rete nei dispositivi Surface.
ms.assetid: 5273C59E-6039-4E50-96B3-426BB38A64C0
ms.reviewer: ''
manager: laurawi
keywords: ethernet, distribuire, rimovibile, rete, connettività, avvio, firmware, dispositivo, scheda, avvio PXE, USB
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.audience: itpro
ms.openlocfilehash: 0eb0eb1e1d73852a2131c5aa5d6a7731ce78d54f
ms.sourcegitcommit: 6d531906c36da51cb4032a220d70182e686114a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2021
ms.locfileid: "11721256"
---
# <a name="ethernet-adapters-and-surface-deployment"></a>Schede Ethernet e distribuzione di Surface

Questo articolo fornisce indicazioni per eseguire una distribuzione di rete dei dispositivi Surface più recenti Surface Pro 3 e versioni successive.

La distribuzione di rete nei dispositivi Surface può porre alcune sfide complesse agli amministratori di sistema. A causa dell'assenza di una scheda di rete Ethernet cablata nativa, gli amministratori devono fornire la connettività tramite una scheda Ethernet rimovibile.

## <a name="select-an-ethernet-adapter-for-surface-devices"></a>Selezionare una scheda Ethernet per dispositivi Surface

Prima di affrontare le problematiche correlate a come avviare l'ambiente di distribuzione o al modo in cui i dispositivi verranno riconosciuti dalla soluzione di distribuzione, devi usare una scheda di rete cablata.

L'aspetto principale di cui tenere conto quando selezioni una scheda Ethernet è il modo in cui sarà in grado di avviare il dispositivo Surface dalla rete. Se stai pre-gestione temporanea dei client con servizi di distribuzione di Windows (WDS) o se stai usando Microsoft Endpoint Configuration Manager, puoi anche valutare se le schede Ethernet rimovibili saranno dedicate a un dispositivo Surface specifico o condivise tra più dispositivi. Per ulteriori informazioni sui potenziali conflitti con schede condivise, vedere Gestire indirizzi MAC con schede [Ethernet](#manage-mac-addresses) rimovibili più avanti in questo articolo.

L'avvio dalla rete (avvio PXE) è supportato solo quando usi una scheda Ethernet o un alloggiamento di espansione Microsoft. Per eseguire l'avvio dalla rete, il chipset nella scheda Ethernet o nel dock deve essere rilevato e configurato come dispositivo di avvio nel firmware del dispositivo Surface. Le schede Ethernet Microsoft, come la scheda Ethernet Surface e il [dock Surface](https://www.microsoft.com/surface/accessories/surface-dock) usano un chipset compatibile con il firmware per Surface.

I dispositivi Ethernet seguenti sono supportati per l'avvio di rete con i dispositivi Surface:

- Surface USB-C to Ethernet and USB 3.0 Adapter
- Scheda Ethernet da Surface USB 3.0 a Gigabit
- Surface Dock
- Surface Dock 2
- Alloggiamento di espansione per Surface 3
- Alloggiamento di espansione per Surface Pro 3
- Alloggiamento di espansione per Surface Pro e Surface Pro 2

Sono supportate anche le schede Ethernet di terze parti per la distribuzione di rete, ma queste non supportano l'avvio PXE. Per usare una scheda Ethernet di terze parti, devi caricare i driver nell'immagine di avvio di distribuzione e avviare questa immagine di avvio da un dispositivo di archiviazione separato, come una chiavetta USB.

## <a name="boot-surface-devices-from-the-network"></a>Avviare dispositivi Surface dalla rete

Per eseguire l'avvio dalla rete o da una chiavetta USB collegata, devi indicare al dispositivo Surface che l'avvio deve avvenire da un dispositivo di avvio alternativo. Puoi modificare l'ordine di avvio nel firmware del sistema per classificare in ordine di priorità i dispositivi di avvio USB oppure puoi indicare al firmware di eseguire l'avvio da un dispositivo di avvio alternativo durante il processo di avvio stesso.

Per avviare un dispositivo Surface da un dispositivo di avvio alternativo:

1. Assicurati che il dispositivo Surface sia spento.
2. Tieni premuto il pulsante di **abbassamento del volume**.
3. Premi e rilascia il pulsante di **alimentazione**.
4. Dopo che il sistema inizia l'avvio dalla chiavetta USB o dalla scheda Ethernet, rilascia il pulsante di **abbassamento del volume**.

>[!NOTE]
>Oltre a una scheda Ethernet, al dispositivo Surface deve essere collegata una tastiera per accedere all'ambiente di preinstallazione ed esplorare la distribuzione guidata.

Per Windows 10 versione 1511 e successive, incluso Windows Assessment and Deployment Kit (Windows ADK) per Windows 10 versione 1511, i driver per le schede Ethernet Microsoft Surface sono presenti per impostazione predefinita. Se usi una soluzione di distribuzione che usa Ambiente preinstallazione di Windows (WinPE), come Microsoft Deployment Toolkit e l'avvio dalla rete con PXE, verifica che la soluzione di distribuzione usi la versione più recente di Windows ADK.

## <a name="manage-mac-addresses-with-removable-ethernet-adapters"></a><a href="" id="manage-mac-addresses"></a>Gestire gli indirizzi MAC con schede Ethernet rimovibili

Un'altra considerazione di cui devono tenere conto gli amministratori che eseguono una distribuzione di Windows in rete riguarda come identificare i computer quando si usa la stessa scheda Ethernet per una distribuzione in più computer. Un identificatore comune usato dalle tecnologie di distribuzione è l'indirizzo MAC (Media Access Control) associato a ogni scheda Ethernet. Tuttavia, quando usi la stessa scheda Ethernet per la distribuzione in più computer, non puoi usare una tecnologia di distribuzione che controlla gli indirizzi MAC, perché non è possibile distinguere l'indirizzo MAC della scheda rimovibile quando viene usata con computer diversi.

La soluzione più semplice per evitare conflitti tra gli indirizzi MAC consiste nel fornire una scheda Ethernet rimovibile dedicata per ogni dispositivo Surface. Questa è la prassi più sensata in molti scenari in cui la scheda Ethernet o la funzionalità aggiuntiva dell'alloggiamento di espansione verrà usata regolarmente. Tuttavia, non tutti gli scenari sono adatti alla connettività aggiuntiva di un alloggiamento di espansione o al supporto per reti cablate.

Un'altra possibile soluzione per evitare conflitti nel caso di schede condivise consiste nell'usare [Microsoft Deployment Toolkit (MDT)](/mem/configmgr/mdt) per eseguire la distribuzione in dispositivi Surface. Poiché MDT non usa l'indirizzo MAC per identificare i singoli computer, non è soggetto a questa limitazione. Tuttavia, MDT usa Servizi di distribuzione Windows per fornire la funzionalità di avvio PXE ed è soggetto alle limitazioni correlate ai client pre-installazione, descritte più avanti in questa sezione.

Quando usi una scheda condivisa per la distribuzione, la soluzione per le tecnologie di distribuzione interessate consiste nel ricorrere ad altri metodi per identificare i sistemi univoci. Per Configuration Manager e Servizi di distribuzione Windows, che possono essere entrambi soggetti a questo problema, la soluzione consiste nell'usare l'UUID (Universal Unique Identifier) di sistema integrato nel firmware del computer dal produttore del computer. Per i dispositivi Surface, puoi osservare questa voce nel firmware del computer all'interno di **Device Information**.

Per accedere al firmware di un dispositivo Surface:

1. Assicurati che il dispositivo Surface sia spento.
2. Tieni premuto il pulsante di **aumento del volume**.
3. Premi e rilascia il pulsante di **alimentazione**.
4. Dopo che il dispositivo inizia l'avvio, rilascia il pulsante di **aumento del volume**.

Se esegui la distribuzione con Servizi di distribuzione Windows, l'indirizzo MAC viene usato solo per identificare un computer quando il server di distribuzione è configurato per rispondere solo a client pre-installazione noti. Durante la pre-installazione di un client, un amministratore crea un account computer in Active Directory e definisce il computer tramite l'indirizzo MAC o l'UUID di sistema. Per evitare conflitti di identità causati da schede Ethernet condivise, devi usare l'[UUID di sistema per definire client pre-installazione](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742034(v=ws.11)). In alternativa, puoi configurare Servizi di distribuzione Windows per rispondere a client sconosciuti che non richiedono la definizione tramite indirizzo MAC o UUID di sistema selezionando l'opzione **Rispondi a tutti i computer client (conosciuti e sconosciuti)** nella scheda [**Risposta PXE** ](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732360(v=ws.11))nelle proprietà di **Server di distribuzione Windows**.

Il rischio di conflitti con schede Ethernet condivise aumenta notevolmente con Configuration Manager. Mentre Servizi di distribuzione Windows usa gli indirizzi MAC per definire singoli sistemi solo quando è configurato a questo scopo, Configuration Manager usa l'indirizzo MAC per definire singoli sistemi ogni volta che esegue una distribuzione in computer nuovi o sconosciuti. Questo comportamento può produrre dispositivi configurati non correttamente o addirittura l'impossibilità di distribuire più di un sistema con una scheda Ethernet condivisa. Esistono diverse possibili soluzioni per questa situazione descritte in dettaglio in [How to Use The Same External Ethernet Adapter for Multiple SCCM OSD](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374), in un post di blog sul Blog sull'infrastruttura e la sicurezza di base.

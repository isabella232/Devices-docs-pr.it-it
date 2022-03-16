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
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: ec73d437d2784ffbceb350f38507524e761df8dd
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448479"
---
# <a name="ethernet-adapters-and-surface-deployment"></a>Schede Ethernet e distribuzione di Surface

Questo articolo descrive come eseguire una distribuzione di rete dei dispositivi Surface più recenti, tra cui Surface Pro 3 e versioni successive.

La distribuzione di rete nei dispositivi Surface può porre alcune sfide complesse agli amministratori di sistema. A causa dell'assenza di una scheda di rete Ethernet cablata nativa, gli amministratori devono fornire la connettività tramite una scheda Ethernet rimovibile.

## <a name="select-an-ethernet-adapter-for-surface-devices"></a>Selezionare una scheda Ethernet per dispositivi Surface

Prima di affrontare le problematiche correlate a come avviare l'ambiente di distribuzione o al modo in cui i dispositivi verranno riconosciuti dalla soluzione di distribuzione, devi usare una scheda di rete cablata.

Quando selezioni le schede Ethernet, il problema principale è come le schede avviano i dispositivi Surface dalla rete. Si supponga di essere client di pre-gestione temporanea con Windows Deployment Services (WDS) o usando Microsoft Endpoint Configuration Manager. In tal caso, potresti anche decidere se le schede Ethernet rimovibili saranno dedicate a un dispositivo Surface specifico o condivise tra più dispositivi. Per ulteriori informazioni sui potenziali conflitti con schede condivise, vedere [Gestire indirizzi MAC con schede Ethernet rimovibili](#manage-mac-addresses) più avanti in questo articolo.

L'avvio dalla rete (avvio PXE) è supportato solo quando si utilizza una scheda Ethernet o un alloggiamento di espansione da Microsoft. Il chipset nella scheda Ethernet o nel dock deve essere rilevato e configurato come dispositivo di avvio nel firmware del dispositivo Surface. Le schede Ethernet Microsoft, ad esempio surface Ethernet Adapter e [Surface Dock](https://www.microsoft.com/surface/accessories/surface-dock), usano un chipset compatibile con il firmware surface.

I dispositivi Ethernet seguenti sono supportati per l'avvio di rete con i dispositivi Surface:

- Surface USB-C to Ethernet and USB 3.0 Adapter
- Adattatore Ethernet da Surface USB 3.0 a Gigabit
- Microsoft USB-C Travel Hub
- Surface Dock
- Surface Dock 2
- Docking Station per Surface 3
- Docking Station per Surface Pro 3 
- Alloggiamento di espansione per Surface Pro e Surface Pro 2

Sono supportate anche le schede Ethernet di terze parti per la distribuzione di rete, ma queste non supportano l'avvio PXE. Per usare una scheda Ethernet di terze parti, devi caricare i driver nell'immagine di avvio della distribuzione e avviare l'immagine di avvio da un dispositivo di archiviazione separato, ad esempio una chiavetta USB.

## <a name="boot-surface-devices-from-the-network"></a>Avviare dispositivi Surface dalla rete

Per eseguire l'avvio dalla rete o da una chiavetta USB collegata, devi indicare al dispositivo Surface che l'avvio deve avvenire da un dispositivo di avvio alternativo. Puoi modificare l'ordine di avvio nel firmware di sistema per definire la priorità dei dispositivi di avvio USB o l'avvio da un dispositivo di avvio alternativo durante il processo di avvio.

**Per eseguire l'avvio da un dispositivo di avvio alternativo:**

1. Assicurati che il dispositivo Surface sia spento.
2. Tieni premuto il pulsante di **abbassamento del volume**.
3. Premi e rilascia il pulsante di **alimentazione**.
4. Dopo che il sistema inizia l'avvio dalla chiavetta USB o dalla scheda Ethernet, rilascia il pulsante di **abbassamento del volume**.

>[!NOTE]
>Oltre a una scheda Ethernet, al dispositivo Surface deve essere collegata una tastiera per accedere all'ambiente di preinstallazione ed esplorare la distribuzione guidata.

Per Windows 10 versione 1511 e successive, incluso Windows Assessment and Deployment Kit (Windows ADK) per Windows 10 versione 1511, i driver per le schede Ethernet Microsoft Surface sono presenti per impostazione predefinita. Se si utilizza una soluzione di distribuzione che utilizza Windows Preinstallation Environment (WinPE), ad esempio Microsoft Deployment Toolkit e l'avvio dalla rete con PXE, verificare che la soluzione di distribuzione utilizzi la versione più recente di Windows ADK.

## <a name="manage-mac-addresses-with-removable-ethernet-adapters"></a><a href="" id="manage-mac-addresses"></a>Gestire gli indirizzi MAC con schede Ethernet rimovibili

Un'altra considerazione per gli amministratori Windows la distribuzione in rete è l'identificazione dei computer quando si utilizza la stessa scheda Ethernet per la distribuzione in più computer. Un identificatore comune utilizzato dalle tecnologie di distribuzione è l'indirizzo MAC (Media Access Control) associato a ogni scheda Ethernet. Tuttavia, quando si utilizza la stessa scheda Ethernet per la distribuzione in più computer, non è possibile utilizzare una tecnologia di distribuzione che ispeziona gli indirizzi MAC perché non esiste alcun modo per distinguere l'indirizzo MAC della scheda rimovibile se utilizzato in computer diversi.

La soluzione più semplice per evitare conflitti tra gli indirizzi MAC consiste nel fornire una scheda Ethernet rimovibile dedicata per ogni dispositivo Surface. Questa è la prassi più sensata in molti scenari in cui la scheda Ethernet o la funzionalità aggiuntiva dell'alloggiamento di espansione verrà usata regolarmente. Tuttavia, non tutti gli scenari sono adatti alla connettività aggiuntiva di un alloggiamento di espansione o al supporto per reti cablate.

Un'altra possibile soluzione per evitare conflitti nel caso di schede condivise consiste nell'usare [Microsoft Deployment Toolkit (MDT)](/mem/configmgr/mdt) per eseguire la distribuzione in dispositivi Surface. Poiché MDT non usa l'indirizzo MAC per identificare i singoli computer, non è soggetto a questa limitazione. Tuttavia, MDT usa i servizi di distribuzione di Windows per fornire funzionalità di avvio PXE ed è soggetto alle limitazioni relative ai client pre-fasi, come descritto più avanti in questa sezione.

Quando usi una scheda condivisa per la distribuzione, la soluzione per le tecnologie di distribuzione interessate consiste nel ricorrere ad altri metodi per identificare i sistemi univoci. Per Configuration Manager e WdS, che possono essere entrambi interessati da questo problema, la soluzione consiste nell'usare l'identificatore univoco universale di sistema (UUID) incorporato nel firmware del computer dal produttore del computer. Per i dispositivi Surface, puoi osservare questa voce nel firmware del computer all'interno di **Device Information**.

**Per accedere al firmware di un dispositivo Surface:**

1. Assicurati che il dispositivo Surface sia spento.
2. Tieni premuto il pulsante di **aumento del volume**.
3. Premi e rilascia il pulsante di **alimentazione**.
4. Dopo l'avvio del computer, rilascia il **pulsante Volume su** .

Se esegui la distribuzione con Servizi di distribuzione Windows, l'indirizzo MAC viene usato solo per identificare un computer quando il server di distribuzione è configurato per rispondere solo a client pre-installazione noti. Durante la pre-installazione di un client, un amministratore crea un account computer in Active Directory e definisce il computer tramite l'indirizzo MAC o l'UUID di sistema. Per evitare conflitti di identità causati da schede Ethernet condivise, devi usare l'[UUID di sistema per definire client pre-installazione](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc742034(v=ws.11)). 

In alternativa, è possibile configurare WDS per rispondere a client sconosciuti che non richiedono la definizione tramite l'indirizzo MAC o l'UUID di sistema. Selezionare **l'opzione Rispondi a tutti i computer client (** noti e sconosciuti) nella scheda [**Risposta PXE**](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732360(v=ws.11)) Windows **proprietà del server di distribuzione**.

Il rischio di conflitti con schede Ethernet condivise aumenta notevolmente con Configuration Manager. Se WDS usa solo indirizzi MAC per definire singoli sistemi, Configuration Manager usa l'indirizzo MAC per definire sistemi separati ogni volta che viene distribuita in computer nuovi o sconosciuti. Questo comportamento può produrre dispositivi configurati non correttamente o addirittura l'impossibilità di distribuire più di un sistema con una scheda Ethernet condivisa. Diverse possibili soluzioni per questa situazione sono descritte in dettaglio in Come utilizzare la stessa scheda [Ethernet esterna per più OSD SCCM](https://techcommunity.microsoft.com/t5/core-infrastructure-and-security/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm/ba-p/257374).

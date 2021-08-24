---
title: Proteggere e gestire Surface Hub 2S con SEMM
description: Altre informazioni sulla protezione di Surface Hub 2S con SEMM.
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
ms.openlocfilehash: b22bfc39c07facb84ca57438ec16038492f85d15
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911041"
---
# <a name="secure-and-manage-surface-hub-2s-with-semm-and-uefi"></a>Proteggere e gestire Surface Hub 2S con SEMM e UEFI

Novità di Surface Hub 2S, puoi usare SEMM per gestire l'impostazione UEFI del dispositivo.
Usa il configuratore UEFI di Microsoft Surface per controllare i componenti seguenti:

- LAN cablata
- Fotocamere
- Bluetooth
- Wi-Fi
- Sensore di presenza

Usa il configuratore UEFI di Microsoft Surface per attivare o disattivare le impostazioni UEFI seguenti:

- Avvio

    - Avvio di IPv6 per PXE
    - Avvio alternativo
    - Blocco ordine di avvio
    - Avvio da USB
- Pagina iniziale UEFI

    - Dispositivi
    - Avvio
    - Data/ora

## <a name="create-uefi-configuration-image"></a>Creare un'immagine di configurazione UEFI

A differenza di altri dispositivi Surface, non puoi usare un file MSI o un'immagine Win PE per applicare queste impostazioni Surface Hub 2S. Devi invece creare un'immagine USB da caricare nel dispositivo. Per creare un'immagine di configurazione UEFI Surface Hub 2S, scarica e installa la versione più recente del configuratore UEFI di Microsoft Surface dalla pagina [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft. Per altre informazioni sull'uso di UEFI e SEMM, vedi [Microsoft Surface Enterprise Management Mode.](https://docs.microsoft.com/surface/surface-enterprise-management-mode)

## <a name="to-configure-uefi-on-surface-hub-2s"></a>Per configurare UEFI in Surface Hub 2S

1. Avvia configuratore UEFI e nella prima schermata scegli **Pacchetto di configurazione.**<br><br>
![* Avviare il configuratore UEFI e scegliere Pacchetto di configurazione*.](images/sh2-uefi1.png) <br> <br>
2. Per aggiungere il certificato al pacchetto, è necessario disporre di un certificato valido con la chiave privata in un formato di file pfx per firmare e proteggere il pacchetto. Selezionare **+ Protezione certificato.** <br>
![* Selezionare + Protezione certificato *.](images/sh2-uefi2.png) <br><br>
3. Immettere la password della chiave privata del certificato.<br>
![* Immettere la password della chiave privata del certificato *.](images/sh2-uefi3.png) <br><br>
4. Dopo aver importato la chiave privata, continua a creare il pacchetto.<br>
![* Continuare a creare il pacchetto *.](images/sh2-uefi4.png) <br><br>
5. Scegli **Hub** e **Surface Hub 2S** come destinazione per il pacchetto di configurazione UEFI.<br>
![* Scegliere Hub e Surface Hub 2S come destinazione per il pacchetto di configurazione UEFI *.](images/sh2-uefi5.png) <br><br>
6. Scegli i componenti e le impostazioni che vuoi attivare o disattivare Surface Hub 2S.<br>
![* Scegliere i componenti e le impostazioni che si desidera attivare o disattivare *.](images/sh2-uefi6.png) <br><br>
7. Usa l'opzione USB per esportare il file.<br>
![* Usare l'opzione USB per esportare il file *.](images/sh2-uefi8.png) <br><br>
8. Inserisci e scegli l'unità USB che vuoi usare per questo pacchetto. L'unità USB verrà formattata e si perderanno le informazioni in esso contenute.<br>
![* Inserire e scegliere l'unità USB per il pacchetto *.](images/sh2-uefi9.png) <br><br>
9. Dopo la creazione corretta del pacchetto, il configuratore visualizza gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri sono necessari quando si esegue l'importazione nella configurazione Surface Hub 2S.<br>
![* Configurazione corretta del pacchetto *.](images/sh2-uefi10.png) <br>

## <a name="to-boot-into-uefi"></a>Per eseguire l'avvio in UEFI

Disattivare Surface Hub 2S. Tieni premuto il **pulsante Volume su** e premi il pulsante **di** alimentazione. Tieni premuto il pulsante Volume su fino a quando non viene visualizzato il menu UEFI.

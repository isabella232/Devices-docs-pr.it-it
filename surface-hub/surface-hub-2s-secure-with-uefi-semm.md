---
title: Proteggere e gestire Surface Hub 2S con SEMM
description: Leggi altre informazioni su come proteggere Surface Hub 2S con SEMM.
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
ms.openlocfilehash: 03ce1dfa48ade8aade545c63818ca5ae8947e6b7
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832972"
---
# Proteggere e gestire Surface Hub 2S con SEMM e UEFI

Nuovo in Surface Hub 2S, è possibile usare SEMM per gestire l'impostazione UEFI del dispositivo.
Usare Microsoft Surface UEFI Configurator per controllare i componenti seguenti:

- LAN cablata
- Fotocamere
- Bluetooth
- Wi-Fi
- Sensore di presenza

Usare Microsoft Surface UEFI Configurator per attivare o disattivare le impostazioni UEFI seguenti:

- Avvio

    - Avvio di IPv6 per PXE
    - Avvio alternativo
    - Blocco ordine di avvio
    - Avvio da USB
- Prima pagina UEFI

    - Dispositivi
    - Avvio
    - Data/ora

## Creare un'immagine di configurazione UEFI

Diversamente da altri dispositivi Surface, non è possibile usare un file MSI o un'immagine PE Win per applicare queste impostazioni su Surface Hub 2S. Devi invece creare un'immagine USB per caricarla nel dispositivo. Per creare un'immagine di configurazione UEFI di Surface Hub 2S, scaricare e installare la versione più recente di Microsoft Surface UEFI Configurator dalla pagina [strumenti Surface per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft. Per altre informazioni sull'uso di UEFI e SEMM, vedere [modalità di gestione di Microsoft Surface Enterprise](https://docs.microsoft.com/surface/surface-enterprise-management-mode).

## Per configurare UEFI su Surface Hub 2S

1. Avviare il configuratore UEFI e nella prima schermata scegliere **pacchetto di configurazione**.<br><br>
![* Avviare il configuratore UEFI e scegliere il pacchetto di configurazione *](images/sh2-uefi1.png) <br> <br>
2. Per aggiungere il certificato al pacchetto, è necessario disporre di un certificato valido con la chiave privata in un formato di file PFX per firmare e proteggere il pacchetto. Selezionare **+ protezione certificato.** <br>
![* Selezionare + protezione certificato *](images/sh2-uefi2.png) <br><br>
3. Immettere la password della chiave privata del certificato.<br>
![* Immettere la password della chiave privata del certificato *](images/sh2-uefi3.png) <br><br>
4. Dopo aver importato la chiave privata, continuare a creare il pacchetto.<br>
![* Continuare a creare il pacchetto *](images/sh2-uefi4.png) <br><br>
5. Scegli **Hub** e **Surface Hub 2S** come destinazione per il pacchetto di configurazione UEFI.<br>
![* Scegliere hub e Surface Hub 2S come destinazione per il pacchetto di configurazione UEFI *](images/sh2-uefi5.png) <br><br>
6. Scegliere i componenti e le impostazioni che si desidera attivare o disattivare in Surface Hub 2S.<br>
![* Scegliere i componenti e le impostazioni che si desidera attivare o disattivare *](images/sh2-uefi6.png) <br><br>
7. Usare l'opzione USB per esportare il file.<br>
![* Usare l'opzione USB per esportare il file *](images/sh2-uefi8.png) <br><br>
8. Inserire e scegliere l'unità USB che si vuole usare per questo pacchetto. L'unità USB verrà formattata e si perdono tutte le informazioni personali.<br>
![* Inserire e scegliere l'unità USB per il pacchetto *](images/sh2-uefi9.png) <br><br>
9. Dopo aver completato la creazione del pacchetto, il configuratore visualizzerà gli ultimi due caratteri dell'identificazione personale del certificato. Questi caratteri sono necessari quando si importano nella configurazione in Surface Hub 2S.<br>
![* Configurazione corretta del pacchetto *](images/sh2-uefi10.png) <br>

## Per eseguire l'avvio in UEFI

Disattivare l'hub di Surface 2S. Premere e tenere premuto il pulsante **volume su** e premere il pulsante di **accensione** . Tenere premuto il pulsante volume su finché non viene visualizzato il menu UEFI.

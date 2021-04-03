---
title: Implementare la qualità del servizio in Surface Hub
ms.reviewer: ''
manager: laurawi
description: Scopri come configurare QoS in Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/25/2021
ms.localizationpriority: medium
ms.openlocfilehash: 32d7493dc4a76b8e7642b927ec5db41a1e697b2a
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470484"
---
# <a name="implement-quality-of-service-qos-on-surface-hub"></a>Implementare la qualità del servizio (QoS) in Surface Hub

Quality of Service (QoS) è una combinazione di tecnologie di rete che consente agli amministratori di ottimizzare l'esperienza delle comunicazioni audio/video e di condivisione delle applicazioni in tempo reale.
 
La configurazione [di QoS per Skype for Business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) su Surface Hub può essere eseguita usando il provider di gestione dei dispositivi mobili [(MDM)](manage-settings-with-mdm-for-surface-hub.md) o tramite un [pacchetto di provisioning.](provisioning-packages-for-surface-hub.md) 
 
 
Questa procedura spiega come configurare QoS per Surface Hub con Microsoft Intune. 

1. In Intune crea [un criterio personalizzato.](https://docs.microsoft.com/intune/custom-settings-configure)

    > [!div class="mx-imgBorder"]
    > ![Screenshot della finestra di dialogo per la creazione di criteri personalizzati in Intune](images/qos-create.png)

2. In **Impostazioni URI OMA personalizzate**seleziona **Aggiungi.** Per ogni impostazione aggiunta, verranno immessi un nome, una descrizione (facoltativa), un tipo di dati, un URI OMA e un valore.

    > [!div class="mx-imgBorder"]
    > ![Screenshot di una finestra di dialogo di impostazione URI OMA vuota](images/qos-setting.png)

3. Aggiungi le impostazioni URI OMA personalizzate seguenti:<br/><br/>

    Nome | Tipo di dati | URI OMA<br>./Device/Vendor/MSFT/NetworkQoSPolicy |  Value
    --- | --- | --- | ---
    Porta origine audio | Stringa |  /HubAudio/SourcePortMatchCondition  |   Ottenere i valori dall'amministratore di Skype
    DSCP audio | Numero intero |  /HubAudio/DSCPAction  |   46
    Porta origine video | Stringa |  /HubVideo/SourcePortMatchCondition   |  Ottenere i valori dall'amministratore di Skype
    DSCP video | Numero intero |  /HubVideo/DSCPAction   |   34
    Nome processo audio | Stringa |  /HubAudio/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe
    Nome processo video | Stringa |  /HubVideo/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe

    >[!IMPORTANT]
    >Ogni **percorso URI OMA** inizia con `./Device/Vendor/MSFT/NetworkQoSPolicy` . Il percorso completo per l'impostazione della porta di origine audio, ad esempio, sarà `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` .

4. Quando il criterio è stato creato, distribuiscilo in Surface Hub.


>[!WARNING]
>Attualmente, non è possibile configurare **l'impostazione IPProtocolMatchCondition** nel [CSP NetworkQoSPolicy.](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) Se questa impostazione è configurata, il criterio non verrà applicato.
 

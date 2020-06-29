---
title: Implementare la qualità del servizio in Surface Hub
ms.reviewer: ''
manager: laurawi
description: Informazioni su come configurare QoS su Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 99172e77be260559c770f5fc8a1438734bed660f
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832912"
---
# Implementare la qualità del servizio (QoS) in Surface Hub

La qualità del servizio (QoS) è una combinazione di tecnologie di rete che consente agli amministratori di ottimizzare l'esperienza delle comunicazioni in tempo reale audio/video e condivisione applicazioni.
 
La configurazione [di QoS per Skype for business](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp) nell'hub Surface può essere eseguita usando il [provider di gestione di dispositivi mobili (MDM)](manage-settings-with-mdm-for-surface-hub.md) o tramite un pacchetto di [provisioning](provisioning-packages-for-surface-hub.md). 
 
 
Questa procedura spiega come configurare QoS per Surface Hub con Microsoft Intune. 

1. In Intune [creare criteri personalizzati](https://docs.microsoft.com/intune/custom-settings-configure).

    ![Screenshot della finestra di dialogo Creazione di criteri personalizzati in Intune](images/qos-create.png)

2. In **impostazioni di URI OMA personalizzate**selezionare **Aggiungi**. Per ogni impostazione aggiunta, si immetterà un nome, una descrizione (facoltativo), un tipo di dati, un URI OMA e un valore.

    ![Schermata di una finestra di dialogo di impostazione di URI OMA vuota](images/qos-setting.png)

3. Aggiungere le impostazioni di URI OMA personalizzate seguenti:

    Nome | Tipo di dati | URI OMA<br>./Device/Vendor/MSFT/NetworkQoSPolicy |  Value
    --- | --- | --- | ---
    Porta di origine audio | String |  /HubAudio/SourcePortMatchCondition  |   Ottenere i valori dall'amministratore Skype
    DSCP audio | Integer |  /HubAudio/DSCPAction  |   46
    Porta di origine video | String |  /HubVideo/SourcePortMatchCondition   |  Ottenere i valori dall'amministratore Skype
    DSCP video | Integer |  /HubVideo/DSCPAction   |   34
    Nome processo audio | String |  /HubAudio/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe
    Nome processo video | String |  /HubVideo/AppPathNameMatchCondition  |   Microsoft.PPISkype.Windows.exe

    >[!IMPORTANT]
    >Ogni percorso con **URI OMA** inizia con `./Device/Vendor/MSFT/NetworkQoSPolicy` . Il percorso completo per l'impostazione della porta di origine audio, ad esempio, sarà `./Device/Vendor/MSFT/NetworkQoSPolicy/HubAudio/SourcePortMatchCondition` .




4. Quando il criterio è stato creato, [distribuirlo nell'hub Surface.](manage-settings-with-mdm-for-surface-hub.md#manage-surface-hub-settings-with-mdm)


>[!WARNING]
>Attualmente non è possibile configurare l'impostazione **IPProtocolMatchCondition** nel [CSP NetworkQoSPolicy](https://docs.microsoft.com/windows/client-management/mdm/networkqospolicy-csp). Se questa impostazione è configurata, il criterio non verrà applicato.
 

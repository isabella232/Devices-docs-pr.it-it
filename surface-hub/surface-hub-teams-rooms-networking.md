---
title: Configurare la rete e la qualità del servizio per Microsoft Teams room in Surface Hub
description: In questo articolo vengono illustrati i requisiti e i suggerimenti per la rete e la qualità del servizio per ottimizzare Microsoft Teams Rooms in Surface Hub.
keywords: Teams Rooms, Surface Hub, Intune, QoS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 08/20/2021
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: d06a69d89d94839c3a9616a29ff1be12badec76e
ms.sourcegitcommit: b5e7ea8118b848846cf1fb332ed7bf96c4583d20
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2021
ms.locfileid: "11910003"
---
# <a name="configure-networking-and-quality-of-service-for-microsoft-teams-rooms-on-surface-hub"></a>Configurare la rete e la qualità del servizio Microsoft Teams Rooms in Surface Hub

In questo articolo viene illustrato come preparare l'ambiente per ottimizzare Microsoft Teams Rooms in Surface Hub.

## <a name="create-and-test-a-device-account"></a>Creare e testare un account del dispositivo

Un account del dispositivo è un account utilizzato dal client Microsoft Teams Rooms per accedere alle funzionalità da Exchange, ad esempio il calendario, e per abilitare Skype for Business. [Vedi Creare e testare un account del dispositivo](create-and-test-a-device-account-surface-hub.md)

## <a name="check-network-availability"></a>Verificare la disponibilità della rete

> [!TIP]
> È consigliabile usare le procedure per la configurazione di rete elencate Microsoft 365 [principi di connettività di rete](https://aka.ms/pnc)

Teams Rooms in Surface Hub deve avere accesso a una rete che soddisfi questi requisiti:

- Accesso all'istanza di Active Directory o Azure Active Directory (Azure AD)
- Accesso a un server in grado di fornire un indirizzo IP tramite DHCP. Microsoft Teams Rooms in Surface Hub non può essere configurato con un indirizzo IP statico.
- Accesso alle porte HTTP 80 e 443.
- Le porte TCP e UDP configurate come descritto in Port and protocol requirements for [Microsoft 365 and Office 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges) for Microsoft Teams.

> [!IMPORTANT]
> Microsoft Teams Rooms non supporta l'autenticazione proxy in quanto può interferire con le normali operazioni di Teams. Assicurati che Surface Hub dispositivi o Microsoft 365 endpoint del servizio siano stati esentati dall'autenticazione proxy prima di entrare in produzione con Teams Rooms in Surface Hub.

## <a name="implement-quality-of-service-qos-on-surface-hub"></a>Implementare la qualità del servizio (QoS) in Surface Hub

Quality of Service (QoS) è una combinazione di tecnologie di rete che consente agli amministratori di ottimizzare l'esperienza delle comunicazioni audio/video e di condivisione delle applicazioni in tempo reale.
La configurazione di QoS per Microsoft Teams sul Surface Hub può essere eseguita usando il provider di gestione dei dispositivi mobili [(MDM)](manage-settings-with-mdm-for-surface-hub.md) o tramite un [pacchetto di provisioning.](provisioning-packages-for-surface-hub.md)

Per configurare QoS per Surface Hub tramite Microsoft Intune:

1. In Intune crea [un criterio personalizzato.](/intune/custom-settings-configure)

2. In **Custom OMA-URI Impostazioni**selezionare **Add**. Per ogni impostazione aggiunta, immettere un nome, una descrizione (facoltativa), un tipo di dati, un URI OMA e un valore.

3. Per garantire una qualità audio e video ottimale Surface Hub, aggiungi le impostazioni QoS seguenti al dispositivo.

    | Nome                  | Descrizione           | URI OMA                                                                        | Tipo    | Value       |
    | --------------------- | --------------------- | ------------------------------------------------------------------------------ | ------- | ----------- |
    | **Porte audio**       | Intervallo porte audio      | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/SourcePortMatchCondition      | String  | 50000-50019 |
    | **DSCP audio**        | Contrassegno porte audio   | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsAudio/DSCPAction                    | Integer | 46          |
    | **Porta video**        | Intervallo porte video      | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/SourcePortMatchCondition      | String  | 50020-50039 |
    | **DSCP video**        | Contrassegno porte video   | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsVideo/DSCPAction                    | Integer | 34          |
    | **Porta di condivisione**      | Intervallo porte di condivisione    | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/SourcePortMatchCondition    | Stringa  | 50040-50059 |
    | **Condivisione di DSCP**      | Contrassegno delle porte di condivisione | ./Device/Vendor/MSFT/NetworkQoSPolicy/TeamsSharing/DSCPAction                  | Numero intero | 18          |

4. Una volta creato il criterio, distribuirlo Surface Hub.

## <a name="learn-more"></a>Scopri di più

- [Implementare la qualità del servizio (QoS) in Microsoft Teams](/microsoftteams/qos-in-teams)

---
title: Prepara l'ambiente per Surface Hub 2S
description: Scopri cosa devi fare per preparare l'ambiente per Surface Hub 2S.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 2/26/2021
ms.localizationpriority: Medium
ms.openlocfilehash: caa6372820222f6f2f225f028161b3441b147a82
ms.sourcegitcommit: 7e1b351024e33926901ddbdc562ba12aea0b4196
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "11385144"
---
# <a name="prepare-your-environment-for-surface-hub-2s"></a>Prepara l'ambiente per Surface Hub 2S

## <a name="office-365-readiness"></a>Preparazione di Office 365

Se usi Exchange Online, Skype for Business online, Microsoft Teams o Microsoft Whiteboard e intendi gestire Surface Hub 2S con Intune, esamina innanzitutto i requisiti di [Office 365](https://docs.microsoft.com/office365/enterprise/office-365-endpoints)per gli endpoint.

Gli endpoint di Office 365 consentono di ottimizzare la rete inviando tutte le richieste di rete attendibili di Office 365 direttamente attraverso il firewall, ignorando tutte le ulteriori ispezioni o elaborazioni a livello di pacchetto. Questa funzionalità consente di ridurre la latenza e i requisiti di capacità perimetrale.

Microsoft aggiorna regolarmente il servizio Office 365 con nuove caratteristiche e funzionalità, che possono alterare le porte, gli URL e gli indirizzi IP necessari. Per valutare, configurare e rimanere aggiornati con le modifiche, sottoscrivere il servizio Web url e indirizzo IP di [Office 365.](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service)

> [!NOTE]
> Surface Hub funziona con Microsoft Teams, Skype for Business Server 2019, Skype for Business Server 2015 o Skype for Business online.
Le piattaforme precedenti, ad esempio Lync Server 2013, non sono supportate. Surface Hub non è supportato in ambienti GCC-High o DoD.


## <a name="device-affiliation"></a>Affiliazione dei dispositivi

Usa l'affiliazione dei dispositivi per gestire l'accesso degli utenti all'app Impostazioni in Surface Hub 2S.
Con il sistema operativo Windows 10 Team (eseguito in Surface Hub 2S), solo gli utenti autorizzati possono modificare le impostazioni usando l'app Impostazioni. Poiché la scelta dell'affiliazione può influire sulla disponibilità delle funzionalità, pianificare in modo appropriato per garantire che gli utenti possano accedere alle funzionalità come previsto.

> [!NOTE]
> Puoi impostare l'affiliazione dei dispositivi solo durante la configurazione iniziale della Configurazione guidata. Se devi reimpostare l'affiliazione del dispositivo, dovrai ripetere l'installazione della Configurazione guidata.

## <a name="no-affiliation"></a>Nessuna affiliazione

Nessuna affiliazione è come avere Surface Hub 2S in un gruppo di lavoro con un account amministratore locale diverso in ogni Surface Hub 2S. Se scegli Nessuna affiliazione, devi salvare localmente la chiave [BitLocker in un'unità usb usb.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq) Puoi comunque registrare il dispositivo con Intune; Tuttavia, solo l'amministratore locale può accedere all'app Impostazioni usando le credenziali dell'account configurate durante la Configurazione utente. Puoi modificare la password dell'account amministratore dall'app Impostazioni.

## <a name="active-directory-domain-services"></a>Active Directory Domain Services

Se consoci Surface Hub 2S con Servizi di dominio Active Directory locale, devi gestire l'accesso all'app Impostazioni usando un gruppo di sicurezza nel dominio. Ciò garantisce che tutti i membri del gruppo di sicurezza siano in grado di modificare le impostazioni in Surface Hub 2S. Tenere presente anche quanto segue:

- Quando Surface Hub 2S è affiliato a Servizi di dominio Active Directory locale, la chiave BitLocker può essere salvata nello schema di Active Directory. Per altre informazioni, vedi [Preparare l'organizzazione per BitLocker: pianificazione e criteri.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies)

- Le AUTORITÀ di certificazione radice attendibili dell'organizzazione vengono spinte nello stesso contenitore in Surface Hub 2S, il che significa che non è necessario importarle usando un pacchetto di provisioning.

- Puoi comunque registrare il dispositivo con Intune per gestire centralmente le impostazioni in Surface Hub 2S.

## <a name="azure-active-directory"></a>Azure Active Directory

Quando scegli di consociare Surface Hub 2S con Azure Active Directory (Azure AD), qualsiasi utente nel gruppo di sicurezza Global Admins può accedere all'app Impostazioni in Surface Hub 2S. Puoi anche configurare account di amministratore non globale che limitano le autorizzazioni alla gestione dell'app Impostazioni in Surface Hub 2S. In questo modo puoi impostare l'ambito delle autorizzazioni di amministratore solo per Surface Hub 2S e impedire l'accesso amministratore potenzialmente indesiderato in un intero dominio di Azure AD. 

Se hai abilitato la registrazione automatica di Intune per l'organizzazione, Surface Hub 2S si registrerà automaticamente con Intune. La chiave BitLocker del dispositivo viene salvata automaticamente in Azure AD. 

Per altre informazioni sulla gestione di Surface Hub con Azure AD, vedi: 

 - [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md)
 - [Configurare gli account diversi da amministratore globale in Surface Hub 2S](surface-hub-2s-nonglobal-admin.md)


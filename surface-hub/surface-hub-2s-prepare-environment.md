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
ms.date: 11/21/2019
ms.localizationpriority: Medium
ms.openlocfilehash: dddab2adce1bec9ff722a3324b9c4b1be609ae89
ms.sourcegitcommit: ac34f0ec1a9df74ea688bf0da2a51fadf5139a41
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/18/2020
ms.locfileid: "10934846"
---
# Prepara l'ambiente per Surface Hub 2S

## Disponibilità di Office 365

Se si usa Exchange Online, Skype for business online, Microsoft teams o Microsoft lavagna e si intende gestire Surface Hub 2S con Intune, vedere prima di tutto i [requisiti di Office 365 per gli endpoint](https://docs.microsoft.com/office365/enterprise/office-365-endpoints).

Gli endpoint di Office 365 consentono di ottimizzare la rete inviando tutte le richieste di rete di Office 365 attendibili direttamente attraverso il firewall, bypassando qualsiasi ulteriore controllo o elaborazione a livello di pacchetto. Questa funzionalità riduce la latenza e i requisiti della capacità perimetrale.

Microsoft aggiorna regolarmente il servizio Office 365 con nuove funzionalità e funzionalità, che possono modificare le porte, gli URL e gli indirizzi IP necessari. Per valutare, configurare e mantenere aggiornate le modifiche, sottoscrivere l' [indirizzo IP di Office 365 e il servizio Web URL](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

## Affiliazione dispositivi

USA affiliazione dispositivo per gestire l'accesso degli utenti all'app impostazioni in Surface Hub 2S.
Con il sistema operativo Windows 10 team (che viene eseguito su Surface Hub 2S), solo gli utenti autorizzati possono modificare le impostazioni usando l'app Impostazioni. Poiché la scelta dell'affiliazione può avere un impatto sulla disponibilità delle caratteristiche, pianificare in modo appropriato che gli utenti possano accedere alle funzionalità come previsto.

> [!NOTE]
> È possibile impostare l'affiliazione del dispositivo solo durante la configurazione dell'esperienza fuori sede (OOBE) iniziale. Se è necessario reimpostare l'affiliazione del dispositivo, è necessario ripetere la configurazione di OOBE.

## Nessuna affiliazione

Nessuna affiliazione è come avere un hub di Surface 2S in un gruppo di lavoro con un altro account di amministratore locale in ogni hub di Surface 2S. Se si sceglie nessuna affiliazione, è necessario salvare localmente la [chiave BitLocker in un'unità thumb USB](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-key-management-faq). È comunque possibile registrare il dispositivo con Intune; Tuttavia, solo l'amministratore locale può accedere all'app impostazioni usando le credenziali dell'account configurate durante la configurazione guidata. È possibile modificare la password dell'account di amministratore nell'app Impostazioni.

## Active Directory Domain Services

Se si affilia Surface Hub 2S con servizi di dominio Active Directory locale, è necessario gestire l'accesso all'app impostazioni usando un gruppo di sicurezza nel dominio. Questo consente di verificare che tutti i membri del gruppo di sicurezza dispongano delle autorizzazioni per modificare le impostazioni in Surface Hub 2S. Tenere inoltre presente quanto segue:

- Quando l'hub di Surface 2S è affiliato con i servizi di dominio Active Directory locale, la chiave BitLocker può essere salvata nello schema Active Directory. Per altre informazioni, vedere [preparare l'organizzazione per BitLocker: pianificazione e criteri](https://docs.microsoft.com/windows/security/information-protection/bitlocker/prepare-your-organization-for-bitlocker-planning-and-policies). 
- Le autorità di certificazione radice attendibili dell'organizzazione vengono inserite nello stesso contenitore di Surface Hub 2S, quindi non è necessario importarle usando un pacchetto di provisioning.
- È comunque possibile registrare il dispositivo con Intune per gestire in modo centralizzato le impostazioni di Surface Hub 2S.

## Azure Active Directory

Quando si sceglie di affiliare la superficie Hub 2S con Azure Active Directory (Azure AD), qualsiasi utente nel gruppo di sicurezza amministratori globali può accedere all'app impostazioni in Surface Hub 2S. Attualmente, nessun altro gruppo può essere delegato per accedere all'app impostazioni in Surface Hub 2S.

Se è stata abilitata la registrazione automatica di Intune per l'organizzazione, Surface Hub 2S si iscriverà automaticamente con Intune. La chiave BitLocker del dispositivo viene salvata automaticamente in Azure AD. Quando affiliante Surface Hub 2S con Azure AD, Single Sign-on e Easy Authentication non funzionerà.

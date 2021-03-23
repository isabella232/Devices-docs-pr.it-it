---
title: Gestione del gruppo amministratori
description: Tutti i dispositivi Microsoft Surface Hub possono essere configurati singolarmente aprendo l'app Impostazioni nel dispositivo.
ms.assetid: FA67209E-B355-4333-B903-482C4A3BDCCE
ms.reviewer: ''
manager: laurawi
keywords: gestione del gruppo amministratori, app Impostazioni, configurare Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 02/01/2021
ms.localizationpriority: medium
appliesto:
- Surface Hub
- Surface Hub 2S
ms.openlocfilehash: 217567ef310c4288a5073edd1313ce02a633568c
ms.sourcegitcommit: 6c362c5d5f67449f1adf4618847093eaf6ad087b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/22/2021
ms.locfileid: "11442850"
---
# <a name="admin-group-management-for-surface-hub"></a>Gestione dei gruppi di amministratori per Surface Hub


Tutti i dispositivi Surface Hub possono essere configurati localmente usando l'app Impostazioni nel dispositivo. Per impedire agli utenti non autorizzati di modificare le impostazioni, l'app Impostazioni richiede credenziali di amministratore per aprire l'app.


## <a name="admin-group-management"></a>Gestione del gruppo amministratori

Puoi configurare gli account amministratore per il dispositivo nei modi seguenti:

- [Creare un account amministratore locale](#create-a-local-admin-account)
- [Aggiunta del dominio del dispositivo ad Active Directory](#domain-join-the-device-to-active-directory)
- [Aggiunta di Azure AD al dispositivo](#azure-ad-join-the-device)
- [Configurare account di amministratore non globali nei dispositivi aggiunti ad Azure AD (Surface Hub 2S)](#configure-non-global-admin-accounts-on-azure-ad-joined-devices)


### <a name="create-a-local-admin-account"></a>Creare un account amministratore locale

Per creare un amministratore locale, [scegli di usare un amministratore locale durante la prima esecuzione](first-run-program-surface-hub.md#use-a-local-admin). In questo modo verrà creato un singolo account amministratore locale in Surface Hub con il nome utente e la password scelti da te. Usa queste credenziali per aprire l'app Impostazioni.

Tieni presente che le informazioni sull'account amministratore locale non sono supportate da alcun servizio directory. Ti consigliamo di scegliere un amministratore locale solo se il dispositivo non ha accesso ad Active Directory (AD) o ad Azure Active Directory (Azure AD). Se decidi di modificare la password dell'amministratore locale, puoi farlo in Impostazioni. Tuttavia, se vuoi passare dall'uso dell'account amministratore locale all'uso di un gruppo del dominio o del tenant di Azure AD, dovrai [reimpostare il dispositivo](device-reset-surface-hub.md) e rieseguire il programma di prima esecuzione.

### <a name="domain-join-the-device-to-active-directory"></a>Aggiunta del dominio del dispositivo ad Active Directory

Puoi aggiungere il dispositivo Surface Hub al dominio Active Directory per consentire agli utenti di uno specifico gruppo di sicurezza di configurare le impostazioni. Durante la prima esecuzione, scegli di usare [Servizi di dominio Active Directory](first-run-program-surface-hub.md#use-active-directory-domain-services). Dovrai fornire credenziali che consentono l'aggiunta al dominio di tua scelta, oltre al nome di un gruppo di sicurezza esistente. Chiunque appartenga al gruppo di sicurezza può immettere le proprie credenziali e sbloccare Impostazioni.

#### <a name="what-happens-when-you-domain-join-your-surface-hub"></a>Cosa accade quando aggiungi il dispositivo Surface Hub al dominio?
L'aggiunta al dominio dei dispositivi Surface Hub consente di:
- Concedere diritti amministrativi ai membri di uno specifico gruppo di sicurezza di AD.
- Eseguire il backup della chiave di ripristino di BitLocker del dispositivo archiviandola nell'oggetto computer in AD. Per altri dettagli, vedi [Salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md).
- Sincronizzare l'orologio di sistema con il controller di dominio per comunicazioni crittografate

Surface Hub non supporta l'applicazione di Criteri di gruppo o certificati dal controller di dominio.

> [!NOTE]
> Se il dispositivo Surface Hub perde il trust con il dominio (ad esempio, se rimuovi il dispositivo Surface Hub dal dominio dopo l'aggiunta al dominio), non potrai eseguire l'autenticazione nel dispositivo e aprire Impostazioni. Se decidi di rimuovere la relazione di trust di Surface Hub con il dominio, per prima cosa [reimposta il dispositivo](device-reset-surface-hub.md).


### <a name="azure-ad-join-the-device"></a>Aggiunta di Azure AD al dispositivo

Puoi azure Active Directory (Azure AD) per aggiungere Surface Hub per consentire ai professionisti IT del tenant di Azure AD di configurare le impostazioni. Durante la prima esecuzione, scegli di usare [Microsoft Azure Active Directory](first-run-program-surface-hub.md#use-microsoft-azure-active-directory). Dovrai fornire credenziali che consentono l'aggiunta al tenant di Azure AD di tua scelta. Una volta completata l'aggiunta ad Azure AD, alle persone indicate verranno concessi i diritti amministrativi per il dispositivo.

Per impostazione predefinita, tutti gli **amministratori globali** riceveranno i diritti amministrativi per un dispositivo Surface Hub aggiunto ad Azure AD. Con **Azure AD Premium** o **Enterprise Mobility Suite (EMS)**, puoi aggiungere altri amministratori:
1.  Nel [portale classico di Azure](https://manage.windowsazure.com/) fai clic su **Active Directory** e quindi sul nome della directory della tua organizzazione.
2.  Nella pagina **Configura**, in **Dispositivi** > **Amministratori aggiuntivi su dispositivi aggiunti ad Azure AD** fai clic su **Selezionati**.
3.  Fai clic su **Aggiungi** e seleziona gli utenti che vuoi aggiungere come amministratori nel tuo dispositivo Surface Hub e negli altri dispositivi aggiunti ad Azure AD.
4.  Al termine dell'operazione, fai clic sul pulsante del segno di spunta per salvare la modifica.

#### <a name="what-happens-when-you-azure-ad-join-your-surface-hub"></a>Cosa accade quando aggiungi il dispositivo Surface Hub ad Azure AD?
L'aggiunta ad Azure AD dei dispositivi Surface Hub consente di:
- Concedere diritti amministrativi agli utenti appropriati nel tenant di Azure AD.
- Eseguire il backup della chiave di ripristino di BitLocker del dispositivo archiviandola con l'account usato per aggiungere il dispositivo ad Azure AD. Per altri dettagli, vedi [Salvare la chiave BitLocker](save-bitlocker-key-surface-hub.md).

#### <a name="automatic-enrollment-via-azure-active-directory-join"></a>Registrazione automatica tramite l'aggiunta ad Azure Active Directory

Surface Hub ora supporta la possibilità di eseguire automaticamente la registrazione in Intune tramite l'aggiunta del dispositivo ad Azure Active Directory. 

Per altre informazioni, vedi Abilitare la registrazione automatica [di Windows 10.](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)

#### <a name="which-should-i-choose"></a>Quale opzione scegliere?

Se l'organizzazione usa AD o Azure AD, ti consigliamo di aggiungere il dispositivo al dominio o ad Azure AD, soprattutto per motivi di sicurezza. Gli utenti saranno in grado di eseguire l'autenticazione e sbloccare Impostazioni con le proprie credenziali e possono essere spostati all'interno o all'esterno dei gruppi di sicurezza associati al dominio.

| Opzione                                            | Requisiti                            | Quali credenziali possono essere usate per accedere all'app Impostazioni?  |
|---------------------------------------------------|-----------------------------------------|-------|
| Creare un account amministratore locale                      | Nessuno                                    | Il nome utente e la password specificati durante la prima esecuzione |
| Aggiungere il dispositivo a un dominio Active Directory (AD)              | L'organizzazione deve usare AD               | Qualsiasi utente AD di uno specifico gruppo di sicurezza del dominio |
| Aggiungere il dispositivo ad Azure Active Directory (Azure AD) | L'organizzazione deve usare Azure AD Basic   | Solo amministratori globali |
| &nbsp;                                            | L'organizzazione deve usare Azure AD Premium o Enterprise Mobility Suite (EMS) | Amministratori globali e amministratori aggiuntivi |


### <a name="configure-non-global-admin-accounts-on-azure-ad-joined-devices"></a>Configurare account di amministratore non globali nei dispositivi aggiunti ad Azure AD

Per i dispositivi Surface Hub v1 e Surface Hub 2S aggiunti ad Azure AD, Windows 10 Team 2020 Update consente di limitare le autorizzazioni di amministratore alla gestione dell'app Impostazioni in Surface Hub. In questo modo è possibile impostare l'ambito delle autorizzazioni di amministratore solo per Surface Hub e impedire l'accesso amministratore potenzialmente indesiderato a un intero dominio di Azure AD. Per altre informazioni, vedi [Configurare account di amministratore non globali in Surface Hub.](surface-hub-2s-nonglobal-admin.md)
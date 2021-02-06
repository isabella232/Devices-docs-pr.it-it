---
title: Preparare l'ambiente per Microsoft Surface Hub (V1)
description: Questa sezione contiene una panoramica dei passaggi necessari per preparare l'ambiente in modo da poter usare tutte le funzionalità di Microsoft Surface Hub.
ms.assetid: 336A206C-5893-413E-A270-61BFF3DF7DA9
ms.reviewer: ''
manager: laurawi
keywords: preparare l'ambiente, funzionalità di Surface Hub, creare e testare un account del dispositivo, verificare la disponibilità di rete
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 12/04/2017
ms.localizationpriority: medium
appliesto:
- Surface Hub
ms.openlocfilehash: 95b575e5213e3e11685b342cb2a7b77eb3e868a0
ms.sourcegitcommit: 7809222a51eb184f07d6b3ffbdd04a6272b247f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2021
ms.locfileid: "11314399"
---
# Preparare l'ambiente per Microsoft Surface Hub (V1)


Questa sezione contiene una panoramica delle dipendenze per l'installazione e del processo di installazione. Le info di questa sezione ti aiuteranno a preparare l'ambiente e a raccogliere le informazioni necessarie a configurare il tuo Surface Hub.


## Verificare le dipendenze per l'infrastruttura
Verifica queste dipendenze per assicurarti che le funzionalità di Surface Hub funzionino nella tua infrastruttura IT.

| Dipendenza        | Scopo           |
|-------------|------------------|
| Active Directory o Azure Active Directory (Azure AD) | <p>Surface Hub usa un account Active Directory o Azure AD (chiamato **account del dispositivo**) per accedere ai servizi di Exchange e di Skype for Business. Il dispositivo Surface Hub deve essere in grado di connettersi al controller di dominio Active Directory o al tenant di Azure AD per convalidare le credenziali dell'account del dispositivo, nonché per accedere a informazioni come il nome visualizzato dell'account del dispositivo, l'alias, il server Exchange e l'indirizzo SIP (Session Initiation Protocol).</p>Puoi anche aggiungere il tuo dispositivo Surface Hub a un dominio o ad Azure AD per consentire a un gruppo di utenti autorizzati di configurare le impostazioni sul dispositivo Surface Hub. |
| Exchange (Exchange 2013 o versioni successive oppure Exchange Online) ed Exchange ActiveSync | <p>Exchange viene usato per abilitare le funzionalità per e-mail e calendario, oltre a consentire agli utenti che usano il dispositivo di inviare convocazioni riunione al dispositivo Surface Hub, abilitando la partecipazione alla riunione con un solo tocco.</p>ActiveSync viene usato per sincronizzare il calendario e la posta dell'account del dispositivo in Surface Hub. Se il dispositivo non può usare ActiveSync, non visualizzerà le riunioni nella schermata iniziale e la partecipazione alle riunioni e l'invio delle lavagne tramite e-mail non saranno abilitati. |
| Skype for Business (Lync Server 2013 o versione successiva o Skype for Business Online)  | Skype for Business viene usato per varie funzionalità di conferenza, come videochiamate, messaggistica istantanea e condivisione dello schermo.|
| Soluzione di gestione di dispositivi mobili (MDM) (Microsoft Intune, Microsoft endpoint Configuration Manager o provider di MDM di terze parti supportato) | Se vuoi applicare le impostazioni e installare le app in remoto in più dispositivi alla volta, è necessario configurare una soluzione MDM e registrare il dispositivo in tale soluzione. Vedi [Gestire le impostazioni con un provider MDM](manage-settings-with-mdm-for-surface-hub.md) per i dettagli. |
| Microsoft Operations Management Suite (OMS)   | OMS viene usato per monitorare l'integrità dei dispositivi Surface Hub. Vedi [Monitorare il dispositivo Surface Hub](monitor-surface-hub.md) per i dettagli. |
| Rete e accesso a Internet   | Per funzionare correttamente, il dispositivo Surface Hub deve avere accesso a una rete wireless o cablata. In generale, è preferibile una connessione cablata. L'autenticazione 802.1X è supportata per le connessioni cablate e wireless.</br></br></br>**Autenticazione 802.1X:** in Windows 10, versione 1703, l'autenticazione 802.1X per le connessioni cablate e wireless è abilitata per impostazione predefinita in Surface Hub. Se l'organizzazione non usa l'autenticazione 802.1X, non è richiesta alcuna configurazione e Surface Hub continuerà a funzionare come di consueto. Se si utilizza l'autenticazione 802.1X, devi assicurarti che la certificazione di autenticazione sia installata nel dispositivo Surface Hub. Puoi recapitare il certificato per Surface Hub utilizzando il [CSP ClientCertificateInstall](https://msdn.microsoft.com/windows/hardware/commercialize/customize/mdm/clientcertificateinstall-csp) in MDM oppure puoi [creare un pacchetto di provisioning](provisioning-packages-for-surface-hub.md) e installarlo durante la prima esecuzione o tramite l'app Impostazioni. Dopo che il certificato viene applicato a Surface Hub, l'autenticazione 802.1X inizierà a funzionare automaticamente.</br>**Nota:** per altre informazioni su come abilitare l'autenticazione cablata 802.1X in Surface Hub, vedi [Abilitare l'autenticazione cablata 802.1x](enable-8021x-wired-authentication.md).</br></br>**IP dinamico:** il dispositivo Surface Hub non può essere configurato per l'uso di un indirizzo IP statico. È necessario usare DHCP per assegnare un indirizzo IP.</br></br>**Server proxy:** se la topologia richiede una connessione a un server proxy per raggiungere i servizi Internet, questo aspetto può essere configurato durante la prima esecuzione o in Impostazioni. Le credenziali del proxy vengono archiviate in più sessioni di Surface Hub ed è sufficiente impostarle una sola volta. |

È inoltre importante sapere che per Surface Hub le porte seguenti devono essere aperte:
- HTTPS: 443
- HTTP: 80
- NTP: 123

Se si usa Surface Hub con Skype for business, sarà necessario aprire porte aggiuntive. Seguire le indicazioni seguenti:
- Se si usa Skype for business online, vedere [URL IP e intervalli di indirizzi IP di Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US).
- Se si usa Skype for Business Server, vedere [Skype for Business Server: porte e protocolli per i server interni](https://docs.microsoft.com/SkypeForBusiness/plan-your-deployment/network-requirements/ports-and-protocols). 
- Se si usa un ibrido di Skype for business online e Skype for Business Server, è necessario aprire tutte le porte documentate da [URL IP di Office 365 e intervalli di indirizzi IP](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US) e [Skype for Business Server: porte e protocolli per i server interni](https://docs.microsoft.com/SkypeForBusiness/plan-your-deployment/network-requirements/ports-and-protocols?toc=/SkypeForBusiness/toc.json&bc=/SkypeForBusiness/breadcrumb/toc.json).

Microsoft raccoglie i dati di diagnostica per migliorare la tua esperienza con Surface Hub. Aggiungi questi siti all'elenco Consenti:
- Endpoint del client dati di diagnostica: `https://vortex.data.microsoft.com/`
- Endpoint impostazioni dei dati di diagnostica: `https://settings.data.microsoft.com/`

### Configurazione del proxy

Se l'organizzazione impedisce le connessioni a Internet dai computer della rete, esiste un set di URL che devono essere disponibili per i dispositivi per poter usare Microsoft Store per le aziende. Alcune delle funzionalità di Microsoft Store per le aziende usano app e servizi di Microsoft Store. I dispositivi che usano Store per le aziende, per acquisire, installare o aggiornare le app, dovranno avere accesso a questi URL. Se usi un server proxy per bloccare il traffico, la configurazione deve consentire questi URL:

- login.live.com
- login.windows.net
- account.live.com
- clientconfig.passport.net
- windowsphone.com
- *.wns.windows.com
- *.microsoft.com
- www.msftncsi.com (prima di Windows 10 versione 1607)
- www.msftconnecttest.com/connecttest.txt (sostituisce www.msftncsi.com a partire da Windows 10 versione 1607)


## Collaborare con altri amministratori

Surface Hub interagisce con alcuni prodotti e servizi diversi. A seconda delle dimensioni dell'organizzazione, è possibile che più persone supportino prodotti diversi nel tuo ambiente. Dovrai includere le persone che gestiscono Exchange, Active Directory (o Azure Active Directory), la gestione di dispositivi mobili (MDM) e le risorse di rete nella tua pianificazione e preparazione delle distribuzioni di Surface Hub. 


## Creare e verificare un account del dispositivo

Un account del dispositivo è un account della risorsa di Exchange che Surface Hub usa per visualizzare il calendario delle riunioni, partecipare alle chiamate di Skype for Business, inviare e-mail e (facoltativo) autenticarsi su Exchange. Per informazioni dettagliate, vedi [Creare e testare un account del dispositivo](create-and-test-a-device-account-surface-hub.md) .

Dopo aver creato l'account del dispositivo, per verificare che sia configurato correttamente, esegui gli script di PowerShell di convalida dell'account del dispositivo Surface Hub. Per altre informazioni, vedi [Script di PowerShell per Surface Hub](appendix-a-powershell-scripts-for-surface-hub.md) più avanti in questa guida. 

 

## Prepararsi per il programma di prima esecuzione 
Devi considerare ancora alcune cose prima di avviare il [programma di prima esecuzione](first-run-program-surface-hub.md).  

### Creare pacchetti di provisioning (facoltativo)
Puoi usare i pacchetti di provisioning per aggiungere certificati, personalizzare impostazioni e installare app. Per altri dettagli, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md) . Puoi [installare i pacchetti di provisioning alla prima esecuzione](first-run-program-surface-hub.md#first-page).

### Configurare i gruppi di amministratori
Tutti i dispositivi Surface Hub possono essere configurati localmente usando l'app Impostazioni nel dispositivo. Per impedire agli utenti non autorizzati di modificare le impostazioni, l'app Impostazioni richiede credenziali di amministratore per aprire l'app. Vedi [Gestione del gruppo amministratori](admin-group-management-for-surface-hub.md) per informazioni dettagliate su come vengono configurati e gestiti i gruppi di amministratori. Dovrai [configurare gli amministratori per il dispositivo alla prima esecuzione](first-run-program-surface-hub.md#setup-admins).

### Verificare e completare il foglio di lavoro per la configurazione di Surface Hub (facoltativo)
Quando usi il programma di prima esecuzione per il dispositivo Surface Hub, dovrai specificare alcune informazioni che sono riepilogate nel foglio di lavoro per la configurazione, dove troverai anche elenchi di info specifiche dell'ambiente che ti serviranno per il programma di prima esecuzione. Per altre informazioni, vedi [Foglio di lavoro per la configurazione](setup-worksheet-surface-hub.md).


## Contenuto della sezione

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Argomento</th>
<th align="left">Descrizione</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><a href="create-and-test-a-device-account-surface-hub.md" data-raw-source="[Create and test a device account](create-and-test-a-device-account-surface-hub.md)">Creare e testare un account del dispositivo</a></p></td>
<td align="left"><p>Questo argomento spiega come creare e testare l'account del dispositivo che Surface Hub usa per comunicare con Skype.</p></td>
</tr>
<tr class="even">
<td align="left"><p><a href="provisioning-packages-for-certificates-surface-hub.md" data-raw-source="[Create provisioning packages](provisioning-packages-for-certificates-surface-hub.md)">Creare pacchetti di provisioning</a></p></td>
<td align="left"><p>In Windows 10, le impostazioni che usano il Registro di sistema o una piattaforma CSP (Content Services Platform) possono essere configurate tramite pacchetti di provisioning. Ricorrendo al provisioning è possibile anche aggiungere certificati durante la prima esecuzione.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><a href="admin-group-management-for-surface-hub.md" data-raw-source="[Admin group management](admin-group-management-for-surface-hub.md)">Gestione del gruppo amministratori</a></p></td>
<td align="left"><p>Tutti i dispositivi Surface Hub possono essere configurati singolarmente aprendo l'app Impostazioni nel dispositivo. Tuttavia, per impedire ai non amministratori di modificare le impostazioni, l'app Impostazioni richiede le credenziali di amministratore per aprire l'app e modificare le impostazioni.</p>
<p>L'app Impostazioni richiede le credenziali di amministratore locale per aprire l'app.</p></td>
</tr>
</tbody>
</table>

## Ulteriori informazioni

- [Post di blog: Elenco dei domini attendibili di Surface Hub e Skype for Business](https://blogs.technet.microsoft.com/y0av/2017/10/25/95/)
- [Post di blog: Surface Hub in un ambiente con più domini](https://blogs.technet.microsoft.com/y0av/2017/11/08/11/)
- [Post di blog: Configurazione di un proxy per Surface Hub](https://blogs.technet.microsoft.com/y0av/2017/12/03/7/)

 

 






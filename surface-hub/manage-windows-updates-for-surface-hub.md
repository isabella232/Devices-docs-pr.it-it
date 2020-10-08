---
title: Manage Windows updates on Surface Hub
description: You can manage Windows updates on your Microsoft Surface Hub or Surface Hub 2S by setting the maintenance window, deferring updates, or using Windows Server Update Services (WSUS).
ms.assetid: A737BD50-2D36-4DE5-A604-55053D549045
ms.reviewer: ''
manager: laurawi
keywords: manage Windows updates, Surface Hub, Windows Server Update Services, WSUS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 72214ec9436e6ea106d9e42c957664631ee88a0a
ms.sourcegitcommit: f74253629aaf073b35b1af69439f76e63392c5aa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2020
ms.locfileid: "11103790"
---
# Manage Windows updates on Surface Hub

New releases of the Surface Hub operating system are published through Windows Update, just like releases of Windows 10. Sono disponibili due diverse modalità per gestire gli aggiornamenti da installare nei dispositivi Surface Hub e le tempistiche per l'applicazione degli aggiornamenti.
- **Windows Update for Business**: Windows Update for Business, una novità di Windows10, è un insieme di funzionalità progettate per garantire alle aziende un maggiore controllo su come e quando Windows Update installa le versioni, riducendo i costi di gestione dei dispositivi. Con questo metodo, i dispositivi Surface Hub sono direttamente connessi al servizio Windows Update di Microsoft.
- **WindowsServer Update Services (WSUS)**: è un insieme di servizi che consentono agli amministratori IT di ottenere gli aggiornamenti che Windows Update ritiene applicabili ai dispositivi inclusi nella rete aziendale, eseguire ulteriori test e cicli di valutazione su tali aggiornamenti e selezionare gli aggiornamenti da installare. Con questo metodo, i dispositivi Surface Hub riceveranno gli aggiornamenti da WSUS invece che da Windows Update.

Puoi anche configurare Surface Hub per ricevere gli aggiornamenti sia da Windows Update for Business che da WSUS. Vedi [Integrare Windows Update for Business con WindowsServer Update Services](https://technet.microsoft.com/itpro/windows/manage/waas-integrate-wufb#integrate-windows-update-for-business-with-windows-server-update-services) per maggiori dettagli.

| Funzionalità | Windows Update for Business | Windows Server Update Services (WSUS) |
| ------------ | --------------------------- | ------------------------------------- |
| Ricevere gli aggiornamenti direttamente dal servizio Windows Update di Microsoft, senza ulteriori infrastrutture richieste.  | Sì  | No  |
| Posticipare gli aggiornamenti per fornire altro tempo per il test e la valutazione. | Sì  | Sì  |
| Distribuire gli aggiornamenti a gruppi di dispositivi selezionati. | Sì | Sì |
| Definire finestre di manutenzione per l'installazione degli aggiornamenti. | Sì  | Sì  |

> [!TIP]
> Usa la condivisione del contenuto peer-to-peer per ridurre i problemi di larghezza di banda durante gli aggiornamenti. Vedi [Ottimizzare il recapito degli aggiornamenti di Windows10](https://technet.microsoft.com/itpro/windows/manage/waas-optimize-windows-10-updates) per maggiori dettagli.

> [!NOTE]
> Surface Hub non supporta attualmente il rollback gli aggiornamenti.


## Modello di manutenzione di Surface Hub

Surface Hub usa il modello di manutenzione di Windows 10, noto come [Windows as a Service (WaaS)](https://docs.microsoft.com/windows/deployment/update/waas-overview). Solitamente le nuove funzionalità venivano aggiunte solo nelle nuove versioni di Windows che venivano rilasciate a intervalli di qualche anno. Per la distribuzione di ogni nuova versione all'interno dell'organizzazione sono sempre stati necessari lunghi e dispendiosi processi. Di conseguenza, gli utenti finali e le organizzazioni spesso preferiscono non trarre vantaggio dalle innovazioni. L'obiettivo di Windows as a Service è fornire continuamente nuove funzionalità, mantenendo un elevato livello di qualità.

Microsoft pubblica regolarmente due tipi di versioni di Surface Hub su larga scala:
- **Feature updates** - Updates that install the latest new features, experiences, and capabilities. Microsoft expects to publish two new feature updates per year.
- **Quality updates** - Updates that focus on the installation of security fixes, drivers, and other servicing updates. Microsoft prevede di pubblicare un aggiornamento qualitativo cumulativo al mese.

Per migliorare la qualità di rilascio e semplificare le distribuzioni, tutte le nuove versioni di Windows10 pubblicate da Microsoft, incluso Surface Hub, saranno cumulative. Ciò significa che i nuovi aggiornamenti delle funzionalità e i nuovi aggiornamenti qualitativi conterranno i payload di tutte le versioni precedenti (in un formato ottimizzato per ridurre i requisiti di archiviazione e rete). L'installazione della versione consentirà pertanto di aggiornare completamente un dispositivo. Inoltre, diversamente dalle versioni precedenti di Windows, non è possibile installare un sottoinsieme di contenuti di un aggiornamento qualitativo di Windows10. Ad esempio, se un aggiornamento qualitativo contiene correzioni per tre vulnerabilità di sicurezza e per un problema relativo all'affidabilità, la distribuzione dell'aggiornamento determinerà l'installazione di tutte e quattro le correzioni.

The Surface Hub operating system receives updates on the [Semi-Annual Channel](https://docs.microsoft.com/windows/deployment/update/waas-overview#naming-changes). Like other editions of Windows 10, the servicing lifetime is finite. You must install new feature updates on machines running these branches in order to continue receiving quality updates.

Per altre informazioni su Windows as a Service, vedi [Panoramica di Windows as a Service](https://technet.microsoft.com/itpro/windows/manage/waas-overview).


## Usare Windows Update for Business
I dispositivi Surface Hub, come tutti i dispositivi Windows10, includono **Windows Update for Business** che consente di controllare le modalità di aggiornamento dei dispositivi. Windows Update for Business permette di ridurre i costi di gestione dei dispositivi, fornisce controlli per la distribuzione degli aggiornamenti, garantisce un accesso più rapido agli aggiornamenti per la sicurezza e consente l'accesso su base continuativa alle innovazioni più recenti di Microsoft. Per altre informazioni, vedi [Gestire gli aggiornamenti con Windows Update for Business](https://technet.microsoft.com/itpro/windows/manage/waas-manage-updates-wufb).

**Per configurare Windows Update for Business:**
1. [Includere i dispositivi Surface Hub nei circuiti di distribuzione](#group-surface-hub-into-deployment-rings)
2. [Configure when Surface Hub receives updates](#configure-when-surface-hub-receives-updates).

> [!NOTE]
> You can use Microsoft Intune, Microsoft Endpoint Configuration Manager, or a supported third-party MDM provider to set up WUfB. [Walkthrough: use Microsoft Intune to configure Windows Update for Business.](https://docs.microsoft.com/windows/deployment/update/waas-wufb-intune)


### Includere i dispositivi Surface Hub nei circuiti di distribuzione
Puoi usare i circuiti di distribuzione per controllare le tempistiche dell'implementazione degli aggiornamenti nei dispositivi Surface Hub, in modo da avere il tempo necessario per convalidarli. Ad esempio, puoi aggiornare in prima istanza un piccolo pool di dispositivi per verificare la qualità prima di procedere all'implementazione su larga scala nell'intera organizzazione. A seconda di chi gestisce Surface Hub nella tua organizzazione, prendi in considerazione la possibilità di incorporare Surface Hub nei circuiti di distribuzione che hai creato per gli altri dispositivi Windows10. Per altre informazioni sui circuiti di distribuzione, vedi [Creare circuiti di distribuzione per gli aggiornamenti di Windows10](https://technet.microsoft.com/itpro/windows/manage/waas-deployment-rings-windows-10-updates).

Questa tabella fornisce alcuni esempi dei circuiti di distribuzione.

| Circuito di distribuzione | Dimensione del circuito | Ramo di manutenzione | Posticipo per aggiornamenti delle funzionalità | Posticipo per aggiornamenti qualitativi (correzioni per la sicurezza, driver e altri aggiornamenti) | Fase di convalida |
| --------- | --------- | --------- | --------- | --------- | --------- |
| Valutazione (ad esempio, dispositivi non critici o di test) | Small | Windows Insider Preview | None.  | Nessuno.  | Testare e valutare manualmente le nuove funzionalità. Sospendere gli aggiornamenti in caso di problemi. |
| Installazione pilota (ad esempio, dispositivi usati da team selezionati) | Media | Canale semestrale  | Nessuno. | Nessuno.  | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. Sospendere gli aggiornamenti in caso di problemi. |
| Distribuzione su larga scala (ad esempio, maggior parte dei dispositivi dell'organizzazione) | Alta | Canale semestrale |  120 giorni dopo il rilascio. | 7-14 giorni dopo il rilascio. | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. Sospendere gli aggiornamenti in caso di problemi. |
| Importanza critica (ad esempio, dispositivi delle sale riunioni dei dirigenti) | Bassa | Canale semestrale |  180 giorni dopo il rilascio (posticipo massimo per gli aggiornamenti delle funzionalità). | 30 giorni dopo il rilascio (posticipo massimo per gli aggiornamenti qualitativi). | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. |





### Configurare quando i dispositivi Surface Hub ricevono gli aggiornamenti
Dopo avere determinato i circuiti di distribuzione per i dispositivi Surface Hub, configura i criteri per il posticipo degli aggiornamenti per ciascun circuito:
- Per posticipare gli aggiornamenti delle funzionalità, imposta un criterio [Update/DeferFeatureUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays) appropriato per ogni circuito.
- Per posticipare gli aggiornamenti qualitativi, imposta un criterio [Update/DeferQualityUpdatesPeriodInDays](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays) appropriato per ogni circuito.

> [!NOTE]
> Se si verificano problemi durante l'implementazione degli aggiornamenti, puoi sospendere gli aggiornamenti usando [Update/PauseFeatureUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausefeatureupdates) e [Update/PauseQualityUpdates](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-update#update-pausequalityupdates).


## Usare Windows Server Update Services

Puoi connettere Surface Hub al server WSUS (Windows Server Update Services) per gestire gli aggiornamenti. Gli aggiornamenti verranno controllati tramite approvazione o con regole di distribuzione automatica configurate nel server WSUS, in modo che i nuovi aggiornamenti non saranno distribuiti fino a quando non scegli di farlo.

**Per connettere manualmente un dispositivo Surface Hub a un server WSUS:**
1. Apri **Impostazioni** nel dispositivo Surface Hub.
2. Quando viene richiesto, immetti le credenziali di amministratore del dispositivo.
3. Passa a **Aggiornamento e sicurezza** > **Windows Update** > **Opzioni avanzate** > **Configura server WindowsServer Update Services (WSUS)**.
4. Fai clic su **Usa il server WSUS per scaricare gli aggiornamenti** e digita l'URL del server WSUS.

Per connettere Surface Hub a un server WSUS con MDM, imposta un criterio [Update/UpdateServiceUrl](https://msdn.microsoft.com/library/windows/hardware/dn904962.aspx#Update_UpdateServiceUrl) appropriato.

**Se utilizzi un server proxy o un altro metodo di blocco di URL**

Se utilizzi un metodo diverso da WSUS per bloccare URL specifici e impedire gli aggiornamenti, dovrai aggiungere i seguenti URL di siti attendibili di Windows Update all’elenco degli indirizzi consentiti:
- `http(s)://*.update.microsoft.com`
- `http://download.windowsupdate.com` 
- `http://windowsupdate.microsoft.com`

Al termine dell’installazione dell’Aggiornamento dell’anniversario di Windows 10 Team, potrai rimuovere questi indirizzi per ripristinare lo stato precedente di Surface Hub.

## Finestra di manutenzione

To ensure the device is always available for use during business hours, Surface Hub performs its administrative functions during a specified maintenance window. During the maintenance window, the Surface Hub automatically installs updates through Windows Update or WSUS, and reboots the device 20 minutes before the end of the window.

Surface Hub follows these guidelines to apply updates:
- Installare l'aggiornamento durante la finestra di manutenzione successiva. Se l'inizio di una riunione è pianificato durante una finestra di manutenzione o i sensori di Surface Hub rilevano che il dispositivo è in uso, l'aggiornamento in sospeso verrà posticipato alla finestra di manutenzione seguente.
- Se la finestra di manutenzione successiva è prevista dopo il periodo di tolleranza prescritto per l'aggiornamento, il dispositivo calcolerà la successiva fascia oraria disponibile durante l'orario lavorativo sulla base del tempo di installazione stimato dai metadati dell'aggiornamento. Continuerà a posticipare l'aggiornamento se è pianificata una riunione o se i sensori di Surface Hub rilevano che il dispositivo è in uso.
- If the next maintenance window is **not** past the update's grace period, the Surface Hub will continue to postpone the update.
- If a reboot is needed, the Surface Hub will automatically reboot during the next maintenance window.

> [!NOTE]
> Assicurati di lasciare il tempo necessario per gli aggiornamenti quando configuri per la prima volta il tuo dispositivo Surface Hub. Ad esempio, potrebbe essere disponibile un backlog di definizioni dei virus che deve essere installato immediatamente.

A default maintenance window is set for all new Surface Hubs:
-   **Start time:** 2:00 AM
-   **Duration:** 2 hours

**To manually change the maintenance window:**
1.  Apri **Impostazioni** nel dispositivo Surface Hub.
2.  Passa a **Aggiornamento e sicurezza** > **Windows Update** > **Opzioni avanzate**.
3.  In **Ore di manutenzione** seleziona **Cambia**.

Per cambiare la finestra di manutenzione con MDM, imposta il nodo **MOMAgent** nel [provider di servizi di configurazione SurfaceHub](https://msdn.microsoft.com/library/windows/hardware/mt608323.aspx). See [Manage settings with an MDM provider](manage-settings-with-mdm-for-surface-hub.md) for more details.


## More information

- [Blog post: Servicing, Flighting, and Managing updates for Surface Hub (With Intune, of course!)](https://blogs.technet.microsoft.com/y0av/2018/05/31/7-3/)


## Related topics

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)


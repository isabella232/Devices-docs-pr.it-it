---
title: Gestire gli aggiornamenti di Windows su una Surface Hub
description: Vengono descritte le procedure consigliate per la gestione degli aggiornamenti in Microsoft Surface Hub o Surface Hub 2S.
ms.assetid: A737BD50-2D36-4DE5-A604-55053D549045
ms.reviewer: ''
manager: laurawi
keywords: gestire aggiornamenti Windows, Surface Hub, Windows Server Update Services
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/27/2020
ms.localizationpriority: medium
ms.openlocfilehash: ecff961e1aaa14ed2af5e6d91ffc2254e4dcfa46
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497779"
---
# <a name="manage-windows-updates-on-surface-hub"></a>Gestire gli aggiornamenti di Windows su una Surface Hub

Le nuove versioni del sistema operativo Surface Hub vengono pubblicate tramite Windows Update, proprio come le versioni di Windows 10 o Windows 11. Questa pagina illustra le procedure consigliate per la gestione degli aggiornamenti per i dispositivi Surface Hub. 

## <a name="windows-update-for-business"></a>Windows Update per le aziende

Windows Update for Business è un set di funzionalità progettate per fornire alle aziende un controllo aggiuntivo su come e quando Windows Update installa le versioni, riducendo al contempo i costi di gestione dei dispositivi. Con questo metodo, i dispositivi Surface Hub sono direttamente connessi al servizio Windows Update di Microsoft.

- Ricevere gli aggiornamenti direttamente dal servizio Windows Update di Microsoft, senza ulteriori infrastrutture richieste. 
- Posticipare gli aggiornamenti per fornire altro tempo per il test e la valutazione. 
- Distribuire gli aggiornamenti a gruppi di dispositivi selezionati. 
- Definire finestre di manutenzione per l'installazione degli aggiornamenti. 

> [!TIP]
> Usa la condivisione del contenuto peer-to-peer per ridurre i problemi di larghezza di banda durante gli aggiornamenti. Per informazioni dettagliate[, vedere Ottimizzare Windows recapito degli aggiornamenti](/windows/deployment/do/waas-optimize-windows-10-updates).

> [!NOTE]
> Surface Hub non supporta attualmente il rollback gli aggiornamenti.


## <a name="surface-hub-servicing-model"></a>Modello di manutenzione di Surface Hub

Surface Hub usa il modello di manutenzione Windows, noto come [Windows come servizio (WaaS).](/windows/deployment/update/waas-overview) Solitamente le nuove funzionalità venivano aggiunte solo nelle nuove versioni di Windows che venivano rilasciate a intervalli di qualche anno. Per la distribuzione di ogni nuova versione all'interno dell'organizzazione sono sempre stati necessari lunghi e dispendiosi processi. Di conseguenza, gli utenti finali e le organizzazioni spesso preferiscono non trarre vantaggio dalle innovazioni. L'obiettivo di Windows as a Service è fornire continuamente nuove funzionalità, mantenendo un elevato livello di qualità.

Microsoft pubblica regolarmente due tipi di versioni di Surface Hub su larga scala:
- **Aggiornamenti delle funzionalità**: aggiornamenti che consentono di installare la versione più recente di nuove funzionalità, esperienze e caratteristiche. Microsoft prevede di pubblicare due nuovi aggiornamenti delle funzionalità all'anno.
- **Aggiornamenti qualitativi**: aggiornamenti che consentono di installare principalmente correzioni per la sicurezza, driver e altri aggiornamenti di manutenzione. Microsoft prevede di pubblicare un aggiornamento qualitativo cumulativo al mese.

Per migliorare la qualità delle versioni e semplificare le distribuzioni, tutte le nuove versioni pubblicate da Microsoft per Windows 10 o Windows 11, incluse le Surface Hub, saranno cumulative. Ciò significa che i nuovi aggiornamenti delle funzionalità e i nuovi aggiornamenti qualitativi conterranno i payload di tutte le versioni precedenti (in un formato ottimizzato per ridurre i requisiti di archiviazione e rete). L'installazione della versione consentirà pertanto di aggiornare completamente un dispositivo. Inoltre, diversamente dalle versioni precedenti di Windows, non è possibile installare un sottoinsieme di contenuti di un aggiornamento qualitativo di Windows10. Ad esempio, se un aggiornamento qualitativo contiene correzioni per tre vulnerabilità di sicurezza e per un problema relativo all'affidabilità, la distribuzione dell'aggiornamento determinerà l'installazione di tutte e quattro le correzioni.

Il sistema operativo Surface Hub riceve gli aggiornamenti nel [Canale semestrale](/windows/deployment/update/waas-overview#naming-changes). Come altre edizioni di Windows 10 o Windows 11, la durata della manutenzione è limitata. Per poter continuare a ricevere gli aggiornamenti qualitativi devi installare nuovi aggiornamenti delle funzionalità nei computer che eseguono questi rami.

Per altre informazioni su Windows as a Service, vedi [Panoramica di Windows as a Service](/windows/deployment/update/waas-overview).


## <a name="use-windows-update-for-business"></a>Usare Windows Update for Business

I dispositivi Surface Hub, come tutti i dispositivi Windows10, includono **Windows Update for Business** che consente di controllare le modalità di aggiornamento dei dispositivi. Windows Update for Business permette di ridurre i costi di gestione dei dispositivi, fornisce controlli per la distribuzione degli aggiornamenti, garantisce un accesso più rapido agli aggiornamenti per la sicurezza e consente l'accesso su base continuativa alle innovazioni più recenti di Microsoft. Per altre informazioni, vedi [Gestire gli aggiornamenti con Windows Update for Business](/windows/deployment/update/waas-manage-updates-wufb).

> [!IMPORTANT]
> Microsoft rilascia in genere un aggiornamento obbligatorio della sicurezza Windows al mese (rilasciato il 2 martedì e spesso definito "B"). Insieme agli aggiornamenti della sicurezza fuori banda, questi sono gli unici aggiornamenti resi disponibili ai dispositivi che usano WUfB. Tuttavia, Surface Hub miglioramenti vengono in genere forniti tramite aggiornamenti facoltativi non di sicurezza il 3° martedì di ogni mese ("C"). Di conseguenza, i clienti che usano Windows Update for Business con i propri Surface Hub dovranno attendere la versione "B" del mese successivo per visualizzare gli ultimi miglioramenti su questi dispositivi.

**Per configurare Windows Update for Business:**
1. [Includere i dispositivi Surface Hub nei circuiti di distribuzione](#group-surface-hub-into-deployment-rings)
2. [Configurare quando i dispositivi Surface Hub ricevono gli aggiornamenti](#configure-when-surface-hub-receives-updates).

> [!NOTE]
> È possibile usare Microsoft Intune, Microsoft Endpoint Configuration Manager o un provider MDM di terze parti supportato per configurare WUfB. [Procedura dettagliata: usare Microsoft Intune per configurare Windows Update for Business.](/windows/deployment/update/waas-wufb-intune)


### <a name="group-surface-hub-into-deployment-rings"></a>Includere i dispositivi Surface Hub nei circuiti di distribuzione

Puoi usare i circuiti di distribuzione per controllare le tempistiche dell'implementazione degli aggiornamenti nei dispositivi Surface Hub, in modo da avere il tempo necessario per convalidarli. Ad esempio, puoi aggiornare in prima istanza un piccolo pool di dispositivi per verificare la qualità prima di procedere all'implementazione su larga scala nell'intera organizzazione. A seconda di chi gestisce Surface Hub nell'organizzazione, è consigliabile incorporare Surface Hub negli anelli di distribuzione creati per gli altri dispositivi Windows 10 o Windows 11. Per altre informazioni sugli anelli di distribuzione, vedere [Preparare la strategia di manutenzione per Windows aggiornamenti client](/windows/deployment/update/waas-servicing-strategy-windows-10-updates).

Per esempi di circuiti di distribuzione, vedere la tabella seguente.

| Circuito di distribuzione | Dimensione del circuito | Ramo di manutenzione | Posticipo per aggiornamenti delle funzionalità | Posticipo per aggiornamenti qualitativi (correzioni per la sicurezza, driver e altri aggiornamenti) | Fase di convalida |
| --------- | --------- | --------- | --------- | --------- | --------- |
| Valutazione (ad esempio, dispositivi non critici o di test) | Bassa | Windows Insider Preview | Nessuno.  | Nessuno.  | Testare e valutare manualmente le nuove funzionalità. Sospendere gli aggiornamenti in caso di problemi. |
| Installazione pilota (ad esempio, dispositivi usati da team selezionati) | Media | Canale semestrale  | Nessuno. | Nessuno.  | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. Sospendere gli aggiornamenti in caso di problemi. |
| Distribuzione su larga scala (ad esempio, maggior parte dei dispositivi dell'organizzazione) | Alta | Canale semestrale |  120 giorni dopo il rilascio. | 7-14 giorni dopo il rilascio. | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. Sospendere gli aggiornamenti in caso di problemi. |
| Importanza critica (ad esempio, dispositivi delle sale riunioni dei dirigenti) | Bassa | Canale semestrale |  180 giorni dopo il rilascio (posticipo massimo per gli aggiornamenti delle funzionalità). | 30 giorni dopo il rilascio (posticipo massimo per gli aggiornamenti qualitativi). | Monitorare l'utilizzo dei dispositivi e il feedback degli utenti. |


### <a name="configure-when-surface-hub-receives-updates"></a>Configurare quando i dispositivi Surface Hub ricevono gli aggiornamenti

Dopo avere determinato i circuiti di distribuzione per i dispositivi Surface Hub, configura i criteri per il posticipo degli aggiornamenti per ciascun circuito:
- Per posticipare gli aggiornamenti delle funzionalità, imposta un criterio [Update/DeferFeatureUpdatesPeriodInDays](/windows/client-management/mdm/policy-csp-update#update-deferfeatureupdatesperiodindays) appropriato per ogni circuito.
- Per posticipare gli aggiornamenti qualitativi, imposta un criterio [Update/DeferQualityUpdatesPeriodInDays](/windows/client-management/mdm/policy-csp-update#update-deferqualityupdatesperiodindays) appropriato per ogni circuito.

> [!NOTE]
> Se si verificano problemi durante l'implementazione degli aggiornamenti, puoi sospendere gli aggiornamenti usando [Update/PauseFeatureUpdates](/windows/client-management/mdm/policy-csp-update#update-pausefeatureupdates) e [Update/PauseQualityUpdates](/windows/client-management/mdm/policy-csp-update#update-pausequalityupdates).

**Se utilizzi un server proxy o un altro metodo di blocco di URL**

Aggiungere i seguenti Windows aggiornare gli URL del sito attendibile all'"elenco consenti":
- `http(s)://*.update.microsoft.com`
- `http://download.windowsupdate.com` 
- `http://windowsupdate.microsoft.com`

Al termine dell’installazione dell’Aggiornamento dell’anniversario di Windows 10 Team, potrai rimuovere questi indirizzi per ripristinare lo stato precedente di Surface Hub.

## <a name="maintenance-window"></a>Finestra di manutenzione

Per garantire che il dispositivo sia sempre disponibile per l’uso durante l’orario lavorativo, Surface Hub esegue le operazioni amministrative durante una finestra di manutenzione specificata. Durante la finestra di manutenzione, il Surface Hub installa automaticamente gli aggiornamenti tramite Windows Update e riavvia il dispositivo 20 minuti prima della fine della finestra.

Surface Hub si attiene a queste linee guida per l'applicazione degli aggiornamenti:
- Installare l'aggiornamento durante la finestra di manutenzione successiva. Se l'inizio di una riunione è pianificato durante una finestra di manutenzione o i sensori di Surface Hub rilevano che il dispositivo è in uso, l'aggiornamento in sospeso verrà posticipato alla finestra di manutenzione seguente.
- Se la finestra di manutenzione successiva è prevista dopo il periodo di tolleranza prescritto per l'aggiornamento, il dispositivo calcolerà la successiva fascia oraria disponibile durante l'orario lavorativo sulla base del tempo di installazione stimato dai metadati dell'aggiornamento. Continuerà a posticipare l'aggiornamento se è pianificata una riunione o se i sensori di Surface Hub rilevano che il dispositivo è in uso.
- Se la finestra di manutenzione successiva **non** supera il periodo di tolleranza dell'aggiornamento, il Surface Hub continuerà a posticipare l'aggiornamento.
- Se è necessario un riavvio, il dispositivo Surface Hub verrà riavviato automaticamente durante la finestra di manutenzione successiva.

> [!NOTE]
> Assicurati di lasciare il tempo necessario per gli aggiornamenti quando configuri per la prima volta il tuo dispositivo Surface Hub. Ad esempio, potrebbe essere disponibile un backlog di definizioni dei virus che deve essere installato immediatamente.

Per tutti i nuovi dispositivi Surface Hub è impostata una finestra di manutenzione predefinita:
-   **Ora di inizio:** 2:00
-   **Durata:** 2 ore

**Per modificare manualmente la finestra di manutenzione:**
1.  Apri **Impostazioni** nel dispositivo Surface Hub.
2.  Passa a **Aggiornamento e sicurezza** > **Windows Update** > **Opzioni avanzate**.
3.  In **Ore di manutenzione** seleziona **Cambia**.

Per modificare la finestra di manutenzione usando MDM, impostare il nodo **MaintenanceHoursSimple** nel [provider del servizio di configurazione SurfaceHub](/windows/client-management/mdm/surfacehub-csp). Vedi [Gestire le impostazioni con un provider MDM](manage-settings-with-mdm-for-surface-hub.md) per maggiori dettagli.


## <a name="more-information"></a>Altre informazioni

- [Post di blog: Manutenzione, anteprima e gestione degli aggiornamenti per Surface Hub (con Intune, naturalmente!)](https://blogs.technet.microsoft.com/y0av/2018/05/31/7-3/)


## <a name="related-topics"></a>Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)


---
title: Monitorare il dispositivo Microsoft Surface Hub
description: Il monitoraggio dei dispositivi Microsoft Surface Hub è abilitato tramite Microsoft Operations Management Suite (OMS).
ms.assetid: 1D2ED317-DFD9-423D-B525-B16C2B9D6942
ms.reviewer: ''
manager: laurawi
keywords: monitorare Surface Hub, Microsoft Operations Management Suite, OMS
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 108f24036a0e02295cf2a5588bb6b51e517eba8d
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833651"
---
# Monitorare il dispositivo Microsoft Surface Hub

Il monitoraggio dei dispositivi Microsoft Surface Hub è abilitato tramite Microsoft Operations Management Suite (OMS). [Operations Management Suite](https://go.microsoft.com/fwlink/?LinkId=718138) è la soluzione di gestione IT di Microsoft che ti consente di gestire e proteggere l'intera infrastruttura IT, compresi i dispositivi Surface Hub.


Surface Hub è disponibile come soluzione di Log Analytics in OMS, consentendoti di raccogliere e visualizzare dati sull'uso e l'affidabilità per tutti i tuoi dispositivi Surface Hub. Usa la soluzione Surface Hub per:
- Eseguire l'inventario dei dispositivi Surface Hub.
- Visualizzare uno snapshot dei dati sull'uso e l'affidabilità per le riunioni di Skype, la proiezione wireless e cablata e le app nei tuoi dispositivi Surface Hub.
- Creare avvisi personalizzati per intervenire tempestivamente se i dispositivi Surface Hub rilevano problemi hardware o software.

## Aggiungere Surface Hub a Operations Management Suite

1. **Accedi a Operations Management Suite (OMS)**. Puoi usare un account Microsoft oppure un account aziendale o di un istituto di istruzione per creare un'area di lavoro. Se la tua azienda usa già Azure Active Directory (Azure AD), usa un account aziendale o di un istituto di istruzione quando accedi a OMS. Usando un account aziendale o di un istituto di istruzione puoi usare le identità di Azure AD per gestire le autorizzazioni in OMS.
2. **Crea una nuova area di lavoro OMS**. Immetti un nome per l'area di lavoro, seleziona l'area geografica e fornisci l'indirizzo e-mail che vuoi associare a questa area di lavoro. Seleziona **Crea**.
3. **Collega la sottoscrizione Azure all'area di lavoro**. Se la tua organizzazione ha già una sottoscrizione Azure, puoi collegarla all'area di lavoro. Tieni presente che potresti dover richiedere l’accesso all’amministratore Azure della tua organizzazione.

    > [!NOTE] 
    > Se la tua organizzazione non dispone di una sottoscrizione Azure, creane una nuova oppure seleziona dall'elenco la sottoscrizione Azure di OMS predefinita. Verrà aperta l'area di lavoro.

4. **Aggiungi la soluzione Surface Hub**. Nella raccolta soluzioni seleziona il riquadro **Surface Hub** e quindi seleziona **Aggiungi** nella pagina dei dettagli della soluzione. La soluzione è ora visibile nell'area di lavoro.

## Usare il dashboard di Surface Hub
Dalla pagina **Panoramica** nell'area di lavoro di OMS fai clic sul riquadro Surface Hub per visualizzare il dashboard di Surface Hub. Usa il dashboard per ottenere uno snapshot dei dati sull'uso e l'affidabilità dei tuoi dispositivi Surface Hub. Fai clic in ogni visualizzazione nel dashboard per visualizzare dati dettagliati, modificare la query in base alle esigenze e creare avvisi.

> [!NOTE]
> La maggior parte di queste visualizzazioni mostra i dati per gli ultimi 30 giorni, ma questa impostazione è soggetta ai criteri di conservazione dei dati della tua sottoscrizione.

**Dispositivi Surface Hub attivi**

Usa questa visualizzazione per ottenere un inventario di tutti i tuoi dispositivi Surface Hub. Una volta connesso a OMS, ogni dispositivo Surface Hub invia periodicamente un evento "heartbeat" al server. Questa visualizzazione mostra i dispositivi Surface Hub che hanno segnalato un heartbeat nelle ultime 24 ore.

<!--
**Skype meetings**

Use this view to get usage data for Skype over the past 30 days. The graph shows the total number of Skype Meetings started across your Surface Hubs, and a breakdown between scheduled meetings, ad hoc meetings, and PSTN calls.
-->
 
**Proiezione wireless**

Usa questa visualizzazione per ottenere i dati sull'uso e l'affidabilità per la proiezione wireless negli ultimi 30 giorni. Il grafico mostra il numero totale di connessioni wireless tra tutti i dispositivi Surface Hub, fornendo un'indicazione sull'uso di questa funzionalità da parte degli utenti della tua organizzazione. Se è un valore basso, può indicare che gli utenti della tua organizzazione hanno bisogno di formazione su come connettersi in modalità wireless ai dispositivi Surface Hub.
 
Inoltre, il grafico mostra un'analisi dettagliata delle connessioni riuscite e non riuscite. Se viene visualizzato un numero elevato di connessioni non riuscite, i dispositivi potrebbero non supportare correttamente la proiezione wireless con Miracast. Per ottenere prestazioni ottimali dai dispositivi, Microsoft suggerisce di usare un driver Wi-Fi WDI e un driver di grafica WDDM 2.0. Usa la visualizzazione dei dettagli per capire se i problemi di proiezione wireless sono comuni con particolari dispositivi.
 
Quando una connessione ha esito negativo, gli utenti possono anche effettuare le operazioni seguenti se stanno usando un telefono o un portatile Windows:
- Rimuovi il dispositivo associato da **Impostazioni** > **Dispositivi** > **Dispositivi connessi**, quindi riprova a connetterti.
- Riavvia il dispositivo.
 
**Proiezione cablata**

Usa questa visualizzazione per ottenere i dati sull'uso e l'affidabilità per la proiezione cablata negli ultimi 30 giorni. Se il grafico mostra un numero elevato di connessioni non riuscite, può indicare un problema di connettività nella pipeline audiovisiva. Ad esempio, se usi un ripetitore HDMI o un pannello di controllo al centro della stanza, potresti doverlo riavviare.
 
**Uso delle applicazioni**

Usa questa visualizzazione per ottenere i dati sull'uso per le app presenti nei tuoi dispositivi Surface Hub negli ultimi 30 giorni. I dati provengono dagli avvii delle app nei dispositivi Surface Hub, fatta eccezione per Skype for Business. Questa visualizzazione consente di comprendere quali sono le app di Surface Hub più importanti nella tua organizzazione. Se intendi distribuire nuove app line-of-business nel tuo ambiente, questa visualizzazione può anche essere utile per comprendere con che frequenza vengono usate.
 
**Arresti anomali delle applicazioni**

Usa questa visualizzazione per ottenere i dati sull'affidabilità per le app presenti nei tuoi dispositivi Surface Hub negli ultimi 30 giorni. I dati provengono dagli arresti anomali delle app nei dispositivi Surface Hub. Questa visualizzazione consente di rilevare e segnalare agli sviluppatori di app le app line-of-business e quelle incorporate con prestazioni non ottimali.
 
**Query di esempio**

Usa questa funzionalità per creare avvisi personalizzati in base a un insieme consigliato di query. Gli avvisi ti consentono di intervenire tempestivamente se i dispositivi Surface Hub rilevano problemi hardware o software. Per altre informazioni, vedi [Impostare avvisi usando query di esempio](#set-up-alerts-with-sample-queries).

## Impostare avvisi usando query di esempio

Usa gli avvisi per intervenire tempestivamente se i dispositivi Surface Hub rilevano problemi hardware o software. Le regole di avviso eseguono automaticamente ricerche nei log in base a una pianificazione ed eseguono una o più azioni se i risultati corrispondono ai criteri specificati. Per altre informazioni, vedi l'argomento relativo agli [avvisi in Log Analytics](https://azure.microsoft.com/documentation/articles/log-analytics-alerts/).
 
La soluzione Surface Hub di Log Analytics include un set di query di esempio per aiutarti a impostare gli avvisi appropriati e comprendere in che modo risolvere i problemi che possono verificarsi. Usa queste query come punto di partenza per pianificare la tua strategia di monitoraggio e supporto.

Questa tabella descrive le query di esempio nella soluzione Surface Hub:

| Tipo di avviso | Impatto | Correzione consigliata | Dettagli |
| ---------- | ------ | ----------------------- | ------- |
| Software   | Errore  | **Riavviare il dispositivo**. <br> Riavvia manualmente o usando il [provider di servizi di configurazione Reboot](https://msdn.microsoft.com/library/windows/hardware/mt720802(v=vs.85).aspx). <br> È consigliabile eseguire questa operazione tra una riunione e l'altra per ridurre al minimo l'impatto per gli utenti dell'organizzazione. | Condizioni di attivazione: <br> - Un processo critico nel sistema operativo Surface Hub, ad esempio il blocco o l'arresto anomalo della shell, della proiezione o di Skype. <br> - Il dispositivo non ha segnalato heartbeat nelle ultime 24 ore. Ciò può dipendere da un problema di connettività di rete, da un guasto hardware correlato alla rete o da un errore del sistema di reporting dei dati di diagnostica. |
| Software   | Errore  | **Controllare il servizio Exchange**. <br> Verifica: <br> - Che il servizio sia disponibile. <br> - Che la password dell'account del dispositivo sia aggiornata. Per altri dettagli, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).| Viene generato quando si verifica un errore nella sincronizzazione del calendario del dispositivo con Exchange. |
| Software   | Errore  | **Controllare il servizio Skype for Business**. <br> Verifica: <br> - Che il servizio sia disponibile. <br> - Che la password dell'account del dispositivo sia aggiornata. Per altri dettagli, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md). <br> - Che il nome di dominio per Skype for Business sia configurato correttamente. Vedi l'argomento relativo alla [configurazione di un nome di dominio](use-fully-qualified-domain-name-surface-hub.md). | Viene generato quando Skype non riesce a eseguire l'accesso. |
| Software   | Errore  | **Reimpostare il dispositivo**. <br> Questa operazione richiede del tempo, pertanto è consigliabile che il dispositivo sia offline. <br> Per altre informazioni, vedi [Reimpostazione del dispositivo](device-reset-surface-hub.md).| Viene generato quando si verifica un errore durante la cancellazione dei dati dell'utente e delle app al termine di una sessione. Quando questa operazione ha ripetutamente esito negativo, il dispositivo viene bloccato per proteggere i dati dell'utente. È necessario reimpostare il dispositivo per continuare. |
| Hardware   | Avviso | **Nessuno**. Indica un impatto minimo per le funzionalità.| Viene generato quando si verifica un errore con uno dei componenti hardware seguenti: <br> - Slot penna virtuale <br> - Driver NFC <br> - Driver hub USB <br> - Driver Bluetooth <br> - Sensore di prossimità <br> - Prestazioni grafiche (driver scheda video) <br> - Unità disco rigido non corrispondente <br> - Nessun mouse/tastiera rilevato |
| Hardware   | Errore | **Contattare il supporto Microsoft**. <br> Indica l'impatto sulle funzionalità di base (ad esempio Skype, proiezione, tocco e connettività Internet). <br> **Nota** Alcuni eventi, tra cui l'heartbeat, includono il numero di serie del dispositivo che puoi usare quando contatti il supporto tecnico.| Viene generato quando si verifica un errore con uno dei componenti hardware seguenti. <br> **Componenti che influiscono su Skype**: <br> - Driver altoparlante <br> - Driver microfono <br> - Driver fotocamera <br> **Componenti che influiscono sulla proiezione wireless e cablata**: <br> - Driver Touchback cablato <br> - Driver acquisizione cablato <br> - Driver scheda wireless <br> - Errore di Wi-Fi Direct <br> **Altri componenti**: <br> - Driver digitalizzatore a tocco <br> - Errore della scheda di rete (non segnalato a OMS)|

**Per impostare un avviso**
1. Dalla soluzione Surface Hub seleziona una delle query di esempio.
2. Modifica la query in base alle esigenze. Vedi i riferimenti per le ricerche di Log Analytics per saperne di più.
3. Fai clic su **Avviso** nella parte superiore della pagina per aprire la schermata **Aggiungi regola di avviso**. Vedi l'argomento relativo agli [avvisi in Log Analytics](https://azure.microsoft.com/documentation/articles/log-analytics-alerts/) per dettagli sulle opzioni per la configurazione degli avvisi.
4. Fai clic su **Salva** per completare la regola di avviso. Inizierà a essere eseguita immediatamente.

## Registrare il dispositivo Surface Hub

Per la connessione e la registrazione del dispositivo Surface Hub con il servizio OMS, il dispositivo deve avere accesso al numero di porta dei domini e agli URL. Questa tabella elenca le porte richieste per OMS. Per altre informazioni, vedi l’argomento relativo alla [configurazione delle impostazioni proxy e firewall in Log Analytics](https://azure.microsoft.com/documentation/articles/log-analytics-proxy-firewall/).

>[!NOTE]
>Surface Hub non supporta attualmente l’uso di un server proxy per comunicare con il servizio OMS.

| Risorsa agente              | Porte | Ignorare ispezione HTTPS? |
| --------------------------- | ----- | ------------------------ |
| *.ods.opinsights.azure.com  | 443   | Sì |
| *.oms.opinsights.azure.com  | 443   | Sì |
| *.blob.core.windows.net     | 443   | Sì |
| ods.systemcenteradvisor.com | 443   | No  |

Microsoft Monitoring Agent, usato per connettere i dispositivi a OMS, è integrato con il sistema operativo Surface Hub, di conseguenza non è necessario installare client aggiuntivi per connettere Surface Hub a OMS.
 
Una volta configurata l'area di lavoro di OMS, esistono alcuni modi per registrare i tuoi dispositivi Surface Hub:
- [App Impostazioni](#enroll-using-the-settings-app)
- [Pacchetto di provisioning](#enroll-using-a-provisioning-package)
- [Provider MDM](#enroll-using-a-mdm-provider), come Microsoft Intune e Configuration Manager
 
Ti servirà l'ID dell'area di lavoro e la chiave primaria per l'area di lavoro di OMS. Puoi ottenere queste informazioni dal portale di OMS.
 
### Eseguire la registrazione con l'app Impostazioni

**Per eseguire la registrazione con l'app Impostazioni**

1. Dal tuo dispositivo Surface Hub avvia **Impostazioni**.
2. Quando viene richiesto, immetti le credenziali di amministratore del dispositivo.
3. Seleziona **Questo dispositivo** e passa a **Gestione dei dispositivi**.
4. In **Monitoraggio** seleziona **Configura impostazioni OMS**.
5. Nella finestra di dialogo delle impostazioni di OMS seleziona **Abilita monitoraggio**.
6. Digita l'ID dell'area di lavoro e la chiave primaria per l'area di lavoro di OMS. Puoi ottenere queste informazioni dal portale di OMS.
7. Fai clic su **OK** per completare la configurazione.
 
Verrà visualizzata una finestra di dialogo di conferma in cui viene indicato se la configurazione OMS è stata applicata correttamente o meno al dispositivo. Nel primo caso, il dispositivo inizierà a inviare i dati a OMS.

### Eseguire la registrazione con un pacchetto di provisioning
Puoi usare un pacchetto di provisioning per registrare il tuo dispositivo Surface Hub. Per altre informazioni, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md).
 
### Eseguire la registrazione con un provider MDM
Puoi registrare il dispositivo Surface Hub in OMS mediante il CSP SurfaceHub. Intune e Configuration Manager prevedono esperienze predefinite per aiutarti a creare modelli di criteri per Surface Hub. Per altre informazioni, vedi [Gestire le impostazioni di Surface Hub con un provider MDM](manage-settings-with-mdm-for-surface-hub.md).

## Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

 

 






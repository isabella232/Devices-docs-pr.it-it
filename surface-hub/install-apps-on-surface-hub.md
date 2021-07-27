---
title: Installare app nel dispositivo Microsoft Surface Hub
description: Gli amministratori possono installare app da Microsoft Store o da Microsoft Store per le aziende.
ms.assetid: 3885CB45-D496-4424-8533-C9E3D0EDFD94
ms.reviewer: dpandre
manager: laurawi
keywords: installare app, Microsoft Store, Microsoft Store per le aziende
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/16/2021
ms.localizationpriority: medium
audience: ITPro
ms.openlocfilehash: a8c11406c7786e379999ff32f482815d6b180b24
ms.sourcegitcommit: 62b85dfb85abbe0d880b04e1bcee5bacc9fc045f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2021
ms.locfileid: "11676660"
---
# <a name="install-apps-on-your-microsoft-surface-hub"></a>Installare app nel dispositivo Microsoft Surface Hub

Puoi installare altre app nel tuo dispositivo Surface Hub in base alle esigenze del tuo team o dell'organizzazione. Esistono diversi metodi per installare le app, a seconda che tu stia sviluppando e testando un'app o distribuendone una rilasciata. Questo argomento descrive i metodi per l'installazione delle app per entrambi gli scenari.

## <a name="supported-app-guidelines"></a>Linee guida per le app supportate

- Surface Hub esegue solo le [app della piattaforma UWP (Universal Windows Platform)](/windows/uwp/get-started/universal-application-platform-guide). Le app create con lo strumento di creazione [di pacchetti MSIX](/windows/msix/packaging-tool/tool-overview) non verranno eseguite Surface Hub.
- Le app devono essere destinate alla [famiglia di dispositivi universali](/windows/uwp/get-started/universal-application-platform-guide) o alla famiglia di dispositivi Windows Team.
- Surface Hub supporta solo [le app con licenza offline](/microsoft-store/distribute-offline-apps) di [Microsoft Store per le aziende](https://businessstore.microsoft.com/store/private-store).
- Per impostazione predefinita, le app devono riportare la firma dello Store per essere installate. Durante lo sviluppo e il test, puoi anche scegliere di eseguire app UWP firmate dallo sviluppatore inserendo il dispositivo in modalità sviluppatore.
- Quando invii un'app al Microsoft Store, gli sviluppatori devono impostare la disponibilità della famiglia di dispositivi e le opzioni di licenza dell'organizzazione per assicurarsi che un'app sia disponibile per l'esecuzione Surface Hub.
- Sono necessarie credenziali di amministratore per installare app in un dispositivo Surface Hub. Dato che il dispositivo è progettato per l'uso in spazi comuni come le sale riunioni, gli utenti non possono accedere a Microsoft Store per scaricare e installare app.

## <a name="deploy-released-apps"></a>Distribuire app rilasciate

Sono disponibili diverse opzioni per installare le app che sono state rilasciate in Microsoft Store, a seconda che tu voglia valutarle solo in alcuni dispositivi o distribuirle su larga scala alla tua organizzazione.

Per installare app rilasciate:

- Scarica l'app tramite l'app di Microsoft Store oppure
- Scarica il pacchetto dell'app da Microsoft Store per le aziende e distribuiscilo usando un pacchetto di provisioning o un provider MDM supportato.

### <a name="microsoft-store-app"></a>App di Microsoft Store

Per valutare le app rilasciate in Microsoft Store, usa l'app di Microsoft Store nel dispositivo Surface Hub per cercare e scaricare app.

> [!NOTE]
> L'uso dell'app di Microsoft Store non è il metodo consigliato per la distribuzione di app su larga scala nella tua organizzazione:
>
> - Per scaricare le app, è necessario accedere all'app di Microsoft Store con un account Microsoft o un account dell'organizzazione. Tuttavia, puoi connettere un account solo a un massimo di 10 dispositivi contemporaneamente. Se hai più di 10 dispositivi Surface Hub, dovrai creare più account o rimuovere i dispositivi dal tuo account tra un'installazione e l'altra.
> - Per installare le app, dovrai accedere manualmente all'app di Microsoft Store in ogni dispositivo Surface Hub di cui disponi.

#### <a name="to-browse-the-microsoft-store-on-surface-hub"></a>Per esplorare Microsoft Store in Surface Hub

1. Dal tuo dispositivo Surface Hub avvia **Impostazioni**.
2. Quando viene richiesto, digita le credenziali di amministratore del dispositivo.
3. Passare a **Surface Hub**  >  **app & funzionalità**.
4. Seleziona **Apri Store** e cerca l'app che stai cercando.

### <a name="download-app-packages-from-microsoft-store-for-business"></a>Scaricare pacchetti dell'app da Microsoft Store per le aziende

Per scaricare il pacchetto dell'app necessario per installare le app nel tuo dispositivo Surface Hub, visita [Microsoft Store per le aziende](https://www.microsoft.com/business-store). In Windows Store per le aziende puoi trovare, acquistare e gestire le app per i dispositivi Windows10 della tua organizzazione, inclusi i dispositivi Surface Hub.

> [!NOTE]
> Attualmente, Surface Hub supporta solo le app con licenza offline disponibili tramite lo Store per le aziende. Gli sviluppatori di app impostano la disponibilità delle licenze offline quando inviano le app.

Trova e acquista l'app che vuoi, quindi scarica:

- Il pacchetto dell'app con licenza offline (con estensione APPX o APPXBUNDLE)
- Il file di licenza *non codificato* (se usi i pacchetti di provisioning per installare l'app)
- Il file di licenza *codificato* (se usi MDM per distribuire l'app)
- Eventuali file di dipendenza necessari

Per altre informazioni, vedi [Scaricare un'app con licenza offline](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app).

### <a name="install-offline-licensed-apps-via-provisioning-package"></a>Installare app con licenza offline tramite il pacchetto di provisioning

Puoi installare manualmente le app con licenza offline scaricate da Windows Store per le aziende in alcuni dispositivi Surface Hub usando i pacchetti di provisioning. Usa Progettazione immagine e configurazione di Windows per creare un pacchetto di provisioning contenente il pacchetto dell'app e il file di licenza *non codificato* che hai scaricato dallo Store per le aziende. Per altre informazioni, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md).

### <a name="supported-mdm-provider"></a>Provider MDM supportato

Per distribuire le app in un vasto numero di dispositivi Surface Hub nella tua organizzazione, usa un provider MDM supportato. La tabella seguente mostra quali provider MDM supportano la distribuzione di pacchetti dell'app con licenza offline.

| Provider MDM                | Supporta i pacchetti dell'app con licenza offline? |
|-----------------------------|----------------------------------------|
| MDM locale con Configuration Manager (a partire dalla versione 1602) | Sì |
|
| Provider MDM di terze parti    | Verifica che il provider MDM supporti la distribuzione di pacchetti dell'app con licenza offline. |

> [!NOTE]
> Per distribuire app offline in remoto Microsoft Intune, vedere [Gestire le app VPP da Microsoft Store per le aziende](/mem/intune/apps/windows-store-for-business). Surface Hub la distribuzione dell'app supporta solo le app offline assegnate a un gruppo di dispositivi e usa il tipo di licenza Dispositivo.

## <a name="develop-and-test-apps"></a>Sviluppare e testare app

Questa sezione fornisce informazioni agli sviluppatori di app per testare le app Surface Hub.

### <a name="developer-mode"></a>Modalità sviluppatore

Per impostazione predefinita, Surface Hub esegue solo le app UWP che sono state pubblicate in Microsoft Store e ne portano la firma. Le app inviate a Microsoft Store sono sottoposte a test di sicurezza e conformità nell'ambito del [processo di certificazione delle app](/windows/uwp/publish/the-app-certification-process), in modo che il dispositivo Surface Hub sia salvaguardato dall'installazione di app dannose.

Abilitando la modalità sviluppatore, puoi installare anche app UWP firmate dallo sviluppatore.

> [!IMPORTANT]
> Dopo aver abilitato la modalità sviluppatore, dovrai reimpostare il dispositivo Surface Hub per disabilitarla. La reimpostazione del dispositivo rimuove tutti i file utente locali e le configurazioni e quindi reinstalla Windows.

#### <a name="to-turn-on-developer-mode"></a>Per attivare la modalità sviluppatore

1. Dal tuo dispositivo Surface Hub avvia **Impostazioni**.
2. Quando viene richiesto, digita le credenziali di amministratore del dispositivo.
3. Passa a **Aggiornamento e sicurezza** > **Per sviluppatori**.
4. Seleziona **Modalità sviluppatore** e accetta il messaggio di avviso.

### <a name="visual-studio"></a>Visual Studio

In fase di sviluppo, il modo più semplice per testare l'app in un dispositivo Surface Hub è con Visual Studio. La funzionalità di debug remoto di Visual Studio consente di rilevare i problemi nella tua app prima della distribuzione su larga scala. Per altre informazioni, vedi [Testare app di Surface Hub con Visual Studio](/windows/uwp/debug-test-perf/test-surface-hub-apps-using-visual-studio).

#### <a name="create-provisioning-package"></a>Creare il pacchetto di provisioning

Usa Visual Studio per creare un pacchetto dell'app per la tua app UWP, firmato usando un certificato di prova. Quindi usa Progettazione immagine e configurazione di Windows per creare un pacchetto di provisioning contenente il pacchetto dell'app. Per altre informazioni, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md).

## <a name="submit-apps-to-the-microsoft-store"></a>Inviare app a Microsoft Store

Quando un'app è pronta per il rilascio, gli sviluppatori devono inviarla e pubblicarla in Microsoft Store. Per altre informazioni, vedi [Pubblicare Windows app e giochi.](/windows/uwp/publish)

Durante l'invio dell'app, gli sviluppatori devono impostare le opzioni **Disponibilità famiglia di dispositivi** e **Gestione delle licenze per le organizzazioni** per garantire che l'app sarà disponibile per l'esecuzione in Surface Hub.

### <a name="to-set-device-family-availability"></a>Per impostare la disponibilità della famiglia di dispositivi

1. In [Windows Dev Center](https://developer.microsoft.com/windows) passa alla pagina di invio dell'app.
2. Seleziona **Pacchetti**.
3. In **Disponibilità famiglia di dispositivi** seleziona queste opzioni:

    - **Windows 10 Team**
    - **Consenti a Microsoft di decidere se rendere disponibile questa app a eventuali famiglie di dispositivi future**
  
   ![Immagine della pagina Disponibilità famiglia di dispositivi - parte del processo di invio dell'app a Microsoft Store.](images/device-family.png)  

   Per altre informazioni, vedi [Disponibilità famiglia di dispositivi](/windows/uwp/publish/upload-app-packages#device-family-availability).

### <a name="to-set-organizational-licensing"></a>Per impostare la gestione delle licenze per le organizzazioni

1. In [Windows Dev Center](https://developer.microsoft.com/windows) passa alla pagina di invio dell'app.

2. Seleziona **Prezzi e disponibilità**.

3. In Gestione delle licenze per le organizzazioni seleziona **Consenti gli acquisti di licenze disconnesse (offline) da parte delle organizzazioni**.

   ![Immagine della pagina Gestione delle licenze per le organizzazioni - parte del processo di invio dell'app a Microsoft Store.](images/sh-org-licensing.png)

   > [!NOTE]
   > L'opzione **Rendi disponibile la mia app alle organizzazioni con contratti multilicenza gestiti dallo Store (online)** è selezionata per impostazione predefinita.

   > [!NOTE]
   > Gli sviluppatori possono anche pubblicare app line-of-business direttamente per le aziende senza renderle disponibili su larga scala nello Store. Per altre informazioni, vedi [Distribuire app line-of-business alle aziende](/windows/uwp/publish/distribute-lob-apps-to-enterprises).

   Per altre informazioni, vedi [Opzioni relative alla gestione delle licenze per le organizzazioni](/windows/uwp/publish/organizational-licensing).

## <a name="summary"></a>Riepilogo

Esistono diversi modi per installare le app nel Surface Hub a seconda che tu sviluppi app, valuta le app su un numero limitato di dispositivi o distribuisca app in modo generale nella tua organizzazione. Questa tabella riepiloga i metodi supportati:

| Metodo di installazione             | Sviluppo di app | Valutazione di app in <br> alcuni dispositivi | Distribuzione di app su larga scala <br> nell'organizzazione |
| -------------------------- | --------------- | ------------------------------------- | ---------------------- |
| Visual Studio              | X |   |   |
| Pacchetto di provisioning       | X | X |   |
| App di Microsoft Store          |   | X |   |
| Provider MDM supportato     |   |   | X |

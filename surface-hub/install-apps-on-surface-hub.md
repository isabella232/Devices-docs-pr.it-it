---
title: Installare app nel dispositivo Microsoft Surface Hub
description: Gli amministratori possono installare app da Microsoft Store o da Microsoft Store per le aziende.
ms.assetid: 3885CB45-D496-4424-8533-C9E3D0EDFD94
ms.reviewer: ''
manager: laurawi
keywords: installare app, Microsoft Store, Microsoft Store per le aziende
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 10/23/2018
ms.localizationpriority: medium
audience: ITPro
ms.openlocfilehash: a6e791defed4970b9a1940580b5f80bbe4f006a4
ms.sourcegitcommit: f9e7c091a26df0f99500c0d8b6cf40a81133e4e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2021
ms.locfileid: "11470474"
---
# <a name="install-apps-on-your-microsoft-surface-hub"></a>Installare app nel dispositivo Microsoft Surface Hub

Puoi installare altre app nel tuo dispositivo Surface Hub in base alle esigenze del tuo team o dell'organizzazione. Esistono diversi metodi per installare le app, a seconda che tu stia sviluppando e testando un'app o distribuendone una rilasciata. Questo argomento descrive i metodi per l'installazione delle app per entrambi gli scenari.

Alcune cose da sapere sulle app in Surface Hub:
- Surface Hub esegue solo le [app della piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp). Le app create utilizzando [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) non verranno eseguite su Surface Hub.
- Le app devono essere destinate alla [famiglia di dispositivi universali](https://msdn.microsoft.com/library/windows/apps/dn894631) o alla famiglia di dispositivi Windows Team.
- Surface Hub supporta solo [le app con licenza offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) di Microsoft Store per le [aziende.](https://businessstore.microsoft.com/store)
- Per impostazione predefinita, le app devono riportare la firma dello Store per essere installate. Durante lo sviluppo e il test, puoi anche scegliere di eseguire app UWP firmate dallo sviluppatore inserendo il dispositivo in modalità sviluppatore.
- Quando invii un'app a Microsoft Store, gli sviluppatori devono impostare la disponibilità della famiglia di dispositivi e le opzioni di licenza dell'organizzazione per assicurarti che un'app sia disponibile per l'esecuzione in Surface Hub.
- Sono necessarie credenziali di amministratore per installare app in un dispositivo Surface Hub. Dato che il dispositivo è progettato per l'uso in spazi comuni come le sale riunioni, gli utenti non possono accedere a Microsoft Store per scaricare e installare app.


## <a name="develop-and-test-apps"></a>Sviluppare e testare app
Se stai sviluppando un'app personalizzata, esistono diverse opzioni per il test in Surface Hub.

### <a name="developer-mode"></a>Modalità sviluppatore
Per impostazione predefinita, Surface Hub esegue solo le app UWP che sono state pubblicate in Microsoft Store e ne portano la firma. Le app inviate a Microsoft Store sono sottoposte a test di sicurezza e conformità nell'ambito del [processo di certificazione delle app](https://msdn.microsoft.com/windows/uwp/publish/the-app-certification-process), in modo che il dispositivo Surface Hub sia salvaguardato dall'installazione di app dannose.
 
Abilitando la modalità sviluppatore, puoi installare anche app UWP firmate dallo sviluppatore.
 
> [!IMPORTANT]
> Dopo aver abilitato la modalità sviluppatore, dovrai reimpostare il dispositivo Surface Hub per disabilitarla. La reimpostazione del dispositivo rimuove tutti i file utente locali e le configurazioni e quindi reinstalla Windows.

**Per attivare la modalità sviluppatore** 
1. Dal tuo dispositivo Surface Hub avvia **Impostazioni**.
2. Quando viene richiesto, digita le credenziali di amministratore del dispositivo.
3. Passa a **Aggiornamento e sicurezza** > **Per sviluppatori**.
4. Seleziona **Modalità sviluppatore** e accetta il messaggio di avviso.

### <a name="visual-studio"></a>Visual Studio
In fase di sviluppo, il modo più semplice per testare l'app in un dispositivo Surface Hub è con Visual Studio. La funzionalità di debug remoto di Visual Studio consente di rilevare i problemi nella tua app prima della distribuzione su larga scala. Per altre informazioni, vedi [Testare app di Surface Hub con Visual Studio](https://msdn.microsoft.com/windows/uwp/debug-test-perf/test-surface-hub-apps-using-visual-studio).

### <a name="provisioning-package"></a>Pacchetto di provisioning
Usa Visual Studio per [creare un pacchetto dell'app](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) per la tua app UWP, firmato usando un certificato di prova. Quindi usa Progettazione immagine e configurazione di Windows per creare un pacchetto di provisioning contenente il pacchetto dell'app. Per altre informazioni, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md).


## <a name="submit-apps-to-the-microsoft-store"></a>Inviare app a Microsoft Store
Quando un'app è pronta per il rilascio, gli sviluppatori devono inviarla e pubblicarla in Microsoft Store. Per altre informazioni, vedi [Pubblicare app di Windows](https://developer.microsoft.com/store/publish-apps).

Durante l'invio dell'app, gli sviluppatori devono impostare le opzioni **Disponibilità famiglia di dispositivi** e **Gestione delle licenze per le organizzazioni** per garantire che l'app sarà disponibile per l'esecuzione in Surface Hub.

**Per impostare la disponibilità della famiglia di dispositivi**

1. In [Windows Dev Center](https://developer.microsoft.com) passa alla pagina di invio dell'app.

2. Seleziona **Pacchetti**.
3. In **Disponibilità famiglia di dispositivi** seleziona queste opzioni:
    
    - **Windows 10 Team**
    - **Consenti a Microsoft di decidere se rendere disponibile questa app a eventuali famiglie di dispositivi future**
  
   ![Immagine della pagina Disponibilità famiglia di dispositivi - parte del processo di invio dell'app a Microsoft Store.](images/device-family.png)  
    
   Per altre informazioni, vedi [Disponibilità famiglia di dispositivi](https://msdn.microsoft.com/windows/uwp/publish/upload-app-packages#device-family-availability).

**Per impostare la gestione delle licenze per le organizzazioni**

1. In [Windows Dev Center](https://developer.microsoft.com) passa alla pagina di invio dell'app.

2. Seleziona **Prezzi e disponibilità**.

3. In Gestione delle licenze per le organizzazioni seleziona **Consenti gli acquisti di licenze disconnesse (offline) da parte delle organizzazioni**.

   ![Immagine della pagina Gestione delle licenze per le organizzazioni - parte del processo di invio dell'app a Microsoft Store.](images/sh-org-licensing.png)

   > [!NOTE]
   > L'opzione **Rendi disponibile la mia app alle organizzazioni con contratti multilicenza gestiti dallo Store (online)** è selezionata per impostazione predefinita.

   > [!NOTE]
   > Gli sviluppatori possono anche pubblicare app line-of-business direttamente per le aziende senza renderle disponibili su larga scala nello Store. Per altre informazioni, vedi [Distribuire app line-of-business alle aziende](https://msdn.microsoft.com/windows/uwp/publish/distribute-lob-apps-to-enterprises).

   Per altre informazioni, vedi [Opzioni relative alla gestione delle licenze per le organizzazioni](https://msdn.microsoft.com/windows/uwp/publish/organizational-licensing).


## <a name="deploy-released-apps"></a>Distribuire app rilasciate

Sono disponibili diverse opzioni per installare le app che sono state rilasciate in Microsoft Store, a seconda che tu voglia valutarle solo in alcuni dispositivi o distribuirle su larga scala alla tua organizzazione.

Per installare app rilasciate:
- Scarica l'app tramite l'app di Microsoft Store oppure
- Scarica il pacchetto dell'app da Microsoft Store per le aziende e distribuiscilo usando un pacchetto di provisioning o un provider MDM supportato.

### <a name="microsoft-store-app"></a>App di Microsoft Store
Per valutare le app rilasciate in Microsoft Store, usa l'app di Microsoft Store nel dispositivo Surface Hub per cercare e scaricare app.

> [!NOTE]
> L'uso dell'app di Microsoft Store non è il metodo consigliato per la distribuzione di app su larga scala nella tua organizzazione:
> - Per scaricare le app, è necessario accedere all'app di Microsoft Store con un account Microsoft o un account dell'organizzazione. Tuttavia, puoi connettere un account solo a un massimo di 10 dispositivi contemporaneamente. Se hai più di 10 dispositivi Surface Hub, dovrai creare più account o rimuovere i dispositivi dal tuo account tra un'installazione e l'altra.
> - Per installare le app, dovrai accedere manualmente all'app di Microsoft Store in ogni dispositivo Surface Hub di cui disponi.

**Per esplorare Microsoft Store in Surface Hub** 
1. Dal tuo dispositivo Surface Hub avvia **Impostazioni**.
2. Quando viene richiesto, digita le credenziali di amministratore del dispositivo.
3. Passa a **Questo dispositivo** > **App e funzionalità**.
4. Seleziona **Apri Store**.

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

### <a name="provisioning-package"></a>Pacchetto di provisioning
Puoi installare manualmente le app con licenza offline scaricate da Windows Store per le aziende in alcuni dispositivi Surface Hub usando i pacchetti di provisioning. Usa Progettazione immagine e configurazione di Windows per creare un pacchetto di provisioning contenente il pacchetto dell'app e il file di licenza *non codificato* che hai scaricato dallo Store per le aziende. Per altre informazioni, vedi [Creare pacchetti di provisioning](provisioning-packages-for-certificates-surface-hub.md).

### <a name="supported-mdm-provider"></a>Provider MDM supportato
Per distribuire le app in un vasto numero di dispositivi Surface Hub nella tua organizzazione, usa un provider MDM supportato. La tabella seguente mostra quali provider MDM supportano la distribuzione di pacchetti dell'app con licenza offline.

| Provider MDM                | Supporta i pacchetti dell'app con licenza offline? |
|-----------------------------|----------------------------------------|
| MDM locale con Configuration Manager (a partire dalla versione 1602) | Sì |
|
| Provider MDM di terze parti    | Verifica che il provider MDM supporti la distribuzione di pacchetti dell'app con licenza offline. |

**Per distribuire le app in remoto con Microsoft Endpoint Configuration Manager**

> [!NOTE]
> Queste istruzioni si basano sul ramo corrente di Microsoft Endpoint Configuration Manager.

1. Registrare i dispositivi Surface Hub nella gestione MDM. Per altre informazioni, vedi [Gestire Surface Hub con un provider MDM.](manage-settings-with-mdm-for-surface-hub.md)

2. Scarica il pacchetto dell'app con licenza offline, il file di licenza *codificato* ed eventuali file di dipendenza necessari dallo Store per le aziende. Per altre informazioni, vedi [Scaricare un'app con licenza offline](https://technet.microsoft.com/itpro/windows/manage/distribute-offline-apps#download-an-offline-licensed-app). Salva i file scaricati nella stessa cartella in una condivisione di rete.

3. Nell'area di lavoro **Raccolta software** della console di Configuration Manager fai clic su **Panoramica** > **Gestione applicazioni** > **Applicazioni**.

4. Nella scheda **Home**, nel gruppo **Crea** fai clic su **Crea applicazione**.

5. Nella pagina **Generale** della **Creazione guidata applicazione** seleziona la casella di controllo **Rileva automaticamente le informazioni sull'applicazione dai file di installazione**.

6. Nell'elenco a discesa **Tipo** seleziona **Pacchetto app Windows (\*.appx, \*.appxbundle)**.

7. Nel campo **Posizione** specifica il percorso UNC nel formato \\server\condivisione\\nomefile per il pacchetto dell'app con licenza offline scaricato dallo Store per le aziende. In alternativa, fai clic su **Sfoglia** per cercare il pacchetto dell'app.

8. Nella pagina **Importazione informazioni** verifica le informazioni importate e fai clic su **Avanti**. Se necessario, puoi fare clic su **Indietro** per tornare indietro e correggere eventuali errori.

9. Nella pagina **Informazioni generali** inserisci ulteriori dettagli sull'app. Alcune di queste informazioni potrebbero essere già inserite se sono state ottenute automaticamente dal pacchetto dell'app.

10. Fai clic su **Avanti**, verifica le informazioni sull'applicazione nella pagina di riepilogo e quindi completa la Creazione guidata applicazione. 

11. Crea un tipo di distribuzione per l'applicazione. Per altre informazioni, vedi l'argomento relativo alla [creazione di tipi di distribuzione per l'applicazione](https://docs.microsoft.com/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).

12. Distribuisci l'applicazione ai tuoi dispositivi Surface Hub. Per ulteriori informazioni, vedere [Deploy applications with Microsoft Endpoint Configuration Manager.](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)

13. Se necessario, aggiorna l'app scaricando un nuovo pacchetto dallo Store per le aziende e pubblicando una revisione dell'applicazione in Configuration Manager. Per ulteriori informazioni, vedere [Aggiornare e ritirare le applicazioni con Microsoft Endpoint Configuration Manager.](https://technet.microsoft.com/library/mt595704.aspx) 

> [!NOTE] 
> Se si usa Microsoft Endpoint Configuration Manager (current branch), è possibile ignorare i passaggi precedenti connettendo Lo Store per le aziende a Configuration Manager. In questo modo, puoi sincronizzare l'elenco delle app acquistate con Configuration Manager, visualizzarle nella console di Configuration Manager e distribuirle come farei con qualsiasi altra app. Per altre informazioni, vedi [Gestire le app da Microsoft Store per le aziende con Configuration Manager.](https://technet.microsoft.com/library/mt740630.aspx)


## <a name="summary"></a>Riepilogo

Esistono diversi modi per installare le app nel dispositivo Surface Hub a seconda che tu sviluppi app, valutando le app su un numero limitato di dispositivi o distribuendo app su larga parte nell'organizzazione. Questa tabella riepiloga i metodi supportati:

| Metodo di installazione             | Sviluppo di app | Valutazione di app in <br> alcuni dispositivi | Distribuzione di app su larga scala <br> nell'organizzazione |
| -------------------------- | --------------- | ------------------------------------- | ---------------------- |
| Visual Studio              | X |   |   |
| Pacchetto di provisioning       | X | X |   |
| App di Microsoft Store          |   | X |   |
| Provider MDM supportato     |   |   | X |

## <a name="more-information"></a>Ulteriori informazioni

- [Post di blog: distribuire le app di Windows Store in Surface Hub tramite Intune](https://blogs.technet.microsoft.com/y0av/2018/01/18/7-2/)


## <a name="related-topics"></a>Argomenti correlati

[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

 

 






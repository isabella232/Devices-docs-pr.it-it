---
title: Aggiornamento del firmware Microsoft Surface Dock-informazioni tecniche per gli amministratori IT
description: Questo articolo spiega come usare Microsoft Surface Dock Update firmware per aggiornare il firmware di Surface Dock. Una volta installato nel dispositivo Surface, aggiornerà qualsiasi Dock di superficie collegato al dispositivo Surface.
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.reviewer: scottmca
manager: laurawi
ms.audience: itpro
ms.date: 8/07/2020
ms.openlocfilehash: 9069903421d6e621dfbc31cd1cfaffb045fa9f19
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114554"
---
# Aggiornamento del firmware Microsoft Surface Dock: informazioni tecniche per gli amministratori IT

> [!IMPORTANT]
> Questo articolo contiene le istruzioni tecniche per gli amministratori IT. Per gli utenti privati, vedere [come aggiornare il firmware di Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)   nel sito del supporto tecnico Microsoft. Le istruzioni del sito di supporto sono le stesse della procedura di installazione generale di seguito, ma in questo articolo sono disponibili altre informazioni per il monitoraggio, la verifica e la distribuzione dell'aggiornamento in più dispositivi in rete.

Questo articolo spiega come usare Microsoft Surface Dock Update firmware per aggiornare il firmware nel Dock Surface originale 1 e non si applica a Surface Dock 2. Una volta installato nel dispositivo Surface, aggiornerà qualsiasi Dock di superficie collegato al dispositivo Surface. 

Questo strumento sostituisce lo strumento Microsoft Surface Dock Updater precedente, precedentemente disponibile per il download come parte di strumenti di Surface. Lo strumento precedente è stato denominato Surface_Dock_Updater_vx.xx.xxx.x.msi (dove x indica il numero di versione) e non è più disponibile per il download e non deve essere usato.

## Installare l'aggiornamento del firmware di Surface Dock

Questa sezione descrive come installare manualmente l'aggiornamento del firmware.

> [!NOTE]
> Microsoft rilascia periodicamente le nuove versioni dell'aggiornamento del firmware di Surface Dock. Il file MSI non viene aggiornato autonomamente. Se il file MSI è stato distribuito in dispositivi Surface e viene rilasciata una nuova versione del firmware, sarà necessario distribuire la nuova versione.

1. Scaricare e installare l' [aggiornamento del firmware Microsoft Surface Dock](https://www.microsoft.com/download/details.aspx?id=46703).
    - L'aggiornamento richiede un dispositivo Surface che esegua Windows 10, versione 1803 o successiva.
    - L'installazione del file MSI può richiedere di riavviare Surface. Tuttavia, non è necessario riavviare il computer per eseguire l'aggiornamento.

2. Disconnettere il dispositivo Surface dal Dock Surface, attendere ~ 5 secondi e quindi riconnettersi. L'aggiornamento del firmware di Surface Dock aggiornerà il Dock in modo invisibile all'utente in background. Il processo può richiedere alcuni minuti per il completamento e continuerà anche se interrotto. 

## Monitorare l'aggiornamento del firmware di Surface Dock

Questa sezione è facoltativa e offre una panoramica su come monitorare l'installazione dell'aggiornamento del firmware. 

Per monitorare l'aggiornamento:

1. Aprire il Visualizzatore eventi, individuare i **registri di Windows > applicazione**e quindi in **azioni** nel riquadro destro fare clic su **filtro log corrente**, immettere **SurfaceDockFwUpdate** accanto a **origini eventi**e quindi fare clic su **OK**.

2. Digitare il comando seguente a un prompt dei comandi con privilegi elevati:

    ```cmd
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```
3. Installare l'aggiornamento come descritto nella [sezione successiva](#install-the-surface-dock-firmware-update) di questo articolo.
4. L'evento 2007 con il testo seguente indica un aggiornamento riuscito: **aggiornamento del firmware terminato. hr = 0 DriverTelementry eventCode = 2007**. 
    - Se l'aggiornamento non riesce, l'ID evento 2007 verrà visualizzato come evento di **errore** anziché **informazioni**. Inoltre, la versione riportata nel registro di sistema di Windows non sarà aggiornata.
5. Al termine dell'aggiornamento, i valori DWORD aggiornati verranno visualizzati nel registro di sistema di Windows, in modo che corrispondano alla versione corrente dello strumento. Per informazioni dettagliate, vedere la sezione [riferimenti alle versioni](#versions-reference) in questo articolo. Ad esempio:
    - Component10CurrentFwVersion 0x04ac3970 (78395760)
    - Component20CurrentFwVersion 0x04915a70 (76634736)

>[!TIP]
>Se viene visualizzato "la descrizione per l'ID evento xxxx da SurfaceDockFwUpdate di origine non è possibile trovare" nel testo dell'evento, questa operazione è prevista e può essere ignorata.

Vedere anche le sezioni seguenti in questo articolo: 
  - [Come verificare il completamento dell'aggiornamento del firmware](#how-to-verify-completion-of-the-firmware-update)
  - [Registrazione eventi](#event-logging)
  - [Suggerimenti per la risoluzione dei problemi](#troubleshooting-tips)
  - [Riferimenti alle versioni](#versions-reference)

## Distribuzione di rete

Puoi usare i comandi di Windows Installer (Msiexec.exe) per distribuire l'aggiornamento del firmware di Surface dock a più dispositivi in tutta la rete. Quando si usa Microsoft endpoint Configuration Manager o un altro strumento di distribuzione, immettere la sintassi seguente per verificare che l'installazione sia silenziosa:

- **Msiexec.exe/i \<path to msi file\> /quiet/norestart** 

  Ad esempio:
  ```
  msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
  ```

  > [!NOTE]
  > Per impostazione predefinita, un file di log non viene creato. Per creare un file di log, sarà necessario accodare "/l*v [path]". Ad esempio: Msiexec.exe/i \<path to msi file\> /l*v%windir%\logs\ SurfaceDockFWI. log "

  Per altre informazioni, vedere la documentazione relativa alle [Opzioni della riga di comando](https://docs.microsoft.com/windows/win32/msi/command-line-options) .

> [!IMPORTANT]
> Se si vuole che il dock per Surface venga aggiornato usando qualsiasi altro metodo, vedere [aggiornare Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) per i dettagli.

## Distribuzione di Intune

Puoi usare Intune per distribuire l'aggiornamento del firmware di Surface Dock ai tuoi dispositivi. Prima di tutto è necessario convertire il file MSI nel formato intunewin, come descritto nella documentazione seguente: [Intune standalone-gestione delle app Win32](https://docs.microsoft.com/intune/apps/apps-win32-app-management).

Usare il comando seguente:
  - **msiexec/i \<path to msi file\> /quiet/q**

## Come verificare il completamento dell'aggiornamento del firmware

Il firmware di Surface Dock è costituito da due componenti:

- **Component10:** Firmware dell'unità di controllo micro (MCU)
- **Component20:** Visualizza il firmware della porta (DP).

Il completamento dell'aggiornamento del firmware di Surface Dock restituisce i nuovi valori delle chiavi del registro di sistema per questi componenti del firmware.

**Per verificare gli aggiornamenti:**

1. Aprire regedit e passare al percorso del registro di sistema seguente:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters**

2. Cercare le chiavi del registro di sistema: **Component10CurrentFwVersion e Component20CurrentFwVersion**, che fanno riferimento al firmware attualmente presente nel dispositivo.

   ![Processo di installazione dell'aggiornamento del firmware Surface Dock](images/regeditDock.png)

3. Verificare che i nuovi valori della chiave del registro di sistema corrispondano ai valori della chiave del registro di sistema aggiornati elencati nel riferimento alle versioni alla fine del documento. Se i valori corrispondono, il firmware è stato aggiornato correttamente.

4. Se non è possibile verificare, esaminare la registrazione degli eventi e i suggerimenti per la risoluzione dei problemi nella sezione successiva.

## Registrazione eventi

**Tabella 1. File di log per l'aggiornamento del firmware di Surface Dock**

| Log                              | Location                               | Note                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Log degli aggiornamenti del firmware di Surface Dock | Il percorso deve essere specificato (Vedi nota) | Le versioni precedenti di questo strumento hanno scritto eventi per le applicazioni e i servizi Logs\Microsoft Surface Dock Updater.                                                                                                  |
| Log di installazione di dispositivi Windows       | %windir%\inf\setupapi.dev.log           | Per altre informazioni sull'uso del log di installazione del dispositivo, vedere la documentazione relativa alla [registrazione di Setupapi](https://docs.microsoft.com/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) . |


**Tabella 2. ID log eventi per l'aggiornamento del firmware di Surface Dock**<br>
Gli eventi vengono registrati nel log eventi applicazione.  Nota: le versioni precedenti di questo strumento hanno scritto eventi per le applicazioni e i servizi Logs\Microsoft Surface Dock Updater.

| ID evento | Tipo evento                                                           |
| -------- | -------------------------------------------------------------------- |
| 2001     | È stato avviato l'aggiornamento del firmware Dock.                                    |
| 2002     | Aggiornamento del firmware di ancoraggio ignorato perché il Dock è noto per essere aggiornato. |
| 2003     | L'aggiornamento del firmware Dock non è riuscito a ottenere la versione del firmware.                 |
| 2004     | Query sulla versione del firmware.                                       |
| 2005     | Non è stato possibile avviare l'aggiornamento del firmware Dock.                                |
| 2006     | Impossibile inviare coppie di offerte/payload.                                  |
| 2007     | Aggiornamento del firmware terminato.                                            |
| 2008     | INIZIARE a collegare la telemetria.                                                |
| 2011     | FINE della telemetria del Dock.                                                  |

## Suggerimenti per la risoluzione dei problemi

- Scollegare completamente l'alimentazione per Surface dock dall'alimentazione CA per reimpostare Surface Dock.
- Scollegare tutte le periferiche eccetto il dock di superficie.
- Disinstallare qualsiasi aggiornamento del firmware di Surface dock corrente e quindi installare la versione più recente.
- Assicurarsi che Surface dock sia disconnesso e quindi consentire un tempo sufficiente per completare l'aggiornamento come monitorato tramite un LED nella porta Ethernet del Dock. Attendere che il LED smetta di lampeggiare prima di scollegare Surface dock dall'alimentazione.
- Connettere Surface dock a un dispositivo diverso per verificare se è in grado di aggiornare il Dock.

## Riferimenti alle versioni

>[!NOTE]
>Il file di installazione viene rilasciato con il formato di denominazione seguente: **Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (es: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) e viene installato per impostazione predefinita in C:\Program Files\SurfaceUpdate.

### Versione 1.53.139.0
*Data di rilascio: 4 agosto 2020*

Questa versione dell'aggiornamento del firmware di Surface Dock include correzioni di bug e supporto per:
- Aggiornamento della superficie di ancoraggio 1 con Surface Pro X. 
   > [!NOTE]
   > Se si sta usando Surface Pro X, scaricare il. ARM64 Build. Per tutti gli altri dispositivi, usare la build AMD64. 
 


### Versione 1.42.139 
*Data di rilascio: 18 2019 settembre*

Questa versione, contenuta in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, aggiorna il firmware in background. 
**Valori della chiave del registro di sistema aggiornati:**<br>

- Component10CurrentFwVersion è stato aggiornato a **4ac3970**.
- Component20CurrentFwVersion è stato aggiornato a **4a1d570**.

Aggiunge il supporto per Surface Pro 7 e Surface laptop 3.

## Versioni legacy

### Versione 2.23.139.0
*Data di rilascio: 10 ottobre 2018*

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiungere il supporto per Surface Pro 6
- Aggiungere il supporto per Surface laptop 2


### Versione 2.22.139.0
*Data di rilascio: 26 luglio 2018*

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aumentare l'affidabilità degli aggiornamenti
- Aggiungere il supporto per Surface go

### Versione 2.12.136.0
*Data di rilascio: 29 gennaio 2018*

Questa versione di Surface Dock Updater aggiunge il supporto per:
* Aggiornamento del firmware del chipset principale di Surface Dock
* Aggiornamento del firmware DisplayPort di Surface Dock
* Stabilità di visualizzazione migliorata per gli schermi esterni se usato con Surface Book o Surface Book 2

Inoltre, l'installazione di questa versione di Surface Dock Updater nei dispositivi Surface Book include:
* Aggiornamento del firmware per la base di Surface Book
* Aggiunta del supporto per gli aggiornamenti del firmware di Surface Dock con miglioramenti per i dispositivi Surface Book


### Versione 2.9.136.0
*Data di rilascio: 3 novembre 2017*

Questa versione di Surface Dock Updater aggiunge il supporto per:

* Aggiornamento del firmware DisplayPort di Surface Dock
* Risolve un problema con l'audio tramite schede di porta video passive

### Versione 2.1.15.0
*Data di rilascio: 19 giugno 2017*

Questa versione di Surface Dock Updater aggiunge il supporto per:

* Surface Laptop
* Surface Pro

### Versione 2.1.6.0
*Data di rilascio: 7 aprile 2017*

Questa versione di Surface Dock Updater aggiunge il supporto per:

* Aggiornamento del firmware DisplayPort di Surface Dock
* Richiede Windows 10

### Versione 2.0.22.0
*Data di rilascio: 21 ottobre 2016*

Questa versione di Surface Dock Updater aggiunge il supporto per:

* Aggiornamento del firmware USB di Surface Dock
* Miglioramento dell'affidabilità di Ethernet, audio e porte USB

### Versione 1.0.8.0
*Data di rilascio: 26 aprile 2016*

Questa versione di Surface Dock Updater aggiunge il supporto per:

* Aggiornamento del firmware del chipset principale di Surface Dock
* Aggiornamento del firmware DisplayPort di Surface Dock


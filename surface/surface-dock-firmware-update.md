---
title: Aggiornamento firmware di Microsoft Surface Dock 1
description: Questo articolo spiega come usare Microsoft Surface Dock Firmware Update per installare e gestire il firmware nel Surface Dock 1 originale. Se installato nel dispositivo Surface, aggiornerà i dispositivi Surface Dock 1 collegati al dispositivo Surface.
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
ms.date: 2/08/2021
ms.openlocfilehash: 544aa8ab7cb9bb443f368bfbbcecb1fa256d32c5
ms.sourcegitcommit: ad08299d14810db746514f01d977a81fc5a3961e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/29/2021
ms.locfileid: "11708757"
---
# <a name="surface-dock-1-firmware-update"></a>Aggiornamento del firmware di Surface Dock 1

Questo articolo spiega come usare Aggiornamento firmware di Microsoft Surface Dock 1 per installare e gestire il firmware nel Surface Dock 1 originale. Se installato nel dispositivo Surface, aggiornerà i dispositivi Surface Dock 1 collegati al dispositivo Surface.

> [!NOTE]
> Questo articolo non si applica a [Surface Dock 2,](surface-dock-whats-new.md)che riceve automaticamente gli aggiornamenti tramite Windows Update o usando Microsoft Endpoint Configuration Manager o altri strumenti di distribuzione MSI.

Questo strumento sostituisce lo strumento Microsoft Surface Dock Updater precedente, precedentemente disponibile per il download come parte di Surface Tools per IT. Lo strumento precedente è stato denominato Surface_Dock_Updater_vx.xx.xxx.x.msi (dove x indica il numero di versione) e non è più disponibile per il download e non deve essere utilizzato.

> [!IMPORTANT]
> Questo articolo contiene istruzioni tecniche per gli amministratori IT. Se sei un utente principale, vedi [Come aggiornare il firmware del Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock)nel sito del supporto   Microsoft. Le istruzioni nel sito di supporto sono le stesse della procedura di installazione generale riportata di seguito, ma in questo articolo sono disponibili informazioni aggiuntive per il monitoraggio, la verifica e la distribuzione dell'aggiornamento in più dispositivi in una rete.

## <a name="install-surface-dock-1-firmware-update"></a>Installare l'aggiornamento del firmware di Surface Dock 1

Questa sezione descrive come installare manualmente l'aggiornamento del firmware in Surface Dock 1.

> [!TIP]
> Microsoft rilascia periodicamente nuove versioni di Surface Dock 1 Firmware Update. Il file MSI non viene aggiornato automaticamente. Se hai distribuito MSI nei dispositivi Surface e viene rilasciata una nuova versione del firmware, dovrai distribuire la nuova versione.

1. Vai a [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) e scarica e installa il file .msi denominato **Surface_Dock_FwUpdate..** seguito dalla versione appropriata. Se stai eseguendo Surface Pro X, scarica la build **.arm64.** Per tutti gli altri dispositivi, usa la build **.amd64.**  

    - L'aggiornamento richiede un dispositivo Surface Windows 10 versione 1803 o successiva.
    - L'installazione del file MSI potrebbe richiedere il riavvio di Surface. Tuttavia, il riavvio non è necessario per eseguire l'aggiornamento.

2. Scollegare il dispositivo Surface dal Surface Dock, attendere circa 5 secondi e quindi riconnettersi. L'aggiornamento del firmware di Surface Dock 1 aggiornerà il dock automaticamente in background. Il completamento del processo può richiedere alcuni minuti e continuerà anche se interrotto.

## <a name="monitor-the-surface-dock-1-firmware-update"></a>Monitorare l'aggiornamento del firmware di Surface Dock 1

Questa sezione è facoltativa e fornisce una panoramica su come monitorare l'installazione dell'aggiornamento del firmware.

Per monitorare l'aggiornamento:

1. Aprire il Visualizzatore eventi, accedere Windows Registri > Applicazione **** e quindi in Azioni nel riquadro destro fare clic su Filtra registro **corrente,** immettere **SurfaceDockFwUpdate** accanto **a**Origini eventi **e**quindi fare clic su **OK.**

2. Al prompt dei comandi con privilegi elevati digitare il comando seguente:

    ```console
    Reg query "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters"
    ```

3. Installare l'aggiornamento come descritto nella [sezione successiva](#install-surface-dock-1-firmware-update) di questo articolo.

4. L'evento 2007 con il testo seguente indica un aggiornamento riuscito: Aggiornamento **firmware completato. hr=0 DriverTelementry EventCode = 2007**.

   Se l'aggiornamento non riesce, l'ID evento 2007 verrà visualizzato come evento **Error** anziché **come Information.** Inoltre, la versione riportata nel Registro Windows non sarà corrente.

5. Al termine dell'aggiornamento, i valori DWORD aggiornati verranno visualizzati nel Registro di Windows, corrispondente alla versione corrente dello strumento. Per informazioni [dettagliate,](#versions-reference) vedere la sezione Di riferimento sulle versioni in questo articolo. Ad esempio:

    - Component10CurrentFwVersion 0x04ac3970 (78395760)
    - Component20CurrentFwVersion 0x04915a70 (76634736)

>[!TIP]
>Se viene visualizzato "Impossibile trovare la descrizione per l'ID evento xxxx dall'origine SurfaceDockFwUpdate" nel testo dell'evento, questa operazione è prevista e può essere ignorata.

Vedere anche le sezioni seguenti in questo articolo:

- [Come verificare il completamento dell'aggiornamento del firmware](#how-to-verify-completion-of-the-firmware-update)
  - [Registrazione eventi](#event-logging)
  - [Suggerimenti per la risoluzione dei problemi](#troubleshooting-tips)
  - [Informazioni di riferimento sulla versione](#versions-reference)

## <a name="network-deployment"></a>Distribuzione di rete

Puoi usare i comandi Windows Installer (Msiexec.exe) per distribuire Surface Dock 1 Firmware Update a più dispositivi nella rete. Quando si utilizza Microsoft Endpoint Configuration Manager o un altro strumento di distribuzione, immettere la sintassi seguente per assicurarsi che l'installazione non sia invisibile all'utente:

- **Msiexec.exe /i \<path to msi file\> /quiet /norestart**

Ad esempio:

```console
msiexec /i "\\share\folder\Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi" /quiet /norestart
```

> [!NOTE]
> Un file di registro non viene creato per impostazione predefinita. Per creare un file di registro, è necessario aggiungere "/l*v [percorso]". Ad esempio: Msiexec.exe /i \<path to msi file\> /l*v %windir%\logs\ SurfaceDockFWI.log"

Per ulteriori informazioni, vedere la documentazione [relativa alle opzioni della riga di](/windows/win32/msi/command-line-options) comando.

> [!IMPORTANT]
> Se vuoi mantenere il Surface Dock aggiornato con qualsiasi altro metodo, fai riferimento a [Aggiornare il Surface Dock](https://support.microsoft.com/help/4023478/surface-update-your-surface-dock) per informazioni dettagliate.

## <a name="intune-deployment"></a>Distribuzione di Intune

Puoi usare Intune per distribuire Surface Dock 1 Firmware Update ai dispositivi. Prima di tutto sarà necessario convertire il file MSI nel formato .intunewin, come descritto nella documentazione seguente: Intune Autonomo - Gestione app [Win32](/intune/apps/apps-win32-app-management).

Utilizzare il comando seguente:

- **msiexec /i \<path to msi file\> /quiet /q**

## <a name="how-to-verify-completion-of-the-firmware-update"></a>Come verificare il completamento dell'aggiornamento del firmware

Il firmware del surface dock è costituito da due componenti:

- **Component10:** Firmware MCU (Micro Controller Unit)
- **Component20:** Firmware della porta di visualizzazione (DP).

Il corretto completamento dell'aggiornamento del firmware di Surface Dock 1 determina nuovi valori delle chiavi del Registro di sistema per questi componenti del firmware.

### <a name="to-verify-updates"></a>Per verificare gli aggiornamenti

1. Aprire Regedit e passare al percorso del Registro di sistema seguente:

    - **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\WUDF\Services\SurfaceDockFwUpdate\Parameters**

2. Cercare le chiavi del Registro di **sistema: Component10CurrentFwVersion e Component20CurrentFwVersion**, che fanno riferimento al firmware attualmente nel dispositivo.

   ![Processo di installazione dell'aggiornamento del firmware di Surface Dock 1](images/regeditDock.png)

3. Verificare che i nuovi valori delle chiavi del Registro di sistema corrispondano ai valori delle chiavi del Registro di sistema aggiornati elencati nel riferimento Versioni alla fine di questo documento. Se i valori corrispondono, il firmware è stato aggiornato correttamente.

4. Se non è possibile verificare, consultare i suggerimenti per la registrazione degli eventi e la risoluzione dei problemi nella sezione successiva.

## <a name="event-logging"></a>Registrazione eventi

### <a name="table-1-log-files-for-surface-dock-1-firmware-update"></a>Tabella 1. File di registro per l'aggiornamento del firmware di Surface Dock 1

| Log                              | Percorso                               | Note                                                                                                                                                                                                         |
| -------------------------------- | --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Log di aggiornamento firmware di Surface Dock 1 | Il percorso deve essere specificato (vedere la nota) | Nelle versioni precedenti di questo strumento gli eventi sono stati scritti nei registri applicazioni e servizi\Microsoft Surface Dock Updater.                                                                                                  |
| Windows Log installazione dispositivo       | %windir%\inf\setupapi.dev.log           | Per ulteriori informazioni sull'utilizzo del registro di installazione dei dispositivi, vedere la [documentazione relativa alla registrazione SetupAPI.](/windows-hardware/drivers/install/setupapi-logging--windows-vista-and-later-) |

### <a name="table-2-event-log-ids-for-surface-dock-1-firmware-update"></a>Tabella 2. ID del registro eventi per l'aggiornamento del firmware di Surface Dock 1

Gli eventi vengono registrati nel registro eventi applicazioni.  Nota: le versioni precedenti di questo strumento hanno scritto eventi nei registri applicazioni e servizi\Microsoft Surface Dock Updater.

| ID evento | Tipo evento                                                           |
| -------- | -------------------------------------------------------------------- |
| 2001     | L'aggiornamento del firmware del dock è stato avviato.                                    |
| 2002     | Aggiornamento firmware dock ignorato perché il dock è noto per essere aggiornato. |
| 2003     | Aggiornamento firmware dock non riuscito per ottenere la versione del firmware.                 |
| 2004     | Esecuzione di query sulla versione del firmware.                                       |
| 2005     | Impossibile avviare l'aggiornamento del firmware dock.                                |
| 2006     | Impossibile inviare coppie offerta/payload.                                  |
| 2007     | Aggiornamento firmware completato.                                            |
| 2008     | Telemetria del dock BEGIN.                                                |
| 2011     | Telemetria del dock END.                                                  |

## <a name="troubleshooting-tips"></a>Suggerimenti per la risoluzione dei problemi

- Scollegare completamente l'alimentazione per surface dock dall'alimentazione CA per reimpostare il Surface Dock.
- Disconnetti tutte le periferiche ad eccezione del Surface Dock.
- Disinstallare qualsiasi aggiornamento firmware di Surface Dock 1 corrente e quindi installare la versione più recente.
- Assicurati che il Surface Dock sia scollegato e quindi consenti tempo sufficiente per il completamento dell'aggiornamento come monitorato tramite un LED nella porta Ethernet del dock. Attendi fino a quando il LED smette di lampeggiare prima di scollegare Surface Dock dall'alimentazione.
- Connessione il Surface Dock a un dispositivo diverso per vedere se è in grado di aggiornare il dock.

## <a name="versions-reference"></a>Informazioni di riferimento sulla versione

>[!NOTE]
>Il file di installazione viene rilasciato con il formato di denominazione ** seguente:Surface_Dock_FwUpdate_X.XX.XXX_Win10_XXXXX_XX.XXX.XXXXX_X.MSI** (ad esempio: Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.msi) e viene installato per impostazione predefinita in C:\Programmi\SurfaceUpdate.

### <a name="version-1531390"></a>Versione 1.53.139.0

#### <a name="release-date-august-4-2020"></a>Data di rilascio: 4 agosto 2020

Questa versione di Surface Dock 1 Firmware Update include correzioni di bug e supporto per:

- Aggiornamento di Surface Dock 1 con Surface Pro X.

#### <a name="registry-key-values"></a>Valori delle chiavi del Registro di sistema

I valori del Registro di sistema che indicano lo stato degli aggiornamenti del firmware rimangono invariati rispetto alla versione precedente di questo strumento:

- Component10CurrentFwVersion aggiornato a **4ac3970**.
- Component20CurrentFwVersion aggiornato a **4a1d570**.

### <a name="version-142139"></a>Versione 1.42.139

#### <a name="release-date-september-18-2019"></a>Data di rilascio: 18 settembre 2019

Questa versione, contenuta in Surface_Dock_FwUpdate_1.42.139_Win10_17134_19.084.31680_0.MSI, aggiorna il firmware in background.

#### <a name="updated-registry-key-values"></a>Valori aggiornati delle chiavi del Registro di sistema

- Component10CurrentFwVersion aggiornato a **4ac3970**.
- Component20CurrentFwVersion aggiornato a **4a1d570**.

Aggiunge il supporto per Surface Pro 7 e Surface Laptop 3.

## <a name="legacy-versions"></a>Versioni legacy

### <a name="version-2231390"></a>Versione 2.23.139.0

#### <a name="release-date-10-october-2018"></a>Data di rilascio: 10 ottobre 2018

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiungere il supporto per Surface Pro 6
- Aggiungere il supporto per Surface Laptop 2

### <a name="version-2221390"></a>Versione 2.22.139.0

#### <a name="release-date-26-july-2018"></a>Data di rilascio: 26 luglio 2018

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aumentare l'affidabilità degli aggiornamenti
- Aggiungere il supporto per Surface Go

### <a name="version-2121360"></a>Versione 2.12.136.0

#### <a name="release-date-29-january-2018"></a>Data di rilascio: 29 gennaio 2018

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiornamento del firmware del chipset principale di Surface Dock

- Aggiornamento del firmware DisplayPort di Surface Dock

- Stabilità di visualizzazione migliorata per gli schermi esterni se usato con Surface Book o Surface Book 2

Inoltre, l'installazione di questa versione di Surface Dock Updater nei dispositivi Surface Book include:

- Aggiornamento del firmware per la base di Surface Book

- Aggiunta del supporto per gli aggiornamenti del firmware di Surface Dock con miglioramenti per i dispositivi Surface Book

### <a name="version-291360"></a>Versione 2.9.136.0

#### <a name="release-date-november-3-2017"></a>Data di rilascio: 3 novembre 2017

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiornamento del firmware DisplayPort di Surface Dock

- Risolve un problema con l'audio tramite schede di porta video passive

### <a name="version-21150"></a>Versione 2.1.15.0

#### <a name="release-date-june-19-2017"></a>Data di rilascio: 19 giugno 2017

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Surface Laptop

- Surface Pro

### <a name="version-2160"></a>Versione 2.1.6.0

#### <a name="release-date-april-7-2017"></a>Data di rilascio: 7 aprile 2017

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiornamento del firmware DisplayPort di Surface Dock

- Richiede Windows 10

### <a name="version-20220"></a>Versione 2.0.22.0

#### <a name="release-date-october-21-2016"></a>Data di rilascio: 21 ottobre 2016

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiornamento del firmware USB di Surface Dock

- Miglioramento dell'affidabilità di Ethernet, audio e porte USB

### <a name="version-1080"></a>Versione 1.0.8.0

#### <a name="release-date-april-26-2016"></a>Data di rilascio: 26 aprile 2016

Questa versione di Surface Dock Updater aggiunge il supporto per:

- Aggiornamento del firmware del chipset principale di Surface Dock

- Aggiornamento del firmware DisplayPort di Surface Dock

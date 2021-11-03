---
title: Eseguire la console dell'app da riga di comando con Surface Diagnostic Toolkit for Business
description: Come eseguire surface diagnostic Toolkit in una console dei comandi
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 1410760fc89d4654322f2bc9b738e87e839251c3
ms.sourcegitcommit: 94e11386d7034c6bc5fe753f7bebf61a9c815509
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2021
ms.locfileid: "12154121"
---
# <a name="run-command-line-app-console-with-surface-diagnostic-toolkit-for-business"></a>Eseguire la console dell'app da riga di comando con Surface Diagnostic Toolkit for Business

L'esecuzione di Surface Diagnostic Toolkit (SDT) al prompt dei comandi richiede il download della console dell'app SDT. Dopo l'installazione, è possibile eseguire SDT al prompt dei comandi tramite la console dei comandi di Windows (cmd.exe) o utilizzando Windows PowerShell, incluso PowerShell Integrated Scripting Environment (ISE), che fornisce il supporto per il completamento automatico di comandi, copia/incolla e altre funzionalità.  Per un elenco dei dispositivi Surface supportati in SDT, fai riferimento a [Deploy Surface Diagnostic Toolkit for Business.](surface-diagnostic-toolkit-business.md)

>[!NOTE]
>Per eseguire SDT usando i comandi, devi avere eseguito l'accesso all'account amministratore o aver eseguito l'accesso a un account membro del gruppo Administrator nel dispositivo Surface.

## <a name="running-sdt-app-console"></a>Esecuzione della console dell'app SDT

1. Scarica e installa la console dell'app SDT dalla pagina [di download di Surface Tools per IT.](https://www.microsoft.com/download/details.aspx?id=46703)

- Per i dispositivi Intel/AMD, scarica: **Microsoft.Surface.Diagnostics.App.Console.v2.168.139.0.exe**
- Per ARM dispositivi, scaricare: **Microsoft.Surface.Diagnostics.App.Console.v2.168.139.0_x86.exe**

2. Utilizzare il prompt dei Windows (cmd.exe) o Windows PowerShell per:

- Raccogliere tutti i file di registro
- Eseguire la diagnostica dell'integrità utilizzando Best Practice Analyzer
- Verificare la disponibilità di aggiornamenti del firmware o dei driver mancanti

>[!NOTE]
>In questa versione, la console dell'app SDT supporta solo comandi singoli. L'esecuzione di più opzioni della riga di comando richiede l'esecuzione separata dell'exe della console per ogni comando.

Per impostazione predefinita, i file di output vengono salvati nello stesso percorso dell'app console. Fare riferimento alla tabella seguente per un elenco completo dei comandi.

Comando | Note
--- | ---
-DataCollector "file di output" | Raccoglie i dettagli di sistema in un file ZIP. "file di output" è il percorso del file per creare il file ZIP dei dettagli di sistema.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-bpa "file di output" | Controlla diverse impostazioni e indicatori di integrità nel dispositivo. "file di output" è il percorso del file per creare il report HTML.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-windowsupdate | Controlla Windows server online Update per verificare la presenza di aggiornamenti del firmware e/o dei driver mancanti.<br><br>**Esempio**:<br>Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate
-warranty "file di output" | Controlla le informazioni sulla garanzia nel dispositivo (valide o non valide). Il "file di output" facoltativo è il percorso del file per creare il file XML. <br><br>**Esempio**: <br>Microsoft.Surface.Diagnostics.App.Console.exe –warranty "warranty.xml"

>[!NOTE]
>Per eseguire la console dell'app SDT in remoto nei dispositivi di destinazione, puoi usare uno strumento di gestione della configurazione come Microsoft Endpoint Configuration Manager. In alternativa, puoi creare un file .zip contenente l'app console e i comandi della console appropriati e distribuirti in base ai processi di distribuzione software dell'organizzazione.

## <a name="running-best-practice-analyzer"></a>Esecuzione di Best Practice Analyzer

È possibile eseguire i test BPA tra componenti chiave quali BitLocker, Avvio protetto e Trusted Platform Module (TPM) e quindi eseguire l'output dei risultati in un file condivisibile. Lo strumento genera una serie di tabelle con intestazioni con codice a colori e descrittori di condizione insieme a indicazioni su come affrontare la risoluzione del problema.

- Verde indica che il componente è in esecuzione in una condizione ottimale (ottimale).
- Arancione indica che il componente non è in esecuzione in una condizione ottimale (non ottimale).
- Il rosso indica che il componente è in uno stato anomalo.

### <a name="sample-bpa-results-output"></a>Output dei risultati BPA di esempio

<table>
<tr><th colspan="2"><font color="00ff00">BitLocker</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se BitLocker è abilitato nell'unità di sistema.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Protezione on</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>È consigliabile abilitare BitLocker per proteggere i dati.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Avvio protetto</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se l'avvio protetto è abilitato.</td></tr>
<tr><td><strong>Valore:</strong></td><td>True</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>È consigliabile abilitare l'avvio protetto per proteggere il PC.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Trusted Platform Module</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Garantisce che il TPM sia funzionante.</td></tr>
<tr><td><strong>Valore:</strong></td><td>True</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Senza un TPM funzionale, le funzioni basate sulla sicurezza come BitLocker potrebbero non funzionare correttamente.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Standby connesso</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se la modalità standby connesso è abilitata.</td></tr>
<tr><td><strong>Valore:</strong></td><td>True</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Lo standby connesso consente a un dispositivo Surface di ricevere aggiornamenti e notifiche senza essere usato. Per un'esperienza ottimale, è consigliabile attivare lo standby connesso.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se Bluetooth è abilitato.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Abilitato</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Modalità debug</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se il sistema operativo è in modalità debug.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>L'opzione di avvio di debug abilita o disabilita il debug del kernel Windows sistema operativo. L'attivazione di questa opzione può causare instabilità del sistema e impedire la riproduzione di supporti protetti da DRM (digital rights managemend).</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Test Signing</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se la firma di test è abilitata.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Test Signing è un'Windows di avvio che deve essere usata solo per testare i driver non rilasciati.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Combinazione per il risparmio di energia attiva</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica che sia attiva la combinazione per il risparmio di energia corretta.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Bilanciato</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>È consigliabile utilizzare il piano di alimentazione "bilanciato" per ottimizzare la produttività e la durata della batteria.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se il dispositivo è aggiornato con gli Windows automatici.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Microsoft Silverlight (KB4023307), Aggiornamento delle definizioni per Windows Defender Antivirus - KB2267602 (Definizione 1.279.1433.0)</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="ff9500">Non ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>L'aggiornamento alle finestre più recenti garantisce il firmware e i driver più recenti. È consigliabile mantenere sempre aggiornato il dispositivo</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Spazio libero sul disco rigido</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica la presenza di spazio libero insufficiente sul disco rigido.</td></tr>
<tr><td><strong>Valore:</strong></td><td>66%</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Per ottenere prestazioni ottimali, il disco rigido deve avere almeno il 10% della capacità come spazio libero.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Dispositivi non funzionanti</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Elenco dei dispositivi non funzionanti in Gestione dispositivi.</td></tr>
<tr><td><strong>Valore:</strong></td><td></td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>I dispositivi non funzionanti in Gestione dispositivi possono causare problemi imprevedibili con i dispositivi Surface, ad esempio, ma non solo, nessun risparmio energetico per il rispettivo componente hardware.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Monitor esterno</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica la presenza di un monitor esterno che potrebbe avere problemi di compatibilità.</td></tr>
<tr><td><strong>Valore:</strong></td><td></td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Contattare il produttore dell'attrezzatura originale per verificare la compatibilità con il dispositivo Surface.</td></tr>
</table>

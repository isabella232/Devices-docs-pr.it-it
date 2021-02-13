---
title: Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi
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
ms.openlocfilehash: f3856499bd769b96e22c0a47323c984eb38d8a18
ms.sourcegitcommit: 7e028c1e66fb393dc0e8917dac257ce95e5e9ce7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2021
ms.locfileid: "11327330"
---
# Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi

L'esecuzione di Surface Diagnostic Toolkit (SDT) al prompt dei comandi richiede il download della console dell'app SDT. Dopo l'installazione, puoi eseguire SDT da un prompt dei comandi tramite la console dei comandi di Windows (cmd.exe) o usando Windows PowerShell, incluso PowerShell Integrated Scripting Environment (ISE), che fornisce il supporto per il completamento automatico di comandi, copia/incolla e altre funzionalità.  Per un elenco dei dispositivi Surface supportati in SDT, fai riferimento a [Deploy Surface Diagnostic Toolkit for Business.](surface-diagnostic-toolkit-business.md)

>[!NOTE]
>Per eseguire SDT con i comandi, devi aver eseguito l'accesso all'account amministratore o a un account membro del gruppo Administrator nel dispositivo Surface.

## Esecuzione della console dell'app SDT

Scarica e installa la console dell'app SDT dalla pagina [di download di Surface Tools per IT.](https://www.microsoft.com/download/details.aspx?id=46703) Puoi usare il prompt dei comandi di Windows (cmd.exe) o Windows PowerShell per: 

- Raccogliere tutti i file di registro.
- Eseguire la diagnostica dell'integrità utilizzando Best Practice Analyzer.
- Controllare l'aggiornamento per gli aggiornamenti mancanti del firmware o del driver.

>[!NOTE]
>In questa versione, la console dell'app SDT supporta solo comandi singoli. L'esecuzione di più opzioni della riga di comando richiede l'esecuzione separata del file exe della console per ogni comando. 

Per impostazione predefinita, i file di output vengono salvati nello stesso percorso dell'app console. Fare riferimento alla tabella seguente per un elenco completo dei comandi.

Comando | Note
--- | ---
-DataCollector "file di output" | Raccoglie i dettagli di sistema in un file ZIP. "file di output" è il percorso del file per creare il file ZIP dei dettagli di sistema.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-bpa "file di output" | Controlla diverse impostazioni e indicatori di integrità nel dispositivo. "file di output" è il percorso del file per creare il report HTML.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-windowsupdate | Verifica la presenza di aggiornamenti mancanti del firmware e/o dei driver nei server windows update online.<br><br>**Esempio**:<br>Microsoft.Surface.Diagnostics.App.Console.exe -windowsupdate
-warranty "output file" | Controlla le informazioni sulla garanzia nel dispositivo (valide o non valide). Il "file di output" facoltativo è il percorso del file xml. <br><br>**Esempio**: <br>Microsoft.Surface.Diagnostics.App.Console.exe –warranty "warranty.xml"


>[!NOTE]
>Per eseguire la console dell'app SDT in remoto nei dispositivi di destinazione, puoi usare uno strumento di gestione della configurazione come Microsoft Endpoint Configuration Manager. In alternativa, puoi creare un file ZIP contenente l'app console e i comandi della console appropriati e distribuirti in base ai processi di distribuzione software dell'organizzazione. 

## Esecuzione di Best Practice Analyzer 

Puoi eseguire test BPA tra componenti chiave come BitLocker, Avvio protetto e Trusted Platform Module (TPM) e quindi output dei risultati in un file condivisibile. Lo strumento genera una serie di tabelle con intestazioni codificate a colori e descrittori di condizioni, insieme a indicazioni su come affrontare la risoluzione del problema. 

- Verde indica che il componente è in esecuzione in una condizione ottimale (ottimale).
- Arancione indica che il componente non è in esecuzione in una condizione ottimale (non ottimale).
- Il rosso indica che il componente è in uno stato anomalo. 

### Output dei risultati BPA di esempio

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
<tr><td><strong>Descrizione:</strong></td><td>Controlla se lo standby connesso è abilitato.</td></tr>
<tr><td><strong>Valore:</strong></td><td>True</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Lo standby connesso consente a un dispositivo Surface di ricevere aggiornamenti e notifiche mentre non viene usato. Per un'esperienza ottimale, è consigliabile attivare lo standby connesso.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se la Bluetooth è abilitata.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Abilitato</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Modalità debug</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se il sistema operativo è in modalità debug.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>L'opzione di avvio del debug abilita o disabilita il debug in kernel del sistema operativo Windows. L'attivazione di questa opzione può causare instabilità del sistema e impedire la riproduzione di contenuti multimediali protetti da DRM (gestione dei diritti digitali).</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Test Signing</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se la firma di prova è abilitata.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Firma di test è un'impostazione di avvio di Windows che deve essere usata solo per testare i driver non definitiva.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Combinazione per il risparmio di energia attiva</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica che la combinazione per il risparmio di energia corretta sia attiva.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Bilanciato</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>È consigliabile usare il piano per il risparmio di energia "bilanciato" per ottimizzare la produttività e la durata della batteria.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se il dispositivo è aggiornato con gli aggiornamenti di Windows.</td></tr>
<tr><td><strong>Valore:</strong></td><td>Microsoft Silverlight (KB4023307), Aggiornamento delle definizioni per Windows Defender Antivirus - KB2267602 (Definizione 1.279.1433.0)</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="ff9500">Non ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>L'aggiornamento alle finestre più recenti assicura che il firmware e i driver più recenti siano aggiornati. È consigliabile mantenere sempre aggiornato il dispositivo</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Spazio libero sul disco rigido</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica la presenza di spazio libero insufficiente sul disco rigido.</td></tr>
<tr><td><strong>Valore:</strong></td><td>66%</td></tr>
<tr><td><strong>Condizione:</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Linee guida:</strong></td><td>Per ottenere prestazioni ottimali, il disco rigido deve avere almeno il 10% della sua capacità come spazio libero.</td></tr>
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

---
title: Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi
description: Come eseguire Surface Diagnostic Toolkit in una console di comandi
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
ms.openlocfilehash: 6a56e1231ff5d2f672305d7166bbfa46d1bc0354
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832240"
---
# Eseguire Toolkit di diagnostica per Surface per le aziende usando i comandi

L'uso di Surface Diagnostic Toolkit (SDT) al prompt dei comandi richiede il download della console dell'app STD. Dopo l'installazione, è possibile eseguire SDT al prompt dei comandi tramite la console dei comandi di Windows (cmd.exe) o usare Windows PowerShell, incluso PowerShell Integrated Scripting Environment (ISE), che fornisce il supporto per il completamento automatico di comandi, copia/incolla e altre funzionalità.  Per un elenco dei dispositivi Surface supportati in SDT, vedere [distribuire Toolkit di diagnostica superficie per le aziende](surface-diagnostic-toolkit-business.md).

>[!NOTE]
>Per eseguire l'uso di SDT usando i comandi, è necessario avere effettuato l'accesso all'account di amministratore o accedere a un account membro del gruppo di amministratori nel dispositivo Surface.

## Console dell'app SDT in uso

Scaricare e installare la console della app SDT dalla [pagina di download di Surface Tools per it](https://www.microsoft.com/download/details.aspx?id=46703). È possibile usare il prompt dei comandi di Windows (cmd.exe) o Windows PowerShell per: 

- Raccogliere tutti i file di log.
- Eseguire la diagnostica di integrità con Best Practice Analyzer.
- Controllare l'aggiornamento per gli aggiornamenti del firmware o del driver mancanti.

>[!NOTE]
>In questa versione la console dell'app SDT supporta solo comandi singoli. L'uso di più opzioni della riga di comando richiede l'uso di console exe separatamente per ogni comando. 

Per impostazione predefinita, i file di output vengono salvati nella stessa posizione dell'app console. Fare riferimento alla tabella seguente per un elenco completo dei comandi.

Comando | Note
--- | ---
-DataCollector "file di output" | Raccoglie i dettagli di sistema in un file zip. "file di output" è il percorso del file per creare file zip per i dettagli di sistema.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -DataCollector SDT_DataCollection.zip`
-BPA "file di output" | Controlla diverse impostazioni e indicatori di integrità nel dispositivo. "file di output" è il percorso del file per creare il report HTML.<br><br>**Esempio**:<br>`Microsoft.Surface.Diagnostics.App.Console.exe -bpa BPA.html`
-WindowsUpdate | Controlla i server Windows Update online per gli aggiornamenti mancanti del firmware e/o del driver.<br><br>**Esempio**:<br>Microsoft.Surface.Diagnostics.App.Console.exe-windowsupdate
-garanzia "file di output" | Controlla le informazioni sulla garanzia nel dispositivo (valido o non valido). Il file di output facoltativo è il percorso del file per creare il file XML. <br><br>**Esempio**: <br>Microsoft.Surface.Diagnostics.App.Console.exe-garanzia "warranty.xml"


>[!NOTE]
>Per eseguire la console dell'app SDT in remoto nei dispositivi di destinazione, è possibile usare uno strumento di gestione della configurazione, ad esempio Microsoft endpoint Configuration Manager. In alternativa, puoi creare un file con estensione zip contenente l'app console e i comandi di console appropriati e distribuire per i processi di distribuzione del software dell'organizzazione. 

## Gestione di Best Practice Analyzer 

È possibile eseguire test BPA tra componenti chiave, ad esempio BitLocker, Secure Boot e Trusted Platform Module (TPM), quindi restituire i risultati in un file condivisibile. Lo strumento genera una serie di tabelle con intestazioni con codifica a colori e descrittori di condizioni, oltre a indicazioni su come affrontare la risoluzione del problema. 

- Verde indica che il componente viene eseguito in una condizione ottimale (ottimale).
- Orange indica che il componente non è in uso in una condizione ottimale (non ottimale).
- Rosso indica che il componente è in uno stato anormale. 

### Output dei risultati BPA di esempio

<table>
<tr><th colspan="2"><font color="00ff00">BitLocker</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Controlla se BitLocker è abilitato nell'unità di sistema.</td></tr>
<tr><td><strong>Valore</strong></td><td>Protezione in</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>È vivamente consigliabile abilitare BitLocker per la protezione dei dati.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Avvio protetto</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se è abilitato l'avvio sicuro.</td></tr>
<tr><td><strong>Valore</strong></td><td>True</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>È vivamente consigliabile abilitare l'avvio sicuro per proteggere il PC.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Trusted Platform Module</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Garantisce che il TPM sia funzionale.</td></tr>
<tr><td><strong>Valore</strong></td><td>True</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>Senza un TPM funzionale, le funzioni basate sulla sicurezza, ad esempio BitLocker, potrebbero non funzionare correttamente.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Standby connesso</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se la modalità standby connessa è abilitata.</td></tr>
<tr><td><strong>Valore</strong></td><td>True</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>La modalità standby connessa consente a un dispositivo Surface di ricevere aggiornamenti e notifiche durante l'uso. Per una migliore esperienza, la modalità standby connessa deve essere abilitata.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Bluetooth</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se il Bluetooth è abilitato.</td></tr>
<tr><td><strong>Valore</strong></td><td>Abilitato</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td></td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Modalità di debug</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se il sistema operativo è in modalità di debug.</td></tr>
<tr><td><strong>Valore</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>L'opzione debug boot Abilita o Disabilita il debug del kernel del sistema operativo Windows. L'abilitazione di questa opzione può causare l'instabilità del sistema e può impedire la riproduzione di contenuti multimediali protetti DRM (Digital Rights managemend).</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Test di firma</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se la firma del test è abilitata.</td></tr>
<tr><td><strong>Valore</strong></td><td>Normale</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>La firma del test è un'impostazione di avvio di Windows che deve essere usata solo per testare i driver di pre-release.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Piano di alimentazione attiva</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica che sia attivo il piano di alimentazione corretto.</td></tr>
<tr><td><strong>Valore</strong></td><td>Equilibrato</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>Si consiglia vivamente di usare il piano di alimentazione "bilanciato" per massimizzare la produttività e la durata della batteria.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="ff9500">Windows Update</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se il dispositivo è aggiornato con gli aggiornamenti di Windows.</td></tr>
<tr><td><strong>Valore</strong></td><td>Microsoft Silverlight (KB4023307), aggiornamento della definizione per Windows Defender Antivirus-KB2267602 (definizione 1.279.1433.0)</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="ff9500">Non ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>L'aggiornamento alle ultime finestre consente di verificare che siano presenti i driver e i firmware più recenti. È consigliabile mantenere sempre aggiornato il dispositivo</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Spazio libero su disco rigido</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica la disponibilità di spazio su disco rigido gratuito.</td></tr>
<tr><td><strong>Valore</strong></td><td>66%</td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>Per ottenere prestazioni ottimali, il disco rigido dovrebbe avere almeno il 10% della propria capacità di spazio libero.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Dispositivi non funzionanti</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Elenco di dispositivi non funzionanti in gestione dispositivi.</td></tr>
<tr><td><strong>Valore</strong></td><td></td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>I dispositivi non funzionanti in gestione dispositivi possono causare problemi imprevedibili con dispositivi di superficie come, ma non limitati a, nessun risparmio di energia per il componente hardware corrispondente.</td></tr>
</table>

<table>
<tr><th colspan="2"><font color="00ff00">Monitor esterno</font></th></tr>
<tr><td><strong>Descrizione:</strong></td><td>Verifica se un monitor esterno può avere problemi di compatibilità.</td></tr>
<tr><td><strong>Valore</strong></td><td></td></tr>
<tr><td><strong>Condizione</strong></td><td><font color="00ff00">Ottimale</font></td></tr>
<tr><td><strong>Indicazioni</strong></td><td>Verificare con il produttore di apparecchiature originale la compatibilità con il dispositivo Surface.</td></tr>
</table>

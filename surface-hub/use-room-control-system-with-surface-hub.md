---
title: Uso di un sistema di controllo della sala (Surface Hub)
description: Puoi usare i sistemi di controllo della sala con il tuo dispositivo Microsoft Surface Hub.
ms.assetid: DC365002-6B35-45C5-A2B8-3E1EB0CB8B50
ms.reviewer: ''
manager: laurawi
keywords: sistema di controllo della sala, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0e3b1706e58edb6e37156eda8d06fb0faefa4c91
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832654"
---
# Uso di un sistema di controllo della sala (Surface Hub)


Puoi usare i sistemi di controllo della sala con il tuo dispositivo Microsoft Surface Hub.

L'uso di un sistema di controllo della sala con il dispositivo Surface Hub implica la connessione dell'hardware di controllo della sala a Surface Hub, generalmente tramite la porta seriale RJ11 nella parte inferiore di Surface Hub.

## Impostazioni del terminale

Per la connessione al pannello di controllo di un sistema di controllo della sala, non è necessario configurare le impostazioni del terminale in Surface Hub. Se vuoi connettere un PC o un portatile al dispositivo Surface Hub e inviare comandi seriali da Surface Hub, puoi usare un programma di emulazione del terminale come Tera Term o PuTTY. 

| Impostazione | Valore |
| --- | --- |
| Velocità in baud | 115200 |
| Bit di dati | 8 | 
| Bit di stop | 1 |
| Parità | nessuna |
| Controllo di flusso | nessuno |
| Avanzamento riga | ogni ritorno a capo |
 

## Diagramma di collegamento

Puoi usare un connettore RJ-11 (6P6C) standard per la connessione della porta seriale di Surface Hub a un sistema di controllo della sala. Si tratta del metodo consigliato. Anche se sconsigliato, puoi usare in alternativa un cavo a 4 conduttori RJ-11.

Questo diagramma mostra la configurazione corretta dei pin per un cavo da RJ-11 (6P6C) a DB9.

![Immagine che mostra il diagramma di collegamento.](images/room-control-wiring-diagram.png)

## Set di comandi

I sistemi di controllo della sala usano scenari di sale riunioni comuni per i comandi. I comandi provengono dal sistema di controllo della sala e vengono comunicati tramite una connessione seriale a un dispositivo Surface Hub. I comandi sono basati su ASCII e il dispositivo Surface Hub riconoscerà le modifiche dello stato.

Sono disponibili i modificatori di comando seguenti. I comandi terminano con un carattere di nuova riga (\n). Le risposte alle modifiche dello stato non attivate direttamente da un comando della porta di gestione possono arrivare in qualsiasi momento.

| Modificatore | Risultato |
| --- | --- |
| + | Consente di incrementare un valore |
| - | Consente di ridurre un valore |
| = | Consente di impostare un valore discreto |
| ? | Consente di richiedere un valore corrente |
 

## Alimentazione

Surface Hub può trovarsi in uno degli stati di alimentazione seguenti.

| Stato | Stato Energy Star| Descrizione |
| --- | --- | --- |
| 0 | S5 | Inattivo |
| 1 | - | Acceso (indeterminato) |
| 2 | S3 | Sospensione |
| 5 | S0 | Pronto |


In modalità PC di sostituzione, gli stati di alimentazione sono solo Pronto e Inattivo e comportano solo la modifica dello schermo. La porta di gestione non può essere usata per alimentare il PC di sostituzione. 

| Stato | Stato Energy Star| Descrizione |
| --- | --- | --- |
| 0 | S5 | Disattivato |
| 5 | S0 | Pronto |

Per un dispositivo di controllo, qualsiasi valore diverso da 5/Pronto deve essere considerato corrispondente a Inattivo. Ogni comando PowerOn genera due modifiche e risposte di stato. 

| Comando | Modifica di stato| Risposta |
| --- | --- | --- |
| PowerOn | Il dispositivo si accende (schermo + PC).</br></br>Il servizio PC indica al controller SMC che il PC è pronto. |  Power=0</br></br>Power=5 |
| PowerOff | Il dispositivo passa allo stato ambientale (PC acceso, schermo oscurato). |  Power=0 |
| Power? |  Il controller SMC segnala l'ultimo stato di alimentazione noto. |  Power=<#> |



## Luminosità

Il livello di luminosità corrente è compreso nell'intervallo da 0 a 100.

Le modifiche ai livelli di luminosità possono essere inviate da un sistema di controllo della sala o da un altro sistema.

| Comando | Modifica di stato |Risposta |
| --- | --- | --- |
| Brightness+ | Il controller SMC (System Management Controller) invia il comando per aumentare la luminosità.</br></br>Il servizio PC nel sistema di controllo della sala invia notifica al controller SMC del nuovo livello di luminosità. |  Brightness = 51 |
| Brightness- |  Il controller SMC invia il comando per ridurre la luminosità.</br></br>Il servizio PC invia notifica al controller SMC del nuovo livello di luminosità. | Brightness = 50 |

##  <a name="volume"></a>Volume

Il livello di volume corrente è compreso nell'intervallo da 0 a 100.

Le modifiche ai livelli del volume possono essere inviate da un sistema di controllo della sala o da un altro sistema.

>[!NOTE]
>Il comando Volume consente di controllare solo il volume per la modalità PC di sostituzione o integrato e non dalle [origini Guest](connect-and-display-with-surface-hub.md).

| Comando | Modifica di stato | Risposta</br>(Solo in [modalità PC di sostituzione](connect-and-display-with-surface-hub.md#replacement-pc-mode)) |
| --- | --- | --- |
| Volume+ |  Il controller SMC invia il comando per aumentare il volume.</br></br>Il servizio PC invia notifica al controller SMC del nuovo livello del volume. |  Volume = 51 |
| Volume- |  Il controller SMC invia il comando per ridurre il volume.</br></br>Il servizio PC invia notifica al controller SMC del nuovo livello del volume. |  Volume = 50 |


 

## Disattivazione dell'audio

L'audio può essere disattivato.

| Comando | Modifica di stato | Risposta |
| --- | --- | --- |
| AudioMute+ |  Il controller SMC invia il comando di disattivazione dell'audio.</br></br>Il servizio PC invia notifica al controller SMC della disattivazione dell'audio. |  nessuna |


 

## Origine video

Possono essere usate diverse origini di visualizzazione.

| Stato | Descrizione | 
| --- | --- |
| 0 |  Onboard PC |
| 1 |  DisplayPort |
| 2 |  HDMI |
| 3 |  VGA |


 

Le modifiche all'origine di visualizzazione possono essere inviate da un sistema di controllo della sala o da un altro sistema.

| Comando | Modifica di stato | Risposta |
| --- | --- | --- |
| Source=# |  Il controller SMC passa all'origine desiderata.</br></br>Il servizio PC invia notifica al controller SMC del cambiamento dell'origine di visualizzazione. |  Source=&lt;#&gt; |
| Source+ |  Il controller SMC passa all'origine di input attiva successiva.</br></br>Il servizio PC invia notifica al controller SMC dell'origine di input corrente. |  Source=&lt;#&gt; |
| Source- | Il controller SMC passa all'origine di input attiva precedente.</br></br>Il servizio PC invia notifica al controller SMC dell'origine di input corrente. |  Source=&lt;#&gt; |
| Source? |  Il controller SMC richiede l'origine di input attiva al servizio PC.</br></br>Il servizio PC invia notifica al controller SMC dell'origine di input corrente. | Source=&lt;#&gt; |

## Errori

Gli errori vengono restituiti nel formato indicato in questa tabella.

| Errore | Note |
| --- | --- |
| Errore: Comando sconosciuto '&lt;input&gt;'. |  L'istruzione contiene un comando iniziale sconosciuto. Ad esempio, &quot;VOL+&quot; non sarebbe valido e restituirebbe &quot;Errore: Comando sconosciuto 'VOL'&quot;. |
| Errore: Operatore sconosciuto '&lt;input&gt;'. |  L'istruzione contiene un operatore sconosciuto. Ad esempio, &quot;Volume!&quot; non sarebbe valido e restituirebbe &quot; Errore: Operatore sconosciuto "!"&quot;. |
| Errore: Parametro sconosciuto '&lt;input&gt;'. |  L'istruzione contiene un parametro sconosciuto. Ad esempio, &quot;Volume=abc&quot; non sarebbe valido e restituirebbe &quot;Errore: Parametro sconosciuto 'abc'&quot;. |
| Errore: Comando non disponibile in caso di disattivazione '&lt;input&gt;'. |  Quando il dispositivo Surface Hub è disattivato, i comandi diversi da un comando di alimentazione restituiscono questo errore. Ad esempio, &quot;Volume+&quot; non sarebbe valido e restituirebbe &quot;Errore: Comando non disponibile in caso di disattivazione 'Volume'&quot;. |


 

##  <a name="related-topics"></a>Argomenti correlati


[Gestire Microsoft Surface Hub](manage-surface-hub.md)

[Manuale dell'amministratore di Microsoft Surface Hub](surface-hub-administrators-guide.md)

 

 






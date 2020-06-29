---
title: 'Termina sessione: terminare una riunione Surface Hub'
description: Per terminare una riunione Surface Hub, toccare Termina sessione. Surface Hub azzera lo stato delle applicazioni, del sistema operativo e dell'interfaccia utente in modo da poter iniziare un'altra riunione.
keywords: Fatto, terminare una riunione Surface Hub, concludere una riunione Surface Hub, pulire una riunione Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: b18bc4b15b8a3925aeecdd9999b09b61011d1db5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833693"
---
# Terminare una riunione Surface Hub con Termina sessione
Surface Hub è un dispositivo di collaborazione progettato per essere usato nelle aree riunioni da diversi gruppi di persone. Al termine di una riunione, gli utenti possono toccare **Termina sessione** per cancellare tutti i dati sensibili e preparare il dispositivo per la riunione successiva. Surface Hub azzererà o reimposterà gli stati degli elementi seguenti:
- Applicazioni
- Sistema operativo
- Interfaccia utente

Questo argomento spiega in che modo ognuno di questi stati viene reimpostato toccando l'opzione **Termina sessione**.

## Applicazioni
Quando avvii un'app in Surface Hub, l'app viene archiviata in memoria, mentre i dati vengono archiviati a livello di applicazione. Durante la sessione (o la riunione), i dati rimangono a disposizione di tutti gli utenti fino a quando non viene rimossa o sovrascritta la data. Se si seleziona l'opzione **Termina sessione**, lo stato delle applicazioni di Surface Hub viene annullato mediante la chiusura delle applicazioni, l'eliminazione della cronologia del browser, la reimpostazione delle applicazioni e la rimozione dei registri di Skype.

### Chiudere le applicazioni
Surface Hub chiude tutte le finestre visibili, incluse le applicazioni Win32 e UWP (Universal Windows Platform). La fase di chiusura delle applicazioni usa la visualizzazione multitasking per interrogare le finestre visibili. Le finestre Win32 che non si chiudono entro un determinato intervallo di tempo vengono chiuse con **TerminateProcess**. 
   
### Eliminare la cronologia del browser
Surface Hub usa l'opzione di eliminazione della cronologia del browser disponibile in Edge per cancellare la cronologia di Edge e i dati memorizzati nella cache. Rispetto all'eliminazione manuale della cronologia del browser, con l'opzione **Termina sessione** vengono anche cancellati gli stati delle applicazioni e rimossi i dati prima dell'inizio della sessione o della riunione successiva. 
 
### Reimpostare le applicazioni
L'opzione **Termina sessione** reimposta lo stato di ogni applicazione installata in Surface Hub. Con questa operazione vengono cancellate tutte le attività in background, i dati delle applicazioni, le notifiche e le finestre di dialogo del consenso. Le applicazioni vengono inoltre reimpostate allo stato di prima esecuzione per i successivi utenti di Surface Hub.  
 
### Rimuovere i registri di Skype
Skype non archivia informazioni personali in Surface Hub. Le informazioni vengono archiviate nel servizio Skype in conformità alle linee guida esistenti di Skype for Business. Se si seleziona l'opzione **Termina sessione** gli unici dati rimossi sono le informazioni di registrazione a Skype locali, che comprendono anche i registri e i registri multimediali della piattaforma UCCP (Unified Communications Client Platform).   

## Sistema operativo
Nel sistema operativo sono presenti numerose informazioni sullo stato delle sessioni che devono essere cancellate dopo ogni riunione Surface Hub. 

### File system
I partecipanti alla riunione possono accedere a un set limitato di directory in Surface Hub. Se si seleziona l'opzione **Termina sessione**, Surface Hub annulla le directory seguenti:<br>
- Musica
- Video
- Documenti
- Immagini
- Download

Surface Hub cancella anche le directory seguenti, in cui molte applicazioni scrivono spesso dei dati:
- Desktop
- Preferiti
- Recenti
- Documenti pubblici
- Musica pubblica
- Video musicali
- Download pubblici

### Credenziali
Le credenziali utente archiviate in **TokenBroker**, **PasswordVault** o **Gestione credenziali** vengono eliminate quando tocchi **Termina sessione**.

## Interfaccia utente
Se si seleziona l'opzione **Termina sessione**, le impostazioni dell'interfaccia utente vengono reimpostate ai valori predefiniti. 

### Elementi dell'interfaccia utente
- Azioni rapide reimpostate allo stato predefinito
- Notifiche di tipo avviso popup cancellate
- Livelli di volume reimpostati
- Larghezza della barra laterale reimpostata
- Layout della modalità tablet reimpostato
- Disconnettere l'utente dalle riunioni e dai file di Office 365

### Accessibilità
Se si seleziona l'opzione **Termina sessione**, le app e le funzionalità di accessibilità vengono ripristinate alle impostazioni predefinite.
- Filtro tasti
- Contrasto elevato
- Tasti permanenti
- Segnali acustici
- Controllo puntatore
- Lente di ingrandimento
- Assistente vocale

### Appunti
I dati copiati negli Appunti durante la sessione vengono cancellati. 

## Domande frequenti
**Cosa accade se mi dimentico di toccare Termina sessione al termine di una riunione e, in seguito, qualcun altro usa Surface Hub?**<br>
Surface Hub rimuove i contenuti di una riunione solo quando gli utenti toccano **Termina sessione**. Se termini la riunione senza avere toccato **Termina sessione**, il dispositivo tornerà alla schermata iniziale dopo alcuni minuti. Dalla schermata iniziale gli utenti hanno la possibilità di riprendere la sessione precedente o di avviarne una nuova. È inoltre possibile disattivare la capacità di riprendere una sessione se **Termina sessione** non viene premuto.

**I documenti possono essere recuperati?**<br> Se selezioni l'opzione **Termina sessione**, i file vengono rimossi dal disco fisso come qualsiasi altro dato eliminato da un'unità disco rigido. Per recuperarli dal disco rigido è necessario un software di terze parti, ma il recupero dei file non è una funzionalità supportata in Surface Hub. Per evitare la perdita di dati, salva sempre i dati di cui hai bisogno prima di terminare una riunione.

**Le azioni di azzeramento generate dall'opzione Termina sessione sono conformi allo standard di pulizia e sanificazione DoD 5220.22-M, definito dal Dipartimento della Difesa statunitense?**<br>
No. Le azioni di azzeramento generate dall'opzione **Termina sessione** non sono attualmente conformi a questo standard.  
  

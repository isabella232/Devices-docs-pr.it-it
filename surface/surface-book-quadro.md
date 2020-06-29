---
title: Panoramica tecnica della GPU di Surface Book 3
description: In questo articolo vengono illustrate le funzionalità avanzate abilitate da NVIDIA Quadro RTX 3000 in Seleziona Surface Book 3 per le aziende da 15 pollici.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 5/06/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: d93008acfdbddd9d47c3a948f2fec392ac83d025
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832271"
---
# Panoramica tecnica di Surface Book 3 quadro RTX 3000

Surface Book 3 for business alimentato dalla NVIDIA® Quadro RTX™ 3000 GPU è costruito per professionisti che necessitano di rendering in tempo reale, accelerazione AI, grafica avanzata e prestazioni di calcolo in un fattore di forma portatile. Quadro RTX 3000 cambia radicalmente le operazioni che è possibile eseguire con il nuovo libro Surface 3:

- **Ray Tracing** : produce rendering, disegni e animazioni mozzafiato più velocemente che mai con i core da 30 RT per il ray tracing con accelerazione hardware.
- **Intelligenza artificiale** -rimuovere attività ridondanti e noiose e calcolare il lavoro intensivo con i core di tensore di 240 per l'ai.
- **Grafica avanzata e tecnologia Compute** -esperienza di velocità e interattività notevoli durante la grafica più gravosa e calcolare i carichi di lavoro con core CUDA di 1.920 e 6GB di memoria GDDR6.

## Soluzione Grade Enterprise

Di fondamentale importanza per i clienti commerciali, quadro RTX 3000 offre una soluzione completamente professionale che combina le funzionalità di Ray tracing e Deep Learning con una soluzione di gestione e supporto di livello aziendale integrata. I driver quadro sono testati e certificati per più di 100 applicazioni professionali, offrendo un ulteriore livello di garanzia della qualità per convalidare la stabilità, l'affidabilità e le prestazioni.
 
Quadro include strumenti aziendali dedicati per la gestione remota dei dispositivi Surface Book 3 con quadro RTX 3000. Gli amministratori IT possono configurare in remoto sistemi grafici, configurazioni di salvataggio/ripristino, monitorare continuamente i sistemi grafici ed eseguire, se necessario, la risoluzione dei problemi remoti. Queste funzionalità insieme agli strumenti di distribuzione aiutano a massimizzare il tempo di uptime e a minimizzare i requisiti di supporto IT.
 
NVIDIA sviluppa e gestisce i driver per le aziende (ODE) ottimizzati per l'organizzazione, testati e convalidati per consentire a livello aziendale stabilità, affidabilità, disponibilità e supporto per la disponibilità di prodotti estesa. Ogni versione del driver include più di 2.000 giorni di test con le applicazioni professionali e i test case, oltre alla certificazione WHQL. Le minacce alla sicurezza vengono continuamente monitorate e vengono rilasciati aggiornamenti di sicurezza regolari per la protezione dalle vulnerabilità appena scoperte. Inoltre, i driver quadro vengono sottoposti a un ulteriore livello di test per Surface Engineering prima del rilascio tramite Windows Update.
 

## Creato per carichi di lavoro intensivi di calcolo

Surface Book 3 con quadro RTX 3000 offre le migliori prestazioni grafiche di qualsiasi computer portatile di Surface, consentendo ai professionisti avanzati di lavorare ovunque.
 
- **Professionisti creativi come designer e animatori.** Quadro RTX consente il rendering in tempo reale della qualità cinematica tramite le API di Ray Tracing ottimizzate per Turing, come NVIDIA OptiX, Microsoft DXR e Vulkan.
- **Architetti e ingegneri che usano modelli e assembly CAD (computer aided design) di grandi dimensioni e complessi.** La piattaforma RTX offre il nuovo SDK di NGX per infondere potenti funzionalità avanzate per l'intelligenza artificiale in applicazioni visive. Questo libera tempo e risorse attraverso la manipolazione intelligente delle immagini, l'automazione delle attività ripetitive e l'ottimizzazione dei processi di calcolo intensivo.
- **Sviluppatori di software in settori manifatturieri, multimediali e di intrattenimento, medici e di altro settore.** Quadro RTX velocizza lo sviluppo delle applicazioni con le funzionalità di analisi di Ray tracing, Deep Learning e rasterizzazione tramite API e SDK software leader del settore.
- **Scienziati dei dati che usano Core di tensore e Core CUDA per accelerare le attività computazionalmente intensive e altre operazioni di apprendimento approfondite.** Usando sensori, maggiore connettività e apprendimento profondo, ricercatori e sviluppatori possono abilitare le applicazioni AI per tutto, dai veicoli autonomi alla ricerca scientifica.

 
**Tabella 1. Caratteristiche delle prestazioni di quadro RTX 3000**

| **Componente**                                       | **Descrizione**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Core RT                                            | La tecnologia di analisi basata su hardware dedicata consente alla GPU di eseguire il rendering della qualità del film, degli oggetti fotorealistici e degli ambienti con ombreggiature, riflessi e rifrazioni fisicamente accurate.  Il motore di analisi in tempo reale funziona con le API NVIDIA OptiX, Microsoft DXR e Vulkan per offrire un livello di realismo ben oltre ciò che è possibile usando le tecniche di rendering tradizionali. I core RT accelerano le funzioni di trascinamento della gerarchia dei volumi di BVH (bounding volume Hierarchy) e del ray cast usando un numero basso di raggi espressi tramite un pixel.                                     |
| Core di tensore avanzati                               | Nuclei a precisione mista appositamente costruiti per l'aritmetica della matrice di apprendimento profonda, consentono di ottenere TFLOPS 8x per l'allenamento rispetto alla generazione precedente.  Quadro RTX 3000 utilizza i core tensori di 240; ogni tensore Core esegue 64 operazioni di moltiplicazione-Add (FMA) a virgola mobile per orologio e ogni multiprocessore (SM) in streaming esegue complessivamente 1.024 singole operazioni a virgola mobile per orologio. Oltre a supportare le operazioni a matrice FP16/FP32, i nuovi core di tensore hanno aggiunto INT8 (operazioni intere di 2.048 per orologio) e modalità di precisione INT4 e INT1 (Binary) per le operazioni di matrice. |
| Software ottimizzato per Turing                           | I Framework di apprendimento profondi, come Microsoft cognitive Toolkit (CNTK), Caffe2, MXNet, TensorFlow e altri, conferiscono tempi di formazione molto più rapidi e prestazioni di formazione multinodo più elevate. Le librerie con accelerazione GPU, come cuDNN, cuBLAS e TensorRT, garantiscono prestazioni più elevate sia per le inferenze Deep Learning che per le applicazioni HPC (High-Performance Computing).                                                                                                                                                                                           |
| Piattaforma di calcolo parallelo NVIDIA CUDA             | Esegui nativamente linguaggi di programmazione standard come C/C++ e FORTRAN e API come OpenCL, OpenACC e Direct COMPUTE per accelerare tecniche come Ray tracing, video ed elaborazione di immagini e fluidodinamica di calcolo.                                                                                                                                                                                                                                                                                                                                        |
| Architettura multiprocessore (SM) Advanced Streaming | La memoria condivisa combinata e la cache L1 migliorano significativamente le prestazioni, semplificando la programmazione e riducendo l'ottimizzazione necessaria per ottenere le migliori prestazioni dell'applicazione.                                                                                                                                                                                                                                                                                                                                                                                                |
| Memoria GDDR6 ad alte prestazioni             | Quadro RTX 3000 offre 6GB di buffer di frame, che la rende la piattaforma ideale per la gestione di set di dati di grandi dimensioni e applicazioni sensibili alla latenza.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Singola istruzione, più thread (SIMT)          | La nuova funzionalità di pianificazione di thread indipendente consente la sincronizzazione e la cooperazione tra i thread paralleli attraverso la condivisione di risorse tra piccoli processi.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Elaborazione a precisione mista                           | il calcolo della precisione a virgola mobile a 16 bit consente la formazione e la distribuzione di reti neurali più grandi. Con un numero intero parallelo indipendente e percorsi di dati a virgola mobile, la SM di Turing gestisce i carichi di lavoro in modo più efficiente usando una combinazione di calcolo e calcolo degli indirizzi.                                                                                                                                                                                                                                                                                          |
| Bilanciamento del carico dinamico                              | Offre funzionalità di assegnazione dinamica delle risorse GPU per la grafica e le attività di calcolo in base alle esigenze per massimizzare l'utilizzo delle risorse.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Calcolare la precedenza                                  | La precedenza a livello di istruzione fornisce un controllo più preciso sulle attività di calcolo per evitare che le applicazioni a lunga durata vengano monopolizzate dalle risorse di sistema o dall'intervallo.                                                                                                                                                                                                                                                                                                                                                                                            |
| H. 264, H. 265 e HEVC codifica/decodifica motori         | Consente prestazioni più veloci in tempo reale per la transcodifica, l'editing video e altre applicazioni di codifica con due motori di codifica H. 264 e HEVC dedicati e un motore di decodifica dedicato indipendente dalla pipeline 3D/COMPUTE.                                                                                                                                                                                                                                                                                                                                        |
| GPU NVIDIA Boost 4,0                                |  Massimizza le prestazioni delle applicazioni automaticamente senza superare l'inviluppo di potenza e termica della GPU.  Consente alle applicazioni di rimanere all'interno dello stato dell'orologio Boost più a lungo in una soglia di temperatura più alta prima di cadere in un orologio base di temperatura secondaria.                                                                                                                                                                                                                                                                                               |

 **Tabella 2. Specifiche tecniche quadro RTX**

| **Componente**                                              | **Descrizione** |
| ---------------------------------------------------------- | --------------- |
| Core di elaborazione CUDA di NVIDIA                               | 1.920           |
| Core NVIDIA RT                                            | 30              |
| Core di tensore                                               | 240             |
| Memoria GPU                                                 | 6 GB            |
| Larghezza di banda della memoria                                           | 288 Gbps        |
| Tipo di memoria                                                | GDDR6           |
| Interfaccia di memoria                                           | 192 bit         |
| TGP max consumo energetico                                  | 65W             |
| Porta di visualizzazione                                               | 1,4             |
| OpenGL                                                     | 4,6             |
| Modello di shader                                               | 5,1             |
| DirectX                                                    | 12,1            |
| Generazione PCIe                                            | 3               |
| Prestazioni in virgola mobile a precisione singola (TFLOPS, picco) | 5,4             |
| Prestazioni tensore (Top, Peak)                            | 42,9            |
| Anti-aliasing NVIDIA FXAA/TX AA                             | Sì             |
| GPU Direct per il video                                       | Sì             |
| Supporto Vulkan                                             | Sì             |
| NVIDIA 3D Vision Pro                                       | Sì             |
| NVIDIA Optimus                                             | Sì             |

 
## Accelerazione delle app

La tabella seguente mostra il modo in cui quadro RTX 3000 offre un'accelerazione significativamente più rapida tra le principali applicazioni professionali. Include i risultati dei test di benchmark SPECview Perf 13 che confrontano la superficie del libro 3 15-inch con NVIDIA Quadro RTX 3000 e il libro Surface 2 15-inch con i dispositivi NVIDIA GeForce GTX 1060 nel mercato a partire da marzo 2020.

**Tabella 3. Accelerazione delle app in Surface Book 3 con quadro RTX 3000**

| **App**                                     | **Funzionalità di accelerazione delle app RTX 3000 di quadro**<br>                                                                                                                                                                                                                                                                                                                                          |
| ------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dimensione di Adobe                             | -RTX-Ray Tracing accelerato offre rendering 3D fotorealistico a artisti e designer 2D.                                                                                                                                                                                                                                                                                                     |
| Adobe sostanza Alchemist                   | -Creare e miscelare i materiali con facilità, con l'intelligenza artificiale RTX-accelerata.                                                                                                                                                                                                                                                                                                                             |
| Pittore di sostanze Adobe                     | -Dipingere materiali su modelli 3D, con RTX Accelerated Bakers e iray RTX rendering che genera immagini fotorealistiche per flussi di lavoro di rendering interattivo e batch. <br>                                      |
| Progettazione sostanze di Adobe                    | -Autore di materiali procedurali con RTX Accelerated Bakers<br>-Usa il rendering di NVIDIA iray, incluse le trame/sostanze e l'esportazione di trame bitmap per il rendering in qualsiasi iray compatibile con MDL.<br>-DXR-Accelerated Light e la cottura di occlusione ambientale.                                                                                                                                  |
| Adobe Photoshop                             | -CUDA Core Acceleration consente la modifica più rapida con le caratteristiche accelerate da 30 + GPU come Blur Gallery, Fluidifica, Smart Sharpen e Perspective Warp permettono a fotografi e designer di modificare le immagini in modo semplice e rapido.                                                                                                                                                                        |
| Adobe Lightroom                             | -Modifica più rapida delle immagini ad alta risoluzione con il riquadro di visualizzazione con accelerazione GPU, che consente la modellazione di scene 3D più grandi e il sartiame di animazioni più complesse.<br>-L'elaborazione di immagini con accelerazione GPU consente di apportare modifiche notevolmente più reattive, in particolare nei display 4K o con risoluzione superiore.<br>-Accelerato AI-powered con GPU "Enhance Details" per raffinare i dettagli del colore delle immagini non ELABORAte. |
| Adobe Illustrator                           | -Panoramica e zoom con tela accelerata con GPU più veloce, che consente ai progettisti grafici e agli illustratori di eseguire la panoramica e lo zoom avanti e indietro della grafica vettoriale complessa in modo uniforme e interattivo.                                                                                                                                                                                                        |
| Adobe<br>Premiere Pro                       | -Significativamente più veloce la modifica e il rendering di video con effetti accelerati tramite GPU e CPU.<br>-Effetti accelerati con GPU con la tecnologia NVIDIA CUDA per l'editing video in tempo reale e un rendering finale più rapido dei fotogrammi.<br>-Funzionalità di ristrutturazione automatica con accelerazione GPU per convertire in modo intelligente il video panoramico in un video verticale o orizzontale rilevati dinamicamente.                                           |
| Autodesk<br>Revit                           | -Viewport con accelerazione GPU per un'esperienza di progettazione più fluida e interattiva.<br>-Supporta i renderer 3D con accelerazione GPU di terze parti, ad esempio V-Ray e Scape.                                                                                                                                                                                                                                      |
| Autodesk<br>3ds Max                         | -Grafica di viewport con accelerazione GPU per una modellazione e progettazione 3D interattiva e veloce.<br>-RTX-Ray Tracing accelerato e AI denoising con il renderer Arnold predefinito.<br>-Più di 70 per cento più veloce rispetto a Surface Book 2 15 ".                                                                                                                                               |
| Autodesk<br>Maya                            | -RTX-Ray Tracing accelerato e AI denoising con il renderer Arnold predefinito.<br>-Accelerazione viewport OpenGL.                                                                                                                                                                                                                                                                             |
| Dassault Systemes<br>SolidWorks             | -SolidWorks Interactive Ray Tracer (Visualizza) accelerato sia da Core RT che da Core tensori; I-denoiser accelerato AI.<br>-Viene eseguito più di 50% più veloce rispetto a Surface Book 2 15 ".                                                                                                                                                                                                             |
| Dassault Systemes<br>Piattaforma Experience 3D | -CATIA Interactive Ray Tracer (Live rendering) accelerato da Core RT.<br>-CATIA viene eseguito più di 100% più velocemente rispetto a Surface Book 2 15 ".                                                                                                                                                                                                                                                     |
| ImageVis3D                                  | -Viene eseguito più di 2x più velocemente rispetto a Surface Book 2 15 ".                                                                                                                                                                                                                                                                                                                                       |
| McNeel & associati<br>Rhino 3D             | -Viewport con accelerazione GPU per un'esperienza di modellazione e progettazione fluida e interattiva.<br>-Supporta i cicli per il rendering 3D accelerato tramite GPU.                                                                                                                                                                                                                                                     |
| Siemens NX                                  | -Siemens NX Interactive Ray Tracer (Ray traced Studio) accelerato da Core RT.<br>-Viene eseguito più di 10x più veloce rispetto a Surface Book 2 15 ".                                                                                                                                                                                                                                                 |
| ESRI ArcGIS                                 | -Risultati in tempo reale da quelli che hanno richiesto giorni e settimane, a causa dell'inferenza di DL che sfrutta i nuclei di tensore.                                                                                                                                                                                                                                                                                                     |
| PTC Creo                                    | -Lo strumento di simulazione di ingegneria in tempo reale di Creo (creo Simulation Live) è basato su CUDA.<br>-Viene eseguito più del 15% di velocità rispetto al libro Surface 2 15 ".                                                                                                                                                                                                                                               |
| Luxion                              | -Ray Tracer interattivo di terze parti usato da SolidWorks, creo e Rhino. Accelerato da Core RT, OptiX™ denoising con accelerazione AI.                                                                                                                                                                                                                                                                   |
| ANSYS<br>Individuazione Live                     | -ANSYS in tempo reale strumento di simulazione di ingegneria (ANSYS Discovery Live) costruito su CUDA.                                                                                                                                                                                                                                                                                                                  |
## SKU

**Tabella 4. Surface Book 3 con SKU RTX 3000 di quadro**

| **Schermo** | **Responsabile del trattamento**                     | **GPU**                                                                                          | **RAM**    | **Archiviazione** |
| ----------- | --------------------------------- | ------------------------------------------------------------------------------------------------ | ---------- | ----------- |
| 15 pollici | Quad-Core 10 gen Core i7-1065G7 | Elementi grafici Intel Iris™ Plus<br>NVIDIA Quadro RTX 3000. Progettazione Max-Q con memoria grafica GDDR6 da 6GB | 32 LPDDR4x | 512 GB      |
| 15 pollici | Quad-Core 10 gen Core i7-1065G7 | Elementi grafici Intel Iris™ Plus<br>NVIDIA Quadro RTX 3000. Progettazione Max-Q con memoria grafica GDDR6 da 6GB | 32 LPDDR4x | 1 TB        |

## Riepilogo

Surface Book 3 con quadro RTX 3000 offre le migliori prestazioni grafiche di qualsiasi computer portatile di Surface, offrendo ad architetti, ingegneri, sviluppatori e scienziati dati gli strumenti necessari per lavorare in modo efficiente ovunque:
 
- RTX-accelerazione tra più flussi di lavoro, ad esempio progettazione, animazione, produzione video e altro ancora.
- Prestazioni di livello desktop in un fattore di forma per dispositivi mobili.
- Caratteristiche di livello aziendale, affidabilità e supporto per progetti mission-critical.

## Scopri di più

- [Panoramica tecnica della GPU di Surface Book 3](surface-book-GPU-overview.md)
- [Surface per le aziende](https://www.microsoft.com/surface/business)
- [Microsoft cognitive Toolkit (CNTK)](https://docs.microsoft.com/cognitive-toolkit/)

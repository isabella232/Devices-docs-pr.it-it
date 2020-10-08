---
title: Novità di Surface Dock
description: Questo articolo evidenzia le nuove caratteristiche e funzionalità per il dock di Surface di nuova generazione.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 10/01/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: 19aba3e88afd7b17de5b391d1bfe6eaf77db38e9
ms.sourcegitcommit: f996a95af741e54536b1f3eb94d0f13f681f5d5d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2020
ms.locfileid: "11093139"
---
# Novità di Surface Dock 

Surface Dock 2, il Dock Surface di nuova generazione, consente agli utenti di connettere monitor esterni e più periferiche per ottenere un'esperienza desktop completamente modernizzata da un dispositivo Surface. Costruito per massimizzare l'efficienza in Office, in un'area di lavoro flessibile o a casa, Surface Dock 2 include sette porte, tra cui due porte USB-C frontali, con 15 watt di potenza di ricarica rapida per telefono e accessori. 

### Supporto completo per la gestione dei dispositivi

Surface Dock 2 è progettato per semplificare la gestione IT, consentendo agli amministratori di automatizzare gli aggiornamenti del firmware tramite Windows Update o centralizzare gli aggiornamenti con gli strumenti di distribuzione del software interni.

- Surface Enterprise Management Mode (SEMM) consente agli amministratori IT di proteggere le porte in Surface Dock 2. Per altre informazioni, vedere [proteggere le porte di Surface Dock 2 con la modalità di gestione di Surface Enterprise](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/secure-surface-dock-2-ports-with-surface-enterprise-management/ba-p/1418999).
-  Il supporto di Strumentazione gestione Windows (WMI) consente agli amministratori IT di monitorare e gestire in remoto il firmware più recente, lo stato dei criteri e i dati correlati tra i dispositivi Surface Dock 2. Per altre informazioni, vedere [gestire Surface Dock 2 con WMI](surface-dock2-wmi.md).

## Requisiti di sistema generali

- Windows 10 versione 1809. Non è disponibile alcun supporto per i dispositivi host Windows 7, Windows 8 o non Surface. Surface Dock 2 funziona con i seguenti dispositivi Surface:

  - Surface Pro (5a generazione)
  - Laptop Surface (1a generazione)
  - Surface Pro 6
  - Surface Book 2
  - Surface Laptop 2
  - Surface Go
  - Surface Pro 7
  - Surface Pro X 
  - Laptop Surface 3
  - Surface Book 3
  - Superficie Go 2

## Componenti di Surface Dock 2

![Componenti di Surface Dock 2](./images/surface-dock2.png)
 
### USB

- Due porte USB-C fronte-retro.
- Due porte USB-C (gen 2) posteriori.
- Due porte USB-A posteriori di fronte A. 

### Video
    
- Dual 4K@60hz. Supporta fino a due schermi nei dispositivi seguenti:

  - Surface Book 3
  - Superficie Go 2
  - Surface Pro 7
  - Surface Pro X
  - Laptop Surface 3

- 4K@30Hz Dual 4K@. Supporta fino a due schermi nei dispositivi seguenti:

  - Surface Pro 6
  - Surface Pro (5a generazione)
  - Surface Laptop 2
  - Laptop Surface (1a generazione)
  - Surface Go
  - Surface Book 2.

### Ethernet

- 1 porta Gigabit Ethernet. 

### Alimentatore esterno

- 199 watt che supportano 100V-240V.


## Confronto di Surface Dock 

**Tabella 1. Surface Dock e hub di viaggio USB-C**


| Componente                           | Dock Surface                                                | Surface Dock 2                                                                                      | Hub viaggi USB-C |
| ----------------------------------- | ----------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------- |
| Surflink                            | Sì                                                         | Sì                                                                                                 | No               |
| USB-A                               | 2 fronte USB 3,1 gen 1<br>2 rivolto posteriore USB 3,1 gen 1 | 2 rear facing USB 3,2 gen 2 (7.5 W di potenza)                                                            | 1 USB 3,1 gen 2  |
| Porta mini display                   | 2 rivolto posteriore (DP 1.2)                                       | Nessuno                                                                                                | Nessuno             |
| USB-C                               | Nessuno                                                        | 2 fronte USB 3,2 gen 2<br>(15W Power)<br>2 rear facing USB 3,2 gen 2 (DP 1.4 a)<br>(7.5 w di potenza) | 1 USB 3,2 gen 2  |
| 3,5 mm audio in entrata/uscita                 | Sì                                                         | Sì                                                                                                 | Sì              |
| Ethernet                            | Sì, 1 Gigabit                                              | Sì 1 Gigabit                                                                                       | Sì, 1 Gigabit   |
| Alimentazione CC in                         | Sì                                                         | Sì                                                                                                 |                  |
| Blocco di Kensington                     | Sì                                                         | Sì                                                                                                 |                  |
| Lunghezza cavo Surflink               | 65cm                                                        | 80cm                                                                                                | 20cm             |
| Alimentazione host Surflink                 | 60W                                                         | 120W                                                                                                | N/D              |
| Potenza di caricamento USB                      | 30W                                                         | 60W                                                                                                 |                  |
| Velocità in bit USB                        | 5 Gbps                                                      | 10 Gbps                                                                                             | 10 Gbps          |
| Supporto per monitor                     | 2 x 4K @30fps o<br>1 x 4K @ 60fps                         | 2 x 4K @ 60fps                                                                                      | 1 x 4K @ 60fps   |
| Wake-on-LAN dalla modalità standby connessa <sup> 1</sup> | Sì                                                         | Sì                                                                                                 |                  |
| Wake-on-LAN dalle modalità di sospensione di S4/S5  | No                                                          | Sì                                                                                                 |          Sì        |
| Avvio PXE di rete                    | Sì                                                         | Sì                                                                                                 |        Sì          |
| Controllo di accesso host SEMM            | No                                                          | Sì                                                                                                 | No               |
| Controllo di accesso alla porta SEMM <sup> 2</sup>          | No                                                          | Sì                                                                                                 | No               |
| Supporto per la manutenzione                   | MSI                                                         | Windows Update o MSI                                                                               |                  |

 



1. *I dispositivi devono essere configurati per la riattivazione LAN tramite la modalità di gestione di Surface Enterprise (SEMM) o DFCI (device firmware Control Interface) per riattivare gli Stati di ibernazione o di spegnimento. La riattivazione da ibernazione o Power-off è supportata in Surface Pro 7, Surface laptop 3, Surface Pro X, Surface Book 3 e Surface Go 2.  Licenza software necessaria per alcune funzionalità. Venduti separatamente.*

2. *Licenza software necessaria per alcune funzionalità. Venduti separatamente.*

## Gestione semplificata dei dispositivi

Surface ha rilasciato funzionalità di gestione semplificate tramite Windows Update che consente agli amministratori IT di usare le caratteristiche di livello aziendale seguenti:

- Aggiornamenti privi di **attrito**. Aggiornare i dock in modo silenzioso e automatico, con Windows Update o Microsoft endpoint Configuration Manager (in precedenza System Center Configuration Manager-SCCM) o altri strumenti di distribuzione MSI. 
- **Riattivazione dalla rete**. Gestisci e accedi ai dispositivi aziendali senza dipendere dagli utenti per mantenerli accesi. Anche quando un dispositivo ancorato si trova in modalità Sleep, Hibernate o Power off, il team può riattivarsi dalla rete per il servizio e la gestione, usando endpoint Configuration Manager o altri strumenti di gestione aziendale.
- **Controllo IT centralizzato**. Controlla chi può connettersi a Surface Dock 2 attivando e disattivando le porte. Limitare i dispositivi host che possono essere usati con Surface Dock 2. Limita l'accesso a un singolo utente o configura i dock in modo che sia possibile accedervi solo da utenti specifici del team o dall'intera società.

## Passaggi successivi

- [Proteggere Surface Dock 2 porte con la modalità di gestione di Surface Enterprise](https://techcommunity.microsoft.com/t5/surface-it-pro-blog/secure-surface-dock-2-ports-with-surface-enterprise-management/ba-p/1418999)
- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)
- [Procedure consigliate per le impostazioni di risparmio energia per i dispositivi Surface](maintain-optimal-power-settings-on-Surface-devices.md)

---
title: Abilitare PEAP, EAP-FAST e Cisco LEAP in dispositivi Surface (Surface)
description: Scopri come abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nel tuo dispositivo Surface.
ms.assetid: A281EFA3-1552-467D-8A21-EB151E58856D
ms.reviewer: ''
manager: laurawi
keywords: rete, wireless, dispositivo, distribuire, autenticazione, protocollo
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 368ab2bc1480c00ef27a9d35910a1db7a6856748
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12448299"
---
# <a name="enable-peap-eap-fast-and-cisco-leap-on-surface-devices"></a>Abilitare PEAP, EAP-FAST e Cisco LEAP in dispositivi Surface

Scopri come abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nel tuo dispositivo Surface.

Se usi PEAP, EAP-FAST o Cisco LEAP nella tua rete aziendale, probabilmente sai già che questi tre protocolli di autenticazione wireless non sono supportati dai dispositivi Surface in modo predefinito. Alcuni utenti potrebbero rendersi conto del mancato supporto quando tentano di connettersi alla rete wireless, mentre altri potrebbero scoprirlo quando non riescono ad accedere alle risorse all'interno della rete, ad esempio a condivisioni di file e siti interni. Per altre informazioni, vedi [Extensible Authentication Protocol](/windows-server/networking/technologies/extensible-authentication-protocol/network-access).

Puoi aggiungere il supporto per ogni protocollo eseguendo un piccolo pacchetto MSI da una chiavetta USB o una condivisione di file. Per le organizzazioni che desiderano abilitare il supporto EAP nei propri dispositivi Surface, il formato del pacchetto MSI supporta la distribuzione con molti strumenti di gestione e distribuzione, come Microsoft Deployment Toolkit (MDT) e Microsoft Endpoint Configuration Manager.

## <a name="download-peap-eap-fast-or-cisco-leap-installation-files"></a><a href="" id="download-peap--eap-fast--or-cisco-leap-installation-files--"></a>Scaricare i file di installazione per PEAP, EAP-FAST o Cisco LEAP

Puoi scaricare i file di installazione MSI per PEAP, EAP-FAST o Cisco LEAP in un singolo file di archivio ZIP dall'Area download Microsoft. Per scaricare questo file, passa alla pagina degli [strumenti di Surface per l'IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft, fai clic su **Download** e quindi seleziona il file **Cisco EAP-Supplicant Installer.zip**.

## <a name="deploy-peap-eap-fast-or-cisco-leap-with-mdt"></a>Distribuire PEAP, EAP-FAST o Cisco LEAP con MDT

Se stai già eseguendo una distribuzione di Windows nei dispositivi Surface nella tua organizzazione, l'aggiunta dei file di installazione per ogni protocollo alla condivisione di distribuzione e la configurazione dell'installazione automatica durante la distribuzione sono operazioni rapide e semplici. Puoi addirittura configurare una sequenza di attività per l'aggiornamento dei dispositivi Surface distribuiti in precedenza per offrire supporto per questi protocolli usando lo stesso processo.

Per abilitare il supporto per i protocolli PEAP, EAP-FAST e Cisco LEAP nei nuovi dispositivi Surface distribuiti, segui questi passaggi:

1. Scarica ed estrai i file di installazione per ogni protocollo in cartelle separate in un percorso facilmente accessibile.

2. Apri MDT Deployment Workbench ed espandi la condivisione di distribuzione alla cartella **Applications**.

3. Seleziona **New Application** nel riquadro **Action**.

4. Scegli **Application with source files** per copiare i file MSI nella condivisione di distribuzione.

5. Seleziona la cartella che hai creato nel passaggio 1 per il protocollo desiderato.

6. Assegna un nome alla cartella nella condivisione di distribuzione in cui verranno archiviati i file di installazione.

7. Specifica la riga di comando per distribuire l'applicazione:

    - Per PEAP usa **EAP-PEAP.msi /qn /norestart**.

    - Per LEAP usa **EAP-LEAP.msi /qn /norestart**.

    - Per EAP-FAST usa **EAP-FAST.msi /qn /norestart**.

8. Usa le opzioni predefinite per completare la procedura guidata New Application Wizard.

9. Ripeti i passaggi da 3 a 8 per ogni protocollo desiderato.

Dopo aver eseguito questi passaggi per importare i tre pacchetti MSI in MDT, i pacchetti saranno disponibili per la selezione nella pagina Applications della procedura guidata Windows Deployment Wizard. Benché in alcuni scenari di distribuzione semplici potrebbe essere sufficiente permettere ai tecnici di selezionare ogni pacchetto al momento della distribuzione, non si tratta di una scelta consigliata. Questa procedura implica la possibilità che un tecnico tenti di applicare i pacchetti a computer diversi dai dispositivi Surface o che un dispositivo Surface venga distribuito senza supporto EAP a causa di un errore umano.

Per nascondere queste applicazioni dalla pagina Install Applications, seleziona la casella di controllo **Hide this application in the Deployment Wizard** nelle proprietà di ogni applicazione. Una volta nascoste, le applicazioni non verranno visualizzate come facoltative durante la distribuzione. Per distribuirle nella sequenza di attività di distribuzione di Surface, le applicazioni devono essere definite in modo esplicito per l'installazione tramite un passaggio separato nella sequenza di attività.

Per specificare i protocolli in modo esplicito, segui questi passaggi:

1. Apri le proprietà della sequenza di attività di distribuzione di Surface da MDT Deployment Workbench.

2. Nella scheda **Task Sequence** seleziona il passaggio **Install Applications** in **State Restore**. Questo è in genere disponibile tra i passaggi di pre-applicazione e post-applicazione di Windows Update.

3. Usa il pulsante **Add** per creare un nuovo passaggio **Install Application** nella categoria **General**.

4. Seleziona **Install a single application** nella scheda **Properties** del passaggio.

5. Seleziona il protocollo EAP desiderato nell'elenco.

6. Ripeti i passaggi da 2 a 5 per ogni protocollo desiderato.

## <a name="deploy-peap-eap-fast-or-cisco-leap-with-configuration-manager"></a>Distribuire PEAP, EAP-FAST o Cisco LEAP con Configuration Manager

Per le organizzazioni che gestiscono i dispositivi Surface con Configuration Manager, la distribuzione del supporto PEAP, EAP-FAST o Cisco LEAP per tali dispositivi è ancora più semplice. È sufficiente importare ogni file MSI come applicazione dall'area Raccolta software e quindi configurare una distribuzione nella raccolta di dispositivi Surface.

Per altre informazioni su come distribuire le applicazioni con Configuration Manager, vedi [Creare e distribuire un'applicazione con Configuration Manager](/mem/configmgr/apps/get-started/create-and-deploy-an-application).


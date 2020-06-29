---
title: Considerazioni per Surface e Microsoft endpoint Configuration Manager
description: La gestione e la distribuzione dei dispositivi Surface con Configuration Manager è fondamentalmente uguale a qualsiasi altro PC; Questo articolo descrive scenari che potrebbero richiedere ulteriori considerazioni.
keywords: gestire, distribuire, aggiornare, driver, firmware
ms.prod: w10
ms.mktglfcycl: deploy
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.localizationpriority: medium
ms.audience: itpro
ms.reviewer: ''
manager: laurawi
ms.openlocfilehash: 4fa62d227deb0b0b07fa0fbc6552ea5b04c1b87b
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832565"
---
# Considerazioni per Surface e Microsoft endpoint Configuration Manager

Fondamentalmente, la gestione e la distribuzione dei dispositivi Surface con Microsoft endpoint Configuration Manager è la stessa della gestione e della distribuzione di qualsiasi altro PC. Analogamente a qualsiasi altro PC, un dispositivo di distribuzione ai dispositivi Surface include l'importazione di driver, l'importazione di un'immagine Windows, la preparazione di una sequenza di attività di distribuzione e la distribuzione della sequenza di attività in una raccolta. Dopo la distribuzione, i dispositivi Surface sono simili a qualsiasi altro client Windows. per pubblicare app, impostazioni e criteri, è possibile usare lo stesso processo usato per qualsiasi altro dispositivo.

Per altre informazioni su come usare Configuration Manager, è possibile distribuire e gestire i dispositivi nella [documentazione di Microsoft endpoint Configuration Manager](https://docs.microsoft.com/sccm/index).

Anche se la distribuzione e la gestione dei dispositivi Surface è fondamentalmente uguale a qualsiasi altro PC, esistono alcuni scenari che potrebbero richiedere ulteriori considerazioni o passaggi. Questo articolo fornisce descrizioni e indicazioni per questi scenari. Le soluzioni documentate in questo articolo possono essere applicate anche ad altri dispositivi e produttori.

> [!NOTE]
> Per la gestione dei dispositivi Surface è consigliabile usare la filiale corrente di Microsoft endpoint Configuration Manager.

## Aggiornamento di driver e firmware per dispositivi Surface

Per i dispositivi che ricevono gli aggiornamenti tramite Windows Update, i driver per i componenti Surface (e persino gli aggiornamenti del firmware) vengono applicati automaticamente durante il processo di Windows Update. Per i dispositivi con aggiornamenti gestiti, ad esempio quelli aggiornati tramite Windows Server Update Services (WSUS) o Configuration Manager, vedere [gestire il driver della superficie e gli aggiornamenti del firmware](https://docs.microsoft.com/surface/manage-surface-driver-and-firmware-updates/).

> [!NOTE]
> I driver e i firmware per dispositivi di superficie vengono firmati con SHA-256, che non è supportato nativamente da Windows Server 2008 R2. Una soluzione alternativa è disponibile per gli ambienti di Configuration Manager in uso in Windows Server 2008 R2. Per altre informazioni, vedere [non è possibile importare driver in Microsoft endpoint Configuration Manager (KB3025419)](https://support.microsoft.com/kb/3025419).

## Distribuzione di adapter Ethernet Surface e gestione configurazione

Il meccanismo predefinito usato da Configuration Manager per identificare i dispositivi durante la distribuzione è l'indirizzo MAC (Media Access Control). Dato che l'indirizzo MAC è associato al controller Ethernet, una scheda Ethernet condivisa da più dispositivi causerà Configuration Manager per identificare tutti i dispositivi come un singolo dispositivo. Ciò può causare la distribuzione di Windows da Configuration Manager a non essere applicata ai dispositivi previsti.

Per fare in modo che i dispositivi Surface che usano la stessa scheda Ethernet vengano identificati come dispositivi univoci durante la distribuzione, è possibile indicare a Gestione configurazione di identificare i dispositivi con un altro metodo. L'altro metodo potrebbe essere l'indirizzo MAC della scheda di rete wireless o dell'identificatore univoco universale (UUID di sistema). Puoi specificare che Configuration Manager usa altri metodi di identificazione con le opzioni seguenti:

* Aggiungere un'esclusione per gli indirizzi MAC delle schede Ethernet di Surface, che costringe Configuration Manager a trascurare l'indirizzo MAC in preferenza dell'UUID del sistema, come documentato nel [riutilizzo della stessa scheda NIC per più distribuzioni avviate da PXE nel post di Blog di SMicrosoft endpoint Configuration Manager OSD](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/) .

* Dispositivi preallestiti per UUID di sistema come documentati nel [riutilizzo della stessa scheda NIC per più distribuzioni avviate da PXE nel post di Blog di Microsoft endpoint Configuration Manager OSD](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/) .

* Usare uno script per identificare un dispositivo Surface appena distribuito dall'indirizzo MAC della propria scheda wireless, come illustrato nell' [uso della stessa scheda Ethernet esterna per più](https://blogs.technet.microsoft.com/askpfeplat/2014/07/27/how-to-use-the-same-external-ethernet-adapter-for-multiple-sccm-osd/) post di Blog di SCCM OSD.

Un'altra considerazione per la scheda Ethernet di Surface durante le distribuzioni con Configuration Manager è il driver per il controller Ethernet. A partire da Windows 10, versione 1511, il driver per la scheda Ethernet Surface è incluso per impostazione predefinita in Windows. Per le organizzazioni che vogliono distribuire l'ultima versione di Windows 10 e usare la versione più recente di WinPE, l'uso della scheda Ethernet Surface non richiede ulteriori azioni.

Per le versioni di Windows precedenti a Windows 10, versione 1511 (incluso Windows 10 RTM e Windows 8,1), potrebbe essere comunque necessario installare il driver della scheda Ethernet Surface e includere il driver nel supporto di avvio di WinPE. Con l'inclusione in Windows 10, il driver non è più disponibile per il download dall'area download Microsoft. Per scaricare il driver della scheda Ethernet di Surface, scaricarlo dal catalogo Microsoft Update come documentato nel post di Blog di [Surface Ethernet drivers](https://blogs.technet.microsoft.com/askcore/2016/08/18/surface-ethernet-drivers/) dal Blog di Ask the core team.

## Distribuire l'app Surface con Configuration Manager

Con il rilascio di Microsoft Store per le aziende, Surface app non è più disponibile come download di driver e firmware. Le organizzazioni che vogliono distribuire l'app Surface a dispositivi Surface gestiti o durante la distribuzione con l'uso di Configuration Manager devono acquisire l'app Surface tramite Microsoft Store for business e quindi distribuire l'app Surface con PowerShell. Puoi trovare i comandi di PowerShell per la distribuzione dell'app Surface, le istruzioni per scaricare l'app Surface e i Framework prerequisito di Microsoft Store for business nell' [app Distribuisci superficie con l'articolo di Microsoft Store for business](https://technet.microsoft.com/itpro/surface/deploy-surface-app-with-windows-store-for-business) nella libreria TechNet.

## Usare elementi multimediali preallestiti con client Surface

Se l'organizzazione usa elementi multimediali preinstallati per precaricare le risorse di distribuzione per i computer prima della distribuzione con Configuration Manager, la natura dei dispositivi di Surface come dispositivi UEFI può richiedere di eseguire ulteriori operazioni. In particolare, un ambiente nativo UEFI richiede la creazione di più partizioni nel disco di avvio del sistema. Se si seguono insieme alla [documentazione per il supporto](https://technet.microsoft.com/library/79465d90-4831-4872-96c2-2062d80f5583?f=255&MSPPError=-2147217396#BKMK_CreatePrestagedMedia)preinstallato, le istruzioni prevedono solo i dischi di avvio di una singola partizione e quindi non riusciranno se applicati ai dispositivi Surface.

Le istruzioni per l'applicazione di elementi multimediali preallestiti ai dispositivi UEFI, ad esempio i dispositivi Surface, sono disponibili nella [procedura per l'applicazione di elementi multimediali preallestiti su dischi multipartizionati per PC BIOS o UEFI nel post di Blog di Microsoft endpoint Configuration Manager](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2014/04/02/how-to-apply-task-sequence-prestaged-media-on-multi-partitioned-disks-for-bios-or-uefi-pcs-in-system-center-configuration-manager/) .

## Conflitti di licenza con l'attivazione OEM 3,0

I dispositivi Surface vengono preinstallati con una copia con licenza di Windows. Surface Pro 4, ad esempio, è preinstallato con Windows 10 Professional. Il codice di licenza per la copia preinstallata di Windows è incorporato nel firmware del dispositivo con l'attivazione OEM 3,0 (OA 3,0). Quando si esegue il supporto di installazione di Windows in un dispositivo con una chiave OA 3,0, l'installazione di Windows legge automaticamente il codice di licenza e lo usa per installare e attivare Windows. Nella maggior parte dei casi, questo semplifica la reinstallazione di Windows, perché l'utente non deve trovare o immettere una chiave di licenza.

Quando si esegue la riimmagine di un dispositivo con Windows Enterprise, questa chiave di licenza incorporata non causa un conflitto. Il motivo è che il supporto di installazione per Windows Enterprise è configurato per installare solo una versione Enterprise di Windows e pertanto non è compatibile con il codice di licenza incorporato nel firmware di sistema. Se non viene specificato un codice Product Key, ad esempio quando si intende attivare con Key Management Services [KMS] o attivazione basata su Active Directory), viene usata una chiave di licenza GVLK (Generic Volume License Key) finché Windows non viene attivato da una di queste tecnologie.

Tuttavia, i problemi possono verificarsi quando le organizzazioni intendono usare versioni di Windows compatibili con la chiave incorporata del firmware. Ad esempio, un'organizzazione che vuole installare Windows 10 Professional su un dispositivo Surface 3 che in origine è stata fornita con Windows 10 Home Edition può avere difficoltà quando la configurazione di Windows legge automaticamente la chiave Home Edition durante l'installazione e viene installata come Home Edition anziché Professional. Per evitare questo conflitto, è possibile usare il file ei. cfg o Pid.txt per indicare esplicitamente che la configurazione di Windows richiede un codice Product Key oppure è possibile immettere un codice Product Key specifico nella sequenza di attività di distribuzione. Per altre informazioni, vedere [configurazione di Windows Setup Edition e file ID prodotto](https://technet.microsoft.com/library/hh824952.aspx). Se non si dispone di un tasto specifico, è possibile usare i codici Product Key predefiniti per Windows, che è possibile trovare in [personalizzare e distribuire un sistema operativo Windows 10](https://dpcenter.microsoft.com/en/Windows/Build/cp-Windows-10-build) nel centro partner del dispositivo.

## Applicare un tag asset durante la distribuzione

Surface Studio, Surface Book, Surface Pro 4, Surface Pro 3 e Surface 3 Devices supportano l'applicazione di un tag asset in UEFI. Questo tag di asset può essere usato per identificare il dispositivo da UEFI anche se il sistema operativo non riesce e può anche essere interrogato dall'interno del sistema operativo. Per altre informazioni sulla funzione Tag Surface asset, vedere lo [strumento asset tag per](https://blogs.technet.microsoft.com/askcore/2014/10/20/asset-tag-tool-for-surface-pro-3/) il post di Blog Surface Pro 3.

Per applicare un tag asset usando l' [utilità CLI di Surface asset tag](https://www.microsoft.com/download/details.aspx?id=44076) durante una sequenza di attività di distribuzione di Configuration Manager, usare lo script e le istruzioni disponibili nel [tag set Surface asset durante un](https://blogs.technet.microsoft.com/jchalfant/set-surface-pro-3-asset-tag-during-a-configuration-manager-task-sequence/) post di Blog sulla sequenza di attività di Configuration Manager.

## Configurare il pulsante Reimposta

Quando si distribuisce Windows in un dispositivo Surface, la funzionalità di reimpostazione dei pulsanti di Windows è configurata per impostazione predefinita per ripristinare il sistema in uno stato in cui l'ambiente non è ancora configurato. Quando viene usata la funzione Reset, il sistema elimina le applicazioni e le impostazioni installate. Anche se in alcune situazioni può essere utile ripristinare il sistema in uno stato senza applicazioni e impostazioni, in un ambiente professionale questo rende effettivamente il sistema inutilizzabile per l'utente finale.

Il pulsante Reimposta può essere configurato, tuttavia, per ripristinare la configurazione di sistema in uno stato in cui è pronto per l'uso da parte dell'utente finale. Seguire il processo descritto in distribuire le [funzionalità di reimpostazione del pulsante](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/deploy-push-button-reset-features) per personalizzare l'esperienza di reimpostazione dei pulsanti per i dispositivi.

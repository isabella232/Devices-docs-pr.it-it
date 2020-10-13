---
title: Proteggere Surface Dock 2 porte con la modalità di gestione di Surface Enterprise (SEMM)
description: Questo documento fornisce indicazioni per la configurazione delle impostazioni della porta UEFI per Surface Dock 2 quando si è connessi a dispositivi Surface compatibili, tra cui Surface Book 3, Surface laptop 3 e Surface Pro 7.
ms.assetid: 2808a8be-e2d4-4cb6-bd53-9d10c0d3e1d6
ms.reviewer: ''
manager: laurawi
keywords: Risolvere i problemi comuni, problemi di installazione
ms.prod: w10
ms.mktglfcycl: support
ms.sitesec: library
ms.pagetype: surfacehub
author: v-miegge
ms.author: jesko
ms.topic: article
ms.date: 06/08/2020
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 641d023b59426582130dcfb7e0d86c6f3af456e8
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114694"
---
# Proteggere Surface Dock 2 porte con la modalità di gestione di Surface Enterprise (SEMM)

## Introduzione

Surface Enterprise Management Mode (SEMM) consente agli amministratori IT di proteggere e gestire le porte di Surface Dock 2 configurando le impostazioni UEFI in un pacchetto di configurazione di Windows Installer (. File MSI) distribuito in dispositivi Surface compatibili in un ambiente aziendale.

### Dispositivi supportati

La gestione di Surface Dock 2 con SEMM è disponibile per i banchi collegati a Surface Book 3, Surface laptop 3, Surface Laptop Go, Surface Pro 7 e Surface Pro X. Questi dispositivi Surface compatibili vengono comunemente definiti **dispositivi host**. Un pacchetto viene applicato ai dispositivi host in base a se un dispositivo host è **autenticato** o non **autenticato**. Le impostazioni configurate si trovano nel layer UEFI nei dispositivi host che consentono all'amministratore IT di gestire Surface Dock 2, come qualsiasi altra periferica incorporata, ad esempio la fotocamera.

>[!NOTE]
>È possibile gestire le porte di Surface Dock 2 solo quando il Dock è connesso a uno dei seguenti dispositivi compatibili: Surface Book 3, Surface laptop 3 e Surface Pro 7. Qualsiasi dispositivo che non riceve le impostazioni dei criteri autenticati UEFI è intrinsecamente un dispositivo non autenticato.

### Scenari

La restrizione di Surface Dock 2 alle persone autorizzate che hanno effettuato l'accesso a un dispositivo host aziendale offre un altro livello di protezione dei dati. Questa possibilità di bloccare Surface Dock 2 è fondamentale per i clienti specifici in ambienti altamente sicuri che vogliono beneficiare della funzionalità e della produttività del Dock mantenendo la conformità ai protocolli di sicurezza rigorosi. Anticipiamo che SEMM usato con Surface Dock 2 sarà particolarmente utile in uffici aperti e spazi condivisi in particolare per i clienti che vogliono bloccare le porte USB per motivi di sicurezza. Per una dimostrazione video, vedere [SEMM per Surface Dock 2](https://youtu.be/VLV19ISvq_s).

## Configurazione e distribuzione di impostazioni UEFI per Surface Dock 2

In questa sezione vengono fornite indicazioni dettagliate per le attività seguenti:

1. Installare [**Surface UEFI Configurator**](https://www.microsoft.com/download/details.aspx?id=46703).
1. Creare o ottenere certificati di chiave pubblica.
1. Creare un oggetto. Pacchetto di configurazione MSI.
   1. Aggiungere i certificati.
   1. Immettere il numero di 16 cifre della Marina militare per i dispositivi Surface Dock 2.
   1. Configurare le impostazioni UEFI.
1. Creare e applicare il pacchetto di configurazione ai dispositivi Surface mirati (Surface Book 3, Surface laptop 3 o Surface Pro 7).

>[!NOTE]
>Il **numero casuale (RN)** è un identificatore univoco del codice esadecimale a 16 cifre che viene provisionato in fabbrica e stampato in piccolo tipo nella parte inferiore del Dock. Il RN si differenzia dalla maggior parte dei numeri seriali, in quanto non può essere letto elettronicamente. Questo assicura che la prova di proprietà sia principalmente stabilita solo leggendo la RN quando si accede fisicamente al dispositivo. La Marina militare può essere ottenuta anche durante la transazione di acquisto ed è registrata nei sistemi di inventario Microsoft.

### Installare SEMM e Surface UEFI Configurator

Installare SEMM eseguendo **SurfaceUEFI_Configurator_v2.71.139.0.msi**. Si tratta di un programma di installazione autonomo e contiene tutto il necessario per creare e distribuire pacchetti di configurazione per Surface Dock 2.

- Scaricare **Surface UEFI Configurator** da [strumenti di Surface](https://www.microsoft.com/en-us/download/details.aspx?id=46703).

## Creare certificati di chiave pubblica

Questa sezione fornisce le specifiche per la creazione dei certificati necessari per gestire le porte per Surface Dock 2.

### Prerequisiti

In questo articolo si presuppone che si ottengano certificati da un provider di terze parti o si disponga già di competenze in Servizi certificati PKI e si sappia come crearne uno personalizzato.  È necessario avere familiarità con e seguire le raccomandazioni generali per la creazione di certificati come descritto nella documentazione di [Surface Enterprise Management Mode (SEMM)](https://docs.microsoft.com/surface/surface-enterprise-management-mode) , con un'unica eccezione. I certificati documentati in questa pagina richiedono termini di scadenza di 30 anni per l' **autorità di certificazione Dock**e 20 anni per il **certificato di autenticazione host**.

Per altre informazioni, vedere la documentazione relativa all' [architettura di Servizi certificati](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture) e rivedere i capitoli appropriati in [Windows Server 2019 inside out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)o [PKI di Windows Server 2008 e la sicurezza dei certificati](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788) disponibile in Microsoft Press.

### Requisiti per i certificati radice e host

Prima di creare il pacchetto di configurazione, è necessario preparare i certificati di chiave pubblica che autenticano la proprietà di Surface Dock 2 e facilitare eventuali modifiche successive della proprietà durante il ciclo di vita del dispositivo. I certificati host e provisioning richiedono l'immissione di ID EKU, altrimenti noti come **identificatori di oggetti (EKU) per l'autenticazione client (OID)**.

I valori EKU necessari sono elencati nella tabella 1 e nella tabella 2.

#### Tabella 1. Requisiti di certificato radice e ancoraggio

|Certificato|Algoritmo|Descrizione|Scadenza|OID EKU|
|---|---|---|---|---|
|Autorità di certificazione radice|ECDSA_P384|-Certificato radice con algoritmo di firma digitale a curva ellittica prime 384 bit (ECDSA)<br>-Utilizzo della chiave SHA 256:<br>CERT_DIGITAL_SIGNATURE_KEY_USAGE<br>-CERT_KEY_CERT_SIGN_KEY_USAGE<br>CERT_CRL_SIGN_KEY_USAGE|30 anni|N/D
|Autorità di certificazione di ancoraggio|Curva P256 ECC|-Certificato host con crittografia a curva ellittica a 256 bit (ECC)<br>-Utilizzo della chiave SHA 256:<br>CERT_KEY_CERT_SIGN_KEY_USAGE<br>-Vincolo Lunghezza percorso = 0|20 anni|1.3.6.1.4.1.311.76.9.21.2<br>1.3.6.1.4.1.311.76.9.21.3|

   >[!NOTE]
   >La CA di ancoraggio deve essere esportata come file con estensione p7b.

### Requisiti per il provisioning dei certificati di amministrazione

Ogni dispositivo host deve avere la CA doc e due certificati come illustrato nella tabella 2.

#### Tabella 2. Requisiti per il provisioning dei certificati di amministrazione

|Certificato|Algoritmo|Descrizione|OID EKU|
|---|---|---|---|
|Certificato di autenticazione host|ECC P256<br>SHA 256|Dimostra l'identità del dispositivo host.|1.3.6.1.4.1.311.76.9.21.2|
|Certificato di amministrazione di provisioning|ECC P256<br>SHA256|Consente di modificare le impostazioni di proprietà e/o criteri di ancoraggio consentendo di sostituire la CA attualmente installata nel Dock.|1.3.6.1.4.1.311.76.9.21.3<br>1.3.6.1.4.1.311.76.9.21.4|

   >[!NOTE]
   >I certificati di autenticazione e di provisioning host devono essere esportati come file PFX.

### Creare un pacchetto di configurazione

Dopo aver ottenuto o creato i certificati, si è pronti a creare il pacchetto di configurazione MSI che verrà applicato ai dispositivi della superficie di destinazione.

1. Eseguire il **Configuratore UEFI**Surface.

   ![Eseguire il configuratore UEFI Surface](images/secure-surface-dock-ports-semm-1.png)

1. Selezionare **Surface Dock**.

   ![Selezionare Surface Dock](images/secure-surface-dock-ports-semm-2.png)

1. Nella pagina certificato immettere i **certificati**appropriati.

   ![Immettere i certificati appropriati](images/secure-surface-dock-ports-semm-3.png)

1. Aggiungere il Dock RNs appropriato all'elenco.

   >[!NOTE]
   >Quando si crea un pacchetto di configurazione per più dispositivi Surface Dock 2, invece di immettere manualmente ogni RN, è possibile usare un file CSV che contiene un elenco di RNs.

1. Specificare le impostazioni dei criteri per le porte USB, Ethernet e audio. UEFI Configurator consente di configurare le impostazioni dei criteri per gli utenti autenticati (criteri autenticati) e gli utenti non autenticati (criteri non autenticati). La figura seguente mostra l'accesso alla porta attivato per gli utenti autenticati e disattivato per gli utenti non autenticati.

   ![Scegliere i componenti che si desidera attivare o disattivare.](images/secure-surface-dock-ports-semm-4.png)

   - L'utente autenticato fa riferimento a un dispositivo Surface con i certificati appropriati installati, come configurato in. Pacchetto di configurazione MSI applicato ai dispositivi di destinazione. Si applica a qualsiasi utente autenticato dall'utente che accede al dispositivo. 
   - L'utente non autenticato fa riferimento a qualsiasi altro dispositivo.
   - Selezionare **Reimposta** per creare un pacchetto "reset" speciale che eliminerà qualsiasi pacchetto di configurazione precedente accettato dal Dock.

1. Selezionare **Compila** per creare il pacchetto come specificato.

### Applicare il pacchetto di configurazione a una superficie Dock 2

1. È stato creato il file MSI di Surface UEFI Configurator e installato in un dispositivo host Surface. I dispositivi host compatibili sono Surface Book 3, Surface laptop 3 o Surface Pro 7.
1. Connettere il dispositivo host al Dock Surface 2. Quando si collegano le impostazioni dei criteri di dock UEFI vengono applicate.

## Verificare lo stato gestito con l'app Surface

Dopo aver applicato il pacchetto di configurazione, è possibile verificare rapidamente lo stato dei criteri risultante del Dock direttamente dall'app Surface, installato per impostazione predefinita in tutti i dispositivi Surface. Se l'app Surface non è presente nel dispositivo, è possibile scaricarla e installarla da Microsoft Store.

### Scenario di test

Obiettivo: configurare le impostazioni dei criteri per consentire l'accesso tramite la porta solo agli utenti autenticati.

1. Attivare tutte le porte per gli utenti autenticati e disattivarle per gli utenti non autenticati.

   ![Abilitazione delle porte per gli utenti autenticati](images/secure-surface-dock-ports-semm-4.png)

1. Applicare il pacchetto di configurazione al dispositivo di destinazione e quindi connettere Surface Dock 2.

1. Aprire l' **app Surface** e selezionare **Surface Dock** per visualizzare lo stato dei criteri risultante della superficie di ancoraggio. Se vengono applicate le impostazioni dei criteri, l'app Surface indicherà che le porte sono disponibili.

   ![App Surface Mostra che tutte le porte sono disponibili per gli utenti autenticati](images/secure-surface-dock-ports-semm-5.png)

1. Ora è necessario verificare che le impostazioni dei criteri abbiano disattivato tutte le porte per gli utenti non autenticati. Connettere Surface Dock 2 a un dispositivo non gestito, ad esempio qualsiasi dispositivo Surface esterno all'ambito di gestione per il pacchetto di configurazione creato.

1. Aprire l' **app Surface** e selezionare **Surface Dock**. Lo stato dei criteri risultante indicherà che le porte sono disattivate.

   ![App Surface che mostra le porte disattivate per gli utenti non autenticati ](images/secure-surface-dock-ports-semm-6.png)

>[!NOTE]
>Se si vuole conservare la proprietà del dispositivo, ma consentire a tutti gli utenti l'accesso completo, è possibile creare un nuovo pacchetto con tutto ciò che è stato attivato. Se si vuole rimuovere completamente le restrizioni e la proprietà del dispositivo (renderlo non gestito), selezionare **Reimposta** in Surface UEFI Configurator per creare un pacchetto da applicare ai dispositivi di destinazione.

Congratulazioni. Sono state gestite correttamente le porte di Surface Dock 2 nei dispositivi host mirati.

## Scopri di più

- [Documentazione sulla modalità di gestione di Surface Enterprise (SEMM)](https://docs.microsoft.com/surface/surface-enterprise-management-mode)
- [Architettura di Servizi certificati](https://docs.microsoft.com/windows/win32/seccrypto/certificate-services-architecture)
- [Windows Server 2019 inside out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)
- [PKI di Windows Server 2008 e sicurezza del certificato](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)

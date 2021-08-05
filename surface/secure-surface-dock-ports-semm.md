---
title: Secure Surface Dock 2 ports with Surface Enterprise Management Mode (SEMM)
description: Questo documento fornisce indicazioni per la configurazione delle impostazioni delle porte UEFI per Surface Dock 2 quando si è connessi a dispositivi Surface compatibili, tra cui Surface Book 3, Surface Laptop 3 e Surface Pro 7.
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
ms.date: 08/02/2021
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 9a98eb9bab9b0be7f225dedf00ee6cfe7944b05e
ms.sourcegitcommit: 657d0d73a51f0dd35ad60740ed523164a55d2e04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2021
ms.locfileid: "11720930"
---
# <a name="secure-surface-dock-2-ports-with-surface-enterprise-management-mode-semm"></a>Secure Surface Dock 2 ports with Surface Enterprise Management Mode (SEMM)

## <a name="introduction"></a>Introduzione

La modalità di gestione di Surface Enterprise (SEMM) consente agli amministratori IT di proteggere e gestire le porte di Surface Dock 2 configurando le impostazioni UEFI in un pacchetto di configurazione del programma di installazione di Windows (file .msi) distribuito ai dispositivi Surface compatibili in un ambiente aziendale.

### <a name="supported-devices"></a>Dispositivi supportati

La gestione di Surface Dock 2 con SEMM è disponibile per i dock collegati a Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Laptop Go, Surface Pro 7+, Surface Pro 7 e Surface Pro X. Questi dispositivi Surface compatibili sono comunemente denominati **dispositivi host.** Un pacchetto viene applicato ai dispositivi host in base al caso in cui un dispositivo host sia **autenticato** o **non autenticato.** Le impostazioni configurate risiedono nel livello UEFI nei dispositivi host che consentono all'amministratore IT di gestire Surface Dock 2 come qualsiasi altra periferica incorporata, ad esempio la fotocamera.

>[!NOTE]
>Puoi gestire le porte di Surface Dock 2 solo quando il dock è connesso a uno dei seguenti dispositivi compatibili: Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Pro 7+ e Surface Pro 7. Qualsiasi dispositivo che non riceve le impostazioni dei criteri UEFI Authenticated è intrinsecamente un dispositivo non autenticato.

### <a name="scenarios"></a>Scenari

La limitazione di Surface Dock 2 alle persone autorizzate che hanno effettuato l'accesso a un dispositivo host aziendale offre un altro livello di protezione dei dati. Questa possibilità di bloccare Surface Dock 2 è fondamentale per clienti specifici in ambienti altamente sicuri che desiderano i vantaggi di funzionalità e produttività del dock, pur mantenendo la conformità a rigidi protocolli di sicurezza. Prevediamo che SEMM usato con Surface Dock 2 sarà particolarmente utile negli uffici aperti e negli spazi condivisi, soprattutto per i clienti che desiderano bloccare le porte USB per motivi di sicurezza. Per una demo video, consulta [SEMM per Surface Dock 2.](https://youtu.be/VLV19ISvq_s)

## <a name="configuring-and-deploying-uefi-settings-for-surface-dock-2"></a>Configurazione e distribuzione delle impostazioni UEFI per Surface Dock 2

In questa sezione vengono fornite istruzioni dettagliate per le attività seguenti:

1. Installare **Surface UEFI Configurator** da [Surface Tools for IT.](https://www.microsoft.com/download/details.aspx?id=46703)
1. Creare o ottenere certificati a chiave pubblica.
1. Crea un pacchetto .msi configurazione.
   1. Aggiungere i certificati.
   1. Immetti il numero RN a 16 cifre per i dispositivi Surface Dock 2.
   1. Configurare le impostazioni UEFI.
1. Crea e applica il pacchetto di configurazione ai dispositivi Surface di destinazione (Surface Book 3, Surface Laptop 3 o Surface Pro 7).

>[!NOTE]
>Il **numero casuale (RN)** è un identificatore di codice esadecimale univoco a 16 cifre, di cui viene eseguito il provisioning in fabbrica e stampato in piccolo tipo nella parte inferiore del dock. L'RN è diverso dalla maggior parte dei numeri di serie in quanto non può essere letto elettronicamente. In questo modo si garantisce che la prova di proprietà sia stabilita principalmente solo leggendo l'RN quando si accede fisicamente al dispositivo. L'RN può essere ottenuto anche durante la transazione di acquisto ed è registrato nei sistemi di inventario Microsoft.

### <a name="install-semm-and-surface-uefi-configurator"></a>Installare SEMM e Surface UEFI Configurator

Installare SEMM eseguendo **SurfaceUEFI_Configurator_v2.83.139.0.msi.** Si tratta di un programma di installazione autonomo e contiene tutto il necessario per creare e distribuire pacchetti di configurazione per Surface Dock 2.

- Scarica **Surface UEFI Configurator** da [Surface Tools for IT.](https://www.microsoft.com/download/details.aspx?id=46703)

## <a name="create-public-key-certificates"></a>Creare certificati a chiave pubblica

Questa sezione fornisce le specifiche per la creazione dei certificati necessari per gestire le porte per Surface Dock 2.

### <a name="prerequisites"></a>Prerequisiti

In questo articolo si presuppone che si ottengono certificati da un provider di terze parti o si dispone già di competenze in servizi certificati PKI e si sa come crearne di propri.  Dovresti avere familiarità con e seguire i consigli generali per la creazione dei certificati, come descritto nella documentazione relativa alla modalità di gestione di [Surface Enterprise (SEMM),](surface-enterprise-management-mode.md) con un'eccezione. I certificati documentati in questa pagina richiedono termini di scadenza di 30 anni per l'Autorità di certificazione **dock**e di 20 anni per il certificato di **autenticazione host.**

Per ulteriori informazioni, vedere la documentazione [relativa](/windows/win32/seccrypto/certificate-services-architecture) all'architettura di Servizi certificati ed esaminare i capitoli appropriati in [Windows Server 2019 Inside Out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)o Windows Server [2008 PKI e Certificate Security](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788) disponibili da Microsoft Press.

### <a name="root-and-host-certificate-requirements"></a>Requisiti dei certificati radice e host

Prima di creare il pacchetto di configurazione, devi preparare i certificati a chiave pubblica che autenticano la proprietà di Surface Dock 2 e facilitano eventuali modifiche successive della proprietà durante il ciclo di vita del dispositivo. I certificati host e di provisioning richiedono l'immissione di ID EKU altrimenti noti come identificatori di oggetto **EKU (Enhanced Key Usage)** dell'autenticazione client .

I valori EKU necessari sono elencati nella tabella 1 e nella tabella 2.

#### <a name="table-1-root-and-dock-certificate-requirements"></a>Tabella 1. Requisiti dei certificati radice e dock

|Certificato|Algoritmo|Descrizione|Scadenza|EKU OID|
|---|---|---|---|---|
|Autorità di certificazione radice|ECDSA_P384|- Certificato radice con algoritmo ECDSA (Prime Elliptic Curve Digital Signature Algorithm) a 384 bit<br>- Sha 256 Utilizzo chiave:<br>CERT_DIGITAL_SIGNATURE_KEY_USAGE<br>- CERT_KEY_CERT_SIGN_KEY_USAGE<br>CERT_CRL_SIGN_KEY_USAGE|30 anni|N/D
|Autorità di certificazione dock|Curva ECC P256|- Certificato host con crittografia a curva ellittica a 256 bit (ECC)<br>- Sha 256 Utilizzo chiave:<br>CERT_KEY_CERT_SIGN_KEY_USAGE<br>- Vincolo lunghezza percorso = 0|20 anni|1.3.6.1.4.1.311.76.9.21.2<br>1.3.6.1.4.1.311.76.9.21.3|

   >[!NOTE]
   >L'autorità di certificazione dock deve essere esportata come file p7b.

### <a name="provisioning-administration-certificate-requirements"></a>Requisiti dei certificati di amministrazione del provisioning

Ogni dispositivo host deve avere l'autorità di certificazione doc e due certificati, come illustrato nella tabella 2.

#### <a name="table-2-provisioning-administration-certificate-requirements"></a>Tabella 2. Requisiti dei certificati di amministrazione del provisioning

|Certificato|Algoritmo|Descrizione|EKU OID|
|---|---|---|---|
|Certificato di autenticazione host|ECC P256<br>SHA 256|Prova l'identità del dispositivo host.|1.3.6.1.4.1.311.76.9.21.2|
|Provisioning del certificato di amministrazione|ECC P256<br>SHA256|Consente di modificare la proprietà e/o le impostazioni dei criteri del dock, consentendo di sostituire l'autorità di certificazione attualmente installata nel dock.|1.3.6.1.4.1.311.76.9.21.3<br>1.3.6.1.4.1.311.76.9.21.4|

   >[!NOTE]
   >I certificati di autenticazione e provisioning host devono essere esportati come file pfx.

### <a name="create-configuration-package"></a>Creare un pacchetto di configurazione

Dopo aver ottenuto o creato i certificati, sei pronto per creare il pacchetto di configurazione .msi che verrà applicato ai dispositivi Surface di destinazione.

1. Eseguire Surface **UEFI Configurator**.

   ![Eseguire Surface UEFI Configurator](images/secure-surface-dock-ports-semm-1.png)

1. Seleziona **Surface Dock.**

   ![Seleziona Surface Dock](images/secure-surface-dock-ports-semm-2.png)

1. Immettere i certificati **appropriati**  nella pagina del certificato. I certificati demo sono disponibili da [Surface Tools per IT:](https://www.microsoft.com/download/details.aspx?id=46703) ** scarica **SEMM_PowerShell.zipe fai riferimento ** aCreateSurfaceDock2Certificates.ps1**. Assicurati di installare **SurfaceDock2_WmiInstanceProvider** prima di eseguire gli script demo.

   ![immettere i certificati appropriati](images/secure-surface-dock-ports-semm-3.png)

1. Aggiungere gli RN dock appropriati all'elenco.

   >[!TIP]
   >Quando crei un pacchetto di configurazione per più dispositivi Surface Dock 2, invece di immettere manualmente ogni RN, puoi usare un file .csv contenente un elenco di RN.

1. Specificare le impostazioni dei criteri per le porte dati USB, Ethernet e Audio. UeFI Configurator consente di configurare le impostazioni dei criteri per gli utenti autenticati (Criterio autenticato) e gli utenti non autenticati (Criteri non autenticati). Nella figura seguente viene illustrato l'accesso alla porta attivato per gli utenti autenticati e disattivato per gli utenti non autenticati.

   ![Scegliere i componenti che si desidera attivare o disattivare.](images/secure-surface-dock-ports-semm-4.png)

   - L'utente autenticato fa riferimento a un dispositivo Surface in cui sono installati i certificati appropriati, come configurato nel pacchetto di configurazione .msi applicato ai dispositivi di destinazione. Si applica a qualsiasi utente autenticato che accede al dispositivo.
   - L'utente non autenticato fa riferimento a qualsiasi altro dispositivo.
   - Seleziona **Reimposta** per creare uno speciale pacchetto "Reimposta" che rimuoverà qualsiasi pacchetto di configurazione precedente accettato dal dock.

1. Seleziona **Compila** per creare il pacchetto come specificato.

### <a name="apply-the-configuration-package-to-a-surface-dock-2"></a>Applicare il pacchetto di configurazione a un Surface Dock 2

1. Prendi il file .msi generato dal configuratore UEFI di Surface e installalo in un dispositivo host Surface. I dispositivi host compatibili Surface Book 3, Surface Laptop 3 o Surface Pro 7.
1. Connessione il dispositivo host al Surface Dock 2. Quando si connettono le impostazioni dei criteri UEFI dock vengono applicate.

## <a name="verify-managed-state-using-the-surface-app"></a>Verificare lo stato gestito con l'app Surface

Dopo aver applicato il pacchetto di configurazione, puoi verificare rapidamente lo stato dei criteri risultante del dock direttamente dall'app Surface, installata per impostazione predefinita in tutti i dispositivi Surface. Se Surface App non è presente nel dispositivo, puoi scaricarla e installarla dal Microsoft Store.

### <a name="test-scenario"></a>Scenario di test

Obiettivo: configurare le impostazioni dei criteri per consentire l'accesso alla porta solo da parte di utenti autenticati.

1. Attivare tutte le porte per gli utenti autenticati e disattivarle per gli utenti non autenticati.

   ![Abilitazione delle porte per gli utenti autenticati](images/secure-surface-dock-ports-semm-4.png)

1. Applica il pacchetto di configurazione al dispositivo di destinazione e quindi connetti Surface Dock 2.

1. Apri **Surface App** e seleziona Surface **Dock** per visualizzare lo stato dei criteri risultante del Surface Dock. Se vengono applicate le impostazioni dei criteri, Surface App indicherà che le porte sono disponibili.

   ![L'app Surface mostra che tutte le porte sono disponibili per gli utenti autenticati](images/secure-surface-dock-ports-semm-5.png)

1. Ora è necessario verificare che le impostazioni dei criteri siano state disattivate correttamente tutte le porte per gli utenti non autenticati. Connessione Surface Dock 2 a un dispositivo non gestito, ad esempio qualsiasi dispositivo Surface esterno all'ambito di gestione per il pacchetto di configurazione creato.

1. Apri **Surface App** e seleziona Surface **Dock.** Lo stato dei criteri risultante indicherà che le porte sono disattivate.

   ![App Surface che mostra le porte disattivate per gli utenti non autenticati ](images/secure-surface-dock-ports-semm-6.png)

>[!TIP]
>Se vuoi mantenere la proprietà del dispositivo, ma consentire a tutti gli utenti l'accesso completo, puoi creare un nuovo pacchetto con tutto attivato. Se vuoi rimuovere completamente le restrizioni e la proprietà del dispositivo (renderlo non gestito), seleziona Reimposta **in** Configuratore UEFI di Surface per creare un pacchetto da applicare ai dispositivi di destinazione.

Congratulazioni. Le porte Surface Dock 2 sono state gestite correttamente nei dispositivi host di destinazione.

## <a name="learn-more"></a>Altre informazioni

- [Documentazione di Surface Enterprise Management Mode (SEMM)](surface-enterprise-management-mode.md)
- [Architettura di Servizi certificati](/windows/win32/seccrypto/certificate-services-architecture)
- [Windows Server 2019 Inside Out](https://www.microsoftpressstore.com/store/windows-server-2019-inside-out-9780135492277)
- [Windows Server 2008 PKI e sicurezza dei certificati](https://www.microsoftpressstore.com/store/windows-server-2008-pki-and-certificate-security-9780735640788)

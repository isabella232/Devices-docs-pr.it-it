---
title: Modalità di gestione di Surface Enterprise (Surface)
description: Ecco come questa caratteristica dei dispositivi Surface con UEFI Surface consente di proteggere e gestire le impostazioni del firmware all'interno dell'organizzazione.
keywords: UEFI, configura, firmware, Secure, SEMM
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices, security
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
audience: itpro
ms.date: 01/15/2021
ms.openlocfilehash: e6f81639253c646f5d3956243a80f4d61c91028a
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271420"
---
# Modalità di gestione Microsoft Surface Enterprise

Microsoft Surface Enterprise Management Mode (SEMM) è una caratteristica dei dispositivi Surface con UEFI di Surface che consente di proteggere e gestire le impostazioni del firmware all'interno dell'organizzazione. Con SEMM, i professionisti IT possono preparare configurazioni di impostazioni UEFI e installarle su un dispositivo Surface. Oltre alla possibilità di configurare le impostazioni UEFI, SEMM usa anche un certificato per proteggere la configurazione da manomissioni o rimozione non autorizzate. SEMM è un requisito per poter eseguire la migrazione di un hub di Surface 2S a Windows 10 Pro e Enterprise.

>[!NOTE]
>SEMM è disponibile solo nei dispositivi con il firmware di Surface UEFI. Questo include la maggior parte degli altri dispositivi Surface, tra cui Surface Pro 7 +, Surface Pro X, Surface Hub 2S e Surface laptop 3 SKU commerciali con un processore Intel e Surface laptop go. SEMM non è supportato nella SKU 15 "Surface laptop 3 con processore AMD (disponibile solo come SKU per il dettaglio). 

Quando i dispositivi Surface sono configurati da SEMM e protetti con il certificato SEMM, vengono considerati *registrati* in SEMM. Quando il certificato SEMM viene rimosso e il controllo delle impostazioni UEFI viene restituito all'utente del dispositivo, il dispositivo Surface *viene considerato non* registrato in SEMM.

È possibile usare due opzioni amministrative per gestire SEMM e registrare i dispositivi Surface, uno strumento autonomo o un'integrazione con Microsoft endpoint Configuration Manager. In questo articolo è descritto lo strumento autonomo SEMM, chiamato Microsoft Surface UEFI Configurator. Per altre informazioni su come gestire SEMM con Microsoft endpoint Configuration Manager, vedere [usare Microsoft endpoint Configuration Manager per gestire i dispositivi con SEMM](https://technet.microsoft.com/itpro/surface/use-system-center-configuration-manager-to-manage-devices-with-semm).


## Microsoft Surface UEFI Configurator

L'area di lavoro principale di SEMM è Microsoft Surface UEFI Configurator, come illustrato nella figura 1. Microsoft Surface UEFI Configurator è uno strumento usato per creare pacchetti di Windows Installer (con estensione msi) o immagini WinPE usate per registrare, configurare e annullare la registrazione di SEMM in un dispositivo Surface. Questi pacchetti contengono un file di configurazione in cui vengono specificate le impostazioni per UEFI. I pacchetti SEMM contengono anche un certificato, che viene installato e archiviato nel firmware e usato per verificare la firma dei file di configurazione prima dell'applicazione delle impostazioni UEFI.

>[!NOTE]
>Ora è possibile usare Surface UEFI Configurator e SEMM per gestire le porte in Surface Dock 2. Per altre informazioni, vedere [proteggere le porte di Surface Dock 2 con SEMM](secure-surface-dock-ports-semm.md).

![Microsoft Surface UEFI Configurator](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*Figura 1. Microsoft Surface UEFI Configurator*


È possibile usare lo strumento Microsoft Surface UEFI Configurator in tre modi:

* [Pacchetto di configurazione UEFI di Surface](#configuration-package). Usare questa modalità per creare un pacchetto di configurazione UEFI di Surface per la registrazione di un dispositivo Surface in SEMM e per configurare le impostazioni UEFI nei dispositivi registrati.
* [Pacchetto di ripristino di Surface UEFI](#reset-package). Usare questa modalità per annullare la registrazione di un dispositivo Surface da SEMM.
* [Richiesta di ripristino di Surface UEFI](#recovery-request). Usa questa modalità per rispondere a una richiesta di ripristino per annullare la registrazione di un dispositivo Surface da SEMM in cui un'operazione di reimpostazione del pacchetto non riesce.


#### Scarica Microsoft Surface UEFI Configurator

È possibile scaricare Microsoft Surface UEFI Configurator dalla pagina [strumenti superficie per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.

### Pacchetto di configurazione

I pacchetti di configurazione UEFI di Surface sono il meccanismo principale per implementare e gestire SEMM su dispositivi Surface. Questi pacchetti contengono un file di configurazione delle impostazioni UEFI specificato durante la creazione del pacchetto in Microsoft Surface UEFI Configurator e un file di certificato, come illustrato nella figura 2. Quando viene eseguito un pacchetto di configurazione per la prima volta su un dispositivo Surface non già registrato in SEMM, il file del certificato viene disposto nel firmware del dispositivo e il dispositivo viene registrato in SEMM. Quando si effettua la registrazione di un dispositivo in SEMM, verrà richiesto di confermare l'operazione fornendo le ultime due cifre dell'identificazione personale del certificato SEMM prima che il file di certificato sia archiviato e la registrazione possa essere completata. Questa conferma richiede che un utente sia fisicamente presente al dispositivo al momento dell'iscrizione per eseguire la conferma.

![Proteggere un pacchetto di configurazione di SEMM con un certificato](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*Figura 2. Proteggere un pacchetto di configurazione di SEMM con un certificato*

Per altre informazioni sui requisiti per il certificato SEMM, vedere la sezione [requisiti di certificato in modalità di gestione di Surface Enterprise](#surface-enterprise-management-mode-certificate-requirements) in questo articolo.

>[!NOTE]
>È anche possibile specificare una password UEFI con SEMM necessaria per visualizzare la **sicurezza**, i **dispositivi**, la **configurazione di avvio**o le pagine di **gestione aziendale** di Surface UEFI.

Dopo che un dispositivo è stato registrato in SEMM, il file di configurazione viene letto e le impostazioni specificate nel file vengono applicate a UEFI. Quando si esegue un pacchetto di configurazione in un dispositivo già registrato in SEMM, la firma del file di configurazione viene controllata in base al certificato archiviato nel firmware del dispositivo. Se la firma non corrisponde, non vengono applicate modifiche al dispositivo.

### Abilitare o disabilitare dispositivi in UEFI di Surface con SEMM

L'elenco seguente mostra tutti i dispositivi disponibili che è possibile gestire in SEMM:

* Porta USB di ancoraggio
* Audio integrato
* DGPU
* Cover con tasti
* Scheda micro SD
* Front Camera
* Rear Camera
* Videocamera ad infrarossi, per Windows Hello
* Solo Bluetooth
* Wi-Fi e Bluetooth
*              LTE           

 >[!NOTE]
>I dispositivi predefiniti visualizzati nella pagina Dispositivi UEFI possono variare a seconda del dispositivo o dell'ambiente aziendale. Ad esempio, la pagina Dispositivi UEFI non è supportata in Surface Pro X; LTE viene visualizzato solo nei dispositivi dotati di LTE. 
### Configurare le impostazioni avanzate con SEMM
**Tabella 1. Impostazioni avanzate**

| Impostazione                            | Descrizione                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Avvio di IPv6 per PXE                  | Consente di gestire il supporto IPv6 per l'avvio PXE. Se non si configura questa impostazione, il supporto IPv6 per l'avvio PXE è disabilitato.                                                                               |
| Avvio alternativo                     | Consente di gestire l'uso di un ordine di avvio alternativo per l'avvio diretto a un dispositivo USB o Ethernet premendo sia il pulsante volume giù che il pulsante Power durante l'avvio. Se non si configura questa impostazione, è abilitato l'avvio alternativo. |
| Blocco ordine di avvio                    | Consente di bloccare l'ordine di avvio per evitare modifiche. Se non si configura questa impostazione, il blocco dell'ordine di avvio è disabilitato.                                                                                                        |
| Avvio da USB                           | Consente di gestire l'avvio in dispositivi USB. Se non si configura questa impostazione, l'avvio USB è abilitato.                                                                                                                 |
| Stack di rete                      | Consente di gestire le impostazioni di avvio dello stack di rete. Se non si configura questa impostazione, la possibilità di gestire le impostazioni di avvio dello stack di rete è disabilitata.                                                                                                           |
| Accensione automatica                      | Consente di gestire l'alimentazione automatica sulle impostazioni di avvio. Se non si configura questa impostazione, l'opzione di attivazione automatica è abilitata.                                                                                                        |
| Multithreading simultaneo (SMT) | Consente di gestire il multithreading simultaneo (SMT) per abilitare o disabilitare l'hyperthreading. Se non si configura questa impostazione, SMT è abilitato.                                                  |
|Abilitare il limite di batteria| Consente di gestire la funzionalità limite batteria. Se non si configura questa impostazione, il limite di batteria è abilitato |
| Sicurezza                           | Visualizza la pagina **sicurezza** UEFI di Surface. Se non si configura questa impostazione, verrà visualizzata la pagina sicurezza.                                                                                                                 |
| Dispositivi                            | Visualizza la pagina **dispositivi** UEFI di Surface. Se non si configura questa impostazione, verrà visualizzata la pagina dispositivi.                                                                                                                     |
| Avvio                               | Visualizza la pagina di **avvio** di Surface UEFI. Se non si configura questa impostazione, viene visualizzata la pagina di avvio.                                                                                                                                                            |
| DateTime                           | Visualizza la pagina **DateTime** di Surface UEFI. Se non si configura questa impostazione, verrà visualizzata la pagina DateTime.                                                                                                                |
| EnableOSMigration                          | Consente di eseguire la migrazione di Surface Hub 2 dal team di Windows 10 a Windows 10 Pro o Enterprise. Se non si configura questa impostazione, i dispositivi Surface Hub 2 possono eseguire solo il sistema operativo Windows 10 team.   Nota: il dual boot tra il team Windows 10 e Windows 10 Pro/Enterprise non è disponibile in Surface Hub 2.                                                                                                           |


>[!NOTE]
>Quando crei un pacchetto di configurazione di SEMM, nella pagina di **successo** vengono visualizzati due caratteri, come illustrato nella figura 3.

![Visualizzazione identificazione personale del certificato](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*Figura 3. Visualizzazione degli ultimi due caratteri dell'identificazione personale del certificato nella pagina riuscita*

Questi caratteri sono gli ultimi due caratteri dell'identificazione personale del certificato e devono essere scritti o registrati. I caratteri sono necessari per confermare la registrazione in SEMM su un dispositivo Surface, come illustrato nella figura 4.

![Conferma di registrazione in SEMM](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*Figura 4. Conferma della registrazione in SEMM con l'identificazione personale del certificato SEMM*

>[!NOTE]
>Gli amministratori con accesso al file di certificato (con estensione pfx) possono leggere l'identificazione personale in qualsiasi momento aprendo il file pfx in CertMgr. Per visualizzare l'identificazione personale con CertMgr, seguire questa procedura:
>1. Fare clic con il pulsante destro del mouse sul file PFX e quindi scegliere **Apri**.
>2. Espandere la cartella nel riquadro di spostamento.
>3. Fare clic su **Certificati**.
>4. Fare clic con il pulsante destro del mouse sul certificato nel riquadro principale e quindi scegliere **Apri**.
>5. Fare clic sulla scheda **Dettagli** .
>6. È necessario selezionare solo **tutte le** **proprietà o solo** nel menu a discesa **Mostra** .
>7. Selezionare l' **identificazione personale**del campo.

Per registrare un dispositivo Surface in SEMM o per applicare la configurazione UEFI da un pacchetto di configurazione, è sufficiente eseguire il file con estensione msi con privilegi amministrativi nel dispositivo Surface previsto. Puoi usare le tecnologie di distribuzione delle applicazioni o del sistema operativo, ad esempio [Microsoft endpoint Configuration Manager](https://technet.microsoft.com/library/mt346023) o [Microsoft Deployment Toolkit](https://technet.microsoft.com/windows/dn475741). Quando si esegue la registrazione di un dispositivo in SEMM, è necessario essere fisicamente presenti per confermare l'iscrizione nel dispositivo. L'interazione dell'utente non è necessaria quando si applica una configurazione ai dispositivi già registrati in SEMM.

Per una procedura dettagliata su come registrare un dispositivo Surface in SEMM o applicare una configurazione UEFI di Surface con SEMM, vedere [registrare e configurare i dispositivi Surface con SEMM](https://technet.microsoft.com/itpro/surface/enroll-and-configure-surface-devices-with-semm).

### Reimposta pacchetto

Per eseguire una sola attività, viene usato un pacchetto di reimpostazione UEFI di Surface per annullare la registrazione di un dispositivo Surface da SEMM. Il pacchetto di reimpostazione contiene le istruzioni firmate per rimuovere il certificato SEMM dal firmware del dispositivo e per reimpostare le impostazioni di UEFI in Factory default. Come un pacchetto di configurazione UEFI di Surface, un pacchetto di reimpostazione deve essere firmato con lo stesso certificato SEMM di cui viene eseguito il provisioning nel dispositivo Surface. Quando si crea un pacchetto di reimpostazione di SEMM, è necessario specificare il numero seriale del dispositivo Surface che si vuole reimpostare. I pacchetti di reimpostazione di SEMM non sono universali e sono specifici di un dispositivo.

### Richiesta di ripristino

In alcuni scenari può essere Impossibile usare un pacchetto di ripristino di Surface UEFI. Ad esempio, se Windows diventa inutilizzabile nel dispositivo Surface. In questi scenari puoi annullare la registrazione del dispositivo Surface da SEMM tramite la pagina **gestione aziendale** di Surface UEFI (illustrato nella figura 5) con un'operazione di richiesta di ripristino.

![Avviare una richiesta di ripristino SEMM](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*Figura 5. Avviare una richiesta di ripristino di SEMM nella pagina Gestione aziendale*

Quando si usa il processo nella pagina **gestione aziendale** per reimpostare SEMM su un dispositivo Surface, viene fornita una richiesta di reimpostazione. Questa richiesta di reimpostazione può essere salvata come file in un'unità USB, copiata come testo o letta come codice QR con un dispositivo mobile per essere facilmente inviata tramite posta elettronica o messaged. Usare l'opzione di reimpostazione della richiesta Reimposta Microsoft Surface UEFI Configurator per caricare un file di richiesta di reimpostazione o immettere il testo della richiesta di reimpostazione o il codice QR. Microsoft Surface UEFI Configurator genera un codice di verifica che può essere immesso nel dispositivo Surface. Se si immette il codice nel dispositivo Surface e si fa clic su **Riavvia**, il dispositivo non verrà registrato da SEMM. 

>[!NOTE]
>Una richiesta di reimpostazione scade due ore dopo la creazione.

Per una procedura dettagliata su come annullare la registrazione di dispositivi Surface da SEMM, vedere annullare la [registrazione dei dispositivi Surface da SEMM](https://technet.microsoft.com/itpro/surface/unenroll-surface-devices-from-semm).

## Requisiti dei certificati della modalità di gestione di Surface Enterprise
L'uso di SEMM con Microsoft Surface UEFI Configurator richiede un certificato per verificare la firma dei file di configurazione prima che le impostazioni di UEFI possano essere applicate. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, sia possibile usare solo i pacchetti creati con il certificato approvato per modificare le impostazioni di UEFI.

>[!NOTE]
>Il certificato SEMM è necessario per eseguire qualsiasi modifica a SEMM o alle impostazioni di Surface UEFI nei dispositivi della superficie registrata. Se il certificato SEMM è danneggiato o perso, SEMM non può essere rimosso o reimpostato. Gestire di conseguenza il certificato SEMM con una soluzione appropriata per il backup e il ripristino.

I pacchetti creati con lo strumento Microsoft Surface UEFI Configurator sono firmati con un certificato. Questo certificato garantisce che, dopo la registrazione di un dispositivo in SEMM, sia possibile usare solo i pacchetti creati con il certificato approvato per modificare le impostazioni di UEFI. 
### Impostazioni di certificato consigliate
Per il certificato SEMM sono consigliate le impostazioni seguenti:

* **Algoritmo Key** -RSA 
* **Lunghezza chiave** -2048
* **Algoritmo hash** -SHA-256
* **Tipo** -autenticazione server SSL
* **Uso chiave** -firma digitale, crittografia chiave
* **Provider** : Microsoft Enhanced RSA e AES Cryptographic Provider
* **Data di scadenza** -15 mesi dalla creazione di certificati
* **Criteri di esportazione chiave** -esportabili

Si consiglia inoltre di autenticare il certificato SEMM in un'architettura a chiave pubblica (PKI) a due livelli, in cui l'autorità di certificazione intermedia è dedicata a SEMM, abilitando la revoca del certificato. Per altre informazioni su una configurazione PKI a due livelli, vedere [Guida di test lab: distribuzione di un annuncio CS Two-Tier gerarchia PKI](https://technet.microsoft.com/library/hh831348).

### Certificato autofirmato 
Puoi usare lo script di PowerShell di esempio seguente per creare un certificato autofirmato per l'uso in scenari di prova di concetto.
Per usare questo script, copiare il testo seguente in blocco note e salvare il file come script di PowerShell (con estensione ps1). 

> [!NOTE]
> Questo script crea un certificato con una password `12345678` . Il certificato generato da questo script non è consigliato per gli ambienti di produzione.
  
```powershell
if (-not (Test-Path "Demo Certificate"))  { New-Item -ItemType Directory -Force -Path "Demo Certificate" }
if (Test-Path "Demo Certificate\TempOwner.pfx") { Remove-Item "Demo Certificate\TempOwner.pfx" }

# Generate the Ownership private signing key with password 12345678
$pw = ConvertTo-SecureString "12345678" -AsPlainText -Force

$TestUefiV2 = New-SelfSignedCertificate `
  -Subject "CN=Surface Demo Kit, O=Contoso Corporation, C=US" `
  -Type SSLServerAuthentication `
  -HashAlgorithm sha256 `
  -KeyAlgorithm RSA `
  -KeyLength 2048 `
  -KeyUsage KeyEncipherment `
  -KeyUsageProperty All `
  -Provider "Microsoft Enhanced RSA and AES Cryptographic Provider" `
  -NotAfter (Get-Date).AddYears(25) `
  -TextExtension @("2.5.29.37={text}1.2.840.113549.1.1.1") `
  -KeyExportPolicy Exportable

$TestUefiV2 | Export-PfxCertificate -Password $pw -FilePath "Demo Certificate\TempOwner.pfx"
```

>[!IMPORTANT]
>Per l'uso con SEMM e Microsoft Surface UEFI Configurator, il certificato deve essere esportato con la chiave privata e con la password di protezione. Microsoft Surface UEFI Configurator richiede di selezionare il file di certificato SEMM (PFX) e la password del certificato quando necessario.

1.  Creare una cartella nell'unità C: in cui verrà salvato lo script; ad esempio, C:\SEMM.
2.  Copiare lo script di esempio in blocco note o in un editor di testo equivalente e salvare il file come script di PowerShell (con estensione ps1).
3.  Accedere al PC con le credenziali di amministratore e aprire una sessione di PowerShell con privilegi elevati.
4.  Verificare che le autorizzazioni siano impostate per consentire l'esecuzione di script. Per impostazione predefinita, gli script sono bloccati dall'esecuzione, a meno che non modifichiate il criterio di esecuzione. Per altre informazioni, vedere [informazioni sui criteri di esecuzione](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies).
5.  Al prompt dei comandi immettere il percorso completo dello script e quindi premere INVIO. Lo script crea un certificato demo denominato TempOwner. pfx.

In alternativa, puoi creare un certificato autofirmato usando PowerShell. Per altre informazioni, vedere la documentazione di PowerShell seguente: [New-SelfSignedCertificate](https://docs.microsoft.com/powershell/module/pkiclient/new-selfsignedcertificate).




>[!NOTE]
>Per le organizzazioni che usano una radice offline nell'infrastruttura PKI, Microsoft Surface UEFI Configurator deve essere eseguito in un ambiente connesso alla CA radice per autenticare il certificato SEMM. I pacchetti generati da Microsoft Surface UEFI Configurator possono essere trasferiti come file e quindi possono essere trasferiti all'esterno dell'ambiente di rete offline con uno spazio di archiviazione rimovibile, ad esempio una chiavetta USB.

### Domande frequenti sulla gestione dei certificati

La lunghezza *minima* consigliata è di 15 mesi. È possibile usare un certificato che scade in meno di 15 mesi o utilizzare un certificato che scade in più di 15 mesi.

>[!NOTE] 
>Quando un certificato scade, non viene rinnovato automaticamente. 


**Un certificato scaduto influirà sulla funzionalità dei dispositivi registrati di SEMM?**<br><br>
No, un certificato ha un impatto solo sulle attività di gestione degli amministratori IT in SEMM e non ha alcun effetto sulla funzionalità del dispositivo alla scadenza.


**Il pacchetto e il certificato di SEMM devono essere aggiornati in tutti i computer in cui si trova?**

Se si vuole che SEMM ripristini o il ripristino funzioni, il certificato deve essere valido e non scaduto. 

**È possibile creare pacchetti di ripristino in blocco per ogni superficie ordinata? Si può costruire uno che reimposta tutti i computer nell'ambiente?**

Gli esempi di PowerShell che creano un pacchetto di configurazione per un tipo di dispositivo specifico possono essere usati anche per creare un pacchetto di reimpostazione con numero seriale indipendente. Se il certificato è ancora valido, è possibile creare un pacchetto di reimpostazione tramite PowerShell per reimpostare SEMM.

## Cronologia versioni

### Versione 2.79.139.0

Questa versione di SEMM include:
- Supporto per Surface Pro 7 +
- Miglioramenti dell'esperienza utente


### Versione 2.78.139.0

Questa versione di SEMM include:

- Supporto per laptop Surface go e Surface Pro X
- Notifiche per la nuova versione di rilascio
- Possibilità di creare pacchetti personalizzati per la modifica della proprietà
- Correzioni di bug

### Versione 2.73.136.0

Questa versione di SEMM include:

- Ora l'audio può essere disabilitato in Surface Hub2S usando SEMM
- Supporto per Surface Pro X per dock 2
- Supporto per le operazioni correlate di UEFI Manager per dock 2
- Correzione bug di Surface go Reset pacchetto
- Supporto per la migrazione dei dispositivi Surface Hub 2 da Windows 10 Team OS a Windows 10 Pro o Enterprise.

### Versione 2.71.139.0

Questa versione di SEMM aggiunge il supporto per le caratteristiche di gestione di Surface Dock 2 per Surface Book 3, Surface laptop 3 e Surface Pro 7, tra cui:

- Abilitazione dell'audio (blocco/sblocco), porte Ethernet e USB
- Possibilità di creare pacchetti di ancoraggio per host autenticati e non autenticati

### Versione 2.70.130.0

Questa versione di SEMM include:

- Supporto per Surface Go 2
- Supporto per Surface Book 3
- Correzioni di bug


### Versione 2.59.139.0

* Supporto per i modelli Surface Pro 7, Surface Pro X e Surface laptop 3 13,5 "e 15" con processore Intel. Nota: il processore AMD Surface laptop 3 15 non è supportato.

- Supporto per la funzionalità riattiva in Power

### Versione 2.54.139.0
* Supporto per Surface Hub 2S
* Correzioni di bug

### Versione 2.43.136.0
* Supporto per l'abilitazione/disabilitazione di simulatenous multithreating 
* Opzioni separate per Wi-Fi e Bluetooth per alcuni dispositivi 
* Limite di batteria rimosso per Surface Studio 

### Versione 2.26.136.0
* Aggiungere il supporto di Surface Studio 2
* Caratteristica limite batteria

### Versione 2.21.136.0
* Aggiungere il supporto a Surface Pro 6
* Aggiungere il supporto per Surface laptop 2

### Versione 2.14.136.0
* Aggiungere il supporto per Surface go

### Versione 2.9.136.0
* Aggiungere il supporto a Surface Book 2
* Aggiungere il supporto per Surface Pro LTE
* Miglioramenti all'accessibilità

### Versione 1.0.74.0
* Aggiungere il supporto al portatile Surface
* Aggiungere il supporto a Surface Pro
* Correzioni di bug e miglioramenti generali

## Argomenti correlati

- [Registrare e configurare i dispositivi Surface con SEMM](enroll-and-configure-surface-devices-with-semm.md)
- [Annullare la registrazione dei dispositivi Surface da SEMM](unenroll-surface-devices-from-semm.md)
- [Proteggere le porte del Surface Dock 2 con SEMM](secure-surface-dock-ports-semm.md)

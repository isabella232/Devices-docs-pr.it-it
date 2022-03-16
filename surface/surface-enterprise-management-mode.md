---
title: Surface Enterprise Management Mode (Surface)
description: Scopri come questa funzionalità dei dispositivi Surface con Surface UEFI consente di proteggere e gestire le impostazioni del firmware all'interno dell'organizzazione.
keywords: uefi, configurare, firmware, sicuro, semm
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
ms.date: 12/08/2021
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 4e1d9b012b79fadc7876d3cd5d8004eee4955ea8
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449199"
---
# <a name="microsoft-surface-enterprise-management-mode"></a>Modalità di Enterprise Microsoft Surface

Microsoft Surface Enterprise Management Mode (SEMM) è una funzionalità dei dispositivi Surface con Surface Unified Extensible Firmware Interface (UEFI). È possibile utilizzare SEMM per:

- Proteggere e gestire le impostazioni del firmware nell'organizzazione.
- Preparare le configurazioni delle impostazioni UEFI e installarle in un dispositivo Surface.

SEMM usa anche un certificato per proteggere la configurazione da manomissioni o rimozioni non autorizzate. Per eseguire la migrazione di Surface Hub 2S a Windows 10 Pro o Windows Enterprise, è necessario SEMM.

## <a name="supported-devices"></a>Dispositivi supportati

SEMM è disponibile solo nei dispositivi con firmware UEFI di Surface, tra cui: 

- Surface Pro 8 (solo SKU commerciali)
- Surface Pro 4 e versioni successive (tutti gli SKU)
- Surface Pro X (tutti gli SKU)
- Surface Laptop edizione Standard (tutti gli SKU)
- Surface Laptop Studio (solo SKU commerciali) 
- Surface Hub 2S
- Surface Laptop 4 (solo SKU commerciali)
- Surface Laptop 3 (solo processori Intel)
- Surface Laptop Go 
- Surface Book (tutte le generazioni)
- Surface Go, Surface Go 2
- Surface Go 3 (solo SKU commerciali)
- Surface Studio 

>[!TIP]
> Le SKU commerciali (Surface per le aziende) vengono eseguite Windows 10 Pro/Enterprise o Windows 11 Pro/Enterprise; le SKU consumer vengono eseguite Windows 10/Windows 11 Home. Per altre informazioni, vedi [Visualizzare le informazioni di sistema](https://support.microsoft.com/windows/view-your-system-info-a965a8f2-0773-1d65-472a-1e747c9ebe00). 


## <a name="getting-started"></a>Attività iniziali 

Quando i dispositivi Surface sono configurati da SEMM e protetti con il certificato SEMM, vengono considerati *registrati* in SEMM. Quando il certificato SEMM viene rimosso e il controllo delle impostazioni UEFI viene restituito all'utente del dispositivo, il dispositivo Surface viene considerato non *in* registrazione in SEMM.

Esistono due opzioni amministrative che puoi usare per gestire SEMM e registrare i dispositivi Surface:

- Lo strumento autonomo SEMM, Configuratore UEFI di Microsoft Surface, è descritto in questo articolo.

- Integrazione con Microsoft Endpoint Configuration Manager. Per informazioni, vedi [Usare Microsoft Endpoint Configuration Manager per gestire i dispositivi con SEMM](use-system-center-configuration-manager-to-manage-devices-with-semm.md).

## <a name="microsoft-surface-uefi-configurator"></a>Configuratore UEFI di Microsoft Surface

L'area di lavoro principale di SEMM è Microsoft Surface UEFI Configurator, come illustrato nella figura 1.

Puoi usare il configuratore UEFI di Microsoft Surface per:

- Crea Windows installer (.msi) pacchetti.
- Usa le immagini WinPE per registrare, configurare e annullare la registrazione di SEMM in un dispositivo Surface.

Questi pacchetti contengono un file di configurazione che specifica le impostazioni UEFI. I pacchetti SEMM contengono anche un certificato installato e archiviato nel firmware e utilizzato per verificare la firma dei file di configurazione prima dell'applicazione delle impostazioni UEFI.

>[!TIP]
>Ora puoi usare Surface UEFI Configurator e SEMM per gestire le porte su Surface Dock 2. Per altre informazioni, vedi [Proteggere le porte di Surface Dock 2 con SEMM](secure-surface-dock-ports-semm.md).

![Configuratore UEFI di Microsoft Surface.](images/surface-ent-mgmt-fig1-uefi-configurator.png "Microsoft Surface UEFI Configurator")

*Figura 1. Configuratore UEFI di Microsoft Surface*

Puoi usare lo strumento configuratore UEFI di Microsoft Surface in tre modalità:

- [Pacchetto di configurazione UEFI di Surface](#configuration-package). Usa questa modalità per creare un pacchetto di configurazione UEFI di Surface per registrare un dispositivo Surface in SEMM e configurare le impostazioni UEFI nei dispositivi registrati.
- [Pacchetto di reimpostazione UEFI di Surface](#reset-package). Usa questa modalità per annullare la registrazione di un dispositivo Surface da SEMM.
- [Richiesta di ripristino UEFI di Surface](#recovery-request). Usa questa modalità per rispondere a una richiesta di ripristino per annullare la registrazione di un dispositivo Surface da SEMM in cui un'operazione di reimpostazione del pacchetto non riesce.

### <a name="download-microsoft-surface-uefi-configurator"></a>Scaricare Il configuratore UEFI di Microsoft Surface

Puoi scaricare il configuratore UEFI di Microsoft Surface dalla pagina [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft.

- Per i dispositivi Intel/AMD, scarica: **SurfaceUEFI_Configurator_v2.94.139.0_x64.msi**
- Per ARM dispositivi, scarica: **SurfaceUEFI_Configurator_v2.94.139.0_x86.msi.**

### <a name="configuration-package"></a>Pacchetto di configurazione

I pacchetti di configurazione UEFI di Surface sono il meccanismo principale per implementare e gestire SEMM nei dispositivi Surface. Questi pacchetti contengono un file di configurazione e un file di certificato, come illustrato nella figura 2. Il file di configurazione contiene le impostazioni UEFI specificate al momento della creazione del pacchetto in Configuratore UEFI di Microsoft Surface. Quando un pacchetto di configurazione viene eseguito per la prima volta in un dispositivo Surface che non è già registrato in SEMM, esegue il provisioning del file di certificato nel firmware del dispositivo e registra il dispositivo in SEMM. Quando si registra un dispositivo in SEMM e prima che il certificato venga archiviato e la registrazione venga completata, viene richiesto di confermare l'operazione fornendo le ultime due cifre dell'identificazione personale del certificato SEMM. Questa conferma richiede che un utente sia fisicamente presente nel dispositivo durante la registrazione per eseguire la conferma.

![Proteggere un pacchetto di configurazione SEMM con un certificato.](images/surface-ent-mgmt-fig2-securepackage.png "Secure a SEMM configuration package with a certificate")

*Figura 2. Proteggere un pacchetto di configurazione SEMM con un certificato*

Per altre informazioni sui requisiti per il certificato SEMM, vedi la sezione Requisiti dei certificati per la modalità di gestione di [Surface Enterprise](#surface-enterprise-management-mode-certificate-requirements) più avanti in questo articolo.

>[!TIP]
>È possibile richiedere una password UEFI con SEMM. In questo caso, la password è necessaria per visualizzare le pagine **Sicurezza, Dispositivi********, Configurazione** di avvio **** e gestione Enterprise di Surface UEFI.

Dopo la registrazione di un dispositivo in SEMM, il file di configurazione viene letto e le impostazioni specificate nel file vengono applicate a UEFI. Quando esegui un pacchetto di configurazione in un dispositivo già registrato in SEMM, la firma del file di configurazione viene verificata rispetto al certificato archiviato nel firmware del dispositivo. Se la firma non corrisponde, non viene applicata alcuna modifica al dispositivo.

### <a name="enable-or-disable-devices-in-surface-uefi-with-semm"></a>Abilitare o disabilitare i dispositivi in Surface UEFI con SEMM

L'elenco seguente mostra tutti i dispositivi disponibili che puoi gestire in SEMM:

- Porta USB di ancoraggio
- Audio di bordo
- Unità di elaborazione grafica digitale
- Copertina tipo
- Scheda Micro SD
- Fotocamera anteriore
- Fotocamera posteriore
- Fotocamera a infrarossi (per Windows Hello)
- Bluetooth solo
- Rete wireless e Bluetooth
- Evoluzione a lungo termine (LTE)

 >[!NOTE]
>Nella pagina Dispositivi UEFI, i dispositivi incorporati possono variare a seconda del dispositivo o dell'ambiente aziendale. Ad esempio, la pagina Dispositivi UEFI non è supportata in Surface Pro X; LTE viene visualizzato solo nei dispositivi dotati di LTE.

### <a name="configure-advanced-settings-with-semm"></a>Configurare le impostazioni avanzate con SEMM

**Tabella 1. Impostazioni avanzate**

| Impostazione                            | Descrizione                                                                                                                                                                                        |
| ---------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Avvio di IPv6 per PXE                  | Consente di gestire il supporto IPv6 per l'avvio PXE. Se non si configura questa impostazione, il supporto IPv6 per l'avvio PXE è disabilitato.                                                                               |
| Avvio alternativo                     | Consente di gestire l'uso di un ordine di avvio alternativo per l'avvio direttamente su un dispositivo USB o Ethernet premendo sia il pulsante Volume giù che il pulsante Di alimentazione durante l'avvio. Se non si configura questa impostazione, l'avvio alternativo è abilitato. |
| Blocco ordine di avvio                    | Consente di bloccare l'ordine di avvio per impedire modifiche. Se non si configura questa impostazione, Boot Order Lock è disabilitato.                                                                                                        |
| Avvio da USB                           | Consente di gestire l'avvio in dispositivi USB. Se non si configura questa impostazione, l'avvio USB è abilitato.                                                                                                                 |
| Stack di rete                      | Consente di gestire le impostazioni di avvio dello stack di rete. Se non si configura questa impostazione, la possibilità di gestire le impostazioni di avvio dello stack di rete è disabilitata.                                                                                                           |
| Accensione automatica                      | Consente di gestire le impostazioni di avvio automatico di Accensione automatica. Se non si configura questa impostazione, l'accensione automatica è abilitata.                                                                                                        |
| Multithreading simultaneo (SMT) | Consente di gestire SMT (Simultaneous Multi-Threading) per abilitare o disabilitare l'hyperthreading. Se non si configura questa impostazione, SMT è abilitato.                                                  |
|Abilita limite batteria| Consente di gestire la funzionalità limite di batteria. Se non si configura questa impostazione, il limite di batteria è abilitato |
| Sicurezza                           | Visualizza la pagina Sicurezza UEFI **di** Surface. Se non si configura questa impostazione, verrà visualizzata la pagina Sicurezza.                                                                                                                 |
| Dispositivi                            | Visualizza la pagina Dispositivi UEFI **surface** . Se non si configura questa impostazione, verrà visualizzata la pagina Dispositivi.                                                                                                                     |
| Avvio                               | Visualizza la pagina di avvio UEFI **di** Surface. Se non si configura questa impostazione, verrà visualizzata la pagina Avvio.                                                                                                                                                            |
| DateTime                           | Visualizza la pagina Surface UEFI **DateTime** . Se non si configura questa impostazione, verrà visualizzata la pagina DateTime.                                                                                                                |
| EnableOSMigration                          | Consente di eseguire la migrazione Surface Hub 2 da Windows 10 Team a Windows 10/11 Pro o Enterprise. Se non si configura questa impostazione, Surface Hub 2 dispositivi possono eseguire solo il Windows 10 Team sistema operativo. Nota: l'avvio doppio tra Windows 10 Team e Windows 10/11 Pro/Enterprise non è disponibile in Surface Hub 2.                                                                                                           |

>[!TIP]
>Quando si crea un pacchetto di configurazione SEMM, nella pagina **Operazione** completata vengono visualizzati due caratteri, come illustrato nella figura 3.

![Visualizzazione dell'identificazione personale del certificato.](images/surface-ent-mgmt-fig5-success.png "Certificate thumbprint display")

*Figura 3. Visualizzazione degli ultimi due caratteri dell'identificazione personale del certificato nella pagina Esito positivo*

Questi caratteri sono gli ultimi due caratteri dell'identificazione personale del certificato e devono essere scritti o registrati. I caratteri sono necessari per confermare la registrazione in SEMM in un dispositivo Surface, come illustrato nella figura 4.

![Conferma di registrazione in SEMM.](images/surface-ent-mgmt-fig6-enrollconfirm.png "Enrollment confirmation in SEMM")

*Figura 4. Conferma di registrazione in SEMM con l'identificazione personale del certificato SEMM*

>[!TIP]
>Gli amministratori con accesso al file di certificato (con estensione pfx) possono leggere l'identificazione personale in qualsiasi momento aprendo il file pfx in CertMgr. Per visualizzare l'identificazione personale con CertMgr:
>
>1. Selezionare e tenere premuto (o fare clic con il pulsante destro del mouse) sul file pfx, quindi selezionare **Apri**.
>2. Nel riquadro di spostamento espandere la cartella.
>3. Selezionare **Certificati**.
>4. Nel riquadro principale, selezionare e tenere premuto (o fare clic con il pulsante destro del mouse) sul certificato, quindi selezionare **Apri**.
>5. Selezionare la **scheda** Dettagli.
>6. Nel menu **a discesa Mostra** è necessario selezionare **Solo** tutte **** le proprietà o Solo proprietà.
>7. Selezionare il **campo Identificazione** personale.

Per registrare un dispositivo Surface in SEMM o applicare la configurazione UEFI da un pacchetto di configurazione, esegui il file .msi con privilegi amministrativi nel dispositivo Surface previsto. È possibile utilizzare le tecnologie di distribuzione delle applicazioni o del sistema operativo, [ad esempio Microsoft Endpoint Configuration Manager](/mem/configmgr) o microsoft [Deployment Toolkit](/mem/configmgr/mdt). Quando si registra un dispositivo in SEMM, è necessario essere fisicamente presenti per confermare la registrazione nel dispositivo. Quando applichino una configurazione ai dispositivi già registrati in SEMM, l'interazione dell'utente non è necessaria.

Per una procedura dettagliata su come registrare un dispositivo Surface in SEMM o applicare una configurazione UEFI di Surface con SEMM, vedi [Registrare e configurare i dispositivi Surface con SEMM](enroll-and-configure-surface-devices-with-semm.md).

### <a name="reset-package"></a>Reimposta pacchetto

Un pacchetto di reimpostazione UEFI di Surface viene usato per eseguire una sola attività, ovvero per annullare la registrazione di un dispositivo Surface da SEMM. Il pacchetto di reimpostazione contiene istruzioni firmate per rimuovere il certificato SEMM dal firmware del dispositivo e per reimpostare le impostazioni UEFI sulle impostazioni predefinite di fabbrica. Come un pacchetto di configurazione UEFI di Surface, un pacchetto di reimpostazione deve essere firmato con lo stesso certificato SEMM di cui è stato eseguito il provisioning nel dispositivo Surface. Quando crei un pacchetto di reimpostazione SEMM, devi specificare il numero di serie del dispositivo Surface che intendi reimpostare. I pacchetti di reimpostazione SEMM non sono universali, ma sono specifici di un dispositivo.

### <a name="recovery-request"></a>Richiesta di ripristino

In alcuni scenari, potrebbe essere impossibile usare un pacchetto di reimpostazione UEFI di Surface. Ad esempio, se Windows diventa inutilizzabile nel dispositivo Surface. In questi scenari puoi annullare la registrazione del dispositivo Surface da SEMM tramite la pagina gestione **Enterprise** di Surface UEFI (illustrata nella figura 5) con un'operazione di richiesta di ripristino.

> [!div class="mx-imgBorder"]
> ![Avviare una richiesta di ripristino SEMM.](images/surface-ent-mgmt-fig7-semmrecovery.png "Initiate a SEMM recovery request")

*Figura 5. Avviare una richiesta di ripristino SEMM nella Enterprise gestione dei dati*

Quando usi il processo nella pagina **gestione** Enterprise per reimpostare SEMM in un dispositivo Surface, ti viene inviata una richiesta di reimpostazione. Questa richiesta di reimpostazione può essere salvata come file in un'unità USB, copiata come testo o letta come codice QR con un dispositivo mobile per essere facilmente inviata tramite posta elettronica o tramite messaggio. Usa l'opzione Richiesta di reimpostazione configuratore UEFI di Microsoft Surface per caricare un file di richiesta di reimpostazione o per immettere il testo Della richiesta di reimpostazione o il codice QR. Configuratore UEFI di Microsoft Surface genera un codice di verifica che può essere immesso nel dispositivo Surface. Se immetti il codice nel dispositivo Surface e seleziona **Riavvia**, la registrazione del dispositivo viene annullata da SEMM.

>[!NOTE]
>Una richiesta di reimpostazione scade due ore dopo la sua creazione.

Per una procedura dettagliata su come annullare la registrazione dei dispositivi Surface da SEMM, vedi Annullare la registrazione dei dispositivi [Surface da SEMM](unenroll-surface-devices-from-semm.md).

## <a name="surface-enterprise-management-mode-certificate-requirements"></a>Requisiti dei certificati per la modalità di gestione di Surface Enterprise

Quando usi SEMM con Microsoft Surface UEFI Configurator e vuoi applicare le impostazioni UEFI, è necessario un certificato per verificare la firma dei file di configurazione. Questo certificato garantisce che dopo la registrazione di un dispositivo in SEMM, solo i pacchetti creati con il certificato approvato possano essere usati per modificare le impostazioni UEFI.

>[!NOTE]
>Per apportare qualsiasi modifica alle impostazioni SEMM o UeFI di Surface nei dispositivi Surface registrati, è necessario il certificato SEMM. Se il certificato SEMM è danneggiato o perso, SEMM non può essere rimosso o reimpostato. Gestire il certificato SEMM di conseguenza con una soluzione appropriata per il backup e il ripristino

I pacchetti creati con lo strumento configuratore UEFI di Microsoft Surface vengono firmati con un certificato. Questo certificato garantisce che dopo la registrazione di un dispositivo in SEMM, solo i pacchetti creati con il certificato approvato possano essere usati per modificare le impostazioni di UEFI.

### <a name="recommended-certificate-settings"></a>Impostazioni consigliate per i certificati

Per il certificato SEMM sono consigliate le impostazioni seguenti:

- **Algoritmo chiave** - RSA
- **Lunghezza chiave** - 2048
- **Algoritmo hash** - SHA-256
- **Tipo** - Autenticazione server SSL
- **Utilizzo chiave** - Firma digitale, Crittografia chiave
- **Provider** - Microsoft Enhanced RSA and AES Cryptographic Provider
- **Data di scadenza** - 15 mesi dalla creazione del certificato
- **Criteri di esportazione chiave** - Esportabile

È inoltre consigliabile autenticare il certificato SEMM in un'architettura PKI (Public Key Infrastructure) a due livelli in cui l'autorità di certificazione intermedia è dedicata a SEMM, consentendo la revoca dei certificati. Per ulteriori informazioni su una configurazione PKI a due livelli, vedere [Test Lab Guide: Deploying an AD CS Two-Tier PKI Hierarchy](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831348(v=ws.11)).

### <a name="self-signed-certificate"></a>Certificato autofirmato

È possibile utilizzare lo script di PowerShell di esempio seguente per creare un certificato autofirmato da utilizzare in scenari di prova.
Per usare questo script, copiare il testo seguente Blocco note e quindi salvare il file come script di PowerShell (.ps1).

> [!NOTE]
> Questo script crea un certificato con una password di `12345678`. Il certificato generato da questo script non è consigliato per gli ambienti di produzione.
  
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
>Per l'uso con SEMM e Microsoft Surface UEFI Configurator, il certificato deve essere esportato con la chiave privata e con la protezione con password. Configuratore UEFI di Microsoft Surface richiede di selezionare il file di certificato SEMM (con estensione pfx) e la password del certificato.

Per creare un certificato autofirmato:

1. Nell'unità C: crea la cartella in cui salvare lo script. ad esempio, C:\SEMM.
2. Copiare lo script di esempio Blocco note (o editor di testo equivalente) e quindi salvare il file come script di PowerShell (.ps1).
3. Accedere al computer con le credenziali di amministratore e quindi aprire una sessione di PowerShell con privilegi elevati.
4. Verificare che le autorizzazioni siano impostate per consentire l'esecuzione degli script. Per impostazione predefinita, l'esecuzione degli script viene bloccata a meno che non si modificano i criteri di esecuzione. Per ulteriori informazioni, vedere [Informazioni sui criteri di esecuzione](/powershell/module/microsoft.powershell.core/about/about_execution_policies).
5. Al prompt dei comandi immettere il percorso completo dello script e quindi premere **INVIO**. Lo script crea un certificato demo denominato TempOwner.pfx.

In alternativa, è possibile creare un certificato autofirmato tramite PowerShell. Per altre informazioni, vedi [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate).

>[!NOTE]
>Per le organizzazioni che usano una radice offline nell'infrastruttura PKI, il configuratore UEFI di Microsoft Surface deve essere eseguito in un ambiente connesso all'autorità di certificazione radice per autenticare il certificato SEMM. I pacchetti generati dal configuratore UEFI di Microsoft Surface possono essere trasferiti come file, in modo che possano essere trasferiti all'esterno dell'ambiente di rete offline con spazio di archiviazione rimovibile, ad esempio una chiavetta USB.

### <a name="managing-certificates-faq"></a>Domande frequenti sulla gestione dei certificati

La lunghezza *minima consigliata* è 15 mesi. È possibile utilizzare un certificato che scade tra meno di 15 mesi o un certificato che scade tra più di 15 mesi.

>[!NOTE]
>Quando un certificato scade, non viene rinnovato automaticamente.

**Un certificato scaduto influirà sulla funzionalità dei dispositivi registrati con SEMM?**<br><br>
No, un certificato influisce solo sulle attività di gestione dell'amministratore IT in SEMM e non ha alcun effetto sulle funzionalità del dispositivo alla scadenza.

**Il pacchetto e il certificato SEMM dovranno essere aggiornati in tutti i computer che lo dispongono?**<br><br>
Se si desidera che la reimpostazione o il ripristino SEMM funzioni, il certificato deve essere valido e non scaduto.

**È possibile creare pacchetti di reimpostazione in blocco per ogni superficie ordinata? È possibile creare un'applicazione che reimposta tutti i computer dell'ambiente?**<br><br>
Gli esempi di PowerShell che creano un pacchetto di configurazione per un tipo di dispositivo specifico possono essere usati anche per creare un pacchetto di reimpostazione indipendente dal numero di serie. Se il certificato è ancora valido, puoi creare un pacchetto di reimpostazione usando PowerShell per reimpostare SEMM.

## <a name="version-history"></a>Cronologia versioni

### <a name="version-2941390"></a>Versione 2.94.139.0

Questa versione di SEMM include:

- Supporto per Surface Laptop Studio, Surface Pro 8 e Surface Go 3

### <a name="version-2831390"></a>Versione 2.83.139.0

Questa versione di SEMM include:

- Supporto per Surface Laptop 4
- Opzione di supporto per multithreading simultaneo per Surface Pro 7
- Rimozione delle impostazioni SEMM obsolete  
- Firma MSI migliorata

### <a name="version-2791390"></a>Versione 2.79.139.0

Questa versione di SEMM include:

- Supporto per Surface Pro 7+.
- Miglioramenti dell'esperienza utente.

### <a name="version-2781390"></a>Versione 2.78.139.0

Questa versione di SEMM include:

- Supporto per Surface Laptop Go e Surface Pro X.
- Notifiche per le versioni nuove.
- Possibilità di creare pacchetti personalizzati per modificare la proprietà.
- Correzioni di bug.

### <a name="version-2731360"></a>Versione 2.73.136.0

Questa versione di SEMM include:

- Possibilità di disabilitare l'audio in Surface Hub2S usando SEMM.
- Supporto per Surface Pro X per Dock 2.
- Supporto per UEFI Manager per le operazioni correlate al Dock 2.
- Correzione di un bug del pacchetto di reimpostazione di Surface Go.
- Supporto per la migrazione Surface Hub 2 dispositivi da Windows 10 Team sistema operativo a Windows 10 Pro o Enterprise.

### <a name="version-2711390"></a>Versione 2.71.139.0

Questa versione di SEMM aggiunge il supporto per le funzionalità di gestione di Surface Dock 2 per Surface Book 3, Surface Laptop 3 e Surface Pro 7. Include:

- Possibilità di abilitare l'audio (blocco/sblocco) e le porte Ethernet e USB.
- Possibilità di creare pacchetti dock sia per gli host autenticati che per gli host non autenticati.

### <a name="version-2701300"></a>Versione 2.70.130.0

Questa versione di SEMM include:

- Supporto per Surface Go 2.
- Supporto per Surface Book 3.
- Correzioni di bug.

### <a name="version-2591390"></a>Versione 2.59.139.0

Questa versione di SEMM include:

- Supporto per Surface Pro modelli da 7, Surface Pro X e Surface Laptop 3 modelli da 13,5" e 15" con processore Intel.
    >[!NOTE]
    >Surface Laptop processore AMD da 3 15" non è supportato.
- Supporto per la funzionalità Wake on Power.

### <a name="version-2541390"></a>Versione 2.54.139.0

Questa versione di SEMM include:

- Supporto per Surface Hub 2S.
- Correzioni di bug.

### <a name="version-2431360"></a>Versione 2.43.136.0

Questa versione di SEMM include:

- Supporto per abilitare/disabilitare il multithreading simultaneo.
- Opzioni separate per la rete wireless e Bluetooth per alcuni dispositivi.
- Limite batteria rimosso per Surface Studio.

### <a name="version-2261360"></a>Versione 2.26.136.0

Questa versione di SEMM include:

- Supporto per Surface Studio 2.
- Funzionalità Limite batteria.

### <a name="version-2211360"></a>Versione 2.21.136.0

Questa versione di SEMM include:

- Supporto per Surface Pro 6.
- Supporto per Surface Laptop 2.

### <a name="version-2141360"></a>Versione 2.14.136.0

Questa versione di SEMM include:

- Supporto per Surface Go.

### <a name="version-291360"></a>Versione 2.9.136.0

Questa versione di SEMM include:

- Supporto per Surface Book 2.
- Supporto per Surface Pro LTE.
- Miglioramenti all'accessibilità.

### <a name="version-10740"></a>Versione 1.0.74.0

Questa versione di SEMM include:

- Supporto per Surface Laptop.
- Supporto per Surface Pro.
- Correzioni di bug e miglioramenti generali.

## <a name="related-topics"></a>Argomenti correlati

- [Registrare e configurare i dispositivi Surface con SEMM](enroll-and-configure-surface-devices-with-semm.md)
- [Annullare la registrazione dei dispositivi Surface da SEMM](unenroll-surface-devices-from-semm.md)
- [Proteggere le porte del Surface Dock 2 con SEMM](secure-surface-dock-ports-semm.md)

---
title: Usare Microsoft endpoint Configuration Manager per gestire i dispositivi con SEMM (Surface)
description: Informazioni su come gestire Microsoft Surface Enterprise Management Mode (SEMM) con endpoint Configuration Manager.
keywords: registrazione, aggiornamento, script, impostazioni
ms.prod: w10
ms.mktglfcycl: manage
ms.pagetype: surface, devices
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.localizationpriority: medium
ms.audience: itpro
ms.date: 10/28/2020
ms.openlocfilehash: 2d31f520d8c4da54f47b2b89b58b43e2cb983f1a
ms.sourcegitcommit: 7f5b97275fe301ef700f9c77954a1054e2e8d046
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "11145617"
---
# Usare Microsoft Endpoint Configuration Manager per configurare dispositivi con SEMM

La funzionalità SEMM (Microsoft Surface Enterprise Management Mode) dei dispositivi UEFI di Surface consente agli amministratori di gestire e proteggere la configurazione delle impostazioni di Surface UEFI. Per la maggior parte delle organizzazioni, questo processo viene eseguito creando pacchetti di Windows Installer (con estensione msi) con lo strumento Microsoft Surface UEFI Configurator. Questi pacchetti vengono quindi eseguiti o distribuiti nei dispositivi Surface client per la registrazione dei dispositivi in SEMM e per aggiornare la configurazione delle impostazioni di Surface UEFI.

Per le organizzazioni con Microsoft endpoint Configuration Manager è disponibile un'alternativa all'uso del processo Microsoft Surface UEFI Configurator. msi per la distribuzione e l'amministrazione di SEMM. Microsoft Surface UEFI Manager è un programma di installazione leggero che rende disponibili gli assembly necessari per la gestione di SEMM in un dispositivo. Installando questi assembly con Microsoft Surface UEFI Manager in un client gestito, SEMM può essere gestito da Configuration Manager con gli script di PowerShell, distribuiti come applicazioni. Con questo processo, la gestione di SEMM viene eseguita in Configuration Manager, che elimina l'esigenza dello strumento Microsoft Surface UEFI Configurator esterno.

> [!Note]
> Anche se il processo descritto in questo articolo può funzionare con le versioni precedenti di endpoint Configuration Manager o con altre soluzioni di gestione di terze parti, la gestione di SEMM con Microsoft Surface UEFI Manager e PowerShell è supportata solo con il ramo corrente di endpoint Configuration Manager.

#### Prerequisiti

Prima di iniziare il processo descritto in questo articolo, acquisire familiarità con le tecnologie e gli strumenti seguenti:

* [UEFI di Surface](https://technet.microsoft.com/itpro/surface/manage-surface-uefi-settings)
* [SEMM (Surface Enterprise Management Mode)](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode)
* [Script di PowerShell](https://technet.microsoft.com/scriptcenter/dd742419)
* [Distribuzione delle applicazioni di System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/deploy-applications)
* Gestione dei certificati

> [!Note]
> Sarà inoltre necessario l'accesso al certificato che si vuole usare per proteggere SEMM. Per informazioni dettagliate sui requisiti per il certificato, vedere [requisiti per i certificati della modalità di gestione di Surface Enterprise](https://technet.microsoft.com/itpro/surface/surface-enterprise-management-mode#surface-enterprise-management-mode-certificate-requirements).
> 
> È molto importante che il certificato venga mantenuto in una posizione sicura e correttamente eseguito il backup. Se il certificato viene perso o inutilizzabile, non è possibile reimpostare la superficie UEFI, modificare le impostazioni di Surface UEFI gestite o rimuovere SEMM da un dispositivo Surface registrato.

#### Scarica Microsoft Surface UEFI Manager

La gestione di SEMM con Configuration Manager richiede l'installazione di Microsoft Surface UEFI Manager in ogni dispositivo Surface client. È possibile scaricare Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) dalla pagina [strumenti superficie per it](https://www.microsoft.com/download/details.aspx?id=46703) nell'area download Microsoft.

#### Scaricare gli script di SEMM per Configuration Manager

Dopo aver installato Microsoft Surface UEFI Manager nel dispositivo Surface client, SEMM viene distribuito e gestito con gli script di PowerShell. È possibile scaricare esempi degli [script di gestione di SEMM](https://www.microsoft.com/download/details.aspx?id=46703) dall'area download.

## Distribuire Microsoft Surface UEFI Manager

La distribuzione di Microsoft Surface UEFI Manager è una distribuzione tipica dell'applicazione. Il file del programma di installazione di Microsoft Surface UEFI Manager è un file di Windows Installer standard che è possibile installare con l' [opzione standard quiet](https://msdn.microsoft.com/library/windows/desktop/aa367988).

Il comando per installare Microsoft Surface UEFI Manager è il seguente.

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

Il comando per disinstallare Microsoft Surface UEFI Manager è il seguente.

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

Per creare una nuova applicazione e distribuirla a una raccolta che contiene i dispositivi Surface, eseguire la procedura seguente:

1. Aprire Configuration Manager Console dalla schermata **Start** o dal menu **Start** .
2. Selezionare **raccolta software** nell'angolo in basso a sinistra della finestra.
3. Espandere il nodo **Gestione applicazioni** della raccolta software e quindi selezionare **applicazioni**.
4. Selezionare il pulsante **Crea applicazione** nella scheda **Home** nella parte superiore della finestra. Verrà avviata la creazione guidata applicazione.
5. La procedura guidata Crea applicazione presenta una serie di passaggi:

   * **Generale** : l'opzione **rileva automaticamente le informazioni sull'applicazione da file di installazione** è selezionata per impostazione predefinita. Nel campo **tipo** è selezionato anche **Windows Installer (file con estensione msi)** per impostazione predefinita. Selezionare **Sfoglia** per passare a e selezionare **SurfaceUEFIManagerSetup.msi**e quindi selezionare **Avanti**.
   
      > [!Note]
      > La posizione di SurfaceUEFIManagerSetup.msi deve essere in una condivisione di rete e si trova in una cartella che non contiene altri file. Non è possibile usare un percorso di file locale.

   * **Importare informazioni** : la creazione guidata applicazione analizzerà il file con estensione msi e leggerà il **nome dell'applicazione** e il **codice del prodotto**. SurfaceUEFIManagerSetup.msi deve essere elencato come unico file sotto i file di **contenuto**della riga, come illustrato nella figura 1. Selezionare **Avanti** per procedere.

      ![Le informazioni dalla configurazione di Surface UEFI Manager vengono analizzate automaticamente](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *Figura 1. Le informazioni della configurazione di Microsoft Surface UEFI Manager vengono analizzate automaticamente*

   * **Informazioni generali** : è possibile modificare il nome dell'applicazione e le informazioni sull'editore e la versione oppure aggiungere commenti in questa pagina. Il comando di installazione per Microsoft Surface UEFI Manager viene visualizzato nel campo del programma di installazione. Il comportamento predefinito per l'installazione di install for System consentirà a Microsoft Surface UEFI Manager di installare gli assembly necessari per SEMM anche se un utente non ha effettuato l'accesso al dispositivo Surface. Selezionare **Avanti** per procedere.
   * **Riepilogo** : le informazioni analizzate nel passaggio informazioni sull' **importazione** e le selezioni del passaggio **informazioni generali** vengono visualizzate in questa pagina. Selezionare **Avanti** per confermare le selezioni e creare l'applicazione.
   * **Progress** : Visualizza una barra di stato e uno stato quando l'applicazione viene importata e aggiunta alla raccolta software.
   * **Completamento** : la conferma della corretta creazione dell'applicazione viene visualizzata al termine del processo di creazione dell'applicazione. Selezionare **Chiudi** per completare la creazione guidata applicazione.

Dopo aver creato l'applicazione in Configuration Manager, è possibile distribuirla ai punti di distribuzione e distribuirla alle raccolte, inclusi i dispositivi Surface. Questa applicazione non installerà o consentirà SEMM nel dispositivo Surface. Fornisce solo gli assembly necessari per l'abilitazione di SEMM con lo script di PowerShell.

Se non si vogliono installare gli assembly di Microsoft Surface UEFI Manager nei dispositivi che non verranno gestiti con SEMM, è possibile configurare Microsoft Surface UEFI Manager come dipendenza dagli script di gestione configurazione di SEMM. Questo scenario è descritto nella sezione [deploy SEMM Configuration Manager scripts](#deploy-semm-configuration-manager-scripts) più avanti in questo articolo.

## Creare o modificare gli script di gestione configurazione di SEMM

Dopo aver installato gli assembly obbligatori nei dispositivi, il processo di registrazione dei dispositivi in SEMM e configurazione della superficie UEFI viene eseguito con gli script di PowerShell e distribuiti come applicazione script con Configuration Manager. Questi script possono essere modificati per adattarsi alle esigenze dell'organizzazione e dell'ambiente. Ad esempio, puoi creare più configurazioni per i dispositivi Surface gestiti in diversi reparti o ruoli. È possibile scaricare esempi di script per SEMM e Configuration Manager dal collegamento nella sezione [prerequisiti](#prerequisites) all'inizio di questo articolo.

Per eseguire una distribuzione di SEMM con Configuration Manager sono necessari due script principali:

* **ConfigureSEMM.ps1** : usare questo script per creare pacchetti di configurazione per i dispositivi Surface con le impostazioni di UEFI di Surface desiderate per applicare le impostazioni specificate a un dispositivo Surface, per registrare il dispositivo in SEMM e per impostare una chiave del registro di sistema usata per identificare la registrazione del dispositivo in SEMM.
* **ResetSEMM.ps1** : usa questo script per reimpostare SEMM su un dispositivo Surface, che annulla la registrazione da SEMM e rimuove il controllo sulle impostazioni di Surface UEFI.

Gli script di esempio includono esempi di come impostare le impostazioni di Surface UEFI e come controllare le autorizzazioni per tali impostazioni. Queste impostazioni possono essere modificate per proteggere la superficie UEFI e impostare le impostazioni di Surface UEFI in base alle esigenze dell'ambiente. Le sezioni seguenti di questo articolo illustrano lo script ConfigureSEMM.ps1 ed esplorano le modifiche che è necessario apportare allo script in base alle proprie esigenze.

> [!NOTE]
> Gli script di gestione configurazione di SEMM e il file di certificato SEMM esportato (PFX) devono essere posizionati nella stessa cartella senza altri file prima di aggiungerli a Configuration Manager.

### Specificare i nomi di certificato e pacchetto

La prima area dello script che è necessario modificare è la parte che specifica e carica il certificato SEMM e indica anche la versione SurfaceUEFIManager e i nomi per il pacchetto di configurazione di SEMM e il pacchetto di reimpostazione di SEMM. Il nome del certificato e la versione di SurfaceUEFIManager sono specificati nelle righe da 56 a 73 nello script ConfigureSEMM.ps1.

  ```powershell
  56    $WorkingDirPath = split-path -parent $MyInvocation.MyCommand.Definition
  57    $packageRoot = "$WorkingDirPath\Config"
  58    $certName = "FabrikamSEMMSample.pfx"
  59  $DllVersion = "2.26.136.0"
  60
  61  $certNameOnly = [System.IO.Path]::GetFileNameWithoutExtension($certName)
  62  $ProvisioningPackage = $certNameOnly + "ProvisioningPackage.pkg"
  63  $ResetPackage = $certNameOnly + "ResetPackage.pkg"
  64
  65    if (-not (Test-Path $packageRoot))  { New-Item -ItemType Directory -Force -Path $packageRoot }
  66    Copy-Item "$WorkingDirPath\$certName" $packageRoot
  67    
  68    $privateOwnerKey = Join-Path -Path $packageRoot -ChildPath $certName
  69    $ownerPackageName = Join-Path -Path $packageRoot -ChildPath $ProvisioningPackage
  70    $resetPackageName = Join-Path -Path $packageRoot -ChildPath $ResetPackage
  71    
  72    # If your PFX file requires a password then it can be set here, otherwise use a blank string.
  73    $password = "1234" 
  ```

Sostituire il valore **FabrikamSEMMSample. pfx** per la variabile **$CertName** con il nome del file di certificato SEMM nella riga 58. Lo script creerà una directory di lavoro (denominata config) nella cartella in cui si trovano gli script e quindi copierà il file del certificato nella directory di lavoro.

Verrà creato anche il pacchetto proprietario e il pacchetto Reimposta nella directory di configurazione e si terrà la configurazione per le impostazioni e le autorizzazioni di Surface UEFI generate dallo script.

Nella riga 73 sostituire il valore della variabile **$password** , da **1234** alla password del file di certificato. Se non è necessaria una password, eliminare il testo di **1234** .

> [!Note]
> Gli ultimi due caratteri dell'identificazione personale del certificato sono necessari per la registrazione di un dispositivo in SEMM. Questo script visualizzerà queste cifre per l'utente, che consente all'utente o al tecnico di registrare queste cifre prima che il sistema venga riavviato per la registrazione del dispositivo in SEMM. Lo script usa il codice seguente, disponibile nelle righe 150-155, per eseguire questa operazione.

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

Gli amministratori con accesso al file di certificato (con estensione pfx) possono leggere l'identificazione personale in qualsiasi momento aprendo il file pfx in CertMgr. Per visualizzare l'identificazione personale con CertMgr, seguire questa procedura:

1. Fare clic con il pulsante destro del mouse sul file PFX e quindi scegliere **Apri**.
2. Espandere la cartella nel riquadro di spostamento.
3. Selezionare **certificati**.
4. Fare clic con il pulsante destro del mouse sul certificato nel riquadro principale e quindi scegliere **Apri**.
5. Selezionare la scheda **Dettagli** .
6. È necessario selezionare solo **tutte le** **proprietà o solo** nel menu a discesa **Mostra** .
7. Selezionare l' **identificazione personale**del campo.

> [!NOTE]
> Il nome del certificato e la password di SEMM devono essere immessi anche in questa sezione dello script ResetSEMM.ps1 per abilitare Configuration Manager per rimuovere SEMM dal dispositivo con l'azione di disinstallazione.

### Configurare le autorizzazioni

La prima area dello script in cui verrà specificata la configurazione per la superficie UEFI è l'area di configurazione **delle autorizzazioni** . Questa area inizia alla riga 210 nello script di esempio con il commento **# Configura le autorizzazioni** e continua alla riga 247. Il frammento di codice seguente imposta prima di tutto le autorizzazioni per tutte le impostazioni di Surface UEFI in modo che possano essere modificate solo da SEMM, quindi aggiunge autorizzazioni esplicite per consentire all'utente locale di modificare la password di Surface UEFI, il TPM e le telecamere anteriori e posteriori.

```powershell
210 # Configure Permissions
211 foreach ($uefiV2 IN $surfaceDevices.Values) {
212 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
213 Write-Host "Configuring permissions"
214 Write-Host $Device.Model
215 Write-Host "======================="
216
217 # Here we define which "identities" will be allowed to modify which settings
218 #   PermissionSignerOwner = The primary SEMM enterprise owner identity
219 #   PermissionLocal = The user when booting to the UEFI pre-boot GUI
220 #   PermissionSignerUser, PermissionSignerUser1, PermissionSignerUser2 =
221 #     Additional user identities created so that the signer owner
222 #     can delegate permission control for some settings.
223 $ownerOnly = [Microsoft.Surface.IUefiSetting]::PermissionSignerOwner
224 $ownerAndLocalUser = ([Microsoft.Surface.IUefiSetting]::PermissionSignerOwner -bor [Microsoft.Surface.IUefiSetting]::PermissionLocal)
225 
226 # Make all permissions owner only by default
227 foreach ($setting IN $uefiV2.Settings.Values) {
228 $setting.ConfiguredPermissionFlags = $ownerOnly
229 }
230 
231 # Allow the local user to change their own password
232 $uefiV2.SettingsById[501].ConfiguredPermissionFlags = $ownerAndLocalUser
233
234 Write-Host ""
235  
236 # Create a unique package name based on family and LSV.
237 # We will choose a name that can be parsed by later scripts.
238 $packageName = $uefiV2.SurfaceUefiFamily + "^Permissions^" + $lsv + ".pkg"
239 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
240 
241 # Build and sign the Permission package then save it to a file.
242 $permissionPackageStream =  $uefiV2.BuildAndSignPermissionPackage($privateOwnerKey, $password, "", $null, $lsv)
243 $permissionPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
244 $permissionPackageStream.CopyTo($permissionPackage)
245 $permissionPackage.Close()
246 }
247 }
```

Ogni variabile **$uefiV 2** identifica un'impostazione UEFI di superficie impostando nome o ID e quindi configura le autorizzazioni su uno dei valori seguenti:

* **$ownerOnly** : l'autorizzazione per la modifica di questa impostazione viene concessa solo a SEMM.
* **$ownerAndLocalUser** : l'autorizzazione per la modifica di questa impostazione viene concessa a un utente locale che avvia l'installazione di Surface UEFI, nonché a SEMM.

Puoi trovare informazioni sui nomi delle impostazioni disponibili e sugli ID per la superficie UEFI nella sezione [nomi delle impostazioni e ID](#settings-names-and-ids) di questo articolo.

### Configurare le impostazioni

La seconda area dello script in cui verrà specificata la configurazione per la superficie UEFI è l'area **Configura impostazioni** dello script ConfigureSEMM.ps1, che configura se ogni impostazione è abilitata o disabilitata. Lo script di esempio include istruzioni per impostare tutte le impostazioni sui valori predefiniti. Lo script fornisce quindi istruzioni esplicite per disabilitare l'avvio di IPv6 per PXE e per non modificare la password di amministratore di Surface UEFI. Questa regione può iniziare con il commento **# Configure Settings** alla riga 291 tramite la riga 335 nello script di esempio. L'area geografica viene visualizzata come segue.

```powershell
291 # Configure Settings
292 foreach ($uefiV2 IN $surfaceDevices.Values) {
293 if ($uefiV2.SurfaceUefiFamily -eq $Device.Model) {
294 Write-Host "Configuring settings"
295 Write-Host $Device.Model
296 Write-Host "===================="
297
298 # In this demo, we will start by setting every setting to the default factory setting.
299 # You may want to start by doing this in your scripts
300 # so that every setting gets set to a known state.
301 foreach ($setting IN $uefiV2.Settings.Values) {
302 $setting.ConfiguredValue = $setting.DefaultValue
303 }
304 
305 $EnabledValue = "Enabled"
306 $DisabledValue = "Disabled"
307
308 # If you want to set something to a different value from the default,
309 # here are examples of how to accomplish this.
310 # This disables IPv6 PXE boot by name:
311 $uefiV2.Settings["IPv6 for PXE Boot"].ConfiguredValue = $DisabledValue
312
313 # This disables IPv6 PXE Boot by ID:
314 $uefiV2.SettingsById[400].ConfiguredValue = $DisabledValue
315
316 Write-Host ""
317
318 # If you want to leave the setting unmodified, set it to $null
319 # PowerShell has issues setting things to $null so ClearConfiguredValue()
320 # is supplied to do this explicitly.
321 # Here is an example of leaving the UEFI administrator password as-is,
322 # even after we initially set it to factory default above.
323 $uefiV2.SettingsById[501].ClearConfiguredValue()
324 
325 # Create a unique package name based on family and LSV.
326 # We will choose a name that can be parsed by later scripts.
327 $packageName = $uefiV2.SurfaceUefiFamily + "^Settings^" + $lsv + ".pkg"
328 $fullPackageName = Join-Path -Path $packageRoot -ChildPath $packageName
329 
330 # Build and sign the Settings package then save it to a file.
331 $settingsPackageStream =  $uefiV2.BuildAndSignSecuredSettingsPackage($privateOwnerKey, $password, "", $null, $lsv)
332 $settingsPackage = New-Object System.IO.Filestream($fullPackageName, [System.IO.FileMode]::CreateNew, [System.IO.FileAccess]::Write)
333 $settingsPackageStream.CopyTo($settingsPackage)
334 $settingsPackage.Close()
335 }
```

Come le autorizzazioni impostate nella sezione **Configura autorizzazioni** dello script, la configurazione di ogni impostazione UEFI di Surface viene eseguita definendo la variabile **$uefiV 2** . Per ogni riga che definisce la variabile **$uefiV 2** , viene identificata un'impostazione UEFI di Surface impostando Name o ID e il valore configurato è impostato su **Enabled** o **disabled**.

Se non si vuole modificare la configurazione di un'impostazione UEFI di Surface, ad esempio per verificare che la password di amministratore di Surface UEFI non sia cancellata dall'azione di reimpostare tutte le impostazioni di Surface UEFI sul valore predefinito, è possibile usare **ClearConfiguredValue ()** per far sì che questa impostazione non venga modificata. Nello script di esempio, questo viene usato in linea 323 per impedire la cancellazione della password di amministratore di Surface UEFI, identificata nello script di esempio dall'ID di impostazione, **501**.

Puoi trovare informazioni sui nomi delle impostazioni disponibili e sugli ID per l'UEFI di Surface nella sezione [nomi delle impostazioni e ID](#settings-names-and-ids) più avanti in questo articolo.

### Chiave del registro di sistema impostazioni

Per identificare i sistemi registrati per Configuration Manager, lo script ConfigureSEMM.ps1 scrive le chiavi del registro di sistema che possono essere usate per identificare i sistemi registrati come installati con lo script di configurazione di SEMM. Queste chiavi si trovano nella posizione seguente.

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

Il frammento di codice seguente, disponibile nelle righe 380-477, viene usato per scrivere queste chiavi del registro di sistema.

```powershell
380 # For Endpoint Configuration Manager or other management solutions that wish to know what version is applied, tattoo the LSV and current DateTime (in UTC) to the registry:
381 $UTCDate = (Get-Date).ToUniversalTime().ToString()
382 $certIssuer = $certPrint.Issuer
383 $certSubject = $certPrint.Subject
384 
385 $SurfaceRegKey = "HKLM:\SOFTWARE\Microsoft\Surface\SEMM"
386 New-RegKey $SurfaceRegKey
387 $LSVRegValue = Get-ItemProperty $SurfaceRegKey LSV -ErrorAction SilentlyContinue
388 $DateTimeRegValue = Get-ItemProperty $SurfaceRegKey LastConfiguredUTC -ErrorAction SilentlyContinue
389 $OwnershipSessionIdRegValue = Get-ItemProperty $SurfaceRegKey OwnershipSessionId -ErrorAction SilentlyContinue
390 $PermissionSessionIdRegValue = Get-ItemProperty $SurfaceRegKey PermissionSessionId -ErrorAction SilentlyContinue
391 $SettingsSessionIdRegValue = Get-ItemProperty $SurfaceRegKey SettingsSessionId -ErrorAction SilentlyContinue
392 $IsResetRegValue = Get-ItemProperty $SurfaceRegKey IsReset -ErrorAction SilentlyContinue
393 $certUsedRegValue = Get-ItemProperty $SurfaceRegKey CertName -ErrorAction SilentlyContinue
394 $certIssuerRegValue = Get-ItemProperty $SurfaceRegKey CertIssuer -ErrorAction SilentlyContinue
395 $certSubjectRegValue = Get-ItemProperty $SurfaceRegKey CertSubject -ErrorAction SilentlyContinue
396 
397 
398 If ($LSVRegValue -eq $null)
399 {
400     New-ItemProperty -Path $SurfaceRegKey -Name LSV -PropertyType DWORD -Value $lsv | Out-Null
401 }
402 Else
403 {
404     Set-ItemProperty -Path $SurfaceRegKey -Name LSV -Value $lsv
405 }
406 
407 If ($DateTimeRegValue -eq $null)
408 {
409     New-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -PropertyType String -Value $UTCDate | Out-Null
410 }
411 Else
412 {
413     Set-ItemProperty -Path $SurfaceRegKey -Name LastConfiguredUTC -Value $UTCDate
414 }
415 
416 If ($OwnershipSessionIdRegValue -eq $null)
417 {
418     New-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -PropertyType String -Value $ownerSessionIdValue | Out-Null
419 }
420 Else
421 {
422     Set-ItemProperty -Path $SurfaceRegKey -Name OwnershipSessionId -Value $ownerSessionIdValue
423 }
424 
425 If ($PermissionSessionIdRegValue -eq $null)
426 {
427     New-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -PropertyType String -Value $permissionSessionIdValue | Out-Null
428 }
429 Else
430 {
431     Set-ItemProperty -Path $SurfaceRegKey -Name PermissionSessionId -Value $permissionSessionIdValue
432 }
433 
434 If ($SettingsSessionIdRegValue -eq $null)
435 {
436     New-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -PropertyType String -Value $settingsSessionIdValue | Out-Null
437 }
438 Else
439 {
440     Set-ItemProperty -Path $SurfaceRegKey -Name SettingsSessionId -Value $settingsSessionIdValue
441 }
442 
443 If ($IsResetRegValue -eq $null)
444 {
445     New-ItemProperty -Path $SurfaceRegKey -Name IsReset -PropertyType DWORD -Value 0 | Out-Null
446 }
447 Else
448 {
449     Set-ItemProperty -Path $SurfaceRegKey -Name IsReset -Value 0
450 }
451 
452 If ($certUsedRegValue -eq $null)
453 {
454     New-ItemProperty -Path $SurfaceRegKey -Name CertName -PropertyType String -Value $certName | Out-Null
455 }
456 Else
457 {
458     Set-ItemProperty -Path $SurfaceRegKey -Name CertName -Value $certName
459 }
460 
461 If ($certIssuerRegValue -eq $null)
462 {
463     New-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -PropertyType String -Value $certIssuer | Out-Null
464 }
465 Else
466 {
467     Set-ItemProperty -Path $SurfaceRegKey -Name CertIssuer -Value $certIssuer
468 }
469 
470 If ($certSubjectRegValue -eq $null)
471 {
472     New-ItemProperty -Path $SurfaceRegKey -Name CertSubject -PropertyType String -Value $certSubject | Out-Null
473 }
474 Else
475 {
476     Set-ItemProperty -Path $SurfaceRegKey -Name CertSubject -Value $certSubject
477 }
```

### Nomi delle impostazioni e ID

Per configurare le impostazioni di Surface UEFI o le autorizzazioni per le impostazioni di Surface UEFI, è necessario fare riferimento a ogni impostazione tramite il nome dell'impostazione o l'ID impostazione. Con ogni nuovo aggiornamento per la superficie UEFI, potrebbero essere aggiunte nuove impostazioni. Il modo migliore per ottenere un elenco completo delle impostazioni disponibili in un dispositivo Surface, insieme al nome delle impostazioni e agli ID delle impostazioni, consiste nell'usare lo script ShowSettingsOptions.ps1 di SEMM_Powershell.zip in [strumenti di Surface per i download](https://www.microsoft.com/download/details.aspx?id=46703) 

Il computer in cui è in esecuzione ShowSettingsOptions.ps1 deve avere Microsoft Surface UEFI Manager installato, ma lo script non richiede un dispositivo Surface.


## Distribuire script di gestione configurazione di SEMM

Dopo aver preparato gli script per la configurazione e l'abilitazione di SEMM nel dispositivo client, il passaggio successivo consiste nell'aggiungere questi script come applicazione in Configuration Manager. Prima di aprire Configuration Manager, assicurarsi che i file seguenti si trovino in una cartella condivisa che non includa altri file:

* ConfigureSEMM.ps1
* ResetSEMM.ps1
* Il certificato di SEMM (ad esempio SEMMCertificate. pfx)

Gli script di gestione configurazione di SEMM verranno aggiunti a Configuration Manager come applicazione script. Il comando per installare SEMM con ConfigureSEMM.ps1 è il seguente.

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

Il comando per disinstallare SEMM con ResetSEMM.ps1 è il seguente.

`Powershell.exe -file ".\ResetSEMM.ps1"`

Per aggiungere gli script di gestione configurazione di SEMM a Configuration Manager come applicazione, usare il processo seguente:

1. Avviare la creazione guidata applicazione usando il passaggio 1 al passaggio 5 dalla sezione [Distribuisci Microsoft Surface UEFI Manager](#deploy-microsoft-surface-uefi-manager) in questo articolo.

2. Procedere con la procedura guidata Crea applicazione come indicato di seguito:

   - **Generale** : selezionare **specifica manualmente le informazioni sull'applicazione**e quindi selezionare **Avanti**.

   - **Informazioni generali** : immettere un nome per l'applicazione (ad esempio SEMM) e tutte le altre informazioni desiderate, come Publisher, versione o commenti in questa pagina. Selezionare **Avanti** per procedere.

   - **Catalogo applicazioni** : i campi in questa pagina possono essere lasciati con i relativi valori predefiniti. Seleziona **Avanti**.

   - **Tipi di distribuzione** : selezionare **Aggiungi** per avviare la procedura guidata Crea tipo di distribuzione.

   - Procedere con i passaggi della procedura guidata Crea tipo di distribuzione, come indicato di seguito:

     * **Generale** : selezionare **script Installer** dal menu a discesa **tipo** . L'opzione **specifica manualmente le informazioni sul tipo di distribuzione** verrà selezionata automaticamente. Selezionare **Avanti** per procedere.
     * **Informazioni generali** : immettere un nome per il tipo di distribuzione, ad esempio gli script di configurazione di SEMM, quindi scegliere **Avanti** per continuare.
     * **Contenuto** : selezionare **Sfoglia** accanto al campo **percorso contenuto** e quindi selezionare la cartella in cui si trovano gli script di gestione configurazione di SEMM. Nel campo **programma di installazione** Digitare il [comando di installazione](#deploy-semm-configuration-manager-scripts) trovato in precedenza in questo articolo. Nel campo **Disinstalla programma** immettere il comando di [disinstallazione](#deploy-semm-configuration-manager-scripts) disponibile in precedenza in questo articolo (illustrato nella figura 2). Selezionare **Avanti** per tornare alla pagina successiva.
    
     ![Impostare gli script di gestione configurazione di SEMM come comandi di installazione e disinstallazione](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *Figura 2. Impostare gli script di gestione configurazione di SEMM come comandi di installazione e disinstallazione*

     * **Metodo di rilevamento** : selezionare **Aggiungi clausola** per aggiungere la regola di rilevamento della chiave del registro di sistema di SEMM Configuration Manager script. Viene visualizzata la finestra della **regola di rilevamento** , come illustrato nella figura 3. Usa le impostazioni seguenti:

       - Selezionare **Registro di sistema** dal menu a discesa **tipo di impostazione** .
       - Selezionare **HKEY_LOCAL_MACHINE** dal menu a discesa **hive** .
       - Immettere **SOFTWARE\Microsoft\Surface\SEMM** nel campo **chiave** .
       - Immettere **CertName** nel campo **valore** .
       - Selezionare **stringa** dal menu a discesa **tipo di dati** .
       - Selezionare l' **impostazione di questo registro di sistema deve soddisfare la regola seguente per indicare la presenza del pulsante applicazione** .
       - Immettere il nome del certificato immesso nella riga 58 dello script nel campo **valore** .
       - Selezionare **OK** per chiudere la finestra della **regola di rilevamento** .

     ![Usare una chiave del registro di sistema per identificare i dispositivi registrati in SEMM](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *Figura 3. Usare una chiave del registro di sistema per identificare i dispositivi registrati in SEMM*

     * Selezionare **Avanti** per passare alla pagina successiva.
     
     * **Esperienza utente** : selezionare **Installa per sistema** dal menu a discesa **comportamento di installazione** . Se si vuole che gli utenti registrino e immettino l'identificazione personale del certificato, abbandonare il requisito di accesso **solo quando l'utente ha effettuato**l'accesso. Se si vuole che gli amministratori immettino l'identificazione personale per gli utenti e che gli utenti non debbano vedere l'identificazione personale, selezionare **se un utente ha effettuato** l'accesso dal menu a discesa **requisiti di accesso** .

     * **Requisiti** : lo script ConfigureSEMM.ps1 verifica automaticamente che il dispositivo sia un dispositivo Surface prima di provare a abilitare SEMM. Tuttavia, se intendi distribuire questa applicazione di script a una raccolta con dispositivi diversi da quelli da gestire con SEMM, puoi aggiungere requisiti per verificare che l'applicazione venga eseguita solo su dispositivi o dispositivi di Surface che intendi usare con SEMM. Selezionare **Avanti** per continuare.
     
     * **Dipendenze** : selezionare **Aggiungi** per aprire la finestra **Aggiungi dipendenza** .

       * Selezionare **Aggiungi** per aprire la finestra **specifica applicazione richiesta** .

          - Immettere un nome per le dipendenze SEMM nel campo **nome gruppo di dipendenze** (ad esempio, *assembly SEMM*).

          - Selezionare **Microsoft Surface UEFI Manager** dall'elenco delle **applicazioni disponibili** e dal tipo di distribuzione MSI, quindi scegliere **OK** per chiudere la finestra **specifica applicazione necessaria** .
          
         *   Selezionare la casella di controllo **installazione automatica** se si vuole che Microsoft Surface UEFI Manager sia installato automaticamente nei dispositivi quando si tenta di abilitare SEMM con gli script di Configuration Manager. Selezionare **OK** per chiudere la finestra **Aggiungi dipendenza** .

     * Selezionare **Avanti** per procedere.
     
     * **Riepilogo** : le informazioni immesse in tutta la procedura guidata Crea tipo di distribuzione vengono visualizzate in questa pagina. Selezionare **Avanti** per confermare le selezioni.
     
     * **Progress** : viene visualizzata una barra di stato e uno stato come tipo di distribuzione per l'applicazione di script SEMM in questa pagina.
     
     * **Completamento** : la conferma della creazione del tipo di distribuzione viene visualizzata al termine del processo. Selezionare **Chiudi** per completare la procedura guidata Crea tipo di distribuzione.

   - **Riepilogo** : vengono visualizzate le informazioni immesse in tutta la creazione guidata applicazione. Selezionare **Avanti** per creare l'applicazione.

   - **Progress** : viene visualizzata una barra di stato e uno stato quando l'applicazione viene aggiunta alla raccolta software in questa pagina.

   - **Completamento** : la conferma della corretta creazione dell'applicazione viene visualizzata al termine del processo di creazione dell'applicazione. Selezionare **Chiudi** per completare la creazione guidata applicazione.

Dopo che l'applicazione script è disponibile nella raccolta software di Configuration Manager, è possibile distribuire e distribuire SEMM usando gli script preparati per i dispositivi o le raccolte. Se gli assembly di Microsoft Surface UEFI Manager sono stati configurati come una dipendenza che verrà installata automaticamente, è possibile distribuire SEMM in un singolo passaggio. Se gli assembly non sono stati configurati come dipendenza, è necessario che siano installati nei dispositivi che si vuole gestire prima di abilitare SEMM.

Quando si distribuisce SEMM con questa applicazione script e con una configurazione visibile per l'utente finale, verrà avviato lo script di PowerShell e l'identificazione personale del certificato verrà visualizzata dalla finestra di PowerShell. Gli utenti possono registrare questa identificazione personale e immetterla quando viene richiesto dall'UEFI di Surface dopo il riavvio del dispositivo.

In alternativa, puoi configurare l'installazione dell'applicazione per il riavvio automatico e per l'installazione invisibile all'utente. In questo scenario, a un tecnico verrà richiesto di immettere l'identificazione personale in ogni dispositivo durante il riavvio. Qualsiasi tecnico con accesso al file di certificato può leggere l'identificazione personale visualizzando il certificato con CertMgr. Le istruzioni per la visualizzazione dell'identificazione personale con CertMgr si trovano nella sezione [creare o modificare gli script di gestione configurazione di SEMM](#create-or-modify-the-semm-configuration-manager-scripts) di questo articolo.

La rimozione di SEMM da un dispositivo distribuito con Configuration Manager tramite questi script è facile come disinstallare l'applicazione con Configuration Manager. Questa azione avvia lo script ResetSEMM.ps1 e disiscrive correttamente il dispositivo con lo stesso file di certificato usato durante la distribuzione di SEMM.

> [!NOTE]
> Microsoft Surface consiglia di creare pacchetti di reimpostazione solo quando è necessario annullare la registrazione di un dispositivo. Questi pacchetti di reimpostazione sono in genere validi per un solo dispositivo, identificato dal numero seriale. Puoi tuttavia creare un pacchetto di reimpostazione universale che funzioni per qualsiasi dispositivo registrato in SEMM con questo certificato.
> 
> Ti consigliamo vivamente di proteggere il pacchetto di reimpostazione universale con la massima cautela del certificato usato per la registrazione dei dispositivi in SEMM. Tieni presente che, proprio come il certificato stesso, questo pacchetto di reimpostazione universale può essere usato per annullare la registrazione dei dispositivi Surface della tua organizzazione da SEMM.
> 
> Quando si installa un pacchetto di reimpostazione, il valore supportato più basso (LSV) viene reimpostato su un valore pari a 1. Puoi rieseguire la registrazione di un dispositivo usando un pacchetto di configurazione esistente. Il dispositivo chiederà l'identificazione personale del certificato prima che venga eseguita la proprietà.
> 
> Per questo motivo, la riregistrazione di un dispositivo in SEMM richiederà la creazione e l'installazione di un nuovo pacchetto nel dispositivo. Poiché questa azione è una nuova registrazione e non una modifica della configurazione in un dispositivo già registrato in SEMM, il dispositivo chiederà l'identificazione personale del certificato prima che venga eseguita la proprietà.

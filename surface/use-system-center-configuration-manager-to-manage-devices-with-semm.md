---
title: Usare Microsoft Endpoint Configuration Manager per configurare dispositivi con SEMM
description: Scopri come gestire microsoft Surface Enterprise Management Mode (SEMM) con Endpoint Configuration Manager.
keywords: registrare, aggiornare, script, impostazioni
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
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 470fec76afded98127464d956d907e90758de9d6
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449249"
---
# <a name="use-microsoft-endpoint-configuration-manager-to-manage-devices-with-semm"></a>Usare Microsoft Endpoint Configuration Manager per configurare dispositivi con SEMM

La funzionalità SeMM (Microsoft Surface Enterprise Management Mode) dei dispositivi UEFI surface consente agli amministratori di gestire e proteggere la configurazione delle impostazioni UEFI di Surface. Per la maggior parte delle organizzazioni, questo processo viene realizzato creando pacchetti Windows Installer (.msi) con lo strumento Configuratore UEFI di Microsoft Surface. Questi pacchetti vengono quindi eseguiti o distribuiti nei dispositivi Surface client per registrare i dispositivi in SEMM e aggiornare la configurazione delle impostazioni UEFI di Surface.

Per le organizzazioni con Microsoft Endpoint Configuration Manager è disponibile un'alternativa all'uso del processo di configurazione UEFI di Microsoft Surface .msi per distribuire e amministrare SEMM. Microsoft Surface UEFI Manager è un programma di installazione leggero che rende disponibili gli assembly necessari per la gestione SEMM in un dispositivo. Installando questi assembly con Microsoft Surface UEFI Manager in un client gestito, SEMM può essere amministrato da Configuration Manager con script di PowerShell, distribuiti come applicazioni. Con questo processo, la gestione SEMM viene eseguita all'interno di Configuration Manager, eliminando la necessità dello strumento ueFI Configurator UEFI di Microsoft Surface esterno.

> [!Note]
> Anche se il processo descritto in questo articolo può funzionare con le versioni precedenti di Endpoint Configuration Manager o con altre soluzioni di gestione di terze parti, la gestione di SEMM con Microsoft Surface UEFI Manager e PowerShell è supportata solo con Current Branch of Endpoint Configuration Manager.

#### <a name="prerequisites"></a>Prerequisiti

Prima di iniziare il processo descritto in questo articolo, acquisire familiarità con le tecnologie e gli strumenti seguenti:

* [Surface UEFI](manage-surface-uefi-settings.md)
* [SEMM (Surface Enterprise Management Mode)](surface-enterprise-management-mode.md)
* [Script di PowerShell](/powershell)
* [Distribuire applicazioni con Configuration Manager](/mem/configmgr/apps/deploy-use/deploy-applications)


> [!Note]
> Sarà inoltre necessario accedere al certificato che si intende utilizzare per proteggere SEMM. Per informazioni dettagliate sui requisiti per questo certificato, [vedi Requisiti del certificato per la modalità di gestione di Surface Enterprise](surface-enterprise-management-mode.md#surface-enterprise-management-mode-certificate-requirements).
> 
> È molto importante che questo certificato venga conservato in un luogo sicuro ed eseguito correttamente il backup. Se questo certificato viene perso o inutilizzabile, non è possibile reimpostare Surface UEFI, modificare le impostazioni UEFI di Surface gestite o rimuovere SEMM da un dispositivo Surface registrato.

#### <a name="download-microsoft-surface-uefi-manager"></a>Scaricare Microsoft Surface UEFI Manager

La gestione di SEMM con Configuration Manager richiede l'installazione di Microsoft Surface UEFI Manager in ogni dispositivo Surface client. Puoi scaricare Microsoft Surface UEFI Manager (SurfaceUEFIManager.msi) dalla pagina [Surface Tools for IT](https://www.microsoft.com/download/details.aspx?id=46703) nell'Area download Microsoft.

#### <a name="download-semm-scripts-for-configuration-manager"></a>Scaricare gli script SEMM per Configuration Manager

Dopo l'installazione di Microsoft Surface UEFI Manager nel dispositivo Surface client, SEMM può essere distribuito e gestito con gli script di PowerShell. Ottieni esempi di [script di gestione SEMM](https://www.microsoft.com/download/details.aspx?id=46703) scaricando SEMM_PowerShell.zip da Surface Tools per IT.

## <a name="deploy-microsoft-surface-uefi-manager"></a>Distribuire Microsoft Surface UEFI Manager

La distribuzione di Microsoft Surface UEFI Manager è una distribuzione tipica delle applicazioni. Il file del programma di installazione di Microsoft Surface UEFI Manager è un file Windows installer standard che puoi installare con [l'opzione non interattiva standard](https://msdn.microsoft.com/library/windows/desktop/aa367988).

Il comando per installare Microsoft Surface UEFI Manager è il seguente.

`msiexec /i "SurfaceUEFIManagerSetup.msi" /q`

Il comando per disinstallare Microsoft Surface UEFI Manager è il seguente.

`msiexec /x {541DA890-1AEB-446D-B3FD-D5B3BB18F9AF} /q`

Per creare una nuova applicazione e distribuirla in una raccolta contenente i dispositivi Surface, esegui la procedura seguente:

1. Apri la console di Configuration Manager dalla **schermata Start** o dal menu **Start** .
2. Seleziona **Raccolta software** nell'angolo in basso a sinistra della finestra.
3. Espandere il **nodo Gestione** applicazioni della raccolta software e quindi selezionare **Applicazioni**.
4. Seleziona il **pulsante Crea** applicazione nella **scheda Home** nella parte superiore della finestra. Verrà avviata la Creazione guidata applicazione.
5. La Creazione guidata applicazione presenta una serie di passaggi:

   * **Generale** : **l'opzione Rileva automaticamente informazioni su questa applicazione dai file di** installazione è selezionata per impostazione predefinita. Nel campo **Tipo** è selezionato **Windows Installer (.msi file)** per impostazione predefinita. Selezionare **Sfoglia** per passare a e selezionare **SurfaceUEFIManagerSetup.msi**e quindi selezionare **Avanti**.
   
      > [!Note]
      > Il percorso di SurfaceUEFIManagerSetup.msi deve trovarsi in una condivisione di rete e trovarsi in una cartella che non contiene altri file. Non è possibile utilizzare un percorso file locale.

   * **Importa informazioni** : la Creazione guidata applicazione analerà il file .msi e leggerà il nome **dell'applicazione e** il **codice prodotto**. SurfaceUEFIManagerSetup.msi deve essere elencato come l'unico file sotto la riga **File di contenuto**, come illustrato nella figura 1. Selezionare **Avanti** per procedere.

      ![Le informazioni della configurazione di Surface UEFI Manager vengono analizzate automaticamente.](images/config-mgr-semm-fig1.png "Information from Surface UEFI Manager setup is automatically parsed")

      *Figura 1. Le informazioni della configurazione di Microsoft Surface UEFI Manager vengono analizzate automaticamente*

   * **Informazioni generali** : è possibile modificare il nome dell'applicazione e le informazioni sull'autore e la versione oppure aggiungere commenti in questa pagina. Il comando di installazione per Microsoft Surface UEFI Manager viene visualizzato nel campo Programma di installazione. Il comportamento di installazione predefinito di Installa per il sistema consentirà a Microsoft Surface UEFI Manager di installare gli assembly necessari per SEMM anche se un utente non è connesso al dispositivo Surface. Selezionare **Avanti** per procedere.
   * **Riepilogo**: le informazioni analizzate nel passaggio Importa informazioni **** e le selezioni del passaggio Informazioni generali vengono visualizzate **** in questa pagina. Selezionare **Avanti** per confermare le selezioni e creare l'applicazione.
   * **Progress** : visualizza un indicatore di stato e uno stato quando l'applicazione viene importata e aggiunta alla Raccolta software.
   * **Completamento** : al termine del processo di creazione dell'applicazione viene visualizzata la conferma della corretta creazione dell'applicazione. Selezionare **Chiudi per** completare la Creazione guidata applicazione.

Dopo aver creato l'applicazione in Configuration Manager, puoi distribuirla ai punti di distribuzione e distribuirla alle raccolte, inclusi i dispositivi Surface. Questa applicazione non installerà o abiliterà SEMM nel dispositivo Surface. Fornisce solo gli assembly necessari per l'attivazione di SEMM tramite lo script di PowerShell.

Se non vuoi installare gli assembly di Microsoft Surface UEFI Manager nei dispositivi che non verranno gestiti con SEMM, puoi configurare Microsoft Surface UEFI Manager come dipendenza degli script di SEMM Configuration Manager. Questo scenario è descritto nella sezione [Distribuire gli script di Configuration Manager SEMM](#deploy-semm-configuration-manager-scripts) più avanti in questo articolo.

## <a name="create-or-modify-the-semm-configuration-manager-scripts"></a>Creare o modificare gli script di SEMM Configuration Manager

Dopo l'installazione degli assembly necessari nei dispositivi, il processo di registrazione dei dispositivi in SEMM e configurazione di Surface UEFI viene eseguito con script di PowerShell e distribuito come applicazione script con Configuration Manager. Questi script possono essere modificati in base alle esigenze dell'organizzazione e dell'ambiente. Ad esempio, puoi creare più configurazioni per i dispositivi Surface gestiti in reparti o ruoli diversi. È possibile scaricare esempi di script per SEMM e Configuration Manager dal collegamento nella sezione [Prerequisiti](#prerequisites) all'inizio di questo articolo.

Esistono due script principali necessari per eseguire una distribuzione SEMM con Configuration Manager:

* **ConfigureSEMM.ps1** : usa questo script per creare pacchetti di configurazione per i dispositivi Surface con le impostazioni UEFI di Surface desiderate per applicare le impostazioni specificate a un dispositivo Surface, registrare il dispositivo in SEMM e impostare una chiave del Registro di sistema usata per identificare la registrazione del dispositivo in SEMM.
* **ResetSEMM.ps1** : usa questo script per reimpostare SEMM su un dispositivo Surface, che lo annulla da SEMM e rimuove il controllo sulle impostazioni UEFI di Surface.

Gli script di esempio includono esempi di come impostare le impostazioni UEFI di Surface e come controllare le autorizzazioni per tali impostazioni. Queste impostazioni possono essere modificate per proteggere Surface UEFI e impostare le impostazioni UEFI di Surface in base alle esigenze del tuo ambiente. Nelle sezioni seguenti di questo articolo viene illustrato lo script ConfigureSEMM.ps1 ed esplorare le modifiche necessarie allo script per soddisfare le proprie esigenze.

> [!NOTE]
> Gli script di SEMM Configuration Manager e il file di certificato SEMM esportato (con estensione pfx) devono essere inseriti nella stessa cartella senza altri file prima di essere aggiunti a Configuration Manager.

### <a name="specify-certificate-and-package-names"></a>Specificare i nomi dei certificati e dei pacchetti

La prima area dello script che devi modificare è la parte che specifica e carica il certificato SEMM e indica anche la versione di SurfaceUEFIManager e i nomi per il pacchetto di configurazione SEMM e il pacchetto di reimpostazione SEMM. Il nome del certificato e la versione di SurfaceUEFIManager sono specificati nelle righe da 56 a 73 nello script ConfigureSEMM.ps1.

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

Sostituire il **valore FabrikamSEMMSample.pfx** per la **variabile $certName** con il nome del file di certificato SEMM nella riga 58. Lo script creerà una directory di lavoro (denominata Config) nella cartella in cui si trovano gli script e quindi copierà il file del certificato in questa directory di lavoro.

Il pacchetto proprietario e il pacchetto di reimpostazione verranno creati anche nella directory Config e conteneranno la configurazione per le impostazioni UEFI di Surface e le autorizzazioni generate dallo script.

Nella riga 73 sostituire il valore della variabile **$password** , **da 1234** alla password del file di certificato. Se non è necessaria una password, eliminare il **testo 1234** .

> [!Note]
> Gli ultimi due caratteri dell'identificazione personale del certificato sono necessari per registrare un dispositivo in SEMM. Questo script visualizza queste cifre all'utente, che consente all'utente o al tecnico di registrare queste cifre prima del riavvio del sistema per registrare il dispositivo in SEMM. Per ottenere questo risultato, lo script utilizza il codice seguente, disponibile nelle righe 150-155.

```powershell
150 # Device owners will need the last two characters of the thumbprint to accept SEMM ownership.
151 # For convenience we get the thumbprint here and present to the user.
152 $pw = ConvertTo-SecureString $password -AsPlainText -Force
153 $certPrint = New-Object System.Security.Cryptography.X509Certificates.X509Certificate2
154 $certPrint.Import($privateOwnerKey, $pw, [System.Security.Cryptography.X509Certificates.X509KeyStorageFlags]::DefaultKeySet)
155 Write-Host "Thumbprint =" $certPrint.Thumbprint
```

Gli amministratori con accesso al file di certificato (con estensione pfx) possono leggere l'identificazione personale in qualsiasi momento aprendo il file pfx in CertMgr. Per visualizzare l'identificazione personale con CertMgr, eseguire la procedura seguente:

1. Fare clic con il pulsante destro del mouse sul file pfx e quindi scegliere **Apri**.
2. Espandere la cartella nel riquadro di spostamento.
3. Selezionare **Certificati**.
4. Fare clic con il pulsante destro del mouse sul certificato nel riquadro principale e quindi scegliere **Apri**.
5. Selezionare la **scheda** Dettagli.
6. **Nel** menu **a discesa** Mostra è necessario selezionare Solo **** proprietà o Solo proprietà.
7. Selezionare il campo **Identificazione personale**.

> [!NOTE]
> Il nome del certificato SEMM e la password devono essere immessi anche in questa sezione dello script ResetSEMM.ps1 per consentire a Configuration Manager di rimuovere SEMM dal dispositivo con l'azione di disinstallazione.

### <a name="configure-permissions"></a>Configurare le autorizzazioni

La prima area dello script in cui specificare la configurazione per Surface UEFI è **l'area Configura** autorizzazioni. Questa area inizia dalla riga 210 dello script di esempio con il commento **# Configure Permissions** e continua con la riga 247. Il frammento di codice seguente imposta innanzitutto le autorizzazioni per tutte le impostazioni UEFI di Surface in modo che possano essere modificate solo da SEMM, quindi aggiunge autorizzazioni esplicite per consentire all'utente locale di modificare la password UEFI di Surface, il TPM e le fotocamere anteriori e posteriori.

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

Ogni **$uefiV 2 identifica** un'impostazione UEFI di Surface impostando il nome o l'ID e quindi configura le autorizzazioni su uno dei valori seguenti:

* **$ownerOnly** : l'autorizzazione per modificare questa impostazione viene concessa solo a SEMM.
* **$ownerAndLocalUser** : l'autorizzazione per modificare questa impostazione viene concessa a un utente locale che avvia Surface UEFI, nonché a SEMM.

Puoi trovare informazioni sui nomi e gli ID delle impostazioni disponibili per Surface UEFI nella sezione [Impostazioni Nomi e ID](#settings-names-and-ids) di questo articolo.

### <a name="configure-settings"></a>Configurare le impostazioni

La seconda area dello script in cui verrà specificata la configurazione per Surface UEFI è l'area **Configura Impostazioni** dello script di ConfigureSEMM.ps1, che configura se ogni impostazione è abilitata o disabilitata. Lo script di esempio include istruzioni per impostare tutte le impostazioni sui valori predefiniti. Lo script fornisce quindi istruzioni esplicite per disabilitare IPv6 per l'avvio PXE e lasciare invariata la password dell'amministratore UEFI di Surface. Questa area inizia con il commento **#Configure Impostazioni** alla riga 291-335 nello script di esempio. L'area viene visualizzata come segue.

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

Come le autorizzazioni impostate nella sezione **Configura** autorizzazioni dello script, la configurazione di ogni impostazione UEFI di Surface viene eseguita definendo la **variabile $uefiV 2** . Per ogni riga che definisce la **variabile $uefiV 2** , un'impostazione UEFI di Surface viene identificata dal nome o dall'ID dell'impostazione e il valore configurato è impostato su **Abilitato** o **Disabilitato**.

Se non vuoi modificare la configurazione di un'impostazione UEFI di Surface, ad esempio per assicurarti che la password di amministratore UEFI di Surface non sia cancellata dall'azione di reimpostare tutte le impostazioni UEFI di Surface sul valore predefinito, puoi usare **ClearConfiguredValue()** per imporre che questa impostazione non verrà modificata. Nello script di esempio viene usato nella riga 323 per impedire la cancellazione della password dell'amministratore UEFI di Surface, identificata nello script di esempio dal relativo ID di impostazione, **501**.

Puoi trovare informazioni sui nomi delle impostazioni disponibili e sugli ID per Surface UEFI nella sezione Nomi e ID [di Impostazioni](#settings-names-and-ids) più avanti in questo articolo.

### <a name="settings-registry-key"></a>Impostazioni del Registro di sistema

Per identificare i sistemi registrati per Configuration Manager, lo script di ConfigureSEMM.ps1 scrive le chiavi del Registro di sistema che possono essere utilizzate per identificare i sistemi registrati come installati con lo script di configurazione SEMM. Queste chiavi sono disponibili nel percorso seguente.

`HKLM\SOFTWARE\Microsoft\Surface\SEMM`

Il frammento di codice seguente, disponibile nelle righe 380-477, viene utilizzato per scrivere queste chiavi del Registro di sistema.

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

### <a name="settings-names-and-ids"></a>Impostazioni nomi e ID

Per configurare le impostazioni o le autorizzazioni UEFI di Surface per le impostazioni UEFI di Surface, devi fare riferimento a ogni impostazione tramite il nome o l'ID dell'impostazione. Con ogni nuovo aggiornamento per Surface UEFI, è possibile aggiungere nuove impostazioni. L'ShowSettingsOptions.ps1 script (da SEMM_Powershell.zip in [Surface Tools per IT](https://www.microsoft.com/download/details.aspx?id=46703)) fornisce informazioni dettagliate sulle impostazioni disponibili. Nel computer in ShowSettingsOptions.ps1 deve essere installato Microsoft Surface UEFI Manager, ma lo script non richiede un dispositivo Surface.


## <a name="deploy-semm-configuration-manager-scripts"></a>Distribuire gli script di SeMM Configuration Manager

Dopo aver preparato gli script per configurare e abilitare SEMM nel dispositivo client, il passaggio successivo consiste nell'aggiungere questi script come applicazione in Configuration Manager. Prima di aprire Configuration Manager, verificare che i file seguenti si presentino in una cartella condivisa che non include altri file:

* ConfigureSEMM.ps1
* ResetSEMM.ps1
* Il certificato SEMM (ad esempio SEMMCertificate.pfx)

Gli script di SeMM Configuration Manager verranno aggiunti a Configuration Manager come applicazione script. Il comando per installare SEMM con ConfigureSEMM.ps1 è il seguente.

`Powershell.exe -file ".\ConfigureSEMM.ps1"`

Il comando per disinstallare SEMM con ResetSEMM.ps1 è il seguente.

`Powershell.exe -file ".\ResetSEMM.ps1"`

Per aggiungere gli script di SeMM Configuration Manager a Configuration Manager come applicazione, utilizzare il processo seguente:

1. Avvia la Creazione guidata applicazione usando i passaggi da 1 a 5 della sezione [Distribuire Microsoft Surface UEFI Manager](#deploy-microsoft-surface-uefi-manager) in precedenza in questo articolo.

2. Procedere con la Creazione guidata applicazione come segue:

   - **Generale** : selezionare **Specificare manualmente le informazioni sull'applicazione** e quindi selezionare **Avanti**.

   - **Informazioni generali** : immettere un nome per l'applicazione (ad esempio SEMM) e qualsiasi altra informazione desiderata, ad esempio autore, versione o commenti in questa pagina. Selezionare **Avanti** per procedere.

   - **Catalogo applicazioni** : i campi di questa pagina possono essere lasciati con i relativi valori predefiniti. Seleziona **Avanti**.

   - **Tipi di distribuzione** : selezionare **Aggiungi** per avviare la Creazione guidata tipo di distribuzione.

   - Procedere con i passaggi della Creazione guidata tipo di distribuzione, come indicato di seguito:

     * **Generale** : selezionare **Programma di installazione script** **dal menu** a discesa Tipo. **L'opzione Specifica manualmente le informazioni sul tipo di** distribuzione verrà selezionata automaticamente. Selezionare **Avanti** per procedere.
     * **Informazioni generali** : immettere un nome per il tipo di distribuzione ,ad esempio Script di configurazione SEMM, e quindi **selezionare Avanti** per continuare.
     * **Contenuto** : selezionare **Sfoglia** accanto al **campo Percorso** contenuto e quindi selezionare la cartella in cui si trovano gli script di SEMM Configuration Manager. Nel campo **Programma di** installazione digitare il comando [di installazione](#deploy-semm-configuration-manager-scripts) riportato in precedenza in questo articolo. Nel campo **Disinstalla programma** immettere il comando [di disinstallazione](#deploy-semm-configuration-manager-scripts) riportato in precedenza in questo articolo (illustrato nella figura 2). Selezionare **Avanti** per passare alla pagina successiva.
    
     ![Imposta gli script di SEMM Configuration Manager come comandi di installazione e disinstallazione.](images/config-mgr-semm-fig2.png "Set the SEMM Configuration Manager scripts as the install and uninstall commands")

     *Figura 2. Impostare gli script di SeMM Configuration Manager come comandi di installazione e disinstallazione*

     * **Metodo di rilevamento** : selezionare **Aggiungi clausola** per aggiungere la regola di rilevamento delle chiavi del Registro di sistema dello script seMM Configuration Manager. Viene **visualizzata la** finestra Regola di rilevamento, come illustrato nella figura 3. Usa le impostazioni seguenti:

       - Seleziona **Registro** di sistema dal menu a discesa **Tipo** di impostazione.
       - Seleziona **HKEY_LOCAL_MACHINE** dal menu a discesa **Hive** .
       - Immetti **SOFTWARE\Microsoft\Surface\SEMM** nel **campo** Chiave.
       - Immettere **CertName** nel **campo** Valore.
       - Selezionare **String** dal menu **a discesa Tipo** di dati.
       - Selezionare **l'impostazione Del Registro di sistema deve soddisfare la regola seguente per indicare la presenza di questo pulsante dell'applicazione** .
       - Immettere il nome del certificato immesso nella riga 58 dello script nel **campo** Valore.
       - Selezionare **OK** per chiudere la **finestra Regola di** rilevamento.

     ![Usa una chiave del Registro di sistema per identificare i dispositivi registrati in SEMM.](images/config-mgr-semm-fig3.png "Use a registry key to identify devices enrolled in SEMM")
     
     *Figura 3. Usare una chiave del Registro di sistema per identificare i dispositivi registrati in SEMM*

     * Selezionare **Avanti** per passare alla pagina successiva.
     
     * **Esperienza utente** : selezionare **Installa per il** sistema dal menu a discesa **Installation Behavior** . Se si desidera che gli utenti registrano e immissione dell'identificazione personale del certificato, lasciare il requisito di accesso impostato su **Solo quando un utente è connesso**. Se si desidera che gli amministratori immissione dell'identificazione personale per gli utenti e gli utenti non devono visualizzare l'identificazione personale, selezionare Se un utente è connesso o meno dal menu **a** discesa **Requisito** di accesso.

     * **Requisiti** : lo script ConfigureSEMM.ps1 verifica automaticamente che il dispositivo sia un dispositivo Surface prima di tentare di abilitare SEMM. Tuttavia, se intendi distribuire questa applicazione script in una raccolta con dispositivi diversi da quelli da gestire con SEMM, puoi aggiungere qui i requisiti per assicurarti che questa applicazione sia eseguita solo nei dispositivi Surface o nei dispositivi che intendi gestire con SEMM. Selezionare **Avanti** per continuare.
     
     * **Dipendenze** : selezionare **Aggiungi** per aprire la **finestra Aggiungi** dipendenza.

       * Selezionare **Aggiungi** per aprire la **finestra Specifica applicazione** necessaria.

          - Immettere un nome per le dipendenze SEMM nel campo **Nome** gruppo di dipendenze (ad esempio, *Assembly SEMM*).

          - Seleziona **Microsoft Surface UEFI Manager** nell'elenco Applicazioni **** disponibili e il tipo di distribuzione MSI, quindi seleziona **OK** per chiudere la **finestra Specifica applicazione** necessaria.
          
         *   Tieni selezionata **la casella di** controllo Installazione automatica se vuoi che Microsoft Surface UEFI Manager sia installato automaticamente nei dispositivi quando tenti di abilitare SEMM con gli script di Configuration Manager. Selezionare **OK** per chiudere la **finestra Aggiungi** dipendenza.

     * Selezionare **Avanti** per procedere.
     
     * **Riepilogo** : le informazioni immesse durante la procedura guidata Crea tipo di distribuzione vengono visualizzate in questa pagina. Selezionare **Avanti** per confermare le selezioni.
     
     * **Progress** : in questa pagina vengono visualizzati l'indicatore di stato e lo stato del tipo di distribuzione per l'applicazione script SEMM.
     
     * **Completamento** : al termine del processo viene visualizzata la conferma della creazione del tipo di distribuzione. Selezionare **Chiudi per** completare la Creazione guidata tipo di distribuzione.

   - **Riepilogo** : vengono visualizzate le informazioni immesse durante la Creazione guidata applicazione. Selezionare **Avanti** per creare l'applicazione.

   - **Progress** : in questa pagina vengono visualizzati un indicatore di stato e uno stato quando l'applicazione viene aggiunta alla Raccolta software.

   - **Completamento** : al termine del processo di creazione dell'applicazione viene visualizzata la conferma della corretta creazione dell'applicazione. Selezionare **Chiudi per** completare la Creazione guidata applicazione.

Una volta che l'applicazione script è disponibile nella Raccolta software di Configuration Manager, puoi distribuire SEMM usando gli script preparati per dispositivi o raccolte. Se hai configurato gli assembly di Microsoft Surface UEFI Manager come dipendenza che verrà installata automaticamente, puoi distribuire SEMM in un unico passaggio. Se non hai configurato gli assembly come dipendenza, questi devono essere installati nei dispositivi che intendi gestire prima di abilitare SEMM.

Quando si distribuisce SEMM utilizzando questa applicazione script e con una configurazione visibile all'utente finale, lo script di PowerShell verrà avviato e l'identificazione personale del certificato verrà visualizzata dalla finestra di PowerShell. Puoi chiedere agli utenti di registrare questa identificazione personale e immetterla quando richiesto da Surface UEFI dopo il riavvio del dispositivo.

In alternativa, è possibile configurare l'installazione dell'applicazione per il riavvio automatico e l'installazione invisibile all'utente. In questo scenario, un tecnico dovrà immettere l'identificazione personale in ogni dispositivo al riavvio. Qualsiasi tecnico con accesso al file del certificato può leggere l'identificazione personale visualizzando il certificato con CertMgr. Le istruzioni per la visualizzazione dell'identificazione personale con CertMgr sono disponibili nella sezione Creare o modificare gli [script di SEMM Configuration Manager](#create-or-modify-the-semm-configuration-manager-scripts) di questo articolo.

La rimozione di SEMM da un dispositivo distribuito con Configuration Manager con questi script è semplice come disinstallare l'applicazione con Configuration Manager. Questa azione avvia lo script ResetSEMM.ps1 e annulla correttamente la registrazione del dispositivo con lo stesso file di certificato usato durante la distribuzione di SEMM.

> [!NOTE]
> Microsoft Surface consiglia di creare pacchetti di reimpostazione solo quando devi annullare la registrazione di un dispositivo. Questi pacchetti di reimpostazione sono in genere validi per un solo dispositivo, identificato dal relativo numero di serie. Puoi, tuttavia, creare un pacchetto di reimpostazione universale che funzioni per qualsiasi dispositivo registrato in SEMM con questo certificato.
> 
> Ti consigliamo vivamente di proteggere il pacchetto di reimpostazione universale con la prudenza del certificato usato per registrare i dispositivi in SEMM. Ricorda che, proprio come il certificato stesso, questo pacchetto di reimpostazione universale può essere usato per annullare la registrazione di qualsiasi dispositivo Surface dell'organizzazione da SEMM.
> 
> Quando installi un pacchetto di reimpostazione, il valore LSV (Lowest Supported Value) viene reimpostato su un valore pari a 1. Puoi eseguire di nuovo la registrazione di un dispositivo usando un pacchetto di configurazione esistente. Il dispositivo richiederà l'identificazione personale del certificato prima di assumere la proprietà.
> 
> Per questo motivo, la nuova registrazione di un dispositivo in SEMM richiederebbe la creazione e l'installazione di un nuovo pacchetto in tale dispositivo. Poiché questa azione è una nuova registrazione e non una modifica della configurazione in un dispositivo già registrato in SEMM, il dispositivo richiederà l'identificazione personale del certificato prima di assumere la proprietà.

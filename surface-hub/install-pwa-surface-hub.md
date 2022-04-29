---
title: Installare App Web progressive in Surface Hub
description: Spiega come gli amministratori possono installare i App Web progressivi (PWA) in Surface Hub tramite Intune o un pacchetto di provisioning.
keywords: Surface Hub, PWA, app
ms.reviewer: dpandre
manager: laurawi
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 04/27/2022
ms.localizationpriority: medium
audience: ITPro
ms.openlocfilehash: 687dd85d3490d420133edc5b7de3b2af0c0433ef
ms.sourcegitcommit: e1d7782c2d205da9d1eb6b7aad0333350f2cb5a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/29/2022
ms.locfileid: "12497550"
---
# <a name="install-progressive-web-apps-on-surface-hub"></a>Installare App Web progressive in Surface Hub

Il supporto dell'app Web progressiva (PWA) apre una nuova e completa origine di app che estende in modo significativo la libreria di app disponibili che possono essere eseguite nell'hub Suface.  Gli utenti possono accedere a un'ampia gamma di applicazioni all'esterno del Microsoft Store ed eseguirle direttamente dal menu App.  Rispetto alle pagine Web, le pwa si comportano più come app native con funzionalità offline, la possibilità di eseguire l'aggiornamento in background e altre funzionalità univoche. La maggior parte dei siti Web può essere installata come PWA e sfruttare qualsiasi funzionalità aggiuntiva abilitata dagli sviluppatori Web.

Gli amministratori possono installare i pwa in remoto in Surface Hub tramite provider di gestione dei dispositivi mobili (MDM) come Microsoft Intune. In alternativa, è possibile usare un pacchetto di provisioning. Questo articolo descrive entrambi i metodi con codice di esempio per l'installazione di YouTube, WebEx, Zoom e Uber e le istruzioni per l'installazione dei propri PWA. Per altre informazioni, vedere [Panoramica delle App Web progressive](/microsoft-edge/progressive-web-apps-chromium/).

> [!IMPORTANT]
> Prima di installare le pwa, assicurarsi che nel Surface Hub sia installato [KB5011543](https://support.microsoft.com/help/5011543) (o un aggiornamento Windows successivo). Per altre informazioni sugli aggiornamenti Windows 10 Team più recenti, vedere [Surface Hub cronologia degli aggiornamenti](surface-hub-update-history.md).

- [Installare pwa in Surface Hub tramite Intune](#install-pwas-via-intune)
- [Installare pwa in Surface Hub tramite il pacchetto di provisioning](#install-pwas-via-provisioning-package)

Gli utenti possono anche installare le pwa da usare durante la sessione dell'hub. Al termine della sessione, le pwa vengono rimosse. Per altre informazioni, vedere [Installare, gestire o disinstallare app in Microsoft Edge](https://support.microsoft.com/topic/install-manage-or-uninstall-apps-in-microsoft-edge-0c156575-a94a-45e4-a54f-3a84846f6113)

## <a name="install-pwas-via-intune"></a>Installare le pwa tramite Intune

Usare Intune o un altro provider MDM per installare pwa in Surface Hubs. Per altre informazioni, vedere [Gestire le impostazioni con un provider MDM](manage-settings-with-mdm-for-surface-hub.md).

### <a name="get-started"></a>Informazioni di base

1. Accedere al portale di Intune [**nell'interfaccia di amministrazione di Microsoft Endpoint Manager**](https://endpoint.microsoft.com/).

2. Passare a **DispositiviCriteri** **** > **di configurazioneCrea** >  **profilo**.

3. In Piattaforma selezionare **Windows 10 e versioni successive**. In Tipo di profilo selezionare **Modelli**. In Nome modello selezionare **Modelli amministrativi.**

4. Selezionare **Crea.**

    :::image type="content" source="images/pwa-hubpwainstall.png" alt-text="Creare Intune profilo di configurazione" lightbox="images/pwa-hubpwainstall.png":::

5. Assegnare un nome al profilo, immettere una descrizione facoltativa e selezionare **Avanti**.

    :::image type="content" source="images/pwa-hubwebappscreateprofile.png" alt-text="Profilo del nome" lightbox="images/pwa-hubwebappscreateprofile.png":::

### <a name="configure-force-installed-web-apps-policy-intune"></a>Configurare i criteri di App Web forzati installati (Intune)

1. In **All Impostazioni** >  **Computer Configuration** (Configurazione computer) selezionare **Microsoft Edge** e nella casella Di ricerca immettere **force-installed (Forza installazione**), selezionare **force-installed App Web (Forza installazione App Web**) e quindi selezionare **Enabled (Abilitato).**

    :::image type="content" source="images/pwa-enable-force-install.png" alt-text="Abilitare le app Web installate forzatamente" lightbox="images/pwa-enable-force-install.png":::

2. In **URL per App Web essere installato in modo invisibile all'utente**, copiare e immettere il frammento di codice seguente per installare le pwa per YouTube, Webex, Zoom e Uber. In alternativa, passare al passaggio successivo per installare altre pwa.

    :::image type="content" source="images/hub-pwa-install-enable.png" alt-text="Immettere l'elenco delle app Web installate forzatamente" lightbox="images/hub-pwa-install-enable.png":::

    ```json
    [
    { "url": "https://www.youtube.com/",       "default_launch_container": "window" },
    { "url": "https://signin.webex.com/join",  "default_launch_container": "window" },
    { "url": "https://zoom.us/join",           "default_launch_container": "window" },
    { "url": "https://www.uber.com/",          "default_launch_container": "tab"}
    ]
    ```

3. In alternativa, è possibile creare un frammento JSON dalla sintassi seguente per installare altre pwa.

    ```json
    [ { "url": "https://www.contoso.com ",   "default_launch_container": "window" }, 
    
   { "url": "https://www.fabrikam.com/",   "default_launch_container": "tab"  } ]
    ```

4. Nella pagina Tag ambito selezionare **Avanti** per ignorare.

5. Nella pagina Assegnazioni selezionare **Aggiungi gruppi** in **Gruppi inclusi**.

    :::image type="content" source="images/pwa-add-groups.png" alt-text="Aggiungi gruppi" lightbox="images/pwa-add-groups.png" :::

6. In **Seleziona gruppi da includere** immettere il nome di un gruppo contenente i surface hub di destinazione, scegliere **Seleziona** e quindi fare clic su **Avanti**. Per altre informazioni sull'assegnazione di un profilo di configurazione a un gruppo, vedere [Aggiungere gruppi per organizzare utenti e dispositivi](/mem/intune/fundamentals/groups-add).

    :::image type="content" source="images/pwa-select-groups.png" alt-text="Selezionare i gruppi" lightbox="images/pwa-select-groups.png":::

7. Esaminare e quindi selezionare **Crea**.

    :::image type="content" source="images/pwa-create-profile.png" alt-text="Creare il profilo" lightbox="images/pwa-create-profile.png" :::

8. Per applicare il profilo di configurazione in modo immmediately, selezionare **DispositiviTutti** >  **i dispositivi** e trovare il dispositivo di destinazione. Aprire il riquadro Panoramica e selezionare **Sincronizza**.

    :::image type="content" source="images/pwa-sync-tenant.png" alt-text="Tenant di sincronizzazione" lightbox="images/pwa-select-groups.png":::

 > [!IMPORTANT]
 > Per completare l'installazione di PWA, passare alla Surface Hub e avviare Edge. Le pwa vengono installate e visualizzate nell'elenco menu Start Tutte le app.

 ### <a name="troubleshooting-intune-managed-pwas"></a>Risoluzione dei problemi relativi alle pwa gestite da Intune
 
Se le pwa non sono elencate in **Tutte le app:**

- Assicurarsi che il Surface Hub disponga degli aggiornamenti più recenti, in particolare [KB5011543](https://support.microsoft.com/help/5011543) (o un aggiornamento Windows successivo). Per altre informazioni sugli aggiornamenti Windows 10 Team più recenti, vedere [Surface Hub cronologia degli aggiornamenti](surface-hub-update-history.md).
- Verificare che il profilo di configurazione sia stato applicato correttamente e che non sia in conflitto con altre impostazioni. 
- Verificare che il profilo di configurazione sia destinato a un gruppo di sicurezza che contiene il Surface Hub. 
- Ricordarsi di avviare Edge una sola volta nel Surface Hub, che è necessario per l'installazione corretta delle pwa gestite da Intune.

## <a name="install-pwas-via-provisioning-package"></a>Installare le pwa tramite il pacchetto di provisioning

È possibile installare le pwa applicando un pacchetto di provisioning a Surface Hub usando un'unità USB. Per altre informazioni, vedere [Creare pacchetti di provisioning](/surface-hub/provisioning-packages-for-surface-hub#use-surface-hub-provisioning-wizard).

### <a name="get-started-with-provisioning"></a>Attività iniziali con provisioning

1. In un PC separato che esegue Windows 10 o Windows 11 installare [Windows Configuration Designer](https://www.microsoft.com/store/apps/9nblggh4tx22) (WCD) dal Microsoft Store.

2. In WCD creare un nuovo Project. Selezionare **Provision Desktop Devices (Esegui il provisioning di dispositivi desktop),** specificare un nome per il progetto e scegliere **Fine.**

3. Selezionare **Passa all'editor avanzato** e selezionare **Sì** per confermare.

### <a name="configure-msedgepolicy"></a>Configurare MSEdgePolicy

1. Nel riquadro Personalizzazioni disponibili in WCD passare a **\Runtime Impostazioni\ADMXIngestion\ConfigOperations\ADMXInstall\AppName**

2. Nel riquadro di modifica delle personalizzazioni immettere il nome dell'app come **MSEdgePolicy** e selezionare **Aggiungi**.

    :::image type="content" source="images/pwa-add-edge-policy.png" alt-text="Immettere il nome dell'app come MSEdgePolicy" lightbox="images/pwa-add-edge-policy.png" :::

3. Nel riquadro Personalizzazioni disponibili selezionare **AppName: MSEdgePolicy** e nel riquadro di modifica impostare **SettingType** su **Policy** e scegliere **Aggiungi**.

4. Nel riquadro Personalizzazioni disponibili selezionare **SettingType: Policy** e nel riquadro di modifica impostare **AdmxFileUid** su **MSEdgePolicy** e scegliere **Aggiungi**.

5. Nel riquadro Personalizzazioni disponibili selezionare **AdmxFileUid: MSEdgePolicy** e nel riquadro di modifica impostare **MSEdgePolicy** immettendo il codice seguente come singola riga di testo:

   :::image type="content" source="images/pwa-enter-edge-policy.png" alt-text="Immettere il codice per MSEdgePolicy" lightbox="images/pwa-enter-edge-policy.png" :::

    ```xml
    <policyDefinitions revision="1.0" schemaVersion="1.0" xmlns="http://www.microsoft.com/GroupPolicy/PolicyDefinitions">  <!--microsoft_edge version: 96.0.1054.53-->  <policyNamespaces>    <target namespace="Microsoft.Policies.Edge" prefix="microsoft_edge"/>    <using namespace="Microsoft.Policies.Windows" prefix="windows"/>  </policyNamespaces>  <resources minRequiredRevision="1.0"/>  <supportedOn>    <definitions>      <definition displayName="$(string.SUPPORTED_WIN7_V80)" name="SUPPORTED_WIN7_V80"/>     </definitions>  </supportedOn>  <categories>    <category displayName="$(string.microsoft_edge)" name="microsoft_edge"/>    <category displayName="$(string.microsoft_edge_recommended)" name="microsoft_edge_recommended"/>  </categories>  <policies>    <policy class="Both" displayName="$(string.WebAppInstallForceList)" explainText="$(string.WebAppInstallForceList_Explain)" key="Software\Policies\Microsoft\Edge" name="WebAppInstallForceList" presentation="$(presentation.WebAppInstallForceList)">      <parentCategory ref="microsoft_edge"/>      <supportedOn ref="SUPPORTED_WIN7_V80"/>      <elements>        <text id="WebAppInstallForceList" maxLength="1000000" valueName="WebAppInstallForceList"/>      </elements>    </policy>    </policies></policyDefinitions>
    ```

### <a name="configure-force-installed-web-apps-policy-provisioning-package"></a>Configurare i criteri di App Web installati forzatamente (pacchetto di provisioning)

1. Nel riquadro Personalizzazioni disponibili in WCD passare a: **\Runtime Impostazioni\ADMXIngestion\ConfigADMXInstalledPolicy\AreaName**

2. Nel riquadro di modifica delle personalizzazioni immettere nomearea come **MSEdgePolicy~Policy~microsoft_edge,** selezionare **Aggiungi**.

3. Nel riquadro Personalizzazioni disponibili selezionare **AreaName: MSEdgePolicy~Policy~microsoft_edge** e nel riquadro di modifica impostare **Nome criterio** su **WebAppInstallForceList** e selezionare **Aggiungi**.

4. Nel riquadro Personalizzazioni disponibili selezionare **PolicyName: WebAppInstallForceList** e nel riquadro di modifica per **WebAppInstallForceList** immettere [PWA codice](#ppkg-code-samples) come singola riga di testo.

    :::image type="content" source="images/pwa-force-web-app-install.png" alt-text="Immettere il codice per i criteri di App Web forzati" lightbox="images/pwa-force-web-app-install.png":::

### <a name="ppkg-code-samples"></a>Esempi di codice PPKG

- YouTube PWA:

    ```xml
    <enabled/><data id="WebAppInstallForceList" value="[{&quot;url&quot;: &quot;https://www.youtube.com&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;}]"/>
    ```

- Più PWA tra cui YouTube, Webex, Zoom e Uber:

    ```xml
     <enabled/><data id="WebAppInstallForceList" value="[{&quot;url&quot;: &quot;https://www.youtube.com&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;},{&quot;url&quot;: &quot;https://www.signin.webex.com/join&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;},{&quot;url&quot;: &quot;https://zoom.us/join&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;},{&quot;url&quot;: &quot;https://www.uber.com&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;}]"/>
    ```

- In alternativa, è possibile creare un frammento JSON dalla sintassi seguente per installare altre pwa:

    ```xml
    <enabled/><data id="WebAppInstallForceList" value="[{&quot;url&quot;: &quot;https://www.contoso.com&quot;, &quot;create_desktop_shortcut&quot;: true, &quot;default_launch_container&quot;: &quot;window&quot;}]"/>
    ```

### <a name="export-provisioning-package-and-apply-to-surface-hubs"></a>Esportare il pacchetto di provisioning e applicarlo a Surface Hub

1. Nella barra dei menu selezionare **Esporta**, selezionare **Pacchetto di provisioning** e seguire le istruzioni per generare il file con estensione ppkg.

2. Inserire un'unità flash USB vuota. Selezionare il percorso di output per passare alla posizione del pacchetto. Copiare il file con estensione ppkg nell'unità USB.

3. Applicare il pacchetto di provisioning tramite l'app Impostazioni o durante l'installazione della prima esecuzione. Per altre informazioni, vedere [Creare pacchetti di provisioning](/surface-hub/provisioning-packages-for-surface-hub#apply-a-provisioning-package-to-surface-hub)

 ### <a name="troubleshooting-provisioning-package-pwas"></a>Risoluzione dei problemi relativi ai pacchetti di provisioning pwa
 
Se le pwa non sono elencate in **Tutte le app**:

- Assicurarsi che il Surface Hub disponga degli aggiornamenti più recenti, in particolare [KB5011543](https://support.microsoft.com/help/5011543) (o un aggiornamento Windows successivo). Per altre informazioni sugli aggiornamenti Windows 10 Team più recenti, vedere [Surface Hub cronologia degli aggiornamenti](surface-hub-update-history.md).

## <a name="learn-more"></a>Scopri di più

- [Riferimento WCD: ADMXIngestion](/windows/configuration/wcd/wcd-admxingestion)
- [Panoramica di progressive App Web (PWA)](/microsoft-edge/progressive-web-apps-chromium/)

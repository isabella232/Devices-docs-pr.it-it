---
title: Gestire DFCI nei dispositivi Surface
description: Questo articolo spiega come configurare un ambiente DFCI in Microsoft Intune e gestire le impostazioni del firmware per i dispositivi Surface di destinazione.
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 04/13/2021
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
- Surface Laptop 4
ms.openlocfilehash: b9b58406bbd256e79aec9065c5e25f618e584a02
ms.sourcegitcommit: d6ac31a94b6630f04cf3469d5dcf8b66e46c7412
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2021
ms.locfileid: "11911971"
---
# <a name="manage-dfci-on-surface-devices"></a>Gestire DFCI nei dispositivi Surface

## <a name="introduction"></a>Introduzione

La possibilità di gestire i dispositivi dal cloud ha notevolmente semplificato la distribuzione e il provisioning IT nel ciclo di vita. Con i profili DFCI (Device Firmware Configuration Interface) incorporati in [Microsoft Intune,](/intune/configuration/device-firmware-configuration-interface-windows)la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning senza tocco, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, tra cui le opzioni di avvio e le periferiche incorporate, e costituisce le basi per scenari di sicurezza avanzati in futuro. Per le risposte alle domande frequenti, vedi [Ignite 2019: Annuncio](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333)della gestione remota delle impostazioni UEFI di Surface da Intune.

### <a name="background"></a>Background

Come qualsiasi computer che esegue Windows 10, i dispositivi Surface si basano sul codice archiviato nel SoC che consente alla CPU di interfacciarsi con i dischi rigidi, i dispositivi di visualizzazione, le porte USB e altri dispositivi. I programmi archiviati in questa memoria di sola lettura (ROM) sono noti come firmware (mentre i programmi archiviati in supporti dinamici sono noti come software).

A differenza degli altri dispositivi Windows 10 attualmente disponibili sul mercato, Surface offre agli amministratori IT la possibilità di configurare e gestire il firmware tramite un ricco set di impostazioni di configurazione UEFI. Ciò fornisce un livello di controllo hardware sulla gestione dei criteri basata su software implementata tramite i criteri di gestione dei dispositivi mobili (MDM), Configuration Manager o Criteri di gruppo. Ad esempio, le organizzazioni che distribuiscono dispositivi in aree altamente sicure con informazioni riservate possono impedire l'uso della fotocamera rimuovendo la funzionalità a livello hardware. Dal punto di vista del dispositivo, spegnere la fotocamera tramite un'impostazione del firmware equivale a rimuovere fisicamente la fotocamera. Confronta la sicurezza aggiunta della gestione a livello di firmware con l'uso solo delle impostazioni del software del sistema operativo. Ad esempio, se disabiliti il servizio audio Windows tramite un'impostazione dei criteri in un ambiente di dominio, un amministratore locale potrebbe comunque riattivare il servizio.

### <a name="dfci-versus-semm"></a>DFCI e SEMM

In precedenza, la gestione del firmware richiedeva la registrazione dei dispositivi nella modalità di gestione di Surface Enterprise (SEMM) con l'overhead delle attività manuali che richiedono un utilizzo intensivo dell'IT. Ad esempio, SEMM richiede al personale IT di accedere fisicamente a ogni PC per immettere un pin a due cifre come parte del processo di gestione dei certificati. Anche se SEMM rimane una buona soluzione per le organizzazioni in un ambiente strettamente locale, la complessità e i requisiti di utilizzo intensivo dell'IT rendono molto dispendario l'utilizzo.

 Con le funzionalità integrate di gestione del firmware UEFI in Microsoft Intune, la possibilità di bloccare l'hardware è semplificata e più facile da usare con le nuove funzionalità per il provisioning, la sicurezza e l'aggiornamento semplificato in un'unica console, ora unificata [come Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager). La figura seguente mostra le impostazioni UEFI visualizzate direttamente nel dispositivo (a sinistra) e visualizzate nella console Endpoint Manager (a destra).

![Impostazioni UEFI visualizzate nel dispositivo (a sinistra) e nella console Endpoint Manager (a destra).](images/uefidfci.png)

Fondamentalmente, DFCI consente la gestione zero touch, eliminando la necessità di interazione manuale da parte degli amministratori IT. DFCI viene distribuito tramite Windows Autopilot usando la funzionalità dei profili dispositivo in Intune. Un profilo di dispositivo consente di aggiungere e configurare impostazioni che possono essere distribuite ai dispositivi registrati nella gestione all'interno dell'organizzazione. Una volta che il dispositivo riceve il profilo del dispositivo, le funzionalità e le impostazioni vengono applicate automaticamente. Esempi di profili di dispositivo comuni includono i modelli di posta elettronica, restrizioni del dispositivo, VPN, Wi-Fi e amministrativi. DFCI è semplicemente un profilo di dispositivo aggiuntivo che consente di gestire le impostazioni di configurazione UEFI dal cloud senza dover gestire l'infrastruttura locale.  

## <a name="supported-devices"></a>Dispositivi supportati

DFCI è supportato nei dispositivi seguenti:

- Surface Pro 7+
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
- Surface Laptop Go
- Surface Laptop 4

> [!NOTE]
> Surface Pro X non supporta la gestione delle impostazioni DFCI per fotocamera, audio e Wi-Fi/Bluetooth incorporati.

## <a name="prerequisites"></a>Prerequisiti

- I dispositivi devono essere registrati con Windows Autopilot da un [partner Microsoft Cloud Solution Provider (CSP) o](https://partner.microsoft.com/membership/cloud-solution-provider) un distributore OEM.

- Prima di configurare DFCI per Surface, devi avere familiarità con i requisiti di configurazione di Autopilot in [Microsoft Intune](/intune/) e [Azure Active Directory](/azure/active-directory/) (Azure AD).

## <a name="before-you-begin"></a>Prima di iniziare

Aggiungi i dispositivi Surface di destinazione a un gruppo di sicurezza di Azure AD. Per ulteriori informazioni sulla creazione e la gestione dei gruppi di sicurezza, vedere la [documentazione di Intune.](/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups)

## <a name="configure-dfci-management-for-surface-devices"></a>Configurare la gestione DFCI per i dispositivi Surface

Un ambiente DFCI richiede la configurazione di un profilo DFCI contenente le impostazioni e di un profilo Autopilot per applicare le impostazioni ai dispositivi registrati. È inoltre consigliabile utilizzare un profilo di stato di registrazione per garantire che le impostazioni siano spinte verso il basso durante la configurazione della Configurazione guidata quando gli utenti avviano il dispositivo per la prima volta. Questa guida spiega come configurare l'ambiente DFCI e gestire le impostazioni di configurazione UEFI per i dispositivi Surface di destinazione.

## <a name="create-dfci-profile"></a>Creare un profilo DFCI

Prima di configurare le impostazioni dei criteri DFCI, crea innanzitutto un profilo DFCI e assegnalo al gruppo di sicurezza di Azure AD che contiene i dispositivi di destinazione.

1. Accedere al tenant all'devicemanagement.microsoft.com.
2. Nell'Microsoft Endpoint Manager di amministrazione selezionare Dispositivi **> profili di configurazione > Crea** profilo e immettere un nome; ad esempio, **Criteri di configurazione DFCI.**
3. Seleziona **Windows 10 e versioni successive per** tipo di piattaforma.
4. Nell'elenco a discesa Tipo di profilo seleziona **Device Firmware Configuration Interface** per aprire il pannello DFCI contenente tutte le impostazioni dei criteri disponibili. Per informazioni sulle impostazioni DFCI, fare riferimento alla tabella 1 in questa pagina o nella documentazione [di Intune.](/intune/configuration/device-firmware-configuration-interface-windows) È possibile configurare le impostazioni DFCI durante il processo di installazione iniziale o in un secondo momento modificando il profilo DFCI.

    ![Creare il profilo DFCI.](images/df1.png)

5. Fare **clic su OK** e quindi selezionare **Crea**.
6. Selezionare **Assegnazioni** e in Seleziona gruppi **da includere** selezionare il gruppo di sicurezza di Azure AD che contiene i dispositivi di destinazione, come illustrato nella figura seguente. Fai clic su **Salva**.

    ![Assegnare un gruppo di sicurezza.](images/df2a.png)

## <a name="create-autopilot-profile"></a>Creare un profilo Autopilot

1. In Endpoint Manager in devicemanagement.microsoft.com selezionare i dispositivi > Windows **registrazione e** scorrere verso il basso fino a Profili **di distribuzione**.
2. Selezionare **Crea profilo** e immettere un nome. ad esempio My **Autopilot profile**e selezionare **Next.**
3. Selezionare le impostazioni seguenti:

    - Modalità di distribuzione: **guidata dall'utente.**
    - Tipo di partecipazione: Aggiunta ad Azure **AD**.

4. Lasciare invariate le impostazioni predefinite rimanenti e selezionare **Avanti**, come illustrato nella figura seguente.

    ![Creare il profilo Autopilot.](images/df3b.png)

5. Nella pagina Assegnazioni scegliere Seleziona gruppi **da includere e** fare clic sul gruppo di sicurezza di Azure AD. Seleziona **Avanti**.
6. Accettare il riepilogo e quindi selezionare **Crea**. Il profilo Autopilot viene ora creato e assegnato al gruppo.

## <a name="configure-enrollment-status-page"></a>Pagina Configura stato registrazione

Per assicurarsi che i dispositivi appliche siano in grado di applicare la configurazione DFCI durante la configurazione guidata prima che gli utenti accedano, è necessario configurare lo stato di registrazione.

Per ulteriori informazioni, vedere [Set up an enrollment status page](/intune/enrollment/windows-enrollment-status).


## <a name="configure-dfci-settings-on-surface-devices"></a>Configurare le impostazioni DFCI nei dispositivi Surface

DFCI include un set semplificato di criteri di configurazione UEFI che offrono un ulteriore livello di sicurezza bloccando i dispositivi a livello hardware. DFCI è progettato per essere usato insieme alle impostazioni di gestione dei dispositivi mobili a livello software. Tieni presente che le impostazioni DFCI influiscono solo sui componenti hardware incorporati nei dispositivi Surface e non si estendono alle periferiche collegate, come le webcam USB. Tuttavia, puoi usare i criteri di restrizione dei dispositivi in Intune per disattivare l'accesso alle periferiche collegate a livello software.

È possibile configurare le impostazioni dei criteri DFCI modificando il profilo DFCI da Endpoint Manager, come illustrato nella figura seguente. 

- In Endpoint Manager in devicemanagement.microsoft.com selezionare Dispositivi > Windows > Profili di configurazione > "Nome profilo **DFCI"**> proprietà > Impostazioni .

    ![Configurare le impostazioni DFCI.](images/dfciconfig.png)

### <a name="block-user-access-to-uefi-settings"></a>Bloccare l'accesso degli utenti alle impostazioni UEFI

Per molti clienti, la possibilità di impedire agli utenti di modificare le impostazioni UEFI è fondamentale e un motivo principale per usare DFCI. Come indicato nella tabella 1, questa operazione viene gestita tramite l'impostazione Consenti all'utente locale **di modificare le impostazioni UEFI.** Se non si modifica o non si configura questa impostazione, gli utenti locali potranno modificare qualsiasi impostazione UEFI non gestita da Intune. Pertanto, è consigliabile disabilitare Consenti agli **utenti locali di modificare le impostazioni UEFI.**
Il resto delle impostazioni DFCI consente di disattivare funzionalità altrimenti disponibili per gli utenti. Ad esempio, se è necessario proteggere le informazioni riservate in aree altamente sicure, è possibile disabilitare la fotocamera e, se non si desidera che gli utenti si avviano da unità USB, è possibile disabilitare anche quella.

### <a name="table-1-dfci-scenarios"></a>Tabella 1. Scenari DFCI

| Obiettivo di gestione dei dispositivi                        | Passaggi di configurazione                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Impedire agli utenti locali di modificare le impostazioni UEFI | In **Funzionalità di sicurezza > Consenti agli utenti locali di modificare le impostazioni UEFI**selezionare **Nessuna.**              |
| Disabilitare le fotocamere                               | In **Built in Hardware > Cameras**selezionare **Disabled.**                                       |
| Disabilitare microfoni e altoparlanti              | In **Built in Hardware > Microphones and speakers**selezionare **Disabled.**                      |
| Disabilitare le radio (Bluetooth, Wi-Fi)             | In **Built in Hardware > Radios (Bluetooth, Wi-Fi e così via)** seleziona **Disabilitato.**                   |
| Disabilitare l'avvio da supporti esterni (USB, SD)    | In **Built in Hardware > Boot Options > Boot from external media (USB, SD)** seleziona **Disabled.** |

> [!CAUTION]
> L'impostazione Disattiva **radio (Bluetooth, Wi-Fi)** deve essere usata solo nei dispositivi che dispongono di una connessione Ethernet cablata.
 
> [!NOTE]
>  DFCI in Intune include due impostazioni che attualmente non si applicano ai dispositivi Surface: (1) Virtualizzazione CPU e I/O e (2) Disabilita l'avvio dalle schede di rete.
 
Intune fornisce tag di ambito per delegare i diritti amministrativi e le regole di applicabilità per gestire i tipi di dispositivi. Per ulteriori informazioni sul supporto per la gestione dei criteri e per informazioni dettagliate su tutte le impostazioni DFCI, vedere Microsoft Intune [documentazione.](/intune/configuration/device-firmware-configuration-interface-windows)

## <a name="register-devices-in-autopilot"></a>Registrare i dispositivi in Autopilot

Come indicato in precedenza, DFCI può essere applicato solo ai dispositivi registrati in Windows Autopilot dal rivenditore o dal distributore ed è supportato solo in Surface Pro 7+, Surface Laptop Go, Surface Pro 7, Surface Pro X e Surface Laptop 3. Per motivi di sicurezza, non è possibile effettuare il "provisioning automatico" dei dispositivi in Autopilot. Per altre informazioni, vedi Surface [Registration Support for Windows Autopilot.](surface-autopilot-registration-support.md) 

## <a name="manually-sync-autopilot-devices"></a>Sincronizzare manualmente i dispositivi Autopilot

Anche se le impostazioni dei criteri di Intune vengono in genere applicate quasi immediatamente, potrebbe verificarsi un ritardo di 10 minuti prima che le impostazioni siano effettive sui dispositivi di destinazione. In rari casi, sono possibili ritardi fino a 8 ore. Per garantire che le impostazioni siano applicate il prima possibile, ad esempio negli scenari di test, puoi sincronizzare manualmente i dispositivi di destinazione.

- In Endpoint Manager su devicemanagement.microsoft.com, passare a Dispositivi > Registrazione dispositivo > Windows registrazione > Windows **Dispositivi Autopilot e** selezionare **Sincronizza**.

 Per ulteriori informazioni, vedere [Sincronizzare manualmente Windows dispositivo.](/intune-user-help/sync-your-device-manually-windows)

> [!NOTE]
> Quando si modificano le impostazioni direttamente in UEFI, devi assicurarti che il dispositivo si riavvii completamente al Windows login standard.

## <a name="verifying-uefi-settings-on-dfci-managed-devices"></a>Verifica delle impostazioni UEFI nei dispositivi gestiti da DFCI

In un ambiente di testing puoi verificare le impostazioni nell'interfaccia UEFI di Surface.

1. Apri Surface UEFI, che prevede la pressione **dei pulsanti Volume +** e **Alimentazione** contemporaneamente.
2. Selezionare **Dispositivi**. Il menu UEFI rifletterà le impostazioni configurate, come illustrato nella figura seguente.

    ![Surface UEFI.](images/df3.png)

    Nota come:

      - Le impostazioni sono disattivate perché **Consenti all'utente locale di modificare** l'impostazione UEFI è impostata su Nessuno.
      - L'audio è disattivato perché **i microfoni e gli altoparlanti** sono impostati su **Disabilitato.**

## <a name="removing-dfci-policy-settings"></a>Rimozione delle impostazioni dei criteri DFCI

Quando crei un profilo DFCI, tutte le impostazioni configurate rimarranno effettive in tutti i dispositivi nell'ambito di gestione del profilo. È possibile rimuovere le impostazioni dei criteri DFCI solo modificando direttamente il profilo DFCI.

Se il profilo DFCI originale è stato eliminato, è possibile rimuovere le impostazioni dei criteri creando un nuovo profilo e quindi modificando le impostazioni, in base alle esigenze.

## <a name="removing-dfci-management"></a>Rimozione della gestione DFCI

**Per rimuovere la gestione DFCI e riportare il dispositivo al nuovo stato di fabbrica:**

1. Ritirare il dispositivo da Intune:
    1. In Endpoint Manager in devicemanagement.microsoft.com scegliere **Gruppi > tutti i dispositivi**. Seleziona i dispositivi che vuoi ritirare e quindi scegli **Ritira/Cancella.** Per ulteriori informazioni, vedere [Rimuovere i dispositivi tramite cancellazione,](/intune/remote-actions/devices-wipe)ritiro o annullamento manuale della registrazione del dispositivo. 
2. Eliminare la registrazione di Autopilot da Intune:
    1.  Scegliere **Registrazione dispositivo > Windows registrazione > dispositivi**.
    2. In Windows dispositivi Autopilot scegliere i dispositivi che si desidera eliminare e quindi scegliere **Elimina.**
3. Connessione da dispositivo a Internet cablato con scheda ethernet con marchio Surface. Riavvia il dispositivo e apri il menu UEFI (tieni premuto il pulsante di accensione del volume mentre premi e rilascia il pulsante di alimentazione).
4. Selezionare **Gestione > Configura > aggiornamento dalla rete** e quindi scegliere **Rifiuta.**

Per continuare a gestire il dispositivo con Intune, ma senza la gestione DFCI, registra automaticamente il dispositivo in Autopilot e registralo in Intune. DFCI non verrà applicato ai dispositivi auto-registrati.

## <a name="learn-more"></a>Scopri di più
- [Ignite 2019: Annuncio della](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) gestione remota delle impostazioni UEFI di Surface da Intune 
 [Windows Autopilot](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md) 
- [Usare i profili DFCI Windows dispositivi in Microsoft Intune](/intune/configuration/device-firmware-configuration-interface-windows)

---
title: Gestione di Intune delle impostazioni UEFI di Surface
description: Questo articolo spiega come configurare un ambiente DFCI in Microsoft Intune e gestire le impostazioni del firmware per i dispositivi Surface mirati.
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 08/19/2020
ms.reviewer: jesko
manager: laurawi
ms.audience: itpro
appliesto:
- Surface Pro 7
- Surface Pro X
- Surface Laptop 3
- Surface Book 3
ms.openlocfilehash: 9d83fe9b7febf996d2cb314399505ed050a69a92
ms.sourcegitcommit: b94832cba98e01014f7d184c85d79f8339e046c4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/20/2020
ms.locfileid: "10941667"
---
# Gestione di Intune delle impostazioni UEFI di Surface

## Introduzione

La possibilità di gestire i dispositivi dal Cloud semplifica notevolmente la distribuzione e il provisioning del ciclo di vita. Con i profili di DFCI (device firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in [anteprima pubblica](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)), Surface UEFI Management estende il moderno stack di gestione fino al livello hardware UEFI. DFCI supporta il provisioning a zero tocco, Elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, incluse le opzioni di avvio e le periferiche predefinite, e stabilisce le basi per scenari di sicurezza avanzati in futuro. Per le risposte alle domande frequenti, vedere [ignite 2019: annuncio della gestione remota delle impostazioni di Surface UEFI da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333).

### Background

Analogamente a qualsiasi computer con Windows 10, i dispositivi Surface si basano sul codice archiviato nel SoC che consente alla CPU di interfacciarsi con dischi rigidi, dispositivi di visualizzazione, porte USB e altri dispositivi. I programmi archiviati in questa memoria di sola lettura (ROM) sono noti come firmware (mentre i programmi archiviati in elementi multimediali dinamici sono noti come software).

A differenza di altri dispositivi Windows 10 disponibili oggi sul mercato, Surface fornisce agli amministratori IT la possibilità di configurare e gestire il firmware tramite una vasta gamma di impostazioni di configurazione UEFI. In questo modo viene fornito un livello di controllo hardware basato sulla gestione dei criteri basata su software implementato tramite criteri di gestione di dispositivi mobili (MDM), Gestione configurazione o criteri di gruppo. Ad esempio, le organizzazioni che distribuiscono dispositivi in aree altamente sicure con informazioni riservate possono impedire l'uso della fotocamera rimuovendo le funzionalità a livello di hardware. Da un punto di vista del dispositivo, la disattivazione della videocamera tramite un'impostazione del firmware equivale a rimuovere fisicamente la fotocamera. Confrontare la sicurezza aggiunta di gestione a livello di firmware per fare affidamento solo sulle impostazioni del software del sistema operativo. Ad esempio, se si disattiva il servizio audio Windows tramite un'impostazione di criteri in un ambiente di dominio, un amministratore locale potrebbe comunque riattivare il servizio.

### DFCI versus SEMM

Fino a questo momento, la gestione del firmware richiede la registrazione di dispositivi in modalità di gestione di Surface Enterprise (SEMM) con l'overhead delle attività manuali ad alta intensità di IT in corso. Ad esempio, SEMM richiede al personale IT di accedere fisicamente a ogni PC per immettere un pin a due cifre nell'ambito del processo di gestione dei certificati. Anche se SEMM rimane una buona soluzione per le organizzazioni in un ambiente rigorosamente locale, i suoi requisiti di complessità e intensivo lo rendono costoso da usare.

Ora, con le nuove funzionalità di gestione del firmware UEFI integrate in Microsoft Intune, la possibilità di bloccare l'hardware è semplificata e più facile da usare per il provisioning, la sicurezza e l'aggiornamento semplificato di tutti in una singola console, ora unificata come [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager). La figura seguente mostra le impostazioni UEFI visualizzate direttamente sul dispositivo (a sinistra) e visualizzate nella console di Endpoint Manager (a destra).

![Impostazioni UEFI visualizzate sul dispositivo (a sinistra) e nella console di Endpoint Manager (a destra)](images/uefidfci.png)

In modo cruciale, DFCI Abilita la gestione del tocco zero, eliminando l'esigenza di interagire manualmente con gli amministratori IT. DFCI è distribuito tramite Windows Autopilot usando la funzionalità dei profili di dispositivo in Intune. Un profilo di dispositivo consente di aggiungere e configurare impostazioni che possono quindi essere distribuite in dispositivi registrati in gestione all'interno dell'organizzazione. Una volta che il dispositivo riceve il profilo del dispositivo, le caratteristiche e le impostazioni vengono applicate automaticamente. Esempi di profili di dispositivi comuni includono posta elettronica, restrizioni dei dispositivi, VPN, Wi-Fi e modelli amministrativi. DFCI è semplicemente un ulteriore profilo di dispositivo che consente di gestire le impostazioni di configurazione UEFI dal cloud senza dover mantenere l'infrastruttura locale.  

## Dispositivi supportati

DFCI è supportato nei dispositivi seguenti:

- Surface Pro 7
- Surface Pro X
- Laptop Surface 3
- Surface Book 3

> [!NOTE]
> Surface Pro X non supporta la gestione delle impostazioni di DFCI per la fotocamera incorporata, l'audio e la rete Wi-Fi/Bluetooth.

## Prerequisiti

- I dispositivi devono essere registrati con il pilota automatico Windows da un [partner di Microsoft Cloud Solution Provider (CSP)](https://partner.microsoft.com/membership/cloud-solution-provider) o un distributore OEM.

- Prima di configurare DFCI per Surface, è necessario avere familiarità con i requisiti di configurazione del pilota automatico in  [Microsoft Intune](https://docs.microsoft.com/intune/) e [Azure Active Directory](https://docs.microsoft.com/azure/active-directory/) (Azure ad).

## Prima di iniziare

Aggiungere i dispositivi della superficie di destinazione a un gruppo di sicurezza di Azure AD. Per altre informazioni sulla creazione e la gestione dei gruppi di sicurezza, vedere la [documentazione di Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows#create-your-azure-ad-security-groups).

## Configurare la gestione di DFCI per i dispositivi Surface

Un ambiente DFCI richiede la configurazione di un profilo DFCI che contiene le impostazioni e un profilo Autopilot per applicare le impostazioni ai dispositivi registrati. È inoltre consigliabile un profilo di stato di registrazione per verificare che le impostazioni vengano spostate in basso durante la configurazione di OOBE quando gli utenti avviano prima il dispositivo. Questa guida spiega come configurare l'ambiente DFCI e gestire le impostazioni di configurazione UEFI per i dispositivi Surface mirati.

## Creare il profilo DFCI

Prima di configurare le impostazioni dei criteri di DFCI, creare prima di tutto un profilo DFCI e assegnarlo al gruppo di sicurezza di Azure AD che contiene i dispositivi di destinazione.

1. Accedere al tenant in devicemanagement.microsoft.com.
2. Nell'interfaccia di amministrazione di Microsoft Endpoint Manager selezionare **dispositivi > profili di configurazione > Crea profilo** e immettere un nome. ad esempio, **criteri di configurazione di DFCI.**
3. Selezionare **Windows 10 e versioni successive** per il tipo di piattaforma.
4. Nell'elenco a discesa tipo di profilo selezionare **interfaccia di configurazione del firmware del dispositivo** per aprire la DFCI Blade contenente tutte le impostazioni dei criteri disponibili. Per informazioni sulle impostazioni di DFCI, vedere la tabella 1 in questa pagina o la [documentazione di Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows). È possibile configurare le impostazioni di DFCI durante il processo di configurazione iniziale o in un secondo momento modificando il profilo DFCI.

    ![Creare il profilo DFCI](images/df1.png)

5. Fare clic su **OK** e quindi selezionare **Crea**.
6. Selezionare **assegnazioni** e in **selezionare gruppi per includere** Selezionare il gruppo di sicurezza di Azure ad contenente i dispositivi di destinazione, come illustrato nella figura seguente. Fare clic su **Save**.

    ![Assegnare un gruppo di sicurezza](images/df2a.png)

## Creare il profilo Autopilot

1. In Endpoint Manager su devicemanagement.microsoft.com selezionare **dispositivi > registrazione di Windows** e scorrere verso il basso fino a **profili di distribuzione**.
2. Selezionare **Crea profilo** e immettere un nome; ad esempio, il **mio profilo Autopilot**e selezionare **Avanti**.
3. Selezionare le impostazioni seguenti:

    - Modalità di distribuzione: **guidata dall'utente**.
    - Tipo di join: Azure **ad Unito**.

4. Lascia invariate le impostazioni predefinite rimanenti e seleziona **Avanti**, come illustrato nella figura seguente.

    ![Creare il profilo Autopilot](images/df3b.png)

5. Nella pagina assegnazioni scegliere **Seleziona gruppi da includere** e fare clic sul gruppo di sicurezza di Azure ad. Seleziona **Avanti**.
6. Accettare il riepilogo e quindi selezionare **Crea**. Il profilo del pilota automatico viene ora creato e assegnato al gruppo.

## Pagina Configura stato registrazione

Per fare in modo che i dispositivi applichino la configurazione DFCI durante OOBE prima di accedere agli utenti, è necessario configurare lo stato di registrazione.

Per altre informazioni, vedere [configurare una pagina di stato di registrazione](https://docs.microsoft.com/intune/enrollment/windows-enrollment-status).


## Configurare le impostazioni di DFCI nei dispositivi Surface

DFCI include un set semplificato di criteri di configurazione UEFI che garantiscono un livello di sicurezza aggiuntivo bloccando i dispositivi a livello di hardware. DFCI è progettato per essere usato in combinazione con le impostazioni di gestione dei dispositivi mobili a livello software. Tieni presente che le impostazioni di DFCI influenzano solo i componenti hardware incorporati in dispositivi di Surface e non si estendono alle periferiche connesse, ad esempio le webcam USB. Tuttavia, puoi usare i criteri di restrizione dei dispositivi in Intune per disattivare l'accesso alle periferiche connesse a livello software.

Puoi configurare le impostazioni dei criteri di DFCI modificando il profilo DFCI da Endpoint Manager, come illustrato nella figura seguente. 

- In Endpoint Manager su devicemanagement.microsoft.com selezionare **dispositivi > profili di configurazione di Windows > > "nome profilo DFCI" > proprietà > impostazioni**.

    ![Configurare le impostazioni di DFCI](images/dfciconfig.png)

### Bloccare l'accesso degli utenti alle impostazioni UEFI

Per molti clienti, la possibilità di impedire agli utenti di modificare le impostazioni UEFI è di importanza cruciale e un motivo principale per usare DFCI. Come elencato nella tabella 1, questa operazione viene gestita tramite l'impostazione **Consenti agli utenti locali di modificare le impostazioni UEFI**. Se non si modifica o si configura questa impostazione, gli utenti locali saranno in grado di modificare qualsiasi impostazione UEFI non gestita da Intune. Di conseguenza, è vivamente consigliabile disabilitare l'opzione **Consenti agli utenti locali di modificare le impostazioni UEFI.**
Il resto delle impostazioni di DFCI consente di disattivare la funzionalità che altrimenti sarebbe disponibile per gli utenti. Ad esempio, se devi proteggere le informazioni riservate in aree molto sicure, puoi disabilitare la videocamera e, se non vuoi che gli utenti possano eseguire l'avvio da unità USB, puoi disabilitare anche quella.

### Tabella 1. Scenari di DFCI

| Obiettivo di gestione dei dispositivi                        | Passaggi di configurazione                                                                           |
| --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Bloccare gli utenti locali dalla modifica delle impostazioni UEFI | In **caratteristiche di sicurezza > consentire agli utenti locali di modificare le impostazioni UEFI**, selezionare **Nessuna**.              |
| Disabilitare le telecamere                               | In **built in Hardware > telecamere**selezionare **disabled**.                                       |
| Disabilitare Microfoni e altoparlanti              | In **built in Hardware > Microfoni e altoparlanti**selezionare **disabled**.                      |
| Disabilitare le radio (Bluetooth, Wi-Fi)             | In **built in Hardware > radio (Bluetooth, Wi-Fi, ecc**...) selezionare **disabled**.                   |
| Disabilitare l'avvio da elementi multimediali esterni (USB, SD)    | In **built in Hardware > opzioni di avvio > avvio da elementi multimediali esterni (USB, SD)**, selezionare **disabled**. |

> [!CAUTION]
> L'impostazione **Disattiva radio (Bluetooth, Wi-Fi)** deve essere usata solo nei dispositivi con connessione Ethernet cablata.
 
> [!NOTE]
>  DFCI in Intune include due impostazioni che attualmente non si applicano ai dispositivi Surface: (1) virtualizzazione di CPU e IO e (2) disabilitare l'avvio dalle schede di rete.
 
Intune include i tag di ambito per delegare diritti amministrativi e regole di applicabilità per gestire i tipi di dispositivo. Per altre informazioni sul supporto della gestione dei criteri e i dettagli completi su tutte le impostazioni di DFCI, vedere la [documentazione di Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows).

## Registrare i dispositivi in Autopilot

Come indicato sopra, DFCI può essere applicato solo ai dispositivi registrati in Windows Autopilot da un rivenditore o da un distributore ed è supportato solo in questo momento in Surface Pro 7, Surface Pro X e Surface laptop 3. Per motivi di sicurezza, non è possibile "eseguire il provisioning automatico" dei dispositivi in Autopilot.

## Sincronizzare manualmente i dispositivi Autopilot

Anche se le impostazioni dei criteri di Intune vengono in genere applicate quasi immediatamente, potrebbe essere previsto un ritardo di 10 minuti prima che le impostazioni abbiano effetto sui dispositivi mirati. In rari casi sono possibili ritardi fino a 8 ore. Per verificare che le impostazioni siano valide il più presto possibile, ad esempio in scenari di test, è possibile sincronizzare manualmente i dispositivi di destinazione.

- In Endpoint Manager su devicemanagement.microsoft.com accedere a **dispositivi > Registrazione dispositivi > registrazione di windows > dispositivi Autopilot Windows** e selezionare **Sincronizza**.

 Per altre informazioni, vedere [sincronizzare manualmente il dispositivo Windows](https://docs.microsoft.com/intune-user-help/sync-your-device-manually-windows).

> [!NOTE]
> Quando si regolano le impostazioni direttamente in UEFI, è necessario assicurarsi che il dispositivo ricominci completamente con l'accesso standard di Windows.

## Verifica delle impostazioni UEFI nei dispositivi gestiti da DFCI

In un ambiente di test puoi verificare le impostazioni nell'interfaccia UEFI di Surface.

1. Open Surface UEFI, che prevede la pressione simultanea dei pulsanti **volume +** e **Power** .
2. Selezionare **dispositivi**. Il menu UEFI rifletterà le impostazioni configurate, come illustrato nella figura seguente.

    ![UEFI di Surface](images/df3.png)

    Nota in che modo:

      - Le impostazioni sono in grigio perché **consentire agli utenti locali di modificare l'impostazione UEFI** è impostata su None.
      - L'audio è impostato su disattivato perché i **Microfoni e gli altoparlanti** sono impostati su **disabled**.

## Rimozione delle impostazioni dei criteri di DFCI

Quando crei un profilo DFCI, tutte le impostazioni configurate rimarranno in vigore in tutti i dispositivi all'interno dell'ambito di gestione del profilo. È possibile rimuovere solo le impostazioni dei criteri di DFCI modificando direttamente il profilo DFCI.

Se il profilo di DFCI originale è stato eliminato, è possibile rimuovere le impostazioni dei criteri creando un nuovo profilo e quindi modificando le impostazioni in base alle esigenze.

## Rimozione della gestione di DFCI

**Per rimuovere la gestione di DFCI e restituire il dispositivo allo stato Factory New:**

1. Ritirare il dispositivo da Intune:
    1. In Endpoint Manager in devicemanagement.microsoft.com scegliere **gruppi > tutti i dispositivi**. Selezionare i dispositivi che si desidera ritirare e quindi scegliere **ritira/Pulisci.** Per altre informazioni, vedere [rimuovere i dispositivi tramite wipe, ritirare o annullare la registrazione manuale del dispositivo](https://docs.microsoft.com/intune/remote-actions/devices-wipe). 
2. Eliminare la registrazione Autopilot da Intune:
    1.  Scegliere **registrazione dispositivo > dispositivi di registrazione > di Windows**.
    2. In dispositivi Autopilot Windows scegliere i dispositivi da eliminare e quindi scegliere **Elimina**.
3. Connettere il dispositivo a Internet cablato con la scheda Ethernet con marchio Surface. Riavviare il dispositivo e aprire il menu UEFI (tenere premuto il pulsante volume-up mentre si preme e si rilascia il pulsante di alimentazione).
4. Selezionare **gestione > configurare > aggiornamento dalla rete** e quindi scegliere **opt-out.**

Per conservare la gestione del dispositivo con Intune, ma senza la gestione di DFCI, è necessario registrare automaticamente il dispositivo per Autopilot e iscriverlo a Intune. DFCI non verrà applicato ai dispositivi auto-registrati.

## Scopri di più
- [Ignite 2019: annuncio della gestione remota delle impostazioni di Surface UEFI da Intune](https://techcommunity.microsoft.com/t5/Surface-IT-Pro-Blog/Ignite-2019-Announcing-remote-management-of-Surface-UEFI/ba-p/978333) 
 [Autopilot Windows](https://www.microsoft.com/microsoft-365/windows/windows-autopilot)
- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md) 
- [Usare i profili di DFCI nei dispositivi Windows in Microsoft Intune](https://docs.microsoft.com/intune/configuration/device-firmware-configuration-interface-windows)

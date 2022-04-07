---
title: Gestire le impostazioni UEFI di Surface
description: Usa le impostazioni UEFI di Surface per abilitare o disabilitare dispositivi o componenti, configurare impostazioni di sicurezza e modificare le impostazioni di avvio dei dispositivi Surface.
keywords: firmware, sicurezza, funzionalità, configurare, hardware
ms.localizationpriority: medium
ms.prod: w10
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: devices, surface
author: coveminer
ms.author: greglin
ms.topic: article
ms.reviewer: hachidan
manager: laurawi
ms.date: 04/01/2022
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: e38fb3ae8a25fddfcb64985a64b41d4d2e084178
ms.sourcegitcommit: b922aaf7287bdfb99f848aad455b2b4001b8f5be
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2022
ms.locfileid: "12472655"
---
# <a name="manage-surface-uefi-settings"></a>Gestire le impostazioni UEFI di Surface

 I dispositivi Surface PC sono progettati per usare un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft appositamente per questi dispositivi. Le impostazioni UEFI di Surface offrono la possibilità di abilitare o disabilitare i dispositivi e i componenti predefiniti, proteggere le impostazioni UEFI dalla modifica e regolare le impostazioni di avvio del dispositivo Surface.

## <a name="supported-products"></a>Prodotti supportati

La gestione UEFI è supportata nei modi seguenti:

- Surface Pro 4, Surface Pro (quinta generazione), Surface Pro 6, Surface Pro 7, Surface Pro 7+ (solo SKU commerciali), Surface Pro 8 (solo SKU commerciali), Surface Pro X
- Surface Laptop (prima generazione), Surface Laptop 2, Surface Laptop 3 (solo processori Intel), Surface Laptop Go, Surface Laptop 4 (solo SKU commerciali), Surface Laptop edizione Standard
- Surface Studio (prima generazione), Surface Studio 2
- Surface Book (tutte le generazioni)
- Surface Laptop Studio (solo SKU commerciali)
- Surface Go, Surface Go [21<sup></sup>](#references), Surface Go 3 (solo SKU commerciali)

>[!TIP]
> Gli SKU commerciali (noti anche come Surface per le aziende) eseguono Windows 10 Pro/Enterprise o Windows 11 Pro/Enterprise; gli SKU consumer eseguono Windows 10/Windows 11 Home. In UEFI, gli SKU commerciali sono gli unici modelli a presentare la [pagina Dispositivi](#uefi-devices-page) e la [pagina Gestione](#uefi-management-page). Per altre informazioni, vedi [Visualizzare le informazioni di sistema](https://support.microsoft.com/windows/view-your-system-info-a965a8f2-0773-1d65-472a-1e747c9ebe00). 


## <a name="support-for-cloud-based-management"></a>Supporto per la gestione basata sul cloud

Con i profili Device Firmware Configuration Interface (DFCI) incorporati in Microsoft Intune (ora disponibili in anteprima pubblica), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning senza tocco, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, incluse le opzioni di avvio e le periferiche predefinite, e pone le basi per scenari di sicurezza avanzati in futuro. DFCI è attualmente disponibile per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X. Per altre informazioni, vedere [Intune gestione delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

## <a name="open-surface-uefi-menu"></a>Aprire il menu UEFI di Surface

Per modificare le impostazioni UEFI durante l'avvio del sistema:

1. Arrestare Surface e attendere circa 10 secondi per assicurarsi che sia spento.
2. Tenere premuto il pulsante **Di aumento del volume** e, contemporaneamente, premere e rilasciare il **pulsante di alimentazione.**
3. Quando viene visualizzato il logo Microsoft o Surface sullo schermo, continuare a tenere premuto il pulsante **Volume-up** fino a quando non viene visualizzata la schermata UEFI.

## <a name="uefi-pc-information-page"></a>Pagina delle informazioni su UEFI PC

La pagina delle informazioni sul PC include informazioni dettagliate sul dispositivo Surface:

- **Modello**: il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7. Non viene visualizzata la configurazione esatta del dispositivo, ad esempio processore, dimensioni del disco o dimensioni della memoria.
- **UUID**: codice Universally Unique Identification specifico del dispositivo e usato per identificare il dispositivo durante la distribuzione o la gestione.

- **Numero di serie** : questo numero identifica questo dispositivo Surface specifico per gli scenari di assegnazione di tag e supporto degli asset.
- **Asset Tag**: tag asset assegnato al dispositivo Surface tramite [Asset Tag Tool](assettag.md).

Qui troverai anche informazioni dettagliate sul firmware del tuo dispositivo Surface. I dispositivi Surface hanno svariati componenti interni, ognuno dei quali esegue versioni diverse del firmware. La versione del firmware di ognuno dei dispositivi seguenti viene visualizzata nella pagina **PC information** (mostrata nella figura 1):

- UEFI di sistema

- Controller SAM

- Intel Management Engine

- Controller integrato di sistema

- Firmware per il tocco

:::image type="content" alt-text="Informazioni di sistema e informazioni sulla versione del firmware." source="images/manage-surface-uefi-figure-1.png":::

*Figura 1. Informazioni di sistema e informazioni sulla versione del firmware*

Puoi trovare informazioni aggiornate sulla versione più recente del firmware per il dispositivo Surface nella pagina [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) per il tuo dispositivo.

## <a name="uefi-security-page"></a>Pagina Sicurezza UEFI

:::image type="content" alt-text="Configurare le impostazioni di sicurezza UEFI di Surface." source="images/manage-surface-uefi-fig4.png":::

*Figura 2. Configurazione delle impostazioni di sicurezza UEFI di Surface*

La pagina Sicurezza consente di impostare una password per proteggere le impostazioni UEFI. Questa password deve essere immessa quando avvii il dispositivo Surface in UEFI. La password può contenere i caratteri seguenti (come illustrato nella figura 3):

- Lettere maiuscole: A-Z

- Lettere minuscole: a-z

- Numeri: 1-0

- Caratteri speciali: !@#$%^&*()?<>{}[]-_=+|.,;:''"

La password deve essere di almeno sei caratteri e fa distinzione tra maiuscole e minuscole.

![Aggiungere una password per proteggere le impostazioni UEFI di Surface.](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*Figura 3. Aggiunta di una password per proteggere le impostazioni UEFI di Surface*

Nella pagina Sicurezza è anche possibile modificare la configurazione di Avvio protetto nel dispositivo Surface. La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit. Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti. È anche possibile configurare l'avvio protetto per l'uso con certificati di terze parti, come illustrato nella figura 4. Per altre informazioni, vedere [Avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot).

![Configurare l'avvio protetto.](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*Figura 4. Configurazione di Avvio protetto*

A seconda del dispositivo, è anche possibile verificare se il TPM è abilitato o disabilitato. Se non viene visualizzata l'impostazione **Abilita TPM**, aprire tpm.msc in Windows per controllare lo stato, come illustrato nella figura 5. Il TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker. Per altre informazioni, vedere [Panoramica di BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview).

![Console TPM.](images/manage-surface-uefi-fig5-a.png "TPM console")

*Figura 5. Console TPM*

## <a name="uefi-devices-page"></a>Pagina Dispositivi UEFI

La pagina Dispositivi consente di abilitare o disabilitare componenti specifici nei dispositivi idonei, tra cui Surface Pro 8, Surface Go 3, Surface Laptop Studio, Surface Pro 7+, Surface Pro 7, Surface Pro X, Surface Laptop 4, Surface Laptop 3, Surface Laptop edizione Standard e Surface Book 3. I componenti sono costituiti dagli elementi seguenti:

- Ancoraggio della porta USB

- Slot per scheda microSD o SD

- Fotocamera posteriore

- Fotocamera anteriore

- Fotocamera a infrarossi

- Wi-Fi e Bluetooth

- Audio integrato (altoparlanti e microfono)

Ogni dispositivo è elencato con un pulsante di scorrimento che è possibile passare alla posizione **Attivato** (abilitato) o **Disattivato** (disabilitato), come illustrato nella figura 6.

:::image type="content" alt-text="Abilitare e disabilitare dispositivi specifici." source="images/manage-surface-uefi-fig5a.png":::

*Figura 6. Abilitazione e disabilitazione di dispositivi specifici*

## <a name="uefi-boot-configuration-page"></a>Pagina di configurazione dell'avvio UEFI

La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio, nonché di abilitare o disabilitare l'avvio dei dispositivi seguenti:

- Windows Boot Manager

- Archiviazione USB

- Rete PXE

- Archiviazione interna

È possibile eseguire immediatamente l'avvio da un dispositivo specifico o scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen. Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente.

Per rendere effettivo l'ordine di avvio specificato, è necessario impostare l'opzione **Abilita sequenza di avvio alternativo** **su Sì**, come illustrato nella figura 7.

:::image type="content" alt-text="Configurare l'ordine di avvio per il dispositivo Surface." source="images/manage-surface-uefi-fig6.png":::

*Figura 7. Configurazione dell'ordine di avvio per il dispositivo Surface*

È anche possibile attivare e disattivare il supporto IPv6 per PXE con l'opzione **Abilita IPv6 per L'avvio di rete PXE**, ad esempio quando si esegue una distribuzione Windows usando PXE in cui il server PXE è configurato solo per IPv4.  

## <a name="uefi-management-page"></a>Pagina Gestione UEFI

La pagina Gestione consente di gestire l'uso di Zero Touch UEFI Management e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 8, Surface Go 3, Surface Laptop Studio, Surface Pro 7+, Surface Pro 7, Surface Pro X, Surface Laptop 4, Surface Laptop 3, Surface Laptop edizione Standard e Surface Book 3. 

:::image type="content" alt-text="Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità." source="images/manage-surface-uefi-fig7a.png":::

*Figura 8. Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità*

Gestione UEFI Zero Touch consente di gestire in remoto le impostazioni UEFI usando un profilo di dispositivo all'interno di Intune denominato Device Firmware Configuration Interface (DFCI). Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **Pronto**. Per impedire DFCI, selezionare **Opt-Out**.

> [!NOTE]
> La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono attualmente disponibili per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X.  Per altre informazioni, vedere [Intune gestione delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

## <a name="uefi-exit-page"></a>Pagina di uscita UEFI

Usare il pulsante **Riavvia ora** nella pagina **Esci** per uscire dalle impostazioni UEFI, come illustrato nella figura 9.

:::image type="content" alt-text="Uscire da Surface UEFI e riavviare il dispositivo." source="images/manage-surface-uefi-fig7.png":::

*Figura 9. Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo*

## <a name="surface-uefi-boot-screens"></a>Schermate di avvio UEFI di Surface

Quando si aggiorna il firmware del dispositivo Surface usando Windows Update o l'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma durante il ciclo di riavvio successivo. Per altre informazioni sul processo di aggiornamento del firmware di Surface, vedere [Gestire e distribuire gli aggiornamenti del driver e del firmware di Surface](manage-surface-driver-and-firmware-updates.md). Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su una schermata con barre di stato di colori diversi per indicare il firmware per ogni componente. La barra di stato di ogni componente viene visualizzata nelle figure da 9 a 18.

![Aggiornamento del firmware UEFI di Surface con indicatore di stato blu.](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*Figura 10. L'aggiornamento del firmware UEFI di Surface visualizza una barra di stato blu*

![Firmware del controller incorporato di sistema con barra di stato verde.](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*Figura 11. L'aggiornamento del firmware del controller integrato di sistema visualizza una barra di stato verde*

![Aggiornamento del firmware del controller SAM con barra di stato arancione.](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*Figura 12. L'aggiornamento del firmware del controller SAM visualizza una barra di stato arancione*

![Firmware del motore di gestione Intel con barra di stato rossa.](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*Figura 13. L'aggiornamento del firmware Intel Management Engine visualizza una barra di stato rossa*

![Firmware surface touch con barra di stato grigia.](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*Figura 14. L'aggiornamento del firmware di Surface touch visualizza una barra di stato grigia*

![Firmware DI SURFACE KIP con indicatore di stato verde chiaro.](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*Figura 15. L'aggiornamento del firmware di Surface KIP visualizza un indicatore di stato verde chiaro*

![Firmware di Surface ISH con barra di stato rosa.](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*Figura 16 L'aggiornamento del firmware di Surface ISH visualizza un indicatore di stato rosa chiaro*

![Firmware di Surface Trackpad con barra di stato grigia.](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*Figura 17. L'aggiornamento del firmware di Surface Trackpad visualizza un indicatore di stato rosa*

![Firmware TCON surface con indicatore di stato grigio chiaro.](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*Figura 18. L'aggiornamento del firmware di Surface TCON visualizza un indicatore di stato grigio chiaro*

![Firmware TPM di Surface con indicatore di stato viola chiaro.](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*Figura 19. L'aggiornamento del firmware di Surface TPM visualizza un indicatore di stato viola*

>[!NOTE]
>Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio protetto è disabilitato, come illustrato nella figura 19.

![Schermata di avvio di Surface che indica che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*Figura 20. Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface*

## <a name="references"></a>Riferimenti

1. Surface Go e Surface Go 2 usano un UEFI di terze parti e non supportano DFCI. DFCI è attualmente disponibile per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X.

## <a name="related-topics"></a>Argomenti correlati

- [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)

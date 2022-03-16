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
ms.date: 01/18/2022
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 7da3a2908acc654abd86406af36eba4929bf4760
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449659"
---
# <a name="manage-surface-uefi-settings"></a>Gestire le impostazioni UEFI di Surface

 I dispositivi Surface PC sono progettati per utilizzare un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft appositamente per questi dispositivi. Le impostazioni UEFI di Surface consentono di abilitare o disabilitare i dispositivi e i componenti incorporati, proteggere le impostazioni UEFI dalle modifiche e modificare le impostazioni di avvio dei dispositivi Surface.

## <a name="supported-products"></a>Prodotti supportati

La gestione UEFI è supportata nei seguenti modi:

- Surface Pro 4, Surface Pro (5° generazione), Surface Pro 6, Surface Pro 7, Surface Pro 7+ (solo SKU commerciali), Surface Pro 8 (solo SKU commerciali), Surface Pro X
- Surface Laptop (prima generazione), Surface Laptop 2, Surface Laptop 3 (solo processori Intel), Surface Laptop Go, Surface Laptop 4 (solo SKU commerciali), Surface Laptop edizione Standard
- Surface Studio (prima generazione), Surface Studio 2
- Surface Book (tutte le generazioni)
- Surface Laptop Studio (solo SKU commerciali)
- Surface Go, Surface Go [21<sup></sup>](#references), Surface Go 3 (solo SKU commerciali)

>[!TIP]
> Le SKU commerciali (Surface per le aziende) vengono eseguite Windows 10 Pro/Enterprise o Windows 11 Pro/Enterprise; le SKU consumer vengono eseguite Windows 10/Windows 11 Home. Per altre informazioni, vedi [Visualizzare le informazioni di sistema](https://support.microsoft.com/windows/view-your-system-info-a965a8f2-0773-1d65-472a-1e747c9ebe00). 


## <a name="support-for-cloud-based-management"></a>Supporto per la gestione basata su cloud

Con i profili DFCI (Device Firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in anteprima pubblica), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning senza tocco, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, tra cui le opzioni di avvio e le periferiche incorporate, e costituisce le basi per scenari di sicurezza avanzati in futuro. DFCI è attualmente disponibile per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X.   Per altre informazioni, fai riferimento alla [gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

## <a name="open-surface-uefi-menu"></a>Apri il menu UEFI di Surface

Per modificare le impostazioni UEFI durante l'avvio del sistema:

1. Arresta Surface e attendi circa 10 secondi per assicurarti che sia spento.
2. Tenere premuto il **pulsante Volume-up** e, contemporaneamente, premere e rilasciare il **pulsante Di alimentazione.**
3. Man mano che sullo schermo viene visualizzato il logo Microsoft o Surface, continua a tenere premuto il pulsante **Volume-up** finché non viene visualizzata la schermata UEFI.

## <a name="uefi-pc-information-page"></a>Pagina informazioni PC UEFI

La pagina delle informazioni sul PC include informazioni dettagliate sul dispositivo Surface:

- **Modello**: il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7. L'esatta configurazione del dispositivo non viene visualizzata, ad esempio processore, dimensioni dei dischi o dimensioni della memoria.
- **UUID**: codice Universally Unique Identification specifico del dispositivo e usato per identificare il dispositivo durante la distribuzione o la gestione.

- **Serial Number**: numero usato per identificare questo dispositivo Surface specifico per gli scenari di tag asset e supporto.
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

- Caratteri speciali: !@#$%^&*()?<>{}[]-_=+|.,;:'""

La password deve contenere almeno sei caratteri e fa distinzione tra maiuscole e minuscole.

![Aggiungi una password per proteggere le impostazioni UEFI di Surface.](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*Figura 3. Aggiunta di una password per proteggere le impostazioni UEFI di Surface*

Nella pagina Security puoi anche modificare la configurazione di Avvio protetto nel tuo dispositivo Surface. La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit. Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti. È inoltre possibile configurare l'avvio protetto per l'utilizzo con certificati di terze parti, come illustrato nella figura 4. Per ulteriori informazioni, vedere [Avvio protetto](/windows-hardware/design/device-experiences/oem-secure-boot).

![Configurare l'avvio protetto.](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*Figura 4. Configurazione di Avvio protetto*

A seconda del dispositivo, potresti anche essere in grado di vedere se il TPM è abilitato o disabilitato. Se non viene visualizzata l'impostazione **Abilita TPM**, aprire tpm.msc in Windows per verificare lo stato, come illustrato nella figura 5. Il dispositivo TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker. Per altre informazioni, vedi Panoramica [di BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview).

![Console TPM.](images/manage-surface-uefi-fig5-a.png "TPM console")

*Figura 5. Console TPM*

## <a name="uefi-menu-devices"></a>Menu UEFI: dispositivi

La pagina Dispositivi consente di abilitare o disabilitare dispositivi e componenti specifici, tra cui:

- Porta USB di ancoraggio

- Slot per scheda microSD o SD

- Fotocamera posteriore

- Fotocamera anteriore

- Fotocamera a infrarossi

- Wi-Fi e Bluetooth

- Audio integrato (altoparlanti e microfono)

Ogni dispositivo è elencato con un pulsante del dispositivo di scorrimento che puoi spostare nella posizione **Attivato (abilitato** ) o **Disattivato** (disabilitato), come illustrato nella figura 6.

:::image type="content" alt-text="Abilitare e disabilitare dispositivi specifici." source="images/manage-surface-uefi-fig5a.png":::

*Figura 6. Abilitazione e disabilitazione di dispositivi specifici*

## <a name="uefi-menu-boot-configuration"></a>Menu UEFI: Configurazione di avvio

La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio, nonché di abilitare o disabilitare l'avvio dei dispositivi seguenti:

- Windows Boot Manager

- Archiviazione USB

- Rete PXE

- Archiviazione interna

Puoi eseguire l'avvio da un dispositivo specifico immediatamente oppure puoi scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen. Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente.

Per attivare l'ordine di avvio specificato, è necessario impostare l'opzione **Abilita sequenza di avvio alternativa** su **Attivato**, come illustrato nella figura 7.

:::image type="content" alt-text="Configura l'ordine di avvio per il dispositivo Surface." source="images/manage-surface-uefi-fig6.png":::

*Figura 7. Configurazione dell'ordine di avvio per il dispositivo Surface*

Poi anche attivare o disattivare il supporto IPv6 per PXE con l'opzione **Enable IPv6 for PXE Network Boot**, ad esempio quando esegui una distribuzione di Windows con PXE in cui il server PXE è configurato solo per IPv4.  

## <a name="uefi-menu-management"></a>Menu UEFI: Gestione

La pagina Gestione consente di gestire l'uso della gestione UEFI Zero Touch e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 8, Surface Go 3, Surface Laptop Studio, Surface Pro 7+, Surface Pro 7, Surface Pro X, Surface Laptop 4 , Surface Laptop 3, Surface Laptop edizione Standard e Surface Book 3. 

:::image type="content" alt-text="Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità." source="images/manage-surface-uefi-fig7a.png":::

*Figura 8. Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità*

Zero Touch UEFI Management consente di gestire in remoto le impostazioni UEFI usando un profilo del dispositivo in Intune denominato Device Firmware Configuration Interface (DFCI). Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **Pronto**. Per impedire la DFCI, seleziona **Rifiuta esplicitamente**.

> [!NOTE]
> La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono attualmente disponibili per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X.  Per altre informazioni, vedi [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md).

## <a name="uefi-menu-exit"></a>Menu UEFI: Esci

Utilizzare il **pulsante Riavvia** ora nella **pagina Esci** per uscire da impostazioni UEFI, come illustrato nella figura 9.

:::image type="content" alt-text="Esci da Surface UEFI e riavvia il dispositivo." source="images/manage-surface-uefi-fig7.png":::

*Figura 9. Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo*

## <a name="surface-uefi-boot-screens"></a>Schermate di avvio UEFI di Surface

Quando aggiorni il firmware del dispositivo Surface, tramite Windows Update o un'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma al successivo ciclo di riavvio. Per altre informazioni sul processo di aggiornamento del firmware di Surface, vedere [Gestire e distribuire gli aggiornamenti di driver e firmware di Surface](manage-surface-driver-and-firmware-updates.md). Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su uno schermo con barre di stato di colori diversi per indicare il firmware di ogni componente. L'indicatore di stato di ogni componente viene visualizzato nelle figure da 9 a 18.

![Aggiornamento del firmware UEFI di Surface con barra di avanzamento blu.](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*Figura 10. L'aggiornamento del firmware UEFI di Surface visualizza una barra di stato blu*

![Firmware del controller incorporato di sistema con barra di avanzamento verde.](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*Figura 11. L'aggiornamento del firmware del controller integrato di sistema visualizza una barra di stato verde*

![Aggiornamento del firmware del controller SAM con indicatore di stato arancione.](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*Figura 12. L'aggiornamento del firmware del controller SAM visualizza una barra di stato arancione*

![Firmware del motore di gestione Intel con barra di avanzamento rossa.](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*Figura 13. L'aggiornamento del firmware Intel Management Engine visualizza una barra di stato rossa*

![Firmware surface touch con indicatore di stato grigio.](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*Figura 14. L'aggiornamento del firmware di Surface touch visualizza una barra di stato grigia*

![Firmware Surface KIP con indicatore di stato verde chiaro.](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*Figura 15. L'aggiornamento del firmware di Surface KIP visualizza un indicatore di stato verde chiaro*

![Firmware ISH surface con barra di avanzamento rosa.](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*Figura 16 L'aggiornamento del firmware ISH di Surface visualizza un indicatore di stato rosa chiaro*

![Firmware Surface Trackpad con indicatore di stato grigio.](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*Figura 17. L'aggiornamento del firmware di Surface Trackpad visualizza un indicatore di stato rosa*

![Firmware Surface TCON con indicatore di stato grigio chiaro.](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*Figura 18. L'aggiornamento del firmware TCON di Surface visualizza un indicatore di stato grigio chiaro*

![Firmware TPM surface con indicatore di stato viola chiaro.](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*Figura 19. L'aggiornamento del firmware TPM di Surface visualizza un indicatore di stato viola*

>[!NOTE]
>Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio protetto è disabilitato, come illustrato nella figura 19.

![Schermata di avvio di Surface che indica che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*Figura 20. Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface*

## <a name="references"></a>Riferimenti

1. Surface Go e Surface Go 2 usano un UEFI di terze parti e non supportano DFCI. DFCI è attualmente disponibile per Surface Laptop edizione Standard, Surface Laptop Studio, Surface Pro 8, Surface Go 3, Surface Laptop 4, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7+, Surface Pro 7 e Surface Pro X.

## <a name="related-topics"></a>Argomenti correlati

- [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)

- [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)

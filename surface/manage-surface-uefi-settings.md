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
ms.date: 04/13/2021
ms.openlocfilehash: ea995eda277ecf235eedd92f3af6edb0b60ae68a
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576506"
---
# <a name="manage-surface-uefi-settings"></a>Gestire le impostazioni UEFI di Surface

 I dispositivi Surface PC sono progettati per utilizzare un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft in modo specifico per questi dispositivi. Le impostazioni UEFI di Surface consentono di abilitare o disabilitare i dispositivi e i componenti incorporati, proteggere le impostazioni UEFI dalle modifiche e modificare le impostazioni di avvio dei dispositivi Surface. 

## <a name="supported-products"></a>Prodotti supportati

La gestione UEFI è supportata nei seguenti modi: 

- Surface Pro 4, Surface Pro (5° generazione), Surface Pro 6, Surface Pro 7, Surface Pro 7+, Surface Pro X
- Surface Laptop (prima generazione), Surface Laptop 2, Surface Laptop 3, Surface Laptop Go, Surface Laptop 4
- Surface Studio (prima generazione), Surface Studio 2
- Surface Book, Surface Book 2, Surface Book 3
- Surface Go, Surface Go 2[ <sup> 1 </sup> ](#references)

## <a name="support-for-cloud-based-management"></a>Supporto per la gestione basata su cloud

Con i profili DFCI (Device Firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in anteprima pubblica), la gestione UEFI di Surface estende lo stack di gestione moderno fino al livello hardware UEFI. DFCI supporta il provisioning a tocco zero, elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, tra cui le opzioni di avvio e le periferiche incorporate, e costituisce le basi per scenari di sicurezza avanzati in futuro. DFCI è attualmente disponibile per Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 3, Surface Pro 7 e Surface Pro X.  Per altre informazioni, fai riferimento alla [gestione di Intune delle impostazioni UEFI di Surface.](surface-manage-dfci-guide.md)

## <a name="open-surface-uefi-menu"></a>Apri il menu UEFI di Surface

Per modificare le impostazioni UEFI durante l'avvio del sistema:

1. Arresta Surface e attendi circa 10 secondi per assicurarti che sia spento.
2. Tenere premuto il **pulsante Volume-up** e, contemporaneamente, premere e rilasciare il **pulsante Di alimentazione.**
3. Man mano che sullo schermo viene visualizzato il logo Microsoft o Surface, continua a tenere premuto il pulsante **Volume-up** finché non viene visualizzata la schermata UEFI.

## <a name="uefi-pc-information-page"></a>Pagina informazioni PC UEFI

La pagina delle informazioni sul PC include informazioni dettagliate sul dispositivo Surface: 

- **Modello:** il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7. L'esatta configurazione del dispositivo non viene visualizzata, ad esempio processore, dimensioni dei dischi o dimensioni della memoria. 
- **UUID**: codice Universally Unique Identification specifico del dispositivo e usato per identificare il dispositivo durante la distribuzione o la gestione. 

- **Serial Number**: numero usato per identificare questo dispositivo Surface specifico per gli scenari di tag asset e supporto.
- **Asset Tag**: tag asset assegnato al dispositivo Surface tramite [Asset Tag Tool](https://docs.microsoft.com/surface/assettag). 

Qui troverai anche informazioni dettagliate sul firmware del tuo dispositivo Surface. I dispositivi Surface hanno svariati componenti interni, ognuno dei quali esegue versioni diverse del firmware. La versione del firmware di ognuno dei dispositivi seguenti viene visualizzata nella pagina **PC information** (mostrata nella figura 1): 

- UEFI di sistema 

- Controller SAM 

- Intel Management Engine 

- Controller integrato di sistema 

- Firmware per il tocco 

![Informazioni di sistema e informazioni sulla versione del firmware](images/manage-surface-uefi-figure-1.png "System information and firmware version information")

*Figura 1. Informazioni di sistema e informazioni sulla versione del firmware*

Puoi trovare informazioni aggiornate sulla versione più recente del firmware per il dispositivo Surface nella pagina [Surface Update History](https://www.microsoft.com/surface/support/install-update-activate/surface-update-history) per il tuo dispositivo. 

## <a name="uefi-security-page"></a>Pagina Sicurezza UEFI 

![Configurazione delle impostazioni di sicurezza UEFI di Surface](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*Figura 2. Configurazione delle impostazioni di sicurezza UEFI di Surface*

La pagina Sicurezza consente di impostare una password per proteggere le impostazioni UEFI. Questa password deve essere immessa quando avvii il dispositivo Surface in UEFI. La password può contenere i caratteri seguenti (come illustrato nella figura 3): 

- Lettere maiuscole: A-Z 

- Lettere minuscole: a-z 

- Numeri: 1-0 

- Caratteri speciali: !@#$%^&*()?<>{} []-_=+|.,;:'"" 

La password deve contenere almeno 6 caratteri e fa distinzione tra maiuscole e minuscole. 

![Aggiunta di una password per proteggere le impostazioni UEFI di Surface](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*Figura 3. Aggiunta di una password per proteggere le impostazioni UEFI di Surface*

Nella pagina Security puoi anche modificare la configurazione di Avvio protetto nel tuo dispositivo Surface. La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit. Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti. È inoltre possibile configurare l'avvio protetto per l'utilizzo con certificati di terze parti, come illustrato nella figura 4. Per altre informazioni, vedi [Avvio protetto](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) nella Libreria TechNet.

![Configurazione di Avvio protetto](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*Figura 4. Configurazione di Avvio protetto*

A seconda del dispositivo, potresti anche essere in grado di vedere se il TPM è abilitato o disabilitato. Se non viene visualizzata l'impostazione **Abilita TPM,** aprire tpm.msc in Windows per verificare lo stato, come illustrato nella figura 5. Il dispositivo TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker. Per ulteriori informazioni, vedere [BitLocker panoramica.](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview) 

![Console TPM](images/manage-surface-uefi-fig5-a.png "TPM console")

*Figura 5. Console TPM*


## <a name="uefi-menu-devices"></a>Menu UEFI: dispositivi 

La pagina Dispositivi consente di abilitare o disabilitare dispositivi e componenti specifici, tra cui:

- Alloggiamento di espansione e porte USB 

- Slot per scheda microSD o SD 

- Fotocamera posteriore 

- Fotocamera anteriore 

- Fotocamera a infrarossi 

- Wi-Fi e Bluetooth 

- Audio integrato (altoparlanti e microfono) 

Ogni dispositivo è elencato con un pulsante del dispositivo di scorrimento che puoi spostare nella posizione **Attivato** (abilitato) o **Disattivato** (disabilitato), come illustrato nella figura 6. 

![Abilitazione e disabilitazione di dispositivi specifici](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*Figura 6. Abilitazione e disabilitazione di dispositivi specifici*

## <a name="uefi-menu-boot-configuration"></a>Menu UEFI: Configurazione di avvio 

La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio, nonché di abilitare o disabilitare l'avvio dei dispositivi seguenti: 

- Windows Boot Manager 

- Archiviazione USB 

- Rete PXE 

- Archiviazione interna 

Puoi eseguire l'avvio da un dispositivo specifico immediatamente oppure puoi scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen. Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente. 

Per fare in modo che l'ordine di avvio specificato sia attivo, è necessario impostare l'opzione **Abilita sequenza di** avvio alternativa su **On,** come illustrato nella figura 7. 

![Configurazione dell'ordine di avvio per il dispositivo Surface](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*Figura 7. Configurazione dell'ordine di avvio per il dispositivo Surface* 

Poi anche attivare o disattivare il supporto IPv6 per PXE con l'opzione **Enable IPv6 for PXE Network Boot**, ad esempio quando esegui una distribuzione di Windows con PXE in cui il server PXE è configurato solo per IPv4.  

## <a name="uefi-menu-management"></a>Menu UEFI: Gestione
La pagina Gestione consente di gestire l'uso di Zero Touch UEFI Management e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 7, Surface Pro X e Surface Laptop 3.  

![Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *figura 8. Gestire l'accesso a Zero Touch UEFI Management e ad altre funzionalità* 


Zero Touch UEFI Management consente di gestire in remoto le impostazioni UEFI usando un profilo del dispositivo in Intune denominato Device Firmware Configuration Interface (DFCI). Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **Pronto.** Per impedire la DFCI, selezionare **Rifiuta.** 

> [!NOTE]
> La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono attualmente disponibili per Surface Pro 7+, Surface Laptop Go, Surface Book 3, Surface Laptop 4, Surface Laptop 3, Surface Pro 7 e Surface Pro X. Per altre informazioni, vedi [Gestione di Intune delle impostazioni UEFI di Surface.](surface-manage-dfci-guide.md)

## <a name="uefi-menu-exit"></a>Menu UEFI: Esci 

Utilizzare il **pulsante Riavvia** ora nella **pagina Esci** per uscire da impostazioni UEFI, come illustrato nella figura 9. 

![Chiusura delle impostazioni UEFI di Surface e riavvio del dispositivo](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*Figura 9. Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo*

## <a name="surface-uefi-boot-screens"></a>Schermate di avvio UEFI di Surface

Quando aggiorni il firmware del dispositivo Surface, tramite Windows Update o un'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma al successivo ciclo di riavvio. Per altre informazioni sul processo di aggiornamento del firmware di Surface, vedere Gestire e distribuire gli aggiornamenti di driver e [firmware di Surface.](manage-surface-driver-and-firmware-updates.md) Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su uno schermo con barre di stato di colori diversi per indicare il firmware di ogni componente. L'indicatore di stato di ogni componente viene visualizzato nelle figure da 9 a 18.

![Aggiornamento del firmware UEFI di Surface con barra di stato blu](images/manage-surface-uefi-fig8.png "Surface UEFI firmware update with blue progress bar")

*Figura 10. L'aggiornamento del firmware UEFI di Surface visualizza una barra di stato blu*

![Firmware del controller integrato di sistema con la barra di stato verde](images/manage-surface-uefi-fig9.png "System Embedded Controller firmware with green progress bar")

*Figura 11. L'aggiornamento del firmware del controller integrato di sistema visualizza una barra di stato verde*

![Aggiornamento del firmware del controller SAM con barra di stato arancione](images/manage-surface-uefi-fig10.png "SAM Controller firmware update with orange progress bar")

*Figura 12. L'aggiornamento del firmware del controller SAM visualizza una barra di stato arancione*

![Firmware Intel Management Engine con barra di stato rosso](images/manage-surface-uefi-fig11.png "Intel Management Engine firmware with red progress bar")

*Figura 13. L'aggiornamento del firmware Intel Management Engine visualizza una barra di stato rossa*

![Firmware di Surface touch con barra di stato grigia](images/manage-surface-uefi-fig12.png "Surface touch firmware with gray progress bar")

*Figura 14. L'aggiornamento del firmware di Surface touch visualizza una barra di stato grigia*

![Firmware Surface KIP con indicatore di stato verde chiaro](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*Figura 15. L'aggiornamento del firmware di Surface KIP visualizza un indicatore di stato verde chiaro*

![Firmware ISH surface con barra di avanzamento rosa](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*Figura 16 L'aggiornamento del firmware ISH di Surface visualizza un indicatore di stato rosa chiaro*

![Firmware Surface Trackpad con indicatore di stato grigio](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*Figura 17. L'aggiornamento del firmware di Surface Trackpad visualizza un indicatore di stato rosa*

![Firmware Surface TCON con indicatore di stato grigio chiaro](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*Figura 18. L'aggiornamento del firmware TCON di Surface visualizza un indicatore di stato grigio chiaro*


![Firmware TPM surface con indicatore di stato viola chiaro](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*Figura 19. L'aggiornamento del firmware TPM di Surface visualizza un indicatore di stato viola*


>[!NOTE]
>Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio protetto è disabilitato, come illustrato nella figura 19.

![Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*Figura 20. Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface*

## <a name="references"></a>Riferimenti

1. Surface Go e Surface Go 2 usano un UEFI di terze parti e non supportano DFCI. 

## <a name="related-topics"></a>Argomenti correlati

- [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)

-  [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)

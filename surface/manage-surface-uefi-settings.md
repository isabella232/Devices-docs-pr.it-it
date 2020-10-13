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
ms.date: 10/12/2020
ms.openlocfilehash: 218f98b23adcb7bae2af92655d85144c6e5665e6
ms.sourcegitcommit: c1efb75e8524193bdc0a5f7496dc23a92ac665c8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2020
ms.locfileid: "11114724"
---
# Gestire le impostazioni UEFI di Surface

Tutte le generazioni correnti e future dei dispositivi Surface usano un'interfaccia UEFI (Unified Extensible Firmware Interface) univoca progettata da Microsoft in modo specifico per questi dispositivi. Le impostazioni di Surface UEFI offrono la possibilità di abilitare o disabilitare dispositivi e componenti incorporati, proteggere le impostazioni UEFI e modificare le impostazioni di avvio del dispositivo Surface. 

## Prodotti supportati

La gestione UEFI è supportata nelle operazioni seguenti: 

- Surface Pro 4, Surface Pro (5a gen), Surface Pro 6, Surface Pro 7, Surface Pro X
- Superficie portatile (1a Gen), Surface laptop 2, Surface laptop 3, Surface laptop go
- Surface Studio (1a generazione), Surface Studio 2
- Surface Book, Surface Book 2, Surface Book 3
- Superficie andare, superficie andare 2

## Supporto per la gestione basata sul cloud

Con i profili di DFCI (device firmware Configuration Interface) incorporati in Microsoft Intune (ora disponibile in anteprima pubblica), Surface UEFI Management estende il moderno stack di gestione fino al livello hardware UEFI. DFCI supporta il provisioning a zero tocco, Elimina le password del BIOS, fornisce il controllo delle impostazioni di sicurezza, incluse le opzioni di avvio e le periferiche predefinite, e stabilisce le basi per scenari di sicurezza avanzati in futuro. DFCI è attualmente disponibile per Surface Pro 7, Surface Pro X e Surface laptop 3. Per altre informazioni, vedere [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md).

## Menu open Surface UEFI

Per regolare le impostazioni UEFI durante l'avvio del sistema:

1. Chiudere la superficie e attendere circa 10 secondi per verificare che sia disattivata.
2. Premere e tenere premuto il pulsante **volume-up** e-allo stesso tempo-premere e rilasciare il **pulsante di accensione.**
3. Quando sullo schermo compare il logo Microsoft o Surface, continuare a tenere premuto il pulsante **volume-up** finché non viene visualizzata la schermata UEFI.

## Pagina informazioni PC UEFI

La pagina informazioni PC include informazioni dettagliate sul dispositivo Surface: 

- **Modello** : il modello del dispositivo Surface verrà visualizzato qui, ad esempio Surface Book 2 o Surface Pro 7. L'esatta configurazione del dispositivo non viene visualizzata, ad esempio processore, dimensioni dei dischi o dimensioni della memoria. 
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

## Pagina sicurezza UEFI 

![Configurazione delle impostazioni di sicurezza UEFI di Surface](images/manage-surface-uefi-fig4.png "Configure Surface UEFI security settings")

*Figura 2. Configurazione delle impostazioni di sicurezza UEFI di Surface*

La pagina sicurezza consente di impostare una password per la protezione delle impostazioni UEFI. Questa password deve essere immessa quando avvii il dispositivo Surface in UEFI. La password può contenere i caratteri seguenti (come illustrato nella figura 3): 

- Lettere maiuscole: A-Z 

- Lettere minuscole: a-z 

- Numeri: 1-0 

- Caratteri speciali:! @ # $% ^& * ()? <>{} []-_ = + |.,;:'' " 

La password deve contenere almeno 6 caratteri e fa distinzione tra maiuscole e minuscole. 

![Aggiunta di una password per proteggere le impostazioni UEFI di Surface](images/manage-surface-uefi-fig2.png "Add a password to protect Surface UEFI settings")

*Figura 3. Aggiunta di una password per proteggere le impostazioni UEFI di Surface*

Nella pagina Security puoi anche modificare la configurazione di Avvio protetto nel tuo dispositivo Surface. La tecnologia Avvio protetto impedisce l'avvio di un codice di avvio non autorizzato nel dispositivo Surface, per proteggere il sistema da infezioni malware di tipo bootkit e rootkit. Puoi disabilitare Avvio protetto per permettere al dispositivo Surface di avviare sistemi operativi o supporti di avvio di terze parti. È anche possibile configurare l'avvio sicuro per l'utilizzo con certificati di terze parti, come illustrato nella figura 4. Per altre informazioni, vedi [Avvio protetto](https://msdn.microsoft.com/windows/hardware/commercialize/manufacture/desktop/secure-boot-overview) nella Libreria TechNet.

![Configurazione di Avvio protetto](images/manage-surface-uefi-fig3.png "Configure Secure Boot")

*Figura 4. Configurazione di Avvio protetto*

A seconda del dispositivo, potrebbe essere anche possibile verificare se il TPM è abilitato o disabilitato. Se l'impostazione **Abilita TPM**  non è visibile, aprire TPM. msc in Windows per verificare lo stato, come illustrato nella figura 5. Il dispositivo TPM viene usato per autenticare la crittografia per i dati del dispositivo con BitLocker. Per altre informazioni, vedere [Cenni preliminari su BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview). 

![Console TPM](images/manage-surface-uefi-fig5-a.png "TPM console")

*Figura 5. Console TPM*


## Menu UEFI: dispositivi 

La pagina dispositivi consente di abilitare o disabilitare dispositivi e componenti specifici, tra cui:

- Alloggiamento di espansione e porte USB 

- Slot per scheda microSD o SD 

- Fotocamera posteriore 

- Fotocamera anteriore 

- Fotocamera a infrarossi 

- Wi-Fi e Bluetooth 

- Audio integrato (altoparlanti e microfono) 

Ogni dispositivo è elencato con un **pulsante di scorrimento che consente di spostare** la posizione **attivato (abilitato) o disattivato** (disabilitato), come illustrato nella figura 6. 

![Abilitazione e disabilitazione di dispositivi specifici](images/manage-surface-uefi-fig5a.png "Enable and disable specific devices")

*Figura 6. Abilitazione e disabilitazione di dispositivi specifici*

## Menu UEFI: configurazione di avvio 

La pagina Configurazione di avvio consente di modificare l'ordine dei dispositivi di avvio e di abilitare o disabilitare l'avvio dei dispositivi seguenti: 

- Windows Boot Manager 

- Archiviazione USB 

- Rete PXE 

- Archiviazione interna 

Puoi eseguire l'avvio da un dispositivo specifico immediatamente oppure puoi scorrere rapidamente verso sinistra sulla voce del dispositivo nell'elenco usando il touchscreen. Puoi anche eseguire l'avvio immediatamente da un dispositivo USB o da una scheda Ethernet USB quando il dispositivo Surface è spento premendo il pulsante di **riduzione del volume** e quello di **accensione** simultaneamente. 

Per rendere effettivo l'ordine di avvio specificato, è necessario impostare l'opzione **Attiva sequenza di avvio alternativo** **su**attivato, come illustrato nella figura 7. 

![Configurazione dell'ordine di avvio per il dispositivo Surface](images/manage-surface-uefi-fig6.png "Configure the boot order for your Surface device")

*Figura 7. Configurazione dell'ordine di avvio per il dispositivo Surface* 

Poi anche attivare o disattivare il supporto IPv6 per PXE con l'opzione **Enable IPv6 for PXE Network Boot**, ad esempio quando esegui una distribuzione di Windows con PXE in cui il server PXE è configurato solo per IPv4.  

## Menu UEFI: gestione
La pagina di gestione consente di gestire l'uso della gestione delle funzioni di zero touch UEFI e di altre funzionalità nei dispositivi idonei, tra cui Surface Pro 7, Surface Pro X e Surface laptop 3.  

![Gestire l'accesso alla gestione di zero touch UEFI e ad altre caratteristiche ](images/manage-surface-uefi-fig7a.png "Manage access to Zero Touch UEFI Management and other features")
 *Figura 8. Gestire l'accesso alla gestione di zero touch UEFI e ad altre caratteristiche* 


Zero Touch UEFI Management consente di gestire in remoto le impostazioni UEFI usando un profilo di dispositivo all'interno di Intune denominato device firmware Configuration Interface (DFCI). Se non si configura questa impostazione, la possibilità di gestire i dispositivi idonei con DFCI è impostata su **pronto**. Per evitare DFCI, selezionare **opt-out**. 

> [!NOTE]
> La pagina delle impostazioni di gestione UEFI e l'uso di DFCI sono disponibili solo in Surface Pro 7, Surface Pro X e Surface laptop 3.  

Per altre informazioni, vedere [gestione di Intune delle impostazioni di Surface UEFI](surface-manage-dfci-guide.md).

## Menu UEFI: Esci 

Usare il pulsante **Riavvia ora** nella pagina **Esci** per uscire dalle impostazioni di UEFI, come illustrato nella figura 9. 

![Chiusura delle impostazioni UEFI di Surface e riavvio del dispositivo](images/manage-surface-uefi-fig7.png "Exit Surface UEFI and restart the device")

*Figura 9. Fai clic su Riavvia ora per uscire dalle impostazioni UEFI di Surface e riavviare il dispositivo*

## Schermate di avvio UEFI di Surface

Quando aggiorni il firmware del dispositivo Surface, tramite Windows Update o un'installazione manuale, gli aggiornamenti non vengono applicati immediatamente al dispositivo, ma al successivo ciclo di riavvio. Puoi trovare ulteriori informazioni sul processo di aggiornamento del firmware di Surface in [Gestire gli aggiornamenti di driver e firmware Surface](https://docs.microsoft.com/surface/manage-surface-pro-3-firmware-updates). Lo stato di avanzamento dell'aggiornamento del firmware viene visualizzato su uno schermo con barre di stato di colori diversi per indicare il firmware di ogni componente. La barra di stato di ogni componente viene visualizzata nelle figure da 9 a 18.

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

![Firmware di Surface KIP con barra di avanzamento verde chiaro](images/manage-surface-uefi-fig13.png "Surface touch firmware with light green progress bar")

*Figura 15. L'aggiornamento del firmware di Surface KIP Visualizza una barra di stato verde chiaro*

![Superficie del firmware ISH con barra di avanzamento rosa](images/manage-surface-uefi-fig14.png "Surface ISH firmware with pink progress bar")

*Figura 16 la superficie dell'aggiornamento del firmware ISH Mostra una barra di avanzamento rosa chiaro*

![Firmware Surface trackpad con barra di avanzamento grigio](images/manage-surface-uefi-fig15.png "Surface Trackpad firmware with gray progress bar")

*Figura 17. L'aggiornamento del firmware Surface trackpad Visualizza una barra di stato rosa*

![Firmware Surface TCON con indicatore di stato grigio chiaro](images/manage-surface-uefi-fig16.png "Surface TCON firmware with light gray progress bar")

*Figura 18. L'aggiornamento del firmware Surface TCON Visualizza una barra di stato grigio chiaro*


![Firmware di Surface TPM con indicatore di stato viola chiaro](images/manage-surface-uefi-fig17.png "Surface TPM firmware with purple progress bar")

*Figura 19. L'aggiornamento del firmware Surface TPM Visualizza una barra di stato viola*


>[!NOTE]
>Viene visualizzato un messaggio di avviso aggiuntivo che indica che l'avvio sicuro è disabilitato, come illustrato nella figura 19.

![Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato.](images/manage-surface-uefi-fig18.png "Surface boot screen that indicates Secure Boot has been disabled")

*Figura 20. Schermata di avvio di Surface indicante che l'avvio protetto è stato disabilitato nelle impostazioni UEFI di Surface*

## Argomenti correlati

- [Gestione di Intune delle impostazioni UEFI di Surface](surface-manage-dfci-guide.md)

-  [Surface Enterprise Management Mode](surface-enterprise-management-mode.md)

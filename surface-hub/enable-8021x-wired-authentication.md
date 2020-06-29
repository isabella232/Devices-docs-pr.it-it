---
title: Abilitare l'autenticazione cablata 802.1x
description: I criteri MDM per l'autenticazione cablata 802.1x sono stati abilitati nei dispositivi Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 11/15/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: 119f879d74ccda5d53da27d842413346a50693f1
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833705"
---
# Abilita autenticazione cablata 802.1x

Il [14 novembre 2017 l'aggiornamento a Windows 10](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (build 15063.726) abilita i criteri MDM per l'autenticazione cablata 802.1x sui dispositivi Surface Hub. La funzionalità consente alle organizzazioni di applicare l'autenticazione di rete cablata standardizzata tramite il [protocollo di autenticazione IEEE 802.1x](http://www.ieee802.org/1/pages/802.1x-2010.html). Questo è già disponibile per l'autenticazione wireless con i profili WLAN tramite MDM. In questo argomento viene illustrato come configurare un dispositivo Surface Hub per l'utilizzo con l'autenticazione cablata. 

L'imposizione e l'abilitazione dell'autenticazione cablata 802.1x su dispositivi Surface Hub possono essere eseguite tramite MDM [definizione OMA-URI](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings). 

La configurazione primaria da impostare è il criterio **LanProfile**. A seconda del metodo di autenticazione selezionato, altri criteri potrebbero essere necessari, il criterio **EapUserData** o i criteri MDM per l'aggiunta di certificati utente o del computer (ad esempio [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) per certificati utente/dispositivo o [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) per certificati dispositivo). 

## Elemento dei criteri LanProfile

Per configurare Surface Hub per l'utilizzo di uno dei metodi di autenticazione 802.1x supportati, utilizza il seguente OMA-URI. 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

Questo nodo OMA-URI accetta una stringa di testo XML come parametro. L'XML fornito come parametro deve essere conforme allo [schema del profilo rete LAN cablata](https://msdn.microsoft.com/library/cc233002.aspx) inclusi gli elementi dello [schema 802.1X](https://msdn.microsoft.com/library/cc233003.aspx). 

Nella maggior parte dei casi, un amministratore o un utente può esportare l'XML LanProfile da un PC esistente che è già configurato nella rete per 802.1X con il comando NETSH seguente. 

```
netsh lan export profile folder=.
```

L'esecuzione di questo comando darà il risultato seguente e posizionerà un file denominato **Ethernet.xml** nella directory corrente. 

```
Interface: Ethernet
Profile File Name: .\Ethernet.xml
1 profile(s) were exported successfully.
```

## Elemento dei criteri EapUserData

Se il metodo di autenticazione selezionato richiede un nome utente e una password anziché un certificato, puoi utilizzare l'elemento **EapUserData** per specificare le credenziali per il dispositivo da utilizzare per eseguire l'autenticazione in rete. 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

Questo nodo OMA-URI accetta una stringa di testo XML come parametro. L'XML fornito come parametro deve essere conforme all'[esempio Proprietà dell'utente MS-CHAPv2 PEAP](https://msdn.microsoft.com/library/windows/desktop/bb891979). Nell'esempio dovrai sostituire tutte le istanze di *test* e *ias-domain* con i tuoi dati.



## Aggiunta di certificati

Se il metodo di autenticazione selezionato è basato su certificati, sarà necessario [creare un pacchetto di provisioning](provisioning-packages-for-surface-hub.md), [utilizzare MDM](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)o importare un certificato dalle impostazioni (aggiornamento**delle impostazioni**  >  **e**  >  **certificati**di sicurezza) per distribuire tali certificati nel dispositivo Surface Hub nell'archivio certificati appropriato. Quando si aggiungono i certificati, ogni PFX deve contenere un solo certificato (un PFX non può includere più certificati).


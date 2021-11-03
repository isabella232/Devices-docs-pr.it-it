---
title: Abilita autenticazione cablata 802.1x
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
ms.openlocfilehash: dcb2799accfcbccb41e44e09f0df3fd1ac6eb57e
ms.sourcegitcommit: 94e11386d7034c6bc5fe753f7bebf61a9c815509
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/02/2021
ms.locfileid: "12154041"
---
# <a name="enable-8021x-wired-authentication"></a>Abilita autenticazione cablata 802.1x

L'aggiornamento [del 14 novembre 2017](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) a Windows 10 (build 15063.726) ha abilitato i criteri MDM di autenticazione cablata 802.1x nei dispositivi Surface Hub. La funzionalità consente alle organizzazioni di applicare l'autenticazione di rete cablata standardizzata tramite il [protocollo di autenticazione IEEE 802.1x](http://www.ieee802.org/1/pages/802.1x-2010.html). Questo era già disponibile per l'autenticazione wireless [tramite profili WLAN](/mem/intune/configuration/wi-fi-settings-import-windows-8-1) tramite MDM. In questo argomento viene illustrato come configurare un dispositivo Surface Hub per l'utilizzo con l'autenticazione cablata. 

L'imposizione e l'abilitazione dell'autenticazione cablata 802.1x su dispositivi Surface Hub possono essere eseguite tramite MDM [definizione OMA-URI](/mem/intune/configuration/custom-settings-windows-10). 

La configurazione primaria da impostare è il criterio **LanProfile**. A seconda del metodo di autenticazione selezionato, altri criteri potrebbero essere necessari, il criterio **EapUserData** o i criteri MDM per l'aggiunta di certificati utente o del computer (ad esempio [ClientCertificateInstall](/windows/client-management/mdm/clientcertificateinstall-csp) per certificati utente/dispositivo o [RootCATrustedCertificates](/windows/client-management/mdm/rootcacertificates-csp) per certificati dispositivo). 

## <a name="lanprofile-policy-element"></a>Elemento dei criteri LanProfile

Per configurare Surface Hub per l'utilizzo di uno dei metodi di autenticazione 802.1x supportati, utilizza il seguente OMA-URI. 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

Questo nodo OMA-URI accetta una stringa di testo XML come parametro. L'XML fornito come parametro deve essere conforme allo [schema del profilo rete LAN cablata](/openspecs/windows_protocols/ms-gpwl/c88a926a-087b-405f-9a76-effaf7277bf3) inclusi gli elementi dello [schema 802.1X](/openspecs/windows_protocols/ms-gpwl/71f2eda6-d018-4ba3-ad37-32c98b926ebb). 

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

## <a name="eapuserdata-policy-element"></a>Elemento dei criteri EapUserData

Se il metodo di autenticazione selezionato richiede un nome utente e una password anziché un certificato, puoi utilizzare l'elemento **EapUserData** per specificare le credenziali per il dispositivo da utilizzare per eseguire l'autenticazione in rete. 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

Questo nodo OMA-URI accetta una stringa di testo XML come parametro. L'XML fornito come parametro deve essere conforme all'[esempio Proprietà dell'utente MS-CHAPv2 PEAP](/windows/win32/eaphost/peap-ms-chapv2-user-properties). Nell'esempio dovrai sostituire tutte le istanze di *test* e *ias-domain* con i tuoi dati.



## <a name="adding-certificates"></a>Aggiunta di certificati

Se il metodo di autenticazione selezionato è basato su certificati, dovrai creare un pacchetto di [provisioning,](provisioning-packages-for-surface-hub.md)usare [MDM](/windows/client-management/mdm/clientcertificateinstall-csp)o importare un certificato dalle impostazioni (**Impostazioni**Update and Security Certificates ) per distribuire tali certificati nel dispositivo Surface Hub nell'archivio certificati  >  ****  >  **** appropriato. Quando si aggiungono i certificati, ogni PFX deve contenere un solo certificato (un PFX non può includere più certificati).


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
# <span data-ttu-id="0f944-103">Abilita autenticazione cablata 802.1x</span><span class="sxs-lookup"><span data-stu-id="0f944-103">Enable 802.1x wired authentication</span></span>

<span data-ttu-id="0f944-104">Il [14 novembre 2017 l'aggiornamento a Windows 10](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (build 15063.726) abilita i criteri MDM per l'autenticazione cablata 802.1x sui dispositivi Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="0f944-104">The [November 14, 2017 update to Windows 10](https://support.microsoft.com/help/4048954/windows-10-update-kb4048954) (build 15063.726) enables 802.1x wired authentication MDM policies on Surface Hub devices.</span></span> <span data-ttu-id="0f944-105">La funzionalità consente alle organizzazioni di applicare l'autenticazione di rete cablata standardizzata tramite il [protocollo di autenticazione IEEE 802.1x](http://www.ieee802.org/1/pages/802.1x-2010.html).</span><span class="sxs-lookup"><span data-stu-id="0f944-105">The feature allows organizations to enforce standardized wired network authentication using the [IEEE 802.1x authentication protocol](http://www.ieee802.org/1/pages/802.1x-2010.html).</span></span> <span data-ttu-id="0f944-106">Questo è già disponibile per l'autenticazione wireless con i profili WLAN tramite MDM.</span><span class="sxs-lookup"><span data-stu-id="0f944-106">This is already available for wireless authentication using WLAN profiles via MDM.</span></span> <span data-ttu-id="0f944-107">In questo argomento viene illustrato come configurare un dispositivo Surface Hub per l'utilizzo con l'autenticazione cablata.</span><span class="sxs-lookup"><span data-stu-id="0f944-107">This topic explains how to  configure a Surface Hub for use with wired authentication.</span></span> 

<span data-ttu-id="0f944-108">L'imposizione e l'abilitazione dell'autenticazione cablata 802.1x su dispositivi Surface Hub possono essere eseguite tramite MDM [definizione OMA-URI](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings).</span><span class="sxs-lookup"><span data-stu-id="0f944-108">Enforcement and enablement of 802.1x wired authentication on Surface Hub can be done through MDM [OMA-URI definition](https://docs.microsoft.com/intune-classic/deploy-use/windows-10-policy-settings-in-microsoft-intune#oma-uri-settings).</span></span> 

<span data-ttu-id="0f944-109">La configurazione primaria da impostare è il criterio **LanProfile**.</span><span class="sxs-lookup"><span data-stu-id="0f944-109">The primary configuration to set is the **LanProfile** policy.</span></span> <span data-ttu-id="0f944-110">A seconda del metodo di autenticazione selezionato, altri criteri potrebbero essere necessari, il criterio **EapUserData** o i criteri MDM per l'aggiunta di certificati utente o del computer (ad esempio [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) per certificati utente/dispositivo o [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) per certificati dispositivo).</span><span class="sxs-lookup"><span data-stu-id="0f944-110">Depending on the authentication method selected, other policies may be required, either the **EapUserData** policy or through MDM policies for adding user or machine certificates (such as [ClientCertificateInstall](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp) for user/device certificates or [RootCATrustedCertificates](https://docs.microsoft.com/windows/client-management/mdm/rootcacertificates-csp) for device certificates).</span></span> 

## <span data-ttu-id="0f944-111">Elemento dei criteri LanProfile</span><span class="sxs-lookup"><span data-stu-id="0f944-111">LanProfile policy element</span></span>

<span data-ttu-id="0f944-112">Per configurare Surface Hub per l'utilizzo di uno dei metodi di autenticazione 802.1x supportati, utilizza il seguente OMA-URI.</span><span class="sxs-lookup"><span data-stu-id="0f944-112">To configure Surface Hub to use one of the supported 802.1x authentication methods, utilize the following OMA-URI.</span></span> 

```
./Vendor/MSFT/SurfaceHub/Dot3/LanProfile
```

<span data-ttu-id="0f944-113">Questo nodo OMA-URI accetta una stringa di testo XML come parametro.</span><span class="sxs-lookup"><span data-stu-id="0f944-113">This OMA-URI node takes a text string of XML as a parameter.</span></span> <span data-ttu-id="0f944-114">L'XML fornito come parametro deve essere conforme allo [schema del profilo rete LAN cablata](https://msdn.microsoft.com/library/cc233002.aspx) inclusi gli elementi dello [schema 802.1X](https://msdn.microsoft.com/library/cc233003.aspx).</span><span class="sxs-lookup"><span data-stu-id="0f944-114">The XML provided as a parameter should conform to the [Wired LAN Profile Schema](https://msdn.microsoft.com/library/cc233002.aspx) including elements from the [802.1X schema](https://msdn.microsoft.com/library/cc233003.aspx).</span></span> 

<span data-ttu-id="0f944-115">Nella maggior parte dei casi, un amministratore o un utente può esportare l'XML LanProfile da un PC esistente che è già configurato nella rete per 802.1X con il comando NETSH seguente.</span><span class="sxs-lookup"><span data-stu-id="0f944-115">In most instances, an administrator or user can export the LanProfile XML from an existing PC that is already configured on the network for 802.1X using this following NETSH command.</span></span> 

```
netsh lan export profile folder=.
```

<span data-ttu-id="0f944-116">L'esecuzione di questo comando darà il risultato seguente e posizionerà un file denominato **Ethernet.xml** nella directory corrente.</span><span class="sxs-lookup"><span data-stu-id="0f944-116">Running this command will give the following output and place a file titled **Ethernet.xml** in the current directory.</span></span> 

```
Interface: Ethernet
Profile File Name: .\Ethernet.xml
1 profile(s) were exported successfully.
```

## <span data-ttu-id="0f944-117">Elemento dei criteri EapUserData</span><span class="sxs-lookup"><span data-stu-id="0f944-117">EapUserData policy element</span></span>

<span data-ttu-id="0f944-118">Se il metodo di autenticazione selezionato richiede un nome utente e una password anziché un certificato, puoi utilizzare l'elemento **EapUserData** per specificare le credenziali per il dispositivo da utilizzare per eseguire l'autenticazione in rete.</span><span class="sxs-lookup"><span data-stu-id="0f944-118">If your selected authentication method requires a username and password as opposed to a certificate, you can use the **EapUserData** element to specify credentials for the device to use to authenticate to the network.</span></span> 

```
./Vendor/MSFT/SurfaceHub/Dot3/EapUserData 
```

<span data-ttu-id="0f944-119">Questo nodo OMA-URI accetta una stringa di testo XML come parametro.</span><span class="sxs-lookup"><span data-stu-id="0f944-119">This OMA-URI node takes a text string of XML as a parameter.</span></span> <span data-ttu-id="0f944-120">L'XML fornito come parametro deve essere conforme all'[esempio Proprietà dell'utente MS-CHAPv2 PEAP](https://msdn.microsoft.com/library/windows/desktop/bb891979).</span><span class="sxs-lookup"><span data-stu-id="0f944-120">The XML provided as a parameter should conform to the [PEAP MS-CHAPv2 User Properties example](https://msdn.microsoft.com/library/windows/desktop/bb891979).</span></span> <span data-ttu-id="0f944-121">Nell'esempio dovrai sostituire tutte le istanze di *test* e *ias-domain* con i tuoi dati.</span><span class="sxs-lookup"><span data-stu-id="0f944-121">In the example, you will need to replace all instances of *test* and *ias-domain* with your information.</span></span>



## <span data-ttu-id="0f944-122">Aggiunta di certificati</span><span class="sxs-lookup"><span data-stu-id="0f944-122">Adding certificates</span></span>

<span data-ttu-id="0f944-123">Se il metodo di autenticazione selezionato è basato su certificati, sarà necessario [creare un pacchetto di provisioning](provisioning-packages-for-surface-hub.md), [utilizzare MDM](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp)o importare un certificato dalle impostazioni (aggiornamento**delle impostazioni**  >  **e**  >  **certificati**di sicurezza) per distribuire tali certificati nel dispositivo Surface Hub nell'archivio certificati appropriato.</span><span class="sxs-lookup"><span data-stu-id="0f944-123">If your selected authentication method is certificate-based, you will need to [create a provisioning package](provisioning-packages-for-surface-hub.md), [utilize MDM](https://docs.microsoft.com/windows/client-management/mdm/clientcertificateinstall-csp), or import a certificate from settings (**Settings** > **Update and Security** > **Certificates**) to deploy those certificates to your Surface Hub device in the appropriate Certificate Store.</span></span> <span data-ttu-id="0f944-124">Quando si aggiungono i certificati, ogni PFX deve contenere un solo certificato (un PFX non può includere più certificati).</span><span class="sxs-lookup"><span data-stu-id="0f944-124">When adding certificates, each PFX must contain only one certificate (a PFX cannot have multiple certificates).</span></span>


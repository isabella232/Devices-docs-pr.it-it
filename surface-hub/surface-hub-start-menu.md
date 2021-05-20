---
title: Configurare il menu Start di Surface Hub
description: Usa MDM per personalizzare il menu Start in Surface Hub.
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
ms.topic: article
ms.date: 08/15/2018
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: cf9649b8d1f747722064793fbbde70116bc7f424
ms.sourcegitcommit: a4f8d271b1372321c3b45fc5a7a29703976964a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/20/2021
ms.locfileid: "11576846"
---
# <a name="configure-surface-hub-start-menu"></a><span data-ttu-id="a74b9-103">Configurare il menu Start di Surface Hub</span><span class="sxs-lookup"><span data-stu-id="a74b9-103">Configure Surface Hub Start menu</span></span>

<span data-ttu-id="a74b9-104">L'aggiornamento del [17 gennaio 2018 a Windows 10](https://support.microsoft.com/help/4057144) (build 15063.877) abilita i menu Start personalizzati nei dispositivi Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="a74b9-104">The [January 17, 2018 update to Windows 10](https://support.microsoft.com/help/4057144) (build 15063.877) enables customized Start menus on Surface Hub devices.</span></span> <span data-ttu-id="a74b9-105">Il layout del menu Start personalizzato può essere applicato tramite Gestione di dispositivi mobili (MDM).</span><span class="sxs-lookup"><span data-stu-id="a74b9-105">You apply the customized Start menu layout using mobile device management (MDM).</span></span>

<span data-ttu-id="a74b9-106">Quando viene applicato un layout del menu Start personalizzato a Surface Hub, gli utenti non possono aggiungere, rimuovere o disinstallare app nella schermata Start.</span><span class="sxs-lookup"><span data-stu-id="a74b9-106">When you apply a customized Start menu layout to Surface Hub, users cannot pin, unpin, or uninstall apps from Start.</span></span> 

## <a name="how-to-apply-a-customized-start-menu-to-surface-hub"></a><span data-ttu-id="a74b9-107">Come applicare un menu Start personalizzato a Surface Hub</span><span class="sxs-lookup"><span data-stu-id="a74b9-107">How to apply a customized Start menu to Surface Hub</span></span>

<span data-ttu-id="a74b9-108">Il menu Start personalizzato viene definito in un file XML di layout di Start.</span><span class="sxs-lookup"><span data-stu-id="a74b9-108">The customized Start menu is defined in a Start layout XML file.</span></span> <span data-ttu-id="a74b9-109">Sono disponibili due opzioni per la creazione del file XML di layout di Start:</span><span class="sxs-lookup"><span data-stu-id="a74b9-109">You have two options for creating your Start layout XML file:</span></span>

- <span data-ttu-id="a74b9-110">Modifica il file [XML Start di Surface Hub predefinito](#default)</span><span class="sxs-lookup"><span data-stu-id="a74b9-110">Edit the [default Surface Hub Start XML](#default)</span></span>

    <span data-ttu-id="a74b9-111">-oppure-</span><span class="sxs-lookup"><span data-stu-id="a74b9-111">-or-</span></span>

- <span data-ttu-id="a74b9-112">Configura il menu Start desiderato su un desktop (aggiungendo solo le app disponibili in Surface Hub) e quindi [esporta il layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout).</span><span class="sxs-lookup"><span data-stu-id="a74b9-112">Configure the desired Start menu on a desktop (pinning only apps that are available on Surface Hub), and then [export the layout](https://docs.microsoft.com/windows/configuration/customize-and-export-start-layout#export-the-start-layout).</span></span>

>[!TIP]
><span data-ttu-id="a74b9-113">Per aggiungere un riquadro con un collegamento Web al menu Start del desktop, vai al collegamento in Microsoft Edge, seleziona `...` nell'angolo in alto a destra e seleziona **Aggiungi questa pagina a Start**.</span><span class="sxs-lookup"><span data-stu-id="a74b9-113">To add a tile with a web link to your desktop start menu, go to the link in Microsoft Edge, select `...` in the top right corner, and select **Pin this page to Start**.</span></span> <span data-ttu-id="a74b9-114">Vedere [un layout Start che include un collegamento di Microsoft Edge](#edge) per un esempio di come i collegamenti verranno visualizzati nel file XML.</span><span class="sxs-lookup"><span data-stu-id="a74b9-114">See [a Start layout that includes a Microsoft Edge link](#edge) for an example of how links will appear in the XML.</span></span>

<span data-ttu-id="a74b9-115">Per modificare il file XML predefinito o il layout esportato, acquisisci familiarità con il file [XML di layout di Start](https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop).</span><span class="sxs-lookup"><span data-stu-id="a74b9-115">To edit the default XML or the exported layout, familiarize yourself with the [Start layout XML](https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop).</span></span> <span data-ttu-id="a74b9-116">Esistono alcune [differenze tra il layout Start in un desktop e su Surface Hub.](#differences)</span><span class="sxs-lookup"><span data-stu-id="a74b9-116">There are a few [differences between Start layout on a deskop and a Surface Hub.](#differences)</span></span>

<span data-ttu-id="a74b9-117">Dopo aver definito il menu Start in un file XML di layout di Start, [crea un criterio MDM per applicare il layout.](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management#a-href-idbkmk-domaingpodeploymentacreate-a-policy-for-your-customized-start-layout)</span><span class="sxs-lookup"><span data-stu-id="a74b9-117">When you have your Start menu defined in a Start layout XML, [create an MDM policy to apply the layout.](https://docs.microsoft.com/windows/configuration/customize-windows-10-start-screens-by-using-mobile-device-management#a-href-idbkmk-domaingpodeploymentacreate-a-policy-for-your-customized-start-layout)</span></span>

<span id="differences" />

## <a name="differences-between-surface-hub-and-desktop-start-menu"></a><span data-ttu-id="a74b9-118">Differenze tra il menu Start su Surface Hub e sul desktop</span><span class="sxs-lookup"><span data-stu-id="a74b9-118">Differences between Surface Hub and desktop Start menu</span></span>

<span data-ttu-id="a74b9-119">Esistono alcune differenze chiave tra la personalizzazione del menu Start per Surface Hub e un desktop di Windows 10:</span><span class="sxs-lookup"><span data-stu-id="a74b9-119">There are a few key differences between Start menu customization for Surface Hub and a Windows 10 desktop:</span></span>

- <span data-ttu-id="a74b9-120">Non è possibile **utilizzare DesktopApplicationTile** ( nel codice XML del layout della schermata Start perché Windows applicazioni desktop (Win32) non sono supportate in https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop#startdesktopapplicationtile) Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="a74b9-120">You cannot use **DesktopApplicationTile** (https://docs.microsoft.com/windows/configuration/start-layout-xml-desktop#startdesktopapplicationtile) in your Start layout XML because Windows desktop applications (Win32) are not supported on Surface Hub.</span></span>
- <span data-ttu-id="a74b9-121">Non è possibile utilizzare il file XML del layout di Start per configurare la barra delle applicazioni o la schermata iniziale per Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="a74b9-121">You cannot use the Start layout XML to configure the taskbar or the Welcome screen for Surface Hub.</span></span>  
- <span data-ttu-id="a74b9-122">Il criterio layout della schermata Start deve essere assegnato solo ai dispositivi e non agli utenti.</span><span class="sxs-lookup"><span data-stu-id="a74b9-122">The Start layout policy should be assigned only to devices, not users.</span></span>
- <span data-ttu-id="a74b9-123">L'impostazione URI OMA da utilizzare nel criterio è</span><span class="sxs-lookup"><span data-stu-id="a74b9-123">The OMA-URI setting to use in the policy is</span></span> `./Device/Vendor/MSFT/Policy/Config/Start/StartLayout`
- <span data-ttu-id="a74b9-124">Surface Hub supporta un massimo di 6 colonne (6 riquadri 1 x 1), tuttavia **devi** definire `GroupCellWidth=8`anche se su Surface Hub verranno visualizzati solo i riquadri nelle colonne 0-5, non le colonne 6 e 7.</span><span class="sxs-lookup"><span data-stu-id="a74b9-124">Surface Hub supports a maximum of 6 columns (6 1x1 tiles), however, you **must** define `GroupCellWidth=8` even though Surface Hub will only display tiles in columns 0-5, not columns 6 and 7.</span></span>
- <span data-ttu-id="a74b9-125">Surface Hub supporta un massimo di righe 6 (6 riquadri 1 x 1)</span><span class="sxs-lookup"><span data-stu-id="a74b9-125">Surface Hub supports a maximum 6 rows (6 1x1 tiles)</span></span>
- `SecondaryTile`<span data-ttu-id="a74b9-126">, che viene utilizzato per i collegamenti, verrà aperto il collegamento in Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="a74b9-126">, which is used for links, will open the link in Microsoft Edge.</span></span>


<span id="default" />

## <a name="example-default-surface-hub-start-layout"></a><span data-ttu-id="a74b9-127">Esempio: layout di Start su Surface Hub predefinito</span><span class="sxs-lookup"><span data-stu-id="a74b9-127">Example: Default Surface Hub Start layout</span></span>

```xml
<LayoutModificationTemplate Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification">
  <LayoutOptions StartTileGroupCellWidth="8" />
  <DefaultLayoutOverride>
    <StartLayoutCollection>
      <defaultlayout:StartLayout GroupCellWidth="8" xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout">
        <start:Group Name="" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
        <start:Tile
            AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
            Size="2x2"
            Row="0"
            Column="0"/>
        <start:Tile
            AppUserModelID="Microsoft.Getstarted_8wekyb3d8bbwe!App"
            Size="4x2"
            Row="0"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.PowerPoint_8wekyb3d8bbwe!Microsoft.pptim"
            Size="2x2"
            Row="2"
            Column="0"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!Microsoft.Word"
            Size="2x2"
            Row="2"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!Microsoft.Excel"
            Size="2x2"
            Row="2"
            Column="4"/>
        <start:Tile
            AppUserModelID="c5e2524a-ea46-4f67-841f-6a9465d9d515_cw5n1h2txyewy!App"
            Size="2x2"
            Row="4"
            Column="0"/>
        <start:Tile
            AppUserModelID="microsoft.microsoftskydrive_8wekyb3d8bbwe!App"
            Size="2x2"
            Row="4"
            Column="2"/>
        <start:Tile
            AppUserModelID="Microsoft.MicrosoftPowerBIForWindows_8wekyb3d8bbwe!Microsoft.MicrosoftPowerBIForWindows"
            Size="2x2"
            Row="4"
            Column="4"/>
        </start:Group>
      </defaultlayout:StartLayout>
    </StartLayoutCollection>
  </DefaultLayoutOverride>
</LayoutModificationTemplate>
```

<span id="edge" />

## <a name="example-start-layout-that-includes-a-microsoft-edge-link"></a><span data-ttu-id="a74b9-128">Esempio: layout di Start che include un collegamento di Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a74b9-128">Example: Start layout that includes a Microsoft Edge link</span></span>

<span data-ttu-id="a74b9-129">Questo esempio mostra un collegamento a un sito Web e un collegamento a un file .pdf.</span><span class="sxs-lookup"><span data-stu-id="a74b9-129">This example shows a link to a website and a link to a .pdf file.</span></span> <span data-ttu-id="a74b9-130">Il riquadro secondario Microsoft Edge un'icona di 150 x 150 pixel.</span><span class="sxs-lookup"><span data-stu-id="a74b9-130">The secondary tile for Microsoft Edge uses a 150 x 150 pixel icon.</span></span>

```xml
<LayoutModificationTemplate Version="1" xmlns="http://schemas.microsoft.com/Start/2014/LayoutModification">
  <LayoutOptions StartTileGroupCellWidth="8" />
  <DefaultLayoutOverride>
    <StartLayoutCollection>
      <defaultlayout:StartLayout GroupCellWidth="8" xmlns:defaultlayout="http://schemas.microsoft.com/Start/2014/FullDefaultLayout">
        <start:Group Name="" xmlns:start="http://schemas.microsoft.com/Start/2014/StartLayout">
    <start:Tile
              AppUserModelID="Microsoft.Office.PowerPoint_8wekyb3d8bbwe!Microsoft.pptim"
              Size="2x2"
              Row="0"
              Column="0"/>
          <start:Tile
              AppUserModelID="Microsoft.Office.Word_8wekyb3d8bbwe!Microsoft.Word"
              Size="2x2"
              Row="0"
              Column="2"/>
          <start:Tile
              AppUserModelID="Microsoft.Office.Excel_8wekyb3d8bbwe!Microsoft.Excel"
              Size="2x2"
              Row="0"
              Column="4"/>
    <start:Tile
              AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
              Size="2x2"
              Row="2"
              Column="0"/>
    <start:Tile
              AppUserModelID="microsoft.microsoftskydrive_8wekyb3d8bbwe!App"
              Size="2x2" 
             Row="2"
             Column="2"/>   
  <start:SecondaryTile
            AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
           TileID="2678823080"
           DisplayName="Bing"
           Arguments="https://www.bing.com/"
           Square150x150LogoUri="ms-appx:///"
           Wide310x150LogoUri="ms-appx:///"
           ShowNameOnSquare150x150Logo="true"
           ShowNameOnWide310x150Logo="false"
           BackgroundColor="#ffe9e7e7"
           ForegroundText="dark"
           Size="2x2"
           Column="4"
           Row="2"  />
    <start:Tile
              AppUserModelID="Microsoft.Windows.Photos_8wekyb3d8bbwe!App"
              Size="2x2"
              Row="4"
              Column="0"/>
    <start:SecondaryTile
             AppUserModelID="Microsoft.MicrosoftEdge_8wekyb3d8bbwe!MicrosoftEdge"
             TileID="6153963000"
             DisplayName="cstrtqbiology.pdf"
             Arguments="-contentTile -formatVersion 0x00000003 -pinnedTimeLow 0x45b7376e -pinnedTimeHigh 0x01d2356c -securityFlags 0x00000000 -tileType 0x00000000 -url 0x0000003a https://www.ada.gov/regs2010/2010ADAStandards/Guidance_2010ADAStandards.pdf"
             Square150x150LogoUri="ms-appx:///Assets/MicrosoftEdgeSquare150x150.png"
             Wide310x150LogoUri="ms-appx:///" 
             ShowNameOnSquare150x150Logo="true"
             ShowNameOnWide310x150Logo="false"
             BackgroundColor="#ff4e4248"
             Size="4x2" 
             Row="4"
             Column="2"/>
        </start:Group>
      </defaultlayout:StartLayout>
    </StartLayoutCollection>
  </DefaultLayoutOverride>
</LayoutModificationTemplate>
```

>[!NOTE]
><span data-ttu-id="a74b9-131">Il valore predefinito per è light. Non è necessario includere nel codice XML a meno che il valore non venga impostato `ForegroundText` `ForegroundText` su scuro.</span><span class="sxs-lookup"><span data-stu-id="a74b9-131">The default value for `ForegroundText` is light; you don't need to include `ForegroundText` in your XML unless you're changing the value to dark.</span></span>

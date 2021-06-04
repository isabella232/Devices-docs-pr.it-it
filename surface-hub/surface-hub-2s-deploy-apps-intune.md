---
title: Distribuire app in Surface Hub 2S con Intune
description: Informazioni su come distribuire le app in Surface Hub 2S usando Intune.
keywords: separare i valori con virgole
ms.prod: surface-hub
ms.sitesec: library
author: greg-lindsay
ms.author: greglin
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 06/20/2019
ms.localizationpriority: Medium
ms.openlocfilehash: 51e54a5b2881519f2fc361675253c9e50bad0864
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833284"
---
# Distribuire app in Surface Hub 2S con Intune

È possibile installare altre app per soddisfare le esigenze del team o dell'organizzazione.

##  <a name="developer-guidelines"></a>Linee guida per gli sviluppatori

- Surface Hub esegue solo le [app della piattaforma UWP (Universal Windows Platform)](https://msdn.microsoft.com/windows/uwp/get-started/whats-a-uwp). Le app create utilizzando [Desktop App Converter](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-run-desktop-app-converter) non verranno eseguite su Surface Hub.
- Le app devono essere destinate alla [famiglia di dispositivi universali](https://msdn.microsoft.com/library/windows/apps/dn894631) o alla famiglia di dispositivi Windows Team.
- Surface Hub supporta solo le [app con licenza offline](https://docs.microsoft.com/microsoft-store/distribute-offline-apps) di [Microsoft Store for business](https://businessstore.microsoft.com/store).
- Per impostazione predefinita, le app devono riportare la firma dello Store per essere installate. Durante lo sviluppo e il test, puoi anche scegliere di eseguire app UWP firmate dallo sviluppatore inserendo il dispositivo in modalità sviluppatore.
- Durante lo sviluppo e l'invio di app a Microsoft Store, imposta la disponibilità della famiglia di dispositivi e le opzioni di licenza organizzativa per verificare che le app siano disponibili per l'esecuzione su Surface Hub.
- Sono necessarie credenziali di amministratore per installare le app in Surface Hub. Progettato per l'uso nelle sale riunioni e in altri spazi condivisi, Surface Hub impedisce agli utenti abituali di accedere a Microsoft Store per scaricare e installare le app.

##  <a name="deployment-guidelines"></a>Linee guida per la distribuzione

Puoi distribuire app UWP (Universal Windows Platform) a Surface Hub 2S usando Intune, facilitando la distribuzione delle app ai dispositivi.

1. Per distribuire le app, Abilita MDM per l'organizzazione. Nel portale di Intune selezionare **Intune** come autorità MDM (scelta consigliata). <br>

    ![Scegliere autorità MDM](images/sh2-set-intune5.png)

2. Abilitare Microsoft Store for business in Intune. Aprire Intune, selezionare **app client**  >  **Microsoft Store for business.** <br>

    ![Abilitare Store for business](images/sh2-deploy-apps-sync.png)

3. In Intune aprire **Microsoft Store for business** e selezionare **Impostazioni**  >  **Distribuisci**  >  **strumenti di gestione**. Scegliere **Microsoft Intune** come strumento di gestione. <br>

    ![Aggiungere Intune come strumento di gestione](images/sh2-set-intune8.png)

4. In Microsoft Store for business selezionare **Impostazioni**  >  **Shop**  >  **shopping experience**Shop e quindi selezionare **Mostra app offline**. Le app offline si riferiscono alle app che possono essere sincronizzate con Intune e distribuite centralmente in un dispositivo.
5. Dopo aver abilitato lo shopping offline, puoi acquistare licenze offline per le app che puoi sincronizzare con Intune e distribuire come licenze per dispositivi.
6. Nelle **Intune**  >  **app client**di Intune  >  **Microsoft Store for business**selezionare **Sincronizza**.
7. Nella pagina app client cerca l'app nell'elenco delle app. Assegna le app al gruppo o ai gruppi di dispositivi desiderati. Selezionare **assegnazioni**  >  **gruppo Aggiungi**. <br>

![* Assegnazione di app a gruppi *](images/sh2-assign-group.png) <br>

8. In tipo di assegnazione scegliere **obbligatorio**. <br>

![* Assegnazione di app a gruppi *](images/sh2-add-group.png) <br>

9. Per i gruppi selezionati, scegliere **licenze per dispositivi** e quindi fare clic su **OK** e salvare l'assegnazione. <br>
 
![* Assegnazione di app a gruppi *](images/sh2-apps-assign.png)

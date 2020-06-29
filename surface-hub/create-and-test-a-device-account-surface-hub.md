---
title: Creare e testare un account del dispositivo (Surface Hub)
description: Questo argomento spiega come creare e testare l'account del dispositivo che Microsoft Surface Hub usa per comunicare con Microsoft Exchange e Skype.
ms.assetid: C8605B5F-2178-4C3A-B4E0-CE32C70ECF67
ms.reviewer: rikot
manager: laurawi
keywords: creare e testare l'account del dispositivo, account del dispositivo, Surface Hub e Microsoft Exchange, Surface Hub e Skype
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 03/06/2018
ms.localizationpriority: medium
ms.audience: itpro
ms.openlocfilehash: 20ec9b3a81ad511bcb7880de6b53025fbac0a561
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833771"
---
# Creare e testare un account del dispositivo (Surface Hub)


Questo argomento spiega come creare e testare l'account del dispositivo che Microsoft Surface Hub usa per comunicare con Microsoft Exchange e Skype.

Un **account del dispositivo** è un account della risorsa di Exchange che il dispositivo Surface Hub usa per:

-   Visualizzare il calendario delle riunioni
-   Partecipare a teams o chiamate Skype for business
-   Inviare e-mail (ad esempio, inviare il contenuto della lavagna tramite e-mail durante una riunione)

Al termine della configurazione dell'account del dispositivo in un dispositivo Surface Hub, gli utenti possono aggiungere questo account a un invito a una riunione con le stesse modalità di invito di una sala riunioni. 

## Panoramica della configurazione

Questa tabella descrive i passaggi principali e le decisioni di configurazione per la creazione di un account del dispositivo. 
 
| Passaggio | Descrizione                     |  Scopo                             |
|------|---------------------------------|--------------------------------------|
| 1    | Creare una cassetta postale delle risorse di Exchange abilitata per l'accesso (Exchange 2013 o versione successiva oppure Exchange Online) | Questa cassetta postale delle risorse consente al dispositivo di gestire un calendario delle riunioni, ricevere convocazioni di riunione e inviare e-mail. Deve essere abilitata per l'accesso per poter essere configurata in un dispositivo Surface Hub. |
| 2    | Configurare le proprietà della cassetta postale | La cassetta postale deve essere configurata con le proprietà corrette per assicurare la migliore esperienza per le riunioni nel dispositivo Surface Hub. Per altre informazioni sulle proprietà della cassetta postale, vedi l'argomento relativo alle [proprietà della cassetta postale](exchange-properties-for-surface-hub-device-accounts.md). |
| 3    | Applicare alla cassetta postale un criterio cassetta postale per dispositivi mobili compatibile | Surface Hub viene gestito tramite Gestione di dispositivi mobili (MDM) anziché con i criteri cassetta postale per dispositivi mobili. Per la compatibilità, l'account del dispositivo deve avere un criterio cassetta postale per dispositivi mobili con l'impostazione **PasswordEnabled** impostata su False. In caso contrario, Surface Hub non sarà in grado di sincronizzare le informazioni della posta e del calendario. |
| 4    | Abilitare la cassetta postale con Skype for Business (Lync Server 2013 o versione successiva oppure Skype for Business Online) | Skype for Business deve essere abilitato per usare le funzionalità di conferenza come videochiamate, messaggistica istantanea e condivisione dello schermo.  |
| 5    | (Facoltativo) Inserire l'ID del dispositivo ActiveSync nell'elenco elementi consentiti | L'organizzazione potrebbe disporre di un criterio globale che impedisce la sincronizzazione delle informazioni della posta e del calendario con gli account del dispositivo. In questo caso, devi consentire l'ID del dispositivo ActiveSync del tuo hub Surface. |
| 6    | (Facoltativo) Disabilitare la scadenza delle password | Per semplificare la gestione, puoi disattivare la scadenza delle password per l'account del dispositivo e consentire al dispositivo Surface Hub di ruotare automaticamente la password per l'account del dispositivo. Per altre informazioni sulla gestione delle password, vedi [Gestione delle password](password-management-for-surface-hub-device-accounts.md).  |

## Passaggi di configurazione dettagliati 

Ti consigliamo di configurare gli account del dispositivo con PowerShell remoto. Sono disponibili diversi script di PowerShell per creare e convalidare gli account del dispositivo. Per altre informazioni sugli script di PowerShell e le relative istruzioni, vedi [Appendice A: PowerShell](appendix-a-powershell-scripts-for-surface-hub.md). 

Per istruzioni dettagliate sull'uso di PowerShell per configurare un account del dispositivo, scegli un'opzione della tabella, in base alla distribuzione della tua organizzazione. 

| Distribuzione dell'organizzazione             |  Descrizione                  |
|---------------------------------|--------------------------------------|
| [Distribuzione online (Office 365)](online-deployment-surface-hub-device-accounts.md) | L’ambiente dell’organizzazione viene distribuito interamente in Office 365. |
| [Distribuzione locale (singola foresta)](on-premises-deployment-surface-hub-device-accounts.md) | L’organizzazione dispone di server che controlla e usa per ospitare Active Directory, Exchange e Skype for Business (o Lync) in un ambiente a singola foresta. |
| [Distribuzione locale (più foreste)](on-premises-deployment-surface-hub-multi-forest.md) | L’organizzazione dispone di server che controlla e usa per ospitare Active Directory, Exchange e Skype for Business (o Lync) in un ambiente a più foreste. |
| [Distribuzione ibrida](hybrid-deployment-surface-hub-device-accounts.md) | L’organizzazione dispone di un insieme di servizi, in parte ospitati in locale e in parte ospitati online tramite Office 365. |
| [Distribuzione online o ibrida con l'ambiente Skype Hybrid Voice](skype-hybrid-voice.md) | L'organizzazione dispone di pool principali di Skype for Business e di server Exchange nel cloud e utilizza un pool locale di Skype for Business 2015 o Cloud Connector Edition connesso tramite sistema PSTN (Public Switched Telephone Network). |


Se preferisci usare un'interfaccia utente grafica, alcuni passaggi possono essere eseguiti tramite l'interfaccia utente invece che con PowerShell. Per altre informazioni, vedi [Creare account del dispositivo con l'interfaccia utente](create-a-device-account-using-office-365.md).

## Verifica dell'account e test

Esistono due metodi disponibili che è possibile utilizzare per convalidare e testare un account del dispositivo Surface Hub: [script per le verifiche dell'account](appendix-a-powershell-scripts-for-surface-hub.md#acct-verification-ps-scripts) e l'[app di diagnostica hardware di Surface Hub](https://www.microsoft.com/store/apps/9nblggh51f2g). Lo script di verifica dell'account convaliderà un account dispositivo creato in precedenza con PowerShell dal desktop. L'app di diagnostica hardware di Surface Hub viene installata in Surface Hub e fornisce un feedback dettagliato sugli errori di accesso e comunicazione. Entrambi gli strumenti sono efficaci per testare gli account del dispositivo appena creati e devono essere usati per garantire una disponibilità ottimale degli account.

 

 

 






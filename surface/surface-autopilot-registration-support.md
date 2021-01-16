---
title: Supporto alla registrazione di Surface per Windows Autopilot
description: In questo articolo vengono illustrati i requisiti per inviare le richieste di registrazione del pilota automatico al supporto Microsoft.
ms.prod: w10
ms.mktglfcycl: manage
ms.localizationpriority: medium
ms.sitesec: library
author: coveminer
ms.author: greglin
ms.topic: article
ms.date: 9/14/2020
ms.reviewer: brrecord
manager: laurawi
audience: itpro
ms.openlocfilehash: 4ff3803701ffe71e1c5c0c36200c40e833a7fb25
ms.sourcegitcommit: 1053479c191fd10651d31a466fad1769fb0cd28b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "11271390"
---
# Supporto alla registrazione di Surface per Windows Autopilot

Un processo semplificato per la registrazione dei dispositivi Surface per la distribuzione di Autopilot Windows è ora disponibile nel supporto Microsoft. A partire da settembre 2020, i clienti e i provider di soluzioni cloud Microsoft (CSP) possono registrare i dispositivi Surface inviando richieste al supporto Microsoft. In questa pagina sono descritti i requisiti per gli scenari di registrazione del pilota automatico supportati seguenti:
 

- **Registrazione Autopilot di Surface Device**. Invia la richiesta di registrazione di dispositivi Surface in Windows Autopilot.
- **Richiesta hash hardware per dispositivi Surface.** Invia la richiesta al supporto Microsoft per fornire agli utenti gli hash hardware che i clienti o i CSP possono usare per la registrazione automatica dei dispositivi tramite Microsoft Intune o il centro partner Microsoft.
- **Cancellazione Autopilot del dispositivo Surface.** Invia la richiesta di eliminazione dei dispositivi da Windows Autopilot, in genere usato in scenari di fine vita del dispositivo.

Vedere la tabella seguente per dettagli sulle informazioni che sarà necessario raccogliere prima di inviare richieste di registrazione al supporto Microsoft.
 
**Tabella 1. Informazioni obbligatorie per le richieste di registrazione del pilota automatico**
 

| Informazioni obbligatorie                   | Descrizione                                                                                                                                                                                                                                                                                    | Registrazione Autopilot | Richiesta hash hardware | Autopilota<br>Annullamento |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **ID tenant di Azure Active Directory**   | L'ID tenant di Azure Active Directory è un identificatore univoco globale (GUID) diverso dal nome dell'organizzazione o dal dominio.<br> <br>Per trovare l'ID tenant [nel portale di](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)Azure. | Y                      | N                     | Y                           |
| **Nome di dominio di Azure Active Directory** | Il nome di dominio di primo livello; ad esempio, contoso.com.                                                                                                                                                                                                                                          | Y                      | N                     | Y                           |
| **Prova di proprietà**                 | Verificare la prova di proprietà caricando la fattura di vendita o fattura originale in formato PDF. Le schermate non vengono accettate.<br> <br>La fattura di vendita o fattura deve includere i seguenti elementi:<br>Numeri di serie del dispositivo.<br>Nome società.                                                           | Y                      | Y                     | Y                           |
| **Numeri di serie del dispositivo**              | Caricare file di Excel in formato CSV con ogni numero seriale del dispositivo in una nuova riga.                                                                                                                                                                                                                  | Y                      | Y                     | Y                           |

 

## Inviare richieste di supporto

  [![Ge supporto per la registrazione del pilota automatico per Surface](images/autopilot-reg-support-surface.png)](https://prod.support.services.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## Scopri di più

- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md)
- [Registrare i dispositivi Windows in Intune con Windows Autopilot](https://docs.microsoft.com/mem/autopilot/enrollment-autopilot)
- [Panoramica di Windows Autopilot](https://docs.microsoft.com/mem/autopilot/windows-autopilot)

 
 
 


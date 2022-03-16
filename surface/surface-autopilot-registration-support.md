---
title: Supporto alla registrazione di Surface per Windows Autopilot
description: In questo articolo vengono descritti i requisiti per l'invio delle richieste di registrazione Autopilot al supporto tecnico Microsoft.
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
appliesto:
- Windows 10
- Windows 11
ms.openlocfilehash: 77881fae189af1ad3773f5fad192a28746e2d983
ms.sourcegitcommit: beb2f9db90b19b74da6cdee8717cc0888f3b1d70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2022
ms.locfileid: "12449419"
---
# <a name="surface-registration-support-for-windows-autopilot"></a>Supporto alla registrazione di Surface per Windows Autopilot

Un processo semplificato di registrazione dei dispositivi Surface Windows distribuzione di Autopilot è ora disponibile dal supporto Microsoft. A partire da settembre 2020, i clienti e i provider di soluzioni cloud Microsoft (CSP) possono registrare i dispositivi Surface inviando richieste al supporto tecnico Microsoft. In questa pagina vengono descritti i requisiti per i seguenti scenari di registrazione autopilot supportati:
 
- **Registrazione di Surface Device Autopilot**. Invia la richiesta di registrare i dispositivi Surface Windows Autopilot.
- **Richiesta hash hardware dispositivo Surface.** Invia una richiesta al Supporto tecnico Microsoft per fornire hash hardware che i clienti o i CSP possono usare per registrare automaticamente i dispositivi tramite Microsoft Intune o il Centro per i partner Microsoft.
- **Annullamento della registrazione di Surface Device Autopilot.** Invia la richiesta di eliminazione dei dispositivi Windows Autopilot, in genere usata negli scenari di fine vita del dispositivo.

Per informazioni dettagliate sulle informazioni da raccogliere prima di inviare richieste di registrazione al supporto tecnico Microsoft, vedere la tabella seguente. Per i nomi ufficiali del modello di sistema di tutti i dispositivi Surface, fai riferimento a [Informazioni di riferimento sulla SKU di Surface System](surface-system-sku-reference.md).
 
**Tabella 1. Informazioni necessarie per le richieste di registrazione Autopilot**
 

| Informazioni obbligatorie                   | Descrizione                                                                                                                                                                                                                                                                                    | Registrazione autopilot | Richiesta hash hardware | Autopilot<br>Annullamento della registrazione |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- | --------------------- | --------------------------- |
| **Azure Active Directory tenant**   | Il Azure Active Directory tenant è un identificatore univoco globale (GUID) diverso dal nome o dal dominio dell'organizzazione.<br> <br>Per trovare l'ID tenant accedi al portale di Azure [qui](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties). | S                      | N                     | S                           |
| **Azure Active Directory dominio** | Nome di dominio di primo livello; ad esempio, contoso.com.                                                                                                                                                                                                                                          | S                      | N                     | S                           |
| **Prova di proprietà**                 | Verifica la prova di proprietà caricando la fattura o la fattura originale in formato PDF. Gli screenshot non vengono accettati.<br> <br>L'effetto attivo o la fattura deve includere quanto segue:<br>Numeri di serie del dispositivo.<br>Nome della società.                                                           | S                      | S                     | S                           |
| **Numeri di serie del dispositivo**              | Upload Excel file in formato CSV con ogni numero di serie del dispositivo in una nuova riga.                                                                                                                                                                                                                  | S                      | S                     | S                           |

 

## <a name="submit-support-requests"></a>Inviare richieste di supporto

  [![Get Autopilot Registration Support for Surface.](images/autopilot-reg-support-surface.png)](https://prod.support.services.microsoft.com/supportrequestform/0d8bf192-cab7-6d39-143d-5a17840b9f5f)
 
 
 
## <a name="learn-more"></a>Scopri di più

- [Windows Autopilot e dispositivi Surface](windows-autopilot-and-surface-devices.md)
- [Registrare i dispositivi Windows in Intune con Windows Autopilot](/mem/autopilot/enrollment-autopilot)
- [Panoramica di Windows Autopilot](/mem/autopilot/windows-autopilot)
- [Riferimento SKU del sistema Surface](surface-system-sku-reference.md)

 
 
 


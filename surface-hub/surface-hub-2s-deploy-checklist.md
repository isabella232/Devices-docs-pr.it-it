---
title: Elenchi di controllo di distribuzione di Surface Hub 2S
description: Verificare la distribuzione di Surface Hub 2S usando elenchi di controllo pre e post-distribuzione.
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
ms.openlocfilehash: 3c30892a3ae4f534006aa32ad6d969b42a52cbf2
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833794"
---
# Elenchi di controllo di distribuzione di Surface Hub 2S

## Elenco di controllo di Surface Hub 2S pre-distribuzione

|**Item**|**Risposta**|
|:------ |:------ |
|**Nome account dispositivo**| |
|**UPN dell'account di dispositivo**| |
|**Criteri di ActiveSync**| |
|**Configurazione di elaborazione del calendario completata**| ☐ Sì <br>  ☐ No |
|**Nome descrittivo del dispositivo**| |
|**Nome host del dispositivo**| |
|**Affiliazione**| ☐ None <br> ☐ Affiliazione di Active Directory <br> ☐ Azure Active Directory |
|**Modalità Microsoft Teams**| Modalità ☐ 0 <br> ☐ Modalità 1 <br> Modalità ☐ 2 |
|**Gestione dispositivi**| ☐ Sì, Microsoft Intune <br> ☐ Sì, altro gestore di dispositivi mobili [MDM] <br> ☐ None |  
|**Proxy**| ☐ Configurazione automatica <br> ☐ Server proxy <br> ☐ File di configurazione automatica del proxy (PAC) |
|**Autenticazione proxy**| ☐ Le credenziali dell'account del dispositivo <br> Richiesta di ☐ per le credenziali |
|**Rotazione delle password**| ☐ Su <br> ☐ Disattivato |
|**Nomi di dominio aggiuntivi di Skype for business (solo locale)**| |
|**Tempo di timeout della sessione**| |
|**Azione timeout sessione**| ☐ Sessione finale <br> ☐ Consenti curriculum vitae |
|**Riunioni e file personali**| ☐ Abilitato <br> ☐ Disabilitato |
|**Bloccare il timeout dello schermo**| |
|**Timeout di sospensione inattività**| |
|**Bluetooth**| ☐ Su <br> ☐ Disattivato |
|**Usare solo le unità USB di BitLocker**| ☐ Su <br> ☐ Disattivato |
|**Installare certificati aggiuntivi (solo locale)**| |
|**Aggiornamento di Windows**| ☐ Windows Update for business <br> ☐ Windows Server Update Services [WSUS] |
|**Impostazione del relatore app Surface**| ☐ Supporto per il rotolamento <br> ☐ Montato a parete |
|**Indirizzo IP**| ☐ Wired: DHCP <br> ☐ Wired-prenotazione DHCP <br> ☐ Wireless: DHCP <br> ☐ Wireless: prenotazione DHCP |

## Elenco di controllo di Surface Hub 2S post-distribuzione

|**Segno di spunta**|**Risposta**|
|:------|:---------|
|**Sincronizzazione dell'account del dispositivo**| ☐ Sì <br> ☐ No |
|**Chiave BitLocker**| ☐ Salvato in un file (nessuna affiliazione) <br> ☐ Salvati in Active Directory (affiliazione AD) <br>☐ Salvati in Azure AD |
|**Aggiornamenti del sistema operativo per dispositivi**| ☐ Completata |
|**Aggiornamenti di Windows Store**| ☐ Automatico <br> Manuale ☐ |
|**Riunione pianificata di Microsoft Teams**| Messaggio di posta elettronica di conferma ☐ ricevuto <br> ☐ Riunione viene visualizzata nella schermata Start <br>  ☐ Funzioni di join One-Touch <br> ☐ In grado di partecipare all'audio <br> ☐ In grado di partecipare a un video <br> ☐ In grado di condividere la schermata ||
|**Riunione pianificata di Skype for business**| Messaggio di posta elettronica di conferma ☐ ricevuto <br> ☐ Riunione viene visualizzata nella schermata Start <br> ☐ Correttamente le funzioni di join One-Touch <br> ☐ In grado di partecipare all'audio <br> ☐ In grado di partecipare a un video <br> ☐ In grado di condividere la schermata <br> ☐ In grado di inviare/ricevere messaggi istantanei |
|**Riunione pianificata già invitata**| ☐ Riunione rifiutata |
|**Riunione ad-hoc di Microsoft Teams**| ☐ Invitare altri utenti a lavorare <br> ☐ In grado di partecipare all'audio <br> ☐ In grado di partecipare a un video <br> ☐ In grado di condividere la schermata |
|**Riunione pianificata di Skype for business**| ☐ Invitare altri utenti a lavorare <br> ☐ In grado di partecipare all'audio <br> ☐ In grado di partecipare a un video <br> ☐ In grado di condividere la schermata <br> ☐ In grado di inviare/ricevere messaggi istantanei |
|**Microsoft Whiteboard**| ☐ Avvio da schermata iniziale/inizio <br> ☐ Avvio da Microsoft Teams | 
|**Chiamata in arrivo Skype/Teams**| ☐ In grado di partecipare all'audio<br>☐ In grado di partecipare a un video <br> ☐ In grado di condividere la schermata <br> ☐ In grado di inviare/ricevere messaggi istantanei (solo Skype for business) |
|**Flussi video live in arrivo**| ☐ Massimo 2 (Skype for business) <br> ☐ Massimo 4 (Microsoft Teams) |
|**Comportamento di Microsoft teams Mode 0**| ☐ Riquadro di Skype for business nella schermata di benvenuto/Start <br> ☐ Può partecipare a riunioni programmate di Skype for business (interfaccia utente Skype) <br> ☐ Può partecipare a riunioni di Team pianificate (interfaccia utente Teams) |
|**Comportamento di Microsoft teams Mode 1**| Riquadro ☐ teams nella schermata di benvenuto/inizio <br> ☐ Può partecipare a riunioni programmate di Skype for business (interfaccia utente Skype) <br> ☐ Può partecipare a riunioni di Team pianificate (interfaccia utente Teams) |
|**Comportamento di Microsoft teams Mode 2**| Riquadro ☐ teams nella schermata di benvenuto/inizio <br> ☐ Possono partecipare a riunioni programmate in teams <br> ☐ Non partecipare a riunioni Skype for business |

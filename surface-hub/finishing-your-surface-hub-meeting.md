---
title: 'Termina sessione: terminare una riunione Surface Hub'
description: Per terminare una riunione Surface Hub, toccare Termina sessione. Surface Hub azzera lo stato delle applicazioni, del sistema operativo e dell'interfaccia utente in modo da poter iniziare un'altra riunione.
keywords: Fatto, terminare una riunione Surface Hub, concludere una riunione Surface Hub, pulire una riunione Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.reviewer: ''
manager: laurawi
ms.localizationpriority: medium
ms.openlocfilehash: b18bc4b15b8a3925aeecdd9999b09b61011d1db5
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10833693"
---
# <span data-ttu-id="63cc4-105">Terminare una riunione Surface Hub con Termina sessione</span><span class="sxs-lookup"><span data-stu-id="63cc4-105">End a Surface Hub meeting with End session</span></span>
<span data-ttu-id="63cc4-106">Surface Hub è un dispositivo di collaborazione progettato per essere usato nelle aree riunioni da diversi gruppi di persone.</span><span class="sxs-lookup"><span data-stu-id="63cc4-106">Surface Hub is a collaboration device designed to be used in meeting spaces by different groups of people.</span></span> <span data-ttu-id="63cc4-107">Al termine di una riunione, gli utenti possono toccare **Termina sessione** per cancellare tutti i dati sensibili e preparare il dispositivo per la riunione successiva.</span><span class="sxs-lookup"><span data-stu-id="63cc4-107">At the end of a meeting, users can tap **End session** to clean up any sensitive data and prepare the device for the next meeting.</span></span> <span data-ttu-id="63cc4-108">Surface Hub azzererà o reimposterà gli stati degli elementi seguenti:</span><span class="sxs-lookup"><span data-stu-id="63cc4-108">Surface Hub will clean up, or reset, the following states:</span></span>
- <span data-ttu-id="63cc4-109">Applicazioni</span><span class="sxs-lookup"><span data-stu-id="63cc4-109">Applications</span></span>
- <span data-ttu-id="63cc4-110">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="63cc4-110">Operating system</span></span>
- <span data-ttu-id="63cc4-111">Interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="63cc4-111">User interface</span></span>

<span data-ttu-id="63cc4-112">Questo argomento spiega in che modo ognuno di questi stati viene reimpostato toccando l'opzione **Termina sessione**.</span><span class="sxs-lookup"><span data-stu-id="63cc4-112">This topic explains what **End session** resets for each of these states.</span></span>

## <span data-ttu-id="63cc4-113">Applicazioni</span><span class="sxs-lookup"><span data-stu-id="63cc4-113">Applications</span></span>
<span data-ttu-id="63cc4-114">Quando avvii un'app in Surface Hub, l'app viene archiviata in memoria, mentre i dati vengono archiviati a livello di applicazione.</span><span class="sxs-lookup"><span data-stu-id="63cc4-114">When you start apps on Surface Hub, they are stored in memory and data is stored at the application level.</span></span> <span data-ttu-id="63cc4-115">Durante la sessione (o la riunione), i dati rimangono a disposizione di tutti gli utenti fino a quando non viene rimossa o sovrascritta la data.</span><span class="sxs-lookup"><span data-stu-id="63cc4-115">Data is available to all users during that session (or meeting) until date is removed or overwritten.</span></span> <span data-ttu-id="63cc4-116">Se si seleziona l'opzione **Termina sessione**, lo stato delle applicazioni di Surface Hub viene annullato mediante la chiusura delle applicazioni, l'eliminazione della cronologia del browser, la reimpostazione delle applicazioni e la rimozione dei registri di Skype.</span><span class="sxs-lookup"><span data-stu-id="63cc4-116">When **End session** is selected, Surface Hub application state is cleared out by closing applications, deleting browser history, resetting applications, and removing Skype logs.</span></span>

### <span data-ttu-id="63cc4-117">Chiudere le applicazioni</span><span class="sxs-lookup"><span data-stu-id="63cc4-117">Close applications</span></span>
<span data-ttu-id="63cc4-118">Surface Hub chiude tutte le finestre visibili, incluse le applicazioni Win32 e UWP (Universal Windows Platform).</span><span class="sxs-lookup"><span data-stu-id="63cc4-118">Surface Hub closes all visible windows, including Win32 and Universal Windows Platform (UWP) applications.</span></span> <span data-ttu-id="63cc4-119">La fase di chiusura delle applicazioni usa la visualizzazione multitasking per interrogare le finestre visibili.</span><span class="sxs-lookup"><span data-stu-id="63cc4-119">The application close stage uses the multitasking view to query the visible windows.</span></span> <span data-ttu-id="63cc4-120">Le finestre Win32 che non si chiudono entro un determinato intervallo di tempo vengono chiuse con **TerminateProcess**.</span><span class="sxs-lookup"><span data-stu-id="63cc4-120">Win32 windows that do not close within a certain timeframe are closed using **TerminateProcess**.</span></span> 
   
### <span data-ttu-id="63cc4-121">Eliminare la cronologia del browser</span><span class="sxs-lookup"><span data-stu-id="63cc4-121">Delete browser history</span></span>
<span data-ttu-id="63cc4-122">Surface Hub usa l'opzione di eliminazione della cronologia del browser disponibile in Edge per cancellare la cronologia di Edge e i dati memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="63cc4-122">Surface Hub uses Delete Browser History (DBH) in Edge to clear Edge history and cached data.</span></span> <span data-ttu-id="63cc4-123">Rispetto all'eliminazione manuale della cronologia del browser, con l'opzione **Termina sessione** vengono anche cancellati gli stati delle applicazioni e rimossi i dati prima dell'inizio della sessione o della riunione successiva.</span><span class="sxs-lookup"><span data-stu-id="63cc4-123">This is similar to how a user can clear out their browser history manually, but **End session** also ensures that application states are cleared and data is removed before the next session, or meeting, starts.</span></span> 
 
### <span data-ttu-id="63cc4-124">Reimpostare le applicazioni</span><span class="sxs-lookup"><span data-stu-id="63cc4-124">Reset applications</span></span>
<span data-ttu-id="63cc4-125">L'opzione **Termina sessione** reimposta lo stato di ogni applicazione installata in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-125">**End session** resets the state of each application that is installed on the Surface Hub.</span></span> <span data-ttu-id="63cc4-126">Con questa operazione vengono cancellate tutte le attività in background, i dati delle applicazioni, le notifiche e le finestre di dialogo del consenso.</span><span class="sxs-lookup"><span data-stu-id="63cc4-126">Resetting an application clears all background tasks, application data, notifications, and user consent dialogs.</span></span> <span data-ttu-id="63cc4-127">Le applicazioni vengono inoltre reimpostate allo stato di prima esecuzione per i successivi utenti di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-127">Applications are returned to their first-run state for the next people that use Surface Hub.</span></span>  
 
### <span data-ttu-id="63cc4-128">Rimuovere i registri di Skype</span><span class="sxs-lookup"><span data-stu-id="63cc4-128">Remove Skype logs</span></span>
<span data-ttu-id="63cc4-129">Skype non archivia informazioni personali in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-129">Skype does not store personally-identifiable information on Surface Hub.</span></span> <span data-ttu-id="63cc4-130">Le informazioni vengono archiviate nel servizio Skype in conformità alle linee guida esistenti di Skype for Business.</span><span class="sxs-lookup"><span data-stu-id="63cc4-130">Information is stored in the Skype service to meet existing Skype for Business guidance.</span></span> <span data-ttu-id="63cc4-131">Se si seleziona l'opzione **Termina sessione** gli unici dati rimossi sono le informazioni di registrazione a Skype locali,</span><span class="sxs-lookup"><span data-stu-id="63cc4-131">Local Skype logging information is the only data removed when **End session** is selected.</span></span> <span data-ttu-id="63cc4-132">che comprendono anche i registri e i registri multimediali della piattaforma UCCP (Unified Communications Client Platform).</span><span class="sxs-lookup"><span data-stu-id="63cc4-132">This includes Unified Communications Client Platform (UCCP) logs and media logs.</span></span>   

## <span data-ttu-id="63cc4-133">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="63cc4-133">Operating System</span></span>
<span data-ttu-id="63cc4-134">Nel sistema operativo sono presenti numerose informazioni sullo stato delle sessioni che devono essere cancellate dopo ogni riunione Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-134">The operating system hosts a variety of information about the state of the sessions that needs to be cleared after each Surface Hub meeting.</span></span> 

### <span data-ttu-id="63cc4-135">File system</span><span class="sxs-lookup"><span data-stu-id="63cc4-135">File System</span></span>
<span data-ttu-id="63cc4-136">I partecipanti alla riunione possono accedere a un set limitato di directory in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-136">Meeting attendees have access to a limited set of directories on the Surface Hub.</span></span> <span data-ttu-id="63cc4-137">Se si seleziona l'opzione **Termina sessione**, Surface Hub annulla le directory seguenti:</span><span class="sxs-lookup"><span data-stu-id="63cc4-137">When **End session** is selected, Surface Hub clears these directories:</span></span><br>
- <span data-ttu-id="63cc4-138">Musica</span><span class="sxs-lookup"><span data-stu-id="63cc4-138">Music</span></span>
- <span data-ttu-id="63cc4-139">Video</span><span class="sxs-lookup"><span data-stu-id="63cc4-139">Videos</span></span>
- <span data-ttu-id="63cc4-140">Documenti</span><span class="sxs-lookup"><span data-stu-id="63cc4-140">Documents</span></span>
- <span data-ttu-id="63cc4-141">Immagini</span><span class="sxs-lookup"><span data-stu-id="63cc4-141">Pictures</span></span>
- <span data-ttu-id="63cc4-142">Download</span><span class="sxs-lookup"><span data-stu-id="63cc4-142">Downloads</span></span>

<span data-ttu-id="63cc4-143">Surface Hub cancella anche le directory seguenti, in cui molte applicazioni scrivono spesso dei dati:</span><span class="sxs-lookup"><span data-stu-id="63cc4-143">Surface Hub also clears these directories, since many applications often write to them:</span></span>
- <span data-ttu-id="63cc4-144">Desktop</span><span class="sxs-lookup"><span data-stu-id="63cc4-144">Desktop</span></span>
- <span data-ttu-id="63cc4-145">Preferiti</span><span class="sxs-lookup"><span data-stu-id="63cc4-145">Favorites</span></span>
- <span data-ttu-id="63cc4-146">Recenti</span><span class="sxs-lookup"><span data-stu-id="63cc4-146">Recent</span></span>
- <span data-ttu-id="63cc4-147">Documenti pubblici</span><span class="sxs-lookup"><span data-stu-id="63cc4-147">Public Documents</span></span>
- <span data-ttu-id="63cc4-148">Musica pubblica</span><span class="sxs-lookup"><span data-stu-id="63cc4-148">Public Music</span></span>
- <span data-ttu-id="63cc4-149">Video musicali</span><span class="sxs-lookup"><span data-stu-id="63cc4-149">Public Videos</span></span>
- <span data-ttu-id="63cc4-150">Download pubblici</span><span class="sxs-lookup"><span data-stu-id="63cc4-150">Public Downloads</span></span>

### <span data-ttu-id="63cc4-151">Credenziali</span><span class="sxs-lookup"><span data-stu-id="63cc4-151">Credentials</span></span>
<span data-ttu-id="63cc4-152">Le credenziali utente archiviate in **TokenBroker**, **PasswordVault** o **Gestione credenziali** vengono eliminate quando tocchi **Termina sessione**.</span><span class="sxs-lookup"><span data-stu-id="63cc4-152">User credentials that are stored in **TokenBroker**, **PasswordVault**, or **Credential Manager** are cleared when you tap **End session**.</span></span>

## <span data-ttu-id="63cc4-153">Interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="63cc4-153">User interface</span></span>
<span data-ttu-id="63cc4-154">Se si seleziona l'opzione **Termina sessione**, le impostazioni dell'interfaccia utente vengono reimpostate ai valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="63cc4-154">User interface (UI) settings are returned to their default values when **End session** is selected.</span></span> 

### <span data-ttu-id="63cc4-155">Elementi dell'interfaccia utente</span><span class="sxs-lookup"><span data-stu-id="63cc4-155">UI items</span></span>
- <span data-ttu-id="63cc4-156">Azioni rapide reimpostate allo stato predefinito</span><span class="sxs-lookup"><span data-stu-id="63cc4-156">Reset Quick Actions to default state</span></span>
- <span data-ttu-id="63cc4-157">Notifiche di tipo avviso popup cancellate</span><span class="sxs-lookup"><span data-stu-id="63cc4-157">Clear Toast notifications</span></span>
- <span data-ttu-id="63cc4-158">Livelli di volume reimpostati</span><span class="sxs-lookup"><span data-stu-id="63cc4-158">Reset volume levels</span></span>
- <span data-ttu-id="63cc4-159">Larghezza della barra laterale reimpostata</span><span class="sxs-lookup"><span data-stu-id="63cc4-159">Reset sidebar width</span></span>
- <span data-ttu-id="63cc4-160">Layout della modalità tablet reimpostato</span><span class="sxs-lookup"><span data-stu-id="63cc4-160">Reset tablet mode layout</span></span>
- <span data-ttu-id="63cc4-161">Disconnettere l'utente dalle riunioni e dai file di Office 365</span><span class="sxs-lookup"><span data-stu-id="63cc4-161">Sign user out of Office 365 meetings and files</span></span>

### <span data-ttu-id="63cc4-162">Accessibilità</span><span class="sxs-lookup"><span data-stu-id="63cc4-162">Accessibility</span></span>
<span data-ttu-id="63cc4-163">Se si seleziona l'opzione **Termina sessione**, le app e le funzionalità di accessibilità vengono ripristinate alle impostazioni predefinite.</span><span class="sxs-lookup"><span data-stu-id="63cc4-163">Accessibility features and apps are returned to default settings when **End session** is selected.</span></span>
- <span data-ttu-id="63cc4-164">Filtro tasti</span><span class="sxs-lookup"><span data-stu-id="63cc4-164">Filter keys</span></span>
- <span data-ttu-id="63cc4-165">Contrasto elevato</span><span class="sxs-lookup"><span data-stu-id="63cc4-165">High contrast</span></span>
- <span data-ttu-id="63cc4-166">Tasti permanenti</span><span class="sxs-lookup"><span data-stu-id="63cc4-166">Sticky keys</span></span>
- <span data-ttu-id="63cc4-167">Segnali acustici</span><span class="sxs-lookup"><span data-stu-id="63cc4-167">Toggle keys</span></span>
- <span data-ttu-id="63cc4-168">Controllo puntatore</span><span class="sxs-lookup"><span data-stu-id="63cc4-168">Mouse keys</span></span>
- <span data-ttu-id="63cc4-169">Lente di ingrandimento</span><span class="sxs-lookup"><span data-stu-id="63cc4-169">Magnifier</span></span>
- <span data-ttu-id="63cc4-170">Assistente vocale</span><span class="sxs-lookup"><span data-stu-id="63cc4-170">Narrator</span></span>

### <span data-ttu-id="63cc4-171">Appunti</span><span class="sxs-lookup"><span data-stu-id="63cc4-171">Clipboard</span></span>
<span data-ttu-id="63cc4-172">I dati copiati negli Appunti durante la sessione vengono cancellati.</span><span class="sxs-lookup"><span data-stu-id="63cc4-172">The clipboard is cleared to remove data that was copied to the clipboard during the session.</span></span> 

## <span data-ttu-id="63cc4-173">Domande frequenti</span><span class="sxs-lookup"><span data-stu-id="63cc4-173">Frequently asked questions</span></span>
**<span data-ttu-id="63cc4-174">Cosa accade se mi dimentico di toccare Termina sessione al termine di una riunione e, in seguito, qualcun altro usa Surface Hub?</span><span class="sxs-lookup"><span data-stu-id="63cc4-174">What happens if I forget to tap End session at the end of a meeting, and someone else uses the Surface Hub later?</span></span>**<br>
<span data-ttu-id="63cc4-175">Surface Hub rimuove i contenuti di una riunione solo quando gli utenti toccano **Termina sessione**.</span><span class="sxs-lookup"><span data-stu-id="63cc4-175">Surface Hub only cleans up meeting content when users tap **End session**.</span></span> <span data-ttu-id="63cc4-176">Se termini la riunione senza avere toccato **Termina sessione**, il dispositivo tornerà alla schermata iniziale dopo alcuni minuti.</span><span class="sxs-lookup"><span data-stu-id="63cc4-176">If you leave the meeting without tapping **End session**, the device will return to the welcome screen after some time.</span></span> <span data-ttu-id="63cc4-177">Dalla schermata iniziale gli utenti hanno la possibilità di riprendere la sessione precedente o di avviarne una nuova.</span><span class="sxs-lookup"><span data-stu-id="63cc4-177">From the welcome screen, users have the option to resume the previous session or start a new one.</span></span> <span data-ttu-id="63cc4-178">È inoltre possibile disattivare la capacità di riprendere una sessione se **Termina sessione** non viene premuto.</span><span class="sxs-lookup"><span data-stu-id="63cc4-178">You can also disable the ability to resume a session if **End session** is not pressed.</span></span>

**<span data-ttu-id="63cc4-179">I documenti possono essere recuperati?</span><span class="sxs-lookup"><span data-stu-id="63cc4-179">Are documents recoverable?</span></span>**<br> <span data-ttu-id="63cc4-180">Se selezioni l'opzione **Termina sessione**, i file vengono rimossi dal disco fisso come qualsiasi altro dato eliminato da un'unità disco rigido.</span><span class="sxs-lookup"><span data-stu-id="63cc4-180">Removing files from the hard drive when **End session** is selected is just like any other file deletion from a hard disk drive.</span></span> <span data-ttu-id="63cc4-181">Per recuperarli dal disco rigido è necessario un software di terze parti, ma il recupero dei file non è una funzionalità supportata in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="63cc4-181">Third-party software might be able to recover data from the hard disk drive, but file recovery is not a supported feature on Surface Hub.</span></span> <span data-ttu-id="63cc4-182">Per evitare la perdita di dati, salva sempre i dati di cui hai bisogno prima di terminare una riunione.</span><span class="sxs-lookup"><span data-stu-id="63cc4-182">To prevent data loss, always save the data you need before leaving a meeting.</span></span>

**<span data-ttu-id="63cc4-183">Le azioni di azzeramento generate dall'opzione Termina sessione sono conformi allo standard di pulizia e sanificazione DoD 5220.22-M, definito dal Dipartimento della Difesa statunitense?</span><span class="sxs-lookup"><span data-stu-id="63cc4-183">Do the clean-up actions from End session comply with the US Department of Defense clearing and sanitizing standard: DoD 5220.22-M?</span></span>**<br>
<span data-ttu-id="63cc4-184">No.</span><span class="sxs-lookup"><span data-stu-id="63cc4-184">No.</span></span> <span data-ttu-id="63cc4-185">Le azioni di azzeramento generate dall'opzione **Termina sessione** non sono attualmente conformi a questo standard.</span><span class="sxs-lookup"><span data-stu-id="63cc4-185">Currently, the clean-up actions from **End session** do not comply with this standard.</span></span>  
  

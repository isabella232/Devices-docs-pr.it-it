---
title: Uso di un sistema di controllo della sala (Surface Hub)
description: Puoi usare i sistemi di controllo della sala con il tuo dispositivo Microsoft Surface Hub.
ms.assetid: DC365002-6B35-45C5-A2B8-3E1EB0CB8B50
ms.reviewer: ''
manager: laurawi
keywords: sistema di controllo della sala, Surface Hub
ms.prod: surface-hub
ms.sitesec: library
author: dansimp
ms.author: dansimp
ms.topic: article
ms.date: 07/27/2017
ms.localizationpriority: medium
ms.openlocfilehash: 0e3b1706e58edb6e37156eda8d06fb0faefa4c91
ms.sourcegitcommit: 109d1d7608ac4667564fa5369e8722e569b8ea36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "10832654"
---
# <span data-ttu-id="70ae3-104">Uso di un sistema di controllo della sala (Surface Hub)</span><span class="sxs-lookup"><span data-stu-id="70ae3-104">Using a room control system (Surface Hub)</span></span>


<span data-ttu-id="70ae3-105">Puoi usare i sistemi di controllo della sala con il tuo dispositivo Microsoft Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="70ae3-105">Room control systems can be used with your Microsoft Surface Hub.</span></span>

<span data-ttu-id="70ae3-106">L'uso di un sistema di controllo della sala con il dispositivo Surface Hub implica la connessione dell'hardware di controllo della sala a Surface Hub, generalmente tramite la porta seriale RJ11 nella parte inferiore di Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="70ae3-106">Using a room control system with your Surface Hub involves connecting room control hardware to the Surface Hub, usually through the RJ11 serial port on the bottom of the Surface Hub.</span></span>

## <a name="terminal-settings"></a><span data-ttu-id="70ae3-107">Impostazioni del terminale</span><span class="sxs-lookup"><span data-stu-id="70ae3-107">Terminal settings</span></span>

<span data-ttu-id="70ae3-108">Per la connessione al pannello di controllo di un sistema di controllo della sala, non è necessario configurare le impostazioni del terminale in Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="70ae3-108">To connect to a room control system control panel, you don't need to configure any terminal settings on the Surface Hub.</span></span> <span data-ttu-id="70ae3-109">Se vuoi connettere un PC o un portatile al dispositivo Surface Hub e inviare comandi seriali da Surface Hub, puoi usare un programma di emulazione del terminale come Tera Term o PuTTY.</span><span class="sxs-lookup"><span data-stu-id="70ae3-109">If you want to connect a PC or laptop to your Surface Hub and send serial commands from the Surface Hub, you can use a terminal emulator program like Tera Term or PuTTY.</span></span> 

| <span data-ttu-id="70ae3-110">Impostazione</span><span class="sxs-lookup"><span data-stu-id="70ae3-110">Setting</span></span> | <span data-ttu-id="70ae3-111">Valore</span><span class="sxs-lookup"><span data-stu-id="70ae3-111">Value</span></span> |
| --- | --- |
| <span data-ttu-id="70ae3-112">Velocità in baud</span><span class="sxs-lookup"><span data-stu-id="70ae3-112">Baud rate</span></span> | <span data-ttu-id="70ae3-113">115200</span><span class="sxs-lookup"><span data-stu-id="70ae3-113">115200</span></span> |
| <span data-ttu-id="70ae3-114">Bit di dati</span><span class="sxs-lookup"><span data-stu-id="70ae3-114">Data bits</span></span> | <span data-ttu-id="70ae3-115">8</span><span class="sxs-lookup"><span data-stu-id="70ae3-115">8</span></span> | 
| <span data-ttu-id="70ae3-116">Bit di stop</span><span class="sxs-lookup"><span data-stu-id="70ae3-116">Stop bits</span></span> | <span data-ttu-id="70ae3-117">1</span><span class="sxs-lookup"><span data-stu-id="70ae3-117">1</span></span> |
| <span data-ttu-id="70ae3-118">Parità</span><span class="sxs-lookup"><span data-stu-id="70ae3-118">Parity</span></span> | <span data-ttu-id="70ae3-119">nessuna</span><span class="sxs-lookup"><span data-stu-id="70ae3-119">none</span></span> |
| <span data-ttu-id="70ae3-120">Controllo di flusso</span><span class="sxs-lookup"><span data-stu-id="70ae3-120">Flow control</span></span> | <span data-ttu-id="70ae3-121">nessuno</span><span class="sxs-lookup"><span data-stu-id="70ae3-121">none</span></span> |
| <span data-ttu-id="70ae3-122">Avanzamento riga</span><span class="sxs-lookup"><span data-stu-id="70ae3-122">Line feed</span></span> | <span data-ttu-id="70ae3-123">ogni ritorno a capo</span><span class="sxs-lookup"><span data-stu-id="70ae3-123">every carriage return</span></span> |
 

## <a name="wiring-diagram"></a><span data-ttu-id="70ae3-124">Diagramma di collegamento</span><span class="sxs-lookup"><span data-stu-id="70ae3-124">Wiring diagram</span></span>

<span data-ttu-id="70ae3-125">Puoi usare un connettore RJ-11 (6P6C) standard per la connessione della porta seriale di Surface Hub a un sistema di controllo della sala.</span><span class="sxs-lookup"><span data-stu-id="70ae3-125">You can use a standard RJ-11 (6P6C) connector to connect the Surface Hub serial port to a room control system.</span></span> <span data-ttu-id="70ae3-126">Si tratta del metodo consigliato.</span><span class="sxs-lookup"><span data-stu-id="70ae3-126">This is the recommended method.</span></span> <span data-ttu-id="70ae3-127">Anche se sconsigliato, puoi usare in alternativa un cavo a 4 conduttori RJ-11.</span><span class="sxs-lookup"><span data-stu-id="70ae3-127">You can also use an RJ-11 4-conductor cable, but we do not recommend this method.</span></span>

<span data-ttu-id="70ae3-128">Questo diagramma mostra la configurazione corretta dei pin per un cavo da RJ-11 (6P6C) a DB9.</span><span class="sxs-lookup"><span data-stu-id="70ae3-128">This diagram shows the correct pinout used for an RJ-11 (6P6C) to DB9 cable.</span></span>

![Immagine che mostra il diagramma di collegamento.](images/room-control-wiring-diagram.png)

## <a name="command-sets"></a><span data-ttu-id="70ae3-130">Set di comandi</span><span class="sxs-lookup"><span data-stu-id="70ae3-130">Command sets</span></span>

<span data-ttu-id="70ae3-131">I sistemi di controllo della sala usano scenari di sale riunioni comuni per i comandi.</span><span class="sxs-lookup"><span data-stu-id="70ae3-131">Room control systems use common meeting-room scenarios for commands.</span></span> <span data-ttu-id="70ae3-132">I comandi provengono dal sistema di controllo della sala e vengono comunicati tramite una connessione seriale a un dispositivo Surface Hub.</span><span class="sxs-lookup"><span data-stu-id="70ae3-132">Commands originate from the room control system, and are communicated over a serial connection to a Surface Hub.</span></span> <span data-ttu-id="70ae3-133">I comandi sono basati su ASCII e il dispositivo Surface Hub riconoscerà le modifiche dello stato.</span><span class="sxs-lookup"><span data-stu-id="70ae3-133">Commands are ASCII based, and the Surface Hub will acknowledge when state changes occur.</span></span>

<span data-ttu-id="70ae3-134">Sono disponibili i modificatori di comando seguenti.</span><span class="sxs-lookup"><span data-stu-id="70ae3-134">The following command modifiers are available.</span></span> <span data-ttu-id="70ae3-135">I comandi terminano con un carattere di nuova riga (\n).</span><span class="sxs-lookup"><span data-stu-id="70ae3-135">Commands terminate with a new line character (\n).</span></span> <span data-ttu-id="70ae3-136">Le risposte alle modifiche dello stato non attivate direttamente da un comando della porta di gestione possono arrivare in qualsiasi momento.</span><span class="sxs-lookup"><span data-stu-id="70ae3-136">Responses can come at any time in response to state changes not triggered directly by a management port command.</span></span>

| <span data-ttu-id="70ae3-137">Modificatore</span><span class="sxs-lookup"><span data-stu-id="70ae3-137">Modifier</span></span> | <span data-ttu-id="70ae3-138">Risultato</span><span class="sxs-lookup"><span data-stu-id="70ae3-138">Result</span></span> |
| --- | --- |
| + | <span data-ttu-id="70ae3-139">Consente di incrementare un valore</span><span class="sxs-lookup"><span data-stu-id="70ae3-139">Increment a value</span></span> |
| - | <span data-ttu-id="70ae3-140">Consente di ridurre un valore</span><span class="sxs-lookup"><span data-stu-id="70ae3-140">Decrease a value</span></span> |
| = | <span data-ttu-id="70ae3-141">Consente di impostare un valore discreto</span><span class="sxs-lookup"><span data-stu-id="70ae3-141">Set a discrete value</span></span> |
| <span data-ttu-id="70ae3-142">?</span><span class="sxs-lookup"><span data-stu-id="70ae3-142">?</span></span> | <span data-ttu-id="70ae3-143">Consente di richiedere un valore corrente</span><span class="sxs-lookup"><span data-stu-id="70ae3-143">Queries for a current value</span></span> |
 

## <a name="power"></a><span data-ttu-id="70ae3-144">Alimentazione</span><span class="sxs-lookup"><span data-stu-id="70ae3-144">Power</span></span>

<span data-ttu-id="70ae3-145">Surface Hub può trovarsi in uno degli stati di alimentazione seguenti.</span><span class="sxs-lookup"><span data-stu-id="70ae3-145">Surface Hub can be in one of these power states.</span></span>

| <span data-ttu-id="70ae3-146">Stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-146">State</span></span> | <span data-ttu-id="70ae3-147">Stato Energy Star</span><span class="sxs-lookup"><span data-stu-id="70ae3-147">Energy Star state</span></span>| <span data-ttu-id="70ae3-148">Descrizione</span><span class="sxs-lookup"><span data-stu-id="70ae3-148">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-149">0</span><span class="sxs-lookup"><span data-stu-id="70ae3-149">0</span></span> | <span data-ttu-id="70ae3-150">S5</span><span class="sxs-lookup"><span data-stu-id="70ae3-150">S5</span></span> | <span data-ttu-id="70ae3-151">Inattivo</span><span class="sxs-lookup"><span data-stu-id="70ae3-151">Off</span></span> |
| <span data-ttu-id="70ae3-152">1</span><span class="sxs-lookup"><span data-stu-id="70ae3-152">1</span></span> | - | <span data-ttu-id="70ae3-153">Acceso (indeterminato)</span><span class="sxs-lookup"><span data-stu-id="70ae3-153">Power up (indeterminate)</span></span> |
| <span data-ttu-id="70ae3-154">2</span><span class="sxs-lookup"><span data-stu-id="70ae3-154">2</span></span> | <span data-ttu-id="70ae3-155">S3</span><span class="sxs-lookup"><span data-stu-id="70ae3-155">S3</span></span> | <span data-ttu-id="70ae3-156">Sospensione</span><span class="sxs-lookup"><span data-stu-id="70ae3-156">Sleep</span></span> |
| <span data-ttu-id="70ae3-157">5</span><span class="sxs-lookup"><span data-stu-id="70ae3-157">5</span></span> | <span data-ttu-id="70ae3-158">S0</span><span class="sxs-lookup"><span data-stu-id="70ae3-158">S0</span></span> | <span data-ttu-id="70ae3-159">Pronto</span><span class="sxs-lookup"><span data-stu-id="70ae3-159">Ready</span></span> |


<span data-ttu-id="70ae3-160">In modalità PC di sostituzione, gli stati di alimentazione sono solo Pronto e Inattivo e comportano solo la modifica dello schermo.</span><span class="sxs-lookup"><span data-stu-id="70ae3-160">In Replacement PC mode, the power states are only Ready and Off and only change the display.</span></span> <span data-ttu-id="70ae3-161">La porta di gestione non può essere usata per alimentare il PC di sostituzione.</span><span class="sxs-lookup"><span data-stu-id="70ae3-161">The management port can't be used to power on the replacement PC.</span></span> 

| <span data-ttu-id="70ae3-162">Stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-162">State</span></span> | <span data-ttu-id="70ae3-163">Stato Energy Star</span><span class="sxs-lookup"><span data-stu-id="70ae3-163">Energy Star state</span></span>| <span data-ttu-id="70ae3-164">Descrizione</span><span class="sxs-lookup"><span data-stu-id="70ae3-164">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-165">0</span><span class="sxs-lookup"><span data-stu-id="70ae3-165">0</span></span> | <span data-ttu-id="70ae3-166">S5</span><span class="sxs-lookup"><span data-stu-id="70ae3-166">S5</span></span> | <span data-ttu-id="70ae3-167">Disattivato</span><span class="sxs-lookup"><span data-stu-id="70ae3-167">Off</span></span> |
| <span data-ttu-id="70ae3-168">5</span><span class="sxs-lookup"><span data-stu-id="70ae3-168">5</span></span> | <span data-ttu-id="70ae3-169">S0</span><span class="sxs-lookup"><span data-stu-id="70ae3-169">S0</span></span> | <span data-ttu-id="70ae3-170">Pronto</span><span class="sxs-lookup"><span data-stu-id="70ae3-170">Ready</span></span> |

<span data-ttu-id="70ae3-171">Per un dispositivo di controllo, qualsiasi valore diverso da 5/Pronto deve essere considerato corrispondente a Inattivo.</span><span class="sxs-lookup"><span data-stu-id="70ae3-171">For a control device, anything other than 5 / Ready should be considered off.</span></span> <span data-ttu-id="70ae3-172">Ogni comando PowerOn genera due modifiche e risposte di stato.</span><span class="sxs-lookup"><span data-stu-id="70ae3-172">Each PowerOn command results in two state changes and responses.</span></span> 

| <span data-ttu-id="70ae3-173">Comando</span><span class="sxs-lookup"><span data-stu-id="70ae3-173">Command</span></span> | <span data-ttu-id="70ae3-174">Modifica di stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-174">State change</span></span>| <span data-ttu-id="70ae3-175">Risposta</span><span class="sxs-lookup"><span data-stu-id="70ae3-175">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-176">PowerOn</span><span class="sxs-lookup"><span data-stu-id="70ae3-176">PowerOn</span></span> | <span data-ttu-id="70ae3-177">Il dispositivo si accende (schermo + PC).</span><span class="sxs-lookup"><span data-stu-id="70ae3-177">Device turns on (display + PC).</span></span></br></br><span data-ttu-id="70ae3-178">Il servizio PC indica al controller SMC che il PC è pronto.</span><span class="sxs-lookup"><span data-stu-id="70ae3-178">PC service notifies SMC that the PC is ready.</span></span> |  <span data-ttu-id="70ae3-179">Power=0</span><span class="sxs-lookup"><span data-stu-id="70ae3-179">Power=0</span></span></br></br><span data-ttu-id="70ae3-180">Power=5</span><span class="sxs-lookup"><span data-stu-id="70ae3-180">Power=5</span></span> |
| <span data-ttu-id="70ae3-181">PowerOff</span><span class="sxs-lookup"><span data-stu-id="70ae3-181">PowerOff</span></span> | <span data-ttu-id="70ae3-182">Il dispositivo passa allo stato ambientale (PC acceso, schermo oscurato).</span><span class="sxs-lookup"><span data-stu-id="70ae3-182">Device transitions to ambient state (PC on, display dim).</span></span> |  <span data-ttu-id="70ae3-183">Power=0</span><span class="sxs-lookup"><span data-stu-id="70ae3-183">Power=0</span></span> |
| <span data-ttu-id="70ae3-184">Power?</span><span class="sxs-lookup"><span data-stu-id="70ae3-184">Power?</span></span> |  <span data-ttu-id="70ae3-185">Il controller SMC segnala l'ultimo stato di alimentazione noto.</span><span class="sxs-lookup"><span data-stu-id="70ae3-185">SMC reports the last-known power state.</span></span> |  <span data-ttu-id="70ae3-186">Power=<#></span><span class="sxs-lookup"><span data-stu-id="70ae3-186">Power=<#></span></span> |



## <a name="brightness"></a><span data-ttu-id="70ae3-187">Luminosità</span><span class="sxs-lookup"><span data-stu-id="70ae3-187">Brightness</span></span>

<span data-ttu-id="70ae3-188">Il livello di luminosità corrente è compreso nell'intervallo da 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="70ae3-188">The current brightness level is a range from 0 to 100.</span></span>

<span data-ttu-id="70ae3-189">Le modifiche ai livelli di luminosità possono essere inviate da un sistema di controllo della sala o da un altro sistema.</span><span class="sxs-lookup"><span data-stu-id="70ae3-189">Changes to brightness levels can be sent by a room control system, or other system.</span></span>

| <span data-ttu-id="70ae3-190">Comando</span><span class="sxs-lookup"><span data-stu-id="70ae3-190">Command</span></span> | <span data-ttu-id="70ae3-191">Modifica di stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-191">State change</span></span> |<span data-ttu-id="70ae3-192">Risposta</span><span class="sxs-lookup"><span data-stu-id="70ae3-192">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-193">Brightness+</span><span class="sxs-lookup"><span data-stu-id="70ae3-193">Brightness+</span></span> | <span data-ttu-id="70ae3-194">Il controller SMC (System Management Controller) invia il comando per aumentare la luminosità.</span><span class="sxs-lookup"><span data-stu-id="70ae3-194">System management controller (SMC) sends the brightness up command.</span></span></br></br><span data-ttu-id="70ae3-195">Il servizio PC nel sistema di controllo della sala invia notifica al controller SMC del nuovo livello di luminosità.</span><span class="sxs-lookup"><span data-stu-id="70ae3-195">PC service on the room control system notifies SMC of new brightness level.</span></span> |  <span data-ttu-id="70ae3-196">Brightness = 51</span><span class="sxs-lookup"><span data-stu-id="70ae3-196">Brightness = 51</span></span> |
| <span data-ttu-id="70ae3-197">Brightness-</span><span class="sxs-lookup"><span data-stu-id="70ae3-197">Brightness-</span></span> |  <span data-ttu-id="70ae3-198">Il controller SMC invia il comando per ridurre la luminosità.</span><span class="sxs-lookup"><span data-stu-id="70ae3-198">SMC sends the brightness down command.</span></span></br></br><span data-ttu-id="70ae3-199">Il servizio PC invia notifica al controller SMC del nuovo livello di luminosità.</span><span class="sxs-lookup"><span data-stu-id="70ae3-199">PC service notifies SMC of new brightness level.</span></span> | <span data-ttu-id="70ae3-200">Brightness = 50</span><span class="sxs-lookup"><span data-stu-id="70ae3-200">Brightness = 50</span></span> |

## <a name="volume"></a><span data-ttu-id="70ae3-201">Volume</span><span class="sxs-lookup"><span data-stu-id="70ae3-201">Volume</span></span>

<span data-ttu-id="70ae3-202">Il livello di volume corrente è compreso nell'intervallo da 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="70ae3-202">The current volume level is a range from 0 to 100.</span></span>

<span data-ttu-id="70ae3-203">Le modifiche ai livelli del volume possono essere inviate da un sistema di controllo della sala o da un altro sistema.</span><span class="sxs-lookup"><span data-stu-id="70ae3-203">Changes to volume levels can be sent by a room control system, or other system.</span></span>

>[!NOTE]
><span data-ttu-id="70ae3-204">Il comando Volume consente di controllare solo il volume per la modalità PC di sostituzione o integrato e non dalle [origini Guest](connect-and-display-with-surface-hub.md).</span><span class="sxs-lookup"><span data-stu-id="70ae3-204">The Volume command will only control the volume for embedded or Replacement PC mode, not from [Guest sources](connect-and-display-with-surface-hub.md).</span></span>

| <span data-ttu-id="70ae3-205">Comando</span><span class="sxs-lookup"><span data-stu-id="70ae3-205">Command</span></span> | <span data-ttu-id="70ae3-206">Modifica di stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-206">State change</span></span> | <span data-ttu-id="70ae3-207">Risposta</span><span class="sxs-lookup"><span data-stu-id="70ae3-207">Response</span></span></br><span data-ttu-id="70ae3-208">(Solo in [modalità PC di sostituzione](connect-and-display-with-surface-hub.md#replacement-pc-mode))</span><span class="sxs-lookup"><span data-stu-id="70ae3-208">(On in [Replacement PC mode](connect-and-display-with-surface-hub.md#replacement-pc-mode))</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-209">Volume+</span><span class="sxs-lookup"><span data-stu-id="70ae3-209">Volume+</span></span> |  <span data-ttu-id="70ae3-210">Il controller SMC invia il comando per aumentare il volume.</span><span class="sxs-lookup"><span data-stu-id="70ae3-210">SMC sends the volume up command.</span></span></br></br><span data-ttu-id="70ae3-211">Il servizio PC invia notifica al controller SMC del nuovo livello del volume.</span><span class="sxs-lookup"><span data-stu-id="70ae3-211">PC service notifies SMC of new volume level.</span></span> |  <span data-ttu-id="70ae3-212">Volume = 51</span><span class="sxs-lookup"><span data-stu-id="70ae3-212">Volume = 51</span></span> |
| <span data-ttu-id="70ae3-213">Volume-</span><span class="sxs-lookup"><span data-stu-id="70ae3-213">Volume-</span></span> |  <span data-ttu-id="70ae3-214">Il controller SMC invia il comando per ridurre il volume.</span><span class="sxs-lookup"><span data-stu-id="70ae3-214">SMC sends the volume down command.</span></span></br></br><span data-ttu-id="70ae3-215">Il servizio PC invia notifica al controller SMC del nuovo livello del volume.</span><span class="sxs-lookup"><span data-stu-id="70ae3-215">PC service notifies SMC of new volume level.</span></span> |  <span data-ttu-id="70ae3-216">Volume = 50</span><span class="sxs-lookup"><span data-stu-id="70ae3-216">Volume = 50</span></span> |


 

## <a name="mute-for-audio"></a><span data-ttu-id="70ae3-217">Disattivazione dell'audio</span><span class="sxs-lookup"><span data-stu-id="70ae3-217">Mute for audio</span></span>

<span data-ttu-id="70ae3-218">L'audio può essere disattivato.</span><span class="sxs-lookup"><span data-stu-id="70ae3-218">Audio can be muted.</span></span>

| <span data-ttu-id="70ae3-219">Comando</span><span class="sxs-lookup"><span data-stu-id="70ae3-219">Command</span></span> | <span data-ttu-id="70ae3-220">Modifica di stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-220">State change</span></span> | <span data-ttu-id="70ae3-221">Risposta</span><span class="sxs-lookup"><span data-stu-id="70ae3-221">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-222">AudioMute+</span><span class="sxs-lookup"><span data-stu-id="70ae3-222">AudioMute+</span></span> |  <span data-ttu-id="70ae3-223">Il controller SMC invia il comando di disattivazione dell'audio.</span><span class="sxs-lookup"><span data-stu-id="70ae3-223">SMC sends the audio mute command.</span></span></br></br><span data-ttu-id="70ae3-224">Il servizio PC invia notifica al controller SMC della disattivazione dell'audio.</span><span class="sxs-lookup"><span data-stu-id="70ae3-224">PC service notifies SMC that audio is muted.</span></span> |  <span data-ttu-id="70ae3-225">nessuna</span><span class="sxs-lookup"><span data-stu-id="70ae3-225">none</span></span> |


 

## <a name="video-source"></a><span data-ttu-id="70ae3-226">Origine video</span><span class="sxs-lookup"><span data-stu-id="70ae3-226">Video source</span></span>

<span data-ttu-id="70ae3-227">Possono essere usate diverse origini di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="70ae3-227">Several display sources can be used.</span></span>

| <span data-ttu-id="70ae3-228">Stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-228">State</span></span> | <span data-ttu-id="70ae3-229">Descrizione</span><span class="sxs-lookup"><span data-stu-id="70ae3-229">Description</span></span> | 
| --- | --- |
| <span data-ttu-id="70ae3-230">0</span><span class="sxs-lookup"><span data-stu-id="70ae3-230">0</span></span> |  <span data-ttu-id="70ae3-231">Onboard PC</span><span class="sxs-lookup"><span data-stu-id="70ae3-231">Onboard PC</span></span> |
| <span data-ttu-id="70ae3-232">1</span><span class="sxs-lookup"><span data-stu-id="70ae3-232">1</span></span> |  <span data-ttu-id="70ae3-233">DisplayPort</span><span class="sxs-lookup"><span data-stu-id="70ae3-233">DisplayPort</span></span> |
| <span data-ttu-id="70ae3-234">2</span><span class="sxs-lookup"><span data-stu-id="70ae3-234">2</span></span> |  <span data-ttu-id="70ae3-235">HDMI</span><span class="sxs-lookup"><span data-stu-id="70ae3-235">HDMI</span></span> |
| <span data-ttu-id="70ae3-236">3</span><span class="sxs-lookup"><span data-stu-id="70ae3-236">3</span></span> |  <span data-ttu-id="70ae3-237">VGA</span><span class="sxs-lookup"><span data-stu-id="70ae3-237">VGA</span></span> |


 

<span data-ttu-id="70ae3-238">Le modifiche all'origine di visualizzazione possono essere inviate da un sistema di controllo della sala o da un altro sistema.</span><span class="sxs-lookup"><span data-stu-id="70ae3-238">Changes to display source can be sent by a room control system, or other system.</span></span>

| <span data-ttu-id="70ae3-239">Comando</span><span class="sxs-lookup"><span data-stu-id="70ae3-239">Command</span></span> | <span data-ttu-id="70ae3-240">Modifica di stato</span><span class="sxs-lookup"><span data-stu-id="70ae3-240">State change</span></span> | <span data-ttu-id="70ae3-241">Risposta</span><span class="sxs-lookup"><span data-stu-id="70ae3-241">Response</span></span> |
| --- | --- | --- |
| <span data-ttu-id="70ae3-242">Source=#</span><span class="sxs-lookup"><span data-stu-id="70ae3-242">Source=#</span></span> |  <span data-ttu-id="70ae3-243">Il controller SMC passa all'origine desiderata.</span><span class="sxs-lookup"><span data-stu-id="70ae3-243">SMC changes to the desired source.</span></span></br></br><span data-ttu-id="70ae3-244">Il servizio PC invia notifica al controller SMC del cambiamento dell'origine di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="70ae3-244">PC service notifies SMC that the display source has switched.</span></span> |  <span data-ttu-id="70ae3-245">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="70ae3-245">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="70ae3-246">Source+</span><span class="sxs-lookup"><span data-stu-id="70ae3-246">Source+</span></span> |  <span data-ttu-id="70ae3-247">Il controller SMC passa all'origine di input attiva successiva.</span><span class="sxs-lookup"><span data-stu-id="70ae3-247">SMC cycles to the next active input source.</span></span></br></br><span data-ttu-id="70ae3-248">Il servizio PC invia notifica al controller SMC dell'origine di input corrente.</span><span class="sxs-lookup"><span data-stu-id="70ae3-248">PC service notifies SMC of the current input source.</span></span> |  <span data-ttu-id="70ae3-249">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="70ae3-249">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="70ae3-250">Source-</span><span class="sxs-lookup"><span data-stu-id="70ae3-250">Source-</span></span> | <span data-ttu-id="70ae3-251">Il controller SMC passa all'origine di input attiva precedente.</span><span class="sxs-lookup"><span data-stu-id="70ae3-251">SMC cycles to the previous active input source.</span></span></br></br><span data-ttu-id="70ae3-252">Il servizio PC invia notifica al controller SMC dell'origine di input corrente.</span><span class="sxs-lookup"><span data-stu-id="70ae3-252">PC service notifies SMC of the current input source.</span></span> |  <span data-ttu-id="70ae3-253">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="70ae3-253">Source=&lt;#&gt;</span></span> |
| <span data-ttu-id="70ae3-254">Source?</span><span class="sxs-lookup"><span data-stu-id="70ae3-254">Source?</span></span> |  <span data-ttu-id="70ae3-255">Il controller SMC richiede l'origine di input attiva al servizio PC.</span><span class="sxs-lookup"><span data-stu-id="70ae3-255">SMC queries PC service for the active input source.</span></span></br></br><span data-ttu-id="70ae3-256">Il servizio PC invia notifica al controller SMC dell'origine di input corrente.</span><span class="sxs-lookup"><span data-stu-id="70ae3-256">PC service notifies SMC of the current in;put source.</span></span> | <span data-ttu-id="70ae3-257">Source=&lt;#&gt;</span><span class="sxs-lookup"><span data-stu-id="70ae3-257">Source=&lt;#&gt;</span></span> |

## <a name="errors"></a><span data-ttu-id="70ae3-258">Errori</span><span class="sxs-lookup"><span data-stu-id="70ae3-258">Errors</span></span>

<span data-ttu-id="70ae3-259">Gli errori vengono restituiti nel formato indicato in questa tabella.</span><span class="sxs-lookup"><span data-stu-id="70ae3-259">Errors are returned following the format in this table.</span></span>

| <span data-ttu-id="70ae3-260">Errore</span><span class="sxs-lookup"><span data-stu-id="70ae3-260">Error</span></span> | <span data-ttu-id="70ae3-261">Note</span><span class="sxs-lookup"><span data-stu-id="70ae3-261">Notes</span></span> |
| --- | --- |
| <span data-ttu-id="70ae3-262">Errore: Comando sconosciuto '&lt;input&gt;'.</span><span class="sxs-lookup"><span data-stu-id="70ae3-262">Error: Unknown command '&lt;input&gt;'.</span></span> |  <span data-ttu-id="70ae3-263">L'istruzione contiene un comando iniziale sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="70ae3-263">The instruction contains an unknown initial command.</span></span> <span data-ttu-id="70ae3-264">Ad esempio, &quot;VOL+&quot; non sarebbe valido e restituirebbe &quot;Errore: Comando sconosciuto 'VOL'&quot;.</span><span class="sxs-lookup"><span data-stu-id="70ae3-264">For example, &quot;VOL+&quot; would be invalid and return &quot; Error: Unknown command 'VOL'&quot;.</span></span> |
| <span data-ttu-id="70ae3-265">Errore: Operatore sconosciuto '&lt;input&gt;'.</span><span class="sxs-lookup"><span data-stu-id="70ae3-265">Error: Unknown operator '&lt;input&gt;'.</span></span> |  <span data-ttu-id="70ae3-266">L'istruzione contiene un operatore sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="70ae3-266">The instruction contains an unknown operator.</span></span> <span data-ttu-id="70ae3-267">Ad esempio, &quot;Volume!&quot; non sarebbe valido e restituirebbe &quot; Errore: Operatore sconosciuto "!"&quot;.</span><span class="sxs-lookup"><span data-stu-id="70ae3-267">For example, &quot;Volume!&quot; would be invalid and return &quot; Error: Unknown operator '!'&quot;.</span></span> |
| <span data-ttu-id="70ae3-268">Errore: Parametro sconosciuto '&lt;input&gt;'.</span><span class="sxs-lookup"><span data-stu-id="70ae3-268">Error: Unknown parameter '&lt;input&gt;'.</span></span> |  <span data-ttu-id="70ae3-269">L'istruzione contiene un parametro sconosciuto.</span><span class="sxs-lookup"><span data-stu-id="70ae3-269">The instruction contains an unknown parameter.</span></span> <span data-ttu-id="70ae3-270">Ad esempio, &quot;Volume=abc&quot; non sarebbe valido e restituirebbe &quot;Errore: Parametro sconosciuto 'abc'&quot;.</span><span class="sxs-lookup"><span data-stu-id="70ae3-270">For example, &quot;Volume=abc&quot; would be invalid and return &quot; Error: Unknown parameter 'abc'&quot;.</span></span> |
| <span data-ttu-id="70ae3-271">Errore: Comando non disponibile in caso di disattivazione '&lt;input&gt;'.</span><span class="sxs-lookup"><span data-stu-id="70ae3-271">Error: Command not available when off '&lt;input&gt;'.</span></span> |  <span data-ttu-id="70ae3-272">Quando il dispositivo Surface Hub è disattivato, i comandi diversi da un comando di alimentazione restituiscono questo errore.</span><span class="sxs-lookup"><span data-stu-id="70ae3-272">When the Surface Hub is off, commands other than Power return this error.</span></span> <span data-ttu-id="70ae3-273">Ad esempio, &quot;Volume+&quot; non sarebbe valido e restituirebbe &quot;Errore: Comando non disponibile in caso di disattivazione 'Volume'&quot;.</span><span class="sxs-lookup"><span data-stu-id="70ae3-273">For example, &quot;Volume+&quot; would be invalid and return &quot; Error: Command not available when off 'Volume'&quot;.</span></span> |


 

## <a name="related-topics"></a><span data-ttu-id="70ae3-274">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="70ae3-274">Related topics</span></span>


[<span data-ttu-id="70ae3-275">Gestire Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="70ae3-275">Manage Microsoft Surface Hub</span></span>](manage-surface-hub.md)

[<span data-ttu-id="70ae3-276">Manuale dell'amministratore di Microsoft Surface Hub</span><span class="sxs-lookup"><span data-stu-id="70ae3-276">Microsoft Surface Hub administrator's guide</span></span>](surface-hub-administrators-guide.md)

 

 






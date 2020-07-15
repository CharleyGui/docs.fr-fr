---
title: Événements ETW de garbage collection
description: 'Affichez des informations détaillées sur garbage collection événements ETW. Les événements traités sont les suivants : GCStart_V1, GCEnd_V1, GCHeapStats_V1, GCCreateSegment_V1, etc.'
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 58ad874ef6a12c18c404640aa66577c391573534
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309740"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="4ed6a-104">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="4ed6a-104">Garbage Collection ETW Events</span></span>

<span data-ttu-id="4ed6a-105">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-105">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="4ed6a-106">Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-106">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="4ed6a-107">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="4ed6a-107">This category consists of the following events:</span></span>

- [<span data-ttu-id="4ed6a-108">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-108">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="4ed6a-109">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-109">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="4ed6a-110">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-110">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="4ed6a-111">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-111">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="4ed6a-112">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-112">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="4ed6a-113">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-113">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="4ed6a-114">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-114">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="4ed6a-115">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-115">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="4ed6a-116">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-116">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="4ed6a-117">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="4ed6a-117">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="4ed6a-118">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-118">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="4ed6a-119">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-119">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="4ed6a-120">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-120">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="4ed6a-121">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-121">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="4ed6a-122">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-122">GCStart_V1 Event</span></span>  

<span data-ttu-id="4ed6a-123">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-123">The following table shows the keyword and level.</span></span> <span data-ttu-id="4ed6a-124">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-124">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="4ed6a-125">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-125">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-126">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-126">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-127">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-127">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-128">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-128">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-129">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-129">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-130">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-130">Event</span></span>|<span data-ttu-id="4ed6a-131">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-131">Event ID</span></span>|<span data-ttu-id="4ed6a-132">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-132">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="4ed6a-133">1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-133">1</span></span>|<span data-ttu-id="4ed6a-134">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-134">A garbage collection has started.</span></span>|

<span data-ttu-id="4ed6a-135">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-135">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-136">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-136">Field name</span></span>|<span data-ttu-id="4ed6a-137">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-137">Data type</span></span>|<span data-ttu-id="4ed6a-138">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-138">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-139">Count</span><span class="sxs-lookup"><span data-stu-id="4ed6a-139">Count</span></span>|<span data-ttu-id="4ed6a-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-140">win:UInt32</span></span>|<span data-ttu-id="4ed6a-141">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-141">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="4ed6a-142">Profondeur</span><span class="sxs-lookup"><span data-stu-id="4ed6a-142">Depth</span></span>|<span data-ttu-id="4ed6a-143">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-143">win:UInt32</span></span>|<span data-ttu-id="4ed6a-144">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-144">The generation that is being collected.</span></span>|
|<span data-ttu-id="4ed6a-145">Motif</span><span class="sxs-lookup"><span data-stu-id="4ed6a-145">Reason</span></span>|<span data-ttu-id="4ed6a-146">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-146">win:UInt32</span></span>|<span data-ttu-id="4ed6a-147">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="4ed6a-147">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="4ed6a-148">0x0 – Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-148">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="4ed6a-149">0x1 – Induit.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-149">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="4ed6a-150">0x2 – Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-150">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="4ed6a-151">0x3 – Vide.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-151">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="4ed6a-152">0x4 – Allocation de tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-152">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="4ed6a-153">0x5 – Espace insuffisant (pour un tas de petits objets)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-153">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="4ed6a-154">0x6 – Espace insuffisant (pour un tas d'objets volumineux)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-154">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="4ed6a-155">0x7 – Induit mais non forcé comme blocage</span><span class="sxs-lookup"><span data-stu-id="4ed6a-155">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="4ed6a-156">Type</span><span class="sxs-lookup"><span data-stu-id="4ed6a-156">Type</span></span>|<span data-ttu-id="4ed6a-157">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-157">win:UInt32</span></span>|<span data-ttu-id="4ed6a-158">0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-158">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="4ed6a-159">0x1 – Garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-159">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="4ed6a-160">0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-160">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="4ed6a-161">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-161">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-162">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-162">win:UInt16</span></span>|<span data-ttu-id="4ed6a-163">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-163">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="4ed6a-164">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-164">GCEnd_V1 Event</span></span>

<span data-ttu-id="4ed6a-165">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-165">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-166">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-166">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-167">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-167">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-168">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-168">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-169">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-169">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-170">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-170">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-171">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-171">Event</span></span>|<span data-ttu-id="4ed6a-172">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-172">Event ID</span></span>|<span data-ttu-id="4ed6a-173">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-173">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="4ed6a-174">2</span><span class="sxs-lookup"><span data-stu-id="4ed6a-174">2</span></span>|<span data-ttu-id="4ed6a-175">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-175">The garbage collection has ended.</span></span>|

<span data-ttu-id="4ed6a-176">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-176">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-177">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-177">Field name</span></span>|<span data-ttu-id="4ed6a-178">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-178">Data type</span></span>|<span data-ttu-id="4ed6a-179">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-179">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-180">Count</span><span class="sxs-lookup"><span data-stu-id="4ed6a-180">Count</span></span>|<span data-ttu-id="4ed6a-181">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-181">win:UInt32</span></span>|<span data-ttu-id="4ed6a-182">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-182">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="4ed6a-183">Profondeur</span><span class="sxs-lookup"><span data-stu-id="4ed6a-183">Depth</span></span>|<span data-ttu-id="4ed6a-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-184">win:UInt32</span></span>|<span data-ttu-id="4ed6a-185">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-185">The generation that was collected.</span></span>|
|<span data-ttu-id="4ed6a-186">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-186">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-187">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-187">win:UInt16</span></span>|<span data-ttu-id="4ed6a-188">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-188">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="4ed6a-189">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-189">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="4ed6a-190">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-190">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-191">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-191">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-192">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-192">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-194">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-194">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-195">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-195">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-196">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-196">Event</span></span>|<span data-ttu-id="4ed6a-197">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-197">Event ID</span></span>|<span data-ttu-id="4ed6a-198">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-198">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="4ed6a-199">4</span><span class="sxs-lookup"><span data-stu-id="4ed6a-199">4</span></span>|<span data-ttu-id="4ed6a-200">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-200">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="4ed6a-201">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-201">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-202">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-202">Field name</span></span>|<span data-ttu-id="4ed6a-203">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-203">Data type</span></span>|<span data-ttu-id="4ed6a-204">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-204">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="4ed6a-205">GenerationSize0</span></span>|<span data-ttu-id="4ed6a-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-206">win:UInt64</span></span>|<span data-ttu-id="4ed6a-207">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-207">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="4ed6a-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="4ed6a-208">TotalPromotedSize0</span></span>|<span data-ttu-id="4ed6a-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-209">win:UInt64</span></span>|<span data-ttu-id="4ed6a-210">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="4ed6a-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-211">GenerationSize1</span></span>|<span data-ttu-id="4ed6a-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-212">win:UInt64</span></span>|<span data-ttu-id="4ed6a-213">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-213">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="4ed6a-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-214">TotalPromotedSize1</span></span>|<span data-ttu-id="4ed6a-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-215">win:UInt64</span></span>|<span data-ttu-id="4ed6a-216">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="4ed6a-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="4ed6a-217">GenerationSize2</span></span>|<span data-ttu-id="4ed6a-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-218">win:UInt64</span></span>|<span data-ttu-id="4ed6a-219">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-219">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="4ed6a-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="4ed6a-220">TotalPromotedSize2</span></span>|<span data-ttu-id="4ed6a-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-221">win:UInt64</span></span>|<span data-ttu-id="4ed6a-222">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="4ed6a-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="4ed6a-223">GenerationSize3</span></span>|<span data-ttu-id="4ed6a-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-224">win:UInt64</span></span>|<span data-ttu-id="4ed6a-225">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-225">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="4ed6a-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="4ed6a-226">TotalPromotedSize3</span></span>|<span data-ttu-id="4ed6a-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-227">win:UInt64</span></span>|<span data-ttu-id="4ed6a-228">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="4ed6a-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="4ed6a-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="4ed6a-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-230">win:UInt64</span></span>|<span data-ttu-id="4ed6a-231">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="4ed6a-232">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="4ed6a-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="4ed6a-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-233">win:UInt64</span></span>|<span data-ttu-id="4ed6a-234">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-234">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="4ed6a-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="4ed6a-235">PinnedObjectCount</span></span>|<span data-ttu-id="4ed6a-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-236">win:UInt32</span></span>|<span data-ttu-id="4ed6a-237">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-237">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="4ed6a-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="4ed6a-238">SinkBlockCount</span></span>|<span data-ttu-id="4ed6a-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-239">win:UInt32</span></span>|<span data-ttu-id="4ed6a-240">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-240">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="4ed6a-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="4ed6a-241">GCHandleCount</span></span>|<span data-ttu-id="4ed6a-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-242">win:UInt32</span></span>|<span data-ttu-id="4ed6a-243">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-243">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="4ed6a-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-244">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-245">win:UInt16</span></span>|<span data-ttu-id="4ed6a-246">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="4ed6a-247">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-247">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="4ed6a-248">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-248">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-249">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-249">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-250">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-250">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-251">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-251">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-252">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-252">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-253">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-253">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-254">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-254">Event</span></span>|<span data-ttu-id="4ed6a-255">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-255">Event ID</span></span>|<span data-ttu-id="4ed6a-256">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-256">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="4ed6a-257">5</span><span class="sxs-lookup"><span data-stu-id="4ed6a-257">5</span></span>|<span data-ttu-id="4ed6a-258">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-258">A new garbage collection segment has been created.</span></span> <span data-ttu-id="4ed6a-259">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-259">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="4ed6a-260">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-260">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-261">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-261">Field name</span></span>|<span data-ttu-id="4ed6a-262">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-262">Data type</span></span>|<span data-ttu-id="4ed6a-263">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-263">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-264">Adresse</span><span class="sxs-lookup"><span data-stu-id="4ed6a-264">Address</span></span>|<span data-ttu-id="4ed6a-265">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-265">win:UInt64</span></span>|<span data-ttu-id="4ed6a-266">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-266">The address of the segment.</span></span>|
|<span data-ttu-id="4ed6a-267">Taille</span><span class="sxs-lookup"><span data-stu-id="4ed6a-267">Size</span></span>|<span data-ttu-id="4ed6a-268">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-268">win:UInt64</span></span>|<span data-ttu-id="4ed6a-269">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-269">The size of the segment.</span></span>|
|<span data-ttu-id="4ed6a-270">Type</span><span class="sxs-lookup"><span data-stu-id="4ed6a-270">Type</span></span>|<span data-ttu-id="4ed6a-271">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-271">win:UInt32</span></span>|<span data-ttu-id="4ed6a-272">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-272">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="4ed6a-273">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-273">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="4ed6a-274">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-274">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="4ed6a-275">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-275">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-276">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-276">win:UInt16</span></span>|<span data-ttu-id="4ed6a-277">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-277">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="4ed6a-278">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-278">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="4ed6a-279">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-279">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="4ed6a-280">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-280">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="4ed6a-281">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-281">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-282">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-282">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-283">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-283">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-284">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-284">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-285">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-285">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-286">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-286">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-287">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-287">Event</span></span>|<span data-ttu-id="4ed6a-288">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-288">Event ID</span></span>|<span data-ttu-id="4ed6a-289">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-289">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="4ed6a-290">6</span><span class="sxs-lookup"><span data-stu-id="4ed6a-290">6</span></span>|<span data-ttu-id="4ed6a-291">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-291">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="4ed6a-292">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-292">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-293">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-293">Field name</span></span>|<span data-ttu-id="4ed6a-294">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-294">Data type</span></span>|<span data-ttu-id="4ed6a-295">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-295">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-296">Adresse</span><span class="sxs-lookup"><span data-stu-id="4ed6a-296">Address</span></span>|<span data-ttu-id="4ed6a-297">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-297">win:UInt64</span></span>|<span data-ttu-id="4ed6a-298">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-298">The address of the segment.</span></span>|
|<span data-ttu-id="4ed6a-299">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-299">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-300">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-300">win:UInt16</span></span>|<span data-ttu-id="4ed6a-301">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-301">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="4ed6a-302">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-302">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="4ed6a-303">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-303">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-304">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-304">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-305">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-305">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-306">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-306">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-307">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-307">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-308">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-308">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-309">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-309">Event</span></span>|<span data-ttu-id="4ed6a-310">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-310">Event ID</span></span>|<span data-ttu-id="4ed6a-311">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-311">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="4ed6a-312">7</span><span class="sxs-lookup"><span data-stu-id="4ed6a-312">7</span></span>|<span data-ttu-id="4ed6a-313">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-313">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="4ed6a-314">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-314">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="4ed6a-315">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-315">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="4ed6a-316">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-316">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-317">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-317">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-318">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-318">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-319">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-319">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-320">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-320">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-321">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-321">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-322">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-322">Event</span></span>|<span data-ttu-id="4ed6a-323">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-323">Event Id</span></span>|<span data-ttu-id="4ed6a-324">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-324">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="4ed6a-325">3</span><span class="sxs-lookup"><span data-stu-id="4ed6a-325">3</span></span>|<span data-ttu-id="4ed6a-326">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-326">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="4ed6a-327">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-327">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="4ed6a-328">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-328">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="4ed6a-329">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-329">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-330">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-330">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-331">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-331">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-332">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-332">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-333">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-333">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-334">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-334">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-335">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-335">Event</span></span>|<span data-ttu-id="4ed6a-336">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-336">Event ID</span></span>|<span data-ttu-id="4ed6a-337">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-337">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="4ed6a-338">9</span><span class="sxs-lookup"><span data-stu-id="4ed6a-338">9</span></span>|<span data-ttu-id="4ed6a-339">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-339">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="4ed6a-340">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-340">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-341">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-341">Field name</span></span>|<span data-ttu-id="4ed6a-342">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-342">Data type</span></span>|<span data-ttu-id="4ed6a-343">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-343">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-344">Raison</span><span class="sxs-lookup"><span data-stu-id="4ed6a-344">Reason</span></span>|<span data-ttu-id="4ed6a-345">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-345">win:UInt16</span></span>|<span data-ttu-id="4ed6a-346">0x0 – Autre.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-346">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="4ed6a-347">0x1 – Garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-347">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="4ed6a-348">0x2 – Fermeture du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-348">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="4ed6a-349">0x3 – Pitching de code.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-349">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="4ed6a-350">0x4 – Arrêt.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-350">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="4ed6a-351">0x5 – Débogueur.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-351">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="4ed6a-352">0x6 – Préparation pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-352">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="4ed6a-353">Count</span><span class="sxs-lookup"><span data-stu-id="4ed6a-353">Count</span></span>|<span data-ttu-id="4ed6a-354">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-354">win:UInt32</span></span>|<span data-ttu-id="4ed6a-355">Nombre GC à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-355">The GC count at the time.</span></span> <span data-ttu-id="4ed6a-356">En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-356">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="4ed6a-357">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-357">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-358">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-358">win:UInt16</span></span>|<span data-ttu-id="4ed6a-359">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-359">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="4ed6a-360">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-360">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="4ed6a-361">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-361">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-362">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-362">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-363">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-363">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-364">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-364">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-365">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-365">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-366">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-366">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-367">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-367">Event</span></span>|<span data-ttu-id="4ed6a-368">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-368">Event ID</span></span>|<span data-ttu-id="4ed6a-369">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-369">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="4ed6a-370">8</span><span class="sxs-lookup"><span data-stu-id="4ed6a-370">8</span></span>|<span data-ttu-id="4ed6a-371">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-371">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="4ed6a-372">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-372">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="4ed6a-373">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="4ed6a-373">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="4ed6a-374">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-374">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-375">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-375">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-376">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-376">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-377">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-377">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-378">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-378">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-379">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-379">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-380">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-380">Event</span></span>|<span data-ttu-id="4ed6a-381">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-381">Event ID</span></span>|<span data-ttu-id="4ed6a-382">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-382">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="4ed6a-383">10</span><span class="sxs-lookup"><span data-stu-id="4ed6a-383">10</span></span>|<span data-ttu-id="4ed6a-384">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-384">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="4ed6a-385">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-385">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-386">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-386">Field name</span></span>|<span data-ttu-id="4ed6a-387">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-387">Data type</span></span>|<span data-ttu-id="4ed6a-388">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-388">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-389">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="4ed6a-389">AllocationAmount</span></span>|<span data-ttu-id="4ed6a-390">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-390">win:UInt32</span></span>|<span data-ttu-id="4ed6a-391">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-391">The allocation size, in bytes.</span></span> <span data-ttu-id="4ed6a-392">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-392">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="4ed6a-393">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-393">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="4ed6a-394">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-394">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="4ed6a-395">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="4ed6a-395">AllocationKind</span></span>|<span data-ttu-id="4ed6a-396">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-396">win:UInt32</span></span>|<span data-ttu-id="4ed6a-397">0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-397">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="4ed6a-398">0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-398">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="4ed6a-399">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-399">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-400">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-400">win:UInt16</span></span>|<span data-ttu-id="4ed6a-401">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-401">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="4ed6a-402">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-402">AllocationAmount64</span></span>|<span data-ttu-id="4ed6a-403">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="4ed6a-403">win:UInt64</span></span>|<span data-ttu-id="4ed6a-404">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-404">The allocation size, in bytes.</span></span> <span data-ttu-id="4ed6a-405">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-405">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="4ed6a-406">TypeId</span><span class="sxs-lookup"><span data-stu-id="4ed6a-406">TypeId</span></span>|<span data-ttu-id="4ed6a-407">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="4ed6a-407">win:Pointer</span></span>|<span data-ttu-id="4ed6a-408">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-408">The address of the MethodTable.</span></span> <span data-ttu-id="4ed6a-409">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-409">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="4ed6a-410">TypeName</span><span class="sxs-lookup"><span data-stu-id="4ed6a-410">TypeName</span></span>|<span data-ttu-id="4ed6a-411">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="4ed6a-411">win:UnicodeString</span></span>|<span data-ttu-id="4ed6a-412">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-412">The name of the type that was allocated.</span></span> <span data-ttu-id="4ed6a-413">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="4ed6a-413">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="4ed6a-414">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="4ed6a-414">HeapIndex</span></span>|<span data-ttu-id="4ed6a-415">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-415">win:UInt32</span></span>|<span data-ttu-id="4ed6a-416">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-416">The heap where the object was allocated.</span></span> <span data-ttu-id="4ed6a-417">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-417">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="4ed6a-418">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-418">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="4ed6a-419">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-419">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-420">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-420">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-421">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-421">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-422">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-422">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-423">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-423">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-424">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-424">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-425">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-425">Event</span></span>|<span data-ttu-id="4ed6a-426">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-426">Event ID</span></span>|<span data-ttu-id="4ed6a-427">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-427">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="4ed6a-428">14</span><span class="sxs-lookup"><span data-stu-id="4ed6a-428">14</span></span>|<span data-ttu-id="4ed6a-429">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-429">The start of running finalizers.</span></span>|

<span data-ttu-id="4ed6a-430">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-430">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="4ed6a-431">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-431">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="4ed6a-432">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-432">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-433">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-433">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-434">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-434">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-435">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-435">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-436">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-436">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-437">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-437">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-438">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-438">Event</span></span>|<span data-ttu-id="4ed6a-439">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-439">Event ID</span></span>|<span data-ttu-id="4ed6a-440">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-440">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="4ed6a-441">13</span><span class="sxs-lookup"><span data-stu-id="4ed6a-441">13</span></span>|<span data-ttu-id="4ed6a-442">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-442">The end of running finalizers.</span></span>|

<span data-ttu-id="4ed6a-443">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-443">The following table shows the event data:</span></span>

|<span data-ttu-id="4ed6a-444">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="4ed6a-444">Field name</span></span>|<span data-ttu-id="4ed6a-445">Type de données</span><span class="sxs-lookup"><span data-stu-id="4ed6a-445">Data type</span></span>|<span data-ttu-id="4ed6a-446">Description</span><span class="sxs-lookup"><span data-stu-id="4ed6a-446">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="4ed6a-447">Count</span><span class="sxs-lookup"><span data-stu-id="4ed6a-447">Count</span></span>|<span data-ttu-id="4ed6a-448">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4ed6a-448">win:UInt32</span></span>|<span data-ttu-id="4ed6a-449">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-449">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="4ed6a-450">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4ed6a-450">ClrInstanceID</span></span>|<span data-ttu-id="4ed6a-451">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="4ed6a-451">win:UInt16</span></span>|<span data-ttu-id="4ed6a-452">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-452">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="4ed6a-453">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-453">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="4ed6a-454">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-454">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-455">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-455">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-456">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-456">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-457">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-457">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-458">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-458">Informational (4)</span></span>|
|<span data-ttu-id="4ed6a-459">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-459">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4ed6a-460">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-460">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-461">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-461">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-462">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-462">Event</span></span>|<span data-ttu-id="4ed6a-463">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-463">Event ID</span></span>|<span data-ttu-id="4ed6a-464">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-464">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="4ed6a-465">11</span><span class="sxs-lookup"><span data-stu-id="4ed6a-465">11</span></span>|<span data-ttu-id="4ed6a-466">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-466">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="4ed6a-467">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-467">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="4ed6a-468">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="4ed6a-468">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="4ed6a-469">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-469">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="4ed6a-470">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-470">Keyword for raising the event</span></span>|<span data-ttu-id="4ed6a-471">Level</span><span class="sxs-lookup"><span data-stu-id="4ed6a-471">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="4ed6a-472">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-472">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="4ed6a-473">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-473">Informational (4)</span></span>|
|<span data-ttu-id="4ed6a-474">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-474">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="4ed6a-475">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="4ed6a-475">Informational (4)</span></span>|

<span data-ttu-id="4ed6a-476">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-476">The following table shows the event information:</span></span>

|<span data-ttu-id="4ed6a-477">Événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-477">Event</span></span>|<span data-ttu-id="4ed6a-478">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-478">Event ID</span></span>|<span data-ttu-id="4ed6a-479">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="4ed6a-479">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="4ed6a-480">12</span><span class="sxs-lookup"><span data-stu-id="4ed6a-480">12</span></span>|<span data-ttu-id="4ed6a-481">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-481">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="4ed6a-482">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="4ed6a-482">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ed6a-483">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ed6a-483">See also</span></span>

- [<span data-ttu-id="4ed6a-484">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="4ed6a-484">CLR ETW Events</span></span>](clr-etw-events.md)

---
title: Événements ETW de garbage collection
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd4a4699f115c5b134ea60e703607ff36c229a78
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040582"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="5f09e-102">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="5f09e-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="5f09e-103">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="5f09e-104">Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="5f09e-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="5f09e-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="5f09e-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="5f09e-106">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="5f09e-107">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="5f09e-108">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="5f09e-109">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="5f09e-110">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="5f09e-111">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="5f09e-112">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="5f09e-113">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="5f09e-114">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="5f09e-115">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="5f09e-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="5f09e-116">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="5f09e-117">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="5f09e-118">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="5f09e-119">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="5f09e-120">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="5f09e-121">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="5f09e-122">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5f09e-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="5f09e-123">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-123">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-124">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-126">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-126">Informational (4)</span></span>|

<span data-ttu-id="5f09e-127">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-127">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-128">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-128">Event</span></span>|<span data-ttu-id="5f09e-129">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-129">Event ID</span></span>|<span data-ttu-id="5f09e-130">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="5f09e-131">1</span><span class="sxs-lookup"><span data-stu-id="5f09e-131">1</span></span>|<span data-ttu-id="5f09e-132">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="5f09e-132">A garbage collection has started.</span></span>|

<span data-ttu-id="5f09e-133">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-133">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-134">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-134">Field name</span></span>|<span data-ttu-id="5f09e-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-135">Data type</span></span>|<span data-ttu-id="5f09e-136">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-137">Count</span><span class="sxs-lookup"><span data-stu-id="5f09e-137">Count</span></span>|<span data-ttu-id="5f09e-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-138">win:UInt32</span></span>|<span data-ttu-id="5f09e-139">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="5f09e-140">Profondeur</span><span class="sxs-lookup"><span data-stu-id="5f09e-140">Depth</span></span>|<span data-ttu-id="5f09e-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-141">win:UInt32</span></span>|<span data-ttu-id="5f09e-142">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="5f09e-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="5f09e-143">Raison</span><span class="sxs-lookup"><span data-stu-id="5f09e-143">Reason</span></span>|<span data-ttu-id="5f09e-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-144">win:UInt32</span></span>|<span data-ttu-id="5f09e-145">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="5f09e-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="5f09e-146">0x0 – Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="5f09e-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="5f09e-147">0x1 – Induit.</span><span class="sxs-lookup"><span data-stu-id="5f09e-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="5f09e-148">0x2 – Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="5f09e-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="5f09e-149">0x3 – Vide.</span><span class="sxs-lookup"><span data-stu-id="5f09e-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="5f09e-150">0x4 – Allocation de tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="5f09e-151">0x5 – Espace insuffisant (pour un tas de petits objets)</span><span class="sxs-lookup"><span data-stu-id="5f09e-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="5f09e-152">0x6 – Espace insuffisant (pour un tas d'objets volumineux)</span><span class="sxs-lookup"><span data-stu-id="5f09e-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="5f09e-153">0x7 – Induit mais non forcé comme blocage</span><span class="sxs-lookup"><span data-stu-id="5f09e-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="5f09e-154">Tapez</span><span class="sxs-lookup"><span data-stu-id="5f09e-154">Type</span></span>|<span data-ttu-id="5f09e-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-155">win:UInt32</span></span>|<span data-ttu-id="5f09e-156">0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5f09e-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="5f09e-157">0x1 – Garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5f09e-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="5f09e-158">0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="5f09e-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="5f09e-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-159">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-160">win:UInt16</span></span>|<span data-ttu-id="5f09e-161">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="5f09e-162">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="5f09e-163">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-164">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-164">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-165">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-167">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-167">Informational (4)</span></span>|

<span data-ttu-id="5f09e-168">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-168">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-169">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-169">Event</span></span>|<span data-ttu-id="5f09e-170">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-170">Event ID</span></span>|<span data-ttu-id="5f09e-171">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="5f09e-172">2</span><span class="sxs-lookup"><span data-stu-id="5f09e-172">2</span></span>|<span data-ttu-id="5f09e-173">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="5f09e-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="5f09e-174">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-174">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-175">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-175">Field name</span></span>|<span data-ttu-id="5f09e-176">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-176">Data type</span></span>|<span data-ttu-id="5f09e-177">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-178">Count</span><span class="sxs-lookup"><span data-stu-id="5f09e-178">Count</span></span>|<span data-ttu-id="5f09e-179">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-179">win:UInt32</span></span>|<span data-ttu-id="5f09e-180">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="5f09e-181">Profondeur</span><span class="sxs-lookup"><span data-stu-id="5f09e-181">Depth</span></span>|<span data-ttu-id="5f09e-182">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-182">win:UInt32</span></span>|<span data-ttu-id="5f09e-183">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="5f09e-183">The generation that was collected.</span></span>|
|<span data-ttu-id="5f09e-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-184">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-185">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-185">win:UInt16</span></span>|<span data-ttu-id="5f09e-186">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="5f09e-187">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="5f09e-188">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-189">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-189">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-190">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-192">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-192">Informational (4)</span></span>|

<span data-ttu-id="5f09e-193">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-193">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-194">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-194">Event</span></span>|<span data-ttu-id="5f09e-195">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-195">Event ID</span></span>|<span data-ttu-id="5f09e-196">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="5f09e-197">4</span><span class="sxs-lookup"><span data-stu-id="5f09e-197">4</span></span>|<span data-ttu-id="5f09e-198">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="5f09e-199">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-199">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-200">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-200">Field name</span></span>|<span data-ttu-id="5f09e-201">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-201">Data type</span></span>|<span data-ttu-id="5f09e-202">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="5f09e-203">GenerationSize0</span></span>|<span data-ttu-id="5f09e-204">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-204">win:UInt64</span></span>|<span data-ttu-id="5f09e-205">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="5f09e-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="5f09e-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="5f09e-206">TotalPromotedSize0</span></span>|<span data-ttu-id="5f09e-207">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-207">win:UInt64</span></span>|<span data-ttu-id="5f09e-208">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="5f09e-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="5f09e-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="5f09e-209">GenerationSize1</span></span>|<span data-ttu-id="5f09e-210">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-210">win:UInt64</span></span>|<span data-ttu-id="5f09e-211">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="5f09e-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="5f09e-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="5f09e-212">TotalPromotedSize1</span></span>|<span data-ttu-id="5f09e-213">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-213">win:UInt64</span></span>|<span data-ttu-id="5f09e-214">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="5f09e-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="5f09e-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="5f09e-215">GenerationSize2</span></span>|<span data-ttu-id="5f09e-216">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-216">win:UInt64</span></span>|<span data-ttu-id="5f09e-217">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="5f09e-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="5f09e-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="5f09e-218">TotalPromotedSize2</span></span>|<span data-ttu-id="5f09e-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-219">win:UInt64</span></span>|<span data-ttu-id="5f09e-220">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="5f09e-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="5f09e-221">GenerationSize3</span></span>|<span data-ttu-id="5f09e-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-222">win:UInt64</span></span>|<span data-ttu-id="5f09e-223">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="5f09e-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="5f09e-224">TotalPromotedSize3</span></span>|<span data-ttu-id="5f09e-225">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-225">win:UInt64</span></span>|<span data-ttu-id="5f09e-226">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="5f09e-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="5f09e-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="5f09e-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-228">win:UInt64</span></span>|<span data-ttu-id="5f09e-229">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="5f09e-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="5f09e-230">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="5f09e-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="5f09e-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-231">win:UInt64</span></span>|<span data-ttu-id="5f09e-232">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="5f09e-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="5f09e-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="5f09e-233">PinnedObjectCount</span></span>|<span data-ttu-id="5f09e-234">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-234">win:UInt32</span></span>|<span data-ttu-id="5f09e-235">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="5f09e-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="5f09e-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="5f09e-236">SinkBlockCount</span></span>|<span data-ttu-id="5f09e-237">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-237">win:UInt32</span></span>|<span data-ttu-id="5f09e-238">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="5f09e-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="5f09e-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="5f09e-239">GCHandleCount</span></span>|<span data-ttu-id="5f09e-240">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-240">win:UInt32</span></span>|<span data-ttu-id="5f09e-241">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="5f09e-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="5f09e-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-242">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-243">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-243">win:UInt16</span></span>|<span data-ttu-id="5f09e-244">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="5f09e-245">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="5f09e-246">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-247">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-247">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-248">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-250">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-250">Informational (4)</span></span>|

<span data-ttu-id="5f09e-251">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-251">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-252">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-252">Event</span></span>|<span data-ttu-id="5f09e-253">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-253">Event ID</span></span>|<span data-ttu-id="5f09e-254">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="5f09e-255">5</span><span class="sxs-lookup"><span data-stu-id="5f09e-255">5</span></span>|<span data-ttu-id="5f09e-256">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="5f09e-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="5f09e-257">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="5f09e-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="5f09e-258">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-258">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-259">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-259">Field name</span></span>|<span data-ttu-id="5f09e-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-260">Data type</span></span>|<span data-ttu-id="5f09e-261">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-262">Adresse</span><span class="sxs-lookup"><span data-stu-id="5f09e-262">Address</span></span>|<span data-ttu-id="5f09e-263">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-263">win:UInt64</span></span>|<span data-ttu-id="5f09e-264">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="5f09e-264">The address of the segment.</span></span>|
|<span data-ttu-id="5f09e-265">Size</span><span class="sxs-lookup"><span data-stu-id="5f09e-265">Size</span></span>|<span data-ttu-id="5f09e-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-266">win:UInt64</span></span>|<span data-ttu-id="5f09e-267">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="5f09e-267">The size of the segment.</span></span>|
|<span data-ttu-id="5f09e-268">Tapez</span><span class="sxs-lookup"><span data-stu-id="5f09e-268">Type</span></span>|<span data-ttu-id="5f09e-269">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-269">win:UInt32</span></span>|<span data-ttu-id="5f09e-270">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="5f09e-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="5f09e-271">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="5f09e-272">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="5f09e-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="5f09e-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-273">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-274">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-274">win:UInt16</span></span>|<span data-ttu-id="5f09e-275">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="5f09e-276">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="5f09e-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="5f09e-277">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="5f09e-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="5f09e-278">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="5f09e-279">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-280">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-280">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-281">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-283">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-283">Informational (4)</span></span>|

<span data-ttu-id="5f09e-284">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-284">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-285">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-285">Event</span></span>|<span data-ttu-id="5f09e-286">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-286">Event ID</span></span>|<span data-ttu-id="5f09e-287">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="5f09e-288">6</span><span class="sxs-lookup"><span data-stu-id="5f09e-288">6</span></span>|<span data-ttu-id="5f09e-289">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="5f09e-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="5f09e-290">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-290">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-291">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-291">Field name</span></span>|<span data-ttu-id="5f09e-292">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-292">Data type</span></span>|<span data-ttu-id="5f09e-293">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-294">Adresse</span><span class="sxs-lookup"><span data-stu-id="5f09e-294">Address</span></span>|<span data-ttu-id="5f09e-295">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-295">win:UInt64</span></span>|<span data-ttu-id="5f09e-296">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="5f09e-296">The address of the segment.</span></span>|
|<span data-ttu-id="5f09e-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-297">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-298">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-298">win:UInt16</span></span>|<span data-ttu-id="5f09e-299">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="5f09e-300">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="5f09e-301">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-302">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-302">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-303">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-305">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-305">Informational (4)</span></span>|

<span data-ttu-id="5f09e-306">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-306">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-307">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-307">Event</span></span>|<span data-ttu-id="5f09e-308">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-308">Event ID</span></span>|<span data-ttu-id="5f09e-309">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="5f09e-310">7</span><span class="sxs-lookup"><span data-stu-id="5f09e-310">7</span></span>|<span data-ttu-id="5f09e-311">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="5f09e-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="5f09e-312">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="5f09e-313">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="5f09e-314">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-315">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-315">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-316">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-318">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-318">Informational (4)</span></span>|

<span data-ttu-id="5f09e-319">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-319">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-320">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-320">Event</span></span>|<span data-ttu-id="5f09e-321">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-321">Event Id</span></span>|<span data-ttu-id="5f09e-322">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="5f09e-323">3</span><span class="sxs-lookup"><span data-stu-id="5f09e-323">3</span></span>|<span data-ttu-id="5f09e-324">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="5f09e-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="5f09e-325">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="5f09e-326">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="5f09e-327">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-328">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-328">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-329">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-331">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-331">Informational (4)</span></span>|

<span data-ttu-id="5f09e-332">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-332">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-333">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-333">Event</span></span>|<span data-ttu-id="5f09e-334">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-334">Event ID</span></span>|<span data-ttu-id="5f09e-335">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="5f09e-336">9</span><span class="sxs-lookup"><span data-stu-id="5f09e-336">9</span></span>|<span data-ttu-id="5f09e-337">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="5f09e-338">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-338">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-339">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-339">Field name</span></span>|<span data-ttu-id="5f09e-340">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-340">Data type</span></span>|<span data-ttu-id="5f09e-341">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-342">Raison</span><span class="sxs-lookup"><span data-stu-id="5f09e-342">Reason</span></span>|<span data-ttu-id="5f09e-343">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-343">win:UInt16</span></span>|<span data-ttu-id="5f09e-344">0x0 – Autre.</span><span class="sxs-lookup"><span data-stu-id="5f09e-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="5f09e-345">0x1 – Garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="5f09e-346">0x2 – Fermeture du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="5f09e-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="5f09e-347">0x3 – Pitching de code.</span><span class="sxs-lookup"><span data-stu-id="5f09e-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="5f09e-348">0x4 – Arrêt.</span><span class="sxs-lookup"><span data-stu-id="5f09e-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="5f09e-349">0x5 – Débogueur.</span><span class="sxs-lookup"><span data-stu-id="5f09e-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="5f09e-350">0x6 – Préparation pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="5f09e-351">Count</span><span class="sxs-lookup"><span data-stu-id="5f09e-351">Count</span></span>|<span data-ttu-id="5f09e-352">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-352">win:UInt32</span></span>|<span data-ttu-id="5f09e-353">Nombre GC à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="5f09e-353">The GC count at the time.</span></span> <span data-ttu-id="5f09e-354">En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="5f09e-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-355">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-356">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-356">win:UInt16</span></span>|<span data-ttu-id="5f09e-357">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="5f09e-358">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="5f09e-359">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-360">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-360">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-361">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-363">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-363">Informational (4)</span></span>|

<span data-ttu-id="5f09e-364">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-364">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-365">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-365">Event</span></span>|<span data-ttu-id="5f09e-366">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-366">Event ID</span></span>|<span data-ttu-id="5f09e-367">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="5f09e-368">8</span><span class="sxs-lookup"><span data-stu-id="5f09e-368">8</span></span>|<span data-ttu-id="5f09e-369">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="5f09e-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="5f09e-370">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="5f09e-371">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="5f09e-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="5f09e-372">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-373">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-373">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-374">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-376">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-376">Informational (4)</span></span>|

<span data-ttu-id="5f09e-377">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-377">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-378">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-378">Event</span></span>|<span data-ttu-id="5f09e-379">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-379">Event ID</span></span>|<span data-ttu-id="5f09e-380">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="5f09e-381">10</span><span class="sxs-lookup"><span data-stu-id="5f09e-381">10</span></span>|<span data-ttu-id="5f09e-382">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="5f09e-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="5f09e-383">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-383">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-384">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-384">Field name</span></span>|<span data-ttu-id="5f09e-385">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-385">Data type</span></span>|<span data-ttu-id="5f09e-386">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="5f09e-387">AllocationAmount</span></span>|<span data-ttu-id="5f09e-388">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-388">win:UInt32</span></span>|<span data-ttu-id="5f09e-389">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="5f09e-389">The allocation size, in bytes.</span></span> <span data-ttu-id="5f09e-390">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="5f09e-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="5f09e-391">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="5f09e-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="5f09e-392">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5f09e-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="5f09e-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="5f09e-393">AllocationKind</span></span>|<span data-ttu-id="5f09e-394">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-394">win:UInt32</span></span>|<span data-ttu-id="5f09e-395">0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="5f09e-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="5f09e-396">0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="5f09e-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="5f09e-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-397">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-398">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-398">win:UInt16</span></span>|<span data-ttu-id="5f09e-399">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="5f09e-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="5f09e-400">AllocationAmount64</span></span>|<span data-ttu-id="5f09e-401">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="5f09e-401">win:UInt64</span></span>|<span data-ttu-id="5f09e-402">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="5f09e-402">The allocation size, in bytes.</span></span> <span data-ttu-id="5f09e-403">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="5f09e-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="5f09e-404">TypeId</span><span class="sxs-lookup"><span data-stu-id="5f09e-404">TypeId</span></span>|<span data-ttu-id="5f09e-405">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="5f09e-405">win:Pointer</span></span>|<span data-ttu-id="5f09e-406">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="5f09e-406">The address of the MethodTable.</span></span> <span data-ttu-id="5f09e-407">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="5f09e-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="5f09e-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="5f09e-408">TypeName</span></span>|<span data-ttu-id="5f09e-409">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="5f09e-409">win:UnicodeString</span></span>|<span data-ttu-id="5f09e-410">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="5f09e-410">The name of the type that was allocated.</span></span> <span data-ttu-id="5f09e-411">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="5f09e-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="5f09e-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="5f09e-412">HeapIndex</span></span>|<span data-ttu-id="5f09e-413">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-413">win:UInt32</span></span>|<span data-ttu-id="5f09e-414">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="5f09e-414">The heap where the object was allocated.</span></span> <span data-ttu-id="5f09e-415">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="5f09e-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="5f09e-416">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="5f09e-417">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-418">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-418">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-419">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-421">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-421">Informational (4)</span></span>|

<span data-ttu-id="5f09e-422">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-422">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-423">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-423">Event</span></span>|<span data-ttu-id="5f09e-424">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-424">Event ID</span></span>|<span data-ttu-id="5f09e-425">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="5f09e-426">14</span><span class="sxs-lookup"><span data-stu-id="5f09e-426">14</span></span>|<span data-ttu-id="5f09e-427">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="5f09e-427">The start of running finalizers.</span></span>|

<span data-ttu-id="5f09e-428">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="5f09e-429">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="5f09e-430">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-431">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-431">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-432">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-434">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-434">Informational (4)</span></span>|

<span data-ttu-id="5f09e-435">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-435">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-436">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-436">Event</span></span>|<span data-ttu-id="5f09e-437">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-437">Event ID</span></span>|<span data-ttu-id="5f09e-438">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="5f09e-439">13</span><span class="sxs-lookup"><span data-stu-id="5f09e-439">13</span></span>|<span data-ttu-id="5f09e-440">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="5f09e-440">The end of running finalizers.</span></span>|

<span data-ttu-id="5f09e-441">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-441">The following table shows the event data:</span></span>

|<span data-ttu-id="5f09e-442">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="5f09e-442">Field name</span></span>|<span data-ttu-id="5f09e-443">Type de données</span><span class="sxs-lookup"><span data-stu-id="5f09e-443">Data type</span></span>|<span data-ttu-id="5f09e-444">Description</span><span class="sxs-lookup"><span data-stu-id="5f09e-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="5f09e-445">Count</span><span class="sxs-lookup"><span data-stu-id="5f09e-445">Count</span></span>|<span data-ttu-id="5f09e-446">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="5f09e-446">win:UInt32</span></span>|<span data-ttu-id="5f09e-447">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="5f09e-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="5f09e-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="5f09e-448">ClrInstanceID</span></span>|<span data-ttu-id="5f09e-449">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="5f09e-449">win:UInt16</span></span>|<span data-ttu-id="5f09e-450">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="5f09e-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="5f09e-451">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="5f09e-452">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-453">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-453">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-454">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-456">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-456">Informational (4)</span></span>|
|<span data-ttu-id="5f09e-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5f09e-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5f09e-458">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-458">Informational (4)</span></span>|

<span data-ttu-id="5f09e-459">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-459">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-460">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-460">Event</span></span>|<span data-ttu-id="5f09e-461">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-461">Event ID</span></span>|<span data-ttu-id="5f09e-462">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="5f09e-463">11</span><span class="sxs-lookup"><span data-stu-id="5f09e-463">11</span></span>|<span data-ttu-id="5f09e-464">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="5f09e-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="5f09e-465">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="5f09e-466">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="5f09e-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="5f09e-467">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="5f09e-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="5f09e-468">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-468">Keyword for raising the event</span></span>|<span data-ttu-id="5f09e-469">Level</span><span class="sxs-lookup"><span data-stu-id="5f09e-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="5f09e-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="5f09e-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="5f09e-471">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-471">Informational (4)</span></span>|
|<span data-ttu-id="5f09e-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="5f09e-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="5f09e-473">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="5f09e-473">Informational (4)</span></span>|

<span data-ttu-id="5f09e-474">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="5f09e-474">The following table shows the event information:</span></span>

|<span data-ttu-id="5f09e-475">événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-475">Event</span></span>|<span data-ttu-id="5f09e-476">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5f09e-476">Event ID</span></span>|<span data-ttu-id="5f09e-477">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="5f09e-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="5f09e-478">12</span><span class="sxs-lookup"><span data-stu-id="5f09e-478">12</span></span>|<span data-ttu-id="5f09e-479">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="5f09e-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="5f09e-480">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="5f09e-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="5f09e-481">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f09e-481">See also</span></span>

- [<span data-ttu-id="5f09e-482">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="5f09e-482">CLR ETW Events</span></span>](clr-etw-events.md)

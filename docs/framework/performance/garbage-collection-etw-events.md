---
title: Événements ETW de garbage collection
ms.date: 03/30/2017
helpviewer_keywords:
- GC events
- garbage collection events [.NET Framework]
- ETW, garbage collection events (CLR)
ms.assetid: f14b6fd7-0966-4d87-bc89-54ef3a44a94a
ms.openlocfilehash: 5ff214314b92796f4a4a89ddd33a976d8b1f21d1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716068"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="0902d-102">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="0902d-102">Garbage Collection ETW Events</span></span>

<span data-ttu-id="0902d-103">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="0902d-104">Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="0902d-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>

<span data-ttu-id="0902d-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="0902d-105">This category consists of the following events:</span></span>

- [<span data-ttu-id="0902d-106">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-106">GCStart_V1 Event</span></span>](#gcstart_v1-event)
- [<span data-ttu-id="0902d-107">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-107">GCEnd_V1 Event</span></span>](#gcend_v1-event)
- [<span data-ttu-id="0902d-108">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1-event)
- [<span data-ttu-id="0902d-109">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1-event)
- [<span data-ttu-id="0902d-110">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1-event)
- [<span data-ttu-id="0902d-111">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1-event)
- [<span data-ttu-id="0902d-112">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1-event)
- [<span data-ttu-id="0902d-113">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1-event)
- [<span data-ttu-id="0902d-114">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1-event)
- [<span data-ttu-id="0902d-115">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0902d-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2-event)
- [<span data-ttu-id="0902d-116">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1-event)
- [<span data-ttu-id="0902d-117">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1-event)
- [<span data-ttu-id="0902d-118">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1-event)
- [<span data-ttu-id="0902d-119">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1-event)

## <a name="gcstart_v1-event"></a><span data-ttu-id="0902d-120">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-120">GCStart_V1 Event</span></span>  

<span data-ttu-id="0902d-121">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="0902d-122">Pour plus d’informations, consultez [niveaux et Mots clés ETW du CLR](clr-etw-keywords-and-levels.md).</span><span class="sxs-lookup"><span data-stu-id="0902d-122">For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).</span></span>

|<span data-ttu-id="0902d-123">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-123">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-124">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-124">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-126">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-126">Informational (4)</span></span>|

<span data-ttu-id="0902d-127">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-127">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-128">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-128">Event</span></span>|<span data-ttu-id="0902d-129">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-129">Event ID</span></span>|<span data-ttu-id="0902d-130">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-130">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="0902d-131">1</span><span class="sxs-lookup"><span data-stu-id="0902d-131">1</span></span>|<span data-ttu-id="0902d-132">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="0902d-132">A garbage collection has started.</span></span>|

<span data-ttu-id="0902d-133">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-133">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-134">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-134">Field name</span></span>|<span data-ttu-id="0902d-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-135">Data type</span></span>|<span data-ttu-id="0902d-136">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-136">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-137">Nombre</span><span class="sxs-lookup"><span data-stu-id="0902d-137">Count</span></span>|<span data-ttu-id="0902d-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-138">win:UInt32</span></span>|<span data-ttu-id="0902d-139">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-139">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0902d-140">Profondeur</span><span class="sxs-lookup"><span data-stu-id="0902d-140">Depth</span></span>|<span data-ttu-id="0902d-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-141">win:UInt32</span></span>|<span data-ttu-id="0902d-142">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="0902d-142">The generation that is being collected.</span></span>|
|<span data-ttu-id="0902d-143">Raison</span><span class="sxs-lookup"><span data-stu-id="0902d-143">Reason</span></span>|<span data-ttu-id="0902d-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-144">win:UInt32</span></span>|<span data-ttu-id="0902d-145">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="0902d-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="0902d-146">0x0 – Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="0902d-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="0902d-147">0x1 – Induit.</span><span class="sxs-lookup"><span data-stu-id="0902d-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="0902d-148">0x2 – Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="0902d-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="0902d-149">0x3 – Vide.</span><span class="sxs-lookup"><span data-stu-id="0902d-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="0902d-150">0x4 – Allocation de tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="0902d-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="0902d-151">0x5 – Espace insuffisant (pour un tas de petits objets)</span><span class="sxs-lookup"><span data-stu-id="0902d-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="0902d-152">0x6 – Espace insuffisant (pour un tas d'objets volumineux)</span><span class="sxs-lookup"><span data-stu-id="0902d-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="0902d-153">0x7 – Induit mais non forcé comme blocage</span><span class="sxs-lookup"><span data-stu-id="0902d-153">0x7 - Induced but not forced as blocking.</span></span>|
|<span data-ttu-id="0902d-154">Type</span><span class="sxs-lookup"><span data-stu-id="0902d-154">Type</span></span>|<span data-ttu-id="0902d-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-155">win:UInt32</span></span>|<span data-ttu-id="0902d-156">0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0902d-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="0902d-157">0x1 – Garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0902d-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="0902d-158">0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="0902d-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|
|<span data-ttu-id="0902d-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-159">ClrInstanceID</span></span>|<span data-ttu-id="0902d-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-160">win:UInt16</span></span>|<span data-ttu-id="0902d-161">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="0902d-162">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-162">GCEnd_V1 Event</span></span>

<span data-ttu-id="0902d-163">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-163">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-164">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-164">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-165">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-165">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-166">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-166">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-167">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-167">Informational (4)</span></span>|

<span data-ttu-id="0902d-168">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-168">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-169">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-169">Event</span></span>|<span data-ttu-id="0902d-170">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-170">Event ID</span></span>|<span data-ttu-id="0902d-171">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-171">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="0902d-172">2</span><span class="sxs-lookup"><span data-stu-id="0902d-172">2</span></span>|<span data-ttu-id="0902d-173">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="0902d-173">The garbage collection has ended.</span></span>|

<span data-ttu-id="0902d-174">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-174">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-175">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-175">Field name</span></span>|<span data-ttu-id="0902d-176">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-176">Data type</span></span>|<span data-ttu-id="0902d-177">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-177">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-178">Nombre</span><span class="sxs-lookup"><span data-stu-id="0902d-178">Count</span></span>|<span data-ttu-id="0902d-179">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-179">win:UInt32</span></span>|<span data-ttu-id="0902d-180">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-180">The *n*th garbage collection.</span></span>|
|<span data-ttu-id="0902d-181">Profondeur</span><span class="sxs-lookup"><span data-stu-id="0902d-181">Depth</span></span>|<span data-ttu-id="0902d-182">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-182">win:UInt32</span></span>|<span data-ttu-id="0902d-183">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="0902d-183">The generation that was collected.</span></span>|
|<span data-ttu-id="0902d-184">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-184">ClrInstanceID</span></span>|<span data-ttu-id="0902d-185">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-185">win:UInt16</span></span>|<span data-ttu-id="0902d-186">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-186">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcheapstats_v1-event"></a><span data-ttu-id="0902d-187">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-187">GCHeapStats_V1 Event</span></span>

<span data-ttu-id="0902d-188">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-188">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-189">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-189">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-190">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-190">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-191">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-191">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-192">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-192">Informational (4)</span></span>|

<span data-ttu-id="0902d-193">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-193">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-194">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-194">Event</span></span>|<span data-ttu-id="0902d-195">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-195">Event ID</span></span>|<span data-ttu-id="0902d-196">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-196">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V1`|<span data-ttu-id="0902d-197">4</span><span class="sxs-lookup"><span data-stu-id="0902d-197">4</span></span>|<span data-ttu-id="0902d-198">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-198">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="0902d-199">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-199">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-200">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-200">Field name</span></span>|<span data-ttu-id="0902d-201">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-201">Data type</span></span>|<span data-ttu-id="0902d-202">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-202">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-203">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="0902d-203">GenerationSize0</span></span>|<span data-ttu-id="0902d-204">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-204">win:UInt64</span></span>|<span data-ttu-id="0902d-205">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="0902d-205">The size, in bytes, of generation 0 memory.</span></span>|
|<span data-ttu-id="0902d-206">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="0902d-206">TotalPromotedSize0</span></span>|<span data-ttu-id="0902d-207">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-207">win:UInt64</span></span>|<span data-ttu-id="0902d-208">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="0902d-208">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|<span data-ttu-id="0902d-209">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="0902d-209">GenerationSize1</span></span>|<span data-ttu-id="0902d-210">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-210">win:UInt64</span></span>|<span data-ttu-id="0902d-211">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="0902d-211">The size, in bytes, of generation 1 memory.</span></span>|
|<span data-ttu-id="0902d-212">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="0902d-212">TotalPromotedSize1</span></span>|<span data-ttu-id="0902d-213">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-213">win:UInt64</span></span>|<span data-ttu-id="0902d-214">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="0902d-214">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|<span data-ttu-id="0902d-215">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="0902d-215">GenerationSize2</span></span>|<span data-ttu-id="0902d-216">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-216">win:UInt64</span></span>|<span data-ttu-id="0902d-217">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="0902d-217">The size, in bytes, of generation 2 memory.</span></span>|
|<span data-ttu-id="0902d-218">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="0902d-218">TotalPromotedSize2</span></span>|<span data-ttu-id="0902d-219">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-219">win:UInt64</span></span>|<span data-ttu-id="0902d-220">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-220">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|<span data-ttu-id="0902d-221">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="0902d-221">GenerationSize3</span></span>|<span data-ttu-id="0902d-222">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-222">win:UInt64</span></span>|<span data-ttu-id="0902d-223">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="0902d-223">The size, in bytes, of the large object heap.</span></span>|
|<span data-ttu-id="0902d-224">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="0902d-224">TotalPromotedSize3</span></span>|<span data-ttu-id="0902d-225">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-225">win:UInt64</span></span>|<span data-ttu-id="0902d-226">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-226">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|<span data-ttu-id="0902d-227">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0902d-227">FinalizationPromotedSize</span></span>|<span data-ttu-id="0902d-228">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-228">win:UInt64</span></span>|<span data-ttu-id="0902d-229">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="0902d-229">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0902d-230">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="0902d-230">FinalizationPromotedCount</span></span>|<span data-ttu-id="0902d-231">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-231">win:UInt64</span></span>|<span data-ttu-id="0902d-232">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="0902d-232">The number of objects that are ready for finalization.</span></span>|
|<span data-ttu-id="0902d-233">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="0902d-233">PinnedObjectCount</span></span>|<span data-ttu-id="0902d-234">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-234">win:UInt32</span></span>|<span data-ttu-id="0902d-235">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="0902d-235">The number of pinned (unmovable) objects.</span></span>|
|<span data-ttu-id="0902d-236">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="0902d-236">SinkBlockCount</span></span>|<span data-ttu-id="0902d-237">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-237">win:UInt32</span></span>|<span data-ttu-id="0902d-238">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="0902d-238">The number of synchronization blocks in use.</span></span>|
|<span data-ttu-id="0902d-239">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="0902d-239">GCHandleCount</span></span>|<span data-ttu-id="0902d-240">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-240">win:UInt32</span></span>|<span data-ttu-id="0902d-241">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="0902d-241">The number of garbage collection handles in use.</span></span>|
|<span data-ttu-id="0902d-242">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-242">ClrInstanceID</span></span>|<span data-ttu-id="0902d-243">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-243">win:UInt16</span></span>|<span data-ttu-id="0902d-244">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-244">Unique ID for the instance of CLR or CoreCLR.</span></span>|
  
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="0902d-245">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-245">GCCreateSegment_V1 Event</span></span>

<span data-ttu-id="0902d-246">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-246">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-247">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-247">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-248">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-248">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-249">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-249">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-250">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-250">Informational (4)</span></span>|

<span data-ttu-id="0902d-251">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-251">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-252">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-252">Event</span></span>|<span data-ttu-id="0902d-253">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-253">Event ID</span></span>|<span data-ttu-id="0902d-254">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-254">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="0902d-255">5</span><span class="sxs-lookup"><span data-stu-id="0902d-255">5</span></span>|<span data-ttu-id="0902d-256">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="0902d-256">A new garbage collection segment has been created.</span></span> <span data-ttu-id="0902d-257">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="0902d-257">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="0902d-258">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-258">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-259">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-259">Field name</span></span>|<span data-ttu-id="0902d-260">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-260">Data type</span></span>|<span data-ttu-id="0902d-261">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-261">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-262">Address</span><span class="sxs-lookup"><span data-stu-id="0902d-262">Address</span></span>|<span data-ttu-id="0902d-263">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-263">win:UInt64</span></span>|<span data-ttu-id="0902d-264">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="0902d-264">The address of the segment.</span></span>|
|<span data-ttu-id="0902d-265">Taille</span><span class="sxs-lookup"><span data-stu-id="0902d-265">Size</span></span>|<span data-ttu-id="0902d-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-266">win:UInt64</span></span>|<span data-ttu-id="0902d-267">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="0902d-267">The size of the segment.</span></span>|
|<span data-ttu-id="0902d-268">Type</span><span class="sxs-lookup"><span data-stu-id="0902d-268">Type</span></span>|<span data-ttu-id="0902d-269">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-269">win:UInt32</span></span>|<span data-ttu-id="0902d-270">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="0902d-270">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="0902d-271">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="0902d-271">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="0902d-272">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="0902d-272">0x2 - Read-only heap.</span></span>|
|<span data-ttu-id="0902d-273">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-273">ClrInstanceID</span></span>|<span data-ttu-id="0902d-274">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-274">win:UInt16</span></span>|<span data-ttu-id="0902d-275">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-275">Unique ID for the instance of CLR or CoreCLR.</span></span>|

<span data-ttu-id="0902d-276">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="0902d-276">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="0902d-277">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="0902d-277">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="0902d-278">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-278">GCFreeSegment_V1 Event</span></span>

<span data-ttu-id="0902d-279">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-279">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-280">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-280">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-281">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-281">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-282">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-282">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-283">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-283">Informational (4)</span></span>|

<span data-ttu-id="0902d-284">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-284">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-285">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-285">Event</span></span>|<span data-ttu-id="0902d-286">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-286">Event ID</span></span>|<span data-ttu-id="0902d-287">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-287">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="0902d-288">6</span><span class="sxs-lookup"><span data-stu-id="0902d-288">6</span></span>|<span data-ttu-id="0902d-289">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="0902d-289">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="0902d-290">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-290">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-291">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-291">Field name</span></span>|<span data-ttu-id="0902d-292">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-292">Data type</span></span>|<span data-ttu-id="0902d-293">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-293">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-294">Address</span><span class="sxs-lookup"><span data-stu-id="0902d-294">Address</span></span>|<span data-ttu-id="0902d-295">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-295">win:UInt64</span></span>|<span data-ttu-id="0902d-296">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="0902d-296">The address of the segment.</span></span>|
|<span data-ttu-id="0902d-297">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-297">ClrInstanceID</span></span>|<span data-ttu-id="0902d-298">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-298">win:UInt16</span></span>|<span data-ttu-id="0902d-299">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-299">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="0902d-300">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-300">GCRestartEEBegin_V1 Event</span></span>

<span data-ttu-id="0902d-301">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-301">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-302">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-302">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-303">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-303">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-304">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-304">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-305">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-305">Informational (4)</span></span>|

<span data-ttu-id="0902d-306">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-306">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-307">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-307">Event</span></span>|<span data-ttu-id="0902d-308">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-308">Event ID</span></span>|<span data-ttu-id="0902d-309">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-309">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="0902d-310">7</span><span class="sxs-lookup"><span data-stu-id="0902d-310">7</span></span>|<span data-ttu-id="0902d-311">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="0902d-311">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="0902d-312">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-312">No event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="0902d-313">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-313">GCRestartEEEnd_V1 Event</span></span>

<span data-ttu-id="0902d-314">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-314">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-315">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-315">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-316">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-316">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-317">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-317">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-318">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-318">Informational (4)</span></span>|

<span data-ttu-id="0902d-319">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-319">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-320">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-320">Event</span></span>|<span data-ttu-id="0902d-321">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-321">Event Id</span></span>|<span data-ttu-id="0902d-322">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-322">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="0902d-323">3</span><span class="sxs-lookup"><span data-stu-id="0902d-323">3</span></span>|<span data-ttu-id="0902d-324">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="0902d-324">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="0902d-325">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-325">No event data.</span></span>

## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="0902d-326">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-326">GCSuspendEE_V1 Event</span></span>

<span data-ttu-id="0902d-327">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-327">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-328">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-328">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-329">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-329">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-330">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-330">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-331">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-331">Informational (4)</span></span>|

<span data-ttu-id="0902d-332">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-332">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-333">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-333">Event</span></span>|<span data-ttu-id="0902d-334">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-334">Event ID</span></span>|<span data-ttu-id="0902d-335">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-335">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEE_V1`|<span data-ttu-id="0902d-336">9</span><span class="sxs-lookup"><span data-stu-id="0902d-336">9</span></span>|<span data-ttu-id="0902d-337">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-337">Start of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0902d-338">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-338">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-339">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-339">Field name</span></span>|<span data-ttu-id="0902d-340">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-340">Data type</span></span>|<span data-ttu-id="0902d-341">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-341">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-342">Raison</span><span class="sxs-lookup"><span data-stu-id="0902d-342">Reason</span></span>|<span data-ttu-id="0902d-343">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-343">win:UInt16</span></span>|<span data-ttu-id="0902d-344">0x0 – Autre.</span><span class="sxs-lookup"><span data-stu-id="0902d-344">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="0902d-345">0x1 – Garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-345">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="0902d-346">0x2 – Fermeture du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="0902d-346">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="0902d-347">0x3 – Pitching de code.</span><span class="sxs-lookup"><span data-stu-id="0902d-347">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="0902d-348">0x4 – Arrêt.</span><span class="sxs-lookup"><span data-stu-id="0902d-348">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="0902d-349">0x5 – Débogueur.</span><span class="sxs-lookup"><span data-stu-id="0902d-349">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="0902d-350">0x6 – Préparation pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-350">0x6 - Preparation for garbage collection.</span></span>|
|<span data-ttu-id="0902d-351">Nombre</span><span class="sxs-lookup"><span data-stu-id="0902d-351">Count</span></span>|<span data-ttu-id="0902d-352">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-352">win:UInt32</span></span>|<span data-ttu-id="0902d-353">Nombre GC à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="0902d-353">The GC count at the time.</span></span> <span data-ttu-id="0902d-354">En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-354">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|
|<span data-ttu-id="0902d-355">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-355">ClrInstanceID</span></span>|<span data-ttu-id="0902d-356">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-356">win:UInt16</span></span>|<span data-ttu-id="0902d-357">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-357">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="0902d-358">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-358">GCSuspendEEEnd_V1 Event</span></span>

<span data-ttu-id="0902d-359">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-359">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-360">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-360">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-361">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-361">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-362">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-362">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-363">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-363">Informational (4)</span></span>|

<span data-ttu-id="0902d-364">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-364">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-365">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-365">Event</span></span>|<span data-ttu-id="0902d-366">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-366">Event ID</span></span>|<span data-ttu-id="0902d-367">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-367">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="0902d-368">8</span><span class="sxs-lookup"><span data-stu-id="0902d-368">8</span></span>|<span data-ttu-id="0902d-369">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="0902d-369">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="0902d-370">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-370">No event data.</span></span>

## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="0902d-371">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="0902d-371">GCAllocationTick_V2 Event</span></span>

<span data-ttu-id="0902d-372">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-372">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-373">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-373">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-374">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-374">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-375">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-375">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-376">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-376">Informational (4)</span></span>|

<span data-ttu-id="0902d-377">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-377">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-378">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-378">Event</span></span>|<span data-ttu-id="0902d-379">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-379">Event ID</span></span>|<span data-ttu-id="0902d-380">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-380">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V2`|<span data-ttu-id="0902d-381">10</span><span class="sxs-lookup"><span data-stu-id="0902d-381">10</span></span>|<span data-ttu-id="0902d-382">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="0902d-382">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="0902d-383">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-383">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-384">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-384">Field name</span></span>|<span data-ttu-id="0902d-385">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-385">Data type</span></span>|<span data-ttu-id="0902d-386">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-386">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-387">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="0902d-387">AllocationAmount</span></span>|<span data-ttu-id="0902d-388">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-388">win:UInt32</span></span>|<span data-ttu-id="0902d-389">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="0902d-389">The allocation size, in bytes.</span></span> <span data-ttu-id="0902d-390">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="0902d-390">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="0902d-391">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="0902d-391">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="0902d-392">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="0902d-392">Use `AllocationAmount64` for very large allocations.</span></span>|
|<span data-ttu-id="0902d-393">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="0902d-393">AllocationKind</span></span>|<span data-ttu-id="0902d-394">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-394">win:UInt32</span></span>|<span data-ttu-id="0902d-395">0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="0902d-395">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="0902d-396">0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="0902d-396">0x1 - Large object allocation (allocation is in large object heap).</span></span>|
|<span data-ttu-id="0902d-397">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-397">ClrInstanceID</span></span>|<span data-ttu-id="0902d-398">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-398">win:UInt16</span></span>|<span data-ttu-id="0902d-399">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-399">Unique ID for the instance of CLR or CoreCLR.</span></span>|
|<span data-ttu-id="0902d-400">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="0902d-400">AllocationAmount64</span></span>|<span data-ttu-id="0902d-401">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="0902d-401">win:UInt64</span></span>|<span data-ttu-id="0902d-402">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="0902d-402">The allocation size, in bytes.</span></span> <span data-ttu-id="0902d-403">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="0902d-403">This value is accurate for very large allocations.</span></span>|
|<span data-ttu-id="0902d-404">ID du type</span><span class="sxs-lookup"><span data-stu-id="0902d-404">TypeId</span></span>|<span data-ttu-id="0902d-405">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="0902d-405">win:Pointer</span></span>|<span data-ttu-id="0902d-406">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="0902d-406">The address of the MethodTable.</span></span> <span data-ttu-id="0902d-407">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="0902d-407">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0902d-408">TypeName</span><span class="sxs-lookup"><span data-stu-id="0902d-408">TypeName</span></span>|<span data-ttu-id="0902d-409">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0902d-409">win:UnicodeString</span></span>|<span data-ttu-id="0902d-410">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="0902d-410">The name of the type that was allocated.</span></span> <span data-ttu-id="0902d-411">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="0902d-411">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|<span data-ttu-id="0902d-412">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="0902d-412">HeapIndex</span></span>|<span data-ttu-id="0902d-413">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-413">win:UInt32</span></span>|<span data-ttu-id="0902d-414">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="0902d-414">The heap where the object was allocated.</span></span> <span data-ttu-id="0902d-415">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="0902d-415">This value is 0 (zero) when running with workstation garbage collection.</span></span>|

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="0902d-416">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-416">GCFinalizersBegin_V1 Event</span></span>

<span data-ttu-id="0902d-417">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-417">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-418">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-418">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-419">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-419">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-420">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-420">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-421">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-421">Informational (4)</span></span>|

<span data-ttu-id="0902d-422">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-422">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-423">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-423">Event</span></span>|<span data-ttu-id="0902d-424">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-424">Event ID</span></span>|<span data-ttu-id="0902d-425">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-425">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="0902d-426">14</span><span class="sxs-lookup"><span data-stu-id="0902d-426">14</span></span>|<span data-ttu-id="0902d-427">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="0902d-427">The start of running finalizers.</span></span>|

<span data-ttu-id="0902d-428">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-428">No event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="0902d-429">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-429">GCFinalizersEnd_V1 Event</span></span>

<span data-ttu-id="0902d-430">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-430">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-431">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-431">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-432">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-432">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-433">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-433">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-434">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-434">Informational (4)</span></span>|

<span data-ttu-id="0902d-435">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-435">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-436">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-436">Event</span></span>|<span data-ttu-id="0902d-437">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-437">Event ID</span></span>|<span data-ttu-id="0902d-438">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-438">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="0902d-439">13</span><span class="sxs-lookup"><span data-stu-id="0902d-439">13</span></span>|<span data-ttu-id="0902d-440">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="0902d-440">The end of running finalizers.</span></span>|

<span data-ttu-id="0902d-441">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-441">The following table shows the event data:</span></span>

|<span data-ttu-id="0902d-442">Nom de champ</span><span class="sxs-lookup"><span data-stu-id="0902d-442">Field name</span></span>|<span data-ttu-id="0902d-443">Type de données</span><span class="sxs-lookup"><span data-stu-id="0902d-443">Data type</span></span>|<span data-ttu-id="0902d-444">Description</span><span class="sxs-lookup"><span data-stu-id="0902d-444">Description</span></span>|
|----------------|---------------|-----------------|
|<span data-ttu-id="0902d-445">Nombre</span><span class="sxs-lookup"><span data-stu-id="0902d-445">Count</span></span>|<span data-ttu-id="0902d-446">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0902d-446">win:UInt32</span></span>|<span data-ttu-id="0902d-447">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="0902d-447">The number of finalizers that were run.</span></span>|
|<span data-ttu-id="0902d-448">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0902d-448">ClrInstanceID</span></span>|<span data-ttu-id="0902d-449">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0902d-449">win:UInt16</span></span>|<span data-ttu-id="0902d-450">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0902d-450">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="0902d-451">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-451">GCCreateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0902d-452">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-452">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-453">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-453">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-454">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-454">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-455">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-455">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-456">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-456">Informational (4)</span></span>|
|<span data-ttu-id="0902d-457">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0902d-457">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0902d-458">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-458">Informational (4)</span></span>|

<span data-ttu-id="0902d-459">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-459">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-460">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-460">Event</span></span>|<span data-ttu-id="0902d-461">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-461">Event ID</span></span>|<span data-ttu-id="0902d-462">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-462">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="0902d-463">11</span><span class="sxs-lookup"><span data-stu-id="0902d-463">11</span></span>|<span data-ttu-id="0902d-464">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="0902d-464">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="0902d-465">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-465">No event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="0902d-466">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="0902d-466">GCTerminateConcurrentThread_V1 Event</span></span>

<span data-ttu-id="0902d-467">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0902d-467">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="0902d-468">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-468">Keyword for raising the event</span></span>|<span data-ttu-id="0902d-469">Niveau</span><span class="sxs-lookup"><span data-stu-id="0902d-469">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="0902d-470">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="0902d-470">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="0902d-471">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-471">Informational (4)</span></span>|
|<span data-ttu-id="0902d-472">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="0902d-472">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="0902d-473">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="0902d-473">Informational (4)</span></span>|

<span data-ttu-id="0902d-474">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0902d-474">The following table shows the event information:</span></span>

|<span data-ttu-id="0902d-475">Event</span><span class="sxs-lookup"><span data-stu-id="0902d-475">Event</span></span>|<span data-ttu-id="0902d-476">ID de l'événement</span><span class="sxs-lookup"><span data-stu-id="0902d-476">Event ID</span></span>|<span data-ttu-id="0902d-477">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0902d-477">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="0902d-478">12</span><span class="sxs-lookup"><span data-stu-id="0902d-478">12</span></span>|<span data-ttu-id="0902d-479">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="0902d-479">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="0902d-480">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="0902d-480">No event data.</span></span>

## <a name="see-also"></a><span data-ttu-id="0902d-481">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0902d-481">See also</span></span>

- [<span data-ttu-id="0902d-482">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="0902d-482">CLR ETW Events</span></span>](clr-etw-events.md)

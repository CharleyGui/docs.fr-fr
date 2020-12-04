---
title: Événements d’exécution du garbage collection
description: Consultez événements du Runtime .NET qui recueillent des informations de diagnostic spécifiques au garbage collector .NET.
ms.date: 11/13/2020
ms.topic: reference
helpviewer_keywords:
- GC events
- garbage collection events (CoreCLR)
- ETW, EventPipe, LTTng garbage collection events (CoreCLR)
ms.openlocfilehash: 2799a93f351baf23ec7a359b0b4b2be5c216dc4d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "96588611"
---
# <a name="net-runtime-garbage-collection-events"></a><span data-ttu-id="74084-103">Événements de garbage collection du Runtime .NET</span><span class="sxs-lookup"><span data-stu-id="74084-103">.NET runtime garbage collection events</span></span>

<span data-ttu-id="74084-104">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-104">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="74084-105">Ils facilitent le diagnostic et le débogage, notamment la détermination du nombre de fois que garbage collection a été effectué, la quantité de mémoire libérée pendant la garbage collection, etc. Pour plus d’informations sur l’utilisation de ces événements à des fins de diagnostic, consultez [journalisation et traçage d’applications .net](../../core/diagnostics/logging-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="74084-105">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, etc. For more information about how to use these events for diagnostic purposes, see [logging and tracing .NET applications](../../core/diagnostics/logging-tracing.md)</span></span>

## <a name="gcstart_v2-event"></a><span data-ttu-id="74084-106">Événement GCStart_V2</span><span class="sxs-lookup"><span data-stu-id="74084-106">GCStart_V2 Event</span></span>

<span data-ttu-id="74084-107">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-107">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-108">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-108">Keyword for raising the event</span></span>|<span data-ttu-id="74084-109">Level</span><span class="sxs-lookup"><span data-stu-id="74084-109">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-110">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-110">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-111">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-111">Informational (4)</span></span>|

<span data-ttu-id="74084-112">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-112">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-113">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-113">Event</span></span>|<span data-ttu-id="74084-114">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-114">Event ID</span></span>|<span data-ttu-id="74084-115">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-115">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCStart_V1`|<span data-ttu-id="74084-116">1</span><span class="sxs-lookup"><span data-stu-id="74084-116">1</span></span>|<span data-ttu-id="74084-117">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="74084-117">A garbage collection has started.</span></span>|

<span data-ttu-id="74084-118">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-118">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-119">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-119">Field name</span></span>|<span data-ttu-id="74084-120">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-120">Data type</span></span>|<span data-ttu-id="74084-121">Description</span><span class="sxs-lookup"><span data-stu-id="74084-121">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="74084-122">Le *n* ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-122">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="74084-123">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="74084-123">The generation that is being collected.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="74084-124">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="74084-124">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="74084-125">`0x0` -Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="74084-125">`0x0` - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="74084-126">`0x1` Induit.</span><span class="sxs-lookup"><span data-stu-id="74084-126">`0x1` - Induced.</span></span><br /><br /> <span data-ttu-id="74084-127">`0x2` -Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="74084-127">`0x2` - Low memory.</span></span><br /><br /> <span data-ttu-id="74084-128">`0x3` Vidé.</span><span class="sxs-lookup"><span data-stu-id="74084-128">`0x3` - Empty.</span></span><br /><br /> <span data-ttu-id="74084-129">`0x4` -Allocation du tas d’objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="74084-129">`0x4` - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="74084-130">`0x5` -Espace insuffisant (pour un tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="74084-130">`0x5` - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="74084-131">`0x6` -Espace insuffisant (pour le tas d’objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="74084-131">`0x6` - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="74084-132">`0x7` -Induite mais n’est pas forcée comme un blocage.</span><span class="sxs-lookup"><span data-stu-id="74084-132">`0x7` - Induced but not forced as blocking.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="74084-133">`0x0` -Le blocage garbage collection s’est produit en dehors des garbage collection en arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="74084-133">`0x0` - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="74084-134">`0x1` -Garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="74084-134">`0x1` - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="74084-135">`0x2` -Les garbage collection bloquantes se sont produites lors de la garbage collection d’arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="74084-135">`0x2` - Blocking garbage collection occurred during background garbage collection.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="74084-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-136">win:UInt16</span></span>|<span data-ttu-id="74084-137">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-137">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcend_v1-event"></a><span data-ttu-id="74084-138">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="74084-138">GCEnd_V1 Event</span></span>

<span data-ttu-id="74084-139">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-139">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-140">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-140">Keyword for raising the event</span></span>|<span data-ttu-id="74084-141">Level</span><span class="sxs-lookup"><span data-stu-id="74084-141">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-142">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-142">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-143">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-143">Informational (4)</span></span>|

<span data-ttu-id="74084-144">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-144">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-145">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-145">Event</span></span>|<span data-ttu-id="74084-146">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-146">Event ID</span></span>|<span data-ttu-id="74084-147">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-147">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCEnd_V1`|<span data-ttu-id="74084-148">2</span><span class="sxs-lookup"><span data-stu-id="74084-148">2</span></span>|<span data-ttu-id="74084-149">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="74084-149">The garbage collection has ended.</span></span>|

<span data-ttu-id="74084-150">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-150">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-151">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-151">Field name</span></span>|<span data-ttu-id="74084-152">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-152">Data type</span></span>|<span data-ttu-id="74084-153">Description</span><span class="sxs-lookup"><span data-stu-id="74084-153">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="74084-154">Le *n* ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-154">The *n* th garbage collection.</span></span>|
|`Depth`|`win:UInt32`|<span data-ttu-id="74084-155">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="74084-155">The generation that was collected.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="74084-156">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-156">win:UInt16</span></span>|<span data-ttu-id="74084-157">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-157">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcheapstats_v2-event"></a><span data-ttu-id="74084-158">Événement GCHeapStats_V2</span><span class="sxs-lookup"><span data-stu-id="74084-158">GCHeapStats_V2 Event</span></span>

<span data-ttu-id="74084-159">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-159">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-160">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-160">Keyword for raising the event</span></span>|<span data-ttu-id="74084-161">Level</span><span class="sxs-lookup"><span data-stu-id="74084-161">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-162">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-162">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-163">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-163">Informational (4)</span></span>|

<span data-ttu-id="74084-164">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-164">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-165">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-165">Event</span></span>|<span data-ttu-id="74084-166">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-166">Event ID</span></span>|<span data-ttu-id="74084-167">Description</span><span class="sxs-lookup"><span data-stu-id="74084-167">Description</span></span>|
|-----------|--------------|-----------------|
|`GCHeapStats_V2`|<span data-ttu-id="74084-168">4</span><span class="sxs-lookup"><span data-stu-id="74084-168">4</span></span>|<span data-ttu-id="74084-169">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-169">Shows the heap statistics at the end of each garbage collection.</span></span>|

<span data-ttu-id="74084-170">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-170">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-171">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-171">Field name</span></span>|<span data-ttu-id="74084-172">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-172">Data type</span></span>|<span data-ttu-id="74084-173">Description</span><span class="sxs-lookup"><span data-stu-id="74084-173">Description</span></span>|
|----------------|---------------|-----------------|
|`GenerationSize0`|`win:UInt64`|<span data-ttu-id="74084-174">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="74084-174">The size, in bytes, of generation 0 memory.</span></span>|
|`TotalPromotedSize0`|`win:UInt64`|<span data-ttu-id="74084-175">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="74084-175">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|
|`GenerationSize1`|`win:UInt64`|<span data-ttu-id="74084-176">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="74084-176">The size, in bytes, of generation 1 memory.</span></span>|
|`TotalPromotedSize1`|`win:UInt64`|<span data-ttu-id="74084-177">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="74084-177">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|
|`GenerationSize2`|`win:UInt64`|<span data-ttu-id="74084-178">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="74084-178">The size, in bytes, of generation 2 memory.</span></span>|
|`TotalPromotedSize2`|`win:UInt64`|<span data-ttu-id="74084-179">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="74084-179">The number of bytes that survived in generation 2 after the last collection.</span></span>|
|`GenerationSize3`|`win:UInt64`|<span data-ttu-id="74084-180">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="74084-180">The size, in bytes, of the large object heap.</span></span>|
|`TotalPromotedSize3`|`win:UInt64`|<span data-ttu-id="74084-181">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="74084-181">The number of bytes that survived in the large object heap after the last collection.</span></span>|
|`FinalizationPromotedSize`|`win:UInt64`|<span data-ttu-id="74084-182">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="74084-182">The total size, in bytes, of the objects that are ready for finalization.</span></span>|
|`FinalizationPromotedCount`|`win:UInt64`|<span data-ttu-id="74084-183">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="74084-183">The number of objects that are ready for finalization.</span></span>|
|`PinnedObjectCount`|`win:UInt32`|<span data-ttu-id="74084-184">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="74084-184">The number of pinned (unmovable) objects.</span></span>|
|`SinkBlockCount`|`win:UInt32`|<span data-ttu-id="74084-185">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="74084-185">The number of synchronization blocks in use.</span></span>|
|`GCHandleCount`|`win:UInt32`|<span data-ttu-id="74084-186">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="74084-186">The number of garbage collection handles in use.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-187">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-187">Unique ID for the instance of CoreCLR.</span></span>|
|`GenerationSize4`|`win:UInt64`|<span data-ttu-id="74084-188">Taille, en octets, du tas d’objets épinglés.</span><span class="sxs-lookup"><span data-stu-id="74084-188">The size, in bytes, of the pinned object heap.</span></span>|
|`TotalPromotedSize4`|`win:UInt64`|<span data-ttu-id="74084-189">Nombre d’octets qui ont survécu dans le tas d’objets épinglés après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="74084-189">The number of bytes that survived in the pinned object heap after the last collection.</span></span>|

## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="74084-190">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="74084-190">GCCreateSegment_V1 event</span></span>

<span data-ttu-id="74084-191">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-191">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-192">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-192">Keyword for raising the event</span></span>|<span data-ttu-id="74084-193">Level</span><span class="sxs-lookup"><span data-stu-id="74084-193">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-194">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-194">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-195">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-195">Informational (4)</span></span>|

<span data-ttu-id="74084-196">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-196">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-197">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-197">Event</span></span>|<span data-ttu-id="74084-198">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-198">Event ID</span></span>|<span data-ttu-id="74084-199">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-199">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateSegment_V1`|<span data-ttu-id="74084-200">5</span><span class="sxs-lookup"><span data-stu-id="74084-200">5</span></span>|<span data-ttu-id="74084-201">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="74084-201">A new garbage collection segment has been created.</span></span> <span data-ttu-id="74084-202">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="74084-202">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|

<span data-ttu-id="74084-203">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-203">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-204">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-204">Field name</span></span>|<span data-ttu-id="74084-205">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-205">Data type</span></span>|<span data-ttu-id="74084-206">Description</span><span class="sxs-lookup"><span data-stu-id="74084-206">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="74084-207">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="74084-207">The address of the segment.</span></span>|
|`Size`|`win:UInt64`|<span data-ttu-id="74084-208">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="74084-208">The size of the segment.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="74084-209">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="74084-209">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="74084-210">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="74084-210">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="74084-211">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="74084-211">0x2 - Read-only heap.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-212">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-212">Unique ID for the instance of CoreCLR.</span></span>|

<span data-ttu-id="74084-213">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="74084-213">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="74084-214">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="74084-214">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="74084-215">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="74084-215">GCFreeSegment_V1 event</span></span>

<span data-ttu-id="74084-216">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-216">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-217">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-217">Keyword for raising the event</span></span>|<span data-ttu-id="74084-218">Level</span><span class="sxs-lookup"><span data-stu-id="74084-218">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-219">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-219">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-220">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-220">Informational (4)</span></span>|

<span data-ttu-id="74084-221">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-221">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-222">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-222">Event</span></span>|<span data-ttu-id="74084-223">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-223">Event ID</span></span>|<span data-ttu-id="74084-224">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-224">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFreeSegment_V1`|<span data-ttu-id="74084-225">6</span><span class="sxs-lookup"><span data-stu-id="74084-225">6</span></span>|<span data-ttu-id="74084-226">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="74084-226">A garbage collection segment has been released.</span></span>|

<span data-ttu-id="74084-227">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-227">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-228">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-228">Field name</span></span>|<span data-ttu-id="74084-229">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-229">Data type</span></span>|<span data-ttu-id="74084-230">Description</span><span class="sxs-lookup"><span data-stu-id="74084-230">Description</span></span>|
|----------------|---------------|-----------------|
|`Address`|`win:UInt64`|<span data-ttu-id="74084-231">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="74084-231">The address of the segment.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-232">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-232">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="74084-233">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="74084-233">GCRestartEEBegin_V1 event</span></span>

<span data-ttu-id="74084-234">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-234">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-235">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-235">Keyword for raising the event</span></span>|<span data-ttu-id="74084-236">Level</span><span class="sxs-lookup"><span data-stu-id="74084-236">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-237">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-237">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-238">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-238">Informational (4)</span></span>|

<span data-ttu-id="74084-239">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-239">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-240">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-240">Event</span></span>|<span data-ttu-id="74084-241">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-241">Event ID</span></span>|<span data-ttu-id="74084-242">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-242">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEBegin_V1`|<span data-ttu-id="74084-243">7</span><span class="sxs-lookup"><span data-stu-id="74084-243">7</span></span>|<span data-ttu-id="74084-244">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="74084-244">Resumption from common language runtime suspension has begun.</span></span>|

<span data-ttu-id="74084-245">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-245">This event does not have any event data.</span></span>

## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="74084-246">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="74084-246">GCRestartEEEnd_V1 event</span></span>

<span data-ttu-id="74084-247">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-247">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-248">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-248">Keyword for raising the event</span></span>|<span data-ttu-id="74084-249">Level</span><span class="sxs-lookup"><span data-stu-id="74084-249">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-250">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-250">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-251">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-251">Informational (4)</span></span>|

<span data-ttu-id="74084-252">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-252">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-253">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-253">Event</span></span>|<span data-ttu-id="74084-254">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="74084-254">Event Id</span></span>|<span data-ttu-id="74084-255">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-255">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCRestartEEEnd_V1`|<span data-ttu-id="74084-256">3</span><span class="sxs-lookup"><span data-stu-id="74084-256">3</span></span>|<span data-ttu-id="74084-257">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="74084-257">Resumption from common language runtime suspension has ended.</span></span>|

<span data-ttu-id="74084-258">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-258">This event does not have any event data.</span></span>

## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="74084-259">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="74084-259">GCSuspendEEEnd_V1 event</span></span>

<span data-ttu-id="74084-260">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-260">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-261">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-261">Keyword for raising the event</span></span>|<span data-ttu-id="74084-262">Level</span><span class="sxs-lookup"><span data-stu-id="74084-262">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-263">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-263">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-264">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-264">Informational (4)</span></span>|

<span data-ttu-id="74084-265">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-265">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-266">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-266">Event</span></span>|<span data-ttu-id="74084-267">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-267">Event ID</span></span>|<span data-ttu-id="74084-268">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-268">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEEnd_V1`|<span data-ttu-id="74084-269">8</span><span class="sxs-lookup"><span data-stu-id="74084-269">8</span></span>|<span data-ttu-id="74084-270">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-270">End of suspension of the execution engine for garbage collection.</span></span>|

<span data-ttu-id="74084-271">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-271">This event does not have any event data.</span></span>

## <a name="gcsuspendeebegin_v1-event"></a><span data-ttu-id="74084-272">Événement GCSuspendEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="74084-272">GCSuspendEEBegin_V1 event</span></span>

<span data-ttu-id="74084-273">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-273">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-274">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-274">Keyword for raising the event</span></span>|<span data-ttu-id="74084-275">Level</span><span class="sxs-lookup"><span data-stu-id="74084-275">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-276">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-276">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-277">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-277">Informational (4)</span></span>|

<span data-ttu-id="74084-278">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-278">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-279">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-279">Event</span></span>|<span data-ttu-id="74084-280">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-280">Event ID</span></span>|<span data-ttu-id="74084-281">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-281">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCSuspendEEBegin_V1`|<span data-ttu-id="74084-282">8</span><span class="sxs-lookup"><span data-stu-id="74084-282">8</span></span>|<span data-ttu-id="74084-283">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-283">Start of suspension of the execution engine for garbage collection.</span></span>|

|<span data-ttu-id="74084-284">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-284">Field name</span></span>|<span data-ttu-id="74084-285">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-285">Data type</span></span>|<span data-ttu-id="74084-286">Description</span><span class="sxs-lookup"><span data-stu-id="74084-286">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="74084-287">Le *n* ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="74084-287">The *n* th garbage collection.</span></span>|
|`Reason`|`win:UInt32`|<span data-ttu-id="74084-288">Raison de la suspension EE.</span><span class="sxs-lookup"><span data-stu-id="74084-288">Reason for EE suspension.</span></span><br/><br/><span data-ttu-id="74084-289">`0x0`: Suspendre pour d’autres</span><span class="sxs-lookup"><span data-stu-id="74084-289">`0x0`: Suspend for Other</span></span><br/><br/><span data-ttu-id="74084-290">`0x1`: Suspend pour GC.</span><span class="sxs-lookup"><span data-stu-id="74084-290">`0x1`: Suspend for GC.</span></span><br/><br/><span data-ttu-id="74084-291">`0x2`: Suspend for AppDomain Shutdown.</span><span class="sxs-lookup"><span data-stu-id="74084-291">`0x2`: Suspend for AppDomain shutdown.</span></span><br/><br/><span data-ttu-id="74084-292">`0x3`: Suspend la présentation du code.</span><span class="sxs-lookup"><span data-stu-id="74084-292">`0x3`: Suspend for code pitching.</span></span><br/><br/><span data-ttu-id="74084-293">`0x4`: Suspendre pour l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="74084-293">`0x4`: Suspend for shutdown.</span></span><br/><br/><span data-ttu-id="74084-294">`0x5`: Suspend pour le débogueur.</span><span class="sxs-lookup"><span data-stu-id="74084-294">`0x5`: Suspend for debugger.</span></span><br/><br/><span data-ttu-id="74084-295">`0x6`: Suspension de la préparation du catalogue global.</span><span class="sxs-lookup"><span data-stu-id="74084-295">`0x6`: Suspend for GC Prep.</span></span><br/><br/><span data-ttu-id="74084-296">`0x7`: Interrompre le balayage du débogueur</span><span class="sxs-lookup"><span data-stu-id="74084-296">`0x7`: Suspend for debugger sweep</span></span>|

## <a name="gcallocationtick_v3-event"></a><span data-ttu-id="74084-297">Événement GCAllocationTick_V3</span><span class="sxs-lookup"><span data-stu-id="74084-297">GCAllocationTick_V3 event</span></span>

<span data-ttu-id="74084-298">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-298">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-299">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-299">Keyword for raising the event</span></span>|<span data-ttu-id="74084-300">Level</span><span class="sxs-lookup"><span data-stu-id="74084-300">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-301">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-301">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-302">Verbose (4)</span><span class="sxs-lookup"><span data-stu-id="74084-302">Verbose (4)</span></span>|

<span data-ttu-id="74084-303">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-303">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-304">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-304">Event</span></span>|<span data-ttu-id="74084-305">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-305">Event ID</span></span>|<span data-ttu-id="74084-306">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-306">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCAllocationTick_V3`|<span data-ttu-id="74084-307">10</span><span class="sxs-lookup"><span data-stu-id="74084-307">10</span></span>|<span data-ttu-id="74084-308">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="74084-308">Each time approximately 100 KB is allocated.</span></span>|

<span data-ttu-id="74084-309">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-309">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-310">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-310">Field name</span></span>|<span data-ttu-id="74084-311">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-311">Data type</span></span>|<span data-ttu-id="74084-312">Description</span><span class="sxs-lookup"><span data-stu-id="74084-312">Description</span></span>|
|----------------|---------------|-----------------|
|`AllocationAmount`|`win:UInt32`|<span data-ttu-id="74084-313">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="74084-313">The allocation size, in bytes.</span></span> <span data-ttu-id="74084-314">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="74084-314">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="74084-315">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="74084-315">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="74084-316">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="74084-316">Use `AllocationAmount64` for very large allocations.</span></span>|
|`AllocationKind`|`win:UInt32`|<span data-ttu-id="74084-317">`0x0` -Allocation d’objets de petite taille (l’allocation est dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="74084-317">`0x0` - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="74084-318">`0x1` -Allocation d’objets volumineux (l’allocation est dans le tas d’objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="74084-318">`0x1` - Large object allocation (allocation is in large object heap).</span></span>|
|`AllocationAmount64`|`win:UInt64`|<span data-ttu-id="74084-319">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="74084-319">The allocation size, in bytes.</span></span> <span data-ttu-id="74084-320">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="74084-320">This value is accurate for very large allocations.</span></span>|
|`TypeId`|`win:Pointer`|<span data-ttu-id="74084-321">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="74084-321">The address of the MethodTable.</span></span> <span data-ttu-id="74084-322">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="74084-322">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="74084-323">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="74084-323">The name of the type that was allocated.</span></span> <span data-ttu-id="74084-324">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="74084-324">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|
|`HeapIndex`|`win:UInt32`|<span data-ttu-id="74084-325">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="74084-325">The heap where the object was allocated.</span></span> <span data-ttu-id="74084-326">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="74084-326">This value is 0 (zero) when running with workstation garbage collection.</span></span>|
|`Address`|`win:Pointer`|<span data-ttu-id="74084-327">Adresse du dernier objet alloué.</span><span class="sxs-lookup"><span data-stu-id="74084-327">The address of the last allocated object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-328">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-328">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="74084-329">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="74084-329">GCCreateConcurrentThread_V1 event</span></span>

<span data-ttu-id="74084-330">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-330">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-331">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-331">Keyword for raising the event</span></span>|<span data-ttu-id="74084-332">Level</span><span class="sxs-lookup"><span data-stu-id="74084-332">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-333">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-333">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-334">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-334">Informational (4)</span></span>|
|<span data-ttu-id="74084-335">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="74084-335">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="74084-336">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-336">Informational (4)</span></span>|

<span data-ttu-id="74084-337">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-337">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-338">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-338">Event</span></span>|<span data-ttu-id="74084-339">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-339">Event ID</span></span>|<span data-ttu-id="74084-340">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-340">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="74084-341">11</span><span class="sxs-lookup"><span data-stu-id="74084-341">11</span></span>|<span data-ttu-id="74084-342">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="74084-342">Concurrent garbage collection thread was created.</span></span>|

<span data-ttu-id="74084-343">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-343">This event does not have any event data.</span></span>

## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="74084-344">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="74084-344">GCTerminateConcurrentThread_V1 event</span></span>

<span data-ttu-id="74084-345">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-345">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-346">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-346">Keyword for raising the event</span></span>|<span data-ttu-id="74084-347">Level</span><span class="sxs-lookup"><span data-stu-id="74084-347">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-348">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-348">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-349">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-349">Informational (4)</span></span>|
|<span data-ttu-id="74084-350">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="74084-350">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="74084-351">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-351">Informational (4)</span></span>|

<span data-ttu-id="74084-352">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-352">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-353">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-353">Event</span></span>|<span data-ttu-id="74084-354">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-354">Event ID</span></span>|<span data-ttu-id="74084-355">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-355">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="74084-356">12</span><span class="sxs-lookup"><span data-stu-id="74084-356">12</span></span>|<span data-ttu-id="74084-357">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="74084-357">Concurrent garbage collection thread was terminated.</span></span>|

<span data-ttu-id="74084-358">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-358">This event does not have any event data.</span></span>

## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="74084-359">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="74084-359">GCFinalizersBegin_V1 event</span></span>

<span data-ttu-id="74084-360">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-360">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-361">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-361">Keyword for raising the event</span></span>|<span data-ttu-id="74084-362">Level</span><span class="sxs-lookup"><span data-stu-id="74084-362">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-363">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-363">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-364">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-364">Informational (4)</span></span>|

<span data-ttu-id="74084-365">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-365">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-366">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-366">Event</span></span>|<span data-ttu-id="74084-367">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-367">Event ID</span></span>|<span data-ttu-id="74084-368">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-368">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersBegin_V1`|<span data-ttu-id="74084-369">14</span><span class="sxs-lookup"><span data-stu-id="74084-369">14</span></span>|<span data-ttu-id="74084-370">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="74084-370">The start of running finalizers.</span></span>|

<span data-ttu-id="74084-371">Cet événement n’a pas de données d’événement.</span><span class="sxs-lookup"><span data-stu-id="74084-371">This event does not have any event data.</span></span>

## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="74084-372">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="74084-372">GCFinalizersEnd_V1 event</span></span>

<span data-ttu-id="74084-373">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-373">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-374">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-374">Keyword for raising the event</span></span>|<span data-ttu-id="74084-375">Level</span><span class="sxs-lookup"><span data-stu-id="74084-375">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-376">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-376">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-377">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-377">Informational (4)</span></span>|

<span data-ttu-id="74084-378">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-378">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-379">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-379">Event</span></span>|<span data-ttu-id="74084-380">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-380">Event ID</span></span>|<span data-ttu-id="74084-381">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-381">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCFinalizersEnd_V1`|<span data-ttu-id="74084-382">13</span><span class="sxs-lookup"><span data-stu-id="74084-382">13</span></span>|<span data-ttu-id="74084-383">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="74084-383">The end of running finalizers.</span></span>|

<span data-ttu-id="74084-384">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-384">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-385">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-385">Field name</span></span>|<span data-ttu-id="74084-386">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-386">Data type</span></span>|<span data-ttu-id="74084-387">Description</span><span class="sxs-lookup"><span data-stu-id="74084-387">Description</span></span>|
|----------------|---------------|-----------------|
|`Count`|`win:UInt32`|<span data-ttu-id="74084-388">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="74084-388">The number of finalizers that were run.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="74084-389">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-389">win:UInt16</span></span>|<span data-ttu-id="74084-390">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-390">Unique ID for the instance of CLR or CoreCLR.</span></span>|

## <a name="setgchandle-event"></a><span data-ttu-id="74084-391">Événement SetGCHandle</span><span class="sxs-lookup"><span data-stu-id="74084-391">SetGCHandle event</span></span>

<span data-ttu-id="74084-392">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-392">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-393">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-393">Keyword for raising the event</span></span>|<span data-ttu-id="74084-394">Level</span><span class="sxs-lookup"><span data-stu-id="74084-394">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-395">`GCHandleKeyword` 0X2</span><span class="sxs-lookup"><span data-stu-id="74084-395">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="74084-396">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-396">Informational (4)</span></span>|

<span data-ttu-id="74084-397">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-397">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-398">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-398">Event</span></span>|<span data-ttu-id="74084-399">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-399">Event ID</span></span>|<span data-ttu-id="74084-400">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-400">Raised when</span></span>|
|-----------|--------------|-----------------|
|`SetGCHandle`|<span data-ttu-id="74084-401">30</span><span class="sxs-lookup"><span data-stu-id="74084-401">30</span></span>|<span data-ttu-id="74084-402">Un descripteur GC a été défini.</span><span class="sxs-lookup"><span data-stu-id="74084-402">A GC Handle has been set.</span></span>|

<span data-ttu-id="74084-403">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-403">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-404">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-404">Field name</span></span>|<span data-ttu-id="74084-405">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-405">Data type</span></span>|<span data-ttu-id="74084-406">Description</span><span class="sxs-lookup"><span data-stu-id="74084-406">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="74084-407">Adresse du handle alloué.</span><span class="sxs-lookup"><span data-stu-id="74084-407">The address of the allocated handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="74084-408">Adresse de l’objet dont le handle a été créé.</span><span class="sxs-lookup"><span data-stu-id="74084-408">The address of the object whose handle was created.</span></span>|
|`Kind`|`win:UInt32`|<span data-ttu-id="74084-409">Type de descripteur GC défini.</span><span class="sxs-lookup"><span data-stu-id="74084-409">The type of GC handle that was set.</span></span> <br /><br /><span data-ttu-id="74084-410">`0x0`: WeakShort</span><span class="sxs-lookup"><span data-stu-id="74084-410">`0x0`: WeakShort</span></span> <br/><br/><span data-ttu-id="74084-411">`0x1`: WeakLong</span><span class="sxs-lookup"><span data-stu-id="74084-411">`0x1`: WeakLong</span></span> <br /><br /><span data-ttu-id="74084-412">`0x2`: Fort</span><span class="sxs-lookup"><span data-stu-id="74084-412">`0x2`: Strong</span></span> <br /><br /><span data-ttu-id="74084-413">`0x3`: Épinglé</span><span class="sxs-lookup"><span data-stu-id="74084-413">`0x3`: Pinned</span></span> <br /><br /><span data-ttu-id="74084-414">`0x4`: Variable</span><span class="sxs-lookup"><span data-stu-id="74084-414">`0x4`: Variable</span></span><br /><br /><span data-ttu-id="74084-415">`0x5`: RefCounted</span><span class="sxs-lookup"><span data-stu-id="74084-415">`0x5`: RefCounted</span></span> <br /><br /><span data-ttu-id="74084-416">`0x6`: Dépendant</span><span class="sxs-lookup"><span data-stu-id="74084-416">`0x6`: Dependent</span></span><br /><br /><span data-ttu-id="74084-417">`0x7`: AsyncPinned</span><span class="sxs-lookup"><span data-stu-id="74084-417">`0x7`: AsyncPinned</span></span><br /><br /><span data-ttu-id="74084-418">`0x8`: Handle sizedref</span><span class="sxs-lookup"><span data-stu-id="74084-418">`0x8`: SizedRef</span></span>|
|`Generation`|`win:UInt32`|<span data-ttu-id="74084-419">Génération de l’objet dont le handle a été créé.</span><span class="sxs-lookup"><span data-stu-id="74084-419">The generation of the object whose handle was created.</span></span>|
|`AppDomainID`|`win:UInt64`|<span data-ttu-id="74084-420">ID AppDomain.</span><span class="sxs-lookup"><span data-stu-id="74084-420">The AppDomain ID.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-421">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-421">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="destroygchandle-event"></a><span data-ttu-id="74084-422">Événement DestroyGCHandle</span><span class="sxs-lookup"><span data-stu-id="74084-422">DestroyGCHandle event</span></span>

<span data-ttu-id="74084-423">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-423">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-424">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-424">Keyword for raising the event</span></span>|<span data-ttu-id="74084-425">Level</span><span class="sxs-lookup"><span data-stu-id="74084-425">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-426">`GCHandleKeyword` 0X2</span><span class="sxs-lookup"><span data-stu-id="74084-426">`GCHandleKeyword` (0x2)</span></span>|<span data-ttu-id="74084-427">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="74084-427">Informational (4)</span></span>|

<span data-ttu-id="74084-428">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-428">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-429">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-429">Event</span></span>|<span data-ttu-id="74084-430">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-430">Event ID</span></span>|<span data-ttu-id="74084-431">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-431">Raised when</span></span>|
|-----------|--------------|-----------------|
|`DestroyGCHandle`|<span data-ttu-id="74084-432">31</span><span class="sxs-lookup"><span data-stu-id="74084-432">31</span></span>|<span data-ttu-id="74084-433">Un descripteur GC est détruit.</span><span class="sxs-lookup"><span data-stu-id="74084-433">A GC Handle is destroyed.</span></span>|

<span data-ttu-id="74084-434">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-434">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-435">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-435">Field name</span></span>|<span data-ttu-id="74084-436">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-436">Data type</span></span>|<span data-ttu-id="74084-437">Description</span><span class="sxs-lookup"><span data-stu-id="74084-437">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="74084-438">Adresse du handle détruit.</span><span class="sxs-lookup"><span data-stu-id="74084-438">The address of the destroyed handle.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="74084-439">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-439">win:UInt16</span></span>|<span data-ttu-id="74084-440">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-440">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="pinobjectatgctime-event"></a><span data-ttu-id="74084-441">Événement PinObjectAtGCTime</span><span class="sxs-lookup"><span data-stu-id="74084-441">PinObjectAtGCTime event</span></span>

<span data-ttu-id="74084-442">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-442">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-443">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-443">Keyword for raising the event</span></span>|<span data-ttu-id="74084-444">Level</span><span class="sxs-lookup"><span data-stu-id="74084-444">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-445">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-445">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-446">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="74084-446">Verbose (5)</span></span>|

<span data-ttu-id="74084-447">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-447">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-448">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-448">Event</span></span>|<span data-ttu-id="74084-449">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-449">Event ID</span></span>|<span data-ttu-id="74084-450">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-450">Raised when</span></span>|
|-----------|--------------|-----------------|
|`PinObjectAtGCTime`|<span data-ttu-id="74084-451">33</span><span class="sxs-lookup"><span data-stu-id="74084-451">33</span></span>|<span data-ttu-id="74084-452">Un objet a été épinglé pendant un GC.</span><span class="sxs-lookup"><span data-stu-id="74084-452">An object was pinned during a GC.</span></span>|

<span data-ttu-id="74084-453">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-453">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-454">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-454">Field name</span></span>|<span data-ttu-id="74084-455">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-455">Data type</span></span>|<span data-ttu-id="74084-456">Description</span><span class="sxs-lookup"><span data-stu-id="74084-456">Description</span></span>|
|----------------|---------------|-----------------|
|`HandleID`|`win:Pointer`|<span data-ttu-id="74084-457">Adresse du handle.</span><span class="sxs-lookup"><span data-stu-id="74084-457">The address of the handle.</span></span>|
|`ObjectID`|`win:Pointer`|<span data-ttu-id="74084-458">Adresse de l’objet épinglé.</span><span class="sxs-lookup"><span data-stu-id="74084-458">The address of the pinned object.</span></span>|
|`ObjectSize`|`win:UInt64`|<span data-ttu-id="74084-459">Taille de l’objet épinglé.</span><span class="sxs-lookup"><span data-stu-id="74084-459">The size of the pinned object.</span></span>|
|`TypeName`|`win:UnicodeString`|<span data-ttu-id="74084-460">Nom du type de l’objet épinglé.</span><span class="sxs-lookup"><span data-stu-id="74084-460">The name of the type of the pinned object.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-461">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-461">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gctriggered-event"></a><span data-ttu-id="74084-462">Événement GCTriggered</span><span class="sxs-lookup"><span data-stu-id="74084-462">GCTriggered event</span></span>

<span data-ttu-id="74084-463">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-463">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-464">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-464">Keyword for raising the event</span></span>|<span data-ttu-id="74084-465">Level</span><span class="sxs-lookup"><span data-stu-id="74084-465">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-466">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-466">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-467">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="74084-467">Verbose (5)</span></span>|

<span data-ttu-id="74084-468">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-468">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-469">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-469">Event</span></span>|<span data-ttu-id="74084-470">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-470">Event ID</span></span>|<span data-ttu-id="74084-471">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-471">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCTriggered`|<span data-ttu-id="74084-472">33</span><span class="sxs-lookup"><span data-stu-id="74084-472">33</span></span>|<span data-ttu-id="74084-473">Un GC a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="74084-473">A GC has been triggered.</span></span>|

<span data-ttu-id="74084-474">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-474">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-475">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-475">Field name</span></span>|<span data-ttu-id="74084-476">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-476">Data type</span></span>|<span data-ttu-id="74084-477">Description</span><span class="sxs-lookup"><span data-stu-id="74084-477">Description</span></span>|
|----------------|---------------|-----------------|
|`Reason`|`win:UInt32`|<span data-ttu-id="74084-478">Raison pour laquelle un GC a été déclenché.</span><span class="sxs-lookup"><span data-stu-id="74084-478">The reason a GC was triggered.</span></span><br/><br/><span data-ttu-id="74084-479">`0x0`: AllocSmall</span><span class="sxs-lookup"><span data-stu-id="74084-479">`0x0`: AllocSmall</span></span><br/><br/><span data-ttu-id="74084-480">`0x1`: Induite</span><span class="sxs-lookup"><span data-stu-id="74084-480">`0x1`: Induced</span></span> <br/><br/><span data-ttu-id="74084-481">`0x2`: LowMemory</span><span class="sxs-lookup"><span data-stu-id="74084-481">`0x2`: LowMemory</span></span> <br/><br/><span data-ttu-id="74084-482">`0x3`: Vide</span><span class="sxs-lookup"><span data-stu-id="74084-482">`0x3`: Empty</span></span> <br/><br/><span data-ttu-id="74084-483">`0x4`: AllocLarge</span><span class="sxs-lookup"><span data-stu-id="74084-483">`0x4`: AllocLarge</span></span> <br/><br/><span data-ttu-id="74084-484">`0x5`: OutOfSpaceSmallObjectHeap</span><span class="sxs-lookup"><span data-stu-id="74084-484">`0x5`: OutOfSpaceSmallObjectHeap</span></span> <br/><br/><span data-ttu-id="74084-485">`0x6`: OutOfSpaceLargeObjectHeap</span><span class="sxs-lookup"><span data-stu-id="74084-485">`0x6`: OutOfSpaceLargeObjectHeap</span></span> <br/><br/><span data-ttu-id="74084-486">`0x7`:InducedNoForce</span><span class="sxs-lookup"><span data-stu-id="74084-486">`0x7`:InducedNoForce</span></span> <br/><br/><span data-ttu-id="74084-487">`0x8`: Contrainte</span><span class="sxs-lookup"><span data-stu-id="74084-487">`0x8`: Stress</span></span> <br/><br/><span data-ttu-id="74084-488">`0x9`: InducedLowMemory</span><span class="sxs-lookup"><span data-stu-id="74084-488">`0x9`: InducedLowMemory</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-489">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-489">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="increasememorypressure-event"></a><span data-ttu-id="74084-490">Événement IncreaseMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="74084-490">IncreaseMemoryPressure event</span></span>

<span data-ttu-id="74084-491">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-491">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-492">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-492">Keyword for raising the event</span></span>|<span data-ttu-id="74084-493">Level</span><span class="sxs-lookup"><span data-stu-id="74084-493">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-494">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-494">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-495">Informations (4)</span><span class="sxs-lookup"><span data-stu-id="74084-495">Information (4)</span></span>|

<span data-ttu-id="74084-496">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-496">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-497">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-497">Event</span></span>|<span data-ttu-id="74084-498">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-498">Event ID</span></span>|<span data-ttu-id="74084-499">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-499">Raised when</span></span>|
|----------------|---------------|-----------------|
|`IncreaseMemoryPressure`|<span data-ttu-id="74084-500">200</span><span class="sxs-lookup"><span data-stu-id="74084-500">200</span></span>|<span data-ttu-id="74084-501">La sollicitation de la mémoire a été augmentée.</span><span class="sxs-lookup"><span data-stu-id="74084-501">Memory pressure was increased.</span></span>|

<span data-ttu-id="74084-502">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-502">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-503">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-503">Field Name</span></span>|<span data-ttu-id="74084-504">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-504">Data type</span></span>|<span data-ttu-id="74084-505">Description</span><span class="sxs-lookup"><span data-stu-id="74084-505">Description</span></span>|
|----------------|---------------|-----------------|
|`ClrInstanceID`|<span data-ttu-id="74084-506">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-506">win:UInt16</span></span>|<span data-ttu-id="74084-507">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-507">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="decreasememorypressure-event"></a><span data-ttu-id="74084-508">Événement DecreaseMemoryPressure</span><span class="sxs-lookup"><span data-stu-id="74084-508">DecreaseMemoryPressure event</span></span>

<span data-ttu-id="74084-509">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-509">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-510">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-510">Keyword for raising the event</span></span>|<span data-ttu-id="74084-511">Level</span><span class="sxs-lookup"><span data-stu-id="74084-511">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-512">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-512">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-513">Informations (4)</span><span class="sxs-lookup"><span data-stu-id="74084-513">Information (4)</span></span>|

<span data-ttu-id="74084-514">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-514">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-515">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-515">Event</span></span>|<span data-ttu-id="74084-516">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-516">Event ID</span></span>|<span data-ttu-id="74084-517">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-517">Raised when</span></span>|
|----------------|---------------|-----------------|
|`DecreaseMemoryPressure`|<span data-ttu-id="74084-518">201</span><span class="sxs-lookup"><span data-stu-id="74084-518">201</span></span>|<span data-ttu-id="74084-519">La sollicitation de la mémoire a été réduite.</span><span class="sxs-lookup"><span data-stu-id="74084-519">Memory pressure was decreased.</span></span>|

<span data-ttu-id="74084-520">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-520">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-521">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-521">Field Name</span></span>|<span data-ttu-id="74084-522">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-522">Data type</span></span>|<span data-ttu-id="74084-523">Description</span><span class="sxs-lookup"><span data-stu-id="74084-523">Description</span></span>|
|----------------|---------------|-----------------|
|`BytesFreed`|`win:UInt32`|<span data-ttu-id="74084-524">Octets libérés.</span><span class="sxs-lookup"><span data-stu-id="74084-524">Bytes freed.</span></span>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-525">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-525">Unique ID for the instance of CoreCLR.</span></span>|

## <a name="gcmarkwithtype-event"></a><span data-ttu-id="74084-526">Événement GCMarkWithType</span><span class="sxs-lookup"><span data-stu-id="74084-526">GCMarkWithType event</span></span>

<span data-ttu-id="74084-527">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-527">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-528">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-528">Keyword for raising the event</span></span>|<span data-ttu-id="74084-529">Level</span><span class="sxs-lookup"><span data-stu-id="74084-529">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-530">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-530">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-531">Informations (4)</span><span class="sxs-lookup"><span data-stu-id="74084-531">Information (4)</span></span>|

<span data-ttu-id="74084-532">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-532">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-533">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-533">Event</span></span>|<span data-ttu-id="74084-534">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-534">Event ID</span></span>|<span data-ttu-id="74084-535">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-535">Raised when</span></span>|
|----------------|---------------|-----------------|
|`GCMarkWithType`|<span data-ttu-id="74084-536">202</span><span class="sxs-lookup"><span data-stu-id="74084-536">202</span></span>|<span data-ttu-id="74084-537">Une racine GC a été marquée au cours de la phase de marque GC.</span><span class="sxs-lookup"><span data-stu-id="74084-537">A GC root has been marked during GC mark phase.</span></span>|

<span data-ttu-id="74084-538">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-538">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-539">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-539">Field Name</span></span>|<span data-ttu-id="74084-540">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-540">Data type</span></span>|<span data-ttu-id="74084-541">Description</span><span class="sxs-lookup"><span data-stu-id="74084-541">Description</span></span>|
|----------------|---------------|-----------------|
|`HeapNum`|`win:UInt32`|<span data-ttu-id="74084-542">Numéro du tas.</span><span class="sxs-lookup"><span data-stu-id="74084-542">The heap number.</span></span>|
|`ClrInstanceID`|<span data-ttu-id="74084-543">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="74084-543">win:UInt16</span></span>|<span data-ttu-id="74084-544">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-544">Unique ID for the instance of CoreCLR.</span></span>|
|`Type`|`win:UInt32`|<span data-ttu-id="74084-545">Type de racine GC.</span><span class="sxs-lookup"><span data-stu-id="74084-545">The GC root type.</span></span><br/><br/><span data-ttu-id="74084-546">`0x0`: Pile</span><span class="sxs-lookup"><span data-stu-id="74084-546">`0x0`: Stack</span></span><br/><br/><span data-ttu-id="74084-547">`0x1`: Finaliseur</span><span class="sxs-lookup"><span data-stu-id="74084-547">`0x1`: Finalizer</span></span><br/><br/><span data-ttu-id="74084-548">`0x2`: Handle</span><span class="sxs-lookup"><span data-stu-id="74084-548">`0x2`: Handle</span></span><br/><br/><span data-ttu-id="74084-549">`0x3`: Plus ancien</span><span class="sxs-lookup"><span data-stu-id="74084-549">`0x3`: Older</span></span><br/><br/><span data-ttu-id="74084-550">`0x4`: Handle sizedref</span><span class="sxs-lookup"><span data-stu-id="74084-550">`0x4`: SizedRef</span></span><br/><br/><span data-ttu-id="74084-551">`0x5`: Dépassement de capacité</span><span class="sxs-lookup"><span data-stu-id="74084-551">`0x5`: Overflow</span></span><br/><br/>|
|`Bytes`|`win:UInt64`|<span data-ttu-id="74084-552">Nombre d’octets marqués.</span><span class="sxs-lookup"><span data-stu-id="74084-552">The number of bytes marked.</span></span>|

## <a name="gcjoin_v2-event"></a><span data-ttu-id="74084-553">Événement GCJoin_V2</span><span class="sxs-lookup"><span data-stu-id="74084-553">GCJoin_V2 event</span></span>

<span data-ttu-id="74084-554">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="74084-554">The following table shows the keyword and level:</span></span>

|<span data-ttu-id="74084-555">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="74084-555">Keyword for raising the event</span></span>|<span data-ttu-id="74084-556">Level</span><span class="sxs-lookup"><span data-stu-id="74084-556">Level</span></span>|
|-----------------------------------|-----------|
|<span data-ttu-id="74084-557">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="74084-557">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="74084-558">Détaillé (5)</span><span class="sxs-lookup"><span data-stu-id="74084-558">Verbose (5)</span></span>|

<span data-ttu-id="74084-559">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="74084-559">The following table shows the event information:</span></span>

|<span data-ttu-id="74084-560">Événement</span><span class="sxs-lookup"><span data-stu-id="74084-560">Event</span></span>|<span data-ttu-id="74084-561">ID de l’événement</span><span class="sxs-lookup"><span data-stu-id="74084-561">Event ID</span></span>|<span data-ttu-id="74084-562">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="74084-562">Raised when</span></span>|
|-----------|--------------|-----------------|
|`GCJoin_V2`|<span data-ttu-id="74084-563">203</span><span class="sxs-lookup"><span data-stu-id="74084-563">203</span></span>|<span data-ttu-id="74084-564">Thread de GC joint.</span><span class="sxs-lookup"><span data-stu-id="74084-564">A GC thread joined.</span></span>|

<span data-ttu-id="74084-565">Le tableau ci-dessous montre les données d’événements.</span><span class="sxs-lookup"><span data-stu-id="74084-565">The following table shows the event data:</span></span>

|<span data-ttu-id="74084-566">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="74084-566">Field name</span></span>|<span data-ttu-id="74084-567">Type de données</span><span class="sxs-lookup"><span data-stu-id="74084-567">Data type</span></span>|<span data-ttu-id="74084-568">Description</span><span class="sxs-lookup"><span data-stu-id="74084-568">Description</span></span>|
|----------------|---------------|-----------------|
|`Heap`|`win:UInt32`|<span data-ttu-id="74084-569">Numéro du tas</span><span class="sxs-lookup"><span data-stu-id="74084-569">The heap number</span></span>|
|`JoinTime`|`win:UInt32`|<span data-ttu-id="74084-570">Indique si cet événement est déclenché au début d’une jointure ou d’une fin de jointure (pour le début de la jointure `0x0` , pour la fin de la `0x1` jointure)</span><span class="sxs-lookup"><span data-stu-id="74084-570">Indicates whether this event is fired at the start of a join or end of a join (`0x0` for join start, `0x1` for join end)</span></span>|
|`JoinType`|`win:UInt32`|<span data-ttu-id="74084-571">Type de jointure.</span><span class="sxs-lookup"><span data-stu-id="74084-571">The join type.</span></span> <br/><br/><span data-ttu-id="74084-572">`0x0`: Dernière jointure</span><span class="sxs-lookup"><span data-stu-id="74084-572">`0x0`: Last Join</span></span><br/><br/><span data-ttu-id="74084-573">`0x1`: Joindre</span><span class="sxs-lookup"><span data-stu-id="74084-573">`0x1`: Join</span></span> <br/><br/><span data-ttu-id="74084-574">`0x2`: Redémarrer</span><span class="sxs-lookup"><span data-stu-id="74084-574">`0x2`: Restart</span></span> <br/><br/><span data-ttu-id="74084-575">`0x3`: Première jointure inverse</span><span class="sxs-lookup"><span data-stu-id="74084-575">`0x3`: First Reverse Join</span></span><br/><br/><span data-ttu-id="74084-576">`0x4`: Jointure inverse</span><span class="sxs-lookup"><span data-stu-id="74084-576">`0x4`: Reverse Join</span></span><br/><br/>|
|`ClrInstanceID`|`win:UInt16`|<span data-ttu-id="74084-577">ID unique de l’instance de CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="74084-577">Unique ID for the instance of CoreCLR.</span></span>|

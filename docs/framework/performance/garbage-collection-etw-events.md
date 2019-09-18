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
ms.openlocfilehash: ec90d022a0c72782f413a84b6fbd2c1b8d663a73
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046497"
---
# <a name="garbage-collection-etw-events"></a><span data-ttu-id="f19a9-102">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="f19a9-102">Garbage Collection ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f19a9-103">Ces événements collectent des informations relatives au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-103">These events collect information pertaining to garbage collection.</span></span> <span data-ttu-id="f19a9-104">Ils vous aident dans le diagnostic et le débogage, y compris pour déterminer combien de fois le garbage collection a été effectué, la quantité de mémoire libérée pendant le garbage collection, etc.</span><span class="sxs-lookup"><span data-stu-id="f19a9-104">They help in diagnostics and debugging, including determining how many times garbage collection was performed, how much memory was freed during garbage collection, and so on.</span></span>  
  
 <span data-ttu-id="f19a9-105">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="f19a9-105">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="f19a9-106">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-106">GCStart_V1 Event</span></span>](#gcstart_v1_event)  
  
- [<span data-ttu-id="f19a9-107">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-107">GCEnd_V1 Event</span></span>](#gcend_v1_event)  
  
- [<span data-ttu-id="f19a9-108">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-108">GCHeapStats_V1 Event</span></span>](#gcheapstats_v1_event)  
  
- [<span data-ttu-id="f19a9-109">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-109">GCCreateSegment_V1 Event</span></span>](#gccreatesegment_v1_event)  
  
- [<span data-ttu-id="f19a9-110">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-110">GCFreeSegment_V1 Event</span></span>](#gcfreesegment_v1_event)  
  
- [<span data-ttu-id="f19a9-111">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-111">GCRestartEEBegin_V1 Event</span></span>](#gcrestarteebegin_v1_event)  
  
- [<span data-ttu-id="f19a9-112">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-112">GCRestartEEEnd_V1 Event</span></span>](#gcrestarteeend_v1_event)  
  
- [<span data-ttu-id="f19a9-113">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-113">GCSuspendEE_V1 Event</span></span>](#gcsuspendee_v1_event)  
  
- [<span data-ttu-id="f19a9-114">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-114">GCSuspendEEEnd_V1 Event</span></span>](#gcsuspendeeend_v1_event)  
  
- [<span data-ttu-id="f19a9-115">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="f19a9-115">GCAllocationTick_V2 Event</span></span>](#gcallocationtick_v2_event)  
  
- [<span data-ttu-id="f19a9-116">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-116">GCFinalizersBegin_V1 Event</span></span>](#gcfinalizersbegin_v1_event)  
  
- [<span data-ttu-id="f19a9-117">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-117">GCFinalizersEnd_V1 Event</span></span>](#gcfinalizersend_v1_event)  
  
- [<span data-ttu-id="f19a9-118">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-118">GCCreateConcurrentThread_V1 Event</span></span>](#gccreateconcurrentthread_v1_event)  
  
- [<span data-ttu-id="f19a9-119">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-119">GCTerminateConcurrentThread_V1 Event</span></span>](#gcterminateconcurrentthread_v1_event)  
  
<a name="gcstart_v1_event"></a>   
## <a name="gcstart_v1-event"></a><span data-ttu-id="f19a9-120">Événement GCStart_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-120">GCStart_V1 Event</span></span>  
 <span data-ttu-id="f19a9-121">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-121">The following table shows the keyword and level.</span></span> <span data-ttu-id="f19a9-122">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="f19a9-122">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f19a9-123">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-123">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-124">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-124">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-125">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-125">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-126">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-126">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-127">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-127">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-128">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-128">Event</span></span>|<span data-ttu-id="f19a9-129">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-129">Event ID</span></span>|<span data-ttu-id="f19a9-130">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-130">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCStart_V1`|<span data-ttu-id="f19a9-131">1</span><span class="sxs-lookup"><span data-stu-id="f19a9-131">1</span></span>|<span data-ttu-id="f19a9-132">Un garbage collection a démarré.</span><span class="sxs-lookup"><span data-stu-id="f19a9-132">A garbage collection has started.</span></span>|  
  
 <span data-ttu-id="f19a9-133">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-133">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-134">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-134">Field name</span></span>|<span data-ttu-id="f19a9-135">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-135">Data type</span></span>|<span data-ttu-id="f19a9-136">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-136">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-137">Nombre</span><span class="sxs-lookup"><span data-stu-id="f19a9-137">Count</span></span>|<span data-ttu-id="f19a9-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-138">win:UInt32</span></span>|<span data-ttu-id="f19a9-139">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-139">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="f19a9-140">Profondeur</span><span class="sxs-lookup"><span data-stu-id="f19a9-140">Depth</span></span>|<span data-ttu-id="f19a9-141">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-141">win:UInt32</span></span>|<span data-ttu-id="f19a9-142">La génération est collectée.</span><span class="sxs-lookup"><span data-stu-id="f19a9-142">The generation that is being collected.</span></span>|  
|<span data-ttu-id="f19a9-143">Reason</span><span class="sxs-lookup"><span data-stu-id="f19a9-143">Reason</span></span>|<span data-ttu-id="f19a9-144">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-144">win:UInt32</span></span>|<span data-ttu-id="f19a9-145">Pourquoi le garbage collection a été déclenché :</span><span class="sxs-lookup"><span data-stu-id="f19a9-145">Why the garbage collection was triggered:</span></span><br /><br /> <span data-ttu-id="f19a9-146">0x0 – Allocation de tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="f19a9-146">0x0 - Small object heap allocation.</span></span><br /><br /> <span data-ttu-id="f19a9-147">0x1 – Induit.</span><span class="sxs-lookup"><span data-stu-id="f19a9-147">0x1 - Induced.</span></span><br /><br /> <span data-ttu-id="f19a9-148">0x2 – Mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="f19a9-148">0x2 - Low memory.</span></span><br /><br /> <span data-ttu-id="f19a9-149">0x3 – Vide.</span><span class="sxs-lookup"><span data-stu-id="f19a9-149">0x3 - Empty.</span></span><br /><br /> <span data-ttu-id="f19a9-150">0x4 – Allocation de tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-150">0x4 - Large object heap allocation.</span></span><br /><br /> <span data-ttu-id="f19a9-151">0x5 – Espace insuffisant (pour un tas de petits objets)</span><span class="sxs-lookup"><span data-stu-id="f19a9-151">0x5 - Out of space (for small object heap).</span></span><br /><br /> <span data-ttu-id="f19a9-152">0x6 – Espace insuffisant (pour un tas d'objets volumineux)</span><span class="sxs-lookup"><span data-stu-id="f19a9-152">0x6 - Out of space (for large object heap).</span></span><br /><br /> <span data-ttu-id="f19a9-153">0x7 – Induit mais non forcé comme blocage</span><span class="sxs-lookup"><span data-stu-id="f19a9-153">0x7 - Induced but not forced as blocking.</span></span>|  
|<span data-ttu-id="f19a9-154">Type</span><span class="sxs-lookup"><span data-stu-id="f19a9-154">Type</span></span>|<span data-ttu-id="f19a9-155">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-155">win:UInt32</span></span>|<span data-ttu-id="f19a9-156">0x0 – Un blocage de garbage collection s'est produit en dehors du garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f19a9-156">0x0 - Blocking garbage collection occurred outside background garbage collection.</span></span><br /><br /> <span data-ttu-id="f19a9-157">0x1 – Garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f19a9-157">0x1 - Background garbage collection.</span></span><br /><br /> <span data-ttu-id="f19a9-158">0x2 – Un blocage de garbage collection s'est produit pendant le garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="f19a9-158">0x2 - Blocking garbage collection occurred during background garbage collection.</span></span>|  
|<span data-ttu-id="f19a9-159">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-159">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-160">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-160">win:UInt16</span></span>|<span data-ttu-id="f19a9-161">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-161">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-162">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-162">Back to top</span></span>](#top)  
  
<a name="gcend_v1_event"></a>   
## <a name="gcend_v1-event"></a><span data-ttu-id="f19a9-163">Événement GCEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-163">GCEnd_V1 Event</span></span>  
 <span data-ttu-id="f19a9-164">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-164">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-165">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-165">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-166">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-166">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-167">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-167">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-168">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-168">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-169">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-169">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-170">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-170">Event</span></span>|<span data-ttu-id="f19a9-171">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-171">Event ID</span></span>|<span data-ttu-id="f19a9-172">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-172">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCEnd_V1`|<span data-ttu-id="f19a9-173">2</span><span class="sxs-lookup"><span data-stu-id="f19a9-173">2</span></span>|<span data-ttu-id="f19a9-174">Un garbage collection s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="f19a9-174">The garbage collection has ended.</span></span>|  
  
 <span data-ttu-id="f19a9-175">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-175">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-176">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-176">Field name</span></span>|<span data-ttu-id="f19a9-177">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-177">Data type</span></span>|<span data-ttu-id="f19a9-178">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-178">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-179">Nombre</span><span class="sxs-lookup"><span data-stu-id="f19a9-179">Count</span></span>|<span data-ttu-id="f19a9-180">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-180">win:UInt32</span></span>|<span data-ttu-id="f19a9-181">Le *n*ième garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-181">The *n*th garbage collection.</span></span>|  
|<span data-ttu-id="f19a9-182">Profondeur</span><span class="sxs-lookup"><span data-stu-id="f19a9-182">Depth</span></span>|<span data-ttu-id="f19a9-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-183">win:UInt32</span></span>|<span data-ttu-id="f19a9-184">Génération ayant été collectée.</span><span class="sxs-lookup"><span data-stu-id="f19a9-184">The generation that was collected.</span></span>|  
|<span data-ttu-id="f19a9-185">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-185">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-186">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-186">win:UInt16</span></span>|<span data-ttu-id="f19a9-187">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-187">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-188">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-188">Back to top</span></span>](#top)  
  
<a name="gcheapstats_v1_event"></a>   
## <a name="gcheapstats_v1-event"></a><span data-ttu-id="f19a9-189">Événement GCHeapStats_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-189">GCHeapStats_V1 Event</span></span>  
 <span data-ttu-id="f19a9-190">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-190">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-191">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-191">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-192">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-192">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-193">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-193">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-194">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-194">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-195">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-195">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-196">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-196">Event</span></span>|<span data-ttu-id="f19a9-197">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-197">Event ID</span></span>|<span data-ttu-id="f19a9-198">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-198">Description</span></span>|  
|-----------|--------------|-----------------|  
|`GCHeapStats_V1`|<span data-ttu-id="f19a9-199">4</span><span class="sxs-lookup"><span data-stu-id="f19a9-199">4</span></span>|<span data-ttu-id="f19a9-200">Affiche les statistiques relatives aux tas à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-200">Shows the heap statistics at the end of each garbage collection.</span></span>|  
  
 <span data-ttu-id="f19a9-201">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-201">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-202">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-202">Field name</span></span>|<span data-ttu-id="f19a9-203">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-203">Data type</span></span>|<span data-ttu-id="f19a9-204">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-204">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-205">GenerationSize0</span><span class="sxs-lookup"><span data-stu-id="f19a9-205">GenerationSize0</span></span>|<span data-ttu-id="f19a9-206">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-206">win:UInt64</span></span>|<span data-ttu-id="f19a9-207">Taille, en octets, de la mémoire de génération 0.</span><span class="sxs-lookup"><span data-stu-id="f19a9-207">The size, in bytes, of generation 0 memory.</span></span>|  
|<span data-ttu-id="f19a9-208">TotalPromotedSize0</span><span class="sxs-lookup"><span data-stu-id="f19a9-208">TotalPromotedSize0</span></span>|<span data-ttu-id="f19a9-209">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-209">win:UInt64</span></span>|<span data-ttu-id="f19a9-210">Nombre d'octets promus de la génération 0 à la génération 1.</span><span class="sxs-lookup"><span data-stu-id="f19a9-210">The number of bytes that are promoted from generation 0 to generation 1.</span></span>|  
|<span data-ttu-id="f19a9-211">GenerationSize1</span><span class="sxs-lookup"><span data-stu-id="f19a9-211">GenerationSize1</span></span>|<span data-ttu-id="f19a9-212">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-212">win:UInt64</span></span>|<span data-ttu-id="f19a9-213">Taille, en octets, de la mémoire de génération 1.</span><span class="sxs-lookup"><span data-stu-id="f19a9-213">The size, in bytes, of generation 1 memory.</span></span>|  
|<span data-ttu-id="f19a9-214">TotalPromotedSize1</span><span class="sxs-lookup"><span data-stu-id="f19a9-214">TotalPromotedSize1</span></span>|<span data-ttu-id="f19a9-215">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-215">win:UInt64</span></span>|<span data-ttu-id="f19a9-216">Nombre d'octets promus de la génération 1 à la génération 2.</span><span class="sxs-lookup"><span data-stu-id="f19a9-216">The number of bytes that are promoted from generation 1 to generation 2.</span></span>|  
|<span data-ttu-id="f19a9-217">GenerationSize2</span><span class="sxs-lookup"><span data-stu-id="f19a9-217">GenerationSize2</span></span>|<span data-ttu-id="f19a9-218">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-218">win:UInt64</span></span>|<span data-ttu-id="f19a9-219">Taille, en octets, de la mémoire de génération 2.</span><span class="sxs-lookup"><span data-stu-id="f19a9-219">The size, in bytes, of generation 2 memory.</span></span>|  
|<span data-ttu-id="f19a9-220">TotalPromotedSize2</span><span class="sxs-lookup"><span data-stu-id="f19a9-220">TotalPromotedSize2</span></span>|<span data-ttu-id="f19a9-221">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-221">win:UInt64</span></span>|<span data-ttu-id="f19a9-222">Nombre d'octets ayant survécu dans la génération 2 après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-222">The number of bytes that survived in generation 2 after the last collection.</span></span>|  
|<span data-ttu-id="f19a9-223">GenerationSize3</span><span class="sxs-lookup"><span data-stu-id="f19a9-223">GenerationSize3</span></span>|<span data-ttu-id="f19a9-224">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-224">win:UInt64</span></span>|<span data-ttu-id="f19a9-225">Taille, en octets, du tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-225">The size, in bytes, of the large object heap.</span></span>|  
|<span data-ttu-id="f19a9-226">TotalPromotedSize3</span><span class="sxs-lookup"><span data-stu-id="f19a9-226">TotalPromotedSize3</span></span>|<span data-ttu-id="f19a9-227">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-227">win:UInt64</span></span>|<span data-ttu-id="f19a9-228">Nombre d'octets ayant survécu dans le tas d'objets volumineux après la dernière collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-228">The number of bytes that survived in the large object heap after the last collection.</span></span>|  
|<span data-ttu-id="f19a9-229">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="f19a9-229">FinalizationPromotedSize</span></span>|<span data-ttu-id="f19a9-230">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-230">win:UInt64</span></span>|<span data-ttu-id="f19a9-231">Taille totale, en octets, des objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="f19a9-231">The total size, in bytes, of the objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="f19a9-232">FinalizationPromotedSize</span><span class="sxs-lookup"><span data-stu-id="f19a9-232">FinalizationPromotedCount</span></span>|<span data-ttu-id="f19a9-233">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-233">win:UInt64</span></span>|<span data-ttu-id="f19a9-234">Nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="f19a9-234">The number of objects that are ready for finalization.</span></span>|  
|<span data-ttu-id="f19a9-235">PinnedObjectCount</span><span class="sxs-lookup"><span data-stu-id="f19a9-235">PinnedObjectCount</span></span>|<span data-ttu-id="f19a9-236">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-236">win:UInt32</span></span>|<span data-ttu-id="f19a9-237">Nombre d'objets (non déplaçables) épinglés.</span><span class="sxs-lookup"><span data-stu-id="f19a9-237">The number of pinned (unmovable) objects.</span></span>|  
|<span data-ttu-id="f19a9-238">SinkBlockCount</span><span class="sxs-lookup"><span data-stu-id="f19a9-238">SinkBlockCount</span></span>|<span data-ttu-id="f19a9-239">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-239">win:UInt32</span></span>|<span data-ttu-id="f19a9-240">Nombre de blocs de synchronisation en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="f19a9-240">The number of synchronization blocks in use.</span></span>|  
|<span data-ttu-id="f19a9-241">GCHandleCount</span><span class="sxs-lookup"><span data-stu-id="f19a9-241">GCHandleCount</span></span>|<span data-ttu-id="f19a9-242">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-242">win:UInt32</span></span>|<span data-ttu-id="f19a9-243">Nombre de handles de garbage collection en cours d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="f19a9-243">The number of garbage collection handles in use.</span></span>|  
|<span data-ttu-id="f19a9-244">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-244">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-245">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-245">win:UInt16</span></span>|<span data-ttu-id="f19a9-246">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-246">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-247">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-247">Back to top</span></span>](#top)  
  
<a name="gccreatesegment_v1_event"></a>   
## <a name="gccreatesegment_v1-event"></a><span data-ttu-id="f19a9-248">Événement GCCreateSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-248">GCCreateSegment_V1 Event</span></span>  
 <span data-ttu-id="f19a9-249">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-249">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-250">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-250">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-251">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-251">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-252">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-252">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-253">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-253">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-254">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-254">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-255">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-255">Event</span></span>|<span data-ttu-id="f19a9-256">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-256">Event ID</span></span>|<span data-ttu-id="f19a9-257">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-257">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateSegment_V1`|<span data-ttu-id="f19a9-258">5\.</span><span class="sxs-lookup"><span data-stu-id="f19a9-258">5</span></span>|<span data-ttu-id="f19a9-259">Un nouveau segment de garbage collection a été créé.</span><span class="sxs-lookup"><span data-stu-id="f19a9-259">A new garbage collection segment has been created.</span></span> <span data-ttu-id="f19a9-260">En outre, quand le suivi est activé sur un processus en cours d'exécution, cet événement est déclenché pour chaque segment existant.</span><span class="sxs-lookup"><span data-stu-id="f19a9-260">In addition, when tracing is enabled on a process that is already running, this event is raised for each existing segment.</span></span>|  
  
 <span data-ttu-id="f19a9-261">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-261">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-262">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-262">Field name</span></span>|<span data-ttu-id="f19a9-263">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-263">Data type</span></span>|<span data-ttu-id="f19a9-264">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-264">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-265">Adresse</span><span class="sxs-lookup"><span data-stu-id="f19a9-265">Address</span></span>|<span data-ttu-id="f19a9-266">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-266">win:UInt64</span></span>|<span data-ttu-id="f19a9-267">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="f19a9-267">The address of the segment.</span></span>|  
|<span data-ttu-id="f19a9-268">Taille</span><span class="sxs-lookup"><span data-stu-id="f19a9-268">Size</span></span>|<span data-ttu-id="f19a9-269">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-269">win:UInt64</span></span>|<span data-ttu-id="f19a9-270">Taille du segment.</span><span class="sxs-lookup"><span data-stu-id="f19a9-270">The size of the segment.</span></span>|  
|<span data-ttu-id="f19a9-271">Type</span><span class="sxs-lookup"><span data-stu-id="f19a9-271">Type</span></span>|<span data-ttu-id="f19a9-272">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-272">win:UInt32</span></span>|<span data-ttu-id="f19a9-273">0x0 – Tas de petits objets.</span><span class="sxs-lookup"><span data-stu-id="f19a9-273">0x0 - Small object heap.</span></span><br /><br /> <span data-ttu-id="f19a9-274">0x1 – Tas d'objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-274">0x1 - Large object heap.</span></span><br /><br /> <span data-ttu-id="f19a9-275">0x2 – Tas en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="f19a9-275">0x2 - Read-only heap.</span></span>|  
|<span data-ttu-id="f19a9-276">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-276">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-277">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-277">win:UInt16</span></span>|<span data-ttu-id="f19a9-278">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-278">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 <span data-ttu-id="f19a9-279">Notez que la taille des segments alloués par le garbage collector est spécifique à l'implémentation et susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="f19a9-279">Note that the size of segments allocated by the garbage collector is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="f19a9-280">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="f19a9-280">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>  
  
 [<span data-ttu-id="f19a9-281">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-281">Back to top</span></span>](#top)  
  
<a name="gcfreesegment_v1_event"></a>   
## <a name="gcfreesegment_v1-event"></a><span data-ttu-id="f19a9-282">Événement GCFreeSegment_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-282">GCFreeSegment_V1 Event</span></span>  
 <span data-ttu-id="f19a9-283">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-283">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-284">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-284">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-285">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-285">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-286">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-286">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-287">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-287">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-288">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-288">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-289">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-289">Event</span></span>|<span data-ttu-id="f19a9-290">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-290">Event ID</span></span>|<span data-ttu-id="f19a9-291">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-291">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFreeSegment_V1`|<span data-ttu-id="f19a9-292">6\.</span><span class="sxs-lookup"><span data-stu-id="f19a9-292">6</span></span>|<span data-ttu-id="f19a9-293">Un nouveau segment de garbage collection a été libéré.</span><span class="sxs-lookup"><span data-stu-id="f19a9-293">A garbage collection segment has been released.</span></span>|  
  
 <span data-ttu-id="f19a9-294">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-294">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-295">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-295">Field name</span></span>|<span data-ttu-id="f19a9-296">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-296">Data type</span></span>|<span data-ttu-id="f19a9-297">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-297">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-298">Adresse</span><span class="sxs-lookup"><span data-stu-id="f19a9-298">Address</span></span>|<span data-ttu-id="f19a9-299">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-299">win:UInt64</span></span>|<span data-ttu-id="f19a9-300">Adresse du segment.</span><span class="sxs-lookup"><span data-stu-id="f19a9-300">The address of the segment.</span></span>|  
|<span data-ttu-id="f19a9-301">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-301">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-302">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-302">win:UInt16</span></span>|<span data-ttu-id="f19a9-303">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-303">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-304">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-304">Back to top</span></span>](#top)  
  
<a name="gcrestarteebegin_v1_event"></a>   
## <a name="gcrestarteebegin_v1-event"></a><span data-ttu-id="f19a9-305">Événement GCRestartEEBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-305">GCRestartEEBegin_V1 Event</span></span>  
 <span data-ttu-id="f19a9-306">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-306">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-307">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-307">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-308">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-308">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-309">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-309">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-310">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-310">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-311">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-311">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-312">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-312">Event</span></span>|<span data-ttu-id="f19a9-313">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-313">Event ID</span></span>|<span data-ttu-id="f19a9-314">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-314">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEBegin_V1`|<span data-ttu-id="f19a9-315">7</span><span class="sxs-lookup"><span data-stu-id="f19a9-315">7</span></span>|<span data-ttu-id="f19a9-316">La reprise du common language runtime après sa suspension a commencé.</span><span class="sxs-lookup"><span data-stu-id="f19a9-316">Resumption from common language runtime suspension has begun.</span></span>|  
  
 <span data-ttu-id="f19a9-317">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-317">No event data.</span></span>  
  
 [<span data-ttu-id="f19a9-318">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-318">Back to top</span></span>](#top)  
  
<a name="gcrestarteeend_v1_event"></a>   
## <a name="gcrestarteeend_v1-event"></a><span data-ttu-id="f19a9-319">Événement GCRestartEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-319">GCRestartEEEnd_V1 Event</span></span>  
 <span data-ttu-id="f19a9-320">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-320">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-321">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-321">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-322">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-322">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-323">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-323">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-324">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-324">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-325">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-325">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-326">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-326">Event</span></span>|<span data-ttu-id="f19a9-327">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-327">Event Id</span></span>|<span data-ttu-id="f19a9-328">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-328">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCRestartEEEnd_V1`|<span data-ttu-id="f19a9-329">3</span><span class="sxs-lookup"><span data-stu-id="f19a9-329">3</span></span>|<span data-ttu-id="f19a9-330">La reprise du common language runtime après sa suspension s'est terminée.</span><span class="sxs-lookup"><span data-stu-id="f19a9-330">Resumption from common language runtime suspension has ended.</span></span>|  
  
 <span data-ttu-id="f19a9-331">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-331">No event data.</span></span>  
  
 [<span data-ttu-id="f19a9-332">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-332">Back to top</span></span>](#top)  
  
<a name="gcsuspendee_v1_event"></a>   
## <a name="gcsuspendee_v1-event"></a><span data-ttu-id="f19a9-333">Événement GCSuspendEE_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-333">GCSuspendEE_V1 Event</span></span>  
 <span data-ttu-id="f19a9-334">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-334">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-335">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-335">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-336">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-336">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-337">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-337">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-338">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-338">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-339">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-339">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-340">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-340">Event</span></span>|<span data-ttu-id="f19a9-341">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-341">Event ID</span></span>|<span data-ttu-id="f19a9-342">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-342">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEE_V1`|<span data-ttu-id="f19a9-343">9</span><span class="sxs-lookup"><span data-stu-id="f19a9-343">9</span></span>|<span data-ttu-id="f19a9-344">Début de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-344">Start of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="f19a9-345">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-345">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-346">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-346">Field name</span></span>|<span data-ttu-id="f19a9-347">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-347">Data type</span></span>|<span data-ttu-id="f19a9-348">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-348">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-349">Raison</span><span class="sxs-lookup"><span data-stu-id="f19a9-349">Reason</span></span>|<span data-ttu-id="f19a9-350">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-350">win:UInt16</span></span>|<span data-ttu-id="f19a9-351">0x0 – Autre.</span><span class="sxs-lookup"><span data-stu-id="f19a9-351">0x0 - Other.</span></span><br /><br /> <span data-ttu-id="f19a9-352">0x1 – Garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-352">0x1 - Garbage collection.</span></span><br /><br /> <span data-ttu-id="f19a9-353">0x2 – Fermeture du domaine d'application.</span><span class="sxs-lookup"><span data-stu-id="f19a9-353">0x2 - Application domain shutdown.</span></span><br /><br /> <span data-ttu-id="f19a9-354">0x3 – Pitching de code.</span><span class="sxs-lookup"><span data-stu-id="f19a9-354">0x3 - Code pitching.</span></span><br /><br /> <span data-ttu-id="f19a9-355">0x4 – Arrêt.</span><span class="sxs-lookup"><span data-stu-id="f19a9-355">0x4 - Shutdown.</span></span><br /><br /> <span data-ttu-id="f19a9-356">0x5 – Débogueur.</span><span class="sxs-lookup"><span data-stu-id="f19a9-356">0x5 - Debugger.</span></span><br /><br /> <span data-ttu-id="f19a9-357">0x6 – Préparation pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-357">0x6 - Preparation for garbage collection.</span></span>|  
|<span data-ttu-id="f19a9-358">Nombre</span><span class="sxs-lookup"><span data-stu-id="f19a9-358">Count</span></span>|<span data-ttu-id="f19a9-359">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-359">win:UInt32</span></span>|<span data-ttu-id="f19a9-360">Nombre GC à ce moment-là.</span><span class="sxs-lookup"><span data-stu-id="f19a9-360">The GC count at the time.</span></span> <span data-ttu-id="f19a9-361">En règle générale, vous verrez un événement de démarrage de GC par la suite et son nombre doit être égal à ce nombre + 1 à mesure que nous augmentons l’index GC pendant un garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-361">Usually, you would see a subsequent GC Start event after this, and its Count would be this Count + 1 as we increase the GC index during a garbage collection.</span></span>|  
|<span data-ttu-id="f19a9-362">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-362">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-363">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-363">win:UInt16</span></span>|<span data-ttu-id="f19a9-364">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-364">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-365">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-365">Back to top</span></span>](#top)  
  
<a name="gcsuspendeeend_v1_event"></a>   
## <a name="gcsuspendeeend_v1-event"></a><span data-ttu-id="f19a9-366">Événement GCSuspendEEEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-366">GCSuspendEEEnd_V1 Event</span></span>  
 <span data-ttu-id="f19a9-367">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-367">The following table shows the keyword and level:</span></span>  
  
|<span data-ttu-id="f19a9-368">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-368">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-369">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-369">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-370">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-370">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-371">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-371">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-372">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-372">The following table shows the event information:</span></span>  
  
|<span data-ttu-id="f19a9-373">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-373">Event</span></span>|<span data-ttu-id="f19a9-374">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-374">Event ID</span></span>|<span data-ttu-id="f19a9-375">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-375">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCSuspendEEEnd_V1`|<span data-ttu-id="f19a9-376">8</span><span class="sxs-lookup"><span data-stu-id="f19a9-376">8</span></span>|<span data-ttu-id="f19a9-377">Fin de la suspension du moteur d'exécution pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f19a9-377">End of suspension of the execution engine for garbage collection.</span></span>|  
  
 <span data-ttu-id="f19a9-378">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-378">No event data.</span></span>  
  
 [<span data-ttu-id="f19a9-379">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-379">Back to top</span></span>](#top)  
  
<a name="gcallocationtick_v2_event"></a>   
## <a name="gcallocationtick_v2-event"></a><span data-ttu-id="f19a9-380">Événement GCAllocationTick_V2</span><span class="sxs-lookup"><span data-stu-id="f19a9-380">GCAllocationTick_V2 Event</span></span>  
 <span data-ttu-id="f19a9-381">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-381">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-382">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-382">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-383">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-383">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-384">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-384">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-385">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-385">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-386">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-386">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-387">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-387">Event</span></span>|<span data-ttu-id="f19a9-388">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-388">Event ID</span></span>|<span data-ttu-id="f19a9-389">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-389">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCAllocationTick_V2`|<span data-ttu-id="f19a9-390">10</span><span class="sxs-lookup"><span data-stu-id="f19a9-390">10</span></span>|<span data-ttu-id="f19a9-391">Chaque fois qu'environ 100 Ko sont alloués.</span><span class="sxs-lookup"><span data-stu-id="f19a9-391">Each time approximately 100 KB is allocated.</span></span>|  
  
 <span data-ttu-id="f19a9-392">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-392">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-393">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-393">Field name</span></span>|<span data-ttu-id="f19a9-394">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-394">Data type</span></span>|<span data-ttu-id="f19a9-395">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-395">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-396">AllocationAmount</span><span class="sxs-lookup"><span data-stu-id="f19a9-396">AllocationAmount</span></span>|<span data-ttu-id="f19a9-397">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-397">win:UInt32</span></span>|<span data-ttu-id="f19a9-398">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="f19a9-398">The allocation size, in bytes.</span></span> <span data-ttu-id="f19a9-399">Cette valeur est correcte pour les allocations inférieures à la longueur d'un ULONG (4 294 967 295 octets).</span><span class="sxs-lookup"><span data-stu-id="f19a9-399">This value is accurate for allocations that are less than the length of a ULONG (4,294,967,295 bytes).</span></span> <span data-ttu-id="f19a9-400">Si l'allocation est supérieure, ce champ contient une valeur tronquée.</span><span class="sxs-lookup"><span data-stu-id="f19a9-400">If the allocation is greater, this field contains a truncated value.</span></span> <span data-ttu-id="f19a9-401">Utilisez `AllocationAmount64` pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="f19a9-401">Use `AllocationAmount64` for very large allocations.</span></span>|  
|<span data-ttu-id="f19a9-402">AllocationKind</span><span class="sxs-lookup"><span data-stu-id="f19a9-402">AllocationKind</span></span>|<span data-ttu-id="f19a9-403">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-403">win:UInt32</span></span>|<span data-ttu-id="f19a9-404">0x0 – Allocation de petits objets (l'allocation se fait dans le tas de petits objets).</span><span class="sxs-lookup"><span data-stu-id="f19a9-404">0x0 - Small object allocation (allocation is in small object heap).</span></span><br /><br /> <span data-ttu-id="f19a9-405">0x1 – Allocation d'objets volumineux (l'allocation se fait dans le tas des objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="f19a9-405">0x1 - Large object allocation (allocation is in large object heap).</span></span>|  
|<span data-ttu-id="f19a9-406">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-406">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-407">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-407">win:UInt16</span></span>|<span data-ttu-id="f19a9-408">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-408">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
|<span data-ttu-id="f19a9-409">AllocationAmount64</span><span class="sxs-lookup"><span data-stu-id="f19a9-409">AllocationAmount64</span></span>|<span data-ttu-id="f19a9-410">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f19a9-410">win:UInt64</span></span>|<span data-ttu-id="f19a9-411">Taille de l'allocation, en octets.</span><span class="sxs-lookup"><span data-stu-id="f19a9-411">The allocation size, in bytes.</span></span> <span data-ttu-id="f19a9-412">Cette valeur est correcte pour les allocations très volumineuses.</span><span class="sxs-lookup"><span data-stu-id="f19a9-412">This value is accurate for very large allocations.</span></span>|  
|<span data-ttu-id="f19a9-413">TypeId</span><span class="sxs-lookup"><span data-stu-id="f19a9-413">TypeId</span></span>|<span data-ttu-id="f19a9-414">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="f19a9-414">win:Pointer</span></span>|<span data-ttu-id="f19a9-415">Adresse de MethodTable.</span><span class="sxs-lookup"><span data-stu-id="f19a9-415">The address of the MethodTable.</span></span> <span data-ttu-id="f19a9-416">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit de l'adresse de MethodTable qui correspond au dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="f19a9-416">When there are several types of objects that were allocated during this event, this is the address of the MethodTable that corresponds to the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="f19a9-417">TypeName</span><span class="sxs-lookup"><span data-stu-id="f19a9-417">TypeName</span></span>|<span data-ttu-id="f19a9-418">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f19a9-418">win:UnicodeString</span></span>|<span data-ttu-id="f19a9-419">Nom du type ayant été alloué.</span><span class="sxs-lookup"><span data-stu-id="f19a9-419">The name of the type that was allocated.</span></span> <span data-ttu-id="f19a9-420">Quand plusieurs types d'objets ont été alloués au cours de cet événement, il s'agit du type du dernier objet alloué (l'objet qui a provoqué le dépassement du seuil de 100 Ko).</span><span class="sxs-lookup"><span data-stu-id="f19a9-420">When there are several types of objects that were allocated during this event, this is the type of the last object allocated (the object that caused the 100 KB threshold to be exceeded).</span></span>|  
|<span data-ttu-id="f19a9-421">HeapIndex</span><span class="sxs-lookup"><span data-stu-id="f19a9-421">HeapIndex</span></span>|<span data-ttu-id="f19a9-422">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-422">win:UInt32</span></span>|<span data-ttu-id="f19a9-423">Segment de mémoire où l'objet a été alloué.</span><span class="sxs-lookup"><span data-stu-id="f19a9-423">The heap where the object was allocated.</span></span> <span data-ttu-id="f19a9-424">Cette valeur est de 0 (zéro) lors d'une exécution avec le garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="f19a9-424">This value is 0 (zero) when running with workstation garbage collection.</span></span>|  
  
 [<span data-ttu-id="f19a9-425">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-425">Back to top</span></span>](#top)  
  
<a name="gcfinalizersbegin_v1_event"></a>   
## <a name="gcfinalizersbegin_v1-event"></a><span data-ttu-id="f19a9-426">Événement GCFinalizersBegin_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-426">GCFinalizersBegin_V1 Event</span></span>  
 <span data-ttu-id="f19a9-427">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-427">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-428">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-428">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-429">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-429">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-430">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-430">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-431">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-431">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-432">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-432">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-433">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-433">Event</span></span>|<span data-ttu-id="f19a9-434">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-434">Event ID</span></span>|<span data-ttu-id="f19a9-435">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-435">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersBegin_V1`|<span data-ttu-id="f19a9-436">14</span><span class="sxs-lookup"><span data-stu-id="f19a9-436">14</span></span>|<span data-ttu-id="f19a9-437">Début de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="f19a9-437">The start of running finalizers.</span></span>|  
  
 <span data-ttu-id="f19a9-438">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-438">No event data.</span></span>  
  
 [<span data-ttu-id="f19a9-439">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-439">Back to top</span></span>](#top)  
  
<a name="gcfinalizersend_v1_event"></a>   
## <a name="gcfinalizersend_v1-event"></a><span data-ttu-id="f19a9-440">Événement GCFinalizersEnd_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-440">GCFinalizersEnd_V1 Event</span></span>  
 <span data-ttu-id="f19a9-441">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-441">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-442">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-442">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-443">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-443">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-444">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-444">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-445">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-445">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-446">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-446">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-447">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-447">Event</span></span>|<span data-ttu-id="f19a9-448">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-448">Event ID</span></span>|<span data-ttu-id="f19a9-449">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-449">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCFinalizersEnd_V1`|<span data-ttu-id="f19a9-450">13</span><span class="sxs-lookup"><span data-stu-id="f19a9-450">13</span></span>|<span data-ttu-id="f19a9-451">Fin de l'exécution des finaliseurs.</span><span class="sxs-lookup"><span data-stu-id="f19a9-451">The end of running finalizers.</span></span>|  
  
 <span data-ttu-id="f19a9-452">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-452">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f19a9-453">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="f19a9-453">Field name</span></span>|<span data-ttu-id="f19a9-454">Type de données</span><span class="sxs-lookup"><span data-stu-id="f19a9-454">Data type</span></span>|<span data-ttu-id="f19a9-455">Description</span><span class="sxs-lookup"><span data-stu-id="f19a9-455">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f19a9-456">Nombre</span><span class="sxs-lookup"><span data-stu-id="f19a9-456">Count</span></span>|<span data-ttu-id="f19a9-457">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f19a9-457">win:UInt32</span></span>|<span data-ttu-id="f19a9-458">Nombre de finaliseurs exécutés.</span><span class="sxs-lookup"><span data-stu-id="f19a9-458">The number of finalizers that were run.</span></span>|  
|<span data-ttu-id="f19a9-459">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f19a9-459">ClrInstanceID</span></span>|<span data-ttu-id="f19a9-460">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f19a9-460">win:UInt16</span></span>|<span data-ttu-id="f19a9-461">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f19a9-461">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f19a9-462">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-462">Back to top</span></span>](#top)  
  
<a name="gccreateconcurrentthread_v1_event"></a>   
## <a name="gccreateconcurrentthread_v1-event"></a><span data-ttu-id="f19a9-463">Événement GCCreateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-463">GCCreateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="f19a9-464">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-464">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-465">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-465">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-466">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-466">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-467">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-467">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-468">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-468">Informational (4)</span></span>|  
|<span data-ttu-id="f19a9-469">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f19a9-469">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f19a9-470">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-470">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-471">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-471">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-472">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-472">Event</span></span>|<span data-ttu-id="f19a9-473">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-473">Event ID</span></span>|<span data-ttu-id="f19a9-474">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-474">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCCreateConcurrentThread_V1`|<span data-ttu-id="f19a9-475">11</span><span class="sxs-lookup"><span data-stu-id="f19a9-475">11</span></span>|<span data-ttu-id="f19a9-476">Un thread de garbage collection simultané a été créé.</span><span class="sxs-lookup"><span data-stu-id="f19a9-476">Concurrent garbage collection thread was created.</span></span>|  
  
 <span data-ttu-id="f19a9-477">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-477">No event data.</span></span>  
  
 [<span data-ttu-id="f19a9-478">Revenir en haut</span><span class="sxs-lookup"><span data-stu-id="f19a9-478">Back to top</span></span>](#top)  
  
<a name="gcterminateconcurrentthread_v1_event"></a>   
## <a name="gcterminateconcurrentthread_v1-event"></a><span data-ttu-id="f19a9-479">Événement GCTerminateConcurrentThread_V1</span><span class="sxs-lookup"><span data-stu-id="f19a9-479">GCTerminateConcurrentThread_V1 Event</span></span>  
 <span data-ttu-id="f19a9-480">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="f19a9-480">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f19a9-481">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-481">Keyword for raising the event</span></span>|<span data-ttu-id="f19a9-482">Niveau</span><span class="sxs-lookup"><span data-stu-id="f19a9-482">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f19a9-483">`GCKeyword` (0x1)</span><span class="sxs-lookup"><span data-stu-id="f19a9-483">`GCKeyword` (0x1)</span></span>|<span data-ttu-id="f19a9-484">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-484">Informational (4)</span></span>|  
|<span data-ttu-id="f19a9-485">`ThreadingKeyword` (0x10000)</span><span class="sxs-lookup"><span data-stu-id="f19a9-485">`ThreadingKeyword` (0x10000)</span></span>|<span data-ttu-id="f19a9-486">Informatif (4)</span><span class="sxs-lookup"><span data-stu-id="f19a9-486">Informational (4)</span></span>|  
  
 <span data-ttu-id="f19a9-487">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="f19a9-487">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f19a9-488">Événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-488">Event</span></span>|<span data-ttu-id="f19a9-489">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="f19a9-489">Event ID</span></span>|<span data-ttu-id="f19a9-490">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="f19a9-490">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`GCTerminateConcurrentThread_V1`|<span data-ttu-id="f19a9-491">12</span><span class="sxs-lookup"><span data-stu-id="f19a9-491">12</span></span>|<span data-ttu-id="f19a9-492">Un thread de garbage collection simultané s'est terminé.</span><span class="sxs-lookup"><span data-stu-id="f19a9-492">Concurrent garbage collection thread was terminated.</span></span>|  
  
 <span data-ttu-id="f19a9-493">Aucune donnée d'événement.</span><span class="sxs-lookup"><span data-stu-id="f19a9-493">No event data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f19a9-494">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f19a9-494">See also</span></span>

- [<span data-ttu-id="f19a9-495">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="f19a9-495">CLR ETW Events</span></span>](clr-etw-events.md)

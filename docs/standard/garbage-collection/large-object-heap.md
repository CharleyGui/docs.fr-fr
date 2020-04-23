---
title: Grand tas d’objets (LOH) sur Windows
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: ab9beca58b3d6118bc0f5121b6f5dec71a9f9f36
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102266"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="0e35d-102">Tas de grands objets sur les systèmes Windows</span><span class="sxs-lookup"><span data-stu-id="0e35d-102">The large object heap on Windows systems</span></span>

<span data-ttu-id="0e35d-103">Le collecteur d’ordures .NET (GC) divise les objets en petits et grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-103">The .NET garbage collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="0e35d-104">Quand un objet est grand, certains de ses attributs prennent plus d’importance que s’il est petit.</span><span class="sxs-lookup"><span data-stu-id="0e35d-104">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="0e35d-105">Par exemple, le&mdash;compactage qui est, le copier&mdash;en mémoire ailleurs sur le tas peut être coûteux.</span><span class="sxs-lookup"><span data-stu-id="0e35d-105">For instance, compacting it&mdash;that is, copying it in memory elsewhere on the heap&mdash;can be expensive.</span></span> <span data-ttu-id="0e35d-106">Pour cette raison, le collecteur d’ordures place de grands objets sur le tas de gros objets (LOH).</span><span class="sxs-lookup"><span data-stu-id="0e35d-106">Because of this, the garbage collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="0e35d-107">Cet article traite de ce qui qualifie un objet comme un grand objet, comment de grands objets sont collectés, et quel genre d’implications de performance de grands objets imposent.</span><span class="sxs-lookup"><span data-stu-id="0e35d-107">This article discusses what qualifies an object as a large object, how large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0e35d-108">Cet article traite du tas de gros objets dans .NET Framework et .NET Core fonctionnant uniquement sur les systèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="0e35d-108">This article discusses the large object heap in .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="0e35d-109">Elle ne couvre pas le LOH exécuté sur des implémentations de .NET sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="0e35d-109">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-loh"></a><span data-ttu-id="0e35d-110">Comment un objet se retrouve sur le LOH</span><span class="sxs-lookup"><span data-stu-id="0e35d-110">How an object ends up on the LOH</span></span>

<span data-ttu-id="0e35d-111">Si un objet est supérieur ou égal à 85 000 octets de taille, il est considéré comme un objet de grande taille.</span><span class="sxs-lookup"><span data-stu-id="0e35d-111">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="0e35d-112">Ce chiffre a été déterminé par le réglage des performances.</span><span class="sxs-lookup"><span data-stu-id="0e35d-112">This number was determined by performance tuning.</span></span> <span data-ttu-id="0e35d-113">Quand une demande d’allocation d’objet est de 85 000 octets ou plus, le runtime l’alloue sur le tas de grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-113">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="0e35d-114">Pour comprendre ce que cela signifie, il est utile d’examiner certains principes fondamentaux sur le collecteur d’ordures.</span><span class="sxs-lookup"><span data-stu-id="0e35d-114">To understand what this means, it's useful to examine some fundamentals about the garbage collector.</span></span>

<span data-ttu-id="0e35d-115">Le collecteur d’ordures est un collectionneur générationnel.</span><span class="sxs-lookup"><span data-stu-id="0e35d-115">The garbage collector is a generational collector.</span></span> <span data-ttu-id="0e35d-116">Il a trois générations : génération 0, génération 1 et génération 2.</span><span class="sxs-lookup"><span data-stu-id="0e35d-116">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="0e35d-117">La raison de ces 3 générations est que la plupart des objets meurent dans la génération 0 (dans une application optimisée).</span><span class="sxs-lookup"><span data-stu-id="0e35d-117">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="0e35d-118">Par exemple, dans une application serveur, les allocations associées à chaque demande doivent mourir une fois la demande terminée.</span><span class="sxs-lookup"><span data-stu-id="0e35d-118">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="0e35d-119">Les demandes d’allocation en cours passent en génération 1 et y meurent.</span><span class="sxs-lookup"><span data-stu-id="0e35d-119">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="0e35d-120">La génération 1 joue, pour ainsi dire, le rôle de tampon entre les zones d’objets jeunes et les zones d’objets qui vivent déjà depuis un certain temps.</span><span class="sxs-lookup"><span data-stu-id="0e35d-120">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="0e35d-121">Les petits objets sont toujours alloués dans la génération 0 et, selon leur durée de vie, peuvent être promus dans les générations 1 ou 2.</span><span class="sxs-lookup"><span data-stu-id="0e35d-121">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="0e35d-122">Les grands objets sont toujours alloués dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="0e35d-122">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="0e35d-123">Les grands objets appartiennent à la génération 2 parce qu’ils sont nettoyés uniquement lors d’un nettoyage de la génération 2.</span><span class="sxs-lookup"><span data-stu-id="0e35d-123">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="0e35d-124">Quand une génération est nettoyée, ses générations plus jeunes sont également nettoyées.</span><span class="sxs-lookup"><span data-stu-id="0e35d-124">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="0e35d-125">Par exemple, pendant le nettoyage de la mémoire (GC, Garbage Collection) de la génération 1, les générations 1 et 0 sont toutes deux nettoyées.</span><span class="sxs-lookup"><span data-stu-id="0e35d-125">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="0e35d-126">De la même façon, pendant le GC de la génération 2, le tas tout entier est nettoyé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-126">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="0e35d-127">Pour cette raison, un GC de la génération 2 est également appelé *GC complet*.</span><span class="sxs-lookup"><span data-stu-id="0e35d-127">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="0e35d-128">Cet article fait référence au GC de la génération 2 et non au GC complet, mais les termes sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="0e35d-128">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="0e35d-129">Les générations fournissent une vue logique du tas du récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e35d-129">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="0e35d-130">Physiquement, les objets vivent dans des segments de tas managés.</span><span class="sxs-lookup"><span data-stu-id="0e35d-130">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="0e35d-131">Un *segment de tas managé* est un bloc de mémoire que le récupérateur de mémoire réserve sur le système d’exploitation en appelant la [fonction VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) pour le compte du code managé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-131">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="0e35d-132">Lorsque le CLR est chargé, le GC alloue deux segments de tas initiaux : l’un pour les petits objets (le tas de petit objet, ou SOH), et l’autre pour les gros objets (le tas de gros objets).</span><span class="sxs-lookup"><span data-stu-id="0e35d-132">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="0e35d-133">Les demandes d’allocation sont alors traitées en plaçant des objets managés sur ces segments de tas managés.</span><span class="sxs-lookup"><span data-stu-id="0e35d-133">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="0e35d-134">Si l’objet est inférieur à 85 000 octets, il est placé sur un segment SOH, sinon, sur un segment LOH.</span><span class="sxs-lookup"><span data-stu-id="0e35d-134">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="0e35d-135">Les segments sont réservés (en blocs plus petits) à mesure que leur nombre d’objets alloués augmente.</span><span class="sxs-lookup"><span data-stu-id="0e35d-135">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="0e35d-136">Pour le SOH, les objets qui survivent à un GC sont promus à la génération suivante.</span><span class="sxs-lookup"><span data-stu-id="0e35d-136">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="0e35d-137">Les objets qui survivent à un nettoyage de la génération 0 sont considérés comme des objets de génération 1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="0e35d-137">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="0e35d-138">Toutefois, les objets qui survivent à la plus vieille génération sont toujours considérés comme des objets de cette génération.</span><span class="sxs-lookup"><span data-stu-id="0e35d-138">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="0e35d-139">En d’autres termes, les survivants de la génération 2 sont des objets de la génération 2 et les survivants du LOH sont des objets du LOH (qui sont nettoyés avec la génération 2).</span><span class="sxs-lookup"><span data-stu-id="0e35d-139">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="0e35d-140">Le code d’utilisateur peut seulement allouer dans la génération 0 (petits objets) ou le LOH (grands objets).</span><span class="sxs-lookup"><span data-stu-id="0e35d-140">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="0e35d-141">Seul le récupérateur de mémoire peut « allouer » des objets dans la génération 1 (en promouvant les survivants de la génération 0) et la génération 2 (en promouvant les survivants des générations 1 et 2).</span><span class="sxs-lookup"><span data-stu-id="0e35d-141">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="0e35d-142">Quand un nettoyage de la mémoire est déclenché, le récupérateur de mémoire repère les objets en vie et les compacte.</span><span class="sxs-lookup"><span data-stu-id="0e35d-142">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="0e35d-143">Parce que le compactage coûte cher, le récupérateur de mémoire *balaye* le LOH et dresse une liste des objets morts qui peuvent être réutilisés plus tard pour répondre aux demandes d’allocation des grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-143">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="0e35d-144">Les objets morts adjacents sont transformés en un seul objet libre.</span><span class="sxs-lookup"><span data-stu-id="0e35d-144">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="0e35d-145">Le .NET Framework (à partir de .NET Framework 4.5.1) et .NET Core intègrent la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> qui permet aux utilisateurs de spécifier que le LOH doit être compacté au prochain GC bloquant complet.</span><span class="sxs-lookup"><span data-stu-id="0e35d-145">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="0e35d-146">Par la suite, .NET peut décider de compacter le LOH automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0e35d-146">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="0e35d-147">Donc, si vous allouez des grands objets et voulez garantir qu'ils ne bougent pas, vous devez quand même les épingler.</span><span class="sxs-lookup"><span data-stu-id="0e35d-147">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="0e35d-148">La figure 1 illustre un scénario dans lequel le récupérateur de mémoire forme la génération 1 après le premier GC de la génération 0 où `Obj1` et `Obj3` sont morts, et forme la génération 2 après le premier GC de la génération 1 où `Obj2` et `Obj5` sont morts.</span><span class="sxs-lookup"><span data-stu-id="0e35d-148">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="0e35d-149">Notez que cette figure et les suivantes sont uniquement à titre d’illustration. Elles contiennent très peu d’objets pour mieux montrer ce qui se passe sur le tas.</span><span class="sxs-lookup"><span data-stu-id="0e35d-149">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="0e35d-150">En réalité, un GC implique généralement bien plus d’objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-150">In reality, many more objects are typically involved in a GC.</span></span>

![Figure 1 : GC de la génération 0 et GC de la génération 1](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="0e35d-152">Figure 1 : GC des générations 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="0e35d-152">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="0e35d-153">La figure 2 montre qu’après un GC de la génération 2 qui a vu que `Obj1` et `Obj2` étaient morts, le récupérateur de mémoire forme un espace libre contigu dans la mémoire qui était auparavant occupée par `Obj1` et `Obj2`, lequel est ensuite utilisé pour répondre à une demande d’allocation concernant `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="0e35d-153">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="0e35d-154">L’espace entre le dernier objet `Obj3` et la fin du segment peut aussi être utilisé pour répondre aux demandes d’allocation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-154">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Figure 2 : Après un GC de la génération 2](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="0e35d-156">Figure 2 : Après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="0e35d-156">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="0e35d-157">Si l’espace libre est insuffisant pour répondre aux demandes d’allocation des grands objets, le récupérateur de mémoire tente d’acquérir d’autres segments du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-157">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="0e35d-158">En cas d’échec, il déclenche un GC de la génération 2 pour tenter de libérer l’espace.</span><span class="sxs-lookup"><span data-stu-id="0e35d-158">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="0e35d-159">Pendant un GC de la génération 1 ou 2, le récupérateur de mémoire libère les segments qui n’ont pas d’objet en vie et les rend au système d’exploitation en appelant la [fonction VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="0e35d-159">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="0e35d-160">La réservation de l’espace entre le dernier objet en vie et la fin du segment est annulée (sauf sur le segment éphémère, où vivent les générations 0 et 1, sur lequel le récupérateur de mémoire maintient la réservation pour que votre application puisse l’utiliser immédiatement).</span><span class="sxs-lookup"><span data-stu-id="0e35d-160">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="0e35d-161">Par ailleurs, les espaces libres restent réservés bien qu’ils soient réinitialisés, ce qui signifie que le système d’exploitation n’a pas besoin d’écrire de données dans ces espaces une fois revenus sur le disque.</span><span class="sxs-lookup"><span data-stu-id="0e35d-161">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="0e35d-162">Comme que le LOH est collecté uniquement pendant le GC de la génération 2, le segment LOH peut seulement être libéré pendant ce GC.</span><span class="sxs-lookup"><span data-stu-id="0e35d-162">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="0e35d-163">La figure 3 illustre un scénario où le récupérateur de mémoire rend un segment (segment 2) au système d’exploitation et annule la réservation d’espace supplémentaire sur les segments restants.</span><span class="sxs-lookup"><span data-stu-id="0e35d-163">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="0e35d-164">S’il doit utiliser l’espace libéré à la fin du segment pour répondre aux demandes d’allocation de grands objets, il réserve de nouveau la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e35d-164">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="0e35d-165">(Pour obtenir une explication de la réservation/libération, consultez la documentation de [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="0e35d-165">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Figure 3 : LOH après un GC de la génération 2](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="0e35d-167">Figure 3 : LOH après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="0e35d-167">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="0e35d-168">Quand un grand objet est-il collecté ?</span><span class="sxs-lookup"><span data-stu-id="0e35d-168">When is a large object collected?</span></span>

<span data-ttu-id="0e35d-169">En général, un GC se produit sous l’une des trois conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e35d-169">In general, a GC occurs under one of the following three conditions:</span></span>

- <span data-ttu-id="0e35d-170">L’allocation dépasse le seuil des grands objets ou de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="0e35d-170">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="0e35d-171">Le seuil est une propriété des générations.</span><span class="sxs-lookup"><span data-stu-id="0e35d-171">The threshold is a property of a generation.</span></span> <span data-ttu-id="0e35d-172">Le seuil d’une génération est défini quand le récupérateur de mémoire lui alloue des objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-172">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="0e35d-173">Quand le seuil est dépassé, un GC est déclenché sur cette génération.</span><span class="sxs-lookup"><span data-stu-id="0e35d-173">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="0e35d-174">Quand vous allouez des petits ou des grands objets, vous consommez les seuils de la génération 0 et du LOH, respectivement.</span><span class="sxs-lookup"><span data-stu-id="0e35d-174">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="0e35d-175">Quand le récupérateur de mémoire alloue des objets dans les générations 1 et 2, il consomme leurs seuils.</span><span class="sxs-lookup"><span data-stu-id="0e35d-175">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="0e35d-176">Ces seuils sont réglés dynamiquement pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="0e35d-176">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="0e35d-177">C’est le cas par défaut. La plupart des GC se produisent suite à des allocations sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-177">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="0e35d-178">La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée.</span><span class="sxs-lookup"><span data-stu-id="0e35d-178">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="0e35d-179">Si la méthode <xref:System.GC.Collect?displayProperty=nameWithType> sans paramètre est appelée ou qu’une autre surcharge reçoit <xref:System.GC.MaxGeneration?displayProperty=nameWithType> comme argument, le LOH est nettoyé avec le reste du tas managé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-179">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="0e35d-180">Le système est en situation d’insuffisance de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e35d-180">The system is in low memory situation.</span></span>

  <span data-ttu-id="0e35d-181">Cela se produit quand le récupérateur de mémoire reçoit une notification de mémoire haute du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-181">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="0e35d-182">Si le récupérateur de mémoire pense qu’un GC de la génération 2 peut être productif, il le déclenche.</span><span class="sxs-lookup"><span data-stu-id="0e35d-182">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="0e35d-183">Incidences sur le rendement de LOH</span><span class="sxs-lookup"><span data-stu-id="0e35d-183">LOH performance implications</span></span>

<span data-ttu-id="0e35d-184">Les allocations sur le tas de grands objets impacte les performances des façons suivantes.</span><span class="sxs-lookup"><span data-stu-id="0e35d-184">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="0e35d-185">Coût d’allocation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-185">Allocation cost.</span></span>

  <span data-ttu-id="0e35d-186">Le CLR garantit que la mémoire allouée pour chaque nouvel objet est libérée.</span><span class="sxs-lookup"><span data-stu-id="0e35d-186">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="0e35d-187">Cela signifie que le coût d’allocation d’un grand objet est complètement dominé par la libération de la mémoire (sauf s’il déclenche un GC).</span><span class="sxs-lookup"><span data-stu-id="0e35d-187">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="0e35d-188">S’il faut 2 cycles pour libérer un octet, il faut 170 000 cycles pour libérer le plus petit des grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-188">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="0e35d-189">Pour libérer la mémoire d’un objet de 16 Mo sur une machine de 2 GHz, il faut environ 16 ms.</span><span class="sxs-lookup"><span data-stu-id="0e35d-189">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="0e35d-190">C’est un coût plutôt élevé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-190">That's a rather large cost.</span></span>

- <span data-ttu-id="0e35d-191">Coût de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="0e35d-191">Collection cost.</span></span>

  <span data-ttu-id="0e35d-192">Comme le LOH et la génération 2 sont nettoyés ensemble, si le seuil de l’un des deux est dépassé, un nettoyage de la génération 2 est déclenché.</span><span class="sxs-lookup"><span data-stu-id="0e35d-192">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="0e35d-193">Si le nettoyage de la génération 2 est déclenché à cause du LOH, la génération 2 n’est pas forcément plus petite après le GC.</span><span class="sxs-lookup"><span data-stu-id="0e35d-193">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="0e35d-194">Si la génération 2 n’a pas beaucoup de données, l’impact est minime.</span><span class="sxs-lookup"><span data-stu-id="0e35d-194">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="0e35d-195">En revanche, si la génération 2 est grande, le nettoyage peut entraîner des problèmes de performances s’il faut déclencher plusieurs GC sur la génération 2.</span><span class="sxs-lookup"><span data-stu-id="0e35d-195">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="0e35d-196">Si de nombreux grands objets sont alloués de façon très temporaire et que vous avez un grand SOH, vous risquez de passer trop de temps sur les GC.</span><span class="sxs-lookup"><span data-stu-id="0e35d-196">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="0e35d-197">Par ailleurs, le coût d’allocation vient s’ajouter si vous continuez d’allouer et de libérer de très grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-197">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="0e35d-198">Éléments de tableau avec des types référence.</span><span class="sxs-lookup"><span data-stu-id="0e35d-198">Array elements with reference types.</span></span>

  <span data-ttu-id="0e35d-199">Les très grands objets sur le LOH sont généralement des tableaux (il est très rare d’avoir un objet d’instance très grand).</span><span class="sxs-lookup"><span data-stu-id="0e35d-199">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="0e35d-200">Si les éléments d’un tableau ont beaucoup de références, le coût est plus élevé.</span><span class="sxs-lookup"><span data-stu-id="0e35d-200">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="0e35d-201">Si l’élément n’a aucune référence, le récupérateur de mémoire n’a pas besoin de traiter le tableau.</span><span class="sxs-lookup"><span data-stu-id="0e35d-201">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="0e35d-202">Par exemple, si vous utilisez un tableau pour stocker des nœuds dans une arborescence binaire, vous pouvez l’implémenter en référençant les nœuds droit et gauche d’un nœud comme étant les nœuds eux-mêmes :</span><span class="sxs-lookup"><span data-stu-id="0e35d-202">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="0e35d-203">Si `num_nodes` est grand, le récupérateur de mémoire doit traiter au moins deux références par élément.</span><span class="sxs-lookup"><span data-stu-id="0e35d-203">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="0e35d-204">Une autre méthode est de stocker l’index des nœuds droit et gauche :</span><span class="sxs-lookup"><span data-stu-id="0e35d-204">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="0e35d-205">Au lieu de référencer les données du nœud gauche comme `left.d`, vous les référencez comme `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="0e35d-205">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="0e35d-206">Ainsi, le récupérateur de mémoire n’a pas besoin d’examiner les références des nœuds gauche et droit.</span><span class="sxs-lookup"><span data-stu-id="0e35d-206">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="0e35d-207">Des trois facteurs, les deux premiers ont généralement plus d’impact que le troisième.</span><span class="sxs-lookup"><span data-stu-id="0e35d-207">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="0e35d-208">Pour cette raison, nous vous recommandons d’allouer un pool de grands objets que vous réutilisez au lieu d’allouer des objets temporaires.</span><span class="sxs-lookup"><span data-stu-id="0e35d-208">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collect-performance-data-for-the-loh"></a><span data-ttu-id="0e35d-209">Recueillir des données sur le rendement pour le LOH</span><span class="sxs-lookup"><span data-stu-id="0e35d-209">Collect performance data for the LOH</span></span>

<span data-ttu-id="0e35d-210">Avant de collecter des données de performances pour une zone spécifique, vous devez déjà avoir effectué les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="0e35d-210">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="0e35d-211">Rechercher les raisons d’examiner cette zone.</span><span class="sxs-lookup"><span data-stu-id="0e35d-211">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="0e35d-212">Examiner toutes les autres zones connues sans trouver ce qui pourrait expliquer le problème de performances rencontré.</span><span class="sxs-lookup"><span data-stu-id="0e35d-212">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="0e35d-213">Consultez le blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) (Comprendre le problème avant d’essayer de chercher une solution) pour plus d’informations sur les principes fondamentaux de la mémoire et du processeur.</span><span class="sxs-lookup"><span data-stu-id="0e35d-213">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="0e35d-214">Vous pouvez utiliser les outils suivants pour collecter des données sur les performances du LOH :</span><span class="sxs-lookup"><span data-stu-id="0e35d-214">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="0e35d-215">Compteurs de performance pour la mémoire CRL .NET</span><span class="sxs-lookup"><span data-stu-id="0e35d-215">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="0e35d-216">Événements ETW</span><span class="sxs-lookup"><span data-stu-id="0e35d-216">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="0e35d-217">Débogueur</span><span class="sxs-lookup"><span data-stu-id="0e35d-217">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="0e35d-218">Compteurs de performances pour la mémoire CRL .NET</span><span class="sxs-lookup"><span data-stu-id="0e35d-218">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="0e35d-219">Ces compteurs de performances sont une bonne première étape pour rechercher les problèmes de performances (même si nous vous recommandons d’utiliser les [événements ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="0e35d-219">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="0e35d-220">Vous configurez le moniteur de performances en ajoutant les compteurs souhaités, comme le montre la Figure 4.</span><span class="sxs-lookup"><span data-stu-id="0e35d-220">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="0e35d-221">Ceux qui sont pertinents pour le LOH sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="0e35d-221">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="0e35d-222">**Gen 2 Collections**</span><span class="sxs-lookup"><span data-stu-id="0e35d-222">**Gen 2 Collections**</span></span>

   <span data-ttu-id="0e35d-223">Affiche le nombre d’occurrences de GC de la génération 2 depuis le démarrage du processus.</span><span class="sxs-lookup"><span data-stu-id="0e35d-223">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="0e35d-224">Ce compteur est incrémenté à la fin de chaque nettoyage de la génération 2 (aussi appelé nettoyage complet de la mémoire).</span><span class="sxs-lookup"><span data-stu-id="0e35d-224">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="0e35d-225">Ce compteur affiche la dernière valeur observée.</span><span class="sxs-lookup"><span data-stu-id="0e35d-225">This counter displays the last observed value.</span></span>

- <span data-ttu-id="0e35d-226">**Taille du tas d’objets volumineux**</span><span class="sxs-lookup"><span data-stu-id="0e35d-226">**Large Object Heap size**</span></span>

   <span data-ttu-id="0e35d-227">Affiche la taille actuelle du LOH en octets (y compris l’espace libre).</span><span class="sxs-lookup"><span data-stu-id="0e35d-227">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="0e35d-228">Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-228">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="0e35d-229">En général, vous surveillez les compteurs de performances par le biais du moniteur de performances (PerfMon.exe).</span><span class="sxs-lookup"><span data-stu-id="0e35d-229">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="0e35d-230">Utilisez « Ajouter des compteurs » pour ajouter le compteur de votre choix pour les processus qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="0e35d-230">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="0e35d-231">Vous pouvez enregistrer les données des compteurs de performances dans un fichier journal, comme illustré dans la figure 4 :</span><span class="sxs-lookup"><span data-stu-id="0e35d-231">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="0e35d-232">![Capture d’écran qui montre l’ajout de compteurs de performance.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="0e35d-232">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="0e35d-233">Figure 4 : LOH après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="0e35d-233">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="0e35d-234">Les compteurs de performances peuvent également être interrogés par programmation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-234">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="0e35d-235">Beaucoup d’utilisateurs les collectent de cette façon dans le cadre de leur processus de test normal.</span><span class="sxs-lookup"><span data-stu-id="0e35d-235">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="0e35d-236">S’ils repèrent des compteurs avec des valeurs anormales, ils utilisent d’autres moyens d’obtenir des données plus détaillées pour les aider dans leurs recherches.</span><span class="sxs-lookup"><span data-stu-id="0e35d-236">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="0e35d-237">Nous vous recommandons d’utiliser les événements ETW au lieu des compteurs de performances, car ETW fournit des informations plus détaillées.</span><span class="sxs-lookup"><span data-stu-id="0e35d-237">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="0e35d-238">Événements ETW</span><span class="sxs-lookup"><span data-stu-id="0e35d-238">ETW events</span></span>

<span data-ttu-id="0e35d-239">Le récupérateur de mémoire fournit un riche ensemble d’événements ETW pour vous aider à comprendre ce que fait le tas et pourquoi.</span><span class="sxs-lookup"><span data-stu-id="0e35d-239">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="0e35d-240">Les billets de blog suivants décrivent comment collecter et comprendre les événements GC avec ETW :</span><span class="sxs-lookup"><span data-stu-id="0e35d-240">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="0e35d-241">Événements GC ETW - 1</span><span class="sxs-lookup"><span data-stu-id="0e35d-241">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="0e35d-242">Événements ETW de GC - 2</span><span class="sxs-lookup"><span data-stu-id="0e35d-242">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="0e35d-243">Événements ETW de GC - 3</span><span class="sxs-lookup"><span data-stu-id="0e35d-243">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="0e35d-244">Événements ETW de GC - 4</span><span class="sxs-lookup"><span data-stu-id="0e35d-244">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="0e35d-245">Pour identifier le nombre excessif de GC de la génération 2 dus à des allocations de LOH temporaires, observez la colonne Raison du déclencheur pour les GC.</span><span class="sxs-lookup"><span data-stu-id="0e35d-245">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="0e35d-246">Pour un test simple qui alloue uniquement des grands objets temporaires, vous pouvez collecter des informations sur les événements ETW avec la ligne de commande [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) suivante :</span><span class="sxs-lookup"><span data-stu-id="0e35d-246">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="0e35d-247">Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="0e35d-247">The result is something like this:</span></span>

<span data-ttu-id="0e35d-248">![Capture d’écran montrant les événements ETW dans PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="0e35d-248">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="0e35d-249">Figure 5 : Événements ETW affichés à l’aide de PerfView</span><span class="sxs-lookup"><span data-stu-id="0e35d-249">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="0e35d-250">Comme vous pouvez le voir, tous les GC sont effectués sur la génération 2 et ils sont déclenchés par AllocLarge, ce qui signifie que c’est l’allocation d’un grand objet qui a déclenché ce GC.</span><span class="sxs-lookup"><span data-stu-id="0e35d-250">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="0e35d-251">Nous savons que ces allocations sont temporaires parce que la colonne **% de taux de survie LOH** indique 1 %.</span><span class="sxs-lookup"><span data-stu-id="0e35d-251">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="0e35d-252">Vous pouvez collecter d’autres événements ETW qui vous indiquent qui a alloué ces grands objets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-252">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="0e35d-253">La ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="0e35d-253">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="0e35d-254">collecte un événement AllocationTick qui est déclenché toutes les 100 000 allocations environ.</span><span class="sxs-lookup"><span data-stu-id="0e35d-254">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="0e35d-255">En d’autres termes, un événement est déclenché chaque fois qu’un grand objet est alloué.</span><span class="sxs-lookup"><span data-stu-id="0e35d-255">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="0e35d-256">Vous pouvez alors examiner une des vues d’allocation de tas du récupérateur de mémoire qui indique les pile d’appels qui ont alloué des grands objets :</span><span class="sxs-lookup"><span data-stu-id="0e35d-256">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="0e35d-257">![Capture d’écran montrant une vue du tas garbage collector.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="0e35d-257">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="0e35d-258">Figure 6 : Une vue d’allocation de tas du récupérateur de mémoire</span><span class="sxs-lookup"><span data-stu-id="0e35d-258">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="0e35d-259">Comme vous pouvez le voir, il s’agit d’un test très simple qui alloue simplement de grands objets à partir de sa méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="0e35d-259">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="0e35d-260">Débogueur</span><span class="sxs-lookup"><span data-stu-id="0e35d-260">A debugger</span></span>

<span data-ttu-id="0e35d-261">Si tout ce que vous avez est un vidage de mémoire et que vous devez examiner les objets qui se trouvent sur le LOH, vous pouvez utiliser [l’extension de débogueur SoS](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) fournie par .NET.</span><span class="sxs-lookup"><span data-stu-id="0e35d-261">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../../docs/framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="0e35d-262">Les commandes de débogage indiquées dans cette section sont applicables aux [débogueurs Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="0e35d-262">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="0e35d-263">Le code suivant illustre un exemple de sortie de l’analyse du LOH :</span><span class="sxs-lookup"><span data-stu-id="0e35d-263">The following shows sample output from analyzing the LOH:</span></span>

```console
0:003> .loadby sos mscorwks
0:003> !eeheap -gc
Number of GC Heaps: 1
generation 0 starts at 0x013e35ec
sdgeneration 1 starts at 0x013e1b6c
generation 2 starts at 0x013e1000
ephemeral segment allocation context: none
segment   begin allocated     size
0018f2d0 790d5588 790f4b38 0x0001f5b0(128432)
013e0000 013e1000 013e35f8 0x000025f8(9720)
Large object heap starts at 0x023e1000
segment   begin allocated     size
023e0000 023e1000 033db630 0x00ffa630(16754224)
033e0000 033e1000 043cdf98 0x00fecf98(16699288)
043e0000 043e1000 05368b58 0x00f87b58(16284504)
Total Size 0x2f90cc8(49876168)
------------------------------
GC Heap Size 0x2f90cc8(49876168)
0:003> !dumpheap -stat 023e1000 033db630
total 133 objects
Statistics:
MT   Count   TotalSize Class Name
001521d0       66     2081792     Free
7912273c       63     6663696 System.Byte[]
7912254c       4     8008736 System.Object[]
Total 133 objects
```

<span data-ttu-id="0e35d-264">La taille du tas LOH est (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 octets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-264">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="0e35d-265">Entre les adresses 023e1000 et 033db630, 8 008 736 octets sont occupés par un tableau d’objets <xref:System.Object?displayProperty=nameWithType>, 6 663 696 octets sont occupés par un tableau d’objets <xref:System.Byte?displayProperty=nameWithType> et 2 081 792 octets sont occupés par de l’espace libre.</span><span class="sxs-lookup"><span data-stu-id="0e35d-265">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="0e35d-266">Parfois, le débogueur montre que la taille totale du LOH est inférieure à 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="0e35d-266">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="0e35d-267">C’est parce que le runtime lui-même utilise le LOH pour allouer des objets dont la taille est inférieure à celle d’un grand objet.</span><span class="sxs-lookup"><span data-stu-id="0e35d-267">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="0e35d-268">Comme le LOH n’est pas compacté, il est parfois perçu comme la source de la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="0e35d-268">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="0e35d-269">Une fragmentation peut désigner :</span><span class="sxs-lookup"><span data-stu-id="0e35d-269">Fragmentation means:</span></span>

- <span data-ttu-id="0e35d-270">La fragmentation du tas managé, indiquée par la quantité d’espace libre entre les objets managés.</span><span class="sxs-lookup"><span data-stu-id="0e35d-270">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="0e35d-271">Dans SoS, la commande `!dumpheap –type Free` affiche la quantité d’espace libre entre les objets managés.</span><span class="sxs-lookup"><span data-stu-id="0e35d-271">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="0e35d-272">La fragmentation de l’espace d’adressage de mémoire virtuelle, qui est la mémoire marquée comme `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="0e35d-272">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="0e35d-273">Vous pouvez l’obtenir à l’aide de diverses commandes de débogueur dans windbg.</span><span class="sxs-lookup"><span data-stu-id="0e35d-273">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="0e35d-274">L’exemple suivant montre une fragmentation dans l’espace de mémoire virtuelle :</span><span class="sxs-lookup"><span data-stu-id="0e35d-274">The following example shows fragmentation in the VM space:</span></span>

   ```console
   0:000> !address
   00000000 : 00000000 - 00010000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   00010000 : 00010000 - 00002000
   Type     00020000 MEM_PRIVATE
   Protect 00000004 PAGE_READWRITE
   State   00001000 MEM_COMMIT
   Usage   RegionUsageEnvironmentBlock
   00012000 : 00012000 - 0000e000
   Type     00000000
   Protect 00000001 PAGE_NOACCESS
   State   00010000 MEM_FREE
   Usage   RegionUsageFree
   … [omitted]
   -------------------- Usage SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Pct(Busy)   Usage
   701000 (   7172) : 00.34%   20.69%   : RegionUsageIsVAD
   7de15000 ( 2062420) : 98.35%   00.00%   : RegionUsageFree
   1452000 (   20808) : 00.99%   60.02%   : RegionUsageImage
   300000 (   3072) : 00.15%   08.86%   : RegionUsageStack
   3000 (     12) : 00.00%   00.03%   : RegionUsageTeb
   381000 (   3588) : 00.17%   10.35%   : RegionUsageHeap
   0 (       0) : 00.00%   00.00%   : RegionUsagePageHeap
   1000 (       4) : 00.00%   00.01%   : RegionUsagePeb
   1000 (       4) : 00.00%   00.01%   : RegionUsageProcessParametrs
   2000 (       8) : 00.00%   00.02%   : RegionUsageEnvironmentBlock
   Tot: 7fff0000 (2097088 KB) Busy: 021db000 (34668 KB)

   -------------------- Type SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   7de15000 ( 2062420) : 98.35%   : <free>
   1452000 (   20808) : 00.99%   : MEM_IMAGE
   69f000 (   6780) : 00.32%   : MEM_MAPPED
   6ea000 (   7080) : 00.34%   : MEM_PRIVATE

   -------------------- State SUMMARY --------------------------
   TotSize (     KB)   Pct(Tots) Usage
   1a58000 (   26976) : 01.29%   : MEM_COMMIT
   7de15000 ( 2062420) : 98.35%   : MEM_FREE
   783000 (   7692) : 00.37%   : MEM_RESERVE

   Largest free region: Base 01432000 - Size 707ee000 (1843128 KB)
   ```

<span data-ttu-id="0e35d-275">Souvent, la fragmentation de mémoire virtuelle est causée par des grands objets temporaires qui obligent le récupérateur de mémoire à fréquemment acquérir de nouveaux segments de tas managé du système d’exploitation et lui en rendre des vides.</span><span class="sxs-lookup"><span data-stu-id="0e35d-275">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="0e35d-276">Pour vérifier si le LOH provoque une fragmentation de mémoire virtuelle, vous pouvez définir un point d’arrêt sur [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) et [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) et voir qui les appelle.</span><span class="sxs-lookup"><span data-stu-id="0e35d-276">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="0e35d-277">Par exemple, pour voir qui a essayé d’allouer des blocs de mémoire virtuelle de système d’exploitation supérieurs à 8 Mo, vous pouvez définir un point d’arrêt de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="0e35d-277">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="0e35d-278">Cette commande entre dans le débbugger et montre la pile d’appel que si [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) est appelé avec une taille d’allocation supérieure à 8 Mo (0x800000).</span><span class="sxs-lookup"><span data-stu-id="0e35d-278">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="0e35d-279">CLR 2.0 a ajouté une fonctionnalité appelée *VM Hoarding* (Réserve de mémoire virtuelle) qui peut être utile dans les scénarios où des segments (y compris ceux des tas de petits et grands objets) sont fréquemment acquis et libérés.</span><span class="sxs-lookup"><span data-stu-id="0e35d-279">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="0e35d-280">Pour utiliser la fonctionnalité VM Hoarding, vous spécifiez un indicateur de démarrage appelé `STARTUP_HOARD_GC_VM` via l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="0e35d-280">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="0e35d-281">Au lieu de renvoyer des segments vides au système d’exploitation, le CLR annule la réservation de mémoire sur ces segments et les met sur liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="0e35d-281">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="0e35d-282">(Notez que le CLR ne le fait pas pour les segments qui sont trop grands.) Le CLR utilise plus tard ces segments pour satisfaire les nouvelles demandes de segment.</span><span class="sxs-lookup"><span data-stu-id="0e35d-282">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="0e35d-283">La prochaine fois que votre application a besoin d’un nouveau segment, le CLR en utilise un de cette liste d’attente, s’il est assez grand.</span><span class="sxs-lookup"><span data-stu-id="0e35d-283">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="0e35d-284">La thésaurisation VM est également utile pour les applications qui veulent conserver les segments qu’ils ont déjà acquis, tels que certaines applications serveur qui sont les applications dominantes en cours d’exécution sur le système, pour éviter les exceptions hors mémoire.</span><span class="sxs-lookup"><span data-stu-id="0e35d-284">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out-of-memory exceptions.</span></span>

<span data-ttu-id="0e35d-285">Nous vous recommandons vivement de tester soigneusement votre application quand vous utilisez cette fonctionnalité, pour vérifier qu’elle utilise la mémoire de façon suffisamment stable.</span><span class="sxs-lookup"><span data-stu-id="0e35d-285">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>

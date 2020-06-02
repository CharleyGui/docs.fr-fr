---
title: Tas d’objets volumineux (LOH) sur Windows
description: Cet article traite des objets volumineux, de la façon dont ils sont gérés par le garbage collector .NET et des implications sur les performances de l’utilisation d’objets volumineux.
ms.date: 05/02/2018
helpviewer_keywords:
- large object heap (LOH)"
- LOH
- garbage collection, large object heap
- GC [.NET ], large object heap
ms.openlocfilehash: 87105acbd43eb8eda0daa00c65ca0635f5e1cc74
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286026"
---
# <a name="the-large-object-heap-on-windows-systems"></a><span data-ttu-id="125ee-103">Tas de grands objets sur les systèmes Windows</span><span class="sxs-lookup"><span data-stu-id="125ee-103">The large object heap on Windows systems</span></span>

<span data-ttu-id="125ee-104">Le garbage collector (GC) .NET divise les objets en objets petits et grands.</span><span class="sxs-lookup"><span data-stu-id="125ee-104">The .NET garbage collector (GC) divides objects up into small and large objects.</span></span> <span data-ttu-id="125ee-105">Quand un objet est grand, certains de ses attributs prennent plus d’importance que s’il est petit.</span><span class="sxs-lookup"><span data-stu-id="125ee-105">When an object is large, some of its attributes become more significant than if the object is small.</span></span> <span data-ttu-id="125ee-106">Par exemple, si vous la compactez &mdash; , la copie en mémoire ailleurs sur le tas &mdash; peut être coûteuse.</span><span class="sxs-lookup"><span data-stu-id="125ee-106">For instance, compacting it&mdash;that is, copying it in memory elsewhere on the heap&mdash;can be expensive.</span></span> <span data-ttu-id="125ee-107">Pour cette raison, le garbage collector place des objets volumineux sur le tas d’objets volumineux (LOH).</span><span class="sxs-lookup"><span data-stu-id="125ee-107">Because of this, the garbage collector places large objects on the large object heap (LOH).</span></span> <span data-ttu-id="125ee-108">Cet article explique ce qui qualifie un objet en tant qu’objet volumineux, la façon dont les objets volumineux sont collectés et les implications en termes de performances imposées par les objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="125ee-108">This article discusses what qualifies an object as a large object, how large objects are collected, and what kind of performance implications large objects impose.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="125ee-109">Cet article décrit le tas d’objets volumineux dans .NET Framework et .NET Core s’exécutant sur des systèmes Windows uniquement.</span><span class="sxs-lookup"><span data-stu-id="125ee-109">This article discusses the large object heap in .NET Framework and .NET Core running on Windows systems only.</span></span> <span data-ttu-id="125ee-110">Elle ne couvre pas le LOH exécuté sur des implémentations de .NET sur d’autres plateformes.</span><span class="sxs-lookup"><span data-stu-id="125ee-110">It does not cover the LOH running on .NET implementations on other platforms.</span></span>

## <a name="how-an-object-ends-up-on-the-loh"></a><span data-ttu-id="125ee-111">Comment un objet se termine sur le LOH</span><span class="sxs-lookup"><span data-stu-id="125ee-111">How an object ends up on the LOH</span></span>

<span data-ttu-id="125ee-112">Si la taille d’un objet est supérieure ou égale à 85 000 octets, il est considéré comme un objet volumineux.</span><span class="sxs-lookup"><span data-stu-id="125ee-112">If an object is greater than or equal to 85,000 bytes in size, it’s considered a large object.</span></span> <span data-ttu-id="125ee-113">Ce chiffre a été déterminé par le réglage des performances.</span><span class="sxs-lookup"><span data-stu-id="125ee-113">This number was determined by performance tuning.</span></span> <span data-ttu-id="125ee-114">Quand une demande d’allocation d’objet est de 85 000 octets ou plus, le runtime l’alloue sur le tas de grands objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-114">When an object allocation request is for 85,000 or more bytes, the runtime allocates it on the large object heap.</span></span>

<span data-ttu-id="125ee-115">Pour comprendre ce que cela signifie, il est utile d’examiner quelques notions de base sur le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="125ee-115">To understand what this means, it's useful to examine some fundamentals about the garbage collector.</span></span>

<span data-ttu-id="125ee-116">Le garbage collector est un collecteur générationnel.</span><span class="sxs-lookup"><span data-stu-id="125ee-116">The garbage collector is a generational collector.</span></span> <span data-ttu-id="125ee-117">Il a trois générations : génération 0, génération 1 et génération 2.</span><span class="sxs-lookup"><span data-stu-id="125ee-117">It has three generations: generation 0, generation 1, and generation 2.</span></span> <span data-ttu-id="125ee-118">La raison de ces 3 générations est que la plupart des objets meurent dans la génération 0 (dans une application optimisée).</span><span class="sxs-lookup"><span data-stu-id="125ee-118">The reason for having 3 generations is that, in a well-tuned app, most objects die in gen0.</span></span> <span data-ttu-id="125ee-119">Par exemple, dans une application serveur, les allocations associées à chaque demande doivent mourir une fois la demande terminée.</span><span class="sxs-lookup"><span data-stu-id="125ee-119">For example, in a server app, the allocations associated with each request should die after the request is finished.</span></span> <span data-ttu-id="125ee-120">Les demandes d’allocation en cours passent en génération 1 et y meurent.</span><span class="sxs-lookup"><span data-stu-id="125ee-120">The in-flight allocation requests will make it into gen1 and die there.</span></span> <span data-ttu-id="125ee-121">La génération 1 joue, pour ainsi dire, le rôle de tampon entre les zones d’objets jeunes et les zones d’objets qui vivent déjà depuis un certain temps.</span><span class="sxs-lookup"><span data-stu-id="125ee-121">Essentially, gen1 acts as a buffer between young object areas and long-lived object areas.</span></span>

<span data-ttu-id="125ee-122">Les petits objets sont toujours alloués dans la génération 0 et, selon leur durée de vie, peuvent être promus dans les générations 1 ou 2.</span><span class="sxs-lookup"><span data-stu-id="125ee-122">Small objects are always allocated in generation 0 and, depending on their lifetime, may be promoted to generation 1 or generation2.</span></span> <span data-ttu-id="125ee-123">Les grands objets sont toujours alloués dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="125ee-123">Large objects are always allocated in generation 2.</span></span>

<span data-ttu-id="125ee-124">Les grands objets appartiennent à la génération 2 parce qu’ils sont nettoyés uniquement lors d’un nettoyage de la génération 2.</span><span class="sxs-lookup"><span data-stu-id="125ee-124">Large objects belong to generation 2 because they are collected only during a generation 2 collection.</span></span> <span data-ttu-id="125ee-125">Quand une génération est nettoyée, ses générations plus jeunes sont également nettoyées.</span><span class="sxs-lookup"><span data-stu-id="125ee-125">When a generation is collected, all its younger generation(s) are also collected.</span></span> <span data-ttu-id="125ee-126">Par exemple, pendant le nettoyage de la mémoire (GC, Garbage Collection) de la génération 1, les générations 1 et 0 sont toutes deux nettoyées.</span><span class="sxs-lookup"><span data-stu-id="125ee-126">For example, when a generation 1 GC happens, both generation 1 and 0 are collected.</span></span> <span data-ttu-id="125ee-127">De la même façon, pendant le GC de la génération 2, le tas tout entier est nettoyé.</span><span class="sxs-lookup"><span data-stu-id="125ee-127">And when a generation 2 GC happens, the whole heap is collected.</span></span> <span data-ttu-id="125ee-128">Pour cette raison, un GC de la génération 2 est également appelé *GC complet*.</span><span class="sxs-lookup"><span data-stu-id="125ee-128">For this reason, a generation 2 GC is also called a *full GC*.</span></span> <span data-ttu-id="125ee-129">Cet article fait référence au GC de la génération 2 et non au GC complet, mais les termes sont interchangeables.</span><span class="sxs-lookup"><span data-stu-id="125ee-129">This article refers to generation 2 GC instead of full GC, but the terms are interchangeable.</span></span>

<span data-ttu-id="125ee-130">Les générations fournissent une vue logique du tas du récupérateur de mémoire.</span><span class="sxs-lookup"><span data-stu-id="125ee-130">Generations provide a logical view of the GC heap.</span></span> <span data-ttu-id="125ee-131">Physiquement, les objets vivent dans des segments de tas managés.</span><span class="sxs-lookup"><span data-stu-id="125ee-131">Physically, objects live in managed heap segments.</span></span> <span data-ttu-id="125ee-132">Un *segment de tas managé* est un bloc de mémoire que le récupérateur de mémoire réserve sur le système d’exploitation en appelant la [fonction VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) pour le compte du code managé.</span><span class="sxs-lookup"><span data-stu-id="125ee-132">A *managed heap segment* is a chunk of memory that the GC reserves from the OS by calling the [VirtualAlloc function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) on behalf of managed code.</span></span> <span data-ttu-id="125ee-133">Lorsque le CLR est chargé, le garbage collector alloue deux segments de tas initiaux : un pour les petits objets (le tas de petits objets, ou SOH) et l’autre pour les objets volumineux (le tas d’objets volumineux).</span><span class="sxs-lookup"><span data-stu-id="125ee-133">When the CLR is loaded, the GC allocates two initial heap segments: one for small objects (the small object heap, or SOH), and one for large objects (the large object heap).</span></span>

<span data-ttu-id="125ee-134">Les demandes d’allocation sont alors traitées en plaçant des objets managés sur ces segments de tas managés.</span><span class="sxs-lookup"><span data-stu-id="125ee-134">The allocation requests are then satisfied by putting managed objects on these managed heap segments.</span></span> <span data-ttu-id="125ee-135">Si l’objet est inférieur à 85 000 octets, il est placé sur un segment SOH, sinon, sur un segment LOH.</span><span class="sxs-lookup"><span data-stu-id="125ee-135">If the object is less than 85,000 bytes, it is put on the segment for the SOH; otherwise, it is put on an LOH segment.</span></span> <span data-ttu-id="125ee-136">Les segments sont réservés (en blocs plus petits) à mesure que leur nombre d’objets alloués augmente.</span><span class="sxs-lookup"><span data-stu-id="125ee-136">Segments are committed (in smaller chunks) as more and more objects are allocated onto them.</span></span>
<span data-ttu-id="125ee-137">Pour le SOH, les objets qui survivent à un GC sont promus à la génération suivante.</span><span class="sxs-lookup"><span data-stu-id="125ee-137">For the SOH, objects that survive a GC are promoted to the next generation.</span></span> <span data-ttu-id="125ee-138">Les objets qui survivent à un nettoyage de la génération 0 sont considérés comme des objets de génération 1, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="125ee-138">Objects that survive a generation 0 collection are now considered generation 1 objects, and so on.</span></span> <span data-ttu-id="125ee-139">Toutefois, les objets qui survivent à la plus vieille génération sont toujours considérés comme des objets de cette génération.</span><span class="sxs-lookup"><span data-stu-id="125ee-139">However, objects that survive the oldest generation are still considered to be in the oldest generation.</span></span> <span data-ttu-id="125ee-140">En d’autres termes, les survivants de la génération 2 sont des objets de la génération 2 et les survivants du LOH sont des objets du LOH (qui sont nettoyés avec la génération 2).</span><span class="sxs-lookup"><span data-stu-id="125ee-140">In other words, survivors from generation 2 are generation 2 objects; and survivors from the LOH are LOH objects (which are collected with gen2).</span></span>

<span data-ttu-id="125ee-141">Le code d’utilisateur peut seulement allouer dans la génération 0 (petits objets) ou le LOH (grands objets).</span><span class="sxs-lookup"><span data-stu-id="125ee-141">User code can only allocate in generation 0 (small objects) or the LOH (large objects).</span></span> <span data-ttu-id="125ee-142">Seul le récupérateur de mémoire peut « allouer » des objets dans la génération 1 (en promouvant les survivants de la génération 0) et la génération 2 (en promouvant les survivants des générations 1 et 2).</span><span class="sxs-lookup"><span data-stu-id="125ee-142">Only the GC can “allocate” objects in generation 1 (by promoting survivors from generation 0) and generation 2 (by promoting survivors from generations 1 and 2).</span></span>

<span data-ttu-id="125ee-143">Quand un nettoyage de la mémoire est déclenché, le récupérateur de mémoire repère les objets en vie et les compacte.</span><span class="sxs-lookup"><span data-stu-id="125ee-143">When a garbage collection is triggered, the GC traces through the live objects and compacts them.</span></span> <span data-ttu-id="125ee-144">Parce que le compactage coûte cher, le récupérateur de mémoire *balaye* le LOH et dresse une liste des objets morts qui peuvent être réutilisés plus tard pour répondre aux demandes d’allocation des grands objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-144">But because compaction is expensive, the GC *sweeps* the LOH; it makes a free list out of dead objects that can be reused later to satisfy large object allocation requests.</span></span> <span data-ttu-id="125ee-145">Les objets morts adjacents sont transformés en un seul objet libre.</span><span class="sxs-lookup"><span data-stu-id="125ee-145">Adjacent dead objects are made into one free object.</span></span>

<span data-ttu-id="125ee-146">Le .NET Framework (à partir de .NET Framework 4.5.1) et .NET Core intègrent la propriété <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> qui permet aux utilisateurs de spécifier que le LOH doit être compacté au prochain GC bloquant complet.</span><span class="sxs-lookup"><span data-stu-id="125ee-146">.NET Core and .NET Framework (starting with .NET Framework 4.5.1) include the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode?displayProperty=nameWithType> property that allows users to specify that the LOH should be compacted during the next full blocking GC.</span></span> <span data-ttu-id="125ee-147">Par la suite, .NET peut décider de compacter le LOH automatiquement.</span><span class="sxs-lookup"><span data-stu-id="125ee-147">And in the future, .NET may decide to compact the LOH automatically.</span></span> <span data-ttu-id="125ee-148">Donc, si vous allouez des grands objets et voulez garantir qu'ils ne bougent pas, vous devez quand même les épingler.</span><span class="sxs-lookup"><span data-stu-id="125ee-148">This means that, if you allocate large objects and want to make sure that they don’t move, you should still pin them.</span></span>

<span data-ttu-id="125ee-149">La figure 1 illustre un scénario dans lequel le récupérateur de mémoire forme la génération 1 après le premier GC de la génération 0 où `Obj1` et `Obj3` sont morts, et forme la génération 2 après le premier GC de la génération 1 où `Obj2` et `Obj5` sont morts.</span><span class="sxs-lookup"><span data-stu-id="125ee-149">Figure 1 illustrates a scenario where the GC forms generation 1 after the first generation 0 GC where `Obj1` and `Obj3` are dead, and it forms generation 2 after the first generation 1 GC where `Obj2` and `Obj5` are dead.</span></span> <span data-ttu-id="125ee-150">Notez que cette figure et les suivantes sont uniquement à titre d’illustration. Elles contiennent très peu d’objets pour mieux montrer ce qui se passe sur le tas.</span><span class="sxs-lookup"><span data-stu-id="125ee-150">Note that this and the following figures are only for illustration purposes; they contain very few objects to better show what happens on the heap.</span></span> <span data-ttu-id="125ee-151">En réalité, un GC implique généralement bien plus d’objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-151">In reality, many more objects are typically involved in a GC.</span></span>

![Figure 1 : GC de la génération 0 et GC de la génération 1](media/loh/loh-figure-1.jpg)\
<span data-ttu-id="125ee-153">Figure 1 : GC des générations 0 et 1.</span><span class="sxs-lookup"><span data-stu-id="125ee-153">Figure 1: A generation 0 and a generation 1 GC.</span></span>

<span data-ttu-id="125ee-154">La figure 2 montre qu’après un GC de la génération 2 qui a vu que `Obj1` et `Obj2` étaient morts, le récupérateur de mémoire forme un espace libre contigu dans la mémoire qui était auparavant occupée par `Obj1` et `Obj2`, lequel est ensuite utilisé pour répondre à une demande d’allocation concernant `Obj4`.</span><span class="sxs-lookup"><span data-stu-id="125ee-154">Figure 2 shows that after a generation 2 GC which saw that `Obj1` and `Obj2` are dead, the GC forms contiguous free space out of memory that used to be occupied by `Obj1` and `Obj2`, which then was used to satisfy an allocation request for `Obj4`.</span></span> <span data-ttu-id="125ee-155">L’espace entre le dernier objet `Obj3` et la fin du segment peut aussi être utilisé pour répondre aux demandes d’allocation.</span><span class="sxs-lookup"><span data-stu-id="125ee-155">The space after the last object, `Obj3`, to end of the segment can also be used to satisfy allocation requests.</span></span>

![Figure 2 : Après un GC de la génération 2](media/loh/loh-figure-2.jpg)\
<span data-ttu-id="125ee-157">Figure 2 : Après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="125ee-157">Figure 2: After a generation 2 GC</span></span>

<span data-ttu-id="125ee-158">Si l’espace libre est insuffisant pour répondre aux demandes d’allocation des grands objets, le récupérateur de mémoire tente d’acquérir d’autres segments du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="125ee-158">If there isn't enough free space to accommodate the large object allocation requests, the GC first attempts to acquire more segments from the OS.</span></span> <span data-ttu-id="125ee-159">En cas d’échec, il déclenche un GC de la génération 2 pour tenter de libérer l’espace.</span><span class="sxs-lookup"><span data-stu-id="125ee-159">If that fails, it triggers a generation 2 GC in the hope of freeing up some space.</span></span>

<span data-ttu-id="125ee-160">Pendant un GC de la génération 1 ou 2, le récupérateur de mémoire libère les segments qui n’ont pas d’objet en vie et les rend au système d’exploitation en appelant la [fonction VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span><span class="sxs-lookup"><span data-stu-id="125ee-160">During a generation 1 or generation 2 GC, the garbage collector releases segments that have no live objects on them back to the OS by calling the [VirtualFree function](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree).</span></span> <span data-ttu-id="125ee-161">La réservation de l’espace entre le dernier objet en vie et la fin du segment est annulée (sauf sur le segment éphémère, où vivent les générations 0 et 1, sur lequel le récupérateur de mémoire maintient la réservation pour que votre application puisse l’utiliser immédiatement).</span><span class="sxs-lookup"><span data-stu-id="125ee-161">Space after the last live object to the end of the segment is decommitted (except on the ephemeral segment where gen0/gen1 live, where the garbage collector does keep some committed because your application will be allocating in it right away).</span></span> <span data-ttu-id="125ee-162">Par ailleurs, les espaces libres restent réservés bien qu’ils soient réinitialisés, ce qui signifie que le système d’exploitation n’a pas besoin d’écrire de données dans ces espaces une fois revenus sur le disque.</span><span class="sxs-lookup"><span data-stu-id="125ee-162">And the free spaces remain committed though they are reset, meaning that the OS doesn’t need to write data in them back to disk.</span></span>

<span data-ttu-id="125ee-163">Comme que le LOH est collecté uniquement pendant le GC de la génération 2, le segment LOH peut seulement être libéré pendant ce GC.</span><span class="sxs-lookup"><span data-stu-id="125ee-163">Since the LOH is only collected during generation 2 GCs, the LOH segment can only be freed during such a GC.</span></span> <span data-ttu-id="125ee-164">La figure 3 illustre un scénario où le récupérateur de mémoire rend un segment (segment 2) au système d’exploitation et annule la réservation d’espace supplémentaire sur les segments restants.</span><span class="sxs-lookup"><span data-stu-id="125ee-164">Figure 3 illustrates a scenario where the garbage collector releases one segment (segment 2) back to the OS and decommits more space on the remaining segments.</span></span> <span data-ttu-id="125ee-165">S’il doit utiliser l’espace libéré à la fin du segment pour répondre aux demandes d’allocation de grands objets, il réserve de nouveau la mémoire.</span><span class="sxs-lookup"><span data-stu-id="125ee-165">If it needs to use the decommitted space at the end of the segment to satisfy large object allocation requests, it commits the memory again.</span></span> <span data-ttu-id="125ee-166">(Pour obtenir une explication de la réservation/libération, consultez la documentation de [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span><span class="sxs-lookup"><span data-stu-id="125ee-166">(For an explanation of commit/decommit, see the documentation for [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc).</span></span>

![Figure 3 : LOH après un GC de la génération 2](media/loh/loh-figure-3.jpg)\
<span data-ttu-id="125ee-168">Figure 3 : LOH après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="125ee-168">Figure 3: The LOH after a generation 2 GC</span></span>

## <a name="when-is-a-large-object-collected"></a><span data-ttu-id="125ee-169">Quand un grand objet est-il collecté ?</span><span class="sxs-lookup"><span data-stu-id="125ee-169">When is a large object collected?</span></span>

<span data-ttu-id="125ee-170">En général, un GC se produit dans l’une des trois conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="125ee-170">In general, a GC occurs under one of the following three conditions:</span></span>

- <span data-ttu-id="125ee-171">L’allocation dépasse le seuil des grands objets ou de la génération 0.</span><span class="sxs-lookup"><span data-stu-id="125ee-171">Allocation exceeds the generation 0 or large object threshold.</span></span>

  <span data-ttu-id="125ee-172">Le seuil est une propriété des générations.</span><span class="sxs-lookup"><span data-stu-id="125ee-172">The threshold is a property of a generation.</span></span> <span data-ttu-id="125ee-173">Le seuil d’une génération est défini quand le récupérateur de mémoire lui alloue des objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-173">A threshold for a generation is set when the garbage collector allocates objects into it.</span></span> <span data-ttu-id="125ee-174">Quand le seuil est dépassé, un GC est déclenché sur cette génération.</span><span class="sxs-lookup"><span data-stu-id="125ee-174">When the threshold is exceeded, a GC is triggered on that generation.</span></span> <span data-ttu-id="125ee-175">Quand vous allouez des petits ou des grands objets, vous consommez les seuils de la génération 0 et du LOH, respectivement.</span><span class="sxs-lookup"><span data-stu-id="125ee-175">When you allocate small or large objects, you consume generation 0 and the LOH’s thresholds, respectively.</span></span> <span data-ttu-id="125ee-176">Quand le récupérateur de mémoire alloue des objets dans les générations 1 et 2, il consomme leurs seuils.</span><span class="sxs-lookup"><span data-stu-id="125ee-176">When the garbage collector allocates into generation 1 and 2, it consumes their thresholds.</span></span> <span data-ttu-id="125ee-177">Ces seuils sont réglés dynamiquement pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="125ee-177">These thresholds are dynamically tuned as the program runs.</span></span>

  <span data-ttu-id="125ee-178">C’est le cas par défaut. La plupart des GC se produisent suite à des allocations sur le tas managé.</span><span class="sxs-lookup"><span data-stu-id="125ee-178">This is the typical case; most GCs happen because of allocations on the managed heap.</span></span>

- <span data-ttu-id="125ee-179">La méthode <xref:System.GC.Collect%2A?displayProperty=nameWithType> est appelée.</span><span class="sxs-lookup"><span data-stu-id="125ee-179">The <xref:System.GC.Collect%2A?displayProperty=nameWithType> method is called.</span></span>

  <span data-ttu-id="125ee-180">Si la méthode <xref:System.GC.Collect?displayProperty=nameWithType> sans paramètre est appelée ou qu’une autre surcharge reçoit <xref:System.GC.MaxGeneration?displayProperty=nameWithType> comme argument, le LOH est nettoyé avec le reste du tas managé.</span><span class="sxs-lookup"><span data-stu-id="125ee-180">If the parameterless <xref:System.GC.Collect?displayProperty=nameWithType> method is called or another overload is passed <xref:System.GC.MaxGeneration?displayProperty=nameWithType> as an argument, the LOH is collected along with the rest of the managed heap.</span></span>

- <span data-ttu-id="125ee-181">Le système est en situation d’insuffisance de mémoire.</span><span class="sxs-lookup"><span data-stu-id="125ee-181">The system is in low memory situation.</span></span>

  <span data-ttu-id="125ee-182">Cela se produit quand le récupérateur de mémoire reçoit une notification de mémoire haute du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="125ee-182">This occurs when the garbage collector receives a high memory notification from the OS.</span></span> <span data-ttu-id="125ee-183">Si le récupérateur de mémoire pense qu’un GC de la génération 2 peut être productif, il le déclenche.</span><span class="sxs-lookup"><span data-stu-id="125ee-183">If the garbage collector thinks that doing a generation 2 GC will be productive, it triggers one.</span></span>

## <a name="loh-performance-implications"></a><span data-ttu-id="125ee-184">Implications sur les performances de LOH</span><span class="sxs-lookup"><span data-stu-id="125ee-184">LOH performance implications</span></span>

<span data-ttu-id="125ee-185">Les allocations sur le tas de grands objets impacte les performances des façons suivantes.</span><span class="sxs-lookup"><span data-stu-id="125ee-185">Allocations on the large object heap impact performance in the following ways.</span></span>

- <span data-ttu-id="125ee-186">Coût d’allocation.</span><span class="sxs-lookup"><span data-stu-id="125ee-186">Allocation cost.</span></span>

  <span data-ttu-id="125ee-187">Le CLR garantit que la mémoire allouée pour chaque nouvel objet est libérée.</span><span class="sxs-lookup"><span data-stu-id="125ee-187">The CLR makes the guarantee that the memory for every new object it gives out is cleared.</span></span> <span data-ttu-id="125ee-188">Cela signifie que le coût d’allocation d’un grand objet est complètement dominé par la libération de la mémoire (sauf s’il déclenche un GC).</span><span class="sxs-lookup"><span data-stu-id="125ee-188">This means the allocation cost of a large object is completely dominated by memory clearing (unless it triggers a GC).</span></span> <span data-ttu-id="125ee-189">S’il faut 2 cycles pour libérer un octet, il faut 170 000 cycles pour libérer le plus petit des grands objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-189">If it takes 2 cycles to clear one byte, it takes 170,000 cycles to clear the smallest large object.</span></span> <span data-ttu-id="125ee-190">Pour libérer la mémoire d’un objet de 16 Mo sur une machine de 2 GHz, il faut environ 16 ms.</span><span class="sxs-lookup"><span data-stu-id="125ee-190">Clearing the memory of a 16MB object on a 2GHz machine takes approximately 16ms.</span></span> <span data-ttu-id="125ee-191">C’est un coût plutôt élevé.</span><span class="sxs-lookup"><span data-stu-id="125ee-191">That's a rather large cost.</span></span>

- <span data-ttu-id="125ee-192">Coût de nettoyage.</span><span class="sxs-lookup"><span data-stu-id="125ee-192">Collection cost.</span></span>

  <span data-ttu-id="125ee-193">Comme le LOH et la génération 2 sont nettoyés ensemble, si le seuil de l’un des deux est dépassé, un nettoyage de la génération 2 est déclenché.</span><span class="sxs-lookup"><span data-stu-id="125ee-193">Because the LOH and generation 2 are collected together, if either one's threshold is exceeded, a generation 2 collection is triggered.</span></span> <span data-ttu-id="125ee-194">Si le nettoyage de la génération 2 est déclenché à cause du LOH, la génération 2 n’est pas forcément plus petite après le GC.</span><span class="sxs-lookup"><span data-stu-id="125ee-194">If a generation 2 collection is triggered because of the LOH, generation 2 won't necessarily be much smaller after the GC.</span></span> <span data-ttu-id="125ee-195">Si la génération 2 n’a pas beaucoup de données, l’impact est minime.</span><span class="sxs-lookup"><span data-stu-id="125ee-195">If there's not much data on generation 2, this has minimal impact.</span></span> <span data-ttu-id="125ee-196">En revanche, si la génération 2 est grande, le nettoyage peut entraîner des problèmes de performances s’il faut déclencher plusieurs GC sur la génération 2.</span><span class="sxs-lookup"><span data-stu-id="125ee-196">But if generation 2 is large, it can cause performance problems if many generation 2 GCs are triggered.</span></span> <span data-ttu-id="125ee-197">Si de nombreux grands objets sont alloués de façon très temporaire et que vous avez un grand SOH, vous risquez de passer trop de temps sur les GC.</span><span class="sxs-lookup"><span data-stu-id="125ee-197">If many large objects are allocated on a very temporary basis and you have a large SOH, you could be spending too much time doing GCs.</span></span> <span data-ttu-id="125ee-198">Par ailleurs, le coût d’allocation vient s’ajouter si vous continuez d’allouer et de libérer de très grands objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-198">In addition, the allocation cost can really add up if you keep allocating and letting go of really large objects.</span></span>

- <span data-ttu-id="125ee-199">Éléments de tableau avec des types référence.</span><span class="sxs-lookup"><span data-stu-id="125ee-199">Array elements with reference types.</span></span>

  <span data-ttu-id="125ee-200">Les très grands objets sur le LOH sont généralement des tableaux (il est très rare d’avoir un objet d’instance très grand).</span><span class="sxs-lookup"><span data-stu-id="125ee-200">Very large objects on the LOH are usually arrays (it's very rare to have an instance object that's really large).</span></span> <span data-ttu-id="125ee-201">Si les éléments d’un tableau ont beaucoup de références, le coût est plus élevé.</span><span class="sxs-lookup"><span data-stu-id="125ee-201">If the elements of an array are reference-rich, it incurs a cost that is not present if the elements are not reference-rich.</span></span> <span data-ttu-id="125ee-202">Si l’élément n’a aucune référence, le récupérateur de mémoire n’a pas besoin de traiter le tableau.</span><span class="sxs-lookup"><span data-stu-id="125ee-202">If the element doesn’t contain any references, the garbage collector doesn’t need to go through the array at all.</span></span> <span data-ttu-id="125ee-203">Par exemple, si vous utilisez un tableau pour stocker des nœuds dans une arborescence binaire, vous pouvez l’implémenter en référençant les nœuds droit et gauche d’un nœud comme étant les nœuds eux-mêmes :</span><span class="sxs-lookup"><span data-stu-id="125ee-203">For example, if you use an array to store nodes in a binary tree, one way to implement it is to refer to a node’s right and left node by the actual nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     Node left;
     Node right;
  };

  Node[] binary_tr = new Node [num_nodes];
  ```

  <span data-ttu-id="125ee-204">Si `num_nodes` est grand, le récupérateur de mémoire doit traiter au moins deux références par élément.</span><span class="sxs-lookup"><span data-stu-id="125ee-204">If `num_nodes` is large, the garbage collector needs to go through at least two references per element.</span></span> <span data-ttu-id="125ee-205">Une autre méthode est de stocker l’index des nœuds droit et gauche :</span><span class="sxs-lookup"><span data-stu-id="125ee-205">An alternative approach is to store the index of the right and the left nodes:</span></span>

  ```csharp
  class Node
  {
     Data d;
     uint left_index;
     uint right_index;
  } ;
  ```

  <span data-ttu-id="125ee-206">Au lieu de référencer les données du nœud gauche comme `left.d`, vous les référencez comme `binary_tr[left_index].d`.</span><span class="sxs-lookup"><span data-stu-id="125ee-206">Instead of referring the left node’s data as `left.d`, you refer to it as `binary_tr[left_index].d`.</span></span> <span data-ttu-id="125ee-207">Ainsi, le récupérateur de mémoire n’a pas besoin d’examiner les références des nœuds gauche et droit.</span><span class="sxs-lookup"><span data-stu-id="125ee-207">And the garbage collector doesn’t need to look at any references for the left and right node.</span></span>

<span data-ttu-id="125ee-208">Des trois facteurs, les deux premiers ont généralement plus d’impact que le troisième.</span><span class="sxs-lookup"><span data-stu-id="125ee-208">Out of the three factors, the first two are usually more significant than the third.</span></span> <span data-ttu-id="125ee-209">Pour cette raison, nous vous recommandons d’allouer un pool de grands objets que vous réutilisez au lieu d’allouer des objets temporaires.</span><span class="sxs-lookup"><span data-stu-id="125ee-209">Because of this, we recommend that you allocate a pool of large objects that you reuse instead of allocating temporary ones.</span></span>

## <a name="collect-performance-data-for-the-loh"></a><span data-ttu-id="125ee-210">Collecter les données de performances du LOH</span><span class="sxs-lookup"><span data-stu-id="125ee-210">Collect performance data for the LOH</span></span>

<span data-ttu-id="125ee-211">Avant de collecter des données de performances pour une zone spécifique, vous devez déjà avoir effectué les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="125ee-211">Before you collect performance data for a specific area, you should already have done the following:</span></span>

1. <span data-ttu-id="125ee-212">Rechercher les raisons d’examiner cette zone.</span><span class="sxs-lookup"><span data-stu-id="125ee-212">Found evidence that you should be looking at this area.</span></span>

2. <span data-ttu-id="125ee-213">Examiner toutes les autres zones connues sans trouver ce qui pourrait expliquer le problème de performances rencontré.</span><span class="sxs-lookup"><span data-stu-id="125ee-213">Exhausted other areas that you know of without finding anything that could explain the performance problem you saw.</span></span>

<span data-ttu-id="125ee-214">Consultez le blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) (Comprendre le problème avant d’essayer de chercher une solution) pour plus d’informations sur les principes fondamentaux de la mémoire et du processeur.</span><span class="sxs-lookup"><span data-stu-id="125ee-214">See the blog [Understand the problem before you try to find a solution](https://devblogs.microsoft.com/dotnet/understand-the-problem-before-you-try-to-find-a-solution/) for more information on the fundamentals of memory and the CPU.</span></span>

<span data-ttu-id="125ee-215">Vous pouvez utiliser les outils suivants pour collecter des données sur les performances du LOH :</span><span class="sxs-lookup"><span data-stu-id="125ee-215">You can use the following tools to collect data on LOH performance:</span></span>

- [<span data-ttu-id="125ee-216">Compteurs de performance pour la mémoire CRL .NET</span><span class="sxs-lookup"><span data-stu-id="125ee-216">.NET CLR memory performance counters</span></span>](#net-clr-memory-performance-counters)

- [<span data-ttu-id="125ee-217">Événements ETW</span><span class="sxs-lookup"><span data-stu-id="125ee-217">ETW events</span></span>](#etw-events)

- [<span data-ttu-id="125ee-218">Débogueur</span><span class="sxs-lookup"><span data-stu-id="125ee-218">A debugger</span></span>](#a-debugger)

### <a name="net-clr-memory-performance-counters"></a><span data-ttu-id="125ee-219">Compteurs de performances pour la mémoire CRL .NET</span><span class="sxs-lookup"><span data-stu-id="125ee-219">.NET CLR Memory Performance counters</span></span>

<span data-ttu-id="125ee-220">Ces compteurs de performances sont une bonne première étape pour rechercher les problèmes de performances (même si nous vous recommandons d’utiliser les [événements ETW](#etw-events)).</span><span class="sxs-lookup"><span data-stu-id="125ee-220">These performance counters are usually a good first step in investigating performance issues (although we recommend that you use [ETW events](#etw-events)).</span></span> <span data-ttu-id="125ee-221">Vous configurez le moniteur de performances en ajoutant les compteurs souhaités, comme le montre la Figure 4.</span><span class="sxs-lookup"><span data-stu-id="125ee-221">You configure Performance Monitor by adding the counters that you want, as Figure 4 shows.</span></span> <span data-ttu-id="125ee-222">Ceux qui sont pertinents pour le LOH sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="125ee-222">The ones that are relevant for the LOH are:</span></span>

- <span data-ttu-id="125ee-223">**Collections de la génération 2**</span><span class="sxs-lookup"><span data-stu-id="125ee-223">**Gen 2 Collections**</span></span>

   <span data-ttu-id="125ee-224">Affiche le nombre d’occurrences de GC de la génération 2 depuis le démarrage du processus.</span><span class="sxs-lookup"><span data-stu-id="125ee-224">Displays the number of times generation 2 GCs have occurred since the process started.</span></span> <span data-ttu-id="125ee-225">Ce compteur est incrémenté à la fin de chaque nettoyage de la génération 2 (aussi appelé nettoyage complet de la mémoire).</span><span class="sxs-lookup"><span data-stu-id="125ee-225">The counter is incremented at the end of a generation 2 collection (also called a full garbage collection).</span></span> <span data-ttu-id="125ee-226">Ce compteur affiche la dernière valeur observée.</span><span class="sxs-lookup"><span data-stu-id="125ee-226">This counter displays the last observed value.</span></span>

- <span data-ttu-id="125ee-227">**Taille du tas d’objets volumineux**</span><span class="sxs-lookup"><span data-stu-id="125ee-227">**Large Object Heap size**</span></span>

   <span data-ttu-id="125ee-228">Affiche la taille actuelle du LOH en octets (y compris l’espace libre).</span><span class="sxs-lookup"><span data-stu-id="125ee-228">Displays the current size, in bytes, including free space, of the LOH.</span></span> <span data-ttu-id="125ee-229">Ce compteur est actualisé à la fin de chaque garbage collection, et non à chaque allocation.</span><span class="sxs-lookup"><span data-stu-id="125ee-229">This counter is updated at the end of a garbage collection, not at each allocation.</span></span>

<span data-ttu-id="125ee-230">En général, vous surveillez les compteurs de performances par le biais du moniteur de performances (PerfMon.exe).</span><span class="sxs-lookup"><span data-stu-id="125ee-230">A common way to look at performance counters is with Performance Monitor (perfmon.exe).</span></span> <span data-ttu-id="125ee-231">Utilisez « Ajouter des compteurs » pour ajouter le compteur de votre choix pour les processus qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="125ee-231">Use “Add Counters” to add the interesting counter for processes that you care about.</span></span> <span data-ttu-id="125ee-232">Vous pouvez enregistrer les données des compteurs de performances dans un fichier journal, comme illustré dans la figure 4 :</span><span class="sxs-lookup"><span data-stu-id="125ee-232">You can save the performance counter data to a log file, as Figure 4 shows:</span></span>

<span data-ttu-id="125ee-233">![Capture d’écran illustrant l’ajout de compteurs de performances.](media/large-object-heap/add-performance-counter.png)</span><span class="sxs-lookup"><span data-stu-id="125ee-233">![Screenshot that shows adding performance counters.](media/large-object-heap/add-performance-counter.png)</span></span>
<span data-ttu-id="125ee-234">Figure 4 : LOH après un GC de la génération 2</span><span class="sxs-lookup"><span data-stu-id="125ee-234">Figure 4: The LOH after a generation 2 GC</span></span>

<span data-ttu-id="125ee-235">Les compteurs de performances peuvent également être interrogés par programmation.</span><span class="sxs-lookup"><span data-stu-id="125ee-235">Performance counters can also be queried programmatically.</span></span> <span data-ttu-id="125ee-236">Beaucoup d’utilisateurs les collectent de cette façon dans le cadre de leur processus de test normal.</span><span class="sxs-lookup"><span data-stu-id="125ee-236">Many people collect them this way as part of their routine testing process.</span></span> <span data-ttu-id="125ee-237">S’ils repèrent des compteurs avec des valeurs anormales, ils utilisent d’autres moyens d’obtenir des données plus détaillées pour les aider dans leurs recherches.</span><span class="sxs-lookup"><span data-stu-id="125ee-237">When they spot counters with values that are out of the ordinary, they use other means to get more detailed data to help with the investigation.</span></span>

> [!NOTE]
> <span data-ttu-id="125ee-238">Nous vous recommandons d’utiliser les événements ETW au lieu des compteurs de performances, car ETW fournit des informations plus détaillées.</span><span class="sxs-lookup"><span data-stu-id="125ee-238">We recommend that you to use ETW events instead of performance counters, because ETW provides much richer information.</span></span>

### <a name="etw-events"></a><span data-ttu-id="125ee-239">Événements ETW</span><span class="sxs-lookup"><span data-stu-id="125ee-239">ETW events</span></span>

<span data-ttu-id="125ee-240">Le récupérateur de mémoire fournit un riche ensemble d’événements ETW pour vous aider à comprendre ce que fait le tas et pourquoi.</span><span class="sxs-lookup"><span data-stu-id="125ee-240">The garbage collector provides a rich set of ETW events to help you understand what the heap is doing and why.</span></span> <span data-ttu-id="125ee-241">Les billets de blog suivants décrivent comment collecter et comprendre les événements GC avec ETW :</span><span class="sxs-lookup"><span data-stu-id="125ee-241">The following blog posts show how to collect and understand GC events with ETW:</span></span>

- [<span data-ttu-id="125ee-242">Événements ETW GC-1</span><span class="sxs-lookup"><span data-stu-id="125ee-242">GC ETW Events - 1</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-1/)

- [<span data-ttu-id="125ee-243">Événements ETW de GC - 2</span><span class="sxs-lookup"><span data-stu-id="125ee-243">GC ETW Events - 2</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-2/)

- [<span data-ttu-id="125ee-244">Événements ETW de GC - 3</span><span class="sxs-lookup"><span data-stu-id="125ee-244">GC ETW Events - 3</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-3/)

- [<span data-ttu-id="125ee-245">Événements ETW de GC - 4</span><span class="sxs-lookup"><span data-stu-id="125ee-245">GC ETW Events - 4</span></span>](https://devblogs.microsoft.com/dotnet/gc-etw-events-4/)

<span data-ttu-id="125ee-246">Pour identifier le nombre excessif de GC de la génération 2 dus à des allocations de LOH temporaires, observez la colonne Raison du déclencheur pour les GC.</span><span class="sxs-lookup"><span data-stu-id="125ee-246">To identify excessive generation 2 GCs caused by temporary LOH allocations, look at the Trigger Reason column for GCs.</span></span> <span data-ttu-id="125ee-247">Pour un test simple qui alloue uniquement des grands objets temporaires, vous pouvez collecter des informations sur les événements ETW avec la ligne de commande [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) suivante :</span><span class="sxs-lookup"><span data-stu-id="125ee-247">For a simple test that only allocates temporary large objects, you can collect information on ETW events with the following [PerfView](https://www.microsoft.com/download/details.aspx?id=28567) command line:</span></span>

```console
perfview /GCCollectOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="125ee-248">Le résultat ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="125ee-248">The result is something like this:</span></span>

<span data-ttu-id="125ee-249">![Capture d’écran montrant les événements ETW dans PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span><span class="sxs-lookup"><span data-stu-id="125ee-249">![Screenshot that shows ETW events in PerfView.](media/large-object-heap/event-tracing-windows-perfview.png)</span></span>
<span data-ttu-id="125ee-250">Figure 5 : Événements ETW affichés à l’aide de PerfView</span><span class="sxs-lookup"><span data-stu-id="125ee-250">Figure 5: ETW events shown using PerfView</span></span>

<span data-ttu-id="125ee-251">Comme vous pouvez le voir, tous les GC sont effectués sur la génération 2 et ils sont déclenchés par AllocLarge, ce qui signifie que c’est l’allocation d’un grand objet qui a déclenché ce GC.</span><span class="sxs-lookup"><span data-stu-id="125ee-251">As you can see, all GCs are generation 2 GCs, and they are all triggered by AllocLarge, which means that allocating a large object triggered this GC.</span></span> <span data-ttu-id="125ee-252">Nous savons que ces allocations sont temporaires parce que la colonne **% de taux de survie LOH** indique 1 %.</span><span class="sxs-lookup"><span data-stu-id="125ee-252">We know that these allocations are temporary because the **LOH Survival Rate %** column says 1%.</span></span>

<span data-ttu-id="125ee-253">Vous pouvez collecter d’autres événements ETW qui vous indiquent qui a alloué ces grands objets.</span><span class="sxs-lookup"><span data-stu-id="125ee-253">You can collect additional ETW events that tell you who allocated these large objects.</span></span> <span data-ttu-id="125ee-254">La ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="125ee-254">The following command line:</span></span>

```console
perfview /GCOnly /AcceptEULA /nogui collect
```

<span data-ttu-id="125ee-255">collecte un événement AllocationTick qui est déclenché toutes les 100 000 allocations environ.</span><span class="sxs-lookup"><span data-stu-id="125ee-255">collects an AllocationTick event which is fired approximately every 100k worth of allocations.</span></span> <span data-ttu-id="125ee-256">En d’autres termes, un événement est déclenché chaque fois qu’un grand objet est alloué.</span><span class="sxs-lookup"><span data-stu-id="125ee-256">In other words, an event is fired each time a large object is allocated.</span></span> <span data-ttu-id="125ee-257">Vous pouvez alors examiner une des vues d’allocation de tas du récupérateur de mémoire qui indique les pile d’appels qui ont alloué des grands objets :</span><span class="sxs-lookup"><span data-stu-id="125ee-257">You can then look at one of the GC Heap Alloc views which show you the callstacks that allocated large objects:</span></span>

<span data-ttu-id="125ee-258">![Capture d’écran montrant une vue du tas garbage collector.](media/large-object-heap/garbage-collector-heap.png)</span><span class="sxs-lookup"><span data-stu-id="125ee-258">![Screenshot that shows a garbage collector heap view.](media/large-object-heap/garbage-collector-heap.png)</span></span>
<span data-ttu-id="125ee-259">Figure 6 : Une vue d’allocation de tas du récupérateur de mémoire</span><span class="sxs-lookup"><span data-stu-id="125ee-259">Figure 6: A GC Heap Alloc view</span></span>

<span data-ttu-id="125ee-260">Comme vous pouvez le voir, il s’agit d’un test très simple qui alloue simplement de grands objets à partir de sa méthode `Main`.</span><span class="sxs-lookup"><span data-stu-id="125ee-260">As you can see, this is a very simple test that just allocates large objects from its `Main` method.</span></span>

### <a name="a-debugger"></a><span data-ttu-id="125ee-261">Débogueur</span><span class="sxs-lookup"><span data-stu-id="125ee-261">A debugger</span></span>

<span data-ttu-id="125ee-262">Si tout ce que vous avez est un vidage de mémoire et que vous devez examiner les objets qui se trouvent sur le LOH, vous pouvez utiliser [l’extension de débogueur SoS](../../framework/tools/sos-dll-sos-debugging-extension.md) fournie par .NET.</span><span class="sxs-lookup"><span data-stu-id="125ee-262">If all you have is a memory dump and you need to look at what objects are actually on the LOH, you can use the [SoS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) provided by .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="125ee-263">Les commandes de débogage indiquées dans cette section sont applicables aux [débogueurs Windows](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span><span class="sxs-lookup"><span data-stu-id="125ee-263">The debugging commands mentioned in this section are applicable to the [Windows Debuggers](https://www.microsoft.com/whdc/devtools/debugging/default.mspx).</span></span>

<span data-ttu-id="125ee-264">Le code suivant illustre un exemple de sortie de l’analyse du LOH :</span><span class="sxs-lookup"><span data-stu-id="125ee-264">The following shows sample output from analyzing the LOH:</span></span>

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

<span data-ttu-id="125ee-265">La taille du tas LOH est (16 754 224 + 16 699 288 + 16 284 504) = 49 738 016 octets.</span><span class="sxs-lookup"><span data-stu-id="125ee-265">The LOH heap size is (16,754,224 + 16,699,288 + 16,284,504) = 49,738,016 bytes.</span></span> <span data-ttu-id="125ee-266">Entre les adresses 023e1000 et 033db630, 8 008 736 octets sont occupés par un tableau d’objets <xref:System.Object?displayProperty=nameWithType>, 6 663 696 octets sont occupés par un tableau d’objets <xref:System.Byte?displayProperty=nameWithType> et 2 081 792 octets sont occupés par de l’espace libre.</span><span class="sxs-lookup"><span data-stu-id="125ee-266">Between addresses 023e1000 and 033db630, 8,008,736 bytes are occupied by an array of <xref:System.Object?displayProperty=nameWithType> objects, 6,663,696 bytes are occupied by an array of <xref:System.Byte?displayProperty=nameWithType>  objects, and 2,081,792 bytes are occupied by free space.</span></span>

<span data-ttu-id="125ee-267">Parfois, le débogueur montre que la taille totale du LOH est inférieure à 85 000 octets.</span><span class="sxs-lookup"><span data-stu-id="125ee-267">Sometimes, the debugger shows that the total size of the LOH is less than 85,000 bytes.</span></span> <span data-ttu-id="125ee-268">C’est parce que le runtime lui-même utilise le LOH pour allouer des objets dont la taille est inférieure à celle d’un grand objet.</span><span class="sxs-lookup"><span data-stu-id="125ee-268">This happens because the runtime itself uses the LOH to allocate some objects that are smaller than a large object.</span></span>

<span data-ttu-id="125ee-269">Comme le LOH n’est pas compacté, il est parfois perçu comme la source de la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="125ee-269">Because the LOH is not compacted, sometimes the LOH is thought to be the source of fragmentation.</span></span> <span data-ttu-id="125ee-270">Une fragmentation peut désigner :</span><span class="sxs-lookup"><span data-stu-id="125ee-270">Fragmentation means:</span></span>

- <span data-ttu-id="125ee-271">La fragmentation du tas managé, indiquée par la quantité d’espace libre entre les objets managés.</span><span class="sxs-lookup"><span data-stu-id="125ee-271">Fragmentation of the managed heap, which is indicated by the amount of free space between managed objects.</span></span> <span data-ttu-id="125ee-272">Dans SoS, la commande `!dumpheap –type Free` affiche la quantité d’espace libre entre les objets managés.</span><span class="sxs-lookup"><span data-stu-id="125ee-272">In SoS, the `!dumpheap –type Free` command displays the amount of free space between managed objects.</span></span>

- <span data-ttu-id="125ee-273">La fragmentation de l’espace d’adressage de mémoire virtuelle, qui est la mémoire marquée comme `MEM_FREE`.</span><span class="sxs-lookup"><span data-stu-id="125ee-273">Fragmentation of the virtual memory (VM) address space, which is the memory marked as `MEM_FREE`.</span></span> <span data-ttu-id="125ee-274">Vous pouvez l’obtenir à l’aide de diverses commandes de débogueur dans windbg.</span><span class="sxs-lookup"><span data-stu-id="125ee-274">You can get it by using various debugger commands in windbg.</span></span>

   <span data-ttu-id="125ee-275">L’exemple suivant montre une fragmentation dans l’espace de mémoire virtuelle :</span><span class="sxs-lookup"><span data-stu-id="125ee-275">The following example shows fragmentation in the VM space:</span></span>

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

<span data-ttu-id="125ee-276">Souvent, la fragmentation de mémoire virtuelle est causée par des grands objets temporaires qui obligent le récupérateur de mémoire à fréquemment acquérir de nouveaux segments de tas managé du système d’exploitation et lui en rendre des vides.</span><span class="sxs-lookup"><span data-stu-id="125ee-276">It’s more common to see VM fragmentation caused by temporary large objects that require the garbage collector to frequently acquire new managed heap segments from the OS and to release empty ones back to the OS.</span></span>

<span data-ttu-id="125ee-277">Pour vérifier si le LOH provoque une fragmentation de mémoire virtuelle, vous pouvez définir un point d’arrêt sur [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) et [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) et voir qui les appelle.</span><span class="sxs-lookup"><span data-stu-id="125ee-277">To verify whether the LOH is causing VM fragmentation, you can set a breakpoint on [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) and [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) to see who call them.</span></span> <span data-ttu-id="125ee-278">Par exemple, pour voir qui a essayé d’allouer des blocs de mémoire virtuelle de système d’exploitation supérieurs à 8 Mo, vous pouvez définir un point d’arrêt de la façon suivante :</span><span class="sxs-lookup"><span data-stu-id="125ee-278">For example, to see who tried to allocate virtual memory chunks larger than 8MBB from the OS, you can set a breakpoint like this:</span></span>

```console
bp kernel32!virtualalloc "j (dwo(@esp+8)>800000) 'kb';'g'"
```

<span data-ttu-id="125ee-279">Cette commande s’arrête dans le débogueur et affiche la pile des appels uniquement si [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) est appelé avec une taille d’allocation supérieure à 8 Mo (0x800000).</span><span class="sxs-lookup"><span data-stu-id="125ee-279">This command breaks into the debugger and shows the call stack only if [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) is called with an allocation size greater than 8MB (0x800000).</span></span>

<span data-ttu-id="125ee-280">CLR 2.0 a ajouté une fonctionnalité appelée *VM Hoarding* (Réserve de mémoire virtuelle) qui peut être utile dans les scénarios où des segments (y compris ceux des tas de petits et grands objets) sont fréquemment acquis et libérés.</span><span class="sxs-lookup"><span data-stu-id="125ee-280">CLR 2.0 added a feature called *VM Hoarding* that can be useful for scenarios where segments (including on the large and small object heaps) are frequently acquired and released.</span></span> <span data-ttu-id="125ee-281">Pour utiliser la fonctionnalité VM Hoarding, vous spécifiez un indicateur de démarrage appelé `STARTUP_HOARD_GC_VM` via l’API d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="125ee-281">To specify VM Hoarding, you specify a startup flag called `STARTUP_HOARD_GC_VM` via the hosting API.</span></span> <span data-ttu-id="125ee-282">Au lieu de renvoyer des segments vides au système d’exploitation, le CLR annule la réservation de mémoire sur ces segments et les met sur liste d’attente.</span><span class="sxs-lookup"><span data-stu-id="125ee-282">Instead of releasing empty segments back to the OS, the CLR decommits the memory on these segments and puts them on a standby list.</span></span> <span data-ttu-id="125ee-283">(Notez que le CLR ne le fait pas pour les segments trop grands.) Le CLR utilise ensuite ces segments pour répondre aux nouvelles demandes de segment.</span><span class="sxs-lookup"><span data-stu-id="125ee-283">(Note that the CLR doesn't do this for segments that are too large.) The CLR later uses those segments to satisfy new segment requests.</span></span> <span data-ttu-id="125ee-284">La prochaine fois que votre application a besoin d’un nouveau segment, le CLR en utilise un de cette liste d’attente, s’il est assez grand.</span><span class="sxs-lookup"><span data-stu-id="125ee-284">The next time that your app needs a new segment, the CLR uses one from this standby list if it can find one that’s big enough.</span></span>

<span data-ttu-id="125ee-285">Les Hoarding d’ordinateur virtuel sont également utiles pour les applications qui souhaitent tenir sur les segments qu’ils ont déjà acquis, par exemple certaines applications serveur qui sont des applications dominantes s’exécutant sur le système, afin d’éviter les exceptions de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="125ee-285">VM hoarding is also useful for applications that want to hold onto the segments that they already acquired, such as some server apps that are the dominant apps running on the system, to avoid out-of-memory exceptions.</span></span>

<span data-ttu-id="125ee-286">Nous vous recommandons vivement de tester soigneusement votre application quand vous utilisez cette fonctionnalité, pour vérifier qu’elle utilise la mémoire de façon suffisamment stable.</span><span class="sxs-lookup"><span data-stu-id="125ee-286">We strongly recommend that you carefully test your application when you use this feature to ensure your application has fairly stable memory usage.</span></span>

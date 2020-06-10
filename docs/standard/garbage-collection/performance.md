---
title: Garbage Collection et niveau de performance
description: En savoir plus sur les problèmes liés à l’utilisation de la garbage collection et de la mémoire. Apprenez à réduire l’effet de garbage collection sur vos applications.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: dee5a4b54806bdadc18d759c5df7016da060fd75
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662847"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="e69fe-104">Garbage Collection et niveau de performance</span><span class="sxs-lookup"><span data-stu-id="e69fe-104">Garbage Collection and Performance</span></span>

<span data-ttu-id="e69fe-105">Cette rubrique décrit les problèmes liés au garbage collection et à l’utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-105">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="e69fe-106">Elle apporte des solutions aux problèmes concernant les tas managés et explique comment réduire l’effet du garbage collection sur vos applications.</span><span class="sxs-lookup"><span data-stu-id="e69fe-106">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="e69fe-107">Chaque problème contient des liens vers des procédures à suivre pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="e69fe-107">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="e69fe-108">Outils d'analyse des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-108">Performance Analysis Tools</span></span>

<span data-ttu-id="e69fe-109">Les sections suivantes décrivent les outils disponibles pour analyser les problèmes liés à l’utilisation de la mémoire et au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-109">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="e69fe-110">Les [procédures](#performance-check-procedures) fournies plus loin dans cette rubrique font référence à ces outils.</span><span class="sxs-lookup"><span data-stu-id="e69fe-110">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="e69fe-111">Compteurs de performance mémoire</span><span class="sxs-lookup"><span data-stu-id="e69fe-111">Memory Performance Counters</span></span>

<span data-ttu-id="e69fe-112">Vous pouvez utiliser les compteurs de performances pour collecter des données sur les performances.</span><span class="sxs-lookup"><span data-stu-id="e69fe-112">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="e69fe-113">Pour obtenir des instructions, voir [Génération de profils d'exécution](../../framework/debug-trace-profile/runtime-profiling.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-113">For instructions, see [Runtime Profiling](../../framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="e69fe-114">La catégorie Mémoire CLR .NET des compteurs de performances, telle qu'elle est décrite dans [Compteurs de performances dans le .NET Framework](../../framework/debug-trace-profile/performance-counters.md), fournit des informations sur le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="e69fe-114">The .NET CLR Memory category of performance counters, as described in [Performance Counters in the .NET Framework](../../framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="e69fe-115">Débogage avec l'extension SOS</span><span class="sxs-lookup"><span data-stu-id="e69fe-115">Debugging with SOS</span></span>

<span data-ttu-id="e69fe-116">Vous pouvez utiliser le [Débogueur Windows (WinDbg)](/windows-hardware/drivers/debugger/index) pour inspecter les objets du tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-116">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="e69fe-117">Pour installer WinDbg, installez les outils de débogage pour Windows à partir de la page [Outils de débogage pour Windows](/windows-hardware/drivers/debugger/debugger-download-tools).</span><span class="sxs-lookup"><span data-stu-id="e69fe-117">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="e69fe-118">Événements ETW de garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-118">Garbage Collection ETW Events</span></span>

<span data-ttu-id="e69fe-119">Le suivi d'événements pour Windows (ETW) est un système de suivi qui complète la prise en charge du profilage et du débogage fournie par .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e69fe-119">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by the .NET Framework.</span></span> <span data-ttu-id="e69fe-120">À compter de .NET Framework 4, les [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md) capturent des informations utiles pour l’analyse du tas managé d’un point de vue statistique.</span><span class="sxs-lookup"><span data-stu-id="e69fe-120">Starting with the .NET Framework 4, [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="e69fe-121">Par exemple, l'événement `GCStart_V1`, qui est déclenché quand un garbage collection est sur le point de se produire, fournit les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e69fe-121">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="e69fe-122">La génération d'objets qui est collectée</span><span class="sxs-lookup"><span data-stu-id="e69fe-122">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="e69fe-123">Ce qui a déclenché le garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-123">What triggered the garbage collection.</span></span>

- <span data-ttu-id="e69fe-124">Le type de garbage collection (simultané ou non simultané)</span><span class="sxs-lookup"><span data-stu-id="e69fe-124">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="e69fe-125">La journalisation des événements ETW est efficace et ne masque pas les problèmes de performances liés au garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-125">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="e69fe-126">Un processus peut fournir ses propres événements conjointement aux événements ETW.</span><span class="sxs-lookup"><span data-stu-id="e69fe-126">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="e69fe-127">Quand ils sont journalisés, les événements d'application et les événements de garbage collection peuvent être corrélés pour déterminer quand et comment les problèmes de tas se produisent.</span><span class="sxs-lookup"><span data-stu-id="e69fe-127">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="e69fe-128">Par exemple, une application serveur peut fournir des événements au début et à la fin d'une demande client.</span><span class="sxs-lookup"><span data-stu-id="e69fe-128">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="e69fe-129">L'API de profilage</span><span class="sxs-lookup"><span data-stu-id="e69fe-129">The Profiling API</span></span>

<span data-ttu-id="e69fe-130">Les interfaces de profilage du common language runtime (CLR) fournissent des informations détaillées sur les objets qui ont été affectés pendant le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-130">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="e69fe-131">Un profileur peut être informé quand un garbage collection commence et se termine.</span><span class="sxs-lookup"><span data-stu-id="e69fe-131">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="e69fe-132">Il peut fournir des rapports sur les objets du tas managé, y compris une identification des objets au cours de chaque génération.</span><span class="sxs-lookup"><span data-stu-id="e69fe-132">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="e69fe-133">Pour plus d'informations, voir [Vue d'ensemble du profilage](../../framework/unmanaged-api/profiling/profiling-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-133">For more information, see [Profiling Overview](../../framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="e69fe-134">Les profileurs peuvent fournir des informations complètes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-134">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="e69fe-135">Toutefois, les profileurs complexes peuvent potentiellement modifier le comportement d'une application.</span><span class="sxs-lookup"><span data-stu-id="e69fe-135">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="e69fe-136">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="e69fe-136">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="e69fe-137">À compter de .NET Framework 4, l’outil ARM (Application Domain Resource Monitoring) permet aux hôtes de superviser l’utilisation du processeur et de la mémoire par domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="e69fe-137">Starting with the .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="e69fe-138">Pour plus d'informations, voir [Analyse de ressource de domaine d'application](app-domain-resource-monitoring.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-138">For more information, see [Application Domain Resource Monitoring](app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="e69fe-139">Résolution des problèmes de performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-139">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="e69fe-140">La première étape consiste à [déterminer si le problème est effectivement lié au garbage collection](#IsGC).</span><span class="sxs-lookup"><span data-stu-id="e69fe-140">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="e69fe-141">Si c'est le cas, cliquez sur l'un des liens suivants pour résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="e69fe-141">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="e69fe-142">Une exception de mémoire insuffisante est levée</span><span class="sxs-lookup"><span data-stu-id="e69fe-142">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="e69fe-143">Le processus utilise trop de mémoire</span><span class="sxs-lookup"><span data-stu-id="e69fe-143">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="e69fe-144">Le garbage collector ne récupère pas les objets suffisamment rapidement</span><span class="sxs-lookup"><span data-stu-id="e69fe-144">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="e69fe-145">Le tas managé est trop fragmenté</span><span class="sxs-lookup"><span data-stu-id="e69fe-145">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="e69fe-146">Les pauses du nettoyage de la mémoire sont trop longues</span><span class="sxs-lookup"><span data-stu-id="e69fe-146">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="e69fe-147">La génération 0 est trop volumineuse</span><span class="sxs-lookup"><span data-stu-id="e69fe-147">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="e69fe-148">L’utilisation du processeur pendant une garbage collection est trop élevée</span><span class="sxs-lookup"><span data-stu-id="e69fe-148">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="e69fe-149">Problème : une exception de mémoire insuffisante est levée</span><span class="sxs-lookup"><span data-stu-id="e69fe-149">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="e69fe-150">Il existe deux cas légitimes pour la levée d'une <xref:System.OutOfMemoryException> managée :</span><span class="sxs-lookup"><span data-stu-id="e69fe-150">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="e69fe-151">Une mémoire virtuelle insuffisante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-151">Running out of virtual memory.</span></span>

  <span data-ttu-id="e69fe-152">Le garbage collector alloue la mémoire depuis le système en segments d'une taille prédéterminée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-152">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="e69fe-153">Si une allocation requiert un segment supplémentaire, mais qu'il n'existe aucun bloc contigu libre dans l'espace de mémoire virtuelle du processus, l'allocation du tas managé échoue.</span><span class="sxs-lookup"><span data-stu-id="e69fe-153">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="e69fe-154">Ne pas avoir suffisamment de mémoire physique à allouer.</span><span class="sxs-lookup"><span data-stu-id="e69fe-154">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="e69fe-155">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-155">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-156">Déterminez si l’exception de mémoire insuffisante est gérée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-156">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="e69fe-157">Identifiez la quantité de mémoire virtuelle pouvant être réservée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-157">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="e69fe-158">Déterminez si la mémoire physique est suffisante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-158">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="e69fe-159">Si vous déterminez que l'exception n'est pas légitime, contactez le support technique Microsoft et préparez-vous à fournir les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="e69fe-159">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="e69fe-160">La pile où a été levée l'exception d'insuffisance de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-160">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="e69fe-161">Le fichier complet de vidage mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-161">Full memory dump.</span></span>

- <span data-ttu-id="e69fe-162">Les données qui prouvent qu'il ne s'agit pas d'une exception de mémoire insuffisante légitime, y compris les données indiquant que ni la mémoire virtuelle ni la mémoire physique ne posent un problème.</span><span class="sxs-lookup"><span data-stu-id="e69fe-162">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="e69fe-163">Problème : le processus utilise trop de mémoire</span><span class="sxs-lookup"><span data-stu-id="e69fe-163">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="e69fe-164">On suppose souvent que l’utilisation de la mémoire qui s’affiche sous l’onglet **Performances** du Gestionnaire des tâches Windows peut indiquer à l’utilisateur que trop de mémoire est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-164">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="e69fe-165">Toutefois, cet affichage concerne le jeu de travail et ne fournit pas d'informations sur l'utilisation de la mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="e69fe-165">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="e69fe-166">Si vous déterminez que le problème est provoqué par le tas managé, vous devez examiner le tas managé dans le temps pour déterminer les éventuels schémas récurrents.</span><span class="sxs-lookup"><span data-stu-id="e69fe-166">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="e69fe-167">Si vous déterminez que le problème n'est pas provoqué par le tas managé, vous devez utiliser le débogage natif.</span><span class="sxs-lookup"><span data-stu-id="e69fe-167">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="e69fe-168">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-168">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-169">Identifiez la quantité de mémoire virtuelle pouvant être réservée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-169">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="e69fe-170">Identifiez la quantité de mémoire validée par le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-170">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="e69fe-171">Identifiez la quantité de mémoire réservée par le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-171">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="e69fe-172">Identifiez les objets volumineux dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-172">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="e69fe-173">Identifiez les références aux objets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-173">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="e69fe-174">Problème : le garbage collector ne récupère pas les objets suffisamment rapidement</span><span class="sxs-lookup"><span data-stu-id="e69fe-174">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="e69fe-175">Quand les objets semblent ne pas être récupérés comme prévu pour le garbage collection, vous devez déterminer s'il existe des références solides à ces objets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-175">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="e69fe-176">Vous pouvez également rencontrer ce problème si aucun garbage collection n'a eu lieu pour la génération qui contient un objet mort, ce qui indique que le finaliseur de l'objet mort n'a pas été exécuté.</span><span class="sxs-lookup"><span data-stu-id="e69fe-176">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="e69fe-177">Par exemple, ceci est possible quand vous exécutez une application à thread unique cloisonné (STA) et que le thread qui gère la file d'attente du finaliseur ne peut pas appeler depuis celle-ci.</span><span class="sxs-lookup"><span data-stu-id="e69fe-177">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="e69fe-178">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-178">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-179">Vérifiez les références aux objets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-179">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="e69fe-180">Déterminez si un finaliseur a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="e69fe-180">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="e69fe-181">Déterminez s’il y a des objets en attente de finalisation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-181">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="e69fe-182">Problème : le tas managé est trop fragmenté</span><span class="sxs-lookup"><span data-stu-id="e69fe-182">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="e69fe-183">Le niveau de fragmentation est calculé comme le rapport entre l'espace libre et le total de la mémoire allouée pour la génération.</span><span class="sxs-lookup"><span data-stu-id="e69fe-183">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="e69fe-184">Pour la génération 2, un niveau acceptable de fragmentation ne doit pas dépasser 20 %.</span><span class="sxs-lookup"><span data-stu-id="e69fe-184">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="e69fe-185">Étant donné que la génération 2 peut devenir très volumineuse, le taux de fragmentation est plus important que la valeur absolue.</span><span class="sxs-lookup"><span data-stu-id="e69fe-185">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="e69fe-186">L'espace libre n'est pas une préoccupation pour la génération 0, car il s'agit de la génération où les nouveaux objets sont alloués.</span><span class="sxs-lookup"><span data-stu-id="e69fe-186">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="e69fe-187">La fragmentation se produit toujours dans le tas des objets volumineux, car il n'est pas compacté.</span><span class="sxs-lookup"><span data-stu-id="e69fe-187">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="e69fe-188">Les objets libres qui sont adjacents sont réduits naturellement dans un même espace pour répondre aux requêtes d'allocation des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="e69fe-188">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="e69fe-189">La fragmentation peut devenir un problème avec la génération 1 et la génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-189">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="e69fe-190">Si ces générations disposent d'une grande quantité d'espace libre après un garbage collection, l'utilisation des objets d'une application peut nécessiter des modifications et vous devrez envisager de réévaluer la durée de vie des objets à long terme.</span><span class="sxs-lookup"><span data-stu-id="e69fe-190">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="e69fe-191">L'épinglage excessif d'objets peut augmenter la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-191">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="e69fe-192">Si la fragmentation est élevée, un trop grand nombre d’objets a pu être épinglé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-192">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="e69fe-193">Si la fragmentation de la mémoire virtuelle empêche le garbage collector d'ajouter des segments, la cause peut se trouver dans la liste ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="e69fe-193">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="e69fe-194">Le chargement et le déchargement fréquents de nombreux petits assemblys.</span><span class="sxs-lookup"><span data-stu-id="e69fe-194">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="e69fe-195">Des références trop nombreuses à des objets COM en cas d'interopérabilité avec du code non managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-195">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="e69fe-196">La création d'objets transitoires volumineux, ce qui entraîne l'allocation et la libération fréquentes de segments par le tas des objets volumineux.</span><span class="sxs-lookup"><span data-stu-id="e69fe-196">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="e69fe-197">Lors de l'hébergement du CLR, une application peut demander que le garbage collector conserve ses segments.</span><span class="sxs-lookup"><span data-stu-id="e69fe-197">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="e69fe-198">Cela réduit la fréquence des allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="e69fe-198">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="e69fe-199">Pour cela, utilisez la balise STARTUP_HOARD_GC_VM dans l'[énumération STARTUP_FLAGS](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-199">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="e69fe-200">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-200">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-201">Identifiez la quantité d’espace libre dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-201">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="e69fe-202">Identifiez le nombre d’objets épinglés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-202">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="e69fe-203">Si vous pensez qu'il n'existe aucune cause légitime à la fragmentation, contactez le support technique Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e69fe-203">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="e69fe-204">Problème : les pauses du garbage collection sont trop longues</span><span class="sxs-lookup"><span data-stu-id="e69fe-204">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="e69fe-205">Le garbage collection fonctionne en temps réel souple. Les applications doivent donc être en mesure de tolérer quelques pauses.</span><span class="sxs-lookup"><span data-stu-id="e69fe-205">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="e69fe-206">L'un des critères du temps réel souple est que 95 % des opérations doivent se terminer à temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-206">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="e69fe-207">Avec le garbage collection simultané, les threads managés sont autorisés à s'exécuter pendant une collection, ce qui signifie que les pauses sont très minimes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-207">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="e69fe-208">Les garbage collection éphémères (générations 0 et 1) ne durent que quelques millisecondes. La réduction du temps de pause n'est donc généralement pas possible.</span><span class="sxs-lookup"><span data-stu-id="e69fe-208">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="e69fe-209">Toutefois, vous pouvez réduire les temps de pause des collections de génération 2 en modifiant le modèle des demandes d’allocation effectuées par une application.</span><span class="sxs-lookup"><span data-stu-id="e69fe-209">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="e69fe-210">Une autre méthode plus précise est celle qui consiste à utiliser les [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-210">Another, more accurate, method is to use [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="e69fe-211">Vous pouvez rechercher le minutage des collections en ajoutant les différences de timestamp pour une séquence d’événements.</span><span class="sxs-lookup"><span data-stu-id="e69fe-211">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="e69fe-212">L’intégralité de la séquence de collection inclut la suspension du moteur d’exécution, le garbage collection proprement dit et la reprise du moteur d’exécution.</span><span class="sxs-lookup"><span data-stu-id="e69fe-212">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="e69fe-213">Vous pouvez utiliser les [notifications de garbage collection](notifications.md) pour déterminer si un serveur est sur le point de disposer d’une collection de génération 2, et si la redirection des demandes vers un autre serveur peut atténuer les problèmes liés aux pauses.</span><span class="sxs-lookup"><span data-stu-id="e69fe-213">You can use [Garbage Collection Notifications](notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="e69fe-214">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-214">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-215">Identifiez la durée d’un nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-215">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="e69fe-216">Déterminez ce qui a provoqué un nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-216">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="e69fe-217">Problème : la génération 0 est trop volumineuse</span><span class="sxs-lookup"><span data-stu-id="e69fe-217">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="e69fe-218">La génération 0 est susceptible de contenir un plus grand nombre d'objets sur un système 64 bits, notamment si vous utilisez le garbage collection pour serveur au lieu du garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="e69fe-218">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="e69fe-219">En effet, le seuil auquel se déclenche un garbage collection de génération 0 est plus élevé dans ces environnements, et les collections de génération 0 peuvent donc être beaucoup plus volumineuses.</span><span class="sxs-lookup"><span data-stu-id="e69fe-219">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="e69fe-220">Les performances sont améliorées quand une application alloue plus de mémoire avant qu'un garbage collection ne soit déclenché.</span><span class="sxs-lookup"><span data-stu-id="e69fe-220">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="e69fe-221">Problème : l'utilisation du processeur pendant un garbage collection est trop élevée</span><span class="sxs-lookup"><span data-stu-id="e69fe-221">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="e69fe-222">L'utilisation du processeur est élevée pendant les garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-222">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="e69fe-223">Si un temps de processus suffisant est consacré à un garbage collection, les collections seront trop fréquent ou la collection durera trop longtemps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-223">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="e69fe-224">Un taux d'allocation d'objets plus élevé sur le tas managé entraîne des garbage collection plus fréquents.</span><span class="sxs-lookup"><span data-stu-id="e69fe-224">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="e69fe-225">La diminution du taux d'allocation réduit la fréquence des garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-225">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="e69fe-226">Vous pouvez surveiller les taux d'allocation à l'aide du compteur de performances `Allocated Bytes/second`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-226">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="e69fe-227">Pour plus d'informations, voir [Compteurs de performance dans le .NET Framework](../../framework/debug-trace-profile/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="e69fe-227">For more information, see [Performance Counters in the .NET Framework](../../framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="e69fe-228">La durée d’une collection est principalement un facteur du nombre d’objets qui survivent après l’allocation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-228">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="e69fe-229">Le garbage collector devra parcourir une grande quantité de mémoire si de nombreux objets restent à collecter.</span><span class="sxs-lookup"><span data-stu-id="e69fe-229">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="e69fe-230">Le travail qui consiste à compacter les survivants prend beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-230">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="e69fe-231">Pour déterminer le nombre d'objets traités au cours d'une collection, définissez un point d'arrêt dans le débogueur à la fin d'un garbage collection pour une génération spécifique.</span><span class="sxs-lookup"><span data-stu-id="e69fe-231">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="e69fe-232">Contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-232">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="e69fe-233">Déterminez si l’utilisation élevée du processeur est provoquée par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-233">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="e69fe-234">Définissez un point d’arrêt à la fin du nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-234">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="e69fe-235">Instructions de dépannage</span><span class="sxs-lookup"><span data-stu-id="e69fe-235">Troubleshooting Guidelines</span></span>

<span data-ttu-id="e69fe-236">Cette section comporte les instructions que vous devez prendre en compte avant de commencer vos recherches.</span><span class="sxs-lookup"><span data-stu-id="e69fe-236">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="e69fe-237">Garbage collection pour station de travail et pour serveur</span><span class="sxs-lookup"><span data-stu-id="e69fe-237">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="e69fe-238">Déterminez si vous utilisez le type de garbage collection qui convient.</span><span class="sxs-lookup"><span data-stu-id="e69fe-238">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="e69fe-239">Si votre application utilise plusieurs threads et instances d'objet, utilisez le garbage collection pour serveur au lieu du garbage collection pour station de travail.</span><span class="sxs-lookup"><span data-stu-id="e69fe-239">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="e69fe-240">Le garbage collection pour serveur traite plusieurs threads, tandis que le garbage collection pour station de travail nécessite que plusieurs instances d'une application exécutent leurs propres threads de garbage collection et soient en concurrence pour le temps processeur.</span><span class="sxs-lookup"><span data-stu-id="e69fe-240">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="e69fe-241">Une application qui possède une faible charge et qui n'effectue que rarement des tâches en arrière-plan, telles qu'un service, peut utiliser le garbage collection pour station de travail en désactivant le garbage collection simultané.</span><span class="sxs-lookup"><span data-stu-id="e69fe-241">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="e69fe-242">Quand mesurer la taille du tas managé</span><span class="sxs-lookup"><span data-stu-id="e69fe-242">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="e69fe-243">Sauf si vous utilisez un profileur, vous devrez établir un modèle cohérent de mesure pour diagnostiquer efficacement les problèmes de performances.</span><span class="sxs-lookup"><span data-stu-id="e69fe-243">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="e69fe-244">Prenez en compte les points suivants pour établir une planification :</span><span class="sxs-lookup"><span data-stu-id="e69fe-244">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="e69fe-245">Si vous effectuez la mesure après un garbage collection de génération 2, le tas managé ne contiendra aucun objet mort.</span><span class="sxs-lookup"><span data-stu-id="e69fe-245">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="e69fe-246">Si vous effectuez la mesure immédiatement après un garbage collection de génération 0, les objets de génération 1 et 2 n'auront pas encore été collectés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-246">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="e69fe-247">Si vous effectuez la mesure immédiatement avant un garbage collection, vous mesurerez autant de l'allocation que possible avant le démarrage du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-247">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="e69fe-248">Effectuer une mesure pendant un garbage collection pose problème, car l'état des structures de données du garbage collector n'est pas valide pour la traversée et les résultats obtenus peuvent ne pas être complets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-248">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="e69fe-249">C'est la procédure normale.</span><span class="sxs-lookup"><span data-stu-id="e69fe-249">This is by design.</span></span>

- <span data-ttu-id="e69fe-250">Quand utilisez le garbage collection pour station de travail avec le garbage collection simultané, les objets récupérés ne sont pas compactés, donc la taille du tas peut être identique voire supérieure (la fragmentation peut le faire apparaître plus volumineux).</span><span class="sxs-lookup"><span data-stu-id="e69fe-250">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="e69fe-251">Le garbage collection simultané sur la génération 2 est différé quand la charge de mémoire physique est trop élevée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-251">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="e69fe-252">La procédure suivante décrit comment définir un point d'arrêt pour mesurer le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-252">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="e69fe-253">Pour définir un point d'arrêt à la fin du garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-253">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="e69fe-254">Dans le débogueur WinDbg, après avoir chargé l’extension SOS, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-254">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="e69fe-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) ’kb’;’g’"**</span><span class="sxs-lookup"><span data-stu-id="e69fe-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="e69fe-256">où **GcCondemnedGeneration** est défini sur la génération de votre choix.</span><span class="sxs-lookup"><span data-stu-id="e69fe-256">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="e69fe-257">Cette commande requiert des symboles privés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-257">This command requires private symbols.</span></span>

  <span data-ttu-id="e69fe-258">Cette commande force un arrêt si **RestartEE** est exécuté après la récupération des objets de génération 2 pour le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-258">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="e69fe-259">Dans le garbage collection pour serveur, un seul thread appelle **RestartEE**. Ainsi, le point d’arrêt se produit une seule fois pendant un garbage collection de génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-259">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="e69fe-260">Procédures de contrôle des performances</span><span class="sxs-lookup"><span data-stu-id="e69fe-260">Performance Check Procedures</span></span>

<span data-ttu-id="e69fe-261">Cette section décrit les procédures suivantes permettant d'isoler la cause des problèmes de performances :</span><span class="sxs-lookup"><span data-stu-id="e69fe-261">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="e69fe-262">Déterminez si le problème est causé par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-262">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="e69fe-263">Déterminez si l’exception de mémoire insuffisante est gérée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-263">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="e69fe-264">Identifiez la quantité de mémoire virtuelle pouvant être réservée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-264">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="e69fe-265">Déterminez si la mémoire physique est suffisante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-265">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="e69fe-266">Identifiez la quantité de mémoire validée par le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-266">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="e69fe-267">Identifiez la quantité de mémoire réservée par le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-267">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="e69fe-268">Identifiez les objets volumineux dans la génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-268">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="e69fe-269">Identifiez les références aux objets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-269">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="e69fe-270">Déterminez si un finaliseur a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="e69fe-270">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="e69fe-271">Déterminez s’il y a des objets en attente de finalisation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-271">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="e69fe-272">Identifiez la quantité d’espace libre dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-272">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="e69fe-273">Identifiez le nombre d’objets épinglés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-273">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="e69fe-274">Identifiez la durée d’un nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-274">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="e69fe-275">Déterminez ce qui a déclenché le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-275">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="e69fe-276">Déterminez si l’utilisation élevée du processeur est causée par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="e69fe-276">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="e69fe-277">Pour déterminer si le problème est causé par le garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-277">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="e69fe-278">Examinez les deux compteurs de performances de mémoire suivants :</span><span class="sxs-lookup"><span data-stu-id="e69fe-278">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="e69fe-279">**% Temps dans le GC**.</span><span class="sxs-lookup"><span data-stu-id="e69fe-279">**% Time in GC**.</span></span> <span data-ttu-id="e69fe-280">Affiche le pourcentage de la durée calendaire passé à effectuer un garbage collection après le dernier cycle de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-280">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="e69fe-281">Utilisez ce compteur pour déterminer si le garbage collector passe trop de temps à libérer de l'espace dans le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-281">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="e69fe-282">Si le temps passé au garbage collection est relativement faible, cela peut indiquer un problème de ressources en dehors du tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-282">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="e69fe-283">Ce compteur peut être inexact si le garbage collection simultané ou le garbage collection d’arrière-plan sont impliqués.</span><span class="sxs-lookup"><span data-stu-id="e69fe-283">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="e69fe-284">Nombre **total d’octets validés**.</span><span class="sxs-lookup"><span data-stu-id="e69fe-284">**# Total committed Bytes**.</span></span> <span data-ttu-id="e69fe-285">Affiche la quantité de mémoire virtuelle actuellement validée par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="e69fe-285">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="e69fe-286">Utilisez ce compteur pour déterminer si la mémoire consommée par le garbage collector est trop élevée par rapport à la mémoire totale utilisée par votre application.</span><span class="sxs-lookup"><span data-stu-id="e69fe-286">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="e69fe-287">La plupart des compteurs de performances de mémoire sont mis à jour à la fin de chaque garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-287">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="e69fe-288">Ils peuvent donc ne pas refléter les conditions actuelles à propos desquelles vous voulez obtenir des informations.</span><span class="sxs-lookup"><span data-stu-id="e69fe-288">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="e69fe-289">Pour déterminer si l'exception de mémoire insuffisante est managée</span><span class="sxs-lookup"><span data-stu-id="e69fe-289">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="e69fe-290">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande d’exception d’impression (**pe**) suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-290">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="e69fe-291">**! PE**</span><span class="sxs-lookup"><span data-stu-id="e69fe-291">**!pe**</span></span>

    <span data-ttu-id="e69fe-292">Si l'exception est managée, <xref:System.OutOfMemoryException> s'affiche comme le type d'exception, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e69fe-292">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="e69fe-293">Si la sortie ne spécifie pas d'exception, vous devez déterminer de quel thread provient l'exception de mémoire insuffisante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-293">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="e69fe-294">Tapez la commande suivante dans le débogueur pour afficher tous les threads avec leurs piles d'appels :</span><span class="sxs-lookup"><span data-stu-id="e69fe-294">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="e69fe-295">**~\*kbit**</span><span class="sxs-lookup"><span data-stu-id="e69fe-295">**~\*kb**</span></span>

    <span data-ttu-id="e69fe-296">Le thread avec la pile associée aux appels d'exception est indiqué par l'argument `RaiseTheException`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-296">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="e69fe-297">Il s'agit de l'objet exception managée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-297">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="e69fe-298">Vous pouvez utiliser la commande suivante pour faire un dump des exceptions imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e69fe-298">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="e69fe-299">**!pe -nested**</span><span class="sxs-lookup"><span data-stu-id="e69fe-299">**!pe -nested**</span></span>

    <span data-ttu-id="e69fe-300">Si vous ne trouvez pas d'exceptions, l'exception de mémoire insuffisante provient de code non managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-300">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="e69fe-301">Pour déterminer la quantité de mémoire virtuelle pouvant être réservée</span><span class="sxs-lookup"><span data-stu-id="e69fe-301">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="e69fe-302">Dans le débogueur WinDbg avec l’extension SOS chargée, tapez la commande suivante pour obtenir la région libre la plus grande :</span><span class="sxs-lookup"><span data-stu-id="e69fe-302">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="e69fe-303">**!address -summary**</span><span class="sxs-lookup"><span data-stu-id="e69fe-303">**!address -summary**</span></span>

  <span data-ttu-id="e69fe-304">La plus grande région libre est affichée comme dans la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-304">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="e69fe-305">Dans cet exemple, la taille de la région libre la plus grande est d'environ 24 000 Ko (3A980 en hexadécimal).</span><span class="sxs-lookup"><span data-stu-id="e69fe-305">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="e69fe-306">Cette région est beaucoup plus petite que ce dont le garbage collector a besoin pour un segment.</span><span class="sxs-lookup"><span data-stu-id="e69fe-306">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="e69fe-307">-ou-</span><span class="sxs-lookup"><span data-stu-id="e69fe-307">-or-</span></span>

- <span data-ttu-id="e69fe-308">Utilisez la commande **vmstat** :</span><span class="sxs-lookup"><span data-stu-id="e69fe-308">Use the **vmstat** command:</span></span>

  <span data-ttu-id="e69fe-309">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="e69fe-309">**!vmstat**</span></span>

  <span data-ttu-id="e69fe-310">La région libre la plus grande correspond à la plus grande valeur de la colonne MAXIMUM, comme illustré dans la sortie suivante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-310">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="e69fe-311">Pour déterminer si la mémoire physique est suffisante</span><span class="sxs-lookup"><span data-stu-id="e69fe-311">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="e69fe-312">Démarrez le Gestionnaire des tâches Windows.</span><span class="sxs-lookup"><span data-stu-id="e69fe-312">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="e69fe-313">Sous l’onglet **Performances**, regardez la valeur validée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-313">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="e69fe-314">(Dans Windows 7, regardez **Validation (Ko)** sous **Groupe système**.)</span><span class="sxs-lookup"><span data-stu-id="e69fe-314">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="e69fe-315">Si le **Total** est proche de la **Limite**, la mémoire physique devient insuffisante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-315">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="e69fe-316">Pour déterminer la quantité de mémoire que le tas managé valide</span><span class="sxs-lookup"><span data-stu-id="e69fe-316">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="e69fe-317">Utilisez le compteur de performances de mémoire `# Total committed bytes` pour obtenir le nombre d'octets que le tas managé valide.</span><span class="sxs-lookup"><span data-stu-id="e69fe-317">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="e69fe-318">Le garbage collector valide des parties d'un segment au fur et à mesure des besoins, et non tous en même temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-318">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="e69fe-319">N'utilisez pas le compteur de performances `# Bytes in all Heaps`, car il ne représente pas l'utilisation réelle de la mémoire par le tas managé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-319">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="e69fe-320">La taille d'une génération est incluse dans cette valeur et correspond à la taille de son seuil, c'est-à-dire, à la taille qui déclenche un garbage collection si la génération est remplie d'objets.</span><span class="sxs-lookup"><span data-stu-id="e69fe-320">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="e69fe-321">Cette valeur est donc généralement égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="e69fe-321">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="e69fe-322">Pour déterminer la quantité de mémoire réservée pour le tas managé</span><span class="sxs-lookup"><span data-stu-id="e69fe-322">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="e69fe-323">Utilisez le compteur de performances de mémoire `# Total reserved bytes`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-323">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="e69fe-324">Le garbage collector réserve de la mémoire sous forme de segments, et vous pouvez déterminer où démarre un segment à l'aide de la commande **eeheap**.</span><span class="sxs-lookup"><span data-stu-id="e69fe-324">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e69fe-325">Même s'il est possible de déterminer la quantité de mémoire que le garbage collector alloue à chaque segment, la taille d'un segment dépend de l'implémentation et est susceptible de changer à tout moment, y compris lors des mises à jour périodiques.</span><span class="sxs-lookup"><span data-stu-id="e69fe-325">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="e69fe-326">Votre application ne doit jamais faire d'hypothèses concernant une taille de segment particulière, ni dépendre de celle-ci. Elle ne doit pas non plus tenter de configurer la quantité de mémoire disponible pour les allocations de segments.</span><span class="sxs-lookup"><span data-stu-id="e69fe-326">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="e69fe-327">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-327">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="e69fe-328">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="e69fe-328">**!eeheap -gc**</span></span>

  <span data-ttu-id="e69fe-329">Le résultat est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e69fe-329">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="e69fe-330">Les adresses indiquées par "segment" sont les adresses de début des segments.</span><span class="sxs-lookup"><span data-stu-id="e69fe-330">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="e69fe-331">Pour déterminer les objets volumineux dans la génération 2</span><span class="sxs-lookup"><span data-stu-id="e69fe-331">To determine large objects in generation 2</span></span>

- <span data-ttu-id="e69fe-332">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-332">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="e69fe-333">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="e69fe-333">**!dumpheap –stat**</span></span>

  <span data-ttu-id="e69fe-334">Si le tas managé est volumineux, l’exécution de **dumpheap** peut prendre un certain temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-334">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="e69fe-335">Vous pouvez commencer l'analyse des dernières lignes de la sortie, car elles contiennent les objets qui utilisent le plus d'espace.</span><span class="sxs-lookup"><span data-stu-id="e69fe-335">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="e69fe-336">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e69fe-336">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="e69fe-337">Le dernier objet répertorié est une chaîne qui occupe le plus d'espace.</span><span class="sxs-lookup"><span data-stu-id="e69fe-337">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="e69fe-338">Vous pouvez examiner votre application pour voir comment vos objets de chaîne peuvent être optimisés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-338">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="e69fe-339">Pour afficher les chaînes dont la taille est comprise entre 150 et 200 octets, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-339">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="e69fe-340">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="e69fe-340">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="e69fe-341">Voici un exemple de résultat.</span><span class="sxs-lookup"><span data-stu-id="e69fe-341">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="e69fe-342">L'utilisation d'un entier au lieu d'une chaîne pour un ID peut être plus efficace.</span><span class="sxs-lookup"><span data-stu-id="e69fe-342">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="e69fe-343">Si la même chaîne est répétée des milliers de fois, envisagez la centralisation des chaînes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-343">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="e69fe-344">Pour plus d'informations sur la centralisation des chaînes, voir la rubrique de référence sur la méthode <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e69fe-344">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="e69fe-345">Pour déterminer les références aux objets</span><span class="sxs-lookup"><span data-stu-id="e69fe-345">To determine references to objects</span></span>

- <span data-ttu-id="e69fe-346">Dans le débogueur WinDbg avec l’extension SOS chargée, tapez la commande suivante pour obtenir la liste des références aux objets :</span><span class="sxs-lookup"><span data-stu-id="e69fe-346">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="e69fe-347">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="e69fe-347">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="e69fe-348">Pour déterminer les références à un objet spécifique, incluez l'adresse suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-348">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="e69fe-349">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="e69fe-349">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="e69fe-350">Les racines trouvées sur les piles peuvent être de faux positifs.</span><span class="sxs-lookup"><span data-stu-id="e69fe-350">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="e69fe-351">Pour plus d'informations, utilisez la commande `!help gcroot`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-351">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="e69fe-352">L'exécution de la commande **gcroot** peut prendre beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-352">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="e69fe-353">Tout objet qui n’est pas récupéré par le garbage collection est un objet dynamique.</span><span class="sxs-lookup"><span data-stu-id="e69fe-353">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="e69fe-354">Cela signifie qu’une racine maintient directement ou indirectement l’objet. **gcroot** doit donc retourner des informations de chemin d’accès à l’objet.</span><span class="sxs-lookup"><span data-stu-id="e69fe-354">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="e69fe-355">Vous devez examiner les graphiques retournés et voir pourquoi ces objets sont encore référencés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-355">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="e69fe-356">Pour déterminer si un finaliseur a été exécuté</span><span class="sxs-lookup"><span data-stu-id="e69fe-356">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="e69fe-357">Exécutez un programme de test contenant le code suivant :</span><span class="sxs-lookup"><span data-stu-id="e69fe-357">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="e69fe-358">Si le test résout le problème, cela signifie que le garbage collector ne récupérait pas les objets, parce que les finaliseurs de ces objets avaient été interrompus.</span><span class="sxs-lookup"><span data-stu-id="e69fe-358">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="e69fe-359">La méthode <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> permet aux finaliseurs d'effectuer leurs tâches et résout le problème.</span><span class="sxs-lookup"><span data-stu-id="e69fe-359">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="e69fe-360">Pour déterminer s'il existe des objets en attente de finalisation</span><span class="sxs-lookup"><span data-stu-id="e69fe-360">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="e69fe-361">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-361">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="e69fe-362">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="e69fe-362">**!finalizequeue**</span></span>

    <span data-ttu-id="e69fe-363">Regardez le nombre d'objets qui sont prêts pour la finalisation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-363">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="e69fe-364">Si le nombre est élevé, vous devez examiner les raisons pour lesquelles ces finaliseurs ne peuvent pas progresser du tout ou pas assez rapidement.</span><span class="sxs-lookup"><span data-stu-id="e69fe-364">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="e69fe-365">Pour obtenir une sortie des threads, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-365">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="e69fe-366">**threads -special**</span><span class="sxs-lookup"><span data-stu-id="e69fe-366">**threads -special**</span></span>

    <span data-ttu-id="e69fe-367">Cette commande fournit une sortie semblable à la suivante.</span><span class="sxs-lookup"><span data-stu-id="e69fe-367">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="e69fe-368">Le thread finaliseur indique quel finaliseur, est en cours d'exécution, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="e69fe-368">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="e69fe-369">Quand un thread finaliseur n'exécute pas de finaliseur, il attend qu'un événement lui demande d'effectuer son travail.</span><span class="sxs-lookup"><span data-stu-id="e69fe-369">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="e69fe-370">La plupart du temps, vous verrez le thread finaliseur dans cet état, car il s'exécute avec une THREAD_HIGHEST_PRIORITY et est supposé terminer l'exécution des finaliseurs, le cas échéant, très rapidement.</span><span class="sxs-lookup"><span data-stu-id="e69fe-370">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="e69fe-371">Pour déterminer la quantité d'espace libre dans le tas managé</span><span class="sxs-lookup"><span data-stu-id="e69fe-371">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="e69fe-372">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-372">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="e69fe-373">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="e69fe-373">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="e69fe-374">Cette commande affiche la taille totale de tous les objets libres sur le tas managé, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e69fe-374">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="e69fe-375">Pour déterminer l'espace libre dans la génération 0, tapez la commande suivante pour obtenir des informations sur la consommation de mémoire par génération :</span><span class="sxs-lookup"><span data-stu-id="e69fe-375">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="e69fe-376">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="e69fe-376">**!eeheap -gc**</span></span>

  <span data-ttu-id="e69fe-377">Cette commande affiche une sortie similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-377">This command displays output similar to the following.</span></span> <span data-ttu-id="e69fe-378">La dernière ligne indique le segment éphémère.</span><span class="sxs-lookup"><span data-stu-id="e69fe-378">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="e69fe-379">Calculez l'espace utilisé par la génération 0 :</span><span class="sxs-lookup"><span data-stu-id="e69fe-379">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="e69fe-380">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="e69fe-380">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="e69fe-381">Le résultat est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e69fe-381">The result is as follows.</span></span> <span data-ttu-id="e69fe-382">La génération 0 est d'environ 9 Mo.</span><span class="sxs-lookup"><span data-stu-id="e69fe-382">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="e69fe-383">La commande suivante fait un dump pour l'espace libre dans la plage de la génération 0 :</span><span class="sxs-lookup"><span data-stu-id="e69fe-383">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="e69fe-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="e69fe-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="e69fe-385">Le résultat est le suivant :</span><span class="sxs-lookup"><span data-stu-id="e69fe-385">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="e69fe-386">Cette sortie indique que la partie du tas consacrée à la génération 0 utilise 9 Mo d'espace pour les objets et dispose de 7 Mo d'espace libre.</span><span class="sxs-lookup"><span data-stu-id="e69fe-386">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="e69fe-387">Cette analyse montre dans quelle mesure la génération 0 contribue à la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="e69fe-387">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="e69fe-388">Cette quantité d'utilisation du tas doit être retirée de la quantité totale, car elle est la cause de la fragmentation par les objets à long terme.</span><span class="sxs-lookup"><span data-stu-id="e69fe-388">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="e69fe-389">Pour déterminer le nombre d'objets épinglés</span><span class="sxs-lookup"><span data-stu-id="e69fe-389">To determine the number of pinned objects</span></span>

- <span data-ttu-id="e69fe-390">Dans le débogueur WinDbg ou Visual Studio avec l’extension SOS chargée, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-390">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="e69fe-391">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="e69fe-391">**!gchandles**</span></span>

  <span data-ttu-id="e69fe-392">Les statistiques affichées incluent le nombre de handles épinglés, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e69fe-392">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="e69fe-393">Pour déterminer la durée d'un garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-393">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="e69fe-394">Regardez ce qu'affiche le compteur de performances de mémoire `% Time in GC`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-394">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="e69fe-395">La valeur est calculée à partir d'un échantillon d'intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-395">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="e69fe-396">Les compteurs sont mis à jour à la fin de chaque garbage collection. L'exemple actuel aura donc la même valeur que l'exemple précédent si aucune collection ne s'est produite pendant l'intervalle.</span><span class="sxs-lookup"><span data-stu-id="e69fe-396">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="e69fe-397">La durée de la collection est obtenue en multipliant l'échantillon d'intervalle de temps par la valeur de pourcentage.</span><span class="sxs-lookup"><span data-stu-id="e69fe-397">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="e69fe-398">Les données suivantes montrent quatre échantillons d'intervalles de deux secondes, pour une étude de 8 secondes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-398">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="e69fe-399">Les colonnes `Gen0`, `Gen1` et `Gen2` indiquent le nombre de garbage collection qui se sont produits pendant cet intervalle pour cette génération.</span><span class="sxs-lookup"><span data-stu-id="e69fe-399">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="e69fe-400">Ces informations n'affichent pas le moment auquel s'est produit le garbage collection, mais vous pouvez toutefois connaître le nombre de garbage collection qui se sont produits dans un intervalle de temps.</span><span class="sxs-lookup"><span data-stu-id="e69fe-400">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="e69fe-401">Dans le pire des cas, le dixième garbage collection de génération 0 s'est terminé au début du deuxième intervalle et le onzième garbage collection de génération 0 s'est terminé à la fin du cinquième intervalle.</span><span class="sxs-lookup"><span data-stu-id="e69fe-401">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="e69fe-402">Le délai entre la fin du dixième et la fin du onzième garbage collection est d'environ 2 secondes. Le compteur de performances indique 3 %. La durée du onzième garbage collection de génération 0 était donc de (2 secondes \* 3 % = 60 ms).</span><span class="sxs-lookup"><span data-stu-id="e69fe-402">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="e69fe-403">Cet exemple comprend 5 périodes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-403">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="e69fe-404">Le deuxième garbage collection de génération 2 a démarré pendant le troisième intervalle et s'est terminé au cinquième intervalle.</span><span class="sxs-lookup"><span data-stu-id="e69fe-404">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="e69fe-405">Dans le pire des cas, le dernier garbage collection était pour une collection de génération 0 qui s'est terminée au début du deuxième intervalle et le garbage collection de génération 2 s'est terminé à la fin du cinquième intervalle.</span><span class="sxs-lookup"><span data-stu-id="e69fe-405">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="e69fe-406">Le délai entre la fin du garbage collection de génération 0 et la fin du garbage collection de génération 2 est donc de 4 secondes.</span><span class="sxs-lookup"><span data-stu-id="e69fe-406">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="e69fe-407">Étant donné que le compteur `% Time in GC` affiche 20 %, la durée maximale du garbage collection de génération 2 est de (4 secondes \* 20 % = 800 ms).</span><span class="sxs-lookup"><span data-stu-id="e69fe-407">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="e69fe-408">Vous pouvez également déterminer la durée d’un garbage collection à l’aide des [événements ETW de garbage collection](../../framework/performance/garbage-collection-etw-events.md) en analysant les informations fournies.</span><span class="sxs-lookup"><span data-stu-id="e69fe-408">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="e69fe-409">Par exemple, les données suivantes indiquent une séquence d’événements qui se sont produits pendant un garbage collection non simultané.</span><span class="sxs-lookup"><span data-stu-id="e69fe-409">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="e69fe-410">La suspension des threads managés a pris 26 us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span><span class="sxs-lookup"><span data-stu-id="e69fe-410">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="e69fe-411">Le garbage collection réel a pris 4,8 ms (`GCEnd_V1` – `GCStart_V1`).</span><span class="sxs-lookup"><span data-stu-id="e69fe-411">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="e69fe-412">La reprise des threads managés a pris 21 us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span><span class="sxs-lookup"><span data-stu-id="e69fe-412">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="e69fe-413">La sortie suivante fournit un exemple de garbage collection d'arrière-plan et inclut les champs de processus, de thread et d'événement</span><span class="sxs-lookup"><span data-stu-id="e69fe-413">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="e69fe-414">(toutes les données ne sont pas affichées).</span><span class="sxs-lookup"><span data-stu-id="e69fe-414">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="e69fe-415">L'événement `GCStart_V1` à la ligne 42504816 indique qu'il s'agit d'un garbage collection d'arrière-plan, car le dernier champ est `1`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-415">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="e69fe-416">Cela devient le garbage collection numéro</span><span class="sxs-lookup"><span data-stu-id="e69fe-416">This becomes garbage collection No.</span></span> <span data-ttu-id="e69fe-417">102019.</span><span class="sxs-lookup"><span data-stu-id="e69fe-417">102019.</span></span>

  <span data-ttu-id="e69fe-418">L'événement `GCStart` se produit, car un garbage collection éphémère doit être effectué avant de démarrer un garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="e69fe-418">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="e69fe-419">Cela devient le garbage collection numéro</span><span class="sxs-lookup"><span data-stu-id="e69fe-419">This becomes garbage collection No.</span></span> <span data-ttu-id="e69fe-420">102020.</span><span class="sxs-lookup"><span data-stu-id="e69fe-420">102020.</span></span>

  <span data-ttu-id="e69fe-421">À la ligne 42514170, le garbage collection numéro</span><span class="sxs-lookup"><span data-stu-id="e69fe-421">At 42514170, garbage collection No.</span></span> <span data-ttu-id="e69fe-422">102020 prend fin.</span><span class="sxs-lookup"><span data-stu-id="e69fe-422">102020 finishes.</span></span> <span data-ttu-id="e69fe-423">Les threads managés sont redémarrés à cet endroit.</span><span class="sxs-lookup"><span data-stu-id="e69fe-423">The managed threads are restarted at this point.</span></span> <span data-ttu-id="e69fe-424">L'opération se termine au thread 4372, qui a déclenché ce garbage collection d'arrière-plan.</span><span class="sxs-lookup"><span data-stu-id="e69fe-424">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="e69fe-425">Au thread 4744, une suspension se produit.</span><span class="sxs-lookup"><span data-stu-id="e69fe-425">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="e69fe-426">C'est la seule fois où le garbage collection d'arrière-plan doit suspendre les threads managés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-426">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="e69fe-427">Cette durée est d'environ 99 ms ((63784407-63685394)/1000).</span><span class="sxs-lookup"><span data-stu-id="e69fe-427">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="e69fe-428">L'événement `GCEnd` pour le garbage collection d'arrière-plan se trouve à la ligne 89931423.</span><span class="sxs-lookup"><span data-stu-id="e69fe-428">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="e69fe-429">Cela signifie que le garbage collection d'arrière-plan a duré environ 47 secondes ((89931423-42504816)/1000).</span><span class="sxs-lookup"><span data-stu-id="e69fe-429">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="e69fe-430">Pendant que les threads managés sont exécutés, vous pouvez voir tous les garbage collection éphémères en cours.</span><span class="sxs-lookup"><span data-stu-id="e69fe-430">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="e69fe-431">Pour déterminer ce qui a déclenché un garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-431">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="e69fe-432">Dans le débogueur WinDbg ou Visual Studio avec l’extension de débogueur SOS chargée, tapez la commande suivante pour afficher tous les threads avec leurs piles d’appels :</span><span class="sxs-lookup"><span data-stu-id="e69fe-432">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="e69fe-433">**~\*kbit**</span><span class="sxs-lookup"><span data-stu-id="e69fe-433">**~\*kb**</span></span>

  <span data-ttu-id="e69fe-434">Cette commande affiche une sortie similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="e69fe-434">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="e69fe-435">Si le garbage collection a été provoqué par une notification de mémoire insuffisante du système d'exploitation, la pile des appels sera similaire, à ceci près que le thread sera le thread finaliseur.</span><span class="sxs-lookup"><span data-stu-id="e69fe-435">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="e69fe-436">Le thread finaliseur reçoit une notification asynchrone de mémoire insuffisante et déclenche le garbage collection.</span><span class="sxs-lookup"><span data-stu-id="e69fe-436">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="e69fe-437">Si le garbage collection a été provoqué par l'allocation de mémoire, la pile se présente comme ceci :</span><span class="sxs-lookup"><span data-stu-id="e69fe-437">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="e69fe-438">Un programme d'assistance juste-à-temps (`JIT_New*`) appelle `GCHeap::GarbageCollectGeneration`.</span><span class="sxs-lookup"><span data-stu-id="e69fe-438">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="e69fe-439">Si vous déterminez que les garbage collection de génération 2 sont dus à des allocations, vous devez déterminer quels objets sont collectés par les garbage collection de génération 2 et comment les éviter.</span><span class="sxs-lookup"><span data-stu-id="e69fe-439">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="e69fe-440">Autrement dit, vous devez déterminer la différence entre le début et la fin d'un garbage collection de génération 2, ainsi que les objets qui ont provoqué la collection de génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-440">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="e69fe-441">Par exemple, tapez la commande suivante dans le débogueur pour afficher le début d’une collection de génération 2 :</span><span class="sxs-lookup"><span data-stu-id="e69fe-441">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="e69fe-442">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="e69fe-442">**!dumpheap –stat**</span></span>

  <span data-ttu-id="e69fe-443">Exemple de sortie (abrégé pour montrer les objets qui utilisent le plus d'espace) :</span><span class="sxs-lookup"><span data-stu-id="e69fe-443">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="e69fe-444">Répétez la commande à la fin de la génération 2 :</span><span class="sxs-lookup"><span data-stu-id="e69fe-444">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="e69fe-445">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="e69fe-445">**!dumpheap –stat**</span></span>

  <span data-ttu-id="e69fe-446">Exemple de sortie (abrégé pour montrer les objets qui utilisent le plus d'espace) :</span><span class="sxs-lookup"><span data-stu-id="e69fe-446">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="e69fe-447">Les objets `double[]` ont disparu de la fin de la sortie, ce qui signifie qu'ils ont été collectés.</span><span class="sxs-lookup"><span data-stu-id="e69fe-447">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="e69fe-448">Ces objets représentent environ 70 Mo.</span><span class="sxs-lookup"><span data-stu-id="e69fe-448">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="e69fe-449">Les objets restants n'ont pas beaucoup changé.</span><span class="sxs-lookup"><span data-stu-id="e69fe-449">The remaining objects did not change much.</span></span> <span data-ttu-id="e69fe-450">Ces objets `double[]` étaient donc à l'origine du déclenchement du garbage collection de génération 2.</span><span class="sxs-lookup"><span data-stu-id="e69fe-450">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="e69fe-451">L'étape suivante consiste à déterminer pourquoi les objets `double[]` y sont situés et pourquoi ils sont morts.</span><span class="sxs-lookup"><span data-stu-id="e69fe-451">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="e69fe-452">Vous pouvez demander à un développeur d'où proviennent ces objets ou vous pouvez utiliser la commande **gcroot**.</span><span class="sxs-lookup"><span data-stu-id="e69fe-452">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="e69fe-453">Pour déterminer si l’utilisation élevée du processeur est causée par le garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-453">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="e69fe-454">Mettez en corrélation la valeur du compteur de performances de mémoire `% Time in GC` avec le temps d'exécution.</span><span class="sxs-lookup"><span data-stu-id="e69fe-454">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="e69fe-455">Si la valeur `% Time in GC` connaît un pic en même temps que le temps d'exécution, le garbage collection provoque une utilisation élevée du processeur.</span><span class="sxs-lookup"><span data-stu-id="e69fe-455">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="e69fe-456">Dans le cas contraire, profilez l'application pour trouver où se produit l'utilisation élevée.</span><span class="sxs-lookup"><span data-stu-id="e69fe-456">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="e69fe-457">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e69fe-457">See also</span></span>

- [<span data-ttu-id="e69fe-458">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="e69fe-458">Garbage Collection</span></span>](index.md)

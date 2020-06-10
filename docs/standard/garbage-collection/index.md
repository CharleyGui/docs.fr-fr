---
title: Garbage collection .NET
description: En savoir plus sur les garbage collection dans .NET. Le garbage collector .NET gère l’allocation et la libération de mémoire pour votre application.
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662483"
---
# <a name="garbage-collection"></a><span data-ttu-id="f7eb2-104">Garbage collection</span><span class="sxs-lookup"><span data-stu-id="f7eb2-104">Garbage collection</span></span>

<span data-ttu-id="f7eb2-105">Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="f7eb2-106">Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="f7eb2-107">Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="f7eb2-108">Toutefois, la mémoire n’est pas infinie.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-108">However, memory is not infinite.</span></span> <span data-ttu-id="f7eb2-109">Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="f7eb2-110">Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="f7eb2-111">Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7eb2-112">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f7eb2-112">In this section</span></span>
  
|<span data-ttu-id="f7eb2-113">Intitulé</span><span class="sxs-lookup"><span data-stu-id="f7eb2-113">Title</span></span>|<span data-ttu-id="f7eb2-114">Description</span><span class="sxs-lookup"><span data-stu-id="f7eb2-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f7eb2-115">Notions de base de garbage collection</span><span class="sxs-lookup"><span data-stu-id="f7eb2-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="f7eb2-116">Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="f7eb2-117">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="f7eb2-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="f7eb2-118">Décrit les différences entre les garbage collection de station de travail pour les applications clientes et les garbage collection de serveur pour les applications serveur.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="f7eb2-119">garbage collection d’arrière-plan</span><span class="sxs-lookup"><span data-stu-id="f7eb2-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="f7eb2-120">Décrit les garbage collection d’arrière-plan, qui est la collection d’objets de génération 0 et 1 alors que la collection de génération 2 est en cours.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="f7eb2-121">Tas d’objets volumineux</span><span class="sxs-lookup"><span data-stu-id="f7eb2-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="f7eb2-122">Décrit le tas d’objets volumineux (LOH) et la façon dont les objets volumineux sont récupérés par le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="f7eb2-123">Garbage collection et performances</span><span class="sxs-lookup"><span data-stu-id="f7eb2-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="f7eb2-124">Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="f7eb2-125">Collections forcées</span><span class="sxs-lookup"><span data-stu-id="f7eb2-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="f7eb2-126">Décrit comment faire pour qu’un garbage collection se produise.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="f7eb2-127">Modes de latence</span><span class="sxs-lookup"><span data-stu-id="f7eb2-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="f7eb2-128">Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="f7eb2-129">Optimisation pour l’hébergement web partagé</span><span class="sxs-lookup"><span data-stu-id="f7eb2-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="f7eb2-130">Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="f7eb2-131">Notifications du garbage collection</span><span class="sxs-lookup"><span data-stu-id="f7eb2-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="f7eb2-132">Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="f7eb2-133">Supervision des ressource de domaine d’application</span><span class="sxs-lookup"><span data-stu-id="f7eb2-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="f7eb2-134">Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="f7eb2-135">Références faibles</span><span class="sxs-lookup"><span data-stu-id="f7eb2-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="f7eb2-136">Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.</span><span class="sxs-lookup"><span data-stu-id="f7eb2-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="f7eb2-137">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="f7eb2-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="f7eb2-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7eb2-138">See also</span></span>

- [<span data-ttu-id="f7eb2-139">Nettoyer les ressources non managées</span><span class="sxs-lookup"><span data-stu-id="f7eb2-139">Clean up unmanaged resources</span></span>](unmanaged.md)

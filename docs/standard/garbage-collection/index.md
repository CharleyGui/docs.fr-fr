---
title: .NET collecte des ordures
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
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102240"
---
# <a name="garbage-collection"></a><span data-ttu-id="14504-102">Nettoyage de la mémoire</span><span class="sxs-lookup"><span data-stu-id="14504-102">Garbage collection</span></span>

<span data-ttu-id="14504-103">Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="14504-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="14504-104">Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé.</span><span class="sxs-lookup"><span data-stu-id="14504-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="14504-105">Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets.</span><span class="sxs-lookup"><span data-stu-id="14504-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="14504-106">Toutefois, la mémoire n’est pas infinie.</span><span class="sxs-lookup"><span data-stu-id="14504-106">However, memory is not infinite.</span></span> <span data-ttu-id="14504-107">Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="14504-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="14504-108">Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées.</span><span class="sxs-lookup"><span data-stu-id="14504-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="14504-109">Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.</span><span class="sxs-lookup"><span data-stu-id="14504-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14504-110">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="14504-110">In this section</span></span>
  
|<span data-ttu-id="14504-111">Intitulé</span><span class="sxs-lookup"><span data-stu-id="14504-111">Title</span></span>|<span data-ttu-id="14504-112">Description</span><span class="sxs-lookup"><span data-stu-id="14504-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="14504-113">Principes fondamentaux de la collecte des ordures</span><span class="sxs-lookup"><span data-stu-id="14504-113">Fundamentals of garbage collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="14504-114">Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.</span><span class="sxs-lookup"><span data-stu-id="14504-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="14504-115">Garbage collection de station de travail et de serveur</span><span class="sxs-lookup"><span data-stu-id="14504-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="14504-116">Décrit les différences entre la collecte des ordures de poste de travail pour les applications client et la collecte des ordures du serveur pour les applications serveur.</span><span class="sxs-lookup"><span data-stu-id="14504-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="14504-117">Collecte des ordures de fond</span><span class="sxs-lookup"><span data-stu-id="14504-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="14504-118">Décrit la collecte des ordures de fond, qui est la collecte d’objets de génération 0 et 1 alors que la collection de la génération 2 est en cours.</span><span class="sxs-lookup"><span data-stu-id="14504-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="14504-119">Le grand tas d’objets</span><span class="sxs-lookup"><span data-stu-id="14504-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="14504-120">Décrit le grand tas d’objets (LOH) et comment les gros objets sont collectés par les ordures.</span><span class="sxs-lookup"><span data-stu-id="14504-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="14504-121">Collecte et performance des ordures</span><span class="sxs-lookup"><span data-stu-id="14504-121">Garbage collection and performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="14504-122">Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.</span><span class="sxs-lookup"><span data-stu-id="14504-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="14504-123">Collections forcées</span><span class="sxs-lookup"><span data-stu-id="14504-123">Induced collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="14504-124">Décrit comment faire pour qu’un garbage collection se produise.</span><span class="sxs-lookup"><span data-stu-id="14504-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="14504-125">Modes de latence</span><span class="sxs-lookup"><span data-stu-id="14504-125">Latency modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="14504-126">Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="14504-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="14504-127">Optimisation pour l’hébergement web partagé</span><span class="sxs-lookup"><span data-stu-id="14504-127">Optimization for shared web hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="14504-128">Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.</span><span class="sxs-lookup"><span data-stu-id="14504-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="14504-129">Notifications du garbage collection</span><span class="sxs-lookup"><span data-stu-id="14504-129">Garbage collection notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="14504-130">Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="14504-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="14504-131">Supervision des ressource de domaine d’application</span><span class="sxs-lookup"><span data-stu-id="14504-131">Application domain resource monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="14504-132">Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="14504-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="14504-133">Références faibles</span><span class="sxs-lookup"><span data-stu-id="14504-133">Weak references</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="14504-134">Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.</span><span class="sxs-lookup"><span data-stu-id="14504-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="14504-135">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="14504-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="14504-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14504-136">See also</span></span>

- [<span data-ttu-id="14504-137">Nettoyer les ressources non managées</span><span class="sxs-lookup"><span data-stu-id="14504-137">Clean up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)

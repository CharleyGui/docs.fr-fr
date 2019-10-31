---
title: Garbage Collection
ms.date: 03/30/2017
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
ms.openlocfilehash: 0038f4ba28c7ea3e7be4502a71026a2b3ad47829
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120988"
---
# <a name="garbage-collection"></a><span data-ttu-id="c56d2-102">Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="c56d2-102">Garbage Collection</span></span>
<span data-ttu-id="c56d2-103">Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="c56d2-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="c56d2-104">Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé.</span><span class="sxs-lookup"><span data-stu-id="c56d2-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="c56d2-105">Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets.</span><span class="sxs-lookup"><span data-stu-id="c56d2-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="c56d2-106">Toutefois, la mémoire n’est pas infinie.</span><span class="sxs-lookup"><span data-stu-id="c56d2-106">However, memory is not infinite.</span></span> <span data-ttu-id="c56d2-107">Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c56d2-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="c56d2-108">Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées.</span><span class="sxs-lookup"><span data-stu-id="c56d2-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="c56d2-109">Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.</span><span class="sxs-lookup"><span data-stu-id="c56d2-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="c56d2-110">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="c56d2-110">Related Topics</span></span>  
  
|<span data-ttu-id="c56d2-111">Titre</span><span class="sxs-lookup"><span data-stu-id="c56d2-111">Title</span></span>|<span data-ttu-id="c56d2-112">Description</span><span class="sxs-lookup"><span data-stu-id="c56d2-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c56d2-113">Principes de base du Garbage Collection</span><span class="sxs-lookup"><span data-stu-id="c56d2-113">Fundamentals of Garbage Collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="c56d2-114">Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.</span><span class="sxs-lookup"><span data-stu-id="c56d2-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="c56d2-115">Garbage Collection et performances</span><span class="sxs-lookup"><span data-stu-id="c56d2-115">Garbage Collection and Performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="c56d2-116">Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.</span><span class="sxs-lookup"><span data-stu-id="c56d2-116">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="c56d2-117">Collections forcées</span><span class="sxs-lookup"><span data-stu-id="c56d2-117">Induced Collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="c56d2-118">Décrit comment faire pour qu’un garbage collection se produise.</span><span class="sxs-lookup"><span data-stu-id="c56d2-118">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="c56d2-119">Modes de latence</span><span class="sxs-lookup"><span data-stu-id="c56d2-119">Latency Modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="c56d2-120">Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.</span><span class="sxs-lookup"><span data-stu-id="c56d2-120">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="c56d2-121">Optimisation de l'hébergement Web partagé</span><span class="sxs-lookup"><span data-stu-id="c56d2-121">Optimization for Shared Web Hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="c56d2-122">Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.</span><span class="sxs-lookup"><span data-stu-id="c56d2-122">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="c56d2-123">Notifications de garbage collection</span><span class="sxs-lookup"><span data-stu-id="c56d2-123">Garbage Collection Notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="c56d2-124">Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.</span><span class="sxs-lookup"><span data-stu-id="c56d2-124">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="c56d2-125">Analyse de ressource de domaine d'application</span><span class="sxs-lookup"><span data-stu-id="c56d2-125">Application Domain Resource Monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="c56d2-126">Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c56d2-126">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="c56d2-127">Références faibles</span><span class="sxs-lookup"><span data-stu-id="c56d2-127">Weak References</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="c56d2-128">Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.</span><span class="sxs-lookup"><span data-stu-id="c56d2-128">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="c56d2-129">Reference</span><span class="sxs-lookup"><span data-stu-id="c56d2-129">Reference</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
  
 <xref:System.GCCollectionMode?displayProperty=nameWithType>  
  
 <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
  
 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
  
 <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="c56d2-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c56d2-130">See also</span></span>

- [<span data-ttu-id="c56d2-131">Nettoyage de ressources non managées</span><span class="sxs-lookup"><span data-stu-id="c56d2-131">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)

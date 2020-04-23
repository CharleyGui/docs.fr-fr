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
# <a name="garbage-collection"></a>Nettoyage de la mémoire

Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application. Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé. Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets. Toutefois, la mémoire n’est pas infinie. Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire. Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées. Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.  
  
## <a name="in-this-section"></a>Contenu de cette section
  
|Intitulé|Description|  
|-----------|-----------------|  
|[Principes fondamentaux de la collecte des ordures](../../../docs/standard/garbage-collection/fundamentals.md)|Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.|  
|[Garbage collection de station de travail et de serveur](workstation-server-gc.md)|Décrit les différences entre la collecte des ordures de poste de travail pour les applications client et la collecte des ordures du serveur pour les applications serveur.|
|[Collecte des ordures de fond](background-gc.md)|Décrit la collecte des ordures de fond, qui est la collecte d’objets de génération 0 et 1 alors que la collection de la génération 2 est en cours.|
|[Le grand tas d’objets](large-object-heap.md)|Décrit le grand tas d’objets (LOH) et comment les gros objets sont collectés par les ordures.|
|[Collecte et performance des ordures](../../../docs/standard/garbage-collection/performance.md)|Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.|  
|[Collections forcées](../../../docs/standard/garbage-collection/induced.md)|Décrit comment faire pour qu’un garbage collection se produise.|  
|[Modes de latence](../../../docs/standard/garbage-collection/latency.md)|Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.|  
|[Optimisation pour l’hébergement web partagé](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.|  
|[Notifications du garbage collection](../../../docs/standard/garbage-collection/notifications.md)|Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.|  
|[Supervision des ressource de domaine d’application](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.|  
|[Références faibles](../../../docs/standard/garbage-collection/weak-references.md)|Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.|  
  
## <a name="reference"></a>Informations de référence

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Voir aussi

- [Nettoyer les ressources non managées](../../../docs/standard/garbage-collection/unmanaged.md)

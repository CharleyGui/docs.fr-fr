---
title: Garbage collection .NET
description: En savoir plus sur les garbage collection dans .NET. Le garbage collector .NET gère l’allocation et la libération de mémoire pour votre application.
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET]
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
ms.openlocfilehash: 39b5bf62935054bd4b9be2d228cc42202aa89144
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063187"
---
# <a name="garbage-collection"></a>Garbage collection

Le « garbage collector » du .NET gère l’allocation et la libération de mémoire pour votre application. Chaque fois que vous créez un objet, le Common Language Runtime alloue de la mémoire pour l’objet à partir du tas managé. Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets. Toutefois, la mémoire n’est pas infinie. Pour finir, le garbage collector doit exécuter une collecte afin de libérer de la mémoire. Le moteur d'optimisation du « garbage collector » détermine le meilleur moment pour lancer une opération garbage collection sur base des allocations de mémoire effectuées. Lorsque le garbage collector effectue une collecte, il recherche les objets dans le tas managé qui ne sont plus utilisés par l’application et effectue les opérations nécessaires pour récupérer leur mémoire.  
  
## <a name="in-this-section"></a>Dans cette section
  
|Titre|Description|  
|-----------|-----------------|  
|[Notions de base de garbage collection](fundamentals.md)|Décrit le fonctionnement du garbage collection, l’allocation des objets sur le tas managé, ainsi que d’autres concepts principaux.|  
|[Garbage collection de station de travail et de serveur](workstation-server-gc.md)|Décrit les différences entre les garbage collection de station de travail pour les applications clientes et les garbage collection de serveur pour les applications serveur.|
|[garbage collection d’arrière-plan](background-gc.md)|Décrit les garbage collection d’arrière-plan, qui est la collection d’objets de génération 0 et 1 alors que la collection de génération 2 est en cours.|
|[Tas d’objets volumineux](large-object-heap.md)|Décrit le tas d’objets volumineux (LOH) et la façon dont les objets volumineux sont récupérés par le garbage collector.|
|[Garbage collection et performances](performance.md)|Décrit les contrôles de performances que vous pouvez utiliser pour diagnostiquer les problèmes de garbage collection et de performances.|  
|[Collections forcées](induced.md)|Décrit comment faire pour qu’un garbage collection se produise.|  
|[Modes de latence](latency.md)|Décrit les modes qui déterminent le niveau d’intrusion du garbage collection.|  
|[Optimisation pour l’hébergement web partagé](optimization-for-shared-web-hosting.md)|Explique comment optimiser le garbage collection sur des serveurs partagés par plusieurs petits sites web.|  
|[Notifications du garbage collection](notifications.md)|Explique comment déterminer si un garbage collection est presque atteint et s’il est terminé.|  
|[Supervision des ressource de domaine d’application](app-domain-resource-monitoring.md)|Explique comment surveiller l’utilisation du processeur et de la mémoire par un domaine d’application.|  
|[Références faibles](weak-references.md)|Décrit les fonctionnalités qui permettent au Garbage collector de collecter un objet tout en permettant à l’application d’accéder à cet objet.|  
  
## <a name="reference"></a>Référence

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Voir aussi

- [Nettoyer les ressources non managées](unmanaged.md)

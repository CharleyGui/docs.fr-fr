---
title: Fonctionnalités et objets de threading
ms.date: 10/01/2018
helpviewer_keywords:
- threading [.NET], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: 8a66904a6db3fa45d8a42dec4e1e42883c1c3e98
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826168"
---
# <a name="threading-objects-and-features"></a>Fonctionnalités et objets de threading

En plus de la classe <xref:System.Threading.Thread?displayProperty=nameWithType>, .NET fournit plusieurs classes qui facilitent le développement des applications multithread. Les articles suivants présentent ces différentes classes :

|Intitulé|Description|  
|-----------|-----------------|  
|[Pool de threads managés](the-managed-thread-pool.md)|Décrit la classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, qui fournit un pool de threads de travail managés par .NET.|  
|[Minuteries](timers.md)|Décrit les minuteurs .NET qui peuvent être utilisés dans un environnement multithread.|
|[Vue d’ensemble des primitives de synchronisation](overview-of-synchronization-primitives.md)|Décrit les types qui peuvent être utilisés pour synchroniser l’accès à une ressource partagée ou contrôler les interactions de threads.|
|[EventWaitHandle](eventwaithandle.md)|Décrit la classe <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, qui représente un événement de synchronisation de threads.|
|[CountdownEvent](countdownevent.md)|Décrit la classe <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, qui représente un événement de synchronisation de threads défini quand son nombre est égal à zéro.|
|[Mutex](mutexes.md)|Décrit la classe <xref:System.Threading.Mutex?displayProperty=nameWithType>, qui accorde un accès exclusif à une ressource partagée.|
|[Semaphore et SemaphoreSlim](semaphore-and-semaphoreslim.md)|Décrit la classe <xref:System.Threading.Semaphore?displayProperty=nameWithType>, qui limite le nombre de threads qui peuvent accéder simultanément à une ressource partagée ou à un pool de ressources.|
|[Cloisonnement](barrier.md)|Décrit la classe <xref:System.Threading.Barrier?displayProperty=nameWithType>, qui implémente le modèle de cloisonnement pour la coordination des threads dans les opérations planifiées.|
|[SpinLock](spinlock.md)|Décrit la structure <xref:System.Threading.SpinLock?displayProperty=nameWithType>, une alternative légère à la classe <xref:System.Threading.Monitor?displayProperty=nameWithType> pour certains scénarios de verrouillage de bas niveau.|
|[SpinWait](spinwait.md)|Décrit la structure <xref:System.Threading.SpinWait?displayProperty=nameWithType>, qui fournit la prise en charge pour l’attente basée sur les spins.|

## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [Utilisation des threads et du threading](using-threads-and-threading.md)
- [E/s de fichier asynchrones](../io/asynchronous-file-i-o.md)
- [Programmation parallèle](../parallel-programming/index.md)
- [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md)

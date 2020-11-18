---
title: Le pool de threads managés
description: Découvrez plus d’informations sur le pool de threads .NET qui fournit des threads de travail en arrière-plan
ms.date: 08/02/2018
helpviewer_keywords:
- thread pooling [.NET]
- thread pools [.NET]
- threading [.NET], thread pool
- threading [.NET], pooling
ms.assetid: 2be05b06-a42e-4c9d-a739-96c21d673927
ms.openlocfilehash: 9bc90acd6d7e1bef81e767ce8c257fed78322554
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826181"
---
# <a name="the-managed-thread-pool"></a>Le pool de threads managés

La classe <xref:System.Threading.ThreadPool?displayProperty=nameWithType> fournit à votre application un pool de threads de travail qui sont gérés par le système, ce qui vous permet de vous concentrer sur les tâches d’application plutôt que sur la gestion des threads. Si vous avez des tâches courtes qui nécessitent un traitement en arrière-plan, le pool de threads managés est un moyen simple de tirer parti de plusieurs threads. L’utilisation du pool de threads est beaucoup plus facile dans Framework 4 et ultérieur, car vous pouvez créer des objets <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601> qui effectuent des tâches asynchrones sur les threads de pool.  
  
.NET utilise des threads de pool pour de nombreux scénarios, notamment les opérations de [bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md), l’achèvement des E/S asynchrones, les rappels de [timer](timers.md), les opérations d’attente inscrites, les appels de méthodes asynchrones utilisant des délégués et les connexions de sockets <xref:System.Net?displayProperty=nameWithType>.  

## <a name="thread-pool-characteristics"></a>Caractéristiques du pool de threads

Les threads de pool sont des threads [d’arrière-plan](foreground-and-background-threads.md). Chaque thread utilise la taille de pile par défaut, s'exécute avec la priorité par défaut et se trouve dans le multithread cloisonné. Une fois qu’un thread du pool de threads a terminé sa tâche, il est retourné à une file d’attente de threads en attente. À partir de ce moment, il peut être réutilisé. Cette réutilisation permet aux applications d’éviter le coût lié à la création d’un nouveau thread pour chaque tâche.
  
Il n'y a qu'un seul pool de threads par processus.  
  
### <a name="exceptions-in-thread-pool-threads"></a>Exceptions dans les threads de pool

Les exceptions non gérées dans les threads de pool entraînent la fin du processus. Il y a trois exceptions à cette règle :  
  
- Une <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> est levée dans un thread de pool, car <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> a été appelée.  
- Une <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> est levée dans un thread de pool, car le domaine d’application est en cours de déchargement.  
- Le common language runtime ou un processus hôte met fin au thread.  
  
Pour plus d'informations, voir [Exceptions dans les threads managés](exceptions-in-managed-threads.md).  
  
### <a name="maximum-number-of-thread-pool-threads"></a>Nombre maximal de threads dans un pool

Le nombre d’opérations qui peuvent être mises en file d’attente pour le pool de threads est limité seulement par la mémoire disponible. Cependant, le pool de threads limite le nombre de threads qui peuvent être actifs simultanément dans le processus. Si tous les threads du pool sont occupés, les éléments de travail supplémentaires sont mis en file d’attente jusqu’à ce que des threads soient disponibles pour les exécuter. La taille par défaut du pool de threads pour un processus dépend de plusieurs facteurs, tels que la taille de l’espace d’adressage virtuel. Un processus peut appeler la méthode <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> pour déterminer le nombre de threads.  
  
Vous pouvez contrôler le nombre maximal de threads à l'aide des méthodes <xref:System.Threading.ThreadPool.GetMaxThreads%2A?displayProperty=nameWithType> et <xref:System.Threading.ThreadPool.SetMaxThreads%2A?displayProperty=nameWithType>.  

> [!NOTE]
> Le code qui héberge l’common language runtime peut définir la taille à l’aide de la [`ICorThreadpool::CorSetMaxThreads`](../../framework/unmanaged-api/hosting/icorthreadpool-corsetmaxthreads-method.md) méthode.  
  
### <a name="thread-pool-minimums"></a>Valeurs minimales d’un pool de threads

Le pool de threads fournit de nouveaux threads de travail ou des threads de terminaison d'E/S à la demande jusqu'à ce qu'il atteigne la valeur minimale spécifiée pour chaque catégorie. Vous pouvez utiliser la méthode <xref:System.Threading.ThreadPool.GetMinThreads%2A?displayProperty=nameWithType> pour obtenir ces valeurs minimales.  
  
> [!NOTE]
> Quand la demande est faible, le nombre réel de threads du pool peut être inférieur aux valeurs minimales.  
  
Quand une valeur minimale est atteinte, le pool de threads peut créer des threads supplémentaires ou attendre que certaines tâches soient terminées. Le pool de threads crée et détruit les threads de travail afin d’optimiser le débit, qui est défini comme le nombre de tâches qui se terminent par unité de temps. Un nombre trop bas de threads peut ne pas permettre une utilisation optimale des ressources disponibles, tandis qu'un nombre trop élevé de threads peut augmenter les conflits de ressources.  
  
> [!CAUTION]
> Vous pouvez utiliser la méthode <xref:System.Threading.ThreadPool.SetMinThreads%2A?displayProperty=nameWithType> pour augmenter le nombre minimal de threads inactifs. Toutefois, une augmentation non nécessaire de ces valeurs peut entraîner des problèmes de performances. Si vous démarrez trop de tâches en même temps, celles-ci seront lentes. Dans la plupart des cas, le pool de threads sera plus performant avec son propre algorithme d'allocation de threads.  

## <a name="using-the-thread-pool"></a>Utilisation du pool de threads

Le moyen le plus simple d’utiliser le pool de threads consiste à utiliser la [bibliothèque parallèle de tâches (TPL)](../parallel-programming/task-parallel-library-tpl.md). Par défaut, les types de la bibliothèque parallèle de tâches, comme <xref:System.Threading.Tasks.Task> et <xref:System.Threading.Tasks.Task%601>, utilisent des threads de pool pour exécuter des tâches.

Vous pouvez également utiliser le pool de threads en appelant <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> à partir du code managé (ou [`ICorThreadpool::CorQueueUserWorkItem`](../../framework/unmanaged-api/hosting/icorthreadpool-corqueueuserworkitem-method.md) à partir du code non managé) et en passant un <xref:System.Threading.WaitCallback?displayProperty=nameWithType> délégué représentant la méthode qui exécute la tâche.

Une autre façon d’utiliser le pool de threads est de mettre en file d’attente des éléments de travail associés à une opération d’attente en utilisant la méthode <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> et en passant un <xref:System.Threading.WaitHandle?displayProperty=nameWithType> qui, quand il est signalé ou quand il a expiré, appelle la méthode représentée par le délégué <xref:System.Threading.WaitOrTimerCallback?displayProperty=nameWithType>. Les threads de pool sont utilisés pour appeler les méthodes de rappel.  

Pour obtenir des exemples, consultez les pages des API référencées.
  
## <a name="skipping-security-checks"></a>Ignorer les vérifications de sécurité

Le pool de threads fournit également les méthodes <xref:System.Threading.ThreadPool.UnsafeQueueUserWorkItem%2A?displayProperty=nameWithType> et <xref:System.Threading.ThreadPool.UnsafeRegisterWaitForSingleObject%2A?displayProperty=nameWithType>. Ces méthodes ne doivent être utilisées que si vous êtes certain que la pile de l'appelant n'a pas fait l'objet de vérifications de sécurité effectuées pendant l'exécution de la tâche mise en file d'attente. <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A?displayProperty=nameWithType> et <xref:System.Threading.ThreadPool.RegisterWaitForSingleObject%2A?displayProperty=nameWithType> capturent la pile de l'appelant, qui est fusionnée avec la pile du thread de pool quand le thread commence à exécuter une tâche. Si une vérification de sécurité est requise, la pile entière doit être vérifiée. Même si elle garantit une sécurité, cette vérification a un impact sur les performances.  

## <a name="when-not-to-use-thread-pool-threads"></a>Quand ne pas utiliser les threads de pool

Il existe plusieurs scénarios dans lesquels il est préférable de créer et de gérer vos propres threads au lieu d’utiliser des threads de pool :  
  
- Si vous devez utiliser un thread de premier plan.  
- Si un thread doit avoir une priorité particulière.  
- Si vous avez des tâches qui entraînent le blocage du thread pendant une longue durée. Le pool de threads possède un nombre maximal de threads. Un grand nombre de threads de pool bloqués pourrait donc empêcher le démarrage des tâches.  
- Vous devez placer les threads dans un thread unique cloisonné. Tous les threads <xref:System.Threading.ThreadPool> se trouvent dans le multithread cloisonné.  
- Vous avez besoin d'une identité stable associée au thread ou avez besoin de dédier un thread à une tâche.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.ThreadPool?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [Bibliothèque parallèle de tâches](../parallel-programming/task-parallel-library-tpl.md)
- [Procédure : retourner une valeur à partir d’une tâche](../parallel-programming/how-to-return-a-value-from-a-task.md)
- [Fonctionnalités et objets de threading](threading-objects-and-features.md)
- [Threads et threading](threads-and-threading.md)
- [E/s de fichier asynchrones](../io/asynchronous-file-i-o.md)
- [Minuteurs](timers.md)

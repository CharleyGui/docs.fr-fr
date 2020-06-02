---
title: Structures de données pour la programmation parallèle
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: f9c130b73044440f24b7b8bbebe9527490a165c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288522"
---
# <a name="data-structures-for-parallel-programming"></a>Structures de données pour la programmation parallèle
La version 4 de .NET Framework introduit de nouveaux types très utiles pour la programmation parallèle, notamment un ensemble de classes de collections simultanées, des primitives de synchronisation légères et des types pour l’initialisation tardive. Vous pouvez utiliser ces types avec n’importe quel code d’application multithread, y compris la bibliothèque parallèle de tâches et PLINQ.  
  
## <a name="concurrent-collection-classes"></a>Classes de collections simultanées  
 Les classes de collections de l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType> fournissent des opérations d’ajout et de suppression thread-safe qui évitent autant que possible les verrous et, là où ils se révèlent nécessaires, utilisent un verrouillage de granularité fine. Avec une classe de collections simultanées, contrairement aux collections introduites dans les versions 1.0 et 2.0 de .NET Framework, il n’est pas nécessaire que le code utilisateur prenne des verrous pour accéder aux éléments. Les classes de collections simultanées peuvent améliorer considérablement les performances des types comme <xref:System.Collections.ArrayList?displayProperty=nameWithType> et <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (avec verrouillage implémenté par l’utilisateur) dans le cas où plusieurs threads ajoutent et suppriment des éléments d’une collection.  
  
 Le tableau suivant liste les classes de collections simultanées :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Fournit des fonctions bloquantes et englobantes pour les collections thread-safe qui implémentent <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Les threads producteurs se bloquent si aucun emplacement n’est disponible ou que la collection est pleine. Les threads consommateurs se bloquent si la collection est vide. Ce type prend également en charge l’accès non bloquant par les producteurs et les consommateurs. <xref:System.Collections.Concurrent.BlockingCollection%601> peut être utilisé comme classe de base ou comme magasin de stockage pour assurer le blocage et la liaison des classes de collection qui prennent en charge <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Implémentation de conteneur thread-safe qui effectue des opérations Add et Get évolutives.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Type dictionnaire simultané et évolutif.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|File d’attente FIFO simultanée et évolutive.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Pile LIFO simultanée et évolutive.|  
  
 Pour plus d’informations, consultez [Collections thread-safe](../collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Primitives de synchronisation  
 Les nouvelles primitives de synchronisation de l’espace de noms <xref:System.Threading?displayProperty=nameWithType> affinent la concurrence et améliorent les performances en évitant les coûteux mécanismes de verrouillage du code multithread hérité. Certains des nouveaux types, par exemple, <xref:System.Threading.Barrier?displayProperty=nameWithType> et <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, ont pas d’équivalents dans les versions antérieures de .NET Framework.  
  
 Le tableau suivant liste les nouveaux types de synchronisation :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Permet à plusieurs threads de fonctionner en parallèle sur un algorithme en fournissant un point auquel chaque tâche peut signaler son arrivée, puis se bloquer jusqu'à ce qu’une partie ou la totalité des tâches soient arrivées. Pour plus d’informations, voir [Cloisonnement](../threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Simplifie les scénarios de duplication et de jointure en fournissant un mécanisme facile de réunion. Pour plus d'informations, consultez la page [CountdownEvent](../threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Primitive de synchronisation similaire à <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim> est léger mais n’est utilisable que pour la communication intraprocessus.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Primitive de synchronisation qui limite le nombre de threads pouvant accéder simultanément à une ressource ou à un pool de ressources. Pour plus d’informations, consultez la page [Semaphore et SemaphoreSlim](../threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Primitive de verrou mutex obligeant le thread qui essaie d’acquérir le verrou à attendre dans une boucle ou à rester en *attente active* pendant un certain temps avant de transmettre son quantum. Dans les scénarios où l’attente du verrou est censée être courte, <xref:System.Threading.SpinLock> offre de meilleures performances que les autres types de verrouillage. Pour plus d'informations, consultez la page [SpinLock](../threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Type petit et léger qui restera en attente active pendant un certain temps et mettra le thread dans un état d’attente si le nombre est dépassé.  Pour plus d'informations, consultez la page [SpinWait](../threading/spinwait.md).|  
  
 Pour plus d'informations, consultez les pages suivantes :  
  
- [Comment : utiliser le verrouillage SpinLock pour une synchronisation de bas niveau](../threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Comment : synchroniser des opérations simultanées avec un cloisonnement](../threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Classes d’initialisation tardive  
 Avec l’initialisation tardive, la mémoire d’un objet n’est pas allouée tant qu’elle n’est pas nécessaire. L’initialisation tardive peut améliorer les performances en répartissant uniformément les allocations d’objets sur toute la durée de vie d’un programme. Vous pouvez l’activer sur n’importe quel type personnalisé en incluant le type <xref:System.Lazy%601> dans un wrapper.  
  
 Le tableau suivant liste les nouveaux types d’initialisation tardive :  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Assure une initialisation tardive légère et thread-safe.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Fournit une valeur initialisée tardivement thread par thread, chacun appelant de façon tardive la fonction d’initialisation.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Fournit des méthodes statiques qui évitent d’avoir à allouer une instance dédiée d’initialisation tardive. Utilise plutôt des références pour vérifier que les cibles ont été initialisées lorsqu’elles sont consultées.|  
  
 Pour plus d’informations, consultez [Initialisation tardive](../../framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Agréger des exceptions  
 Le type <xref:System.AggregateException?displayProperty=nameWithType> permet de capturer plusieurs exceptions levées simultanément sur des threads distincts, et de les retourner au thread de jonction comme une seule exception. Les types <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ainsi que PLINQ utilisent beaucoup <xref:System.AggregateException> pour cela. Pour plus d’informations, consultez [Gestion des exceptions](exception-handling-task-parallel-library.md) et [Comment gérer des exceptions dans une requête PLINQ](how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Programmation parallèle](index.md)

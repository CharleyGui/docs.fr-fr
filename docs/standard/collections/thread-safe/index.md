---
title: Collections thread-safe
description: Prise en main des collections thread-safe à l’aide de l’espace de noms System. Collections. concurrent dans .NET, qui comprend des classes de collection à thread sécurisée et évolutives.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
ms.openlocfilehash: 27b0e887d7dcff6a6c792cf2dfab6a449f59646f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547686"
---
# <a name="thread-safe-collections"></a>Collections thread-safe
.NET Framework 4 introduit l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>, qui contient plusieurs classes de collection qui sont à la fois thread-safe et scalables. Plusieurs threads peuvent, sans risque et de façon efficace, ajouter ou supprimer des éléments dans ces collections, sans nécessiter une synchronisation supplémentaire dans le code utilisateur. Quand vous écrivez du code, utilisez des classes de collections simultanées si plusieurs threads écrivent en même temps dans la collection. Si vous lisez seulement dans une collection partagée, vous pouvez utiliser les classes de l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType>. Nous vous recommandons de ne pas utiliser les classes de collections 1.0, à moins que vous ne deviez cibler le runtime .NET Framework 1.1 ou une version antérieure.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>Synchronisation de threads dans les collections .NET Framework 1.0 et 2.0  
 Les collections introduites dans le .NET Framework 1.0 se trouvent dans l’espace de noms <xref:System.Collections?displayProperty=nameWithType>. Ces collections, qui incluent les <xref:System.Collections.ArrayList> et <xref:System.Collections.Hashtable> fréquemment utilisés, garantissent une certaine cohérence des threads par le biais de la propriété `Synchronized`, qui retourne un wrapper thread-safe autour de la collection. Le wrapper fonctionne en verrouillant l’ensemble de la collection à chaque opération d’ajout ou de suppression. Par conséquent, chaque thread qui tente d’accéder à la collection doit attendre son tour pour prendre le verrou. Ce fonctionnement n’est pas évolutif et peut provoquer une importante dégradation des performances pour les grandes collections. De même, la conception n’est pas complètement protégée contre la concurrence critique. Pour plus d’informations, consultez [Synchronisation dans les collections génériques](/archive/blogs/bclteam/synchronization-in-generic-collections-brian-grunkemeyer).  
  
 Les classes de collection introduites dans le .NET Framework 2.0 se trouvent dans l’espace de noms <xref:System.Collections.Generic?displayProperty=nameWithType>. Elles comprennent notamment <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602>, etc. Ces classes garantissent une cohérence des types et des performances améliorées par rapport aux classes du .NET Framework 1.0. Toutefois, les classes de collections .NET Framework 2.0 ne fournissent pas de synchronisation des threads. Le code utilisateur doit fournir toute la synchronisation quand des éléments sont ajoutés ou supprimés simultanément sur plusieurs threads.  
  
 Nous vous recommandons les classes de collections simultanées de .NET Framework 4, car elles offrent non seulement la cohérence des types des classes de collections .NET Framework 2.0, mais également une cohérence de thread plus efficace et plus complète que les collections .NET Framework 1.0.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Verrouillage de granularité fine et mécanismes sans verrou  
 Certains types de collections simultanées utilisent des mécanismes de synchronisation légers, comme <xref:System.Threading.SpinLock>, <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim> et <xref:System.Threading.CountdownEvent>, qui sont nouveaux dans .NET Framework 4. Ces types de synchronisation utilisent généralement la *rotation intensive* pendant de courtes périodes avant de mettre le thread dans un véritable état d’attente. Lorsque les temps d’attente sont supposés être très courts, la rotation est beaucoup moins gourmande en ressources informatiques que l’attente, qui implique une transition de noyau coûteuse. Pour les classes de collections qui utilisent la rotation, cette efficacité signifie que plusieurs threads peuvent ajouter et supprimer des éléments à un taux très élevé. Pour plus d'informations sur la rotation et le blocage, consultez [SpinLock](../../threading/spinlock.md) et [SpinWait](../../threading/spinwait.md).  
  
 Les classes <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601> n’utilisent pas de verrous du tout. Au lieu de cela, elles s’appuient sur des opérations <xref:System.Threading.Interlocked> pour assurer la cohérence des threads.  
  
> [!NOTE]
> Étant donné que les classes de collections simultanées prennent en charge <xref:System.Collections.ICollection>, elles fournissent des implémentations pour les propriétés <xref:System.Collections.ICollection.IsSynchronized%2A> et <xref:System.Collections.ICollection.SyncRoot%2A>, bien que ces propriétés ne soient pas pertinentes. `IsSynchronized` retourne toujours `false` et `SyncRoot` a toujours la valeur `null` (`Nothing` dans Visual Basic).  
  
 Le tableau suivant répertorie les types de collections dans l’espace de noms <xref:System.Collections.Concurrent?displayProperty=nameWithType>.  
  
|Type|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|Fournit des fonctionnalités de délimitation et de blocage pour tous les types qui implémentent <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>. Pour plus d’informations, consultez [Vue d’ensemble de BlockingCollection](blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Implémentation thread-safe d’un dictionnaire de paires clé-valeur.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Implémentation thread-safe d’une file d’attente FIFO (premier entré, premier sorti).|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Implémentation thread-safe d’une pile LIFO (dernier entré, premier sorti).|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Implémentation thread-safe d’une collection non ordonnée d’éléments.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Interface qu’un type doit implémenter pour être utilisé dans un `BlockingCollection`.|  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Vue d'ensemble de BlockingCollection](blockingcollection-overview.md)|Décrit la fonctionnalité fournie par le type <xref:System.Collections.Concurrent.BlockingCollection%601>.|  
|[Procédure : ajouter et supprimer des éléments d’un ConcurrentDictionary](how-to-add-and-remove-items.md)|Décrit comment ajouter et supprimer des éléments dans un <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.|  
|[Procédure : ajouter et prendre des éléments individuellement dans un BlockingCollection](how-to-add-and-take-items.md)|Décrit comment ajouter et récupérer des éléments dans une collection de blocage sans utiliser l’énumérateur en lecture seule.|  
|[Procédure : ajouter des fonctionnalités de délimitation et de blocage à une collection](how-to-add-bounding-and-blocking.md)|Décrit comment utiliser une classe de collection comme mécanisme de stockage sous-jacent pour une collection <xref:System.Collections.Concurrent.IProducerConsumerCollection%601>.|  
|[Procédure : utiliser la boucle ForEach pour supprimer les éléments d’un BlockingCollection](how-to-use-foreach-to-remove.md)|Décrit comment utiliser `foreach`, (`For Each` dans Visual Basic) pour supprimer tous les éléments d’une collection de blocage.|  
|[Procédure : utiliser des tableaux de collections de blocage dans un pipeline](how-to-use-arrays-of-blockingcollections.md)|Décrit comment utiliser simultanément plusieurs collections de blocage pour implémenter un pipeline.|  
|[Procédure : créer un pool d’objets à l’aide d’un ConcurrentBag](how-to-create-an-object-pool.md)|Montre comment utiliser un conteneur simultané pour améliorer les performances dans les scénarios où vous pouvez réutiliser des objets au lieu d’en créer continuellement de nouveaux.|  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>

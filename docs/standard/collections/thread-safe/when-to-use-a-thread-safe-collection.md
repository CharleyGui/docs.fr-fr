---
title: Quand utiliser une collection thread-safe
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
ms.openlocfilehash: 5a0abef6de9f932f44fc7e3239b98c3a27846580
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711218"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Quand utiliser une collection thread-safe
.NET Framework 4 propose cinq nouveaux types de collection spécialement conçus pour prendre en charge les opérations d’ajout et de suppression multithread. Pour garantir la cohérence de thread, ces nouveaux types utilisent différentes sortes de mécanismes de verrouillage et de synchronisation sans verrou efficaces. La synchronisation ajoute une surcharge à une opération. La quantité de la surcharge dépend du genre de synchronisation utilisé, du genre d’opérations exécutées et d’autres facteurs tels que le nombre de threads qui tentent d’accéder simultanément à la collection.  
  
 Dans certains scénarios, la surcharge de synchronisation est négligeable et permet au type multithread de s’exécuter beaucoup plus rapidement et d’évoluer beaucoup mieux que son équivalent qui n’est pas thread-safe quand il est protégé par un verrou externe. Dans d’autres scénarios, la surcharge peut entraîner une exécution et une scalabilité du type thread-safe à peu près identiques, ou même plus lentes, que celles de la version du type qui n’est pas thread-safe et qui est verrouillée de manière externe.  
  
 Les sections suivantes fournissent des recommandations générales concernant le moment où utiliser une collection thread-safe ou son équivalent non thread-safe qui a un verrou fourni par l’utilisateur autour de ses opérations de lecture et d’écriture. Étant donné que les performances peuvent varier en fonction de nombreux facteurs, ces recommandations ne sont pas spécifiques et ne sont pas nécessairement valables dans toutes les circonstances. Si les performances sont très importantes, la meilleure façon de déterminer le type de collection à utiliser consiste à mesurer les performances en fonction de configurations et de charges d’ordinateur représentatives. Ce document utilise les termes suivants :  
  
 *Scénario producteur-consommateur pur*  
 Tout thread donné ajoute ou supprime des éléments, mais pas les deux.  
  
 *Scénario producteur-consommateur mixte*  
 Tout thread donné ajoute et supprime des éléments.  
  
 *Accélération*  
 Performances algorithmiques plus rapides par rapport à un autre type dans le même scénario.  
  
 *Évolutivité*  
 Augmentation des performances proportionnelle au nombre de cœurs de l’ordinateur. Un algorithme évolutif s’exécute plus vite sur huit cœurs que sur deux cœurs.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs File d’attente(T)  
 Dans les scénarios producteur-consommateur purs, où le temps de traitement de chaque élément est très court (quelques instructions), <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> peut offrir des avantages modestes en matière de performances par rapport à un <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> qui a un verrou externe. Dans ce scénario, <xref:System.Collections.Concurrent.ConcurrentQueue%601> fonctionne mieux quand un thread dédié effectue la mise en file d’attente et qu’un autre thread dédié annule la mise en file d’attente. Si vous n’appliquez pas cette règle, <xref:System.Collections.Generic.Queue%601> peut même s’exécuter légèrement plus rapidement que <xref:System.Collections.Concurrent.ConcurrentQueue%601> sur les ordinateurs à plusieurs cœurs.  
  
 Quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, la règle de deux threads ne s’applique pas à <xref:System.Collections.Concurrent.ConcurrentQueue%601>, qui possède alors une très bonne scalabilité. <xref:System.Collections.Generic.Queue%601> n’évolue pas bien dans ce scénario.  
  
 Dans les scénarios producteur-consommateur mixtes, quand le temps de traitement est très court, un <xref:System.Collections.Generic.Queue%601> qui a un externe verrou évolue mieux que <xref:System.Collections.Concurrent.ConcurrentQueue%601>. Toutefois, quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, <xref:System.Collections.Concurrent.ConcurrentQueue%601> évolue mieux.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs Stack  
 Dans les scénarios producteur-consommateur purs, quand le temps de traitement est très court, <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> qui a un verrou externe s’exécuteront probablement de la même manière avec un thread d’exécution de type push dédié et un thread d’exécution de type pop dédié. Toutefois, à mesure que le nombre de threads augmente, les deux types ralentissent à cause de l’augmentation des conflits, et <xref:System.Collections.Generic.Stack%601> peut fonctionner mieux que <xref:System.Collections.Concurrent.ConcurrentStack%601>. Quand le temps de traitement est autour de 500 opérations en virgule flottante (FLOPS), ou plus, les deux types évoluent à peu près au même rythme.  
  
 Dans les scénarios producteur-consommateur mixtes, <xref:System.Collections.Concurrent.ConcurrentStack%601> est plus rapide à la fois pour les petites et les grandes charges de travail.  
  
 L’utilisation de <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> et de <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> peut accélérer considérablement les temps d’accès.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs Dictionnaire  
 En général, vous devez utiliser un <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> dans tout scénario où vous ajoutez et mettez à jour des clés ou des valeurs simultanément à partir de plusieurs threads. Dans les scénarios qui impliquent des mises à jour fréquentes et des lectures relativement peu nombreuses, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> offre généralement des avantages modestes. Dans les scénarios qui impliquent de nombreuses lectures et de nombreuses mises à jour, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> est généralement beaucoup plus rapide, quel que soit le nombre de cœurs des ordinateurs.  
  
 Dans les scénarios qui impliquent des mises à jour fréquentes, vous pouvez augmenter le degré d’accès concurrentiel dans <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, puis mesurer pour voir si les performances augmentent sur les ordinateurs qui ont plus de cœurs. Si vous modifiez le niveau d’accès concurrentiel, évitez, autant que possible, les opérations globales.  
  
 Si vous lisez uniquement une clé ou des valeurs, <xref:System.Collections.Generic.Dictionary%602> est plus rapide car aucune synchronisation n’est nécessaire si le dictionnaire n’est pas modifié par des threads.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Dans les scénarios producteur-consommateur purs, <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> s’exécutera probablement plus lentement que les autres types de collections simultanées.  
  
 Dans les scénarios producteur-consommateur mixtes, <xref:System.Collections.Concurrent.ConcurrentBag%601> est généralement beaucoup plus rapide et plus évolutif que les autres types de collections simultanées à la fois pour les petites et pour les grandes charges de travail.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Quand une sémantique de délimitation et de blocage est nécessaire, <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> s’exécutera probablement plus rapidement que toute implémentation personnalisée. Il prend également en charge une gestion enrichie des annulations, énumérations et exceptions.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Thread-Safe Collections](../../../../docs/standard/collections/thread-safe/index.md)
- [Programmation parallèle](../../../../docs/standard/parallel-programming/index.md)

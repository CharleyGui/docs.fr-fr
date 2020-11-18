---
title: Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
ms.openlocfilehash: 2268df2eb5cae4dcd7adde491b42c86c546aa1fc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829230"
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Partitionneurs personnalisés pour PLINQ et la bibliothèque parallèle de tâches (TPL)

Pour paralléliser une opération sur une source de données, l’une des étapes essentielles consiste à *partitionner* la source en plusieurs sections accessibles simultanément par plusieurs threads. PLINQ et la bibliothèque parallèle de tâches (TPL) fournissent des partitionneurs par défaut qui fonctionnent de façon transparente lorsque vous écrivez une requête parallèle ou une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A>. Pour des scénarios plus élaborés, vous pouvez incorporer votre propre partitionneur.

## <a name="kinds-of-partitioning"></a>Types de partitionnement

Il existe de nombreuses façons de partitionner une source de données. Dans les approches les plus efficaces, plusieurs threads coopèrent pour traiter la séquence source d’origine, au lieu de séparer physiquement la source en plusieurs sous-séquences. Pour des tableaux et d’autres sources indexées telles que des collections <xref:System.Collections.IList> où la longueur est connue à l’avance, le *partitionnement par plage de valeurs* est le type de partitionnement le plus simple. Chaque thread reçoit des index de début et de fin uniques pour pouvoir traiter sa plage de la source, sans remplacer ni être remplacé par un autre thread. La seule surcharge impliquée dans le partitionnement par plage de valeurs est le travail initial consistant à créer les plages : aucune synchronisation supplémentaire n’est requise par la suite. Par conséquent, cette méthode offre de bonnes performances tant que la charge de travail est répartie uniformément. L’inconvénient du partitionnement par plage de valeurs réside dans le fait que si un thread se termine plus tôt, il ne peut pas aider les autres threads à terminer leur travail.

Pour les listes liées ou d’autres collections dont la longueur n’est pas connue, vous pouvez utiliser le *partitionnement par segments*. Dans le partitionnement par segments, chaque thread ou tâche d’une boucle parallèle ou d’une requête consomme un certain nombre d’éléments de la source dans un segment, les traite, puis revient pour extraire des éléments supplémentaires. Le partitionneur s’assure que tous les éléments sont distribués et qu’il n’y a pas de doublons. Un segment peut être de n’importe quelle taille. Par exemple, le partitionneur présenté dans la section [Guide pratique pour implémenter des partitions dynamiques](how-to-implement-dynamic-partitions.md) crée des segments qui ne contiennent qu’un seul élément. Tant que les segments ne sont pas trop volumineux, ce type de partitionnement effectue, par nature, un équilibrage de charge car l’affectation des éléments aux threads n’est pas prédéfinie. Cependant, le partitionneur déclenche la surcharge de synchronisation chaque fois que le thread a besoin d’un autre segment. Le niveau de synchronisation effectué dans ce cas est inversement proportionnel à la taille des segments.

En règle générale, le partitionnement par plage de valeurs n’est plus rapide que lorsque la durée d’exécution du délégué est faible à modérée, que la source comporte un grand nombre d’éléments, et que le travail total de chaque partition est à peu près équivalent. Le partitionnement par segments est donc généralement plus rapide dans la plupart des cas. Sur les sources comportant un petit nombre d’éléments ou avec des durées d’exécution plus longues pour le délégué, les performances du partitionnement par plage de valeurs et du partitionnement par segments sont équivalentes.

Les partitionneurs TPL prennent également en charge un nombre dynamique de partitions. Cela signifie qu’ils peuvent créer des partitions à la volée, par exemple lorsque la boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A> génère une nouvelle tâche. Cette fonctionnalité permet la mise à l’échelle du partitionneur par rapport à la boucle elle-même. Par nature, les partitionneurs dynamiques effectuent également un équilibrage de charge. Lorsque vous créez un partitionneur personnalisé, vous devez faire en sortie que le partitionnement dynamique soit utilisable par une boucle <xref:System.Threading.Tasks.Parallel.ForEach%2A>.

### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Configuration des partitionneurs d’équilibrage de charge pour PLINQ

Certaines surcharges de la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> vous permettent de créer un partitionneur pour un tableau ou une source <xref:System.Collections.IList> et de spécifier s’il doit tenter d’équilibrer la charge de travail entre les threads. Lorsque le partitionneur est configuré pour l’équilibrage de charge, le partitionnement par segments est utilisé, et les éléments sont transmis, à la demande, par petits segments à chaque partition. Cette approche garantit que toutes les partitions disposent d’éléments à traiter jusqu'à ce que la boucle ou la requête soit terminée. Une surcharge supplémentaire peut être utilisée pour fournir le partitionnement d’équilibrage de charge de n’importe quelle source <xref:System.Collections.IEnumerable>.

En général, l’équilibrage de charge requiert que les partitions sollicitent fréquemment le partitionneur pour obtenir des éléments. En revanche, un partitionneur qui effectue un partitionnement statique peut affecter les éléments à chaque partitionneur en même temps à l’aide d’un partitionnement par plage de valeurs ou par segments. Cette méthode nécessite moins de surcharge que l’équilibrage de charge, mais elle peut prendre plus de temps à s’exécuter si un thread se retrouve avec beaucoup plus de travail que les autres. Par défaut, lorsqu’il reçoit un objet IList ou un tableau, PLINQ utilise toujours le partitionnement par plage de valeurs sans équilibrage de charge. Pour activer l’équilibrage de charge pour PLINQ, utilisez la méthode `Partitioner.Create`, comme indiqué dans l’exemple suivant.

[!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
[!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]

La meilleure méthode pour déterminer si vous devez utiliser l’équilibrage de charge dans un scénario donné consiste à faire des essais et à mesurer la durée des opérations avec des charges et des configurations d’ordinateur représentatives. Par exemple, le partitionnement statique peut accélérer considérablement les opérations sur un ordinateur multicœur doté de quelques cœurs, mais il peut entraîner des ralentissements sur les ordinateurs qui disposent de nombreux cœurs.

Le tableau ci-dessous répertorie les surcharges disponibles avec la méthode <xref:System.Collections.Concurrent.Partitioner.Create%2A>. L’utilisation de ces partitionneurs ne se limite pas à PLINQ ou à <xref:System.Threading.Tasks.Task>. Ils peuvent également être utilisés avec n’importe quelle construction parallèle personnalisée.

|Surcharge|Utiliser l'équilibrage de charge|
|--------------|-------------------------|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Toujours|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Lorsque l’argument booléen est spécifié comme true|
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Lorsque l’argument booléen est spécifié comme true|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Jamais|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Jamais|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Jamais|
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Jamais|

### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Configuration de partitionneurs de plages statiques pour Parallel.ForEach

Dans une boucle <xref:System.Threading.Tasks.Parallel.For%2A>, le corps de la boucle est transmis à la méthode en tant que délégué. Le coût d’un appel à ce délégué est équivalent à celui d’un appel à une méthode virtuelle. Dans certains scénarios, le corps d’une boucle parallèle peut être suffisamment petit de sorte que le coût d’un appel au délégué sur chaque itération de la boucle devient important. Dans ce cas, vous pouvez utiliser une des surcharges <xref:System.Collections.Concurrent.Partitioner.Create%2A> pour créer un objet <xref:System.Collections.Generic.IEnumerable%601> de partitions par plages de valeurs sur les éléments sources. Vous pouvez ensuite transmettre cette collection de plages de valeurs à une méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A> dont le corps se compose d’une boucle `for` standard. L’avantage de cette approche est que le coût d’un appel au délégué n’est généré qu’une seule fois par plage au lieu d’une seule fois par élément. L'exemple suivant illustre le modèle de base.

[!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
[!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]

Chaque thread de la boucle reçoit son propre objet <xref:System.Tuple%602>, qui contient les valeurs d’index de début et de fin dans la sous-plage spécifiée. La boucle `for` interne utilise les valeurs `fromInclusive` et `toExclusive` pour parcourir le tableau ou <xref:System.Collections.IList> directement.

Une des surcharges <xref:System.Collections.Concurrent.Partitioner.Create%2A> vous permet de spécifier la taille des partitions ainsi que leur nombre. Cette surcharge peut être utilisée dans des scénarios où le travail par élément est si faible que même un appel à une méthode virtuelle par élément a un impact perceptible sur les performances.

## <a name="custom-partitioners"></a>Partitionneurs personnalisés

Dans certains scénarios, il peut être utile ou même obligatoire d’implémenter votre propre partitionneur. Par exemple, vous pouvez partionner une classe de collection personnalisée plus efficacement qu’avec les partitionneurs par défaut, selon votre connaissance de la structure interne de la classe. Ou vous pouvez créer des partitions de plages de valeurs de tailles différentes en fonction du temps nécessaire pour traiter les éléments situés en différents emplacements de la collection source.

Pour créer un partitionneur personnalisé de base, dérivez une classe de <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> puis remplacez les méthodes virtuelles, comme décrit dans le tableau suivant.

|||
|-|-|
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un objet IList(IEnumerator(TSource)). Chaque thread de travail dans la boucle ou la requête peut appeler `GetEnumerator` sur la liste pour récupérer un objet <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retournez `true` si vous implémentez <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, et `false` dans le cas contraire.|
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|

Si les résultats doivent pouvoir être triés ou que vous avez besoin d’un accès indexé aux éléments, dérivez <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> et remplacez ses méthodes virtuelles, comme décrit dans le tableau suivant.

|||
|-|-|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Cette méthode est appelée une fois par le thread principal et retourne un objet `IList(IEnumerator(TSource))`. Chaque thread de travail dans la boucle ou la requête peut appeler `GetEnumerator` sur la liste pour récupérer un objet <xref:System.Collections.Generic.IEnumerator%601> sur une partition distincte.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retournez `true` si vous implémentez <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>, et false dans le cas contraire.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|En règle générale, cette méthode appelle simplement <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Si <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> est `true`, cette méthode peut éventuellement être appelée à la place de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|

Le tableau suivant fournit des détails supplémentaires sur la façon dont les trois types de partitionneurs d’équilibrage de charge implémentent la classe <xref:System.Collections.Concurrent.OrderablePartitioner%601>.

|Méthode/propriété|IList / tableau sans équilibrage de charge|IList / tableau avec équilibrage de charge|IEnumerable|
|----------------------|-------------------------------------------|----------------------------------------|-----------------|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Utilise le partitionnement par plages de valeurs|Utilise le partitionnement par segments, optimisé pour les listes, pour la valeur partitionCount spécifiée|Utilise le partitionnement par segments en créant un nombre statique de partitions.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Lève une exception non prise en charge|Utilise le partitionnement par segments, optimisé pour les listes, pour les partitions dynamiques|Utilise le partitionnement par segments en créant un nombre dynamique de partitions.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Retourne `true`.|Retourne `true`.|Retourne `true`.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Retourne `true`.|Retourne `false`.|Retourne `false`.|
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Retourne `true`.|Retourne `true`.|Retourne `true`.|
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retourne `false`.|Retourne `true`.|Retourne `true`.|

### <a name="dynamic-partitions"></a>Partitions dynamiques

Si vous envisagez d’utiliser le partitionneur dans une méthode <xref:System.Threading.Tasks.Parallel.ForEach%2A>, vous devez être en mesure de retourner un nombre dynamique de partitions. Cela signifie que le partitionneur peut fournir un énumérateur pour une nouvelle partition, à la demande et à tout moment pendant l’exécution de la boucle. En fait, chaque fois que la boucle ajoute une nouvelle tâche parallèle, elle demande une nouvelle partition pour cette tâche. Si vous avez besoin de pouvoir classer les données, effectuez une dérivation <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> afin d’affecter un index unique à chaque élément de chaque partition.

Pour plus d’informations et consulter un exemple, voir [Guide pratique pour implémenter des partitions dynamiques](how-to-implement-dynamic-partitions.md).

### <a name="contract-for-partitioners"></a>Contrat pour les partitionneurs

Lorsque vous implémentez un partitionneur personnalisé, suivez ces instructions pour garantir une interaction correcte avec PLINQ et <xref:System.Threading.Tasks.Parallel.ForEach%2A> dans la bibliothèque parallèle de tâches (TPL) :

- Si <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> est appelé avec un argument de zéro ou moins pour `partitionsCount`, levez <xref:System.ArgumentOutOfRangeException>. Bien que PLINQ et TPL ne fourniront jamais une valeur `partitionCount` égale à 0, nous vous recommandons néanmoins de vous prémunir contre ce risque.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> devraient toujours renvoyer un nombre de partitions équivalant à `partitionsCount`. Si le partitionneur manque de données et ne peut pas créer autant de partitions que demandé, la méthode devrait retourner un énumérateur vide pour chacune des partitions restantes. Sinon, PLINQ et TPL lèveront une <xref:System.InvalidOperationException>.

- <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, et <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> ne devraient jamais retourner `null` (`Nothing` en Visual Basic). Si tel est le cas, PLINQ/TPL lèveront une <xref:System.InvalidOperationException>.

- Les méthodes qui retournent des partitions devraient toujours renvoyer des partitions capables d’énumérer totalement et de manière unique la source de données. Il ne devrait y avoir aucune duplication dans la source de données ou les éléments ignorés, sauf si cela est spécifiquement requis par la conception du partitionneur. Si cette règle n’est pas suivie, l’ordre de sortie peut être brouillé.

- Les accesseurs booléens suivants doivent toujours retourner correctement les valeurs ci-dessous afin que l’ordre de sortie ne soit pas brouillé :

  - `KeysOrderedInEachPartition` : chaque partition retourne des éléments en augmentant les index clés.

  - `KeysOrderedAcrossPartitions` : pour toutes les partitions retournées, les index clés dans la partition *i* sont plus élevés que les index clés de la partition *i*-1.

  - `KeysNormalized`: tous les index clés augmentent de monotone, sans écarts, à partir de zéro.

- Tous les index doivent être uniques. Il ne doit pas y avoir de doublons. Si cette règle n’est pas suivie, l’ordre de sortie peut être brouillé.

- Tous les index doivent être non négatifs. Si cette règle n’est pas suivie, PLINQ/TPL peuvent lever des exceptions.

## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](index.md)
- [Procédure : implémenter des partitions dynamiques](how-to-implement-dynamic-partitions.md)
- [Procédure : implémenter un partitionneur pour un partitionnement statique](how-to-implement-a-partitioner-for-static-partitioning.md)

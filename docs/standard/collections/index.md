---
title: Collections et structures de données
description: Découvrez comment utiliser les collections et les structures de données dans .NET. Utilisez des collections génériques et non génériques dans des opérations thread-safe.
ms.date: 04/30/2020
helpviewer_keywords:
- grouping data in collections
- objects [.NET], grouping in collections
- Array class, grouping data in collections
- threading [.NET], safety
- Collections classes
- collections [.NET]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
ms.openlocfilehash: 7400d460c4d1ebf5c02d8313f33a5a63de1734d4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733514"
---
# <a name="collections-and-data-structures"></a>Collections et structures de données

Des données similaires peuvent souvent être gérées plus efficacement quand elles sont stockées et manipulées en tant que collection. Vous pouvez utiliser la <xref:System.Array?displayProperty=nameWithType> classe ou les classes des <xref:System.Collections> espaces de <xref:System.Collections.Generic> noms,, <xref:System.Collections.Concurrent> et <xref:System.Collections.Immutable> pour ajouter, supprimer et modifier des éléments individuels ou une plage d’éléments dans une collection.

Il existe deux principaux types de collections : les collections génériques et non génériques. Les collections génériques sont de type sécurisé au moment de la compilation. Pour cette raison, les collections génériques offrent généralement de meilleures performances. Les collections génériques acceptent un paramètre de type lorsqu'elles sont construites, et ne nécessitent pas de transtypage du type <xref:System.Object> quand vous ajoutez ou supprimez des éléments de la collection.  En outre, la plupart des collections génériques sont prises en charge dans les applications du Windows Store. Les collections non génériques stockent des éléments en tant que <xref:System.Object> , nécessitent un cast et la plupart ne sont pas prises en charge pour le développement d’applications du Windows Store. Cependant, vous pouvez rencontrer ces collections non génériques dans du code plus ancien.

À partir de .NET Framework 4, les collections de l' <xref:System.Collections.Concurrent> espace de noms fournissent des opérations thread-safe efficaces pour accéder aux éléments de collection à partir de plusieurs threads. Les classes de collection immuables de l' <xref:System.Collections.Immutable> espace de noms ([package NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) sont thread-safe, car les opérations sont effectuées sur une copie de la collection d’origine et la collection d’origine ne peut pas être modifiée.

<a name="BKMK_Commoncollectionfeatures"></a>

## <a name="common-collection-features"></a>Fonctionnalités communes à toutes les collections

Toutes les collections fournissent des méthodes pour l’ajout, la suppression ou la recherche d’éléments dans la collection. De plus, toutes les collections qui implémentent directement ou indirectement l'interface <xref:System.Collections.ICollection> ou <xref:System.Collections.Generic.ICollection%601> partagent les fonctionnalités suivantes :

- **Possibilité d’énumérer la collection**

    Les collections .NET implémentent <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> pour permettre l’itération de la collection. Un énumérateur peut être vu comme un pointeur mobile pointant vers n'importe quel élément d'une collection. L’instruction [foreach, in](../../csharp/language-reference/keywords/foreach-in.md) et [For Each...Next Instruction](../../visual-basic/language-reference/statements/for-each-next-statement.md) utilisent l’énumérateur exposé par la méthode <xref:System.Collections.IEnumerable.GetEnumerator%2A> et masquent la complexité de la manipulation de l’énumérateur. En outre, toute collection qui implémente <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> est considérée comme étant un *type requêtable* et peut être interrogée avec LINQ. Les requêtes LINQ fournissent un modèle commun d'accès aux données. Elles sont généralement plus concises et lisibles que les boucles `foreach` standard, et fournissent des fonctionnalités de filtrage, de tri et de regroupement. Les requêtes LINQ peuvent également améliorer les performances. Pour plus d’informations, consultez [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), [Introduction aux requêtes LINQ (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) et [Opérations de requête de base (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).

- **Possibilité de copier le contenu d’une collection dans un tableau**

    Toutes les collections peuvent être copiées dans un tableau à l'aide de la méthode **CopyTo**. Toutefois, l'ordre des éléments du nouveau tableau sera basé sur l'ordre où ils sont retournés par l'énumérateur. Le tableau résultant est toujours unidimensionnel avec une limite inférieure de zéro.

De plus, de nombreuses classes de collection comprennent les fonctionnalités suivantes :

- **Propriétés Capacity et Count**

    La propriété Capacity d'une collection indique le nombre d'éléments qu'elle peut contenir. La propriété Count d'une collection indique le nombre d'éléments qu'elle contient réellement. Certaines collections masquent l'une de ces propriétés, voire les deux.

    La capacité de la plupart des collections s'étend automatiquement quand la valeur de la propriété Capacity est atteinte. La mémoire est réallouée et les éléments sont copiés depuis l'ancienne collection vers la nouvelle. Cela permet de réduire le code nécessaire à l'utilisation de la collection. Toutefois, les performances de la collection peuvent être affectées. Par exemple, pour <xref:System.Collections.Generic.List%601> , si <xref:System.Collections.Generic.List%601.Count%2A> est inférieur à <xref:System.Collections.Generic.List%601.Capacity%2A> , l’ajout d’un élément est une opération O (1). Si la capacité doit être augmentée pour s’adapter au nouvel élément, l’ajout d’un élément devient une opération O ( `n` ), où `n` est <xref:System.Collections.Generic.List%601.Count%2A> . Le meilleur moyen d'éviter la dégradation des performances en raison des réallocations est de définir la propriété Capacity sur la taille estimée de la collection.

    <xref:System.Collections.BitArray> est un cas particulier. Sa capacité est égale à sa longueur, qui est elle-même égale à son nombre.

- **Limite inférieure cohérente**

    La limite inférieure d'une collection est l'index de son premier élément. Toutes les collections indexées dans l'espace de noms <xref:System.Collections> ont une limite inférieure de zéro, ce qui signifie qu'elles sont indexées à 0. <xref:System.Array> a une limite inférieure de zéro par défaut, mais une limite inférieure différente peut être définie lors de la création d’une instance de la classe **Array** à l’aide de <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> .

- **Synchronisation pour l’accès à partir de plusieurs threads** ( <xref:System.Collections> classes uniquement).

    Les types de collections non génériques de l'espace de noms <xref:System.Collections> fournissent une certaine cohérence de thread pour la synchronisation, généralement exposée par des membres <xref:System.Collections.ICollection.SyncRoot%2A> et <xref:System.Collections.ICollection.IsSynchronized%2A>. Ces collections ne sont pas thread-safe par défaut. Si vous avez besoin d'un accès multithread évolutif et efficace pour une collection, utilisez l'une des classes de l'espace de noms <xref:System.Collections.Concurrent> ou envisagez d'utiliser une collection immuable. Pour plus d’informations, consultez [Collections thread-safe](thread-safe/index.md).

<a name="BKMK_Choosingacollection"></a>

## <a name="choose-a-collection"></a>Choisir un regroupement

En règle générale, vous devez utiliser des collections génériques. Le tableau suivant décrit certains scénarios courants concernant les collections, ainsi que les classes de collection que vous pouvez utiliser pour ces scénarios. Si vous ne connaissez pas encore les collections génériques, ce tableau vous aidera à choisir la collection générique qui répond le mieux à vos besoins.

|Je souhaite :|Options de collection générique|Options de collection non générique|Options de collection thread-safe ou immuable|
|-|-|-|-|
|Stocker les éléments sous forme de paires clé/valeur pour une recherche rapide par clé|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Collection de paires clé/valeur organisées en fonction du code de hachage de la clé).|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|
|Accéder aux éléments par index|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|
|Utiliser des éléments premier entré, premier sorti (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|
|Utiliser des données dernier entré, premier sorti (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|
|Accéder aux éléments de manière séquentielle|<xref:System.Collections.Generic.LinkedList%601>|Aucune recommandation|Aucune recommandation|
|Recevoir des notifications quand des éléments sont supprimés ou ajoutés à la collection. (implémente <xref:System.ComponentModel.INotifyPropertyChanged> et <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Aucune recommandation|Aucune recommandation|
|Collection triée|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|
|Ensemble de fonctions mathématiques|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Aucune recommandation|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|

### <a name="algorithmic-complexity-of-collections"></a>Complexité algorithmique des collections

Lors du choix d’une [classe de collection](selecting-a-collection-class.md), il convient d’envisager des compromis potentiels en matière de performances. Utilisez le tableau suivant pour référencer la manière dont les différents types de collections mutables sont comparés dans la complexité algorithmique à leurs équivalents immuables correspondants. Souvent, les types de collections immuables sont moins performants, mais fournissent une immuabilité, ce qui est souvent un avantage comparatif valide.

| Mutable                   | Amorti  | Pire des cas                | Non modifiable                          | Complexité |
|---------------------------|------------|---------------------------|------------------------------------|------------|
| `Stack<T>.Push`           | O (1)       | O ( `n` )                    | `ImmutableStack<T>.Push`           | O (1)       |
| `Queue<T>.Enqueue`        | O (1)       | O ( `n` )                    | `ImmutableQueue<T>.Enqueue`        | O (1)       |
| `List<T>.Add`             | O (1)       | O ( `n` )                    | `ImmutableList<T>.Add`             | O (journal `n` ) |
| `List<T>.Item[Int32]`     | O (1)       | O (1)                      | `ImmutableList<T>.Item[Int32]`     | O (journal `n` ) |
| `List<T>.Enumerator`      | O ( `n` )     | O ( `n` )                    | `ImmutableList<T>.Enumerator`      | O ( `n` )     |
| `HashSet<T>.Add`, recherche  | O (1)       | O ( `n` )                    | `ImmutableHashSet<T>.Add`          | O (journal `n` ) |
| `SortedSet<T>.Add`        | O (journal `n` ) | O ( `n` )                    | `ImmutableSortedSet<T>.Add`        | O (journal `n` ) |
| `Dictionary<T>.Add`       | O (1)       | O ( `n` )                    | `ImmutableDictionary<T>.Add`       | O (journal `n` ) |
| `Dictionary<T>` directes    | O (1)       | O (1) – ou strictement O ( `n` ) | `ImmutableDictionary<T>` directes    | O (journal `n` ) |
| `SortedDictionary<T>.Add` | O (journal `n` ) | O ( `n` journal `n` )            | `ImmutableSortedDictionary<T>.Add` | O (journal `n` ) |

Un `List<T>` peut être énuméré efficacement à l’aide d’une boucle `for` ou d’une `foreach` boucle. `ImmutableList<T>`Toutefois, un travail mal fait à l’intérieur d' `for` une boucle, en raison de l’heure O (log `n` ) de son indexeur. L’énumération d’une `ImmutableList<T>` boucle à l’aide d’une `foreach` boucle est efficace, car `ImmutableList<T>` utilise une arborescence binaire pour stocker ses données au lieu d’un tableau simple comme les `List<T>` utilisations. Un tableau peut être indexé très rapidement dans, tandis qu’une arborescence binaire doit être parcourue jusqu’à ce que le nœud avec l’index souhaité soit trouvé.

En outre, `SortedSet<T>` a la même complexité que `ImmutableSortedSet<T>` . En effet, ils utilisent tous deux des arborescences binaires. La différence significative est évidemment que `ImmutableSortedSet<T>` utilise une arborescence binaire immuable. Étant donné que `ImmutableSortedSet<T>` offre également une <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder?displayProperty=nameWithType> classe qui permet la mutation, vous pouvez avoir à la fois une immuabilité et des performances.

<a name="BKMK_RelatedTopics"></a>

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Sélection d’une classe de collection](selecting-a-collection-class.md)|Décrit les différentes collections et permet d'en sélectionner une pour votre scénario.|
|[Types de collections couramment utilisés](commonly-used-collection-types.md)|Décrit les types de collection génériques et non génériques fréquemment utilisés, tels que <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|
|[Quand utiliser des collections génériques](when-to-use-generic-collections.md)|Traite de l'utilisation des types de collections génériques.|
|[Comparaisons et tris dans les collections](comparisons-and-sorts-within-collections.md)|Aborde l'utilisation des comparaisons d'égalité et de tri dans les collections.|
|[Types de collections triées](sorted-collection-types.md)|Aborde les caractéristiques et les performances des collections triées.|
|[Types de collections Hashtable et Dictionary](hashtable-and-dictionary-collection-types.md)|Décrit les fonctionnalités des types de dictionnaires basés sur le hachage génériques et non génériques.|
|[Collections thread-safe](thread-safe/index.md)|Décrit les types de collections tels que <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> et <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> qui prennent en charge l'accès simultané sécurisé et efficace de plusieurs threads.|
|System.Collections.Immutable|Présente les collections immuables et fournit des liens vers les types de collection.|

<a name="BKMK_Reference"></a>

## <a name="reference"></a>Informations de référence

<xref:System.Array?displayProperty=nameWithType>
<xref:System.Collections?displayProperty=nameWithType>
<xref:System.Collections.Concurrent?displayProperty=nameWithType>
<xref:System.Collections.Generic?displayProperty=nameWithType>
<xref:System.Collections.Specialized?displayProperty=nameWithType>
<xref:System.Linq?displayProperty=nameWithType>
<xref:System.Collections.Immutable>

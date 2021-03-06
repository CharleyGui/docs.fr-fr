---
title: Quand utiliser les collections génériques
ms.date: 04/30/2020
helpviewer_keywords:
- collections [.NET], generic
- generic collections [.NET]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 7b8b7b458a1667a1d3239ef378c729929678e8aa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733072"
---
# <a name="when-to-use-generic-collections"></a>Quand utiliser les collections génériques

L’utilisation de collections génériques vous offre l’avantage automatique de la cohérence des types sans avoir à dériver d’un type de collection de base et à implémenter des membres spécifiques au type. Les types de collections génériques sont généralement plus performants que les types de collections non génériques correspondants (et mieux que les types dérivés de types de collections de base non génériques) quand les éléments de la collection sont des types valeur, car avec les génériques, il n’est pas nécessaire de définir un cadre pour les éléments.

Pour les programmes qui ciblent .NET Standard 1,0 ou une version ultérieure, utilisez les classes de collection génériques dans l' <xref:System.Collections.Concurrent> espace de noms lorsque plusieurs threads peuvent ajouter ou supprimer simultanément des éléments de la collection. En outre, lorsque l’immuabilité est souhaitée, tenez compte des classes de collection génériques dans l' <xref:System.Collections.Immutable> espace de noms.

Les types génériques suivants correspondent à des types de collections existants :

- <xref:System.Collections.Generic.List%601> est la classe générique qui correspond à <xref:System.Collections.ArrayList>.

- <xref:System.Collections.Generic.Dictionary%602> et <xref:System.Collections.Concurrent.ConcurrentDictionary%602> sont les classes génériques qui correspondent à <xref:System.Collections.Hashtable>.

- <xref:System.Collections.ObjectModel.Collection%601> est la classe générique qui correspond à <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> peut être utilisé comme classe de base, mais contrairement <xref:System.Collections.CollectionBase> à, il n’est pas abstrait, ce qui le rend beaucoup plus facile à utiliser.

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> est la classe générique qui correspond à <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> n’est pas abstraite et possède un constructeur qui facilite l’exposition d’un existant <xref:System.Collections.Generic.List%601> en tant que collection en lecture seule.

- Les classes génériques,,,, <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Immutable.ImmutableQueue%601> <xref:System.Collections.Immutable.ImmutableArray%601> <xref:System.Collections.Generic.SortedList%602> et <xref:System.Collections.Immutable.ImmutableSortedSet%601> correspondent aux classes non génériques respectives portant le même nom.

## <a name="additional-types"></a>Autres types

Plusieurs types de collections génériques n'ont pas d'équivalents non génériques. Il s'agit des dossiers suivants :

- <xref:System.Collections.Generic.LinkedList%601> est une liste liée à usage général qui fournit des opérations d'insertion et de suppression O(1).

- <xref:System.Collections.Generic.SortedDictionary%602> est un dictionnaire trié avec des opérations d'insertion et d'extraction O(log `n`), ce qui en fait une alternative pratique à <xref:System.Collections.Generic.SortedList%602>.

- <xref:System.Collections.ObjectModel.KeyedCollection%602> est un hybride entre une liste et un dictionnaire qui permet de stocker des objets qui contiennent leurs propres clés.

- <xref:System.Collections.Concurrent.BlockingCollection%601> implémente une classe de collection avec une fonctionnalité d'englobement et de blocage.

- <xref:System.Collections.Concurrent.ConcurrentBag%601> permet une insertion et une suppression rapides des éléments non triés.

### <a name="immutable-builders"></a>Générateurs immuables

Quand vous souhaitez une fonctionnalité d’immuabilité dans votre application, l' <xref:System.Collections.Immutable> espace de noms offre des types de collections génériques que vous pouvez utiliser. Tous les types de collections immuables offrent des `Builder` classes qui peuvent optimiser les performances lorsque vous effectuez plusieurs mutations. La `Builder` classe traite les opérations dans un État mutable. Une fois toutes les mutations terminées, appelez la `ToImmutable` méthode pour « figer » tous les nœuds et créer une collection générique immuable, par exemple, <xref:System.Collections.Immutable.ImmutableList%601> .

L' `Builder` objet peut être créé en appelant la méthode non générique `CreateBuilder()` . À partir d’une `Builder` instance, vous pouvez appeler `ToImmutable()` . De même, à partir de la `Immutable*` collection, vous pouvez appeler `ToBuilder()` pour créer une instance de générateur à partir de la collection immuable générique. Les différents types sont les suivants `Builder` .

- <xref:System.Collections.Immutable.ImmutableArray%601.Builder>
- <xref:System.Collections.Immutable.ImmutableDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableHashSet%601.Builder>
- <xref:System.Collections.Immutable.ImmutableList%601.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder>

## <a name="linq-to-objects"></a>LINQ to Objects

La fonctionnalité LINQ to Objects permet d'utiliser des requêtes LINQ pour accéder aux objets en mémoire tant que le type d'objet implémente l'interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> . Les requêtes LINQ fournissent un modèle commun pour accéder aux données ; sont généralement plus concises et lisibles que les boucles standard, `foreach` et fournissent des fonctionnalités de filtrage, de classement et de regroupement. Les requêtes LINQ peuvent également améliorer les performances. Pour plus d’informations, consultez [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) et [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="additional-functionality"></a>Autres fonctionnalités

Certains types génériques ont des fonctionnalités que n'ont pas les types de collections non génériques. Par exemple, la classe <xref:System.Collections.Generic.List%601> , qui correspond à la classe non générique <xref:System.Collections.ArrayList> , possède plusieurs méthodes acceptant des délégués génériques, telles que le délégué <xref:System.Predicate%601> qui permet de spécifier des méthodes pour effectuer des recherches dans la liste, le délégué <xref:System.Action%601> , qui représente des méthodes qui agissent sur chaque élément de la liste, et le délégué <xref:System.Converter%602> qui permet de définir des conversions de types.

La classe <xref:System.Collections.Generic.List%601> permet de spécifier vos propres implémentations d'interface générique <xref:System.Collections.Generic.IComparer%601> pour trier et parcourir des listes. Les classes <xref:System.Collections.Generic.SortedDictionary%602> et <xref:System.Collections.Generic.SortedList%602> possèdent également cette fonctionnalité. De plus, ces classes permettent de spécifier des comparateurs au moment de la création de la collection. De la même façon, les classes <xref:System.Collections.Generic.Dictionary%602> et <xref:System.Collections.ObjectModel.KeyedCollection%602> permettent de spécifier vos propres comparateurs d'égalité.

## <a name="see-also"></a>Voir aussi

- [Collections et structures de données](index.md)
- [Types de collections couramment utilisés](commonly-used-collection-types.md)
- [Génériques](../generics/index.md)

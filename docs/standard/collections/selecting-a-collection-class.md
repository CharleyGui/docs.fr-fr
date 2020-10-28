---
title: Sélection d’une classe de collection
description: Découvrez comment choisir la classe de collection de .NET à choisir. L’utilisation d’un type incorrect peut limiter votre utilisation de la collection.
ms.date: 03/18/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
ms.openlocfilehash: 2a3615d5bb404247ec9280ff3c88e2c10a75768b
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889333"
---
# <a name="selecting-a-collection-class"></a>Sélection d’une classe de collection

Veillez à choisir votre classe de collection avec soin. L’utilisation d’un type incorrect peut limiter votre utilisation de la collection.

> [!IMPORTANT]
> Éviter d’utiliser les types dans l’espace de noms <xref:System.Collections>. Les versions génériques et simultanées des collections sont recommandées en raison de la sécurité supérieure des types et d'autres améliorations.

Posez-vous les questions suivantes :

- Avez-vous besoin d'une liste séquentielle où l'élément est en général abandonné une fois sa valeur récupérée ?

  - Si oui, envisagez d'utiliser la classe <xref:System.Collections.Queue> ou bien la classe générique <xref:System.Collections.Generic.Queue%601> si vous avez besoin d'un comportement premier entré, premier sorti (FIFO, First-In, First-Out). Envisagez d'utiliser la classe <xref:System.Collections.Stack> ou bien la classe générique <xref:System.Collections.Generic.Stack%601> si vous avez besoin d'un comportement dernier entré, premier sorti (LIFO, Last-In, First-Out). Pour un accès sécurisé à partir de plusieurs threads, utilisez les versions simultanées <xref:System.Collections.Concurrent.ConcurrentQueue%601> et <xref:System.Collections.Concurrent.ConcurrentStack%601>. Pour l’immuabilité, prenez en compte les versions immuables, <xref:System.Collections.Immutable.ImmutableQueue%601> et <xref:System.Collections.Immutable.ImmutableStack%601> .

  - Si ce n'est pas le cas, envisagez d'utiliser les autres collections.

- Avez-vous besoin d'accéder aux éléments dans un certain ordre, comme FIFO ou LIFO, ou de façon aléatoire ?

  - La <xref:System.Collections.Queue> classe, ainsi que les <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> classes génériques, et <xref:System.Collections.Immutable.ImmutableQueue%601> offrent tous l’accès FIFO. Pour plus d’informations, consultez [Quand utiliser une collection thread-safe](thread-safe/when-to-use-a-thread-safe-collection.md).

  - La <xref:System.Collections.Stack> classe, ainsi que les <xref:System.Collections.Generic.Stack%601> <xref:System.Collections.Concurrent.ConcurrentStack%601> classes génériques, et <xref:System.Collections.Immutable.ImmutableStack%601> offrent tous l’accès LIFO. Pour plus d’informations, consultez [Quand utiliser une collection thread-safe](thread-safe/when-to-use-a-thread-safe-collection.md).

  - La classe générique <xref:System.Collections.Generic.LinkedList%601> autorise un accès séquentiel de haut en bas ou de bas en haut.

- Avez-vous besoin d'accéder à chaque élément selon son index ?

  - Les classes <xref:System.Collections.ArrayList> et <xref:System.Collections.Specialized.StringCollection>, ainsi que la classe générique <xref:System.Collections.Generic.List%601>, offrent un accès à leurs éléments via l'index de base zéro de l'élément. Pour l’immuabilité, prenez en compte les versions génériques immuables, <xref:System.Collections.Immutable.ImmutableArray%601> et <xref:System.Collections.Immutable.ImmutableList%601> .

  - Les classes <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary> et <xref:System.Collections.Specialized.StringDictionary>, ainsi que les classes génériques <xref:System.Collections.Generic.Dictionary%602> et <xref:System.Collections.Generic.SortedDictionary%602>, offrent un accès à leurs éléments via la clé de l'élément. En outre, il existe des versions immuables de plusieurs types correspondants : <xref:System.Collections.Immutable.ImmutableHashSet%601> , <xref:System.Collections.Immutable.ImmutableDictionary%602> , <xref:System.Collections.Immutable.ImmutableSortedSet%601> et <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

  - Les classes <xref:System.Collections.Specialized.NameObjectCollectionBase> et <xref:System.Collections.Specialized.NameValueCollection>, ainsi que les classes génériques <xref:System.Collections.ObjectModel.KeyedCollection%602> et <xref:System.Collections.Generic.SortedList%602>, offrent un accès à leurs éléments via l'index de base zéro ou via la clé de l'élément.

- Chaque élément contiendra-t-il une valeur, une combinaison d'une clé et d'une valeur, ou une combinaison d'une clé et de plusieurs valeurs ?

  - Une valeur : utilisez une des collections basées sur l'interface <xref:System.Collections.IList> ou l'interface générique  <xref:System.Collections.Generic.IList%601>. Pour une option immuable, considérez l' <xref:System.Collections.Immutable.IImmutableList%601> interface générique.

  - Une clé et une valeur : utilisez une des collections basées sur l'interface <xref:System.Collections.IDictionary> ou l'interface générique  <xref:System.Collections.Generic.IDictionary%602>. Pour une option immuable, prenez en compte <xref:System.Collections.Immutable.IImmutableSet%601> les <xref:System.Collections.Immutable.IImmutableDictionary%602> interfaces génériques ou.

  - Une valeur avec une clé incorporée : utilisez la classe générique <xref:System.Collections.ObjectModel.KeyedCollection%602>.

  - Une clé et plusieurs valeurs : utilisez la classe <xref:System.Collections.Specialized.NameValueCollection>.

- Avez-vous besoin de trier les éléments différemment de la façon dont ils ont été entrés ?

  - La classe <xref:System.Collections.Hashtable> trie ses éléments selon leur code de hachage.

  - La classe <xref:System.Collections.SortedList> et les classes génériques <xref:System.Collections.Generic.SortedList%602> et <xref:System.Collections.Generic.SortedDictionary%602> trient leurs éléments par clé. L’ordre de tri est basé sur l’implémentation de l’interface <xref:System.Collections.IComparer> pour la classe <xref:System.Collections.SortedList> et sur l’implémentation de l’interface générique <xref:System.Collections.Generic.IComparer%601> pour les classes génériques <xref:System.Collections.Generic.SortedList%602> et <xref:System.Collections.Generic.SortedDictionary%602>. Des deux types génériques, c’est <xref:System.Collections.Generic.SortedDictionary%602> qui offre de meilleures performances que <xref:System.Collections.Generic.SortedList%602>, tandis que <xref:System.Collections.Generic.SortedList%602> consomme moins de mémoire.

  - <xref:System.Collections.ArrayList> fournit une méthode <xref:System.Collections.ArrayList.Sort%2A> qui prend une implémentation de <xref:System.Collections.IComparer> comme paramètre. Sa contrepartie générique, la classe générique <xref:System.Collections.Generic.List%601>, fournit une méthode <xref:System.Collections.Generic.List%601.Sort%2A> qui prend une implémentation de l'interface générique <xref:System.Collections.Generic.IComparer%601> comme paramètre.

- Avez-vous besoin de recherches et d'une récupération rapides des informations ?

  - <xref:System.Collections.Specialized.ListDictionary> est plus rapide que <xref:System.Collections.Hashtable> pour les petites collections (10 éléments ou moins). La classe générique <xref:System.Collections.Generic.Dictionary%602> permet une recherche plus rapide que celle de la classe générique <xref:System.Collections.Generic.SortedDictionary%602>. L'implémentation multithread est <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> fournit une insertion multithread rapide pour les données non ordonnées. Pour plus d’informations sur les deux types multithread, consultez [Quand utiliser une collection thread-safe](thread-safe/when-to-use-a-thread-safe-collection.md).

- Avez-vous besoin de collections qui acceptent seulement des chaînes ?

  - <xref:System.Collections.Specialized.StringCollection> (basée sur <xref:System.Collections.IList>) et <xref:System.Collections.Specialized.StringDictionary> (basée sur <xref:System.Collections.IDictionary>) se trouvent dans l'espace de noms <xref:System.Collections.Specialized>.

  - En outre, vous pouvez utiliser toutes les classes de collection génériques dans l'espace de noms <xref:System.Collections.Generic> comme des collections de chaînes fortement typées en spécifiant la classe <xref:System.String> pour leurs arguments de types génériques. Par exemple, vous pouvez déclarer une variable comme étant de type [List \<String> ](xref:System.Collections.Generic.List%601) ou [dictionary<String, String>](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects et PLINQ

La fonctionnalité LINQ to Objects permet aux développeurs d'utiliser des requêtes LINQ pour accéder aux objets en mémoire pour autant que le type d'objet implémente <xref:System.Collections.IEnumerable> ou <xref:System.Collections.Generic.IEnumerable%601>. Les requêtes LINQ fournissent un modèle commun pour accéder aux données. Elles sont généralement plus concises et plus lisibles que les boucles `foreach` standard et offrent des fonctions de filtrage, de classement et de regroupement. Pour plus d’informations, consultez [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) et [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLINQ fournit une implémentation parallèle de LINQ to Objects, qui peut offrir une exécution plus rapide des requêtes dans de nombreux scénarios, via une utilisation plus efficace des ordinateurs multicœurs. Pour plus d’informations, consultez [PLINQ (Parallel LINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Collections thread-safe](thread-safe/index.md)

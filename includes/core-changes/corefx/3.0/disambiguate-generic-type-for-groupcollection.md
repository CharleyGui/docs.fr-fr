---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366877"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a>Passer GroupCollection à des méthodes d’extension en acceptant IEnumerable \<T> requiert une ambiguïté

Lors de l’appel d’une méthode d’extension qui accepte un `IEnumerable<T>` sur un <xref:System.Text.RegularExpressions.GroupCollection> , vous devez lever l’ambiguïté du type à l’aide d’un cast.

#### <a name="change-description"></a>Description de la modification

À compter de .NET Core 3,0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implémente `IEnumerable<KeyValuePair<String,Group>>` en plus des autres types qu’il implémente, y compris `IEnumerable<Group>` . Cela entraîne une ambiguïté lors de l’appel d’une méthode d’extension qui prend un <xref:System.Collections.Generic.IEnumerable%601> . Si vous appelez une telle méthode d’extension sur une <xref:System.Text.RegularExpressions.GroupCollection> instance, par exemple, vous verrez <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> l’erreur de compilateur suivante :

**CS1061 : 'GroupCollection’ne contient pas de définition pour’Count’et aucune méthode d’extension accessible’Count’acceptant un premier argument de type’GroupCollection’n’a été trouvée (une directive using ou une référence d’assembly est-elle manquante ?)**

Dans les versions précédentes de .NET, il n’existait aucune ambiguïté et aucune erreur du compilateur.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

Il s’agissait d’une [modification avec rupture non intentionnelle](https://github.com/dotnet/corefx/pull/30077). Comme cela a été le plus tard pendant un certain temps, nous ne prévoyons pas de le rétablir. En outre, une telle modification serait elle-même une rupture.

#### <a name="recommended-action"></a>Action recommandée

Pour les <xref:System.Text.RegularExpressions.GroupCollection> instances, lever l’ambiguïté des appels aux méthodes d’extension qui acceptent un `IEnumerable<T>` avec un cast.

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

Toute méthode d’extension qui accepte un <xref:System.Collections.Generic.IEnumerable%601> est affectée. Par exemple :

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- La plupart des `System.Linq.Enumerable` méthodes, par exemple, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName>
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->

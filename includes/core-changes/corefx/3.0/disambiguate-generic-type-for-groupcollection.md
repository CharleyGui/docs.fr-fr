---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366877"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a><span data-ttu-id="f0b5b-101">Passer GroupCollection à des méthodes d’extension en acceptant IEnumerable \<T> requiert une ambiguïté</span><span class="sxs-lookup"><span data-stu-id="f0b5b-101">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>

<span data-ttu-id="f0b5b-102">Lors de l’appel d’une méthode d’extension qui accepte un `IEnumerable<T>` sur un <xref:System.Text.RegularExpressions.GroupCollection> , vous devez lever l’ambiguïté du type à l’aide d’un cast.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-102">When calling an extension method that takes an `IEnumerable<T>` on a <xref:System.Text.RegularExpressions.GroupCollection>, you must disambiguate the type using a cast.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f0b5b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="f0b5b-103">Change description</span></span>

<span data-ttu-id="f0b5b-104">À compter de .NET Core 3,0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implémente `IEnumerable<KeyValuePair<String,Group>>` en plus des autres types qu’il implémente, y compris `IEnumerable<Group>` .</span><span class="sxs-lookup"><span data-stu-id="f0b5b-104">Starting in .NET Core 3.0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implements `IEnumerable<KeyValuePair<String,Group>>` in addition to the other types it implements, including `IEnumerable<Group>`.</span></span> <span data-ttu-id="f0b5b-105">Cela entraîne une ambiguïté lors de l’appel d’une méthode d’extension qui prend un <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="f0b5b-105">This results in ambiguity when calling an extension method that takes an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="f0b5b-106">Si vous appelez une telle méthode d’extension sur une <xref:System.Text.RegularExpressions.GroupCollection> instance, par exemple, vous verrez <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> l’erreur de compilateur suivante :</span><span class="sxs-lookup"><span data-stu-id="f0b5b-106">If you call such an extension method on a <xref:System.Text.RegularExpressions.GroupCollection> instance, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, you'll see the following compiler error:</span></span>

<span data-ttu-id="f0b5b-107">**CS1061 : 'GroupCollection’ne contient pas de définition pour’Count’et aucune méthode d’extension accessible’Count’acceptant un premier argument de type’GroupCollection’n’a été trouvée (une directive using ou une référence d’assembly est-elle manquante ?)**</span><span class="sxs-lookup"><span data-stu-id="f0b5b-107">**CS1061: 'GroupCollection' does not contain a definition for 'Count' and no accessible extension method 'Count' accepting a first argument of type 'GroupCollection' could be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="f0b5b-108">Dans les versions précédentes de .NET, il n’existait aucune ambiguïté et aucune erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-108">In previous versions of .NET, there was no ambiguity and no compiler error.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f0b5b-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f0b5b-109">Version introduced</span></span>

<span data-ttu-id="f0b5b-110">3.0</span><span class="sxs-lookup"><span data-stu-id="f0b5b-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f0b5b-111">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f0b5b-111">Reason for change</span></span>

<span data-ttu-id="f0b5b-112">Il s’agissait d’une [modification avec rupture non intentionnelle](https://github.com/dotnet/corefx/pull/30077).</span><span class="sxs-lookup"><span data-stu-id="f0b5b-112">This was an [unintentional breaking change](https://github.com/dotnet/corefx/pull/30077).</span></span> <span data-ttu-id="f0b5b-113">Comme cela a été le plus tard pendant un certain temps, nous ne prévoyons pas de le rétablir.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-113">Because it has been like this for some time, we don't plan to revert it.</span></span> <span data-ttu-id="f0b5b-114">En outre, une telle modification serait elle-même une rupture.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-114">In addition, such a change would itself be breaking.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f0b5b-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f0b5b-115">Recommended action</span></span>

<span data-ttu-id="f0b5b-116">Pour les <xref:System.Text.RegularExpressions.GroupCollection> instances, lever l’ambiguïté des appels aux méthodes d’extension qui acceptent un `IEnumerable<T>` avec un cast.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-116">For <xref:System.Text.RegularExpressions.GroupCollection> instances, disambiguate calls to extension methods that accept an `IEnumerable<T>` with a cast.</span></span>

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a><span data-ttu-id="f0b5b-117">Category</span><span class="sxs-lookup"><span data-stu-id="f0b5b-117">Category</span></span>

<span data-ttu-id="f0b5b-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="f0b5b-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f0b5b-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="f0b5b-119">Affected APIs</span></span>

<span data-ttu-id="f0b5b-120">Toute méthode d’extension qui accepte un <xref:System.Collections.Generic.IEnumerable%601> est affectée.</span><span class="sxs-lookup"><span data-stu-id="f0b5b-120">Any extension method that accepts an <xref:System.Collections.Generic.IEnumerable%601> is affected.</span></span> <span data-ttu-id="f0b5b-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="f0b5b-121">For example:</span></span>

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- <span data-ttu-id="f0b5b-122">La plupart des `System.Linq.Enumerable` méthodes, par exemple, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="f0b5b-122">Most of the `System.Linq.Enumerable` methods, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span></span>
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

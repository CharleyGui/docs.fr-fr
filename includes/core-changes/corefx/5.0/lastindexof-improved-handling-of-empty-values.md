---
ms.openlocfilehash: 0ba77a6a6ac0e2d29036635ea3cdb9ba9a9da10e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440174"
---
### <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="7f87f-101">LastIndexOf a amélioré la gestion des chaînes de recherche vides</span><span class="sxs-lookup"><span data-stu-id="7f87f-101">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="7f87f-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées retournent désormais des valeurs correctes lors de la recherche d’une sous-chaîne de longueur nulle (ou équivalente de longueur nulle) dans une chaîne plus grande.</span><span class="sxs-lookup"><span data-stu-id="7f87f-102"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7f87f-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="7f87f-103">Change description</span></span>

<span data-ttu-id="7f87f-104">Dans .NET Framework et .NET Core 1,0-3,1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées peuvent retourner une valeur incorrecte lorsque l’appelant recherche une sous-chaîne de longueur nulle.</span><span class="sxs-lookup"><span data-stu-id="7f87f-104">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="7f87f-105">À compter de .NET 5,0, ces API retournent la valeur correcte pour `LastIndexOf` .</span><span class="sxs-lookup"><span data-stu-id="7f87f-105">Starting with .NET 5.0, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="7f87f-106">Dans ces exemples, `5` est la réponse correcte, car `"Hello".Substring(5)` et `"Hello".AsSpan().Slice(5)` les deux produisent une chaîne vide, qui est, de manière triviale, égale à la sous-chaîne vide recherchée.</span><span class="sxs-lookup"><span data-stu-id="7f87f-106">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7f87f-107">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7f87f-107">Reason for change</span></span>

<span data-ttu-id="7f87f-108">Cette modification faisait partie d’un effort de correction global des bogues autour de la gestion des chaînes pour .NET 5.</span><span class="sxs-lookup"><span data-stu-id="7f87f-108">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="7f87f-109">Il permet également d’unifier notre comportement entre les plates-formes Windows et non-Windows.</span><span class="sxs-lookup"><span data-stu-id="7f87f-109">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="7f87f-110">Pour plus d’informations, consultez [dotnet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) et [dotnet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).</span><span class="sxs-lookup"><span data-stu-id="7f87f-110">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7f87f-111">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7f87f-111">Version introduced</span></span>

<span data-ttu-id="7f87f-112">5.0</span><span class="sxs-lookup"><span data-stu-id="7f87f-112">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7f87f-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7f87f-113">Recommended action</span></span>

<span data-ttu-id="7f87f-114">Aucune action de votre part n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="7f87f-114">You don't need to take any action.</span></span> <span data-ttu-id="7f87f-115">Le Runtime .NET 5,0 fournit automatiquement les nouveaux comportements.</span><span class="sxs-lookup"><span data-stu-id="7f87f-115">The .NET 5.0 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="7f87f-116">Il n’existe aucun commutateur de compatibilité pour restaurer l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="7f87f-116">There is no compatibility switch to restore the old behavior.</span></span>

#### <a name="category"></a><span data-ttu-id="7f87f-117">Category</span><span class="sxs-lookup"><span data-stu-id="7f87f-117">Category</span></span>

<span data-ttu-id="7f87f-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f87f-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7f87f-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="7f87f-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->

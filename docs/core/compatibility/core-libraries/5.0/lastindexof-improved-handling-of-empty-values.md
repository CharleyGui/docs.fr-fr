---
title: 'Modification avec rupture : LastIndexOf a amélioré la gestion des chaînes de recherche vides'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où LastIndexOf et les API associées retournent désormais des valeurs correctes lors de la recherche d’une sous-chaîne de longueur nulle.
ms.date: 11/01/2020
ms.openlocfilehash: 6d1a676eb2b9ed3de6a745db27d53bd43560a32f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760867"
---
# <a name="lastindexof-has-improved-handling-of-empty-search-strings"></a><span data-ttu-id="fc32c-103">LastIndexOf a amélioré la gestion des chaînes de recherche vides</span><span class="sxs-lookup"><span data-stu-id="fc32c-103">LastIndexOf has improved handling of empty search strings</span></span>

<span data-ttu-id="fc32c-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées retournent désormais des valeurs correctes lors de la recherche d’une sous-chaîne de longueur nulle (ou équivalente de longueur nulle) dans une chaîne plus grande.</span><span class="sxs-lookup"><span data-stu-id="fc32c-104"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs now return correct values when searching for a zero-length (or zero-length equivalent) substring within a larger string.</span></span>

## <a name="change-description"></a><span data-ttu-id="fc32c-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="fc32c-105">Change description</span></span>

<span data-ttu-id="fc32c-106">Dans .NET Framework et .NET Core 1,0-3,1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> et les API associées peuvent retourner une valeur incorrecte lorsque l’appelant recherche une sous-chaîne de longueur nulle.</span><span class="sxs-lookup"><span data-stu-id="fc32c-106">In .NET Framework and .NET Core 1.0 - 3.1, <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> and related APIs might return an incorrect value when the caller searches for a zero-length substring.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '4' (incorrect)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '0' (incorrect)
```

<span data-ttu-id="fc32c-107">À compter de .NET 5,0, ces API retournent la valeur correcte pour `LastIndexOf` .</span><span class="sxs-lookup"><span data-stu-id="fc32c-107">Starting with .NET 5.0, these APIs return the correct value for `LastIndexOf`.</span></span>

```csharp
Console.WriteLine("Hello".LastIndexOf("")); // prints '5' (correct)

ReadOnlySpan<char> span = "Hello";
Console.WriteLine(span.LastIndexOf("")); // prints '5' (correct)
```

<span data-ttu-id="fc32c-108">Dans ces exemples, `5` est la réponse correcte, car `"Hello".Substring(5)` et `"Hello".AsSpan().Slice(5)` les deux produisent une chaîne vide, qui est, de manière triviale, égale à la sous-chaîne vide recherchée.</span><span class="sxs-lookup"><span data-stu-id="fc32c-108">In these examples, `5` is the correct answer because `"Hello".Substring(5)` and `"Hello".AsSpan().Slice(5)` both produce an empty string, which is trivially equal to the empty substring that is sought.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="fc32c-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="fc32c-109">Reason for change</span></span>

<span data-ttu-id="fc32c-110">Cette modification faisait partie d’un effort de correction global des bogues autour de la gestion des chaînes pour .NET 5.</span><span class="sxs-lookup"><span data-stu-id="fc32c-110">This change was part of an overall bug fixing effort around string handling for .NET 5.</span></span> <span data-ttu-id="fc32c-111">Il permet également d’unifier notre comportement entre les plates-formes Windows et non-Windows.</span><span class="sxs-lookup"><span data-stu-id="fc32c-111">It also helps unify our behavior between Windows and non-Windows platforms.</span></span> <span data-ttu-id="fc32c-112">Pour plus d’informations, consultez [dotnet/Runtime # 13383](https://github.com/dotnet/runtime/issues/13383) et [dotnet/Runtime # #13382](https://github.com/dotnet/runtime/issues/13382).</span><span class="sxs-lookup"><span data-stu-id="fc32c-112">For more information, see [dotnet/runtime#13383](https://github.com/dotnet/runtime/issues/13383) and [dotnet/runtime##13382](https://github.com/dotnet/runtime/issues/13382).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="fc32c-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc32c-113">Version introduced</span></span>

<span data-ttu-id="fc32c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="fc32c-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="fc32c-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fc32c-115">Recommended action</span></span>

<span data-ttu-id="fc32c-116">Aucune action de votre part n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fc32c-116">You don't need to take any action.</span></span> <span data-ttu-id="fc32c-117">Le Runtime .NET 5,0 fournit automatiquement les nouveaux comportements.</span><span class="sxs-lookup"><span data-stu-id="fc32c-117">The .NET 5.0 runtime provides the new behaviors automatically.</span></span>

<span data-ttu-id="fc32c-118">Il n’existe aucun commutateur de compatibilité pour restaurer l’ancien comportement.</span><span class="sxs-lookup"><span data-stu-id="fc32c-118">There is no compatibility switch to restore the old behavior.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="fc32c-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="fc32c-119">Affected APIs</span></span>

- <xref:System.String.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.Globalization.CompareInfo.LastIndexOf%2A?displayProperty=fullName>
- <xref:System.MemoryExtensions.LastIndexOf%2A?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.String.LastIndexOf`
- `Overload:System.Globalization.CompareInfo.LastIndexOf`
- `Overload:System.MemoryExtensions.LastIndexOf`

-->

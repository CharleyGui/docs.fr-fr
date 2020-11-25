---
title: 'Modification avec rupture : complexité de LINQ OrderBy. la première {OrDefault} a augmenté'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où l’implémentation de OrderBy. First a changé.
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f8fd0bb2051c3e1ac14eab091be11f10f88b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761046"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="2d98b-103">Complexité de LINQ OrderBy. la première {OrDefault} a augmenté</span><span class="sxs-lookup"><span data-stu-id="2d98b-103">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="2d98b-104">L’implémentation de <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> et <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> a changé, ce qui a entraîné une plus grande complexité pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="2d98b-104">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

## <a name="change-description"></a><span data-ttu-id="2d98b-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="2d98b-105">Change description</span></span>

<span data-ttu-id="2d98b-106">Dans .NET Core 1. x-3. x, l’appel de <xref:System.Linq.Enumerable.OrderBy%2A> ou <xref:System.Linq.Enumerable.OrderByDescending%2A> suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N)` complexité.</span><span class="sxs-lookup"><span data-stu-id="2d98b-106">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="2d98b-107">Étant donné que seul le premier élément (ou par défaut) est requis, une seule énumération est nécessaire pour le trouver.</span><span class="sxs-lookup"><span data-stu-id="2d98b-107">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="2d98b-108">Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> est appelé exactement `N` fois, où `N` est la longueur de la séquence.</span><span class="sxs-lookup"><span data-stu-id="2d98b-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="2d98b-109">Dans .NET 5,0 et versions ultérieures, une [modification a été apportée](https://github.com/dotnet/runtime/pull/36643) de telle sorte que l’appel <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> de ou suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N log N)` la complexité plutôt que `O(N)` la complexité.</span><span class="sxs-lookup"><span data-stu-id="2d98b-109">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="2d98b-110">Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> peut être appelé *moins* de `N` fois, ce qui est plus important pour les performances globales.</span><span class="sxs-lookup"><span data-stu-id="2d98b-110">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="2d98b-111">Cette modification correspond à l’implémentation et à la complexité de l’opération dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2d98b-111">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2d98b-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2d98b-112">Reason for change</span></span>

<span data-ttu-id="2d98b-113">L’avantage de l’appel du prédicat moins souvent compense une complexité globale plus faible, de sorte que l’implémentation introduite dans .NET Core 1,0 a été annulée.</span><span class="sxs-lookup"><span data-stu-id="2d98b-113">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="2d98b-114">Pour plus d’informations, consultez [ce problème dotnet/Runtime](https://github.com/dotnet/runtime/issues/31554).</span><span class="sxs-lookup"><span data-stu-id="2d98b-114">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2d98b-115">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2d98b-115">Version introduced</span></span>

<span data-ttu-id="2d98b-116">5.0</span><span class="sxs-lookup"><span data-stu-id="2d98b-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2d98b-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2d98b-117">Recommended action</span></span>

<span data-ttu-id="2d98b-118">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="2d98b-118">No action is required on the developer's part.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2d98b-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="2d98b-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->

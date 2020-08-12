---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137483"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="63aae-101">Complexité de LINQ OrderBy. la première {OrDefault} a augmenté</span><span class="sxs-lookup"><span data-stu-id="63aae-101">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="63aae-102">L’implémentation de <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> et <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> a changé, ce qui a entraîné une plus grande complexité pour l’opération.</span><span class="sxs-lookup"><span data-stu-id="63aae-102">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

#### <a name="change-description"></a><span data-ttu-id="63aae-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="63aae-103">Change description</span></span>

<span data-ttu-id="63aae-104">Dans .NET Core 1. x-3. x, l’appel de <xref:System.Linq.Enumerable.OrderBy%2A> ou <xref:System.Linq.Enumerable.OrderByDescending%2A> suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N)` complexité.</span><span class="sxs-lookup"><span data-stu-id="63aae-104">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="63aae-105">Étant donné que seul le premier élément (ou par défaut) est requis, une seule énumération est nécessaire pour le trouver.</span><span class="sxs-lookup"><span data-stu-id="63aae-105">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="63aae-106">Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> est appelé exactement `N` fois, où `N` est la longueur de la séquence.</span><span class="sxs-lookup"><span data-stu-id="63aae-106">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="63aae-107">Dans .NET 5,0 et versions ultérieures, une [modification a été apportée](https://github.com/dotnet/runtime/pull/36643) de telle sorte que l’appel <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> de ou suivi de <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> fonctionne avec `O(N log N)` la complexité plutôt que `O(N)` la complexité.</span><span class="sxs-lookup"><span data-stu-id="63aae-107">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="63aae-108">Toutefois, le prédicat fourni à <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> ou <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> peut être appelé *moins* de `N` fois, ce qui est plus important pour les performances globales.</span><span class="sxs-lookup"><span data-stu-id="63aae-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="63aae-109">Cette modification correspond à l’implémentation et à la complexité de l’opération dans .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63aae-109">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="63aae-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="63aae-110">Reason for change</span></span>

<span data-ttu-id="63aae-111">L’avantage de l’appel du prédicat moins souvent compense une complexité globale plus faible, de sorte que l’implémentation introduite dans .NET Core 1,0 a été annulée.</span><span class="sxs-lookup"><span data-stu-id="63aae-111">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="63aae-112">Pour plus d’informations, consultez [ce problème dotnet/Runtime](https://github.com/dotnet/runtime/issues/31554).</span><span class="sxs-lookup"><span data-stu-id="63aae-112">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="63aae-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="63aae-113">Version introduced</span></span>

<span data-ttu-id="63aae-114">5.0</span><span class="sxs-lookup"><span data-stu-id="63aae-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="63aae-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="63aae-115">Recommended action</span></span>

<span data-ttu-id="63aae-116">Aucune action n’est requise de la part du développeur.</span><span class="sxs-lookup"><span data-stu-id="63aae-116">No action is required on the developer's part.</span></span>

#### <a name="category"></a><span data-ttu-id="63aae-117">Category</span><span class="sxs-lookup"><span data-stu-id="63aae-117">Category</span></span>

<span data-ttu-id="63aae-118">Bibliothèques .NET Core</span><span class="sxs-lookup"><span data-stu-id="63aae-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63aae-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="63aae-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->

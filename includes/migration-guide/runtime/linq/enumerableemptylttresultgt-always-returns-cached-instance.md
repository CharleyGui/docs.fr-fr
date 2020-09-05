---
ms.openlocfilehash: 05f60978f5380c406c43aa98ded0c812b1d50694
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496435"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="455f5-101">Enumerable.Empty&lt;TResult&gt; retourne toujours une instance mise en cache</span><span class="sxs-lookup"><span data-stu-id="455f5-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="455f5-102">Détails</span><span class="sxs-lookup"><span data-stu-id="455f5-102">Details</span></span>

<span data-ttu-id="455f5-103">À compter de .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> retourne toujours une instance interne mise en cache <xref:System.Collections.Generic.IEnumerable%601>. Avant, <xref:System.Linq.Enumerable.Empty%60%601> mettait en cache un <xref:System.Collections.Generic.IEnumerable%601> vide lors de l’appel de l’API, ce qui signifiait que dans certaines conditions, quand <xref:System.Linq.Enumerable.Empty%60%601> était appelé rapidement et simultanément, différentes instances du type pouvaient être retournées pour différents appels à l’API.</span><span class="sxs-lookup"><span data-stu-id="455f5-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="455f5-104">Suggestion</span><span class="sxs-lookup"><span data-stu-id="455f5-104">Suggestion</span></span>

<span data-ttu-id="455f5-105">Étant donné que l’ancien comportement était non déterministe, il est peu probable que le code en dépende.</span><span class="sxs-lookup"><span data-stu-id="455f5-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="455f5-106">Toutefois, dans le cas peu probable où des énumérables vides sont comparés et supposés être parfois inégaux, vous devez créer des tableaux vides explicites (<code>new T[0]</code>) au lieu d’utiliser <xref:System.Linq.Enumerable.Empty%60%601>.</span><span class="sxs-lookup"><span data-stu-id="455f5-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="455f5-107">Name</span><span class="sxs-lookup"><span data-stu-id="455f5-107">Name</span></span>    | <span data-ttu-id="455f5-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="455f5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="455f5-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="455f5-109">Scope</span></span>   |<span data-ttu-id="455f5-110">Edge</span><span class="sxs-lookup"><span data-stu-id="455f5-110">Edge</span></span>|
|<span data-ttu-id="455f5-111">Version</span><span class="sxs-lookup"><span data-stu-id="455f5-111">Version</span></span>|<span data-ttu-id="455f5-112">4,5</span><span class="sxs-lookup"><span data-stu-id="455f5-112">4.5</span></span>|
|<span data-ttu-id="455f5-113">Type</span><span class="sxs-lookup"><span data-stu-id="455f5-113">Type</span></span>|<span data-ttu-id="455f5-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="455f5-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="455f5-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="455f5-115">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Linq.Enumerable.Empty``1``

-->

---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497894"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="912f9-101">Algorithme List.Sort modifié</span><span class="sxs-lookup"><span data-stu-id="912f9-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="912f9-102">Détails</span><span class="sxs-lookup"><span data-stu-id="912f9-102">Details</span></span>

<span data-ttu-id="912f9-103">À compter de .NET Framework 4.5, l’algorithme de tri de <xref:System.Collections.Generic.List%601?displayProperty=fullName> a changé (pour correspondre à un tri approfondi au lieu d’un tri rapide).</span><span class="sxs-lookup"><span data-stu-id="912f9-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="912f9-104">Le tri de <xref:System.Collections.Generic.List%601?displayProperty=fullName> n’a jamais été stable, mais cette modification peut aboutir à des tris instables dans le cadre de différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="912f9-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="912f9-105">Cela signifie simplement que des éléments équivalents peuvent être triés dans des ordres différents lors des appels suivants de l’API.</span><span class="sxs-lookup"><span data-stu-id="912f9-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="912f9-106">Suggestion</span><span class="sxs-lookup"><span data-stu-id="912f9-106">Suggestion</span></span>

<span data-ttu-id="912f9-107">Comme l’ancien algorithme de tri était également instable (de manière légèrement différente, toutefois), aucun code ne doit dépendre du tri dans un ordre particulier des éléments équivalents.</span><span class="sxs-lookup"><span data-stu-id="912f9-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="912f9-108">Si des instances de code présentent cette dépendance et réussissent avec l’ancien comportement, ce code doit être mis à jour pour utiliser un comparateur qui va trier de façon déterministe les éléments dans l’ordre souhaité.</span><span class="sxs-lookup"><span data-stu-id="912f9-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="912f9-109">Name</span><span class="sxs-lookup"><span data-stu-id="912f9-109">Name</span></span>    | <span data-ttu-id="912f9-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="912f9-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="912f9-111">Étendue</span><span class="sxs-lookup"><span data-stu-id="912f9-111">Scope</span></span>   |<span data-ttu-id="912f9-112">Mode transparent</span><span class="sxs-lookup"><span data-stu-id="912f9-112">Transparent</span></span>|
|<span data-ttu-id="912f9-113">Version</span><span class="sxs-lookup"><span data-stu-id="912f9-113">Version</span></span>|<span data-ttu-id="912f9-114">4,5</span><span class="sxs-lookup"><span data-stu-id="912f9-114">4.5</span></span>|
|<span data-ttu-id="912f9-115">Type</span><span class="sxs-lookup"><span data-stu-id="912f9-115">Type</span></span>|<span data-ttu-id="912f9-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="912f9-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="912f9-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="912f9-117">Affected APIs</span></span>

- <xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType>
- <xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.Generic.List`1.Sort``
- ``M:System.Collections.Generic.List`1.Sort(System.Collections.Generic.IComparer{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Comparison{`0})``
- ``M:System.Collections.Generic.List`1.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{`0})``

-->

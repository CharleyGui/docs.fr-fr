---
ms.openlocfilehash: 05f60978f5380c406c43aa98ded0c812b1d50694
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496435"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; retourne toujours une instance mise en cache

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> retourne toujours une instance interne mise en cache <xref:System.Collections.Generic.IEnumerable%601>. Avant, <xref:System.Linq.Enumerable.Empty%60%601> mettait en cache un <xref:System.Collections.Generic.IEnumerable%601> vide lors de l’appel de l’API, ce qui signifiait que dans certaines conditions, quand <xref:System.Linq.Enumerable.Empty%60%601> était appelé rapidement et simultanément, différentes instances du type pouvaient être retournées pour différents appels à l’API.

#### <a name="suggestion"></a>Suggestion

Étant donné que l’ancien comportement était non déterministe, il est peu probable que le code en dépende. Toutefois, dans le cas peu probable où des énumérables vides sont comparés et supposés être parfois inégaux, vous devez créer des tableaux vides explicites (<code>new T[0]</code>) au lieu d’utiliser <xref:System.Linq.Enumerable.Empty%60%601>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Linq.Enumerable.Empty``1``

-->

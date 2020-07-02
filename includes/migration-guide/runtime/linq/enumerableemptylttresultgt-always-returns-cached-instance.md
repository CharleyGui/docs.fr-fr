---
ms.openlocfilehash: 9131c91b34f4c24653dea37ea39af6be6e072287
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620033"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a>Enumerable.Empty&lt;TResult&gt; retourne toujours une instance mise en cache

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> retourne toujours une instance interne mise en cache <xref:System.Collections.Generic.IEnumerable%601>. Avant, <xref:System.Linq.Enumerable.Empty%60%601> mettait en cache un <xref:System.Collections.Generic.IEnumerable%601> vide lors de l’appel de l’API, ce qui signifiait que dans certaines conditions, quand <xref:System.Linq.Enumerable.Empty%60%601> était appelé rapidement et simultanément, différentes instances du type pouvaient être retournées pour différents appels à l’API.

#### <a name="suggestion"></a>Suggestion

Étant donné que l’ancien comportement était non déterministe, il est peu probable que le code en dépende. Toutefois, dans le cas peu probable où des énumérables vides sont comparés et supposés être parfois inégaux, vous devez créer des tableaux vides explicites (<code>new T[0]</code>) au lieu d’utiliser <xref:System.Linq.Enumerable.Empty%60%601>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType></li></ul>|

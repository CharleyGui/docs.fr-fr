---
ms.openlocfilehash: 09bd2c6312493f8b6369d05d8f1c4e88e4c05ece
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497894"
---
### <a name="listsort-algorithm-changed"></a>Algorithme List.Sort modifié

#### <a name="details"></a>Détails

À compter de .NET Framework 4.5, l’algorithme de tri de <xref:System.Collections.Generic.List%601?displayProperty=fullName> a changé (pour correspondre à un tri approfondi au lieu d’un tri rapide). Le tri de <xref:System.Collections.Generic.List%601?displayProperty=fullName> n’a jamais été stable, mais cette modification peut aboutir à des tris instables dans le cadre de différents scénarios. Cela signifie simplement que des éléments équivalents peuvent être triés dans des ordres différents lors des appels suivants de l’API.

#### <a name="suggestion"></a>Suggestion

Comme l’ancien algorithme de tri était également instable (de manière légèrement différente, toutefois), aucun code ne doit dépendre du tri dans un ordre particulier des éléments équivalents. Si des instances de code présentent cette dépendance et réussissent avec l’ancien comportement, ce code doit être mis à jour pour utiliser un comparateur qui va trier de façon déterministe les éléments dans l’ordre souhaité.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Mode transparent|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

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

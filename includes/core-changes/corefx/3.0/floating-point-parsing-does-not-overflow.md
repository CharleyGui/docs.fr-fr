---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721625"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException

Les méthodes d’analyse à virgule flottante ne lèvent plus d’exception <xref:System.OverflowException> ou retournent `false` lorsqu’elles analysent une chaîne dont la valeur numérique est en dehors de la plage du <xref:System.Single> <xref:System.Double> type à virgule flottante ou.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et les versions antérieures, <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Single.Parse%2A?displayProperty=nameWithType> méthodes et lèvent un <xref:System.OverflowException> pour les valeurs qui se trouvent en dehors de la plage de leur type respectif. Les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> méthodes et retournent `false` pour les représentations sous forme de chaîne de valeurs numériques hors limites.

À compter de .net Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> méthodes,, <xref:System.Single.Parse%2A?displayProperty=nameWithType> et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> n’échouent plus lors de l’analyse de chaînes numériques hors limites. Au lieu de cela, les <xref:System.Double> méthodes d’analyse retournent <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> des valeurs qui dépassent <xref:System.Double.MaxValue?displayProperty=nameWithType> , et elles retournent <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> des valeurs inférieures à <xref:System.Double.MinValue?displayProperty=nameWithType> . De même, les <xref:System.Single> méthodes d’analyse retournent <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pour les valeurs qui dépassent <xref:System.Single.MaxValue?displayProperty=nameWithType> , et elles retournent <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> des valeurs inférieures à <xref:System.Single.MinValue?displayProperty=nameWithType> .

Cette modification a été apportée pour améliorer la conformité IEEE 754:2008.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification peut avoir un impact sur votre code de deux manières :

- Votre code dépend du gestionnaire du <xref:System.OverflowException> à exécuter lorsqu’un dépassement de capacité se produit. Dans ce cas, vous devez supprimer l' `catch` instruction et placer le code nécessaire dans une `If` instruction qui teste si <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> a `true` la valeur.

- Votre code suppose que les valeurs à virgule flottante ne le sont pas `Infinity` . Dans ce cas, vous devez ajouter le code nécessaire pour vérifier les valeurs à virgule flottante de `PositiveInfinity` et `NegativeInfinity` .

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->

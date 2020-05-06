---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021636"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException

Les méthodes d’analyse à virgule flottante ne lèvent <xref:System.OverflowException> plus d' `false` exception ou retournent lorsqu’elles analysent une chaîne dont la valeur <xref:System.Single> numérique <xref:System.Double> est en dehors de la plage du type à virgule flottante ou.

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2,2 et les versions antérieures, <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Single.Parse%2A?displayProperty=nameWithType> méthodes et lèvent un <xref:System.OverflowException> pour les valeurs qui se trouvent en dehors de la plage de leur type respectif. Les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> méthodes <xref:System.Single.TryParse%2A?displayProperty=nameWithType> et retournent `false` pour les représentations sous forme de chaîne de valeurs numériques hors limites.

À compter de .net Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>les <xref:System.Double.TryParse%2A?displayProperty=nameWithType>méthodes <xref:System.Single.Parse%2A?displayProperty=nameWithType>,, <xref:System.Single.TryParse%2A?displayProperty=nameWithType> et n’échouent plus lors de l’analyse de chaînes numériques hors limites. Au lieu de <xref:System.Double> cela, les méthodes <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> d’analyse retournent des valeurs <xref:System.Double.MaxValue?displayProperty=nameWithType>qui <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> dépassent, et elles <xref:System.Double.MinValue?displayProperty=nameWithType>retournent des valeurs inférieures à. De même, les <xref:System.Single> méthodes d’analyse <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> retournent pour les <xref:System.Single.MaxValue?displayProperty=nameWithType>valeurs qui dépassent, et elles retournent <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> des valeurs inférieures à. <xref:System.Single.MinValue?displayProperty=nameWithType>

Cette modification a été apportée pour améliorer la conformité IEEE 754:2008.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification peut avoir un impact sur votre code de deux manières :

- Votre code dépend du gestionnaire du <xref:System.OverflowException> à exécuter lorsqu’un dépassement de capacité se produit. Dans ce cas, vous devez supprimer l' `catch` instruction et placer le code nécessaire dans une `If` instruction qui teste <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> si <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> ou `true`a la valeur.

- Votre code suppose que les valeurs à virgule flottante ne `Infinity`le sont pas. Dans ce cas, vous devez ajouter le code nécessaire pour vérifier les valeurs à virgule flottante `PositiveInfinity` de `NegativeInfinity`et.

#### <a name="category"></a>Category

Bibliothèques .NET Core

#### <a name="affected-apis"></a>API affectées

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->

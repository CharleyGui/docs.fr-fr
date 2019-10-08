---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002450"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Les opérations d’analyse de virgule flottante n’échouent plus ou lèvent une exception OverflowException

Les méthodes d’analyse à virgule flottante ne lèvent plus d’exception <xref:System.OverflowException> ou retournent `false` quand elles analysent une chaîne dont la valeur numérique est en dehors de la plage du type à virgule flottante <xref:System.Single> ou <xref:System.Double>.

#### <a name="change-description"></a>Modifier la description

Dans .NET Core 2,2 et les versions antérieures, les méthodes <xref:System.Double.Parse%2A?displayProperty=nameWithType> et <xref:System.Single.Parse%2A?displayProperty=nameWithType> lèvent une <xref:System.OverflowException> pour les valeurs qui se trouvent en dehors de la plage de leur type respectif. Les méthodes <xref:System.Double.TryParse%2A?displayProperty=nameWithType> et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> retournent `false` pour les représentations sous forme de chaîne de valeurs numériques hors limites.

À compter de .NET Core 3,0, les méthodes <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> n’échouent plus lors de l’analyse de chaînes numériques hors limites. Au lieu de cela, les méthodes d’analyse <xref:System.Double> retournent <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> pour les valeurs qui dépassent <xref:System.Double.MaxValue?displayProperty=nameWithType>, et elles retournent <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> pour les valeurs inférieures à <xref:System.Double.MinValue?displayProperty=nameWithType>. De même, les méthodes d’analyse <xref:System.Single> retournent <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pour les valeurs qui dépassent <xref:System.Single.MaxValue?displayProperty=nameWithType>, et elles retournent <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> pour les valeurs inférieures à <xref:System.Single.MinValue?displayProperty=nameWithType>.

Cette modification a été apportée pour améliorer la conformité IEEE 754:2008. 

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification peut avoir un impact sur votre code de deux manières :

- Votre code dépend du gestionnaire de l' <xref:System.OverflowException> pour s’exécuter lorsqu’un dépassement de capacité se produit. Dans ce cas, vous devez supprimer l’instruction `catch` et placer tout code nécessaire dans une instruction `If` qui teste si <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> ou <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> est `true`.

- Votre code suppose que les valeurs à virgule flottante ne sont pas `Infinity`. Dans ce cas, vous devez ajouter le code nécessaire pour vérifier les valeurs à virgule flottante de `PositiveInfinity` et `NegativeInfinity`.

#### <a name="category"></a>Catégorie

CoreFx

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

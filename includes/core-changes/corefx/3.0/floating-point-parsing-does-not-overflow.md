---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568078"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Les opérations d’analyse des points flottants ne échouent plus ou ne jettent plus de OverflowException

Les méthodes d’analyse des points <xref:System.OverflowException> flottants `false` ne jettent plus une ou une déclaration <xref:System.Single> lorsqu’elles analysent une chaîne dont la valeur numérique est hors de la portée du type de point flottant. <xref:System.Double>

#### <a name="change-description"></a>Description de la modification

Dans .NET Core 2.2 et <xref:System.Double.Parse%2A?displayProperty=nameWithType> les <xref:System.Single.Parse%2A?displayProperty=nameWithType> versions <xref:System.OverflowException> antérieures, le et les méthodes jettent un pour les valeurs qui en dehors de la gamme de leur type respectif. Les <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> et `false` les méthodes reviennent pour les représentations de cordes de valeurs numériques hors de portée.

En commençant par .NET Core 3.0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>le , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>et <xref:System.Single.TryParse%2A?displayProperty=nameWithType> les méthodes ne manquent plus lors de l’analyse des chaînes numériques hors de portée. Au lieu <xref:System.Double> de cela, <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> les méthodes <xref:System.Double.MaxValue?displayProperty=nameWithType>d’analyse <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> reviennent pour les <xref:System.Double.MinValue?displayProperty=nameWithType>valeurs qui dépassent , et ils reviennent pour des valeurs qui sont inférieures à . De même, les <xref:System.Single> méthodes <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> d’analyse <xref:System.Single.MaxValue?displayProperty=nameWithType>reviennent pour <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> les valeurs qui <xref:System.Single.MinValue?displayProperty=nameWithType>dépassent , et elles reviennent pour des valeurs qui sont inférieures à .

Ce changement a été apporté pour améliorer la conformité IEEE 754:2008.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="recommended-action"></a>Action recommandée

Cette modification peut affecter votre code de deux façons :

- Votre code dépend du <xref:System.OverflowException> gestionnaire pour que le gestionnaire s’exécute lorsqu’un débordement se produit. Dans ce cas, vous `catch` devez supprimer la déclaration `If` et placer <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> tout `true`code nécessaire dans une déclaration qui teste si ou est .

- Votre code suppose que les valeurs `Infinity`de point flottant ne sont pas . Dans ce cas, vous devez ajouter le code nécessaire `PositiveInfinity` `NegativeInfinity`pour vérifier les valeurs de point flottant de et .

#### <a name="category"></a>Category

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

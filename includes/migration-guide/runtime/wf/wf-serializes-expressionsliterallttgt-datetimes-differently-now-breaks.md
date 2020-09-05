---
ms.openlocfilehash: 06424c4fa40343a881356c20003300f65e93efbb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496872"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF sérialise désormais différemment les objets DateTimes Expressions.Literal&lt;T&gt; (il arrête les analyseurs XAML personnalisés)

#### <a name="details"></a>Détails

L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=fullName> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=fullName>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne. Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.

#### <a name="suggestion"></a>Suggestion

Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

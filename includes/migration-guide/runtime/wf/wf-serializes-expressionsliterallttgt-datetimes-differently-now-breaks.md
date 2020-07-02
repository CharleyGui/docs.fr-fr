---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620076"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF sérialise désormais différemment les objets DateTimes Expressions.Literal&lt;T&gt; (il arrête les analyseurs XAML personnalisés)

#### <a name="details"></a>Détails

L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=fullName> ou <xref:System.DateTimeOffset?displayProperty=fullName> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=fullName> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=fullName>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne. Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.

#### <a name="suggestion"></a>Suggestion

Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=fullName> et <xref:System.DateTimeOffset?displayProperty=fullName> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

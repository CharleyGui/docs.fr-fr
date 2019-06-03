---
ms.openlocfilehash: 335647f899c79eff22e313fa40b2e2a73e7cfff0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379606"
---
### <a name="wf-serializes-expressionsliteralt-datetimes-differently-now-breaks-custom-xaml-parsers"></a>WF sérialise désormais différemment les objets DateHeure Expressions.Literal\<T> (arrêt des analyseurs XAML personnalisés)

|   |   |
|---|---|
|Détails|L’objet <xref:System.Windows.Markup.ValueSerializer> associé convertira un objet <xref:System.DateTime?displayProperty=name> ou <xref:System.DateTimeOffset?displayProperty=name> dont les composants Second et <xref:System.DateTime.Millisecond?displayProperty=name> ne sont pas nuls et (pour une valeur de <xref:System.DateTime?displayProperty=name>) dont la propriété <xref:System.DateTime.Kind> n’est pas Unspecified pour la syntaxe d’élément de propriété au lieu d’une chaîne. Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=name> et <xref:System.DateTimeOffset?displayProperty=name> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|
|Suggestion|Cette modification permet aux valeurs <xref:System.DateTime?displayProperty=name> et <xref:System.DateTimeOffset?displayProperty=name> de faire l'objet d'un aller-retour. Les analyseurs XAML personnalisés qui supposent que l'entrée XAML figure dans la syntaxe d'attribut ne fonctionnent pas correctement.|
|Portée|Microsoft Edge|
|Version|4.5|
|Type|Runtime|

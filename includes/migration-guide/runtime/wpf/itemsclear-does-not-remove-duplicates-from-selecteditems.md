---
ms.openlocfilehash: 25ce391f917bd270d4d9a75f608e4a8ec763d15c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497606"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear ne supprime pas les doublons de SelectedItems

#### <a name="details"></a>Détails

Supposons qu’un sélecteur (avec la sélection multiple activée) a des doublons dans sa collection <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> - le même élément apparaît plusieurs fois.  La suppression de ces éléments de la source de données (par exemple en appelant Items.Clear) échoue à les supprimer de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>. Seule la première instance est supprimée. De plus, une utilisation ultérieure de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (par exemple SelectedItems.Clear()) peut rencontrer des problèmes comme <xref:System.ArgumentException?displayProperty=fullName>, car <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contient des éléments qui ne sont plus dans la source de données.

#### <a name="suggestion"></a>Suggestion

Si possible, mettez à niveau vers .NET Framework 4.6.2.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.MultiSelector.SelectedItems`

-->

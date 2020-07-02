---
ms.openlocfilehash: cd59818fe674e10a206725bea8a74c4aceed99b1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620467"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>Le texte sélectionné dans la zone de texte WPF sélectionnée s’affiche dans une autre couleur quand la zone de texte est inactive

#### <a name="details"></a>Détails

Dans .NET Framework 4.5, quand un contrôle de zone de texte WPF est inactif (c’est-à-dire qu’il n’a pas le focus), le texte sélectionné dans la zone s’affiche dans une couleur différente de celle utilisée quand le contrôle est actif.

#### <a name="suggestion"></a>Suggestion

Vous pouvez restaurer le comportement précédent (.NET Framework 4.0) en affectant la valeur <code>false</code> à la propriété <xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|

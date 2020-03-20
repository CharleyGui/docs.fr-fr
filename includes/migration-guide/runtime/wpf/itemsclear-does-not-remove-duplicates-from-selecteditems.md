---
ms.openlocfilehash: 1545c807e3bef675e63e14d01ab82c1131600f39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857504"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear ne supprime pas les doublons de SelectedItems

|   |   |
|---|---|
|Détails|Supposons qu’un sélecteur (avec la sélection multiple activée) a des doublons dans sa collection <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> - le même élément apparaît plusieurs fois.  La suppression de ces éléments de la source de données (par exemple en appelant Items.Clear) échoue à les supprimer de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>. Seule la première instance est supprimée. De plus, une utilisation ultérieure de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (par exemple SelectedItems.Clear()) peut rencontrer des problèmes comme <xref:System.ArgumentException?displayProperty=name>, car <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contient des éléments qui ne sont plus dans la source de données.|
|Suggestion|Si possible, mettez à niveau vers .NET Framework 4.6.2.|
|Étendue|Secondaire|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: 2f94ec58e6fdb56cfc5147e74b6ffd6bb657228d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857504"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a>Items.Clear ne supprime pas les doublons de SelectedItems

|   |   |
|---|---|
|Détails|Supposons qu’un sélecteur (avec la sélection multiple activée) a des doublons dans sa collection <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> - le même élément apparaît plusieurs fois.  La suppression de ces éléments de la source de données (par exemple en appelant Items.Clear) échoue à les supprimer de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name>. Seule la première instance est supprimée. De plus, une utilisation ultérieure de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> (par exemple SelectedItems.Clear()) peut rencontrer des problèmes comme <xref:System.ArgumentException?displayProperty=name>, car <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=name> contient des éléments qui ne sont plus dans la source de données.|
|Suggestion|Si possible, mettez à niveau vers .NET Framework 4.6.2.|
|Portée|Mineur|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|


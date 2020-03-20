---
ms.openlocfilehash: e2d63d85adce64db6e00b62ec17f55ae71ce3052
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803208"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus

|   |   |
|---|---|
|Détails|L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=name> de <xref:System.Windows.Controls.DataGrid?displayProperty=name> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=name> perd le focus.|
|Suggestion|Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=name> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=name>.|
|Étendue|Edge|
|Version|4.5|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

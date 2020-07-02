---
ms.openlocfilehash: c3c3ed44cf53625c246dfe0408bb861750ecf336
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622027"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus

#### <a name="details"></a>Détails

L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perd le focus.

#### <a name="suggestion"></a>Suggestion

Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType></li></ul>|

---
ms.openlocfilehash: c78122a2fe69c78625d6cb7fa9ddf41c49c2e737
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496180"
---
### <a name="calling-datagridcommitedit-from-a-celleditending-handler-drops-focus"></a>L’appel de DataGrid.CommitEdit à partir d’un gestionnaire CellEditEnding supprime le focus

#### <a name="details"></a>Détails

L’appel de <xref:System.Windows.Controls.DataGrid.CommitEdit> depuis un des gestionnaires d’événements <xref:System.Windows.Controls.DataGrid.CellEditEnding?displayProperty=fullName> de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> fait que <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> perd le focus.

#### <a name="suggestion"></a>Suggestion

Ce bogue a été résolu dans le .NET Framework 4.5.2. Vous pouvez donc l’éviter en mettant à niveau votre version du .NET Framework. Vous pouvez également contourner ce problème en resélectionnant explicitement <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> après avoir appelé <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=fullName>.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.DataGrid.CommitEdit?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.CommitEdit`
- `M:System.Windows.Controls.DataGrid.CommitEdit(System.Windows.Controls.DataGridEditingUnit,System.Boolean)`

-->

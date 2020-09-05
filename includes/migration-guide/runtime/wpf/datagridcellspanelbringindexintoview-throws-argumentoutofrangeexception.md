---
ms.openlocfilehash: 961ca545560a53fc2c1d52722b68ae460de66877
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497245"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView lève une exception ArgumentOutOfRangeException

#### <a name="details"></a>Détails

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> fonctionne de façon asynchrone quand la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas encore été déterminées.  Si des colonnes sont supprimées avant le travail asynchrone, une <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> peut se produire.

#### <a name="suggestion"></a>Suggestion

Effectuez une des actions suivantes :<ol><li>Mise à niveau vers .NET Framework 4.7</li><li>Installation du dernier correctif pour .NET Framework 4.6.2</li><li>Évitez de supprimer des colonnes jusqu’à ce que la réponse asynchrone à <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> soit effective.</li></ol>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType>
- <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)`
- `M:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)`

-->

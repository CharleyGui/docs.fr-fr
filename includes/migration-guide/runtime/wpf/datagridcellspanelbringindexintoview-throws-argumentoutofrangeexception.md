---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802486"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView lève une exception ArgumentOutOfRangeException

|   |   |
|---|---|
|Détails|<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> fonctionne de façon asynchrone quand la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas encore été déterminées.  Si des colonnes sont supprimées avant le travail asynchrone, une <xref:System.ArgumentOutOfRangeException?displayProperty=name> peut se produire.|
|Suggestion|Effectuez une des actions suivantes :<ol><li>Mise à niveau vers .NET Framework 4.7</li><li>Installation du dernier correctif pour .NET Framework 4.6.2</li><li>Évitez de supprimer des colonnes jusqu’à ce que la réponse asynchrone à <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> soit effective.</li></ol>|
|Étendue|Edge|
|Version|4.6.2|
|Type|Runtime|
|API affectées|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

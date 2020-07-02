---
ms.openlocfilehash: d78d083b16ac034c6c393dbc0f6094ee4c6c63c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622352"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView lève une exception ArgumentOutOfRangeException

#### <a name="details"></a>Détails

<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> fonctionne de façon asynchrone quand la virtualisation des colonnes est activée, mais que les largeurs de colonne n’ont pas encore été déterminées.  Si des colonnes sont supprimées avant le travail asynchrone, une <xref:System.ArgumentOutOfRangeException?displayProperty=fullName> peut se produire.

#### <a name="suggestion"></a>Suggestion

Effectuez une des actions suivantes :<ol><li>Mise à niveau vers .NET Framework 4.7</li><li>Installation du dernier correctif pour .NET Framework 4.6.2</li><li>Évitez de supprimer des colonnes jusqu’à ce que la réponse asynchrone à <xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> soit effective.</li></ol>

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6.2|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|

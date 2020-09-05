---
ms.openlocfilehash: e1faee846627b22b88eb888d6241d47d8ea6ea06
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497109"
---
### <a name="right-clicking-on-a-wpf-datagrid-row-header-changes-the-datagrid-selection"></a>Un clic droit sur l’en-tête de ligne d’un DataGrid WPF modifie la sélection de la grille de données

#### <a name="details"></a>Détails

Un clic droit sur un en-tête de ligne de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> sélectionné alors que plusieurs lignes sont sélectionnées fait que la sélection de <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> est réduite à cette seule ligne.

#### <a name="suggestion"></a>Suggestion

Ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.DataGrid.%23ctor>

<!--

#### Affected APIs

- `M:System.Windows.Controls.DataGrid.#ctor`

-->

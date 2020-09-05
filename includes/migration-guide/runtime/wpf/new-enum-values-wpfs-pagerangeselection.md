---
ms.openlocfilehash: 61749f59f9379a6d18bb013b2612a07cb7822b3a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497034"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>Nouvelles valeurs enum dans le PageRangeSelection de WPF

#### <a name="details"></a>Détails

Deux nouveaux membres (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> et <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) ont été ajoutés à l’énumération <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Dans la plupart des cas, ces modifications n’affectent pas le code utilisateur. Le code qui dépend d’un certain nombre d’éléments existants dans les appels de <xref:System.Enum.GetNames(System.Type)> et de <xref:System.Enum.GetValues(System.Type)> sur le type <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> doit cependant être modifié.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.PageRangeSelection`

-->

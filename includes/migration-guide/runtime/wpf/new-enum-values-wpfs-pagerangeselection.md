---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620455"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a>Nouvelles valeurs enum dans le PageRangeSelection de WPF

#### <a name="details"></a>Détails

Deux nouveaux membres (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> et <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) ont été ajoutés à l’énumération <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Dans la plupart des cas, ces modifications n’affectent pas le code utilisateur. Le code qui dépend d’un certain nombre d’éléments existants dans les appels de <xref:System.Enum.GetNames(System.Type)> et de <xref:System.Enum.GetValues(System.Type)> sur le type <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> doit cependant être modifié.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|

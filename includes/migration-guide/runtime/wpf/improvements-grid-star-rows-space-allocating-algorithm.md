---
ms.openlocfilehash: 415eb1960c20fb662469e126560d6f366309eb0d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497053"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille

#### <a name="details"></a>Détails

Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.  Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.

#### <a name="suggestion"></a>Suggestion

L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621996"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille

#### <a name="details"></a>Détails

Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.  Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.

#### <a name="suggestion"></a>Suggestion

L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Majeure|
|Version|4.8|
|Type|Runtime|

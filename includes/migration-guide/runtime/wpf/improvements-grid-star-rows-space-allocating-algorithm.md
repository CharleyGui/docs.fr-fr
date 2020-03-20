---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237613"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille

|   |   |
|---|---|
|Détails|Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.  Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.|
|Suggestion|L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.|
|Étendue|Majeure|
|Version|4.8|
|Type|Runtime|

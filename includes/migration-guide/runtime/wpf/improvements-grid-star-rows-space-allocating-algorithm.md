---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237613"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille

|   |   |
|---|---|
|Détails|Correction d’un bogue dans [l’algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.  Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.|
|Suggestion|L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.|
|Étendue|Majeur|
|Version|4.8|
|Type|Runtime|

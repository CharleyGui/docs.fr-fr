---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802695"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a>Améliorations de l’algorithme d’allocation d’espace aux lignes étoile d’une grille

|   |   |
|---|---|
|Détails|Correction d’un bogue dans l’[algorithme d’allocation de tailles à ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) dans une <xref:System.Windows.Controls.Grid> introduite dans .NET Framework 4.7.  Dans certains cas, comme dans une grille avec <code>Height=&quot;Auto&quot;</code> contenant des lignes vides, les lignes ont été réorganisées à la mauvaise position, peut-être même en dehors de la grille.|
|Suggestion|L’application doit s’exécuter sur .NET Framework 4.8 ou ultérieur pour tirer parti de ces changements.|
|Portée|Majeur|
|Version|4.8|
|Type|Runtime|


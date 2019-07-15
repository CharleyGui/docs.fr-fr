---
ms.openlocfilehash: c1a2d76b4e596acc395da6cefed008078e57a336
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858602"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Les valeurs de fusion Null ne sont pas visibles dans le débogueur jusqu’à une étape ultérieure

|   |   |
|---|---|
|Détails|Un bogue dans.NET Framework 4.5 empêche de voir les valeurs définies via une opération de fusion Null dans le débogueur immédiatement après le déroulement de l’opération d’assignation lors de l’exécution de la version 64 bits du .NET Framework.|
|Suggestion|Une nouvelle exécution pas à pas dans le débogueur entraînera la mise à jour correcte de la valeur locale/du champ. Par ailleurs, ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.|
|Portée|Microsoft Edge|
|Version|4.5|
|Type|Runtime|


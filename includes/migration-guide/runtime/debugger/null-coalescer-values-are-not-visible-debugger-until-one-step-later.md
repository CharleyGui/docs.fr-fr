---
ms.openlocfilehash: af8de731ee93d0bfb01042d894f5730570dcdd78
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497046"
---
### <a name="null-coalescer-values-are-not-visible-in-debugger-until-one-step-later"></a>Les valeurs de fusion Null ne sont pas visibles dans le débogueur jusqu’à une étape ultérieure

#### <a name="details"></a>Détails

Un bogue dans.NET Framework 4.5 empêche de voir les valeurs définies via une opération de fusion Null dans le débogueur immédiatement après le déroulement de l’opération d’assignation lors de l’exécution de la version 64 bits du .NET Framework.

#### <a name="suggestion"></a>Suggestion

Une nouvelle exécution pas à pas dans le débogueur entraînera la mise à jour correcte de la valeur locale/du champ. Par ailleurs, ce problème a été corrigé dans .NET Framework 4.6 et vous pouvez le résoudre en effectuant la mise à niveau vers cette version du .NET Framework.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

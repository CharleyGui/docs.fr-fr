---
ms.openlocfilehash: 68b0c4bb032b9744ef585eaef3d68e31afebee24
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496699"
---
### <a name="winforms-checkforoverflowunderflow-property-is-now-true-for-systemdrawing"></a>La propriété CheckForOverflowUnderflow de WinForm est désormais true pour System.Drawing

#### <a name="details"></a>Détails

La propriété CheckForOverflowUnderflow pour l’assembly System.Drawing.dll est définie sur true.

#### <a name="suggestion"></a>Suggestion

Auparavant, en cas de dépassement de capacité, le résultat était tronqué automatiquement. Désormais, une exception <xref:System.OverflowException?displayProperty=fullName> est levée.

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

---
ms.openlocfilehash: 51ac10e6b4cc9c757cb7f68d7d665982bcb57d4e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497133"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities est maintenant APTCA

#### <a name="details"></a>Détails

L'assembly est marqué avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Les classes dérivées ne peuvent pas être marquées avec l'objet <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName>. Auparavant, les types dérivés devaient être marqués avec l'objet <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName>. Toutefois, cette modification ne doit pas avoir d'impact réel.

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

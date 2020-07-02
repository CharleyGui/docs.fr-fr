---
ms.openlocfilehash: beaac7b14535335a665add4fa056a60793879753
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620075"
---
### <a name="systemactivities-is-now-aptca"></a>System.Activities est maintenant APTCA

#### <a name="details"></a>Détails

L'assembly est marqué avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute?displayProperty=fullName>.

#### <a name="suggestion"></a>Suggestion

Les classes dérivées ne peuvent pas être marquées avec l'objet <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName>. Auparavant, les types dérivés devaient être marqués avec l'objet <xref:System.Security.SecurityCriticalAttribute?displayProperty=fullName>. Toutefois, cette modification ne doit pas avoir d'impact réel.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

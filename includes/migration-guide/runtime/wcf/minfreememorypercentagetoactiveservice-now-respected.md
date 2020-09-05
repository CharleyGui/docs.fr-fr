---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496266"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Le paramètre MinFreeMemoryPercentageToActiveService est désormais pris en compte

#### <a name="details"></a>Détails

Ce paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l’activation d’un service WCF. Il a pour but de prévenir les exceptions <xref:System.OutOfMemoryException?displayProperty=fullName>. Dans le .NET Framework 4.5, ce paramètre était sans effet. Dans le .NET Framework 4.5.1, ce paramètre est pris en compte.

#### <a name="suggestion"></a>Suggestion

Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

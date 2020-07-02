---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620051"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a>Le paramètre MinFreeMemoryPercentageToActiveService est désormais pris en compte

#### <a name="details"></a>Détails

Ce paramètre détermine la mémoire minimale devant être disponible sur le serveur avant l’activation d’un service WCF. Il a pour but de prévenir les exceptions <xref:System.OutOfMemoryException?displayProperty=fullName>. Dans le .NET Framework 4.5, ce paramètre était sans effet. Dans le .NET Framework 4.5.1, ce paramètre est pris en compte.

#### <a name="suggestion"></a>Suggestion

Une exception se produit si la mémoire disponible sur le serveur web est inférieure au pourcentage défini par le paramètre de configuration. Certains services WCF qui ont réussi à démarrer et à s'exécuter dans un environnement où la mémoire est limitée risquent à présent d'échouer.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Secondaire|
|Version|4.5.1|
|Type|Runtime|

---
ms.openlocfilehash: 8b70df0fb2072fd5243d9e46a4a20c22cc7fd677
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607788"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Le profilage des applications MVC4 ASP.NET peut provoquer une erreur irrécupérable du moteur d’exécution

#### <a name="details"></a>Détails

Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu dans .NET Framework 4.5.2. Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

Non détectable via l’analyse des API.

<!--

#### Affected APIs

Not detectable via API analysis.

-->

---
ms.openlocfilehash: c679cb2603d39f580203d9373d76481e904e6c1d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497546"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution

#### <a name="details"></a>Détails

Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution

#### <a name="suggestion"></a>Suggestion

Ce problème a été résolu dans .NET Framework 4.5.2. Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.

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

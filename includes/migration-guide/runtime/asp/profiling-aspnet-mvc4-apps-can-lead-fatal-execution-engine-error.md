---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803167"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a>Le profilage des applications ASP.NET MVC4 peut aboutir à une erreur irrécupérable du moteur d’exécution

|   |   |
|---|---|
|Détails|Les profileurs qui utilisent des assemblys NGEN /profil peuvent planter des applications ASP.NET MVC4 profilées au démarrage avec une exception irrécupérable du moteur d’exécution|
|Suggestion|Ce problème a été résolu dans .NET Framework 4.5.2. Le profileur peut aussi éviter ce problème en spécifiant <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> dans son masque d’événement.|
|Étendue|Edge|
|Version|4.5|
|Type|Runtime|

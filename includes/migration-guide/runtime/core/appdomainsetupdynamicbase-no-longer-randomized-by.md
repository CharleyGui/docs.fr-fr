---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621288"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase n’est plus aléatoire en activant UseRandomizedStringHashAlgorithm

#### <a name="details"></a>Détails

Avant .NET Framework 4.6, la valeur de <xref:System.AppDomainSetup.DynamicBase> était aléatoire entre les domaines d’application, ou entre les processus, si UseRandomizedStringHashAlgorithm était activé dans le fichier de configuration de l’application. À compter de .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retourne un résultat stable entre différentes instances d’une application en cours d’exécution et entre différents domaines d’application. Les bases dynamiques seront toujours différentes pour différentes applications ; cette modification supprime uniquement l’élément de nommage aléatoire pour différentes instances de la même application.

#### <a name="suggestion"></a>Suggestion

Gardez à l’esprit que l’activation de <code>UseRandomizedStringHashAlgorithm</code> ne rendra pas <xref:System.AppDomainSetup.DynamicBase> aléatoire. Si une base aléatoire est nécessaire, elle doit être générée dans le code de votre application plutôt que via cette API.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|

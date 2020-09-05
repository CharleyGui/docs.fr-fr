---
ms.openlocfilehash: 26c50ac8b0e570e31a38b1913f73acbe21fae08b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497059"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a>AppDomainSetup.DynamicBase n’est plus aléatoire en activant UseRandomizedStringHashAlgorithm

#### <a name="details"></a>Détails

Avant .NET Framework 4.6, la valeur de <xref:System.AppDomainSetup.DynamicBase> était aléatoire entre les domaines d’application, ou entre les processus, si UseRandomizedStringHashAlgorithm était activé dans le fichier de configuration de l’application. À compter de .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> retourne un résultat stable entre différentes instances d’une application en cours d’exécution et entre différents domaines d’application. Les bases dynamiques seront toujours différentes pour différentes applications ; cette modification supprime uniquement l’élément de nommage aléatoire pour différentes instances de la même application.

#### <a name="suggestion"></a>Suggestion

Gardez à l’esprit que l’activation de <code>UseRandomizedStringHashAlgorithm</code> ne rendra pas <xref:System.AppDomainSetup.DynamicBase> aléatoire. Si une base aléatoire est nécessaire, elle doit être générée dans le code de votre application plutôt que via cette API.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,6|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.AppDomainSetup.DynamicBase`

-->

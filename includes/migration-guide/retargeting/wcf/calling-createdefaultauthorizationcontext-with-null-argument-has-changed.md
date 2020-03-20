---
ms.openlocfilehash: 9ec5fa379556dedeaa7a35e34f004340ab47a39c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804588"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>L’appel de CreateDefaultAuthorizationContext avec un argument Null a été modifié

|   |   |
|---|---|
|Détails|L’implémentation de la valeur <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=name> retournée par un appel à <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=name> avec un argument authorizationPolicies null est maintenant différente dans .NET Framework 4.6.|
|Suggestion|Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement. Dans ce cas, vous pouvez restaurer l’ancien comportement de deux manières :<ol><li>Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6. Pour les services hébergés dans IIS, utilisez l’élément &lt;httpRuntime targetFramework=&quot;x.x&quot; /&gt; pour cibler une version antérieure du .NET Framework.</li><li>Ajoutez la ligne suivante à la section <code>&lt;appSettings&gt;</code> de votre fichier app.config : <code>&lt;add key=&quot;appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext&quot; value=&quot;true&quot; /&gt;</code></li></ol>|
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType></li></ul>|

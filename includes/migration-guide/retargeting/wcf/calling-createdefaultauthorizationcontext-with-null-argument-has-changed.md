---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615705"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a>L’appel de CreateDefaultAuthorizationContext avec un argument Null a été modifié

#### <a name="details"></a>Détails

L’implémentation de la valeur <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> retournée par un appel à <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> avec un argument authorizationPolicies null est maintenant différente dans .NET Framework 4.6.

#### <a name="suggestion"></a>Suggestion

Dans de rares cas, les applications WCF qui utilisent l'authentification personnalisée peuvent voir les différences de comportement. Dans ce cas, vous pouvez restaurer l’ancien comportement de deux manières :

- Recompiler l'application pour cibler une version antérieure du .NET Framework autre que 4.6. Pour les services hébergés dans IIS, utilisez l'élément `<httpRuntime targetFramework="x.x">` pour cibler une version antérieure du .NET Framework.
- Ajoutez la ligne suivante à la section `<appSettings>` de votre fichier app.config :

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.6         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>

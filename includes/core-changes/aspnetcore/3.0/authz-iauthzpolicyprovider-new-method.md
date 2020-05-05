---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901884"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode

Dans ASP.NET Core 3,0, une nouvelle `GetFallbackPolicyAsync` méthode a été ajoutée `IAuthorizationPolicyProvider`à. Cette stratégie de secours est utilisée par l’intergiciel (middleware) d’autorisation quand aucune stratégie n’est spécifiée.

Pour plus d’informations, consultez [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les implémentations `IAuthorizationPolicyProvider` de n’ont `GetFallbackPolicyAsync` pas besoin d’une méthode.

#### <a name="new-behavior"></a>Nouveau comportement

Les implémentations `IAuthorizationPolicyProvider` de requièrent une `GetFallbackPolicyAsync` méthode.

#### <a name="reason-for-change"></a>Motif de modification

Une nouvelle méthode était nécessaire pour que le `AuthorizationMiddleware` nouveau utilise quand aucune stratégie n’est spécifiée.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez la `GetFallbackPolicyAsync` méthode à vos implémentations de `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->

---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901884"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode

Dans ASP.NET Core 3,0, une nouvelle méthode de `GetFallbackPolicyAsync` a été ajoutée à `IAuthorizationPolicyProvider`. Cette stratégie de secours est utilisée par l’intergiciel (middleware) d’autorisation quand aucune stratégie n’est spécifiée.

Pour plus d’informations, consultez [dotnet/aspnetcore # 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les implémentations de `IAuthorizationPolicyProvider` n’ont pas besoin d’une méthode `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Nouveau comportement

Les implémentations de `IAuthorizationPolicyProvider` requièrent une méthode `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Motif de modification

Une nouvelle méthode était nécessaire pour que la nouvelle `AuthorizationMiddleware` utilise quand aucune stratégie n’est spécifiée.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez la méthode `GetFallbackPolicyAsync` à vos implémentations de `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->

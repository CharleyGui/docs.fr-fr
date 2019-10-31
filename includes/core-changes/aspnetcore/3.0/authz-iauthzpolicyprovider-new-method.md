---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198419"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorisation : les implémentations de IAuthorizationPolicyProvider nécessitent une nouvelle méthode

Dans ASP.NET Core 3,0, une nouvelle méthode `GetFallbackPolicyAsync` a été ajoutée à `IAuthorizationPolicyProvider`. Cette stratégie de secours est utilisée par l’intergiciel (middleware) d’autorisation quand aucune stratégie n’est spécifiée.

Pour plus d’informations, consultez [ASPNET/AspNetCore # 9759](https://github.com/aspnet/AspNetCore/pull/9759).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

Les implémentations de `IAuthorizationPolicyProvider` n’ont pas besoin d’une méthode `GetFallbackPolicyAsync`.

#### <a name="new-behavior"></a>Nouveau comportement

Les implémentations de `IAuthorizationPolicyProvider` requièrent une méthode `GetFallbackPolicyAsync`.

#### <a name="reason-for-change"></a>Motif de modification

Une nouvelle méthode était nécessaire pour la nouvelle `AuthorizationMiddleware` à utiliser quand aucune stratégie n’est spécifiée.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez la méthode `GetFallbackPolicyAsync` à vos implémentations de `IAuthorizationPolicyProvider`.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->

---
ms.openlocfilehash: 58dbb73902c0226fa81acf1a70de2160f406f6c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901884"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Autorisation: IAuthorizationPolicyProvider implémentations nécessitent une nouvelle méthode

Dans ASP.NET Core 3.0, une `GetFallbackPolicyAsync` nouvelle méthode `IAuthorizationPolicyProvider`a été ajoutée à . Cette politique de repli est utilisée par l’autorisation middleware lorsqu’aucune politique n’est spécifiée.

Pour plus d’informations, voir [dotnet/aspnetcore 9759](https://github.com/dotnet/aspnetcore/pull/9759).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les implémentations `IAuthorizationPolicyProvider` `GetFallbackPolicyAsync` de n’a pas nécessité de méthode.

#### <a name="new-behavior"></a>Nouveau comportement

Les implémentations nécessitent `IAuthorizationPolicyProvider` une `GetFallbackPolicyAsync` méthode.

#### <a name="reason-for-change"></a>Raison du changement

Une nouvelle méthode était `AuthorizationMiddleware` nécessaire pour que le nouveau soit utilisé lorsqu’aucune stratégie n’est spécifiée.

#### <a name="recommended-action"></a>Action recommandée

Ajoutez `GetFallbackPolicyAsync` la méthode à `IAuthorizationPolicyProvider`vos implémentations de .

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->

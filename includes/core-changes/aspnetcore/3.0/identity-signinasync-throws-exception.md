---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032554"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identité : SignInAsync lève une exception pour l’identité non authentifiée

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false` .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`SignInAsync` accepte tous les principaux/identités, y compris les identités dans lesquelles `IsAuthenticated` est `false` .

#### <a name="new-behavior"></a>Nouveau comportement

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false` . Il existe un nouvel indicateur pour supprimer ce comportement, mais le comportement par défaut a changé.

#### <a name="reason-for-change"></a>Motif de modification

L’ancien comportement était problématique parce que, par défaut, ces principaux ont été rejetés par `[Authorize]`  /  `RequireAuthenticatedUser()` .

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Core 3,0 Preview 6, la valeur par `RequireAuthenticatedSignIn` `AuthenticationOptions` défaut est un indicateur `true` . Affectez à cet indicateur `false` la valeur pour restaurer l’ancien comportement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

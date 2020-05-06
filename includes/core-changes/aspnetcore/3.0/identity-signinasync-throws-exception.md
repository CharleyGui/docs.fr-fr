---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394219"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identité : SignInAsync lève une exception pour l’identité non authentifiée

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false`.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`SignInAsync`accepte tous les principaux/identités, y compris les `IsAuthenticated` identités dans lesquelles est `false`.

#### <a name="new-behavior"></a>Nouveau comportement

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquelles `IsAuthenticated` est `false`. Il existe un nouvel indicateur pour supprimer ce comportement, mais le comportement par défaut a changé.

#### <a name="reason-for-change"></a>Motif de modification

L’ancien comportement était problématique parce que, par défaut, ces principaux ont été rejetés par `[Authorize]`  /  `RequireAuthenticatedUser()`.

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Core 3,0 Preview 6, la valeur par `RequireAuthenticatedSignIn` défaut est `AuthenticationOptions` `true` un indicateur. Affectez à cet `false` indicateur la valeur pour restaurer l’ancien comportement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

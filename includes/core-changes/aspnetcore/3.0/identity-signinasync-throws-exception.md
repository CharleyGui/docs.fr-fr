---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394219"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identité: SignInAsync jette l’exception pour l’identité non authentique

Par défaut, `SignInAsync` jette une exception pour les `IsAuthenticated` `false`directeurs / identités dans lequel est .

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`SignInAsync`accepte tous les principes / identités, y compris les identités dans lesquelles `IsAuthenticated` est `false`.

#### <a name="new-behavior"></a>Nouveau comportement

Par défaut, `SignInAsync` jette une exception pour les `IsAuthenticated` `false`directeurs / identités dans lequel est . Il ya un nouveau drapeau pour supprimer ce comportement, mais le comportement par défaut a changé.

#### <a name="reason-for-change"></a>Raison du changement

Le vieux comportement était problématique parce que, par `[Authorize]`  /  `RequireAuthenticatedUser()`défaut, ces directeurs ont été rejetés par .

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Core 3.0 Preview 6, il `RequireAuthenticatedSignIn` y `AuthenticationOptions` a `true` un drapeau qui est par défaut. Réglez `false` ce drapeau pour restaurer l’ancien comportement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

None

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

---
ms.openlocfilehash: 6679e38aefa7d61ce430dc5375ff3b35c641ea27
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394219"
---
### <a name="identity-signinasync-throws-exception-for-unauthenticated-identity"></a>Identité : SignInAsync lève une exception pour l’identité non authentifiée

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquels `IsAuthenticated` est `false`.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

`SignInAsync` accepte les principaux/identités, y compris les identités dans lesquelles `IsAuthenticated` est `false`.

#### <a name="new-behavior"></a>Nouveau comportement

Par défaut, `SignInAsync` lève une exception pour les principaux/identités dans lesquels `IsAuthenticated` est `false`. Il existe un nouvel indicateur pour supprimer ce comportement, mais le comportement par défaut a changé.

#### <a name="reason-for-change"></a>Motif de modification

L’ancien comportement était problématique parce que, par défaut, ces principaux ont été rejetés par `[Authorize]` @ no__t-1 @ no__t-2.

#### <a name="recommended-action"></a>Action recommandée

Dans ASP.NET Core 3,0 Preview 6, il existe un indicateur `RequireAuthenticatedSignIn` sur `AuthenticationOptions` qui est `true` par défaut. Définissez cet indicateur sur `false` pour restaurer l’ancien comportement.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

aucune.

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

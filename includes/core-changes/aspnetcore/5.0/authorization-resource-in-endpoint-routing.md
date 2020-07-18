---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441546"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a>Autorisation : la ressource dans le routage du point de terminaison est HttpContext

Lors de l’utilisation du routage de point de terminaison dans ASP.NET Core 3,1, la ressource utilisée pour l’autorisation est le point de terminaison. Cette approche était insuffisante pour accéder aux données de route ( <xref:Microsoft.AspNetCore.Routing.RouteData> ). Précédemment dans MVC, une <xref:Microsoft.AspNetCore.Http.HttpContext> ressource était passée, ce qui permet l’accès au point de terminaison ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) et aux données d’itinéraire. Cette modification garantit que la ressource transmise à l’autorisation est toujours la `HttpContext` .

#### <a name="version-introduced"></a>Version introduite

5,0 Preview 7

#### <a name="old-behavior"></a>Ancien comportement

Lorsque vous utilisez le routage de point de terminaison et les attributs d’autorisation ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) ou [Authorize []](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) , la ressource passée à l’autorisation est le point de terminaison correspondant.

#### <a name="new-behavior"></a>Nouveau comportement

Le routage des points de terminaison transmet le `HttpContext` à l’autorisation.

#### <a name="reason-for-change"></a>Motif de modification

Vous pouvez accéder au point de terminaison à partir du `HttpContext` . Toutefois, il n’existait aucun moyen de passer du point de terminaison à des choses telles que les données d’itinéraire. Une perte de fonctionnalité du routage non-point de terminaison a été perdue.

#### <a name="recommended-action"></a>Action recommandée

Si votre application utilise la ressource de point de terminaison, appelez <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> sur `HttpContext` pour continuer à accéder au point de terminaison.

Dans ASP.NET Core 5,0 Preview 8 et versions ultérieures, vous pouvez revenir à l’ancien comportement avec <xref:System.AppContext.SetSwitch%2A> . Par exemple :

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Aucun

<!--

#### Affected APIs

Not detectable via API analysis

-->

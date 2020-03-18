---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393972"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC: Web API cal de compatibilité supprimé

En commençant par ASP.NET Core 3.0, le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` forfait n’est plus disponible.

#### <a name="change-description"></a>Description de la modification

Le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` forfait (WebApiCompatShim) offre une compatibilité partielle dans ASP.NET Core avec ASP.NET 4.x Web API 2 pour simplifier la migration des implémentations existantes d’API Web à ASP.NET Core. Toutefois, les applications utilisant le WebApiCompatShim ne bénéficient pas des fonctionnalités liées à l’API lors des dernières versions ASP.NET Core. Ces fonctionnalités comprennent l’amélioration de la génération de spécifications Open API, la gestion normalisée des erreurs et la génération de code client. Pour mieux concentrer les efforts de l’API en 3.0, WebApiCompatShim a été supprimé. Les applications existantes utilisant le WebApiCompatShim devraient migrer vers le `[ApiController]` nouveau modèle.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Raison du changement

Le shim de compatibilité Web API était un outil de migration. Il restreint l’accès des utilisateurs aux nouvelles fonctionnalités ajoutées dans ASP.NET Core.

#### <a name="recommended-action"></a>Action recommandée

Supprimer l’utilisation de cette cale et migrer directement vers la fonctionnalité similaire dans ASP.NET Core lui-même.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->

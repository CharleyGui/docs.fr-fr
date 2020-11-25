---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032625"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a>MVC : Shim de compatibilité de l’API Web supprimé

À compter de ASP.NET Core 3,0, le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package n’est plus disponible.

#### <a name="change-description"></a>Description de la modification

Le `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package (WebApiCompatShim) fournit une compatibilité partielle dans ASP.net core avec l’API Web 2 ASP.net 4. x afin de simplifier la migration des implémentations d’API Web existantes vers ASP.net core. Toutefois, les applications qui utilisent WebApiCompatShim ne bénéficient pas des fonctionnalités d’API fournies dans les versions récentes de ASP.NET Core. Ces fonctionnalités incluent la génération améliorée des spécifications d’API Open, la gestion standardisée des erreurs et la génération de code client. Pour mieux cibler les efforts des API dans 3,0, WebApiCompatShim a été supprimé. Les applications existantes utilisant WebApiCompatShim doivent migrer vers le `[ApiController]` modèle plus récent.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="reason-for-change"></a>Motif de modification

Le shim de compatibilité des API Web était un outil de migration. Elle restreint l’accès utilisateur aux nouvelles fonctionnalités ajoutées dans ASP.NET Core.

#### <a name="recommended-action"></a>Action recommandée

Supprimez l’utilisation de ce shim et migrez directement vers la fonctionnalité similaire dans ASP.NET Core lui-même.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->

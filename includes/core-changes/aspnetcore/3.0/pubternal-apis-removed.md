---
ms.openlocfilehash: 52b9caf2d5b3d44c0c6349501dafc371541fdd70
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396356"
---
### <a name="pubternal-apis-removed"></a>API « Pubternal » supprimées

Pour mieux gérer la surface d’API publique de ASP.NET Core, la plupart des types dans les `*.Internal` espaces de noms (appelés :::no-loc text="\"pubternal\""::: API) sont devenus véritablement internes. Les membres de ces espaces de noms n’étaient jamais destinés à être pris en charge en tant qu’API accessibles au public. Les API peuvent s’arrêter dans les versions mineures et le faisait souvent. Le code qui dépend de ces API s’interrompt lors de la mise à jour vers ASP.NET Core 3,0.

Pour plus d’informations, consultez [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) et [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

Les API affectées sont marquées avec le `public` modificateur d’accès et existent dans les `*.Internal` espaces de noms.

#### <a name="new-behavior"></a>Nouveau comportement

Les API affectées sont marquées avec le modificateur d’accès [Internal (~/docs/CSharp/Language-Reference/Keywords/Internal.MD) et ne peuvent plus être utilisées par du code en dehors de cet assembly.

#### <a name="reason-for-change"></a>Motif de modification

Les conseils pour ces :::no-loc text="\"pubternal\""::: API étaient les suivants :

* Peut changer sans préavis.
* N’ont pas fait l’objet de stratégies .NET pour empêcher toute modification avec rupture.

Laisser les API `public` (même dans les `*.Internal` espaces de noms) déroutantes pour les clients.

#### <a name="recommended-action"></a>Action recommandée

Arrêtez l’utilisation de ces :::no-loc text="\"pubternal\""::: API. Si vous avez des questions sur d’autres API, ouvrez un problème dans le référentiel [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .

Par exemple, considérez le code de mise en mémoire tampon des requêtes HTTP suivant dans un projet ASP.NET Core 2,2. La `EnableRewind` méthode d’extension existe dans l' `Microsoft.AspNetCore.Http.Internal` espace de noms.

```csharp
HttpContext.Request.EnableRewind();
```

Dans un projet ASP.NET Core 3,0, remplacez l' `EnableRewind` appel par un appel à la `EnableBuffering` méthode d’extension. La fonctionnalité de mise en mémoire tampon des demandes fonctionne comme dans le passé. `EnableBuffering`appelle l' `internal` API Now.

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

Toutes les API dans `Microsoft.AspNetCore.*` les `Microsoft.Extensions.*` espaces de noms et qui ont un `Internal` segment dans le nom de l’espace de noms. Par exemple :

- `Microsoft.AspNetCore.Authentication.Internal`
- `Microsoft.AspNetCore.Builder.Internal`
- `Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `Microsoft.AspNetCore.DataProtection.Internal`
- `Microsoft.AspNetCore.Hosting.Internal`
- `Microsoft.AspNetCore.Http.Internal`
- `Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `Microsoft.AspNetCore.Mvc.Core.Internal`
- `Microsoft.AspNetCore.Mvc.Cors.Internal`
- `Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `Microsoft.AspNetCore.Mvc.Internal`
- `Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `Microsoft.AspNetCore.Mvc.Razor.Internal`
- `Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `Microsoft.AspNetCore.Rewrite.Internal`
- `Microsoft.AspNetCore.Routing.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

<!--

#### Affected APIs

- `N:Microsoft.AspNetCore.Authentication.Internal`
- `N:Microsoft.AspNetCore.Builder.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Cng.Internal`
- `N:Microsoft.AspNetCore.DataProtection.Internal`
- `N:Microsoft.AspNetCore.Hosting.Internal`
- `N:Microsoft.AspNetCore.Http.Internal`
- `N:Microsoft.AspNetCore.Mvc.Core.Infrastructure`
- `N:Microsoft.AspNetCore.Mvc.Core.Internal`
- `N:Microsoft.AspNetCore.Mvc.Cors.Internal`
- `N:Microsoft.AspNetCore.Mvc.DataAnnotations.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Json.Internal`
- `N:Microsoft.AspNetCore.Mvc.Formatters.Xml.Internal`
- `N:Microsoft.AspNetCore.Mvc.Internal`
- `N:Microsoft.AspNetCore.Mvc.ModelBinding.Internal`
- `N:Microsoft.AspNetCore.Mvc.Razor.Internal`
- `N:Microsoft.AspNetCore.Mvc.RazorPages.Internal`
- `N:Microsoft.AspNetCore.Mvc.TagHelpers.Internal`
- `N:Microsoft.AspNetCore.Mvc.ViewFeatures.Internal`
- `N:Microsoft.AspNetCore.Rewrite.Internal`
- `N:Microsoft.AspNetCore.Routing.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Adapter.Internal`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Http`
- `N:Microsoft.AspNetCore.Server.Kestrel.Core.Internal.Infrastructure`
- `N:Microsoft.AspNetCore.Server.Kestrel.Https.Internal`

-->

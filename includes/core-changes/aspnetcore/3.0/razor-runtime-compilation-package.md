---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394430"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor : la compilation du runtime a été déplacée vers un package

La prise en charge de la compilation du runtime des vues Razor et des Razor Pages a été déplacée vers un package distinct.

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

La compilation du runtime est disponible sans avoir besoin de packages supplémentaires.

#### <a name="new-behavior"></a>Nouveau comportement

La fonctionnalité a été déplacée vers le package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

Les API suivantes étaient précédemment disponibles dans `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pour prendre en charge la compilation du Runtime. Les API sont désormais disponibles via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

De plus, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` a été supprimé. La recompilation sur les modifications de fichier est activée par défaut en référençant le package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification était nécessaire pour supprimer la ASP.NET Core dépendance de Framework partagé sur Roslyn.

#### <a name="recommended-action"></a>Action recommandée

Les applications qui requièrent la compilation ou la recompilation des fichiers Razor doivent suivre les étapes suivantes :

1. Ajoutez une référence au package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.
1. Mettez à jour la méthode `Startup.ConfigureServices` du projet pour inclure un appel à `AddMvcRazorRuntimeCompilation`. Par exemple, dans `Startup.ConfigureServices` :

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

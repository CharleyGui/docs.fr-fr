---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344317"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor : la compilation du runtime a été déplacée vers un package

La prise en charge de la compilation du runtime des vues Razor et des Razor Pages a été déplacée vers un package distinct.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

La compilation du runtime est disponible sans avoir besoin de packages supplémentaires.

#### <a name="new-behavior"></a>Nouveau comportement

La fonctionnalité a été déplacée vers le package [Microsoft. AspNetCore. Mvc. Razor. RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) .

Les API suivantes étaient précédemment disponibles dans `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pour prendre en charge la compilation du Runtime. Les API sont désormais disponibles via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.

- `RazorViewEngineOptions.FileProviders` est maintenant `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` est maintenant `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

En outre, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` a été supprimé. La recompilation sur les modifications de fichier est activée par défaut `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` en référençant le package.

#### <a name="reason-for-change"></a>Motif de modification

Cette modification était nécessaire pour supprimer la ASP.NET Core dépendance de Framework partagé sur Roslyn.

#### <a name="recommended-action"></a>Action recommandée

Les applications qui requièrent la compilation ou la recompilation des fichiers Razor doivent suivre les étapes suivantes :

1. Ajoutez une référence au `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.
1. Mettez à jour la `Startup.ConfigureServices` méthode du projet pour inclure un `AddRazorRuntimeCompilation`appel à. Par exemple :

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

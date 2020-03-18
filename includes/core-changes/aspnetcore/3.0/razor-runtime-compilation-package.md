---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344317"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: Compilation Runtime déplacé à un paquet

La prise en charge de la compilation en temps d’exécution des vues Razor et Razor Pages est passée à un paquet distinct.

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

La compilation Runtime est disponible sans avoir besoin de paquets supplémentaires.

#### <a name="new-behavior"></a>Nouveau comportement

La fonctionnalité a été déplacée vers le package [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)

Les API suivantes étaient `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` auparavant disponibles pour soutenir la compilation en temps d’exécution. Les API sont `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`maintenant disponibles via .

- `RazorViewEngineOptions.FileProviders` est maintenant `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` est maintenant `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

En outre, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` a été supprimé. La comcompilation sur les modifications de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` fichiers est activée par défaut en faisant référence au paquet.

#### <a name="reason-for-change"></a>Raison du changement

Ce changement était nécessaire pour éliminer la dépendance ASP.NET Core cadre partagé à Roslyn.

#### <a name="recommended-action"></a>Action recommandée

Les applications qui nécessitent une compilation ou une recomplification des fichiers Razor doivent prendre les étapes suivantes :

1. Ajoutez une référence `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` au paquet.
1. Mettre à jour `Startup.ConfigureServices` la méthode du `AddRazorRuntimeCompilation`projet pour inclure un appel à . Par exemple :

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

---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394430"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="880f9-101">Razor : la compilation du runtime a été déplacée vers un package</span><span class="sxs-lookup"><span data-stu-id="880f9-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="880f9-102">La prise en charge de la compilation du runtime des vues Razor et des Razor Pages a été déplacée vers un package distinct.</span><span class="sxs-lookup"><span data-stu-id="880f9-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="880f9-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="880f9-103">Version introduced</span></span>

<span data-ttu-id="880f9-104">3,0</span><span class="sxs-lookup"><span data-stu-id="880f9-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="880f9-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="880f9-105">Old behavior</span></span>

<span data-ttu-id="880f9-106">La compilation du runtime est disponible sans avoir besoin de packages supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="880f9-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="880f9-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="880f9-107">New behavior</span></span>

<span data-ttu-id="880f9-108">La fonctionnalité a été déplacée vers le package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="880f9-108">The functionality has been moved to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

<span data-ttu-id="880f9-109">Les API suivantes étaient précédemment disponibles dans `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` pour prendre en charge la compilation du Runtime.</span><span class="sxs-lookup"><span data-stu-id="880f9-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="880f9-110">Les API sont désormais disponibles via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span><span class="sxs-lookup"><span data-stu-id="880f9-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

<span data-ttu-id="880f9-111">De plus, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="880f9-111">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="880f9-112">La recompilation sur les modifications de fichier est activée par défaut en référençant le package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="880f9-112">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="880f9-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="880f9-113">Reason for change</span></span>

<span data-ttu-id="880f9-114">Cette modification était nécessaire pour supprimer la ASP.NET Core dépendance de Framework partagé sur Roslyn.</span><span class="sxs-lookup"><span data-stu-id="880f9-114">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="880f9-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="880f9-115">Recommended action</span></span>

<span data-ttu-id="880f9-116">Les applications qui requièrent la compilation ou la recompilation des fichiers Razor doivent suivre les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="880f9-116">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="880f9-117">Ajoutez une référence au package `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="880f9-117">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="880f9-118">Mettez à jour la méthode `Startup.ConfigureServices` du projet pour inclure un appel à `AddMvcRazorRuntimeCompilation`.</span><span class="sxs-lookup"><span data-stu-id="880f9-118">Update the project's `Startup.ConfigureServices` method to include a call to `AddMvcRazorRuntimeCompilation`.</span></span> <span data-ttu-id="880f9-119">Par exemple, dans `Startup.ConfigureServices` :</span><span class="sxs-lookup"><span data-stu-id="880f9-119">For example, in `Startup.ConfigureServices`:</span></span>

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="880f9-120">Category</span><span class="sxs-lookup"><span data-stu-id="880f9-120">Category</span></span>

<span data-ttu-id="880f9-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="880f9-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="880f9-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="880f9-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

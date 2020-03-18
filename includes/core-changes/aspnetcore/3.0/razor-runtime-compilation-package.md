---
ms.openlocfilehash: cd13e7560ee98e0c862c5e2293521c6aaa273455
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344317"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a><span data-ttu-id="6fc62-101">Razor: Compilation Runtime déplacé à un paquet</span><span class="sxs-lookup"><span data-stu-id="6fc62-101">Razor: Runtime compilation moved to a package</span></span>

<span data-ttu-id="6fc62-102">La prise en charge de la compilation en temps d’exécution des vues Razor et Razor Pages est passée à un paquet distinct.</span><span class="sxs-lookup"><span data-stu-id="6fc62-102">Support for runtime compilation of Razor views and Razor Pages has moved to a separate package.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6fc62-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6fc62-103">Version introduced</span></span>

<span data-ttu-id="6fc62-104">3.0</span><span class="sxs-lookup"><span data-stu-id="6fc62-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6fc62-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6fc62-105">Old behavior</span></span>

<span data-ttu-id="6fc62-106">La compilation Runtime est disponible sans avoir besoin de paquets supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="6fc62-106">Runtime compilation is available without needing additional packages.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6fc62-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6fc62-107">New behavior</span></span>

<span data-ttu-id="6fc62-108">La fonctionnalité a été déplacée vers le package [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/)</span><span class="sxs-lookup"><span data-stu-id="6fc62-108">The functionality has been moved to the [Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation](https://www.nuget.org/packages/Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation/) package.</span></span>

<span data-ttu-id="6fc62-109">Les API suivantes étaient `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` auparavant disponibles pour soutenir la compilation en temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="6fc62-109">The following APIs were previously available in `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` to support runtime compilation.</span></span> <span data-ttu-id="6fc62-110">Les API sont `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`maintenant disponibles via .</span><span class="sxs-lookup"><span data-stu-id="6fc62-110">The APIs are now available via `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions`.</span></span>

- <span data-ttu-id="6fc62-111">`RazorViewEngineOptions.FileProviders` est maintenant `MvcRazorRuntimeCompilationOptions.FileProviders`</span><span class="sxs-lookup"><span data-stu-id="6fc62-111">`RazorViewEngineOptions.FileProviders` is now `MvcRazorRuntimeCompilationOptions.FileProviders`</span></span>
- <span data-ttu-id="6fc62-112">`RazorViewEngineOptions.AdditionalCompilationReferences` est maintenant `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span><span class="sxs-lookup"><span data-stu-id="6fc62-112">`RazorViewEngineOptions.AdditionalCompilationReferences` is now `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`</span></span>

<span data-ttu-id="6fc62-113">En outre, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="6fc62-113">In addition, `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` has been removed.</span></span> <span data-ttu-id="6fc62-114">La comcompilation sur les modifications de `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` fichiers est activée par défaut en faisant référence au paquet.</span><span class="sxs-lookup"><span data-stu-id="6fc62-114">Recompilation on file changes is enabled by default by referencing the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6fc62-115">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="6fc62-115">Reason for change</span></span>

<span data-ttu-id="6fc62-116">Ce changement était nécessaire pour éliminer la dépendance ASP.NET Core cadre partagé à Roslyn.</span><span class="sxs-lookup"><span data-stu-id="6fc62-116">This change was necessary to remove the ASP.NET Core shared framework dependency on Roslyn.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6fc62-117">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6fc62-117">Recommended action</span></span>

<span data-ttu-id="6fc62-118">Les applications qui nécessitent une compilation ou une recomplification des fichiers Razor doivent prendre les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6fc62-118">Apps that require runtime compilation or recompilation of Razor files should take the following steps:</span></span>

1. <span data-ttu-id="6fc62-119">Ajoutez une référence `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` au paquet.</span><span class="sxs-lookup"><span data-stu-id="6fc62-119">Add a reference to the `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` package.</span></span>
1. <span data-ttu-id="6fc62-120">Mettre à jour `Startup.ConfigureServices` la méthode du `AddRazorRuntimeCompilation`projet pour inclure un appel à .</span><span class="sxs-lookup"><span data-stu-id="6fc62-120">Update the project's `Startup.ConfigureServices` method to include a call to `AddRazorRuntimeCompilation`.</span></span> <span data-ttu-id="6fc62-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="6fc62-121">For example:</span></span>

    ```csharp
    services.AddMvc()
        .AddRazorRuntimeCompilation();
    ```

#### <a name="category"></a><span data-ttu-id="6fc62-122">Category</span><span class="sxs-lookup"><span data-stu-id="6fc62-122">Category</span></span>

<span data-ttu-id="6fc62-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6fc62-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6fc62-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="6fc62-124">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->

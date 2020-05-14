---
ms.openlocfilehash: 52b9caf2d5b3d44c0c6349501dafc371541fdd70
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396356"
---
### <a name="pubternal-apis-removed"></a><span data-ttu-id="20d81-101">API « Pubternal » supprimées</span><span class="sxs-lookup"><span data-stu-id="20d81-101">"Pubternal" APIs removed</span></span>

<span data-ttu-id="20d81-102">Pour mieux gérer la surface d’API publique de ASP.NET Core, la plupart des types dans les `*.Internal` espaces de noms (appelés :::no-loc text="\"pubternal\""::: API) sont devenus véritablement internes.</span><span class="sxs-lookup"><span data-stu-id="20d81-102">To better maintain the public API surface of ASP.NET Core, most of the types in `*.Internal` namespaces (referred to as :::no-loc text="\"pubternal\""::: APIs) have become truly internal.</span></span> <span data-ttu-id="20d81-103">Les membres de ces espaces de noms n’étaient jamais destinés à être pris en charge en tant qu’API accessibles au public.</span><span class="sxs-lookup"><span data-stu-id="20d81-103">Members in these namespaces were never meant to be supported as public-facing APIs.</span></span> <span data-ttu-id="20d81-104">Les API peuvent s’arrêter dans les versions mineures et le faisait souvent.</span><span class="sxs-lookup"><span data-stu-id="20d81-104">The APIs could break in minor releases and often did.</span></span> <span data-ttu-id="20d81-105">Le code qui dépend de ces API s’interrompt lors de la mise à jour vers ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="20d81-105">Code that depends on these APIs breaks when updating to ASP.NET Core 3.0.</span></span>

<span data-ttu-id="20d81-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 4932](https://github.com/dotnet/aspnetcore/issues/4932) et [dotnet/aspnetcore # 11312](https://github.com/dotnet/aspnetcore/issues/11312).</span><span class="sxs-lookup"><span data-stu-id="20d81-106">For more information, see [dotnet/aspnetcore#4932](https://github.com/dotnet/aspnetcore/issues/4932) and [dotnet/aspnetcore#11312](https://github.com/dotnet/aspnetcore/issues/11312).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="20d81-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="20d81-107">Version introduced</span></span>

<span data-ttu-id="20d81-108">3.0</span><span class="sxs-lookup"><span data-stu-id="20d81-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="20d81-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="20d81-109">Old behavior</span></span>

<span data-ttu-id="20d81-110">Les API affectées sont marquées avec le `public` modificateur d’accès et existent dans les `*.Internal` espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="20d81-110">The affected APIs are marked with the `public` access modifier and exist in `*.Internal` namespaces.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="20d81-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="20d81-111">New behavior</span></span>

<span data-ttu-id="20d81-112">Les API affectées sont marquées avec le modificateur d’accès [Internal (~/docs/CSharp/Language-Reference/Keywords/Internal.MD) et ne peuvent plus être utilisées par du code en dehors de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="20d81-112">The affected APIs are marked with the [internal(~/docs/csharp/language-reference/keywords/internal.md) access modifier and can no longer be used by code outside that assembly.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="20d81-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="20d81-113">Reason for change</span></span>

<span data-ttu-id="20d81-114">Les conseils pour ces :::no-loc text="\"pubternal\""::: API étaient les suivants :</span><span class="sxs-lookup"><span data-stu-id="20d81-114">The guidance for these :::no-loc text="\"pubternal\""::: APIs was that they:</span></span>

* <span data-ttu-id="20d81-115">Peut changer sans préavis.</span><span class="sxs-lookup"><span data-stu-id="20d81-115">Could change without notice.</span></span>
* <span data-ttu-id="20d81-116">N’ont pas fait l’objet de stratégies .NET pour empêcher toute modification avec rupture.</span><span class="sxs-lookup"><span data-stu-id="20d81-116">Weren't subject to .NET policies to prevent breaking changes.</span></span>

<span data-ttu-id="20d81-117">Laisser les API `public` (même dans les `*.Internal` espaces de noms) déroutantes pour les clients.</span><span class="sxs-lookup"><span data-stu-id="20d81-117">Leaving the APIs `public` (even in the `*.Internal` namespaces) was confusing to customers.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="20d81-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="20d81-118">Recommended action</span></span>

<span data-ttu-id="20d81-119">Arrêtez l’utilisation de ces :::no-loc text="\"pubternal\""::: API.</span><span class="sxs-lookup"><span data-stu-id="20d81-119">Stop using these :::no-loc text="\"pubternal\""::: APIs.</span></span> <span data-ttu-id="20d81-120">Si vous avez des questions sur d’autres API, ouvrez un problème dans le référentiel [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) .</span><span class="sxs-lookup"><span data-stu-id="20d81-120">If you have questions about alternate APIs, open an issue in the [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues) repository.</span></span>

<span data-ttu-id="20d81-121">Par exemple, considérez le code de mise en mémoire tampon des requêtes HTTP suivant dans un projet ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="20d81-121">For example, consider the following HTTP request buffering code in an ASP.NET Core 2.2 project.</span></span> <span data-ttu-id="20d81-122">La `EnableRewind` méthode d’extension existe dans l' `Microsoft.AspNetCore.Http.Internal` espace de noms.</span><span class="sxs-lookup"><span data-stu-id="20d81-122">The `EnableRewind` extension method exists in the `Microsoft.AspNetCore.Http.Internal` namespace.</span></span>

```csharp
HttpContext.Request.EnableRewind();
```

<span data-ttu-id="20d81-123">Dans un projet ASP.NET Core 3,0, remplacez l' `EnableRewind` appel par un appel à la `EnableBuffering` méthode d’extension.</span><span class="sxs-lookup"><span data-stu-id="20d81-123">In an ASP.NET Core 3.0 project, replace the `EnableRewind` call with a call to the `EnableBuffering` extension method.</span></span> <span data-ttu-id="20d81-124">La fonctionnalité de mise en mémoire tampon des demandes fonctionne comme dans le passé.</span><span class="sxs-lookup"><span data-stu-id="20d81-124">The request buffering feature works as it did in the past.</span></span> <span data-ttu-id="20d81-125">`EnableBuffering`appelle l' `internal` API Now.</span><span class="sxs-lookup"><span data-stu-id="20d81-125">`EnableBuffering` calls the now `internal` API.</span></span>

```csharp
HttpContext.Request.EnableBuffering();
```

#### <a name="category"></a><span data-ttu-id="20d81-126">Category</span><span class="sxs-lookup"><span data-stu-id="20d81-126">Category</span></span>

<span data-ttu-id="20d81-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="20d81-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="20d81-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="20d81-128">Affected APIs</span></span>

<span data-ttu-id="20d81-129">Toutes les API dans `Microsoft.AspNetCore.*` les `Microsoft.Extensions.*` espaces de noms et qui ont un `Internal` segment dans le nom de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="20d81-129">All APIs in the `Microsoft.AspNetCore.*` and `Microsoft.Extensions.*` namespaces that have an `Internal` segment in the namespace name.</span></span> <span data-ttu-id="20d81-130">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="20d81-130">For example:</span></span>

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

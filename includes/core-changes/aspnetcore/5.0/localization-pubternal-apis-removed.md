---
ms.openlocfilehash: 62a5f56bb7fffc453623a2c3202f288a19110158
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539468"
---
### <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="5013b-101">Localisation : API « Pubternal » supprimées</span><span class="sxs-lookup"><span data-stu-id="5013b-101">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="5013b-102">Pour mieux gérer la surface de l’API publique de ASP.NET Core, certaines :::no-loc text="\"pubternal\""::: API de localisation ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="5013b-102">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="5013b-103">Une :::no-loc text="\"pubternal\""::: API a un `public` modificateur d’accès et est définie dans un espace de noms qui implique une intention [interne](../../../../docs/csharp/language-reference/keywords/internal.md) .</span><span class="sxs-lookup"><span data-stu-id="5013b-103">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../docs/csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="5013b-104">Pour plus d’informations, consultez [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="5013b-104">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5013b-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="5013b-105">Version introduced</span></span>

<span data-ttu-id="5013b-106">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="5013b-106">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="5013b-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="5013b-107">Old behavior</span></span>

<span data-ttu-id="5013b-108">Les API suivantes étaient `public` :</span><span class="sxs-lookup"><span data-stu-id="5013b-108">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="5013b-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="5013b-109">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a><span data-ttu-id="5013b-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="5013b-110">New behavior</span></span>

<span data-ttu-id="5013b-111">La liste suivante présente les modifications :</span><span class="sxs-lookup"><span data-stu-id="5013b-111">The following list outlines the changes:</span></span>

- <span data-ttu-id="5013b-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` devient `Microsoft.Extensions.Localization.AssemblyWrapper` et est maintenant `internal` .</span><span class="sxs-lookup"><span data-stu-id="5013b-112">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="5013b-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` devient `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` et est maintenant `internal` .</span><span class="sxs-lookup"><span data-stu-id="5013b-113">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="5013b-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants sont désormais `internal` :</span><span class="sxs-lookup"><span data-stu-id="5013b-114">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a><span data-ttu-id="5013b-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="5013b-115">Reason for change</span></span>

<span data-ttu-id="5013b-116">Expliquée plus en détail dans [ASPNET/annonces # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: les types ont été supprimés de la surface de l' `public` API.</span><span class="sxs-lookup"><span data-stu-id="5013b-116">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="5013b-117">Ces modifications adaptent plus de classes à cette décision de conception.</span><span class="sxs-lookup"><span data-stu-id="5013b-117">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="5013b-118">Les classes en question étaient conçues comme des points d’extension pour les tests internes de l’équipe.</span><span class="sxs-lookup"><span data-stu-id="5013b-118">The classes in question were intended as extension points for the team's internal testing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5013b-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="5013b-119">Recommended action</span></span>

<span data-ttu-id="5013b-120">Bien que cela soit peu probable, certaines applications peuvent intentionnellement ou accidentellement dépendre des :::no-loc text="\"pubternal\""::: types.</span><span class="sxs-lookup"><span data-stu-id="5013b-120">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="5013b-121">Consultez les sections [nouveau comportement](#new-behavior) pour déterminer comment migrer à partir des types.</span><span class="sxs-lookup"><span data-stu-id="5013b-121">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="5013b-122">Si vous avez identifié un scénario pour lequel l’API publique est autorisée avant cette modification mais ne le fait pas maintenant, signalez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="5013b-122">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="5013b-123">Category</span><span class="sxs-lookup"><span data-stu-id="5013b-123">Category</span></span>

<span data-ttu-id="5013b-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5013b-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5013b-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="5013b-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

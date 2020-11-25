---
title: 'Modification avec rupture : API Pubternal supprimées'
description: En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 où certaines API de localisation pubternal ont été supprimées
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760895"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="1b4ee-103">Localisation : API « Pubternal » supprimées</span><span class="sxs-lookup"><span data-stu-id="1b4ee-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="1b4ee-104">Pour mieux gérer la surface de l’API publique de ASP.NET Core, certaines :::no-loc text="\"pubternal\""::: API de localisation ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="1b4ee-105">Une :::no-loc text="\"pubternal\""::: API a un `public` modificateur d’accès et est définie dans un espace de noms qui implique une intention [interne](../../../../csharp/language-reference/keywords/internal.md) .</span><span class="sxs-lookup"><span data-stu-id="1b4ee-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="1b4ee-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).</span><span class="sxs-lookup"><span data-stu-id="1b4ee-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1b4ee-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1b4ee-107">Version introduced</span></span>

<span data-ttu-id="1b4ee-108">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="1b4ee-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="1b4ee-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="1b4ee-109">Old behavior</span></span>

<span data-ttu-id="1b4ee-110">Les API suivantes étaient `public` :</span><span class="sxs-lookup"><span data-stu-id="1b4ee-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="1b4ee-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="1b4ee-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="1b4ee-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="1b4ee-112">New behavior</span></span>

<span data-ttu-id="1b4ee-113">La liste suivante présente les modifications :</span><span class="sxs-lookup"><span data-stu-id="1b4ee-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="1b4ee-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` devient `Microsoft.Extensions.Localization.AssemblyWrapper` et est maintenant `internal` .</span><span class="sxs-lookup"><span data-stu-id="1b4ee-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="1b4ee-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` devient `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` et est maintenant `internal` .</span><span class="sxs-lookup"><span data-stu-id="1b4ee-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="1b4ee-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` les surcharges de constructeur acceptant l’un des types de paramètres suivants sont désormais `internal` :</span><span class="sxs-lookup"><span data-stu-id="1b4ee-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="1b4ee-117">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="1b4ee-117">Reason for change</span></span>

<span data-ttu-id="1b4ee-118">Expliquée plus en détail dans [ASPNET/annonces # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: les types ont été supprimés de la surface de l' `public` API.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="1b4ee-119">Ces modifications adaptent plus de classes à cette décision de conception.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="1b4ee-120">Les classes en question étaient conçues comme des points d’extension pour les tests internes de l’équipe.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1b4ee-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1b4ee-121">Recommended action</span></span>

<span data-ttu-id="1b4ee-122">Bien que cela soit peu probable, certaines applications peuvent intentionnellement ou accidentellement dépendre des :::no-loc text="\"pubternal\""::: types.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="1b4ee-123">Consultez les sections [nouveau comportement](#new-behavior) pour déterminer comment migrer à partir des types.</span><span class="sxs-lookup"><span data-stu-id="1b4ee-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="1b4ee-124">Si vous avez identifié un scénario pour lequel l’API publique est autorisée avant cette modification mais ne le fait pas maintenant, signalez un problème dans [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span><span class="sxs-lookup"><span data-stu-id="1b4ee-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1b4ee-125">API affectées</span><span class="sxs-lookup"><span data-stu-id="1b4ee-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->

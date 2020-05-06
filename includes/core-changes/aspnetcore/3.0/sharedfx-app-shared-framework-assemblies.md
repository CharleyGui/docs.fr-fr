---
ms.openlocfilehash: 64e854b06895ca54a9ab9870b85868788a731c00
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549598"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="0ede2-101">Framework partagé : assemblys supprimés de Microsoft. AspNetCore. app</span><span class="sxs-lookup"><span data-stu-id="0ede2-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="0ede2-102">À compter de ASP.NET Core 3,0, le ASP.NET Core Shared`Microsoft.AspNetCore.App`Framework () contient uniquement les assemblys internes entièrement développés, pris en charge et pouvant être gérés par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0ede2-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0ede2-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="0ede2-103">Change description</span></span>

<span data-ttu-id="0ede2-104">Considérez la modification comme la redéfinition des limites pour le ASP.NET Core « plateforme ».</span><span class="sxs-lookup"><span data-stu-id="0ede2-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="0ede2-105">L’infrastructure partagée sera [source-Buildable par quiconque via github](https://github.com/dotnet/source-build) et continuera à offrir les avantages existants des frameworks partagés .net core à vos applications.</span><span class="sxs-lookup"><span data-stu-id="0ede2-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="0ede2-106">Certains avantages incluent une taille de déploiement plus petite, une mise à jour corrective centralisée et un temps de démarrage plus rapide.</span><span class="sxs-lookup"><span data-stu-id="0ede2-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="0ede2-107">Dans le cadre de la modification, certaines modifications importantes de la table sont `Microsoft.AspNetCore.App`introduites dans.</span><span class="sxs-lookup"><span data-stu-id="0ede2-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0ede2-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="0ede2-108">Version introduced</span></span>

<span data-ttu-id="0ede2-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0ede2-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0ede2-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="0ede2-110">Old behavior</span></span>

<span data-ttu-id="0ede2-111">Projets référencés `Microsoft.AspNetCore.App` via un `<PackageReference>` élément dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ede2-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="0ede2-112">En outre, `Microsoft.AspNetCore.App` contient les sous-composants suivants :</span><span class="sxs-lookup"><span data-stu-id="0ede2-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="0ede2-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="0ede2-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="0ede2-114">Entity Framework Core (assemblys préfixés `Microsoft.EntityFrameworkCore.`avec)</span><span class="sxs-lookup"><span data-stu-id="0ede2-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="0ede2-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="0ede2-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0ede2-116">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="0ede2-116">New behavior</span></span>

<span data-ttu-id="0ede2-117">Une référence à `Microsoft.AspNetCore.App` ne requiert plus d' `<PackageReference>` élément dans le fichier projet.</span><span class="sxs-lookup"><span data-stu-id="0ede2-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="0ede2-118">L’kit SDK .NET Core prend en charge un nouvel `<FrameworkReference>`élément appelé, qui remplace l' `<PackageReference>`utilisation de.</span><span class="sxs-lookup"><span data-stu-id="0ede2-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="0ede2-119">Pour plus d’informations, consultez [dotnet/aspnetcore # 3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="0ede2-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="0ede2-120">Entity Framework Core est fourni sous forme de packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ede2-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="0ede2-121">Cette modification aligne le modèle d’expédition avec toutes les autres bibliothèques d’accès aux données sur .NET.</span><span class="sxs-lookup"><span data-stu-id="0ede2-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="0ede2-122">Il fournit Entity Framework Core le chemin le plus simple pour poursuivre l’innovation tout en prenant en charge les diverses plateformes .NET.</span><span class="sxs-lookup"><span data-stu-id="0ede2-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="0ede2-123">Le déplacement de Entity Framework Core hors de l’infrastructure partagée n’a aucun impact sur son état en tant que bibliothèque Microsoft, prise en charge et gérée.</span><span class="sxs-lookup"><span data-stu-id="0ede2-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="0ede2-124">La [stratégie de support .net Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continue à la couvrir.</span><span class="sxs-lookup"><span data-stu-id="0ede2-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="0ede2-125">Json.NET et Entity Framework Core continuent de fonctionner avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0ede2-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="0ede2-126">Toutefois, ils ne sont pas inclus dans le Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="0ede2-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="0ede2-127">Pour plus d’informations, consultez [l’avenir de JSON dans .net Core 3,0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="0ede2-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="0ede2-128">Consultez également [la liste complète des binaires](https://github.com/dotnet/aspnetcore/issues/3755) supprimés de l’infrastructure partagée.</span><span class="sxs-lookup"><span data-stu-id="0ede2-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0ede2-129">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="0ede2-129">Reason for change</span></span>

<span data-ttu-id="0ede2-130">Cette modification simplifie la consommation de `Microsoft.AspNetCore.App` et réduit la duplication entre les packages NuGet et les frameworks partagés.</span><span class="sxs-lookup"><span data-stu-id="0ede2-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="0ede2-131">Pour plus d’informations sur la motivation de cette modification, consultez ce billet de [blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="0ede2-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0ede2-132">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="0ede2-132">Recommended action</span></span>

<span data-ttu-id="0ede2-133">Il n’est pas nécessaire que les projets utilisent des `Microsoft.AspNetCore.App` assemblys dans en tant que packages NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ede2-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="0ede2-134">Pour simplifier le ciblage et l’utilisation de l’infrastructure partagée ASP.NET Core, de nombreux packages NuGet livrés depuis ASP.NET Core 1,0 ne sont plus produits.</span><span class="sxs-lookup"><span data-stu-id="0ede2-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="0ede2-135">Les API fournies par ces packages sont toujours disponibles pour les applications à `<FrameworkReference>` l' `Microsoft.AspNetCore.App`aide d’un à.</span><span class="sxs-lookup"><span data-stu-id="0ede2-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="0ede2-136">Les exemples d’API courants incluent Kestrel, MVC et Razor.</span><span class="sxs-lookup"><span data-stu-id="0ede2-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="0ede2-137">Cette modification ne s’applique pas à tous les fichiers binaires référencés via `Microsoft.AspNetCore.App` dans ASP.net Core 2. x.</span><span class="sxs-lookup"><span data-stu-id="0ede2-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="0ede2-138">Les exceptions notables sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="0ede2-138">Notable exceptions include:</span></span>

- <span data-ttu-id="0ede2-139">`Microsoft.Extensions`les bibliothèques qui continuent de cibler .NET Standard seront disponibles en tant que packages NuGet https://github.com/dotnet/extensions)(consultez.</span><span class="sxs-lookup"><span data-stu-id="0ede2-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="0ede2-140">API produites par l’équipe ASP.NET Core qui ne font pas `Microsoft.AspNetCore.App`partie de.</span><span class="sxs-lookup"><span data-stu-id="0ede2-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="0ede2-141">Par exemple, les composants suivants sont disponibles sous forme de packages NuGet :</span><span class="sxs-lookup"><span data-stu-id="0ede2-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="0ede2-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="0ede2-142">Entity Framework Core</span></span>
  - <span data-ttu-id="0ede2-143">API fournissant une intégration tierce</span><span class="sxs-lookup"><span data-stu-id="0ede2-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="0ede2-144">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="0ede2-144">Experimental features</span></span>
  - <span data-ttu-id="0ede2-145">Les API avec des dépendances qui n’ont pas pu [répondre aux conditions requises pour se trouver dans le Framework partagé](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="0ede2-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="0ede2-146">Les extensions de MVC qui maintiennent la prise en charge de Json.NET.</span><span class="sxs-lookup"><span data-stu-id="0ede2-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="0ede2-147">Une API sera fournie en tant que package NuGet pour prendre en charge l’utilisation de Json.NET et MVC.</span><span class="sxs-lookup"><span data-stu-id="0ede2-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="0ede2-148">Le client .NET Signalr continue à prendre en charge .NET Standard et à être fourni en tant que package NuGet.</span><span class="sxs-lookup"><span data-stu-id="0ede2-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="0ede2-149">Elle est destinée à être utilisée sur de nombreux runtimes .NET, tels que Xamarin et UWP.</span><span class="sxs-lookup"><span data-stu-id="0ede2-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="0ede2-150">Pour plus d’informations, consultez [arrêter la production de packages pour les assemblys de Framework partagé dans 3,0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="0ede2-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="0ede2-151">Pour plus d’informations, consultez [dotnet/aspnetcore # 3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="0ede2-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="0ede2-152">Category</span><span class="sxs-lookup"><span data-stu-id="0ede2-152">Category</span></span>

<span data-ttu-id="0ede2-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0ede2-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0ede2-154">API affectées</span><span class="sxs-lookup"><span data-stu-id="0ede2-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->

---
ms.openlocfilehash: a8146db1fb54d63d4716b879ce793f7d817cef59
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937287"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="1936b-101">Cadre partagé : Assemblées supprimées de Microsoft.AspNetCore.App</span><span class="sxs-lookup"><span data-stu-id="1936b-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="1936b-102">À partir de ASP.NET Core 3.0, le cadre partagé`Microsoft.AspNetCore.App`ASP.NET Core () ne contient que des assemblages de premier parti qui sont entièrement développés, pris en charge et utilisables par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1936b-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1936b-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="1936b-103">Change description</span></span>

<span data-ttu-id="1936b-104">Considérez le changement comme la redéfinition des limites pour la ASP.NET «plateforme» de base.</span><span class="sxs-lookup"><span data-stu-id="1936b-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="1936b-105">Le cadre partagé sera [source-buildable par n’importe qui via GitHub](https://github.com/dotnet/source-build) et continuera d’offrir les avantages existants de .NET Core cadres partagés à vos applications.</span><span class="sxs-lookup"><span data-stu-id="1936b-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="1936b-106">Certains avantages comprennent une plus petite taille de déploiement, un patching centralisé et un temps de démarrage plus rapide.</span><span class="sxs-lookup"><span data-stu-id="1936b-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="1936b-107">Dans le cadre du changement, certains `Microsoft.AspNetCore.App`changements de rupture notables sont introduits dans .</span><span class="sxs-lookup"><span data-stu-id="1936b-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1936b-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="1936b-108">Version introduced</span></span>

<span data-ttu-id="1936b-109">3.0</span><span class="sxs-lookup"><span data-stu-id="1936b-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1936b-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="1936b-110">Old behavior</span></span>

<span data-ttu-id="1936b-111">Projets `Microsoft.AspNetCore.App` référencés par un `<PackageReference>` élément du dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="1936b-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="1936b-112">En `Microsoft.AspNetCore.App` outre, contenait les sous-compactes suivantes :</span><span class="sxs-lookup"><span data-stu-id="1936b-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="1936b-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="1936b-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="1936b-114">Entity Framework Core (assemblages `Microsoft.EntityFrameworkCore.`préfixés avec )</span><span class="sxs-lookup"><span data-stu-id="1936b-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="1936b-115">Roslyn`Microsoft.CodeAnalysis`( )</span><span class="sxs-lookup"><span data-stu-id="1936b-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1936b-116">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="1936b-116">New behavior</span></span>

<span data-ttu-id="1936b-117">Une référence `Microsoft.AspNetCore.App` à ne `<PackageReference>` plus nécessite un élément dans le dossier du projet.</span><span class="sxs-lookup"><span data-stu-id="1936b-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="1936b-118">Le .NET Core SDK prend `<FrameworkReference>`en charge un `<PackageReference>`nouvel élément appelé , qui remplace l’utilisation de .</span><span class="sxs-lookup"><span data-stu-id="1936b-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="1936b-119">Pour plus d’informations, voir [dotnet/aspnetcore 3612](https://github.com/dotnet/aspnetcore/issues/3612).</span><span class="sxs-lookup"><span data-stu-id="1936b-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="1936b-120">Entity Framework Core navires comme paquets NuGet.</span><span class="sxs-lookup"><span data-stu-id="1936b-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="1936b-121">Cette modification aligne le modèle d’expédition avec toutes les autres bibliothèques d’accès aux données sur .NET.</span><span class="sxs-lookup"><span data-stu-id="1936b-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="1936b-122">Il fournit Entity Framework Core la voie la plus simple pour continuer à innover tout en soutenant les différentes plates-formes .NET.</span><span class="sxs-lookup"><span data-stu-id="1936b-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="1936b-123">Le transfert de Entity Framework Core hors du cadre partagé n’a aucun impact sur son statut de bibliothèque développée, soutenue et utilisable par Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1936b-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="1936b-124">La [politique de soutien de base .NET](https://www.microsoft.com/net/platform/support-policy) continue de la couvrir.</span><span class="sxs-lookup"><span data-stu-id="1936b-124">The [.NET Core support policy](https://www.microsoft.com/net/platform/support-policy) continues to cover it.</span></span>

<span data-ttu-id="1936b-125">Json.NET et le noyau cadre d’entité continuent de travailler avec ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1936b-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="1936b-126">Ils ne seront toutefois pas inclus dans le cadre commun.</span><span class="sxs-lookup"><span data-stu-id="1936b-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="1936b-127">Pour plus d’informations, voir [L’avenir de JSON dans .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span><span class="sxs-lookup"><span data-stu-id="1936b-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="1936b-128">Voir également [la liste complète des binaires retirés](https://github.com/dotnet/aspnetcore/issues/3755) du cadre partagé.</span><span class="sxs-lookup"><span data-stu-id="1936b-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1936b-129">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="1936b-129">Reason for change</span></span>

<span data-ttu-id="1936b-130">Ce changement simplifie `Microsoft.AspNetCore.App` la consommation et réduit les chevauchements entre les paquets NuGet et les cadres partagés.</span><span class="sxs-lookup"><span data-stu-id="1936b-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="1936b-131">Pour plus d’informations sur la motivation de ce changement, voir [ce blog](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="1936b-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1936b-132">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="1936b-132">Recommended action</span></span>

<span data-ttu-id="1936b-133">Il ne sera pas nécessaire pour les `Microsoft.AspNetCore.App` projets de consommer des assemblages en tant que paquets NuGet.</span><span class="sxs-lookup"><span data-stu-id="1936b-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="1936b-134">Pour simplifier le ciblage et l’utilisation du cadre partagé ASP.NET Core, de nombreux paquets NuGet expédiés depuis ASP.NET Core 1.0 ne sont plus produits.</span><span class="sxs-lookup"><span data-stu-id="1936b-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="1936b-135">Les API que ces paquets fournissent `<FrameworkReference>` sont `Microsoft.AspNetCore.App`toujours disponibles pour les applications en utilisant un à .</span><span class="sxs-lookup"><span data-stu-id="1936b-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="1936b-136">Kestrel, MVC et Razor sont des exemples courants d’API.</span><span class="sxs-lookup"><span data-stu-id="1936b-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="1936b-137">Ce changement ne s’applique pas à `Microsoft.AspNetCore.App` tous les binaires référencés via dans ASP.NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="1936b-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="1936b-138">Les exceptions notables comprennent :</span><span class="sxs-lookup"><span data-stu-id="1936b-138">Notable exceptions include:</span></span>

- <span data-ttu-id="1936b-139">`Microsoft.Extensions`bibliothèques qui continuent à cibler .NET Standard sera https://github.com/dotnet/extensions)disponible sous forme de forfaits NuGet (voir .</span><span class="sxs-lookup"><span data-stu-id="1936b-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see https://github.com/dotnet/extensions).</span></span>
- <span data-ttu-id="1936b-140">API produite par l’équipe ASP.NET Core qui `Microsoft.AspNetCore.App`ne font pas partie de .</span><span class="sxs-lookup"><span data-stu-id="1936b-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="1936b-141">Par exemple, les composants suivants sont disponibles sous forme de forfaits NuGet :</span><span class="sxs-lookup"><span data-stu-id="1936b-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="1936b-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1936b-142">Entity Framework Core</span></span>
  - <span data-ttu-id="1936b-143">API qui assurent l’intégration de tiers</span><span class="sxs-lookup"><span data-stu-id="1936b-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="1936b-144">Fonctionnalités expérimentales</span><span class="sxs-lookup"><span data-stu-id="1936b-144">Experimental features</span></span>
  - <span data-ttu-id="1936b-145">API avec des dépendances qui ne pouvaient pas [répondre aux exigences d’être dans le cadre partagé](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span><span class="sxs-lookup"><span data-stu-id="1936b-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="1936b-146">Extensions à MVC qui maintiennent le soutien pour Json.NET.</span><span class="sxs-lookup"><span data-stu-id="1936b-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="1936b-147">Une API sera fournie sous forme de forfait NuGet à prendre en charge à l’aide de Json.NET et de MVC.</span><span class="sxs-lookup"><span data-stu-id="1936b-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="1936b-148">Le client SignalR .NET continuera à prendre en charge .NET Standard et à expédier sous forme de forfait NuGet.</span><span class="sxs-lookup"><span data-stu-id="1936b-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="1936b-149">Il est destiné à une utilisation sur de nombreux runtimes .NET, tels que Xamarin et UWP.</span><span class="sxs-lookup"><span data-stu-id="1936b-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="1936b-150">Pour plus d’informations, voir [Arrêtez de produire des paquets pour les assemblages-cadres partagés en 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span><span class="sxs-lookup"><span data-stu-id="1936b-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="1936b-151">Pour discussion, voir [dotnet/aspnetcore 3757](https://github.com/dotnet/aspnetcore/issues/3757).</span><span class="sxs-lookup"><span data-stu-id="1936b-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="1936b-152">Category</span><span class="sxs-lookup"><span data-stu-id="1936b-152">Category</span></span>

<span data-ttu-id="1936b-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1936b-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1936b-154">API affectées</span><span class="sxs-lookup"><span data-stu-id="1936b-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->

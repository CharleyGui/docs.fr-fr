---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032676"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="a4580-101">SPAs : SpaServices et NodeServices marqués comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="a4580-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="a4580-102">Le contenu des packages NuGet suivants a été inutile depuis ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="a4580-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="a4580-103">Par conséquent, les packages suivants sont marqués comme obsolètes :</span><span class="sxs-lookup"><span data-stu-id="a4580-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="a4580-104">Microsoft. AspNetCore. SpaServices</span><span class="sxs-lookup"><span data-stu-id="a4580-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="a4580-105">Microsoft. AspNetCore. NodeServices</span><span class="sxs-lookup"><span data-stu-id="a4580-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="a4580-106">Pour la même raison, les modules NPM suivants sont marqués comme dépréciés :</span><span class="sxs-lookup"><span data-stu-id="a4580-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="a4580-107">ASPNET-angulaire</span><span class="sxs-lookup"><span data-stu-id="a4580-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="a4580-108">ASPNET-prérendu</span><span class="sxs-lookup"><span data-stu-id="a4580-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="a4580-109">ASPNET-WebPack</span><span class="sxs-lookup"><span data-stu-id="a4580-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="a4580-110">ASPNET-WebPack-réagir</span><span class="sxs-lookup"><span data-stu-id="a4580-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="a4580-111">domaine-tâche</span><span class="sxs-lookup"><span data-stu-id="a4580-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="a4580-112">Les packages précédents et les modules NPM seront supprimés ultérieurement dans .NET 5.</span><span class="sxs-lookup"><span data-stu-id="a4580-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a4580-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a4580-113">Version introduced</span></span>

<span data-ttu-id="a4580-114">3.0</span><span class="sxs-lookup"><span data-stu-id="a4580-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a4580-115">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a4580-115">Old behavior</span></span>

<span data-ttu-id="a4580-116">Les packages déconseillés et les modules NPM étaient destinés à intégrer des ASP.NET Core avec différentes infrastructures d’application Single-Page (SPA).</span><span class="sxs-lookup"><span data-stu-id="a4580-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="a4580-117">Ces infrastructures incluent l’angle, la réaction et la réaction avec Redux.</span><span class="sxs-lookup"><span data-stu-id="a4580-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a4580-118">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a4580-118">New behavior</span></span>

<span data-ttu-id="a4580-119">Un nouveau mécanisme d’intégration existe dans le package NuGet [Microsoft. AspNetCore. SpaServices. extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) .</span><span class="sxs-lookup"><span data-stu-id="a4580-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="a4580-120">Le package reste la base des modèles de projet angulaire et REACT depuis ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="a4580-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a4580-121">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a4580-121">Reason for change</span></span>

<span data-ttu-id="a4580-122">ASP.NET Core prend en charge l’intégration avec différentes infrastructures d’application Single-Page (SPA), y compris angulaires, réagir et réagir avec Redux.</span><span class="sxs-lookup"><span data-stu-id="a4580-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="a4580-123">Initialement, l’intégration à ces frameworks a été effectuée avec des composants spécifiques à ASP.NET Core qui géraient des scénarios tels que le prérendu côté serveur et l’intégration à WebPack.</span><span class="sxs-lookup"><span data-stu-id="a4580-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="a4580-124">À l’époque, les normes du secteur ont changé.</span><span class="sxs-lookup"><span data-stu-id="a4580-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="a4580-125">Chacun des frameworks SPA a publié ses propres interfaces de ligne de commande standard.</span><span class="sxs-lookup"><span data-stu-id="a4580-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="a4580-126">Par exemple, l’interface CLI angulaire et Create-REACT-App.</span><span class="sxs-lookup"><span data-stu-id="a4580-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="a4580-127">Lorsque ASP.NET Core 2,1 a été publié en mai 2018, l’équipe a répondu au changement de normes.</span><span class="sxs-lookup"><span data-stu-id="a4580-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="a4580-128">Un moyen plus récent et plus simple d’intégrer les chaînes propres aux frameworks SPA a été fourni.</span><span class="sxs-lookup"><span data-stu-id="a4580-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="a4580-129">Le nouveau mécanisme d’intégration existe dans le package `Microsoft.AspNetCore.SpaServices.Extensions` et reste la base des modèles de projet angulaires et réagi depuis ASP.NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="a4580-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="a4580-130">Pour préciser que les anciens composants spécifiques à ASP.NET Core sont sans importance et déconseillés :</span><span class="sxs-lookup"><span data-stu-id="a4580-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="a4580-131">Le mécanisme d’intégration antérieur à 2,1 est marqué comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="a4580-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="a4580-132">Les packages de NPM de prise en charge sont marqués comme dépréciés.</span><span class="sxs-lookup"><span data-stu-id="a4580-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a4580-133">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a4580-133">Recommended action</span></span>

<span data-ttu-id="a4580-134">Si vous utilisez ces packages, mettez à jour vos applications pour qu’elles utilisent les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="a4580-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="a4580-135">Dans le `Microsoft.AspNetCore.SpaServices.Extensions` Package.</span><span class="sxs-lookup"><span data-stu-id="a4580-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="a4580-136">Fourni par les infrastructures SPA que vous utilisez</span><span class="sxs-lookup"><span data-stu-id="a4580-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="a4580-137">Pour activer des fonctionnalités telles que le prérendu côté serveur et le rechargement des modules à chaud, consultez la documentation de l’infrastructure SPA correspondante.</span><span class="sxs-lookup"><span data-stu-id="a4580-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="a4580-138">Les fonctionnalités dans ne `Microsoft.AspNetCore.SpaServices.Extensions` sont *pas* obsolètes et continuent d’être prises en charge.</span><span class="sxs-lookup"><span data-stu-id="a4580-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="a4580-139">Category</span><span class="sxs-lookup"><span data-stu-id="a4580-139">Category</span></span>

<span data-ttu-id="a4580-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4580-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a4580-141">API affectées</span><span class="sxs-lookup"><span data-stu-id="a4580-141">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.SpaRouteExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.WebpackDevMiddleware?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.INodeServices?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesFactory?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.NodeServicesOptions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.StringAsTempFile?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance?displayProperty=nameWithType>

- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions?displayProperty=nameWithType>

- <xref:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Builder.SpaRouteExtensions`
- `T:Microsoft.AspNetCore.Builder.WebpackDevMiddleware`

- `T:Microsoft.AspNetCore.NodeServices.EmbeddedResourceReader`
- `T:Microsoft.AspNetCore.NodeServices.INodeServices`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesFactory`
- `T:Microsoft.AspNetCore.NodeServices.NodeServicesOptions`
- `T:Microsoft.AspNetCore.NodeServices.StringAsTempFile`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.INodeInstance`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationException`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeInvocationInfo`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.NodeServicesOptionsExtensions`
- `T:Microsoft.AspNetCore.NodeServices.HostingModels.OutOfProcessNodeInstance`

- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.ISpaPrerendererBuilder`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.JavaScriptModuleExport`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.Prerenderer`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.PrerenderTagHelper`
- `T:Microsoft.AspNetCore.SpaServices.Prerendering.RenderToStringResult`
- `T:Microsoft.AspNetCore.SpaServices.Webpack.WebpackDevMiddlewareOptions`

- `T:Microsoft.Extensions.DependencyInjection.NodeServicesServiceCollectionExtensions`
- `T:Microsoft.Extensions.DependencyInjection.PrerenderingServiceCollectionExtensions`

-->

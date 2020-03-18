---
ms.openlocfilehash: ac5a3c4f3aefbb59418ad92b2d795f36916f877f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394479"
---
### <a name="spas-spaservices-and-nodeservices-marked-obsolete"></a><span data-ttu-id="58658-101">SPAs: SpaServices et NodeServices marqués obsolètes</span><span class="sxs-lookup"><span data-stu-id="58658-101">SPAs: SpaServices and NodeServices marked obsolete</span></span>

<span data-ttu-id="58658-102">Le contenu des paquets NuGet suivants n’ont pas été nécessaires depuis ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="58658-102">The contents of the following NuGet packages have all been unnecessary since ASP.NET Core 2.1.</span></span> <span data-ttu-id="58658-103">Par conséquent, les paquets suivants sont marqués comme obsolètes :</span><span class="sxs-lookup"><span data-stu-id="58658-103">Consequently, the following packages are being marked as obsolete:</span></span>

- [<span data-ttu-id="58658-104">Microsoft.AspNetCore.SpaServices (en anglais seulement)</span><span class="sxs-lookup"><span data-stu-id="58658-104">Microsoft.AspNetCore.SpaServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices/)
- [<span data-ttu-id="58658-105">Microsoft.AspNetCore.NodeServices (en anglais seulement)</span><span class="sxs-lookup"><span data-stu-id="58658-105">Microsoft.AspNetCore.NodeServices</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.NodeServices/)

<span data-ttu-id="58658-106">Pour la même raison, les modules npm suivants sont marqués comme dépréciés :</span><span class="sxs-lookup"><span data-stu-id="58658-106">For the same reason, the following npm modules are being marked as deprecated:</span></span>

- [<span data-ttu-id="58658-107">aspnet-angulaire</span><span class="sxs-lookup"><span data-stu-id="58658-107">aspnet-angular</span></span>](https://www.npmjs.com/package/aspnet-angular)
- [<span data-ttu-id="58658-108">aspnet-prerendering</span><span class="sxs-lookup"><span data-stu-id="58658-108">aspnet-prerendering</span></span>](https://www.npmjs.com/package/aspnet-prerendering)
- [<span data-ttu-id="58658-109">aspnet-webpack</span><span class="sxs-lookup"><span data-stu-id="58658-109">aspnet-webpack</span></span>](https://www.npmjs.com/package/aspnet-webpack)
- [<span data-ttu-id="58658-110">aspnet-webpack-réagir</span><span class="sxs-lookup"><span data-stu-id="58658-110">aspnet-webpack-react</span></span>](https://www.npmjs.com/package/aspnet-webpack-react)
- [<span data-ttu-id="58658-111">domaine-tâche</span><span class="sxs-lookup"><span data-stu-id="58658-111">domain-task</span></span>](https://www.npmjs.com/package/domain-task)

<span data-ttu-id="58658-112">Les paquets précédents et les modules npm seront plus tard supprimés en .NET 5.</span><span class="sxs-lookup"><span data-stu-id="58658-112">The preceding packages and npm modules will later be removed in .NET 5.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="58658-113">Version introduite</span><span class="sxs-lookup"><span data-stu-id="58658-113">Version introduced</span></span>

<span data-ttu-id="58658-114">3.0</span><span class="sxs-lookup"><span data-stu-id="58658-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="58658-115">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="58658-115">Old behavior</span></span>

<span data-ttu-id="58658-116">Les paquets dépréciés et les modules npm étaient destinés à intégrer ASP.NET Core avec divers cadres d’application à une page unique (SPA).</span><span class="sxs-lookup"><span data-stu-id="58658-116">The deprecated packages and npm modules were intended to integrate ASP.NET Core with various Single-Page App (SPA) frameworks.</span></span> <span data-ttu-id="58658-117">Ces cadres incluent Angular, React, et React with Redux.</span><span class="sxs-lookup"><span data-stu-id="58658-117">Such frameworks include Angular, React, and React with Redux.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="58658-118">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="58658-118">New behavior</span></span>

<span data-ttu-id="58658-119">Un nouveau mécanisme d’intégration existe dans le paquet [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet.</span><span class="sxs-lookup"><span data-stu-id="58658-119">A new integration mechanism exists in the [Microsoft.AspNetCore.SpaServices.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.SpaServices.Extensions/) NuGet package.</span></span> <span data-ttu-id="58658-120">Le paquet demeure la base des modèles de projet Angular and React depuis ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="58658-120">The package remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="58658-121">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="58658-121">Reason for change</span></span>

<span data-ttu-id="58658-122">ASP.NET Core soutient l’intégration avec divers cadres d’applications à une seule page (SPA), y compris Angulaire, Réagir et réagir avec Redux.</span><span class="sxs-lookup"><span data-stu-id="58658-122">ASP.NET Core supports integration with various Single-Page App (SPA) frameworks, including Angular, React, and React with Redux.</span></span> <span data-ttu-id="58658-123">Initialement, l’intégration avec ces cadres a été réalisée avec ASP.NET composants core-spécifiques qui traitaient des scénarios comme le prerendering côté serveur et l’intégration avec Webpack.</span><span class="sxs-lookup"><span data-stu-id="58658-123">Initially, integration with these frameworks was accomplished with ASP.NET Core-specific components that handled scenarios like server-side prerendering and integration with Webpack.</span></span> <span data-ttu-id="58658-124">Au fil du temps, les normes de l’industrie ont changé.</span><span class="sxs-lookup"><span data-stu-id="58658-124">As time went on, industry standards changed.</span></span> <span data-ttu-id="58658-125">Chacun des cadres SPA a publié ses propres interfaces standard de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="58658-125">Each of the SPA frameworks released their own standard command-line interfaces.</span></span> <span data-ttu-id="58658-126">Par exemple, Angular CLI et create-react-app.</span><span class="sxs-lookup"><span data-stu-id="58658-126">For example, Angular CLI and create-react-app.</span></span>

<span data-ttu-id="58658-127">Lorsque ASP.NET Core 2.1 a été publié en mai 2018, l’équipe a réagi à la modification des normes.</span><span class="sxs-lookup"><span data-stu-id="58658-127">When ASP.NET Core 2.1 was released in May 2018, the team responded to the change in standards.</span></span> <span data-ttu-id="58658-128">Une façon plus nouvelle et plus simple de s’intégrer aux propres chaînes d’outils des cadres SPA a été fournie.</span><span class="sxs-lookup"><span data-stu-id="58658-128">A newer and simpler way to integrate with the SPA frameworks' own toolchains was provided.</span></span> <span data-ttu-id="58658-129">Le nouveau mécanisme d’intégration `Microsoft.AspNetCore.SpaServices.Extensions` existe dans le paquet et demeure la base des modèles de projets Angular et React depuis ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="58658-129">The new integration mechanism exists in the package `Microsoft.AspNetCore.SpaServices.Extensions` and remains the basis of the Angular and React project templates since ASP.NET Core 2.1.</span></span>

<span data-ttu-id="58658-130">Pour préciser que les composants les plus anciens ASP.NET propres au noyau ne sont pas pertinents et ne sont pas recommandés :</span><span class="sxs-lookup"><span data-stu-id="58658-130">To clarify that the older ASP.NET Core-specific components are irrelevant and not recommended:</span></span>

- <span data-ttu-id="58658-131">Le mécanisme d’intégration avant 2,1 est considéré comme obsolète.</span><span class="sxs-lookup"><span data-stu-id="58658-131">The pre-2.1 integration mechanism is marked as obsolete.</span></span>
- <span data-ttu-id="58658-132">Les forfaits npm de soutien sont marqués comme dépréciés.</span><span class="sxs-lookup"><span data-stu-id="58658-132">The supporting npm packages are marked as deprecated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="58658-133">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="58658-133">Recommended action</span></span>

<span data-ttu-id="58658-134">Si vous utilisez ces paquets, mettez à jour vos applications pour utiliser les fonctionnalités :</span><span class="sxs-lookup"><span data-stu-id="58658-134">If you're using these packages, update your apps to use the functionality:</span></span>

- <span data-ttu-id="58658-135">Dans `Microsoft.AspNetCore.SpaServices.Extensions` le paquet.</span><span class="sxs-lookup"><span data-stu-id="58658-135">In the `Microsoft.AspNetCore.SpaServices.Extensions` package.</span></span>
- <span data-ttu-id="58658-136">Fourni par les cadres SPA que vous utilisez</span><span class="sxs-lookup"><span data-stu-id="58658-136">Provided by the SPA frameworks you're using</span></span>

<span data-ttu-id="58658-137">Pour activer des fonctionnalités telles que le prerendering côté serveur et le rechargement du module chaud, consultez la documentation du cadre SPA correspondant.</span><span class="sxs-lookup"><span data-stu-id="58658-137">To enable features like server-side prerendering and hot module reload, see the documentation for the corresponding SPA framework.</span></span> <span data-ttu-id="58658-138">La fonctionnalité `Microsoft.AspNetCore.SpaServices.Extensions` n’est *pas* obsolète et continuera d’être prise en charge.</span><span class="sxs-lookup"><span data-stu-id="58658-138">The functionality in `Microsoft.AspNetCore.SpaServices.Extensions` is *not* obsolete and will continue to be supported.</span></span>

#### <a name="category"></a><span data-ttu-id="58658-139">Category</span><span class="sxs-lookup"><span data-stu-id="58658-139">Category</span></span>

<span data-ttu-id="58658-140">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="58658-140">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="58658-141">API affectées</span><span class="sxs-lookup"><span data-stu-id="58658-141">Affected APIs</span></span>

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

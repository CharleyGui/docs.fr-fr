---
title: 'Modification avec rupture : autorisation : la ressource dans le routage du point de terminaison est HttpContext'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée autorisation : la ressource dans le routage du point de terminaison est HttpContext'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 7c5a77cb8999c60a7780b9b4f7ad2a1c79fd8310
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761244"
---
# <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="55cc2-103">Autorisation : la ressource dans le routage du point de terminaison est HttpContext</span><span class="sxs-lookup"><span data-stu-id="55cc2-103">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="55cc2-104">Lors de l’utilisation du routage de point de terminaison dans ASP.NET Core 3,1, la ressource utilisée pour l’autorisation est le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="55cc2-104">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="55cc2-105">Cette approche était insuffisante pour accéder aux données de route ( <xref:Microsoft.AspNetCore.Routing.RouteData> ).</span><span class="sxs-lookup"><span data-stu-id="55cc2-105">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="55cc2-106">Précédemment dans MVC, une <xref:Microsoft.AspNetCore.Http.HttpContext> ressource était passée, ce qui permet l’accès au point de terminaison ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) et aux données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="55cc2-106">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="55cc2-107">Cette modification garantit que la ressource transmise à l’autorisation est toujours la `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="55cc2-107">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="55cc2-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="55cc2-108">Version introduced</span></span>

<span data-ttu-id="55cc2-109">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="55cc2-109">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="55cc2-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="55cc2-110">Old behavior</span></span>

<span data-ttu-id="55cc2-111">Lorsque vous utilisez le routage de point de terminaison et les attributs d’autorisation ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) ou [Authorize []](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) , la ressource passée à l’autorisation est le point de terminaison correspondant.</span><span class="sxs-lookup"><span data-stu-id="55cc2-111">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="55cc2-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="55cc2-112">New behavior</span></span>

<span data-ttu-id="55cc2-113">Le routage des points de terminaison transmet le `HttpContext` à l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="55cc2-113">Endpoint routing passes the `HttpContext` to authorization.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="55cc2-114">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="55cc2-114">Reason for change</span></span>

<span data-ttu-id="55cc2-115">Vous pouvez accéder au point de terminaison à partir du `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="55cc2-115">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="55cc2-116">Toutefois, il n’existait aucun moyen de passer du point de terminaison à des choses telles que les données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="55cc2-116">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="55cc2-117">Une perte de fonctionnalité du routage non-point de terminaison a été perdue.</span><span class="sxs-lookup"><span data-stu-id="55cc2-117">There was a loss in functionality from non-endpoint routing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="55cc2-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="55cc2-118">Recommended action</span></span>

<span data-ttu-id="55cc2-119">Si votre application utilise la ressource de point de terminaison, appelez <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> sur `HttpContext` pour continuer à accéder au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="55cc2-119">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="55cc2-120">Dans ASP.NET Core 5,0 Preview 8 et versions ultérieures, vous pouvez revenir à l’ancien comportement avec <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="55cc2-120">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="55cc2-121">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="55cc2-121">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

## <a name="affected-apis"></a><span data-ttu-id="55cc2-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="55cc2-122">Affected APIs</span></span>

<span data-ttu-id="55cc2-123">None</span><span class="sxs-lookup"><span data-stu-id="55cc2-123">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

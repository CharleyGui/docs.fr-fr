---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441546"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="26c0d-101">Autorisation : la ressource dans le routage du point de terminaison est HttpContext</span><span class="sxs-lookup"><span data-stu-id="26c0d-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="26c0d-102">Lors de l’utilisation du routage de point de terminaison dans ASP.NET Core 3,1, la ressource utilisée pour l’autorisation est le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="26c0d-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="26c0d-103">Cette approche était insuffisante pour accéder aux données de route ( <xref:Microsoft.AspNetCore.Routing.RouteData> ).</span><span class="sxs-lookup"><span data-stu-id="26c0d-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="26c0d-104">Précédemment dans MVC, une <xref:Microsoft.AspNetCore.Http.HttpContext> ressource était passée, ce qui permet l’accès au point de terminaison ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) et aux données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="26c0d-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="26c0d-105">Cette modification garantit que la ressource transmise à l’autorisation est toujours la `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="26c0d-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="26c0d-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="26c0d-106">Version introduced</span></span>

<span data-ttu-id="26c0d-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="26c0d-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="26c0d-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="26c0d-108">Old behavior</span></span>

<span data-ttu-id="26c0d-109">Lorsque vous utilisez le routage de point de terminaison et les attributs d’autorisation ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) ou [Authorize []](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) , la ressource passée à l’autorisation est le point de terminaison correspondant.</span><span class="sxs-lookup"><span data-stu-id="26c0d-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="26c0d-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="26c0d-110">New behavior</span></span>

<span data-ttu-id="26c0d-111">Le routage des points de terminaison transmet le `HttpContext` à l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="26c0d-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="26c0d-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="26c0d-112">Reason for change</span></span>

<span data-ttu-id="26c0d-113">Vous pouvez accéder au point de terminaison à partir du `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="26c0d-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="26c0d-114">Toutefois, il n’existait aucun moyen de passer du point de terminaison à des choses telles que les données d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="26c0d-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="26c0d-115">Une perte de fonctionnalité du routage non-point de terminaison a été perdue.</span><span class="sxs-lookup"><span data-stu-id="26c0d-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="26c0d-116">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="26c0d-116">Recommended action</span></span>

<span data-ttu-id="26c0d-117">Si votre application utilise la ressource de point de terminaison, appelez <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> sur `HttpContext` pour continuer à accéder au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="26c0d-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="26c0d-118">Dans ASP.NET Core 5,0 Preview 8 et versions ultérieures, vous pouvez revenir à l’ancien comportement avec <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="26c0d-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="26c0d-119">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="26c0d-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="26c0d-120">Category</span><span class="sxs-lookup"><span data-stu-id="26c0d-120">Category</span></span>

<span data-ttu-id="26c0d-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="26c0d-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="26c0d-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="26c0d-122">Affected APIs</span></span>

<span data-ttu-id="26c0d-123">Aucun</span><span class="sxs-lookup"><span data-stu-id="26c0d-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

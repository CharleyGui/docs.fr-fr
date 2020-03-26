---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291638"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="09f97-101">SignalR: UtilisationSignalR et UseConnections méthodes supprimées</span><span class="sxs-lookup"><span data-stu-id="09f97-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="09f97-102">Dans ASP.NET Core 3.0, SignalR a adopté le routage de point final.</span><span class="sxs-lookup"><span data-stu-id="09f97-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="09f97-103">Dans le cadre de <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>ce changement, le , et certaines méthodes connexes ont été marqués comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="09f97-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="09f97-104">Dans ASP.NET Core 5.0, ces méthodes obsolètes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="09f97-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="09f97-105">Pour la liste complète des méthodes, voir [API affectées](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="09f97-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="09f97-106">Pour discussion sur cette question, voir [dotnet/aspnetcore-20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="09f97-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="09f97-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="09f97-107">Version introduced</span></span>

<span data-ttu-id="09f97-108">5.0 Aperçu 3</span><span class="sxs-lookup"><span data-stu-id="09f97-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="09f97-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="09f97-109">Old behavior</span></span>

<span data-ttu-id="09f97-110">Les hubs SignalR et les gestionnaires de connexion `UseSignalR` peuvent `UseConnections` être enregistrés dans le pipeline middleware en utilisant le ou les méthodes.</span><span class="sxs-lookup"><span data-stu-id="09f97-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="09f97-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="09f97-111">New behavior</span></span>

<span data-ttu-id="09f97-112">Les hubs SignalR et les <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> gestionnaires <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> de <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> connexion <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>doivent être enregistrés à l’intérieur à l’aide des méthodes et des méthodes d’extension sur .</span><span class="sxs-lookup"><span data-stu-id="09f97-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="09f97-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="09f97-113">Reason for change</span></span>

<span data-ttu-id="09f97-114">Les anciennes méthodes avaient une logique de routage personnalisée qui n’interagissait pas avec d’autres composants de routage dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="09f97-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="09f97-115">Dans ASP.NET Core 3.0, un nouveau système de routage à usage général, appelé itinéraire par point final, a été introduit.</span><span class="sxs-lookup"><span data-stu-id="09f97-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="09f97-116">Le routage de point de terminaison a permis à SignalR d’interagir avec d’autres composants de routage.</span><span class="sxs-lookup"><span data-stu-id="09f97-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="09f97-117">Le passage à ce modèle permet aux utilisateurs de réaliser tous les avantages du routage par point final.</span><span class="sxs-lookup"><span data-stu-id="09f97-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="09f97-118">Par conséquent, les anciennes méthodes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="09f97-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09f97-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="09f97-119">Recommended action</span></span>

<span data-ttu-id="09f97-120">Supprimez le `UseSignalR` `UseConnections` code qui appelle `Startup.Configure` ou de la méthode de votre projet.</span><span class="sxs-lookup"><span data-stu-id="09f97-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="09f97-121">Remplacez-le `MapHub` par `MapConnectionHandler`des appels vers ou, `UseEndpoints`respectivement, dans le corps d’un appel à .</span><span class="sxs-lookup"><span data-stu-id="09f97-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="09f97-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="09f97-122">For example:</span></span>

<span data-ttu-id="09f97-123">**Ancien code:**</span><span class="sxs-lookup"><span data-stu-id="09f97-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="09f97-124">**Nouveau code :**</span><span class="sxs-lookup"><span data-stu-id="09f97-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="09f97-125">En général, `MapHub` vos `MapConnectionHandler` appels précédents et peuvent `UseSignalR` être `UseConnections` `UseEndpoints` transférés directement du corps de et vers avec peu ou pas de changement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="09f97-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="09f97-126">Category</span><span class="sxs-lookup"><span data-stu-id="09f97-126">Category</span></span>

<span data-ttu-id="09f97-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="09f97-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09f97-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="09f97-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->

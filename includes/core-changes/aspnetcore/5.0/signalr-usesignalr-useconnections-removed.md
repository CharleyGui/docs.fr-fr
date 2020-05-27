---
ms.openlocfilehash: 329ef39c7626ecd743577f336a4c8cd4a38fb082
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291638"
---
### <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="d63db-101">Signalr : les méthodes UseSignalR et UseConnections ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="d63db-101">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="d63db-102">Dans ASP.NET Core 3,0, Signalr a adopté le routage du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d63db-102">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="d63db-103">Dans le cadre de cette modification, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> , <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> et certaines méthodes associées ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="d63db-103">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="d63db-104">Dans ASP.NET Core 5,0, ces méthodes obsolètes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="d63db-104">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="d63db-105">Pour obtenir la liste complète des méthodes, consultez [API affectées](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="d63db-105">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="d63db-106">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="d63db-106">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d63db-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d63db-107">Version introduced</span></span>

<span data-ttu-id="d63db-108">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="d63db-108">5.0 Preview 3</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d63db-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d63db-109">Old behavior</span></span>

<span data-ttu-id="d63db-110">Les hubs signalr et les gestionnaires de connexions peuvent être enregistrés dans le pipeline de l’intergiciel (middleware) à l’aide des `UseSignalR` `UseConnections` méthodes ou.</span><span class="sxs-lookup"><span data-stu-id="d63db-110">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d63db-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d63db-111">New behavior</span></span>

<span data-ttu-id="d63db-112">Les hubs et les gestionnaires de connexion signalr doivent être inscrits dans <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> à l’aide des <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> méthodes d’extension et sur <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="d63db-112">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d63db-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d63db-113">Reason for change</span></span>

<span data-ttu-id="d63db-114">Les anciennes méthodes ont une logique de routage personnalisée qui n’interagit pas avec d’autres composants de routage dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d63db-114">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="d63db-115">Dans ASP.NET Core 3,0, un nouveau système de routage à usage général, appelé routage des points de terminaison, a été introduit.</span><span class="sxs-lookup"><span data-stu-id="d63db-115">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="d63db-116">Routage des points de terminaison activé Signalr pour interagir avec d’autres composants de routage.</span><span class="sxs-lookup"><span data-stu-id="d63db-116">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="d63db-117">Le passage à ce modèle permet aux utilisateurs de bénéficier de tous les avantages du routage des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="d63db-117">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="d63db-118">Par conséquent, les anciennes méthodes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="d63db-118">Consequently, the old methods have been removed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d63db-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d63db-119">Recommended action</span></span>

<span data-ttu-id="d63db-120">Supprimez le code qui appelle `UseSignalR` ou `UseConnections` de la méthode de votre projet `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="d63db-120">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="d63db-121">Remplacez-le par des appels à `MapHub` ou `MapConnectionHandler` , respectivement, dans le corps d’un appel à `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="d63db-121">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="d63db-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="d63db-122">For example:</span></span>

<span data-ttu-id="d63db-123">**Ancien code :**</span><span class="sxs-lookup"><span data-stu-id="d63db-123">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="d63db-124">**Nouveau code :**</span><span class="sxs-lookup"><span data-stu-id="d63db-124">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="d63db-125">En général, vos `MapHub` appels précédents et `MapConnectionHandler` peuvent être transférés directement à partir du corps de `UseSignalR` et `UseConnections` vers avec un minimum de `UseEndpoints` modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="d63db-125">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

#### <a name="category"></a><span data-ttu-id="d63db-126">Category</span><span class="sxs-lookup"><span data-stu-id="d63db-126">Category</span></span>

<span data-ttu-id="d63db-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d63db-127">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d63db-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="d63db-128">Affected APIs</span></span>

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

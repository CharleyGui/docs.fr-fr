---
title: 'Modification avec rupture : Signalr : les méthodes UseSignalR et UseConnections ont été supprimées'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 Signalr : les méthodes UseSignalR et UseConnections ont été supprimées'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 1b1fce04518e69927cdc1650cc1e19107cc81e3b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760892"
---
# <a name="signalr-usesignalr-and-useconnections-methods-removed"></a><span data-ttu-id="2d52c-103">Signalr : les méthodes UseSignalR et UseConnections ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="2d52c-103">SignalR: UseSignalR and UseConnections methods removed</span></span>

<span data-ttu-id="2d52c-104">Dans ASP.NET Core 3,0, Signalr a adopté le routage du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2d52c-104">In ASP.NET Core 3.0, SignalR adopted endpoint routing.</span></span> <span data-ttu-id="2d52c-105">Dans le cadre de cette modification, <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A> , <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A> et certaines méthodes associées ont été marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="2d52c-105">As part of that change, the <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A>, <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A>, and some related methods were marked as obsolete.</span></span> <span data-ttu-id="2d52c-106">Dans ASP.NET Core 5,0, ces méthodes obsolètes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="2d52c-106">In ASP.NET Core 5.0, those obsolete methods were removed.</span></span> <span data-ttu-id="2d52c-107">Pour obtenir la liste complète des méthodes, consultez [API affectées](#affected-apis).</span><span class="sxs-lookup"><span data-stu-id="2d52c-107">For the full list of methods, see [Affected APIs](#affected-apis).</span></span>

<span data-ttu-id="2d52c-108">Pour plus d’informations sur ce problème, consultez [dotnet/aspnetcore # 20082](https://github.com/dotnet/aspnetcore/issues/20082).</span><span class="sxs-lookup"><span data-stu-id="2d52c-108">For discussion on this issue, see [dotnet/aspnetcore#20082](https://github.com/dotnet/aspnetcore/issues/20082).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2d52c-109">Version introduite</span><span class="sxs-lookup"><span data-stu-id="2d52c-109">Version introduced</span></span>

<span data-ttu-id="2d52c-110">5,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="2d52c-110">5.0 Preview 3</span></span>

## <a name="old-behavior"></a><span data-ttu-id="2d52c-111">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="2d52c-111">Old behavior</span></span>

<span data-ttu-id="2d52c-112">Les hubs signalr et les gestionnaires de connexions peuvent être enregistrés dans le pipeline de l’intergiciel (middleware) à l’aide des `UseSignalR` `UseConnections` méthodes ou.</span><span class="sxs-lookup"><span data-stu-id="2d52c-112">SignalR hubs and connection handlers could be registered in the middleware pipeline using the `UseSignalR` or `UseConnections` methods.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="2d52c-113">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="2d52c-113">New behavior</span></span>

<span data-ttu-id="2d52c-114">Les hubs et les gestionnaires de connexion signalr doivent être inscrits dans <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> à l’aide des <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> méthodes d’extension et sur <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder> .</span><span class="sxs-lookup"><span data-stu-id="2d52c-114">SignalR hubs and connection handlers should be registered within <xref:Microsoft.AspNetCore.Builder.EndpointRoutingApplicationBuilderExtensions.UseEndpoints%2A> using the <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A> and <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A> extension methods on <xref:Microsoft.AspNetCore.Routing.IEndpointRouteBuilder>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="2d52c-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="2d52c-115">Reason for change</span></span>

<span data-ttu-id="2d52c-116">Les anciennes méthodes ont une logique de routage personnalisée qui n’interagit pas avec d’autres composants de routage dans ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2d52c-116">The old methods had custom routing logic that didn't interact with other routing components in ASP.NET Core.</span></span> <span data-ttu-id="2d52c-117">Dans ASP.NET Core 3,0, un nouveau système de routage à usage général, appelé routage des points de terminaison, a été introduit.</span><span class="sxs-lookup"><span data-stu-id="2d52c-117">In ASP.NET Core 3.0, a new general-purpose routing system, called endpoint routing, was introduced.</span></span> <span data-ttu-id="2d52c-118">Routage des points de terminaison activé Signalr pour interagir avec d’autres composants de routage.</span><span class="sxs-lookup"><span data-stu-id="2d52c-118">Endpoint routing enabled SignalR to interact with other routing components.</span></span> <span data-ttu-id="2d52c-119">Le passage à ce modèle permet aux utilisateurs de bénéficier de tous les avantages du routage des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2d52c-119">Switching to this model allows users to realize the full benefits of endpoint routing.</span></span> <span data-ttu-id="2d52c-120">Par conséquent, les anciennes méthodes ont été supprimées.</span><span class="sxs-lookup"><span data-stu-id="2d52c-120">Consequently, the old methods have been removed.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2d52c-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="2d52c-121">Recommended action</span></span>

<span data-ttu-id="2d52c-122">Supprimez le code qui appelle `UseSignalR` ou `UseConnections` de la méthode de votre projet `Startup.Configure` .</span><span class="sxs-lookup"><span data-stu-id="2d52c-122">Remove code that calls `UseSignalR` or `UseConnections` from your project's `Startup.Configure` method.</span></span> <span data-ttu-id="2d52c-123">Remplacez-le par des appels à `MapHub` ou `MapConnectionHandler` , respectivement, dans le corps d’un appel à `UseEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="2d52c-123">Replace it with calls to `MapHub` or `MapConnectionHandler`, respectively, within the body of a call to `UseEndpoints`.</span></span> <span data-ttu-id="2d52c-124">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2d52c-124">For example:</span></span>

<span data-ttu-id="2d52c-125">**Ancien code :**</span><span class="sxs-lookup"><span data-stu-id="2d52c-125">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="2d52c-126">**Nouveau code :**</span><span class="sxs-lookup"><span data-stu-id="2d52c-126">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="2d52c-127">En général, vos `MapHub` appels précédents et `MapConnectionHandler` peuvent être transférés directement à partir du corps de `UseSignalR` et `UseConnections` vers avec un minimum de `UseEndpoints` modifications nécessaires.</span><span class="sxs-lookup"><span data-stu-id="2d52c-127">In general, your previous `MapHub` and `MapConnectionHandler` calls can be transferred directly from the body of `UseSignalR` and `UseConnections` to `UseEndpoints` with little-to-no change needed.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2d52c-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="2d52c-128">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections`
- `Overload:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnections`
- `Overload:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder.MapConnectionHandler`
- `Overload:Microsoft.AspNetCore.SignalR.HubRouteBuilder.MapHub`

-->

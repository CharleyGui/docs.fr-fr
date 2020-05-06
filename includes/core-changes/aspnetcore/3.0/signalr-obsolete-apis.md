---
ms.openlocfilehash: 2a65caedea2af65796267aa145e275ebff814bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394090"
---
### <a name="signalr-usesignalr-and-useconnections-methods-marked-obsolete"></a><span data-ttu-id="c6d4e-101">Signalr : méthodes UseSignalR et UseConnections marquées comme obsolètes</span><span class="sxs-lookup"><span data-stu-id="c6d4e-101">SignalR: UseSignalR and UseConnections methods marked obsolete</span></span>

<span data-ttu-id="c6d4e-102">Les méthodes `UseConnections` et `UseSignalR` `ConnectionsRouteBuilder` et et `HubRouteBuilder` sont marquées comme obsolètes dans ASP.net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="c6d4e-102">The methods `UseConnections` and `UseSignalR` and the classes `ConnectionsRouteBuilder` and `HubRouteBuilder` are marked as obsolete in ASP.NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c6d4e-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c6d4e-103">Version introduced</span></span>

<span data-ttu-id="c6d4e-104">3.0</span><span class="sxs-lookup"><span data-stu-id="c6d4e-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c6d4e-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="c6d4e-105">Old behavior</span></span>

<span data-ttu-id="c6d4e-106">Le routage du concentrateur signalr `UseSignalR` a `UseConnections`été configuré à l’aide de ou.</span><span class="sxs-lookup"><span data-stu-id="c6d4e-106">SignalR hub routing was configured using `UseSignalR` or `UseConnections`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c6d4e-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="c6d4e-107">New behavior</span></span>

<span data-ttu-id="c6d4e-108">L’ancienne méthode de configuration du routage a été obsolète et remplacée par le routage des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c6d4e-108">The old way of configuring routing has been obsoleted and replaced with endpoint routing.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c6d4e-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="c6d4e-109">Reason for change</span></span>

<span data-ttu-id="c6d4e-110">Le middleware est déplacé vers le nouveau système de routage des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c6d4e-110">Middleware is being moved to the new endpoint routing system.</span></span> <span data-ttu-id="c6d4e-111">L’ancienne méthode d’ajout d’un intergiciel (middleware) est obsolète.</span><span class="sxs-lookup"><span data-stu-id="c6d4e-111">The old way of adding middleware is being obsoleted.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c6d4e-112">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c6d4e-112">Recommended action</span></span>

<span data-ttu-id="c6d4e-113">Remplacez `UseSignalR` par `UseEndpoints` :</span><span class="sxs-lookup"><span data-stu-id="c6d4e-113">Replace `UseSignalR` with `UseEndpoints`:</span></span>

<span data-ttu-id="c6d4e-114">**Ancien code :**</span><span class="sxs-lookup"><span data-stu-id="c6d4e-114">**Old code:**</span></span>

```csharp
app.UseSignalR(routes =>
{
    routes.MapHub<SomeHub>("/path");
});
```

<span data-ttu-id="c6d4e-115">**Nouveau code :**</span><span class="sxs-lookup"><span data-stu-id="c6d4e-115">**New code:**</span></span>

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapHub<SomeHub>("/path");
});
```

#### <a name="category"></a><span data-ttu-id="c6d4e-116">Category</span><span class="sxs-lookup"><span data-stu-id="c6d4e-116">Category</span></span>

<span data-ttu-id="c6d4e-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c6d4e-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6d4e-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="c6d4e-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.SignalR.HubRouteBuilder?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:Microsoft.AspNetCore.Builder.ConnectionsAppBuilderExtensions.UseConnections(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder})`
- `M:Microsoft.AspNetCore.Builder.SignalRAppBuilderExtensions.UseSignalR(Microsoft.AspNetCore.Builder.IApplicationBuilder,System.Action{Microsoft.AspNetCore.SignalR.HubRouteBuilder})`
- `T:Microsoft.AspNetCore.Http.Connections.ConnectionsRouteBuilder`
- `T:Microsoft.AspNetCore.SignalR.HubRouteBuilder`

-->

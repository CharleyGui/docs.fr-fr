---
ms.openlocfilehash: 8979b7ffc09726c6588fe3ba60b916202697648f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522675"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="6b6dc-101">SignalR : Les constructeurs HubConnectionContext ont changé</span><span class="sxs-lookup"><span data-stu-id="6b6dc-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="6b6dc-102">Les constructeurs `HubConnectionContext` de SignalR ont changé pour accepter un type d’options, plutôt que plusieurs paramètres, pour ajouter des options à l’épreuve de l’avenir.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="6b6dc-103">Ce changement remplace deux constructeurs par un seul constructeur qui accepte un type d’options.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b6dc-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="6b6dc-104">Version introduced</span></span>

<span data-ttu-id="6b6dc-105">3.0</span><span class="sxs-lookup"><span data-stu-id="6b6dc-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6b6dc-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="6b6dc-106">Old behavior</span></span>

<span data-ttu-id="6b6dc-107">`HubConnectionContext`a deux constructeurs :</span><span class="sxs-lookup"><span data-stu-id="6b6dc-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="6b6dc-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="6b6dc-108">New behavior</span></span>

<span data-ttu-id="6b6dc-109">Les deux constructeurs ont été enlevés et remplacés par un constructeur :</span><span class="sxs-lookup"><span data-stu-id="6b6dc-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="6b6dc-110">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="6b6dc-110">Reason for change</span></span>

<span data-ttu-id="6b6dc-111">Le nouveau constructeur utilise un nouvel objet d’options.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="6b6dc-112">Par conséquent, les `HubConnectionContext` caractéristiques de peut être élargi à l’avenir sans faire plus de constructeurs et de briser les changements.</span><span class="sxs-lookup"><span data-stu-id="6b6dc-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b6dc-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="6b6dc-113">Recommended action</span></span>

<span data-ttu-id="6b6dc-114">Au lieu d’utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="6b6dc-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="6b6dc-115">Utilisez le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="6b6dc-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="6b6dc-116">Category</span><span class="sxs-lookup"><span data-stu-id="6b6dc-116">Category</span></span>

<span data-ttu-id="6b6dc-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6b6dc-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b6dc-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="6b6dc-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->

---
ms.openlocfilehash: 6be98e7ced6608ba0793c635adfe61c8b1a7e9d9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032659"
---
### <a name="signalr-hubconnectioncontext-constructors-changed"></a><span data-ttu-id="35db3-101">Signalr : les constructeurs HubConnectionContext ont été modifiés</span><span class="sxs-lookup"><span data-stu-id="35db3-101">SignalR: HubConnectionContext constructors changed</span></span>

<span data-ttu-id="35db3-102">Les constructeurs de signalr `HubConnectionContext` ont été modifiés pour accepter un type d’options, plutôt que plusieurs paramètres, pour les options d’ajout à la prochaine épreuve.</span><span class="sxs-lookup"><span data-stu-id="35db3-102">SignalR's `HubConnectionContext` constructors changed to accept an options type, rather than multiple parameters, to future-proof adding options.</span></span> <span data-ttu-id="35db3-103">Cette modification remplace deux constructeurs par un constructeur unique qui accepte un type d’options.</span><span class="sxs-lookup"><span data-stu-id="35db3-103">This change replaces two constructors with a single constructor that accepts an options type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="35db3-104">Version introduite</span><span class="sxs-lookup"><span data-stu-id="35db3-104">Version introduced</span></span>

<span data-ttu-id="35db3-105">3.0</span><span class="sxs-lookup"><span data-stu-id="35db3-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="35db3-106">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="35db3-106">Old behavior</span></span>

<span data-ttu-id="35db3-107">`HubConnectionContext` a deux constructeurs :</span><span class="sxs-lookup"><span data-stu-id="35db3-107">`HubConnectionContext` has two constructors:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory);
public HubConnectionContext(ConnectionContext connectionContext, TimeSpan keepAliveInterval, ILoggerFactory loggerFactory, TimeSpan clientTimeoutInterval);
```

#### <a name="new-behavior"></a><span data-ttu-id="35db3-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="35db3-108">New behavior</span></span>

<span data-ttu-id="35db3-109">Les deux constructeurs ont été supprimés et remplacés par un constructeur :</span><span class="sxs-lookup"><span data-stu-id="35db3-109">The two constructors were removed and replaced with one constructor:</span></span>

```csharp
public HubConnectionContext(ConnectionContext connectionContext, HubConnectionContextOptions contextOptions, ILoggerFactory loggerFactory)
```

#### <a name="reason-for-change"></a><span data-ttu-id="35db3-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="35db3-110">Reason for change</span></span>

<span data-ttu-id="35db3-111">Le nouveau constructeur utilise un nouvel objet d’options.</span><span class="sxs-lookup"><span data-stu-id="35db3-111">The new constructor uses a new options object.</span></span> <span data-ttu-id="35db3-112">Par conséquent, les fonctionnalités de `HubConnectionContext` peuvent être développées à l’avenir sans créer plus de constructeurs et de modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="35db3-112">Consequently, the features of `HubConnectionContext` can be expanded in the future without making more constructors and breaking changes.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="35db3-113">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="35db3-113">Recommended action</span></span>

<span data-ttu-id="35db3-114">Au lieu d’utiliser le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="35db3-114">Instead of using the following constructor:</span></span>

```csharp
HubConnectionContext connectionContext = new HubConnectionContext(
    connectionContext,
    keepAliveInterval: TimeSpan.FromSeconds(15),
    loggerFactory,
    clientTimeoutInterval: TimeSpan.FromSeconds(15));
```

<span data-ttu-id="35db3-115">Utilisez le constructeur suivant :</span><span class="sxs-lookup"><span data-stu-id="35db3-115">Use the following constructor:</span></span>

```csharp
HubConnectionContextOptions contextOptions = new HubConnectionContextOptions()
{
    KeepAliveInterval = TimeSpan.FromSeconds(15),
    ClientTimeoutInterval = TimeSpan.FromSeconds(15)
};
HubConnectionContext connectionContext = new HubConnectionContext(connectionContext, contextOptions, loggerFactory);
```

#### <a name="category"></a><span data-ttu-id="35db3-116">Category</span><span class="sxs-lookup"><span data-stu-id="35db3-116">Category</span></span>

<span data-ttu-id="35db3-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="35db3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="35db3-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="35db3-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)>
- <xref:Microsoft.AspNetCore.SignalR.HubConnectionContext.%23ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory)`
- `M:Microsoft.AspNetCore.SignalR.HubConnectionContext.#ctor(Microsoft.AspNetCore.Connections.ConnectionContext,System.TimeSpan,Microsoft.Extensions.Logging.ILoggerFactory,System.TimeSpan)`

-->

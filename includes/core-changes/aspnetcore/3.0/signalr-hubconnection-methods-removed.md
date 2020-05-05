---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901920"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="168e2-101">Signalr : les méthodes HubConnection ResetSendPing et ResetTimeout ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="168e2-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="168e2-102">Les `ResetSendPing` méthodes `ResetTimeout` et ont été supprimées de l' `HubConnection` API signalr.</span><span class="sxs-lookup"><span data-stu-id="168e2-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="168e2-103">Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="168e2-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="168e2-104">Ces méthodes ne seront pas disponibles à partir de la version ASP.NET Core 3,0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="168e2-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="168e2-105">Pour plus d’informations, consultez [dotnet/aspnetcore # 8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="168e2-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="168e2-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="168e2-106">Version introduced</span></span>

<span data-ttu-id="168e2-107">3.0</span><span class="sxs-lookup"><span data-stu-id="168e2-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="168e2-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="168e2-108">Old behavior</span></span>

<span data-ttu-id="168e2-109">Les API étaient disponibles.</span><span class="sxs-lookup"><span data-stu-id="168e2-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="168e2-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="168e2-110">New behavior</span></span>

<span data-ttu-id="168e2-111">Les API sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="168e2-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="168e2-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="168e2-112">Reason for change</span></span>

<span data-ttu-id="168e2-113">Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="168e2-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="168e2-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="168e2-114">Recommended action</span></span>

<span data-ttu-id="168e2-115">N’utilisez pas ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="168e2-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="168e2-116">Category</span><span class="sxs-lookup"><span data-stu-id="168e2-116">Category</span></span>

<span data-ttu-id="168e2-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="168e2-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="168e2-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="168e2-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

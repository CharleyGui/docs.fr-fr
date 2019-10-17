---
ms.openlocfilehash: a56c5fc32b5fd274d5da0d9b295918f5ea3b345e
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394199"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="63cba-101">Signalr : les méthodes HubConnection ResetSendPing et ResetTimeout ont été supprimées</span><span class="sxs-lookup"><span data-stu-id="63cba-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="63cba-102">Les méthodes `ResetSendPing` et `ResetTimeout` ont été supprimées de l’API Signalr `HubConnection`.</span><span class="sxs-lookup"><span data-stu-id="63cba-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="63cba-103">Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="63cba-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="63cba-104">Ces méthodes ne seront pas disponibles à partir de la version ASP.NET Core 3,0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="63cba-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="63cba-105">Pour plus d’informations, consultez [ASPNET/AspNetCore # 8543](https://github.com/aspnet/AspNetCore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="63cba-105">For discussion, see [aspnet/AspNetCore#8543](https://github.com/aspnet/AspNetCore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="63cba-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="63cba-106">Version introduced</span></span>

<span data-ttu-id="63cba-107">3,0</span><span class="sxs-lookup"><span data-stu-id="63cba-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="63cba-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="63cba-108">Old behavior</span></span>

<span data-ttu-id="63cba-109">Les API étaient disponibles.</span><span class="sxs-lookup"><span data-stu-id="63cba-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="63cba-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="63cba-110">New behavior</span></span>

<span data-ttu-id="63cba-111">Les API sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="63cba-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="63cba-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="63cba-112">Reason for change</span></span>

<span data-ttu-id="63cba-113">Ces méthodes étaient initialement destinées à un usage interne uniquement mais rendues publiques dans ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="63cba-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="63cba-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="63cba-114">Recommended action</span></span>

<span data-ttu-id="63cba-115">N’utilisez pas ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="63cba-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="63cba-116">Category</span><span class="sxs-lookup"><span data-stu-id="63cba-116">Category</span></span>

<span data-ttu-id="63cba-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="63cba-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63cba-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="63cba-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

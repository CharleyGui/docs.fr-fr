---
ms.openlocfilehash: de06825f1031d05bc83183a83bae165e2f9512ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901920"
---
### <a name="signalr-hubconnection-resetsendping-and-resettimeout-methods-removed"></a><span data-ttu-id="3f481-101">SignalR : Les méthodes HubConnection ResetSendPing et ResetTimeout supprimées</span><span class="sxs-lookup"><span data-stu-id="3f481-101">SignalR: HubConnection ResetSendPing and ResetTimeout methods removed</span></span>

<span data-ttu-id="3f481-102">Les `ResetSendPing` `ResetTimeout` méthodes et les méthodes `HubConnection` ont été retirées de l’API SignalR.</span><span class="sxs-lookup"><span data-stu-id="3f481-102">The `ResetSendPing` and `ResetTimeout` methods were removed from the SignalR `HubConnection` API.</span></span> <span data-ttu-id="3f481-103">À l’origine, ces méthodes n’étaient destinées qu’à des fins internes, mais elles ont été rendues publiques dans ASP.NET cœur 2.2.</span><span class="sxs-lookup"><span data-stu-id="3f481-103">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span> <span data-ttu-id="3f481-104">Ces méthodes ne seront pas disponibles à partir de la version ASP.NET Core 3.0 Preview 4.</span><span class="sxs-lookup"><span data-stu-id="3f481-104">These methods won't be available starting in the ASP.NET Core 3.0 Preview 4 release.</span></span> <span data-ttu-id="3f481-105">Pour discussion, voir [dotnet/aspnetcore 8543](https://github.com/dotnet/aspnetcore/issues/8543).</span><span class="sxs-lookup"><span data-stu-id="3f481-105">For discussion, see [dotnet/aspnetcore#8543](https://github.com/dotnet/aspnetcore/issues/8543).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f481-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3f481-106">Version introduced</span></span>

<span data-ttu-id="3f481-107">3.0</span><span class="sxs-lookup"><span data-stu-id="3f481-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3f481-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3f481-108">Old behavior</span></span>

<span data-ttu-id="3f481-109">Des API étaient disponibles.</span><span class="sxs-lookup"><span data-stu-id="3f481-109">APIs were available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3f481-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3f481-110">New behavior</span></span>

<span data-ttu-id="3f481-111">Les API sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="3f481-111">APIs are removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3f481-112">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="3f481-112">Reason for change</span></span>

<span data-ttu-id="3f481-113">À l’origine, ces méthodes n’étaient destinées qu’à des fins internes, mais elles ont été rendues publiques dans ASP.NET cœur 2.2.</span><span class="sxs-lookup"><span data-stu-id="3f481-113">These methods were originally intended only for internal use but were made public in ASP.NET Core 2.2.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f481-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3f481-114">Recommended action</span></span>

<span data-ttu-id="3f481-115">N’utilisez pas ces méthodes.</span><span class="sxs-lookup"><span data-stu-id="3f481-115">Don't use these methods.</span></span>

#### <a name="category"></a><span data-ttu-id="3f481-116">Category</span><span class="sxs-lookup"><span data-stu-id="3f481-116">Category</span></span>

<span data-ttu-id="3f481-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3f481-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f481-118">API affectées</span><span class="sxs-lookup"><span data-stu-id="3f481-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetSendPing`
- `M:Microsoft.AspNetCore.SignalR.Client.HubConnection.ResetTimeout`

-->

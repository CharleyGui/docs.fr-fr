---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="3a754-101">Kestrel : les abstractions de transport ont été supprimées et rendues publiques</span><span class="sxs-lookup"><span data-stu-id="3a754-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="3a754-102">Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu' `Microsoft.AspNetCore.Connections.Abstractions` interface publique dans la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="3a754-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3a754-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="3a754-103">Version introduced</span></span>

<span data-ttu-id="3a754-104">3.0</span><span class="sxs-lookup"><span data-stu-id="3a754-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="3a754-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="3a754-105">Old behavior</span></span>

- <span data-ttu-id="3a754-106">Des abstractions relatives au transport étaient disponibles dans `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="3a754-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="3a754-107">La `ListenOptions.NoDelay` propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="3a754-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="3a754-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="3a754-108">New behavior</span></span>

- <span data-ttu-id="3a754-109">L' `IConnectionListener` interface a été introduite `Microsoft.AspNetCore.Connections.Abstractions` dans la bibliothèque pour exposer la fonctionnalité la plus `...Transport.Abstractions` utilisée à partir de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="3a754-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="3a754-110">Le `NoDelay` est désormais disponible dans les options de`LibuvTransportOptions` transport `SocketTransportOptions`(et).</span><span class="sxs-lookup"><span data-stu-id="3a754-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="3a754-111">`SchedulingMode`n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="3a754-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3a754-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="3a754-112">Reason for change</span></span>

<span data-ttu-id="3a754-113">ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».</span><span class="sxs-lookup"><span data-stu-id="3a754-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3a754-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="3a754-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="3a754-115">Category</span><span class="sxs-lookup"><span data-stu-id="3a754-115">Category</span></span>

<span data-ttu-id="3a754-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3a754-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3a754-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="3a754-117">Affected APIs</span></span>

<span data-ttu-id="3a754-118">Aucun</span><span class="sxs-lookup"><span data-stu-id="3a754-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->

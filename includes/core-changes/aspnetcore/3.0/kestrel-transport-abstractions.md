---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="d77c7-101">Kestrel : les abstractions de transport ont été supprimées et rendues publiques</span><span class="sxs-lookup"><span data-stu-id="d77c7-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="d77c7-102">Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu’interface publique dans la bibliothèque `Microsoft.AspNetCore.Connections.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="d77c7-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d77c7-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d77c7-103">Version introduced</span></span>

<span data-ttu-id="d77c7-104">3,0</span><span class="sxs-lookup"><span data-stu-id="d77c7-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d77c7-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d77c7-105">Old behavior</span></span>

- <span data-ttu-id="d77c7-106">Les abstractions relatives au transport étaient disponibles dans la bibliothèque `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="d77c7-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="d77c7-107">La propriété `ListenOptions.NoDelay` était disponible.</span><span class="sxs-lookup"><span data-stu-id="d77c7-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d77c7-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d77c7-108">New behavior</span></span>

- <span data-ttu-id="d77c7-109">L’interface `IConnectionListener` a été introduite dans la bibliothèque `Microsoft.AspNetCore.Connections.Abstractions` pour exposer les fonctionnalités les plus utilisées à partir de la bibliothèque `...Transport.Abstractions`.</span><span class="sxs-lookup"><span data-stu-id="d77c7-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="d77c7-110">La `NoDelay` est désormais disponible dans options de transport (`LibuvTransportOptions` et `SocketTransportOptions`).</span><span class="sxs-lookup"><span data-stu-id="d77c7-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="d77c7-111">`SchedulingMode` n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="d77c7-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d77c7-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="d77c7-112">Reason for change</span></span>

<span data-ttu-id="d77c7-113">ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».</span><span class="sxs-lookup"><span data-stu-id="d77c7-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d77c7-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d77c7-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="d77c7-115">Category</span><span class="sxs-lookup"><span data-stu-id="d77c7-115">Category</span></span>

<span data-ttu-id="d77c7-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d77c7-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d77c7-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="d77c7-117">Affected APIs</span></span>

<span data-ttu-id="d77c7-118">aucune.</span><span class="sxs-lookup"><span data-stu-id="d77c7-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->

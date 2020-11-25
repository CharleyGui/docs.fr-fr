---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032584"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="f9c7d-101">Kestrel : les abstractions de transport ont été supprimées et rendues publiques</span><span class="sxs-lookup"><span data-stu-id="f9c7d-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="f9c7d-102">Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu’interface publique dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f9c7d-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f9c7d-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="f9c7d-103">Version introduced</span></span>

<span data-ttu-id="f9c7d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="f9c7d-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="f9c7d-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="f9c7d-105">Old behavior</span></span>

- <span data-ttu-id="f9c7d-106">Des abstractions relatives au transport étaient disponibles dans la `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f9c7d-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="f9c7d-107">La `ListenOptions.NoDelay` propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="f9c7d-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="f9c7d-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="f9c7d-108">New behavior</span></span>

- <span data-ttu-id="f9c7d-109">L' `IConnectionListener` interface a été introduite dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque pour exposer la fonctionnalité la plus utilisée à partir de la `...Transport.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="f9c7d-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="f9c7d-110">Le `NoDelay` est désormais disponible dans les options de transport ( `LibuvTransportOptions` et `SocketTransportOptions` ).</span><span class="sxs-lookup"><span data-stu-id="f9c7d-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="f9c7d-111">`SchedulingMode` n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="f9c7d-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="f9c7d-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="f9c7d-112">Reason for change</span></span>

<span data-ttu-id="f9c7d-113">ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».</span><span class="sxs-lookup"><span data-stu-id="f9c7d-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f9c7d-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="f9c7d-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="f9c7d-115">Category</span><span class="sxs-lookup"><span data-stu-id="f9c7d-115">Category</span></span>

<span data-ttu-id="f9c7d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9c7d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f9c7d-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="f9c7d-117">Affected APIs</span></span>

<span data-ttu-id="f9c7d-118">None</span><span class="sxs-lookup"><span data-stu-id="f9c7d-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

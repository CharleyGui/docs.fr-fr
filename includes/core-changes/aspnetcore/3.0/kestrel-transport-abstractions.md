---
ms.openlocfilehash: fb23418816abcae125106c93b339a546aa9bc2ee
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721022"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="a8618-101">Kestrel : les abstractions de transport ont été supprimées et rendues publiques</span><span class="sxs-lookup"><span data-stu-id="a8618-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="a8618-102">Dans le cadre du déplacement des API « pubternal », les API de la couche de transport Kestrel sont exposées en tant qu’interface publique dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a8618-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a8618-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a8618-103">Version introduced</span></span>

<span data-ttu-id="a8618-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a8618-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a8618-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a8618-105">Old behavior</span></span>

- <span data-ttu-id="a8618-106">Des abstractions relatives au transport étaient disponibles dans la `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a8618-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="a8618-107">La `ListenOptions.NoDelay` propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="a8618-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a8618-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a8618-108">New behavior</span></span>

- <span data-ttu-id="a8618-109">L' `IConnectionListener` interface a été introduite dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque pour exposer la fonctionnalité la plus utilisée à partir de la `...Transport.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="a8618-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="a8618-110">Le `NoDelay` est désormais disponible dans les options de transport ( `LibuvTransportOptions` et `SocketTransportOptions` ).</span><span class="sxs-lookup"><span data-stu-id="a8618-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="a8618-111">`SchedulingMode`n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="a8618-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a8618-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a8618-112">Reason for change</span></span>

<span data-ttu-id="a8618-113">ASP.NET Core 3,0 a été déplacée hors des API « pubternal ».</span><span class="sxs-lookup"><span data-stu-id="a8618-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a8618-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a8618-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="a8618-115">Category</span><span class="sxs-lookup"><span data-stu-id="a8618-115">Category</span></span>

<span data-ttu-id="a8618-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a8618-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8618-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="a8618-117">Affected APIs</span></span>

<span data-ttu-id="a8618-118">Aucune</span><span class="sxs-lookup"><span data-stu-id="a8618-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

---
ms.openlocfilehash: f95c3916f4da8164cf927344f60f2845f04ddc5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394166"
---
### <a name="kestrel-transport-abstractions-removed-and-made-public"></a><span data-ttu-id="fc91e-101">Kestrel: Les abstractions de transport supprimées et rendues publiques</span><span class="sxs-lookup"><span data-stu-id="fc91e-101">Kestrel: Transport abstractions removed and made public</span></span>

<span data-ttu-id="fc91e-102">Dans le cadre de l’éloignement des API « pubtérinaires », les API de la couche de transport de Kestrel sont exposées comme une interface publique dans la `Microsoft.AspNetCore.Connections.Abstractions` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="fc91e-102">As part of moving away from "pubternal" APIs, the Kestrel transport layer APIs are exposed as a public interface in the `Microsoft.AspNetCore.Connections.Abstractions` library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fc91e-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="fc91e-103">Version introduced</span></span>

<span data-ttu-id="fc91e-104">3.0</span><span class="sxs-lookup"><span data-stu-id="fc91e-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fc91e-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="fc91e-105">Old behavior</span></span>

- <span data-ttu-id="fc91e-106">Des abstractions liées aux `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` transports étaient disponibles dans la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="fc91e-106">Transport-related abstractions were available in the `Microsoft.AspNetCore.Server.Kestrel.Transport.Abstractions` library.</span></span>
- <span data-ttu-id="fc91e-107">La `ListenOptions.NoDelay` propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="fc91e-107">The `ListenOptions.NoDelay` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fc91e-108">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="fc91e-108">New behavior</span></span>

- <span data-ttu-id="fc91e-109">L’interface `IConnectionListener` a `Microsoft.AspNetCore.Connections.Abstractions` été introduite dans la bibliothèque `...Transport.Abstractions` pour exposer les fonctionnalités les plus utilisées de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="fc91e-109">The `IConnectionListener` interface was introduced in the `Microsoft.AspNetCore.Connections.Abstractions` library to expose the most used functionality from the `...Transport.Abstractions` library.</span></span>
- <span data-ttu-id="fc91e-110">Le `NoDelay` est maintenant disponible`LibuvTransportOptions` dans `SocketTransportOptions`les options de transport ( et ).</span><span class="sxs-lookup"><span data-stu-id="fc91e-110">The `NoDelay` is now available in transport options (`LibuvTransportOptions` and `SocketTransportOptions`).</span></span>
- <span data-ttu-id="fc91e-111">`SchedulingMode`n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="fc91e-111">`SchedulingMode` is no longer available.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fc91e-112">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="fc91e-112">Reason for change</span></span>

<span data-ttu-id="fc91e-113">ASP.NET Core 3.0 s’est éloigné des API " pubtérinaux »."</span><span class="sxs-lookup"><span data-stu-id="fc91e-113">ASP.NET Core 3.0 has moved away from "pubternal" APIs.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fc91e-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="fc91e-114">Recommended action</span></span>

#### <a name="category"></a><span data-ttu-id="fc91e-115">Category</span><span class="sxs-lookup"><span data-stu-id="fc91e-115">Category</span></span>

<span data-ttu-id="fc91e-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fc91e-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fc91e-117">API affectées</span><span class="sxs-lookup"><span data-stu-id="fc91e-117">Affected APIs</span></span>

<span data-ttu-id="fc91e-118">None</span><span class="sxs-lookup"><span data-stu-id="fc91e-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->

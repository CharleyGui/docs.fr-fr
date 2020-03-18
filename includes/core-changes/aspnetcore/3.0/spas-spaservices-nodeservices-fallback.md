---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522656"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="23ef2-101">SPAs: SpaServices et NodeServices ne retomberent plus à l’enregistreur de console</span><span class="sxs-lookup"><span data-stu-id="23ef2-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="23ef2-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType>et <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> n’affichera pas les journaux de console à moins que la connexion ne soit configurée.</span><span class="sxs-lookup"><span data-stu-id="23ef2-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="23ef2-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="23ef2-103">Version introduced</span></span>

<span data-ttu-id="23ef2-104">3.0</span><span class="sxs-lookup"><span data-stu-id="23ef2-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="23ef2-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="23ef2-105">Old behavior</span></span>

<span data-ttu-id="23ef2-106">`Microsoft.AspNetCore.SpaServices`et `Microsoft.AspNetCore.NodeServices` utilisé pour créer automatiquement un enregistreur de console lors de la connexion n’est pas configuré.</span><span class="sxs-lookup"><span data-stu-id="23ef2-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="23ef2-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="23ef2-107">New behavior</span></span>

<span data-ttu-id="23ef2-108">`Microsoft.AspNetCore.SpaServices`et `Microsoft.AspNetCore.NodeServices` n’affichera pas les journaux de console à moins que la connexion ne soit configurée.</span><span class="sxs-lookup"><span data-stu-id="23ef2-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="23ef2-109">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="23ef2-109">Reason for change</span></span>

<span data-ttu-id="23ef2-110">Il est nécessaire de s’aligner sur la façon dont d’autres paquets ASP.NET Core implémentent l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="23ef2-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="23ef2-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="23ef2-111">Recommended action</span></span>

<span data-ttu-id="23ef2-112">Si l’ancien comportement est nécessaire, pour `services.AddLogging(builder => builder.AddConsole())` configurer l’enregistrement de console, ajouter à votre `Setup.ConfigureServices` méthode.</span><span class="sxs-lookup"><span data-stu-id="23ef2-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="23ef2-113">Category</span><span class="sxs-lookup"><span data-stu-id="23ef2-113">Category</span></span>

<span data-ttu-id="23ef2-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="23ef2-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="23ef2-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="23ef2-115">Affected APIs</span></span>

<span data-ttu-id="23ef2-116">None</span><span class="sxs-lookup"><span data-stu-id="23ef2-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

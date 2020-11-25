---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032683"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a><span data-ttu-id="c01c3-101">SPAs : SpaServices et NodeServices ne sont plus renvoyés à l’enregistreur de console</span><span class="sxs-lookup"><span data-stu-id="c01c3-101">SPAs: SpaServices and NodeServices no longer fall back to console logger</span></span>

<span data-ttu-id="c01c3-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> et <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> n’affichent pas les journaux de la console, sauf si la journalisation est configurée.</span><span class="sxs-lookup"><span data-stu-id="c01c3-102"><xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> and <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> won't display console logs unless logging is configured.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c01c3-103">Version introduite</span><span class="sxs-lookup"><span data-stu-id="c01c3-103">Version introduced</span></span>

<span data-ttu-id="c01c3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="c01c3-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c01c3-105">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="c01c3-105">Old behavior</span></span>

<span data-ttu-id="c01c3-106">`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` permettent de créer automatiquement un journal de console lorsque la journalisation n’est pas configurée.</span><span class="sxs-lookup"><span data-stu-id="c01c3-106">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` used to automatically create a console logger when logging isn't configured.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c01c3-107">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="c01c3-107">New behavior</span></span>

<span data-ttu-id="c01c3-108">`Microsoft.AspNetCore.SpaServices` et `Microsoft.AspNetCore.NodeServices` n’affichent pas les journaux de la console, sauf si la journalisation est configurée.</span><span class="sxs-lookup"><span data-stu-id="c01c3-108">`Microsoft.AspNetCore.SpaServices` and `Microsoft.AspNetCore.NodeServices` won't display console logs unless logging is configured.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c01c3-109">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="c01c3-109">Reason for change</span></span>

<span data-ttu-id="c01c3-110">Il est nécessaire de s’aligner sur la manière dont les autres packages d’ASP.NET Core implémentent la journalisation.</span><span class="sxs-lookup"><span data-stu-id="c01c3-110">There's a need to align with how other ASP.NET Core packages implement logging.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c01c3-111">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="c01c3-111">Recommended action</span></span>

<span data-ttu-id="c01c3-112">Si l’ancien comportement est requis, pour configurer la journalisation de la console, ajoutez `services.AddLogging(builder => builder.AddConsole())` à votre `Setup.ConfigureServices` méthode.</span><span class="sxs-lookup"><span data-stu-id="c01c3-112">If the old behavior is required, to configure console logging, add `services.AddLogging(builder => builder.AddConsole())` to your `Setup.ConfigureServices` method.</span></span>

#### <a name="category"></a><span data-ttu-id="c01c3-113">Category</span><span class="sxs-lookup"><span data-stu-id="c01c3-113">Category</span></span>

<span data-ttu-id="c01c3-114">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c01c3-114">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c01c3-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="c01c3-115">Affected APIs</span></span>

<span data-ttu-id="c01c3-116">None</span><span class="sxs-lookup"><span data-stu-id="c01c3-116">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

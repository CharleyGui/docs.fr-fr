---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901588"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="d3fc5-101">SignalR: Le nom du forfait client JavaScript modifié</span><span class="sxs-lookup"><span data-stu-id="d3fc5-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="d3fc5-102">Dans ASP.NET Core 3.0 Preview 7, le nom du `@aspnet/signalr` client `@microsoft/signalr`SignalR JavaScript est passé de .</span><span class="sxs-lookup"><span data-stu-id="d3fc5-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="d3fc5-103">Le changement de nom reflète le fait que SignalR est utile dans plus de ASP.NET applications Core, grâce au service SignalR Azure.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="d3fc5-104">Pour réagir à ce changement, modifiez les `require` références dans *vos* fichiers, relevés et instructions ECMAScript. `import`</span><span class="sxs-lookup"><span data-stu-id="d3fc5-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="d3fc5-105">Aucune API ne changera dans le cadre de ce changement.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="d3fc5-106">Pour discussion, voir [dotnet/aspnetcore 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="d3fc5-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d3fc5-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="d3fc5-107">Version introduced</span></span>

<span data-ttu-id="d3fc5-108">3.0</span><span class="sxs-lookup"><span data-stu-id="d3fc5-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d3fc5-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="d3fc5-109">Old behavior</span></span>

<span data-ttu-id="d3fc5-110">Le paquet client `@aspnet/signalr`a été nommé .</span><span class="sxs-lookup"><span data-stu-id="d3fc5-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d3fc5-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="d3fc5-111">New behavior</span></span>

<span data-ttu-id="d3fc5-112">Le forfait client `@microsoft/signalr`est nommé .</span><span class="sxs-lookup"><span data-stu-id="d3fc5-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d3fc5-113">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="d3fc5-113">Reason for change</span></span>

<span data-ttu-id="d3fc5-114">Le changement de nom précise que SignalR est utile au-delà de ASP.NET applications Core, grâce au service SignalR Azure.</span><span class="sxs-lookup"><span data-stu-id="d3fc5-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d3fc5-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="d3fc5-115">Recommended action</span></span>

<span data-ttu-id="d3fc5-116">Passez au nouveau `@microsoft/signalr`paquet .</span><span class="sxs-lookup"><span data-stu-id="d3fc5-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="d3fc5-117">Category</span><span class="sxs-lookup"><span data-stu-id="d3fc5-117">Category</span></span>

<span data-ttu-id="d3fc5-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d3fc5-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d3fc5-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="d3fc5-119">Affected APIs</span></span>

<span data-ttu-id="d3fc5-120">None</span><span class="sxs-lookup"><span data-stu-id="d3fc5-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

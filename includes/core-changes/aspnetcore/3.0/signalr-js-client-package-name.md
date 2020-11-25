---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032667"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="e11d7-101">Signalr : nom du package client JavaScript modifié</span><span class="sxs-lookup"><span data-stu-id="e11d7-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="e11d7-102">Dans ASP.NET Core 3,0 Preview 7, le nom du package client JavaScript Signalr est passé de `@aspnet/signalr` à `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="e11d7-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="e11d7-103">Le changement de nom reflète le fait que Signalr est utile dans les applications plus que simplement ASP.NET Core, grâce au service Azure Signalr.</span><span class="sxs-lookup"><span data-stu-id="e11d7-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="e11d7-104">Pour réagir à cette modification, modifiez les références dans votre *package.jssur* les fichiers, les `require` instructions et les `import` instructions ECMAScript.</span><span class="sxs-lookup"><span data-stu-id="e11d7-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="e11d7-105">Aucune API ne changera dans le cadre de ce changement de nom.</span><span class="sxs-lookup"><span data-stu-id="e11d7-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="e11d7-106">Pour plus d’informations, consultez [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).</span><span class="sxs-lookup"><span data-stu-id="e11d7-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e11d7-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="e11d7-107">Version introduced</span></span>

<span data-ttu-id="e11d7-108">3.0</span><span class="sxs-lookup"><span data-stu-id="e11d7-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e11d7-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="e11d7-109">Old behavior</span></span>

<span data-ttu-id="e11d7-110">Le package client a été nommé `@aspnet/signalr` .</span><span class="sxs-lookup"><span data-stu-id="e11d7-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e11d7-111">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="e11d7-111">New behavior</span></span>

<span data-ttu-id="e11d7-112">Le package client est nommé `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="e11d7-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e11d7-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="e11d7-113">Reason for change</span></span>

<span data-ttu-id="e11d7-114">Le changement de nom clarifie que Signalr est utile au-delà de ASP.NET Core applications, grâce au service Azure Signalr.</span><span class="sxs-lookup"><span data-stu-id="e11d7-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e11d7-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="e11d7-115">Recommended action</span></span>

<span data-ttu-id="e11d7-116">Basculez vers le nouveau package `@microsoft/signalr` .</span><span class="sxs-lookup"><span data-stu-id="e11d7-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="e11d7-117">Category</span><span class="sxs-lookup"><span data-stu-id="e11d7-117">Category</span></span>

<span data-ttu-id="e11d7-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e11d7-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e11d7-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="e11d7-119">Affected APIs</span></span>

<span data-ttu-id="e11d7-120">None</span><span class="sxs-lookup"><span data-stu-id="e11d7-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->

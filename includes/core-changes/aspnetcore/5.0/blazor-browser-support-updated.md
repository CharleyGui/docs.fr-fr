---
ms.openlocfilehash: 584014572ab799e1e3ab2f02c9fbf4fe6b0c17e7
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804922"
---
### <a name="blazor-updated-browser-support"></a><span data-ttu-id="9c268-101">Éblouissant : prise en charge mise à jour du navigateur</span><span class="sxs-lookup"><span data-stu-id="9c268-101">Blazor: Updated browser support</span></span>

<span data-ttu-id="9c268-102">ASP.NET Core 5,0 introduit de [nouvelles fonctionnalités éblouissantes](https://github.com/dotnet/aspnetcore/issues/21514), dont certaines ne sont pas compatibles avec les navigateurs plus anciens.</span><span class="sxs-lookup"><span data-stu-id="9c268-102">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="9c268-103">La liste des navigateurs pris en charge par éblouissant dans ASP.NET Core 5,0 a été mise à jour en conséquence.</span><span class="sxs-lookup"><span data-stu-id="9c268-103">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="9c268-104">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="9c268-104">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9c268-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9c268-105">Version introduced</span></span>

<span data-ttu-id="9c268-106">5.0</span><span class="sxs-lookup"><span data-stu-id="9c268-106">5.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="9c268-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="9c268-107">Old behavior</span></span>

<span data-ttu-id="9c268-108">Le serveur éblouissant prend en charge Microsoft Internet Explorer 11 avec des polyremplissages suffisants.</span><span class="sxs-lookup"><span data-stu-id="9c268-108">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="9c268-109">Le serveur éblouissant et le webassembly éblouissant sont également fonctionnels dans l' [héritage Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span><span class="sxs-lookup"><span data-stu-id="9c268-109">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="9c268-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="9c268-110">New behavior</span></span>

<span data-ttu-id="9c268-111">Le serveur éblouissant dans ASP.NET Core 5,0 n’est pas pris en charge avec Microsoft Internet Explorer 11.</span><span class="sxs-lookup"><span data-stu-id="9c268-111">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="9c268-112">Le serveur éblouissant et l’webassembly éblouissant ne sont pas entièrement fonctionnels dans l’héritage Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="9c268-112">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="9c268-113">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="9c268-113">Reason for change</span></span>

<span data-ttu-id="9c268-114">Les nouvelles fonctionnalités éblouissantes de ASP.NET Core 5,0 ne sont pas compatibles avec ces anciens navigateurs, et l’utilisation de ces anciens navigateurs diminue.</span><span class="sxs-lookup"><span data-stu-id="9c268-114">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="9c268-115">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="9c268-115">For more information, see the following resources:</span></span>

* [<span data-ttu-id="9c268-116">Le support Windows pour l’héritage Microsoft Edge se termine également le 9 mars 2021</span><span class="sxs-lookup"><span data-stu-id="9c268-116">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="9c268-117">Les applications et services Microsoft 365 prendront en charge Microsoft Internet Explorer 11 le 17 août 2021</span><span class="sxs-lookup"><span data-stu-id="9c268-117">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

#### <a name="recommended-action"></a><span data-ttu-id="9c268-118">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9c268-118">Recommended action</span></span>

<span data-ttu-id="9c268-119">Effectuez une mise à niveau à partir de ces anciens navigateurs vers le [nouveau Microsoft Edge basé sur le chrome](https://www.microsoft.com/edge).</span><span class="sxs-lookup"><span data-stu-id="9c268-119">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="9c268-120">Pour les applications éblouissantes qui doivent prendre en charge ces anciens navigateurs, utilisez ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9c268-120">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="9c268-121">La liste des navigateurs pris en charge pour éblouissant dans ASP.NET Core 3,1 n’a pas changé et est documentée sur les [plateformes prises en charge](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="9c268-121">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

#### <a name="category"></a><span data-ttu-id="9c268-122">Category</span><span class="sxs-lookup"><span data-stu-id="9c268-122">Category</span></span>

<span data-ttu-id="9c268-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="9c268-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9c268-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="9c268-124">Affected APIs</span></span>

<span data-ttu-id="9c268-125">None</span><span class="sxs-lookup"><span data-stu-id="9c268-125">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->

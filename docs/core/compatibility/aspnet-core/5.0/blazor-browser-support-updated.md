---
title: 'Modification avec rupture : éblouissant : prise en charge mise à jour du navigateur'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée éblouissant : prise en charge du navigateur mise à jour'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 63b35aa8cb73bfb82c565007704375bac3737299
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761225"
---
# <a name="blazor-updated-browser-support"></a><span data-ttu-id="7d698-103">Éblouissant : prise en charge mise à jour du navigateur</span><span class="sxs-lookup"><span data-stu-id="7d698-103">Blazor: Updated browser support</span></span>

<span data-ttu-id="7d698-104">ASP.NET Core 5,0 introduit de [nouvelles fonctionnalités éblouissantes](https://github.com/dotnet/aspnetcore/issues/21514), dont certaines ne sont pas compatibles avec les navigateurs plus anciens.</span><span class="sxs-lookup"><span data-stu-id="7d698-104">ASP.NET Core 5.0 introduces [new Blazor features](https://github.com/dotnet/aspnetcore/issues/21514), some of which are incompatible with older browsers.</span></span> <span data-ttu-id="7d698-105">La liste des navigateurs pris en charge par éblouissant dans ASP.NET Core 5,0 a été mise à jour en conséquence.</span><span class="sxs-lookup"><span data-stu-id="7d698-105">The list of browsers supported by Blazor in ASP.NET Core 5.0 has been updated accordingly.</span></span>

<span data-ttu-id="7d698-106">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 26475](https://github.com/dotnet/aspnetcore/issues/26475).</span><span class="sxs-lookup"><span data-stu-id="7d698-106">For discussion, see GitHub issue [dotnet/aspnetcore#26475](https://github.com/dotnet/aspnetcore/issues/26475).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="7d698-107">Version introduite</span><span class="sxs-lookup"><span data-stu-id="7d698-107">Version introduced</span></span>

<span data-ttu-id="7d698-108">5.0</span><span class="sxs-lookup"><span data-stu-id="7d698-108">5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="7d698-109">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="7d698-109">Old behavior</span></span>

<span data-ttu-id="7d698-110">Le serveur éblouissant prend en charge Microsoft Internet Explorer 11 avec des polyremplissages suffisants.</span><span class="sxs-lookup"><span data-stu-id="7d698-110">Blazor Server supports Microsoft Internet Explorer 11 with sufficient polyfills.</span></span> <span data-ttu-id="7d698-111">Le serveur éblouissant et le webassembly éblouissant sont également fonctionnels dans l' [héritage Microsoft Edge](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span><span class="sxs-lookup"><span data-stu-id="7d698-111">Blazor Server and Blazor WebAssembly are also functional in [Microsoft Edge Legacy](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy).</span></span>

## <a name="new-behavior"></a><span data-ttu-id="7d698-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="7d698-112">New behavior</span></span>

<span data-ttu-id="7d698-113">Le serveur éblouissant dans ASP.NET Core 5,0 n’est pas pris en charge avec Microsoft Internet Explorer 11.</span><span class="sxs-lookup"><span data-stu-id="7d698-113">Blazor Server in ASP.NET Core 5.0 isn't supported with Microsoft Internet Explorer 11.</span></span> <span data-ttu-id="7d698-114">Le serveur éblouissant et l’webassembly éblouissant ne sont pas entièrement fonctionnels dans l’héritage Microsoft Edge.</span><span class="sxs-lookup"><span data-stu-id="7d698-114">Blazor Server and Blazor WebAssembly aren't fully functional in Microsoft Edge Legacy.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="7d698-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="7d698-115">Reason for change</span></span>

<span data-ttu-id="7d698-116">Les nouvelles fonctionnalités éblouissantes de ASP.NET Core 5,0 ne sont pas compatibles avec ces anciens navigateurs, et l’utilisation de ces anciens navigateurs diminue.</span><span class="sxs-lookup"><span data-stu-id="7d698-116">New Blazor features in ASP.NET Core 5.0 are incompatible with these older browsers, and use of these older browsers is diminishing.</span></span> <span data-ttu-id="7d698-117">Pour plus d’informations, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="7d698-117">For more information, see the following resources:</span></span>

* [<span data-ttu-id="7d698-118">Le support Windows pour l’héritage Microsoft Edge se termine également le 9 mars 2021</span><span class="sxs-lookup"><span data-stu-id="7d698-118">Windows support for Microsoft Edge Legacy is also ending on March 9, 2021</span></span>](https://support.microsoft.com/help/4533505/what-is-microsoft-edge-legacy)
* [<span data-ttu-id="7d698-119">Les applications et services Microsoft 365 prendront en charge Microsoft Internet Explorer 11 le 17 août 2021</span><span class="sxs-lookup"><span data-stu-id="7d698-119">Microsoft 365 apps and services will end support for Microsoft Internet Explorer 11 by August 17, 2021</span></span>](/lifecycle/announcements/m365-ie11-microsoft-edge-legacy)

## <a name="recommended-action"></a><span data-ttu-id="7d698-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="7d698-120">Recommended action</span></span>

<span data-ttu-id="7d698-121">Effectuez une mise à niveau à partir de ces anciens navigateurs vers le [nouveau Microsoft Edge basé sur le chrome](https://www.microsoft.com/edge).</span><span class="sxs-lookup"><span data-stu-id="7d698-121">Upgrade from these older browsers to the [new, Chromium-based Microsoft Edge](https://www.microsoft.com/edge).</span></span> <span data-ttu-id="7d698-122">Pour les applications éblouissantes qui doivent prendre en charge ces anciens navigateurs, utilisez ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7d698-122">For Blazor apps that need to support these older browsers, use ASP.NET Core 3.1.</span></span> <span data-ttu-id="7d698-123">La liste des navigateurs pris en charge pour éblouissant dans ASP.NET Core 3,1 n’a pas changé et est documentée sur les [plateformes prises en charge](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span><span class="sxs-lookup"><span data-stu-id="7d698-123">The supported browsers list for Blazor in ASP.NET Core 3.1 hasn't changed and is documented at [Supported platforms](/aspnet/core/blazor/supported-platforms?view=aspnetcore-3.1).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="7d698-124">API affectées</span><span class="sxs-lookup"><span data-stu-id="7d698-124">Affected APIs</span></span>

<span data-ttu-id="7d698-125">None</span><span class="sxs-lookup"><span data-stu-id="7d698-125">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

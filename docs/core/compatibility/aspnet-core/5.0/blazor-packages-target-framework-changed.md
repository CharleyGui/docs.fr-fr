---
title: 'Modification avec rupture : éblouissant : version cible du .NET Framework des packages NuGet modifiée'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée éblouissant : version cible du .NET Framework des packages NuGet modifiée'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 5515edc66ff9786f0d8f7e24e5fc28c71502567b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760968"
---
# <a name="blazor-target-framework-of-nuget-packages-changed"></a><span data-ttu-id="27809-103">Éblouissante : version cible du .NET Framework des packages NuGet modifiée</span><span class="sxs-lookup"><span data-stu-id="27809-103">Blazor: Target framework of NuGet packages changed</span></span>

<span data-ttu-id="27809-104">Les projets de webassembly éblouissants 3,2 ont été compilés pour cibler .NET Standard 2,1 ( `<TargetFramework>netstandard2.1</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="27809-104">Blazor 3.2 WebAssembly projects were compiled to target .NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`).</span></span> <span data-ttu-id="27809-105">Dans ASP.NET Core 5,0, les projets de serveur éblouissant et de webassembly éblouissant ciblent .NET 5,0 ( `<TargetFramework>net5.0</TargetFramework>` ).</span><span class="sxs-lookup"><span data-stu-id="27809-105">In ASP.NET Core 5.0, both Blazor Server and Blazor WebAssembly projects target .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`).</span></span> <span data-ttu-id="27809-106">Pour mieux s’aligner sur la modification de la version cible de .NET Framework, les packages éblouissants suivants ne ciblent plus .NET Standard 2,1 :</span><span class="sxs-lookup"><span data-stu-id="27809-106">To better align with the target framework change, the following Blazor packages no longer target .NET Standard 2.1:</span></span>

* [<span data-ttu-id="27809-107">Microsoft. AspNetCore. Components</span><span class="sxs-lookup"><span data-stu-id="27809-107">Microsoft.AspNetCore.Components</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [<span data-ttu-id="27809-108">Microsoft. AspNetCore. Components. Authorization</span><span class="sxs-lookup"><span data-stu-id="27809-108">Microsoft.AspNetCore.Components.Authorization</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [<span data-ttu-id="27809-109">Microsoft. AspNetCore. Components. Forms</span><span class="sxs-lookup"><span data-stu-id="27809-109">Microsoft.AspNetCore.Components.Forms</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [<span data-ttu-id="27809-110">Microsoft. AspNetCore. Components. Web</span><span class="sxs-lookup"><span data-stu-id="27809-110">Microsoft.AspNetCore.Components.Web</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [<span data-ttu-id="27809-111">Microsoft. AspNetCore. Components. webassembly</span><span class="sxs-lookup"><span data-stu-id="27809-111">Microsoft.AspNetCore.Components.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [<span data-ttu-id="27809-112">Microsoft. AspNetCore. Components. webassembly. Authentication</span><span class="sxs-lookup"><span data-stu-id="27809-112">Microsoft.AspNetCore.Components.WebAssembly.Authentication</span></span>](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [<span data-ttu-id="27809-113">Microsoft.JSInterop</span><span class="sxs-lookup"><span data-stu-id="27809-113">Microsoft.JSInterop</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop)
* [<span data-ttu-id="27809-114">Microsoft.JSInterop. webassembly</span><span class="sxs-lookup"><span data-stu-id="27809-114">Microsoft.JSInterop.WebAssembly</span></span>](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [<span data-ttu-id="27809-115">Microsoft. Authentication. webassembly. MSAL</span><span class="sxs-lookup"><span data-stu-id="27809-115">Microsoft.Authentication.WebAssembly.Msal</span></span>](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

<span data-ttu-id="27809-116">Pour plus d’informations, consultez GitHub issue [dotnet/aspnetcore # 23424](https://github.com/dotnet/aspnetcore/issues/23424).</span><span class="sxs-lookup"><span data-stu-id="27809-116">For discussion, see GitHub issue [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="27809-117">Version introduite</span><span class="sxs-lookup"><span data-stu-id="27809-117">Version introduced</span></span>

<span data-ttu-id="27809-118">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="27809-118">5.0 Preview 7</span></span>

## <a name="old-behavior"></a><span data-ttu-id="27809-119">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="27809-119">Old behavior</span></span>

<span data-ttu-id="27809-120">Dans éblouissant 3,1 et 3,2, les packages ciblent .NET Standard 2,1 et .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="27809-120">In Blazor 3.1 and 3.2, packages target .NET Standard 2.1 and .NET Core 3.1.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="27809-121">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="27809-121">New behavior</span></span>

<span data-ttu-id="27809-122">Dans ASP.NET Core 5,0, les packages ciblent .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="27809-122">In ASP.NET Core 5.0, packages target .NET 5.0.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="27809-123">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="27809-123">Reason for change</span></span>

<span data-ttu-id="27809-124">La modification a été apportée pour mieux s’adapter aux exigences de .NET Target Framework.</span><span class="sxs-lookup"><span data-stu-id="27809-124">The change was made to better align with .NET target framework requirements.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="27809-125">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="27809-125">Recommended action</span></span>

<span data-ttu-id="27809-126">Les projets de webassembly éblouissants 3,2 doivent cibler .NET 5,0 dans le cadre de la mise à jour de leurs références de package à 5. x.x.</span><span class="sxs-lookup"><span data-stu-id="27809-126">Blazor 3.2 WebAssembly projects should target .NET 5.0 as part of updating their package references to 5.x.x.</span></span> <span data-ttu-id="27809-127">Les bibliothèques qui font référence à l’un de ces packages peuvent cibler .NET 5,0 ou plusieurs cibles en fonction de leurs besoins.</span><span class="sxs-lookup"><span data-stu-id="27809-127">Libraries that reference one of these packages can either target .NET 5.0 or multi-target depending on their requirements.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="27809-128">API affectées</span><span class="sxs-lookup"><span data-stu-id="27809-128">Affected APIs</span></span>

<span data-ttu-id="27809-129">None</span><span class="sxs-lookup"><span data-stu-id="27809-129">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->
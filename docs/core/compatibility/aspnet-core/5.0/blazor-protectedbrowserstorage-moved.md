---
title: 'Modification avec rupture : éblouissant : fonctionnalité ProtectedBrowserStorage déplacée vers l’infrastructure partagée'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée « éblouissant » : fonctionnalité ProtectedBrowserStorage déplacée vers le Framework partagé'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c8058adf8b66aef8dd011ea672cd306ae4de60a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760967"
---
# <a name="blazor-protectedbrowserstorage-feature-moved-to-shared-framework"></a><span data-ttu-id="79a25-103">Éblouissant : fonctionnalité ProtectedBrowserStorage déplacée vers le Framework partagé</span><span class="sxs-lookup"><span data-stu-id="79a25-103">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>

<span data-ttu-id="79a25-104">Dans le cadre de la version ASP.NET Core 5,0 RC2, la `ProtectedBrowserStorage` fonctionnalité a été déplacée vers le ASP.net Core Framework partagé.</span><span class="sxs-lookup"><span data-stu-id="79a25-104">As part of the ASP.NET Core 5.0 RC2 release, the `ProtectedBrowserStorage` feature moved to the ASP.NET Core shared framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="79a25-105">Version introduite</span><span class="sxs-lookup"><span data-stu-id="79a25-105">Version introduced</span></span>

<span data-ttu-id="79a25-106">5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="79a25-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="79a25-107">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="79a25-107">Old behavior</span></span>

<span data-ttu-id="79a25-108">Dans ASP.NET Core 5,0 Preview 8, la fonctionnalité est disponible en tant que partie du package [Microsoft. AspNetCore. Components. Web. extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) , mais n’est utilisable que dans le webassembly éblouissant.</span><span class="sxs-lookup"><span data-stu-id="79a25-108">In ASP.NET Core 5.0 Preview 8, the feature is available as a part of the [Microsoft.AspNetCore.Components.Web.Extensions](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web.Extensions) package but was only usable in Blazor WebAssembly.</span></span>

<span data-ttu-id="79a25-109">Dans ASP.NET Core RC1 5,0, la fonctionnalité est disponible dans le package [Microsoft. AspNetCore. Components. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) , qui fait référence à l' `Microsoft.AspNetCore.App` infrastructure partagée.</span><span class="sxs-lookup"><span data-stu-id="79a25-109">In ASP.NET Core 5.0 RC1, the feature is available as part of the [Microsoft.AspNetCore.Components.ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.ProtectedBrowserStorage) package, which references the `Microsoft.AspNetCore.App` shared framework.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="79a25-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="79a25-110">New behavior</span></span>

<span data-ttu-id="79a25-111">Dans ASP.NET Core RC2 5,0, une référence de package NuGet n’est plus nécessaire pour référencer et utiliser la fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="79a25-111">In ASP.NET Core 5.0 RC2, a NuGet package reference is no longer needed to reference and use the feature.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="79a25-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="79a25-112">Reason for change</span></span>

<span data-ttu-id="79a25-113">Le passage à l’infrastructure partagée est mieux adapté à l’expérience utilisateur que les clients attendent.</span><span class="sxs-lookup"><span data-stu-id="79a25-113">The move to the shared framework is a better fit for the user experience customers expect.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="79a25-114">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="79a25-114">Recommended action</span></span>

<span data-ttu-id="79a25-115">Si vous effectuez une mise à niveau à partir de ASP.NET Core 5,0 RC1, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="79a25-115">If upgrading from ASP.NET Core 5.0 RC1, complete the following steps:</span></span>

1. <span data-ttu-id="79a25-116">Supprimez la `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` référence de package du projet.</span><span class="sxs-lookup"><span data-stu-id="79a25-116">Remove the `Microsoft.AspNetCore.Components.ProtectedBrowserStorage` package reference from the project.</span></span>
1. <span data-ttu-id="79a25-117">Remplacez `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` par `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="79a25-117">Replace `using Microsoft.AspNetCore.Components.ProtectedBrowserStorage;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="79a25-118">Supprimez l’appel à `AddProtectedBrowserStorage` de votre `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="79a25-118">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

<span data-ttu-id="79a25-119">Si vous effectuez une mise à niveau à partir de ASP.NET Core 5,0 Preview 8, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="79a25-119">If upgrading from ASP.NET Core 5.0 Preview 8, complete the following steps:</span></span>

1. <span data-ttu-id="79a25-120">Supprimez la `Microsoft.AspNetCore.Components.Web.Extensions` référence de package du projet.</span><span class="sxs-lookup"><span data-stu-id="79a25-120">Remove the `Microsoft.AspNetCore.Components.Web.Extensions` package reference from the project.</span></span>
1. <span data-ttu-id="79a25-121">Remplacez `using Microsoft.AspNetCore.Components.Web.Extensions;` par `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span><span class="sxs-lookup"><span data-stu-id="79a25-121">Replace `using Microsoft.AspNetCore.Components.Web.Extensions;` with `using Microsoft.AspNetCore.Components.Server.ProtectedBrowserStorage;`.</span></span>
1. <span data-ttu-id="79a25-122">Supprimez l’appel à `AddProtectedBrowserStorage` de votre `Startup` classe.</span><span class="sxs-lookup"><span data-stu-id="79a25-122">Remove the call to `AddProtectedBrowserStorage` from your `Startup` class.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="79a25-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="79a25-123">Affected APIs</span></span>

<span data-ttu-id="79a25-124">None</span><span class="sxs-lookup"><span data-stu-id="79a25-124">None</span></span>

<!--

### Category

ASP.NET Core

### Affected APIs

Not detectable via API analysis

-->

---
title: 'Modification avec rupture : HTTP : Kestrel et types de BadHttpRequestException IIS marqués comme obsolètes et remplacés'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulée HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c51b1dd9d708c04bc1bbcfb65ea2e9daea5330b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760960"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a><span data-ttu-id="9cf4e-103">HTTP : Kestrel et les types de BadHttpRequestException IIS marqués comme obsolètes et remplacés</span><span class="sxs-lookup"><span data-stu-id="9cf4e-103">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>

<span data-ttu-id="9cf4e-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` ont été marqués comme obsolètes et ont été modifiés pour dériver de `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="9cf4e-104">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` have been marked obsolete and changed to derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span> <span data-ttu-id="9cf4e-105">Les serveurs Kestrel et IIS lèvent toujours leurs anciens types d’exception à des fins de compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-105">The Kestrel and IIS servers still throw their old exception types for backwards compatibility.</span></span> <span data-ttu-id="9cf4e-106">Les types obsolètes seront supprimés dans une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-106">The obsolete types will be removed in a future release.</span></span>

<span data-ttu-id="9cf4e-107">Pour plus d’informations, consultez [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).</span><span class="sxs-lookup"><span data-stu-id="9cf4e-107">For discussion, see [dotnet/aspnetcore#20614](https://github.com/dotnet/aspnetcore/issues/20614).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="9cf4e-108">Version introduite</span><span class="sxs-lookup"><span data-stu-id="9cf4e-108">Version introduced</span></span>

<span data-ttu-id="9cf4e-109">5,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="9cf4e-109">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="9cf4e-110">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="9cf4e-110">Old behavior</span></span>

<span data-ttu-id="9cf4e-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` dérivées de <xref:System.IO.IOException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="9cf4e-111">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derived from <xref:System.IO.IOException?displayProperty=nameWithType>.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="9cf4e-112">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="9cf4e-112">New behavior</span></span>

<span data-ttu-id="9cf4e-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` sont obsolètes.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-113">`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` are obsolete.</span></span> <span data-ttu-id="9cf4e-114">Les types dérivent également de `Microsoft.AspNetCore.Http.BadHttpRequestException` , qui dérive de `System.IO.IOException` .</span><span class="sxs-lookup"><span data-stu-id="9cf4e-114">The types also derive from `Microsoft.AspNetCore.Http.BadHttpRequestException`, which derives from `System.IO.IOException`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="9cf4e-115">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="9cf4e-115">Reason for change</span></span>

<span data-ttu-id="9cf4e-116">La modification a été apportée à :</span><span class="sxs-lookup"><span data-stu-id="9cf4e-116">The change was made to:</span></span>

* <span data-ttu-id="9cf4e-117">Consolidez les types dupliqués.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-117">Consolidate duplicate types.</span></span>
* <span data-ttu-id="9cf4e-118">Unifiez le comportement entre les implémentations de serveur.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-118">Unify behavior across server implementations.</span></span>

<span data-ttu-id="9cf4e-119">Une application peut maintenant intercepter l’exception de base `Microsoft.AspNetCore.Http.BadHttpRequestException` lors de l’utilisation de Kestrel ou IIS.</span><span class="sxs-lookup"><span data-stu-id="9cf4e-119">An app can now catch the base exception `Microsoft.AspNetCore.Http.BadHttpRequestException` when using either Kestrel or IIS.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="9cf4e-120">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="9cf4e-120">Recommended action</span></span>

<span data-ttu-id="9cf4e-121">Remplacer les utilisations de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` et de `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` par `Microsoft.AspNetCore.Http.BadHttpRequestException` .</span><span class="sxs-lookup"><span data-stu-id="9cf4e-121">Replace usages of `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` and `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` with `Microsoft.AspNetCore.Http.BadHttpRequestException`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="9cf4e-122">API affectées</span><span class="sxs-lookup"><span data-stu-id="9cf4e-122">Affected APIs</span></span>

- [<span data-ttu-id="9cf4e-123">Microsoft. AspNetCore. Server. IIS. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="9cf4e-123">Microsoft.AspNetCore.Server.IIS.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [<span data-ttu-id="9cf4e-124">Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException</span><span class="sxs-lookup"><span data-stu-id="9cf4e-124">Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->

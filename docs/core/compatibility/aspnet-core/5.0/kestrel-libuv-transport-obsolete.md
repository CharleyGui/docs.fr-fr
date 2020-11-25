---
title: 'Modification avec rupture : Kestrel : transport Libuv marqué comme obsolète'
description: 'En savoir plus sur la modification avec rupture dans ASP.NET Core 5,0 intitulé Kestrel : Libuv transport marqué comme obsolète'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: f66b9b646671e07957e6d30a95333d392eb29617
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761010"
---
# <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="93c23-103">Kestrel : transport Libuv marqué comme obsolète</span><span class="sxs-lookup"><span data-stu-id="93c23-103">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="93c23-104">Les versions antérieures de ASP.NET Core utilisé Libuv comme un détail d’implémentation de la façon dont les entrées et sorties asynchrones ont été effectuées.</span><span class="sxs-lookup"><span data-stu-id="93c23-104">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="93c23-105">Dans ASP.NET Core 2,0, un transport alternatif <xref:System.Net.Sockets.Socket> a été développé.</span><span class="sxs-lookup"><span data-stu-id="93c23-105">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="93c23-106">Dans ASP.NET Core 2,1, Kestrel est passé à l’utilisation du `Socket` transport basé sur-based par défaut.</span><span class="sxs-lookup"><span data-stu-id="93c23-106">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="93c23-107">La prise en charge de Libuv a été maintenue pour des raisons de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="93c23-107">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="93c23-108">À ce stade, l’utilisation du `Socket` transport basé sur est bien plus courante que le transport Libuv.</span><span class="sxs-lookup"><span data-stu-id="93c23-108">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="93c23-109">Par conséquent, la prise en charge de Libuv est marquée comme obsolète dans .NET 5,0 et sera entièrement supprimée dans .NET 6,0.</span><span class="sxs-lookup"><span data-stu-id="93c23-109">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="93c23-110">Dans le cadre de cette modification, la prise en charge Libuv pour les nouvelles plateformes de système d’exploitation (par exemple, Windows ARM64) ne sera pas ajoutée dans le délai de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="93c23-110">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="93c23-111">Pour plus d’informations sur les problèmes de blocage qui nécessitent l’utilisation du transport Libuv, consultez le problème GitHub à l’adresse [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409).</span><span class="sxs-lookup"><span data-stu-id="93c23-111">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="93c23-112">Version introduite</span><span class="sxs-lookup"><span data-stu-id="93c23-112">Version introduced</span></span>

<span data-ttu-id="93c23-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="93c23-113">5.0 Preview 8</span></span>

## <a name="old-behavior"></a><span data-ttu-id="93c23-114">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="93c23-114">Old behavior</span></span>

<span data-ttu-id="93c23-115">Les API Libuv ne sont pas marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="93c23-115">The Libuv APIs aren't marked as obsolete.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="93c23-116">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="93c23-116">New behavior</span></span>

<span data-ttu-id="93c23-117">Les API Libuv sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="93c23-117">The Libuv APIs are marked as obsolete.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="93c23-118">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="93c23-118">Reason for change</span></span>

<span data-ttu-id="93c23-119">La `Socket` valeur par défaut est le transport basé sur.</span><span class="sxs-lookup"><span data-stu-id="93c23-119">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="93c23-120">Il n’existe aucune raison impérieuse de continuer à utiliser le transport Libuv.</span><span class="sxs-lookup"><span data-stu-id="93c23-120">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="93c23-121">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="93c23-121">Recommended action</span></span>

<span data-ttu-id="93c23-122">Cesser d’utiliser le [package Libuv](https://www.nuget.org/packages/Libuv) et les méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="93c23-122">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="93c23-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="93c23-123">Affected APIs</span></span>

- [<span data-ttu-id="93c23-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="93c23-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-125">WebHostBuilderLibuvExtensions.UseLibuv</span><span class="sxs-lookup"><span data-stu-id="93c23-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-126">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="93c23-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-127">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="93c23-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-128">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. NoDelay</span><span class="sxs-lookup"><span data-stu-id="93c23-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-129">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="93c23-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="93c23-130">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="93c23-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->

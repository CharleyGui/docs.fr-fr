---
ms.openlocfilehash: 203d75f5858c8ff039cf579c0539efda0c5c9f02
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474374"
---
### <a name="kestrel-libuv-transport-marked-as-obsolete"></a><span data-ttu-id="a642f-101">Kestrel : transport Libuv marqué comme obsolète</span><span class="sxs-lookup"><span data-stu-id="a642f-101">Kestrel: Libuv transport marked as obsolete</span></span>

<span data-ttu-id="a642f-102">Les versions antérieures de ASP.NET Core utilisé Libuv comme un détail d’implémentation de la façon dont les entrées et sorties asynchrones ont été effectuées.</span><span class="sxs-lookup"><span data-stu-id="a642f-102">Earlier versions of ASP.NET Core used Libuv as an implementation detail of how asynchronous input and output was performed.</span></span> <span data-ttu-id="a642f-103">Dans ASP.NET Core 2,0, un transport alternatif <xref:System.Net.Sockets.Socket> a été développé.</span><span class="sxs-lookup"><span data-stu-id="a642f-103">In ASP.NET Core 2.0, an alternative, <xref:System.Net.Sockets.Socket>-based transport was developed.</span></span> <span data-ttu-id="a642f-104">Dans ASP.NET Core 2,1, Kestrel est passé à l’utilisation du `Socket` transport basé sur-based par défaut.</span><span class="sxs-lookup"><span data-stu-id="a642f-104">In ASP.NET Core 2.1, Kestrel switched to using the `Socket`-based transport by default.</span></span> <span data-ttu-id="a642f-105">La prise en charge de Libuv a été maintenue pour des raisons de compatibilité.</span><span class="sxs-lookup"><span data-stu-id="a642f-105">Libuv support was maintained for compatibility reasons.</span></span>

<span data-ttu-id="a642f-106">À ce stade, l’utilisation du `Socket` transport basé sur est bien plus courante que le transport Libuv.</span><span class="sxs-lookup"><span data-stu-id="a642f-106">At this point, use of the `Socket`-based transport is far more common than the Libuv transport.</span></span> <span data-ttu-id="a642f-107">Par conséquent, la prise en charge de Libuv est marquée comme obsolète dans .NET 5,0 et sera entièrement supprimée dans .NET 6,0.</span><span class="sxs-lookup"><span data-stu-id="a642f-107">Consequently, Libuv support is marked as obsolete in .NET 5.0 and will be removed entirely in .NET 6.0.</span></span>

<span data-ttu-id="a642f-108">Dans le cadre de cette modification, la prise en charge Libuv pour les nouvelles plateformes de système d’exploitation (par exemple, Windows ARM64) ne sera pas ajoutée dans le délai de .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="a642f-108">As part of this change, Libuv support for new operating system platforms (like Windows ARM64) won't be added in the .NET 5.0 timeframe.</span></span>

<span data-ttu-id="a642f-109">Pour plus d’informations sur les problèmes de blocage qui nécessitent l’utilisation du transport Libuv, consultez le problème GitHub à l’adresse [dotnet/aspnetcore # 23409](https://github.com/dotnet/aspnetcore/issues/23409).</span><span class="sxs-lookup"><span data-stu-id="a642f-109">For discussion on blocking issues that require the use of the Libuv transport, see the GitHub issue at [dotnet/aspnetcore#23409](https://github.com/dotnet/aspnetcore/issues/23409).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a642f-110">Version introduite</span><span class="sxs-lookup"><span data-stu-id="a642f-110">Version introduced</span></span>

<span data-ttu-id="a642f-111">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="a642f-111">5.0 Preview 8</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a642f-112">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="a642f-112">Old behavior</span></span>

<span data-ttu-id="a642f-113">Les API Libuv ne sont pas marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="a642f-113">The Libuv APIs aren't marked as obsolete.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a642f-114">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="a642f-114">New behavior</span></span>

<span data-ttu-id="a642f-115">Les API Libuv sont marquées comme obsolètes.</span><span class="sxs-lookup"><span data-stu-id="a642f-115">The Libuv APIs are marked as obsolete.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a642f-116">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="a642f-116">Reason for change</span></span>

<span data-ttu-id="a642f-117">La `Socket` valeur par défaut est le transport basé sur.</span><span class="sxs-lookup"><span data-stu-id="a642f-117">The `Socket`-based transport is the default.</span></span> <span data-ttu-id="a642f-118">Il n’existe aucune raison impérieuse de continuer à utiliser le transport Libuv.</span><span class="sxs-lookup"><span data-stu-id="a642f-118">There aren't any compelling reasons to continue using the Libuv transport.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a642f-119">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="a642f-119">Recommended action</span></span>

<span data-ttu-id="a642f-120">Cesser d’utiliser le [package Libuv](https://www.nuget.org/packages/Libuv) et les méthodes d’extension.</span><span class="sxs-lookup"><span data-stu-id="a642f-120">Discontinue use of the [Libuv package](https://www.nuget.org/packages/Libuv) and extension methods.</span></span>

#### <a name="category"></a><span data-ttu-id="a642f-121">Category</span><span class="sxs-lookup"><span data-stu-id="a642f-121">Category</span></span>

<span data-ttu-id="a642f-122">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a642f-122">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a642f-123">API affectées</span><span class="sxs-lookup"><span data-stu-id="a642f-123">Affected APIs</span></span>

- [<span data-ttu-id="a642f-124">WebHostBuilderLibuvExtensions</span><span class="sxs-lookup"><span data-stu-id="a642f-124">WebHostBuilderLibuvExtensions</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-125">WebHostBuilderLibuvExtensions.UseLibuv</span><span class="sxs-lookup"><span data-stu-id="a642f-125">WebHostBuilderLibuvExtensions.UseLibuv</span></span>](/dotnet/api/microsoft.aspnetcore.hosting.webhostbuilderlibuvextensions.uselibuv?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-126">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions</span><span class="sxs-lookup"><span data-stu-id="a642f-126">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-127">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. ThreadCount</span><span class="sxs-lookup"><span data-stu-id="a642f-127">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.threadcount?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-128">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. NoDelay</span><span class="sxs-lookup"><span data-stu-id="a642f-128">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.nodelay?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-129">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxWriteBufferSize</span><span class="sxs-lookup"><span data-stu-id="a642f-129">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxwritebuffersize?view=aspnetcore-3.0)
- [<span data-ttu-id="a642f-130">Microsoft. AspNetCore. Server. Kestrel. transport. Libuv. LibuvTransportOptions. MaxReadBufferSize</span><span class="sxs-lookup"><span data-stu-id="a642f-130">Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize</span></span>](/dotnet/api/microsoft.aspnetcore.server.kestrel.transport.libuv.libuvtransportoptions.maxreadbuffersize?view=aspnetcore-3.0)
- `Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions`
- `Overload:Microsoft.AspNetCore.Hosting.WebHostBuilderLibuvExtensions.UseLibuv`
- `T:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.ThreadCount`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.NoDelay`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxWriteBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.MaxReadBufferSize`
- `P:Microsoft.AspNetCore.Server.Kestrel.Transport.Libuv.LibuvTransportOptions.Backlog`

-->

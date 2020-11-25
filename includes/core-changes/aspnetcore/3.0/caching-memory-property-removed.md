---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032474"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="189c5-101">Caching : propriété CompactOnMemoryPressure supprimée</span><span class="sxs-lookup"><span data-stu-id="189c5-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="189c5-102">La version 3,0 de ASP.NET Core a supprimé les [API obsolètes de MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="189c5-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="189c5-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="189c5-103">Change description</span></span>

<span data-ttu-id="189c5-104">Cette modification est un suivi de [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="189c5-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="189c5-105">Pour plus d’informations, consultez [dotnet/extensions # 1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="189c5-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="189c5-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="189c5-106">Version introduced</span></span>

<span data-ttu-id="189c5-107">3.0</span><span class="sxs-lookup"><span data-stu-id="189c5-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="189c5-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="189c5-108">Old behavior</span></span>

<span data-ttu-id="189c5-109">`MemoryCacheOptions.CompactOnMemoryPressure` la propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="189c5-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="189c5-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="189c5-110">New behavior</span></span>

<span data-ttu-id="189c5-111">La `MemoryCacheOptions.CompactOnMemoryPressure` propriété a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="189c5-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="189c5-112">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="189c5-112">Reason for change</span></span>

<span data-ttu-id="189c5-113">Le compactage automatique du cache a provoqué des problèmes.</span><span class="sxs-lookup"><span data-stu-id="189c5-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="189c5-114">Pour éviter un comportement inattendu, le cache ne doit être compacté que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="189c5-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="189c5-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="189c5-115">Recommended action</span></span>

<span data-ttu-id="189c5-116">Pour compacter le cache, les casts aval `MemoryCache` et appellent quand cela est `Compact` nécessaire.</span><span class="sxs-lookup"><span data-stu-id="189c5-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="189c5-117">Category</span><span class="sxs-lookup"><span data-stu-id="189c5-117">Category</span></span>

<span data-ttu-id="189c5-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="189c5-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="189c5-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="189c5-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->

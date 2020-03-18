---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901633"
---
### <a name="caching-compactonmemorypressure-property-removed"></a><span data-ttu-id="29929-101">Caching: CompactOnMemoryPressure propriété supprimée</span><span class="sxs-lookup"><span data-stu-id="29929-101">Caching: CompactOnMemoryPressure property removed</span></span>

<span data-ttu-id="29929-102">La version ASP.NET Core 3.0 a supprimé les [API obsolètes MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span><span class="sxs-lookup"><span data-stu-id="29929-102">The ASP.NET Core 3.0 release removed the [obsolete MemoryCacheOptions APIs](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).</span></span>

#### <a name="change-description"></a><span data-ttu-id="29929-103">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="29929-103">Change description</span></span>

<span data-ttu-id="29929-104">Ce changement fait suite à [aspnet/Caching 221](https://github.com/aspnet/Caching/issues/221).</span><span class="sxs-lookup"><span data-stu-id="29929-104">This change is a follow-up to [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221).</span></span> <span data-ttu-id="29929-105">Pour discussion, voir [dotnet/extensions 1062](https://github.com/dotnet/extensions/issues/1062).</span><span class="sxs-lookup"><span data-stu-id="29929-105">For discussion, see [dotnet/extensions#1062](https://github.com/dotnet/extensions/issues/1062).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29929-106">Version introduite</span><span class="sxs-lookup"><span data-stu-id="29929-106">Version introduced</span></span>

<span data-ttu-id="29929-107">3.0</span><span class="sxs-lookup"><span data-stu-id="29929-107">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="29929-108">Ancien comportement</span><span class="sxs-lookup"><span data-stu-id="29929-108">Old behavior</span></span>

<span data-ttu-id="29929-109">`MemoryCacheOptions.CompactOnMemoryPressure`propriété était disponible.</span><span class="sxs-lookup"><span data-stu-id="29929-109">`MemoryCacheOptions.CompactOnMemoryPressure` property was available.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="29929-110">Nouveau comportement</span><span class="sxs-lookup"><span data-stu-id="29929-110">New behavior</span></span>

<span data-ttu-id="29929-111">La `MemoryCacheOptions.CompactOnMemoryPressure` propriété a été enlevée.</span><span class="sxs-lookup"><span data-stu-id="29929-111">The `MemoryCacheOptions.CompactOnMemoryPressure` property has been removed.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="29929-112">Raison du changement</span><span class="sxs-lookup"><span data-stu-id="29929-112">Reason for change</span></span>

<span data-ttu-id="29929-113">Le compactage automatique du cache a causé des problèmes.</span><span class="sxs-lookup"><span data-stu-id="29929-113">Automatically compacting the cache caused problems.</span></span> <span data-ttu-id="29929-114">Pour éviter un comportement inattendu, le cache ne doit être compacté que si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="29929-114">To avoid unexpected behavior, the cache should only be compacted when needed.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29929-115">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="29929-115">Recommended action</span></span>

<span data-ttu-id="29929-116">Pour compacter le cache, downcast et `MemoryCache` appeler `Compact` en cas de besoin.</span><span class="sxs-lookup"><span data-stu-id="29929-116">To compact the cache, downcast to `MemoryCache` and call `Compact` when needed.</span></span>

#### <a name="category"></a><span data-ttu-id="29929-117">Category</span><span class="sxs-lookup"><span data-stu-id="29929-117">Category</span></span>

<span data-ttu-id="29929-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29929-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29929-119">API affectées</span><span class="sxs-lookup"><span data-stu-id="29929-119">Affected APIs</span></span>

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->

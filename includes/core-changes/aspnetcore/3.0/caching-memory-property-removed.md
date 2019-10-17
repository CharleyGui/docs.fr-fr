---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394274"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Caching : propriété CompactOnMemoryPressure supprimée

La version 3,0 de ASP.NET Core a supprimé les [API obsolètes de MemoryCacheOptions](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Modifier la description

Cette modification est un suivi de [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221). Pour plus d’informations, consultez [ASPNET/extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).

#### <a name="version-introduced"></a>Version introduite

3,0

#### <a name="old-behavior"></a>Ancien comportement

la propriété `MemoryCacheOptions.CompactOnMemoryPressure` était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

La propriété `MemoryCacheOptions.CompactOnMemoryPressure` a été supprimée.

#### <a name="reason-for-change"></a>Motif de modification

Le compactage automatique du cache a provoqué des problèmes. Pour éviter un comportement inattendu, le cache ne doit être compacté que si nécessaire.

#### <a name="recommended-action"></a>Action recommandée

Pour compacter le cache, vous devez effectuer un cast aval sur `MemoryCache` et appeler `Compact` en cas de besoin.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->

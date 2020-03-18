---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901633"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Caching: CompactOnMemoryPressure propriété supprimée

La version ASP.NET Core 3.0 a supprimé les [API obsolètes MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Description de la modification

Ce changement fait suite à [aspnet/Caching 221](https://github.com/aspnet/Caching/issues/221). Pour discussion, voir [dotnet/extensions 1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

`MemoryCacheOptions.CompactOnMemoryPressure`propriété était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

La `MemoryCacheOptions.CompactOnMemoryPressure` propriété a été enlevée.

#### <a name="reason-for-change"></a>Raison du changement

Le compactage automatique du cache a causé des problèmes. Pour éviter un comportement inattendu, le cache ne doit être compacté que si nécessaire.

#### <a name="recommended-action"></a>Action recommandée

Pour compacter le cache, downcast et `MemoryCache` appeler `Compact` en cas de besoin.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->

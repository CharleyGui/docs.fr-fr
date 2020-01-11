---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901633"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Caching : propriété CompactOnMemoryPressure supprimée

La version 3,0 de ASP.NET Core a supprimé les [API obsolètes de MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Description des modifications

Cette modification est un suivi de [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221). Pour plus d’informations, consultez [dotnet/extensions # 1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Version introduite

3.0

#### <a name="old-behavior"></a>Ancien comportement

la propriété `MemoryCacheOptions.CompactOnMemoryPressure` était disponible.

#### <a name="new-behavior"></a>Nouveau comportement

La propriété `MemoryCacheOptions.CompactOnMemoryPressure` a été supprimée.

#### <a name="reason-for-change"></a>Motif de modification

Le compactage automatique du cache a provoqué des problèmes. Pour éviter un comportement inattendu, le cache ne doit être compacté que si nécessaire.

#### <a name="recommended-action"></a>Action recommandée

Pour compacter le cache, vous devez effectuer un cast aval pour `MemoryCache` et appeler `Compact` quand cela est nécessaire.

#### <a name="category"></a>Catégorie

ASP.NET Core

#### <a name="affected-apis"></a>API affectées

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->

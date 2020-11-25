---
title: 'Modification avec rupture : modification du comportement pour Vector2. Lerp et Vector4. Lerp'
description: En savoir plus sur le changement critique .NET 5,0 dans les bibliothèques .NET de base où l’implémentation de Vector2. Lerp et Vector4. Lerp a été modifiée pour prendre en compte correctement une erreur d’arrondi à virgule flottante.
ms.date: 11/01/2020
ms.openlocfilehash: 8e363a559dba8b7563c40637c47f101d59951216
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760899"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Changement de comportement pour Vector2. Lerp et Vector4. Lerp

L’implémentation de <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> a changé pour tenir compte d’une erreur d’arrondi à virgule flottante.

## <a name="change-description"></a>Description de la modification

Précédemment, <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> et <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> étaient implémentées en tant que `value1 + (value2 - value1) * amount` . Toutefois, en raison d’une erreur d’arrondi à virgule flottante, cet algorithme ne retourne pas toujours `value2` lorsque `amount` est `1.0f` .

Dans .NET 5,0 et versions ultérieures, l’implémentation utilise le même algorithme que <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> , qui est `(value1 * (1.0f - amount)) + (value2 * amount)` . Cet algorithme gère correctement l’erreur d’arrondi. Désormais, lorsque `amount` a `1.0f` la valeur, le résultat est exact `value2` . L’algorithme mis à jour permet également à l’algorithme d’être optimisé librement à l’aide <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> de lorsqu’il est disponible.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

Aucune action n'est nécessaire. Toutefois, si vous souhaitez conserver l’ancien comportement, vous pouvez implémenter votre propre `Lerp` fonction qui utilise l’algorithme précédent de `value1 + (value2 - value1) * amount` .

## <a name="affected-apis"></a>API affectées

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->

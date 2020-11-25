---
title: 'Modification avec rupture : le vecteur <T> lève une exception NotSupportedException'
description: Découvrez la modification avec rupture .NET 5,0 dans les bibliothèques .NET de base où Vector <T> lève toujours une exception pour les paramètres de type non pris en charge.
ms.date: 11/01/2020
ms.openlocfilehash: 63db7c6b720735b180ed11098227b31a14008f74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761004"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vector \<T> lève toujours l’exception NotSupportedException pour les types non pris en charge

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> lève à présent toujours un <xref:System.NotSupportedException> pour les paramètres de type non pris en charge.

## <a name="change-description"></a>Description de la modification

Auparavant, les membres de <xref:System.Numerics.Vector%601> ne lèvent pas toujours une exception <xref:System.NotSupportedException> quand `T` était un [type non pris en charge](#unsupported-types). L’exception n’a pas toujours été levée en raison des chemins de code qui ont pris en charge l’accélération matérielle. Par exemple, `Vector<bool> + Vector<bool>` retourné `default` au lieu de lever une exception sur les plateformes qui n’ont pas d’accélération matérielle, telles que ARM32. Pour les types non pris en charge, <xref:System.Numerics.Vector%601> les membres présentent un comportement incohérent sur différentes plateformes et configurations matérielles.

À compter de .NET 5,0, <xref:System.Numerics.Vector%601> les membres lèvent toujours une <xref:System.NotSupportedException> sur toutes les configurations matérielles lorsque `T` n’est pas un type pris en charge.

### <a name="unsupported-types"></a>Types non pris en charge

Les types pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> sont :

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Les types pris en charge n’ont pas changé, toutefois, ils peuvent changer à l’avenir.

## <a name="version-introduced"></a>Version introduite

5.0

## <a name="recommended-action"></a>Action recommandée

N’utilisez pas un type non pris en charge pour le paramètre de type de <xref:System.Numerics.Vector%601> .

## <a name="affected-apis"></a>API affectées

- <xref:System.Numerics.Vector%601?displayProperty=fullName> et tous ses membres

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->

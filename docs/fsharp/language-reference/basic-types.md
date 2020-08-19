---
title: Types de base
description: 'Découvrez les principaux types de base utilisés dans le langage F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 659ac8424c62985affcca1741e1b2a74c9c3ee8d
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557696"
---
# <a name="basic-types"></a>Types de base

Cette rubrique répertorie les types de base définis en langage F #. Ces types sont les plus fondamentaux en F #, formant la base de presque tous les programmes F #. Il s’agit d’un sur-ensemble de types primitifs .NET.

|Type|Type .NET|Description|Exemple|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|Les valeurs possibles sont `true` et `false`.|`true`/`false`|
|`byte`|<xref:System.Byte>|Valeurs comprises entre 0 et 255.|`1uy`|
|`sbyte`|<xref:System.SByte>|Valeurs comprises entre-128 et 127.|`1y`|
|`int16`|<xref:System.Int16>|Valeurs comprises entre-32768 et 32767.|`1s`|
|`uint16`|<xref:System.UInt16>|Valeurs comprises entre 0 et 65535.|`1us`|
|`int`|<xref:System.Int32>|Valeurs comprises entre-2 147 483 648 et 2 147 483 647.|`1`|
|`uint`|<xref:System.UInt32>|Valeurs comprises entre 0 et 4 294 967 295.|`1u`|
|`int64`|<xref:System.Int64>|Valeurs comprises entre-9223372036854775808 et 9 223 372 036 854 775 807.|`1L`|
|`uint64`|<xref:System.UInt64>|Valeurs comprises entre 0 et 18446744073709551615.|`1UL`|
|`nativeint`|<xref:System.IntPtr>|Pointeur natif en tant qu’entier signé.|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|Pointeur natif sous la forme d’un entier non signé.|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|Type de données à virgule flottante qui contient au moins 28 chiffres significatifs.|`1.0`|
|`float`, `double`|<xref:System.Double>|Type à virgule flottante 64 bits.|`1.0`|
|`float32`, `single`|<xref:System.Single>|Type à virgule flottante 32 bits.|`1.0f`|
|`char`|<xref:System.Char>|Valeurs de caractères Unicode.|`'c'`|
|`string`|<xref:System.String>|Texte Unicode.|`"str"`|
|`unit`|Non applicable|Indique l’absence d’une valeur réelle. Le type a une seule valeur formelle, ce qui est indiqué `()` . La valeur d’unité, `()` , est souvent utilisée comme un espace réservé dans lequel une valeur est nécessaire, mais aucune valeur réelle n’est disponible ou logique.|`()`|

> [!NOTE]
> Vous pouvez effectuer des calculs avec des entiers trop grands pour le type d’entier 64 bits à l’aide du type [bigint](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-bigint.html) . `bigint` n’est pas considéré comme un type de base ; Il s’agit d’une abréviation pour `System.Numerics.BigInteger` .

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)

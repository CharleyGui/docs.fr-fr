---
title: Types non managés - Référence C#
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512076"
---
# <a name="unmanaged-types-c-reference"></a>Types non managés (référence C#)

Un **type non managé** est un type qui n’est ni un type référence ni un type construit (type comprenant au moins un argument de type) et qui ne contient pas de champs de type référence ou de type construit, quel que soit le niveau d’imbrication. En d’autres termes, un type non managé est l’un des suivants :

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Tout type [enum](../keywords/enum.md)
- Tout type [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Tout type [struct](../keywords/struct.md) défini par l’utilisateur n’étant pas un type construit et contenant des champs de types non managés uniquement

À compter de C# 7.3, vous pouvez utiliser la [`unmanaged`contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé « non-pointer ».

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
- [Opérateur sizeof](../operators/sizeof.md)
- [Opérateur stackalloc](../operators/stackalloc.md)

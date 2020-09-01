---
description: 'En savoir plus sur les types non managés dans C #'
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: b5a689ca3ade36ef77da958549894f76e074986e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89143530"
---
# <a name="unmanaged-types-c-reference"></a>Types non managés (référence C#)

Un type est un **type non managé** s’il s’agit de l’un des types suivants :

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Tout type [enum](enum.md)
- Tout type [pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Tout type [struct](struct.md) défini par l’utilisateur qui contient des champs de types non managés uniquement et, en C# 7,3 et antérieur, n’est pas un type construit (un type qui inclut au moins un argument de type)

À compter de C# 7,3, vous pouvez utiliser la [ `unmanaged` contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé qui n’est pas un pointeur, non Nullable.

À compter de C# 8,0, un type struct *construit* qui contient des champs de types non managés uniquement est également non managé, comme le montre l’exemple suivant :

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Un struct générique peut être la source des types construits non managés et non managés. L’exemple précédent définit un struct générique `Coords<T>` et présente les exemples de types construits non managés. L’exemple de n’est pas un type non managé `Coords<object>` . Elle n’est pas non plus gérée, car elle contient les champs du `object` type, qui ne sont pas non managés. Si vous souhaitez que *tous les* types construits soient des types non managés, utilisez la `unmanaged` contrainte dans la définition d’un struct générique :

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
- [Opérateur sizeof](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)

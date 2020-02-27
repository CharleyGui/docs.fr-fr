---
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 042cf382879cc4010a388fb75f41099b4342c9d9
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626943"
---
# <a name="unmanaged-types-c-reference"></a>Types non managés (référence C#)

Un type est un **type non managé** s’il s’agit de l’un des types suivants :

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Tout type [enum](enum.md)
- Tout type [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Tout type [struct](struct.md) défini par l’utilisateur qui contient des champs de types non managés uniquement et C# , dans 7,3 et les versions antérieures, n’est pas un type construit (un type qui inclut au moins un argument de type)

À partir C# de 7,3, vous pouvez utiliser la [contrainte`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non managé non-pointeur, non Nullable.

À C# partir de 8,0, un type struct *construit* qui contient des champs de types non managés uniquement est également non managé, comme le montre l’exemple suivant :

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Un struct générique peut être la source des types construits non managés et non managés. L’exemple précédent définit une structure générique `Coords<T>` et présente les exemples de types construits non managés. L’exemple de type non managé est `Coords<object>`. Elle n’est pas non plus gérée, car elle contient les champs du type de `object`, qui n’est pas non géré. Si vous souhaitez que *tous les* types construits soient des types non managés, utilisez la contrainte `unmanaged` dans la définition d’un struct générique :

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
- [Opérateur sizeof](../operators/sizeof.md)
- [Opérateur stackalloc](../operators/stackalloc.md)

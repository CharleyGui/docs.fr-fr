---
title: Types non managés - Référence C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846460"
---
# <a name="unmanaged-types-c-reference"></a>Types non managés (référence C#)

Un type est un **type non menté** s’il s’agit de l’un des types suivants :

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal` ou `bool`
- Tout type [enum](enum.md)
- Tout type [de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Tout type [de struction](struct.md) défini par l’utilisateur qui ne contient que des champs de types non traités et, dans C 7.3 et plus tôt, n’est pas un type construit (un type qui comprend au moins un argument de type)

En commençant par le C 7.3, vous pouvez utiliser la [ `unmanaged` contrainte](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) pour spécifier qu’un paramètre de type est un type non-pointeur et non-nullable non managérétique.

Commençant par le C 8.0, un type de struct *construit* qui contient des champs de types non managéraux seulement n’est également non managéré, comme le montre l’exemple suivant :

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Une struct générique peut être la source de types construits non mentés et non non mentés. L’exemple précédent définit une `Coords<T>` struction générique et présente les exemples de types construits non mentés. L’exemple de ne pas un `Coords<object>`type non-gestion est . Ce n’est pas unmanaged parce `object` qu’il a les champs du type, qui n’est pas non gestion. Si vous voulez que *tous les* types construits `unmanaged` soient des types non gémandés, utilisez la contrainte dans la définition d’une struct générique :

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Types de pointeur](~/_csharplang/spec/unsafe-code.md#pointer-types) de la [Spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à la travée](../../../standard/memory-and-spans/index.md)
- [sizeof, opérateur](../operators/sizeof.md)
- [Opérateur stackalloc](../operators/stackalloc.md)

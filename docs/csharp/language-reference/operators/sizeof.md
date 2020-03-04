---
title: sizeof, opérateur- Référence C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 711005479eea2757b4ef18f6710a4453bfca02f9
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238830"
---
# <a name="sizeof-operator-c-reference"></a>sizeof, opérateur (référence C#)

L’opérateur `sizeof` retourne le nombre d’octets occupés par une variable d’un type donné. L’argument de l’opérateur `sizeof` doit être le nom d’un [type non managé](../builtin-types/unmanaged-types.md) ou d’un paramètre de type qui est [contraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) comme type non managé.

L’opérateur `sizeof` nécessite un contexte [unsafe](../keywords/unsafe.md). Toutefois, les expressions présentées dans le tableau suivant sont évaluées au moment de la compilation par rapport aux valeurs de constante correspondantes et ne nécessitent pas de contexte unsafe :

|Expression|Valeur constante|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Vous n’avez pas non plus besoin d’utiliser un contexte unsafe quand l’opérande de l’opérateur `sizeof` est le nom d’un type [enum](../builtin-types/enum.md).

L’exemple suivant illustre l’utilisation de l’opérateur `sizeof` :

[!code-csharp[sizeof examples](~/samples/snippets/csharp/language-reference/operators/SizeOfOperator.cs)]

L’opérateur `sizeof` retourne un nombre d’octets qui seraient alloués par la Common Language Runtime dans la mémoire managée. Pour les types [struct](../builtin-types/struct.md), cette valeur comprend le remplissage, comme le montre l’exemple précédent. Le résultat de l’opérateur `sizeof` peut différer de celui de la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, qui retourne la taille d’un type dans la mémoire *non managée*.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateur sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs associés au pointeur](pointer-related-operators.md)
- [Types de pointeur](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Types liés à la mémoire et à l’étendue](../../../standard/memory-and-spans/index.md)
- [Génériques en .NET](../../../standard/generics/index.md)

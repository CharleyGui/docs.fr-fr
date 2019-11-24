---
title: Opérateurs au niveau du bit et opérateurs de décalage - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations logiques de décalage ou au niveau du bit avec des opérandes de types intégraux.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 27f7cf46bd3e344503f74527df34506d38ad4545
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428437"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Opérateurs au niveau du bit et opérateurs de décalage (référence C#)

The following operators perform bitwise or shift operations with operands of the [integral numeric types](../builtin-types/integral-numeric-types.md) or the [char](../builtin-types/char.md) type:

- Opérateur unaire [`~` (complément de bits)](#bitwise-complement-operator-)
- Opérateurs de décalage binaires [`<<` (décalage gauche)](#left-shift-operator-) et [`>>` (décalage droite)](#right-shift-operator-)
- Opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-)

Ces opérateurs sont définis pour les types `int`, `uint`, `long` et `ulong`. Lorsque les deux opérandes sont d’autres types intégraux (`sbyte`, `byte`, `short`, `ushort` ou `char`), leurs valeurs sont converties en valeurs de type `int`, qui est également le type de résultat d’une opération. Lorsque les opérandes sont de différents types intégraux, leurs valeurs sont converties vers le type intégral le plus proche. Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

The `&`, `|`, and `^` operators are also defined for operands of the `bool` type. Pour plus d’informations, consultez [Opérateurs logiques booléens](boolean-logical-operators.md).

Les opérations de décalage et au niveau du bit ne provoquent jamais de dépassements de capacité et donnent les mêmes résultats dans des contextes [checked et unchecked](../keywords/checked-and-unchecked.md).

## <a name="bitwise-complement-operator-"></a>Opérateur de complément de bits ~

L’opérateur `~` produit un complément de bits de son opérande en inversant chaque bit :

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Vous pouvez également utiliser le symbole `~` pour déclarer des finaliseurs. Pour plus d’informations, consultez [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Opérateur de décalage gauche \<\<

L’opérateur `<<` décale son opérande de partie gauche vers le nombre de bits spécifié par son opérande de partie droite.

L’opération de décalage gauche supprime les bits d’ordre supérieur qui sont en dehors de la plage du type de résultat, et définit les positions de bits vides d’ordre inférieur sur zéro, comme le montre l’exemple suivant :

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Étant donné que les opérateurs de décalage sont définis uniquement pour les types `int`, `uint`, `long` et `ulong`, le résultat d’une opération contient toujours au moins 32 bits. Si l’opérande de partie gauche est d’un autre type intégral (`sbyte`, `byte`, `short`, `ushort` ou `char`), sa valeur est convertie en type `int`, comme l’indique l’exemple suivant :

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `<<` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).

## <a name="right-shift-operator-"></a>Opérateur de décalage vers la droite >>

L’opérateur `>>` décale son opérande de partie gauche vers le nombre de bits défini par son opérande de partie droite.

L’opération de décalage vers la droite ignore les bits d’ordre inférieur, comme le montre l’exemple suivant :

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Les positions de bits vides d’ordre supérieur sont définies en fonction du type de l’opérande de partie gauche comme suit :

- If the left-hand operand is of type `int` or `long`, the right-shift operator performs an *arithmetic* shift: the value of the most significant bit (the sign bit) of the left-hand operand is propagated to the high-order empty bit positions. Autrement dit, les positions de bits vides d’ordre supérieur sont définies sur zéro si l’opérande de partir gauche n’est pas négatif et sur un s’il est négatif.

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- If the left-hand operand is of type `uint` or `ulong`, the right-shift operator performs a *logical* shift: the high-order empty bit positions are always set to zero.

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `>>` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).

## <a name="logical-and-operator-"></a> Opérateur AND logique &amp;

L’opérateur `&` calcule le AND logique au niveau du bit de ses opérandes :

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

For `bool` operands, the `&` operator computes the [logical AND](boolean-logical-operators.md#logical-and-operator-) of its operands. L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>L’opérateur OR exclusif logique ^

L’opérateur `^` calcule le OR exclusif logique au niveau du bit (également appelé XOR logique au niveau du bit) de ses opérandes.

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

For `bool` operands, the `^` operator computes the [logical exclusive OR](boolean-logical-operators.md#logical-exclusive-or-operator-) of its operands.

## <a name="logical-or-operator-"></a>L’opérateur OU logique |

L’opérateur `|` calcule le OR logique au niveau du bit de ses opérandes :

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

For `bool` operands, the `|` operator computes the [logical OR](boolean-logical-operators.md#logical-or-operator-) of its operands.

## <a name="compound-assignment"></a>Assignation composée

Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire

```csharp
x op= y
```

est équivalent à

```csharp
x = x op y
```

sauf que `x` n’est évalué qu’une seule fois.

L’exemple suivant montre l’utilisation de l’assignation composée avec des opérateurs de décalage et des opérateurs au niveau du bit :

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`. Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois. L’exemple suivant illustre ce comportement :

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Priorité des opérateurs

La liste suivante présente les opérateurs au niveau du bit et les opérateurs de décalage par ordre de précédence, de la plus élevée à la plus basse :

- Opérateur de complément de bits `~`
- Opérateurs de décalage `<<` et `>>`
- L’opérateur AND logique `&`
- Opérateur OR exclusif logique `^`
- Opérateur OR logique `|`

Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.

## <a name="shift-count-of-the-shift-operators"></a>Valeur de décalage des opérateurs de décalage

For the shift operators `<<` and `>>`, the type of the right-hand operand must be `int` or a type that has a [predefined implicit numeric conversion](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) to `int`.

Pour les expressions `x << count` et `x >> count`, la valeur réelle du décalage varie selon le type de `x` :

- If the type of `x` is `int` or `uint`, the shift count is defined by the low-order *five* bits of the right-hand operand. La valeur de décalage est donc calculée à partir de `count & 0x1F` (ou de `count & 0b_1_1111`).

- If the type of `x` is `long` or `ulong`, the shift count is defined by the low-order *six* bits of the right-hand operand. La valeur de décalage est donc calculée à partir de `count & 0x3F` (ou de `count & 0b_11_1111`).

L’exemple suivant illustre ce comportement :

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a>Opérateurs logiques d’énumération

The `~`, `&`, `|`, and `^` operators are also supported by any [enumeration](../keywords/enum.md) type. For operands of the same enumeration type, a logical operation is performed on the corresponding values of the underlying integral type. Par exemple, pour tout `x` et `y` d’un type énumération `T` avec un type sous-jacent `U`, l’expression `x & y` produit le même résultat que l’expression `(T)((U)x & (U)y)`.

Vous utilisez généralement des opérateurs logiques au niveau du bit avec un type énumération qui est défini à l’aide de l’attribut [Flags](xref:System.FlagsAttribute). Pour plus d’informations, consultez la section [Types énumération comme indicateurs binaires](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) de l’article[Types énumération](../../programming-guide/enumeration-types.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `~`, `<<`, `>>`, `&`, `|` et `^`. Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.

Si un type `T` défini par l’utilisateur surcharge l’opérateur `<<` ou `>>`, l’opérande de partie gauche doit être de type `T` et l’opérande de partie droite de type `int`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateur de complément de bits](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Opérateurs de décalage](~/_csharplang/spec/expressions.md#shift-operators)
- [Opérateurs logiques](~/_csharplang/spec/expressions.md#logical-operators)
- [Assignation composée](~/_csharplang/spec/expressions.md#compound-assignment)
- [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs logiques booléens](boolean-logical-operators.md)

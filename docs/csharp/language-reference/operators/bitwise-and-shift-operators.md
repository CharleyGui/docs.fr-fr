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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399265"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Opérateurs au niveau du bit et opérateurs de décalage (référence C#)

Les opérateurs suivants effectuent des opérations de décalage ou de décalage avec des opérands des [types numériques intégrals](../builtin-types/integral-numeric-types.md) ou du type [d’omble :](../builtin-types/char.md)

- Opérateur unary [ `~` (bitwise complement)](#bitwise-complement-operator-)
- Opérateurs binaires [ `<<` (changement de gauche)](#left-shift-operator-) et [ `>>` (changement de droite)](#right-shift-operator-)
- Opérateurs [ `&` binaires (logiques ET)](#logical-and-operator-) [ `|` , (logiques)](#logical-or-operator-)et [ `^` (logiques exclusives OU)](#logical-exclusive-or-operator-)

Ces opérateurs sont définis pour les types `int`, `uint`, `long` et `ulong`. Lorsque les deux opérandes sont d’autres types intégraux (`sbyte`, `byte`, `short`, `ushort` ou `char`), leurs valeurs sont converties en valeurs de type `int`, qui est également le type de résultat d’une opération. Lorsque les opérandes sont de différents types intégraux, leurs valeurs sont converties vers le type intégral le plus proche. Pour plus d’informations, consultez la section [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Le `&` `|`, `^` , et les opérateurs sont `bool` également définis pour les opérands du type. Pour plus d’informations, consultez [Opérateurs logiques booléens](boolean-logical-operators.md).

Les opérations de décalage et au niveau du bit ne provoquent jamais de dépassements de capacité et donnent les mêmes résultats dans des contextes [checked et unchecked](../keywords/checked-and-unchecked.md).

## <a name="bitwise-complement-operator-"></a>Opérateur de complément de bits ~

L’opérateur `~` produit un complément de bits de son opérande en inversant chaque bit :

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Vous pouvez également utiliser le symbole `~` pour déclarer des finaliseurs. Pour plus d’informations, consultez [Finaliseurs](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Opérateur de décalage gauche \<\<

L’opérateur `<<` déplace son opérat gauche à gauche par le [nombre de bits définis par son opéra de droite](#shift-count-of-the-shift-operators).

L’opération de décalage gauche supprime les bits d’ordre supérieur qui sont en dehors de la plage du type de résultat, et définit les positions de bits vides d’ordre inférieur sur zéro, comme le montre l’exemple suivant :

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

Étant donné que les opérateurs de décalage sont définis uniquement pour les types `int`, `uint`, `long` et `ulong`, le résultat d’une opération contient toujours au moins 32 bits. Si l’opérande de partie gauche est d’un autre type intégral (`sbyte`, `byte`, `short`, `ushort` ou `char`), sa valeur est convertie en type `int`, comme l’indique l’exemple suivant :

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `<<` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).

## <a name="right-shift-operator-"></a>Opérateur de décalage vers la droite >>

L’opérateur `>>` déplace son opéra de gauche à droite par le [nombre de bits définis par son opéra de droite](#shift-count-of-the-shift-operators).

L’opération de décalage vers la droite ignore les bits d’ordre inférieur, comme le montre l’exemple suivant :

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

Les positions de bits vides d’ordre supérieur sont définies en fonction du type de l’opérande de partie gauche comme suit :

- Si l’opérande gauche `int` est `long`de type ou, l’opérateur de virage à droite effectue un changement *arithmétique* : la valeur du bit le plus significatif (le bit de signe) de l’opératoire gauche est propagée aux positions de bit vide de haut ordre. Autrement dit, les positions de bits vides d’ordre supérieur sont définies sur zéro si l’opérande de partir gauche n’est pas négatif et sur un s’il est négatif.

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Si l’opératoire gauche `uint` est `ulong`de type ou, l’opérateur de virage à droite effectue un changement *logique* : les positions de bits vides de haut ordre sont toujours réglées à zéro.

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Pour plus d’informations sur la façon dont l’opérande de partie droite de l’opérateur `>>` définit la valeur de décalage, consultez la section [Valeur de décalage des opérateurs de décalage](#shift-count-of-the-shift-operators).

## <a name="logical-and-operator-"></a>Logique ET opérateur&amp;

L’opérateur `&` calcule le AND logique au niveau du bit de ses opérandes :

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Pour `bool` les opérands, l’opérateur `&` calcule la logique [ET](boolean-logical-operators.md#logical-and-operator-) de ses opérandes. L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>L’opérateur OR exclusif logique ^

L’opérateur `^` calcule le OR exclusif logique au niveau du bit (également appelé XOR logique au niveau du bit) de ses opérandes.

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

Pour `bool` les opérands, l’opérateur `^` calcule la logique exclusive [OR](boolean-logical-operators.md#logical-exclusive-or-operator-) de ses opérandes.

## <a name="logical-or-operator-"></a>L’opérateur OU logique |

L’opérateur `|` calcule le OR logique au niveau du bit de ses opérandes :

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

Pour `bool` les opérandes, l’opérateur `|` calcule la [DO logique](boolean-logical-operators.md#logical-or-operator-) de ses opérandes.

## <a name="compound-assignment"></a>Assignation composée

Pour un opérateur binaire `op`, une expression d’assignation composée du formulaire

```csharp
x op= y
```

équivaut à :

```csharp
x = x op y
```

sauf que `x` n’est évalué qu’une seule fois.

L’exemple suivant montre l’utilisation de l’assignation composée avec des opérateurs de décalage et des opérateurs au niveau du bit :

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

En raison des [promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions), le résultat de l’opération `op` risque de ne pas être implicitement convertible en type `T` de `x`. Dans ce cas, si `op` est un opérateur prédéfini et que le résultat de l’opération est explicitement convertible en type `T` de `x`, une expression d’assignation composée de la forme `x op= y` équivaut à `x = (T)(x op y)`, sauf que `x` n’est évalué qu’une seule fois. L’exemple suivant illustre ce comportement :

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Précédence des opérateurs

La liste suivante présente les opérateurs au niveau du bit et les opérateurs de décalage par ordre de précédence, de la plus élevée à la plus basse :

- Opérateur de complément de bits `~`
- Opérateurs de décalage `<<` et `>>`
- L’opérateur AND logique `&`
- Opérateur OR exclusif logique `^`
- Opérateur OR logique `|`

Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

Pour la liste complète des opérateurs C’commandés par niveau de préséance, voir la section [De préséance de l’opérateur](index.md#operator-precedence) de [l’article des opérateurs C.](index.md)

## <a name="shift-count-of-the-shift-operators"></a>Valeur de décalage des opérateurs de décalage

Pour les `<<` opérateurs `>>`de quarts et , le type `int` de l’opéra de droite doit être `int`ou un type qui a une conversion numérique implicite [prédéfinie](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) à .

Pour les expressions `x << count` et `x >> count`, la valeur réelle du décalage varie selon le type de `x` :

- Si le `x` type `int` `uint`de est ou , le nombre de décalage est défini par le bas-ordre *cinq* bits de l’opéra de droite. La valeur de décalage est donc calculée à partir de `count & 0x1F` (ou de `count & 0b_1_1111`).

- Si le `x` type `long` `ulong`de est ou , le nombre de décalage est défini par l’ordre bas *six* bits de l’opéra de droite. La valeur de décalage est donc calculée à partir de `count & 0x3F` (ou de `count & 0b_11_1111`).

L’exemple suivant illustre ce comportement :

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Comme le montre l’exemple précédent, le résultat d’une opération de quart peut être non nul, même si la valeur de l’opéra de droite est supérieure au nombre de bits dans l’opéra de gauche.

## <a name="enumeration-logical-operators"></a>Opérateurs logiques d’énumération

Le `~` `&`, `|`, `^` et les opérateurs sont également pris en charge par tout type [de recensement.](../builtin-types/enum.md) Pour les opérandes du même type d’énumération, une opération logique est effectuée sur les valeurs correspondantes du type intégral sous-jacent. Par exemple, pour tout `x` et `y` d’un type énumération `T` avec un type sous-jacent `U`, l’expression `x & y` produit le même résultat que l’expression `(T)((U)x & (U)y)`.

Vous utilisez généralement des opérateurs logiques bitwise avec un type d’énumération qui est défini avec l’attribut [Drapeaux.](xref:System.FlagsAttribute) Pour plus d’informations, consultez la section [Types énumération comme indicateurs binaires](../builtin-types/enum.md#enumeration-types-as-bit-flags) de l’article[Types énumération](../builtin-types/enum.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur `>>` `&`peut `|` [surcharger](operator-overloading.md) le `~`, `<<`, , , et `^` les opérateurs. Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.

Si un type `T` défini par l’utilisateur surcharge l’opérateur `<<` ou `>>`, l’opérande de partie gauche doit être de type `T` et l’opérande de partie droite de type `int`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateur de complément Bitwise](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Opérateurs de décalage](~/_csharplang/spec/expressions.md#shift-operators)
- [Opérateurs logiques](~/_csharplang/spec/expressions.md#logical-operators)
- [Assignation composée](~/_csharplang/spec/expressions.md#compound-assignment)
- [Promotions numériques](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Opérateurs logiques booléens](boolean-logical-operators.md)

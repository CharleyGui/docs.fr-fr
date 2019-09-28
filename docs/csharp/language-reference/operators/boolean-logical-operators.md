---
title: Opérateurs logiques booléens - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de négation logique, de conjonction (AND) et de disjonction inclusive et exclusive (OR) avec des opérandes booléens.
ms.date: 04/08/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: 39f5be7a667b4e37e84246ef0bfeb03c0099d4b7
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353364"
---
# <a name="boolean-logical-operators-c-reference"></a>Opérateurs logiques booléens (référence C#)

Les opérateurs suivants effectuent des opérations logiques avec les opérandes [booléens](../keywords/bool.md) :

- opérateur unaire [`!` (négation logique)](#logical-negation-operator-) ;
- opérateurs binaires [`&` (AND logique)](#logical-and-operator-), [`|` (OR logique)](#logical-or-operator-) et [`^` (OR exclusif logique)](#logical-exclusive-or-operator-), qui évaluent toujours les deux opérandes ;
- opérateurs binaires [`&&` (AND logique conditionnel)](#conditional-logical-and-operator-) et [`||` (OR logique conditionnel)](#conditional-logical-or-operator-), Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.

En ce qui concerne les opérandes de type [intégral](../builtin-types/integral-numeric-types.md), les opérateurs `&`, `|` et `^` effectuent des opérations logiques au niveau du bit. Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>L’opérateur de négation logique !

L’opérateur `!` calcule la négation logique de son opérande. Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a> Opérateur AND logique &amp;

L’opérateur `&` calcule le AND logique de ses opérandes. Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`. Sinon, le résultat est `false`.

L’opérateur `&` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `false`. Le résultat doit donc être `false` quelle que soit la valeur de l’opérande de partie droite.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.

Dans le cas des opérandes de type intégral, l’opérateur `&` calcule le [AND logique au niveau du bit](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes. L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>L’opérateur OR exclusif logique ^

L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes. Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`. Sinon, le résultat est `false`. Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

Dans le cas des opérandes de type intégral, l’opérateur `^` calcule le [OR exclusif logique au niveau du bit](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) de ses opérandes.

## <a name="logical-or-operator-"></a>L’opérateur OU logique |

L’opérateur `|` calcule le OR logique de ses opérandes. Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`. Sinon, le résultat est `false`.

L’opérateur `|` évalue les deux opérandes, même si l’opérande de partie gauche donne la valeur de `true`. Le résultat doit donc être `true` quelle que soit la valeur de l’opérande de partie droite.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.

Dans le cas des opérandes de type intégral, l’opérateur `|` calcule le [OR logique au niveau du bit](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérandes.

## <a name="conditional-logical-and-operator-"></a> Opérateur AND logique conditionnel &amp;&amp;

L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes. Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`. Sinon, le résultat est `false`. Si `x` donne la valeur de `false`, `y` n’est pas évalué.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.

## <a name="conditional-logical-or-operator-"></a>L’opérateur OR logique conditionnel ||

L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes. Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`. Sinon, le résultat est `false`. Si `x` donne la valeur de `true`, `y` n’est pas évalué.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[L’opérateur OR logique](#logical-or-operator-) `|` calcule également le OR logique de ses opérandes, mais évalue toujours les deux opérandes.

## <a name="nullable-boolean-logical-operators"></a>Les opérateurs logiques booléens Nullable

Dans le cas des opérandes `bool?`, les opérateurs `&` et `|` prennent en charge la logique à trois valeurs. La sémantique de ces opérateurs est définie par le tableau suivant :  
  
|x|o|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|Null|Null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|Null|false|null|  
|Null|true|Null|true|  
|Null|false|false|null|  
|Null|Null|Null|Null|  

Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable. En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant. Il produit `null` si l’un de ses opérandes est `null`. Toutefois, les opérateurs `&` et `|` peuvent produire une valeur non Null même si l’un des opérandes est `null`. Pour plus d’informations sur le comportement de l’opérateur avec les types valeur Nullable, consultez la section [opérateurs](../../programming-guide/nullable-types/using-nullable-types.md#operators) de l’article [utilisation de types valeur Nullable](../../programming-guide/nullable-types/using-nullable-types.md) .

Vous pouvez également utiliser les opérateurs `!` et `^` avec les opérandes `bool?`, comme le montre l’exemple suivant :

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge les opérandes `bool?`.

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

Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Les opérateurs logiques conditionnels `&&` et `||` ne prennent pas en charge l’assignation composée.

## <a name="operator-precedence"></a>Précédence des opérateurs

La liste suivante présente les opérateurs logiques par ordre de précédence, de la plus élevée à la plus basse :

- Opérateur de négation logique `!`
- L’opérateur AND logique `&`
- Opérateur OR exclusif logique `^`
- Opérateur OR logique `|`
- Opérateur AND logique conditionnel `&&`
- Opérateur OR logique conditionnel `||`

Utilisez des parenthèses, `()`, pour modifier l’ordre d’évaluation imposé par la précédence des opérateurs :

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Pour obtenir la liste complète des opérateurs C# classés par niveau de priorité, consultez [Opérateurs C#](index.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `!`, `&`, `|` et `^`. Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.

Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`. Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateur de négation logique](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Opérateurs logiques](~/_csharplang/spec/expressions.md#logical-operators)
- [Opérateurs logiques conditionnels](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Assignation composée](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md)

---
title: Opérateurs logiques booléens - Référence C#
description: Découvrez les opérateurs C# qui effectuent des opérations de négation logique, de conjonction (AND) et de disjonction inclusive et exclusive (OR) avec des opérandes booléens.
ms.date: 09/27/2019
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399496"
---
# <a name="boolean-logical-operators-c-reference"></a>Opérateurs logiques booléens (référence C#)

Les opérateurs suivants effectuent des opérations logiques avec des opérands [bool](../builtin-types/bool.md) :

- Opérateur nonaire [ `!` (négation logique).](#logical-negation-operator-)
- Opérateurs [ `&` binaires (logiques ET)](#logical-and-operator-) [ `|` , (logiques)](#logical-or-operator-)et [ `^` (logiques exclusives OU).](#logical-exclusive-or-operator-) qui évaluent toujours les deux opérandes ;
- Opérateurs [ `&&` binaires (conditionnels logiques)](#conditional-logical-and-operator-) et [ `||` (conditionnel logiques).](#conditional-logical-or-operator-) Ces opérateurs n’évaluent l’opérande de partie droite que si nécessaire.

Pour les opérands des types `&` `|` `^` [numériques intégrals,](../builtin-types/integral-numeric-types.md)le , et les opérateurs effectuer des opérations logiques bitwise. Pour plus d’informations, consultez [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>L’opérateur de négation logique !

L’opérateur de `!` préfixe unary calcule la négation logique de son opérande. Autrement dit, il produit `true` si l’opérande donne `false` et `false` si l’opérande donne `true` :

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

Commençant par C 8.0, l’opérateur de poteaufix `!` nonary est [l’opérateur nul-indulgent](null-forgiving.md).

## <a name="logical-and-operator-"></a>Logique ET opérateur&amp;

L’opérateur `&` calcule le AND logique de ses opérandes. Le résultat de `x & y` est `true` si `x` et `y` prennent la valeur `true`. Sinon, le résultat est `false`.

L’opérateur `&` évalue les deux opérandes même si l’opérande gauche évalue à `false`, de sorte que le résultat de l’opération est `false` indépendamment de la valeur de l’opéra de droite.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[L’opérateur AND logique conditionnel](#conditional-logical-and-operator-) `&&` calcule également le AND logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `false`.

Pour les opérandes des types `&` [numériques intégrals,](../builtin-types/integral-numeric-types.md)l’opérateur calcule la logique [bitwise ET](bitwise-and-shift-operators.md#logical-and-operator-) de ses opérandes. L’opérateur unaire `&` est [l’opérateur address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>L’opérateur OR exclusif logique ^

L’opérateur `^` calcule le OR exclusif logique, également appelé XOR logique, de ses opérandes. Le résultat de `x ^ y` est `true` si `x` donne `true` et `y` donne `false`, ou `x` donne `false` et `y` donne `true`. Sinon, le résultat est `false`. Autrement dit, pour les opérandes `bool`, l’opérateur `^` calcule le même résultat que [l’opérateur d’inégalité](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

Pour les opérandes des types `^` [numériques intégrals,](../builtin-types/integral-numeric-types.md)l’opérateur calcule [l’exclusivité logique bitwise de](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) ses opérands.

## <a name="logical-or-operator-"></a>L’opérateur OU logique |

L’opérateur `|` calcule le OR logique de ses opérandes. Le résultat de `x | y` est `true` si `x` ou `y` prend la valeur `true`. Sinon, le résultat est `false`.

L’opérateur `|` évalue les deux opérandes même si l’opérande gauche évalue à `true`, de sorte que le résultat de l’opération est `true` indépendamment de la valeur de l’opéra de droite.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `|` est un appel de méthode, effectué indépendamment de la valeur de l’opérande de partie gauche :

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[L’opérateur OR logique conditionnel](#conditional-logical-or-operator-) `||` calcule également le OR logique de ses opérandes, mais n’évalue pas l’opérande de partie droite si l’opérande de partie gauche donne la valeur de `true`.

Pour les opérandes des types `|` [numériques intégrals,](../builtin-types/integral-numeric-types.md)l’opérateur calcule la logique [bitwise OU](bitwise-and-shift-operators.md#logical-or-operator-) de ses opérands.

## <a name="conditional-logical-and-operator-"></a>Conditionnel logique ET opérateur&amp;&amp;

L’opérateur AND logique conditionnel `&&`, également appelé opérateur AND logique de « court-circuit », calcule le AND logique de ses opérandes. Le résultat de `x && y` est `true` si `x` et `y` prennent la valeur `true`. Sinon, le résultat est `false`. Si `x` donne la valeur de `false`, `y` n’est pas évalué.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `&&` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `false` :

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[L’opérateur AND logique](#logical-and-operator-) `&` calcule également le AND logique de ses opérandes, mais évalue toujours les deux opérandes.

## <a name="conditional-logical-or-operator-"></a>L’opérateur OR logique conditionnel ||

L’opérateur OR logique conditionnel `||`, également appelé opérateur OR logique de « court-circuit », calcule le OR logique de ses opérandes. Le résultat de `x || y` est `true` si `x` ou `y` prend la valeur `true`. Sinon, le résultat est `false`. Si `x` donne la valeur de `true`, `y` n’est pas évalué.

Dans l’exemple suivant, l’opérande de partie droite de l’opérateur `||` est un appel de méthode, non effectué si l’opérande de partie gauche donne la valeur de `true` :

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

`|` [L’opérateur de l’OR logique](#logical-or-operator-) calcule également la DO logique de ses opérandes, mais évalue toujours les deux opérandes.

## <a name="nullable-boolean-logical-operators"></a>Les opérateurs logiques booléens Nullable

Pour `bool?` les opérands, les `&` opérateurs et `|` les opérateurs soutiennent la logique à trois valeur. La sémantique de ces opérateurs est définie par le tableau suivant :  
  
|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Le comportement de ces opérateurs diffère du comportement classique des opérateurs avec des types valeur Nullable. En règle générale, un opérateur défini pour les opérandes d’un type valeur peut être également utilisé avec des opérandes du type valeur Nullable correspondant. Un tel `null` opérateur produit si l’un `null`de ses opérands évalue à . Cependant, `&` les `|` opérateurs et les opérateurs peuvent produire non-null, `null`même si l’un des opérands évalue à . Pour plus d’informations sur le comportement de l’opérateur avec des types de valeur nul, consultez la section [opérateurs lifted](../builtin-types/nullable-value-types.md#lifted-operators) de [l’article nullable types](../builtin-types/nullable-value-types.md) de valeurs.

Vous pouvez également `!` `^` utiliser `bool?` les opérateurs et les opérateurs avec des opérands, comme le montre l’exemple suivant :

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Les opérateurs `&&` logiques conditionnels et `||` ne soutiennent `bool?` pas les opérands.

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

Les opérateurs `&`, `|` et `^` prennent en charge l’assignation composée, comme le montre l’exemple suivant :

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

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

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Pour la liste complète des opérateurs C’commandés par niveau de préséance, voir la section [De préséance de l’opérateur](index.md#operator-precedence) de [l’article des opérateurs C.](index.md)

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur `|`peut `^` [surcharger](operator-overloading.md) le `!`, `&`, et les opérateurs. Quand un opérateur binaire est surchargé, l’opérateur d’assignation composée correspondant est aussi implicitement surchargé. Un type défini par l’utilisateur ne peut pas surcharger explicitement un opérateur d’assignation composée.

Un type défini par l’utilisateur ne peut pas surcharger les opérateurs logiques conditionnels `&&` et `||`. Toutefois, si un type défini par l’utilisateur surcharge les [opérateurs true et false](true-false-operators.md) et l’opérateur `&` ou `|` d’une certaine manière, l’opération `&&` ou `||` peut être évaluée respectivement pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Opérateur de négation logique](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Opérateurs logiques](~/_csharplang/spec/expressions.md#logical-operators)
- [Opérateurs logiques conditionnels](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Assignation composée](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Opérateurs de bits et de décalage](bitwise-and-shift-operators.md)

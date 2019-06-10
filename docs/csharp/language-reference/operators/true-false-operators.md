---
title: Opérateurs true et false - Référence C#
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: b1acf9a16dd977ec49a7f1dc3bea4ee41792e9be
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758140"
---
# <a name="true-and-false-operators-c-reference"></a>Opérateurs true et false (Référence C#)

L’opérateur `true` retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est true. L’opérateur `false` retourne la valeur `bool` `true` pour indiquer qu’un opérande est false. Les opérateurs `true` et `false` ne sont pas forcément complémentaires. Autrement dit, les opérateurs `true` et `false` peuvent retourner la valeur `bool` `false` pour le même opérande. Si un type définit un des deux opérateurs, il doit aussi définir un autre opérateur.

Si un type avec les opérateurs `true` et `false` définis [surcharge](../keywords/operator.md) [l’opérateur OR logique](boolean-logical-operators.md#logical-or-operator-) `|` ou [l’opérateur AND logique](boolean-logical-operators.md#logical-and-operator-) `&` d’une façon, [l’opérateur OR logique conditionnel](boolean-logical-operators.md#conditional-logical-or-operator-) `||` ou [l’opérateur AND logique conditionnel](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectivement, peut être évalué pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Un type avec l’opérateur `true` défini peut être le type de résultat d’une expression conditionnelle de contrôle dans les instructions [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md) et [for](../keywords/for.md) et dans [l’opérateur conditionnel `?:`](conditional-operator.md). Pour plus d’informations, voir la section [Expressions booléennes](~/_csharplang/spec/expressions.md#boolean-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

> [!TIP]
> Utilisez le type `bool?` si vous voulez suivre une logique à trois valeurs, par exemple pour travailler avec des bases de données qui acceptent un type booléen à trois valeurs. C# fournit les opérateurs `&` et `|` qui prennent en charge la logique à trois valeurs avec les opérandes `bool?`. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](boolean-logical-operators.md).

L’exemple suivant présente le type qui définit les opérateurs `true` et `false`. Par ailleurs, il surcharge l’opérateur AND logique `&` de sorte que l’opérateur `&&` peut aussi être évalué pour les opérandes de ce type.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Remarquez le comportement de court-circuit de l’opérateur `&&`. Lorsque la méthode `GetFuelLaunchStatus` retourne `LaunchStatus.Red`, le second opérande de l’opérateur `&&` n’est pas évalué. En effet, `LaunchStatus.Red` est false. Le résultat du AND logique ne dépend donc pas la valeur du second opérande. Voici la sortie de l’exemple :

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Opérateurs C#](index.md)
- [`true`, littéral](../keywords/true-literal.md)
- [`false`, littéral](../keywords/false-literal.md)

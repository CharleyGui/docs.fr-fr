---
title: Opérateurs true et false - Référence C#
ms.custom: seodec18
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: cb5cde6be16ecf8898c5976e8db23d5ef70d1a47
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401308"
---
# <a name="true-and-false-operators-c-reference"></a>Opérateurs true et false (rférence C#)

L’opérateur `true` retourne la valeur [bool](../keywords/bool.md) `true` pour indiquer qu’un opérande est true. L’opérateur `false` retourne la valeur `bool` `true` pour indiquer qu’un opérande est false. Les opérateurs `true` et `false` ne sont pas forcément complémentaires. Autrement dit, les opérateurs `true` et `false` peuvent retourner la valeur `bool` `false` pour le même opérande. Si un type définit un des deux opérateurs, il doit aussi définir un autre opérateur.

> [!TIP]
> Utilisez le type `bool?` si vous voulez suivre une logique à trois valeurs, par exemple pour travailler avec des bases de données qui acceptent un type booléen à trois valeurs. C# fournit les opérateurs `&` et `|` qui prennent en charge la logique à trois valeurs avec les opérandes `bool?`. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](boolean-logical-operators.md).

## <a name="boolean-expressions"></a>Expressions booléennes

Un type avec l’opérateur `true` défini peut être le type de résultat d’une expression conditionnelle de contrôle dans les instructions [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md) et [for](../keywords/for.md) et dans [l’opérateur conditionnel `?:`](conditional-operator.md). Pour plus d’informations, voir la section [Expressions booléennes](~/_csharplang/spec/expressions.md#boolean-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="user-defined-conditional-logical-operators"></a>Opérateurs logiques conditionnels définis par l’utilisateur

Si un type avec les opérateurs `true` et `false` définis [surcharge](../keywords/operator.md) [l’opérateur OR logique](boolean-logical-operators.md#logical-or-operator-) `|` ou [l’opérateur AND logique](boolean-logical-operators.md#logical-and-operator-) `&` d’une façon, [l’opérateur OR logique conditionnel](boolean-logical-operators.md#conditional-logical-or-operator-) `||` ou [l’opérateur AND logique conditionnel](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectivement, peut être évalué pour les opérandes de ce type. Pour plus d’informations, consultez la section [Opérateurs logiques conditionnels définis par l’utilisateur](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="example"></a>Exemples

L’exemple suivant présente le type qui définit les opérateurs `true` et `false`. Le type surcharge également l’opérateur AND logique `&` de sorte que l’opérateur `&&` peut aussi être évalué pour les opérandes de ce type.

[!code-csharp[true and false operators example](~/samples/csharp/language-reference/operators/TrueFalseOperators.cs)]

Remarquez le comportement de court-circuit de l’opérateur `&&`. Lorsque la méthode `GetFuelLaunchStatus` retourne `LaunchStatus.Red`, l’opérande de partie droite de l’opérateur `&&` n’est pas évalué. En effet, `LaunchStatus.Red` est false. Le résultat du AND logique ne dépend donc pas de la valeur de l’opérande de partie droite. Voici la sortie de l’exemple :

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [true, littéral](../keywords/true-literal.md)
- [false, littéral](../keywords/false-literal.md)

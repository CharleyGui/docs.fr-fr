---
title: opérateur par défaut - référence C#
description: Utilisez l’opérateur par défaut pour produire la valeur par défaut d’un type
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 0d37fe952e71e74f014872231a2e58663dea9d18
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399482"
---
# <a name="default-operator-c-reference"></a>opérateur par défaut (référence C#)

L’opérateur `default` produit la [valeur par défaut](../builtin-types/default-values.md) d’un type. L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type.

L’exemple suivant illustre l’utilisation de l’opérateur `default` :

[!code-csharp-interactive[default of T](snippets/DefaultOperator.cs#WithOperand)]

Vous utilisez `default` également le mot clé comme étiquette de cas par défaut dans une [ `switch` déclaration](../keywords/switch.md).

## <a name="default-literal"></a>littéral par défaut

À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression. L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit. Vous pouvez utiliser le littéral `default` dans les cas suivants :

- Dans l'affectation ou l'initialisation d'une variable.
- Dans la déclaration de la valeur par défaut pour un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).
- Dans un appel de méthode pour fournir une valeur d'argument.
- Dans [ `return` ](../keywords/return.md) une déclaration ou comme une expression dans un [membre expression-corps](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

L’exemple suivant illustre l’utilisation du littéral `default` :

[!code-csharp-interactive[default literal](snippets/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- [Valeurs par défaut des types C](../builtin-types/default-values.md)
- [Génériques en .NET](../../../standard/generics/index.md)

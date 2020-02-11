---
title: opérateur default - référence C#
description: Utiliser l’opérateur par défaut pour produire la valeur par défaut d’un type
ms.date: 08/01/2019
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 651c4698514aee8cf4dab75ea32c98493e19a30b
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964617"
---
# <a name="default-operator-c-reference"></a>opérateur default (référence C#)

L’opérateur `default` produit la [valeur par défaut](../builtin-types/default-values.md) d’un type. L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type.

L’exemple suivant illustre l’utilisation de l’opérateur `default` :

[!code-csharp-interactive[default of T](~/samples/csharp/language-reference/operators/DefaultOperator.cs#WithOperand)]

Vous utilisez également le mot clé `default` comme étiquette de cas par défaut dans une [instruction`switch`](../keywords/switch.md).

## <a name="default-literal"></a>littéral par défaut

À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression. L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit. Vous pouvez utiliser le littéral `default` dans les cas suivants :

- Dans l'affectation ou l'initialisation d'une variable.
- Dans la déclaration de la valeur par défaut d’un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).
- Dans un appel de méthode pour fournir une valeur d'argument.
- Dans une [instruction`return`](../keywords/return.md) ou en tant qu’expression dans un [membre d’expression](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

L’exemple suivant illustre l’utilisation du littéral `default` :

[!code-csharp-interactive[default literal](~/samples/csharp/language-reference/operators/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- [Valeurs par défaut C# des types](../builtin-types/default-values.md)
- [Génériques en .NET](../../../standard/generics/index.md)

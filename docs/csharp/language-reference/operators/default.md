---
title: expressions de valeur par défaut-référence C#
description: Utiliser les expressions de valeur par défaut pour obtenir la valeur par défaut d’un type
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: 92ad8e919567e1f9f57e6875d53c4055eb960829
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997652"
---
# <a name="default-value-expressions-c-reference"></a>expressions de valeur par défaut (référence C#)

Une expression de valeur par défaut produit la [valeur par défaut](../builtin-types/default-values.md) d’un type. Il existe deux types d’expressions de valeur par défaut : l’appel d' [opérateur par défaut](#default-operator) et un [littéral par défaut](#default-literal).

Vous utilisez également le `default` mot clé comme étiquette de cas par défaut dans une [ `switch` instruction](../keywords/switch.md).

## <a name="default-operator"></a>Opérateur default

L’argument de l’opérateur `default` doit avoir le nom d’un type ou d’un paramètre de type, comme le montre l’exemple suivant :

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a>littéral par défaut

À partir de C# 7.1, vous pouvez utiliser le littéral `default` pour produire la valeur par défaut d'un type lorsque le compilateur peut déduire le type d'expression. L’expression littérale `default` génère la même valeur que l’expression `default(T)`, où `T` est le type déduit. Vous pouvez utiliser le littéral `default` dans les cas suivants :

- Dans l'affectation ou l'initialisation d'une variable.
- Dans la déclaration de la valeur par défaut d’un [paramètre de méthode facultatif](../../methods.md#optional-parameters-and-arguments).
- Dans un appel de méthode pour fournir une valeur d'argument.
- Dans une [ `return` instruction](../keywords/return.md) ou en tant qu’expression dans un [membre d’expression](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

L’exemple suivant illustre l’utilisation du littéral `default` :

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir la section [Expressions de valeur par défaut](~/_csharplang/spec/expressions.md#default-value-expressions) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Pour plus d’informations sur le littéral `default`, voir la [proposition de fonctionnalité](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs et expressions C#](index.md)
- [Valeurs par défaut des types C#](../builtin-types/default-values.md)
- [Génériques en .NET](../../../standard/generics/index.md)

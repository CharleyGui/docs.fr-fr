---
title: (), opérateur - Référence C#
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 8f7382a49c81b6fd8e104b864ffc2f70db7fe4a6
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758109"
---
# <a name="-operator-c-reference"></a>(), opérateur (référence C#)

Les parenthèses, `()`, sont généralement utilisées pour l’appel de méthode ou de délégué, ou dans les expressions Cast.

Vous utilisez également des parenthèses pour spécifier l’ordre dans lequel évaluer les opérations dans une expression. Pour plus d’informations, consultez la section [Ajout de parenthèses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) de l’article [Opérateurs](../../programming-guide/statements-expressions-operators/operators.md). Pour obtenir la liste des opérateurs classés par niveau de priorité, consultez [Opérateurs C#](index.md).

## <a name="method-invocation"></a>Appel de méthode

L’exemple suivant montre comment appeler une méthode, avec ou sans arguments, et un délégué :

[!code-csharp-interactive[use for invocation](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

Vous utilisez également des parenthèses quand vous appelez un [constructeur](../../programming-guide/classes-and-structs/constructors.md) avec un opérateur [`new`](../keywords/new-operator.md).

Pour plus d’informations sur les méthodes, consultez [Méthodes](../../programming-guide/classes-and-structs/methods.md). Pour plus d’informations sur les délégués, consultez [Délégués](../../programming-guide/delegates/index.md).

## <a name="cast-expression"></a>Expression Cast

Une expression Cast de la forme `(T)E` appelle un opérateur de conversion pour convertir la valeur d’expression `E` en type `T`. S’il n’existe aucune conversion explicite du type de `E` en type `T`, une erreur de compilation se produit. Pour plus d’informations sur la définition d’un opérateur de conversion, consultez les articles sur les mots clés [explicit](../keywords/explicit.md) et [implicit](../keywords/implicit.md).

L’exemple suivant illustre la conversion de type entre des types numériques :

[!code-csharp-interactive[use for cast](~/samples/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

Pour plus d’informations sur les conversions explicites prédéfinies entre des types numériques, consultez [Tableau des conversions numériques explicites](../keywords/explicit-numeric-conversions-table.md).

Pour plus d’informations, consultez [Cast et conversions de types](../../programming-guide/types/casting-and-type-conversions.md) et [Opérateurs de conversion](../../programming-guide/statements-expressions-operators/conversion-operators.md).

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

L’opérateur `()` ne peut pas être surchargé.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections [Expressions d’appel](~/_csharplang/spec/expressions.md#invocation-expressions) et [Expressions Cast](~/_csharplang/spec/expressions.md#cast-expressions) de la [spécification du langage C#](../language-specification/index.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Opérateurs C#](index.md)

---
title: Opérateurs d’égalité - Référence C#
description: En savoir plus sur les opérateurs de comparaison d’égalité C# et l’égalité de type C#.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 7dd3e544dc03fb94577892b42aecd1a15a6621ac
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110917"
---
# <a name="equality-operators-c-reference"></a>Opérateurs d’égalité (référence C#)

Les [ `==` opérateurs (d’égalité)](#equality-operator-) et [ `!=` (d’inégalité)](#inequality-operator-) vérifient si leurs opérands sont égaux ou non.

## <a name="equality-operator-"></a>Opérateur d’égalité ==

L’opérateur d’égalité `==` retourne `true` si ses opérandes sont égaux, `false` dans le cas contraire.

### <a name="value-types-equality"></a>Égalité de types valeur

Les opérandes des [types valeur intégrés](../builtin-types/value-types.md#built-in-value-types) sont égaux si leurs valeurs sont égales :

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Pour `==`le , [ `<`, , `>`, `<=`et `>=` ](comparison-operators.md) les opérateurs, si l’un des opérands n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`. Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`. Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

Deux opérandes du même type [enum](../builtin-types/enum.md) sont égaux si les valeurs correspondantes du type intégral sous-jacent sont égales.

Par défaut, les types [struct](../builtin-types/struct.md) définis par l’utilisateur ne prennent pas en charge l’opérateur `==`. Pour prendre en charge l’opérateur `==`, un struct défini par l’utilisateur doit le [surcharger](operator-overloading.md).

À compter de C# 7.3, les opérateurs `==` et `!=` sont pris en charge par les [tuples](../../tuples.md) C#. Pour plus d’informations, consultez la section [Égalité et tuples](../../tuples.md#equality-and-tuples) de l’article [Types de tuple C#](../../tuples.md).

### <a name="reference-types-equality"></a>Égalité de types référence

Par défaut, deux opérandes de type référence sont égaux s’ils font référence au même objet :

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Comme le montre l’exemple, les types référence définis par l’utilisateur prennent en charge l’opérateur `==` par défaut. Un type référence peut toutefois surcharger l’opérateur `==`. Si un type référence surcharge l’opérateur `==`, utilisez la méthode <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> pour vérifier si deux références de ce type font référence au même objet.

### <a name="string-equality"></a>Égalité de chaîne

Deux opérandes [string](../builtin-types/reference-types.md#the-string-type) sont égaux lorsque les deux sont `null` ou lorsque les deux instances de chaîne sont de même longueur et ont des caractères identiques dans chaque position de caractère :

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

Il s’agit d’une comparaison ordinaire sensible aux cas. Pour plus d’informations sur la comparaison de chaînes, consultez [Comment comparer des chaînes en C#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Égalité de délégué

Deux opérandes de [délégué](../../programming-guide/delegates/index.md) du même type de runtime sont égaux si les deux sont `null` ou si leurs listes d’appel sont de même longueur et ont des entrées égales dans chaque position :

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Pour plus d’informations, consultez la section [Opérateurs d’égalité de délégué](~/_csharplang/spec/expressions.md#delegate-equality-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

Les délégués qui sont produits à partir de l’évaluation d’[expressions lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) identiques sémantiquement ne sont pas égaux, comme l’indique l’exemple suivant :

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Opérateur d’inégalité !=

L’opérateur d’inégalité `!=` retourne `true` si ses opérandes ne sont pas égaux, `false` dans le cas contraire. Pour les opérandes des [types intégrés](../builtin-types/built-in-types.md), l’expression `x != y` produit le même résultat que l’expression `!(x == y)`. Pour plus d’informations sur l’égalité des types, consultez la section [Opérateur d’égalité](#equality-operator-).

L’exemple suivant illustre l’utilisation de l’opérateur `!=` :

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](operator-overloading.md) les opérateurs `==` et `!=`. Si un type surcharge l’un des deux opérateurs, il doit également surcharger l’autre.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Opérateurs CMD](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Comparaisons d’égalité](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Opérateurs de comparaison](comparison-operators.md)

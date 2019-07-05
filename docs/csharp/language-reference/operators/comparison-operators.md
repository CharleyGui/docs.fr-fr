---
title: Opérateurs de comparaison - Référence C#
description: Découvrez les opérateurs de comparaison C# que vous pouvez utiliser pour vérifier l’ordre des valeurs numériques.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 5b6668e20e4d69b7d6bdf3e6283574f1b974ef54
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423965"
---
# <a name="comparison-operators-c-reference"></a>Opérateurs de comparaison (référence C#)

Les opérateurs de comparaison, également appelés relationnels, [`<` (inférieur à)](#less-than-operator-), [`>` (supérieur à)](#greater-than-operator-), [`<=` (inférieur ou égal à)](#less-than-or-equal-operator-), et [ `>=` (supérieur ou égal à)](#greater-than-or-equal-operator-) comparent leurs opérandes. Ces opérateurs prennent en charge tous les types numériques [intégraux](../builtin-types/integral-numeric-types.md) et [à virgule flottante](../keywords/floating-point-types-table.md).

> [!NOTE]
> Pour les opérateurs `==`, `<`, `>`, `<=` et `>=`, si un des opérandes n’est pas un nombre (<xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>), le résultat de l’opération est `false`. Cela signifie que la valeur `NaN` n’est ni supérieure à, ni inférieure à, ni égale à n’importe quelle autre valeur `double` (ou `float`), y compris `NaN`. Pour plus d’informations et des exemples, consultez l’article de référence <xref:System.Double.NaN?displayProperty=nameWithType> ou <xref:System.Single.NaN?displayProperty=nameWithType>.

Les types d’énumération prennent également en charge les opérateurs de comparaison. Pour les opérandes du même type [enum](../keywords/enum.md), les valeurs correspondantes du type intégral sous-jacent sont comparées.

Les [opérateurs `==` et `!=`](equality-operators.md) vérifient si leurs opérandes sont égaux ou non.

## <a name="less-than-operator-"></a>Opérateur Inférieur à \<

L’opérateur `<` retourne `true` si son opérande de partie gauche est inférieur à son opérande de partie droite, `false` dans le cas contraire :

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Opérateur Supérieur à >

L’opérateur `>` retourne `true` si son opérande de partie gauche est supérieur à son opérande de partie droite, `false` dans le cas contraire :

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Opérateur Inférieur ou égal à \<=

L’opérateur `<=` retourne `true` si son opérande de partie gauche est inférieur ou égal à son opérande de partie droite, `false` dans le cas contraire :

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Opérateur Supérieur ou égal à >=

L’opérateur `>=` retourne `true` si son opérande de partie gauche est supérieur ou égal à son opérande de partie droite, `false` dans le cas contraire :

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Capacité de surcharge de l’opérateur

Un type défini par l’utilisateur peut [surcharger](../keywords/operator.md) les opérateurs `<`, `>`, `<=` et `>=`.

Si un type surcharge un des opérateurs `<` ou `>`, il doit surcharger à la fois `<` et `>`. Si un type surcharge un des opérateurs `<=` ou `>=`, il doit surcharger à la fois `<=` et `>=`.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Opérateurs relationnels et de test de type](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Opérateurs C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Opérateurs d’égalité](equality-operators.md)

---
title: Types valeur Nullable-référence C#
description: En savoir plus sur les types valeur Nullable C# et leur utilisation
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 8c3a8b997fbb8154f79dff04018cf3ea76f85d7a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537351"
---
# <a name="nullable-value-types-c-reference"></a>Types valeur Nullable (référence C#)

Un *type valeur Nullable* `T?` représente toutes les valeurs de son [type valeur](value-types.md) sous-jacent `T` et une valeur [null](../keywords/null.md) supplémentaire. Par exemple, vous pouvez assigner l’une des trois valeurs suivantes à une `bool?` variable : `true` , `false` ou `null` . Un type valeur sous-jacent `T` ne peut pas être un type valeur Nullable lui-même.

> [!NOTE]
> C# 8,0 introduit la fonctionnalité de types référence Nullable. Pour plus d’informations, consultez [types de référence Nullable](nullable-reference-types.md). Les types valeur Nullable sont disponibles à partir de C# 2.

Tout type valeur Nullable est une instance de la <xref:System.Nullable%601?displayProperty=nameWithType> structure générique. Vous pouvez faire référence à un type valeur Nullable avec un type sous-jacent `T` dans l’un des formulaires interchangeables suivants : `Nullable<T>` ou `T?` .

En général, vous utilisez un type valeur Nullable lorsque vous devez représenter la valeur indéfinie d’un type valeur sous-jacent. Par exemple, une variable booléenne, ou `bool` , ne peut être que `true` ou `false` . Toutefois, dans certaines applications, une valeur de variable peut être indéfinie ou manquante. Par exemple, un champ de base de données peut contenir `true` ou `false` , ou il ne peut contenir aucune valeur, autrement dit, `NULL` . Vous pouvez utiliser le `bool?` type dans ce scénario.

## <a name="declaration-and-assignment"></a>Déclaration et affectation

Comme un type valeur est implicitement convertible en type valeur Nullable correspondant, vous pouvez assigner une valeur à une variable d’un type valeur Nullable comme vous le feriez pour son type valeur sous-jacent. Vous pouvez également affecter la `null` valeur. Exemple :

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

La valeur par défaut d’un type valeur Nullable représente `null` , autrement dit, une instance dont la <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> propriété retourne `false` .

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Examen d’une instance d’un type valeur Nullable

À compter de C# 7,0, vous pouvez utiliser l' [ `is` opérateur avec un modèle de type](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) pour examiner à la fois une instance d’un type de valeur Nullable pour `null` et récupérer une valeur d’un type sous-jacent :

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Vous pouvez toujours utiliser les propriétés en lecture seule suivantes pour examiner et obtenir la valeur d’une variable de type valeur Nullable :

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indique si une instance d’un type valeur Nullable a une valeur de son type sous-jacent.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`. Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.

L’exemple suivant utilise la `HasValue` propriété pour déterminer si la variable contient une valeur avant de l’afficher :

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Vous pouvez également comparer une variable d’un type valeur Nullable avec `null` au lieu d’utiliser la `HasValue` propriété, comme le montre l’exemple suivant :

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversion d’un type valeur Nullable en un type sous-jacent

Si vous souhaitez assigner une valeur d’un type valeur Nullable à une variable de type valeur n’acceptant pas les valeurs NULL, vous devrez peut-être spécifier la valeur à assigner à la place de `null` . Utilisez l' [opérateur `??` de fusion Null](../operators/null-coalescing-operator.md) pour effectuer cette opération (vous pouvez également utiliser la <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> méthode dans le même but) :

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Si vous souhaitez utiliser la valeur [par défaut](default-values.md) du type valeur sous-jacent à la place de `null` , utilisez la <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> méthode.

Vous pouvez également effectuer un cast explicite d’un type valeur Nullable vers un type non Nullable, comme le montre l’exemple suivant :

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

Au moment de l’exécution, si la valeur d’un type valeur Nullable est `null` , le cast explicite lève une <xref:System.InvalidOperationException> .

Un type valeur n’acceptant pas les valeurs null `T` est implicitement convertible en type valeur Nullable correspondant `T?` .

## <a name="lifted-operators"></a>Opérateurs levés

Les [opérateurs](../operators/index.md) unaires et binaires prédéfinis ou tous les opérateurs surchargés pris en charge par un type valeur `T` sont également pris en charge par le type valeur Nullable correspondant `T?` . Ces opérateurs, également appelés *opérateurs levés*, produisent `null` si l’un des opérandes ou les deux sont `null` ; sinon, l’opérateur utilise les valeurs contenues de ses opérandes pour calculer le résultat. Exemple :

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Pour le `bool?` type, les opérateurs prédéfinis `&` et `|` ne suivent pas les règles décrites dans cette section : le résultat d’une évaluation d’opérateur peut être non null, même si l’un des opérandes est `null` . Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

Pour les [opérateurs de comparaison](../operators/comparison-operators.md) `<` , `>` , `<=` et `>=` , si l’un des opérandes ou les deux sont `null` , le résultat est `false` ; sinon, les valeurs contenues des opérandes sont comparées. Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`. L’exemple suivant montre que 10 n’est

- ni supérieur ou égal à `null`
- ni inférieur à `null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Pour l' [opérateur d’égalité](../operators/equality-operators.md#equality-operator-) `==` , si les deux opérandes sont `null` , le résultat est `true` , si un seul des opérandes est `null` , le résultat est `false` ; sinon, les valeurs contenues des opérandes sont comparées.

Pour l' [opérateur d’inégalité](../operators/equality-operators.md#inequality-operator-) `!=` , si les deux opérandes sont `null` , le résultat est `false` , si un seul des opérandes est `null` , le résultat est `true` ; sinon, les valeurs contenues des opérandes sont comparées.

S’il existe une [conversion définie par l’utilisateur](../operators/user-defined-conversion-operators.md) entre deux types valeur, la même conversion peut également être utilisée entre les types valeur Nullable correspondants.

## <a name="boxing-and-unboxing"></a>Boxing et unboxing

Une instance d’un type valeur Nullable `T?` est [convertie](../../programming-guide/types/boxing-and-unboxing.md) comme suit :

- Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.
- Si <xref:System.Nullable%601.HasValue%2A> retourne `true` , la valeur correspondante du type valeur sous-jacent `T` est boxed, et non l’instance de <xref:System.Nullable%601> .

Vous pouvez convertir une valeur boxed d’un type valeur `T` en type valeur Nullable correspondant `T?` , comme le montre l’exemple suivant :

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Comment identifier un type valeur Nullable

L’exemple suivant montre comment déterminer si une <xref:System.Type?displayProperty=nameWithType> instance représente un type valeur Nullable construit, autrement dit, le <xref:System.Nullable%601?displayProperty=nameWithType> type avec un paramètre de type spécifié `T` :

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Comme le montre l’exemple, vous utilisez l’opérateur [typeof](../operators/type-testing-and-cast.md#typeof-operator) pour créer une <xref:System.Type?displayProperty=nameWithType> instance.

Si vous souhaitez déterminer si une instance est d’un type valeur Nullable, n’utilisez pas la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode pour obtenir une <xref:System.Type> instance à tester avec le code précédent. Quand vous appelez la <xref:System.Object.GetType%2A?displayProperty=nameWithType> méthode sur une instance d’un type valeur Nullable, l’instance est [convertie](#boxing-and-unboxing) en <xref:System.Object> . La conversion boxing d’une instance non null d’un type valeur Nullable équivaut au boxing d’une valeur du type sous-jacent, <xref:System.Object.GetType%2A> retourne une <xref:System.Type> instance qui représente le type sous-jacent d’un type valeur Nullable :

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

En outre, n’utilisez pas l’opérateur [is](../operators/type-testing-and-cast.md#is-operator) pour déterminer si une instance est d’un type valeur Nullable. Comme le montre l’exemple suivant, vous ne pouvez pas distinguer les types d’une instance de type valeur Nullable et son instance de type sous-jacent avec l' `is` opérateur :

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type valeur Nullable :

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Les méthodes décrites dans cette section ne sont pas applicables dans le cas des [types référence Nullable](nullable-reference-types.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types Nullable](~/_csharplang/spec/types.md#nullable-types)
- [Opérateurs levés](~/_csharplang/spec/expressions.md#lifted-operators)
- [Conversions Nullable implicites](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Conversions Nullable explicites](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Opérateurs de conversion levés](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Que signifie réellement « lifted » ?](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Types références Nullables](nullable-reference-types.md)

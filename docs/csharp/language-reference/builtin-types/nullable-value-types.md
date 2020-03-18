---
title: Types de valeur nuls - Référence C
description: Renseignez-vous sur les types de valeur nulS de C et sur la façon de les utiliser
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: a84b3d60269491846b783e5046a84a1d14e258a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399587"
---
# <a name="nullable-value-types-c-reference"></a>Types de valeur nuls (référence C)

Un *type* `T?` de valeur in nullable représente toutes les valeurs de son type `T` de [valeur](value-types.md) sous-jacente et une valeur [nulle](../keywords/null.md) supplémentaire. Par exemple, vous pouvez attribuer l’une `bool?` des `true` `false`trois `null`valeurs suivantes à une variable : , , ou . Un type `T` de valeur sous-jacent ne peut pas être un type de valeur nul lui-même.

> [!NOTE]
> C 8.0 introduit la fonction de type de référence nul. Pour plus d’informations, voir [Les types de référence Nullable](../../nullable-references.md). Les types de valeur nulles sont disponibles à partir de C 2.

Tout type de valeur in nullable est un exemple de la structure générique. <xref:System.Nullable%601?displayProperty=nameWithType> Vous pouvez vous référer à un type `T` de valeur nul avec `Nullable<T>` un `T?`type sous-jacent dans l’un des formulaires interchangeables suivants : ou .

Vous utilisez généralement un type de valeur inquérable lorsque vous devez représenter la valeur indéfinie d’un type de valeur sous-jacent. Par exemple, un Boolean, ou `bool`, `true` `false`variable ne peut être soit ou . Toutefois, dans certaines applications, une valeur variable peut être indéfinie ou manquante. Par exemple, un champ `true` `false`de base de données peut contenir ou, ou il peut ne contenir aucune valeur du tout, c’est-à-dire, `NULL`. Vous pouvez `bool?` utiliser le type dans ce scénario.

## <a name="declaration-and-assignment"></a>Déclaration et affectation

Comme un type de valeur est implicitement convertible au type de valeur nullable correspondant, vous pouvez attribuer une valeur à une variable d’un type de valeur nul, comme vous le feriez pour son type de valeur sous-jacente. Vous pouvez également affecter la valeur `null`. Par exemple :

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

La valeur par défaut d’un type de valeur nul représente, `null`c’est-à-dire, c’est une instance dont <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> la propriété retourne `false`.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Examen d’un cas de type de valeur nul

En commençant par le C 7.0, vous pouvez utiliser [ `is` l’opérateur avec un](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) `null` modèle de type pour examiner à la fois une instance d’un type de valeur nul pour et récupérer une valeur d’un type sous-jacent :

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Vous pouvez toujours utiliser les propriétés suivantes pour examiner et obtenir une valeur d’une variable de type valeur nulle :

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>indique si un cas de type de valeur nulle a une valeur de son type sous-jacent.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`. Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.

L’exemple suivant `HasValue` utilise la propriété pour vérifier si la variable contient une valeur avant de l’afficher :

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Vous pouvez également comparer une variable d’un type de valeur nul avec `null` au lieu d’utiliser la `HasValue` propriété, comme le montre l’exemple suivant :

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversion d’un type de valeur in nullable à un type sous-jacent

Si vous souhaitez attribuer une valeur d’un type de valeur nul à une variable de type valeur `null`non annulable, vous devrez peut-être spécifier la valeur à attribuer à la place de . Utilisez [l’opérateur `??` de fusion nulle](../operators/null-coalescing-operator.md) pour le faire <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (vous pouvez également utiliser la méthode dans le même but):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Si vous souhaitez utiliser la valeur [par défaut](default-values.md) `null`du type <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> de valeur sous-jacente à la place de , utilisez la méthode.

Vous pouvez également lancer explicitement un type de valeur nul à un type non annulable, comme l’exemple suivant le montre :

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

Au moment de l’exécution, si la `null`valeur d’un <xref:System.InvalidOperationException>type de valeur nul est , le casting explicite jette un .

Un type `T` de valeur non annulable est implicitement `T?`convertible au type de valeur nullable correspondant .

## <a name="lifted-operators"></a>Opérateurs levés

Les opérateurs prédéfinis non classés et [binaires](../operators/index.md) ou tout `T` opérateur surchargé qui sont pris `T?`en charge par un type de valeur sont également pris en charge par le type de valeur nulle correspondant . Ces opérateurs, également connus sous `null` le nom `null` *d’opérateurs levés,* produisent si l’un ou les deux opérands sont ; autrement, l’opérateur utilise les valeurs contenues de ses opérandes pour calculer le résultat. Par exemple :

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Pour `bool?` le type, les `&` prédéfinis et `|` les opérateurs ne suivent pas les règles décrites dans cette section: le `null`résultat d’une évaluation de l’opérateur peut être non-null même si l’un des opérands est . Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

Pour [comparison operators](../operators/comparison-operators.md) `<`les opérateurs `>` `<=`de `>=`comparaison , , , et `null`, si `false`l’un ou les deux opérands sont , le résultat est; autrement, les valeurs contenues des opérandes sont comparées. Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`. L’exemple suivant montre que 10 n’est

- ni plus grand ni égal à`null`
- ni moins que`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Pour [l’opérateur](../operators/equality-operators.md#equality-operator-) `==`de l’égalité `null`, si `true`les deux opérandes sont `null`, le `false`résultat est , si un seul des opérands est , le résultat est; autrement, les valeurs contenues des opérandes sont comparées.

Pour [l’opérateur](../operators/equality-operators.md#inequality-operator-) `!=`d’inégalité , `null`si les `false`deux opérandes sont , `null`le résultat `true`est , si un seul des opérands est , le résultat est ; autrement, les valeurs contenues des opérandes sont comparées.

S’il existe une [conversion définie par l’utilisateur](../operators/user-defined-conversion-operators.md) entre deux types de valeurs, la même conversion peut également être utilisée entre les types de valeur nuls correspondants.

## <a name="boxing-and-unboxing"></a>Boxing et unboxing

Une instance d’un `T?` type de valeur nulle est [boxée](../../programming-guide/types/boxing-and-unboxing.md) comme suit :

- Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.
- Si <xref:System.Nullable%601.HasValue%2A> `true`les rendements , la `T` valeur correspondante du type <xref:System.Nullable%601>de valeur sous-jacente est en boîte, et non l’exemple de .

Vous pouvez déballer une valeur `T` en boîte d’un `T?`type de valeur au type de valeur nullable correspondant, comme le montre l’exemple suivant :

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Comment identifier un type de valeur nul

L’exemple suivant montre comment <xref:System.Type?displayProperty=nameWithType> déterminer si une instance représente un <xref:System.Nullable%601?displayProperty=nameWithType> type de valeur `T`nulle construit, c’est-à-dire le type avec un paramètre de type spécifié :

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Comme l’exemple le montre, vous utilisez <xref:System.Type?displayProperty=nameWithType> le [type d’opérateur](../operators/type-testing-and-cast.md#typeof-operator) pour créer une instance.

Si vous souhaitez déterminer si une instance est d’un type <xref:System.Object.GetType%2A?displayProperty=nameWithType> de valeur <xref:System.Type> nulle, n’utilisez pas la méthode pour obtenir une instance à tester avec le code précédent. Lorsque vous <xref:System.Object.GetType%2A?displayProperty=nameWithType> appelez la méthode sur une instance d’un type <xref:System.Object>de valeur nulle, l’instance est en [boîte](#boxing-and-unboxing) à . Comme la boxe d’un cas non nul d’un type de valeur <xref:System.Object.GetType%2A> nulle <xref:System.Type> équivaut à la boxe d’une valeur du type sous-jacent, renvoie une instance qui représente le type sous-jacent d’un type de valeur nul:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

En outre, ne pas utiliser [l’opérateur est](../operators/type-testing-and-cast.md#is-operator) pour déterminer si une instance est d’un type de valeur nulle. Comme l’indique l’exemple suivant, vous ne pouvez pas distinguer les `is` types d’instance de type valeur nul et son exemple de type sous-jacent avec l’opérateur :

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Vous pouvez utiliser le code présenté dans l’exemple suivant pour déterminer si une instance est d’un type de valeur nul :

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Les méthodes décrites dans cet article ne s’appliquent pas dans le cas des types de [référence nuls](../../nullable-references.md).

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types Nullable](~/_csharplang/spec/types.md#nullable-types)
- [Opérateurs levés](~/_csharplang/spec/expressions.md#lifted-operators)
- [Conversions implicites annulables](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Conversions annulées explicites](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Opérateurs de conversion levés](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Que signifie réellement « lifted » ?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Types références Nullables](../../nullable-references.md)

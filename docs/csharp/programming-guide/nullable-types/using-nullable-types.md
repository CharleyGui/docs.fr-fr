---
title: Utilisation des types valeur Nullable C# -Guide de programmation
ms.custom: seodec18
description: En savoir plus sur l' C# utilisation des types valeur Nullable
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396163"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>Utilisation des types valeur NullableC# (Guide de programmation)

Les types valeur Nullable sont des types qui représentent toutes les valeurs d’un type valeur sous-jacent `T`, et une valeur [null](../../language-reference/keywords/null.md) supplémentaire. Pour plus d’informations, consultez la rubrique [types valeur Nullable](index.md) .

> [!NOTE]
> C#8,0 introduit la fonctionnalité de types référence Nullable. Pour plus d’informations, consultez [types de référence Nullable](../../nullable-references.md). Les types valeur Nullable sont disponibles à partir C# de 2.

Vous pouvez faire référence à un type valeur Nullable dans l’un des formulaires interchangeables suivants : `Nullable<T>` ou `T?`. `T` doit être un type valeur.

## <a name="declaration-and-assignment"></a>Déclaration et affectation

Comme un type valeur peut être implicitement converti en type valeur Nullable correspondant, vous assignez une valeur à un type Nullable comme vous le feriez pour son type valeur sous-jacent. Vous pouvez également affecter la valeur `null`. Exemple :

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Examen d’une valeur de type Nullable

Utilisez les propriétés ReadOnly suivantes pour examiner une instance d’un type valeur Nullable pour null et pour récupérer une valeur d’un type sous-jacent :

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> indique si une instance d’un type Nullable a une valeur de son type sous-jacent.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> obtient la valeur d’un type sous-jacent si <xref:System.Nullable%601.HasValue%2A> est `true`. Si <xref:System.Nullable%601.HasValue%2A> est `false`, la propriété <xref:System.Nullable%601.Value%2A> lève une <xref:System.InvalidOperationException>.

Le code dans l’exemple suivant utilise la propriété `HasValue` pour tester si la variable contient une valeur avant de l’afficher :

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

Vous pouvez également comparer une variable d’un type valeur Nullable avec `null` au lieu d’utiliser la propriété `HasValue`, comme le montre l’exemple suivant :

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

À partir C# de 7,0, vous pouvez utiliser les [critères spéciaux](../../pattern-matching.md) pour examiner et obtenir une valeur d’un type valeur Nullable :

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Conversion d’un type valeur Nullable en un type sous-jacent

Si vous devez assigner une valeur d’un type valeur Nullable à un type non Nullable, utilisez l' [opérateur de fusion null `??`](../../language-reference/operators/null-coalescing-operator.md) pour spécifier la valeur à assigner si une valeur d’un type valeur Nullable est null (vous pouvez également utiliser la méthode <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType>) :

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> si la valeur à utiliser lorsqu’une valeur d’un type valeur Nullable est `null` doit être la valeur par défaut du type valeur sous-jacent.

Vous pouvez effectuer un cast explicite d’un type valeur Nullable en un type non Nullable. Exemple :

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

Au moment de l’exécution, si la valeur d’un type valeur Nullable est `null`, le cast explicite lève une <xref:System.InvalidOperationException>.

Un type valeur non Nullable est implicitement converti en type Nullable correspondant.

## <a name="operators"></a>Opérateurs

Les opérateurs unaires et binaires prédéfinis et tous les opérateurs définis par l’utilisateur qui existent pour les types valeur peuvent également être utilisés par les types Nullable correspondants. Ces opérateurs produisent `null` si un ou les deux opérandes sont `null` ; dans le cas contraire, l’opérateur utilise les valeurs contenues pour calculer le résultat. Exemple :

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Pour le type `bool?`, les opérateurs prédéfinis `&` et `|` ne suivent pas les règles décrites dans cette section : le résultat d’une évaluation d’opérateur peut être non null, même si l’un des opérandes est `null`. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../../language-reference/operators/boolean-logical-operators.md).
  
Pour les opérateurs relationnels (`<`, `>`, `<=`, `>=`), si l’un des opérandes ou les deux sont `null`, le résultat est `false`. Ne partez pas du principe que parce qu’une comparaison spécifique (par exemple `<=`) retourne `false`, la comparaison opposée (`>`) retourne `true`. L’exemple suivant montre que 10 n’est

- ni supérieur ou égal à `null`,
- ni inférieur à `null`.

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

L’exemple ci-dessus montre également qu’une comparaison d’égalité de deux types valeur Nullable à la fois null correspond à `true`.

Pour plus d’informations, voir la section [Opérateurs lifted](~/_csharplang/spec/expressions.md#lifted-operators) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Boxing et unboxing

Un type valeur Nullable est [boxed](../types/boxing-and-unboxing.md) d’après les règles suivantes :

- Si <xref:System.Nullable%601.HasValue%2A> retourne `false`, la référence null est générée.
- Si <xref:System.Nullable%601.HasValue%2A> retourne `true`, une valeur du type valeur sous-jacent `T` est boxed, pas l’instance de <xref:System.Nullable%601>.

Vous pouvez effectuer l’unboxing du type valeur boxed vers le type Nullable correspondant, comme le montre l’exemple suivant :

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Voir aussi

- [Types valeur Nullable](index.md)
- [Que signifie réellement « Lifted » ?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)

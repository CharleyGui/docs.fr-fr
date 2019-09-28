---
title: Types valeur Nullable- C# Guide de programmation
ms.custom: seodec18
description: En savoir C# plus sur les types valeur Nullable et leur utilisation
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396222"
---
# <a name="nullable-value-types-c-programming-guide"></a>Types valeur Nullable (C# Guide de programmation)

Les types valeur Nullable sont des instances de la structure <xref:System.Nullable%601?displayProperty=nameWithType>. Les types valeur Nullable peuvent représenter toutes les valeurs d’un type sous-jacent `T`, et une valeur [null](../../language-reference/keywords/null.md) supplémentaire. Le type sous-jacent `T` peut être n’importe quel [type valeur](../../language-reference/keywords/value-types.md) non nullable. `T` ne peut pas être un type référence.

> [!NOTE]
> C#8,0 introduit la fonctionnalité de types référence Nullable. Pour plus d’informations, consultez [types de référence Nullable](../../nullable-references.md). Les types valeur Nullable sont disponibles à partir C# de 2.

Par exemple, vous pouvez affecter `null` ou toute valeur entière à partir de <xref:System.Int32.MinValue?displayProperty=nameWithType> à <xref:System.Int32.MaxValue?displayProperty=nameWithType> à un `Nullable<int>` et [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) ou `null` à un `Nullable<bool>`.

Vous utilisez un type valeur Nullable lorsque vous devez représenter la valeur indéfinie d’un type sous-jacent. Une variable booléenne ne peut avoir que deux valeurs : `true` et `false`. Il n’existe aucune valeur « non définie ». Dans de nombreuses applications de programmation, notamment dans les interactions de base de données, une valeur de variable peut être indéfinie ou manquante. Par exemple, un champ dans une base de données peut contenir les valeurs true ou false, ou aucune valeur du tout. Vous utilisez un type `Nullable<bool>` dans ce cas.

Les types valeur Nullable présentent les caractéristiques suivantes :

- Les types valeur Nullable représentent des variables de type valeur auxquelles il est possible d’assigner la valeur `null`.

- La syntaxe `T?` est l’abréviation de `Nullable<T>`. Les deux formats sont interchangeables.

- Assignez une valeur à un type valeur Nullable comme vous le feriez pour un type valeur sous-jacent : `int? x = 10;` ou `double? d = 4.108;`. Vous pouvez également affecter la valeur `null` : `int? x = null;`.

- Utilisez les propriétés <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> et <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> en lecture seule pour rechercher les valeurs null et récupérer la valeur, comme indiqué dans l’exemple suivant : `if (x.HasValue) y = x.Value;`

  - La propriété <xref:System.Nullable%601.HasValue%2A> retourne `true` si la variable contient une valeur, ou `false` si elle est `null`.

  - La propriété <xref:System.Nullable%601.Value%2A> retourne une valeur si <xref:System.Nullable%601.HasValue%2A> retourne `true`. Sinon, une exception <xref:System.InvalidOperationException> est levée.

- Vous pouvez également utiliser les opérateurs `==` et `!=` avec un type valeur Nullable, comme indiqué dans l’exemple suivant : `if (x != null) y = x.Value;`. Si `a` et `b` sont tous les deux null, `a == b` prend la valeur `true`.

- À compter de C# 7.0, vous pouvez utiliser les [critères spéciaux](../../pattern-matching.md#the-is-type-pattern-expression) pour examiner et obtenir une valeur d’un type Nullable : `if (x is int valueOfX) y = valueOfX;`.

- La valeur par défaut de `T?` est une instance dont la propriété <xref:System.Nullable%601.HasValue%2A> retourne `false`.

- Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault> pour retourner la valeur affectée, ou la valeur [par défaut](../../language-reference/keywords/default-values-table.md) du type valeur sous-jacent si la valeur du type Nullable est `null`.

- Utilisez la méthode <xref:System.Nullable%601.GetValueOrDefault(%600)> pour retourner la valeur affectée, ou la valeur par défaut fournie si la valeur du type Nullable est `null`.

- Utilisez l' [opérateur de fusion Null](../../language-reference/operators/null-coalescing-operator.md), `??`, pour assigner une valeur à une variable d’un type valeur sous-jacent en fonction d’une valeur de type nullable : `int? x = null; int y = x ?? -1;`. Dans l’exemple, étant donné que `x` est `null`, la valeur de résultat de `y` est `-1`.

- Si une conversion définie par l’utilisateur est définie entre deux types valeur, la même conversion peut également être utilisée avec les types Nullable correspondants.

- Les types valeur Nullable imbriqués ne sont pas autorisés. Il n’est pas possible de compiler la ligne suivante : `Nullable<Nullable<int>> n;`

Pour plus d’informations, consultez les rubriques [utilisation des types valeur Nullable](using-nullable-types.md) et [Comment : identifier un type valeur Nullable](how-to-identify-a-nullable-type.md) .

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [?? Opérateur](../../language-reference/operators/null-coalescing-operator.md)
- [Types valeur Nullable (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>

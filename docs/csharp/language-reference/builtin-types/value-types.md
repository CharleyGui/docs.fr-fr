---
title: Types de valeur - Référence C
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399580"
---
# <a name="value-types-c-reference"></a>Types de valeur (référence C)

*Les types* de valeur et [les types de référence](../keywords/reference-types.md) sont les deux principales catégories de types de C. Une variable d’un type de valeur contient une instance du type. Cela diffère d’une variable d’un type de référence, qui contient une référence à une instance du type. Par défaut, en [affectation,](../operators/assignment-operator.md)en passant un argument à une méthode, et en retournant un résultat de méthode, les valeurs variables sont copiées. Dans le cas des variables de type valeur, les instances de type correspondant sont copiées. L’exemple suivant illustre ce comportement :

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

Comme l’exemple précédent l’indique, les opérations sur une variable de type valeur n’affectent que cette instance du type de valeur, stockée dans la variable.

Si un type de valeur contient un membre de données d’un type de référence, seule la référence à l’instance du type de référence est copiée lorsqu’une instance de type valeur est copiée. La copie et l’instance de type valeur originale ont accès à la même instance de type de référence. L’exemple suivant illustre ce comportement :

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Pour rendre votre code moins sujet aux erreurs et plus robuste, définissez et utilisez des types de valeur immuables. Cet article utilise des types de valeur mutables uniquement à des fins de démonstration.

## <a name="kinds-of-value-types"></a>Types de types de valeur

Un type de valeur peut être l’un des deux types suivants :

- un [type de structure](struct.md), qui encapsule les données et les fonctionnalités connexes
- un [type d’énumération](enum.md), qui est défini par un ensemble de constantes nommées et représente un choix ou une combinaison de choix

Un `T?` [type de valeur in nullable](nullable-value-types.md) `T` représente toutes les valeurs de son type de valeur sous-jacente et une valeur [nulle](../keywords/null.md) supplémentaire. Vous ne `null` pouvez pas attribuer à une variable d’un type de valeur, à moins qu’il ne s’agit d’un type de valeur nul.

## <a name="built-in-value-types"></a>Types de valeur intégrés

C fournit les types de valeur intégré suivants, également connus sous le nom *de types simples*:

- [Types numériques intégraux](integral-numeric-types.md)
- [Types numériques à virgule flottante](floating-point-numeric-types.md)
- [bool](bool.md) qui représente une valeur Boolean
- [char](char.md) qui représente un personnage Unicode UTF-16

Tous les types simples sont des types de structure et diffèrent des autres types de structure en ce qu’ils permettent certaines opérations supplémentaires:

- Vous pouvez utiliser des littérals pour fournir une valeur d’un type simple. Par exemple, `'A'` est un littéral de type `char`, tandis que `2001` est un littéral de type `int`.

- Vous pouvez déclarer des constantes des types simples avec le mot clé [const](../keywords/const.md). Il n’est pas possible d’avoir des constantes d’autres types de structures.

- Les expressions constantes, dont les opérands sont toutes des constantes des types simples, sont évaluées au moment de la compilation.

Commençant par C 7.0, C ' prend en charge [les tuples de valeur](../../tuples.md). Un tuple de valeur est un type de valeur, mais pas un type simple.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types de valeur](~/_csharplang/spec/types.md#value-types)
- [Types simples](~/_csharplang/spec/types.md#simple-types)
- [Variables](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Types référence](../keywords/reference-types.md)

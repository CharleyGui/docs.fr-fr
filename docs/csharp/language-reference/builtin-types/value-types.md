---
title: Types valeur- C# référence
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 76f4a3ed929e3ac8e3e6cc74158e75af7a6c8cf2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625945"
---
# <a name="value-types-c-reference"></a>Types valeur (C# référence)

Les types *valeur* et les [types référence](../keywords/reference-types.md) sont les deux catégories C# principales de types. Une variable d’un type valeur contient une instance du type. Cela diffère d’une variable d’un type référence, qui contient une référence à une instance du type. Par défaut, lors de l' [assignation](../operators/assignment-operator.md), en passant un argument à une méthode et en retournant un résultat de méthode, les valeurs des variables sont copiées. Dans le cas des variables de type valeur, les instances de type correspondantes sont copiées. L’exemple suivant illustre ce comportement :

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

Comme le montre l’exemple précédent, les opérations sur une variable de type valeur affectent uniquement cette instance du type valeur, stockée dans la variable.

Si un type valeur contient un membre de données d’un type référence, seule la référence à l’instance du type référence est copiée lorsqu’une instance de type valeur est copiée. La copie et l’instance de type valeur d’origine ont accès à la même instance de type référence. L’exemple suivant illustre ce comportement :

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> Pour que votre code soit moins sujet aux erreurs et plus robuste, définissez et utilisez des types de valeurs immuables. Cet article utilise des types de valeur mutable uniquement à des fins de démonstration.

## <a name="kinds-of-value-types"></a>Genres de types valeur

Un type valeur peut être l’un des deux types suivants :

- [type structure](struct.md), qui encapsule les données et les fonctionnalités associées
- [type énumération](enum.md), qui est défini par un ensemble de constantes nommées et qui représente un choix ou une combinaison de choix

Un [type valeur nullable](nullable-value-types.md) `T?` représente toutes les valeurs de son type valeur sous-jacent `T` et une valeur [null](../keywords/null.md) supplémentaire. Vous ne pouvez pas assigner `null` à une variable d’un type valeur, sauf s’il s’agit d’un type valeur Nullable.

## <a name="built-in-value-types"></a>Types valeur intégrés

C#fournit les types valeur intégrés suivants, également appelés *types simples*:

- [Types numériques intégraux](integral-numeric-types.md)
- [Types numériques à virgule flottante](floating-point-numeric-types.md)
- [booléen](bool.md) qui représente une valeur booléenne
- [char](char.md) qui représente un caractère Unicode UTF-16

Tous les types simples sont des types structure et diffèrent des autres types de structure en ce qu’ils autorisent certaines opérations supplémentaires :

- Vous pouvez utiliser des littéraux pour fournir une valeur d’un type simple. Par exemple, `'A'` est un littéral de type `char`, tandis que `2001` est un littéral de type `int`.

- Vous pouvez déclarer des constantes des types simples avec le mot clé [const](../keywords/const.md). Il n’est pas possible d’avoir des constantes d’autres types de structure.

- Les expressions constantes, dont les opérandes sont toutes des constantes des types simples, sont évaluées au moment de la compilation.

À partir C# de 7,0 C# , prend en charge les [tuples de valeur](../../tuples.md). Un tuple de valeur est un type valeur, mais pas un type simple.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez les sections suivantes de la [spécification du langage C#](~/_csharplang/spec/introduction.md) :

- [Types de valeur](~/_csharplang/spec/types.md#value-types)
- [Types simples](~/_csharplang/spec/types.md#simple-types)
- [Variables](~/_csharplang/spec/variables.md)

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [Types référence](../keywords/reference-types.md)

---
title: bool, type C# -référence
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 720ece2f7f47961e0ab6ebf03c8afeb5fa3a6271
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093264"
---
# <a name="bool-c-reference"></a>bool (C# référence)

Le mot clé `bool` type est un alias pour le type de structure .NET <xref:System.Boolean?displayProperty=nameWithType> qui représente une valeur booléenne, qui peut être `true` ou `false`.

Pour effectuer des opérations logiques avec des valeurs de type `bool`, utilisez des opérateurs [logiques booléens](../operators/boolean-logical-operators.md) . Le type de `bool` est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et d' [égalité](../operators/equality-operators.md) . Une expression `bool` peut être une expression conditionnelle de contrôle dans les instructions [If](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)et [for](../keywords/for.md) et dans l' [opérateur conditionnel `?:`](../operators/conditional-operator.md).

La valeur par défaut du type de `bool` est `false`.

## <a name="literals"></a>Littéraux

Vous pouvez utiliser les littéraux `true` et `false` pour initialiser une variable `bool` ou pour passer une valeur `bool` :

[!code-csharp-interactive[bool literals](~/samples/csharp/language-reference/builtin-types/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logique booléenne à trois valeurs

Utilisez le type de `bool?` Nullable, si vous avez besoin de prendre en charge la logique à trois valeurs, par exemple, lorsque vous utilisez des bases de données qui prennent en charge un type booléen à trois valeurs. Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

Pour plus d’informations sur les types valeur Nullable, consultez [types valeur Nullable](nullable-value-types.md).

## <a name="conversions"></a>Conversions

C#fournit uniquement deux conversions qui impliquent le type de `bool`. Il s’agit d’une conversion implicite vers le type de `bool?` Nullable correspondant et d’une conversion explicite du type de `bool?`. Toutefois, .NET fournit des méthodes supplémentaires que vous pouvez utiliser pour convertir vers ou à partir du type de `bool`. Pour plus d’informations, consultez la section [conversion de valeurs booléennes vers et à partir](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) de la page de référence des API <xref:System.Boolean?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [la section type bool](~/_csharplang/spec/types.md#the-bool-type) de la [ C# spécification du langage](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [Opérateurs true et false](../operators/true-false-operators.md)

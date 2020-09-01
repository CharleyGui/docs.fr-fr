---
description: 'En savoir plus sur le type booléen intégré en C #'
title: bool, type-référence C#
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
- "true"
- "false"
- true_CSharpKeyword
- false_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 23e5bc34f1751b0a706c20dae340920239fcda9d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126461"
---
# <a name="bool-c-reference"></a>bool (référence C#)

Le `bool` mot clé type est un alias pour le <xref:System.Boolean?displayProperty=nameWithType> type de structure .net qui représente une valeur booléenne, qui peut être `true` ou `false` .

Pour effectuer des opérations logiques avec des valeurs de `bool` type, utilisez des opérateurs [logiques booléens](../operators/boolean-logical-operators.md) . Le `bool` type est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et d' [égalité](../operators/equality-operators.md) . Une `bool` expression peut être une expression conditionnelle de contrôle dans les instructions [If](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md)et [for](../keywords/for.md) et dans l' [opérateur `?:` conditionnel ](../operators/conditional-operator.md).

La valeur par défaut du `bool` type est `false` .

## <a name="literals"></a>Littéraux

Vous pouvez utiliser les `true` `false` littéraux et pour initialiser une `bool` variable ou pour passer une `bool` valeur :

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logique booléenne à trois valeurs

Utilisez le `bool?` type Nullable, si vous avez besoin de prendre en charge la logique à trois valeurs, par exemple, lorsque vous utilisez des bases de données qui prennent en charge un type booléen à trois valeurs. Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

Pour plus d’informations sur les types valeur Nullable, consultez [types valeur Nullable](nullable-value-types.md).

## <a name="conversions"></a>Conversions

C# fournit uniquement deux conversions qui impliquent le `bool` type. Il s’agit d’une conversion implicite vers le type Nullable correspondant `bool?` et d’une conversion explicite du `bool?` type. Toutefois, .NET fournit des méthodes supplémentaires que vous pouvez utiliser pour convertir vers ou à partir du `bool` type. Pour plus d’informations, consultez la section [conversion de valeurs booléennes en et à partir](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) de la <xref:System.Boolean?displayProperty=nameWithType> page de référence des API.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez [la section type bool](~/_csharplang/spec/types.md#the-bool-type) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Types de valeur](value-types.md)
- [opérateurs true et false](../operators/true-false-operators.md)

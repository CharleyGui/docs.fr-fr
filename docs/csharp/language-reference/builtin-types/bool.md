---
title: type de seins - référence C
ms.date: 11/26/2019
f1_keywords:
- bool
- bool_CSharpKeyword
helpviewer_keywords:
- bool data type [C#]
- Boolean [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 2ba2e54a6b0f24402fc3728dfe19b548a2368830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846443"
---
# <a name="bool-c-reference"></a>bool (référence C)

Le `bool` mot clé de type <xref:System.Boolean?displayProperty=nameWithType> est un alias pour le type de `true` `false`structure .NET qui représente une valeur Boolean, qui peut être soit ou .

Pour effectuer des opérations `bool` logiques avec des valeurs du type, utilisez [boolean](../operators/boolean-logical-operators.md) opérateurs logiques. Le `bool` type est le type de résultat des opérateurs de [comparaison](../operators/comparison-operators.md) et [d’égalité.](../operators/equality-operators.md) Une `bool` expression peut être une expression conditionnelle de contrôle dans le [si,](../keywords/if-else.md) [faire](../keywords/do.md), [tandis que](../keywords/while.md), et [pour](../keywords/for.md) les déclarations et dans l’opérateur [ `?:`conditionnel ](../operators/conditional-operator.md).

La valeur par `bool` défaut `false`du type est .

## <a name="literals"></a>Littéraux

Vous pouvez `true` utiliser `false` les et les `bool` littérals pour `bool` initialiser une variable ou pour passer une valeur :

[!code-csharp-interactive[bool literals](snippets/BoolType.cs#Literals)]

## <a name="three-valued-boolean-logic"></a>Logique Boolean à trois valeur

Utilisez le `bool?` type infirmable, si vous devez prendre en charge la logique à trois valeur, par exemple, lorsque vous travaillez avec des bases de données qui prennent en charge un type Boolean de trois valeur. Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

Pour plus d’informations sur les types de valeur nulable, voir [les types de valeur nulable](nullable-value-types.md).

## <a name="conversions"></a>Conversions

C fournit seulement deux conversions `bool` qui impliquent le type. Il s’agit d’une `bool?` conversion implicite au type `bool?` nul correspondant et d’une conversion explicite du type. Cependant, .NET fournit des méthodes supplémentaires que vous `bool` pouvez utiliser pour convertir vers ou à partir du type. Pour plus d’informations, consultez la section [Convertir les valeurs de Boolean à](/dotnet/api/system.boolean#converting-to-and-from-boolean-values) partir de la page de référence de l’API. <xref:System.Boolean?displayProperty=nameWithType>

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, voir La section [du type bool](~/_csharplang/spec/types.md#the-bool-type) de la [spécification linguistique C](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Types de valeur](value-types.md)
- [opérateurs true et false](../operators/true-false-operators.md)

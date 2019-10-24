---
title: bool, mot clé - Référence C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 880e8c0b733afbf5c09f543e06a5a4a858d2b456
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771846"
---
# <a name="bool-c-reference"></a>bool (référence C#)

Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=nameWithType>. Il sert à déclarer des variables qui stockent les valeurs booléennes : [true](true-literal.md) et [false](false-literal.md).

> [!NOTE]
> Utilisez le type `bool?` si vous voulez suivre une logique à trois valeurs, par exemple pour travailler avec des bases de données qui acceptent un type booléen à trois valeurs. Dans le cas des opérandes `bool?`, les opérateurs prédéfinis `&` et `|` prennent en charge la logique à trois valeurs. Pour plus d’informations, voir la section [Opérateurs logiques booléens Nullable](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) de l’article [Opérateurs logiques booléens](../operators/boolean-logical-operators.md).

## <a name="literals"></a>Littéraux

Vous pouvez assigner une valeur booléenne à une variable `bool`. Vous pouvez également assigner à une variable `bool` une expression dont le résultat est une valeur `bool`.

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

La valeur par défaut d’une variable `bool` est `false`. La valeur par défaut d’une variable `bool?` est `null`.

## <a name="conversions"></a>Conversions

Dans C++, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d’autres termes, `false` équivaut à zéro et `true` équivaut à une valeur différente de zéro. Dans C#, il n’y a pas de conversion possible entre le type `bool` et les autres types. Par exemple, l’instruction `if` suivante n’est pas valide dans C# :

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur, telle que zéro, comme suit :

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>Exemple

Dans cet exemple, vous tapez un caractère, et le programme vérifie si le caractère entré est une lettre. Si c’est une lettre, le programme vérifie s’il s’agit d’une minuscule ou d’une majuscule. Ces vérifications sont effectuées avec les méthodes <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent toutes les deux le type `bool` :

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur C#](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Mots clés C#](./index.md)
- [Types intégraux](../builtin-types/integral-numeric-types.md)
- [Tableau des types intégrés](./built-in-types-table.md)

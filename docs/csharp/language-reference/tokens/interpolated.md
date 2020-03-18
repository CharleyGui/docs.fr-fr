---
title: $ - Interpolation des cordes - Référence C
description: L’interpolation de chaîne fournit une syntaxe plus lisible et plus pratique pour mettre en forme la sortie de chaîne que la traditionnelle mise en forme composite de chaîne.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980117"
---
# <a name="---string-interpolation-c-reference"></a>$ - interpolation des cordes (référence C)

Le caractère spécial `$` identifie un littéral de chaîne comme une *chaîne interpolée*. Une chaîne interpolée est un littéral de chaîne qui peut contenir des *expressions d’interpolation*. Quand une chaîne interpolée est résolue en une chaîne de résultat, les éléments avec des expressions d’interpolation sont remplacés par les représentations sous forme de chaîne des résultats des expressions. Cette fonctionnalité est disponible en commençant par le C 6.

L’interpolation de chaîne offre une syntaxe plus lisible et plus simple pour créer des chaînes mises en forme que la fonctionnalité de [mise en forme de chaîne composite](../../../standard/base-types/composite-formatting.md). L’exemple suivant utilise les deux fonctionnalités pour produire la même sortie :

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Structure d’une chaîne interpolée

Pour identifier un littéral de chaîne comme chaîne interpolée, préfixez-la du symbole `$`. N’ajoutez pas d’espace entre les signes `$` et `"` au début d’un littéral de chaîne.

La structure d’un élément avec une expression d’interpolation se présente comme suit :

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Les éléments entre crochets sont facultatifs. Le tableau suivant décrit chaque élément :

|Élément|Description|
|-------------|-----------------|
|`interpolationExpression`|Expression qui produit un résultat à mettre en forme. Représentation des `null` <xref:System.String.Empty?displayProperty=nameWithType>cordes de est .|
|`alignment`|L’expression constante dont la valeur définit le nombre minimum de caractères dans la représentation de chaîne du résultat d’expression. Si le nombre est positif, la représentation sous forme de chaîne est alignée à droite ; s’il est négatif, elle est alignée à gauche. Pour plus d'informations, consultez [Composant d’alignement](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Chaîne de format qui est prise en charge par le type de résultat de l’expression. Pour plus d'informations, consultez [Composant de chaîne de format](../../../standard/base-types/composite-formatting.md#format-string-component).|

L’exemple suivant utilise les composants de mise en forme facultatifs décrits ci-dessus :

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Caractères spéciaux

Pour ajouter une accolade, « { » ou « } », dans le texte produit par une chaîne interpolée, entrez deux accolades, « {{ » ou « }} ». Pour plus d'informations, consultez [Accolades d’échappement](../../../standard/base-types/composite-formatting.md#escaping-braces).

Comme le caractère deux-points (« : ») a une signification spéciale dans un élément d’expression d’interpolation, pour utiliser un [opérateur conditionnel](../operators/conditional-operator.md) dans une expression d’interpolation, placez cette expression entre parenthèses.

L’exemple suivant montre comment ajouter une accolade dans une chaîne de résultat et comment utiliser un opérateur conditionnel dans une expression d’interpolation :

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Une chaîne textuelle interpolée `$` commence par `@` le personnage suivi du personnage. Pour plus d’informations sur les chaînes textuelles, consultez les rubriques [string](../builtin-types/reference-types.md) et [Identificateur textuel](verbatim.md).

> [!NOTE]
> En commençant par C 8.0, `$` `@` vous pouvez utiliser les `$@"..."` jetons et les jetons dans n’importe quel ordre : les deux et `@$"..."` sont valides interpolés chaînes textuelles. Dans les versions précédentes de C, le `$` jeton doit apparaître devant le `@` jeton.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Conversions implicites et `IFormatProvider` comment spécifier la mise en œuvre

Trois conversions implicites sont possibles à partir d’une chaîne interpolée :

1. Conversion d’une chaîne interpolée en instance de <xref:System.String> qui est le résultat de la résolution d’une chaîne interpolée avec des éléments d’expression d’interpolation remplacés par la représentation sous forme de chaîne correctement mise en forme de leurs résultats. Cette conversion <xref:System.Globalization.CultureInfo.CurrentCulture> utilise les résultats d’expression de format.

1. Conversion d’une chaîne interpolée en instance <xref:System.FormattableString> qui représente une chaîne de format composite avec les résultats d’expression à mettre en forme. Cette conversion vous permet de créer plusieurs chaînes de résultat avec du contenu propre à la culture à partir d’une seule instance de <xref:System.FormattableString>. Pour ce faire, appelez l’une des méthodes suivantes :

      - Une surcharge <xref:System.FormattableString.ToString> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Une méthode <xref:System.FormattableString.Invariant%2A> qui produit une chaîne de résultat pour <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - Une méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> qui produit une chaîne de résultat pour une culture spécifiée.

    Vous pouvez également utiliser la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> pour fournir une implémentation définie par l’utilisateur de l’interface <xref:System.IFormatProvider> qui prend en charge une mise en forme personnalisée. Pour plus d’informations, voir le formatage personnalisé avec la section [ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) des [types de formatage dans l’article .NET.](../../../standard/base-types/formatting-types.md)

1. Conversion d’une chaîne interpolée en instance <xref:System.IFormattable> qui vous permet aussi de créer plusieurs chaînes de résultat avec du contenu propre à la culture à partir d’une seule instance de <xref:System.IFormattable>.

L’exemple suivant utilise la conversion implicite en <xref:System.FormattableString> pour créer des chaînes de résultat propres à la culture :

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Ressources supplémentaires

Si vous ne connaissez pas l’interpolation de chaînes, consultez le tutoriel interactif [Interpolation de chaînes en C#](../../tutorials/exploration/interpolated-strings.yml). Vous pouvez également consulter un autre tutoriel sur l’[interpolation de chaîne en C#](../../tutorials/string-interpolation.md) qui montre comment utiliser des chaînes interpolées pour produire des chaînes mises en forme.

## <a name="compilation-of-interpolated-strings"></a>Compilation de chaînes interpolées

Si une chaîne interpolée est de type `string`, elle est généralement transformée en un appel de méthode <xref:System.String.Format%2A?displayProperty=nameWithType>. Le compilateur peut remplacer <xref:System.String.Format%2A?displayProperty=nameWithType> par <xref:System.String.Concat%2A?displayProperty=nameWithType> si le comportement analysé équivaut à une concaténation.

Si une chaîne interpolée est de type <xref:System.IFormattable> ou <xref:System.FormattableString>, le compilateur génère un appel à la méthode <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>spécification du langage C#

Pour plus d’informations, consultez la section [Chaînes interpolées](~/_csharplang/spec/expressions.md#interpolated-strings) de la [spécification du langage C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Voir aussi

- [Référence C#](../index.md)
- [Caractères spéciaux C#](index.md)
- [Cordes](../../programming-guide/strings/index.md)
- [Chaînes de format numérique standard](../../../standard/base-types/standard-numeric-format-strings.md)
- [Formatage composite](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>

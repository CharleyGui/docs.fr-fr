---
title: Interpolation de chaîne en C#
description: Découvrez comment inclure des résultats d’expressions mises en forme dans une chaîne de résultat en C# avec une interpolation de chaîne.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039210"
---
# <a name="string-interpolation-in-c"></a>Interpolation de chaîne en C\#

Ce tutoriel vous montre comment utiliser une [interpolation de chaîne](../language-reference/tokens/interpolated.md) pour mettre en forme et inclure des résultats d’expressions dans une chaîne de résultat. Les exemples supposent que vous êtes familiarisé avec les concepts de base de C# et la mise en forme des types .NET. Si vous ne connaissez pas l’interpolation de chaînes ou la mise en forme de types .NET, consultez d’abord le [tutoriel interactif sur l’interpolation de chaînes](exploration/interpolated-strings.yml). Pour plus d’informations sur la mise en forme des types dans .NET, consultez la rubrique [Mise en forme des types dans .NET](../../standard/base-types/formatting-types.md).

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Introduction

La fonctionnalité [Interpolation de chaîne](../language-reference/tokens/interpolated.md) s’appuie sur la fonctionnalité [Mise en forme composite](../../standard/base-types/composite-formatting.md) et fournit une syntaxe plus lisible et plus pratique pour inclure des résultats d’expressions mises en forme dans une chaîne de résultat.

Pour identifier un littéral de chaîne comme chaîne interpolée, préfixez-la du symbole `$`. Vous pouvez incorporer n’importe quelle expression C# valide qui retourne une valeur dans une chaîne interpolée. Dans l’exemple suivant, dès qu’une expression est évaluée, son résultat est converti en chaîne et est inclus dans une chaîne de résultat :

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Comme le montre l’exemple, vous incluez une expression dans une chaîne interpolée en la plaçant entre des accolades :

```csharp
{<interpolationExpression>}
```

Les chaînes interpolées prennent en charge toutes les fonctions de la fonctionnalité [Mise en forme de chaîne composite](../../standard/base-types/composite-formatting.md). Elles constituent ainsi une alternative plus lisible à l’utilisation de la méthode <xref:System.String.Format%2A?displayProperty=nameWithType>.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Comment spécifier une chaîne de format pour une expression d’interpolation

Vous spécifiez une chaîne de format prise en charge par le type du résultat d’expression en plaçant un signe deux-points (« : ») et la chaîne de format après l’expression d’interpolation :

```csharp
{<interpolationExpression>:<formatString>}
```

L’exemple suivant montre comment spécifier des chaînes de format standard et personnalisées pour des expressions qui produisent des résultats de type date/heure ou numérique :

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Pour plus d’informations, consultez la section [Composant de chaîne de format](../../standard/base-types/composite-formatting.md#format-string-component) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md). Cette section fournit des liens vers les rubriques qui décrivent les chaînes de format standard et personnalisées prises en charge par les types de base .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Comment contrôler la largeur de champ et l’alignement de l’expression d’interpolation mise en forme

Vous spécifiez la largeur minimale du champ et l’alignement du résultat de l’expression mise en forme en plaçant une virgule (« , ») et l’expression constante après l’expression d’interpolation :

```csharp
{<interpolationExpression>,<alignment>}
```

Si la valeur de *l’alignement* est positive, le résultat de l’expression mise en forme est aligné à droite ; si la valeur est négative, il est aligné à gauche.

Si vous devez spécifier à la fois un alignement et une chaîne de format, commencez par le composant d’alignement :

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

L’exemple suivant montre comment spécifier l’alignement ; il utilise des caractères de barre verticale (« | ») pour délimiter les champs texte :

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Comme le montre l’exemple de sortie, si la longueur du résultat d’expression mise en forme dépasse la largeur de champ spécifiée, la valeur de *l’alignement* est ignorée.

Pour plus d’informations, consultez la section [Composant d’alignement](../../standard/base-types/composite-formatting.md#alignment-component) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md).

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Comment utiliser des séquences d’échappement dans une chaîne interpolée

Les chaînes interpolées prennent en charge toutes les séquences d’échappement qui peuvent être utilisés dans les littéraux de chaîne ordinaires. Pour plus d’informations, consultez [Séquences d’échappement de chaîne](../programming-guide/strings/index.md#string-escape-sequences).

Pour interpréter les séquences d’échappement littéralement, utilisez un littéral de chaîne [textuelle](../language-reference/tokens/verbatim.md). Une chaîne textuelle interpolée `$` commence par `@` le personnage suivi du personnage. En commençant par C 8.0, `$` `@` vous pouvez utiliser les `$@"..."` jetons et les jetons dans n’importe quel ordre : les deux et `@$"..."` sont valides interpolés chaînes textuelles.

Pour inclure une accolade, « { » ou «} », dans une chaîne de résultat, utilisez deux accolades, « {{ » ou «}} ». Pour plus d’informations, consultez la section [Échappement des accolades](../../standard/base-types/composite-formatting.md#escaping-braces) de la rubrique [Mise en forme composite](../../standard/base-types/composite-formatting.md).

L’exemple suivant montre comment inclure des accolades dans une chaîne de résultat et construire une chaîne interpolée textuelle :

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Comment utiliser un opérateur conditionnel ternaire `?:` dans une expression d’interpolation

Comme le caractère deux-points (« : ») a une signification spéciale dans un élément avec une expression d’interpolation, pour utiliser un [opérateur conditionnel](../language-reference/operators/conditional-operator.md) dans une expression, placez-la entre parenthèses, comme le montre l’exemple suivant :

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Comment créer une chaîne de résultat spécifique à une culture avec une interpolation de chaîne

Par défaut, une chaîne interpolée utilise la culture active définie par la propriété <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> pour toutes les opérations de mise en forme. Utilisez la conversion implicite d’une chaîne interpolée en une instance de <xref:System.FormattableString?displayProperty=nameWithType> et appelez sa méthode <xref:System.FormattableString.ToString(System.IFormatProvider)> pour créer une chaîne de résultat spécifique à une culture. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Comme le montre l’exemple, vous pouvez utiliser une même instance de <xref:System.FormattableString> pour générer plusieurs chaînes de résultat pour différentes cultures.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Comment créer une chaîne de résultat avec la culture invariante

Avec la méthode <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType>, vous pouvez utiliser la méthode statique <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> pour résoudre une chaîne interpolée en une chaîne de résultat pour <xref:System.Globalization.CultureInfo.InvariantCulture>. L’exemple suivant montre comment effectuer cette opération :

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Conclusion

Ce tutoriel décrit des scénarios courants d’utilisation de l’interpolation de chaîne. Pour plus d’informations sur l’interpolation de chaîne, consultez la rubrique [Interpolation de chaîne](../language-reference/tokens/interpolated.md). Pour plus d’informations sur la mise en forme des types dans .NET, consultez les rubriques [Mise en forme des types dans .NET](../../standard/base-types/formatting-types.md) et [Mise en forme composite](../../standard/base-types/composite-formatting.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Cordes](../programming-guide/strings/index.md)

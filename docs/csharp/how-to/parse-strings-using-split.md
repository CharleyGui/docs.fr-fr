---
title: Comment analyser des chaînes à l’aide de String. Split (Guide C#)
description: String.Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple pour analyser des chaînes.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662990"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>Comment analyser des chaînes à l’aide de String. Split en C\#

La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs. C’est souvent le moyen le plus simple pour séparer une chaîne sur des limites de mots. Elle sert également à fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné. Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné. Vous pouvez voir comment une chaîne vide est créée dans l’exemple suivant, qui utilise le caractère espace comme séparateur.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

Ce comportement facilite l’utilisation de formats tels que des fichiers de valeurs séparées par des virgules (CSV) représentant des données tabulaires. Les virgules consécutives représentent une colonne vide.

Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> facultatif pour exclure toutes les chaînes vides dans le tableau retourné. Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.

<xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.
L’exemple suivant utilise des caractères de séparation (espaces, virgules, points, deux-points et onglets) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.
La boucle en bas du code affiche chacun des mots dans le tableau retourné.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../programming-guide/index.md)
- [Chaînes](../programming-guide/strings/index.md)
- [Expressions régulières .NET](../../standard/base-types/regular-expressions.md)

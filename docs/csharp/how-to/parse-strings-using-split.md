---
title: Comment analyser les cordes à l’aide de String.Split (Guide C)
description: String.Split retourne un tableau de chaînes fractionnées à partir d’un ensemble de délimiteurs. Il s’agit d’un moyen simple pour analyser des chaînes.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: fb11ff59705188f9425beedfbbbf3c244d21f587
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121508"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Comment analyser les cordes à l’aide de String.Split (Guide C)

La méthode <xref:System.String.Split%2A?displayProperty=nameWithType> crée un tableau de sous-chaînes en fractionnant la chaîne d’entrée en fonction d’un ou plusieurs délimiteurs. C’est souvent le moyen le plus simple pour séparer une chaîne sur des limites de mots. Elle sert également à fractionner des chaînes sur d’autres caractères ou chaînes spécifiques.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Le code suivant fractionne une expression commune en un tableau de chaînes pour chaque mot.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Chaque instance d’un caractère de séparation génère une valeur dans le tableau retourné. Les caractères de séparation consécutifs produisent une chaîne vide comme valeur dans le tableau retourné.  Vous pouvez l’observer dans l’exemple suivant, qui utilise l’espace comme séparateur :

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Ce comportement facilite l’utilisation de formats tels que les fichiers CSV (valeurs séparées par des virgules) représentant des données tabulaires. Les virgules consécutives représentent une colonne vide.

Vous pouvez passer un paramètre <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> facultatif pour exclure toutes les chaînes vides dans le tableau retourné. Pour un traitement plus complexe de la collection retournée, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) pour manipuler la séquence de résultat.

<xref:System.String.Split%2A?displayProperty=nameWithType> peut utiliser plusieurs caractères de séparation.
L’exemple suivant utilise des caractères de séparation (espaces, virgules, points, deux-points et onglets) qui sont tous passés dans un tableau à <xref:System.String.Split%2A>.
La boucle en bas du code affiche chacun des mots dans le tableau retourné.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Les instances consécutives d’un séparateur produisent une chaîne vide dans le tableau de sortie :

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> peut accepter un tableau de chaînes (séquences de caractères, à la place de caractères uniques, qui agissent comme séparateurs lors de l’analyse de la chaîne cible).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Vous pouvez essayer ces échantillons en regardant le code dans notre [référentiel GitHub](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](../../../samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Voir aussi

- [Guide de programmation CMD](../programming-guide/index.md)
- [Chaînes](../programming-guide/strings/index.md)
- [Expressions régulières .NET](../../standard/base-types/regular-expressions.md)

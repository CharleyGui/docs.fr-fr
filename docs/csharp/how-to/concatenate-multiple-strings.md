---
title: Comment concaténer plusieurs chaînes (C# Guide)
description: Il existe plusieurs façons de concaténer des chaînes dans C#. Découvrez les options et les raisons de les choisir.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: 2e443030445d2817c8f53a044a261edd22eeb26e
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973272"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Comment concaténer plusieurs chaînes (C# Guide)

La *concaténation* consiste à ajouter une chaîne à la fin d’une autre chaîne. Vous concaténez les chaînes à l’aide de l’opérateur `+`. Pour les littéraux de chaîne et les constantes de chaîne, la concaténation se produit au moment de la compilation ; aucune concaténation ne se produit au moment de l’exécution. Pour les variables de chaîne, la concaténation se produit uniquement au moment de l’exécution.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

L’exemple suivant utilise la concaténation pour diviser un long littéral de chaîne en plus petites chaînes pour améliorer la lisibilité du code source. Les diverses parties sont concaténées en une chaîne unique lors de la compilation. Il n’y a aucune incidence sur les performances d’exécution, quel que soit le nombre de chaînes impliquées.  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

Pour concaténer des variables de chaîne, vous pouvez utiliser les opérateurs `+` ou `+=`, l’[interpolation de chaînes](../language-reference/tokens/interpolated.md), ou encore les méthodes <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>. L’opérateur `+` est facile à utiliser et convient au code intuitif. Même si vous utilisez plusieurs opérateurs `+` dans une instruction, le contenu de la chaîne est copié une seule fois. Le code suivant montre des exemples d’utilisation des opérateurs `+` et `+=` pour concaténer des chaînes :

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

Dans certaines expressions, il est plus facile de concaténer des chaînes à l’aide de l’interpolation de chaînes, comme le montre le code suivant :
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> Dans les opérations de concaténation de chaîne, le compilateur C# traite une chaîne null de la même manière qu’une chaîne vide.

Une autre méthode permettant de concaténer des chaînes est <xref:System.String.Format%2A?displayProperty=nameWithType>. Cette méthode fonctionne bien quand vous créez une chaîne à partir d’un petit nombre de chaînes de composant.

Dans d’autres cas, vous pouvez combiner des chaînes dans une boucle quand vous ne connaissez pas le nombre de chaînes sources que vous combinez et que le nombre réel de chaînes sources peut se révéler très grand. La classe <xref:System.Text.StringBuilder> a été conçue pour ces scénarios. Le code suivant utilise la méthode <xref:System.Text.StringBuilder.Append%2A> de la classe <xref:System.Text.StringBuilder> pour concaténer des chaînes.  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

Vous pouvez en savoir plus sur les [raisons de choisir la concaténation de chaînes ou la classe `StringBuilder`](xref:System.Text.StringBuilder#StringAndSB)

Une autre option permettant de joindre les chaînes d’une collection consiste à utiliser la méthode <xref:System.String.Concat%2A?displayProperty=nameWithType>. Utilisez la méthode <xref:System.String.Join%2A?displayProperty=nameWithType> si les chaînes sources doivent être séparées par un délimiteur. Le code suivant combine un tableau de mots en utilisant ces deux méthodes :

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

Enfin, vous pouvez utiliser [LINQ](../programming-guide/concepts/linq/index.md) et la méthode <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> pour joindre les chaînes d’une collection. Cette méthode combine les chaînes sources en utilisant une expression lambda. L’expression lambda effectue le travail d’ajouter chaque chaîne à l’accumulation existante. L’exemple suivant combine un tableau de mots en ajoutant un espace entre chaque mot du tableau :

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

Vous pouvez essayer ces exemples en examinant le code dans notre [dépôt GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Vous pouvez aussi télécharger les exemples [sous forme de fichier zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Voir aussi

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [Guide de programmation C#](../programming-guide/index.md)
- [Chaînes](../programming-guide/strings/index.md)

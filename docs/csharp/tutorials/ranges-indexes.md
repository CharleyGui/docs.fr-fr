---
title: Explorer les plages de données à l’aide d’index et de plages
description: Ce tutoriel avancé vous apprend à explorer les données à l’aide d’index et de plages pour examiner les tranches d’un jeu de données séquentiel.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 27f4b90f130345dd10517a5de78c759066afdf07
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926638"
---
# <a name="indices-and-ranges"></a>Index et plages

Les plages et les index fournissent une syntaxe concise pour accéder à des éléments uniques ou des plages dans un <xref:System.Array>, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>. Ces fonctionnalités permettent d’utiliser une syntaxe plus concise et claire pour accéder à des éléments uniques ou à des plages d’éléments dans une séquence.

Dans ce tutoriel, vous allez apprendre à :

> [!div class="checklist"]
>
> - Utiliser la syntaxe pour les plages dans une séquence.
> - Comprendre les décisions de conception pour le début et la fin de chaque séquence.
> - Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Prise en charge linguistique pour les index et les plages

Cette prise en charge linguistique s’appuie sur deux nouveaux types et deux nouveaux opérateurs.

- <xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.
- L’opérateur `^` spécifie qu’un index est relatif à la fin d’une séquence.
- <xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.
- L’opérateur de plage (`..`) spécifie le début et la fin d’une plage comme ses opérandes.

Commençons par les règles concernant les indices. Prenons pour exemple un tableau `sequence`. L’index `0` est identique à l’index `sequence[0]`. L’index `^0` est identique à l’index `sequence[sequence.Length]`. Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`. Pour n’importe quel nombre `n`, l’index `^n` est le même que l’index `sequence[sequence.Length - n]`.

```csharp-interactive
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Vous pouvez récupérer le dernier mot avec l’index `^1`. Ajoutez le code suivant sous l’initialisation :

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Une plage spécifie son *début* et sa *fin*. Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la plage. La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière. 

Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox » et va de `words[1]` à `words[3]`. L’élément `words[4]` n’est pas dans la plage. Ajoutez le code suivant à la même méthode. Copiez-le et collez-le en bas de la fenêtre interactive.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Le code suivant crée une sous-plage qui comporte « lazy » et « dog » et comprend `words[^2]` et `words[^1]`. L’index de fin `words[^0]` n’est pas inclus. Ajoutez également le code suivant :

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Vous pouvez également déclarer des plages ou index comme variables. La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

L’exemple suivant montre un grand nombre des raisons de ces choix. Modifiez `x`, `y` et `z` pour essayer différentes combinaisons. Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides. Ajoutez le code suivant à une nouvelle méthode. Essayez différentes combinaisons :

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénarios pour les index et les plages

L’utilisation de plages et d’index est fréquente pour effectuer une analyse sur une sous-plage d’une séquence entière. La nouvelle syntaxe permet de mieux lire la sous-plage exactement impliquée. La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument. La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne. Essayez le code suivant dans votre projet :

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Vous pouvez télécharger le code terminé à partir du dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).

---
title: Explorer les plages de données à l’aide d’index et de plages
description: Ce tutoriel avancé vous apprend à explorer les données à l’aide d’index et de plages pour examiner les tranches d’un jeu de données séquentiel.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156492"
---
# <a name="indices-and-ranges"></a>Index et plages

Les gammes et les indices fournissent une syntaxe succincte pour accéder à des éléments ou des plages uniques dans une séquence.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Utiliser la syntaxe pour les plages dans une séquence.
> - Comprendre les décisions de conception pour le début et la fin de chaque séquence.
> - Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Prise en charge linguistique pour les index et les plages

Ce support linguistique repose sur deux nouveaux types et deux nouveaux opérateurs :

- <xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.
- L’indice de `^`l’opérateur final , qui précise qu’un indice est relatif à la fin d’une séquence.
- <xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.
- L’opérateur `..`de gamme , qui spécifie le début et la fin d’une gamme comme ses opérands.

Commençons par les règles concernant les indices. Prenons pour exemple un tableau `sequence`. L’index `0` est identique à l’index `sequence[0]`. L’index `^0` est identique à l’index `sequence[sequence.Length]`. L’expression `sequence[^0]` ne jeter une `sequence[sequence.Length]` exception, tout comme le fait. Pour n’importe quel nombre `n`, l’index `^n` est identique à l’index `sequence[sequence.Length - n]`.

```csharp
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

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Une plage spécifie son *début* et sa *fin*. Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la gamme. La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.

Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox » et va de `words[1]` à `words[3]`. L’élément `words[4]` n’est pas dans la plage. Ajoutez le code suivant à la même méthode. Copiez-le et collez-le en bas de la fenêtre interactive.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Le code suivant crée une sous-plage qui comporte « lazy » et « dog » et comprend `words[^2]` et `words[^1]`. L’index de fin `words[^0]` n’est pas inclus. Ajoutez également le code suivant :

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Vous pouvez également déclarer des plages ou index comme variables. La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

L’exemple suivant montre un grand nombre des raisons de ces choix. Modifiez `x`, `y` et `z` pour essayer différentes combinaisons. Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides. Ajoutez le code suivant à une nouvelle méthode. Essayez différentes combinaisons :

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Type de support pour les indices et les plages

Les index et les plages fournissent une syntaxe claire et concise pour accéder à un seul élément ou à une sous-gamme d’éléments dans une séquence. Une expression d’index renvoie généralement le type des éléments d’une séquence. Une expression de plage renvoie généralement le même type de séquence que la séquence source.

Tout type qui fournit à <xref:System.Index> <xref:System.Range> un [indexeur](../programming-guide/indexers/index.md) un ou un paramètre prend explicitement en charge les indices ou les plages respectivement. Un indexeur qui <xref:System.Range> prend un seul paramètre peut <xref:System.Span%601?displayProperty=nameWithType>retourner un type de séquence différent, tel que .

Un type est **comptabilisable** `Length` s’il a une propriété nommée ou `Count` avec un getter accessible et un type de retour de `int`. Un type de comptage qui ne prend pas explicitement en charge les indices ou les plages peut leur fournir un support implicite. Pour plus d’informations, consultez les sections de support implicite de [l’indice](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) et de [la portée implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) de la note de proposition de [fonctionnalité](~/_csharplang/proposals/csharp-8.0/ranges.md). Les plages utilisant le support implicite de portée renvoient le même type de séquence que la séquence source.

Par exemple, les types .NET suivants prennent <xref:System.String> <xref:System.Span%601>en <xref:System.ReadOnlySpan%601>charge les indices et les gammes: , , et . Les <xref:System.Collections.Generic.List%601> indices prennent en charge les indices mais ne prennent pas en charge les plages.

<xref:System.Array>a un comportement plus nuancé. Les tableaux à dimension unique prennent en charge à la fois les indices et les gammes. Les tableaux multidimensionnels ne le font pas. L’indexeur d’un tableau multidimensionnel a plusieurs paramètres, pas un seul paramètre. Les tableaux déchiquetés, aussi appelés un éventail de tableaux, prennent en charge les gammes et les indexeurs. L’exemple suivant montre comment itérer une sous-section rectangulaire d’un tableau déchiqueté. Il itère la section dans le centre, à l’exclusion des trois premières et dernières rangées, et les deux premières et dernières colonnes de chaque rangée sélectionnée:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénarios pour indices et gammes

Vous utilisez souvent des plages et des indices lorsque vous souhaitez analyser une sous-gamme d’une séquence plus grande. La nouvelle syntaxe permet de mieux lire la sous-plage exactement impliquée. La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument. La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne. Essayez le code suivant dans votre projet :

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

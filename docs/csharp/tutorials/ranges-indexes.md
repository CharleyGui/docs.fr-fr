---
title: Explorer les plages de données à l’aide d’index et de plages
description: Ce didacticiel avancé vous apprend à explorer les données à l’aide d’index et de plages pour examiner une plage continue d’un jeu de données séquentiel.
ms.date: 09/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: cf6c83484332ed517b2326b3fd9d7458f191227e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "90738864"
---
# <a name="indices-and-ranges"></a>Index et plages

Les plages et les index fournissent une syntaxe concise pour accéder à des éléments ou des plages uniques dans une séquence.

Ce didacticiel vous montre comment effectuer les opérations suivantes :

> [!div class="checklist"]
>
> - Utiliser la syntaxe pour les plages dans une séquence.
> - Comprendre les décisions de conception pour le début et la fin de chaque séquence.
> - Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.

## <a name="language-support-for-indices-and-ranges"></a>Prise en charge linguistique pour les index et les plages

Cette prise en charge de langage s’appuie sur deux nouveaux types et deux nouveaux opérateurs :

- <xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.
- Index de l’opérateur End `^` , qui spécifie qu’un index est relatif à la fin d’une séquence.
- <xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.
- Opérateur de plage `..` , qui spécifie le début et la fin d’une plage comme opérandes.

Commençons par les règles concernant les indices. Prenons pour exemple un tableau `sequence`. L’index `0` est identique à l’index `sequence[0]`. L’index `^0` est identique à l’index `sequence[sequence.Length]`. L’expression `sequence[^0]` lève une exception, tout comme le `sequence[sequence.Length]` fait. Pour n’importe quel nombre `n`, l’index `^n` est identique à l’index `sequence[sequence.Length - n]`.

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

Une plage spécifie son *début* et sa *fin*. Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la plage. La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.

Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox » et va de `words[1]` à `words[3]`. L’élément `words[4]` n’est pas dans la plage. Ajoutez le code suivant à la même méthode. Copiez-le et collez-le en bas de la fenêtre interactive.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Le code suivant retourne la plage avec « Lazy » et « Dog ». et comprend `words[^2]` et `words[^1]`. L’index de fin `words[^0]` n’est pas inclus. Ajoutez également le code suivant :

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Vous pouvez également déclarer des plages ou index comme variables. La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

L’exemple suivant montre un grand nombre des raisons de ces choix. Modifiez `x`, `y` et `z` pour essayer différentes combinaisons. Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides. Ajoutez le code suivant à une nouvelle méthode. Essayez différentes combinaisons :

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Prise en charge des types d’index et de plages

Les index et les plages fournissent une syntaxe claire et concise permettant d’accéder à un élément unique ou à une plage d’éléments dans une séquence. Une expression d’index retourne généralement le type des éléments d’une séquence. Une expression de plage retourne généralement le même type de séquence que la séquence source.

Tout type qui fournit un [indexeur](../programming-guide/indexers/index.md) avec un <xref:System.Index> <xref:System.Range> paramètre ou prend explicitement en charge les index ou les plages respectivement. Un indexeur qui accepte un <xref:System.Range> paramètre unique peut retourner un type de séquence différent, tel que <xref:System.Span%601?displayProperty=nameWithType> .

> [!IMPORTANT]
> Les performances du code à l’aide de l’opérateur de plage dépendent du type de l’opérande de séquence.
>
> La complexité du temps de l’opérateur de plage dépend du type de séquence. Par exemple, si la séquence est un `string` tableau ou, le résultat est une copie de la section spécifiée de l’entrée, de sorte que la complexité de l’heure est *O (n)* (où n est la longueur de la plage). En revanche, s’il s’agit d’un <xref:System.Span%601?displayProperty=nameWithType> ou d’un <xref:System.Memory%601?displayProperty=nameWithType> , le résultat fait référence au même magasin de stockage, ce qui signifie qu’il n’y a pas de copie et que l’opération est *O (1)*.
>
> En plus de la complexité du temps, cela provoque des allocations et des copies supplémentaires, ce qui a un impact sur les performances. Dans le code dépendant des performances, envisagez d’utiliser `Span<T>` ou `Memory<T>` comme type de séquence, puisque l’opérateur de plage ne les alloue pas.

Un type est **compté** s’il a une propriété nommée `Length` ou `Count` avec un accesseur Get accessible et un type de retour `int` . Un type pouvant être compté qui ne prend pas explicitement en charge les index ou les plages peut fournir une prise en charge implicite pour eux. Pour plus d’informations, consultez les sections prise en charge d' [index implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) et [prise en charge de plage implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) de la [proposition](~/_csharplang/proposals/csharp-8.0/ranges.md). Les plages utilisant la prise en charge de plage implicite retournent le même type de séquence que la séquence source.

Par exemple, les types .NET suivants prennent en charge les index et les plages : <xref:System.String> , <xref:System.Span%601> et <xref:System.ReadOnlySpan%601> . Le <xref:System.Collections.Generic.List%601> prend en charge les index mais ne prend pas en charge les plages.

<xref:System.Array> a un comportement plus nuance. Les tableaux à une seule dimension prennent en charge les index et les plages. Les tableaux multidimensionnels ne le sont pas. L’indexeur d’un tableau multidimensionnel possède plusieurs paramètres, et non un seul paramètre. Les tableaux en escalier, également connus sous le terme de tableau de tableaux, prennent en charge les plages et les indexeurs. L’exemple suivant montre comment itérer une sous-section rectangulaire d’un tableau en escalier. Il itère la section au centre, en excluant les trois dernières lignes, et les deux dernières colonnes de chaque ligne sélectionnée :

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

Dans tous les cas, l’opérateur de plage pour <xref:System.Array> alloue un tableau pour stocker les éléments retournés.

## <a name="scenarios-for-indices-and-ranges"></a>Scénarios pour les index et les plages

Vous utiliserez souvent des plages et des index lorsque vous souhaitez analyser une partie d’une plus grande séquence. La nouvelle syntaxe est plus claire pour la lecture exacte de la partie de la séquence. La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument. La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne. Essayez le code suivant dans votre projet :

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

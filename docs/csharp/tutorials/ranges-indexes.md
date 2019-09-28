---
title: Explorer les plages de données à l’aide d’index et de plages
description: Ce tutoriel avancé vous apprend à explorer les données à l’aide d’index et de plages pour examiner les tranches d’un jeu de données séquentiel.
ms.date: 09/20/2019
ms.custom: mvc
ms.openlocfilehash: a879601e1358f72e80983992a3cd96ba1fb06a38
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71391968"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="b6cc3-103">Index et plages</span><span class="sxs-lookup"><span data-stu-id="b6cc3-103">Indices and ranges</span></span>

<span data-ttu-id="b6cc3-104">Les plages et les index fournissent une syntaxe concise pour accéder à des éléments ou des plages uniques dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="b6cc3-105">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="b6cc3-106">Utiliser la syntaxe pour les plages dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="b6cc3-107">Comprendre les décisions de conception pour le début et la fin de chaque séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="b6cc3-108">Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="b6cc3-109">Prise en charge linguistique pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="b6cc3-109">Language support for indices and ranges</span></span>

<span data-ttu-id="b6cc3-110">Cette prise en charge de langage s’appuie sur deux nouveaux types et deux nouveaux opérateurs :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="b6cc3-111"><xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="b6cc3-112">Index de l’opérateur `^`end, qui spécifie qu’un index est relatif à la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="b6cc3-113"><xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="b6cc3-114">Opérateur `..`de plage, qui spécifie le début et la fin d’une plage comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="b6cc3-115">Commençons par les règles concernant les indices.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="b6cc3-116">Prenons pour exemple un tableau `sequence`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-116">Consider an array `sequence`.</span></span> <span data-ttu-id="b6cc3-117">L’index `0` est identique à l’index `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="b6cc3-118">L’index `^0` est identique à l’index `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="b6cc3-119">Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="b6cc3-120">Pour n’importe quel nombre `n`, l’index `^n` est le même que l’index `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="b6cc3-121">Vous pouvez récupérer le dernier mot avec l’index `^1`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="b6cc3-122">Ajoutez le code suivant sous l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="b6cc3-123">Une plage spécifie son *début* et sa *fin*.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="b6cc3-124">Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la plage.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="b6cc3-125">La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="b6cc3-126">Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox »</span><span class="sxs-lookup"><span data-stu-id="b6cc3-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="b6cc3-127">et va de `words[1]` à `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="b6cc3-128">L’élément `words[4]` n’est pas dans la plage.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="b6cc3-129">Ajoutez le code suivant à la même méthode.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-129">Add the following code to the same method.</span></span> <span data-ttu-id="b6cc3-130">Copiez-le et collez-le en bas de la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="b6cc3-131">Le code suivant crée une sous-plage qui comporte « lazy » et « dog »</span><span class="sxs-lookup"><span data-stu-id="b6cc3-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="b6cc3-132">et comprend `words[^2]` et `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="b6cc3-133">L’index de fin `words[^0]` n’est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="b6cc3-134">Ajoutez également le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="b6cc3-135">Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="b6cc3-136">Vous pouvez également déclarer des plages ou index comme variables.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="b6cc3-137">La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="b6cc3-138">L’exemple suivant montre un grand nombre des raisons de ces choix.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="b6cc3-139">Modifiez `x`, `y` et `z` pour essayer différentes combinaisons.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="b6cc3-140">Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="b6cc3-141">Ajoutez le code suivant à une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-141">Add the following code in a new method.</span></span> <span data-ttu-id="b6cc3-142">Essayez différentes combinaisons :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="b6cc3-143">Prise en charge des types d’index et de plages</span><span class="sxs-lookup"><span data-stu-id="b6cc3-143">Type support for indices and ranges</span></span>

<span data-ttu-id="b6cc3-144">Si un type fournit un [indexeur](../programming-guide/indexers/index.md) avec un paramètre <xref:System.Index> ou <xref:System.Range>, il prend explicitement en charge les index ou les plages respectivement.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-144">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span>

<span data-ttu-id="b6cc3-145">Un type est **compté** s’il a une propriété nommée `Length` ou `Count` avec un accesseur Get accessible et un type de retour `int`.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-145">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="b6cc3-146">Un type pouvant être compté qui ne prend pas explicitement en charge les index ou les plages peut fournir une prise en charge implicite pour eux.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-146">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="b6cc3-147">Pour plus d’informations, consultez les sections prise en charge d' [index implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) et [prise en charge de plage implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) de la [proposition](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="b6cc3-147">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

<span data-ttu-id="b6cc3-148">Par exemple, les types .NET suivants prennent en charge les index et les plages : <xref:System.Array>, <xref:System.String>, <xref:System.Span%601> et <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-148">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="b6cc3-149">Le <xref:System.Collections.Generic.List%601> prend en charge les index, mais ne prend pas en charge les plages.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-149">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="b6cc3-150">Scénarios pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="b6cc3-150">Scenarios for indices and ranges</span></span>

<span data-ttu-id="b6cc3-151">L’utilisation de plages et d’index est fréquente pour effectuer une analyse sur une sous-plage d’une séquence entière.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-151">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="b6cc3-152">La nouvelle syntaxe permet de mieux lire la sous-plage exactement impliquée.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-152">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="b6cc3-153">La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-153">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="b6cc3-154">La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne.</span><span class="sxs-lookup"><span data-stu-id="b6cc3-154">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="b6cc3-155">Essayez le code suivant dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="b6cc3-155">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="b6cc3-156">Vous pouvez télécharger le code terminé à partir du dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).</span><span class="sxs-lookup"><span data-stu-id="b6cc3-156">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>

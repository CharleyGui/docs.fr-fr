---
title: Explorer les plages de données à l’aide d’index et de plages
description: Ce tutoriel avancé vous apprend à explorer les données à l’aide d’index et de plages pour examiner les tranches d’un jeu de données séquentiel.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 5b6277763cfccfc75947f6fa0534964389b1dea3
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240039"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="a57d1-103">Index et plages</span><span class="sxs-lookup"><span data-stu-id="a57d1-103">Indices and ranges</span></span>

<span data-ttu-id="a57d1-104">Les plages et les index fournissent une syntaxe concise pour accéder à des éléments ou des plages uniques dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="a57d1-105">Ce didacticiel vous montre comment effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a57d1-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="a57d1-106">Utiliser la syntaxe pour les plages dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="a57d1-107">Comprendre les décisions de conception pour le début et la fin de chaque séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="a57d1-108">Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="a57d1-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="a57d1-109">Prise en charge linguistique pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="a57d1-109">Language support for indices and ranges</span></span>

<span data-ttu-id="a57d1-110">Cette prise en charge de langage s’appuie sur deux nouveaux types et deux nouveaux opérateurs :</span><span class="sxs-lookup"><span data-stu-id="a57d1-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="a57d1-111"><xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="a57d1-112">L’index de l’opérateur end `^`, qui spécifie qu’un index est relatif à la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="a57d1-113"><xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="a57d1-114">L’opérateur de plage `..`, qui spécifie le début et la fin d’une plage comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="a57d1-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="a57d1-115">Commençons par les règles concernant les indices.</span><span class="sxs-lookup"><span data-stu-id="a57d1-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="a57d1-116">Prenons pour exemple un tableau `sequence`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-116">Consider an array `sequence`.</span></span> <span data-ttu-id="a57d1-117">L’index `0` est identique à l’index `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="a57d1-118">L’index `^0` est identique à l’index `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="a57d1-119">Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="a57d1-120">Pour n’importe quel nombre `n`, l’index `^n` est le même que l’index `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="a57d1-121">Vous pouvez récupérer le dernier mot avec l’index `^1`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="a57d1-122">Ajoutez le code suivant sous l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="a57d1-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="a57d1-123">Une plage spécifie son *début* et sa *fin*.</span><span class="sxs-lookup"><span data-stu-id="a57d1-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="a57d1-124">Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la plage.</span><span class="sxs-lookup"><span data-stu-id="a57d1-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="a57d1-125">La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.</span><span class="sxs-lookup"><span data-stu-id="a57d1-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="a57d1-126">Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox »</span><span class="sxs-lookup"><span data-stu-id="a57d1-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="a57d1-127">et va de `words[1]` à `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="a57d1-128">L’élément `words[4]` n’est pas dans la plage.</span><span class="sxs-lookup"><span data-stu-id="a57d1-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="a57d1-129">Ajoutez le code suivant à la même méthode.</span><span class="sxs-lookup"><span data-stu-id="a57d1-129">Add the following code to the same method.</span></span> <span data-ttu-id="a57d1-130">Copiez-le et collez-le en bas de la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="a57d1-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="a57d1-131">Le code suivant crée une sous-plage qui comporte « lazy » et « dog »</span><span class="sxs-lookup"><span data-stu-id="a57d1-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="a57d1-132">et comprend `words[^2]` et `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="a57d1-133">L’index de fin `words[^0]` n’est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="a57d1-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="a57d1-134">Ajoutez également le code suivant :</span><span class="sxs-lookup"><span data-stu-id="a57d1-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="a57d1-135">Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :</span><span class="sxs-lookup"><span data-stu-id="a57d1-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="a57d1-136">Vous pouvez également déclarer des plages ou index comme variables.</span><span class="sxs-lookup"><span data-stu-id="a57d1-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="a57d1-137">La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :</span><span class="sxs-lookup"><span data-stu-id="a57d1-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="a57d1-138">L’exemple suivant montre un grand nombre des raisons de ces choix.</span><span class="sxs-lookup"><span data-stu-id="a57d1-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="a57d1-139">Modifiez `x`, `y` et `z` pour essayer différentes combinaisons.</span><span class="sxs-lookup"><span data-stu-id="a57d1-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="a57d1-140">Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides.</span><span class="sxs-lookup"><span data-stu-id="a57d1-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="a57d1-141">Ajoutez le code suivant à une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="a57d1-141">Add the following code in a new method.</span></span> <span data-ttu-id="a57d1-142">Essayez différentes combinaisons :</span><span class="sxs-lookup"><span data-stu-id="a57d1-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="a57d1-143">Prise en charge des types d’index et de plages</span><span class="sxs-lookup"><span data-stu-id="a57d1-143">Type support for indices and ranges</span></span>

<span data-ttu-id="a57d1-144">Les index et les plages fournissent une syntaxe claire et concise permettant d’accéder à un élément unique ou à une sous-plage d’éléments dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-144">Indexes and ranges provide clear, concise syntax to access a single element or a sub-range of elements in a sequence.</span></span> <span data-ttu-id="a57d1-145">Une expression d’index retourne généralement le type des éléments d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="a57d1-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="a57d1-146">Une expression de plage retourne généralement le même type de séquence que la séquence source.</span><span class="sxs-lookup"><span data-stu-id="a57d1-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a57d1-147">Si un type fournit un [indexeur](../programming-guide/indexers/index.md) avec un paramètre <xref:System.Index> ou <xref:System.Range>, il prend explicitement en charge les index ou les plages, respectivement.</span><span class="sxs-lookup"><span data-stu-id="a57d1-147">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="a57d1-148">Lorsque le type fournit un indexeur qui accepte un seul paramètre <xref:System.Range>, il peut choisir de retourner un autre type de séquence, tel que <xref:System.Span%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a57d1-148">When the type provides an indexer that takes a single <xref:System.Range> parameter, it may choose to return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a57d1-149">Un type est **compté** s’il a une propriété nommée `Length` ou `Count` avec un accesseur Get accessible et un type de retour `int`.</span><span class="sxs-lookup"><span data-stu-id="a57d1-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="a57d1-150">Un type pouvant être compté qui ne prend pas explicitement en charge les index ou les plages peut fournir une prise en charge implicite pour eux.</span><span class="sxs-lookup"><span data-stu-id="a57d1-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="a57d1-151">Pour plus d’informations, consultez les sections prise en charge d' [index implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) et [prise en charge de plage implicite](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) de la [proposition](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="a57d1-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="a57d1-152">Les plages utilisant la prise en charge de plage implicite retournent le même type de séquence que la séquence source.</span><span class="sxs-lookup"><span data-stu-id="a57d1-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="a57d1-153">Par exemple, les types .NET suivants prennent en charge les index et les plages : <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>et <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="a57d1-153">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="a57d1-154">Le <xref:System.Collections.Generic.List%601> prend en charge les index mais ne prend pas en charge les plages.</span><span class="sxs-lookup"><span data-stu-id="a57d1-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="a57d1-155">Scénarios pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="a57d1-155">Scenarios for indices and ranges</span></span>

<span data-ttu-id="a57d1-156">L’utilisation de plages et d’index est fréquente pour effectuer une analyse sur une sous-plage d’une séquence entière.</span><span class="sxs-lookup"><span data-stu-id="a57d1-156">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="a57d1-157">La nouvelle syntaxe permet de mieux lire la sous-plage exactement impliquée.</span><span class="sxs-lookup"><span data-stu-id="a57d1-157">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="a57d1-158">La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument.</span><span class="sxs-lookup"><span data-stu-id="a57d1-158">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="a57d1-159">La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne.</span><span class="sxs-lookup"><span data-stu-id="a57d1-159">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="a57d1-160">Essayez le code suivant dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="a57d1-160">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="a57d1-161">Vous pouvez télécharger le code terminé à partir du dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).</span><span class="sxs-lookup"><span data-stu-id="a57d1-161">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>

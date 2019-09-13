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
# <a name="indices-and-ranges"></a><span data-ttu-id="9813b-103">Index et plages</span><span class="sxs-lookup"><span data-stu-id="9813b-103">Indices and ranges</span></span>

<span data-ttu-id="9813b-104">Les plages et les index fournissent une syntaxe concise pour accéder à des éléments uniques ou des plages dans un <xref:System.Array>, <xref:System.Span%601> ou <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="9813b-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="9813b-105">Ces fonctionnalités permettent d’utiliser une syntaxe plus concise et claire pour accéder à des éléments uniques ou à des plages d’éléments dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="9813b-106">Dans ce tutoriel, vous allez apprendre à :</span><span class="sxs-lookup"><span data-stu-id="9813b-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="9813b-107">Utiliser la syntaxe pour les plages dans une séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-107">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="9813b-108">Comprendre les décisions de conception pour le début et la fin de chaque séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-108">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="9813b-109">Découvrir des scénarios pour les types <xref:System.Index> et <xref:System.Range>.</span><span class="sxs-lookup"><span data-stu-id="9813b-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="9813b-110">Prise en charge linguistique pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="9813b-110">Language support for indices and ranges</span></span>

<span data-ttu-id="9813b-111">Cette prise en charge linguistique s’appuie sur deux nouveaux types et deux nouveaux opérateurs.</span><span class="sxs-lookup"><span data-stu-id="9813b-111">This language support relies on two new types and two new operators.</span></span>

- <span data-ttu-id="9813b-112"><xref:System.Index?displayProperty=nameWithType> représente un index au sein d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="9813b-113">L’opérateur `^` spécifie qu’un index est relatif à la fin d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="9813b-114"><xref:System.Range?displayProperty=nameWithType> représente une sous-plage d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="9813b-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="9813b-115">L’opérateur de plage (`..`) spécifie le début et la fin d’une plage comme ses opérandes.</span><span class="sxs-lookup"><span data-stu-id="9813b-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="9813b-116">Commençons par les règles concernant les indices.</span><span class="sxs-lookup"><span data-stu-id="9813b-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="9813b-117">Prenons pour exemple un tableau `sequence`.</span><span class="sxs-lookup"><span data-stu-id="9813b-117">Consider an array `sequence`.</span></span> <span data-ttu-id="9813b-118">L’index `0` est identique à l’index `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="9813b-119">L’index `^0` est identique à l’index `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="9813b-120">Notez que `sequence[^0]` lève une exception, tout comme `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="9813b-121">Pour n’importe quel nombre `n`, l’index `^n` est le même que l’index `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="9813b-122">Vous pouvez récupérer le dernier mot avec l’index `^1`.</span><span class="sxs-lookup"><span data-stu-id="9813b-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="9813b-123">Ajoutez le code suivant sous l’initialisation :</span><span class="sxs-lookup"><span data-stu-id="9813b-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="9813b-124">Une plage spécifie son *début* et sa *fin*.</span><span class="sxs-lookup"><span data-stu-id="9813b-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="9813b-125">Les plages sont exclusives, ce qui signifie que la *fin* n’est pas incluse dans la plage.</span><span class="sxs-lookup"><span data-stu-id="9813b-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="9813b-126">La plage `[0..^0]` représente la plage dans son intégralité, tout comme `[0..sequence.Length]` représente la plage entière.</span><span class="sxs-lookup"><span data-stu-id="9813b-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="9813b-127">Le code suivant crée une sous-plage qui comporte les mots « quick », « brown » et « fox »</span><span class="sxs-lookup"><span data-stu-id="9813b-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="9813b-128">et va de `words[1]` à `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="9813b-129">L’élément `words[4]` n’est pas dans la plage.</span><span class="sxs-lookup"><span data-stu-id="9813b-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="9813b-130">Ajoutez le code suivant à la même méthode.</span><span class="sxs-lookup"><span data-stu-id="9813b-130">Add the following code to the same method.</span></span> <span data-ttu-id="9813b-131">Copiez-le et collez-le en bas de la fenêtre interactive.</span><span class="sxs-lookup"><span data-stu-id="9813b-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="9813b-132">Le code suivant crée une sous-plage qui comporte « lazy » et « dog »</span><span class="sxs-lookup"><span data-stu-id="9813b-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="9813b-133">et comprend `words[^2]` et `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="9813b-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="9813b-134">L’index de fin `words[^0]` n’est pas inclus.</span><span class="sxs-lookup"><span data-stu-id="9813b-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="9813b-135">Ajoutez également le code suivant :</span><span class="sxs-lookup"><span data-stu-id="9813b-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="9813b-136">Les exemples suivants créent des plages ouvertes au début, à la fin ou les deux :</span><span class="sxs-lookup"><span data-stu-id="9813b-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="9813b-137">Vous pouvez également déclarer des plages ou index comme variables.</span><span class="sxs-lookup"><span data-stu-id="9813b-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="9813b-138">La variable peut ensuite être utilisée à l’intérieur des caractères `[` et `]` :</span><span class="sxs-lookup"><span data-stu-id="9813b-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="9813b-139">L’exemple suivant montre un grand nombre des raisons de ces choix.</span><span class="sxs-lookup"><span data-stu-id="9813b-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="9813b-140">Modifiez `x`, `y` et `z` pour essayer différentes combinaisons.</span><span class="sxs-lookup"><span data-stu-id="9813b-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="9813b-141">Quand vous effectuez des essais, utilisez des valeurs de telle sorte que `x` soit inférieur à `y` et `y` inférieur à `z` pour avoir des combinaisons valides.</span><span class="sxs-lookup"><span data-stu-id="9813b-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="9813b-142">Ajoutez le code suivant à une nouvelle méthode.</span><span class="sxs-lookup"><span data-stu-id="9813b-142">Add the following code in a new method.</span></span> <span data-ttu-id="9813b-143">Essayez différentes combinaisons :</span><span class="sxs-lookup"><span data-stu-id="9813b-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="9813b-144">Scénarios pour les index et les plages</span><span class="sxs-lookup"><span data-stu-id="9813b-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="9813b-145">L’utilisation de plages et d’index est fréquente pour effectuer une analyse sur une sous-plage d’une séquence entière.</span><span class="sxs-lookup"><span data-stu-id="9813b-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="9813b-146">La nouvelle syntaxe permet de mieux lire la sous-plage exactement impliquée.</span><span class="sxs-lookup"><span data-stu-id="9813b-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="9813b-147">La fonction locale `MovingAverage` prend un <xref:System.Range> comme argument.</span><span class="sxs-lookup"><span data-stu-id="9813b-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="9813b-148">La méthode énumère ensuite simplement cette plage lors du calcul des valeurs minimale, maximale et moyenne.</span><span class="sxs-lookup"><span data-stu-id="9813b-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="9813b-149">Essayez le code suivant dans votre projet :</span><span class="sxs-lookup"><span data-stu-id="9813b-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="9813b-150">Vous pouvez télécharger le code terminé à partir du dépôt GitHub [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes).</span><span class="sxs-lookup"><span data-stu-id="9813b-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>

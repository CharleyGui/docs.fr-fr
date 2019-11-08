---
title: Tranches (F#)
description: Découvrez comment utiliser des tranches pour les types F# de données existants et comment définir vos propres tranches pour d’autres types de données.
ms.date: 01/22/2019
ms.openlocfilehash: 2f7b87cda87aad1fdac05b4e14b16f454f8c0461
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733374"
---
# <a name="slices"></a><span data-ttu-id="16d15-103">Sections</span><span class="sxs-lookup"><span data-stu-id="16d15-103">Slices</span></span>

<span data-ttu-id="16d15-104">Dans F#, une tranche est un sous-ensemble d’un type de données.</span><span class="sxs-lookup"><span data-stu-id="16d15-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="16d15-105">Pour pouvoir prendre une tranche d’un type de données, le type de données doit définir une méthode `GetSlice` ou dans une [extension de type](type-extensions.md) qui se trouve dans l’étendue.</span><span class="sxs-lookup"><span data-stu-id="16d15-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="16d15-106">Cet article explique comment prendre des tranches de types F# existants et comment définir les vôtres.</span><span class="sxs-lookup"><span data-stu-id="16d15-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="16d15-107">Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="16d15-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="16d15-108">F#prend actuellement en charge la découpage des chaînes, des listes, des tableaux et des tableaux 2D.</span><span class="sxs-lookup"><span data-stu-id="16d15-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="16d15-109">Découpage de F# base avec des listes et des tableaux</span><span class="sxs-lookup"><span data-stu-id="16d15-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="16d15-110">Les types de données les plus courants qui sont découpés sont F# des listes et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="16d15-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="16d15-111">L’exemple suivant montre comment effectuer cette opération avec des listes :</span><span class="sxs-lookup"><span data-stu-id="16d15-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="16d15-112">Le découpage de tableaux se présente comme des listes de découpage :</span><span class="sxs-lookup"><span data-stu-id="16d15-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="16d15-113">Découpage de tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="16d15-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="16d15-114">F#prend en charge les tableaux multidimensionnels F# dans la bibliothèque principale.</span><span class="sxs-lookup"><span data-stu-id="16d15-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="16d15-115">Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles.</span><span class="sxs-lookup"><span data-stu-id="16d15-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="16d15-116">Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="16d15-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="16d15-117">Les exemples suivants montrent comment découper un tableau 2D :</span><span class="sxs-lookup"><span data-stu-id="16d15-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="16d15-118">La F# bibliothèque principale ne définit pas`GetSlice`pour les tableaux 3D.</span><span class="sxs-lookup"><span data-stu-id="16d15-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="16d15-119">Si vous souhaitez découper ces tableaux ou d’autres dimensions, vous devez définir le `GetSlice` membre vous-même.</span><span class="sxs-lookup"><span data-stu-id="16d15-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="16d15-120">Définition de tranches pour d’autres structures de données</span><span class="sxs-lookup"><span data-stu-id="16d15-120">Defining slices for other data structures</span></span>

<span data-ttu-id="16d15-121">La F# bibliothèque principale définit des tranches pour un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="16d15-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="16d15-122">Si vous souhaitez définir des tranches pour davantage de types de données, vous pouvez le faire soit dans la définition de type elle-même, soit dans une extension de type.</span><span class="sxs-lookup"><span data-stu-id="16d15-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="16d15-123">Par exemple, voici comment vous pouvez définir des secteurs pour la classe <xref:System.ArraySegment%601> pour permettre une manipulation pratique des données :</span><span class="sxs-lookup"><span data-stu-id="16d15-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="16d15-124">Utilisez l’incorporation pour éviter le boxing si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="16d15-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="16d15-125">Si vous définissez des tranches pour un type qui est en fait un struct, nous vous recommandons de `inline` le membre `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="16d15-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="16d15-126">Le F# compilateur optimise les arguments facultatifs, évitant ainsi toute allocation de tas résultant du découpage.</span><span class="sxs-lookup"><span data-stu-id="16d15-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="16d15-127">Cela est essentiel pour les constructions de découpage telles que les <xref:System.Span%601> qui ne peuvent pas être allouées sur le tas.</span><span class="sxs-lookup"><span data-stu-id="16d15-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a><span data-ttu-id="16d15-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16d15-128">See also</span></span>

- [<span data-ttu-id="16d15-129">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="16d15-129">Indexed properties</span></span>](./members/indexed-properties.md)

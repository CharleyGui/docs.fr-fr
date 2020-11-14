---
title: Sections
description: 'Découvrez comment utiliser des tranches pour les types de données F # existants et comment définir vos propres tranches pour d’autres types de données.'
ms.date: 12/23/2019
ms.openlocfilehash: a3920ad9e1b205b506aaee92c4606bcebf94feba
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557075"
---
# <a name="slices"></a><span data-ttu-id="2db54-103">Sections</span><span class="sxs-lookup"><span data-stu-id="2db54-103">Slices</span></span>

<span data-ttu-id="2db54-104">En F #, une tranche est un sous-ensemble de tout type de données qui a une `GetSlice` méthode dans sa définition ou dans une [extension de type](type-extensions.md)dans la portée.</span><span class="sxs-lookup"><span data-stu-id="2db54-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="2db54-105">Il est le plus couramment utilisé avec les tableaux et les listes F #.</span><span class="sxs-lookup"><span data-stu-id="2db54-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="2db54-106">Cet article explique comment prendre des tranches à partir de types F # existants et comment définir vos propres tranches.</span><span class="sxs-lookup"><span data-stu-id="2db54-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="2db54-107">Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="2db54-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="2db54-108">F # a actuellement une prise en charge intrinsèque pour le découpage des chaînes, des listes, des tableaux et des tableaux 2D.</span><span class="sxs-lookup"><span data-stu-id="2db54-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="2db54-109">Découpage de base avec des listes et des tableaux F #</span><span class="sxs-lookup"><span data-stu-id="2db54-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="2db54-110">Les types de données les plus courants qui sont découpés sont des listes et des tableaux F #.</span><span class="sxs-lookup"><span data-stu-id="2db54-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="2db54-111">L’exemple suivant montre comment effectuer cette opération avec des listes :</span><span class="sxs-lookup"><span data-stu-id="2db54-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="2db54-112">Le découpage de tableaux se présente comme des listes de découpage :</span><span class="sxs-lookup"><span data-stu-id="2db54-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="2db54-113">Découpage de tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="2db54-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="2db54-114">F # prend en charge les tableaux multidimensionnels dans la bibliothèque principale F #.</span><span class="sxs-lookup"><span data-stu-id="2db54-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="2db54-115">Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles.</span><span class="sxs-lookup"><span data-stu-id="2db54-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="2db54-116">Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="2db54-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="2db54-117">Les exemples suivants montrent comment découper un tableau 2D :</span><span class="sxs-lookup"><span data-stu-id="2db54-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="2db54-118">Actuellement, la bibliothèque principale F # n’est pas définie `GetSlice` pour les tableaux 3D.</span><span class="sxs-lookup"><span data-stu-id="2db54-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="2db54-119">Si vous souhaitez découper des tableaux 3D ou d’autres tableaux de dimensions supplémentaires, définissez le `GetSlice` membre vous-même.</span><span class="sxs-lookup"><span data-stu-id="2db54-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="2db54-120">Définition de tranches pour d’autres structures de données</span><span class="sxs-lookup"><span data-stu-id="2db54-120">Defining slices for other data structures</span></span>

<span data-ttu-id="2db54-121">La bibliothèque principale F # définit des tranches pour un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="2db54-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="2db54-122">Si vous souhaitez définir des tranches pour davantage de types de données, vous pouvez le faire soit dans la définition de type elle-même, soit dans une extension de type.</span><span class="sxs-lookup"><span data-stu-id="2db54-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="2db54-123">Par exemple, voici comment vous pouvez définir des secteurs pour la <xref:System.ArraySegment%601> classe afin de faciliter la manipulation de données :</span><span class="sxs-lookup"><span data-stu-id="2db54-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="2db54-124">Autre exemple utilisant les <xref:System.Span%601> <xref:System.ReadOnlySpan%601> types et :</span><span class="sxs-lookup"><span data-stu-id="2db54-124">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
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
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="2db54-125">Les tranches F # intégrées sont finales</span><span class="sxs-lookup"><span data-stu-id="2db54-125">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="2db54-126">Toutes les tranches intrinsèques en F # sont de fin inclusive ; autrement dit, la limite supérieure est incluse dans la tranche.</span><span class="sxs-lookup"><span data-stu-id="2db54-126">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="2db54-127">Pour une tranche donnée avec un index de départ `x` et un index de fin `y` , la tranche résultante inclut la valeur *YTH* .</span><span class="sxs-lookup"><span data-stu-id="2db54-127">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="2db54-128">Tranches vides F # intégrées</span><span class="sxs-lookup"><span data-stu-id="2db54-128">Built-in F# empty slices</span></span>

<span data-ttu-id="2db54-129">Les listes, les tableaux, les séquences, les chaînes, les tableaux 2D, les tableaux 3D et les tableaux 4D de F # produisent tous une tranche vide si la syntaxe peut produire une tranche qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="2db54-129">F# lists, arrays, sequences, strings, 2D arrays, 3D arrays, and 4D arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="2db54-130">Tenez compte des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2db54-130">Consider the following:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

<span data-ttu-id="2db54-131">Les développeurs C# peuvent s’attendre à ce qu’ils lèvent une exception au lieu de produire une tranche vide.</span><span class="sxs-lookup"><span data-stu-id="2db54-131">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="2db54-132">Il s’agit d’une décision de conception enracinée dans le fait que les collections vides composent en F #.</span><span class="sxs-lookup"><span data-stu-id="2db54-132">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="2db54-133">Une liste F # vide peut être composée d’une autre liste F #, une chaîne vide peut être ajoutée à une chaîne existante, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="2db54-133">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="2db54-134">Il peut être courant de prendre des tranches basées sur des valeurs transmises en tant que paramètres, et d’être tolérantes aux hors limites en produisant une collection vide qui respecte la nature compositionnelle du code F #.</span><span class="sxs-lookup"><span data-stu-id="2db54-134">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="2db54-135">Tranches à index fixe pour les tableaux 3D et 4D</span><span class="sxs-lookup"><span data-stu-id="2db54-135">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="2db54-136">Pour les tableaux F # 3D et 4D, vous pouvez « corriger » un index particulier et découper les autres dimensions avec cet index fixe.</span><span class="sxs-lookup"><span data-stu-id="2db54-136">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="2db54-137">Pour illustrer cela, examinez le tableau 3D suivant :</span><span class="sxs-lookup"><span data-stu-id="2db54-137">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="2db54-138">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="2db54-138">*z = 0*</span></span>
| <span data-ttu-id="2db54-139">x\y</span><span class="sxs-lookup"><span data-stu-id="2db54-139">x\y</span></span>   | <span data-ttu-id="2db54-140">0</span><span class="sxs-lookup"><span data-stu-id="2db54-140">0</span></span> | <span data-ttu-id="2db54-141">1</span><span class="sxs-lookup"><span data-stu-id="2db54-141">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2db54-142">**0**</span><span class="sxs-lookup"><span data-stu-id="2db54-142">**0**</span></span> | <span data-ttu-id="2db54-143">0</span><span class="sxs-lookup"><span data-stu-id="2db54-143">0</span></span> | <span data-ttu-id="2db54-144">1</span><span class="sxs-lookup"><span data-stu-id="2db54-144">1</span></span> |
| <span data-ttu-id="2db54-145">**1**</span><span class="sxs-lookup"><span data-stu-id="2db54-145">**1**</span></span> | <span data-ttu-id="2db54-146">2</span><span class="sxs-lookup"><span data-stu-id="2db54-146">2</span></span> | <span data-ttu-id="2db54-147">3</span><span class="sxs-lookup"><span data-stu-id="2db54-147">3</span></span> |

<span data-ttu-id="2db54-148">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="2db54-148">*z = 1*</span></span>
| <span data-ttu-id="2db54-149">x\y</span><span class="sxs-lookup"><span data-stu-id="2db54-149">x\y</span></span>   | <span data-ttu-id="2db54-150">0</span><span class="sxs-lookup"><span data-stu-id="2db54-150">0</span></span> | <span data-ttu-id="2db54-151">1</span><span class="sxs-lookup"><span data-stu-id="2db54-151">1</span></span> |
|-------|---|---|
| <span data-ttu-id="2db54-152">**0**</span><span class="sxs-lookup"><span data-stu-id="2db54-152">**0**</span></span> | <span data-ttu-id="2db54-153">4</span><span class="sxs-lookup"><span data-stu-id="2db54-153">4</span></span> | <span data-ttu-id="2db54-154">5</span><span class="sxs-lookup"><span data-stu-id="2db54-154">5</span></span> |
| <span data-ttu-id="2db54-155">**1**</span><span class="sxs-lookup"><span data-stu-id="2db54-155">**1**</span></span> | <span data-ttu-id="2db54-156">6</span><span class="sxs-lookup"><span data-stu-id="2db54-156">6</span></span> | <span data-ttu-id="2db54-157">7</span><span class="sxs-lookup"><span data-stu-id="2db54-157">7</span></span> |

<span data-ttu-id="2db54-158">Si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau, utilisez une tranche à index fixe.</span><span class="sxs-lookup"><span data-stu-id="2db54-158">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

```fsharp
let dim = 2
let m = Array3D.zeroCreate<int> dim dim dim

let mutable count = 0

for z in 0..dim-1 do
    for y in 0..dim-1 do
        for x in 0..dim-1 do
            m.[x,y,z] <- count
            count <- count + 1

// Now let's get the [4;5] slice!
m.[*, 0, 1]
```

<span data-ttu-id="2db54-159">La dernière ligne corrige les `y` `z` indices et du tableau 3D et prend le reste des `x` valeurs qui correspondent à la matrice.</span><span class="sxs-lookup"><span data-stu-id="2db54-159">The last line fixes the `y` and `z` indicies of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="2db54-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2db54-160">See also</span></span>

- [<span data-ttu-id="2db54-161">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="2db54-161">Indexed properties</span></span>](./members/indexed-properties.md)

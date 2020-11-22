---
title: Sections
description: 'Découvrez comment utiliser des tranches pour les types de données F # existants et comment définir vos propres tranches pour d’autres types de données.'
ms.date: 11/20/2020
ms.openlocfilehash: 9c072648ed46ae29871f2be5cc64b493f6a9b857
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95098955"
---
# <a name="slices"></a><span data-ttu-id="8477b-103">Sections</span><span class="sxs-lookup"><span data-stu-id="8477b-103">Slices</span></span>

<span data-ttu-id="8477b-104">Cet article explique comment prendre des tranches à partir de types F # existants et comment définir vos propres tranches.</span><span class="sxs-lookup"><span data-stu-id="8477b-104">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="8477b-105">En F #, une tranche est un sous-ensemble de n’importe quel type de données.</span><span class="sxs-lookup"><span data-stu-id="8477b-105">In F#, a slice is a subset of any data type.</span></span>  <span data-ttu-id="8477b-106">Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="8477b-106">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span> <span data-ttu-id="8477b-107">Les tranches utilisent la `..` syntaxe d’opérateur pour sélectionner la plage d’index spécifiée dans un type de données.</span><span class="sxs-lookup"><span data-stu-id="8477b-107">Slices use the `..` operator syntax to select the range of specified indices in a data type.</span></span> <span data-ttu-id="8477b-108">Pour plus d’informations, consultez l’article de référence sur les [expressions de bouclage](./loops-for-in-expression.md).</span><span class="sxs-lookup"><span data-stu-id="8477b-108">For more information, see the [looping expression reference article](./loops-for-in-expression.md).</span></span>

<span data-ttu-id="8477b-109">F # prend actuellement en charge la découpage des chaînes, des listes, des tableaux et des tableaux multidimensionnels (2D, 3D, 4D).</span><span class="sxs-lookup"><span data-stu-id="8477b-109">F# currently has intrinsic support for slicing strings, lists, arrays, and multidimensional (2D, 3D, 4D) arrays.</span></span> <span data-ttu-id="8477b-110">Le découpage est le plus souvent utilisé avec les tableaux et les listes F #.</span><span class="sxs-lookup"><span data-stu-id="8477b-110">Slicing is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="8477b-111">Vous pouvez ajouter des découpages à vos types de données personnalisés à l’aide `GetSlice` de la méthode dans votre définition de type ou dans une [extension de type](type-extensions.md)dans la portée.</span><span class="sxs-lookup"><span data-stu-id="8477b-111">You can add slicing to your custom data types by using the `GetSlice` method in your type definition or in an in-scope [type extension](type-extensions.md).</span></span>

## <a name="slicing-f-lists-and-arrays"></a><span data-ttu-id="8477b-112">Découpage des listes et des tableaux F #</span><span class="sxs-lookup"><span data-stu-id="8477b-112">Slicing F# lists and arrays</span></span>

<span data-ttu-id="8477b-113">Les types de données les plus courants qui sont découpés sont des listes et des tableaux F #.</span><span class="sxs-lookup"><span data-stu-id="8477b-113">The most common data types that are sliced are F# lists and arrays.</span></span>  <span data-ttu-id="8477b-114">L’exemple suivant montre comment découper des listes :</span><span class="sxs-lookup"><span data-stu-id="8477b-114">The following example demonstrates how to slice lists:</span></span>

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

<span data-ttu-id="8477b-115">Le découpage de tableaux se présente comme des listes de découpage :</span><span class="sxs-lookup"><span data-stu-id="8477b-115">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="8477b-116">Découpage de tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="8477b-116">Slicing multidimensional arrays</span></span>

<span data-ttu-id="8477b-117">F # prend en charge les tableaux multidimensionnels dans la bibliothèque principale F #.</span><span class="sxs-lookup"><span data-stu-id="8477b-117">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="8477b-118">Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles.</span><span class="sxs-lookup"><span data-stu-id="8477b-118">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="8477b-119">Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.</span><span class="sxs-lookup"><span data-stu-id="8477b-119">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="8477b-120">Les exemples suivants montrent comment découper un tableau 2D :</span><span class="sxs-lookup"><span data-stu-id="8477b-120">The following examples demonstrate how to slice a 2D array:</span></span>

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

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="8477b-121">Définition de tranches pour d’autres structures de données</span><span class="sxs-lookup"><span data-stu-id="8477b-121">Defining slices for other data structures</span></span>

<span data-ttu-id="8477b-122">La bibliothèque principale F # définit des tranches pour un ensemble limité de types.</span><span class="sxs-lookup"><span data-stu-id="8477b-122">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="8477b-123">Si vous souhaitez définir des tranches pour davantage de types de données, vous pouvez le faire soit dans la définition de type elle-même, soit dans une extension de type.</span><span class="sxs-lookup"><span data-stu-id="8477b-123">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="8477b-124">Par exemple, voici comment vous pouvez définir des secteurs pour la <xref:System.ArraySegment%601> classe afin de faciliter la manipulation de données :</span><span class="sxs-lookup"><span data-stu-id="8477b-124">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

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

<span data-ttu-id="8477b-125">Autre exemple utilisant les <xref:System.Span%601> <xref:System.ReadOnlySpan%601> types et :</span><span class="sxs-lookup"><span data-stu-id="8477b-125">Another example using the <xref:System.Span%601> and <xref:System.ReadOnlySpan%601> types:</span></span>

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

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="8477b-126">Les tranches F # intégrées sont finales</span><span class="sxs-lookup"><span data-stu-id="8477b-126">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="8477b-127">Toutes les tranches intrinsèques en F # sont de fin inclusive ; autrement dit, la limite supérieure est incluse dans la tranche.</span><span class="sxs-lookup"><span data-stu-id="8477b-127">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="8477b-128">Pour une tranche donnée avec un index de départ `x` et un index de fin `y` , la tranche résultante inclut la valeur *YTH* .</span><span class="sxs-lookup"><span data-stu-id="8477b-128">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a><span data-ttu-id="8477b-129">Tranches vides F # intégrées</span><span class="sxs-lookup"><span data-stu-id="8477b-129">Built-in F# empty slices</span></span>

<span data-ttu-id="8477b-130">Les listes F #, les tableaux, les séquences, les chaînes, les tableaux multidimensionnels (2D, 3D, 4D) génèrent tous une tranche vide si la syntaxe peut produire une tranche qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="8477b-130">F# lists, arrays, sequences, strings, multidimensional (2D, 3D, 4D) arrays will all produce an empty slice if the syntax could produce a slice that doesn't exist.</span></span>

<span data-ttu-id="8477b-131">Prenons l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="8477b-131">Consider the following example:</span></span>

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> <span data-ttu-id="8477b-132">Les développeurs C# peuvent s’attendre à ce qu’ils lèvent une exception au lieu de produire une tranche vide.</span><span class="sxs-lookup"><span data-stu-id="8477b-132">C# developers may expect these to throw an exception rather than produce an empty slice.</span></span> <span data-ttu-id="8477b-133">Il s’agit d’une décision de conception enracinée dans le fait que les collections vides composent en F #.</span><span class="sxs-lookup"><span data-stu-id="8477b-133">This is a design decision rooted in the fact that empty collections compose in F#.</span></span> <span data-ttu-id="8477b-134">Une liste F # vide peut être composée d’une autre liste F #, une chaîne vide peut être ajoutée à une chaîne existante, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8477b-134">An empty F# list can be composed with another F# list, an empty string can be added to an existing string, and so on.</span></span> <span data-ttu-id="8477b-135">Il peut être courant de prendre des tranches basées sur des valeurs transmises en tant que paramètres, et d’être tolérantes aux valeurs hors limites > en produisant une collection vide qui respecte la nature compositionnelle du code F #.</span><span class="sxs-lookup"><span data-stu-id="8477b-135">It can be common to take slices based on values passed in as parameters, and being tolerant of out-of-bounds > by producing an empty collection fits with the compositional nature of F# code.</span></span>

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a><span data-ttu-id="8477b-136">Tranches à index fixe pour les tableaux 3D et 4D</span><span class="sxs-lookup"><span data-stu-id="8477b-136">Fixed-index slices for 3D and 4D arrays</span></span>

<span data-ttu-id="8477b-137">Pour les tableaux F # 3D et 4D, vous pouvez « corriger » un index particulier et découper les autres dimensions avec cet index fixe.</span><span class="sxs-lookup"><span data-stu-id="8477b-137">For F# 3D and 4D arrays, you can "fix" a particular index and slice other dimensions with that index fixed.</span></span>

<span data-ttu-id="8477b-138">Pour illustrer cela, examinez le tableau 3D suivant :</span><span class="sxs-lookup"><span data-stu-id="8477b-138">To illustrate this, consider the following 3D array:</span></span>

<span data-ttu-id="8477b-139">*z = 0*</span><span class="sxs-lookup"><span data-stu-id="8477b-139">*z = 0*</span></span>

| <span data-ttu-id="8477b-140">x\y</span><span class="sxs-lookup"><span data-stu-id="8477b-140">x\y</span></span>   | <span data-ttu-id="8477b-141">0</span><span class="sxs-lookup"><span data-stu-id="8477b-141">0</span></span> | <span data-ttu-id="8477b-142">1</span><span class="sxs-lookup"><span data-stu-id="8477b-142">1</span></span> |
|-------|---|---|
| <span data-ttu-id="8477b-143">**0**</span><span class="sxs-lookup"><span data-stu-id="8477b-143">**0**</span></span> | <span data-ttu-id="8477b-144">0</span><span class="sxs-lookup"><span data-stu-id="8477b-144">0</span></span> | <span data-ttu-id="8477b-145">1</span><span class="sxs-lookup"><span data-stu-id="8477b-145">1</span></span> |
| <span data-ttu-id="8477b-146">**1**</span><span class="sxs-lookup"><span data-stu-id="8477b-146">**1**</span></span> | <span data-ttu-id="8477b-147">2</span><span class="sxs-lookup"><span data-stu-id="8477b-147">2</span></span> | <span data-ttu-id="8477b-148">3</span><span class="sxs-lookup"><span data-stu-id="8477b-148">3</span></span> |

<span data-ttu-id="8477b-149">*z = 1*</span><span class="sxs-lookup"><span data-stu-id="8477b-149">*z = 1*</span></span>

| <span data-ttu-id="8477b-150">x\y</span><span class="sxs-lookup"><span data-stu-id="8477b-150">x\y</span></span>   | <span data-ttu-id="8477b-151">0</span><span class="sxs-lookup"><span data-stu-id="8477b-151">0</span></span> | <span data-ttu-id="8477b-152">1</span><span class="sxs-lookup"><span data-stu-id="8477b-152">1</span></span> |
|-------|---|---|
| <span data-ttu-id="8477b-153">**0**</span><span class="sxs-lookup"><span data-stu-id="8477b-153">**0**</span></span> | <span data-ttu-id="8477b-154">4</span><span class="sxs-lookup"><span data-stu-id="8477b-154">4</span></span> | <span data-ttu-id="8477b-155">5</span><span class="sxs-lookup"><span data-stu-id="8477b-155">5</span></span> |
| <span data-ttu-id="8477b-156">**1**</span><span class="sxs-lookup"><span data-stu-id="8477b-156">**1**</span></span> | <span data-ttu-id="8477b-157">6</span><span class="sxs-lookup"><span data-stu-id="8477b-157">6</span></span> | <span data-ttu-id="8477b-158">7</span><span class="sxs-lookup"><span data-stu-id="8477b-158">7</span></span> |

<span data-ttu-id="8477b-159">Si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau, utilisez une tranche à index fixe.</span><span class="sxs-lookup"><span data-stu-id="8477b-159">If you want to extract the slice `[| 4; 5 |]` from the array, use a fixed-index slice.</span></span>

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

<span data-ttu-id="8477b-160">La dernière ligne corrige les `y` `z` index et du tableau 3D et prend le reste des `x` valeurs qui correspondent à la matrice.</span><span class="sxs-lookup"><span data-stu-id="8477b-160">The last line fixes the `y` and `z` indices of the 3D array and takes the rest of the `x` values that correspond to the matrix.</span></span>

## <a name="see-also"></a><span data-ttu-id="8477b-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8477b-161">See also</span></span>

- [<span data-ttu-id="8477b-162">Propriétés indexées</span><span class="sxs-lookup"><span data-stu-id="8477b-162">Indexed properties</span></span>](./members/indexed-properties.md)

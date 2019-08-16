---
title: Tranches (F#)
description: Découvrez comment utiliser des tranches pour les types F# de données existants et comment définir vos propres tranches pour d’autres types de données.
ms.date: 01/22/2019
ms.openlocfilehash: 3067982c2b4249312c7e9365bbfb994be840911d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627149"
---
# <a name="slices"></a>Sections

Dans F#, une tranche est un sous-ensemble d’un type de données. Pour pouvoir prendre une tranche d’un type de données, le type de données doit définir une `GetSlice` méthode ou dans une extension de [type](type-extensions.md) qui se trouve dans la portée. Cet article explique comment prendre des tranches de types F# existants et comment définir les vôtres.

Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs.

F#prend actuellement en charge la découpage des chaînes, des listes, des tableaux et des tableaux 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Découpage de F# base avec des listes et des tableaux

Les types de données les plus courants qui sont découpés sont F# des listes et des tableaux. L’exemple suivant montre comment effectuer cette opération avec des listes:

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

Le découpage de tableaux se présente comme des listes de découpage:

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

## <a name="slicing-multidimensional-arrays"></a>Découpage de tableaux multidimensionnels

F#prend en charge les tableaux multidimensionnels F# dans la bibliothèque principale. Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles. Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.

Les exemples suivants montrent comment découper un tableau 2D:

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

La F# bibliothèque principale n’est pas `GetSlice`définie pour les tableaux 3D. Si vous souhaitez découper ces tableaux ou d’autres dimensions, vous devez définir le `GetSlice` membre vous-même.

## <a name="defining-slices-for-other-data-structures"></a>Définition de tranches pour d’autres structures de données

La F# bibliothèque principale définit des tranches pour un ensemble limité de types. Si vous souhaitez définir des tranches pour davantage de types de données, vous pouvez le faire soit dans la définition de type elle-même, soit dans une extension de type.

Par exemple, voici comment vous pouvez définir des secteurs pour la <xref:System.ArraySegment%601> classe afin de faciliter la manipulation de données:

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Utilisez l’incorporation pour éviter le boxing si nécessaire.

Si vous définissez des tranches pour un type qui est en fait un struct, nous vous recommandons `inline` d' `GetSlice` utiliser le membre. Le F# compilateur optimise les arguments facultatifs, évitant ainsi toute allocation de tas résultant du découpage. Cela est très important pour les constructions de découpage, <xref:System.Span%601> telles que, qui ne peuvent pas être allouées sur le tas.

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a>Voir aussi

- [Propriétés indexées](./members/indexed-properties.md)

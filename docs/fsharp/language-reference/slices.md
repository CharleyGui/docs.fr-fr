---
title: Sections
description: 'Découvrez comment utiliser des tranches pour les types de données F # existants et comment définir vos propres tranches pour d’autres types de données.'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559009"
---
# <a name="slices"></a>Sections

En F #, une tranche est un sous-ensemble de tout type de données qui a une `GetSlice` méthode dans sa définition ou dans une [extension de type](type-extensions.md)dans la portée. Il est le plus couramment utilisé avec les tableaux et les listes F #. Cet article explique comment prendre des tranches à partir de types F # existants et comment définir vos propres tranches.

Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs.

F # a actuellement une prise en charge intrinsèque pour le découpage des chaînes, des listes, des tableaux et des tableaux 2D.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Découpage de base avec des listes et des tableaux F #

Les types de données les plus courants qui sont découpés sont des listes et des tableaux F #. L’exemple suivant montre comment effectuer cette opération avec des listes :

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

Le découpage de tableaux se présente comme des listes de découpage :

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

F # prend en charge les tableaux multidimensionnels dans la bibliothèque principale F #. Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles. Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.

Les exemples suivants montrent comment découper un tableau 2D :

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

Actuellement, la bibliothèque principale F # n’est pas définie `GetSlice` pour les tableaux 3D. Si vous souhaitez découper des tableaux 3D ou d’autres tableaux de dimensions supplémentaires, définissez le `GetSlice` membre vous-même.

## <a name="defining-slices-for-other-data-structures"></a>Définition de tranches pour d’autres structures de données

La bibliothèque principale F # définit des tranches pour un ensemble limité de types. Si vous souhaitez définir des tranches pour davantage de types de données, vous pouvez le faire soit dans la définition de type elle-même, soit dans une extension de type.

Par exemple, voici comment vous pouvez définir des secteurs pour la <xref:System.ArraySegment%601> classe afin de faciliter la manipulation de données :

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

Autre exemple utilisant les <xref:System.Span%601> <xref:System.ReadOnlySpan%601> types et :

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

## <a name="built-in-f-slices-are-end-inclusive"></a>Les tranches F # intégrées sont finales

Toutes les tranches intrinsèques en F # sont de fin inclusive ; autrement dit, la limite supérieure est incluse dans la tranche. Pour une tranche donnée avec un index de départ `x` et un index de fin `y` , la tranche résultante inclut la valeur *YTH* .

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a>Voir aussi

- [Propriétés indexées](./members/indexed-properties.md)

---
title: Sections
description: 'Découvrez comment utiliser des tranches pour les types de données F # existants et comment définir vos propres tranches pour d’autres types de données.'
ms.date: 11/20/2020
ms.openlocfilehash: b776058df5a174dfe48dbf513bf17281036dd83e
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740378"
---
# <a name="slices"></a>Sections

Cet article explique comment prendre des tranches à partir de types F # existants et comment définir vos propres tranches.

En F #, une tranche est un sous-ensemble de n’importe quel type de données.  Les tranches sont similaires aux [indexeurs](./members/indexed-properties.md), mais au lieu de produire une valeur unique à partir de la structure de données sous-jacente, elles produisent plusieurs valeurs. Les tranches utilisent la `..` syntaxe d’opérateur pour sélectionner la plage d’index spécifiée dans un type de données. Pour plus d’informations, consultez l’article de référence sur les [expressions de bouclage](./loops-for-in-expression.md).

F # prend actuellement en charge la découpage des chaînes, des listes, des tableaux et des tableaux multidimensionnels (2D, 3D, 4D). Le découpage est le plus souvent utilisé avec les tableaux et les listes F #. Vous pouvez ajouter des découpages à vos types de données personnalisés à l’aide `GetSlice` de la méthode dans votre définition de type ou dans une [extension de type](type-extensions.md)dans la portée.

## <a name="slicing-f-lists-and-arrays"></a>Découpage des listes et des tableaux F #

Les types de données les plus courants qui sont découpés sont des listes et des tableaux F #.  L’exemple suivant montre comment découper des listes :

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

Le découpage de tableaux se présente comme des listes de découpage :

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn $"Small slice: {smallSlice}"

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn $"Unbounded beginning slice: {unboundedBeginning}"

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn $"Unbounded end slice: {unboundedEnd}"
```

## <a name="slicing-multidimensional-arrays"></a>Découpage de tableaux multidimensionnels

F # prend en charge les tableaux multidimensionnels dans la bibliothèque principale F #. Comme avec les tableaux unidimensionnels, les secteurs des tableaux multidimensionnels peuvent également être utiles. Toutefois, l’introduction de dimensions supplémentaires impose une syntaxe légèrement différente pour vous permettre de prendre des tranches de lignes et de colonnes spécifiques.

Les exemples suivants montrent comment découper un tableau 2D :

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn $"Full matrix:\n {A}"

// Take the first row
let row0 = A.[0,*]
printfn $"{row0}"

// Take the first column
let col0 = A.[*,0]
printfn $"{col0}"

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn $"{subA}"

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn $"{subA}"

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn $"{twoByTwo}"
```

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
    printfn $"{arr}"

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

printfn $"{xs.[2..5]}" // Includes the 5th index
```

## <a name="built-in-f-empty-slices"></a>Tranches vides F # intégrées

Les listes F #, les tableaux, les séquences, les chaînes, les tableaux multidimensionnels (2D, 3D, 4D) génèrent tous une tranche vide si la syntaxe peut produire une tranche qui n’existe pas.

Prenons l’exemple suivant :

```fsharp
let l = [ 1..10 ]
let a = [| 1..10 |]
let s = "hello!"

let emptyList = l.[-2..(-1)]
let emptyArray = a.[-2..(-1)]
let emptyString = s.[-2..(-1)]
```

> [!IMPORTANT]
> Les développeurs C# peuvent s’attendre à ce qu’ils lèvent une exception au lieu de produire une tranche vide. Il s’agit d’une décision de conception enracinée dans le fait que les collections vides composent en F #. Une liste F # vide peut être composée d’une autre liste F #, une chaîne vide peut être ajoutée à une chaîne existante, et ainsi de suite. Il peut être courant de prendre des tranches basées sur des valeurs transmises en tant que paramètres, et d’être tolérantes aux valeurs hors limites > en produisant une collection vide qui respecte la nature compositionnelle du code F #.

## <a name="fixed-index-slices-for-3d-and-4d-arrays"></a>Tranches à index fixe pour les tableaux 3D et 4D

Pour les tableaux F # 3D et 4D, vous pouvez « corriger » un index particulier et découper les autres dimensions avec cet index fixe.

Pour illustrer cela, examinez le tableau 3D suivant :

*z = 0*

| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 0 | 1 |
| **1** | 2 | 3 |

*z = 1*

| x\y   | 0 | 1 |
|-------|---|---|
| **0** | 4 | 5 |
| **1** | 6 | 7 |

Si vous souhaitez extraire la tranche `[| 4; 5 |]` du tableau, utilisez une tranche à index fixe.

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

La dernière ligne corrige les `y` `z` index et du tableau 3D et prend le reste des `x` valeurs qui correspondent à la matrice.

## <a name="see-also"></a>Voir aussi

- [Propriétés indexées](./members/indexed-properties.md)

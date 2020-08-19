---
title: Tableaux
description: 'Découvrez comment créer et utiliser des tableaux dans le langage de programmation F #.'
ms.date: 08/13/2020
ms.openlocfilehash: 93d524046ff93a7f1b04e72d580d9d0e1360ba0b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558879"
---
# <a name="arrays"></a>Tableaux

Les tableaux sont des collections de taille fixe, de base zéro et mutables d’éléments de données consécutifs qui sont tous du même type.

## <a name="create-arrays"></a>Créer des tableaux

Vous pouvez créer des tableaux de plusieurs façons. Vous pouvez créer un petit tableau en répertoriant des valeurs consécutives entre `[|` et `|]` et séparées par des points-virgules, comme indiqué dans les exemples suivants.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

Vous pouvez également placer chaque élément sur une ligne distincte, auquel cas le séparateur de points-virgules est facultatif.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

Le type des éléments du tableau est déduit des littéraux utilisés et doit être cohérent. Le code suivant génère une erreur, car 1,0 est de type float et 2 et 3 sont des entiers.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Vous pouvez également utiliser des expressions de séquence pour créer des tableaux. Voici un exemple qui crée un tableau de carrés d’entiers de 1 à 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

Pour créer un tableau dans lequel tous les éléments sont initialisés à zéro, utilisez `Array.zeroCreate` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>Éléments d’accès

Vous pouvez accéder aux éléments de tableau à l’aide d’un opérateur point ( `.` ) et de crochets ( `[` et `]` ).

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

Les index de tableau commencent à 0.

Vous pouvez également accéder aux éléments de tableau à l’aide de la notation de découpage, qui vous permet de spécifier une sous-plage du tableau. Voici des exemples de notation de découpage.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

Lorsque la notation par segment est utilisée, une nouvelle copie du tableau est créée.

## <a name="array-types-and-modules"></a>Modules et types de tableau

Le type de tous les tableaux F # est le type de .NET Framework <xref:System.Array?displayProperty=nameWithType> . Par conséquent, les tableaux F # prennent en charge toutes les fonctionnalités disponibles dans <xref:System.Array?displayProperty=nameWithType> .

Le [ `Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) prend en charge les opérations sur les tableaux unidimensionnels. Les modules `Array2D` , `Array3D` et `Array4D` contiennent des fonctions qui prennent en charge les opérations sur les tableaux de deux, trois et quatre dimensions, respectivement. Vous pouvez créer des tableaux de rang supérieur à quatre à l’aide de <xref:System.Array?displayProperty=nameWithType> .

### <a name="simple-functions"></a>Fonctions simples

[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Obtient un élément. [`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) donne la longueur d’un tableau. [`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) affecte une valeur spécifiée à un élément. L’exemple de code suivant illustre l’utilisation de ces fonctions.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

La sortie est la suivante.

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Fonctions qui créent des tableaux

Plusieurs fonctions créent des tableaux sans nécessiter de tableau existant. [`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) crée un tableau qui ne contient aucun élément. [`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) crée un tableau d’une taille spécifiée et définit tous les éléments sur les valeurs fournies. [`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) crée un tableau, en fonction d’une dimension et d’une fonction pour générer les éléments. [`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) crée un tableau dans lequel tous les éléments sont initialisés à la valeur zéro pour le type du tableau. Le code suivant illustre ces fonctions.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

La sortie est la suivante.

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) crée un tableau qui contient des éléments copiés à partir d’un tableau existant. Notez que la copie est une copie superficielle, ce qui signifie que si le type d’élément est un type référence, seule la référence est copiée, et non l’objet sous-jacent. L'exemple de code suivant illustre ceci.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

La sortie du code précédent est la suivante :

```console
[|Test1; Test2; |]
[|; Test2; |]
```

La chaîne `Test1` apparaît uniquement dans le premier tableau, car l’opération de création d’un nouvel élément remplace la référence dans, `firstArray` mais n’affecte pas la référence d’origine à une chaîne vide qui est encore présente dans `secondArray` . La chaîne `Test2` apparaît dans les deux tableaux, car l' `Insert` opération sur le <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affecte l’objet sous-jacent <xref:System.Text.StringBuilder?displayProperty=nameWithType> , qui est référencé dans les deux tableaux.

[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) génère un nouveau tableau à partir d’une sous-plage d’un tableau. Vous spécifiez la sous-plage en fournissant l’index de départ et la longueur. Le code suivant montre l'utilisation de `Array.sub`.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

La sortie indique que le sous-tableau commence à l’élément 5 et contient 10 éléments.

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) crée un tableau en combinant deux tableaux existants.

Le code suivant illustre **Array. Append**.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

La sortie du code précédent est la suivante.

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) sélectionne les éléments d’un tableau à inclure dans un nouveau tableau. Le code suivant illustre `Array.choose` . Notez que le type d’élément du tableau ne doit pas nécessairement correspondre au type de la valeur retournée dans le type d’option. Dans cet exemple, le type d’élément est `int` et l’option est le résultat d’une fonction polynomiale, `elem*elem - 1` , sous la forme d’un nombre à virgule flottante.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

La sortie du code précédent est la suivante.

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) exécute une fonction spécifiée sur chaque élément de tableau d’un tableau existant, puis collecte les éléments générés par la fonction et les combine dans un nouveau tableau. Le code suivant illustre `Array.collect` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

La sortie du code précédent est la suivante.

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) prend une séquence de tableaux et les combine en un seul tableau. Le code suivant illustre `Array.concat` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

La sortie du code précédent est la suivante.

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) prend une fonction de condition booléenne et génère un nouveau tableau qui contient uniquement les éléments du tableau d’entrée pour lesquels la condition a la valeur true. Le code suivant illustre `Array.filter` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

La sortie du code précédent est la suivante.

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) génère un nouveau tableau en inversant l’ordre d’un tableau existant. Le code suivant illustre `Array.rev` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

La sortie du code précédent est la suivante.

```console
"Hello world!"
```

Vous pouvez facilement combiner des fonctions dans le module de tableau qui transforment des tableaux à l’aide de l’opérateur de pipeline ( `|>` ), comme indiqué dans l’exemple suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

La sortie est la suivante :

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Tableaux multidimensionnels

Un tableau multidimensionnel peut être créé, mais il n’existe aucune syntaxe pour l’écriture d’un littéral de tableau multidimensionnel. Utilisez l’opérateur [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) pour créer un tableau à partir d’une séquence de séquences d’éléments de tableau. Les séquences peuvent être des littéraux de liste ou de tableau. Par exemple, le code suivant crée un tableau à deux dimensions.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

Vous pouvez également utiliser la fonction [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) pour initialiser des tableaux de deux dimensions, et des fonctions similaires sont disponibles pour les tableaux de trois et quatre dimensions. Ces fonctions prennent une fonction qui est utilisée pour créer les éléments. Pour créer un tableau à deux dimensions qui contient des éléments définis sur une valeur initiale au lieu de spécifier une fonction, utilisez la [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) fonction, qui est également disponible pour les tableaux jusqu’à quatre dimensions. L’exemple de code suivant montre d’abord comment créer un tableau de tableaux qui contiennent les éléments souhaités, puis utilise `Array2D.init` pour générer le tableau à deux dimensions souhaité.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

L’indexation de tableau et la syntaxe de découpage sont prises en charge pour les tableaux jusqu’au rang 4. Lorsque vous spécifiez un index dans plusieurs dimensions, vous utilisez des virgules pour séparer les index, comme illustré dans l’exemple de code suivant.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

Le type d’un tableau à deux dimensions est écrit sous la forme `<type>[,]` (par exemple, `int[,]` , `double[,]` ), et le type d’un tableau à trois dimensions est écrit `<type>[,,]` , et ainsi de suite pour les tableaux de dimensions supérieures.

Seul un sous-ensemble des fonctions disponibles pour les tableaux unidimensionnels est également disponible pour les tableaux multidimensionnels.

### <a name="array-slicing-and-multidimensional-arrays"></a>Découpage de tableau et tableaux multidimensionnels

Dans un tableau à deux dimensions (une matrice), vous pouvez extraire une sous-matrice en spécifiant des plages et en utilisant un caractère générique ( `*` ) pour spécifier des lignes ou des colonnes entières.

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Vous pouvez décomposer un tableau multidimensionnel en sous-tableaux de la même dimension ou de la même dimension inférieure. Par exemple, vous pouvez obtenir un vecteur à partir d’une matrice en spécifiant une seule ligne ou colonne.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Vous pouvez utiliser cette syntaxe de découpage pour les types qui implémentent les opérateurs d’accès aux éléments et les méthodes surchargées `GetSlice` . Par exemple, le code suivant crée un type de matrice qui encapsule le tableau F # 2D, implémente une propriété d’élément pour assurer la prise en charge de l’indexation de tableau et implémente trois versions de `GetSlice` . Si vous pouvez utiliser ce code comme modèle pour vos types de matrices, vous pouvez utiliser toutes les opérations de découpage décrites dans cette section.

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>Fonctions booléennes sur les tableaux

Les fonctions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) et les [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) éléments de test dans un ou deux tableaux, respectivement. Ces fonctions prennent une fonction de test et retournent `true` s’il existe un élément (ou une paire d’éléments pour `Array.exists2` ) qui satisfait à la condition.

Le code suivant illustre l’utilisation de `Array.exists` et de `Array.exists2` . Dans ces exemples, de nouvelles fonctions sont créées en appliquant un seul des arguments, dans ce cas, l’argument de fonction.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

La sortie du code précédent est la suivante.

```console
true
false
false
true
```

De même, la fonction [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) teste un tableau pour déterminer si chaque élément remplit une condition booléenne. La variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) fait la même chose à l’aide d’une fonction booléenne qui implique des éléments de deux tableaux de longueur égale. Le code suivant illustre l’utilisation de ces fonctions.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

La sortie de ces exemples est la suivante.

```console
false
true
true
false
```

### <a name="search-arrays"></a>Rechercher dans les tableaux

[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) prend une fonction booléenne et retourne le premier élément pour lequel la fonction retourne `true` , ou lève une <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> si aucun élément répondant à la condition n’est trouvé. [`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) est semblable `Array.find` à, à ceci près qu’elle retourne l’index de l’élément au lieu de l’élément lui-même.

Le code suivant utilise `Array.find` et `Array.findIndex` pour localiser un nombre qui est à la fois un carré parfait et un cube parfait.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

La sortie est la suivante.

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) est semblable `Array.find` à, à ceci près que son résultat est un type d’option et qu’il retourne `None` si aucun élément n’est trouvé. `Array.tryFind` doit être utilisé au lieu de `Array.find` lorsque vous ne savez pas si un élément correspondant se trouve dans le tableau. De même, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) est semblable `Array.findIndex` à, à ceci près que le type d’option est la valeur de retour. Si aucun élément n’est trouvé, l’option est `None` .

Le code suivant montre l'utilisation de `Array.tryFind`. Ce code dépend du code précédent.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

La sortie est la suivante.

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

Utilisez [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) lorsque vous devez transformer un élément en plus de le trouver. Le résultat est le premier élément pour lequel la fonction retourne l’élément transformé comme valeur d’option, ou `None` si aucun élément de ce type n’est trouvé.

Le code suivant illustre l'utilisation de `Array.tryPick`. Dans ce cas, au lieu d’une expression lambda, plusieurs fonctions d’assistance locales sont définies pour simplifier le code.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

La sortie est la suivante.

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>Effectuer des calculs sur des tableaux

La [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) fonction retourne la moyenne de chaque élément d’un tableau. Elle est limitée aux types d’éléments qui prennent en charge la Division exacte par un entier, ce qui comprend les types à virgule flottante, mais pas les types intégraux. La [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) fonction retourne la moyenne des résultats de l’appel d’une fonction sur chaque élément. Pour un tableau de type intégral, vous pouvez utiliser `Array.averageBy` et faire en sorte que la fonction convertisse chaque élément en type à virgule flottante pour le calcul.

Utilisez [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) ou [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) pour accéder à l’élément maximal ou minimal, si le type d’élément le prend en charge. De même, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) et [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) autorisent l’exécution d’une fonction en premier, peut-être à transformer en un type qui prend en charge la comparaison.

[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Ajoute les éléments d’un tableau et [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) appelle une fonction sur chaque élément et ajoute les résultats ensemble.

Pour exécuter une fonction sur chaque élément d’un tableau sans stocker les valeurs de retour, utilisez [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) . Pour une fonction qui implique deux tableaux de longueur égale, utilisez [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) . Si vous devez également conserver un tableau des résultats de la fonction, utilisez [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) ou [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , qui opère sur deux tableaux à la fois.

Les variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) et [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) permettent à l’index de l’élément d’être impliqué dans le calcul. il en va de même pour [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) et [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .

Les fonctions,,,, [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) et [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) exécutent des algorithmes qui impliquent tous les éléments d’un tableau. De même, les variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) et [`Array.foldBack2`](foldBack2) effectuent des calculs sur deux tableaux.

Ces fonctions pour effectuer des calculs correspondent aux fonctions du même nom dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html). Pour obtenir des exemples d’utilisation, consultez [listes](lists.md).

### <a name="modify-arrays"></a>Modifier des tableaux

[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) affecte une valeur spécifiée à un élément. [`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) affecte une valeur spécifiée à une plage d’éléments d’un tableau. Le code suivant fournit un exemple de `Array.fill` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

La sortie est la suivante.

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Vous pouvez utiliser [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) pour copier une sous-section d’un tableau dans un autre tableau.

### <a name="convert-to-and-from-other-types"></a>Convertir en et à partir d’autres types

[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) crée un tableau à partir d’une liste. [`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) crée un tableau à partir d’une séquence. [`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) et sont [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convertis en ces autres types de collection à partir du type de tableau.

### <a name="sort-arrays"></a>Trier les tableaux

Utilisez [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) pour trier un tableau à l’aide de la fonction de comparaison générique. Utilisez [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) pour spécifier une fonction qui génère une valeur, appelée *clé*, à trier à l’aide de la fonction de comparaison générique sur la clé. Utilisez [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) si vous souhaitez fournir une fonction de comparaison personnalisée. `Array.sort`, `Array.sortBy` et `Array.sortWith` retournent tous le tableau trié sous la forme d’un nouveau tableau. Les variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) et [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modifient le tableau existant au lieu de retourner un nouveau.

### <a name="arrays-and-tuples"></a>Tableaux et tuples

Les fonctions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) et [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convertissent les tableaux de paires de tuples en tuples de tableaux, et vice versa. [`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) et [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) sont similaires, à ceci près qu’ils fonctionnent avec des tuples de trois éléments ou des tuples de trois tableaux.

## <a name="parallel-computations-on-arrays"></a>Calculs parallèles sur les tableaux

Le module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contient des fonctions permettant d’effectuer des calculs parallèles sur des tableaux. Ce module n’est pas disponible dans les applications qui ciblent les versions de .NET Framework antérieures à la version 4.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Types F#](fsharp-types.md)

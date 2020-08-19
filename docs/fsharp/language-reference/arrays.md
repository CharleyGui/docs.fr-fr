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
# <a name="arrays"></a><span data-ttu-id="aee10-103">Tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-103">Arrays</span></span>

<span data-ttu-id="aee10-104">Les tableaux sont des collections de taille fixe, de base zéro et mutables d’éléments de données consécutifs qui sont tous du même type.</span><span class="sxs-lookup"><span data-stu-id="aee10-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="aee10-105">Créer des tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-105">Create arrays</span></span>

<span data-ttu-id="aee10-106">Vous pouvez créer des tableaux de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="aee10-106">You can create arrays in several ways.</span></span> <span data-ttu-id="aee10-107">Vous pouvez créer un petit tableau en répertoriant des valeurs consécutives entre `[|` et `|]` et séparées par des points-virgules, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="aee10-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="aee10-108">Vous pouvez également placer chaque élément sur une ligne distincte, auquel cas le séparateur de points-virgules est facultatif.</span><span class="sxs-lookup"><span data-stu-id="aee10-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="aee10-109">Le type des éléments du tableau est déduit des littéraux utilisés et doit être cohérent.</span><span class="sxs-lookup"><span data-stu-id="aee10-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="aee10-110">Le code suivant génère une erreur, car 1,0 est de type float et 2 et 3 sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="aee10-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="aee10-111">Vous pouvez également utiliser des expressions de séquence pour créer des tableaux.</span><span class="sxs-lookup"><span data-stu-id="aee10-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="aee10-112">Voici un exemple qui crée un tableau de carrés d’entiers de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="aee10-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="aee10-113">Pour créer un tableau dans lequel tous les éléments sont initialisés à zéro, utilisez `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="aee10-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="aee10-114">Éléments d’accès</span><span class="sxs-lookup"><span data-stu-id="aee10-114">Access elements</span></span>

<span data-ttu-id="aee10-115">Vous pouvez accéder aux éléments de tableau à l’aide d’un opérateur point ( `.` ) et de crochets ( `[` et `]` ).</span><span class="sxs-lookup"><span data-stu-id="aee10-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="aee10-116">Les index de tableau commencent à 0.</span><span class="sxs-lookup"><span data-stu-id="aee10-116">Array indexes start at 0.</span></span>

<span data-ttu-id="aee10-117">Vous pouvez également accéder aux éléments de tableau à l’aide de la notation de découpage, qui vous permet de spécifier une sous-plage du tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="aee10-118">Voici des exemples de notation de découpage.</span><span class="sxs-lookup"><span data-stu-id="aee10-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="aee10-119">Lorsque la notation par segment est utilisée, une nouvelle copie du tableau est créée.</span><span class="sxs-lookup"><span data-stu-id="aee10-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="aee10-120">Modules et types de tableau</span><span class="sxs-lookup"><span data-stu-id="aee10-120">Array types and modules</span></span>

<span data-ttu-id="aee10-121">Le type de tous les tableaux F # est le type de .NET Framework <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aee10-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aee10-122">Par conséquent, les tableaux F # prennent en charge toutes les fonctionnalités disponibles dans <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aee10-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="aee10-123">Le [ `Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) prend en charge les opérations sur les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="aee10-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="aee10-124">Les modules `Array2D` , `Array3D` et `Array4D` contiennent des fonctions qui prennent en charge les opérations sur les tableaux de deux, trois et quatre dimensions, respectivement.</span><span class="sxs-lookup"><span data-stu-id="aee10-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="aee10-125">Vous pouvez créer des tableaux de rang supérieur à quatre à l’aide de <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aee10-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="aee10-126">Fonctions simples</span><span class="sxs-lookup"><span data-stu-id="aee10-126">Simple functions</span></span>

<span data-ttu-id="aee10-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Obtient un élément.</span><span class="sxs-lookup"><span data-stu-id="aee10-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="aee10-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) donne la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="aee10-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) affecte une valeur spécifiée à un élément.</span><span class="sxs-lookup"><span data-stu-id="aee10-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="aee10-130">L’exemple de code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="aee10-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="aee10-131">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="aee10-132">Fonctions qui créent des tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-132">Functions that create arrays</span></span>

<span data-ttu-id="aee10-133">Plusieurs fonctions créent des tableaux sans nécessiter de tableau existant.</span><span class="sxs-lookup"><span data-stu-id="aee10-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="aee10-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) crée un tableau qui ne contient aucun élément.</span><span class="sxs-lookup"><span data-stu-id="aee10-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="aee10-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) crée un tableau d’une taille spécifiée et définit tous les éléments sur les valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="aee10-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="aee10-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) crée un tableau, en fonction d’une dimension et d’une fonction pour générer les éléments.</span><span class="sxs-lookup"><span data-stu-id="aee10-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="aee10-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) crée un tableau dans lequel tous les éléments sont initialisés à la valeur zéro pour le type du tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="aee10-138">Le code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="aee10-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="aee10-139">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="aee10-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) crée un tableau qui contient des éléments copiés à partir d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="aee10-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="aee10-141">Notez que la copie est une copie superficielle, ce qui signifie que si le type d’élément est un type référence, seule la référence est copiée, et non l’objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="aee10-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="aee10-142">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="aee10-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="aee10-143">La sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="aee10-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="aee10-144">La chaîne `Test1` apparaît uniquement dans le premier tableau, car l’opération de création d’un nouvel élément remplace la référence dans, `firstArray` mais n’affecte pas la référence d’origine à une chaîne vide qui est encore présente dans `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="aee10-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="aee10-145">La chaîne `Test2` apparaît dans les deux tableaux, car l' `Insert` opération sur le <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affecte l’objet sous-jacent <xref:System.Text.StringBuilder?displayProperty=nameWithType> , qui est référencé dans les deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="aee10-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="aee10-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) génère un nouveau tableau à partir d’une sous-plage d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="aee10-147">Vous spécifiez la sous-plage en fournissant l’index de départ et la longueur.</span><span class="sxs-lookup"><span data-stu-id="aee10-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="aee10-148">Le code suivant montre l'utilisation de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="aee10-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="aee10-149">La sortie indique que le sous-tableau commence à l’élément 5 et contient 10 éléments.</span><span class="sxs-lookup"><span data-stu-id="aee10-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="aee10-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) crée un tableau en combinant deux tableaux existants.</span><span class="sxs-lookup"><span data-stu-id="aee10-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="aee10-151">Le code suivant illustre **Array. Append**.</span><span class="sxs-lookup"><span data-stu-id="aee10-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="aee10-152">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="aee10-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) sélectionne les éléments d’un tableau à inclure dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="aee10-154">Le code suivant illustre `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="aee10-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="aee10-155">Notez que le type d’élément du tableau ne doit pas nécessairement correspondre au type de la valeur retournée dans le type d’option.</span><span class="sxs-lookup"><span data-stu-id="aee10-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="aee10-156">Dans cet exemple, le type d’élément est `int` et l’option est le résultat d’une fonction polynomiale, `elem*elem - 1` , sous la forme d’un nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="aee10-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="aee10-157">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="aee10-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) exécute une fonction spécifiée sur chaque élément de tableau d’un tableau existant, puis collecte les éléments générés par la fonction et les combine dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="aee10-159">Le code suivant illustre `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="aee10-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="aee10-160">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="aee10-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) prend une séquence de tableaux et les combine en un seul tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="aee10-162">Le code suivant illustre `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="aee10-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="aee10-163">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="aee10-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) prend une fonction de condition booléenne et génère un nouveau tableau qui contient uniquement les éléments du tableau d’entrée pour lesquels la condition a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="aee10-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="aee10-165">Le code suivant illustre `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="aee10-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="aee10-166">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="aee10-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) génère un nouveau tableau en inversant l’ordre d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="aee10-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="aee10-168">Le code suivant illustre `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="aee10-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="aee10-169">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="aee10-170">Vous pouvez facilement combiner des fonctions dans le module de tableau qui transforment des tableaux à l’aide de l’opérateur de pipeline ( `|>` ), comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="aee10-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="aee10-171">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="aee10-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="aee10-172">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="aee10-172">Multidimensional arrays</span></span>

<span data-ttu-id="aee10-173">Un tableau multidimensionnel peut être créé, mais il n’existe aucune syntaxe pour l’écriture d’un littéral de tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="aee10-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="aee10-174">Utilisez l’opérateur [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) pour créer un tableau à partir d’une séquence de séquences d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="aee10-175">Les séquences peuvent être des littéraux de liste ou de tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="aee10-176">Par exemple, le code suivant crée un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="aee10-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="aee10-177">Vous pouvez également utiliser la fonction [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) pour initialiser des tableaux de deux dimensions, et des fonctions similaires sont disponibles pour les tableaux de trois et quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="aee10-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="aee10-178">Ces fonctions prennent une fonction qui est utilisée pour créer les éléments.</span><span class="sxs-lookup"><span data-stu-id="aee10-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="aee10-179">Pour créer un tableau à deux dimensions qui contient des éléments définis sur une valeur initiale au lieu de spécifier une fonction, utilisez la [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) fonction, qui est également disponible pour les tableaux jusqu’à quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="aee10-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="aee10-180">L’exemple de code suivant montre d’abord comment créer un tableau de tableaux qui contiennent les éléments souhaités, puis utilise `Array2D.init` pour générer le tableau à deux dimensions souhaité.</span><span class="sxs-lookup"><span data-stu-id="aee10-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="aee10-181">L’indexation de tableau et la syntaxe de découpage sont prises en charge pour les tableaux jusqu’au rang 4.</span><span class="sxs-lookup"><span data-stu-id="aee10-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="aee10-182">Lorsque vous spécifiez un index dans plusieurs dimensions, vous utilisez des virgules pour séparer les index, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="aee10-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="aee10-183">Le type d’un tableau à deux dimensions est écrit sous la forme `<type>[,]` (par exemple, `int[,]` , `double[,]` ), et le type d’un tableau à trois dimensions est écrit `<type>[,,]` , et ainsi de suite pour les tableaux de dimensions supérieures.</span><span class="sxs-lookup"><span data-stu-id="aee10-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="aee10-184">Seul un sous-ensemble des fonctions disponibles pour les tableaux unidimensionnels est également disponible pour les tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="aee10-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="aee10-185">Découpage de tableau et tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="aee10-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="aee10-186">Dans un tableau à deux dimensions (une matrice), vous pouvez extraire une sous-matrice en spécifiant des plages et en utilisant un caractère générique ( `*` ) pour spécifier des lignes ou des colonnes entières.</span><span class="sxs-lookup"><span data-stu-id="aee10-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="aee10-187">Vous pouvez décomposer un tableau multidimensionnel en sous-tableaux de la même dimension ou de la même dimension inférieure.</span><span class="sxs-lookup"><span data-stu-id="aee10-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="aee10-188">Par exemple, vous pouvez obtenir un vecteur à partir d’une matrice en spécifiant une seule ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="aee10-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="aee10-189">Vous pouvez utiliser cette syntaxe de découpage pour les types qui implémentent les opérateurs d’accès aux éléments et les méthodes surchargées `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="aee10-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="aee10-190">Par exemple, le code suivant crée un type de matrice qui encapsule le tableau F # 2D, implémente une propriété d’élément pour assurer la prise en charge de l’indexation de tableau et implémente trois versions de `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="aee10-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="aee10-191">Si vous pouvez utiliser ce code comme modèle pour vos types de matrices, vous pouvez utiliser toutes les opérations de découpage décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="aee10-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="aee10-192">Fonctions booléennes sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-192">Boolean functions on arrays</span></span>

<span data-ttu-id="aee10-193">Les fonctions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) et les [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) éléments de test dans un ou deux tableaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="aee10-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="aee10-194">Ces fonctions prennent une fonction de test et retournent `true` s’il existe un élément (ou une paire d’éléments pour `Array.exists2` ) qui satisfait à la condition.</span><span class="sxs-lookup"><span data-stu-id="aee10-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="aee10-195">Le code suivant illustre l’utilisation de `Array.exists` et de `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="aee10-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="aee10-196">Dans ces exemples, de nouvelles fonctions sont créées en appliquant un seul des arguments, dans ce cas, l’argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="aee10-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="aee10-197">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="aee10-198">De même, la fonction [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) teste un tableau pour déterminer si chaque élément remplit une condition booléenne.</span><span class="sxs-lookup"><span data-stu-id="aee10-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="aee10-199">La variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) fait la même chose à l’aide d’une fonction booléenne qui implique des éléments de deux tableaux de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="aee10-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="aee10-200">Le code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="aee10-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="aee10-201">La sortie de ces exemples est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="aee10-202">Rechercher dans les tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-202">Search arrays</span></span>

<span data-ttu-id="aee10-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) prend une fonction booléenne et retourne le premier élément pour lequel la fonction retourne `true` , ou lève une <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> si aucun élément répondant à la condition n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="aee10-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="aee10-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) est semblable `Array.find` à, à ceci près qu’elle retourne l’index de l’élément au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="aee10-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="aee10-205">Le code suivant utilise `Array.find` et `Array.findIndex` pour localiser un nombre qui est à la fois un carré parfait et un cube parfait.</span><span class="sxs-lookup"><span data-stu-id="aee10-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="aee10-206">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="aee10-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) est semblable `Array.find` à, à ceci près que son résultat est un type d’option et qu’il retourne `None` si aucun élément n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="aee10-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="aee10-208">`Array.tryFind` doit être utilisé au lieu de `Array.find` lorsque vous ne savez pas si un élément correspondant se trouve dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="aee10-209">De même, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) est semblable `Array.findIndex` à, à ceci près que le type d’option est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="aee10-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="aee10-210">Si aucun élément n’est trouvé, l’option est `None` .</span><span class="sxs-lookup"><span data-stu-id="aee10-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="aee10-211">Le code suivant montre l'utilisation de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="aee10-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="aee10-212">Ce code dépend du code précédent.</span><span class="sxs-lookup"><span data-stu-id="aee10-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="aee10-213">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="aee10-214">Utilisez [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) lorsque vous devez transformer un élément en plus de le trouver.</span><span class="sxs-lookup"><span data-stu-id="aee10-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="aee10-215">Le résultat est le premier élément pour lequel la fonction retourne l’élément transformé comme valeur d’option, ou `None` si aucun élément de ce type n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="aee10-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="aee10-216">Le code suivant illustre l'utilisation de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="aee10-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="aee10-217">Dans ce cas, au lieu d’une expression lambda, plusieurs fonctions d’assistance locales sont définies pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="aee10-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="aee10-218">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="aee10-219">Effectuer des calculs sur des tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-219">Perform computations on arrays</span></span>

<span data-ttu-id="aee10-220">La [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) fonction retourne la moyenne de chaque élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="aee10-221">Elle est limitée aux types d’éléments qui prennent en charge la Division exacte par un entier, ce qui comprend les types à virgule flottante, mais pas les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="aee10-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="aee10-222">La [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) fonction retourne la moyenne des résultats de l’appel d’une fonction sur chaque élément.</span><span class="sxs-lookup"><span data-stu-id="aee10-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="aee10-223">Pour un tableau de type intégral, vous pouvez utiliser `Array.averageBy` et faire en sorte que la fonction convertisse chaque élément en type à virgule flottante pour le calcul.</span><span class="sxs-lookup"><span data-stu-id="aee10-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="aee10-224">Utilisez [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) ou [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) pour accéder à l’élément maximal ou minimal, si le type d’élément le prend en charge.</span><span class="sxs-lookup"><span data-stu-id="aee10-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="aee10-225">De même, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) et [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) autorisent l’exécution d’une fonction en premier, peut-être à transformer en un type qui prend en charge la comparaison.</span><span class="sxs-lookup"><span data-stu-id="aee10-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="aee10-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Ajoute les éléments d’un tableau et [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) appelle une fonction sur chaque élément et ajoute les résultats ensemble.</span><span class="sxs-lookup"><span data-stu-id="aee10-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="aee10-227">Pour exécuter une fonction sur chaque élément d’un tableau sans stocker les valeurs de retour, utilisez [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) .</span><span class="sxs-lookup"><span data-stu-id="aee10-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="aee10-228">Pour une fonction qui implique deux tableaux de longueur égale, utilisez [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) .</span><span class="sxs-lookup"><span data-stu-id="aee10-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="aee10-229">Si vous devez également conserver un tableau des résultats de la fonction, utilisez [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) ou [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , qui opère sur deux tableaux à la fois.</span><span class="sxs-lookup"><span data-stu-id="aee10-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="aee10-230">Les variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) et [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) permettent à l’index de l’élément d’être impliqué dans le calcul. il en va de même pour [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) et [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .</span><span class="sxs-lookup"><span data-stu-id="aee10-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="aee10-231">Les fonctions,,,, [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) et [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) exécutent des algorithmes qui impliquent tous les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="aee10-232">De même, les variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) et [`Array.foldBack2`](foldBack2) effectuent des calculs sur deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="aee10-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="aee10-233">Ces fonctions pour effectuer des calculs correspondent aux fonctions du même nom dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="aee10-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="aee10-234">Pour obtenir des exemples d’utilisation, consultez [listes](lists.md).</span><span class="sxs-lookup"><span data-stu-id="aee10-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="aee10-235">Modifier des tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-235">Modify arrays</span></span>

<span data-ttu-id="aee10-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) affecte une valeur spécifiée à un élément.</span><span class="sxs-lookup"><span data-stu-id="aee10-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="aee10-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) affecte une valeur spécifiée à une plage d’éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="aee10-238">Le code suivant fournit un exemple de `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="aee10-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="aee10-239">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="aee10-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="aee10-240">Vous pouvez utiliser [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) pour copier une sous-section d’un tableau dans un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="aee10-241">Convertir en et à partir d’autres types</span><span class="sxs-lookup"><span data-stu-id="aee10-241">Convert to and from other types</span></span>

<span data-ttu-id="aee10-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) crée un tableau à partir d’une liste.</span><span class="sxs-lookup"><span data-stu-id="aee10-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="aee10-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) crée un tableau à partir d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="aee10-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="aee10-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) et sont [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convertis en ces autres types de collection à partir du type de tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="aee10-245">Trier les tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-245">Sort arrays</span></span>

<span data-ttu-id="aee10-246">Utilisez [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) pour trier un tableau à l’aide de la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="aee10-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="aee10-247">Utilisez [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) pour spécifier une fonction qui génère une valeur, appelée *clé*, à trier à l’aide de la fonction de comparaison générique sur la clé.</span><span class="sxs-lookup"><span data-stu-id="aee10-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="aee10-248">Utilisez [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) si vous souhaitez fournir une fonction de comparaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="aee10-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="aee10-249">`Array.sort`, `Array.sortBy` et `Array.sortWith` retournent tous le tableau trié sous la forme d’un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="aee10-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="aee10-250">Les variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) et [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modifient le tableau existant au lieu de retourner un nouveau.</span><span class="sxs-lookup"><span data-stu-id="aee10-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="aee10-251">Tableaux et tuples</span><span class="sxs-lookup"><span data-stu-id="aee10-251">Arrays and tuples</span></span>

<span data-ttu-id="aee10-252">Les fonctions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) et [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convertissent les tableaux de paires de tuples en tuples de tableaux, et vice versa.</span><span class="sxs-lookup"><span data-stu-id="aee10-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="aee10-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) et [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) sont similaires, à ceci près qu’ils fonctionnent avec des tuples de trois éléments ou des tuples de trois tableaux.</span><span class="sxs-lookup"><span data-stu-id="aee10-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="aee10-254">Calculs parallèles sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="aee10-254">Parallel computations on arrays</span></span>

<span data-ttu-id="aee10-255">Le module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contient des fonctions permettant d’effectuer des calculs parallèles sur des tableaux.</span><span class="sxs-lookup"><span data-stu-id="aee10-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="aee10-256">Ce module n’est pas disponible dans les applications qui ciblent les versions de .NET Framework antérieures à la version 4.</span><span class="sxs-lookup"><span data-stu-id="aee10-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="aee10-257">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aee10-257">See also</span></span>

- [<span data-ttu-id="aee10-258">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="aee10-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="aee10-259">Types F#</span><span class="sxs-lookup"><span data-stu-id="aee10-259">F# Types</span></span>](fsharp-types.md)

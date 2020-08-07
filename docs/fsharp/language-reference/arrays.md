---
title: Tableaux
description: 'Découvrez comment créer et utiliser des tableaux dans le langage de programmation F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f95ca3274e098fda044973a48205cb591ec30b27
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855606"
---
# <a name="arrays"></a><span data-ttu-id="4c94c-103">Tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-103">Arrays</span></span>

<span data-ttu-id="4c94c-104">Les tableaux sont des collections de taille fixe, de base zéro et mutables d’éléments de données consécutifs qui sont tous du même type.</span><span class="sxs-lookup"><span data-stu-id="4c94c-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

> [!NOTE]
> <span data-ttu-id="4c94c-105">La référence de l’API docs.microsoft.com pour F # n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="4c94c-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="4c94c-106">Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="4c94c-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="4c94c-107">Créer des tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-107">Create arrays</span></span>

<span data-ttu-id="4c94c-108">Vous pouvez créer des tableaux de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="4c94c-108">You can create arrays in several ways.</span></span> <span data-ttu-id="4c94c-109">Vous pouvez créer un petit tableau en répertoriant des valeurs consécutives entre `[|` et `|]` et séparées par des points-virgules, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="4c94c-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="4c94c-110">Vous pouvez également placer chaque élément sur une ligne distincte, auquel cas le séparateur de points-virgules est facultatif.</span><span class="sxs-lookup"><span data-stu-id="4c94c-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="4c94c-111">Le type des éléments du tableau est déduit des littéraux utilisés et doit être cohérent.</span><span class="sxs-lookup"><span data-stu-id="4c94c-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="4c94c-112">Le code suivant génère une erreur, car 1,0 est de type float et 2 et 3 sont des entiers.</span><span class="sxs-lookup"><span data-stu-id="4c94c-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="4c94c-113">Vous pouvez également utiliser des expressions de séquence pour créer des tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="4c94c-114">Voici un exemple qui crée un tableau de carrés d’entiers de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="4c94c-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="4c94c-115">Pour créer un tableau dans lequel tous les éléments sont initialisés à zéro, utilisez `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="4c94c-116">Éléments d’accès</span><span class="sxs-lookup"><span data-stu-id="4c94c-116">Access elements</span></span>

<span data-ttu-id="4c94c-117">Vous pouvez accéder aux éléments de tableau à l’aide d’un opérateur point ( `.` ) et de crochets ( `[` et `]` ).</span><span class="sxs-lookup"><span data-stu-id="4c94c-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="4c94c-118">Les index de tableau commencent à 0.</span><span class="sxs-lookup"><span data-stu-id="4c94c-118">Array indexes start at 0.</span></span>

<span data-ttu-id="4c94c-119">Vous pouvez également accéder aux éléments de tableau à l’aide de la notation de découpage, qui vous permet de spécifier une sous-plage du tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="4c94c-120">Voici des exemples de notation de découpage.</span><span class="sxs-lookup"><span data-stu-id="4c94c-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="4c94c-121">Lorsque la notation par segment est utilisée, une nouvelle copie du tableau est créée.</span><span class="sxs-lookup"><span data-stu-id="4c94c-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="4c94c-122">Modules et types de tableau</span><span class="sxs-lookup"><span data-stu-id="4c94c-122">Array types and modules</span></span>

<span data-ttu-id="4c94c-123">Le type de tous les tableaux F # est le type de .NET Framework <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4c94c-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4c94c-124">Par conséquent, les tableaux F # prennent en charge toutes les fonctionnalités disponibles dans <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4c94c-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="4c94c-125">Le module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) de bibliothèque prend en charge les opérations sur les tableaux unidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="4c94c-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="4c94c-126">Les modules `Array2D` , `Array3D` et `Array4D` contiennent des fonctions qui prennent en charge les opérations sur les tableaux de deux, trois et quatre dimensions, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4c94c-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="4c94c-127">Vous pouvez créer des tableaux de rang supérieur à quatre à l’aide de <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="4c94c-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="4c94c-128">Fonctions simples</span><span class="sxs-lookup"><span data-stu-id="4c94c-128">Simple functions</span></span>

<span data-ttu-id="4c94c-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Obtient un élément.</span><span class="sxs-lookup"><span data-stu-id="4c94c-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="4c94c-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)donne la longueur d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="4c94c-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)affecte une valeur spécifiée à un élément.</span><span class="sxs-lookup"><span data-stu-id="4c94c-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="4c94c-132">L’exemple de code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="4c94c-133">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-133">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="4c94c-134">Fonctions qui créent des tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-134">Functions that create arrays</span></span>

<span data-ttu-id="4c94c-135">Plusieurs fonctions créent des tableaux sans nécessiter de tableau existant.</span><span class="sxs-lookup"><span data-stu-id="4c94c-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="4c94c-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)crée un tableau qui ne contient aucun élément.</span><span class="sxs-lookup"><span data-stu-id="4c94c-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="4c94c-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)crée un tableau d’une taille spécifiée et définit tous les éléments sur les valeurs fournies.</span><span class="sxs-lookup"><span data-stu-id="4c94c-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="4c94c-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)crée un tableau, en fonction d’une dimension et d’une fonction pour générer les éléments.</span><span class="sxs-lookup"><span data-stu-id="4c94c-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="4c94c-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)crée un tableau dans lequel tous les éléments sont initialisés à la valeur zéro pour le type du tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="4c94c-140">Le code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="4c94c-141">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-141">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="4c94c-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)crée un tableau qui contient des éléments copiés à partir d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="4c94c-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="4c94c-143">Notez que la copie est une copie superficielle, ce qui signifie que si le type d’élément est un type référence, seule la référence est copiée, et non l’objet sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="4c94c-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="4c94c-144">L'exemple de code suivant illustre ceci.</span><span class="sxs-lookup"><span data-stu-id="4c94c-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="4c94c-145">La sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4c94c-145">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="4c94c-146">La chaîne `Test1` apparaît uniquement dans le premier tableau, car l’opération de création d’un nouvel élément remplace la référence dans, `firstArray` mais n’affecte pas la référence d’origine à une chaîne vide qui est encore présente dans `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="4c94c-147">La chaîne `Test2` apparaît dans les deux tableaux, car l' `Insert` opération sur le <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affecte l’objet sous-jacent <xref:System.Text.StringBuilder?displayProperty=nameWithType> , qui est référencé dans les deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="4c94c-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)génère un nouveau tableau à partir d’une sous-plage d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="4c94c-149">Vous spécifiez la sous-plage en fournissant l’index de départ et la longueur.</span><span class="sxs-lookup"><span data-stu-id="4c94c-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="4c94c-150">Le code suivant montre l'utilisation de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="4c94c-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="4c94c-151">La sortie indique que le sous-tableau commence à l’élément 5 et contient 10 éléments.</span><span class="sxs-lookup"><span data-stu-id="4c94c-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="4c94c-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)crée un tableau en combinant deux tableaux existants.</span><span class="sxs-lookup"><span data-stu-id="4c94c-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="4c94c-153">Le code suivant illustre **Array. Append**.</span><span class="sxs-lookup"><span data-stu-id="4c94c-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="4c94c-154">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-154">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="4c94c-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)sélectionne les éléments d’un tableau à inclure dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="4c94c-156">Le code suivant illustre `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="4c94c-157">Notez que le type d’élément du tableau ne doit pas nécessairement correspondre au type de la valeur retournée dans le type d’option.</span><span class="sxs-lookup"><span data-stu-id="4c94c-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="4c94c-158">Dans cet exemple, le type d’élément est `int` et l’option est le résultat d’une fonction polynomiale, `elem*elem - 1` , sous la forme d’un nombre à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="4c94c-159">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-159">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="4c94c-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)exécute une fonction spécifiée sur chaque élément de tableau d’un tableau existant, puis collecte les éléments générés par la fonction et les combine dans un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="4c94c-161">Le code suivant illustre `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="4c94c-162">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-162">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="4c94c-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)prend une séquence de tableaux et les combine en un seul tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="4c94c-164">Le code suivant illustre `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="4c94c-165">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-165">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="4c94c-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)prend une fonction de condition booléenne et génère un nouveau tableau qui contient uniquement les éléments du tableau d’entrée pour lesquels la condition a la valeur true.</span><span class="sxs-lookup"><span data-stu-id="4c94c-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="4c94c-167">Le code suivant illustre `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="4c94c-168">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-168">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="4c94c-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)génère un nouveau tableau en inversant l’ordre d’un tableau existant.</span><span class="sxs-lookup"><span data-stu-id="4c94c-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="4c94c-170">Le code suivant illustre `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="4c94c-171">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-171">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="4c94c-172">Vous pouvez facilement combiner des fonctions dans le module de tableau qui transforment des tableaux à l’aide de l’opérateur de pipeline ( `|>` ), comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="4c94c-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="4c94c-173">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="4c94c-173">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="4c94c-174">Tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="4c94c-174">Multidimensional arrays</span></span>

<span data-ttu-id="4c94c-175">Un tableau multidimensionnel peut être créé, mais il n’existe aucune syntaxe pour l’écriture d’un littéral de tableau multidimensionnel.</span><span class="sxs-lookup"><span data-stu-id="4c94c-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="4c94c-176">Utilisez l’opérateur [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) pour créer un tableau à partir d’une séquence de séquences d’éléments de tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="4c94c-177">Les séquences peuvent être des littéraux de liste ou de tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="4c94c-178">Par exemple, le code suivant crée un tableau à deux dimensions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="4c94c-179">Vous pouvez également utiliser la fonction [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) pour initialiser des tableaux de deux dimensions, et des fonctions similaires sont disponibles pour les tableaux de trois et quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="4c94c-180">Ces fonctions prennent une fonction qui est utilisée pour créer les éléments.</span><span class="sxs-lookup"><span data-stu-id="4c94c-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="4c94c-181">Pour créer un tableau à deux dimensions qui contient des éléments définis sur une valeur initiale au lieu de spécifier une fonction, utilisez la [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) fonction, qui est également disponible pour les tableaux jusqu’à quatre dimensions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="4c94c-182">L’exemple de code suivant montre d’abord comment créer un tableau de tableaux qui contiennent les éléments souhaités, puis utilise `Array2D.init` pour générer le tableau à deux dimensions souhaité.</span><span class="sxs-lookup"><span data-stu-id="4c94c-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="4c94c-183">L’indexation de tableau et la syntaxe de découpage sont prises en charge pour les tableaux jusqu’au rang 4.</span><span class="sxs-lookup"><span data-stu-id="4c94c-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="4c94c-184">Lorsque vous spécifiez un index dans plusieurs dimensions, vous utilisez des virgules pour séparer les index, comme illustré dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="4c94c-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="4c94c-185">Le type d’un tableau à deux dimensions est écrit sous la forme `<type>[,]` (par exemple, `int[,]` , `double[,]` ), et le type d’un tableau à trois dimensions est écrit `<type>[,,]` , et ainsi de suite pour les tableaux de dimensions supérieures.</span><span class="sxs-lookup"><span data-stu-id="4c94c-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="4c94c-186">Seul un sous-ensemble des fonctions disponibles pour les tableaux unidimensionnels est également disponible pour les tableaux multidimensionnels.</span><span class="sxs-lookup"><span data-stu-id="4c94c-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="4c94c-187">Pour plus d’informations, consultez [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d) ,, [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d) [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d) et [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d) .</span><span class="sxs-lookup"><span data-stu-id="4c94c-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="4c94c-188">Découpage de tableau et tableaux multidimensionnels</span><span class="sxs-lookup"><span data-stu-id="4c94c-188">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="4c94c-189">Dans un tableau à deux dimensions (une matrice), vous pouvez extraire une sous-matrice en spécifiant des plages et en utilisant un caractère générique ( `*` ) pour spécifier des lignes ou des colonnes entières.</span><span class="sxs-lookup"><span data-stu-id="4c94c-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="4c94c-190">À compter de F # 3,1, vous pouvez décomposer un tableau multidimensionnel en sous-tableaux de la même dimension ou de la même dimension inférieure.</span><span class="sxs-lookup"><span data-stu-id="4c94c-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="4c94c-191">Par exemple, vous pouvez obtenir un vecteur à partir d’une matrice en spécifiant une seule ligne ou colonne.</span><span class="sxs-lookup"><span data-stu-id="4c94c-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="4c94c-192">Vous pouvez utiliser cette syntaxe de découpage pour les types qui implémentent les opérateurs d’accès aux éléments et les méthodes surchargées `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="4c94c-193">Par exemple, le code suivant crée un type de matrice qui encapsule le tableau F # 2D, implémente une propriété d’élément pour assurer la prise en charge de l’indexation de tableau et implémente trois versions de `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="4c94c-194">Si vous pouvez utiliser ce code comme modèle pour vos types de matrices, vous pouvez utiliser toutes les opérations de découpage décrites dans cette section.</span><span class="sxs-lookup"><span data-stu-id="4c94c-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="4c94c-195">Fonctions booléennes sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-195">Boolean functions on arrays</span></span>

<span data-ttu-id="4c94c-196">Les fonctions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) et les [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) éléments de test dans un ou deux tableaux, respectivement.</span><span class="sxs-lookup"><span data-stu-id="4c94c-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="4c94c-197">Ces fonctions prennent une fonction de test et retournent `true` s’il existe un élément (ou une paire d’éléments pour `Array.exists2` ) qui satisfait à la condition.</span><span class="sxs-lookup"><span data-stu-id="4c94c-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="4c94c-198">Le code suivant illustre l’utilisation de `Array.exists` et de `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="4c94c-199">Dans ces exemples, de nouvelles fonctions sont créées en appliquant un seul des arguments, dans ce cas, l’argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="4c94c-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="4c94c-200">La sortie du code précédent est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-200">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="4c94c-201">De même, la fonction [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) teste un tableau pour déterminer si chaque élément remplit une condition booléenne.</span><span class="sxs-lookup"><span data-stu-id="4c94c-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="4c94c-202">La variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) fait la même chose à l’aide d’une fonction booléenne qui implique des éléments de deux tableaux de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="4c94c-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="4c94c-203">Le code suivant illustre l’utilisation de ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="4c94c-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="4c94c-204">La sortie de ces exemples est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-204">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="4c94c-205">Rechercher dans les tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-205">Search arrays</span></span>

<span data-ttu-id="4c94c-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)prend une fonction booléenne et retourne le premier élément pour lequel la fonction retourne `true` , ou lève une <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> si aucun élément répondant à la condition n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="4c94c-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="4c94c-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)est semblable `Array.find` à, à ceci près qu’elle retourne l’index de l’élément au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="4c94c-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="4c94c-208">Le code suivant utilise `Array.find` et `Array.findIndex` pour localiser un nombre qui est à la fois un carré parfait et un cube parfait.</span><span class="sxs-lookup"><span data-stu-id="4c94c-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="4c94c-209">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-209">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="4c94c-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)est semblable `Array.find` à, à ceci près que son résultat est un type d’option et qu’il retourne `None` si aucun élément n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="4c94c-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="4c94c-211">`Array.tryFind`doit être utilisé au lieu de `Array.find` lorsque vous ne savez pas si un élément correspondant se trouve dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="4c94c-212">De même, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) est semblable [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) à, à ceci près que le type d’option est la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="4c94c-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="4c94c-213">Si aucun élément n’est trouvé, l’option est `None` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="4c94c-214">Le code suivant montre l'utilisation de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="4c94c-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="4c94c-215">Ce code dépend du code précédent.</span><span class="sxs-lookup"><span data-stu-id="4c94c-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="4c94c-216">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-216">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="4c94c-217">Utilisez [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) lorsque vous devez transformer un élément en plus de le trouver.</span><span class="sxs-lookup"><span data-stu-id="4c94c-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="4c94c-218">Le résultat est le premier élément pour lequel la fonction retourne l’élément transformé comme valeur d’option, ou `None` si aucun élément de ce type n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="4c94c-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="4c94c-219">Le code suivant illustre l'utilisation de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="4c94c-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="4c94c-220">Dans ce cas, au lieu d’une expression lambda, plusieurs fonctions d’assistance locales sont définies pour simplifier le code.</span><span class="sxs-lookup"><span data-stu-id="4c94c-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="4c94c-221">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-221">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="4c94c-222">Effectuer des calculs sur des tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-222">Perform computations on arrays</span></span>

<span data-ttu-id="4c94c-223">La [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) fonction retourne la moyenne de chaque élément d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="4c94c-224">Elle est limitée aux types d’éléments qui prennent en charge la Division exacte par un entier, ce qui comprend les types à virgule flottante, mais pas les types intégraux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="4c94c-225">La [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) fonction retourne la moyenne des résultats de l’appel d’une fonction sur chaque élément.</span><span class="sxs-lookup"><span data-stu-id="4c94c-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="4c94c-226">Pour un tableau de type intégral, vous pouvez utiliser `Array.averageBy` et faire en sorte que la fonction convertisse chaque élément en type à virgule flottante pour le calcul.</span><span class="sxs-lookup"><span data-stu-id="4c94c-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="4c94c-227">Utilisez [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) ou [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) pour accéder à l’élément maximal ou minimal, si le type d’élément le prend en charge.</span><span class="sxs-lookup"><span data-stu-id="4c94c-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="4c94c-228">De même, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) et [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) autorisent l’exécution d’une fonction en premier, peut-être à transformer en un type qui prend en charge la comparaison.</span><span class="sxs-lookup"><span data-stu-id="4c94c-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="4c94c-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)Ajoute les éléments d’un tableau et [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) appelle une fonction sur chaque élément et ajoute les résultats ensemble.</span><span class="sxs-lookup"><span data-stu-id="4c94c-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="4c94c-230">Pour exécuter une fonction sur chaque élément d’un tableau sans stocker les valeurs de retour, utilisez [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516) .</span><span class="sxs-lookup"><span data-stu-id="4c94c-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="4c94c-231">Pour une fonction qui implique deux tableaux de longueur égale, utilisez [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc) .</span><span class="sxs-lookup"><span data-stu-id="4c94c-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="4c94c-232">Si vous devez également conserver un tableau des résultats de la fonction, utilisez [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) ou [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c) , qui opère sur deux tableaux à la fois.</span><span class="sxs-lookup"><span data-stu-id="4c94c-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="4c94c-233">Les variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) et [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) permettent à l’index de l’élément d’être impliqué dans le calcul. il en va de même pour [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) et [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0) .</span><span class="sxs-lookup"><span data-stu-id="4c94c-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="4c94c-234">Les fonctions,,,, [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09) [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c) [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d) [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0) et [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) exécutent des algorithmes qui impliquent tous les éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="4c94c-235">De même, les variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) et [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) effectuent des calculs sur deux tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="4c94c-236">Ces fonctions pour effectuer des calculs correspondent aux fonctions du même nom dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="4c94c-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="4c94c-237">Pour obtenir des exemples d’utilisation, consultez [listes](lists.md).</span><span class="sxs-lookup"><span data-stu-id="4c94c-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="4c94c-238">Modifier des tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-238">Modify arrays</span></span>

<span data-ttu-id="4c94c-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)affecte une valeur spécifiée à un élément.</span><span class="sxs-lookup"><span data-stu-id="4c94c-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="4c94c-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)affecte une valeur spécifiée à une plage d’éléments d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="4c94c-241">Le code suivant fournit un exemple de `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="4c94c-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="4c94c-242">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="4c94c-242">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="4c94c-243">Vous pouvez utiliser [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) pour copier une sous-section d’un tableau dans un autre tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="4c94c-244">Convertir en et à partir d’autres types</span><span class="sxs-lookup"><span data-stu-id="4c94c-244">Convert to and from other types</span></span>

<span data-ttu-id="4c94c-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)crée un tableau à partir d’une liste.</span><span class="sxs-lookup"><span data-stu-id="4c94c-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="4c94c-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)crée un tableau à partir d’une séquence.</span><span class="sxs-lookup"><span data-stu-id="4c94c-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="4c94c-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)et sont [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convertis en ces autres types de collection à partir du type de tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="4c94c-248">Trier les tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-248">Sort arrays</span></span>

<span data-ttu-id="4c94c-249">Utilisez [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) pour trier un tableau à l’aide de la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="4c94c-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="4c94c-250">Utilisez [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) pour spécifier une fonction qui génère une valeur, appelée *clé*, à trier à l’aide de la fonction de comparaison générique sur la clé.</span><span class="sxs-lookup"><span data-stu-id="4c94c-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="4c94c-251">Utilisez [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) si vous souhaitez fournir une fonction de comparaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4c94c-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="4c94c-252">`Array.sort`, `Array.sortBy` et `Array.sortWith` retournent tous le tableau trié sous la forme d’un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="4c94c-253">Les variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0) , [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f) et [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modifient le tableau existant au lieu de retourner un nouveau.</span><span class="sxs-lookup"><span data-stu-id="4c94c-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="4c94c-254">Tableaux et tuples</span><span class="sxs-lookup"><span data-stu-id="4c94c-254">Arrays and tuples</span></span>

<span data-ttu-id="4c94c-255">Les fonctions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) et [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convertissent les tableaux de paires de tuples en tuples de tableaux, et vice versa.</span><span class="sxs-lookup"><span data-stu-id="4c94c-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="4c94c-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)et [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) sont similaires, à ceci près qu’ils fonctionnent avec des tuples de trois éléments ou des tuples de trois tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="4c94c-257">Calculs parallèles sur les tableaux</span><span class="sxs-lookup"><span data-stu-id="4c94c-257">Parallel computations on arrays</span></span>

<span data-ttu-id="4c94c-258">Le module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contient des fonctions permettant d’effectuer des calculs parallèles sur des tableaux.</span><span class="sxs-lookup"><span data-stu-id="4c94c-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="4c94c-259">Ce module n’est pas disponible dans les applications qui ciblent les versions de .NET Framework antérieures à la version 4.</span><span class="sxs-lookup"><span data-stu-id="4c94c-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c94c-260">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c94c-260">See also</span></span>

- [<span data-ttu-id="4c94c-261">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="4c94c-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="4c94c-262">Types F#</span><span class="sxs-lookup"><span data-stu-id="4c94c-262">F# Types</span></span>](fsharp-types.md)

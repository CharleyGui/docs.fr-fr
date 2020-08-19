---
title: Listes
description: 'En savoir plus sur les listes F #, une série immuable et ordonnée d’éléments du même type.'
ms.date: 08/13/2020
ms.openlocfilehash: 16d7195039d25cf63630f5cc3be6563b1bf45c44
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559165"
---
# <a name="lists"></a><span data-ttu-id="b185e-103">Listes</span><span class="sxs-lookup"><span data-stu-id="b185e-103">Lists</span></span>

<span data-ttu-id="b185e-104">En F#, une liste est une série immuable et ordonnée d'éléments du même type.</span><span class="sxs-lookup"><span data-stu-id="b185e-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="b185e-105">Pour effectuer des opérations de base sur les listes, utilisez les fonctions dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="b185e-105">To perform basic operations on lists, use the functions in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="b185e-106">Création et initialisation de listes</span><span class="sxs-lookup"><span data-stu-id="b185e-106">Creating and Initializing Lists</span></span>

<span data-ttu-id="b185e-107">Vous pouvez définir une liste en répertoriant de manière explicite les éléments, séparés par des points-virgules et placés entre crochets, comme indiqué dans la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="b185e-107">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="b185e-108">Vous pouvez également insérer des sauts de ligne entre les éléments, les points-virgules étant facultatifs dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="b185e-108">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="b185e-109">Cette syntaxe produit du code plus lisible quand les expressions d'initialisation des éléments sont plus longues, ou quand vous souhaitez ajouter un commentaire pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-109">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="b185e-110">Généralement, tous les éléments de liste doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="b185e-110">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="b185e-111">Il existe une exception : une liste dont les éléments sont spécifiés comme type de base peut comporter des éléments qui sont des types dérivés.</span><span class="sxs-lookup"><span data-stu-id="b185e-111">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="b185e-112">L'exemple suivant est acceptable, car `Button` et `CheckBox` dérivent de `Control`.</span><span class="sxs-lookup"><span data-stu-id="b185e-112">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="b185e-113">Vous pouvez également définir des éléments de liste à l'aide d'une plage indiquée par des entiers séparés par l'opérateur de plage (`..`), comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b185e-113">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="b185e-114">Une liste vide est spécifiée par une paire de crochets vide.</span><span class="sxs-lookup"><span data-stu-id="b185e-114">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="b185e-115">Vous pouvez également utiliser une expression de séquence pour créer une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-115">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="b185e-116">Pour plus d’informations, consultez [expressions de séquence](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="b185e-116">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="b185e-117">Par exemple, le code suivant crée une liste d'entiers au carré, de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="b185e-117">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="b185e-118">Opérateurs utilisés avec les listes</span><span class="sxs-lookup"><span data-stu-id="b185e-118">Operators for Working with Lists</span></span>

<span data-ttu-id="b185e-119">Vous pouvez joindre des éléments à une liste en utilisant l'opérateur (cons) `::`.</span><span class="sxs-lookup"><span data-stu-id="b185e-119">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="b185e-120">Si `list1` est `[2; 3; 4]`, le code suivant crée `list2` sous la forme `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="b185e-120">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="b185e-121">Vous pouvez concaténer des listes qui présentent des types compatibles à l'aide de l'opérateur `@`, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b185e-121">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="b185e-122">Si `list1` est `[2; 3; 4]` et `list2` est `[100; 2; 3; 4]`, ce code crée `list3` sous la forme `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="b185e-122">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="b185e-123">Les fonctions permettant d’effectuer des opérations sur des listes sont disponibles dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="b185e-123">Functions for performing operations on lists are available in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

<span data-ttu-id="b185e-124">En F#, les listes étant immuables, toute opération de changement a pour effet de générer de nouvelles listes au lieu de modifier les listes existantes.</span><span class="sxs-lookup"><span data-stu-id="b185e-124">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="b185e-125">Les listes en F # sont implémentées en tant que listes à liaison unique, ce qui signifie que les opérations qui accèdent uniquement au début de la liste sont O (1) et que l’accès à l’élément est O (*n*).</span><span class="sxs-lookup"><span data-stu-id="b185e-125">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="b185e-126">Propriétés</span><span class="sxs-lookup"><span data-stu-id="b185e-126">Properties</span></span>

<span data-ttu-id="b185e-127">Le type de liste prend en charge les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="b185e-127">The list type supports the following properties:</span></span>

|<span data-ttu-id="b185e-128">Propriété</span><span class="sxs-lookup"><span data-stu-id="b185e-128">Property</span></span>|<span data-ttu-id="b185e-129">Type</span><span class="sxs-lookup"><span data-stu-id="b185e-129">Type</span></span>|<span data-ttu-id="b185e-130">Description</span><span class="sxs-lookup"><span data-stu-id="b185e-130">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="b185e-131">Siège</span><span class="sxs-lookup"><span data-stu-id="b185e-131">Head</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|<span data-ttu-id="b185e-132">Premier élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-132">The first element.</span></span>|
|[<span data-ttu-id="b185e-133">Vide</span><span class="sxs-lookup"><span data-stu-id="b185e-133">Empty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|<span data-ttu-id="b185e-134">Propriété statique qui retourne une liste vide du type approprié.</span><span class="sxs-lookup"><span data-stu-id="b185e-134">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="b185e-135">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="b185e-135">IsEmpty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|<span data-ttu-id="b185e-136">`true` si la liste ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-136">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="b185e-137">Item</span><span class="sxs-lookup"><span data-stu-id="b185e-137">Item</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|<span data-ttu-id="b185e-138">Élément au niveau de l'index spécifié (de base zéro).</span><span class="sxs-lookup"><span data-stu-id="b185e-138">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="b185e-139">Longueur</span><span class="sxs-lookup"><span data-stu-id="b185e-139">Length</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|<span data-ttu-id="b185e-140">Nombre d'éléments.</span><span class="sxs-lookup"><span data-stu-id="b185e-140">The number of elements.</span></span>|
|[<span data-ttu-id="b185e-141">Tail</span><span class="sxs-lookup"><span data-stu-id="b185e-141">Tail</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|<span data-ttu-id="b185e-142">Liste sans premier élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-142">The list without the first element.</span></span>|

<span data-ttu-id="b185e-143">Voici quelques exemples d'utilisation de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="b185e-143">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="b185e-144">Utilisation de listes</span><span class="sxs-lookup"><span data-stu-id="b185e-144">Using Lists</span></span>

<span data-ttu-id="b185e-145">La programmation à l'aide de listes vous permet d'effectuer des opérations complexes avec peu de code.</span><span class="sxs-lookup"><span data-stu-id="b185e-145">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="b185e-146">Cette section décrit des opérations courantes sur des listes qui sont importantes pour la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="b185e-146">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="b185e-147">Récursivité avec des listes</span><span class="sxs-lookup"><span data-stu-id="b185e-147">Recursion with Lists</span></span>

<span data-ttu-id="b185e-148">Les listes sont particulièrement adaptées aux techniques de programmation récursive.</span><span class="sxs-lookup"><span data-stu-id="b185e-148">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="b185e-149">Prenons en compte une opération à effectuer sur chaque élément d'une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-149">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="b185e-150">Vous pouvez procéder de manière récursive en effectuant l'opération sur le début de la liste, puis en passant à la fin de la liste, qui est une liste plus petite comprenant la liste d'origine sans le premier élément, et en revenant au niveau suivant de récursivité.</span><span class="sxs-lookup"><span data-stu-id="b185e-150">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="b185e-151">Pour écrire ce type de fonction récursive, utilisez l’opérateur cons (`::`) dans les critères spéciaux, qui vous permet de séparer le début d’une liste de sa fin.</span><span class="sxs-lookup"><span data-stu-id="b185e-151">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="b185e-152">L’exemple de code suivant indique comment utiliser les critères spéciaux pour implémenter une fonction récursive qui exécute des opérations sur une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-152">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="b185e-153">Le code précédent fonctionne bien dans le cas de petites listes, mais dans le cas de listes plus longues, il peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="b185e-153">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="b185e-154">Le code suivant améliore le précédent à l’aide d’un argument d’accumulation, technique standard utilisée avec les fonctions récursives.</span><span class="sxs-lookup"><span data-stu-id="b185e-154">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="b185e-155">L'argument d'accumulation rend la fin de la fonction récursive, ce qui permet de contenir l'espace de pile.</span><span class="sxs-lookup"><span data-stu-id="b185e-155">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="b185e-156">La fonction `RemoveAllMultiples` est récursive et accepte deux listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-156">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="b185e-157">La première liste contient les nombres dont les multiples seront supprimés ; la seconde liste contient les nombres à supprimer.</span><span class="sxs-lookup"><span data-stu-id="b185e-157">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="b185e-158">Le code de l’exemple suivant utilise cette fonction récursive pour éliminer tous les nombres non premiers d’une liste, générant ainsi une liste de nombres premiers.</span><span class="sxs-lookup"><span data-stu-id="b185e-158">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="b185e-159">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-159">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="b185e-160">Fonctions de module</span><span class="sxs-lookup"><span data-stu-id="b185e-160">Module Functions</span></span>

<span data-ttu-id="b185e-161">Le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) fournit des fonctions qui accèdent aux éléments d’une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-161">The [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) provides functions that access the elements of a list.</span></span> <span data-ttu-id="b185e-162">L'élément de début offre l'accès le plus simple et rapide.</span><span class="sxs-lookup"><span data-stu-id="b185e-162">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="b185e-163">Utilisez l' [en-tête](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) de propriété ou la fonction de module [List. Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span><span class="sxs-lookup"><span data-stu-id="b185e-163">Use the property [Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) or the module function [List.head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span></span> <span data-ttu-id="b185e-164">Vous pouvez accéder à la fin d’une liste à l’aide de la propriété [tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) ou de la fonction [List. tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) .</span><span class="sxs-lookup"><span data-stu-id="b185e-164">You can access the tail of a list by using the [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) property or the [List.tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) function.</span></span> <span data-ttu-id="b185e-165">Pour rechercher un élément par index, utilisez la fonction [List. nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) .</span><span class="sxs-lookup"><span data-stu-id="b185e-165">To find an element by index, use the [List.nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) function.</span></span> <span data-ttu-id="b185e-166">`List.nth` parcourt la liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-166">`List.nth` traverses the list.</span></span> <span data-ttu-id="b185e-167">Par conséquent, il s’agit de O (*n*).</span><span class="sxs-lookup"><span data-stu-id="b185e-167">Therefore, it is O(*n*).</span></span> <span data-ttu-id="b185e-168">Si votre code utilise fréquemment `List.nth`, envisagez d'utiliser un tableau à la place d'une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-168">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="b185e-169">L'accès aux éléments des tableaux est O(1).</span><span class="sxs-lookup"><span data-stu-id="b185e-169">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="b185e-170">Opérations booléennes sur des listes</span><span class="sxs-lookup"><span data-stu-id="b185e-170">Boolean Operations on Lists</span></span>

<span data-ttu-id="b185e-171">La fonction [List. IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) détermine si une liste contient des éléments.</span><span class="sxs-lookup"><span data-stu-id="b185e-171">The [List.isEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) function determines whether a list has any elements.</span></span>

<span data-ttu-id="b185e-172">La fonction [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) applique un test booléen aux éléments d’une liste et retourne `true` si un élément satisfait au test.</span><span class="sxs-lookup"><span data-stu-id="b185e-172">The [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="b185e-173">[List. exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) est similaire, mais fonctionne sur des paires d’éléments successifs dans deux listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-173">[List.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="b185e-174">Le code suivant montre l'utilisation de `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="b185e-174">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="b185e-175">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-175">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="b185e-176">L'exemple suivant montre l'utilisation de `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="b185e-176">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="b185e-177">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-177">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="b185e-178">Vous pouvez utiliser [List. forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) si vous souhaitez tester si tous les éléments d’une liste remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="b185e-178">You can use [List.forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="b185e-179">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-179">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="b185e-180">De même, [List. forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) détermine si tous les éléments des positions correspondantes dans deux listes satisfont à une expression booléenne qui implique chaque paire d’éléments.</span><span class="sxs-lookup"><span data-stu-id="b185e-180">Similarly, [List.forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="b185e-181">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-181">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="b185e-182">Opérations de tri sur des listes</span><span class="sxs-lookup"><span data-stu-id="b185e-182">Sort Operations on Lists</span></span>

<span data-ttu-id="b185e-183">Les fonctions [List. sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List. SortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)et [List. sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) trient les listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-183">The [List.sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List.sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy), and [List.sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) functions sort lists.</span></span> <span data-ttu-id="b185e-184">La fonction de tri détermine laquelle de ces trois fonctions utiliser.</span><span class="sxs-lookup"><span data-stu-id="b185e-184">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="b185e-185">`List.sort` utilise la comparaison générique par défaut.</span><span class="sxs-lookup"><span data-stu-id="b185e-185">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="b185e-186">Celle-ci compare des valeurs à l'aide d'opérateurs globaux reposant sur la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="b185e-186">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="b185e-187">Elle est efficace avec une large gamme de types d'éléments, tels que les types numériques simples, les tuples, les enregistrements, les unions discriminées, les listes, les tableaux et tout type qui implémente `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="b185e-187">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="b185e-188">Dans le cas des types implémentant `System.IComparable`, la comparaison générique utilise la fonction `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="b185e-188">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="b185e-189">La comparaison générique fonctionne aussi avec les chaînes, mais utilise un ordre de tri indépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="b185e-189">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="b185e-190">Elle ne doit pas être utilisée sur les types non pris en charge, tels que les types de fonction.</span><span class="sxs-lookup"><span data-stu-id="b185e-190">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="b185e-191">De plus, les performances de la comparaison générique par défaut sont meilleures dans le cas de petits types structurés. Dans le cas de types structurés plus importants qui impliquent une fréquence de comparaison et de tri plus soutenue, envisagez d'implémenter `System.IComparable` et de fournir une implémentation efficace de la méthode `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="b185e-191">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="b185e-192">`List.sortBy` accepte une fonction qui retourne une valeur utilisée comme critère de tri, et `List.sortWith` accepte une fonction de comparaison comme argument.</span><span class="sxs-lookup"><span data-stu-id="b185e-192">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="b185e-193">Ces deux fonctions sont utiles quand les types ne prennent pas en charge la comparaison ou quand la comparaison nécessite une sémantique plus complexe, comme avec les chaînes prenant en compte la culture.</span><span class="sxs-lookup"><span data-stu-id="b185e-193">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="b185e-194">L'exemple suivant montre l'utilisation de `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="b185e-194">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="b185e-195">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-195">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="b185e-196">L'exemple suivant montre l'utilisation de `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="b185e-196">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="b185e-197">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-197">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="b185e-198">L'exemple suivant montre l'utilisation de `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="b185e-198">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="b185e-199">Dans cet exemple, la fonction de comparaison personnalisée `compareWidgets` est utilisée pour comparer en premier un champ de type personnalisé, puis un autre champ quand les valeurs du premier champ sont égales.</span><span class="sxs-lookup"><span data-stu-id="b185e-199">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="b185e-200">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-200">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="b185e-201">Opérations de recherche sur des listes</span><span class="sxs-lookup"><span data-stu-id="b185e-201">Search Operations on Lists</span></span>

<span data-ttu-id="b185e-202">Les listes prennent en charge plusieurs opérations de recherche.</span><span class="sxs-lookup"><span data-stu-id="b185e-202">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="b185e-203">La plus simple, [List. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), vous permet de rechercher le premier élément qui correspond à une condition donnée.</span><span class="sxs-lookup"><span data-stu-id="b185e-203">The simplest, [List.find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="b185e-204">L'exemple de code suivant montre l'utilisation de `List.find` pour rechercher le premier nombre divisible par 5 dans une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-204">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="b185e-205">Le résultat est 5.</span><span class="sxs-lookup"><span data-stu-id="b185e-205">The result is 5.</span></span>

<span data-ttu-id="b185e-206">Si les éléments doivent être transformés en premier, appelez [List. Pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), qui prend une fonction qui retourne une option, et recherche la première valeur d’option qui est `Some(x)` .</span><span class="sxs-lookup"><span data-stu-id="b185e-206">If the elements must be transformed first, call [List.pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="b185e-207">Au lieu de renvoyer l'élément, `List.pick` retourne le résultat `x`.</span><span class="sxs-lookup"><span data-stu-id="b185e-207">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="b185e-208">Si aucun élément correspondant n'est trouvé, `List.pick` lève `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="b185e-208">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="b185e-209">Le code suivant illustre l'utilisation de `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="b185e-209">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="b185e-210">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-210">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="b185e-211">Un autre groupe d’opérations de recherche, [List. tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) et les fonctions associées, retournent une valeur d’option.</span><span class="sxs-lookup"><span data-stu-id="b185e-211">Another group of search operations, [List.tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) and related functions, return an option value.</span></span> <span data-ttu-id="b185e-212">La fonction `List.tryFind` retourne le premier élément d'une liste qui satisfait à une condition, le cas échéant, et la valeur d'option `None` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="b185e-212">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="b185e-213">La liste de variantes [. tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) retourne l’index de l’élément, le cas échéant, au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="b185e-213">The variation [List.tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="b185e-214">Ces fonctions sont illustrées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b185e-214">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="b185e-215">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-215">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="b185e-216">Opérations arithmétiques sur des listes</span><span class="sxs-lookup"><span data-stu-id="b185e-216">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="b185e-217">Les opérations arithmétiques courantes telles que SUM et Average sont intégrées dans le [module List](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="b185e-217">Common arithmetic operations such as sum and average are built into the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="b185e-218">Pour fonctionner avec [List. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), le type d’élément de liste doit prendre en charge l' `+` opérateur et avoir une valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="b185e-218">To work with [List.sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="b185e-219">Tous les types arithmétiques intégrés remplissent ces conditions.</span><span class="sxs-lookup"><span data-stu-id="b185e-219">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="b185e-220">Pour fonctionner avec [List. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), le type d’élément doit prendre en charge la Division sans reste, ce qui exclut les types intégraux, mais autorise les types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="b185e-220">To work with [List.average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="b185e-221">Les fonctions [List. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) et [List. averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) prennent une fonction comme paramètre, et les résultats de cette fonction sont utilisés pour calculer les valeurs de la somme ou de la moyenne.</span><span class="sxs-lookup"><span data-stu-id="b185e-221">The [List.sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) and [List.averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="b185e-222">Le code suivant montre l'utilisation de `List.sum`, `List.sumBy` et `List.average`.</span><span class="sxs-lookup"><span data-stu-id="b185e-222">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="b185e-223">Le résultat est `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="b185e-223">The output is `1.000000`.</span></span>

<span data-ttu-id="b185e-224">Le code suivant illustre l'utilisation de `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="b185e-224">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="b185e-225">Le résultat est `5.5`.</span><span class="sxs-lookup"><span data-stu-id="b185e-225">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="b185e-226">Listes et tuples</span><span class="sxs-lookup"><span data-stu-id="b185e-226">Lists and Tuples</span></span>

<span data-ttu-id="b185e-227">Les listes qui contiennent des tuples peuvent être manipulées par des fonctions de compression et de décompression.</span><span class="sxs-lookup"><span data-stu-id="b185e-227">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="b185e-228">Ces fonctions combinent deux listes de valeurs uniques en une seule liste de tuples ou séparent une liste de tuples en deux listes de valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="b185e-228">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="b185e-229">La fonction [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) la plus simple prend deux listes d’éléments uniques et produit une seule liste de paires de tuples.</span><span class="sxs-lookup"><span data-stu-id="b185e-229">The simplest [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="b185e-230">Une autre version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), prend trois listes d’éléments uniques et produit une seule liste de tuples qui ont trois éléments.</span><span class="sxs-lookup"><span data-stu-id="b185e-230">Another version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="b185e-231">L'exemple de code suivant montre l'utilisation de `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="b185e-231">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="b185e-232">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-232">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="b185e-233">L'exemple de code suivant montre l'utilisation de `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="b185e-233">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="b185e-234">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-234">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="b185e-235">Les versions de décompression correspondantes, [List. unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) et [List. unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), prennent des listes de tuples et des listes de retour dans un tuple, où la première liste contient tous les éléments qui étaient en premier dans chaque tuple, et la deuxième liste contient le deuxième élément de chaque tuple, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="b185e-235">The corresponding unzip versions, [List.unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) and [List.unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="b185e-236">L’exemple de code suivant illustre l’utilisation de [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="b185e-236">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="b185e-237">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-237">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="b185e-238">L’exemple de code suivant illustre l’utilisation de [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="b185e-238">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="b185e-239">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-239">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="b185e-240">Opérations sur les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="b185e-240">Operating on List Elements</span></span>

<span data-ttu-id="b185e-241">F# prend en charge un éventail d'opérations sur des éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-241">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="b185e-242">La méthode [List. ITER](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter)la plus simple vous permet d’appeler une fonction sur chaque élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-242">The simplest is [List.iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="b185e-243">Les variations incluent [List. iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), qui vous permet d’effectuer une opération sur les éléments de deux listes, [List. iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), qui est similaire, `List.iter` à ceci près que l’index de chaque élément est passé comme argument à la fonction appelée pour chaque élément et [List. iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), qui est une combinaison des fonctionnalités de `List.iter2` et de `List.iteri` .</span><span class="sxs-lookup"><span data-stu-id="b185e-243">Variations include [List.iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), which enables you to perform an operation on elements of two lists, [List.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="b185e-244">L'exemple de code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="b185e-244">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="b185e-245">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-245">The output is as follows:</span></span>

```console
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="b185e-246">Une autre fonction fréquemment utilisée qui transforme les éléments de liste est [List. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), qui vous permet d’appliquer une fonction à chaque élément d’une liste et de placer tous les résultats dans une nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-246">Another frequently used function that transforms list elements is [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="b185e-247">[List. map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) et [List. map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) sont des variations qui acceptent plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-247">[List.map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) and [List.map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) are variations that take multiple lists.</span></span> <span data-ttu-id="b185e-248">Vous pouvez également utiliser [List. MAPI](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) et [List. mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), si, en plus de l’élément, la fonction doit être passée à l’index de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-248">You can also use [List.mapi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) and [List.mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="b185e-249">La seule différence entre `List.mapi2` et `List.mapi` est le fait que `List.mapi2` fonctionne avec les deux listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-249">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="b185e-250">L’exemple suivant illustre [List. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span><span class="sxs-lookup"><span data-stu-id="b185e-250">The following example illustrates [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="b185e-251">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-251">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="b185e-252">L’exemple suivant illustre l’utilisation de `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="b185e-252">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="b185e-253">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-253">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="b185e-254">L’exemple suivant illustre l’utilisation de `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="b185e-254">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="b185e-255">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-255">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="b185e-256">L’exemple suivant illustre l’utilisation de `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="b185e-256">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="b185e-257">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-257">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="b185e-258">L’exemple suivant illustre l’utilisation de `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="b185e-258">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="b185e-259">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-259">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="b185e-260">[List. Collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) est semblable `List.map` à, à ceci près que chaque élément produit une liste et que toutes ces listes sont concaténées dans une liste finale.</span><span class="sxs-lookup"><span data-stu-id="b185e-260">[List.collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="b185e-261">Dans le code suivant, chaque élément de la liste génère trois nombres.</span><span class="sxs-lookup"><span data-stu-id="b185e-261">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="b185e-262">Ils sont tous rassemblés dans une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-262">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="b185e-263">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-263">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="b185e-264">Vous pouvez également utiliser [List. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), qui prend une condition booléenne et produit une nouvelle liste qui se compose uniquement d’éléments qui répondent à la condition donnée.</span><span class="sxs-lookup"><span data-stu-id="b185e-264">You can also use [List.filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="b185e-265">La liste obtenue est `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="b185e-265">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="b185e-266">Une combinaison de Map et Filter, [List. choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) vous permet de transformer et de sélectionner des éléments en même temps.</span><span class="sxs-lookup"><span data-stu-id="b185e-266">A combination of map and filter, [List.choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="b185e-267">`List.choose` applique une fonction qui retourne une option à chaque élément d'une liste et renvoie une nouvelle liste des résultats pour les éléments quand la fonction retourne la valeur d'option `Some`.</span><span class="sxs-lookup"><span data-stu-id="b185e-267">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="b185e-268">Le code suivant illustre l'utilisation de `List.choose` pour sélectionner des mots en majuscules dans une liste de mots.</span><span class="sxs-lookup"><span data-stu-id="b185e-268">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="b185e-269">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="b185e-269">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="b185e-270">Opérations sur plusieurs listes</span><span class="sxs-lookup"><span data-stu-id="b185e-270">Operating on Multiple Lists</span></span>

<span data-ttu-id="b185e-271">Les listes peuvent être jointes.</span><span class="sxs-lookup"><span data-stu-id="b185e-271">Lists can be joined together.</span></span> <span data-ttu-id="b185e-272">Pour joindre deux listes en une seule, utilisez [List. Append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span><span class="sxs-lookup"><span data-stu-id="b185e-272">To join two lists into one, use [List.append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span></span> <span data-ttu-id="b185e-273">Pour joindre plus de deux listes, utilisez [List. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span><span class="sxs-lookup"><span data-stu-id="b185e-273">To join more than two lists, use [List.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="b185e-274">Opérations de repli et d'analyse</span><span class="sxs-lookup"><span data-stu-id="b185e-274">Fold and Scan Operations</span></span>

<span data-ttu-id="b185e-275">Certaines opérations de liste impliquent l'interdépendance entre tous les éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-275">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="b185e-276">Les opérations de repli et d’analyse sont similaires et, dans le cas `List.iter` `List.map` où vous appelez une fonction sur chaque élément, mais ces opérations fournissent un paramètre supplémentaire appelé l' *accumulation* qui transporte des informations via le calcul.</span><span class="sxs-lookup"><span data-stu-id="b185e-276">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="b185e-277">Utilisez `List.fold` pour effectuer un calcul sur une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-277">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="b185e-278">L’exemple de code suivant illustre l’utilisation de [List. fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) pour effectuer diverses opérations.</span><span class="sxs-lookup"><span data-stu-id="b185e-278">The following code example demonstrates the use of [List.fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) to perform various operations.</span></span>

<span data-ttu-id="b185e-279">La liste est parcourue ; l'accumulateur `acc` est une valeur passée au cours du calcul.</span><span class="sxs-lookup"><span data-stu-id="b185e-279">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="b185e-280">Le premier argument prend l'accumulateur et l'élément de liste, puis retourne le résultat intermédiaire du calcul pour cet élément de liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-280">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="b185e-281">Le deuxième argument est la valeur initiale de l’accumulateur.</span><span class="sxs-lookup"><span data-stu-id="b185e-281">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="b185e-282">Les versions de ces fonctions dont le nom contient un chiffre s'effectuent sur plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-282">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="b185e-283">Par exemple, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) effectue des calculs sur deux listes.</span><span class="sxs-lookup"><span data-stu-id="b185e-283">For example, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) performs computations on two lists.</span></span>

<span data-ttu-id="b185e-284">L'exemple suivant montre l'utilisation de `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="b185e-284">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="b185e-285">`List.fold` et [List. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) diffère dans qui `List.fold` retourne la valeur finale du paramètre supplémentaire, mais `List.scan` retourne la liste des valeurs intermédiaires (avec la valeur finale) du paramètre supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="b185e-285">`List.fold` and [List.scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="b185e-286">Chacune de ces fonctions comprend une variation inverse, par exemple [List. foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), qui diffère selon l’ordre dans lequel la liste est parcourue et l’ordre des arguments.</span><span class="sxs-lookup"><span data-stu-id="b185e-286">Each of these functions includes a reverse variation, for example, [List.foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="b185e-287">En outre, `List.fold` et `List.foldBack` ont des variations, [List. fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) et [List. foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), qui acceptent deux listes de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="b185e-287">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) and [List.foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), that take two lists of equal length.</span></span> <span data-ttu-id="b185e-288">La fonction qui s'exécute sur chaque élément peut utiliser des éléments correspondants aux deux listes pour effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="b185e-288">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="b185e-289">Les types d’éléments des deux listes peuvent être différents, comme dans l’exemple suivant, où une liste contient des montants de transactions sur un compte bancaire et l’autre contient le type de transaction : dépôt ou retrait.</span><span class="sxs-lookup"><span data-stu-id="b185e-289">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="b185e-290">Pour un calcul tel qu'une addition, `List.fold` et `List.foldBack` ont le même effet car le résultat ne dépend pas de l'ordre de traversée.</span><span class="sxs-lookup"><span data-stu-id="b185e-290">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="b185e-291">Dans l'exemple ci-dessous, `List.foldBack` est utilisé pour ajouter les éléments à une liste.</span><span class="sxs-lookup"><span data-stu-id="b185e-291">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="b185e-292">Voici à nouveau l'exemple du compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="b185e-292">The following example returns to the bank account example.</span></span> <span data-ttu-id="b185e-293">Cette fois, un nouveau type de transaction est ajouté : le calcul d'intérêts.</span><span class="sxs-lookup"><span data-stu-id="b185e-293">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="b185e-294">Le solde de fin dépend désormais de l'ordre des transactions.</span><span class="sxs-lookup"><span data-stu-id="b185e-294">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="b185e-295">La fonction [List. Reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) est un peu comme `List.fold` et `List.scan` , à ceci près qu’au lieu de passer autour d’un accumulateur séparé, `List.reduce` prend une fonction qui accepte deux arguments du type d’élément au lieu d’un seul, et l’un de ces arguments joue le rôle d’accumulateur, ce qui signifie qu’elle stocke le résultat intermédiaire du calcul.</span><span class="sxs-lookup"><span data-stu-id="b185e-295">The function [List.reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="b185e-296">`List.reduce` commence par fonctionner sur les deux premiers éléments de liste, puis utilise le résultat de l'opération avec l'élément suivant.</span><span class="sxs-lookup"><span data-stu-id="b185e-296">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="b185e-297">Comme aucun accumulateur distinct ne possède son propre type, `List.reduce` ne peut être utilisé à la place de `List.fold` si l'accumulateur et le type d'élément ont le même type.</span><span class="sxs-lookup"><span data-stu-id="b185e-297">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="b185e-298">Le code suivant montre l'utilisation de `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="b185e-298">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="b185e-299">`List.reduce` lève une exception si la liste fournie ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="b185e-299">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="b185e-300">Dans le code suivant, le premier appel à l’expression lambda reçoit les arguments 2 et 4, et retourne 6. L’appel suivant reçoit les arguments 6 et 10, le résultat est donc 16.</span><span class="sxs-lookup"><span data-stu-id="b185e-300">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="b185e-301">Conversion entre listes et autres types de collections</span><span class="sxs-lookup"><span data-stu-id="b185e-301">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="b185e-302">Le module `List` fournit des fonctions pour convertir vers et depuis des séquences et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="b185e-302">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="b185e-303">Pour convertir vers ou à partir d’une séquence, utilisez [List. toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) ou [List. ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span><span class="sxs-lookup"><span data-stu-id="b185e-303">To convert to or from a sequence, use [List.toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) or [List.ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span></span> <span data-ttu-id="b185e-304">Pour convertir vers ou à partir d’un tableau, utilisez [List. ToArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) ou [List. ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span><span class="sxs-lookup"><span data-stu-id="b185e-304">To convert to or from an array, use [List.toArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) or [List.ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="b185e-305">Opérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="b185e-305">Additional Operations</span></span>

<span data-ttu-id="b185e-306">Pour plus d’informations sur les opérations supplémentaires sur les listes, consultez le module de la [liste](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)de rubriques de référence sur la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="b185e-306">For information about additional operations on lists, see the library reference topic [List Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="b185e-307">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b185e-307">See also</span></span>

- [<span data-ttu-id="b185e-308">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="b185e-308">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b185e-309">Types F#</span><span class="sxs-lookup"><span data-stu-id="b185e-309">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="b185e-310">Séquences</span><span class="sxs-lookup"><span data-stu-id="b185e-310">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="b185e-311">Tableaux</span><span class="sxs-lookup"><span data-stu-id="b185e-311">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="b185e-312">Options</span><span class="sxs-lookup"><span data-stu-id="b185e-312">Options</span></span>](options.md)

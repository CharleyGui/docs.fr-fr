---
title: Listes
description: 'En savoir plus sur les listes F #, une série immuable et ordonnée d’éléments du même type.'
ms.date: 05/16/2016
ms.openlocfilehash: 236ae77813a3448f159228c5c58d9fe3d024fbd8
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854969"
---
# <a name="lists"></a><span data-ttu-id="9a53e-103">Listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-103">Lists</span></span>

<span data-ttu-id="9a53e-104">En F#, une liste est une série immuable et ordonnée d'éléments du même type.</span><span class="sxs-lookup"><span data-stu-id="9a53e-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="9a53e-105">Pour effectuer des opérations de base sur les listes, utilisez les fonctions dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="9a53e-105">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

> [!NOTE]
> <span data-ttu-id="9a53e-106">La référence de l’API docs.microsoft.com pour F # n’est pas terminée.</span><span class="sxs-lookup"><span data-stu-id="9a53e-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="9a53e-107">Si vous rencontrez des liens rompus, consultez plutôt [la documentation de la bibliothèque principale F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="9a53e-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="9a53e-108">Création et initialisation de listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="9a53e-109">Vous pouvez définir une liste en répertoriant de manière explicite les éléments, séparés par des points-virgules et placés entre crochets, comme indiqué dans la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="9a53e-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="9a53e-110">Vous pouvez également insérer des sauts de ligne entre les éléments, les points-virgules étant facultatifs dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="9a53e-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="9a53e-111">Cette syntaxe produit du code plus lisible quand les expressions d'initialisation des éléments sont plus longues, ou quand vous souhaitez ajouter un commentaire pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="9a53e-112">Généralement, tous les éléments de liste doivent être du même type.</span><span class="sxs-lookup"><span data-stu-id="9a53e-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="9a53e-113">Il existe une exception : une liste dont les éléments sont spécifiés comme type de base peut comporter des éléments qui sont des types dérivés.</span><span class="sxs-lookup"><span data-stu-id="9a53e-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="9a53e-114">L'exemple suivant est acceptable, car `Button` et `CheckBox` dérivent de `Control`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="9a53e-115">Vous pouvez également définir des éléments de liste à l'aide d'une plage indiquée par des entiers séparés par l'opérateur de plage (`..`), comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9a53e-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="9a53e-116">Une liste vide est spécifiée par une paire de crochets vide.</span><span class="sxs-lookup"><span data-stu-id="9a53e-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="9a53e-117">Vous pouvez également utiliser une expression de séquence pour créer une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="9a53e-118">Pour plus d’informations, consultez [expressions de séquence](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="9a53e-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="9a53e-119">Par exemple, le code suivant crée une liste d'entiers au carré, de 1 à 10.</span><span class="sxs-lookup"><span data-stu-id="9a53e-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="9a53e-120">Opérateurs utilisés avec les listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-120">Operators for Working with Lists</span></span>

<span data-ttu-id="9a53e-121">Vous pouvez joindre des éléments à une liste en utilisant l'opérateur (cons) `::`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="9a53e-122">Si `list1` est `[2; 3; 4]`, le code suivant crée `list2` sous la forme `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="9a53e-123">Vous pouvez concaténer des listes qui présentent des types compatibles à l'aide de l'opérateur `@`, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9a53e-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="9a53e-124">Si `list1` est `[2; 3; 4]` et `list2` est `[100; 2; 3; 4]`, ce code crée `list3` sous la forme `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="9a53e-125">Les fonctions permettant d’effectuer des opérations sur des listes sont disponibles dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="9a53e-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="9a53e-126">En F#, les listes étant immuables, toute opération de changement a pour effet de générer de nouvelles listes au lieu de modifier les listes existantes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="9a53e-127">Les listes en F # sont implémentées en tant que listes à liaison unique, ce qui signifie que les opérations qui accèdent uniquement au début de la liste sont O (1) et que l’accès à l’élément est O (*n*).</span><span class="sxs-lookup"><span data-stu-id="9a53e-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="9a53e-128">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9a53e-128">Properties</span></span>

<span data-ttu-id="9a53e-129">Le type de liste prend en charge les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="9a53e-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="9a53e-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="9a53e-130">Property</span></span>|<span data-ttu-id="9a53e-131">Type</span><span class="sxs-lookup"><span data-stu-id="9a53e-131">Type</span></span>|<span data-ttu-id="9a53e-132">Description</span><span class="sxs-lookup"><span data-stu-id="9a53e-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="9a53e-133">Siège</span><span class="sxs-lookup"><span data-stu-id="9a53e-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="9a53e-134">Premier élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-134">The first element.</span></span>|
|[<span data-ttu-id="9a53e-135">Vide</span><span class="sxs-lookup"><span data-stu-id="9a53e-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="9a53e-136">Propriété statique qui retourne une liste vide du type approprié.</span><span class="sxs-lookup"><span data-stu-id="9a53e-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="9a53e-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="9a53e-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="9a53e-138">`true` si la liste ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="9a53e-139">Item</span><span class="sxs-lookup"><span data-stu-id="9a53e-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="9a53e-140">Élément au niveau de l'index spécifié (de base zéro).</span><span class="sxs-lookup"><span data-stu-id="9a53e-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="9a53e-141">Longueur</span><span class="sxs-lookup"><span data-stu-id="9a53e-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="9a53e-142">Nombre d'éléments.</span><span class="sxs-lookup"><span data-stu-id="9a53e-142">The number of elements.</span></span>|
|[<span data-ttu-id="9a53e-143">Tail</span><span class="sxs-lookup"><span data-stu-id="9a53e-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="9a53e-144">Liste sans premier élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-144">The list without the first element.</span></span>|

<span data-ttu-id="9a53e-145">Voici quelques exemples d'utilisation de ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="9a53e-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="9a53e-146">Utilisation de listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-146">Using Lists</span></span>

<span data-ttu-id="9a53e-147">La programmation à l'aide de listes vous permet d'effectuer des opérations complexes avec peu de code.</span><span class="sxs-lookup"><span data-stu-id="9a53e-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="9a53e-148">Cette section décrit des opérations courantes sur des listes qui sont importantes pour la programmation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="9a53e-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="9a53e-149">Récursivité avec des listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-149">Recursion with Lists</span></span>

<span data-ttu-id="9a53e-150">Les listes sont particulièrement adaptées aux techniques de programmation récursive.</span><span class="sxs-lookup"><span data-stu-id="9a53e-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="9a53e-151">Prenons en compte une opération à effectuer sur chaque élément d'une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="9a53e-152">Vous pouvez procéder de manière récursive en effectuant l'opération sur le début de la liste, puis en passant à la fin de la liste, qui est une liste plus petite comprenant la liste d'origine sans le premier élément, et en revenant au niveau suivant de récursivité.</span><span class="sxs-lookup"><span data-stu-id="9a53e-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="9a53e-153">Pour écrire ce type de fonction récursive, utilisez l’opérateur cons (`::`) dans les critères spéciaux, qui vous permet de séparer le début d’une liste de sa fin.</span><span class="sxs-lookup"><span data-stu-id="9a53e-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="9a53e-154">L’exemple de code suivant indique comment utiliser les critères spéciaux pour implémenter une fonction récursive qui exécute des opérations sur une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="9a53e-155">Le code précédent fonctionne bien dans le cas de petites listes, mais dans le cas de listes plus longues, il peut entraîner un dépassement de capacité de la pile.</span><span class="sxs-lookup"><span data-stu-id="9a53e-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="9a53e-156">Le code suivant améliore le précédent à l’aide d’un argument d’accumulation, technique standard utilisée avec les fonctions récursives.</span><span class="sxs-lookup"><span data-stu-id="9a53e-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="9a53e-157">L'argument d'accumulation rend la fin de la fonction récursive, ce qui permet de contenir l'espace de pile.</span><span class="sxs-lookup"><span data-stu-id="9a53e-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="9a53e-158">La fonction `RemoveAllMultiples` est récursive et accepte deux listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="9a53e-159">La première liste contient les nombres dont les multiples seront supprimés ; la seconde liste contient les nombres à supprimer.</span><span class="sxs-lookup"><span data-stu-id="9a53e-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="9a53e-160">Le code de l’exemple suivant utilise cette fonction récursive pour éliminer tous les nombres non premiers d’une liste, générant ainsi une liste de nombres premiers.</span><span class="sxs-lookup"><span data-stu-id="9a53e-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="9a53e-161">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-161">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="9a53e-162">Fonctions de module</span><span class="sxs-lookup"><span data-stu-id="9a53e-162">Module Functions</span></span>

<span data-ttu-id="9a53e-163">Le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) fournit des fonctions qui accèdent aux éléments d’une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="9a53e-164">L'élément de début offre l'accès le plus simple et rapide.</span><span class="sxs-lookup"><span data-stu-id="9a53e-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="9a53e-165">Utilisez l' [en-tête](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) de propriété ou la fonction de module [List. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="9a53e-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="9a53e-166">Vous pouvez accéder à la fin d’une liste à l’aide de la propriété [tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) ou de la fonction [List. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) .</span><span class="sxs-lookup"><span data-stu-id="9a53e-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="9a53e-167">Pour rechercher un élément par index, utilisez la fonction [List. nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) .</span><span class="sxs-lookup"><span data-stu-id="9a53e-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="9a53e-168">`List.nth` parcourt la liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="9a53e-169">Par conséquent, il s’agit de O (*n*).</span><span class="sxs-lookup"><span data-stu-id="9a53e-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="9a53e-170">Si votre code utilise fréquemment `List.nth`, envisagez d'utiliser un tableau à la place d'une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="9a53e-171">L'accès aux éléments des tableaux est O(1).</span><span class="sxs-lookup"><span data-stu-id="9a53e-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="9a53e-172">Opérations booléennes sur des listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="9a53e-173">La fonction [List. IsEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) détermine si une liste contient des éléments.</span><span class="sxs-lookup"><span data-stu-id="9a53e-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="9a53e-174">La fonction [List. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) applique un test booléen aux éléments d’une liste et retourne `true` si un élément satisfait au test.</span><span class="sxs-lookup"><span data-stu-id="9a53e-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="9a53e-175">[List. exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) est similaire, mais fonctionne sur des paires d’éléments successifs dans deux listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="9a53e-176">Le code suivant montre l'utilisation de `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="9a53e-177">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-177">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="9a53e-178">L'exemple suivant montre l'utilisation de `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="9a53e-179">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-179">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="9a53e-180">Vous pouvez utiliser [List. forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) si vous souhaitez tester si tous les éléments d’une liste remplissent une condition.</span><span class="sxs-lookup"><span data-stu-id="9a53e-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="9a53e-181">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-181">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="9a53e-182">De même, [List. forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) détermine si tous les éléments des positions correspondantes dans deux listes satisfont à une expression booléenne qui implique chaque paire d’éléments.</span><span class="sxs-lookup"><span data-stu-id="9a53e-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="9a53e-183">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-183">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="9a53e-184">Opérations de tri sur des listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-184">Sort Operations on Lists</span></span>

<span data-ttu-id="9a53e-185">Les fonctions [List. sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List. SortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)et [List. sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) trient les listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="9a53e-186">La fonction de tri détermine laquelle de ces trois fonctions utiliser.</span><span class="sxs-lookup"><span data-stu-id="9a53e-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="9a53e-187">`List.sort` utilise la comparaison générique par défaut.</span><span class="sxs-lookup"><span data-stu-id="9a53e-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="9a53e-188">Celle-ci compare des valeurs à l'aide d'opérateurs globaux reposant sur la fonction de comparaison générique.</span><span class="sxs-lookup"><span data-stu-id="9a53e-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="9a53e-189">Elle est efficace avec une large gamme de types d'éléments, tels que les types numériques simples, les tuples, les enregistrements, les unions discriminées, les listes, les tableaux et tout type qui implémente `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="9a53e-190">Dans le cas des types implémentant `System.IComparable`, la comparaison générique utilise la fonction `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="9a53e-191">La comparaison générique fonctionne aussi avec les chaînes, mais utilise un ordre de tri indépendant de la culture.</span><span class="sxs-lookup"><span data-stu-id="9a53e-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="9a53e-192">Elle ne doit pas être utilisée sur les types non pris en charge, tels que les types de fonction.</span><span class="sxs-lookup"><span data-stu-id="9a53e-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="9a53e-193">De plus, les performances de la comparaison générique par défaut sont meilleures dans le cas de petits types structurés. Dans le cas de types structurés plus importants qui impliquent une fréquence de comparaison et de tri plus soutenue, envisagez d'implémenter `System.IComparable` et de fournir une implémentation efficace de la méthode `System.IComparable.CompareTo()`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="9a53e-194">`List.sortBy` accepte une fonction qui retourne une valeur utilisée comme critère de tri, et `List.sortWith` accepte une fonction de comparaison comme argument.</span><span class="sxs-lookup"><span data-stu-id="9a53e-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="9a53e-195">Ces deux fonctions sont utiles quand les types ne prennent pas en charge la comparaison ou quand la comparaison nécessite une sémantique plus complexe, comme avec les chaînes prenant en compte la culture.</span><span class="sxs-lookup"><span data-stu-id="9a53e-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="9a53e-196">L'exemple suivant montre l'utilisation de `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="9a53e-197">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-197">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="9a53e-198">L'exemple suivant montre l'utilisation de `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="9a53e-199">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-199">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="9a53e-200">L'exemple suivant montre l'utilisation de `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="9a53e-201">Dans cet exemple, la fonction de comparaison personnalisée `compareWidgets` est utilisée pour comparer en premier un champ de type personnalisé, puis un autre champ quand les valeurs du premier champ sont égales.</span><span class="sxs-lookup"><span data-stu-id="9a53e-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="9a53e-202">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-202">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="9a53e-203">Opérations de recherche sur des listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-203">Search Operations on Lists</span></span>

<span data-ttu-id="9a53e-204">Les listes prennent en charge plusieurs opérations de recherche.</span><span class="sxs-lookup"><span data-stu-id="9a53e-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="9a53e-205">La plus simple, [List. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), vous permet de rechercher le premier élément qui correspond à une condition donnée.</span><span class="sxs-lookup"><span data-stu-id="9a53e-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="9a53e-206">L'exemple de code suivant montre l'utilisation de `List.find` pour rechercher le premier nombre divisible par 5 dans une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="9a53e-207">Le résultat est 5.</span><span class="sxs-lookup"><span data-stu-id="9a53e-207">The result is 5.</span></span>

<span data-ttu-id="9a53e-208">Si les éléments doivent être transformés en premier, appelez [List. Pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), qui prend une fonction qui retourne une option, et recherche la première valeur d’option qui est `Some(x)` .</span><span class="sxs-lookup"><span data-stu-id="9a53e-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="9a53e-209">Au lieu de renvoyer l'élément, `List.pick` retourne le résultat `x`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="9a53e-210">Si aucun élément correspondant n'est trouvé, `List.pick` lève `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="9a53e-211">Le code suivant illustre l'utilisation de `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="9a53e-212">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-212">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="9a53e-213">Un autre groupe d’opérations de recherche, [List. tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) et les fonctions associées, retournent une valeur d’option.</span><span class="sxs-lookup"><span data-stu-id="9a53e-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="9a53e-214">La fonction `List.tryFind` retourne le premier élément d'une liste qui satisfait à une condition, le cas échéant, et la valeur d'option `None` dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="9a53e-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="9a53e-215">La liste de variantes [. tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) retourne l’index de l’élément, le cas échéant, au lieu de l’élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="9a53e-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="9a53e-216">Ces fonctions sont illustrées dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9a53e-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="9a53e-217">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-217">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="9a53e-218">Opérations arithmétiques sur des listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="9a53e-219">Les opérations arithmétiques courantes telles que SUM et Average sont intégrées dans le [module List](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="9a53e-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="9a53e-220">Pour fonctionner avec [List. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), le type d’élément de liste doit prendre en charge l' `+` opérateur et avoir une valeur égale à zéro.</span><span class="sxs-lookup"><span data-stu-id="9a53e-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="9a53e-221">Tous les types arithmétiques intégrés remplissent ces conditions.</span><span class="sxs-lookup"><span data-stu-id="9a53e-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="9a53e-222">Pour fonctionner avec [List. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), le type d’élément doit prendre en charge la Division sans reste, ce qui exclut les types intégraux, mais autorise les types à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="9a53e-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="9a53e-223">Les fonctions [List. sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) et [List. averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) prennent une fonction comme paramètre, et les résultats de cette fonction sont utilisés pour calculer les valeurs de la somme ou de la moyenne.</span><span class="sxs-lookup"><span data-stu-id="9a53e-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="9a53e-224">Le code suivant montre l'utilisation de `List.sum`, `List.sumBy` et `List.average`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="9a53e-225">Le résultat est `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-225">The output is `1.000000`.</span></span>

<span data-ttu-id="9a53e-226">Le code suivant illustre l'utilisation de `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="9a53e-227">Le résultat est `5.5`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="9a53e-228">Listes et tuples</span><span class="sxs-lookup"><span data-stu-id="9a53e-228">Lists and Tuples</span></span>

<span data-ttu-id="9a53e-229">Les listes qui contiennent des tuples peuvent être manipulées par des fonctions de compression et de décompression.</span><span class="sxs-lookup"><span data-stu-id="9a53e-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="9a53e-230">Ces fonctions combinent deux listes de valeurs uniques en une seule liste de tuples ou séparent une liste de tuples en deux listes de valeurs uniques.</span><span class="sxs-lookup"><span data-stu-id="9a53e-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="9a53e-231">La fonction [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) la plus simple prend deux listes d’éléments uniques et produit une seule liste de paires de tuples.</span><span class="sxs-lookup"><span data-stu-id="9a53e-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="9a53e-232">Une autre version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), prend trois listes d’éléments uniques et produit une seule liste de tuples qui ont trois éléments.</span><span class="sxs-lookup"><span data-stu-id="9a53e-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="9a53e-233">L'exemple de code suivant montre l'utilisation de `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="9a53e-234">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-234">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="9a53e-235">L'exemple de code suivant montre l'utilisation de `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="9a53e-236">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-236">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="9a53e-237">Les versions de décompression correspondantes, [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) et [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), prennent des listes de tuples et des listes de retour dans un tuple, où la première liste contient tous les éléments qui étaient en premier dans chaque tuple, et la deuxième liste contient le deuxième élément de chaque tuple, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="9a53e-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="9a53e-238">L’exemple de code suivant illustre l’utilisation de [List. unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="9a53e-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="9a53e-239">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-239">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="9a53e-240">L’exemple de code suivant illustre l’utilisation de [List. unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="9a53e-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="9a53e-241">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-241">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="9a53e-242">Opérations sur les éléments de liste</span><span class="sxs-lookup"><span data-stu-id="9a53e-242">Operating on List Elements</span></span>

<span data-ttu-id="9a53e-243">F# prend en charge un éventail d'opérations sur des éléments de liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="9a53e-244">La méthode [List. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)la plus simple vous permet d’appeler une fonction sur chaque élément d’une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="9a53e-245">Les variations incluent [List. iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), qui vous permet d’effectuer une opération sur les éléments de deux listes, [List. iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), qui est similaire, `List.iter` à ceci près que l’index de chaque élément est passé comme argument à la fonction appelée pour chaque élément et [List. iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), qui est une combinaison des fonctionnalités de `List.iter2` et de `List.iteri` .</span><span class="sxs-lookup"><span data-stu-id="9a53e-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="9a53e-246">L'exemple de code suivant illustre ces fonctions.</span><span class="sxs-lookup"><span data-stu-id="9a53e-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="9a53e-247">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-247">The output is as follows:</span></span>

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

<span data-ttu-id="9a53e-248">Une autre fonction fréquemment utilisée qui transforme les éléments de liste est [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), qui vous permet d’appliquer une fonction à chaque élément d’une liste et de placer tous les résultats dans une nouvelle liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="9a53e-249">[List. map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) et [List. map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) sont des variations qui acceptent plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="9a53e-250">Vous pouvez également utiliser [List. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) et [List. mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), si, en plus de l’élément, la fonction doit être passée à l’index de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="9a53e-251">La seule différence entre `List.mapi2` et `List.mapi` est le fait que `List.mapi2` fonctionne avec les deux listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="9a53e-252">L’exemple suivant illustre [List. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="9a53e-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="9a53e-253">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-253">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="9a53e-254">L’exemple suivant illustre l’utilisation de `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="9a53e-255">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-255">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="9a53e-256">L’exemple suivant illustre l’utilisation de `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="9a53e-257">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-257">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="9a53e-258">L’exemple suivant illustre l’utilisation de `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="9a53e-259">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-259">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="9a53e-260">L’exemple suivant illustre l’utilisation de `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="9a53e-261">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-261">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="9a53e-262">[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) est semblable `List.map` à, à ceci près que chaque élément produit une liste et que toutes ces listes sont concaténées dans une liste finale.</span><span class="sxs-lookup"><span data-stu-id="9a53e-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="9a53e-263">Dans le code suivant, chaque élément de la liste génère trois nombres.</span><span class="sxs-lookup"><span data-stu-id="9a53e-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="9a53e-264">Ils sont tous rassemblés dans une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="9a53e-265">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-265">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="9a53e-266">Vous pouvez également utiliser [List. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), qui prend une condition booléenne et produit une nouvelle liste qui se compose uniquement d’éléments qui répondent à la condition donnée.</span><span class="sxs-lookup"><span data-stu-id="9a53e-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="9a53e-267">La liste obtenue est `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="9a53e-268">Une combinaison de Map et Filter, [List. choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) vous permet de transformer et de sélectionner des éléments en même temps.</span><span class="sxs-lookup"><span data-stu-id="9a53e-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="9a53e-269">`List.choose` applique une fonction qui retourne une option à chaque élément d'une liste et renvoie une nouvelle liste des résultats pour les éléments quand la fonction retourne la valeur d'option `Some`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="9a53e-270">Le code suivant illustre l'utilisation de `List.choose` pour sélectionner des mots en majuscules dans une liste de mots.</span><span class="sxs-lookup"><span data-stu-id="9a53e-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="9a53e-271">La sortie se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="9a53e-271">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="9a53e-272">Opérations sur plusieurs listes</span><span class="sxs-lookup"><span data-stu-id="9a53e-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="9a53e-273">Les listes peuvent être jointes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-273">Lists can be joined together.</span></span> <span data-ttu-id="9a53e-274">Pour joindre deux listes en une seule, utilisez [List. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="9a53e-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="9a53e-275">Pour joindre plus de deux listes, utilisez [List. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="9a53e-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="9a53e-276">Opérations de repli et d'analyse</span><span class="sxs-lookup"><span data-stu-id="9a53e-276">Fold and Scan Operations</span></span>

<span data-ttu-id="9a53e-277">Certaines opérations de liste impliquent l'interdépendance entre tous les éléments de la liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="9a53e-278">Les opérations de repli et d’analyse sont similaires et, dans le cas `List.iter` `List.map` où vous appelez une fonction sur chaque élément, mais ces opérations fournissent un paramètre supplémentaire appelé l' *accumulation* qui transporte des informations via le calcul.</span><span class="sxs-lookup"><span data-stu-id="9a53e-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="9a53e-279">Utilisez `List.fold` pour effectuer un calcul sur une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="9a53e-280">L’exemple de code suivant illustre l’utilisation de [List. fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) pour effectuer diverses opérations.</span><span class="sxs-lookup"><span data-stu-id="9a53e-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="9a53e-281">La liste est parcourue ; l'accumulateur `acc` est une valeur passée au cours du calcul.</span><span class="sxs-lookup"><span data-stu-id="9a53e-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="9a53e-282">Le premier argument prend l'accumulateur et l'élément de liste, puis retourne le résultat intermédiaire du calcul pour cet élément de liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="9a53e-283">Le deuxième argument est la valeur initiale de l’accumulateur.</span><span class="sxs-lookup"><span data-stu-id="9a53e-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="9a53e-284">Les versions de ces fonctions dont le nom contient un chiffre s'effectuent sur plusieurs listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="9a53e-285">Par exemple, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) effectue des calculs sur deux listes.</span><span class="sxs-lookup"><span data-stu-id="9a53e-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="9a53e-286">L'exemple suivant montre l'utilisation de `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="9a53e-287">`List.fold`et [List. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) diffère dans qui `List.fold` retourne la valeur finale du paramètre supplémentaire, mais `List.scan` retourne la liste des valeurs intermédiaires (avec la valeur finale) du paramètre supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="9a53e-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="9a53e-288">Chacune de ces fonctions comprend une variation inverse, par exemple [List. foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), qui diffère selon l’ordre dans lequel la liste est parcourue et l’ordre des arguments.</span><span class="sxs-lookup"><span data-stu-id="9a53e-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="9a53e-289">En outre, `List.fold` et `List.foldBack` ont des variations, [List. fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) et [List. foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), qui acceptent deux listes de longueur égale.</span><span class="sxs-lookup"><span data-stu-id="9a53e-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="9a53e-290">La fonction qui s'exécute sur chaque élément peut utiliser des éléments correspondants aux deux listes pour effectuer une action.</span><span class="sxs-lookup"><span data-stu-id="9a53e-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="9a53e-291">Les types d’éléments des deux listes peuvent être différents, comme dans l’exemple suivant, où une liste contient des montants de transactions sur un compte bancaire et l’autre contient le type de transaction : dépôt ou retrait.</span><span class="sxs-lookup"><span data-stu-id="9a53e-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="9a53e-292">Pour un calcul tel qu'une addition, `List.fold` et `List.foldBack` ont le même effet car le résultat ne dépend pas de l'ordre de traversée.</span><span class="sxs-lookup"><span data-stu-id="9a53e-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="9a53e-293">Dans l'exemple ci-dessous, `List.foldBack` est utilisé pour ajouter les éléments à une liste.</span><span class="sxs-lookup"><span data-stu-id="9a53e-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="9a53e-294">Voici à nouveau l'exemple du compte bancaire.</span><span class="sxs-lookup"><span data-stu-id="9a53e-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="9a53e-295">Cette fois, un nouveau type de transaction est ajouté : le calcul d'intérêts.</span><span class="sxs-lookup"><span data-stu-id="9a53e-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="9a53e-296">Le solde de fin dépend désormais de l'ordre des transactions.</span><span class="sxs-lookup"><span data-stu-id="9a53e-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="9a53e-297">La fonction [List. Reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) est un peu comme `List.fold` et `List.scan` , à ceci près qu’au lieu de passer autour d’un accumulateur séparé, `List.reduce` prend une fonction qui accepte deux arguments du type d’élément au lieu d’un seul, et l’un de ces arguments joue le rôle d’accumulateur, ce qui signifie qu’elle stocke le résultat intermédiaire du calcul.</span><span class="sxs-lookup"><span data-stu-id="9a53e-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="9a53e-298">`List.reduce` commence par fonctionner sur les deux premiers éléments de liste, puis utilise le résultat de l'opération avec l'élément suivant.</span><span class="sxs-lookup"><span data-stu-id="9a53e-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="9a53e-299">Comme aucun accumulateur distinct ne possède son propre type, `List.reduce` ne peut être utilisé à la place de `List.fold` si l'accumulateur et le type d'élément ont le même type.</span><span class="sxs-lookup"><span data-stu-id="9a53e-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="9a53e-300">Le code suivant montre l'utilisation de `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="9a53e-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="9a53e-301">`List.reduce` lève une exception si la liste fournie ne comporte aucun élément.</span><span class="sxs-lookup"><span data-stu-id="9a53e-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="9a53e-302">Dans le code suivant, le premier appel à l’expression lambda reçoit les arguments 2 et 4, et retourne 6. L’appel suivant reçoit les arguments 6 et 10, le résultat est donc 16.</span><span class="sxs-lookup"><span data-stu-id="9a53e-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="9a53e-303">Conversion entre listes et autres types de collections</span><span class="sxs-lookup"><span data-stu-id="9a53e-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="9a53e-304">Le module `List` fournit des fonctions pour convertir vers et depuis des séquences et des tableaux.</span><span class="sxs-lookup"><span data-stu-id="9a53e-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="9a53e-305">Pour convertir vers ou à partir d’une séquence, utilisez [List. toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) ou [List. ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="9a53e-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="9a53e-306">Pour convertir vers ou à partir d’un tableau, utilisez [List. ToArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) ou [List. ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="9a53e-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="9a53e-307">Opérations supplémentaires</span><span class="sxs-lookup"><span data-stu-id="9a53e-307">Additional Operations</span></span>

<span data-ttu-id="9a53e-308">Pour plus d’informations sur les opérations supplémentaires sur les listes, consultez le [module Collections. List](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)de la rubrique de référence de la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="9a53e-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a53e-309">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a53e-309">See also</span></span>

- [<span data-ttu-id="9a53e-310">Informations de référence sur le langage F #</span><span class="sxs-lookup"><span data-stu-id="9a53e-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="9a53e-311">Types F#</span><span class="sxs-lookup"><span data-stu-id="9a53e-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="9a53e-312">Séquences</span><span class="sxs-lookup"><span data-stu-id="9a53e-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="9a53e-313">Tableaux</span><span class="sxs-lookup"><span data-stu-id="9a53e-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="9a53e-314">Options</span><span class="sxs-lookup"><span data-stu-id="9a53e-314">Options</span></span>](options.md)

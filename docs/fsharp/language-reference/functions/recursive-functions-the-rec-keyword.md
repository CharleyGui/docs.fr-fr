---
title: 'Fonctions récursives : mot clé rec'
description: "Découvrez comment le mot clé F # 'Rec’est utilisé avec le mot clé’Let’pour définir une fonction récursive."
ms.date: 08/12/2020
ms.openlocfilehash: 389357bd13cef39b1d07972c1a3167320b61612b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558710"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="63dbe-103">Fonctions récursives : mot clé rec</span><span class="sxs-lookup"><span data-stu-id="63dbe-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="63dbe-104">Le `rec` mot clé est utilisé conjointement avec le `let` mot clé pour définir une fonction récursive.</span><span class="sxs-lookup"><span data-stu-id="63dbe-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="63dbe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63dbe-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
    function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
    function1-body

and function2-nameparameter-list =
    function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="63dbe-106">Notes</span><span class="sxs-lookup"><span data-stu-id="63dbe-106">Remarks</span></span>

<span data-ttu-id="63dbe-107">Fonctions récursives : les fonctions qui s’appellent elles-mêmes sont identifiées explicitement dans le langage F # avec le `rec` mot clé.</span><span class="sxs-lookup"><span data-stu-id="63dbe-107">Recursive functions - functions that call themselves - are identified explicitly in the F# language with the `rec` keyword.</span></span> <span data-ttu-id="63dbe-108">Le `rec` mot clé rend le nom de la `let` liaison disponible dans son corps.</span><span class="sxs-lookup"><span data-stu-id="63dbe-108">The `rec` keyword makes the name of the `let` binding available in its body.</span></span>

<span data-ttu-id="63dbe-109">L’exemple suivant montre une fonction récursive qui calcule le *n*<sup>ième</sup> nombre de Fibonacci à l’aide de la définition mathématique.</span><span class="sxs-lookup"><span data-stu-id="63dbe-109">The following example shows a recursive function that computes the *n*<sup>th</sup> Fibonacci number using the mathematical definition.</span></span>

```fsharp
let fib n =
    match n with
    | 0 | 1 -> 1
    | n -> fib (n-1) + fib (n-2)
```

> [!NOTE]
> <span data-ttu-id="63dbe-110">Dans la pratique, le code comme l’exemple précédent n’est pas idéal, car il unecessarily recalcule les valeurs qui ont déjà été calculées.</span><span class="sxs-lookup"><span data-stu-id="63dbe-110">In practice, code like the previous sample is not ideal because it unecessarily recomputes values that have already been computed.</span></span> <span data-ttu-id="63dbe-111">Cela est dû au fait qu’elle n’est pas une fin récursive, ce qui est expliqué plus loin dans cet article.</span><span class="sxs-lookup"><span data-stu-id="63dbe-111">This is because it is not tail recursive, which is explained further in this article.</span></span>

<span data-ttu-id="63dbe-112">Les méthodes sont implicitement récursives dans le type dans lequel elles sont définies, ce qui signifie qu’il n’est pas nécessaire d’ajouter le `rec` mot clé.</span><span class="sxs-lookup"><span data-stu-id="63dbe-112">Methods are implicitly recursive within the type they are defined in, meaning there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="63dbe-113">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="63dbe-113">For example:</span></span>

```fsharp
type MyClass() =
    member this.Fib(n) =
        match n with
        | 0 | 1 -> 1
        | n -> this.Fib(n-1) + this.Fib(n-2)
```

<span data-ttu-id="63dbe-114">Toutefois, les liaisons Let dans les classes ne sont pas implicitement récursives.</span><span class="sxs-lookup"><span data-stu-id="63dbe-114">Let bindings within classes are not implicitly recursive, though.</span></span> <span data-ttu-id="63dbe-115">Toutes les `let` fonctions liées nécessitent le `rec` mot clé.</span><span class="sxs-lookup"><span data-stu-id="63dbe-115">All `let`-bound functions require the `rec` keyword.</span></span>

## <a name="tail-recursion"></a><span data-ttu-id="63dbe-116">Récurrence de la fin</span><span class="sxs-lookup"><span data-stu-id="63dbe-116">Tail recursion</span></span>

<span data-ttu-id="63dbe-117">Pour certaines fonctions récursives, il est nécessaire de refactoriser une définition plus « pure » vers une définition qui est une [fin récursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span><span class="sxs-lookup"><span data-stu-id="63dbe-117">For some recursive functions, it is necessary to refactor a more "pure" definition to one that is [tail recursive](https://cs.stackexchange.com/questions/6230/what-is-tail-recursion).</span></span> <span data-ttu-id="63dbe-118">Cela évite les recalculs inutiles.</span><span class="sxs-lookup"><span data-stu-id="63dbe-118">This prevents unnecessary recomputations.</span></span> <span data-ttu-id="63dbe-119">Par exemple, le générateur de nombres Fibonacci précédent peut être réécrit comme suit :</span><span class="sxs-lookup"><span data-stu-id="63dbe-119">For example, the previous fibonacci number generator can be rewritten like this:</span></span>

```fsharp
let fib n =
    let rec loop acc1 acc2 n =
        match n with
        | 0 -> acc1
        | 1 -> acc2
        | _ ->
            loop acc2 (acc1 + acc2) (n - 1)
    loop 0 1 n
```

<span data-ttu-id="63dbe-120">Il s’agit d’une implémentation plus complexe.</span><span class="sxs-lookup"><span data-stu-id="63dbe-120">This is a more complicated implementation.</span></span> <span data-ttu-id="63dbe-121">La génération d’un nombre de Fibonacci est un bon exemple d’algorithme naïve qui est mathématiquement pur, mais inefficace dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="63dbe-121">Generating a fibonacci number is a great example of a "naive" algorithm that's mathematically pure but inefficient in practice.</span></span> <span data-ttu-id="63dbe-122">Plusieurs aspects le rendent efficace en F # tout en restant défini de manière récursive :</span><span class="sxs-lookup"><span data-stu-id="63dbe-122">Several aspects make it efficient in F# while still remaining recursively defined:</span></span>

* <span data-ttu-id="63dbe-123">Une fonction interne récursive nommée `loop` , qui est un modèle F # idiomatique.</span><span class="sxs-lookup"><span data-stu-id="63dbe-123">A recursive inner function named `loop`, which is an idiomatic F# pattern.</span></span>
* <span data-ttu-id="63dbe-124">Deux paramètres d’accumulation, qui réussissent à accumuler des valeurs à des appels récursifs.</span><span class="sxs-lookup"><span data-stu-id="63dbe-124">Two accumulator parameters, which pass accumulate values to recursive calls.</span></span>
* <span data-ttu-id="63dbe-125">Contrôle de la valeur de `n` pour retourner un cumul spécifique.</span><span class="sxs-lookup"><span data-stu-id="63dbe-125">A check on the value of `n` to return a specific accumulate.</span></span>

<span data-ttu-id="63dbe-126">Si cet exemple a été écrit de façon itérative avec une boucle, le code doit ressembler à deux valeurs différentes qui accumulent des nombres jusqu’à ce qu’une condition particulière soit remplie.</span><span class="sxs-lookup"><span data-stu-id="63dbe-126">If this example were written iteratively with a loop, the code would look similar with two different values accumulating numbers until a particular condition was met.</span></span>

<span data-ttu-id="63dbe-127">La raison pour laquelle il s’agit d’une fin récursive est que l’appel récursif n’a pas besoin d’enregistrer les valeurs sur la pile des appels.</span><span class="sxs-lookup"><span data-stu-id="63dbe-127">The reason why this is tail-recursive is because the recursive call does not need to save any values on the call stack.</span></span> <span data-ttu-id="63dbe-128">Toutes les valeurs intermédiaires calculées sont accumulées via des entrées dans la fonction interne.</span><span class="sxs-lookup"><span data-stu-id="63dbe-128">All intermediate values being calculated are accumulated via inputs to the inner function.</span></span> <span data-ttu-id="63dbe-129">Cela permet également au compilateur F # d’optimiser le code pour qu’il soit aussi rapide que si vous aviez écrit des éléments tels qu’une `while` boucle.</span><span class="sxs-lookup"><span data-stu-id="63dbe-129">This also allows the F# compiler to optimize the code to be just as fast as if you had written something like a `while` loop.</span></span>

<span data-ttu-id="63dbe-130">Il est courant d’écrire du code F # qui traite de manière récursive un événement à l’aide d’une fonction interne et externe, comme le montre l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="63dbe-130">It's common to write F# code that recursively processes something with an inner and outer function, as the previous example shows.</span></span> <span data-ttu-id="63dbe-131">La fonction interne utilise la récursivité de fin, tandis que la fonction externe a une meilleure interface pour les appelants.</span><span class="sxs-lookup"><span data-stu-id="63dbe-131">The inner function uses tail recursion, while the outer function has a better interface for callers.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="63dbe-132">Fonctions mutuellement récursives</span><span class="sxs-lookup"><span data-stu-id="63dbe-132">Mutually Recursive Functions</span></span>

<span data-ttu-id="63dbe-133">Parfois, les fonctions sont *mutuellement récursives*, ce qui signifie que les appels forment un cercle, où une fonction appelle une autre qui, à son tour, appelle la première, avec un nombre quelconque d’appels entre les deux.</span><span class="sxs-lookup"><span data-stu-id="63dbe-133">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="63dbe-134">Vous devez définir de telles fonctions dans une `let` liaison, en utilisant le `and` mot clé pour les lier ensemble.</span><span class="sxs-lookup"><span data-stu-id="63dbe-134">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="63dbe-135">L’exemple suivant montre deux fonctions mutuellement récursives.</span><span class="sxs-lookup"><span data-stu-id="63dbe-135">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="recursive-values"></a><span data-ttu-id="63dbe-136">Valeurs récursives</span><span class="sxs-lookup"><span data-stu-id="63dbe-136">Recursive values</span></span>

<span data-ttu-id="63dbe-137">Vous pouvez également définir une `let` valeur liée à une valeur récursive.</span><span class="sxs-lookup"><span data-stu-id="63dbe-137">You can also define a `let`-bound value to be recursive.</span></span> <span data-ttu-id="63dbe-138">Cela est parfois fait pour la journalisation.</span><span class="sxs-lookup"><span data-stu-id="63dbe-138">This is sometimes done for logging.</span></span> <span data-ttu-id="63dbe-139">Avec F # 5 et la `nameof` fonction, vous pouvez effectuer cette opération :</span><span class="sxs-lookup"><span data-stu-id="63dbe-139">With F# 5 and the `nameof` function, you can do this:</span></span>

```fsharp
let rec nameDoubles = nameof nameDoubles + nameof nameDoubles
```

## <a name="see-also"></a><span data-ttu-id="63dbe-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63dbe-140">See also</span></span>

- [<span data-ttu-id="63dbe-141">Fonctions</span><span class="sxs-lookup"><span data-stu-id="63dbe-141">Functions</span></span>](index.md)

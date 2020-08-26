---
title: Fonctions de première classe
description: 'En savoir plus sur les fonctions de première classe et leur importance pour la programmation fonctionnelle en F #.'
ms.date: 10/29/2018
ms.openlocfilehash: 1dc8eae1655187282f05bf4e9501ecc8a17deba8
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810909"
---
# <a name="first-class-functions"></a><span data-ttu-id="824ce-103">Fonctions de première classe</span><span class="sxs-lookup"><span data-stu-id="824ce-103">First-class functions</span></span>

<span data-ttu-id="824ce-104">Une caractéristique de définition des langages de programmation fonctionnelle est l’élévation de fonctions à l’état de première classe.</span><span class="sxs-lookup"><span data-stu-id="824ce-104">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="824ce-105">Vous devez être en mesure de faire avec une fonction tout ce que vous pouvez faire avec les valeurs des autres types intégrés et être en mesure de le faire avec un degré comparable d’effort.</span><span class="sxs-lookup"><span data-stu-id="824ce-105">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="824ce-106">Les mesures typiques de l’état de première classe sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="824ce-106">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="824ce-107">Pouvez-vous lier des fonctions à des identificateurs ?</span><span class="sxs-lookup"><span data-stu-id="824ce-107">Can you bind functions to identifiers?</span></span> <span data-ttu-id="824ce-108">Autrement dit, pouvez-vous leur attribuer des noms ?</span><span class="sxs-lookup"><span data-stu-id="824ce-108">That is, can you give them names?</span></span>

- <span data-ttu-id="824ce-109">Pouvez-vous stocker des fonctions dans des structures de données, comme dans une liste ?</span><span class="sxs-lookup"><span data-stu-id="824ce-109">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="824ce-110">Pouvez-vous passer une fonction en tant qu’argument dans un appel de fonction ?</span><span class="sxs-lookup"><span data-stu-id="824ce-110">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="824ce-111">Pouvez-vous retourner une fonction à partir d’un appel de fonction ?</span><span class="sxs-lookup"><span data-stu-id="824ce-111">Can you return a function from a function call?</span></span>

<span data-ttu-id="824ce-112">Les deux dernières mesures définissent ce que l’on appelle des *opérations d’ordre supérieur* ou *des fonctions d’ordre supérieur*.</span><span class="sxs-lookup"><span data-stu-id="824ce-112">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="824ce-113">Les fonctions d’ordre supérieur acceptent des fonctions comme arguments et retournent des fonctions comme valeur d’appels de fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-113">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="824ce-114">Ces opérations prennent en charge un tel mainstays de la programmation fonctionnelle comme fonctions de mappage et la composition de fonctions.</span><span class="sxs-lookup"><span data-stu-id="824ce-114">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>

## <a name="give-the-value-a-name"></a><span data-ttu-id="824ce-115">Donnez un nom à la valeur</span><span class="sxs-lookup"><span data-stu-id="824ce-115">Give the Value a Name</span></span>

<span data-ttu-id="824ce-116">Si une fonction est une valeur de première classe, vous devez être en mesure de la nommer, tout comme vous pouvez nommer des entiers, des chaînes et d’autres types intégrés.</span><span class="sxs-lookup"><span data-stu-id="824ce-116">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="824ce-117">Pour ce faire, vous pouvez faire appel à la documentation sur la programmation fonctionnelle pour lier un identificateur à une valeur.</span><span class="sxs-lookup"><span data-stu-id="824ce-117">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="824ce-118">F # utilise des [ `let` liaisons](../language-reference/functions/let-bindings.md) pour lier les noms aux valeurs : `let <identifier> = <value>` .</span><span class="sxs-lookup"><span data-stu-id="824ce-118">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="824ce-119">Le code suivant illustre deux exemples.</span><span class="sxs-lookup"><span data-stu-id="824ce-119">The following code shows two examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="824ce-120">Vous pouvez nommer une fonction tout aussi facilement.</span><span class="sxs-lookup"><span data-stu-id="824ce-120">You can name a function just as easily.</span></span> <span data-ttu-id="824ce-121">L’exemple suivant définit une fonction nommée `squareIt` en liant l’identificateur `squareIt` à l' [expression lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n` .</span><span class="sxs-lookup"><span data-stu-id="824ce-121">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="824ce-122">`squareIt`La fonction a un paramètre, `n` , et retourne le carré de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="824ce-122">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="824ce-123">F # fournit la syntaxe plus concise suivante pour obtenir le même résultat avec moins de frappes.</span><span class="sxs-lookup"><span data-stu-id="824ce-123">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="824ce-124">Les exemples qui suivent utilisent principalement le premier style, `let <function-name> = <lambda-expression>` , pour mettre en évidence les similarités entre la déclaration de fonctions et la déclaration d’autres types de valeurs.</span><span class="sxs-lookup"><span data-stu-id="824ce-124">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="824ce-125">Toutefois, toutes les fonctions nommées peuvent également être écrites avec la syntaxe concise.</span><span class="sxs-lookup"><span data-stu-id="824ce-125">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="824ce-126">Certains des exemples sont écrits d’une manière ou d’une autre.</span><span class="sxs-lookup"><span data-stu-id="824ce-126">Some of the examples are written in both ways.</span></span>

## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="824ce-127">Stocker la valeur dans une structure de données</span><span class="sxs-lookup"><span data-stu-id="824ce-127">Store the Value in a Data Structure</span></span>

<span data-ttu-id="824ce-128">Une valeur de première classe peut être stockée dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="824ce-128">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="824ce-129">Le code suivant montre des exemples qui stockent des valeurs dans des listes et dans des tuples.</span><span class="sxs-lookup"><span data-stu-id="824ce-129">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="824ce-130">Pour vérifier qu’un nom de fonction stocké dans un tuple correspond en fait à une fonction, l’exemple suivant utilise `fst` les `snd` opérateurs et pour extraire le premier et le deuxième élément du Tuple `funAndArgTuple` .</span><span class="sxs-lookup"><span data-stu-id="824ce-130">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="824ce-131">Le premier élément du tuple est `squareIt` et le deuxième élément est `num` .</span><span class="sxs-lookup"><span data-stu-id="824ce-131">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="824ce-132">L’identificateur `num` est lié dans un exemple précédent à l’entier 10, un argument valide pour la `squareIt` fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-132">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="824ce-133">La deuxième expression applique le premier élément du tuple au deuxième élément du tuple : `squareIt num` .</span><span class="sxs-lookup"><span data-stu-id="824ce-133">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="824ce-134">De même, tout comme l’identificateur `num` et l’entier 10 peuvent être utilisés indifféremment, l’identificateur et l' `squareIt` expression lambda peuvent être utilisés `fun n -> n * n` .</span><span class="sxs-lookup"><span data-stu-id="824ce-134">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet25.fs)]

## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="824ce-135">Passer la valeur en tant qu’argument</span><span class="sxs-lookup"><span data-stu-id="824ce-135">Pass the Value as an Argument</span></span>

<span data-ttu-id="824ce-136">Si une valeur a un état de première classe dans une langue, vous pouvez la passer en tant qu’argument à une fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-136">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="824ce-137">Par exemple, il est courant de passer des entiers et des chaînes en tant qu’arguments.</span><span class="sxs-lookup"><span data-stu-id="824ce-137">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="824ce-138">Le code suivant affiche les entiers et les chaînes passés comme arguments en F #.</span><span class="sxs-lookup"><span data-stu-id="824ce-138">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="824ce-139">Si les fonctions ont l’état de première classe, vous devez être en mesure de les passer comme arguments de la même façon.</span><span class="sxs-lookup"><span data-stu-id="824ce-139">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="824ce-140">N’oubliez pas qu’il s’agit de la première caractéristique des fonctions d’ordre supérieur.</span><span class="sxs-lookup"><span data-stu-id="824ce-140">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="824ce-141">Dans l’exemple suivant, la fonction `applyIt` a deux paramètres, `op` et `arg` .</span><span class="sxs-lookup"><span data-stu-id="824ce-141">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="824ce-142">Si vous envoyez dans une fonction avec un paramètre pour `op` et un argument approprié pour la fonction à `arg` , la fonction retourne le résultat de l’application de `op` à `arg` .</span><span class="sxs-lookup"><span data-stu-id="824ce-142">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="824ce-143">Dans l’exemple suivant, l’argument de fonction et l’argument entier sont envoyés de la même manière, à l’aide de leurs noms.</span><span class="sxs-lookup"><span data-stu-id="824ce-143">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="824ce-144">La possibilité d’envoyer une fonction en tant qu’argument à une autre fonction sous-tend des abstractions courantes dans des langages de programmation fonctionnelle, tels que des opérations de mappage ou de filtre.</span><span class="sxs-lookup"><span data-stu-id="824ce-144">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="824ce-145">Une opération de mappage, par exemple, est une fonction d’ordre supérieur qui capture le calcul partagé par des fonctions qui parcourent une liste, effectuent une opération sur chaque élément, puis renvoient une liste des résultats.</span><span class="sxs-lookup"><span data-stu-id="824ce-145">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="824ce-146">Vous pouvez incrémenter chaque élément dans une liste d’entiers, ou pour placer chaque élément dans une liste de chaînes en majuscules.</span><span class="sxs-lookup"><span data-stu-id="824ce-146">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="824ce-147">La partie sujette aux erreurs du calcul est le processus récursif qui parcourt la liste et génère une liste des résultats à retourner.</span><span class="sxs-lookup"><span data-stu-id="824ce-147">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="824ce-148">Cette partie est capturée dans la fonction de mappage.</span><span class="sxs-lookup"><span data-stu-id="824ce-148">That part is captured in the mapping function.</span></span> <span data-ttu-id="824ce-149">Tout ce que vous devez écrire pour une application particulière est la fonction que vous souhaitez appliquer à chaque élément de la liste (ajout, élévation, modification de la casse).</span><span class="sxs-lookup"><span data-stu-id="824ce-149">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="824ce-150">Cette fonction est envoyée en tant qu’argument à la fonction de mappage, de la même façon que `squareIt` `applyIt` dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="824ce-150">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="824ce-151">F # fournit des méthodes cartographiques pour la plupart des types de collections, y compris les [listes](../language-reference/lists.md), les [tableaux](../language-reference/arrays.md)et les [séquences](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="824ce-151">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="824ce-152">Les exemples suivants utilisent des listes.</span><span class="sxs-lookup"><span data-stu-id="824ce-152">The following examples use lists.</span></span> <span data-ttu-id="824ce-153">La syntaxe est `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="824ce-153">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="824ce-154">Pour plus d’informations, consultez [listes](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="824ce-154">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="824ce-155">Retourne la valeur d’un appel de fonction</span><span class="sxs-lookup"><span data-stu-id="824ce-155">Return the Value from a Function Call</span></span>

<span data-ttu-id="824ce-156">Enfin, si une fonction a l’état de première classe dans un langage, vous devez être en mesure de la retourner comme valeur d’un appel de fonction, de la même façon que vous retournez d’autres types, tels que des entiers et des chaînes.</span><span class="sxs-lookup"><span data-stu-id="824ce-156">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="824ce-157">Les appels de fonction suivants retournent des entiers et les affichent.</span><span class="sxs-lookup"><span data-stu-id="824ce-157">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="824ce-158">L’appel de fonction suivant retourne une chaîne.</span><span class="sxs-lookup"><span data-stu-id="824ce-158">The following function call returns a string.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="824ce-159">L’appel de fonction suivant, déclaré Inline, retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="824ce-159">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="824ce-160">La valeur affichée est `True` .</span><span class="sxs-lookup"><span data-stu-id="824ce-160">The value displayed is `True`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="824ce-161">La possibilité de retourner une fonction comme valeur d’un appel de fonction est la deuxième caractéristique des fonctions d’ordre supérieur.</span><span class="sxs-lookup"><span data-stu-id="824ce-161">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="824ce-162">Dans l’exemple suivant, `checkFor` est défini comme une fonction qui accepte un argument, `item` , et retourne une nouvelle fonction comme sa valeur.</span><span class="sxs-lookup"><span data-stu-id="824ce-162">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="824ce-163">La fonction retournée prend une liste comme argument, `lst` , et recherche `item` dans `lst` .</span><span class="sxs-lookup"><span data-stu-id="824ce-163">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="824ce-164">Si `item` est présent, la fonction retourne `true` .</span><span class="sxs-lookup"><span data-stu-id="824ce-164">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="824ce-165">Si `item` n’est pas présent, la fonction retourne `false` .</span><span class="sxs-lookup"><span data-stu-id="824ce-165">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="824ce-166">Comme dans la section précédente, le code suivant utilise une fonction de liste fournie, [List. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), pour effectuer une recherche dans la liste.</span><span class="sxs-lookup"><span data-stu-id="824ce-166">As in the previous section, the following code uses a provided list function, [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists), to search the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="824ce-167">Le code suivant utilise `checkFor` pour créer une fonction qui accepte un argument, une liste et recherche 7 dans la liste.</span><span class="sxs-lookup"><span data-stu-id="824ce-167">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="824ce-168">L’exemple suivant utilise l’état de première classe des fonctions en F # pour déclarer une fonction, `compose` , qui retourne une composition de deux arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-168">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet34.fs)]

> [!NOTE]
> <span data-ttu-id="824ce-169">Pour une version encore plus concise, consultez la section suivante, « fonctions curryfiée ».</span><span class="sxs-lookup"><span data-stu-id="824ce-169">For an even shorter version, see the following section, "Curried Functions."</span></span>

<span data-ttu-id="824ce-170">Le code suivant envoie deux fonctions comme arguments à `compose` , qui acceptent toutes deux un seul argument du même type.</span><span class="sxs-lookup"><span data-stu-id="824ce-170">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="824ce-171">La valeur de retour est une nouvelle fonction qui est une composition des deux arguments de fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-171">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet35.fs)]

> [!NOTE]
> <span data-ttu-id="824ce-172">F # fournit deux opérateurs, `<<` et `>>` , qui composent des fonctions.</span><span class="sxs-lookup"><span data-stu-id="824ce-172">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="824ce-173">Par exemple, `let squareAndDouble2 = doubleIt << squareIt` est équivalent à `let squareAndDouble = compose doubleIt squareIt` dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="824ce-173">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="824ce-174">L’exemple suivant de retour d’une fonction comme valeur d’un appel de fonction crée un jeu d’estimation simple.</span><span class="sxs-lookup"><span data-stu-id="824ce-174">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="824ce-175">Pour créer un jeu, appelez `makeGame` avec la valeur que vous souhaitez qu’une personne devine soit envoyée pour `target` .</span><span class="sxs-lookup"><span data-stu-id="824ce-175">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="824ce-176">La valeur de retour de la fonction `makeGame` est une fonction qui accepte un argument (l’estimation) et indique si l’estimation est correcte.</span><span class="sxs-lookup"><span data-stu-id="824ce-176">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="824ce-177">Le code suivant appelle `makeGame` , en envoyant la valeur `7` pour `target` .</span><span class="sxs-lookup"><span data-stu-id="824ce-177">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="824ce-178">L’identificateur `playGame` est lié à l’expression lambda retournée.</span><span class="sxs-lookup"><span data-stu-id="824ce-178">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="824ce-179">Par conséquent, `playGame` est une fonction qui prend comme valeur un argument pour `guess` .</span><span class="sxs-lookup"><span data-stu-id="824ce-179">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet37.fs)]

## <a name="curried-functions"></a><span data-ttu-id="824ce-180">Fonctions curryfiée</span><span class="sxs-lookup"><span data-stu-id="824ce-180">Curried Functions</span></span>

<span data-ttu-id="824ce-181">La plupart des exemples de la section précédente peuvent être écrits de façon plus concise en tirant parti de la *curryfication* implicite dans les déclarations de fonction F #.</span><span class="sxs-lookup"><span data-stu-id="824ce-181">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="824ce-182">La curryfication est un processus qui transforme une fonction qui a plusieurs paramètres en une série de fonctions incorporées, chacune d’elles ayant un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="824ce-182">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="824ce-183">En F #, les fonctions qui ont plusieurs paramètres sont curryfiée par nature.</span><span class="sxs-lookup"><span data-stu-id="824ce-183">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="824ce-184">Par exemple, `compose` dans la section précédente, vous pouvez écrire comme indiqué dans le style concis suivant, avec trois paramètres.</span><span class="sxs-lookup"><span data-stu-id="824ce-184">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="824ce-185">Toutefois, le résultat est une fonction d’un paramètre qui retourne une fonction d’un paramètre qui, à son tour, retourne une autre fonction d’un paramètre, comme indiqué dans `compose4curried` .</span><span class="sxs-lookup"><span data-stu-id="824ce-185">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="824ce-186">Vous pouvez accéder à cette fonction de plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="824ce-186">You can access this function in several ways.</span></span> <span data-ttu-id="824ce-187">Chacun des exemples suivants retourne et affiche 18.</span><span class="sxs-lookup"><span data-stu-id="824ce-187">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="824ce-188">Vous pouvez remplacer `compose4` par `compose4curried` dans l’un des exemples.</span><span class="sxs-lookup"><span data-stu-id="824ce-188">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="824ce-189">Pour vérifier que la fonction fonctionne toujours comme auparavant, réessayez les cas de test d’origine.</span><span class="sxs-lookup"><span data-stu-id="824ce-189">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet41.fs)]

> [!NOTE]
> <span data-ttu-id="824ce-190">Vous pouvez restreindre la curryfication en encadrant les paramètres dans les tuples.</span><span class="sxs-lookup"><span data-stu-id="824ce-190">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="824ce-191">Pour plus d’informations, consultez « modèles de paramètres » dans [paramètres et arguments](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="824ce-191">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="824ce-192">L’exemple suivant utilise une curryfication implicite pour écrire une version plus petite de `makeGame` .</span><span class="sxs-lookup"><span data-stu-id="824ce-192">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="824ce-193">Les détails de la façon dont `makeGame` construit et retourne la `game` fonction sont moins explicites dans ce format, mais vous pouvez vérifier en utilisant les cas de test d’origine que le résultat est le même.</span><span class="sxs-lookup"><span data-stu-id="824ce-193">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="824ce-194">Pour plus d’informations sur la curryfication, consultez « application partielle d’arguments » dans les [fonctions](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="824ce-194">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>

## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="824ce-195">L’identificateur et la définition de fonction sont interchangeables</span><span class="sxs-lookup"><span data-stu-id="824ce-195">Identifier and Function Definition Are Interchangeable</span></span>

<span data-ttu-id="824ce-196">Le nom de la variable `num` dans les exemples précédents correspond à l’entier 10, et il n’est pas surprenant que `num` , si est valide, 10 soit également valide.</span><span class="sxs-lookup"><span data-stu-id="824ce-196">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="824ce-197">Il en va de même pour les identificateurs de fonction et leurs valeurs : partout où le nom de la fonction peut être utilisé, l’expression lambda à laquelle elle est liée peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="824ce-197">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="824ce-198">L’exemple suivant définit une `Boolean` fonction appelée `isNegative` , puis utilise le nom de la fonction et la définition de la fonction de façon interchangeable.</span><span class="sxs-lookup"><span data-stu-id="824ce-198">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="824ce-199">Les trois exemples suivants retournent et affichent `False` .</span><span class="sxs-lookup"><span data-stu-id="824ce-199">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="824ce-200">Pour aller plus loin, remplacez la valeur `applyIt` de pour `applyIt` .</span><span class="sxs-lookup"><span data-stu-id="824ce-200">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="824ce-201">Les fonctions sont des valeurs de première classe en F\#</span><span class="sxs-lookup"><span data-stu-id="824ce-201">Functions Are First-Class Values in F\#</span></span>

<span data-ttu-id="824ce-202">Les exemples des sections précédentes montrent que les fonctions en F # satisfont les critères pour les valeurs de première classe en F # :</span><span class="sxs-lookup"><span data-stu-id="824ce-202">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="824ce-203">Vous pouvez lier un identificateur à une définition de fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-203">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="824ce-204">Vous pouvez stocker une fonction dans une structure de données.</span><span class="sxs-lookup"><span data-stu-id="824ce-204">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="824ce-205">Vous pouvez passer une fonction comme argument.</span><span class="sxs-lookup"><span data-stu-id="824ce-205">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="824ce-206">Vous pouvez retourner une fonction comme valeur d’un appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="824ce-206">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="824ce-207">Pour plus d’informations sur F #, consultez la référence sur le [langage f #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="824ce-207">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="824ce-208">Exemple</span><span class="sxs-lookup"><span data-stu-id="824ce-208">Example</span></span>

### <a name="description"></a><span data-ttu-id="824ce-209">Description</span><span class="sxs-lookup"><span data-stu-id="824ce-209">Description</span></span>

<span data-ttu-id="824ce-210">Le code suivant contient tous les exemples de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="824ce-210">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="824ce-211">Code</span><span class="sxs-lookup"><span data-stu-id="824ce-211">Code</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/contour/snippet47.fs)]

## <a name="see-also"></a><span data-ttu-id="824ce-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="824ce-212">See also</span></span>

- [<span data-ttu-id="824ce-213">Listes</span><span class="sxs-lookup"><span data-stu-id="824ce-213">Lists</span></span>](../language-reference/lists.md)
- [<span data-ttu-id="824ce-214">Tuples</span><span class="sxs-lookup"><span data-stu-id="824ce-214">Tuples</span></span>](../language-reference/tuples.md)
- [<span data-ttu-id="824ce-215">Fonctions</span><span class="sxs-lookup"><span data-stu-id="824ce-215">Functions</span></span>](../language-reference/functions/index.md)
- [<span data-ttu-id="824ce-216">`let` Liaisons</span><span class="sxs-lookup"><span data-stu-id="824ce-216">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)
- [<span data-ttu-id="824ce-217">Expressions lambda : `fun` mot clé</span><span class="sxs-lookup"><span data-stu-id="824ce-217">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)

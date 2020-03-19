---
title: Paramètres et arguments
description: Renseignez-vous sur le support linguistique de FMD pour définir les paramètres et transmettre des arguments aux fonctions, aux méthodes et aux propriétés.
ms.date: 12/04/2019
ms.openlocfilehash: b234ef939128e7cf09d35f9580d4d5010d7dc639
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400196"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="210cd-103">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="210cd-103">Parameters and Arguments</span></span>

<span data-ttu-id="210cd-104">Ce sujet décrit le support linguistique pour définir les paramètres et passer des arguments aux fonctions, aux méthodes et aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="210cd-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="210cd-105">Il comprend des informations sur la façon de passer par référence, et comment définir et utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="210cd-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="210cd-106">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="210cd-106">Parameters and Arguments</span></span>

<span data-ttu-id="210cd-107">Le *paramètre* de terme est utilisé pour décrire les noms des valeurs qui devraient être fournies.</span><span class="sxs-lookup"><span data-stu-id="210cd-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="210cd-108">Le terme *argument* est utilisé pour les valeurs prévues pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="210cd-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="210cd-109">Les paramètres peuvent être spécifiés sous forme de tuple ou de curry, ou dans une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="210cd-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="210cd-110">Vous pouvez passer des arguments en utilisant un nom de paramètre explicite.</span><span class="sxs-lookup"><span data-stu-id="210cd-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="210cd-111">Les paramètres des méthodes peuvent être spécifiés comme facultatifs et une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="210cd-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="210cd-112">Modèles de paramètres</span><span class="sxs-lookup"><span data-stu-id="210cd-112">Parameter Patterns</span></span>

<span data-ttu-id="210cd-113">Les paramètres fournis aux fonctions et aux méthodes sont, en général, des modèles séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="210cd-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="210cd-114">Cela signifie que, en principe, l’un des modèles décrits dans [Les expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.</span><span class="sxs-lookup"><span data-stu-id="210cd-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="210cd-115">Les méthodes utilisent généralement la forme de tuple des arguments de passage.</span><span class="sxs-lookup"><span data-stu-id="210cd-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="210cd-116">Cela permet d’obtenir un résultat plus clair du point de vue d’autres langues .NET parce que la forme de tuple correspond à la façon dont les arguments sont adoptés dans des méthodes .NET.</span><span class="sxs-lookup"><span data-stu-id="210cd-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="210cd-117">La forme au curry est le plus `let` souvent utilisée avec les fonctions créées à l’aide de fixations.</span><span class="sxs-lookup"><span data-stu-id="210cd-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="210cd-118">Le pseudocode suivant montre des exemples de tuple et d’arguments au curry.</span><span class="sxs-lookup"><span data-stu-id="210cd-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="210cd-119">Des formes combinées sont possibles lorsque certains arguments sont en tuples et d’autres ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="210cd-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="210cd-120">D’autres modèles peuvent également être utilisés dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il pourrait y avoir une correspondance incomplète au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="210cd-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="210cd-121">L’exception `MatchFailureException` est générée lorsque la valeur d’un argument ne correspond pas aux modèles spécifiés dans la liste des paramètres.</span><span class="sxs-lookup"><span data-stu-id="210cd-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="210cd-122">Le compilateur émet un avertissement lorsqu’un modèle de paramètre permet des correspondances incomplètes.</span><span class="sxs-lookup"><span data-stu-id="210cd-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="210cd-123">Au moins un autre modèle est généralement utile pour les listes de paramètres, et c’est le modèle wildcard.</span><span class="sxs-lookup"><span data-stu-id="210cd-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="210cd-124">Vous utilisez le modèle wildcard dans une liste de paramètres lorsque vous voulez simplement ignorer tous les arguments qui sont fournis.</span><span class="sxs-lookup"><span data-stu-id="210cd-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="210cd-125">Le code suivant illustre l’utilisation du modèle wildcard dans une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="210cd-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="210cd-126">Le modèle wildcard peut être utile chaque fois que vous n’avez pas besoin des arguments passés, comme dans le point d’entrée principal d’un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande qui sont normalement fournis comme un tableau de chaîne, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="210cd-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="210cd-127">D’autres modèles qui sont `as` parfois utilisés dans les arguments sont le modèle, et les modèles d’identification associés à des syndicats discriminés et des modèles actifs.</span><span class="sxs-lookup"><span data-stu-id="210cd-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="210cd-128">Vous pouvez utiliser le modèle syndical à cas unique et discriminé comme suit.</span><span class="sxs-lookup"><span data-stu-id="210cd-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="210cd-129">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="210cd-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="210cd-130">Les modèles actifs peuvent être utiles comme paramètres, par exemple, lors de la transformation d’un argument en un format souhaité, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="210cd-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="210cd-131">Vous pouvez `as` utiliser le modèle pour stocker une valeur appariée comme valeur locale, comme le montre la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="210cd-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="210cd-132">Un autre modèle qui est utilisé de temps en temps est une fonction qui laisse le dernier argument sans nom en fournissant, comme le corps de la fonction, une expression lambda qui effectue immédiatement une correspondance de modèle sur l’argument implicite.</span><span class="sxs-lookup"><span data-stu-id="210cd-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="210cd-133">Un exemple de ceci est la ligne suivante de code.</span><span class="sxs-lookup"><span data-stu-id="210cd-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="210cd-134">Ce code définit une fonction qui prend `true` une liste générique `false` et renvoie si la liste est vide, et autrement.</span><span class="sxs-lookup"><span data-stu-id="210cd-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="210cd-135">L’utilisation de telles techniques peut rendre le code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="210cd-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="210cd-136">De temps en temps, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes de votre programme n’ont que trois éléments, vous pouvez utiliser un modèle comme ce qui suit dans une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="210cd-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="210cd-137">L’utilisation de modèles qui ont des correspondances incomplètes est mieux réservée au prototypage rapide et à d’autres utilisations temporaires.</span><span class="sxs-lookup"><span data-stu-id="210cd-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="210cd-138">Le compilateur émettra un avertissement pour un tel code.</span><span class="sxs-lookup"><span data-stu-id="210cd-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="210cd-139">Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et ne conviennent donc pas aux API composant.</span><span class="sxs-lookup"><span data-stu-id="210cd-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="210cd-140">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="210cd-140">Named Arguments</span></span>

<span data-ttu-id="210cd-141">Les arguments en faveur de méthodes peuvent être spécifiés par position dans une liste d’arguments séparées par virgule, ou ils peuvent être transmis à une méthode explicitement en fournissant le nom, suivi d’un signe égal et de la valeur à transmettre.</span><span class="sxs-lookup"><span data-stu-id="210cd-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="210cd-142">S’ils sont spécifiés en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="210cd-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="210cd-143">Les arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications de l’API, comme une réorganisation des paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="210cd-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="210cd-144">Les arguments nommés ne sont `let`autorisés que pour les méthodes, pas pour les fonctions liées, les valeurs de fonction, ou les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="210cd-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="210cd-145">L’exemple de code suivant montre l’utilisation d’arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="210cd-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="210cd-146">Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe en utilisant une syntaxe similaire à celle des arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="210cd-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="210cd-147">L’exemple suivant montre cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="210cd-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="210cd-148">Pour plus d’informations, voir [Constructors (F)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span><span class="sxs-lookup"><span data-stu-id="210cd-148">For more information, see [Constructors (F#)](https://msdn.microsoft.com/library/2cd0ed07-d214-4125-8317-4f288af99f05).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="210cd-149">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="210cd-149">Optional Parameters</span></span>

<span data-ttu-id="210cd-150">Vous pouvez spécifier un paramètre facultatif pour une méthode en utilisant un point d’interrogation devant le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="210cd-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="210cd-151">Les paramètres facultatifs sont interprétés comme le type d’option F, de sorte que `match` vous `Some` pouvez `None`les interroger de la manière régulière que les types d’options sont interrogés, en utilisant une expression avec et .</span><span class="sxs-lookup"><span data-stu-id="210cd-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="210cd-152">Les paramètres facultatifs ne sont autorisés que `let` sur les membres, et non sur les fonctions créées par l’utilisation de fixations.</span><span class="sxs-lookup"><span data-stu-id="210cd-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="210cd-153">Vous pouvez transmettre les valeurs facultatives `?arg=None` existantes à la méthode par nom de paramètre, comme ou `?arg=Some(3)` `?arg=arg`.</span><span class="sxs-lookup"><span data-stu-id="210cd-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="210cd-154">Cela peut être utile lors de la construction d’une méthode qui passe arguments optionnels à une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="210cd-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="210cd-155">Vous pouvez également `defaultArg`utiliser une fonction , qui définit une valeur par défaut d’un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="210cd-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="210cd-156">La `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut comme le second.</span><span class="sxs-lookup"><span data-stu-id="210cd-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="210cd-157">L’exemple suivant illustre l’utilisation de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="210cd-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="210cd-158">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="210cd-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="210cd-159">Aux fins de l’interop de base visuelle `[<Optional; DefaultParameterValue<(...)>]` et de C, vous pouvez utiliser les attributs dans le F, de sorte que les appelants verront un argument comme facultatif.</span><span class="sxs-lookup"><span data-stu-id="210cd-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="210cd-160">Cela équivaut à définir l’argument comme `MyMethod(int i = 3)`facultatif dans C ' comme dans .</span><span class="sxs-lookup"><span data-stu-id="210cd-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="210cd-161">Vous pouvez également spécifier un nouvel objet comme valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="210cd-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="210cd-162">Par exemple, `Foo` le membre `CancellationToken` pourrait avoir une option comme entrée à la place :</span><span class="sxs-lookup"><span data-stu-id="210cd-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="210cd-163">La valeur donnée `DefaultParameterValue` comme argument doit correspondre au type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="210cd-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="210cd-164">Par exemple, ce qui suit n’est pas autorisé :</span><span class="sxs-lookup"><span data-stu-id="210cd-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="210cd-165">Dans ce cas, le compilateur génère un avertissement et ignorera les deux attributs tout à fait.</span><span class="sxs-lookup"><span data-stu-id="210cd-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="210cd-166">Notez que `null` la valeur par défaut doit être annotée de type, comme sinon le `[<Optional; DefaultParameterValue(null:obj)>] o:obj`compilateur déduit le mauvais type, c’est-à-dire .</span><span class="sxs-lookup"><span data-stu-id="210cd-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="210cd-167">Passer par référence</span><span class="sxs-lookup"><span data-stu-id="210cd-167">Passing by Reference</span></span>

<span data-ttu-id="210cd-168">Passer une valeur F par référence implique [byrefs](byrefs.md), qui sont gérés types de pointeurs.</span><span class="sxs-lookup"><span data-stu-id="210cd-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="210cd-169">Les conseils pour le type à utiliser sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="210cd-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="210cd-170">Utilisez `inref<'T>` si vous avez seulement besoin de lire le pointeur.</span><span class="sxs-lookup"><span data-stu-id="210cd-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="210cd-171">Utilisez `outref<'T>` si vous avez seulement besoin d’écrire sur le pointeur.</span><span class="sxs-lookup"><span data-stu-id="210cd-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="210cd-172">Utilisez `byref<'T>` si vous avez besoin à la fois lire et écrire sur le pointeur.</span><span class="sxs-lookup"><span data-stu-id="210cd-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

```fsharp
let example1 (x: inref<int>) = printfn "It's %d" x

let example2 (x: outref<int>) = x <- x + 1

let example3 (x: byref<int>) =
    printfn "It'd %d" x
    x <- x + 1

let test () =
    // No need to make it mutable, since it's read-only
    let x = 1
    example1 &x

    // Needs to be mutable, since we write to it
    let mutable y = 2
    example2 &y
    example3 &y // Now 'y' is 3
```

<span data-ttu-id="210cd-173">Étant donné que le paramètre est un pointeur et que la valeur est mutable, toute modification de la valeur est conservée après l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="210cd-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="210cd-174">Vous pouvez utiliser un tuple comme `out` valeur de retour pour stocker tous les paramètres dans les méthodes de bibliothèque .NET.</span><span class="sxs-lookup"><span data-stu-id="210cd-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="210cd-175">Alternativement, vous pouvez `out` traiter `byref` le paramètre comme un paramètre.</span><span class="sxs-lookup"><span data-stu-id="210cd-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="210cd-176">L’exemple de code suivant illustre les deux façons.</span><span class="sxs-lookup"><span data-stu-id="210cd-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="210cd-177">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="210cd-177">Parameter Arrays</span></span>

<span data-ttu-id="210cd-178">Il est parfois nécessaire de définir une fonction qui prend un nombre arbitraire de paramètres de type hétérogène.</span><span class="sxs-lookup"><span data-stu-id="210cd-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="210cd-179">Il ne serait pas pratique de créer toutes les méthodes surchargées possibles pour tenir compte de tous les types qui pourraient être utilisés.</span><span class="sxs-lookup"><span data-stu-id="210cd-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="210cd-180">Les implémentations .NET fournissent un soutien à ces méthodes grâce à la fonction de tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="210cd-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="210cd-181">Une méthode qui prend un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="210cd-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="210cd-182">Les paramètres sont mis dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="210cd-182">The parameters are put into an array.</span></span> <span data-ttu-id="210cd-183">Le type d’éléments de tableau détermine les types de paramètres qui peuvent être transmis à la fonction.</span><span class="sxs-lookup"><span data-stu-id="210cd-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="210cd-184">Si vous définissez `System.Object` le tableau de paramètres comme type d’élément, le code client peut passer des valeurs de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="210cd-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="210cd-185">Dans les tableaux de paramètres, les paramètres ne peuvent être définis que dans les méthodes.</span><span class="sxs-lookup"><span data-stu-id="210cd-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="210cd-186">Ils ne peuvent pas être utilisés dans des fonctions ou des fonctions autonomes qui sont définies dans des modules.</span><span class="sxs-lookup"><span data-stu-id="210cd-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="210cd-187">Vous définissez un tableau `ParamArray` de paramètres en utilisant l’attribut.</span><span class="sxs-lookup"><span data-stu-id="210cd-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="210cd-188">L’attribut `ParamArray` ne peut être appliqué qu’au dernier paramètre.</span><span class="sxs-lookup"><span data-stu-id="210cd-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="210cd-189">Le code suivant illustre à la fois l’appel d’une méthode .NET qui prend un tableau de paramètres et la définition d’un type dans F 'qui a une méthode qui prend un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="210cd-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="210cd-190">Lorsqu’il est exécuté dans un projet, la sortie du code précédent est la suivante :</span><span class="sxs-lookup"><span data-stu-id="210cd-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="210cd-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="210cd-191">See also</span></span>

- [<span data-ttu-id="210cd-192">Membres</span><span class="sxs-lookup"><span data-stu-id="210cd-192">Members</span></span>](./members/index.md)

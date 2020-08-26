---
title: Paramètres et arguments
description: 'En savoir plus sur la prise en charge du langage F # pour définir des paramètres et passer des arguments à des fonctions, des méthodes et des propriétés.'
ms.date: 08/15/2020
ms.openlocfilehash: 6564fd31105427683af8fc6280672e638737e9b5
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811520"
---
# <a name="parameters-and-arguments"></a><span data-ttu-id="5d925-103">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="5d925-103">Parameters and Arguments</span></span>

<span data-ttu-id="5d925-104">Cette rubrique décrit la prise en charge linguistique pour définir des paramètres et passer des arguments à des fonctions, des méthodes et des propriétés.</span><span class="sxs-lookup"><span data-stu-id="5d925-104">This topic describes language support for defining parameters and passing arguments to functions, methods, and properties.</span></span> <span data-ttu-id="5d925-105">Elle contient des informations sur la façon de passer par référence, ainsi que sur la façon de définir et d’utiliser des méthodes qui peuvent prendre un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5d925-105">It includes information about how to pass by reference, and how to define and use methods that can take a variable number of arguments.</span></span>

## <a name="parameters-and-arguments"></a><span data-ttu-id="5d925-106">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="5d925-106">Parameters and Arguments</span></span>

<span data-ttu-id="5d925-107">Le terme *paramètre* est utilisé pour décrire les noms des valeurs qui sont supposées être fournies.</span><span class="sxs-lookup"><span data-stu-id="5d925-107">The term *parameter* is used to describe the names for values that are expected to be supplied.</span></span> <span data-ttu-id="5d925-108">Le terme *argument* est utilisé pour les valeurs fournies pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="5d925-108">The term *argument* is used for the values provided for each parameter.</span></span>

<span data-ttu-id="5d925-109">Les paramètres peuvent être spécifiés sous forme de tuple ou de formulaire curryfiée, ou dans une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="5d925-109">Parameters can be specified in tuple or curried form, or in some combination of the two.</span></span> <span data-ttu-id="5d925-110">Vous pouvez passer des arguments à l’aide d’un nom de paramètre explicite.</span><span class="sxs-lookup"><span data-stu-id="5d925-110">You can pass arguments by using an explicit parameter name.</span></span> <span data-ttu-id="5d925-111">Les paramètres des méthodes peuvent être spécifiés comme facultatifs et donner une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="5d925-111">Parameters of methods can be specified as optional and given a default value.</span></span>

## <a name="parameter-patterns"></a><span data-ttu-id="5d925-112">Modèles de paramètres</span><span class="sxs-lookup"><span data-stu-id="5d925-112">Parameter Patterns</span></span>

<span data-ttu-id="5d925-113">Les paramètres fournis aux fonctions et aux méthodes sont, en général, des modèles séparés par des espaces.</span><span class="sxs-lookup"><span data-stu-id="5d925-113">Parameters supplied to functions and methods are, in general, patterns separated by spaces.</span></span> <span data-ttu-id="5d925-114">Cela signifie que, en principe, l’un des modèles décrits dans [expressions de correspondance](match-expressions.md) peut être utilisé dans une liste de paramètres pour une fonction ou un membre.</span><span class="sxs-lookup"><span data-stu-id="5d925-114">This means that, in principle, any of the patterns described in [Match Expressions](match-expressions.md) can be used in a parameter list for a function or member.</span></span>

<span data-ttu-id="5d925-115">Les méthodes utilisent généralement la forme de tuple de passage des arguments.</span><span class="sxs-lookup"><span data-stu-id="5d925-115">Methods usually use the tuple form of passing arguments.</span></span> <span data-ttu-id="5d925-116">Cela permet d’obtenir un résultat plus clair du point de vue d’autres langages .NET, car la forme de tuple correspond à la façon dont les arguments sont passés dans les méthodes .NET.</span><span class="sxs-lookup"><span data-stu-id="5d925-116">This achieves a clearer result from the perspective of other .NET languages because the tuple form matches the way arguments are passed in .NET methods.</span></span>

<span data-ttu-id="5d925-117">La forme curryfiée est le plus souvent utilisée avec les fonctions créées à l’aide de `let` liaisons.</span><span class="sxs-lookup"><span data-stu-id="5d925-117">The curried form is most often used with functions created by using `let` bindings.</span></span>

<span data-ttu-id="5d925-118">Le pseudo-code suivant montre des exemples de tuple et d’arguments curryfiés.</span><span class="sxs-lookup"><span data-stu-id="5d925-118">The following pseudocode shows examples of tuple and curried arguments.</span></span>

```fsharp
// Tuple form.
member this.SomeMethod(param1, param2) = ...
// Curried form.
let function1 param1 param2 = ...
```

<span data-ttu-id="5d925-119">Les formulaires combinés sont possibles lorsque certains arguments se trouvent dans des tuples et d’autres non.</span><span class="sxs-lookup"><span data-stu-id="5d925-119">Combined forms are possible when some arguments are in tuples and some are not.</span></span>

```fsharp
let function2 param1 (param2a, param2b) param3 = ...
```

<span data-ttu-id="5d925-120">D’autres modèles peuvent également être utilisés dans les listes de paramètres, mais si le modèle de paramètre ne correspond pas à toutes les entrées possibles, il peut y avoir une correspondance incomplète au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="5d925-120">Other patterns can also be used in parameter lists, but if the parameter pattern does not match all possible inputs, there might be an incomplete match at run time.</span></span> <span data-ttu-id="5d925-121">L’exception `MatchFailureException` est générée lorsque la valeur d’un argument ne correspond pas aux critères spécifiés dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d925-121">The exception `MatchFailureException` is generated when the value of an argument does not match the patterns specified in the parameter list.</span></span> <span data-ttu-id="5d925-122">Le compilateur émet un avertissement lorsqu’un modèle de paramètre autorise des correspondances incomplètes.</span><span class="sxs-lookup"><span data-stu-id="5d925-122">The compiler issues a warning when a parameter pattern allows for incomplete matches.</span></span> <span data-ttu-id="5d925-123">Au moins un autre modèle est souvent utile pour les listes de paramètres et c’est le modèle de caractère générique.</span><span class="sxs-lookup"><span data-stu-id="5d925-123">At least one other pattern is commonly useful for parameter lists, and that is the wildcard pattern.</span></span> <span data-ttu-id="5d925-124">Vous utilisez le modèle de caractère générique dans une liste de paramètres lorsque vous souhaitez simplement ignorer tous les arguments fournis.</span><span class="sxs-lookup"><span data-stu-id="5d925-124">You use the wildcard pattern in a parameter list when you simply want to ignore any arguments that are supplied.</span></span> <span data-ttu-id="5d925-125">Le code suivant illustre l’utilisation du modèle de caractère générique dans une liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="5d925-125">The following code illustrates the use of the wildcard pattern in an argument list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3801.fs)]

<span data-ttu-id="5d925-126">Le modèle de caractère générique peut être utile lorsque vous n’avez pas besoin des arguments passés, comme dans le point d’entrée principal d’un programme, lorsque vous n’êtes pas intéressé par les arguments de ligne de commande qui sont normalement fournis en tant que tableau de chaînes, comme dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="5d925-126">The wildcard pattern can be useful whenever you do not need the arguments passed in, such as in the main entry point to a program, when you are not interested in the command-line arguments that are normally supplied as a string array, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3802.fs)]

<span data-ttu-id="5d925-127">Les autres modèles qui sont parfois utilisés dans les arguments sont le `as` modèle et les modèles d’identificateur associés aux unions discriminées et aux modèles actifs.</span><span class="sxs-lookup"><span data-stu-id="5d925-127">Other patterns that are sometimes used in arguments are the `as` pattern, and identifier patterns associated with discriminated unions and active patterns.</span></span> <span data-ttu-id="5d925-128">Vous pouvez utiliser le modèle d’union discriminée à cas unique comme suit.</span><span class="sxs-lookup"><span data-stu-id="5d925-128">You can use the single-case discriminated union pattern as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3803.fs)]

<span data-ttu-id="5d925-129">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="5d925-129">The output is as follows.</span></span>

```console
Data begins at 0 and ends at 4 in string Et tu, Brute?
Et tu
```

<span data-ttu-id="5d925-130">Les modèles actifs peuvent être utiles comme paramètres, par exemple lors de la transformation d’un argument dans un format souhaité, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="5d925-130">Active patterns can be useful as parameters, for example, when transforming an argument into a desired format, as in the following example:</span></span>

```fsharp
type Point = { x : float; y : float }

let (| Polar |) { x = x; y = y} =
    ( sqrt (x*x + y*y), System.Math.Atan (y/ x) )

let radius (Polar(r, _)) = r
let angle (Polar(_, theta)) = theta
```

<span data-ttu-id="5d925-131">Vous pouvez utiliser le `as` modèle pour stocker une valeur correspondante comme valeur locale, comme indiqué dans la ligne de code suivante.</span><span class="sxs-lookup"><span data-stu-id="5d925-131">You can use the `as` pattern to store a matched value as a local value, as is shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3805.fs)]

<span data-ttu-id="5d925-132">Un autre modèle qui est utilisé occasionnellement est une fonction qui laisse le dernier argument sans nom en fournissant, en tant que corps de la fonction, une expression lambda qui effectue immédiatement une correspondance de modèle sur l’argument implicite.</span><span class="sxs-lookup"><span data-stu-id="5d925-132">Another pattern that is used occasionally is a function that leaves the last argument unnamed by providing, as the body of the function, a lambda expression that immediately performs a pattern match on the implicit argument.</span></span> <span data-ttu-id="5d925-133">La ligne de code suivante en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="5d925-133">An example of this is the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3804.fs)]

<span data-ttu-id="5d925-134">Ce code définit une fonction qui prend une liste générique et retourne `true` si la liste est vide, et dans le `false` cas contraire.</span><span class="sxs-lookup"><span data-stu-id="5d925-134">This code defines a function that takes a generic list and returns `true` if the list is empty, and `false` otherwise.</span></span> <span data-ttu-id="5d925-135">L’utilisation de ces techniques peut rendre le code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="5d925-135">The use of such techniques can make code more difficult to read.</span></span>

<span data-ttu-id="5d925-136">Parfois, les modèles qui impliquent des correspondances incomplètes sont utiles, par exemple, si vous savez que les listes de votre programme ne comportent que trois éléments, vous pouvez utiliser un modèle comme celui qui suit dans une liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d925-136">Occasionally, patterns that involve incomplete matches are useful, for example, if you know that the lists in your program have only three elements, you might use a pattern like the following in a parameter list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3806.fs)]

<span data-ttu-id="5d925-137">L’utilisation de modèles qui ont des correspondances incomplètes est réservée au prototypage rapide et à d’autres utilisations temporaires.</span><span class="sxs-lookup"><span data-stu-id="5d925-137">The use of patterns that have incomplete matches is best reserved for quick prototyping and other temporary uses.</span></span> <span data-ttu-id="5d925-138">Le compilateur émettra un avertissement pour ce type de code.</span><span class="sxs-lookup"><span data-stu-id="5d925-138">The compiler will issue a warning for such code.</span></span> <span data-ttu-id="5d925-139">Ces modèles ne peuvent pas couvrir le cas général de toutes les entrées possibles et ne conviennent donc pas aux API de composant.</span><span class="sxs-lookup"><span data-stu-id="5d925-139">Such patterns cannot cover the general case of all possible inputs and therefore are not suitable for component APIs.</span></span>

## <a name="named-arguments"></a><span data-ttu-id="5d925-140">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="5d925-140">Named Arguments</span></span>

<span data-ttu-id="5d925-141">Les arguments des méthodes peuvent être spécifiés par position dans une liste d’arguments séparée par des virgules, ou ils peuvent être passés explicitement à une méthode en fournissant le nom, suivi d’un signe égal et de la valeur à passer.</span><span class="sxs-lookup"><span data-stu-id="5d925-141">Arguments for methods can be specified by position in a comma-separated argument list, or they can be passed to a method explicitly by providing the name, followed by an equal sign and the value to be passed in.</span></span> <span data-ttu-id="5d925-142">S’ils sont spécifiés en fournissant le nom, ils peuvent apparaître dans un ordre différent de celui utilisé dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="5d925-142">If specified by providing the name, they can appear in a different order from that used in the declaration.</span></span>

<span data-ttu-id="5d925-143">Les arguments nommés peuvent rendre le code plus lisible et plus adaptable à certains types de modifications dans l’API, tels que la réorganisation des paramètres de méthode.</span><span class="sxs-lookup"><span data-stu-id="5d925-143">Named arguments can make code more readable and more adaptable to certain types of changes in the API, such as a reordering of method parameters.</span></span>

<span data-ttu-id="5d925-144">Les arguments nommés sont autorisés uniquement pour les méthodes, pas pour les `let` fonctions liées aux fonctions, les valeurs de fonctions ou les expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="5d925-144">Named arguments are allowed only for methods, not for `let`-bound functions, function values, or lambda expressions.</span></span>

<span data-ttu-id="5d925-145">L’exemple de code suivant illustre l’utilisation d’arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="5d925-145">The following code example demonstrates the use of named arguments.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3807.fs)]

<span data-ttu-id="5d925-146">Dans un appel à un constructeur de classe, vous pouvez définir les valeurs des propriétés de la classe à l’aide d’une syntaxe similaire à celle des arguments nommés.</span><span class="sxs-lookup"><span data-stu-id="5d925-146">In a call to a class constructor, you can set the values of properties of the class by using a syntax similar to that of named arguments.</span></span> <span data-ttu-id="5d925-147">L’exemple suivant illustre cette syntaxe.</span><span class="sxs-lookup"><span data-stu-id="5d925-147">The following example shows this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="5d925-148">Pour plus d’informations, consultez [constructeurs (F #)](members/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="5d925-148">For more information, see [Constructors (F#)](members/constructors.md).</span></span>

## <a name="optional-parameters"></a><span data-ttu-id="5d925-149">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="5d925-149">Optional Parameters</span></span>

<span data-ttu-id="5d925-150">Vous pouvez spécifier un paramètre facultatif pour une méthode à l’aide d’un point d’interrogation devant le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5d925-150">You can specify an optional parameter for a method by using a question mark in front of the parameter name.</span></span> <span data-ttu-id="5d925-151">Les paramètres facultatifs sont interprétés comme le type d’option F #, ce qui vous permet de les interroger de manière régulière que les types d’options sont interrogés, en utilisant une `match` expression avec `Some` et `None` .</span><span class="sxs-lookup"><span data-stu-id="5d925-151">Optional parameters are interpreted as the F# option type, so you can query them in the regular way that option types are queried, by using a `match` expression with `Some` and `None`.</span></span> <span data-ttu-id="5d925-152">Les paramètres facultatifs sont autorisés uniquement sur les membres, et non sur les fonctions créées à l’aide de `let` liaisons.</span><span class="sxs-lookup"><span data-stu-id="5d925-152">Optional parameters are permitted only on members, not on functions created by using `let` bindings.</span></span>

<span data-ttu-id="5d925-153">Vous pouvez passer des valeurs facultatives existantes à la méthode par nom de paramètre, tel que `?arg=None` ou `?arg=Some(3)` `?arg=arg` .</span><span class="sxs-lookup"><span data-stu-id="5d925-153">You can pass existing optional values to method by parameter name, such as `?arg=None` or `?arg=Some(3)` or `?arg=arg`.</span></span> <span data-ttu-id="5d925-154">Cela peut être utile lors de la génération d’une méthode qui transmet des arguments facultatifs à une autre méthode.</span><span class="sxs-lookup"><span data-stu-id="5d925-154">This can be useful when building a method that passes optional arguments to another method.</span></span>

<span data-ttu-id="5d925-155">Vous pouvez également utiliser une fonction `defaultArg` , qui définit une valeur par défaut d’un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="5d925-155">You can also use a function `defaultArg`, which sets a default value of an optional argument.</span></span> <span data-ttu-id="5d925-156">La `defaultArg` fonction prend le paramètre facultatif comme premier argument et la valeur par défaut comme second.</span><span class="sxs-lookup"><span data-stu-id="5d925-156">The `defaultArg` function takes the optional parameter as the first argument and the default value as the second.</span></span>

<span data-ttu-id="5d925-157">L’exemple suivant illustre l’utilisation de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="5d925-157">The following example illustrates the use of optional parameters.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3808.fs)]

<span data-ttu-id="5d925-158">La sortie est la suivante.</span><span class="sxs-lookup"><span data-stu-id="5d925-158">The output is as follows.</span></span>

```console
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
Baud Rate: 300 Duplex: Half Parity: true
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 9600 Duplex: Full Parity: false
Baud Rate: 4800 Duplex: Half Parity: false
```

<span data-ttu-id="5d925-159">Dans le cadre de C# et de Visual Basic Interop, vous pouvez utiliser les attributs `[<Optional; DefaultParameterValue<(...)>]` en F # pour que les appelants voient un argument comme facultatif.</span><span class="sxs-lookup"><span data-stu-id="5d925-159">For the purposes of C# and Visual Basic interop you can use the attributes `[<Optional; DefaultParameterValue<(...)>]` in F#, so that callers will see an argument as optional.</span></span> <span data-ttu-id="5d925-160">Cela équivaut à définir l’argument comme facultatif dans C#, comme dans `MyMethod(int i = 3)` .</span><span class="sxs-lookup"><span data-stu-id="5d925-160">This is equivalent to defining the argument as optional in C# as in `MyMethod(int i = 3)`.</span></span>

```fsharp
open System
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue("Hello world")>] message) =
        printfn "%s" message
```

<span data-ttu-id="5d925-161">Vous pouvez également spécifier un nouvel objet en tant que valeur de paramètre par défaut.</span><span class="sxs-lookup"><span data-stu-id="5d925-161">You can also specify a new object as a default parameter value.</span></span> <span data-ttu-id="5d925-162">Par exemple, le `Foo` membre peut avoir un facultatif `CancellationToken` comme entrée à la place :</span><span class="sxs-lookup"><span data-stu-id="5d925-162">For example, the `Foo` member could have an optional `CancellationToken` as input instead:</span></span>

```fsharp
open System.Threading
open System.Runtime.InteropServices
type C =
    static member Foo([<Optional; DefaultParameterValue(CancellationToken())>] ct: CancellationToken) =
        printfn "%A" ct
```

<span data-ttu-id="5d925-163">La valeur donnée comme argument de `DefaultParameterValue` doit correspondre au type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5d925-163">The value given as argument to `DefaultParameterValue` must match the type of the parameter.</span></span> <span data-ttu-id="5d925-164">Par exemple, ce qui suit n’est pas autorisé :</span><span class="sxs-lookup"><span data-stu-id="5d925-164">For example, the following is not allowed:</span></span>

```fsharp
type C =
    static member Wrong([<Optional; DefaultParameterValue("string")>] i:int) = ()
```

<span data-ttu-id="5d925-165">Dans ce cas, le compilateur génère un avertissement et ignore les deux attributs.</span><span class="sxs-lookup"><span data-stu-id="5d925-165">In this case, the compiler generates a warning and will ignore both attributes altogether.</span></span> <span data-ttu-id="5d925-166">Notez que la valeur par défaut `null` doit être annotée de type, dans le cas contraire, le compilateur déduit le type incorrect, c.-à-d. `[<Optional; DefaultParameterValue(null:obj)>] o:obj` .</span><span class="sxs-lookup"><span data-stu-id="5d925-166">Note that the default value `null` needs to be type-annotated, as otherwise the compiler infers the wrong type, i.e. `[<Optional; DefaultParameterValue(null:obj)>] o:obj`.</span></span>

## <a name="passing-by-reference"></a><span data-ttu-id="5d925-167">Passer par référence</span><span class="sxs-lookup"><span data-stu-id="5d925-167">Passing by Reference</span></span>

<span data-ttu-id="5d925-168">La transmission d’une valeur F # par référence implique [types ByRef](byrefs.md), qui sont des types pointeur managés.</span><span class="sxs-lookup"><span data-stu-id="5d925-168">Passing an F# value by reference involves [byrefs](byrefs.md), which are managed pointer types.</span></span> <span data-ttu-id="5d925-169">Les instructions pour le type à utiliser sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d925-169">Guidance for which type to use is as follows:</span></span>

- <span data-ttu-id="5d925-170">Utilisez `inref<'T>` si vous devez uniquement lire le pointeur.</span><span class="sxs-lookup"><span data-stu-id="5d925-170">Use `inref<'T>` if you only need to read the pointer.</span></span>
- <span data-ttu-id="5d925-171">Utilisez `outref<'T>` si vous devez uniquement écrire dans le pointeur.</span><span class="sxs-lookup"><span data-stu-id="5d925-171">Use `outref<'T>` if you only need to write to the pointer.</span></span>
- <span data-ttu-id="5d925-172">Utilisez `byref<'T>` si vous avez besoin de lire et d’écrire dans le pointeur.</span><span class="sxs-lookup"><span data-stu-id="5d925-172">Use `byref<'T>` if you need to both read from and write to the pointer.</span></span>

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

<span data-ttu-id="5d925-173">Étant donné que le paramètre est un pointeur et que la valeur est mutable, toute modification apportée à la valeur est conservée après l’exécution de la fonction.</span><span class="sxs-lookup"><span data-stu-id="5d925-173">Because the parameter is a pointer and the value is mutable, any changes to the value are retained after the execution of the function.</span></span>

<span data-ttu-id="5d925-174">Vous pouvez utiliser un tuple comme valeur de retour pour stocker des `out` paramètres dans les méthodes de la bibliothèque .net.</span><span class="sxs-lookup"><span data-stu-id="5d925-174">You can use a tuple as a return value to store any `out` parameters in .NET library methods.</span></span> <span data-ttu-id="5d925-175">Vous pouvez également traiter le `out` paramètre en tant que `byref` paramètre.</span><span class="sxs-lookup"><span data-stu-id="5d925-175">Alternatively, you can treat the `out` parameter as a `byref` parameter.</span></span> <span data-ttu-id="5d925-176">L’exemple de code suivant illustre les deux méthodes.</span><span class="sxs-lookup"><span data-stu-id="5d925-176">The following code example illustrates both ways.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-1/snippet3810.fs)]

## <a name="parameter-arrays"></a><span data-ttu-id="5d925-177">Tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="5d925-177">Parameter Arrays</span></span>

<span data-ttu-id="5d925-178">Il est parfois nécessaire de définir une fonction qui accepte un nombre arbitraire de paramètres de type hétérogène.</span><span class="sxs-lookup"><span data-stu-id="5d925-178">Occasionally it is necessary to define a function that takes an arbitrary number of parameters of heterogeneous type.</span></span> <span data-ttu-id="5d925-179">Il n’est pas pratique de créer toutes les méthodes surchargées possibles pour tenir compte de tous les types qui pourraient être utilisés.</span><span class="sxs-lookup"><span data-stu-id="5d925-179">It would not be practical to create all the possible overloaded methods to account for all the types that could be used.</span></span> <span data-ttu-id="5d925-180">Les implémentations .NET prennent en charge ces méthodes par le biais de la fonctionnalité de tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d925-180">The .NET implementations provide support for such methods through the parameter array feature.</span></span> <span data-ttu-id="5d925-181">Une méthode qui accepte un tableau de paramètres dans sa signature peut être fournie avec un nombre arbitraire de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d925-181">A method that takes a parameter array in its signature can be provided with an arbitrary number of parameters.</span></span> <span data-ttu-id="5d925-182">Les paramètres sont placés dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="5d925-182">The parameters are put into an array.</span></span> <span data-ttu-id="5d925-183">Le type des éléments du tableau détermine les types de paramètres qui peuvent être passés à la fonction.</span><span class="sxs-lookup"><span data-stu-id="5d925-183">The type of the array elements determines the parameter types that can be passed to the function.</span></span> <span data-ttu-id="5d925-184">Si vous définissez le tableau de paramètres avec `System.Object` comme type d’élément, le code client peut passer des valeurs de n’importe quel type.</span><span class="sxs-lookup"><span data-stu-id="5d925-184">If you define the parameter array with `System.Object` as the element type, then client code can pass values of any type.</span></span>

<span data-ttu-id="5d925-185">En F #, les tableaux de paramètres ne peuvent être définis que dans des méthodes.</span><span class="sxs-lookup"><span data-stu-id="5d925-185">In F#, parameter arrays can only be defined in methods.</span></span> <span data-ttu-id="5d925-186">Elles ne peuvent pas être utilisées dans des fonctions autonomes ou des fonctions définies dans des modules.</span><span class="sxs-lookup"><span data-stu-id="5d925-186">They cannot be used in standalone functions or functions that are defined in modules.</span></span>

<span data-ttu-id="5d925-187">Vous définissez un tableau de paramètres à l’aide de l' `ParamArray` attribut.</span><span class="sxs-lookup"><span data-stu-id="5d925-187">You define a parameter array by using the `ParamArray` attribute.</span></span> <span data-ttu-id="5d925-188">L' `ParamArray` attribut ne peut être appliqué qu’au dernier paramètre.</span><span class="sxs-lookup"><span data-stu-id="5d925-188">The `ParamArray` attribute can only be applied to the last parameter.</span></span>

<span data-ttu-id="5d925-189">Le code suivant illustre l’appel d’une méthode .NET qui accepte un tableau de paramètres et la définition d’un type en F # qui a une méthode qui prend un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5d925-189">The following code illustrates both calling a .NET method that takes a parameter array and the definition of a type in F# that has a method that takes a parameter array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/parameters-and-arguments-2/snippet3811.fs)]

<span data-ttu-id="5d925-190">Lorsqu’il est exécuté dans un projet, la sortie du code précédent se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="5d925-190">When run in a project, the output of the previous code is as follows:</span></span>

```console
a 1 10 Hello world 1 True
"a"
1
10.0
"Hello world"
1u
true
```

## <a name="see-also"></a><span data-ttu-id="5d925-191">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5d925-191">See also</span></span>

- <span data-ttu-id="5d925-192">[Members](./members/index.md) (Membres)</span><span class="sxs-lookup"><span data-stu-id="5d925-192">[Members](./members/index.md)</span></span>

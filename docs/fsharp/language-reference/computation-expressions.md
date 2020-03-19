---
title: Expressions de calcul
description: Apprenez à créer une syntaxe pratique pour l’écriture de calculs en F qui peuvent être séquencés et combinés à l’aide de constructions de flux de contrôle et de liaisons.
ms.date: 11/04/2019
ms.openlocfilehash: 55406cc12d9e6e890fe69d712f79486d23b84452
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400231"
---
# <a name="computation-expressions"></a><span data-ttu-id="73456-103">Expressions de calcul</span><span class="sxs-lookup"><span data-stu-id="73456-103">Computation Expressions</span></span>

<span data-ttu-id="73456-104">Les expressions de calcul dans le Fmd fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de constructions et de liaisons de flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="73456-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="73456-105">Selon le type d’expression de calcul, ils peuvent être considérés comme un moyen d’exprimer des monads, des monoids, des transformateurs monad et des functors applicatifs.</span><span class="sxs-lookup"><span data-stu-id="73456-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="73456-106">Cependant, contrairement à d’autres langues (comme la notation de *haskell),* elles ne sont pas liées à une seule abstraction, et ne s’appuient pas sur des macros ou d’autres formes de métaprogrammation pour accomplir une syntaxe pratique et sensible au contexte.</span><span class="sxs-lookup"><span data-stu-id="73456-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="73456-107">Vue d’ensemble</span><span class="sxs-lookup"><span data-stu-id="73456-107">Overview</span></span>

<span data-ttu-id="73456-108">Les calculs peuvent prendre de nombreuses formes.</span><span class="sxs-lookup"><span data-stu-id="73456-108">Computations can take many forms.</span></span> <span data-ttu-id="73456-109">La forme de calcul la plus courante est l’exécution à threads simples, qui est facile à comprendre et à modifier.</span><span class="sxs-lookup"><span data-stu-id="73456-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="73456-110">Cependant, toutes les formes de calcul ne sont pas aussi simples que l’exécution à threads simples.</span><span class="sxs-lookup"><span data-stu-id="73456-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="73456-111">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="73456-111">Some examples include:</span></span>

- <span data-ttu-id="73456-112">Calculs non déterministes</span><span class="sxs-lookup"><span data-stu-id="73456-112">Non-deterministic computations</span></span>
- <span data-ttu-id="73456-113">Calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="73456-113">Asynchronous computations</span></span>
- <span data-ttu-id="73456-114">Calculs effectieux</span><span class="sxs-lookup"><span data-stu-id="73456-114">Effectful computations</span></span>
- <span data-ttu-id="73456-115">Calculs génératifs</span><span class="sxs-lookup"><span data-stu-id="73456-115">Generative computations</span></span>

<span data-ttu-id="73456-116">Plus généralement, il existe des calculs *contextuelles* que vous devez effectuer dans certaines parties d’une application.</span><span class="sxs-lookup"><span data-stu-id="73456-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="73456-117">Écrire un code sensible au contexte peut être difficile, car il est facile de "fuite" de calculs en dehors d’un contexte donné sans abstractions pour vous empêcher de le faire.</span><span class="sxs-lookup"><span data-stu-id="73456-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="73456-118">Ces abstractions sont souvent difficiles à écrire par vous-même, c’est pourquoi F a une façon généralisée de le faire appelé **expressions de calcul**.</span><span class="sxs-lookup"><span data-stu-id="73456-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="73456-119">Les expressions de calcul offrent un modèle uniforme de syntaxe et d’abstraction pour coder les calculs contextuelles.</span><span class="sxs-lookup"><span data-stu-id="73456-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="73456-120">Chaque expression de calcul est soutenue par un type *de constructeur.*</span><span class="sxs-lookup"><span data-stu-id="73456-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="73456-121">Le type constructeur définit les opérations qui sont disponibles pour l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="73456-122">Voir [Créer un nouveau type d’expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisée.</span><span class="sxs-lookup"><span data-stu-id="73456-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="73456-123">Vue d’ensemble de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="73456-123">Syntax overview</span></span>

<span data-ttu-id="73456-124">Toutes les expressions de calcul ont la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="73456-124">All computation expressions have the following form:</span></span>

```fsharp
builder-expr { cexper }
```

<span data-ttu-id="73456-125">où `builder-expr` est le nom d’un type de constructeur `cexper` qui définit l’expression de calcul, et est le corps d’expression de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="73456-126">Par exemple, `async` le code d’expression de calcul peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="73456-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="73456-127">Il existe une syntaxe spéciale et supplémentaire disponible dans une expression de calcul, comme le montre l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="73456-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="73456-128">Les formes d’expression suivantes sont possibles avec des expressions de calcul :</span><span class="sxs-lookup"><span data-stu-id="73456-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="73456-129">Chacun de ces mots clés, et d’autres mots-clés F standard ne sont disponibles que dans une expression de calcul s’ils ont été définis dans le type de constructeur d’accompagnement.</span><span class="sxs-lookup"><span data-stu-id="73456-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="73456-130">La seule exception `match!`à cela est , qui est `let!` lui-même sucre syntaxique pour l’utilisation de suivi d’un match de modèle sur le résultat.</span><span class="sxs-lookup"><span data-stu-id="73456-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="73456-131">Le type de constructeur est un objet qui définit des méthodes spéciales qui régissent la façon dont les fragments de l’expression de calcul sont combinés; c’est-à-dire que ses méthodes contrôlent le comportement de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="73456-132">Une autre façon de décrire une classe de constructeur est de dire qu’il vous permet de personnaliser le fonctionnement de nombreuses constructions de F, telles que des boucles et des fixations.</span><span class="sxs-lookup"><span data-stu-id="73456-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="73456-133">Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom:</span><span class="sxs-lookup"><span data-stu-id="73456-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="73456-134">Si vous liez l’appel à `let`une expression de calcul avec, vous n’obtiendrez pas le résultat de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="73456-135">Au lieu de cela, vous aurez lié la valeur de l’appel *non réalisé* à cette expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="73456-136">Utilisez `let!` pour lier au résultat.</span><span class="sxs-lookup"><span data-stu-id="73456-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="73456-137">`let!`est défini `Bind(x, f)` par le membre sur le type de constructeur.</span><span class="sxs-lookup"><span data-stu-id="73456-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="73456-138">Le `do!` mot clé est pour appeler une `unit`expression de calcul `Zero` qui renvoie un type-comme (défini par le membre sur le constructeur):</span><span class="sxs-lookup"><span data-stu-id="73456-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="73456-139">Pour le [flux de travail async](asynchronous-workflows.md), ce type est `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="73456-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="73456-140">Pour d’autres expressions de calcul, `CExpType<unit>`le type est susceptible d’être .</span><span class="sxs-lookup"><span data-stu-id="73456-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="73456-141">`do!`est défini `Bind(x, f)` par le membre sur `f` le `unit`type de constructeur, où produit un .</span><span class="sxs-lookup"><span data-stu-id="73456-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="73456-142">Le `yield` mot clé est pour le retour d’une valeur de <xref:System.Collections.Generic.IEnumerable%601>l’expression de calcul afin qu’il puisse être consommé comme un :</span><span class="sxs-lookup"><span data-stu-id="73456-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="73456-143">Dans la plupart des cas, il peut être omis par les appelants.</span><span class="sxs-lookup"><span data-stu-id="73456-143">In most cases, it can be omitted by callers.</span></span> <span data-ttu-id="73456-144">La façon la plus `yield` courante `->` d’omettre est avec l’opérateur :</span><span class="sxs-lookup"><span data-stu-id="73456-144">The most common way to omit `yield` is with the `->` operator:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="73456-145">Pour des expressions plus complexes qui pourraient donner beaucoup de valeurs différentes, et peut-être sous condition, simplement omettre le mot clé peut faire:</span><span class="sxs-lookup"><span data-stu-id="73456-145">For more complex expressions that might yield many different values, and perhaps conditionally, simply omitting the keyword can do:</span></span>

```fsharp
let weekdays includeWeekend =
    seq {
        "Monday"
        "Tuesday"
        "Wednesday"
        "Thursday"
        "Friday"
        if includeWeekend then
            "Saturday"
            "Sunday"
    }
```

<span data-ttu-id="73456-146">Comme avec le [mot clé de rendement dans C ,](../../csharp/language-reference/keywords/yield.md)chaque élément dans l’expression de calcul est retourné comme il est itéré.</span><span class="sxs-lookup"><span data-stu-id="73456-146">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="73456-147">`yield`est défini `Yield(x)` par le membre sur `x` le type de constructeur, où est l’élément à céder.</span><span class="sxs-lookup"><span data-stu-id="73456-147">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="73456-148">Le `yield!` mot clé est pour aplatir une collection de valeurs à partir d’une expression de calcul:</span><span class="sxs-lookup"><span data-stu-id="73456-148">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..3 -> i * i
    }

let cubes =
    seq {
        for i in 1..3 -> i * i * i
    }

let squaresAndCubes =
    seq {
        yield! squares
        yield! cubes
    }

printfn "%A" squaresAndCubes // Prints - 1; 4; 9; 1; 8; 27
```

<span data-ttu-id="73456-149">Une fois évaluée, l’expression `yield!` de calcul appelée par verra ses éléments redélévés un par un, aplatissant le résultat.</span><span class="sxs-lookup"><span data-stu-id="73456-149">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="73456-150">`yield!`est défini `YieldFrom(x)` par le membre sur `x` le type de constructeur, où est une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="73456-150">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

<span data-ttu-id="73456-151">Contrairement `yield` `yield!` à , doit être explicitement spécifié.</span><span class="sxs-lookup"><span data-stu-id="73456-151">Unlike `yield`, `yield!` must be explicitly specified.</span></span> <span data-ttu-id="73456-152">Son comportement n’est pas implicite dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-152">Its behavior isn't implicit in computation expressions.</span></span>

### `return`

<span data-ttu-id="73456-153">Le `return` mot clé enveloppe une valeur dans le type correspondant à l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-153">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="73456-154">Mis à part les `yield`expressions de calcul à l’aide , il est utilisé pour «compléter» une expression de calcul:</span><span class="sxs-lookup"><span data-stu-id="73456-154">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="73456-155">`return`est défini `Return(x)` par le membre sur `x` le type de constructeur, où est l’élément à envelopper.</span><span class="sxs-lookup"><span data-stu-id="73456-155">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="73456-156">Le `return!` mot clé réalise la valeur d’une expression de calcul et enveloppe qui résultent dans le type correspondant à l’expression de calcul:</span><span class="sxs-lookup"><span data-stu-id="73456-156">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="73456-157">`return!`est défini `ReturnFrom(x)` par le membre sur `x` le type de constructeur, où est une autre expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-157">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="73456-158">Le `match!` mot clé vous permet d’inlimiter un appel à une autre expression de calcul et de correspondance de modèle sur son résultat :</span><span class="sxs-lookup"><span data-stu-id="73456-158">The `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="73456-159">Lorsque vous appelez une `match!`expression de calcul avec , `let!`il se rendra compte du résultat de l’appel comme .</span><span class="sxs-lookup"><span data-stu-id="73456-159">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="73456-160">Ceci est souvent utilisé lors de l’appel d’une expression de calcul lorsque le résultat est une [option](options.md).</span><span class="sxs-lookup"><span data-stu-id="73456-160">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="73456-161">Expressions de calcul intégrées</span><span class="sxs-lookup"><span data-stu-id="73456-161">Built-in computation expressions</span></span>

<span data-ttu-id="73456-162">La bibliothèque de base de F définit trois expressions de calcul intégrées : [Séquence Expressions](sequences.md), flux de [travail asynchrones](asynchronous-workflows.md)et [Expressions de requête](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="73456-162">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="73456-163">Création d’un nouveau type d’expression de calcul</span><span class="sxs-lookup"><span data-stu-id="73456-163">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="73456-164">Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de constructeur et en définissant certaines méthodes spéciales sur la classe.</span><span class="sxs-lookup"><span data-stu-id="73456-164">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="73456-165">La classe de constructeur peut définir optionnellement les méthodes énumérées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="73456-165">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="73456-166">Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de constructeur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="73456-166">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="73456-167">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="73456-167">**Method**</span></span>|<span data-ttu-id="73456-168">**Signature typique(s)**</span><span class="sxs-lookup"><span data-stu-id="73456-168">**Typical signature(s)**</span></span>|<span data-ttu-id="73456-169">**Description**</span><span class="sxs-lookup"><span data-stu-id="73456-169">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="73456-170">Appelé `let!` et `do!` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-170">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="73456-171">Enveloppe une expression de calcul comme une fonction.</span><span class="sxs-lookup"><span data-stu-id="73456-171">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="73456-172">Appelé `return` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-172">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="73456-173">Appelé `return!` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-173">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="73456-174">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="73456-174">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="73456-175">Exécute une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-175">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="73456-176">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="73456-176">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="73456-177">Appelé au séquençage dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-177">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="73456-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="73456-178">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="73456-179">Appelé `for...do` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-179">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="73456-180">Appelé `try...finally` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-180">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="73456-181">Appelé `try...with` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-181">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|<span data-ttu-id="73456-182">Appelé `use` à des fixations dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-182">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="73456-183">Appelé `while...do` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-183">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="73456-184">Appelé `yield` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-184">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="73456-185">Appelé `yield!` pour des expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-185">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="73456-186">Appelé pour `else` des `if...then` branches vides d’expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-186">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="73456-187">Indique que l’expression de calcul `Run` est transmise au membre comme citation.</span><span class="sxs-lookup"><span data-stu-id="73456-187">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="73456-188">Il traduit tous les cas d’un calcul en une citation.</span><span class="sxs-lookup"><span data-stu-id="73456-188">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="73456-189">Beaucoup de méthodes dans une classe `M<'T>` de constructeur utilisent et retournent une construction, qui est généralement un type défini `Async<'T>` séparément qui caractérise le type `Seq<'T>` de calculs combinés, par exemple, pour les flux de travail asynchrones et pour les flux de travail de séquence.</span><span class="sxs-lookup"><span data-stu-id="73456-189">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="73456-190">Les signatures de ces méthodes leur permettent d’être combinés et imbriqués les uns avec les autres, de sorte que l’objet de flux de travail retourné d’une construction peut être passé à l’autre.</span><span class="sxs-lookup"><span data-stu-id="73456-190">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="73456-191">Le compilateur, lorsqu’il analyse une expression de calcul, convertit l’expression en une série d’appels de fonction imbriqués en utilisant les méthodes dans le tableau précédent et le code dans l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-191">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="73456-192">L’expression imbriquée est de la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="73456-192">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="73456-193">Dans le code ci-dessus, les appels vers et `Run` `Delay` sont omis s’ils ne sont pas définis dans la classe de constructeur d’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-193">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="73456-194">Le corps de l’expression de calcul, `{| cexpr |}`ici dénoté comme , est traduit en appels impliquant les méthodes de la classe de constructeur par les traductions décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="73456-194">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="73456-195">L’expression `{| cexpr |}` de calcul est définie de façon récursive selon ces traductions où `expr` se trouve une expression de F et `cexpr` est une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-195">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="73456-196">Expression</span><span class="sxs-lookup"><span data-stu-id="73456-196">Expression</span></span>|<span data-ttu-id="73456-197">Traduction</span><span class="sxs-lookup"><span data-stu-id="73456-197">Translation</span></span>|
|----------|-----------|
|<code>{ let binding in cexpr }</code>|<code>let binding in {&#124; cexpr &#124;}</code>|
|<code>{ let! pattern = expr in cexpr }</code>|<code>builder.Bind(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ do! expr in cexpr }</code>|<code>builder.Bind(expr, (fun () -> {&#124; cexpr &#124;}))</code>|
|<code>{ yield expr }</code>|`builder.Yield(expr)`|
|<code>{ yield! expr }</code>|`builder.YieldFrom(expr)`|
|<code>{ return expr }</code>|`builder.Return(expr)`|
|<code>{ return! expr }</code>|`builder.ReturnFrom(expr)`|
|<code>{ use pattern = expr in cexpr }</code>|<code>builder.Using(expr, (fun pattern -> {&#124; cexpr &#124;}))</code>|
|<code>{ use! value = expr in cexpr }</code>|<code>builder.Bind(expr, (fun value -> builder.Using(value, (fun value -> { cexpr }))))</code>|
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else builder.Zero()</code>|
|<code>{ if expr then cexpr0 else cexpr1 &#124;}</code>|<code>if expr then { cexpr0 } else { cexpr1 }</code>|
|<code>{ match expr with &#124; pattern_i -> cexpr_i }</code>|<code>match expr with &#124; pattern_i -> { cexpr_i }</code>|
|<code>{ for pattern in expr do cexpr }</code>|<code>builder.For(enumeration, (fun pattern -> { cexpr }))</code>|
|<code>{ for identifier = expr1 to expr2 do cexpr }</code>|<code>builder.For(enumeration, (fun identifier -> { cexpr }))</code>|
|<code>{ while expr do cexpr }</code>|<code>builder.While(fun () -> expr, builder.Delay({ cexpr }))</code>|
|<code>{ try cexpr with &#124; pattern_i -> expr_i }</code>|<code>builder.TryWith(builder.Delay({ cexpr }), (fun value -> match value with &#124; pattern_i -> expr_i &#124; exn -> reraise exn)))</code>|
|<code>{ try cexpr finally expr }</code>|<code>builder.TryFinally(builder.Delay( { cexpr }), (fun () -> expr))</code>|
|<code>{ cexpr1; cexpr2 }</code>|<code>builder.Combine({ cexpr1 }, { cexpr2 })</code>|
|<code>{ other-expr; cexpr }</code>|<code>expr; { cexpr }</code>|
|<code>{ other-expr }</code>|`expr; builder.Zero()`|

<span data-ttu-id="73456-198">Dans le tableau `other-expr` précédent, décrit une expression qui n’est pas autrement répertoriée dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="73456-198">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="73456-199">Une classe de constructeurs n’a pas besoin de mettre en œuvre toutes les méthodes et de soutenir toutes les traductions énumérées dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="73456-199">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="73456-200">Les constructions qui ne sont pas mises en œuvre ne sont pas disponibles dans les expressions de calcul de ce type.</span><span class="sxs-lookup"><span data-stu-id="73456-200">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="73456-201">Par exemple, si vous ne `use` voulez pas prendre en charge le mot clé `Use` dans vos expressions de calcul, vous pouvez omettre la définition de dans votre classe de constructeur.</span><span class="sxs-lookup"><span data-stu-id="73456-201">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="73456-202">L’exemple de code suivant montre une expression de calcul qui encapsule un calcul comme une série d’étapes qui peuvent être évaluées une étape à la fois.</span><span class="sxs-lookup"><span data-stu-id="73456-202">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="73456-203">Un type d’union discriminé, `OkOrException`code l’état d’erreur de l’expression telle qu’évaluée jusqu’à présent.</span><span class="sxs-lookup"><span data-stu-id="73456-203">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="73456-204">Ce code montre plusieurs modèles typiques que vous pouvez utiliser dans vos expressions de calcul, telles que les implémentations de plaques chauffantes de certaines des méthodes de constructeur.</span><span class="sxs-lookup"><span data-stu-id="73456-204">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

```fsharp
// Computations that can be run step by step
type Eventually<'T> =
    | Done of 'T
    | NotYetDone of (unit -> Eventually<'T>)

module Eventually =
    // The bind for the computations. Append 'func' to the
    // computation.
    let rec bind func expr =
        match expr with
        | Done value -> func value
        | NotYetDone work -> NotYetDone (fun () -> bind func (work()))

    // Return the final value wrapped in the Eventually type.
    let result value = Done value

    type OkOrException<'T> =
        | Ok of 'T
        | Exception of System.Exception

    // The catch for the computations. Stitch try/with throughout
    // the computation, and return the overall result as an OkOrException.
    let rec catch expr =
        match expr with
        | Done value -> result (Ok value)
        | NotYetDone work ->
            NotYetDone (fun () ->
                let res = try Ok(work()) with | exn -> Exception exn
                match res with
                | Ok cont -> catch cont // note, a tailcall
                | Exception exn -> result (Exception exn))

    // The delay operator.
    let delay func = NotYetDone (fun () -> func())

    // The stepping action for the computations.
    let step expr =
        match expr with
        | Done _ -> expr
        | NotYetDone func -> func ()

    // The rest of the operations are boilerplate.
    // The tryFinally operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryFinally expr compensation =
        catch (expr)
        |> bind (fun res ->
            compensation();
            match res with
            | Ok value -> result value
            | Exception exn -> raise exn)

    // The tryWith operator.
    // This is boilerplate in terms of "result", "catch", and "bind".
    let tryWith exn handler =
        catch exn
        |> bind (function Ok value -> result value | Exception exn -> handler exn)

    // The whileLoop operator.
    // This is boilerplate in terms of "result" and "bind".
    let rec whileLoop pred body =
        if pred() then body |> bind (fun _ -> whileLoop pred body)
        else result ()

    // The sequential composition operator.
    // This is boilerplate in terms of "result" and "bind".
    let combine expr1 expr2 =
        expr1 |> bind (fun () -> expr2)

    // The using operator.
    let using (resource: #System.IDisposable) func =
        tryFinally (func resource) (fun () -> resource.Dispose())

    // The forLoop operator.
    // This is boilerplate in terms of "catch", "result", and "bind".
    let forLoop (collection:seq<_>) func =
        let ie = collection.GetEnumerator()
        tryFinally
            (whileLoop
                (fun () -> ie.MoveNext())
                (delay (fun () -> let value = ie.Current in func value)))
            (fun () -> ie.Dispose())

// The builder class.
type EventuallyBuilder() =
    member x.Bind(comp, func) = Eventually.bind func comp
    member x.Return(value) = Eventually.result value
    member x.ReturnFrom(value) = value
    member x.Combine(expr1, expr2) = Eventually.combine expr1 expr2
    member x.Delay(func) = Eventually.delay func
    member x.Zero() = Eventually.result ()
    member x.TryWith(expr, handler) = Eventually.tryWith expr handler
    member x.TryFinally(expr, compensation) = Eventually.tryFinally expr compensation
    member x.For(coll:seq<_>, func) = Eventually.forLoop coll func
    member x.Using(resource, expr) = Eventually.using resource expr

let eventually = new EventuallyBuilder()

let comp = eventually {
    for x in 1..2 do
        printfn " x = %d" x
    return 3 + 4 }

// Try the remaining lines in F# interactive to see how this
// computation expression works in practice.
let step x = Eventually.step x

// returns "NotYetDone <closure>"
comp |> step

// prints "x = 1"
// returns "NotYetDone <closure>"
comp |> step |> step

// prints "x = 1"
// prints "x = 2"
// returns "Done 7"
comp |> step |> step |> step |> step
```

<span data-ttu-id="73456-205">Une expression de calcul a un type sous-jacent, que l’expression renvoie.</span><span class="sxs-lookup"><span data-stu-id="73456-205">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="73456-206">Le type sous-jacent peut représenter un résultat calculé ou un calcul retardé qui peut être effectué, ou il peut fournir un moyen d’itérer par un certain type de collecte.</span><span class="sxs-lookup"><span data-stu-id="73456-206">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="73456-207">Dans l’exemple précédent, le type sous-jacent a **finalement**été .</span><span class="sxs-lookup"><span data-stu-id="73456-207">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="73456-208">Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73456-208">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73456-209">Pour une expression de requête, <xref:System.Linq.IQueryable?displayProperty=nameWithType>le type sous-jacent est .</span><span class="sxs-lookup"><span data-stu-id="73456-209">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73456-210">Pour un flux de travail asynchrone, [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)le type sous-jacent est .</span><span class="sxs-lookup"><span data-stu-id="73456-210">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="73456-211">L’objet `Async` représente l’œuvre à effectuer pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="73456-211">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="73456-212">Par exemple, [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) vous appelez pour exécuter un calcul et retourner le résultat.</span><span class="sxs-lookup"><span data-stu-id="73456-212">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="73456-213">Opérations personnalisées</span><span class="sxs-lookup"><span data-stu-id="73456-213">Custom Operations</span></span>

<span data-ttu-id="73456-214">Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée en tant qu’opérateur dans une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-214">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="73456-215">Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="73456-215">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="73456-216">Lorsque vous définissez une opération personnalisée, vous devez définir le rendement et les méthodes pour l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-216">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="73456-217">Pour définir une opération personnalisée, mettez-la dans une classe de [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)constructeur pour l’expression de calcul, puis appliquez le .</span><span class="sxs-lookup"><span data-stu-id="73456-217">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="73456-218">Cet attribut prend une chaîne comme un argument, qui est le nom à utiliser dans une opération personnalisée.</span><span class="sxs-lookup"><span data-stu-id="73456-218">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="73456-219">Ce nom entre en portée au début de l’accolade bouclée d’ouverture de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="73456-219">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="73456-220">Par conséquent, vous ne devriez pas utiliser des identifiants qui ont le même nom qu’une opération personnalisée dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="73456-220">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="73456-221">Par exemple, évitez l’utilisation `all` d’identifiants tels que ou `last` dans des expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="73456-221">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="73456-222">Élargir les constructeurs existants avec de nouvelles opérations personnalisées</span><span class="sxs-lookup"><span data-stu-id="73456-222">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="73456-223">Si vous avez déjà une classe de constructeur, ses opérations personnalisées peuvent être étendues à l’extérieur de cette classe de constructeur.</span><span class="sxs-lookup"><span data-stu-id="73456-223">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="73456-224">Les extensions doivent être déclarées dans les modules.</span><span class="sxs-lookup"><span data-stu-id="73456-224">Extensions must be declared in modules.</span></span> <span data-ttu-id="73456-225">Les espaces de noms ne peuvent pas contenir les membres de vulgarisation, sauf dans le même fichier et le même groupe de déclaration d’espace de nom où le type est défini.</span><span class="sxs-lookup"><span data-stu-id="73456-225">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="73456-226">L’exemple suivant montre l’extension de la classe existante. `Microsoft.FSharp.Linq.QueryBuilder`</span><span class="sxs-lookup"><span data-stu-id="73456-226">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="73456-227">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73456-227">See also</span></span>

- [<span data-ttu-id="73456-228">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="73456-228">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="73456-229">Workflows asynchrones</span><span class="sxs-lookup"><span data-stu-id="73456-229">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="73456-230">Séquences</span><span class="sxs-lookup"><span data-stu-id="73456-230">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="73456-231">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="73456-231">Query Expressions</span></span>](query-expressions.md)

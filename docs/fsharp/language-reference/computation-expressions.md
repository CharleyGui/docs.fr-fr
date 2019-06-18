---
title: Expressions de calcul
description: Découvrez comment créer une syntaxe pratique pour l’écriture de calculs F# que peuvent être séquencés et combinés à l’aide contrôler les liaisons et constructions de flux.
ms.date: 03/15/2019
ms.openlocfilehash: b352c5541bc31b5c583904b99651de9180c8afb3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152031"
---
# <a name="computation-expressions"></a><span data-ttu-id="eb9db-103">Expressions de calcul</span><span class="sxs-lookup"><span data-stu-id="eb9db-103">Computation Expressions</span></span>

<span data-ttu-id="eb9db-104">Expressions de calcul en F# fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de liaisons et constructions de flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="eb9db-104">Computation expressions in F# provide a convenient syntax for writing computations that can be sequenced and combined using control flow constructs and bindings.</span></span> <span data-ttu-id="eb9db-105">En fonction du type d’expression de calcul, elles peuvent être considérés comme un moyen d’exprimer monades, monoids, monad transformateurs et les functors applicative.</span><span class="sxs-lookup"><span data-stu-id="eb9db-105">Depending on the kind of computation expression, they can be thought of as a way to express monads, monoids, monad transformers, and applicative functors.</span></span> <span data-ttu-id="eb9db-106">Cependant, contrairement à d’autres langages (tels que *-notation* de Haskell), ils ne sont pas liées à une simple abstraction et que vous ne comptez pas sur les macros ou d’autres formes de métaprogrammation pour accomplir une syntaxe pratique et sensible au contexte.</span><span class="sxs-lookup"><span data-stu-id="eb9db-106">However, unlike other languages (such as *do-notation* in Haskell), they are not tied to a single abstraction, and do not rely on macros or other forms of metaprogramming to accomplish a convenient and context-sensitive syntax.</span></span>

## <a name="overview"></a><span data-ttu-id="eb9db-107">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="eb9db-107">Overview</span></span>

<span data-ttu-id="eb9db-108">Les calculs peuvent prendre différentes formes.</span><span class="sxs-lookup"><span data-stu-id="eb9db-108">Computations can take many forms.</span></span> <span data-ttu-id="eb9db-109">La forme la plus courante de calcul est une exécution monothread, qui est facile à comprendre et à modifier.</span><span class="sxs-lookup"><span data-stu-id="eb9db-109">The most common form of computation is single-threaded execution, which is easy to understand and modify.</span></span> <span data-ttu-id="eb9db-110">Toutefois, pas toutes les formes de calcul sont aussi simples que d’une exécution monothread.</span><span class="sxs-lookup"><span data-stu-id="eb9db-110">However, not all forms of computation are as straightforward as single-threaded execution.</span></span> <span data-ttu-id="eb9db-111">Voici quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="eb9db-111">Some examples include:</span></span>

* <span data-ttu-id="eb9db-112">Calculs non déterministes</span><span class="sxs-lookup"><span data-stu-id="eb9db-112">Non-deterministic computations</span></span>
* <span data-ttu-id="eb9db-113">Calculs asynchrones</span><span class="sxs-lookup"><span data-stu-id="eb9db-113">Asynchronous computations</span></span>
* <span data-ttu-id="eb9db-114">Calculs effectful</span><span class="sxs-lookup"><span data-stu-id="eb9db-114">Effectful computations</span></span>
* <span data-ttu-id="eb9db-115">Calculs générative</span><span class="sxs-lookup"><span data-stu-id="eb9db-115">Generative computations</span></span>

<span data-ttu-id="eb9db-116">En règle générale, il existe *contextuelle* calculs que vous devez effectuer dans certaines parties d’une application.</span><span class="sxs-lookup"><span data-stu-id="eb9db-116">More generally, there are *context-sensitive* computations that you must perform in certain parts of an application.</span></span> <span data-ttu-id="eb9db-117">Écrire du code contextuelle peut être difficile, car il est facile de calculs de « fuite » en dehors d’un contexte donné sans abstractions pour vous éviter de le faire.</span><span class="sxs-lookup"><span data-stu-id="eb9db-117">Writing context-sensitive code can be challenging, as it is easy to "leak" computations outside of a given context without abstractions to prevent you from doing so.</span></span> <span data-ttu-id="eb9db-118">Ces abstractions sont souvent difficile à écrire vous-même, ce qui explique pourquoi F# a une méthode généralisée pour faire ce qu’on appelle **expressions de calcul**.</span><span class="sxs-lookup"><span data-stu-id="eb9db-118">These abstractions are often challenging to write by yourself, which is why F# has a generalized way to do so called **computation expressions**.</span></span>

<span data-ttu-id="eb9db-119">Expressions de calcul offrent un modèle uniforme de syntaxe et d’abstraction pour l’encodage des calculs contextuelles.</span><span class="sxs-lookup"><span data-stu-id="eb9db-119">Computation expressions offer a uniform syntax and abstraction model for encoding context-sensitive computations.</span></span>

<span data-ttu-id="eb9db-120">Chaque expression de calcul est soutenue par un *Générateur* type.</span><span class="sxs-lookup"><span data-stu-id="eb9db-120">Every computation expression is backed by a *builder* type.</span></span> <span data-ttu-id="eb9db-121">Le type de générateur de rapports définit les opérations qui sont disponibles pour l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-121">The builder type defines the operations that are available for the computation expression.</span></span> <span data-ttu-id="eb9db-122">Consultez [création d’un nouveau Type d’Expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisé.</span><span class="sxs-lookup"><span data-stu-id="eb9db-122">See [Creating a New Type of Computation Expression](computation-expressions.md#creating-a-new-type-of-computation-expression), which shows how to create a custom computation expression.</span></span>

### <a name="syntax-overview"></a><span data-ttu-id="eb9db-123">Vue d’ensemble de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb9db-123">Syntax overview</span></span>

<span data-ttu-id="eb9db-124">Toutes les expressions de calcul ont la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="eb9db-124">All computation expressions have the following form:</span></span>

```
builder-expr { cexper }
```

<span data-ttu-id="eb9db-125">où `builder-expr` est le nom d’un type de générateur qui définit l’expression de calcul, et `cexper` est le corps de l’expression de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-125">where `builder-expr` is the name of a builder type that defines the computation expression, and `cexper` is the expression body of the computation expression.</span></span> <span data-ttu-id="eb9db-126">Par exemple, `async` code d’expression de calcul peut ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="eb9db-126">For example, `async` computation expression code can look like this:</span></span>

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

<span data-ttu-id="eb9db-127">Une syntaxe spéciale, supplémentaire est disponible au sein d’une expression de calcul, comme indiqué dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="eb9db-127">There is a special, additional syntax available within a computation expression, as shown in the previous example.</span></span> <span data-ttu-id="eb9db-128">Les formes d’expression suivantes sont possibles avec les expressions de calcul :</span><span class="sxs-lookup"><span data-stu-id="eb9db-128">The following expression forms are possible with computation expressions:</span></span>

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

<span data-ttu-id="eb9db-129">Chacune de ces mots clés et autres standard F# mots clés sont uniquement disponibles dans une expression de calcul s’ils ont été définis dans le type de générateur de rapports de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="eb9db-129">Each of these keywords, and other standard F# keywords are only available in a computation expression if they have been defined in the backing builder type.</span></span> <span data-ttu-id="eb9db-130">La seule exception à cela est `match!`, qui est lui-même liant syntaxique pour l’utilisation de `let!` suivie d’une correspondance de modèle sur le résultat.</span><span class="sxs-lookup"><span data-stu-id="eb9db-130">The only exception to this is `match!`, which is itself syntactic sugar for the use of `let!` followed by a pattern match on the result.</span></span>

<span data-ttu-id="eb9db-131">Le type de générateur est un objet qui définit des méthodes spéciales qui régissent la manière de que combiner les fragments de l’expression de calcul ; Autrement dit, ses méthodes contrôlent le comportement de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-131">The builder type is an object that defines special methods that govern the way the fragments of the computation expression are combined; that is, its methods control how the computation expression behaves.</span></span> <span data-ttu-id="eb9db-132">Un autre moyen de décrire une classe de générateur est à dire qu’il vous permet de personnaliser l’opération de nombreuses F# construit, comme des boucles et des liaisons.</span><span class="sxs-lookup"><span data-stu-id="eb9db-132">Another way to describe a builder class is to say that it enables you to customize the operation of many F# constructs, such as loops and bindings.</span></span>

### `let!`

<span data-ttu-id="eb9db-133">Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom :</span><span class="sxs-lookup"><span data-stu-id="eb9db-133">The `let!` keyword binds the result of a call to another computation expression to a name:</span></span>

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

<span data-ttu-id="eb9db-134">Si vous liez l’appel à une expression de calcul avec `let`, vous n’obtiendrez pas le résultat de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-134">If you bind the call to a computation expression with `let`, you will not get the result of the computation expression.</span></span> <span data-ttu-id="eb9db-135">Au lieu de cela, vous serez l’avez liée la valeur de la *non réalisés* l’appel à cette expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-135">Instead, you will have bound the value of the *unrealized* call to that computation expression.</span></span> <span data-ttu-id="eb9db-136">Utilisez `let!` à lier au résultat.</span><span class="sxs-lookup"><span data-stu-id="eb9db-136">Use `let!` to bind to the result.</span></span>

<span data-ttu-id="eb9db-137">`let!` est défini par le `Bind(x, f)` membre sur le type de générateur de rapports.</span><span class="sxs-lookup"><span data-stu-id="eb9db-137">`let!` is defined by the `Bind(x, f)` member on the builder type.</span></span>

### `do!`

<span data-ttu-id="eb9db-138">Le `do!` mot clé est pour l’appel d’une expression de calcul qui retourne un `unit`-comme type (défini par le `Zero` membre sur le générateur) :</span><span class="sxs-lookup"><span data-stu-id="eb9db-138">The `do!` keyword is for calling a computation expression that returns a `unit`-like type (defined by the `Zero` member on the builder):</span></span>

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

<span data-ttu-id="eb9db-139">Pour le [async workflow](asynchronous-workflows.md), ce type est `Async<unit>`.</span><span class="sxs-lookup"><span data-stu-id="eb9db-139">For the [async workflow](asynchronous-workflows.md), this type is `Async<unit>`.</span></span> <span data-ttu-id="eb9db-140">Pour les autres expressions de calcul, le type est susceptible d’être `CExpType<unit>`.</span><span class="sxs-lookup"><span data-stu-id="eb9db-140">For other computation expressions, the type is likely to be `CExpType<unit>`.</span></span>

<span data-ttu-id="eb9db-141">`do!` est défini par le `Bind(x, f)` membre sur le type de générateur de rapports, où `f` génère un `unit`.</span><span class="sxs-lookup"><span data-stu-id="eb9db-141">`do!` is defined by the `Bind(x, f)` member on the builder type, where `f` produces a `unit`.</span></span>

### `yield`

<span data-ttu-id="eb9db-142">Le `yield` mot clé est de retourner une valeur à partir de l’expression de calcul afin qu’il peut être utilisé comme un <xref:System.Collections.Generic.IEnumerable%601>:</span><span class="sxs-lookup"><span data-stu-id="eb9db-142">The `yield` keyword is for returning a value from the computation expression so that it can be consumed as an <xref:System.Collections.Generic.IEnumerable%601>:</span></span>

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

<span data-ttu-id="eb9db-143">Comme avec la [yield mot clé dans C#](../../csharp/language-reference/keywords/yield.md), chaque élément dans l’expression de calcul est cédée car elle est itérée.</span><span class="sxs-lookup"><span data-stu-id="eb9db-143">As with the [yield keyword in C#](../../csharp/language-reference/keywords/yield.md), each element in the computation expression is yielded back as it is iterated.</span></span>

<span data-ttu-id="eb9db-144">`yield` est défini par le `Yield(x)` membre sur le type de générateur de rapports, où `x` est l’élément à générer de nouveau.</span><span class="sxs-lookup"><span data-stu-id="eb9db-144">`yield` is defined by the `Yield(x)` member on the builder type, where `x` is the item to yield back.</span></span>

### `yield!`

<span data-ttu-id="eb9db-145">Le `yield!` mot clé est pour la mise à plat une collection de valeurs à partir d’une expression de calcul :</span><span class="sxs-lookup"><span data-stu-id="eb9db-145">The `yield!` keyword is for flattening a collection of values from a computation expression:</span></span>

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

<span data-ttu-id="eb9db-146">Lors de l’évaluation, l’expression de calcul appelées par `yield!` seront vous ses éléments a différé un par un, le résultat de mise à plat.</span><span class="sxs-lookup"><span data-stu-id="eb9db-146">When evaluated, the computation expression called by `yield!` will have its items yielded back one-by-one, flattening the result.</span></span>

<span data-ttu-id="eb9db-147">`yield!` est défini par le `YieldFrom(x)` membre sur le type de générateur de rapports, où `x` est une collection de valeurs.</span><span class="sxs-lookup"><span data-stu-id="eb9db-147">`yield!` is defined by the `YieldFrom(x)` member on the builder type, where `x` is a collection of values.</span></span>

### `return`

<span data-ttu-id="eb9db-148">Le `return` mot clé encapsule une valeur dans le type correspondant à l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-148">The `return` keyword wraps a value in the type corresponding to the computation expression.</span></span> <span data-ttu-id="eb9db-149">Outre les expressions de calcul à l’aide de `yield`, il est utilisé pour une expression de calcul « terminé » :</span><span class="sxs-lookup"><span data-stu-id="eb9db-149">Aside from computation expressions using `yield`, it is used to "complete" a computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="eb9db-150">`return` est défini par le `Return(x)` membre sur le type de générateur de rapports, où `x` est l’élément à encapsuler.</span><span class="sxs-lookup"><span data-stu-id="eb9db-150">`return` is defined by the `Return(x)` member on the builder type, where `x` is the item to wrap.</span></span>

### `return!`

<span data-ttu-id="eb9db-151">Le `return!` mot clé se rend compte de la valeur d’une expression de calcul et encapsule ce résultat dans le type correspondant à l’expression de calcul :</span><span class="sxs-lookup"><span data-stu-id="eb9db-151">The `return!` keyword realizes the value of a computation expression and wraps that result in the type corresponding to the computation expression:</span></span>

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

<span data-ttu-id="eb9db-152">`return!` est défini par le `ReturnFrom(x)` membre sur le type de générateur de rapports, où `x` est une autre expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-152">`return!` is defined by the `ReturnFrom(x)` member on the builder type, where `x` is another computation expression.</span></span>

### `match!`

<span data-ttu-id="eb9db-153">En commençant par F# 4.5, le `match!` mot clé vous permet d’inline un appel à une autre correspondance d’expression et le modèle de calcul sur son résultat :</span><span class="sxs-lookup"><span data-stu-id="eb9db-153">Starting with F# 4.5, the `match!` keyword allows you to inline a call to another computation expression and pattern match on its result:</span></span>

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

<span data-ttu-id="eb9db-154">Lors de l’appel d’une expression de calcul avec `match!`, elle réalisera le résultat de l’appel comme `let!`.</span><span class="sxs-lookup"><span data-stu-id="eb9db-154">When calling a computation expression with `match!`, it will realize the result of the call like `let!`.</span></span> <span data-ttu-id="eb9db-155">Il est souvent utilisé lors de l’appel à une expression de calcul où le résultat est un [facultatif](options.md).</span><span class="sxs-lookup"><span data-stu-id="eb9db-155">This is often used when calling a computation expression where the result is an [optional](options.md).</span></span>

## <a name="built-in-computation-expressions"></a><span data-ttu-id="eb9db-156">Expressions de calcul intégré</span><span class="sxs-lookup"><span data-stu-id="eb9db-156">Built-in computation expressions</span></span>

<span data-ttu-id="eb9db-157">Le F# bibliothèque principale définit trois expressions de calcul intégré : [Expressions de séquence](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md), et [Expressions de requête](query-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="eb9db-157">The F# core library defines three built-in computation expressions: [Sequence Expressions](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Query Expressions](query-expressions.md).</span></span>

## <a name="creating-a-new-type-of-computation-expression"></a><span data-ttu-id="eb9db-158">Création d’un nouveau Type d’Expression de calcul</span><span class="sxs-lookup"><span data-stu-id="eb9db-158">Creating a New Type of Computation Expression</span></span>

<span data-ttu-id="eb9db-159">Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de générateur et en définissant certaines méthodes spéciales sur la classe.</span><span class="sxs-lookup"><span data-stu-id="eb9db-159">You can define the characteristics of your own computation expressions by creating a builder class and defining certain special methods on the class.</span></span> <span data-ttu-id="eb9db-160">La classe de générateur peut éventuellement définir les méthodes comme indiqué dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="eb9db-160">The builder class can optionally define the methods as listed in the following table.</span></span>

<span data-ttu-id="eb9db-161">Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de générateur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="eb9db-161">The following table describes methods that can be used in a workflow builder class.</span></span>

|<span data-ttu-id="eb9db-162">**Méthode**</span><span class="sxs-lookup"><span data-stu-id="eb9db-162">**Method**</span></span>|<span data-ttu-id="eb9db-163">**Signatures typiques**</span><span class="sxs-lookup"><span data-stu-id="eb9db-163">**Typical signature(s)**</span></span>|<span data-ttu-id="eb9db-164">**Description**</span><span class="sxs-lookup"><span data-stu-id="eb9db-164">**Description**</span></span>|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|<span data-ttu-id="eb9db-165">Appelé pour `let!` et `do!` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-165">Called for `let!` and `do!` in computation expressions.</span></span>|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|<span data-ttu-id="eb9db-166">Encapsule une expression de calcul en tant que fonction.</span><span class="sxs-lookup"><span data-stu-id="eb9db-166">Wraps a computation expression as a function.</span></span>|
|`Return`|`'T -> M<'T>`|<span data-ttu-id="eb9db-167">Appelé pour `return` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-167">Called for `return` in computation expressions.</span></span>|
|`ReturnFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="eb9db-168">Appelé pour `return!` dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-168">Called for `return!` in computation expressions.</span></span>|
|`Run`|<span data-ttu-id="eb9db-169">`M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="eb9db-169">`M<'T> -> M<'T>` or</span></span><br /><br />`M<'T> -> 'T`|<span data-ttu-id="eb9db-170">Exécute une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-170">Executes a computation expression.</span></span>|
|`Combine`|<span data-ttu-id="eb9db-171">`M<'T> * M<'T> -> M<'T>` ou</span><span class="sxs-lookup"><span data-stu-id="eb9db-171">`M<'T> * M<'T> -> M<'T>` or</span></span><br /><br />`M<unit> * M<'T> -> M<'T>`|<span data-ttu-id="eb9db-172">Appelée pour le séquencement dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-172">Called for sequencing in computation expressions.</span></span>|
|`For`|<span data-ttu-id="eb9db-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` ou</span><span class="sxs-lookup"><span data-stu-id="eb9db-173">`seq<'T> * ('T -> M<'U>) -> M<'U>` or</span></span><br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|<span data-ttu-id="eb9db-174">Appelé pour `for...do` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-174">Called for `for...do` expressions in computation expressions.</span></span>|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|<span data-ttu-id="eb9db-175">Appelé pour `try...finally` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-175">Called for `try...finally` expressions in computation expressions.</span></span>|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|<span data-ttu-id="eb9db-176">Appelé pour `try...with` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-176">Called for `try...with` expressions in computation expressions.</span></span>|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|<span data-ttu-id="eb9db-177">Appelé pour `use` liaisons dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-177">Called for `use` bindings in computation expressions.</span></span>|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|<span data-ttu-id="eb9db-178">Appelé pour `while...do` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-178">Called for `while...do` expressions in computation expressions.</span></span>|
|`Yield`|`'T -> M<'T>`|<span data-ttu-id="eb9db-179">Appelé pour `yield` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-179">Called for `yield` expressions in computation expressions.</span></span>|
|`YieldFrom`|`M<'T> -> M<'T>`|<span data-ttu-id="eb9db-180">Appelé pour `yield!` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-180">Called for `yield!` expressions in computation expressions.</span></span>|
|`Zero`|`unit -> M<'T>`|<span data-ttu-id="eb9db-181">Appelé pour vide `else` branches de `if...then` expressions dans les expressions de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-181">Called for empty `else` branches of `if...then` expressions in computation expressions.</span></span>|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|<span data-ttu-id="eb9db-182">Indique que l’expression de calcul est passée à la `Run` membre en tant que quotation.</span><span class="sxs-lookup"><span data-stu-id="eb9db-182">Indicates that the computation expression is passed to the `Run` member as a quotation.</span></span> <span data-ttu-id="eb9db-183">Il traduit toutes les instances d’un calcul dans une quotation.</span><span class="sxs-lookup"><span data-stu-id="eb9db-183">It translates all instances of a computation into a quotation.</span></span>|

<span data-ttu-id="eb9db-184">La plupart des méthodes dans une classe de générateur utilisent et retournent un `M<'T>` construct, qui est généralement un type défini séparément qui caractérise le genre des calculs combinés, par exemple, `Async<'T>` pour les flux de travail asynchrones et `Seq<'T>` pour les workflows de la séquence.</span><span class="sxs-lookup"><span data-stu-id="eb9db-184">Many of the methods in a builder class use and return an `M<'T>` construct, which is typically a separately defined type that characterizes the kind of computations being combined, for example, `Async<'T>` for asynchronous workflows and `Seq<'T>` for sequence workflows.</span></span> <span data-ttu-id="eb9db-185">Les signatures de ces méthodes activez-les être combinées et imbriquées avec les autres, afin que l’objet de flux de travail retourné d’une construction qui peut être passé à la suivante.</span><span class="sxs-lookup"><span data-stu-id="eb9db-185">The signatures of these methods enable them to be combined and nested with each other, so that the workflow object returned from one construct can be passed to the next.</span></span> <span data-ttu-id="eb9db-186">Le compilateur, lorsqu’il analyse une expression de calcul, convertit l’expression en une série d’appels de fonction imbriquée en utilisant les méthodes dans le tableau précédent et le code dans l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-186">The compiler, when it parses a computation expression, converts the expression into a series of nested function calls by using the methods in the preceding table and the code in the computation expression.</span></span>

<span data-ttu-id="eb9db-187">L’expression imbriquée est au format suivant :</span><span class="sxs-lookup"><span data-stu-id="eb9db-187">The nested expression is of the following form:</span></span>

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

<span data-ttu-id="eb9db-188">Dans le code ci-dessus, les appels à `Run` et `Delay` sont omis s’ils ne sont pas définis dans la classe de générateur d’expression calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-188">In the above code, the calls to `Run` and `Delay` are omitted if they are not defined in the computation expression builder class.</span></span> <span data-ttu-id="eb9db-189">Le corps de l’expression de calcul, désignée ici comme `{| cexpr |}`, est convertie en appels impliquant les méthodes de la classe de générateur de rapports par les traductions décrites dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="eb9db-189">The body of the computation expression, here denoted as `{| cexpr |}`, is translated into calls involving the methods of the builder class by the translations described in the following table.</span></span> <span data-ttu-id="eb9db-190">L’expression de calcul `{| cexpr |}` est définie de manière récursive en fonction de ces traductions où `expr` est un F# expression et `cexpr` est une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-190">The computation expression `{| cexpr |}` is defined recursively according to these translations where `expr` is an F# expression and `cexpr` is a computation expression.</span></span>

|<span data-ttu-id="eb9db-191">Expression</span><span class="sxs-lookup"><span data-stu-id="eb9db-191">Expression</span></span>|<span data-ttu-id="eb9db-192">Traduction</span><span class="sxs-lookup"><span data-stu-id="eb9db-192">Translation</span></span>|
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
|<code>{ if expr then cexpr0 &#124;}</code>|<code>if expr then { cexpr0 } else binder.Zero()</code>|
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

<span data-ttu-id="eb9db-193">Dans le tableau précédent, `other-expr` décrit une expression qui ne figure pas dans le cas contraire dans la table.</span><span class="sxs-lookup"><span data-stu-id="eb9db-193">In the previous table, `other-expr` describes an expression that is not otherwise listed in the table.</span></span> <span data-ttu-id="eb9db-194">Une classe de générateur est inutile d’implémenter toutes les méthodes et de prendre en charge toutes les traductions répertoriées dans le tableau précédent.</span><span class="sxs-lookup"><span data-stu-id="eb9db-194">A builder class does not need to implement all of the methods and support all of the translations listed in the previous table.</span></span> <span data-ttu-id="eb9db-195">Ces constructions qui ne sont pas implémentées ne sont pas disponibles dans les expressions de calcul de ce type.</span><span class="sxs-lookup"><span data-stu-id="eb9db-195">Those constructs that are not implemented are not available in computation expressions of that type.</span></span> <span data-ttu-id="eb9db-196">Par exemple, si vous ne souhaitez pas prendre en charge la `use` mot clé dans les expressions de calcul, vous pouvez omettre la définition de `Use` dans votre classe de générateur de rapports.</span><span class="sxs-lookup"><span data-stu-id="eb9db-196">For example, if you do not want to support the `use` keyword in your computation expressions, you can omit the definition of `Use` in your builder class.</span></span>

<span data-ttu-id="eb9db-197">L’exemple de code suivant montre une expression de calcul qui encapsule un calcul telle qu’une série d’étapes qui peut être évaluée une seule étape à la fois.</span><span class="sxs-lookup"><span data-stu-id="eb9db-197">The following code example shows a computation expression that encapsulates a computation as a series of steps that can be evaluated one step at a time.</span></span> <span data-ttu-id="eb9db-198">Un type d’union, de différencier `OkOrException`, encode l’état d’erreur de l’expression, telle qu’évaluée jusqu'à présent.</span><span class="sxs-lookup"><span data-stu-id="eb9db-198">A discriminated union type, `OkOrException`, encodes the error state of the expression as evaluated so far.</span></span> <span data-ttu-id="eb9db-199">Ce code illustre plusieurs modèles classiques que vous pouvez utiliser dans vos expressions de calcul, telles que des implémentations de réutilisable de certaines des méthodes de générateur de rapports.</span><span class="sxs-lookup"><span data-stu-id="eb9db-199">This code demonstrates several typical patterns that you can use in your computation expressions, such as boilerplate implementations of some of the builder methods.</span></span>

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

<span data-ttu-id="eb9db-200">Une expression de calcul a un type sous-jacent, ce qui retourne l’expression.</span><span class="sxs-lookup"><span data-stu-id="eb9db-200">A computation expression has an underlying type, which the expression returns.</span></span> <span data-ttu-id="eb9db-201">Le type sous-jacent peut représenter un résultat du calcul ou un calcul retardé qui peut être effectué, ou elle peut fournir un moyen pour effectuer une itération dans un type de collection.</span><span class="sxs-lookup"><span data-stu-id="eb9db-201">The underlying type may represent a computed result or a delayed computation that can be performed, or it may provide a way to iterate through some type of collection.</span></span> <span data-ttu-id="eb9db-202">Dans l’exemple précédent, le type sous-jacent a été **finalement**.</span><span class="sxs-lookup"><span data-stu-id="eb9db-202">In the previous example, the underlying type was **Eventually**.</span></span> <span data-ttu-id="eb9db-203">Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb9db-203">For a sequence expression, the underlying type is <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb9db-204">Pour une expression de requête, le type sous-jacent est <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb9db-204">For a query expression, the underlying type is <xref:System.Linq.IQueryable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="eb9db-205">Pour un flux de travail asynchrone, le type sous-jacent est [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span><span class="sxs-lookup"><span data-stu-id="eb9db-205">For an asynchronous workflow, the underlying type is [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7).</span></span> <span data-ttu-id="eb9db-206">Le `Async` objet représente le travail à effectuer pour calculer le résultat.</span><span class="sxs-lookup"><span data-stu-id="eb9db-206">The `Async` object represents the work to be performed to compute the result.</span></span> <span data-ttu-id="eb9db-207">Par exemple, vous appelez [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pour effectuer un calcul et de retourner le résultat.</span><span class="sxs-lookup"><span data-stu-id="eb9db-207">For example, you call [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) to execute a computation and return the result.</span></span>

## <a name="custom-operations"></a><span data-ttu-id="eb9db-208">Opérations personnalisées</span><span class="sxs-lookup"><span data-stu-id="eb9db-208">Custom Operations</span></span>

<span data-ttu-id="eb9db-209">Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée en tant qu’opérateur dans une expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-209">You can define a custom operation on a computation expression and use a custom operation as an operator in a computation expression.</span></span> <span data-ttu-id="eb9db-210">Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête.</span><span class="sxs-lookup"><span data-stu-id="eb9db-210">For example, you can include a query operator in a query expression.</span></span> <span data-ttu-id="eb9db-211">Lorsque vous définissez une opération personnalisée, vous devez définir le rendement et les méthodes dans l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-211">When you define a custom operation, you must define the Yield and For methods in the computation expression.</span></span> <span data-ttu-id="eb9db-212">Pour définir une opération personnalisée, placez-le dans une classe de générateur pour l’expression de calcul, puis appliquer le [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span><span class="sxs-lookup"><span data-stu-id="eb9db-212">To define a custom operation, put it in a builder class for the computation expression, and then apply the [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19).</span></span> <span data-ttu-id="eb9db-213">Cet attribut prend une chaîne en tant qu’argument, qui est le nom à utiliser dans une opération personnalisée.</span><span class="sxs-lookup"><span data-stu-id="eb9db-213">This attribute takes a string as an argument, which is the name to be used in a custom operation.</span></span> <span data-ttu-id="eb9db-214">Ce nom est fourni dans la portée au début de l’accolade ouvrante de l’expression de calcul.</span><span class="sxs-lookup"><span data-stu-id="eb9db-214">This name comes into scope at the start of the opening curly brace of the computation expression.</span></span> <span data-ttu-id="eb9db-215">Par conséquent, vous ne devez pas utiliser des identificateurs qui ont le même nom qu’une opération personnalisée dans ce bloc.</span><span class="sxs-lookup"><span data-stu-id="eb9db-215">Therefore, you shouldn’t use identifiers that have the same name as a custom operation in this block.</span></span> <span data-ttu-id="eb9db-216">Par exemple, évitez l’utilisation des identificateurs comme `all` ou `last` dans les expressions de requête.</span><span class="sxs-lookup"><span data-stu-id="eb9db-216">For example, avoid the use of identifiers such as `all` or `last` in query expressions.</span></span>

### <a name="extending-existing-builders-with-new-custom-operations"></a><span data-ttu-id="eb9db-217">Extension des générateurs existants avec les nouvelles opérations personnalisé</span><span class="sxs-lookup"><span data-stu-id="eb9db-217">Extending existing Builders with new Custom Operations</span></span>

<span data-ttu-id="eb9db-218">Si vous avez déjà une classe de générateur, ses opérations personnalisées peuvent être étendues d’en dehors de cette classe de générateur de rapports.</span><span class="sxs-lookup"><span data-stu-id="eb9db-218">If you already have a builder class, its custom operations can be extended from outside of this builder class.</span></span> <span data-ttu-id="eb9db-219">Les extensions doivent être déclarées dans des modules.</span><span class="sxs-lookup"><span data-stu-id="eb9db-219">Extensions must be declared in modules.</span></span> <span data-ttu-id="eb9db-220">Espaces de noms ne peut pas contenir de membres d’extension à l’exception dans le même fichier et le même groupe de déclaration d’espace de noms dans lequel le type est défini.</span><span class="sxs-lookup"><span data-stu-id="eb9db-220">Namespaces cannot contain extension members except in the same file and the same namespace declaration group where the type is defined.</span></span>

<span data-ttu-id="eb9db-221">L’exemple suivant montre l’extension existants `Microsoft.FSharp.Linq.QueryBuilder` classe.</span><span class="sxs-lookup"><span data-stu-id="eb9db-221">The following example shows the extension of the existing `Microsoft.FSharp.Linq.QueryBuilder` class.</span></span>

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a><span data-ttu-id="eb9db-222">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eb9db-222">See also</span></span>

- [<span data-ttu-id="eb9db-223">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="eb9db-223">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="eb9db-224">Flux de travail asynchrones</span><span class="sxs-lookup"><span data-stu-id="eb9db-224">Asynchronous Workflows</span></span>](asynchronous-workflows.md)
- [<span data-ttu-id="eb9db-225">Séquences</span><span class="sxs-lookup"><span data-stu-id="eb9db-225">Sequences</span></span>](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [<span data-ttu-id="eb9db-226">Expressions de requête</span><span class="sxs-lookup"><span data-stu-id="eb9db-226">Query Expressions</span></span>](query-expressions.md)

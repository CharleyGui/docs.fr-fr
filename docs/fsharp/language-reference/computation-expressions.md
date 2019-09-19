---
title: Expressions de calcul
description: Découvrez comment créer une syntaxe pratique pour écrire des calculs dans F# qui peut être séquencé et combiné à l’aide de constructions et de liaisons de workflow de contrôle.
ms.date: 03/15/2019
ms.openlocfilehash: 9222be5a585914761d3001d6649b196030eec05e
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083053"
---
# <a name="computation-expressions"></a>Expressions de calcul

Les expressions de calcul F# dans fournissent une syntaxe pratique pour écrire des calculs qui peuvent être séquencés et combinés à l’aide de constructions et de liaisons de workflow de contrôle. Selon le type d’expression de calcul, ils peuvent être considérés comme un moyen d’exprimer les monades, monoids, les transformateurs Monad et les functors applicative. Toutefois, contrairement à d’autres langages (comme la *notation do-notation* dans Haskell), ils ne sont pas liés à une abstraction unique et ne s’appuient pas sur des macros ou d’autres formes de surprogrammation pour accomplir une syntaxe pratique et contextuel.

## <a name="overview"></a>Présentation

Les calculs peuvent prendre plusieurs formes. La forme la plus courante de calcul est l’exécution à thread unique, qui est facile à comprendre et à modifier. Toutefois, toutes les formes de calcul ne sont pas aussi simples qu’une exécution monothread. Voici quelques exemples :

- Calculs non déterministes
- Calculs asynchrones
- Calculs avec effet
- Calculs de la génération de calcul

Plus généralement, il existe des calculs *contextuels* que vous devez effectuer dans certaines parties d’une application. L’écriture de code contextuel peut être difficile, car il est facile de « fuite » les calculs en dehors d’un contexte donné sans abstractions pour vous empêcher de le faire. Ces abstractions sont souvent difficiles à écrire par vous-même, ce F# qui est la raison pour laquelle il est possible de faire appel à des **expressions de calcul**.

Les expressions de calcul offrent une syntaxe uniforme et un modèle d’abstraction pour l’encodage des calculs contextuels.

Chaque expression de calcul est sauvegardée par un type de *Générateur* . Le type de générateur définit les opérations qui sont disponibles pour l’expression de calcul. Consultez [création d’un nouveau type d’expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisée.

### <a name="syntax-overview"></a>Vue d’ensemble de la syntaxe

Toutes les expressions de calcul se présentent sous la forme suivante :

```fsharp
builder-expr { cexper }
```

où `builder-expr` est le nom d’un type de générateur qui définit l’expression de calcul, `cexper` et est le corps de l’expression de l’expression de calcul. Par exemple, `async` le code d’expression de calcul peut se présenter comme suit :

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Une syntaxe supplémentaire spéciale est disponible dans une expression de calcul, comme illustré dans l’exemple précédent. Les formules de calcul sont possibles avec les expressions de calcul suivantes :

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Chacun de ces mots clés et d’autres F# Mots clés standard sont uniquement disponibles dans une expression de calcul s’ils ont été définis dans le type de générateur de stockage. La seule exception à cela est `match!`, qui est elle-même la syntaxe du sucre `let!` pour l’utilisation de suivi d’une correspondance de modèle sur le résultat.

Le type de générateur est un objet qui définit des méthodes spéciales qui régissent la façon dont les fragments de l’expression de calcul sont combinés. autrement dit, ses méthodes contrôlent le comportement de l’expression de calcul. Une autre façon de décrire une classe de générateur est de vous permettre de personnaliser l’opération de nombreuses F# constructions, telles que des boucles et des liaisons.

### `let!`

Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom :

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Si vous liez l’appel à une expression de calcul avec `let`, vous n’obtiendrez pas le résultat de l’expression de calcul. Au lieu de cela, vous aurez lié la valeur de l’appel non *réalisé* à cette expression de calcul. Utilisez `let!` pour établir une liaison avec le résultat.

`let!`est défini par le `Bind(x, f)` membre sur le type de générateur.

### `do!`

Le `do!` mot clé est utilisé pour appeler une expression de calcul qui `unit`retourne un type semblable à (défini `Zero` par le membre sur le générateur) :

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pour le [flux de travail asynchrone](asynchronous-workflows.md), ce `Async<unit>`type est. Pour les autres expressions de calcul, le type est susceptible d' `CExpType<unit>`être.

`do!`est défini par le `Bind(x, f)` membre sur le type de générateur, `f` où produit `unit`un.

### `yield`

Le `yield` mot clé est utilisé pour retourner une valeur à partir de l’expression de calcul afin qu’il puisse <xref:System.Collections.Generic.IEnumerable%601>être consommé en tant que :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Comme avec le [mot clé yield C#dans ](../../csharp/language-reference/keywords/yield.md), chaque élément de l’expression de calcul est renvoyé à mesure qu’il est itéré.

`yield`est défini par le `Yield(x)` membre sur le type de générateur, `x` où est l’élément à retourner.

### `yield!`

Le `yield!` mot clé sert à aplatir une collection de valeurs à partir d’une expression de calcul :

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

En cas d’évaluation, l’expression de calcul `yield!` appelée par aura ses éléments retournés un par un, ce qui a pour effet d’aplatir le résultat.

`yield!`est défini par le `YieldFrom(x)` membre sur le type de générateur, `x` où est une collection de valeurs.

### `return`

Le `return` mot clé encapsule une valeur dans le type correspondant à l’expression de calcul. Outre les expressions de calcul utilisant `yield`, il est utilisé pour « terminer » une expression de calcul :

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`est défini par le `Return(x)` membre sur le type de générateur, `x` où est l’élément à inclure dans un wrapper.

### `return!`

Le `return!` mot clé réalise la valeur d’une expression de calcul et encapsule le résultat dans le type correspondant à l’expression de calcul :

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`est défini par le `ReturnFrom(x)` membre sur le type de générateur, `x` où est une autre expression de calcul.

### `match!`

À partir F# de 4,5, `match!` le mot clé vous permet d’incorporer un appel à une autre expression de calcul et une correspondance de modèle sur son résultat :

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Lors de l’appel d’une expression `match!`de calcul avec, le résultat de l’appel est `let!`similaire à. Cela est souvent utilisé lors de l’appel d’une expression de calcul où le résultat est un [facultatif](options.md).

## <a name="built-in-computation-expressions"></a>Expressions de calcul intégrées

La F# bibliothèque principale définit trois expressions de calcul intégrées : Les [expressions de séquence](sequences.md), les flux de [travail asynchrones](asynchronous-workflows.md)et les [expressions de requête](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Création d’un nouveau type d’expression de calcul

Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de générateur et en définissant certaines méthodes spéciales sur la classe. La classe de générateur peut éventuellement définir les méthodes comme indiqué dans le tableau suivant.

Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de générateur de flux de travail.

|**Méthode**|**Signature (s) classique (s)**|**Description**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Appelé pour `let!` et `do!` dans les expressions de calcul.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Encapsule une expression de calcul en tant que fonction.|
|`Return`|`'T -> M<'T>`|Appelé pour `return` dans les expressions de calcul.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Appelé pour `return!` dans les expressions de calcul.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Exécute une expression de calcul.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Appelé pour le séquencement dans les expressions de calcul.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Appelé pour `for...do` les expressions dans les expressions de calcul.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Appelé pour `try...finally` les expressions dans les expressions de calcul.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Appelé pour `try...with` les expressions dans les expressions de calcul.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Appelé pour `use` les liaisons dans les expressions de calcul.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Appelé pour `while...do` les expressions dans les expressions de calcul.|
|`Yield`|`'T -> M<'T>`|Appelé pour `yield` les expressions dans les expressions de calcul.|
|`YieldFrom`|`M<'T> -> M<'T>`|Appelé pour `yield!` les expressions dans les expressions de calcul.|
|`Zero`|`unit -> M<'T>`|Appelé pour les `else` branches vides `if...then` d’expressions dans les expressions de calcul.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Indique que l’expression de calcul est passée au `Run` membre en tant que quotation. Il convertit toutes les instances d’un calcul en un devis.|

La plupart des méthodes d’une classe de générateur utilisent et retournent une `M<'T>` construction, qui est généralement un type défini séparément qui caractérise le type de calculs combinés, par `Async<'T>` exemple pour les flux de travail `Seq<'T>` asynchrones et pour les workflows de séquence. Les signatures de ces méthodes leur permettent d’être combinées et imbriquées les unes avec les autres, afin que l’objet de flux de travail retourné à partir d’une construction puisse être passé au suivant. Lorsqu’il analyse une expression de calcul, le compilateur convertit l’expression en une série d’appels de fonction imbriqués à l’aide des méthodes du tableau précédent et du code de l’expression de calcul.

L’expression imbriquée se présente sous la forme suivante :

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Dans le code ci-dessus, les `Run` appels `Delay` à et sont omis s’ils ne sont pas définis dans la classe de générateur d’expressions de calcul. Le corps de l’expression de calcul, ici désigné par `{| cexpr |}`, est traduit en appels impliquant les méthodes de la classe de générateur par les traductions décrites dans le tableau suivant. L’expression `{| cexpr |}` de calcul est définie de manière récursive en fonction de ces traductions `expr` , où F# est une `cexpr` expression et est une expression de calcul.

|Expression|Traduction|
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

Dans le tableau précédent, `other-expr` décrit une expression qui ne figure pas dans le tableau. Une classe de générateur n’a pas besoin d’implémenter toutes les méthodes et de prendre en charge toutes les traductions listées dans le tableau précédent. Les constructions qui ne sont pas implémentées ne sont pas disponibles dans les expressions de calcul de ce type. Par exemple, si vous ne souhaitez pas prendre en charge `use` le mot clé dans vos expressions de calcul, vous pouvez omettre la `Use` définition de dans votre classe de générateur.

L’exemple de code suivant montre une expression de calcul qui encapsule un calcul sous la forme d’une série d’étapes qui peuvent être évaluées une par une à la fois. Un type d’union discriminée `OkOrException`,, encode l’état d’erreur de l’expression comme évalué jusqu’à présent. Ce code illustre plusieurs modèles typiques que vous pouvez utiliser dans vos expressions de calcul, telles que les implémentations réutilisables de certaines méthodes de générateur.

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

Une expression de calcul a un type sous-jacent, que l’expression retourne. Le type sous-jacent peut représenter un résultat calculé ou un calcul retardé qui peut être effectué, ou il peut fournir un moyen d’itérer au sein d’un type de collection. Dans l’exemple précédent, le type sous-jacent était **finalement**. Pour une expression de séquence, le type sous <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>-jacent est. Pour une expression de requête, le type sous <xref:System.Linq.IQueryable?displayProperty=nameWithType>-jacent est. Pour un flux de travail asynchrone, le type [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)sous-jacent est. L' `Async` objet représente le travail à effectuer pour calculer le résultat. Par exemple, vous appelez [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pour exécuter un calcul et retourner le résultat.

## <a name="custom-operations"></a>Opérations personnalisées

Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée comme opérateur dans une expression de calcul. Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête. Lorsque vous définissez une opération personnalisée, vous devez définir les méthodes yield et for dans l’expression de calcul. Pour définir une opération personnalisée, placez-la dans une classe de générateur pour l’expression de calcul, puis appliquez [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Cet attribut prend une chaîne en tant qu’argument, qui est le nom à utiliser dans une opération personnalisée. Ce nom est placé dans la portée au début de l’accolade ouvrante de l’expression de calcul. Par conséquent, vous ne devez pas utiliser d’identificateurs portant le même nom qu’une opération personnalisée dans ce bloc. Par exemple, évitez d’utiliser des identificateurs tels que `all` ou `last` dans les expressions de requête.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Extension des générateurs existants à l’aide de nouvelles opérations personnalisées

Si vous disposez déjà d’une classe de générateur, ses opérations personnalisées peuvent être étendues à partir de l’extérieur de cette classe de générateur. Les extensions doivent être déclarées dans des modules. Les espaces de noms ne peuvent pas contenir de membres d’extension, sauf dans le même fichier et dans le même groupe de déclaration d’espace de noms où le type est défini.

L’exemple suivant montre l’extension de la classe `Microsoft.FSharp.Linq.QueryBuilder` existante.

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member __.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence du langage F#](index.md)
- [Flux de travail asynchrones](asynchronous-workflows.md)
- [Séquences](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Expressions de requête](query-expressions.md)

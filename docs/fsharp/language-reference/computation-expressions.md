---
title: Expressions de calcul
description: 'Découvrez comment créer une syntaxe pratique pour écrire des calculs en F # qui peut être séquencé et combiné à l’aide de constructions et de liaisons de workflow de contrôle.'
ms.date: 08/15/2020
f1_keywords:
- let!_FS
ms.openlocfilehash: bc3842b6f1075d68d1997e78c8bd8485731fca52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705304"
---
# <a name="computation-expressions"></a>Expressions de calcul

Les expressions de calcul en F # fournissent une syntaxe pratique pour écrire des calculs qui peuvent être séquencés et combinés à l’aide de constructions et de liaisons de workflow de contrôle. Selon le type d’expression de calcul, ils peuvent être considérés comme un moyen d’exprimer les monades, monoids, les transformateurs Monad et les functors applicative. Toutefois, contrairement à d’autres langages (comme la *notation do-notation* dans Haskell), ils ne sont pas liés à une abstraction unique et ne s’appuient pas sur des macros ou d’autres formes de surprogrammation pour accomplir une syntaxe pratique et contextuel.

## <a name="overview"></a>Vue d’ensemble

Les calculs peuvent prendre plusieurs formes. La forme la plus courante de calcul est l’exécution à thread unique, qui est facile à comprendre et à modifier. Toutefois, toutes les formes de calcul ne sont pas aussi simples qu’une exécution monothread. Voici quelques exemples :

- Calculs non déterministes
- Calculs asynchrones
- Calculs avec effet
- Calculs de la génération de calcul

Plus généralement, il existe des calculs *contextuels* que vous devez effectuer dans certaines parties d’une application. L’écriture de code contextuel peut être difficile, car il est facile de « fuite » les calculs en dehors d’un contexte donné sans abstractions pour vous empêcher de le faire. Ces abstractions sont souvent difficiles à écrire par vous-même, c’est pourquoi F # dispose d’une méthode généralisée pour faire appel à des **expressions de calcul**.

Les expressions de calcul offrent une syntaxe uniforme et un modèle d’abstraction pour l’encodage des calculs contextuels.

Chaque expression de calcul est sauvegardée par un type de *Générateur* . Le type de générateur définit les opérations qui sont disponibles pour l’expression de calcul. Consultez [création d’un nouveau type d’expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisée.

### <a name="syntax-overview"></a>Vue d’ensemble de la syntaxe

Toutes les expressions de calcul se présentent sous la forme suivante :

```fsharp
builder-expr { cexper }
```

où `builder-expr` est le nom d’un type de générateur qui définit l’expression de calcul, et `cexper` est le corps de l’expression de l’expression de calcul. Par exemple, `async` le code d’expression de calcul peut se présenter comme suit :

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

Chacun de ces mots clés, ainsi que d’autres mots clés F # standard, sont disponibles uniquement dans une expression de calcul s’ils ont été définis dans le type de générateur de stockage. La seule exception à cela est `match!` , qui est elle-même la syntaxe du sucre pour l’utilisation de `let!` suivi d’une correspondance de modèle sur le résultat.

Le type de générateur est un objet qui définit des méthodes spéciales qui régissent la façon dont les fragments de l’expression de calcul sont combinés. autrement dit, ses méthodes contrôlent le comportement de l’expression de calcul. Une autre façon de décrire une classe de générateur est de vous permettre de personnaliser l’opération de nombreuses constructions F #, telles que des boucles et des liaisons.

### `let!`

Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom :

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Si vous liez l’appel à une expression de calcul avec `let` , vous n’obtiendrez pas le résultat de l’expression de calcul. Au lieu de cela, vous aurez lié la valeur de l’appel non *réalisé* à cette expression de calcul. Utilisez `let!` pour établir une liaison avec le résultat.

`let!` est défini par le `Bind(x, f)` membre sur le type de générateur.

### `do!`

Le `do!` mot clé est utilisé pour appeler une expression de calcul qui retourne un `unit` type semblable à (défini par le `Zero` membre sur le générateur) :

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pour le [flux de travail asynchrone](asynchronous-workflows.md), ce type est `Async<unit>` . Pour les autres expressions de calcul, le type est susceptible d’être `CExpType<unit>` .

`do!` est défini par le `Bind(x, f)` membre sur le type de générateur, où `f` produit un `unit` .

### `yield`

Le `yield` mot clé est utilisé pour retourner une valeur à partir de l’expression de calcul afin qu’il puisse être consommé en tant que <xref:System.Collections.Generic.IEnumerable%601> :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Dans la plupart des cas, il peut être omis par les appelants. La méthode la plus courante pour omettre `yield` est avec l' `->` opérateur :

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Pour les expressions plus complexes qui peuvent générer de nombreuses valeurs différentes, et peut-être de manière conditionnelle, il suffit d’omettre le mot clé :

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

Comme avec le [mot clé yield en C#](../../csharp/language-reference/keywords/yield.md), chaque élément de l’expression de calcul est renvoyé à mesure qu’il est itéré.

`yield` est défini par le `Yield(x)` membre sur le type de générateur, où `x` est l’élément à retourner.

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

En cas d’évaluation, l’expression de calcul appelée par `yield!` aura ses éléments retournés un par un, ce qui a pour effet d’aplatir le résultat.

`yield!` est défini par le `YieldFrom(x)` membre sur le type de générateur, où `x` est une collection de valeurs.

Contrairement `yield` `yield!` à, doit être spécifié explicitement. Son comportement n’est pas implicite dans les expressions de calcul.

### `return`

Le `return` mot clé encapsule une valeur dans le type correspondant à l’expression de calcul. Outre les expressions de calcul utilisant `yield` , il est utilisé pour « terminer » une expression de calcul :

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` est défini par le `Return(x)` membre sur le type de générateur, où `x` est l’élément à inclure dans un wrapper.

### `return!`

Le `return!` mot clé réalise la valeur d’une expression de calcul et encapsule le résultat dans le type correspondant à l’expression de calcul :

```fsharp
let req = // 'req' is of type 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` est défini par le `ReturnFrom(x)` membre sur le type de générateur, où `x` est une autre expression de calcul.

### `match!`

Le `match!` mot clé vous permet d’incorporer un appel à une autre expression de calcul et une correspondance de modèle sur son résultat :

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Lors de l’appel d’une expression de calcul avec `match!` , le résultat de l’appel est similaire à `let!` . Cela est souvent utilisé lors de l’appel d’une expression de calcul où le résultat est un [facultatif](options.md).

## <a name="built-in-computation-expressions"></a>Expressions de calcul intégrées

La bibliothèque principale F # définit trois expressions de calcul intégrées : les [expressions de séquence](sequences.md), les [flux de travail asynchrones](asynchronous-workflows.md)et les [expressions de requête](query-expressions.md).

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
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Appelé pour les `for...do` expressions dans les expressions de calcul.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Appelé pour les `try...finally` expressions dans les expressions de calcul.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Appelé pour les `try...with` expressions dans les expressions de calcul.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Appelé pour les `use` liaisons dans les expressions de calcul.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Appelé pour les `while...do` expressions dans les expressions de calcul.|
|`Yield`|`'T -> M<'T>`|Appelé pour les `yield` expressions dans les expressions de calcul.|
|`YieldFrom`|`M<'T> -> M<'T>`|Appelé pour les `yield!` expressions dans les expressions de calcul.|
|`Zero`|`unit -> M<'T>`|Appelé pour les `else` branches vides d' `if...then` expressions dans les expressions de calcul.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Indique que l’expression de calcul est passée au `Run` membre en tant que quotation. Il convertit toutes les instances d’un calcul en un devis.|

La plupart des méthodes d’une classe de générateur utilisent et retournent une `M<'T>` construction, qui est généralement un type défini séparément qui caractérise le type de calculs combinés, par exemple, `Async<'T>` pour les flux de travail asynchrones et les `Seq<'T>` workflows de séquence. Les signatures de ces méthodes leur permettent d’être combinées et imbriquées les unes avec les autres, afin que l’objet de flux de travail retourné à partir d’une construction puisse être passé au suivant. Lorsqu’il analyse une expression de calcul, le compilateur convertit l’expression en une série d’appels de fonction imbriqués à l’aide des méthodes du tableau précédent et du code de l’expression de calcul.

L’expression imbriquée se présente sous la forme suivante :

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Dans le code ci-dessus, les appels à `Run` et `Delay` sont omis s’ils ne sont pas définis dans la classe de générateur d’expressions de calcul. Le corps de l’expression de calcul, ici désigné par `{| cexpr |}` , est traduit en appels impliquant les méthodes de la classe de générateur par les traductions décrites dans le tableau suivant. L’expression de calcul `{| cexpr |}` est définie de manière récursive en fonction de ces traductions `expr` , où est une expression F # et `cexpr` est une expression de calcul.

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

Dans le tableau précédent, `other-expr` décrit une expression qui ne figure pas dans le tableau. Une classe de générateur n’a pas besoin d’implémenter toutes les méthodes et de prendre en charge toutes les traductions listées dans le tableau précédent. Les constructions qui ne sont pas implémentées ne sont pas disponibles dans les expressions de calcul de ce type. Par exemple, si vous ne souhaitez pas prendre en charge le `use` mot clé dans vos expressions de calcul, vous pouvez omettre la définition de `Use` dans votre classe de générateur.

L’exemple de code suivant montre une expression de calcul qui encapsule un calcul sous la forme d’une série d’étapes qui peuvent être évaluées une par une à la fois. Un type d’union discriminée, `OkOrException` , encode l’état d’erreur de l’expression comme évalué jusqu’à présent. Ce code illustre plusieurs modèles typiques que vous pouvez utiliser dans vos expressions de calcul, telles que les implémentations réutilisables de certaines méthodes de générateur.

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

Une expression de calcul a un type sous-jacent, que l’expression retourne. Le type sous-jacent peut représenter un résultat calculé ou un calcul retardé qui peut être effectué, ou il peut fournir un moyen d’itérer au sein d’un type de collection. Dans l’exemple précédent, le type sous-jacent était **finalement**. Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> . Pour une expression de requête, le type sous-jacent est <xref:System.Linq.IQueryable?displayProperty=nameWithType> . Pour un flux de travail asynchrone, le type sous-jacent est [`Async`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync-1.html) . L' `Async` objet représente le travail à effectuer pour calculer le résultat. Par exemple, vous appelez [`Async.RunSynchronously`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpasync.html#RunSynchronously) pour exécuter un calcul et retourner le résultat.

## <a name="custom-operations"></a>Opérations personnalisées

Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée comme opérateur dans une expression de calcul. Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête. Lorsque vous définissez une opération personnalisée, vous devez définir les méthodes yield et for dans l’expression de calcul. Pour définir une opération personnalisée, placez-la dans une classe de générateur pour l’expression de calcul, puis appliquez [`CustomOperationAttribute`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-customoperationattribute.html) . Cet attribut prend une chaîne en tant qu’argument, qui est le nom à utiliser dans une opération personnalisée. Ce nom est placé dans la portée au début de l’accolade ouvrante de l’expression de calcul. Par conséquent, vous ne devez pas utiliser d’identificateurs portant le même nom qu’une opération personnalisée dans ce bloc. Par exemple, évitez d’utiliser des identificateurs tels que `all` ou `last` dans les expressions de requête.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Extension des générateurs existants à l’aide de nouvelles opérations personnalisées

Si vous disposez déjà d’une classe de générateur, ses opérations personnalisées peuvent être étendues à partir de l’extérieur de cette classe de générateur. Les extensions doivent être déclarées dans des modules. Les espaces de noms ne peuvent pas contenir de membres d’extension, sauf dans le même fichier et dans le même groupe de déclaration d’espace de noms où le type est défini.

L’exemple suivant montre l’extension de la `FSharp.Linq.QueryBuilder` classe existante.

```fsharp
type FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur le langage F #](index.md)
- [Workflows asynchrones](asynchronous-workflows.md)
- [Séquences](sequences.md)
- [Expressions de requête](query-expressions.md)

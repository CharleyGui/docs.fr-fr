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
# <a name="computation-expressions"></a>Expressions de calcul

Expressions de calcul en F# fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de liaisons et constructions de flux de contrôle. En fonction du type d’expression de calcul, elles peuvent être considérés comme un moyen d’exprimer monades, monoids, monad transformateurs et les functors applicative. Cependant, contrairement à d’autres langages (tels que *-notation* de Haskell), ils ne sont pas liées à une simple abstraction et que vous ne comptez pas sur les macros ou d’autres formes de métaprogrammation pour accomplir une syntaxe pratique et sensible au contexte.

## <a name="overview"></a>Vue d'ensemble

Les calculs peuvent prendre différentes formes. La forme la plus courante de calcul est une exécution monothread, qui est facile à comprendre et à modifier. Toutefois, pas toutes les formes de calcul sont aussi simples que d’une exécution monothread. Voici quelques exemples :

* Calculs non déterministes
* Calculs asynchrones
* Calculs effectful
* Calculs générative

En règle générale, il existe *contextuelle* calculs que vous devez effectuer dans certaines parties d’une application. Écrire du code contextuelle peut être difficile, car il est facile de calculs de « fuite » en dehors d’un contexte donné sans abstractions pour vous éviter de le faire. Ces abstractions sont souvent difficile à écrire vous-même, ce qui explique pourquoi F# a une méthode généralisée pour faire ce qu’on appelle **expressions de calcul**.

Expressions de calcul offrent un modèle uniforme de syntaxe et d’abstraction pour l’encodage des calculs contextuelles.

Chaque expression de calcul est soutenue par un *Générateur* type. Le type de générateur de rapports définit les opérations qui sont disponibles pour l’expression de calcul. Consultez [création d’un nouveau Type d’Expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisé.

### <a name="syntax-overview"></a>Vue d’ensemble de la syntaxe

Toutes les expressions de calcul ont la forme suivante :

```
builder-expr { cexper }
```

où `builder-expr` est le nom d’un type de générateur qui définit l’expression de calcul, et `cexper` est le corps de l’expression de l’expression de calcul. Par exemple, `async` code d’expression de calcul peut ressembler à ceci :

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Une syntaxe spéciale, supplémentaire est disponible au sein d’une expression de calcul, comme indiqué dans l’exemple précédent. Les formes d’expression suivantes sont possibles avec les expressions de calcul :

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Chacune de ces mots clés et autres standard F# mots clés sont uniquement disponibles dans une expression de calcul s’ils ont été définis dans le type de générateur de rapports de sauvegarde. La seule exception à cela est `match!`, qui est lui-même liant syntaxique pour l’utilisation de `let!` suivie d’une correspondance de modèle sur le résultat.

Le type de générateur est un objet qui définit des méthodes spéciales qui régissent la manière de que combiner les fragments de l’expression de calcul ; Autrement dit, ses méthodes contrôlent le comportement de l’expression de calcul. Un autre moyen de décrire une classe de générateur est à dire qu’il vous permet de personnaliser l’opération de nombreuses F# construit, comme des boucles et des liaisons.

### `let!`

Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom :

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Si vous liez l’appel à une expression de calcul avec `let`, vous n’obtiendrez pas le résultat de l’expression de calcul. Au lieu de cela, vous serez l’avez liée la valeur de la *non réalisés* l’appel à cette expression de calcul. Utilisez `let!` à lier au résultat.

`let!` est défini par le `Bind(x, f)` membre sur le type de générateur de rapports.

### `do!`

Le `do!` mot clé est pour l’appel d’une expression de calcul qui retourne un `unit`-comme type (défini par le `Zero` membre sur le générateur) :

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pour le [async workflow](asynchronous-workflows.md), ce type est `Async<unit>`. Pour les autres expressions de calcul, le type est susceptible d’être `CExpType<unit>`.

`do!` est défini par le `Bind(x, f)` membre sur le type de générateur de rapports, où `f` génère un `unit`.

### `yield`

Le `yield` mot clé est de retourner une valeur à partir de l’expression de calcul afin qu’il peut être utilisé comme un <xref:System.Collections.Generic.IEnumerable%601>:

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Comme avec la [yield mot clé dans C#](../../csharp/language-reference/keywords/yield.md), chaque élément dans l’expression de calcul est cédée car elle est itérée.

`yield` est défini par le `Yield(x)` membre sur le type de générateur de rapports, où `x` est l’élément à générer de nouveau.

### `yield!`

Le `yield!` mot clé est pour la mise à plat une collection de valeurs à partir d’une expression de calcul :

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

Lors de l’évaluation, l’expression de calcul appelées par `yield!` seront vous ses éléments a différé un par un, le résultat de mise à plat.

`yield!` est défini par le `YieldFrom(x)` membre sur le type de générateur de rapports, où `x` est une collection de valeurs.

### `return`

Le `return` mot clé encapsule une valeur dans le type correspondant à l’expression de calcul. Outre les expressions de calcul à l’aide de `yield`, il est utilisé pour une expression de calcul « terminé » :

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return` est défini par le `Return(x)` membre sur le type de générateur de rapports, où `x` est l’élément à encapsuler.

### `return!`

Le `return!` mot clé se rend compte de la valeur d’une expression de calcul et encapsule ce résultat dans le type correspondant à l’expression de calcul :

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!` est défini par le `ReturnFrom(x)` membre sur le type de générateur de rapports, où `x` est une autre expression de calcul.

### `match!`

En commençant par F# 4.5, le `match!` mot clé vous permet d’inline un appel à une autre correspondance d’expression et le modèle de calcul sur son résultat :

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Lors de l’appel d’une expression de calcul avec `match!`, elle réalisera le résultat de l’appel comme `let!`. Il est souvent utilisé lors de l’appel à une expression de calcul où le résultat est un [facultatif](options.md).

## <a name="built-in-computation-expressions"></a>Expressions de calcul intégré

Le F# bibliothèque principale définit trois expressions de calcul intégré : [Expressions de séquence](sequences.md), [flux de travail asynchrones](asynchronous-workflows.md), et [Expressions de requête](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Création d’un nouveau Type d’Expression de calcul

Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de générateur et en définissant certaines méthodes spéciales sur la classe. La classe de générateur peut éventuellement définir les méthodes comme indiqué dans le tableau suivant.

Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de générateur de flux de travail.

|**Méthode**|**Signatures typiques**|**Description**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Appelé pour `let!` et `do!` dans les expressions de calcul.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Encapsule une expression de calcul en tant que fonction.|
|`Return`|`'T -> M<'T>`|Appelé pour `return` dans les expressions de calcul.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Appelé pour `return!` dans les expressions de calcul.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Exécute une expression de calcul.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Appelée pour le séquencement dans les expressions de calcul.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Appelé pour `for...do` expressions dans les expressions de calcul.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Appelé pour `try...finally` expressions dans les expressions de calcul.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Appelé pour `try...with` expressions dans les expressions de calcul.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'U :> IDisposable`|Appelé pour `use` liaisons dans les expressions de calcul.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Appelé pour `while...do` expressions dans les expressions de calcul.|
|`Yield`|`'T -> M<'T>`|Appelé pour `yield` expressions dans les expressions de calcul.|
|`YieldFrom`|`M<'T> -> M<'T>`|Appelé pour `yield!` expressions dans les expressions de calcul.|
|`Zero`|`unit -> M<'T>`|Appelé pour vide `else` branches de `if...then` expressions dans les expressions de calcul.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Indique que l’expression de calcul est passée à la `Run` membre en tant que quotation. Il traduit toutes les instances d’un calcul dans une quotation.|

La plupart des méthodes dans une classe de générateur utilisent et retournent un `M<'T>` construct, qui est généralement un type défini séparément qui caractérise le genre des calculs combinés, par exemple, `Async<'T>` pour les flux de travail asynchrones et `Seq<'T>` pour les workflows de la séquence. Les signatures de ces méthodes activez-les être combinées et imbriquées avec les autres, afin que l’objet de flux de travail retourné d’une construction qui peut être passé à la suivante. Le compilateur, lorsqu’il analyse une expression de calcul, convertit l’expression en une série d’appels de fonction imbriquée en utilisant les méthodes dans le tableau précédent et le code dans l’expression de calcul.

L’expression imbriquée est au format suivant :

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Dans le code ci-dessus, les appels à `Run` et `Delay` sont omis s’ils ne sont pas définis dans la classe de générateur d’expression calcul. Le corps de l’expression de calcul, désignée ici comme `{| cexpr |}`, est convertie en appels impliquant les méthodes de la classe de générateur de rapports par les traductions décrites dans le tableau suivant. L’expression de calcul `{| cexpr |}` est définie de manière récursive en fonction de ces traductions où `expr` est un F# expression et `cexpr` est une expression de calcul.

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

Dans le tableau précédent, `other-expr` décrit une expression qui ne figure pas dans le cas contraire dans la table. Une classe de générateur est inutile d’implémenter toutes les méthodes et de prendre en charge toutes les traductions répertoriées dans le tableau précédent. Ces constructions qui ne sont pas implémentées ne sont pas disponibles dans les expressions de calcul de ce type. Par exemple, si vous ne souhaitez pas prendre en charge la `use` mot clé dans les expressions de calcul, vous pouvez omettre la définition de `Use` dans votre classe de générateur de rapports.

L’exemple de code suivant montre une expression de calcul qui encapsule un calcul telle qu’une série d’étapes qui peut être évaluée une seule étape à la fois. Un type d’union, de différencier `OkOrException`, encode l’état d’erreur de l’expression, telle qu’évaluée jusqu'à présent. Ce code illustre plusieurs modèles classiques que vous pouvez utiliser dans vos expressions de calcul, telles que des implémentations de réutilisable de certaines des méthodes de générateur de rapports.

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

Une expression de calcul a un type sous-jacent, ce qui retourne l’expression. Le type sous-jacent peut représenter un résultat du calcul ou un calcul retardé qui peut être effectué, ou elle peut fournir un moyen pour effectuer une itération dans un type de collection. Dans l’exemple précédent, le type sous-jacent a été **finalement**. Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pour une expression de requête, le type sous-jacent est <xref:System.Linq.IQueryable?displayProperty=nameWithType>. Pour un flux de travail asynchrone, le type sous-jacent est [ `Async` ](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7). Le `Async` objet représente le travail à effectuer pour calculer le résultat. Par exemple, vous appelez [ `Async.RunSynchronously` ](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) pour effectuer un calcul et de retourner le résultat.

## <a name="custom-operations"></a>Opérations personnalisées

Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée en tant qu’opérateur dans une expression de calcul. Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête. Lorsque vous définissez une opération personnalisée, vous devez définir le rendement et les méthodes dans l’expression de calcul. Pour définir une opération personnalisée, placez-le dans une classe de générateur pour l’expression de calcul, puis appliquer le [ `CustomOperationAttribute` ](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19). Cet attribut prend une chaîne en tant qu’argument, qui est le nom à utiliser dans une opération personnalisée. Ce nom est fourni dans la portée au début de l’accolade ouvrante de l’expression de calcul. Par conséquent, vous ne devez pas utiliser des identificateurs qui ont le même nom qu’une opération personnalisée dans ce bloc. Par exemple, évitez l’utilisation des identificateurs comme `all` ou `last` dans les expressions de requête.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Extension des générateurs existants avec les nouvelles opérations personnalisé

Si vous avez déjà une classe de générateur, ses opérations personnalisées peuvent être étendues d’en dehors de cette classe de générateur de rapports. Les extensions doivent être déclarées dans des modules. Espaces de noms ne peut pas contenir de membres d’extension à l’exception dans le même fichier et le même groupe de déclaration d’espace de noms dans lequel le type est défini.

L’exemple suivant montre l’extension existants `Microsoft.FSharp.Linq.QueryBuilder` classe.

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

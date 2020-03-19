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
# <a name="computation-expressions"></a>Expressions de calcul

Les expressions de calcul dans le Fmd fournissent une syntaxe pratique pour l’écriture de calculs qui peuvent être séquencés et combinés à l’aide de constructions et de liaisons de flux de contrôle. Selon le type d’expression de calcul, ils peuvent être considérés comme un moyen d’exprimer des monads, des monoids, des transformateurs monad et des functors applicatifs. Cependant, contrairement à d’autres langues (comme la notation de *haskell),* elles ne sont pas liées à une seule abstraction, et ne s’appuient pas sur des macros ou d’autres formes de métaprogrammation pour accomplir une syntaxe pratique et sensible au contexte.

## <a name="overview"></a>Vue d’ensemble

Les calculs peuvent prendre de nombreuses formes. La forme de calcul la plus courante est l’exécution à threads simples, qui est facile à comprendre et à modifier. Cependant, toutes les formes de calcul ne sont pas aussi simples que l’exécution à threads simples. Voici quelques exemples :

- Calculs non déterministes
- Calculs asynchrones
- Calculs effectieux
- Calculs génératifs

Plus généralement, il existe des calculs *contextuelles* que vous devez effectuer dans certaines parties d’une application. Écrire un code sensible au contexte peut être difficile, car il est facile de "fuite" de calculs en dehors d’un contexte donné sans abstractions pour vous empêcher de le faire. Ces abstractions sont souvent difficiles à écrire par vous-même, c’est pourquoi F a une façon généralisée de le faire appelé **expressions de calcul**.

Les expressions de calcul offrent un modèle uniforme de syntaxe et d’abstraction pour coder les calculs contextuelles.

Chaque expression de calcul est soutenue par un type *de constructeur.* Le type constructeur définit les opérations qui sont disponibles pour l’expression de calcul. Voir [Créer un nouveau type d’expression de calcul](computation-expressions.md#creating-a-new-type-of-computation-expression), qui montre comment créer une expression de calcul personnalisée.

### <a name="syntax-overview"></a>Vue d’ensemble de la syntaxe

Toutes les expressions de calcul ont la forme suivante :

```fsharp
builder-expr { cexper }
```

où `builder-expr` est le nom d’un type de constructeur `cexper` qui définit l’expression de calcul, et est le corps d’expression de l’expression de calcul. Par exemple, `async` le code d’expression de calcul peut ressembler à ceci :

```fsharp
let fetchAndDownload url =
    async {
        let! data = downloadData url

        let processedData = processData data

        return processedData
    }
```

Il existe une syntaxe spéciale et supplémentaire disponible dans une expression de calcul, comme le montre l’exemple précédent. Les formes d’expression suivantes sont possibles avec des expressions de calcul :

```fsharp
expr { let! ... }
expr { do! ... }
expr { yield ... }
expr { yield! ... }
expr { return ... }
expr { return! ... }
expr { match! ... }
```

Chacun de ces mots clés, et d’autres mots-clés F standard ne sont disponibles que dans une expression de calcul s’ils ont été définis dans le type de constructeur d’accompagnement. La seule exception `match!`à cela est , qui est `let!` lui-même sucre syntaxique pour l’utilisation de suivi d’un match de modèle sur le résultat.

Le type de constructeur est un objet qui définit des méthodes spéciales qui régissent la façon dont les fragments de l’expression de calcul sont combinés; c’est-à-dire que ses méthodes contrôlent le comportement de l’expression de calcul. Une autre façon de décrire une classe de constructeur est de dire qu’il vous permet de personnaliser le fonctionnement de nombreuses constructions de F, telles que des boucles et des fixations.

### `let!`

Le `let!` mot clé lie le résultat d’un appel à une autre expression de calcul à un nom:

```fsharp
let doThingsAsync url =
    async {
        let! data = getDataAsync url
        ...
    }
```

Si vous liez l’appel à `let`une expression de calcul avec, vous n’obtiendrez pas le résultat de l’expression de calcul. Au lieu de cela, vous aurez lié la valeur de l’appel *non réalisé* à cette expression de calcul. Utilisez `let!` pour lier au résultat.

`let!`est défini `Bind(x, f)` par le membre sur le type de constructeur.

### `do!`

Le `do!` mot clé est pour appeler une `unit`expression de calcul `Zero` qui renvoie un type-comme (défini par le membre sur le constructeur):

```fsharp
let doThingsAsync data url =
    async {
        do! submitData data url
        ...
    }
```

Pour le [flux de travail async](asynchronous-workflows.md), ce type est `Async<unit>`. Pour d’autres expressions de calcul, `CExpType<unit>`le type est susceptible d’être .

`do!`est défini `Bind(x, f)` par le membre sur `f` le `unit`type de constructeur, où produit un .

### `yield`

Le `yield` mot clé est pour le retour d’une valeur de <xref:System.Collections.Generic.IEnumerable%601>l’expression de calcul afin qu’il puisse être consommé comme un :

```fsharp
let squares =
    seq {
        for i in 1..10 do
            yield i * i
    }

for sq in squares do
    printfn "%d" sq
```

Dans la plupart des cas, il peut être omis par les appelants. La façon la plus `yield` courante `->` d’omettre est avec l’opérateur :

```fsharp
let squares =
    seq {
        for i in 1..10 -> i * i
    }

for sq in squares do
    printfn "%d" sq
```

Pour des expressions plus complexes qui pourraient donner beaucoup de valeurs différentes, et peut-être sous condition, simplement omettre le mot clé peut faire:

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

Comme avec le [mot clé de rendement dans C ,](../../csharp/language-reference/keywords/yield.md)chaque élément dans l’expression de calcul est retourné comme il est itéré.

`yield`est défini `Yield(x)` par le membre sur `x` le type de constructeur, où est l’élément à céder.

### `yield!`

Le `yield!` mot clé est pour aplatir une collection de valeurs à partir d’une expression de calcul:

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

Une fois évaluée, l’expression `yield!` de calcul appelée par verra ses éléments redélévés un par un, aplatissant le résultat.

`yield!`est défini `YieldFrom(x)` par le membre sur `x` le type de constructeur, où est une collection de valeurs.

Contrairement `yield` `yield!` à , doit être explicitement spécifié. Son comportement n’est pas implicite dans les expressions de calcul.

### `return`

Le `return` mot clé enveloppe une valeur dans le type correspondant à l’expression de calcul. Mis à part les `yield`expressions de calcul à l’aide , il est utilisé pour «compléter» une expression de calcul:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        let! data = fetch url
        return data
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return`est défini `Return(x)` par le membre sur `x` le type de constructeur, où est l’élément à envelopper.

### `return!`

Le `return!` mot clé réalise la valeur d’une expression de calcul et enveloppe qui résultent dans le type correspondant à l’expression de calcul:

```fsharp
let req = // 'req' is of type is 'Async<data>'
    async {
        return! fetch url
    }

// 'result' is of type 'data'
let result = Async.RunSynchronously req
```

`return!`est défini `ReturnFrom(x)` par le membre sur `x` le type de constructeur, où est une autre expression de calcul.

### `match!`

Le `match!` mot clé vous permet d’inlimiter un appel à une autre expression de calcul et de correspondance de modèle sur son résultat :

```fsharp
let doThingsAsync url =
    async {
        match! callService url with
        | Some data -> ...
        | None -> ...
    }
```

Lorsque vous appelez une `match!`expression de calcul avec , `let!`il se rendra compte du résultat de l’appel comme . Ceci est souvent utilisé lors de l’appel d’une expression de calcul lorsque le résultat est une [option](options.md).

## <a name="built-in-computation-expressions"></a>Expressions de calcul intégrées

La bibliothèque de base de F définit trois expressions de calcul intégrées : [Séquence Expressions](sequences.md), flux de [travail asynchrones](asynchronous-workflows.md)et [Expressions de requête](query-expressions.md).

## <a name="creating-a-new-type-of-computation-expression"></a>Création d’un nouveau type d’expression de calcul

Vous pouvez définir les caractéristiques de vos propres expressions de calcul en créant une classe de constructeur et en définissant certaines méthodes spéciales sur la classe. La classe de constructeur peut définir optionnellement les méthodes énumérées dans le tableau suivant.

Le tableau suivant décrit les méthodes qui peuvent être utilisées dans une classe de constructeur de flux de travail.

|**Méthode**|**Signature typique(s)**|**Description**|
|----|----|----|
|`Bind`|`M<'T> * ('T -> M<'U>) -> M<'U>`|Appelé `let!` et `do!` dans les expressions de calcul.|
|`Delay`|`(unit -> M<'T>) -> M<'T>`|Enveloppe une expression de calcul comme une fonction.|
|`Return`|`'T -> M<'T>`|Appelé `return` dans les expressions de calcul.|
|`ReturnFrom`|`M<'T> -> M<'T>`|Appelé `return!` dans les expressions de calcul.|
|`Run`|`M<'T> -> M<'T>` ou<br /><br />`M<'T> -> 'T`|Exécute une expression de calcul.|
|`Combine`|`M<'T> * M<'T> -> M<'T>` ou<br /><br />`M<unit> * M<'T> -> M<'T>`|Appelé au séquençage dans les expressions de calcul.|
|`For`|`seq<'T> * ('T -> M<'U>) -> M<'U>` ou<br /><br />`seq<'T> * ('T -> M<'U>) -> seq<M<'U>>`|Appelé `for...do` pour des expressions dans les expressions de calcul.|
|`TryFinally`|`M<'T> * (unit -> unit) -> M<'T>`|Appelé `try...finally` pour des expressions dans les expressions de calcul.|
|`TryWith`|`M<'T> * (exn -> M<'T>) -> M<'T>`|Appelé `try...with` pour des expressions dans les expressions de calcul.|
|`Using`|`'T * ('T -> M<'U>) -> M<'U> when 'T :> IDisposable`|Appelé `use` à des fixations dans les expressions de calcul.|
|`While`|`(unit -> bool) * M<'T> -> M<'T>`|Appelé `while...do` pour des expressions dans les expressions de calcul.|
|`Yield`|`'T -> M<'T>`|Appelé `yield` pour des expressions dans les expressions de calcul.|
|`YieldFrom`|`M<'T> -> M<'T>`|Appelé `yield!` pour des expressions dans les expressions de calcul.|
|`Zero`|`unit -> M<'T>`|Appelé pour `else` des `if...then` branches vides d’expressions dans les expressions de calcul.|
|`Quote`|`Quotations.Expr<'T> -> Quotations.Expr<'T>`|Indique que l’expression de calcul `Run` est transmise au membre comme citation. Il traduit tous les cas d’un calcul en une citation.|

Beaucoup de méthodes dans une classe `M<'T>` de constructeur utilisent et retournent une construction, qui est généralement un type défini `Async<'T>` séparément qui caractérise le type `Seq<'T>` de calculs combinés, par exemple, pour les flux de travail asynchrones et pour les flux de travail de séquence. Les signatures de ces méthodes leur permettent d’être combinés et imbriqués les uns avec les autres, de sorte que l’objet de flux de travail retourné d’une construction peut être passé à l’autre. Le compilateur, lorsqu’il analyse une expression de calcul, convertit l’expression en une série d’appels de fonction imbriqués en utilisant les méthodes dans le tableau précédent et le code dans l’expression de calcul.

L’expression imbriquée est de la forme suivante :

```fsharp
builder.Run(builder.Delay(fun () -> {| cexpr |}))
```

Dans le code ci-dessus, les appels vers et `Run` `Delay` sont omis s’ils ne sont pas définis dans la classe de constructeur d’expression de calcul. Le corps de l’expression de calcul, `{| cexpr |}`ici dénoté comme , est traduit en appels impliquant les méthodes de la classe de constructeur par les traductions décrites dans le tableau suivant. L’expression `{| cexpr |}` de calcul est définie de façon récursive selon ces traductions où `expr` se trouve une expression de F et `cexpr` est une expression de calcul.

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

Dans le tableau `other-expr` précédent, décrit une expression qui n’est pas autrement répertoriée dans le tableau. Une classe de constructeurs n’a pas besoin de mettre en œuvre toutes les méthodes et de soutenir toutes les traductions énumérées dans le tableau précédent. Les constructions qui ne sont pas mises en œuvre ne sont pas disponibles dans les expressions de calcul de ce type. Par exemple, si vous ne `use` voulez pas prendre en charge le mot clé `Use` dans vos expressions de calcul, vous pouvez omettre la définition de dans votre classe de constructeur.

L’exemple de code suivant montre une expression de calcul qui encapsule un calcul comme une série d’étapes qui peuvent être évaluées une étape à la fois. Un type d’union discriminé, `OkOrException`code l’état d’erreur de l’expression telle qu’évaluée jusqu’à présent. Ce code montre plusieurs modèles typiques que vous pouvez utiliser dans vos expressions de calcul, telles que les implémentations de plaques chauffantes de certaines des méthodes de constructeur.

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

Une expression de calcul a un type sous-jacent, que l’expression renvoie. Le type sous-jacent peut représenter un résultat calculé ou un calcul retardé qui peut être effectué, ou il peut fournir un moyen d’itérer par un certain type de collecte. Dans l’exemple précédent, le type sous-jacent a **finalement**été . Pour une expression de séquence, le type sous-jacent est <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Pour une expression de requête, <xref:System.Linq.IQueryable?displayProperty=nameWithType>le type sous-jacent est . Pour un flux de travail asynchrone, [`Async`](https://msdn.microsoft.com/library/03eb4d12-a01a-4565-a077-5e83f17cf6f7)le type sous-jacent est . L’objet `Async` représente l’œuvre à effectuer pour calculer le résultat. Par exemple, [`Async.RunSynchronously`](https://msdn.microsoft.com/library/0a6663a9-50f2-4d38-8bf3-cefd1a51fd6b) vous appelez pour exécuter un calcul et retourner le résultat.

## <a name="custom-operations"></a>Opérations personnalisées

Vous pouvez définir une opération personnalisée sur une expression de calcul et utiliser une opération personnalisée en tant qu’opérateur dans une expression de calcul. Par exemple, vous pouvez inclure un opérateur de requête dans une expression de requête. Lorsque vous définissez une opération personnalisée, vous devez définir le rendement et les méthodes pour l’expression de calcul. Pour définir une opération personnalisée, mettez-la dans une classe de [`CustomOperationAttribute`](https://msdn.microsoft.com/library/199f3927-79df-484b-ba66-85f58cc49b19)constructeur pour l’expression de calcul, puis appliquez le . Cet attribut prend une chaîne comme un argument, qui est le nom à utiliser dans une opération personnalisée. Ce nom entre en portée au début de l’accolade bouclée d’ouverture de l’expression de calcul. Par conséquent, vous ne devriez pas utiliser des identifiants qui ont le même nom qu’une opération personnalisée dans ce bloc. Par exemple, évitez l’utilisation `all` d’identifiants tels que ou `last` dans des expressions de requête.

### <a name="extending-existing-builders-with-new-custom-operations"></a>Élargir les constructeurs existants avec de nouvelles opérations personnalisées

Si vous avez déjà une classe de constructeur, ses opérations personnalisées peuvent être étendues à l’extérieur de cette classe de constructeur. Les extensions doivent être déclarées dans les modules. Les espaces de noms ne peuvent pas contenir les membres de vulgarisation, sauf dans le même fichier et le même groupe de déclaration d’espace de nom où le type est défini.

L’exemple suivant montre l’extension de la classe existante. `Microsoft.FSharp.Linq.QueryBuilder`

```fsharp
type Microsoft.FSharp.Linq.QueryBuilder with

    [<CustomOperation("existsNot")>]
    member _.ExistsNot (source: QuerySource<'T, 'Q>, predicate) =
        Enumerable.Any (source.Source, Func<_,_>(predicate)) |> not
```

## <a name="see-also"></a>Voir aussi

- [Référence linguistique F](index.md)
- [Workflows asynchrones](asynchronous-workflows.md)
- [Séquences](https://msdn.microsoft.com/library/6b773b6b-9c9a-4af8-bd9e-d96585c166db)
- [Expressions de requête](query-expressions.md)

---
title: Byrefs
description: 'En savoir plus sur les types ByRef et de type ByRef en F #, qui sont utilisés pour la programmation de bas niveau.'
ms.date: 11/04/2019
ms.openlocfilehash: ff2c06d8940f7341d5d8b1d942be264bfac586c5
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740313"
---
# <a name="byrefs"></a>Byrefs

F # a deux domaines de fonctionnalités majeurs qui traitent de l’espace de la programmation de bas niveau :

* `byref` / `inref` / `outref` Types, qui sont des pointeurs managés. Ils ont des restrictions sur l’utilisation afin que vous ne soyez pas en mesure de compiler un programme qui n’est pas valide au moment de l’exécution.
* `byref`Struct de type like, qui est une [structure](structures.md) qui a une sémantique similaire et les mêmes restrictions au moment de la compilation que `byref<'T>` . Par exemple <xref:System.Span%601> .

## <a name="syntax"></a>Syntaxe

```fsharp
// Byref types as parameters
let f (x: byref<'T>) = ()
let g (x: inref<'T>) = ()
let h (x: outref<'T>) = ()

// Calling a function with a byref parameter
let mutable x = 3
f &x

// Declaring a byref-like struct
open System.Runtime.CompilerServices

[<Struct; IsByRefLike>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

## <a name="byref-inref-and-outref"></a>ByRef, inref et outref

Il existe trois formes de `byref` :

* `inref<'T>`, pointeur managé pour la lecture de la valeur sous-jacente.
* `outref<'T>`, pointeur managé pour l’écriture dans la valeur sous-jacente.
* `byref<'T>`, pointeur managé pour la lecture et l’écriture de la valeur sous-jacente.

Un `byref<'T>` peut être passé là où un `inref<'T>` est attendu. De même, un `byref<'T>` peut être passé là où un `outref<'T>` est attendu.

## <a name="using-byrefs"></a>Utilisation de types ByRef

Pour utiliser un `inref<'T>` , vous devez obtenir une valeur de pointeur avec `&` :

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn $"Now: %O{dt}"

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Pour écrire dans le pointeur à l’aide d’un ou d’un `outref<'T>` `byref<'T>` , vous devez également définir la valeur à laquelle vous attrapez un pointeur `mutable` .

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn $"Now: %O{dt}"
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Si vous écrivez uniquement le pointeur au lieu de le lire, envisagez d’utiliser à la `outref<'T>` place de `byref<'T>` .

### <a name="inref-semantics"></a>Sémantique Inref

Considérez le code suivant :

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Sémantiquement, cela signifie ce qui suit :

* Le détenteur du `x` pointeur ne peut l’utiliser que pour lire la valeur.
* Tout pointeur acquis pour les `struct` champs imbriqués dans `SomeStruct` est du type donné `inref<_>` .

Les éléments suivants sont également vrais :

* Il n’y a aucune implication que d’autres threads ou alias n’ont pas d’accès en écriture à `x` .
* Il n’y a aucune implication qui `SomeStruct` est immuable en raison d' `x` un `inref` .

Toutefois, pour les types valeur F # qui **sont** immuables, le `this` pointeur est déduit comme étant `inref` .

Toutes ces règles signifient que le détenteur d’un `inref` pointeur ne peut pas modifier le contenu immédiat de la mémoire vers laquelle pointe.

### <a name="outref-semantics"></a>Sémantique Outref

L’objectif de `outref<'T>` est d’indiquer que le pointeur doit uniquement être écrit dans. De manière inattendue, `outref<'T>` autorise la lecture de la valeur sous-jacente en dépit de son nom. À des fins de compatibilité. Sémantiquement, `outref<'T>` n’est pas différent de `byref<'T>` .

### <a name="interop-with-c"></a>Interopérabilité avec C\#

C# prend en charge les `in ref` `out ref` Mots clés et, en plus des `ref` retours. Le tableau suivant montre comment F # interprète les émissions de C# :

|Construction C#|F # déduit|
|------------|---------|
|`ref` valeur de retour|`outref<'T>`|
|`ref readonly` valeur de retour|`inref<'T>`|
|Paramètre `in ref`|`inref<'T>`|
|Paramètre `out ref`|`outref<'T>`|

Le tableau suivant montre ce que F # émet :

|Construction F #|Construction émise|
|------------|-----------------|
|Argument `inref<'T>`|`[In]` attribut sur l’argument|
|`inref<'T>` renvoi|`modreq` attribut sur la valeur|
|`inref<'T>` dans l’emplacement ou l’implémentation abstraits|`modreq` argument on ou return|
|Argument `outref<'T>`|`[Out]` attribut sur l’argument|

### <a name="type-inference-and-overloading-rules"></a>Inférence de type et règles de surcharge

Un `inref<'T>` type est déduit par le compilateur F # dans les cas suivants :

1. Un paramètre .NET ou un type de retour qui a un `IsReadOnly` attribut.
2. `this`Pointeur sur un type struct qui n’a aucun champ mutable.
3. Adresse d’un emplacement de mémoire dérivé d’un autre `inref<_>` pointeur.

Quand une adresse implicite d’un `inref` est prise, une surcharge avec un argument de type `SomeType` est préférable à une surcharge avec un argument de type `inref<SomeType>` . Par exemple :

```fsharp
type C() =
    static member M(x: System.DateTime) = x.AddDays(1.0)
    static member M(x: inref<System.DateTime>) = x.AddDays(2.0)
    static member M2(x: System.DateTime, y: int) = x.AddDays(1.0)
    static member M2(x: inref<System.DateTime>, y: int) = x.AddDays(2.0)

let res = System.DateTime.Now
let v =  C.M(res)
let v2 =  C.M2(res, 4)
```

Dans les deux cas, les surcharges `System.DateTime` qui prennent sont résolues plutôt que les surcharges qui prennent `inref<System.DateTime>` .

## <a name="byref-like-structs"></a>Structs de type ByRef

Outre le `byref` / `inref` / `outref` trio, vous pouvez définir vos propres structs qui peuvent adhérer à `byref` une sémantique similaire. Cette opération s’effectue avec l' <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> attribut :

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike` n’implique pas `Struct` . Les deux doivent être présents sur le type.

Un `byref` struct « -like » en F # est un type valeur lié à la pile. Elle n’est jamais allouée sur le tas managé. Un `byref` struct de type like est utile pour la programmation hautes performances, car il est appliqué avec un ensemble de vérifications fortes sur la durée de vie et la non-capture. Les règles sont les suivantes :

* Elles peuvent être utilisées en tant que paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.
* Ils ne peuvent pas être des membres statiques ou d’instance d’une classe ou d’un struct normal.
* Ils ne peuvent pas être capturés par une construction de fermeture ( `async` méthodes ou expressions lambda).
* Ils ne peuvent pas être utilisés comme paramètre générique.

Ce dernier point est essentiel pour la programmation de style pipeline F #, comme c' `|>` est le cas d’une fonction générique qui paramètre ses types d’entrée. Cette restriction peut être assouplie à `|>` l’avenir, car elle est inline et n’effectue aucun appel aux fonctions génériques non inline dans son corps.

Bien que ces règles restreignent fortement l’utilisation, elles le font pour garantir la promesse de l’informatique hautes performances de manière sûre.

## <a name="byref-returns"></a>ByRef retourne

ByRef retourne des fonctions ou des membres F # peuvent être générés et consommés. Lors de l’utilisation d’une `byref` méthode qui retourne une valeur, la valeur est déréférencée implicitement. Par exemple :

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn $"%d{squared}"
```

Pour retourner une valeur ByRef, la variable qui contient la valeur doit être plus longue que la portée actuelle.
En outre, pour retourner ByRef, utilisez `&value` (où la valeur est une variable qui dure plus longtemps que la portée actuelle).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Pour éviter la déréférence implicite, telle que le passage d’une référence par le biais de plusieurs appels chaînés, utilisez `&x` (où `x` est la valeur).

Vous pouvez également assigner directement à un retour `byref` . Considérez le programme suivant (très impératif) :

```fsharp
type C() =
    let mutable nums = [| 1; 3; 7; 15; 31; 63; 127; 255; 511; 1023 |]

    override _.ToString() = String.Join(' ', nums)

    member _.FindLargestSmallerThan(target: int) =
        let mutable ctr = nums.Length - 1

        while ctr > 0 && nums.[ctr] >= target do ctr <- ctr - 1

        if ctr > 0 then &nums.[ctr] else &nums.[0]

[<EntryPoint>]
let main argv =
    let c = C()
    printfn $"Original sequence: %O{c}"

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn $"New sequence:      %O{c}"

    0 // return an integer exit code
```

Il s'agit de la sortie :

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Portée pour types ByRef

Une `let` valeur liée à une valeur ne peut pas avoir une référence supérieure à la portée dans laquelle elle a été définie. Par exemple, les éléments suivants ne sont pas autorisés :

```fsharp
let test2 () =
    let x = 12
    &x // Error: 'x' exceeds its defined scope!

let test () =
    let x =
        let y = 1
        &y // Error: `y` exceeds its defined scope!
    ()
```

Cela vous empêche d’obtenir des résultats différents selon que vous compilez avec des optimisations ou non.

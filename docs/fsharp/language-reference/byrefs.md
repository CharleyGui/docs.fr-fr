---
title: Byrefs
description: Renseignez-vous sur les types byref et byref-like dans F, qui sont utilisés pour la programmation de bas niveau.
ms.date: 11/04/2019
ms.openlocfilehash: 527f465ee87fe153a2deae1306b6730531dc4123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187052"
---
# <a name="byrefs"></a>Byrefs

FMD dispose de deux domaines d’envergure majeurs qui traitent dans l’espace de la programmation de bas niveau :

* `byref` / Les `inref` / types, qui sont des pointeurs `outref` gérés. Ils ont des restrictions sur l’utilisation de sorte que vous ne pouvez pas compiler un programme qui est invalide au moment de l’exécution.
* Une `byref`struct-like, qui est une [structure](structures.md) qui a la sémantique `byref<'T>`similaire et les mêmes restrictions de temps de compilation que . Un exemple <xref:System.Span%601>est .

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

## <a name="byref-inref-and-outref"></a>Byref, inref, et outref

Il existe trois `byref`formes de :

* `inref<'T>`, un pointeur géré pour lire la valeur sous-jacente.
* `outref<'T>`, un pointeur géré pour écrire à la valeur sous-jacente.
* `byref<'T>`, un pointeur géré pour lire et écrire la valeur sous-jacente.

A `byref<'T>` peut être `inref<'T>` passé là où on s’attend à un. De même, un `byref<'T>` peut `outref<'T>` être passé là où on s’attend à un.

## <a name="using-byrefs"></a>Utilisation de byrefs

Pour utiliser `inref<'T>`un , vous devez `&`obtenir une valeur pointeur avec :

```fsharp
open System

let f (dt: inref<DateTime>) =
    printfn "Now: %s" (dt.ToString())

let usage =
    let dt = DateTime.Now
    f &dt // Pass a pointer to 'dt'
```

Pour écrire au pointeur `outref<'T>` `byref<'T>`en utilisant un ou , vous `mutable`devez également faire la valeur que vous prenez un pointeur à .

```fsharp
open System

let f (dt: byref<DateTime>) =
    printfn "Now: %s" (dt.ToString())
    dt <- DateTime.Now

// Make 'dt' mutable
let mutable dt = DateTime.Now

// Now you can pass the pointer to 'dt'
f &dt
```

Si vous n’écrivez que le pointeur au lieu de le lire, envisager d’utiliser `outref<'T>` au lieu de `byref<'T>`.

### <a name="inref-semantics"></a>Sémantique inref

Examinons le code ci-dessous.

```fsharp
let f (x: inref<SomeStruct>) = x.SomeField
```

Semantically, cela signifie ce qui suit:

* Le titulaire `x` du pointeur ne peut l’utiliser que pour lire la valeur.
* Tout pointeur `struct` acquis aux `SomeStruct` champs imbriqués à l’intérieur sont donnés type `inref<_>`.

Ce qui suit est également vrai:

* Il n’y a aucune implication que d’autres `x`fils ou alias n’ont pas l’accès d’écriture à .
* Il n’y `SomeStruct` a aucune implication `x` qui `inref`est immuable en vertu d’être un .

Cependant, pour les types **are** de valeur F `this` ' qui sont immuables, le pointeur est déduit d’être un `inref`.

Toutes ces règles ensemble signifient `inref` que le titulaire d’un pointeur ne peut pas modifier le contenu immédiat de la mémoire pointée vers.

### <a name="outref-semantics"></a>Sémantique Outref

Le but `outref<'T>` est d’indiquer que le pointeur ne doit être écrit à. De façon `outref<'T>` inattendue, permet de lire la valeur sous-jacente malgré son nom. C’est à des fins de compatibilité. Semantically, `outref<'T>` n’est `byref<'T>`pas différent de .

### <a name="interop-with-c"></a>Interop avec C\#

CMD prend `in ref` `out ref` en charge les `ref` mots clés et les mots clés, en plus des retours. Le tableau suivant montre comment le FMD interprète ce que le CMD émet :

|Construction de C|Infère les infères|
|------------|---------|
|`ref`valeur de retour|`outref<'T>`|
|`ref readonly`valeur de retour|`inref<'T>`|
|Paramètre `in ref`|`inref<'T>`|
|Paramètre `out ref`|`outref<'T>`|

Le tableau suivant montre ce que le FMD émet :

|Construction de F|Construction émise|
|------------|-----------------|
|Argument `inref<'T>`|`[In]`attribut sur l’argumentation|
|`inref<'T>`Retour|`modreq`attribut sur la valeur|
|`inref<'T>`dans la fente abstraite ou la mise en œuvre|`modreq`sur l’argumentation ou le retour|
|Argument `outref<'T>`|`[Out]`attribut sur l’argumentation|

### <a name="type-inference-and-overloading-rules"></a>Règles d’inférence et de surcharge de type

Un `inref<'T>` type est déduit par le compilateur F dans les cas suivants :

1. Un paramètre .NET ou `IsReadOnly` un type de retour qui a un attribut.
2. Le `this` pointeur sur un type de struct qui n’a pas de champs mutables.
3. L’adresse d’un emplacement `inref<_>` de mémoire dérivé d’un autre pointeur.

Lorsqu’une adresse `inref` implicite d’un est prise, une `SomeType` surcharge avec un argument de `inref<SomeType>`type est préférable à une surcharge avec un argument de type . Par exemple :

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

Dans les deux cas, `System.DateTime` les surcharges de prise `inref<System.DateTime>`sont résolues plutôt que les surcharges prenant .

## <a name="byref-like-structs"></a>Les structs de byref

En plus `byref` / `inref` / `outref` du trio, vous pouvez définir vos propres `byref`structs qui peuvent adhérer à -comme la sémantique. Ceci est fait <xref:System.Runtime.CompilerServices.IsByRefLikeAttribute> avec l’attribut:

```fsharp
open System
open System.Runtime.CompilerServices

[<IsByRefLike; Struct>]
type S(count1: Span<int>, count2: Span<int>) =
    member x.Count1 = count1
    member x.Count2 = count2
```

`IsByRefLike`n’implique `Struct`pas . Les deux doivent être présents sur le type.

Une`byref`struction «-comme » dans le F est un type de valeur lié à la pile. Il n’est jamais alloué sur le tas géré. Une `byref`structure comme est utile pour la programmation haute performance, car elle est appliquée avec un ensemble de contrôles forts sur la durée de vie et la non-capture. Les règles sont les suivante :

* Ils peuvent être utilisés comme paramètres de fonction, paramètres de méthode, variables locales, retours de méthode.
* Ils ne peuvent pas être statiques ou des membres d’instance d’une classe ou d’une struct normale.
* Ils ne peuvent pas être`async` capturés par une construction de fermeture (méthodes ou expressions lambda).
* Ils ne peuvent pas être utilisés comme paramètre générique.

Ce dernier point est crucial pour la `|>` programmation de type pipeline F, tout comme une fonction générique qui paramélise ses types d’entrées. Cette restriction peut `|>` être assouplie pour l’avenir, car elle est en ligne et ne fait pas d’appels à des fonctions génériques non-inlined dans son corps.

Bien que ces règles restreignent fortement l’utilisation, elles le font pour remplir la promesse d’informatique de haute performance d’une manière sûre.

## <a name="byref-returns"></a>Byref revient

Les retours byref des fonctions de F ou des membres peuvent être produits et consommés. Lors de `byref`la consommation d’une méthode de retour, la valeur est implicitement déreférée. Par exemple :

```fsharp
let squareAndPrint (data : byref<int>) =
    let squared = data*data    // data is implicitly dereferenced
    printfn "%d" squared
```

Pour retourner une valeur byref, la variable qui contient la valeur doit vivre plus longtemps que la portée actuelle.
En outre, pour revenir `&value` byref, l’utilisation (où la valeur est une variable qui vit plus longtemps que la portée actuelle).

```fsharp
let mutable sum = 0
let safeSum (bytes: Span<byte>) =
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    &sum  // sum lives longer than the scope of this function.
```

Pour éviter la déreférence implicite, comme passer une référence `&x` par `x` plusieurs appels enchaînés, utilisez (où est la valeur).

Vous pouvez également attribuer `byref`directement à un retour . Considérez le programme suivant (hautement impératif) :

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
    printfn "Original sequence: %s" (c.ToString())

    let v = &c.FindLargestSmallerThan 16

    v <- v*2 // Directly assign to the byref return

    printfn "New sequence:      %s" (c.ToString())

    0 // return an integer exit code
```

Il s'agit de la sortie :

```console
Original sequence: 1 3 7 15 31 63 127 255 511 1023
New sequence:      1 3 7 30 31 63 127 255 511 1023
```

## <a name="scoping-for-byrefs"></a>Scoping for byrefs

Une `let`valeur liée ne peut pas avoir sa référence supérieure à la portée dans laquelle elle a été définie. Par exemple, ce qui suit est refusé :

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

Cela vous empêche d’obtenir des résultats différents en fonction de si vous compilez avec des optimisations ou non.

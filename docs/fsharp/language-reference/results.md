---
title: Résultats
description: Découvrez comment utiliser le type F# « résultat » pour vous aider à écrire du code tolérant aux erreurs.
ms.date: 04/24/2017
ms.openlocfilehash: 187aa26ccbaac7e0ec998756377bb7b0489eb1ab
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424854"
---
# <a name="results"></a>Résultats

À F# partir de 4,1, il existe un type de `Result<'T,'TFailure>` que vous pouvez utiliser pour écrire du code tolérant aux erreurs qui peut être composé.

## <a name="syntax"></a>Syntaxe

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Notes

Notez que le type de résultat est une [union discriminée struct](discriminated-unions.md#struct-discriminated-unions), qui est une autre fonctionnalité F# introduite dans 4,1.  La sémantique d’égalité structurelle s’applique ici.

Le type de `Result` est généralement utilisé dans la gestion des erreurs monadic, qui est souvent appelée [programmation orientée ferroviaire](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) au sein F# de la communauté.  L’exemple trivial suivant illustre cette approche.

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

Comme vous pouvez le voir, il est assez facile de chaîner plusieurs fonctions de validation si vous les forcez à retourner une `Result`.  Cela vous permet de décomposer des fonctionnalités comme celles-ci en petites parties, comme vous le souhaitez.  Cela a également la valeur ajoutée de l' *application* de l’utilisation des [critères spéciaux](pattern-matching.md) à la fin d’un cycle de validation, qui, à son tour, applique un degré plus élevé de corrections du programme.

## <a name="see-also"></a>Voir aussi

- [Unions discriminées](discriminated-unions.md)
- [Critères spéciaux](pattern-matching.md)

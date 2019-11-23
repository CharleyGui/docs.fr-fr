---
title: Qu’est-ce que F# ?
description: En savoir plus sur F# le langage de programmation et F# la programmation. En savoir plus sur les types de données riches, les fonctions et la façon dont elles s’adaptent.
ms.date: 08/03/2018
ms.openlocfilehash: 3cba509f59a8e81e1a0264de7451e9d80304d768
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332734"
---
# <a name="what-is-f"></a>Qu’est-ce que F\#

F#est un langage de programmation fonctionnelle qui facilite l’écriture de code correct et facile à gérer.

F#la programmation implique principalement la définition de types et de fonctions qui sont déduits et généralisés automatiquement. Vous pouvez ainsi vous concentrer sur le domaine du problème et manipuler ses données, plutôt que sur les détails de la programmation.

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

F#possède de nombreuses fonctionnalités, notamment :

* Syntaxe simplifiée
* Immuable par défaut
* Inférence de type et généralisation automatique
* Fonctions de première classe
* Types de données puissants
* Critères spéciaux
* Programmation asynchrone

Un jeu complet de fonctionnalités est documenté dans la [ F# référence du langage](./language-reference/index.md).

## <a name="rich-data-types"></a>Types de données enrichis

Les types de données tels que les [enregistrements](./language-reference/records.md) et les [unions discriminées](./language-reference/discriminated-unions.md) vous permettent de représenter des données et des domaines complexes.

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F#les enregistrements et les unions discriminées sont non null, immuables et comparables par défaut, ce qui les rend très faciles à utiliser.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Exactitude appliquée avec les fonctions et les critères spéciaux

F#les fonctions sont faciles à déclarer et puissantes dans la pratique. Lorsqu’elles sont combinées avec des [critères spéciaux](./language-reference/pattern-matching.md), elles vous permettent de définir le comportement dont l’exactitude est appliquée par le compilateur.

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F#les fonctions sont également de première classe, ce qui signifie qu’elles peuvent être passées en tant que paramètres et retournées à partir d’autres fonctions.

## <a name="functions-to-define-operations-on-objects"></a>Fonctions permettant de définir des opérations sur des objets

F#offre une prise en charge complète des objets, qui sont des types de données utiles lorsque vous devez mélanger des données et des fonctionnalités. F#les fonctions sont utilisées pour manipuler des objets.

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Plutôt que d’écrire du code orienté objet, dans, F#vous écrirez souvent du code qui traite les objets comme un autre type de données pour les fonctions à manipuler. Les fonctionnalités telles que les [interfaces génériques](./language-reference/interfaces.md), les [expressions d’objet](./language-reference/object-expressions.md)et l’utilisation judicieuse des [membres](./language-reference/members/index.md) sont F# communes aux programmes plus volumineux.

## <a name="next-steps"></a>Étapes suivantes :

Pour en savoir plus sur un plus grand F# ensemble de fonctionnalités, consultez la [ F# visite guidée](tour.md).

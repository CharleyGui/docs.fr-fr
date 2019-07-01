---
title: Qu’est-ce que F# ?
description: En savoir plus sur ce que le F# langage de programmation est et ce qu’il F# ressemble par programmation. En savoir plus sur les types de données enrichis, fonctions et comment ils s’imbriquent.
ms.date: 08/03/2018
ms.openlocfilehash: fc4f4db771c43a4ec08cc9d3a247cf1f38e60457
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486831"
---
# <a name="what-is-f"></a><span data-ttu-id="8bea6-104">Nouveautés de F\#</span><span class="sxs-lookup"><span data-stu-id="8bea6-104">What is F\#</span></span>

<span data-ttu-id="8bea6-105">F#est un langage de programmation fonctionnel qui le rend facile à écrire du code correct et facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="8bea6-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="8bea6-106">F#programmation principalement implique la définition des types et fonctions qui sont de type déduit et généralisées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="8bea6-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="8bea6-107">Cela permet de prendre en compte restent sur le domaine du problème et la manipulation de ses données, plutôt que les détails de la programmation.</span><span class="sxs-lookup"><span data-stu-id="8bea6-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="8bea6-108">F#comporte de nombreuses fonctionnalités, notamment :</span><span class="sxs-lookup"><span data-stu-id="8bea6-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="8bea6-109">Syntaxe simplifiée</span><span class="sxs-lookup"><span data-stu-id="8bea6-109">Lightweight syntax</span></span>
* <span data-ttu-id="8bea6-110">Immuable par défaut</span><span class="sxs-lookup"><span data-stu-id="8bea6-110">Immutable by default</span></span>
* <span data-ttu-id="8bea6-111">Généralisation automatique et inférence de type</span><span class="sxs-lookup"><span data-stu-id="8bea6-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="8bea6-112">Fonctions de première classe</span><span class="sxs-lookup"><span data-stu-id="8bea6-112">First-class functions</span></span>
* <span data-ttu-id="8bea6-113">Types de données puissants</span><span class="sxs-lookup"><span data-stu-id="8bea6-113">Powerful data types</span></span>
* <span data-ttu-id="8bea6-114">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="8bea6-114">Pattern matching</span></span>
* <span data-ttu-id="8bea6-115">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="8bea6-115">Async programming</span></span>

<span data-ttu-id="8bea6-116">Un ensemble complet de fonctionnalités sont documentées dans le [ F# référence du langage](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="8bea6-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="8bea6-117">Types de données riches</span><span class="sxs-lookup"><span data-stu-id="8bea6-117">Rich data types</span></span>

<span data-ttu-id="8bea6-118">Types de données tels que [enregistrements](language-reference/records.md) et [Unions discriminées](language-reference/discriminated-unions.md) vous permettent de représenter des données complexes et domaines.</span><span class="sxs-lookup"><span data-stu-id="8bea6-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="8bea6-119">F#enregistrements et les unions discriminées sont non null, immuable et comparables par défaut, ce qui les rend très facile à utiliser.</span><span class="sxs-lookup"><span data-stu-id="8bea6-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="8bea6-120">Exactitude appliqué avec les fonctions et les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="8bea6-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="8bea6-121">F#les fonctions sont faciles à déclarer et puissantes dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="8bea6-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="8bea6-122">Lorsqu’il est combiné avec [critères spéciaux](language-reference/pattern-matching.md), ils vous permettent de définir un comportement dont l’exactitude est appliquée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="8bea6-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="8bea6-123">F#les fonctions sont également une excellente, ce qui signifie que peuvent être passés comme paramètres et retournés à partir d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="8bea6-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="8bea6-124">Fonctions pour définir des opérations sur des objets</span><span class="sxs-lookup"><span data-stu-id="8bea6-124">Functions to define operations on objects</span></span>

<span data-ttu-id="8bea6-125">F#a une prise en charge complète pour les objets qui sont des types de données utiles lorsque vous avez besoin fusionner des données et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="8bea6-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="8bea6-126">F#fonctions sont utilisées pour manipuler des objets.</span><span class="sxs-lookup"><span data-stu-id="8bea6-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<[<EqualityConditionOn>] 'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

<span data-ttu-id="8bea6-127">Au lieu d’écrire du code qui est orienté objet, dans F#, vous allez souvent écrire du code qui traite les objets qu’un autre type de données pour les fonctions à manipuler.</span><span class="sxs-lookup"><span data-stu-id="8bea6-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="8bea6-128">Fonctionnalités telles que [interfaces génériques](language-reference/interfaces.md), [expressions d’objet](language-reference/object-expressions.md)et l’utilisation judicieuse des [membres](language-reference/members/index.md) sont courantes dans les plus volumineux F# programmes.</span><span class="sxs-lookup"><span data-stu-id="8bea6-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8bea6-129">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8bea6-129">Next steps</span></span>

<span data-ttu-id="8bea6-130">Pour en savoir plus sur un ensemble plus important de F# fonctionnalités, consultez le [ F# visite](tour.md).</span><span class="sxs-lookup"><span data-stu-id="8bea6-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>

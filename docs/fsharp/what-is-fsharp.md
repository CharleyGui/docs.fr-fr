---
title: Qu’est-ce que F# ?
description: 'En savoir plus sur le langage de programmation F # et sur la programmation F #. En savoir plus sur les types de données riches, les fonctions et la façon dont elles s’adaptent.'
ms.date: 08/03/2018
ms.openlocfilehash: a6bad3e1db63c3fe948b5916925d5eb24a18a41c
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739475"
---
# <a name="what-is-f"></a><span data-ttu-id="0ad43-104">Présentation de F\#</span><span class="sxs-lookup"><span data-stu-id="0ad43-104">What is F\#</span></span>

<span data-ttu-id="0ad43-105">F # est un langage de programmation fonctionnelle qui facilite l’écriture de code correct et facile à gérer.</span><span class="sxs-lookup"><span data-stu-id="0ad43-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="0ad43-106">La programmation F # implique principalement de définir des types et des fonctions qui sont déduits et généralisés automatiquement.</span><span class="sxs-lookup"><span data-stu-id="0ad43-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="0ad43-107">Vous pouvez ainsi vous concentrer sur le domaine du problème et manipuler ses données, plutôt que sur les détails de la programmation.</span><span class="sxs-lookup"><span data-stu-id="0ad43-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name = $"Hello, {name}! Isn't F# great?"

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn $"{greeting}")

    0
```

<span data-ttu-id="0ad43-108">F # propose de nombreuses fonctionnalités, notamment :</span><span class="sxs-lookup"><span data-stu-id="0ad43-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="0ad43-109">Syntaxe simplifiée</span><span class="sxs-lookup"><span data-stu-id="0ad43-109">Lightweight syntax</span></span>
* <span data-ttu-id="0ad43-110">Immuable par défaut</span><span class="sxs-lookup"><span data-stu-id="0ad43-110">Immutable by default</span></span>
* <span data-ttu-id="0ad43-111">Inférence de type et généralisation automatique</span><span class="sxs-lookup"><span data-stu-id="0ad43-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="0ad43-112">Fonctions de première classe</span><span class="sxs-lookup"><span data-stu-id="0ad43-112">First-class functions</span></span>
* <span data-ttu-id="0ad43-113">Types de données puissants</span><span class="sxs-lookup"><span data-stu-id="0ad43-113">Powerful data types</span></span>
* <span data-ttu-id="0ad43-114">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="0ad43-114">Pattern matching</span></span>
* <span data-ttu-id="0ad43-115">Programmation asynchrone</span><span class="sxs-lookup"><span data-stu-id="0ad43-115">Async programming</span></span>

<span data-ttu-id="0ad43-116">Un jeu complet de fonctionnalités est documenté dans la [Référence du langage F #](./language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ad43-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="0ad43-117">Types de données enrichis</span><span class="sxs-lookup"><span data-stu-id="0ad43-117">Rich data types</span></span>

<span data-ttu-id="0ad43-118">Les types de données tels que les [enregistrements](./language-reference/records.md) et les [unions discriminées](./language-reference/discriminated-unions.md) vous permettent de représenter des données et des domaines complexes.</span><span class="sxs-lookup"><span data-stu-id="0ad43-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

```fsharp
// Group data with Records
type SuccessfulWithdrawal =
    { Amount: decimal
      Balance: decimal }

type FailedWithdrawal =
    { Amount: decimal
      Balance: decimal
      IsOverdraft: bool }

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

<span data-ttu-id="0ad43-119">Les enregistrements F # et les unions discriminées sont non null, immuables et comparables par défaut, ce qui les rend très faciles à utiliser.</span><span class="sxs-lookup"><span data-stu-id="0ad43-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="0ad43-120">Exactitude appliquée avec les fonctions et les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="0ad43-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="0ad43-121">Les fonctions F # sont faciles à déclarer et puissantes dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="0ad43-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="0ad43-122">Lorsqu’elles sont combinées avec des [critères spéciaux](./language-reference/pattern-matching.md), elles vous permettent de définir le comportement dont l’exactitude est appliquée par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="0ad43-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f{s.Amount}"
    | InsufficientFunds f -> printfn "Failed: balance is %f{f.Balance}"
    | CardExpired d -> printfn "Failed: card expired on {d}"
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

<span data-ttu-id="0ad43-123">Les fonctions F # sont également de première classe, ce qui signifie qu’elles peuvent être passées en tant que paramètres et retournées à partir d’autres fonctions.</span><span class="sxs-lookup"><span data-stu-id="0ad43-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="0ad43-124">Fonctions permettant de définir des opérations sur des objets</span><span class="sxs-lookup"><span data-stu-id="0ad43-124">Functions to define operations on objects</span></span>

<span data-ttu-id="0ad43-125">F # offre une prise en charge complète des objets, qui sont des types de données utiles lorsque vous devez mélanger des données et des fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="0ad43-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="0ad43-126">Les fonctions F # sont utilisées pour manipuler des objets.</span><span class="sxs-lookup"><span data-stu-id="0ad43-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="0ad43-127">Plutôt que d’écrire du code orienté objet, en F #, vous écrirez souvent du code qui traite les objets comme un autre type de données pour les fonctions à manipuler.</span><span class="sxs-lookup"><span data-stu-id="0ad43-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="0ad43-128">Les fonctionnalités telles que les [interfaces génériques](./language-reference/interfaces.md), les [expressions d’objet](./language-reference/object-expressions.md)et l’utilisation judicieuse des [membres](./language-reference/members/index.md) sont courantes dans des programmes F # plus volumineux.</span><span class="sxs-lookup"><span data-stu-id="0ad43-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0ad43-129">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="0ad43-129">Next steps</span></span>

<span data-ttu-id="0ad43-130">Pour en savoir plus sur un plus grand ensemble de fonctionnalités F #, consultez la [visite guidée de f #](tour.md).</span><span class="sxs-lookup"><span data-stu-id="0ad43-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>

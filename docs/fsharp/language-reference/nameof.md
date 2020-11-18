---
title: Nameof
description: En savoir plus sur l’opérateur nameof, une fonctionnalité de recherche de code qui vous permet de générer le nom de n’importe quel symbole dans votre code source.
ms.date: 11/12/2020
ms.openlocfilehash: 9947d7172d1b73db5c181297ec8b1131382e1f5e
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688617"
---
# <a name="nameof"></a><span data-ttu-id="ec545-103">Nameof</span><span class="sxs-lookup"><span data-stu-id="ec545-103">Nameof</span></span>

<span data-ttu-id="ec545-104">L' `nameof` expression produit une constante de chaîne qui correspond au nom dans la source pour presque toutes les constructions F # dans la source.</span><span class="sxs-lookup"><span data-stu-id="ec545-104">The `nameof` expression produces a string constant that matches the name in source for nearly any F# construct in source.</span></span>

## <a name="syntax"></a><span data-ttu-id="ec545-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec545-105">Syntax</span></span>

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a><span data-ttu-id="ec545-106">Notes</span><span class="sxs-lookup"><span data-stu-id="ec545-106">Remarks</span></span>

<span data-ttu-id="ec545-107">`nameof` fonctionne en résolvant le symbole qui lui est passé et produit le nom de ce symbole tel qu’il est déclaré dans votre code source.</span><span class="sxs-lookup"><span data-stu-id="ec545-107">`nameof` works by resolving the symbol passed to it and produces the name of that symbol as it is declared in your source code.</span></span> <span data-ttu-id="ec545-108">Cela est utile dans différents scénarios, tels que la journalisation, et protège votre journal des modifications dans le code source.</span><span class="sxs-lookup"><span data-stu-id="ec545-108">This is useful in various scenarios, such as logging, and protects your logging against changes in source code.</span></span>

```fsharp
let months =
    [
        "January"; "February"; "March"; "April";
        "May"; "June"; "July"; "August"; "September";
        "October"; "November"; "December"
    ]

let lookupMonth month =
    if (month > 12 || month < 1) then
        invalidArg (nameof month) ($"Value passed in was %d{month}.")

    months.[month-1]

printfn "%s" (lookupMonth 12)
printfn "%s" (lookupMonth 1)
printfn "%s" (lookupMonth 13)
```

<span data-ttu-id="ec545-109">La dernière ligne lèvera une exception et `"month"` sera affichée dans le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="ec545-109">The last line will throw an exception and `"month"` will be shown in the error message.</span></span>

<span data-ttu-id="ec545-110">Vous pouvez prendre un nom de presque toutes les constructions F # :</span><span class="sxs-lookup"><span data-stu-id="ec545-110">You can take a name of nearly every F# construct:</span></span>

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

<span data-ttu-id="ec545-111">`nameof` n’est pas une fonction de première classe et ne peut pas être utilisée en tant que telle.</span><span class="sxs-lookup"><span data-stu-id="ec545-111">`nameof` is not a first-class function and cannot be used as such.</span></span> <span data-ttu-id="ec545-112">Cela signifie qu’elle ne peut pas être partiellement appliquée et que les valeurs ne peuvent pas être transférées dans celle-ci via des opérateurs de pipeline F #.</span><span class="sxs-lookup"><span data-stu-id="ec545-112">That means it cannot be partially applied and values cannot be piped into it via F# pipeline operators.</span></span>

## <a name="nameof-on-operators"></a><span data-ttu-id="ec545-113">Nameof sur les opérateurs</span><span class="sxs-lookup"><span data-stu-id="ec545-113">Nameof on operators</span></span>

<span data-ttu-id="ec545-114">Les opérateurs en F # peuvent être utilisés de deux manières, en tant que texte d’opérateur proprement dit, ou en tant que symbole représentant le formulaire compilé.</span><span class="sxs-lookup"><span data-stu-id="ec545-114">Operators in F# can be used in two ways, as an operator text itself, or a symbol representing the compiled form.</span></span> <span data-ttu-id="ec545-115">`nameof` sur un opérateur produira le nom de l’opérateur tel qu’il est déclaré dans la source.</span><span class="sxs-lookup"><span data-stu-id="ec545-115">`nameof` on an operator will produce the name of the operator as it is declared in source.</span></span> <span data-ttu-id="ec545-116">Pour récupérer le nom compilé, utilisez le nom compilé dans la source :</span><span class="sxs-lookup"><span data-stu-id="ec545-116">To get the compiled name, use the compiled name in source:</span></span>

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a><span data-ttu-id="ec545-117">Nameof sur les génériques</span><span class="sxs-lookup"><span data-stu-id="ec545-117">Nameof on generics</span></span>

<span data-ttu-id="ec545-118">Vous pouvez également utiliser un nom de paramètre de type générique, mais la syntaxe est différente :</span><span class="sxs-lookup"><span data-stu-id="ec545-118">You can also take a name of a generic type parameter, but the syntax is different:</span></span>

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

<span data-ttu-id="ec545-119">`nameof<'TGeneric>` prend le nom du symbole tel qu’il est défini dans source, et non le nom du type substitué sur un site d’appel.</span><span class="sxs-lookup"><span data-stu-id="ec545-119">`nameof<'TGeneric>` will take the name of the symbol as defined in source, not the name of the type substituted at a call site.</span></span>

<span data-ttu-id="ec545-120">La raison pour laquelle la syntaxe est différente est d’aligner avec d’autres opérateurs intrinsèques F # comme `typeof<>` et `typedefof<>` .</span><span class="sxs-lookup"><span data-stu-id="ec545-120">The reason why the syntax is different is to align with other F# intrinsic operators like `typeof<>` and `typedefof<>`.</span></span> <span data-ttu-id="ec545-121">Cela rend F # cohérent en ce qui concerne les opérateurs qui agissent sur les types génériques et tout autre contenu dans la source.</span><span class="sxs-lookup"><span data-stu-id="ec545-121">This makes F# consistent with respect to operators that act on generic types and anything else in source.</span></span>

## <a name="nameof-in-pattern-matching"></a><span data-ttu-id="ec545-122">Nameof dans les critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="ec545-122">Nameof in pattern matching</span></span>

<span data-ttu-id="ec545-123">Le [ `nameof` modèle](pattern-matching.md#nameof-pattern) vous permet `nameof` d’utiliser dans une expression de correspondance de modèle comme suit :</span><span class="sxs-lookup"><span data-stu-id="ec545-123">The [`nameof` pattern](pattern-matching.md#nameof-pattern) lets you use `nameof` in a pattern match expression like so:</span></span>

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```

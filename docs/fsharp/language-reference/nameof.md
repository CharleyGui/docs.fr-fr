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
# <a name="nameof"></a>Nameof

L' `nameof` expression produit une constante de chaîne qui correspond au nom dans la source pour presque toutes les constructions F # dans la source.

## <a name="syntax"></a>Syntaxe

```fsharp
nameof symbol
nameof<'TGeneric>
```

## <a name="remarks"></a>Notes

`nameof` fonctionne en résolvant le symbole qui lui est passé et produit le nom de ce symbole tel qu’il est déclaré dans votre code source. Cela est utile dans différents scénarios, tels que la journalisation, et protège votre journal des modifications dans le code source.

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

La dernière ligne lèvera une exception et `"month"` sera affichée dans le message d’erreur.

Vous pouvez prendre un nom de presque toutes les constructions F # :

```fsharp
module M =
    let f x = nameof x

printfn $"{(M.f 12)]}"
printfn $"{(nameof M)}"
printfn $"{(nameof M.f)}"
```

`nameof` n’est pas une fonction de première classe et ne peut pas être utilisée en tant que telle. Cela signifie qu’elle ne peut pas être partiellement appliquée et que les valeurs ne peuvent pas être transférées dans celle-ci via des opérateurs de pipeline F #.

## <a name="nameof-on-operators"></a>Nameof sur les opérateurs

Les opérateurs en F # peuvent être utilisés de deux manières, en tant que texte d’opérateur proprement dit, ou en tant que symbole représentant le formulaire compilé. `nameof` sur un opérateur produira le nom de l’opérateur tel qu’il est déclaré dans la source. Pour récupérer le nom compilé, utilisez le nom compilé dans la source :

```fsharp
nameof(+) // "+"
nameof op_Addition // "op_Addition"
```

## <a name="nameof-on-generics"></a>Nameof sur les génériques

Vous pouvez également utiliser un nom de paramètre de type générique, mais la syntaxe est différente :

```fsharp
let f<'a> () = nameof<'a>
f() // "a"
```

`nameof<'TGeneric>` prend le nom du symbole tel qu’il est défini dans source, et non le nom du type substitué sur un site d’appel.

La raison pour laquelle la syntaxe est différente est d’aligner avec d’autres opérateurs intrinsèques F # comme `typeof<>` et `typedefof<>` . Cela rend F # cohérent en ce qui concerne les opérateurs qui agissent sur les types génériques et tout autre contenu dans la source.

## <a name="nameof-in-pattern-matching"></a>Nameof dans les critères spéciaux

Le [ `nameof` modèle](pattern-matching.md#nameof-pattern) vous permet `nameof` d’utiliser dans une expression de correspondance de modèle comme suit :

```fsharp
let f (str: string) =
    match str with
    | nameof str -> "It's 'str'!"
    | _ -> "It is not 'str'!"

f "str" // matches
f "asdf" // does not match
```
